# hark_academic — agent guide

The academic projects site, https://academic.felipeharker.org/. Read
[`README.md`](README.md) first. It is one of four sites built to one
standard; the standard, the decision log and the roadmap for all four live in
[`hark_web`](https://github.com/felipeharker/hark_web) (`web/standards/`,
`planning/`).

## Rules

1. **`main` is live.** Render builds and deploys every push to `main`. Work on
   a branch; push or merge to `main` only when the user asks. Never change
   Render settings unless asked.
2. **The repository is public.** Every file here can be read by anyone, not
   only what is served. No secrets, no `.env`, no private notes.
3. **Privacy.** No street address, no one else's contact details, no client
   named and no work done for one shown.
4. **No links to private `github.com/felipeharker/…` repositories.** A
   visitor gets GitHub's 404. The four public ones — `hark_web`,
   `hark_academic`, `hark_birding`, `hark_resume` — may be linked.
5. **One stylesheet, and it is not here.** Every page links
   `https://felipeharker.org/standards/hark.css`, served by `hark_web`; never
   copy it. A rule only this site needs goes in `site/assets/site.css`,
   commented. A change to a shared component is a change to the standard, in
   `hark_web`. No inline `style` attributes, no CSS framework, no build step,
   no JavaScript where HTML will do. The one script is the standard's too:
   every page links `https://felipeharker.org/standards/hark.js` straight
   after its stylesheets, so it is set in the design — sans or serif — the
   reader chose on felipeharker.org's front page. There is no switch here;
   the front page is the only place to choose.
6. **Only `site/` is published.** Models, board PDFs and design sources go in
   `source/`, which git ignores. PDFs are out of the repository for now, and
   no page links one.
7. **Names.** Anything served is a URL, so it is lowercase kebab-case:
   `projects/<slug>.html`, `assets/projects/<slug>/<abbr>-NN.jpg`.
8. **Images.** Covers: 3:2, 1500 x 1000 or smaller, JPEG. Plates: JPEG, 2000 px
   on the long edge or smaller, named with the project's abbreviation and two
   digits (`lotb-03.jpg`). Every `<img>` has `alt`, and `loading="lazy"` below
   the first screen. **Never invent an image.**
9. **Links.** Within this site: relative. To another site in the family:
   absolute (`tools/site.mjs`), same tab. To anyone else: absolute,
   `target="_blank" rel="noopener noreferrer"`.
10. **Text.** Plain language; headings in Title Case, never numbered. Every
    page opens with the running head and ends with the colophon's site links,
    both Portfolio · Academic (`tools/site.mjs`, `NAV`), with no back link —
    this site's own link is `/`, with `aria-current="page"`; the standards link is
    `https://felipeharker.org/standards/`.
11. **Third-party material** never goes in the repository; it stays in
    `source/`. Credit a source in the page text when a project relies on it.
12. **Keep the docs true.** A change to how something works updates the
    README in the same commit. A decision goes in `hark_web`'s
    `planning/decisions.md`. The family's addresses are in `tools/site.mjs`
    here and in every other `hark_` repository: change them in all four.

## Before a commit

1. `node tools/check.mjs` passes.
2. `node tools/serve.mjs`, and open every page you touched at desktop width
   and at 390 px.

Commit messages end with the attribution line the session gives, for example
`Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>`.
