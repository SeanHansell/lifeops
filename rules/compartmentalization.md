---
type: rule
applies_to: all agents
---

# Compartmentalization

LifeOps prioritizes across the whole life, but executes with strict context separation.

## Contexts

Every state file, input, proposal, and briefing entry carries exactly one context:

- `personal` — the Chief Executive Officer's (CEO's) own personal life, identity, and accounts
- `work` — the CEO's employer and work accounts
- `school` — the CEO's daughter's school, school staff, school systems
- `household` — shared household concerns (chores, bills, logistics involving more than one household member)
- `public` — public-facing or non-confidential material (open community, public events, public web)
- `unknown` — context not yet determined; triage required

## Rules

- Every state file MUST declare `context:` in its Yet Another Markup Language (YAML) frontmatter.
- Every input file SHOULD declare `context:`. If absent, treat as `unknown` and route to `state/inbox/`.
- A proposal MUST declare which context's identity, account, or channel would execute it. A proposal that would mix contexts is invalid and must be split or escalated.
- Briefings reconcile across all contexts for prioritization but label every line with its context.
- Drill-down files about one context must not embed verbatim content from another.
- Do not infer or guess context. If unsure, label `unknown`.

## Identity and accounts

The CEO has distinct accounts and identities per context (personal email, work email, school portals, household-shared services). Account credentials never enter the repository. Account boundaries are honored by proposing actions per context and labeling each proposal with the context that would execute it.

## Phase 1 enforcement

Phase 1 enforces compartmentalization through frontmatter labels and rule discipline only. Before any real personal, work, or school data enters the repository, the compartmentalization model must be re-evaluated. See Future Action Items in [AGENTS.md](../AGENTS.md).
