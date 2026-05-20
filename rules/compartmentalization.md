---
type: rule
applies_to: all agents
---

# Compartmentalization

LifeOps prioritizes across the whole life, but executes with strict context separation.

## Primary operating contexts

Every state file, input, proposal, and briefing entry carries exactly one **primary operating context**. Allowed values:

- `MTS Pro Services` — employer/work context
- `Darkstar Technology` — early-stage business context
- `Family` — shared family system, marriage/spouse logistics, extended family, family travel, celebrations, relatives, holidays, family finance review, family continuity, and family-facing obligations
- `Home` — property, household infrastructure, repairs, maintenance, smart-home, network, physical home projects, and household operational systems
- `School` — school-system, academic, teacher/admin, calendar, assignment, portal, registration, supply, and school-communication obligations
- `Parenting` — child-facing care, development, routines, supervision, comfort, activities, child-specific logistics, and parenting decisions
- `Personal Operations` — Sean-owned personal systems, technology infrastructure, personal administration, individual projects, personal accounts/domains, health coordination, and personal learning not better owned by MTS or Darkstar
- `unknown` — triage context; routes to `state/inbox/`

## Related contexts

A state file may carry `related_contexts:` (a list) to capture cross-context impact. Related contexts are tags; they do not change the primary or the identity that would execute an action.

## Routing rule

For any item that crosses Family / Parenting / School / Home / Personal Operations, choose the primary context by the **nature of the obligation and owner of the next action**, not merely by who is affected.

- Do not route to `Personal Operations` merely because Sean is the actor or the source is Sean-provided.
- Technical personal infrastructure (accounts, domains, identity, migrations, personal systems) belongs in `Personal Operations` even when it has Family / Home / Parenting impact.
- Seane is a Family member first. Parenting is a responsibility mode applied as a related context.

## Public

`public` is a separate external/source/relevance context — not a primary operating context. Use for news, weather, civic, travel-safety, school/public-calendar, and other external signals. Items labeled `public` do not surface by default unless tied to an active obligation, tracked topic, safety issue, travel, weather, school, household operations, or explicit request.

## Identity and accounts

The Chief Executive Officer (CEO) has distinct accounts and identities per context. See [context/boundaries.md](../context/boundaries.md) for the canonical mapping. Account credentials never enter the repository.

Cross-context prohibitions:

- MTS data / work product / code / prompts / customers / pricing / templates / processes / architecture / documents / confidential information → never used in any non-MTS context.
- MTS systems → never used to store, draft, route, or track non-MTS material.
- Personal / Family / Home / Parenting / Darkstar / school communications → never sent from MTS identity.
- Darkstar material → never authored from MTS account or stored in MTS systems.
- Chief Operating Officer (COO) must never act as Seane even when account access exists.
- COO must never represent or act as Maria.
- Historical aliases / domains / identities are not assumed current, canonical, or appropriate for action.

## Rules

- Every state file MUST declare `context:` from the allowed set above.
- Every state file MAY declare `related_contexts:` as a list of additional primary contexts (or `public`).
- Every input file SHOULD declare `context:`. If absent, treat as `unknown` and route to `state/inbox/`.
- A proposal MUST declare which context's identity, account, or channel would execute it. A proposal that would mix contexts is invalid and must be split or escalated.
- Briefings reconcile across all contexts for prioritization but label every line with its primary context.
- Drill-down files about one context must not embed verbatim content from another.
- Do not infer or guess context. If unsure, label `unknown`.

## Phase 1 enforcement

Phase 1 enforces compartmentalization through frontmatter labels and rule discipline only. Before any real personal, work, or school data enters the repository, the compartmentalization model must be re-evaluated. See Future Action Items in [AGENTS.md](../AGENTS.md).
