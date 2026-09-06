---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 20
title: "Path Components Need Not Be Closed: The Comb Space"
coverage: >
  Completes the proof that path components are maximal path-connected subspaces.
  Defines the punctured comb space in the plane and proves that any path starting
  at the top of the limiting vertical spine is trapped within that spine,
  utilizing the supremum argument and local disconnections. Concludes that the comb
  space is connected but not path connected, possessing two path components (one of
  which is not closed) and exactly one connected component, and corrects a
  consequential slip identifying the projection cutting out the vertical spine.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 2
corrections: 1
depends_on:
  - lecture: 19
    title: "Path Connectedness and Path Components"
    relationship: "Supplies the definition of path connectedness, path components, and the theorem being proved."
  - lecture: 15
    title: "Sequential Criteria for Closed Sets and Continuity, and Introduction to Connectedness"
    relationship: "Supplies the theorem that the closure of a connected subset is connected."
  - lecture: 16
    title: "Connectedness of the Real Line and Intervals"
    relationship: "Supplies connectedness of intervals used in the contradiction step of the comb space."
used_in:
  - lecture: 21
    title: "Path Connectedness of GL_n(R)^+"
    relationship: "Contrasts the failure of path connectedness in comb-like spaces with matrix group connectivity."
notation:
  - symbol: "$C$"
    gloss: 'The comb space in $\mathbb{R}^2$ with deleted origin'
  - symbol: "$Y$"
    gloss: 'The vertical spine $\{0\} \times (0, 1]$ of the comb space'
  - symbol: "$P = (0, 1)$"
    gloss: 'The top point of the limiting spine $Y$'
  - symbol: '$S = \{x \in [0, 1] : \gamma([0, x]) \subseteq Y\}$'
    gloss: 'Set of parameters whose path trajectory remains inside $Y$'
prev: lecture-19
next: lecture-21
---

# Lecture 20 — Path Components Need Not Be Closed: The Comb Space

In the previous lecture, we introduced path connectedness and formulated the path-component decomposition $X = \bigsqcup X_i$. We closed that lecture by observing that while connected components are always closed subsets of the ambient space, path components need not be closed. Today we complete the formal proof that path components are maximal path-connected subspaces, and then examine the classic counterexample: the **punctured comb space** $C \subseteq \mathbb{R}^2$. We prove that $C$ is connected but not path connected, possessing two path components—one of which is not closed—and exactly one connected component.

---

## Maximal path-connected subspaces

We open by proving the proposition stated at the close of Lecture 19 ([Lecture 19]({{ site.baseurl }}/point-set-topology/lecture-19/#proposition-19-6-properties-of-path-components)).

### Proposition 20.1 (Maximality of path components) {#proposition-20-1-maximality-of-path-components}

{% capture prop201_content %}
Let $X$ be a topological space, and let $\{X_i\}_{i \in I}$ be the collection of path components of $X$. Then:
1. Every path-connected subspace $T \subseteq X$ is contained in some path component $X_i$.
2. Each path component $X_i$ is a path-connected subspace of $X$.
Consequently, the path components $X_i$ are the **maximal path-connected subspaces** of $X$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 20.1 (Maximality of Path Components)" content=prop201_content %}

{% capture prop201_proof %}
Let us prove these two assertions:

**Proof of Part 1:**
First, we want to show that every path-connected subspace $T$ of $X$ is contained in some $X_i$.
So let $T$ be a path-connected subspace of $X$, and let $x \in T$.
Since the path components partition $X$, $x$ belongs to $X_i$ for some index $i \in I$.
Now we claim that $T \subseteq X_i$.
To show that $T$ is contained in $X_i$, it suffices to show that for any point $t \in T$, there is a path in $X$ joining $x$ and $t$.
As $T$ is path connected, there exists a continuous path:
$$\gamma \colon [0, 1] \longrightarrow T$$
such that $\gamma(0) = x$ and $\gamma(1) = t$.
Composing $\gamma$ with the inclusion map $\iota \colon T \hookrightarrow X$ (which is continuous by the definition of the subspace topology) yields a continuous path $\iota \circ \gamma \colon [0, 1] \to X$ from $x$ to $t$.
This implies that $t \sim x$, so $t$ and $x$ belong to the same path component $X_i$.
Therefore $T \subseteq X_i$.
So this proves Part 1: every path-connected subspace of $X$ is contained in some $X_i$.

**Proof of Part 2:**
To prove Part 2, let $x, y \in X_i$.
We need to show that any two points in $X_i$ can be joined by a path lying entirely in $X_i$.
By definition of the path-component equivalence relation, since $x, y \in X_i$, there exists a continuous path $\gamma \colon [0, 1] \to X$ with $\gamma(0) = x$ and $\gamma(1) = y$.
The image $\gamma([0, 1])$ is a path-connected subspace of $X$ containing $x$. By Part 1, $\gamma([0, 1])$ is contained in $X_i$.
Thus $\gamma$ provides a path in $X_i$ joining $x$ and $y$.
Therefore $X_i$ is path connected.

Both these points together prove that each $X_i$ is a maximal path-connected subspace of $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 20.1" content=prop201_proof %}

---

## The comb space

Recall from [Lecture 18]({{ site.baseurl }}/point-set-topology/lecture-18/#proposition-18-4-properties-connected-components) that every connected component is closed. That is not true of path components. We now construct a counterexample: a space that is connected, but not path connected.

### Definition 20.2 (The punctured comb space) {#definition-20-2-comb-space}

{% capture def202_content %}
The **punctured comb space** $C \subseteq \mathbb{R}^2$, equipped with the subspace topology from Euclidean space $\mathbb{R}^2$, is defined as the union of three pieces:
$$C = \left( \bigcup_{n=1}^\infty \left\{ \frac{1}{n} \right\} \times [0, 1] \right) \cup \left( \{0\} \times (0, 1] \right) \cup \left( (0, 1] \times \{0\} \right).$$
Specifically:
1. The **teeth**: vertical line segments at $x = 1/n$ of height $1$, for all $n \in \mathbb{N}$:
   $$\bigcup_{n=1}^\infty \left\{ \frac{1}{n} \right\} \times [0, 1].$$
2. The **spine** $Y$: the vertical segment on the $y$-axis with the origin removed:
   $$Y = \{0\} \times (0, 1].$$
   In particular, $P = (0, 1)$ is the top point of $Y$.
3. The **base**: the horizontal segment on the $x$-axis with the origin removed:
   $$(0, 1] \times \{0\}.$$

Notice that the origin $(0, 0)$ is explicitly deleted from $C$.
{% endcapture %}
{% include block.html type="definition" title="Definition 20.2 (The Punctured Comb Space $C$)" content=def202_content %}

{% include figure.html
   src="point-set-topology/lecture-20/comb-space.svg"
   num="20.1"
   caption="The punctured comb space $C \subseteq \mathbb{R}^2$: the vertical teeth at $x = 1/n$, the base $(0, 1] \times \{0\}$, and the limiting spine $Y = \{0\} \times (0, 1]$ with top point $P = (0, 1)$. The origin $(0, 0)$ is removed."
   alt="The comb space showing vertical teeth at 1/n, a horizontal base, a vertical spine Y, and the origin deleted." %}

---

## Paths from $P$ are trapped in the spine

We now prove the central geometric property of the comb space: any path starting on the spine $Y$ can never leave $Y$.

### Theorem 20.3 (Paths from $P$ cannot leave $Y$) {#theorem-20-3-paths-from-p-trapped}

{% capture thm203_content %}
Let $C$ be the punctured comb space, and let $P = (0, 1) \in Y$.
If $\gamma \colon [0, 1] \to C$ is any continuous path such that $\gamma(0) = P$, then the image of $\gamma$ is completely contained inside $Y$:
$$\gamma([0, 1]) \subseteq Y.$$
{% endcapture %}
{% include block.html type="theorem" title="Theorem 20.3 (Paths Starting at $P$ are Trapped in $Y$)" content=thm203_content %}

{% capture thm203_proof %}
The starting point of $\gamma$ is $P = (0, 1) \in Y$. The claim is that if we take any continuous map $\gamma \colon [0, 1] \to C$ starting at $P$, then it cannot go outside the subspace $Y$.

Let us prove this claim. Let us assume this is not true, and that the image of $\gamma$ moves out of $Y$.

**Step 1: $Y$ is a closed subspace of $C$.**
Notice that $Y$ is a closed subspace of $C$.
To see this, consider the first coordinate projection map $p_1 \colon \mathbb{R}^2 \to \mathbb{R}$ given by $p_1(x, y) = x$.
The projection $p_1$ is continuous ([Lecture 7]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-4-continuity-of-coordinate-projections)), and the inclusion $\iota \colon C \hookrightarrow \mathbb{R}^2$ is continuous because $C$ carries the subspace topology.
Therefore the restriction $p_1|_C = p_1 \circ \iota \colon C \to \mathbb{R}$ is continuous.
Notice that the points in $C$ with $x$-coordinate equal to $0$ are precisely the points of $Y$, since the base $(0, 1] \times \{0\}$ and the teeth $\{1/n\} \times [0, 1]$ all have strictly positive $x$-coordinates.
Therefore:
$$Y = (p_1|_C)^{-1}(\{0\}).$$
Since $\{0\}$ is a closed subset of $\mathbb{R}$ and $p_1|_C$ is continuous, $Y$ is a closed subspace of $C$.

**Step 2: The parameter set $S$ and its supremum $t_0$.**
Now we define the set:
$$S = \lbrace x \in [0, 1] : \gamma([0, x]) \subseteq Y \rbrace.$$
Notice that $S \subseteq [0, 1]$ is non-empty because $0 \in S$, since $\gamma([0, 0]) = \{\gamma(0)\} = \{P\} \subseteq Y$.
Since $S$ is non-empty and bounded above by $1$, let:
$$t_0 = \sup S \in [0, 1].$$

**Step 3: $\gamma(t_0)$ belongs to $Y$.**
We claim that $\gamma(t_0) \in Y$.
Because $t_0 = \sup S$, there exists a sequence $\{t_n\}_{n=1}^\infty$ in $S$ such that $t_n \to t_0$.
As $\gamma$ is continuous, this implies $\gamma(t_n) \to \gamma(t_0)$.
Since $t_n \in S$, we have $\gamma([0, t_n]) \subseteq Y$, so in particular $\gamma(t_n) \in Y$ for all $n$.
Because $Y$ is closed in $C$ (Step 1), every convergent sequence in $Y$ has its limit in $Y$ ([Lecture 15]({{ site.baseurl }}/point-set-topology/lecture-15/#lemma-15-1-sequential-criterion-closed-subsets)).
Therefore $\gamma(t_0) \in Y$.

If $t_0 = 1$, then $\gamma([0, 1]) \subseteq Y$, and we are done.

**Step 4: The contradiction if $t_0 < 1$.**
So let us assume that $t_0 < 1$.
Since $\gamma(t_0) \in Y$, the point $\gamma(t_0)$ has coordinates $(0, y_0)$ with $y_0 \in (0, 1]$.
Because $y_0 > 0$, we can choose a small rectangular open neighborhood $U$ of $\gamma(t_0)$ in $\mathbb{R}^2$ that misses the $x$-axis entirely:
$$U = (-\varepsilon, \varepsilon) \times (y_0 - \varepsilon, y_0 + \varepsilon) \subseteq \mathbb{R}^2,$$
with $\varepsilon > 0$ chosen small enough that $y_0 - \varepsilon > 0$.
Thus $U$ does not contain the origin $(0, 0)$ and does not intersect the base $(0, 1] \times \{0\}$.

Viewing $\gamma$ as a continuous map from $[0, 1]$ into $\mathbb{R}^2$, the preimage $\gamma^{-1}(U)$ is an open subset of $[0, 1]$.
Since $t_0 \in \gamma^{-1}(U)$, $\gamma^{-1}(U)$ contains an interval $[t_0, t_0 + \varepsilon_0)$ for some $\varepsilon_0 > 0$.

Now, because $t_0 = \sup S$, for any $\delta > t_0$, the image $\gamma([0, \delta])$ cannot be completely contained in $Y$.
Therefore, we can choose a point $\delta \in (t_0, t_0 + \varepsilon_0)$ such that:
$$\gamma(\delta) \notin Y.$$
Since $\delta \in \gamma^{-1}(U)$, we have $\gamma(\delta) \in U \cap C$.
Because $\gamma(\delta) \in C \setminus Y$ and $U$ misses the base, $\gamma(\delta)$ must lie on one of the teeth:
$$\gamma(\delta) \in \left\{ \frac{1}{k} \right\} \times [0, 1]$$
for some integer $k \ge 1$.

Now restrict $\gamma$ to the closed interval $[t_0, \delta]$. The image $\gamma([t_0, \delta])$ is contained in $U \cap C$.
As $[t_0, \delta]$ is connected, its continuous image $\gamma([t_0, \delta])$ must be connected.

**Step 5: Disconnection of $U \cap C$.**
However, the subspace $U \cap C$ is disconnected.
Choose a real number $c$ strictly between $0$ and $1/k$ that is not of the form $1/n$ for any integer $n$ (for instance, an irrational number or the midpoint between two teeth).
Define two open subsets of $\mathbb{R}^2$:
$$V_1 = (-\infty, c) \times \mathbb{R}, \qquad V_2 = (c, \infty) \times \mathbb{R}.$$
Then $V_1$ and $V_2$ are disjoint open subsets of $\mathbb{R}^2$.
Intersecting with $U \cap C$, we have:
$$U \cap C = (V_1 \cap U \cap C) \sqcup (V_2 \cap U \cap C).$$
Notice that:
- $\gamma(t_0) = (0, y_0)$ has $x$-coordinate $0 < c$, so $\gamma(t_0) \in V_1 \cap U \cap C$.
- $\gamma(\delta)$ has $x$-coordinate $1/k > c$, so $\gamma(\delta) \in V_2 \cap U \cap C$.

Taking preimages under $\gamma|_{[t_0, \delta]}$, we write the interval $[t_0, \delta]$ as:
$$[t_0, \delta] = \bigl( \gamma^{-1}(V_1) \cap [t_0, \delta] \bigr) \sqcup \bigl( \gamma^{-1}(V_2) \cap [t_0, \delta] \bigr).$$
Both pieces are non-empty (containing $t_0$ and $\delta$ respectively) and open in $[t_0, \delta]$.
This writes $[t_0, \delta]$ as a disjoint union of two non-empty open subsets, which contradicts the fact that $[t_0, \delta]$ is connected ([Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#proposition-16-1-connectedness-unit-interval)).

Therefore, our assumption that $t_0 < 1$ is impossible.
Thus $t_0 = 1$, which proves that $\gamma([0, 1]) \subseteq Y$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 20.3" content=thm203_proof %}

{% capture corr20_proj %}
**Correction note (Consequential slip: projection cutting out $Y$):**
In Step 1, the transcript states:
> *"From $\mathbb{R}^2$ we have the projection to $Y$. Projection to… Okay, so this is the second projection, projection to the second coordinate, right? … and $Y$ is exactly the inverse image of zero in $C$."*

The vertical spine $Y = \{0\} \times (0, 1]$ lies on the $y$-axis, where the **first** coordinate $x$ vanishes ($x = 0$). Under the second coordinate projection $p_2(x, y) = y$, the inverse image of $\{0\}$ in $C$ is the base segment $(0, 1] \times \{0\}$, not $Y$. The vertical spine $Y$ is cut out by the **first projection** $p_1(x, y) = x$:
$$Y = (p_1|_C)^{-1}(\{0\}).$$
This is recorded in `context/known-defects.md` as a Consequential defect; the exposition above uses the first coordinate projection $p_1$.
{% endcapture %}
{% include block.html type="correction" title="Correction Note: First Coordinate Projection Cuts Out $Y$" content=corr20_proj %}

{% include figure.html
   src="point-set-topology/lecture-20/comb-disconnection-neighborhood.svg"
   num="20.2"
   caption="Disconnection of $U \cap C$: the vertical line $x = c$ separates the spine $Y$ containing $\gamma(t_0)$ from the tooth $x = 1/k$ containing $\gamma(\delta)$, disconnecting $U \cap C$ and producing a contradiction."
   alt="A zoomed-in neighborhood U showing the spine Y on the left, vertical teeth on the right, and a separating dashed line x = c between them." %}

---

## Path components and connectedness of $C$

From Theorem 20.3, the path properties of the comb space follow immediately.

### Corollary 20.4 ($C$ is not path connected) {#corollary-20-4-comb-not-path-connected}

{% capture cor204_content %}
The punctured comb space $C$ is **not path connected**.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 20.4 ($C$ is Not Path Connected)" content=cor204_content %}

{% capture cor204_proof %}
Consider the points $P = (0, 1) \in Y$ and $Q = (1, 1) \in C \setminus Y$.
If there were a continuous path $\gamma \colon [0, 1] \to C$ joining $P$ to $Q$, then $\gamma(0) = P$, so by Theorem 20.3, the entire image $\gamma([0, 1])$ must be contained in $Y$.
In particular, $\gamma(1) = Q$ would have to belong to $Y$.
However, $Q = (1, 1)$ has $x$-coordinate $1 \ne 0$, so $Q \notin Y$.
This contradiction shows that there is no continuous path in $C$ joining $(0, 1)$ to $(1, 1)$.
Therefore $C$ is not path connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 20.4" content=cor204_proof %}

### Proposition 20.5 ($C$ is connected and path components need not be closed) {#proposition-20-5-connected-components-vs-path-components}

{% capture prop205_content %}
The punctured comb space $C$ satisfies:
1. $C \setminus Y$ is path connected, hence connected.
2. The closure of $C \setminus Y$ in $C$ is all of $C$:
   $$\overline{C \setminus Y}^C = C.$$
3. $C$ is **connected**.
4. The path components of $C$ are exactly the two subsets $Y$ and $C \setminus Y$.
Consequently, $C$ has **one connected component** and **two path components**, and the path component $C \setminus Y$ is **not closed** in $C$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 20.5 (Connectedness and Path Components of the Comb Space)" content=prop205_content %}

{% capture prop205_proof %}
Let us verify each claim:

1. **Path-connectedness of $C \setminus Y$:**
   The subspace $C \setminus Y$ consists of the teeth $\{1/n\} \times [0, 1]$ and the horizontal base $(0, 1] \times \{0\}$.
   Any two points in $C \setminus Y$ can be connected by a path: from the first point, travel vertically down its tooth to the base on the $x$-axis; travel along the base $(0, 1] \times \{0\}$ (which is a connected interval missing only the origin); then travel vertically up the tooth of the second point.
   Notice that this path avoids the origin completely.
   Therefore $C \setminus Y$ is path connected, and by Proposition 19.2, $C \setminus Y$ is connected.

2. **Closure of $C \setminus Y$ in $C$:**
   Every point $(0, y) \in Y$ (where $y \in (0, 1]$) is the limit of the sequence:
   $$q_n = \left(\frac{1}{n}, y\right) \in C \setminus Y.$$
   Since $q_n \to (0, y)$ in the Euclidean metric as $n \to \infty$, every point of $Y$ belongs to the closure of $C \setminus Y$ in $C$.
   Thus $\overline{C \setminus Y}^C = (C \setminus Y) \cup Y = C$.

3. **Connectedness of $C$:**
   In [Lecture 15]({{ site.baseurl }}/point-set-topology/lecture-15/#corollary-15-5-closure-of-connected-subspace), we proved that if a subspace $A$ is connected, its closure $\overline{A}$ is also connected.
   Since $C \setminus Y$ is connected and its closure in $C$ is $C$, it follows that $C$ is connected.

4. **Path components:**
   By Theorem 20.3, no point in $Y$ can be joined by a path to any point in $C \setminus Y$.
   Furthermore, $Y = \{0\} \times (0, 1] \cong (0, 1]$ is path connected, and $C \setminus Y$ is path connected (Part 1).
   Therefore, the path components of $C$ are precisely the two pieces:
   $$\pi_0(C) = \{Y, \; C \setminus Y\}.$$

Since $C$ is connected, it has exactly **one connected component**, namely $C$ itself.
However, $C$ has **two path components**, $Y$ and $C \setminus Y$.
Finally, the path component $C \setminus Y$ is not closed in $C$, because its closure contains points of $Y$.
This proves that path components need not be closed. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 20.5" content=prop205_proof %}

---

## At a glance

- [Proposition 20.1 (Maximality of Path Components)](#proposition-20-1-maximality-of-path-components): Every path-connected subspace lies in a unique component; each component is path connected (maximal).
- [Definition 20.2 (The Punctured Comb Space)](#definition-20-2-comb-space): Comb $C \subseteq \mathbb{R}^2$ formed by teeth at $x = 1/n$, base on $x$-axis, and spine $Y$ on $y$-axis, with origin deleted.
- [Theorem 20.3 (Paths from $P$ are Trapped in $Y$)](#theorem-20-3-paths-from-p-trapped): Any path starting on $Y$ cannot escape $Y$, proved via supremum argument and local disconnection.
- [Correction Note: First Coordinate Projection](#correction-note-first-coordinate-projection-cuts-out-y): Fixes slip referring to "second projection" to cut out $Y = \{0\} \times (0, 1]$.
- [Corollary 20.4 ($C$ is Not Path Connected)](#corollary-20-4-comb-not-path-connected): No path can join $(0, 1)$ to $(1, 1)$.
- [Proposition 20.5 (Connectedness and Path Components of the Comb Space)](#proposition-20-5-connected-components-vs-path-components): $C$ is connected via closure of $C \setminus Y$; has 1 connected component and 2 path components; path component $C \setminus Y$ is not closed.

---

## Where we are

We have established that topological connectedness and path connectedness diverge: path connectedness implies connectedness, but the converse fails, as demonstrated by the comb space. In the next lecture ([Lecture 21]({{ site.baseurl }}/point-set-topology/lecture-21/)), we return to matrix groups and prove that $GL_n(\mathbb{R})^+$, the group of real matrices with positive determinant, is path connected.

---

## Further reading

- **Munkres, *Topology* (2nd ed.)**, §24: *Connected Subspaces of the Real Line* (covers the topologist's sine curve and comb spaces as classic examples distinguishing connectedness from path connectedness).
- **Morris, *Topology Without Tears***, Chapter 5: *Connectedness* (discusses spaces that are connected but not path connected).
