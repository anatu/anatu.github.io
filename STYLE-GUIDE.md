# Warm Archival Design System

This document defines the visual design system for the website. The aesthetic is ported from the report-kit style guide (`~/report-kit/STYLE.md`): **warm, woody, lamplit, archival** — a reading room, not a terminal. Dark walnut surfaces, cream ink, one amber accent, serif prose with typewriter-mono labels.

---

## Design Philosophy

A well-made document read by lamplight — legible, quiet, built to be kept. Never a landing page, never a pitch deck.

### Core Principles

1. **Content first** — Typography and whitespace do the work. No cards, shadows, or decorative elements.
2. **Amber is scarce** — It marks structure (the eyebrow tick, links) — not decoration.
3. **Everything warm and matte** — No cool grays, no neon, no glows. The only gradient is the near-invisible lamplight vignette on the page.
4. **Dark only** — `color-scheme: dark`; no light theme, no `prefers-color-scheme` switch.

---

## Color System

All values live as CSS custom properties in `styles.css` `:root`.

| Role | Value | CSS Variable |
|------|-------|--------------|
| Page base (dark walnut) | `#211a15` | `--bg` |
| Page edges / vignette floor | `#191410` | `--bg-deep` |
| Raised surfaces | `#2a2119` | `--bg-elevated` |
| Vignette center | `#2b221a` | `--bg-glow` |
| Border | `#3c3026` | `--border` |
| Border strong | `#4e3f30` | `--border-strong` |
| Body ink (cream) | `#e7dcc7` | `--text` |
| Headings / emphasis | `#f0e7d8` | `--text-strong` |
| Secondary ink | `#b3a68c` | `--text-muted` |
| Metadata / faint | `#8f8371` | `--text-faint` |
| Accent (lamplight amber) | `#e0a13e` | `--accent` |
| Accent hover | `#eab55f` | `--accent-hover` |
| Accent rules / ticks | `rgba(224,161,62,0.45)` | `--accent-dim` |

Never pure black `#000` or pure white `#fff`.

---

## Typography

### Font Stack

```css
--font-serif: "Newsreader", Georgia, "Times New Roman", serif;
--font-mono:  "IBM Plex Mono", ui-monospace, "SF Mono", Menlo, Consolas, monospace;
```

Two families, no sans. Loaded from Google Fonts via `<link>` in each page's `<head>`. **Newsreader** (serif) carries all prose and headings; display headings are light (300). **IBM Plex Mono** is the "archive plate" voice: nav, eyebrows, dates, tags, socials, footer — always small, usually uppercase, always letterspaced.

### Type Scale

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Hero title | 2.7rem | 300 | Serif |
| Section title | 1.95rem | 300 | Serif |
| Company/school name | 1.3125rem | 500 | Serif |
| Body / bio | 1.1875rem (19px) | 400 | Serif |
| Role/degree lines, descriptions | 0.9375rem | 400 | Serif |
| Meta (dates, tags, nav, socials) | 0.75rem | 400 | Mono, letterspaced |

Tracking tokens: `--track-plate: 0.14em` (plates, nav home), `--track-eyebrow: 0.3em` (eyebrows).

---

## Spacing & Layout

- **Content width:** 46rem max, centered
- **Section padding:** 4rem vertical (3rem on mobile)
- **Section dividers:** 1px solid `--border`
- **Page padding:** 1.5rem horizontal (1rem on mobile)

---

## Components

### Eyebrow
The house signature. Mono, amber, uppercase, `0.3em` tracking, with a 3.5rem amber tick rule below (`.eyebrow::after`). One per page, above the hero title.

### Navigation
Top bar: name on left (mono, uppercase, tracked), text links on right (mono, muted, amber on hover). No background, no border.

### Social Links
Mono uppercase text links in a row. Muted, amber on hover. No icons.

### Experience / Education Entries
Logo + name as header, then role/degree line, then a mono letterspaced meta line (dates, location). Logos sit on a parchment chip (`background: var(--text-strong)`, 3px radius, small padding) so dark marks stay legible on the walnut page.

### Links (in prose)
Amber, no underline; a 35%-alpha amber bottom border that strengthens on hover. Transitions 0.12s.

### Footer
Centered mono copyright, top border, faint ink.

---

## Interaction States

- **Links:** amber with soft amber rule; brighten on hover
- **No box-shadows, no transforms, no scale effects**
- **Transitions:** color/border-color only, 0.12s ease
- `::selection` is amber on dark

---

## Responsive

Single breakpoint at 640px: reduce page padding, hero to 2.1rem, section titles to 1.65rem, section padding to 3rem.

---

## Do's and Don'ts

### Do
- Let whitespace and the serif/mono contrast do the heavy lifting
- Keep amber scarce — structure and links only
- Keep everything warm and matte
- Use the tokens — no hardcoded colors, fonts, or spacing inline

### Don't
- Add shadows, gradients (beyond the vignette), or decorative borders
- Use cards or containers — content floats on the page
- Add icons when text suffices
- Introduce a third font family or any sans-serif
- Use pure `#000` / `#fff` or cool-toned grays
