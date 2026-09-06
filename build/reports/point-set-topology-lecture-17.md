# Lecture 17 — build report

> [!WARNING]
> **Consequential defect handled:** Lemma 17.4 (The Union Lemma) transcript states that "the union $T_1 \cup T_2$ is non-empty." This is corrected to **connected**. The entire proof delivered in the lecture establishes connectedness, and the lecturer recalls it correctly in Lecture 18. A Correction Note is raised.

## Coverage
Proves that the Cartesian product of two connected spaces is connected via the slice argument, establishing by induction that all Euclidean spaces $\mathbb{R}^n$ are connected. Demonstrates that no continuous surjection exists from $[0, 1]$ to $[0, 1] \sqcup [3, 4]$, proving they are not homeomorphic and establishing connectedness as a topological invariant. Proves the Union Lemma (the union of intersecting connected subspaces is connected), correcting a consequential verbal slip, and applies it to prove that all unit spheres $S^n$ ($n \ge 1$) are connected via overlapping stereographic charts.

## Fidelity checks
Units in skeleton: 5. Units in page: 5. Order preserved: yes.
Numbered objects preserved: Theorem 17.1 (Connectedness of Product Spaces), Corollary 17.2 (Connectedness of $\mathbb{R}^n$), Example 1 (Connectedness as a Topological Invariant), Proposition 17.3 (Topological Invariance of Connectedness), Lemma 17.4 (The Union Lemma), Corollary 17.5 (Connectedness of Spheres $S^n$).
Untraceable proof steps: 0. Every step in the product space slice argument, the union lemma proof, and the two-chart stereographic decomposition was fully spoken.
Supplements: 0.
Vocabulary gate: passed — no forward concepts (connected components, path connectedness, or compactness) appear.

## Corrections raised
1. **Lemma 17.4 (`the union T1 union T2 is non-empty`)**:
   - *Transcript:* "Then the union $T_1$ union $T_2$ is non-empty." (Sentence 113).
   - *Correction:* Should be "Then the union $T_1 \cup T_2$ is **connected**."
   - *Evidence:* The hypothesis $T_1 \cap T_2 \ne \varnothing$ already implies non-emptiness trivially. The proof that follows immediately shows that $T_1 \cup T_2$ cannot be partitioned into two disjoint non-empty open sets. The lecturer recalls this lemma in Lecture 18 explicitly as stating that $T_1 \cup T_2$ is connected. This is a registered Consequential defect in `context/known-defects.md`.

## Transcription artefacts handled silently
- "fix X nought in X... map from Y to X cross Y given by Y maps to X nought comma Y... projection to first factor is constant... projection to second factor is identity" — rendered as Step 1 of Theorem 17.1.
- "X nought comma Y nought is in A... entire line X nought cross Y is completely contained inside A... X cross Y is completely contained inside A... B is empty" — rendered as Step 2 of Theorem 17.1.
- "phi from S n minus... north pole... to R n is a bijective continuous map with continuous inverse" — rendered as stereographic projection in Corollary 17.5.

## Open questions
None.

## Figures drawn
3 SVGs authored and verified:
1. `product-connectedness-grid.svg` — Cue: *"So suppose a point X nought comma Y nought is here, right? So then if we fix X nought, so this is the line... X nought cross Y... this entire line is completely contained inside A... now we can take any point, let's say Y over here... and look at the line X cross Y... this implies that X cross Y which is equal to the union of X cross small y is completely contained inside A."* (Placed in Theorem 17.1).
2. `union-connected-subspaces.svg` — Cue: *"So let's say our T1 is like this and T2 is like this... So let's take a point in the intersection... let A be a point in the intersection... assume that A is in Y intersection U... as A is in T1 and A is in U, this implies that T1 is completely contained inside U... similarly T2 is contained in U... so Y is contained in U."* (Placed in Lemma 17.4).
3. `sphere-stereographic-connectedness.svg` — Cue: *"So we are taking the sphere, we remove this north pole, one point, and then we project to this plane... Now similar to projecting, removing the north pole, we can instead of the north pole, we can remove the south pole and project once again... and these intersect... previous lemma implies that S n is connected."* (Placed in Corollary 17.5).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 17 as `[PROCESSED]`; forward reference recorded to Lecture 18 (connected components, equivalence classes, components of $\mathbb{Q}$, path connectedness).
- **Glossary & Notation**: Added $X \times Y$, $T_1 \cup T_2$, $S^n$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Product space connectedness (`theorem-17-1-connectedness-of-product-spaces`) and Union lemma (`lemma-17-4-the-union-lemma`).
- **Reference Registry**: Cited Munkres §23 and §24, Morris Chapter 3.

## Supplements
None.

## Verification rhythm retrofit
- **Obligation statements restored (5):**
  - Theorem 17.1 proof setup: *"So let us prove this. So let us assume that X cross Y is not connected. So then there are open subsets, non-empty open subsets A and B such that this product is the disjoint union of A and B"* [`build/tmp/lecture-17-formatted.txt:5-8`].
  - Theorem 17.1 Step 1 slice continuity: *"To check that this map is continuous, we just need to check that both the factors, the projections to both factors are continuous"* [`build/tmp/lecture-17-formatted.txt:19`].
  - Theorem 17.1 Step 2 chaining: *"Now we can get a contradiction as follows: since A is non-empty, let X nought comma Y nought be a point in A"* [`build/tmp/lecture-17-formatted.txt:41, 43`].
  - Lemma 17.4 proof setup: *"So let's prove this. So let us assume, if possible, so if possible, let T1 union T2 be, uh, not be connected... be disconnected... So since we are assuming that Y is disconnected, so we can write, we can write Y is equal to... Y intersection U... disjoint union Y intersection V"* [`build/tmp/lecture-17-formatted.txt:116-125`].
  - Corollary 17.5 stereographic setup: *"So to show this, recall that... we can show that this map phi from S n minus north pole to R n is a bijective continuous map with continuous inverse"* [`build/tmp/lecture-17-formatted.txt:152-159`].
- **Method signposting & Case announcements restored (3):**
  - Theorem 17.1 previous result recall: *"In the previous lecture, we saw that the image of a connected topological space under a continuous map is again connected... So let us use this result"* [`build/tmp/lecture-17-formatted.txt:10-13`].
  - Lemma 17.4 point selection in intersection: *"So let's take a point in the intersection: so let A be a point in the intersection, which exists because we are assuming that the intersection is non-empty... assume that A is in Y intersection U"* [`build/tmp/lecture-17-formatted.txt:130-135`].
  - Proposition 17.3 opening: *"This is easy because if X and Y are homeomorphic, that means there is a bijective continuous map from X to Y... so therefore the image of f is all of Y"* [`build/tmp/lecture-17-formatted.txt:97-98`].
- **Closing declarations restored (5):**
  - Theorem 17.1 Step 1 closing: *"Thus X nought cross Y with the subspace topology, since Y is connected, is connected"* [`build/tmp/lecture-17-formatted.txt:25`].
  - Theorem 17.1 overall closing: *"But this shows that B is empty, which is a contradiction. So thus, X cross Y is connected"* [`build/tmp/lecture-17-formatted.txt:65-67`].
  - Proposition 17.3 closing: *"And since X is connected, so that means Y is connected... and conversely... this will mean that X is connected"* [`build/tmp/lecture-17-formatted.txt:99, 104`].
  - Lemma 17.4 closing: *"So this implies that this Y intersection V has to be empty... this is forced to be empty, which is a contradiction. Therefore, T1 union T2 is connected [corrected from transcript slip: non-empty]"* [`build/tmp/lecture-17-formatted.txt:146-148`].
  - Corollary 17.5 closing: *"As both these intersect... and these are connected, the previous lemma implies that S n is connected"* [`build/tmp/lecture-17-formatted.txt:187-188`].

