# Agent Chat UI guidelines

Version 2.0.0. The rules behind `tokens.css`, `tokens-dark.css` and `motion.css`. `preview.html` shows every one of them on one page.

## Set up

```html
<link rel="stylesheet" href="tokens.css">
<link rel="stylesheet" href="tokens-dark.css">   <!-- optional: the dark theme -->
<link rel="stylesheet" href="motion.css">        <!-- optional: the transition classes -->

<div data-ds-theme>…</div>                          <!-- light, the default -->
<div data-ds-theme="dark">…</div>                   <!-- dark, opt-in -->
<div data-ds-theme data-ds-density="compact">…</div>
<div data-ds-theme dir="rtl" lang="ar">…</div>
```

- Every token lives on `[data-ds-theme]`, so a themed panel can sit inside a page that uses other tokens. A dark panel can sit inside a light page and the other way round, because each scope recomputes its own roles.
- Put `data-ds-density` on the same element as `data-ds-theme`, or on an element inside it. A nested `data-ds-theme` starts again at the default density.
- Text direction comes from `dir`. Set it on the scope or on any element inside it.

## Colour roles

Components read roles, never palette steps. One set of names serves both themes, and a component cannot pick a colour the dark theme does not know about.

| Role | Light | Dark | For |
|---|---|---|---|
| `--ds-surface` | `#FFFFFF` | `#1B1D21` | the page, the dock, the thread |
| `--ds-surface-quiet` | `#F7F7F7` | `#232528` | a well: filled chip, code, table head, hover, selected row |
| `--ds-surface-raised` | `#FFFFFF` | `#232528` | cards and the message box, lifted by elevation |
| `--ds-surface-overlay` | `#FFFFFF` | `#2C2E30` | popovers, the popup window |
| `--ds-surface-side` | `#FCFCFC` | `#0E0F12` | the collapsed rail |
| `--ds-ink` | `#232528` | `#E1E3E5` | text |
| `--ds-ink-muted` | `#5F646D` | `#9EA2A9` | secondary text, placeholder, the off microphone and live-conversation buttons |
| `--ds-ink-faint` | `#9EA2A9` | `#4B4F58` | disabled only, never meaning |
| `--ds-line` | `#E1E3E5` | `#3E4046` | a plain hairline: a divider, a table rule, a blockquote rule, the dock's edge |
| `--ds-line-strong` | `#797E86` | `#797E86` | every control edge: a button, a chip, a field, an avatar ring |
| `--ds-line-bold` | `#5F646D` | `#9EA2A9` | the same edge, hovered or selected |
| `--ds-user-strong` | `#92722A`, white ink | `#CBA344`, dark ink | send, the primary action, the message box edge |
| `--ds-user-strong-hover` | `#7C5E24` | `#D7BC6D` | hover darkens in light, lightens under dark ink in dark |
| `--ds-user-bg`, `-bg-hover` | `#F9F7ED`, `#F2ECCF` | `#312C24`, `#3D3525` | the user's bubble, the avatar, a selected choice |
| `--ds-user-ink` | `#7C5E24` | `#F2ECCF` | text on the user's ground |
| `--ds-user-edge`, `-mark` | soft edge, `#92722A` | the same roles, tinted for the dark | the bubble edge, a voice mark |
| `--ds-machine` | `#2C6A9B` | `#86B7E1` | links, the streaming caret, activity |
| `--ds-machine-rule` | `#9FC0DA` | `#2C6A9B` | the 2px rule beside the assistant's words |
| `--ds-machine-soft`, `-tint` | `#DFECF7`, `#EEF5FB` | `#1F2F3E`, `#1D2832` | hand-off rows |
| `--ds-error-*`, `--ds-success-*` | red 50/200/700, green 50/700 | tinted grounds, red 300, green 300 | status only |
| `--ds-focus` | `#B2550A` | `#F29F10` | the focus ring, and nothing else |

**The accent marks the user and nothing else.** Their bubble, the message box, their avatar, the chip that says where they are, a choice they selected, their own action. Never chips in general, counts, stripes, rules, links or activity. Structure is ink and lines; the machine is the machine tint. The same in the dark theme.

**Dark tints are flattened.** Each dark tint is a palette colour at a stated opacity over the dark ground (the user's ground is the accent at 14%, the hand-off row the machine at 14%), written as a solid hex so it never shifts with what is behind it. The opacity is in a comment beside each value.

**A control edge is never a hairline.** A button, a chip and a field are drawn by their edge alone, so `--ds-line-strong` carries them and reaches 3:1 on every surface a control can sit on, including the error tint behind a Retry button; `--ds-line-bold` is the same edge hovered or selected. `--ds-line` is for rules that separate rather than enclose, so it stays light and never draws a control.

**The brightest accent step (`#B68A35`) never sits under white text** (3.15:1). In the dark theme the strong accent carries dark ink; white on it would be 2.37:1.

## Contrast, measured

Computed from the token files as shipped (WCAG 2.x relative luminance). Every text pair is 4.5:1 or better and every control edge, icon and ring 3:1 or better, in both themes. Plain hairlines (`--ds-line`) sit below that on purpose: they separate, they never enclose a control, and nothing depends on seeing them.

| Pair | Foreground on background | Light | Dark | Needs |
|---|---|---|---|---|
| Body text | `ink` on `surface` | 15.37 | 13.12 | 4.5 |
| Body text on a quiet well | `ink` on `surface-quiet` | 14.34 | 11.94 | 4.5 |
| Body text on an overlay | `ink` on `surface-overlay` | 15.37 | 10.59 | 4.5 |
| Muted text, placeholder | `ink-muted` on `surface` | 5.95 | 6.59 | 4.5 |
| Muted text on a quiet well | `ink-muted` on `surface-quiet` | 5.55 | 6.00 | 4.5 |
| Muted text on an overlay | `ink-muted` on `surface-overlay` | 5.95 | 5.32 | 4.5 |
| The user's bubble, location chip, avatar initial | `user-ink` on `user-bg` | 5.61 | 11.66 | 4.5 |
| Send, primary button | `user-on-strong` on `user-strong` | 4.50 | 7.12 | 4.5 |
| Primary button, hover | `user-on-strong` on `user-strong-hover` | 6.03 | 9.08 | 4.5 |
| Outline button, talk icons | `user-ink` on `surface` | 6.03 | 14.20 | 4.5 |
| Link, streaming caret | `machine` on `surface` | 5.77 | 7.94 | 4.5 |
| Hand-off row text | `ink` on `machine-tint` | 13.97 | 11.64 | 4.5 |
| Error | `error-ink` on `error-bg` | 5.91 | 7.83 | 4.5 |
| Success | `success-ink` on `success-bg` | 6.41 | 8.20 | 4.5 |
| Done word, settled approval | `success-ink` on `surface` | 6.80 | 10.13 | 4.5 |
| Message box edge | `user-strong` on `surface` | 4.50 | 7.12 | 3.0 |
| Off microphone, off live conversation | `ink-muted` on `surface-raised` | 5.95 | 6.00 | 3.0 |
| Activity dots, spinner | `machine` on `surface` | 5.77 | 7.94 | 3.0 |
| Voice mark on the user's bubble | `user-mark` on `user-bg` | 4.19 | 4.40 | 3.0 |
| Focus ring on the ground | `focus` on `surface` | 5.00 | 7.83 | 3.0 |
| Focus ring on a quiet well | `focus` on `surface-quiet` | 4.67 | 7.13 | 3.0 |
| Focus ring on the user's ground | `focus` on `user-bg` | 4.66 | 6.42 | 3.0 |
| Focus ring on an overlay | `focus` on `surface-overlay` | 5.00 | 6.32 | 3.0 |
| Control edge on the ground | `line-strong` on `surface` | 4.08 | 4.13 | 3.0 |
| Control edge on a quiet well | `line-strong` on `surface-quiet` | 3.81 | 3.76 | 3.0 |
| Control edge on an overlay | `line-strong` on `surface-overlay` | 4.08 | 3.34 | 3.0 |
| Control edge on the error tint | `line-strong` on `error-bg` | 3.73 | 3.54 | 3.0 |
| Hover and selected edge | `line-bold` on `surface-quiet` | 5.55 | 6.00 | 3.0 |

**Glass, worst case.** The glass material is translucent, so its text was measured over pure black and pure white behind it. Light glass: ink 12.31 to 15.37, muted 4.77 to 5.95. Dark glass: ink 9.29 to 11.62, muted 4.66 to 5.83. Nothing on glass drops below 4.5:1 whatever is underneath.

The primary action at 4.50:1 in light is exactly the threshold, so its label is never smaller than 16px.

## Type

A minor third (x1.2) from 16, with named roles. Each role is a `font` shorthand, so a component never hand-picks a family, size, weight or leading: `font: var(--ds-type-body)`.

| Role | Size / leading, left to right | Right to left | Weight, family | For |
|---|---|---|---|---|
| `--ds-type-footnote` | 14/20 | 14/24 | 400, text | the surface footer's honesty line, a time under full detail, a staged-voice label. Nothing else |
| `--ds-type-body` | 16/24 | 16/28 | 400, text | everything else: messages, chips, fields, buttons, rows, cards |
| `--ds-type-body-strong` | 16/24 | 16/28 | 500, text | a name inside a row, a button label |
| `--ds-type-name` | 17/24 | 17/28 | 600, display | the assistant's name in a header |
| `--ds-type-heading` | 20/28 | 20/32 | 600, display | a card title, a markdown heading |
| `--ds-type-title` | 24 to 28, fluid | taller leading | 700, display | a panel title |
| `--ds-type-greeting` | 28 to 34, fluid | taller leading | 700, display | the greeting line |
| `--ds-type-code` | 15/24 | 15/24 | 400, mono | code; a monospace at 15 matches a sans at 16 optically |

- **Nothing small unless it earns its place.** Chat text is never under 16/24. The footnote role is for the three uses above; badges, captions, sub-labels, hint lines and small caps have no role.
- **Fluid by container, not viewport.** Title and greeting use container units (`cqi`), so the greeting reaches its minimum in a narrow dock instead of wrapping into four lines. Give the panel `container-type: inline-size`. Without a container, `cqi` falls back to the small viewport, which still stays within the clamp.
- **Arabic gets taller leading** (body 16/28, heading 20/32): Arabic families carry taller ascenders, descenders and marks, and at 16/24 lines touch. Arabic is never letter-spaced; the display tracking of -0.01em is left to right only.
- **Families by name only; nothing is shipped.** Text: a humanist sans for left to right, a Kufi-style Arabic sans for right to left; display: a neutral grotesque and a geometric Arabic display face. Each stack ends in `system-ui, sans-serif` (and `Tahoma` for Arabic), so the system reads correctly with no web font at all.
- **Digits stay Latin in both directions.** Five weights at most on one screen.

## Space, shape and density

A 4px unit. Radius by job: control 8, bubble 10, card 12, window 16, pill for chips and round buttons.

Density changes space and targets, never type.

| Token | Compact | Comfortable (default) | Touch |
|---|---|---|---|
| `--ds-dock-width` | 380px | 400px | 440px |
| `--ds-panel-padding` | 14px | 18px | 20px |
| `--ds-message-gap` | 10px | 14px | 16px |
| `--ds-bubble-padding-y` / `-x` | 6 / 12px | 8 / 16px | 10 / 18px |
| `--ds-card-padding` | 18px | 24px | 24px |
| `--ds-control-height` | 40px | 48px | 48px |
| `--ds-chip-height` | 36px | 40px | 44px |
| `--ds-icon-button` | 32px | 36px | 44px |
| `--ds-icon-button-dock` | 32px | 32px | 44px |
| `--ds-row-height` | 40px | 48px | 52px |

- `--ds-icon-button` is every icon button the user aims at inside the message box: mode, type, speak, live and send, all one size in a row. `--ds-icon-button-dock` is dock chrome only, the header and the rail, which sit quieter than the box.
- No target is ever under 32px (WCAG 2.2 asks for 24; 2.5.8). Touch gives every target 44px (2.5.5).
- Compact is for long desk sessions, touch for tablets. Neither ever becomes a reason to shrink text.

## Depth and material

Five elevation levels, one job each.

| Level | Token | For |
|---|---|---|
| 0 ground | `--ds-elevation-0` | the page, the thread, the dock |
| 1 raised | `--ds-elevation-1` | cards, the message box |
| 2 floating | `--ds-elevation-2` | the popup toggle, jump to the latest, the tooltip |
| 3 overlay | `--ds-elevation-3` | popovers such as the mode picker |
| 4 window | `--ds-elevation-4` | the popup window |

- **Light:** two-layer shadows tinted with the darkest neutral, a tight contact shadow plus a wide soft one. **Dark:** shadows alone vanish on a dark ground, so each level adds a 1px rim of light along its top edge, a deeper shadow, and a lighter surface (ground, then raised, then overlay).
- **One glass material** (`--ds-material-glass`, `--ds-material-filter`, `--ds-material-edge`): 90% opaque in light, 94% in dark, a 20px blur with slight saturation and a hairline edge. Small floating layers only: the tooltip, jump to the latest, the mode picker. Long reading never sits on glass. It turns solid under reduced transparency and more contrast.
- **The dock edge is one token**, `--ds-dock-edge` (with `--ds-dock-edge-rtl`): a hairline and an inward shade together, used as a `box-shadow`, never a plain border. It themes and mirrors as one thing.
- No gradients, no glows, no textures, no photography behind the interface.

## Motion

One calm tempo.

| Token | Value | For |
|---|---|---|
| `--ds-duration-quick` | 120ms | hover tints, a tooltip, anything leaving |
| `--ds-duration-control` | 200ms | focus, press, the send colour |
| `--ds-duration-content` | 400ms | a message arriving, a popover |
| `--ds-duration-card` | 450ms | the dock folding to the rail and back |
| `--ds-duration-travel` | 700ms | the message box travelling from the greeting into the dock |
| `--ds-ease` | `cubic-bezier(.22, 1, .36, 1)` | enter and settle: everything that arrives |
| `--ds-ease-exit` | `cubic-bezier(.4, 0, 1, 1)` | accelerate away: leaving is quicker than arriving |
| `--ds-ease-move` | `cubic-bezier(.65, 0, .35, 1)` | something already on screen changing size or place |
| `--ds-ease-spring` | sampled `linear()` | the travel: 0.93% overshoot, settled by 700ms, never a bounce. Falls back to `--ds-ease` where `linear()` is not supported |

**Four transitions earn their place** (`motion.css`), each showing where something came from or that the machine is working:

- `.ds-arrive`: a new turn rises 8px and fades in, once. Never on history.
- `.ds-draw`: the machine rule beside a new assistant turn draws from the top as the reply starts. While the reply streams the rule is the full machine colour; when it ends it settles to `--ds-machine-rule`. The caret stays still.
- `.ds-pop`: a popover grows from its anchor (scale 0.98 to 1) and fades in. The origin mirrors in right to left.
- `.ds-fade`: a tooltip fades in.

Only status loops: the three activity dots (`.ds-dot`) and the spinner (`.ds-spin`). Nothing decorative loops.

**Reduced motion** (`prefers-reduced-motion: reduce`): nothing travels or scales (rise 0, scale 1, card and travel 0ms), the draw and both loops stop, and colour and opacity keep a 120ms fade. A hard flash on every state change is its own discomfort; the ask is for no motion, not no change.

## Accessibility

WCAG 2.2 AA in both themes.

- **Focus:** a solid 2px ring in `--ds-focus`, offset 2px, on `:focus-visible` only. The icon buttons inside the message box draw it inward (negative offset), so a neighbour never covers it (2.4.11); the box itself takes the standard outward ring when its field has focus, so the accent edge stays visible beneath it. The ring colour is distinct from the user's colour, so it never reads as another button.
- **Targets:** 32px minimum, 44px in touch density.
- **Icons speak.** Each icon button has an `aria-label`, and the same words show in a tooltip on hover (after 400ms) and at once on keyboard focus. An action says what it does in one short sentence; a toggle is named by its control alone, never by its state. It stays while the pointer is on it and closes on Escape (1.4.13). The tooltip bubble is `aria-hidden`, so nothing is read twice. Never the browser `title`: it does not show on keyboard focus or touch, and it renders at the system's small size.
- **State lives in the control.** The microphone and live-conversation buttons carry `aria-pressed`; off is a slashed glyph in muted ink (3:1 or better), not a word, and never part of the name, so it is never announced twice.
- **The mode picker is a radio group:** arrow keys, Home and End move the choice and the focus together, one tab stop for the group (roving `tabindex`, `aria-checked` on the chosen row); the arrows follow the text direction. Escape closes and returns focus to the mode icon.
- **The thread is a polite log** (`role="log"`, `aria-live="polite"`), so each new turn is heard once. Hand-off rows and a settled approval are `role="status"`.
- **Never colour alone.** A tick and a word say done; a slash says off.
- **The user's system settings, answered by the tokens:** more contrast (visible lines, darker muted ink, solid glass), reduced transparency (solid glass), reduced motion (above), forced colours (no blur; give floating layers, the user's bubble and the toggle a `1px solid CanvasText` border and let the ring use `Highlight`).

## Right to left

- The whole layout mirrors: logical properties only (`inline-start`, `inline-end`, `padding-inline`, `border-inline-start`). The dock sits on the inline-start side, the user's bubble at the inline end, the machine rule at the inline start.
- Directional glyphs mirror: left and right arrows, carets, send, regenerate, collapse and expand, the hand-off arrow. Up and down arrows, faces, the spinner, ticks and marks never flip. A popover grows from the mirrored corner.
- Families and leading swap by direction at the token level, never per component.
- Digits stay Latin.

## Layout

- **The dock:** `--ds-dock-width` (400px by default) on the inline-start side, with the designed edge. It folds to a 56px rail (`--ds-rail-width`) over the card duration with the move easing; the rail keeps the assistant's face and one open control.
- **The greeting:** four things only. The face (`--ds-face-greeting`, 120px), one line in the greeting role, the message box at `--ds-greeting-width` (600px), and up to five chips. No digest, no count, no tagline. The footer below them is the surface's, not a fifth thing.
- **The popup:** about 24rem by 600px, window elevation, radius 16. **The sidebar:** about 28rem, full height. Both keep a fixed header (64px), a pinned message box, and a scrolling thread between.
- **The footer:** the last row of every chat surface, below the message box and outside it, holding the honesty line and nothing else. It is pinned with the box, not scrolled with the thread, and it is the only standing use of the footnote role.

## Icon role mapping

One outline icon family at regular weight, 20px glyphs on at least a 32px target, drawn in `currentColor`. No icon font, no emoji, no Unicode characters as icons.

| Role | Glyph |
|---|---|
| send | paper plane (mirrors) |
| stop | stop square |
| regenerate | clockwise arrow (mirrors) |
| open | chat bubble |
| close (collapse) | caret toward the inline start (mirrors) |
| header close | x |
| type | keyboard |
| speak (push to talk) | microphone; microphone with a slash when off |
| voice mark | microphone at 16px, never flips |
| live conversation | waveform; waveform with a slash when off |
| mode | one glyph per mode: an open hand, scales, a lightning bolt |
| activity, spinner | three dots, a spinner |
| jump to the latest | arrow down |
| hand-off | arrow right (mirrors) |
| sent back for a change | back arrow (mirrors) |
| approve, success | check |
| error | warning circle |
| copy, feedback | copy, thumbs up and down |
| attach | paperclip |

## Slot and label conventions

A chat framework's theming layer typically exposes:

- **Slots:** message view, scroll view, input, suggestion view, welcome screen, header, footer, toggle button; nested assistant message, user message, toolbar, copy button. Apply the motion classes through the slots' class props. Where a framework has no footer slot, the footer is rendered once beneath the input slot, still outside the input.
- **Labels:** header title, welcome message, input placeholder, the footer's honesty line, every icon's words. Always from the framework's label props in both languages, never hard-coded in CSS or DOM overrides.
- **Icon props:** a name-to-glyph map matching the table above, including type, speak, live, mode, jump, hand-off and approve.

Theme through these contracts only. Every value here is reachable through custom properties on the framework's own theming attribute, plus the slot, label and icon props. Never fork the framework's DOM or class names to apply a colour.

## Components (visual reference)

A themed mirror of the framework's pieces, for design work only. Every one reads roles, so it follows the theme, the density and the direction.

- **Message box:** one row. The mode icon at the start, the field, then inside the box at its end the three ways to talk as icons (type, speak, live) and send. Never worded buttons. A 2px edge in `--ds-user-strong`, raised elevation. Every icon in the row is one size (`--ds-icon-button`), send included. No disclaimer line of its own: the honesty line belongs to the surface footer below it.
- **Mode picker:** one icon at the start of the box; opened, a glass popover at the overlay level with one row per mode (icon, name, one sentence, a tick on the current one) and one fixed line saying that an act with consequences always waits for the user, in every mode. The tick and the current row are ink, not the accent.
- **Message:** the user's turn is a bubble at the inline end in `--ds-user-bg` with `--ds-user-edge`; the assistant's turn has no bubble and a 2px machine rule at the inline start. A turn the user spoke opens with the voice mark in `--ds-user-mark`. No toolbar, no timestamps, no system rows.
- **Thread:** one gap, no dividers, no date rows; a polite log.
- **Jump to the latest (new):** one round glass button with a down arrow, sticky at the foot of the thread, shown only while the user has scrolled up and something new has arrived. No count.
- **Hand-off row (new):** one pill in the machine tint with a machine-soft edge: two faces at 24px, the two names, an arrow that mirrors, optionally the task and "working" (the spinner) or "done" (a tick and the done word in the success ink). The machine talking about itself, so no accent.
- **Approval card (new):** the one shape for an act that waits for the user. Waiting: a title saying what will happen, the fields, and two actions only, Approve (primary) and Change (outline). No third button, no countdown. Decided: it settles to one row in ink (a tick and "Approved", or a back arrow and "Sent back for a change"), announced once as a status. Nothing accented after the decision.
- **Surface footer (new):** required on every chat surface (dock, rail's opened panel, inline panel, sidebar, popup, greeting). One line in `--ds-type-footnote`, muted ink, centred, saying plainly that answers can be wrong and what matters is worth checking. It belongs to the surface, not to the message box, so the box keeps no line of its own and the sentence is never repeated inside the thread. One sentence, no link, no icon, no accent; of the footnote role's three uses it is the only standing one.
- **Tooltip (new):** body size in ink on the glass material, radius 8, floating elevation. Never small, never accented.
- **Suggestions:** up to five chips, two kinds only (outline and filled), never a written kind.
- **Welcome screen:** the greeting (see Layout).
- **Generative card:** a result inside an assistant turn; one primary action per card; eyebrow, fields and status at body size.
- **Chat window:** dock, rail, inline panel, sidebar, popup; the popup toggle at floating elevation.
- **Markdown:** headings on the type scale, links in the machine colour, inline code and code blocks in the code role on a quiet well, tables with a quiet head, a blockquote with a neutral rule.
- **States:** activity dots, spinner, error banner (a retry that is a real 32px button), success banner. All body size.
