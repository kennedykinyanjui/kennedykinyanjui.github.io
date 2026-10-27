# kennedykinyanjui.github.io

Personal site and CV for Kennedy Kinyanjui — platform engineer, Nairobi, Kenya.

Live at **https://kennedykinyanjui.github.io**

## Stack

One hand-written page. No framework, no build step, no package manager, no
dependencies to install or update.

| | |
|---|---|
| Markup | `index.html` — semantic HTML, anchor-linked sections |
| Styles | `css/style.css` — one stylesheet, CSS custom properties, Grid and Flexbox |
| Scripts | ~25 lines inline: the footer year and an `IntersectionObserver` that highlights the current nav link |
| Fonts | Inter and JetBrains Mono from Google Fonts, with system fallbacks |
| Hosting | GitHub Pages, served from the `master` branch root |

The page is around 27 KB of HTML and CSS plus the fonts. Everything renders
without JavaScript; the script only adds nav highlighting.

## Running it locally

Any static file server works.

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Layout

```
index.html        the whole page
404.html          GitHub Pages error page, reuses css/style.css
css/style.css     the only stylesheet
favicon.svg       KK monogram
og.jpg            1200x630 link-preview card
robots.txt        allows everything, points at the sitemap
sitemap.xml       one URL; update lastmod when the content changes
```

## Design

Dark, typographic, deliberately plain. The rules worth keeping:

- **Colour lives in custom properties** at the top of `css/style.css`. Change
  `--accent` and the whole page follows: links, the active nav pill, role
  titles, buttons, the hero wash and the focus ring.
- **One accent colour**, used sparingly. The page is carried by type and
  spacing, not by colour.
- **Monospace is a signal, not decoration.** It marks machine-ish things —
  dates, section labels, field keys — and nothing else.
- **Content sets the width.** Prose is capped around 64–68 characters.
- **It must work without JavaScript.** Nothing renders from script.
- **There is a print stylesheet.** The dark theme inverts to black-on-white and
  the nav and buttons are dropped, so the page prints or saves to PDF as a
  clean CV. Check it after any layout change.

## Editing notes

- **Sections are anchor targets.** The nav links to `#about`, `#experience`,
  `#competencies` and `#contact`. The nav highlighting reads those same `href`s,
  so renaming a section `id` means updating the nav link in the same change.
  `scroll-margin-top` keeps headings clear of the sticky nav.
- **Content tracks the CV.** The About summary, Competencies and Experience
  sections are transcribed from the current CV. When the CV changes, update
  those together with the hero role, the `<head>` metadata, the JSON-LD block
  and `og.jpg`, so the page, the preview card and the CV never disagree.
- **`og.jpg` is generated, not hand-drawn.** It is a 1200x630 render of an SVG.
  The source SVG is not kept in the repo; regenerate from scratch if the name,
  role or accent changes.
- **Accessibility basics are load-bearing.** Skip link, visible `:focus-visible`
  ring, landmark elements, `aria-labelledby` on every section. Keep them.

## Deploying

Pushing to `master` publishes the site. There is no staging environment and no
CI, so changes are live within a minute or two of the push — preview locally
first.

## Known gaps

- No automated checks. HTML validation, link checking and a Lighthouse budget
  would fit comfortably in a GitHub Actions workflow.
- Google Fonts is the only third-party request, and it cannot carry a
  subresource integrity hash. Self-hosting the two families would remove it.
- There is no projects section. For a platform engineer this is the most
  valuable thing the site could add.

## Licence

© Kennedy Kinyanjui. The markup and stylesheet are original; the site no longer
uses the W3layouts template it started from.
