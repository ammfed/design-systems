# Risk Register UI: guidelines

Version 1.1.0. The rules behind `tokens.css`. `preview.html` shows the three styles side by side.

## Styles

Three complete styles share one set of token names. The page picks one with `data-ds-style` on `<html>`; an admin chooses it once, in setup, and style 1 is the default.

| Style | Name | The look |
|---|---|---|
| 1 | Plain | Flat white page. The chat panel is a flat warm tint and touches the work area, split by one hairline. Thin grey lines, no shadow, small corners, a thin accent stripe over the top bar. Functional and familiar. |
| 2 | Porcelain | Islands: the chat panel and the work area float on a warm paper ground as two white panels, 16px apart, with 22px corners, a firm warm edge, a bright top rim and a soft warm lift. Cards inside take a soft depth, rounder corners and capsule pills. |
| 3 | Paper | Islands, flat: the same two white panels on the paper ground, 16px apart, with 12px corners, one warm edge and no shadow. 8px corners on controls and no capsules, bold titles. |

**A style is the whole look, never a tint.** Grounds, panels, lines, ink, the chat panel's ground, the person's speech box, cue and status colours, corners, depth and title type all change together, on every screen, in every state and in both languages.

**A style changes the look only.** Elements, concepts, behaviour and layout are identical in all three. The islands in styles 2 and 3 are a look too: the same two regions in the same places and order, only set apart on the ground with space, corners and an edge. No screen gains, loses or moves anything when the style changes. If a design needs a new element to look right in one style, it is wrong in all three.

**Shared by all three:** the one accent, a white top bar, the four level colours, the picked, greyed, danger and Undo colours, the type families and sizes, spacing, control sizes, the frame and the chat panel's measurements.

## Colour

### Roles

| Role | Tokens | Use |
|---|---|---|
| Ground | `--ds-ground` | The page behind the panels. White in style 1, warm paper in styles 2 and 3 |
| Panel | `--ds-panel`, `--ds-dock`, `--ds-inset`, `--ds-hover`, `--ds-quiet` | The work area, cards and tables; the chat panel (a warm tint in style 1, white in 2 and 3); a second tone inside a panel (table head, a row not yet reached); row hover; a quiet button |
| Line | `--ds-line`, `--ds-line-strong`, `--ds-edge`, `--ds-second-edge` | Hairlines between rows (decorative); control edges that must be seen (3:1); a card's edge; the second button's outline |
| Islands | `--ds-island-gap`, `--ds-island-radius`, `--ds-island-edge`, `--ds-island-shadow` | How the chat panel and the work area sit on the ground: touching in style 1, floating apart in styles 2 and 3 |
| Ink | `--ds-ink`, `--ds-text`, `--ds-ink-2`, `--ds-ink-3`, `--ds-muted` | Titles and values; reading text; notes; labels and field titles; the quietest words |
| Accent | `--ds-accent`, `-hover`, `-on`, `-soft`, `-soft-line`, `-ink`, `-deep`, `-bright` | The one main action per view, where the person is, their own words |
| Picked | `--ds-picked`, `--ds-picked-edge`, `--ds-picked-ink` | What the person picked: a choice, an option, a pressed toggle |
| Greyed | `--ds-off`, `--ds-off-ink` | A control that cannot be used yet, still readable |
| Danger | `--ds-danger`, `--ds-danger-soft` | Remove, and the error lines |
| Undo bar | `--ds-bar`, `-ink`, `-act`, `-hover` | The ink bar that follows a Remove |
| Speech | `--ds-person-box`, `-edge`, `-ink`, `--ds-input-edge` | The person's lines and the message box. The assistant's lines have no box |
| Rule cue | `--ds-rule`, `--ds-rule-ink` | A value the system checked and found against a rule |
| Status | `--ds-status-{grey,blue,amber,green}-{soft,line,ink}` | Where an item is in its journey |
| Empty cue | `--ds-cue-empty`, `--ds-cue-empty-ink` | An answer still missing |
| Level | `--ds-level-{low,medium,high,critical}`, `-soft`, `-ink` | A risk's level, and nothing else |
| Focus | `--ds-ring`, `--ds-focus`, `--ds-focus-width`, `--ds-focus-offset` | The keyboard ring on buttons (ink); the message box's edge while it holds the keyboard |
| Overlays | `--ds-veil`, `--ds-slide-shade` | Under the check before a send; beside the kept columns of a table that has slid |

`--ds-assistant-box` and `--ds-assistant-edge` are deprecated in 1.1.0 and resolve to transparent in every style.

### The accent

- One solid accent button per view: the step that moves the work on (Send, OK, Next). Everything else is a second, quiet or Remove button.
- The accent also marks where the person is (the current tab, the current step, the field row being asked) and their own words in the chat. What they picked takes the picked colours.
- The same accent in every style. Hover goes one step darker so the white words on it get stronger.
- `--ds-accent-bright` is decorative only: the rule beside a follow-up question, the listening wave, the resize bar under the pointer. Never under text, and no line along the top of the chat panel.

### Colour means level

- **Levels.** A level is a chip with its score, for example *7 High*: the score in a block of the level's full colour at the chip's start (ink on the three lighter levels, white on critical), then the level's name in its dark words on its soft fill, with a 1px edge in the full colour. Four levels, the same four colours in all three styles. No other element uses these colours.
- **The level always comes from the scoring grid.** A person never types it and a model never picks it. Where a value was set by the grid, a small *Why* opens the rule in words: likelihood times impact gives the score, and the score's band gives the level.
- **A control rating** uses the same chip shape with a symbol where a level has its number. **Likelihood and impact** show five small bars before the word, the first few filled in the row's level colour.
- **Statuses** are light outlined pills with a small icon, in shades that can never be read as a level:

| Status | Colour | Icon | Meaning |
|---|---|---|---|
| Draft | grey | none | Being written |
| Sent | blue | clock | With the other side |
| Returned | amber | return arrow | The only one that asks the reader to act |
| Accepted | green | check | Closed |

- **Tags** that say what kind of item something is (a risk or a challenge; a goal, an initiative or a project) are a word in a thin dashed outline, no fill. A goal's outline is solid.
- **A count** of what waits is an accent disc with a white number, beside a tab or a title.
- **Never colour alone.** A word or an icon always carries the meaning; colour only repeats it.

### Cues on an answer

Cues are borders and marks, never fills.

| Cue | Border | Mark |
|---|---|---|
| The row being asked | 2px solid accent | none; rows not yet reached are dimmed |
| Not yet reached | none, on the inset tone | the title in label ink |
| Missing | 2px dashed empty cue | an icon and the word *Missing* |
| Against a rule | 2px solid rule cue | an icon and one line naming the rule |
| To look at again | 2px dotted rule cue | an icon and one line |

A rule's cue stays blue: it is guidance, not an error. Errors are red words (see Error lines).

### Contrast

Every text and control pair, measured from the token values in each style. WCAG 2.2 AA asks for 4.5:1 for text and 3:1 for control edges and focus. Every pair below passes. The lowest text pair is 4.50 (the main button, all styles); the lowest non-text pair is 3.33 (a control edge on the paper ground, styles 2 and 3).

Text (needs 4.5:1)

| Use | Pair | Style 1 | Style 2 | Style 3 |
|---|---|---|---|---|
<!-- CONTRAST-TEXT:START -->
| Reading text, and Stop (reversed) | `text` on `panel` | 15.37 | 16.11 | 15.37 |
| Reading text on the ground | `text` on `ground` | 15.37 | 12.94 | 12.35 |
| Reading text on the chat panel | `text` on `dock` | 13.62 | 16.11 | 15.37 |
| Reading text in a table head | `text` on `inset` | 12.91 | 13.53 | 12.91 |
| Reading text on a hovered row | `text` on `hover` | 14.22 | 14.29 | 13.62 |
| Notes | `ink-2` on `panel` | 10.36 | 11.17 | 10.36 |
| Notes on the chat panel | `ink-2` on `dock` | 9.19 | 11.17 | 10.36 |
| Labels and field titles | `ink-3` on `panel` | 8.21 | 7.65 | 8.21 |
| Field titles on a row not yet reached | `ink-3` on `inset` | 6.90 | 6.43 | 6.90 |
| Quietest words | `muted` on `panel` | 5.95 | 7.29 | 5.95 |
| Quietest words on the ground | `muted` on `ground` | 5.95 | 5.86 | 4.78 |
| Quietest words on the chat panel | `muted` on `dock` | 5.27 | 7.29 | 5.95 |
| Quietest words on a row not yet reached | `muted` on `inset` | 5.00 | 6.12 | 5.00 |
| The person's lines | `person-ink` on `person-box` | 5.61 | 7.23 | 11.26 |
| Main button | `accent-on` on `accent` | 4.50 | 4.50 | 4.50 |
| Main button, hover | `accent-on` on `accent-hover` | 6.03 | 6.03 | 6.03 |
| Accent words | `accent-ink` on `panel` | 6.03 | 6.03 | 6.03 |
| Accent icons on the chat panel | `accent-ink` on `dock` | 5.34 | 6.03 | 6.03 |
| Accent words on a chosen item | `accent-ink` on `accent-soft` | 5.61 | 5.61 | 5.61 |
| A chosen filter or tag | `accent-deep` on `accent-soft` | 7.77 | 7.77 | 7.77 |
| A picked choice and the bar for ticked rows | `picked-ink` on `picked` | 7.05 | 7.05 | 7.05 |
| A greyed button | `off-ink` on `off` | 6.38 | 6.38 | 6.38 |
| Error line and Remove | `danger` on `panel` | 6.57 | 6.57 | 6.57 |
| Remove, hover, and the offline line | `danger` on `danger-soft` | 5.75 | 5.75 | 5.75 |
| The bar after Remove | `bar-ink` on `bar` | 15.37 | 15.37 | 15.37 |
| Undo on the bar | `bar-act` on `bar` | 9.28 | 9.28 | 9.28 |
| Rule cue words | `rule-ink` on `panel` | 9.75 | 7.30 | 7.30 |
| Missing cue words | `cue-empty-ink` on `panel` | 7.58 | 6.86 | 5.95 |
| Draft pill | `status-grey-ink` on `status-grey-soft` | 9.90 | 6.91 | 5.27 |
| Sent pill | `status-blue-ink` on `status-blue-soft` | 9.42 | 9.22 | 8.44 |
| Returned pill | `status-amber-ink` on `status-amber-soft` | 6.87 | 4.59 | 4.59 |
| Accepted pill | `status-green-ink` on `status-green-soft` | 8.52 | 6.07 | 6.07 |
| Low chip | `level-low-ink` on `level-low-soft` | 6.05 | 6.05 | 6.05 |
| Medium chip | `level-medium-ink` on `level-medium-soft` | 6.17 | 6.17 | 6.17 |
| High chip | `level-high-ink` on `level-high-soft` | 5.07 | 5.07 | 5.07 |
| Critical chip | `level-critical-ink` on `level-critical-soft` | 6.61 | 6.61 | 6.61 |
| Low score block | `ink` on `level-low` | 5.15 | 4.91 | 4.69 |
| Medium score block | `ink` on `level-medium` | 12.23 | 11.68 | 11.14 |
| High score block | `ink` on `level-high` | 6.88 | 6.57 | 6.26 |
| Critical score block | `accent-on` on `level-critical` | 6.37 | 6.37 | 6.37 |
| Top bar words | `ink` on `topbar` | 16.88 | 16.11 | 15.37 |
<!-- CONTRAST-TEXT:END -->

Controls and focus (needs 3:1)

| Use | Pair | Style 1 | Style 2 | Style 3 |
|---|---|---|---|---|
<!-- CONTRAST-CONTROLS:START -->
| Control edge | `line-strong` on `panel` | 4.08 | 4.14 | 4.15 |
| Control edge on the ground | `line-strong` on `ground` | 4.08 | 3.33 | 3.33 |
| Control edge on the chat panel | `line-strong` on `dock` | 3.62 | 4.14 | 4.15 |
| Second button edge | `second-edge` on `panel` | 8.21 | 7.65 | 5.95 |
| Message box edge | `input-edge` on `panel` | 4.50 | 4.50 | 4.15 |
| Message box edge on the chat panel | `input-edge` on `dock` | 3.99 | 4.50 | 4.15 |
| Current question, chosen option | `accent` on `panel` | 4.50 | 4.50 | 4.50 |
| Accent on the ground | `accent` on `ground` | 4.50 | 3.62 | 3.62 |
| A picked edge on its fill | `picked-edge` on `picked` | 3.81 | 3.81 | 3.81 |
| Keyboard ring | `ring` on `panel` | 15.37 | 16.11 | 15.37 |
| Keyboard ring on the ground | `ring` on `ground` | 15.37 | 12.94 | 12.35 |
| Keyboard ring on the chat panel | `ring` on `dock` | 13.62 | 16.11 | 15.37 |
| Keyboard ring in a table head | `ring` on `inset` | 12.91 | 13.53 | 12.91 |
| Message box focus edge | `focus` on `panel` | 16.88 | 5.77 | 5.00 |
| Message box focus edge on the chat panel | `focus` on `dock` | 14.96 | 5.77 | 5.00 |
| Rule cue border | `rule` on `panel` | 6.74 | 5.77 | 5.77 |
| Missing cue border | `cue-empty` on `panel` | 4.76 | 4.14 | 4.15 |
<!-- CONTRAST-CONTROLS:END -->

`--ds-line`, `--ds-edge` and `--ds-island-edge` are decorative lines and are not held to 3:1; a control never relies on them. Where 1.1.0 takes a value from the product as built, a value with weaker contrast than 1.0.0 was not taken: the message box edge, the control edges, the quietest words and style 3's focus edge keep their 1.0.0 values.

## Type

- Two families per direction: a sans heading family and a sans body family for left-to-right, an Arabic heading family and an Arabic body family for right-to-left. Named in `tokens.css`, never shipped. Headings use weights 600 and 700, never heavier.
- Sizes: 14px (labels, notes, chips, pills, field titles), 16px (reading text, buttons, the message box, the chat, filters), 18px (the app name, a typed answer, a question in the chat), 20px (a screen title, the question in an asked row, the chat panel's name), 26px (the sign-in welcome), 32px (the greeting's welcome only). **Nothing is smaller than 14px.**
- **Text follows the window.** Body words are 16px up to a 1600px window, then grow with it (18px at 1920, 22px at 2560) up to 26px (`--ds-root-size` on `html`). Every size is in rem, so the top bar, the rows, the columns and the panels grow with the words, and the browser's zoom and the person's own text size still count. The sizes above are at 16px.
- Table words are 15px in style 1 and 16px in styles 2 and 3; compact tables drop to 14px. All three grow with the text.
- Titles take the style's weight and tracking (`--ds-title-weight`, `--ds-title-track`); sizes stay the same across styles.
- Words start at the reading edge and are never justified. Arabic lines open up by `--ds-leading-rtl-extra`, and a fixed-height row that holds Arabic sets its own line height. Numbers stay Western digits in both languages.

## Layout

### One frame on every screen

The screen is a fixed set of regions. Switching a tab, a role, a style or the language changes only what is inside them; nothing floats to a new place. The page itself never scrolls at desk width.

```text
+--------------------------------------------------------------+
| Top bar: mark | unit over app name       person, language, sign out
+----------------+---------------------------------------------+
| Chat pane      | Tab bar                                     |
| one third      | Title row ............ switches at its end  |
|                | Content box (the only part that scrolls)    |
|                |                                             |
|                | Action row ............. main action last   |
+----------------+---------------------------------------------+
```

- **Islands.** In style 1 the chat panel and the work area fill the space under the top bar and touch, split by one hairline. In styles 2 and 3 the same two regions become islands: each a white panel with its own edge and corners, `--ds-island-gap` apart and the same distance from the screen's edges, with the paper ground showing between them. The resize bar fills the gap and shows a 3px accent line under the pointer or the keyboard.
- **Top bar**: white, 80px on every screen. The mark sits in a fixed-width tile at the reading start so the titles start at the same place in both languages; a short centred stroke separates them, not a full-height line. The mark keeps its own orientation and is never mirrored.
- **Tab bar, title row, action row**: fixed heights (`--ds-frame-tabs`, `--ds-frame-title`, `--ds-frame-actions`). The title row holds the screen's one main heading. The action row is there on every tab, empty when a tab has no action, so the content box never changes height.
- **Content box**: the only region that scrolls. A little scrolling is fine; it stays inside this box.
- **One steady frame**: the tab bar, the title row, the content and the action row always run the full width of the work area, whatever is in them, so a tag or a tab never moves the row's last control, the table's end or the last button. A pressed tag keeps the weight of the others; its fill and edge mark it.
- **Fill the frame, then split.** Every block (a table, a list, a form's rows, a tree, a strip) fills the frame from the reading edge to its far edge. A line of words keeps the reading width, 720px (`--ds-work-min`). On a wide work area (`--ds-wide-from`, 72rem) a block that would run wider than a line of words splits: a list keeps the reading width with its opened item beside it, the first item open; a form's rows stand in two columns, read down the first and then the second, and a row is never cut between them.
- **A blank tab** sits its one line and its two ways forward in the middle of the work area.
- **One gap**: 16px between blocks in the content box, between the islands and inside a list row (`--ds-gap`), at every width.
- **Tabs** switch content in a natural order (the order the work happens), never a random one.

### The chat panel's side

From a 1600px window (`--ds-dock-from`) the chat is a docked pane; under it, an island at the bottom edge (see The island). The pane sits at the **reading start**: on the left in a left-to-right language, on the right in a right-to-left language. Everything else mirrors to match: the top bar (the person's name, the language switch and sign out go to the reading end), the tabs, the steps rail, the pinned table columns, the slider and directional icons. One language switch flips the whole page in place, with no reload and the conversation kept.

Use logical properties only (`inline-start`, `inline-end`), so one set of rules serves both directions.

### Widths and zoom

- **A desk tool from 1366px.** Built and checked at 1366, 1440 and 1920px. Under 1600px the work takes the whole width and the chat is an island; from 1600px it is a docked pane of one third, with the work in the other two thirds. Above that the text grows, so a big screen is filled, never left empty in a corner.
- **Never three columns on a laptop**: on a laptop the chat is the island, so the work and what opens beside it have the width.
- **200% zoom.** The work area keeps the page with the island over its bottom edge; the page scrolls down and never sideways; the top bar drops the person's name so Sign out keeps its place. There is no phone layout.

### Size to content

A card is no bigger than its content needs; cards that stack stay small. Nothing is cramped, cut off or truncated: content that is tight gets more room, or is split behind tags that switch what the box shows. Where a picture sits beside text boxes, the picture gets the largest box.

## Components

### Buttons

| Kind | Look | Use |
|---|---|---|
| Main | Solid accent, white words; darker under the pointer | One to a screen: the step that moves the work on |
| Second | 1px `--ds-second-edge` outline, ink words, `--ds-second-hover` under the pointer | The other choices |
| Quiet | Ink words, no edge, `--ds-second-hover` under the pointer | Low-stakes actions |
| Remove | `--ds-danger` words with a bin icon, `--ds-danger-soft` under the pointer | Removing an item |

- 48px tall, or 40px inside the work area and the chat panel. Words never wrap. Labels are verbs of under four words, in sentence case.
- Words first, then an 18px bold icon; a back arrow stays in front.
- **Greyed**: `--ds-off` with `--ds-off-ink`, still readable (6.38:1), never faded. It says why only when asked: the reason shows when the pointer rests on it.
- **Picked** is a state, not a kind: `--ds-picked` fill, `--ds-picked-edge` edge, `--ds-picked-ink` words, and `aria-pressed`.
- **Action row order**: a side tool (Export) alone at the start, then the way back, the other buttons, and the main one last.

### Tabs, the title row and switches

- **Tabs**: an icon in front of the word; the open tab in accent words with an accent underline; a count disc for what waits.
- **Title row**: the screen's name as its one level-one heading, then its switches at the end.
- **Tags that switch content**: 36px pills, each with its icon; the picked one in the picked colours. A **Compact** switch beside them is the person's own choice between 48px and 36px rows.

### The register table

- A table of the reader's own items, readable by default: 48px rows, 15 or 16px words, faint lines between rows, the row under the pointer on `--ds-hover`.
- **The bar over the table**: at the start the progress in words with its short bar (*2 of 4 sent*); at the end, on the same row, a search box and two dropdowns (level and status), each 36px. When the row is too narrow the filters drop to the start of the next line. Search looks through every word of a row. Chosen values show as small removable tags.
- **Sorting**: every column name but the number carries a small arrow button. One press sorts ascending, a second descending, a third returns to the sheet's own order. Levels and scales sort by their number, statuses by their order (Draft, Sent, Returned, Accepted), words by the page's language. The sorted column's arrow is in accent words and says which way; the head cell carries `aria-sort`.
- **The head row stays put**: column names stay at the top of the table's own box while rows scroll under them.
- **Columns**: each column keeps one width on every view and role; the table is as wide as its columns. The number and the item's name stay pinned at the reading start while the rest slides sideways inside the box, with a line and a soft shade (`--ds-slide-shade`) at their edge once slid, and one plain line under the table says how many columns sit beyond the edge.
- **Views as tags.** A wide register is split into a small number of views (for example Summary, Rating, Controls, Treatment), in the order the work happens. Every view keeps the item's number and name as its first columns.
- **Short headers on screen.** Long official field names are rewritten as short, meaningful headers everywhere on screen. The export keeps the full original headers.
- **Cells**: sentences and names from the reading edge; short values (numbers, levels, statuses, counts) in the middle under a heading in the middle; every cell centred up and down. An empty cell reads *Not set*, never a blank.
- Items carried from an earlier cycle get one line above the table while any remain unchanged, speaking of the whole register, not a tag on every row.
- One main action for the whole table (for example *Send register*) sits in the action row. A disabled action says what unlocks it.

### Entry: an interview

**Entry is an interview, not a wall of fields.** The assistant asks; the work area shows the answers taking shape.

- **The steps rail**: a 240px rail at the reading start of the content box holds the job's steps, each a 32px numbered badge, the step's icon and its name. It keeps its place while the content scrolls. The current step sits on the soft accent with even space around its badge and words; current and finished badges are solid accent; a finished step shows a tick alone.
- **Field rows that fold.** Every field is one row: its title at the reading start (a 176px column, 14px, label ink), its value after it, 48px tall. **Every row keeps its title.** Only the row being asked unfolds, downward, into the question (20px) and its control; once answered it folds back to its title and value while the next row unfolds. The fold takes 480ms and settles still; under reduced motion it opens and closes at once. The first row asked is drawn open from its first frame, so arriving shows no entrance motion. An unfolded row is brought into view and its answer box takes the keyboard.
- The asked row has a 2px accent border. Rows not yet reached sit on the inset tone with no border. An answered row can be opened again.
- **The confirm block**: what the assistant filled, held for the person's Confirm, stands in one column under the asked row's title, each value beside its title, then Change and Confirm.
- **A typed answer** is an underlined box (a 2px accent underline, 18px words) with its own OK. The chat panel's box takes the same answer.
- The count of a step's questions sits once, on the question itself (*2 of 8*).
- **Answer choices**: up to five fixed choices are picture tiles (140 by 104px), each a symbol, the word and a number key in the corner; more than five become a searchable list of 44px options, each with its symbol. A picked tile takes a 2px picked edge inside it on the picked fill. Likelihood and impact show a five-bar meter.
- **A specialist term** keeps its name with a dotted underline; a press or Enter opens two plain lines in a small box under it.
- The assistant fills what is already known and asks only the judgement calls. Items from the last cycle come first: still valid, change, or close.

### Setup: a wizard

Steps in order on the steps rail, each step's state as a small pill, a review step at the end, and Back and Next in the action row. A step with nothing changed since the last cycle reads *No change*. Fixed options are picked visually, not typed:

- A period is a strip of months; one click on the last month sets the deadline.
- A scoring grid is a grid of level chips; changing a cell or a band limit shows how many entered items would move before Save.
- Lists are rows in a table with an add row at the foot.
- A hierarchy (goal, then initiative or project) is a short tree.
- Who can do what is a grid of roles by actions, with room to add a role.

### Fields, search and dropdowns

- A form field is white with a 1px `--ds-line-strong` edge and the style's corner, no shadow; with the keyboard in it, a 2px accent line inside the edge.
- Search and dropdowns are 36px, with the style's pill corner, the same edge and the same accent focus.
- No note at the start of a form saying every field is needed; the assistant asks one thing at a time. Mark optional fields, never required ones.

### Error lines

An error that stops the work (a sign in that fails, details that will not save) is one line of red words: `--ds-danger`, 14px, weight 600, `role="alert"`, no box. It says what to do next; a screen that could not load comes with a way to try again.

### Lists, Remove and what follows an action

- **A list** is rows with 16px padding and 1px lines in one box; the opened row on the soft accent. A row's buttons sit in fixed slots, so Open stays in one place down the list.
- **Edit and Remove on every row**, each in a fixed slot; the add field is the last row.
- **Undo after Remove**: an ink bar at the start of the action row says what went, with Undo in the light accent, and a line under it runs out over ten seconds.
- **Several at once**: a tick box at the start of each row that can take one; a row with no box keeps its room, so every row's words start on one line. While any is ticked, one 48px bar in the picked colours sits over the list with the count and the actions for all of them.
- **A long read**: while the assistant reads what many units sent, one line says what is going on with Stop beside it, then each unit in a row with its state.
- **The check before a send**: a card over a soft veil showing what goes, to whom and what is missing, with the send as the one main button.
- **Progress**: one bar with the count in words; a tick on each finished setup step.
- Every write has a visible verb and leaves a receipt line. No click writes without saying so.

### Empty states

- An empty list: one large grey duotone symbol (48px), a title and one line.
- An empty register is a first step: why it is empty in one line, two ways forward (the first item as the main button, ask the assistant beside it) and the job's steps as small numbered marks.

### The chat panel

- **The docked pane**, from 1600px: opens at one third of the window. The person can drag it between 360px and two fifths of the window, step it 16px at a time with the arrow keys on its resize bar (Home and End jump to the ends), and fold it to a 56px rail. The width and the fold are the person's own and are kept. Anything that asks the person to act opens it by itself.
- The panel is `--ds-dock`: a flat warm tint in style 1, a white island in styles 2 and 3. No accent line along its top.
- **Header**, 80px to line up with the top bar: the assistant's face, its name at 20px and the control that folds the panel, with one thin line under it.
- **Sides follow the reading direction.** The person's messages sit at the reading start, the assistant's at the reading end, each at most 85% of the width.
- **The assistant's replies are plain words on the panel**: no box, no fill, no shadow, in every style. A long reply's lines start at its own reading edge. A follow-up question takes a 2px rule on its reading-start side.
- **The person's messages keep their bubble**: the person's box, edge and words.
- A question from the assistant is 18px, weight 500; a note or the busy line is 14px in note ink. The question is said once: the asked row shows it, and the panel does not repeat it.
- **Compact and brief.** The panel shows the latest exchange; earlier messages sit behind one *Earlier* button in its top row. One short line per message, the most important thing first. Reasons sit behind *Why*.
- **A helper's line**: while a helper works, one still pill under the assistant's words: its small face, its name in bold, what it is doing, three still dots.
- **What a helper prepared** (a drafted request, a filled item held for Confirm) sits under the messages, with its buttons kept in reach at the foot. Nothing is saved or sent until the person confirms.
- **Under one of the assistant's answers**: one or two next steps as chips (36px pills, picked colours under the pointer), then on one row *Try again* after a failure, *Why*, and two thumbs at the row's end. No chips while a card waits for the person.
- **What the assistant filled** sits on a card: one line says where the values came from and that nothing is saved yet; each value shows what it holds now over what is proposed, in quieter words for *Now*, with a cross that leaves that one value out. Confirm saves the rest; Reject leaves them all.
- **The assistant's mark**: a value the assistant suggested and the person kept carries a small mark of the assistant, in words where there is room. A value the person changes loses it.
- **What went wrong** is red words with what to do. While the server cannot be reached, one line in the top bar says so in danger words on the soft danger fill, with Try again.
- **The foot** keeps one height on every screen: the message box; a 48px row that holds Back and Skip during an interview and is empty otherwise; and one short line saying the assistant can be wrong and should be checked.

### The island

Under 1600px the chat is an island, a strip at the bottom edge in the middle of the screen. The work area leaves the strip's height free under it, so the strip covers nothing.

- **The strip**: a third of the window wide (never under 320px), 56px tall, top corners 14px. It holds the assistant's latest line on one line and its face at the reading end. A still accent glow behind the face shows while a helper works.
- **The card**: a press on the strip opens it into a card half the window wide (never under 480px), top corners 30px, as tall as what it holds and never past two thirds of the screen. Its top row holds the name, *Earlier* and the control that folds it; then the assistant's one line beside its face, what a helper prepared, and the message box. *Earlier* shows eight lines of the exchange, then scrolls.
- **It opens only when asked**, never by itself.
- It takes the panel's own look in each style (`--ds-dock`, `--ds-edge`, `--ds-shadow-float`), never a dark slab.
- **Motion**: opening takes 520ms with a slight overshoot (`--ds-ease-float-open`), folding 340ms with none. Its animation can be switched off; under reduced motion it opens and folds at once.

### The message box

Used by the chat panel and the greeting.

- A 2px `--ds-input-edge` border that turns `--ds-focus` while it holds the keyboard. The words sit over the controls.
- It starts at one line and grows with the words up to six lines, then scrolls inside. Text is never cut off. Enter sends; Shift and Enter make a new line.
- **Controls**, 36px with 24px icons in accent words, from the reading start: live voice, the microphone, the mode (chat panel only), then send at the reading end as a 40px solid accent button with a paper plane that mirrors. Send is greyed while the box is empty. No keyboard icon.
- **The microphone**: a press records, a second press stops (the icon becomes a stop square and the button takes the picked colours); what was heard lands in the box after what it already holds. A five-bar wave moves beside the controls while it records and stops the instant recording ends.
- **Modes** (how much the assistant may do alone): three rows that open upward over the box, each an icon, a name and one line, the current one picked. A mode above the admin's setting is greyed with its reason on pointing. The highest levels always wait for a person, whatever the mode.
- **Stop**: while the assistant works, send becomes Stop in send's place and size, in dark ink.
- **Attached files**: a paperclip adds text, CSV, Word or Excel files, three at most. Each shows as a 32px chip with its icon, name and a cross over the words in the box, and under the person's words once sent. A file is read like typed words.
- A control that is not ready yet stays greyed and says so in one line when pressed.
- One status line says what is happening (recording, hearing, why nothing was heard). In the chat panel it sits over the box, so the box and its microphone never move under the finger.

### Sign in and greeting

- Sign in is one flat card on the page, no photograph behind it. The account decides the role; there is no role switch in the product.
- The greeting is a full page: the assistant's face, a welcome by first name, one line asking how the assistant can help today, the jobs this person's role opens as second buttons, and the message box.
- **The slider**: those choices sit in one row as wide as the message box, centred while they fit. When they do not fit, the row slides sideways by two 24px arrow buttons, by Tab (each choice comes into view) or by a swipe; the edge with more behind it fades; an arrow shows only while there is more to see, and the one at an end reached is greyed. In a right-to-left language the row starts at the right and the arrows follow the reading direction.
- A choice or a typed line opens the work screen at the right tab: the assistant moves to the panel's side first, then the screen follows.

## States

| State | How it shows |
|---|---|
| Pointer over | Main button one step darker; second and quiet buttons `--ds-second-hover`; a table row `--ds-hover`; a tile's edge `--ds-line-strong` |
| Keyboard focus | A 2px `--ds-ring` outline 2px away on every button; a 2px accent line inside a field, search, dropdown or option; the message box's border turns `--ds-focus`; the resize bar shows its 3px accent line |
| Picked | Picked fill, edge and words; `aria-pressed="true"` |
| Current | A step row on the soft accent; the asked row with a 2px accent border; a list's opened row on the soft accent |
| Greyed | `--ds-off` with `--ds-off-ink`; the reason on pointing |
| Waiting | A field row not yet reached: the inset tone, no border |
| Busy | The assistant's working motion and one plain line under the messages |

## Content

- **Readable at 13.** Every screen can be followed and read by a 13-year-old: short sentences, common words, one idea per line.
- **Specialist terms stay.** Likelihood, impact, residual risk, treatment, control and the like keep their proper names and are explained where they appear (a short line, the dotted term, or behind *Why*), never swapped for simpler words.
- **About 40 words per step** in the work area, and at most five choices on a screen. Nothing that is not meaningfully needed; obvious text is dropped; nothing said twice on one screen.
- **One word per label.** No compound labels joined with slashes; pick the one word that fits. No words in quotation marks unless it is a real quote. No needless brackets.
- **The assistant never says "I".** The action is the subject: *Checking the level*, *Asking the unit*. Its tone in an interview is a supportive coach in a respectful, professional register, with at most two follow-ups.
- Natural wording in both languages, a full translation rather than a transliteration; fixed names and terms stay as they are. Every string exists in both languages; a missing side falls back to the other, never to a blank. Counts use each language's own plural forms.
- No em dashes, no internal codes or references in anything a reader sees. An acronym is spelled out the first time.
- Sample data in designs is invented and generic: *Supplier delay*, *Unit A*, *Low 3*.

## Mixed direction

- A person's message carries `dir="auto"`, so a typed command in a left-to-right script reads correctly inside a right-to-left panel.
- Email and password fields are `dir="ltr"`. A range of numbers inside a right-to-left chip is isolated left to right.
- A fixed line of the assistant's follows the page's language when it is switched; what a box already holds keeps the language it was typed in.

## Motion

- Motion only while a state is happening: the listening wave (900ms, only while recording), the assistant's working motion, a short done moment when a step finishes. Nothing moves on an idle screen. No entrance animation.
- Allowed transitions: the field row's fold (480ms, `--ds-ease-fold`), the island opening and folding, the Undo line running out over ten seconds, a smooth sideways scroll in the slider.
- Where motion is allowed it is calm, never fast; items that appear do so in the order of the journey.
- Reduced motion (the OS setting) opens and closes the fold and the island at once, stops the wave on a still frame, stills the Undo line, makes the slider jump and removes every transition.

## Progress, not points

Progress is shown as progress bars with the count in words, finished ticks, a short done moment and a clear next step. No points, rankings or streaks, and never a comparison between people.

## Focus, targets, direction

- One keyboard ring on every button (see States), passing 3:1 on every surface it sits on (see Contrast).
- Buttons are 40 or 48px tall; filters, search, dropdowns and the message box's tools 36px, with enough room around them to reach easily; answer choices 44px; icon-only buttons 36 to 40px.
- Icons: one outline set in one weight. 18px bold beside words, 24px on every icon-only button, 48px duotone over an empty list, inheriting the text colour. The small cross inside a chosen filter tag is 18px in a 28px button so the tag stays 32px tall. Directional icons (arrows, the double caret that folds the panel, the slider's carets, send, sign out) flip in right-to-left; the rest do not.
- **Landmarks and headings**: a header, the chat pane or island as an `aside` (the pane with its resize bar inside it), `main`, and one level-one heading per screen.
- **Names and roles**: tabs with `aria-selected`, icon-only buttons named, `aria-pressed` on picked choices, `aria-sort` on sorted columns, `aria-expanded` on the fold and the mode icon, `role="alert"` on error lines, `role="status"` on the message box's line. The chat panel's messages take focus when they overflow, so the keyboard can scroll them.
