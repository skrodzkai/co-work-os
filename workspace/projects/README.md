# projects — active work

One folder per project, named `YYYY_topic` or `YYYY-Qn_topic` (short — deep paths break sync):

```
projects/
├── 2026-Q3_merit-cycle/
└── 2026_benchmarking-refresh/
```

**Starting a project:** copy `_templates/_TEMPLATE_project/` here, rename it, fill in its
`CLAUDE.md` brief. Every project has the identical skeleton — that consistency is what lets
Claude (and a teammate opening the folder for the first time) work without a tour.

**One owner at a time.** OneDrive sync is not real-time co-authoring: if two people (or a
person and Claude) edit the same file simultaneously you get conflict copies. The owner runs
Claude sessions in the folder; everyone else reads.

**Finishing a project:** move the whole folder to `_archive/`, intact.
