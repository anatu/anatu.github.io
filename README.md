# anatu.github.io

Personal portfolio website for Anand Natu -- Sr. Product Manager specializing in AI/ML. Sections: About (name + socials), Experience (Reddit, Meta, Amazon, Keystone Strategy), Education (Stanford M.S. Robotics, McGill B.Eng.). Also hosts a visualization hub at `/viz/` for publishing standalone charts and analyses.

**Live site:** [anatu.github.io](https://anatu.github.io) -- viz hub at [anatu.github.io/viz/](https://anatu.github.io/viz/)

## How It's Built

- **Static site** -- single `index.html` page with a separate `styles.css` stylesheet. The main page has no JavaScript; the viz hub uses a small inline script to fetch its manifest.
- **Minimal design** -- content-first, ultra-minimal style. White background, system fonts, 660px narrow column, no decorative elements. Full spec in `STYLE-GUIDE.md`.
- **Dark mode** -- automatic via `prefers-color-scheme` media query, overriding CSS custom properties.
- **Responsive** -- single breakpoint at 640px.
- **Typography** -- system font stack (sans-serif body, Georgia serif for titles). No external font loading.
- **Hosting** -- GitHub Pages, deployed automatically on push to `main`. `.nojekyll` disables Jekyll preprocessing so paths starting with `_` (e.g. `viz/_template.html`) are served verbatim.

## Development

Open `index.html` in a browser to preview locally. To publish, commit and push to `main`.

## Viz Hub

The hub at `/viz/` reads `viz/manifest.json` at runtime and renders one card per registered visualization. To add a viz:

1. Copy `viz/_template.html` to `viz/pages/<slug>.html` (single-file) or `viz/pages/<slug>/index.html` (bundled with sibling `figures/`, `data/`, `sql/`, `scripts/`).
2. Append an entry to `viz/manifest.json`: `{ title, description, file, version, lastModified, tags }`. The `file` path is relative to `viz/`.
3. Commit and push. The hub picks it up on next load.

## File Structure

```
index.html          -- Main single-page site (About, Experience, Education)
styles.css          -- All styling and design tokens
STYLE-GUIDE.md      -- Minimal design system reference
CLAUDE.md           -- Claude Code project instructions
assets/logos/       -- Company and school logo PNGs
viz/
  index.html        -- Viz hub landing page
  manifest.json     -- Registry of published vizzes
  _template.html    -- Copy-and-edit template for new vizzes
  pages/            -- Published viz HTML files (created on first viz)
.nojekyll           -- Disable Jekyll preprocessing on GitHub Pages
```
