# context/

Durable user context lives here. The bootstrap interview that populates these files was executed on 2026-05-19; the canonical files in this directory carry `source: bootstrap-interview` and were confirmed by the Chief Executive Officer (CEO) at intake.

Updates to these files are governed by [rules/approval-gates.md](../rules/approval-gates.md) — the entire `context/` directory is a protected files location and requires explicit CEO approval to modify or delete. To re-run the interview (e.g., for a new domain or after a major life change), invoke [workflows/bootstrap-interview.md](../workflows/bootstrap-interview.md) explicitly; do not auto-run it.

## Files

- `identity.md` — who the CEO is in this system; never-do list
- `domains.md` — which life domains are tracked and at what cadence
- `boundaries.md` — context, account, and approval boundaries
- `people.md` — people relevant to operations (dates, relationships, communication preferences)
- `dates.md` — recurring dates, holidays, school calendar anchors, prep windows

## Notes on context labeling

The `context:` frontmatter field on files in this directory describes the primary domain frame of the file. Cross-context content within a single file is permitted only when the file's purpose is inherently cross-context (e.g., `boundaries.md`), and individual entries should declare their own context inline.
