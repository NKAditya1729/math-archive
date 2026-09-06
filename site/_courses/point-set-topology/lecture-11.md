---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 11
title: "Closed Sets, Dual Axioms, and Preimages"
coverage: >
  Defines closed subsets of a topological space via open complements and derives
  the three dual axioms for closed sets. Proves that a map is continuous if and only
  if preimages of closed sets are closed. Demonstrates how to prove subsets are open
  or closed by realizing them as preimages under polynomial maps, establishing that
  spheres S^1 and S^n, the special linear group SL_n(R), and the orthogonal group
  O(n) are closed subsets, while the general linear group GL_n(R) is an open subset
  of M_n(R). Proves that singletons in R^m are closed.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 1
depends_on:
  - lecture: 10
    title: "Equivalence of Product and Standard Topologies, Projections, and Homeomorphisms"
    relationship: "Supplies the equivalence of product and standard topologies on Euclidean spaces, and the polynomial continuity criterion."
  - lecture: 9
    title: "Properties of Continuous Maps and Algebraic Combinations"
    relationship: "Supplies continuity of sums, products, and compositions of coordinate projections."
used_in:
  - lecture: 12
    title: "The Closure of a Subset: Definition, Properties, and Examples"
    relationship: "Lecture 12 defines the closure of a set as the intersection of all closed sets containing it, and proves A is closed iff A = cl(A)."
notation:
  - symbol: "$X \\setminus Z$"
    gloss: 'Complement of subset $Z$ in $X$'
  - symbol: "$GL_n(\\mathbb{R})$"
    gloss: 'The general linear group $\\lbrace A \\in M_n(\\mathbb{R}) : \\det(A) \\ne 0\\rbrace$, an open subset of $M_n(\\mathbb{R})$'
  - symbol: "$SL_n(\\mathbb{R})$"
    gloss: 'The special linear group $\\lbrace A \\in M_n(\\mathbb{R}) : \\det(A) = 1\\rbrace$, a closed subset of $M_n(\\mathbb{R})$'
  - symbol: "$O(n)$"
    gloss: 'The orthogonal group $\\lbrace A \\in M_n(\\mathbb{R}) : A^T A = I_n\\rbrace$, a closed subset of $M_n(\\mathbb{R})$'
prev: lecture-10
next: lecture-12
---

# Lecture 11 — Closed Sets, Dual Axioms, and Preimages

## Where we are

In [Lecture 10]({{ site.baseurl }}/point-set-topology/lecture-10/), we established that the standard topology on $\mathbb{R}^n$ coincides with the product topology on the $n$-fold Cartesian product $\mathbb{R} \times \dots \times \mathbb{R}$. We verified the continuity of geometric projections by decomposing them into polynomial and rational operations on coordinate projections, and defined the notion of a homeomorphism.

Here we initiate our study of the second fundamental pillar of topology: **closed sets**. Rather than viewing open sets in isolation, we study their complements, deriving the three dual axioms that characterize topologies entirely in terms of closed families. We prove that continuity can be characterized dually via preimages of closed sets. This perspective provides an exceptionally powerful technique: by realizing geometric sets (spheres $S^n$, matrix groups $GL_n(\mathbb{R})$, $SL_n(\mathbb{R})$, $O(n)$) as preimages under polynomial maps, we determine whether they are open or closed in a single line, completely bypassing cumbersome direct epsilon-ball arguments.

---

## Closed sets and the dual topology axioms

We begin with the defining definition of a closed set.

### Definition 11.1 (Closed subset) {#definition-11-1-closed-subset}

{% capture def111_content %}
Let $(X, \tau)$ be a topological space. A subset $Z \subseteq X$ is said to be **closed** in $X$ if its complement
$$X \setminus Z \in \tau$$
is an open subset of $X$.
{% endcapture %}
{% include block.html type="definition" title="Definition 11.1 (Closed Subset)" content=def111_content %}

From the three axioms of open sets ([Lecture 1]({{ site.baseurl }}/point-set-topology/lecture-01/#definition-1-1-topology-topological-space)) and De Morgan's laws, we immediately obtain the dual properties satisfied by closed sets.

### Lemma 11.2 (Dual axioms for closed sets) {#lemma-11-2-dual-axioms-for-closed-sets}

{% capture lem112_content %}
Let $(X, \tau)$ be a topological space.
1. The empty set $\varnothing$ and the whole space $X$ are closed.
2. If $Z_1, Z_2, \dots, Z_r$ are finitely many closed subsets of $X$, then their union
   $$\bigcup_{k=1}^r Z_k = Z_1 \cup Z_2 \cup \dots \cup Z_r$$
   is closed.
3. If $\lbrace Z_i \rbrace_{i \in I}$ is an arbitrary family of closed subsets of $X$, then their intersection
   $$\bigcap_{i \in I} Z_i$$
   is closed.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 11.2 (Dual Axioms for Closed Sets)" content=lem112_content %}

{% capture lem112_proof %}
1. The complement $X \setminus \varnothing = X$ is open by axiom (T1), so $\varnothing$ is closed. The complement $X \setminus X = \varnothing$ is open by axiom (T1), so $X$ is closed.
2. Let $Z_1, \dots, Z_r$ be closed. By De Morgan's law:
   $$X \setminus \left( \bigcup_{k=1}^r Z_k \right) = \bigcap_{k=1}^r (X \setminus Z_k).$$
   Each $X \setminus Z_k$ is open. By axiom (T2), the finite intersection of open sets is open. Hence the complement of $\bigcup_{k=1}^r Z_k$ is open, so $\bigcup_{k=1}^r Z_k$ is closed.
3. Let $\lbrace Z_i \rbrace_{i \in I}$ be a family of closed subsets. By De Morgan's law:
   $$X \setminus \left( \bigcap_{i \in I} Z_i \right) = \bigcup_{i \in I} (X \setminus Z_i).$$
   Each $X \setminus Z_i$ is open. By axiom (T3), an arbitrary union of open sets is open. Hence the complement of $\bigcap_{i \in I} Z_i$ is open, so $\bigcap_{i \in I} Z_i$ is closed. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 11.2" content=lem112_proof %}

{% capture rem_top_by_closed %}
#### Specifying a topology via closed sets
Just as a topology can be defined by specifying a collection $\tau \subseteq \mathcal{P}(X)$ of open sets satisfying (T1)–(T3), one may equivalently define a topology by specifying a collection $\mathcal{F} \subseteq \mathcal{P}(X)$ of closed sets satisfying (1) containing $\varnothing$ and $X$, (2) closed under finite unions, and (3) closed under arbitrary intersections. The collection $\tau = \lbrace X \setminus Z : Z \in \mathcal{F} \rbrace$ then forms a topology on $X$.
{% endcapture %}
{% include block.html type="supplement" title="Specifying a topology via closed sets" content=rem_top_by_closed %}

---

## Characterizing continuity via closed preimages

Recall that a map $f : X \to Y$ is continuous if the preimage of every open set in $Y$ is open in $X$. We now prove that this criterion is completely dualized for closed sets.

### Theorem 11.3 (Continuity via closed preimages) {#theorem-11-3-continuity-via-closed-preimages}

{% capture thm113_content %}
Let $X$ and $Y$ be topological spaces, and let $f : X \to Y$ be a map of sets.
Then $f$ is continuous if and only if for every closed subset $Z \subseteq Y$, the preimage
$$f^{-1}(Z) \subseteq X$$
is a closed subset of $X$.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 11.3 (Continuity via Closed Preimages)" content=thm113_content %}

{% capture thm113_proof %}
The proof relies on the fundamental set-theoretic property of the inverse image: for any subset $Z \subseteq Y$,
$$f^{-1}(Y \setminus Z) = X \setminus f^{-1}(Z).$$
Indeed:
$$x \in f^{-1}(Y \setminus Z) \iff f(x) \in Y \setminus Z \iff f(x) \notin Z \iff x \notin f^{-1}(Z) \iff x \in X \setminus f^{-1}(Z).$$

**$(\implies)$ First let us assume that $f$ is continuous.**
Let $Z \subseteq Y$ be a closed subset. We need to show that $f^{-1}(Z)$ is closed in $X$.
Since $Z$ is closed, the complement $V = Y \setminus Z$ is open in $Y$.
Since $f$ is continuous, the preimage $f^{-1}(V) = f^{-1}(Y \setminus Z)$ is open in $X$.
Using the set-theoretic identity above:
$$X \setminus f^{-1}(Z) = f^{-1}(Y \setminus Z) \in \tau_X.$$
Because the complement of $f^{-1}(Z)$ is open in $X$, by Definition 11.1 this implies that $f^{-1}(Z)$ is closed in $X$.
So this shows that the preimage of every closed subset is closed.

**$(\impliedby)$ Conversely, let us assume that $f^{-1}(Z)$ is closed in $X$ for every closed subset $Z \subseteq Y$.**
We want to show that $f$ is continuous. So let $V \subseteq Y$ be an open subset.
Then the complement $Z = Y \setminus V$ is closed in $Y$.
By hypothesis, the preimage $f^{-1}(Z) = f^{-1}(Y \setminus V)$ is closed in $X$.
Using the identity again:
$$f^{-1}(Y \setminus V) = X \setminus f^{-1}(V).$$
So the complement $X \setminus f^{-1}(V)$ is closed in $X$, which implies that $f^{-1}(V)$ is open in $X$.
Since this holds for every open subset $V \subseteq Y$, thus $f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 11.3" content=thm113_proof %}

---

## Proving sets are open or closed via continuous preimages

We now revisit several geometric sets and matrix groups introduced in [Lecture 6]({{ site.baseurl }}/point-set-topology/lecture-06/), showing how continuity determines their topological status.

### The coordinate projection strips

Before analyzing spheres and matrices, we examine preimages under the coordinate projections $p_1, p_2 : \mathbb{R}^2 \to \mathbb{R}$.
For an open interval $(a, b) \subseteq \mathbb{R}$:
- Under $p_2(x, y) = y$, the preimage is the horizontal strip:
  $$p_2^{-1}\bigl((a, b)\bigr) = \lbrace (x, y) \in \mathbb{R}^2 \;:\; y \in (a, b) \rbrace = \mathbb{R} \times (a, b).$$
- Under $p_1(x, y) = x$, the preimage is the vertical strip:
  $$p_1^{-1}\bigl((a, b)\bigr) = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x \in (a, b) \rbrace = (a, b) \times \mathbb{R}.$$
Since $p_1$ and $p_2$ are continuous ([Proposition 7.4]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-4-continuity-of-coordinate-projections)), both strips are open in $\mathbb{R}^2$.

{% include figure.html
   src="point-set-topology/lecture-11/projection-preimage-strips.svg"
   caption="Preimages of open intervals under coordinate projections: horizontal strip $p_2^{-1}((a, b)) = \mathbb{R} \times (a, b)$ and vertical strip $p_1^{-1}((a, b)) = (a, b) \times \mathbb{R}$ are open in $\mathbb{R}^2$."
   alt="Two panels showing horizontal and vertical open strips in the plane obtained as preimages of intervals under coordinate projections." %}

---

### Example 1: The unit circle $S^1$ is closed in $\mathbb{R}^2$ {#example-1-the-unit-circle-is-closed}

{% capture ex1_content %}
The unit circle is defined as:
$$S^1 = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x^2 + y^2 = 1 \rbrace.$$
Consider the map $f : \mathbb{R}^2 \to \mathbb{R}$ defined by:
$$f(x, y) = x^2 + y^2 = \bigl(p_1(x, y)\bigr)^2 + \bigl(p_2(x, y)\bigr)^2.$$
Because the projections $p_1$ and $p_2$ are continuous, their squares are continuous ([Proposition 9.5]({{ site.baseurl }}/point-set-topology/lecture-09/#proposition-9-5-continuity-of-sum-and-product)), and the sum of continuous functions is continuous. Hence $f$ is continuous.

Now consider the singleton subset $\lbrace 1 \rbrace \subset \mathbb{R}$.
Its complement $\mathbb{R} \setminus \lbrace 1 \rbrace = (-\infty, 1) \cup (1, \infty)$ is the union of two open intervals, hence open in $\mathbb{R}$.
Therefore, $\lbrace 1 \rbrace$ is a closed subset of $\mathbb{R}$.

By Definition, the preimage is:
$$f^{-1}\bigl(\lbrace 1 \rbrace\bigr) = \lbrace (x, y) \in \mathbb{R}^2 \;:\; f(x, y) = 1 \rbrace = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x^2 + y^2 = 1 \rbrace = S^1.$$
By Theorem 11.3, since $f$ is continuous and $\lbrace 1 \rbrace$ is closed in $\mathbb{R}$, the preimage $S^1$ is a **closed subset** of $\mathbb{R}^2$.
{% endcapture %}
{% include block.html type="example" title="Example 1 (The Unit Circle $S^1$ is Closed)" content=ex1_content %}

{% include figure.html
   src="point-set-topology/lecture-11/circle-as-preimage.svg"
   caption="The unit circle $S^1$ realized as the preimage $f^{-1}(\lbrace 1 \rbrace)$ under the continuous map $f(x, y) = x^2 + y^2$. Since $\lbrace 1 \rbrace$ is closed in $\mathbb{R}$, $S^1$ is closed in $\mathbb{R}^2$."
   alt="Diagram showing domain R^2 with circle S^1, map arrow f(x,y)=x^2+y^2, and target line R with closed singleton {1}." %}

---

### Example 2: The $n$-sphere $S^n$ is closed in $\mathbb{R}^{n+1}$ {#example-2-the-n-sphere-is-closed}

{% capture ex2_content %}
For any $n \ge 1$, the $n$-sphere is defined as:
$$S^n = \left\lbrace (x_0, x_1, \dots, x_n) \in \mathbb{R}^{n+1} \;:\; \sum_{k=0}^n x_k^2 = 1 \right\rbrace.$$
Define $f : \mathbb{R}^{n+1} \to \mathbb{R}$ by:
$$f(x_0, \dots, x_n) = \sum_{k=0}^n x_k^2 = \sum_{k=0}^n \bigl(p_k(x)\bigr)^2.$$
As each coordinate projection $p_k : \mathbb{R}^{n+1} \to \mathbb{R}$ is continuous, each square is continuous, and finite sums of continuous functions are continuous.
Thus $f$ is continuous.
Since $\lbrace 1 \rbrace$ is closed in $\mathbb{R}$, the preimage
$$f^{-1}\bigl(\lbrace 1 \rbrace\bigr) = S^n$$
is a **closed subset** of $\mathbb{R}^{n+1}$.
{% endcapture %}
{% include block.html type="example" title="Example 2 (The $n$-Sphere $S^n$ is Closed)" content=ex2_content %}

---

### Example 3: The general linear group $GL_n(\mathbb{R})$ is open in $M_n(\mathbb{R})$ {#example-3-gln-is-open}

{% capture ex3_content %}
Recall from [Lecture 6]({{ site.baseurl }}/point-set-topology/lecture-06/#example-2-classical-real-matrix-groups) that $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$ carries the product/standard topology, and the general linear group is:
$$GL_n(\mathbb{R}) = \lbrace A \in M_n(\mathbb{R}) \;:\; \det(A) \ne 0 \rbrace.$$

Consider the determinant map:
$$\det : M_n(\mathbb{R}) \longrightarrow \mathbb{R}.$$
For $n = 2$, $\det \begin{pmatrix} x_{11} & x_{12} \\ x_{21} & x_{22} \end{pmatrix} = x_{11} x_{22} - x_{12} x_{21}$.
In general, $\det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^n x_{i, \sigma(i)}$ is a polynomial expression in the matrix entries $x_{ij}$.
Each matrix entry $x_{ij}$ is a coordinate projection $p_{ij} : M_n(\mathbb{R}) \to \mathbb{R}$, which is continuous.
Because sums and products of continuous functions are continuous, **any polynomial in the coordinate projections is continuous**.
Hence the determinant map $\det : M_n(\mathbb{R}) \to \mathbb{R}$ is continuous.

Now observe that:
$$GL_n(\mathbb{R}) = \det^{-1}\bigl(\mathbb{R} \setminus \lbrace 0 \rbrace\bigr).$$
The set $\mathbb{R} \setminus \lbrace 0 \rbrace = (-\infty, 0) \cup (0, \infty)$ is an open subset of $\mathbb{R}$.
Since $\det$ is continuous, the preimage $GL_n(\mathbb{R})$ is an **open subset** of $M_n(\mathbb{R})$.
{% endcapture %}
{% include block.html type="example" title="Example 3 (The General Linear Group $GL_n(\mathbb{R})$ is Open)" content=ex3_content %}

{% capture corr11_content %}
**Transcript statement:** The transcript describes $GL_n(\mathbb{R})$ as *"the determinant inverse of this subset $\mathbb{R}$ minus $U$."* (sentence 187).
**Correction:** The target set is $\mathbb{R} \setminus \lbrace 0 \rbrace$. In the very next sentence (189), the lecturer explicitly states: *"and as $\mathbb{R}$ minus zero is open, right, so this implies $GL_n(\mathbb{R})$ is an open subset"*, resolving the transcription slip.
{% endcapture %}
{% include block.html type="correction" title="Correction Note (Target Set for General Linear Group)" content=corr11_content %}

---

### Example 4: The special linear group $SL_n(\mathbb{R})$ is closed in $M_n(\mathbb{R})$ {#example-4-sln-is-closed}

{% capture ex4_content %}
The special linear group is defined by:
$$SL_n(\mathbb{R}) = \lbrace A \in M_n(\mathbb{R}) \;:\; \det(A) = 1 \rbrace.$$
In terms of preimages under the continuous determinant map:
$$SL_n(\mathbb{R}) = \det^{-1}\bigl(\lbrace 1 \rbrace\bigr).$$
Since the singleton $\lbrace 1 \rbrace$ is closed in $\mathbb{R}$ and $\det$ is continuous, $SL_n(\mathbb{R})$ is a **closed subset** of $M_n(\mathbb{R})$.
{% endcapture %}
{% include block.html type="example" title="Example 4 (The Special Linear Group $SL_n(\mathbb{R})$ is Closed)" content=ex4_content %}

---

### Example 5: The orthogonal group $O(n)$ is closed in $M_n(\mathbb{R})$ {#example-5-on-is-closed}

{% capture ex5_content %}
The orthogonal group is defined by:
$$O(n) = \lbrace A \in M_n(\mathbb{R}) \;:\; A^T A = I_n \rbrace.$$
Consider the matrix multiplication map:
$$f : M_n(\mathbb{R}) \longrightarrow M_n(\mathbb{R}), \qquad f(A) = A^T A.$$
To verify that $f$ is continuous, we use the product mapping criterion ([Proposition 9.4]({{ site.baseurl }}/point-set-topology/lecture-09/#proposition-9-4-product-criterion-for-continuity)): $f$ is continuous if and only if each coordinate function $f_{ij} : M_n(\mathbb{R}) \to \mathbb{R}$ is continuous.

For $n = 2$:
$$\begin{pmatrix} x_{11} & x_{21} \\ x_{12} & x_{22} \end{pmatrix} \begin{pmatrix} x_{11} & x_{12} \\ x_{21} & x_{22} \end{pmatrix} = \begin{pmatrix} x_{11}^2 + x_{21}^2 & x_{11} x_{12} + x_{21} x_{22} \\ x_{12} x_{11} + x_{22} x_{21} & x_{12}^2 + x_{22}^2 \end{pmatrix}.$$
In general, the $(i, j)$-entry of $A^T A$ is:
$$f_{ij}(A) = (A^T A)_{ij} = \sum_{k=1}^n (A^T)_{ik} A_{kj} = \sum_{k=1}^n A_{ki} A_{kj} = \sum_{k=1}^n x_{ki} x_{kj}.$$
Each $f_{ij}(A)$ is a polynomial in the matrix entries $x_{rs}$.
Since polynomials in coordinate projections are continuous, each coordinate function $f_{ij}$ is continuous.
Therefore $f$ is continuous.

Notice that:
$$O(n) = f^{-1}\bigl(\lbrace I_n \rbrace\bigr),$$
where $I_n \in M_n(\mathbb{R})$ is the $n \times n$ identity matrix.
By Lemma 11.4 below, singletons in Euclidean space $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$ are closed.
Hence $\lbrace I_n \rbrace$ is a closed subset of $M_n(\mathbb{R})$.
By Theorem 11.3, $O(n) = f^{-1}(\lbrace I_n \rbrace)$ is a **closed subset** of $M_n(\mathbb{R})$.
{% endcapture %}
{% include block.html type="example" title="Example 5 (The Orthogonal Group $O(n)$ is Closed)" content=ex5_content %}

{% include figure.html
   src="point-set-topology/lecture-11/matrix-group-preimages.svg"
   caption="Matrix groups cut out by preimages under continuous maps: $GL_n(\mathbb{R}) = \det^{-1}(\mathbb{R} \setminus \lbrace 0 \rbrace)$ is open, while $SL_n(\mathbb{R}) = \det^{-1}(\lbrace 1 \rbrace)$ and $O(n) = f^{-1}(\lbrace I_n \rbrace)$ are closed."
   alt="Diagram showing M_n(R) with sub-boxes for GL_n, SL_n, and O(n), mapping via det and f(A)=A^T A to target spaces R and M_n(R)." %}

---

## Singletons in Euclidean space are closed

To complete the proof for $O(n)$ and establish a foundational property of Euclidean spaces, we state and prove that every point in $\mathbb{R}^m$ is closed.

### Lemma 11.4 (Points in $\mathbb{R}^m$ are closed) {#lemma-11-4-points-in-rm-are-closed}

{% capture lem114_content %}
Let $a = (a_1, \dots, a_m) \in \mathbb{R}^m$.
Then the singleton set $\lbrace a \rbrace$ is a closed subset of $\mathbb{R}^m$ equipped with the standard topology.
Equivalently, the complement $\mathbb{R}^m \setminus \lbrace a \rbrace$ is an open subset of $\mathbb{R}^m$.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 11.4 (Points in $\mathbb{R}^m$ are Closed)" content=lem114_content %}

{% capture lem114_proof %}
The lecturer left the verification as an exercise; we write it out in full.

To show that the singleton $\lbrace a \rbrace$ is closed, it suffices to show that its complement $U = \mathbb{R}^m \setminus \lbrace a \rbrace$ is open in $\mathbb{R}^m$.

Let $x = (x_1, \dots, x_m) \in \mathbb{R}^m \setminus \lbrace a \rbrace$. Then $x \ne a$, which means there exists at least one coordinate index $k \in \lbrace 1, \dots, m \rbrace$ such that $x_k \ne a_k$.
Set:
$$\varepsilon = |x_k - a_k| > 0.$$
Consider the basic open hypercube $S_\varepsilon(x) = \lbrace y \in \mathbb{R}^m : |y_i - x_i| < \varepsilon \text{ for all } i \rbrace$.
For any point $y \in S_\varepsilon(x)$, the $k$-th coordinate satisfies:
$$|y_k - x_k| < \varepsilon = |x_k - a_k|.$$
If $y = a$, this would imply $|a_k - x_k| < |x_k - a_k|$, a contradiction.
Therefore $a \notin S_\varepsilon(x)$, which means:
$$S_\varepsilon(x) \subseteq \mathbb{R}^m \setminus \lbrace a \rbrace.$$

Thus, for every $x \in \mathbb{R}^m \setminus \lbrace a \rbrace$, we have found $\varepsilon > 0$ such that $S_\varepsilon(x) \subseteq \mathbb{R}^m \setminus \lbrace a \rbrace$.
This implies that $\mathbb{R}^m \setminus \lbrace a \rbrace$ is open in the standard topology on $\mathbb{R}^m$.

So this shows that the singleton $\lbrace a \rbrace$ is a closed subset of $\mathbb{R}^m$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 11.4" content=lem114_proof %}

---

## Exercises

{% capture ex111_content %}
Prove the second remark from the lecture:
Let $X$ be a set, and let $\mathcal{F} \subseteq \mathcal{P}(X)$ be a collection of subsets satisfying:
1. $\varnothing, X \in \mathcal{F}$;
2. If $Z_1, \dots, Z_r \in \mathcal{F}$, then $\bigcup_{k=1}^r Z_k \in \mathcal{F}$;
3. If $\lbrace Z_i \rbrace_{i \in I} \subseteq \mathcal{F}$, then $\bigcap_{i \in I} Z_i \in \mathcal{F}$.

Define $\tau = \lbrace X \setminus Z : Z \in \mathcal{F} \rbrace$.
Show that $\tau$ defines a topology on $X$ whose closed sets are precisely $\mathcal{F}$.
{% endcapture %}
{% capture ex111_sol %}
We verify the three axioms of a topology (T1)–(T3) from [Lecture 1]({{ site.baseurl }}/point-set-topology/lecture-01/#definition-1-1-topology-topological-space):
- **(T1):** Since $X \in \mathcal{F}$, $X \setminus X = \varnothing \in \tau$. Since $\varnothing \in \mathcal{F}$, $X \setminus \varnothing = X \in \tau$.
- **(T2):** Let $U_1, \dots, U_r \in \tau$. Then for each $k$, $Z_k = X \setminus U_k \in \mathcal{F}$.
  By De Morgan's law:
  $$\bigcap_{k=1}^r U_k = \bigcap_{k=1}^r (X \setminus Z_k) = X \setminus \left( \bigcup_{k=1}^r Z_k \right).$$
  By property (2), $\bigcup_{k=1}^r Z_k \in \mathcal{F}$. Hence $X \setminus (\bigcup Z_k) \in \tau$, so $\tau$ is closed under finite intersections.
- **(T3):** Let $\lbrace U_i \rbrace_{i \in I} \subseteq \tau$. For each $i$, $Z_i = X \setminus U_i \in \mathcal{F}$.
  By De Morgan's law:
  $$\bigcup_{i \in I} U_i = \bigcup_{i \in I} (X \setminus Z_i) = X \setminus \left( \bigcap_{i \in I} Z_i \right).$$
  By property (3), $\bigcap_{i \in I} Z_i \in \mathcal{F}$. Hence $X \setminus (\bigcap Z_i) \in \tau$, so $\tau$ is closed under arbitrary unions.

Thus $\tau$ is a topology. Furthermore, $Z$ is closed in $(X, \tau)$ if and only if $X \setminus Z \in \tau \iff X \setminus Z = X \setminus Z'$ for some $Z' \in \mathcal{F} \iff Z = Z' \in \mathcal{F}$. So the closed sets are precisely $\mathcal{F}$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 11.1 (Defining Topologies via Closed Sets)" content=ex111_content solution=ex111_sol %}

{% capture ex112_content %}
Let $f : M_n(\mathbb{R}) \to M_n(\mathbb{R})$ be the map $f(A) = A^T A$.
Write down the explicit formula for the coordinate entry $f_{ij}(A)$ for general $n$, and confirm that $f_{ij}$ is a continuous polynomial function of the matrix entries.
{% endcapture %}
{% capture ex112_sol %}
Let $A = (x_{rs})_{1 \le r, s \le n} \in M_n(\mathbb{R})$.
The transpose is $A^T = (y_{rs})$ where $y_{rs} = x_{sr}$.
By the definition of matrix multiplication, the $(i, j)$-entry of $f(A) = A^T A$ is:
$$f_{ij}(A) = \sum_{k=1}^n y_{ik} x_{kj} = \sum_{k=1}^n x_{ki} x_{kj}.$$
This formula expresses $f_{ij}(A)$ as a finite sum of products of coordinate projections:
$$f_{ij} = \sum_{k=1}^n (p_{ki} \cdot p_{kj}).$$
Since each coordinate projection $p_{rs} : M_n(\mathbb{R}) \to \mathbb{R}$ is continuous, each product $p_{ki} \cdot p_{kj}$ is continuous by [Proposition 9.5]({{ site.baseurl }}/point-set-topology/lecture-09/#proposition-9-5-continuity-of-sum-and-product), and the finite sum of continuous functions is continuous.
Thus $f_{ij}$ is a continuous polynomial function for every $1 \le i, j \le n$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 11.2 (Coordinates of the Orthogonal Gram Matrix)" content=ex112_content solution=ex112_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Definition 11.1 (Closed Subset)](#definition-11-1-closed-subset): $Z \subseteq X$ is closed iff $X \setminus Z$ is open.
- [Lemma 11.2 (Dual Axioms for Closed Sets)](#lemma-11-2-dual-axioms-for-closed-sets): $\varnothing, X$ closed; finite unions closed; arbitrary intersections closed.
- [Theorem 11.3 (Continuity via Closed Preimages)](#theorem-11-3-continuity-via-closed-preimages): $f$ continuous iff $f^{-1}(Z)$ closed for every closed $Z \subseteq Y$.
- [Example 1 ($S^1$ Closed)](#example-1-the-unit-circle-is-closed): $S^1 = f^{-1}(\lbrace 1 \rbrace)$ with $f(x, y) = x^2+y^2$ continuous.
- [Example 2 ($S^n$ Closed)](#example-2-the-n-sphere-is-closed): $S^n = f^{-1}(\lbrace 1 \rbrace)$ with $f(x) = \sum x_i^2$ continuous.
- [Example 3 ($GL_n(\mathbb{R})$ Open)](#example-3-gln-is-open): $GL_n(\mathbb{R}) = \det^{-1}(\mathbb{R} \setminus \lbrace 0 \rbrace)$ is open.
- [Example 4 ($SL_n(\mathbb{R})$ Closed)](#example-4-sln-is-closed): $SL_n(\mathbb{R}) = \det^{-1}(\lbrace 1 \rbrace)$ is closed.
- [Example 5 ($O(n)$ Closed)](#example-5-on-is-closed): $O(n) = f^{-1}(\lbrace I_n \rbrace)$ with $f(A) = A^T A$ continuous.
- [Lemma 11.4 (Points in $\mathbb{R}^m$ are Closed)](#lemma-11-4-points-in-rm-are-closed): Every singleton $\lbrace a \rbrace$ is closed in $\mathbb{R}^m$.
- [Exercise 11.1 (Defining Topologies via Closed Sets)](#exercise-11-1-defining-topologies-via-closed-sets): Dual verification of axioms (T1)–(T3).
- [Exercise 11.2 (Coordinates of the Orthogonal Gram Matrix)](#exercise-11-2-coordinates-of-the-orthogonal-gram-matrix): $f_{ij}(A) = \sum_{k=1}^n x_{ki} x_{kj}$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §17.** Closed sets, dual axioms, preimages of closed sets, and closure.

**Morris, *Topology Without Tears*, Chapter 2.** Section 2.1 discusses closed sets and complements.
