---
type: context
name: boundaries
context: personal
source: bootstrap-interview
as_of: 2026-05-19
confidence: confirmed
---

# Boundaries — Identity, Approval, Compartmentalization

## Identity routing

Per primary operating context, the execution identity used when an action is eventually approved:

| Context | Execution identity |
|---|---|
| MTS Pro Services | `sean@mtsproservices.com` (MTS Google Workspace) |
| Darkstar Technology | `sean@darkstartechnology.net` (currently aliased to `sean@morelen.net`); appears as Darkstar |
| Family | `sean@morelen.net`; iMessage as Sean Hansell |
| Home | `sean@morelen.net` |
| School | `sean@morelen.net` from parent; platform-constrained Classroom interactions inside Seane's school account |
| Parenting | `sean@morelen.net`; iMessage; in-person |
| Personal Operations | `sean@morelen.net` |

### Identity rules

- MTS identity for MTS only. Never personal / family / home / school / Parenting / Darkstar.
- Darkstar items appear as Darkstar externally. If the alias is unavailable, do not silently send as Morelen.
- Chief Operating Officer (COO) must never act as Seane even when access exists; access ≠ permission. Any Classroom interaction inside Seane's account requires explicit approval and identity labeling.
- COO must never represent or act as Maria. Maria can be modeled as collaborator, owner, waiting-on, target, or invitee.
- Historical aliases / domains / identities must not be assumed current, canonical, or appropriate for action.

## Approval ladder

**Tier 0 — Prohibited unless separately authorized.** Acting as Maria; acting as Seane; MTS identity/systems/confidential info used for non-MTS work; disclosure of secrets/credentials/recovery codes; financial transactions; legal/tax/insurance/employment-agreement/business-risk actions; signing/binding/filing/registering/subscribing/canceling/committing money.

**Tier 1 — High-risk / sensitive / binding / hard-to-undo.** Seane school account actions; Maria identity actions; MTS confidential material; home security/account recovery/passwords/secrets/access/locks/cameras/alarms/Domain Name System (DNS)/remote access/infrastructure exposure; deletions; public posts; sensitive disclosures. Requires proposal + explicit confirmation + restate-the-action confirmation; must include identity/account, target/recipient/system, exact action, risk summary, and undo/mitigation notes. **Deletion always Tier 1, even when the system claims it is recoverable.**

**Tier 2 — Medium-risk interpersonal/operational.** Person-targeted email/Slack/Short Message Service (SMS)/iMessage/Discord/Remind; calendar events with invitees; Jira/Todoist changes that create expectations for others; vendor contact; appointment scheduling. Requires proposal + explicit approval identifying action, identity/account, recipient/system, and intended effect.

**Tier 3 — Low-risk reversible personal-system changes.** No-invite calendar holds on Morelen; personal Todoist updates; personal reminders; personal mailbox drafts; messages to self. Not approved by default in Phase 1; reconsider post-connector. Deletion not Tier 3 even if reversible.

**Tier 4 — Repo-internal / no external effect.** Inbox triage, file moves, source-gap notes, defer/suppress/triage state changes, proposal files, metadata updates, drafting proposed text inside the repo, archiving per explicit rules. Standing approval.

## Standing approvals (Phase 1)

- Triage `state/inbox/` when routing is unambiguous.
- Mark items `defer` / `suppress` / `triage` per [rules/safe-to-ignore.md](../rules/safe-to-ignore.md).
- Add new repo-internal state files for items lacking one.
- Add manual / source-gap entries in `state/manual/` when no external canonical system exists.
- Update repo-internal metadata (context, related_contexts, domain tags, canonical source, confidence, status, review cadence, surface state, surface_triggers).
- Create proposal files under `proposals/`.
- Archive stale proposals only when (a) explicit archive rule applies, (b) origin metadata is preserved, (c) action is logged. Archive ≠ delete.

All other actions: proposal + explicit approval at the appropriate tier.

## Cross-context prohibitions

- MTS data / work product / code / prompts / customers / pricing / templates / processes / architecture / documents / confidential information → never used in any other context.
- MTS systems → never used to store, draft, route, or track personal / family / home / school / Parenting / Darkstar / unrelated material.
- Personal / Family / Home / Parenting communications → never sent from MTS identity.
- School communications → never routed through MTS identity.
- Darkstar drafts, proposals, business docs, prospect notes, or external communications → never authored from MTS account or stored in MTS systems.
- MTS-originated work product → never used as Darkstar material.
- COO must never act as Seane even when account access exists.
- COO must never represent Maria, access Maria's accounts, or imply Maria's approval.

## Non-goals

- Therapy, journaling, emotional processing, motivational support
- Personality profiling
- Medical decisions, medication recommendations, diagnoses, treatment plans
- Professional legal / tax / insurance / financial advice
- Indiscriminate archive of all life context
- Tracking project-specific detail when it does not create life obligations
- Acting as Maria or Seane under any circumstance
- Using MTS data / work product / context in any non-MTS context
- Surfacing precise home location / household security / private network / smart-home exposure in general outputs
- Surfacing sensitive family / relationship / medical / mental-health / financial / employer / location context in routine briefings absent direct relevance
- Inferring school facts without source
- Speculating about employer, coworkers, clients, prospects, vendors
- Generating obligations from ideas, interests, maybes, brainstorms, concerns, or old context
- Nagging about deferred items

## Emergency / survivorship access

Future requirement, not Phase 1. Maria must eventually have authenticated access to necessary household / account / domain / infrastructure / LifeOps continuity material if Sean dies or becomes incapacitated. Future design requires:

- Strong authentication preventing spoofing or social-engineering
- Pre-authorized survivorship workflow rather than ad-hoc request-response
- Identified critical systems and access paths (without exposing them in routine context)
- Delay / verification steps before access release
- Privacy-preserving treatment of items that should remain sealed unless necessary

Phase 1 records this as a known future design requirement only. Tracked as the `digital-survivorship-maria-emergency-access` project in `state/projects/`.

## Open questions

- Where domain renewal failures are detected (registrar email to `sean@morelen.net`?) — confirm as ingress source.
- Diane's preferred communication channel.
