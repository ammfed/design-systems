# Risk Register UI

A UI system for a risk register workspace: a register table, a guided entry form, a setup wizard, and an AI assistant in a chat panel beside the work. Light only, fully bilingual in left-to-right and right-to-left languages, and WCAG 2.2 AA in every style. It shares its visual language with the other systems here: one accent, flat quiet surfaces, generous white space.

Version 1.0.0. See `CHANGELOG.md`.

## Use it

```html
<link rel="stylesheet" href="tokens.css">

<html data-ds-style="2" dir="rtl">
```

`data-ds-style` is optional; without it the page takes style 1. Set it once for the whole page (an admin picks it in setup). The same attribute on a single element paints only that element, which is how a setup screen can show a small sample of each style. Components read the tokens only, so a style reaches every component with no extra rules. Open `preview.html` to see the three styles side by side.

## Visual foundations

**Three styles, one product.** Style 1 *Plain* (flat white, the chat panel and the work area touching, thin grey lines, no shadow) is the default. Style 2 *Porcelain* (islands: the two regions float on a warm paper ground as lit white panels with large corners and a soft warm lift) and style 3 *Paper* (flat islands: the same two panels on the paper ground with 12px corners, one warm edge and no shadow) are complete alternatives. A style is the whole look, never a tint, and it changes the look only: every element, concept, behaviour and layout is identical in all three.

**Shared by every style.** The one accent, a white top bar, the four level colours with soft fills and dark words, the type families and sizes, spacing, control sizes, the frame and the chat panel's measurements.

**Colour means level.** Four level colours, used for a risk's level and nothing else: a chip with its score, for example *7 High*. Statuses are light outlined pills with an icon, in shades that can never be read as a level. A word always carries the meaning; colour only repeats it.

**The accent is for the person.** One main action per view, what the person chose, where they are, their own words in the chat. Never structure.

**One frame.** Top bar, chat panel, tab bar, title row, content box and action row sit in the same place on every screen and for every role. Only the content box scrolls.

**Chat panel at the reading start.** Left in a left-to-right language, right in a right-to-left language, with everything else mirrored to match. 400px wide, resizable between 360px and 520px, and folds to a rail.

**Readable at 13.** Plain words a 13-year-old can follow, with specialist risk terms kept and explained where they appear. Nothing under 14px.

**Still unless something is happening.** Motion only while a state is happening (listening, working, done). Nothing moves on an idle screen.

## Components

The register table (views as tags, a density switch, short headers, level chips and status pills), the entry interview (question groups as steps, one current question, visual answer choices, cues for missing or wrong answers), the setup wizard (a step bar, visual pickers for fixed options, a review step), the chat panel (message box, modes, voice, the assistant's and the person's lines), sign in and the greeting. The rules for each are in `guidelines.md`.

## Content rules

- Short sentences, common words, one idea per line; about 40 words per step in the work area.
- Specialist terms keep their proper names and are explained where they appear.
- One word per label: no slash-joined labels, no words in quotation marks unless quoted, no needless brackets.
- The assistant never says "I": the action is the subject (*Checking the level*).
- Natural wording in both languages; fixed names and terms stay as they are.
- No em dashes, no internal codes. Sample data is invented and generic.

## Files

```
tokens.css      shared tokens (accent, levels, type, space, controls, frame, chat panel) and the three styles
guidelines.md   the rules in full: styles, colour roles, levels and statuses, cues, the contrast table, type, layout, components, content, motion
preview.html    the three styles side by side on one page; it links tokens.css beside it and fetches nothing
CHANGELOG.md    dated changes to this system
```
