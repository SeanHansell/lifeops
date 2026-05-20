---
type: context
name: domains
context: personal
source: bootstrap-interview
as_of: 2026-05-19
confidence: confirmed
---

# Operating Contexts and Domains

## Primary operating contexts (seven)

Every state file, input, proposal, and briefing entry carries exactly one primary operating context. Related contexts may be added as secondary tags.

| Context | Type | Default surface |
|---|---|---|
| MTS Pro Services | work | surface |
| Darkstar Technology | business | defer |
| Family | personal | surface |
| Home | personal | surface-when-actionable |
| School | school | surface-with-source |
| Parenting | personal | surface-with-source |
| Personal Operations | personal | surface-when-actionable |

### Definitions

- **MTS Pro Services** — employer/work context.
- **Darkstar Technology** — early-stage business context; deferred unless activated.
- **Family** — shared family system, marriage/spouse logistics, extended family, family travel, celebrations, relatives, holidays, family finance review, family continuity, and family-facing obligations.
- **Home** — property, household infrastructure, repairs, maintenance, smart-home, network, physical home projects, and household operational systems.
- **School** — school-system, academic, teacher/admin, calendar, assignment, portal, registration, supply, and school-communication obligations.
- **Parenting** — child-facing care, development, routines, supervision, comfort, activities, child-specific logistics, and parenting decisions.
- **Personal Operations** — Sean-owned personal systems, technology infrastructure, personal administration, individual projects, personal accounts/domains, health coordination, and personal learning not better owned by MTS or Darkstar.

### Routing rule

For any item that crosses Family, Parenting, School, Home, or Personal Operations, choose the primary context by the **nature of the obligation and owner of the next action**, not merely by who is affected.

- Do not route to Personal Operations merely because Sean is the actor or the source is Sean-provided.
- Technical personal infrastructure (accounts, domains, identity, migrations, personal systems) belongs in **Personal Operations** even when it has Family / Home / Parenting impact. User-facing impact is captured by adding **related contexts**, not by changing the primary.
- Seane is a Family member first. Parenting is a responsibility mode applied as a related context.

### Public (relevance/source context — not primary)

`public` is a separate external/source/relevance context, used for news, weather, civic, travel-safety, school/public-calendar, and other external signals. `public` does not behave like a primary life context and does not surface by default unless tied to an active obligation, tracked topic, safety issue, travel, weather, school, household operations, or explicit request.

### Unknown

`unknown` is the triage context for items whose primary operating context cannot be determined. Items with `context: unknown` route to `state/inbox/`. Do not default to Personal Operations.

## Secondary cross-cutting domains

Attach as tags to a primary operating context. These are lenses, not homes.

| Domain | Default surface |
|---|---|
| Health | defer-unless-scheduled-or-relevant |
| Travel | surface when active |
| Finance | defer-unless-deadline-or-review |
| Learning | suppress-unless-scheduled-or-activated |

## Review cadences

- **MTS Pro Services:** daily on workdays.
- **Darkstar Technology:** quarterly to start (expected to change).
- **Personal Operations:** weekly — Saturday morning.
- **Family:** weekly — Sunday; family finance monthly on the last weekend.
- **Home:** weekly for active operations/maintenance; monthly for general backlog.
- **School:** weekly Sundays during school year (daily if active/time-sensitive); monthly on the 15th during June and July.
- **Parenting:** weekly year-round.
- **Health (secondary domain exception):** monthly weekend.
- **Travel / Learning / Finance:** no standalone global review; attach to primary context.

## Source systems (future canonical; not connected in Phase 1)

- **MTS:** Google Workspace (`sean@mtsproservices.com`), Jira, Atlassian Home (Goals/Projects), Ninety.io (Entrepreneurial Operating System [EOS]), Confluence, Google Drive, IT Glue (legacy), Slack, Zoom.
- **Morelen Workspace** (`sean@morelen.net`): canonical for Personal Operations technical infrastructure; user-facing impact across Family / Home / Parenting / Darkstar. Sean is super-admin.
- **Seane school:** `3712000032@k12.hi.us`. Access without administration. Future Model Context Protocol (MCP) connector possible.
- **Tasks:** Jira (work), Todoist (multi-context — items inside Todoist route to their owning life area, not to Personal Operations by default).
- **Health:** Kaiser Permanente, Apple Health.
- **Notes/Docs:** Apple Notes, Google Drive; Obsidian under consideration. Household is currently manual/analog.
- **School systems:** Google Classroom, Infinite Campus, Remind.
- **Scheduling automation:** Reclaim.ai (downstream of Jira/Todoist; not canonical for meaning).
- **Mac Admins Slack:** community reference; not canonical for obligations; weighting ≈ 60% MTS / 20% Darkstar / 20% Personal Operations.

## Open questions

- Tier C domain classification (5 domains).
- Tier D domain confirmation (10 domains; default Personal Operations + suppress).
- Deferred recurring date categories from Batch 8 Q3 (tax, vehicle registration/inspection, annual physical/dental, Darkstar business filings).
- Domain renewal failure detection: registrar email to `sean@morelen.net` — confirm as ingress source.
