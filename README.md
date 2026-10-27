# kennedykinyanjui.github.io

Personal site and CV for Kennedy Kinyanjui — platform engineer, Nairobi, Kenya.

Live at **https://kennedykinyanjui.github.io**

## Stack

A single static page. No build step, no package manager, no framework.

| | |
|---|---|
| Markup | `index.html` — one page, anchor-linked sections |
| Styles | `css/style.css` (hand-edited), `css/bootstrap.min.css` (3.3.4, grid only), `css/font-awesome.min.css` (icons) |
| Scripts | jQuery 2.1.4, plus small plugins for the nav and smooth scroll |
| Fonts | Font Awesome + Bootstrap glyphicons in `fonts/`; Google Fonts loaded over the network |
| Hosting | GitHub Pages, served from the `master` branch root |

## Running it locally

Any static file server works. There is nothing to install or compile.

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000. Opening `index.html` directly via `file://`
also mostly works, but relative asset paths behave more like production when
served over HTTP.

## Layout

```
index.html        the whole page
404.html          GitHub Pages error page
favicon.svg       KK monogram
robots.txt        allows everything, points at the sitemap
sitemap.xml       one URL; update lastmod when the content changes
css/              styles
js/               jQuery and plugins
fonts/            icon fonts
images/           only the assets actually referenced by index.html or style.css
```

## Deploying

Pushing to `master` publishes the site. There is no staging environment and no
CI, so changes are live within a minute or two of the push — preview locally
first.

## Editing notes

- **Sections are anchor targets.** The nav in `index.html` links to `#home`,
  `#about`, `#highlight`, `#experiences`, `#skills` and `#contact`. The scroll
  handler at the bottom of the file calls `.offset()` on the target, which
  throws if the `id` is missing — so if you comment out a section, remove its
  nav item in the same change.
- **The "My projects" section is still commented out** (the large comment block
  after the skills section). It is the original template's gallery: stock photos
  and lorem ipsum, and the images it referenced have been deleted. Treat it as a
  placeholder to rewrite with real work rather than something to simply
  re-enable.
- **Keep `images/` lean.** Only files referenced from `index.html` or
  `css/style.css` belong here; the template shipped with far more than the page
  uses.
- **Metadata lives in `<head>`.** The description, canonical URL and Open Graph
  / Twitter Card tags are what produce the link preview when the site is shared.
  If the tagline or role changes, update them together — and update
  `sitemap.xml`'s `lastmod`.
- **Content tracks the CV.** The About summary, Core Competencies and
  Professional Experience sections are transcribed from the current CV. When the
  CV changes, update those three together with the banner role and the `<head>`
  metadata, so the page and the CV never disagree.

## Known gaps

- jQuery 2.1.4 and Bootstrap 3.3.4 both date from 2015 and have published CVEs.
  Nothing on the page takes user input, so exploitability is low, but they
  should be upgraded (jQuery 3.7.x is close to a drop-in; Bootstrap 3 → 5 is a
  real port, and only the grid is used).
- No automated checks. HTML validation, link checking and a Lighthouse budget
  would fit comfortably in a GitHub Actions workflow.

## Licence

The page layout started from a [W3layouts](https://w3layouts.com) template —
see [`w3layouts-License.txt`](w3layouts-License.txt) for its terms. The CV
content, copy and photographs are © Kennedy Kinyanjui.
