# Visual and communication preferences

The standing principles all the design systems and the decision-card format in this repo are built to. These aren't tied to any one product — they're how to make something clear rather than merely decorated.

## Visual taste

- **Purposeful minimalism.** Modern, restrained, best-readability, direct and practical — never a templated or generic look. A visual earns its place only when it's the clearest way to show the point; if prose says it just as well, skip the visual.
- **One accent, reserved for a person.** A single accent colour, and it marks a person: the bar beside their quoted words, their name, a signature. It never colours titles, rules, table headers, bullets, chart series or any other structure. Everything else is neutral.
- **Real examples over drawn mock-ups.** Where possible, show a real screenshot or a worked example rather than an invented illustration.
- **No decorative filler.** No taglines, no stock-photo look, no gradient-and-glow treatments, no unnecessary emphasis. If it doesn't carry information, it doesn't belong on the page.
- **Nothing small unless it earns its place.** Before drawing a badge, tag, caption, sub-label, timestamp or hint line, ask whether the reader would miss it. If not, leave it out. A hint belongs in the tooltip or menu it explains, never as a standing line.
- **Calm motion.** Things move at a calm speed, never fast, and only while something is happening. When several things appear, they arrive one after another in reading order. Nothing moves on an idle screen.
- **A second look is a whole skin.** If a product offers more than one look, each one changes the ground, panels, lines, corners, shadows and type together, and never the layout. A tint alone is not a look.
- **Approved visuals carry over.** Once a visual is approved on a review page, the build lifts it and refines it. It never swaps in a different drawing or a weaker one, and one icon family is used throughout.

## Data and status communication

- **Lead with one headline number or answer**, sized to be read first; everything else supports it.
- **Rates as natural frequencies before percentages** ("3 of 5" before "60%") — natural frequencies are read correctly far more often than a bare percentage.
- **One decision per screen**, with a short, named list of options — never a bundle of unrelated choices on one surface.
- **Ranges or "not yet known" instead of a single point estimate** when the real answer is uncertain.
- **Progress as a verifiable count with a visible sense of how close to done** — a fill that closes toward the goal, not just a number.
- **Never colour alone.** A word always carries the same meaning a colour is trying to add. Status words are consistent across every screen they appear on ("On track", not "Good" in one place and "Fine" in another).
- **No comparisons across people.** Progress and state are self-referential, never a leaderboard.
- **Progress and small wins, nothing more.** A progress bar, a finished tick, a short done moment and a clear next step. No points, streaks or reward badges.
- **Charts default to bars or small multiples.** Never a radar chart, never a gauge — see the chart rules in `decision-cards/README.md` and the pattern notes in `patterns/ux-patterns.md` for why.

## Screens and flows

- **Readable at 13.** Someone around thirteen should be able to follow every screen. Specialist terms keep their real names and are explained where they appear.
- **The fewest steps.** Every step between the user and their goal has to earn its place. A choice that fits on the current page is made there.
- **The right control for the choice**, and at most five choices on a screen.
- **One fixed frame.** Switching tabs changes what is inside the boxes, never where the boxes are.
- **Space follows content.** A card is no bigger than what it holds; nothing is cramped or cut off; a bigger screen shows more, not more scrolling.

## Writing

- **Plain, direct, everyday words.** No corporate warmth, no buzzword-heavy abstraction, no compressed labels or invented jargon standing in for a full sentence.
- **Natural and friendly.** Write like a capable colleague talking: full sentences, warm but professional, never robotic.
- **One term per label.** Never two alternatives joined by a slash. No quotation marks or brackets unless they are really needed.
- **An assistant never says "I".** The action is the subject: "Checking the dates".
- **No internal codes** (reference numbers, decision ids, drafting notes) in anything a reader sees. A decision card's own short number is fine.
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
- The page header spans the full width, with a large title, so the page reads at a glance.
- A look or experience change is shown on a review page before it is built, not after.
- When several review pages are due, they are handed over together as one checked set, so no two pages ask the same question or contradict each other.

See `decision-cards/README.md` for the full pattern and its chart rules, and `patterns/ux-patterns.md` for patterns worth reusing and avoiding in data-heavy screens generally.
