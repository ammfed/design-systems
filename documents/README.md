# Documents

A design system for reports, decks and briefs, and for reading them on screen. It is not a web UI kit. Its building blocks are page furniture (covers, contents, dividers, running headers, tables, callouts, key facts, captions, signature blocks), slide masters for a 16:9 deck, and two screen viewers: a deck viewer and a reading view.

Version 2.0.0. Open `preview.html` to see the tokens and components in light and dark side by side.

## Design direction

Structure in ink, generous space, one strong rule where a page needs one, and the accent kept for people. Light by default with an opt-in dark theme for screens. Fully bilingual, with mirrored right-to-left pages for the second language. The palette is shared with the other two systems in this repo; the type roles, media and layout rules here are specific to print, slides and long-form reading.

## Content rules

- Sentence case everywhere: headings, table headers, labels. No all-caps in running text.
- A plain, formal voice. The document speaks as the organisation, not "we" or "I"; the reader is addressed directly only in correspondence.
- Numbers: Latin digits in both languages, thousands separators, the unit after the value, and numbers spelled out when they open a sentence. An unknown value reads "Not yet known"; a forecast is shown as a range.
- Single quotation marks, the Oxford comma, and "and" written out rather than "&".
- Bold at most once or twice per paragraph. Italics for emphasis, citations and defined terms. Underline only for links.
- No emoji, decorative Unicode, exclamation marks, taglines or filler.
- Slides: one idea per slide, at most six bullets, text capped at about 60% of the slide width when there is no supporting graphic.
- Every table has a header row and a caption above it, every figure has a caption below it, and every image has alt text.

## Visual foundations

**Colour.** Components use roles (`--ds-ink`, `--ds-paper`, `--ds-rule-strong`, `--ds-series-1` and the rest), never the ramps. Structure is ink: titles, rules, table headers, bullets and chart series are neutral. The accent (the gold ramp) marks a person only: the bar beside their quoted words, their name, a signature. Supporting hues (blue, amber, red, green) appear only in note, important, warning and success callouts and in status cells. Every role pair passes WCAG 2.2 AA in both themes; the numbers are in `guidelines.md`.

**Dark theme.** Opt-in, for screens, and for a whole deck or document at a time, never mixed slide by slide. Load `tokens-dark.css` and set `data-ds-theme="dark"`; every role keeps its name, so components need no dark variants. Offer it as a moon icon. Print is always light.

**Type.** Eleven named roles, from hero to caption plus a light figure role. Each role has a size per medium: fluid `clamp()` sizes on screen (360 to 1440px), points in print, pixels on a 1920 x 1080 slide. A heading family and a body family, with a second pair swapped in by direction; the second script keeps the same sizes, takes no tracking and gets taller lines. Nothing goes below the floors: 14px on screen, 8pt in print, 24px on slides. Left-align the primary language and right-align the mirrored one; never justify either.

**Layout and density.** A4 pages use 12mm margins and an 8 x 10 grid with 4mm gutters, with a protected column for a mark or a full-bleed image. Slides use a 48px margin, a 12 x 6 grid, registration ticks, a rail, and a hairline progress line. The reading view runs at a 72ch measure. Space comes in eight steps per medium, multiplied by a density: compact, comfortable or spacious.

**Depth and materials.** Inside a page there are no shadows: paper, a tonal plate, a recessed well and, at most once per page, an inverse block. On screen, the sheet sits on a canvas with a soft shadow, and viewer chrome is frosted glass with a float shadow and a rim. Glass turns solid when the reader asks for less transparency. Print drops both.

**Motion.** Short, one-way and once: content rises, accent lines draw, bars grow from the baseline, slides enter from the direction of travel. The keyframes and attribute hooks live in `motion.css`. Under reduced motion, only a short fade on the slide change remains; `data-ds-motion="off"` and print remove everything.

**Bilingual layout.** The second-language version of a page is a full mirror: grid, mark position, margins, protected column, header and footer sides, callout rules and quote bars all flip, and bar charts grow from the right. Time axes keep their order. Arrows, carets and quotation marks mirror; other icons do not.

## Iconography

A single outline icon family, regular weight, at least 24px, with visible text or an accessible name on every icon. Modes are icons rather than worded buttons: a moon for dark, three line icons for density, a grid for overview, corners for fullscreen, each with `aria-pressed` or `aria-checked`. No icon font, no emoji, and no Unicode glyphs standing in for icons.

## Files

```
tokens.css        light roles, materials, type roles, space, density, layout and motion tokens (the default)
tokens-dark.css   the opt-in dark theme: the same role names with dark values, forced light in print
motion.css        keyframes and attribute hooks (rise, draw, grow, trace, enter, fade), with the reduced path
guidelines.md     roles, type, space, depth, motion, components and their states, RTL, focus and contrast in full
preview.html      shows all of the above in light and dark; links the three files above and fetches nothing else
CHANGELOG.md      dated changes to this system
```

## Open questions

Font licensing for offline and print production, the exact slide aspect ratio for older print formats, and a reversed mark variant are all still open. This system ships a working default for each and notes it rather than blocking on it.
