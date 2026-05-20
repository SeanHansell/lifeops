---
type: proposal
context: personal
action: transcribe bootstrap intake summary into context/ files (identity, domains, boundaries, people, dates) and add active/dormant project files to state/projects/
target: repository — context/, state/projects/, and a proposed extension to rules/safe-to-ignore.md
source: bootstrap interview, 2026-05-19
as_of: 2026-05-19
confidence: confirmed for user-stated items; assumed/inferred where explicitly marked
requires_approval: true
---

# Bootstrap Intake Summary — 2026-05-19

Draft summary of the 2026-05-19 bootstrap interview. Pending Chief Executive Officer (CEO) confirmation. No file under `context/` is written until the CEO approves this summary.

Abbreviations used: CEO (Chief Executive Officer), Chief Operating Officer (COO), Hawai‘i Standard Time (HST), Eastern Time (ET), Hawai‘i State Department of Education (HIDOE), Mac Mobile Device Management (MDM), Entrepreneurial Operating System (EOS), Apple Business Manager (ABM), Hawai‘i Department of Education school account domain (`k12.hi.us`).

---

## 1. Confirmed facts

### 1.1 Identity
- Name: Sean Hansell
- Role: Lead Systems Engineer at MTS Pro Services (MTS) — IT services company, New York City
- Side business: Owner of Darkstar Technology (Darkstar) — early-stage home automation and IT consulting intended for Hawai‘i customers; not yet operational
- Spouse: Maria Hansell née Puswald (nickname "Bunny"); married 2007-05-06
- Daughter: Seane Irene Hansell (pronounced same as "Sean"); born 2014-05-26
- Residence: Kailua-Kona, Hawai‘i
- Timezone: HST; works ET-aligned hours

### 1.2 Tone preferences
- Operational, brief, specific, low-fluff
- Direct when something is risky, unclear, stale, unsupported, or not actionable
- No generic encouragement, false warmth, productivity-coach language
- Make priority distinctions explicit; do not treat everything as equally important
- Do not over-apologize
- Concrete verbs and clear next actions; exact dates when timing matters
- For technical, rules-driven, legal-adjacent, financial, medical, or operational topics: distinguish known vs. inferred vs. needs-confirmation

### 1.3 Failure modes to avoid (ranked)
1. Obligation invention from thin context
2. Burying urgent items under polish or stale content
3. Nagging about deferred items
4. Sensitive-context leakage into general briefings
5. Mixing contexts in one priority list
6. Promoting inactive projects to active obligations
7. Treating stale memory as current truth
8. Over-completeness at the cost of usefulness
9. Excessive caution that refuses to be useful

### 1.4 Primary operating contexts (seven; amended 2026-05-19)
Replaces the simpler set in [rules/compartmentalization.md](../rules/compartmentalization.md) for item routing. School and Parenting are split. Personal Operations is narrowed to prevent catch-all misuse.

| Context | Type | Default surface |
|---|---|---|
| MTS Pro Services | work | surface |
| Darkstar Technology | business | defer |
| Family | personal | surface |
| Home | personal | surface-when-actionable |
| School | school | surface-with-source |
| Parenting | personal | surface-with-source |
| Personal Operations | personal | surface-when-actionable |

**Definitions:**
- **Family** — shared family system, marriage/spouse logistics, extended family, family travel, celebrations, relatives, holidays, family finance review, family continuity, and family-facing obligations.
- **Home** — property, household infrastructure, repairs, maintenance, smart-home, network, physical home projects, and household operational systems.
- **School** — school-system, academic, teacher/admin, calendar, assignment, portal, registration, supply, and school-communication obligations.
- **Parenting** — child-facing care, development, routines, supervision, comfort, activities, child-specific logistics, and parenting decisions.
- **Personal Operations** — Sean-specific administration, individual planning, personal systems, personal projects, health coordination, personal learning, and individual obligations not better owned by another primary context.
- **MTS Pro Services** — employer / work context (unchanged).
- **Darkstar Technology** — early-stage business context (unchanged).

**Routing rule (amended 2026-05-19):**
- Do not route an item to Personal Operations merely because Sean is the actor or the source is Sean-provided.
- For any item that crosses Family / Parenting / School / Home / Personal Operations, choose the primary context by the **nature of the obligation and owner of the next action**, not by who is affected.
- Technical personal infrastructure (accounts, domains, identity, migrations, personal systems) belongs in **Personal Operations** even when it has Family / Home / Parenting impact. User-facing impact is captured in **related contexts**, not by changing the primary.
- Seane is a Family member first. Parenting is a responsibility mode applied as a related context; not the default container for every Seane-related item.

**Public** is **not** a primary operating context. Public is a separate external/source/relevance context used for news, weather, civic, travel-safety, school/public-calendar, and other external signals. Public never surfaces by default unless tied to an active obligation, tracked topic, safety issue, travel, weather, school, household operations, or explicit request.

### 1.5 Secondary cross-cutting domains
Attach as tags to a primary operating context, not as item homes.

| Domain | Default surface |
|---|---|
| Health | defer-unless-scheduled-or-relevant |
| Travel | surface when active |
| Finance | defer-unless-deadline-or-review |
| Learning | suppress-unless-scheduled-or-activated |

Default classification rule: classify items by primary operating context first, then attach secondary domains as tags. Health/Travel/Finance/Learning are lenses, not homes.

### 1.6 Review cadences
- MTS Pro Services: daily on workdays
- Darkstar Technology: quarterly to start (expected to change)
- Personal Operations: weekly — Saturday morning
- Family: weekly — Sunday; family finance monthly on last weekend
- Home: weekly for active operations/maintenance; monthly for general backlog
- School: weekly Sundays during school year (daily if active/time-sensitive); monthly on the 15th during June and July
- Parenting: weekly year-round
- Health: monthly weekend (standalone exception — only secondary domain with its own review)
- Travel / Learning / Finance: no standalone global review; attach to primary context

### 1.7 Source systems (future canonical, none connected in Phase 1)
- **MTS** — Google Workspace (`sean@mtsproservices.com`), Jira, Atlassian Home (Goals/Projects), Ninety.io (EOS), Confluence, Google Drive, IT Glue (legacy), Slack, Zoom. Sean is super-admin of MTS Google Workspace; admin access is not implied for COO use.
- **Morelen Workspace** (`sean@morelen.net`) — canonical for Personal Operations / Family / Home; temporary catch-all for Darkstar. Sean is super-admin. Darkstar alias `sean@darkstartechnology.net` routes here.
- **Seane school** — `3712000032@k12.hi.us`. Sean has access; does not administer. Future Model Context Protocol (MCP) connection possible but untested.
- **Tasks** — Jira (work), Todoist (personal/home/family). Darkstar has no canonical task system yet.
- **Health** — Kaiser Permanente app, Apple Health.
- **Notes/Docs** — Apple Notes, Google Drive; Obsidian under consideration. Household is currently manual/analog (kitchen whiteboard, physical calendar, iMessage).
- **School systems** — Google Classroom, Infinite Campus, Remind.
- **Scheduling automation** — Reclaim.ai (downstream of Jira/Todoist; not canonical for meaning).
- **Mac Admins Slack** — community reference only; not canonical for obligations; weight ≈ 60% MTS / 20% Darkstar / 20% Personal Operations.

### 1.8 Identity routing
- **MTS** — `sean@mtsproservices.com`. MTS only.
- **Darkstar** — `sean@darkstartechnology.net` (currently aliased to `sean@morelen.net`). External-facing Darkstar must appear as Darkstar; if alias unavailable, do not silently send as Morelen.
- **Personal / Family / Home** — `sean@morelen.net`; iMessage as Sean Hansell for family.
- **School and Parenting** — `sean@morelen.net` from parent. Classroom interactions inside Seane's school account treated as platform-constrained access, never as permission to act as Seane.

### 1.9 Approval ladder
- **Tier 0 — Prohibited unless separately authorized.** Acting as Maria; acting as Seane; MTS identity/systems/confidential info used for non-MTS work; disclosure of secrets/credentials/recovery codes; financial transactions; legal/tax/insurance/employment-agreement/business-risk actions; signing/binding/filing/registering/subscribing/canceling/committing money.
- **Tier 1 — High-risk / sensitive / binding / hard-to-undo.** Seane school account actions; Maria identity actions; MTS confidential material; home security/account recovery/passwords/secrets/access/locks/cameras/alarms/Domain Name System (DNS)/remote access/infrastructure exposure; deletions; public posts; sensitive disclosures. Requires proposal + explicit confirmation + restate-the-action confirmation; must include identity/account, target/recipient/system, exact action, risk summary, undo/mitigation notes. Deletion always Tier 1.
- **Tier 2 — Medium-risk interpersonal/operational.** Person-targeted email/Slack/Short Message Service (SMS)/iMessage/Discord/Remind; calendar events with invitees; Jira/Todoist changes that create expectations for others; vendor contact; appointment scheduling. Requires proposal + explicit approval identifying action, identity/account, recipient/system, and intended effect.
- **Tier 3 — Low-risk reversible personal-system changes.** No-invite calendar holds on Morelen; personal Todoist updates; personal reminders; personal mailbox drafts; messages to self. Not approved by default in Phase 1; future standing approval possible. Deletion not Tier 3 even if reversible.
- **Tier 4 — Repo-internal / no external effect.** Inbox triage, file moves, source-gap notes, defer/suppress, proposal files, metadata updates, drafting proposed text inside repo, archiving per explicit rule. Standing approval.

### 1.10 Standing approvals (Phase 1)
- Triage `state/inbox/` when routing is unambiguous
- Mark items `defer` or `suppress` per rules
- Add new repo-internal state files for items lacking one
- Add manual / source-gap entries when no external canonical system exists
- Update repo-internal metadata (context, domain tags, canonical source, confidence, status, review cadence, stale/suppressed/deferred state)
- Create proposal files under `proposals/`
- Archive stale proposals only if archive rule is explicit and logged
- All other actions: proposal + explicit approval

### 1.11 People (operationally important)
**Personal / Family:**
- Maria Hansell née Puswald ("Bunny") — wife. iMessage and in-person. Has `maria@morelen.net`. Future emergency/survivorship access person.
- Seane Irene Hansell ("Seane", "Seaney"; common mispronunciation "Shawnee") — daughter, minor. iMessage and in-person; parent comms via parent identity.
- Diane Hansell ("Mom") — Sean's adoptive mother, Valley Stream NY. Preferred channel: TBD.
- Brian Magh and Jessica "Jessie" Magh née Tagney — Seane's godparents. iMessage.
- Kenneth "Ken" Taber — Thursday Dungeons & Dragons (D&D) host. SMS and Discord.

**MTS:**
- Mike Volchok — Chief Executive Officer / founder. Revenue priority, EOS / Level 10 (L10) decisions, executive arbitration.
- Aaron Smith — Chief Technology Officer / Chief Information Security Officer / Systems Director. Primary strategic and technical counterpart.
- Armando Siliezar — Talos team lead. Apple MDM / Jamf delivery.
- Phil Van Lewis — Helios lead. Windows MDM / Intune / JumpCloud.
- Charles Javallas — Infrastructure engineer. On-site / network / storage / hardware.
- Bob Thomas — Process/onboarding/documentation rocks.
- Joey Tesauro — Support leadership. Tier 1/2 process, onboarding/offboarding.
- Amanda Thompson — Account Management leadership. Client-facing friction, contract context, non-project labor scheduling.
- Travis Zwerger — Olaplex client/AM bridge.
- Tiberiu "Tibby" Stanescu — Olaplex technical/operational stakeholder.
- Project Management team — execution coordination.
- Account Management team — client relationship interface.
- Support team / Tier 1+2 leads — intake, triage, escalation.

### 1.12 Recurring dates
Lead-time defaults:
- Birthday: 30 days (gift/travel/shipping), 14 days (planning), 3 days (final), day-of. Deceased: day-of only.
- Anniversary: 30 / 14 / 3 / day-of.
- Memorial: 7 days awareness + day-of; do not frame as action unless attached.
- Halloween / Christmas seasonal decoration projects: 60 / 45 / 30 days before completion target; day-of holiday awareness only.

Recurring personal dates (all annual unless noted):
| Event | Original date | Person | Context |
|---|---|---|---|
| Wedding anniversary | 2007-05-06 | Maria & Sean | Family |
| Birthday | 2014-05-26 | Seane | School and Parenting (per primary context rule; Family-secondary) |
| Birthday | 1983-03-20 | Maria | Family |
| Birthday | 1983-10-17 | Sean | Personal Operations |
| Birthday | 1946-06-15 | Diane "Mom" | Family |
| Birthday | 1946-06-01 | Robert "Bob" Hansell (father, deceased) | Family — day-of only |
| Birthday | 1987-07-19 | Christopher "Chris" Hansell (adoptive brother) | Family |
| Birthday | 07-17 (year unknown) | Laura Mills née Edwards (birth mother) | Family |
| Birthday | 1981-08-02 | Brett Bastiansen (maternal half-sister) | Family |
| Birthday | 1987-03-11 | Jason Mills (maternal half-brother) | Family |
| Work anniversary | 2007-03-19 | Sean / MTS | MTS Pro Services |
| Wedding anniversary | 1972-06-24 | Diane & Bob (Bob deceased) | Family — day-of only |
| Birthday | 1949-05-14 | Irene Puswald (Maria's mom, deceased) | Family — day-of only |
| Birthday | 1940-10-05 | Frank Puswald (Maria's dad, deceased) | Family — day-of only |
| Birthday | 1981-10-31 | John Puswald (Maria's brother) | Family |
| Birthday | 1988-06-20 | Christina Prisco née Puswald (Maria's sister) | Family |
| Wedding anniversary | 1980-12-14 | Frank & Irene (both deceased) | Family — day-of only |
| Birthday | 1989-04-06 | Matthew Prisco (brother-in-law) | Family |
| Birthday | 1983-05-13 | Brian Magh | Family |
| Birthday | 1983-11-07 | Jessie Magh | Family |
| Birthday | 2014-11-07 | Ethan Magh | Family |
| Birthday | TBD | Lily Rose Magh | Family |

Seasonal Home projects (recurring):
- **Halloween House Decoration** — completion target 09-30, event 10-31. Surface during active project window (~Aug–Sep), suppress otherwise.
- **Christmas House Decoration** — completion target 11-25, event 12-25. Surface during active project window (~Oct–Nov), suppress otherwise.

### 1.13 2026–2027 school year (HIDOE PDF, approved 2023-06-01, amended 2026-03-30)
Source: confirmed. Context: School and Parenting.
- 2026-08-03 Students' first day
- 2026-08-21 Statehood Day (no school)
- 2026-09-07 Labor Day
- 2026-10-02 Q1 ends
- 2026-10-05 to 2026-10-09 Fall Break
- 2026-11-03 Election Day
- 2026-11-11 Veterans' Day
- 2026-11-26 Thanksgiving
- 2026-11-27 School Holiday (day after Thanksgiving)
- 2026-12-18 Q2 ends / 1st semester ends
- 2026-12-21 to 2027-01-01 Winter Break
- 2026-12-25 Christmas
- 2027-01-01 New Year's Day
- 2027-01-04 Teacher workday (no students)
- 2027-01-05 2nd semester begins
- 2027-01-18 Dr. Martin Luther King Jr. Day
- 2027-02-08 to 2027-02-12 Institute Day window (one day no students; Hawai‘i Island date TBD)
- 2027-02-15 Presidents' Day
- 2027-03-12 Q3 ends
- 2027-03-15 to 2027-03-19 Spring Break
- 2027-03-26 Good Friday / Kuhio Day (school observes 2027-03-29)
- 2027-05-21 Earliest commencement
- 2027-05-27 Last day for students / 2nd semester ends
- 2027-05-31 Memorial Day

Proposed default school-calendar lead-time (assumption — confirm): 7 days before any break/holiday for logistics, day-of for awareness; 30 days before semester start for back-to-school prep.

### 1.14 One-time future dated anchors (2026)
| Date | Item | Context |
|---|---|---|
| 2026-05-26 | Seane's 12th birthday | School and Parenting + Family |
| 2026-06-09 to 2026-06-29 | New York trip window | Family + Travel |
| 2026-06-13 5pm ET / 12pm HST | Reunion (name TBD) | Family |
| 2026-06-15 | Diane "Mom" 80th birthday (in NY) | Family |
| 2026-06-24 | Diane & Bob 54th wedding anniversary (Bob deceased — day-of only) | Family |
| 2026-06-24 | Evanescence concert — Seane's first concert | Family + Travel |
| TBD | Jessie/Brian visit (within NY trip) | Family |
| TBD | Riverhead Aquarium | Family + Travel |

### 1.15 Domain renewals
21 domains, all auto-renew ON, status active as of 2026-05-19. Source: registrar screenshots, 2026-05-19. Confidence: confirmed for state on that date.

| Tier | Domains | Default lead-time |
|---|---|---|
| A — Operationally critical | `morelen.net` (2027-01-25), `darkstartechnology.net` (2026-09-16), `projectefed.com` (2026-10-19) | 30/14/3/day-of |
| B — Identity reservations | `seanhansell.com` (2027-03-08), `seanehansell.com` (2027-04-08), `mariahansell.com` (2027-04-08) | 14/day-of |
| C — Needs classification | `bigislandjeep.club` (2026-09-12), `bigislandjeepclub.com` (2026-09-06), `bigislandjeepers.com` (2027-01-04), `darkstar.games` (2027-05-29), `darkstarknights.com` (2026-09-14) | per-domain after classification |
| D — Likely historical (suppress) | `sew-wrestling.com` (2026-10-15), `thepwf.co.uk` (2026-10-14), `sovereigninnovations.com` (2026-09-08), `sovinn.com` (2026-10-19), `djctemple.com` (2027-02-12), `djctemple.co.uk` (2026-09-16), `eronautic.com` (2027-02-03), `fanwaypoint.com` (2027-02-03), `paximperius.com` (2026-09-11), `salvecraft.com` (2026-09-18) | suppress; surface on renewal failure only |

### 1.16 Projects
**MTS active (inferred from Jira project spaces; confirmation needed):**
- Holy See Mission IT Stabilization (HSM)
- Holy See Mission Talos Onboarding (HOLY)
- PSP Okta App Integration Workstream (PSP)
- Managed Apple Account Deployment Program (PSP + MAID; customer lanes TBD)
- Talos Fleet Management Platform Reliability (TFM) — triage

**Non-MTS active:**
- LifeOps / COO System Build (Personal Operations)
- Summer 2026 New York Trip Planning (Family + Travel)
- Evanescence / Seane First-Concert Support (Family + Travel)
- 2026–2027 School Year Planning (School and Parenting) — defer until sourced
- Home Assistant / Smart-Home Architecture (Home) — triage, needs activity confirmation
- Project eFed Platform (Personal Operations) — triage, needs activity confirmation
- The Hill (Home) — clear and cover ~4,200 sq ft overgrown backyard hill
- Halloween House Decoration (Home) — recurring seasonal
- Christmas House Decoration (Home) — recurring seasonal

**Dormant but important:**
- Digital Survivorship / Maria Emergency Access Plan
- Darkstar Technology Business Setup
- Darkstar Technology Website / Public Positioning
- Morelen Account / Domain Migration Planning (Workspace → iCloud custom domains; not ABM)
- Home Infrastructure Documentation / Household Technology Map
- Health / Cardio / Flexibility Improvement Plan

**Excluded (operations, not projects):** family logistics; general parenting; general school monitoring; household maintenance review; family finance review (recurring loop); D&D attendance; general learning/reading; current 2025–2026 school-year wrap-up.

### 1.17 Auditor rules
- Strictness priorities (ranked): obligation invention; sensitive-context leakage; stale context promoted as current; missed urgency; external action without approval path; wrong identity/account routing; suppressed/deferred items surfacing without documented trigger.
- Block publication only on the explicit list in Batch 9 §1 (sensitive content in wrong context; MTS confidential outside MTS; proposal under wrong identity; Tier 0 mishandled; deletion without explicit approval; inferred/stale/source-missing item presented as confirmed; question/triage/decision presented as resolved; school item surfaced as confirmed without source; briefing would cause external action under wrong context/tier).
- Otherwise flag-and-publish with appropriate label: TRIAGE / UNKNOWN / NEEDS SOURCE / NEEDS DECISION / STALE / BLOCKED / WAITING / AUDIT WARNING.
- Standing checklist per Batch 9 §2.
- Aggressive safe-to-ignore enforcement per Batch 9 §3.
- False-positive policy: strict but not noisy. First occurrence flag/log; known-OK suppresses repeats; never suppress repeats on Tier 0/1, identity, school, employer-confidential, or deletion findings.
- Reporting: counts in briefing + one-line summary per medium/high-severity finding; full report in log; blockers shown explicitly with reason and required action. Unresolved prior findings persist until acknowledged, fixed, expired, or marked known-OK.

---

## 2. Assumptions (need confirmation)

1. The "primary operating context" set in §1.4 (MTS Pro Services / Darkstar Technology / Personal Operations / Family / Home / School and Parenting) **extends** rather than replaces the existing `personal/work/school/household/public/unknown` set in [rules/compartmentalization.md](../rules/compartmentalization.md). Mapping proposed: MTS → `work`; Darkstar → new context type (proposed addition to the rule); Personal Operations / Family / Home → `personal`; School and Parenting → `school`; `household` retained as legacy/no-longer-used; `public` retained; `unknown` retained. This requires a rules/ change, which is itself approval-gated.
2. Family-context dates currently labeled "Personal" in user submissions (Maria's siblings, Magh family, etc.) will be normalized to `Family` in `context/dates.md`. Confirm or override.
3. Tier C domains (`bigislandjeep.*`, `darkstar.games`, `darkstarknights.com`) reclassified into Tier A/B or Tier D after user input.
4. Tier D domains default `suppress`; surface only on renewal failure or explicit review.
5. School-calendar lead-time: 7 days before break/holiday + day-of; 30 days before semester start.
6. "TRIAGE" as a surface state will be added as an extension to [rules/safe-to-ignore.md](../rules/safe-to-ignore.md) alongside `surface` / `defer` / `suppress`, OR mapped to `surface` with a `triage` tag.
7. The Hill is one Home project, not split.
8. LifeOps daily briefing publishes daily, not only on workdays; "nothing urgent" days produce a brief affirmative briefing.
9. The auditor blocks publication only on the explicit Batch 9 §1 list; all other findings flag-but-publish.
10. Seane's birthday is filed under `School and Parenting` as primary context (per the rule "classify by primary operating context first") with `Family` secondary tag. Confirm or override (could be reversed).

---

## 3. Open questions

- Reunion 2026-06-13: which reunion (Hansell family / Puswald family / school / other)?
- Jessie/Brian NY visit dates within the 2026-06-09–29 window?
- Riverhead Aquarium date?
- Lily Rose Magh birthday?
- Laura Mills née Edwards birth year?
- Current 2025–2026 school-year end date — in scope or excluded?
- Institute Day specific date for Hawai‘i Island (per HIDOE PDF)?
- Tier C domain classification — active community / Darkstar-adjacent / hobby?
- Tier D domain confirmation — any still in use?
- MTS project follow-ups (from your Section 6):
  - HSM vs. HOLY: separate, or HOLY as a subproject of HSM?
  - Managed Apple Account: which customer lanes are active (MTS / PHS / Holy See / Calcium / ASTM / Thriven)?
  - TFM: strategic-risk stream or engineering backlog?
  - PSP Okta: Zoom only, or broader integration list?
  - Stale Jira cleanup: action item or out of scope?
- Non-MTS project confirmation:
  - Home Assistant — current activity level?
  - Project eFed — current activity level?
  - Darkstar Website — standalone or subproject of Darkstar Business Setup?
  - Health plan — does a bounded plan exist yet?
  - Home Infrastructure Documentation — standalone or under Home Assistant / Digital Survivorship?
- Deferred Batch 8 Q3: tax deadlines, vehicle registration/inspection, annual physical/dental, Darkstar business filings.
- Domain renewal failure detection — registrar mail to `sean@morelen.net`?
- Diane's preferred channel?

---

## 4. Phase 1 requirements

- Manual / sample inputs only; no external connectors
- Daily briefing workflow runs from `inputs/` and `state/`
- All factual claims declare `source` / `as_of` / `confidence`
- All state files declare `context`
- Acronyms expanded on first use per file
- Auditor runs in fresh context at end of every briefing
- All external-action drafts written to `proposals/` with required frontmatter; never executed
- One activity log per workflow run in `logs/`
- Repo-internal writes outside `context/`, `rules/`, `workflows/`, `CLAUDE.md`, `AGENTS.md`, `.gitignore` proceed under standing approval
- Compartmentalization enforced by frontmatter labels only; re-evaluation required before real data enters repo

---

## 5. Later-phase requirements

- Connector design and rollout: Calendar, Gmail, Jira, Todoist, Slack, Confluence, Atlassian Home, Ninety.io, Google Classroom, Infinite Campus, Remind, Kaiser, Apple Health, Reclaim.ai
- Per-context read-only access policy: Morelen feasible standing approval; MTS per-session or workflow approval; Seane school explicit + source handling
- Metadata-driven identity routing distinguishing physical mailbox, sender alias, execution identity, context, and canonical source
- Darkstar Workspace migration / dedicated business systems when activated
- Morelen Workspace → iCloud custom domains migration (not ABM)
- Emergency / survivorship access workflow for Maria with strong authentication, delay, verification steps; pre-authorized survivorship plan
- COO eventually replaces Reclaim.ai as scheduling intelligence
- Domain renewal monitoring and failure surfacing
- Compartmentalization re-evaluation before real data enters repo
- Stale-proposal policy: 7-day stale mark (unless deadline/dependency); 30-day archive as expired
- Auditor known-OK suppression for low-tier repeat findings; never suppress Tier 0/1, identity, school, employer-confidential, or deletion findings
- Future standing approvals (post Phase 1 reliability): Morelen no-invite calendar holds; narrow personal Todoist updates; MTS Jira ticket creation in specific queues; draft-only Gmail in personal mailboxes; messages to self as reminder

---

## 6. Non-goals

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

---

## 7. Approval boundaries

Covered in §1.9–§1.10. Anchor rule: default deny for external effect; standing approval only for low-risk repo-internal classification/metadata work; tiered ladder for everything else; restate-the-action confirmation for Tier 1; Tier 0 prohibited under normal flow; deletion always Tier 1.

Silence is never consent. Stale-proposal behavior per §5 (later-phase).

---

## 8. Account and domain boundaries

Covered in §1.4, §1.8, §1.11. Anchor rules:
- MTS identity for MTS only; never personal / family / home / school / Darkstar
- Darkstar items use Darkstar alias as sender (even when routed through Morelen); if alias unavailable, do not silently send as Morelen
- COO must never act as Seane even when access exists; access ≠ permission
- COO must never represent or act as Maria; Maria may be modeled as collaborator / owner / waiting-on / target / invitee
- Historical aliases / domains / identities must not be assumed current, canonical, or appropriate for action
- Ambiguous items → `unknown` context → `state/inbox/`. Do NOT default to Personal Operations.
- High-confidence routing signals: MTS systems/customers/coworkers → MTS; `darkstartechnology.net` or Darkstar service/business mentions → Darkstar; `k12.hi.us` / Classroom / Infinite Campus / Remind / Seane school items → School and Parenting; Maria / family events / coordination → Family; property / appliances / smart home / network / household vendors → Home; personal admin / individual appointments / renewals → Personal Operations.

---

## 9. Daily briefing expectations

- **Cadence:** daily; not workdays only.
- **Length:** real but not exhaustive; "nothing urgent" days stay brief.
- **Default priority order:**
  1. Time-sensitive today
  2. Cross-domain conflicts
  3. Blocked / waiting on me
  4. Decisions pending
  5. Waiting-on-others past expected window
  6. Open inbox items needing triage
  7. Upcoming items near enough to matter
- **Labels:** TODAY, BLOCKED, DECISION, WAITING, CONFLICT, UPCOMING, TRIAGE, NEEDS SOURCE, NEEDS DECISION, STALE, UNKNOWN, AUDIT WARNING.
- **Format:** merged top section for true urgents; per-context sections below only when needed; empty contexts omitted unless absence matters.
- Every item labeled with its context.
- `public` content omitted by default unless tied to an active concern (obligation, travel, weather/safety, school, household ops, work, explicitly tracked topic).
- Item IDs included by default to allow drill-down; file/source paths only on explicit request.
- **Audit section:** counts in briefing + one-liner per medium/high-severity finding + full audit report written to log; blockers shown explicitly with reason and required action; unresolved prior findings persist until resolved/acknowledged.

---

## 10. Safe-to-ignore categories

Suppress aggressively; surface only on documented trigger (real-world consequence, deadline, dependency, conflict, scheduled review, active commitment, or explicit request):
- Hobby / wish-list / someday-maybe items without explicit current commitment
- Early-stage business ideas (Darkstar) without active task / deadline / commitment / risk / scheduled review
- Recurring obligations handled by another person, automation, or external system
- Low-stakes admin past its useful window
- School items without source or explicit user-provided context
- Financial items without source / deadline / consequence / current review
- Stale project context not recently activated
- General health/productivity nudges without concrete plan / appointment / metric / commitment
- Public/news without active-context relevance
- General reminders that do not affect today or the next few days
- Recurring operations appearing as projects without bounded outcome
- Anything tagged Personal Operations that should be Unknown

Suppressed items shown as counts grouped by category.

---

## 11. Post-intake normalization / conflict-resolution pass

### Purpose

Before any proposal content is promoted into canonical files, the Chief Operating Officer (COO) must review the completed intake for contradictions, duplicated rules, overfit corrections created during the interview, misplaced concepts, and unresolved decisions.

### The pass must check for

- Contradictions between batches
- Duplicated rules expressed in multiple places
- Negative prompts or overfit corrections caused by the interview process
- Items placed in the wrong conceptual layer
- Conflicts between context, domain, project, people, dates, approval, source, and audit rules
- Stale assumptions carried in from memory or prior discussion
- Missing decisions needed before canonicalization
- Proposed rules that are stricter than intended and may prevent useful briefings
- Places where uncertainty should produce TRIAGE / NEEDS SOURCE / NEEDS DECISION rather than blocking output

### Resolution rules

- Mechanical conflicts may be corrected according to existing rules.
- Higher-safety classification wins for approval tier, identity, deletion, employer-confidential, school/child, and external-action conflicts.
- Ambiguous context defaults to Unknown.
- Ambiguous source status defaults to NEEDS SOURCE.
- Ambiguous project status defaults to TRIAGE, not active.
- Ambiguous surface state defaults to defer or triage, not surface.
- Value/meaning conflicts require explicit Chief Executive Officer (CEO) decision.
- The auditor may flag conflicts but must not silently rewrite canonical policy.
- COO must not treat unresolved questions as failures. They are preserved as decisions, triage items, or assumptions needing confirmation.

### Gate

No canonical files (`context/`, `rules/`, `workflows/`) may be written until this normalization pass is executed and the CEO approves the resulting normalization-pass proposal.

---

## On approval, the next step is the normalization pass — not transcription

Flow:
1. CEO approves this intake summary (with this change).
2. COO executes the normalization pass and writes its findings/resolutions to a separate proposal: `proposals/2026-05-19-bootstrap-normalization-pass.md`.
3. CEO reviews and approves the normalization-pass proposal.
4. Only then does COO write to `context/`, propose `rules/` extensions, and update `workflows/`.

Planned writes, deferred until step 4:

1. `context/identity.md` — §1.1, §1.2, §1.3
2. `context/domains.md` — §1.4, §1.5, §1.6
3. `context/boundaries.md` — §1.7, §1.8, §1.9, §1.10, §6, §7, §8, §1.17
4. `context/people.md` — §1.11
5. `context/dates.md` — §1.12, §1.13, §1.14, §1.15
6. `state/projects/` — one file per active and dormant project in §1.16
7. Proposed rules change (separate approval): extend [rules/compartmentalization.md](../rules/compartmentalization.md) to add the primary operating contexts in §1.4 and `business` as a context type; extend [rules/safe-to-ignore.md](../rules/safe-to-ignore.md) with TRIAGE handling and the labels in §9; document auditor charter from §1.17 in a new `rules/auditor-charter.md`.
8. Briefing workflow update — [workflows/daily-briefing.md](../workflows/daily-briefing.md) defaults from §9.

Each file will declare `source: bootstrap-interview` with date `2026-05-19`. Items marked `confidence: assumed` listed under each file's "Open questions" section. Anything in §3 above appears as an Open question in the relevant file until resolved.
