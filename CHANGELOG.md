# Changelog

## 2.3.0 - 2026-10-05

- Material Agent Chat 1.0.0: a new system for a staff tool with an AI assistant beside data-heavy screens, built on Material 3 (layout, shape, elevation, state layers, motion and component anatomy) and filled with one warm accent, a neutral scale, the repo's type families and one outline icon set referenced by name with its licence. Light and opt-in dark roles with a measured WCAG 2.1 AA table, Material 3 type roles, the components a data-heavy screen needs, a data table, filter bar and empty state, the agent surfaces (chat sidebar, full-page chat, message, input, suggestion chips, result card, approval card, draft field, agent progress), a mapping to a typical chat framework's theme variables and slots, and a preview page.
- Risk Register UI 1.1.0: what the product learned once built, through two UX and UI passes. The assistant's replies are plain words with no box and the person's messages sit at the reading start; field rows keep their titles and fold open one at a time; the register sorts three ways with a fixed head row and pinned columns; buttons come in four kinds with picked and greyed states; Remove has an Undo bar; one steady full-width frame with text that grows on big screens; the chat as a docked third of the window or an island at the bottom edge on a laptop; cards that show what the assistant proposes before anything is saved, next-step chips, Stop, attached files and several rows at once; one ink focus ring on every button, in the light accent on the Undo bar. The contrast table is remeasured and every pair passes in every style.

## 2.2.0 - 2026-09-29

- Risk Register UI 1.0.0: a new system for a risk register workspace. Three complete styles on one set of token names (Plain, the default; Porcelain and Paper, which set the chat panel and the work area as islands on a paper ground) that change the look only, a shared accent and top bar, four level colours used for level alone, status pills that never read as a level, rules for the register table, the entry interview, the setup wizard and the assistant panel at the reading start in both directions, content readable at 13, a measured WCAG 2.2 AA contrast table for each style, and a preview page.

## 2.1.0 - 2026-09-29

- Documents: content rules for writing the argument before the layout, one term per label, no em dashes, no internal codes or speaker notes in anything sent out, and visuals only where they are the clearest way to show the point. Tokens unchanged.
- Product UI: a screens-and-flows section (readable at 13, one fixed frame, the fewest steps, the right control for each choice, status and level kept apart, small wins only), table cells with words at the start and small numbers centred, the rule that a second look changes the whole skin, and one term per label.
- Agent Chat UI: no keyboard icon in the message box, a box that grows to six lines, a dock the user can resize between 360 and 520px, an assistant that never says "I", rules for several assistants in one thread, a calm thread option, and calm motion in reading order.

## 2.0.0 - 2026-09-23

- Documents: 42 light and dark colour roles, with the accent kept for people. Adds an opt-in dark theme (`tokens-dark.css`), eleven type roles sized per medium (fluid on screen), density modes, depth and materials, and motion tokens with a reduced path (`motion.css`). Every role pair passes WCAG 2.2 AA in both themes, and a `preview.html` that links those files shows it all.
- Product UI: colour by role (the accent reserved for the user, a separate machine colour for model output), a complete opt-in dark theme with every pair measured at WCAG 2.2 AA, fluid type roles, density modes, depth and materials, named motion with a reduced-motion path, RTL motion mirroring, filled-in tables, dashboards, navigation and forms, and a preview page that fetches nothing.
- Agent Chat UI: role tokens, an opt-in dark theme, a type scale with named roles, elevation and a glass material, motion tokens and transitions, density modes, a measured WCAG 2.2 AA contrast table for both themes, five new components including a required surface footer, and a preview page that loads only the system's own stylesheets. 1.x token names stay as aliases.

## 1.1.0 — 2026-09-17

- Documents: added a dark counterpart for every slide master, a whole-deck setting.
- Product UI: added an opt-in dark theme for internal command views, AI-content chip tokens, and a marketing hero pattern note.
- Agent Chat UI: source unchanged, re-checked and confirmed current.

## 1.0.0 — 2026-09-17

- Initial public release: three unbranded design systems (Documents, Agent Chat UI, Product UI), a general UX-patterns note, a decision-card review-page pattern, and a standing visual-preferences guide.
