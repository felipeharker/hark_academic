# hark_academic

The academic architecture and urban design projects of Felipe E. Harker:
three projects from the Bachelor of Architecture at the University of
Houston, a page each. Served at **https://hark-academic.onrender.com/**, and
linked from the portfolio, [felipeharker.org](https://felipeharker.org/).

One of four sites built to the same standard, each in its own repository:

| Site | Address | Repository |
|---|---|---|
| Portfolio, and the standards | https://felipeharker.org/ | [`hark_web`](https://github.com/felipeharker/hark_web) |
| Academic | https://hark-academic.onrender.com/ | `hark_academic`, this one |
| Birding | https://hark-birding.onrender.com/ | [`hark_birding`](https://github.com/felipeharker/hark_birding) |
| Resume | https://hark-resume.onrender.com/ | [`hark_resume`](https://github.com/felipeharker/hark_resume) |

The design standard — the one shared stylesheet, its docs and its specimen
page — lives in `hark_web` and is served at
https://felipeharker.org/standards/. Every page here links
`https://felipeharker.org/standards/hark.css`; there is no copy of it here.

## Layout

```
hark_academic/
  README.md
  AGENTS.md                   rules for coding agents (CLAUDE.md points here)
  render.yaml                 the Render service, recorded
  tools/
    site.mjs                  this site's address, and the family's
    serve.mjs                 serve site/ locally
    check.mjs                 check pages, links and published files
  source/                     working files, git-ignored (see its README)
  site/                       published, and nothing else
    index.html                one row per project
    projects/<slug>.html      one page per project
    assets/
      covers/<slug>.jpg       3:2 covers, 1500 x 1000 or smaller
      projects/<slug>/        the board images
```

## Projects

| Page | Images | Working files in `source/` |
|---|---|---|
| `projects/living-outside-the-box.html` | `lotb-01` … `lotb-13` | the board-set PDF; the Rhino model (144 MB) |
| `projects/dead-mall-fall.html` | `dmf-01` … `dmf-05`, `dmf-banner` | the board-set PDF |
| `projects/collingsworth-marketplace.html` | `cmp-01` … `cmp-07` | the board-set PDF |

The board-set PDFs are not published for now, and the pages do not link
them (`hark_web`, `planning/decisions.md`).

## Running and checking

Node 20.9 or newer, nothing else.

```bash
node tools/serve.mjs
```

serves the site at http://localhost:8000/, straight from `site/`. The
stylesheet comes from felipeharker.org, and the site links lead to the live
sites. Before a commit:

```bash
node tools/check.mjs
```

## Adding a project

1. **The page.** Copy `site/projects/living-outside-the-box.html` to
   `site/projects/<slug>.html`. Replace the title, kicker, subtitle,
   dateline, description and every section. Keep the back link (`← Academic
   Projects`) and the colophon as they are, with `aria-current="page"` on
   Academic.
2. **The images.** Board images go in `site/assets/projects/<slug>/`, named
   with a short abbreviation of the project and two digits in page order —
   `lotb-03.jpg` — as JPEG, 2000 px on the long edge or smaller. Each `<img>`
   gets an `alt`, and `loading="lazy"` unless it is the lead plate.
3. **The cover.** Crop the strongest image to 3:2, 1500 x 1000 or smaller, as
   `site/assets/covers/<slug>.jpg`. The frame holds the ratio: an image that
   does not match it is cropped to fit rather than letterboxed, so crop it
   yourself first.
4. **The row.** Copy one `<li class="work">` in `site/index.html` and fill in
   the title, one-sentence summary, the stack (place / kind of work) and both
   links. Update the abstract above the list if it counts the projects.
5. **Working files.** Models and the board-set PDF go in `source/<slug>/`.
   Git ignores them; back them up separately.
6. **Check.** `node tools/serve.mjs` and look at the front page and the new
   page; then `node tools/check.mjs`.

The portfolio's Academic Projects row links this site as a whole, so it does
not change when a project is added.

There is no stylesheet of its own: everything on these pages is the shared
standard.

## Deploying

A Render static site, `hark-academic`, deployed from `main` on every push:
no build step, publish directory `site`. The settings are recorded in
[`render.yaml`](render.yaml).

The old address, felipeharker.org/academic/, redirects here, path and all,
from `hark-site`, the portfolio's Render service.
