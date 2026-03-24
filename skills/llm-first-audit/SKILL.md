# /llm-first-audit — LLM-First Methodology Compliance Audit

> Audit any project against the LLM-First Specification methodology.
> Identify principle misalignment, failure mode vulnerabilities, and structural issues.
> Produce actionable improvement recommendations ranked by impact.

## When to Use

Use `/llm-first-audit` when:
- After `/llm-first-init` — to deep-audit the generated scaffold
- After manual edits — to verify structural integrity wasn't degraded
- Periodically — to catch drift over time (the "verification loop" from the methodology)
- Before a milestone — to ensure the project is methodology-compliant
- On any project — works on projects not created by `/llm-first-init`

## Methodology

This skill audits against [LLM-First Specification](https://github.com/gim-home/llm-first-specs).
The methodology repo is the authoritative reference.

## What It Evaluates

### A. Core Principles Compliance (scored 1-5)
1. **Stable Identifiers** — Does every important concept have a stable ID? Consistent format? No fragile references (row numbers, section numbers)?
2. **Explicit Relationships** — Are ALL relationships navigable markdown links? No prose descriptions masquerading as relationships? Full-path cross-file format?
3. **Consistent Structure** — Predictable patterns? Consistent header hierarchy? Parseable by an LLM?
4. **Projection Pattern** — Can audience-specific views be generated? Does at least one projection exist?
5. **Markdown as Database** — IDs as primary keys? Links as foreign keys? Schema documented?
6. **Verification Loop** — Is verification repeatable? Are there prompts/checklists for re-running checks?
7. **Definitions as First-Class** — Every important term defined? Ambiguities surfaced? Source attribution?

### B. Failure Mode Vulnerability (10 checks)
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

### C. Structural Integrity
- All cross-file links resolve to existing anchors
- No bare-anchor cross-file references
- No orphaned entities (defined but never referenced)
- No dangling references (referenced but never defined)
- Consistent anchor format (`{#id}` pattern)
- Every activity has: owner, status, evidence field
- Every decision has: date, source, participants

### D. Case Study Pattern Alignment
- Specs as Queryable Knowledge (CS1)
- Markdown as Database / POR pattern (CS2)
- Multi-Audience Views (CS3)
- Methodology Capture with exit criteria (CS4)
- SQL/structured data in context (CS5)

## Pipeline

### Phase 1: SCAN
- Read all markdown files in the target directory
- Build an inventory of: files, IDs, anchors, cross-file links, entity types
- Identify the ID schemes in use

### Phase 2: STRUCTURAL CHECK
- Validate all cross-file links resolve
- Find bare-anchor cross-file references
- Find orphaned entities and dangling references
- Check anchor format consistency
- Check required fields on activities, decisions, entities

### Phase 3: PRINCIPLE ALIGNMENT
- Score each of the 7 principles (1-5) with evidence
- For each score < 5, identify specific gaps

### Phase 4: FAILURE MODE ASSESSMENT
- Evaluate each of the 10 failure modes
- Rate: PROTECTED / PARTIALLY PROTECTED / VULNERABLE
- For VULNERABLE items, provide specific remediation

### Phase 5: REPORT
Generate `AUDIT_REPORT.md` with:
1. **Alignment Scorecard** — Table with scores and evidence
2. **Failure Mode Assessment** — 10 items with ratings and explanations
3. **Structural Issues** — Specific broken links, missing anchors, inconsistencies
4. **Improvement Opportunities** — Ranked by impact (High/Medium/Low) with examples
5. **What the Project Does Well** — Novel patterns, strong implementations
6. **Recommended Changes** — Actionable next steps

## Inputs

| Input | Required | Description |
|-------|----------|-------------|
| Target directory | Yes | Path to the project to audit |
| Methodology reference | No | Path or URL to LLM-First Specs repo (defaults to `https://github.com/gim-home/llm-first-specs`) |

## Outputs

| File | Content |
|------|---------|
| `AUDIT_REPORT.md` | Full methodology compliance audit (placed in target directory) |

## Non-Goals

- Does NOT modify project files — read-only audit
- Does NOT auto-fix issues — reports them for human decision
- Does NOT replace human judgment — provides structured analysis
- Does NOT audit content quality — only structural/methodology compliance

## Relationship to `/llm-first-init`

| Concern | `/llm-first-init` (built-in Phase 6) | `/llm-first-audit` |
|---------|--------------------------------------|---------------------|
| Scope | Structural validation only | Full methodology audit |
| When | Automatically at scaffold creation | On-demand, anytime |
| Checks | Links resolve, anchors exist, required fields present | Principle alignment, failure modes, case study patterns |
| Output | Pass/fail with fix list | Comprehensive AUDIT_REPORT.md |
| Re-runnable | Only during creation | Yes — run after any edit |

## Reference

See [ServiceTreeAudit/AUDIT_REPORT.md](../../examples/) for an example audit output.
