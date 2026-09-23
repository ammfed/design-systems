# Product UI: guidelines

Version 2.0.0. The rules behind `tokens.css`, `tokens-dark.css`, `motion.css` and `materials.css`. `preview.html` shows every system here working in both themes.

## Colour

Components read **roles**, never palette steps. A role says what a colour means; the dark theme re-points roles and nothing else, so a component written once works in both themes.

### Roles

| Role | Tokens | Use |
|---|---|---|
| Surface | `--ds-surface-canvas`, `-sunken`, `-base`, `-raised`, `-float`, `-overlay` | The page, wells (sidebar, table head), cards and panels, then the three materials under Depth |
| Surface states | `--ds-surface-hover`, `-pressed`, `-inverse`, `-veil`, `--ds-scrim` | Row and item states; tooltips and the bulk-action bar; sticky chrome; behind modals |
| Ink | `--ds-ink`, `-strong`, `-muted`, `-inverse`, `-disabled` | Text and icons. Disabled ink only ever sits with a disabled control |
| Line | `--ds-line`, `-strong`, `-float` | Hairlines (decorative); control edges, chart axes, connectors and tracks that must be seen (3:1); float edges |
| User | `--ds-user`, `-hover`, `-pressed`, `-on`, `-soft`, `-ink`, `-line` | The user's one primary action, their choices, where they are |
| Ink action | `--ds-ink-action`, `-hover`, `-on` | Every action that is not the user's one primary step |
| Machine | `--ds-machine`, `-ink`, `-soft`, `-line`, `-bar` | Content a model produced, progress, activity, data series 1 |
| Status | `--ds-{success,info,warning,error}-{fg,soft,solid,on,line}` | Status and feedback only, never decoration |
| Focus | `--ds-focus`, `--ds-focus-inverse`, `--ds-focus-width`, `--ds-focus-offset` | One ring, matched to the surface it sits on |
| Data | `--ds-data-1` to `-4`, `-user`, `-pos`, `-neg`, `-grid`, `-track` | Charts |

### The user and the machine

- **The accent is the user's colour, never structure.** It marks their one primary action per view, what they chose (a selected row, a checked box, the current step, a chosen chip, segment or day), where they are (the current nav item, the tab bar, the current page) and their own value in a chart. Links, borders, rules, counts, card edges, charts in general and activity are ink or the machine.
- **The machine has its own colour.** Anything a model produced carries the machine rule and chip, so it is never mistaken for the user's choice or for something a user entered. While it is working, a 2px bar sweeps under the content.
- **Secondary actions are ink.** Solid, soft, outline and link buttons all come in ink; links are ink and underlined. One solid accent button per view.
- **Status colours are for status.** Success, info, warning and error each come as soft (a ground plus text) and solid (a fill plus text), with a line colour for the inline-start bar of an alert.
- **Data: four series, then "other".** Series 1 is the machine colour; series 4 is the neutral used for comparison, previous period and target. The accent marks the user's own value or series: their own reading over time, or against their own target, never a place in a ranking. Positive and negative colours are for signed deltas only, and always sit with a sign and a word or icon, never colour alone.

### Contrast

Every text, control, focus and chart pair, measured from the token values in both themes. WCAG 2.2 AA asks for 4.5:1 for text and 3:1 for control edges, focus indicators and meaningful graphics. Every pair below passes. The lowest text pairs are 4.50 (light, the primary button) and 4.65 (dark, secondary text on a pressed row); the lowest non-text pair is 3.76 (dark, a control edge on a card). Translucent surfaces are measured after compositing over the surface under them.

Text (needs 4.5:1)

| Use | Pair | Light | Dark |
|---|---|---|---|
| Body text | `ink` on `surface-base` | 15.37 | 11.94 |
| Body text on the page | `ink` on `surface-canvas` | 14.98 | 13.12 |
| Body text in a well | `ink` on `surface-sunken` | 14.34 | 14.89 |
| Headings | `ink-strong` on `surface-base` | 16.88 | 14.34 |
| Secondary text | `ink-muted` on `surface-base` | 5.95 | 6.00 |
| Secondary text in a well | `ink-muted` on `surface-sunken` | 5.55 | 7.48 |
| Secondary text on a hovered row | `ink-muted` on `surface-hover` | 5.31 | 5.16 |
| Secondary text on a pressed row | `ink-muted` on `surface-pressed` | 5.08 | 4.65 |
| Secondary text in a menu | `ink-muted` on `surface-float` | 5.95 | 5.32 |
| Body text on a chosen row | `ink` on `user-soft` | 14.31 | 12.08 |
| Secondary text on a chosen row | `ink-muted` on `user-soft` | 5.54 | 6.06 |
| Tooltip text | `ink-inverse` on `surface-inverse` | 15.75 | 13.12 |
| Primary button | `user-on` on `user` | 4.50 | 7.12 |
| Primary button, hover | `user-on` on `user-hover` | 6.03 | 9.08 |
| Accent text | `user-ink` on `surface-base` | 6.03 | 10.69 |
| Text on a chosen item | `user-ink` on `user-soft` | 5.61 | 10.81 |
| Secondary button | `ink-action-on` on `ink-action` | 14.34 | 13.12 |
| Machine text | `machine-ink` on `surface-base` | 6.87 | 9.76 |
| Machine chip | `machine-ink` on `machine-soft` | 6.47 | 8.41 |
| Success, soft | `success-fg` on `success-soft` | 6.41 | 9.82 |
| Success, solid | `success-on` on `success-solid` | 6.80 | 7.17 |
| Info, soft | `info-fg` on `info-soft` | 6.12 | 8.21 |
| Info, solid | `info-on` on `info-solid` | 6.74 | 5.84 |
| Warning, soft | `warning-fg` on `warning-soft` | 4.82 | 10.39 |
| Warning, solid | `warning-on` on `warning-solid` | 5.30 | 10.09 |
| Error, soft | `error-fg` on `error-soft` | 5.91 | 8.70 |
| Error, solid | `error-on` on `error-solid` | 4.66 | 6.34 |
| Error message | `error-text` on `surface-base` | 6.46 | 5.77 |
| Error word on the inverse surface | `error-on-inverse` on `surface-inverse` | 9.14 | 5.02 |

Controls, focus and charts (needs 3:1)

| Use | Pair | Light | Dark |
|---|---|---|---|
| Control edge, chart axis | `line-strong` on `surface-base` | 4.08 | 3.76 |
| Control edge, chart axis in a well | `line-strong` on `surface-sunken` | 3.81 | 4.69 |
| Focus ring | `focus` on `surface-base` | 5.00 | 7.13 |
| Focus ring in a well | `focus` on `surface-sunken` | 4.67 | 8.89 |
| Focus ring on a chosen item | `focus` on `user-soft` | 4.66 | 7.21 |
| Focus ring on the inverse surface | `focus-inverse` on `surface-inverse` | 7.83 | 3.89 |
| Checked control, selection bar | `user` on `surface-base` | 4.50 | 6.48 |
| Selection edge | `user-line` on `user-soft` | 4.19 | 6.56 |
| Progress, activity | `machine` on `surface-base` | 5.20 | 8.05 |
| Series 1 | `data-1` on `surface-base` | 5.20 | 8.05 |
| Series 2 | `data-2` on `surface-base` | 6.32 | 6.24 |
| Series 3 | `data-3` on `surface-base` | 6.74 | 5.32 |
| Series 4, comparison | `data-4` on `surface-base` | 5.95 | 6.00 |
| The user's own value | `data-user` on `surface-base` | 4.50 | 6.48 |
| Positive delta | `data-pos` on `surface-base` | 4.04 | 6.53 |
| Negative delta | `data-neg` on `surface-base` | 4.66 | 5.77 |

`--ds-line` (1.29:1 light, 1.48:1 dark) and `--ds-line-float` (1.29:1 light, 1.66:1 dark) are decorative: they separate things that are already distinct by position or content. Anything a user has to find to operate or to read off a chart (an input's edge, a checkbox, a toggle track, an axis, a connector) uses `--ds-line-strong`.

Under `prefers-contrast: more`, both themes take the two decorative line roles to the control-edge step and muted text to full ink, so every separator reads as strongly as a control edge.

| Use | Pair | Light | Dark |
|---|---|---|---|
| Hairline | `line` on `surface-base` | 4.08 | 3.76 |
| Hairline in a well | `line` on `surface-sunken` | 3.81 | 4.69 |
| Float edge | `line-float` on `surface-float` | 4.08 | 3.34 |
| Secondary text | `ink-muted` on `surface-base` | 15.37 | 11.94 |

## Dark theme

- **Opt-in.** Light is the default. Load `tokens-dark.css` after `tokens.css` and set `data-ds-theme="dark"` on `<html>`. The attribute works on any region too, for a dark panel inside a light page.
- **Switched from a display menu,** with two icons (sun, moon) rather than words, next to the density choice. The switch cross-fades through `document.startViewTransition` (`motion.css`), and instantly under reduced motion. Remember the choice. Light stays the default whatever the operating system prefers; dark is something the user picks.
- **Palette steps only.** Surfaces keep near-black values; floating layers lift with a faint white tint and a lit top rim rather than a lighter swatch. Status grounds use each hue's darkest step and its text a light step.
- **The accent moves to a lighter step** and text on it turns dark, so a primary button stays 7.12:1.
- **Photographs sit back** a little on dark (about 92% brightness). A logo or mark is never dimmed and always sits on a white patch, never directly on a dark surface.

## Type

Two families per direction: a heading family and a body family, swapped for a matching pair in RTL. Fonts are referenced by family name with a generic fallback; nothing is shipped.

### Roles

Ten named roles. Every size is one of the fixed steps in `tokens.css` or moves between two of them. Fluid roles grow from a 360px to a 1280px viewport; reading sizes stay put. No role grows more than 1.6 times, well inside the 200% text-resize requirement, and the rem term keeps browser zoom working.

| Role | Size (px) | Leading | Weight | Use |
|---|---|---|---|---|
| `display` | 48 to 76 | 1.05 | 200 | Public website hero only |
| `headline` | 32 to 48 | 1.15 | 800 | Page title on a public page |
| `title-1` | 26 to 32 | 1.2 | 700 | Page title in a product screen |
| `title-2` | 20 to 26 | 1.25 | 700 | Section and panel titles |
| `title-3` | 20 | 28 | 600 | Card titles, dialog titles |
| `figure` | 32 to 40 | 1.1 | 700 | KPI values, tabular figures |
| `lead` | 18 to 20 | 1.6 | 400 | The one paragraph under a page title |
| `body` | 16 | 24 | 400 | Everything else; 1.5 in paragraphs |
| `label` | 16 | 24 | 500 | Buttons, fields, table heads, nav items |
| `meta` | 14 | 20 | 400 | Timestamps, table footers, chart ticks, helper text |

- **Nothing is small unless it earns its place.** Body never drops below 16px. `meta` (14px) is the only smaller role and is listed above by use; nothing is 12px.
- Numbers use `--ds-type-numeric` (tabular, lining) wherever they line up: tables, KPIs, charts, dates.
- Latin (Western) digits in both languages, including dates and charts formatted through `Intl`.
- Large type tightens slightly (negative tracking); body and labels are untracked.
- **RTL:** the families swap, tracking goes to zero on every role (letter-spacing breaks joined scripts) and leading opens up (body 28px, paragraphs 1.7).
- Keep body copy near a 68-character measure (`--ds-measure`). Align to the start edge; never justify.

## Density

Three modes, set with `data-ds-density` on `<html>` or on any region; comfortable is the default. Density changes space and control height, never the text size, and no mode goes under the 40px target.

| Token | Compact | Comfortable | Spacious |
|---|---|---|---|
| `--ds-control-height` | 40 | 48 | 56 |
| `--ds-row-height` | 44 | 52 | 64 |
| `--ds-panel-pad` | 16 | 24 | 32 |
| `--ds-stack-gap` | 16 | 24 | 32 |
| `--ds-cluster-gap` | 8 | 12 | 16 |
| `--ds-nav-item-height` | 40 | 48 | 56 |
| `--ds-appbar-height` | 56 | 64 | 72 |
| `--ds-icon-size` | 20 | 24 | 24 |

Compact is for long tables and data-dense views, comfortable for product screens, spacious for public forms, touch and kiosks. The user chooses it from the display menu, as icons.

A control that holds other controls still measures `--ds-control-height` overall: the segmented control gives up its own padding to fit, down to zero in compact, and draws its edge inset so the edge costs no height. The buttons inside it clear the 40px target in every density.

## Depth and materials

Flat by default: canvas, sunken and base are separated by 1px lines, not shadows. Depth is earned only by layers that sit over others.

| Level | Class | Shadow | Use |
|---|---|---|---|
| Flat | none | none | The page, wells, cards and panels at rest |
| Raised | `.ds-material-raised` | `--ds-elevation-raised` | A hovered interactive card, a sticky table head |
| Float | `.ds-material-float`, `.ds-material-float-inverse` | `--ds-elevation-float` | Menus, popovers, toasts, pickers, the command menu; the inverse class for a tooltip and the bulk-action bar |
| Overlay | `.ds-material-overlay` | `--ds-elevation-overlay` | Modal and drawer, over `--ds-scrim` |
| Veil | `.ds-material-veil` | none | Sticky chrome (app bar, table head) over scrolling content |

- **Float comes in two surfaces.** `.ds-material-float` for anything on the base surface; `.ds-material-float-inverse` for the two components that sit on `--ds-surface-inverse`, a tooltip and the bulk-action bar. It carries the inverse surface with `--ds-ink-inverse` on it (15.75:1 light, 13.12:1 dark) and the same float shadow, so neither component has to hand-roll one, and the inverse fill is its own edge against every page surface in both themes.
- Shadows are two layers (a tight contact shadow and a soft ambient one) in the darkest neutral, never pure black in light and never tinted with the accent.
- In dark, shadows deepen and every raised layer gets a lit top rim (`--ds-rim`) and a faint white tint, so depth still reads where a shadow barely shows.
- Filled controls carry the same 1px lit rim in both themes.
- **Translucency only where it stays legible.** The veil is 90% opaque with a 16px blur, used only for sticky chrome; secondary text on it stays at 4.64:1 or better in light and 4.94:1 or better in dark, even with pure black or pure white scrolling behind it. It falls back to a solid surface when blur is unsupported, under `prefers-reduced-transparency`, and in forced colours. Menus, dialogs and cards are always solid.
- Never a shadow on a logo or wordmark.

## Motion

Motion only tells the user that something changed, where it came from, or that the machine is working. Nothing animates on page load in product screens; a small staggered reveal is kept for the public website hero only.

| Token | Value | For |
|---|---|---|
| `--ds-duration-feedback` | 120ms | Hover and press recolour |
| `--ds-duration-state` | 200ms | Toggles, checks, the glide of a selection marker |
| `--ds-duration-float-in` / `-out` | 240 / 160ms | Menus, popovers, tooltips, pickers |
| `--ds-duration-panel-in` / `-out` | 360 / 240ms | Drawers, modals, the scrim |
| `--ds-duration-data` | 640ms | A changed value settles |
| `--ds-duration-reveal` | 480ms | Website hero only, stagger 40ms, at most six steps |
| `--ds-ease-standard` | (0.4, 0, 0.2, 1) | Colour and state changes |
| `--ds-ease-enter` | (0.22, 1, 0.36, 1) | Things arriving decelerate |
| `--ds-ease-exit` | (0.4, 0, 1, 1) | Things leaving accelerate |
| `--ds-ease-data` | (0.65, 0, 0.35, 1) | Values settling |

The six transitions in `motion.css`:

1. **Feedback** (`.ds-t-feedback`): hover and press recolour a control. Never scale.
2. **Float** (`.ds-float-enter`, `.ds-native-float`): menus and popovers fade in and rise 6px from their anchor; they leave faster than they came.
3. **Panel** (`.ds-panel-enter`, `.ds-modal-enter`, `.ds-scrim-enter`): drawers slide in from the inline-end edge, modals rise 12px, the scrim fades.
4. **Glide** (`.ds-glide`): the user's marker (the tab bar, a segment thumb, the sidebar bar) travels to the new choice.
5. **Settle** (`.ds-settle`): a bar, ring or progress eases to its new value when data changes. The first paint is static.
6. **Sweep** (`.ds-sweep`): a 2px machine bar while a model is producing content; `.is-done` stops it.

**Reduced motion.** Under `prefers-reduced-motion: reduce`, or `data-ds-motion="reduce"` set by the product, the tokens zero every travel and settle; floats and panels become 120ms fades; the sweep, the one loop here, stops. Colour feedback stays. A product that adds a loop of its own, a spinner or a skeleton shimmer, stops it the same way.

## Interaction states

- **Hover moves one step inside the same role.** A filled control takes its hover step (`--ds-user-hover`, `--ds-ink-action-hover`, `--ds-error-solid-hover`); a soft or ghost button, a row and a menu item all take `--ds-surface-hover`, and a soft danger button takes `--ds-error-soft-hover`. The fill darkens, so text on it gets stronger rather than weaker (`user-on` on `user-hover` is 6.03 light, 9.08 dark).
- **Press is colour only,** one step further again (`--ds-user-pressed`, `--ds-surface-pressed`, `--ds-error-solid-pressed`), over `--ds-duration-feedback`. Nothing scales, lifts or bounces.
- **Links are ink and underlined at rest.** Hover moves them to `--ds-ink-action-hover` and thickens the underline; the underline never appears or disappears on hover alone.
- **Disabled:** text and icons drop to `--ds-ink-disabled`, the surface stays, the control takes no pointer or keyboard interaction, and `aria-disabled` carries it. This is the one ink outside the contrast table, because WCAG exempts inactive controls, which is also why a disabled control is never the only explanation: say what would enable it, or leave it enabled and explain on submit.
- **Chosen is not hovered.** A selected row, chip or segment keeps `--ds-user-soft` and its `--ds-user-line` edge while the pointer is over it, so a choice and a pointer never read as the same state. That is why the accent soft step has no hover step at all: every surface it can land on is already a chosen one.
- Every state is announced as well as coloured: `aria-pressed`, `aria-checked`, `aria-current` and `aria-expanded` carry what the colour shows.

## Focus and targets

- One ring, matched to the surface it sits on: 2px solid `--ds-focus`, offset 2px, on `:focus-visible` only. Soft controls use offset 0; rows, menu items and segments draw it inset (-2px) so it is never clipped.
- On the inverse surface, `.ds-material-float-inverse` re-points the ring to `--ds-focus-inverse`, the other theme's step, so a tooltip and the bulk-action bar get a ring that clears 3:1 (7.83 light, 3.89 dark) without a rule of their own. It is the same ring, one step along the same hue, never a second colour.
- The ring colour is distinct from the user's accent, so focus is never confused with selection, and passes 3:1 on every surface it can land on (table above).
- Sticky chrome never covers the focused element or its ring: `scroll-padding-top` reserves the app bar or a sticky table head, plus the ring's width and offset. A table that scrolls inside its own frame needs this on the frame; a value on the page does not reach it.
- **Targets:** 40px for every stand-alone control (`--ds-target-min`) in every density; 24px only for an inline icon button inside a chip or badge, with 8px clear space. Pagination pages and dismiss buttons are 40px.
- Dialogs and drawers trap focus, close on Esc and return focus to what opened them.

## RTL and mirroring

- Direction and language switch together at the document root; fonts, tracking and leading follow automatically.
- A region with its own `dir` inside a page of the other direction re-points the whole set on itself, in either direction: the two families, every tracking and leading that changes with the script, and `--ds-dir`. It still needs `font-family: var(--ds-font-body)` on that region (for example `:where([dir]:not(html, bdi)) { font-family: var(--ds-font-body); }`): an inherited font-family keeps the outer value and does not pick up the swapped token.
- Layout uses logical properties only (inline-start/end, block-start/end), never left and right.
- Motion mirrors too: every horizontal travel (a toggle thumb, a progress fill, a drawer, the tab bar, a segment thumb, an indeterminate bar) multiplies by `--ds-dir` (1 in LTR, -1 in RTL).
- Directional icons (arrows, chevrons, "next") flip; functional icons (search, user, bell, check) do not.
- Numbers stay Latin and left-to-right inside RTL text. Isolate signed and mixed values (`<bdi dir="ltr">`) so "+9" never reads "9+".
- The language switch names the other language in its own script.

## Spacing, grid, radii

4px base unit. Common gaps: 8 (button group), 16 (toast, small card), 24 (card padding, section stack, grid gap), 28 (large card). Six-column grid, 24px gutter, container widths tiered by breakpoint (roughly 1480 / 1240 / 980 / 740 / fluid).

Content sits inside a per-section container, never one page-wide wrapper, so a full-bleed band can carry its own background while its text still lines up with the section above it. Screens are written mobile-first and gain columns as the container grows. Under roughly 1024px the product sidebar collapses to its rail and the public website's navigation collapses to a menu; panels and KPI tiles restack on their own container's width, not the viewport's.

Radius roles: 8 for controls, 12 for panels and overlays, full for chips, segment thumbs and pagination. Nested corners: the inner radius is the outer radius minus the padding between them. The fixed scale (4, 6, 8, 12, 16, full) stays for badges, checkboxes and small buttons.

## Backgrounds and imagery

- Surfaces are flat. The only gradients in the system are the thin accent bar in the public website header and footer, the machine's working bar (`--ds-machine-bar`), a progress fill and the protection overlay on an image.
- A subtle line pattern may sit behind the public website hero, always under a protection fade so type keeps its measured contrast. Product screens carry no pattern.
- Photography is real and naturally lit, on simple backgrounds, with a dark overlay (never a coloured one) under any text. Photographs sit back a little in dark, about 92% brightness.
- A small set of fixed aspect ratios, reused everywhere, rather than a one-off crop per page.
- Illustration is geometric and solid-colour, drawn from the same roles as everything else. No photographic collage and no stock-photo look.
- A real screenshot or a worked example beats an invented illustration wherever either would do.

## Components

### Inventory

- **Actions:** button (solid, soft, outline, link; accent only for the one primary step, ink for the rest; loading state), icon button (with pressed and expanded states and a notification dot), link.
- **Forms:** input, textarea, select, combobox (marks the chosen option), checkbox (with a mixed state), radio group, toggle, file input, range slider, **date picker and calendar**, and errors at 16px with an icon beside the field.
- **Navigation:** breadcrumb, tabs (a gliding bar) and pill tabs, **segmented control**, pagination, steps, dropdown menu (arrow keys, danger items), sidebar with a collapsible icon rail, **app bar**, **command menu** (Ctrl or Cmd K).
- **Data display:** card, badge, avatar, accordion, blockquote, **table** (see below), KPI tile, description list, timeline, status pill, **chip** (toggle and applied), **filter bar**, **panel**.
- **Dashboards:** bar chart, **progress ring** (one value closing toward its goal, never a donut or pie), sparkline, **chart legend**, **insight** (the machine's reading of the data).
- **Feedback:** alert, toast (machine tone, action, timed dismissal that pauses), modal (default, serious, language), tooltip, popover, banner, drawer, progress (determinate and indeterminate), spinner, skeleton, empty state, error page, **bulk-action bar**.
- **Layout blocks:** header with mega menu, footer and hero for the public website.

### Tables

- A caption (visible or not), one line per row by default with opt-in wrapping, tabular figures, numbers aligned to the end.
- Row height follows density. The head is sticky under the veil when the table scrolls inside its own frame; the frame is focusable and labelled so keyboard users can scroll it.
- The first column can be pinned, with an edge that appears only while content scrolls beneath it. The first plain column is a row header for screen readers.
- Sortable columns announce their sort. Selection uses a checkbox column with a mixed select-all state; chosen rows take `--ds-user-soft` and an inline-start edge in `--ds-user-line`.
- Row actions appear on hover and on focus within the row, never hover only, and stay visible where the pointer cannot hover (`hover: none` or a coarse pointer), so a touch user sees the target they can already hit. With a selection, the bulk-action bar appears on the inverse surface with a count read out politely and a clear action.
- Loading shows skeleton rows at the current row height; empty states say what will appear and how to add it.

### Dashboards

- A KPI tile says what moved, by how much, and whether that is good: the value in `figure`, a signed delta isolated for RTL, a direction that can be good or bad, and an optional target meter. Tiles stack their parts in narrow containers (a container query, not the viewport).
- Charts: ticks at round values, a one-sentence summary for screen readers, and values that settle when they change. A legend key repeats the mark it labels in the same shape, so a reader can match the two, and whatever the colour separates carries a second cue on the chart itself: the user's own bar is named by its own axis label. The accent marks the user's own value: their own series over time, or their own reading against their own target.
- **Never a comparison across people.** Progress and state are self-referential. A chart does not rank one person, or one team, against another, and a target is the user's own, not someone else's result.
- **A progress ring, never a donut or a pie.** The ring carries one value closing toward its goal with the number in the middle. Length on a shared baseline is read accurately and angle is not, so a comparison across categories is labelled horizontal bars, every time. No gauges.
- The insight block holds the machine's reading, marked with the machine rule and disc, with its actions beside it; its text is announced when it finishes.
- A panel groups a chart or list with a title, a short sub-line and actions, and can run flush for tables.

### Navigation and shell

- The app bar holds the mark on its white patch, the product name, a search field that opens the command menu (with its shortcut shown), notifications, the display menu (theme and density as icons), the language switch and the user's avatar. It is sticky under the veil. The public website keeps its header with a thin accent bar; product screens have none.
- The sidebar collapses to a 72px rail with tooltips. The current item carries the accent bar.
- Dropdowns and the command menu move with arrow keys, Home and End, and close on Esc back to their trigger.

### Forms

- The date picker takes typed dates (DD/MM/YYYY, with `/`, `.` or `-`) and a calendar grid that starts on Monday, moves with arrow keys, Page Up and Page Down (Shift for a year), and strikes out disabled days. Alt and Down opens it; focus returns to the field.
- Errors sit under the field at 16px with an icon, say what to do next, and are tied to the field for screen readers.
- Mark optional fields, never required ones.

## Content

- Voice: professional, accessible, plain; speak to the user, not at them. "You/your" for the user, "we" for the product or organisation.
- Sentence case everywhere. Buttons use a verb, under four words.
- **Rates as a natural frequency first:** "43 of 50" before "86%". Give the percentage after it, never instead of it: a count the reader can verify is read correctly far more often than a bare rate.
- Errors and empty states in plain language, no codes, no blame.
- Full, natural translation for the second language, not transliteration.
- No emoji, no taglines, no filler text. Modes and view options are icons with accessible names, not worded buttons.
