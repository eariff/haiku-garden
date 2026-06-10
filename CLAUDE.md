# Haiku Garden

Single-file drag-and-drop haiku composer with a book/parchment aesthetic.
Live at: https://eariff.github.io/haiku-garden

## Files

- `haiku-garden.html` — the app (always edit this file)
- `index.html` — exact copy of haiku-garden.html; served as the GitHub Pages root

## Development rules

- **Always edit `haiku-garden.html`**, not `index.html` directly.
- **After every prompt that changes a file**, commit and push to GitHub.
- **On `main`**: copy `haiku-garden.html` → `index.html` in the same commit.
- **On feature branches**: only edit `haiku-garden.html`; do not touch `index.html` until the branch is approved and merged to main.

## GitHub

- Repo: https://github.com/eariff/haiku-garden
- No active feature branches.
- To merge a feature branch, get user approval first, then merge into `main` and update `index.html`.

## Architecture

Single standalone HTML file — no build step, no dependencies. Everything (HTML, CSS, JS) lives in `haiku-garden.html`.

- **Word bank**: `WORDS` object keyed by syllable count (1–4)
- **Seasonal words**: `KIGO` object keyed by season (`spring`, `summer`, `autumn`, `winter`, `newyear`), sourced from the Yuki Teikei Haiku Society; toggled off by default
- **Game state**: `G` object tracks current line, placed words, syllable counts, pool, unlocked lines, and last removed word
- **Export**: Canvas API renders a 1080×1080 PNG with symmetric parchment layout
- **Themes**: Light (`#f0e8d5`), Dark (`#3a2618`), Auto (syncs to OS preference)

## Interaction model

- Words are dragged from the bank onto a line; drop position sets word order (insertion caret shown during drag)
- Clicking a word in the bank places it at the end of the current line
- Clicking a placed word removes it; if that word was on a completed line, that line becomes active again
- An **Undo** button appears after any word removal and disappears when the next word is placed
