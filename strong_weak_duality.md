Title: Give Me 25 Minutes — Weak vs Strong Duality Will Finally Click

Thumbnail: Why Two Different Problems Have The Same Answer

Section 1: The Promise — Two Problems, One Truth

Every optimization problem has a twin:

Primal problem

Dual problem

At first glance, they look different.

Different variables.
Different objective.
Different constraints.

And yet…

Sometimes they give exactly the same optimal value.

That’s the magic of duality.

Today you’ll understand:

What Weak Duality says

What Strong Duality says

Why Weak Duality is always true

When Strong Duality is guaranteed

How this connects to KKT

Section 2: The Setup — Primal and Dual

Let’s write a standard linear program (LP).

Primal (Maximization Form)
Maximize 
𝑐
𝑇
𝑥
Maximize c
T
x

Subject to:

𝐴
𝑥
≤
𝑏
Ax≤b
𝑥
≥
0
x≥0
Dual (Minimization Form)
Minimize 
𝑏
𝑇
𝑦
Minimize b
T
y

Subject to:

𝐴
𝑇
𝑦
≥
𝑐
A
T
y≥c
𝑦
≥
0
y≥0

Think of it as:

Primal = choose quantities

Dual = choose prices

Section 3: Weak Duality — The Always-True Inequality

Here is the theorem.

🔹 Weak Duality Theorem

For any feasible primal solution 
𝑥
x and
any feasible dual solution 
𝑦
y:

𝑐
𝑇
𝑥
≤
𝑏
𝑇
𝑦
c
T
x≤b
T
y

In words:

The primal value is always ≤ the dual value.

Always.

No assumptions needed.

Why Is This True?

Start with feasibility:

Primal feasible:

𝐴
𝑥
≤
𝑏
Ax≤b

Multiply both sides by 
𝑦
𝑇
y
T
 (and since 
𝑦
≥
0
y≥0, inequality direction preserved):

𝑦
𝑇
𝐴
𝑥
≤
𝑦
𝑇
𝑏
y
T
Ax≤y
T
b

But dual feasibility says:

𝐴
𝑇
𝑦
≥
𝑐
A
T
y≥c

Multiply both sides by 
𝑥
≥
0
x≥0:

𝑥
𝑇
𝐴
𝑇
𝑦
≥
𝑥
𝑇
𝑐
x
T
A
T
y≥x
T
c

Notice:

𝑥
𝑇
𝐴
𝑇
𝑦
=
𝑦
𝑇
𝐴
𝑥
x
T
A
T
y=y
T
Ax

So combine:

𝑐
𝑇
𝑥
≤
𝑦
𝑇
𝐴
𝑥
≤
𝑏
𝑇
𝑦
c
T
x≤y
T
Ax≤b
T
y

Boom.

𝑐
𝑇
𝑥
≤
𝑏
𝑇
𝑦
c
T
x≤b
T
y

That’s Weak Duality.

Section 4: What Weak Duality Means Intuitively

Primal = “How much profit can I make?”
Dual = “What is the cheapest resource pricing scheme?”

Weak duality says:

You can never make more profit than the total value of the resources priced optimally.

Economically:

You can’t beat fair pricing.

Section 5: Strong Duality — When the Gap Vanishes

Now comes the powerful statement.

🔹 Strong Duality Theorem (Linear Programming)

If:

Primal is feasible

Dual is feasible

Then:

max
⁡
𝑐
𝑇
𝑥
=
min
⁡
𝑏
𝑇
𝑦
maxc
T
x=minb
T
y

The optimal values are equal.

No gap.

So Weak Duality says:

Primal
≤
Dual
Primal≤Dual

Strong Duality says:

Primal
=
Dual (at optimum)
Primal=Dual (at optimum)
Section 6: The Duality Gap

Define:

Duality Gap
=
𝑏
𝑇
𝑦
∗
−
𝑐
𝑇
𝑥
∗
Duality Gap=b
T
y
∗
−c
T
x
∗

Weak duality ⇒ gap ≥ 0
Strong duality ⇒ gap = 0

In linear programming:

Duality gap = 0 (if feasible).

Always.

That’s extraordinary.

Section 7: Why Strong Duality Is Deep

This is not obvious.

We are saying:

Two completely different optimization problems
with different dimensions
have identical optimal objective values.

That’s not trivial algebra.

It comes from:

Convexity

Geometry of polyhedra

Separation theorems

Strong duality is a geometric fact.

Section 8: Geometric Intuition

Primal feasible region = polyhedron.

Dual feasible region = another polyhedron.

At optimum:

Supporting hyperplanes align.

Objective plane touches feasible region at same height from both sides.

They meet at a shared supporting boundary.

Section 9: Complementary Slackness Connects Them

Weak duality gives inequality.

Strong duality gives equality.

Complementary slackness tells us:

When equality holds.

If:

𝑐
𝑇
𝑥
=
𝑏
𝑇
𝑦
c
T
x=b
T
y

Then complementary slackness conditions must hold.

So:

Weak Duality → inequality
Strong Duality → equality
Complementary Slackness → equality structure

Section 10: What About Nonlinear Problems?

Here’s where things get interesting.

For general nonlinear optimization:

Weak duality still holds (under mild assumptions).

Strong duality does NOT always hold.

It depends on convexity.

Section 11: Convex Optimization Case

For convex problems:

If:

Objective is convex

Constraints are convex

Slater’s condition holds (strict feasibility)

Then:

Strong duality holds.

Duality gap = 0.

This is why convex optimization is so powerful.

Section 12: When Strong Duality Fails

In non-convex problems:

Duality gap can be positive.

Dual gives only a lower bound.

Primal optimum may be strictly larger.

This happens often in:

Integer programming

Non-convex optimization

Deep learning

Section 13: Big Picture Comparison
Concept	Weak Duality	Strong Duality
Always true?	Yes	No
Requires convexity?	No	Yes (generally)
Relationship	≤	=
Duality gap	≥ 0	= 0
Section 14: The Hierarchy

Here’s the full ladder you’ve built:

Linear Regression → Optimization

Linear Programming → Duality

Weak Duality → Bound

Strong Duality → Equality

Complementary Slackness → Structure of equality

KKT → General nonlinear optimality

This is the backbone of optimization theory.

Final Intuition

Weak Duality says:

The dual is always an upper bound (for maximization problems).

Strong Duality says:

At optimality, the bound becomes exact.

Complementary Slackness says:

Here’s exactly why the bound becomes exact.

And KKT says:

This structure generalizes beyond linear problems.
