# Risk Register UI

A UI system for a risk register workspace: a register table, a guided entry form, a setup wizard, and an AI assistant in a chat panel beside the work. Light only, fully bilingual in left-to-right and right-to-left languages, and WCAG 2.2 AA in every style. It shares its visual language with the other systems here: one accent, flat quiet surfaces, generous white space.

Version 1.1.0 adds what the product learned once built, through two UX and UI passes: field rows that fold, a sortable register with a fixed head row, Remove with Undo, picked and greyed states, the assistant's replies as plain words, one steady full-width frame with text that grows on big screens, the chat as a docked third of the window or an island on a laptop, and cards that show what the assistant proposes before anything is saved. See `CHANGELOG.md`.

## Use it

```html
<link rel="stylesheet" href="tokens.css">

<html data-ds-style="2" dir="rtl">
```

`data-ds-style` is optional; without it the page takes style 1. Set it once for the whole page (an admin picks it in setup). The same attribute on a single element paints only that element, which is how a setup screen can show a small sample of each style. Components read the tokens only, so a style reaches every component with no extra rules. Open `preview.html` to see the three styles side by side.

## Visual foundations

**Three styles, one product.** Style 1 *Plain* (flat white, a warm-tinted chat panel touching the work area, thin grey lines, no shadow) is the default. Style 2 *Porcelain* (islands: the two regions float on a warm paper ground as lit white panels with large corners and a soft warm lift) and style 3 *Paper* (flat islands: the same two panels on the paper ground with 12px corners, one warm edge and no shadow) are complete alternatives. A style is the whole look, never a tint, and it changes the look only: every element, concept, behaviour and layout is identical in all three.

**Shared by every style.** The one accent, a white top bar, the four level colours with soft fills and dark words, the picked, greyed, danger and Undo colours, the type families and sizes, spacing, control sizes, the frame and the chat panel's measurements.

**Colour means level.** Four level colours, used for a risk's level and nothing else: a chip with its score in a block of the full colour, for example *7 High*. Statuses are light outlined pills with an icon, in shades that can never be read as a level. A word always carries the meaning; colour only repeats it.

**The accent is for the person.** One main action per view, where they are, their own words in the chat. What they picked takes the picked colours. Never structure.

**One frame.** Top bar, chat panel, tab bar, title row, content box and action row sit in the same place on every screen and for every role. Only the content box scrolls.

**Chat panel at the reading start.** Left in a left-to-right language, right in a right-to-left language, with everything else mirrored to match. From a 1600px window it is a docked pane of one third, resizable and folding to a rail; under that it is an island at the bottom edge that opens into a card when asked. The person's messages sit at the reading start in their bubble; the assistant's replies are plain words at the reading end, with no box.

**Readable at 13.** Plain words a 13-year-old can follow, with specialist risk terms kept and explained where they appear. Nothing under 14px, body words 16px up to a 1600px window and growing with it above that, one 16px gap.

**A desk tool that fills the screen.** Built for desks from 1366px. The frame runs the full width of the work area, blocks fill it and split into two on a wide one, and at 200% zoom the work keeps the page with the island over its bottom edge, with no sideways scroll.

**Still unless something is happening.** Motion only while a state is happening (listening, working, done). Nothing moves on an idle screen.

## Components

Buttons in four kinds with picked and greyed states; the register table (a progress and filter bar, three-way sorting, a fixed head row, pinned columns, views as tags, a density switch, short headers, level chips and status pills); the entry interview (a steps rail, field rows that fold open one at a time, picture tiles for fixed answers, terms explained in place, cues for missing or wrong answers); the setup wizard; fields, error lines and empty states; lists with Remove and Undo, tick boxes with one bar for several at once, and a check before a send; the docked chat pane and the island (message box, modes, voice, attached files, Stop, helpers, next-step chips, Why and thumbs, the card of proposed values, the foot); sign in and the greeting with its slider. The rules for each are in `guidelines.md`.

## Content rules

- Short sentences, common words, one idea per line; about 40 words per step in the work area.
- Specialist terms keep their proper names and are explained where they appear.
- One word per label: no slash-joined labels, no words in quotation marks unless quoted, no needless brackets. Buttons are verbs of under four words.
- The assistant never says "I": the action is the subject (*Checking the level*).
- Natural wording in both languages; fixed names and terms stay as they are.
- No em dashes, no internal codes. Sample data is invented and generic.

## Files

```
tokens.css      shared tokens (accent, levels, type, space, controls, frame, chat panel) and the three styles
guidelines.md   the rules in full: styles, colour roles, levels and statuses, cues, the contrast table, type, layout, components, states, content, mixed direction, motion
preview.html    the three styles side by side on one page; it links tokens.css beside it and fetches nothing
CHANGELOG.md    dated changes to this system
```
