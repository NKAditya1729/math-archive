---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 19
title: "Path Connectedness and Path Components"
coverage: >
  Defines paths and path-connected topological spaces, proving that every
  path-connected space is connected. Constructs explicit paths in the unit
  interval, Euclidean space, the circle, and higher-dimensional spheres via radial
  projection. Surveys the connectedness and path connectedness of matrix spaces
  including GL_n(R), M_n(R), O(n), and previews SO(n). Establishes that path
  connectivity is an equivalence relation whose equivalence classes are the path
  components of the space, using the Pasting Lemma to concatenate paths, and notes
  that path components need not be closed.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 2
depends_on:
  - lecture: 16
    title: "Connectedness of the Real Line and Intervals"
    relationship: "Supplies the theorem that [0, 1] is connected, used to prove path-connected spaces are connected."
  - lecture: 13
    title: "Dense Subsets and the Pasting Lemma"
    relationship: "Supplies the Pasting Lemma for closed sets used to prove concatenation of paths is continuous."
  - lecture: 18
    title: "Connected Components of a Topological Space"
    relationship: "Supplies the component theory framework that path components mirror and refine."
used_in:
  - lecture: 20
    title: "Path Components Need Not Be Closed: The Comb Space"
    relationship: "Examines the comb space as a connected space that is not path connected, resolving the closedness remark."
  - lecture: 21
    title: "Path Connectedness of GL_n(R)^+"
    relationship: "Proves that the space of real matrices with positive determinant is path connected."
  - lecture: 22
    title: "Path Connectedness of GL_n(C) and Special Linear Groups"
    relationship: "Proves path connectedness of complex invertible matrices and special linear groups."
notation:
  - symbol: "$\\gamma \\colon [0, 1] \\to X$"
    gloss: 'A path in $X$ from $\gamma(0)$ to $\gamma(1)$'
  - symbol: "$x \\sim y$"
    gloss: 'Path-equivalence relation: there exists a continuous path from $x$ to $y$'
  - symbol: "$H = \\gamma_1 * \\gamma_2$"
    gloss: 'Concatenation of paths $\gamma_1$ and $\gamma_2$ meeting at an intermediate point'
  - symbol: "$X_i$"
    gloss: 'A path component of $X$, an equivalence class under path-equivalence'
prev: lecture-18
next: lecture-20
---

# Lecture 19 — Path Connectedness and Path Components

In the previous lecture, we investigated the equivalence relation of connectedness and decomposed every topological space into its maximal connected subsets, the connected components. Today we introduce **path connectedness**, which provides a more geometric and intuitive notion of connectedness: two points belong to the same piece if they can be joined by a continuous curve. We prove that path connectedness is strictly stronger than connectedness, survey classical geometric spaces and matrix Lie groups, and establish the path-component equivalence relation via the Pasting Lemma.

---

## Paths and path connectedness

We begin with the formal topological formulation of a curve connecting two points.

### Definition 19.1 (Path and path-connected space) {#definition-19-1-path-and-path-connected-space}

{% capture def191_content %}
Let $X$ be a topological space.
1. A **path** in $X$ from a point $x \in X$ to a point $y \in X$ is a continuous map:
   $$\gamma \colon [0, 1] \longrightarrow X$$
   such that $\gamma(0) = x$ and $\gamma(1) = y$. We say that $\gamma$ **joins** or **connects** $x$ to $y$.
2. The space $X$ is said to be **path connected** if for every pair of points $x, y \in X$, there exists a path in $X$ from $x$ to $y$.
{% endcapture %}
{% include block.html type="definition" title="Definition 19.1 (Path and Path-Connected Space)" content=def191_content %}

{% include figure.html
   src="point-set-topology/lecture-19/path-connected-space-gamma.svg"
   num="19.1"
   caption="A path-connected topological space $X$ containing points $x$ and $y$ joined by a continuous path $\gamma \colon [0, 1] \to X$."
   alt="An organic region X with two points x and y connected by a continuous curve gamma." %}

---

## Path connectedness implies connectedness

Our first major result shows that path connectedness is a stronger condition than topological connectedness.

### Proposition 19.2 (Path-connected implies connected) {#proposition-19-2-path-connected-implies-connected}

{% capture prop192_content %}
Let $X$ be a topological space. If $X$ is path connected, then $X$ is connected.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 19.2 (Path Connected $\implies$ Connected)" content=prop192_content %}

{% capture prop192_proof %}
We need to show that if $X$ is path connected, then $X$ is connected.

Let us proceed by contradiction. So let us assume that $X$ is path connected, but not connected.

Then, since $X$ is not connected, we can write $X$ as a disjoint union:
$$X = U \sqcup V,$$
where $U$ and $V$ are non-empty open subsets of $X$.

Since $U$ and $V$ are non-empty, let $x$ be a point in $U$ and let $y$ be a point in $V$.

Because $X$ is assumed to be path connected, there exists a continuous map:
$$\gamma \colon [0, 1] \longrightarrow X$$
such that $\gamma(0) = x$ and $\gamma(1) = y$.

Now we consider the inverse images of $U$ and $V$ under $\gamma$. We can write the unit interval $[0, 1]$ as:
$$[0, 1] = \gamma^{-1}(X) = \gamma^{-1}(U \sqcup V) = \gamma^{-1}(U) \sqcup \gamma^{-1}(V).$$
Let us check the properties of these two subsets:
1. **Disjointness:** Since $U$ and $V$ are disjoint ($U \cap V = \varnothing$), their inverse images are also disjoint:
   $$\gamma^{-1}(U) \cap \gamma^{-1}(V) = \gamma^{-1}(U \cap V) = \gamma^{-1}(\varnothing) = \varnothing.$$
2. **Non-emptiness:** The point $0 \in [0, 1]$ belongs to $\gamma^{-1}(U)$ because $\gamma(0) = x \in U$. Similarly, the point $1 \in [0, 1]$ belongs to $\gamma^{-1}(V)$ because $\gamma(1) = y \in V$. Thus both $\gamma^{-1}(U)$ and $\gamma^{-1}(V)$ are non-empty.
3. **Openness:** Because $\gamma \colon [0, 1] \to X$ is continuous and $U, V$ are open subsets of $X$, the preimages $\gamma^{-1}(U)$ and $\gamma^{-1}(V)$ are open subsets of $[0, 1]$.

So thus we have written $[0, 1]$ as a disjoint union of two non-empty open subsets.
This contradicts the fact that $[0, 1]$ is connected ([Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#proposition-16-1-connectedness-unit-interval)).

Therefore, our assumption that $X$ is not connected must be false.
So a path-connected space is connected.
So this completes the proof. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 19.2" content=prop192_proof %}

---

## Examples of path-connected spaces

We now verify path connectedness for standard geometric spaces.

### Example 1 (Straight-line paths in $\mathbb{R}^n$ and intervals) {#example-1-straight-line-paths-in-rn}

{% capture ex1_content %}
1. **The unit interval $[0, 1]$:** For any two points $a, b \in [0, 1]$, we can connect them by a straight-line path:
   $$\gamma \colon [0, 1] \longrightarrow [0, 1], \qquad \gamma(t) = (1 - t)a + tb.$$
   The map $\gamma$ is a polynomial in $t$, hence continuous. At the endpoints, $\gamma(0) = a$ and $\gamma(1) = b$. Because $[0, 1]$ is convex, $(1-t)a + tb \in [0, 1]$ for all $t \in [0, 1]$. Thus $[0, 1]$ is path connected.
2. **Euclidean space $\mathbb{R}$ and $\mathbb{R}^n$:** Given any two vectors $a, b \in \mathbb{R}^n$, the straight-line segment map:
   $$\gamma \colon [0, 1] \longrightarrow \mathbb{R}^n, \qquad \gamma(t) = (1 - t)a + tb$$
   is continuous because each coordinate function $\gamma_i(t) = (1-t)a_i + tb_i$ is a continuous polynomial. Since $\gamma(0) = a$ and $\gamma(1) = b$, every pair of points can be joined by a path. Therefore $\mathbb{R}^n$ is path connected.
{% endcapture %}
{% include block.html type="example" title="Example 1 (Straight-Line Paths in $\mathbb{R}^n$ and Convex Sets)" content=ex1_content %}

### Example 2 (The circle $S^1$) {#example-2-circle-s1}

{% capture ex2_content %}
Consider the unit circle in the complex plane:
$$S^1 = \lbrace z \in \mathbb{C} : |z| = 1 \rbrace = \lbrace e^{i\theta} : \theta \in \mathbb{R} \rbrace.$$
Given any two points $a, b \in S^1$, write them in polar coordinates as $a = e^{i\theta_1}$ and $b = e^{i\theta_2}$ for some $\theta_1, \theta_2 \in \mathbb{R}$. We define the path:
$$\gamma \colon [0, 1] \longrightarrow S^1, \qquad \gamma(t) = e^{i((1-t)\theta_1 + t\theta_2)}.$$
We check continuity by viewing $\gamma$ as the composition of two continuous maps:
1. The linear angle map $t \mapsto (1-t)\theta_1 + t\theta_2$ from $[0, 1]$ to $\mathbb{R}$, which is continuous.
2. The exponential map $\theta \mapsto e^{i\theta} = (\cos\theta, \sin\theta)$ from $\mathbb{R}$ to $S^1 \subseteq \mathbb{C}$, which is continuous because its real and imaginary components are standard trigonometric functions.

Since the composition of continuous maps is continuous, $\gamma$ is continuous. Moreover, $\gamma(0) = e^{i\theta_1} = a$ and $\gamma(1) = e^{i\theta_2} = b$. Thus $S^1$ is path connected.
{% endcapture %}
{% include block.html type="example" title="Example 2 (The Circle $S^1$)" content=ex2_content %}

### Example 3 (Spheres $S^n$) {#example-3-spheres-sn}

{% capture ex3_content %}
We now consider the $n$-dimensional unit sphere:
$$S^n = \left\lbrace x \in \mathbb{R}^{n+1} : \sum_{i=1}^{n+1} x_i^2 = 1 \right\rbrace.$$
Let us illustrate the construction for $S^2$. Let $N = (0, 0, 1)$ denote the north pole and $S = (0, 0, -1)$ denote the south pole.

**Case 1: Connecting the north pole to any point $p \ne S$.**
Let $p \in S^2$ with $p \ne S$. Consider the straight-line chord in $\mathbb{R}^3$:
$$\gamma_1(t) = (1 - t)N + tp, \qquad t \in [0, 1].$$
Since $p \ne -N$, the origin $0 \in \mathbb{R}^3$ does not lie on the line segment connecting $N$ and $p$. Therefore $\lVert \gamma_1(t) \rVert_2 > 0$ for all $t \in [0, 1]$.
We project this chord radially outward onto the sphere by defining:
$$\gamma(t) = \frac{\gamma_1(t)}{\lVert \gamma_1(t) \rVert_2}, \qquad t \in [0, 1].$$
Each coordinate function of $\gamma(t)$ is the quotient of a polynomial by the non-vanishing continuous norm function $\lVert \gamma_1(t) \rVert_2$. Hence $\gamma \colon [0, 1] \to S^2$ is continuous. Furthermore:
$$\gamma(0) = \frac{N}{\lVert N \rVert_2} = N, \qquad \gamma(1) = \frac{p}{\lVert p \rVert_2} = p.$$
Thus $N$ can be connected to any point $p \ne S$ by a path lying entirely on $S^2$.

**Case 2: Connecting the north pole to the south pole.**
To connect $N$ to $S$, choose any intermediate point on the equator, say $p = (1, 0, 0) \in S^2$.
By Case 1, we have a continuous path joining $N$ to $p$. By exactly the same construction (interchanging the roles of $N$ and $S$), we obtain a continuous path joining $S$ to $p$. Reversing this second path gives a path from $p$ to $S$. Concatenating the two paths yields a continuous path on $S^2$ from $N$ to $S$.

Consequently, any two points on $S^2$ (and by the identical coordinate argument, on $S^n$ for all $n \ge 1$) can be joined by a path, so $S^n$ is path connected.
{% endcapture %}
{% include block.html type="example" title="Example 3 (Spheres $S^n$ via Radial Projection)" content=ex3_content %}

{% include figure.html
   src="point-set-topology/lecture-19/sphere-path-projection.svg"
   num="19.2"
   caption="Constructing a path on $S^2$ from $N$ to $p \ne S$: the straight chord $(1-t)N + tp$ misses the origin and is projected radially onto the sphere surface."
   alt="The unit sphere showing the north pole N, point p, the chord between them, and the projected arc on the sphere surface." %}

---

## Survey of matrix spaces and topological groups

We now examine several matrix spaces introduced earlier in the course and determine their connectedness and path connectedness.

### Example 4 (Connectedness and path connectedness of matrix spaces) {#example-4-matrix-groups-gln-and-on}

{% capture ex4_content %}
1. **The general linear group $GL_n(\mathbb{R})$:**
   The determinant map:
   $$\det \colon GL_n(\mathbb{R}) \longrightarrow \mathbb{R} \setminus \{0\}$$
   is continuous ([Lecture 11]({{ site.baseurl }}/point-set-topology/lecture-11/#example-3-gln-is-open)).
   The determinant is surjective onto $\mathbb{R} \setminus \{0\}$, because for any $\lambda \in \mathbb{R} \setminus \{0\}$, the diagonal matrix $\operatorname{diag}(\lambda, 1, \dots, 1)$ has determinant $\lambda$.
   The target $\mathbb{R} \setminus \{0\} = (-\infty, 0) \sqcup (0, \infty)$ is disconnected.
   Taking preimages:
   $$GL_n(\mathbb{R}) = \det^{-1}\bigl((-\infty, 0)\bigr) \sqcup \det^{-1}\bigl((0, \infty)\bigr).$$
   Because the determinant is continuous and surjective, both preimages are non-empty open subsets of $GL_n(\mathbb{R})$.
   Therefore $GL_n(\mathbb{R})$ is **disconnected**, and consequently cannot be path connected.

2. **The subgroup $GL_n(\mathbb{R})^+$:**
   The space of matrices with strictly positive determinant:
   $$GL_n(\mathbb{R})^+ = \det^{-1}\bigl((0, \infty)\bigr)$$
   cannot be shown to be disconnected by this determinant argument because $\det^{-1}((-\infty, 0))$ is empty. In Lecture 21, we will prove that $GL_n(\mathbb{R})^+$ is **path connected**.

3. **The full matrix space $M_n(\mathbb{R})$:**
   We have $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$ as a topological vector space. Since Euclidean space $\mathbb{R}^{n^2}$ is path connected (Example 1), $M_n(\mathbb{R})$ is **path connected**.

4. **The orthogonal group $O(n)$:**
   For any orthogonal matrix $A \in O(n)$, we have $A A^T = I$, which implies $(\det A)^2 = 1$, so $\det A \in \{-1, 1\}$.
   The determinant map $\det \colon O(n) \to \{-1, 1\}$ is continuous and surjective, since $\det(I) = 1$ and $\det(\operatorname{diag}(-1, 1, \dots, 1)) = -1$.
   Because $\{-1, 1\} = \{-1\} \sqcup \{1\}$ is a discrete two-point space, the preimages give a disconnection:
   $$O(n) = \det^{-1}(\{-1\}) \sqcup \det^{-1}(\{1\}).$$
   Thus $O(n)$ is **disconnected** (hence not path connected).

5. **The groups $SO(n)$, $U(n)$, and $SU(n)$:**
   Although $O(n)$ is disconnected, the special orthogonal group:
   $$SO(n) = \lbrace A \in O(n) : \det A = 1 \rbrace$$
   is **path connected**. Similarly, the unitary group $U(n)$ and special unitary group $SU(n)$ are path connected. We will prove these results later in the course using the quotient topology.
{% endcapture %}
{% include block.html type="example" title="Example 4 (Matrix Spaces and Topological Groups)" content=ex4_content %}

---

## The path-equivalence relation

Just as connectedness led to the partition into connected components, path connectedness defines an equivalence relation on the points of any topological space.

### Definition 19.3 (Path-equivalence relation) {#definition-19-3-path-equivalence-relation}

{% capture def193_content %}
Let $X$ be a topological space. We define a binary relation $\sim$ on the points of $X$ by declaring that for $x, y \in X$:
$$x \sim y \iff \text{there exists a continuous path } \gamma \colon [0, 1] \to X \text{ such that } \gamma(0) = x \text{ and } \gamma(1) = y.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 19.3 (Path-Equivalence Relation)" content=def193_content %}

### Proposition 19.4 (Path-equivalence is an equivalence relation) {#proposition-19-4-path-equivalence-is-an-equivalence-relation}

{% capture prop194_content %}
Let $X$ be a topological space. The relation $\sim$ defined in Definition 19.3 is an **equivalence relation** on $X$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 19.4 (Path-Equivalence is an Equivalence Relation)" content=prop194_content %}

{% capture prop194_proof %}
To check that this defines an equivalence relation on $X$, we need to check three conditions: reflexivity, symmetry, and transitivity. Let us check them one by one.

**Condition 1: Reflexivity.**
We need to check that $x \sim x$ for every $x \in X$.
To show this, we take the constant path:
$$\gamma \colon [0, 1] \longrightarrow X, \qquad \gamma(t) = x \quad \text{for all } t \in [0, 1].$$
A constant map into any topological space is continuous.
Since $\gamma(0) = x$ and $\gamma(1) = x$, this path joins $x$ to $x$.
Therefore $x \sim x$, so reflexivity holds.

**Condition 2: Symmetry.**
We need to check that if $x \sim y$, then $y \sim x$.
Suppose $x \sim y$. Then there exists a continuous path $\gamma \colon [0, 1] \to X$ such that $\gamma(0) = x$ and $\gamma(1) = y$.
We define the reverse path:
$$\gamma_1 \colon [0, 1] \longrightarrow X, \qquad \gamma_1(t) = \gamma(1 - t).$$
Notice that $\gamma_1$ is the composition of the map $t \mapsto 1 - t$ from $[0, 1]$ to $[0, 1]$ (which is continuous) with $\gamma$ (which is continuous). Therefore $\gamma_1$ is continuous.
Evaluating at the endpoints:
$$\gamma_1(0) = \gamma(1) = y, \qquad \gamma_1(1) = \gamma(0) = x.$$
Thus $\gamma_1$ is a continuous path from $y$ to $x$.
Notice that $\gamma_1$ traces the exact same curve as $\gamma$ in the opposite direction, having the identical image $\gamma_1([0, 1]) = \gamma([0, 1])$.
Therefore $y \sim x$, so symmetry is satisfied.

**Condition 3: Transitivity.**
We need to check that if $x \sim y$ and $y \sim z$, then $x \sim z$.
Here we will use the Pasting Lemma ([Lecture 13]({{ site.baseurl }}/point-set-topology/lecture-13/#theorem-13-7-the-pasting-lemma)), which tells us how to check continuity of a map by restricting it to two closed subsets that cover the domain.

Since $x \sim y$, there is a continuous path $\gamma_1 \colon [0, 1] \to X$ with $\gamma_1(0) = x$ and $\gamma_1(1) = y$.
Since $y \sim z$, there is a continuous path $\gamma_2 \colon [0, 1] \to X$ with $\gamma_2(0) = y$ and $\gamma_2(1) = z$.

Let $A = [0, 1/2]$ and $B = [1/2, 1]$. These are both closed subsets of $[0, 1]$, and their union is $A \cup B = [0, 1]$.
We define two helper maps:
- On $A = [0, 1/2]$, define $H_1 \colon [0, 1/2] \to X$ by:
  $$H_1(t) = \gamma_1(2t).$$
  This is continuous because it is the composition of the continuous linear map $t \mapsto 2t$ from $[0, 1/2]$ to $[0, 1]$ with $\gamma_1$.
- On $B = [1/2, 1]$, define $H_2 \colon [1/2, 1] \to X$ by:
  $$H_2(t) = \gamma_2(2t - 1).$$
  This is continuous because it is the composition of the continuous linear map $t \mapsto 2t - 1$ from $[1/2, 1]$ to $[0, 1]$ with $\gamma_2$.

Now we check that $H_1$ and $H_2$ agree on the overlap $A \cap B = \{1/2\}$:
$$H_1(1/2) = \gamma_1(2 \cdot (1/2)) = \gamma_1(1) = y,$$
$$H_2(1/2) = \gamma_2(2 \cdot (1/2) - 1) = \gamma_2(0) = y.$$
So $H_1(1/2) = H_2(1/2) = y$.

By the Pasting Lemma, because $A$ and $B$ are closed subsets of $[0, 1]$ whose union is $[0, 1]$ and $H_1, H_2$ agree on $A \cap B$, the combined function:
$$H \colon [0, 1] \longrightarrow X, \qquad H(t) = \begin{cases} H_1(t) = \gamma_1(2t), & t \in [0, 1/2], \\ H_2(t) = \gamma_2(2t - 1), & t \in [1/2, 1] \end{cases}$$
is continuous.

Finally, we evaluate $H$ at the endpoints:
$$H(0) = H_1(0) = \gamma_1(0) = x,$$
$$H(1) = H_2(1) = \gamma_2(1) = z.$$
Thus $H$ is a continuous path from $x$ to $z$.
So this shows that $x \sim z$.
Therefore, transitivity is satisfied.

Since reflexivity, symmetry, and transitivity all hold, $\sim$ is an equivalence relation on $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 19.4" content=prop194_proof %}

{% capture corr19_slips %}
**Correction notes (two verbal slips in transitivity):**
1. **Transitivity hypothesis:** The transcript states: *"And the third thing we need to check is if $x$ is equivalent to $y$ and $y$ is equivalent to $x$, then $x$ is equivalent to $z$, right?"* The second hypothesis was spoken as $y \sim x$ instead of $y \sim z$. The proof that immediately follows defines $\gamma_2$ with $\gamma_2(0) = y$ and $\gamma_2(1) = z$, confirming $y \sim z$ was intended.
2. **Transitivity conclusion:** After verifying that $H$ joins $x$ to $z$, the transcript reads: *"So this shows that $x$ is equal to $z$."* Plainly, $x$ and $z$ need not be equal as points; what has been proved is that $x$ is *equivalent* to $z$ under the path relation ($x \sim z$).
{% endcapture %}
{% include block.html type="correction" title="Correction Note: Slips in Proposition 19.4 Transitivity Statement" content=corr19_slips %}

{% include figure.html
   src="point-set-topology/lecture-19/path-concatenation.svg"
   num="19.3"
   caption="Concatenation $H = \gamma_1 * \gamma_2$: path $\gamma_1$ traverses from $x$ to $y$ during $t \in [0, 1/2]$, and path $\gamma_2$ traverses from $y$ to $z$ during $t \in [1/2, 1]$."
   alt="A diagram showing two continuous paths in X meeting at point y, forming a single continuous path H from x to z." %}

---

## Path components

Since $\sim$ is an equivalence relation, it partitions any space $X$ into disjoint equivalence classes.

### Definition 19.5 (Path components) {#definition-19-5-path-components}

{% capture def195_content %}
Let $X$ be a topological space. The equivalence classes of $X$ under the path-equivalence relation $\sim$ are called the **path components** of $X$.
{% endcapture %}
{% include block.html type="definition" title="Definition 19.5 (Path Components)" content=def195_content %}

### Proposition 19.6 (Properties of path components) {#proposition-19-6-properties-of-path-components}

{% capture prop196_content %}
Let $X$ be a topological space, and let $\{X_i\}_{i \in I}$ be the collection of path components of $X$. Then:
1. The space $X$ is the disjoint union of its path components:
   $$X = \bigsqcup_{i \in I} X_i.$$
2. Every non-empty path-connected subspace $P \subseteq X$ is contained in a unique path component $X_i$.
3. Each path component $X_i$ is itself a path-connected subspace of $X$.
Consequently, the path components $X_i$ are the **maximal path-connected subspaces** of $X$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 19.6 (Properties of Path Components)" content=prop196_content %}

{% capture prop196_proof %}
Let us verify these properties:
1. **Partition into components:** Because $\sim$ is an equivalence relation on $X$ (Proposition 19.4), the equivalence classes $\{X_i\}_{i \in I}$ partition the set $X$. Hence $X = \bigsqcup_{i \in I} X_i$.
2. **Containment of path-connected subspaces:** Let $P \subseteq X$ be a non-empty path-connected subspace. Choose any point $p_0 \in P$. For every point $p \in P$, since $P$ is path connected, there is a path in $P \subseteq X$ from $p_0$ to $p$. Therefore $p \sim p_0$ for all $p \in P$. This means that all points of $P$ lie in the equivalence class $[p_0]$, so $P \subseteq X_i$ where $X_i = [p_0]$. Since the equivalence classes are mutually disjoint, this component $X_i$ is unique.
3. **Path-connectedness of components:** Let $X_i$ be a path component, and let $x, y \in X_i$. Since $X_i$ is an equivalence class under $\sim$, we have $x \sim y$, which means there is a continuous path $\gamma \colon [0, 1] \to X$ from $x$ to $y$. For every $t \in [0, 1]$, the restricted path $s \mapsto \gamma(st)$ provides a path in $X$ from $x = \gamma(0)$ to $\gamma(t)$, so $\gamma(t) \sim x$, meaning $\gamma(t) \in X_i$. Thus the image $\gamma([0, 1])$ is entirely contained in $X_i$. Hence $X_i$ is path connected as a subspace.

Properties (2) and (3) together prove that each $X_i$ is a maximal path-connected subspace of $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 19.6" content=prop196_proof %}

---

### Remark 19.7 (Path components need not be closed) {#remark-19-7-path-components-need-not-be-closed}

{% capture rmk197_content %}
Recall from [Lecture 18]({{ site.baseurl }}/point-set-topology/lecture-18/#proposition-18-4-properties-connected-components) that every connected component of a topological space is **closed**.

In striking contrast, **path components need not be closed** in $X$. In the next lecture ([Lecture 20]({{ site.baseurl }}/point-set-topology/lecture-20/)), we will construct the classic **comb space** counterexample: a connected space having two path components, one of which is not closed, demonstrating that path connectedness differs fundamentally from topological connectedness.
{% endcapture %}
{% include block.html type="remark" title="Remark 19.7 (Path Components Need Not Be Closed)" content=rmk197_content %}

---

## Supplements

### Supplement 1: Continuity of the radial projection path in $S^n$

{% capture supp_sn_proj %}
In Example 3, we showed that for $p \ne -N$ on $S^n$, the straight chord:
$$\gamma_1(t) = (1 - t)N + tp$$
does not pass through the origin. Let us verify this explicitly.

Suppose there exists $t \in [0, 1]$ such that $\gamma_1(t) = 0$.
Then $(1 - t)N = -tp$.
Taking Euclidean norms on both sides, since $\lVert N \rVert_2 = \lVert p \rVert_2 = 1$:
$$|1 - t| = |-t| \implies 1 - t = t \implies t = \frac{1}{2}.$$
Substituting $t = 1/2$ back into the equation:
$$\frac{1}{2}N = -\frac{1}{2}p \implies p = -N.$$
Thus $\gamma_1(t) = 0$ can only occur if $p = -N$ (the antipodal point, which in $S^2$ is the south pole $S$).
When $p \ne -N$, the norm $\lVert \gamma_1(t) \rVert_2 > 0$ for all $t \in [0, 1]$. Since the Euclidean norm $\lVert \cdot \rVert_2 \colon \mathbb{R}^{n+1} \to [0, \infty)$ is continuous and never vanishes on the compact segment $\gamma_1([0, 1])$, the quotient map $\gamma(t) = \gamma_1(t) / \lVert \gamma_1(t) \rVert_2$ is continuous on $[0, 1]$.
{% endcapture %}
{% include block.html type="supplement" title="Supplement 1: Non-Vanishing Norm for Spherical Chords" content=supp_sn_proj %}

---

## At a glance

- [Definition 19.1 (Path and Path-Connected Space)](#definition-19-1-path-and-path-connected-space): Continuous $\gamma \colon [0, 1] \to X$ connecting $\gamma(0) = x$ to $\gamma(1) = y$.
- [Proposition 19.2 (Path Connected $\implies$ Connected)](#proposition-19-2-path-connected-implies-connected): Disconnecting $X = U \sqcup V$ would pull back to a disconnection of $[0, 1]$.
- [Example 1 (Straight-Line Paths in $\mathbb{R}^n$)](#example-1-straight-line-paths-in-rn): Straight lines $(1-t)a + tb$ connect points in $[0, 1]$ and $\mathbb{R}^n$.
- [Example 2 (The Circle $S^1$)](#example-2-circle-s1): Exponential angle map $t \mapsto e^{i((1-t)\theta_1 + t\theta_2)}$.
- [Example 3 (Spheres $S^n$)](#example-3-spheres-sn): Radial projection of chord from north pole, concatenated to south pole.
- [Example 4 (Matrix Spaces)](#example-4-matrix-groups-gln-and-on): $GL_n(\mathbb{R})$ and $O(n)$ disconnected via determinant; $GL_n(\mathbb{R})^+$ and $M_n(\mathbb{R})$ path connected.
- [Definition 19.3 (Path-Equivalence Relation)](#definition-19-3-path-equivalence-relation): $x \sim y \iff$ there is a path from $x$ to $y$.
- [Proposition 19.4 (Path-Equivalence is an Equivalence Relation)](#proposition-19-4-path-equivalence-is-an-equivalence-relation): Reflexive (constant path), symmetric (reverse path), transitive (concatenation via the Pasting Lemma).
- [Definition 19.5 (Path Components)](#definition-19-5-path-components): Equivalence classes under $\sim$.
- [Proposition 19.6 (Properties of Path Components)](#proposition-19-6-properties-of-path-components): Partition into maximal path-connected subspaces.
- [Remark 19.7 (Path Components Need Not Be Closed)](#remark-19-7-path-components-need-not-be-closed): Contrast with connected components; preview of the comb space in Lecture 20.

---

## Where we are

We have established the definition of path connectedness, shown that it implies topological connectedness, and constructed the path-component decomposition $X = \bigsqcup X_i$. In the next lecture ([Lecture 20]({{ site.baseurl }}/point-set-topology/lecture-20/)), we will investigate the topologist's sine curve and the comb space, demonstrating that the converse to Proposition 19.2 is false: a connected space need not be path connected, and its path components need not be closed.

---

## Further reading

- **Munkres, *Topology* (2nd ed.)**, §24: *Connected Subspaces of the Real Line* (covers path connectedness, path components, and counterexamples).
- **Morris, *Topology Without Tears***, Chapter 5: *Connectedness* (treats path connectedness and concatenation of paths).
