# Minimal Design System

This document defines the visual design system for the website. The aesthetic is ultra-minimal and content-first, inspired by personal sites like darioamodei.com.

---

## Design Philosophy

Content over decoration. The site should feel like a well-typeset document — clean, readable, with generous whitespace. No visual flourish that doesn't serve readability.

### Core Principles

1. **Content first** — Typography and whitespace do all the work. No cards, shadows, or decorative elements.
2. **Narrow column** — 660px max content width for comfortable reading.
3. **Neutral palette** — White background, near-black text, gray accents. Pure and simple.
4. **Restraint** — If in doubt, leave it out.

---

## Color System

### Light Theme

| Role | Value | CSS Variable |
|------|-------|--------------|
| Background | `#ffffff` | `--color-bg` |
| Text | `#1a1a1a` | `--color-text` |
| Text secondary | `#666666` | `--color-text-secondary` |
| Text muted | `#999999` | `--color-text-muted` |
| Border | `#e5e5e5` | `--color-border` |
| Link | `#1a1a1a` | `--color-link` |
| Link hover | `#666666` | `--color-link-hover` |

### Dark Theme

| Role | Value | CSS Variable |
|------|-------|--------------|
| Background | `#161616` | `--color-bg` |
| Text | `#e5e5e5` | `--color-text` |
| Text secondary | `#a0a0a0` | `--color-text-secondary` |
| Text muted | `#707070` | `--color-text-muted` |
| Border | `#2a2a2a` | `--color-border` |
| Link | `#e5e5e5` | `--color-link` |
| Link hover | `#a0a0a0` | `--color-link-hover` |

---

## Typography

### Font Stack

```css
--font-sans: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;
--font-serif: Georgia, 'Times New Roman', serif;
```

System fonts — no external font loading. Serif for section titles, sans-serif for everything else.

### Type Scale

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Hero title | 42px | 700 | Serif |
| Section title | 32px | 700 | Serif |
| Company/school name | 18px | 600 | Sans |
| Body / bio | 16px | 400 | Sans |
| Role descriptions, bullets | 14px | 400 | Sans |
| Meta (dates, locations, tags) | 13px | 400 | Sans |

---

## Spacing & Layout

- **Content width:** 660px max, centered
- **Section padding:** 64px vertical (48px on mobile)
- **Section dividers:** 1px solid `--color-border`
- **Between items:** 28–40px depending on content density
- **Page padding:** 24px horizontal (16px on mobile)

---

## Components

### Navigation
Simple top bar: name on left, 2–3 text links on right. No background, no shadow, no border. Font size 14px.

### Social Links
Plain text links in a row, separated by gap. No icons, no containers. Font size 14px, secondary color.

### Experience Entries
Company logo (28px) + company name as header, followed by role title, date/location meta line, and bullet points. No card wrapper.

### Education Entries
School logo (24px) + school name as header, followed by degree, year, and description. No card wrapper.

### Project Entries
Project name as a link + year on the same line, tech tags as a muted text line, then description. No card wrapper.

### Footer
Centered copyright text, separated by a top border. Font size 13px, muted color.

---

## Interaction States

- **Links:** Underlined by default, color fades on hover
- **No box-shadows, no transforms, no scale effects**
- **Transitions:** color only, 0.15s ease

---

## Responsive

Single breakpoint at 640px:
- Reduce page padding to 16px
- Reduce section title sizes
- Reduce section padding to 48px

---

## Do's and Don'ts

### Do
- Let whitespace do the heavy lifting
- Use weight and size for hierarchy
- Keep the color palette to 4–5 values
- Use system fonts
- Test in both light and dark mode

### Don't
- Add shadows, gradients, or decorative borders
- Use cards or containers — content floats on the page
- Add icons when text suffices
- Use accent colors — everything is grayscale
- Over-style interactive elements
