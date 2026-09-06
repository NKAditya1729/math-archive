# Lecture 13 — build report

## Coverage
Defines dense subsets of a topological space and proves that every subset $A$ is dense in its closure $\overline{A}$ with respect to the subspace topology. Establishes transitivity properties for subspace topologies, showing that an open subset of an open subspace is open, characterizing closed subsets of a subspace as $Z \cap A$, and proving that a closed subset of a closed subspace is closed. Proves the Pasting Lemma for maps defined on closed coverings and applies it to prove that the maximum and minimum functions on $\mathbb{R}^2$ are continuous.

## Fidelity checks
Units in skeleton: 7. Units in page: 7. Order preserved: yes.
Numbered objects preserved: Definition 13.1 (Dense Subset), Proposition 13.2 ($A$ is Dense in Its Closure), Proposition 13.3 (Open in Open is Open), Lemma 13.4 (Closed Subsets of a Subspace), Corollary 13.5 (Closed in Closed is Closed), Proposition 13.6 (Closedness Criterion on Closed Pieces), Theorem 13.7 (The Pasting Lemma), Exercises 13.1–13.3.
Untraceable proof steps: 0. Every logical step and set-theoretic identity in all proofs (including $V = U \cap \overline{A} \implies V \cap A = U \cap A \ne \varnothing$, $A \setminus (U \cap A) = A \cap (X \setminus U)$, and $(f|_A)^{-1}(Z) = f^{-1}(Z) \cap A$) is spoken aloud in transcript lines 1–142.
Supplements: 0.
Vocabulary gate: passed — no forward concepts ("metric space", "convergence", "Cauchy sequence", or "compactness") are used anywhere on the page, including in exercise solutions.

## Corrections raised
None. The mathematics delivered by the lecturer is fully rigorous and free of defects.

## Transcription artefacts handled silently
- "A subset T contained in X is said to be dense, dense in X" — rendered as Definition 13.1.
- "open subset of an open subset is open" — rendered as Proposition 13.3.
- "Z tilde intersection Z" — rendered as $\widetilde{Z} \cap Z$.
- "f restricted to A and f restricted to B are continuous... then f is continuous" — rendered as Theorem 13.7 (The Pasting Lemma).
- "f1 of x,y is equal to the maximum of x,y... f2 is minimum" — rendered as Exercise 13.1.

## Open questions
None. All proofs were articulated completely without board gaps.

## Figures drawn
3 SVGs authored and placed directly in their corresponding units:
1. `dense-subset-intersection.svg` — Cue: *"So by the definition of subspace topology, this set V is equal to U intersection A closure for some open subset U contained in X... U is an open subset of X, and U contains x, and x is in A closure... So this implies that U intersection A... is equal to V. This is nonempty... which shows that A is dense in A closure."* (Placed in Proposition 13.2).
2. `pasting-lemma-closed-pieces.svg` — Cue: *"Let A and B be subsets of X such that, be closed subsets such that X is a union of A and B... f restricted to A and f restricted to B are continuous... So, to show f is continuous, enough to show that f inverse of a closed subspace is closed... f inverse of Y prime intersected with A is simply f restricted to A inverse image... So, this implies f is continuous."* (Placed in Theorem 13.7).
3. `max-min-quadrants.svg` — Cue: *"use this theorem to show that... f1 of x,y is equal to the maximum of x,y... and f2 of x,y is equal to minimum of x,y are continuous... write R2 as a union of two closed subspaces, and f1 and f2 both restricted to each of these subspaces should be continuous."* (Placed in Section on Maximum and Minimum).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 13 as `[PROCESSED]`; forward reference recorded to Lecture 14 (metric spaces, Euclidean metric, Cauchy–Schwarz, metric topology, convergence of sequences).
- **Glossary & Notation**: Added $\text{dense}$, $\max(x,y)$, $\min(x,y)$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Dense subset (`definition-13-1-dense-subset`) and Pasting lemma (`theorem-13-7-the-pasting-lemma`).
- **Reference Registry**: Cited Munkres §18 and Morris Chapters 3 & 4.

## Supplements
None.

## Verification rhythm retrofit
- **Obligation statements restored (6):**
  - Proposition 13.2: *"So let us prove this... by the definition of denseness, so we need to show that if V contained in A closure is a nonempty open subset, then V intersection A is nonempty"* [`build/tmp/lecture-13-formatted.txt:18-20`].
  - Proposition 13.3: *"So then we want to say that then V is open in X... open subset of an open subset is open in the larger topological space, right? So let's prove this. The proof is easy"* [`build/tmp/lecture-13-formatted.txt:38, 40-42`].
  - Lemma 13.4: *"The closed subsets of A, where A is given the subspace topology... are precisely of the form Z intersection A, where Z is closed in X. So let us prove this lemma"* [`build/tmp/lecture-13-formatted.txt:51-52`].
  - Corollary 13.5: *"And the proof of this corollary is very similar"* [`build/tmp/lecture-13-formatted.txt:67`].
  - Proposition 13.6: *"So let's prove this proposition first... If Z is closed... conversely, assume Z intersection Z i is closed in Z i for i equal to one comma two"* [`build/tmp/lecture-13-formatted.txt:78-79, 87`].
  - Theorem 13.7: *"So, proof... To show f is continuous, enough to show that f inverse of a closed subspace is closed... by the previous proposition, it is enough to show that f inverse of Y prime intersected A and f inverse of Y prime intersected B are closed"* [`build/tmp/lecture-13-formatted.txt:118, 120, 122`].
- **Closing declarations restored (6):**
  - Proposition 13.2: *"So thus, V intersection A is nonempty. Right? And which shows that A is dense in A closure"* [`build/tmp/lecture-13-formatted.txt:34-36`].
  - Proposition 13.3: *"this implies U intersection V tilde, this equal V is open in X. So this completes the proof"* [`build/tmp/lecture-13-formatted.txt:44-46`].
  - Lemma 13.4: *"So thus, are precisely of the form Z intersection A, where Z is a closed subset"* [`build/tmp/lecture-13-formatted.txt:60`].
  - Corollary 13.5: *"And as intersection of closed subsets is closed, this implies Z one is closed in X"* [`build/tmp/lecture-13-formatted.txt:70`].
  - Proposition 13.6: *"And finite unions of closed subspaces are closed. This implies Z is closed"* [`build/tmp/lecture-13-formatted.txt:96-97`].
  - Theorem 13.7: *"So, this implies that f inverse Y prime is closed in X. This implies f is continuous"* [`build/tmp/lecture-13-formatted.txt:130-131`].

