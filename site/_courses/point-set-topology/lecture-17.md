---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 17
title: "Connectedness of Product Spaces, the Union Lemma, and Spheres"
coverage: >
  Proves that the product of two connected topological spaces is connected using the
  slice argument, deducing that Euclidean spaces R^n are connected. Applies this to
  prove that no continuous surjection exists from [0,1] to [0,1] \sqcup [3,4],
  distinguishing them up to homeomorphism. Formulates and proves the Union Lemma
  for connected subspaces with non-empty intersection, correcting a consequential
  verbal slip in the statement. Deduces via stereographic projection charts that the
  spheres S^n (n \ge 1) are connected.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 1
depends_on:
  - lecture: 16
    title: "Connectedness of the Unit Interval and Subspaces of the Real Line"
    relationship: "Supplies connectedness of intervals and R, and the continuous image preservation theorem."
  - lecture: 15
    title: "Sequential Criteria for Closed Sets and Continuity, and Introduction to Connectedness"
    relationship: "Supplies the definition of connectedness and subspace connectedness."
  - lecture: 10
    title: "The Standard Topology on R^n, Stereographic Projection, and Homeomorphisms"
    relationship: "Supplies stereographic projection homeomorphisms between punctured spheres and R^n."
  - lecture: 5
    title: "The Comparison Lemma, Second Countability, and Product Topologies"
    relationship: "Supplies the product topology on X \times Y."
used_in:
  - lecture: 18
    title: "Connected Components and Path Connectedness"
    relationship: "Supplies the Union Lemma and product connectedness to define connected components and study path connectedness."
notation:
  - symbol: "$X \\times Y$"
    gloss: 'Product of topological spaces $X$ and $Y$ with the product topology'
  - symbol: "$\\{x_0\\} \\times Y, X \\times \\{y\\}$"
    gloss: 'Vertical and horizontal slices in $X \\times Y$, homeomorphic to $Y$ and $X$'
  - symbol: "$S^n$"
    gloss: 'The $n$-dimensional unit sphere in $\\mathbb{R}^{n+1}$'
prev: lecture-16
next: lecture-18
---

# Lecture 17 — Connectedness of Product Spaces, the Union Lemma, and Spheres

## Where we are

In [Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/), we proved that the closed unit interval $[0, 1]$, all bounded intervals $[a, b]$, and the real line $\mathbb{R}$ are connected. We classified all connected subspaces of $\mathbb{R}$ as intervals, and proved that connectedness is preserved under continuous maps.

In this lecture, we broaden our toolkit by investigating how connectedness behaves under two essential topological operations: Cartesian products and unions. First, we prove that the product $X \times Y$ of any two connected spaces is connected, using a geometric "slice" argument. By induction, this establishes that Euclidean space $\mathbb{R}^n$ is connected for all $n \ge 1$. We use connectedness as a topological invariant to prove that $[0, 1]$ is not homeomorphic to a disjoint union of intervals, resolving an open question from [Lecture 15]({{ site.baseurl }}/point-set-topology/lecture-15/). Finally, we establish the **Union Lemma**—any union of connected subspaces having non-empty intersection is connected—and use it alongside stereographic projection to prove that the $n$-spheres $S^n$ are connected for all $n \ge 1$.

---

## Connectedness of product spaces

We begin with the principal theorem of the lecture: the product of connected spaces is connected.

### Theorem 17.1 (Connectedness of product spaces) {#theorem-17-1-connectedness-of-product-spaces}

{% capture thm171_content %}
Let $X$ and $Y$ be connected topological spaces.
Then the product space $X \times Y$ equipped with the product topology is **connected**.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 17.1 (Connectedness of Product Spaces)" content=thm171_content %}

{% capture thm171_proof %}
So let us prove this. Let us assume that $X \times Y$ is not connected.
So then there are non-empty open subsets $A$ and $B$ such that this product is the disjoint union:
$$X \times Y = A \cup B, \quad \text{with } A \cap B = \varnothing.$$
In the previous lecture ([Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#proposition-16-4-continuous-image-connected), Proposition 16.4), we saw that the image of a connected topological space under a continuous map is again connected. So let us use this result.

**Step 1: Connectedness of vertical and horizontal slices.**
Fix $x_0 \in X$, and consider the map from $Y$ to $X \times Y$ given by:
$$i_{x_0} \colon Y \to X \times Y, \qquad y \mapsto (x_0, y).$$
To check that this map is continuous, we just need to check that the projections to both factors are continuous ([Lecture 9]({{ site.baseurl }}/point-set-topology/lecture-09/#proposition-9-4-product-criterion-for-continuity)):
- The projection to the first factor is just the constant map which sends everything to $x_0$, and therefore it is continuous.
- The projection to the second factor is the identity map, which is continuous.

So this map is continuous and has image equal to the subset $\{x_0\} \times Y$.
Thus $\{x_0\} \times Y$ with the subspace topology, since $Y$ is connected, is connected.

Now let us look at the intersection: we intersect the decomposition $X \times Y = A \cup B$ with $\{x_0\} \times Y$, so we get:
$$\{x_0\} \times Y = \bigl(\{x_0\} \times Y \cap A\bigr) \cup \bigl(\{x_0\} \times Y \cap B\bigr).$$
Both are open in the subspace topology on $\{x_0\} \times Y$, and they are disjoint.
So if $\{x_0\} \times Y \cap A$ is non-empty and $\{x_0\} \times Y \cap B$ is non-empty, then we get a contradiction to the connectedness of $\{x_0\} \times Y$.
Therefore, one of these has to be empty.
This implies that $\{x_0\} \times Y$ is completely contained either in $A$ or in $B$:
$$\{x_0\} \times Y \subseteq A \quad \text{or} \quad \{x_0\} \times Y \subseteq B.$$
And so similarly, arguing the same way, for every $y_0 \in Y$, the horizontal slice $X \times \{y_0\}$ is completely contained either in $A$ or in $B$:
$$X \times \{y_0\} \subseteq A \quad \text{or} \quad X \times \{y_0\} \subseteq B.$$

**Step 2: Connecting the slices to reach a contradiction.**
Now we can get a contradiction as follows: since $A$ is non-empty, let $(x_0, y_0)$ be a point in $A$.
As $\{x_0\} \times Y$ is contained in $A$ or in $B$, and it contains $(x_0, y_0) \in A$, this implies that this entire line $\{x_0\} \times Y$ is completely contained inside $A$:
$$\{x_0\} \times Y \subseteq A.$$
Now we can take any point $y \in Y$ and look at the horizontal line $X \times \{y\}$.
This line contains the point $(x_0, y)$.
As $(x_0, y) \in \{x_0\} \times Y \subseteq A$, this point is contained in $A$.
And since $X \times \{y\}$ is completely contained in $A$ or in $B$, and contains this point $(x_0, y) \in A$, this forces:
$$X \times \{y\} \subseteq A.$$
And this happens for every $y \in Y$.
So this implies that:
$$X \times Y = \bigcup_{y \in Y} \bigl(X \times \{y\}\bigr) \subseteq A.$$
But this shows that $B$ is empty, which is a contradiction.
So thus, $X \times Y$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 17.1" content=thm171_proof %}

{% include figure.html
   src="point-set-topology/lecture-17/product-connectedness-grid.svg"
   caption="Theorem 17.1: if $(x_0, y_0) \in A$, the connected vertical slice $\{x_0\} \times Y$ is forced entirely into $A$. Every horizontal slice $X \times \{y\}$ intersects this vertical slice in $(x_0, y) \in A$, forcing all horizontal slices into $A$ and leaving $B$ empty."
   alt="Grid showing product space X times Y with a point (x0, y0), the vertical slice through it, and intersecting horizontal slices." %}

### Corollary 17.2 (Connectedness of $\mathbb{R}^n$) {#corollary-17-2-connectedness-of-rn}

{% capture cor172_content %}
For every integer $n \ge 1$, Euclidean space $\mathbb{R}^n$ equipped with the standard topology is **connected**.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 17.2 (Connectedness of $\mathbb{R}^n$)" content=cor172_content %}

{% capture cor172_proof %}
We proceed by induction on $n$.
For $n = 1$, $\mathbb{R}^1 = \mathbb{R}$ is connected by Corollary 16.2 ([Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#corollary-16-2-connectedness-of-r)).
Assume that $\mathbb{R}^{n-1}$ is connected.
By Proposition 10.1 ([Lecture 10]({{ site.baseurl }}/point-set-topology/lecture-10/#proposition-10-1-equivalence-of-standard-and-product-topologies-on-rn)), the standard topology on $\mathbb{R}^n$ is homeomorphic to the product topology $\mathbb{R}^{n-1} \times \mathbb{R}$.
Since $\mathbb{R}^{n-1}$ and $\mathbb{R}$ are both connected, Theorem 17.1 implies that $\mathbb{R}^n \cong \mathbb{R}^{n-1} \times \mathbb{R}$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 17.2" content=cor172_proof %}

---

## Applications: Distinguishing spaces up to homeomorphism

We now apply connectedness to answer the topological classification question posed in Lecture 15.

### Example 1 (Non-existence of continuous surjections onto disconnected spaces) {#example-1-non-homeomorphic-intervals}

{% capture ex1_content %}
Consider the unit interval $[0, 1]$ and the disjoint union:
$$X = [0, 1] \sqcup [3, 4] \subseteq \mathbb{R}$$
equipped with the subspace topology from $\mathbb{R}$.
There is **no continuous surjective map** $f \colon [0, 1] \to [0, 1] \sqcup [3, 4]$.

Indeed, if such a map $f$ existed, then by Proposition 16.4 ([Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#proposition-16-4-continuous-image-connected)), the image $f([0, 1]) = [0, 1] \sqcup [3, 4]$ would be connected.
However, in $X$, the subsets $U = [0, 1]$ and $V = [3, 4]$ are non-empty, disjoint, and both are open in the subspace topology on $X$ (as $U = X \cap (-1, 2)$ and $V = X \cap (2, 5)$). Thus $X = U \cup V$ is disconnected, a contradiction.

Consequently:
$$[0, 1] \not\cong [0, 1] \sqcup [3, 4].$$
The two spaces cannot be homeomorphic.
{% endcapture %}
{% include block.html type="example" title="Example 1 (Connectedness as a Topological Invariant)" content=ex1_content %}

### Proposition 17.3 (Topological invariance of connectedness) {#proposition-17-3-topological-invariance-connectedness}

{% capture prop173_content %}
Let $X$ and $Y$ be homeomorphic topological spaces ($X \cong Y$).
Then $X$ is connected if and only if $Y$ is connected.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 17.3 (Topological Invariance of Connectedness)" content=prop173_content %}

{% capture prop173_proof %}
This is easy: let $f \colon X \to Y$ be a homeomorphism, so $f$ is a continuous bijection with continuous inverse $g = f^{-1} \colon Y \to X$.
Therefore the image of $f$ is all of $Y$.
If $X$ is connected, then since $f$ is continuous and $f(X) = Y$, Proposition 16.4 implies that $Y$ is connected.
And conversely, if $Y$ is connected, then since the inverse map $g \colon Y \to X$ is continuous and $g(Y) = X$, Proposition 16.4 implies that $X$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 17.3" content=prop173_proof %}

---

## The Union Lemma and connectedness of spheres

To establish the connectedness of spheres, we prove that overlapping connected sets form a connected union.

### Lemma 17.4 (The Union Lemma) {#lemma-17-4-the-union-lemma}

{% capture lem174_content %}
Let $T_1$ and $T_2$ be connected subspaces of a topological space $X$.
If their intersection is non-empty:
$$T_1 \cap T_2 \ne \varnothing,$$
then their union $T_1 \cup T_2$ (equipped with the subspace topology) is **connected**.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 17.4 (The Union Lemma)" content=lem174_content %}

{% capture lem174_proof %}
So let us prove this. Let us assume, if possible, that $T_1 \cup T_2$ is disconnected.
Let $Y = T_1 \cup T_2$. Since we are assuming that $Y$ is disconnected, we can write:
$$Y = (Y \cap U) \cup (Y \cap V)$$
where $U$ and $V$ are open subsets of $X$, and $Y \cap U, Y \cap V$ are non-empty and disjoint:
$$(Y \cap U) \cap (Y \cap V) = \varnothing.$$
So let us take a point in the intersection: let $a \in T_1 \cap T_2$, which exists because we are assuming that the intersection is non-empty.
Then $a$ is either in $Y \cap U$ or in $Y \cap V$. Assume that:
$$a \in Y \cap U \subseteq U.$$
Now let us look at $T_1$: intersecting this equality with $T_1$, we get:
$$T_1 = (T_1 \cap U) \cup (T_1 \cap V).$$
Both are open in the subspace topology on $T_1$, and they are disjoint.
As $T_1$ is connected, one of these has to be empty: that is, $T_1$ is completely contained in $U$ or $T_1$ is completely contained in $V$.
Since $T_1$ contains $a$ and $a \in U$, this implies that $T_1$ is completely contained inside $U$:
$$T_1 \subseteq U.$$
Similarly, as $a$ is also in $T_2$, and $T_2$ is also connected, repeating the same argument shows that $T_2$ is also contained in $U$:
$$T_2 \subseteq U.$$
But then this implies that:
$$Y = T_1 \cup T_2 \subseteq U.$$
So this implies that $Y \cap V$ has to be empty:
$$Y \cap V = \varnothing.$$
This is forced to be empty, which is a contradiction to the non-emptiness of $Y \cap V$.
Therefore, $Y = T_1 \cup T_2$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 17.4" content=lem174_proof %}

{% capture lem174_note %}
**Defect registered in `context/known-defects.md` (Consequential):**
In sentence 113 of the transcript, the lecturer states: *"Then the union $T_1$ union $T_2$ is non-empty."*
The conclusion must be that $T_1 \cup T_2$ is **connected**. The subsequent proof explicitly establishes connectedness, and the lecturer recalls the result correctly in Lecture 18. The correction has been applied above.
{% endcapture %}
{% include block.html type="correction" id="correction-note-union-lemma-connected" title="Correction Note: Union Lemma Conclusion is Connected" content=lem174_note %}

{% include figure.html
   src="point-set-topology/lecture-17/union-connected-subspaces.svg"
   caption="Lemma 17.4: two connected subspaces $T_1$ and $T_2$ meeting at a point $a$. If $T_1 \cup T_2$ were disconnected by $U$ and $V$, the point $a \in U$ forces both connected pieces $T_1$ and $T_2$ entirely into $U$, leaving $V$ empty."
   alt="Two overlapping connected regions T1 and T2 meeting at point a inside an open set U." %}

We now apply the Union Lemma to spheres via stereographic projection.

### Corollary 17.5 (Connectedness of spheres $S^n$) {#corollary-17-5-connectedness-of-spheres}

{% capture cor175_content %}
For every integer $n \ge 1$, the $n$-dimensional unit sphere $S^n \subseteq \mathbb{R}^{n+1}$ equipped with the subspace topology is **connected**.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 17.5 (Connectedness of Spheres $S^n$)" content=cor175_content %}

{% capture cor175_proof %}
Let $N = (0, \dots, 0, 1)$ denote the north pole and $S = (0, \dots, 0, -1)$ denote the south pole of $S^n$.
In [Lecture 10]({{ site.baseurl }}/point-set-topology/lecture-10/#stereographic-projection-of-the-punctured-sphere), we showed that stereographic projection from the north pole provides a homeomorphism:
$$\varphi_N \colon S^n \setminus \{N\} \xrightarrow{\cong} \mathbb{R}^n.$$
Similarly, stereographic projection from the south pole provides a homeomorphism:
$$\varphi_S \colon S^n \setminus \{S\} \xrightarrow{\cong} \mathbb{R}^n.$$
By Corollary 17.2, $\mathbb{R}^n$ is connected for all $n \ge 1$.
Since $S^n \setminus \{N\} \cong \mathbb{R}^n$ and $S^n \setminus \{S\} \cong \mathbb{R}^n$, Proposition 17.3 implies that both subspaces:
$$T_1 = S^n \setminus \{N\} \quad \text{and} \quad T_2 = S^n \setminus \{S\}$$
are connected.
Notice that their union covers the whole sphere:
$$T_1 \cup T_2 = \bigl(S^n \setminus \{N\}\bigr) \cup \bigl(S^n \setminus \{S\}\bigr) = S^n.$$
Moreover, for any $n \ge 1$, their intersection:
$$T_1 \cap T_2 = S^n \setminus \{N, S\}$$
is non-empty (it contains the entire equatorial sphere $S^{n-1}$, which is non-empty for $n \ge 1$).
By Lemma 17.4, the union $S^n = T_1 \cup T_2$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 17.5" content=cor175_proof %}

{% include figure.html
   src="point-set-topology/lecture-17/sphere-stereographic-connectedness.svg"
   caption="Corollary 17.5: the sphere $S^n$ is the union of two charts $S^n \setminus \{N\} \cong \mathbb{R}^n$ and $S^n \setminus \{S\} \cong \mathbb{R}^n$, each homeomorphic to $\mathbb{R}^n$ and therefore connected. Since they overlap along the equator $S^n \setminus \{N, S\}$, Lemma 17.4 proves $S^n$ is connected."
   alt="Sphere Sn showing north pole N, south pole S, and the overlapping equator between the two charts." %}

---

## At a glance

- [Theorem 17.1 (Connectedness of Product Spaces)](#theorem-17-1-connectedness-of-product-spaces): If $X$ and $Y$ are connected, then $X \times Y$ is connected, proved by showing every vertical and horizontal slice is connected and forced into a single component.
- [Corollary 17.2 (Connectedness of $\mathbb{R}^n$)](#corollary-17-2-connectedness-of-rn): $\mathbb{R}^n$ is connected for all $n \ge 1$ by induction.
- [Example 1 (Connectedness as a Topological Invariant)](#example-1-non-homeomorphic-intervals): $[0, 1] \not\cong [0, 1] \sqcup [3, 4]$ because no continuous surjection can map a connected space onto a disconnected one.
- [Proposition 17.3 (Topological Invariance of Connectedness)](#proposition-17-3-topological-invariance-connectedness): Homeomorphic spaces are simultaneously connected or disconnected.
- [Lemma 17.4 (The Union Lemma)](#lemma-17-4-the-union-lemma): If $T_1$ and $T_2$ are connected and $T_1 \cap T_2 \ne \varnothing$, then $T_1 \cup T_2$ is connected.
- [Correction Note: Union Lemma Conclusion is Connected](#correction-note-union-lemma-connected): Corrects consequential slip in transcript where the union was stated as "non-empty" rather than "connected".
- [Corollary 17.5 (Connectedness of Spheres $S^n$)](#corollary-17-5-connectedness-of-spheres): $S^n$ is covered by two stereographic charts $S^n \setminus \{N\} \cong \mathbb{R}^n$ and $S^n \setminus \{S\} \cong \mathbb{R}^n$ overlapping along $S^n \setminus \{N, S\} \ne \varnothing$, hence $S^n$ is connected for all $n \ge 1$.
