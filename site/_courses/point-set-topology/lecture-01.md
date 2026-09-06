---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 1
title: "Topological Spaces: Definition and First Examples"
coverage: >
  Recalls the power set. Defines a topology on a set X by three conditions:
  that the empty set and X belong; that finite intersections of members
  belong; and that arbitrary unions of members belong. Verifies all three
  conditions for three topologies available on any set X — the trivial
  topology, the discrete topology, and the finite complement topology.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 2
corrections: 0
depends_on: []
used_in:
  - lecture: 2
    title: "The Standard Topology on the Real Line and the Plane"
    relationship: "Supplies the topology axioms (T1)–(T3) used to establish the standard topology on R."
notation:
  - symbol: "$\\varnothing$"
    gloss: "Empty set (read aloud as 'phi' on the lecture audio)"
  - symbol: "$\\mathcal{P}(X)$"
    gloss: "Power set of $X$; the set of all subsets of $X$"
  - symbol: "$\\tau$"
    gloss: "A topology; a collection of subsets of $X$ satisfying axioms (T1)–(T3)"
  - symbol: "$(X, \\tau)$"
    gloss: "A topological space; a set $X$ equipped with topology $\\tau$"
  - symbol: "$X \\setminus U$"
    gloss: "Set difference / relative complement: elements in $X$ not in $U$"
  - symbol: "$\\bigcap_{i=1}^n U_i$"
    gloss: "Finite intersection of sets (axiom (T2))"
  - symbol: "$\\bigcup_{i \\in I} U_i$"
    gloss: "Arbitrary union of sets over any index set $I$ (axiom (T3))"
prev:
next: lecture-02
---

# Lecture 1 — Topological Spaces: Definition and First Examples

## Where we are

This is the opening lecture of the course. Nothing is assumed beyond
elementary set theory: unions, intersections, complements, and the idea of a
collection of subsets.

The lecture does one thing. It gives the definition of a topology, and then
shows that *any* set whatsoever — with no structure on it at all — already
carries at least three different topologies. That is the first real content of
the subject: a topology is extra structure that we *choose* to put on a set,
and the same set admits many different choices.

---

## Recollection: the power set

{% capture def_recollection %}
Let $X$ be any set. The **power set** of $X$, written $\mathcal{P}(X)$, is
the set whose elements are all the subsets of $X$.
{% endcapture %}
{% include block.html type="definition" title="Recollection (Power set)" content=def_recollection %}

In particular both the empty set $\varnothing$ and the full set $X$ are
elements of $\mathcal{P}(X)$.

{% capture supp_phi %}
The lecturer reads this symbol aloud as "phi", which is the usual convention in Indian mathematical teaching. It is the **empty set**, not the Greek letter $\phi$, and it is written $\varnothing$ throughout these notes. Expect to hear "phi" on the audio at every point where these notes show $\varnothing$.
{% endcapture %}
{% include block.html type="supplement" title="A note on the symbol $\varnothing$" content=supp_phi %}

---

## The definition

{% capture def_topology %}
Let $X$ be a set and let $\tau \subseteq \mathcal{P}(X)$ — that is, $\tau$ is
a collection of subsets of $X$. Then $\tau$ is a **topology on $X$** if it
satisfies the following three conditions:

**(T1)** $\varnothing \in \tau$ and $X \in \tau$.

**(T2)** If $U_1, U_2, \dots, U_n$ are **finitely many** subsets of $X$ with
$U_i \in \tau$ for each $i$, then
$$\bigcap_{i=1}^{n} U_i \in \tau.$$

**(T3)** Let $I$ be **any** set, possibly infinite. If for each $i \in I$ we
are given a subset $U_i \subseteq X$ with $U_i \in \tau$, then
$$\bigcup_{i \in I} U_i \in \tau.$$

When $\tau$ is a topology on $X$ we call the pair $(X, \tau)$ a
**topological space**, and we write "let $(X,\tau)$ be a topological space".
{% endcapture %}
{% include block.html type="definition" title="Definition 1.1 (Topology, topological space)" content=def_topology %}

The lecturer stresses two points, and they are the heart of the definition.

**In (T2) the collection is finite.** Only finitely many $U_i$ may be
intersected.

**In (T3) the collection may be infinite.** Any index set $I$ at all is
permitted, of any size.

{% capture supp_not_required %}
Note also what the definition does **not** require: $X$ carries no distance, no order, no algebraic operation. A topology is a choice of a collection of subsets, and the three conditions are the only constraints on that choice.
{% endcapture %}
{% include block.html type="supplement" title="What the definition does not require" content=supp_not_required %}

{% capture supp_asymmetry %}
It is tempting to read (T2) and (T3) as the same condition with $\cap$ and $\cup$ swapped. They are not. The finiteness restriction in (T2) is essential and cannot be dropped, and the third example in this lecture already shows why — [see the supplement after Example 3](#where-finiteness-in-t2-is-doing-real-work). Every time you meet a topology in this course, the first thing worth asking is where its infinite intersections go wrong.
{% endcapture %}
{% include block.html type="supplement" title="Why the asymmetry is worth marking now" content=supp_asymmetry %}

---

## Example 1 — The trivial topology

{% capture ex1_content %}
Let $X$ be any set and put
$$\tau = \lbrace\, \varnothing,\; X \,\rbrace.$$
This collection has exactly two elements. Then $\tau$ is a topology on $X$,
called the **trivial topology**.
{% endcapture %}
{% include block.html type="example" title="Example 1 (Trivial topology)" content=ex1_content %}

{% capture ex1_proof %}
Let us check the three defining conditions.

**(T1).** The first condition was that $\tau$ should contain the empty set and $X$. Clearly $\tau$ contains the empty set $\varnothing$ and the set $X$. So the first condition is satisfied. ✓

**(T2).** The second condition for being a topology was that if we take finitely many elements $U_1, U_2, \dots, U_n$ in $\tau$, then their intersection $\bigcap_{i=1}^n U_i$ should be in $\tau$.

In this case, an element of $\tau$ is either the empty set or the full set $X$.
- *Case (a):* First consider the case where any one of the $U_i$ is the empty set. Then the intersection $\bigcap_{i=1}^n U_i = \varnothing$, and so is in $\tau$.
- *Case (b):* If this does not happen, the only other possibility is that all the $U_i$ are equal to $X$. In this case also, the intersection $\bigcap_{i=1}^n U_i = X$, and so is in $\tau$.

Therefore, the second condition is also satisfied. ✓

**(T3).** Finally, let us check the third condition. The third condition says that let $I$ be any set, and assume that for each $i \in I$ we are given an element $U_i \in \tau$. We need to show that the arbitrary union $\bigcup_{i \in I} U_i$ is in $\tau$.

Since each $U_i$ is either $\varnothing$ or $X$, we again consider two cases:
- *Case (a):* If all the $U_i$ are empty sets, then the union $\bigcup_{i \in I} U_i = \varnothing$, which is in $\tau$.
- *Case (b):* Otherwise, there exists some index $j \in I$ such that $U_j = X$. Then the union $\bigcup_{i \in I} U_i = X$, which is in $\tau$.

Therefore, the third condition is also satisfied. ✓

This shows that $\tau = \lbrace\varnothing, X\rbrace$ satisfies all three defining conditions to be a topology on $X$. Thus $\tau$ defines a topology on $X$, and this is called the trivial topology. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Example 1" content=ex1_proof %}

---

## Example 2 — The discrete topology

{% capture ex2_content %}
Let $X$ be any set and put
$$\tau = \mathcal{P}(X),$$
the whole power set. Then $\tau$ is a topology on $X$, called the
**discrete topology**.
{% endcapture %}
{% include block.html type="example" title="Example 2 (Discrete topology)" content=ex2_content %}

{% capture ex2_proof %}
Once again, to check that $\tau$ defines a topology on $X$, we need to check that $\tau$ satisfies the three defining conditions. Let us check them one by one.

**(T1).** Clearly, $\tau$ contains the empty set $\varnothing$ and $X$ because $\tau$ is all of the power set $\mathcal{P}(X)$, and the power set contains $\varnothing$ and $X$. So this condition is satisfied. ✓

**(T2).** The second condition is that if we take finitely many subsets $U_1, U_2, \dots, U_n$ of $X$ which are in $\tau$, then their intersection should be in $\tau$:
$$\bigcap_{i=1}^n U_i \in \tau.$$
This condition is also satisfied because the intersection $\bigcap_{i=1}^n U_i$ is a subset of $X$. It is in the power set $\mathcal{P}(X)$, which is equal to $\tau$. So therefore, the second condition is also satisfied. ✓

**(T3).** Similarly, the third condition is satisfied. Let $I$ be any set, and suppose we are given for each $i \in I$ a subset $U_i \subseteq X$ which is in $\tau$. Then we need to show that the union is in $\tau$:
$$\bigcup_{i \in I} U_i \in \tau.$$
Again, exactly as in the previous point, this is clear, as the union $\bigcup_{i \in I} U_i$ is a subset of $X$ and so is a member of the power set $\mathcal{P}(X)$, which is equal to $\tau$. So the third condition is also satisfied. ✓

Therefore, $\tau = \mathcal{P}(X)$ satisfies all three conditions and defines a topology on $X$, which is called the discrete topology. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Example 2" content=ex2_proof %}

{% capture supp_extremes %}
These first two examples are the smallest and the largest topologies available on a given set $X$. Any topology $\tau$ on $X$ must contain $\varnothing$ and $X$ by (T1), so $\lbrace\varnothing, X\rbrace \subseteq \tau$; and $\tau$ is by definition a collection of subsets of $X$, so $\tau \subseteq \mathcal{P}(X)$. Every topology on $X$ therefore sits between the trivial and the discrete topology.

{% include figure.html
   src="point-set-topology/lecture-01/topology-lattice-abc.svg"
   caption="Every topology on $X=\lbrace a,b,c\rbrace$ contains $\lbrace\varnothing, X\rbrace$ and is contained in $\mathcal{P}(X)$; the trivial and discrete topologies form the universal lower and upper bounds in the inclusion lattice. (Structure diagram — not drawn on the lecture board.)"
   alt="A Hasse diagram showing topologies on a three-element set ordered by inclusion, with the trivial topology at the bottom and the discrete topology at the top." %}
{% endcapture %}
{% include block.html type="supplement" title="The two extremes" content=supp_extremes %}

---

## Example 3 — The finite complement topology

This one is, in the lecturer's words, a little more interesting.

{% capture ex3_content %}
Let $X$ be any set and put
$$\tau = \lbrace\, U \subseteq X \;:\; U = \varnothing \ \text{ or } \ X \setminus U \text{ is a finite set} \,\rbrace.$$
Then $\tau$ is a topology on $X$, called the **finite complement topology**.
{% endcapture %}
{% include block.html type="example" title="Example 3 (Finite complement topology)" content=ex3_content %}

{% capture ex3_proof %}
For this $\tau$, let us check that it satisfies the three defining conditions for a topology.

**(T1).** Recall that the first condition we need to check was that $\varnothing$ and $X$ are in $\tau$. Clearly $\varnothing \in \tau$ by the definition of $\tau$. And also, since the complement $X \setminus X = \varnothing$ is a finite set of cardinality zero, $X$ satisfies the second clause, which implies that $X \in \tau$. Therefore, the first condition is satisfied. ✓

**(T2).** The second condition was the following: if $U_1, U_2, \dots, U_n$ are elements in $\tau$, then we need to show that their intersection is also in $\tau$:
$$\bigcap_{i=1}^n U_i \in \tau.$$
Let us first consider the case where one of the $U_i$ is empty. In this case, the intersection $\bigcap_{i=1}^n U_i = \varnothing$, and so is in $\tau$.

If this does not happen, the other possibility is that $U_i$ is non-empty for all $i = 1, \dots, n$. In this case, for each $i$, the complement $X \setminus U_i$ is a finite set. Now let us consider the complement of this finite intersection. Some simple set theory shows that this is equal to:
$$X \setminus \bigcap_{i=1}^n U_i = \bigcup_{i=1}^n \bigl(X \setminus U_i\bigr).$$
As each $X \setminus U_i$ is a finite set, their finite union is also a finite set. Thus $X \setminus \bigcap_{i=1}^n U_i$ is a finite set, which implies that $\bigcap_{i=1}^n U_i \in \tau$.

So this shows that $\tau$ satisfies the second condition for being a topology. ✓

**(T3).** Finally, let us check the third condition. Let $I$ be any set, and suppose that for each $i \in I$ we are given a subset $U_i \in \tau$. We have to check that the arbitrary union is in $\tau$:
$$\bigcup_{i \in I} U_i \in \tau.$$
Once again, we consider two cases:
- *Case (a):* First consider the case when all the $U_i$ are the empty set. In this case, clearly the union $\bigcup_{i \in I} U_i = \varnothing$, which is in $\tau$.
- *Case (b):* If this does not happen, the other possibility is that there is at least one index $j \in I$ for which $U_j$ is non-empty. This implies that $X \setminus U_j$ is a finite set. As before, let us consider the complement of the union:
$$X \setminus \bigcup_{i \in I} U_i = \bigcap_{i \in I} \bigl(X \setminus U_i\bigr).$$
This intersection is obviously contained in each of these subsets, so in particular:
$$X \setminus \bigcup_{i \in I} U_i \subseteq X \setminus U_j,$$
which is a finite set. A subset of a finite set is finite, so $X \setminus \bigcup_{i \in I} U_i$ is a finite set, which implies that $\bigcup_{i \in I} U_i \in \tau$.

Therefore, $\tau$ satisfies the third condition also. ✓

Thus we see that $\tau$ satisfies all three conditions which define a topology on $X$, called the finite complement topology. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Example 3" content=ex3_proof %}

{% capture supp_demorgan %}
Both (T2) and (T3) above turn on one identity, which the lecturer passes over as "some simple set theory". These are De Morgan's laws in their general form. For any family $\lbrace A_i\rbrace_{i \in I}$ of subsets of $X$:
$$X \setminus \bigcap_{i \in I} A_i = \bigcup_{i \in I} (X \setminus A_i), \qquad X \setminus \bigcup_{i \in I} A_i = \bigcap_{i \in I} (X \setminus A_i).$$
Both hold for arbitrary $I$, finite or not. To see the first: $x$ fails to lie in every $A_i$ exactly when $x$ fails to lie in at least one of them. The second is the same statement with the roles reversed.
{% endcapture %}
{% include block.html type="supplement" title="The set-theoretic step used twice" content=supp_demorgan %}

{% capture supp_finiteness %}
The finite complement topology already shows that (T2) would be *false* if arbitrary intersections were allowed. Take $X = \mathbb{Z}$ and, for each $n \geq 1$, put
$$U_n = \mathbb{Z} \setminus \lbrace n\rbrace.$$
Each $U_n$ has complement $\lbrace n\rbrace$, a one-element set, so each $U_n \in \tau$. Their intersection over all $n \geq 1$ is
$$\bigcap_{n \geq 1} U_n = \mathbb{Z} \setminus \lbrace 1, 2, 3, \dots\rbrace,$$
which is non-empty (it contains $0$ and every negative integer) and whose complement $\lbrace 1,2,3,\dots\rbrace$ is infinite. So this intersection satisfies neither clause of the definition and does **not** lie in $\tau$.

Notice how narrowly the argument in (T2) actually depended on finiteness: a union of finitely many finite sets is finite, but a union of infinitely many finite sets need not be.

{% include figure.html
   src="point-set-topology/lecture-01/finite-complement-on-Z.svg"
   caption="Left: an open set in $(\mathbb{Z}, \tau_{\text{fc}})$ contains all integers except a finite subset $\lbrace -1, 1, 2\rbrace$. Right: a countable intersection $\bigcap_{n \geq 1} (\mathbb{Z} \setminus \lbrace n\rbrace) = \mathbb{Z} \setminus \lbrace 1, 2, 3, \dots\rbrace$ produces a set with infinite complement escaping $\tau_{\text{fc}}$, demonstrating why axiom (T2) strictly requires finite intersections. (Structure diagram — not drawn on the lecture board.)"
   alt="Two-panel diagram showing open sets in the finite-complement topology on integers, and an infinite intersection of open sets whose complement is infinite, failing the definition." %}
{% endcapture %}
{% include block.html type="supplement" title="Where finiteness in (T2) is doing real work" content=supp_finiteness %}

{% capture supp_obs %}
If $X$ is itself a finite set, then every subset of $X$ has finite complement, so the finite complement topology is the whole power set — that is, it coincides with the discrete topology of Example 2. The finite complement topology is only a genuinely new construction when $X$ is infinite.
{% endcapture %}
{% include block.html type="supplement" title="A small observation" content=supp_obs %}

---

## Where the lecture ends

The lecturer closes by observing what has been established: given **any** set
$X$, with no structure of any kind, we have now seen three topologies that can
be placed on it.

He then states what comes next: the following lecture turns to specific
examples that will be met repeatedly through the course — meaning the standard
topology on the real line.

---

## Exercises

The lecturer sets no explicit exercise in this lecture.

{% capture ex11_content %}
Let $X = \lbrace a, b, c\rbrace$. Write down the trivial topology and the discrete topology on $X$, and count the elements of each. Then find a topology on $X$ that is neither.
{% endcapture %}
{% capture ex11_sol %}
Trivial: $\lbrace\varnothing, X\rbrace$, two elements. Discrete: $\mathcal{P}(X)$, eight elements. One topology in between is $\tau = \lbrace\varnothing, \lbrace a\rbrace, X\rbrace$: condition (T1) holds; the only intersections and unions to check involve $\varnothing$, $\lbrace a\rbrace$ and $X$, and each returns one of those three sets.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 1.1 (not from the lecture — for practice)" content=ex11_content solution=ex11_sol %}

---

## At a glance

<div class="at-a-glance-box">
  <h3>Key Statements &amp; Definitions</h3>
  <ul>
    <li>
      <a href="#definition-1-1-topology-topological-space">Definition 1.1 (Topology &amp; Topological Space)</a>:
      A collection $\tau \subseteq \mathcal{P}(X)$ containing $\varnothing$ and $X$ ((T1)), closed under finite intersections ((T2)), and closed under arbitrary unions ((T3)).
    </li>
    <li>
      <a href="#example-1-trivial-topology">Example 1 (Trivial Topology)</a>:
      $\tau = \lbrace\varnothing, X\rbrace$ is the coarsest (smallest) topology on any set $X$.
    </li>
    <li>
      <a href="#example-2-discrete-topology">Example 2 (Discrete Topology)</a>:
      $\tau = \mathcal{P}(X)$ is the finest (largest) topology on any set $X$; every subset is open.
    </li>
    <li>
      <a href="#example-3-finite-complement-topology">Example 3 (Finite Complement Topology)</a>:
      $\tau = \lbrace U \subseteq X : U = \varnothing \text{ or } X \setminus U \text{ is finite}\rbrace$ is a topology on any set $X$; on infinite sets it demonstrates why axiom (T2) requires finiteness.
    </li>
  </ul>
</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §12.** The same definition, with the three
conditions in the same order. Munkres calls the members of $\tau$ open sets
straight away, which this course does at the start of Lecture 3.

**Munkres, §12, Example 3.** The finite complement topology, there written
$\mathcal{T}_f$, with the same proof structure. Worth reading immediately
after Example 3 above, as a second voice on the same argument.

**Mendelson, *Introduction to Topology*, Ch. 3 §1.** The gentlest available
treatment of the definition, with more elementary examples on small finite
sets — useful if the three conditions still feel abstract.

**Kumaresan, *Topology of Metric Spaces*, Ch. 1.** Approaches the same
material from metric spaces first, which is the route the next lecture takes
in spirit when it constructs the standard topology on $\mathbb{R}$.
