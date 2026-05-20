---
type: rule
applies_to: all agents
---

# Safe to Ignore

The point of LifeOps is to reduce cognitive load, not to resurface every obligation. The system suppresses or defers items aggressively, but never silently.

## Surface states (canonical, four)

Every item has one of four surface states:

- `surface` — show in the default briefing
- `defer` — known and tracked; suppressed from default briefing until a documented trigger fires (date, dependency, milestone, review-window, or activation). Briefing shows a count, not the items.
- `suppress` — explicitly marked not worth attention now. Briefing shows a count and a one-line category summary.
- `triage` — visible holding lane for items requiring classification, routing, source confirmation, or Chief Executive Officer (CEO) decision before they can safely become `surface`, `defer`, or `suppress`.

### Triage rules

- A `triage` item must declare a `triage_question:` (one-line description of what needs deciding) and a `resolution_path:` listing the allowed next states: any of `surface`, `defer`, `suppress`, `archive`, `close`.
- Triage items must not be presented as normal obligations. They appear in a dedicated Triage section of the briefing, not under the priority sections used for surfaced obligations.
- An item may not remain in `triage` indefinitely. Each triage item must include a `triage_age` review per the briefing workflow; the auditor flags stale triage.

### Surface triggers

Items in `defer` may declare `surface_triggers:` — a list of conditions that, when met, surface the item. Allowed triggers include: date reached, dependency satisfied, milestone reached, scheduled review window, registrar failure, deadline, real-world consequence detected, conflict detected, or explicit CEO request. Without a matching trigger, a `defer` item stays in counts only.

## Anti-guilt principle

- `suppress` does not mean forgotten. Every suppressed, deferred, and triage item retains its file and is revisitable by direct query.
- The system does not nag. An item moved to `defer` / `suppress` / `triage` does not return to `surface` until its declared trigger fires or its triage question is resolved.
- The system does not invent obligations. If no source confirms an obligation, it is not surfaced.

## Default categories (refined by bootstrap interview)

Suppress aggressively unless a documented trigger fires:

- Hobby / wish-list / someday-maybe items without explicit current commitment
- Early-stage business ideas (Darkstar Technology) without active task / deadline / commitment / risk / scheduled review
- Recurring obligations handled by another person, automation, or external system
- Low-stakes administrative items past their useful window
- School items without source or explicit user-provided context
- Financial items without source / deadline / consequence / current review
- Stale project context not recently activated
- General health/productivity nudges without concrete plan / appointment / metric / commitment
- Public / news / external content without active-context relevance
- General reminders that do not affect today or the next few days
- Recurring operations appearing as projects without a bounded outcome
- Anything tagged `Personal Operations` that should be `unknown`

## Briefing format

The default briefing:

- Surfaces items in `surface` state in the priority sections defined by [.claude/skills/daily-briefing/SKILL.md](../.claude/skills/daily-briefing/SKILL.md).
- Shows `triage` items in a dedicated Triage section (not mixed with normal obligations).
- Collapses `defer` and `suppress` items into counts at the bottom, with a single line per category.

The CEO may drill in by asking.
