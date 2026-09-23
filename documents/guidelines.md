# Documents: guidelines

How the tokens in `tokens.css`, `tokens-dark.css` and `motion.css` combine into report pages, slides and on-screen reading views. `preview.html` shows every part below in both themes. The role, type and contrast tables are generated from the same source as the token files, so the numbers here match the CSS.

## 1. Principles

- **Structure is ink.** Titles, rules, table headers, bullets and chart series are neutral. Space, weight and one strong rule organise the page.
- **The accent marks a person.** The gold ramp appears only beside someone's own words: the bar beside a quotation, the speaker's name, a signature. It never colours titles, rules, headers, bullets, bars, chart series or grounds.
- **Light by default, dark on request.** Dark is a screen theme for a whole deck or document, offered as a moon icon. Print is always light.
- **One role, three media.** Screen, print (A4) and slide (1920 x 1080) each have their own units. A component asks for a role such as `heading`, and the medium supplies the size.
- **Nothing small unless it earns its place.** Captions are the one small size, and each medium has a floor.
- **Motion once, one way.** Content arrives and settles. Nothing loops or bounces.

## 2. Switches

Load `tokens.css`, then `tokens-dark.css` if you offer dark, then `motion.css` if anything animates.

| Attribute | Values | Changes | Set it on |
|---|---|---|---|
| `data-ds-medium` | `screen` (default), `print`, `slide` | Type, space, radius and motion distance units | The page, slide or view root |
| `data-ds-theme` | `light` (default), `dark` | Colour roles, shadows and glass | The whole deck or document; needs `tokens-dark.css` |
| `data-ds-density` | `compact` 0.75, `comfortable` 1, `spacious` 1.25 | The multiplier on every space step | A page, a table or a deck |
| `data-ds-motion` | `off` | Removes all motion | The root, or a view with its own motion control |
| `data-ds-surface` | `solid`, `inverse` | Re-points the focus ring so it still holds 3:1 on that ground | A solid callout or an inverse block |
| `dir` | `ltr`, `rtl` | Families, tracking, leading, mirroring and motion direction | `html` or the document root |

## 3. Colour roles

Components use roles, never the ramps. Every role has a light and a dark value under one name, so no component needs a dark variant.

<!-- ROLES:START -->
| Token | Light | Dark | Use |
|---|---|---|---|
| `--ds-ink` | neutral-800 #232528 | neutral-100 #E1E3E5 | Body text |
| `--ds-ink-strong` | neutral-900 #1B1D21 | white-50 #FFFFFF | Headings, figures, the one thing read first |
| `--ds-ink-muted` | neutral-500 #5F646D | neutral-300 #9EA2A9 | Captions, labels, metadata |
| `--ds-ink-inverse` | white-50 #FFFFFF | neutral-900 #1B1D21 | Text on an inverse block |
| `--ds-canvas` | white-300 #F2F2F2 | neutral-950 #0E0F12 | Screen only: the desk a page or slide sits on |
| `--ds-paper` | white-50 #FFFFFF | neutral-900 #1B1D21 | The page or slide ground |
| `--ds-plate` | white-200 #F7F7F7 | neutral-800 #232528 | A tonal block on the paper: key facts, key message, zebra rows |
| `--ds-well` | white-300 #F2F2F2 | neutral-950 #0E0F12 | A recessed field: section-divider field, appendix wells |
| `--ds-inverse` | neutral-900 #1B1D21 | white-50 #FFFFFF | An inverse block, used at most once per page |
| `--ds-glass` | rgb(255 255 255 / .86) | rgb(27 29 33 / .86) | Screen only: viewer chrome floating over content |
| `--ds-scrim` | rgb(14 15 18 / .45) | rgb(14 15 18 / .55) | Photo overlay under text, 30 to 60% black |
| `--ds-mark-plate` | white-50 #FFFFFF | white-50 #FFFFFF | The white ground an organisation mark keeps in both themes |
| `--ds-hairline` | neutral-100 #E1E3E5 | neutral-700 #3E4046 | Row rules, separators, tracks |
| `--ds-rule` | neutral-200 #C3C6CB | neutral-600 #4B4F58 | Signing lines, registration ticks, stronger separators |
| `--ds-rule-strong` | neutral-800 #232528 | neutral-100 #E1E3E5 | Table header and total rules, the accent line |
| `--ds-series-1` | neutral-800 #232528 | white-100 #FCFCFC | Series 1, meter fill, current milestone |
| `--ds-series-2` | neutral-400 #797E86 | neutral-400 #797E86 | Series 2, ranges, the rest |
| `--ds-series-track` | neutral-100 #E1E3E5 | neutral-700 #3E4046 | Meter and chart tracks |
| `--ds-marker` | neutral-500 #5F646D | neutral-300 #9EA2A9 | List bullets and numbers |
| `--ds-person` | gold-700 #7C5E24 | gold-300 #D7BC6D | A person's name beside their own words |
| `--ds-person-mark` | gold-500 #B68A35 | gold-400 #CBA344 | The bar beside a person's words |
| `--ds-person-tint` | gold-50 #F9F7ED | neutral-800 #232528 | Ground under a person's words (a neutral plate in dark) |
| `--ds-focus` | amber-700 #B2550B | amber-500 #F29F0E | Keyboard focus ring, 2px, 2px offset |
| `--ds-note-bg` | blue-50 #E7F5FF | blue-950 #071C5F | Note ground |
| `--ds-note-fg` | blue-700 #0033D6 | blue-300 #81C1FF | Note title and icon |
| `--ds-note-rule` | blue-600 #043DFF | blue-400 #4F98FF | Note start rule |
| `--ds-important-bg` | amber-50 #FFFBEB | amber-950 #441B04 | Important ground |
| `--ds-important-fg` | amber-700 #B2550B | amber-300 #FAD44F | Important title and icon |
| `--ds-important-rule` | amber-600 #D67909 | amber-400 #F8C027 | Important start rule |
| `--ds-warning-bg` | red-50 #FEF2F2 | red-950 #430E0C | Warning ground |
| `--ds-warning-fg` | red-700 #B52520 | red-300 #FAAAA7 | Warning title and icon |
| `--ds-warning-rule` | red-600 #D83731 | red-400 #F47A75 | Warning start rule |
| `--ds-success-bg` | green-50 #F3FAF4 | green-950 #0F2415 | Success ground |
| `--ds-success-fg` | green-700 #2F663C | green-300 #A0D5AB | Success title and icon |
| `--ds-success-rule` | green-600 #3F8E50 | green-400 #6FB97F | Success start rule |
| `--ds-key-bg` | white-200 #F7F7F7 | neutral-800 #232528 | Key message ground |
| `--ds-key-fg` | neutral-900 #1B1D21 | white-50 #FFFFFF | Key message title |
| `--ds-key-rule` | neutral-800 #232528 | neutral-100 #E1E3E5 | Key message start rule |
| `--ds-note-solid` | blue-700 #0033D6 | blue-700 #0033D6 | Solid note ground |
| `--ds-important-solid` | amber-700 #B2550B | amber-700 #B2550B | Solid important ground |
| `--ds-warning-solid` | red-700 #B52520 | red-700 #B52520 | Solid warning ground |
| `--ds-success-solid` | green-700 #2F663C | green-700 #2F663C | Solid success ground |
<!-- ROLES:END -->

- **Callouts.** Soft is the default: a 50-shade ground, a 700-shade title and a 600-shade start rule. Solid puts white on the 700 shade, so white text passes at body size. Key message is ink, not a hue. In dark, grounds move to the 950 shade, titles to 300 and rules to 400.
- **Supporting hues** (blue, amber, red, green) appear only in callouts and status cells, never as decoration. Chart series are ink and grey; a third series is a hatch, not a hue.
- **Mark plate.** An organisation mark drawn for white paper keeps its white ground in both themes.
- **More contrast.** Under `prefers-contrast: more`, muted text, hairlines and series 2 step one shade toward the ink in both themes.

## 4. Type

Two families by role, heading and body, with a second pair swapped in by direction: Inter and Roboto for Latin, Alexandria and Noto Kufi Arabic for the second script. The families are named only, never shipped; each falls back to the system sans.

<!-- TYPE:START -->
| Role | Screen (fluid, 360 to 1440px) | Print | Slide (1920 x 1080) | Weight | Use |
|---|---|---|---|---|---|
| hero | 40 to 62px / 1.05 | 32 / 42pt | 136px / 1 | 700 | Cover title, title-slide title |
| title | 32 to 48px / 1.1 | 32 / 38pt | 100px / 1.05 | 800 | Chapter and section-divider title |
| heading | 26 to 32px / 1.2 | 24 / 29pt | 56px / 1.1 | 800 | Section heading, slide heading |
| subheading | 20 to 26px / 1.3 | 18 / 22pt | 44px / 1.2 | 700 | Sub-section heading |
| minor | 18px / 1.4 | 13.5 / 16pt | 32px / 1.3 | 700 | Minor heading, column head |
| lead | 18 to 22px / 1.5 | 14 / 20pt | 44px / 1.35 | 400 | Standfirst, subtitle, the quote |
| body | 16 to 18px / 1.6 | 10 / 14pt | 32px / 1.5 | 400 | Running text |
| small | 16px / 1.5 | 9 / 12pt | 28px / 1.4 | 400 | Table cells, dense lists |
| label | 14px / 1.43 | 9 / 11pt | 24px / 1.3 | 500 | Table headers, rails, running headers |
| caption | 14px / 1.5 | 8 / 11pt | 24px / 1.4 | 400 | Captions, sources, footnotes (the one small size) |
| figure | 48 to 76px / 1 | 36 / 36pt | 200px / 0.9 | 200 | Key figures, light numerals |
<!-- TYPE:END -->

Use a role as a set:

```css
font-size: var(--ds-type-heading-size);
line-height: calc(var(--ds-type-heading-leading) * var(--ds-script-display));
font-weight: var(--ds-type-heading-weight);
letter-spacing: var(--ds-type-heading-tracking);
```

- Display roles (hero, title, heading, subheading, minor, figure) take `--ds-script-display`. Text roles (lead, body, small, label, caption) take `--ds-script-text`. Both are 1 for Latin.
- Screen sizes are exact `clamp()` lines between a 360px and a 1440px viewport, in rem, so the reader's text-size setting still scales them. Print leading is a length in points; screen and slide leading is unitless. Both work in the `calc()` above.
- **Floors:** on screen, 14px for captions and labels and 16px for text. In print, 8pt for captions, 9pt for tables and 10pt for text. On slides, 24px for captions and labels and 32px for text.
- Left-align Latin, right-align the second script, never justify. Underline links only. Space paragraphs; never indent first lines. Sentence case. Tables and figures use tabular lining numerals (`--ds-numerals`). Weight comes from the role, at most five weights in a document. Headings balance their lines. The hero never sits beside a caption.

## 5. Space, density and layout

- **Space:** eight steps per medium, `--ds-space-1` to `-8`. Screen 4, 8, 12, 16, 24, 32, 48, 64px; print 1, 2, 3, 4, 6, 8, 12, 16mm; slide 8, 16, 24, 32, 48, 64, 96, 128px. Use `calc(var(--ds-space-4) * var(--ds-density))`.
- **Density:** compact 0.75 for appendix tables and dense reference pages, comfortable 1 by default, spacious 1.25 for slides read at a distance or a single key table. Density never changes type size or page margins.
- **Radii:** `--ds-radius-1` to `-3` are 4, 8 and 12px on screen, 1, 2 and 3mm in print, and 6, 12 and 16px on slides. They apply to callouts, plates and viewer chrome. Pages and tables stay square.

| Format | Size | Margin | Grid |
|---|---|---|---|
| A4 portrait (reports, briefs) | 210 x 297mm | 12mm all sides | 8 columns x 10 rows, 4mm gutters |
| A4 landscape | 297 x 210mm | 12mm | 10 x 8 |
| Slide | 1920 x 1080px | 48px | 12 x 6, 24px gutters |
| Screen reading view | Fluid | 20 to 64px | 72ch measure; a contents rail from 1024px |

The outer page column nearest the spine (33mm) holds a mark or a full-bleed image only.

## 6. Depth and materials

- **Inside a page:** paper, then plate (key facts, key message, zebra rows), well (a recessed field, with an optional rim) and inverse (at most once per page). Nothing inside a page casts a shadow.
- **On screen:** the sheet sits on the canvas with `--ds-shadow-sheet`. Viewer chrome (a deck toolbar, a reading header) is glass: `--ds-glass` with a 16px blur and raised saturation, `--ds-shadow-float` and `--ds-rim`. Glass never appears inside a document and never prints.
- **Dark:** shadows deepen and gain a faint light edge, so a sheet still separates from a dark canvas.
- **Fallbacks:** glass turns solid under `prefers-reduced-transparency` and where `backdrop-filter` is unsupported. Print drops shadows and forces light.

## 7. Motion

| Token | Normal | Reduced | Use |
|---|---|---|---|
| `--ds-dur-quick` | 120ms | 0ms | Hover and press colour in viewer chrome |
| `--ds-dur-swift` | 200ms | 0ms | Theme and density cross-fade |
| `--ds-dur-steady` | 360ms | 120ms | Slide change and overview; a fade only when reduced |
| `--ds-dur-reveal` | 560ms | 0ms | Slide content entrance, bars growing from the baseline |
| `--ds-dur-draw` | 900ms | 0ms | The accent line under a slide title |
| `--ds-dur-count` | 1400ms | 0ms | Key figures counting up, once |
| `--ds-dur-trace` | 2200ms | 0ms | Hairline fields drawing in, once |

- **Easing:** `--ds-ease-standard` for colour and opacity, `--ds-ease-enter` for anything arriving, `--ds-ease-exit` for anything leaving. Stagger is 60ms. The rise distance is 12px on screen, 24px on slides and 0 in print.
- **Hooks** in `motion.css`: `data-ds-rise`, `data-ds-draw`, `data-ds-grow="x|y"`, `data-ds-trace`, `data-ds-enter` (a slide change; `"prev"` reverses it) and `data-ds-fade` (a theme or density cross-fade). `style="--ds-i: 2"` sets the stagger index. Draws and horizontal growth start from the right in RTL, and slide changes enter from the direction of travel.
- **Reduced path:** under `prefers-reduced-motion`, every duration is 0 except the slide change, which keeps a 120ms fade. `data-ds-motion="off"` and print remove everything. Figures that count up show their final value at once.
- Motion plays once per view. Nothing loops, bounces or autoplays past one pass, and nothing uses parallax.

## 8. Components

### Page furniture

- **Page (A4).** 12mm margins. Running header: the document title and section in the label role, ink-muted, over a hairline. Running footer: the organisation line, the classification in ink at weight 700 when set, and the folio in Latin digits on every page after the cover. The mark sits on its plate in the top start corner.
- **Cover.** The hero title in ink-strong over a 24mm accent line in `--ds-rule-strong`, a subtitle in the lead role, and a meta line (version, classification) at the foot. Behind it: a photograph (text only over `--ds-scrim`) or a hairline pattern field. On screen it may be dark; it is always mirrored in RTL.
- **Title page.** The title role, a lead, and a meta block: version, date, status, classification, owner and pages, as a two-column definition list on hairlines.
- **Contents and agenda.** Contents lists number, title and page, with a hairline above each level-1 entry that keeps its level-2 entries in the group. Agenda uses large light numbers; the current item takes ink-strong and a start bar while the rest step back. Both are a `nav` with `aria-current`.
- **Section divider.** `field`: a title panel on paper beside a well field carrying an outlined numeral in the rule colour. `plain`: the title panel alone. The section number uses Latin digits in the label role.

### Content blocks

- **Data table.** The header row sits in the label role, ink-strong, over a strong rule. Hairline body rows, with optional zebra rows on plate. Numbers are end-aligned tabular digits, with units in the header, never in cells. Row headers are `th scope="row"`. It supports these states:
  - **Group row:** a label spanning the table.
  - **Subtotal:** over a rule.
  - **Highlighted row:** weight plus a start bar.
  - **Total:** over a strong rule.
  - **Status cell:** an icon and a word. Done and on track in the success hue, at risk in the important hue, off track in the warning hue, pending muted.
  - **Footnote marker:** numbered, with the notes under the table.
  - **Empty cell:** an en dash read as "No data".
  - **Total row with no total for a column:** the cell stays blank.
  - **On screen:** a sticky header, and sideways scroll inside a focusable, labelled region.
  - **Density:** all three densities.
- **Callout.** Note, important, warning, success or key; soft or solid. An icon, a title and a body, with a start rule that mirrors in RTL. Callouts carry information, never decoration.
- **A person's words.** The only place the accent appears. A `person-tint` ground and a `person-mark` start bar. The name is in `--ds-person` and the role title is muted. Markup is `figure`, `blockquote` and `figcaption`; a citation is required.
- **Key facts.** Two to four facts per row. The value is in the figure role (weight 200) and the unit in the lead role. One fact may take emphasis while the others step back to ink-muted. A fact can carry a meter (progress with a target tick, or a count such as "5 of 7"), or a delta with an arrow and words. An unknown value reads "Not yet known", never an invented number.
- **Executive summary.** A lead sentence, then short paragraphs or bullets, on a plate or under a top rule. Its body is never smaller than the document body.
- **Caption.** "Figure 3. Title" or "Table 1. Title", with the label at weight 600. Table captions sit above the table and figure captions below the figure, each followed by the source. No dash between number and title.
- **List.** Round markers in `--ds-marker`. Nested items take an en dash. Ordered lists use Latin digits and a full stop.
- **Signature and approvals.** Prepared, reviewed and approved rows. Each has a muted label, signing space above a `--ds-rule` line, the name at weight 600, and the role and date in the caption role.
- **References and appendix.** An appendix restarts with a divider labelled "Appendix A". References are numbered in Latin digits in the caption role. Links break anywhere to fit.

### Graphics

- **Charts.** Column, bar, line, range (a forecast drawn as a band with a central tick), share (parts of a whole on one bar, in place of a donut) and sparkline.
  - **Series:** series 1 in `--ds-series-1`, series 2 in `--ds-series-2`, a third as a hatch.
  - **Highlight:** one mark in ink and the rest in grey.
  - **Target:** a dashed line with its label at the start.
  - **Labels:** values are labelled in place. The drawing takes its box's size in the medium's own units, so labels stay at the label size.
  - **RTL:** bar, range and share grow from the right; time axes keep years left to right.
  - **Accessible name:** a one-line summary written from the data.
- **Meter.** `role="meter"` with its values. Track `--ds-series-track`, fill `--ds-series-1`, target tick `--ds-ink-muted`. Segmented for counts.
- **Timeline.** Done (filled), current (ring, `aria-current="step"`) and next (hollow), each with a spoken state.
- **Pattern.** A hairline lattice, grid, dot or contour field in the rule colour, used on covers and divider fields only, never behind text.

### Slide masters

Every slide shares the same furniture:

- Registration ticks at the 48px margin in the rule colour.
- The mark on its plate in the top start corner.
- A rail in the top end corner ("04 / 14", then the deck title).
- A hairline progress line with the folio on the bottom margin.

The masters are:

- **Title:** the hero, a lead subtitle, the date above the bottom ticks.
- **Section:** a title panel and a well field with an outlined numeral.
- **Content:** a 62% measure.
- **Two-column:** numbered column heads.
- **Chart:** a 5:7 split, with the caption under a hairline.
- **Table:** full width.
- **Image.**
- **Stat:** two to four figures with meters and deltas; one may take emphasis.
- **Agenda.**
- **Closing:** the mark on its plate over a hairline field.

Every colour is a role, so a deck turns dark as a whole.

### Viewers (screen only)

- **Deck viewer.** Slides scale to the stage. A glass toolbar holds previous, a live "n / N" counter, next, overview (a grid icon), dark (a moon, `aria-pressed`) and fullscreen (corners). Arrow keys follow the reading direction; Home and End jump; Escape closes the overview.
- **Reading view.** A sticky glass header holds the title, a density radiogroup of three icons and the moon. Below it sit a reading-progress hairline and, from 1024px, a contents rail. The article runs at 72ch and reflows to 320px wide with no sideways page scroll.

**Control states** (viewer chrome):

| State | Treatment |
|---|---|
| Rest | Ink icon on glass, 24px glyph in a 44px target |
| Hover | Plate ground, `--ds-dur-quick` |
| Pressed or checked | Inverse ground, `--ds-ink-inverse` icon; `aria-pressed` or `aria-checked` |
| Focus | 2px `--ds-focus` outline at 2px offset, `:focus-visible` |
| Disabled | Ink-muted, no hover, `aria-disabled="true"`, still focusable where it explains itself |

## 9. Second script and mirroring (RTL)

1. The page mirrors everything that has a side: grid, mark position, margins, the protected column, header and footer, callout start rules, quote bars, highlighted rows and agenda bars. Bar, range and share charts grow from the right. Use logical properties (`inset-inline-start`, `padding-inline-end`) throughout.
2. Time does not mirror. Column and line charts keep years left to right, because the digits are Latin.
3. The families swap by direction; the sizes stay the same. Tracking is 0, and leading takes the script factor: x1.28 for display roles and x1.14 for text.
4. Digits are Latin in both languages. The word between a count and its total is localised.
5. Text aligns to the start and is never justified.
6. Arrows, carets and quotation marks mirror. Clocks, checks, sun and moon do not. In the deck viewer, the arrow keys follow the reading direction.
7. In a bilingual row, the second script sits on the right and Latin on the left, on one baseline.

## 10. Focus and targets

- **Focus:** a 2px `--ds-focus` outline at 2px offset on every control, link, scroll region and summary. It is never removed and never the accent. Light: 5.00:1 on paper and 3.61:1 on glass in the worst case. Dark: 7.83:1 on paper and 5.05:1 on glass.
- **Focus on a solid or inverse ground:** the theme's own ring cannot hold 3:1 on a solid callout ground or on an inverse block, so those blocks carry `data-ds-surface="solid"` or `data-ds-surface="inverse"` and the one ring re-points to suit the ground it sits on. Solid grounds are the 700 shades in both themes and take a light amber step: 3.48:1 at the tightest, on solid important. An inverse block is the opposite of its theme paper and takes the darker step: 3.37:1 in light and 5.00:1 in dark. Any block carrying a control, a link or a scroll region on one of those grounds needs the attribute.
- **Targets:** viewer controls are 44 x 44px (`--ds-target-min`); WCAG 2.2 SC 2.5.8 asks for 24.
- **Keyboard:** every control is reachable in reading order. Wide tables scroll inside a focusable, labelled region.

## 11. Accessibility

WCAG 2.2 AA in both themes.

- **Contrast:** text is at least 4.5:1 (SC 1.4.3). Graphics, meters and focus are at least 3:1 (SC 1.4.11, 2.4.13). The focus ring holds that minimum on every ground it can sit on: a solid callout ground and an inverse block carry `data-ds-surface`, which re-points the ring instead of letting it fall below 3:1. Glass is measured over the worst case behind it. The full table is in section 12.
- **Meaning without colour:** status cells pair an icon and a word, and the timeline says done, current and next. Charts label values in place and highlight in ink against grey. Meters carry `role="meter"` and their values.
- **Structure:**
  - One `h1`, with headings in order.
  - `th scope` on row and column headers.
  - Captions bound with `figcaption`.
  - A citation on every quotation and alt text on every image.
  - The deck counter is an `aria-live` region.
  - The contents rail is a `nav` with `aria-current`.
- **Reading:** screen body text is 16 to 18px, with 1.6 leading and a 72ch measure. The view reflows at 320px wide with no sideways page scroll (SC 1.4.10).
- **Motion:** section 7 gives the reduced path. Nothing flashes, and nothing autoplays beyond one pass.
- **Print:** never below 8pt, always light, page numbers after the cover. Export tagged PDF.

## 12. Contrast

Computed with the WCAG 2.2 formula for every role pair in both themes; the generator refuses to write the tokens if any pair falls below its minimum.

<!-- CONTRAST:START -->
| Use | Pair | Needs | Light | Dark |
|---|---|---|---|---|
| Body text | `--ds-ink` on `--ds-paper` | 4.5:1 | 15.37 | 13.12 |
| Body text on a plate | `--ds-ink` on `--ds-plate` | 4.5:1 | 14.34 | 11.94 |
| Headings and figures | `--ds-ink-strong` on `--ds-paper` | 4.5:1 | 16.88 | 16.88 |
| Captions and labels | `--ds-ink-muted` on `--ds-paper` | 4.5:1 | 5.95 | 6.59 |
| Captions on a plate | `--ds-ink-muted` on `--ds-plate` | 4.5:1 | 5.55 | 6.00 |
| Labels in a well | `--ds-ink-muted` on `--ds-well` | 4.5:1 | 5.31 | 7.48 |
| Text on glass, worst case | `--ds-ink` on `--ds-glass` | 4.5:1 | 11.10 | 8.47 |
| Speaker name | `--ds-person` on `--ds-paper` | 4.5:1 | 6.03 | 9.08 |
| Speaker name on the quote ground | `--ds-person` on `--ds-person-tint` | 4.5:1 | 5.61 | 8.27 |
| Quote text | `--ds-ink` on `--ds-person-tint` | 4.5:1 | 14.31 | 11.94 |
| Quote rule | `--ds-person-mark` on `--ds-paper` | 3:1 | 3.15 | 7.12 |
| Series 1 and meter fill | `--ds-series-1` on `--ds-paper` | 3:1 | 15.37 | 16.45 |
| Series 2 | `--ds-series-2` on `--ds-paper` | 3:1 | 4.08 | 4.13 |
| Series 2 on a plate | `--ds-series-2` on `--ds-plate` | 3:1 | 3.81 | 3.76 |
| Focus ring | `--ds-focus` on `--ds-paper` | 3:1 | 5.00 | 7.83 |
| Focus ring on a plate | `--ds-focus` on `--ds-plate` | 3:1 | 4.67 | 7.13 |
| Focus ring on glass, worst case | `--ds-focus` on `--ds-glass` | 3:1 | 3.61 | 5.05 |
| Focus ring on a solid callout, worst case | `--ds-focus` under `data-ds-surface="solid"` on `--ds-important-solid` | 3:1 | 3.48 | 3.48 |
| Focus ring on an inverse block | `--ds-focus` under `data-ds-surface="inverse"` on `--ds-inverse` | 3:1 | 3.37 | 5.00 |
| Note title | `--ds-note-fg` on `--ds-note-bg` | 4.5:1 | 7.73 | 8.21 |
| Note body | `--ds-ink` on `--ds-note-bg` | 4.5:1 | 13.83 | 12.18 |
| Important title | `--ds-important-fg` on `--ds-important-bg` | 4.5:1 | 4.82 | 10.39 |
| Important body | `--ds-ink` on `--ds-important-bg` | 4.5:1 | 14.82 | 11.62 |
| Warning title | `--ds-warning-fg` on `--ds-warning-bg` | 4.5:1 | 5.91 | 8.70 |
| Warning body | `--ds-ink` on `--ds-warning-bg` | 4.5:1 | 14.05 | 12.49 |
| Success title | `--ds-success-fg` on `--ds-success-bg` | 4.5:1 | 6.41 | 9.82 |
| Success body | `--ds-ink` on `--ds-success-bg` | 4.5:1 | 14.48 | 12.72 |
| Key message | `--ds-key-fg` on `--ds-key-bg` | 4.5:1 | 15.75 | 15.37 |
| White on solid note | `#FFFFFF` on `--ds-note-solid` | 4.5:1 | 8.59 | 8.59 |
| White on solid important | `#FFFFFF` on `--ds-important-solid` | 4.5:1 | 5.00 | 5.00 |
| White on solid warning | `#FFFFFF` on `--ds-warning-solid` | 4.5:1 | 6.46 | 6.46 |
| White on solid success | `#FFFFFF` on `--ds-success-solid` | 4.5:1 | 6.80 | 6.80 |
| Text on an inverse block | `--ds-ink-inverse` on `--ds-inverse` | 4.5:1 | 16.88 | 16.88 |

66 pairs, all pass. Tightest text pair 4.82:1 (important title, light); tightest graphic pair 3.15:1 (quote rule, light).
<!-- CONTRAST:END -->

## 13. Iconography and imagery

- **Icons:** a single outline family at regular weight. At least 24px and 3:1, always with visible text or an accessible name. Modes are icons, not worded buttons: a moon for dark, three line icons in a radiogroup for density, a grid for overview, corners for fullscreen. Each carries `aria-label` and `aria-pressed` or `aria-checked`. No icon font, no emoji, and no Unicode glyph standing in for an icon.
- **Imagery:** real, contextual photography. Text goes on an image only over a 30 to 60% black `--ds-scrim`, never a coloured one. Ratios are 1:1, 3:4, 3:2, 16:9 and 21:9. The mark never sits on a photograph.

## 14. Content rules, in full

See the README for the condensed version. In full:

- Sentence case everywhere.
- A formal third-person voice for the organisation; second person only in direct correspondence.
- Consistent digit and unit formatting across both language versions.
- Single quotation marks, the Oxford comma, and conjunctions spelled out in running copy.
- Restrained emphasis.
- No emoji or exclamation marks.
- Slides are capped at six bullets and one idea.
- Every table, figure and image carries its caption or alt text.
- A forecast is shown as a range, and an unknown reads "Not yet known".

## 15. Do and don't

**Do**
- Build structure from ink, rules and space; keep the accent for a person's words, name and signature.
- Choose a role for every colour and every line of type.
- Offer dark as a moon icon on screen, for the whole deck or document; print light.
- Label values in place; caption every table and figure; cite every quotation.

**Don't**
- Use the accent for titles, rules, table headers, bullets, bars, chart series or grounds.
- Mix light and dark slides in one deck, or print a dark page.
- Justify, underline non-links, indent first lines, set all-caps headings, or go below the floors in section 4.
- Use donuts for parts of a whole, loop or bounce motion, or animate in print.
- Use worded toggles for modes, emoji, taglines or filler text.

## 16. Moving from 1.x

- Every 1.x variable is still defined; the old type, radius, motion and dark names are grouped at the end of `tokens.css` and marked deprecated. Most keep their 1.x value, but `--ds-radius-sm` to `-xl` and `--ds-size-caption` resolve to their 2.0.0 role, so a part-migrated page gets the medium's own units and stays above the caption floor.
  - `--ds-size-*` becomes the type roles.
  - `--ds-radius-sm` to `-xl` become `--ds-radius-1` to `-3`.
  - `--ds-motion-*` becomes `--ds-dur-*`.
  - `--ds-dark-*` becomes `tokens-dark.css`.
  - `--ds-dark-accent` becomes `--ds-person`.
- 1.x used the accent for rules, bullets, table headers, display titles and the first chart series. In 2.0.0 those move to `--ds-rule-strong`, `--ds-marker`, `--ds-ink-strong` and `--ds-series-1`.
- Dark reaches beyond decks to reading views and on-screen page previews. Print stays light.
- 1.x had no shadows at all. 2.0.0 allows them on screen only, on things that sit over the canvas.
- The smallest screen size rises from 12px to 14px.
