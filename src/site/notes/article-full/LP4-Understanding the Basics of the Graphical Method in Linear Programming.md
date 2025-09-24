---
{"dg-publish":true,"permalink":"/article-full/lp-4-understanding-the-basics-of-the-graphical-method-in-linear-programming/","title":"Understanding the Basics of the Graphical Method in Linear Programming • SLM (Self Learning Material) for MBA","tags":["article","full"]}
---

# Understanding the Basics of the Graphical Method in Linear Programming • SLM (Self Learning Material) for MBA  

Source: [slm.mba](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/)  

#LinearProgramming #GraphicalMethod #Optimization #OperationsResearch  

[Skip to content](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#wp--skip-link--target)

Have you ever wondered how businesses decide the perfect mix of products to manufacture, or how logistics companies determine the most efficient delivery routes? The answer often lies in linear programming, and one of the most intuitive ways to understand this powerful optimization technique is through the graphical method. This visual approach transforms complex mathematical problems into clear, understandable diagrams that reveal optimal solutions at a glance.

#### Table of Contents

- [What is the graphical method in linear programming?](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#what-is-the-graphical-method-in-linear-programming)
- [Converting constraints into graphical representations](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#converting-constraints-into-graphical-representations)
- [From inequalities to equations](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#from-inequalities-to-equations)
- [Determining the feasible side](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#determining-the-feasible-side)
- [Understanding feasible regions and convex sets](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#understanding-feasible-regions-and-convex-sets)
- [Defining the feasible region](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#defining-the-feasible-region)
- [Properties of convex sets](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#properties-of-convex-sets)
- [Extreme points and optimal solutions](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#extreme-points-and-optimal-solutions)
- [What are extreme points?](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#what-are-extreme-points)
- [Finding optimal solutions graphically](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#finding-optimal-solutions-graphically)
- [Special cases and considerations](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#special-cases-and-considerations)
- [Practical applications and limitations](https://slm.mba/mmpo-001/basics-of-graphical-method-linear-programming/#practical-applications-and-limitations)

## What is the graphical method in linear programming?

The graphical method is a visual technique used to solve linear programming problems with two decision variables. Think of it as creating a map where each constraint becomes a boundary line, and the optimal solution sits at a specific corner of the region where all constraints overlap. This method works exceptionally well for problems involving two variables because we can easily plot them on a standard x-y coordinate system.

Consider a simple example: a bakery wants to maximize profit by deciding how many chocolate cakes and vanilla cakes to bake daily. The graphical method would help visualize the constraints like available flour, sugar, and oven time, ultimately pointing to the exact combination that yields maximum profit.

## Converting constraints into graphical representations

The magic of the graphical method begins with transforming mathematical inequalities into visual boundaries. Every constraint in a linear programming problem represents a limitation or requirement that must be satisfied. When we plot these constraints on a graph, they become straight lines that divide the coordinate plane into different regions.

### From inequalities to equations

To plot a constraint graphically, we first convert the inequality into an equation by replacing the inequality sign with an equals sign. For instance, if we have a constraint like 2x + 3y ≤ 12, we first plot the line 2x + 3y = 12. This line represents the boundary of our constraint.

To draw this line, we need at least two points. The easiest approach is to find the x-intercept and y-intercept:

**Finding the x-intercept:** Set y = 0 and solve for x. In our example, 2x + 3(0) = 12, so x = 6. The x-intercept is (6, 0).

**Finding the y-intercept:** Set x = 0 and solve for y. Here, 2(0) + 3y = 12, so y = 4. The y-intercept is (0, 4).

Once we have these two points, we can draw a straight line connecting them. The next step is determining which side of the line satisfies our original inequality.

### Determining the feasible side

After plotting the boundary line, we need to identify which side represents the feasible region for that constraint. A simple test point method works perfectly here. Choose any point not on the line (the origin (0,0) is often convenient if it’s not on the line) and substitute its coordinates into the original inequality.

If the inequality holds true, then the side containing the test point is feasible. If not, the opposite side is feasible. We typically shade the feasible side or use arrows to indicate the direction of feasibility.

## Understanding feasible regions and convex sets

The feasible region is where the real excitement happens in linear programming. It’s the area on our graph where all constraints are simultaneously satisfied, representing all possible solutions that meet our problem’s requirements.

### Defining the feasible region

When we plot multiple constraints on the same graph, their intersection creates the feasible region. This region contains every combination of decision variables that satisfies all constraints simultaneously. Think of it as the “sweet spot” where all your business limitations and requirements are met.

For example, if our bakery has constraints on flour availability, oven capacity, and minimum production requirements, the feasible region would show all possible combinations of chocolate and vanilla cakes that respect these limitations.

### Properties of convex sets

The feasible region in linear programming problems always forms what mathematicians call a “ convex set.” A convex set has a special property: if you take any two points within the set and draw a straight line between them, every point on that line also belongs to the set.

Why does this matter? Convex sets have predictable shapes – they’re typically polygons with no “indentations” or “caves.” This property is crucial because it guarantees that our optimal solution will always be found at one of the corners (vertices) of this polygon, never somewhere in the middle of an edge or inside the region.

**Bounded vs. unbounded regions:** Sometimes our feasible region extends infinitely in one or more directions, creating an unbounded region. While this might seem problematic, it often still leads to optimal solutions, especially when we’re maximizing profits or minimizing costs with appropriate constraints.

## Extreme points and optimal solutions

Here’s where the graphical method reveals its true power: the optimal solution to any linear programming problem always occurs at an extreme point (corner) of the feasible region. This fundamental principle, known as the corner point theorem, makes solving linear programming problems surprisingly straightforward.

### What are extreme points?

Extreme points are the corners or vertices of the feasible region where two or more constraint lines intersect. These points represent unique combinations of decision variables that sit exactly on the boundary of multiple constraints simultaneously.

In our bakery example, an extreme point might represent producing exactly the maximum number of chocolate cakes allowed by flour constraints while also hitting the exact limit of oven capacity. These corner points are special because they represent the most “extreme” feasible solutions – you can’t move in any direction from these points without either violating a constraint or moving away from optimality.

### Finding optimal solutions graphically

To find the optimal solution using the graphical method, we follow a systematic approach:

**Step 1: Identify all extreme points** by finding the coordinates where constraint lines intersect within the feasible region.

**Step 2: Evaluate the objective function** at each extreme point by substituting the coordinates into our objective function (whether we’re maximizing profit or minimizing cost).

**Step 3: Compare the results** to identify which extreme point gives us the best value for our objective function.

Alternatively, we can use the iso-profit (or iso-cost) line method. We plot lines representing constant values of our objective function and gradually move these lines in the direction of improvement until we reach the last point in the feasible region that the line touches. This point is our optimal solution.

### Special cases and considerations

The graphical method also helps us identify special situations that can occur in linear programming:

**Multiple optimal solutions:** When the objective function line is parallel to a constraint boundary, we might have infinite optimal solutions along an entire edge of the feasible region.

**Unbounded solutions:** If the feasible region extends infinitely in the direction of improvement, we might have an unbounded solution, indicating that our problem formulation needs revision.

**Infeasible problems:** Sometimes constraints contradict each other, creating no feasible region at all. The graphical method makes this immediately apparent when constraint lines don’t create any overlapping area.

## Practical applications and limitations

The graphical method shines in educational settings and small-scale problems where visualization aids understanding. It’s particularly valuable for:

**Problem verification:** Even when using computer software for larger problems, sketching a quick graph can help verify that your constraints make sense and that your solution is reasonable.

**Sensitivity analysis:** You can easily see how changing a constraint affects the feasible region and potentially the optimal solution.

**Communication tool:** Graphs make it easier to explain optimization results to stakeholders who might not understand complex mathematical formulations.

However, the graphical method has clear limitations. It only works effectively for problems with two decision variables. Once you have three or more variables, visualization becomes impractical, and you’ll need to rely on algebraic methods like the simplex algorithm.

**What do you think?** How might the visual nature of the graphical method change the way businesses approach optimization problems? Can you think of real-world scenarios where being able to “see” the constraints and optimal solution would be particularly valuable for decision-making?

How useful was this post?

Click on a star to rate it!

Average rating 0 / 5. Vote count: 0

No votes so far! Be the first to rate this post.

[PDF](https://slm.mba/?print-my-blog=1&post-type=post&statuses%5B%5D=publish&rendering_wait=0&columns=1&font_size=normal&image_size=medium&links=include&show_site_title=1&show_site_tagline=1&show_site_url=1&show_date_printed=1&show_title=1&show_url=1&show_date=1&show_categories=1&show_featured_image=1&show_content=1&show_divider=1&pmb_f=pdf&pmb-post=8336)

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