---
type: proposal
context: personal
action: write canonical files derived from the approved intake summary and normalization pass — context/ identity, domains, boundaries, people, dates; state/projects/ for active and dormant projects; rules/ extensions (compartmentalization, safe-to-ignore, approval-gates) and new rules/auditor-charter.md; workflows/daily-briefing.md update; status updates to workflows/bootstrap-interview.md and AGENTS.md
target: repository — context/, state/projects/, rules/, workflows/, AGENTS.md
source: bootstrap intake 2026-05-19, normalization pass 2026-05-19 (Groups A–L)
as_of: 2026-05-19
confidence: confirmed for CEO-stated content; inferred where flagged (e.g., MTS projects); assumed where flagged
requires_approval: true
depends_on:
  - proposals/2026-05-19-bootstrap-intake-summary.md (approved with changes)
  - proposals/2026-05-19-bootstrap-normalization-pass.md (approved with Group L corrections)
---

# Canonical-File Proposal — 2026-05-19

Exact proposed content for every canonical file. The Chief Operating Officer (COO) will write these files only after the Chief Executive Officer (CEO) approves this proposal.

Conventions:
- File blocks fenced with their target path as a header.
- `FRONTMATTER` and body shown as the file would be saved.
- Acronyms expanded on first use per file.
- Items still needing user resolution (Open questions, deferred decisions) appear in each file's "Open questions" section, not as confirmed facts.

---

## File 1 — `context/identity.md`

```markdown
---
type: context
name: identity
context: personal
source: bootstrap-interview
as_of: 2026-05-19
confidence: confirmed
---

# Chief Executive Officer (CEO) Identity

## Name and household
- **Name:** Sean Hansell
- **Spouse:** Maria Hansell née Puswald ("Bunny"); married 2007-05-06
- **Daughter:** Seane Irene Hansell (pronounced same as "Sean"); born 2014-05-26
- **Residence:** Kailua-Kona, Hawai‘i
- **Timezone:** Hawai‘i Standard Time (HST); works Eastern Time (ET)-aligned hours

## Roles
- **Lead Systems Engineer** at MTS Pro Services (MTS) — IT services company based in New York City
- **Owner** of Darkstar Technology (Darkstar) — early-stage home automation and IT consulting intended for Hawai‘i customers; not yet operational

## Tone preferences
- Operational, brief, specific, low-fluff
- Direct when something is risky, unclear, stale, unsupported, or not actionable
- No generic encouragement, false warmth, or productivity-coach language
- Make priority distinctions explicit; do not treat everything as equally important
- Do not over-apologize
- Concrete verbs and clear next actions; exact dates when timing matters
- For technical / rules-driven / legal-adjacent / financial / medical / operational topics: distinguish known vs. inferred vs. needs-confirmation

## Failure modes the system must avoid (ranked)
1. Obligation invention from thin context
2. Burying urgent items under polish or stale content
3. Nagging about deferred items
4. Sensitive-context leakage into general briefings
5. Mixing contexts in one priority list
6. Promoting inactive projects to active obligations
7. Treating stale memory as current truth
8. Over-completeness at the cost of usefulness
9. Excessive caution that refuses to be useful
```

---

## File 2 — `context/domains.md`

```markdown
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
```

---

## File 3 — `context/boundaries.md`

```markdown
---
type: context
name: boundaries
context: personal
source: bootstrap-interview
as_of: 2026-05-19
confidence: confirmed
---

# Boundaries — Identity, Approval, Compartmentalization

## Identity routing

Per primary operating context, the execution identity used when an action is eventually approved:

| Context | Execution identity |
|---|---|
| MTS Pro Services | `sean@mtsproservices.com` (MTS Google Workspace) |
| Darkstar Technology | `sean@darkstartechnology.net` (currently aliased to `sean@morelen.net`); appears as Darkstar |
| Family | `sean@morelen.net`; iMessage as Sean Hansell |
| Home | `sean@morelen.net` |
| School | `sean@morelen.net` from parent; platform-constrained Classroom interactions inside Seane's school account |
| Parenting | `sean@morelen.net`; iMessage; in-person |
| Personal Operations | `sean@morelen.net` |

### Identity rules

- MTS identity for MTS only. Never personal / family / home / school / Parenting / Darkstar.
- Darkstar items appear as Darkstar externally. If the alias is unavailable, do not silently send as Morelen.
- COO must never act as Seane even when access exists; access ≠ permission. Any Classroom interaction inside Seane's account requires explicit approval and identity labeling.
- COO must never represent or act as Maria. Maria can be modeled as collaborator, owner, waiting-on, target, or invitee.
- Historical aliases / domains / identities must not be assumed current, canonical, or appropriate for action.

## Approval ladder

**Tier 0 — Prohibited unless separately authorized.** Acting as Maria; acting as Seane; MTS identity/systems/confidential info used for non-MTS work; disclosure of secrets/credentials/recovery codes; financial transactions; legal/tax/insurance/employment-agreement/business-risk actions; signing/binding/filing/registering/subscribing/canceling/committing money.

**Tier 1 — High-risk / sensitive / binding / hard-to-undo.** Seane school account actions; Maria identity actions; MTS confidential material; home security/account recovery/passwords/secrets/access/locks/cameras/alarms/Domain Name System (DNS)/remote access/infrastructure exposure; deletions; public posts; sensitive disclosures. Requires proposal + explicit confirmation + restate-the-action confirmation; must include identity/account, target/recipient/system, exact action, risk summary, and undo/mitigation notes. **Deletion always Tier 1, even when the system claims it is recoverable.**

**Tier 2 — Medium-risk interpersonal/operational.** Person-targeted email/Slack/Short Message Service (SMS)/iMessage/Discord/Remind; calendar events with invitees; Jira/Todoist changes that create expectations for others; vendor contact; appointment scheduling. Requires proposal + explicit approval identifying action, identity/account, recipient/system, and intended effect.

**Tier 3 — Low-risk reversible personal-system changes.** No-invite calendar holds on Morelen; personal Todoist updates; personal reminders; personal mailbox drafts; messages to self. Not approved by default in Phase 1; reconsider post-connector. Deletion not Tier 3 even if reversible.

**Tier 4 — Repo-internal / no external effect.** Inbox triage, file moves, source-gap notes, defer/suppress/triage state changes, proposal files, metadata updates, drafting proposed text inside the repo, archiving per explicit rules. Standing approval.

## Standing approvals (Phase 1)

- Triage `state/inbox/` when routing is unambiguous.
- Mark items `defer` / `suppress` / `triage` per [rules/safe-to-ignore.md](../rules/safe-to-ignore.md).
- Add new repo-internal state files for items lacking one.
- Add manual / source-gap entries in `state/manual/` when no external canonical system exists.
- Update repo-internal metadata (context, related_contexts, domain tags, canonical source, confidence, status, review cadence, surface state, surface_triggers).
- Create proposal files under `proposals/`.
- Archive stale proposals only when (a) explicit archive rule applies, (b) origin metadata is preserved, (c) action is logged. Archive ≠ delete.

All other actions: proposal + explicit approval at the appropriate tier.

## Cross-context prohibitions

- MTS data / work product / code / prompts / customers / pricing / templates / processes / architecture / documents / confidential information → never used in any other context.
- MTS systems → never used to store, draft, route, or track personal / family / home / school / Parenting / Darkstar / unrelated material.
- Personal / Family / Home / Parenting communications → never sent from MTS identity.
- School communications → never routed through MTS identity.
- Darkstar drafts, proposals, business docs, prospect notes, or external communications → never authored from MTS account or stored in MTS systems.
- MTS-originated work product → never used as Darkstar material.
- COO must never act as Seane even when account access exists.
- COO must never represent Maria, access Maria's accounts, or imply Maria's approval.

## Non-goals

- Therapy, journaling, emotional processing, motivational support
- Personality profiling
- Medical decisions, medication recommendations, diagnoses, treatment plans
- Professional legal / tax / insurance / financial advice
- Indiscriminate archive of all life context
- Tracking project-specific detail when it does not create life obligations
- Acting as Maria or Seane under any circumstance
- Using MTS data / work product / context in any non-MTS context
- Surfacing precise home location / household security / private network / smart-home exposure in general outputs
- Surfacing sensitive family / relationship / medical / mental-health / financial / employer / location context in routine briefings absent direct relevance
- Inferring school facts without source
- Speculating about employer, coworkers, clients, prospects, vendors
- Generating obligations from ideas, interests, maybes, brainstorms, concerns, or old context
- Nagging about deferred items

## Emergency / survivorship access

Future requirement, not Phase 1. Maria must eventually have authenticated access to necessary household / account / domain / infrastructure / LifeOps continuity material if Sean dies or becomes incapacitated. Future design requires:

- Strong authentication preventing spoofing or social-engineering
- Pre-authorized survivorship workflow rather than ad-hoc request-response
- Identified critical systems and access paths (without exposing them in routine context)
- Delay / verification steps before access release
- Privacy-preserving treatment of items that should remain sealed unless necessary

Phase 1 records this as a known future design requirement only. Tracked as the `digital-survivorship-maria-emergency-access` project in `state/projects/`.

## Open questions

- Where domain renewal failures are detected (registrar email to `sean@morelen.net`?) — confirm as ingress source.
- Diane's preferred communication channel.
```

---

## File 4 — `context/people.md`

```markdown
---
type: context
name: people
context: personal
source: bootstrap-interview
as_of: 2026-05-19
confidence: confirmed
---

# People

## Family (individuals)

### Maria Hansell née Puswald ("Bunny")
- Relationship: Wife
- Primary context: Family
- Channel: iMessage and in-person
- Accounts: `maria@morelen.net`
- Notes: Future emergency/survivorship access person. May be modeled as collaborator, owner, waiting-on, target, or invitee — never an identity the COO operates.

### Seane Irene Hansell ("Seane", "Seaney"; common mispronunciation "Shawnee")
- Relationship: Daughter, minor
- Primary context: Family
- Related contexts: Parenting, School
- Channel: iMessage and in-person; parent comms via parent identity `sean@morelen.net`
- Notes: Spelled "Seane", pronounced same as "Sean". COO must never act as Seane. School account `3712000032@k12.hi.us` access does not imply permission to represent her identity.

### Diane Hansell ("Mom")
- Relationship: Sean's adoptive mother; Seane's grandmother
- Primary context: Family
- Location: Valley Stream, New York
- Channel: TBD
- Notes: Relevant for family travel, birthday planning, visits, family logistics. 80th birthday 2026-06-15.

### Brian Magh and Jessica "Jessie" Magh née Tagney
- Relationship: Seane's godparents; family friends
- Primary context: Family
- Channel: iMessage
- Notes: Relevant for NY trip and family visit coordination.

### Ethan Magh, Lily Rose Magh
- Relationship: Children of Jessie and Brian
- Primary context: Family

### Christopher "Chris" Hansell
- Relationship: Sean's adoptive brother
- Primary context: Family

### Brett Bastiansen
- Relationship: Sean's maternal half-sister
- Primary context: Family

### Jason Mills
- Relationship: Sean's maternal half-brother
- Primary context: Family

### Laura Mills née Edwards
- Relationship: Sean's birth mother
- Primary context: Family

### Robert "Bob" Hansell (deceased)
- Relationship: Sean's adoptive father
- Primary context: Family
- Date treatment: day-of only

### John Puswald
- Relationship: Maria's brother
- Primary context: Family

### Christina Prisco née Puswald
- Relationship: Maria's sister
- Primary context: Family

### Matthew Prisco
- Relationship: Maria's brother-in-law (husband of Christina)
- Primary context: Family

### Frank Puswald (deceased), Irene Puswald (deceased)
- Relationship: Maria's parents
- Primary context: Family
- Date treatment: day-of only

## Personal (individuals)

### Kenneth "Ken" Taber
- Relationship: Thursday Dungeons & Dragons (D&D) host; friend
- Primary context: Personal Operations
- Channel: SMS, Discord

## MTS Pro Services (individuals)

### Mike Volchok
- Role: Chief Executive Officer (CEO) / founder
- Primary context: MTS Pro Services
- Routing: founder-level priority, executive arbitration, EOS / Level 10 (L10) decisions, organizational direction. Not the first recipient for implementation detail unless it affects risk, revenue, or accountability.

### Aaron Smith
- Role: Chief Technology Officer (CTO) / Chief Information Security Officer (CISO) / Systems Director
- Primary context: MTS Pro Services
- Routing: primary strategic and technical counterpart. Direct Slack / working-session for high-context reasoning. Route through him on decisions affecting Systems standards, security posture, architecture, escalation policy, or role boundaries.

### Armando Siliezar
- Role: Talos team lead
- Primary context: MTS Pro Services
- Routing: Talos execution, Apple Mobile Device Management (MDM) delivery, Jamf. Escalate to Sean or Aaron when architecture / revenue / platform boundary involved.

### Phil Van Lewis
- Role: Helios lead; Windows endpoint context
- Primary context: MTS Pro Services
- Routing: Helios / Windows MDM / Intune / JumpCloud. Route to Sean/Aaron when scope bleeds into identity, networking, or architecture.

### Charles Javallas
- Role: Infrastructure engineer
- Primary context: MTS Pro Services
- Routing: infrastructure implementation, on-site / network, Synology / storage / hardware lifecycle. Task-specific, explicit communication because non-project labor scheduling is structurally fragile.

### Bob Thomas
- Role: Operational / process owner; onboarding / documentation rocks
- Primary context: MTS Pro Services
- Routing: process-template work, onboarding standardization, documentation framework, cross-department operational cleanup.

### Joey Tesauro
- Role: Support leadership; process owner
- Primary context: MTS Pro Services
- Routing: Tier 1/2 process design, onboarding/offboarding workflow, escalation pattern correction. "Why does this keep happening?" not "who fixes this ticket?"

### Amanda Thompson
- Role: Account Management (AM) leadership; client operations
- Primary context: MTS Pro Services
- Routing: client-facing friction, contract/service context, repeat-client behavior, non-project labor scheduling. Receive signal before a client-facing operational issue turns into relationship damage.

### Travis Zwerger
- Role: Olaplex client / AM operational bridge
- Primary context: MTS Pro Services
- Routing: Olaplex access requests, forms, integrations, MTS↔client coordination.

### Tiberiu "Tibby" Stanescu
- Role: Olaplex-side technical / operational stakeholder
- Primary context: MTS Pro Services
- Routing: Olaplex technical approvals, access/process questions, Gemini, Skedda, device/security policy context.

## MTS Pro Services (groups)

### Project Management team
- Routing: client projects, internal initiatives, EOS Rock execution, cross-functional Systems/PM work. Jira project space for execution tracking; workstreams need clear owners; tasks need one accountable assignee.

### Account Management team
- Routing: client expectations, repeat Direct Message (DM) patterns, Quarterly Business Reviews (QBRs), client-facing context, service-subscription visibility. Bring in for client behavior correction, support-channel bypass repetition, or relationship-consequence operational issues.

### Support team / Tier 1 and Tier 2 leads
- Routing: intake, triage, escalation, recurring execution. Signal flows through Halo / Jira Service Management (JSM) / support channels first, not direct technician DMs. Escalations to Systems must include reproduction, impact, and prior troubleshooting.

## Open questions

- Diane's preferred channel
- Lily Rose Magh date of birth
- Laura Mills née Edwards birth year
```

---

## File 5 — `context/dates.md`

```markdown
---
type: context
name: dates
context: personal
source: bootstrap-interview
as_of: 2026-05-19
confidence: confirmed
---

# Dates

## Lead-time defaults

- **Birthday:** 30 days (gift/travel/shipping) + 14 days (planning) + 3 days (final reminder) + day-of. Deceased: day-of only.
- **Anniversary:** 30 / 14 / 3 / day-of.
- **Memorial date:** 7 days awareness + day-of. Do not frame as action unless attached.
- **Halloween / Christmas seasonal decoration projects:** 60 / 45 / 30 days before completion target; day-of holiday awareness only. (Linked to project files in `state/projects/`.)
- **School breaks / no-school days:** 7 days + day-of.
- **School semester / year start or major transitions:** 30 days + applicable shorter intervals.
- **Domain renewals — Tier A (operationally critical):** 30 / 14 / 3 / day-of (verify auto-renew succeeded).
- **Domain renewals — Tier B (identity reservations):** 14 / day-of.
- **Domain renewals — Tier C (needs classification):** per-domain after classification.
- **Domain renewals — Tier D (historical):** suppress; surface only on registrar failure or explicit review.

## Recurring personal dates (annual unless noted)

| Event | Date | Person | Primary context | Notes |
|---|---|---|---|---|
| Wedding anniversary | 2007-05-06 | Maria & Sean | Family | |
| Birthday | 2014-05-26 | Seane | Family | Related: Parenting |
| Birthday | 1983-03-20 | Maria | Family | |
| Birthday | 1983-10-17 | Sean | Personal Operations | |
| Birthday | 1946-06-15 | Diane "Mom" | Family | |
| Birthday | 1946-06-01 | Robert "Bob" Hansell (father, deceased) | Family | Day-of only |
| Birthday | 1987-07-19 | Christopher "Chris" Hansell | Family | |
| Birthday | 07-17 (year unknown) | Laura Mills née Edwards | Family | NEEDS SOURCE for year |
| Birthday | 1981-08-02 | Brett Bastiansen | Family | |
| Birthday | 1987-03-11 | Jason Mills | Family | |
| Work anniversary | 2007-03-19 | Sean / MTS | MTS Pro Services | |
| Wedding anniversary | 1972-06-24 | Diane & Bob (Bob deceased) | Family | Day-of only |
| Birthday | 1949-05-14 | Irene Puswald (deceased) | Family | Day-of only |
| Birthday | 1940-10-05 | Frank Puswald (deceased) | Family | Day-of only |
| Birthday | 1981-10-31 | John Puswald | Family | |
| Birthday | 1988-06-20 | Christina Prisco née Puswald | Family | |
| Wedding anniversary | 1980-12-14 | Frank & Irene (deceased) | Family | Day-of only |
| Birthday | 1989-04-06 | Matthew Prisco | Family | |
| Birthday | 1983-05-13 | Brian Magh | Family | |
| Birthday | 1983-11-07 | Jessie Magh | Family | |
| Birthday | 2014-11-07 | Ethan Magh | Family | |
| Birthday | TBD | Lily Rose Magh | Family | NEEDS SOURCE |

## Seasonal projects (recurring; linked to project files)

| Project | Completion target | Event | Primary context | Linked project |
|---|---|---|---|---|
| Halloween House Decoration | 09-30 | 10-31 | Home | `state/projects/halloween-house-decoration.md` |
| Christmas House Decoration | 11-25 | 12-25 | Home | `state/projects/christmas-house-decoration.md` |

## 2026-2027 school year (Hawai‘i State Department of Education [HIDOE])

Source: HIDOE 2026-2027 Official School Calendar, approved 2023-06-01, amended 2026-03-30. Primary context: School.

| Date | Item |
|---|---|
| 2026-08-03 | Students' first day (Quarter 1 [Q1] begins) |
| 2026-08-21 | Statehood Day (no school) |
| 2026-09-07 | Labor Day |
| 2026-10-02 | Q1 ends |
| 2026-10-05 to 2026-10-09 | Fall Break |
| 2026-11-03 | Election Day |
| 2026-11-11 | Veterans' Day |
| 2026-11-26 | Thanksgiving |
| 2026-11-27 | School Holiday (day after Thanksgiving) |
| 2026-12-18 | Q2 ends / 1st semester ends |
| 2026-12-21 to 2027-01-01 | Winter Break |
| 2026-12-25 | Christmas |
| 2027-01-01 | New Year's Day |
| 2027-01-04 | Teacher workday (no students) |
| 2027-01-05 | 2nd semester begins |
| 2027-01-18 | Dr. Martin Luther King Jr. Day |
| 2027-02-08 to 2027-02-12 | Institute Day window (one day no students; Hawai‘i Island date TBD) |
| 2027-02-15 | Presidents' Day |
| 2027-03-12 | Q3 ends |
| 2027-03-15 to 2027-03-19 | Spring Break |
| 2027-03-26 | Good Friday / Kuhio Day (school observes 2027-03-29) |
| 2027-05-21 | Earliest commencement |
| 2027-05-27 | Last day for students / 2nd semester ends |
| 2027-05-31 | Memorial Day |

## One-time future anchors (2026)

| Date | Item | Primary context | Related |
|---|---|---|---|
| 2026-05-26 | Seane's 12th birthday | Family | Parenting |
| 2026-06-09 to 2026-06-29 | New York trip window | Family | Travel |
| 2026-06-13 5pm ET / 12pm HST | Reunion (name TBD) | Family | NEEDS DECISION |
| 2026-06-15 | Diane "Mom" 80th birthday | Family | Travel |
| 2026-06-24 | Diane & Bob 54th wedding anniversary | Family | Day-of only (Bob deceased) |
| 2026-06-24 | Evanescence concert — Seane's first concert | Family | Parenting + Travel |
| TBD | Jessie/Brian NY visit | Family | NEEDS SOURCE |
| TBD | Riverhead Aquarium | Family | NEEDS SOURCE |

## Domain renewals

Source: registrar screenshots 2026-05-19. All status active, auto-renew on as of that date. All non-MTS, non-Darkstar domains classified under **Personal Operations** with technology-domain primary; related contexts mark user-facing impact.

| Tier | Domain | Expiry | Primary context | Related contexts |
|---|---|---|---|---|
| A | `morelen.net` | 2027-01-25 | Personal Operations | Family |
| A | `darkstartechnology.net` | 2026-09-16 | Darkstar Technology | — |
| A | `projectefed.com` | 2026-10-19 | Personal Operations | — |
| B | `seanhansell.com` | 2027-03-08 | Personal Operations | — |
| B | `seanehansell.com` | 2027-04-08 | Personal Operations | Family, Parenting |
| B | `mariahansell.com` | 2027-04-08 | Personal Operations | Family |
| C | `bigislandjeep.club` | 2026-09-12 | Personal Operations | NEEDS DECISION |
| C | `bigislandjeepclub.com` | 2026-09-06 | Personal Operations | NEEDS DECISION |
| C | `bigislandjeepers.com` | 2027-01-04 | Personal Operations | NEEDS DECISION |
| C | `darkstar.games` | 2027-05-29 | Personal Operations | NEEDS DECISION (Darkstar-adjacent?) |
| C | `darkstarknights.com` | 2026-09-14 | Personal Operations | NEEDS DECISION (Darkstar-adjacent?) |
| D | `sew-wrestling.com` | 2026-10-15 | Personal Operations | historical_likely; suppress |
| D | `thepwf.co.uk` | 2026-10-14 | Personal Operations | historical_likely; suppress |
| D | `sovereigninnovations.com` | 2026-09-08 | Personal Operations | historical_likely; suppress |
| D | `sovinn.com` | 2026-10-19 | Personal Operations | historical_likely; suppress |
| D | `djctemple.com` | 2027-02-12 | Personal Operations | historical_likely; suppress |
| D | `djctemple.co.uk` | 2026-09-16 | Personal Operations | historical_likely; suppress |
| D | `eronautic.com` | 2027-02-03 | Personal Operations | historical_likely; suppress |
| D | `fanwaypoint.com` | 2027-02-03 | Personal Operations | historical_likely; suppress |
| D | `paximperius.com` | 2026-09-11 | Personal Operations | historical_likely; suppress |
| D | `salvecraft.com` | 2026-09-18 | Personal Operations | historical_likely; suppress |

## Open questions

- Reunion 2026-06-13 name
- Jessie/Brian NY visit date(s)
- Riverhead Aquarium date
- Lily Rose Magh date of birth
- Laura Mills née Edwards birth year
- Current 2025–2026 school year end date (in scope?)
- Hawai‘i Island Institute Day specific date
- Tier C domain classification
- Tier D domain confirmation
- Deferred recurring date categories (tax, vehicle registration/inspection, annual physical/dental, Darkstar business filings)
```

---

## File 6 — `rules/compartmentalization.md` (REPLACE)

```markdown
---
type: rule
applies_to: all agents
---

# Compartmentalization

LifeOps prioritizes across the whole life, but executes with strict context separation.

## Primary operating contexts

Every state file, input, proposal, and briefing entry carries exactly one **primary operating context**. Allowed values:

- `MTS Pro Services` — employer/work context
- `Darkstar Technology` — early-stage business context
- `Family` — shared family system, marriage/spouse logistics, extended family, family travel, celebrations, relatives, holidays, family finance review, family continuity, and family-facing obligations
- `Home` — property, household infrastructure, repairs, maintenance, smart-home, network, physical home projects, and household operational systems
- `School` — school-system, academic, teacher/admin, calendar, assignment, portal, registration, supply, and school-communication obligations
- `Parenting` — child-facing care, development, routines, supervision, comfort, activities, child-specific logistics, and parenting decisions
- `Personal Operations` — Sean-owned personal systems, technology infrastructure, personal administration, individual projects, personal accounts/domains, health coordination, and personal learning not better owned by MTS or Darkstar
- `unknown` — triage context; routes to `state/inbox/`

## Related contexts

A state file may carry `related_contexts:` (a list) to capture cross-context impact. Related contexts are tags; they do not change the primary or the identity that would execute an action.

## Routing rule

For any item that crosses Family / Parenting / School / Home / Personal Operations, choose the primary context by the **nature of the obligation and owner of the next action**, not merely by who is affected.

- Do not route to `Personal Operations` merely because Sean is the actor or the source is Sean-provided.
- Technical personal infrastructure (accounts, domains, identity, migrations, personal systems) belongs in `Personal Operations` even when it has Family / Home / Parenting impact.
- Seane is a Family member first. Parenting is a responsibility mode applied as a related context.

## Public

`public` is a separate external/source/relevance context — not a primary operating context. Use for news, weather, civic, travel-safety, school/public-calendar, and other external signals. Items labeled `public` do not surface by default unless tied to an active obligation, tracked topic, safety issue, travel, weather, school, household operations, or explicit request.

## Identity and accounts

The Chief Executive Officer (CEO) has distinct accounts and identities per context. See [context/boundaries.md](../context/boundaries.md) for the canonical mapping. Account credentials never enter the repository.

Cross-context prohibitions:

- MTS data / work product / code / prompts / customers / pricing / templates / processes / architecture / documents / confidential information → never used in any non-MTS context.
- MTS systems → never used to store, draft, route, or track non-MTS material.
- Personal / Family / Home / Parenting / Darkstar / school communications → never sent from MTS identity.
- Darkstar material → never authored from MTS account or stored in MTS systems.
- COO must never act as Seane even when account access exists.
- COO must never represent or act as Maria.
- Historical aliases / domains / identities are not assumed current, canonical, or appropriate for action.

## Rules

- Every state file MUST declare `context:` from the allowed set above.
- Every state file MAY declare `related_contexts:` as a list of additional primary contexts (or `public`).
- Every input file SHOULD declare `context:`. If absent, treat as `unknown` and route to `state/inbox/`.
- A proposal MUST declare which context's identity, account, or channel would execute it. A proposal that would mix contexts is invalid and must be split or escalated.
- Briefings reconcile across all contexts for prioritization but label every line with its primary context.
- Drill-down files about one context must not embed verbatim content from another.
- Do not infer or guess context. If unsure, label `unknown`.

## Phase 1 enforcement

Phase 1 enforces compartmentalization through frontmatter labels and rule discipline only. Before any real personal, work, or school data enters the repository, the compartmentalization model must be re-evaluated. See Future Action Items in [AGENTS.md](../AGENTS.md).
```

---

## File 7 — `rules/safe-to-ignore.md` (REPLACE)

```markdown
---
type: rule
applies_to: all agents
---

# Safe to Ignore

The point of LifeOps is to reduce cognitive load, not to resurface every obligation. The system suppresses or defers items aggressively, but never silently.

## Surface states (canonical, four)

Every item has one of four surface states:

- `surface` — show in the default briefing
- `defer` — known and tracked; suppressed from default briefing until a documented trigger fires (date, dependency, milestone, review-window, or activation). Briefing shows a count, not the items.
- `suppress` — explicitly marked not worth attention now. Briefing shows a count and a one-line category summary.
- `triage` — visible holding lane for items requiring classification, routing, source confirmation, or Chief Executive Officer (CEO) decision before they can safely become `surface`, `defer`, or `suppress`.

### Triage rules

- A `triage` item must declare a `triage_question:` (one-line description of what needs deciding) and a `resolution_path:` listing the allowed next states: any of `surface`, `defer`, `suppress`, `archive`, `close`.
- Triage items must not be presented as normal obligations. They appear in a dedicated Triage section of the briefing, not under the priority sections used for surfaced obligations.
- An item may not remain in `triage` indefinitely. Each triage item must include a `triage_age` review per the briefing workflow; the auditor flags stale triage.

### Surface triggers

Items in `defer` may declare `surface_triggers:` — a list of conditions that, when met, surface the item. Allowed triggers include: date reached, dependency satisfied, milestone reached, scheduled review window, registrar failure, deadline, real-world consequence detected, conflict detected, or explicit CEO request. Without a matching trigger, a `defer` item stays in counts only.

## Anti-guilt principle

- `suppress` does not mean forgotten. Every suppressed, deferred, and triage item retains its file and is revisitable by direct query.
- The system does not nag. An item moved to `defer` / `suppress` / `triage` does not return to `surface` until its declared trigger fires or its triage question is resolved.
- The system does not invent obligations. If no source confirms an obligation, it is not surfaced.

## Default categories (refined by bootstrap interview)

Suppress aggressively unless a documented trigger fires:

- Hobby / wish-list / someday-maybe items without explicit current commitment
- Early-stage business ideas (Darkstar Technology) without active task / deadline / commitment / risk / scheduled review
- Recurring obligations handled by another person, automation, or external system
- Low-stakes administrative items past their useful window
- School items without source or explicit user-provided context
- Financial items without source / deadline / consequence / current review
- Stale project context not recently activated
- General health/productivity nudges without concrete plan / appointment / metric / commitment
- Public / news / external content without active-context relevance
- General reminders that do not affect today or the next few days
- Recurring operations appearing as projects without a bounded outcome
- Anything tagged `Personal Operations` that should be `unknown`

## Briefing format

The default briefing:

- Surfaces items in `surface` state in the priority sections defined by [workflows/daily-briefing.md](../workflows/daily-briefing.md).
- Shows `triage` items in a dedicated Triage section (not mixed with normal obligations).
- Collapses `defer` and `suppress` items into counts at the bottom, with a single line per category.

The CEO may drill in by asking.
```

---

## File 8 — `rules/approval-gates.md` (REPLACE)

```markdown
---
type: rule
applies_to: all agents
---

# Approval Gates

The default is deny. External effect requires explicit Chief Executive Officer (CEO) approval at the appropriate tier.

## Approval ladder (canonical)

### Tier 0 — Prohibited unless separately authorized

- Acting as Maria
- Acting as Seane
- Using MTS Pro Services (MTS) identity or systems for personal, Family, Home, Parenting, School, or Darkstar Technology (Darkstar) work
- Using MTS confidential information in any non-MTS context
- Disclosure of secrets, credentials, recovery codes, tokens, or private access paths
- Financial transactions
- Legal, tax, insurance, employment-agreement, or business-risk actions
- Signing, filing, registering, binding coverage, subscribing, canceling, or committing money

Not approvable under the normal flow. Requires a separate policy, explicit authorization, and appropriate authentication where relevant.

### Tier 1 — High-risk / sensitive / binding / hard-to-undo

- Any action involving Seane's school account or school communications beyond routine low-risk clarification
- Any action involving Maria's identity, accounts, or implied consent
- Any action involving MTS confidential or employer-sensitive material
- Any action involving home security, account recovery, passwords, secrets, access, locks, cameras, alarms, Domain Name System (DNS), remote access, or infrastructure exposure
- **Deletion of any record (external or repo-internal beyond explicit archive rules) — deletion is always Tier 1, even when the system claims it is recoverable**
- Public posts
- Sending sensitive relationship, medical, financial, employer, school, or family information

Approval requirements:

- Proposal file under `proposals/`
- Explicit approval
- **Restate-the-action confirmation**
- Must include identity/account, target/recipient/system, exact action, risk summary, and undo/mitigation notes where possible

### Tier 2 — Medium-risk interpersonal or operational

- Sending email to a person
- Sending Slack / Short Message Service (SMS) / iMessage / Discord / Remind message
- Creating calendar events with invitees
- Creating or modifying Jira tickets
- Creating or modifying shared Todoist tasks
- Contacting vendors
- Scheduling appointments
- Routine school, family, home, work, or Parenting communications
- Any change that creates expectations for another person

Approval requirements:

- Proposal file under `proposals/`
- Explicit approval identifying action, identity/account, recipient/system, and intended effect

### Tier 3 — Low-risk reversible personal-system changes

- Creating a no-invite calendar hold on Morelen calendar
- Updating a personal Todoist task
- Creating a personal reminder
- Saving a draft in a personal mailbox
- Sending a message to oneself
- Other reversible, private, non-sensitive changes in a personal system

Approval requirements (Phase 1):

- Not approved by default
- Future policy may allow standing approval by narrow category
- Until then: proposal + explicit approval
- Deletion is never Tier 3 even when reversible

### Tier 4 — Repo-internal / no external effect

- Classifying inbox items
- Moving repo-internal files
- Adding source-gap notes (`state/manual/`)
- Marking `defer` / `suppress` / `triage`
- Creating proposal files
- Updating internal metadata
- Drafting proposed text or actions inside the repo without publishing, sending, scheduling, saving externally, or notifying anyone
- Archiving according to explicit archive/retention rules (preserve origin metadata, log the action)

Approval: standing under existing repo rules. Logged when meaningful. No per-item approval unless touching protected files or proposing deletion.

## Standing approvals (Phase 1)

- Triage `state/inbox/` when routing is unambiguous
- Mark items `defer` / `suppress` / `triage` per [rules/safe-to-ignore.md](safe-to-ignore.md)
- Add new repo-internal state files for items lacking one
- Add manual / source-gap entries in `state/manual/`
- Update repo-internal metadata
- Create proposal files under `proposals/`
- Archive stale proposals only when archive rule is explicit and logged. **Archive ≠ delete.**

## Proposal format

External actions are not executed. They are drafted as files under `proposals/`:

- One file per proposed action
- Filename: `YYYY-MM-DD-<short-slug>.md`
- Frontmatter must include: `context:`, `related_contexts:` (optional), `action:`, `target:`, `source:`, `as_of:`, `confidence:`, `tier:` (0/1/2/3/4), `requires_approval: true`
- Body: what would happen, what the effect is, identity/account that would execute, recipient/system, risk summary, undo notes, what the CEO must confirm

## Stale-proposal policy (future-phase reference)

- After 7 days with no decision and no deadline/dependency: mark as stale
- After 30 days: archive as expired/no-action unless explicitly preserved
- Silence is never consent for execution

## Repository-internal writes — protected files

These require explicit CEO approval to modify or delete:

- Any file under `context/` (durable user context)
- Any file under `rules/` or `workflows/`
- `CLAUDE.md`, `AGENTS.md`, `.gitignore`
```

---

## File 9 — `rules/auditor-charter.md` (NEW)

```markdown
---
type: rule
applies_to: auditor subagent and any independent check pass
---

# Auditor Charter

The auditor runs in fresh context at the end of every workflow that produces a Chief Executive Officer (CEO)-facing artifact (briefings, proposed canonicalizations, scheduled reviews). It catches what the main thread misses, rationalizes, or rewrites.

## Strictness priorities (ranked)

1. Obligation invention from thin context
2. Sensitive-context leakage into the wrong context
3. Stale context promoted as current
4. Missed urgency or missed real-world consequence
5. External-action proposals without the required approval path
6. Wrong identity/account routing
7. Suppressed / deferred items surfacing without a documented trigger

## Principle

The auditor blocks unsafe publication, not the existence of a briefing.

A briefing may contain unknowns, unresolved questions, stale items, source gaps, decisions needed, and triage items as long as they are clearly labeled. The auditor downgrades certainty, forces triage, reroutes context, or requires source confirmation rather than preventing a useful briefing from being produced.

## Block publication only if

- Sensitive content appears in the wrong context
- MTS Pro Services (MTS) confidential context appears outside the MTS context
- A proposal would execute under the wrong identity
- A Tier 0 action is treated as approvable through the normal ladder
- A deletion is proposed without explicit approval handling
- The briefing presents an inferred, stale, unresolved, or source-missing item as confirmed/current
- The briefing presents a question, triage item, or decision as if it were already resolved
- A school/Seane item is surfaced as confirmed or actionable without source or explicit user-provided context
- The briefing would cause an external action, approval request, or proposal to proceed under the wrong context or risk tier

## Do not block publication merely because

- A source is missing
- A question is unresolved
- A context is `unknown`
- A project needs confirmation
- A school item needs source confirmation
- An item is stale but labeled stale
- An item lacks enough information to act
- The auditor and main briefing disagree

In those cases the briefing proceeds, but the item must be labeled appropriately as one of: TRIAGE, UNKNOWN, NEEDS SOURCE, NEEDS DECISION, STALE, BLOCKED, WAITING, AUDIT WARNING.

## Standing checklist (every run)

- Every factual claim has `source`, `as_of`, and `confidence` where required
- Nothing labeled `inferred` is downstream of a stale or missing source unless clearly marked as inferred / needs-source
- Every state file has an allowed context value
- No proposal mixes contexts
- No proposal would execute under the wrong identity
- No item was promoted from `defer` / `suppress` / `triage` without a documented trigger or resolution
- No surfaced obligation lacks a concrete commitment, deadline, next action, dependency, or real-world consequence
- No unresolved, stale, or inferred item is presented as confirmed/current
- No sensitive-context content appears in the default briefing surface unless directly relevant
- Activity log matches briefing claims
- Approval tier is correctly assigned
- No Tier 0 action is treated as normally approvable
- No Tier 1 action is downgraded to a lower tier
- No deletion is proposed where archive would suffice
- School / Parenting items are source-backed, explicitly user-provided, or clearly labeled NEEDS SOURCE / TRIAGE
- Work / MTS items remain compartmentalized from personal, Family, Home, Darkstar, School, and Parenting contexts
- `unknown` items are not silently treated as Personal Operations
- Triage items declare a `triage_question` and a `resolution_path`

## Safe-to-ignore enforcement

The auditor aggressively flags these as violations if they appear in the default surface without a documented trigger:

- Hobby / wish-list / someday-maybe items without explicit current commitment
- Darkstar items without explicit activation
- Early-stage business ideas without active task / deadline / commitment / risk / scheduled review
- Health / productivity nudges without concrete plan / appointment / metric / commitment
- Public / news items without relevance to an active context
- School items surfaced as confirmed/actionable without source or explicit user-provided context
- Financial items without source / deadline / consequence / current review window
- Stale project context treated as current
- Anything tagged `Personal Operations` that should be `unknown`
- General reminders that do not affect today or the next few days
- Recurring operations appearing as projects without a bounded outcome

The auditor does not flag properly labeled triage, unknown, stale, needs-source, or needs-decision items merely because they are unresolved.

## False-positive tolerance

- First occurrence: flag and log
- If CEO marks a pattern as known-OK, suppress repeat flags for that documented pattern
- If the same issue recurs without a known-OK rule, keep flagging
- **Never suppress repeat flags for Tier 0, Tier 1, identity-related, school-related, employer-confidential, or deletion-related findings**

When the auditor and the main briefing disagree, the auditor's challenge takes precedence over certainty (the disputed item must not be presented as clean/validated) but not necessarily over publication.

## Auditor cannot rewrite policy

The auditor flags conflicts and proposes resolutions. It does not silently rewrite canonical policy under `rules/`, `workflows/`, or `context/`. Any policy change requires explicit CEO approval through the normal repository write rules.

## Reporting

Daily briefing Audit section:

- Counts in the main briefing
- One-line summary per medium or high-severity finding
- Full audit report written to `logs/`
- Log file path or report identifier available for drill-down

Preferred format:

    Audit:
    - 0 blockers
    - 2 warnings
    - 1 stale-source item
    - Highest severity: warning
    - See audit log: <log-id or path>

For blockers:

    Audit:
    - BLOCKED: briefing not clean
    - Reason: <one-line reason>
    - Required action: <triage / source confirmation / approval correction / context correction>

Unresolved prior audit findings reappear in the briefing until acknowledged, fixed, expired, or explicitly marked known-OK. They do not dominate the briefing unless they block action or affect today; otherwise they appear as counts with drill-down.
```

---

## File 10 — `workflows/daily-briefing.md` (UPDATE)

Key changes versus the current file:

1. Replace `surface: surface | defer | suppress` references with the four-state set `surface | defer | suppress | triage`.
2. Replace the briefing structure (lines 70–113 of the current file) with the priority order from the intake summary §9, the label registry, and the seven-context surface format.
3. Replace the auditor-pass section to reference the new `rules/auditor-charter.md` and the auditor blocker/warning reporting.

Replacement for the "Draft the briefing" body (lines 61–114 of the current file):

```markdown
### 5. Draft the briefing

Write to `briefings/YYYY-MM-DD.md` with the following structure. Empty sections are omitted unless the absence itself is operationally meaningful.

    ---
    date: YYYY-MM-DD
    context_status: <bootstrapped | not yet bootstrapped>
    contexts_present: <list>
    ---

    # Briefing — YYYY-MM-DD

    ## Today
    (Time-sensitive items for today, in `surface` state, across all primary operating contexts. Each line labeled with context and any applicable label from the registry below.)

    ## Cross-domain conflicts
    (Work/Family/School/Home/Parenting timing collisions or identity collisions.)

    ## Blocked / waiting on me
    (Items the CEO must unblock.)

    ## Decisions needed
    (Items requiring CEO judgment; every line carries NEEDS DECISION.)

    ## Waiting on others (past expected window)
    (`state/waiting/` direction:inbound items past `expected_by`.)

    ## Triage
    (Items in `triage` state. Each line shows the `triage_question` and the allowed `resolution_path`.)

    ## Upcoming (next 14 days)
    (Anchors from `context/dates.md`, school calendar, recurring dates, and one-time anchors falling within 14 days.)

    ## Approvals queue
    (Open proposals under `proposals/` awaiting decision. Tier shown.)

    ## Per-context detail
    (Only contexts with items to show. Omit contexts that are empty unless absence matters.)
    ### MTS Pro Services
    ### Darkstar Technology
    ### Family
    ### Home
    ### School
    ### Parenting
    ### Personal Operations

    ## Safe to ignore (collapsed)
    - defer: <count> items across <categories>
    - suppress: <count> items across <categories>

    ## Audit
    (Counts + one-liners per medium/high severity finding. Blockers shown explicitly.)

    ## Activity
    - inspected: <count> files
    - inferred: <count> claims
    - proposed: <count> entries → `proposals/`
    - changed: <count> files in `state/`, `inputs/`, `briefings/`
    - refused: <count> actions (reasons in log)
    - log: `logs/YYYY-MM-DD-daily-briefing.md`

Every line in the surfaced sections carries its primary context label and any applicable label from the registry below. `public` content is omitted by default unless tied to an active concern.

### Label registry

| Label | Meaning | Section |
|---|---|---|
| TODAY | Time-sensitive today | Today |
| BLOCKED | Cannot proceed until something resolves | Blocked / waiting on me |
| DECISION | Requires CEO judgment | Decisions needed (every item) |
| WAITING | Awaiting external response past window | Waiting on others |
| CONFLICT | Cross-domain timing or identity collision | Cross-domain conflicts |
| UPCOMING | Within 14-day window | Upcoming |
| TRIAGE | In `triage` state | Triage |
| NEEDS SOURCE | Item requires source confirmation before action | any section |
| NEEDS DECISION | Open question requiring CEO input | any section |
| STALE | Past freshness threshold | any section |
| UNKNOWN | Context cannot be determined | inbox → Triage |
| AUDIT WARNING | Auditor finding requiring CEO attention | Audit |

### Cadence and length

- One briefing per day (not workday-only).
- "Nothing urgent" days produce a brief affirmative briefing.
- The briefing is real but not exhaustive. Default surface is concise; detail lives in drill-down files.
- Each surfaced item carries an item identifier (slug-based) to support drill-down. File paths and source paths appear only on explicit request.
```

Replacement for the audit pass section (current section 7):

```markdown
### 7. Run an independent audit pass

Run an independent audit per [rules/auditor-charter.md](../rules/auditor-charter.md) in fresh context. Provide:

- The path to the draft briefing
- The path to the log
- The list of paths read during the run

In Claude Code, implement this by spawning the `auditor` subagent defined in [.claude/agents/auditor.md](../.claude/agents/auditor.md). Other runtimes spawn an isolated reviewer per the charter.

Wait for the audit findings. Apply the auditor charter's block-vs-warn distinction: a blocker halts publication; warnings flag the briefing but allow publication with appropriate labels.
```

---

## File 11 — `workflows/bootstrap-interview.md` (STATUS UPDATE)

Update the frontmatter from:

```yaml
status: SPEC — do not execute in the current session
invoked_by: explicit Chief Executive Officer (CEO) request in a later session
```

to:

```yaml
status: executed 2026-05-19; spec retained for future re-runs
invoked_by: explicit Chief Executive Officer (CEO) request
last_executed: 2026-05-19
output_artifacts:
  - proposals/2026-05-19-bootstrap-intake-summary.md
  - proposals/2026-05-19-bootstrap-normalization-pass.md
  - proposals/2026-05-19-canonical-file-proposal.md
```

The body of the file is unchanged — the specification still describes how the interview is run if re-invoked later.

---

## File 12 — `AGENTS.md` (FUTURE ACTION ITEMS UPDATE)

In the "Future action items" section (currently lines 54–59), change:

- **Bootstrap interview.** A later session will run [workflows/bootstrap-interview.md](workflows/bootstrap-interview.md) and write durable user context into `context/`.

to:

- **Bootstrap interview.** Executed 2026-05-19. See [proposals/2026-05-19-bootstrap-intake-summary.md](proposals/2026-05-19-bootstrap-intake-summary.md), [proposals/2026-05-19-bootstrap-normalization-pass.md](proposals/2026-05-19-bootstrap-normalization-pass.md), and [proposals/2026-05-19-canonical-file-proposal.md](proposals/2026-05-19-canonical-file-proposal.md). Durable user context populated in `context/`.

Leave the other Future Action Items (compartmentalization re-evaluation, later phases, canonical-source preference) as-is.

---

## File set 13 — `state/projects/` (20 project files)

Each file uses this frontmatter shape:

```yaml
---
type: project
slug: <kebab-case>
context: <primary>
related_contexts: [<list>]
source: bootstrap-interview
as_of: 2026-05-19
confidence: <confirmed | inferred | assumed>
status: <active | dormant | recurring-seasonal>
surface: <surface | defer | suppress | triage>
surface_triggers: [<list>]
labels: [<list>]
triage_question: <only if surface=triage>
resolution_path: <only if surface=triage>
---
```

### MTS Pro Services projects (5)

All declared `confidence: inferred` with `source: bootstrap-interview + Jira project space inspection 2026-05-19`. Default `surface: defer` with `surface_triggers: ["CEO confirmation as active"]` until CEO confirms.

1. **`state/projects/holy-see-mission-it-stabilization.md`** — context: MTS Pro Services. Scope: Stabilize and transition core IT control for Holy See Mission, including DNS/domain control, email authentication, Microsoft 365, service/account ownership, recovery access, device posture, storage/data flow, third-party platforms, and risk findings. Jira space: HSM. Phases 1–3 visible. Several due dates appear overdue. Next action: confirm field state and either execute remaining assessment / control-transition work or clean up stale scaffolding.

2. **`state/projects/holy-see-mission-talos-onboarding.md`** — context: MTS Pro Services. Scope: Complete Talos onboarding for Holy See Mission, including Managed Apple Account and Apple Business Manager (ABM) domain verification. Jira space: HOLY. ABM verification overdue. Next action: resolve domain verification and confirm whether Managed Apple Account work belongs here or under the broader Managed Apple Account Deployment Program.

3. **`state/projects/psp-okta-app-integration.md`** — context: MTS Pro Services. Scope: Internal Okta application integration work currently tracked in PSP, with Zoom as the visible assigned integration. Jira space: PSP. Next action: complete or revalidate Zoom-to-Okta integration status and determine whether other app integrations remain assigned.

4. **`state/projects/managed-apple-account-deployment-program.md`** — context: MTS Pro Services. Scope: Managed Apple Account deployments across MTS and customer environments (MTS, PHS, Holy See, Calcium, ASTM, Thriven, others). Jira spaces: PSP + MAID. Status mixed: active in PSP/PHS, stale in older MAID epics. Next action: identify currently active deployment list, blockers, completion criteria; suppress or close stale MAID epics. Customer-lane confirmation pending.

5. **`state/projects/talos-fleet-management-platform-reliability.md`** — context: MTS Pro Services. Scope: Maintain and repair Talos / Jamf automation, including Self Service+ Application Programming Interface (API) / reporting, JPConfig reporting, Adobe Creative Cloud account detection, and inferred-user reconnaissance logic. Jira space: TFM. Surface state: `triage`. `triage_question: "Surface to LifeOps as strategic-risk stream or keep as engineering backlog?"`. `resolution_path: [surface, defer, suppress]`.

### Non-MTS active projects (9)

6. **`state/projects/lifeops-coo-system-build.md`** — context: Personal Operations. Scope: Build the LifeOps / Chief Operating Officer (COO) system for source modeling, daily briefing, project tracking, approval gates, review cadence, and future connector/sub-agent workflows. Status: active. Surface: surface. Next action: complete bootstrap canonicalization and begin Phase 1 daily-briefing operation.

7. **`state/projects/summer-2026-ny-trip.md`** — context: Family. related_contexts: [Travel]. Scope: Plan 2026-06-09 to 2026-06-29 New York trip — logistics, family visits, work-hours handling, events, Seane-related coordination. Known anchors: Mom's 80th birthday (2026-06-15), Reunion (2026-06-13), Evanescence concert (2026-06-24), Jessie/Brian visit (TBD), Riverhead Aquarium (TBD). Surface: surface.

8. **`state/projects/evanescence-seane-first-concert.md`** — context: Family. related_contexts: [Parenting, Travel]. Scope: Prepare Seane for first concert experience at Evanescence on 2026-06-24 — hearing protection, comfort, expectations, event logistics. Hearing protection purchased; remaining logistics may need confirmation. Surface: surface until resolved.

9. **`state/projects/school-year-planning-2026-2027.md`** — context: School. Scope: Prepare for Seane's 2026-2027 school year — schedule awareness, school systems, parent responsibilities, supplies, routines, transition items. Surface: defer until sourced. `surface_triggers: ["school calendar review", "school source provides item", "30 days before 2026-08-03 students' first day"]`.

10. **`state/projects/home-assistant-smart-home-architecture.md`** — context: Home. Scope: Build out a Home Assistant-centered household control plane, including integrations, exposure boundaries, security posture, and migration path. Status: triage. Surface: triage. `triage_question: "Confirm current activity level (active vs. dormant)."`. `resolution_path: [surface, defer, suppress]`.

11. **`state/projects/project-efed-platform.md`** — context: Personal Operations. Scope: Build the archive-first eFed platform and related application/domain model. Status: triage. Surface: triage. `triage_question: "Confirm current development activity."`. `resolution_path: [surface, defer, suppress]`.

12. **`state/projects/the-hill.md`** — context: Home. related_contexts: [Finance]. Scope: Clear and cover ~4,200 square feet of overgrown hill area in the backyard. Surface: surface. Next action: define clearing/covering approach, validate area/material assumptions, estimate cost/labor, determine Do-It-Yourself (DIY) vs. hired vs. mixed.

13. **`state/projects/halloween-house-decoration.md`** — context: Home. related_contexts: [Family]. Status: recurring-seasonal. Scope: Annual heavy Halloween house decoration. Completion target: 09-30. Event: 10-31. Surface: defer with `surface_triggers: ["60 days before completion target (Aug 1)", "45 days (Aug 16)", "30 days (Aug 31)", "day-of event (Oct 31)"]`. Linked date entry in `context/dates.md`.

14. **`state/projects/christmas-house-decoration.md`** — context: Home. related_contexts: [Family]. Status: recurring-seasonal. Scope: Annual heavy Christmas house decoration. Completion target: 11-25. Event: 12-25. Surface: defer with `surface_triggers: ["60 days before completion target (Sep 26)", "45 days (Oct 11)", "30 days (Oct 26)", "day-of event (Dec 25)"]`. Linked date entry in `context/dates.md`.

### Dormant but important projects (6)

15. **`state/projects/digital-survivorship-maria-emergency-access.md`** — context: Family. Scope: Design secure, authenticated continuity plan so Maria can access necessary household / account / domain / infrastructure / LifeOps knowledge if Sean dies or becomes incapacitated. Surface: defer. `surface_triggers: ["explicit survivorship planning review", "future household continuity planning window", "CEO activation"]`.

16. **`state/projects/darkstar-technology-business-setup.md`** — context: Darkstar Technology. related_contexts: [Finance, Learning]. Scope: Establish early-stage business positioning, systems, service model, identity, documentation, operational readiness. Surface: defer. `surface_triggers: ["quarterly Darkstar review", "concrete prospect", "deadline", "business-risk issue", "explicit activation"]`.

17. **`state/projects/darkstar-technology-website-positioning.md`** — context: Darkstar Technology. related_contexts: [Learning]. Scope: Build or refine public website, service positioning, brand language, business-facing presentation. Surface: defer. `surface_triggers: ["quarterly Darkstar review", "decision to resume website work", "business launch preparation", "concrete prospect"]`.

18. **`state/projects/morelen-account-domain-migration.md`** — context: Personal Operations. related_contexts: [Family]. Scope: Possible future migration of `morelen.net` mail / contacts / calendars from Google Workspace to iCloud custom domains while preserving family usability. Not Apple Business Manager. Surface: defer. `surface_triggers: ["explicit account/domain review", "family account issue", "Google Workspace or iCloud need", "decision to resume migration planning"]`.

19. **`state/projects/home-infrastructure-documentation.md`** — context: Home. Scope: Document home network, smart-home systems, domains, media server, backups, access paths, operational handoff. Surface: defer. `surface_triggers: ["Home Assistant work", "survivorship planning", "infrastructure change", "troubleshooting event", "explicit home documentation review"]`.

20. **`state/projects/health-cardio-flexibility-improvement.md`** — context: Personal Operations. related_contexts: [Health]. Scope: Define and execute bounded plan to improve cardiovascular health, flexibility, sleep stability, energy management. Surface: defer. `surface_triggers: ["monthly health review", "appointment", "symptom/metric change", "explicit routine planning", "decision to activate"]`.

---

## What gets created vs. modified

| Operation | Path |
|---|---|
| CREATE | `context/identity.md` |
| CREATE | `context/domains.md` |
| CREATE | `context/boundaries.md` |
| CREATE | `context/people.md` |
| CREATE | `context/dates.md` |
| CREATE × 20 | `state/projects/*.md` (list above) |
| CREATE | `rules/auditor-charter.md` |
| REPLACE | `rules/compartmentalization.md` |
| REPLACE | `rules/safe-to-ignore.md` |
| REPLACE | `rules/approval-gates.md` |
| EDIT | `workflows/daily-briefing.md` (briefing format + auditor section) |
| EDIT | `workflows/bootstrap-interview.md` (frontmatter status) |
| EDIT | `AGENTS.md` (Future Action Items bullet) |

Per [rules/approval-gates.md](../rules/approval-gates.md), `context/`, `rules/`, `workflows/`, and `AGENTS.md` modifications require explicit CEO approval. This proposal collects them in one place for that approval.

---

## Confirmation request

Please respond with one of:

- **Approve as-is** — COO writes all files listed above and logs the canonicalization run.
- **Approve with changes** — list the changes inline. COO revises this proposal and re-presents.
- **Reject** — no canonical files written. The three proposals (intake summary, normalization pass, canonical-file proposal) remain for future reference.
