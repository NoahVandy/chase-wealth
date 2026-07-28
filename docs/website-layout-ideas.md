---
title: Website Layout Ideas — Summary & How-To
description: The 12 website layout patterns from Figma's resource library, each with what it is, how to build it, and where it fits the Chase Wealth mockups.
source: https://www.figma.com/resource-library/website-layout-ideas/
audience: agents, designers, builders
last_updated: 2026-07-25
tags: [layout, design, reference, mockups]
---

# Website Layout Ideas

Summary of the 12 layout patterns from [Figma's website-layout-ideas library](https://www.figma.com/resource-library/website-layout-ideas/). Each entry: **what it is**, **how to accomplish it**, and **where it maps** to the Chase Wealth concepts in this repo.

---

## Idea 1: Grid Layout
**What:** Rows and columns organize content into a predictable framework so important elements are easy to find. Sub-types: modular (block-based), single-column (long text), and column grids (3–12 vertical divisions).
**How:** Define a base grid (CSS Grid / flexbox) with a consistent column count and gutter; align every section to it. Pick column count by density — single column for reading, 12-col for complex pages.
**In our mocks:** The backbone of every concept — `neo-geo` makes the grid *visible*; `minimalism` uses a wide single column.

## Idea 2: Split-Screen Layout
**What:** Two equal halves showing contrasting content side by side (e.g. image + description).
**How:** A two-column grid (`grid-template-columns: 1fr 1fr`) at full viewport height; collapse to stacked on mobile.
**In our mocks:** The contact sections (`c-grid`) split copy vs. form.

## Idea 3: Asymmetrical Layout
**What:** Two sections of *unequal* size; the larger space pulls attention and holds the key message/CTA.
**How:** Uneven grid columns (e.g. `2fr 1fr`) or offset placement; deliberately weight one side.
**In our mocks:** `neo-modernist` hero (copy weighted against the smaller geometric art).

## Idea 4: Full-Screen Layout
**What:** One image/design fills the whole viewport as background, with text and buttons overlaid.
**How:** A `100vh` hero with a background image/gradient; overlay text with sufficient contrast (scrim or overlay layer).
**In our mocks:** Not used yet — a candidate hero treatment for `art-deco` or `material`.

## Idea 5: Side-Scrolling Layout
**What:** Content flows horizontally (left→right) instead of vertically — good for categories or galleries.
**How:** A horizontal flex row with `overflow-x: auto` (or scroll-snap); add visible affordances (arrows) so users know to scroll sideways.
**In our mocks:** Echoed by the `neo-modernist` marquee ticker strip (horizontal motion).

## Idea 6: Card Layout
**What:** Square/rectangular "cards" package content (image + summary) with hover interactivity for browsing.
**How:** A grid of card components with consistent padding, radius, and elevation; add hover lift/shadow.
**In our mocks:** `material` is built on elevated cards; services blocks across concepts are card-like.

## Idea 7: Magazine Layout
**What:** A grid-based editorial structure — large hero image + prominent headline + flowing story sections.
**How:** Mix column spans within a grid (a wide feature block beside narrower text columns); lead with a big headline.
**In our mocks:** Closest to `modernist`'s essay-like hierarchy of headline → measured sections.

## Idea 8: Gallery Layout
**What:** Minimal text; equal-spaced image grid lets visuals dominate. Ideal for portfolios.
**How:** A uniform image grid (equal cells, tight consistent gaps); keep captions/text sparse.
**In our mocks:** Not used — this repo is copy-led, not image-led.

## Idea 9: Zig-Zag Layout
**What:** Alternating blocks of text and image guide the eye in a Z pattern down the page, creating natural flow.
**How:** Stack full-width rows; alternate the order of the text/image column each row (reverse the flex/grid direction on even rows).
**In our mocks:** Now used in `neo-modernist` and `minimalism` — the Method section alternates copy with a visual (geometric plate / large numeral) row by row.

## Idea 10: F-Pattern Layout
**What:** Positions key content along the natural F-shaped reading path (horizontal scan, vertical drop, horizontal scan).
**How:** Put the most important items top and left; front-load headings and the start of lines; keep left-alignment for scannability.
**In our mocks:** Implicit in every left-aligned hero + section-head structure.

## Idea 11: Interactive Layout
**What:** Buttons, sliders, scroll effects, and animations invite exploration for a more immersive experience.
**How:** Layer in scroll-triggered reveals, hover state changes, and interactive controls — motion that responds to the user.
**In our mocks:** The `IntersectionObserver` reveal-on-scroll and hover states in every concept.

## Idea 12: Animated Layout
**What:** Motion graphics, transitions, and hover effects capture attention and add delight.
**How:** CSS transitions/keyframes or JS animation; keep motion purposeful and performant (respect `prefers-reduced-motion`).
**In our mocks:** `neo-modernist`'s rotating hero geometry and drawn-rule hover effects.

---

## Quick map: which layout each concept leans on

| Concept | Primary layout idea(s) |
|---|---|
| `art-deco` | Grid + symmetrical (candidate: Full-Screen hero) |
| `material` | Card (6) + Grid (1) |
| `neo-geo` | Grid (1, made visible) + Interactive (11) |
| `modernist` | Magazine (7) + F-Pattern (10) |
| `neo-modernist` | Asymmetrical (3) + **Zig-Zag (9)** + Animated (12) |
| `neumorphic` | Card (6) + Interactive (11) |
| `minimalism` | Grid single-column (1) + **Zig-Zag (9)** + F-Pattern (10) |

**Unused ideas worth trying:** Full-Screen (4), Gallery (8).
