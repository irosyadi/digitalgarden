---
{"dg-publish":true,"permalink":"/article-full/lp-5-step-by-step-guide-to-graphing-linear-programming-problems/","title":"Step-by-Step Guide to Graphing Linear Programming Problems • SLM (Self Learning Material) for MBA","tags":["article","full"]}
---

# Step-by-Step Guide to Graphing Linear Programming Problems • SLM (Self Learning Material) for MBA  

Source: [slm.mba](https://slm.mba/mmpo-001/graphing-linear-programming-guide/)  

#LinearProgramming #Optimization #OperationsResearch #GraphicalMethod  

[Skip to content](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#wp--skip-link--target)

Have you ever wondered how companies decide the perfect mix of products to manufacture, or how airlines determine the most profitable flight schedules? The answer often lies in linear programming, a powerful mathematical technique that helps solve optimization problems. At the heart of this method is the graphical approach – a visual way to find the best solution by literally drawing your way to success. Let’s explore how to master the art of graphing linear programming problems step by step.

#### Table of Contents

- [Setting the foundation: Formulating your linear programming problem](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#setting-the-foundation-formulating-your-linear-programming-problem)
- [Bringing mathematics to life: Plotting constraints on your graph](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#bringing-mathematics-to-life-plotting-constraints-on-your-graph)
- [Setting up your coordinate system](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#setting-up-your-coordinate-system)
- [Converting constraints into boundary lines](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#converting-constraints-into-boundary-lines)
- [Identifying the feasible region](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#identifying-the-feasible-region)
- [The moment of truth: Finding your optimal solution](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#the-moment-of-truth-finding-your-optimal-solution)
- [Locating corner points](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#locating-corner-points)
- [Evaluating the objective function](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#evaluating-the-objective-function)
- [Special cases to watch for](https://slm.mba/mmpo-001/graphing-linear-programming-guide/#special-cases-to-watch-for)

## Setting the foundation: Formulating your linear programming problem

Before you can draw anything meaningful, you need to translate your real-world problem into mathematical language. Think of this as creating a recipe – you need to identify your ingredients (variables) and your cooking instructions (constraints and objectives).

Let’s work with a practical example. Imagine you own a small bakery that makes two types of cookies: chocolate chip and oatmeal raisin. You have limited flour, sugar, and time, but you want to maximize your profit. Here’s how we convert this scenario into mathematical terms:

**Step 1: Define your decision variables.** Let x represent the number of dozens of chocolate chip cookies, and y represent the number of dozens of oatmeal raisin cookies you’ll make.

**Step 2: Write your objective function.** If chocolate chip cookies give you $3 profit per dozen and oatmeal raisin gives $2 profit per dozen, your objective function becomes: Maximize Z = 3x + 2y

**Step 3: Establish your constraints.** Perhaps you have 100 pounds of flour, and chocolate chip cookies need 2 pounds per dozen while oatmeal raisin needs 1 pound per dozen. This gives you the constraint: 2x + y ≤ 100. Similarly, you might have time constraints, sugar limitations, and the obvious non-negativity constraints (x ≥ 0, y ≥ 0).

The key is being systematic and ensuring every limitation in your real-world scenario becomes a mathematical inequality. Remember, linear programming works only when all relationships are linear – no squares, cubes, or other complex mathematical operations.

## Bringing mathematics to life: Plotting constraints on your graph

Now comes the exciting part – transforming those mathematical expressions into visual representations. Think of your graph as a map where each constraint draws a boundary, and together they create a territory where your solution must live.

### Setting up your coordinate system

**Choose appropriate scales.** Look at your constraint values to determine reasonable scales for your x and y axes. If your constraints involve numbers in the hundreds, don’t make each grid square represent 1 unit – you’ll run out of paper! Instead, let each square represent 5 or 10 units.

**Label your axes clearly.** Your x-axis represents your first decision variable, and your y-axis represents your second. In our bakery example, the x-axis shows dozens of chocolate chip cookies, and the y-axis shows dozens of oatmeal raisin cookies.

### Converting constraints into boundary lines

Each constraint inequality becomes a straight line on your graph. Here’s the process:

**Convert inequality to equality.** Take your constraint 2x + y ≤ 100 and temporarily make it 2x + y = 100. This line represents the boundary of your constraint.

**Find two points on the line.** The easiest approach is to find where the line crosses each axis. When x = 0, then y = 100. When y = 0, then 2x = 100, so x = 50. Plot these points (0, 100) and (50, 0) and draw a straight line connecting them.

**Determine which side satisfies the inequality.** Pick any point not on the line – (0, 0) is usually convenient. Substitute into your original inequality: 2(0) + 0 ≤ 100? Yes, 0 ≤ 100 is true. This means the area containing (0, 0) satisfies the constraint. Shade this region lightly or mark it with arrows.

Repeat this process for every constraint. Don’t forget your non-negativity constraints (x ≥ 0, y ≥ 0) – these simply mean you only consider the first quadrant of your graph.

### Identifying the feasible region

The magic happens when you look at where all your shaded regions overlap. This intersection – called the feasible region – represents all possible solutions that satisfy every constraint simultaneously. It’s like finding the sweet spot where all your limitations are respected.

The feasible region in linear programming problems typically forms a polygon. Sometimes it might be unbounded (extending infinitely in one direction), and occasionally, if your constraints are contradictory, there might be no feasible region at all.

## The moment of truth: Finding your optimal solution

Here’s where linear programming reveals its elegant simplicity. The optimal solution – the point that maximizes or minimizes your objective function – always occurs at a corner point (vertex) of your feasible region. This isn’t coincidence; it’s a mathematical certainty known as the fundamental theorem of linear programming.

### Locating corner points

**Visual identification.** Look at your feasible region and identify every corner. These occur where two constraint lines intersect, where a constraint line meets an axis, or where two axes meet (the origin).

**Mathematical calculation.** For precision, calculate the exact coordinates of each corner point by solving the system of equations formed by the intersecting lines. For instance, if lines 2x + y = 100 and x + 2y = 80 intersect, solve this system simultaneously.

From 2x + y = 100, we get y = 100 – 2x. Substituting into the second equation: x + 2(100 – 2x) = 80, which simplifies to x + 200 – 4x = 80, giving us -3x = -120, so x = 40. Therefore, y = 100 – 2(40) = 20. The intersection point is (40, 20).

### Evaluating the objective function

Now test your objective function at each corner point:

**Calculate systematically.** If your objective function is Z = 3x + 2y, substitute each corner point’s coordinates. For point (40, 20): Z = 3(40) + 2(20) = 120 + 40 = 160.

**Compare all values.** The corner point that gives the highest value (for maximization problems) or lowest value (for minimization problems) is your optimal solution.

**Interpret your results.** Don’t just state numbers – translate back to your original problem. If (40, 20) is optimal with Z = 160, this means making 40 dozen chocolate chip cookies and 20 dozen oatmeal raisin cookies will give you the maximum profit of $160.

### Special cases to watch for

Sometimes you might encounter unique situations. If two adjacent corner points give the same optimal value, you have multiple optimal solutions – any point on the line segment between them is also optimal. If your feasible region is unbounded in the direction that improves your objective function, the problem has no finite optimal solution.

The graphical method brilliantly transforms abstract mathematical optimization into a concrete, visual process. By following these systematic steps – formulating equations, plotting constraints, and evaluating corner points – you can solve complex resource allocation problems with nothing more than graph paper and careful calculation.

**What do you think?** Can you imagine applying this graphical approach to optimize your own daily decisions, like balancing study time between different subjects? How might businesses use this method to make strategic decisions about product mixes or resource allocation?

How useful was this post?

Click on a star to rate it!

Average rating 0 / 5. Vote count: 0

No votes so far! Be the first to rate this post.

[PDF](https://slm.mba/?print-my-blog=1&post-type=post&statuses%5B%5D=publish&rendering_wait=0&columns=1&font_size=normal&image_size=medium&links=include&show_site_title=1&show_site_tagline=1&show_site_url=1&show_date_printed=1&show_title=1&show_url=1&show_date=1&show_categories=1&show_featured_image=1&show_content=1&show_divider=1&pmb_f=pdf&pmb-post=8337)

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