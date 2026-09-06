# Lecture 14 — build report

## Coverage
Introduces metric spaces and distance functions, verifying that the Euclidean distance on $\mathbb{R}^n$ defines a metric via the Cauchy–Schwarz inequality. Defines open balls, the metric topology, and characterizes open sets via $\varepsilon$-balls. Introduces sequence convergence in metric spaces and proves the sequential characterization of the closure: a point $x$ belongs to $\overline{A}$ if and only if a sequence in $A$ converges to $x$.

## Fidelity checks
Units in skeleton: 6. Units in page: 6. Order preserved: yes.
Numbered objects preserved: Definition 14.1 (Metric Space and Metric), Example 1 (Euclidean Metric on $\mathbb{R}^n$), Proposition 14.2 (Cauchy–Schwarz and Euclidean Triangle Inequality), Definition 14.3 (Open Ball and Metric Topology), Proposition 14.4 (Characterization of Open Sets), Exercise 14.1 (Standard Topology on $\mathbb{R}^n$), Definition 14.5 (Sequence Convergence), Lemma 14.6 (Sequential Characterization of Closure), Example 2 (Closure of Open Disc in $\mathbb{R}^2$ via Sequences).
Untraceable proof steps: 1. Sentences 91–105 ("So we have norm x minus y whole square is equal to… this is equal to… uh, this is equal to… and this is less than equal to… Over here we have used the claim… Whole square, right? So this implies that…") carried the intermediate algebraic computation of the triangle inequality entirely on the blackboard without spoken mathematics. As required by the Gap protocol in `AGENTS.md` and `context/known-defects.md`, this algebra is not reconstructed as lecture content; an Open Question block quotes the transcript gap, and the standard textbook derivation is supplied in a labelled supplement.
Supplements: 1 (`Standard Derivation of the Triangle Inequality via Cauchy–Schwarz`).
Vocabulary gate: passed — no forward concepts from Lecture 15 or later (such as sequential continuity, completeness, or compactness) appear.

## Corrections raised
None. The defect registered for Lecture 14 in `context/known-defects.md` is classified as a **Gap** (board-only algebra), not a Slip or Consequential defect. It has been handled via an Open Question block and a labelled supplement.

## Transcription artefacts handled silently
- "d of x,y is equal to zero if and only if x is equal to y... d of x,y is equal to d of y,x... triangle inequality" — rendered as Definition 14.1.
- "norm of x minus y... the two norm" — rendered with `\lVert x - y \rVert_2`.
- "consider the map, right, this inner product defined as x_i, y_i" — rendered as $\langle x, y \rangle = \sum_{i=1}^n x_i y_i$.
- "B epsilon x is defined to be those y in x such that distance... strictly less than epsilon" — rendered as Definition 14.3.
- "x_n converges to x... for all n greater than equal to N_0, x_n in B epsilon x" — rendered as Definition 14.5.

## Open questions
1. **Board derivation of triangle inequality from Cauchy–Schwarz** (sentences 91–105): The explicit algebraic lines expanding $\lVert x + y \rVert_2^2$ and applying the Cauchy–Schwarz inequality were written on the board and not spoken aloud. The recoverable structure (quadratic $q(t) = \langle y - tx, y - tx \rangle \ge 0$, discriminant $\Delta \le 0 \implies |\langle x, y \rangle| \le \lVert x \rVert_2 \lVert y \rVert_2$) is recorded in Proposition 14.2; the board-only steps are quoted in an Open Question block; the full derivation is provided in a supplement.

## Figures drawn
3 SVGs authored and verified:
1. `triangle-inequality-metric.svg` — Cue: *"And we know that if we have a triangle, right, so this is x, uh, this is z, and this is y, then the distance between x and z is less than equal to the distance between x and y and y and z, yeah?"* (Placed in Definition 14.1).
2. `metric-open-ball-basis.svg` — Cue: *"So yeah, so if we have our topological space X over here. So a set is open if and only if, given any point X, we can find a ball of radius epsilon around X, which is completely contained inside U. Yeah. So the epsilon, of course, depends on X."* (Placed in Proposition 14.4).
3. `sequence-convergence-closure.svg` — Cue: *"Given any point on the boundary, we can find a sequence inside this red region, this region x square plus y square is strictly less than one... shrinking neighborhoods... and inside each neighborhood we choose one point in that intersection... But if we take some point outside... we can find a small neighborhood around this point outside, which does not meet this set A."* (Placed in Lemma 14.6).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 14 as `[PROCESSED]`; forward reference recorded to Lecture 15 (sequential criteria for closed sets and continuity, and introduction to connectedness).
- **Glossary & Notation**: Added $d(x, y)$, $\lVert x \rVert_2$, $\langle x, y \rangle$, $B_\varepsilon(x)$, $x_n \to x$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Metric space (`definition-14-1-metric-space-and-metric`), Metric topology (`definition-14-3-open-ball-and-metric-topology`), and Sequence convergence (`definition-14-5-sequence-convergence`).
- **Reference Registry**: Cited Munkres §20 and Morris Chapter 6.

## Supplements
1. `Standard Derivation of the Triangle Inequality via Cauchy–Schwarz`: Provides the full expansion $\lVert x + y \rVert_2^2 \le (\lVert x \rVert_2 + \lVert y \rVert_2)^2$ that was left on the blackboard.

## Verification rhythm retrofit
- **Obligation statements restored (5):**
  - Example 1 metric verification opening: *"so let us check that this defines a metric... note that the first two conditions are trivial to check... The only nontrivial condition is the triangle inequality, so which we'll prove now"* [`build/tmp/lecture-14-formatted.txt:31-34`].
  - Proposition 14.2 target statement: *"what we need to prove is that with this-- in this notation that the norm of x minus y is less than equal to... And to check that this defines a metric we need the following proposition"* [`build/tmp/lecture-14-formatted.txt:40, 47`].
  - Proposition 14.2 Cauchy–Schwarz claim obligation: *"So we first claim that this absolute value of this quantity is less than equal to into norm y. So let us first prove this claim"* [`build/tmp/lecture-14-formatted.txt:59-60`].
  - Lemma 14.6 ($\implies$) obligation & question-answer target: *"So then we claim that xn converge to x, right? So to prove this, what do we need to show? So we need to show that given any epsilon positive, there exists some N_0 very large, so that, such that... for n greater than equal to N_0, we have xn belongs to B epsilon x, right? So let us show this"* [`build/tmp/lecture-14-formatted.txt:187-191`].
  - Lemma 14.6 ($\impliedby$) converse obligation: *"And conversely, so suppose xn's is a sequence in A such that x n converge to x, then we need to show that x is in A closure, right? So once again, we will use the definition"* [`build/tmp/lecture-14-formatted.txt:205-206`].
- **Method signposting & Case announcements restored (2):**
  - Proposition 14.2 reduction: *"it is enough to check that [$\lVert u + v \rVert_2 \le \lVert u \rVert_2 + \lVert v \rVert_2$]. And this is left as an easy exercise that it's enough to check this"* [`build/tmp/lecture-14-formatted.txt:52-53`].
  - Proposition 14.2 transition from claim to proposition: *"So using this claim, we will now prove the proposition"* [`build/tmp/lecture-14-formatted.txt:90`].
- **Closing declarations restored (4):**
  - Proposition 14.2 Cauchy–Schwarz claim closing: *"Which proves our claim, right? This is the claim which we want to prove"* [`build/tmp/lecture-14-formatted.txt:86, 88`].
  - Proposition 14.2 overall closing: *"So this shows that this R n comma d is a metric space, right? So this proves triangle inequality holds, and therefore, this is a metric space"* [`build/tmp/lecture-14-formatted.txt:106-107`].
  - Lemma 14.6 ($\implies$) closing: *"So this implies for all n greater than equal to N_0, xn belongs to B epsilon x, which implies that xn converges to x. So in the first part of the proof, we showed that if x is in A closure, then we can find a sequence of xn's in A, so that xn's converge to x"* [`build/tmp/lecture-14-formatted.txt:200, 203`].
  - Lemma 14.6 ($\impliedby$) closing: *"So thus U intersection A is non-empty, right? So thus x belongs to A closure"* [`build/tmp/lecture-14-formatted.txt:214-215`].

