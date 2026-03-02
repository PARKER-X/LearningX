

# sensitivity_analysis.md

## Title: Sensitivity Analysis: Understanding How Changes Affect Your OR Models

---

### Section 1: What is Sensitivity Analysis?

**Sensitivity analysis** studies how **changes in input parameters** affect the **optimal solution** or **objective value** of an optimization problem.

* In OR, it is mostly used with **linear programming (LP), mixed-integer LP (MILP), and stochastic models**.
* Helps answer questions like:

  * What happens if resource availability increases?
  * How much can cost coefficients change before the solution changes?
  * Which constraints are **critical** and which are **slack**?

**Key Idea:**
We don’t just solve an optimization problem once; we **explore the neighborhood of the solution**.

---

### Section 2: Sensitivity Analysis in Linear Programming

Consider a simple LP:

[
\text{Maximize } Z = 3x_1 + 5x_2
]
[
\text{Subject to: }
\begin{cases}
2x_1 + 3x_2 \le 12 \
x_1 + x_2 \le 5 \
x_1, x_2 \ge 0
\end{cases}
]

**Types of Sensitivity Analysis:**

1. **Objective Coefficient Sensitivity (Reduced Cost)**

   * How much can a coefficient (c_i) in the objective change before the optimal **basis** changes?
   * **Reduced cost** tells us:

     * If (x_i) is nonzero, how much can (c_i) decrease before (x_i) becomes zero
     * If (x_i = 0), how much must (c_i) increase to make (x_i > 0)

2. **Right-Hand Side (RHS) Sensitivity (Shadow Prices)**

   * How does the **optimal objective value** change if the availability of a resource changes?
   * Dual values (from strong duality) give **shadow prices**.
   * Example: For constraint (2x_1 + 3x_2 \le 12), if its RHS increases by 1, objective increases by shadow price (if within allowable range).

3. **Allowable Ranges**

   * Each coefficient or RHS has an **allowable range** where the current solution remains optimal
   * Beyond that, **the optimal basis may change**

---

### Section 3: Example – LP Sensitivity Analysis

LP solution:

| Variable | Optimal Value | Reduced Cost |
| -------- | ------------- | ------------ |
| x1       | 3             | 0            |
| x2       | 1             | 0            |

| Constraint     | Shadow Price | Allowable Increase | Allowable Decrease |
| -------------- | ------------ | ------------------ | ------------------ |
| 2x1 + 3x2 ≤ 12 | 1.5          | 4                  | 2                  |
| x1 + x2 ≤ 5    | 0.0          | 3                  | 1                  |

**Interpretation:**

* Increasing the first constraint by 1 → objective increases by 1.5
* x1 can change its cost within allowable range without affecting solution
* Second constraint is non-binding (shadow price = 0) → extra resource doesn’t help

---

### Section 4: Sensitivity in Stochastic and Simulation Models

In **stochastic optimization** or **simulation**, sensitivity analysis often involves:

1. **Varying parameters systematically**

   * E.g., demand mean ± 10%, service rate ± 20%
2. **Observing changes in performance metrics**

   * Objective value, waiting time, cost, inventory levels
3. **Scenario-based sensitivity**

   * Test different random realizations to see variability in outcomes

**Example:** Inventory problem with random demand

| Parameter Change | Expected Profit | Stockouts |
| ---------------- | --------------- | --------- |
| Demand +10%      | 9500            | 12        |
| Demand -10%      | 10500           | 0         |
| Cost +5%         | 9400            | 0         |

> Helps managers **understand risks** and **make robust decisions**.

---

### Section 5: Applications in OR Roles

| Domain        | Use Case               | Sensitivity Focus                    |
| ------------- | ---------------------- | ------------------------------------ |
| Manufacturing | Production planning    | Resource availability, cost changes  |
| Healthcare    | Nurse scheduling       | Patient arrival rates, service times |
| Logistics     | VRP / supply chain     | Fuel cost, demand fluctuations       |
| Finance       | Portfolio optimization | Asset return, risk tolerance         |
| Energy        | Power generation       | Fuel price, demand uncertainty       |

---

### Section 6: How to Perform Sensitivity Analysis

1. **LP / MILP:**

   * Use solver outputs: reduced costs, shadow prices, allowable ranges
2. **Stochastic / Simulation models:**

   * Vary input distributions
   * Run multiple simulations
   * Analyze output metrics statistically (mean, variance, confidence intervals)
3. **Scenario Analysis:**

   * Compare “what-if” scenarios systematically
4. **Visualization:**

   * Tornado charts (for objective sensitivity)
   * Spider plots (for multi-parameter changes)

---

### Section 7: Best Practices for OR Roles

* Focus on **binding constraints** first (high impact on objective)
* Combine **sensitivity + duality** for faster insights
* For stochastic systems, report **both mean performance and variability**
* Communicate insights with **graphs & tables** for managers

---

✅ **Summary**

Sensitivity analysis is **critical for decision-making in OR**:

* Helps understand **impact of parameter changes**
* Connects **duality, shadow prices, and robust optimization**
* Provides **confidence in recommendations**
* Essential for **risk-aware planning in logistics, finance, healthcare, and production**

---
