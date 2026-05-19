# state/projects/

One file per active project. Filename: `<slug>.md`.

## Required frontmatter

- `context:` — one of `personal`, `work`, `school`, `household`, `public`, `unknown`
- `status:` — `active`, `dormant`, `blocked`, or `done`
- `surface:` — `surface`, `defer`, or `suppress` (see [rules/safe-to-ignore.md](../../rules/safe-to-ignore.md))
- `next_review:` — International Organization for Standardization 8601 (ISO 8601) date for the next review trigger
- `source:`, `as_of:`, `confidence:` for any externally-derived claims

Dormant projects that should still be tracked stay here. They move to `state/archive/` only when the Chief Executive Officer (CEO) confirms.
