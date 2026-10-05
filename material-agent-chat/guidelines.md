# Material Agent Chat: guidelines

Version 1.0.0. The rules behind `tokens.css`, `tokens-dark.css` and `motion.css`. `preview.html` shows them in use.

## Who decides what

The system mixes three layers. When two of them disagree, the higher one wins.

1. **The palette, type and icons** (this system's own): colour values, the type families and scale, the icon set, and the accessibility, content and light-page rules below.
2. **Material 3** sets everything else: layout, spacing, window size classes, shape, elevation, state layers, motion, the colour-role structure, the dark-scheme structure, and every component's anatomy.
3. **The chat framework** sets only where the assistant plugs in: its theme variables and its slots. Its chat parts are restyled in Material 3, never redesigned or replaced.

## Colour

### Roles

Components read the `--md-sys-color-*` roles only. The `--ds-ref-*` palette steps exist so the roles have something to point at.

| Role | Light | Dark | Use |
|---|---|---|---|
| `primary` | `#92722A` | `#CBA344` | The one filled button per view, the active indicator, a checked control, links |
| `primary-container` | `#F2ECCF` | `#5D3B26` | The person's own message, a FAB |
| `primary-accent` | `#B68A35` | `#B68A35` | An edge, an icon or large text only; never a fill under white words |
| `secondary` | `#3E4046` | `#D1D5DC` | The focus ring |
| `secondary-container` | `#E1E3E5` | `#364153` | Selected states: navigation indicator, selected filter chip, tonal button, selected row, the bulk-action bar |
| `tertiary` | `#0173AB` | `#76DBFF` | Sparing contrasting accents only |
| `error`, `error-container` | `#D83731`, `#FDE4E3` | `#F47A75`, `#7C2320` | Errors and destructive actions |
| `success`, `success-container` | `#2F663C`, `#E4F4E7` | `#A0D5AB`, `#24432B` | A done step, a saved record |
| `surface` | `#FFFFFF` | `#030712` | The page |
| `surface-container-low` to `-highest` | `#FCFCFC` to `#E1E3E5` | `#0E0F12` to `#364153` | Five tonal steps for things that sit above the page |
| `on-surface`, `on-surface-variant` | `#1B1D21`, `#4B4F58` | `#F1F5F9`, `#D1D5DC` | Text, then secondary text and icons |
| `outline` | `#797E86` | `#6A7282` | Every control edge |
| `outline-variant` | `#C3C6CB` | `#1E2939` | Dividers and card edges, decorative only |
| `inverse-surface`, `inverse-primary` | `#1B1D21`, `#D7BC6D` | `#F1F5F9`, `#7C5E24` | Snackbars and plain tooltips, and the action on them |
| `draft-container`, `draft-outline` | `#F9F7ED`, `#92722A` | `#361E12`, `#B68A35` | A value the assistant filled that the person has not confirmed |
| `chart-1` to `chart-6` | blues, amber, orange, magenta, slate | lighter steps of the same | Chart series, in this order |

The overall feel is warm and neutral: a lot of white and near-white, the accent kept for the one main action, the active indicator and the person's own words, and grey for everything structural. Selected states are grey (`secondary-container`), not accent, so the accent never piles up on a busy screen.

### Dark, opt-in

Load `tokens-dark.css` and set `data-ds-theme="dark"` (or a `.dark` class) on `<html>` or any ancestor. Light stays the default. The accent lightens and carries dark ink, surfaces step lighter as they rise, and every white on-colour becomes the darkest step of its own hue. Error, success and tertiary take the mirrored step of their light value (a 600 becomes a 400, a 700 a 300). The shadows deepen, because light shadows vanish on a near-black ground.

### Contrast

Every pair, computed from the token values by the WCAG 2.x formula. Text needs 4.5:1; control edges, the focus ring, icons and chart series need 3:1. Every pair passes in both themes.

| Use | Pair | Needs | Light | Dark |
|---|---|---|---|---|
<!-- CONTRAST:START -->
| Body text | `on-surface` on `surface` | 4.5 | 16.88 | 18.38 |
| Body text on the highest container | `on-surface` on `surface-container-highest` | 4.5 | 13.12 | 9.41 |
| Secondary text | `on-surface-variant` on `surface` | 4.5 | 8.21 | 13.67 |
| Secondary text on the highest container | `on-surface-variant` on `surface-container-highest` | 4.5 | 6.38 | 7.00 |
| Filled button | `on-primary` on `primary` | 4.5 | 4.50 | 6.56 |
| Primary text and links | `primary` on `surface` | 4.5 | 4.50 | 8.50 |
| The person's message | `on-primary-container` on `primary-container` | 4.5 | 8.34 | 8.34 |
| Selected item | `on-secondary-container` on `secondary-container` | 4.5 | 13.12 | 9.41 |
| Tertiary button | `on-tertiary` on `tertiary` | 4.5 | 5.20 | 8.42 |
| Tertiary container | `on-tertiary-container` on `tertiary-container` | 4.5 | 7.63 | 7.63 |
| Error text | `error` on `surface` | 4.5 | 4.66 | 7.56 |
| Error button | `on-error` on `error` | 4.5 | 4.66 | 6.04 |
| Error container | `on-error-container` on `error-container` | 4.5 | 8.21 | 8.21 |
| Success text | `success` on `surface` | 4.5 | 6.80 | 12.08 |
| Success container | `on-success-container` on `success-container` | 4.5 | 9.62 | 9.62 |
| Snackbar and plain tooltip | `inverse-on-surface` on `inverse-surface` | 4.5 | 16.45 | 16.20 |
| Snackbar action | `inverse-primary` on `inverse-surface` | 4.5 | 9.08 | 5.50 |
| Draft value | `on-surface` on `draft-container` | 4.5 | 15.72 | 14.19 |
| Draft note | `on-primary-container` on `draft-container` | 4.5 | 9.23 | 13.08 |
| Control edge (outline) | `outline` on `surface` | 3 | 4.08 | 4.16 |
| Control edge on a container | `outline` on `surface-container-high` | 3 | 3.65 | 3.03 |
| Focus ring | `secondary` on `surface` | 3 | 10.36 | 13.67 |
| Focus ring on the highest container | `secondary` on `surface-container-highest` | 3 | 8.05 | 7.00 |
| Focus ring on an inverse surface | `inverse-on-surface` on `inverse-surface` | 3 | 16.45 | 16.20 |
| Accent edge | `primary-accent` on `surface` | 3 | 3.15 | 6.40 |
| Draft outline on its tint | `draft-outline` on `draft-container` | 3 | 4.19 | 4.94 |
| Filled control on the page | `primary` on `surface` | 3 | 4.50 | 8.50 |
| Chart series 1 | `chart-1` on `surface` | 3 | 3.53 | 10.54 |
| Chart series 2 | `chart-2` on `surface` | 3 | 4.48 | 10.55 |
| Chart series 3 | `chart-3` on `surface` | 3 | 3.18 | 13.99 |
| Chart series 4 | `chart-4` on `surface` | 3 | 3.39 | 10.62 |
| Chart series 5 | `chart-5` on `surface` | 3 | 3.46 | 11.44 |
| Chart series 6 | `chart-6` on `surface` | 3 | 4.76 | 7.85 |
<!-- CONTRAST:END -->

Where a pair sits near its floor, keep it on the surface the table names. A control's edge goes on `surface` up to `surface-container-high`, never on `-highest` in dark (2.13:1 there). The light filled button and primary text sit exactly at 4.5:1, so never put them on a tinted container.

## Type

- **Families**: a sans heading family and a sans body family for left-to-right text; an Arabic heading family and an Arabic body family for right-to-left. Named in `tokens.css`, never shipped; every stack ends in a system fallback. Setting `dir="rtl"` on any element switches the families for that element and everything inside it.
- **Roles** are `font` shorthands: `font: var(--md-sys-typescale-body-large)`.

| Role | Size and line | Weight | Use |
|---|---|---|---|
| Display large, medium, small | 76/1.1, 62/1.1, 48/1.2 | 600, 800, 800 | Rare: a stat on a dashboard card |
| Headline large, medium, small | 40/1.2, 32/38, 26/34 | 800, 700, 700 | Page titles, the chat welcome line, dialog headlines |
| Title large, medium, small | 20/28, 18/24, 16/24 | 600 | App bar title, card and sheet titles, table titles, tab labels |
| Body large | 16/24 | 400 | Messages, the chat input, list headlines, form values |
| Body medium | 14/20 | 400 | Table cells, supporting text, dialog text |
| Body small | 12/16 | 400 | Field help, the disclaimer under the chat input |
| Label large | 14/20 | 500 | Buttons, chips, menu items, table headers |
| Label medium, small | 12/16 | 500 | Navigation rail labels, badges |
| Code | 13/20 | 400 | Tool details, inline and fenced code |

- **Nothing below 12px.** A count badge grows to 18px tall rather than shrink its number.
- Headings are heavy and tight; body is roomy. Tracking is slightly tight on display sizes, slightly open on labels, neutral elsewhere. Right-to-left text is never tracked.
- Sentence case everywhere. Tabular figures in tables. Digits stay Western in data in both languages, so exports match.

## Shape

The Material 3 scale: 0, 4, 8, 12, 16, 28 and full.

| Corner | Components |
|---|---|
| Full | Buttons, the search bar, badges |
| 28px | Dialogs, bottom sheets, the chat input |
| 16px | FAB, navigation drawer, floating side sheet, chat bubbles (the corner nearest the sender squared to 4px) |
| 12px | Cards, rich tooltips, result and approval cards in the chat |
| 8px | Chips |
| 4px | Text fields, menus, snackbars, plain tooltips |

## Elevation

Levels 0 to 5, shown mainly as a tonal surface and only lightly as a shadow: the elevated card level 1, menus level 2, dialogs, the FAB and snackbars level 3. The side sheet is level 0 with an `outline-variant` edge. No borders on cards except the outlined variant. No inner shadows, no glass, no blur, no gradients, no textures, no background images.

## States

- **State layers** in the content colour: hover 8%, focus 10%, pressed 10%, dragged 16%. Add `.md-state` from `motion.css` to paint them.
- **Disabled**: content at 38%, container at 12%. A disabled control that blocks progress says what unlocks it in its tooltip.
- **Focus**: a 3px `secondary` ring 2px outside the control, on keyboard focus only, always visible. On an inverse surface (a snackbar) the ring takes `inverse-on-surface` instead: set `data-ds-surface="inverse"` on that surface. Inside a list, a table or the chat input, the ring draws inward (`.md-focus-inset`) so its neighbours never cover it.
- No scale or colour shift on press.

## Motion

The Material 3 standard scheme, no overshoot and no bounce.

- **Easing**: standard `cubic-bezier(0.2, 0, 0, 1)` for most things; emphasised decelerate for things entering; emphasised accelerate for things leaving.
- **Durations**: short (50 to 200ms) for state layers and toggles, medium (250 to 400ms) for menus, sheets and dialogs, long (450 to 600ms) for large layout changes.
- **What moves**: a new message rises 8px and fades in (`.md-rise`); tooltips fade (`.md-fade-in`); a running step spins (`.md-spin`) only while it runs. Fades and short slides only. Nothing moves on an idle screen.
- **Reduced motion**: every duration drops to 1ms and the spinner stops. A state still changes; it just does not travel.

## Layout

- **Space** on 4px steps (`--md-sys-spacing-*`).
- **Window size classes**: compact under 600px, medium 600 to 839, expanded 840 to 1199, large 1200 to 1599, extra-large 1600 and up. Margins 16px on compact, 24px above; 24px between panes.
- **Canonical layouts**: list and detail for a dashboard; a supporting pane for a record with the chat beside it; a feed.
- **Fixed sizes**: navigation rail 80px, navigation drawer 360px, side sheet 400px, top app bar 64px, the full-page chat column 768px.
- **Targets**: 48px, or 40px in dense tables only.
- **Right to left**: logical properties only (`inset-inline`, `padding-inline`, `margin-inline-start`). The navigation rail and the chat sidebar sit on the leading edge: left in a left-to-right language, right in a right-to-left one. Arrows, chevrons, carets, the send icon and progress direction mirror; check marks, clocks, the microphone and rotation icons do not.
- **Any screen within three clicks**, with short formal navigation labels (Services, Approvals, Settings).

## Icons

- **One outline icon set in one weight.** The reference build uses Phosphor Icons, an open-source set under the MIT licence, at its Regular weight; install it from its official package and keep its licence with it. Any set with the same names and a regular, fill and duotone weight works. This repository ships no icon files.
- **Weights**: regular by default, so the stroke matches the text beside it. Fill only for a selected state (a selected navigation item, a toggled icon button). Duotone only for empty-state illustrations.
- **Sizes**: 24px standard inside a 40 to 48px target; 18px beside a button's words; 20px only where space forces it; 48px for a state icon; up to 80px for a page-wide empty state.
- **Colour**: `on-surface` or `on-surface-variant`, `primary` for emphasis, always 3:1 or better on its ground.
- **Never meaning alone**: every icon pairs with a word or carries an accessible name. No emoji and no text symbols used as icons.
- Common names: house, table, check square, chart bar, gear, bell, magnifying glass, sparkle (the assistant), paper plane (send), microphone, paperclip, plus, x, caret, three dots, copy, rotate, thumbs up and down, stop, check circle, warning circle, info, spinner.

## The chat framework

A typical chat framework exposes a small set of theme variables on its root element (background, foreground, card, popover, primary, secondary, muted, accent, destructive, border, input, ring, radius, sidebar width and a few chart colours). Fill them from the Material 3 roles; never set colours inside the framework's own parts.

| Framework variable | Material 3 role |
|---|---|
| background, foreground | `surface`, `on-surface` |
| card | `surface-container-low` |
| popover | `surface-container` |
| primary, primary foreground | `primary`, `on-primary` |
| secondary, secondary foreground | `secondary-container`, `on-secondary-container` |
| muted, muted foreground | `surface-container-highest`, `on-surface-variant` |
| accent (its hover fill) | `surface-container-high` |
| destructive | `error` |
| border, input | `outline-variant`, `outline` |
| ring | `secondary` |
| radius | 8px |
| sidebar width | 400px |

Slots, where the framework offers them:

| Slot | Fill it with |
|---|---|
| Header | The sidebar header: a centred title, conversations at the start, close at the end |
| Toggle button | A FAB with the sparkle icon |
| Assistant message, user message | The chat message, in each role |
| Suggestion | A suggestion chip |
| Input | The chat input, with a filled send icon button and a standard add-menu icon button |
| Disclaimer | One body-small line under the input |
| Welcome screen | The empty state of the sidebar or the full-page chat |
| Tool call | A result card, an approval card or agent progress |

Dark follows the same `.dark` ancestor the framework uses, so one token file serves both.

## Components

Every component exists in both directions and both themes, and uses Material 3 anatomy in this system's colour and type.

### Material 3 components

| Component | The rules here |
|---|---|
| Button | Filled (one per view), tonal (secondary emphasis), outlined and text (low emphasis), error (destructive). Pill, 40px (32px in dense tables), label large. Icons 18px, after the words; a back arrow stays in front. |
| Icon button | Standard, filled, tonal, outlined. 40px, 48px in touch layouts. Always named. A toggle switches its icon to the fill weight when selected. |
| FAB | The one promoted action on a screen, bottom trailing corner. `primary-container`, 16px corners, level 3. The assistant's launcher is a FAB with the sparkle icon. |
| Text field | Outlined by default (1px `outline`, 2px `primary` on focus), filled on `surface-container-highest`. 56px, 48px dense, 4px corners. The label floats to body small; help and error text are body small under the field. |
| Checkbox, radio, switch | 18px box, 20px ring, 52 by 32px track, each inside a 40px target. A switch for an immediate setting; a checkbox when the choice is saved with a form. |
| Chip | Assist, filter, input, suggestion. 32px, 8px corners, label large, outlined. A selected filter chip turns `secondary-container` with a leading check. |
| Menu | `surface-container`, level 2, 4px corners, 48px items (40px dense). Destructive items in `error`. |
| Card | Elevated (`surface-container-low`, level 1), filled (`surface-container-highest`), outlined (`surface` with an `outline-variant` edge). 12px corners. One card per idea, never nested. |
| List | 56, 72 or 88px for one, two or three lines; body large headline, body medium supporting text. Selected items on `secondary-container`; chevrons mirror. |
| Dialog | `surface-container-high`, 28px corners, level 3, up to 560px wide. Only for decisions that must interrupt. Focus is trapped and returns to the opener. Buttons are verbs, never OK or Yes. |
| Side sheet | 400px, `surface`, a 64px header with a title and close, an `outline-variant` edge. A modal sheet adds a scrim. |
| Snackbar | `inverse-surface` with `data-ds-surface="inverse"`, one line ending in a full stop, one optional action, 4px corners, level 3. It leaves after six seconds unless it has a close button. |
| Tooltip | Plain: `inverse-surface`, body small, up to 200px, names an icon. Rich: `surface-container`, level 2, 12px corners, a short subhead and line, stays while hovered. Shows on hover and on keyboard focus. |
| Badge | A count 18px tall or a 6px dot, `error` by default. Always has an accessible name (3 new). |
| Progress | A 4px linear bar on `surface-container-highest`, or a circle (48px, or 20 to 24px inside a button or row). Always labelled. |
| Top app bar | Small 64px with title large; medium and large put the title on a second row. Four or five actions at most; the rest in a menu. The title never collapses. |
| Navigation rail | 80px, three to seven destinations, a 56 by 32px `secondary-container` pill behind the selected icon, label medium under it. |
| Navigation drawer | 360px, 56px pill items, selected on `secondary-container` with the fill icon, counts at the end. |
| Tabs | Primary: a 3px `primary` indicator under the label. Secondary: a 2px full-width indicator. Arrow keys move between tabs, direction-aware. |
| Search bar | A 56px pill on `surface-container-high`, a leading icon, a clear button once there is text. Inside one table, use a text field with a search icon instead. |
| Divider | 1px `outline-variant`. Prefer space or a tonal container where it does the job. |

### Data components (no Material 3 spec, drawn in its style)

| Component | The rules here |
|---|---|
| Data table | A 56px header (label large, `on-surface-variant`), 52px rows (40px dense), body medium cells, `outline-variant` lines, 16px cell padding. Numbers aligned to the end with tabular figures. Sort arrows beside the header and `aria-sort` set. Selecting rows turns the toolbar into a `secondary-container` bulk bar with the count and its actions. Loading shows a linear bar and three skeleton rows; the empty state sits inside the table body. A pagination footer with rows per page and mirrored carets. |
| Filter bar | Search, then one filter chip per facet showing its chosen values; each opens a dense menu. Clear all appears only while a filter is on. |
| Empty state | A duotone icon (48px, up to 80px for a page), a title large headline, one body medium line, one action. What is empty, then what to do. |

### Agent surfaces

The assistant plugs into the chat framework's slots; these are how each part looks and behaves.

| Component | The rules here |
|---|---|
| Chat sidebar | A 400px side sheet on the leading edge, `surface`, an `outline-variant` edge, a 64px header with a centred title medium, conversations at the start and close at the end. Empty: the sparkle on an accent disc, a headline small welcome, suggestions above the input. With messages: suggestions follow the last message, and a jump-to-the-latest icon button appears while the reader has scrolled up. The input and disclaimer stay pinned at the foot. |
| Full-page chat | Empty: a 56px sparkle disc, a headline medium welcome, the input, then centred suggestion chips. With messages: a 768px column that scrolls, the input pinned at the foot with the disclaimer under it. |
| Chat message | The person's message: `primary-container`, body large, at the end of the line, at most 80% wide, 16px corners with the corner nearest them squared. The assistant's message: a small sparkle mark, then flat formatted text (paragraphs, lists, bold, code, tables), then any card, then its sources. Copy, thumbs up and down, and retry as 32px icon buttons, hidden while the latest message streams. |
| Chat input | A pill on `surface-container-high` with 28px corners: an add menu at the start, a field that grows to five lines, the microphone, then a filled send icon button that mirrors. While the assistant runs, send becomes stop. Enter sends; Shift and Enter make a new line. Attachments sit as input chips above it. While dictating, a recording dot with cancel and finish. |
| Disclaimer | One body-small line under the input, centred, `on-surface-variant`: the assistant can make mistakes, so check important information before you save. |
| Suggestion chips | 32px suggestion chips with a leading sparkle, wrapping to more rows. Three or four short, task-shaped suggestions; no questions back to the person. |
| Result card | How a tool's result shows in the chat: an outlined card, 12px corners, a `surface-container-low` header with a 20px icon and title small, then label and value rows or a compact table, then a source line and text actions. A status shows as a filled icon. |
| Approval card | The assistant proposes a save; the person approves, edits or rejects; nothing is written until they do. Outlined with a `primary-accent` edge while waiting, a shield icon, a question as the headline, one line saying where the values came from, a table of field, current and proposed, then one line saying nothing is saved until they approve. Actions in emphasis order: reject (text), edit (outlined), approve (filled). Once decided, the card shows the outcome and drops its buttons. Approvals never use a dialog. |
| Draft field | A value the assistant wrote into a form: a `draft-outline` dashed edge on the `draft-container` tint, a sparkle with an accessible name, and help text saying it was filled by the assistant and from where. Confirm accepts it; revert restores the earlier value. Editing keeps the draft mark until confirmed. Every value the assistant writes is a draft first. |
| Agent progress | The plan as steps, each waiting, running, done or failed: a 20px status icon on a 2px rail, a short verb-first label, optional time. The header folds the list (working, then worked for so many seconds). Tool details (name, arguments, result in code type) are folded away by default. A failed step says what went wrong and the fix. |

## Content

- **Voice** stays the same everywhere: professional, clear, plain and short. **Tone** adapts: an error is short and gives the fix; help text can be fuller.
- **Sentence case** for headings, buttons, labels and navigation. No all-caps, no title case.
- **We and you.** The organisation is we; the reader is you.
- **The assistant never says "I".** The action is the subject: *Filled 4 fields from the request. Check them and confirm.* Never *Sure*, never *Great question*.
- **Plain words**, one idea per sentence, acronyms spelled out on first use. Contractions kept to a minimum in dialogs.
- **Errors** say what happened and what to do: *The file is too large. Choose a file under 10 MB.* Never blame the reader.
- **Not witty.** No jokes, no exclamation marks, no emoji.
- **Numbers**: numerals with thousands separators, dates as *2 Oct 2026*, times in 24 hours.
- **One term per label.** No slash-joined alternatives, no quotation marks or brackets unless they are really needed, no em dashes.
- **Both languages are first-class**: the same hierarchy and the same brevity in each, written naturally rather than translated word for word.

| Moment | The assistant says |
|---|---|
| Welcome | How can the assistant help with today's approvals? |
| Filled fields | Filled 4 fields from the request letter. Check them and confirm. |
| Proposing a save | Ready to approve the request and notify the applicant. Nothing is saved until you confirm. |
| Running | Checking the budget line. |
| Done | Done. The request is approved and the applicant was notified. |
| Needs a decision | Two records match this number. Which one is it? |
| Failed | The service could not be reached. Try again, or continue without the check. |
| Offline | You are offline. Your draft is kept on this device. |
| Limit | Today's assistant limit is reached. It resets at 00:00. |

## Accessibility

- WCAG 2.1 AA everywhere, in both themes and both directions, with every colour pair measured above.
- Keyboard access throughout with the visible focus ring. Dialogs trap focus and return it. Tabs, menus and radio groups take arrow keys, direction-aware.
- Text alternatives on every image; every icon has a word beside it or an accessible name.
- Nothing below 12px; targets 48px (40px dense).
- Test at 200% zoom with nothing overlapping.
- Reduced motion is honoured (see Motion).

## Light pages

- Any screen within three clicks; fewer steps; progressive disclosure (tool details folded, filters behind a bar, Clear all only when needed).
- No imagery in the product. Empty states use a duotone icon, not a picture.
- One icon font or one sprite, subset web fonts that cover both scripts, no large libraries for small jobs.
- Reuse these components rather than making one-off variants.
