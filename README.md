# anatu.github.io

Personal portfolio website for Anand Natu -- Sr. Product Manager specializing in AI/ML. Sections: About (name + socials + bio), Experience (Reddit, Meta, Amazon, Keystone Strategy), Education (Stanford M.S. Robotics, McGill B.Eng.).

**Live site:** [anatu.github.io](https://anatu.github.io)

## How It's Built

- **Static site** -- single `index.html` page with a separate `styles.css` stylesheet. The main page has no JavaScript.
- **Minimal design** -- content-first, ultra-minimal style. White background, system fonts, 660px narrow column, no decorative elements. Full spec in `STYLE-GUIDE.md`.
- **Dark mode** -- automatic via `prefers-color-scheme` media query, overriding CSS custom properties.
- **Responsive** -- single breakpoint at 640px.
- **Typography** -- system font stack (sans-serif body, Georgia serif for titles). No external font loading.
- **Hosting** -- GitHub Pages, deployed automatically on push to `main`. `.nojekyll` disables Jekyll preprocessing.

## Development

Open `index.html` in a browser to preview locally. To publish, commit and push to `main`.

## File Structure

```
index.html          -- Main single-page site (About, Experience, Education)
styles.css          -- All styling and design tokens
STYLE-GUIDE.md      -- Minimal design system reference
CLAUDE.md           -- Claude Code project instructions
assets/logos/       -- Company and school logo PNGs
.nojekyll           -- Disable Jekyll preprocessing on GitHub Pages
```
