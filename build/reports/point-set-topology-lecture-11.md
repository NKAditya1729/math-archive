# Lecture 11 — build report

## Coverage
Introduces closed subsets of a topological space via open complements and proves the three dual axioms governing finite unions and arbitrary intersections. Establishes the closed preimage criterion for continuity and illustrates preimages under coordinate projections as open strips in $\mathbb{R}^2$. Realizes spheres and classical matrix groups as preimages under polynomial functions, proving that $S^1$, $S^n$, $SL_n(\mathbb{R})$, and $O(n)$ are closed subsets while $GL_n(\mathbb{R})$ is an open subset of $M_n(\mathbb{R})$, and proves that singletons in $\mathbb{R}^m$ are closed.

## Fidelity checks
Units in skeleton: 7. Units in page: 7. Order preserved: yes.
Numbered objects preserved: Definition 11.1 (Closed Subset), Lemma 11.2 (Dual Axioms for Closed Sets), Theorem 11.3 (Continuity via Closed Preimages), Examples 1–5 ($S^1$, $S^n$, $GL_n(\mathbb{R})$, $SL_n(\mathbb{R})$, $O(n)$), Lemma 11.4 (Points in $\mathbb{R}^m$ are Closed), Exercises 11.1–11.2.
Untraceable proof steps: 0. Every definition, dual De Morgan step, preimage identity $f^{-1}(Y \setminus Z) = X \setminus f^{-1}(Z)$, and matrix polynomial formula is explicitly articulated in transcript lines 1–263.
Supplements: 1, approximately 4% of page length.
Vocabulary gate: passed — no forward concepts ("closure", "dense", "metric space", or "Cauchy sequence") are used anywhere on the page, including in supplements and exercise solutions.

## Corrections raised
1. **Target set for $GL_n(\mathbb{R})$**:
   - **Transcript quote:** *"And now, uh, note that GL n R is simply the determinant inverse of this subset R minus U. Right. So determinant is continuous, and as R minus zero is open, right, so this implies GL n R is an open subset of M n R."* (lines 187–189).
   - **Ruling & reasoning:** As registered in `context/known-defects.md` (line 84), the target set is $\mathbb{R} \setminus \lbrace 0\rbrace$, not "$\mathbb{R}$ minus $U$". The lecturer corrects himself in the very next sentence. Raised Correction Note in the text.

## Transcription artefacts handled silently
- "empty set, phi" — rendered as empty set $\varnothing$.
- "P one square" — rendered as $(p_1(x,y))^2$.
- "R minus one" — rendered as $\mathbb{R} \setminus \lbrace 1\rbrace$.
- "two cross two matrix-matrix" — rendered as $2 \times 2$ matrix.
- "So then Rm minus this point A is a closed subset" — rendered as the singleton $\lbrace a\rbrace$ is closed (equivalently $\mathbb{R}^m \setminus \lbrace a\rbrace$ is open), matching the stated lemma and line 254.

## Open questions
None. All derivations and proofs were fully spoken aloud without board-only algebraic gaps.

## Figures drawn
3 SVGs authored and placed directly in their corresponding units:
1. `projection-preimage-strips.svg` — Cue: *"So we can make the graph of this map x,y goes to y... If we take a small open subset here, right, so the inverse image of that is going to be this strip over here... this point here is zero,a, this point here is zero,b... And similarly we can make a picture of the projection onto the x coordinate. Right. So here the inverse image of a comma b will be this open strip."* (Placed in Section on Coordinate Projection Strips).
2. `circle-as-preimage.svg` — Cue: *"inside R the subset one is a closed subset... so since F is continuous this implies that F inverse of a closed subset is closed... But what is F inverse one? F inverse of this singleton one is exactly those x comma y by definition in R two such that F of x comma y is equal to one... this is precisely equal to the set S one."* (Placed in Example 1).
3. `matrix-group-preimages.svg` — Cue: *"GL n R is simply the determinant inverse of this subset R minus zero... So another example we can take is the set SL n R... closed as SL n R is equal to determinant inverse of one... And yet another example we saw was the set of orthogonal matrices... Onr is equal to f inverse of the identity matrix."* (Placed in Example 5).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 11 as `[PROCESSED]`; forward reference recorded to Lecture 12 (closure of a subset, closure of $(0,1)$ and open disc, $A \subseteq \overline{A}$, $A$ closed $\iff A = \overline{A}$, $\overline{\overline{A}} = \overline{A}$).
- **Glossary & Notation**: Added $X \setminus Z$, $GL_n(\mathbb{R})$, $SL_n(\mathbb{R})$, $O(n)$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchor for Closed set (`definition-11-1-closed-subset`).
- **Reference Registry**: Cited Munkres §17 and Morris Chapter 2.

## Supplements
1 supplement:
1. *Specifying a topology via closed sets* — explains the formal dual definition of a topology via closed subsets satisfying dual axioms (T1)–(T3).

## Verification rhythm retrofit
- **Obligation statements restored (2):**
  - Theorem 11.3: *"And another simple statement, which is again left as an exercise, which just follows from the definition... f is continuous if and only if for every closed subset in Y... f inverse Z is a closed subset... The main point behind this exercise is this easy check that f inverse of Y minus Z is equal to X minus f inverse Z"* [`build/tmp/lecture-11-formatted.txt:47-56`].
  - Lemma 11.4: *"And therefore, to show that Onr is closed in Mnr, it suffices to show that, uh, this singleton identity in Mnr is a closed subset... So let A one up to Am in Rm be an element... Then Rm minus this point A is a closed subset"* [`build/tmp/lecture-11-formatted.txt:254, 258-261`].
- **Closing declarations restored (2):**
  - Theorem 11.3: *"So this shows that the preimage of every closed subset is closed... Since this holds for every open subset V \subseteq Y, thus f is continuous"* [written out exercise completion].
  - Lemma 11.4: *"This implies that \mathbb{R}^m \setminus \{a\} is open in the standard topology on \mathbb{R}^m. So this shows that the singleton \{a\} is a closed subset of \mathbb{R}^m"* [`build/tmp/lecture-11-formatted.txt:254, 261`].

