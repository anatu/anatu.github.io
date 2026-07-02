# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Personal portfolio website for Anand Natu (anatu.github.io). Static site — no build step, no JS, no framework. Just HTML + CSS served directly by GitHub Pages.

## Development

Open `index.html` in a browser to preview. No build, install, or serve commands needed.

To publish: commit and `git push origin main`. GitHub Pages deploys automatically.

## Architecture

- **`index.html`** — Main single-page site. Sections: About (name + socials), Experience, Education, Footer. Uses semantic HTML (`<nav>`, `<main>`, `<section>`, `<article>`).
- **`styles.css`** — All styling for the main page. Design tokens defined as CSS custom properties in `:root`. Dark-only theme (`color-scheme: dark`). Responsive breakpoint at 640px.
- **`STYLE-GUIDE.md`** — Warm archival design system reference, ported from `~/report-kit/STYLE.md`. **Read this before making any visual changes.** Defines the color palette, typography, spacing, component patterns, and conventions.
- **`assets/logos/`** — Company/school logo PNGs used in Experience and Education sections.
- **`resume.pdf`** — Source material for site content. Excluded from git via `.gitignore`.
- **`.nojekyll`** — Empty marker disabling Jekyll preprocessing on GitHub Pages.

## Design System (Warm Archival)

Warm, woody, lamplit, archival — ported from report-kit and documented in `STYLE-GUIDE.md`. Key rules:

- **No shadows, no cards, no decorative elements.** Content stands on its own with whitespace and typography.
- **Narrow content column** — 46rem max width for readability.
- **Warm palette** — dark walnut background (`#211a15`) with a lamplight vignette, cream ink, one amber accent (`#e0a13e`). Never pure `#000`/`#fff`, never cool grays.
- **Two fonts, no sans** — Newsreader (serif) for prose and headings (light-weight display), IBM Plex Mono for nav/meta/eyebrows (small, uppercase, letterspaced). Loaded from Google Fonts.
- **Section dividers** — simple 1px border-top between sections.
- **Links** — amber, soft amber bottom rule, brighten on hover.
- **Dark only** — no light theme, no `prefers-color-scheme` switch.
- **Eyebrow** — mono amber label with a short amber tick rule; the house signature, one per page.

## Conventions

- Social links are plain text `<a>` tags, no icons.
- Company/school logos in Experience and Education sections are PNGs in `assets/logos/`.
- External links use `target="_blank" rel="noopener"`.
- No JavaScript. Smooth scrolling is CSS-only (`scroll-behavior: smooth`).
- Fonts load from Google Fonts (Newsreader + IBM Plex Mono) via `<link>` in the page `<head>`.
- Logos sit on a parchment chip (`background: var(--text-strong)`) so dark marks stay legible on the walnut page.
