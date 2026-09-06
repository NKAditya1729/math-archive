---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 9
title: "Properties of Continuous Maps and Algebraic Combinations"
coverage: >
  Proves general properties of continuous maps: composition of continuous maps is
  continuous, restriction to a subspace is continuous, and corestriction to a
  subspace containing the image is continuous. Formulates and proves the universal
  property of the product topology: a map into a Cartesian product is continuous
  if and only if each coordinate component is continuous, observing that this
  property fails for the box topology. Establishes that the sum f+g, product fg,
  and quotient f/g of continuous real-valued functions are continuous, demonstrating
  that the space of continuous real-valued functions forms a ring.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 8
    title: "The Basis Criterion for Continuity and Continuous Operations"
    relationship: "Supplies the basis criterion for continuity and the continuity of addition, multiplication, and inversion on R."
used_in:
  - lecture: 10
    title: "Homeomorphisms and Topological Equivalence of Euclidean Spaces"
    relationship: "Lecture 10 uses the product mapping criterion and compositions to establish homeomorphisms and coordinate projections."
notation:
  - symbol: "$g \\circ f$"
    gloss: "Composition of maps $(g \\circ f)(x) = g(f(x))$"
  - symbol: "$f|_Y$"
    gloss: "Restriction of $f : X \\to Z$ to a subspace $Y \\subseteq X$"
  - symbol: "$f_0$"
    gloss: "Corestriction of $f : X \\to Z$ to a subspace $Y \\subseteq Z$ containing $f(X)$"
  - symbol: "$f = (f_i)_{i \\in I}$"
    gloss: "Map into a Cartesian product defined by coordinate components $f_i : X \\to Y_i$"
prev: lecture-08
next: lecture-10
---

# Lecture 9 — Properties of Continuous Maps and Algebraic Combinations

## Where we are

In [Lecture 8]({{ site.baseurl }}/point-set-topology/lecture-08/), we proved the basis criterion for continuity and verified that addition $+ : \mathbb{R}^2 \to \mathbb{R}$, multiplication $\cdot : \mathbb{R}^2 \to \mathbb{R}$, and reciprocal inversion $x \mapsto 1/x$ on $\mathbb{R}^\times = \mathbb{R} \setminus \lbrace 0\rbrace$ are continuous maps with respect to the standard topologies.

Here we develop general structural tools for assembling and decomposing continuous functions. We prove three elementary properties: compositions, restrictions to subspaces, and corestrictions to subspaces containing the image are all continuous. We then establish the fundamental universal property of the product topology: a map into an arbitrary Cartesian product is continuous if and only if each of its coordinate components is continuous—and recall why this fundamental property fails under the box topology. Finally, combining this universal property with the continuous operations from Lecture 8, we prove that sums $f+g$, products $fg$, and quotients $f/g$ of continuous real-valued functions are continuous, establishing that the set of continuous real-valued functions on any topological space forms a commutative ring.

---

## Three elementary lemmas: composition, restriction, and corestriction

We begin with three foundational lemmas governing how continuous maps behave under composition and interaction with subspace topologies.

### Lemma 9.1 (Composition of continuous maps) {#lemma-9-1-composition-of-continuous-maps}

{% capture lem91_content %}
Let $X$, $Y$, and $Z$ be topological spaces. Suppose $f : X \to Y$ and $g : Y \to Z$ are continuous maps.

Then the composite map
$$g \circ f : X \to Z$$
is continuous.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 9.1 (Composition of Continuous Maps)" content=lem91_content %}

{% capture lem91_proof %}
The lecturer notes that the proof is immediate and leaves it as an exercise; we write it out in full.

Let $W \subseteq Z$ be an open subset ($W \in \tau_Z$). We need to show that $(g \circ f)^{-1}(W)$ is open in $X$.
By definition of map composition, the preimage satisfies the set-theoretic identity:
$$(g \circ f)^{-1}(W) = f^{-1}\bigl(g^{-1}(W)\bigr).$$
Since $g : Y \to Z$ is continuous and $W \in \tau_Z$, the preimage $V = g^{-1}(W)$ is open in $Y$ ($V \in \tau_Y$).
Since $f : X \to Y$ is continuous and $V \in \tau_Y$, the preimage $f^{-1}(V) = f^{-1}(g^{-1}(W))$ is open in $X$ ($f^{-1}(V) \in \tau_X$).

Therefore $(g \circ f)^{-1}(W)$ is open in $X$ for every open set $W \subseteq Z$.
Hence $g \circ f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 9.1" content=lem91_proof %}

---

### Lemma 9.2 (Restriction to a subspace) {#lemma-9-2-restriction-to-a-subspace}

{% capture lem92_content %}
Let $f : X \to Z$ be a continuous map between topological spaces, and let $Y \subseteq X$ be a subset equipped with the subspace topology $\tau_Y$.

Then the **restriction** of $f$ to $Y$, denoted
$$f|_Y = f \circ i : Y \to Z,$$
where $i : Y \hookrightarrow X$ is the canonical inclusion, is continuous.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 9.2 (Restriction to a Subspace)" content=lem92_content %}

{% capture lem92_proof %}
So $f$ is already given to be a continuous map, and we had seen earlier that with the subspace topology, the inclusion $i : Y \hookrightarrow X$ becomes continuous ([Proposition 7.2]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-2-continuity-of-the-subspace-inclusion)).

Thus, as $f$ is continuous and $i$ is continuous, applying the previous lemma ([Lemma 9.1](#lemma-9-1-composition-of-continuous-maps)), we get that $f \circ i$ is continuous.

So this proves this lemma. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 9.2" content=lem92_proof %}

---

### Lemma 9.3 (Corestriction to a subspace) {#lemma-9-3-corestriction-to-a-subspace}

{% capture lem93_content %}
Let $f : X \to Z$ be a continuous map between topological spaces. Suppose the image $f(X)$ is contained in a subset $Y \subseteq Z$:
$$f(X) \subseteq Y \subseteq Z.$$
Equip $Y$ with the subspace topology inherited from $Z$, and let $i : Y \hookrightarrow Z$ denote the inclusion.

Define the **corestriction** map $f_0 : X \to Y$ by
$$f_0(x) = f(x) \quad \text{for all } x \in X,$$
so that $f = i \circ f_0$.

Then $f_0 : X \to Y$ is continuous.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 9.3 (Corestriction to a Subspace)" content=lem93_content %}

{% capture lem93_proof %}
So let us prove this lemma.

Let $U \subseteq Z$ be open. Then $i^{-1}(U) = U \cap Y$ is open in $Y$, and every open subset of $Y$ has this description by definition of the subspace topology ([Definition 4.3]({{ site.baseurl }}/point-set-topology/lecture-04/#definition-4-3-subspace-topology)).

So thus, to show that $f_0$ is continuous, it is enough to show that $f_0^{-1}(U \cap Y)$ is open in $X$ for every $U$ open in $Z$.

Notice that $f_0^{-1}(U \cap Y)$ can be written as:
$$f_0^{-1}(U \cap Y) = f_0^{-1}\bigl(i^{-1}(U)\bigr) = (i \circ f_0)^{-1}(U).$$
And $i \circ f_0$ is $f$, so this is precisely equal to:
$$f_0^{-1}(U \cap Y) = f^{-1}(U).$$
And as $f$ is continuous, $f^{-1}(U)$ is open in $X$.

Thus, $f_0^{-1}(U \cap Y)$ is open in $X$.

Thus $f_0$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 9.3" content=lem93_proof %}

{% include figure.html
   src="point-set-topology/lecture-09/corestriction-factorisation.svg"
   caption="Figure 9.1: Corestriction factorisation. When the image $f(X)$ is contained in a subspace $Y \subseteq Z$, the map $f$ factors as $X \xrightarrow{f_0} Y \hookrightarrow Z$. The corestriction $f_0$ is continuous with respect to the subspace topology on $Y$."
   alt="Commutative triangle showing map f factoring through subspace Y via corestriction f0." %}

---

## Maps into a Cartesian product

We now examine how continuous maps interact with product spaces.

Let $X$ be a topological space, let $I$ be an arbitrary index set (finite or infinite), and let $\lbrace Y_i \rbrace_{i \in I}$ be an indexed family of topological spaces. Equip the Cartesian product $\prod_{i \in I} Y_i$ with the product topology $\tau_{\text{prod}}$ ([Definition 6.2]({{ site.baseurl }}/point-set-topology/lecture-06/#definition-6-2-the-product-topology-on-arbitrary-products)).

Suppose we are given a family of maps of sets
$$f_i : X \to Y_i \quad \text{for each } i \in I.$$
These determine a unique map into the product:
$$f : X \to \prod_{i \in I} Y_i, \qquad f(x) = \bigl(f_i(x)\bigr)_{i \in I}.$$

### Proposition 9.4 (Product criterion for continuity) {#proposition-9-4-product-criterion-for-continuity}

{% capture prop94_content %}
Let $X$ be a topological space, and equip $\prod_{i \in I} Y_i$ with the product topology. Let $f : X \to \prod_{i \in I} Y_i$ be defined by $f(x) = (f_i(x))_{i \in I}$.

Then $f$ is continuous if and only if each coordinate map
$$f_i : X \to Y_i$$
is continuous for all $i \in I$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 9.4 (Product Criterion for Continuity)" content=prop94_content %}

{% capture prop94_proof %}
So let us prove this proposition.

**$(\Rightarrow)$ First let us assume that $f$ is continuous.**
Now, since this product has the product topology, recall that we had seen the projection maps $p_j : \prod_{i \in I} Y_i \to Y_j$, sending $(y_i)_{i \in I} \mapsto y_j$ ([Proposition 7.4]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-4-continuity-of-coordinate-projections)), and these projection maps are continuous.

And since composition of continuous maps is continuous ([Lemma 9.1](#lemma-9-1-composition-of-continuous-maps)), the composite $p_j \circ f : X \to Y_j$ is continuous.
But the composite is precisely $f_j$: for $x \in X$, $x$ goes to $(f_i(x))_{i \in I}$ and projecting onto the $j$-th coordinate gives $f_j(x)$.
As the composite is $f_j$, it follows that $f_j : X \to Y_j$ is continuous for all $j \in I$.

So this proves one part of the proposition.

**$(\Leftarrow)$ Conversely, let us assume that each $f_i : X \to Y_i$ is continuous for all $i \in I$.**
Recall that the product topology has as basis open sets $\prod_{i \in I} U_i$, where each $U_i \subseteq Y_i$ is open, and the set of indices
$$J = \lbrace i \in I \;:\; U_i \ne Y_i \rbrace$$
is finite ([Definition 6.2]({{ site.baseurl }}/point-set-topology/lecture-06/#definition-6-2-the-product-topology-on-arbitrary-products)).

And as we have seen many times now, to show that $f$ is continuous, it is enough to show that the inverse image of basic open sets is open if the topology is given by a basis ([Lemma 8.1]({{ site.baseurl }}/point-set-topology/lecture-08/#lemma-8-1-basis-criterion-for-continuity)).
So thus, it is enough to show that $f^{-1}(W)$ is open for every basic open set $W = \prod_{i \in I} U_i$.

By a straightforward check in set theory:
$$f^{-1}\left(\prod_{i \in I} U_i\right) = \bigcap_{i \in I} f_i^{-1}(U_i).$$
Now we divide this intersection into two parts:
$$\bigcap_{i \in I} f_i^{-1}(U_i) = \left(\bigcap_{i \in J} f_i^{-1}(U_i)\right) \cap \left(\bigcap_{i \notin J} f_i^{-1}(U_i)\right).$$
Now note that if $i \notin J$, then $U_i = Y_i$, and therefore $f_i^{-1}(U_i) = f_i^{-1}(Y_i) = X$.
So this intersection collapses:
$$\bigcap_{i \in I} f_i^{-1}(U_i) = \left(\bigcap_{i \in J} f_i^{-1}(U_i)\right) \cap X = \bigcap_{i \in J} f_i^{-1}(U_i).$$
Now as each $f_i$ is continuous, this implies $f_i^{-1}(U_i)$ is open in $X$.
And as the cardinality of $J$ is finite and finite intersections of open sets are open (axiom (T2)), this implies that
$$\bigcap_{i \in J} f_i^{-1}(U_i) \text{ is open in } X.$$
Which implies that $f^{-1}\left(\prod_{i \in I} U_i\right)$ is open, which implies that $f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 9.4" content=prop94_proof %}

{% include figure.html
   src="point-set-topology/lecture-09/product-mapping-criterion.svg"
   caption="Figure 9.2: Universal property of the product topology. A map $f = (f_i)_{i \in I} : X \to \prod Y_i$ is continuous if and only if each coordinate projection composite $f_j = p_j \circ f : X \to Y_j$ is continuous."
   alt="Universal property diagram showing map into Cartesian product and coordinate projections." %}

{% capture supp_box_rejection_again %}
**Why this proposition fails for the box topology.**
The lecturer emphasizes that Proposition 9.4 is the fundamental reason mathematicians work with the product topology rather than the box topology on infinite products.

In the box topology $\tau_{\text{box}}$ ([Definition 6.1]({{ site.baseurl }}/point-set-topology/lecture-06/#definition-6-1-the-box-topology)), the index set $J = \lbrace i \in I : U_i \ne Y_i \rbrace$ is permitted to be infinite.
In that case, the preimage becomes an **infinite** intersection $\bigcap_{i \in I} f_i^{-1}(U_i)$. Because arbitrary intersections of open sets are generally not open, the implication $(\Leftarrow)$ completely fails!

We saw this failure concretely in [Proposition 7.6]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-6-discontinuity-of-the-diagonal-map-in-the-box-topology): for the diagonal map $\Delta : \mathbb{R} \to \prod_{n=1}^\infty \mathbb{R}$, $\Delta(x) = (x, x, \dots)$, each coordinate function is the identity $\text{id}_{\mathbb{R}}$, which is continuous. Yet $\Delta$ is discontinuous in the box topology, because the preimage of the basic box $\prod_{n=1}^\infty (-1/n, 1/n)$ is the non-open singleton $\lbrace 0\rbrace$.
Under the product topology, Proposition 9.4 holds unconditionally.
{% endcapture %}
{% include block.html type="supplement" title="Rejection of the box topology via the universal property" content=supp_box_rejection_again %}

---

## Continuous real-valued functions: sums, products, and quotients

Equipped with the product criterion, we return to continuous real-valued functions.

Let $X$ be any topological space, and let $\mathbb{R}$ carry its standard topology.

### Proposition 9.5 (Continuity of sum and product) {#proposition-9-5-continuity-of-sum-and-product}

{% capture prop95_content %}
Let $X$ be a topological space, and let $f, g : X \to \mathbb{R}$ be continuous functions.
1. The **sum function**
   $$(f + g) : X \to \mathbb{R}, \qquad (f + g)(x) = f(x) + g(x)$$
   is continuous.
2. The **product function**
   $$(fg) : X \to \mathbb{R}, \qquad (fg)(x) = f(x)g(x)$$
   is continuous.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 9.5 (Continuity of Sum and Product)" content=prop95_content %}

{% capture prop95_proof %}
And the proof is easy.

So first, using the previous proposition ([Proposition 9.4](#proposition-9-4-product-criterion-for-continuity)), we get a map from $X$ to $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$ given by
$$F : X \to \mathbb{R}^2, \qquad F(x) = \bigl(f(x), g(x)\bigr).$$
And that this map $F$ is continuous as both coordinate functions $f$ and $g$ are continuous.

Since the standard topology on $\mathbb{R}^2$ is the same as the product topology ([Proposition 6.4]({{ site.baseurl }}/point-set-topology/lecture-06/#proposition-6-4-equivalence-of-standard-and-product-topologies-on-rn)), and we proved that $A$ and $M$ are continuous in the standard topology ([Theorem 8.2]({{ site.baseurl }}/point-set-topology/lecture-08/#theorem-8-2-continuity-of-addition-and-multiplication)), this implies that they are also continuous in the product topology.

So therefore, what we can do is look at the compositions with the addition map $A : \mathbb{R}^2 \to \mathbb{R}$ and the multiplication map $M : \mathbb{R}^2 \to \mathbb{R}$:
$$(A \circ F)(x) = A\bigl(f(x), g(x)\bigr) = f(x) + g(x) = (f+g)(x),$$
$$(M \circ F)(x) = M\bigl(f(x), g(x)\bigr) = f(x)g(x) = (fg)(x).$$
So thus, the composite of continuous functions being continuous ([Lemma 9.1](#lemma-9-1-composition-of-continuous-maps)), this implies that $A \circ F$, which is equal to $f + g$, and $M \circ F$, which is equal to $fg$, both these are continuous.

So this completes the proof of the proposition. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 9.5" content=prop95_proof %}

{% include figure.html
   src="point-set-topology/lecture-09/operations-composition-factorisation.svg"
   caption="Figure 9.3: Composition factorisation for operations. Continuous functions $f, g : X \to \mathbb{R}$ combine into the continuous map $F = (f,g) : X \to \mathbb{R} \times \mathbb{R}$. Composing with addition $A$ or multiplication $M$ yields the continuous functions $f+g$ and $fg$."
   alt="Flow diagram showing map X to R x R followed by addition or multiplication to R." %}

---

### Proposition 9.6 (Continuity of the quotient) {#proposition-9-6-continuity-of-the-quotient}

{% capture prop96_content %}
Let $X$ be a topological space, and let $f, g : X \to \mathbb{R}$ be continuous functions.
Suppose that $g(x) \ne 0$ for all $x \in X$, so that the image of $g$ lies in the punctured line $\mathbb{R}^\times = \mathbb{R} \setminus \lbrace 0\rbrace$.

Then the **quotient function**
$$h : X \to \mathbb{R}, \qquad h(x) = \frac{f(x)}{g(x)}$$
is continuous.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 9.6 (Continuity of the Quotient)" content=prop96_content %}

{% capture prop96_proof %}
The proof is very similar to the proof of the earlier propositions.

So proof. First note that, as the image of $g$ is contained in $\mathbb{R}^\times = \mathbb{R} \setminus \lbrace 0\rbrace$, using our earlier result ([Lemma 9.3](#lemma-9-3-corestriction-to-a-subspace)), it follows that $g$ can be viewed as a function
$$g_0 : X \to \mathbb{R}^\times, \qquad g_0(x) = g(x),$$
and is continuous when $\mathbb{R}^\times$ has the subspace topology. (As the lecturer notes, we abuse notation and continue to denote $g_0$ by $g$.)

So therefore, now define a function $1/g$ from $X$ to $\mathbb{R}^\times$:
First, from $X$ to $\mathbb{R}^\times$ we have $g$. And on $\mathbb{R}^\times$, we have the continuous inversion map $y \mapsto 1/y$ ([Theorem 8.4]({{ site.baseurl }}/point-set-topology/lecture-08/#theorem-8-4-continuity-of-inversion-on-the-punctured-real-line)).
So $g$ is continuous, and this map $y \mapsto 1/y$ is continuous.
So therefore, their composite, which sends $x \mapsto g(x) \mapsto 1/g(x)$, is continuous ([Lemma 9.1](#lemma-9-1-composition-of-continuous-maps)).

This composite function shall be denoted $1/g$ from $X$ to $\mathbb{R}^\times$. But now we take the inclusion of $\mathbb{R}^\times$ into $\mathbb{R}$, and this composite is also continuous because $\mathbb{R}^\times$ has the subspace topology ([Lemma 9.2](#lemma-9-2-restriction-to-a-subspace) / [Proposition 7.2]({{ site.baseurl }}/point-set-topology/lecture-07/#proposition-7-2-continuity-of-the-subspace-inclusion)).
So finally we get that the function $1/g : X \to \mathbb{R}$, given by $x \mapsto 1/g(x)$, is continuous.

With this, now we define a map from $X$ to $\mathbb{R} \times \mathbb{R}$ given by
$$x \mapsto \left(f(x), \frac{1}{g(x)}\right).$$
Both coordinate functions are continuous, and this implies by [Proposition 9.4](#proposition-9-4-product-criterion-for-continuity) that this function into $\mathbb{R}^2$ is continuous.
And then we have the multiplication map $M : \mathbb{R}^2 \to \mathbb{R}$, which is also continuous ([Theorem 8.2]({{ site.baseurl }}/point-set-topology/lecture-08/#theorem-8-2-continuity-of-addition-and-multiplication)).

So thus, this shows that $x \mapsto \frac{f(x)}{g(x)}$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 9.6" content=prop96_proof %}

---

## The algebraic structure of continuous functions

The lecturer concludes with a forward-looking remark on the significance of Propositions 9.5 and 9.6.

{% capture rem_ring_structure %}
Let $X$ be any topological space, and let
$$C(X, \mathbb{R}) = \lbrace f : X \to \mathbb{R} \;:\; f \text{ is continuous} \rbrace$$
denote the set of all real-valued continuous functions on $X$.

Propositions 9.5 and 9.6 establish that $C(X, \mathbb{R})$ possesses rich algebraic structures:
1. **Commutative Ring:** Under pointwise addition $(f+g)(x) = f(x)+g(x)$ and pointwise multiplication $(fg)(x) = f(x)g(x)$, $C(X, \mathbb{R})$ forms a commutative ring with identity (the constant function $1$).
2. **Real Vector Space / $\mathbb{R}$-Algebra:** Scalar multiplication by real constants $c \in \mathbb{R}$ preserves continuity ([Exercise 8.2]({{ site.baseurl }}/point-set-topology/lecture-08/#exercise-8-2-continuity-of-scalar-multiplication)), giving $C(X, \mathbb{R})$ the structure of an associative algebra over $\mathbb{R}$.
3. **Invertible Elements:** An element $g \in C(X, \mathbb{R})$ is a unit (invertible element in the ring) if and only if $g(x) \ne 0$ for all $x \in X$, in which case $1/g \in C(X, \mathbb{R})$.

In modern mathematics, the topological properties of the space $X$ can often be recovered directly from the algebraic structure of the ring $C(X, \mathbb{R})$.
{% endcapture %}
{% include block.html type="remark" title="Remark (The Ring of Continuous Functions)" content=rem_ring_structure %}

---

## Exercises

{% capture ex91_content %}
Prove [Lemma 9.1](#lemma-9-1-composition-of-continuous-maps) directly from the definition of continuity:
Let $f : X \to Y$ and $g : Y \to Z$ be continuous maps between topological spaces. Prove that $g \circ f : X \to Z$ is continuous.
{% endcapture %}
{% capture ex91_sol %}
Let $W \subseteq Z$ be an arbitrary open set in $Z$ ($W \in \tau_Z$).
We must show that $(g \circ f)^{-1}(W)$ is open in $X$ ($(g \circ f)^{-1}(W) \in \tau_X$).

Recall the set-theoretic identity for preimages of composite functions:
$$(g \circ f)^{-1}(W) = \lbrace x \in X : (g \circ f)(x) \in W \rbrace = \lbrace x \in X : g(f(x)) \in W \rbrace = \lbrace x \in X : f(x) \in g^{-1}(W) \rbrace = f^{-1}\bigl(g^{-1}(W)\bigr).$$

Now apply the definition of continuity in two stages:
1. Since $g : Y \to Z$ is continuous and $W \in \tau_Z$, the preimage $V = g^{-1}(W)$ is open in $Y$ ($V \in \tau_Y$).
2. Since $f : X \to Y$ is continuous and $V \in \tau_Y$, the preimage $f^{-1}(V) = f^{-1}(g^{-1}(W))$ is open in $X$.

Thus $(g \circ f)^{-1}(W) \in \tau_X$.
Since $W \in \tau_Z$ was arbitrary, $g \circ f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 9.1 (Proof of the Composition Lemma)" content=ex91_content solution=ex91_sol %}

{% capture ex92_content %}
Let $I$ be an arbitrary index set, let $\lbrace Y_i \rbrace_{i \in I}$ be a family of topological spaces, and let $f_i : X \to Y_i$ be set maps for each $i \in I$. Define $f : X \to \prod_{i \in I} Y_i$ by $f(x) = (f_i(x))_{i \in I}$.

Prove the set-theoretic identity:
$$f^{-1}\left(\prod_{i \in I} U_i\right) = \bigcap_{i \in I} f_i^{-1}(U_i)$$
for any choice of subsets $U_i \subseteq Y_i$.
{% endcapture %}
{% capture ex92_sol %}
We establish mutual inclusion:
- **($\subseteq$):** Let $x \in f^{-1}\left(\prod_{i \in I} U_i\right)$.
  By definition of preimage, $f(x) \in \prod_{i \in I} U_i$.
  Since $f(x) = (f_i(x))_{i \in I}$, membership in a Cartesian product means that for every coordinate $i \in I$, the $i$-th entry satisfies $f_i(x) \in U_i$.
  Thus $x \in f_i^{-1}(U_i)$ for all $i \in I$.
  Therefore $x \in \bigcap_{i \in I} f_i^{-1}(U_i)$.

- **($\supseteq$):** Let $x \in \bigcap_{i \in I} f_i^{-1}(U_i)$.
  Then $x \in f_i^{-1}(U_i)$ for every $i \in I$, which means $f_i(x) \in U_i$ for all $i \in I$.
  Consequently, the tuple $(f_i(x))_{i \in I} = f(x)$ belongs to the Cartesian product $\prod_{i \in I} U_i$.
  Hence $x \in f^{-1}\left(\prod_{i \in I} U_i\right)$.

Since both inclusions hold, the two sets are equal. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 9.2 (Preimage of a Product Cylinder)" content=ex92_content solution=ex92_sol %}

{% capture ex93_content %}
Let $X$ be a topological space, and let $f, g : X \to \mathbb{R}$ be continuous functions.
Prove that the difference function
$$(f - g) : X \to \mathbb{R}, \qquad (f - g)(x) = f(x) - g(x)$$
is continuous.
{% endcapture %}
{% capture ex93_sol %}
We present two proofs using results established in the course:

- **Method 1 (via subtraction map):**
  Define $F : X \to \mathbb{R}^2$ by $F(x) = (f(x), g(x))$.
  By [Proposition 9.4](#proposition-9-4-product-criterion-for-continuity), $F$ is continuous because its coordinate maps $f$ and $g$ are continuous.
  In [Exercise 8.3]({{ site.baseurl }}/point-set-topology/lecture-08/#exercise-8-3-continuity-of-subtraction), we proved that the subtraction map $S : \mathbb{R}^2 \to \mathbb{R}$, $S(u,v) = u - v$, is continuous.
  Notice that $(f - g)(x) = f(x) - g(x) = S(f(x), g(x)) = (S \circ F)(x)$.
  By [Lemma 9.1](#lemma-9-1-composition-of-continuous-maps), the composite $f - g = S \circ F$ is continuous.

- **Method 2 (via scalar multiplication and addition):**
  In [Exercise 8.2]({{ site.baseurl }}/point-set-topology/lecture-08/#exercise-8-2-continuity-of-scalar-multiplication), we proved that scalar multiplication $m_{-1} : \mathbb{R} \to \mathbb{R}$, $m_{-1}(t) = -t$, is continuous.
  By Lemma 9.1, the function $-g = m_{-1} \circ g : X \to \mathbb{R}$ is continuous.
  By [Proposition 9.5(1)](#proposition-9-5-continuity-of-sum-and-product), the sum of continuous functions is continuous.
  Therefore $f - g = f + (-g)$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 9.3 (Continuity of the Difference of Functions)" content=ex93_content solution=ex93_sol %}

{% capture ex94_content %}
Let $X = \mathbb{R}$, and consider the countable product $Y = \prod_{n=1}^\infty \mathbb{R}$.
Define the diagonal map $\Delta : \mathbb{R} \to Y$ by $\Delta(x) = (x, x, x, \dots)$.
1. Show that each coordinate map $\Delta_n : \mathbb{R} \to \mathbb{R}$ is continuous.
2. Explain why $\Delta$ is continuous when $Y$ carries the product topology.
3. Show that $\Delta$ is discontinuous when $Y$ carries the box topology, by computing the preimage $\Delta^{-1}\left(\prod_{n=1}^\infty (-1/n, 1/n)\right)$.
{% endcapture %}
{% capture ex94_sol %}
1. For each $n \in \mathbb{N}$, the $n$-th coordinate projection applied to $\Delta(x)$ gives $p_n(\Delta(x)) = x$.
   Thus $\Delta_n = \text{id}_{\mathbb{R}}$ is the identity map on $\mathbb{R}$.
   In [Example 1 of Lecture 7]({{ site.baseurl }}/point-set-topology/lecture-07/#example-1-continuity-of-the-identity-map), the identity map was proved continuous.
2. When $Y$ is given the product topology, [Proposition 9.4](#proposition-9-4-product-criterion-for-continuity) applies: since each coordinate component $\Delta_n = \text{id}_{\mathbb{R}}$ is continuous for all $n \in \mathbb{N}$, the diagonal map $\Delta$ is continuous.
3. In the box topology, the product cylinder $W = \prod_{n=1}^\infty (-1/n, 1/n)$ is an open set, because every factor $(-1/n, 1/n)$ is open in $\mathbb{R}$.
   We compute the preimage under $\Delta$:
   $$\Delta^{-1}(W) = \lbrace x \in \mathbb{R} \;:\; \forall n \in \mathbb{N},\, x \in (-1/n, 1/n) \rbrace = \bigcap_{n=1}^\infty \left(-\frac{1}{n}, \frac{1}{n}\right).$$
   The only real number whose absolute value is strictly less than $1/n$ for all $n \ge 1$ is $0$.
   Therefore:
   $$\Delta^{-1}(W) = \lbrace 0 \rbrace.$$
   In the standard topology on $\mathbb{R}$, the singleton $\lbrace 0 \rbrace$ is not open (any open interval around $0$ contains non-zero reals).
   Since the preimage of the open box $W$ is not open, $\Delta$ is not continuous in the box topology. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 9.4 (Diagonal Map in Product versus Box Topology)" content=ex94_content solution=ex94_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Lemma 9.1 (Composition of Continuous Maps)](#lemma-9-1-composition-of-continuous-maps): $(g \circ f)^{-1}(W) = f^{-1}(g^{-1}(W))$ shows composition preserves continuity.
- [Lemma 9.2 (Restriction to a Subspace)](#lemma-9-2-restriction-to-a-subspace): $f|_Y = f \circ i$ is continuous for any subspace $Y \subseteq X$.
- [Lemma 9.3 (Corestriction to a Subspace)](#lemma-9-3-corestriction-to-a-subspace): $f_0^{-1}(U \cap Y) = f^{-1}(U)$ shows corestriction to $Y \supseteq f(X)$ is continuous.
- [Proposition 9.4 (Product Criterion for Continuity)](#proposition-9-4-product-criterion-for-continuity): $f = (f_i)_{i \in I} : X \to \prod Y_i$ is continuous iff each $f_i$ is continuous (product topology).
- [Proposition 9.5 (Continuity of Sum and Product)](#proposition-9-5-continuity-of-sum-and-product): $f+g = A \circ (f,g)$ and $fg = M \circ (f,g)$ are continuous.
- [Proposition 9.6 (Continuity of the Quotient)](#proposition-9-6-continuity-of-the-quotient): If $g \ne 0$, $1/g = i \circ \text{inv} \circ g_0$ and $f/g = f \cdot (1/g)$ are continuous.
- [Remark (The Ring of Continuous Functions)](#remark-the-ring-of-continuous-functions): $C(X, \mathbb{R})$ forms a commutative ring and real algebra.
- [Exercise 9.1 (Proof of the Composition Lemma)](#exercise-9-1-proof-of-the-composition-lemma): Detail of $(g \circ f)^{-1}(W)$.
- [Exercise 9.2 (Preimage of a Product Cylinder)](#exercise-9-2-preimage-of-a-product-cylinder): Mutual inclusion for $f^{-1}(\prod U_i) = \bigcap f_i^{-1}(U_i)$.
- [Exercise 9.3 (Continuity of the Difference of Functions)](#exercise-9-3-continuity-of-the-difference-of-functions): Factoring $f-g$ via subtraction map $S$ or $(-1)$-scaling.
- [Exercise 9.4 (Diagonal Map in Product versus Box Topology)](#exercise-9-4-diagonal-map-in-product-versus-box-topology): $\Delta^{-1}(\prod (-1/n, 1/n)) = \lbrace 0\rbrace \notin \tau_{\mathbb{R}}$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §18.** Theorem 18.2 covers composition, restriction, and corestriction; Theorem 18.4 establishes the product criterion for continuity; Section 18 concludes with the algebra of continuous real-valued functions.

**Morris, *Topology Without Tears*, Chapter 4.** Section 4.3 discusses properties of continuous maps, compositions, and algebraic combinations of functions.
