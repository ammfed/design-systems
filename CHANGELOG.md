# Changelog

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
