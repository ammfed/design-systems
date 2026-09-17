# Decision cards

A review-page format for putting a visual decision in front of someone: one open question at a time, from a small stack, with a live visual preview per option — not a wall of prose, not a form with fifty fields.

## The pattern

- **One decision card at a time**, drawn from a small stack, labelled "N of M" so progress is always visible.
- **The card and a canvas sit side by side**, never stacked — the card asks the question, the canvas on the other side draws the current decision visually (the card's own headline/bars by default, or a per-option preview when one is supplied).
- **Per-option visual previews**: when a decision has more than one plausible visual outcome, every option gets its own preview, and the viewer can flip between them before picking — never show only the recommended option's visual.
- **A short "why" drawer, closed by default.** One line of evidence sits above it; the full reasoning is one click away, never forced onto the card.
- **Select locally, queue, then send once.** Each answered card queues its answer; nothing is sent until every open card is answered and the viewer explicitly sends the batch back.
- **A one-screen recap before sending** — every queued answer, listed, before the final send.
- **What's already decided** lives in a collapsed sheet below the stack, for reference, not as something to re-decide.

## Content rules

Minimal text: no filler, no small helper text, no explanation of the obvious. Visuals carry the point; prose only states what a visual can't.

## Chart rules for any visual on a card

1. Bars or a dot plot on a shared scale — never a radar/spider chart. Radar's shape depends on axis order and its area grows nonlinearly with value, so it can visually misrepresent unchanged data even though bars and dot-plot positions are read accurately.
2. A rate or probability is stated as a natural frequency first ("3 of 10"), with a percentage as a secondary mention at most — natural frequencies measurably improve correct reasoning over a bare percentage.
3. A progress count ("N of M") is paired with a visible fill that closes toward the goal, never shown as bare text alone.
4. One headline number per card, sized to be read first; supporting detail (bars, evidence) comes after it.
5. No points, badges, streaks, or leaderboards comparing people — the evidence against contingent rewards and leaderboards in a workplace tool outweighs any evidence for them. If a card shows progress, make it self-referential, not comparative.
6. The weakest measure on a card is marked with a text or position cue, not colour alone.
7. If a range or projection is shown, the range is stated in words next to any shaded band, not left to shading alone.

## Files

`template.html` — a self-contained, framework-agnostic starting point implementing the pattern above: card stack, progress bar, side-by-side canvas, per-option preview tabs, evidence drawer, queue-then-send flow. Replace the example `CARDS` array with real content; the card shape (`headline`, `canvas`, `previews`, `visual`, `evidenceLine`, `why`, `rec`) is documented inline in the script.
