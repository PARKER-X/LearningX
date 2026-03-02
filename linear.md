Section 1: The Promise — From Constraints to Optimal Decisions

Give me 30 minutes, and I’ll make the Simplex Method feel mechanical and intuitive.

Linear programming often looks terrifying:

Objective functions

Constraints

Feasible regions

Corner points

Pivot operations

Tableaus

Basis variables

But underneath all the notation, the idea is simple:

We are walking along the corners of a shape to find the best possible value.

That’s it.

Today, we will:

Build the geometric intuition

Translate it into algebra

Perform the Simplex algorithm step-by-step

Understand why it works

Connect it to real-world optimization

By the end, you’ll understand:

The Four Pillars of Linear Programming

The Model (Objective Function)

The Constraints (Feasible Region)

The Corner-Point Theorem

The Simplex Algorithm (Systematic Corner Walking)

Section 2: The Model — What Are We Optimizing?
The Big Picture

Linear programming solves problems of the form:

Maximize 
𝑍
=
𝑐
1
𝑥
1
+
𝑐
2
𝑥
2
+
⋯
+
𝑐
𝑛
𝑥
𝑛
Maximize Z=c
1
	​

x
1
	​

+c
2
	​

x
2
	​

+⋯+c
n
	​

x
n
	​


Subject to:

𝑎
11
𝑥
1
+
𝑎
12
𝑥
2
	
≤
𝑏
1


𝑎
21
𝑥
1
+
𝑎
22
𝑥
2
	
≤
𝑏
2


𝑥
1
,
𝑥
2
	
≥
0
a
11
	​

x
1
	​

+a
12
	​

x
2
	​

a
21
	​

x
1
	​

+a
22
	​

x
2
	​

x
1
	​

,x
2
	​

	​

≤b
1
	​

≤b
2
	​

≥0
	​


Everything is linear.

Concrete Example

Suppose you run a small factory.

You produce:

𝑥
1
x
1
	​

: Tables

𝑥
2
x
2
	​

: Chairs

Profit:

$3 per table

$2 per chair

So your objective is:

Maximize 
𝑍
=
3
𝑥
1
+
2
𝑥
2
Maximize Z=3x
1
	​

+2x
2
	​


Constraints:

Wood constraint:

𝑥
1
+
𝑥
2
≤
4
x
1
	​

+x
2
	​

≤4

Labor constraint:

2
𝑥
1
+
𝑥
2
≤
5
2x
1
	​

+x
2
	​

≤5

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
Section 3: The Geometry — Why Corners Matter
Step 1: Feasible Region

Each inequality forms a half-plane.

When combined, they create a polygon.

This polygon is called the feasible region.

Every point inside it satisfies all constraints.

Step 2: The Key Theorem (Corner-Point Theorem)

Here’s the magic:

If a linear program has an optimal solution, it occurs at a corner point of the feasible region.

Why?

Because:

Objective function = straight line

Constraints = flat boundaries

The maximum occurs at an extreme boundary intersection

You never need to search the interior.

Only the corners.

Let’s Find the Corners

From our constraints:

𝑥
1
+
𝑥
2
=
4
x
1
	​

+x
2
	​

=4

2
𝑥
1
+
𝑥
2
=
5
2x
1
	​

+x
2
	​

=5

Solve simultaneously:

Subtract equations:

(
2
𝑥
1
+
𝑥
2
)
−
(
𝑥
1
+
𝑥
2
)
=
5
−
4
(2x
1
	​

+x
2
	​

)−(x
1
	​

+x
2
	​

)=5−4
𝑥
1
=
1
x
1
	​

=1

Plug back:

𝑥
2
=
3
x
2
	​

=3

Corner points:

(0,0)

(0,4)

(1,3)

(2.5,0)

Evaluate objective:

Point	Z = 3x₁ + 2x₂
(0,0)	0
(0,4)	8
(1,3)	9
(2.5,0)	7.5

Maximum = 9 at (1,3)

So the best solution is:

Produce 1 table and 3 chairs.

But what if we had 200 variables?

We can’t graph that.

That’s where Simplex comes in.

Section 4: The Simplex Method — Systematic Corner Walking
The Big Idea

Instead of graphing:

Start at one corner

Move to a better adjacent corner

Repeat

Stop when no improvement is possible

It’s hill-climbing on a polyhedron.

Section 5: Converting to Standard Form

To use Simplex, we convert inequalities to equations.

Original:

𝑥
1
+
𝑥
2
≤
4
x
1
	​

+x
2
	​

≤4

Add slack variable 
𝑠
1
s
1
	​

:

𝑥
1
+
𝑥
2
+
𝑠
1
=
4
x
1
	​

+x
2
	​

+s
1
	​

=4

Similarly:

2
𝑥
1
+
𝑥
2
+
𝑠
2
=
5
2x
1
	​

+x
2
	​

+s
2
	​

=5

Now variables:

𝑥
1
,
𝑥
2
,
𝑠
1
,
𝑠
2
≥
0
x
1
	​

,x
2
	​

,s
1
	​

,s
2
	​

≥0
Section 6: Initial Simplex Tableau

We write everything in a table:

Basis	x₁	x₂	s₁	s₂	RHS
s₁	1	1	1	0	4
s₂	2	1	0	1	5
Z	-3	-2	0	0	0

Why negative?

Because we rewrite:

𝑍
−
3
𝑥
1
−
2
𝑥
2
=
0
Z−3x
1
	​

−2x
2
	​

=0
Section 7: The Simplex Algorithm (Mechanical Steps)
Step 1: Entering Variable

Look at bottom row.

Pick most negative coefficient.

-3 (for x₁)

So x₁ enters.

Step 2: Leaving Variable (Minimum Ratio Test)

Divide RHS by positive entries in pivot column.

Row 1: 4 / 1 = 4
Row 2: 5 / 2 = 2.5

Smallest = 2.5

So s₂ leaves.

Step 3: Pivot

Pivot element = 2

Divide row 2 by 2:

New row 2:

x₁	x₂	s₁	s₂	RHS
1	0.5	0	0.5	2.5

Now eliminate x₁ from row 1 and Z row.

After row operations, new tableau becomes:

Basis	x₁	x₂	s₁	s₂	RHS
s₁	0	0.5	1	-0.5	1.5
x₁	1	0.5	0	0.5	2.5
Z	0	-0.5	0	1.5	7.5
Step 4: Repeat

Most negative in Z row: -0.5 (x₂)

So x₂ enters.

Perform ratio test:

Row 1: 1.5 / 0.5 = 3
Row 2: 2.5 / 0.5 = 5

Smallest = 3 → s₁ leaves.

Pivot again.

After operations:

Final tableau:

Basis	x₁	x₂	s₁	s₂	RHS
x₂	0	1	2	-1	3
x₁	1	0	-1	1	1
Z	0	0	1	1	9

No negative coefficients remain in Z row.

We stop.

Solution:

𝑥
1
=
1
,
𝑥
2
=
3
x
1
	​

=1,x
2
	​

=3
𝑍
=
9
Z=9

Exactly what geometry gave us.

Section 8: Why Simplex Works

Because:

Feasible region is convex

Objective is linear

If improvement exists, it must lie on an adjacent vertex

No need to revisit points

Finite number of vertices

Simplex systematically checks improving adjacent corners until optimality condition holds.

Section 9: When Things Get Interesting

Simplex also handles:

Degeneracy

Unbounded solutions

Infeasible systems

Multiple optimal solutions

Artificial variables (Big-M method)

Two-phase method

But the core engine never changes:

Enter variable → Leave variable → Pivot → Repeat

Section 10: Gradient Descent vs Simplex (Big Picture)
Feature	Gradient Descent	Simplex
Problem Type	Continuous optimization	Linear programming
Movement	Small steps	Corner jumps
Uses derivatives	Yes	No
Guarantees optimality	Not always	Yes (if feasible & bounded)
Typical Use	ML models	Operations research
Section 11: From Simplex to the Real World

Simplex powers:

Supply chain optimization

Airline scheduling

Resource allocation

Manufacturing planning

Portfolio optimization

Even modern solvers like:

CPLEX

Gurobi

GLPK

are built around advanced variants of Simplex and interior-point methods.

Final Recap — The Engine of Simplex

We built linear programming from scratch:

Objective function — what we optimize

Constraints — define feasible region

Corner-point theorem — optimum at vertex

Simplex algorithm — systematic vertex search

The entire method reduces to:

Add slack variables

Build tableau

Pick entering variable

Pick leaving variable

Pivot

Stop when no negatives remain

That’s it.

Linear programming isn’t magic.

It’s structured corner-walking.

And now it clicks.
