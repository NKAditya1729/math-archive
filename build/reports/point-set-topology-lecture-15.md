# Lecture 15 — build report

## Coverage
Establishes the sequential criteria in metric spaces, proving that a subset is closed if and only if it contains the limits of all its convergent sequences, and that a map between metric spaces is continuous if and only if it preserves sequence limits. Concludes Part II of the course and pivots into Part III (Connectedness) by framing the topological classification problem up to homeomorphism. Defines disconnected and connected topological spaces, and proves that a space containing a dense connected subset is connected, deducing that the closure of any connected subspace is connected.

## Fidelity checks
Units in skeleton: 7. Units in page: 7. Order preserved: yes.
Numbered objects preserved: Lemma 15.1 (Sequential Criterion for Closed Subsets), Theorem 15.2 (Sequential Criterion for Continuity), Definition 15.3 (Disconnected and Connected Spaces), Proposition 15.4 (Space with Dense Connected Subset is Connected), Corollary 15.5 (Closure of a Connected Subspace is Connected).
Untraceable proof steps: 0. Every logical deduction across all proofs was articulated step-by-step in the audio transcript.
Supplements: 1 (`Connectedness via Clopen Subsets`).
Vocabulary gate: passed — no forward concepts (such as compactness or path connectedness) appear ahead of their introduction in the course map.

## Corrections raised
None. The defects register `context/known-defects.md` lists no entries for Lecture 15.

## Transcription artefacts handled silently
- "A is closed if and only if... if XNs is a sequence in A and XNs converge to X, then X is also in A" — rendered as Lemma 15.1.
- "f is continuous if and only if for every sequence xns converging to x, we have f of xn converge to f of x" — rendered as Theorem 15.2.
- "Suppose there are non-empty open subsets, U and V... U intersection V is empty... and X is the union of both these" — rendered as Definition 15.3.
- "U contained in X be dense... if U is connected, then X is connected" — rendered as Proposition 15.4.
- "A contained in X be a subspace. If A is connected, then the closure is connected" — rendered as Corollary 15.5.

## Open questions
None.

## Figures drawn
3 SVGs authored and verified:
1. `sequential-continuity-delta-epsilon.svg` — Cue: *"So we just take this open ball around f of x of radius epsilon, and we look at its in-inverse image, right? Uh, so since f is continuous, so its inverse image may be some open subset like this... So therefore, there is a small delta, a ball of radius delta around x, which is completely contained in this open subset."* (Placed in Theorem 15.2).
2. `connected-vs-disconnected-space.svg` — Cue: *"Suppose there are non-empty open subsets, U and V. So they are non-empty, both of them, that's important, such that U in-- So U intersection V is empty. They are disjoint. And X is the union of both these. Right? So then we say that X is disconnected. Otherwise... X is connected."* (Placed in Definition 15.3).
3. `dense-connected-subset-intersection.svg` — Cue: *"X is a disjoint union of U one and U two, right? So now we simply intersect both sides with U... So as U is dense in X, so as U is dense in X, this implies that U intersection U one is non-empty, and U intersection U two is non-empty, right? But this, but this shows that U is disconnected Which is a contradiction."* (Placed in Proposition 15.4).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 15 as `[PROCESSED]`; forward reference recorded to Lecture 16 (connectedness of $[0,1]$ via supremum, $\mathbb{R}$ connected, intervals as connected subsets of $\mathbb{R}$).
- **Glossary & Notation**: Registered $X = U \sqcup V$ (disconnection) and $\text{connected}$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Connected space (`definition-15-3-connected-and-disconnected-spaces`).
- **Reference Registry**: Cited Munkres §21 and §23, Morris Chapter 6 and Chapter 3.

## Supplements
1. `Connectedness via Clopen Subsets`: Explains the equivalent definition that a space $X$ is connected if and only if its only clopen subsets are $\varnothing$ and $X$.

## Verification rhythm retrofit
- **Obligation statements restored (5):**
  - Lemma 15.1 recall statement & target: *"Recall we had proved that A is closed in a topological space if and only if A is equal to A closure, right? So we will use this criteria... it's enough to show that A is equal to A closure if and only if XN belongs to A and XN converges to X, then X belongs to A"* [`build/tmp/lecture-15-formatted.txt:17-21`].
  - Lemma 15.1 ($\implies$) obligation: *"first assume that A is equal to A closure, right? So then we have to show that the set A, it has this property"* [`build/tmp/lecture-15-formatted.txt:22-23`].
  - Lemma 15.1 ($\impliedby$) converse obligation: *"Conversely, suppose A has this property... and we want to show that A is equal to A closure. So let X be an element of A closure. It's obvious that A is contained in A closure, so we just have to prove the converse"* [`build/tmp/lecture-15-formatted.txt:29-34`].
  - Theorem 15.2 ($\impliedby$) converse target: *"So to prove the converse means we are given that f satisfies a particular property... and we have to show that f is continuous. So to show that f is continuous, it suffices to show that the inverse image of a closed subset is closed... So to show that f inverse Z is closed, we will show that f inverse Z is equal to its closure"* [`build/tmp/lecture-15-formatted.txt:82-86, 91`].
  - Proposition 15.4 proof setup: *"So let us prove this. So let us assume that X is disconnected and arrive at a contradiction"* [`build/tmp/lecture-15-formatted.txt:175-176`].
- **Method signposting & Case announcements restored (2):**
  - Theorem 15.2 opening: *"We first assume that f is continuous"* [`build/tmp/lecture-15-formatted.txt:52`].
  - Corollary 15.5 subspace and density recall: *"Recall that... when we talk about A and A closure, all these are subsets of X, and we are always giving these the subspace topology. So recall that we had proved that A is dense in A closure"* [`build/tmp/lecture-15-formatted.txt:193-195`].
- **Closing declarations restored (5):**
  - Lemma 15.1 ($\implies$): *"Thus, X [A] has this property"* [`build/tmp/lecture-15-formatted.txt:27`].
  - Lemma 15.1 ($\impliedby$): *"So this implies that X belongs to A. Thus A is equal to A closure. So thus A is closed"* [`build/tmp/lecture-15-formatted.txt:40-43`].
  - Theorem 15.2 ($\implies$): *"So by definition of convergence, this implies that f of xn converges to f of x. So this proves one part of the lemma"* [`build/tmp/lecture-15-formatted.txt:78-79`].
  - Theorem 15.2 ($\impliedby$): *"So we started with the point x in f inverse Z closure, and we proved that x belongs to f inverse Z. So this implies that f inverse Z is equal to f inverse Z closure. So this implies that f inverse Z is closed. Which implies that f is continuous"* [`build/tmp/lecture-15-formatted.txt:108-112`].
  - Proposition 15.4 closing: *"But this shows that U is disconnected Which is a contradiction. So this implies that our hypothesis was wrong, so that means X is connected"* [`build/tmp/lecture-15-formatted.txt:185-187`].

