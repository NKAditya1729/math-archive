---
name: figure-authoring
description: Draws the mathematical diagrams a lecturer put on the board but the transcript lost — number lines, epsilon-neighbourhoods, open squares and balls, regions in the plane, blob-and-point pictures, and failure diagrams for non-examples. Use whenever a diagram cue is detected in a transcript, when a definition needs a picture, or when an existing figure must be corrected or restyled. Covers SVG conventions, the site colour tokens, labelling, captions, and accessibility.
---

# Authoring Figures

Every figure on this site is **hand-authored inline SVG**. Never a raster
image, never an image pulled from the web, never a screenshot of a rendered
formula.

Three reasons this is not negotiable: images from the web carry unknown
licences and this is a public site; a drawn figure can match precisely what
this lecturer put on this board, which no stock diagram will; and inline SVG
inherits the page's colour tokens, so a single figure works in both light and
dark themes and stays sharp at any zoom.

## The job

You are reconstructing a specific board, not illustrating a topic. The
lecturer's own words tell you what was drawn — down to which distances he
labelled. Match them.

From Lecture 2, the transcript reads: *"So let this dis— So this distance is
$x$, and this distance is one minus $x$."* That is not decoration. He labelled
exactly two distances because those two are what the $\min$ in the next line
is taken over. Your figure labels those two distances and no others.

## File and include conventions

```
site/_includes/figures/<course>/<lecture-id>/<figure-id>.svg
site/_includes/figures/point-set-topology/lecture-02/epsilon-in-open-interval.svg
```

A real directory under `_includes/`, never a symlink into `assets/` — GitHub
Pages ignores symlinks in safe mode, so a symlinked figures directory builds
fine locally and fails live.

`figure-id` is a short descriptive slug, never `figure-1`. Include with:

```liquid
{% include figure.html
   src="point-set-topology/lecture-02/epsilon-in-open-interval.svg"
   caption="Choosing $\varepsilon = \min\{x/2,\,(1-x)/2\}$ places the whole interval $(x-\varepsilon,\,x+\varepsilon)$ inside $(0,1)$."
   alt="The open interval from 0 to 1 on a number line, with a point x inside it. The distance from 0 to x and the distance from x to 1 are both marked. A shorter interval centred at x lies strictly between 0 and 1." %}
```

Captions carry mathematics and are rendered by KaTeX; write them as a
sentence stating what the picture shows, not "Figure 3".

`alt` describes the *mathematical content* for a reader who cannot see it —
what is where and what relation holds — not the visual appearance.

## Drawing conventions

Use the page tokens by name so the figure re-themes automatically:

```svg
<svg viewBox="0 0 640 220" role="img" aria-labelledby="t1"
     xmlns="http://www.w3.org/2000/svg" class="fig">
  <title id="t1">…same text as alt…</title>
  …
</svg>
```

```css
.fig { --stroke: var(--ink); --hl: var(--accent); --fail: var(--flag); }
```

| Element | Convention |
|---|---|
| Axes, number lines | 1.5px `--ink`, arrowheads only if the line is unbounded |
| The set under discussion | 2px `--accent` outline |
| Region interior | `--accent` at 10% opacity |
| Open boundary | dashed, 4 2 |
| Closed boundary | solid |
| Endpoint excluded | open circle, white fill, `--accent` stroke |
| Endpoint included | filled disc |
| The chosen neighbourhood | 2px `--accent`, 18% fill |
| A failure (nothing works here) | `--flag`, dashed |
| Labelled distance | thin line with end ticks, label above in italic |
| Point labels | italic serif, offset up-right by 6px |

Open versus closed must be visually unmistakable. Half the content of this
course is the difference between $(0,1)$ and $[0,1)$, and a beginner who
cannot see which is which from the picture is being misled by it.

Text in SVG: 14px, `font-style: italic` for variables, `font-family: 'Source
Serif 4', Georgia, serif` so labels match the body type. Do not attempt to
render real LaTeX inside SVG — keep labels to single symbols and short
expressions ($x$, $\varepsilon$, $a$, $1-x$, $U_i$, $S_\varepsilon(a,b)$).
Anything longer belongs in the caption.

Canvas: 640 wide for full-width figures, 320 for a pair set side by side.
Height to suit. Always `viewBox`, never fixed `width`/`height` attributes —
the CSS sets `max-width: 100%`.

## The standing figure vocabulary for this course

These recur. Draw them consistently so that the owner learns to read them.

1. **Number line with a neighbourhood.** Line, marked endpoints, interior
   point $x$, the symmetric interval $(x-\varepsilon, x+\varepsilon)$ shown
   below the line as a bracketed span, both distances labelled.
2. **Nested intervals for the $\min$ argument.** Several
   $(x-\varepsilon_i, x+\varepsilon_i)$ drawn concentrically, the smallest
   highlighted, with $\varepsilon = \min_i \varepsilon_i$ labelled.
3. **The open square $S_\varepsilon(a,b)$.** Axes, centre $(a,b)$ marked,
   dashed boundary, all four half-side distances labelled $\varepsilon$
   exactly as the lecturer labelled them ("this length is epsilon" — four
   times).
4. **Region-and-point.** A free-form closed blob for a general $U_i$, a
   point inside, a small square or disc around the point contained in the
   blob. This is the picture behind almost every proof in the course.
5. **Failure at a boundary point.** The closed unit disc, the point $(1,0)$
   on the boundary, two or three progressively smaller squares around it each
   drawn in `--flag` and each visibly crossing the boundary. Caption states
   that no $\varepsilon$ works.
6. **Two coverings compared.** Squares versus discs around the same point,
   each containing the other at a smaller scale — the picture behind the
   exercise that $\tau = \tau'$ on $\mathbb{R}^n$.

Figures 5 and 6 are the two most valuable in Part I. Both are non-obvious to a
beginner and neither survives transcription.

## Later in the course

7. **Commutative diagrams.** Frequent from L9 onward and easy to miss, because
   the transcript renders them as "we have this map like this". Nodes in
   Source Serif italic, arrows 1.5px `--ink` with a small filled head, labels
   in Plex Sans at 13px above or left of the arrow, dotted stroke for an
   induced or asserted map. Standing examples: L9's $f_0$ factorisation
   through a subspace, L10's $\varphi$ through $H$, L27's left-translation
   square, L32's $f \circ j = i$, L34's $\pi$ and $f_0$.
8. **The tube.** L24. A rectangle for $X \times Y$, the vertical slice
   $\{x\} \times Y$ picked out in `--accent`, the blob $W$ around it, and the
   tube $U \times Y$ as a vertical band. This figure is the entire content of
   the tube lemma and the transcript destroys the statement (see quirks) — it
   is the single most valuable figure in Part IV.
9. **The L20 counterexample.** Vertical unit segments at $x = 1/n$ for
   $n = 1,2,3,4$, converging toward the $y$-axis; the segment $Y = \{0\}
   \times (0,1]$ with an open circle at the origin; the $x$-axis minus the
   origin. Mark $P = (0,1)$ and $(1,1)$. A second panel zooms into $U \cap C$
   showing the disconnection into $V_1$ and $V_2$.
10. **Stereographic projection.** L10, L17, L33. Circle or sphere, north pole
    $P$ marked, a point $x$, the line through both, and the image $Q$ on the
    plane. Reused three times — draw it once and reuse the file.
11. **One-point compactification.** L31–L33. The line bending into a circle
    with $p_0$ closing it; the plane as a sphere. Show a type-B open set as
    the complement of a compact blob.
12. **Separation figures.** L23, L30, L35, L38. Two points, or a point and a
    closed set, or two closed sets, each inside its own `--accent` region,
    the regions visibly disjoint. Four variants of one picture; keep them
    visually consistent so the escalation Hausdorff → regular → normal is
    legible at a glance.
13. **Supremum arguments.** L16, L20, L23. The interval $[0,1]$, the set $S$
    shaded, $a$ or $t_0$ or $x_0$ marked at its supremum, a sequence
    approaching from the left, and the $\varepsilon$-neighbourhood that
    produces the contradiction.

Figures 8 and 9 are the highest-value drawings in the back half of the course,
for the same reason as 5 and 6: they carry content the audio does not.

## Figures the lecturer did not draw

Board reconstructions are recovery of lost content and are unlimited. A second
category is also sanctioned, under a strict budget: **supplement figures**,
drawn for something the lecture stated but did not picture.

**The test.** A figure earns its place if removing it would make a specific
sentence harder to *believe* — not merely harder to picture. A blob labelled
$U$ beside the definition of a topology aids picturing and nothing else; it is
decoration. A square around $(1,0)$ poking outside the closed disc *is* the
reason the non-example fails; it earns its place.

**The budget: at most two supplement figures per lecture**, on top of however
many board reconstructions the transcript demands. Over budget, cut the one
that merely restates a formula.

A supplement figure lives inside a `supplement` block, never in the lecture
body, and its caption says plainly that it was not on the board.

### The four kinds that survive the test

1. **Board reconstructions** — unlimited, see above.
2. **Failure figures** — why a non-example fails. The highest value per pixel
   in this course, because the non-examples are where the definitions get
   their teeth. $[0,1)$ at $0$; the closed disc at $(1,0)$; an infinite
   intersection escaping the finite-complement topology; the comb of L20.
3. **Structure diagrams** — pictures of the *theory*, not of a space. Hasse
   diagrams of topologies ordered by fineness; implication graphs among
   properties (path connected $\Rightarrow$ connected; compact $\Rightarrow$
   closed in Hausdorff). Badly under-used, and exactly what a reader studying
   alone needs, because they answer "where does this sit" rather than "what
   does this look like".
4. **Commutative diagrams** — see the vocabulary above.

### What stays out

Generic blobs illustrating "a set". A picture for every definition. Anything
that restates a formula in pictorial form. Anything decorative. A figure whose
caption you cannot write as a claim.

### Standing supplement figures worth drawing

**L1 — the lattice on $\{a,b,c\}$.** A Hasse diagram: trivial at the bottom,
discrete at the top, four or five topologies between. Makes the supplement
"every topology sits between the trivial and the discrete" visible, and plants
coarser/finer eight lectures before L5 needs it.

**L1 — the finite-complement topology on $\mathbb{Z}$.** Integer dots on a
line; an open set drawn as *everything except three of them*. The most
important early intuition shift in the course: open has nothing to do with
intervals. Second panel: $\mathbb{Z}\setminus\{1\}$,
$\mathbb{Z}\setminus\{1,2\}$, $\mathbb{Z}\setminus\{1,2,3\}$ shrinking
toward a set that is not open.

**Part boundaries — the running fineness lattice.** One diagram, updated at the
end of Parts I, II, III and IV, ordering every topology met so far by
fineness: trivial, finite-complement, standard, subspace, product, box,
discrete, metric, quotient. Lives on the course index, not on a lecture page.
The closest thing to a map of the subject the site can carry.

**L19 / L23 / L30 — the implication graph.** As topological properties
accumulate, one diagram of the one-way implications, with a labelled
counterexample on each arrow that does not reverse. Update it, do not
duplicate it.

## Quality bar

- Legible at 360px wide.
- No text smaller than 12px.
- Colour is never the only signal — dashed/solid and open/filled carry the
  meaning too.
- Nothing decorative. No grid backgrounds, no shadows, no gradients, no
  rounded frame around the figure.
- If a picture needs more than about eight labels, it is doing two jobs.
  Split it.

## Logging

Every figure goes in the build report with the transcript phrase that
triggered it, so the owner can check the reconstruction against the board:

```
FIGURE  epsilon-in-open-interval.svg
CUE     "So let this dis— So this distance is x, and this distance is one
         minus x." (Lecture 2)
DREW    Number line 0 to 1, interior point x, both distances labelled,
        resulting epsilon-interval shown below.
```
