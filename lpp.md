Linear Programming (LP) – From Formulation to Solution
Section 1: The Promise – Optimizing Decisions with Constraints

Linear programming is all about making the best decision when you have:

A linear objective to maximize or minimize

Linear constraints restricting your choices

Real-world example:

A factory produces two products P1 and P2.

Each product requires time on machines and raw materials.

Profit per product is known.

Question: How many units of each product should the factory make to maximize profit without exceeding machine hours and materials?

This is exactly the kind of problem LP solves.

Section 2: Formulating a Linear Program
Step 1: Define Decision Variables

Let:

𝑥
1
=
units of product P1
𝑥
2
=
units of product P2
x
1
	​

=units of product P1x
2
	​

=units of product P2
Step 2: Write the Objective Function

Maximize profit:

Maximize 
𝑍
=
40
𝑥
1
+
30
𝑥
2
Maximize Z=40x
1
	​

+30x
2
	​


Where 40 and 30 are profit per unit.

Step 3: Add Constraints

Machine hours: 
2
𝑥
1
+
𝑥
2
≤
100
2x
1
	​

+x
2
	​

≤100

Raw material: 
𝑥
1
+
𝑥
2
≤
80
x
1
	​

+x
2
	​

≤80

Non-negativity: 
𝑥
1
,
𝑥
2
≥
0
x
1
	​

,x
2
	​

≥0

Step 4: Standard Form

LP in standard form:

Maximize 
𝑍
=
𝑐
𝑇
𝑥
Maximize Z=c
T
x
subject to 
𝐴
𝑥
≤
𝑏
,
𝑥
≥
0
subject to Ax≤b,x≥0

Here, 
𝑐
=
[
40
,
30
]
𝑇
c=[40,30]
T
,

𝑥
=
[
𝑥
1
,
𝑥
2
]
𝑇
x=[x
1
	​

,x
2
	​

]
T
,

𝐴
=
[
2
	
1


1
	
1
]
A=[
2
1
	​

1
1
	​

],

𝑏
=
[
100
,
80
]
𝑇
b=[100,80]
T

Section 3: Graphical Method (2 Variables)

Plot constraints on 2D plane

Feasible region = intersection of half-planes

Vertices = candidate optimal solutions

Intuition:

Linear function increases along a straight line

Maximum occurs at one of the corners (vertices) of feasible region

Example: Solve graphically:

Corner points: (0,0), (0,80), (20,60), (50,0)

Evaluate Z at each:

(0,0) → Z=0

(0,80) → Z=30*80=2400

(20,60) → Z=4020+3060=2800 ✅ Optimal

(50,0) → Z=2000

So optimal production = 20 units of P1, 60 units of P2

Section 4: Simplex Method – LP for n Variables

Graphical method is limited to 2 variables. Simplex works for any n-variable LP.

Step 1: Convert to Slack Form

Add slack variables 
𝑠
1
,
𝑠
2
s
1
	​

,s
2
	​

 to convert inequalities to equalities:

2
𝑥
1
+
𝑥
2
+
𝑠
1
=
100
2x
1
	​

+x
2
	​

+s
1
	​

=100
𝑥
1
+
𝑥
2
+
𝑠
2
=
80
x
1
	​

+x
2
	​

+s
2
	​

=80

All variables ≥ 0

Step 2: Set Up Initial Simplex Tableau
Basic	x1	x2	s1	s2	RHS
s1	2	1	1	0	100
s2	1	1	0	1	80
Z	-40	-30	0	0	0

Z-row = negative coefficients of objective (maximize)

Step 3: Pivot to Optimality

Entering variable = most negative in Z-row → x1 (-40)

Leaving variable = min ratio RHS / pivot column → s2 (80/1=80)

Perform pivot → new tableau

Repeat until all Z-row coefficients ≥ 0 → optimal

Result: 
𝑥
1
=
20
,
𝑥
2
=
60
,
𝑍
=
2800
x
1
	​

=20,x
2
	​

=60,Z=2800 ✅

Section 5: Duality in LP

Every LP has a dual problem.

Primal: maximize profit subject to constraints

Dual: minimize cost of resources while ensuring they are “enough”

Intuition:

Shadow price = value of one extra unit of a resource

Strong duality: optimal primal Z = optimal dual value

Example:

Dual variables 
𝑦
1
,
𝑦
2
y
1
	​

,y
2
	​

 for constraints:

Minimize 
𝑊
=
100
𝑦
1
+
80
𝑦
2
Minimize W=100y
1
	​

+80y
2
	​

subject to 
2
𝑦
1
+
𝑦
2
≥
40
subject to 2y
1
	​

+y
2
	​

≥40
𝑦
1
+
𝑦
2
≥
30
,
𝑦
1
,
𝑦
2
≥
0
y
1
	​

+y
2
	​

≥30,y
1
	​

,y
2
	​

≥0

Solving gives shadow prices for machine hours and raw material

Section 6: Sensitivity Analysis

How changes in profit coefficients or resources affect optimal solution

Example: If profit of P1 changes from 40→45, does solution change?

LP solvers provide allowable range

Section 7: Advantages & Limitations

Advantages:

Well-understood & widely used

Efficient solution algorithms (Simplex, Interior-point)

Strong theoretical guarantees

Limitations:

Only linear relationships

Cannot handle integer-only decisions (use IP/MIP)

Sensitive to precise data

Section 8: Extensions

Integer Programming (IP) → discrete decisions

Mixed-Integer Programming (MIP) → mix of integer & continuous

Goal Programming → multi-objective LP

✅ Summary: LP Engine

Decision variables → what to choose

Objective function → what to optimize

Constraints → limits of resources or rules

Feasible region → all possible solutions

Optimal solution → best vertex of feasible region (graphical) or via Simplex (n-dim)

Duality & sensitivity → understand resource value and robustness


Linear Programming (LP) – From Formulation to Solution
Section 1: The Promise – Optimizing Decisions with Constraints

Linear programming is all about making the best decision when you have:

A linear objective to maximize or minimize

Linear constraints restricting your choices

Real-world example:

A factory produces two products P1 and P2.

Each product requires time on machines and raw materials.

Profit per product is known.

Question: How many units of each product should the factory make to maximize profit without exceeding machine hours and materials?

This is exactly the kind of problem LP solves.

Section 2: Formulating a Linear Program
Step 1: Define Decision Variables

Let:

𝑥
1
=
units of product P1
𝑥
2
=
units of product P2
x
1
	​

=units of product P1x
2
	​

=units of product P2
Step 2: Write the Objective Function

Maximize profit:

Maximize 
𝑍
=
40
𝑥
1
+
30
𝑥
2
Maximize Z=40x
1
	​

+30x
2
	​


Where 40 and 30 are profit per unit.

Step 3: Add Constraints

Machine hours: 
2
𝑥
1
+
𝑥
2
≤
100
2x
1
	​

+x
2
	​

≤100

Raw material: 
𝑥
1
+
𝑥
2
≤
80
x
1
	​

+x
2
	​

≤80

Non-negativity: 
𝑥
1
,
𝑥
2
≥
0
x
1
	​

,x
2
	​

≥0

Step 4: Standard Form

LP in standard form:

Maximize 
𝑍
=
𝑐
𝑇
𝑥
Maximize Z=c
T
x
subject to 
𝐴
𝑥
≤
𝑏
,
𝑥
≥
0
subject to Ax≤b,x≥0

Here, 
𝑐
=
[
40
,
30
]
𝑇
c=[40,30]
T
,

𝑥
=
[
𝑥
1
,
𝑥
2
]
𝑇
x=[x
1
	​

,x
2
	​

]
T
,

𝐴
=
[
2
	
1


1
	
1
]
A=[
2
1
	​

1
1
	​

],

𝑏
=
[
100
,
80
]
𝑇
b=[100,80]
T

Section 3: Graphical Method (2 Variables)

Plot constraints on 2D plane

Feasible region = intersection of half-planes

Vertices = candidate optimal solutions

Intuition:

Linear function increases along a straight line

Maximum occurs at one of the corners (vertices) of feasible region

Example: Solve graphically:

Corner points: (0,0), (0,80), (20,60), (50,0)

Evaluate Z at each:

(0,0) → Z=0

(0,80) → Z=30*80=2400

(20,60) → Z=4020+3060=2800 ✅ Optimal

(50,0) → Z=2000

So optimal production = 20 units of P1, 60 units of P2

Section 4: Simplex Method – LP for n Variables

Graphical method is limited to 2 variables. Simplex works for any n-variable LP.

Step 1: Convert to Slack Form

Add slack variables 
𝑠
1
,
𝑠
2
s
1
	​

,s
2
	​

 to convert inequalities to equalities:

2
𝑥
1
+
𝑥
2
+
𝑠
1
=
100
2x
1
	​

+x
2
	​

+s
1
	​

=100
𝑥
1
+
𝑥
2
+
𝑠
2
=
80
x
1
	​

+x
2
	​

+s
2
	​

=80

All variables ≥ 0

Step 2: Set Up Initial Simplex Tableau
Basic	x1	x2	s1	s2	RHS
s1	2	1	1	0	100
s2	1	1	0	1	80
Z	-40	-30	0	0	0

Z-row = negative coefficients of objective (maximize)

Step 3: Pivot to Optimality

Entering variable = most negative in Z-row → x1 (-40)

Leaving variable = min ratio RHS / pivot column → s2 (80/1=80)

Perform pivot → new tableau

Repeat until all Z-row coefficients ≥ 0 → optimal

Result: 
𝑥
1
=
20
,
𝑥
2
=
60
,
𝑍
=
2800
x
1
	​

=20,x
2
	​

=60,Z=2800 ✅

Section 5: Duality in LP

Every LP has a dual problem.

Primal: maximize profit subject to constraints

Dual: minimize cost of resources while ensuring they are “enough”

Intuition:

Shadow price = value of one extra unit of a resource

Strong duality: optimal primal Z = optimal dual value

Example:

Dual variables 
𝑦
1
,
𝑦
2
y
1
	​

,y
2
	​

 for constraints:

Minimize 
𝑊
=
100
𝑦
1
+
80
𝑦
2
Minimize W=100y
1
	​

+80y
2
	​

subject to 
2
𝑦
1
+
𝑦
2
≥
40
subject to 2y
1
	​

+y
2
	​

≥40
𝑦
1
+
𝑦
2
≥
30
,
𝑦
1
,
𝑦
2
≥
0
y
1
	​

+y
2
	​

≥30,y
1
	​

,y
2
	​

≥0

Solving gives shadow prices for machine hours and raw material

Section 6: Sensitivity Analysis

How changes in profit coefficients or resources affect optimal solution

Example: If profit of P1 changes from 40→45, does solution change?

LP solvers provide allowable range

Section 7: Advantages & Limitations

Advantages:

Well-understood & widely used

Efficient solution algorithms (Simplex, Interior-point)

Strong theoretical guarantees

Limitations:

Only linear relationships

Cannot handle integer-only decisions (use IP/MIP)

Sensitive to precise data

Section 8: Extensions

Integer Programming (IP) → discrete decisions

Mixed-Integer Programming (MIP) → mix of integer & continuous

Goal Programming → multi-objective LP

✅ Summary: LP Engine

Decision variables → what to choose

Objective function → what to optimize

Constraints → limits of resources or rules

Feasible region → all possible solutions

Optimal solution → best vertex of feasible region (graphical) or via Simplex (n-dim)

Duality & sensitivity → understand resource value and robustness
