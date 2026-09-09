# junchenglu.github.io

Personal academic homepage. Plain HTML + one CSS file, no build step, no dependencies.

Layout follows [jonbarron.info](https://jonbarron.info/) — one dense page, ~820px column,
thumbnail-plus-text rows — rebuilt with CSS grid instead of nested tables, plus dark mode,
a responsive mobile layout, and the sections a PhD applicant needs (projects, experience,
education, methods) that the original doesn't have.

```
index.html          the whole page — all content lives here
stylesheet.css      all styling; colours are CSS variables at the top
favicon.svg
images/profile.jpg  ← replace this placeholder with your headshot
data/               CV PDF
```

## Before you publish

1. **`images/profile.jpg`** — currently a grey placeholder. Drop in a square headshot
   (600×600 or larger; it gets cropped to a circle).
2. **Scholar and LinkedIn URLs** — `index.html` has two `REPLACE_ME` placeholders in the
   link row. Fix them, or delete the lines you don't want.
3. **Figures** — the four schematics live in `figures/` as standalone SVG files, referenced
   by `<img>`. Replace a file in place and the page picks it up; no HTML edit needed. They
   illustrate each entry's actual method but are **not plots of real data** — swap in real
   figures when you have them.

   Because an externally-referenced SVG cannot read the page's CSS variables, each file
   carries its own palette plus a `prefers-color-scheme` block. Delete that block and the
   figure stops adapting to dark mode.

   Thumbnails are 1:1 (160×160 desktop). A `<div class="thumb">` stacks its children in one
   square; add `class="on-hover"` to a second image and it cross-fades in over 0.35s while
   the pointer is anywhere on the row:

   ```html
   <div class="thumb">
     <img src="figures/before.svg" alt="what the figure shows" />
     <img class="on-hover" src="figures/after.svg" alt="" aria-hidden="true" />
   </div>
   ```

   Touch devices have no hover and only ever see the base layer, so never put essential
   information in the hover layer. See 编辑指南.md §6 for the full pattern.

## Editing

Everything is one file. To add a publication, copy an existing `<article class="item">`
block and edit the text. `class="item is-highlighted"` gives a row the tinted background
(Barron's convention for highlighting selected work) — keep it to one or two rows.

Colours: edit the CSS variables in `:root` at the top of `stylesheet.css`. The dark-mode
values are in the two blocks below it; change all three if you change a colour's role.

## Preview locally

```bash
python3 -m http.server 8777
```

Then open <http://localhost:8777>. There's no build step — edit, save, reload.

## Deploying to GitHub Pages

This is a static site, so it needs no Actions workflow — GitHub Pages can serve the
repository root directly.

To publish it at `junchenglu218.github.io`, push these files to the root of the
`JunchengLu218.github.io` repository, then in **Settings → Pages** set
**Source: Deploy from a branch**, **Branch: `main` / `(root)`**.

Note that the existing repo is currently set up to deploy via GitHub Actions (the al-folio
workflow). Switching the Pages source to "Deploy from a branch" replaces that; the old
workflow files can be deleted.

## Adding a blog later

There's no blog here by design — it's one page. If you want one later, the cheapest route
that keeps this page untouched is a `notes/` directory of hand-written HTML pages, linked
from a new section. If you want real post tooling, that's the point at which a static site
generator earns its complexity.
