---
title: Chase Wealth — SEO Section Map (Mockup Annotations)
description: Which sections of the landing page signal good SEO/AI-visibility, what each one proves, and how the in-mockup "SEO map" overlay marks them.
derived_from: [seo-stuff.md, site-todo.md]
reference_site: https://www.allstreetwealth.com/
audience: agents, builders, reviewers
last_updated: 2026-07-24
tags: [seo, aio, e-e-a-t, annotations, mockups, overlay]
---

# SEO Section Map

This note defines the **SEO-signal sections** of the landing page — the parts that make the site rank-worthy and AI-citable — and documents the **"SEO map" overlay** built into the mockups so a reviewer can *see* where each signal lives.

Grounded in [seo-stuff.md](./seo-stuff.md) (the strategy) and [site-todo.md](./site-todo.md) (the build list), benchmarked against allstreetwealth.com.

---

## The overlay (how to use it)

Each annotated mockup has a **"Show SEO map"** button fixed at the top-right. Click it to draw labeled outlines over the SEO-relevant sections, plus a legend explaining the colors and listing the **gaps** (signals not yet on the page). Click again to hide. The overlay is a dev tool — it adds no layout when off and gets stripped for the production build.

### Status colors

| Color | Status | Meaning |
|---|---|---|
| 🟢 Green | **present** | The section already delivers this SEO signal well. |
| 🟠 Orange | **partial** | The section exists but needs strengthening to fully count (usually: add specifics or schema). |
| 🔴 Red (legend only) | **missing** | An important signal with no home on the page yet — must be added. |

---

## Section-by-section (what each proves)

Mapped to the current `neo-modernist.html`; the taxonomy is the same for every concept.

| Section | Signal it sends | Status | Strategy ref |
|---|---|---|---|
| **H1 hero headline** | Topical relevance — the page's single most important heading | 🟠 partial (brand-voice line; weave in a "fee-only fiduciary wealth" keyword) | §2 relevance |
| **Hero lede** | Plain value prop containing core keywords ("fee-only fiduciary practice") | 🟢 present | §3.2 specific |
| **Stats row** | Specific, *verifiable* numbers ($480M AUM, tenure, 100% fee-only) — exactly what AI engines favor over vague copy | 🟢 present | §3.2 |
| **Services** | Service keywords + clean H2/H3 structure; anchor for hub-and-spoke + `FinancialService`/`hasOfferCatalog` schema | 🟠 partial (add keywords + schema offers) | §2 clusters |
| **Method / process** | Demonstrates expertise and process transparency (E-E-A-T) | 🟢 present | §1 |
| **Fee statement** | Fee transparency = top trust signal | 🟠 partial ("one flat fee" — add the real number, like AllStreet's "$18,000/yr + 0.35%") | §3.2 |
| **Testimonial** | Social proof; slot for `Review` / `AggregateRating` schema | 🟠 partial (one quote — add review count/rating) | §1 |
| **Contact form** | Conversion + local/hiring intent ("book a free call") | 🟢 present | §2 intent |
| **Footer / legal** | RIA disclosure + NAP + trust links | 🟠 partial (has RIA line; add address/phone NAP, Form ADV, Privacy/Terms) | §1, §2, §4 |

---

## Gaps — signals with no section yet (shown red in the legend)

These have **no home on the page** and are the highest-value additions (see [site-todo.md](./site-todo.md)):

- **JSON-LD schema** in `<head>` — the machine-readable layer; nothing exists (see [site-todo.md § Schema note](./site-todo.md#schema-note))
- **Advisor bio + credentials** (CFP®/CFA) — no bio section at all; central E-E-A-T signal for a money topic
- **FAQ section** — question headings + short direct answers (`FAQPage` schema, AI-Overview eligibility)
- **NAP** (address + phone) — needed for local SEO and schema consistency
- **Form ADV / Privacy / Terms** footer links
- **Aggregate review rating** — a Google review count/link (benchmark: AllStreet's "34+ 5-star")

---

## How it's wired in the mockup

- Sections carry two data attributes: `data-seo="<label>"` and `data-seo-status="present|partial"`.
- CSS draws the outline and renders the label from `attr(data-seo)`; status sets the color.
- A small inline script injects the toggle button and flips a `seo-map-on` class on `<body>`.
- To annotate a **new** concept, copy the overlay `<style>`/legend/`<script>` block and tag its sections with the same `data-seo` labels from the table above.

**Rollout status:** implemented in `neo-modernist.html`, `modernist.html`, `neumorphic.html`, `minimalism.html`, `modernist-brief.html`, `minimalism-brief.html`, `modern-minimalism.html`, `editorial-luxury.html`, `scandinavian.html`. Not applied to `art-deco` or `neo-geo`.

> **The overlay is deliberately absent from the shipped site** (`../index.html`, `../about.html`). Those are the production pages, and the overlay is a dev tool that must be stripped from a production build — so it was never added. Several of the gaps listed above are now closed there: advisor bio + credentials, NAP, and JSON-LD (`FinancialService` + `Person` on the landing page, `ProfilePage`/`Person` on the About page) all exist. The stats row is intentionally gone — the client prohibits publishing AUM. Still open on the shipped pages: FAQ + `FAQPage` schema, reviews/`AggregateRating`, a specific published fee number, and Privacy/Terms pages.

> Note: `modernist`/`neumorphic` use a **palette-independent** version of the overlay (hardcoded colors + system font) so the block is drop-in identical across concepts. `neumorphic` has no stats section, so "on-page firm stats" is listed as a gap there.
