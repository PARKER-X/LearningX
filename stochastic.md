

# stochastic.md

## Title: Stochastic Models: Decision-Making Under Uncertainty

---

### Section 1: What is Stochastic Modeling?

In Operational Research, **stochastic models** are used to handle **uncertainty** in systems:

* Inputs, parameters, or events are **random variables**
* Outcomes are **probabilistic**, not deterministic
* Goal: make decisions that perform well **on average** or with **high probability**

**Key Idea:**
Instead of assuming fixed demand, service times, or costs, we **model them as random variables** (e.g., Poisson, Normal, Exponential) and optimize accordingly.

---

### Section 2: Examples of Stochastic Systems in OR

| System                     | Uncertainty                        |
| -------------------------- | ---------------------------------- |
| Inventory Management       | Random demand                      |
| Queueing / Service Systems | Random arrival/service times       |
| Supply Chain               | Random lead times & disruptions    |
| Financial Portfolio        | Random returns & risks             |
| Transportation             | Traffic delays, weather conditions |

---

### Section 3: Stochastic Processes

A **stochastic process** describes how a random system evolves over time:

* **Discrete-time:** Stock levels, queue length per day
* **Continuous-time:** Arrival of customers in a store, radioactive decay
* Common processes:

  * **Poisson Process:** Random arrivals/events per time unit
  * **Markov Chains:** Probabilities of moving between states
  * **Brownian Motion:** Continuous-time, continuous-space process used in finance

---

### Section 4: Key Stochastic OR Models

#### 1. Inventory Control (Newsvendor Problem)

* **Scenario:** Sell newspapers. Demand (D) is random.
* Cost per unit: (c)
* Selling price per unit: (p)
* Unsold units may have salvage value (s)

**Objective:** Maximize expected profit:

[
\text{Expected Profit} = \mathbb{E}[\text{Revenue} - \text{Cost}]
]

* Optimal order quantity (Q^*) uses **critical fractile formula**:

[
Q^* = F^{-1}\left(\frac{p-c}{p-s}\right)
]

where (F^{-1}) is the inverse cumulative distribution of demand.

---

#### 2. Queueing Models

* **Example:** Hospital ER, bank, call center
* Random arrivals ((\lambda)) and service times ((\mu))
* Common metrics:

  * Average queue length (L_q)
  * Average waiting time (W_q)
  * Server utilization (\rho = \lambda / \mu)

**Classic Model:** M/M/1 queue (Poisson arrivals, exponential service, single server)

[
L_q = \frac{\lambda^2}{\mu (\mu - \lambda)}, \quad W_q = \frac{\lambda}{\mu (\mu - \lambda)}
]

* Helps **decide number of servers or resources**.

---

#### 3. Stochastic Linear Programming (SLP)

* LP with **random parameters** (costs, resources, demand)

[
\max \mathbb{E}[c^T x] \quad \text{s.t.} \quad Ax \le b \text{ (some parameters random)}
]

* Solution strategies:

  * **Expected value problem**: replace random variables with their means
  * **Chance-constrained programming**: ensure constraints hold with high probability
  * **Scenario-based optimization**: simulate multiple realizations

---

#### 4. Markov Decision Processes (MDP)

* Used for **sequential decision-making under uncertainty**
* States (S), actions (A), rewards (R), transition probabilities (P(s'|s,a))
* Objective: maximize expected cumulative reward

[
V(s) = \max_a \sum_{s'} P(s'|s,a) \big[ R(s,a,s') + \gamma V(s') \big]
]

* Applications: inventory replenishment, maintenance scheduling, healthcare decision-making

---

### Section 5: Monte Carlo & Simulation in Stochastic Models

* **Monte Carlo Simulation** is often used to **estimate expected performance** when closed-form solutions are hard
* Example: stochastic VRP (random travel times) → simulate routes to evaluate heuristics
* Combine **simulation + optimization** for complex OR problems

---

### Section 6: Applications in Real OR Roles

| Domain        | Example                | Stochastic Element               | OR Technique            |
| ------------- | ---------------------- | -------------------------------- | ----------------------- |
| Manufacturing | Safety stock planning  | Random demand                    | SLP, Newsvendor         |
| Healthcare    | Patient flow in ER     | Arrival times, service times     | Queueing, DES           |
| Finance       | Portfolio optimization | Random returns                   | Stochastic LP, MDP      |
| Logistics     | Delivery routing       | Travel time & demand uncertainty | Simulation + Heuristics |

---

### Section 7: Advantages & Challenges

**Advantages:**

* Models **realistic uncertainty**
* Helps quantify **risk and variability**
* Supports **robust decision-making**

**Challenges:**

* Requires **data on distributions**
* Computationally expensive for large systems
* Solutions may be **scenario-dependent**

---

### Section 8: Tips for OR Practitioners

1. Always identify **which parameters are random**
2. Choose **distribution models carefully** (Poisson, Normal, Exponential, etc.)
3. Combine **stochastic modeling with simulation or optimization**
4. Use **software**: Python (NumPy, SimPy), R, AnyLogic, Gurobi for SLP

---

✅ **Summary**

Stochastic models are **foundational for OR roles**, enabling **decision-making under uncertainty**. They connect naturally with:

* Simulation (`simulation.md`)
* NP-hard problems (`np-hard.md`)
* Metaheuristics (`meta-hueri.md`)

They provide **insight into variability, risk, and expected outcomes**, critical for logistics, finance, healthcare, and supply chain roles.

---


