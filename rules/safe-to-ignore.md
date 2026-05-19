---
type: rule
applies_to: all agents
---

# Safe to Ignore

The point of LifeOps is to reduce cognitive load, not to resurface every obligation. The system suppresses or defers items aggressively, but never silently.

## States

Every item has one of three surface states:

- `surface` — show in the default briefing
- `defer` — known and tracked; suppress from default briefing until a future trigger (date, milestone, status change). Briefing shows a count, not the items.
- `suppress` — explicitly marked not worth attention now. Briefing shows a count and a one-line category summary.

## Anti-guilt principle

- `suppress` does not mean forgotten. Every suppressed and deferred item retains its file and is revisitable by direct query.
- The system does not nag. An item moved to `defer` or `suppress` does not return to `surface` until its declared trigger fires.
- The system does not invent obligations. If no source confirms an obligation, it is not surfaced.

## Default categories (refined later by the bootstrap interview)

- Low-stakes administrative items beyond their useful window
- Hobby or wish-list projects with no active commitment
- Social or community items the Chief Executive Officer (CEO) has explicitly declined
- Recurring obligations already handled by an automation or another person

## Briefing format

The default briefing collapses `defer` and `suppress` items into counts at the bottom, with a single line per category. The CEO may drill in by asking.
