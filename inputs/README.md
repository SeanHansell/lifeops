# inputs/

Phase 1 accepts manual or sample inputs only. No external connectors.

## How to add an input

Drop a Markdown file into this directory or under `inputs/samples/`. Include frontmatter:

- `context:` — one of `personal`, `work`, `school`, `household`, `public`, `unknown`
- `source:` — what produced this content (e.g., "manual paste", "copy of email", "sample data")
- `as_of:` — the date the content was current, in International Organization for Standardization 8601 (ISO 8601) format
- `confidence:` — `confirmed`, `inferred`, `assumed`, or `unknown`

## What inputs become

The daily briefing workflow consumes inputs and either:

- Updates an existing file under `state/`
- Creates a new state file in the appropriate `state/` subdirectory
- Materializes calendar events, tasks, and date anchors into `state/manual/` while no external canonical source (Calendar, Todoist, Jira, school portal) is connected — see [../state/manual/README.md](../state/manual/README.md)
- Routes to `state/inbox/` if context is unknown or the right destination is unclear

After processing, inputs are not deleted automatically. The Chief Executive Officer (CEO) decides when to remove them.
