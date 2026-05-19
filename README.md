# LifeOps

A repository-backed Chief Operating Officer (COO) system for personal operations. Coordinates commitments, dates, projects, and obligations across personal, work, parenting, household, and other contexts while keeping each context properly compartmentalized.

## How to use

- Claude Code: read [CLAUDE.md](CLAUDE.md), then run `/briefing`.
- Other agents: read [AGENTS.md](AGENTS.md).
- Humans: see [AGENTS.md](AGENTS.md) for the operating model and the directory map.

## Phase 1 status

- Manual or sample inputs only.
- No external connectors. No external writes.
- The bootstrap interview that populates `context/` has not yet been run.
- The repository is ready for a first `/briefing` run against the sample input under `inputs/samples/`.

## What this is not

- Not a journal, therapist, or life coach.
- Not an autonomous actor. Proposed external actions live in `proposals/` and await explicit approval.
- Not a content engine. The point is to reduce cognitive load, not generate more of it.
