---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 8
title: "The Basis Criterion for Continuity and Continuous Operations"
coverage: >
  Proves the basis criterion for continuity: a map is continuous if and only if
  preimages of basic open sets are open. Establishes the continuity of the addition
  map and multiplication map on R2 via explicit epsilon-estimates on basic open squares.
  Constructs a basis for the subspace topology on the punctured real line R*,
  and proves that the inversion map x |-> 1/x is continuous in the subspace topology.
status: drafted
lecture_date:
version: 1.0
timestamps: false
figures: 3
corrections: 0
depends_on:
  - lecture: 7
    title: "Continuous Maps, Inclusions, and Projections"
    relationship: "Lecture 7 defines continuous maps via preimages of open sets and states the basis criterion."
used_in:
  - lecture: 9
    title: "Properties of Continuous Maps and Algebraic Combinations"
    relationship: "Lecture 9 establishes continuous combinations f+g, fg, f/g using the continuity of operations proved in Lecture 8."
notation:
  - symbol: "$A$"
    gloss: "The addition map $\\mathbb{R}^2 \\to \\mathbb{R}$, $(x,y) \\mapsto x+y$"
  - symbol: "$M$"
    gloss: "The multiplication map $\\mathbb{R}^2 \\to \\mathbb{R}$, $(x,y) \\mapsto xy$"
  - symbol: "$\\mathbb{R}^\\times$"
    gloss: "The punctured real line $\\mathbb{R} \\setminus \\lbrace 0\\rbrace$ equipped with the subspace topology"
prev: lecture-07
next: lecture-09
---

# Lecture 8 — The Basis Criterion for Continuity and Continuous Operations

## Where we are

In [Lecture 7]({{ site.baseurl }}/point-set-topology/lecture-07/), we introduced the definition of a continuous map between topological spaces in terms of preimages of open sets. We proved that identity maps, subspace inclusions, and coordinate projections are continuous, and that the product topology is the coarsest topology making all coordinate projections continuous. At the close of that lecture, we stated that to verify continuity, it is sufficient to check preimages of basic open sets rather than all open sets.

Here we prove this basis criterion in full generality. We then use it to establish that the fundamental arithmetic operations on the real numbers—addition $+ : \mathbb{R}^2 \to \mathbb{R}$, multiplication $\cdot : \mathbb{R}^2 \to \mathbb{R}$, and reciprocal inversion $x \mapsto 1/x$ on the punctured real line $\mathbb{R}^\times = \mathbb{R} \setminus \lbrace 0\rbrace$—are continuous maps in their standard topologies. Explicit $\varepsilon$-estimates provide the required basic open squares in $\mathbb{R}^2$, establishing the topological foundations for algebraic operations and function spaces developed in subsequent lectures.

---

## The basis criterion for continuity

In [Definition 7.1]({{ site.baseurl }}/point-set-topology/lecture-07/#definition-7-1-continuous-map), a map $f : X \to Y$ is continuous if $f^{-1}(U) \in \tau_X$ for every open set $U \in \tau_Y$. Because open sets in $Y$ may be arbitrarily complex unions of basic sets, checking every open set directly can be difficult. The following lemma simplifies the verification to checking only the elements of a chosen basis.

{% capture lem_basis_criterion %}
Let $(X,\tau_X)$ and $(Y,\tau_Y)$ be topological spaces, and let $f : X \to Y$ be a map of sets. Let $\mathcal{B}$ be a basis for the topology $\tau_Y$.

If $f^{-1}(V) \in \tau_X$ for every basic open set $V \in \mathcal{B}$, then $f$ is continuous.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 8.1 (Basis Criterion for Continuity)" content=lem_basis_criterion %}

{% capture lem_basis_criterion_proof %}
So let $U \subseteq Y$ be an open set ($U \in \tau_Y$). We want to check that $f$ is continuous, so we will show that $f^{-1}(U)$ is open in $X$.

Since $\mathcal{B}$ is a basis for the topology on $Y$, for each $y \in U$ there exists a basic open set $V_y \in \mathcal{B}$ such that $y \in V_y$ and $V_y \subseteq U$. Therefore, this shows that we can write $U$ as a union over all the $y$'s:
$$U = \bigcup_{y \in U} V_y.$$

Then it is a straightforward check in set theory that preimages distribute over unions:
$$f^{-1}(U) = f^{-1}\left(\bigcup_{y \in U} V_y\right) = \bigcup_{y \in U} f^{-1}(V_y).$$

Each of these $f^{-1}(V_y)$ is open as $V_y \in \mathcal{B}$ and by hypothesis our assumption is that $f^{-1}(V)$ is open for every $V \in \mathcal{B}$. And as arbitrary union of open sets is open, this implies that $f^{-1}(U)$ is open.

And since this happens for every open set $U$, thus $f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 8.1" content=lem_basis_criterion_proof %}

{% capture supp_basis_iff %}
The converse of Lemma 8.1 is immediate: if $f : X \to Y$ is continuous, then $f^{-1}(U) \in \tau_X$ for *all* $U \in \tau_Y$. Since a basis satisfies $\mathcal{B} \subseteq \tau_Y$, every basic open set $V \in \mathcal{B}$ is in particular open in $Y$, so $f^{-1}(V) \in \tau_X$.

Together, the lemma and its converse yield the two-way equivalence:
$$f : X \to Y \text{ is continuous} \iff \forall V \in \mathcal{B},\; f^{-1}(V) \in \tau_X.$$

This criterion is extraordinarily useful: to show that a map into $\mathbb{R}$ is continuous, we only need to test preimages of open intervals $(a,b)$; to show that a map into $\mathbb{R}^n$ is continuous, we only need to test preimages of open rectangles or balls.
{% endcapture %}
{% include block.html type="supplement" title="The two-way characterization" content=supp_basis_iff %}

---

## Continuous arithmetic operations on the real line

We now turn to the algebraic structures on continuous real-valued functions. Continuous functions $\mathbb{R} \to \mathbb{R}$ or $X \to \mathbb{R}$ can be added, multiplied, and inverted. To prove that sums and products of continuous functions are continuous, we must first verify that the arithmetic operations themselves are continuous as maps from $\mathbb{R}^2$ to $\mathbb{R}$.

Recall from [Lecture 2]({{ site.baseurl }}/point-set-topology/lecture-02/#definition-2-1-open-interval-in-r) and [Lecture 3]({{ site.baseurl }}/point-set-topology/lecture-03/#definition-3-3-open-ball-in-rn) the standard bases:
- For $\mathbb{R}$, the basic open sets are open intervals
  $$B_\varepsilon(z) = (z - \varepsilon, z + \varepsilon), \qquad z \in \mathbb{R},\; \varepsilon > 0.$$
- For $\mathbb{R}^2$, the basic open sets are open squares
  $$S_\delta(x,y) = \lbrace (x',y') \in \mathbb{R}^2 \;:\; |x'-x| < \delta \text{ and } |y'-y| < \delta \rbrace, \qquad (x,y) \in \mathbb{R}^2,\; \delta > 0.$$
  In [Lecture 6]({{ site.baseurl }}/point-set-topology/lecture-06/#proposition-6-4-equivalence-of-standard-and-product-topologies-on-rn), we proved that this standard topology coincides with the product topology on $\mathbb{R} \times \mathbb{R}$.

{% capture thm_operations %}
Equip $\mathbb{R}$ and $\mathbb{R}^2$ with their standard topologies.
1. The **addition map**
   $$A : \mathbb{R}^2 \to \mathbb{R}, \qquad A(x,y) = x + y$$
   is continuous.
2. The **multiplication map**
   $$M : \mathbb{R}^2 \to \mathbb{R}, \qquad M(x,y) = xy$$
   is continuous.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 8.2 (Continuity of Addition and Multiplication)" content=thm_operations %}

We will use the above lemma to prove this theorem. By Lemma 8.1, the standard topology on $\mathbb{R}$ has basic open sets $B_\varepsilon(z)$, and it suffices to show that the inverse images of these are open.

---

### Continuity of the addition map

{% capture thm82_add_proof %}
By the lemma above, it suffices to show that $A^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}^2$ for every $z \in \mathbb{R}$ and $\varepsilon > 0$.

**Step 1: Local perturbation estimate.**
Let $(x,y) \in \mathbb{R}^2$ and recall that $S_\delta(x,y)$ consists of those $(x',y') \in \mathbb{R}^2$ such that $|x'-x| < \delta$ and $|y'-y| < \delta$.

Note that if $(x',y') \in S_\delta(x,y)$, then:
$$|A(x',y') - A(x,y)| = |(x'+y') - (x+y)| \le |x'-x| + |y'-y| < 2\delta.$$
So this implies that for $(x',y') \in S_\delta(x,y)$, the value $A(x',y') \in B_{2\delta}(x+y)$. In terms of preimages, setting $\delta = \varepsilon/2$, this shows that
$$S_{\varepsilon/2}(x,y) \subseteq A^{-1}(B_\varepsilon(x+y)).$$
To see this, we check that if $(x',y') \in S_{\varepsilon/2}(x,y)$, then $A(x',y') \in B_\varepsilon(x+y)$.

**Step 2: Preimages of basic open intervals are open.**
Now let $(x,y) \in A^{-1}(B_\varepsilon(z))$. This means $A(x,y) = x+y \in B_\varepsilon(z)$.

Since $B_\varepsilon(z)$ is open, there is an $\varepsilon' > 0$ such that
$$B_{\varepsilon'}(x+y) \subseteq B_\varepsilon(z).$$
From Step 1, we have
$$S_{\varepsilon'/2}(x,y) \subseteq A^{-1}(B_{\varepsilon'}(x+y)) \subseteq A^{-1}(B_\varepsilon(z)).$$

Thus, for every point $(x,y) \in A^{-1}(B_\varepsilon(z))$, we have found an $\varepsilon' > 0$ such that the basic open square $S_{\varepsilon'/2}(x,y)$ around $(x,y)$ is contained in $A^{-1}(B_\varepsilon(z))$.

This implies that $A^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}^2$.

So this shows that the addition map $A$ is continuous. ✓
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 8.2, Part 1 (Addition)" content=thm82_add_proof %}

{% include figure.html
   src="point-set-topology/lecture-08/addition-continuity-pullback.svg"
   caption="Figure 8.1: Pullback geometry for addition. Given a basic open interval $B_\varepsilon(z) \subseteq \mathbb{R}$ containing $x+y$, a nested interval $B_{\varepsilon'}(x+y) \subseteq B_\varepsilon(z)$ is chosen. The open square $S_{\varepsilon'/2}(x,y)$ in $\mathbb{R}^2$ has side length $\varepsilon'$ and maps entirely into $B_{\varepsilon'}(x+y)$ under $A(x',y') = x'+y'$."
   alt="Pullback geometry for addition showing a square in R^2 mapping into an interval on R." %}

---

### Continuity of the multiplication map

{% capture thm82_mult_proof %}
Let $z \in \mathbb{R}$ and $\varepsilon > 0$. We show that $M^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}^2$.

**Step 1: The setup and error decomposition.**
Let $(x,y) \in \mathbb{R}^2$ and choose $\delta$ satisfying $0 < \delta < 1$. Suppose $(x',y') \in S_\delta(x,y)$, so that
$$|x'-x| < \delta \quad \text{and} \quad |y'-y| < \delta.$$
We decompose the difference $x'y' - xy$ by inserting the cross-term $xy'$:
$$x'y' - xy = (x'y' - xy') + (xy' - xy) = (x'-x)y' + x(y'-y).$$

*(At this point, the intermediate chain of inequalities bounding this expression is written on the blackboard rather than spoken in full; see the Open Question block and supplement below.)*

From the board calculation, the lecturer concludes that for all $(x',y') \in S_\delta(x,y)$:
$$|M(x',y') - M(x,y)| < \delta(|x| + |y| + 1).$$
In terms of images, this establishes:
$$M(S_\delta(x,y)) \subseteq B_{\delta(|x| + |y| + 1)}(xy).$$

**Step 2: Choosing $\delta$ for a target radius.**
Now let $\varepsilon'$ be any given target radius with $0 < \varepsilon' \le 1$. We define
$$\delta = \frac{\varepsilon'}{|x| + |y| + 1}.$$
Since $|x| + |y| + 1 \ge 1$ and $\varepsilon' \le 1$, we have $0 < \delta \le \varepsilon' \le 1$, so the condition $\delta \le 1$ holds.
With this choice of $\delta$:
$$\delta(|x| + |y| + 1) = \left(\frac{\varepsilon'}{|x| + |y| + 1}\right)(|x| + |y| + 1) = \varepsilon'.$$
Therefore, by Step 1,
$$M(S_\delta(x,y)) \subseteq B_{\varepsilon'}(xy),$$
or equivalently,
$$S_{\frac{\varepsilon'}{|x| + |y| + 1}}(x,y) \subseteq M^{-1}(B_{\varepsilon'}(xy)).$$

**Step 3: Preimages of basic open intervals are open.**
Let $(x,y) \in M^{-1}(B_\varepsilon(z))$ be an arbitrary point. Then
$$M(x,y) = xy \in B_\varepsilon(z).$$
Because $B_\varepsilon(z)$ is open in $\mathbb{R}$, there exists an interval radius $\varepsilon' > 0$ such that
$$B_{\varepsilon'}(xy) \subseteq B_\varepsilon(z).$$
Furthermore, by replacing $\varepsilon'$ with $\min\lbrace \varepsilon', 1\rbrace$ if necessary, we may assume without loss of generality that $0 < \varepsilon' \le 1$.

Setting $\delta = \frac{\varepsilon'}{|x| + |y| + 1}$, the inclusion from Step 2 gives:
$$S_\delta(x,y) \subseteq M^{-1}(B_{\varepsilon'}(xy)) \subseteq M^{-1}(B_\varepsilon(z)).$$
Thus, for every point $(x,y) \in M^{-1}(B_\varepsilon(z))$, the basic open square $S_\delta(x,y)$ centered at $(x,y)$ is completely contained in $M^{-1}(B_\varepsilon(z))$.

This implies that $M^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}^2$.

So this shows that the multiplication map is also continuous. This completes the proof of the theorem. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 8.2, Part 2 (Multiplication)" content=thm82_mult_proof %}

{% capture open_mult_gap %}
During Step 1 of the multiplication proof, the spoken audio relies on deictic gestures while the algebraic inequalities are written out on the board:
> *"This is less than equal to $x'-x$ into $y'$, plus minus $y$, uh, which is strictly less than $x'-x$ into mod $y$ plus delta. Uh, this because since $y'-y$ is less than delta, so this implies that mod $y$ is-- mod $y'$ is less than mod $y$ plus delta. Uh, plus mod $x$ into $y-y$... So this is strictly less than... Um, right. Now, this is also less than delta, this quantity over here. So we use that. And this quantity is less than delta. So plus this equal to delta into mod $y$ plus mod $x$ plus delta, which is strictly less than delta into mod $y$ plus mod $x$ plus one."*

The exact intermediate steps written on the board are not spoken aloud and require visual confirmation from the lecture video. The clean mathematical derivation connecting $(x'-x)y' + x(y'-y)$ to the bound $\delta(|x| + |y| + 1)$ is provided in the supplement below.
{% endcapture %}
{% include block.html type="open" title="Open Question: Board derivation of the multiplication estimate" content=open_mult_gap %}

{% capture supp_mult_algebra %}
The standard algebraic derivation completing the board passage proceeds as follows:
1. By the triangle inequality applied to $x'y' - xy = (x'-x)y' + x(y'-y)$:
   $$|x'y' - xy| \le |x'-x||y'| + |x||y'-y|.$$
2. Since $(x',y') \in S_\delta(x,y)$, we have $|x'-x| < \delta$ and $|y'-y| < \delta$. For the factor $|y'|$, write $y' = y + (y'-y)$ to obtain:
   $$|y'| \le |y| + |y'-y| < |y| + \delta.$$
3. Substituting these bounds into the triangle inequality:
   $$|x'y' - xy| < \delta(|y| + \delta) + |x|\delta = \delta(|x| + |y| + \delta).$$
4. Because $\delta < 1$, we have $|x| + |y| + \delta < |x| + |y| + 1$. Multiplying by $\delta > 0$ yields:
   $$|x'y' - xy| < \delta(|x| + |y| + 1).$$
{% endcapture %}
{% include block.html type="supplement" title="Supplement: Reconstructed board algebra for multiplication" content=supp_mult_algebra %}

{% include figure.html
   src="point-set-topology/lecture-08/multiplication-estimate-geometry.svg"
   caption="Figure 8.2: Decomposition for multiplication. The difference $x'y' - xy = (x'-x)y' + x(y'-y)$ is bounded by controlling the perturbations $|x'-x| < \delta$ and $|y'-y| < \delta$ with $\delta \le 1$. Choosing $\delta = \varepsilon'/(\lvert x\rvert + \lvert y\rvert + 1)$ ensures that $S_\delta(x,y)$ maps into $B_{\varepsilon'}(xy)$."
   alt="Geometric rectangle decomposition and error bounds for multiplication." %}

---

## Continuous inversion on the punctured real line

To study division, we consider the reciprocal map $x \mapsto 1/x$. Because division by zero is undefined, the origin must be removed.

Let $\mathbb{R}^\times = \mathbb{R} \setminus \lbrace 0\rbrace$ denote the punctured real line, equipped with the subspace topology $\tau_{\mathbb{R}^\times}$ inherited from the standard topology on $\mathbb{R}$ ([Definition 4.3]({{ site.baseurl }}/point-set-topology/lecture-04/#definition-4-3-subspace-topology)).

Consider the inversion map:
$$f : \mathbb{R}^\times \to \mathbb{R}^\times, \qquad f(x) = \frac{1}{x}.$$

To apply [Lemma 8.1](#lemma-8-1-basis-criterion-for-continuity), we first identify a convenient basis for the subspace topology on $\mathbb{R}^\times$.

{% capture lem_subspace_basis_rx %}
The collection of open intervals
$$\mathcal{B}_{\mathbb{R}^\times} = \lbrace B_\varepsilon(x) \;:\; x \in \mathbb{R}^\times \text{ and } 0 < \varepsilon < |x| \rbrace$$
is a basis for the subspace topology on $\mathbb{R}^\times$.
{% endcapture %}
{% include block.html type="lemma" title="Lemma 8.3 (Subspace Basis for the Punctured Real Line)" content=lem_subspace_basis_rx %}

{% capture lem_subspace_basis_rx_proof %}
By [Lemma 5.3]({{ site.baseurl }}/point-set-topology/lecture-05/#lemma-5-3-basis-for-a-subspace), since open intervals $\lbrace B_\delta(x) : x \in \mathbb{R},\, \delta > 0\rbrace$ form a basis for $\mathbb{R}$, their intersections with $\mathbb{R}^\times$ form a basis for $\tau_{\mathbb{R}^\times}$.

For any $x \in \mathbb{R}^\times$ and any $\varepsilon$ with $0 < \varepsilon < |x|$:
- If $x > 0$, then $x - \varepsilon > 0$, so $B_\varepsilon(x) = (x-\varepsilon, x+\varepsilon) \subseteq (0, \infty) \subseteq \mathbb{R}^\times$.
- If $x < 0$, then $x + \varepsilon < 0$, so $B_\varepsilon(x) = (x-\varepsilon, x+\varepsilon) \subseteq (-\infty, 0) \subseteq \mathbb{R}^\times$.

In either case, $0 \notin B_\varepsilon(x)$, so
$$B_\varepsilon(x) \cap \mathbb{R}^\times = B_\varepsilon(x).$$
Thus each element of $\mathcal{B}_{\mathbb{R}^\times}$ is an open interval in $\mathbb{R}$ contained entirely within $\mathbb{R}^\times$, and hence belongs to $\tau_{\mathbb{R}^\times}$.

To verify the basis condition: let $U \in \tau_{\mathbb{R}^\times}$ and let $x \in U$. By definition of the subspace topology, $U = W \cap \mathbb{R}^\times$ for some open set $W \in \tau_{\mathbb{R}}$. Since $x \in W$ and $W$ is open in $\mathbb{R}$, there exists $\delta > 0$ such that $B_\delta(x) \subseteq W$. Setting
$$\varepsilon = \min\left\lbrace \delta, \; \frac{|x|}{2} \right\rbrace > 0,$$
we have $\varepsilon < |x|$ (so $B_\varepsilon(x) \subseteq \mathbb{R}^\times$) and $B_\varepsilon(x) \subseteq B_\delta(x) \subseteq W$. Therefore:
$$x \in B_\varepsilon(x) \subseteq W \cap \mathbb{R}^\times = U.$$
By [Definition 3.6]({{ site.baseurl }}/point-set-topology/lecture-03/#definition-3-6-basis-for-a-topology), $\mathcal{B}_{\mathbb{R}^\times}$ is a basis for $\tau_{\mathbb{R}^\times}$. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Lemma 8.3" content=lem_subspace_basis_rx_proof %}

{% include figure.html
   src="point-set-topology/lecture-08/inversion-subspace-intervals.svg"
   caption="Figure 8.3: Subspace basis and inversion on $\mathbb{R}^\times$. For $x > 0$ and $\varepsilon < \lvert x\rvert$, the interval $(x-\varepsilon, x+\varepsilon)$ does not contain $0$. The preimage under $f(t) = 1/t$ is the open interval $\left(\frac{1}{x+\varepsilon}, \frac{1}{x-\varepsilon}\right)$, which is open in $\mathbb{R}$ and contained in $\mathbb{R}^\times$, hence open in the subspace topology."
   alt="Real line with punctured origin showing the interval and its reciprocal preimage interval." %}

{% capture thm_inversion %}
The inversion map
$$f : \mathbb{R}^\times \to \mathbb{R}^\times, \qquad f(x) = \frac{1}{x}$$
is continuous with respect to the subspace topology on $\mathbb{R}^\times$.
{% endcapture %}
{% include block.html type="theorem" title="Theorem 8.4 (Continuity of Inversion on the Punctured Real Line)" content=thm_inversion %}

{% capture thm_inversion_proof %}
Claim: this map is continuous. Let us prove this claim.

Since $\mathcal{B}_{\mathbb{R}^\times}$ is a basis for the subspace topology on $\mathbb{R}^\times$ ([Lemma 8.3](#lemma-8-3-subspace-basis-for-the-punctured-real-line)), by [Lemma 8.1](#lemma-8-1-basis-criterion-for-continuity) it suffices to check that $f^{-1}(B_\varepsilon(x))$ is open in $\tau_{\mathbb{R}^\times}$ when $\varepsilon < |x|$.

The basic open set is $B_\varepsilon(x) = (x-\varepsilon, x+\varepsilon)$. We compute its preimage:
$$t \in f^{-1}(B_\varepsilon(x)) \iff f(t) \in B_\varepsilon(x) \iff x-\varepsilon < \frac{1}{t} < x+\varepsilon.$$

We analyze the two cases according to the sign of $x$:

- **Case 1: $x > 0$.**
  Since $0 < \varepsilon < x$, we have $0 < x-\varepsilon < x < x+\varepsilon$.
  Because both endpoints are positive, $1/t > 0$, so $t > 0$.
  The reciprocal function $s \mapsto 1/s$ is strictly decreasing on $(0,\infty)$. Taking reciprocals across the inequality $x-\varepsilon < 1/t < x+\varepsilon$ reverses the inequalities:
  $$\frac{1}{x+\varepsilon} < t < \frac{1}{x-\varepsilon}.$$
  Therefore, the preimage is the open interval:
  $$f^{-1}(B_\varepsilon(x)) = \left(\frac{1}{x+\varepsilon}, \; \frac{1}{x-\varepsilon}\right).$$

- **Case 2: $x < 0$.**
  Since $0 < \varepsilon < -x = |x|$, we have $x-\varepsilon < x < x+\varepsilon < 0$.
  Both endpoints are negative, so $1/t < 0$, forcing $t < 0$.
  The reciprocal function $s \mapsto 1/s$ is also strictly decreasing on $(-\infty, 0)$. Taking reciprocals across $x-\varepsilon < 1/t < x+\varepsilon$ again reverses the inequalities:
  $$\frac{1}{x+\varepsilon} < t < \frac{1}{x-\varepsilon}.$$
  (For example, with $x = -2$ and $\varepsilon = 1$: $x-\varepsilon = -3$ and $x+\varepsilon = -1$, giving $-1 < t < -1/3$, so the interval is $(-1, -1/3)$).
  Thus in this case too:
  $$f^{-1}(B_\varepsilon(x)) = \left(\frac{1}{x+\varepsilon}, \; \frac{1}{x-\varepsilon}\right).$$

In both cases, $f^{-1}(B_\varepsilon(x))$ is an open interval $(a,b) \subseteq \mathbb{R}$.
Furthermore, because $a$ and $b$ have the same sign (both positive in Case 1, both negative in Case 2), the interval $(a,b)$ does not contain $0$, so
$$f^{-1}(B_\varepsilon(x)) \subseteq \mathbb{R}^\times.$$

Because $(a,b)$ is open in $\mathbb{R}$ and is contained in $\mathbb{R}^\times$, it satisfies
$$(a,b) = (a,b) \cap \mathbb{R}^\times,$$
which by definition of the subspace topology means that $(a,b)$ is open in $\mathbb{R}^\times$.

Thus $f^{-1}(B_\varepsilon(x)) \in \tau_{\mathbb{R}^\times}$ for every basis element $B_\varepsilon(x) \in \mathcal{B}_{\mathbb{R}^\times}$.

So this proves that $f$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="proof" title="Proof of Theorem 8.4" content=thm_inversion_proof %}

---

## Exercises

{% capture ex81_content %}
Fix a constant $a \in \mathbb{R}$. Define the **translation map**
$$T_a : \mathbb{R} \to \mathbb{R}, \qquad T_a(x) = x + a,$$
where $\mathbb{R}$ carries the standard topology.
Prove that $T_a$ is continuous using [Lemma 8.1](#lemma-8-1-basis-criterion-for-continuity).
{% endcapture %}
{% capture ex81_sol %}
Let $\mathcal{B}_{\mathbb{R}} = \lbrace B_\varepsilon(z) : z \in \mathbb{R},\, \varepsilon > 0 \rbrace$ be the standard basis of open intervals for $\mathbb{R}$.
By Lemma 8.1, it suffices to prove that $T_a^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}$ for every $z \in \mathbb{R}$ and every $\varepsilon > 0$.

We compute the preimage directly:
$$x \in T_a^{-1}(B_\varepsilon(z)) \iff T_a(x) \in (z-\varepsilon, z+\varepsilon) \iff z-\varepsilon < x+a < z+\varepsilon.$$
Subtracting $a$ across the inequalities:
$$(z-a) - \varepsilon < x < (z-a) + \varepsilon.$$
This is precisely the open interval $B_\varepsilon(z-a) = ((z-a)-\varepsilon, (z-a)+\varepsilon)$.

Since $B_\varepsilon(z-a)$ is an open interval in $\mathbb{R}$, it is open in the standard topology.

By Lemma 8.1, $T_a$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 8.1 (Continuity of translation maps)" content=ex81_content solution=ex81_sol %}

{% capture ex82_content %}
Fix a constant $c \in \mathbb{R}$. Define the **scalar multiplication map**
$$m_c : \mathbb{R} \to \mathbb{R}, \qquad m_c(x) = cx,$$
where $\mathbb{R}$ carries the standard topology.
Prove that $m_c$ is continuous using [Lemma 8.1](#lemma-8-1-basis-criterion-for-continuity).
{% endcapture %}
{% capture ex82_sol %}
By Lemma 8.1, it suffices to show that $m_c^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}$ for every $z \in \mathbb{R}$ and every $\varepsilon > 0$.

We separate into two cases:

- **Case 1: $c = 0$.**
  Then $m_c(x) = 0$ for all $x \in \mathbb{R}$, which is a constant map.
  By Exercise 7.4 in Lecture 7, every constant map is continuous.

- **Case 2: $c \ne 0$.**
  Let $z \in \mathbb{R}$ and $\varepsilon > 0$. We compute the preimage of $B_\varepsilon(z) = (z-\varepsilon, z+\varepsilon)$:
  $$x \in m_c^{-1}(B_\varepsilon(z)) \iff z-\varepsilon < cx < z+\varepsilon.$$
  - If $c > 0$, dividing by $c$ preserves the inequalities:
    $$\frac{z-\varepsilon}{c} < x < \frac{z+\varepsilon}{c} \iff \frac{z}{c} - \frac{\varepsilon}{c} < x < \frac{z}{c} + \frac{\varepsilon}{c}.$$
    This is the open interval $B_{\varepsilon/c}(z/c)$.
  - If $c < 0$, dividing by $c$ reverses the inequalities:
    $$\frac{z+\varepsilon}{c} < x < \frac{z-\varepsilon}{c} \iff \frac{z}{c} - \frac{\varepsilon}{|c|} < x < \frac{z}{c} + \frac{\varepsilon}{|c|}.$$
    This is the open interval $B_{\varepsilon/|c|}(z/c)$.

In both cases, $m_c^{-1}(B_\varepsilon(z)) = B_{\varepsilon/|c|}(z/c)$, which is an open interval in $\mathbb{R}$, hence open in the standard topology.

By Lemma 8.1, $m_c$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 8.2 (Continuity of scalar multiplication)" content=ex82_content solution=ex82_sol %}

{% capture ex83_content %}
Define the **subtraction map**
$$S : \mathbb{R}^2 \to \mathbb{R}, \qquad S(x,y) = x - y,$$
where $\mathbb{R}$ and $\mathbb{R}^2$ carry their standard topologies.
Prove that $S$ is continuous directly using open squares $S_\delta(x,y)$ and $\varepsilon$-estimates, mimicking the proof of [Theorem 8.2(1)](#proof-of-theorem-8-2-part-1-addition).
{% endcapture %}
{% capture ex83_sol %}
By Lemma 8.1, it suffices to prove that $S^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}^2$ for every $z \in \mathbb{R}$ and every $\varepsilon > 0$.

**Step 1: Local estimate on open squares.**
Let $(x,y) \in \mathbb{R}^2$ and $\delta > 0$. If $(x',y') \in S_\delta(x,y)$, then $|x'-x| < \delta$ and $|y'-y| < \delta$.
We bound the difference:
$$|S(x',y') - S(x,y)| = |(x'-y') - (x-y)| = |(x'-x) - (y'-y)| \le |x'-x| + |y'-y| < \delta + \delta = 2\delta.$$
Choosing $\delta = \varepsilon/2$, we obtain
$$|S(x',y') - S(x,y)| < 2\left(\frac{\varepsilon}{2}\right) = \varepsilon.$$
Since $S(x,y) = x-y$, this implies $S(x',y') \in B_\varepsilon(x-y)$ for all $(x',y') \in S_{\varepsilon/2}(x,y)$, so:
$$S_{\varepsilon/2}(x,y) \subseteq S^{-1}(B_\varepsilon(x-y)).$$

**Step 2: Preimages are open.**
Let $(x,y) \in S^{-1}(B_\varepsilon(z))$ be an arbitrary point. Then $x-y \in B_\varepsilon(z)$.
Because $B_\varepsilon(z)$ is open in $\mathbb{R}$, there exists $\varepsilon' > 0$ such that $B_{\varepsilon'}(x-y) \subseteq B_\varepsilon(z)$ (for instance, $\varepsilon' = \varepsilon - |(x-y)-z| > 0$).

By Step 1:
$$S_{\varepsilon'/2}(x,y) \subseteq S^{-1}(B_{\varepsilon'}(x-y)) \subseteq S^{-1}(B_\varepsilon(z)).$$
Thus, around every point $(x,y) \in S^{-1}(B_\varepsilon(z))$, the basic open square $S_{\varepsilon'/2}(x,y)$ is entirely contained in $S^{-1}(B_\varepsilon(z))$.

By Definition 2.2, $S^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}^2$.
By Lemma 8.1, $S$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 8.3 (Continuity of subtraction)" content=ex83_content solution=ex83_sol %}

{% capture ex84_content %}
Define the **squaring map**
$$q : \mathbb{R} \to \mathbb{R}, \qquad q(x) = x^2,$$
where $\mathbb{R}$ carries the standard topology.
Prove that $q$ is continuous directly using $\varepsilon$-estimates on basic intervals.
{% endcapture %}
{% capture ex84_sol %}
By Lemma 8.1, it suffices to show that $q^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}$ for every basic open interval $B_\varepsilon(z) \subseteq \mathbb{R}$.

**Step 1: Local estimate.**
Let $x \in \mathbb{R}$. For any $x' \in \mathbb{R}$ with $|x'-x| < \delta$ where $0 < \delta \le 1$:
$$|q(x') - q(x)| = |x'^2 - x^2| = |x'-x||x'+x|.$$
By the triangle inequality, $|x'+x| = |(x'-x) + 2x| \le |x'-x| + 2|x| < \delta + 2|x| \le 2|x| + 1$ (since $\delta \le 1$).
Therefore:
$$|q(x') - q(x)| < \delta(2|x| + 1).$$
Given any $\varepsilon' > 0$ with $\varepsilon' \le 1$, set $\delta = \frac{\varepsilon'}{2|x| + 1} \le 1$. Then:
$$|q(x') - q(x)| < \left(\frac{\varepsilon'}{2|x| + 1}\right)(2|x| + 1) = \varepsilon'.$$
Thus $B_\delta(x) \subseteq q^{-1}(B_{\varepsilon'}(x^2))$.

**Step 2: Preimages are open.**
Let $x \in q^{-1}(B_\varepsilon(z))$. Then $x^2 \in B_\varepsilon(z)$.
Since $B_\varepsilon(z)$ is open, there exists $\varepsilon' > 0$ (which we may take $\le 1$) such that $B_{\varepsilon'}(x^2) \subseteq B_\varepsilon(z)$.
By Step 1, choosing $\delta = \frac{\varepsilon'}{2|x|+1}$, we have:
$$B_\delta(x) \subseteq q^{-1}(B_{\varepsilon'}(x^2)) \subseteq q^{-1}(B_\varepsilon(z)).$$
Thus $q^{-1}(B_\varepsilon(z))$ is open in $\mathbb{R}$.
By Lemma 8.1, $q$ is continuous. $\blacksquare$
{% endcapture %}
{% include block.html type="exercise" title="Exercise 8.4 (Continuity of the squaring map)" content=ex84_content solution=ex84_sol %}

---

## At a glance

<div class="at-a-glance-box" markdown="1">

- [Lemma 8.1 (Basis Criterion for Continuity)](#lemma-8-1-basis-criterion-for-continuity): $f : X \to Y$ is continuous iff $f^{-1}(V) \in \tau_X$ for all $V \in \mathcal{B}_Y$.
- [Theorem 8.2 (Continuity of Addition and Multiplication)](#theorem-8-2-continuity-of-addition-and-multiplication): Both $A(x,y) = x+y$ and $M(x,y) = xy$ are continuous $\mathbb{R}^2 \to \mathbb{R}$.
- [Proof of Theorem 8.2, Part 1 (Addition)](#proof-of-theorem-8-2-part-1-addition): $S_{\varepsilon'/2}(x,y) \subseteq A^{-1}(B_{\varepsilon'}(x+y))$ bounds the perturbation by $2(\varepsilon'/2) = \varepsilon'$.
- [Proof of Theorem 8.2, Part 2 (Multiplication)](#proof-of-theorem-8-2-part-2-multiplication): $x'y' - xy = (x'-x)y' + x(y'-y)$ yields bound $\delta(|x|+|y|+1) = \varepsilon'$ for $\delta \le 1$.
- [Lemma 8.3 (Subspace Basis for the Punctured Real Line)](#lemma-8-3-subspace-basis-for-the-punctured-real-line): $\lbrace B_\varepsilon(x) : x \in \mathbb{R}^\times,\, 0 < \varepsilon < |x|\rbrace$ is a basis for $\tau_{\mathbb{R}^\times}$.
- [Theorem 8.4 (Continuity of Inversion on the Punctured Real Line)](#theorem-8-4-continuity-of-inversion-on-the-punctured-real-line): $f(x) = 1/x$ is continuous on $\mathbb{R}^\times$; preimages of basic intervals are open intervals $(1/(x+\varepsilon), 1/(x-\varepsilon))$.
- [Exercise 8.1 (Continuity of translation maps)](#exercise-8-1-continuity-of-translation-maps): $T_a^{-1}(B_\varepsilon(z)) = B_\varepsilon(z-a)$.
- [Exercise 8.2 (Continuity of scalar multiplication)](#exercise-8-2-continuity-of-scalar-multiplication): $m_c^{-1}(B_\varepsilon(z)) = B_{\varepsilon/|c|}(z/c)$.
- [Exercise 8.3 (Continuity of subtraction)](#exercise-8-3-continuity-of-subtraction): $S_{\varepsilon'/2}(x,y) \subseteq S^{-1}(B_{\varepsilon'}(x-y))$.
- [Exercise 8.4 (Continuity of the squaring map)](#exercise-8-4-continuity-of-the-squaring-map): Error bounded by $\delta(2|x|+1)$.

</div>

---

## Further reading

**Munkres, *Topology* (2nd ed.), §18.** Lemma 18.1 proves the basis criterion for continuity and extends it to subbases. Section 18 also proves that algebraic combinations of continuous real-valued functions are continuous.

**Morris, *Topology Without Tears*, Chapter 4.** Sections 4.2–4.3 demonstrate continuity proofs via bases and provide parallel $\varepsilon$-$\delta$ comparisons.
