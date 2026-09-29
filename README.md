# Design Systems

Four small design systems for building formal, trust-sensitive software: long-form documents and decks, an AI chat assistant surface, a product/website UI kit, and a risk register workspace. They share one visual language (a restrained palette with a single accent reserved for a person, generous white space, bilingual LTR/RTL support) expressed through different token sets, because a report, a chat panel, a dashboard and a register each need different defaults.

Each system is self-contained: a `README.md` explaining its intent and rules, a `tokens.css` with the raw design tokens, a `guidelines.md` with the visual and content rules, and a `CHANGELOG.md`. Where a system has them, it also ships an opt-in dark token file, a motion token file, and a `preview.html` that shows the whole system on one page.

## Systems

| System | For | Folder |
|---|---|---|
| **Documents** | Reports, decks, briefs — page furniture, not a web UI kit | [`documents/`](documents/) |
| **Agent Chat UI** | A themed AI chat assistant surface (panel, sidebar, popup) | [`agent-chat-ui/`](agent-chat-ui/) |
| **Product UI** | Websites and product/dashboard UI components | [`product-ui/`](product-ui/) |
| **Risk Register UI** | A risk register workspace: register table, guided entry, setup wizard and an assistant panel, in three styles | [`risk-register-ui/`](risk-register-ui/) |

## Also here

- [`patterns/ux-patterns.md`](patterns/ux-patterns.md) — general UX patterns observed while studying comparable public dashboards, written as reusable patterns with no product or vendor names attached.
- [`decision-cards/`](decision-cards/) — a review-page format for presenting visual decisions one at a time, with a live visual preview per option.
- [`visual-preferences.md`](visual-preferences.md) — the standing visual, screen-flow and writing principles all the systems and the decision-card format are built to.

## Using this from an online design tool

Every `tokens.css` is a flat set of CSS custom properties (colour, type, spacing, radius, motion) with no build step. Import the token file for the system you need, and alongside it that system's dark and motion files where it has them, then follow that system's `guidelines.md` for how the tokens combine into layout, type, and content rules. Nothing here depends on a specific framework.

## License

Design tokens and written guidelines: use freely, attribution appreciated. No proprietary brand assets (logos, wordmarks, organisation names) are included — this is a values-only, unbranded system.
