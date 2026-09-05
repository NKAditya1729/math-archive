---
layout: lecture
title: "Block Rendering Test Suite"
course: point-set-topology
course_title: "Point-Set Topology"
lecture_number: 99
coverage: "Demonstrates all nine mathematical block types, KaTeX rendering, and interactive toggle controls."
status: drafted
version: 1.0
permalink: /test-blocks/
---

This test page verifies build-time rendering for all nine mathematical block types, proper KaTeX math typesetting (including $\varnothing$ and $\blacksquare$), and interactive toggle behavior.

---

## 1. Definition Block

{% capture def_content %}
Let $X$ be a set. A collection $\tau \subseteq \mathcal{P}(X)$ is a **topology on $X$** if:
1. $\varnothing \in \tau$ and $X \in \tau$.
2. For any $U_1, \dots, U_n \in \tau$, we have $\bigcap_{i=1}^{n} U_i \in \tau$.
3. For any arbitrary collection $\{U_i\}_{i \in I} \subseteq \tau$, we have $\bigcup_{i \in I} U_i \in \tau$.
{% endcapture %}
{% include block.html type="definition" title="Definition 1.1 (Topology on $X$)" content=def_content %}

---

## 2. Theorem Block

{% capture thm_content %}
Let $(X, \tau)$ be a topological space and let $\mathcal{B} \subseteq \tau$. Then $\mathcal{B}$ is a basis for $\tau$ if and only if for every open set $U \in \tau$ and every $x \in U$, there exists $B \in \mathcal{B}$ such that $x \in B \subseteq U$.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 1.2 (Basis Criterion)" content=thm_content %}

---

## 3. Proof Block

{% capture prf_content %}
$(\Rightarrow)$ Assume $\mathcal{B}$ is a basis for $\tau$. Let $U \in \tau$ and $x \in U$. By definition, $U = \bigcup_{i \in I} B_i$ for some collection $\{B_i\}_{i \in I} \subseteq \mathcal{B}$. Since $x \in U$, there must exist some index $i_0 \in I$ such that $x \in B_{i_0} \subseteq U$. Setting $B = B_{i_0}$ yields the desired basis element.

$(\Leftarrow)$ Assume for each $x \in U$ there exists $B_x \in \mathcal{B}$ with $x \in B_x \subseteq U$. Then $\bigcup_{x \in U} B_x = U$, proving $U$ is a union of basis elements.
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 1.2" content=prf_content %}

---

## 4. Example Block

{% capture ex_content %}
Let $X$ be any set. The discrete topology $\tau_{\text{disc}} = \mathcal{P}(X)$ contains every subset of $X$. In particular, every singleton $\{x\}$ is open.
{% endcapture %}
{% include block.html type="example" title="Example 1.3 (Discrete Topology)" content=ex_content %}

---

## 5. Non-Example Block

{% capture nonex_content %}
Let $X = \mathbb{R}$ with the standard topology. The half-open interval $[0, 1)$ is **not** an open set because for $x = 0 \in [0, 1)$, every $\varepsilon$-ball $(-\varepsilon, \varepsilon)$ contains negative numbers outside $[0, 1)$.
{% endcapture %}
{% include block.html type="non-example" title="Non-example 1.4 (Half-open interval in $\mathbb{R}$)" content=nonex_content %}

---

## 6. Supplement Block

{% capture supp_content %}
Condition (T2) requires **finite** intersections. For an infinite collection, openness can fail:
$$
\bigcap_{n=1}^{\infty} \left(-\frac{1}{n}, \frac{1}{n}\right) = \{0\},
$$
which is not open in the standard topology on $\mathbb{R}$.
{% endcapture %}
{% include block.html type="supplement" title="Why Finiteness is Essential in (T2)" content=supp_content %}

---

## 7. Correction Block

{% capture corr_content %}
**As transcribed:** "Every union of closed sets is closed."  
**What is meant:** Only **finite** unions of closed sets are closed.  
**Why:** Arbitrary unions of closed sets need not be closed (e.g., $\bigcup_{n=1}^\infty [1/n, 1] = (0, 1]$).
{% endcapture %}
{% include block.html type="correction" title="Correction: Finite versus arbitrary unions of closed sets" content=corr_content %}

---

## 8. Open Question Block

{% capture open_content %}
The lecturer wrote a calculation on the lower-right blackboard for Cauchy–Schwarz that is obscured by the lectern. Check video timestamp 34:12 to confirm the substitution.
{% endcapture %}
{% include block.html type="open-question" title="Blackboard derivation at 34:12" content=open_content %}

---

## 9. Exercise Block

{% capture exer_content %}
Show that if $(X, d)$ is a metric space, the open balls $B_r(x) = \{\, y \in X : d(x, y) < r \,\}$ form a basis for the metric topology on $X$.
{% endcapture %}
{% capture exer_sol %}
Let $U$ be open in the metric topology and let $x \in U$. By definition of the metric topology, there exists $\varepsilon > 0$ such that $B_\varepsilon(x) \subseteq U$. Since $x \in B_\varepsilon(x)$, the criterion of Theorem 1.2 is satisfied. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 1.5 (Open balls as a basis)" content=exer_content solution=exer_sol %}
