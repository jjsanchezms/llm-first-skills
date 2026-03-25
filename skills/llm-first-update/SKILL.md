---
name: llm-first-update
description: >
  Evolve existing LLM-First projects with new information from documents, meetings, or data.
  Ingests new sources, matches to existing entities, produces a change delta for user approval,
  and applies approved changes while maintaining ID continuity and cross-file integrity.
  WHEN: new meeting happened, new document to incorporate, update project, evolve project,
  ingest new source, what changed, incorporate feedback, add new information, project update,
  new transcript, merge new data into project.
---

# /llm-first-update — LLM-First Project Evolution Skill

## Purpose

LLM-First projects are living knowledge bases. After `/llm-first-init` creates the scaffold, new information arrives — meetings happen, documents are updated, decisions are made. This skill ingests new sources into an **existing** project while preserving stable IDs, maintaining cross-file integrity, and surfacing what changed.

The core output is a **change delta** — a structured diff showing proposed additions, modifications, and resolutions, traced to the new source, presented for user approval before any files are touched.

## Relationship to Other Skills

| Concern | `/llm-first-init` | `/llm-first-update` | `/llm-first-audit` | `/llm-first-reporting` |
|---------|-------------------|---------------------|---------------------|------------------------|
| Purpose | Create project from scratch | Evolve project with new information | Audit methodology compliance | Generate human-readable reports |
| Starting point | No project exists | Project exists with stable IDs | Project exists | Project exists |
| Sources | All sources at once | New/incremental sources | Existing project files | Existing project files |
| Output | Create all files | Merge into existing files | AUDIT_REPORT.md | Human-readable report |
| IDs | Assign from scratch | Continue sequence, reuse existing | Read-only | Read-only |
| Modifies project | Yes — creates all files | Yes — updates existing files | No — read-only + audit report | No — read-only + report file |

## Methodology

This skill implements [LLM-First Specification](https://github.com/gim-home/llm-first-specs).
The methodology repo is the authoritative reference; this skill references it, never duplicates it.

**Core Principles Applied:**
1. **Stable Identifiers** — Reuse existing IDs for known entities; assign next-in-sequence for new ones
2. **Explicit Relationships** — All new connections are navigable markdown links
3. **Consistent Structure** — New entries follow the same patterns as existing ones
4. **Projection Pattern** — Change delta is itself a projection for human review

**Failure Modes Prevented:**
- FM-1: Duplicate/unstable identifiers → Match before create; continue ID sequences
- FM-2: Implicit relationships → New links use full-path cross-file format
- FM-3: Overloaded definitions → Detect when new source uses term differently than GLOSSARY.md
- FM-5: Mixing truth with drafts → Source attribution on every change
- FM-8: No verification loop → Structural validation after applying changes

## Pipeline

The skill executes 8 phases sequentially (Phase 0 + 7 pipeline phases), pausing for user confirmation at gates.

### Phase 0: LOAD METHODOLOGY
**Trigger:** Skill invoked
**Actions:**
- Fetch the methodology repo content from [gim-home/llm-first-specs](https://github.com/gim-home/llm-first-specs) using `github-mcp-server-get_file_contents`
- **Access gate:** Attempt to read `README.md` from `owner: gim-home, repo: llm-first-specs`. If this fails (404, auth error), **STOP immediately** and tell the user:
  > ⛔ Cannot access the LLM-First Specification methodology repo (`gim-home/llm-first-specs`).
  > This skill requires the methodology as loaded context. Please authenticate to the `gim-home` GitHub EMU org and retry.
  > Run `gh auth login` and sign in with your `@microsoft.com` EMU account.
- **Fetch and hold in context** the following files (all from `owner: gim-home, repo: llm-first-specs`):
  - `WHITEPAPER_LLM_Driven_Specification.md` — Core methodology, principles, failure modes
  - `CASE_STUDY_1_SovereignAgent.md` — Example: specs as queryable knowledge
  - `CASE_STUDY_2_MultiTeam.md` — Example: multi-team coordination
  - `CASE_STUDY_3_Documentation.md` — Example: documentation at scale
  - `CASE_STUDY_4_Methodology.md` — Example: methodology capture
  - `CASE_STUDY_5_InContextData.md` — Example: SQL in-context data
  - `references/methodology.md` — Engagement methodology reference
  - `references/structured-data-and-llm-grounding.md` — Research: why structure reduces hallucination
**Output:** Methodology context loaded
**Gate:** None — proceeds automatically (or stops if access check fails)

### Phase 1: READ PROJECT
**Trigger:** Phase 0 complete
**Actions:**
- Read ALL markdown files in the target project directory
- Build a complete project index:
  - **Entity index:** All ENT-* (people, teams, systems) with names, roles, aliases
  - **Activity index:** All ACT-* with owners, statuses, evidence, sources
  - **Decision index:** All DEC-* with dates, deciders, what they affect
  - **Source index:** All SRC-* with types, dates, retrieval status
  - **Glossary index:** All DEF-* with canonical definitions
  - **Consistency index:** All CON-*, AMB-*, GAP-* with resolution status
  - **Discovery index:** All DISC-* with triage decisions
  - **Relationship map:** Cross-file link graph
- Determine current ID high-water marks (e.g., ENT-P008, ACT-022, DEC-007, SRC-009)
- Present project summary to user: file count, entity counts, status distribution
**Output:** Project context loaded with full index
**Gate:** User confirms correct project → proceed to Phase 2

### Phase 2: INGEST SOURCE
**Trigger:** Phase 1 complete
**Actions:**
- Accept new source(s): meeting transcript, document link, text paste, local file
- Retrieve content via WorkIQ MCP tool if URL provided (`workiq ask -q "..." -f "URL"`)
- For Teams meetings: use WorkIQ to get transcript/summary (`workiq ask -q "What was discussed in [meeting] on [date]? Include decisions, action items, updates"`)
- For local files (.vtt, .md, .docx summaries): read directly
- Assign next SRC-* ID (e.g., SRC-010)
- Catalog: type, title, date, participants, retrieval method
**Output:** New source content loaded and cataloged
**Gate:** User confirms source content is complete → proceed to Phase 3

### Phase 3: ANALYZE
**Trigger:** Phase 2 complete
**Actions:**
- Compare new source content against the project index from Phase 1
- For each piece of information in the new source, classify as:

  **Confirmations** — Information that validates existing entries without changing them
  - Match mentioned people/teams/systems to existing ENT-* entries
  - Match discussed topics to existing ACT-*, DEC-* entries
  - Note: confirmations strengthen confidence but don't modify files

  **Status changes** — Existing entries whose state has changed
  - Activities that moved status (e.g., Not Started → In Progress)
  - Decisions that were modified, superseded, or reinforced
  - Consistency items (AMB-*, GAP-*, CON-*) that were partially or fully resolved

  **New entries** — Information not captured in any existing entry
  - New people, teams, or systems mentioned (→ new ENT-*)
  - New action items assigned (→ new ACT-*)
  - New decisions made (→ new DEC-*)
  - New terms requiring definition (→ new DEF-*)

  **Conflicts** — New source contradicts existing entries
  - A decision is reversed or changed
  - A status claimed doesn't match existing evidence
  - A definition used differently than GLOSSARY.md

- For each proposed change, extract **supporting quotes** from the new source
**Output:** Raw change analysis with evidence
**Gate:** None — proceeds to Phase 4

### Phase 4: SCOPE
**Trigger:** Phase 3 complete
**Actions:**
- Present each proposed change to the user with:
  - **What would change** (existing entry + proposed modification)
  - **Supporting evidence** (quote from new source)
  - **Project relevance question** — Is this a project concern or out of scope?
- User approves, rejects, or modifies each change:
  - ✅ Approve — include in delta
  - ❌ Reject — exclude (e.g., "that's a personal goal, not project-related")
  - ✏️ Modify — adjust the proposed change (e.g., "keep Not Started, the meeting hasn't happened yet")
- Group changes by type for efficient review:
  1. New source to add
  2. Decision updates / new decisions
  3. Activity status changes / new activities
  4. Consistency items resolved or progressed
  5. New entities / glossary terms
  6. Conflicts to address
**Output:** User-approved change set
**Gate:** User confirms final set → proceed to Phase 5

### Phase 5: DELTA
**Trigger:** Phase 4 complete (user approved changes)
**Actions:**
- Produce the final **change delta** document:

  ```
  ## Change Delta — [Source Title] ([Date])

  **Source:** SRC-XXX — [title], [type], [date]

  ### Decisions
  | ID | Change | Detail | Evidence |
  |----|--------|--------|----------|

  ### Activities
  | ID | Change | Detail | Evidence |
  |----|--------|--------|----------|

  ### Consistency Items
  | ID | Change | Detail | Evidence |
  |----|--------|--------|----------|

  ### New Entries
  | File | ID | Description |
  |------|----|-------------|

  ### No Change (Confirmed)
  | ID | What was confirmed |
  |----|-------------------|
  ```

- Each row includes: the ID, what changed, the detail, and the supporting quote from the new source
- Present delta to user as final review
**Output:** Structured change delta
**Gate:** User confirms delta is correct → proceed to Phase 6

### Phase 6: APPLY
**Trigger:** Phase 5 complete (user confirmed delta)
**Actions:**
- Apply approved changes to project files:

  **SOURCES.md** — Add new SRC-* entry with full metadata

  **DECISIONS.md** — For updated decisions:
  - Update the existing DEC-* entry (add new source link, update fields that changed)
  - Preserve original decision text; add "Updated" note with date and new source
  - For new decisions: append DEC-* entry following existing format exactly

  **ACTIVITIES.md** — For status changes:
  - Update Status field
  - Add new source to Source field
  - For new activities: append ACT-* entry following existing format; use next-in-sequence ID

  **CONSISTENCY_REPORT.md** — For resolved/progressed items:
  - Update status from Open → Progressing or Resolved
  - Add resolution note with source attribution

  **ENTITIES.md** — For new entities (if any):
  - Append entry following existing format; use next-in-sequence ID

  **GLOSSARY.md** — For new definitions (if any):
  - Append entry following existing format; use next-in-sequence ID

  **RELATIONSHIPS.md** — Update if new relationships were created

  **DISCOVERY.md** — Update if new discovery was performed

  **Format rules:**
  - Every new entry gets a stable ID with `{#anchor}`
  - Every cross-file reference uses full-path format `[ID](FILE.md#anchor)`
  - New entries follow the exact structural pattern of existing entries in the same file
  - ID sequences continue from the current high-water mark (never reuse, never skip)
**Output:** Updated project files
**Gate:** Proceeds to Phase 7

### Phase 7: VERIFY
**Trigger:** Phase 6 complete
**Actions (automatic):**
- Run the same structural validation as `/llm-first-init` Phase 6:
  - Check all cross-file links resolve to existing anchors
  - Check all entities have stable IDs with anchors
  - Check no bare-anchor cross-file references exist
  - Check every ACT-* has: owner, status, evidence field, source link
  - Check no dangling references
- Additionally verify update-specific invariants:
  - No duplicate IDs were created
  - ID sequences are contiguous (no gaps, no reuse)
  - Updated entries still have valid cross-file links
  - New source (SRC-*) is referenced by at least one changed entry
- Report validation results
**Output:** Validation summary (pass/fail with details)
**Gate:** If issues found, fix automatically or report to user

## Inputs

| Input Type | How Provided | Retrieval |
|-----------|-------------|-----------|
| Target project directory | User specifies path | Filesystem read |
| Meeting transcript/summary | Teams meeting link or date/participants | WorkIQ query |
| Document link | SharePoint/OneDrive URL | WorkIQ `-f` flag |
| Transcript file | Local .vtt file | Direct file read |
| Free text | Meeting notes, verbal summary | User input (paste) |
| ADO updates | Work item IDs | WorkIQ ADO search |

## Outputs

The skill modifies existing project files in-place. No new files are created (unless the project is missing an expected file, in which case the skill reports this and defers to `/llm-first-init`).

The change delta (Phase 5) can optionally be saved as `CHANGELOG.md` or appended to an existing changelog if the user requests it.

## Non-Goals

- Does NOT create projects from scratch — that's `/llm-first-init`
- Does NOT audit methodology compliance — that's `/llm-first-audit`
- Does NOT generate human-readable reports — that's `/llm-first-reporting`
- Does NOT make scoping decisions — presents options, user decides
- Does NOT auto-apply changes without user approval — delta review is mandatory
- Does NOT modify source documents or external systems
- Does NOT duplicate the methodology — references it

## Guardrails

- **ID continuity:** Never reuse, skip, or duplicate an ID. Continue from high-water mark.
- **Source attribution:** Every change traces to the new SRC-* entry
- **User approval gate:** No file modifications before delta approval (Phase 4 + Phase 5)
- **Evidence-backed changes:** Every proposed status change or decision update includes supporting quotes from the new source
- **Scope filtering:** Explicitly ask user whether each change is project-relevant before including
- **Format preservation:** New entries match the exact structural pattern of existing entries
- **Graceful degradation without WorkIQ:**
  - Phase 2: Accept manual content paste instead of URL retrieval
  - Phase 3-7: Proceed normally with available content

## Reference Examples

The [LLM-First Specification](https://github.com/gim-home/llm-first-specs) repo contains case studies that demonstrate the methodology principles applied in practice:
- [Case Study 1: SovereignAgent](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_1_SovereignAgent.md) — Specs as queryable knowledge (demonstrates stable ID reuse)
- [Case Study 2: Multi-Team](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_2_MultiTeam.md) — Multi-team coordination (demonstrates incremental updates)

These are loaded into context at runtime via Phase 0.
