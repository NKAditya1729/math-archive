# Lecture 16 — build report

## Coverage
Proves that the closed unit interval $[0, 1]$ is connected using the supremum argument on the set $S = \{x \in [0, 1] : [0, x] \subseteq U\}$. Deduces that all closed intervals $[a, b]$ and the full real line $\mathbb{R}$ are connected, correcting a transcript slip regarding $[a, b]$. Completely classifies the connected subspaces of $\mathbb{R}$ as the intervals, and proves that the continuous image of any connected space is connected.

## Fidelity checks
Units in skeleton: 5. Units in page: 5. Order preserved: yes.
Numbered objects preserved: Proposition 16.1 (Connectedness of $[0, 1]$), Exercise 16.1 (Connectedness of $[a, b]$), Corollary 16.2 (Connectedness of $\mathbb{R}$), Theorem 16.3 (Connected Subspaces of $\mathbb{R}$ Are Intervals), Proposition 16.4 (Continuous Image of a Connected Space is Connected).
Untraceable proof steps: 0. All steps of the supremum argument, interval classification, and continuous image proofs were fully articulated in the spoken lecture.
Supplements: 0.
Vocabulary gate: passed — no forward concepts (path connectedness, product space connectedness, or components) appear.

## Corrections raised
1. **Corollary 16.2 (`contradicts the fact that [a, b] is disconnected`)**:
   - *Transcript:* "which contradicts the fact that $[a,b]$ is disconnected." (Sentences 114, 119).
   - *Correction:* Should be "which contradicts the fact that $[a,b]$ is **connected**."
   - *Evidence:* Proposition 16.1 and Exercise 16.1 proved $[a, b]$ is connected; assuming $\mathbb{R}$ disconnected leads to $[a, b]$ being disconnected, contradicting its established connectedness. This is a registered Slip in `context/known-defects.md`.

## Transcription artefacts handled silently
- "S is equal to those x in [0,1] such that this entire interval [0,x] is contained in U" — rendered as the defining set $S$ in Proposition 16.1.
- "now let a be the supremum... a also belongs to U... a has to be equal to one" — rendered as Steps 1 and 2 of the supremum argument.
- "Y is one of the following... basically it's an interval" — rendered as Theorem 16.3.
- "f of X intersected with U and f of X intersected with V... are disjoint. Need not be empty. So this is just a word of caution." — rendered in the proof of Proposition 16.4.

## Open questions
None.

## Figures drawn
3 SVGs authored and verified:
1. `supremum-connectedness-interval.svg` — Cue: *"So if you were to make a picture, so this is our interval [0,1], right? Our U may be some combination of open sets... this is our point a, and we have the sequence of a n's... if a is strictly less than one... then there is epsilon positive... this interval a plus epsilon by two is completely contained in U."* (Placed in Proposition 16.1).
2. `connected-subspaces-real-line.svg` — Cue: *"So here we have our real line, and our Y is some subset. So we take the infimum of, infimum and supremum of all elements in Y... If not, then there exists C which is contained in this open interval such that C does not belong to Y... we can write Y as Y intersection minus infinity comma C disjoint union Y intersection C comma infinity."* (Placed in Theorem 16.3).
3. `continuous-image-connected.svg` — Cue: *"If not, then there exists open subsets U and V such that f of X is the disjoint union... so this implies that we can easily check that X is equal to f inverse of U disjoint union f inverse of V... as f is continuous, both are open... contradicts connectedness of X."* (Placed in Proposition 16.4).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 16 as `[PROCESSED]`; forward reference recorded to Lecture 17 (connectedness of product spaces, union lemma, $S^n$ connected via stereographic charts).
- **Glossary & Notation**: Added $S = \lbrace x \in [0,1] : [0,x] \subseteq U \rbrace$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Connected subspaces of $\mathbb{R}$ (`theorem-16-3-connected-subspaces-of-r`).
- **Reference Registry**: Cited Munkres §23 and §24, Morris Chapter 3.

## Supplements
None.

## Verification rhythm retrofit
- **Obligation statements restored (5):**
  - Proposition 16.1 proof setup: *"So let us assume that [0,1] is not connected, right? So then there exists non-empty open sets U and V... [0,1] is a disjoint union U disjoint union V"* [`build/tmp/lecture-16-formatted.txt:6-8`].
  - Proposition 16.1 Step 1 claim: *"So we claim that a is in U"* [`build/tmp/lecture-16-formatted.txt:33`]; Step 2 claim: *"Now we claim that a has to be equal to one"* [`build/tmp/lecture-16-formatted.txt:65`].
  - Corollary 16.2 setup & reduction: *"if not, then we can write R as a disjoint union of two open sets... intersecting this relation... with the interval AB, this implies AB intersected with U disjoint union AB intersected with V"* [`build/tmp/lecture-16-formatted.txt:102, 106`].
  - Theorem 16.3 claim for $a < b$: *"then we claim that the open interval A comma B is contained in Y"* [`build/tmp/lecture-16-formatted.txt:146`].
  - Proposition 16.4 setup & preimages: *"The proof is easy. So let's see. If not, then there exists open subsets U and V such that f of X is the disjoint union... so this implies that we can easily check that X is equal to f inverse of U disjoint union f inverse of V"* [`build/tmp/lecture-16-formatted.txt:179-182, 195`].
- **Method signposting & Case announcements restored (3):**
  - Proposition 16.1 WLOG choice: *"So one of these contains 0, so we may assume that it is in U: 0 belongs to U"* [`build/tmp/lecture-16-formatted.txt:12-13`].
  - Theorem 16.3 case breakdown: *"if A is equal to B... clearly in this case Y is connected... If A is strictly less than B, then we claim that the open interval A comma B is contained in Y"* [`build/tmp/lecture-16-formatted.txt:141-146`].
  - Proposition 16.4 word of caution: *"U and V are open subsets in Y. So let me emphasize that U intersection V need not be empty... So this is just a word of caution"* [`build/tmp/lecture-16-formatted.txt:185-191`].
- **Closing declarations restored (5):**
  - Proposition 16.1 Step 1: *"So we have proved that a is in U"* [`build/tmp/lecture-16-formatted.txt:46`]; Step 2: *"So therefore, thus a is forced to be one"* [`build/tmp/lecture-16-formatted.txt:85`].
  - Proposition 16.1 overall closing: *"which contradicts non-emptiness of V. Thus, zero comma one cannot be disconnected. So this implies that zero comma one is connected. So this completes the proof"* [`build/tmp/lecture-16-formatted.txt:87-91`].
  - Corollary 16.2 closing: *"So this shows that AB is disconnected, which is a contradiction... which contradicts the fact that AB is connected [transcript slip: disconnected]. Therefore, R with the standard topology is connected"* [`build/tmp/lecture-16-formatted.txt:113-119`].
  - Theorem 16.3 closing: *"So this contradicts the assumption that Y is connected... Thus, the interval A comma B is contained in Y... from this, we can easily conclude that Y has to be of the type mentioned"* [`build/tmp/lecture-16-formatted.txt:159-161, 167`].
  - Proposition 16.4 closing: *"So thus, we have written X as a disjoint union of non-empty open subsets. But this contradicts the connectedness of X, right? So thus, f of X is connected in the subspace topology"* [`build/tmp/lecture-16-formatted.txt:204-206`].

