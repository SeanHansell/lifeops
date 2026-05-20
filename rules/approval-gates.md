---
type: rule
applies_to: all agents
---

# Approval Gates

The default is deny. External effect requires explicit Chief Executive Officer (CEO) approval at the appropriate tier.

## Approval ladder (canonical)

### Tier 0 — Prohibited unless separately authorized

- Acting as Maria
- Acting as Seane
- Using MTS Pro Services (MTS) identity or systems for personal, Family, Home, Parenting, School, or Darkstar Technology (Darkstar) work
- Using MTS confidential information in any non-MTS context
- Disclosure of secrets, credentials, recovery codes, tokens, or private access paths
- Financial transactions
- Legal, tax, insurance, employment-agreement, or business-risk actions
- Signing, filing, registering, binding coverage, subscribing, canceling, or committing money

Not approvable under the normal flow. Requires a separate policy, explicit authorization, and appropriate authentication where relevant.

### Tier 1 — High-risk / sensitive / binding / hard-to-undo

- Any action involving Seane's school account or school communications beyond routine low-risk clarification
- Any action involving Maria's identity, accounts, or implied consent
- Any action involving MTS confidential or employer-sensitive material
- Any action involving home security, account recovery, passwords, secrets, access, locks, cameras, alarms, Domain Name System (DNS), remote access, or infrastructure exposure
- **Deletion of any record (external or repo-internal beyond explicit archive rules) — deletion is always Tier 1, even when the system claims it is recoverable**
- Public posts
- Sending sensitive relationship, medical, financial, employer, school, or family information

Approval requirements:

- Proposal file under `proposals/`
- Explicit approval
- **Restate-the-action confirmation**
- Must include identity/account, target/recipient/system, exact action, risk summary, and undo/mitigation notes where possible

### Tier 2 — Medium-risk interpersonal or operational

- Sending email to a person
- Sending Slack / Short Message Service (SMS) / iMessage / Discord / Remind message
- Creating calendar events with invitees
- Creating or modifying Jira tickets
- Creating or modifying shared Todoist tasks
- Contacting vendors
- Scheduling appointments
- Routine school, family, home, work, or Parenting communications
- Any change that creates expectations for another person

Approval requirements:

- Proposal file under `proposals/`
- Explicit approval identifying action, identity/account, recipient/system, and intended effect

### Tier 3 — Low-risk reversible personal-system changes

- Creating a no-invite calendar hold on Morelen calendar
- Updating a personal Todoist task
- Creating a personal reminder
- Saving a draft in a personal mailbox
- Sending a message to oneself
- Other reversible, private, non-sensitive changes in a personal system

Approval requirements (Phase 1):

- Not approved by default
- Future policy may allow standing approval by narrow category
- Until then: proposal + explicit approval
- Deletion is never Tier 3 even when reversible

### Tier 4 — Repo-internal / no external effect

- Classifying inbox items
- Moving repo-internal files
- Adding source-gap notes (`state/manual/`)
- Marking `defer` / `suppress` / `triage`
- Creating proposal files
- Updating internal metadata
- Drafting proposed text or actions inside the repo without publishing, sending, scheduling, saving externally, or notifying anyone
- Archiving according to explicit archive/retention rules (preserve origin metadata, log the action)

Approval: standing under existing repo rules. Logged when meaningful. No per-item approval unless touching protected files or proposing deletion.

## Standing approvals (Phase 1)

- Triage `state/inbox/` when routing is unambiguous
- Mark items `defer` / `suppress` / `triage` per [rules/safe-to-ignore.md](safe-to-ignore.md)
- Add new repo-internal state files for items lacking one
- Add manual / source-gap entries in `state/manual/`
- Update repo-internal metadata
- Create proposal files under `proposals/`
- Archive stale proposals only when archive rule is explicit and logged. **Archive ≠ delete.**

## Proposal format

External actions are not executed. They are drafted as files under `proposals/`:

- One file per proposed action
- Filename: `YYYY-MM-DD-<short-slug>.md`
- Frontmatter must include: `context:`, `related_contexts:` (optional), `action:`, `target:`, `source:`, `as_of:`, `confidence:`, `tier:` (0/1/2/3/4), `requires_approval: true`
- Body: what would happen, what the effect is, identity/account that would execute, recipient/system, risk summary, undo notes, what the CEO must confirm

## Stale-proposal policy (future-phase reference)

- After 7 days with no decision and no deadline/dependency: mark as stale
- After 30 days: archive as expired/no-action unless explicitly preserved
- Silence is never consent for execution

## Repository-internal writes — protected files

These require explicit CEO approval to modify or delete:

- Any file under `context/` (durable user context)
- Any file under `rules/` or `workflows/`
- `CLAUDE.md`, `AGENTS.md`, `.gitignore`
