# Rule: Site Architecture and Design

Applies to build, layout, styling, and deployment tasks.

## Stack

Jekyll, deployed by GitHub Pages from the repository's default branch. This
matches the owner's existing archive site and needs no CI configuration. Do
not migrate to another generator without being asked.

- Math: **KaTeX**, loaded from CDN with the auto-render extension, or
  pre-rendered at build time if the build script supports it.
- Search: **lunr.js** over a generated `search.json`. No external service.
- Figures: **inline SVG**, authored by you, stored as real files in
  `site/_includes/figures/<course>/<lecture-id>/<figure-id>.svg` and pulled in
  with `{% include figure.html %}`, never as `<img>` — inline SVG inherits the
  page's colour tokens and stays crisp in both themes.
  **They must live under `_includes/` as a real directory, not a symlink into
  `assets/`.** GitHub Pages runs Jekyll in safe mode, which ignores symlinks:
  a symlinked figures directory works locally and silently fails live.
- No JavaScript framework. No build step beyond Jekyll. The whole site must
  work with JS disabled apart from the toggles and search.

## URL and file layout

```
site/
  _courses/
    point-set-topology/
      index.md              → /point-set-topology/
      lecture-01.md         → /point-set-topology/lecture-01/
      lecture-02.md
  _layouts/  lecture.html, course.html, default.html
  _includes/ figure.html, katex.html, toggle.html
  assets/
    css/site.css
    figures/point-set-topology/lecture-02/open-square.svg
  index.md                  → /
```

Course slugs: `point-set-topology`, `real-analysis`, `complex-analysis`.
Lecture files: `lecture-01.md`, zero-padded, always two digits.

The home page lists courses. A course page lists its lectures in an
accordion — collapsed by default, one row per lecture showing number, title,
and the one-line coverage statement. That accordion is the "toggle" the owner
wants: open a lecture, read, close, move on.

**Group the accordion by part.** Point-Set Topology runs to forty lectures; a
flat list of forty rows is unusable. The four parts are in
`context/course-map.md` — I (1–6) building spaces, II (7–15) continuous maps
and metric spaces, III (16–22) connectedness, IV (23–40) compactness,
quotients, separation. Each part gets a heading and a one-line description; the
lectures sit under it. Parts are open by default, lectures collapsed.

Multi-part transcripts do **not** become multiple entries. Lecture 34 is one
row.

## Required front matter on every lecture page

```yaml
---
layout: lecture
course: point-set-topology
course_title: Point-Set Topology
lecture_number: 3
title: "Standard Topology on R^n; Open Sets; Basis for a Topology"
lecture_date:
coverage: >
  Completes the proof that the standard topology on R^2 is a topology;
  states the standard topology on R^n as an exercise; defines open sets and
  a basis for a topology; shows the open intervals form a basis for the
  standard topology on R.
status: drafted        # drafted | audio-reviewed | verified  — you set only `drafted`
version: 1.0
figures: 3
corrections: 1
prev: lecture-02
next: 
---
```

`coverage` is the single most valuable field. It is what the owner scans on
the course page to find the lecture he wants. Write it as a dense sentence or
two naming every concept, in the lecture's own order. Never write "continues
the discussion of topology."

## Page controls

Three controls in a small bar at the top of every lecture page:

1. **Supplements — hidden / shown.** Default hidden. When hidden, the page is
   exactly the lecture. This is the control that serves the one-to-one
   requirement, and it is the direct analogue of the script toggle on the
   owner's existing archive.
2. **Proofs — expanded / collapsed.** Default expanded. Collapsing turns the
   page into a revision sheet of statements only.
3. **Theme — light / dark.** Respect `prefers-color-scheme` on first load.

State persists across pages via `localStorage`. Both settings survive a
reload. Do not add a fourth control without being asked.

Also required on every lecture page: breadcrumb, previous/next lecture links
at the foot, and a "Report an error" mailto link prefilled with the course
and lecture number.

## Design tokens

The brief: a quiet place to read hard mathematics at night, alone. Not a
product, not a blog. The visual references are a slate board and a printed
monograph, not a documentation site.

```css
:root {
  --paper:      #FBFBF9;   /* page — near-white, not cream */
  --ink:        #1B2A38;   /* body text — deep blue-slate */
  --ink-soft:   #56646F;   /* captions, metadata */
  --rule:       #DCE2E6;   /* hairlines, table borders */
  --accent:     #0F5C68;   /* teal — definitions, links, figure strokes */
  --accent-bg:  #EDF4F4;   /* supplement block background */
  --flag:       #8A4B2A;   /* correction notes — the only warm tone on the site */
}
```

Dark theme inverts `--paper`/`--ink` to `#141B21` / `#E4E9EC`, lifts
`--accent` to `#4FA3AE`, and keeps `--flag` at `#C88055`.

Type, two families with clearly separate jobs:

- **Body and mathematics: Source Serif 4.** A serif, because the body text
  sits beside KaTeX's Computer Modern all day and a sans clashes with it.
  Body 18px / line-height 1.65 / measure capped at 68 characters.
- **Interface: IBM Plex Sans.** Navigation, block labels, figure captions,
  metadata. Never used for body text.

Type scale: 18 body, 15 caption and interface, 22 subheading, 28 lecture
title. No display sizes; nothing on this site is being sold.

Where the boldness goes: **the definition block**. A definition is set with a
2px teal left rule, one step larger than body, and generous space above and
below — so that scrolling a lecture, the definitions are what the eye finds.
Everything else stays quiet.

Explicitly avoid: cards with uniform border-radius and grey drop-shadows;
tracked-out all-caps eyebrow labels; gradient washes; metadata joined by
middle dots; arrows appended to link text; entrance animations on scroll. The
only motion on the site is the toggle disclosure.

## Block rendering

| Block | Rendering |
|---|---|
| Definition | teal left rule, larger, numbered |
| Theorem / Proposition / Claim | teal left rule, italic statement |
| Proof | indented, smaller leading, `∎` right-aligned at close |
| Example / Non-example | numbered, hairline box, non-examples get a warm hairline |
| Supplement | tinted `--accent-bg`, small Plex label "Supplement — not in the lecture" |
| Correction | `--flag` left rule, always visible, label "Correction" |
| Open Question | dashed `--flag` rule, label "Unresolved — needs the video" |
| Exercise | numbered, hairline, `<details>` for any worked solution |

## Accessibility and quality floor

Responsive to 360px. Visible keyboard focus. `prefers-reduced-motion`
respected. All SVG figures carry a `<title>` and a `role="img"` with an
`aria-label` that describes the mathematical content, not the picture: not
"a circle with a dot", but "the open unit disc with a point $p$ inside it and
a small square around $p$ contained in the disc".

Colour is never the only carrier of meaning — every block type has a text
label as well as a colour.

## Deployment

Repository: a **new** repository, separate from the existing archive, so the
two do not entangle. Suggested name `math-archive`, published at
`https://<user>.github.io/math-archive/`. Set `baseurl: "/math-archive"` in
`_config.yml` — omitting it is the single most common cause of a site that
builds locally and 404s live.

`source/*/references/` must be listed in `.gitignore` **and** in Jekyll's
`exclude:`. The textbook PDFs are the owner's personal copies and must never
be committed or published.
