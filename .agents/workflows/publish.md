# Workflow: Build, Verify, Publish

Trigger: notes have been drafted or edited and the site needs rebuilding, or
the owner says "publish".

## Step 1 — Build

```bash
bundle exec jekyll build --trace
```

A build warning is a failure. Fix it; do not proceed past it.

## Step 2 — Mathematics renders

The most common way this site breaks is silently: an unclosed `$$` swallows
the rest of the page into a math block, and the build still succeeds.

Check every changed page:

- Serve locally (`bundle exec jekyll serve`) and open each changed page.
- Confirm no raw `$`, `\begin{`, `\frac`, or `\varepsilon` appears as literal
  text anywhere in the rendered HTML.
- Confirm the browser console logs no KaTeX parse errors.

A quick source-side check for the commonest fault:

```bash
for f in site/_courses/*/*.md; do
  n=$(grep -o '\$\$' "$f" | wc -l)
  [ $((n % 2)) -ne 0 ] && echo "ODD \$\$ COUNT: $f"
done
```

Unbalanced inline `$` is harder to detect mechanically; read the rendered
page. This is not optional — an unrendered page is unusable.

### Check for stripped escapes in compiled HTML

After every build, grep the compiled HTML for bare `{`, `}` or `|` inside math
spans. Kramdown processes backslash escapes inside `$...$` before KaTeX runs,
stripping `\{`, `\}`, and `\|` to bare `{`, `}`, and `|`. KaTeX then reads bare
braces as invisible grouping tokens (stripping set braces entirely) and bare
pipes as single vertical bars (turning double-bar norms into absolute values).
A silently stripped delimiter renders as plausible-looking but wrong
mathematics, which is worse than a visible failure.

```bash
find _site -name '*.html' -exec grep -En '\$[^$\n]*(\{|\}|\|)[^$\n]*\$' {} +
```

Any match indicates an escape consumed by kramdown. Fix in source using
`\lbrace`, `\rbrace`, `\lVert`, or `\rVert`.

## Step 3 — Figures

- Every `{% include figure.html %}` resolves to a file that exists.
- Every SVG has a `<title>` and an `aria-labelledby` or `role="img"` with
  `aria-label`.
- Each figure renders correctly in both light and dark themes. Check one
  figure per lecture at minimum; check all of them if the tokens changed.

## Step 4 — Navigation

- `prev` and `next` resolve in both directions across the whole course.
- The course index lists every lecture in `_courses/<course>/`, in order.
- Breadcrumbs correct on every page.
- No link resolves to a URL missing the `baseurl`.

## Step 5 — Search index

Rebuild `search.json`. Confirm it contains an entry per lecture with title,
coverage, and body text with LaTeX source stripped — searching for
`varepsilon` should not match every page on the site.

## Step 6 — Responsive and accessibility spot-check

At 360px wide: no horizontal scroll, no figure clipped, controls reachable.
Tab through a lecture page: focus is visible at every stop, the three toggles
are operable by keyboard, `<details>` blocks open with Enter.

## Step 7 — Commit and deploy

```bash
git add -A
git commit -m "Add Lecture NN: <short title>"
git push
```

Confirm `source/*/references/` is not in the diff. If a PDF has been staged,
stop, unstage it, and fix `.gitignore` before pushing. Textbook PDFs must
never reach the repository.

GitHub Pages builds from the default branch. Wait for the build, then load the
live URL and open the new lecture page. Local success is not deployment
success — `baseurl` mistakes only appear live.

## Step 8 — Report

One short message: what was published, the live URL of the new page, and
anything that needs the owner's eyes. Nothing else.

---

## Recovery

If the live site is broken, revert the last commit and push, then diagnose
locally. Never debug on the published branch — this is the owner's study
material and he may be reading it tonight.
