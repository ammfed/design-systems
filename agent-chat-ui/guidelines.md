# Agent Chat UI — guidelines

## Colour roles

| Role | Token | Notes |
|---|---|---|
| Primary action | `--ds-color-gold-600` | Exactly 4.5:1 on white at 16px/500 weight |
| Accent (icons, header rule, hover target) | `--ds-color-gold-500` | Never a text-under-fill colour |
| Soft tint (user bubble, pills, selected) | `--ds-color-gold-50` on `--ds-color-gold-700` text | 5.6:1 |
| Body text | `--ds-color-neutral-800` | |
| Secondary text | `--ds-color-neutral-500` | |
| Border | `--ds-color-neutral-100` | |
| Disabled text | `--ds-color-neutral-300` | |
| Surface (page, cards, input) | white | |
| Surface (elevated, code, assistant bubble) | `--ds-color-neutral-50` | |
| Error | `--ds-color-red-700` text / `--ds-color-red-50` fill / `--ds-color-red-200` border | |
| Success | `--ds-color-green-700` text / `--ds-color-green-50` fill | |
| Focus ring | a distinct amber, not the primary hue | avoids the ring reading as "another button" |

## Icon role mapping

send → paper-plane · stop → stop · regenerate → arrow-clockwise · open → chat-bubble · close → caret-down · header-close → x · push-to-talk → microphone · activity/spinner → spinner · attach → paperclip · copy → copy · feedback → thumbs-up/thumbs-down · error → warning-circle · success → check-circle.

## Slot and label conventions

A chat-framework theming layer typically exposes:

- **Slots**: message view, scroll view, input, suggestion view, welcome screen, header, toggle button; nested assistant-message, user-message, toolbar, copy-button.
- **Labels**: header title, welcome message, input placeholder, disclaimer text — always sourced from the framework's label props, never hard-coded.
- **Icon props**: a name-to-glyph map matching the role mapping above.

Theme through these contracts only. Don't fork the framework's DOM or component internals to apply colour — every value here should be reachable through CSS custom properties on the framework's own theming attribute, plus the slot/label/icon props.

## Components (visual reference only)

A themed mirror of the framework's own pieces is useful for design work, but ships as reference, not production code: chat window shell (chat/popup/sidebar), message, message list, markdown renderer, code block, table, chat input, suggestions, suggestion pill, welcome screen, generative-content card, popup toggle, and state indicators (activity dots, spinner, error banner, success banner).
