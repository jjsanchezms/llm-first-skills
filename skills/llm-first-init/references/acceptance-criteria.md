# Acceptance Criteria — llm-first-init

## Must-Pass Criteria

| # | Criterion | How to Verify |
|---|-----------|---------------|
| AC-1 | Produces all 9 scaffold files in target directory | Check: PROJECT.md, GLOSSARY.md, ENTITIES.md, ACTIVITIES.md, RELATIONSHIPS.md, DECISIONS.md, SOURCES.md, DISCOVERY.md, CONSISTENCY_REPORT.md |
| AC-2 | Every entity across all files has a stable ID with `{#anchor}` | Grep all files for entity headers; each must have `{#ID}` anchor |
| AC-3 | Every cross-file reference uses full-path format `[ID](FILE.md#anchor)` | No bare-anchor cross-file refs (e.g., `[ID](#anchor)` referencing another file) |
| AC-4 | All cross-file links resolve to existing anchors | Follow every `[...](FILE.md#anchor)` link; target file and anchor must exist |
| AC-5 | User gates are respected — skill pauses at Phase 1, 2, and 4 gates | Skill asks for confirmation before proceeding past each gate |
| AC-6 | SOURCES.md catalogs every input source with SRC-* ID | Each provided source appears with stable ID, type, title, retrieval status |
| AC-7 | CONSISTENCY_REPORT.md surfaces conflicts, ambiguities, and gaps | CON-*, AMB-*, GAP-* items present (or explicit "none found" statement) |
| AC-8 | Graceful degradation without WorkIQ | When WorkIQ unavailable: Phase 1 accepts paste, Phase 2 skipped with note, Phases 3-6 proceed |
| AC-9 | Every ACT-* has owner, status, evidence field, and source link | Grep ACTIVITIES.md; each entry has all 4 required fields |
| AC-10 | Loads `references/scaffold-schema.md` during Phase 5 | Output files match schema (correct file names, ID schemes, structural guarantees) |

## Test Scenarios

### Scenario 1: Full pipeline with WorkIQ
- **Input:** Project name + 3 SharePoint URLs + 1 Teams meeting link
- **Expected:** All 7 phases execute; 9 files produced; user prompted at 3 gates; DISCOVERY.md contains WorkIQ search results
- **Validates:** AC-1, AC-5, AC-6, AC-10

### Scenario 2: Graceful degradation without WorkIQ
- **Input:** Project name + manual text paste (no URLs)
- **Expected:** Phase 1 accepts paste; Phase 2 skipped with note in DISCOVERY.md; Phases 3-6 produce valid scaffold (9 files)
- **Validates:** AC-8, AC-1, AC-2, AC-3

### Scenario 3: Cross-file link integrity
- **Input:** Any valid source set
- **Expected:** Phase 6 validates all links resolve; no dangling references; no bare-anchor cross-file refs
- **Validates:** AC-2, AC-3, AC-4

### Scenario 4: Consistency report with conflicting sources
- **Input:** Two documents that define the same term differently
- **Expected:** CONSISTENCY_REPORT.md contains AMB-* entry with both source SRC-* links and suggested resolution
- **Validates:** AC-7

### Scenario 5: Meeting transcript extraction
- **Input:** Project name + local .vtt transcript file
- **Expected:** DECISIONS.md contains DEC-* entries extracted from transcript; ACTIVITIES.md contains ACT-* action items with owner/deadline from transcript
- **Validates:** AC-6, AC-9
