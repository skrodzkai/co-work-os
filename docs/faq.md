# FAQ

**Does Claude see everything in the folder I connect?**
Assume yes. Whatever is inside a connected folder is in scope for a session pointed there —
there is no "Claude, ignore that subfolder" you can rely on. That's why confidentiality is
handled *above* the workspace (separate sites, separate membership), and why you connect the
workspace folder, never Documents or your home directory.

**Can Claude delete or overwrite my files?**
Permanent deletion always requires your explicit approval, in either permission mode. Writes
and overwrites are gated only in "Ask before acting" — in "Act without asking," Claude
writes freely, which is why the workspace narrows writes by convention: new files only in
`10_working/` and `20_outputs/`, never edit inbox files in place, move superseded work to
`90_archive/` instead of deleting. On a team deployment, SharePoint version history is the
recovery net under all of it. On the solo path there is no version history behind you — the
archive-don't-overwrite conventions are your only net, so keep originals in `00_inbox/` and
let outputs be new dated files.

**Where does my conversation history live? Can my admin see it?**
On your machine — and not by default. Cowork activity isn't captured in Claude's audit logs
or Compliance API (as of July 2026), and admins can't export your local history. But if IT
has set up OpenTelemetry monitoring — which this template's own governance checklist
recommends — your prompts, tool actions, and file paths stream to the organization's
monitoring endpoint from then on. Assume work sessions are visible to your employer, the
same assumption you'd make about email. Either way, the workspace treats **files** as the
record — decisions in `DECISIONS.md`, outputs dated in `20_outputs/` — not chat history.

**Can I share my Cowork project with a teammate?**
No — Cowork projects are local to your machine and can't be shared or synced. The *folder*
is the shared layer: your teammate syncs the same SharePoint library and wraps their own
project around it. Anything a teammate needs must be in the files, which is why the session
end routine exists.

**Why is "Always keep on this device" mandatory?**
OneDrive's Files On-Demand keeps files in the cloud as placeholders. There are confirmed
reports of Cowork reading placeholders truncated and silently writing the truncated version
back ([issue #62140](https://github.com/anthropics/claude-code/issues/62140)). Pinning the
folder fully downloads it and removes that failure mode. A related report
([#41702](https://github.com/anthropics/claude-code/issues/41702)) saw silent write
truncation on OneDrive paths even beyond placeholders — which is why the library's version
history is the mandatory recovery layer, not a nice-to-have, and why the constitution keeps
originals in inboxes Claude never edits in place. Pinning removes the biggest failure mode
and costs only disk space — pin it — but "pinned + version history + originals preserved" is
the full safety story, not pinning alone.

**Is our data used to train Claude?**
Not on Team or Enterprise plans by default. One caveat: the thumbs-up/down feedback buttons
are an opt-in path — skip them on sensitive threads.

**What about files with sensitivity labels?**
Labels that apply *encryption* make file **contents** unreadable to Claude — locally and via
the M365 connector — though the file's name and metadata can still surface in connector
search, so filename hygiene applies doubly to labeled material. Classification-only labels
don't block anything. Test one file per label before assuming either way; and treat an
encryption label as the right tool for content that must never be AI-readable.

**Two of us need to work in the same project. How?**
One owner at a time, named in the project's `CLAUDE.md`. OneDrive sync is not real-time
co-authoring — simultaneous edits create conflict copies. Handing off is one line in
`DECISIONS.md`. Everyone else can read the folder freely the whole time.

**What if Claude makes up a number?**
The constitution forbids stating figures that don't come from a workspace file, and
benchmark data only counts as a governed extract with a source and as-of date — in
`_reference/` or listed as a source in the project's `CLAUDE.md`. (Independent testing found AI benchmarking from memory off by up to 83% on
senior roles — this rule is not paranoia.) If a number can't be traced to a file, the
output says so instead of guessing.

**Do I need to be technical to use this?**
No. If you can copy a folder, paste two blocks of text, and right-click → "Always keep on
this device," you can run the whole system. The bootstrap session in SETUP.md does the rest
by interviewing you.

**Can I use this without SharePoint — just for myself?**
Yes — the solo path in SETUP.md is a plain local folder and takes about 20 minutes. The
tiers and sync rules only matter once you share.

**Claude ignored a rule in CLAUDE.md. Now what?**
First check the three layers are in place (global instructions, folder instructions, the
CLAUDE.md itself — see INSTRUCTIONS.md); the folder-instruction block exists precisely
because auto-reading CLAUDE.md is undocumented behavior. If the layers are fine and a rule
still gets missed repeatedly, sharpen the rule's wording in CLAUDE.md — one specific
sentence beats three vague ones — and mention it explicitly at the start of sessions where
it matters most.
