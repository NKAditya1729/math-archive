---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 7
title: "Continuous Maps, Inclusions, and Projections"
coverage: >
  Defines continuous maps between topological spaces via preimages of open sets.
  Proves that identity maps and inclusions of subspaces are continuous, and
  shows that the subspace topology is the coarsest topology making the inclusion
  continuous. Establishes that coordinate projections from product spaces are
  continuous, and proves that the product topology is the coarsest topology
  making all projections continuous. Concludes by proving that the diagonal map
  fails to be continuous under the box topology, explaining why the box topology
  is rejected.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 6
    title: "Infinite Products, the Box Topology, and Topological Examples"
    relationship: "Uses the product topology, the box topology, and the Comparison Lemma."
used_in:
  - lecture: 8
    title: "The Basis Criterion for Continuity and Continuous Operations"
    relationship: "Lecture 8 proves the basis criterion stated at the end of Lecture 7 and verifies continuity of algebraic operations on R."
notation:
  - symbol: "$f^{-1}(V)$"
    gloss: "The preimage $\\lbrace x \\in X : f(x) \\in V\\rbrace$ under a map $f : X \\to Y$"
  - symbol: "$p_j$"
    gloss: "The coordinate projection map $\\prod_{i \\in I} X_i \\to X_j$"
  - symbol: "$\\Delta$"
    gloss: "The diagonal map $x \\mapsto (x, x, \\dots)$ into a Cartesian product"
prev: lecture-06
next: lecture-08
---

# Lecture 7 — Continuous Maps, Inclusions, and Projections

## Where we are

In Part I of this course ([Lectures 1–6]({{ site.baseurl }}/point-set-topology/lecture-01/)), we developed the architecture of topological spaces: the open set axioms, bases, the generating proposition, subspace topologies, product topologies, and an extensive catalogue of spaces including spheres, matrix spaces, and matrix Lie groups.

Here begins **Part II: Continuous Maps and Metric Spaces**. Just as the structure of groups is revealed by homomorphisms, the structure of topological spaces is studied through maps that respect open sets. We define **continuous maps** between topological spaces via preimages. We show that identity maps, subspace inclusions, and Cartesian projections are continuous, and prove that both the subspace topology and the product topology are characterized as the **coarsest topologies** that make their canonical maps continuous. Finally, we establish the concrete failure of the box topology: the natural diagonal map $\Delta : \mathbb{R} \to \prod_{n=1}^\infty \mathbb{R}$ fails to be continuous under the box topology.

---

## Definition of a continuous map

In calculus, continuity of a function $f : \mathbb{R} \to \mathbb{R}$ is typically formulated using $\varepsilon$-$\delta$ estimates. In point-set topology, where neither metrics nor distances are assumed, continuity is formulated purely in terms of open sets.

{% capture def_cont_map %}
Let $(X,\tau_X)$ and $(Y,\tau_Y)$ be topological spaces, and let $f : X \to Y$ be a map of sets.

We say that $f$ is **continuous** if for every open subset $V \subseteq Y$ (that is, for every $V \in \tau_Y$), the inverse image (or preimage) $f^{-1}(V)$ is open in $X$ (that is, $f^{-1}(V) \in \tau_X$).

Recall that the preimage $f^{-1}(V)$ is the subset of all points in the domain that map into $V$:
$$f^{-1}(V) = \lbrace x \in X \;:\; f(x) \in V \rbrace \subseteq X.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 7.1 (Continuous Map)" content=def_cont_map %}

{% include figure.html
   src="point-set-topology/lecture-07/continuity-preimage.svg"
   caption="Definition of continuity: for every open set $V \in \tau_Y$, its preimage $f^{-1}(V)$ must be an open set in $\tau_X$."
   alt="Two spaces X and Y with an open set V in Y pulling back along f to an open set f^{-1}(V) in X." %}

{% capture supp_preimage_vs_forward %}
Beginners often wonder why continuity is defined in terms of *preimages* of open sets rather than *forward images*.

If we required that forward images of open sets be open (maps with this property are called **open maps**), familiar continuous functions would immediately fail. For instance:
- A constant function $f : \mathbb{R} \to \mathbb{R}$, $f(x) = c$, sends every open interval to the singleton $\lbrace c \rbrace$, which is *not* open in $\mathbb{R}$. Yet a constant function is undeniably continuous.
- The squaring function $f(x) = x^2$ maps the open interval $(-1, 1)$ to the half-open interval $[0, 1)$, which is not open in $\mathbb{R}$.

Under Definition 7.1, the preimage of any open set $V$ under a constant map is either $X$ (if $c \in V$) or $\varnothing$ (if $c \notin V$), both of which are always open by axiom (T1). Preimages preserve all set-theoretic operations (unions, intersections, complements), whereas forward images do not.
{% endcapture %}
{% include block.html type="supplement" title="Why preimages rather than forward images?" content=supp_preimage_vs_forward %}

---

## First examples: identity and inclusion maps

We examine the simplest maps between topological spaces.

### Example 1: The identity map

{% capture ex_identity %}
Let $(X,\tau)$ be any topological space, and let $\text{id}_X : X \to X$ be the identity map: $\text{id}_X(x) = x$.

**Claim.** $\text{id}_X$ is continuous.

**Proof.** Let $U \subseteq X$ be an open subset ($U \in \tau$). The preimage is
$$\text{id}_X^{-1}(U) = \lbrace x \in X \;:\; \text{id}_X(x) \in U \rbrace = \lbrace x \in X \;:\; x \in U \rbrace = U.$$
Since $U \in \tau$, the preimage is open in $X$. Thus $\text{id}_X$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="example" title="Example 1 (Continuity of the Identity Map)" content=ex_identity %}

---

### Example 2: The inclusion of a subspace

{% capture prop_incl_cont %}
Let $(X,\tau_X)$ be a topological space, let $Y \subseteq X$ be a subset equipped with the subspace topology $\tau_Y$, and let
$$i : Y \hookrightarrow X, \qquad i(y) = y$$
denote the canonical inclusion map.

Then $i : (Y, \tau_Y) \to (X, \tau_X)$ is continuous.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 7.2 (Continuity of the Subspace Inclusion)" content=prop_incl_cont %}

{% capture prop_incl_proof %}
Let $U \subseteq X$ be an open subset in the ambient space ($U \in \tau_X$). We must show that $i^{-1}(U)$ is open in $Y$ with respect to the subspace topology $\tau_Y$.

By definition of the preimage:
$$i^{-1}(U) = \lbrace y \in Y \;:\; i(y) \in U \rbrace = \lbrace y \in Y \;:\; y \in U \rbrace = U \cap Y.$$
By [Definition 4.3 in Lecture 4]({{ site.baseurl }}/point-set-topology/lecture-04/#definition-4-3-subspace-topology), the subspace topology $\tau_Y$ consists precisely of all intersections of open sets in $X$ with $Y$:
$$\tau_Y = \lbrace U \cap Y \;:\; U \in \tau_X \rbrace.$$
Therefore, $i^{-1}(U) = U \cap Y \in \tau_Y$.

Hence the preimage of every open set in $X$ is open in $Y$, so the inclusion map $i$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 7.2" content=prop_incl_proof %}

---

### Characterization: the subspace topology is minimal

The subspace topology is not merely *some* topology making the inclusion continuous; it is the unique smallest topology on $Y$ with this property.

{% capture prop_subspace_min %}
Let $X$ be a topological space, let $Y \subseteq X$ be a subset, and let $i : Y \hookrightarrow X$ be the inclusion map.

Let $\tau$ be *any* topology on $Y$ such that the inclusion map $i : (Y,\tau) \to (X,\tau_X)$ is continuous. Then $\tau$ contains the subspace topology $\tau_Y$:
$$\tau_Y \subseteq \tau.$$
In other words, the subspace topology $\tau_Y$ is the **coarsest (smallest)** topology on $Y$ for which the inclusion map $i$ is continuous.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 7.3 (Subspace Topology is the Coarsest Making Inclusion Continuous)" content=prop_subspace_min %}

{% capture prop_subspace_min_proof %}
Let $V \in \tau_Y$ be an arbitrary open set in the subspace topology.
By definition of $\tau_Y$, there exists an open set $U \in \tau_X$ such that
$$V = U \cap Y.$$
As shown in Proposition 7.2, $U \cap Y = i^{-1}(U)$. Thus
$$V = i^{-1}(U).$$
Now we use our hypothesis: the inclusion map $i : (Y,\tau) \to (X,\tau_X)$ is given to be continuous. By Definition 7.1, the preimage of the open set $U \in \tau_X$ under $i$ must be open in the topology $\tau$ on $Y$:
$$i^{-1}(U) \in \tau.$$
Since $V = i^{-1}(U)$, this implies $V \in \tau$.

Since $V \in \tau_Y$ was arbitrary, this establishes that $\tau_Y \subseteq \tau$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 7.3" content=prop_subspace_min_proof %}

---

## Projections from product spaces

We now examine maps associated with Cartesian products.

Let $\lbrace (X_i, \tau_i) \rbrace_{i \in I}$ be an arbitrary collection of topological spaces, and let $\prod_{i \in I} X_i$ be equipped with the product topology $\tau_{\text{prod}}$ ([Definition 6.2 in Lecture 6]({{ site.baseurl }}/point-set-topology/lecture-06/#definition-6-2-the-product-topology-on-arbitrary-products)).

For each index $j \in I$, the **coordinate projection** onto the $j$-th factor is the map
$$p_j : \prod_{i \in I} X_i \to X_j, \qquad p_j\bigl((x_i)_{i \in I}\bigr) = x_j.$$

{% capture prop_proj_cont %}
Let $\prod_{i \in I} X_i$ be equipped with the product topology $\tau_{\text{prod}}$. Then for every $j \in I$, the coordinate projection map
$$p_j : \prod_{i \in I} X_i \to X_j$$
is continuous.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 7.4 (Continuity of Coordinate Projections)" content=prop_proj_cont %}

{% include figure.html
   src="point-set-topology/lecture-07/projection-cylinder.svg"
   caption="Coordinate projection $p_j$: pulling back an open set $U \subseteq X_j$ gives the basic open cylinder $p_j^{-1}(U) = U \times \prod_{i \ne j} X_i$ in the product space."
   alt="Product space with a vertical strip representing the preimage p_j^{-1}(U) projecting down onto the interval U in X_j." %}

{% capture prop_proj_proof %}
Let $U \subseteq X_j$ be an open subset ($U \in \tau_j$). We must show that $p_j^{-1}(U)$ is open in $\tau_{\text{prod}}$.

By definition of the preimage:
$$p_j^{-1}(U) = \lbrace (x_i)_{i \in I} \in \prod_{i \in I} X_i \;:\; p_j\bigl((x_i)_{i \in I}\bigr) \in U \rbrace = \lbrace (x_i)_{i \in I} \;:\; x_j \in U \rbrace.$$
In terms of Cartesian products, this can be written as
$$p_j^{-1}(U) = \prod_{i \in I} U_i, \qquad \text{where } U_j = U, \text{ and } U_i = X_i \text{ for all } i \ne j.$$
We examine whether this set belongs to the defining basis $\mathcal{B}_2$ of the product topology:
1. For each coordinate $i$, $U_i$ is open in $X_i$: $U_j = U \in \tau_j$, and for $i \ne j$, $U_i = X_i \in \tau_i$.
2. The set of coordinates where $U_i \ne X_i$ consists of at most the single index $j$:
   $$\lbrace i \in I \;:\; U_i \ne X_i \rbrace \subseteq \lbrace j \rbrace,$$
   which has cardinality at most $1$, and is therefore finite.

Thus $p_j^{-1}(U)$ is a basic open cylinder in $\mathcal{B}_2$.
Since $\mathcal{B}_2 \subseteq \tau_{\text{prod}}$, it follows that $p_j^{-1}(U) \in \tau_{\text{prod}}$.

Therefore, each coordinate projection $p_j$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 7.4" content=prop_proj_proof %}

---

### Characterization: the product topology is minimal

Just as the subspace topology is the coarsest topology making the inclusion continuous, the product topology is the coarsest topology making all projections continuous.

{% capture prop_prod_min %}
Let $\lbrace (X_i, \tau_i) \rbrace_{i \in I}$ be a family of topological spaces, and let $\tau$ be *any* topology on the product $\prod_{i \in I} X_i$ such that every coordinate projection
$$p_j : \left(\prod_{i \in I} X_i, \; \tau\right) \to (X_j, \tau_j)$$
is continuous for every $j \in I$.

Then $\tau$ contains the product topology:
$$\tau_{\text{prod}} \subseteq \tau.$$
In other words, the product topology $\tau_{\text{prod}}$ is the **coarsest (smallest)** topology on $\prod_{i \in I} X_i$ for which all coordinate projection maps are continuous.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 7.5 (Product Topology is the Coarsest Making All Projections Continuous)" content=prop_prod_min %}

{% capture prop_prod_min_proof %}
By [Lemma 5.1 (The Comparison Lemma)]({{ site.baseurl }}/point-set-topology/lecture-05/#lemma-5-1-the-comparison-lemma), to prove $\tau_{\text{prod}} \subseteq \tau$, it is sufficient to show that the defining basis $\mathcal{B}_2$ of $\tau_{\text{prod}}$ is contained in $\tau$:
$$\mathcal{B}_2 \subseteq \tau.$$

Let $W \in \mathcal{B}_2$ be an arbitrary basic open cylinder:
$$W = \prod_{i \in I} U_i, \qquad U_i \in \tau_i \text{ for all } i \in I,$$
where the set of restricted indices $J = \lbrace i \in I : U_i \ne X_i \rbrace$ is finite.

We express $W$ in terms of preimages under the coordinate projections:

> **Key Identity.** For any basic cylinder $W = \prod_{i \in I} U_i \in \mathcal{B}_2$ with finite restricted index set $J$:
> $$\prod_{i \in I} U_i = \bigcap_{j \in J} p_j^{-1}(U_j).$$

*(Proof of Key Identity: A point $x = (x_i)_{i \in I}$ belongs to $\prod_{i \in I} U_i$ if and only if $x_i \in U_i$ for all $i \in I$. When $i \notin J$, $U_i = X_i$, so $x_i \in X_i$ is automatically satisfied. Thus $x \in \prod U_i$ if and only if $x_j \in U_j$ for all $j \in J$, which is equivalent to $x \in p_j^{-1}(U_j)$ for all $j \in J$, that is, $x \in \bigcap_{j \in J} p_j^{-1}(U_j)$).*

Now inspect this expression in the topology $\tau$:
- For each $j \in J$, $U_j \in \tau_j$. Since the projection $p_j$ is continuous with respect to $\tau$, the preimage $p_j^{-1}(U_j)$ belongs to $\tau$.
- The set $J$ is **finite**. Since $\tau$ is a topology, it satisfies axiom (T2): finite intersections of open sets are open. Therefore,
  $$W = \bigcap_{j \in J} p_j^{-1}(U_j) \in \tau.$$

This proves that every basic cylinder $W \in \mathcal{B}_2$ belongs to $\tau$, so $\mathcal{B}_2 \subseteq \tau$.
By the Comparison Lemma, $\tau_{\text{prod}} \subseteq \tau$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 7.5" content=prop_prod_min_proof %}

---

## Why the box topology fails: the diagonal map

We now reveal the concrete defect of the box topology.

Consider the real line $\mathbb{R}$ with its standard Euclidean topology, and let $\mathbb{R}^\mathbb{N} = \prod_{n=1}^\infty \mathbb{R}$ be the countably infinite Cartesian product of copies of $\mathbb{R}$.

Consider the **diagonal map** $\Delta : \mathbb{R} \to \prod_{n=1}^\infty \mathbb{R}$, which copies an input across all coordinates:
$$\Delta : \mathbb{R} \to \prod_{n=1}^\infty \mathbb{R}, \qquad \Delta(x) = (x, x, x, \dots).$$

Intuitively, duplicating a real number into every coordinate is as simple and well-behaved an operation as one could conceive. Yet under the box topology, it is discontinuous:

{% capture prop_box_diag_fail %}
Equip $\prod_{n=1}^\infty \mathbb{R}$ with the box topology $\tau_{\text{box}}$. Then the diagonal map
$$\Delta : \mathbb{R} \to \left(\prod_{n=1}^\infty \mathbb{R}, \; \tau_{\text{box}}\right)$$
is **not continuous**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 7.6 (Discontinuity of the Diagonal Map in the Box Topology)" content=prop_box_diag_fail %}

{% include figure.html
   src="point-set-topology/lecture-07/diagonal-box-failure.svg"
   caption="Discontinuity of the diagonal map $\Delta$ under the box topology: the preimage of the box open set $\prod_{n=1}^\infty (-1/n, 1/n)$ is the singleton $\lbrace 0\rbrace$, which fails to be open in $\mathbb{R}$."
   alt="The domain R on the left mapping via Delta to the infinite product on the right, showing shrinking coordinate intervals whose intersection collapses to the isolated point 0." %}

{% capture prop_box_diag_proof %}
To prove that $\Delta$ is not continuous, we exhibit an open set $U \in \tau_{\text{box}}$ whose preimage $\Delta^{-1}(U)$ is **not open** in the standard topology on $\mathbb{R}$.

For each integer $n \ge 1$, consider the open interval
$$U_n = \left(-\frac{1}{n}, \; \frac{1}{n}\right) \subseteq \mathbb{R}.$$
Each $U_n$ is open in $\mathbb{R}$. By [Definition 6.1 in Lecture 6]({{ site.baseurl }}/point-set-topology/lecture-06/#definition-6-1-the-box-topology), the Cartesian product
$$U = \prod_{n=1}^\infty U_n = \prod_{n=1}^\infty \left(-\frac{1}{n}, \; \frac{1}{n}\right) = (-1, 1) \times \left(-\frac{1}{2}, \frac{1}{2}\right) \times \left(-\frac{1}{3}, \frac{1}{3}\right) \times \cdots$$
is a basic open set in the box topology, so $U \in \tau_{\text{box}}$.

We compute the preimage $\Delta^{-1}(U) \subseteq \mathbb{R}$:
$$\begin{aligned}
\Delta^{-1}(U) &= \lbrace x \in \mathbb{R} \;:\; \Delta(x) \in U \rbrace \\
&= \lbrace x \in \mathbb{R} \;:\; (x, x, x, \dots) \in \prod_{n=1}^\infty \left(-\frac{1}{n}, \frac{1}{n}\right) \rbrace \\
&= \lbrace x \in \mathbb{R} \;:\; -\frac{1}{n} < x < \frac{1}{n} \text{ for every } n \ge 1 \rbrace \\
&= \bigcap_{n=1}^\infty \left(-\frac{1}{n}, \; \frac{1}{n}\right).
\end{aligned}$$

What real numbers satisfy $\lvert x \rvert < 1/n$ for every positive integer $n$?
- Clearly $x = 0$ satisfies $0 < 1/n$ for all $n \ge 1$.
- If $x \ne 0$, then $\lvert x \rvert > 0$. By the Archimedean property of the real numbers, there exists an integer $n_0$ such that $1/n_0 < \lvert x \rvert$, which means $x \notin (-1/n_0, 1/n_0)$.

Therefore, the intersection collapses to a single point:
$$\Delta^{-1}(U) = \lbrace 0 \rbrace.$$

In the standard topology on $\mathbb{R}$, is the singleton $\lbrace 0 \rbrace$ an open set?
No. By [Lecture 2]({{ site.baseurl }}/point-set-topology/lecture-02/#definition-2-2-property), for $\lbrace 0 \rbrace$ to be open, there would have to exist $\varepsilon > 0$ such that
$$(-\varepsilon, \varepsilon) \subseteq \lbrace 0 \rbrace,$$
which is absurd (any interval contains non-zero points such as $\varepsilon/2$).

Thus $U$ is open in $\tau_{\text{box}}$, but its preimage $\Delta^{-1}(U) = \lbrace 0 \rbrace$ is not open in $\mathbb{R}$.
We conclude that $\Delta$ is not continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 7.6" content=prop_box_diag_proof %}

---

## Forward reference: the basis criterion for continuity

In contrast to Proposition 7.6, the diagonal map $\Delta : X \to \prod_{i \in I} X$ **is continuous** when the product is given the product topology $\tau_{\text{prod}}$ ([Exercise 7.3](#exercise-7-3-continuity-of-the-diagonal-map-into-a-product-space)).

To prove this easily, one does not check all open sets of the codomain, but only the basic open sets:

{% capture lem_basis_cont_preview %}
Let $(X,\tau_X)$ and $(Y,\tau_Y)$ be topological spaces, and let $\mathcal{B}_Y$ be a basis for $\tau_Y$. A map $f : X \to Y$ is continuous if and only if
$$f^{-1}(B) \in \tau_X \quad \text{for every basis element } B \in \mathcal{B}_Y.$$
{% endcapture %}
{% include block.html type="lemma" title="Lemma 7.7 (The Basis Criterion for Continuity — Preview)" content=lem_basis_cont_preview %}

We will prove Lemma 7.7 at the very start of [Lecture 8]({{ site.baseurl }}/point-set-topology/lecture-08/), and use it to verify the continuity of algebraic addition and multiplication $\mathbb{R}^2 \to \mathbb{R}$.

---

## Exercises

{% capture ex71_content %}
Let $\lbrace X_i \rbrace_{i \in I}$ be a collection of sets, let $J \subseteq I$ be a finite subset, and for each $j \in J$, let $U_j \subseteq X_j$. Prove the set identity:
$$\prod_{i \in I} U_i = \bigcap_{j \in J} p_j^{-1}(U_j),$$
where $U_i = X_i$ for all $i \notin J$.
{% endcapture %}
{% capture ex71_sol %}
Let $x = (x_i)_{i \in I} \in \prod_{i \in I} X_i$.
1. Suppose $x \in \prod_{i \in I} U_i$. Then $x_i \in U_i$ for all $i \in I$. In particular, for every $j \in J$, $x_j = p_j(x) \in U_j$, so $x \in p_j^{-1}(U_j)$. Since this holds for all $j \in J$, $x \in \bigcap_{j \in J} p_j^{-1}(U_j)$.
2. Conversely, suppose $x \in \bigcap_{j \in J} p_j^{-1}(U_j)$. Then for every $j \in J$, $p_j(x) = x_j \in U_j$. For any $i \notin J$, $x_i \in X_i = U_i$ holds trivially. Thus $x_i \in U_i$ for all $i \in I$, which means $x \in \prod_{i \in I} U_i$.

Both inclusions hold, proving the identity. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 7.1 (The cylinder intersection identity)" content=ex71_content solution=ex71_sol %}

{% capture ex72_content %}
Let $X, Y, Z$ be topological spaces, and let $f : X \to Y$ and $g : Y \to Z$ be continuous maps. Prove that the composition
$$g \circ f : X \to Z$$
is continuous.
{% endcapture %}
{% capture ex72_sol %}
Let $W \subseteq Z$ be an open subset ($W \in \tau_Z$).
By the set-theoretic identity for preimages of composed functions:
$$(g \circ f)^{-1}(W) = f^{-1}\bigl(g^{-1}(W)\bigr).$$
Since $g : Y \to Z$ is continuous, the preimage $V = g^{-1}(W)$ is open in $Y$ ($V \in \tau_Y$).
Since $f : X \to Y$ is continuous and $V \in \tau_Y$, the preimage $f^{-1}(V) = f^{-1}\bigl(g^{-1}(W)\bigr)$ is open in $X$.
Therefore, $(g \circ f)^{-1}(W) \in \tau_X$, proving that $g \circ f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 7.2 (Composition of continuous maps)" content=ex72_content solution=ex72_sol %}

{% capture ex73_content %}
Let $X$ be a topological space, and let $\prod_{i \in I} X$ carry the product topology $\tau_{\text{prod}}$. Prove that the diagonal map
$$\Delta : X \to \prod_{i \in I} X, \qquad \Delta(x) = (x)_{i \in I}$$
is continuous.
{% endcapture %}
{% capture ex73_sol %}
Let $W = \prod_{i \in I} U_i \in \mathcal{B}_2$ be an arbitrary basic open cylinder in the product topology, with restricted index set $J = \lbrace i \in I : U_i \ne X \rbrace$ finite.
By Exercise 7.1, $W = \bigcap_{j \in J} p_j^{-1}(U_j)$.
Taking preimages under $\Delta$:
$$\Delta^{-1}(W) = \Delta^{-1}\left(\bigcap_{j \in J} p_j^{-1}(U_j)\right) = \bigcap_{j \in J} \Delta^{-1}\bigl(p_j^{-1}(U_j)\bigr) = \bigcap_{j \in J} (p_j \circ \Delta)^{-1}(U_j).$$
Notice that for any $x \in X$, $(p_j \circ \Delta)(x) = p_j(x, x, \dots) = x$.
Thus $p_j \circ \Delta = \text{id}_X$ is the identity map on $X$!
Therefore, $(p_j \circ \Delta)^{-1}(U_j) = \text{id}_X^{-1}(U_j) = U_j$.
Hence,
$$\Delta^{-1}(W) = \bigcap_{j \in J} U_j.$$
Since $J$ is **finite** and each $U_j \in \tau_X$, axiom (T2) implies that the finite intersection $\bigcap_{j \in J} U_j$ is open in $X$.
Since preimages of basic cylinders are open, the preimage of any arbitrary union of basic cylinders is an arbitrary union of open sets in $X$, which is open by (T3).
Thus $\Delta$ is continuous in the product topology. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 7.3 (Continuity of the diagonal map into a product space)" content=ex73_content solution=ex73_sol %}

{% capture ex74_content %}
Let $X$ and $Y$ be topological spaces, and let $c \in Y$. Prove that the constant map
$$f : X \to Y, \qquad f(x) = c \quad \text{for all } x \in X$$
is continuous.
{% endcapture %}
{% capture ex74_sol %}
Let $V \subseteq Y$ be an open subset.
We compute the preimage $f^{-1}(V) = \lbrace x \in X : f(x) \in V \rbrace = \lbrace x \in X : c \in V \rbrace$:
- If $c \in V$, then every point $x \in X$ satisfies $f(x) = c \in V$, so $f^{-1}(V) = X$.
- If $c \notin V$, then no point $x \in X$ satisfies $f(x) \in V$, so $f^{-1}(V) = \varnothing$.

In both cases, by axiom (T1) of a topological space, $\varnothing \in \tau_X$ and $X \in \tau_X$.
Therefore, the preimage of every open set is open, so $f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 7.4 (Continuity of constant maps)" content=ex74_content solution=ex74_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Definition 7.1 (Continuous Map)](#definition-7-1-continuous-map): $f : X \to Y$ is continuous if $\forall V \in \tau_Y$, $f^{-1}(V) \in \tau_X$.
- [Example 1 (Continuity of the Identity Map)](#example-1-continuity-of-the-identity-map): $\text{id}_X^{-1}(U) = U$ is open.
- [Proposition 7.2 (Continuity of the Subspace Inclusion)](#proposition-7-2-continuity-of-the-subspace-inclusion): $i : (Y,\tau_Y) \hookrightarrow (X,\tau_X)$ is continuous via $i^{-1}(U) = U \cap Y$.
- [Proposition 7.3 (Subspace Topology is the Coarsest Making Inclusion Continuous)](#proposition-7-3-subspace-topology-is-the-coarsest-making-inclusion-continuous): Any topology on $Y$ making inclusion continuous contains $\tau_Y$.
- [Proposition 7.4 (Continuity of Coordinate Projections)](#proposition-7-4-continuity-of-coordinate-projections): Coordinate projections $p_j : \prod X_i \to X_j$ are continuous under $\tau_{\text{prod}}$.
- [Proposition 7.5 (Product Topology is the Coarsest Making All Projections Continuous)](#proposition-7-5-product-topology-is-the-coarsest-making-all-projections-continuous): Any topology making all $p_j$ continuous contains $\tau_{\text{prod}}$.
- [Proposition 7.6 (Discontinuity of the Diagonal Map in the Box Topology)](#proposition-7-6-discontinuity-of-the-diagonal-map-in-the-box-topology): $\Delta^{-1}\left(\prod_{n=1}^\infty (-1/n, 1/n)\right) = \lbrace 0\rbrace \notin \tau_{\mathbb{R}}$, proving box failure.
- [Lemma 7.7 (The Basis Criterion for Continuity — Preview)](#lemma-7-7-the-basis-criterion-for-continuity-preview): $f$ continuous iff $f^{-1}(B)$ open for all $B \in \mathcal{B}_Y$.
- [Exercise 7.1 (The cylinder intersection identity)](#exercise-7-1-the-cylinder-intersection-identity): $\prod U_i = \bigcap_{j \in J} p_j^{-1}(U_j)$.
- [Exercise 7.2 (Composition of continuous maps)](#exercise-7-2-composition-of-continuous-maps): $(g \circ f)^{-1}(W) = f^{-1}(g^{-1}(W))$.
- [Exercise 7.3 (Continuity of the diagonal map into a product space)](#exercise-7-3-continuity-of-the-diagonal-map-into-a-product-space): $\Delta$ is continuous in the product topology.
- [Exercise 7.4 (Continuity of constant maps)](#exercise-7-4-continuity-of-constant-maps): Preimages are $\varnothing$ or $X$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §18.** Section 18 introduces continuous maps with numerous examples, proves that inclusions and projections are continuous, and formulates the subspace and product topologies as initial topologies.

**Morris, *Topology Without Tears*, Chapter 4.** Sections 4.1–4.2 present an accessible introduction to continuity via open sets, comparing it directly to metric continuity.
