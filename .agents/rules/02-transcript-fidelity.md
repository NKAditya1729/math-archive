# Rule: Transcript Fidelity

Applies to every task that turns a transcript into notes. This is the rule that
makes the site useful; the mathematics is worthless to the owner if he cannot
follow along with the video.

## The correspondence test

Imagine him watching the lecture with the notes open. At any moment he can
pause and put his finger on the corresponding place. That is the standard.

- **Order is preserved absolutely.** His sequence is the notes' sequence. If he
  proves condition (2) before (3), so do you. If he digresses and returns, the
  notes digress and return.
- **Numbering is preserved.** "Example 5", "property $(\ast)$", "step two",
  "claim one" keep their identifiers even where arbitrary.
- **His examples, not better ones.** His method, not a slicker one.
- **His asides stay** when they carry content — "let us emphasize that in this
  condition there are only finitely many $U_i$", "it's important to say that
  this map is surjective". These are the teaching.

## What to strip

Substantive fidelity, not verbatim transcription. Remove fillers (*uh, um, so,
yeah, okay, right?, you know*), restarts, board-management talk, and repeated
sentences — keeping the clearest version. Keep emphasis, warnings, "note that",
## The verification rhythm

The lecturer teaches through a deliberate rhythm: **state the obligation → discharge it → declare it closed**. This is repeated for every axiom, in every example, in every verification across the course. That repetition is the core pedagogic device by which a beginner learns the shape of a mathematical argument.

Protect these six elements as **lecture content**; never compress or omit them:

1. **Obligation statements** — "we need to check that…", "then their intersection should be in $\tau$", "so then we need to show that the union is in $\tau$". These come *before* the argument and explicitly name its target.
2. **Recall statements** — "recall that the first condition was…", "recall that $\tau$ is a collection of subsets of $X$". He restates prior definitions constantly; that repetition is deliberate.
3. **Closing declarations** — "so the second condition is also satisfied", "therefore the first condition is satisfied". Write the sentence. A ✓ may accompany it but never replace it.
4. **Method signposting** — "let's check them one by one", "once again, we apply the same method", "exactly as in the previous point".
5. **Case announcements** — "so first consider the case where…", "so if this does not happen, the only other possibility is…".
6. **Reason clauses in his order** — where he says "because $\tau$ is all of the power set, and the power set contains $\varnothing$ and $X$", do not re-derive it in the opposite direction.

**Prohibition: never open a proof by summarising why it will work.** Sentences such as "each is immediate for the same reason: everything in sight is a subset of $X$" front-load the punchline and reduce the subsequent checks to mere formalities. If that overarching observation is worth making, place it in a supplement *after* the proof.

Where his own scaffolding is thin — where he says "similarly" or "exactly as before" over something a beginner needs spelled out — supply the missing statement in a marked supplement, never silently in the lecture body.

## Multi-part transcripts

Lecture 34 arrives as `Lecture_34_Part_1/2/3.rtf`. **One lecture, one page.**
Concatenate in part order before the skeleton pass. Part 1 is the quotient
topology theorem, Part 2 topological groups and $G/H$ Hausdorff, Part 3 the
Grassmannian — one continuous argument. Treating a part as a lecture produces
three broken pages and wrong `prev`/`next` links throughout Part IV.

Filenames are not authoritative for lecture number. Confirm from the lecturer's
own words, or from the "in the previous lecture we…" opening.

## The four block types

Every piece of content is one of four kinds, visually distinct on the page.

**1. Lecture content** — plain body text. Everything here was said. The default
and the majority.

**2. Supplement** — nothing in it was said in the lecture.

```markdown
> [!SUPPLEMENT]
> **Why the minimum works.** A minimum of finitely many positive numbers is
> positive; an infimum of infinitely many need not be...
```

**3. Correction Note** — the transcript as it stands is mathematically wrong.

```markdown
> [!CORRECTION]
> **As transcribed:** $(a,b) = \{x : x < a \text{ and } x < b\}$.
> **What is meant:** $\{x : a < x < b\}$.
> **Why:** as transcribed this is $(-\infty,\min(a,b))$; his later use of
> $(a,b)$, and his statement that $\mathbb{R} = (-\infty,+\infty)$, are
> consistent only with the corrected reading.
```

**4. Open Question** — you could not determine what was meant.

```markdown
> [!OPEN]
> The transcript here reads only "this is equal to… and this is less than
> equal to…". The computation was on the board. The structure of the argument
> is given above; the algebraic steps need the video.
```

The notes then proceed with the **correct** mathematics. Never propagate an
error; never quietly repair one. Every Correction Note also goes in the report.

The site shows lecture content by default; supplements are revealed by a
toggle. Corrections and Open Questions are always visible.

## Judging a suspected error

1. **Is it a transcription artefact?** Check `context/transcript-quirks.md`
   first. Most are.
2. **Is it already adjudicated?** Check `context/known-defects.md`. Every real
   error in all 40 lectures is registered there with its ruling. Use it; do not
   re-litigate.
3. **Is it correct but non-standard?** Then it is *not* an error. Keep it, note
   the standard form in a supplement. He defines compactness only for Hausdorff
   spaces and reverses his own axiom order in L31 — both deliberate.
4. **Is the library silent?** Lectures 21, 22, 27, 28 and 34 have no parallel
   treatment in the seven books. Absence is not evidence of error.
5. **Genuinely wrong?** Correction Note, full reasoning, high prominence in the
   report.
6. **Unsure?** Open Question. Never resolve it silently.

**The governing heuristic: when a stated result and the proof beneath it
disagree, the proof wins**, and the Correction Note cites the proof as its
evidence. Almost every real defect in this course is a swapped word in a
statement — connected/non-empty, first/second, equal/equivalent — with a
correct proof underneath.

## Passages you must not reconstruct

Three lectures have algebra that exists only on the board: **L14** (Cauchy–
Schwarz and the triangle inequality), **L21** (the block-matrix argument, which
he calls a sketch himself), and the middle of **L37** (the Tietze estimate).

Write the recoverable *structure* — what is being set up, what is concluded —
then an Open Question block quoting the transcript. If you supply the standard
derivation, it goes in a clearly labelled supplement, never as lecture content.
Inventing these steps is the single worst failure available to you here,
because the reader cannot detect it.

## Diagram cues — the most important detection task

The lecturer draws constantly; the transcription captures none of it. Roughly a
third of the mathematical content of some lectures was drawn, and survives only
as deictic language. **Every phrase below means a figure was on the board.**

| Transcript phrase | Meaning |
|---|---|
| "so this looks like the following" / "in terms of a diagram" | a figure follows |
| "maybe I can make it on the next page" / "let's make a picture" | a figure follows |
| "so this is..." / "this is our circle" / "let's say this is one" | labelling a figure |
| "this distance is $x$, and this distance is $1-x$" | annotated lengths |
| "we can take a point here" / "$x$ is somewhere over here" | a marked point |
| "$U_i$ may be some set like this" / "our $U$ could be this" | a free-form blob |
| "the region inside this circle" / "this green region" | shading |
| "no matter how small we take $\varepsilon$, it goes outside" | a failure figure |
| "let's just copy this diagram" | the previous figure, reused |
| "so this is a picture of the projection" | a map drawn between two spaces |
| "and here we have this map like this" | a commutative diagram |
| "so these are all these lines at one upon $n$" | the L20 counterexample |
| "we can take a small square like this" | a neighbourhood inside a region |

**Non-examples and failure figures matter most.** The closed disc failing
$(\ast)$ at $(1,0)$, and the space $C$ in L20 where no path leaves $Y$, live
entirely in their pictures.

Commutative diagrams are frequent from L9 onward and are figures too — L9's
$f_0$ factorisation, L10's $\varphi$ through $H$, L27's left-translation
square, L32's $f \circ j = i$, L34's $\pi$ and $f_0$. Draw them.

When a cue is ambiguous, draw the mathematically standard picture and say in
the report that you inferred it. Log every figure with its trigger phrase.

## The lecturer's forward references

Lectures end with statements like "in the next lecture we will see two
important properties that these bases have". Keep these — they are the thread
between pages and become the next lecture's *Where we are*. Record them in
`context/course-map.md`.

Likewise, **L33 explicitly corrects L32** ("I had said that $X$ has to be
compact, but that's not necessary"). When a lecture corrects an earlier one,
add a forward note to the earlier page rather than editing its argument.

"This is an exercise" is a first-class object: it goes in the Exercises section
with its number and is **never solved in the main body**.
