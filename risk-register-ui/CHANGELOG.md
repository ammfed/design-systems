# Changelog — Risk Register UI

## 1.0.0 — 2026-09-29

- Initial public release: a UI system for a risk register workspace.
- Three complete styles on one set of token names (Plain, the default; Porcelain; Paper), picked with `data-ds-style`. Porcelain and Paper set the chat panel and the work area as islands on a paper ground. A style changes the look only, never an element, a behaviour or the layout.
- Shared across all three: one accent, a white top bar, four level colours as soft fills with dark words, type, spacing, control sizes, the frame and the chat panel's measurements.
- Colour means level: level chips with the score, and status pills with an icon in shades that never read as a level.
- Rules for the register table, the entry interview, the setup wizard, the chat panel at the reading start in both directions, sign in and the greeting, content readable at 13 with specialist terms kept and explained, and motion only while something is happening.
- A measured WCAG 2.2 AA contrast table for every text and control pair in each style, and a `preview.html` that shows the three styles side by side.
