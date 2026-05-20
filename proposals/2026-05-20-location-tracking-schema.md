---
type: proposal
context: Personal Operations
related_contexts:
  - Family
  - Home
  - School
  - MTS Pro Services
  - Darkstar Technology
  - Parenting
action: add a `location:` field convention to date anchors, project state files, and waiting/decision/manual entries, and document the convention in the relevant rule and skill files
target: LifeOps repository schema
source: CEO observation 2026-05-20 — "we're not tracking location of these things, so you're missing that context"
as_of: 2026-05-20
confidence: confirmed
tier: 4
requires_approval: true
status: open
---

# Location-Tracking Schema

## Why this exists

On 2026-05-20 the Chief Executive Officer (CEO) noted that LifeOps currently does not track the location of date anchors, projects, waits, or manual items. Location matters for cross-domain conflict detection (e.g., the New York [NY] trip is the travel container for the Evanescence concert and Diane "Mom"'s 80th birthday — both anchors share a location that the system was not modeling), for travel and logistics planning, and for context-correct routing of identity and account use.

This proposal adds a lightweight, optional `location:` field. It does not introduce a new operating context or change the seven-context compartmentalization model; it adds location as a tag-style attribute on items that have one.

## Proposed schema

Add an optional frontmatter field to state files, context files, and proposals:

```yaml
location: <free-text location>
```

Suggested conventions:

- **Free text first.** Sample values: `Hawai'i — Hilo`, `Hawai'i — Kona`, `New York — Brooklyn`, `New York — Riverhead`, `Holy See Mission`, `MTS office`, `home`. No fixed taxonomy at this stage.
- **Multi-location items.** If an item has more than one location (e.g., a trip with several stops), use `locations:` (plural) as a list of free-text values.
- **Container relationship.** If an item occurs *inside* another item's location envelope (e.g., the Evanescence concert occurs inside the NY trip window), prefer pointing at the container via a `travel_container:` field (slug of the containing project) and leaving `location:` blank or aspirational until firm.
- **Unknown.** If the location is genuinely unknown, omit the field. Do not write `unknown` — that creates false signal.

### Where the field applies

- `context/dates.md` table — add a `Location` column for the recurring-personal-dates and one-time future anchors tables.
- `state/projects/<slug>.md` frontmatter — optional `location:` or `locations:`.
- `state/waiting/<slug>.md` frontmatter — optional `location:` (e.g., a plumber appointment is at home).
- `state/manual/<slug>.md` frontmatter — optional `location:` (since calendar events typically carry one).
- `state/decisions/<slug>.md` frontmatter — only when the decision is location-dependent.
- `proposals/<slug>.md` frontmatter — only when the action would have location effect.

### Where it does not apply

- `rules/`, `workflows/` — no location field on policy or workflow files.
- `state/inbox/` — items in inbox are pre-classification; add location only when routing forward.

## Where to document the convention

This is data-model policy that the daily-briefing skill consumes. Documentation lives in:

1. `.claude/skills/daily-briefing/SKILL.md` — add a short note under [Input handling → Classification and labeling](../.claude/skills/daily-briefing/SKILL.md#classification-and-labeling) that items may carry `location:` / `locations:` / `travel_container:`.
2. `state/manual/README.md` — note that manual items may include `location:` (e.g., when materializing a calendar event whose canonical source would carry one).

No `rules/` file needs to change. Location is descriptive metadata, not policy.

## Effect on existing briefings

Once accepted, future briefings:

- Add a `Location:` metadata line to surfaced items in the action sections when a location is set.
- Use locations to refine the **Cross-domain conflicts and stacked dates** section — two anchors at the same location with tight timing become a logistical stacked-date risk; two anchors with conflicting locations become a Conflict.
- Populate location on the seven anchors and projects most affected by the 2026-05-20 reclassifications, where the CEO supplies the value.

## Migration

This is additive. No existing state file is invalidated. The skill's normal-daily mode reads index files first, so location appears in indexes only after the next reindex.

## Initial values to capture (waiting on CEO)

The following items would benefit from a location value now. Each one is currently unknown to the system and needs the CEO to supply or confirm:

- `state/projects/summer-2026-ny-trip.md` — confirmed New York (NY); specific lodging / sub-locations TBD
- `state/projects/evanescence-seane-first-concert.md` — venue TBD (likely NY, inside the trip container)
- `context/dates.md` 2026-06-15 Diane "Mom" 80th birthday — likely NY; confirm
- `context/dates.md` 2026-06-13 reunion — likely NY based on `5pm ET / 12pm HST` framing; confirm
- `context/dates.md` 2026-06-24 Evanescence concert — see above
- `context/dates.md` 2026-06-24 Diane & Bob wedding anniversary (memorial) — historical event date; location not required
- `state/projects/the-hill.md` — home property (Hawai'i)

## Tier and approval

Tier 4 (repo-internal schema change with no external effect). Approval is a standing-approval-eligible category in principle, but because this affects multiple file types and the daily-briefing skill, it is being filed as an explicit proposal so the CEO can confirm the conventions before they propagate.

## Self-check

- Free-text first, no premature taxonomy.
- Optional, not required — backward compatible with all existing state files.
- Lives in metadata, not in body content, so the briefing surface can use it without rewriting summaries.
- Does not introduce a new operating context or change compartmentalization.
- Documentation site is the skill, with one supporting note in `state/manual/README.md`.

## Unresolved questions

- Q1: Should `location:` accept a structured object (`{ city: "New York", venue: "Madison Square Garden" }`) eventually, or stay free-text?
- Q2: Should the `Cross-domain conflicts` detection use string-match on location, or wait for structured values?
- Q3: For travel containers, is `travel_container:` the right name, or `inside_trip:` / `container:`?
