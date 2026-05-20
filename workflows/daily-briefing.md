---
type: workflow
name: daily-briefing
status: superseded
superseded_by: .claude/skills/daily-briefing/SKILL.md
superseded_on: 2026-05-20
---

# Daily Briefing — SUPERSEDED

This file is **no longer the runtime contract** for the LifeOps daily briefing.

The canonical runtime contract — modes, inputs, surfacing rules, section order, surfaced-item format, classification taxonomy, reconciliation rules, token / read budget, audit behavior, and stop conditions — now lives in:

**[.claude/skills/daily-briefing/SKILL.md](../.claude/skills/daily-briefing/SKILL.md)**

All policy that previously lived here has been migrated to the skill, including:

- The four modes (normal daily, bootstrap / rebuild, reindex, audit) and the Monday weekly review extension.
- Index-first reading discipline for normal daily mode.
- Input processing rules (single-item vs. multi-item parsing; routing logic; canonical-source rule for `state/manual/`).
- The canonical section order and surfaced-item format.
- The status taxonomy and the conflict / stacked-date taxonomy.
- The Audit and data quality section format.
- Reconciliation rules for each kind of auditor finding.
- The token / read budget per mode.
- Stop conditions and canonical-source migration policy.

`rules/` remains canonical for cross-cutting policy (operating model, compartmentalization, source confidence, approval gates, safe-to-ignore, activity visibility, auditor charter). The skill aligns with `rules/`; if there is a conflict, `rules/` win.

`/briefing` routes through the skill. The `auditor` subagent (`.claude/agents/auditor.md`) is invoked from the skill per its audit and normal-mode procedures.

This file is preserved as a redirect so historical references in `briefings/`, `logs/`, `proposals/`, and other artifacts still resolve. Do not add policy here. Update the skill instead.
