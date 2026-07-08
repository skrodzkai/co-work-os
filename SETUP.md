# Setup

Two paths. **Solo** gets you running in about 20 minutes on your own machine — do this first, even
if a team rollout is the goal, so you learn the system before you teach it. **Team** deploys
the workspace on SharePoint with tiered access.

---

## Solo setup (about 20 minutes)

1. **Get the files.** On this repo's GitHub page, click the green **Code** button →
   **Download ZIP**. Double-click the downloaded ZIP to extract it. Inside the extracted
   `co-work-os-main` folder, find the folder named **`workspace`** — that's the only part
   you need.
2. **Copy the `workspace` folder** somewhere ordinary and rename it, e.g. a folder called
   `Co-work OS` inside your Documents (Windows) or in your home folder (Mac).

   Two checks before moving on:
   - Open your copy and confirm **`CLAUDE.md` is the first thing you see at the top
     level**. If you instead see a folder named `workspace` inside it, that inner folder
     is the one everything below means.
   - On a company laptop, Documents often syncs to OneDrive (look for cloud icons on the
     files). If yours does, right-click your `Co-work OS` folder → **"Always keep on this
     device"** — the same silent-corruption bug the team setup guards against (step 4
     below) applies to any OneDrive-synced location.
3. **Connect the folder in Cowork.** In Claude Desktop, open Cowork and start a new
   session; when it asks which folder to work in, browse to and select your `Co-work OS`
   folder — not Documents, not Desktop, not your whole home folder. The folder you connect
   is exactly what Claude can read and write locally — that boundary is the core of the
   security model. (It is not the *whole* story: connectors, web search, and telemetry are
   separate surfaces your admin governs — see [GOVERNANCE.md](GOVERNANCE.md).)
   (Menus move as the app evolves — if you don't see a folder picker, check the current
   [getting-started guide](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork).)
4. **Paste the two instruction blocks** from [INSTRUCTIONS.md](INSTRUCTIONS.md), filling
   in the `<ROLE>`, `<COMPANY>`, and tier placeholders as noted under each block: Block 1
   into Settings → Cowork → Global instructions, Block 2 into the folder's Folder
   instructions (the box that appears when you select the connected folder).
5. **Run the bootstrap session.** In a session pointed at the folder, paste:

   ```
   This folder is a Co-work OS workspace you and I will share from now on. Read
   CLAUDE.md, then interview me — one question at a time — to fill in every
   placeholder in angle brackets in CLAUDE.md and _reference/glossary.md: the data
   tier (suggest TEAM CONFIDENTIAL if this is a solo workspace), my team, my
   company, the systems and acronyms I use, who owns _reference/. Then create my
   first real project in projects/ by copying _templates/_TEMPLATE_project/ and
   interviewing me for its brief. Confirm each file edit before you make it.
   ```

   Fifteen minutes of questions and the workspace knows your world. That's the install.

6. **First real task.** Drop something messy into the new project's `00_inbox/` — an export,
   meeting notes, a draft — and ask for a deliverable using the five-part brief at the bottom
   of INSTRUCTIONS.md. Check that the output lands in `20_outputs/`, dated. If it does,
   the system is working.

   One habit that matters on the solo path: there is no SharePoint version history behind
   you. The archive-don't-overwrite conventions are your only safety net — keep originals
   in `00_inbox/` and let every output be a new dated file.

   And one quick check any time Claude edits an existing file (on either path): open the
   result and confirm it's complete — no cut-off tables or missing tail. The OneDrive
   truncation bug (see the pinning note below and the FAQ) is rare once you've pinned, but a
   ten-second glance is the cheap insurance.

---

## Team setup on SharePoint/OneDrive

### The one design rule

**One confidentiality tier = one SharePoint site.** Never subfolders of one site with
"special permissions." Site membership decides who can sync the workspace onto their machine
at all — which is exactly the guarantee you need, because whatever is inside a connected
folder is readable by Claude in a session pointed there. A person who was never a member of
the restricted site can't sync those files at all. (One caveat to be honest about: someone
who *was* a member and later left may still hold already-synced local copies, backups, or
screenshots until offboarding removes them — so device encryption, MDM/remote-wipe, and a
real offboarding step are part of the story, not site membership alone. That's on the IT
checklist in [GOVERNANCE.md](GOVERNANCE.md).)

A typical Total Rewards deployment is two sites:

| Site | Tier | Members | Holds |
|---|---|---|---|
| e.g. "TR Workspace" | TEAM CONFIDENTIAL | the comp/analytics team (a security group, not individuals) | cycles, projects, working models |
| innocuously named | RESTRICTED | 2–3 people | executive/committee material |

Each site gets its own complete copy of `workspace/` — same skeleton, different tier badge.
Add a third COMMONS site later if you open templates up to the broader HR team.

### Steps (workspace owner, ~30 minutes per site)

1. **Ask IT to create the site** with group-based membership (see the pre-flight checklist
   in [GOVERNANCE.md](GOVERNANCE.md) — ideally that conversation has already happened).
   Keep site and library names short: the synced path prefix eats into Windows path limits.
2. **Copy the contents of `workspace/`** into the site's document library root, so
   `CLAUDE.md` sits at the top level. Edit `CLAUDE.md`: set the tier badge, workspace name,
   and the `_reference/` owner.
3. **Sync the library** with the OneDrive client (the **Sync** button in the SharePoint
   library — this is the reliable mode for Cowork; if your IT standardizes on "Add shortcut
   to OneDrive" instead, test step 4's pinning behaves the same way before rolling out).
   The synced folder appears in File Explorer's left sidebar under your company's name
   (Mac: in Finder's sidebar, similarly under the company name). That folder is what every
   step below means by "the synced workspace folder."
4. **⚠️ Pin the folder — this step is mandatory, not a preference.**
   Right-click the synced workspace folder → **"Always keep on this device"**
   (Windows Explorer and macOS Finder both show this in the right-click menu).

   Why: OneDrive's Files On-Demand keeps files in the cloud as placeholders until opened.
   There are confirmed, unresolved reports of Cowork reading placeholder files *truncated*
   and writing the truncated version back — silently, no error
   ([anthropics/claude-code#62140](https://github.com/anthropics/claude-code/issues/62140)).
   Pinning fully downloads the folder and removes that placeholder failure mode. It is not
   a complete guarantee — a related report
   ([#41702](https://github.com/anthropics/claude-code/issues/41702)) saw writes silently
   truncated on OneDrive paths even without placeholders — which is why the SharePoint
   library's **version history is the mandatory recovery layer** (confirm it's on), and why
   the constitution keeps originals in inboxes Claude never edits in place.
5. **Run your own bootstrap session** (solo steps 3–6) against the synced folder to
   personalize `CLAUDE.md` and the glossary *before* inviting the team.

### Steps (each team member, ~10 minutes)

1. Confirm you can open the SharePoint site. Sync the library (owner shows you where).
   The synced folder appears in File Explorer's sidebar under your company's name.
2. Right-click the synced folder → **"Always keep on this device."** Not optional.
3. In Cowork, connect the synced workspace folder — never a parent folder above it.
4. Paste Block 1 (global) and Block 2 (folder) from INSTRUCTIONS.md, filling in the
   placeholders noted under each block. (Folder instructions are per-person: everyone
   pastes Block 2 on their own machine.)
5. Read `CLAUDE.md` yourself once. It's short. It's also the entire training manual.

### Working agreements that make sharing work

- **One owner per project folder at a time** (named in the project's `CLAUDE.md`). OneDrive
  sync is not real-time co-authoring — simultaneous edits to one file produce conflict
  copies. The owner runs the Claude sessions; teammates read, or take ownership explicitly
  (a `DECISIONS.md` line).
- **Don't co-edit files in `20_outputs/`** while a session is running in that project.
- **Everything a teammate needs must be in the files.** Cowork's chat history and project
  memory live only on your machine and cannot be shared. `DECISIONS.md` and the Status
  lines are the team's memory — the session end routine in `CLAUDE.md` exists for exactly
  this reason.

### Scheduled tasks (once you're comfortable)

Cowork can run recurring tasks (weekly digest, report refresh) — they run only while your
computer is awake with the app open, and usage counts against your plan. One hard rule from
this workspace's governance, aligned with Anthropic's own guidance: **scheduled tasks never
touch employee-level data.** Schedule against aggregated outputs and reference material
only, with a human reviewing each run's output.
