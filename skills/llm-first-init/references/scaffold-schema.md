# Scaffold Schema & Structural Guarantees

> Load this file during Phase 5 (SCAFFOLD) of the init pipeline.

## Output Files

| File | Content | ID Scheme |
|------|---------|-----------|
| `PROJECT.md` | Master index, methodology reference, canonical source declaration, exit criteria, verification prompts | — |
| `GLOSSARY.md` | Canonical definitions for all project terms; ambiguous terms flagged with ⚠️ pointing to AMB-* entries | `DEF-*` |
| `ENTITIES.md` | People, teams, systems, artifacts with roles and relationships | `ENT-*` |
| `ACTIVITIES.md` | Work items / action items with owner, status, evidence, dependencies | `ACT-*` |
| `RELATIONSHIPS.md` | Explicit link map — navigable markdown (no code-block trees) | — |
| `DECISIONS.md` | Strategic decisions from meetings and documents with rationale | `DEC-*` |
| `SOURCES.md` | Catalog of all input sources with retrieval metadata | `SRC-*` |
| `DISCOVERY.md` | Search log with triage decisions (included/excluded/deferred) | `DISC-*` |
| `CONSISTENCY_REPORT.md` | Conflicts, ambiguities, gaps with resolution status | `CON-*`, `AMB-*`, `GAP-*` |
| `STATUS_BRIEF.md` | Audience-specific projection (at least one) | — |

## Structural Guarantees

These invariants MUST be enforced on every generated file:

- Every entity has a stable ID with `{#anchor}`
- Every cross-file reference uses full-path format `[ID](FILE.md#anchor)`
- Every activity links to its originating commitment and source
- Every decision links to its source meeting/document
- Every status claim has an evidence field (even if empty)
- Canonical source declaration present
- Methodology reference present (link, not duplication)
- Exit criteria section present
