---
{"dg-publish":true,"permalink":"/article-full/all-the-transformer-math-you-need-to-know-how-to-scale-your-model/","title":"All the Transformer Math You Need to Know | How To Scale Your Model","tags":["article","full"]}
---

# All the Transformer Math You Need to Know | How To Scale Your Model  

Source: [github.io](https://jax-ml.github.io/scaling-book/transformers/)  

#TransformerModels #DeepLearning #NeuralNetworks #AI  

## All the Transformer Math You Need to Know

Part 4 of [How To Scale Your Model](https://jax-ml.github.io/scaling-book) ([Part 3: Sharding](https://jax-ml.github.io/scaling-book/sharding) | [Part 5: Training](https://jax-ml.github.io/scaling-book/training))

Here we'll do a quick review of the Transformer architecture, specifically how to calculate FLOPs, bytes, and other quantities of interest.

## Counting Dots

Let’s start with vectors $x$ , $y$ and matrices $A$ , $B$ of the following shapes:

$$
arrayshapex[P]y[P]A[N P]B[P M]
$$
- A dot product of $x⋅y$ requires $P$ *adds* and *multiplies*, or $2P$ floating-point operations total.
- A matrix-vector product $Ax$ does $N$ dot-products along the rows of $A$ , for $2NP$ FLOPs.
- A matrix-matrix product $AB$ does $M$ matrix-vector products for each column of $B$ , for $2NPM$ FLOPs total.
- In general, if we have two higher dimensional arrays $C$ and $D$ , where some dimensions are CONTRACTING and some are BATCHING. (e.g. $C[GHIJKL],D[GHMNKL]$ ) then the FLOPs cost of this contraction is two times the product of all of the $C$ and $D$ dimensions where the batch and contraction dimensions are only counted once, (e.g. $2GHIJMNKL$ ). Note that a dimension is only batching if it occurs in both multiplicands. (Note also that the factor of 2 won’t apply if there are no contracting dimensions and this is just an elementwise product.)
$$
OperationFLOPsDatax⋅y2P2PAx2NPNP+PAB2NPMNP+PM[c0,...,cN]⋅[d0,...,dN]2∏ci×∏dj∉BATCHdj∉CONTRACTdj∏ci+∏dj
$$

Make note of the fact that for a matrix-matrix multiply, the *compute* scales cubically $O(N3)$ while the data transfer only scales quadratically $O(N2)$ - this means that as we scale up our matmul size, it becomes *easier* to hit the compute-saturated limit. This is extremely unusual, and explains in large part why we use architectures dominated by matrix multiplication - they’re amenable to being scaled!

![](https://jax-ml.github.io/scaling-book/assets/img/matmul-flops.gif)

### Forward and reverse FLOPs

During training, we don’t particularly care about the result of a given matrix multiply; we really care about its derivative. That means we do significantly more FLOPs during backpropagation.

If we imagine **B** is just one matrix in a larger network and **A** are our input activations with **C = A B**, the derivative of the loss **L** with respect to **B** is given by the chain rule:

$$
∂L∂B=∂L∂C∂C∂B=AT(∂L∂C)
$$

which is an outer product and requires 2NPM FLOPs to compute (since it contracts over the N dimension). Likewise, the derivative of the loss with respect to **A** is

$$
∂L∂A=∂L∂C∂C∂A=(∂L∂C)BT
$$

is again 2NPM FLOPs since **dL/dC** is a (co-)vector of size $[N,M]$ . While this quantity isn’t the derivative wrt. a parameter, it’s used to compute derivatives for previous layers of the network (e.g. just as dL/dC is used to compute dL/dB above).

Adding these up, we see that **during training, we have a total of 6NPM FLOPs**, compared to 2NPM during inference: 2NPM in the forward pass, 4NPM in the backward pass. Since PM is the number of parameters in the matrix, this is the simplest form of the famous $6∗num parameters∗num tokens$ approximation of Transformer FLOPs during training: each token requires $6∗num parameters$ FLOPs. We’ll show a more correct derivation below.

## Transformer Accounting

Transformers are the future. Well, they’re the present at least. Maybe a few years ago, they were one of many architectures. But today, it’s worth knowing pretty much every detail of the architecture. We won’t reintroduce the architecture but [this blog](https://jalammar.github.io/illustrated-transformer/) and the [original Transformer paper](https://arxiv.org/abs/1706.03762) may be helpful references.

Here’s a basic diagram of the Transformer decoder architecture:

![](https://jax-ml.github.io/scaling-book/assets/img/transformer-diagram.png)

Figure: this diagram shows one layer of a standard Transformer and flows from top-to-bottom. We use a single-letter convention to describe the shapes and layouts of arrays in a Transformer, again showing contracting dimensions in red, and batched dimensions in blue. In a given operation, the input shape is given on top-left and the parameter shape is given on the top-right, with the resulting shape below, e.g. BTD is the input shape for the gating einsum and DF is the weight shape.

**Note \[gating einsum\]**: The diagram above uses a “ [gating einsums](https://arxiv.org/abs/2002.05202) ” where we split the up-projection matrix into two matrices (W\_\\text{In1} and W\_\\text{In2} above) whose outputs are elementwise multiplied as a kind of “gating function”. Not all LLMs use this, so you will sometimes see a single W\_\\text{In} matrix and a total MLP parameter count of 2DF instead of 3DF. Typically in this case, D and F will be scaled up to keep the parameter count the same as the 3 matrix case. With that said, some form of gating einsum is used by LLAMA, DeepSeek, and many other models.

**Note 2 \[MHA attention\]**: With self-attention, T and S are the same but for cross-attention they may be different. With vanilla Multi-Head Attention (MHA), N and K are the same while for [Multi-Query Attention](https://arxiv.org/abs/1911.02150) (MQA) K=1 and for [Grouped MQA](https://arxiv.org/abs/2305.13245) (GMQA) K merely has to divide N.

## Global FLOPs and Params Calculation

For the below we’re going to compute per-layer FLOPs to avoid having to stick factors of **L** everywhere.

### MLPs

The MLPs of a Transformer typically consist of 2 input matmuls that are element-wise combined and a single output matmul:

$$
operationtrain FLOPsparamsA[B,T,D]⋅Win1[D,F]6BTDFDFA[B,T,D]⋅Win2[D,F]6BTDFDFσ(Ain1)[B,T,F]∗Ain2[B,T,F]O(BTF)A[B,T,F]⋅Wout[F,D]6BTDFDF≈18BTDF3DF
$$

### Attention

For the generic grouped-query attention case with different **Q** and **KV** head numbers, let us assume equal head dimension H for **Q**,**K**,**V** projections, and estimate the cost of the **QKVO** matmuls:

$$
operationtrain FLOPsparamsA[B,T,D]⋅WQ[D,N,H]6BTDNHDNHA[B,T,D]⋅WK[D,K,H]6BTDKHDKHA[B,T,D]⋅WV[D,K,H]6BTDKHDKHA[B,T,N,H]⋅WO[N,H,D]6BTDNHDNH12BTD(N+K)H2D(N+K)H
$$

The dot-product attention operation is more subtle, effectively being a $TH⋅HS$ matmul batched over the $B$ , $K$ dimensions, a softmax, and a $TS⋅SH$ matmul again batched over the $B$ , $K$ dimensions. We highlight the batched dims in blue:

$$
operationtrain FLOPsQ[B,T,K,G,H]⋅K[B,S,K,H]6BTSKGH=6BTSNHsoftmaxSL[B,T,S,K,G]O(BTSKG)=O(BTSN)S[B,T,S,K,G]⋅V[B,S,K,H]6BTSKGH=6BTSNH≈12BTSNH=12BT2NH
$$

### Other Operations

There are several other operations happening in a Transformer. Layernorms are comparatively cheap and can be ignored for first-order cost estimates. There is also the final enormous (though not per-layer) unembedding matrix multiply.

$$
operationtrain FLOPsparamslayernormDA[B,T,D]O(BTD)DA[B,T,D]⋅Wunembed[D,V]6BTDVDV
$$

### General rule of thumb for Transformer FLOPs

If we neglect the cost of dot-product attention for shorter-context training, then the total FLOPs across all layers is

$$
(18BTDF+12BTD(N+K)H)L=6∗BT∗(3DF+2D(N+K)H)L=6∗num tokens∗parameter count
$$

Leading to a famous rule of thumb for estimating dense Transformer FLOP count, ignoring the attention FLOPs. (Unembedding is another simple matmul with 6BSDV FLOPs and DV params, and follows the same rule of thumb.)

### Fractional cost of attention with context length

If we do account for dot-product attention above and assume $F=4D$ , $D=NH$ (as is typical) and $N=K$ :

$$
attention FLOPsmatmul FLOPs=12BT2NH18BTDF+24BTDNH=12BT2D4∗18BTD2+24BTD2=12BT2D96BTD2=T8D
$$

So the takeaway is that **dot-product attention FLOPs only become dominant during training once T>8D**. For D ~ 8k, this would be ~64K tokens. This makes some sense, since it means as the MLP size increases, the attention FLOPs become less critical. For large models, the quadratic cost of attention is not actually a huge obstacle to longer context training. However, for smaller models, even e.g. Gemma-27B, D=4608 which means attention becomes dominant around 32k sequence lengths. Flash Attention also helps alleviate the cost of long-context, which we discuss briefly [in Appendix A](https://jax-ml.github.io/scaling-book/transformers/#appendix-a-how-does-flash-attention-work).

## Miscellaneous Math

### Sparsity and Mixture-of-Experts

We’d be remiss not to briefly discuss Mixture of Experts (MoE) models, which replace the single dense MLP blocks in a standard Transformer with a set of independent MLPs that can be dynamically routed between. To a first approximation, **an MoE is just a normal dense model with E MLP blocks per layer**, instead of just one. Each token activates k of these experts, typically k=2. This increases the parameter count by O(E), while multiplying the total number of activated parameters per token by k, compared with the dense version.

![](https://jax-ml.github.io/scaling-book/assets/img/moe.png)

Figure: an example MoE layer with n experts. The gating expert routes each token to k of them, and the output of those MLPs get summed. Our parameter count is times the size of each expert, but only are used for each token. Source.

Compared to a dense model, an MoE introduces new comms, primarily two AllToAlls (one before and one after the MoE block) that route tokens to the correct expert and bring them back to their home device.Technically, this only happens if we are data or sequence sharded along the same axis as our experts. However as we saw in the previous section, the cost of each AllToAll is only 1/4 that of a comparable AllGather along a single axis (for a bidirectional ring).

### Gradient checkpointing

Backpropagation as an algorithm trades memory for compute. Instead of a backward pass requiring $O(nlayers2)$ FLOPs, **it requires $O(nlayers)$ memory**, saving all intermediate activations generated during the forward pass. While this is better than quadratic compute, it’s incredibly expensive memory-wise: a model with $B∗T=4M$ (4M total tokens per batch), L=64, and D=8192 that avoids all unnecessary backward pass compute would have to save roughly $2∗20∗B∗T∗D∗L=84TB$ of activations in bfloat16. 20 comes from (roughly) counting every intermediate node in the Transformer diagram above, since e.g.

$$
f(x)=exp⁡(g(x))
$$
 
$$
dfdx=exp⁡(g(x))⋅dgdx
$$

so to avoid recomputing we need to save $g(x)$ and $exp⁡(g(x))$ from the forward pass. To avoid saving this much memory, we can choose to only save some fraction of the intermediate activations. Here are a few strategies we use.

- **Block remat**: only save the input to each layer. This is the most aggressive method we use and only saves 1 checkpoint per layer, meaning we’d only save 4.2TB in the example above. This forces us to repeat essentially all forward pass FLOPs in the backward pass, meaning we increase our FLOPs from $6ND$ to roughly $8ND$ .
- **Big matmuls only:** another simple policy is to only save the outputs of large matmuls. This lets us avoid recomputing any large matmuls during the backward pass, but still makes us recompute other activation functions and parts of attention. This reduces 20 per layer to closer to 7 per layer.

This by no means comprehensive. When using JAX, these are typically controlled by `jax.remat` / `jax.checkpoint` (you can read more [here](https://jax.readthedocs.io/en/latest/_autosummary/jax.checkpoint.html)).

### Key-Value (KV) caching

As we’ll see in [Section 7](https://jax-ml.github.io/scaling-book/inference), LLM inference has two key parts, prefill and generation.

- **Prefill** processes a long prompt and saves its attention activations in a Key-Value Cache (KV Cache) for use in generation, specifically the key-value projections in the attention block.
- **Generation** batches several of these KV caches together and samples tokens from each of them.

Each KV cache is then effectively an array of size \[2, S, L, K, H\] where the 2 accounts for the keys and values. This is quite large! The total size of the Key-Value cache in int8 is 2SLKH. For a moderately-sized model with 8k context length, 64 layers, and KH = NH = D = 8192, this is 2 \\cdot 8192 \\cdot 64 \\cdot 8192 = 8\\text{GiB}. You can see why we would want to use GMQA with K \\ll N.

## What Should You Take Away from this Section?

- The overall parameters and FLOPs of a Transformer are fairly easy to calculate, and are summarized here, assuming MHA (with batch size B, vocab size V, a sequence of length T, D=d <sub>model</sub>, and F=d <sub>ff</sub>):

| Component | Params per layer | Training FLOPs per layer |
| --- | --- | --- |
| **MLP** | 3DF | 18BTDF |
| **Attention** | 4DNH | 24BTDNH + 12BT <sup>2</sup> NH |
| **Other** | D | BTD |
| **Vocab** | DV (total, not per-layer) | 12BTDV |

- The parameter count of the MLP block dominates the total parameter count and the MLP block also dominates the FLOPs budget as long as the sequence length T < 8D.
- The total FLOPs budget during training is well approximated by $6⋅num_params⋅num_tokens$ for reasonable context lengths.
- During inference, our KV caches are roughly $2⋅S⋅L⋅N⋅H$ per cache, although architectural modifications can often reduce this.

## A Few Problems to Work

**Question 1:** How many parameters does a model with D=4096, F=4 \\cdot D, V=32,000, and L=64 have? What fraction of these are attention parameters? How large are our KV caches per token? *You can assume N\\cdot H=D and multi-head attention with int8 KVs.*

Click here for the answer.
1. The total parameters is roughly $L⋅(3DF+4DNH+D)+2DV$ . For the given numbers, this is $64⋅(3⋅4e3⋅16e3+4⋅4e3⋅4e3+4e3)+2⋅4e3⋅32e3=16e9$ , or 16B parameters.
2. The ratio of attention parameters to total parameters in general is $4DNH/(4DNH+3DF)=4D2/(4D2+12D2)=1/4$ . This gives us roughly 1/4 of parameters are used in attention.
3. Per token, our KV caches are $2⋅L⋅N⋅H=2⋅64⋅4096$ in int8, which is `512kB / token`.

**Question 2:** How many total FLOPs are required to perform A\[B <sub>X</sub>, D <sub>Y</sub>\] \* <sub>D</sub> W\[D <sub>Y</sub>, F\] on `{‘X': 4, ‘Y': 8, ‘Z': 4}`. How many FLOPs are performed by each TPU?

Click here for the answer.

The total “theoretical” FLOPs of the operation is $2⋅B⋅D⋅F$ . However, because the computation isn’t sharded across the Z dimension, we’re actually doing Z extra FLOPs, meaning $2⋅B⋅D⋅F⋅Z$ total FLOPs. Since the computation is sharded across the other dimensions, the total per-device is roughly $2⋅B⋅D⋅F/(X⋅Y)$ .

**Question 3:** How many FLOPs are involved in performing A\[I,J,K,L\] \* B\[I,J,M,N,O\] \\rightarrow C\[K,L,M,N,O\]?

Click here for the answer.

Following the rule above, we have I and J as contracting dimensions and K, L, M, N, and O as non-contracting dimensions. We have no “batching dimensions”, so this is just $2⋅I⋅J⋅K⋅L⋅M⋅N⋅O$ , the sum of all the axes. If we had a shared axis, it would only be counted once.

**Question 4:** What is the arithmetic intensity of self-attention (ignoring the Q/K/V/O projections)? *Give the answer as a function of the Q and KV lengths T and S.* At what context length is attention FLOPs-bound? Given the HBM bandwidth of our TPUs, plot the effective relative cost of attention to the FFW block as the context length grows.

Click here for the answer.

Self-attention requires loading the $Q$ , $K$ , and $V$ activations, then computing $softmax(Q⋅K)⋅V$ , then writing the result back to HBM. This will be done with Flash Attention so there are some caveats to this math, but basically in bf16 self-attention performs

$$
Q[B,T,N,H]→reshapeQ[B, T, K, G, H]⋅K[B, S, K, H]→O[B, T, S, K, G]
$$
 
$$
U=softmaxS(O[B, T, S, K, G])
$$
 
$$
U[B, T, S, K, G]⋅V[B, S, K, H]→X[B, T, K, G, H]
$$

So our total bytes is $2∗sizeof(Q)+2∗sizeof(K or V)=4BTNH+4BSKH=4BHK∗(TG+S)$ , total FLOPs is $4BTSNH+O(BTSN)$ and the arithmetic intensity is $4BTSKGH/(4BHK∗(TG+S))$ .

So basically, during prefill we have $S=T$ so we have an arithmetic intensity of $4BT2KGH/4BHKT⋅(G+1)=TG/(G+1)=O(T)$ . During generation, $T=1$ so we have $4BSKGH/(4BHK⋅(G+S))=SG/(G+S)→G$ assuming $S$ is very large. Depending on how you interpret the question, during prefill or training self-attention is compute bound at S=240 assuming no sequence sharding. During generation, we are never compute bound because $G$ is small. Nonetheless, however, you can see that increasing $G$ leads to us being closer to compute bound.

**Question 5:** At what sequence length are self-attention FLOPs equal to the QKVO projection FLOPs?

Click here for the answer.

This is purely a question of when $24BTDNH==12BT2NH$ . Simplifying we get $2D=T$ , so e.g. for $D=4096$ , this is $8192$ . This tells us that for most reasonable context lengths, matmul FLOPs are greater.

**Question 6:** Say we only save the output of each of the 7 main matmuls in a Transformer layer during our forward pass (Q, K, V, O + the three FFW matrices). How many extra FLOPs do we need to “rematerialize” during the backwards pass?

**Question 7:** DeepSeek v3 says it was trained for 2.79M H800 hours on 14.8T tokens ([source](https://arxiv.org/pdf/2412.19437v1)). Given that it has 37B activated parameters, roughly what hardware utilization did they achieve? *Hint: note that they used FP8 FLOPs without structured sparsity.*

Click here for the answer.

From the spec sheet [here](https://lenovopress.lenovo.com/lp1814.pdf), we find 3,026 TFLOPs/s of FP8 performance with sparsity, or typically half this (`1.513e15` FLOPs/s) without sparsity. 2.79M H800 hours means `2.79e6 * 1.513e15 * 60 * 60 = 1.52e25` total FLOPs. Given the activated parameter count of 37B, this training run should have used about `6 * 37e9 * 14.8e12 = 3.3e24` FLOPs. That means the FLOPs utilization is about `3.3e24 / 1.52e25 = 21.7%`.

**Question 8:** Mixture of Experts (MoE) models have E copies of a standard dense MLP block, and each token activates k of these experts. What batch size in tokens is required to be compute-bound for an MoE with weights in int8 on TPU v5e? For DeepSeek, which has 256 (routed) experts and k=8, what is this number?

Click here for the answer.

Because we have E copies of each expert, in int8, we need to load E \\cdot D \\cdot F bytes. Because each token activates k experts, we have 2\\cdot k \\cdot B \\cdot D \\cdot F FLOPs. To be compute-bound with bfloat16 FLOPs, we need an arithmetic intensity over 240 which happens when (2\\cdot k \\cdot BDF) / EDF > 240 or k \\cdot B / E > 120.

Therefore, we need B > 120 \\cdot E / k to be compute bound. For DeepSeek, this gives us B > 120 \\cdot 256 / 8 = 3840. This is a remarkably large batch size at generation time.

The traditional objection to scaling Transformers to very long context is that the attention FLOPs and memory usage scale quadratically with context length. While it’s true that the attention QK product has shape \[B, S, T, N\] where B is the batch size, S and T are the Q and K sequence dims, and N is the number of heads, this claim comes with some serious caveats:

1. As we noted in Section 4, even though this is quadratic, the attention FLOPs only dominated when $S>8⋅D$ , and especially during training the memory of a single attention matrix is small compared to all of the weights and activation checkpoints living in memory, especially when sharded.
2. We don’t need to materialize the full attention matrix in order to compute attention! We can compute local sums and maxes and avoid ever materializing more than a small chunk of the array. While the total FLOPs is still quadratic, we drastically reduce memory pressure.

This second observation was first made by [Rabe et al. 2021](https://arxiv.org/abs/2112.05682) and later in the [Flash Attention paper](https://arxiv.org/abs/2205.14135) (Dao et al. 2022). The basic idea is to compute the attention in chunks of K/V, where we compute the local softmax and some auxiliary statistics, then pass them onto the next chunk which combines them with its local chunk. Specifically, we compute

1. **M:** The running max of $q⋅k$ over the sequence dimension
2. **O:** The running full attention softmax over the sequence dimension
3. **L:** The running denominator $∑i(q⋅ki−running max)$

With these, we can compute the new max, the new running sum, and the new output with only a constant amount of memory. To give a sketchy description of how this works, attention is roughly this operation:

$$
Attn(Q,K,V)=∑iexp⁡(Q⋅Ki−maxjQ⋅Kj)Vi∑lexp⁡(Q⋅Kl−maxjQ⋅Kj)
$$

The max is subtracted for numerical stability and can be added without affecting the outcome since $∑iexp⁡(ai+b)=exp⁡(b)∑exp⁡(a)$ . Looking just at the denominator above, if we imagine having two contiguous chunks of key vectors, $K1$ and $K2$ and we compute the local softmax sums $L1$ and $L2$ for each

$$
L1=∑iexp⁡(Q⋅Ki1−maxjQ⋅Kj1)
$$
 
$$
L2=∑iexp⁡(Q⋅Ki2−maxjQ⋅Kj1)
$$

Then we can combine these into the full softmax sum for these two chunks together by using

$$
Lcombined=exp⁡(M1−max(M1,M2))⋅L1+exp⁡(M2−max(M1,M2))⋅L2
$$

where

$$
M1=maxjQ⋅Kj1 and M2=maxjQ⋅Kj2
$$

This can be done for the full softmax as well, giving us a way of accumulating arbitrarily large softmax sums. Here’s the full algorithm from the Flash Attention paper.

![](https://jax-ml.github.io/scaling-book/assets/img/flash-algo.png)

From a hardware standpoint, this lets us fit our chunk of Q into VMEM (what the algorithm above calls on-chip SRAM) so we only have to load the KV chunks on each iteration, reducing the arithmetic intensity. We can also keep the running statistics in VMEM.

One last subtle point worth emphasizing is an attention softmax property that’s used to make the Flash VJP (reverse mode derivative) calculation practical for training. If we define an intermediate softmax array as:

$$
Sij=eτqi⋅kj∑keτqi⋅kj
$$

In attention, we obtain *dS* from reverse-mode *dO* and *V* arrays:

$$
dSij=dOid⋅dVjd=∑ddOidVjd
$$

During the backpropagation of this gradient to Q and K

$$
d(qi⋅kj)=(dSij−Sij⋅jdSij)Sij
$$

We exploit an identity that allows us to exchange a contraction along the large key **length** dimension with a local contraction along the feature **depth** dimension.

$$
Sij⋅jdSij=∑jeτqi⋅kj∑keτqi⋅kk∑ddOidVjd=∑ddOid∑jeτqi⋅kj∑keτqi⋅kkVjd=∑ddOidOid=dOid⋅dOid
$$

This replacement is crucial for being able to implement a sequence-block *local* calculation for the VJP, and enables further clever sharding schemes like ring attention.

### Footnotes

1. Technically, this only happens if we are data or sequence sharded along the same axis as our experts.

### References

[^1]: GLU Variants Improve Transformer  
Shazeer, N., 2020. arXiv \[cs.LG\].

[^2]: Fast Transformer decoding: One write-head is all you need  
Noam, S., 2019. arXiv \[cs.NE\].

[^3]: GQA: Training generalized multi-query transformer models from multi-head checkpoints  
Ainslie, J., Lee-Thorp, J., de Jong, M., Zemlyanskiy, Y., Lebrón, F. and Sanghai, S., 2023. arXiv \[cs.CL\].

[^4]: Outrageously large neural networks: The Sparsely-Gated Mixture-of-experts layer  
Shazeer, N., Mirhoseini, A., Maziarz, K., Davis, A., Le, Q., Hinton, G. and Dean, J., 2017. arXiv \[cs.LG\].  