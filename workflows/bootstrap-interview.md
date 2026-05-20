---
type: workflow
name: bootstrap-interview
status: executed 2026-05-19; spec retained for future re-runs
invoked_by: explicit Chief Executive Officer (CEO) request
last_executed: 2026-05-19
output_artifacts:
  - proposals/2026-05-19-bootstrap-intake-summary.md
  - proposals/2026-05-19-bootstrap-normalization-pass.md
  - proposals/2026-05-19-canonical-file-proposal.md
---

# Bootstrap Interview — Specification

This file defines what a session must do to populate `context/`. The interview was executed on 2026-05-19; `context/` is bootstrapped. **Do not re-run this interview unless the Chief Executive Officer (CEO) explicitly requests it** (e.g., to add a new domain or after a major life change). Treat this file as a design contract for future re-runs.

## Purpose

Gather the stable operating context that makes briefings reliable: identity, domains, boundaries, people, dates, and what should be suppressed or deferred. The interview is requirements gathering for a personal operations system. It is not a personality profile, journal, or therapy intake.

## Pre-conditions

- The CEO has explicitly asked to run the bootstrap interview.
- The repository scaffold is in place.
- No real personal, work, or school data is yet in the repository.
- The compartmentalization model has been re-evaluated (see Future Action Items in [AGENTS.md](../AGENTS.md)) and the CEO has confirmed the storage approach is acceptable for real data.

## Interview principles

- Ask in small batches: no more than five questions per batch.
- Explain why each batch matters before asking.
- Prefer structured answers that can be turned into durable context files.
- Do not ask for credentials, secrets, tokens, cookies, or session data.
- Capture uncertainty explicitly. Do not force premature decisions.
- Separate stable facts from assumptions, preferences, and future action items.
- Ask what should be suppressed, deferred, or marked safe to ignore — not only what should be surfaced.
- Identify which topics belong inside LifeOps as operational tracking and which should be routed elsewhere (reflection, emotional processing, creative development, legal or medical review, human decision-making).

## Suggested batches

1. **Identity and role boundaries.** Who the CEO is in this system. Hard never-dos. Tone preferences.
2. **Daily briefing expectations.** What to surface, suppress, defer, escalate. Default cadence. Drill-down preferences.
3. **Domains.** Which life domains are tracked. Review cadence per domain. Which domains stay in `defer` by default.
4. **Source systems (future, not connected yet).** Which external systems exist and which are in scope for later phases.
5. **Account and identity boundaries.** Per-context identities and accounts at a structural level. No credentials.
6. **Approval boundaries.** What can be drafted internally, proposed, or executed externally only with approval.
7. **Projects.** Active projects, dormant-but-important projects, wish-list projects. Review cadence per project class.
8. **People and dates.** Birthdays, anniversaries, school dates, holidays, gift windows, relationship-sensitive obligations. Per-person communication preferences at a structural level.
9. **Audit and check needs.** Source confidence preferences. What the auditor should be especially strict about. What "safe to ignore" should suppress aggressively.

## Output — intake summary

After interviewing, write a draft intake summary and present it to the CEO for confirmation **before** writing any file under `context/`. The summary separates:

- Confirmed facts
- Assumptions
- Open questions
- Phase 1 requirements
- Later-phase requirements
- Non-goals
- Approval boundaries
- Account and domain boundaries
- Daily briefing expectations
- Safe-to-ignore categories

## Writing to `context/`

Only after the CEO confirms the intake summary:

- Write `context/identity.md`, `context/domains.md`, `context/boundaries.md`, `context/people.md`, `context/dates.md`.
- Each file declares its `context:` and its `source: bootstrap-interview` with the date.
- Any item the CEO did not confirm is marked `confidence: assumed` and listed in an "Open questions" section.

## Stop conditions

- If the CEO declines to confirm the intake summary, do not write to `context/`.
- If the conversation drifts into emotional, therapeutic, or journaling territory, redirect to operational scope or end the interview.
- If a question would require credentials or external account access, skip it.
