# Acceptance Criteria — llm-first-update

## Must-Pass Criteria

| # | Criterion | How to Verify |
|---|-----------|---------------|
| AC-1 | Reads all existing project files and builds complete index before any changes | Phase 1 output shows entity/activity/decision/source counts and ID high-water marks |
| AC-2 | Matches new source mentions to existing entities by name/alias | People, teams, systems mentioned in new source are linked to existing ENT-* IDs, not duplicated |
| AC-3 | Assigns next-in-sequence IDs for genuinely new entries | New ACT-* ID = previous high-water mark + 1; no gaps, no reuse |
| AC-4 | Produces change delta with supporting quotes before modifying any files | Phase 5 delta includes evidence column with source quotes for every proposed change |
| AC-5 | User scoping gate is respected — skill pauses for approval at Phase 4 | User can reject changes as out-of-scope (e.g., personal goals) and they are excluded from delta |
| AC-6 | Updated files maintain structural integrity | Phase 7 validates: all cross-file links resolve, all IDs have anchors, no bare-anchor cross-file refs |
| AC-7 | New SRC-* entry is created and referenced by at least one changed entry | SOURCES.md updated; every change in delta cites the new SRC-* |
| AC-8 | Existing entries are updated in-place, not duplicated | DEC-003 confirmed = DEC-003 updated (not DEC-003 + DEC-008 with same content) |
| AC-9 | Status changes include both old and new status in the delta | Delta shows "Not Started → In Progress" not just "In Progress" |
| AC-10 | Graceful degradation without WorkIQ | When WorkIQ unavailable: Phase 2 accepts paste, Phases 3-7 proceed normally |

## Test Scenarios

### Scenario 1: Meeting ingestion with mixed relevance
- **Input:** Existing project + meeting transcript that is partially about the project, partially off-topic
- **Expected:** Phase 4 presents all proposed changes; user rejects off-topic items; only approved changes appear in final delta and are applied
- **Validates:** AC-4, AC-5

### Scenario 2: Entity matching (no duplicates)
- **Input:** Existing project with ENT-P002 (Daysha Carter) + new source mentioning "Daysha" by first name
- **Expected:** "Daysha" maps to existing ENT-P002, not a new ENT-P009
- **Validates:** AC-2, AC-8

### Scenario 3: ID continuity
- **Input:** Project with ACT-001 through ACT-022 + new source with 2 new action items
- **Expected:** New activities assigned ACT-023 and ACT-024 (not ACT-001, not ACT-100)
- **Validates:** AC-3

### Scenario 4: Decision update vs. new decision
- **Input:** Project with DEC-005 ("Weekly sync") + new source changing cadence to bi-weekly
- **Expected:** DEC-005 is updated (not a new DEC-008 created for the cadence change); delta shows DEC-005 with "Changed" label
- **Validates:** AC-8, AC-9

### Scenario 5: Consistency item resolution
- **Input:** Project with GAP-001 ("No audit relationship") + new source where audit meeting is being scheduled
- **Expected:** GAP-001 status updated from Open to Progressing with source attribution; delta includes supporting quote
- **Validates:** AC-4, AC-7

### Scenario 6: Cross-file link integrity after update
- **Input:** Any valid update that adds new ACT-* entries
- **Expected:** New ACT-* entries have proper anchors; RELATIONSHIPS.md updated if needed; all links resolve; Phase 7 passes
- **Validates:** AC-6

### Scenario 7: Graceful degradation
- **Input:** Project path + manual paste of meeting notes (no WorkIQ)
- **Expected:** Phase 2 accepts paste; skill produces valid delta and applies changes without WorkIQ
- **Validates:** AC-10
