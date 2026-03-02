

# **Vehicle Routing Problem (VRP) – Click Forever Tutorial**

---

## **Section 1: The Promise – From Depot to Delivery in Minutes**

Imagine you’re managing a fleet of delivery trucks. You want to deliver packages to all your customers **efficiently**, using the **least total distance**, without exceeding truck capacities.

**Our Example Dataset:**

| Customer | Demand | Location (x,y) |
| -------- | ------ | -------------- |
| Depot    | –      | (0,0)          |
| C1       | 1      | (2,3)          |
| C2       | 1      | (5,2)          |
| C3       | 2      | (6,6)          |
| C4       | 1      | (8,3)          |

**Fleet:** 2 trucks, each capacity = 3 units

Goal: Assign routes → **minimize total distance traveled**

By the end of this tutorial, you’ll understand:

1. How to define **VRP mathematically**
2. How to construct **feasible routes**
3. How to compute **total distance**
4. How heuristics and exact methods differ

---

## **Section 2: Understanding the VRP Model**

### **Decision Variables**

[
x_{ij}^k =
\begin{cases}
1 & \text{if truck k travels from i to j} \
0 & \text{otherwise}
\end{cases}
]

Where:

* i, j = depot + customers
* k = truck index

---

### **Objective Function**

Minimize total distance:

[
\text{Minimize } Z = \sum_{k} \sum_{i,j} d_{ij} \cdot x_{ij}^k
]

* (d_{ij}) = distance between node i and j

---

### **Constraints**

1. **Visit each customer exactly once**

[
\sum_k \sum_i x_{ij}^k = 1 \quad \forall j \neq depot
]

2. **Truck capacity not exceeded**

[
\sum_{i,j} \text{demand}*j \cdot x*{ij}^k \le \text{capacity}_k
]

3. **Flow conservation:** Each truck leaves every node it enters

[
\sum_i x_{ij}^k = \sum_l x_{jl}^k \quad \forall j
]

---

## **Section 3: Distance Table**

| From \ To | Depot | C1 | C2 | C3 | C4 |
| --------- | ----- | -- | -- | -- | -- |
| Depot     | 0     | 3  | 5  | 8  | 9  |
| C1        | 3     | 0  | 4  | 6  | 7  |
| C2        | 5     | 4  | 0  | 3  | 4  |
| C3        | 8     | 6  | 3  | 0  | 3  |
| C4        | 9     | 7  | 4  | 3  | 0  |

---

## **Section 4: Step 1 – LP Relaxation**

* Relax integer constraint: trucks can “fractionally” visit customers
* Lower bound on minimum total distance

**Fractional example:**

| Truck | Route Fractional              |
| ----- | ----------------------------- |
| 1     | Depot → C1 → C2 → Depot = 0.5 |
| 2     | Depot → C1 → C2 → Depot = 0.5 |

💡 **Insight:** Gives **best-case distance**, but not feasible in reality

---

## **Section 5: Step 2 – Construct Feasible Routes**

* Assign integer routes, respecting truck capacities

**Truck 1:** Depot → C1 → C3 → Depot (Demand = 3 ≤ 3)
**Truck 2:** Depot → C2 → C4 → Depot (Demand = 2 ≤ 3)

**Total distance:**

* Truck 1: Depot→C1=3, C1→C3=6, C3→Depot=8 → total=17
* Truck 2: Depot→C2=5, C2→C4=4, C4→Depot=9 → total=18
* **Combined total = 35**

✅ Feasible integer solution

---

## **Section 6: Step 3 – Optimization Methods**

### **Exact Method – Branch & Bound**

* Explores all feasible routes
* Guarantees **optimal solution**
* Time-consuming for large problems

### **Heuristics – Quick Approximation**

* **Nearest Neighbor:** Visit nearest unvisited customer
* **Savings / Clarke-Wright:** Merge routes to reduce distance
* **Metaheuristics:** Genetic Algorithm, Tabu Search, Simulated Annealing

---

## **Section 7: Visualizing Routes**

* **Depot = blue dot**

* **Customers = green dots**

* **Truck 1 path = red line**

* **Truck 2 path = orange line**

* Visualizes total distance

* Shows how routes split between trucks

* Makes constraints and capacity limits obvious

---

## **Section 8: Summary Table**

| Component                   | Role                           | Example                    |
| --------------------------- | ------------------------------ | -------------------------- |
| Decision Variables          | Which truck travels where      | x_{ij}^k                   |
| Objective                   | Minimize total distance        | Z = Σ d_{ij} x_{ij}^k      |
| Constraints                 | Visit once, capacity, flow     | Σ x_{ij}^k = 1             |
| LP Relaxation               | Lower bound / fractional route | Fractional route example   |
| Branch-and-Bound            | Exact integer solution         | Assign trucks to customers |
| Heuristics / Metaheuristics | Approximate solution fast      | Nearest Neighbor, GA       |

---

## **Section 9: Key Takeaways**

* VRP = **TSP + multiple vehicles + capacity**
* LP relaxation → lower bound on distance
* Integer solution → feasible route
* Heuristics → fast approximation for large datasets
* Visualization = essential for planning

---

This structure mirrors your **Linear Regression click tutorial**: problem, decision variables, constraints, solution methods, and visual intuition.

---

If you want, I can **make a “VRP Step-by-Step Animation” cheat sheet next** showing:

1. LP relaxation vs integer solution
2. Branch-and-bound tree
3. Heuristic route construction
4. Color-coded trucks & depot


