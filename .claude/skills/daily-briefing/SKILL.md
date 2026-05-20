---
name: daily-briefing
description: Generate the LifeOps daily briefing for the Chief Executive Officer (CEO) across the seven primary operating contexts (MTS Pro Services, Darkstar Technology, Family, Home, School, Parenting, Personal Operations). Use whenever Sean says "start my day", "daily briefing", "morning briefing", "what's on my plate today", "what do I need to know today", "LifeOps briefing", invokes `/briefing`, or otherwise asks for the day's situational overview. Default to normal daily mode (bounded, index-first). Switch to bootstrap, reindex, or audit mode only on explicit request or when indexes are missing. Do not run a full repo scan as part of normal daily mode.
---

# LifeOps Daily Briefing — Canonical Runtime Contract

This skill is the **canonical runtime contract** for generating the LifeOps daily briefing. It defines:

- when to trigger
- the four modes (normal daily / bootstrap / reindex / audit) plus the Monday weekly review extension
- input reading discipline and routing
- surfacing rules
- section order and output format
- classification taxonomy
- reconciliation rules
- token / read budget
- audit behavior
- stop conditions

The skill aligns with policy in `rules/` (operating model, compartmentalization, source confidence, approval gates, safe-to-ignore, activity visibility, auditor charter). Where `rules/` define a constraint, the skill obeys it. The skill is the authoritative description of *what the briefing run does*; `rules/` are the authoritative description of *what the system as a whole is allowed to do*.

The prior contract in `workflows/daily-briefing.md` is superseded by this file (see [workflows/daily-briefing.md](../../../workflows/daily-briefing.md), which now redirects here).

---

## Purpose

Give the CEO a complete, executive-readable situational picture at the start of the day — across all seven primary operating contexts — without burning a full repository scan on every run.

---

## When to run

Trigger this skill when Sean says any of:

- "start my day"
- "daily briefing" / "morning briefing" / "LifeOps briefing"
- "what's on my plate today"
- "what do I need to know today"
- `/briefing` (slash command)
- anything that clearly asks for a daily situational overview

Do not wait for him to be explicit — if he's starting a session and wants orientation across LifeOps contexts, run normal daily mode.

If he says any of the following, switch mode before generating:

- "bootstrap the briefing", "rebuild the briefing", "full scan" → **bootstrap/rebuild mode**
- "reindex", "refresh the indexes", "the indexes are stale" → **reindex mode**
- "audit the briefing", "verify the briefing", "audit-only pass" → **audit mode**
- "Monday weekly review", "weekly LifeOps review", "run the deep pass" → **Monday weekly review** (extension of normal daily mode)

---

## Modes

### 1. Normal daily mode (default)

Index-first, delta-driven. Produces the briefing directly. **No full repo discovery.**

Required reads (mandatory; in this order):

1. `state/indexes/briefing-contract.md` — compact rules summary (contexts, surface states, source-confidence labels, approval tiers, status taxonomy).
2. `state/indexes/dates.md` — anchors with current lead-time ring positions for today.
3. `state/indexes/waiting.md` — outbound and inbound waits with `direction` and `expected_by`.
4. `state/indexes/decisions.md` — open decisions with `needed_by` if known.
5. `state/indexes/approvals.md` — open proposals with tier and AUDIT WARNING flags.
6. `state/indexes/briefing-surface.md` — current `surface`-state items per context.
7. `state/indexes/projects.md` — compact project summaries (slug, context, status, surface, last touched, next action) for active or due projects only.
8. `state/indexes/triage.md` — triage items with `triage_question`, `resolution_path`, `triage_age_days`.

Conditional reads (only when justified):

- `briefings/<previous-date>.md` — open only to copy carryover framing or verify continuity, not as a wholesale re-read.
- Any cited source file (`state/projects/<slug>.md`, `state/waiting/<id>.md`, `state/decisions/<id>.md`, `context/dates.md`, an open proposal) — open only when an index entry is stale, ambiguous, contradicts another index, or carries an inline `VERIFY` tag.
- `inputs/**` — open and process **only if non-empty**. If empty, note in the Activity section and skip. Input processing follows the [Input handling](#input-handling) rules below.

If any required index file is missing or has not been refreshed since the last `state/` mutation, halt normal mode and switch to **reindex mode** (or **bootstrap mode** if no indexes have ever been built). Surface the switch to the CEO before continuing.

### 2. Bootstrap / rebuild mode

Full canonical scan permitted. Used for:

- First-time skill setup (no `state/indexes/` directory exists).
- Schema changes to the index format.
- Repair after detected index corruption or contradiction.

Bootstrap mode reads:

- All files under `rules/`, `context/`, `state/projects/`, `state/waiting/`, `state/decisions/`, `state/inbox/`, `state/manual/`, `inputs/`, the most recent briefing under `briefings/`, and all open proposals under `proposals/`.
- `state/archive/` is **not** loaded by default.

Bootstrap mode writes:

- All files under `state/indexes/` (creates the directory if absent).
- A bootstrap log under `logs/<date>-briefing-bootstrap.md`.

Bootstrap mode must declare in chat: "Running in **bootstrap/rebuild mode** — full canonical scan. Token budget exceeded by design."

Bootstrap does **not** produce a briefing as part of the same run unless the CEO explicitly asks for both. By default, after bootstrap finishes, prompt the CEO to confirm before running normal daily mode against the new indexes.

### 3. Reindex mode

Refreshes compact indexes from source files after major edits. Lighter than bootstrap — it walks only the index categories that changed.

Reindex mode reads:

- All source files in the directories whose indexes are being refreshed (e.g., `state/projects/` for `state/indexes/projects.md`).
- The previous index file being replaced (to compare deltas for the log).

Reindex mode writes:

- The updated index file(s) under `state/indexes/`.
- A reindex log under `logs/<date>-briefing-reindex.md`.

Trigger reindex automatically if normal mode detects an index that is stale relative to a `state/` file's `as_of:` timestamp.

### 4. Audit mode

Verifies a previously-produced briefing against its cited sources and indexes. Does **not** regenerate the briefing.

Audit mode reads:

- The target briefing file (default: today's, else most recent under `briefings/`).
- The corresponding `logs/<date>-daily-briefing.md`.
- Every file path cited in `Source:` metadata lines in the briefing.
- The indexes referenced by the briefing run.

Audit mode invokes the `auditor` subagent in fresh context per [.claude/agents/auditor.md](../../agents/auditor.md), passing the briefing path, log path, and the cited-paths list. It then appends the auditor's report and any reconciliation to the log per [Reconciliation rules](#reconciliation-rules) below.

Audit mode does not rerun normal-mode generation. If the auditor returns a `block` verdict, surface the blocker to the CEO and stop — do not auto-regenerate.

### Monday weekly review (extension)

A **Monday weekly review** is an optional extension of normal daily mode, gated on either:

- today being Monday **and** the CEO explicitly confirming the deep pass, or
- the CEO explicitly invoking the weekly review by name on any day.

It must never run as a side effect of normal daily mode, even on Monday.

The Monday weekly review adds:

- A full read of `state/projects/` (not just active/due summaries) to refresh `state/indexes/projects.md`.
- A confirmation pass over any `confidence: inferred` items in the project shelf (e.g., the MTS inferred-active backlog) — propose promotion to `confirmed` or demotion to dormant.
- A `state/indexes/triage.md` age sweep — flag triage items older than seven days.
- An "Approaching this week" rollup at the top of the briefing.

The weekly review is allowed to exceed the normal-mode token budget. It must declare in chat: "Running **Monday weekly review** — extended scan."

---

## Input handling

When `inputs/**` contains files, determine the unit of processing per file:

- **Single-item input.** The file describes one item. Its file-level `context:` and other frontmatter apply to that item.
- **Multi-item input.** The file declares `context: unknown` at the file level and the body lists individually labeled items (each with its own inline context such as `personal`, `work`, `school`, or `household`). Treat each inline-labeled item as a separate input. The file-level `as_of:`, `source:`, and `confidence:` apply to every item unless an item declares its own override.

For each resulting item:

1. If it matches an existing state file in any subdirectory, propose an update to that file.
2. Otherwise, if the item's individual context is unknown or ambiguous, route to `state/inbox/`.
3. Otherwise, choose the destination by item shape:
   - Active or dormant multi-step initiative → `state/projects/`
   - Obligation between the CEO and another party (inbound or outbound) → `state/waiting/`
   - Open decision requiring CEO judgment → `state/decisions/`
   - Calendar event, task, or date anchor that fits none of the above → `state/manual/` (see [Canonical-source rule](#canonical-source-rule-for-statemanual) below)
4. Do not duplicate the item across subdirectories.

Do not silently delete inputs after processing. Note them in the activity log, including the per-file unit-of-processing decision and the destination subdirectory for each item.

### Canonical-source rule for `state/manual/`

For any item destined for `state/manual/`, set:

- `canonical_source:` — the external system that would own this item once connectors exist (`calendar`, `todoist`, `jira`, `school_portal`, etc.) — or `unknown` if the canonical system is not yet known.
- `canonical_status:` — one of `not_connected`, `connector_planned`, `connected`. If `connected`, do not materialize the item; the connector pass will surface it.

`state/manual/` is transitional. When external connectors exist for a canonical source listed on a manual item, the skill prefers the connector's view and stops creating new manual entries of that type. Supersession of existing manual entries follows the archive-with-traceability policy documented in [state/manual/README.md](../../../state/manual/README.md). Connector mechanics are deferred to a later phase; this skill defines the preference, not the implementation.

### Classification and labeling

For every item destined for the briefing, ensure it carries:

- `context:` (per [rules/compartmentalization.md](../../../rules/compartmentalization.md))
- `source:`, `as_of:`, `confidence:` (per [rules/source-confidence.md](../../../rules/source-confidence.md))
- `surface:` — `surface`, `defer`, `suppress`, or `triage` (per [rules/safe-to-ignore.md](../../../rules/safe-to-ignore.md))
- `related_contexts:` (optional list) — additional primary contexts impacted, used as tags
- `triage_question:` and `resolution_path:` — required when `surface: triage`

Items missing any of these go into "Blocked by missing or ambiguous data" rather than into the surfaced sections.

---

## Surfacing policy

In normal daily mode, an item is surfaced in the briefing if it matches at least one of:

- `due today` (date == today)
- `overdue` (date < today and `status != Done`)
- `expected_by` passed (waiting items)
- inside a configured lead-time window per `context/dates.md` (e.g., 14-day planning ring for a birthday)
- explicitly marked `surface: surface`
- marked `surface: triage`
- carries `NEEDS DECISION`
- attached to an open proposal in `state/indexes/approvals.md`
- changed since the previous briefing (by `as_of:` or index delta)
- creates a conflict or stacked-date interaction with another surfaced item

Items not matching any trigger are not surfaced. They appear only as counts under **Safe to ignore**.

`public`-context items are omitted by default unless tied to an active obligation, tracked topic, safety issue, travel, weather, school, household operations, or explicit request.

### Safe-to-ignore policy

Use counts and category labels from `state/indexes/briefing-surface.md` and `state/indexes/projects.md` rather than rereading every deferred or dormant source file.

Default output:

    - defer: <count> items across <category list>
    - suppress: <count> items across <category list>

    Drill-down available on request.

Do not list deferred or suppressed items inline. If the CEO asks to drill in, open the index entry first; only open the source file if the index doesn't answer the question.

---

## Section order and output format

Produce the briefing as `briefings/YYYY-MM-DD.md` using exactly this section order:

```
# Daily Briefing — YYYY-MM-DD

## Today
## Decisions needed
## Waiting on me
## Waiting on others
## Cross-domain conflicts and stacked dates
## Upcoming
## Triage
## Approvals queue
## Context summaries
## Safe to ignore
## Audit and data quality
## Activity
```

Sections are presented in this order. Empty sections are omitted unless absence itself is meaningful (e.g., "Today: nothing time-sensitive" on a low-load day stays as an affirmative line).

The briefing frontmatter is:

    ---
    date: YYYY-MM-DD
    context_status: <bootstrapped | not yet bootstrapped>
    contexts_present: <list>
    ---

### Surfaced-item format (canonical)

Every surfaced item in the action sections (`Today`, `Decisions needed`, `Waiting on me`, `Waiting on others`, `Triage`, `Upcoming`, `Approvals queue`) is a bullet starting with a bolded human-readable title:

    - **Human-readable title** — Short executive-facing sentence on why it matters.
      - Context: <primary context>
      - Status: <Active | Waiting | Decision needed | Triage | Informational | Audit warning>
      - Source: `path/to/source.md`

Additional metadata lines per section:

- `Waiting on me` / `Waiting on others`: `Direction:` (`outbound` | `inbound`) and `Expected by:` (ISO 8601). Mark overdue inline when past window.
- `Decisions needed`: `Needed by:` (ISO 8601) when known.
- `Upcoming`: `Date:` (ISO 8601) and `Lead-time ring:` per `context/dates.md` (e.g., `14-day planning`, `3-day final reminder`, `day-of`).
- `Triage`: `Triage question:` and `Resolution path:` (subset of `surface | defer | suppress | archive | close`).
- `Approvals queue`: `Tier:` (`0` through `4`).

Rules:

- Titles are short noun phrases, executive-readable. Acronyms expanded on first use per the acronym rule below.
- The one-line summary after the em-dash explains **why this matters**, not what the file contains.
- Every surfaced item carries a `Source:` metadata line citing the canonical state, context, input, proposal, or log path. Source traceability is mandatory.
- Each item declares its primary `Context:` from the seven-context model in `rules/compartmentalization.md`. `public` items are omitted by default unless tied to an active concern.

### Classification taxonomy

Use these classifications, in the section noted:

| Section | Field | Allowed values |
|---|---|---|
| Action sections | `Status:` | Active, Waiting, Decision needed, Triage, Informational, Audit warning |
| Cross-domain conflicts and stacked dates | `Type:` | Conflict, Stacked date, Informational overlap |
| Audit and data quality | `Type:` | Audit warning, Data quality issue |

Status meanings:

| Status | Meaning |
|---|---|
| Active | Tracked surface-state item with an owner and a next action. |
| Waiting | Awaiting response or unblock (pair with `Direction:` and `Expected by:`). |
| Decision needed | Requires Chief Executive Officer (CEO) judgment before progress. |
| Triage | Routing or classification question; carries `Triage question:` and `Resolution path:`. |
| Informational | No action required; surfaced for awareness (e.g., upcoming anchors). |
| Audit warning | Auditor finding surfaced to the CEO at the action surface (rare; usually lives under Audit and data quality). |

### Cross-domain conflicts and stacked dates

Reserved for **real-world scheduling, responsibility, emotional-load, logistical, or priority collisions** — not for data inconsistencies or process findings. Use `Type:` (not `Status:`) in metadata.

    - **Human-readable title** — Plain description of the collision or overlap.
      - Context: <primary context, or "Multiple" with the contexts named>
      - Type: <Conflict | Stacked date | Informational overlap>
      - Severity: <Watch | Plan | Resolve>
      - Action: <one-line>
      - Source: `path/to/source.md`

Type definitions:

- **Conflict** — Two or more obligations cannot both be honored as planned. True scheduling, responsibility, or identity collision. Requires a decision or rescheduling.
- **Stacked date** — Multiple meaningful anchors land on the same date or in a tight window without strict incompatibility, but with real emotional, logistical, or attentional load.
- **Informational overlap** — Anchors that happen to coincide but create no planning load. Use sparingly; if no load, consider omitting.

Severity: `Watch` (no action now), `Plan` (schedule resolution within the relevant horizon), `Resolve` (decision or action required before the date).

### Audit and data quality

Consolidates auditor findings and data-quality observations. Each finding is a bullet in the same title-plus-metadata format, with `Type:` instead of `Status:`.

    - **Human-readable title** — Short explanation.
      - Type: <Audit warning | Data quality issue>
      - Action: <one-line>
      - Source: `path/to/source.md` (or "auditor" / "main thread" when no file source)

Type definitions:

- **Audit warning** — Process or policy compliance finding from the auditor. See [rules/auditor-charter.md](../../../rules/auditor-charter.md).
- **Data quality issue** — Inconsistency, mismatch, stale value, missing source, or freshness gap. Surfaced here rather than in action sections.

The section opens with a short header summarizing verdict and counts, then lists findings:

    - Verdict: <pass | pass-with-warnings | block>
    - Blockers: <count>
    - Warnings: <count>
    - Highest severity: <none | warning | blocker>
    - Audit log: `logs/YYYY-MM-DD-daily-briefing.md`

    Findings:
    - **<title>** — ...

For blockers, the verdict line reads `Verdict: block` and the blocking finding carries a `Required action:` metadata line (e.g., `triage`, `source confirmation`, `approval correction`, `context correction`).

### Context summaries

A short paragraph or sub-list per primary context with at least one tracked item. Reads as a state-of-context summary, not a project dump. Omit contexts with nothing tracked.

    ### <Context name>
    - **Headline** — One-line state of this context today.
      - Active surfaces: <count> (slugs listed if useful)
      - Triage: <count>
      - Deferred: <count>
      - Notable change today: <one-line, or "none">

### Acronyms

The first time an acronym appears in a generated artifact, write the term in full followed by the acronym in parentheses. After that, use the acronym. This includes Chief Executive Officer (CEO), Chief Operating Officer (COO), MTS Pro Services (MTS), International Organization for Standardization 8601 (ISO 8601), Do-It-Yourself (DIY).

### Inline qualifiers

`NEEDS SOURCE`, `NEEDS DECISION`, `STALE`, `OVERDUE`, `UNKNOWN` may be appended to a title when they materially change the read. Prefer explicit metadata fields over inline label noise.

### Cadence and length

- One briefing per day (not workday-only).
- "Nothing urgent" days produce a brief affirmative briefing.
- The briefing is real but not exhaustive. Default surface is concise; implementation and audit detail live at the end of the briefing, not at the top.
- Each surfaced item is identifiable by its title; the `Source:` metadata line provides the canonical file path for drill-down.

---

## Token / read budget

Express budget against repository input opened during the run (file reads), not output tokens.

| Mode | Target | Warning threshold | Hard exception |
|---|---|---|---|
| Normal daily | ≤ 8,000 tokens of repo input | ≥ 12,000 → declare in Activity section | None — if budget exceeded, switch to reindex mode and try again |
| Monday weekly review | ≤ 20,000 tokens | ≥ 30,000 → declare in Activity section | Allowed to exceed; must announce |
| Bootstrap / rebuild | Unbounded | n/a | Must declare full-scan mode in chat before reading |
| Reindex | ≤ 10,000 tokens per index category | n/a | Declare per-category counts in the reindex log |
| Audit | ≤ 6,000 tokens (cited sources only) | ≥ 10,000 → declare in Activity section | Never re-read the full repo |

If the model cannot directly measure token counts, use file-count + lines-read as a proxy and state the proxy in the Activity section.

---

## How to run normal daily mode

1. **Resolve today's date.** Use the system date or, if the CEO supplies one, use the supplied date.

2. **Read the eight required indexes** under `state/indexes/`. If any index is missing or its `as_of:` is older than the most recent `as_of:` in a related `state/` file, halt and switch modes per [Modes](#modes).

3. **Process inputs** per [Input handling](#input-handling) (only if `inputs/**` is non-empty).

4. **Compute today's deltas** vs. the previous briefing (read at most one previous briefing, only if needed for carryover framing).

5. **Apply the surfacing policy** to identify which items earn a surfaced bullet. Everything else collapses to counts under Safe to ignore.

6. **Resolve verification flags.** For any index entry marked `VERIFY`, stale, ambiguous, or contradictory with another entry, open the cited source file and reconcile. Cite the source in the briefing.

7. **Draft `briefings/YYYY-MM-DD.md`** in the canonical section order, with surfaced items in the canonical format.

8. **Write the activity log** to `logs/YYYY-MM-DD-daily-briefing.md`. Include:
   - `skill_mode:` in frontmatter (`normal-daily` | `monday-weekly-review` | `bootstrap` | `reindex` | `audit`).
   - Inspected / Inferred / Proposed / Changed / Refused sections per [rules/activity-visibility.md](../../../rules/activity-visibility.md).
   - Indexes read; source files opened; source files skipped because the index was current; stale or missing index entries; approximate token / read budget status; validation or audit warnings encountered before the formal audit pass.

9. **Run the auditor** in fresh context via the `auditor` subagent per [.claude/agents/auditor.md](../../agents/auditor.md). Pass the briefing path, log path, and the list of paths actually opened. Wait for findings.

10. **Reconcile auditor findings** per [Reconciliation rules](#reconciliation-rules) below. Apply changes to the briefing. Append the auditor report and the reconciliation to the log.

11. **Surface to the CEO** per [Output to chat](#output-to-chat-ceo-surface) — a concise chat summary with section counts, the Decisions / Actions / Waiting / Approaching Dates lines in full, and a pointer to the briefing file. Do not paste the entire briefing into chat.

---

## How to run bootstrap / rebuild mode

1. Announce: "Running in **bootstrap/rebuild mode** — full canonical scan. Token budget exceeded by design."

2. Read everything in scope (see [Modes → 2](#2-bootstrap--rebuild-mode)).

3. For each canonical index, generate or rebuild the file under `state/indexes/`. Required indexes:

    | Index | Source directories | Required columns / fields |
    |---|---|---|
    | `briefing-contract.md` | `rules/`, this skill | summary of contexts, surface states, source-confidence labels, approval tiers, status taxonomy — one page, no verbatim policy text |
    | `dates.md` | `context/dates.md` | anchor, date, primary context, lead-time ring positions for the index's `as_of:` date |
    | `waiting.md` | `state/waiting/` | id, title, context, direction, expected_by, status, source |
    | `decisions.md` | `state/decisions/` | id, title, context, needed_by, status, source |
    | `approvals.md` | `proposals/` | id, title, context, tier, audit_warning flag, source |
    | `briefing-surface.md` | `state/projects/`, `state/manual/`, `state/inbox/` | slug, context, surface state, surface_triggers, last_touched, source |
    | `projects.md` | `state/projects/` | slug, context, status, surface, confidence, last_touched, next_action, source |
    | `triage.md` | `state/projects/`, `state/manual/`, `state/inbox/` | slug, context, triage_question, resolution_path, triage_age_days, source |

4. Write a bootstrap log at `logs/<date>-briefing-bootstrap.md` with `skill_mode: bootstrap`. Record what each index was built from and any source-file warnings discovered during the scan.

5. Stop. Ask the CEO to confirm before running normal daily mode against the new indexes.

---

## How to run reindex mode

1. Announce: "Running in **reindex mode** — refreshing <list of indexes>."

2. For each index being refreshed, read the source directory and rebuild the index file. Preserve previous-run metadata where unchanged.

3. Write a reindex log at `logs/<date>-briefing-reindex.md` with `skill_mode: reindex`. Record per-index delta counts (added, updated, removed).

4. Return control. Do not auto-run normal daily mode unless the CEO requested both.

---

## How to run audit mode

1. Announce: "Running in **audit mode** — verifying briefing against cited sources."

2. Open the target briefing and its log. Collect every `Source:` path cited in the briefing.

3. Open each cited source file once. Verify:
   - The claim in the briefing is supported by the cited source.
   - `source`, `as_of`, `confidence` are present where required.
   - No `inferred` claim is downstream of a stale or missing source.
   - Compartmentalization holds (every entry has exactly one primary context; no cross-context leakage).
   - Approval-tier assignments are correct.

4. Invoke the `auditor` subagent in fresh context for an independent pass.

5. Append findings and reconciliation to the briefing's log per [Reconciliation rules](#reconciliation-rules).

6. Do not regenerate the briefing.

---

## Reconciliation rules

For each auditor finding:

- If it identifies an unsupported or unsourced claim, remove or relabel the claim in the briefing.
- If it identifies a boundary violation (context leakage), move the affected item to `state/inbox/` and note the move in the log.
- If it identifies stale data past threshold, mark the item stale in the briefing.
- If it identifies a missing approval gate on a proposed action, move the item to `proposals/` and remove it from any action-taking section.

Apply changes to the briefing file. Append the auditor's findings and the reconciliation to the log. The Audit and data quality section in the published briefing must reflect the actual auditor pass — never pre-fill it before the auditor runs.

Apply the auditor charter's block-vs-warn distinction (see [rules/auditor-charter.md](../../../rules/auditor-charter.md)): a blocker halts publication; warnings flag the briefing but allow publication with appropriate labels.

---

## Activity section requirements

The briefing's `## Activity` section must report:

- `run mode:` one of `normal-daily`, `monday-weekly-review`, `bootstrap`, `reindex`, `audit`
- `indexes read:` list (filename only)
- `source files opened:` count + list (filename or path)
- `source files skipped because indexes were current:` count (or `n/a` for bootstrap)
- `stale or missing index entries:` count + brief list (or `none`)
- `approximate token / read budget status:` `under target` | `at warning` | `over warning — switching modes` | `bootstrap exception`
- `validation or audit warnings:` count + one-line categories (or `none — see Audit and data quality for the formal audit pass`)

In addition to the standard Activity counts (`inspected`, `inferred`, `proposed`, `changed`, `refused`, `log:`) required by [rules/activity-visibility.md](../../../rules/activity-visibility.md).

---

## Output to chat (CEO surface)

After the briefing file and log are written and the auditor pass is reconciled, surface a concise summary in chat:

- One sentence on context status (`bootstrapped` or `not yet bootstrapped`) and the run mode.
- Section counts for the canonical section order.
- The full content of **Decisions needed**, **Waiting on me**, the next-day **Today** line, and the **Upcoming** anchors inside an open lead-time ring.
- The audit verdict (`pass`, `pass-with-warnings`, `block`) and the blocker / warning counts.
- A single line pointing at `briefings/YYYY-MM-DD.md` for full detail and `logs/YYYY-MM-DD-daily-briefing.md` for the activity log.

Do not paste the entire briefing into chat.

---

## Stop conditions

- If a required index file is missing or stale in normal mode, halt and switch to reindex / bootstrap.
- If the auditor returns `block`, halt and surface the blocker; do not auto-regenerate.
- If `rules/`, `context/`, `CLAUDE.md`, `AGENTS.md`, `.gitignore`, or this skill file have been edited in the same session without explicit CEO approval, halt and report per [rules/approval-gates.md](../../../rules/approval-gates.md).
- If a boundary violation cannot be resolved by relabeling, escalate to the CEO and do not finalize.
- If the CEO has not bootstrapped `context/` and asks for a briefing, generate the briefing against `state/`, `inputs/`, and `rules/` only — do not run the bootstrap interview from this skill — and state in the chat surface that context has not been bootstrapped.

---

## Policy alignment

This skill is the canonical runtime contract. The following files in `rules/` remain canonical for cross-cutting policy and must not be silently overridden:

- [rules/operating-model.md](../../../rules/operating-model.md) — roles, escalation, what AI may and may not do
- [rules/compartmentalization.md](../../../rules/compartmentalization.md) — the seven-context model
- [rules/source-confidence.md](../../../rules/source-confidence.md) — `source` / `as_of` / `confidence` discipline
- [rules/approval-gates.md](../../../rules/approval-gates.md) — the four-tier ladder and protected files
- [rules/safe-to-ignore.md](../../../rules/safe-to-ignore.md) — the four surface states
- [rules/activity-visibility.md](../../../rules/activity-visibility.md) — what to log
- [rules/auditor-charter.md](../../../rules/auditor-charter.md) — strictness priorities, block-vs-warn, false-positive tolerance

If this skill conflicts with any of the above, the rules win; surface the conflict to the CEO and stop.
