# Agent Chat UI

A theme for an AI chat assistant surface — inline panel, sidebar, and popup — in a chat-framework-agnostic form: colour, type, shape, spacing and motion tokens, plus the slot and label conventions a typical chat-framework theming layer expects (message view, scroll view, input, suggestions, welcome screen, header, toggle button, and nested assistant/user/toolbar elements). It does not replace any chat framework's own component library — it themes it.

Three surfaces are covered, each in both text directions: an inline **chat panel**, a **sidebar** panel, and a floating **popup** with its own toggle. Light theme only for this release.

## Content rules

- Formal, plain, institutional tone. Second person to the user ("Ask a question", "Verify important information"); the assistant never speaks in an effusive first person. No exclamation marks, no emoji, no jokes.
- Sentence case everywhere; spell the product name out in full rather than using a nickname.
- Every string exists in both languages and is delivered through the framework's label/slot props — never hard-coded into CSS or DOM overrides. Digits use a consistent style in both languages.
- A disclaimer stays visible under the input: the assistant may make mistakes, verify important information.
- Labels are short imperatives: Send, Retry, Approve, Request changes.

## Visual foundations

**Colour.** One hue. The primary action colour sits at exactly the accessibility threshold for 16px/medium-weight text, so it is used at that size or larger. A brighter version of the same hue is accent-only — icons, a header rule, a hover state — never a background under white text. A soft tint of the hue marks user message bubbles, pills and selected states. Body text is near-black neutral; secondary text and borders are lighter neutrals; two surfaces only (white and a very light grey). Success and error each get one supporting hue, used only in confirmation and error contexts.

**Type.** Two family pairings, one per text direction, swapped by direction rather than duplicated per component. Chat text is never smaller than 16/24; timestamps, disclaimers and pills go down to 14/20; nothing drops below 12px. At most five weights on one screen.

**Spacing and shape.** A 4px spacing scale; panel padding roughly 24px; message gap roughly 16px; bubble padding 8/12. Controls, inputs and bubbles get a small radius; cards, the chat window and code blocks get a larger radius; badges, chips and the popup toggle are fully rounded.

**Elevation.** Inputs and chips carry a small shadow, cards and the toggle a medium one, modals a large one, and the floating window its own soft, wide shadow. No shadow anywhere is decorative — each marks a distinct elevation level.

**Backgrounds.** Flat white or very light grey only. No gradients, no glows, no textures, no photography behind the UI.

**Interaction states.** Hover darkens the primary colour by one step and lightens the soft tint by one step; message controls fade in rather than snapping in. Press uses colour only, no scale change beyond a chat framework's own small icon-button scale. Focus is a solid 2px ring in a colour distinct from the primary action colour, offset from the element. Disabled drops opacity to 30% (50% for soft-tinted elements) and removes pointer interaction.

**Layout.** A popup window is roughly 24rem wide and 600px tall; a sidebar is roughly 28rem wide and full height; both keep a fixed header, a pinned input at the bottom, and a scrolling message area between them. The mirrored-direction layout flips alignment so the user's own messages sit at the inline-end.

**Motion.** Activity indicator roughly 1.4s ease-in-out, a spinner at 1s linear, window open at roughly 200ms ease-out. No bounces.

## Iconography

One icon family, regular weight for body text, bold weight paired with headings, minimum 24px, rendered in the current text colour. A fixed mapping from icon name to role (send, stop, regenerate, open, close, push-to-talk, activity, attach, copy, feedback, error, success) keeps every instance of the assistant consistent. Directional glyphs (arrows, carets, the send icon) mirror in the reversed text direction; everything else stays put. No icon font, no emoji, no Unicode glyphs as icons.

## Files

```
tokens.css        colour, type, spacing, shape, and motion custom properties
guidelines.md     the rules above in full, plus the slot/label mapping
CHANGELOG.md      dated changes to this system
```
