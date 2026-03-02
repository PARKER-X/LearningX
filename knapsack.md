

# **Knapsack Problem (KP) – Click Forever Tutorial**

---

## **Section 1: The Promise – From Items to Maximum Value**

Imagine you’re a treasure hunter with a backpack that can carry **only so much weight**. You have several items, each with a **weight** and a **value**. Your goal? Fill your backpack **to maximize total value**, without exceeding its weight limit.

**Example Dataset:**

| Item | Value | Weight |
| ---- | ----- | ------ |
| 1    | 60    | 10     |
| 2    | 100   | 20     |
| 3    | 120   | 30     |

**Knapsack Capacity:** 50

Goal: Select items → maximize value without exceeding weight limit.

By the end of this tutorial, you’ll understand:

1. **0/1 Knapsack Problem**
2. **Fractional Knapsack Problem**
3. **Dynamic Programming solution**
4. **Greedy heuristics**
5. How to visualize and solve step-by-step

---

## **Section 2: Understanding the Knapsack Problem**

### **Decision Variables**

[
x_i =
\begin{cases}
1 & \text{if item i is included} \
0 & \text{otherwise}
\end{cases}
]

Where:

* i = 1…n (number of items)

---

### **Objective Function**

Maximize total value:

[
\text{Maximize } Z = \sum_{i=1}^{n} v_i x_i
]

Where:

* (v_i) = value of item i

---

### **Constraint**

Total weight ≤ knapsack capacity:

[
\sum_{i=1}^{n} w_i x_i \le W
]

Where:

* (w_i) = weight of item i
* W = max capacity of the knapsack

---

## **Section 3: Step 1 – Fractional Knapsack (Greedy)**

* Items can be **broken into fractions**
* Take items in order of **value/weight ratio**

**Value/Weight Ratio:**

| Item | Value | Weight | Ratio (v/w) |
| ---- | ----- | ------ | ----------- |
| 1    | 60    | 10     | 6           |
| 2    | 100   | 20     | 5           |
| 3    | 120   | 30     | 4           |

**Greedy Approach:**

1. Take Item 1 → Weight used = 10, Value = 60
2. Take Item 2 → Weight used = 30, Value = 160
3. Take 2/3 of Item 3 → Weight used = 20, Value = 160 + 80 = 240

✅ **Total Value = 240** (Fractional knapsack solution)

💡 **Insight:** This is **fast** and **optimal** when fractions are allowed.

---

## **Section 4: Step 2 – 0/1 Knapsack (Dynamic Programming)**

* Items **cannot be broken**
* Must decide **include or exclude each item**
* Use **DP table** for exact solution

**DP Table Structure:**

* Rows → items (1…n)
* Columns → weight capacities (0…W)
* Cell[i][w] → max value using first i items with capacity w

---

### **Step 2a: Initialize Table**

| Item\Capacity | 0 | 10 | 20 | 30 | 40 | 50 |
| ------------- | - | -- | -- | -- | -- | -- |
| 0             | 0 | 0  | 0  | 0  | 0  | 0  |

---

### **Step 2b: Fill Table**

**Item 1 (Value=60, Weight=10):**

| Item\Capacity | 0 | 10 | 20 | 30 | 40 | 50 |
| ------------- | - | -- | -- | -- | -- | -- |
| 1             | 0 | 60 | 60 | 60 | 60 | 60 |

**Item 2 (Value=100, Weight=20):**

* For capacity 20 → max(Exclude=60, Include=100) = 100
* For capacity 30 → max(Exclude=60, Include=60+100=160) = 160
* For capacity 40 → Include 160
* For capacity 50 → Include 160

| Item\Capacity | 0 | 10 | 20  | 30  | 40  | 50  |
| ------------- | - | -- | --- | --- | --- | --- |
| 2             | 0 | 60 | 100 | 160 | 160 | 160 |

**Item 3 (Value=120, Weight=30):**

* For capacity 30 → max(Exclude=160, Include=120) = 160
* For capacity 40 → max(Exclude=160, Include=60+120=180) = 180
* For capacity 50 → max(Exclude=160, Include=100+120=220) = 220

| Item\Capacity | 0 | 10 | 20  | 30  | 40  | 50  |
| ------------- | - | -- | --- | --- | --- | --- |
| 3             | 0 | 60 | 100 | 160 | 180 | 220 |

✅ **Optimal 0/1 Knapsack Value = 220**

---

## **Section 5: Step 3 – Trace Back Solution**

* Start at **Cell[n][W] = 220**
* Compare with previous row:

1. 220 ≠ 160 → Item 3 included
2. Remaining weight = 50-30=20
3. Check Cell[2][20]=100 → Item 2 included
4. Remaining weight = 20-20=0 → No room for Item 1

**Selected Items:** Item 2 + Item 3
**Total Weight = 50, Total Value = 220**

💡 **Observation:** 0/1 knapsack < fractional knapsack because you can’t take fractions

---

## **Section 6: Step 4 – Greedy vs DP Comparison**

| Approach          | Optimal? | Fraction Allowed | Speed              |
| ----------------- | -------- | ---------------- | ------------------ |
| Fractional Greedy | ✅ Yes    | Yes              | Fast (O(n log n))  |
| 0/1 Knapsack DP   | ✅ Yes    | No               | Moderate (O(nW))   |
| Naive Enumeration | ✅ Yes    | No               | Very slow (O(2^n)) |

---

## **Section 7: Key Takeaways**

* Knapsack = **maximize value under capacity constraints**
* **Decision variable:** include/exclude each item
* **Fractional knapsack** → greedy, fastest, optimal with divisible items
* **0/1 knapsack** → dynamic programming, exact for indivisible items
* Visualizing DP table → helps trace **which items are selected**

---

