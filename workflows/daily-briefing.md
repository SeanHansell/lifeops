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

Read every file under `state/projects/`, `state/waiting/`, `state/decisions/`, `state/inbox/`. Do not load `state/archive/` by default.

### 3. Read inputs

Read every file under `inputs/`. Determine the unit of processing per file:

- **Single-item input.** The file describes one item. Its file-level `context:` and other frontmatter apply to that item.
- **Multi-item input.** The file declares `context: unknown` at the file level and the body lists individually labeled items (each with its own inline context such as `personal`, `work`, `school`, or `household`). In this case, treat each inline-labeled item as a separate input. The file-level `as_of:`, `source:`, and `confidence:` apply to every item unless an item declares its own override.

For each resulting item, decide:

- Does this match an existing state file? Propose an update.
- Does this create a new obligation? Propose a new state file under the appropriate `state/` subdirectory for its context.
- Is the item's individual context still unknown or ambiguous? Route to `state/inbox/`.

Do not silently delete inputs after processing. Note them in the log, including the per-file unit-of-processing decision.

### 4. Classify and label

For every item destined for the briefing, ensure it carries:

- `context:` (per [rules/compartmentalization.md](../rules/compartmentalization.md))
- `source:`, `as_of:`, `confidence:` (per [rules/source-confidence.md](../rules/source-confidence.md))
- `surface:` — `surface`, `defer`, or `suppress` (per [rules/safe-to-ignore.md](../rules/safe-to-ignore.md))

Items missing any of these go into "Blocked by missing or ambiguous data" rather than into the surfaced sections.

### 5. Draft the briefing

Write to `briefings/YYYY-MM-DD.md` with the following structure:

    ---
    date: YYYY-MM-DD
    context_status: <bootstrapped | not yet bootstrapped>
    ---

    # Briefing — YYYY-MM-DD

    ## Today
    - (items with `surface: surface` and `needed_by` within today, labeled by context)

    ## This week
    - (items with `surface: surface` and `needed_by` within seven days, excluding today)

    ## Decisions needed
    - (open items from `state/decisions/` with `needed_by` within seven days)

    ## Actions needed
    - (concrete actions the CEO must take; one line each, labeled with context)

    ## Waiting on others
    - (`state/waiting/` with `direction: inbound`, sorted by `expected_by`)

    ## Waiting on the CEO
    - (`state/waiting/` with `direction: outbound`, sorted by `expected_by`)

    ## Approaching dates
    - (anchors from `context/dates.md` or input data falling within fourteen days)

    ## Stale but important
    - (items not surfaced in N days whose review trigger fires today)

    ## Requires approval before any external action
    - (anything in `proposals/` not yet approved)

    ## Blocked by missing or ambiguous data
    - (unbootstrapped context, missing sources, stale entries past threshold, items lacking required labels)

    ## Safe to ignore (collapsed)
    - defer: <count> items across <categories>
    - suppress: <count> items across <categories>

    ## Activity
    - inspected: <count> files
    - inferred: <count> claims
    - proposed: <count> entries → `proposals/`
    - changed: <count> files in `state/`, `inputs/`, `briefings/`
    - refused: <count> actions (reasons in log)
    - log: `logs/YYYY-MM-DD-daily-briefing.md`

Every line in the surfaced sections must carry its context label.

### 6. Write the activity log

Append `logs/YYYY-MM-DD-daily-briefing.md` per [rules/activity-visibility.md](../rules/activity-visibility.md).

### 7. Run an independent audit pass

Run an independent audit per [workflows/audit-pass.md](audit-pass.md) in fresh context. Provide:

- The path to the draft briefing
- The path to the log
- The list of paths read during the run

In Claude Code, implement this by spawning the `auditor` subagent defined in [.claude/agents/auditor.md](../.claude/agents/auditor.md). Other runtimes spawn an isolated reviewer per the audit-pass spec.

Wait for the audit findings.

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
