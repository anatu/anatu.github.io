# anatu.github.io

Personal portfolio website for Anand Natu -- Sr. Product Manager specializing in AI/ML. Features professional experience (Reddit, Meta, Amazon, Keystone Strategy), education (Stanford M.S. Robotics, McGill B.Eng.), and a showcase of public GitHub projects spanning robotics, deep learning, reinforcement learning, and computer vision.

**Live site:** [anatu.github.io](https://anatu.github.io)

## How It's Built

- **Static site** -- single `index.html` page with a separate `styles.css` stylesheet. No JavaScript, no build step, no framework.
- **Minimal design** -- content-first, ultra-minimal style. White background, system fonts, 660px narrow column, no decorative elements. Full spec in `STYLE-GUIDE.md`.
- **Dark mode** -- automatic via `prefers-color-scheme` media query, overriding CSS custom properties.
- **Responsive** -- single breakpoint at 640px.
- **Typography** -- system font stack (sans-serif body, Georgia serif for titles). No external font loading.
- **Hosting** -- GitHub Pages, deployed automatically on push to `main`.

## Development

Open `index.html` in a browser to preview locally. To publish, commit and push to `main`.

## File Structure

```
index.html          -- Single-page site (About, Experience, Education, Projects)
styles.css          -- All styling and design tokens
STYLE-GUIDE.md      -- Minimal design system reference
CLAUDE.md           -- Claude Code project instructions
assets/logos/       -- Company and school logo PNGs
```
