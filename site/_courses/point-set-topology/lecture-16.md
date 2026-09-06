---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 16
title: "Connectedness of the Unit Interval and Subspaces of the Real Line"
coverage: >
  Proves that the closed unit interval [0,1] is connected using the supremum argument.
  Deduces as a corollary that R is connected, correcting a verbal slip regarding the
  connectedness of [a,b]. Proves that the non-empty connected subspaces of the real
  line are precisely the intervals. Establishes the fundamental topological theorem
  that the continuous image of any connected space is connected.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 1
depends_on:
  - lecture: 15
    title: "Sequential Criteria for Closed Sets and Continuity, and Introduction to Connectedness"
    relationship: "Supplies the definition of connected spaces and preservation by dense subsets and closures."
  - lecture: 7
    title: "Continuous Maps: Topological Definition and Examples"
    relationship: "Supplies the topological definition of continuous maps via open preimages."
used_in:
  - lecture: 17
    title: "Connectedness of Products, Union Lemma, and Stereographic Charts"
    relationship: "Supplies connectedness of intervals and continuous image preservation used to prove product spaces and spheres are connected."
notation:
  - symbol: "$S = \\lbrace x \\in [0,1] : [0,x] \\subseteq U \\rbrace$"
    gloss: 'The bounded set of points whose initial segments lie in $U$, whose supremum is $1$'
  - symbol: "$\\sup Y, \\inf Y$"
    gloss: 'Supremum and infimum of a subset $Y \\subseteq \\mathbb{R}$ in $[-\\infty, \\infty]$'
prev: lecture-15
next: lecture-17
---

# Lecture 16 — Connectedness of the Unit Interval and Subspaces of the Real Line

## Where we are

In [Lecture 15]({{ site.baseurl }}/point-set-topology/lecture-15/), we entered Part III of the course by introducing the topological property of **connectedness**: a space $X$ is connected if it cannot be partitioned into two disjoint, non-empty open subsets. We proved that if a dense subset of $X$ is connected, then $X$ is connected, which implies that the closure $\overline{A}$ of any connected subset $A$ is connected.

In this lecture, we establish the foundational connectedness theorems of real analysis and topology. First, we prove that the closed unit interval $[0, 1]$ is connected using the classic **supremum argument**—a recurring proof technique in this course. From this, we deduce that every closed interval $[a, b]$ and the full real line $\mathbb{R}$ are connected. Next, we completely classify the connected subspaces of $\mathbb{R}$: a non-empty subset of the real line is connected if and only if it is an interval. Finally, we prove the fundamental preservation theorem that the continuous image of a connected space is always connected.

---

## Connectedness of the unit interval

We prove that the closed unit interval $[0, 1]$ equipped with the subspace topology from $\mathbb{R}$ is connected.

### Proposition 16.1 (Connectedness of $[0, 1]$) {#proposition-16-1-connectedness-unit-interval}

{% capture prop161_content %}
The closed unit interval $[0, 1]$ equipped with the standard subspace topology from $\mathbb{R}$ is **connected**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 16.1 (Connectedness of $[0, 1]$)" content=prop161_content %}

{% capture prop161_proof %}
Let us assume that $[0, 1]$ is not connected.
So then there exist non-empty open sets $U$ and $V$, which are also disjoint, such that $[0, 1]$ is a disjoint union:
$$[0, 1] = U \cup V, \quad \text{with } U \cap V = \varnothing.$$
One of these contains $0$, so we may assume without loss of generality that $0 \in U$.

So let us consider the set:
$$S = \lbrace x \in [0, 1] : [0, x] \subseteq U \rbrace.$$
Clearly, $S$ is non-empty because $0 \in S$, since the closed interval $[0, 0] = \{0\}$ is definitely in $U$.
Since $S$ is non-empty and bounded above by $1$, let $a$ be the supremum:
$$a = \sup S.$$
Then $a$ satisfies $0 \le a \le 1$.

**Step 1: We claim that $a$ is in $U$.**
Let us prove this claim.
By the definition of the supremum, there is a sequence $(a_n)_{n \ge 1}$ in $S$ such that $a_n$ converges to $a$.
As $V$ is open in $[0, 1]$ and $U = [0, 1] \setminus V$ is the complement of $V$, this implies that $U$ is closed in $[0, 1]$.
And since each $a_n \in S$, by definition $[0, a_n] \subseteq U$, which in particular implies that each $a_n \in U$.
So $U$ is closed, each $a_n \in U$, and $a_n \to a$. These together imply by Lemma 15.1 that:
$$a \in U.$$
So we have proved that $a$ is in $U$. ✓

Now note that as each $a_n \in S$, this implies $[0, a_n] \subseteq U$, which implies that when we take the union:
$$\bigcup_{n=1}^\infty [0, a_n] \subseteq U.$$
Now observe that for any $y \in [0, a)$ with $0 \le y < a$, we can choose an $\varepsilon$-neighbourhood around $a$ which does not contain $y$, and for all $n$ sufficiently large, $a_n$ will be in this neighbourhood. Therefore, $y \in [0, a_n]$ for sufficiently large $n$.
So this shows that the half-open interval $[0, a)$ is contained in $U$.
And plus we have already proved that $a \in U$.
So this implies that the closed interval:
$$[0, a] \subseteq U.$$

**Step 2: Now we claim that $a$ has to be equal to $1$.**
If $a$ is not equal to $1$, so if $a < 1$:
since $a \in U$ and $U$ is open, there is $\varepsilon > 0$ such that the interval $(a - \varepsilon, a + \varepsilon) \cap [0, 1]$ is contained in $U$.
Since $a < 1$, we can choose $\varepsilon > 0$ sufficiently small such that $a + \varepsilon < 1$.
This implies that the half-open interval $[a, a + \varepsilon) \subseteq U$.
We already know that $[0, a] \subseteq U$. Therefore:
$$[0, a + \varepsilon) = [0, a] \cup [a, a + \varepsilon) \subseteq U.$$
This implies that the interval:
$$\left[0, a + \frac{\varepsilon}{2}\right] \subseteq [0, a + \varepsilon) \subseteq U.$$
So this implies that $a + \frac{\varepsilon}{2} \in S$.
But this contradicts the fact that $a$ is the supremum of elements in $S$.
So therefore, thus $a$ is forced to be $1$. ✓

In particular, this implies that this entire interval $[0, 1]$ is contained in $U$, which contradicts the non-emptiness of $V$.
Thus, $[0, 1]$ cannot be disconnected.
So this implies that $[0, 1]$ is connected. This completes the proof. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 16.1" content=prop161_proof %}

{% include figure.html
   src="point-set-topology/lecture-16/supremum-connectedness-interval.svg"
   caption="Proposition 16.1: the supremum $a = \sup S$ belongs to $U$ because $U$ is closed. If $a < 1$, openness of $U$ extends the interval into $[0, a + \varepsilon/2] \subseteq U$, producing a point in $S$ strictly larger than $\sup S$."
   alt="Number line showing the interval from 0 to 1, the segment from 0 to a in U, sequence an converging to a, and the contradiction extension past a." %}

### Exercise 16.1 (Connectedness of arbitrary closed intervals) {#exercise-16-1-closed-intervals-connected}

{% capture ex161_content %}
Let $a, b \in \mathbb{R}$ with $a < b$. Prove that the closed interval $[a, b]$ is connected.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 16.1 (Connectedness of $[a, b]$)" content=ex161_content %}

{% capture ex161_sol %}
**Solution:**
The map $h \colon [0, 1] \to [a, b]$ defined by $h(t) = a + t(b - a)$ is a continuous bijection with continuous inverse $h^{-1}(x) = \frac{x - a}{b - a}$.
Thus $h$ is a homeomorphism. Since $[0, 1]$ is connected and connectedness is preserved under continuous maps (Proposition 16.4 below), $[a, b] = h([0, 1])$ is connected. Alternatively, one can repeat the supremum argument of Proposition 16.1 on $[a, b]$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Solution to Exercise 16.1" content=ex161_sol %}

---

## Connectedness of the real line

Using the connectedness of closed intervals, we prove that $\mathbb{R}$ is connected.

### Corollary 16.2 (Connectedness of $\mathbb{R}$) {#corollary-16-2-connectedness-of-r}

{% capture cor162_content %}
The real line $\mathbb{R}$ equipped with the standard topology is **connected**.
{% endcapture %}
{% include block.html type="corollary" title="Corollary 16.2 (Connectedness of $\mathbb{R}$)" content=cor162_content %}

{% capture cor162_proof %}
Proof: if not, then we can write $\mathbb{R}$ as a disjoint union:
$$\mathbb{R} = U \cup V$$
where $U$ and $V$ are disjoint non-empty open subsets of $\mathbb{R}$.
So we can choose any $a \in U$ and $b \in V$, and without loss of generality may assume that $a < b$.

So then intersecting this relation $\mathbb{R} = U \cup V$ with the interval $[a, b]$, this implies:
$$[a, b] = \bigl([a, b] \cap U\bigr) \cup \bigl([a, b] \cap V\bigr).$$
Notice that:
1. $[a, b] \cap U$ and $[a, b] \cap V$ are disjoint, because $U \cap V = \varnothing$.
2. Both $[a, b] \cap U$ and $[a, b] \cap V$ are open in the subspace topology on $[a, b]$.
3. As $a \in [a, b] \cap U$, the first set is non-empty.
4. As $b \in [a, b] \cap V$, the second set is non-empty.

So this shows that $[a, b]$ is disconnected, which is a contradiction.
For here $[a, b]$ has the subspace topology, and we have written $[a, b]$ as a disjoint union of two non-empty open subsets, which contradicts the fact that $[a, b]$ is connected (Proposition 16.1 and Exercise 16.1).
Therefore, $\mathbb{R}$ with the standard topology is connected. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Corollary 16.2" content=cor162_proof %}

{% capture cor162_note %}
**Defect registered in `context/known-defects.md` (Slip):**
In sentence 119 of the transcript, the lecturer concludes: *"which contradicts the fact that $[a,b]$ is disconnected."*
The intended statement is that this contradicts the fact that $[a,b]$ is **connected**. The slip has been corrected above.
{% endcapture %}
{% include block.html type="correction" id="correction-note-slip-on-connectedness-of-ab" title="Correction Note: Slip on Connectedness of $[a,b]$" content=cor162_note %}

---

## Connected subspaces of the real line

We now completely characterize all connected subsets of $\mathbb{R}$.

### Theorem 16.3 (Connected subspaces of $\mathbb{R}$ are intervals) {#theorem-16-3-connected-subspaces-of-r}

{% capture thm163_content %}
A non-empty subset $Y \subseteq \mathbb{R}$ is connected in the subspace topology if and only if $Y$ is an **interval** (that is, a singleton $\{a\}$, an open, closed, or half-open bounded interval, an infinite ray, or $\mathbb{R}$ itself).
{% endcapture %}
{% include block.html type="theorem" title="Theorem 16.3 (Connected Subspaces of $\mathbb{R}$ Are Intervals)" content=thm163_content %}

{% capture thm163_proof %}
The idea is simple. Let $Y \subseteq \mathbb{R}$ be a non-empty connected subspace.
We define:
$$a = \inf_{y \in Y} y, \qquad b = \sup_{y \in Y} y.$$
Here $a$ and $b$ are allowed to be in $[-\infty, \infty]$. Then $a \le b$.

- **Case 1 ($a = b$):** This clearly implies that $Y$ is just the singleton set $\{a\} = [a, a]$. Clearly in this case $Y$ is connected and equal to the interval $[a, a]$.
- **Case 2 ($a < b$):** In this case, we claim that the open interval $(a, b)$ is contained in $Y$:
  $$(a, b) \subseteq Y.$$
  If not, then there exists $c \in (a, b)$ such that $c$ does not belong to $Y$.
  Then this will imply that we can write $Y$ as a disjoint union:
  $$Y = \bigl(Y \cap (-\infty, c)\bigr) \cup \bigl(Y \cap (c, \infty)\bigr).$$
  Let us check that both sets are non-empty:
  - As $a$ is the infimum of elements in $Y$, there is a sequence in $Y$ converging to $a$, and since $a < c$, there will be elements of the sequence strictly less than $c$. So this shows that $Y \cap (-\infty, c)$ is non-empty.
  - And similarly, as $b$ is the supremum of elements in $Y$, there is a sequence of elements converging to $b$, and since $b > c$, almost all members of the sequence will be greater than $c$. So $Y \cap (c, \infty)$ is non-empty.

  $Y$ has the subspace topology, and in the subspace topology, both these sets are open. Thus this gives a contradiction: it contradicts the assumption that $Y$ is connected, because we have written $Y$ as a disjoint union of non-empty open subsets.
  Thus, the interval $(a, b)$ is contained in $Y$. ✓

And also notice that $Y \subseteq [a, b]$, as $a = \inf Y$ and $b = \sup Y$. Thus:
$$(a, b) \subseteq Y \subseteq [a, b].$$
From this, we conclude that $Y$ has to be one of the intervals $(a, b)$, $[a, b)$, $(a, b]$, or $[a, b]$ (with the appropriate ray if an endpoint is infinite). In every case, $Y$ is an interval. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 16.3" content=thm163_proof %}

{% include figure.html
   src="point-set-topology/lecture-16/connected-subspaces-real-line.svg"
   caption="Theorem 16.3: if a point $c \in (a, b)$ did not belong to $Y$, the open rays $(-\infty, c)$ and $(c, \infty)$ would split $Y$ into two non-empty open subsets, contradicting its connectedness."
   alt="Number line with a connected set Y from infimum a to supremum b, partitioned into two open sets by a missing point c." %}

---

## Continuous images of connected spaces

We conclude with a fundamental theorem governing the interaction between continuous maps and connectedness.

### Proposition 16.4 (Continuous image of a connected space is connected) {#proposition-16-4-continuous-image-connected}

{% capture prop164_content %}
Let $X$ and $Y$ be topological spaces, and let $f \colon X \to Y$ be a continuous map.
If $X$ is **connected**, then the image subspace $f(X) \subseteq Y$ equipped with the subspace topology is **connected**.
{% endcapture %}
{% include block.html type="proposition" title="Proposition 16.4 (Continuous Image of a Connected Space is Connected)" content=prop164_content %}

{% capture prop164_proof %}
The proof is easy: let us see.
If not, then there exist open subsets $U$ and $V$ in $Y$ such that $f(X)$ is the disjoint union:
$$f(X) = \bigl(f(X) \cap U\bigr) \cup \bigl(f(X) \cap V\bigr), \quad \text{with } \bigl(f(X) \cap U\bigr) \cap \bigl(f(X) \cap V\bigr) = \varnothing.$$
*(Word of caution: $U \cap V$ need not be empty in $Y$; we can only say that their intersections with $f(X)$ are disjoint).*
And both $f(X) \cap U$ and $f(X) \cap V$ are non-empty.

So note that this implies we can easily check that $X$ is equal to:
$$X = f^{-1}(U) \cup f^{-1}(V), \quad \text{with } f^{-1}(U) \cap f^{-1}(V) = \varnothing.$$
Moreover, as $f(X) \cap U$ is non-empty, this implies $f^{-1}(U)$ is non-empty; and similarly $f^{-1}(V)$ is non-empty.
As $f$ is continuous, both $f^{-1}(U)$ and $f^{-1}(V)$ are open subsets of $X$.

So thus, we have written $X$ as a disjoint union of non-empty open subsets.
But this contradicts the connectedness of $X$.
So thus, $f(X)$ is connected in the subspace topology. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Proposition 16.4" content=prop164_proof %}

{% include figure.html
   src="point-set-topology/lecture-16/continuous-image-connected.svg"
   caption="Proposition 16.4: if the image $f(X)$ were disconnected by open sets $U$ and $V$, their preimages $f^{-1}(U)$ and $f^{-1}(V)$ would disconnect $X$, contradicting that $X$ is connected."
   alt="Diagram showing continuous map f from a connected space X into space Y, pulling back a disconnection of f(X) to disconnect X." %}

---

## At a glance

- [Proposition 16.1 (Connectedness of $[0, 1]$)](#proposition-16-1-connectedness-unit-interval): Proves $[0, 1]$ is connected using the supremum argument on $S = \{x \in [0, 1] : [0, x] \subseteq U\}$.
- [Exercise 16.1 (Connectedness of $[a, b]$)](#exercise-16-1-closed-intervals-connected): Any closed bounded interval $[a, b]$ is homeomorphic to $[0, 1]$ and hence connected.
- [Corollary 16.2 (Connectedness of $\mathbb{R}$)](#corollary-16-2-connectedness-of-r): $\mathbb{R}$ is connected, deduced by intersecting any hypothetical disconnection with a closed interval $[a, b]$.
- [Correction Note: Slip on Connectedness of $[a,b]$](#correction-note-slip-on-connectedness-of-ab): Corrects verbal slip where the transcript claimed $[a, b]$ is disconnected instead of connected.
- [Theorem 16.3 (Connected Subspaces of $\mathbb{R}$ Are Intervals)](#theorem-16-3-connected-subspaces-of-r): Non-empty connected subspaces of $\mathbb{R}$ are precisely the intervals; any missing point in $(\inf Y, \sup Y)$ would disconnect $Y$.
- [Proposition 16.4 (Continuous Image of a Connected Space is Connected)](#proposition-16-4-continuous-image-connected): If $X$ is connected and $f \colon X \to Y$ is continuous, then the subspace $f(X) \subseteq Y$ is connected.
