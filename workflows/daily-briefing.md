---
type: workflow
name: daily-briefing
invoked_by: /briefing
---

# Daily Briefing Workflow

This is the Phase 1 core loop. It runs when the Chief Executive Officer (CEO) invokes `/briefing` or asks for the daily briefing by name.

## Inputs

- All files under `rules/` — read every run
- All files under `context/` — read every run; if stubs, note that in the briefing
- All files under `state/` (excluding `state/archive/` by default) — read every run
- All files under `inputs/` (including `inputs/samples/`) — read every run
- Today's date

## Steps

### 1. Load rules and context

Read every file in `rules/`. Read every file in `context/`. If any `context/` file has `status: stub`, set `context_status` to `not yet bootstrapped` and note that in the briefing's "Blocked by missing or ambiguous data" section.

### 2. Read state

Read every file under `state/projects/`, `state/waiting/`, `state/decisions/`, `state/inbox/`, and `state/manual/`. Do not load `state/archive/` by default.

### 3. Read inputs

Read every file under `inputs/`. Determine the unit of processing per file:

- **Single-item input.** The file describes one item. Its file-level `context:` and other frontmatter apply to that item.
- **Multi-item input.** The file declares `context: unknown` at the file level and the body lists individually labeled items (each with its own inline context such as `personal`, `work`, `school`, or `household`). In this case, treat each inline-labeled item as a separate input. The file-level `as_of:`, `source:`, and `confidence:` apply to every item unless an item declares its own override.

For each resulting item:

1. If it matches an existing state file in any subdirectory, propose an update to that file.
2. Otherwise, if the item's individual context is unknown or ambiguous, route to `state/inbox/`.
3. Otherwise, choose the destination by item shape:
   - Active or dormant multi-step initiative → `state/projects/`
   - Obligation between the CEO and another party (inbound or outbound) → `state/waiting/`
   - Open decision requiring CEO judgment → `state/decisions/`
   - Calendar event, task, or date anchor that fits none of the above → `state/manual/` (see canonical-source rule below)
4. Do not duplicate the item across subdirectories.

**Canonical-source rule for `state/manual/`.** For any item destined for `state/manual/`, set `canonical_source:` to the external system that would own this item once connectors exist (`calendar`, `todoist`, `jira`, `school_portal`, etc.) and `canonical_status:` to `not_connected`, `connector_planned`, or `connected`. If `canonical_status: connected`, do not materialize the item; the connector pass will surface it. If the canonical system is not yet known, set `canonical_source: unknown` and proceed. See [../state/manual/README.md](../state/manual/README.md).

Do not silently delete inputs after processing. Note them in the log, including the per-file unit-of-processing decision and the destination subdirectory for each item.

### 4. Classify and label

For every item destined for the briefing, ensure it carries:

- `context:` (per [rules/compartmentalization.md](../rules/compartmentalization.md))
- `source:`, `as_of:`, `confidence:` (per [rules/source-confidence.md](../rules/source-confidence.md))
- `surface:` — `surface`, `defer`, `suppress`, or `triage` (per [rules/safe-to-ignore.md](../rules/safe-to-ignore.md))
- `related_contexts:` (optional list) — additional primary contexts impacted, used as tags
- `triage_question:` and `resolution_path:` — required when `surface: triage`

Items missing any of these go into "Blocked by missing or ambiguous data" rather than into the surfaced sections.

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
    (Work / Family / School / Home / Parenting timing collisions or identity collisions.)

    ## Blocked / waiting on me
    (Items the Chief Executive Officer [CEO] must unblock.)

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

#### Label registry

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

#### Cadence and length

- One briefing per day (not workday-only).
- "Nothing urgent" days produce a brief affirmative briefing.
- The briefing is real but not exhaustive. Default surface is concise; detail lives in drill-down files.
- Each surfaced item carries an item identifier (slug-based) to support drill-down. File paths and source paths appear only on explicit request.

### 6. Write the activity log

Append `logs/YYYY-MM-DD-daily-briefing.md` per [rules/activity-visibility.md](../rules/activity-visibility.md).

### 7. Run an independent audit pass

Run an independent audit per [rules/auditor-charter.md](../rules/auditor-charter.md) and [workflows/audit-pass.md](audit-pass.md) in fresh context. Provide:

- The path to the draft briefing
- The path to the log
- The list of paths read during the run

In Claude Code, implement this by spawning the `auditor` subagent defined in [.claude/agents/auditor.md](../.claude/agents/auditor.md). Other runtimes spawn an isolated reviewer per the charter.

Wait for the audit findings. Apply the auditor charter's block-vs-warn distinction: a blocker halts publication; warnings flag the briefing but allow publication with appropriate labels.

### 8. Reconcile auditor findings

For each auditor finding:

- If it identifies an unsupported or unsourced claim, remove or relabel the claim.
- If it identifies a boundary violation, move the affected item to `state/inbox/` and note the move.
- If it identifies stale data past threshold, mark the item stale.
- If it identifies a missing approval gate on a proposed action, move the item to `proposals/` and remove it from the action-taking section.

Apply changes to the briefing file. Append the auditor's findings and the reconciliation to the log.

### 9. Surface to the CEO

In chat, present a concise summary:

- One sentence on context status (bootstrapped or not).
- Counts for each section.
- The Decisions, Actions, Waiting on the CEO, and Approaching Dates lines in full (these are the smallest high-signal surface).
- A single line pointing at the briefing file for full detail.

Do not paste the entire briefing into chat.

## Stop conditions

- If the auditor reports a boundary violation that cannot be resolved by relabeling, escalate to the CEO and do not finalize the briefing.
- If `rules/` or `context/` files are missing or have been edited in this session without approval, halt and report.

## Canonical-source preference and migration policy

The `state/manual/` directory is transitional. When external connectors exist for a canonical source listed on a manual item (Calendar, Todoist, Jira, school portals, etc.), the workflow prefers the connector's view and stops creating new manual entries of that type. Supersession of existing manual entries follows the archive-with-traceability policy documented in [../state/manual/README.md](../state/manual/README.md).

Connector mechanics are deferred to a later phase. This workflow defines the preference, not the implementation.
