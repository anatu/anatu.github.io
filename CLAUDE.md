# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

Personal portfolio website for Anand Natu (anatu.github.io). Static site — no build step, no JS, no framework. Just HTML + CSS served directly by GitHub Pages.

## Development

Open `index.html` in a browser to preview. No build, install, or serve commands needed.

To publish: commit and `git push origin main`. GitHub Pages deploys automatically.

## Architecture

- **`index.html`** — Single-page site. Sections: About (with socials), Experience, Education, Projects, Footer. Uses semantic HTML (`<nav>`, `<main>`, `<section>`, `<article>`).
- **`styles.css`** — All styling. Design tokens defined as CSS custom properties in `:root`. Dark mode via `prefers-color-scheme` media query. Responsive breakpoint at 640px.
- **`STYLE-GUIDE.md`** — Minimal design system reference. **Read this before making any visual changes.** Defines the color palette, typography, spacing, component patterns, and conventions.
- **`assets/logos/`** — Company/school logo PNGs used in Experience and Education sections.
- **`resume.pdf`** — Source material for site content. Excluded from git via `.gitignore`.

## Design System (Minimal)

Ultra-minimal, content-first design documented in `STYLE-GUIDE.md`. Key rules:

- **No shadows, no cards, no decorative elements.** Content stands on its own with whitespace and typography.
- **Narrow content column** — 660px max width for readability.
- **Neutral grayscale palette** — white background, near-black text, gray accents. No accent colors.
- **System fonts** — sans-serif for body, serif (Georgia) for section titles. No external font loading.
- **Section dividers** — simple 1px border-top between sections.
- **Links** — underlined, same color as text, fade on hover.
- **Dark mode** — inverted palette via `prefers-color-scheme`.

## Conventions

- Social links are plain text `<a>` tags, no icons.
- Company/school logos in Experience and Education sections are PNGs in `assets/logos/`.
- External links use `target="_blank" rel="noopener"`.
- No JavaScript. Smooth scrolling is CSS-only (`scroll-behavior: smooth`).
- No external font dependencies — uses system font stack.
