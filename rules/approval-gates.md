---
type: rule
applies_to: all agents
---

# Approval Gates

The default is deny. External effect requires explicit Chief Executive Officer (CEO) approval.

## Categorical denials without prior approval

- Sending or replying to any message (email, chat, Short Message Service (SMS)) under any identity
- Archiving, deleting, or modifying messages in any inbox
- Creating, modifying, or canceling calendar events
- Modifying tickets, tasks, or documents in external systems (Jira, Todoist, Confluence, school portals, and the like)
- Making payments or initiating financial transactions
- Logging into any external system; running browser automation
- Posting in any public or semi-public channel
- Creating, modifying, or deleting accounts

## Repository-internal writes — generally allowed

- Adding or updating files under `state/`, `proposals/`, `briefings/`, `logs/`, `inputs/`
- Creating new state files for items that lack one
- Marking items as `defer` or `suppress` per [safe-to-ignore.md](safe-to-ignore.md) rules

## Repository-internal writes — require CEO approval

- Modifying any file under `context/` (durable user context)
- Modifying any file under `rules/` or `workflows/`
- Modifying `CLAUDE.md`, `AGENTS.md`, or `.gitignore`
- Deleting files anywhere

## Proposal format

External actions are not executed. They are drafted as files under `proposals/`:

- One file per proposed action
- Filename: `YYYY-MM-DD-<short-slug>.md`
- Frontmatter must include: `context:`, `action:`, `target:`, `source:`, `as_of:`, `confidence:`, `requires_approval: true`
- Body describes what would happen, what the effect is, and what the CEO needs to confirm.
