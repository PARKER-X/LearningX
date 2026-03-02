
# **MILP: Give Me 20 Minutes, I’ll Make Mixed-Integer Linear Programming Click Forever**

**Thumbnail:** MILP is Actually EASY

---

## **Section 1: The Promise – From Decisions to Optimal Solutions in 20 Minutes**

Mixed-Integer Linear Programming (MILP) might sound scary: variables that are sometimes integers, sometimes continuous, and constraints everywhere. But the idea is simple: **find the best solution given limited resources and rules**.

We’ll use a concrete, tiny example: scheduling workers to tasks.

**Example Problem:**

| Worker | Task | Profit if assigned |
| ------ | ---- | ------------------ |
| A      | 1    | 10                 |
| A      | 2    | 12                 |
| B      | 1    | 15                 |
| B      | 2    | 8                  |

Constraints:

* Each task must be assigned to exactly **one worker**
* Each worker can do **at most one task**
* Worker-task assignments are **binary variables** (0 or 1)

Goal: **maximize total profit**.

---

### **Your Learning Promise**

By the end of this guide, you will understand:

1. What MILP really is and why integer variables matter
2. How to formulate MILP with decision variables, objective, and constraints
3. How the solver finds optimal solutions
4. Real intuition behind linear relaxation and branch-and-bound

---

## **Section 2: The Model – Decision Variables**

MILP uses **variables that can be integers, 0-1 (binary), or continuous**.

**For our example:**

[
x_{A1}, x_{A2}, x_{B1}, x_{B2} \in {0,1}
]

Where:

[
x_{A1} = 1 \text{ if Worker A is assigned to Task 1, else 0}
]

---

### **The Objective Function**

We want **maximize total profit**:

[
\text{Maximize } Z = 10x_{A1} + 12x_{A2} + 15x_{B1} + 8x_{B2}
]

---

### **Constraints**

1. Each task assigned to **exactly one worker**

[
x_{A1} + x_{B1} = 1 \quad \text{(Task 1)}
]
[
x_{A2} + x_{B2} = 1 \quad \text{(Task 2)}
]

2. Each worker does **at most one task**

[
x_{A1} + x_{A2} \le 1
]
[
x_{B1} + x_{B2} \le 1
]

3. Variables are **binary**

[
x_{A1}, x_{A2}, x_{B1}, x_{B2} \in {0,1}
]

---

## **Section 3: Solving MILP – Step by Step**

MILP solvers use a **mix of LP relaxation and branch-and-bound**:

1. **Relax integers**: Allow 0 ≤ x ≤ 1 (like LP)
2. Solve **linear program** → get fractional solution
3. **Branch** on a variable that isn’t integer (x = 0 or x = 1)
4. Solve subproblems recursively
5. **Prune** subproblems if the solution cannot beat the current best

**Intuition:** Imagine searching a tree of decisions, but skipping branches that cannot improve profit.

---

## **Section 4: Solving Our Tiny Example**

**Step 1: Relax the binary constraint**

* Allow x variables to be any number between 0 and 1
* Solve LP → could get fractional assignment (e.g., x_{A1}=0.7, x_{B1}=0.3)
* Fractional solution is **not valid in reality**, but gives an **upper bound**

**Step 2: Branch**

* Choose a variable, say x_{A1}, branch into: x_{A1} = 1 or x_{A1} = 0
* Solve each branch LP → prune branches that can’t beat current best

**Step 3: Reach integer solution**

* Solver finds:

[
x_{A2} = 1, x_{B1} = 1, x_{A1} = x_{B2} = 0
]

**Check:**

* Each task assigned exactly once
* Each worker assigned ≤ 1 task
* Total profit = 12 + 15 = 27 ✅

---

## **Section 5: MILP vs LP – Why Integers Matter**

* LP relaxation ignores integer restrictions → may give **impossible solutions**
* MILP ensures feasibility for **real-world decisions**:

| Problem | Variable type  | Real-world use                                         |
| ------- | -------------- | ------------------------------------------------------ |
| LP      | Continuous     | Production quantities, blend ratios                    |
| MILP    | Integer/Binary | Task assignment, routing, scheduling, yes/no decisions |

* Example: Assigning 0.7 of a worker to a task is impossible in reality → MILP fixes this

---

## **Section 6: Practical Tradeoffs**

| Feature      | LP                       | MILP                                |
| ------------ | ------------------------ | ----------------------------------- |
| Solving Time | Polynomial (fast)        | NP-Hard (slow for big problems)     |
| Solution     | Continuous               | Integer-feasible                    |
| Techniques   | Simplex / Interior-Point | Branch-and-Bound, Branch-and-Cut    |
| Use Case     | Resource allocation      | Scheduling, routing, network design |

---

## **Section 7: Conclusion – From Tiny Example to Real MILP Problems**

* MILP is **just LP + integer variables**
* With small examples, you can **solve by hand or branch-and-bound mentally**
* With large real-world problems, solvers (CPLEX, Gurobi, OR-Tools) do the heavy lifting
* **Key intuition:** Relax, branch, prune → find optimal discrete decisions

**Your takeaway:**

* Define decision variables
* Write linear objective
* Add linear constraints
* Identify which variables must be integers
* Let solver handle the search

MILP might look intimidating, but at its core, it’s **structured decision-making + linear relationships + discrete choices**.

---


---

# **MILP Worked Example: Scheduling Workers – Click Forever**

---

## **Section 1: Problem Recap**

We want to **assign workers to tasks to maximize profit**, with the constraints:

| Worker | Task | Profit |
| ------ | ---- | ------ |
| A      | 1    | 10     |
| A      | 2    | 12     |
| B      | 1    | 15     |
| B      | 2    | 8      |

**Constraints:**

1. Each task must be done by exactly one worker
2. Each worker can do at most one task
3. Assignments are binary (0 or 1)

**Decision Variables:**

[
x_{A1}, x_{A2}, x_{B1}, x_{B2} \in {0,1}
]

**Objective:**

[
\text{Maximize } Z = 10x_{A1} + 12x_{A2} + 15x_{B1} + 8x_{B2}
]

**Constraints:**

[
x_{A1} + x_{B1} = 1
]
[
x_{A2} + x_{B2} = 1
]
[
x_{A1} + x_{A2} \le 1
]
[
x_{B1} + x_{B2} \le 1
]

---

## **Section 2: Step 1 – LP Relaxation**

Step 1: **Ignore the integer constraint** → let variables be continuous (0 ≤ x ≤ 1).

* Solve LP:

  * Maximum Z = **27.5** (example)
  * Fractional solution:

    * x_{A1} = 0.5
    * x_{A2} = 0.5
    * x_{B1} = 0.5
    * x_{B2} = 0.5

💡 **Intuition:** LP gives an **upper bound** on profit. Real solution must be ≤ 27.5.

---

## **Section 3: Step 2 – Branch on a Variable**

Pick a fractional variable to branch: **x_{A1}**

* **Branch 1:** x_{A1} = 0
* **Branch 2:** x_{A1} = 1

Solve LP for each branch.

---

### **Branch 1: x_{A1} = 0**

* Update constraints:

  * Task 1: x_{B1} = 1
* Solve remaining LP:

  * Task 2: assign either A2 or B2
  * Worker constraints: A can do one task, B already assigned → A2 = 1, B2 = 0
* **Integer solution found:**

[
x_{A1}=0, x_{A2}=1, x_{B1}=1, x_{B2}=0
]

* **Profit Z = 12 + 15 = 27 ✅**

---

### **Branch 2: x_{A1} = 1**

* Update constraints:

  * Task 1: B1 = 0
  * Worker A already assigned → A2 = 0
* Task 2: x_{B2} = 1 (B can do one task)
* **Integer solution found:**

[
x_{A1}=1, x_{A2}=0, x_{B1}=0, x_{B2}=1
]

* **Profit Z = 10 + 8 = 18 ❌**

---

## **Section 4: Step 3 – Compare Branches and Pick Best**

* Branch 1 → Z = 27 ✅
* Branch 2 → Z = 18 ❌
* **Optimal MILP solution = Branch 1**

---

## **Section 5: Branch-and-Bound Tree Diagram**

```
                   x_{A1}?
                  /      \
         x_{A1}=0          x_{A1}=1
         /       \          /      \
   LP Solution  Integer    Integer  LP Solution
     Z<=27.5     Z=27      Z=18     prune
```

* Nodes that **cannot beat current best (Z=27)** are **pruned**
* Branch-and-bound ensures we **don’t check every combination**, only promising paths

---

## **Section 6: Key Takeaways**

1. **MILP = LP + integer/binary variables**
2. **LP relaxation** gives an upper bound and fractional intuition
3. **Branch-and-bound** systematically explores integer feasible solutions
4. **Pruning** avoids wasting time on impossible or suboptimal branches
5. **Small example → solved by hand**, large-scale MILP → solvers like **Gurobi, CPLEX, OR-Tools**

---

### **Section 7: Quick Real-World Analogy**

* Think of MILP as **puzzle-solving**:

  * Pieces = decision variables
  * Rules = constraints
  * Goal = maximize/minimize something (profit, cost, time)
  * LP relaxation = allowing pieces to be “fractional” → can’t actually assemble puzzle, but tells you what’s possible
  * Branch-and-bound = exploring branches of the puzzle tree, pruning impossible paths

💡 **Insight:** Once you see it visually and step by step, MILP isn’t scary—it’s structured decision-making with a **smart search strategy**.

---

--

# **MILP Worked Example: Scheduling Workers – Click Forever**

---

## **Section 1: Problem Recap**

We want to **assign workers to tasks to maximize profit**, with the constraints:

| Worker | Task | Profit |
| ------ | ---- | ------ |
| A      | 1    | 10     |
| A      | 2    | 12     |
| B      | 1    | 15     |
| B      | 2    | 8      |

**Constraints:**

1. Each task must be done by exactly one worker
2. Each worker can do at most one task
3. Assignments are binary (0 or 1)

**Decision Variables:**

[
x_{A1}, x_{A2}, x_{B1}, x_{B2} \in {0,1}
]

**Objective:**

[
\text{Maximize } Z = 10x_{A1} + 12x_{A2} + 15x_{B1} + 8x_{B2}
]

**Constraints:**

[
x_{A1} + x_{B1} = 1
]
[
x_{A2} + x_{B2} = 1
]
[
x_{A1} + x_{A2} \le 1
]
[
x_{B1} + x_{B2} \le 1
]

---

## **Section 2: Step 1 – LP Relaxation**

Step 1: **Ignore the integer constraint** → let variables be continuous (0 ≤ x ≤ 1).

* Solve LP:

  * Maximum Z = **27.5** (example)
  * Fractional solution:

    * x_{A1} = 0.5
    * x_{A2} = 0.5
    * x_{B1} = 0.5
    * x_{B2} = 0.5

💡 **Intuition:** LP gives an **upper bound** on profit. Real solution must be ≤ 27.5.

---

## **Section 3: Step 2 – Branch on a Variable**

Pick a fractional variable to branch: **x_{A1}**

* **Branch 1:** x_{A1} = 0
* **Branch 2:** x_{A1} = 1

Solve LP for each branch.

---

### **Branch 1: x_{A1} = 0**

* Update constraints:

  * Task 1: x_{B1} = 1
* Solve remaining LP:

  * Task 2: assign either A2 or B2
  * Worker constraints: A can do one task, B already assigned → A2 = 1, B2 = 0
* **Integer solution found:**

[
x_{A1}=0, x_{A2}=1, x_{B1}=1, x_{B2}=0
]

* **Profit Z = 12 + 15 = 27 ✅**

---

### **Branch 2: x_{A1} = 1**

* Update constraints:

  * Task 1: B1 = 0
  * Worker A already assigned → A2 = 0
* Task 2: x_{B2} = 1 (B can do one task)
* **Integer solution found:**

[
x_{A1}=1, x_{A2}=0, x_{B1}=0, x_{B2}=1
]

* **Profit Z = 10 + 8 = 18 ❌**

---

## **Section 4: Step 3 – Compare Branches and Pick Best**

* Branch 1 → Z = 27 ✅
* Branch 2 → Z = 18 ❌
* **Optimal MILP solution = Branch 1**

---

## **Section 5: Branch-and-Bound Tree Diagram**

```
                   x_{A1}?
                  /      \
         x_{A1}=0          x_{A1}=1
         /       \          /      \
   LP Solution  Integer    Integer  LP Solution
     Z<=27.5     Z=27      Z=18     prune
```

* Nodes that **cannot beat current best (Z=27)** are **pruned**
* Branch-and-bound ensures we **don’t check every combination**, only promising paths

---

## **Section 6: Key Takeaways**

1. **MILP = LP + integer/binary variables**
2. **LP relaxation** gives an upper bound and fractional intuition
3. **Branch-and-bound** systematically explores integer feasible solutions
4. **Pruning** avoids wasting time on impossible or suboptimal branches
5. **Small example → solved by hand**, large-scale MILP → solvers like **Gurobi, CPLEX, OR-Tools**

---

### **Section 7: Quick Real-World Analogy**

* Think of MILP as **puzzle-solving**:

  * Pieces = decision variables
  * Rules = constraints
  * Goal = maximize/minimize something (profit, cost, time)
  * LP relaxation = allowing pieces to be “fractional” → can’t actually assemble puzzle, but tells you what’s possible
  * Branch-and-bound = exploring branches of the puzzle tree, pruning impossible paths

💡 **Insight:** Once you see it visually and step by step, MILP isn’t scary—it’s structured decision-making with a **smart search strategy**.

---


