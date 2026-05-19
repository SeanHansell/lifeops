# state/waiting/

Items the Chief Executive Officer (CEO) is waiting on, or that others are waiting on the CEO for.

Two patterns per file:

- `direction: inbound` — someone owes the CEO a response or action
- `direction: outbound` — the CEO owes someone a response or action

## Required frontmatter

- `context:`
- `direction:` (`inbound` or `outbound`)
- `expected_by:` — International Organization for Standardization 8601 (ISO 8601) date the system should escalate if unmet
- `source:`, `as_of:`, `confidence:`

The Chief Operating Officer (COO) escalates outbound items in briefings as they approach `expected_by`.
