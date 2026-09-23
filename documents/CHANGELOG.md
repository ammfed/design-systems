# Changelog: Documents

## 2.0.0 - 2026-09-23

- **Colour roles.** Added 42 roles for text, grounds, materials, rules, chart series, the person accent, focus and callouts, each with a light and a dark value. Components use roles instead of ramps.
- **Accent.** The accent now marks a person only (a quotation bar, a name, a signature). Titles, rules, table headers, bullets and chart series move to ink.
- **Dark theme.** Added `tokens-dark.css`, an opt-in dark theme for decks, reading views and on-screen page previews, set with `data-ds-theme="dark"` for a whole deck or document. Print is forced light. The 1.x deck-only dark tokens are superseded.
- **Contrast.** Every one of 34 role pairs passes WCAG 2.2 AA in both themes (68 checks), with the ratios published in `guidelines.md`. `prefers-contrast: more` is supported.
- **Type.** Replaced the H1 to H6 screen list with eleven named type roles, each sized per medium: fluid `clamp()` sizes on screen, points in print, pixels on slides. Added weights and tracking per role, taller leading and no tracking for the second script, and floors of 14px, 8pt and 24px.
- **Space and density.** Added eight space steps per medium, radii per medium, and three density modes (`data-ds-density`).
- **Depth and materials.** Added paper, plate, well, inverse, canvas and glass, with sheet and float shadows and a rim for screen only. Glass has solid fallbacks for reduced transparency and missing `backdrop-filter`.
- **Motion.** Added `motion.css` with duration, easing, stagger and distance tokens and rise, draw, grow, trace, enter and fade hooks. Horizontal motion is direction-aware. Under reduced motion only a short fade remains, and `data-ds-motion="off"` and print remove all motion.
- **Components.** Guidelines now cover the component set with its states: data-table rows and status cells, key facts with meters and deltas, range and share charts, contents and agenda, the section divider field, deck and reading viewers, and viewer control states.
- **Accessibility.** Guidelines now cover focus (2px at 2px offset), 44px targets, RTL mirroring rules, and a WCAG 2.2 AA checklist. A solid callout ground, an inverse block or the mark plate carries `data-ds-surface`, which re-points the one focus ring to a step that still holds 3:1 on it.
- **Preview.** Added `preview.html`, showing the tokens, both themes side by side, depth, motion and the key components. It links the three token files from beside it, uses system font fallbacks, and fetches nothing from outside the folder.
- **Compatibility.** Every 1.x variable is kept and marked deprecated, with a migration section in `guidelines.md`. Most hold their 1.x value; `--ds-radius-sm` to `-xl` and `--ds-size-caption` resolve to their 2.0.0 role instead, so a part-migrated page gets the medium's own units and the raised caption floor. The screen caption floor rises from 12px to 14px.

## 1.1.0 - 2026-09-17

- Added a dark counterpart for every slide master (title, section, stat, chart, closing): a whole-deck setting, never mixed within one deck. A4 print documents remain light-only.
- Added dark-ground, dark-text, hairline, and accent tokens to `tokens.css` for the deck-only dark theme.

## 1.0.0 - 2026-09-17

- Initial public release: tokens, guidelines, and content rules for reports, decks, and briefs, generalised from an internal v2.0 system into a standalone, unbranded design system.
