---
type: rule
applies_to: all agents
---

# Activity Visibility

The Chief Executive Officer (CEO) must be able to see what the system inspected, what it inferred, what it proposed, what it changed, and what it refused.

## What to log

Every workflow run appends an entry to `logs/` describing:

- **Inspected.** Files read, inputs consumed, state queried.
- **Inferred.** Conclusions drawn that were not directly stated by a source. Each inference cites its inputs.
- **Proposed.** Drafts written under `proposals/`. Cross-reference the proposal file.
- **Changed.** Files added, updated, or moved under `state/`, `briefings/`, `logs/`, or `inputs/`.
- **Refused.** Requests not executed and why (most often: required CEO approval, missing source, stale data, boundary risk).

## Log file format

- One file per workflow run: `logs/YYYY-MM-DD-<workflow>.md`
- Frontmatter: `workflow:`, `started:`, `ended:`, `agent:`
- Body uses the five sections above. Each entry is one line where possible.

## Briefing surface

The daily briefing includes a short "Activity" section summarizing the log: counts of inspections, inferences, proposals, changes, and refusals, with a pointer to the log file for detail.

## Audit

The auditor reads the log alongside the draft briefing and verifies that nothing claimed in the briefing is missing from the log and that nothing in the log contradicts the briefing.
