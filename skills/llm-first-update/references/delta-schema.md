# Delta Schema & Update Guarantees

> Load this file during Phase 5 (DELTA) and Phase 6 (APPLY) of the update pipeline.

## Change Delta Format

The change delta is the core output of the update skill. It is presented to the user for review before any files are modified.

### Delta Structure

```markdown
## Change Delta — [Source Title] ([Date])

**Source:** SRC-XXX — [title], [type], [date]
**Project:** [project directory path]
**Existing counts:** [X] entities, [Y] activities, [Z] decisions, [W] sources

### Decisions
| ID | Change Type | Current State | Proposed State | Evidence |
|----|-------------|---------------|----------------|----------|

### Activities
| ID | Change Type | Current State | Proposed State | Evidence |
|----|-------------|---------------|----------------|----------|

### Consistency Items
| ID | Change Type | Current State | Proposed State | Evidence |
|----|-------------|---------------|----------------|----------|

### New Entries
| File | ID | Type | Description | Evidence |
|------|----|------|-------------|----------|

### Entities (if changed)
| ID | Change Type | Detail | Evidence |
|----|-------------|--------|----------|

### No Change (Confirmed)
| ID | What was confirmed |
|----|-------------------|
```

### Change Types

| Label | Meaning | When to Use |
|-------|---------|-------------|
| ✅ Confirmed | Existing entry validated by new source, no modification needed | Entity mentioned, decision referenced without change |
| ⚠️ Changed | Existing entry needs modification | Status change, cadence change, scope change |
| 🆕 New | Entry does not exist in project, needs to be created | New action item, new decision, new entity |
| ❌ Superseded | Existing entry replaced by new decision | Decision reversed, approach abandoned |
| 🔄 Progressing | Consistency item partially addressed | Gap has action plan but isn't fully resolved |
| ✔️ Resolved | Consistency item fully addressed | Ambiguity defined, gap filled, conflict resolved |

## Update Guarantees

These invariants MUST be enforced during Phase 6 (APPLY):

### ID Continuity
- Determine high-water mark for each ID scheme before any changes
- New IDs = high-water mark + 1, incrementing sequentially
- Never reuse a previously assigned ID
- Never skip an ID in the sequence

### Entity Matching
- Before creating a new ENT-*, search existing entities by:
  - Exact name match
  - First name / last name partial match
  - Known aliases (if documented in existing entry)
- If match found → reuse existing ID
- If no match → assign next ENT-* ID

### Format Preservation
- New entries MUST follow the exact structural pattern of existing entries in the same file
- Copy the table layout (Field/Value pairs) from an existing entry as template
- Maintain consistent heading levels, anchor format, separator lines

### Source Attribution
- Every modified or new entry MUST reference the new SRC-* in its Source field
- For updated entries: append new source to existing Source field (don't replace)
- Format: `[SRC-XXX](SOURCES.md#src-xxx)`

### Cross-File Links
- Every new cross-file reference uses full-path format: `[ID](FILE.md#anchor)`
- No bare-anchor references to other files (e.g., never `[ACT-023](#act-023)` when ACTIVITIES.md is a different file)
- Intra-file references may use bare anchors

### Update Notation
When modifying an existing entry, add a brief update note:
```markdown
| **Updated** | 2026-03-24 via [SRC-010](SOURCES.md#src-010) — cadence changed from weekly to bi-weekly |
```
