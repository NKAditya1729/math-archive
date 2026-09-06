# Lecture 07 — build report

## Coverage
Defines continuous maps between topological spaces via preimages of open sets. Proves that identity maps and inclusions of subspaces are continuous, and shows that the subspace topology is the coarsest topology making the inclusion continuous. Establishes that coordinate projections from product spaces are continuous, and proves that the product topology is the coarsest topology making all projections continuous. Concludes by proving that the diagonal map fails to be continuous under the box topology, explaining why the box topology is rejected.

## Fidelity checks
Units in skeleton: 8.  Units in page: 8.  Order preserved: yes.
Numbered objects preserved: Definition 7.1 (Continuous Map), Example 1 (Identity map), Proposition 7.2 (Continuity of subspace inclusions), Proposition 7.3 (Subspace is coarsest), Proposition 7.4 (Continuity of projections), Proposition 7.5 (Product is coarsest), Proposition 7.6 (Discontinuity of diagonal map in box topology), Lemma 7.7 preview (Basis criterion for continuity), Exercises 7.1–7.4.
Untraceable sentences found and removed: 0.
Supplements: 1, approximately 10% of page length.
Vocabulary gate: passed — no forward concepts (such as "homeomorphism", "closed set", "compactness", or "metric space") are used anywhere on the page, including in supplements and exercise solutions.

## Corrections raised
None. The mathematics of this lecture is correct as delivered.

## Transcription artefacts handled silently
- "f inverse U, V" — rendered as $f^{-1}(V)$.
- "p j" — rendered as projection $p_j$.
- "delta" — rendered as diagonal map $\Delta$.
- "minus one upon n, comma, one upon n" — rendered as $(-1/n, 1/n)$.
- "singleton zero" — rendered as $\lbrace 0 \rbrace$.

## Open questions
None. The arguments and proofs are completely clear and self-contained.

## Figures drawn
3 SVGs authored and placed directly in their corresponding units:
1. `continuity-preimage.svg` — Cue: *"So we say that $f$ is continuous if for every open subset $V$ in $Y$... the set $f^{-1}(V)$ contained in $X$ is open in $X$."* (Placed in Definition 7.1).
2. `projection-cylinder.svg` — Cue: *"So what is $p_j^{-1}(U)$? It is actually equal to a product $U_i$ where $U_j = U$ and $U_i = X_i$ for $i \ne j$."* (Placed in Proposition 7.4).
3. `diagonal-box-failure.svg` — Cue: *"consider the set $U_n = (-1/n, 1/n)$... delta inverse of this set is just equal to singleton zero, which is not open in $X$."* (Placed in Proposition 7.6).

## Glossary / course-map / registry / defect-register additions
- **Glossary & Notation**: Verified entries for continuous map, projection $p_j$, diagonal map $\Delta$, and coarsest topologies.
- **Course Map**: Marked Lecture 7 as `[PROCESSED]`; forward reference recorded to Lecture 8 (basis criterion for continuity and continuous operations on $\mathbb{R}$).
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Continuous map and Projection map.
- **Reference Registry**: Cited Munkres §18 and Morris Chapter 4.

## Supplements
1 supplement, approximately 10% of page length:
1. *Why preimages rather than forward images?* — explains why continuity is defined via preimages rather than forward open images, giving counterexamples of constant functions and $x \mapsto x^2$.

## Verification rhythm retrofit
- **Obligation statements restored (4):**
  - Proposition 7.2: *"What do we have to do to prove that i is continuous? ... What is i inverse U? ... But i is simply the inclusion"* [`build/tmp/lecture-07-formatted.txt:51-53`].
  - Proposition 7.3: *"We are given that tau is a topology on Y such that the inclusion map is continuous, and we need to show that tau sub Y is contained in tau"* [`build/tmp/lecture-07-formatted.txt:72`].
  - Proposition 7.4: *"What do we have to do to prove continuity? We have to take an open subset in X_j and show that the inverse image of that open subset is open in the product topology"* [`build/tmp/lecture-07-formatted.txt:116-117`].
  - Proposition 7.5: *"Our aim is to show that... we need to show that the product topology is contained in our topology tau... it suffices to show that this basis B for the product topology is contained in tau"* [`build/tmp/lecture-07-formatted.txt:175-177`].
- **Closing declarations restored (4):**
  - Proposition 7.2: *"So this shows that i is continuous. This inclusion map is continuous"* [`build/tmp/lecture-07-formatted.txt:55-56`].
  - Proposition 7.3: *"So thus we have proved that tau sub Y is contained in tau... the subspace topology on a subset Y is the smallest topology which makes the inclusion map continuous"* [`build/tmp/lecture-07-formatted.txt:94-96`].
  - Proposition 7.4: *"Therefore, this implies that thus the projection maps are continuous"* [`build/tmp/lecture-07-formatted.txt:148`].
  - Proposition 7.5: *"So this implies that B is contained in tau. This implies that tau product is contained in tau. So therefore, in view of the above, we see that this product topology is the smallest topology... for which all the projection maps are continuous"* [`build/tmp/lecture-07-formatted.txt:188-191`].
