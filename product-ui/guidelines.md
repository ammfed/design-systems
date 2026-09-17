# Product UI — guidelines

## Colour roles

| Role | Token | Notes |
|---|---|---|
| Accent (large text, hover, header/footer bar) | `--ds-color-gold-500` | |
| Component fill (buttons, links) | `--ds-color-gold-600` | 4.5:1 on white |
| Card border (bordered/service cards) | `--ds-color-gold-300` | |
| Body text | `--ds-color-neutral-800` | |
| Muted text | `--ds-color-neutral-500` | |
| Border | `--ds-color-neutral-100` | |
| Page surface | white / `--ds-color-neutral-25` | |
| Muted band | `--ds-color-neutral-50` | |
| Success | `--ds-color-green-600` | |
| Info | `--ds-color-blue-600` | |
| Warning fill/text | `--ds-color-amber-fill` / `--ds-color-amber-text` | |
| Error | `--ds-color-red-600` | |
| Focus ring | a distinct amber, not the accent hue | |

## Type scale

Headings (7 steps, largest to smallest): 76 / 62 / 48 / 40 / 32 / 26 / 20, weight decreasing from a light display weight at the top toward a semi-bold weight at the smallest heading step. Body (7 steps): 30 / 24 / 20 / 18 / 16 / 14 / 12.

## Spacing and grid

4px base unit. Common gaps: 8 (button group), 16 (toast, small card), 24 (card padding, section stack, grid gap), 28 (large card). Six-column grid, 24px gutter, container widths tiered by breakpoint (roughly 1480 / 1240 / 980 / 740 / fluid).

## Radii

4 (badge, alert, checkbox) · 6 (small button) · 8 (button, input, modal, dropdown, toast) · 12 (card) · 16 (large card) · full (avatar, pagination, toggle, step badge).

## Elevation

None by default — 1px borders carry separation. Small shadow on inputs; a larger one on dropdown/popover/toast; a distinct modal shadow. A subtle hover glow in the lightest accent tint on interactive cards.

## Component inventory

**Direct equivalents to a standard accessible component kit**: icon, button, link, input, textarea, select, checkbox, radio (+ group), toggle, file input, range slider, breadcrumb, tabs, pagination, steps (+ title), dropdown, card (+ group), badge, avatar (+ group), accordion, blockquote, alert, toast (+ region), modal (default / serious / language), tooltip, popover, banner, header (with mega menu), footer, hero (slider / static).

**Composed from primitives, no direct equivalent**: combobox, sidebar, data table, KPI tile, description list, timeline, status pill (a badge variant), drawer, progress, spinner, skeleton, empty state, error page, page header, button loading state.

**Not built yet**: a full date picker beyond the native input, dark mode, filter/newsletter/team blocks.

## Dark theme (opt-in)

A separate stylesheet, `tokens-dark.css`, layers dark-mode values over the same component classes when a dark-mode attribute is set on the document root. It is never loaded by default. Intended for internal, data-dense command views only — the public website and product portal stay light, and a page is never toggled between the two at runtime.

| Role | Light | Dark |
|---|---|---|
| Page background | white | `--ds-dark-bg-page` |
| Card / raised surface | `--ds-color-neutral-50` | `--ds-dark-bg-card` / `--ds-dark-bg-raised` |
| Border | `--ds-color-neutral-100` | `--ds-dark-border` |
| Body text | `--ds-color-neutral-800` | `--ds-dark-text` |
| Muted text | `--ds-color-neutral-500` | `--ds-dark-text-muted` |
| Accent | `--ds-color-gold-500` | `--ds-dark-accent` (lighter step, 6.9:1 on the dark ground) |
| Focus ring | amber | `--ds-dark-focus` |

Status badges keep their own dark tints (a deep version of each semantic hue with a light-tinted foreground) rather than reusing the light-mode badge colours directly, so they stay readable against the dark surfaces. The product's mark always sits on a white patch, never directly on a dark surface.

## Accessibility and bilingual rules (short form)

Direction and language switch together at the document root; fonts and layout follow automatically. Language switching uses a dedicated dialog, not an inline toggle. Every interactive element shows a visible focus ring; touch targets are at least 40px (48px as the base size); the layout tolerates zoom to 175% without overlap.
