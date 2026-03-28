# Neumorphism Style Guide

This document defines the visual design system for the website. Every UI element should conform to the neumorphic (soft UI) aesthetic described below.

---

## Table of Contents

1. [Design Philosophy](#design-philosophy)
2. [Color System](#color-system)
3. [Shadow System](#shadow-system)
4. [Border Radius](#border-radius)
5. [Typography](#typography)
6. [Spacing & Layout](#spacing--layout)
7. [Components](#components)
8. [Interaction States](#interaction-states)
9. [Surface Variations](#surface-variations)
10. [Dark Mode](#dark-mode)
11. [Accessibility](#accessibility)
12. [Do's and Don'ts](#dos-and-donts)
13. [CSS Custom Properties Reference](#css-custom-properties-reference)
14. [Tools & Resources](#tools--resources)

---

## Design Philosophy

Neumorphism (neomorphism) sits between flat design and skeuomorphism. Elements appear **extruded from** or **pressed into** the background surface, as if molded from the same material. The illusion is created through carefully paired light and dark shadows simulating a single, consistent light source.

### Core Principles

1. **Same-material illusion** — Element backgrounds must exactly match their parent background. The element and surface are visually "one piece."
2. **Consistent light source** — All shadows across the entire interface assume light arrives from the **top-left**. This must never vary.
3. **Softness** — All edges are rounded, all shadows are diffuse, all transitions are smooth.
4. **Restraint** — Neumorphism works best as an accent. Apply it to key interactive elements and cards, not to every pixel on the page.
5. **Minimalism** — Embrace generous whitespace. Neumorphic elements need breathing room because shadows extend beyond the element box.

---

## Color System

### Light Theme (Primary)

| Role | Value | CSS Variable | Notes |
|------|-------|--------------|-------|
| Base background | `#e0e5ec` | `--color-bg` | Applied to `body` and all neumorphic element backgrounds |
| Dark shadow | `#a3b1c6` | `--color-shadow-dark` | Bottom-right shadow (away from light) |
| Light shadow | `#ffffff` | `--color-shadow-light` | Top-left shadow (toward light) |
| Dark shadow (soft) | `rgba(163, 177, 198, 0.6)` | `--color-shadow-dark-soft` | For subtler / smaller elements |
| Light shadow (soft) | `rgba(255, 255, 255, 0.7)` | `--color-shadow-light-soft` | For subtler / smaller elements |
| Text primary | `#2d3436` | `--color-text-primary` | Headings, body copy |
| Text secondary | `#636e72` | `--color-text-secondary` | Captions, metadata |
| Text muted | `#95a5a6` | `--color-text-muted` | Placeholders, disabled text |
| Accent | `#2D4CC8` | `--color-accent` | Links, active states, CTA highlights |
| Accent hover | `#1a3a9e` | `--color-accent-hover` | Darker accent for hover |
| Success | `#27ae60` | `--color-success` | Positive feedback |
| Warning | `#f39c12` | `--color-warning` | Caution states |
| Danger | `#e74c3c` | `--color-danger` | Error states |

### Critical Color Rules

- **Element background = parent background.** If they diverge even slightly, the illusion breaks.
- **Never use pure white (`#fff`) or pure black (`#000`) as a base.** Mid-range grays and soft pastels are ideal.
- The dark shadow color is the base darkened by ~15–20%. The light shadow is pushed toward white.
- Accent colors should be used sparingly — for text highlights, icons, active indicators — not for element backgrounds.

---

## Shadow System

Shadows are the defining feature of neumorphism. Every neumorphic element uses **two box-shadows**: one dark (cast shadow, bottom-right) and one light (reflected light, top-left).

### Shadow Scale

| Level | Offset | Blur | Use Case |
|-------|--------|------|----------|
| `xs` | `2px` | `5px` | Checkboxes, radio buttons, small icons |
| `sm` | `3px` | `7px` | Tags, badges, small buttons |
| `md` | `5px` | `10px` | Standard buttons, input fields |
| `lg` | `8px` | `16px` | Cards, panels |
| `xl` | `12px` | `24px` | Hero sections, modal dialogs |

### Raised (Extruded) Element — Default

The element protrudes from the surface.

```css
/* xs */
box-shadow: 2px 2px 5px var(--color-shadow-dark-soft),
           -2px -2px 5px var(--color-shadow-light-soft);

/* sm */
box-shadow: 3px 3px 7px var(--color-shadow-dark),
           -3px -3px 7px var(--color-shadow-light);

/* md */
box-shadow: 5px 5px 10px var(--color-shadow-dark),
           -5px -5px 10px var(--color-shadow-light);

/* lg */
box-shadow: 8px 8px 16px var(--color-shadow-dark),
           -8px -8px 16px var(--color-shadow-light);

/* xl */
box-shadow: 12px 12px 24px var(--color-shadow-dark),
           -12px -12px 24px var(--color-shadow-light);
```

### Pressed (Inset) Element

The element is recessed into the surface. Used for active buttons, text inputs, and toggled-on states.

```css
/* sm */
box-shadow: inset 3px 3px 7px var(--color-shadow-dark),
            inset -3px -3px 7px var(--color-shadow-light);

/* md */
box-shadow: inset 5px 5px 10px var(--color-shadow-dark),
            inset -5px -5px 10px var(--color-shadow-light);

/* lg */
box-shadow: inset 8px 8px 16px var(--color-shadow-dark),
            inset -8px -8px 16px var(--color-shadow-light);
```

### Flat (No Shadow)

Used for transitions and for elements that should blend entirely into the background.

```css
box-shadow: none;
```

### Shadow Transition

All shadow changes should animate smoothly:

```css
transition: box-shadow 0.25s ease, background 0.25s ease;
```

---

## Border Radius

Rounded edges are a defining quality of neumorphism. Sharp corners break the soft aesthetic.

| Token | Value | Use Case |
|-------|-------|----------|
| `--radius-sm` | `8px` | Small elements: tags, badges, checkboxes |
| `--radius-md` | `12px` | Buttons, inputs |
| `--radius-lg` | `16px` | Cards, panels |
| `--radius-xl` | `24px` | Large cards, hero sections |
| `--radius-pill` | `50px` | Pill buttons, toggle tracks |
| `--radius-circle` | `50%` | Avatars, circular icon buttons |

---

## Typography

### Font Stack

```css
--font-primary: 'Nunito Sans', 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
--font-mono: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace;
```

**Nunito Sans** is the recommended primary font — its rounded letterforms complement the soft neumorphic aesthetic. Load weights 400 (regular), 600 (semi-bold), and 700 (bold) from Google Fonts.

### Type Scale

| Token | Size | Weight | Line Height | Use |
|-------|------|--------|-------------|-----|
| `--text-display` | `48px` | 700 | 1.1 | Hero headings |
| `--text-h1` | `36px` | 700 | 1.2 | Page titles |
| `--text-h2` | `28px` | 700 | 1.3 | Section headings |
| `--text-h3` | `22px` | 600 | 1.3 | Subsection headings |
| `--text-h4` | `18px` | 600 | 1.4 | Card titles |
| `--text-body` | `16px` | 400 | 1.6 | Body copy (base) |
| `--text-sm` | `14px` | 400 | 1.5 | Captions, secondary info |
| `--text-xs` | `12px` | 400 | 1.4 | Labels, fine print |

### Text Styling Rules

- Use `--color-text-primary` for headings and body copy.
- Use `--color-text-secondary` for supporting text.
- Use font weight variation (not color variation) as the primary tool for hierarchy, since the muted palette limits color-based hierarchy.
- Avoid text-shadow on body text — it conflicts with the surface illusion.
- Links use `--color-accent` with no underline by default; underline on hover.

---

## Spacing & Layout

### Spacing Scale

Based on a 4px grid:

| Token | Value |
|-------|-------|
| `--space-1` | `4px` |
| `--space-2` | `8px` |
| `--space-3` | `12px` |
| `--space-4` | `16px` |
| `--space-5` | `20px` |
| `--space-6` | `24px` |
| `--space-8` | `32px` |
| `--space-10` | `40px` |
| `--space-12` | `48px` |
| `--space-16` | `64px` |
| `--space-20` | `80px` |

### Layout Rules

- **Generous margins between neumorphic elements.** Shadows extend beyond the element box, so adjacent elements need at least `--space-8` (32px) between them to avoid shadow overlap.
- **Internal padding** should be at least `--space-5` (20px) for cards and panels.
- **Max content width:** `1200px`, centered.
- **Grid gap:** Use `--space-8` (32px) minimum between neumorphic grid items.
- **Section vertical spacing:** `--space-16` (64px) to `--space-20` (80px) between major page sections.
- Prefer CSS Grid or Flexbox for layout. Avoid float-based layouts.

---

## Components

### Button

```css
.neu-btn {
  padding: 14px 28px;
  border: none;
  border-radius: var(--radius-md);       /* 12px */
  background: var(--color-bg);           /* #e0e5ec */
  color: var(--color-text-primary);
  font-family: var(--font-primary);
  font-size: var(--text-body);           /* 16px */
  font-weight: 600;
  cursor: pointer;
  box-shadow: 5px 5px 10px var(--color-shadow-dark),
             -5px -5px 10px var(--color-shadow-light);
  transition: box-shadow 0.25s ease;
}

.neu-btn:hover {
  box-shadow: 3px 3px 6px var(--color-shadow-dark),
             -3px -3px 6px var(--color-shadow-light);
}

.neu-btn:active {
  box-shadow: inset 3px 3px 7px var(--color-shadow-dark),
              inset -3px -3px 7px var(--color-shadow-light);
}
```

**Accent button:** Same as above, but with `color: var(--color-accent)` and optionally a subtle left-border accent:
```css
.neu-btn--accent {
  color: var(--color-accent);
  border-left: 3px solid var(--color-accent);
}
```

### Card

```css
.neu-card {
  padding: var(--space-6);               /* 24px */
  border-radius: var(--radius-lg);       /* 16px */
  background: var(--color-bg);
  box-shadow: 8px 8px 16px var(--color-shadow-dark),
             -8px -8px 16px var(--color-shadow-light);
}

.neu-card__title {
  font-size: var(--text-h4);
  font-weight: 600;
  margin-bottom: var(--space-3);
}

.neu-card__body {
  font-size: var(--text-body);
  color: var(--color-text-secondary);
  line-height: 1.6;
}
```

### Text Input

Inputs are **inset** by default (recessed into the surface), contrasting with raised buttons and cards.

```css
.neu-input {
  width: 100%;
  padding: 12px 16px;
  border: none;
  border-radius: var(--radius-md);       /* 12px */
  background: var(--color-bg);
  color: var(--color-text-primary);
  font-family: var(--font-primary);
  font-size: var(--text-body);
  box-shadow: inset 5px 5px 10px var(--color-shadow-dark),
              inset -5px -5px 10px var(--color-shadow-light);
  outline: none;
  transition: box-shadow 0.25s ease;
}

.neu-input::placeholder {
  color: var(--color-text-muted);
}

.neu-input:focus {
  box-shadow: inset 3px 3px 6px var(--color-shadow-dark),
              inset -3px -3px 6px var(--color-shadow-light);
}
```

### Toggle Switch

```css
.neu-toggle {
  width: 56px;
  height: 28px;
  border-radius: var(--radius-pill);
  background: var(--color-bg);
  box-shadow: inset 5px 5px 10px var(--color-shadow-dark),
              inset -5px -5px 10px var(--color-shadow-light);
  position: relative;
  cursor: pointer;
  transition: box-shadow 0.25s ease;
}

.neu-toggle__knob {
  width: 22px;
  height: 22px;
  border-radius: var(--radius-circle);
  background: var(--color-bg);
  box-shadow: 2px 2px 5px var(--color-shadow-dark),
             -2px -2px 5px var(--color-shadow-light);
  position: absolute;
  top: 3px;
  left: 3px;
  transition: transform 0.25s ease;
}

/* Active state */
.neu-toggle--active .neu-toggle__knob {
  transform: translateX(28px);
}
```

### Checkbox

```css
.neu-checkbox {
  width: 24px;
  height: 24px;
  border-radius: var(--radius-sm);       /* 8px */
  background: var(--color-bg);
  box-shadow: 3px 3px 6px var(--color-shadow-dark),
             -3px -3px 6px var(--color-shadow-light);
  cursor: pointer;
  transition: box-shadow 0.25s ease;
}

.neu-checkbox--checked {
  box-shadow: inset 3px 3px 6px var(--color-shadow-dark),
              inset -3px -3px 6px var(--color-shadow-light);
}
```

### Progress Bar

```css
.neu-progress {
  height: 12px;
  border-radius: var(--radius-pill);
  background: var(--color-bg);
  box-shadow: inset 3px 3px 6px var(--color-shadow-dark),
              inset -3px -3px 6px var(--color-shadow-light);
  overflow: hidden;
}

.neu-progress__fill {
  height: 100%;
  border-radius: var(--radius-pill);
  background: var(--color-accent);
  transition: width 0.4s ease;
}
```

### Navigation Bar

```css
.neu-nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--space-4) var(--space-8);
  background: var(--color-bg);
  box-shadow: 0 4px 12px var(--color-shadow-dark-soft);
}

.neu-nav__link {
  padding: 8px 16px;
  border-radius: var(--radius-md);
  color: var(--color-text-secondary);
  font-weight: 600;
  text-decoration: none;
  transition: box-shadow 0.25s ease, color 0.25s ease;
}

.neu-nav__link:hover {
  color: var(--color-text-primary);
  box-shadow: 3px 3px 6px var(--color-shadow-dark),
             -3px -3px 6px var(--color-shadow-light);
}

.neu-nav__link--active {
  color: var(--color-accent);
  box-shadow: inset 3px 3px 6px var(--color-shadow-dark),
              inset -3px -3px 6px var(--color-shadow-light);
}
```

### Icon Button (Circular)

```css
.neu-icon-btn {
  width: 48px;
  height: 48px;
  border: none;
  border-radius: var(--radius-circle);
  background: var(--color-bg);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  box-shadow: 5px 5px 10px var(--color-shadow-dark),
             -5px -5px 10px var(--color-shadow-light);
  transition: box-shadow 0.25s ease;
}

.neu-icon-btn:hover {
  box-shadow: 3px 3px 6px var(--color-shadow-dark),
             -3px -3px 6px var(--color-shadow-light);
}

.neu-icon-btn:active {
  box-shadow: inset 3px 3px 7px var(--color-shadow-dark),
              inset -3px -3px 7px var(--color-shadow-light);
}
```

---

## Interaction States

Neumorphism maps physical metaphors to interaction states:

| State | Shadow Style | Visual Metaphor |
|-------|-------------|-----------------|
| **Default** | Raised (`md` or `lg`) | Element sits on top of the surface |
| **Hover** | Raised but reduced (smaller offset/blur) | Element settles slightly, as if lightly touched |
| **Active / Pressed** | Inset | Element is pushed into the surface |
| **Focus** | Inset (lighter) + accent ring | Element is recessed with a colored highlight |
| **Disabled** | Flat (no shadow) + reduced opacity | Element merges back into the surface |

### Focus Ring (Accessibility)

Since `outline: none` is used on neumorphic elements, provide an accessible focus indicator:

```css
.neu-focusable:focus-visible {
  box-shadow: inset 3px 3px 6px var(--color-shadow-dark),
              inset -3px -3px 6px var(--color-shadow-light),
              0 0 0 3px var(--color-accent);
}
```

### Disabled State

```css
.neu-disabled {
  box-shadow: none;
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}
```

---

## Surface Variations

Beyond flat raised/pressed states, neumorphism supports convex and concave surface illusions via gradients.

### Convex (Curves Outward)

The surface bulges toward the viewer. Gradient lighter portion aligns with the light shadow.

```css
.neu-convex {
  background: linear-gradient(145deg, #f0f0f0, #cacaca);
  box-shadow: 8px 8px 16px var(--color-shadow-dark),
             -8px -8px 16px var(--color-shadow-light);
}
```

### Concave (Curves Inward)

The surface dips away from the viewer. Gradient darker portion aligns with the light shadow.

```css
.neu-concave {
  background: linear-gradient(145deg, #cacaca, #f0f0f0);
  box-shadow: 8px 8px 16px var(--color-shadow-dark),
             -8px -8px 16px var(--color-shadow-light);
}
```

### When to Use

- **Convex:** Buttons, icon containers — things that should feel "pushable."
- **Concave:** Display areas, image wells — things that feel like they hold content.
- **Flat raised:** Cards, panels — neutral elevated surfaces.
- **Flat inset:** Inputs, text areas — surfaces that receive content.

---

## Dark Mode

### Dark Theme Palette

| Role | Value | CSS Variable |
|------|-------|--------------|
| Base background | `#2d3436` | `--color-bg` |
| Dark shadow | `#1a1f21` | `--color-shadow-dark` |
| Light shadow | `#3d4a4d` | `--color-shadow-light` |
| Dark shadow (soft) | `rgba(26, 31, 33, 0.6)` | `--color-shadow-dark-soft` |
| Light shadow (soft) | `rgba(61, 74, 77, 0.5)` | `--color-shadow-light-soft` |
| Text primary | `#dfe6e9` | `--color-text-primary` |
| Text secondary | `#b2bec3` | `--color-text-secondary` |
| Text muted | `#636e72` | `--color-text-muted` |
| Accent | `#74b9ff` | `--color-accent` |

### Implementation

Use `prefers-color-scheme` and/or a manual toggle:

```css
@media (prefers-color-scheme: dark) {
  :root {
    --color-bg: #2d3436;
    --color-shadow-dark: #1a1f21;
    --color-shadow-light: #3d4a4d;
    --color-shadow-dark-soft: rgba(26, 31, 33, 0.6);
    --color-shadow-light-soft: rgba(61, 74, 77, 0.5);
    --color-text-primary: #dfe6e9;
    --color-text-secondary: #b2bec3;
    --color-text-muted: #636e72;
    --color-accent: #74b9ff;
  }
}
```

The same shadow CSS applies in both themes — only the custom property values change.

---

## Accessibility

Neumorphism's biggest weakness is accessibility. The following mitigations are **required**:

### Contrast

- All text must meet **WCAG 2.1 AA** minimum contrast ratios: 4.5:1 for normal text, 3:1 for large text.
- Test text colors against `--color-bg` with a contrast checker. The palette above (`#2d3436` on `#e0e5ec`) yields ~10:1 contrast ratio.

### Interactive Element Identification

- Always pair neumorphic buttons with clear text labels and/or icons. Do not rely solely on shadow differences to indicate interactivity.
- Use `cursor: pointer` on all clickable elements.
- Provide visible `:focus-visible` indicators (see [Focus Ring](#focus-ring-accessibility) above).

### Screen Reader Support

- Use semantic HTML elements (`<button>`, `<input>`, `<nav>`, `<main>`, `<section>`).
- Add `aria-label` attributes where visual context is lost without shadows (e.g., icon-only buttons).
- Use `aria-pressed` for toggle buttons.
- Ensure form inputs have associated `<label>` elements.

### Motion

- Wrap transitions in `prefers-reduced-motion` checks:

```css
@media (prefers-reduced-motion: reduce) {
  * {
    transition-duration: 0.01ms !important;
  }
}
```

### Supplementary Visual Cues

When neumorphic shadows alone are insufficient to convey state:
- Add subtle borders (`1px solid rgba(0,0,0,0.05)`) to element edges for definition.
- Use accent color highlights for active/selected states.
- Add icons (checkmarks, arrows) to reinforce meaning.

---

## Do's and Don'ts

### Do

- Use neumorphism **selectively** — on cards, buttons, nav elements, and key interactive components.
- Maintain a **single, consistent light source** (top-left) across the entire page.
- Match element background colors **exactly** to their parent surface.
- Provide **generous spacing** between neumorphic elements to prevent shadow overlap.
- Use **font weight and size** (not just color) to create text hierarchy.
- Ensure every neumorphic element **works without shadows** (graceful degradation).
- Test on multiple screens — subtle shadows can vanish on low-contrast displays.
- Animate shadow changes smoothly (`transition: box-shadow 0.25s ease`).
- Pair neumorphism with clear, readable typography.

### Don't

- Don't apply neumorphic shadows to **every element** — the interface becomes a featureless blob.
- Don't use **pure white** (`#fff`) or **pure black** (`#000`) as base background colors.
- Don't rely **solely on shadows** to distinguish interactive from static elements.
- Don't use neumorphism on **very small elements** (under 20px) — the shadow detail is lost.
- Don't mix neumorphism with **hard drop shadows** or **solid borders** — they break the soft aesthetic.
- Don't place neumorphic elements on backgrounds that differ in color from the element.
- Don't sacrifice **accessibility** for aesthetics. If a neumorphic treatment makes something harder to use, simplify it.
- Don't over-nest neumorphic containers (raised card inside raised card) — the illusion loses coherence.

---

## CSS Custom Properties Reference

Complete set of custom properties to define in `:root`:

```css
:root {
  /* Colors */
  --color-bg: #e0e5ec;
  --color-shadow-dark: #a3b1c6;
  --color-shadow-light: #ffffff;
  --color-shadow-dark-soft: rgba(163, 177, 198, 0.6);
  --color-shadow-light-soft: rgba(255, 255, 255, 0.7);
  --color-text-primary: #2d3436;
  --color-text-secondary: #636e72;
  --color-text-muted: #95a5a6;
  --color-accent: #2D4CC8;
  --color-accent-hover: #1a3a9e;
  --color-success: #27ae60;
  --color-warning: #f39c12;
  --color-danger: #e74c3c;

  /* Radii */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --radius-pill: 50px;
  --radius-circle: 50%;

  /* Typography */
  --font-primary: 'Nunito Sans', 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-mono: 'JetBrains Mono', 'Fira Code', 'SF Mono', monospace;
  --text-display: 48px;
  --text-h1: 36px;
  --text-h2: 28px;
  --text-h3: 22px;
  --text-h4: 18px;
  --text-body: 16px;
  --text-sm: 14px;
  --text-xs: 12px;

  /* Spacing */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
  --space-20: 80px;

  /* Shadows (precomposed) */
  --shadow-raised-sm: 3px 3px 7px var(--color-shadow-dark), -3px -3px 7px var(--color-shadow-light);
  --shadow-raised-md: 5px 5px 10px var(--color-shadow-dark), -5px -5px 10px var(--color-shadow-light);
  --shadow-raised-lg: 8px 8px 16px var(--color-shadow-dark), -8px -8px 16px var(--color-shadow-light);
  --shadow-raised-xl: 12px 12px 24px var(--color-shadow-dark), -12px -12px 24px var(--color-shadow-light);
  --shadow-inset-sm: inset 3px 3px 7px var(--color-shadow-dark), inset -3px -3px 7px var(--color-shadow-light);
  --shadow-inset-md: inset 5px 5px 10px var(--color-shadow-dark), inset -5px -5px 10px var(--color-shadow-light);
  --shadow-inset-lg: inset 8px 8px 16px var(--color-shadow-dark), inset -8px -8px 16px var(--color-shadow-light);

  /* Transitions */
  --transition-shadow: box-shadow 0.25s ease;
  --transition-all: all 0.25s ease;
}
```

---

## Tools & Resources

- **[neumorphism.io](https://neumorphism.io/)** — Interactive CSS generator for neumorphic shadows. Adjust color, size, distance, blur, and shape.
- **[Hype4 Neumorphism Generator](https://hype4.academy/tools/neumorphism-generator)** — Alternative generator with additional options.
- **[CSS-Tricks: Neumorphism and CSS](https://css-tricks.com/neumorphism-and-css/)** — In-depth tutorial by Adrian Bece.
- **[Themesberg Neumorphism UI](https://themesberg.com/docs/neumorphism-ui/)** — Bootstrap-based neumorphic component kit for reference.
