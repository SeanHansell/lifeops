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

The briefing surfaces audit results in the **Audit and data quality** section, which also carries data-quality findings. Canonical format is defined by [.claude/skills/daily-briefing/SKILL.md](../.claude/skills/daily-briefing/SKILL.md); the auditor produces content that conforms to that format.

The auditor's own report (returned by the subagent) keeps its existing Critical / Warnings / Notes / Verdict structure per `workflows/audit-pass.md`. The main thread reconciles the auditor's report into the briefing's Audit and data quality section.

Briefing Audit and data quality section — required content:

- Verdict (`pass | pass-with-warnings | block`), blocker count, warning count, highest severity, and audit log path.
- One bullet per medium or high-severity finding using the canonical surfaced-item format:

      - **Human-readable title** — Short explanation.
        - Type: <Audit warning | Data quality issue>
        - Action: <one-line>
        - Source: `path/to/source.md` (or "auditor" / "main thread")

- Data-quality findings (mismatches, stale values, missing or weak sources, freshness gaps) also appear here under `Type: Data quality issue`. They do **not** appear under Cross-domain conflicts and stacked dates, which is reserved for real-world planning collisions.

For blockers, the section opens with the verdict line `Verdict: block` and includes a `Required action:` metadata line on the blocking finding (e.g., `triage`, `source confirmation`, `approval correction`, `context correction`).

Unresolved prior audit findings reappear in the briefing until acknowledged, fixed, expired, or explicitly marked known-OK. They do not dominate the briefing unless they block action or affect today; otherwise they appear as counts with drill-down to the audit log.
