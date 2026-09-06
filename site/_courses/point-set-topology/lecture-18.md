---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 18
title: "Connected Components of a Topological Space"
coverage: >
  Defines the equivalence relation of connectedness on any topological space and
  partitions the space into connected components. Proves the three fundamental
  properties of connected components: every connected subspace lies in a single
  component, each component is connected (hence maximal connected), and each
  component is closed in the ambient space, correcting a verbal slip regarding the
  connectedness of X. Examines the connected components of Q, showing they are
  singletons, and establishes the criterion that a space is connected if and only
  if it has exactly one connected component.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 1
depends_on:
  - lecture: 17
    title: "Connectedness of Product Spaces, the Union Lemma, and Spheres"
    relationship: "Supplies the Union Lemma used to prove transitivity of the component relation and connectedness of components."
  - lecture: 15
    title: "Sequential Criteria for Closed Sets and Continuity, and Introduction to Connectedness"
    relationship: "Supplies the theorem that the closure of a connected subspace is connected."
used_in:
  - lecture: 19
    title: "Path Connectedness and Path Components"
    relationship: "Supplies the component theory framework that path components and path connectedness parallel and refine."
notation:
  - symbol: "$x \\sim y$"
    gloss: 'Equivalence relation: there exists a connected subspace $T \\subseteq X$ with $x, y \\in T$'
  - symbol: "$X_i$"
    gloss: 'A connected component of $X$, an equivalence class under $\\sim$'
  - symbol: "$X = \\bigsqcup_{i \\in I} X_i$"
    gloss: 'Partition of $X$ into its maximal connected, closed components'
prev: lecture-17
next: lecture-19
---

# Lecture 18 — Connected Components of a Topological Space

## Where we are

In [Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/) and [Lecture 17]({{ site.baseurl }}/point-set-topology/lecture-17/), we investigated the properties of connected spaces, proving that intervals, real spaces $\mathbb{R}^n$, products $X \times Y$, and spheres $S^n$ are connected. We also established the Union Lemma: any union of connected subspaces that share a common point is connected.

When a topological space $X$ is disconnected, a natural question arises: what are its maximal connected constituent pieces? In this lecture, we introduce the concept of **connected components**. We define an equivalence relation on the points of any topological space $X$, whereby two points are equivalent if they lie in a common connected subspace. We prove that the resulting equivalence classes—the connected components—partition $X$, that every connected subspace of $X$ lies entirely within a single component, that each component is connected (and therefore maximal connected), and that every component is closed in $X$. Finally, we show that the connected components of the rational numbers $\mathbb{Q}$ are individual singletons.

---

## The equivalence relation of connectedness

We define an equivalence relation on the points of an arbitrary topological space.

### Definition 18.1 (Connectedness equivalence relation) {#definition-18-1-connectedness-equivalence-relation}

{% capture def181_content %}
Let $X$ be a topological space. For points $x, y \in X$, we define the relation:
$$x \sim y \iff \text{there exists a connected subspace } T \subseteq X \text{ such that } x, y \in T.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 18.1 (Connectedness Equivalence Relation)" content=def181_content %}

### Proposition 18.2 ($\sim$ is an equivalence relation) {#proposition-18-2-equivalence-relation}

{% capture prop182_content %}
The relation $\sim$ defined in Definition 18.1 is an **equivalence relation** on $X$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 18.2 ($\sim$ is an Equivalence Relation)" content=prop182_content %}

{% capture prop182_proof %}
So let us check that this defines an equivalence relation on $X$. There are three things which we need to check:

1. **First, we need to check that $x \sim x$ for all $x \in X$:**
   This is clear by taking $T = \{x\}$ to be just the singleton set. Any singleton set $\{x\}$ is connected, because for a set to be disconnected it has to have at least two points (we cannot write a singleton set as a disjoint union of non-empty open subsets). Since $x, x \in \{x\}$, it follows that $x \sim x$. ✓
2. **The second point we need to check is if $x \sim y$, then $y \sim x$:**
   This is also clear: if $T$ is a connected subset which contains $x$ and $y$, then it obviously contains $y$ and $x$ again. So $y \sim x$. ✓
3. **Three, if $x \sim y$ and $y \sim z$, then $x \sim z$:**
   To show this, recall that in the previous lecture ([Lecture 17]({{ site.baseurl }}/point-set-topology/lecture-17/#lemma-17-4-the-union-lemma), Lemma 17.4) we proved that if $T_1$ and $T_2$ are connected subsets of $X$ such that $T_1 \cap T_2 \ne \varnothing$, then the union $T_1 \cup T_2$ is connected.
   Now since $x \sim y$, there exists a connected subset $T_1$ such that $x, y \in T_1$. Similarly, since $y \sim z$, there is a connected subset $T_2$ such that $y, z \in T_2$.
   Then $y \in T_1 \cap T_2$, and so the intersection is non-empty.
   And thus $T_1 \cup T_2$ is connected and contains $x$ and $z$.
   So thus, $x \sim z$. ✓

So this shows that $\sim$ is an equivalence relation. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 18.2" content=prop182_proof %}

---

## Connected components and their properties

As with any equivalence relation, $\sim$ partitions $X$ into disjoint equivalence classes.

### Definition 18.3 (Connected components) {#definition-18-3-connected-components}

{% capture def183_content %}
Let $X$ be a topological space. The equivalence classes of the relation $\sim$ on $X$ are called the **connected components** of $X$.
The space $X$ decomposes into the disjoint union of its connected components:
$$X = \bigsqcup_{i \in I} X_i.$$
Two points $x, y \in X$ belong to the same connected component $X_i$ if and only if $x \sim y$.
{% endcapture %}
{% include block.html type="definition" title="Definition 18.3 (Connected Components)" content=def183_content %}

We now establish the three fundamental properties of connected components.

### Proposition 18.4 (Properties of connected components) {#proposition-18-4-properties-connected-components}

{% capture prop184_content %}
Let $X$ be a topological space, and let $X = \bigsqcup_{i \in I} X_i$ be its decomposition into connected components.
1. Every connected subspace $T \subseteq X$ is contained in a single connected component $X_i$ for some $i \in I$.
2. Each connected component $X_i$ is **connected** (and hence is a maximal connected subspace of $X$).
3. Each connected component $X_i$ is **closed** in $X$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 18.4 (Properties of Connected Components)" content=prop184_content %}

{% capture prop184_proof %}
So let us prove this proposition.

**Proof of (1): Every connected subspace lies in a single component.**
We will prove the first point by contradiction: let us assume that a connected subspace meets two distinct components, say $T \cap X_i \ne \varnothing$ and $T \cap X_j \ne \varnothing$ where $i \ne j$.
Choose points:
$$t \in T \cap X_i \quad \text{and} \quad s \in T \cap X_j.$$
Then as $s, t \in T$ and $T$ is connected, by the definition of the equivalence relation this implies:
$$s \sim t.$$
But then this implies that the equivalence class of $t$, which is $X_i$, is equal to the equivalence class of $s$, which is $X_j$:
$$X_i = X_j.$$
And this is a contradiction, because $X_i \ne X_j$.
So therefore, given any connected subspace, it can be contained only in one $X_i$.
So this proves (1). ✓

**Proof of (2): Each component $X_i$ is connected.**
Next, let us prove (2). Let $X_i$ be an equivalence class, and let $x \in X_i$: we fix this point $x$.
Then for any $y \in X_i$, since $x$ and $y$ are both in $X_i$, as $x \sim y$ there is a connected subspace $T_y \subseteq X$ such that $x, y \in T_y$.
Clearly from point (1), it follows that $T_y \subseteq X_i$.
So thus, we can write $X_i$ as:
$$X_i = \bigcup_{y \in X_i} T_y.$$
(Indeed, this inclusion is obvious because for each $y \in X_i$, the subset $T_y \subseteq X_i$, so the union is contained in $X_i$; and conversely for every $y \in X_i$, $T_y$ contains $y$).
Now consider the following lemma: let $T_y$ be a family of connected subsets of $X$, and suppose their intersection is non-empty; then their union is connected.
*(Proof: suppose $\bigcup T_y$ were disconnected into disjoint non-empty open subsets $U$ and $V$. The common point $x \in \bigcap T_y$ must lie in one of them, say $x \in U$. For every $y$, $T_y$ is connected and contains $x \in U$, forcing $T_y \subseteq U$, and hence $\bigcup T_y \subseteq U$, leaving $V = \varnothing$, a contradiction).*
Applying this to our situation, each $T_y$ is connected, and the intersection of all these $T_y$ at least contains $x$, so the intersection is non-empty:
$$x \in \bigcap_{y \in X_i} T_y \ne \varnothing.$$
So this implies that $X_i$ is connected.
So this proves (2). ✓

**Proof of (3): Each component $X_i$ is closed in $X$.**
And finally, let us prove (3).
As $X_i$ is connected, recall the corollary from [Lecture 15]({{ site.baseurl }}/point-set-topology/lecture-15/#corollary-15-5-closure-of-connected-subspace) that if a subspace is connected, its closure is connected.
This implies that $\overline{X_i}$ is connected.
Now by part (1), each connected subspace is contained in a unique component $X_j$:
$$\overline{X_i} \subseteq X_j.$$
Thus this $X_j$ has to be $X_i$ because $X_i \subseteq \overline{X_i}$.
Thus $\overline{X_i} \subseteq X_i$, which implies that:
$$X_i = \overline{X_i}.$$
So this implies that $X_i$ is closed.
This completes the proof of the proposition. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 18.4" content=prop184_proof %}

{% capture cor184_note %}
**Defect registered in `context/known-defects.md` (Slip):**
In sentence 142 of the transcript, the proof of part (3) begins: *"as $X$ is connected, as $X_i$ is connected..."*
The first clause is a slip; only $X_i$ is assumed connected. The ambient space $X$ is arbitrary and need not be connected. The slip has been removed in the proof above.
{% endcapture %}
{% include block.html type="correction" id="correction-note-slip-connected-hypothesis" title="Correction Note: Spurious Connectedness Hypothesis on $X$" content=cor184_note %}

{% include figure.html
   src="point-set-topology/lecture-18/connected-components-partition.svg"
   caption="Proposition 18.4 (1): a space $X$ decomposes into disjoint closed connected components $X_1, X_2, X_3$. Any connected subspace $T$ is trapped entirely within a single component $X_1$."
   alt="Partition of space X into components X1, X2, X3, with a connected subset T lying entirely inside X1." %}

{% include figure.html
   src="point-set-topology/lecture-18/component-as-star-union.svg"
   caption="Proposition 18.4 (2): component $X_i$ is a star-like union of connected sets $T_y$ joining fixed point $x$ to every other point $y \in X_i$. Since all $T_y$ share $x$, their union $X_i$ is connected."
   alt="Diagram of a component Xi formed as the union of connected subsets Ty meeting at a common point x." %}

---

## The connected components of the rational numbers

We examine a space whose connected components are as small as possible.

### Example 1 (Connected components of $\mathbb{Q}$) {#example-1-connected-components-of-q}

{% capture ex1_content %}
Let $\mathbb{Q} \subseteq \mathbb{R}$ have the subspace topology from the standard topology on $\mathbb{R}$.
What are the connected components of $\mathbb{Q}$?

Before that, note that given any $a \in \mathbb{Q}$, the singleton subset $\{a\}$ is connected.
So the question is: what is the maximal connected subset which contains this singleton $\{a\}$? That would be the connected component containing $a$.

We claim that the connected component containing $a$ is just the singleton set $\{a\}$.
Why is that? So let us see this:
Write $\mathbb{Q} = \bigsqcup_{i \in I} X_i$ as a disjoint union of connected components $X_i$.
Pick $a \in X_i$, and our claim is that $X_i = \{a\}$.

If not, suppose $b$ also belongs to $X_i$, and $b \ne a$.
Suppose without loss of generality that $b > a$.
Then we can choose an irrational number $c \in \mathbb{R} \setminus \mathbb{Q}$ strictly between $a$ and $b$:
$$a < c < b.$$
Now $c$ is not in $\mathbb{Q}$, and $X_i \subseteq \mathbb{Q}$, therefore $c$ is not in $X_i$.
So $X_i$ does not contain $c$, and so we can write $X_i$ as a disjoint union of open subsets:
$$X_i = \bigl(X_i \cap (-\infty, c)\bigr) \cup \bigl(X_i \cap (c, \infty)\bigr).$$
Notice that:
1. Both $(-\infty, c)$ and $(c, \infty)$ are open in $\mathbb{R}$, so their intersections with $X_i$ are open in the subspace topology on $X_i$.
2. The two pieces are disjoint.
3. Both these are non-empty because the first contains $a$ and the second contains $b$.

This contradicts the connectedness of $X_i$ (Proposition 18.4 (2)).
So thus, $X_i$ is forced to be a single point:
$$X_i = \{a\}.$$
Therefore, all the connected components of $\mathbb{Q}$ are just the singletons $\{q\}$ for each $q \in \mathbb{Q}$. ✓
{% endcapture %}
{% include block.html type="example" title="Example 1 (Connected Components of $\mathbb{Q}$)" content=ex1_content %}

{% include figure.html
   src="point-set-topology/lecture-18/rational-components-irrational-split.svg"
   caption="Example 1: any two distinct rationals $a, b \in \mathbb{Q}$ are separated by an irrational $c \notin \mathbb{Q}$, splitting the subspace into two disjoint open pieces and forcing every connected component of $\mathbb{Q}$ to be a singleton."
   alt="Number line showing rationals a and b split by an irrational number c." %}

### Proposition 18.5 (Criterion for connectedness via components) {#proposition-18-5-criterion-connectedness-components}

{% capture prop185_content %}
A topological space $X$ is **connected** if and only if it has **only one connected component** ($X = X_1$).
{% endcapture %}
{% include block.html type="proposition" title="Proposition 18.5 (Criterion for Connectedness via Components)" content=prop185_content %}

{% capture prop185_proof %}
This is obvious:
because if $X$ is connected, then given any two points $x$ and $y$, the subset $T$ can be taken equal to $X$, so there is just one equivalence class in the decomposition.
And conversely, if there is just one equivalence class, then that has to be $X$, and therefore $X$ is connected because each equivalence class is connected (Proposition 18.4 (2)). $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 18.5" content=prop185_proof %}

---

## At a glance

- [Definition 18.1 (Connectedness Equivalence Relation)](#definition-18-1-connectedness-equivalence-relation): $x \sim y$ if there exists a connected subspace $T \subseteq X$ with $x, y \in T$.
- [Proposition 18.2 ($\sim$ is an Equivalence Relation)](#proposition-18-2-equivalence-relation): Reflexive via singletons, symmetric by definition, and transitive via the Union Lemma.
- [Definition 18.3 (Connected Components)](#definition-18-3-connected-components): Equivalence classes of $\sim$, partitioning $X = \bigsqcup X_i$.
- [Proposition 18.4 (Properties of Connected Components)](#proposition-18-4-properties-connected-components): (1) Any connected subspace lies in a single component; (2) Each component is connected (maximal connected); (3) Each component is closed ($X_i = \overline{X_i}$).
- [Correction Note: Spurious Connectedness Hypothesis on $X$](#correction-note-slip-connected-hypothesis): Corrects transcript slip opening the proof of closedness with "as $X$ is connected".
- [Example 1 (Connected Components of $\mathbb{Q}$)](#example-1-connected-components-of-q): Every connected component of $\mathbb{Q}$ is a single point, split by irrationals.
- [Proposition 18.5 (Criterion for Connectedness via Components)](#proposition-18-5-criterion-connectedness-components): $X$ is connected if and only if it consists of a single connected component.
