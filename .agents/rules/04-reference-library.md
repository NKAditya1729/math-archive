# Rule: The Reference Library

Applies whenever you check a definition, look for a counterexample, choose a
supplement, or write further reading.

Seven books in `source/point-set-topology/references/`, all identified. They
are **read-only inputs to your reasoning** and never inputs to the published
site. Full details and the lecture-by-lecture concordance are in
`context/reference-registry.md`.

## Copyright — non-negotiable

- **Never** copy a paragraph, a definition verbatim, a proof, or an image into
  `site/`.
- **Never** commit the files. They are `.gitignore`d and Jekyll-`exclude`d.
- Cite by location only: "Munkres, *Topology* (2nd ed.), §13, Lemma 13.1".
- Restate any idea you use in your own words and the lecturer's notation.
- Short quotation — under fifteen words, quoted, cited — at most once per page,
  and only where the exact phrasing is the point.

Morris carries an explicit no-reproduction notice on its title page. The rule
is the same for all seven. The site is public; treat it as a publication.

## The seven, and what each is for

**Munkres, *Topology*, 2nd ed. (554 pp) — the spine.** Default authority for
definitions and statements, and the book to point the reader toward, since he
will meet it again everywhere. Covers roughly 34 of the 40 lectures; the
course's sequence tracks it closely through §12–§35.

**Morris, *Topology Without Tears* (729 pp) — the second voice.** Free and
actively maintained, generous with worked examples, good where Munkres is
terse. **The only source in the library for topological groups** (Appendix 5)
and the natural companion for the quotient material (Ch. 11) and the countable
product (Ch. 9). Note his "finite-closed topology" is the lecturer's
finite-complement topology.

**Kumaresan, *Topology of Metric Spaces* (166 pp).** Closest to this lecturer's
idiom and notation. Reach for it when you need a second worked example in the
same style, or when a step seems to assume a metric fact the lecture never
proved. Most valuable across L14–L15 and L28–L29.

**Simmons, *Introduction to Topology and Modern Analysis* (384 pp).**
Analysis-flavoured motivation — best on "why define it this way". Strong in the
back half: compactness, normality, Urysohn.

**Mendelson, *Introduction to Topology*, 3rd ed.** The gentlest. Use it to
calibrate a supplement's level: if Mendelson spends a page on something, the
owner needs that page. Also the source for the elementary set theory the
lectures use silently — De Morgan for arbitrary families, used twice in L1 and
never stated.

**Starbird & Su, *Topology Through Inquiry* (330 pp).** Mostly questions. Your
exercise mine for Parts I–III. Restate in your own words and the lecturer's
notation; never copy its numbering. Falls away after roughly L20.

**Chinn & Steenrod, *First Concepts of Topology* (168 pp).** Geometric and
intuitive, with pictures. Use it to decide *what a figure should show*. Not a
source for point-set definitions. Falls away after Part I.

## Where the library runs out

**Lectures 21, 22, 27, 28 and 34** — path connectedness of
$GL_n(\mathbb{R})^+$ and $GL_n(\mathbb{C})$, connectedness of $SO(n)$ and
$U(n)$, and the Grassmannian — are **not in Munkres, Simmons, Mendelson,
Kumaresan, Chinn–Steenrod, or Starbird–Su**. Morris's Appendix 5 is the only
coverage, and it is partial.

On these lectures, "check it against Munkres" comes back empty. **Absence is
not evidence the lecturer is wrong.** Do not raise a Correction Note because a
result cannot be found. Verify the mathematics on its own terms and say in the
report that the library has no parallel treatment.

## How to use them while writing

1. **Write the lecture content from the transcript alone.** No books open.
   Books pull your phrasing toward theirs and away from his.
2. **Then check.** Does the mathematics hold up? A disagreement with Munkres is
   a signal to re-read the transcript, not to rewrite the lecture — and where
   the lecturer differs deliberately (compactness with Hausdorff built in), the
   difference is content, not error.
3. **Then write supplements**, using the routing above to pick the level.
4. **Then further reading**: two to four precise pointers, each with a line
   saying what the reader will find.

A good entry:

> **Munkres §13.** The same basis idea developed in the opposite direction: he
> starts from a collection $\mathcal{B}$ satisfying two conditions and *builds*
> a topology. That is exactly what this lecturer does next lecture.

A bad one: "See Munkres for more on bases."

## Using the internet

Permitted for checking a standard name, finding a standard counterexample,
confirming an attribution, or resolving an ambiguity across sources.

Not permitted for pulling images to use as figures, copying explanatory prose,
citing anything you have not read, or relying on a forum answer when seven
textbooks are on disk. Cite any web source in the build report.

## Maintaining the registry

Keep `context/reference-registry.md` current: add each section you cite to the
concordance and one line per published citation to the log. Over time this
becomes a concordance between the course and the library — the thing that lets
the owner pick up a book and find his place.
