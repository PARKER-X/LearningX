Title: Give Me 30 Minutes — KKT Conditions Will Make Constrained Optimization Click

Thumbnail: Optimization is Just Structured Logic

Section 1: The Promise — The Universal Optimality Test

The Karush–Kuhn–Tucker (KKT) conditions are:

The generalization of complementary slackness to nonlinear optimization.

They answer:

When is a constrained solution optimal?

How do gradients interact with constraints?

What replaces “corner points” when geometry isn’t linear?

By the end, you will understand:

The optimization setup

The Lagrangian

The four KKT conditions

Why they make intuitive sense

How they reduce to complementary slackness

Section 2: The General Optimization Problem

We now move beyond linear programming.

General constrained optimization:

Minimize 
𝑓
(
𝑥
)
Minimize f(x)

Subject to:

𝑔
𝑖
(
𝑥
)
≤
0
(
𝑖
=
1
,
…
,
𝑚
)
g
i
	​

(x)≤0(i=1,…,m)
ℎ
𝑗
(
𝑥
)
=
0
(
𝑗
=
1
,
…
,
𝑝
)
h
j
	​

(x)=0(j=1,…,p)

Where:

𝑓
(
𝑥
)
f(x) = objective

𝑔
𝑖
(
𝑥
)
g
i
	​

(x) = inequality constraints

ℎ
𝑗
(
𝑥
)
h
j
	​

(x) = equality constraints

Everything can now be nonlinear.

Section 3: First Recall — Unconstrained Optimization

If no constraints:

Optimal point satisfies:

∇
𝑓
(
𝑥
∗
)
=
0
∇f(x
∗
)=0

Gradient equals zero.

That’s it.

Constraints complicate this because:

The gradient doesn’t have to be zero anymore.

Instead:

It must not point in a feasible descent direction.

Section 4: The Lagrangian — Merging Objective and Constraints

We combine everything into one function:

𝐿
(
𝑥
,
𝜆
,
𝜇
)
=
𝑓
(
𝑥
)
+
∑
𝑖
=
1
𝑚
𝜆
𝑖
𝑔
𝑖
(
𝑥
)
+
∑
𝑗
=
1
𝑝
𝜇
𝑗
ℎ
𝑗
(
𝑥
)
L(x,λ,μ)=f(x)+
i=1
∑
m
	​

λ
i
	​

g
i
	​

(x)+
j=1
∑
p
	​

μ
j
	​

h
j
	​

(x)

Where:

𝜆
𝑖
≥
0
λ
i
	​

≥0 (multipliers for inequalities)

𝜇
𝑗
μ
j
	​

 free (multipliers for equalities)

This is called the Lagrangian.

It blends objective + constraint penalties.

Section 5: The Four KKT Conditions

At optimal point 
𝑥
∗
x
∗
, there exist multipliers 
𝜆
∗
,
𝜇
∗
λ
∗
,μ
∗
 such that:

1️⃣ Stationarity
∇
𝑥
𝐿
(
𝑥
∗
,
𝜆
∗
,
𝜇
∗
)
=
0
∇
x
	​

L(x
∗
,λ
∗
,μ
∗
)=0

Meaning:

Gradient of objective

weighted gradients of active constraints
= zero

This replaces “gradient = 0”.

2️⃣ Primal Feasibility
𝑔
𝑖
(
𝑥
∗
)
≤
0
g
i
	​

(x
∗
)≤0
ℎ
𝑗
(
𝑥
∗
)
=
0
h
j
	​

(x
∗
)=0

Point satisfies constraints.

3️⃣ Dual Feasibility
𝜆
𝑖
∗
≥
0
λ
i
∗
	​

≥0

Multipliers for inequality constraints must be nonnegative.

4️⃣ Complementary Slackness
𝜆
𝑖
∗
𝑔
𝑖
(
𝑥
∗
)
=
0
λ
i
∗
	​

g
i
	​

(x
∗
)=0

Either:

Constraint is active (tight)

OR multiplier is zero

This is exactly what you learned before.

Section 6: Intuition — Why These Conditions Make Sense

Imagine minimizing inside a region.

At optimum:

If you're inside the region → gradient must be zero.

If you're on a boundary → gradient can point outward, but constraint pushes back.

So the constraint gradients combine with objective gradient to balance forces.

Think of it like:

Objective pulls downhill.
Constraints push you inward.
At optimum, forces balance.

Section 7: Concrete Example

Minimize:

𝑓
(
𝑥
)
=
𝑥
2
f(x)=x
2

Subject to:

𝑥
≥
1
x≥1

Rewrite constraint:

𝑔
(
𝑥
)
=
1
−
𝑥
≤
0
g(x)=1−x≤0
Step 1: Lagrangian
𝐿
(
𝑥
,
𝜆
)
=
𝑥
2
+
𝜆
(
1
−
𝑥
)
L(x,λ)=x
2
+λ(1−x)
Step 2: Stationarity
𝑑
𝑑
𝑥
𝐿
=
2
𝑥
−
𝜆
=
0
dx
d
	​

L=2x−λ=0

So:

𝜆
=
2
𝑥
λ=2x
Step 3: Complementary Slackness
𝜆
(
1
−
𝑥
)
=
0
λ(1−x)=0
Step 4: Check Cases

If constraint inactive:

1
−
𝑥
<
0
1−x<0 → x > 1

Then complementary slackness ⇒ λ = 0

But then stationarity ⇒ 2x = 0 → x = 0

Not feasible.

So constraint must be active.

Thus:

𝑥
=
1
x=1

Then:

𝜆
=
2
λ=2

Solution:

𝑥
∗
=
1
x
∗
=1

Correct.

Section 8: How KKT Generalizes Everything
Problem Type	Optimality Condition
Unconstrained	∇f = 0
Equality constraints	Lagrange multipliers
Linear programming	Complementary slackness
Nonlinear constrained	KKT

KKT is the master version.

Section 9: When KKT Guarantees Optimality

Important:

KKT gives:

Necessary conditions in general

Necessary AND sufficient if problem is convex

If:

f is convex

g_i are convex

h_j are affine

Then any KKT point is globally optimal.

This is why convex optimization is powerful.

Section 10: Geometric Interpretation

At optimum:

∇
𝑓
(
𝑥
∗
)
=
−
∑
𝑖
𝜆
𝑖
∇
𝑔
𝑖
(
𝑥
∗
)
−
∑
𝑗
𝜇
𝑗
∇
ℎ
𝑗
(
𝑥
∗
)
∇f(x
∗
)=−
i
∑
	​

λ
i
	​

∇g
i
	​

(x
∗
)−
j
∑
	​

μ
j
	​

∇h
j
	​

(x
∗
)

Meaning:

Objective gradient lies in span of active constraint gradients.

In simple terms:

You can’t move downhill without violating constraints.

Section 11: Why This Is Fundamental in ML

KKT appears everywhere:

Support Vector Machines

Constrained logistic regression

Dual problems

Regularization

Portfolio optimization

Interior point methods

For example:

SVM dual derivation is pure KKT.

Final Mental Model

KKT is just structured logic:

You must satisfy constraints.

Multipliers must be nonnegative.

Either constraint binds or multiplier is zero.

Objective gradient balances constraint gradients.

It’s not magic.

It’s force balance under constraints.
