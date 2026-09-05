# Workflow: Process One Lecture

Trigger: the owner says "process lecture N", or asks for the next unprocessed
lecture.

**Exactly one lecture per run.** If several are outstanding, do the
lowest-numbered, report, and stop. Ask before continuing.

---

## Step 0 — Orient

- `ls source/<course-slug>/transcripts/` and identify the target file **or
  files**. Lecture 34 is `Lecture_34_Part_1/2/3.rtf` — one lecture.
- Read `context/course-map.md`: what this lecture covers, what the previous one
  promised, and **which vocabulary is available**.
- Read `context/glossary-and-notation.md`.
- If this is your first notes task this session, read
  `context/GOLD-STANDARD-lecture-01.md`.
- Confirm the lecture number from the lecturer's own words, not the filename.

## Step 1 — Convert, and concatenate if multi-part

```bash
textutil -convert txt -stdout "source/<course>/transcripts/Lecture_34_Part_1.rtf" \
  "source/<course>/transcripts/Lecture_34_Part_2.rtf" \
  "source/<course>/transcripts/Lecture_34_Part_3.rtf" \
  > build/tmp/lecture-34.txt
```

(`textutil` is built into macOS; `pandoc -t plain` otherwise.) Never modify the
originals. `build/tmp/` is scratch and gitignored.

Check the converted text for **dropped brackets** — a dangling comma or orphan
`]` means an interval was eaten by the conversion. Note any you find.

## Step 2 — Skeleton pass

Pass 1 of `.agents/skills/lecture-notes/SKILL.md`. Produce the unit outline in
the lecturer's order and the unit count. This count is your fidelity checksum.
Write it into the report as the first section.

## Step 3 — Cue and defect sweep

Pass 2. Three lists: diagram cues with their trigger sentences; suspected
defects; undefined terms.

Then, in this order:

- Check every suspected defect against `context/transcript-quirks.md`. Most
  apparent errors are the transcription tool, and the four dangerous losses
  (case, $\mathbb{R}^{\mathbb{N}}$, matrix subscripts, phi) are catalogued
  there.
- Check `context/known-defects.md`. Every genuine error across all 40 lectures
  is already adjudicated there. Use the ruling; do not re-derive it.
- Anything left is new. Judge it by the ladder in
  `@.agents/rules/02-transcript-fidelity.md`, and **add it to the register**.

If this lecture is 14, 21 or 37, note now which passages are board-only. You
will write structure and an Open Question there, not reconstruction.

## Step 4 — Reconstruction

Pass 3. Write the lecture content from the transcript alone. No books, no web.

## Step 5 — Figures

Pass 4, using `.agents/skills/figure-authoring/SKILL.md`. Author each SVG at
the point where it was drawn. Commutative diagrams count.

## Step 6 — Verify the mathematics

Now open the reference library. For each definition and claim: does it agree
with the standard treatment? If not, is the difference deliberate or a defect?

Remember that L21, L22, L27, L28 and L34 have **no parallel treatment in the
library**. Silence there proves nothing.

Resolve every remaining suspicion into a Correction Note, an Open Question, or
a report line saying it turned out to be fine.

## Step 7 — Supplements and apparatus

Pass 5. Supplements (cap at roughly one-third of page length), exercises
collected, *Where we are*, recall sheet (`## At a glance` linking to each anchor,
in an `.at-a-glance-box`), *Further reading*, front matter with `coverage`
written last.

Front matter requirements:
- `timestamps: false` (timestamps are **owner-added only**; never invent one).
- `notation:` key list populated from `context/glossary-and-notation.md`.
- `depends_on:` list of prerequisites with short descriptions.
- `used_in:` list of subsequent lectures that depend on this one.
- **Back-populate dependencies:** When authoring Lecture N, open each prerequisite
  lecture and append Lecture N to its `used_in:` list in front matter.

Check every supplement against the vocabulary gate in `context/course-map.md`.
A supplement using a term the course has not reached is a defect.

## Step 8 — Update the standing context

Five files, every time:

- `context/glossary-and-notation.md` — new symbols and terms, with lecture.
- `site/_data/concepts.yml` — add any newly defined concepts, named results, or notation entries with their lecture number and anchor; `site/concepts.md` renders from this file automatically.
- `context/course-map.md` — mark processed; record any forward reference.
- `context/reference-registry.md` — sections newly cited.
- `context/known-defects.md` — any new defect, with the same three fields.

Skipping this is how Lecture 30 ends up inconsistent with Lecture 3.

## Step 9 — Build and check

```bash
bundle exec jekyll build
```

Then the checks in `.agents/workflows/publish.md`. At minimum: KaTeX renders
with no errors; every figure exists; `prev`/`next` resolve both ways; the
previous lecture's `next` now points here; the course index lists it under the
right part.

## Step 10 — Report

Write `build/reports/<course>-lecture-<NN>.md`:

```markdown
# Lecture NN — build report

## Coverage
Three sentences.

## Fidelity checks
Units in outline: 9.  Units in page: 9.  Order preserved: yes.
Numbered objects preserved: Example 6, property (∗), steps 1–3.
Untraceable sentences found and removed: 2 (listed below).
Vocabulary gate: passed — no supplement used an unavailable term.

## Corrections raised
1. [from known-defects, or new] As transcribed … / What is meant … / Why …
   Consequence: none — the topology is unaffected. Video check suggested.

## Open questions
1. Transcript at "…" — board-only computation. Structure written; algebra
   marked as needing the video.

## Figures drawn
1. `open-square-s-epsilon.svg` — cue: "in terms of a diagram, so this looks
   like the following."

## Glossary / course-map / registry / defect-register additions
…

## Supplements
4, ~28% of page length.
```

Then **stop**. Tell the owner the page is drafted and summarise the corrections
and open questions in two or three sentences. Do not set `status: verified`.

---

## If a transcript is unusable

If reconstruction would be guesswork across a whole argument — not the known
board-only passages, but genuine audio loss — do not produce a page. Write the
report with the problem sections quoted and ask for a video check. A page full
of confident invention is worse than no page.
