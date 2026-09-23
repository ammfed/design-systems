# Project agent memory

This file is the project's committed home for project-intrinsic agent knowledge: build, test, release, architecture, and sharp-edge notes that should travel with the code.

- Add durable project-specific notes here as they are discovered through real work.
- Public copy rules: everything here stays unbranded. No names of organisations, people, characters or projects; no logos, brand colour names, vendor names, URLs, emails or paths. Fonts are named by family only, never shipped.
- `documents/preview.html` links `tokens.css`, `tokens-dark.css` and `motion.css` from beside it, so a token change reaches the preview with no second copy to update; it still fetches nothing from outside that folder. The role, type and contrast tables in `documents/guidelines.md` sit between `<!-- NAME:START -->` and `<!-- NAME:END -->` markers and mirror the token values; keep them in step.
- In the token files, a `:root, [data-x="default"]` rule must come before the other `[data-x]` rules for the same property, or an attribute set on `<html>` loses to `:root` at equal specificity.
- The root `CHANGELOG.md` has one bullet per system under each version heading; edit only your own system's bullet.

## Maintaining this file

Keep this file for knowledge useful to almost every future agent session in this project.
Do not repeat what the codebase already shows; point to the authoritative file or command instead.
Prefer rewriting or pruning existing entries over appending new ones.
When updating this file, preserve this bar for all agents and keep entries concise.
