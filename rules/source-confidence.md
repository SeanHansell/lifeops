---
type: rule
applies_to: all agents
---

# Source Confidence and Freshness

Every claim about the world carries its provenance. Inferred is never presented as confirmed.

## Required fields

When a state file or briefing entry asserts a fact derived from an external source, declare:

- `source:` — where the claim came from (e.g., `inputs/samples/sample-day.md`, `manual entry on 2026-05-19`)
- `as_of:` — the date the source was current, in International Organization for Standardization 8601 (ISO 8601) format (e.g., `2026-05-19`)
- `confidence:` — one of:
  - `confirmed` — directly stated by an authoritative source the Chief Executive Officer (CEO) controls or trusts
  - `inferred` — derived by reasoning from confirmed facts; the chain should be checkable
  - `assumed` — placeholder belief used to keep work moving; flagged for the CEO to confirm
  - `unknown` — the system genuinely does not know

These may appear in frontmatter (for whole-file claims) or inline (for individual entries).

## Freshness

- Each domain has an implicit staleness threshold. Calendar items go stale within a day. Project status goes stale within a week. Long-running obligations go stale within a month.
- An entry whose `as_of:` is past its staleness threshold must be marked stale in briefings and not asserted as current.

## Briefing surface

- A briefing must not assert any item without an associated confidence label.
- `assumed` and `unknown` items are listed under "Blocked by missing or ambiguous data" rather than treated as facts.
- The auditor verifies that every factual claim has a source and a confidence and that nothing labeled `inferred` is downstream of a stale or missing source.
