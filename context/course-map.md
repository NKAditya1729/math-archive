# Course Map — Point-Set Topology

The complete course: **40 lectures, closed**. Lecture 40 ends "this also brings
our course to an end." Lecture 34 arrives as three transcript files but is one
lecture.

This file has two jobs. It tells you **where a lecture sits** so that *Where we
are* can be written. And it gates the vocabulary: **nothing may appear in a
supplement that the course has not yet reached.**

---

## The four parts

The lecturer announces two of these boundaries himself. The other two are
evident from the material. Use these to group the course index page.

| Part | Lectures | Theme |
|---|---|---|
| I | 1–6 | Topological spaces and how to build them |
| II | 7–15 | Continuous maps, closed sets, metric spaces |
| III | 16–22 | Connectedness and path connectedness |
| IV | 23–40 | Compactness, quotients, and separation |

He says at the end of L6: "that sort of brings the first part of this course to
an end." And at the end of L15: "that kind of brings us to an end of the second
part… now we are coming to the third part." Part IV is not announced but begins
cleanly at L23 with Hausdorff and compactness.

---

## Part I — Building spaces (1–6)

**L1.** Power set. Definition of a topology, three conditions, finite/arbitrary
asymmetry stressed. Trivial, discrete, and finite-complement topologies on an
arbitrary set, all three verified in full.

**L2.** Intervals. Property $(\ast)$ on $\mathbb{R}$. $(0,1)$ satisfies it via
$\varepsilon = \min\{x/2,(1-x)/2\}$; $[0,1)$ fails at $0$. Standard topology on
$\mathbb{R}$, all three axioms — the **min argument** appears here first. Open
square $S_\varepsilon(a,b)$. $(\ast)$ restated for $\mathbb{R}^2$; open disc
satisfies, closed disc fails at $(1,0)$. Ends mid-argument.

**L3.** Completes $\mathbb{R}^2$. States $\mathbb{R}^n$ as an exercise. Open
ball $B_\varepsilon(x)$ and $(\ast')$; two exercises, including
$\tau = \tau'$, with the remark that one topology has many descriptions.
Defines **open set**. Defines **basis** (one condition). Open intervals form a
basis for $\mathbb{R}$; squares for $\mathbb{R}^2$, $\mathbb{R}^n$.

**L4.** Lemma: $\bigcup_{W \in \mathcal{B}} W = X$. **The generating
proposition** — a collection $\mathcal{B}$ satisfying (i) it covers $X$ and
(ii) the refinement condition on pairwise intersections generates a topology
$\tau_{\mathcal{B}}$ with $\mathcal{B}$ as basis. Condition (2) $\Rightarrow$
(2′) for $n$ sets, by induction, left as an exercise. Exercise: $\tau =
\tau_{\mathcal{B}}$. **Subspace topology** defined. Examples: trivial, discrete,
and $\mathbb{Z} \subseteq \mathbb{R}$ is discrete.

**L5.** $\mathbb{R} \hookrightarrow \mathbb{R}^2$ as the $x$-axis; subspace
topology equals the standard one. **The comparison lemma** ($\mathcal{B}_1
\subseteq \tau_2 \Rightarrow \tau_1 \subseteq \tau_2$) and its corollary —
used constantly thereafter. Basis for a subspace. Lemma: $\{U \times V\}$
satisfies the two generating conditions. **Product topology** on $X \times Y$.

**L6.** Finite products. **Box topology** $\mathcal{B}_1$ versus **product
topology** $\mathcal{B}_2$ (all but finitely many factors full) on infinite
products; $\tau_2 \subseteq \tau_1$; they agree for finite index sets. The
catalogue of examples: standard $=$ product on $\mathbb{R}^n$ (claim), $S^1$,
$S^n$, $M_n(\mathbb{R}) \cong \mathbb{R}^{n^2}$, transporting a topology along
a bijection, $GL_n(\mathbb{R})$, $O(n)$, $SO(n)$, $\mathbb{C}$ two ways,
$M_n(\mathbb{C})$, $GL_n(\mathbb{C})$, $SL_n(\mathbb{C})$, $U(n)$, $SU(n)$.

---

## Part II — Continuous maps and metric spaces (7–15)

**L7.** **Continuity** by preimages. Identity; inclusion of a subspace;
subspace topology is the smallest making the inclusion continuous. Projections
are continuous; product topology is the smallest making all projections
continuous. Why the box topology fails: the diagonal $\Delta : \mathbb{R} \to
\prod \mathbb{R}$ is not box-continuous. Exercise, plus the basis lemma stated
for next time.

**L8.** Basis criterion for continuity, proved. Addition and multiplication
$\mathbb{R}^2 \to \mathbb{R}$ are continuous, by explicit $\varepsilon$
estimates. $x \mapsto 1/x$ on $\mathbb{R}^{\times}$ is continuous.

**L9.** Composition; restriction to a subspace; corestriction to a subspace
containing the image. **Maps into a product** are continuous iff each component
is — and the remark that this fails for the box topology. Consequences:
$f+g$, $fg$, and $f/g$ where $g$ never vanishes.

**L10.** Standard $=$ product topology on $\mathbb{R}^n$, proved. Worked
example: the projection $\mathbb{R}^n \setminus H' \to H$ from a point, in
coordinates, shown continuous. **Homeomorphism** defined, with two exercises.

**L11.** **Closed sets**; the three dual properties; a topology may be
specified by its closed sets. Continuity via preimages of closed sets. Worked
examples using continuity: $S^1$, $S^n$, $SL_n$, $O(n)$ closed;
$GL_n(\mathbb{R})$ open. Lemma: points are closed in $\mathbb{R}^m$ (exercise).

**L12.** That exercise solved. **Closure** defined. Closure of $(0,1)$ and of
the open disc. $\overline{A}$ is closed; $A$ closed $\iff A = \overline{A}$;
$\overline{\overline{B}} = \overline{B}$. Two exercises; the remark that
$\overline{A}$ is the smallest closed set containing $A$.

**L13.** **Dense** subsets; $A$ is dense in $\overline{A}$. Open in open is
open; closed subsets of a subspace are $Z \cap A$; closed in closed is closed.
**The pasting lemma** for two closed pieces, with $\max$ and $\min$ on
$\mathbb{R}^2$ as the application.

**L14.** **Metric spaces**. The Euclidean metric; Cauchy–Schwarz and the
triangle inequality *(board-heavy — see known-defects)*. The metric topology.
**Convergence**. Lemma: $x \in \overline{A}$ iff some sequence in $A$ converges
to $x$.

**L15.** Closed $\iff$ closed under limits of sequences. **Sequential criterion
for continuity** between metric spaces. Then the turn to Part III:
homeomorphism as sameness, the classification question, **connectedness**
defined. $U$ dense and connected $\Rightarrow X$ connected; $A$ connected
$\Rightarrow \overline{A}$ connected.

---

## Part III — Connectedness (16–22)

**L16.** $[0,1]$ is connected, by the supremum argument. $\mathbb{R}$ is
connected. **The connected subsets of $\mathbb{R}$ are the intervals.**
Continuous image of a connected space is connected.

**L17.** $X \times Y$ connected; $\mathbb{R}^n$ connected. No surjection
$[0,1] \to [0,1] \sqcup [3,4]$. Homeomorphic spaces are equiconnected. Lemma:
$T_1, T_2$ connected with $T_1 \cap T_2 \neq \varnothing$ $\Rightarrow$
$T_1 \cup T_2$ connected. $S^n$ connected via two stereographic charts.

**L18.** **Connected components** as equivalence classes. Each is maximal,
connected, and **closed**. Components of $\mathbb{Q}$ are points. $X$ connected
iff one component.

**L19.** **Path connectedness**. Path connected $\Rightarrow$ connected.
$[0,1]$, $\mathbb{R}^n$, $S^1$, $S^n$ path connected. Which matrix groups are:
$GL_n$ and $O(n)$ are not (surjective determinant); $M_n$ is; $SO(n)$, $U(n)$,
$SU(n)$ are, promised for later. **Path components**; concatenation of paths
via the pasting lemma. Remark: path components need not be closed.

**L20.** That proposition proved. **The topologist's sine-curve-style
counterexample** $C$: the vertical segments at $x = 1/n$, the punctured
$y$-axis segment, and the $x$-axis. Connected but not path connected; two path
components, one connected component; path components need not be closed.

**L21.** **$GL_n(\mathbb{R})^+$ is path connected**, in four steps by
induction, using elementary matrices *(a sketch by his own description — see
known-defects)*.

**L22.** **$GL_n(\mathbb{C})$ is path connected**, by avoiding the finitely
many roots of $\det \gamma(t)$ in $\mathbb{C}$. Continuous image of a path
connected space is path connected; hence $SL_n(\mathbb{R})$ and
$SL_n(\mathbb{C})$.

---

## Part IV — Compactness, quotients, separation (23–40)

**L23.** **Hausdorff**; products and subspaces of Hausdorff are Hausdorff.
**Compactness — defined only for Hausdorff spaces** (see known-defects,
Conventions). $\mathbb{R}$ is not compact. **$[0,1]$ is compact.**

**L24.** Compactness is not inherited by subspaces. **The tube lemma** (see
transcript-quirks — the slice is invisible). $X, Y$ compact $\Rightarrow
X \times Y$ compact. Closed subspace of a compact space is compact.

**L25.** Two exercises from L24 discharged ($\mathbb{R} \cong (0,1)$; the slice
$\{x\}\times Y \cong Y$). Compact subspace of a Hausdorff space is closed.
**Heine–Borel: $Y \subseteq \mathbb{R}^n$ is compact iff closed and bounded.**
$SO(n)$ is compact.

**L26.** Continuous image of a compact set is compact. **Bijective continuous
from a compact space is a homeomorphism.** **Tychonoff stated without proof**
(Munkres §37).

**L27.** **$SO(n)$ is connected**, by induction using $\varphi : SO(n+1) \to
S^n$, the subgroup $H \cong SO(n)$, and left translations as homeomorphisms.

**L28.** $U(n)$, $SU(n)$ connected, sketched. **A metric space is compact iff
every sequence has a convergent subsequence**, both directions in full.

**L29.** The distance function $d_Z$ and its continuity. **The Lebesgue number
lemma**, proved cleanly via $\sum d_{C_i}$.

**L30.** **Local compactness**. $\mathbb{R}^n$ is locally compact. The
separation of a point from a compact set. The shrinking proposition: $x \in W$
open $\Rightarrow \exists V$ with $x \in V \subseteq \overline{V} \subseteq W$
and $\overline{V}$ compact. Motivation for compactification.

**L31.** **The one-point compactification $\hat{X}$** constructed: the two
kinds of open set, all three axioms, Hausdorff, compact, $i$ continuous,
$i(X)$ open and dense.

**L32.** **The universal property** of $\hat{X}$: any Hausdorff $T$ containing
$X$ as an open subspace maps uniquely to $\hat{X}$ collapsing the complement.

**L33.** Remark on compact $X$. **Uniqueness of the one-point
compactification.** The explicit correction to L32's hypothesis. Infinite-
dimensional Hilbert space is not locally compact. Quotients in group theory as
motivation. **$\widehat{\mathbb{R}^n} = S^n$.**

**L34** *(three files, one lecture)*. **The quotient topology**: existence and
uniqueness. **Topological groups**; translations and inversion are
homeomorphisms; the $U^2 \subseteq V$ and $UxU$ lemmas; $G/H$ is Hausdorff for
$H$ closed. **The Grassmannian** $Gr(r,n) = GL_n(\mathbb{R})/P$: Hausdorff,
path connected, compact. Projective spaces as $r = 1$.

**L35.** **Normal** spaces. Every metric space is normal. The shrinking lemma
for normal spaces. Urysohn's conclusion proved easily in the metric case via
$d_A/(d_A + d_B)$.

**L36.** **Urysohn's lemma** in full: the dyadic-style construction of
$\{U_q\}_{q \in \mathbb{Q}}$, the function $f(x) = \inf S_x$, and the four
verifications. *(The definition of $U_q$ is misstated — see known-defects.)*

**L37.** **Tietze's extension theorem**, both parts, via a uniformly Cauchy
sequence built from Urysohn's lemma *(board-heavy in the middle)*.

**L38.** **Second countable**; **regular**. A regular second-countable space is
normal.

**L39.** The bounded metric $d' = \min(d,1)$. The metric
$d(x,y) = \sup_n d'(x_n,y_n)/n$ on **$\mathbb{R}^{\mathbb{N}}$** induces the
product topology. *(Read "R n" as the countable product throughout.)*

**L40.** **Urysohn's metrization theorem**: a regular second-countable space
embeds in $\mathbb{R}^{\mathbb{N}}$ and is therefore metrisable. Course ends.

---

## Vocabulary gating

A supplement may use only terms the course has already defined. The table gives
the first lecture at which each becomes available.

| Available from | Terms |
|---|---|
| L1 | topology, topological space, power set, trivial / discrete / finite-complement topology |
| L2–L3 | interval, property $(\ast)$, standard topology, open square, open ball, **open set**, **basis** |
| L4–L6 | generated topology $\tau_{\mathcal{B}}$, subspace topology, product topology, box topology |
| L7–L10 | **continuous map**, projection, diagonal, **homeomorphism** |
| L11–L13 | **closed set**, **closure**, dense, pasting lemma |
| L14–L15 | **metric space**, metric topology, convergence, **connected** |
| L16–L20 | connected components, **path connected**, path components |
| L23–L26 | **Hausdorff**, **compact**, open cover, finite subcover, tube lemma, bounded |
| L28–L30 | sequential compactness, Lebesgue number, **locally compact** |
| L31–L33 | one-point compactification $\hat{X}$ |
| L34 | **quotient topology**, topological group, Grassmannian |
| L35–L38 | **normal**, **regular**, **second countable** |
| L39–L40 | countable product $\mathbb{R}^{\mathbb{N}}$, **metrisable** |

**Never available** — the course does not reach these, and no supplement may
use them: interior, boundary, limit point (as a technical term), subbasis,
order topology, first countable, separable, Lindelöf, completeness, Baire,
Tychonoff's proof, nets, filters, fundamental group, homotopy, covering space,
compactly generated, Stone–Čech, paracompact, $T_0$/$T_1$/$T_3$/$T_4$ notation.

The temptation to reach for "limit point", "interior", or "$T_2$" is strong,
especially in Part IV where the textbooks use them freely. Resist it. He builds
these notions from nothing and a supplement using an undefined word undoes
that.

---

## Adding a course

When Real Analysis begins, create `context/course-map-real-analysis.md` on this
pattern. Keep courses in separate files. A supplement in one may link to a
lecture in the other only if that lecture is already published.
