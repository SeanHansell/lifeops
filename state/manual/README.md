# state/manual/

Temporary holding directory for manually-supplied calendar events, tasks, and date anchors that lack a connected external canonical source. This directory is **transitional**. Once connectors exist for Calendar, Todoist, Jira, school portals, and similar systems, those canonical sources are preferred and `state/manual/` shrinks to items that have no canonical home or that span multiple systems.

## What goes here

- Calendar-like events (appointments, meetings, school days) supplied by paste or sample
- Task-like items (renew car registration, order a gift) supplied by paste
- Date anchors (birthdays, deadlines, holidays) supplied by paste
- Cross-system commitments where the canonical source is unclear or multiple

## What does not go here

- Active or dormant multi-step initiatives — `state/projects/`
- Obligations between the Chief Executive Officer (CEO) and another party — `state/waiting/`
- Open decisions — `state/decisions/`
- Items whose context is unknown — `state/inbox/`
- Real personal, work, or school data before the compartmentalization re-evaluation lands (see [../../AGENTS.md](../../AGENTS.md) Future Action Items)

## Required frontmatter

- `context:` — `personal`, `work`, `school`, `household`, `public`, or `unknown`
- `item_type:` — `calendar_event`, `task`, `date_anchor`, or `note`
- `canonical_source:` — the external system that would own this item once connected: `calendar`, `todoist`, `jira`, `school_portal`, `school_remind`, `infinite_campus`, `manual`, or `unknown`. A list is permitted when the item legitimately lives in two systems.
- `canonical_status:` — `not_connected`, `connector_planned`, or `connected`
- `when:` — date or date-and-time, for `calendar_event` and `date_anchor` (International Organization for Standardization 8601 (ISO 8601))
- `due:` — date, for `task` (ISO 8601)
- `surface:` — `surface`, `defer`, or `suppress`
- `source:`, `as_of:`, `confidence:` — per [../../rules/source-confidence.md](../../rules/source-confidence.md)

## Filename convention

Slug-based: `dentist-appointment.md`, `renew-car-registration.md`, `daughter-birthday-2026.md`. Dates live in `when:` or `due:`, not in the filename. This keeps a file's identity stable when a date slips.

## Future migration policy — archive with traceability

When a connector becomes available for a given `canonical_source:`, the daily briefing workflow will:

1. Stop creating new `state/manual/` entries of that type.
2. Prefer the canonical source for surfacing the items it owns.
3. For each existing `state/manual/` entry superseded by canonical data, move the file to `state/archive/` with appended frontmatter recording:
   - `superseded_by:` — the canonical source that now owns this item
   - `superseded_at:` — the date supersession occurred (ISO 8601)
   - `supersession_reason:` — short note (e.g., "Calendar connector live; event present in canonical source")

Entries that are not superseded — because they have no canonical home, or because they legitimately span multiple systems and serve as the cross-system reference — remain in `state/manual/`.

Connector supersession mechanics are deferred to a later phase. This README defines the policy only.

## Phase 1.1 status

This directory was introduced in Phase 1.1 to give manually-supplied dated and task-like items real state memory between briefing runs while preserving the design choice that the repository does not duplicate external canonical systems.
