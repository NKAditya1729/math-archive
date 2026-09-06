# Lecture 18 — build report

## Coverage
Introduces the connectedness equivalence relation on any topological space, proving reflexivity via singletons, symmetry by definition, and transitivity via the Union Lemma. Defines connected components as the resulting equivalence classes and proves their three central properties: every connected subspace lies in a single component, each component is connected, and each component is closed in the ambient space. Computes the connected components of the rational numbers $\mathbb{Q}$, proving they are singletons, and establishes that a space is connected if and only if it consists of a single connected component.

## Fidelity checks
Units in skeleton: 5. Units in page: 5. Order preserved: yes.
Numbered objects preserved: Definition 18.1 (Connectedness Equivalence Relation), Proposition 18.2 ($\sim$ is an Equivalence Relation), Definition 18.3 (Connected Components), Proposition 18.4 (Properties of Connected Components), Example 1 (Connected Components of $\mathbb{Q}$), Proposition 18.5 (Criterion for Connectedness via Components).
Untraceable proof steps: 0. All steps of the equivalence verification, component properties, star-union argument, and rational component splitting were fully articulated in the spoken lecture.
Supplements: 0.
Vocabulary gate: passed — no forward concepts (path connectedness, path components, or compactness) appear.

## Corrections raised
1. **Proposition 18.4 (3) (`as X is connected, as Xi is connected`)**:
   - *Transcript:* "as $X$ is connected, as $X_i$ is connected, this implies..." (Sentence 142).
   - *Correction:* Only $X_i$ is assumed connected; the ambient space $X$ is an arbitrary topological space and is not assumed connected.
   - *Evidence:* Connected components exist precisely to analyze spaces that are not connected. The hypothesis that $X$ is connected is neither stated in the proposition nor needed in the proof. The lecturer misspoke the first clause and immediately corrected to "as $X_i$ is connected". This is a registered Slip in `context/known-defects.md`.

## Transcription artefacts handled silently
- "not the path components, the connected components" — rendered as connected components in Definition 18.3.
- "breaks X into a disjoint union of equivalence classes {X... we can write X as a disjoint union of Xis" — rendered as $X = \bigsqcup_{i \in I} X_i$.
- "each Xi closure is contained in a unique Xj... thus this Xj has to be Xi" — rendered as part (3) of Proposition 18.4.
- "choose a rational-- irrational C... C is not in Q, and Xi is in Q, therefore C is not in Xi" — rendered as Example 1.

## Open questions
None.

## Figures drawn
3 SVGs authored and verified:
1. `connected-components-partition.svg` — Cue: *"So this equivalence relation breaks X into a disjoint union of equivalence classes... every connected subspace of X is contained in Xi for some i... Given any connected subspace of X, it is gonna be contained in one of the Xis."* (Placed in Proposition 18.4).
2. `component-as-star-union.svg` — Cue: *"Then for any y in Xi... there is a connected subspace T sub y... such that x and y belong to T sub y... so thus we can write Xi as union over all these y in Xi, T sub y... and the intersection of all these T y's, it at least contains x... so this implies that Xi is connected."* (Placed in Proposition 18.4).
3. `rational-components-irrational-split.svg` — Cue: *"So if not, suppose B also belongs to Xi, and B is not equal to A... and we can choose an irrational C... so then Xi does not contain C... and so we can write Xi as a disjoint union of open subsets minus infinity comma C disjoint union C comma infinity... contradicts connectedness of Xi."* (Placed in Example 1).

## Glossary / course-map / registry additions
- **Course Map**: Marked Lecture 18 as `[PROCESSED]`; forward reference recorded to Lecture 19 (path connectedness, path components, matrix groups).
- **Glossary & Notation**: Added $x \sim y$, $X_i$, $X = \bigsqcup X_i$.
- **Concept Index (`site/_data/concepts.yml`)**: Added verified anchors for Connected component (`definition-18-3-connected-components`).
- **Reference Registry**: Cited Munkres §25 and Morris Chapter 3.

## Supplements
None.

## Verification rhythm retrofit
- **Obligation statements restored (5):**
  - Proposition 18.2 equivalence check opening: *"So let us check that this is an equivalence relations... So there are th-three things which we need to check"* [`build/tmp/lecture-18-formatted.txt:9-11`].
  - Proposition 18.2 transitivity recall: *"To s- to show this, recall that... in the previous lecture we had proved that if T1 and T2 are connected subsets of X such that T1 intersection T2 is non-empty, right, then the union, T1 union T2 is non-empty, is connected"* [`build/tmp/lecture-18-formatted.txt:22`].
  - Proposition 18.4 (1) contradiction setup: *"We'll prove the first point by contradiction. So let's assume that a connected subspace meets two Xis. So it meets Xi and Xj, where i is not equal to j"* [`build/tmp/lecture-18-formatted.txt:56-58`].
  - Proposition 18.4 (2) star union setup: *"Next, let us prove two... Then for any y in Xi... as x is equivalent to y, there is a connected subspace T sub y... such that x and y belong to T sub y... so thus, we can write X i as union over all these y in X i, T sub y"* [`build/tmp/lecture-18-formatted.txt:76-87`].
  - Example 1 rational component claim: *"We claim that the connected component containing A is, is just this set A. Why is that? So let's see this"* [`build/tmp/lecture-18-formatted.txt:172-174, 180-181`].
- **Method signposting & Case announcements restored (3):**
  - Proposition 18.2 3-axiom signpost: *"First, we need to check that x is equivalent to x... So the second point we need to check is if x is equivalent to y, then y is equivalent to x... Three, if x is equivalent to y and y is equivalent to z, then x is equivalent to z"* [`build/tmp/lecture-18-formatted.txt:12, 18, 21`].
  - Proposition 18.4 (3) closure recall: *"And finally, let's prove three... As X i is connected, this implies... So we had seen this corollary that A is connected in X, implies A closure is connected"* [`build/tmp/lecture-18-formatted.txt:141-144`].
  - Proposition 18.5 component criterion: *"This remark is obvious, right? Because if X is connected... there will be just one equivalence class... and conversely, if there's just one equivalence class, then that has to be X, and therefore X is going to be connected"* [`build/tmp/lecture-18-formatted.txt:208-211`].
- **Closing declarations restored (5):**
  - Proposition 18.2 closing: *"And thus, T1 union T2 is connected and contains x and z... So thus, x is equivalent to z. So this shows that this sim is an equivalence relation"* [`build/tmp/lecture-18-formatted.txt:26-29`].
  - Proposition 18.4 (1) closing: *"And this is a contradiction. Because Xi is not equal to Xj. So therefore, given any connected subspace, it can be contained only in one Xi. So this proves one"* [`build/tmp/lecture-18-formatted.txt:70-75`].
  - Proposition 18.4 (2) closing: *"Because all the T y's, they contain X, right? So this implies that X i is connected. So this proves two"* [`build/tmp/lecture-18-formatted.txt:138-140`].
  - Proposition 18.4 (3) closing: *"Thus, X i closure is contained in X i, which implies that X i is equal to X i closure. So this implies that X i is closed. This completes the proof of the proposition"* [`build/tmp/lecture-18-formatted.txt:148-152`].
  - Example 1 closing: *"This contradicts the connectedness of X i, right? So thus, X i is forced to be a singleton, right? So thus, X i is forced to be a single point... all the connected components are just A in Q"* [`build/tmp/lecture-18-formatted.txt:199-202`].

