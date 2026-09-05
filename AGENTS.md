# Mathematical Lecture Archive — Agent Rules

You maintain a personal mathematics study website. Its purpose: the owner
watches recorded lectures, and this site holds reading notes that correspond to
those lectures **line by line**, so that revision without the video is possible.

The owner is a serious but self-taught beginner. He is not a mathematician by
training. He reads these notes alone, at night, after work. Every line you write
is read by someone with no one to ask.

## The single governing rule

> **The notes are a faithful written form of the lecture, not a summary of the
> topic.**

If the lecturer proved something in four steps, the notes have those four steps
in that order. If he chose an ugly example, the notes keep the ugly example. If
he numbered something "Example 5", it stays Example 5. Never reorder, never
compress, never substitute a slicker proof.

Anything you add that the lecturer did not say goes in a marked supplement
block. Never inline. See `@.agents/rules/02-transcript-fidelity.md`.

## The first course

**Point-Set Topology, 40 lectures, complete.** All transcripts are already in
`source/point-set-topology/transcripts/`; nothing more is coming. Lecture 40
ends the course. **Lecture 34 arrives as three files and is one lecture** —
concatenate before processing and produce one page.

The course runs in four parts (1–6, 7–15, 16–22, 23–40); `context/course-map.md`
has the full per-lecture breakdown. Real Analysis and Complex Analysis follow
later, so nothing you write may assume topology is the only course.

## What this repository is

```
source/                     ← raw input, never edited by you
  <course-slug>/
    transcripts/            ← MacWhisper .rtf, one per lecture (34 has three)
    references/             ← the owner's textbooks (read-only, never published)
context/                    ← long-form standing context; read on demand
site/                       ← the generated website (Jekyll, GitHub Pages)
  _courses/<course-slug>/   ← one markdown file per lecture
  assets/figures/           ← SVG figures you author
build/                      ← scripts and reports
```

## Standing rules, by topic

Read the file when the task touches its subject; not all four every time.

- `@.agents/rules/01-mathematical-standards.md` — rigour, notation, LaTeX, what
  "explained well" means here. **Every note-writing task.**
- `@.agents/rules/02-transcript-fidelity.md` — the correspondence protocol,
  correction handling, diagram cues. **Every note-writing task.**
- `@.agents/rules/03-site-architecture.md` — structure, design, build, deploy.
- `@.agents/rules/04-reference-library.md` — which book answers what; citation
  and copyright limits.
- `@.agents/rules/05-environment-and-limits.md` — what never to work around,
  what to do when a tool is missing. **Read this at the start of every
  session.**

Skills and workflows:

- `.agents/skills/lecture-notes/SKILL.md` — the authoring method.
- `.agents/skills/figure-authoring/SKILL.md` — drawing the board.
- `.agents/workflows/new-lecture.md` — the pipeline for one lecture.
  **Follow exactly.**
- `.agents/workflows/publish.md` — build, verify, deploy.

Reference material, all read before or during writing:

- `context/GOLD-STANDARD-lecture-01.md` — completed notes in the target format.
  **Read before your first notes in any session.** Format questions are settled
  by matching this file.
- `context/course-map.md` — where each lecture sits, and **which vocabulary is
  available**. A supplement may not use a term the course has not reached.
- `context/transcript-quirks.md` — how the transcription mangles mathematics.
  **Read before judging anything to be an error.**
- `context/known-defects.md` — the register of real errors across all 40
  lectures, already adjudicated. **Check your lecture here during the defect
  sweep.**
- `context/glossary-and-notation.md` — the running symbol and term registry,
  plus the named recurring arguments.
- `context/reference-registry.md` — the seven books and the concordance.

## Mathematical standard

Write as a careful lecturer preparing typed notes for a student who cannot ask
questions.

- **Nothing asserted without a reason.** "Clearly", "obviously", "easy to see"
  are forbidden unless the lecturer said them — and then you supply the reason
  in a supplement.
- **Every symbol defined at first appearance in a lecture**, even if defined
  three lectures ago.
- **Quantifier order never ambiguous.** "for every $x \in U$ there exists
  $\varepsilon > 0$ (depending on $x$)" — the parenthetical is not optional.
- **Every proof states what is proved and when it is finished**, closing with
  $\blacksquare$.
- **Where the lecturer gestured at a board, you draw the board.** "So this looks
  like the following" is a figure instruction, not filler.

You are held to research standard even though you write for a beginner. Where
the lecture contains a real error you neither repeat it nor silently fix it —
see the Correction Note protocol in rule 02 and the register in
`context/known-defects.md`.

## Hard prohibitions

1. **Never edit anything under `source/`.** Transcripts are evidence.
2. **Never publish textbook text or figures.** The seven books in
   `source/*/references/` are the owner's personal copies. Cite by section and
   theorem number only. Morris in particular carries an explicit
   no-reproduction notice.
3. **Never use a web image as a mathematical figure.** Author SVG yourself.
4. **Never invent a lecture number or date.** If the transcript does not state
   it, leave the field empty and say so in the report.
5. **Never rewrite a published lecture** to accommodate a new one. Add a
   correction; keep the history.
6. **Never mark a lecture `status: verified`.** Only the owner does that, after
   watching the video. You may set `status: drafted`.
7. **Never circumvent a technical protection** — no decrypting a document, no
   patching a crypto library, no stripping restrictions, for any reason. If a
   file will not open with ordinary tools, say so and stop. See rule 05.
8. **Never reconstruct a passage the board carried.** Three lectures (14, 21,
   37) have algebra that exists only on the board. Write the structure, then an
   Open Question block. A confident wrong derivation is far worse than an
   honest gap, because the reader cannot check it.

## Working style

**One lecture per run, completely, then stop.** Do not batch. One correct,
fully figured lecture is worth more than five thin drafts.

After every lecture, write `build/reports/<course>-lecture-<NN>.md` with: what
it covered in three sentences; every Correction Note and your reasoning; every
place you were unsure, quoted, with your best reading and your confidence;
every figure and the transcript phrase that prompted it; every glossary
addition. The owner reads this against the video. It is how errors get caught —
never bury an uncertainty in a footnote instead.

## When you are unsure

1. What the transcript literally says.
2. What the reference library says (`@.agents/rules/04-reference-library.md`).
3. What is mathematically true.

If (1) and (3) conflict, follow (3) and record a Correction Note. **When a
stated result and the proof beneath it disagree, the proof wins** — that single
heuristic resolves nearly every genuine defect in this course.

Note that Lectures 21, 22, 27, 28 and 34 have **no parallel treatment in the
library**. Absence there is not evidence the lecturer is wrong.

If you cannot reconstruct what he meant, say so in an explicit block. An honest
gap beats a confident invention. Never guess at a definition.
