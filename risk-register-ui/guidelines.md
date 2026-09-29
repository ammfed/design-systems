# Risk Register UI: guidelines

Version 1.0.0. The rules behind `tokens.css`. `preview.html` shows the three styles side by side.

## Styles

Three complete styles share one set of token names. The page picks one with `data-ds-style` on `<html>`; an admin chooses it once, in setup, and style 1 is the default.

| Style | Name | The look |
|---|---|---|
| 1 | Plain | Flat white page. The chat panel and the work area touch, split by one hairline. Thin grey lines, no shadow, small corners, a thin accent stripe over the top bar. Functional and familiar. |
| 2 | Porcelain | Islands: the chat panel and the work area float on a warm paper ground as two white panels, 16px apart, with 22px corners, a firm warm edge, a bright top rim and a soft warm lift. Cards inside take a soft depth, rounder corners and capsule pills; the assistant's lines sit in a cool grey box. |
| 3 | Paper | Islands, flat: the same two white panels on the paper ground, 16px apart, with 12px corners, one warm edge and no shadow. 8px corners on controls and no capsules, bold titles, the assistant's lines in a warm grey box with no edge. |

**A style is the whole look, never a tint.** Grounds, panels, lines, ink, both speech boxes, cue and status colours, corners, depth and title type all change together, on every screen, in every state and in both languages.

**A style changes the look only.** Elements, concepts, behaviour and layout are identical in all three. The islands in styles 2 and 3 are a look too: the same two regions in the same places and order, only set apart on the ground with space, corners and an edge. No screen gains, loses or moves anything when the style changes. If a design needs a new element to look right in one style, it is wrong in all three.

**Shared by all three:** the one accent, a white top bar, the four level colours, the type families and sizes, spacing, control sizes, the frame and the chat panel's measurements.

## Colour

### Roles

| Role | Tokens | Use |
|---|---|---|
| Ground | `--ds-ground` | The page behind the panels. White in style 1, warm paper in styles 2 and 3 |
| Panel | `--ds-panel`, `--ds-inset`, `--ds-hover`, `--ds-quiet` | Cards, tables and the chat panel; a second tone inside a panel (table head, a quiet question); row hover; a quiet button |
| Line | `--ds-line`, `--ds-line-strong`, `--ds-edge` | Hairlines between rows (decorative); control edges that must be seen (3:1); a card's edge |
| Islands | `--ds-island-gap`, `--ds-island-radius`, `--ds-island-edge`, `--ds-island-shadow` | How the chat panel and the work area sit on the ground: touching in style 1, floating apart in styles 2 and 3 |
| Ink | `--ds-ink`, `--ds-text`, `--ds-ink-2`, `--ds-ink-3`, `--ds-muted` | Titles and values; reading text; notes; labels; the quietest words |
| Accent | `--ds-accent`, `-hover`, `-on`, `-soft`, `-soft-line`, `-ink`, `-deep`, `-bright` | The one main action per view, what the person chose, where they are |
| Speech | `--ds-assistant-box`, `-edge`, `--ds-person-box`, `-edge`, `-ink`, `--ds-input-edge` | The assistant's lines, the person's lines, the message box |
| Rule cue | `--ds-rule`, `--ds-rule-ink` | A value the system checked and found against a rule |
| Status | `--ds-status-{grey,blue,amber,green}-{soft,line,ink}` | Where an item is in its journey |
| Empty cue | `--ds-cue-empty`, `--ds-cue-empty-ink` | An answer still missing |
| Level | `--ds-level-{low,medium,high,critical}`, `-soft`, `-ink` | A risk's level, and nothing else |
| Focus | `--ds-focus`, `--ds-focus-width`, `--ds-focus-offset` | One ring on `:focus-visible` |

### The accent

- One solid accent button per view: the step that moves the work on (Send, OK, Next). Everything else is an outline or a quiet button.
- The accent also marks what the person chose (a chosen option, row, filter or month), where they are (the current tab, the current step, the current question) and their own words in the chat.
- The same accent in every style. Hover goes one step darker so the white words on it get stronger.
- `--ds-accent-bright` is decorative only: the chat panel's top line, the rule beside a follow-up question, the listening wave. Never under text.

### Colour means level

- **Levels.** A level is a chip with its score, for example *7 High*: the level's soft fill, its dark words, and the full level colour as a thin edge. Four levels, the same four colours in all three styles. No other element uses these colours.
- **The level always comes from the scoring grid.** A person never types it and a model never picks it. Where a value was set by the grid, a small *Why* opens the rule in words: likelihood times impact gives the score, and the score's band gives the level.
- **Statuses** are light outlined pills with a small icon, in shades that can never be read as a level:

| Status | Colour | Icon | Meaning |
|---|---|---|---|
| Draft | grey | none | Being written |
| Sent | blue | clock | With the other side |
| Returned | amber | return arrow | The only one that asks the reader to act |
| Accepted | green | check | Closed |

- **Tags** that say what kind of item something is (a risk or a challenge; a goal, an initiative or a project) are a word in a thin dashed outline, no fill.
- **Never colour alone.** A word or an icon always carries the meaning; colour only repeats it.

### Cues on an answer

Cues are borders and marks, never fills.

| Cue | Border | Mark |
|---|---|---|
| The current question | 2px solid accent | none; the others are dimmed |
| Still to come | none, on the inset tone | the label in muted ink |
| Missing | 2px dashed empty cue | an icon and the word *Missing* |
| Against a rule | 2px solid rule cue | an icon and one line naming the rule |
| To look at again | 2px dotted rule cue | an icon and one line |

### Contrast

Every text and control pair, measured from the token values in each style. WCAG 2.2 AA asks for 4.5:1 for text and 3:1 for control edges and focus. Every pair below passes. The lowest text pair is 4.50 (the main button, all styles); the lowest non-text pair is 3.33 (a control edge on the paper ground, styles 2 and 3).

Text (needs 4.5:1)

| Use | Pair | Style 1 | Style 2 | Style 3 |
|---|---|---|---|---|
| Reading text | `text` on `panel` | 15.37 | 16.11 | 15.37 |
| Reading text on the ground | `text` on `ground` | 15.37 | 12.94 | 12.35 |
| Reading text in a table head | `text` on `inset` | 14.34 | 14.53 | 13.62 |
| Reading text on a hovered row | `text` on `hover` | 14.34 | 14.29 | 13.62 |
| Notes | `ink-2` on `panel` | 10.36 | 6.86 | 5.95 |
| Labels | `ink-3` on `panel` | 8.21 | 6.86 | 5.95 |
| Labels on a quiet question | `ink-3` on `inset` | 7.66 | 6.19 | 5.27 |
| Quietest words | `muted` on `panel` | 5.95 | 7.29 | 5.95 |
| Quietest words on the ground | `muted` on `ground` | 5.95 | 5.86 | 4.78 |
| Quietest words on a quiet question | `muted` on `inset` | 5.55 | 6.58 | 5.27 |
| The assistant's lines | `text` on `assistant-box` | 15.37 (no box) | 13.87 | 13.12 |
| The person's lines | `person-ink` on `person-box` | 5.61 | 7.23 | 11.26 |
| Main button | `accent-on` on `accent` | 4.50 | 4.50 | 4.50 |
| Main button, hover | `accent-on` on `accent-hover` | 6.03 | 6.03 | 6.03 |
| Accent words | `accent-ink` on `panel` | 6.03 | 6.03 | 6.03 |
| Accent words on a chosen item | `accent-ink` on `accent-soft` | 5.61 | 5.61 | 5.61 |
| A chosen filter or tag | `accent-deep` on `accent-soft` | 7.77 | 7.77 | 7.77 |
| Reading text on a chosen row | `text` on `accent-soft` | 14.31 | 15.00 | 14.31 |
| Rule cue words | `rule-ink` on `panel` | 9.75 | 7.30 | 7.30 |
| Missing cue words | `cue-empty-ink` on `panel` | 7.58 | 6.86 | 5.95 |
| Draft pill | `status-grey-ink` on `status-grey-soft` | 9.90 | 6.19 | 5.27 |
| Sent pill | `status-blue-ink` on `status-blue-soft` | 9.42 | 9.22 | 8.44 |
| Returned pill | `status-amber-ink` on `status-amber-soft` | 6.87 | 4.59 | 4.59 |
| Accepted pill | `status-green-ink` on `status-green-soft` | 8.52 | 6.07 | 6.07 |
| Low chip | `level-low-ink` on `level-low-soft` | 6.05 | 6.05 | 6.05 |
| Medium chip | `level-medium-ink` on `level-medium-soft` | 6.17 | 6.17 | 6.17 |
| High chip | `level-high-ink` on `level-high-soft` | 5.07 | 5.07 | 5.07 |
| Critical chip | `level-critical-ink` on `level-critical-soft` | 6.61 | 6.61 | 6.61 |
| Top bar words | `ink` on `topbar` | 16.88 | 16.11 | 15.37 |

Controls and focus (needs 3:1)

| Use | Pair | Style 1 | Style 2 | Style 3 |
|---|---|---|---|---|
| Control edge | `line-strong` on `panel` | 4.08 | 4.14 | 4.15 |
| Control edge on the ground | `line-strong` on `ground` | 4.08 | 3.33 | 3.33 |
| Message box edge | `input-edge` on `panel` | 4.50 | 4.50 | 4.15 |
| Current question, chosen option | `accent` on `panel` | 4.50 | 4.50 | 4.50 |
| Accent on the ground | `accent` on `ground` | 4.50 | 3.62 | 3.62 |
| Focus ring | `focus` on `panel` | 16.88 | 5.77 | 5.00 |
| Focus ring on the ground | `focus` on `ground` | 16.88 | 4.63 | 4.02 |
| Focus ring in a table head | `focus` on `inset` | 15.75 | 5.20 | 4.44 |
| Rule cue border | `rule` on `panel` | 6.74 | 5.77 | 5.77 |
| Missing cue border | `cue-empty` on `panel` | 4.76 | 4.14 | 4.15 |

`--ds-line`, `--ds-edge` and `--ds-island-edge` are decorative lines and are not held to 3:1; a control never relies on them.

## Type

- Two families per direction: a sans heading family and a sans body family for left-to-right, an Arabic heading family and an Arabic body family for right-to-left. Named in `tokens.css`, never shipped.
- Five sizes: 14px (labels, notes, chips), 16px (reading text, the chat), 18px (the app name, a typed answer), 20px (a screen title, the current question), 32px (the welcome line only). **Nothing is smaller than 14px.**
- Table words are 15px in style 1 and 16px in styles 2 and 3; compact tables drop to 14px.
- Titles take the style's weight and tracking (`--ds-title-weight`, `--ds-title-track`); sizes stay the same across styles.
- Arabic lines open up by `--ds-leading-rtl-extra`. Numbers stay Western digits in both languages.

## Layout

### One frame on every screen

The screen is a fixed set of regions. Switching a tab or a role changes only what is inside them; nothing floats to a new place.

```text
+--------------------------------------------------------------+
| Top bar: mark | unit over app name       person, language, sign out
+----------------+---------------------------------------------+
| Chat panel     | Tab bar                                     |
| 400px          | Title row ............ filters at its end   |
|                | Content box (the only part that scrolls)    |
|                |                                             |
|                | Action row ............. main action last   |
+----------------+---------------------------------------------+
```

- **Islands.** In style 1 the chat panel and the work area fill the space under the top bar and touch, split by one hairline. In styles 2 and 3 the same two regions become islands: each a white panel with its own edge and corners, `--ds-island-gap` apart and the same distance from the screen's edges, with the paper ground showing between them. The tab bar, title row, content box and action row sit inside the work island exactly as they sit in the work area in style 1.
- **Top bar**: white, one fixed height. The mark sits in a fixed-width tile so the titles start at the same place in both languages; a short centred stroke separates them, not a full-height line. The mark keeps its own orientation and is never mirrored.
- **Tab bar, title row, action row**: fixed heights (`--ds-frame-tabs`, `--ds-frame-title`, `--ds-frame-actions`). The action row is there on every tab, empty when a tab has no action, so the content box never changes height.
- **Content box**: the only region that scrolls. A little scrolling is fine; it stays inside this box.
- **Tabs** switch content in a natural order (the order the work happens), never a random one.

### The chat panel's side

The chat panel sits at the **reading start**: on the left in a left-to-right language, on the right in a right-to-left language. Everything else mirrors to match: the top bar (the person's name, the language switch and sign out go to the reading end), the tabs, the step bars, the tables and directional icons. One language switch flips the whole page in place, with no reload and the conversation kept.

Use logical properties only (`inline-start`, `inline-end`), so one set of rules serves both directions.

### A bigger screen shows more, never more scrolling

On a laptop, the content box shows the current question and its choices; on a large screen it can show the question and the open answers side by side. Never three columns on a laptop: when something opens beside the work, the chat panel folds to its rail.

### Size to content

A card is no bigger than its content needs; cards that stack stay small. Nothing is cramped, cut off or truncated: content that is tight gets more room, or is split behind tags that switch what the box shows. Where a picture sits beside text boxes, the picture gets the largest box.

## Components

### The register table

- A table of the reader's own items, readable by default: 48px rows, 15 or 16px words, the column names staying at the top while rows scroll under them, faint lines between rows.
- A **density switch** the person controls: compact makes rows 36px and words 14px. It never goes below 14px.
- **Views as tags.** A wide register is split into a small number of views (for example Summary, Rating, Controls, Treatment) switched by tags above the table, in the order the work happens. **Every view keeps the item's number and name as its first columns**, so a reader always knows which row is which item.
- **Short headers on screen.** Long official field names are rewritten as short, meaningful headers everywhere on screen. The export keeps the full original headers.
- **Unset values are words.** An empty cell reads *Not set*, never a blank.
- Each row carries its level chip and its status pill. One main action for the whole table (for example *Send register*) sits in the action row. A disabled action says what unlocks it: *Fill the level first*.
- Items carried from an earlier cycle get one line above the table while any remain unchanged, not a tag on every row.
- Filters for a long list: a search field, then at most two dropdowns with counts. The chosen values show as small removable tags under the row.
- Text in a cell sits in the middle vertically; column widths hold steady when views switch.

### Forms

**Entry is an interview, not a wall of fields.** The assistant asks; the work area shows the answers taking shape.

- Questions come in **small meaningful groups**, shown as steps. The current group is lit; the others are dimmed.
- **One question at a time is current**: a card with a 2px accent edge, the question as its label at 20px, and the answer inside the card with its own OK. Answered questions sit as quiet rows (label, value) in the panel tone; questions still to come sit in the inset tone.
- **Answer choices** are buttons at least 44px tall with a small number key, never a bare list. Where a picture helps (a level, a likelihood, a trend), the choice shows it. At most five choices on a screen.
- Cues for missing, wrong or doubtful answers follow the cue table above: borders and marks, never fills.
- The assistant fills what is already known and asks only the judgement calls. Items from the last cycle come first: still valid, change, or close.

**Setup is a wizard.** Steps in order with a fixed step bar at the top of the content box, each step's state as a pill on the bar, a review step at the end, and Back and Next in the action row. A step with nothing changed since the last cycle reads *No change*. Fixed options (a period, a grid, a list of units) are picked visually, not typed:

- A period is a strip of months; one click on the last month sets the deadline.
- A scoring grid is a grid of level chips; changing a cell or a band limit shows how many entered items would move before Save.
- Lists are rows in a table with an add row at the foot.
- A hierarchy (goal, then initiative or project) is a short tree.
- Who can do what is a grid of roles by actions, with room to add a role.

**General rules.** Mark optional fields, never required ones. An error says what to do next. Every write has a visible verb and leaves a receipt line. No click writes without saying so.

### The chat panel

- Opens at 400px. The person can drag it between 360px and 520px, or step it 16px at a time with the arrow keys on its resize bar, and fold it to a 56px rail. The width and the fold are the person's own and are kept.
- The join with the work area is deliberate: one hairline in style 1; in styles 2 and 3 the panel is its own island with the ground showing in the gap. A 2px accent line runs along the panel's top, and a resize bar in the join thickens to the accent under the pointer.
- **Compact and brief.** The panel shows the latest exchange and one line per helper; earlier messages sit behind one button. One short line per message, the most important thing first. Reasons sit behind *Why*.
- **The assistant never says "I".** The action is the subject: *Checking the level*, *Asking the unit*. Its own lines are plain words in style 1 and sit in a grey box in styles 2 and 3. A follow-up question takes a 2px rule on its reading-start side.
- **The person's lines** sit at the reading end in the person's box.
- **The message box** starts at one line and grows as the person types, up to six lines, then scrolls inside. Text is never cut off. Inside it, in one row under the words: the mode icon, the microphone, the live voice icon, then send at the reading end. No keyboard icon.
- **Modes** (how much the assistant may do alone) sit behind one small icon in the message box. Tapping it opens three rows, each an icon, a name and one short line. The highest levels always wait for a person, whatever the mode.
- **Voice**: a visible microphone for tap to speak, and a live voice icon beside it. A five-bar wave moves beside the microphone while it listens and stops the instant listening ends.
- One short line under the box says the assistant can be wrong and should be checked.
- The panel's foot keeps one height on every screen, so the message box never jumps.

### Sign in and greeting

- Sign in is one flat card on the page, no photograph behind it. The account decides the role; there is no role switch in the product.
- The greeting welcomes the person by name and asks how the assistant can help today, with a small chip for any live count (*Answer 2 requests*). Then the assistant moves to its panel and the work area opens.

## Content

- **Readable at 13.** Every screen can be followed and read by a 13-year-old: short sentences, common words, one idea per line.
- **Specialist terms stay.** Likelihood, impact, residual risk, treatment, control and the like keep their proper names and are explained where they appear (a short line, or behind *Why*), never swapped for simpler words.
- **About 40 words per step** in the work area. Nothing that is not meaningfully needed; obvious text is dropped.
- **One word per label.** No compound labels joined with slashes; pick the one word that fits. No words in quotation marks unless it is a real quote. No needless brackets.
- Natural wording in both languages, a full translation rather than a transliteration; fixed names and terms stay as they are.
- No em dashes, no internal codes or references in anything a reader sees.
- Sample data in designs is invented and generic: *Supplier delay*, *Unit A*, *Low 3*.

## Motion

- Motion only while a state is happening: the listening wave, a working indicator while the assistant works, a short done moment when a step finishes. Nothing moves on an idle screen. No entrance animation.
- Where motion is allowed it is calm, never fast; items that appear do so in the order of the journey.
- Reduced motion (the OS setting) stops the wave on a still frame and removes every transition.

## Progress, not points

Progress is shown as progress bars, finished ticks, a short done moment and a clear next step. No points, rankings or streaks, and never a comparison between people.

## Focus, targets, direction

- One focus ring, `--ds-focus-width` wide, on `:focus-visible`, in the style's focus colour. It passes 3:1 on every surface it sits on (see Contrast).
- Buttons are 40 or 48px tall; filters and the message box's tools 36px, with enough room around them to reach easily; answer choices 44px.
- Icons: one outline set in one weight, 20 or 24px, inheriting the text colour. Directional icons flip in right-to-left; functional ones do not.
