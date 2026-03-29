# anatu.github.io

Personal portfolio website for Anand Natu -- Sr. Product Manager specializing in AI/ML. Features professional experience (Reddit, Meta, Amazon, Keystone Strategy), education (Stanford M.S. Robotics, McGill B.Eng.), and a showcase of public GitHub projects spanning robotics, deep learning, reinforcement learning, and computer vision.

**Live site:** [anatu.github.io](https://anatu.github.io)

## How It's Built

- **Static site** -- single `index.html` page with a separate `styles.css` stylesheet. No JavaScript, no build step, no framework.
- **Neumorphism design system** -- soft UI style with dual box-shadows, warm color palette (`#efe7dd` base, `#b45309` accent), and CSS custom properties for all design tokens. Full spec in `STYLE-GUIDE.md`.
- **Dark mode** -- automatic via `prefers-color-scheme` media query, overriding the same CSS custom properties.
- **Responsive** -- single breakpoint at 768px.
- **Typography** -- [Nunito Sans](https://fonts.google.com/specimen/Nunito+Sans) (400/600/700) via Google Fonts.
- **Icons** -- inline SVGs for social links (LinkedIn, Substack, GitHub).
- **Hosting** -- GitHub Pages, deployed automatically on push to `main`.

## Development

Open `index.html` in a browser to preview locally. To publish, commit and push to `main`.

## File Structure

```
index.html          -- Single-page site (About, Experience, Education, Projects)
styles.css          -- All styling and design tokens
STYLE-GUIDE.md      -- Neumorphism design system reference
assets/logos/       -- Company and school logo PNGs
```
