
# simulation.md

## Title: Simulation: From Models to Real-World Decisions

### Section 1: What is Simulation?

Simulation is a technique to **model real-world systems** and study their behavior over time without experimenting on the actual system.

* **Why use it in OR?**

  * Complex systems may be **too expensive, risky, or slow** to test directly.
  * Provides insights into **uncertain or stochastic systems**.
  * Helps in **decision-making, resource allocation, and optimization**.

**Key idea:** Instead of solving a closed-form formula, we **mimic the system** and observe outcomes.

---

### Section 2: Types of Simulation

1. **Monte Carlo Simulation**

   * Uses **random sampling** to estimate outcomes.
   * Example: Predicting total demand for a product over a month when daily demand is uncertain.

2. **Discrete-Event Simulation (DES)**

   * Models a system as a **sequence of events in time**.
   * Example: Hospital emergency room – patients arrive, are treated, and leave.

3. **System Dynamics**

   * Models **continuous flows and feedback loops**.
   * Example: Inventory levels over time with supply and demand rates.

---

### Section 3: Monte Carlo Simulation – Example

**Problem:** Estimate expected total profit of a product line with uncertain demand.

* Cost per unit: $10
* Selling price: $20
* Demand is **uniform between 50 and 100 units**

**Simulation Steps:**

1. Randomly generate 1,000 demand values between 50 and 100
2. Calculate profit for each:
   [
   \text{Profit} = \text{Revenue} - \text{Cost} = \min(\text{Demand}, \text{Inventory}) \times (20 - 10)
   ]
3. Average profits → estimate expected profit

**Python-style pseudocode:**

```python
import numpy as np

n_sim = 1000
demand = np.random.randint(50, 101, size=n_sim)
profit = np.minimum(demand, 80) * (20 - 10)  # Inventory = 80
expected_profit = profit.mean()
print(expected_profit)
```

> This gives a realistic estimate **without needing a closed formula**.

---

### Section 4: Discrete-Event Simulation – Example

**Problem:** Hospital Emergency Room (ER) patient flow

* Patients arrive **Poisson(λ=10 per hour)**
* Service time: **Exponential(mean=15 min)**
* 2 doctors available

**Steps:**

1. Track **event timeline**: arrival, start treatment, end treatment
2. Keep track of **queues** and **resource utilization**
3. Run simulation over a **week**
4. Analyze: average waiting time, doctor utilization, patient throughput

**Insights:**

* Helps identify bottlenecks
* Can test adding extra staff or extending working hours **before changing the real system**

---

### Section 5: Key OR Applications

* **Manufacturing:** assembly line, machine breakdown, production scheduling
* **Healthcare:** patient flow, nurse scheduling, surgery planning
* **Supply Chain:** warehouse operations, inventory under uncertainty
* **Transportation & Logistics:** airport operations, port container handling, VRP stochastic demand
* **Finance:** risk management, portfolio analysis

---

### Section 6: Advantages & Limitations

| Advantages                              | Limitations                                                  |
| --------------------------------------- | ------------------------------------------------------------ |
| Can model **complex systems**           | Requires **computational power** for large-scale simulations |
| Handles **stochasticity & uncertainty** | Accuracy depends on **model quality & assumptions**          |
| Flexible: **test multiple scenarios**   | Does **not always give optimal solutions**, only insights    |
| Safe: no impact on real system          | May require **expertise in statistical modeling**            |

---

### Section 7: Tips for OR Roles

1. Learn **Python / R / SimPy / AnyLogic** for simulation modeling
2. Always **validate your model** against known benchmarks
3. Combine **simulation with optimization** for stochastic OR problems (e.g., simulation-optimization)
4. Use **visualization** to communicate results to decision-makers

---

### Section 8: Simulation & NP-Hard Problems

Simulation is often combined with heuristics/metaheuristics for **NP-hard problems**:

* **Stochastic VRP:** simulate routes under uncertain travel times
* **Inventory optimization:** simulate stock levels under random demand
* **Scheduling:** test heuristics for nurse rostering or production sequencing

> Simulation provides **performance estimates when exact optimization is infeasible**.

---

✅ **Summary**

* Simulation is a **core OR tool** for modeling complex, uncertain systems
* Monte Carlo, discrete-event, and system dynamics are the main types
* Provides **insight, risk evaluation, and scenario testing**
* Often used in combination with optimization or heuristics for real-world decisions

---
