# /llm-first-init — LLM-First Project Scaffolding Skill

> Create new projects that are LLM-First by default.
> Scaffold structure, invariants, and traceability — not content.
> Make projects safe, comprehensible, and reusable for BOTH humans and agents.

## When to Use

Use `/llm-first-init` when:
- Starting a new project from scattered sources (docs, meetings, data)
- Onboarding to an existing project that lacks structure
- A key person is leaving and knowledge must be captured
- Multiple teams need to coordinate with shared vocabulary
- An external audience (audit, leadership, customers) needs traceable evidence

## Methodology

This skill implements [LLM-First Specification](https://github.com/gim-home/llm-first-specs).
The methodology repo is the authoritative reference; this skill references it, never duplicates it.

**Core Principles Applied:**
1. **Stable Identifiers** — Every entity gets a unique, immutable ID (`DEF-*`, `ENT-*`, `ACT-*`, `DEC-*`, `SRC-*`)
2. **Explicit Relationships** — All connections are navigable markdown links, never prose
3. **Consistent Structure** — Predictable patterns enabling semantic comprehension
4. **Projection Pattern** — Multiple audience views generated from single source of truth

**Failure Modes Prevented:**
- FM-1: Missing/unstable identifiers → Stable IDs on everything
- FM-2: Implicit relationships → Full-path cross-file links
- FM-3: Overloaded definitions → Ambiguity surfacing with AMB-* items
- FM-5: Mixing truth with drafts → Canonical source declaration
- FM-6: Word/Loop in authoring path → Markdown as POR
- FM-7: Missing projections → At least one audience view generated
- FM-8: No verification loop → Built-in structural validation + verification prompts

## Pipeline

The skill executes 6 phases sequentially, waiting for user confirmation at gates.

### Phase 1: INTAKE
**Trigger:** User provides project name + source links
**Actions:**
- Accept links to documents (SharePoint, OneDrive), meetings (Teams), data (Excel, ADO), images, transcripts
- Retrieve content via WorkIQ MCP tool (`workiq ask -q "..." -f "URL"`)
- For .vtt transcript files: read directly from local filesystem
- Catalog each source with: stable SRC-* ID, type, title, location, date, retrieval status, content summary
**Output:** Source catalog (will become SOURCES.md)
**Gate:** User confirms sources are complete → proceed to Phase 2

### Phase 2: DISCOVER
**Trigger:** Phase 1 complete
**Actions:**
- Extract entities (people, teams, systems, concepts) and keywords from Phase 1 sources
- Run WorkIQ searches:
  - Related documents by keywords and people names
  - Related ADO work items by keywords, area paths, assigned-to
  - Related communications (email, chat, meetings) by keywords
- Classify discovered sources by relevance:
  - 🔴 **High** — Directly addresses a gap or provides missing definitions
  - 🟡 **Medium** — Provides context, background, or related governance
  - 🟢 **Low** — Reference only, not needed for scaffold
- Present triage table to user
**Output:** Discovery log (will become DISCOVERY.md)
**Gate:** User selects which discoveries to include → fetch selected → proceed to Phase 3

### Phase 3: ANALYZE
**Trigger:** Phase 2 complete (all sources ingested)
**Actions:**
- For each source, extract along 5 dimensions:
  - **Context** — What type of work, who is involved
  - **Intent** — What problem is being solved, undocumented assumptions
  - **Structure** — What is structured vs. implicit
  - **Friction** — Where an LLM or new person would struggle
  - **Reusability** — What should be captured once and reused
- For meeting transcripts, extract:
  - Decisions (who decided, what, when, why, what it affects)
  - Action items (owner, task, deadline)
  - Disputed items (who disputes, rationale)
  - Context/background not in other sources
**Output:** Analysis artifacts (feeds Phases 4 and 5)
**Gate:** None — proceeds automatically to Phase 4

### Phase 4: CONSISTENCY CHECK
**Trigger:** Phase 3 complete
**Actions:**
- Cross-reference ALL sources to identify:
  - **Conflicts (CON-*)** — Sources contradict each other
  - **Ambiguities (AMB-*)** — Terms used without shared definition
  - **Gaps (GAP-*)** — Required information not found in any source
- Each item gets: stable ID, severity (Critical/High/Medium/Low), affected sources with SRC-* links, suggested resolution path, proposed owner
- Present CONSISTENCY_REPORT to user
**Output:** CONSISTENCY_REPORT.md
**Gate:** User reviews report → resolves critical items or acknowledges them → proceed to Phase 5

### Phase 5: SCAFFOLD
**Trigger:** Phase 4 complete (user confirmed)
**Actions:**
Generate the following files in the target directory:

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

**Structural guarantees enforced:**
- Every entity has a stable ID with `{#anchor}`
- Every cross-file reference uses full-path format `[ID](FILE.md#anchor)`
- Every activity links to its originating commitment and source
- Every decision links to its source meeting/document
- Every status claim has an evidence field (even if empty)
- Canonical source declaration present
- Methodology reference present (link, not duplication)
- Exit criteria section present

**Output:** Complete project scaffold
**Gate:** Proceeds to Phase 6

### Phase 6: VALIDATE
**Trigger:** Phase 5 complete
**Actions (automatic):**
- Check all cross-file links resolve to existing anchors
- Check all entities have stable IDs with anchors
- Check no bare-anchor cross-file references exist
- Check every ACT-* has: owner, status, evidence field, MAP/source link
- Check no dangling references (mentioned in prose but no entity entry)
- Report structural issues found
**Output:** Validation summary (pass/fail with details)
**Gate:** If issues found, fix automatically or report to user

## Inputs

| Input Type | How Provided | Retrieval |
|-----------|-------------|-----------|
| Document links | SharePoint/OneDrive URLs | WorkIQ `-f` flag |
| Meeting links | Teams recording URLs | WorkIQ meeting search |
| Transcript files | Local .vtt files | Direct file read |
| ADO references | Work item IDs or keywords | WorkIQ ADO search |
| Images | Local files | Direct file read |
| Free text | Project name, description, key people | User input |
| Existing files | Local markdown, code, configs | Filesystem read |

## Outputs

All outputs are markdown following [LLM-First principles](https://github.com/gim-home/llm-first-specs/blob/main/WHITEPAPER_LLM_Driven_Specification.md):
- Stable IDs as primary keys
- Markdown links as foreign keys
- Consistent structural patterns
- The LLM is the query engine

## Non-Goals

- Does NOT generate project deliverables (reports, code, plans)
- Does NOT replace domain expertise
- Does NOT manage ongoing execution (sprints, status updates)
- Does NOT modify source documents or external systems
- Does NOT make decisions — surfaces information for humans to decide
- Does NOT duplicate the methodology — references it

## Guardrails

- Every output artifact traces to at least one input source
- No entity created without source citation
- Consistency report presented before scaffold finalized
- Discovery results user-triaged (not auto-included)
- Graceful degradation if WorkIQ unavailable:
  - Phase 1: Accept manual content paste instead of URL retrieval
  - Phase 2: Skip discovery, note limitation in DISCOVERY.md
  - Phases 3-6: Proceed normally with available sources

## Reference Implementation

See [ServiceTreeAudit](../../examples/) — a scaffold produced from 15 real-world sources for an internal audit remediation project.
