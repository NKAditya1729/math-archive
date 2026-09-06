# Lecture 22 — build report

## Coverage
Proves that the complex general linear group $GL_n(\mathbb{C})$ is path connected via an affine line of matrices whose determinant polynomial has at most $n$ roots in $\mathbb{C}$, which can be continuously avoided in the complex plane. Establishes that the continuous image of any path-connected space is path connected, and that surjective continuous maps preserve path connectedness. Concludes Part III by showing that the special linear groups $SL_n(\mathbb{R})$ and $SL_n(\mathbb{C})$ are path connected as continuous images under column-scaling retractions from $GL_n(\mathbb{R})^+$ and $GL_n(\mathbb{C})$.

## Fidelity checks
Units in skeleton: 5. Units in page: 5. Order preserved: yes.
Numbered objects preserved: Proposition 22.1 (Path Connectedness of $GL_n(\mathbb{C})$), Lemma 22.2 (Continuous Images of Path-Connected Spaces), Corollary 22.3 (Surjections from Path-Connected Spaces), Theorem 22.4 (Path Connectedness of $SL_n(\mathbb{R})$), Theorem 22.5 (Path Connectedness of $SL_n(\mathbb{C})$).
Untraceable proof steps: 0. Every step in the root avoidance construction and the column-scaling retract is completely rigorous and fully detailed.
Supplements: 0.
Vocabulary gate: passed — no forward concepts from Part IV (compactness, Hausdorff) appear.

## Corrections raised
None. The mathematical arguments are complete and rigorous.

## Transcription artefacts handled silently
- Silent fix from `context/known-defects.md` (sentence 22): The transcript states *"gamma of zero we know is A, which is not equal to zero, because A is in GL n C"*. The matrix $A$ is not being compared to zero; its determinant is $p(0) = \det(A) \ne 0$. Corrected silently in the notes to $\det(A) \ne 0$.
- Spoken "GL n C" rendered as $GL_n(\mathbb{C})$.
- Spoken "M n C" rendered as $M_n(\mathbb{C})$.
- Spoken "SL n R" rendered as $SL_n(\mathbb{R})$.
- Spoken "SL n C" rendered as $SL_n(\mathbb{C})$.

## Open questions
None.

## Figures drawn
3 SVGs authored and verified:
1. `complex-polynomial-root-avoidance.svg` (Figure 22.1) — Cue: *"So if you make the complex plane, then here we have zero, and here we have one, and let's say the roots of p are lambda one up to some lambda r... We can take a path joining zero and one, which misses all these lambda i's"* [`build/tmp/lecture-22-formatted.txt:26-32`]. (Placed in Proposition 22.1).
2. `path-connected-continuous-image.svg` (Figure 22.2) — Cue: *"So we have our X over here, and here we have x one and x two, and here we have, let's say, f of X... f compose gamma from zero one to f of X is a continuous path"* [`build/tmp/lecture-22-formatted.txt:56-62`]. (Placed in Lemma 22.2).
3. `special-linear-retraction.svg` (Figure 22.3) — Cue: *"So we will simply take this map to SLnr... So if I take a matrix A, A gets mapped to... we just divide all the entries in the first column with determinant of A"* [`build/tmp/lecture-22-formatted.txt:72-76`]. (Placed in Theorem 22.4).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 22 as `[PROCESSED]`; forward reference recorded to Lecture 23 (Part IV, Hausdorff and compactness).
- **Concept Index (`site/_data/concepts.yml`)**: Added entries for $GL_n(\mathbb{C})$ (`proposition-22-1-gln-c-path-connected`), $SL_n(\mathbb{R})$ (`theorem-22-4-sln-r-path-connected`), and $SL_n(\mathbb{C})$ (`theorem-22-5-sln-c-path-connected`).
- **Reference Registry**: Appended L22 citations for Morris Chapter 5 and Munkres §24.

## Verification rhythm retrofit
- **Obligation statements preserved/restored (5):**
  - Proposition 22.1 target: *"So to show that GL n C is path connected, so given a matrix A in GL n C, we will find a path joining A to identity... in GL n C"* [`build/tmp/lecture-22-formatted.txt:5-6`].
  - Lemma 22.2 obligation: *"So now we want to show that f of X is path-connected"* [`build/tmp/lecture-22-formatted.txt:53`].
  - Theorem 22.4 obligation: *"So in order to show that SLnr is path connected, all that we have to do is we have to construct using the previous corollary a surjective map from a path connected space to SLnr"* [`build/tmp/lecture-22-formatted.txt:71`].
  - Well-defined target: *"So determinant of f of A is equal to... one upon determinant of A into determinant of A, which is one"* [`build/tmp/lecture-22-formatted.txt:80`].
  - Continuity target: *"So it only remains to show that f is continuous... enough to show that the coordinate functions are continuous"* [`build/tmp/lecture-22-formatted.txt:87-91`].
- **Method signposting & Case announcements preserved/restored (3):**
  - Non-zero polynomial check: *"And this polynomial is nonzero because as p of zero is equal to determinant... which is not equal to zero... p of t has at most n roots"* [`build/tmp/lecture-22-formatted.txt:20-25`].
  - Root avoidance method: *"We can simply take a path joining zero and one, which misses all these lambda i's in the complex plane"* [`build/tmp/lecture-22-formatted.txt:31-32`].
  - Coordinate continuity split: First column coordinates $A_{i1}/\det(A)$ vs other column coordinates $A_{ij}$ ($j > 1$) [`build/tmp/lecture-22-formatted.txt:95, 103`].
- **Closing declarations preserved/restored (4):**
  - Proposition 22.1 closing: *"So thus, every matrix A in GL and C can be joined to identity by a continuous path in GL and C. So thus, GL and C is path-connected"* [`build/tmp/lecture-22-formatted.txt:41-42`].
  - Lemma 22.2 closing: *"So this implies that f compose gamma from zero one to f of X is a continuous path joining f of x one and f of x two. So this implies that f of X is path-connected"* [`build/tmp/lecture-22-formatted.txt:62-63`].
  - Theorem 22.4 closing: *"And since GLnr plus is path connected and f is surjective and continuous, this implies SLnr is path connected"* [`build/tmp/lecture-22-formatted.txt:109`].
  - Theorem 22.5 closing: *"Again, we use the same map from GLnC to SLnC... SLnC is path connected"* [`build/tmp/lecture-22-formatted.txt:111-113`].