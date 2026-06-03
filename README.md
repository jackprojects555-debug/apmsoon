# Handoff: AntiParos Marine Group — "The Home Port of Antiparos" (Coming Soon)

## Overview
A one-page, responsive **"Coming Soon" landing site** for AntiParos Marine Group, a new lifestyle harbor in Antiparos, Cyclades, Greece (Est. 2011, opening 2026). The page's single job is to plant a feeling of anticipation and belonging, and to capture **Early Access** email sign-ups before any service launches.

Positioning is **"Mediterranean Lifestyle Destination"** — a premium island address, NOT a marina/boatyard services company. The page leads with water, heritage, and human warmth; services are presented as curated "chapters," never an icon grid.

The experience follows a deliberate **tidal rhythm**: bright hero → dark Vision → light Lifestyle → light Harbor → dark Early Access → still Footer. (light → dark → light → dark → still)

---

## About the Design Files
The files in this bundle (`index.html`, `Antiparos Mobile.html`) are **design references created in HTML** — prototypes that demonstrate the intended look, motion, and behavior. **They are not production code to ship directly.**

The task is to **recreate these designs in the target codebase's environment** using its established patterns and libraries. If no codebase exists yet, choose an appropriate stack (Next.js / Astro / plain Vite + vanilla are all good fits for a one-page marketing site) and implement there.

- `index.html` is the actual responsive site (desktop + mobile in one file via media queries).
- `Antiparos Mobile.html` is a presentation-only showcase that embeds `index.html` in four phone frames — **do not port this file**; it exists to demonstrate the mobile layout.

---

## Fidelity
**High-fidelity (hifi).** Final colors, typography, spacing, copy, and interactions are all specified and should be recreated faithfully. The one caveat is **photography** (see Assets) — all images are tagged placeholders awaiting final art direction.

---

## Design Tokens

### Colors
| Token | Hex | Usage |
|---|---|---|
| `--paper` | `#F4F1EA` | Limestone/oyster — primary light background |
| `--paper-2` | `#EBE6DA` | Warmer sand-paper — Harbor section background |
| `--ink` | `#0E1F33` | Deep sea navy (from logo) — primary text + dark fields |
| `--ink-2` | `#0A1727` | Darker field — footer |
| `--oyster` | `#EDE7DB` | Light text on dark fields |
| `--cyan` | `#5BB8D6` | Aegean accent — **used exactly 3 times only** (see note) |
| `--sand` | `#C9B79C` | Warm sand — eyebrows on dark, secondary text |
| `--brass` | `#A98B5D` | Brass — hairlines, EST mark, eyebrows on light, inactive numerals |

**Cyan discipline (critical to the brand):** the Aegean cyan appears in exactly three places — (1) the hero kicker hairline, (2) the *active* service chapter numeral + the access form focus underline, (3) the Early Access button border. It is an accent that signals meaning/action; never use it as a fill or background. Keep this restraint.

### Typography
- **Display serif:** `'Cormorant Garamond'` (Google Fonts), weights 300/400/500, plus italics. High-contrast editorial serif — carries all headlines, pull-quotes, taglines, and the "Est." mark. Loaded at light weights (300) at large sizes — luxury lives in thin serifs.
- **Body/UI sans:** `'Mulish'` (Google Fonts), weights 300/400/500/600/700. Calm humanist sans — body copy, eyebrows, labels, nav, buttons.
- **Font stacks:** `--serif: 'Cormorant Garamond', Georgia, serif;` · `--sans: 'Mulish', system-ui, sans-serif;`
- **Eyebrow/label pattern:** sans, weight 500, `font-size: .72rem`, `letter-spacing: .32em`, `text-transform: uppercase`. (Labels elsewhere range `.18em`–`.34em` tracking.)

Google Fonts import used:
```
https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Mulish:wght@300;400;500;600;700&display=swap
```

### Type scale (clamp values from the build)
| Role | Family | Size |
|---|---|---|
| Hero headline | serif 300 | `clamp(2.6rem, 5.8vw, 5.6rem)`, line-height 1.05, max-width 16ch |
| Hero subheadline | sans 300 | `clamp(1.05rem, 1.5vw, 1.45rem)`, line-height 1.55 |
| Vision pull-quote | serif 300 italic | `clamp(1.7rem, 2.7vw, 2.5rem)`, line-height 1.42 |
| Lifestyle lead | serif 300 | `clamp(2.1rem, 4.6vw, 4rem)`, line-height 1.06 |
| Lifestyle fragments | serif 400 italic | `clamp(1.3rem, 2vw, 1.85rem)` |
| Harbor frame title | serif 300 | `clamp(2rem, 3.4vw, 3rem)` |
| Harbor chapter name | serif 400 | `1.55rem` |
| Access title | serif 300 | `clamp(2.4rem, 5vw, 3.6rem)` |
| Footer tagline | serif italic | `1.5rem` |
| Eyebrows / labels | sans 500 | `.72rem`, uppercase, tracked |

### Spacing
- Section vertical padding: `~150–170px` desktop, `96px` mobile.
- Horizontal page gutter: `56px` desktop, `24px` mobile.
- Content max-width: `1320px` (sections), `1100px` (footer).
- Mobile breakpoints: `1024px` (tablet — grids collapse to 1 column), `720px` (phone — nav → hamburger, mosaic stacks, form stacks).

### Radius / Shadow / Motion
- Border radius: minimal — `2px` on buttons/lozenges only. Photography and fields are square-cornered (editorial, not webby).
- Shadows: essentially none on the site itself (luxury restraint). Soft text-shadow on hero text over imagery: `0 2px 50px rgba(10,23,39,.5)`.
- Easing: `cubic-bezier(.2,.7,.2,1)` everywhere for entrances; `ease` for hovers.
- Reveal entrances are **transform-only** (translateY), gated behind a `.js` class on `<html>`/`<body>` so content is never invisible if JS fails. Respect `@media (prefers-reduced-motion: no-preference)` for the hero entrance.

---

## Screens / Views

This is a single scrolling page. Sections in order:

### 1. Navigation (fixed)
- **Layout:** Fixed top bar, transparent over hero, `padding: 28px 56px`. Left: **AM** monogram (serif, cyan). Center/right: links `THE VISION · THE HARBOR · EARLY ACCESS` + a `PRIORITY ACCESS` text-button with a brass underline.
- **Scroll state (`.scrolled`, past 80px):** frosted limestone backdrop (`rgba(244,241,234,.86)` + `backdrop-filter: blur(14px)`), padding shrinks, links/monogram invert to ink, and the full "Antiparos Marine" wordmark fades in beside the monogram.
- **Link hover:** fine cyan underline draws left→right (250ms).
- **Mobile (≤720px):** links hide, hamburger appears; tapping opens a full-screen ink overlay menu with serif-italic links.

### 2. Hero (full viewport, `100vh`, min-height 480px)
- **Layout:** Full-bleed background image (the Antiparos lagoon). Content anchored lower-left (`left: 56px; bottom: 10vh`), asymmetric. Dual gradient overlay (bottom + left) for legibility.
- **Elements:**
  - Top-right lozenge: `ARRIVING 2026` (brass border, oyster text).
  - Top-left tag: a `▶ Aerial video loop — placeholder still` marker. **In production this becomes an actual muted, looping, autoplay `<video>`** of a slow aerial of Antiparos water/boats; the still is a fallback poster.
  - Kicker: `ANTIPAROS · CYCLADES · EST 2011` with a cyan hairline after it.
  - Headline: **The Home Port of Antiparos.**
  - Subheadline: *A new lifestyle harbor for the island — for boats, for people, for the way Antiparos lives.*
  - Bottom-center scroll cue: breathing vertical hairline + `SCROLL`.
- **Motion:** background slow Ken-Burns zoom (scale 1.04→1.14 over 26s, alternating). Headline + sub rise-fade on load (riseIn, staggered ~0.35s/0.75s). On scroll, hero content parallaxes up and fades.

### 3. The Vision (dark / heritage)
- **Layout:** Full deep-ink (`--ink`) field, `padding: 160px 56px`. Two-column grid (`1.25fr .9fr`, gap 90px). Oversized **AM** monogram watermark centered behind, brass at ~5% opacity.
- **Left:** eyebrow `THE VISION`; pull-quote (serif italic): *"For fifteen years, Antiparos has been our home. We came to know its rhythms — the boats that winter here, the families who stay past summer, the quiet that returns each autumn. Now we are building a place to hold all of it. One address on the water, where the island gathers."*; signature `AntiParos Marine Group · Est. 2011` with a brass rule.
- **Right:** one tall portrait photo (moody, desaturated — `filter: saturate(.82) brightness(.85)`), height 560px.
- **Motion:** quote + image reveal on scroll. No cyan here — pure gravitas.

### 4. The Island, Lived (light / Lifestyle mosaic)
- **Layout:** `--paper` field, `padding: 170px 56px 150px`. Header: eyebrow `THE ISLAND, LIVED` + lead *"Some places you visit. **This one you belong to.**"* (em on second clause, italic). Below: a 12-column grid mosaic of three photos at varying sizes/offsets, interleaved with three serif-italic fragments:
  - Fig A (cols 1–6, h480, top-aligned) + fragment *"Mornings that start with coffee and end on the water."*
  - Fig B (cols 7–13, h560, +60px top) + fragment *"Long evenings. Good company. The sound of the rally."*
  - Fig C (cols 3–10, h520) + fragment *"The island slows you down. We built a place to match."*
- Each figure has a tiny brass uppercase caption.
- **Motion:** figures rise-fade on scroll; hover scales image to 1.05 (1.1s ease).
- **Mobile:** mosaic becomes a single column (`flex-direction: column`), images `height: 64vw`.

### 5. The Harbor (services as chapters)
- **Layout:** `--paper-2` field, `padding: 150px 56px 160px`. Two columns (`1fr 1.05fr`, gap 80px).
- **Left (sticky, `top: 120px`):** eyebrow `WHAT'S COMING ASHORE`; frame title *"A harbor for the practical and the beautiful alike."*; then a typographic index list (NOT icons). Each item: two-digit numeral (brass) + serif chapter name + a small uppercase plain-label subtitle. Closing line *"Opening in stages through 2026."*
  - `01 — Berthing & Boat Care` *(VIP Boat Parking)*
  - `02 — Harbor Parking` *(Car & Jet Ski)*
  - `03 — The Wash House` *(Car Wash)*
  - `04 — The Courts` *(Padel)*
  - `05 — Kitchen & Coffee` *(Home-Cooked Food & Coffee)*
  - `06 — The Studio` *(Wellness)*
  - `07 — Spaces to Let` *(Commercial Rental)*
- **Right:** a single large image (height 640px) that **cross-fades** to match whichever chapter is active.
- **Interaction:** hovering (desktop) or clicking a chapter sets it `.active` — its numeral turns **cyan**, name darkens to full ink, the item slides 8px right, and the right-hand image cross-fades (600ms). Default active = chapter 01.
- **Mobile:** columns stack; the image stage moves above the list (`order: -1`).

### 6. Early Access (dark / conversion)
- **Layout:** Full-bleed dark twilight water image (`filter: brightness(.5) saturate(.9)`) + radial ink gradient. Centered narrow column (max 640px), min-height 84vh.
- **Elements:** eyebrow `PRIORITY ACCESS`; title *"Be among the first ashore."*; sub *"Join the Early Access list for a first look, opening dates, and a standing invitation when the harbor opens."*; a single-line form (email input + `REQUEST ACCESS` button on one hairline-bordered row); micro-line *"No noise. Only word from the harbor."*
- **Interaction:** input focus draws a cyan underline; button fills cyan-on-ink on hover; **on submit** the form + micro-line hide and a success line fades in: *"Welcome aboard. We'll be in touch from Antiparos."* (adds class `done` to the section).
- **Mobile:** form stacks vertically; input centered, button full-width.

### 7. Footer (still)
- **Layout:** `--ink-2` field, centered, `padding: 90px 56px 50px`. Centered brand lockup (AM monogram + "Antiparos Marine" + "Est 2011"). Brass hairline. A single row: location `ANTIPAROS · CYCLADES · GREECE` / links `Instagram · Contact` (cyan dot separator) / `EST. 2011`. Then the tagline *"Belong to the island."* (serif italic) and a copyright line `© 2026 AntiParos Marine Group · Arriving 2026`.

---

## Interactions & Behavior
- **Nav scroll transform:** at `scrollY > 80`, add `.scrolled` (frosted bg, invert colors, reveal wordmark).
- **Mobile menu:** hamburger toggles a fixed full-screen overlay; links close it on tap.
- **Scroll reveals:** `IntersectionObserver` (threshold .18, rootMargin `0px 0px -8% 0px`) adds `.in` to `.reveal` elements (transform-only translateY → 0). Observer is used (not scroll listeners or timers) because it's reliable and not throttled.
- **Hero entrance:** CSS keyframe `riseIn` on load, gated behind `.js` + `prefers-reduced-motion`. Important: entrances animate **transform only**, never opacity-to-visible from a hidden base without the `.js` gate — so no-JS / reduced-motion / print always show content.
- **Harbor chapter swap:** `mouseenter` + `click` on each `.harbor__item` → toggle `.active` and move `.show` on the matching stage `<img>`.
- **Early Access submit:** `preventDefault`, add `.done` to `#access`. **In production, wire to the real email/ESP** (Mailchimp/Klaviyo/etc.) with proper validation, success + error states.
- **Hero parallax:** on scroll, hero content `translateY(scrollY * .18)` and fades out by ~0.7×viewport.

## State Management
Minimal — this is a marketing page. State needed:
- `navScrolled: boolean` (scroll position)
- `mobileMenuOpen: boolean`
- `activeChapter: number` (0–6, Harbor section)
- `emailSubmitted: boolean` + `email: string` + validation/error state (Early Access)
- Email submission → POST to ESP endpoint; handle loading / success / error.

---

## Assets
All photography is **placeholder** and tagged `PLACEHOLDER · FINAL PHOTOGRAPHY TBR` in the UI. Sourced from the client's reference uploads (low-res, mood only). Replace with final, art-directed, high-resolution images:
- `assets/hero-lagoon.jpg` — hero background (**replace with aerial video loop** + poster still)
- `assets/cove.jpg`, `assets/boat-cruise.jpg`, `assets/village.jpg`, `assets/yacht-care.jpg` — Vision, Lifestyle, and Harbor chapter imagery
- **Priority shots needed:** hero aerial video; one cinematic frame per Harbor chapter (incl. the boat-handling reality shot, lit beautifully); 3–4 golden-hour human moments for Lifestyle; one moody texture detail for Vision.

**Logo:** the AM monogram + wordmark are currently a faithful **typographic recreation** (Cormorant Garamond) so they recolor cleanly on dark/light surfaces. Swap in the client's official vector AM mark when available.

**Design system note:** this project was tagged with a "Design System" reference that is currently **empty** — there were no tokens, fonts, or components to inherit. The tokens documented above (defined in `index.html`) ARE the de facto design system for this site. If the client later populates the shared design system, reconcile against it.

---

## Files
- `index.html` — the complete responsive site (all sections, CSS in `<style>`, JS in `<script>` at the end). This is the source of truth.
- `Antiparos Mobile.html` — presentation-only mobile showcase (embeds index.html in phone frames). **Do not port.**
- `assets/` — placeholder photography (replace before launch).
