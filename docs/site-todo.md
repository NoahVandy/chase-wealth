---
title: Chase Wealth — Site Elements To Add for Search & AI Visibility
description: Actionable checklist of on-site sections, content, and technical markup needed to make the Chase Wealth landing pages rank on Google and get cited by AI engines.
derived_from: [seo-stuff.md]
reference_site: https://www.allstreetwealth.com/
firm_type: fee-only fiduciary wealth management (NOT a law firm)
audience: agents, builders, content strategists
status: draft — nothing below is implemented in the current mockups yet
last_updated: 2026-07-24
tags: [checklist, seo, aio, geo, e-e-a-t, schema, content]
---

# Chase Wealth — Things We Need to Add

Working checklist of what the site needs so it's **trusted by Google** and **citable by AI engines**. Derived from [seo-stuff.md](./seo-stuff.md) and benchmarked against allstreetwealth.com. The current `*.html` mockups are visual concepts only — they have **none** of the items below.

> **Vertical note:** the source strategy was written for an estate-planning *attorney*. Chase Wealth is a **fee-only fiduciary wealth firm**, so translate legal specifics: `Attorney`/`LegalService` schema → `FinancialService`/`FinancialAdvisor`, bar/ABA Rule 7.1 → **SEC/FINRA advertising rules**, legal directories → financial ones. Keep the fee-only / fiduciary angle as the primary trust hook.

---

## Priority 0 — Technical foundation (highest leverage, currently zero)

- [ ] **Structured data / schema markup** (JSON-LD). The single biggest gap — nothing machine-readable exists today. **See the full spec in [§ Schema note](#schema-note) below.**
  - [ ] `FinancialService` / `Organization` — firm name, logo, address, phone, area served, fee model
  - [ ] `Person` for each advisor (name, title, credentials, sameAs → LinkedIn)
  - [ ] `FAQPage` on any FAQ content
  - [ ] `Review` / `AggregateRating` for testimonials
  - [ ] `Article` + `author` on every blog post
- [ ] **`robots.txt` that allows AI crawlers** (GPTBot, PerplexityBot, etc.) — don't accidentally block them
- [ ] **Meta basics per page** — unique `<title>`, meta description, canonical (mockups already have title/description; standardize)
- [ ] **Performance/mobile** — fast, mobile-first, clean internal linking (mostly OK as static single-file pages)

## Priority 1 — Trust / E-E-A-T sections (needed for a YMYL money topic)

- [ ] **Advisor bio section** with real credentials (CFP®, CFA, etc.), photo, and background — *currently missing entirely*
- [ ] **Fee transparency block** — state the actual fee model in specific numbers (benchmark: AllStreet publishes "$X/year + Y% on assets"). Specific & verifiable > vague.
- [ ] **Fiduciary / fee-only statement** — explicit, plus a link to **Form ADV** and RIA registration / states served
- [ ] **Client testimonials embedded on-page** (verbatim quotes, not just a "read reviews" link)
- [ ] **Reviews signal** — Google review count/rating with link
- [ ] **Case studies / client success stories** shown on-page, not just linked
- [ ] **Awards / rankings / "as seen in"** press logos
- [ ] **Privacy Policy and Terms pages** (+ any required regulatory disclosures/disclaimers)

## Priority 2 — Content built to be extracted by AI (§3.1 of strategy)

- [ ] **FAQ section** with question-style headings, each followed by a **direct 1–2 sentence answer** before elaboration
- [ ] **Blog / content hub** organized in clusters around real services (benchmark AllStreet: tax planning, equity comp/RSUs, business owners, budgeting)
  - [ ] **Named author byline + date** on every post
  - [ ] Question-format and keyword-targeted titles (e.g. "How much do I need to retire?")
  - [ ] Clean, self-contained definitions the AI can lift
- [ ] **Specific, verifiable claims** throughout — kill vague marketing copy ("we create a roadmap") in favor of concrete process/outcomes/numbers
- [ ] **Service pages / hub-and-spoke** — a page per service (investment management, tax planning, retirement, equity comp) with location + intent keywords

## Priority 3 — Off-site & entity (§3.3, §4 of strategy)

*Not code, but track it — AI recommendations depend heavily on off-site presence.*

- [ ] Consistent **Name/Address/Phone** across financial directories and profiles
- [ ] **LinkedIn** profiles for firm + advisors, identical naming everywhere (feeds Google knowledge panel)
- [ ] Earned mentions: local press, podcast appearances, community/Q&A presence (Reddit/YouTube are heavily cited by AI)
- [ ] Google Business Profile fully completed

## Priority 4 — Measurement

- [ ] Baseline **AI-citation check** — query ChatGPT/Perplexity/Gemini/Claude with buyer questions, record whether the firm gets named
- [ ] Track traditional metrics (rankings, map-pack, review count) alongside AI-citation frequency

---

## Compliance gate (applies to all content above)

- [ ] Route marketing claims through **SEC/FINRA advertising-rule** review — no misleading claims, careful handling of testimonials/performance
- [ ] Build the review step in from the start, not after the fact

---

<a id="schema-note"></a>
## Schema note — the JSON-LD to add

**Goal:** add schema.org structured data (JSON-LD in `<head>`) so engines can machine-read who Chase Wealth is, what it does, and that it's trustworthy. This follows the E-E-A-T / "let machines parse who he is" point in [seo-stuff.md](./seo-stuff.md) §1–§2, adapted from WebKey Digital's estate-lawyer schema stack (`webkeydigital.com/estate-lawyer-seo/`).

**Translate the legal stack → financial.** WebKey's recommendations were for a law firm; swap the types:

| WebKey (legal) | Chase Wealth (financial) |
|---|---|
| `LegalService` | `FinancialService` |
| `Attorney` | `FinancialAdvisor` (subtype of LocalBusiness) or `Person` with `jobTitle` |
| `hasCredential` (ACTEC Fellow, board cert) | `hasCredential` (CFP®, CFA, CPA) |
| Offers: Will Drafting, Living Trust, Probate | Offers: the services AllStreet highlighted (below) |

**Services to model in `hasOfferCatalog`** (mirroring the AllStreet example):
- Investment Management
- Tax Planning
- Business / Business-owner Planning
- Equity Compensation (RSUs, options)
- Retirement / Financial Planning

**Schema types to implement (checklist):**
- [ ] **`FinancialService`** — core firm entity: `name`, `description`, `url`, `logo`, `telephone`, `address` (PostalAddress), `areaServed` (AdministrativeArea — Carmel/Indiana + "nationwide" states served), `priceRange` or fee note, `hasOfferCatalog` → the services above as `Offer` objects, `sameAs` → LinkedIn/social/directory profiles
- [ ] **`Person` / `FinancialAdvisor`** for each advisor — `name`, `jobTitle`, `image`, `worksFor` → the firm, `hasCredential` (CFP®/CFA/CPA), `sameAs` → LinkedIn
- [ ] **`FAQPage`** — each Q as `Question` + `acceptedAnswer` `Answer`; pairs directly with the on-page FAQ block (helps AI Overview eligibility)
- [ ] **`Review` / `AggregateRating`** — surface the Google review count/rating (benchmark: "34+ 5-star")
- [ ] **`BreadcrumbList`** — site hierarchy on inner pages
- [ ] **`SpeakableSpecification`** — mark the short direct-answer chunks (§3.1) to boost AI Overview eligibility
- [ ] **`Article` + `author`** — on every blog post, wired to the advisor `Person`

**Best practices (from WebKey + strategy doc):**
- Keep **NAP identical** to what's shown on-page and across all directories/profiles ([seo-stuff.md](./seo-stuff.md) §2, §4)
- Use `sameAs` to link the firm/advisor entities to LinkedIn + directory profiles — this is the "coherent picture" that earns a knowledge panel (§4)
- **Validate** every block with **Google's Rich Results Test** before shipping
- Only mark up content that's actually visible on the page (no phantom reviews/FAQs)

**Compliance:** any advisor credentials, testimonials, or performance/fee claims in the schema are marketing claims too — run them through the **SEC/FINRA** review gate above before publishing.

---

## Mapping to the mockups

The concept files (`art-deco`, `neo-geo`, `neumorphic`, `modernist`, `neo-modernist`, …) share a nav → hero → sections → CTA structure and still have none of the above.

**The Material concept shipped** as `../index.html` + `../about.html`. Status there:

| Slot | Status on the shipped pages |
|---|---|
| Advisor bio block | ✅ teaser card on `index.html`, full bio page at `about.html` |
| Fee/fiduciary transparency | ✅ the real tiered schedule is published on-page in the `#fees` section (1.00% → 0.60% across five breakpoints) and mirrored into `feesAndCommissionsSpecification` in the schema. Beats the AllStreet benchmark of naming a number. |
| Testimonials + reviews | ❌ deliberately absent — no real, disclosure-compliant testimonials exist yet (see the SEC Marketing Rule note under the compliance gate) |
| FAQ block | ❌ not built |
| Footer links | 🟠 About/Services/How it works/Contact/Form ADV present; Form ADV points at generic `adviserinfo.sec.gov` pending a CRD, and Privacy/Terms don't exist |
| JSON-LD | ✅ `FinancialService` + `Person` on `index.html`; `ProfilePage`/`Person` on `about.html`. `hasOfferCatalog` lists the six real services. Not yet validated with Google's Rich Results Test. |
| NAP | ✅ identical in the contact card, both footers, and both schema blocks |

**Do not** add an AUM figure or an aggregate rating to the shipped pages — the client prohibits publishing AUM, and there is no review corpus to aggregate. Note that publishing the *fee schedule* (a rate applied to a client's own portfolio) is not the same thing as publishing firm AUM, and is explicitly wanted.

**Open question on the fee schedule:** the source the client supplied is just the five brackets and rates. It does not say whether the tiers are **marginal** (each dollar billed at its own bracket's rate) or **flat** (the whole balance billed at the rate its total falls into) — the difference is thousands of dollars a year for a client near a breakpoint. The on-page note is deliberately worded to avoid asserting either. Confirm against the advisory agreement and Form ADV Part 2A, then make the page say so explicitly; ambiguity about how a fee is calculated is exactly what the SEC advertising rules treat as misleading.

FAQ + `FAQPage` schema is now the highest-value remaining item.
