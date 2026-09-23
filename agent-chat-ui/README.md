# Agent Chat UI

A theme for an AI chat assistant surface: a docked panel that folds to a rail, an inline panel, a sidebar, and a floating popup. It is framework-agnostic: colour, type, space, depth and motion tokens, plus the slot and label conventions a typical chat-framework theming layer expects. It themes a chat framework's own components; it does not replace them.

Version 2.0.0 adds a principled type scale, an opt-in dark theme, motion, depth and materials, density modes, a measured WCAG 2.2 AA pass in both themes, and five components the system was missing. Everything works in both text directions.

Open `preview.html` to see it: the tokens, light and dark side by side, the motion and depth in use, and the key components. It loads the three stylesheets beside it and nothing else, so there are no external requests and no build step.

## The rules that make the look

1. **Nothing small unless it earns its place.** No badges, tags, captions, sub-labels, timestamps, system rows or hint lines beyond the few that honesty or meaning keeps. State lives in the control. Everything is body size (16/24) except a footnote role, whose standing use is the surface footer.
2. **The ways to talk are icons inside the message box**: type, speak, live conversation, then send. One row, each icon with a short label: a sentence for an action, the control's name for a toggle. Never worded buttons, and no disclaimer line of its own under the box: that line is the surface's footer (rule 9).
3. **The mode picker is one icon** at the start of the box. Opened, one row per mode with one sentence each, and one fixed line: an act with consequences always waits for the user, in every mode.
4. **The greeting is four things**: the face, one line, the message box, up to five suggestion chips. No digest, no count, no tagline. The footer below them belongs to the surface.
5. **The dock has a designed edge**, never a plain border, and folds to a 56px rail.
6. **The accent marks the user and nothing else**: their bubble, the message box, their avatar, where they are, their choice, their own action. Never chips in general, counts, stripes, rules, links or activity. Structure is ink; the machine is a quiet blue tint.
7. **Full mirror in right to left.** Logical properties throughout; digits stay Latin; faces never flip.
8. **Generous space, calm motion.** Nothing decorative moves and nothing decorative loops.
9. **One honesty line, in the surface footer.** Every chat surface ends with a single footnote line saying answers can be wrong and what matters is worth checking. It belongs to the surface, not the message box, and it is the only standing use of a size below body.

## Content rules

- Plain, direct words. Address the user as you. No exclamation marks, no emoji, no jokes, no taglines.
- Sentence case everywhere.
- Every string exists in both languages and comes through the framework's label and slot props, never hard-coded in CSS or DOM overrides. Every icon's label is its accessible name and its tooltip.
- Labels are short imperatives: Send, Retry, Approve, Change.

## What 2.0.0 adds

**Roles, not palette steps.** Components read roles: surface (ground, quiet, raised, overlay, side), ink (text, muted, faint), line (hairline, strong, bold), user, machine, error, success and focus. One set of names serves both themes.

**Dark theme, opt-in.** Load `tokens-dark.css` and set `data-ds-theme="dark"`. Light stays the default everywhere. A near-black ground `#1B1D21`, wells and cards one step lighter, overlays one more; soft ink `#E1E3E5` to avoid halation; the user's strong colour moves to a lighter step carrying dark ink; the machine lightens to a pale blue.

**Measured contrast.** 28 role pairs computed from the token files in both themes: every text pair 4.5:1 or better, every control edge, icon and focus ring 3:1 or better. Translucent glass was measured over pure black and pure white. The table is in `guidelines.md`.

**Type roles on one scale.** A minor third (x1.2) from 16. Roles are `font` shorthands (`--ds-type-footnote`, `-body`, `-body-strong`, `-name`, `-heading`, `-title`, `-greeting`, `-code`). Title and greeting are fluid by container width, so the greeting fits a narrow dock without wrapping. Right-to-left text takes taller leading (body 16/28).

**Depth and materials.** Five elevation levels, each with one job (ground, raised, floating, overlay, window): two-layer shadows in light, a rim of light plus a deeper shadow in dark. One glass material for small floating layers only, opaque enough that text stays at AA over anything. The dock edge is one token that themes and mirrors.

**Motion.** Five durations, four easings including a sampled spring under 1% overshoot, and four transitions that earn their place (`motion.css`): a new turn rises into place, the machine rule draws as a reply starts, a popover grows from its anchor, a tooltip fades. Reduced motion stills travel, scale and loops and keeps a short fade.

**Density.** `data-ds-density="compact|comfortable|touch"` changes space and targets, never type. No target under 32px; touch gives 44px.

**Accessibility.** A focus ring that reaches 3:1 on every surface, drawn inward on the controls inside the message box and outside the box's own accent edge; a real tooltip in place of the browser `title`; pressed states on the microphone and live buttons; the mode picker as a radio group; the thread as a polite log; answers to more contrast, reduced transparency, reduced motion and forced colours.

**Components added.** Tooltip, jump to the latest, hand-off row, approval card, surface footer. See `guidelines.md`.

## Files

```
tokens.css        palette, light roles, type, space, shape, density, elevation, material and motion tokens
tokens-dark.css   the opt-in dark theme: the same roles, redefined
motion.css        optional: the transition and status-loop classes
guidelines.md     the rules in full: roles, measured contrast, type, density, depth, motion, accessibility, layout, icons, slots, components
preview.html      one page showing the system in both themes, loading the three stylesheets beside it
CHANGELOG.md      dated changes to this system
```

Fonts are referenced by family name only and never shipped; every stack ends in a system fallback, so the system reads correctly with no web font at all.
