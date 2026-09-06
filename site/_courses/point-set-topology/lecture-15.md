---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 15
title: "Sequential Criteria for Closed Sets and Continuity, and Introduction to Connectedness"
coverage: >
  Establishes the sequential criterion for closed sets in metric spaces (closed iff
  closed under sequence limits) and the sequential criterion for continuity between
  metric spaces. Concludes Part II and initiates Part III of the course by motivating
  the classification of topological spaces up to homeomorphism. Defines disconnected
  and connected spaces, formulates key motivating questions, and proves that a space
  containing a dense connected subset is connected, concluding that the closure of a
  connected subset is connected.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 14
    title: "Metric Spaces, the Euclidean Metric, and Sequence Convergence"
    relationship: "Supplies metric topologies, open balls, and the sequential criterion for closure."
  - lecture: 13
    title: "Dense Subsets, Subspace Closed Sets, and the Pasting Lemma"
    relationship: "Supplies dense subsets and the theorem that A is dense in cl(A)."
  - lecture: 12
    title: "The Closure of a Subset: Definition, Properties, and Examples"
    relationship: "Supplies the characterization A is closed iff A = cl(A)."
  - lecture: 11
    title: "Closed Sets, Dual Axioms, and Preimages"
    relationship: "Supplies continuity via closed preimages."
  - lecture: 10
    title: "The Standard Topology on R^n, Stereographic Projection, and Homeomorphisms"
    relationship: "Supplies homeomorphisms as topological equivalence."
used_in:
  - lecture: 16
    title: "Connectedness of the Unit Interval and Subspaces of the Real Line"
    relationship: "Supplies the definition of connectedness and closure theorem used to prove [0,1] and R are connected."
notation:
  - symbol: "$X = U \\sqcup V$"
    gloss: 'A disconnection of a space $X$ into disjoint, non-empty open subsets'
  - symbol: "$\\text{connected}$"
    gloss: 'A topological space that cannot be partitioned into two disjoint non-empty open sets'
prev: lecture-14
next: lecture-16
---

# Lecture 15 — Sequential Criteria for Closed Sets and Continuity, and Introduction to Connectedness

## Where we are

This lecture marks a major structural turning point in the course. It concludes **Part II (Continuous Maps and Metric Spaces, Lectures 7–15)** and pivots directly into **Part III (Connectedness, Lectures 16–22)**.

In the first half, we complete our investigation of metric spaces from [Lecture 14]({{ site.baseurl }}/point-set-topology/lecture-14/). Using the sequential characterization of closure, we establish two fundamental criteria: a subset of a metric space is closed if and only if it contains the limits of all its convergent sequences, and a map between metric spaces is continuous if and only if it preserves limits of convergent sequences.

In the second half, we turn to the grand objective of topology: classifying topological spaces up to homeomorphism. Two spaces that are homeomorphic cannot be distinguished by any topological property. To prove that two spaces (such as the connected interval $[0, 1]$ and a disjoint union of intervals) are not homeomorphic, we need **topological invariants**. We introduce the first such invariant—**connectedness**—and prove that any space possessing a dense connected subset is connected, which immediately implies that the closure of a connected subset is connected.

---

## Sequential criteria in metric spaces

In [Lecture 14]({{ site.baseurl }}/point-set-topology/lecture-14/#lemma-14-6-sequential-characterization-of-closure), we proved Lemma 14.6: in any metric space $(X, d)$, a point $x$ belongs to the closure $\overline{A}$ if and only if there exists a sequence $(x_n)_{n \ge 1}$ in $A$ such that $x_n \to x$. We now apply this result to characterize closed sets and continuous maps.

### Lemma 15.1 (Sequential criterion for closed subsets) {#lemma-15-1-sequential-criterion-closed-subsets}

{% capture lem151_content %}
Let $(X, d)$ be a metric space, and let $A \subseteq X$ be a subset. Then $A$ is closed if and only if it has the following property:
whenever $(x_n)_{n \ge 1}$ is a sequence of points in $A$ and $x_n \to x$ in $X$, the limit point $x$ also belongs to $A$.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 15.1 (Sequential Criterion for Closed Subsets)" content=lem151_content %}

{% capture lem151_proof %}
Recall we had proved in [Lecture 12]({{ site.baseurl }}/point-set-topology/lecture-12/#proposition-12-4-characterization-of-closed-sets-via-closure) that a subset $A$ in a topological space is closed if and only if $A = \overline{A}$. So we will use this criterion: it is enough to show that $A = \overline{A}$ if and only if whenever $x_n \in A$ and $x_n \to x$, then $x \in A$.

**($\implies$) First, assume that $A = \overline{A}$:**
Then we have to show that the set $A$ has this property. If $(x_n)_{n \ge 1}$ is a sequence in $A$ and $x_n \to x$, then by Lemma 14.6 ([Lecture 14]({{ site.baseurl }}/point-set-topology/lecture-14/#lemma-14-6-sequential-characterization-of-closure)), $x \in \overline{A}$. Since we are assuming that $A = \overline{A}$, this implies that $x \in A$. Thus $A$ has this property. ✓

**($\impliedby$) Conversely, suppose $A$ has this property:**
That is, every time we have $x_n \in A$ and $x_n \to x$, then $x \in A$. We assume that $A$ has this property, and we want to show that $A = \overline{A}$. It is obvious that $A \subseteq \overline{A}$, so we just have to prove the converse: let $x \in \overline{A}$.

By Lemma 14.6 proved in the previous lecture, there is a sequence $(x_n)_{n \ge 1}$ in $A$ such that $x_n \to x$. By the property that $A$ has, every time we have such a sequence, $x$ belongs to $A$. So we have a sequence $(x_n)$ in $A$ with $x_n \to x$, so we have $x \in A$.

This implies that $\overline{A} \subseteq A$. Thus $A = \overline{A}$. So therefore, $A$ is closed. ✓ $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 15.1" content=lem151_proof %}

We next characterize continuity of maps between metric spaces in terms of sequences.

### Theorem 15.2 (Sequential criterion for continuity) {#theorem-15-2-sequential-criterion-continuity}

{% capture thm152_content %}
Let $(X, d_X)$ and $(Y, d_Y)$ be metric spaces, and let $f \colon X \to Y$ be a map. Then $f$ is continuous if and only if for every sequence $(x_n)_{n \ge 1}$ in $X$ converging to a point $x \in X$, the sequence $\bigl(f(x_n)\bigr)_{n \ge 1}$ in $Y$ converges to $f(x)$:
$$x_n \to x \implies f(x_n) \to f(x).$$
{% endcapture %}
{% include block.html type="theorem" title="Theorem 15.2 (Sequential Criterion for Continuity)" content=thm152_content %}

{% capture thm152_proof %}
We prove both directions.

**($\implies$) First, assume that $f$ is continuous:**
Let $(x_n)_{n \ge 1}$ be a sequence in $X$ converging to $x$. For $\varepsilon > 0$, consider the open ball $B_\varepsilon\bigl(f(x)\bigr)$ around $f(x)$ in $Y$.
Since $f$ is continuous, the preimage:
$$f^{-1}\bigl(B_\varepsilon(f(x))\bigr)$$
is an open subset of $X$ ([Lecture 7]({{ site.baseurl }}/point-set-topology/lecture-07/#definition-7-1-continuous-map)).
And moreover, since $x$ belongs to this open preimage, by Proposition 14.4 ([Lecture 14]({{ site.baseurl }}/point-set-topology/lecture-14/#proposition-14-4-characterization-of-open-sets)) there is $\delta > 0$ such that the ball of radius $\delta$ around $x$ is completely contained inside the preimage:
$$B_\delta(x) \subseteq f^{-1}\bigl(B_\varepsilon(f(x))\bigr).$$
As $x_n \to x$, by the definition of convergence there exists an integer $N \in \mathbb{N}$ such that for all $n \ge N$, the points $x_n$ are in this ball:
$$x_n \in B_\delta(x).$$
Applying $f$, this implies that for all $n \ge N$:
$$f(x_n) \in B_\varepsilon\bigl(f(x)\bigr).$$
And by the definition of convergence, this implies that $f(x_n) \to f(x)$. So this proves one part of the theorem. ✓

**($\impliedby$) Conversely, suppose $f$ satisfies this property:**
To prove the converse means we are given that $f$ takes convergent sequences to convergent sequences, and we have to show that $f$ is continuous.
To show that $f$ is continuous, it suffices to show that the inverse image of a closed subset is closed: let $Z \subseteq Y$ be closed.
And to show that $f^{-1}(Z)$ is closed, we will show that $f^{-1}(Z)$ is equal to its closure.

Let $x \in \overline{f^{-1}(Z)}$.
This implies that there is a sequence $(x_n)_{n \ge 1}$ in $f^{-1}(Z)$ converging to $x$.
Now $x_n \in f^{-1}(Z)$ implies that $f(x_n) \in Z$.
Moreover, since $f$ has the property that it takes convergent sequences to convergent sequences, as $x_n \to x$ this implies:
$$f(x_n) \to f(x).$$
Now as $Z$ is closed, $f(x_n) \in Z$, and $f(x_n) \to f(x)$, this implies by Lemma 15.1 that:
$$f(x) \in Z.$$
Thus $x \in f^{-1}(Z)$.
So we started with the point $x \in \overline{f^{-1}(Z)}$, and we proved that $x \in f^{-1}(Z)$.
This implies that $f^{-1}(Z) = \overline{f^{-1}(Z)}$.
So this implies that $f^{-1}(Z)$ is closed, which implies that $f$ is continuous. ✓ $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 15.2" content=thm152_proof %}

{% include figure.html
   src="point-set-topology/lecture-15/sequential-continuity-delta-epsilon.svg"
   caption="Sequential continuity: the preimage of the $\varepsilon$-ball $B_\varepsilon(f(x))$ contains an open ball $B_\delta(x)$ around $x$. Since $x_n \to x$, all terms for $n \ge N$ lie in $B_\delta(x)$, forcing their images $f(x_n)$ into $B_\varepsilon(f(x))$."
   alt="Two spaces X and Y with map f showing a delta ball around x mapping into an epsilon ball around f(x)." %}

---

## Part III: The classification problem and connectedness

Having studied open sets, continuous maps, and metric spaces, we now enter **Part III** of the course: the study of topological properties.

Recall from [Lecture 10]({{ site.baseurl }}/point-set-topology/lecture-10/#definition-10-3-homeomorphism) that two topological spaces $X$ and $Y$ are **homeomorphic** ($X \cong Y$) if there exists a continuous bijection $f \colon X \to Y$ whose inverse $f^{-1} \colon Y \to X$ is also continuous. Homeomorphic spaces are topologically indistinguishable—they share every intrinsic topological property.

A central problem of topology is the **classification problem**: given two topological spaces, are they homeomorphic?
For example, consider the open unit interval $(0, 1)$ and the disjoint union of two open intervals $(0, 1) \sqcup (2, 3)$. Both are subsets of $\mathbb{R}$ with the subspace topology, and both have the cardinality of the continuum. Are they homeomorphic?

Intuitively, $(0, 1)$ consists of a single undivided piece, whereas $(0, 1) \sqcup (2, 3)$ is broken into two separate components. To turn this geometric intuition into a rigorous proof that no homeomorphism exists between them, we define the property of **connectedness**.

### Definition 15.3 (Disconnected and connected spaces) {#definition-15-3-connected-and-disconnected-spaces}

{% capture def153_content %}
Let $X$ be a topological space.
1. The space $X$ is said to be **disconnected** if there exist non-empty open subsets $U, V \subseteq X$ such that:
   $$U \cap V = \varnothing \quad \text{and} \quad X = U \cup V.$$
   Such a pair $\{U, V\}$ is called a **disconnection** (or separation) of $X$.
2. The space $X$ is said to be **connected** if it is not disconnected—that is, if it is impossible to write $X$ as a union of two disjoint, non-empty open subsets.
{% endcapture %}
{% include block.html type="definition" title="Definition 15.3 (Disconnected and Connected Spaces)" content=def153_content %}

{% capture supp_clopen %}
**Equivalent characterization via clopen sets:**
Suppose $X = U \cup V$ with $U, V$ disjoint and open. Then $V = X \setminus U$, so $U$ is both open and closed (a **clopen** set).
Conversely, if $U \subseteq X$ is a non-empty proper subset that is clopen, then $V = X \setminus U$ is non-empty, open, disjoint from $U$, and $X = U \cup V$.
Therefore, a space $X$ is connected if and only if the only clopen subsets of $X$ are $\varnothing$ and $X$.
{% endcapture %}
{% include block.html type="supplement" title="Connectedness via Clopen Subsets" content=supp_clopen %}

{% include figure.html
   src="point-set-topology/lecture-15/connected-vs-disconnected-space.svg"
   caption="Definition 15.3: a disconnected space (left) partitions into two disjoint non-empty open sets $U$ and $V$. A connected space (right) cannot be divided into two disjoint non-empty open pieces."
   alt="Comparison of a disconnected space consisting of two separate open regions U and V against a connected space." %}

The lecturer outlines several motivating questions to guide our upcoming lectures:
1. Is $\mathbb{R}$ connected with the standard topology?
2. Is $\mathbb{R}^n$ connected?
3. What are the connected subspaces of $\mathbb{R}$?
4. If $X$ and $Y$ are connected, is the product space $X \times Y$ connected?
5. Which matrix groups ($GL_n(\mathbb{R})$, $SL_n(\mathbb{R})$, $O(n)$, $SO(n)$, $GL_n(\mathbb{C})$, $SL_n(\mathbb{C})$, $U(n)$) are connected?

---

## Dense subsets and connectedness of the closure

To begin answering these questions, we establish two fundamental preservation results.

### Proposition 15.4 (Space with dense connected subset is connected) {#proposition-15-4-dense-connected-subset}

{% capture prop154_content %}
Let $X$ be a topological space, and let $U \subseteq X$ be a dense subset.
If $U$ (equipped with the subspace topology) is **connected**, then $X$ is **connected**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 15.4 (Space with Dense Connected Subset is Connected)" content=prop154_content %}

{% capture prop154_proof %}
So let us prove this. Let us assume that $X$ is disconnected and arrive at a contradiction.

As $X$ is disconnected, there are non-empty open sets $U_1$ and $U_2$ which are disjoint, such that we can write $X$ as a disjoint union:
$$X = U_1 \cup U_2, \quad \text{with } U_1 \cap U_2 = \varnothing.$$
So now we simply intersect both sides with $U$ to get:
$$U = (U \cap U_1) \cup (U \cap U_2).$$
Notice that:
1. Since $U_1$ and $U_2$ are disjoint, the intersections $(U \cap U_1)$ and $(U \cap U_2)$ are disjoint:
   $$(U \cap U_1) \cap (U \cap U_2) = U \cap (U_1 \cap U_2) = \varnothing.$$
2. By the definition of the subspace topology ([Lecture 4]({{ site.baseurl }}/point-set-topology/lecture-04/#definition-4-3-subspace-topology)), both $U \cap U_1$ and $U \cap U_2$ are open subsets of $U$.
3. So as $U$ is dense in $X$, this implies that $U \cap U_1$ is non-empty, and $U \cap U_2$ is non-empty:
   $$U \cap U_1 \ne \varnothing \quad \text{and} \quad U \cap U_2 \ne \varnothing.$$

But this shows that $U$ is disconnected, which is a contradiction. So this implies that our hypothesis was wrong, so that means $X$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 15.4" content=prop154_proof %}

{% include figure.html
   src="point-set-topology/lecture-15/dense-connected-subset-intersection.svg"
   caption="Proposition 15.4: if $X$ were disconnected into disjoint open sets $U_1$ and $U_2$, any dense subset $U$ would meet both $U_1$ and $U_2$, partitioning $U$ into two non-empty open pieces and contradicting its connectedness."
   alt="A space partitioned into U1 and U2 intersected by a dense connected subset U spanning across both pieces." %}

As an immediate corollary, the closure of any connected set is connected.

### Corollary 15.5 (Closure of a connected subspace is connected) {#corollary-15-5-closure-of-connected-subspace}

{% capture cor155_content %}
Let $X$ be a topological space, and let $A \subseteq X$ be a subspace.
If $A$ is connected, then its closure $\overline{A}$ (equipped with the subspace topology) is connected.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 15.5 (Closure of a Connected Subspace is Connected)" content=cor155_content %}

{% capture cor155_proof %}
Recall that when we talk about $A$ and $\overline{A}$, all these are subsets of $X$, and we are giving these the subspace topology.
Recall that we had proved in [Lecture 13]({{ site.baseurl }}/point-set-topology/lecture-13/#proposition-13-2-a-is-dense-in-its-closure) (Proposition 13.2) that $A$ is dense in $\overline{A}$.
So applying the previous proposition implies that $\overline{A}$ is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 15.5" content=cor155_proof %}

---

## At a glance

- [Lemma 15.1 (Sequential Criterion for Closed Subsets)](#lemma-15-1-sequential-criterion-closed-subsets): In a metric space, $A$ is closed if and only if for every sequence $(x_n) \subseteq A$ with $x_n \to x$, the limit $x$ lies in $A$.
- [Theorem 15.2 (Sequential Criterion for Continuity)](#theorem-15-2-sequential-criterion-continuity): A map $f \colon X \to Y$ between metric spaces is continuous if and only if $x_n \to x \implies f(x_n) \to f(x)$ for all sequences in $X$.
- [Definition 15.3 (Disconnected and Connected Spaces)](#definition-15-3-connected-and-disconnected-spaces): $X$ is disconnected if $X = U \cup V$ for non-empty, disjoint open subsets $U, V$. Otherwise, $X$ is connected (equivalently, the only clopen subsets are $\varnothing$ and $X$).
- [Proposition 15.4 (Space with Dense Connected Subset is Connected)](#proposition-15-4-dense-connected-subset): If $U \subseteq X$ is dense and connected in the subspace topology, then $X$ is connected.
- [Corollary 15.5 (Closure of a Connected Subspace is Connected)](#corollary-15-5-closure-of-connected-subspace): If $A \subseteq X$ is connected, then its closure $\overline{A}$ is connected.
