---
name: llm-first-audit
description: >
  Audit any project against the LLM-First Specification methodology.
  Scores principle alignment, identifies failure mode vulnerabilities, and checks structural integrity.
  WHEN: audit project, check methodology compliance, verify LLM-first structure,
  validate scaffold, post-edit verification, methodology drift check, before milestone,
  catch structural drift, works on any project.
---

# /llm-first-audit — LLM-First Methodology Compliance Audit

## Methodology

This skill audits against [LLM-First Specification](https://github.com/gim-home/llm-first-specs).
The methodology repo is the authoritative reference.

## What It Evaluates

Four evaluation dimensions — load `references/evaluation-criteria.md` for full checklists:
- **A. Core Principles Compliance** — 7 principles scored 1-5 with evidence
- **B. Failure Mode Vulnerability** — 10 failure modes rated PROTECTED / PARTIALLY PROTECTED / VULNERABLE
- **C. Structural Integrity** — Cross-file links, orphaned entities, required fields
- **D. Case Study Pattern Alignment** — 5 case study patterns from the methodology

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

See [ServiceTreeAudit/AUDIT_REPORT.md](https://github.com/gim-home/llm-first-skills/tree/main/examples/ServiceTreeAudit) for an example audit output.
