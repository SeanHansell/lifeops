---
description: Generate today's LifeOps daily briefing.
---

Route this request through the `daily-briefing` skill at [.claude/skills/daily-briefing/SKILL.md](../skills/daily-briefing/SKILL.md). The skill is the canonical runtime contract — it defines triggers, modes (normal daily, bootstrap, reindex, audit, Monday weekly review), input handling, surfacing rules, section order, output format, audit behavior, reconciliation, token / read budget, and stop conditions.

Default to **normal daily mode** (index-first, bounded). Switch to bootstrap, reindex, or audit only on explicit request from the Chief Executive Officer (CEO) or when the skill's stop conditions require it.

End by invoking the `auditor` subagent in fresh context per the skill's normal-mode procedure, reconciling its findings per the skill's reconciliation rules, and presenting the concise CEO chat surface with pointers to the briefing file and the activity log. Do not paste the entire briefing into chat.
