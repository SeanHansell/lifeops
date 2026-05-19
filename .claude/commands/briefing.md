---
description: Generate today's LifeOps daily briefing.
---

Run the daily briefing workflow defined in [workflows/daily-briefing.md](../../workflows/daily-briefing.md). Follow every step in order. End by invoking the `auditor` subagent, reconciling its findings, and presenting the concise surface to the Chief Executive Officer (CEO) with a pointer to the full briefing file.

If `context/` is not yet bootstrapped, do not run the bootstrap interview from this command. Generate the briefing against `state/`, `inputs/`, and `rules/` only, and state explicitly in the surface that context has not been bootstrapped.
