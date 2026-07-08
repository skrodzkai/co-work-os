# _reference — stable truth

Curated documents Claude should treat as authoritative context: glossary, comp philosophy,
plan mechanics, benchmark extracts, style guide. This folder is read-mostly — Claude cites
it, it doesn't edit it.

**Rules that keep this folder useful:**

- It has a **named owner** (set in the root `CLAUDE.md`). No owner, no folder.
- Every file gets reviewed quarterly. Stale reference is worse than no reference — every
  outdated file here is a wrong answer waiting to be retrieved.
- Benchmark/market data lives here as **files with a source and an as-of date** in the name
  (e.g. `2026-06_<vendor>-extract_<population>.xlsx`). Claude is instructed to use only
  these — never remembered market figures.
- Add a file only when its absence has caused a repeated failure. Don't pre-populate.

Start with `glossary.md` — filled in during your first bootstrap session (see SETUP.md).
