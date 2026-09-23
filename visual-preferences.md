# Visual and communication preferences

The standing principles all three design systems and the decision-card format in this repo are built to. These aren't tied to any one product — they're how to make something clear rather than merely decorated.

## Visual taste

- **Purposeful minimalism.** Modern, restrained, best-readability, direct and practical — never a templated or generic look. A visual earns its place only when it's the clearest way to show the point; if prose says it just as well, skip the visual.
- **One accent, reserved for a person.** A single accent colour, and it marks a person: the bar beside their quoted words, their name, a signature. It never colours titles, rules, table headers, bullets, chart series or any other structure. Everything else is neutral.
- **Real examples over drawn mock-ups.** Where possible, show a real screenshot or a worked example rather than an invented illustration.
- **No decorative filler.** No taglines, no stock-photo look, no gradient-and-glow treatments, no unnecessary emphasis. If it doesn't carry information, it doesn't belong on the page.

## Data and status communication

- **Lead with one headline number or answer**, sized to be read first; everything else supports it.
- **Rates as natural frequencies before percentages** ("3 of 5" before "60%") — natural frequencies are read correctly far more often than a bare percentage.
- **One decision per screen**, with a short, named list of options — never a bundle of unrelated choices on one surface.
- **Ranges or "not yet known" instead of a single point estimate** when the real answer is uncertain.
- **Progress as a verifiable count with a visible sense of how close to done** — a fill that closes toward the goal, not just a number.
- **Never colour alone.** A word always carries the same meaning a colour is trying to add. Status words are consistent across every screen they appear on ("On track", not "Good" in one place and "Fine" in another).
- **No comparisons across people.** Progress and state are self-referential, never a leaderboard.
- **Charts default to bars or small multiples.** Never a radar chart, never a gauge — see the chart rules in `decision-cards/README.md` and the pattern notes in `patterns/ux-patterns.md` for why.

## Writing

- **Plain, direct, everyday words.** No corporate warmth, no buzzword-heavy abstraction, no compressed labels or invented jargon standing in for a full sentence.
- **A claim carries its evidence.** State uncertainty plainly rather than faking certainty; never a bare assertion without its mechanism or its tradeoff.
- **No em dashes.** Periods, commas, or a plain conjunction instead.
- **Sentence case everywhere**, no unnecessary capitalisation, no all-caps in running text.
- **Brief by default.** Lead with the point, cut preamble and restatement, go deeper only when the reader asks for it. Tables and short lists over paragraphs of prose.

## Review pages (decision cards)

- One decision at a time, from a small stack, "N of M" always visible.
- The question and a live visual preview sit side by side, horizontally, never stacked.
- Every option gets its own visual preview, not just the recommended one.
- A short "why" stays collapsed until asked for.
- Minimal text throughout: no fluff, no small unneeded helper copy.

See `decision-cards/README.md` for the full pattern and its chart rules, and `patterns/ux-patterns.md` for patterns worth reusing and avoiding in data-heavy screens generally.
