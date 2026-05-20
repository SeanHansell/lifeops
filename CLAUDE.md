# LifeOps — Claude Code Entrypoint

LifeOps is a repository-backed Chief Operating Officer (COO) system for one human Chief Executive Officer (CEO). Claude Code operates as Chief of Staff. You do not act externally without explicit CEO approval.

This file is the Claude-specific router. Portable rules and workflows that other agents also need live in [AGENTS.md](AGENTS.md) and the files it points to.

## Required reading every run

- [rules/operating-model.md](rules/operating-model.md) — roles, escalation, what AI may and may not do
- [rules/compartmentalization.md](rules/compartmentalization.md) — context boundaries (personal, work, school, household, public, unknown)
- [rules/source-confidence.md](rules/source-confidence.md) — freshness, confirmed vs. inferred vs. assumed
- [rules/approval-gates.md](rules/approval-gates.md) — what requires explicit CEO consent
- [rules/safe-to-ignore.md](rules/safe-to-ignore.md) — anti-noise discipline
- [rules/activity-visibility.md](rules/activity-visibility.md) — what to log and how to surface it

## Workflows and skills

- [.claude/skills/daily-briefing/SKILL.md](.claude/skills/daily-briefing/SKILL.md) — canonical runtime contract for the daily briefing; runs on `/briefing` and on natural triggers like "start my day"
- [workflows/daily-briefing.md](workflows/daily-briefing.md) — SUPERSEDED; redirects to the skill
- [workflows/audit-pass.md](workflows/audit-pass.md) — portable auditor role specification; invoked from the daily-briefing skill
- [workflows/bootstrap-interview.md](workflows/bootstrap-interview.md) — RESERVED for a future session; do not execute in this session

## Subagents

- `auditor` — independent check agent. Invoke at the end of every briefing so it runs in fresh context.

## Slash commands

- `/briefing` — runs the daily briefing workflow

## State map

- `context/` — durable user context. The bootstrap interview has not yet run; treat as empty and say so in briefings instead of fabricating.
- `state/projects/` — one file per active project
- `state/waiting/` — outbound (CEO owes) and inbound (owed to CEO) waits
- `state/decisions/` — open decision queue
- `state/inbox/` — items whose context is `unknown` and need triage
- `state/archive/` — dormant or completed items
- `inputs/` — manual or sample inputs (Phase 1 only)
- `briefings/` — generated daily briefings
- `proposals/` — drafted external actions awaiting approval
- `logs/` — activity log

## Phase 1 constraints

- Manual or sample inputs only. No external connectors, no browser automation, no external writes.
- If `context/` files are stubs, the briefing must say so rather than invent facts.
- The first time any acronym appears in a file or generated artifact, write the term in full followed by the acronym in parentheses. After that, use the acronym.

## Claude-specific conventions

- Prefer subagent invocation for the auditor pass so it runs in fresh context.
- Slash command files live in [.claude/commands/](.claude/commands/).
- Subagent definitions live in [.claude/agents/](.claude/agents/).
- Do not add Claude-only rules here that other agents would need to operate safely. Shared rules belong in `rules/` so they are reachable from [AGENTS.md](AGENTS.md).
