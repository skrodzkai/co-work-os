# Co-work OS

**A workspace template for [Claude Cowork](https://claude.com/product/cowork)** — a folder
structure and a small set of instruction files that turn Cowork from a cold-start assistant
into a system that knows your team's rules, formats, and history the moment it opens a
folder. It is not software, and it is not affiliated with Anthropic or with the unrelated
"CoWork-OS" desktop application. There is nothing to install: you copy a folder, paste two
instruction blocks, and start working.

Built for teams that get **Claude chat + Cowork** at work (no Claude Code), that share files
on **SharePoint/OneDrive**, and that handle data where "who can see this?" is a real
question — it was designed for HR/Total Rewards use cases, the harder case that makes
every easier case work.

**Scope:** this is deliberately the *foundation layer* — folder structure, operating
instructions, and confidentiality tiers. It intentionally does **not** ship Skills or plugins
(Cowork's way of packaging repeatable procedures). Those are a valuable next layer you can add
on top once the folder discipline is working; keeping them out makes this usable by anyone on
day one, with nothing to install.

## Why this exists

Point Cowork at a messy folder and you get messy results — every session starts from zero,
outputs land wherever, and nothing your best analyst figured out last month is available to
anyone else. The fix is not a bigger prompt. It's a **file-system contract**:

- **A constitution** (`CLAUDE.md`) — the rules of the workspace, which the setup instructions
  have Claude read at the start of each session.
- **The same project anatomy everywhere** — `00_inbox → 10_working → 20_outputs → 90_archive`,
  so Claude never guesses where things go and a teammate never needs a tour.
- **Decisions in files, not in chat.** Cowork's chat history and memory live only on one
  person's machine. `DECISIONS.md` and dated outputs are the team's memory — inspectable,
  diffable, shared.
- **Confidentiality above the folder, not inside it.** Whatever is in a connected folder is
  readable by Claude in that session — so tiers are separate SharePoint sites with separate
  membership, and sync decides who can even have the files.

## What's in this repo

```
co-work-os/
├── README.md            ← you are here
├── SETUP.md             ← solo setup in ~20 minutes; team setup on SharePoint
├── INSTRUCTIONS.md      ← the two required instruction blocks (plus an optional third)
│                          and the task-brief format
├── GOVERNANCE.md        ← the tier model, HR-data rules, and the IT pre-flight checklist
├── docs/
│   ├── demo-script.md   ← a 15-minute show-and-tell for your team
│   └── faq.md
└── workspace/           ← THE PRODUCT — copy this folder and start working
    ├── CLAUDE.md            ← the workspace constitution (template)
    ├── _inbox/              ← unsorted, non-sensitive drops, triaged by Claude
    ├── _reference/          ← stable truth: glossary, philosophy, benchmark extracts
    ├── _templates/          ← _TEMPLATE_project/ — copy to start any project
    ├── projects/            ← active work, one identical skeleton per project
    ├── _export_review/      ← the only door out of the workspace
    └── _archive/            ← retired projects, moved whole
```

## Quick start

1. Copy `workspace/` somewhere ordinary (e.g. `Documents/Co-work OS/`) and connect that
   folder in Claude Desktop → Cowork.
2. Paste the two instruction blocks from [INSTRUCTIONS.md](INSTRUCTIONS.md).
3. Run the bootstrap prompt in [SETUP.md](SETUP.md) — Claude interviews you and fills in
   the placeholders. That's the install.

Rolling it out to a team on SharePoint? Read [SETUP.md](SETUP.md) — and don't skip the
**"Always keep on this device"** step; it works around a real, silent data-corruption bug
with OneDrive cloud-placeholder files.

## Design principles

1. **The folder is both the context unit and the exposure unit.** One workspace root = one
   audience = one data tier. Design as if every file in the tree will be read.
2. **Separation happens above the root.** Site membership, not subfolder permissions.
3. **File names carry context.** `YYYY-MM-DD_topic_vN`, short paths, and never a person's
   name or pay value in a filename.
4. **Claude maintains the memory files; humans audit them.** Status lines and decision logs
   beat any chat-history feature: they're files, so they sync, diff, and survive.
5. **Grow on repeat, prune on quarter.** Start minimal. Add a rule only when a failure
   repeats. Stale reference is worse than none.

## Status and provenance

This is a personal open-source project, not an artifact of any employer. All examples are
synthetic; anything in `<angle brackets>` is yours to fill. Product behavior referenced here
(instruction layers, sync caveats, governance surfaces) was verified in **July 2026**
against official documentation, vendor guidance, and — where noted — public bug reports and
independent testing. Cowork changes monthly, so re-check
[support.claude.com](https://support.claude.com) for anything load-bearing.

Co-work OS is part of the [SKRODZKai](https://skrodzkai.com) portfolio. Related writing:
[custom agent harnesses](https://skrodzkai.com/agent-harnesses) and
[practical, model-agnostic AI training](https://skrodzkai.com/ai-training).

## License

[MIT](LICENSE).
