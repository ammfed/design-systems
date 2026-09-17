# Product UI

A UI component library for websites and product dashboards: gold as an accent, flat white surfaces, generous space, full bilingual LTR/RTL support, and a target of WCAG 2.1 AA throughout. It follows the same visual language as the other two systems here, expressed as reusable components rather than document layout.

Covers a public marketing/service website and an authenticated product/dashboard shell.

## Content rules

- Voice: professional, accessible, plain — speaking to a user directly, not at them.
- "You/your" for the user, "we" for the product or organisation. Example: *"We sent a confirmation to your email."*
- Sentence case everywhere — headings, buttons, labels, navigation.
- Buttons use actionable verbs, under four words: *Submit application · Save draft · Start*. One solid (filled) button per group, the rest secondary.
- Mark optional fields, never required ones. Error copy states what to do next, not just what went wrong.
- Errors and empty states use plain language, no error codes, no blame: *"We're working on a problem that's preventing this page from loading."* / *"No requests yet — requests you submit will appear here."*
- Full, natural translation for the second language, not transliteration; consistent tone across both.
- No emoji.

## Visual foundations

**Colour.** The accent colour appears only as accent, hover state, large display text, and a thin gradient bar in the header/footer. A slightly deeper shade of the same hue carries component fills (buttons, links) at an accessible 4.5:1 on white. Body text is a near-black neutral, muted text and borders are lighter neutrals, surfaces are white and a very light grey. Semantic colours (success, info, warning, error) are reserved for status and feedback, never decoration.

**Type.** A heading family and a body family for the primary direction, swapped for a matching pair in the mirrored direction. Headings run from roughly 20px to 76px across seven steps at decreasing weight as size increases toward the largest, most decorative step; body text runs from 12px to 30px. Base size never drops below 16px, paragraph line-height stays at 1.5 or higher, and a comfortable measure (60–100 characters) is kept for body copy. Left-align the primary direction, right-align the mirrored one, never justify either.

**Spacing and shape.** A 4px spacing scale; common component gaps at 8/16/24/28px; a six-column responsive grid with consistent container widths per breakpoint. Radii scale from small (badges, checkboxes) through medium (buttons, inputs, cards) to fully rounded (avatars, pagination, toggles).

**Backgrounds.** Flat white or a very light grey band. No textures, no gradients except the header/footer accent bar and a couple of clearly-scoped exceptions (a progress fill, a card image overlay). Background patterns, where used at all, stay subtle and appear only on inner pages.

**Imagery.** Real, naturally-lit photography with simple backgrounds; a dark overlay under any text on a photo, never a coloured one. A small set of fixed aspect ratios. Geometric, solid-colour illustration only — no photographic collage, no stock-photo look.

**Dark theme (opt-in, separate stylesheet).** A second, near-black theme exists as its own stylesheet, never imported by default — load it explicitly and set a dark-mode attribute on the root when it's wanted. It's meant for internal, data-dense command views, not the public website or product portal, which stay light. Gold shifts to a lighter step so it still reads at 6.9:1 on the dark ground; surfaces step through three dark tones (page, card, raised); the mark's area stays on a white patch so it's never placed directly on the dark ground. Light and dark are never shown in the same view — a page is one or the other, never a runtime toggle mid-session.

**Elevation.** Flat by default, bordered rather than shadowed. A small shadow on inputs, a larger one on dropdowns/popovers/toasts, and a distinct modal shadow. Never a shadow on a logo or wordmark.

**Interaction states.** Hover moves a filled control one step darker (or a soft-tint control one step deeper); links gain an underline and shift one step in the accent scale; press uses colour only, no scale change. Focus is a solid 2px ring in a colour distinct from the primary action colour, offset outward for filled controls and inset for outline/link controls. Disabled drops opacity and removes pointer interaction.

**Motion.** A single easing curve for colour/background/border/shadow transitions at roughly 0.3s; toggles at roughly 200ms; no bounces, no entrance animations on page load; everything stops under reduced-motion preferences.

**Layout.** A fixed header (accent bar, then a logo row, then a navigation row) and a fixed footer bracket the page; content lives inside a per-section container, never one page-wide wrapper. Mobile-first; navigation collapses to a menu under roughly 1024px width.

**RTL.** Everything mirrors through logical (start/end) properties rather than hard left/right values; directional icons flip, functional icons (search, user, notification) do not; the header mark moves to the leading edge of the mirrored layout.

## Iconography

One icon family across three weights (regular for body text, bold for confirmations, a filled/duotone treatment for empty and state illustrations), minimum 24px, inheriting text colour by default with the accent reserved for feature icons and selected states. No icon font of the product's own, no PNG icons, no emoji, no hand-drawn glyphs.

## Components

Actions (button, link), forms (input, textarea, select, checkbox, radio, toggle, file input, range slider), navigation (breadcrumb, tabs, pagination, steps, dropdown, sidebar), data display (card, badge, avatar, accordion, blockquote, table, KPI tile, description list, timeline, status pill), feedback (alert, toast, modal, tooltip, popover, banner, drawer, progress, spinner, skeleton, empty state, error page), and layout blocks (header with mega menu, footer, hero).

## Marketing hero pattern

A subtle line-pattern sits behind a homepage hero, always under a protection fade so text stays legible; service cards and key stats reveal with a small staggered fade-in; a thin pattern divider introduces a stats band. Light-only, no colour tokens change — this is a motion and texture layer over the existing hero, not a new component.

## Files

```
tokens.css        colour, type, spacing, radius, elevation, and motion custom properties
tokens-dark.css    opt-in dark-theme tokens, not loaded by default (see Dark theme above)
guidelines.md     the rules above in full, plus the full component inventory and dark-theme token set
CHANGELOG.md      dated changes to this system
```
