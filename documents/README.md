# Documents

A design system for reports, decks, and briefs. It is not a web UI kit — its building blocks are page furniture: covers, dividers, running headers, tables, callouts, captions, and signature blocks, plus slide masters for a 16:9 deck.

## Design direction

Restrained decoration, one accent colour used sparingly, generous white space, dark neutral text on white, fully bilingual with mirrored right-to-left pages for the second language. The palette and type scale are shared with the other two systems in this repo; the layout rules here are specific to print and slide formats.

## Content rules

- Sentence case everywhere — headings, table headers, labels. No all-caps in running text.
- Plain, formal voice: the document speaks as the organisation, not "we/I"; the reader is addressed directly only in correspondence.
- Numbers: consistent digit style even in bilingual documents, thousands separators, unit after the value, spell out numbers that open a sentence.
- Single quotation marks, Oxford comma, "and" written out rather than "&".
- Bold at most once or twice per paragraph; italics for emphasis, citations, and defined terms; underline reserved for hyperlinks.
- No emoji, no decorative Unicode, no exclamation marks, no informal phrasing in formal documents.
- Slides: one idea per slide, at most six bullets, text capped at roughly 60% of slide width when there's no supporting graphic.
- Every table has a header row and a caption above it; every figure has a caption below it; every image has alt text.

## Visual foundations

**Colour.** One accent colour used for rules, bullets, and large display text only — it fails accessibility contrast at body-text size, so body text stays in a near-black neutral. A light tint of the accent marks quotes, key facts, and total rows. Supporting hues (blue, green, amber-brown, red) appear only inside note/success/important/warning callouts, never as decoration. At most one accent element competes for attention per page — a title rule, or a table header, or a pull quote, never all three at once.

**Type.** A serif-free heading family paired with a plain body family; a second pairing for the second language, swapped by document direction rather than by weight. Print and screen each get their own type scale so print sizes stay in points and screen sizes stay in pixels. Left-align the primary language, right-align the mirrored language, never justify either.

**Layout.** A fixed page grid (columns and rows with consistent gutters) reserves a protected margin column for a mark or full-bleed image; body text runs across the remaining columns. Slides use a wide-format grid with a consistent corner position for a mark, a consistent corner for a running label, and a consistent corner for a page/slide number.

**Shape and elevation.** No drop shadows — sections are separated with white space and a hairline rule, not elevation. Radii scale from small (badges, table corners) to large (feature blocks), used sparingly in print. Cards are bordered, not shadowed.

**Backgrounds and imagery.** White pages, no gradients, no background patterns on covers (a subtle pattern is acceptable elsewhere, kept very light). Photography is real and contextual, never stock-looking; text over a photo always sits on a dark overlay, never a coloured one. Illustration, when used, is a flat geometric style, not photographic.

**Motion.** Documents are static. Slide/deck previews may use a single restrained fade-and-rise on body content and a slow draw-in on an accent line, both disabled under reduced-motion preferences.

**Dark deck theme.** Slide masters (title, section, stat, chart, closing) each have a dark counterpart — near-black ground, white text, dimmed hairlines, mark on a white band. It's a whole-deck choice, never mixed slide-by-slide. A4 print documents stay light-only.

**Bilingual layout.** The second-language version of a page is a full mirror: grid, mark position, margins, protected column, and header/footer sides all flip. Punctuation marks that have a directional form (quotes, carets) mirror too; icons that aren't inherently directional do not.

## Iconography

A single icon family, regular weight paired with normal-weight text and bold weight paired with headings, minimum 24px, used sparingly and always next to a text label — icons alone never carry meaning. No icon font, no emoji, no Unicode glyphs standing in for icons.

## Files

```
tokens.css        colour, type, spacing, radius, and motion custom properties
guidelines.md     the rules above in full, plus a components list
CHANGELOG.md      dated changes to this system
```

## Open questions

Font licensing for offline/print production, the exact slide aspect ratio for older print formats, and a reversed/light logo variant are all still open — this system ships a working default for each and notes it rather than blocking on it.
