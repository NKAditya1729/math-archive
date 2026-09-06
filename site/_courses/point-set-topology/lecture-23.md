---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 23
title: "Compact Spaces and the Hausdorff Property"
coverage: >
  Opens Part IV of the course by introducing the Hausdorff (T_2) separation axiom
  and proving that Hausdorffness is inherited by products and subspaces. Defines
  compactness via open covers and finite subcovers, highlighting the course-wide
  convention that all compact spaces are assumed to be Hausdorff. Proves that R
  is not compact, and proves that the closed unit interval [0, 1] is compact
  using a supremum argument.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 16
    title: "Connected Spaces and Connected Subsets of the Real Line"
    relationship: "Supplies the supremum construction and least-upper-bound technique on $[0, 1]$."
  - lecture: 4
    title: "Subspaces and the Relative Topology"
    relationship: "Supplies the subspace topology used in proving subspaces of Hausdorff spaces are Hausdorff."
  - lecture: 5
    title: "Product Topology and Metric Topologies"
    relationship: "Supplies basic open sets in the product topology $X \\times Y$."
used_in:
  - lecture: 24
    title: "The Tube Lemma and Products of Compact Spaces"
    relationship: "Supplies compactness and the Hausdorff axiom, which are foundational for the Tube Lemma."
notation:
  - symbol: 'Hausdorff ($T_2$)'
    gloss: 'A topological space where any two distinct points possess disjoint open neighborhoods'
  - symbol: '$\mathcal{U} = \{U_i\}_{i \in I}$'
    gloss: 'An open cover of a topological space $X$'
  - symbol: '$\sup S$'
    gloss: 'The least upper bound of a non-empty subset of $\mathbb{R}$ bounded above'
prev: lecture-22
next: lecture-24
---

# Lecture 23 — Compact Spaces and the Hausdorff Property

Having concluded our study of connectedness in Part III, we now begin **Part IV — Compactness, Quotients, and Separation Axioms**. Questions regarding the connectedness of the matrix groups $SO(n)$ and $U(n)$ require tools from compactness and continuous maps on compact domains, which we will develop over the coming lectures.

In this lecture, we introduce two foundational concepts of point-set topology:
1. The **Hausdorff separation axiom** ($T_2$), ensuring that distinct points can be separated by disjoint open sets.
2. **Compactness**, the topological abstraction of finiteness, defined in terms of open covers and finite subcovers.

We prove that products and subspaces of Hausdorff spaces remain Hausdorff, demonstrate that the real line $\mathbb{R}$ is not compact, and prove that the closed unit interval $[0, 1]$ is compact using a supremum argument.

---

## The Hausdorff separation property

In an arbitrary topological space, open sets may fail to separate distinct points (for example, in the indiscrete topology $\{\varnothing, X\}$ with $|X| \ge 2$, no two points can be separated). The Hausdorff property eliminates such pathological behavior.

### Definition 23.1 (Hausdorff space / $T_2$ space) {#definition-23-1-hausdorff-space}

{% capture def231_content %}
A topological space $(X, \tau)$ is called **Hausdorff** (or a **$T_2$ space**) if for every pair of distinct points $x_1, x_2 \in X$ ($x_1 \ne x_2$), there exist open sets $U_1, U_2 \in \tau$ such that:
$$x_1 \in U_1, \qquad x_2 \in U_2, \qquad \text{and} \qquad U_1 \cap U_2 = \varnothing.$$
{% endcapture %}
{% include block.html type="definition" title="Definition 23.1 (Hausdorff Space)" content=def231_content %}

{% include figure.html
   src="point-set-topology/lecture-23/hausdorff-separation.svg"
   num="23.1"
   caption="The Hausdorff ($T_2$) condition: for any two distinct points $x_1 \ne x_2$ in $X$, there exist disjoint open neighborhoods $U_1$ around $x_1$ and $U_2$ around $x_2$ such that $U_1 \cap U_2 = \varnothing$."
   alt="A topological space X containing points x1 and x2 enclosed in disjoint open sets U1 and U2." %}

---

## Hereditary and product properties of Hausdorff spaces

### Proposition 23.2 (Products of Hausdorff spaces are Hausdorff) {#proposition-23-2-products-of-hausdorff-spaces}

{% capture prop232_content %}
If $X$ and $Y$ are Hausdorff topological spaces, then the product space $X \times Y$, equipped with the product topology, is **Hausdorff**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 23.2 (Binary Products of Hausdorff Spaces)" content=prop232_content %}

{% capture prop232_proof %}
Let $(x_1, y_1)$ and $(x_2, y_2)$ be two distinct points in $X \times Y$:
$$(x_1, y_1) \ne (x_2, y_2).$$
By definition of equality of ordered pairs, this inequality means that at least one coordinate must differ:
$$x_1 \ne x_2 \qquad \text{or} \qquad y_1 \ne y_2.$$

Without loss of generality, assume that the second coordinates differ: $y_1 \ne y_2$.
Since $Y$ is Hausdorff, there exist open sets $V_1, V_2 \in \tau_Y$ such that:
$$y_1 \in V_1, \qquad y_2 \in V_2, \qquad \text{and} \qquad V_1 \cap V_2 = \varnothing.$$

Now consider the cylinder sets in $X \times Y$:
$$W_1 = X \times V_1 \qquad \text{and} \qquad W_2 = X \times V_2.$$
By definition of the product topology ([Lecture 5]({{ site.baseurl }}/point-set-topology/lecture-05/#the-product-topology)), both $W_1$ and $W_2$ are open subsets of $X \times Y$.
Let us verify the separation conditions:
1. **Containment:** Because $x_1 \in X$ and $y_1 \in V_1$, $(x_1, y_1) \in X \times V_1 = W_1$. Similarly, because $x_2 \in X$ and $y_2 \in V_2$, $(x_2, y_2) \in X \times V_2 = W_2$.
2. **Disjointness:** By distributivity of Cartesian products over set intersections:
   $$W_1 \cap W_2 = (X \times V_1) \cap (X \times V_2) = (X \cap X) \times (V_1 \cap V_2) = X \times \varnothing = \varnothing.$$

If instead $x_1 \ne x_2$, the identical argument applied to disjoint open sets $U_1, U_2 \subseteq X$ separating $x_1$ and $x_2$ yields disjoint open sets $U_1 \times Y$ and $U_2 \times Y$ separating $(x_1, y_1)$ and $(x_2, y_2)$.

Thus, any two distinct points in $X \times Y$ can be separated by disjoint open sets.
This proves that $X \times Y$ is Hausdorff. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 23.2" content=prop232_proof %}

{% include figure.html
   src="point-set-topology/lecture-23/hausdorff-product-separation.svg"
   num="23.2"
   caption="Separation in the product space $X \times Y$: when two points differ in their $Y$-coordinates ($y_1 \ne y_2$), disjoint open sets $V_1, V_2 \subseteq Y$ induce disjoint open horizontal strips $X \times V_1$ and $X \times V_2$ in $X \times Y$."
   alt="The Cartesian product X x Y showing two points separated by open strips X x V1 and X x V2." %}

{% capture ex232_content %}
Let $\{X_i\}_{i \in I}$ be any arbitrary family of Hausdorff topological spaces. Show that the Cartesian product $\prod_{i \in I} X_i$, equipped with the product topology, is Hausdorff.

*Hint:* If $(x_i)_{i \in I} \ne (y_i)_{i \in I}$, there exists some coordinate index $j \in I$ such that $x_j \ne y_j$. Use the Hausdorff property of $X_j$ and take preimages under the canonical projection $p_j \colon \prod X_i \to X_j$.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 23.1 (Arbitrary Products of Hausdorff Spaces)" content=ex232_content %}

---

### Proposition 23.3 (Subspaces of Hausdorff spaces are Hausdorff) {#proposition-23-3-subspaces-of-hausdorff-spaces}

{% capture prop233_content %}
Let $X$ be a Hausdorff topological space, and let $Y \subseteq X$ be any subspace equipped with the subspace topology. Then $Y$ is **Hausdorff**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 23.3 (Subspaces of Hausdorff Spaces)" content=prop233_content %}

{% capture prop233_proof %}
Let $y_1, y_2 \in Y$ be two distinct points in the subspace: $y_1 \ne y_2$.
Since $Y \subseteq X$, $y_1$ and $y_2$ are also distinct points of $X$.
Because $X$ is Hausdorff, there exist open sets $U_1, U_2 \in \tau_X$ such that:
$$y_1 \in U_1, \qquad y_2 \in U_2, \qquad \text{and} \qquad U_1 \cap U_2 = \varnothing.$$

Now consider their traces on $Y$:
$$V_1 = U_1 \cap Y \qquad \text{and} \qquad V_2 = U_2 \cap Y.$$
By definition of the subspace topology ([Lecture 4]({{ site.baseurl }}/point-set-topology/lecture-04/#the-subspace-topology)), $V_1$ and $V_2$ are open subsets of $Y$.
Let us verify the conditions:
1. **Containment:** Since $y_1 \in Y$ and $y_1 \in U_1$, we have $y_1 \in U_1 \cap Y = V_1$. Similarly, $y_2 \in U_2 \cap Y = V_2$.
2. **Disjointness:**
   $$V_1 \cap V_2 = (U_1 \cap Y) \cap (U_2 \cap Y) = (U_1 \cap U_2) \cap Y = \varnothing \cap Y = \varnothing.$$

Thus, $V_1$ and $V_2$ are disjoint open subsets of $Y$ separating $y_1$ and $y_2$.
This proves that $Y$ is Hausdorff. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 23.3" content=prop233_proof %}

---

## Standing convention: Hausdorff assumption

> [!IMPORTANT]
> **Standing Course Convention: Compactness is Defined Only for Hausdorff Spaces**
> 
> In this lecture (sentences 58–66), the lecturer establishes the standing convention for the remainder of the course:
> > *"So for the rest of this course we will be interested only in Hausdorff topological spaces. So if nothing is mentioned, then it's safe to assume that the topological space we are working with is Hausdorff... Let $X$ be a Hausdorff topological space. So we shall say that $X$ is compact if..."*
> 
> **Note on textbook divergence:**
> In standard modern textbooks such as Munkres (§26), Morris (Chapter 7), and Simmons, compactness is defined for **any** topological space via the open cover condition, without requiring the space to be Hausdorff (spaces satisfying both are referred to as "compact Hausdorff" spaces, while in the French/Bourbaki tradition, spaces with the finite-subcover property alone are called "quasi-compact").
> 
> In this course, **every compact space is Hausdorff by definition**. A reader consulting Munkres or Morris must keep this convention in mind: theorems stated in later lectures as *"a compact subspace of a space is closed"* or *"a continuous bijection from a compact space is a homeomorphism"* rely fundamentally on the ambient or domain spaces being Hausdorff.

---

## Compactness

We now define compactness. Intuitively, compactness is the topological analogue of finiteness: it allows one to pass from an arbitrary (potentially infinite or uncountable) collection of local open approximations to a finite subcollection that still covers the entire space.

### Definition 23.4 (Open cover and compactness) {#definition-23-4-compact-space}

{% capture def234_content %}
Let $X$ be a Hausdorff topological space.
1. An **open cover** of $X$ is an indexed family of open sets $\mathcal{U} = \{U_i\}_{i \in I}$ in $X$ such that:
   $$\bigcup_{i \in I} U_i = X.$$
2. A **finite subcover** of $\mathcal{U}$ is a finite subcollection $\{U_{i_1}, U_{i_2}, \dots, U_{i_n}\} \subseteq \mathcal{U}$ such that:
   $$\bigcup_{j=1}^n U_{i_j} = X.$$
3. The space $X$ is called **compact** if **every** open cover of $X$ admits a finite subcover.
{% endcapture %}
{% include block.html type="definition" title="Definition 23.4 (Open Cover and Compactness)" content=def234_content %}

---

## Non-compactness of $\mathbb{R}$

To demonstrate that a space is not compact, it suffices to construct a single open cover that admits no finite subcover.

### Example 23.5 ($\mathbb{R}$ is not compact) {#example-23-5-r-is-not-compact}

{% capture eg235_content %}
The real line $\mathbb{R}$, equipped with the standard topology, is **not compact**.
{% endcapture %}
{% include block.html type="example" title="Example 23.5 ($\mathbb{R}$ is Not Compact)" content=eg235_content %}

{% capture eg235_proof %}
To show that $\mathbb{R}$ is not compact, it suffices to produce an open cover of $\mathbb{R}$ that has no finite subcover.

For each integer $n \in \mathbb{Z}$, define the open interval:
$$U_n = \left(n - \frac{1}{4}, \; n + 1 + \frac{1}{4}\right) = \left(n - \frac{1}{4}, \; n + \frac{5}{4}\right).$$
Each $U_n$ is an open subset of $\mathbb{R}$.
For each $n \in \mathbb{Z}$, the closed interval $[n, n+1]$ is contained in $U_n$:
$$[n, n+1] \subseteq \left(n - \frac{1}{4}, \; n + \frac{5}{4}\right) = U_n.$$
Since every real number $x \in \mathbb{R}$ lies in $[n, n+1]$ for $n = \lfloor x \rfloor$, we have:
$$\bigcup_{n \in \mathbb{Z}} U_n = \mathbb{R}.$$
Thus $\mathcal{U} = \{U_n\}_{n \in \mathbb{Z}}$ is an open cover of $\mathbb{R}$.

Now let $\{U_{n_1}, U_{n_2}, \dots, U_{n_k}\}$ be any finite subcollection of $\mathcal{U}$.
Let:
$$N_{\min} = \min \lbrace n_1, \dots, n_k \rbrace \qquad \text{and} \qquad N_{\max} = \max \lbrace n_1, \dots, n_k \rbrace.$$
Then the union of this finite subcollection satisfies:
$$\bigcup_{j=1}^k U_{n_j} \subseteq \left(N_{\min} - \frac{1}{4}, \; N_{\max} + \frac{5}{4}\right).$$
This union is a bounded open interval, whereas $\mathbb{R}$ is unbounded.
Specifically, any real number $x \ge N_{\max} + 2$ is not in the union:
$$x \notin \bigcup_{j=1}^k U_{n_j}.$$
Therefore, no finite subcollection of $\mathcal{U}$ can cover $\mathbb{R}$.
This proves that the open cover $\mathcal{U}$ has no finite subcover, and consequently $\mathbb{R}$ is not compact. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Example 23.5" content=eg235_proof %}

---

## Compactness of the unit interval $[0, 1]$

We now establish one of the fundamental theorems of analysis and topology: the closed unit interval $[0, 1]$ is compact. The proof mirrors the supremum technique used in [Lecture 16]({{ site.baseurl }}/point-set-topology/lecture-16/#theorem-16-1-the-unit-interval-is-connected) to establish connectedness.

### Theorem 23.6 (The unit interval $[0, 1]$ is compact) {#theorem-23-6-unit-interval-is-compact}

{% capture thm236_content %}
The closed unit interval $[0, 1] \subseteq \mathbb{R}$, equipped with the subspace topology from the standard topology on $\mathbb{R}$, is **compact**.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 23.6 (Compactness of $[0, 1]$)" content=thm236_content %}

{% capture thm236_proof %}
Let $\mathcal{U} = \{U_i\}_{i \in I}$ be an arbitrary open cover of $[0, 1]$.
We must show that $\mathcal{U}$ admits a finite subcover.

Consider the set:
$$S = \lbrace x \in [0, 1] : [0, x] \text{ is covered by a finite subcollection of } \mathcal{U} \rbrace.$$

**Step 1: $S$ is non-empty.**
We show that $0 \in S$. The interval $[0, 0]$ is simply the singleton $\{0\}$.
Because $\mathcal{U}$ covers $[0, 1]$ and $0 \in [0, 1]$, there exists some index $i_0 \in I$ such that $0 \in U_{i_0}$.
Then $[0, 0] = \{0\} \subseteq U_{i_0}$.
Thus $[0, 0]$ is covered by a single member of $\mathcal{U}$, which means that $0 \in S$.
Therefore $S \ne \varnothing$.

**Step 2: Existence of the supremum.**
By definition, $S \subseteq [0, 1]$, so $S$ is bounded above by $1$.
Since $S$ is a non-empty subset of $\mathbb{R}$ that is bounded above, the completeness of the real numbers implies that $S$ has a least upper bound:
$$x_0 = \sup S \in [0, 1].$$

**Step 3: The supremum $x_0$ belongs to $S$.**
We claim that $x_0 \in S$.
Since $x_0 \in [0, 1]$ and $\mathcal{U}$ covers $[0, 1]$, there exists an index $i_0 \in I$ such that:
$$x_0 \in U_{i_0}.$$
Because $U_{i_0}$ is open in the subspace topology on $[0, 1]$, there exists $\varepsilon > 0$ such that:
$$(x_0 - \varepsilon, \; x_0 + \varepsilon) \cap [0, 1] \subseteq U_{i_0}.$$
By the defining property of the supremum, $x_0 - \varepsilon$ is not an upper bound for $S$.
Therefore, there exists some element $x_m \in S$ such that:
$$x_0 - \varepsilon < x_m \le x_0.$$
Since $x_m \in S$, the closed interval $[0, x_m]$ is covered by a finite subcollection of $\mathcal{U}$, say:
$$[0, x_m] \subseteq \bigcup_{j=1}^k U_{i_j}.$$
Furthermore, because $x_m \in (x_0 - \varepsilon, x_0]$, the closed interval $[x_m, x_0]$ satisfies:
$$[x_m, x_0] \subseteq (x_0 - \varepsilon, \; x_0 + \varepsilon) \cap [0, 1] \subseteq U_{i_0}.$$
Decomposing the interval $[0, x_0]$:
$$[0, x_0] = [0, x_m] \cup [x_m, x_0] \subseteq \left(\bigcup_{j=1}^k U_{i_j}\right) \cup U_{i_0}.$$
This exhibits $[0, x_0]$ as a subset of the union of the $k + 1$ open sets $\{U_{i_1}, \dots, U_{i_k}, U_{i_0}\}$.
Thus $[0, x_0]$ is covered by a finite subcollection of $\mathcal{U}$, which proves that:
$$x_0 \in S.$$

**Step 4: The supremum $x_0$ is equal to $1$.**
We claim that $x_0 = 1$.
Suppose for contradiction that $x_0 < 1$.
Then $x_0$ is not the right endpoint of $[0, 1]$.
Since $U_{i_0}$ contains $x_0$ and is open, the neighborhood $(x_0 - \varepsilon, x_0 + \varepsilon) \cap [0, 1] \subseteq U_{i_0}$ extends strictly to the right of $x_0$.
Choose $\delta > 0$ small enough that $\delta \le \varepsilon$ and $x_0 + \delta \le 1$.
Then the closed interval $[x_0, x_0 + \delta]$ is contained in $U_{i_0}$:
$$[x_0, x_0 + \delta] \subseteq (x_0 - \varepsilon, \; x_0 + \varepsilon) \cap [0, 1] \subseteq U_{i_0}.$$
Combining this with our finite cover of $[0, x_0]$ from Step 3:
$$[0, x_0 + \delta] = [0, x_0] \cup [x_0, x_0 + \delta] \subseteq \left(\bigcup_{j=1}^k U_{i_j} \cup U_{i_0}\right) \cup U_{i_0} = \bigcup_{j=1}^k U_{i_j} \cup U_{i_0}.$$
This shows that $[0, x_0 + \delta]$ is covered by a finite subcollection of $\mathcal{U}$, which implies:
$$x_0 + \delta \in S.$$
Since $\delta > 0$, we have $x_0 + \delta > x_0 = \sup S$.
This contradicts the fact that $x_0$ is an upper bound for $S$.

Therefore, our assumption that $x_0 < 1$ was false, so we must have:
$$x_0 = 1.$$

**Conclusion:**
From Step 3, we know that $x_0 \in S$. From Step 4, we have $x_0 = 1$.
Therefore:
$$1 \in S.$$
By definition of $S$, this means that $[0, 1]$ is covered by a finite subcollection of $\mathcal{U}$:
$$[0, 1] \subseteq \bigcup_{j=1}^n U_{i_j}.$$
Since $\mathcal{U}$ was an arbitrary open cover of $[0, 1]$, every open cover of $[0, 1]$ admits a finite subcover.
This proves that $[0, 1]$ is compact. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 23.6" content=thm236_proof %}

{% include figure.html
   src="point-set-topology/lecture-23/compactness-unit-interval-supremum.svg"
   num="23.3"
   caption="The supremum proof that $[0, 1]$ is compact: $S$ is the set of $x$ for which $[0, x]$ admits a finite subcover. The open set $U_{i_0}$ containing $x_0 = \sup S$ extends back to an already-covered $x_m \in S$ (proving $x_0 \in S$) and forward past $x_0$ to $x_0 + \delta$ (yielding a contradiction if $x_0 < 1$)."
   alt="The unit interval [0, 1] with covered segment [0, xm], supremum x0, open set Ui0, and extension x0 + delta." %}

---

## At a glance

- [Definition 23.1 (Hausdorff Space)](#definition-23-1-hausdorff-space): Distinct points possess disjoint open neighborhoods.
- [Proposition 23.2 (Products of Hausdorff Spaces)](#proposition-23-2-products-of-hausdorff-spaces): Cartesian product of Hausdorff spaces is Hausdorff in the product topology.
- [Proposition 23.3 (Subspaces of Hausdorff Spaces)](#proposition-23-3-subspaces-of-hausdorff-spaces): Every subspace of a Hausdorff space inherits the Hausdorff property.
- [Standing Convention: Hausdorff Assumption](#standing-convention-hausdorff-assumption): Prominent alert detailing that compactness in this course requires the Hausdorff axiom.
- [Definition 23.4 (Compact Space)](#definition-23-4-compact-space): A Hausdorff space where every open cover admits a finite subcover.
- [Example 23.5 ($\mathbb{R}$ is Not Compact)](#example-23-5-r-is-not-compact): The open cover $\{(n - 1/4, n + 5/4) : n \in \mathbb{Z}\}$ admits no finite subcover.
- [Theorem 23.6 ($[0, 1]$ is Compact)](#theorem-23-6-unit-interval-is-compact): Supremum argument showing $[0, 1]$ is compact.

---

## Where we are

With this lecture, we have introduced the twin foundations of Part IV: Hausdorff separation and compactness. In the next lecture (**Lecture 24**), we prove the **Tube Lemma**, establish that the product of two compact spaces is compact, and examine how compactness behaves under taking closed subspaces.

---

## Further reading

- **Munkres, *Topology* (2nd ed.)**, §17: *Closed Sets and Limit Points* (Hausdorff spaces); §26: *Compact Spaces*.
- **Morris, *Topology Without Tears***, Chapter 7: *Compactness*.