# Material Agent Chat

A Material 3 design system for a staff tool where an AI assistant works beside data-heavy screens: tables, forms, approvals and dashboards, with an assistant that fills, drafts and runs tasks, and always asks before it saves. Light and dark, left to right and right to left.

It differs from **Agent Chat UI** in this repo by scope and by base. Agent Chat UI themes one chat surface in its own calm language. Material Agent Chat is a whole product kit on Material 3: the layout, shapes, elevation, state layers, motion and component anatomy are Material 3, filled with this repo's restrained palette, its type families and one outline icon set. The assistant plugs into a chat framework's own parts and slots, restyled in Material 3, never redesigned.

Version 1.0.0. See `CHANGELOG.md`.

## Use it

```html
<link rel="stylesheet" href="tokens.css">
<link rel="stylesheet" href="tokens-dark.css"> <!-- optional: the dark theme -->
<link rel="stylesheet" href="motion.css">      <!-- optional: state layers, focus ring, motion classes -->

<html data-ds-theme="dark" dir="rtl">
```

Light is the default. `data-ds-theme="dark"` (or a `.dark` class) on any ancestor switches to dark. `dir="rtl"` switches the type families and mirrors the layout. Open `preview.html` to see both themes side by side.

## The rules that make the look

1. **Material 3 shapes the product; the palette, type and icons are this system's own.** When the two disagree, colour, type, icons, accessibility and content win; everything else is Material 3.
2. **One filled button per view.** The accent fills the one main action and marks the active indicator and the person's own message. Selected states are grey, so the accent never piles up.
3. **Warm and neutral.** A lot of white and near-white, grey for everything structural, the accent kept for the few things above.
4. **Flat and light.** Elevation is mainly a tonal surface, with light two-layer shadows. No glass, blur, gradients, textures or pictures.
5. **The assistant asks before it saves.** Every save goes through an approval card in the chat; every value the assistant writes into a form is a draft until the person confirms it.
6. **Full mirror in right to left.** Logical properties throughout; the chat sidebar on the leading edge; directional icons mirror and the rest do not.
7. **Calm motion.** Material 3's standard scheme, fades and short slides, no bounce, nothing moving on an idle screen, and a reduced path that drops every duration to 1ms.
8. **Plain words.** Sentence case, short sentences, no emoji, and an assistant that never says "I".

## What is in it

- **Colour roles**: the Material 3 set plus success and two agent roles (draft container and outline), with a measured WCAG 2.1 AA table for both themes in `guidelines.md`.
- **Type roles**: the Material 3 scale from display to label, heavy tight headings and roomy body, nothing below 12px, with right-to-left families that switch on `dir`.
- **Shape, elevation, states, space, layout and motion** as Material 3 tokens.
- **Components**: the Material 3 set a data-heavy screen needs (buttons, icon button, FAB, text field, checkbox, radio, switch, chips, menu, card, list, dialog, side sheet, snackbar, tooltip, badge, progress, top app bar, navigation rail and drawer, tabs, search, divider), three data components Material 3 does not specify (data table, filter bar, empty state), and the agent surfaces (chat sidebar, full-page chat, chat message, chat input, suggestion chips, result card, approval card, draft field, agent progress).
- **A chat framework mapping**: which Material 3 role fills each of a typical chat framework's theme variables, and which component fills each of its slots.

## Icons

The system is drawn with one outline icon set at one weight. The reference build uses Phosphor Icons (MIT licence) at its Regular weight, installed from its official package with its licence kept beside it. This repository ships no icon files; the preview draws its few icons inline.

## Files

```
tokens.css        palette, light colour roles, type roles, shape, elevation, states, space, layout, icon sizes and motion
tokens-dark.css   the opt-in dark theme: the same roles, redefined
motion.css        optional: the state layer, the focus ring and the motion classes
guidelines.md     the rules in full: roles, measured contrast, type, shape, elevation, states, motion, layout, icons, the chat framework mapping, components, content, accessibility, light pages
preview.html      one page showing the system in both themes, loading the three stylesheets beside it
CHANGELOG.md      dated changes to this system
```

Fonts are referenced by family name only and never shipped; every stack ends in a system fallback, so the system reads correctly with no web font at all.
