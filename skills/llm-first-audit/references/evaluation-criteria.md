# Audit Evaluation Criteria

> Load this file during Phases 2–4 of the audit pipeline.

## A. Core Principles Compliance (scored 1-5)

1. **Stable Identifiers** — Does every important concept have a stable ID? Consistent format? No fragile references (row numbers, section numbers)?
2. **Explicit Relationships** — Are ALL relationships navigable markdown links? No prose descriptions masquerading as relationships? Full-path cross-file format?
3. **Consistent Structure** — Predictable patterns? Consistent header hierarchy? Parseable by an LLM?
4. **Projection Pattern** — Can audience-specific views be generated? Does at least one projection exist?
5. **Markdown as Database** — IDs as primary keys? Links as foreign keys? Schema documented?
6. **Verification Loop** — Is verification repeatable? Are there prompts/checklists for re-running checks?
7. **Definitions as First-Class** — Every important term defined? Ambiguities surfaced? Source attribution?

## B. Failure Mode Vulnerability (10 checks)

For each of the 10 failure modes from the [whitepaper](https://github.com/gim-home/llm-first-specs/blob/main/WHITEPAPER_LLM_Driven_Specification.md#lessons-learned):
- **PROTECTED** — The project actively prevents this failure mode
- **PARTIALLY PROTECTED** — Some protection but gaps exist
- **VULNERABLE** — The project is susceptible to this failure mode

Failure modes checked:
1. Missing or Unstable Identifiers
2. Implicit Relationships
3. Overloaded Definitions
4. Inconsistent Formatting or Structure
5. Mixing Authoritative Truth with Draft Brainstorming
6. Unstructured Word or Loop Documents in Authoring Path
7. Missing Projections for Complex Data
8. No Verification Loop
9. Shallow Definitions or Partial Schemas
10. Attempting Multi-step Reasoning Without Structure

## C. Structural Integrity

- All cross-file links resolve to existing anchors
- No bare-anchor cross-file references
- No orphaned entities (defined but never referenced)
- No dangling references (referenced but never defined)
- Consistent anchor format (`{#id}` pattern)
- Every activity has: owner, status, evidence field
- Every decision has: date, source, participants

## D. Case Study Pattern Alignment

- Specs as Queryable Knowledge (CS1)
- Markdown as Database / POR pattern (CS2)
- Multi-Audience Views (CS3)
- Methodology Capture with exit criteria (CS4)
- SQL/structured data in context (CS5)
