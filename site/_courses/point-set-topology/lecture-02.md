---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 2
title: "The Standard Topology on the Real Line and the Plane"
coverage: >
  Introduces the open interval and property (*) on the real line, verifying
  that subsets satisfying (*) form the standard topology on R via the
  finite-minimum argument. Extends the construction to R2 using open
  squares S_epsilon(a,b) of side length 2*epsilon, stating property (*) on
  the plane. Concludes by contrasting the open unit disc and the closed
  unit disc as example and non-example for property (*) on R2.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 6
corrections: 1
depends_on:
  - lecture: 1
    title: "Topological Spaces: Definition and First Examples"
    relationship: "Supplies the topology axioms (T1)–(T3) used to establish that subsets satisfying property (*) form a topology."
used_in:
  - lecture: 3
    title: "The Standard Topology on Rn, Open Sets, and Bases"
    relationship: "Lecture 3 completes the verification of the topology on R2, extends it to Rn, names sets in tau 'open sets', and introduces bases."
notation:
  - symbol: "$(a,b)$"
    gloss: "Open interval in $\\mathbb{R}$, $\\lbrace x \\in \\mathbb{R} : a < x < b\\rbrace$"
  - symbol: "$(\\ast_{\\mathbb{R}})$"
    gloss: "Property $(\\ast)$ on $\\mathbb{R}$: $\\forall x \\in U\\ \\exists \\varepsilon > 0$ such that $(x-\\varepsilon, x+\\varepsilon) \\subseteq U$"
  - symbol: "$S_\\varepsilon(a,b)$"
    gloss: "Open square in $\\mathbb{R}^2$ centered at $(a,b)$ of side length $2\\varepsilon$"
  - symbol: "$(\\ast_{\\mathbb{R}^2})$"
    gloss: "Property $(\\ast)$ on $\\mathbb{R}^2$: $\\forall (a,b) \\in U\\ \\exists \\varepsilon > 0$ such that $S_\\varepsilon(a,b) \\subseteq U$"
  - symbol: "$\\tau$"
    gloss: "The standard topology on $\\mathbb{R}$ (or $\\mathbb{R}^2$), consisting of all subsets satisfying property $(\\ast)$"
prev: lecture-01
next: lecture-03
---

# Lecture 2 — The Standard Topology on the Real Line and the Plane

## Where we are

In [Lecture 1]({{ site.baseurl }}/point-set-topology/lecture-01/), we established that a topology is extra structure chosen on a set, satisfying three axioms (T1)–(T3). The three universal topologies introduced there—trivial, discrete, and finite complement—can be placed on any set whatsoever, precisely because they ignore the underlying geometry entirely.

This lecture builds the first topologies that genuinely capture Euclidean geometry: the standard topologies on $\mathbb{R}$ and $\mathbb{R}^2$. Rather than declaring all members of $\tau$ at once, we test subsets through a local condition, property $(\ast)$, requiring that every point possesses symmetric breathing room inside the set. Verifying that such sets form a topology introduces the finite minimum argument, the governing technique for intersections throughout the course.

---

## Open intervals on the real line

In the previous lecture, we saw how to define different topologies on the same set $X$, where $X$ could be completely arbitrary. Today, we turn to specific examples that are central to this course.

We begin with the standard topology on the set of real numbers $\mathbb{R}$ (the real line).

Recall first the definition of an open interval in $\mathbb{R}$.

{% capture corr_interval %}
**As transcribed:** $(a,b) = \lbrace x \in \mathbb{R} : x < a \text{ and } x < b\rbrace$.

**What is meant:** $(a,b) = \lbrace x \in \mathbb{R} : a < x < b\rbrace$.

**Why:** The condition as transcribed defines the ray $(-\infty, \min\lbrace a, b\rbrace)$. The lecturer's explicit assumption that $a < b$, his subsequent specialization to $a = -\infty$ as $(-\infty, b) = \lbrace x \in \mathbb{R} : x < b\rbrace$ and $b = +\infty$ as $(a, +\infty) = \lbrace x \in \mathbb{R} : x > a\rbrace$, and his identification $\mathbb{R} = (-\infty, +\infty)$ make certain that the standard bounded open interval was meant.
{% endcapture %}
{% include block.html type="correction" title="Correction: Definition of the open interval" content=corr_interval %}

{% capture def_interval %}
Let $a, b \in \mathbb{R} \cup \lbrace -\infty, +\infty\rbrace$ with $a < b$. By the **open interval** $(a,b)$ in $\mathbb{R}$, we mean the subset
$$(a,b) = \lbrace x \in \mathbb{R} \;:\; a < x < b \rbrace.$$
In particular:
- If $a = -\infty$ and $b \in \mathbb{R}$, then $(-\infty, b) = \lbrace x \in \mathbb{R} : x < b \rbrace$.
- If $a \in \mathbb{R}$ and $b = +\infty$, then $(a, +\infty) = \lbrace x \in \mathbb{R} : x > a \rbrace$.
- If $a = -\infty$ and $b = +\infty$, then $(-\infty, +\infty) = \mathbb{R}$.
{% endcapture %}
{% include block.html type="definition" title="Definition 2.1 (Open interval in R)" content=def_interval %}

---

## Property (*)

We want to define a topology on the real line $\mathbb{R}$. To do this, we first define a condition on subsets of $\mathbb{R}$, which we denote by $(\ast)$ (or $(\ast_{\mathbb{R}})$ when distinguishing it from higher dimensions).

{% capture def_star %}
Let $U \subseteq \mathbb{R}$ be a subset. We say that $U$ satisfies **property $(\ast)$** if for every point $x \in U$, there exists a strictly positive real number $\varepsilon > 0$ (depending on $x$) such that
$$(x - \varepsilon, x + \varepsilon) \subseteq U.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 2.2 (Property (*))" content=def_star %}

The lecturer explicitly emphasizes the quantifier order: the positive number $\varepsilon$ depends on the chosen point $x$, and need not be uniform across all points of $U$.

{% capture supp_quantifiers %}
The quantifier structure of property $(\ast)$ is:
$$\forall x \in U, \quad \exists \varepsilon > 0 \quad \text{such that} \quad (x - \varepsilon, x + \varepsilon) \subseteq U.$$
The choice of $\varepsilon$ is permitted to vary from point to point. As $x$ approaches the boundary of $U$, $\varepsilon$ will typically need to be chosen smaller and smaller. There is no requirement that a single $\varepsilon > 0$ work simultaneously for all $x \in U$.
{% endcapture %}
{% include block.html type="supplement" title="Quantifier order in property (*)" content=supp_quantifiers %}

---

## Testing property (*): intervals with and without endpoints

To understand what kinds of subsets satisfy property $(\ast)$, the lecturer presents two introductory examples.

### Example: The open interval (0,1)

{% capture ex_open_interval %}
The open interval $(0,1) = \lbrace x \in \mathbb{R} : 0 < x < 1\rbrace$ satisfies property $(\ast)$.

**Verification.** Let $x \in (0,1)$. Then $0 < x < 1$, so both $x > 0$ and $1 - x > 0$. The distance from $x$ to the left endpoint $0$ is $x$, and the distance from $x$ to the right endpoint $1$ is $1 - x$.

Define
$$\varepsilon = \min \left\lbrace \frac{x}{2}, \; \frac{1-x}{2} \right\rbrace.$$
Since $x > 0$ and $1 - x > 0$, both $x/2$ and $(1-x)/2$ are strictly positive, and hence $\varepsilon > 0$.

We claim that $(x - \varepsilon, x + \varepsilon) \subseteq (0,1)$. Indeed, if $y \in (x - \varepsilon, x + \varepsilon)$, then:
$$y > x - \varepsilon \ge x - \frac{x}{2} = \frac{x}{2} > 0,$$
and
$$y < x + \varepsilon \le x + \frac{1-x}{2} = \frac{1+x}{2} < \frac{1+1}{2} = 1.$$
Thus $0 < y < 1$, so $y \in (0,1)$. This shows that $(x - \varepsilon, x + \varepsilon) \subseteq (0,1)$, proving that $(0,1)$ satisfies property $(\ast)$.

{% include figure.html
   src="point-set-topology/lecture-02/epsilon-in-open-interval.svg"
   caption="Choosing $\varepsilon = \min\lbrace x/2,\,(1-x)/2\rbrace$ places the whole interval $(x-\varepsilon,\,x+\varepsilon)$ inside $(0,1)$ by staying strictly within half the distance to each boundary."
   alt="The open interval from 0 to 1 on a number line, with a point x inside it. The distance from 0 to x and the distance from x to 1 are both marked. A shorter interval centred at x lies strictly between 0 and 1." %}
{% endcapture %}
{% include block.html type="example" title="Example: The interval (0,1) satisfies (*)" content=ex_open_interval %}

### Non-example: The half-open interval [0,1)

{% capture nonex_half_open %}
Consider the half-open interval
$$[0,1) = \lbrace x \in \mathbb{R} \;:\; 0 \le x < 1 \rbrace.$$
This subset does **not** satisfy property $(\ast)$.

**Verification.** Consider the point $0 \in [0,1)$. For any $\varepsilon > 0$, the interval around $0$ of radius $\varepsilon$ is
$$(0 - \varepsilon, 0 + \varepsilon) = (-\varepsilon, \varepsilon).$$
No matter how small $\varepsilon > 0$ is chosen, the interval $(-\varepsilon, \varepsilon)$ contains negative numbers; for instance, the midpoint $-\varepsilon/2$ satisfies $-\varepsilon < -\varepsilon/2 < 0$. But negative numbers do not belong to $[0,1)$.

Therefore, there is no $\varepsilon > 0$ such that $(-\varepsilon, \varepsilon) \subseteq [0,1)$. Because property $(\ast)$ fails at $x = 0$, the set $[0,1)$ does not satisfy property $(\ast)$.

{% include figure.html
   src="point-set-topology/lecture-02/half-open-interval-failure.svg"
   caption="The half-open interval $[0,1)$ fails property $(\ast)$ at $x = 0$: any interval $(-\varepsilon, \varepsilon)$ protrudes into the negative reals $\mathbb{R} < 0$, escaping the set."
   alt="The half-open interval [0,1) on a number line with a solid dot at 0 and an open circle at 1. An epsilon-interval around 0 extends to the left into negative numbers, highlighted as escaping." %}
{% endcapture %}
{% include block.html type="non-example" title="Non-example: The interval [0,1) fails (*)" content=nonex_half_open %}

{% capture supp_open_endpoints %}
The contrast between $(0,1)$ and $[0,1)$ illustrates the general rule on the real line: an included boundary point always obstructs property $(\ast)$. At any point strictly between two endpoints, there is non-zero room on both sides to fit a symmetric interval $(x-\varepsilon, x+\varepsilon)$. But at an included endpoint, one side immediately steps outside into the complement, so no two-sided symmetric interval can fit inside.
{% endcapture %}
{% include block.html type="supplement" title="Why included endpoints obstruct property (*)" content=supp_open_endpoints %}

---

## Example 4: the standard topology on the real line

Having clarified which subsets satisfy property $(\ast)$, we now define a topology on $\mathbb{R}$ consisting of all such subsets.

{% capture ex4_def %}
Let $\tau \subseteq \mathcal{P}(\mathbb{R})$ be the collection of all subsets of $\mathbb{R}$ that satisfy property $(\ast)$:
$$\tau = \lbrace U \subseteq \mathbb{R} \;:\; U \text{ satisfies property } (\ast) \rbrace.$$
Then $\tau$ defines a topology on $\mathbb{R}$, called the **standard topology** on the real line.
{% endcapture %}
{% include block.html type="example" title="Example 4 (Standard topology on R)" content=ex4_def %}

To check that $\tau$ defines a topology on $\mathbb{R}$, we need to check that it satisfies the three defining conditions for a topology. Let us check these one by one.

{% capture ex4_proof %}
**(T1).** Recall that the first condition was that $\varnothing$, the empty set, and the entire set $\mathbb{R}$ should be in $\tau$.

Clearly, the empty set is in $\tau$ because there is nothing to check: there is no $x$ in the empty set and therefore there is no condition to check, so this is vacuously true. And it is also clear that $\mathbb{R}$ is in $\tau$, as for any $x \in \mathbb{R}$, we can simply take $\varepsilon = 1$. Then clearly $(x - 1, x + 1) \subseteq \mathbb{R}$.

So therefore, this first defining condition for being a topology is satisfied. ✓

**(T2).** For the second condition, we need that if $U_1, U_2, \dots, U_n \in \tau$ are finitely many subsets of $\mathbb{R}$, then their intersection $\bigcap_{i=1}^n U_i$ should also be in $\tau$.

Let us check that this condition is satisfied: we need to check that this intersection $\bigcap_{i=1}^n U_i$ satisfies property $(\ast)$.

Let us choose some $x \in \bigcap_{i=1}^n U_i$. In particular, this implies that $x \in U_i$ for all $i \in \lbrace 1, 2, \dots, n \rbrace$. Since each $U_i$ satisfies property $(\ast)$, there exists some $\varepsilon_i > 0$ such that
$$(x - \varepsilon_i, \; x + \varepsilon_i) \subseteq U_i.$$

Now let
$$\varepsilon = \min \lbrace \varepsilon_1, \varepsilon_2, \dots, \varepsilon_n \rbrace.$$
Clearly, $\varepsilon$ is positive because we have finitely many positive real numbers and we take the smallest one among them, so that is also going to be positive ($\varepsilon > 0$).

It is also clear that $(x - \varepsilon, x + \varepsilon) \subseteq (x - \varepsilon_i, x + \varepsilon_i)$ because $\varepsilon$ is the smallest among all these $\varepsilon_i$. This implies that
$$(x - \varepsilon, \; x + \varepsilon) \subseteq (x - \varepsilon_i, \; x + \varepsilon_i) \subseteq U_i$$
for all $i$. In particular, this implies that
$$(x - \varepsilon, \; x + \varepsilon) \subseteq \bigcap_{i=1}^n U_i.$$

So this shows that this intersection $\bigcap_{i=1}^n U_i$ satisfies property $(\ast)$. Therefore, the second condition for being a topology is also satisfied. ✓

{% include figure.html
   src="point-set-topology/lecture-02/nested-epsilons-min.svg"
   caption="The finite minimum argument in condition (T2): choosing $\varepsilon = \min\lbrace\varepsilon_1, \dots, \varepsilon_n\rbrace$ produces an interval $(x-\varepsilon, x+\varepsilon)$ that simultaneously nests inside every $(x-\varepsilon_i, x+\varepsilon_i) \subseteq U_i$."
   alt="Nested concentric intervals on a number line around point x. The smallest interval, with radius epsilon equal to the minimum of the radii, lies inside all larger intervals." %}

<span id="condition-t3-arbitrary-unions"></span>
**(T3).** And finally, we have to check one more condition. Let $I$ be a set, and suppose for each $i \in I$ we are given $U_i \in \tau$. Then we need to show that the union $\bigcup_{i \in I} U_i$ is in $\tau$. That is, it satisfies property $(\ast)$.

Once again, this is easy: we apply the same method that we used in the second case.

We take any $x \in \bigcup_{i \in I} U_i$. Then there is some $j \in I$ such that $x \in U_j$. Now since $U_j$ satisfies property $(\ast)$, there is an $\varepsilon > 0$ such that
$$(x - \varepsilon, \; x + \varepsilon) \subseteq U_j.$$
In particular, this implies that
$$(x - \varepsilon, \; x + \varepsilon) \subseteq U_j \subseteq \bigcup_{i \in I} U_i.$$

Thus, we have proved that this union satisfies our property $(\ast)$. That is, this union is also in $\tau$. So therefore, $\tau$ also satisfies the third condition. ✓

All this implies that $\tau$ defines a topology on $\mathbb{R}$, which we call the standard topology. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Example 4" content=ex4_proof %}

{% capture supp_min_infinite %}
Observe where the proof of (T2) crucially used finiteness: the minimum of a finite collection of strictly positive numbers is strictly positive:
$$\varepsilon_1, \dots, \varepsilon_n > 0 \implies \min\lbrace \varepsilon_1, \dots, \varepsilon_n \rbrace > 0.$$
For an infinite collection $\lbrace \varepsilon_n \rbrace_{n=1}^\infty$, the infimum can be zero. For example, taking $U_n = (-1/n, 1/n) \in \tau$ for each $n \ge 1$, the intersection over all $n \ge 1$ is
$$\bigcap_{n=1}^\infty \left( -\frac{1}{n}, \; \frac{1}{n} \right) = \lbrace 0 \rbrace.$$
The singleton set $\lbrace 0 \rbrace$ does **not** satisfy property $(\ast)$, because for any $\varepsilon > 0$, the interval $(-\varepsilon, \varepsilon)$ contains non-zero points and is not contained in $\lbrace 0 \rbrace$. Thus $\lbrace 0 \rbrace \notin \tau$. This reinforces once again the fundamental asymmetry between finite intersections and arbitrary unions in topology.
{% endcapture %}
{% include block.html type="supplement" title="Where finiteness in (T2) is essential" content=supp_min_infinite %}

---

## Transition to the plane and higher dimensions

In the exact same way that we defined this topology on $\mathbb{R}$, we can define a topology on $\mathbb{R}^2$, and more generally on $\mathbb{R}^n$.

We now examine the two-dimensional case $\mathbb{R}^2$ in detail. The generalization to $\mathbb{R}^n$ will be stated as an exercise.

This is our fifth example: the **standard topology on $\mathbb{R}^2$**.

---

## Open squares in the plane

Before defining the topology on $\mathbb{R}^2$, we require the two-dimensional analogue of the symmetric open interval $(x-\varepsilon, x+\varepsilon)$. In the plane, the lecturer chooses to use an **open square** of side length $2\varepsilon$.

{% capture def_square %}
Let $(a,b) \in \mathbb{R}^2$ and let $\varepsilon > 0$. We define the **open square of side length $2\varepsilon$ centered at $(a,b)$**, denoted $S_\varepsilon(a,b)$, by
$$S_\varepsilon(a,b) = \lbrace (x,y) \in \mathbb{R}^2 \;:\; \lvert x - a \rvert < \varepsilon \ \text{ and } \ \lvert y - b \rvert < \varepsilon \rbrace.$$
Equivalently, in terms of intervals on the coordinate axes:
$$S_\varepsilon(a,b) = (a - \varepsilon, \; a + \varepsilon) \times (b - \varepsilon, \; b + \varepsilon).$$

{% include figure.html
   src="point-set-topology/lecture-02/open-square-s-epsilon.svg"
   caption="The open square $S_\varepsilon(a,b)$ of side length $2\varepsilon$ centered at $(a,b)$, defined by $\lvert x-a\rvert < \varepsilon$ and $\lvert y-b\rvert < \varepsilon$. The dashed perimeter indicates that boundary edges and vertices are excluded."
   alt="An open square in the Cartesian plane centered at point (a,b). All four distances from the center to the edges are marked as epsilon, and the perimeter is drawn dashed." %}
{% endcapture %}
{% include block.html type="definition" title="Definition 2.3 (Open square in R2)" content=def_square %}

As the lecturer explains from the board diagram: the center is the point $(a,b)$, and moving to each of the four edges from the center covers a distance of $\varepsilon$. The total horizontal length is $2\varepsilon$ and the total vertical height is $2\varepsilon$. The strict inequalities mean that the perimeter edges and the four corners are excluded from $S_\varepsilon(a,b)$.

---

## Example 5: property (*) on the plane and disc examples

With open squares defined, we can now formulate the two-dimensional analogue of property $(\ast)$.

{% capture def_star2 %}
Let $U \subseteq \mathbb{R}^2$ be a subset. We say that $U$ satisfies **property $(\ast)$** (or $(\ast_{\mathbb{R}^2})$) if for every point $(a,b) \in U$, there exists a strictly positive real number $\varepsilon > 0$ (which may depend on $(a,b)$) such that
$$S_\varepsilon(a,b) \subseteq U.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 2.4 (Property (*) on R2)" content=def_star2 %}

{% capture supp_star_convention %}
The lecturer comments: *"If you want, you can denote it by star two, so that you don't confuse it with the same star earlier. But I will be lazy, and I will call this property star."* 

To preserve the lecturer's notation while preventing ambiguity across dimensions, we use $(\ast)$ in informal context and $(\ast_{\mathbb{R}^2})$ when explicit distinction from $(\ast_{\mathbb{R}})$ is needed.
{% endcapture %}
{% include block.html type="supplement" title="Convention: Notation for property (*)" content=supp_star_convention %}

As in the one-dimensional case, we contrast a set that satisfies property $(\ast)$ with one that does not.

### Example: The open unit disc

{% capture ex_open_disc %}
Consider the subset $U \subseteq \mathbb{R}^2$ given by
$$U = \lbrace (a,b) \in \mathbb{R}^2 \;:\; a^2 + b^2 < 1 \rbrace.$$
This is the region strictly inside the circle of radius $1$ centered at the origin (the **open unit disc**).

**Claim.** $U$ satisfies property $(\ast)$.

Geometrically, if we take any point $(a,b)$ in the interior (the green region on the board), the distance from $(a,b)$ to the origin is strictly less than $1$. Because this point sits strictly inside the circle, there is positive clearance to the boundary. Consequently, we can always choose a small open square $S_\varepsilon(a,b)$ centered at $(a,b)$ that fits completely inside $U$. The algebraic construction of $\varepsilon$ is left as an exercise ([Exercise 2.1](#exercise-2-1-open-unit-disc-satisfies-property)).

{% include figure.html
   src="point-set-topology/lecture-02/open-disc-property-star.svg"
   caption="The open unit disc $U = \lbrace (x,y) \in \mathbb{R}^2 : x^2 + y^2 < 1\rbrace$. Around every point $(a,b) \in U$, a sufficiently small open square $S_\varepsilon(a,b)$ fits entirely inside the disc."
   alt="The open unit disc in R^2 with a dashed boundary circle. An interior point (a,b) is surrounded by a small dashed square that lies entirely inside the disc." %}
{% endcapture %}
{% include block.html type="example" title="Example: The open unit disc satisfies (*)" content=ex_open_disc %}

### Non-example: The closed unit disc

{% capture nonex_closed_disc %}
Consider the subset $V \subseteq \mathbb{R}^2$ given by
$$V = \lbrace (a,b) \in \mathbb{R}^2 \;:\; a^2 + b^2 \le 1 \rbrace.$$
This set includes the boundary circle $a^2 + b^2 = 1$ (the **closed unit disc**).

**Claim.** $V$ does **not** satisfy property $(\ast)$.

**Verification.** Consider the boundary point $(1,0) \in V$, since $1^2 + 0^2 = 1 \le 1$.

For any $\varepsilon > 0$, consider the open square $S_\varepsilon(1,0)$ centered at $(1,0)$:
$$S_\varepsilon(1,0) = (1 - \varepsilon, \; 1 + \varepsilon) \times (-\varepsilon, \; \varepsilon).$$
No matter how small $\varepsilon > 0$ is chosen, $S_\varepsilon(1,0)$ contains points of the form $(1 + \delta, 0)$ where $0 < \delta < \varepsilon$. For any such point:
$$(1 + \delta)^2 + 0^2 = (1 + \delta)^2 > 1.$$
Therefore, $(1 + \delta, 0) \notin V$.

This demonstrates that for every $\varepsilon > 0$, the open square $S_\varepsilon(1,0)$ fails to be contained in $V$:
$$S_\varepsilon(1,0) \not\subseteq V \quad \text{for all } \varepsilon > 0.$$
Because property $(\ast)$ fails at the point $(1,0) \in V$, the subset $V$ does not satisfy property $(\ast)$. The formal verification is left as an exercise ([Exercise 2.2](#exercise-2-2-closed-unit-disc-fails-property)).

{% include figure.html
   src="point-set-topology/lecture-02/closed-disc-failure.svg"
   caption="The closed unit disc $V = \lbrace (x,y) \in \mathbb{R}^2 : x^2 + y^2 \le 1\rbrace$ fails property $(\ast)$ at $(1,0)$: every open square $S_\varepsilon(1,0)$ protrudes past $x = 1$ into $x^2 + y^2 > 1$."
   alt="The closed unit disc with a solid boundary circle. Squares of different sizes centered at the boundary point (1,0) extend across the boundary into the exterior region." %}
{% endcapture %}
{% include block.html type="non-example" title="Non-example: The closed unit disc fails (*)" content=nonex_closed_disc %}

---

## Closing and forward reference

The lecture pauses at this point, having defined property $(\ast)$ on $\mathbb{R}^2$ and illustrated it with the open and closed unit discs.

In [Lecture 3]({{ site.baseurl }}/point-set-topology/lecture-03/), we will complete the proof that the collection $\tau$ of subsets of $\mathbb{R}^2$ satisfying property $(\ast)$ defines a topology on $\mathbb{R}^2$, generalize this construction to $\mathbb{R}^n$, and introduce the formal term **open set** along with the central concept of a **basis** for a topology.

---

## Exercises

{% capture ex21_content %}
Let $U = \lbrace (a,b) \in \mathbb{R}^2 : a^2 + b^2 < 1 \rbrace$ be the open unit disc. For an arbitrary point $(a,b) \in U$, find an explicit formula for $\varepsilon > 0$ in terms of $a$ and $b$ such that the open square $S_\varepsilon(a,b) \subseteq U$.
{% endcapture %}
{% capture ex21_sol %}
Let $(a,b) \in U$, so $a^2 + b^2 < 1$. Then $1 - (a^2 + b^2) > 0$.

For any point $(x,y) \in S_\varepsilon(a,b)$, we have $\lvert x - a \rvert < \varepsilon$ and $\lvert y - b \rvert < \varepsilon$. Expanding $(x-a)$ and $(y-b)$:
$$x^2 = (a + (x-a))^2 = a^2 + 2a(x-a) + (x-a)^2 \le a^2 + 2\lvert a \rvert \lvert x-a \rvert + (x-a)^2 < a^2 + 2\lvert a \rvert \varepsilon + \varepsilon^2,$$
$$y^2 = (b + (y-b))^2 = b^2 + 2b(y-b) + (y-b)^2 \le b^2 + 2\lvert b \rvert \lvert y-b \rvert + (y-b)^2 < b^2 + 2\lvert b \rvert \varepsilon + \varepsilon^2.$$
Adding these two inequalities:
$$x^2 + y^2 < a^2 + b^2 + 2(\lvert a \rvert + \lvert b \rvert)\varepsilon + 2\varepsilon^2.$$
Since $a^2 \le a^2 + b^2 < 1$ and $b^2 \le a^2 + b^2 < 1$, we have $\lvert a \rvert < 1$ and $\lvert b \rvert < 1$, so $\lvert a \rvert + \lvert b \rvert < 2$.
Requiring $\varepsilon \le 1$ gives $\varepsilon^2 \le \varepsilon$, so:
$$2(\lvert a \rvert + \lvert b \rvert)\varepsilon + 2\varepsilon^2 < 2(2)\varepsilon + 2\varepsilon = 6\varepsilon.$$
Thus $x^2 + y^2 < a^2 + b^2 + 6\varepsilon$. To guarantee $x^2 + y^2 < 1$, it suffices to have $6\varepsilon \le 1 - (a^2 + b^2)$. We may therefore choose:
$$\varepsilon = \min \left\lbrace 1, \; \frac{1 - (a^2 + b^2)}{7} \right\rbrace > 0.$$
With this choice, for any $(x,y) \in S_\varepsilon(a,b)$, we have $x^2 + y^2 < a^2 + b^2 + 6\frac{1 - (a^2 + b^2)}{7} < a^2 + b^2 + (1 - (a^2 + b^2)) = 1$. Hence $(x,y) \in U$, which proves $S_\varepsilon(a,b) \subseteq U$.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 2.1 (Open unit disc satisfies property (*))" content=ex21_content solution=ex21_sol %}

{% capture ex22_content %}
Prove rigorously that for any $\varepsilon > 0$, the open square $S_\varepsilon(1,0)$ is not contained in the closed unit disc $V = \lbrace (a,b) \in \mathbb{R}^2 : a^2 + b^2 \le 1 \rbrace$.
{% endcapture %}
{% capture ex22_sol %}
Let $\varepsilon > 0$ be given. Consider the point $p = (1 + \varepsilon/2, \; 0)$.
Since $\lvert (1 + \varepsilon/2) - 1 \rvert = \varepsilon/2 < \varepsilon$ and $\lvert 0 - 0 \rvert = 0 < \varepsilon$, the point $p$ belongs to the open square $S_\varepsilon(1,0)$.
However, the sum of squares for $p$ is:
$$\left(1 + \frac{\varepsilon}{2}\right)^2 + 0^2 = 1 + \varepsilon + \frac{\varepsilon^2}{4} > 1.$$
Thus $p \notin V$. Because $p \in S_\varepsilon(1,0)$ but $p \notin V$, it follows that $S_\varepsilon(1,0) \not\subseteq V$. Since $\varepsilon > 0$ was arbitrary, no such $\varepsilon$ exists, and property $(\ast)$ fails at $(1,0)$.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 2.2 (Closed unit disc fails property (*))" content=ex22_content solution=ex22_sol %}

{% capture ex23_content %}
Formulate the generalization of property $(\ast)$ to Euclidean space $\mathbb{R}^n$ for $n \ge 1$, using open hypercubes $S_\varepsilon(x)$. What is the corresponding standard topology on $\mathbb{R}^n$?
{% endcapture %}
{% capture ex23_sol %}
For $x = (x_1, \dots, x_n) \in \mathbb{R}^n$ and $\varepsilon > 0$, define the open hypercube
$$S_\varepsilon(x) = \lbrace y = (y_1, \dots, y_n) \in \mathbb{R}^n \;:\; \lvert y_i - x_i \rvert < \varepsilon \text{ for all } i \in \lbrace 1, \dots, n \rbrace \rbrace = \prod_{i=1}^n (x_i - \varepsilon, \; x_i + \varepsilon).$$
A subset $U \subseteq \mathbb{R}^n$ satisfies property $(\ast_{\mathbb{R}^n})$ if for every $x \in U$, there exists $\varepsilon > 0$ such that $S_\varepsilon(x) \subseteq U$.
The collection $\tau = \lbrace U \subseteq \mathbb{R}^n : U \text{ satisfies } (\ast_{\mathbb{R}^n}) \rbrace$ defines the standard topology on $\mathbb{R}^n$.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 2.3 (Generalization to Rn)" content=ex23_content solution=ex23_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Definition 2.1 (Open interval in R)](#definition-2-1-open-interval-in-r): $(a,b) = \lbrace x \in \mathbb{R} : a < x < b\rbrace$ for $a < b$ with $a, b \in \mathbb{R} \cup \lbrace -\infty, +\infty\rbrace$.
- [Definition 2.2 (Property (*))](#definition-2-2-property): $U \subseteq \mathbb{R}$ satisfies $(\ast)$ if for every $x \in U$ there exists $\varepsilon > 0$ such that $(x-\varepsilon, x+\varepsilon) \subseteq U$.
- [Example: The interval (0,1) satisfies (*)](#example-the-interval-0-1-satisfies): $(0,1)$ satisfies $(\ast)$ via $\varepsilon = \min\lbrace x/2, (1-x)/2\rbrace > 0$.
- [Non-example: The interval [0,1) fails (*)](#non-example-the-interval-0-1-fails): $[0,1)$ fails $(\ast)$ at $0$ because $(-\varepsilon, \varepsilon) \not\subseteq [0,1)$ for every $\varepsilon > 0$.
- [Example 4 (Standard topology on R)](#example-4-standard-topology-on-r): $\tau = \lbrace U \subseteq \mathbb{R} : U \text{ satisfies } (\ast)\rbrace$ is a topology on $\mathbb{R}$, verified via the finite minimum argument for (T2).
- [Definition 2.3 (Open square in R2)](#definition-2-3-open-square-in-r2): $S_\varepsilon(a,b) = (a-\varepsilon, a+\varepsilon) \times (b-\varepsilon, b+\varepsilon)$, an open square of side length $2\varepsilon$ centered at $(a,b)$.
- [Definition 2.4 (Property (*) on R2)](#definition-2-4-property-on-r2): $U \subseteq \mathbb{R}^2$ satisfies $(\ast)$ if for every $(a,b) \in U$ there exists $\varepsilon > 0$ such that $S_\varepsilon(a,b) \subseteq U$.
- [Example: The open unit disc satisfies (*)](#example-the-open-unit-disc-satisfies): $U = \lbrace (a,b) \in \mathbb{R}^2 : a^2 + b^2 < 1\rbrace$ satisfies $(\ast)$ in $\mathbb{R}^2$.
- [Non-example: The closed unit disc fails (*)](#non-example-the-closed-unit-disc-fails): $V = \lbrace (a,b) \in \mathbb{R}^2 : a^2 + b^2 \le 1\rbrace$ fails $(\ast)$ at $(1,0)$ because $S_\varepsilon(1,0) \not\subseteq V$ for every $\varepsilon > 0$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §13.** Introduces the standard topology on $\mathbb{R}$ generated by open intervals $(a,b)$.

**Morris, *Topology Without Tears*, Chapter 2.** Definitions and proofs for the Euclidean topology on $\mathbb{R}$ and $\mathbb{R}^2$ via intervals and open discs/squares.
