# Changelog — Product UI

## 2.0.0 — 2026-09-23

A new version of the whole system: colour by role, a complete opt-in dark theme, type roles, density, depth, motion, and the thin component groups filled in.

- **Colour roles.** Components now read roles (surface, ink, line, user, ink action, machine, status, focus, data) instead of palette steps. The warm accent is reserved for the user (their one primary action, their choices, where they are, their own value in a chart) and no longer carries links, card borders, card hover glows or chart series. Secondary actions and links are ink.
- **The machine colour.** Content a model produced, progress, activity and data series 1 use a cool cyan with its own chip, rule and working bar. The 1.x AI chip, which used the accent, moves to it.
- **Dark theme, complete and opt-in.** `tokens-dark.css` re-points every role and the depth tokens, so every component works in dark with no extra rules. Palette steps only: the off-palette status tints of 1.1.0 are replaced. It is no longer limited to internal command views and can be switched at runtime from a display menu, with a cross-fade. Light stays the default.
- **Contrast table.** Every text, control, focus and chart pair in both themes, with its ratio, in `guidelines.md`. Target moves from WCAG 2.1 AA to 2.2 AA. The focus ring moves one step darker so it passes 3:1 on light wells.
- **Type roles.** Ten named roles on a fluid scale, built from the existing steps; tabular Latin figures; RTL tracking and leading. The 12px caption size is removed: nothing is under 14px, and only helper text, timestamps, chart ticks and table footers use 14px.
- **Density.** Compact, comfortable and spacious modes through `data-ds-density`, never under the 40px target.
- **Depth and materials.** Four levels (flat, raised, float, overlay) with two-layer shadows, a lit rim in dark, and a 90% veil for sticky chrome with solid fallbacks. New `materials.css`.
- **Motion.** Named durations and easings, six transitions in the new `motion.css`, and a full reduced-motion path through the OS setting or `data-ds-motion="reduce"`. Horizontal travel mirrors in RTL. No page-load animation in product screens.
- **Components** (inventory and rules in `guidelines.md`). New: app bar, display menu, command menu, segmented control, icon button, chip, filter bar, bulk-action bar, panel, date picker and calendar, chart legend, insight. Rebuilt: table (sticky head, pinned column, row header, mixed select-all, row and bulk actions, loading rows, density), KPI tile (direction, target, narrow layout), charts (round ticks, the user's own value against their own history or target, a summary sentence, a progress ring in place of a donut), dropdown and dialogs (keyboard and focus trapping), steps, combobox, form errors (16px with an icon).
- **States, layout and imagery.** The 1.x rules for interaction states, disabled controls, per-section containers with the 1024px navigation breakpoint, and imagery are carried into `guidelines.md`, expressed in the 2.0 roles and tokens.
- **Preview.** `preview.html` shows every token system and the key components in light and dark side by side. It links `tokens.css`, `tokens-dark.css`, `motion.css` and `materials.css` from its own folder, so it always shows what the system currently says, and fetches nothing.

### Moving from 1.x

| 1.x | 2.0.0 |
|---|---|
| `--ds-color-gold-300`, `-500`, `-600` | `--ds-accent-300`, `-500`, `-600` (palette); in components use `--ds-user`, `--ds-user-hover`, `--ds-user-ink`, `--ds-user-line` |
| `--ds-color-neutral-50`, `-100`, `-500`, `-800` | `--ds-neutral-*` (palette); in components `--ds-surface-sunken`, `--ds-line`, `--ds-ink-muted`, `--ds-ink` |
| `--ds-color-page`, `--ds-color-page-alt` | `--ds-surface-base`, `--ds-surface-canvas` |
| `--ds-color-green-600`, `-blue-600`, `-red-600`, `-amber-fill`, `-amber-text` | `--ds-{success,info,error,warning}-{fg,soft,solid,on,line}` |
| `--ds-color-focus` (`#D67909`) | `--ds-focus` (`#B2550B`) |
| `--ds-ai-chip-bg`, `--ds-ai-chip-fg` | `--ds-machine-soft`, `--ds-machine-ink` |
| `--ds-dark-*` | Removed. The same role names take dark values under `data-ds-theme="dark"` |
| `--ds-shadow-sm`, `-xl`, `-modal` | `--ds-elevation-raised`, `-float`, `-overlay` |
| `--ds-motion-standard` (0.3s), `--ds-motion-toggle` (200ms), `--ds-motion-spinner` | `--ds-duration-*` by what moves; `--ds-duration-state` (200ms); `--ds-duration-spin` |
| `--ds-size-caption` (12px) | Removed; use `--ds-type-meta-size` (14px) |
| `--ds-size-*`, `--ds-weight-*`, `--ds-font-*`, spacing, grid and radius tokens | Unchanged; prefer the `--ds-type-*` and `--ds-radius-{control,panel,overlay,chip}` roles |

## 1.1.0 — 2026-09-17

- Added an opt-in dark theme (`tokens-dark.css`), for internal command views only — the public website and portal stay light, and a page never toggles between the two at runtime. Dark theme carries its own status-badge tints rather than reusing the light-mode pair.
- Added AI-generated-content chip tokens (light and dark).
- Added a marketing hero pattern note: a subtle line pattern behind the homepage hero and a staggered card/stat reveal, light-only, no colour tokens changed.

## 1.0.0 — 2026-09-17

- Initial public release: tokens, guidelines, and component inventory for a website and product/dashboard UI kit, generalised from an internal v2.0 system into a standalone, unbranded design system.
