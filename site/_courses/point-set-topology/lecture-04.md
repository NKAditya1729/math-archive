---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 4
title: "The Generating Conditions for a Basis and the Subspace Topology"
coverage: >
  Proves that the union of all elements in a basis equals the ambient space.
  Formulates and proves the generating proposition: an abstract collection B
  satisfying the coverage and pairwise intersection conditions generates a unique
  topology tau_B for which B is a basis. Introduces the subspace topology
  tau_Y on a subset Y of a topological space, verifies the restrictions of trivial
  and discrete spaces, and proves that the integers Z with the subspace topology
  from the real line form a discrete space.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 3
    title: "The Standard Topology on Rn, Open Sets, and Bases"
    relationship: "Supplies the definition of a basis for an existing topology and the formal definition of an open set."
used_in:
  - lecture: 5
    title: "The Comparison Lemma and the Product Topology"
    relationship: "Lecture 5 uses the generating conditions to define the product topology on X x Y and applies the subspace topology to the real line embedded in the plane."
notation:
  - symbol: "$\\tau_{\\mathcal{B}}$"
    gloss: "The topology generated on $X$ by a collection $\\mathcal{B} \\subseteq \\mathcal{P}(X)$ satisfying the generating conditions"
  - symbol: "$\\tau_Y$"
    gloss: "The subspace topology on $Y \\subseteq X$, consisting of all relative open sets $U \\cap Y$ with $U \\in \\tau$"
prev: lecture-03
next: lecture-05
---

# Lecture 4 — The Generating Conditions for a Basis and the Subspace Topology

## Where we are

In [Lecture 3]({{ site.baseurl }}/point-set-topology/lecture-03/), we defined what it means for a collection of subsets $\mathcal{B} \subseteq \tau$ to form a basis for an *already existing* topological space $(X,\tau)$: every open set $U \in \tau$ and every point $x \in U$ must admit a basic witness $W \in \mathcal{B}$ with $x \in W \subseteq U$. We then verified that open intervals, open squares, and open hypercubes form bases for the standard topologies on $\mathbb{R}$, $\mathbb{R}^2$, and $\mathbb{R}^n$.

Here we invert the perspective. Instead of starting with a known topology and finding a basis for it, we ask: under what intrinsic conditions can an abstract collection $\mathcal{B} \subseteq \mathcal{P}(X)$ be used to *construct* a topology from scratch? We identify two necessary and sufficient conditions—the **generating conditions**—and prove the fundamental proposition that any such collection generates a unique topology $\tau_{\mathcal{B}}$ with $\mathcal{B}$ as its basis. We then introduce the **subspace topology**, which allows any subset of a topological space to inherit a topology in a natural way, and prove that $\mathbb{Z} \subseteq \mathbb{R}$ forms a discrete topological space.

---

## Union of basis elements

We begin with a preliminary lemma concerning any basis of a given topological space.

{% capture lem_union_basis %}
Let $(X,\tau)$ be a topological space, and let $\mathcal{B} \subseteq \tau$ be a basis for $\tau$. Then the union of all elements of $\mathcal{B}$ is the whole space $X$:
$$\bigcup_{W \in \mathcal{B}} W = X.$$
{% endcapture %}
{% include block.html type="lemma" title="Lemma 4.1 (Union of basis elements)" content=lem_union_basis %}

{% capture lem_union_proof %}
It is clear that the union $\bigcup_{W \in \mathcal{B}} W \subseteq X$, as $\mathcal{B}$ is a subset of $\tau$, which is a subset of the power set of $X$; so $W \in \mathcal{B}$ implies $W \subseteq X$, and we are just taking the union.

So we only need to prove the reverse inclusion ($X \subseteq \bigcup_{W \in \mathcal{B}} W$).

Let $x \in X$ be an element. Then, taking $U = X$ (note that $U = X$ is in $\tau$ by axiom (T1)), we can use the defining property of the basis. There is a $W \in \mathcal{B}$—let us denote it $W_x$—such that $x \in W_x$, and obviously $W_x \subseteq X = U$.

Thus we get that this union contains $x$ for all $x \in X$. Thus $X$ is contained in the union, because one of these $W$'s is $W_x$.

This completes the proof of the lemma. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 4.1" content=lem_union_proof %}

---

## Generating a topology from an abstract collection

We now turn to the central question: suppose $X$ is merely a set with *no topology specified in advance*. When can a collection of subsets $\mathcal{B} \subseteq \mathcal{P}(X)$ serve as the basis for a topology on $X$?

{% capture prop_gen_topo %}
Let $X$ be a set, and let $\mathcal{B} \subseteq \mathcal{P}(X)$ be a collection of subsets of $X$ satisfying the following two properties:

1. **Covering condition:** The union of all elements of $\mathcal{B}$ is $X$:
   $$\bigcup_{W \in \mathcal{B}} W = X.$$
2. **Intersection refinement condition:** For any two elements $W_1, W_2 \in \mathcal{B}$ and any point $x \in W_1 \cap W_2$, there exists an element $W \in \mathcal{B}$ such that
   $$x \in W \subseteq W_1 \cap W_2.$$

Define a collection $\tau \subseteq \mathcal{P}(X)$ as follows:
$$\tau = \lbrace U \subseteq X \;:\; \forall x \in U\ \exists W \in \mathcal{B} \text{ such that } x \in W \subseteq U \rbrace.$$
Then:
1. $\tau$ is a topology on $X$.
2. $\mathcal{B}$ is a basis for $\tau$.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 4.2 (The Generating Proposition)" content=prop_gen_topo %}

{% include figure.html
   src="point-set-topology/lecture-04/basis-intersection-condition.svg"
   caption="The intersection refinement condition (ii) for a basis: given $W_1, W_2 \in \mathcal{B}$ and a point $x \in W_1 \cap W_2$, there exists a basic set $W \in \mathcal{B}$ containing $x$ and contained within $W_1 \cap W_2$."
   alt="Two intersecting regions W_1 and W_2 with a point x in their intersection surrounded by a smaller basic open set W." %}

{% capture supp_gen_vs_basis %}
Notice the essential distinction between [Definition 3.6 in Lecture 3]({{ site.baseurl }}/point-set-topology/lecture-03/#definition-3-6-basis-for-a-topology) and Proposition 4.2:

- In **Lecture 3**, a topology $\tau$ is already given. A subcollection $\mathcal{B} \subseteq \tau$ needs only **one** condition: every $U \in \tau$ must be witnessed locally by elements of $\mathcal{B}$. The intersection property comes for free because if $W_1, W_2 \in \mathcal{B} \subseteq \tau$, their intersection $W_1 \cap W_2$ already belongs to $\tau$ by axiom (T2), so any point in the intersection automatically has a basic witness in $\mathcal{B}$.
- In **Proposition 4.2**, *no topology exists beforehand*. The intersection $W_1 \cap W_2$ of two basic sets is generally *not* a member of $\mathcal{B}$. (For instance, the intersection of two open discs in the plane is not an open disc). Condition (2) guarantees that points in finite intersections can still be sheltered inside basic elements, which is precisely what is needed to prove that $\tau$ satisfies axiom (T2).
{% endcapture %}
{% include block.html type="supplement" title="The generating conditions versus the basis definition" content=supp_gen_vs_basis %}

{% capture prop_gen_proof %}
In order to prove this proposition, we have to check that $\tau$ satisfies the three conditions which define a topology. Let us check these one by one.

**(T1).** The empty set is in $\tau$: this is vacuously true, since there is no point $x$ in the empty set, and so therefore there is nothing to check.

The full set $X$ is in $\tau$. Why is this? As $\bigcup_{W \in \mathcal{B}} W = X$, given any $x \in X$, it is in one of these $W \in \mathcal{B}$ such that $x \in W$. And obviously $W \subseteq X$.

Thus, we have proved that both the empty set and $X$ are in $\tau$. So this proves the first condition. ✓

**(T2).** Let's look at the second condition. Here we want to say that finite intersections of elements of $\tau$ are in $\tau$. So suppose $U_1, U_2, \dots, U_n \in \tau$. Then we need to show that the intersection $\bigcap_{i=1}^n U_i$ is in $\tau$.

For this, we choose $x \in \bigcap_{i=1}^n U_i$. Then for each $i$, as $U_i \in \tau$ and $x \in U_i$, there is $W_i \in \mathcal{B}$ such that $x \in W_i$ and $W_i \subseteq U_i$.

So we claim that property (2) implies the following condition, which we call (2$'$):
> **Condition (2$'$).** If $x \in \bigcap_{i=1}^n W_i$ for finitely many $W_1, \dots, W_n \in \mathcal{B}$, then there is a $W \in \mathcal{B}$ such that $x \in W$ and $W \subseteq \bigcap_{i=1}^n W_i$.

Property (2) is the same as (2$'$) when $n = 2$. For general $n$, the fact that (2) implies (2$'$) follows by an easy induction argument, which is left as an exercise ([Exercise 4.1](#exercise-4-1-generalization-of-condition-2-by-induction)).

Then, using (2$'$), we get that there is $W \in \mathcal{B}$ which contains $x$, such that
$$x \in W \subseteq \bigcap_{i=1}^n W_i \subseteq \bigcap_{i=1}^n U_i.$$

Thus, this intersection $\bigcap_{i=1}^n U_i$ is in $\tau$, as it satisfies the property defining $\tau$. So the second condition holds. ✓

**(T3).** And finally, we have to check the third condition. Given a set $I$ and subsets $U_i \subseteq X$ such that each $U_i \in \tau$, we need to show that the union $\bigcup_{i \in I} U_i$ is in $\tau$.

Once again, we do the same. Let $x$ be an element in the union: $x \in \bigcup_{i \in I} U_i$. Then $x \in U_j$ for some $j \in I$. And since $U_j \in \tau$, this implies there exists some $W \in \mathcal{B}$ such that $x \in W$ and $W \subseteq U_j$, which in turn is going to be contained in this union:
$$x \in W \subseteq U_j \subseteq \bigcup_{i \in I} U_i.$$

So this shows that the union satisfies the defining property for $\tau$, and so is contained in $\tau$.

This completes the proof that $\tau$ is a topology on $X$. ✓

Next, we also need to show that $\mathcal{B}$ is a basis for $\tau$. That is, for every $U \in \tau$ and $x \in U$, we need to show there exists $W \in \mathcal{B}$ such that $x \in W$ and $W \subseteq U$. But this follows immediately from the definition of $U$ being in $\tau$ (and taking $W = W_0 \in \mathcal{B}$ shows $\mathcal{B} \subseteq \tau$).

This completes the proof of the proposition. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 4.2" content=prop_gen_proof %}

---

## The notation $\tau_{\mathcal{B}}$ and basis equivalence

Whenever a collection $\mathcal{B} \subseteq \mathcal{P}(X)$ satisfies the two generating conditions of Proposition 4.2, we denote the topology it generates by
$$\tau_{\mathcal{B}}.$$
By Proposition 4.2, $\mathcal{B}$ is a basis for $\tau_{\mathcal{B}}$.

Suppose now that we begin with a topological space $(X,\tau)$ and choose a basis $\mathcal{B}$ for $\tau$. By [Lemma 4.1](#lemma-4-1-union-of-basis-elements), $\bigcup_{W \in \mathcal{B}} W = X$, so property (1) holds. Furthermore, because each $W_1, W_2 \in \mathcal{B}$ belongs to $\tau$, their intersection $W_1 \cap W_2$ belongs to $\tau$ by axiom (T2); since $\mathcal{B}$ is a basis for $\tau$, any point $x \in W_1 \cap W_2$ admits a witness $W \in \mathcal{B}$ with $x \in W \subseteq W_1 \cap W_2$. Thus $\mathcal{B}$ satisfies both generating properties (1) and (2).

Therefore, $\mathcal{B}$ generates a topology $\tau_{\mathcal{B}}$ on $X$. A priori, this generated topology $\tau_{\mathcal{B}}$ might differ from our original topology $\tau$. In fact, they always coincide ([Exercise 4.2](#exercise-4-2-equivalence-of-tau-and-tau-b)):
$$\tau = \tau_{\mathcal{B}}.$$

---

## The subspace topology

We now set bases aside temporarily and examine how subsets of a topological space inherit a topology.

{% capture def_subspace %}
Let $(X,\tau)$ be a topological space, and let $Y \subseteq X$ be an arbitrary subset. The **subspace topology** (or **relative topology**) on $Y$, denoted $\tau_Y$, is the collection of all intersections of open sets of $X$ with $Y$:
$$\tau_Y = \lbrace U \cap Y \;:\; U \in \tau \rbrace \subseteq \mathcal{P}(Y).$$
Equipped with this topology, the pair $(Y,\tau_Y)$ is called a **subspace** of $(X,\tau)$.

A subset $V \subseteq Y$ is said to be **open in $Y$** (or **relatively open**) if $V \in \tau_Y$; that is, if there exists an open set $U \in \tau$ such that $V = U \cap Y$.
{% endcapture %}
{% include block.html type="definition" title="Definition 4.3 (Subspace topology)" content=def_subspace %}

{% include figure.html
   src="point-set-topology/lecture-04/subspace-open-set.svg"
   caption="The subspace topology: an open set $U \in \tau$ in the ambient space $X$ intersects the subset $Y$ to produce a relative open set $U \cap Y \in \tau_Y$."
   alt="The ambient space X containing a subspace Y and an open set U, with their intersection shaded as a relative open set." %}

{% capture supp_rel_open %}
Openness in a subspace $Y$ must never be confused with openness in the ambient space $X$.

A set $V \subseteq Y$ can be open in the subspace topology $\tau_Y$ without being open in the ambient topology $\tau$. For example, consider the interval $Y = [0,1) \subseteq \mathbb{R}$ with the subspace topology inherited from the standard topology on $\mathbb{R}$. The half-open interval $[0, 1/2)$ is open in $Y$, because
$$[0, 1/2) = (-1/2, 1/2) \cap [0,1),$$
and $(-1/2, 1/2)$ is an open interval in $\mathbb{R}$. But as established in [Lecture 2]({{ site.baseurl }}/point-set-topology/lecture-02/#non-example-the-interval-0-1-fails), $[0, 1/2)$ is *not* open in $\mathbb{R}$.

Only when $Y$ itself is an open subset of $X$ ($Y \in \tau$) does every relatively open set $V \in \tau_Y$ become open in $X$ as well.
{% endcapture %}
{% include block.html type="supplement" title="Relative openness versus ambient openness" content=supp_rel_open %}

---

## First examples of subspace topologies

We examine three introductory examples of the subspace topology.

### Example 1: Subspaces of trivial spaces

{% capture ex_sub_triv %}
Let $(X,\tau)$ be a set equipped with the trivial topology $\tau = \lbrace \varnothing, X \rbrace$, and let $Y \subseteq X$ be any subset.

The open sets of the subspace topology $\tau_Y$ are the intersections of members of $\tau$ with $Y$:
$$\tau_Y = \lbrace \varnothing \cap Y, \; X \cap Y \rbrace = \lbrace \varnothing, Y \rbrace.$$
Thus, the subspace topology on $Y$ is the **trivial topology** on $Y$.
{% endcapture %}
{% include block.html type="example" title="Example 1 (Subspace of a trivial space)" content=ex_sub_triv %}

### Example 2: Subspaces of discrete spaces

{% capture ex_sub_disc %}
Let $(X,\tau)$ be a set equipped with the discrete topology $\tau = \mathcal{P}(X)$, and let $Y \subseteq X$ be any subset.

We claim that $\tau_Y$ is the discrete topology on $Y$; that is, $\tau_Y = \mathcal{P}(Y)$.

**Proof.** Clearly $\tau_Y \subseteq \mathcal{P}(Y)$. Conversely, let $V \subseteq Y$ be an arbitrary subset of $Y$. Since $Y \subseteq X$, $V$ is also a subset of $X$, so $V \in \mathcal{P}(X) = \tau$. Therefore,
$$V = V \cap Y \in \tau_Y.$$
Thus every subset of $Y$ belongs to $\tau_Y$, so $\tau_Y = \mathcal{P}(Y)$ is the **discrete topology** on $Y$. $\blacksquare$
{% endcapture %}
{% include block.html type="example" title="Example 2 (Subspace of a discrete space)" content=ex_sub_disc %}

### Example 3: The integers as a subspace of the real line

{% capture ex_sub_z %}
Let $X = \mathbb{R}$ equipped with the standard topology $\tau$, and let $Y = \mathbb{Z}$ be the subset of integers.

**Claim.** The subspace topology on $\mathbb{Z}$ is the **discrete topology**:
$$\tau_{\mathbb{Z}} = \mathcal{P}(\mathbb{Z}).$$

**Proof Strategy.** To prove that a topology on a set is discrete, it is sufficient to show that **every singleton is open**. Indeed, if each singleton $\lbrace n \rbrace \in \tau_{\mathbb{Z}}$, then any arbitrary subset $W \subseteq \mathbb{Z}$ can be expressed as the union of its constituent singletons:
$$W = \bigcup_{n \in W} \lbrace n \rbrace.$$
By axiom (T3), arbitrary unions of open sets are open. Thus, if every singleton is open, every subset $W \subseteq \mathbb{Z}$ must be open.

**Proof.** Let $n \in \mathbb{Z}$ be an arbitrary integer. Consider the open interval
$$U_n = \left(n - \frac{1}{2}, \; n + \frac{1}{2}\right) \subseteq \mathbb{R}.$$
By [Exercise 3.4 in Lecture 3]({{ site.baseurl }}/point-set-topology/lecture-03/#exercise-3-4-open-intervals-belong-to-tau), $U_n$ is open in the standard topology on $\mathbb{R}$, so $U_n \in \tau$.

{% include figure.html
   src="point-set-topology/lecture-04/z-subspace-discrete.svg"
   caption="The open interval $(n - 1/2, n + 1/2)$ contains only the integer $n$, isolating the singleton $\lbrace n\rbrace$ as a relative open set in $\mathbb{Z}$."
   alt="A number line showing integer points, with an interval of length 1 centered at n isolating n from all other integers." %}

We now compute the intersection $U_n \cap \mathbb{Z}$:
$$U_n \cap \mathbb{Z} = \left\lbrace x \in \mathbb{Z} \;:\; n - \frac{1}{2} < x < n + \frac{1}{2} \right\rbrace.$$
The only integer strictly between $n - 1/2$ and $n + 1/2$ is $n$ itself. Therefore,
$$U_n \cap \mathbb{Z} = \lbrace n \rbrace.$$
By Definition 4.3, this proves that the singleton $\lbrace n \rbrace \in \tau_{\mathbb{Z}}$.

Since $n \in \mathbb{Z}$ was arbitrary, every singleton in $\mathbb{Z}$ is open in the subspace topology. As noted in our strategy, any subset $W \subseteq \mathbb{Z}$ is the union $W = \bigcup_{n \in W} \lbrace n \rbrace$, which is an arbitrary union of open sets in $\tau_{\mathbb{Z}}$. By condition (T3), $W \in \tau_{\mathbb{Z}}$.

Therefore, $\tau_{\mathbb{Z}} = \mathcal{P}(\mathbb{Z})$, so the subspace topology on $\mathbb{Z}$ is the discrete topology. $\blacksquare$
{% endcapture %}
{% include block.html type="example" title="Example 3 (The integers Z in R is discrete)" content=ex_sub_z %}

---

## Closing and forward reference

We have established the two generating conditions for constructing a topology from a basis $\mathcal{B}$, and introduced the subspace topology $\tau_Y$.

In [Lecture 5]({{ site.baseurl }}/point-set-topology/lecture-05/), we will:
1. Examine a geometric example of a subspace: the embedding of the real line $\mathbb{R} \hookrightarrow \mathbb{R}^2$ as the horizontal axis, proving that its subspace topology coincides with the standard topology on $\mathbb{R}$.
2. Formulate and prove the **Comparison Lemma**, which gives a criterion for when one topology is contained within another in terms of their bases.
3. Use the generating conditions of Proposition 4.2 to construct the **product topology** on the Cartesian product $X \times Y$.

---

## Exercises

{% capture ex41_content %}
Let $\mathcal{B} \subseteq \mathcal{P}(X)$ be a collection satisfying property (2) of Proposition 4.2: for any $W_1, W_2 \in \mathcal{B}$ and $x \in W_1 \cap W_2$, there exists $W \in \mathcal{B}$ such that $x \in W \subseteq W_1 \cap W_2$.

Prove by mathematical induction on $n \ge 2$ that Condition (2$'$) holds: for any $W_1, W_2, \dots, W_n \in \mathcal{B}$ and any $x \in \bigcap_{i=1}^n W_i$, there exists $W \in \mathcal{B}$ such that
$$x \in W \subseteq \bigcap_{i=1}^n W_i.$$
{% endcapture %}
{% capture ex41_sol %}
We proceed by induction on $n$.

- **Base case ($n = 2$):** When $n = 2$, the statement is precisely condition (2) of Proposition 4.2, which holds by hypothesis.
- **Inductive step:** Assume the statement holds for some $n \ge 2$. Let $W_1, \dots, W_n, W_{n+1} \in \mathcal{B}$ and let
  $$x \in \bigcap_{i=1}^{n+1} W_i = \left(\bigcap_{i=1}^n W_i\right) \cap W_{n+1}.$$
  In particular, $x \in \bigcap_{i=1}^n W_i$. By the induction hypothesis, there exists an element $W' \in \mathcal{B}$ such that
  $$x \in W' \subseteq \bigcap_{i=1}^n W_i.$$
  Since $x \in W'$ and $x \in W_{n+1}$, we have $x \in W' \cap W_{n+1}$. Since both $W'$ and $W_{n+1}$ belong to $\mathcal{B}$, we may apply the base case ($n = 2$) to the pair $W', W_{n+1}$. This produces an element $W \in \mathcal{B}$ such that
  $$x \in W \subseteq W' \cap W_{n+1}.$$
  Since $W' \subseteq \bigcap_{i=1}^n W_i$, we have
  $$W' \cap W_{n+1} \subseteq \left(\bigcap_{i=1}^n W_i\right) \cap W_{n+1} = \bigcap_{i=1}^{n+1} W_i.$$
  Combining these inclusions gives $x \in W \subseteq \bigcap_{i=1}^{n+1} W_i$, which completes the inductive step. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 4.1 (Generalization of Condition 2 by induction)" content=ex41_content solution=ex41_sol %}

{% capture ex42_content %}
Let $(X,\tau)$ be a topological space and let $\mathcal{B} \subseteq \tau$ be a basis for $\tau$. Show that the topology $\tau_{\mathcal{B}}$ generated by $\mathcal{B}$ according to Proposition 4.2 is equal to $\tau$.
{% endcapture %}
{% capture ex42_sol %}
We show mutual inclusion between $\tau$ and $\tau_{\mathcal{B}}$.

1. **$\tau \subseteq \tau_{\mathcal{B}}$:**
   Let $U \in \tau$. If $U = \varnothing$, then $\varnothing \in \tau_{\mathcal{B}}$ by axiom (T1). If $U \ne \varnothing$, let $x \in U$. Since $\mathcal{B}$ is a basis for $\tau$, there exists $W \in \mathcal{B}$ such that $x \in W \subseteq U$. By definition of $\tau_{\mathcal{B}}$, this means $U \in \tau_{\mathcal{B}}$. Thus $\tau \subseteq \tau_{\mathcal{B}}$.

2. **$\tau_{\mathcal{B}} \subseteq \tau$:**
   Let $V \in \tau_{\mathcal{B}}$. For each $x \in V$, the definition of $\tau_{\mathcal{B}}$ provides an element $W_x \in \mathcal{B}$ such that $x \in W_x \subseteq V$. Taking the union over all $x \in V$, we obtain
   $$V = \bigcup_{x \in V} W_x.$$
   Since $\mathcal{B}$ is a basis for $\tau$, each $W_x \in \mathcal{B} \subseteq \tau$. Thus $V$ is expressed as an arbitrary union of open sets in $\tau$. By axiom (T3) for $(X,\tau)$, the union belongs to $\tau$. Thus $V \in \tau$, so $\tau_{\mathcal{B}} \subseteq \tau$.

We conclude that $\tau = \tau_{\mathcal{B}}$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 4.2 (Equivalence of tau and tau_B)" content=ex42_content solution=ex42_sol %}

{% capture ex43_content %}
Let $(X,\tau)$ be a topological space and $Y \subseteq X$ a subset. Verify that the collection
$$\tau_Y = \lbrace U \cap Y \;:\; U \in \tau \rbrace$$
satisfies the three defining axioms (T1)–(T3) of a topology on $Y$.
{% endcapture %}
{% capture ex43_sol %}
We check the three axioms for $\tau_Y$:

- **Condition (T1):** Since $\varnothing, X \in \tau$, we have
  $$\varnothing = \varnothing \cap Y \in \tau_Y \quad \text{and} \quad Y = X \cap Y \in \tau_Y.$$
- **Condition (T2):** Let $V_1, \dots, V_n \in \tau_Y$. By definition, for each $i \in \lbrace 1, \dots, n \rbrace$, there exists $U_i \in \tau$ such that $V_i = U_i \cap Y$. Using the distributive property of intersections:
  $$\bigcap_{i=1}^n V_i = \bigcap_{i=1}^n (U_i \cap Y) = \left(\bigcap_{i=1}^n U_i\right) \cap Y.$$
  Since $(X,\tau)$ is a topological space, $\bigcap_{i=1}^n U_i \in \tau$ by axiom (T2). Therefore, the intersection of $V_i$ is the intersection of an open set in $X$ with $Y$, so $\bigcap_{i=1}^n V_i \in \tau_Y$.
- **Condition (T3):** Let $\lbrace V_i \rbrace_{i \in I}$ be an arbitrary family in $\tau_Y$. For each $i \in I$, write $V_i = U_i \cap Y$ with $U_i \in \tau$. Using the distributive property of unions over intersections:
  $$\bigcup_{i \in I} V_i = \bigcup_{i \in I} (U_i \cap Y) = \left(\bigcup_{i \in I} U_i\right) \cap Y.$$
  By axiom (T3) for $(X,\tau)$, $\bigcup_{i \in I} U_i \in \tau$. Hence $\bigcup_{i \in I} V_i \in \tau_Y$.

Thus $\tau_Y$ is a topology on $Y$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 4.3 (Verification of the subspace axioms)" content=ex43_content solution=ex43_sol %}

{% capture ex44_content %}
Let $(X,\tau)$ be a topological space, and let $Z \subseteq Y \subseteq X$. Prove that the subspace topology on $Z$ inherited from $(Y,\tau_Y)$ is identical to the subspace topology on $Z$ inherited directly from $(X,\tau)$; that is,
$$(\tau_Y)_Z = \tau_Z.$$
{% endcapture %}
{% capture ex44_sol %}
By Definition 4.3:
- An element of $(\tau_Y)_Z$ has the form $V \cap Z$, where $V \in \tau_Y$. Since $V \in \tau_Y$, $V = U \cap Y$ for some $U \in \tau$. Therefore,
  $$V \cap Z = (U \cap Y) \cap Z = U \cap (Y \cap Z) = U \cap Z,$$
  because $Z \subseteq Y$ implies $Y \cap Z = Z$. Since $U \in \tau$, $U \cap Z \in \tau_Z$. Thus $(\tau_Y)_Z \subseteq \tau_Z$.
- Conversely, an element of $\tau_Z$ has the form $U \cap Z$ with $U \in \tau$. Since $Z \subseteq Y$, we can write
  $$U \cap Z = (U \cap Y) \cap Z.$$
  Since $U \in \tau$, the set $V = U \cap Y$ belongs to $\tau_Y$. Thus $U \cap Z = V \cap Z \in (\tau_Y)_Z$. Hence $\tau_Z \subseteq (\tau_Y)_Z$.

Therefore, $(\tau_Y)_Z = \tau_Z$. Subspaces inherit topologies transitively. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 4.4 (Transitivity of subspaces)" content=ex44_content solution=ex44_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Lemma 4.1 (Union of basis elements)](#lemma-4-1-union-of-basis-elements): If $\mathcal{B}$ is a basis for $(X,\tau)$, then $\bigcup_{W \in \mathcal{B}} W = X$.
- [Proposition 4.2 (The Generating Proposition)](#proposition-4-2-the-generating-proposition): Any collection $\mathcal{B} \subseteq \mathcal{P}(X)$ covering $X$ and satisfying pairwise intersection refinement generates a topology $\tau_{\mathcal{B}}$ with $\mathcal{B}$ as a basis.
- [Definition 4.3 (Subspace topology)](#definition-4-3-subspace-topology): $\tau_Y = \lbrace U \cap Y : U \in \tau\rbrace$ is the subspace topology on $Y \subseteq X$.
- [Example 1 (Subspace of a trivial space)](#example-1-subspace-of-a-trivial-space): Trivial spaces restrict to trivial subspaces.
- [Example 2 (Subspace of a discrete space)](#example-2-subspace-of-a-discrete-space): Discrete spaces restrict to discrete subspaces.
- [Example 3 (The integers Z in R is discrete)](#example-3-the-integers-z-in-r-is-discrete): $\mathbb{Z} \subseteq \mathbb{R}$ is discrete because $(n - 1/2, n + 1/2) \cap \mathbb{Z} = \lbrace n\rbrace$.
- [Exercise 4.1 (Generalization of Condition 2 by induction)](#exercise-4-1-generalization-of-condition-2-by-induction): Proof that pairwise refinement extends to finite intersections.
- [Exercise 4.2 (Equivalence of tau and tau_B)](#exercise-4-2-equivalence-of-tau-and-tau-b): A basis for a topology generates the same topology back: $\tau = \tau_{\mathcal{B}}$.
- [Exercise 4.3 (Verification of the subspace axioms)](#exercise-4-3-verification-of-the-subspace-axioms): Proof that $\tau_Y$ satisfies axioms (T1)–(T3).
- [Exercise 4.4 (Transitivity of subspaces)](#exercise-4-4-transitivity-of-subspaces): $(\tau_Y)_Z = \tau_Z$ for nested subspaces $Z \subseteq Y \subseteq X$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §13 & §16.** Section 13 presents Lemma 13.1 (the generating proposition for bases) and the inductive extension of condition (2). Section 16 introduces the subspace topology with standard examples and proves transitivity of subspaces.

**Morris, *Topology Without Tears*, Chapter 3.** Section 3.1 covers the subspace topology with detailed examples on subsets of the real line, including the discrete topology on $\mathbb{Z}$.
