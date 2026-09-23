# Product UI

A UI system for product dashboards, work queues and public service websites: flat, quiet surfaces, one warm accent that belongs to the user, a separate colour for what a model produced, full bilingual LTR/RTL support, and WCAG 2.2 AA in both a light theme (the default) and an opt-in dark theme. It shares its visual language with the other two systems here, expressed as tokens and rules for reusable components.

Version 2.0.0. See `CHANGELOG.md` for what changed and how to move from 1.x.

## Use it

```html
<link rel="stylesheet" href="tokens.css">
<link rel="stylesheet" href="tokens-dark.css">   <!-- optional: the dark theme -->
<link rel="stylesheet" href="motion.css">        <!-- optional: the named transitions -->
<link rel="stylesheet" href="materials.css">     <!-- optional: depth classes -->

<html data-ds-theme="dark" data-ds-density="compact" data-ds-motion="reduce" dir="rtl">
```

Every attribute is optional and works on any region as well as `<html>`: light, comfortable density and full motion are the defaults, and `prefers-reduced-motion` is honoured without the attribute. Components read the role tokens (`--ds-surface-*`, `--ds-ink-*`, `--ds-user-*`, `--ds-machine-*` and so on), never the palette steps, so they follow the theme with no extra rules. Open `preview.html` to see all of it at once, in both themes side by side.

## Visual foundations

**Colour by role.** Surfaces, ink, lines, status, focus and data are named by what they mean. The warm accent is the **user's colour**: their one primary action per view, what they chose, where they are, and their own value in a chart (their own series over time, or against their own target, never a ranking against other people). It is never used for structure: links, borders, rules, card edges and charts in general are ink or the machine colour. Anything a model produced carries the **machine** colour (a cool cyan), so it is never mistaken for the user's choice. Status colours are for status only.

**Contrast, shown.** Every text, control, focus and chart pair meets WCAG 2.2 AA in both themes. `guidelines.md` lists each pair with its ratio in light and dark; the lowest text pair is 4.50:1 and the lowest control edge 3.76:1.

**Dark theme (opt-in).** A complete counterpart, not a partial one: `tokens-dark.css` re-points every role under `data-ds-theme="dark"`. Light stays the default; the user switches from a display menu with icons, and the page cross-fades. Palette steps only, no one-off tints. Floating layers lift with a faint tint and a lit rim. A logo or mark always sits on a white patch.

**Type by role.** Ten named roles (display, headline, three titles, figure, lead, body, label, meta) on the same two families per direction. Headings grow fluidly with the viewport; reading sizes stay put. Body never drops below 16px, and only `meta` (14px) is smaller. Numbers are tabular and Latin in both languages. In RTL the families swap, tracking goes to zero and leading opens up.

**Density.** Compact, comfortable and spacious modes change control height, row height and padding, never text size, and never go under the 40px target.

**Depth and materials.** Flat by default, with 1px lines between canvas, wells and cards. Only layers that sit over others get depth: raised, float and overlay, each a two-layer shadow, with a lit rim in dark. Float comes in a base and an inverse surface, so a tooltip and the bulk-action bar take the same shadow without hand-rolling one. Translucency is kept to sticky chrome (a 90% veil with blur), with a solid fallback under reduced transparency and forced colours.

**Motion.** Six named transitions: feedback, float, panel, glide, settle and sweep. Durations are named by what moves and easings by direction. Nothing animates on page load in product screens. Reduced motion (the OS setting or `data-ds-motion="reduce"`) removes every travel, stops the sweep, and keeps short fades and colour feedback.

**States.** Hover moves a control one step inside its own role, press goes one step further in colour alone, and a disabled control drops to `--ds-ink-disabled`, keeps its surface and takes no interaction. Nothing scales or bounces.

**Layout.** Content lives in a per-section container, never one page-wide wrapper. Mobile-first: under roughly 1024px the sidebar collapses to its rail and the website navigation collapses to a menu, and panels restack on their own container width.

**Focus, targets, RTL.** One 2px focus ring, distinct from the accent, on `:focus-visible`, matched to the surface it sits on (the inverse surface takes the other theme's step so the ring still clears 3:1). 40px targets in every density. Layout uses logical properties only, and every horizontal travel in motion mirrors in RTL through `--ds-dir`.

**Backgrounds and imagery.** Flat surfaces. No textures or gradients, except the thin accent bar in the public website header and footer, the machine's working bar, a progress fill and an image overlay. A subtle line pattern may sit behind the public website hero only, under a protection fade. Real, naturally lit photography with a dark overlay under any text; photographs sit back slightly in dark. A small set of fixed aspect ratios, and geometric, solid-colour illustration only, never a photographic collage.

## Content rules

- Voice: professional, accessible, plain, speaking to the user directly, not at them.
- "You/your" for the user, "we" for the product or organisation. Example: *"We sent a confirmation to your email."*
- Sentence case everywhere: headings, buttons, labels, navigation.
- Buttons use actionable verbs, under four words: *Submit application*, *Save draft*, *Start*. One solid accent button per view, the rest ink.
- Mark optional fields, never required ones. Error copy states what to do next, not just what went wrong.
- Errors and empty states in plain language, no error codes, no blame: *"No requests yet. Requests you submit will appear here."*
- Full, natural translation for the second language, not transliteration.
- No emoji, no taglines, no filler text. Modes and view options are icons with accessible names.

## Iconography

One outline icon family in three weights (regular for interface icons, bold for confirmations, filled for a selected state and for empty-state illustrations), 24px by default and 20px in compact density, inheriting the text colour. Directional icons flip in RTL; functional ones do not. No emoji, no bitmap icons.

## Components

Actions, forms (including a date picker and calendar), navigation (including an app bar, segmented control and command menu), data display (a full table with sticky head, pinned column, selection, row and bulk actions and loading rows; chips, filter bar, panels), dashboards (KPI tile, bar charts, a progress ring, sparkline, chart legend, the machine's insight block), feedback (alerts, toasts, dialogs and drawer with focus trapping, progress, skeletons, the bulk-action bar) and public website blocks (header, footer, hero). The full inventory and the rules for each group are in `guidelines.md`.

## Files

```
tokens.css        palette, colour roles, type roles, spacing, radii, targets, depth, motion, density, reduced motion, higher contrast
tokens-dark.css   the opt-in dark theme: re-points the colour roles and depth, with its higher-contrast pair
motion.css        the six named transitions and the reduced-motion path for the sweep
materials.css     the raised, float (base and inverse), overlay and veil materials, with fallbacks
guidelines.md     the rules in full: roles, the contrast table, dark theme, type, density, depth, motion, states, focus, RTL, layout, imagery, components
preview.html      one page showing every token system and the key components, light and dark side by side; it links the four stylesheets beside it and fetches nothing
CHANGELOG.md      dated changes to this system, and the 1.x to 2.0 migration
```
