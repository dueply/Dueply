# AGENTS.md — THE SCALE

## Architecture
- `index.html` holds the whole game. The user explicitly asked for a single file, so keep it that way. Don't add a bundler, framework or extra JS/CSS files.
- `netlify.toml` publishes the repo root as a static site with no build command.
- There is no backend and no database. The only persistence is `localStorage`: `scale.best` stores the best streak and `scale.muted` stores the mute state.

## Layout of index.html
1. `<style>` is split into numbered sections: tokens, header, stage/cards, VS badge, magnitude rail, overlays, responsive. Colors and fonts are CSS variables in `:root`.
2. The markup is the header (streak, best, mute), then `#arena` with `#cardA`, `#vs` and `#cardB`, then the rail, then the `#intro` and `#over` overlays and the toast.
3. The `<script>` is one IIFE with numbered sections: DATA/CATS/RANKS, helpers, `sfx` (Web Audio), DOM refs, rail, game state and flow, game over/share, events, boot.

## Non-obvious decisions
- **Cards stay put and their content swaps.** `#cardA` and `#cardB` are never re-created. To slide, card B gets a transform toward card A's position (measured with `getBoundingClientRect`, so it works for both the side-by-side and stacked layouts). After that, `.no-anim` is applied to the arena, both cards are re-rendered and the transforms are reset in one frame.
- **Matchmaking:** `drawNext()` picks the next mystery item from items within N orders of magnitude of the current one. N shrinks as the streak grows. Items are spliced out of the shuffled deck, so none repeats within a run. If the deck runs out, the game ends with a "FLAWLESS" screen.
- **The roll animation uses log space** (`10^(log10(v) * eased t)`), so every digit place gets screen time. Ties count as correct, and no two values in DATA are equal.
- Numbers of 1e12 and above are shown in words ("43.3 quintillion"). `sizeClass()` picks the font size from the target value, so the font doesn't change size mid-roll.
- `font-variant-numeric: tabular-nums` on `.num` keeps the rolling digits from shifting sideways.

## Conventions
- Add new categories to `CATS` along with their pill color.
- Keep every value in DATA unique. The check is: `values.length === new Set(values).size`.
- Keep figures sourced and rounded, and put the year or a caveat in `n`.
