---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 12
title: "The Closure of a Subset: Definition, Properties, and Examples"
coverage: >
  Solves the exercise from Lecture 11 proving singletons in Euclidean space are
  closed. Defines the closure of a subset via neighbourhood intersection and computes
  explicit closures of open intervals and open discs. Proves that the closure of any
  subset is closed, that a subset is closed if and only if it equals its closure,
  and that closure is idempotent. Establishes that the closure is the smallest closed
  subset containing a given subset.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 1
depends_on:
  - lecture: 11
    title: "Closed Sets, Dual Axioms, and Preimages"
    relationship: "Supplies the definition of closed sets and the exercise that points in Euclidean space are closed."
used_in:
  - lecture: 13
    title: "Dense Subsets, Subspace Closed Sets, and the Pasting Lemma"
    relationship: "Lecture 13 defines dense subsets via closure (A dense in X iff cl(A) = X) and proves A is dense in cl(A)."
notation:
  - symbol: "$\\overline{A}$"
    gloss: 'The closure of subset $A$ in topological space $X$'
  - symbol: "$\\overline{\\overline{B}}$"
    gloss: 'Iterated closure $\\overline{\\overline{B}} = \\overline{B}$ (idempotence)'
prev: lecture-11
next: lecture-13
---

# Lecture 12 — The Closure of a Subset: Definition, Properties, and Examples

## Where we are

In [Lecture 11]({{ site.baseurl }}/point-set-topology/lecture-11/), we defined closed subsets as complements of open sets and established the three dual axioms governing closed families. We proved that a map is continuous if and only if preimages of closed sets are closed, and used polynomial maps to demonstrate that spheres and classical matrix groups are closed or open. We concluded with the claim that singletons in $\mathbb{R}^m$ are closed.

Here we begin by providing the complete proof of that closing exercise, showing that every point in $\mathbb{R}^m$ has an open complement. We then introduce the central concept of the **closure** of an arbitrary subset $A \subseteq X$. We compute concrete examples on the real line and in the plane, showing how closure attaches the boundary to open intervals and discs. We prove three structural theorems: the closure $\overline{A}$ is always a closed set, a set is closed if and only if it equals its closure, and taking the closure is idempotent ($\overline{\overline{B}} = \overline{B}$). Finally, we show that $\overline{A}$ is the smallest closed set containing $A$.

---

## Solved exercise: singletons in $\mathbb{R}^m$ are closed

We open by settling the exercise left at the conclusion of Lecture 11.

### Lemma 12.1 (Points in $\mathbb{R}^m$ are closed) {#lemma-12-1-points-in-rm-are-closed}

{% capture lem121_content %}
Let $a = (a_1, \dots, a_m) \in \mathbb{R}^m$.
Then the singleton $\lbrace a \rbrace$ is a closed subset of $\mathbb{R}^m$, or equivalently, the complement $\mathbb{R}^m \setminus \lbrace a \rbrace$ is an open subset of $\mathbb{R}^m$.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 12.1 (Points in $\mathbb{R}^m$ are Closed)" content=lem121_content %}

{% capture lem121_proof %}
So let us do this exercise. We want to show that the complement of this point is an open subset.

Let $x = (x_1, \dots, x_m) \in \mathbb{R}^m \setminus \lbrace a \rbrace$.
Because $x \ne a$, there exists at least one coordinate index $i \in \lbrace 1, \dots, m \rbrace$ such that $x_i \ne a_i$.
Let $\varepsilon = |x_i - a_i| > 0$.

We claim that the basic open hypercube $S_{\varepsilon/4}(x)$ is completely contained inside $\mathbb{R}^m \setminus \lbrace a \rbrace$.
So let us prove this.
Suppose $y = (y_1, \dots, y_m) \in S_{\varepsilon/4}(x)$. Then in the $i$-th coordinate:
$$|y_i - x_i| < \frac{\varepsilon}{4}.$$
But then this implies that $y_i \ne a_i$, because if $y_i = a_i$, we would have $|a_i - x_i| < \frac{\varepsilon}{4}$, which would mean $\varepsilon < \frac{\varepsilon}{4}$, an impossibility since $\varepsilon > 0$.
So therefore, this implies that $y \in \mathbb{R}^m \setminus \lbrace a \rbrace$.
This shows that $S_{\varepsilon/4}(x) \subseteq \mathbb{R}^m \setminus \lbrace a \rbrace$.

So this proves that given any point in the complement, we have found a basic open subset containing that point which is completely contained inside the complement.
So therefore, the complement $\mathbb{R}^m \setminus \lbrace a \rbrace$ is open.
Which implies, by the definition of a closed subset, that the singleton $\lbrace a \rbrace$ is a closed subset. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 12.1" content=lem121_proof %}

---

## The closure of a subset

We now introduce the closure of an arbitrary subset of a topological space.

### Definition 12.2 (Closure of a subset) {#definition-12-2-closure-of-a-subset}

{% capture def122_content %}
Let $X$ be a topological space, and let $A \subseteq X$ be any subset.
The **closure** of $A$ in $X$, denoted $\overline{A}$, is defined as:
$$\overline{A} = \lbrace x \in X \;:\; \text{for every open set } U \subseteq X \text{ with } x \in U,\; U \cap A \ne \varnothing \rbrace.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 12.2 (Closure of a Subset)" content=def122_content %}

{% capture rem_containment %}
#### Immediate containment $A \subseteq \overline{A}$
If $x \in A$, then every open set $U$ containing $x$ satisfies $x \in U \cap A$, so $U \cap A \ne \varnothing$.
Therefore, every point of $A$ belongs to $\overline{A}$:
$$A \subseteq \overline{A}.$$
{% endcapture %}
{% include block.html type="supplement" title="Immediate containment $A \subseteq \overline{A}$" content=rem_containment %}

---

## Examples: intervals and discs

### Example 1: Closure of an open interval in $\mathbb{R}$ {#example-1-closure-of-open-interval}

{% capture ex1_content %}
Consider the real line $\mathbb{R}$ with the standard topology, and let $A = (0, 1)$ be the open unit interval.
We compute the closure $\overline{A}$:

1. **Points strictly outside $[0, 1]$:**
   - If $x < 0$, let $\varepsilon = |x| = -x > 0$. The open interval $B_\varepsilon(x) = (x - \varepsilon, x + \varepsilon) = (2x, 0)$ contains $x$ and is disjoint from $(0, 1)$. Since there exists an open neighbourhood of $x$ not meeting $A$, we have $x \notin \overline{A}$.
   - If $x > 1$, let $\varepsilon = x - 1 > 0$. The open interval $B_\varepsilon(x) = (1, 2x - 1)$ contains $x$ and is disjoint from $(0, 1)$. Hence $x \notin \overline{A}$.
   Therefore $\overline{A} \subseteq [0, 1]$.

2. **The boundary points $0$ and $1$:**
   - Let $x = 0$. Let $U$ be any open set in $\mathbb{R}$ containing $0$. By the definition of the standard topology, there exists $\varepsilon > 0$ such that $B_\varepsilon(0) = (-\varepsilon, \varepsilon) \subseteq U$.
     Choose $\delta = \min(\varepsilon/2, 1/2) > 0$. Then $\delta \in (-\varepsilon, \varepsilon) \subseteq U$ and $\delta \in (0, 1) = A$.
     Thus $U \cap A \ne \varnothing$, which shows that $0 \in \overline{A}$.
   - Similarly, for $x = 1$, any open neighbourhood $U$ contains $B_\varepsilon(1) = (1 - \varepsilon, 1 + \varepsilon)$, which contains $1 - \min(\varepsilon/2, 1/2) \in (0, 1)$. Thus $1 \in \overline{A}$.

Since $A = (0, 1) \subseteq \overline{A}$ and the boundary points $0, 1 \in \overline{A}$, we conclude:
$$\overline{(0, 1)} = [0, 1].$$
{% endcapture %}
{% include block.html type="example" title="Example 1 (Closure of an Open Interval)" content=ex1_content %}

{% include figure.html
   src="point-set-topology/lecture-12/closure-open-interval.svg"
   caption="Computing the closure of $(0, 1)$ in $\mathbb{R}$. Exterior points have disjoint neighbourhoods; boundary points $0$ and $1$ meet $(0, 1)$ in every neighbourhood; hence $\overline{(0, 1)} = [0, 1]$."
   alt="Number line showing open interval (0,1), exterior points with disjoint intervals, boundary points with overlapping intervals, and closure [0,1]." %}

---

### Example 2: Closure of the open unit disc in $\mathbb{R}^2$ {#example-2-closure-of-open-disc}

{% capture ex2_content %}
In $\mathbb{R}^2$ equipped with the standard topology, consider the open unit disc:
$$A = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x^2 + y^2 < 1 \rbrace.$$
- If $(a, b) \in \mathbb{R}^2$ satisfies $a^2 + b^2 > 1$, let $d = \sqrt{a^2 + b^2} > 1$. Setting $\varepsilon = (d - 1)/2 > 0$, the basic open square $S_\varepsilon(a, b)$ is entirely exterior to the unit disc, so $S_\varepsilon(a, b) \cap A = \varnothing$. Hence $(a, b) \notin \overline{A}$.
- If $(a, b) \in \mathbb{R}^2$ satisfies $a^2 + b^2 = 1$ (the boundary circle), then for every $\varepsilon > 0$, scaling towards the origin $(1 - \delta)(a, b)$ with $\delta > 0$ sufficiently small produces points in $S_\varepsilon(a, b) \cap A \ne \varnothing$. Hence $(a, b) \in \overline{A}$.

Thus the closure of the open disc is the **closed unit disc**:
$$\overline{\lbrace (x, y) \in \mathbb{R}^2 : x^2 + y^2 < 1 \rbrace} = \lbrace (x, y) \in \mathbb{R}^2 \;:\; x^2 + y^2 \le 1 \rbrace.$$
Taking the closure adds the boundary circle $S^1$ to the interior.
{% endcapture %}
{% include block.html type="example" title="Example 2 (Closure of the Open Unit Disc)" content=ex2_content %}

{% include figure.html
   src="point-set-topology/lecture-12/closure-open-disc.svg"
   caption="The closure of the open unit disc $A = \lbrace x^2+y^2 < 1 \rbrace$ adds the boundary circle $S^1$, producing the closed disc $\overline{A} = \lbrace x^2+y^2 \le 1 \rbrace$."
   alt="Two diagrams showing the open disc with dashed boundary, and the closed disc with solid boundary." %}

---

## Fundamental properties of the closure

We now establish the three fundamental theorems governing the closure operation.

### Lemma 12.3 (The closure is closed) {#lemma-12-3-the-closure-is-closed}

{% capture lem123_content %}
Let $X$ be a topological space and let $A \subseteq X$ be any subset.
Then the closure $\overline{A}$ is a **closed subset** of $X$.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 12.3 (The Closure is Closed)" content=lem123_content %}

{% capture lem123_proof %}
So let us prove this.

It suffices to show that the complement $X \setminus \overline{A}$ is open in $X$. The definition of a closed subset was that the complement should be open, so that is what we are going to show.

So let $x \in X \setminus \overline{A}$.
That is, $x \notin \overline{A}$. But then by definition, there exists an open set $U_x$ containing $x$ such that:
$$U_x \cap A = \varnothing.$$
Now if $y \in U_x$, then $y$ has an open subset, namely $U_x$ itself, which does not meet $A$.
Thus $y \notin \overline{A}$.
So therefore, we have proved that $U_x$ is completely contained inside $X \setminus \overline{A}$:
$$U_x \subseteq X \setminus \overline{A}.$$

Thus, for every $x \in X \setminus \overline{A}$, we have found an open set $U_x$ containing $x$ such that $U_x \subseteq X \setminus \overline{A}$.
So therefore, this implies that we can write the complement as a union:
$$X \setminus \overline{A} = \bigcup_{x \in X \setminus \overline{A}} U_x.$$
And each of these is open, and an arbitrary union of open sets is open (axiom (T3)), so this implies that $X \setminus \overline{A}$ is open.

Hence $\overline{A}$ is closed in $X$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 12.3" content=lem123_proof %}

{% include figure.html
   src="point-set-topology/lecture-12/closure-is-closed-neighborhood.svg"
   caption="Proof of Lemma 12.3: every point $x \in X \setminus \overline{A}$ has an open neighbourhood $U_x$ disjoint from $A$. Any point $y \in U_x$ also has $U_x \cap A = \varnothing$, showing $U_x \subseteq X \setminus \overline{A}$, so the complement is open."
   alt="Venn diagram showing space X, subset A, closure cl(A), and point x in complement with neighborhood U_x inside complement." %}

---

### Proposition 12.4 (Characterization of closed sets via closure) {#proposition-12-4-characterization-of-closed-sets-via-closure}

{% capture prop124_content %}
Let $X$ be a topological space and let $A \subseteq X$ be a subset.
Then $A$ is a closed subset of $X$ if and only if:
$$A = \overline{A}.$$
{% endcapture %}
{% include block.html type="proposition" title="Proposition 12.4 (Characterization of Closed Sets via Closure)" content=prop124_content %}

{% capture prop124_proof %}
So let us prove this.

**$(\implies)$ First let us assume that $A$ is closed.**
We need to show that $A = \overline{A}$.
Since $A \subseteq \overline{A}$ is already known (from the remark following the definition), it is enough to show the reverse inclusion:
$$\overline{A} \subseteq A.$$
To show this, taking complements, it suffices to show that:
$$X \setminus A \subseteq X \setminus \overline{A},$$
and this is what we are going to prove.

Let $x \in X \setminus A$.
As $A$ is closed, it follows from the definition that $X \setminus A$ is open.
So let us denote this open subset by $U = X \setminus A$.
Then there is an open subset, namely $U$, which contains $x$, and such that $U \cap A = \varnothing$.
Thus $x$ does not belong to $\overline{A}$, by definition of the closure.
So this implies that $x \in X \setminus \overline{A}$.
So thus we have proved that $X \setminus A \subseteq X \setminus \overline{A}$, which proves $\overline{A} \subseteq A$.
So this implies that $A = \overline{A}$. That was one direction of the proposition.

**$(\impliedby)$ Next let us assume that $A = \overline{A}$.**
We want to show that $A$ is closed.
By the previous lemma ([Lemma 12.3](#lemma-12-3-the-closure-is-closed)), the closure $\overline{A}$ is closed in $X$.
And since $A = \overline{A}$, thus $A$ is closed in $X$, which is exactly what we wanted to prove.

So this completes the proof of the proposition. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 12.4" content=prop124_proof %}

{% capture corr12_content %}
**Transcript statement:** In sentence 176, the transcript states: *"It's, it is enough to show that $A$ closure is contained in $U$."*
**Correction:** The target inclusion is $\overline{A} \subseteq A$. The set $U$ has not been introduced at that point; eight sentences later (sentence 184), the lecturer defines $U = X \setminus A$ as the open complement. The argument proves that $x \in X \setminus A \implies x \in X \setminus \overline{A}$, which is equivalent to $\overline{A} \subseteq A$.
{% endcapture %}
{% include block.html type="correction" title="Correction Note (Target Inclusion for Equality with Closure)" content=corr12_content %}

---

### Corollary 12.5 (Idempotence of the closure) {#corollary-12-5-idempotence-of-the-closure}

{% capture cor125_content %}
Let $B$ be any subset of a topological space $X$.
Then taking the closure twice yields the same set:
$$\overline{\overline{B}} = \overline{B}.$$
{% endcapture %}
{% include block.html type="corollary" title="Corollary 12.5 (Idempotence of the Closure)" content=cor125_content %}

{% capture cor125_proof %}
So let us see how to prove this.

From the lemma ([Lemma 12.3](#lemma-12-3-the-closure-is-closed)), no matter which subset we take, the closure is always closed in $X$. Applying this lemma, we get that $\overline{B}$ is a closed subset.
And the proposition above ([Proposition 12.4](#proposition-12-4-characterization-of-closed-sets-via-closure)) says that a set is closed if and only if it equals its closure.
Applying the proposition to the closed set $A = \overline{B}$, we get:
$$\overline{B} = \overline{\overline{B}}.$$
So taking closure again makes no difference. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 12.5" content=cor125_proof %}

---

## Exercises

{% capture ex121_content %}
Let $A$ and $B$ be subsets of a topological space $X$ with $A \subseteq B$.
Prove that:
$$\overline{A} \subseteq \overline{B}.$$
{% endcapture %}
{% capture ex121_sol %}
Let $x \in \overline{A}$.
By Definition 12.2, for every open set $U \subseteq X$ containing $x$, we have $U \cap A \ne \varnothing$.
Since $A \subseteq B$, the intersection satisfies:
$$U \cap A \subseteq U \cap B.$$
Because $U \cap A$ is non-empty, $U \cap B$ must also be non-empty.
Since this holds for every open neighbourhood $U$ of $x$, it follows by Definition 12.2 that $x \in \overline{B}$.
Therefore $\overline{A} \subseteq \overline{B}$. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 12.1 (Monotonicity of Closure)" content=ex121_content solution=ex121_sol %}

{% capture ex122_content %}
Let $X$ be a topological space, let $Z \subseteq X$ be a closed subset, and let $A \subseteq X$ be a subset such that $A \subseteq Z$.
Prove that:
$$\overline{A} \subseteq Z.$$
Conclude that $\overline{A}$ is the smallest closed subset of $X$ containing $A$, and that:
$$\overline{A} = \bigcap_{\substack{Z \supseteq A \\ Z \text{ closed}}} Z.$$
{% endcapture %}
{% capture ex122_sol %}
1. By Exercise 12.1, since $A \subseteq Z$, we have $\overline{A} \subseteq \overline{Z}$.
   Since $Z$ is closed, Proposition 12.4 gives $\overline{Z} = Z$.
   Therefore:
   $$\overline{A} \subseteq Z.$$
2. By Lemma 12.3, $\overline{A}$ is closed, and by the remark following Definition 12.2, $A \subseteq \overline{A}$.
   Thus $\overline{A}$ is itself one of the closed sets containing $A$.
   The statement proved in part 1 shows that if $Z$ is *any* closed set containing $A$, then $\overline{A} \subseteq Z$.
   Therefore, $\overline{A}$ is contained in every closed set containing $A$, making it the **unique smallest closed subset** containing $A$.
3. Taking the intersection over all closed sets containing $A$: since $\overline{A}$ is closed and contains $A$, $\bigcap_{Z \supseteq A, Z \text{ closed}} Z \subseteq \overline{A}$. Conversely, since $\overline{A} \subseteq Z$ for every such $Z$, $\overline{A} \subseteq \bigcap Z$. Thus equality holds:
   $$\overline{A} = \bigcap_{\substack{Z \supseteq A \\ Z \text{ closed}}} Z. \qquad \blacksquare$$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 12.2 (Closure as the Smallest Closed Set)" content=ex122_content solution=ex122_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Lemma 12.1 (Points in $\mathbb{R}^m$ are Closed)](#lemma-12-1-points-in-rm-are-closed): Every point in $\mathbb{R}^m$ has an open complement via disjoint basic hypercubes.
- [Definition 12.2 (Closure of a Subset)](#definition-12-2-closure-of-a-subset): $x \in \overline{A}$ iff every open neighbourhood $U$ of $x$ meets $A$; always $A \subseteq \overline{A}$.
- [Example 1 (Closure of an Open Interval)](#example-1-closure-of-open-interval): $\overline{(0, 1)} = [0, 1]$ in $\mathbb{R}$.
- [Example 2 (Closure of the Open Unit Disc)](#example-2-closure-of-open-disc): $\overline{\lbrace x^2+y^2 < 1 \rbrace} = \lbrace x^2+y^2 \le 1 \rbrace$ in $\mathbb{R}^2$.
- [Lemma 12.3 (The Closure is Closed)](#lemma-12-3-the-closure-is-closed): $X \setminus \overline{A}$ is a union of open sets, hence $\overline{A}$ is closed.
- [Proposition 12.4 (Characterization of Closed Sets via Closure)](#proposition-12-4-characterization-of-closed-sets-via-closure): $A$ is closed iff $A = \overline{A}$.
- [Corollary 12.5 (Idempotence of the Closure)](#corollary-12-5-idempotence-of-the-closure): $\overline{\overline{B}} = \overline{B}$.
- [Exercise 12.1 (Monotonicity of Closure)](#exercise-12-1-monotonicity-of-closure): $A \subseteq B \implies \overline{A} \subseteq \overline{B}$.
- [Exercise 12.2 (Closure as Smallest Closed Set)](#exercise-12-2-closure-as-the-smallest-closed-set): $\overline{A} = \bigcap \lbrace Z \text{ closed} : A \subseteq Z \rbrace$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §17.** Closure operation, limit points, interior, and characterization as the intersection of all closed sets containing a subset.

**Morris, *Topology Without Tears*, Chapter 2.** Section 2.2 introduces the closure and proves that $\overline{A}$ is the smallest closed set containing $A$.
