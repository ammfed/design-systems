# Changelog — Risk Register UI

## 1.1.0 - 2026-10-05

What the product learned once built, through two UX and UI passes, folded back into the system. Every 1.0.0 token name still resolves.

- **The chat panel.** The assistant's replies are plain words with no box in every style, so `--ds-assistant-box` and `--ds-assistant-edge` are deprecated and resolve to transparent. The person's messages sit at the reading start and the assistant's at the reading end. The accent line along the panel's top is gone. In style 1 the panel is a flat warm tint (`--ds-dock`). A helper's line, what a helper prepared, and a foot that keeps one height are written down.
- **The message box.** Controls in a fixed order (live voice, microphone, mode, send), a status line above the box so it never moves, and a greyed control that says it is not ready when pressed.
- **Buttons.** Four kinds (main, second, quiet, Remove), a greyed state that stays readable and gives its reason on pointing, a picked state (`--ds-picked`, `-edge`, `-ink`), and a fixed action row order.
- **Entry.** A steps rail, field rows that keep their titles and fold open one at a time (480ms, instant under reduced motion), a confirm block, picture tiles for up to five fixed answers, and specialist terms explained in place.
- **The register table.** A progress and filter bar, three-way sorting with `aria-sort`, a head row that stays put, pinned columns with a shade once the rest slides, and a level chip whose score sits in a block of the level's full colour.
- **Lists and actions.** Edit and Remove in fixed slots, Undo after Remove on an ink bar that runs out over ten seconds, a check before a send over a veil, red error lines, and empty states that offer a first step.
- **Layout.** One 16px gap, a reading width of 720px for lines of words, and a desk tool from 1366px. The frame, text growth and the chat at each width are below.
- **Focus.** One ink ring on every button in every style (`--ds-ring`), in the light accent on the Undo bar (`--ds-bar-act`); `--ds-focus` is now the message box's focus edge.
- **Values.** Taken from the product as built: the table head and row tone, style 1's hover, styles 2 and 3's note and label inks, a few decorative lines and style 2's draft pill ink. Where a built value had weaker contrast than 1.0.0 (the message box edge, control edges, the quietest words, style 3's focus edge), the 1.0.0 value stays. The top bar is 80px. The contrast table is remeasured with the new pairs, and every pair passes in every style.
- **The frame and the window.** One steady frame: the tab bar, title row, content and action row always run the work area's full width, and a pressed tag keeps its weight, so nothing shifts. Blocks fill the frame and split on a wide work area (`--ds-wide-from`): a list beside its opened item, a form's rows in two columns. Text is 16px up to a 1600px window and grows with it above that (`--ds-root-size`); table sizes move to rem.
- **Docked pane and island.** From 1600px (`--ds-dock-from`) the chat is a docked pane of one third, dragged between 22.5rem and two fifths of the window, its header lined up with the top bar. Under that it is an island at the bottom edge: a strip with the latest line that opens into a card only when asked, with its own sizes, corners and motion (`--ds-float-*`). At 200% zoom the work keeps the page with the island over it.
- **What the assistant proposes.** A card of filled values shows Now over Proposed with a cross to leave one out; next-step chips, Try again, Why and thumbs under an answer; the assistant's mark on a kept value; Stop in send's place; attached files as chips; plain error lines and an offline line in the top bar; tick boxes with one bar for several at once; a long read that lists each unit with its state.
- **Mixed direction.** Typed text, email fields and number ranges are isolated so they read correctly in either direction.
- **Preview.** Plain replies on the reading end, the warm panel, score blocks on the level chips, a folded field row above the asked one, picked tags and choices, the Undo bar, and the island open over a list with ticked rows in all three styles.

## 1.0.0 — 2026-09-29

- Initial public release: a UI system for a risk register workspace.
- Three complete styles on one set of token names (Plain, the default; Porcelain; Paper), picked with `data-ds-style`. Porcelain and Paper set the chat panel and the work area as islands on a paper ground. A style changes the look only, never an element, a behaviour or the layout.
- Shared across all three: one accent, a white top bar, four level colours as soft fills with dark words, type, spacing, control sizes, the frame and the chat panel's measurements.
- Colour means level: level chips with the score, and status pills with an icon in shades that never read as a level.
- Rules for the register table, the entry interview, the setup wizard, the chat panel at the reading start in both directions, sign in and the greeting, content readable at 13 with specialist terms kept and explained, and motion only while something is happening.
- A measured WCAG 2.2 AA contrast table for every text and control pair in each style, and a `preview.html` that shows the three styles side by side.
