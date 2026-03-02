Perfect.
These two concepts are the **spine of modern optimization**.

If you truly understand:

* Convex Sets
* Convex Functions

Then:

* Strong duality makes sense
* KKT sufficiency makes sense
* Gradient methods become predictable
* Global optimality becomes simple

Let’s build them from first principles.

---

# 🎯 Part 1 — Convex Sets

---

# Section 1: The Promise — Why Convex Sets Matter

Optimization is hard because of **local minima**.

Convexity eliminates that problem.

If your feasible region is convex:

> Any local minimum is automatically global.

That’s powerful.

---

# Section 2: The Definition (Geometric View)

A set ( C \subseteq \mathbb{R}^n ) is **convex** if:

For any two points ( x, y \in C ) and any ( \theta \in [0,1] ):

[
\theta x + (1-\theta)y \in C
]

This means:

> The entire line segment between any two points in the set stays inside the set.

---

## Visual Intuition

Convex shape:

* No dents
* No caves
* No inward curves

Non-convex shape:

* Has a “bite” taken out
* Has holes
* Has inward curves

---

# Section 3: Convex Combinations

A convex combination of points:

[
\sum_{i=1}^k \theta_i x_i
]

Where:

* ( \theta_i \ge 0 )
* ( \sum \theta_i = 1 )

Convex set property:

> Any convex combination of points in the set remains in the set.

---

# Section 4: Important Examples of Convex Sets

### ✅ Always Convex

* Lines
* Hyperplanes
* Halfspaces
* Balls (Euclidean norm balls)
* Polyhedra
* Affine sets

### ❌ Not Convex

* Donut shape
* Two separate circles
* Crescent shape

---

# Section 5: Why Convex Sets Matter in Optimization

If feasible region is convex:

* There are no disconnected regions.
* You can move between feasible points smoothly.
* Geometry behaves nicely.

Convex feasible region + convex objective = guaranteed global solution.

---

# Section 6: Key Theorems About Convex Sets

### 1️⃣ Intersection of convex sets is convex

This is crucial.

All constraints like:

[
Ax \le b
]

form halfspaces.

Intersection of halfspaces = convex polyhedron.

That’s why linear programming is convex.

---

### 2️⃣ Supporting Hyperplane Theorem

If a point is outside a convex set:

There exists a hyperplane separating them.

This is the geometric foundation of duality.

---

---

# 🎯 Part 2 — Convex Functions

Now we move from geometry to curvature.

---

# Section 7: The Definition

A function ( f: \mathbb{R}^n \to \mathbb{R} ) is convex if:

[
f(\theta x + (1-\theta)y)
\le
\theta f(x) + (1-\theta)f(y)
]

for all ( x,y ) and ( \theta \in [0,1] ).

---

## Interpretation

The function lies **below the straight line** connecting two points on the graph.

Graphically:

Convex function looks like a bowl.

Non-convex function looks like hills and valleys.

---

# Section 8: First-Order Characterization

If ( f ) is differentiable, convexity is equivalent to:

[
f(y) \ge f(x) + \nabla f(x)^T (y - x)
]

This says:

> The function always lies above its tangent plane.

This is one of the most important formulas in optimization.

---

# Section 9: Second-Order Characterization

If twice differentiable:

[
f \text{ convex } \iff \nabla^2 f(x) \succeq 0
]

Meaning:

Hessian is positive semidefinite everywhere.

Positive curvature = convex.

---

# Section 10: Why Convex Functions Are Special

## 1️⃣ Local Minimum = Global Minimum

If:

[
\nabla f(x^*) = 0
]

Then ( x^* ) is global minimum.

No traps.

---

## 2️⃣ No Multiple Local Valleys

Nonconvex:

* Many local minima
* Hard optimization

Convex:

* One valley
* Predictable behavior

---

# Section 11: Examples of Convex Functions

### Convex

* ( x^2 )
* ( |x|_2^2 )
* Exponential function
* Log-sum-exp
* Norms

### Not Convex

* ( \sin(x) )
* ( x^4 - x^2 )
* Neural networks (generally)

---

# Section 12: Strong Convexity (Even Better)

A function is strongly convex if:

[
\nabla^2 f(x) \succeq mI
]

for some ( m > 0 ).

This gives:

* Unique minimum
* Faster convergence
* Linear convergence rate

---

# Section 13: Big Picture Connection

Now see the hierarchy:

Convex Set → nice geometry
Convex Function → nice curvature
Convex Optimization = convex set + convex function

If both hold:

* KKT conditions are sufficient
* Strong duality holds
* No duality gap
* Efficient algorithms exist

That’s why convex optimization dominates theory.

---

# Final Mental Model

Convex set = no dents in feasible region.
Convex function = no dents in objective surface.

Together:

> You’re sliding into one clean bowl inside one clean region.

No hidden traps.

No fake minima.

Only one true answer.

---

🎯 Part 1 — Subgradients
Section 1: The Promise — Why Subgradients Exist

Gradient descent is simple:

Move opposite the gradient → decrease the function

Works beautifully if function is smooth

Problem:

Some functions are nonsmooth
e.g., 
𝑓
(
𝑥
)
=
∣
𝑥
∣
f(x)=∣x∣, 
𝑓
(
𝑥
)
=
max
⁡
(
0
,
𝑥
)
f(x)=max(0,x)

Gradient doesn’t exist at “kinks”

Subgradients generalize gradients so we can still optimize nonsmooth convex functions.

Section 2: Definition

Let 
𝑓
:
𝑅
𝑛
→
𝑅
f:R
n
→R be convex.

A vector 
𝑔
∈
𝑅
𝑛
g∈R
n
 is a subgradient of 
𝑓
f at 
𝑥
0
x
0
	​

 if:

𝑓
(
𝑥
)
≥
𝑓
(
𝑥
0
)
+
𝑔
𝑇
(
𝑥
−
𝑥
0
)
,
∀
𝑥
f(x)≥f(x
0
	​

)+g
T
(x−x
0
	​

),∀x

Compare to gradient:

𝑓
(
𝑥
)
≈
𝑓
(
𝑥
0
)
+
∇
𝑓
(
𝑥
0
)
𝑇
(
𝑥
−
𝑥
0
)
f(x)≈f(x
0
	​

)+∇f(x
0
	​

)
T
(x−x
0
	​

)

Subgradient = a slope that supports the function from below.

Section 3: Geometric Intuition

At a kink (like 
𝑓
(
𝑥
)
=
∣
𝑥
∣
f(x)=∣x∣ at 
𝑥
=
0
x=0)

Draw any line passing under the graph that touches the kink

The slope of this line is a subgradient

For 
𝑓
(
𝑥
)
=
∣
𝑥
∣
f(x)=∣x∣ at 0:

𝑔
∈
[
−
1
,
1
]
g∈[−1,1]

Any slope in that interval is a valid subgradient.

Section 4: Subdifferential

The set of all subgradients at a point is called the subdifferential:

∂
𝑓
(
𝑥
0
)
=
{
𝑔
 
∣
 
𝑓
(
𝑥
)
≥
𝑓
(
𝑥
0
)
+
𝑔
𝑇
(
𝑥
−
𝑥
0
)
,
∀
𝑥
}
∂f(x
0
	​

)={g∣f(x)≥f(x
0
	​

)+g
T
(x−x
0
	​

),∀x}

If 
𝑓
f is smooth → subdifferential = singleton = gradient

If 
𝑓
f nonsmooth → subdifferential = set of slopes

Section 5: Why Subgradients Matter

Subgradient methods generalize gradient descent

Can handle nonsmooth functions like 
ℓ
1
ℓ
1
	​

 norm, hinge loss, ReLU

Provide optimality condition:

0
∈
∂
𝑓
(
𝑥
∗
)
  
⟹
  
𝑥
∗
 is optimal
0∈∂f(x
∗
)⟹x
∗
 is optimal
Section 6: Examples
1. Absolute Value

𝑓
(
𝑥
)
=
∣
𝑥
∣
f(x)=∣x∣

∂
𝑓
(
𝑥
)
=
{
{
−
1
}
,
	
𝑥
<
0


[
−
1
,
1
]
,
	
𝑥
=
0


{
1
}
,
	
𝑥
>
0
∂f(x)=
⎩
⎨
⎧
	​

{−1},
[−1,1],
{1},
	​

x<0
x=0
x>0
	​

2. Max Function

𝑓
(
𝑥
1
,
𝑥
2
)
=
max
⁡
(
𝑥
1
,
𝑥
2
)
f(x
1
	​

,x
2
	​

)=max(x
1
	​

,x
2
	​

)

Gradient exists if 
𝑥
1
≠
𝑥
2
x
1
	​


=x
2
	​


Subdifferential at 
𝑥
1
=
𝑥
2
x
1
	​

=x
2
	​

 = convex hull of 
𝑒
1
,
𝑒
2
e
1
	​

,e
2
	​


Section 7: Takeaways

Subgradient = generalized gradient

Works for nonsmooth convex functions

Central for convex optimization and dual methods

🎯 Part 2 — Supporting Hyperplane Theorem
Section 8: The Promise

Supporting hyperplanes connect geometry with optimization:

Convex sets can be “touched” without cutting through

This idea underlies duality, KKT, and Fenchel conjugates

Section 9: The Statement

Let 
𝐶
⊆
𝑅
𝑛
C⊆R
n
 be convex, and let 
𝑥
0
x
0
	​

 be a boundary point of 
𝐶
C.

There exists a nonzero vector 
𝑎
a and scalar 
𝑏
b such that:

𝑎
𝑇
𝑥
≤
𝑏
,
∀
𝑥
∈
𝐶
a
T
x≤b,∀x∈C

and

𝑎
𝑇
𝑥
0
=
𝑏
a
T
x
0
	​

=b

Hyperplane = 
{
𝑥
 
∣
 
𝑎
𝑇
𝑥
=
𝑏
}
{x∣a
T
x=b}

Hyperplane touches the set at x₀ but does not cut inside

Section 10: Geometric Intuition

Imagine a convex set like a balloon

Pick a point on the surface

Place a flat board that just touches the surface without going inside

That board = supporting hyperplane

Section 11: Why It Matters in Optimization

Duality: hyperplanes define linear inequalities in dual problems

Subgradients: subgradient at 
𝑥
0
x
0
	​

 = normal to supporting hyperplane of epigraph

KKT: multipliers are weights of supporting hyperplanes

Section 12: Example

Convex set: 
𝐶
=
{
𝑥
∈
𝑅
2
∣
𝑥
2
≥
𝑥
1
2
}
C={x∈R
2
∣x
2
	​

≥x
1
2
	​

} (parabola region)

Point on boundary: 
𝑥
0
=
(
1
,
1
)
x
0
	​

=(1,1)

Supporting hyperplane: tangent line at 
𝑥
0
x
0
	​


Equation: 
𝑥
2
=
2
𝑥
1
−
1
x
2
	​

=2x
1
	​

−1

Lies below or on the set everywhere

Section 13: Connection to Subgradients

Epigraph of 
𝑓
f = set above the function graph: 
epi
(
𝑓
)
=
{
(
𝑥
,
𝑡
)
∣
𝑡
≥
𝑓
(
𝑥
)
}
epi(f)={(x,t)∣t≥f(x)}

Supporting hyperplane to epigraph → subgradient of 
𝑓
f at that point

This shows subgradients = geometric supporting hyperplanes.

Section 14: Big Picture

Convex Set → “nice geometry”

Supporting Hyperplane → boundary touch

Convex Function → epigraph = convex set

Subgradient → slope of supporting hyperplane

Everything connects naturally:

Convex sets → feasible region

Supporting hyperplanes → dual constraints

Subgradients → generalize gradients for nonsmooth functions

🎯 Part 1 — Slater’s Condition
Section 1: The Promise — Why Slater’s Condition Exists

We’ve seen:

Convex functions

Convex feasible sets

Supporting hyperplanes

Subgradients

Now, we want strong duality — the guarantee that:

Primal optimal
=
Dual optimal
Primal optimal=Dual optimal

Problem:

Even for convex problems, duality gap can exist if constraints are “too tight” or degenerate.

Slater’s condition is the criterion that ensures no duality gap for convex problems.

Section 2: The Statement (Inequality Constraints)

Consider a convex optimization problem:

minimize 
	
𝑓
0
(
𝑥
)


subject to 
	
𝑓
𝑖
(
𝑥
)
≤
0
,
𝑖
=
1
,
…
,
𝑚


	
𝐴
𝑥
=
𝑏
minimize 
subject to 
	​

f
0
	​

(x)
f
i
	​

(x)≤0,i=1,…,m
Ax=b
	​


𝑓
0
,
𝑓
𝑖
f
0
	​

,f
i
	​

 convex

𝐴
𝑥
=
𝑏
Ax=b affine

Slater’s condition:

There exists a point 
𝑥
x in the relative interior of the domain such that

𝑓
𝑖
(
𝑥
)
<
0
∀
𝑖
f
i
	​

(x)<0∀i
𝐴
𝑥
=
𝑏
Ax=b

That is, there is a strictly feasible point

Intuition:

All inequality constraints are not on the edge; you’re “inside” the feasible region

Prevents degeneracy that breaks strong duality

Section 3: Geometric Intuition

Convex set = feasible region

Slater’s condition = there exists a point deep inside the region, not touching boundaries of inequalities

Think of it like a ball that fits strictly inside a polygon rather than just touching the sides

Section 4: Why Slater’s Condition Matters

If convex + Slater → strong duality holds

Duality gap = 0 → optimal solutions of dual and primal coincide

Guarantees existence of KKT multipliers

Section 5: Example
Problem:
minimize 
	
𝑓
0
(
𝑥
)
=
𝑥
2


subject to 
	
𝑥
≥
1
minimize 
subject to 
	​

f
0
	​

(x)=x
2
x≥1
	​


Convert to 
𝑓
1
(
𝑥
)
=
1
−
𝑥
≤
0
f
1
	​

(x)=1−x≤0

Check Slater:

Need 
𝑥
x s.t. 
1
−
𝑥
<
0
1−x<0 → 
𝑥
>
1
x>1

Pick 
𝑥
=
2
x=2 → strictly feasible → Slater satisfied

Consequence:

Strong duality holds → dual optimal = primal optimal

KKT conditions are necessary and sufficient

🎯 Part 2 — Strong Duality
Section 6: The Promise — What Strong Duality Gives You

Duality is powerful:

Solving dual problem often easier

Lagrange multipliers give shadow prices

Sensitivity analysis becomes simple

Weak duality always holds:

𝑑
∗
≤
𝑝
∗
d
∗
≤p
∗

𝑑
∗
d
∗
 = dual optimal

𝑝
∗
p
∗
 = primal optimal

Strong duality:

𝑑
∗
=
𝑝
∗
d
∗
=p
∗

Holds for convex problems if Slater’s condition is satisfied

Section 7: Why Convex + Slater Guarantees Strong Duality

Convex feasible region → no “valleys” or “pockets”

Convex objective → bowl-shaped surface

Slater → strictly feasible → ensures supporting hyperplanes exist without touching boundary

Then, dual problem touches primal optimum exactly

This eliminates duality gap.

Section 8: KKT + Strong Duality

When strong duality holds:

KKT conditions are both necessary and sufficient for optimality

Lagrange multipliers exist

You can solve primal by solving dual

Section 9: Examples of Slater Failing
1. Empty Interior
minimize 
	
𝑥
2


subject to 
	
𝑥
2
≤
0
minimize 
subject to 
	​

x
2
x
2
≤0
	​


Feasible point 
𝑥
=
0
x=0 is on the boundary, not strictly feasible

Slater fails

Strong duality may fail

2. Nonconvex Problems

Slater is meaningless

Strong duality may never hold

Section 10: Practical Tips

Check strict feasibility of all inequality constraints

For equality constraints → must be affine

In ML, most convex loss + regularizer problems satisfy Slater automatically

e.g., 
ℓ
2
ℓ
2
	​

 SVM, LASSO

Section 11: Big Picture — Flow

Convex problem

Check Slater → strictly feasible

Then strong duality holds → dual = primal

KKT conditions sufficient → solve dual, get primal

Subgradients & supporting hyperplanes justify the multipliers

Section 12: Mental Model

Weak duality = “dual underestimates primal”

Slater = “feasible region has breathing room”

Strong duality = “dual catches up exactly”

KKT = “dual multipliers tell us how to move inside the feasible bowl”
