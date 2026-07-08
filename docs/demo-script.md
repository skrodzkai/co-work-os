# The 15-minute demo

The internal show-and-tell that turns "interesting" into "can I have this?" Run it live —
slides kill it. Total: ~15 minutes plus questions.

## Prep (before anyone's in the room)

- [ ] A deliberately messy folder on your desktop (20 files, vague names, no structure)
- [ ] Your real (or realistic) Co-work OS workspace, synced and pinned, with one project
      containing a filled-in brief, a few inbox files, and dated outputs — **synthetic data
      only if anyone can see your screen**
- [ ] The same task brief saved in two places, ready to paste twice
- [ ] Cowork open, "Ask before acting" on — approving actions live *is part of the demo*

## Beat 1 — The problem (2 min)

Open the messy folder. Say the quiet part: *"This is how we all work today, and it's how
Claude works when we point it here — which is why its output is inconsistent. Every session
starts from zero."* Don't demo anything yet. Let the folder be the argument.

## Beat 2 — The OS (3 min)

Open the workspace root. Walk the tree top-down, one sentence per item: constitution →
reference → project template → a live project. Open `CLAUDE.md` and scroll it slowly —
*"this is the entire training manual, and the setup points Claude at it before every
session."* Then open the project's `DECISIONS.md`: *"and this is why February-you will know
what October-you decided, and so will Claude."*

## Beat 3 — Cold start vs. warm start (5 min) — the whole pitch

Run the **same brief twice**:

1. In the messy folder: output lands wherever, format is generic, and Claude asks things a
   colleague would know.
2. In the workspace: it reads the constitution and the project brief, uses your glossary
   terms, writes to `20_outputs/` with a dated name, and updates the status line.

Say nothing while it runs. The delta is the demo. If you only have time for one beat, it's
this one.

## Beat 4 — The teamwork part (3 min)

Show the SharePoint site and its membership group. *"Sharing the workspace = being in this
group. Confidentiality = which sites you're in. There is no step three."* If you can, show
the same folder synced on a second machine or account. Then show `_export_review/` and read
the checklist out loud — this is the moment HR and legal people lean in.

## Beat 5 — The guardrails (2 min)

Rapid fire: the tier badge at the top of `CLAUDE.md` · "Ask before acting" prompts you've
been approving all demo · never-delete/never-edit-inbox rules · figures-come-from-files
rule. Close with the ask:

> *"The repo is public. Copy the folder, paste two blocks, run the bootstrap prompt —
> you're where I am in 20 minutes. I'm holding office hours <WHEN>."*

## Questions you will get (rehearse these)

- **"Does Claude see everything in the folder?"** Yes — that's why tiers are separate sites,
  and why you connect the workspace, not your Documents folder.
- **"Where does the chat go?"** It stays on your machine — though if IT enables telemetry
  monitoring, session activity streams to the org, like email. Either way the files are the
  record: decisions land in `DECISIONS.md` and finished work in dated outputs, so the
  *results* are reviewable and diffable. (True activity auditing — every tool call and file
  touch — comes from that IT telemetry, not from the folder itself.)
- **"Can I break it?"** The constitution says never delete and never overwrite inbox files,
  and SharePoint keeps version history on every file — so a bad edit is recoverable. Treat
  it like any shared drive: mistakes are fixable from history, not risk-free.
- **"Why can't we just share a Cowork project?"** Cowork projects can't be shared — they
  live on your machine. The folder *is* the shared layer. (That's not a workaround; it's
  the design.)
