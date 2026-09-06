---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 13
title: "Dense Subsets, Subspace Closed Sets, and the Pasting Lemma"
coverage: >
  Defines dense subsets and proves that every subset A is dense in its closure
  cl(A). Proves that an open subset of an open subspace is open in the ambient space,
  characterizes closed subsets in the subspace topology as Z \cap A, and shows that
  a closed subset of a closed subspace is closed in the ambient space. Formulates
  and proves the Pasting Lemma for maps defined on finite closed covers, and applies
  it to prove the continuity of the maximum and minimum functions on R^2.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 12
    title: "The Closure of a Subset: Definition, Properties, and Examples"
    relationship: "Supplies the definition and properties of the closure, including cl(A) as the smallest closed set containing A."
  - lecture: 11
    title: "Closed Sets, Dual Axioms, and Preimages"
    relationship: "Supplies closed sets and the closed preimage criterion for continuity."
used_in:
  - lecture: 14
    title: "Metric Spaces, Cauchy–Schwarz, and the Metric Topology"
    relationship: "Metric topology and sequence limits build on closed sets, closures, and dense subsets."
  - lecture: 19
    title: "Path Connectedness and Path Components"
    relationship: "Supplies the Pasting Lemma for closed sets used to prove concatenation of paths is continuous."
notation:
  - symbol: "$\\text{dense}$"
    gloss: 'A subset $T \\subseteq X$ meeting every non-empty open set $U \\subseteq X$'
  - symbol: "$\\max(x, y)$"
    gloss: 'The maximum function $\\mathbb{R}^2 \\to \\mathbb{R}$, continuous by the Pasting Lemma'
  - symbol: "$\\min(x, y)$"
    gloss: 'The minimum function $\\mathbb{R}^2 \\to \\mathbb{R}$, continuous by the Pasting Lemma'
prev: lecture-12
next: lecture-14
---

# Lecture 13 — Dense Subsets, Subspace Closed Sets, and the Pasting Lemma

## Where we are

In [Lecture 12]({{ site.baseurl }}/point-set-topology/lecture-12/), we defined the closure $\overline{A}$ of an arbitrary subset $A \subseteq X$ and proved that it is the smallest closed set containing $A$. We computed closures of intervals and discs, and proved that a subset is closed if and only if it equals its closure ($A = \overline{A}$).

Here we complete our foundational study of closed sets and subspace topologies. We introduce the concept of a **dense subset**—a subset that intersects every non-empty open set—and prove that any subset $A$ is dense in its closure $\overline{A}$. We then examine transitivity of open and closed sets in subspaces: while arbitrary subspace open sets need not be open in the ambient space, an open subset of an open subspace is open, and a closed subset of a closed subspace is closed. Finally, we formulate and prove the **Pasting Lemma** (or Gluing Lemma), which guarantees that piecewise continuous functions defined on closed pieces that cover a space glue together into a continuous global function. We apply this lemma to establish the continuity of the $\max$ and $\min$ functions on $\mathbb{R}^2$.

---

## Dense subsets and closure

We begin by defining what it means for a subset to be dense in a topological space.

### Definition 13.1 (Dense subset) {#definition-13-1-dense-subset}

{% capture def131_content %}
Let $X$ be a topological space. A subset $T \subseteq X$ is said to be **dense** in $X$ if for every non-empty open set $U \subseteq X$ ($U \in \tau$, $U \ne \varnothing$), we have:
$$T \cap U \ne \varnothing.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 13.1 (Dense Subset)" content=def131_content %}

A fundamental link connects dense subsets to the closure operation.

### Proposition 13.2 ($A$ is dense in its closure) {#proposition-13-2-a-is-dense-in-its-closure}

{% capture prop132_content %}
Let $X$ be a topological space, let $A \subseteq X$ be an arbitrary subset, and let $\overline{A}$ denote its closure equipped with the subspace topology.
Then $A$ is **dense** in $\overline{A}$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 13.2 ($A$ is Dense in Its Closure)" content=prop132_content %}

{% capture prop132_proof %}
So let us prove this.

By the definition of denseness, we need to show that if $V \subseteq \overline{A}$ is a non-empty open subset in the subspace topology on $\overline{A}$, then $V \cap A$ is non-empty.

By the definition of the subspace topology ([Lecture 4]({{ site.baseurl }}/point-set-topology/lecture-04/#definition-4-3-subspace-topology)), this set $V$ is equal to $U \cap \overline{A}$ for some open subset $U \subseteq X$.
And as $V$ is non-empty, this implies there exists some $x \in V = U \cap \overline{A}$.
Therefore, $U$ is an open subset of $X$ containing $x$, and $x \in \overline{A}$.
So thus, by the definition of closure ([Definition 12.2]({{ site.baseurl }}/point-set-topology/lecture-12/#definition-12-2-closure-of-a-subset)), this implies that $U \cap A$ is non-empty (recall that $x \in \overline{A}$ if every open subset containing $x$ meets $A$).

Now notice that:
$$U \cap A = (U \cap \overline{A}) \cap A = V \cap A,$$
because $A \subseteq \overline{A}$.
Since $U \cap A \ne \varnothing$, this implies that $V \cap A$ is non-empty.

So thus, $V \cap A$ is non-empty, which shows that $A$ is dense in $\overline{A}$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 13.2" content=prop132_proof %}

{% include figure.html
   src="point-set-topology/lecture-13/dense-subset-intersection.svg"
   caption="Proof of Proposition 13.2: any non-empty subspace open set $V = U \cap \overline{A}$ contains a point $x \in \overline{A}$. Since $x \in \overline{A}$, the open set $U$ meets $A$, so $V \cap A = (U \cap \overline{A}) \cap A = U \cap A \ne \varnothing$."
   alt="Venn diagram showing space X, closure cl(A), subset A, open set U, and intersection V meeting A." %}

---

## Transitivity of openness and closedness in subspaces

We now consider how subspace open and closed sets behave when placed in larger ambient spaces.

### Proposition 13.3 (Open in open is open) {#proposition-13-3-open-in-open-is-open}

{% capture prop133_content %}
Let $X$ be a topological space, let $U \subseteq X$ be an open subset equipped with the subspace topology, and let $V \subseteq U$ be an open subset of $U$.
Then $V$ is an **open subset of $X$**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 13.3 (Open in Open is Open)" content=prop133_content %}

{% capture prop133_proof %}
The proof is easy.

By the definition of the subspace topology, there is an open subset $\widetilde{V} \subseteq X$ such that $V = U \cap \widetilde{V}$.
Both $U$ and $\widetilde{V}$ are open in $X$.
And as finite intersections of open sets are open (axiom (T2)), this implies that $V = U \cap \widetilde{V}$ is open in $X$.

So this completes the proof. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 13.3" content=prop133_proof %}

To state the dual result for closed sets, we first characterize closed subsets of a subspace.

### Lemma 13.4 (Closed subsets of a subspace) {#lemma-13-4-closed-subsets-of-a-subspace}

{% capture lem134_content %}
Let $X$ be a topological space and let $A \subseteq X$ be a subset equipped with the subspace topology.
Then the closed subsets of $A$ in the subspace topology are precisely the subsets of the form:
$$Z \cap A,$$
where $Z$ is a closed subset of $X$.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 13.4 (Closed Subsets of a Subspace)" content=lem134_content %}

{% capture lem134_proof %}
So let us prove this lemma.

The open subsets of $A$ in the subspace topology are precisely of the form $U \cap A$, where $U$ is open in $X$.
And the closed subsets of $A$ are the complements in $A$ of open subsets.
So thus, closed subsets of $A$ are precisely of the form $A \setminus (U \cap A)$ for some open set $U \subseteq X$.
Now a simple set-theoretic check shows that:
$$A \setminus (U \cap A) = A \cap (X \setminus U).$$
Let $Z = X \setminus U$. Because $U$ is open in $X$, $Z$ is a closed subset of $X$ ([Definition 11.1]({{ site.baseurl }}/point-set-topology/lecture-11/#definition-11-1-closed-subset)).
So thus, the closed subsets of $A$ are precisely of the form $Z \cap A$, where $Z$ is a closed subset of $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 13.4" content=lem134_proof %}

### Corollary 13.5 (Closed in closed is closed) {#corollary-13-5-closed-in-closed-is-closed}

{% capture cor135_content %}
Let $X$ be a topological space, let $Z \subseteq X$ be a closed subset equipped with the subspace topology, and let $Z_1 \subseteq Z$ be a closed subset of $Z$.
Then $Z_1$ is a **closed subset of $X$**.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 13.5 (Closed in Closed is Closed)" content=cor135_content %}

{% capture cor135_proof %}
The proof of this corollary is very similar.

By the previous lemma ([Lemma 13.4](#lemma-13-4-closed-subsets-of-a-subspace)), since $Z_1$ is closed in $Z$, this subset $Z_1$ can be written as $Z_1 = \widetilde{Z} \cap Z$, where $\widetilde{Z}$ is a closed subset of $X$.
And as the intersection of closed subsets is closed ([Lemma 11.2(3)]({{ site.baseurl }}/point-set-topology/lecture-11/#lemma-11-2-dual-axioms-for-closed-sets)), this implies that $Z_1$ is closed in $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 13.5" content=cor135_proof %}

---

## Testing closedness on a closed decomposition

We now show that whether a subset is closed can be tested locally on closed pieces covering the space.

### Proposition 13.6 (Closedness criterion on closed pieces) {#proposition-13-6-closedness-criterion-on-closed-pieces}

{% capture prop136_content %}
Let $X$ be a topological space, and suppose $X = Z_1 \cup Z_2$, where $Z_1$ and $Z_2$ are closed subsets of $X$ equipped with their subspace topologies.
A subset $Z \subseteq X$ is closed in $X$ if and only if
$$Z \cap Z_1 \text{ is closed in } Z_1 \qquad \text{and} \qquad Z \cap Z_2 \text{ is closed in } Z_2.$$
{% endcapture %}
{% include block.html type="proposition" title="Proposition 13.6 (Closedness Criterion on Closed Pieces)" content=prop136_content %}

{% capture prop136_proof %}
So let us prove this proposition first.

**$(\implies)$ If $Z$ is closed in $X$:**
Then by the lemma ([Lemma 13.4](#lemma-13-4-closed-subsets-of-a-subspace)), this implies $Z \cap Z_i$ is closed in $Z_i$ for $i = 1, 2$.

**$(\impliedby)$ Conversely, assume $Z \cap Z_i$ is closed in $Z_i$ for $i = 1, 2$:**
Then by the corollary above ([Corollary 13.5](#corollary-13-5-closed-in-closed-is-closed)), $Z \cap Z_1$ and $Z \cap Z_2$ both are closed in $X$.
Since $X = Z_1 \cup Z_2$, we can write $Z$ as:
$$Z = Z \cap X = Z \cap (Z_1 \cup Z_2) = (Z \cap Z_1) \cup (Z \cap Z_2).$$
And since finite unions of closed subspaces are closed ([Lemma 11.2(2)]({{ site.baseurl }}/point-set-topology/lecture-11/#lemma-11-2-dual-axioms-for-closed-sets)), this implies that $Z$ is closed in $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 13.6" content=prop136_proof %}

---

## The Pasting Lemma (Gluing Lemma)

We now arrive at the principal theorem of the lecture: gluing continuous maps along closed pieces.

### Theorem 13.7 (The Pasting Lemma) {#theorem-13-7-the-pasting-lemma}

{% capture thm137_content %}
Let $X$ and $Y$ be topological spaces. Suppose $X = A \cup B$, where $A$ and $B$ are closed subsets of $X$ equipped with the subspace topology.
Let $f : X \to Y$ be a map of sets such that:
1. The restriction $f|_A : A \to Y$ is continuous; and
2. The restriction $f|_B : B \to Y$ is continuous.

Then $f : X \to Y$ is **continuous**.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 13.7 (The Pasting Lemma)" content=thm137_content %}

{% capture thm137_proof %}
So proof.

To show that $f$ is continuous, it is enough to show that $f^{-1}(Z)$ is closed in $X$ for every closed subset $Z \subseteq Y$ ([Theorem 11.3]({{ site.baseurl }}/point-set-topology/lecture-11/#theorem-11-3-continuity-via-closed-preimages)).

Let $Z \subseteq Y$ be a closed subset.
By the previous proposition ([Proposition 13.6](#proposition-13-6-closedness-criterion-on-closed-pieces)), it is enough to show that $f^{-1}(Z) \cap A$ and $f^{-1}(Z) \cap B$ are closed in $A$ and $B$ respectively.

A simple set-theoretic check shows that:
$$f^{-1}(Z) \cap A = (f|_A)^{-1}(Z),$$
and similarly:
$$f^{-1}(Z) \cap B = (f|_B)^{-1}(Z).$$

As $f|_A$ and $f|_B$ are continuous and $Z$ is closed in $Y$, by Theorem 11.3 this implies that $(f|_A)^{-1}(Z)$ is closed in $A$, and similarly $(f|_B)^{-1}(Z)$ is closed in $B$.
So thus, $f^{-1}(Z) \cap A$ is closed in $A$ and $f^{-1}(Z) \cap B$ is closed in $B$.
By Proposition 13.6, this implies that $f^{-1}(Z)$ is closed in $X$.
This implies that $f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 13.7" content=thm137_proof %}

{% include figure.html
   src="point-set-topology/lecture-13/pasting-lemma-closed-pieces.svg"
   caption="The Pasting Lemma: when $X = A \cup B$ with $A, B$ closed, a map $f : X \to Y$ whose restrictions $f|_A$ and $f|_B$ are continuous pulls back any closed set $Z \subseteq Y$ to closed sets in $A$ and $B$, guaranteeing $f^{-1}(Z)$ is closed in $X$."
   alt="Diagram showing domain X partitioned into closed pieces A and B meeting at an interface, mapping to codomain Y with closed set Z." %}

---

## Application: continuity of $\max$ and $\min$ on $\mathbb{R}^2$

We use the Pasting Lemma to prove that the maximum and minimum functions on the real plane are continuous.

{% include figure.html
   src="point-set-topology/lecture-13/max-min-quadrants.svg"
   caption="Partitioning $\mathbb{R}^2$ along the diagonal $y = x$ into two closed half-planes $A = \lbrace x \ge y \rbrace$ and $B = \lbrace x \le y \rbrace$. On $A$, $\max(x, y) = x$ (coordinate projection $p_1$); on $B$, $\max(x, y) = y$ (coordinate projection $p_2$). The two formulas agree on $y = x$, ensuring continuity via the Pasting Lemma."
   alt="Coordinate plane divided by the diagonal line y = x into two closed half planes labeled A and B with formulas for max and min." %}

---

## Exercises

{% capture ex131_content %}
Define $f_1, f_2 : \mathbb{R}^2 \to \mathbb{R}$ by:
$$f_1(x, y) = \max(x, y), \qquad f_2(x, y) = \min(x, y).$$
Prove that both $f_1$ and $f_2$ are continuous maps.
{% endcapture %}
{% capture ex131_sol %}
Consider the two half-planes in $\mathbb{R}^2$:
$$A = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x \ge y \rbrace, \qquad B = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x \le y \rbrace.$$

1. **$A$ and $B$ are closed and cover $\mathbb{R}^2$:**
   Consider the difference map $D : \mathbb{R}^2 \to \mathbb{R}$, $D(x, y) = x - y$.
   By [Exercise 8.3]({{ site.baseurl }}/point-set-topology/lecture-08/#exercise-8-3-continuity-of-subtraction), $D$ is continuous.
   Notice that $A = D^{-1}\bigl([0, \infty)\bigr)$ and $B = D^{-1}\bigl((-\infty, 0]\bigr)$.
   The intervals $[0, \infty) = \mathbb{R} \setminus (-\infty, 0)$ and $(-\infty, 0] = \mathbb{R} \setminus (0, \infty)$ have open complements in $\mathbb{R}$, so they are closed subsets of $\mathbb{R}$.
   By [Theorem 11.3]({{ site.baseurl }}/point-set-topology/lecture-11/#theorem-11-3-continuity-via-closed-preimages), $A$ and $B$ are closed subsets of $\mathbb{R}^2$.
   For every $(x, y) \in \mathbb{R}^2$, either $x \ge y$ or $x \le y$ (or both). Hence $\mathbb{R}^2 = A \cup B$.

2. **Continuity of restrictions for $f_1 = \max$:**
   - On $A$, $x \ge y$, so $f_1(x, y) = \max(x, y) = x = p_1(x, y)$.
     Thus $f_1|_A = p_1|_A$. Since the first coordinate projection $p_1 : \mathbb{R}^2 \to \mathbb{R}$ is continuous ([Proposition 7.4]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-4-continuity-of-coordinate-projections)), its restriction $f_1|_A$ to the subspace $A$ is continuous ([Lemma 9.2]({{ site.baseurl }}/point-set-topology/lecture-09/#lemma-9-2-restriction-to-a-subspace)).
   - On $B$, $x \le y$, so $f_1(x, y) = \max(x, y) = y = p_2(x, y)$.
     Thus $f_1|_B = p_2|_B$, which is continuous by the same reasoning.
   - On the intersection $A \cap B = \lbrace (x, y) : x = y \rbrace$, both definitions give $f_1(x, x) = x$, so $f_1$ is well-defined.
   By Theorem 13.7 (The Pasting Lemma), $f_1(x, y) = \max(x, y)$ is continuous on $\mathbb{R}^2$.

3. **Continuity of $f_2 = \min$:**
   - On $A$, $f_2(x, y) = \min(x, y) = y = p_2(x, y)$, which is continuous.
   - On $B$, $f_2(x, y) = \min(x, y) = x = p_1(x, y)$, which is continuous.
   By Theorem 13.7, $f_2(x, y) = \min(x, y)$ is continuous on $\mathbb{R}^2$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 13.1 (Continuity of Maximum and Minimum)" content=ex131_content solution=ex131_sol %}

{% capture ex132_content %}
State and prove the generalized Pasting Lemma for a finite closed cover:
Let $X = \bigcup_{k=1}^m A_k$, where each $A_k$ is closed in $X$. If $f : X \to Y$ has continuous restrictions $f|_{A_k} : A_k \to Y$ for all $k = 1, \dots, m$, then $f$ is continuous.
{% endcapture %}
{% capture ex132_sol %}
We proceed by mathematical induction on the number of closed pieces $m$.
- **Base case $m = 1$:** Trivial, since $X = A_1$ and $f = f|_{A_1}$ is continuous.
- **Base case $m = 2$:** This is Theorem 13.7.
- **Inductive step:** Assume the statement holds for any union of $m-1$ closed pieces ($m \ge 3$).
  Let $X = \bigcup_{k=1}^m A_k$ with each $A_k$ closed.
  Define:
  $$A = \bigcup_{k=1}^{m-1} A_k, \qquad B = A_m.$$
  By Lemma 11.2(2), a finite union of closed sets is closed, so $A$ is closed in $X$, and $B = A_m$ is closed in $X$.
  Notice $X = A \cup B$.
  On $A$, the space is covered by the $m-1$ closed sets $A_1, \dots, A_{m-1}$.
  By the induction hypothesis, the restriction $f|_A : A \to Y$ is continuous.
  The restriction $f|_B = f|_{A_m} : B \to Y$ is continuous by hypothesis.
  Applying Theorem 13.7 to $X = A \cup B$ shows that $f$ is continuous on $X$.
By induction, the statement holds for all finite $m \ge 1$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 13.2 (Finite Closed Pasting Lemma)" content=ex132_content solution=ex132_sol %}

{% capture ex133_content %}
Prove that a subset $T \subseteq X$ is dense in $X$ if and only if its closure is the whole space:
$$\overline{T} = X.$$
{% endcapture %}
{% capture ex133_sol %}
($\implies$) Suppose $T$ is dense in $X$.
Let $x \in X$. We show $x \in \overline{T}$.
Let $U$ be any open neighbourhood of $x$ in $X$.
Since $x \in U$, $U$ is non-empty.
By Definition 13.1 of denseness, $T \cap U \ne \varnothing$.
By Definition 12.2 of closure, this means $x \in \overline{T}$.
Since this holds for every $x \in X$, we have $X \subseteq \overline{T}$.
Since $\overline{T} \subseteq X$ by definition, $\overline{T} = X$.

($\impliedby$) Suppose $\overline{T} = X$.
Let $U \subseteq X$ be a non-empty open set.
Since $U \ne \varnothing$, choose a point $x \in U$.
Since $\overline{T} = X$, we have $x \in \overline{T}$.
By Definition 12.2, since $U$ is an open neighbourhood of $x$, $T \cap U \ne \varnothing$.
Since this holds for every non-empty open set $U$, $T$ is dense in $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 13.3 (Equivalence of Denseness and Full Closure)" content=ex133_content solution=ex133_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Definition 13.1 (Dense Subset)](#definition-13-1-dense-subset): $T \subseteq X$ is dense iff $T \cap U \ne \varnothing$ for all non-empty open $U$.
- [Proposition 13.2 ($A$ Dense in Its Closure)](#proposition-13-2-a-is-dense-in-its-closure): For any subset $A \subseteq X$, $A$ is dense in the subspace $\overline{A}$.
- [Proposition 13.3 (Open in Open is Open)](#proposition-13-3-open-in-open-is-open): If $U \in \tau_X$ and $V \in \tau_U$, then $V \in \tau_X$.
- [Lemma 13.4 (Closed Subsets of a Subspace)](#lemma-13-4-closed-subsets-of-a-subspace): Subspace closed sets are precisely $Z \cap A$ with $Z$ closed in $X$.
- [Corollary 13.5 (Closed in Closed is Closed)](#corollary-13-5-closed-in-closed-is-closed): If $Z$ is closed in $X$ and $Z_1$ is closed in $Z$, then $Z_1$ is closed in $X$.
- [Proposition 13.6 (Closedness on Closed Pieces)](#proposition-13-6-closedness-criterion-on-closed-pieces): For $X = Z_1 \cup Z_2$ closed, $Z$ is closed iff $Z \cap Z_i$ is closed in $Z_i$.
- [Theorem 13.7 (The Pasting Lemma)](#theorem-13-7-the-pasting-lemma): If $X = A \cup B$ (closed) and $f|_A, f|_B$ are continuous, then $f$ is continuous.
- [Exercise 13.1 (Continuity of Maximum and Minimum)](#exercise-13-1-continuity-of-maximum-and-minimum): Proving $\max(x, y)$ and $\min(x, y)$ are continuous on $\mathbb{R}^2$ via the Pasting Lemma.
- [Exercise 13.2 (Finite Closed Pasting Lemma)](#exercise-13-2-finite-closed-pasting-lemma): Inductive extension to covers of $m$ closed sets.
- [Exercise 13.3 (Denseness and Full Closure)](#exercise-13-3-equivalence-of-denseness-and-full-closure): $T$ is dense in $X \iff \overline{T} = X$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §18.** Theorem 18.3 is the Pasting Lemma; Section 18 demonstrates the continuity of the maximum and minimum functions and piecewise linear paths.

**Morris, *Topology Without Tears*, Chapter 3 & Chapter 4.** Section 3.2 treats dense subsets; Section 4.3 presents the pasting lemma for closed sets.
