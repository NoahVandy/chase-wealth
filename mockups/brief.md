# Chase Wealth — Concept Brief (structured template)

A structured companion to `prompts.md`. The three-paragraph prompts drive the *visual style*
of each concept; this brief pins down everything that stays **constant** across all of them —
the firm, the audience, the copy, and the technical floor. When starting a new concept, keep the
fixed fields below verbatim and only rewrite the three **per-concept** fields (Tone, References,
Motion) to match that concept's entry in `prompts.md`.

---

## PROJECT
Single-page landing concept for **Chase Wealth Management**, a fee-only fiduciary wealth-management
firm — a self-contained design exploration whose one job is to convince a prospective client that
this firm is trustworthy enough to manage their money, and to get them to **book a free call**.
(Each `mockups/*.html` renders this same firm and copy in a different visual style; the concepts
compete, they don't link.)

## AUDIENCE
Prospective clients evaluating who should manage their wealth: pre-retirees and established
professionals/families with real assets, plus referrers doing due diligence. They already know
roughly what a financial advisor does — what they're skeptical about is **hidden incentives**:
commissions, product-pushing, fine print, advisors who aren't on their side of the table. They are
convinced by the opposite of a sales pitch: fee-only/fiduciary stated plainly, a written plan they
can hold the firm to, transparent flat-fee pricing, verifiable numbers, and calm competence. This
is **YMYL** ("Your Money or Your Life") content, so it's held to a higher trust bar — every claim
should read as specific and verifiable, never hedgy marketing filler.

## TONE & REGISTER
*(Per-concept — this is where a concept expresses its style. Rewrite to match the concept's
`prompts.md` entry; the register below is the shared baseline all concepts stay within.)*
Trustworthy, precise, quietly confident, plainspoken. Premium through restraint, never flashy or
salesy — a firm that "deals in fundamentals." Each concept then adds its own adjective set, e.g.
Art Deco = *ceremonial, machined, weighty*; Material = *calm, friendly, engineered*;
Neo-Geo = *rational, metronomic, exact*; Neo-Modernist = *structural, instrumented, deliberate*.

## REFERENCES
*(Per-concept — pull the named references and "what to take from each" straight from this concept's
`prompts.md` paragraph 3.)* Shared throughline across every concept: **restraint as the signal of
wealth** — take structure/proportion/legibility, avoid generic financial-services stock imagery,
gradients, and SaaS-template clichés. Style-specific anchors live in `prompts.md` (e.g. interwar
grand architecture for Art Deco; paper-elevation and a well-run clinic for Material; mid-century
concrete-poetry posters and observatory instruments for Neo-Geo).

## CONTENT & HIERARCHY
Shared page spine (same order and meaning in every concept; real copy below beats placeholder):
1. **Sticky nav** — logo · Services / Method / Contact · primary CTA "Book a free call". *(primary)*
2. **Hero** *(primary)* — a style-appropriate headline over the value prop:
   "Chase Wealth Management is a fee-only fiduciary practice. We build written plans and rule-based
   portfolios for families who want their money managed the way good things are engineered:
   plainly, precisely, and to last." CTAs: **Book a free call** + a secondary "See the work".
3. **Trust ticker/strip** *(supporting)* — Fee-only fiduciary · Rules-based rebalancing ·
   Written plans, verified annually · No commissions, ever.
4. **Stats** *(supporting proof)* — **$480M** assets under advisement · **26 yrs** combined advisor
   tenure · **100%** fee-only, fiduciary, always.
5. **Services** *(primary)* — three, no bundling: **Investment management** (globally diversified,
   low-cost portfolios rebalanced by written rule); **Financial planning** (retirement income,
   taxes, insurance, estate in one annually-reviewed document); **Ongoing counsel** (one advisor
   who knows the whole structure).
6. **Method** *(primary)* — three steps, each with a defined output: **Assess** (free call + full
   inventory) → **Plan** (written plan + model portfolio, walked through line by line) →
   **Maintain** (rule-based rebalancing, quarterly reporting, annual reviews). Close on fee
   transparency: **one flat fee, in writing — no commissions, no products sold, no asterisks.**
7. **Proof / testimonial** *(supporting)* — "They removed everything from my finances that didn't
   need to be there. What's left is simple, and it works." — M. Whitfield, client since 2016.
8. **Contact CTA** *(primary — the conversion)* — "Begin with one honest hour." A first
   conversation costs nothing and obliges nothing; taking new clients this quarter. Name / Email /
   Subject / optional Message → "Book my free call".
9. **Footer** — logo, tagline **"Advice on your side of the table,"** nav, CTA, and RIA disclosure.

## MOTION & INTERACTION
*(Per-concept — the interaction *feel* is part of each concept's spec in `prompts.md`: Art Deco
"machined and weighty," Material "snappy with a soft landing," Neo-Geo "metronomic," Neumorphic
"cushioned," etc. Match it.)* Shared baseline in every concept: a lightweight scroll-reveal on
sections (IntersectionObserver), hover affordances on nav/CTA/service rows, smooth in-page anchor
scrolling. Motion must **explain, not entertain** — no carnival. **Respect
`prefers-reduced-motion`** and keep any looping/marquee/animation graceful when disabled.

## ASSETS (attached)
No external binary assets — everything is inline and self-contained:
- **Logo** — inline SVG: a "chasing arc" mark + wordmark `CHASE` / `WEALTH MANAGEMENT`, drawn with
  `fill: currentColor` so it inherits the palette (used in nav and footer).
- **Decorative art** — inline SVG geometry authored per concept (no raster images, no photos).
- **Fonts** — Google Fonts via CDN only (each concept picks its own display + text pairing in
  `:root`; e.g. Neo-Modernist uses Space Grotesk + Manrope).
- **Icons** — inline SVG glyphs for the three services.

## CONSTRAINTS
- **Single self-contained `.html` file** per concept, hand-written, with an inline `<style>` block
  (and inline `<script>` only if needed). **No build system, no dependencies, no framework, no
  external CSS/JS** except Google Fonts. Must render correctly opened directly from disk.
- Design tokens (palette + font stack) live in `:root` custom properties — change them there, not
  inline. A top HTML comment names the concept; the palette comment names any single accent color.
- The two black-and-white concepts (`neumorphic`, `modernist`) stay **strictly monochrome** — all
  emphasis from scale/contrast/light, no hue.
- Accessibility: **WCAG AA** contrast, semantic landmarks/headings, labeled form fields,
  `aria-hidden` on decorative SVG, honor `prefers-reduced-motion`.
- Responsive / mobile-first; no horizontal overflow at small widths.
- YMYL trust posture: keep claims specific and verifiable; include the fee-only RIA disclosure in
  the footer ("nothing herein constitutes investment advice").
- The optional **SEO-map overlay** (toggle button + `data-seo` attributes + legend) is a
  dev/review tool only — it must be trivially removable and **stripped from any production build**.

## DELIVERABLE
One complete, production-quality `mockups/<style-name>.html` — fully responsive, self-contained,
AA-accessible, rendering the firm/copy above in the chosen style — plus its matching three-paragraph
entry in `prompts.md` (mood/arrival, philosophy/typography/interaction, abstract references).
