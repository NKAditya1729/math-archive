# Lecture 12 — build report

## Coverage
Solves the exercise from Lecture 11 proving that points in $\mathbb{R}^m$ have open complements and are therefore closed. Defines the closure $\overline{A}$ of an arbitrary subset $A \subseteq X$ as the set of points whose every open neighbourhood intersects $A$, and computes explicit closures of open intervals and open discs. Proves that the closure $\overline{A}$ is closed in $X$, that a subset is closed if and only if $A = \overline{A}$, and that closure is idempotent ($\overline{\overline{B}} = \overline{B}$), concluding that $\overline{A}$ is the smallest closed subset containing $A$.

## Fidelity checks
Units in skeleton: 6. Units in page: 6. Order preserved: yes.
Numbered objects preserved: Lemma 12.1 (Points in $\mathbb{R}^m$ are Closed), Definition 12.2 (Closure of a Subset), Example 1 (Closure of an Open Interval), Example 2 (Closure of the Open Unit Disc), Lemma 12.3 (The Closure is Closed), Proposition 12.4 (Characterization of Closed Sets via Closure), Corollary 12.5 (Idempotence of the Closure), Exercises 12.1–12.2.
Untraceable proof steps: 0. Every logical step in the singleton complement proof, the closure computations, the union of open sets $X \setminus \overline{A} = \bigcup U_x$, and the mutual inclusions is spoken aloud in transcript lines 1–234.
Supplements: 1, approximately 4% of page length.
Vocabulary gate: passed — no forward concepts ("dense", "metric space", or "Cauchy sequence") are used anywhere on the page, including in supplements and exercise solutions.

## Corrections raised
1. **Target inclusion in proof of Proposition 12.4**:
   - **Transcript quote:** *"It's, it is enough to show that A closure is contained in U. Okay, so taking complements, so we should prove this. To show this, it suffices to show that X minus A closure contains X minus A, and which is what we are going to prove... Let X belong to X minus A... as A is closed... This implies X minus A is open. Yeah, so let us denote this open subset by U."* (lines 176–184).
   - **Ruling & reasoning:** As registered in `context/known-defects.md` (line 68), the phrase *"it is enough to show that $\overline{A}$ is contained in $U$"* is an early slip of notation before $U = X \setminus A$ was introduced. The target inclusion is $\overline{A} \subseteq A$, which by taking complements is equivalent to $X \setminus A \subseteq X \setminus \overline{A}$. Raised Correction Note in the text.

## Transcription artefacts handled silently
- "X bar... Xm in Rn" — rendered as point $x = (x_1, \dots, x_m) \in \mathbb{R}^m$.
- "S epsilon to the by four around this point" — rendered as basic hypercube $S_{\varepsilon/4}(x)$.
- "ball of neighborhood radius zero epsilon" — rendered as open ball/interval $B_\varepsilon(0)$.
- "A bar" / "A closure" — rendered uniformly as closure $\overline{A}$.
- "B closure closure" — rendered as $\overline{\overline{B}}$.

## Open questions
None. Every proof was articulated verbally without board-only algebraic gaps.

## Figures drawn
3 SVGs authored and placed directly in their corresponding units:
1. `closure-open-interval.svg` — Cue: *"Let's take this interval zero, one, and let's see what its closure is... if x is strictly less than zero, then x does not belong to A closure... The only possible points which could be in the closure are zero and one... epsilon by two belongs to this ball, and epsilon by two is contained in zero, one... therefore A closure in this case is precisely the closed interval zero, one."* (Placed in Example 1).
2. `closure-open-disc.svg` — Cue: *"So let's give an example in R two... A is equal to those x comma y in R two such that x square plus y square is strictly less than one... A closure is exactly the set x comma y in R two such that x square plus y square is less than or equal to one... So A closure is just adding the boundary, this boundary circle, to A."* (Placed in Example 2).
3. `closure-is-closed-neighborhood.svg` — Cue: *"so it suffices to show that X minus A closure is open... let x be an element in X minus A closure... there exists an open set U containing x and U intersection A is empty... then y has an open subset, namely U, which does not meet A... So roughly, this says that if you take any point here, we can find this small neighborhood which does not meet the closure... And the complement... is open."* (Placed in Lemma 12.3).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 12 as `[PROCESSED]`; forward reference recorded to Lecture 13 (dense subsets, $A$ is dense in $\overline{A}$, open in open is open, closed in closed is closed, pasting lemma).
- **Glossary & Notation**: Added $\overline{A}$, $\overline{\overline{B}}$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchor for Closure (`definition-12-2-closure-of-a-subset`).
- **Reference Registry**: Cited Munkres §17 and Morris Chapter 2.

## Supplements
1 supplement:
1. *Immediate containment $A \subseteq \overline{A}$* — explains why any point in $A$ trivially satisfies the closure condition because every neighbourhood meets $A$ at that point itself.

## Verification rhythm retrofit
- **Obligation statements restored (4):**
  - Lemma 12.1: *"So let's just do this exercise... And we wanna show that the complement of this point... is an open subset, right? So how will we prove this? We claim that S epsilon by four of X is completely contained inside Rn minus this A1 up to AM... So let's prove this"* [`build/tmp/lecture-12-formatted.txt:2, 7-8, 11, 20-21, 28`].
  - Lemma 12.3: *"So let's prove this. So it suffices to show that X minus A closure is open, right? The definition of a closed subset was the complement should be open, so that's what we are gonna show, that the complement is open"* [`build/tmp/lecture-12-formatted.txt:126-128`].
  - Proposition 12.4: *"So let us prove this. So let us assume, first assume that A is closed, right? So we need to show that A is equal to A closure... It is enough to show that A closure is contained in A... To show this, it suffices to show that X minus A contains X minus A closure... So next let us assume that A is equal to A bar, right? We wanted to show that A is closed, right?"* [`build/tmp/lecture-12-formatted.txt:165, 171-172, 176-178, 199, 205`].
  - Corollary 12.5: *"So let's see how to prove this. So proof... from the lemma we get that B closure is a closed subset. And the above proposition says that B closure is closed implies B closure is equal to B closure closure"* [`build/tmp/lecture-12-formatted.txt:213-219`].
- **Closing declarations restored (4):**
  - Lemma 12.1: *"So therefore, the complement is open. Which implies, by the definition of closed subset, the singleton is a closed subset"* [`build/tmp/lecture-12-formatted.txt:37, 42`].
  - Lemma 12.3: *"And each of these is open, and an arbitrary union of open sets is open, so this implies that X minus A closure is open"* [`build/tmp/lecture-12-formatted.txt:154`].
  - Proposition 12.4: *"So this implies that A is equal to A bar. That was one direction of the proposition... so thus A is closed in X, which is exactly what we wanted to prove... So this completes the proof of the proposition"* [`build/tmp/lecture-12-formatted.txt:197-198, 204-206`].
  - Corollary 12.5: *"So taking closure again makes no difference"* [`build/tmp/lecture-12-formatted.txt:212`].

