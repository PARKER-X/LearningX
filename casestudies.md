

## Title: Operational Research Case Studies: From Theory to Practice

---

### Section 1: Introduction

Case studies in OR demonstrate how **models, algorithms, and sensitivity analyses** solve **real-world decision-making problems**.
They show the full workflow:

1. Define the problem and objectives
2. Identify constraints and stochastic elements
3. Formulate the mathematical or simulation model
4. Solve using optimization, heuristics, or simulation
5. Perform sensitivity or scenario analysis
6. Interpret results for actionable insights

---

### Section 2: Inventory Management – Newsvendor Problem

**Scenario:** A retailer must decide how many newspapers to order daily. Demand (D) is random.

**Data:**

| Parameter                  | Value        |
| -------------------------- | ------------ |
| Selling price per unit (p) | $2           |
| Purchase cost per unit (c) | $1           |
| Salvage value per unit (s) | $0.5         |
| Demand (D)                 | Poisson(100) |

**Model:**

* Objective: Maximize expected profit
  [
  \mathbb{E}[\text{Profit}] = \mathbb{E}[p \min(Q,D) - c Q + s \max(Q-D,0)]
  ]
* Optimal order quantity:
  [
  Q^* = F^{-1}\Big(\frac{p-c}{p-s}\Big) = F^{-1}\Big(\frac{2-1}{2-0.5}\Big) = F^{-1}(0.6667)
  ]

**Results:**

* Using Poisson distribution, (Q^* \approx 105) units
* Expected profit: $90

**Insights:**

* Performing **sensitivity analysis** on (p, c, s) shows robustness of the order decision
* Can be extended to **stochastic lead times** (simulation with `simulation.md`)

---

### Section 3: Vehicle Routing Problem with Stochastic Demand (VRP)

**Scenario:** A delivery company must serve 5 customers. Demands are random, travel times uncertain.

**Data:**

| Customer | Location | Mean Demand |
| -------- | -------- | ----------- |
| A        | (2,3)    | 10          |
| B        | (5,5)    | 8           |
| C        | (1,7)    | 12          |
| D        | (6,2)    | 7           |
| E        | (3,6)    | 9           |

**Model:**

* **NP-hard** problem (`np-hard.md`)
* Objective: Minimize total distance, ensure vehicle capacity ≥ stochastic demand
* Approach: **Simulation + Metaheuristics (`meta-hueri.md`)**

  * Simulate multiple demand realizations
  * Solve VRP for each scenario
  * Use average distance as objective

**Insights:**

* Route 1: Depot → A → C → E → Depot
* Route 2: Depot → B → D → Depot
* Monte Carlo simulation shows **95% probability of completing all deliveries without exceeding capacity**

---

### Section 4: Hospital Emergency Department – Queueing Model

**Scenario:** ER wants to estimate waiting times for patients based on arrivals and service times.

**Data:**

| Parameter              | Value                         |
| ---------------------- | ----------------------------- |
| Arrival rate (\lambda) | 12 patients/hour (Poisson)    |
| Service rate (\mu)     | 5 patients/hour (Exponential) |
| Number of servers      | 3                             |

**Model:**

* Use **M/M/c queue** (`stochastic.md`)

[
L_q = \frac{(\lambda/\mu)^c \cdot \rho}{c! (1-\rho)^2} \cdot P_0
]
[
W_q = L_q / \lambda
]

**Results:**

* Average patients waiting: 4.2
* Average waiting time: 21 minutes
* Adding one more doctor reduces waiting time to 12 minutes

**Insights:**

* Sensitivity analysis (`sensitivity_analysis.md`) helps decide **staffing levels** under arrival variability

---

### Section 5: Manufacturing Scheduling – Job Shop

**Scenario:** Schedule 3 machines for 5 jobs with random processing times.

**Data:**

| Job | Machine 1 | Machine 2 | Machine 3 |
| --- | --------- | --------- | --------- |
| J1  | 3±1       | 2±0.5     | 4±1       |
| J2  | 2±0.5     | 3±1       | 3±0.5     |
| J3  | 4±1       | 2±0.5     | 2±0.5     |
| J4  | 3±0.5     | 3±1       | 1±0.2     |
| J5  | 2±0.5     | 1±0.2     | 4±1       |

**Model:**

* **Stochastic Job Shop Scheduling**
* Objective: Minimize makespan
* Approach: **Metaheuristics + Simulation** (`meta-hueri.md` + `simulation.md`)

**Results:**

* Best schedule (average over 100 simulations): Makespan = 15.8 hours
* Sensitivity: Machine 3 delays increase makespan more than other machines

**Insights:**

* Identifies **bottleneck machines**
* Supports **robust scheduling under uncertainty**

---

### Section 6: Portfolio Optimization under Uncertainty

**Scenario:** Maximize expected return for an investment portfolio with 3 assets, considering random returns.

**Data:**

| Asset | Expected Return | Std Dev |
| ----- | --------------- | ------- |
| A     | 8%              | 5%      |
| B     | 12%             | 10%     |
| C     | 10%             | 6%      |

**Model:**

* **Stochastic Linear Programming** (`stochastic.md`)
* Objective: Maximize expected return, limit portfolio variance ≤ 0.005

[
\max \mathbb{E}[R] = 0.08x_A + 0.12x_B + 0.10x_C
]
[
\text{s.t. } x_A + x_B + x_C = 1, \quad x_i \ge 0, \quad \text{Var(R)} \le 0.005
]

**Results:**

* Optimal allocation: A=0.4, B=0.2, C=0.4
* Expected return: 9.6%
* Sensitivity: Increasing allowed variance → more in Asset B

**Insights:**

* Combines **risk, stochasticity, and sensitivity analysis**
* Useful for **financial OR roles**

---

### Section 7: Summary & Workflow

**OR Case Study Workflow:**

1. Define problem → stochastic elements → objectives
2. Choose modeling approach:

   * LP/MILP for deterministic or expected values
   * Stochastic LP or simulation for uncertainty
   * Metaheuristics for NP-hard combinatorial problems
3. Solve & validate
4. Sensitivity analysis → robust decision-making
5. Communicate results: tables, charts, scenarios

**Integration with your repo:**

* `np-hard.md` → metaheuristics in VRP/job shop
* `stochastic.md` → inventory, finance, ER queues
* `simulation.md` → VRP, scheduling, hospital ER
* `sensitivity_analysis.md` → inventory, hospital, portfolio

---


# case_studies.md

## Title: Operational Research Case Studies: From Theory to Practice

---

### Section 1: Introduction

Case studies in OR demonstrate how **models, algorithms, and sensitivity analyses** solve **real-world decision-making problems**.
They show the full workflow:

1. Define the problem and objectives
2. Identify constraints and stochastic elements
3. Formulate the mathematical or simulation model
4. Solve using optimization, heuristics, or simulation
5. Perform sensitivity or scenario analysis
6. Interpret results for actionable insights

---

### Section 2: Inventory Management – Newsvendor Problem

**Scenario:** A retailer must decide how many newspapers to order daily. Demand (D) is random.

**Data:**

| Parameter                  | Value        |
| -------------------------- | ------------ |
| Selling price per unit (p) | $2           |
| Purchase cost per unit (c) | $1           |
| Salvage value per unit (s) | $0.5         |
| Demand (D)                 | Poisson(100) |

**Model:**

* Objective: Maximize expected profit
  [
  \mathbb{E}[\text{Profit}] = \mathbb{E}[p \min(Q,D) - c Q + s \max(Q-D,0)]
  ]
* Optimal order quantity:
  [
  Q^* = F^{-1}\Big(\frac{p-c}{p-s}\Big) = F^{-1}\Big(\frac{2-1}{2-0.5}\Big) = F^{-1}(0.6667)
  ]

**Results:**

* Using Poisson distribution, (Q^* \approx 105) units
* Expected profit: $90

**Insights:**

* Performing **sensitivity analysis** on (p, c, s) shows robustness of the order decision
* Can be extended to **stochastic lead times** (simulation with `simulation.md`)

---

### Section 3: Vehicle Routing Problem with Stochastic Demand (VRP)

**Scenario:** A delivery company must serve 5 customers. Demands are random, travel times uncertain.

**Data:**

| Customer | Location | Mean Demand |
| -------- | -------- | ----------- |
| A        | (2,3)    | 10          |
| B        | (5,5)    | 8           |
| C        | (1,7)    | 12          |
| D        | (6,2)    | 7           |
| E        | (3,6)    | 9           |

**Model:**

* **NP-hard** problem (`np-hard.md`)
* Objective: Minimize total distance, ensure vehicle capacity ≥ stochastic demand
* Approach: **Simulation + Metaheuristics (`meta-hueri.md`)**

  * Simulate multiple demand realizations
  * Solve VRP for each scenario
  * Use average distance as objective

**Insights:**

* Route 1: Depot → A → C → E → Depot
* Route 2: Depot → B → D → Depot
* Monte Carlo simulation shows **95% probability of completing all deliveries without exceeding capacity**

---

### Section 4: Hospital Emergency Department – Queueing Model

**Scenario:** ER wants to estimate waiting times for patients based on arrivals and service times.

**Data:**

| Parameter              | Value                         |
| ---------------------- | ----------------------------- |
| Arrival rate (\lambda) | 12 patients/hour (Poisson)    |
| Service rate (\mu)     | 5 patients/hour (Exponential) |
| Number of servers      | 3                             |

**Model:**

* Use **M/M/c queue** (`stochastic.md`)

[
L_q = \frac{(\lambda/\mu)^c \cdot \rho}{c! (1-\rho)^2} \cdot P_0
]
[
W_q = L_q / \lambda
]

**Results:**

* Average patients waiting: 4.2
* Average waiting time: 21 minutes
* Adding one more doctor reduces waiting time to 12 minutes

**Insights:**

* Sensitivity analysis (`sensitivity_analysis.md`) helps decide **staffing levels** under arrival variability

---

### Section 5: Manufacturing Scheduling – Job Shop

**Scenario:** Schedule 3 machines for 5 jobs with random processing times.

**Data:**

| Job | Machine 1 | Machine 2 | Machine 3 |
| --- | --------- | --------- | --------- |
| J1  | 3±1       | 2±0.5     | 4±1       |
| J2  | 2±0.5     | 3±1       | 3±0.5     |
| J3  | 4±1       | 2±0.5     | 2±0.5     |
| J4  | 3±0.5     | 3±1       | 1±0.2     |
| J5  | 2±0.5     | 1±0.2     | 4±1       |

**Model:**

* **Stochastic Job Shop Scheduling**
* Objective: Minimize makespan
* Approach: **Metaheuristics + Simulation** (`meta-hueri.md` + `simulation.md`)

**Results:**

* Best schedule (average over 100 simulations): Makespan = 15.8 hours
* Sensitivity: Machine 3 delays increase makespan more than other machines

**Insights:**

* Identifies **bottleneck machines**
* Supports **robust scheduling under uncertainty**

---

### Section 6: Portfolio Optimization under Uncertainty

**Scenario:** Maximize expected return for an investment portfolio with 3 assets, considering random returns.

**Data:**

| Asset | Expected Return | Std Dev |
| ----- | --------------- | ------- |
| A     | 8%              | 5%      |
| B     | 12%             | 10%     |
| C     | 10%             | 6%      |

**Model:**

* **Stochastic Linear Programming** (`stochastic.md`)
* Objective: Maximize expected return, limit portfolio variance ≤ 0.005

[
\max \mathbb{E}[R] = 0.08x_A + 0.12x_B + 0.10x_C
]
[
\text{s.t. } x_A + x_B + x_C = 1, \quad x_i \ge 0, \quad \text{Var(R)} \le 0.005
]

**Results:**

* Optimal allocation: A=0.4, B=0.2, C=0.4
* Expected return: 9.6%
* Sensitivity: Increasing allowed variance → more in Asset B

**Insights:**

* Combines **risk, stochasticity, and sensitivity analysis**
* Useful for **financial OR roles**

---

### Section 7: Summary & Workflow

**OR Case Study Workflow:**

1. Define problem → stochastic elements → objectives
2. Choose modeling approach:

   * LP/MILP for deterministic or expected values
   * Stochastic LP or simulation for uncertainty
   * Metaheuristics for NP-hard combinatorial problems
3. Solve & validate
4. Sensitivity analysis → robust decision-making
5. Communicate results: tables, charts, scenarios

**Integration with your repo:**

* `np-hard.md` → metaheuristics in VRP/job shop
* `stochastic.md` → inventory, finance, ER queues
* `simulation.md` → VRP, scheduling, hospital ER
* `sensitivity_analysis.md` → inventory, hospital, portfolio

---


