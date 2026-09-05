---
name: lecture-notes
description: Converts a raw lecture transcript in mathematics into publishable reading notes that correspond one-to-one with the lecture. Use whenever a transcript file is being turned into a page, when existing notes are being revised or corrected, or when checking whether a set of notes faithfully matches its lecture. Covers the reconstruction pass, block structure, numbering, exercise handling, supplements, and the build report.
---

# Authoring Lecture Notes

Read `AGENTS.md`, `.agents/rules/01-mathematical-standards.md`, and
`.agents/rules/02-transcript-fidelity.md` before using this skill. Read
`context/GOLD-STANDARD-lecture-01.md` if you have not seen it this session —
it is the format target and it is worth more than any description of the
format.

## The five passes

Do not write the page in one go. Five separate passes over the transcript,
each with a single job. Passes 1 and 2 produce no prose at all.

### Pass 0 — Assemble

Confirm you have the whole lecture. Lecture 34 is three files and must be
concatenated in part order before anything else; treating a part as a lecture
produces three broken pages. Confirm the lecture number from the lecturer's own
words, not the filename.

### Pass 1 — Skeleton

Read the whole transcript once without writing mathematics. Produce a bare
outline, in the lecturer's order, of every unit he presents:

```
- recall: power set
- Definition: topology (3 conditions)
- Example 1: trivial topology  [3 conditions verified]
- Example 2: discrete topology [3 conditions verified]
- Example 3: finite complement topology [3 conditions verified]
- closing: forward reference to "specific examples" next lecture
```

Count the units. This count is your fidelity checksum: the finished page must
contain exactly these units, in this order, none merged, none dropped.

### Pass 2 — Cue and defect sweep

Second read, marking three things and still writing no prose:

- **Diagram cues.** Every phrase from the table in rule 02. Note the exact
  transcript sentence and what you think was on the board.
- **Suspected defects.** Anything mathematically off. Do not resolve yet.
- **Undefined terms.** Every symbol or word used without definition in this
  lecture — check `context/glossary-and-notation.md` to see whether an earlier
  lecture defined it. Those that no lecture has defined are supplement
  candidates.

### Pass 3 — Reconstruction

Now write the lecture content, unit by unit, from the transcript alone.
No books open, no web. You are transcribing a person's argument into
mathematics, not writing about the topic.

Working method for each unit:

1. Read the transcript for that unit twice.
2. Write the mathematical statement in display form.
3. Write the argument, in his steps, in his order, filling only the grammar —
   never the reasoning.
4. Re-read the transcript against what you wrote. Anything in your version
   that is not traceable to a sentence of his is either deleted or moved to a
   supplement. There is no third option.

That last check is the whole discipline. Apply it to every unit.

### Pass 4 — Figures

Author every figure marked in pass 2, at the point in the notes where the
lecturer drew it. Use `.agents/skills/figure-authoring/SKILL.md`.

Do not write figures earlier — a figure drawn before the surrounding prose
exists tends to illustrate the topic rather than the moment.

### Pass 5 — Supplements, apparatus, report

In order: resolve the pass-2 defects into Correction Notes or Open Questions;
write supplements; collect exercises; write *Where we are*; write the `## At a glance`
recall sheet section as the last section right before *Further reading* (every definition,
claim, and example on the page, statement only, no proofs, linking to its anchor above,
enclosed in an `.at-a-glance-box`); write *Further reading*; write the front matter
(with `timestamps: false`, `notation:` list, `depends_on:`, `used_in:`, and `coverage`
written last so it reflects the finished page); write the build report.

### Video timestamps: owner-added only

Timestamps are **for the owner to add**, not the agent. You never invent or guess
a timestamp. In lecture front matter, set `timestamps: false` by default. Do not
include the `time` parameter in `block.html` or inline `time.html` markers; the
owner adds them while verifying the notes against the video.

### Vocabulary gate: applies to the entire page

The vocabulary gate recorded in `context/course-map.md` applies to **every part of
the page without exception**:
- Supplements
- Exercise statements and worked solutions
- Examples and non-examples
- Reading notes and open questions
- Figure captions and annotations

Never use a concept, notation, or theorem the course has not yet reached. For example:
- In Lecture 2, "open set", "basis", norms $\lVert \cdot \rVert$, and metric spaces are forbidden everywhere on the page, including in exercise solutions.
- If an exercise requires bounding distances in $\mathbb{R}^2$ in Lecture 2, use elementary coordinate algebra ($x^2 + y^2$), never the triangle inequality for Euclidean vectors or norms (which arrive in Lecture 14). Using an unreached concept in an exercise solution is a gate defect.

## Block grammar

Use build-time Liquid includes via `{% include block.html ... %}`. The template renders semantic HTML classes and data attributes matching the styles in rule 03.

```liquid
{% capture block_content %}
Let $X$ be a set. A collection $\tau \subseteq \mathcal{P}(X)$ is a **topology on $X$** if ...
{% endcapture %}
{% include block.html type="definition" title="Definition 1.2 (Topology)" content=block_content %}

{% include block.html type="theorem" title="Claim" content="$\mathcal{B}$ is a basis for $\tau$." %}

{% capture proof_content %}
Let $U \in \tau$ and $x \in U$. By definition ...
{% endcapture %}
{% include block.html type="proof" title="Proof" content=proof_content %}

{% capture example_content %}
Let $X$ be any set and let $\tau = \lbrace\varnothing, X\rbrace$.
{% endcapture %}
{% include block.html type="example" title="Example 3 (Finite complement topology)" content=example_content %}

{% include block.html type="non-example" title="Non-example" content="The interval $[0,1)$ does **not** satisfy $(\ast)$." %}

{% capture supp_content %}
Finiteness in condition (T2) is essential. Consider the infinite intersection ...
{% endcapture %}
{% include block.html type="supplement" title="Why finiteness is essential here" content=supp_content %}

{% capture corr_content %}
**As transcribed:** ...
**What is meant:** ...
**Why:** ...
{% endcapture %}
{% include block.html type="correction" title="Transcribed notation error" content=corr_content %}

{% capture open_content %}
The transcript reads "...". Two readings are possible: ... The notes take the first. Please check the video at this point.
{% endcapture %}
{% include block.html type="open-question" title="Algebra on the board" content=open_content %}

{% capture ex_content %}
Show that $\tau'$ defines a topology on $\mathbb{R}^n$.
{% endcapture %}
{% capture ex_solution %}
Verify conditions (T1)–(T3) directly.
{% endcapture %}
{% include block.html type="exercise" title="Exercise 3.1 (set by the lecturer)" content=ex_content solution=ex_solution %}
```

### Math escaping rules: `\lbrace`, `\rbrace`, `\lVert`, `\rVert`, and `aligned`

Kramdown processes markdown escapes inside inline math `$...$` before KaTeX runs.
Backslash-escaped punctuation is stripped to bare characters:

- **Set braces**: Always write `\lbrace` and `\rbrace` (e.g. `\tau =
  \lbrace\varnothing, X\rbrace`, `\lbrace a, b, c\rbrace`, `\lbrace\, x \in X :
  P(x) \,\rbrace`, `\mathbb{Z} \setminus \lbrace n\rbrace`). Never write `\{`
  and `\}` (kramdown emits bare `{` and `}`, which KaTeX reads as grouping
  tokens, causing braces to vanish from rendered pages).
- **Norms**: Always write `\lVert` and `\rVert` (e.g. `\lVert f \rVert_\infty`,
  `\lVert x \rVert_2`). Never write `\|` (kramdown strips `\|` to bare `|`,
  silently converting a double-bar norm into a single-bar absolute value).
- **Multi-line display math (`aligned`)**: Always set `aligned` environments
  inside display math blocks `$$...$$` with `\\` for line breaks. Kramdown
  preserves `\\` inside `$$...$$`, but collapses `\\` to `\` inside single-dollar
  inline math `$...$`.

Numbering: definitions, claims and examples take `<lecture>.<n>` unless the
lecturer used his own number, in which case his number wins and yours goes in
parentheses. Exercises always take `<lecture>.<n>`.

## Named properties

This course names conditions and reuses them across lectures — property
$(\ast)$ appears in Lectures 2 and 3 with different meanings in $\mathbb{R}$,
$\mathbb{R}^2$ and $\mathbb{R}^n$, and the lecturer explicitly says he is
being lazy about the distinction. Handle this as follows:

- State each version separately with a disambiguating subscript
  ($(\ast_{\mathbb{R}})$, $(\ast_{\mathbb{R}^2})$, $(\ast_{\mathbb{R}^n})$).
- Note in a supplement that the lecturer uses the single symbol $(\ast)$ for
  all of them, and why that is harmless.
- Register all versions in the glossary with their lecture of origin.

This is exactly the kind of thing that loses a beginner reading alone, and
exactly the kind of thing a summary would smooth over.

## Board-only passages

Three lectures contain algebra that exists only on the board: **L14**
(Cauchy–Schwarz and the triangle inequality), **L21** (the block-matrix
argument, which the lecturer calls a sketch himself), and the middle of **L37**
(the Tietze estimate). Lesser cases appear in L8, L28 and L30.

The protocol is the same each time, and it is not negotiable:

1. Write the **structure** — what is being set up, what is being concluded, and
   why the step is needed. This is usually fully recoverable. For L14: set
   $w = y - tx$, expand $\langle w,w\rangle \geq 0$ by bilinearity and
   symmetry, read it as a quadratic in $t$, conclude from the discriminant.
2. Mark the missing computation with an Open Question block quoting the
   transcript.
3. If you supply the standard derivation, it goes in a **clearly labelled
   supplement**, never as lecture content, and never presented as what he said.

Inventing these steps is the worst failure available to you, because the reader
cannot detect it. An honest gap sends him to the video for ninety seconds; a
confident wrong derivation misleads him for months.

## Repeated proofs

This lecturer proves the same three axioms for topology after topology, and
the proofs of the second and third axioms are often near-identical across
examples. **Write them out every time.** Do not write "the argument is as in
Example 2". The owner is watching a specific lecture and needs the specific
proof in front of him.

Where the *lecturer* says "the same proof as in $\mathbb{R}$", you may compress
to his level — but then a supplement spells out the argument in full for the
new setting. Repetition is the pedagogy here; do not optimise it away.

## Fidelity self-check before you finish

Run these six checks explicitly and record the result in the report:

1. Unit count and order match pass 1.
2. Every numbered object the lecturer named keeps his number.
3. Every diagram cue from pass 2 has a figure.
4. No sentence of lecture content is untraceable to the transcript.
5. No supplement contains material from later in the course.
6. Every `$` and `$$` closes; no stray `\begin{align}`; KaTeX check passes.

If any check fails, fix it before writing the report.

## What a finished page is not

- Not a summary. Length roughly tracks lecture length; a fifty-minute lecture
  yields a substantial page, not five paragraphs.
- Not an essay on the topic with the lecture as a source.
- Not a cleaned-up transcript — the mathematics must be *typeset and argued*,
  not narrated.
- Not a place to show range. Nothing from later in the subject.
