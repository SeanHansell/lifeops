# context/

Durable user context lives here. The bootstrap interview that populates these files **has not yet been run**.

Until then, every file in this directory is a stub. Agents must treat the context as empty and say so in briefings rather than inventing facts.

A later session will run [workflows/bootstrap-interview.md](../workflows/bootstrap-interview.md) and write content into these files only after the Chief Executive Officer (CEO) confirms the intake summary.

## Files

- `identity.md` — who the CEO is in this system; never-do list
- `domains.md` — which life domains are tracked and at what cadence
- `boundaries.md` — context, account, and approval boundaries
- `people.md` — people relevant to operations (dates, relationships, communication preferences). Sensitivity to be re-evaluated before any real data is added.
- `dates.md` — recurring dates, holidays, school calendar anchors, prep windows

## Notes on context labeling

The `context:` frontmatter field on files in this directory describes the primary domain frame of the file. Cross-context content within a single file is permitted only when the file's purpose is inherently cross-context (e.g., `boundaries.md`), and individual entries should declare their own context inline.
