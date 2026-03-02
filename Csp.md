Title: Give Me 25 Minutes — Complementary Slackness Will Finally Make Sense

Thumbnail: Duality is Actually Simple

Section 1: The Promise — From Solutions to Insight

You now understand:

Linear Programs

Corner points

Simplex

Optimal solutions

But here’s the deeper question:

How do we prove a solution is optimal without running Simplex again?

That’s where:

🔑 Complementary Slackness Theorem

comes in.

It connects:

The primal problem

The dual problem

Optimal solutions of both

And it gives us a simple algebraic test for optimality.

Section 2: The Big Picture — Every LP Has a Twin

Every linear program (called the primal) has a corresponding dual.

If the primal is:

Maximize 
𝑐
𝑇
𝑥
Maximize c
T
x
𝐴
𝑥
≤
𝑏
,
𝑥
≥
0
Ax≤b,x≥0

Then the dual is:

Minimize 
𝑏
𝑇
𝑦
Minimize b
T
y
𝐴
𝑇
𝑦
≥
𝑐
,
𝑦
≥
0
A
T
y≥c,y≥0

They are mirrors of each other.

Section 3: Why Duality Exists (Intuition)

Think economically.

Primal = production problem
Dual = pricing problem

Primal says:

How much should I produce?

Dual says:

What are the implicit prices of resources?

Complementary slackness links:

Resource usage

Resource prices

Section 4: Concrete Example (Same Factory)

Primal:

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
Z=3x
1
	​

+2x
2
	​


Subject to:

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

We already solved this:

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
Section 5: Build the Dual

Introduce dual variables:

𝑦
1
y
1
	​

 for first constraint

𝑦
2
y
2
	​

 for second constraint

Dual becomes:

Minimize

𝑊
=
4
𝑦
1
+
5
𝑦
2
W=4y
1
	​

+5y
2
	​


Subject to:

𝑦
1
+
2
𝑦
2
≥
3
y
1
	​

+2y
2
	​

≥3
𝑦
1
+
𝑦
2
≥
2
y
1
	​

+y
2
	​

≥2
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

,y
2
	​

≥0
Section 6: The Complementary Slackness Theorem

Here is the theorem:

For optimal solutions 
𝑥
∗
x
∗
 and 
𝑦
∗
y
∗
:

Condition 1 (Primal side)
𝑦
𝑖
(
𝑏
𝑖
−
𝐴
𝑖
𝑥
)
=
0
y
i
	​

(b
i
	​

−A
i
	​

x)=0

For each constraint.

Meaning:

Either:

Constraint is tight (no slack)

OR its dual variable is zero

But NOT both positive.

Condition 2 (Dual side)
𝑥
𝑗
(
𝐴
𝑗
𝑇
𝑦
−
𝑐
𝑗
)
=
0
x
j
	​

(A
j
T
	​

y−c
j
	​

)=0

Meaning:

Either:

Variable is zero

OR corresponding dual constraint is tight

Section 7: Let’s Apply It

From primal solution:

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

Check slack in constraints:

Constraint 1:

1
+
3
=
4
1+3=4

No slack.

Constraint 2:

2
(
1
)
+
3
=
5
2(1)+3=5

No slack.

Both constraints are tight.

So complementary slackness says:

𝑦
1
>
0
,
𝑦
2
>
0
y
1
	​

>0,y
2
	​

>0

Now check dual constraints:

𝑦
1
+
2
𝑦
2
=
3
y
1
	​

+2y
2
	​

=3
𝑦
1
+
𝑦
2
=
2
y
1
	​

+y
2
	​

=2

Solve:

Subtract equations:

(
𝑦
1
+
2
𝑦
2
)
−
(
𝑦
1
+
𝑦
2
)
=
3
−
2
(y
1
	​

+2y
2
	​

)−(y
1
	​

+y
2
	​

)=3−2
𝑦
2
=
1
y
2
	​

=1

Plug back:

𝑦
1
+
1
=
2
y
1
	​

+1=2
𝑦
1
=
1
y
1
	​

=1

So dual solution:

𝑦
1
=
1
,
𝑦
2
=
1
y
1
	​

=1,y
2
	​

=1

Dual objective:

𝑊
=
4
(
1
)
+
5
(
1
)
=
9
W=4(1)+5(1)=9

Same as primal.

Optimality confirmed.

Section 8: What Complementary Slackness Really Says

It says:

If a resource has leftover capacity → its price is zero

If a resource has positive price → it must be fully used

And:

If a variable is positive → its dual constraint is tight

If dual constraint has slack → variable must be zero

It is a zero-product condition.

Section 9: Why This Is Powerful

Complementary slackness allows you to:

Prove optimality without running Simplex

Solve LPs faster in theory problems

Derive economic interpretation

Understand shadow prices

Connect to KKT conditions in nonlinear optimization

In fact:

Complementary Slackness
= Linear version of KKT conditions

Section 10: Big Picture Connection

You now see the ladder:

Linear Regression → Optimization
Gradient Descent → First-order methods
Linear Programming → Structured optimization
Duality → Hidden mirror problem
Complementary Slackness → Optimality certificate

This is the bridge to:

Convex optimization

Game theory

Mechanism design

Advanced ML theory

Final Intuition

Simplex walks corners.

Duality watches prices.

Complementary slackness ensures:

No money is left on the table.

If both primal and dual are feasible and complementary slackness holds:

You are at the optimum.
