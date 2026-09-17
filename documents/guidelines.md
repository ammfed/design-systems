# Documents — guidelines

## Colour roles

| Role | Token | Notes |
|---|---|---|
| Accent (large text, rules, bullets) | `--ds-color-gold-500` | Fails AA at body size — display and rule use only |
| Accent (text, AA-safe) | `--ds-color-gold-700` | |
| Accent fill under white text | `--ds-color-gold-600` | Exactly 4.5:1 |
| Body text | `--ds-color-neutral-800` | |
| Muted text / captions | `--ds-color-neutral-500` | |
| Alt row / zebra surface | `--ds-color-neutral-50` | |
| Quote / key-fact tint | `--ds-color-gold-50` | |
| Closing-slide ground | `--ds-color-neutral-900` | Optional, used once per deck at most |

Supporting hues (`blue`, `green`, `red`, plus a secondary warm accent) appear only inside note / success / important / warning callouts.

## Type scale

Two families: one for headings, one for body, each with a matching pair for the mirrored-language version (swapped by document direction, not layout). Screen scale runs on a 1.333 ratio from a 16px base; print scale is defined separately in points; slide scale is defined separately again. Never below 16px on screen or 8pt in print. At most five weights in one document.

## Layout

A4-equivalent page: 12mm margins, an 8×10 column/row grid, 4mm gutters. The outer column nearest the spine is protected for a mark or full-bleed image only. Slides: 1920×1080, 0.5in margins, a 12×6 grid, mark in one fixed corner, a short running label in the opposite corner, a slide number in a third corner.

## Components

- **Page furniture** — cover, section divider, running header, running footer, page frame.
- **Content blocks** — data table, callout (note/success/important/warning), pull quote, caption, list, key-facts block, executive summary block, signature block, reference list.
- **Slide masters** — title, section divider, content, two-column, chart, table, image, closing.
- **Graphics layer** (deck-only, additive) — a line-based geometric pattern for section dividers, a small chart set (bar, column, line, ring, sparkline) using the accent as the first series and neutral tones for the rest, and a milestone timeline with the current node ringed in the accent colour.

## Motion tokens

A single reveal timing (roughly 700ms fade-rise) for body content on a slide, and a slower draw-in (roughly 900ms) for an accent line under a title. Both are opt-in and both respect reduced-motion preferences.

## Dark deck theme

Every slide master also has a dark tone: a near-black ground, white text, and dimmed hairlines, with the mark sitting on a white band so it stays legible on the dark ground. This is a **whole-deck** setting, never mixed slide-by-slide within one deck — pick light or dark for the deck as a whole. A4 documents stay light-only; the dark tone is a deck (slide) feature.

## Content rules, in full

See the README for the condensed version. In full: sentence case everywhere; formal third-person voice for the organisation, second person only in direct correspondence; consistent digit and unit formatting across both language versions; single quotes; Oxford comma; spelled-out conjunctions in running copy; restrained emphasis; no emoji or exclamation marks; slides capped at six bullets and one idea; every table/figure/image carries its caption or alt text.
