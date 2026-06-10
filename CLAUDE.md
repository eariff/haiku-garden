# Haiku Garden

Single-file drag-and-drop haiku composer with a book/parchment aesthetic.
Live at: https://eariff.github.io/haiku-garden

## Files

- `haiku-garden.html` — the app (always edit this file)
- `index.html` — exact copy of haiku-garden.html; served as the GitHub Pages root
- `CNAME` — custom domain config (haikugarden.app, not yet active)

## Development rules

- **Always edit `haiku-garden.html`**, not `index.html` directly.
- **After every prompt that changes a file**, commit and push to GitHub.
- **On `main`**: copy `haiku-garden.html` → `index.html` in the same commit.
- **On feature branches**: only edit `haiku-garden.html`; do not touch `index.html` until the branch is approved and merged to main.

## GitHub

- Repo: https://github.com/eariff/haiku-garden
- Active feature branch: `feature/seasonal-words`
- To merge a feature branch, get user approval first, then merge into `main` and update `index.html`.

## Architecture

Single standalone HTML file — no build step, no dependencies. Everything (HTML, CSS, JS) lives in `haiku-garden.html`.

- **Word bank**: `WORDS` object keyed by syllable count (1–4)
- **Seasonal words**: `KIGO` object keyed by season (`spring`, `summer`, `autumn`, `winter`, `newyear`), sourced from the Yuki Teikei Haiku Society
- **Game state**: `G` object tracks current line, placed words, syllable counts, and pool
- **Export**: Canvas API renders a 1080×1080 PNG with symmetric parchment layout
- **Themes**: Light (`#f0e8d5`), Dark (`#3a2618`), Auto (syncs to OS preference)
