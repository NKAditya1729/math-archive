# Lecture 23 — build report

## Coverage
Opens Part IV of the course by defining the Hausdorff ($T_2$) separation axiom and proving that the Hausdorff property is preserved under Cartesian products and subspace restriction. Formulates compactness via open covers and finite subcovers, establishing the course-wide convention that all compact spaces are assumed to be Hausdorff. Demonstrates that the real line $\mathbb{R}$ is not compact by exhibiting an explicit unbounded open cover, and proves that the closed unit interval $[0, 1]$ is compact via a supremum argument.

## Fidelity checks
Units in skeleton: 6. Units in page: 6. Order preserved: yes.
Numbered objects preserved: Definition 23.1 (Hausdorff Space), Proposition 23.2 (Binary Products of Hausdorff Spaces), Exercise 23.1 (Arbitrary Products of Hausdorff Spaces), Proposition 23.3 (Subspaces of Hausdorff Spaces), Definition 23.4 (Open Cover and Compactness), Example 23.5 ($\mathbb{R}$ is Not Compact), Theorem 23.6 (Compactness of $[0, 1]$).
Untraceable proof steps: 0. Every proof step across Propositions 23.2 and 23.3, Example 23.5, and Theorem 23.6 is mathematically rigorous and complete.
Supplements: 0 (the lecture presentation is self-contained).
Vocabulary gate: passed — no forward concepts from Lecture 24 or later (such as the Tube Lemma, Heine-Borel, or one-point compactification) appear.

## Corrections raised
None. (The course-wide convention defining compactness only for Hausdorff spaces is recorded under Conventions in `context/known-defects.md` and is given a prominent callout block in the notes).

## Transcription artefacts handled silently
- Spoken "R" rendered as $\mathbb{R}$.
- Spoken "n minus one fourth" rendered as $n - 1/4$.
- Spoken "zero comma one" rendered as $[0, 1]$ (or $(0, 1)$ depending on mathematical context).
- Spoken "x naught" rendered as $x_0$.
- Spoken "x n's" rendered as $x_n$.
- Spoken "U i naught" rendered as $U_{i_0}$.

## Open questions
None.

## Figures drawn
3 SVGs authored and verified:
1. `hausdorff-separation.svg` (Figure 23.1) — Cue: *"Distinct points x one and x two in X, so we have our X, we have x one here, and we have x two here. So there should be two small open sets which contain x one and x two, uh, which are disjoint"* [`build/tmp/lecture-23-formatted.txt:12-14`]. (Placed in Definition 23.1).
2. `hausdorff-product-separation.svg` (Figure 23.2) — Cue: *"y one is here... y two is here... there exists open sets such that y one belongs to V one, y two belongs to V two... Then X cross V 1 and X cross V 2 are open sets in the product topology... This is X cross V 2, and this is X cross V 1"* [`build/tmp/lecture-23-formatted.txt:28-37`]. (Placed in Proposition 23.2).
3. `compactness-unit-interval-supremum.svg` (Figure 23.3) — Cue: *"So we have zero, we have one, and let's say our x naught is here. So x naught is gonna be in some open set U i naught... there is an epsilon positive... we choose some x m... zero comma x m is covered by a finite union... zero comma x naught plus epsilon"* [`build/tmp/lecture-23-formatted.txt:127-160`]. (Placed in Theorem 23.6).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 23 as `[PROCESSED]`; forward reference recorded to Lecture 24 (The Tube Lemma and products of compact spaces).
- **Concept Index (`site/_data/concepts.yml`)**: Added entries for Hausdorff space (`definition-23-1-hausdorff-space`) and Compact space (`definition-23-4-compact-space`).
- **Reference Registry**: Appended L23 citations for Munkres §17, §26 and Morris Chapter 7.

## Verification rhythm retrofit
- **Obligation statements preserved/restored (5):**
  - Proposition 23.2 obligation: *"So let's say we have two points, x one, y one and x two, y two... since x one, y one is not equal to x two, y two, so this implies either y one is not equal to y two or x one is not equal to x two"* [`build/tmp/lecture-23-formatted.txt:21, 23`].
  - Proposition 23.3 obligation: *"if you take any Y 1 and Y 2, then since X is Hausdorff, there is an open set U 1 containing Y 1, U 2 containing Y 2 such that U 1 intersection U 2 is empty"* [`build/tmp/lecture-23-formatted.txt:51`].
  - Example 23.5 obligation: *"to say that R is not compact, it is enough to produce an open cover for R which has no finite sub-cover"* [`build/tmp/lecture-23-formatted.txt:82`].
  - Theorem 23.6 aim & obligation: *"So our aim is to find a finite sub-cover of this. So we need to show that this has a finite sub-cover"* [`build/tmp/lecture-23-formatted.txt:106-107`].
  - Theorem 23.6 Step 3 & 4 claims: *"So we claim that x naught is also in S... So now, next we claim x naught is equal to one"* [`build/tmp/lecture-23-formatted.txt:123, 152`].
- **Method signposting & Case announcements preserved/restored (3):**
  - Standing convention announcement: *"for the rest of this course we will be interested only in Hausdorff topological spaces. So if nothing is mentioned, then it's safe to assume that the topological space we are working with is Hausdorff"* [`build/tmp/lecture-23-formatted.txt:61-62`].
  - Example 23.5 construction: *"So what we do is we take any n, n+1, and we take n-1/4 and n+1+1/4... clearly, any finite sub-collection of intervals... will not cover R"* [`build/tmp/lecture-23-formatted.txt:85, 92`].
  - Theorem 23.6 contradiction assumption: *"So once again, if x naught is strictly less than one, then that would mean that there is some epsilon positive... which contradicts the assumption that x naught was a supremum"* [`build/tmp/lecture-23-formatted.txt:154, 163`].
- **Closing declarations preserved/restored (4):**
  - Proposition 23.2 closing: *"So clearly, X 1 comma Y 1 is in X cross V 1, X 2 comma Y 2 is in X cross V 2, and the intersection is empty... So this shows that X cross Y is Hausdorff"* [`build/tmp/lecture-23-formatted.txt:38-39`].
  - Proposition 23.3 closing: *"these are disjoint open subsets of Y. Thus, Y is Hausdorff"* [`build/tmp/lecture-23-formatted.txt:53, 55`].
  - Example 23.5 closing: *"So thus, this cover has no finite sub-cover. Thus, R is not compact"* [`build/tmp/lecture-23-formatted.txt:94-95`].
  - Theorem 23.6 closing: *"So therefore, this proves that the open cover we started with has a finite subcover. Thus, this interval is compact. So this completes the proof of theorem"* [`build/tmp/lecture-23-formatted.txt:172-174`].