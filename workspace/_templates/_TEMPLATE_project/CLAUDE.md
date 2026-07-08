# Project: <PROJECT NAME>

| | |
|---|---|
| **Owner** | <NAME — one owner at a time; others read> |
| **Audience** | <who consumes the output, e.g. CHRO / CFO / comp committee> |
| **Due** | <YYYY-MM-DD> |
| **Tier** | <inherits the workspace tier — restate it here> |
| **Status** | <Claude keeps this line current at the end of every session> |

## Goal

<One paragraph: what "done" looks like and who consumes it. If you can't write this
paragraph yet, the project isn't ready to start.>

## Key files

<Point Claude at the sources of record so it never guesses. Examples:>
- `00_inbox/2026-08-01_hris-export.csv` — source of record for headcount/comp
- `10_working/model_v2.xlsx` — current working model
- `../../_reference/comp-philosophy.md` — framing for narratives

## Project-specific rules

<Constraints that override or extend the workspace constitution. Examples:>
- Budget assumptions frozen as of <DATE>; express all deltas vs. <BASELINE>.
- <Population X> is out of scope for this tier — do not model it here.

## How this folder works

`00_inbox/` = raw drops, never edited in place · `10_working/` = analysis in progress ·
`20_outputs/` = finished deliverables only, dated `YYYY-MM-DD_topic_vN` ·
`90_archive/` = superseded drafts (moved, never deleted).
Every session that changes direction appends one line to `DECISIONS.md`.
