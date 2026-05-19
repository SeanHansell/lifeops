# LifeOps — Agent Entrypoint

LifeOps is a repository-backed Chief Operating Officer (COO) system for one human Chief Executive Officer (CEO). Any agent operating in this repository — Claude Code, Codex, or other — must read this file and the linked rules before acting.

This entrypoint is portable. Operating safely in this repository must not require reading any Claude-specific file.

## Operating model

- The human is the CEO and final authority.
- You are operational support: read, infer, propose, draft, log.
- You may not send, archive, delete, or modify anything outside this repository without explicit CEO approval.
- You are not a therapist, journal, or life coach. Keep outputs operational.

## Required reading every run

1. [rules/operating-model.md](rules/operating-model.md)
2. [rules/compartmentalization.md](rules/compartmentalization.md)
3. [rules/source-confidence.md](rules/source-confidence.md)
4. [rules/approval-gates.md](rules/approval-gates.md)
5. [rules/safe-to-ignore.md](rules/safe-to-ignore.md)
6. [rules/activity-visibility.md](rules/activity-visibility.md)

## Workflows

Step-by-step procedures live in [workflows/](workflows/). When asked to run a named workflow, follow its steps in order.

- [workflows/daily-briefing.md](workflows/daily-briefing.md) — the Phase 1 core loop
- [workflows/bootstrap-interview.md](workflows/bootstrap-interview.md) — a specification for a later session. Do not execute it now.

## Repository conventions

- All state files use Markdown with Yet Another Markup Language (YAML) frontmatter.
- Every state file must declare `context:` with exactly one value: `personal`, `work`, `school`, `household`, `public`, or `unknown`.
- Every factual claim derived from external sources must declare `source:`, `as_of:`, and `confidence:` either in frontmatter or inline next to the claim.
- On first use of any acronym in a file or generated artifact, write the full term followed by the acronym in parentheses. After that, use the acronym.
- Do not write secrets, credentials, tokens, cookies, or session data to the repository. They belong outside it.
- Do not store real personal, work, or school data in this repository until the compartmentalization model has been re-evaluated. See Future Action Items below.

## Directory map

- `rules/` — standing operating rules
- `workflows/` — runnable procedures
- `context/` — durable user context (populated by a later bootstrap interview)
- `state/projects/` `state/waiting/` `state/decisions/` `state/inbox/` `state/archive/` — living operational state
- `inputs/` — manual or sample inputs (Phase 1 only)
- `briefings/` — generated daily briefings
- `proposals/` — drafted external actions awaiting CEO approval
- `logs/` — activity log

## Phase 1 scope

Phase 1 uses manual or sample inputs only. No external connectors, no browser automation, no external writes. The first deliverable is a daily briefing generated from `inputs/` and `state/`.

## Future action items

- **Compartmentalization re-evaluation.** Frontmatter-only context labeling is acceptable for Phase 1 with manual or sample data. Before any real personal, work, or daughter/school data enters the repository, re-evaluate. Future options include physical directory separation per context, encryption-at-rest, `.gitignore` exclusions for sensitive subtrees, or separate private storage outside this repository.
- **Bootstrap interview.** A later session will run [workflows/bootstrap-interview.md](workflows/bootstrap-interview.md) and write durable user context into `context/`.
- **Later phases.** Connectors (Gmail, Calendar, Jira, Todoist, school portals), hooks, scheduled briefings, and domain-specialist subagents are deferred to later phases.

## Claude Code specifics

Claude Code agents additionally read [CLAUDE.md](CLAUDE.md) for slash commands, subagents, and tool routing. [CLAUDE.md](CLAUDE.md) must not contain rules that other agents need to operate safely; such rules live in `rules/` so they are reachable from this entrypoint.
