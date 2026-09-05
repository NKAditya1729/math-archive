# Rule: Mathematical Standards

Applies to every task that produces mathematical prose.

## The reader

One person. He is intelligent, motivated, and works through material slowly
and repeatedly. He has no formal training past school mathematics. He has no
one to ask when a step does not follow.

Two failure modes ruin the notes for him, and they pull in opposite
directions:

- **Too terse.** A step is asserted; he cannot reconstruct it; he stops.
- **Too chatty.** The mathematics is buried in encouragement and analogy; he
  reads three pages and has learned one definition.

Aim between them: *complete reasoning, stated plainly, with nothing skipped
and nothing padded.* The model is a well-written graduate textbook that has
had all of its "clearly"s expanded.

## Rigour rules

**R1. No unjustified assertion.** Every "therefore" must be earned by
something already on the page. If a step uses a fact from an earlier lecture,
name it and link it: "by the second topology axiom (Lecture 1, Definition 1.2)".

**R2. Banned phrases.** *clearly, obviously, trivially, it is easy to see,
one can show, it follows immediately, evidently.* If the lecturer used one,
you may keep his sentence, but you then supply the missing reason in a
supplement block.

**R3. Quantifiers are explicit and ordered.** Point-set topology is almost
entirely a subject about quantifier order. Never write "there is $\varepsilon$
such that..." without saying what it may depend on. The house form is:

> for every $x \in U$ there exists $\varepsilon > 0$, *possibly depending on
> $x$*, such that $(x-\varepsilon, x+\varepsilon) \subseteq U$.

The dependence parenthetical is mandatory the first three times a
quantifier pattern appears in a course, and any time the lecturer stresses it.

**R4. Finite versus arbitrary is always flagged.** When a statement holds for
finite collections but fails for infinite ones (intersections of open sets,
for instance), that restriction is stated in bold in the definition and given
a counterexample in a supplement the first time it appears.

**R5. Proofs are framed.** Every proof opens by restating what is to be
proved, and closes with `$\blacksquare$`. Long proofs are broken into named
steps that mirror the lecturer's own steps.

**R6. Both directions.** For any "if and only if", or any claim that two
definitions give the same object, both inclusions are shown separately with
headings. Never "similarly" across a direction the lecturer actually did.
"Similarly" is acceptable only where the lecturer himself said it, and then
the omitted argument is spelled out in a supplement.

**R7. Counterexamples are first-class.** The lecturer's non-examples (the
half-open interval that fails the property, the closed disc that fails it) do
more teaching than the examples. Give them equal space, equal figures, and
say precisely *which* point breaks the property and *why no* $\varepsilon$
works for it.

**R8. Names.** Attach standard names to what is being done even when the
lecturer did not: "this is the standard (Euclidean) topology", "this
collection is a basis in the sense of Definition 3.4". Put the name in the
glossary. This is what lets him read a textbook later and recognise the thing.

## Notation conventions

House style, applied consistently across all courses. When the lecturer's
notation differs, **use the lecturer's** and note the standard alternative
once in a supplement.

| Object | Write | Not |
|---|---|---|
| Empty set | `\varnothing` | `\phi`, `\emptyset` |
| Real line, plane, $n$-space | `\mathbb{R}`, `\mathbb{R}^2`, `\mathbb{R}^n` | `R`, `R2` |
| Power set | `\mathcal{P}(X)` | `P(X)` |
| A topology | `\tau` | `T` |
| Subset (not nec. proper) | `\subseteq` | `\subset` |
| Set braces | `\lbrace \dots \rbrace` | `\{ \dots \}` (kramdown strips `\{`/`\}`) |
| Set-builder | `\lbrace\, x \in X : P(x) \,\rbrace` | `\{x \| P(x)\}` |
| Norm | `\lVert x \rVert`, `\lVert f \rVert_\infty` | `\|x\|`, `\|f\|_\infty` (kramdown strips `\|` to `|`) |
| Modulus / absolute value | `|x|`, `\lvert x \rvert` | |
| Indexed union | `\bigcup_{i \in I} U_i` | `U U_i` |
| Finite intersection | `\bigcap_{i=1}^{n} U_i` | |
| Open interval | `(a,b)` | `]a,b[` |
| End of proof | `\blacksquare` | `QED` |

Note on `\varnothing`: the lecturer says "phi" out loud and the transcript
writes "phi". This is the standard Indian convention for reading $\varnothing$.
It is the empty set, **never** the letter $\phi$. Render it `\varnothing`
throughout and state this once, in Lecture 1, in a Reading Note.

Displayed equations for anything longer than a short clause. Inline math for
single symbols. Never break a formula across a line break in the source.

## LaTeX and rendering

KaTeX renders the site. It is fast and covers everything point-set topology
needs, but it is **not** full LaTeX.

- **Set braces must be `\lbrace` and `\rbrace`.** Kramdown parses markdown before
  KaTeX processes math. It treats `\{` and `\}` as escaped characters and emits
  bare `{` and `}`, which KaTeX then reads as invisible grouping characters —
  stripping every set brace from the rendered page. Always write `\lbrace` and
  `\rbrace` for literal set braces (e.g. `\lbrace a, b, c\rbrace`,
  `\lbrace\varnothing, X\rbrace`).
- **Norms must be `\lVert` and `\rVert`.** Writing `\|f\|` in inline math is stripped
  by Kramdown to bare `|f|`, turning a double-bar norm into a single-bar absolute value.
  Always write `\lVert` and `\rVert` (e.g. `\lVert f \rVert_\infty`, `\lVert x \rVert_2`).
- **Multi-line alignments (`aligned`) must be in display math `$$...$$` with `\\`.**
  Kramdown preserves `\\` inside display math blocks `$$...$$`, but collapses `\\` to
  `\` inside single-dollar inline math `$...$`. Always set multi-line alignments as
  displayed equations inside `$$...$$` and use `\\` for line breaks.
- Supported and used freely: `\mathbb`, `\mathcal`, `\subseteq`, `\varnothing`,
  `\bigcup`, `\bigcap`, `\varepsilon`, `\blacksquare`, `aligned`, `cases`,
  `\overline`, `\operatorname`, `\lbrace`, `\rbrace`, `\lVert`, `\rVert`,
  `\lvert`, `\rvert`.
- **Not supported.** No `\begin{tikzpicture}`, no `\newcommand` in page
  source, no `\label`/`\ref` cross-referencing, no `align` (use `aligned`
  inside `$$`), no `\text` with nested math beyond one level.
- Cross-references are ordinary markdown links to anchors, written by hand.
- Macros, if genuinely needed, are declared once in the KaTeX config in
  `site/_includes/katex.html`, never inline.

Every page you generate must be checked: run the KaTeX check in
`.agents/workflows/publish.md` before deploying. An unrendered `$$` block is
worse than no notes.

## Structure of a set of lecture notes

Fixed skeleton. Do not improvise a new one per lecture.

1. **Front matter** — course, lecture number, date if known, one-paragraph
   *Coverage* statement listing what the lecture actually covered, `status`,
   `version`.
2. **Where we are** — two or three sentences connecting to the previous
   lecture, in the arc of the course. Drawn from `context/course-map.md`.
3. **The notes proper** — following the lecture's own order exactly.
   Definitions, Examples, Claims, Proofs, each numbered as the lecturer
   numbered them (`Example 5` stays `Example 5`), each with the lecturer's
   own wording preserved in substance.
4. **Exercises left by the lecturer** — verbatim in substance, collected in
   one place at the end as well as appearing in flow. Never solved in the
   main body. Solutions, if you write them, go behind a collapsed
   `<details>` block labelled *Worked solution (not from the lecture)*.
5. **Supplements** — everything you added. Clearly bounded. See rule 02.
6. **Further reading** — cross-references into the reference library, by
   section number.

## Supplements: what to add, and how much

You are asked to supplement, and you should. But supplements are seasoning.
A good ratio is **no more than one-third** of the page by length.

Add a supplement when, and only when:

- a step of the lecturer's argument would not follow for this reader without
  one more sentence;
- a term is used that the lecture never defined;
- the lecturer said "similarly" or "exercise" over something load-bearing;
- a second example would make a definition concrete (give the *simplest*
  possible one, not the cleverest);
- a picture is needed that the lecturer drew but the transcript lost.

Do **not** add:

- material from later in the subject the lecturer has not reached;
- alternative proofs that are shorter but use unavailable machinery;
- historical anecdotes, motivational framing, or "why this matters" essays;
- anything you cannot state with certainty.

A supplement that introduces a concept the course has not reached is a defect,
not a bonus. Check `context/course-map.md` for what has been covered before
you reach forward.
