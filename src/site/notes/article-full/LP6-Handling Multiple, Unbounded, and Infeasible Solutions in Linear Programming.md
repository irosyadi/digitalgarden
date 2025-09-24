---
{"dg-publish":true,"permalink":"/article-full/lp-6-handling-multiple-unbounded-and-infeasible-solutions-in-linear-programming/","title":"Handling Multiple, Unbounded, and Infeasible Solutions in Linear Programming • SLM (Self Learning Material) for MBA","tags":["article","full"]}
---

# Handling Multiple, Unbounded, and Infeasible Solutions in Linear Programming • SLM (Self Learning Material) for MBA  

Source: [slm.mba](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/)  

#LinearProgramming #Optimization #InfeasibleSolutions #UnboundedSolutions  

[Skip to content](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#wp--skip-link--target)

Linear programming doesn’t always give us neat, single answers wrapped in a bow. Sometimes we encounter situations where problems have multiple optimal solutions, solutions that stretch to infinity, or worse yet, no solutions at all. These special cases – multiple, unbounded, and infeasible solutions – might seem like mathematical oddities, but they’re actually common in real-world business scenarios. Understanding these cases is crucial for anyone working with optimization problems, as they can reveal important insights about your business constraints and objectives.

#### Table of Contents

- [When one solution isn’t enough: Multiple optimal solutions](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#when-one-solution-isnt-enough-multiple-optimal-solutions)
- [Recognizing multiple solutions graphically](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#recognizing-multiple-solutions-graphically)
- [Real-world implications of multiple solutions](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#real-world-implications-of-multiple-solutions)
- [When solutions reach for infinity: Unbounded problems](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#when-solutions-reach-for-infinity-unbounded-problems)
- [Understanding unbounded solutions through examples](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#understanding-unbounded-solutions-through-examples)
- [Dealing with unbounded solutions in practice](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#dealing-with-unbounded-solutions-in-practice)
- [When no solution exists: Infeasible problems](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#when-no-solution-exists-infeasible-problems)
- [Common causes of infeasibility](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#common-causes-of-infeasibility)
- [Real-world example of infeasibility](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#real-world-example-of-infeasibility)
- [Resolving infeasible problems](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#resolving-infeasible-problems)
- [Practical tips for handling special cases](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming/#practical-tips-for-handling-special-cases)

## When one solution isn’t enough: Multiple optimal solutions

Imagine you’re running a bakery and trying to maximize profit from selling cookies and cakes. After setting up your linear programming model, you discover something interesting – there isn’t just one way to achieve maximum profit, but infinitely many ways! This happens when we encounter multiple optimal solutions.

Multiple optimal solutions occur when the objective function line is parallel to one of the constraint lines that forms the boundary of the feasible region. Think of it like this: instead of the objective function touching the feasible region at just one corner point, it lies flat against an entire edge of the region. Every point along this edge gives the same optimal value.

### Recognizing multiple solutions graphically

When you’re solving a linear programming problem graphically, multiple solutions reveal themselves quite clearly. As you move the objective function line toward the optimal position, you’ll notice it becomes parallel to one of the constraint boundaries. Instead of touching at a single point, the objective function line coincides with an entire edge of the feasible region.

For example, consider a company producing two products with the objective of maximizing profit. If the profit per unit for both products creates an objective function that’s parallel to a binding constraint, then any combination of products along that constraint line will yield the same maximum profit.

### Real-world implications of multiple solutions

Multiple solutions aren’t just mathematical curiosities – they offer valuable flexibility in decision-making. When you have multiple optimal solutions, you can choose the one that best fits other considerations not captured in your model. Maybe one solution requires less labor overtime, or another solution uses more environmentally friendly processes. This flexibility can be a significant advantage in practical business applications.

## When solutions reach for infinity: Unbounded problems

Sometimes linear programming problems seem to suggest that you can achieve infinite profit or minimize costs to negative infinity. These are called unbounded solutions, and while they might sound like a business owner’s dream, they actually indicate a problem with your model formulation.

An unbounded solution occurs when the feasible region extends infinitely in the direction that improves the objective function. Graphically, this means there’s no constraint preventing you from moving as far as you want in the direction of improvement.

### Understanding unbounded solutions through examples

Consider a manufacturing problem where you want to maximize profit from two products. If your constraints don’t properly limit production capacity, raw materials, or market demand, you might end up with an unbounded solution. The mathematical model would suggest you can produce infinite quantities and earn infinite profit – clearly unrealistic!

For instance, if a company’s linear programming model for production planning doesn’t include capacity constraints or market demand limits, the solution might suggest producing unlimited quantities of the most profitable product. This unbounded result signals that important real-world limitations haven’t been captured in the model.

### Dealing with unbounded solutions in practice

When you encounter an unbounded solution, it’s time to revisit your problem formulation. Ask yourself: What constraints am I missing? In the real world, there are always limitations – production capacity, available materials, market size, labor hours, or budget restrictions. An unbounded solution is your model’s way of telling you that these realistic constraints need to be included.

The key is to identify and add the missing constraints that reflect real-world limitations. Once you include these forgotten constraints, your unbounded problem typically becomes a well-defined optimization problem with a finite optimal solution.

## When no solution exists: Infeasible problems

Perhaps the most frustrating situation in linear programming is discovering that your problem has no feasible solution at all. This happens when the constraints are so restrictive or contradictory that no point can satisfy all of them simultaneously. We call this an infeasible problem.

Infeasibility occurs when the intersection of all constraint regions is empty – there’s literally no point that satisfies every constraint. Graphically, you’ll see constraint lines that don’t overlap in any common area, leaving no feasible region where a solution could exist.

### Common causes of infeasibility

Infeasible problems often arise from conflicting constraints that contradict each other. For example, imagine a production scenario where one constraint requires producing at least 100 units of a product, while another constraint limits production to no more than 50 units of the same product. These constraints directly contradict each other, making the problem infeasible.

Another common cause is overly restrictive constraints that, while not directly contradictory, combine to eliminate all possible solutions. This might happen when quality requirements, budget limitations, and production capacities are all set so strictly that no production plan can satisfy them all.

### Real-world example of infeasibility

Consider a logistics company trying to optimize delivery routes with the following constraints: all deliveries must be completed within 4 hours, each truck can carry a maximum of 10 packages, fuel costs must not exceed $50, and all 100 packages must be delivered using only 2 trucks. These constraints might be infeasible because 2 trucks carrying 10 packages each can only handle 20 packages, not 100.

### Resolving infeasible problems

When faced with infeasibility, you have several options. First, examine your constraints carefully to identify conflicts or overly restrictive conditions. You might need to relax some constraints, perhaps accepting slightly lower quality standards or increasing budget limits. Alternatively, you might need to reconsider your objectives or add more resources to make the problem feasible.

Sometimes infeasibility reveals important insights about your business situation. It might highlight unrealistic expectations, insufficient resources, or the need for operational changes. In this sense, discovering infeasibility can be just as valuable as finding an optimal solution.

## Practical tips for handling special cases

When working with linear programming problems, always be prepared for these special cases. Start by carefully examining your problem formulation to ensure all relevant constraints are included and realistic. If you encounter multiple solutions, consider additional criteria to help choose among the alternatives. When facing unbounded solutions, look for missing constraints that reflect real-world limitations. For infeasible problems, systematically examine constraints to identify conflicts or unrealistic restrictions.

Remember that these special cases often provide valuable insights into your business situation. Multiple solutions offer flexibility, unbounded solutions reveal missing constraints, and infeasible problems highlight unrealistic expectations or insufficient resources. Each case teaches us something important about the problem we’re trying to solve.

**What do you think?** Have you encountered situations in your studies or work where constraints seemed impossible to satisfy simultaneously? How might understanding these special cases help you better formulate and solve real-world optimization problems?

How useful was this post?

Click on a star to rate it!

Average rating 0 / 5. Vote count: 0

No votes so far! Be the first to rate this post.

[PDF](https://slm.mba/?print-my-blog=1&post-type=post&statuses%5B%5D=publish&rendering_wait=0&columns=1&font_size=normal&image_size=medium&links=include&show_site_title=1&show_site_tagline=1&show_site_url=1&show_date_printed=1&show_title=1&show_url=1&show_date=1&show_categories=1&show_featured_image=1&show_content=1&show_divider=1&pmb_f=pdf&pmb-post=8338)

---

### Comments

### Leave a Reply

#### Operations Research

**1 Operations Research-An Overview**

1. [Introduction](https://slm.mba/mmpo-001/operations-research-introductory-guide)
2. [History of O.R.](https://slm.mba/mmpo-001/evolution-operations-research-wwii-modern-applications)
3. [Approach, Techniques and Tools](https://slm.mba/mmpo-001/core-techniques-operations-research)
4. [Phases and Processes of O.R. Study](https://slm.mba/mmpo-001/phases-operations-research-analysis-implementation)
5. [Typical Applications of O.R.](https://slm.mba/mmpo-001/real-world-applications-of-operations-research)
6. [Limitations of Operations Research](https://slm.mba/mmpo-001/challenges-in-operations-research-limitations)
7. [Models in Operations Research](https://slm.mba/mmpo-001/exploring-models-in-operations-research)
8. [O.R. in the Real World](https://slm.mba/mmpo-001/operations-research-successful-case-studies)

**2 Linear Programming- Formulation and Graphical Method**

1. [Introduction](https://slm.mba/mmpo-001/linear-programming-decision-making)
2. [General Formulation of Linear Programming Problem](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem)
3. [Optimisation Models](https://slm.mba/mmpo-001/optimization-models-linear-programming-maximization-minimization)
4. [Basics of Graphic Method](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming)
5. [Important Steps to Draw the Graph](https://slm.mba/mmpo-001/graphing-linear-programming-guide)
6. [Multiple, Unbounded Solution, and Infeasible Problems](https://slm.mba/mmpo-001/handling-multiple-unbounded-infeasible-solutions-linear-programming)
7. [Solving Linear Programming Graphically Using Computer](https://slm.mba/mmpo-001/computer-software-linear-programming-graphically)
8. [Application of Linear Programming in Business and Industry](https://slm.mba/mmpo-001/linear-programming-business-industry)

**3 Linear Programming-Simplex Method**

1. [Principle of Simplex Method](https://slm.mba/mmpo-001/simplex-method-basics-linear-programming)
2. [Computational Aspect of Simplex Method](https://slm.mba/mmpo-001/simplex-method-computation-guide)
3. [Simplex Method with Several Decision Variables](https://slm.mba/mmpo-001/simplex-method-multi-variable-linear-programming)
4. [Two Phase and M-method](https://slm.mba/mmpo-001/two-phase-m-method-simplex)
5. [Multiple Solution, Unbounded Solution and Infeasible Problem](https://slm.mba/mmpo-001/linear-programming-special-cases)
6. [Sensitivity Analysis](https://slm.mba/mmpo-001/sensitivity-analysis-in-linear-programming)
7. [Dual Linear Programming Problem](https://slm.mba/mmpo-001/exploring-duality-in-linear-programming)

**4 Transportation Problem**

1. [Basic Feasible Solution of a Transportation Problem](https://slm.mba/mmpo-001/basic-feasible-solutions-transportation)
2. [Modified Distribution Method](https://slm.mba/mmpo-001/optimizing-transportation-problems-modi-method)
3. [Stepping Stone Method](https://slm.mba/mmpo-001/stepping-stone-method-transportation-costs)
4. [Unbalanced Transportation Problem](https://slm.mba/mmpo-001/solving-unbalanced-transportation-problems)
5. [Degenerate Transportation Problem](https://slm.mba/mmpo-001/degeneracy-transportation-problems-perturbation)
6. [Transhipment Problem](https://slm.mba/mmpo-001/transhipment-problems-logistics-supply-chain)
7. [Maximisation in a Transportation Problem](https://slm.mba/mmpo-001/solve-maximization-problems-transportation-models)

**5 Assignment Problem**

1. [Solution of the Assignment Problem](https://slm.mba/mmpo-001/step-by-step-guide-hungarian-method)
2. [Unbalanced Assignment Problem](https://slm.mba/mmpo-001/tackle-unbalanced-assignment-problems-in-operations-research)
3. [Problem with Some Infeasible Assignments](https://slm.mba/mmpo-001/dealing-with-infeasible-assignments)
4. [Maximization in an Assignment Problem](https://slm.mba/mmpo-001/maximizing-outcomes-assignment-strategies-solutions)
5. [Crew Assignment Problem](https://slm.mba/mmpo-001/optimizing-crew-assignments-minimize-waiting-times-transport-services)

**6 Application of Excel Solver to Solve LPP**

1. [Building Excel model for solving LPP: An Illustrative Example](https://slm.mba/mmpo-001/excel-model-for-linear-programming-step-by-step-example)
2. [Sensitivity Analysis in Excel Solver](https://slm.mba/mmpo-001/sensitivity-analysis-excel-solver-lpp)

**7 Goal Programming**

1. [Concepts of Goal Programming](https://slm.mba/mmpo-001/goal-programming-fundamentals)
2. [Goal Programming Model Formulation](https://slm.mba/mmpo-001/goal-programming-models-guide)
3. [Graphical Method of Goal Programming](https://slm.mba/mmpo-001/graphical-approach-to-solving-goal-programming-problems)
4. [The Simplex Method of Goal Programming](https://slm.mba/mmpo-001/simplex-method-goal-programming-guide)
5. [Using Excel Solver to Solve Goal Programming Models](https://slm.mba/mmpo-001/goal-programming-excel-solver-guide)
6. [Application Areas of Goal Programming](https://slm.mba/mmpo-001/real-world-applications-goal-programming-management)

**8 Integer Programming**

1. [Introduction](https://slm.mba/mmpo-001/integer-programming-essential-decision-making)
2. [Some Integer Programming Formulation Techniques](https://slm.mba/mmpo-001/integer-programming-model-techniques)
3. [Binary Representation of General Integer Variables](https://slm.mba/mmpo-001/simplifying-integer-variables-with-binary)
4. [Unimodularity](https://slm.mba/mmpo-001/unimodularity-integer-programming-optimal-solutions)
5. [Cutting Plane Method](https://slm.mba/mmpo-001/step-by-step-guide-cutting-plane-method-integer-programming)
6. [Branch and Bound Method](https://slm.mba/mmpo-001/branch-and-bound-method-for-integer-programming-solutions)
7. [Solver Solution](https://slm.mba/mmpo-001/solve-integer-programming-excel)

**9 Dynamic Programming**

1. [Introduction](https://slm.mba/mmpo-001/dynamic-programming-multistage-decision-making)
2. [Dynamic Programming Methodology: An Example](https://slm.mba/mmpo-001/dynamic-programming-shortest-route)
3. [Definitions and Notations](https://slm.mba/mmpo-001/key-definitions-notations-in-dynamic-programming)
4. [Dynamic Programming Applications](https://slm.mba/mmpo-001/real-world-applications-of-dynamic-programming)

**10 Non-Linear Programming**

1. [Introduction](https://slm.mba/mmpo-001/non-linear-programming-overview)
2. [Solution of a Non-Linear Programming Problem](https://slm.mba/mmpo-001/non-linear-programming-methods-challenges)
3. [Convex and Concave Functions](https://slm.mba/mmpo-001/convex-vs-concave-functions-in-non-linear-programming)
4. [Kuhn-Tucker Conditions for Constrained Optimisation](https://slm.mba/mmpo-001/kuhn-tucker-conditions-non-linear-problems)
5. [Quadratic Programming](https://slm.mba/mmpo-001/quadratic-programming-complex-optimization)
6. [Separable Programming](https://slm.mba/mmpo-001/separable-programming-non-linear-optimization)
7. [NLP Models with Solver](https://slm.mba/mmpo-001/using-solver-for-non-linear-programming-models-guide)

**11 Introduction to game theory and its Applications**

1. [Introduction](https://slm.mba/mmpo-001/game-theory-introduction-strategic-decision-making)
2. [Definitions and Explanation of Some Important Terms](https://slm.mba/mmpo-001/game-theory-terms-players-strategies-payoffs)
3. [Saddle Points](https://slm.mba/mmpo-001/saddle-points-game-theory-strategies)
4. [Dominance](https://slm.mba/mmpo-001/dominance-principle-simplify-game-theory-matrices)
5. [Mixed Strategies: Games Without Saddle Points](https://slm.mba/mmpo-001/mixed-strategies-game-theory)
6. [2xn Games](https://slm.mba/mmpo-001/solving-2xn-games-strategies)
7. [Exploiting an Opponent’s Mistakes](https://slm.mba/mmpo-001/exploit-opponent-mistakes-game-theory-advantage)

**12 Monte Carlo Simulation**

1. [Reasons for using simulation](https://slm.mba/mmpo-001/simulation-in-management-problems)
2. [Monte Carlo simulation](https://slm.mba/mmpo-001/monte-carlo-simulation-guide)
3. [Limitations of simulation](https://slm.mba/mmpo-001/limitations-of-simulation-in-decision-making)
4. [Steps in the simulation process](https://slm.mba/mmpo-001/effective-simulation-step-by-step-process)
5. [Some practical applications of simulation](https://slm.mba/mmpo-001/real-world-applications-simulation-management)
6. [Two typical examples of hand-computed simulation](https://slm.mba/mmpo-001/hand-computed-simulation-examples-in-queuing-and-inventory)
7. [Computer simulation](https://slm.mba/mmpo-001/computers-monte-carlo-simulation)

**13 Queueing Models**

1. [Characteristics of a Queueing Model](https://slm.mba/mmpo-001/key-features-queueing-models-explained)
2. [Notations and Symbols](https://slm.mba/mmpo-001/understanding-queueing-model-notations-guide)
3. [Statistical Methods in Queueing](https://slm.mba/mmpo-001/statistical-analysis-queueing-models)
4. [The M/M/1 System](https://slm.mba/mmpo-001/introduction-m-m-1-queueing-systems)
5. [The M/M/C System](https://slm.mba/mmpo-001/m-m-c-queueing-models-multi-server-scenarios)
6. [The M/Ek/1 System](https://slm.mba/mmpo-001/queueing-models-erlang-distribution-mek1-system)
7. [Decision Problems in Queueing](https://slm.mba/mmpo-001/queueing-models-decision-making-cost-optimization)
8. [Solved Problems](https://slm.mba/mmpo-001/solving-real-world-queueing-problems)  