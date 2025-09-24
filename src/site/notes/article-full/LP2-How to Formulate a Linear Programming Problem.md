---
{"dg-publish":true,"permalink":"/article-full/lp-2-how-to-formulate-a-linear-programming-problem/","title":"How to Formulate a Linear Programming Problem • SLM (Self Learning Material) for MBA","tags":["article","full"]}
---

# How to Formulate a Linear Programming Problem • SLM (Self Learning Material) for MBA  

Source: [slm.mba](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/)  

#LinearProgramming #Optimization #OperationsResearch #BusinessAnalytics  

[Skip to content](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#wp--skip-link--target)

Ever wondered how businesses decide the best way to allocate their limited resources to maximize profits or minimize costs? The answer often lies in linear programming, a powerful mathematical technique that helps solve optimization problems. At its core, every linear programming problem starts with proper formulation – the process of translating a real-world business scenario into mathematical language that computers can solve. Understanding how to formulate these problems correctly is your gateway to mastering one of the most practical tools in operations research.

#### Table of Contents

- [What exactly is linear programming formulation?](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#what-exactly-is-linear-programming-formulation)
- [Defining the objective function](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#defining-the-objective-function)
- [Maximization vs minimization objectives](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#maximization-vs-minimization-objectives)
- [Writing the objective function mathematically](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#writing-the-objective-function-mathematically)
- [Decision variables and their role](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#decision-variables-and-their-role)
- [Identifying decision variables](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#identifying-decision-variables)
- [Variable relationships and dependencies](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#variable-relationships-and-dependencies)
- [Understanding constraints and their mathematical representation](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#understanding-constraints-and-their-mathematical-representation)
- [Types of constraints](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#types-of-constraints)
- [Writing constraints mathematically](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#writing-constraints-mathematically)
- [Complete mathematical representation](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#complete-mathematical-representation)
- [Standard LP formulation structure](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#standard-lp-formulation-structure)
- [Complete bakery example formulation](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#complete-bakery-example-formulation)
- [Common formulation mistakes to avoid](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#common-formulation-mistakes-to-avoid)
- [Verification and validation techniques](https://slm.mba/mmpo-001/how-to-formulate-linear-programming-problem/#verification-and-validation-techniques)

## What exactly is linear programming formulation?

Linear programming formulation is the art of converting a business problem into a mathematical model. Think of it as creating a blueprint before building a house – you need to identify all the essential components and how they relate to each other before you can find the optimal solution.

The formulation process involves three critical steps: defining what you want to achieve (objective function), identifying what you can control (decision variables), and recognizing what limits your choices (constraints). This systematic approach ensures that no important aspect of the problem gets overlooked.

Consider a simple example: a bakery wants to determine how many chocolate cakes and vanilla cakes to produce daily to maximize profit. The formulation process would identify the number of each cake type as decision variables, profit maximization as the objective, and factors like available flour, sugar, and oven time as constraints.

## Defining the objective function

The objective function represents the goal you’re trying to achieve – it’s the mathematical expression of what you want to optimize. Every linear programming problem has exactly one objective function, though the real world might seem to present multiple goals.

### Maximization vs minimization objectives

Most business problems fall into two categories: maximizing something desirable or minimizing something undesirable. **Maximization problems** typically involve increasing profit, revenue, production output, or customer satisfaction. **Minimization problems** usually focus on reducing costs, time, waste, or resource consumption.

Here’s how to identify your objective type: ask yourself, “In an ideal world with unlimited resources, would I want this value to be as high as possible or as low as possible?” If the answer is “as high as possible,” you have a maximization problem. If it’s “as low as possible,” you’re dealing with minimization.

For our bakery example, if the goal is profit maximization, the objective function might look like: Maximize Z = 15x₁ + 10x₂, where x₁ represents chocolate cakes, x₂ represents vanilla cakes, and the coefficients (15 and 10) represent the profit per cake.

### Writing the objective function mathematically

The objective function follows a standard format: Maximize (or Minimize) Z = c₁x₁ + c₂x₂ + … + cₙxₙ, where Z represents the objective value, c₁, c₂, etc., are coefficients representing the contribution of each variable, and x₁, x₂, etc., are the decision variables.

The coefficients in your objective function should reflect the per-unit contribution of each decision variable. In profit maximization, these would be profit margins. In cost minimization, they’d be cost per unit. Always ensure these coefficients are accurate, as they directly influence the optimal solution.

## Decision variables and their role

Decision variables are the controllable factors in your problem – they represent the decisions you need to make. These variables are what you’re solving for, and their optimal values will tell you the best course of action.

### Identifying decision variables

To identify decision variables, ask yourself: “What decisions do I have control over?” and “What am I trying to determine the optimal amount of?” Common decision variables include production quantities, resource allocations, investment amounts, or schedule assignments.

Decision variables must be clearly defined and measurable. Instead of vague descriptions like “production level,” use specific definitions like “number of units produced per day” or “kilograms of raw material purchased weekly.” This precision prevents confusion and ensures accurate problem formulation.

In our bakery scenario, the decision variables are x₁ (number of chocolate cakes to produce daily) and x₂ (number of vanilla cakes to produce daily). Notice how each variable has a clear, specific definition with units of measurement.

### Variable relationships and dependencies

Sometimes decision variables have natural relationships. For instance, if you’re allocating a budget across different projects, the sum of all allocations cannot exceed the total budget. Understanding these relationships early helps in formulating accurate constraints.

Decision variables in linear programming are typically assumed to be non-negative and continuous, meaning they can take any value greater than or equal to zero, including decimal values. However, some problems require integer variables, leading to integer programming variants.

## Understanding constraints and their mathematical representation

Constraints represent the limitations and requirements that restrict your decision-making freedom. They’re the mathematical expressions of real-world restrictions like limited resources, capacity bounds, or policy requirements.

### Types of constraints

**Resource constraints** are the most common type, representing limited availability of materials, time, money, or personnel. For example, if a factory has only 40 hours of machine time available daily, this becomes a constraint limiting production.

**Demand constraints** ensure that production meets minimum or maximum demand requirements. A company might need to produce at least 100 units to fulfill a contract, or produce no more than 500 units due to storage limitations.

**Policy constraints** reflect business rules or regulations. For instance, a company policy might require that at least 30% of production consists of premium products, translating into a mathematical constraint.

**Non-negativity constraints** ensure that decision variables cannot be negative, which makes logical sense in most business contexts – you can’t produce negative quantities or invest negative amounts.

### Writing constraints mathematically

Constraints follow the general format: a₁x₁ + a₂x₂ + … + aₙxₙ ≤, =, or ≥ b, where the left side represents resource consumption or output, and b represents the availability or requirement level.

The inequality direction depends on the constraint type. Use ≤ for “at most” situations (like maximum capacity), ≥ for “at least” requirements (like minimum demand), and = for exact requirements (like meeting specific quotas).

For our bakery, if chocolate cakes require 2 hours of oven time and vanilla cakes require 1.5 hours, with only 20 hours available daily, the constraint would be: 2x₁ + 1.5x₂ ≤ 20.

## Complete mathematical representation

A complete linear programming formulation brings together all components in a structured format. The standard form includes the objective function, followed by all constraints, and ends with non-negativity restrictions.

### Standard LP formulation structure

Here’s the complete formulation structure:

**Objective Function:**  
Maximize (or Minimize) Z = c₁x₁ + c₂x₂ + … + cₙxₙ

**Subject to:**  
Constraint 1: a₁₁x₁ + a₁₂x₂ + … + a₁ₙxₙ ≤/=/≥ b₁  
Constraint 2: a₂₁x₁ + a₂₂x₂ + … + a₂ₙxₙ ≤/=/≥ b₂  
…  
Constraint m: aₘ₁x₁ + aₘ₂x₂ + … + aₘₙxₙ ≤/=/≥ bₘ

**Non-negativity:**  
x₁, x₂, …, xₙ ≥ 0

### Complete bakery example formulation

Let’s complete our bakery formulation with additional realistic constraints:

**Maximize Z = 15x₁ + 10x₂** (profit maximization)

**Subject to:**  
2x₁ + 1.5x₂ ≤ 20 (oven time constraint)  
3x₁ + 2x₂ ≤ 24 (flour constraint in kg)  
x₁ + x₂ ≤ 12 (daily production capacity)  
x₁ ≥ 2 (minimum chocolate cake requirement)  
x₂ ≥ 1 (minimum vanilla cake requirement)

**Non-negativity:**  
x₁, x₂ ≥ 0

This formulation captures the complete business scenario: the bakery wants to maximize profit while respecting resource limitations and minimum production requirements.

## Common formulation mistakes to avoid

Even experienced practitioners make formulation errors that can lead to incorrect solutions. **Inconsistent units** represent a frequent problem – ensure all variables and coefficients use compatible units throughout the formulation.

**Missing constraints** can make problems unrealistic. Always verify that your formulation captures all significant limitations and requirements from the original problem statement.

**Incorrect objective function coefficients** will optimize the wrong thing. Double-check that coefficients accurately represent the per-unit contribution of each decision variable to your objective.

**Wrong inequality directions** in constraints can completely reverse the meaning. “At most 100 units” becomes x ≤ 100, not x ≥ 100.

## Verification and validation techniques

After formulating your linear programming problem, verification ensures mathematical correctness while validation confirms that the model represents the real-world situation accurately.

For verification, check that all constraints are mathematically consistent, the objective function includes all relevant decision variables, and inequality directions match the problem description. Substitute simple test values to see if constraints behave as expected.

Validation involves asking domain experts to review the formulation, testing the model with known scenarios, and ensuring that optimal solutions make business sense. If the optimal solution suggests producing 1000 units when maximum capacity is 100, something’s wrong with the formulation.

Regular validation prevents the common trap of solving the wrong problem correctly – a mathematically perfect solution to a poorly formulated problem is worthless in practice.

**What do you think?** Can you identify a business problem in your field of study that could benefit from linear programming formulation? What would be the biggest challenge in accurately capturing all the real-world constraints mathematically?

How useful was this post?

Click on a star to rate it!

Average rating 0 / 5. Vote count: 0

No votes so far! Be the first to rate this post.

[PDF](https://slm.mba/?print-my-blog=1&post-type=post&statuses%5B%5D=publish&rendering_wait=0&columns=1&font_size=normal&image_size=medium&links=include&show_site_title=1&show_site_tagline=1&show_site_url=1&show_date_printed=1&show_title=1&show_url=1&show_date=1&show_categories=1&show_featured_image=1&show_content=1&show_divider=1&pmb_f=pdf&pmb-post=8334)

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