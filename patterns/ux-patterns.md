# General UX patterns for data-heavy dashboards

Patterns observed while studying comparable public case-management and project-tracking dashboards, written up as reusable patterns rather than a review of any specific product. No product names, URLs, or screenshots — these are the shapes worth reusing, and the ones worth avoiding, independent of where they were seen.

## Patterns worth reusing

**KPI card: headline number + status word + target line + trend.** A single large number, a small delta with a percentage, a plain-language status word next to a coloured dot ("On target" / "Off target" — never colour alone), and a small sparkline showing the recent trend. This is the strongest single pattern in this category: the headline number stays primary, the status is readable without colour, and the trend adds context without competing for attention.

**Breakdown list under a headline number.** A plain list of counts by category directly under a KPI headline (e.g. "8 of type A, 3 of type B…") reads faster than a pie or donut chart at the same information density, and it's naturally accessible.

**Stage funnel as bars on a shared baseline.** A horizontal bar per pipeline stage, all sharing one scale, with the count at the end of each bar. This answers "how many are still moving" at a glance and never distorts proportion the way a funnel-cone shape can.

**Deadline urgency as a ring + day-count chip.** A small ring icon (colour-coded but always paired with a "N days left" / "N days over" label) reused identically everywhere a due date appears — a table row, a card, a kanban tile. Reusing one idiom for urgency, instead of inventing a new visual per screen, is itself the valuable part of this pattern.

**Status pill with icon + word, not colour alone.** A pill combining a coloured dot, a short status word, and consistent placement. Passing a colour-blindness check is table stakes; the win here is using the exact same pill shape everywhere a status appears, so users learn it once.

**Stage tabs with counts, not a flat list.** When a queue has named stages (screening, review, escalation, etc.), tabs labelled with the stage name and a live count turn "what's waiting on whom" into a countable, scannable structure — much easier to scan than one long flat list with a status column.

**Provenance tags on AI-assisted content.** When an assistant surfaces a suggestion, flag the *specific* concern by name ("unsupported claim," "source may be stale") rather than only showing a bare confidence percentage. A named problem is actionable; a lone number is not.

**Numbered, checked-off journey stepper.** A horizontal or vertical stepper with numbered stages, a highlighted current step, and a checkmark on completed ones, used to orient a user inside a multi-phase process.

**Explanatory empty states over broken charts.** When a data source is genuinely empty, state the precondition in plain words ("this becomes available once X is complete") and offer exactly one next action, rather than showing a zero-value chart, a spinner that never resolves, or nothing at all.

**Plain line-item breakdowns for cost/budget summaries.** A short list of labelled amounts, right-aligned, with a total row, reads faster than a chart when there are only a handful of components — a chart doesn't earn its place at eight line items.

## Patterns to avoid

**Donut or pie charts for outcome summaries.** Position and length beat angle and area for comparison — a chart viewer can compare bar lengths accurately but not wedge angles. Use labelled horizontal bars instead, every time.

**Stacked bars when segment-level comparison matters.** A stacked bar hides the true zero baseline for every segment except the bottom one. It reads fine only when every value is small and the comparison being made is the *total*, not the segments — prefer small multiples (one small chart per category, same scale) whenever segment values need to be compared to each other.

**Bare, unscaled score badges.** A number with no stated scale and no context ("Risk 58") is not information — a viewer can't tell if it's good, bad, or where it falls against other cases. Any score shown must carry its scale explicitly (e.g. "8 of 10 — high").

**Two unrelated numbers placed next to each other with no stated relationship.** If a screen shows two different-looking metrics beside each other (a score and a percentage, say), state what relates them, or split them apart — otherwise it reads as inconsistency rather than as two deliberately distinct measures.

**Mixed-language number formatting.** If a sentence is in one language, its numbers and their unit words should be too — literally switching languages mid-word inside a translated sentence, or trailing an English unit noun onto an otherwise-translated sentence, is a common and avoidable failure. A full mirror (layout, panel position, and phrasing all switching together) reads far better than a partial one.

**Two-dimensional heatmaps at growing scale.** A small matrix (say, under ten rows by under ten columns) with each cell carrying its value as text, not colour alone, can work. The same idiom breaks down once the grid grows — plan to page or group before it does, rather than after.

## The throughline

The strongest dashboards in this category share one discipline more than any single chart choice: pick one visual idiom per concept (one deadline treatment, one status pill, one urgency ring) and reuse it identically everywhere that concept appears, rather than re-inventing the visual on every new screen. Consistency of idiom does more for comprehension than any individual chart type does.
