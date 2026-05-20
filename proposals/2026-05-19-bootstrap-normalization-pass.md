---
type: proposal
context: personal
action: resolve contradictions, duplicated rules, layer-misplacements, and stricter-than-intended rules in the bootstrap intake summary before transcribing canonical files
target: repository — proposed changes to context/, rules/, workflows/ structures
source: bootstrap intake summary 2026-05-19, normalization pass on 2026-05-19
as_of: 2026-05-19
confidence: confirmed for mechanical findings; needs-decision where flagged
requires_approval: true
depends_on: proposals/2026-05-19-bootstrap-intake-summary.md (approved with changes)
---

# Bootstrap Normalization Pass — 2026-05-19

Executes §11 of [the intake summary](2026-05-19-bootstrap-intake-summary.md). No canonical file is written until the Chief Executive Officer (CEO) approves this pass.

Findings are grouped by category. Each finding has:
- **Type** — Conflict / Duplication / Layer / Overfit / Stale / Decision-needed
- **Disposition** — what the Chief Operating Officer (COO) proposes
- **Resolution rule applied** — which rule from §11 governs

Conventions: "Mechanical" disposition means COO will apply the resolution rule without further CEO input. "Needs decision" means a value/meaning conflict that requires the CEO to choose before canonicalization. "Defer" means the item remains as an Open question and does not block canonicalization.

---

## Group A — Compartmentalization / context model

### A1. Primary operating contexts vs. `rules/compartmentalization.md` enum
- **Type:** Conflict (layer mismatch).
- **Detail:** [rules/compartmentalization.md](../rules/compartmentalization.md) defines the allowed `context:` values as exactly `personal / work / school / household / public / unknown`. §1.4 introduces six primary operating contexts (MTS Pro Services / Darkstar Technology / Personal Operations / Family / Home / School and Parenting), some of which do not map cleanly onto the enum.
- **Disposition (needs decision):** Two viable models.
  - **(a) Replace the enum.** Update the rule's allowed values to the six primary operating contexts plus `unknown`. Cleaner; matches user vocabulary; loses `household` and `public` as distinct values.
  - **(b) Layer the enum.** Keep `context:` as the existing enum and add a new required field `primary_operating_context:` for the six-value set. More verbose but preserves rule-compatibility.
  - **COO recommendation:** (a). Rationale: the user's model is more specific and the rule's `personal/work/school/household/public` set is mostly subsumed (`household` ≈ `Home`; `public` may be retained as a seventh value). User uses these names operationally; the enum is from initial scaffold and not yet load-bearing.
- **Resolution rule applied:** Value/meaning conflict — explicit CEO decision required.

### A2. `business` as a context type
- **Type:** Conflict.
- **Detail:** §1.4 lists Darkstar Technology with context type `business`. Not in the current enum.
- **Disposition:** Adopted under either A1(a) or A1(b). If (a): `business` becomes an allowed value. If (b): `business` becomes an allowed `primary_operating_context` but `context:` for Darkstar items is `personal` (since Sean owns it as a sole-prop side venture). Resolves with A1.
- **Resolution rule applied:** Higher-safety wins — Darkstar must never blend with MTS regardless of model choice, so the keep-separate guarantee is preserved either way.

### A3. School and Parenting "context type: Seane"
- **Type:** Overfit / layer.
- **Detail:** §1.4 lists "context type: Seane" for School and Parenting. A person is not a context type.
- **Disposition (mechanical):** Map context type to `school` (under model A1(a) or A1(b)) with Seane as the subject. Files declare `subject: seane` as metadata where relevant, not as the context value.
- **Resolution rule applied:** Mechanical correction.

### A4. `household` (rule) vs. `Home` (intake)
- **Type:** Duplication / naming.
- **Detail:** Existing rule uses `household`; intake uses `Home` for the same conceptual area (property, smart home, network, household infra).
- **Disposition (mechanical):** Adopt `Home` as the canonical name. `household` is retired. (Note for A1: this is part of the enum replacement.)
- **Resolution rule applied:** Mechanical correction.

### A5. `public` context
- **Type:** Decision-needed.
- **Detail:** Existing rule has `public`. §1.4 does not. §9 says public/news content is omitted by default unless tied to an active concern.
- **Disposition (needs decision):** Retain `public` as a seventh primary operating context, used only for genuinely external public-facing material (e.g., publicly-posted Darkstar marketing, civic items, weather/safety affecting active obligations). Default surface: suppress.
- **Resolution rule applied:** Ambiguous surface state defaults to defer/triage, not surface — adopted as `suppress` per intake §10.

### A6. Personal Operations vs. `personal` ambiguity
- **Type:** Layer.
- **Detail:** Multiple intake items (e.g., Sean's birthday) are labeled "Personal" in user submissions. "Personal Operations" is a primary operating context but "Personal" is colloquial.
- **Disposition (mechanical):** All "Personal" labels normalize to `Personal Operations` unless the item is clearly Family / Home / Health-tagged-Personal-Operations.
- **Resolution rule applied:** Mechanical correction.

---

## Group B — Surface state model

### B1. Surface-state vocabulary explosion
- **Type:** Conflict / overfit.
- **Detail:** [rules/safe-to-ignore.md](../rules/safe-to-ignore.md) defines three surface states: `surface / defer / suppress`. The intake uses: `surface`, `surface-when-actionable`, `surface-with-source`, `defer`, `defer-unless-scheduled-or-relevant`, `defer-unless-deadline-or-review`, `suppress`, `suppress-unless-scheduled-or-activated`, `surface when active`, `triage`.
- **Disposition (mechanical):** Collapse to **three canonical states** + **trigger conditions**. The compound forms are not new states; they are existing states with documented surfacing triggers. Proposed normalization:
  - `surface` — always considered for default briefing
  - `defer` — tracked, suppressed by default, surfaces on declared trigger (date, dependency, milestone, review-window, activation)
  - `suppress` — counts-only; surfaces only on explicit user request or category-level threshold event
  - Trigger conditions are written as `surface_triggers:` frontmatter on the item or context. Example: a Darkstar item is `defer` with `surface_triggers: ["quarterly review", "concrete prospect", "deadline", "business-risk issue"]`.
- **Effect:** [rules/safe-to-ignore.md](../rules/safe-to-ignore.md) extended with the `surface_triggers:` field; surface state names stay as the existing three.
- **Resolution rule applied:** Duplicated rule expressed in multiple places — consolidated. Stricter-than-intended rule (state proliferation) — relaxed back to the existing three with explicit trigger metadata.

### B2. TRIAGE as a surface state
- **Type:** Decision-needed.
- **Detail:** Intake §11 list and §9 label set both include TRIAGE. §1.16 uses "Triage" as a surface state for multiple projects (Talos Fleet Management, Home Assistant, Project eFed, etc.).
- **Disposition (needs decision):** Two options.
  - **(a) TRIAGE is a label, not a state.** Surface state remains `surface/defer/suppress`. An item can be `surface` AND have label `TRIAGE` (it appears in the briefing tagged as needing triage). Per resolution rule "ambiguous surface state defaults to defer or triage, not surface," "triage" here means: show it labeled TRIAGE rather than suppress it.
  - **(b) TRIAGE is a fourth surface state.** Items in `triage` state surface in a dedicated triage section, not under normal surface.
  - **COO recommendation:** (a). Rationale: it composes cleanly with the existing three states; the label set already covers it; no new rule needed beyond the label registry.
- **Resolution rule applied:** Value/meaning conflict — explicit CEO decision required.

### B3. Briefing label set definition
- **Type:** Missing rule.
- **Detail:** §9 introduces labels TODAY, BLOCKED, DECISION, WAITING, CONFLICT, UPCOMING, TRIAGE, NEEDS SOURCE, NEEDS DECISION, STALE, UNKNOWN, AUDIT WARNING. No existing rule defines the label set, allowed combinations, or severity.
- **Disposition (mechanical):** Add a labels registry to [workflows/daily-briefing.md](../workflows/daily-briefing.md) (or a new `rules/briefing-labels.md`). Document each label with definition, when it applies, and which priority section it groups under.
- **Resolution rule applied:** Mechanical addition.

---

## Group C — Approval & identity

### C1. Tier 3 actions "not approved by default in Phase 1" + no connectors
- **Type:** Duplication / phase note.
- **Detail:** §1.9 Tier 3 examples (no-invite Morelen calendar holds, personal Todoist updates, drafts in personal mailbox, messages to self) are not approved by default in Phase 1; Phase 1 also has no connectors. Tier 3 is effectively unreachable until connectors arrive.
- **Disposition (mechanical):** Document this explicitly in `context/boundaries.md`: "Tier 3 actions exist in policy but are operationally inert in Phase 1 — no connector exists that could perform them. Tier 3 standing approvals will be reconsidered post-connector."
- **Resolution rule applied:** Mechanical clarification.

### C2. Darkstar alias send-as constraint
- **Type:** Overfit risk.
- **Detail:** §1.8 says external-facing Darkstar must appear as Darkstar; if alias unavailable, "do not silently send as Morelen." Phase 1 has no connectors, so this is fine. Future connectors must enforce the constraint.
- **Disposition (mechanical):** Document as a connector requirement in §5 later-phase requirements. No Phase 1 effect.
- **Resolution rule applied:** Higher-safety wins — preserve the prohibition; document the constraint for connector design.

### C3. Standing approval scope vs. deletion
- **Type:** Conflict (latent).
- **Detail:** §1.10 standing approvals include "archive stale proposals only if the archive rule is explicit and logged." §1.9 Tier 1 says deletion always requires explicit approval. Archive vs. delete must be unambiguous.
- **Disposition (mechanical):** Add to `context/boundaries.md`: archiving means moving the file under `state/archive/` with a metadata link to its origin. Archive ≠ delete. Standing approval covers archive only when (a) explicit archive rule applies, (b) origin metadata is preserved, (c) action is logged. Any deletion remains Tier 1 explicit approval.
- **Resolution rule applied:** Higher-safety wins.

### C4. "Repo-internal writes outside `context/`, `rules/`, `workflows/`, `CLAUDE.md`, `AGENTS.md`, `.gitignore`" — is `state/manual/` in or out?
- **Type:** Layer / mechanical.
- **Detail:** [AGENTS.md](../AGENTS.md) introduces `state/manual/` as a holding bucket. §1.10 covers it implicitly under "Add manual / source-gap entries." Mechanically consistent but should be made explicit.
- **Disposition (mechanical):** Confirm in `context/boundaries.md` that `state/manual/` writes are standing-approved.
- **Resolution rule applied:** Mechanical clarification.

---

## Group D — Source confidence & freshness

### D1. MTS project list provenance
- **Type:** Stale / inferred-as-confirmed risk.
- **Detail:** §1.16 MTS Active list was inferred from Jira project spaces (HSM, HOLY, PSP, MAID, TFM). User flagged this in the original submission.
- **Disposition (mechanical):** Every MTS project state file under `state/projects/` declares `confidence: inferred` and `source: Jira project space inspection 2026-05-19`. None are surfaced as active until CEO confirms. Default surface state for each: `defer` with `surface_triggers: ["CEO confirmation as active"]`.
- **Resolution rule applied:** Ambiguous project status defaults to TRIAGE, not active.

### D2. Domain renewal Tier classifications
- **Type:** Decision-needed.
- **Detail:** §1.15 Tier C (5 domains) and Tier D (10 domains) are tentative.
- **Disposition (defer):** Created as `state/projects/` entries? No — they are date anchors, not projects. They go in `context/dates.md`. Tier C entries marked `confidence: assumed` with `triage_required: true`. Tier D entries marked `confidence: assumed` with `surface_state: suppress` and `historical_likely: true`. CEO resolves at next review.
- **Resolution rule applied:** Ambiguous source status defaults to NEEDS SOURCE — preserved as an open decision.

### D3. Lily Rose Magh birthday, Laura Mills birth year
- **Type:** Stale / incomplete data.
- **Disposition (mechanical):** Both entries marked `confidence: assumed` with `NEEDS SOURCE`. Lead-time policy still applies once date is known.
- **Resolution rule applied:** Mechanical preservation.

### D4. Reunion 2026-06-13 name
- **Type:** Decision-needed.
- **Disposition (defer):** Entry created with `NEEDS DECISION` label and a placeholder slug `reunion-2026-06-13`. Does not block canonicalization.
- **Resolution rule applied:** Mechanical preservation; defer for CEO resolution.

### D5. Default school-calendar lead-time
- **Type:** Assumption proposed without explicit CEO confirmation.
- **Disposition (needs decision):** §1.13 includes a proposed lead-time (7 days before break/holiday + day-of; 30 days before semester start). CEO must approve or override.
- **Resolution rule applied:** Value/meaning conflict — explicit CEO decision required.

---

## Group E — Project model

### E1. Seasonal Home projects vs. recurring dates duplication
- **Type:** Duplication.
- **Detail:** Halloween / Christmas decoration appear both as `state/projects/` (§1.16) and as recurring dates with completion targets in `context/dates.md` (§1.12). Both representations are useful (project tracking + calendar surface).
- **Disposition (mechanical):** Keep both, but link. The project file declares `recurring_completion_target:` (09-30 / 11-25) and references the date entry; the date entry declares `linked_project:` (filename). Surface state for the project: `defer` during off-season with `surface_triggers: ["60 days before completion target", "45 days", "30 days", "day-of holiday"]`.
- **Resolution rule applied:** Duplication consolidated via linking.

### E2. "Triage" project surface state
- **Type:** Conflict (resolved by B2).
- **Detail:** Projects "Talos Fleet Management Platform Reliability," "Home Assistant," "Project eFed" have surface state "triage."
- **Disposition (mechanical, contingent on B2(a)):** Treat as `surface` + label `TRIAGE`. Project file declares `surface_state: surface` and `labels: ["TRIAGE"]` and `triage_question:` (one-line description of what needs deciding).
- **Resolution rule applied:** Ambiguous project status defaults to TRIAGE.

### E3. The Hill as one project vs. split
- **Type:** Decision-needed (assumption #7).
- **Disposition (defer):** Default to one project. If clearing and covering become independently scheduled, split later. Does not block canonicalization.
- **Resolution rule applied:** Mechanical preservation of the simpler model.

### E4. Project eFed and Home Assistant — active or dormant?
- **Type:** Decision-needed.
- **Detail:** Both flagged Triage in §1.16; both also listed under "Waiting / blocked" in the user's Batch 7 submission.
- **Disposition (mechanical, contingent on B2(a)):** Treat as `surface` + label `TRIAGE` + `triage_question: "Confirm current activity level"`. CEO resolves at next briefing.
- **Resolution rule applied:** Ambiguous project status defaults to TRIAGE.

### E5. Seane's birthday primary context
- **Type:** Decision-needed (assumption #10).
- **Detail:** Could be primary School and Parenting (Seane lives in that context) or primary Family (event nature).
- **Disposition (needs decision):** COO recommendation — primary `Family` with secondary tag `School and Parenting`. Rationale: it's a family celebratory event, not a school-system obligation. CEO confirms or overrides.
- **Resolution rule applied:** Value/meaning conflict — explicit CEO decision required.

---

## Group F — People model

### F1. Family-context labels in user submission
- **Type:** Layer / overfit (assumption #2).
- **Detail:** Submitted labels mix "Personal" and "Family" for relatives. Maria's siblings labeled "Personal"; Magh family labeled "Personal"; Sean's birthday labeled "Personal."
- **Disposition (mechanical):** Per the primary-context rule "classify by primary operating context first":
  - Sean's birthday → `Personal Operations` (it's the CEO's own date, not a Family event he's organizing for others).
  - All relatives (Maria's siblings, Hansell siblings, Magh family, in-laws) → `Family` primary, with `Personal Operations` secondary tag if useful.
- **Resolution rule applied:** Mechanical correction.

### F2. Diane's preferred channel
- **Type:** Missing data.
- **Disposition (mechanical):** Entry created with `preferred_channel: TBD` and `NEEDS DECISION` flag.
- **Resolution rule applied:** Mechanical preservation.

### F3. MTS Project Management / Account Management / Support team entries
- **Type:** Layer.
- **Detail:** §1.11 lists groups (PM team, AM team, Support team) alongside individuals. Groups don't map cleanly to single-person fields.
- **Disposition (mechanical):** Represent groups in `context/people.md` under a `groups:` section, separate from `individuals:`. Each group has routing notes; individuals have communication preferences.
- **Resolution rule applied:** Mechanical structuring.

---

## Group G — Briefing & auditor

### G1. Briefing publishes daily (was assumption #8)
- **Type:** Stale assumption (already confirmed in Batch 2).
- **Disposition (mechanical):** Move from §2 Assumptions to §1 Confirmed facts. User confirmed: "One briefing per day, not only on workdays."
- **Resolution rule applied:** Mechanical correction.

### G2. Auditor blocks publication only on explicit list (was assumption #9)
- **Type:** Stale assumption (already confirmed in Batch 9 §1).
- **Disposition (mechanical):** Move from §2 to §1.
- **Resolution rule applied:** Mechanical correction.

### G3. Auditor cannot rewrite canonical policy
- **Type:** Duplication (already present in Batch 9 §4 and re-stated in §11 resolution rules).
- **Disposition (mechanical):** Consolidate in the new `rules/auditor-charter.md`. Reference from intake summary §1.17 instead of restating.
- **Resolution rule applied:** Duplication consolidated.

### G4. Priority order item #4 "Decisions pending" + auditor rule "block if briefing presents a question as resolved"
- **Type:** Latent conflict.
- **Detail:** Briefing surfaces decisions; auditor blocks if a decision is presented as resolved. These are consistent only if the briefing format consistently labels decisions with NEEDS DECISION.
- **Disposition (mechanical):** Codify in [workflows/daily-briefing.md](../workflows/daily-briefing.md): every priority-#4 item must carry the NEEDS DECISION label; auditor verifies.
- **Resolution rule applied:** Mechanical codification.

### G5. "Show stale items as stale" + "Auditor flags inferred-as-confirmed"
- **Type:** Consistent; just needs explicit format.
- **Disposition (mechanical):** Codify: every briefing item declares confidence inline (e.g., `[CONFIRMED]`, `[INFERRED]`, `[ASSUMED]`, `[STALE]`). Auditor verifies against state file metadata.
- **Resolution rule applied:** Mechanical codification.

---

## Group H — Strictness vs. usefulness check

### H1. "Never speculate about my employer" + COO uses MTS Jira inference for project list
- **Type:** Apparent overfit, resolved.
- **Detail:** Batch 1: never speculate about employer without source. §1.16 derives MTS project list from Jira inference.
- **Disposition (mechanical):** No conflict — Jira is a CEO-controlled employer source, so reading it and citing it is sourced inference, not speculation. Each MTS project file declares `source: Jira project space inspection 2026-05-19` and `confidence: inferred`. Auditor verifies the source link.
- **Resolution rule applied:** No conflict; mechanical clarification.

### H2. "Never make assumptions about my daughter's school without a source" + 2026-27 school calendar
- **Type:** Apparent overfit, resolved.
- **Detail:** Batch 1 forbids school inference without source. §1.13 captures the HIDOE 2026-27 calendar from a PDF the CEO supplied.
- **Disposition (mechanical):** No conflict — the PDF is the source. Each date entry declares `source: HIDOE 2026-2027 Official School Calendar, approved 2023-06-01, amended 2026-03-30`. Items not in the PDF (e.g., Hawai‘i Island Institute Day specific date) remain NEEDS SOURCE.
- **Resolution rule applied:** No conflict.

### H3. "Never nag about deferred items" + "Surface a defer item on documented trigger"
- **Type:** No conflict; needs explicit definition of "trigger."
- **Disposition (mechanical):** Codify in [rules/safe-to-ignore.md](../rules/safe-to-ignore.md) extension: a defer item surfaces only when a `surface_triggers:` entry matches the current state (date reached, dependency satisfied, milestone reached, scheduled review window, CEO request). Otherwise it stays deferred and appears only as a count.
- **Resolution rule applied:** Mechanical codification; no nagging by construction.

### H4. "Auditor must not block useful briefings" + "Auditor blocks on Tier 0 mishandled"
- **Type:** No conflict; consistent.
- **Disposition (mechanical):** Document in `rules/auditor-charter.md`: block list is explicit and bounded; everything else flags-but-publishes with label.
- **Resolution rule applied:** Mechanical codification.

---

## Group I — Stale or carried-in items

### I1. Bootstrap interview file says "do not execute in current session"
- **Type:** Stale assumption in [workflows/bootstrap-interview.md](../workflows/bootstrap-interview.md).
- **Detail:** That file's status frontmatter says `SPEC — do not execute in the current session`. We did execute it. The file's pre-conditions (CEO explicit request, scaffold in place) were met. The "do not execute" flag is no longer accurate.
- **Disposition (mechanical):** As part of step 4 transcription, update [workflows/bootstrap-interview.md](../workflows/bootstrap-interview.md) frontmatter to `status: executed 2026-05-19; spec retained for future re-runs`. Add a reference to this normalization pass and the intake summary.
- **Resolution rule applied:** Mechanical correction.

### I2. AGENTS.md "Future action items" — bootstrap interview
- **Type:** Stale.
- **Disposition (mechanical):** [AGENTS.md](../AGENTS.md) line 57 says "A later session will run [workflows/bootstrap-interview.md] and write durable user context into `context/`." This is now in progress. After step 4 completes, update AGENTS.md to reflect completion.
- **Resolution rule applied:** Mechanical correction.

### I3. Compartmentalization re-evaluation
- **Type:** Open; not yet executable.
- **Detail:** [AGENTS.md](../AGENTS.md) and [rules/compartmentalization.md](../rules/compartmentalization.md) both flag that compartmentalization must be re-evaluated before real personal/work/school data enters the repo. The intake captures structural metadata (names, dates, identities) but no MTS confidential content, no medical content, no financial detail.
- **Disposition (defer):** Re-evaluation remains a Phase 1 → Phase 2 gate. Canonicalization of the intake summary itself does not constitute "real personal/work/school data" beyond structural metadata. CEO confirms this characterization, or flags items that should be redacted.
- **Resolution rule applied:** Value/meaning conflict — explicit CEO acknowledgment requested.

---

## Group K — Context redistribution review (added 2026-05-19)

CEO amended §1.4 of the intake summary to **seven primary operating contexts**: MTS Pro Services, Darkstar Technology, Family, Home, School, Parenting, Personal Operations. School and Parenting are now separate. Personal Operations is narrowed (Sean-specific individual obligations only, not catch-all). This requires walking every classified item and reclassifying.

Routing rule applied: do not route to Personal Operations merely because Sean is the actor or the source is Sean-provided. Route by the life area that owns the obligation or next action.

### K1. Items currently `Personal Operations` — reclassified

| Item | Original | Reclassified to | Rationale |
|---|---|---|---|
| Sean's birthday 1983-10-17 | Personal Operations | Personal Operations (kept) | Sean's own personal date; obligation is Sean-individual |
| Kenneth "Ken" Taber — Thursday D&D host | Personal Operations | Personal Operations (kept) | Personal social activity owned by Sean individually |
| LifeOps / COO System Build (project) | Personal Operations | Personal Operations (kept) | Personal system Sean operates; obligation is Sean-individual |
| Project eFed Platform (project) | Personal Operations | Personal Operations (kept) | Personal/individual project |
| Health / Cardio / Flexibility Improvement Plan (project) | Personal Operations + Health | Personal Operations + Health (kept) | Sean's own health |
| Morelen Account / Domain Migration Planning (project) | Personal Operations / Family | **Family** | Affects shared family identity infra (Maria's account, family domain); life area owning the obligation is Family. Sean is the actor but not the owner. Secondary tag: Personal Operations |
| Personal Operations weekly Saturday review cadence | Personal Operations | Personal Operations (kept) | Cadence applies to Sean's individual obligations |

### K2. Items currently `School and Parenting` — split

| Item | Reclassified to | Rationale |
|---|---|---|
| 2026-2027 School Year Planning (project) | **School** | School-system obligation |
| All HIDOE 2026-27 calendar dates (§1.13) | **School** | School-system dates |
| Google Classroom, Infinite Campus, Remind (source systems) | **School** | School platforms |
| `3712000032@k12.hi.us` school account | **School** | School-system identity |
| Seane (person, primary context) | **Parenting** (recommended) | Seane is the child being parented; primary context is the relationship. Secondary tags: Family, School |
| 2026-2027 School Year Planning review cadence (weekly Sun, monthly during break) | **School** | School cadence |
| Year-round weekly parenting review | **Parenting** | Parenting cadence |

### K3. Items currently `Family` — confirmed or reclassified

| Item | Original | Reclassified to | Rationale |
|---|---|---|---|
| Maria Hansell (person) | Family | Family (kept) | Spouse; family-system primary |
| Diane "Mom" Hansell (person) | Family | Family (kept) | Extended family |
| Brian & Jessie Magh, Ethan Magh, Lily Rose Magh (persons) | Family | Family (kept) | Godparents and their children — family system |
| Maria's siblings (John, Christina), in-laws (Matthew) | Family | Family (kept) | Extended family |
| Sean's siblings (Chris, Brett, Jason) | Family | Family (kept) | Extended family |
| Birth mother (Laura), parents-in-law (Frank/Irene) | Family | Family (kept) | Extended family |
| Wedding anniversaries (Sean & Maria, parents, in-laws) | Family | Family (kept) | Family events |
| Summer 2026 NY Trip Planning (project) | Family + Travel | Family + Travel (kept) | Family travel |
| Reunion 2026-06-13 | Family | Family (kept) | Family event |
| Diane's 80th birthday 2026-06-15 | Family | Family (kept) | Family celebration |
| Seane's birthday 2026-05-26 (event-this-year) | Family (per E5) | **Parenting** primary + Family secondary (revised recommendation) | Now that Parenting is a distinct context, the celebration of the child is more accurately Parenting; family attendance is a Family tag. Supersedes E5. |
| Evanescence concert 2026-06-24 (Seane's first concert) | Family + Travel | **Parenting** + Travel + Family (revised) | Project framing was already "Seane First-Concert Support" — child-facing care/comfort/development. Parenting primary; Family + Travel secondary |
| Evanescence / Seane First-Concert Support (project) | Family + Travel | **Parenting** + Travel + Family | Same rationale |
| Digital Survivorship / Maria Emergency Access Plan (project) | Family / Personal Operations | **Family** | Affects family continuity; obligation owner is Family |

### K4. Items currently `Home` — confirmed

| Item | Status | Rationale |
|---|---|---|
| Home Assistant / Smart-Home Architecture (project) | Home (kept) | Household infrastructure |
| The Hill (project) | Home (kept) | Property |
| Halloween House Decoration (project + dates) | Home (kept) | Property/household project |
| Christmas House Decoration (project + dates) | Home (kept) | Property/household project |
| Home Infrastructure Documentation / Household Technology Map (project) | Home (kept) | Household infrastructure |

### K5. Items currently `MTS Pro Services` and `Darkstar Technology` — unchanged

All MTS project entries (HSM, HOLY, PSP, MAID, TFM) and Darkstar entries (Business Setup, Website / Public Positioning) keep their primary context. No redistribution.

Sean's MTS work anniversary 2007-03-19 — kept under MTS Pro Services (already correct).

### K6. Domain renewals (§1.15) — reclassified by life area

| Domain Tier | Items | Primary context |
|---|---|---|
| Tier A — Operationally critical | `morelen.net` | **Family** (shared family identity host) |
| Tier A — Operationally critical | `darkstartechnology.net` | **Darkstar Technology** |
| Tier A — Operationally critical | `projectefed.com` | **Personal Operations** (Project eFed is Sean's personal project) |
| Tier B — Identity reservations | `seanhansell.com` | **Personal Operations** (Sean's name) |
| Tier B — Identity reservations | `seanehansell.com` | **Parenting** (Seane's name reservation — child-facing logistics) |
| Tier B — Identity reservations | `mariahansell.com` | **Family** (Maria's name; family identity) |
| Tier C — Needs classification | `bigislandjeep.*`, `darkstar.games`, `darkstarknights.com` | TBD per CEO |
| Tier D — Likely historical | All 10 | **Personal Operations** with `historical_likely: true` and `surface_state: suppress` (Sean's own historical aliases — individual obligation) |

### K7. People / groups — confirmed

| Item | Context | Rationale |
|---|---|---|
| Maria | Family | Spouse |
| Seane | Parenting (primary) + School + Family (secondary) | Child being parented; school subject; family member |
| Diane "Mom" | Family | Extended family |
| Brian & Jessie Magh | Family | Godparents — family system |
| Ken Taber | Personal Operations | Personal D&D host |
| All MTS individuals/groups | MTS Pro Services | Unchanged |

### K8. Source systems — reclassified

| System | Primary context |
|---|---|
| Morelen Workspace, `sean@morelen.net` | **Family** (shared family identity host) — was "Personal/Family/Home/Darkstar catch-all"; primary becomes Family. Used as ingress for multiple contexts but owned by Family. |
| `maria@morelen.net` | Family |
| `sean@mtsproservices.com` + MTS Google Workspace | MTS Pro Services (unchanged) |
| `sean@darkstartechnology.net` (alias) | Darkstar Technology (unchanged) |
| `3712000032@k12.hi.us` + Google Classroom + Infinite Campus + Remind | School |
| Todoist (personal/home/family tasks) | Stays multi-context — items inside Todoist route to their owning life area, not "Personal Operations" |
| Kaiser Permanente, Apple Health | Personal Operations + Health (Sean's individual health systems) |
| Apple Notes, Google Drive (personal) | Personal Operations (Sean's individual knowledge stores), but documents within may route elsewhere |
| Kitchen whiteboard, physical calendar, iMessage (household) | Home + Family (shared household coordination) |
| Mac Admins Slack | Unchanged: ~60% MTS / 20% Darkstar / 20% Personal Operations |

### K9. Identity routing — confirmed

| Context | Execution identity | Change |
|---|---|---|
| MTS Pro Services | `sean@mtsproservices.com` | unchanged |
| Darkstar Technology | `sean@darkstartechnology.net` (alias via Morelen) | unchanged |
| Family | `sean@morelen.net`; iMessage as Sean Hansell | unchanged |
| Home | `sean@morelen.net` | unchanged |
| School | `sean@morelen.net` from parent; platform-constrained Classroom interactions inside Seane's school account | (was "School and Parenting") |
| Parenting | `sean@morelen.net`; iMessage; in-person | (new — split from School and Parenting) |
| Personal Operations | `sean@morelen.net` | unchanged |

### K10. Decisions raised by the redistribution

| ID | Item | COO recommendation | Type |
|---|---|---|---|
| K-a | Seane primary context | **Parenting** (with School + Family secondary) | Decision-needed |
| K-b | Seane's birthday primary context | **Parenting** primary + Family secondary (supersedes E5) | Decision-needed |
| K-c | Evanescence concert primary context | **Parenting** primary + Travel + Family secondary | Decision-needed |
| K-d | Evanescence project name | **"Seane First-Concert Support (Parenting)"** — explicit Parenting framing | Decision-needed |
| K-e | Morelen migration project primary | **Family** primary + Personal Operations secondary | Decision-needed |
| K-f | Morelen Workspace canonical primary | **Family** | Decision-needed |
| K-g | `seanehansell.com` primary | **Parenting** | Decision-needed |
| K-h | `mariahansell.com` primary | **Family** | Decision-needed |
| K-i | Tier D historical domains primary | **Personal Operations** with `historical_likely: true` and `surface_state: suppress` | Decision-needed |
| K-j | Whether to retain `public` as a context | (still A5) Recommended retain; if dropped, public/news items either go in `Personal Operations` or are not tracked. If retained, the context becomes the **eighth** primary operating context. | Decision-needed (was A5) |

### K11. Updates this redistribution requires elsewhere

- **A1 superseded:** The compartmentalization model is decided — replace the enum with the seven primary operating contexts (plus `unknown`, and `public` pending A5). Layered-enum option is dropped.
- **E5 superseded by K-b:** Seane's birthday no longer "Family vs. School and Parenting"; now Parenting primary + Family secondary.
- **F1 amended:** Sean's birthday → Personal Operations (kept). All relatives → Family. No change.
- **Cadence rule (§1.6):** School cadence and Parenting cadence are now two separate review cadences (already updated in intake summary).
- **`context/people.md`:** Seane's primary context becomes Parenting; her School and Family secondaries are tags.

---

## Group J (updated) — Decisions required from CEO before canonicalization

Items that block canonicalization unless explicitly decided. Defer items do not block.

| ID | Item | Recommendation | Status |
|---|---|---|---|
| ~~A1~~ | Compartmentalization model | Replace enum with seven primary operating contexts (+ `unknown`, + `public` pending A5) | **Resolved by Group K** |
| A5 | Retain `public` as a primary operating context | Retain (would make total 8) | Open |
| B2 | TRIAGE as label vs. fourth surface state | Label only | Open |
| D5 | School-calendar lead-time | 7 days + day-of (breaks); 30 days (semester start) | Open |
| ~~E5~~ | Seane's birthday primary context | Superseded by K-b | **Resolved by Group K** |
| I3 | Confirm intake metadata is not "real data" requiring compartmentalization re-evaluation | Confirm | Open |
| K-a | Seane primary context | Parenting (+ School, Family secondary) | Open |
| K-b | Seane's birthday primary | Parenting + Family | Open |
| K-c | Evanescence concert primary | Parenting + Travel + Family | Open |
| K-d | Evanescence project name change | "Seane First-Concert Support (Parenting)" | Open |
| K-e | Morelen migration project primary | Family + Personal Operations | Open |
| K-f | Morelen Workspace canonical primary | Family | Open |
| K-g | `seanehansell.com` primary | Parenting | Open |
| K-h | `mariahansell.com` primary | Family | Open |
| K-i | Tier D historical domains | Personal Operations, suppress | Open |

---

## Group L — CEO resolutions of open decisions (2026-05-19)

| ID | Decision |
|---|---|
| A5 | **Public is not a primary operating context.** Public is a separate external/source/relevance context (news, weather, civic, travel-safety, school/public-calendar). Does not surface by default. Total primary contexts remains **seven**. |
| B2 | **TRIAGE is a fourth canonical surface state.** Canonical surface states: `surface`, `defer`, `suppress`, `triage`. Triage items must declare a resolution path to surface / defer / suppress / archive / close, and must not be presented as normal obligations. |
| D5 | School-calendar lead-time accepted: 7 days + day-of for breaks/no-school days; 30 days for semester/year start or major transitions. Revisit after source connection. |
| I3 | Bootstrap metadata is **not** "real data" requiring compartmentalization re-evaluation. No redaction required at proposal stage unless an item would expose MTS confidential content outside MTS, credentials/secrets, or sensitive third-party information. |

### Routing rule (amended)

Adopted as the binding routing rule for all primary-context assignments:

> For any item that crosses Family, Parenting, School, Home, or Personal Operations, choose the primary context by the **nature of the obligation and owner of the next action**, not merely by who is affected.

Technical personal infrastructure belongs in **Personal Operations** even when it has Family / Home / Parenting impact. User-facing impact is captured by adding **related contexts**, not by changing the primary.

Seane is a **Family** member first; Parenting is a responsibility mode applied as related context, not the default container for every Seane-related item.

### Group K corrections applied

The CEO corrected several Group K recommendations. Final assignments:

| Item | COO recommendation (superseded) | CEO decision (final) |
|---|---|---|
| K-a Seane (person) primary | Parenting + School + Family | **Family** primary; Parenting and School as related |
| K-b Seane's birthday primary | Parenting + Family | **Family** primary; Parenting as related when child-specific planning/comfort/logistics; School only when school-system coordination involved |
| K-c Evanescence concert primary | Parenting + Travel + Family | **Family** primary; Parenting + Travel as related |
| K-d Evanescence project name | "Seane First-Concert Support (Parenting)" | Keep as Family-primary; project name unchanged from intake §1.16 ("Evanescence / Seane First-Concert Support"); Parenting + Travel are related contexts |
| K-e Morelen migration project | Family + Personal Operations | **Personal Operations** primary; Family as related (user-facing consent/coordination/household impact) |
| K-f Morelen Workspace canonical | Family | **Personal Operations** primary by default (technical/account infrastructure); Family related when the specific item concerns family email/calendar/contact use or household communication |
| K-g `seanehansell.com` primary | Parenting | **Personal Operations** primary (technical domain/identity infrastructure); Family / Parenting related |
| K-h `mariahansell.com` primary | Family | **Personal Operations** primary; Family related |
| K-i Tier D historical domains | Personal Operations, suppress | **Personal Operations** primary, `surface_state: suppress`, `historical_likely: true` — confirmed |

**Generalized domain renewal rule:** All non-MTS, non-Darkstar technology domains → **Personal Operations** primary, with related contexts marking user-facing impact.

- `morelen.net` → Personal Operations; related: Family
- `seanehansell.com` → Personal Operations; related: Family, Parenting
- `mariahansell.com` → Personal Operations; related: Family
- `projectefed.com` → Personal Operations
- Tier C `bigislandjeep.*`, `darkstar.games`, `darkstarknights.com` → Personal Operations until classified; still need CEO triage decisions
- Tier D historical (10 domains) → Personal Operations, suppress, historical_likely
- Darkstar domains (`darkstartechnology.net`) → Darkstar Technology
- MTS domains → MTS Pro Services

### Items reverted from earlier Group K assignments

| Item | Earlier K assignment | Reverted to |
|---|---|---|
| Morelen migration project | K1 → Family | Personal Operations |
| Morelen Workspace canonical | K8 → Family | Personal Operations |
| `seanehansell.com` | K6 → Parenting | Personal Operations |
| `mariahansell.com` | K6 → Family | Personal Operations |
| `morelen.net` | K6 → Family | Personal Operations |
| Seane (person) primary | K7 → Parenting | Family |
| Seane's birthday 2026-05-26 | K3 → Parenting | Family |
| Evanescence concert / project | K3 → Parenting | Family |
| Digital Survivorship / Maria Emergency Access Plan | K3 → Family (unchanged — still Family) | Family (confirmed) |

### Final classification table (post-Group L)

Roll-up of every classified item in this proposal after Group L corrections:

**MTS Pro Services (primary):** HSM, HOLY, PSP, MAID, TFM projects; MTS people; MTS source systems; `sean@mtsproservices.com`; Sean's MTS work anniversary 2007-03-19.

**Darkstar Technology (primary):** Darkstar Business Setup; Darkstar Website / Public Positioning; Darkstar alias / `darkstartechnology.net`; future Darkstar systems.

**Family (primary):** Maria, Diane "Mom", Brian & Jessie Magh, Ethan Magh, Lily Rose Magh, John Puswald, Christina Prisco, Matthew Prisco, Chris Hansell, Brett Bastiansen, Jason Mills, Laura Mills, Frank/Irene Puswald (deceased), Robert "Bob" Hansell (deceased); Seane (primary; related Parenting + School); all family birthdays/anniversaries/memorial dates; Summer 2026 NY Trip; Reunion 2026-06-13; Diane's 80th birthday 2026-06-15; Mom & Dad anniversary 2026-06-24; Evanescence concert 2026-06-24 (related: Parenting + Travel); Wedding anniversary 2026-05-06; Seane's birthday 2026-05-26 (related: Parenting); Evanescence / Seane First-Concert Support project (related: Parenting + Travel); Digital Survivorship / Maria Emergency Access Plan project.

**Home (primary):** Home Assistant / Smart-Home Architecture; The Hill; Halloween House Decoration (project + dates); Christmas House Decoration (project + dates); Home Infrastructure Documentation.

**School (primary):** 2026-2027 School Year Planning project; all HIDOE 2026-27 calendar dates; Google Classroom, Infinite Campus, Remind; `3712000032@k12.hi.us`.

**Parenting (primary):** Year-round weekly parenting review cadence. (Specific child-facing care items appear when activated; none currently active in intake.)

**Personal Operations (primary):** Sean's birthday 1983-10-17; Ken Taber; LifeOps / COO System Build project; Project eFed Platform project; Health / Cardio / Flexibility Improvement Plan project (+ Health domain); Morelen Account / Domain Migration Planning project (related: Family); Morelen Workspace and `sean@morelen.net` (related: Family); Kaiser Permanente, Apple Health; Apple Notes; Mac Admins Slack (weighted); all non-MTS, non-Darkstar domains (`morelen.net`, `seanehansell.com`, `mariahansell.com`, `projectefed.com`, Tier C, Tier D).

**Public (relevance/source, not primary):** news, weather, civic, travel-safety, school/public-calendar external signals. Suppressed unless tied to active concern.

---

## Summary (post-Group L)

- **Mechanical resolutions:** A2, A3, A4, A6, B1, B3, C1, C2, C3, C4, D1, D3, D4, E1, E2, E4, F1, F2, F3, G1, G2, G3, G4, G5, H1, H2, H3, H4, I1, I2 — applied.
- **Group K (re-applied with Group L corrections):** K1, K2, K3, K4, K5, K6, K7, K8, K9 — applied with Group L overrides.
- **Group J resolutions:** A1 (resolved by K → 7 contexts), A5 (resolved), B2 (resolved → 4 surface states), D5 (resolved), E5 (superseded by Group L K-b), I3 (resolved), K-a through K-i (resolved per Group L).
- **Deferred (do not block):** D2 Tier C/D domain detailed classification (now all under Personal Operations until further triaged), E3 The Hill split, plus all Open questions in §3 of the intake summary.

**Gate status:** All canonicalization blockers resolved. COO proceeds to write a **canonical-file proposal** showing the exact contents that would be written to `context/`, `state/projects/`, `rules/`, and `workflows/`. No canonical file is written until CEO approves that proposal.

---

## Confirmation request

Please respond with one of:

- **Approve mechanical resolutions and decide blockers** — answer Group J (six items). On receipt, COO writes canonical files per the intake summary §"On approval" plan.
- **Approve mechanical, defer blockers** — answer some Group J items; the rest stay as Open questions and the canonical files use the recommended defaults flagged in this pass. (Note: A1 and B2 cannot be deferred — they shape the file structure itself.)
- **Request changes** — list inline. COO revises this pass and re-presents.
- **Reject** — no canonical files written. Both proposals remain for future reference.
