# Changelog — Agent Chat UI

## 2.0.0 - 2026-09-23

Components now read role tokens instead of palette steps. Every 1.x token name still resolves, as an alias of its 2.0 role (`--ds-color-focus` to `--ds-focus`, `--ds-shadow-*` to `--ds-elevation-*`, `--ds-size-chat-text` to the body role), for this major version. Values that changed: the focus ring colour, and the comfortable spacing (panel padding 24 to 18px, message gap 16 to 14px, bubble padding 8/12 to 8/16px).

- Roles: surface, ink, line, user, machine, error, success and focus roles, so one set of names serves both themes. The palette gains the steps the roles need.
- Dark theme, opt-in: `tokens-dark.css` with `data-ds-theme="dark"`. Light stays the default.
- Contrast: 23 role pairs measured in both themes, all at WCAG 2.2 AA, with the numbers in `guidelines.md`. The focus ring moves to a darker amber in light (the 1.x ring was 2.97:1 on the quiet well) and a brighter one in dark.
- Type: a minor-third scale from 16 with named roles used as `font` shorthands; title and greeting are fluid by container width; right-to-left text takes taller leading. Nothing below body except the footnote role (1.x allowed 14px pills and 12px text).
- Depth: five elevation levels by job, with a rim of light in dark; one glass material for small floating layers; the dock edge as one mirrored token.
- Motion: five durations, four easings including a sampled spring, and `motion.css` with four transitions and the status loops. Reduced motion stills travel, scale and loops and keeps a short fade.
- Density: compact, comfortable (default) and touch. Targets never under 32px, 44px in touch.
- Accessibility: tooltip in place of the browser `title`, pressed states, radio-group mode picker, polite log, answers to more contrast, reduced transparency and forced colours.
- Components: tooltip, jump to the latest, hand-off row and approval card added. The message box is one row with icon modes and no disclaimer line; the dock folds to a rail.
- `preview.html`: one self-contained page showing the tokens and components in both themes.

## 1.0.0 — 2026-09-17 (confirmed current, no changes 2026-09-17)

- Initial public release: tokens, guidelines, and slot/label conventions for a themed chat assistant surface, generalised from an internal v2.0 system into a standalone, unbranded, framework-agnostic theme.
