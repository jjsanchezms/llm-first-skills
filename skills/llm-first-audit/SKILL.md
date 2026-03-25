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
- These files become the loaded reference for all subsequent pipeline phases (especially Phase 3: PRINCIPLE ALIGNMENT and Phase 4: FAILURE MODE ASSESSMENT)
**Output:** Methodology context loaded
**Gate:** None — proceeds automatically to Phase 1 (or stops if access check fails)

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
Generate `AUDIT_REPORT.md` following the formatting conventions from [`/llm-first-reporting`](../llm-first-reporting/SKILL.md):
- Write in natural prose, not raw data tables
- Use bracket tags `[ACT-023]` sparingly for traceable items
- No inline markdown links in the report body
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

## Relationship to Other Skills

| Concern | `/llm-first-init` (built-in Phase 6) | `/llm-first-audit` | `/llm-first-reporting` |
|---------|--------------------------------------|---------------------|------------------------|
| Scope | Structural validation only | Full methodology audit | Human-readable projections |
| When | Automatically at scaffold creation | On-demand, anytime | On-demand, after init or audit |
| Checks | Links resolve, anchors exist, required fields present | Principle alignment, failure modes, case study patterns | N/A — generates reports, not checks |
| Output | Pass/fail with fix list | Comprehensive AUDIT_REPORT.md | Prose-first reports (status brief, exec summary, etc.) |
| Re-runnable | Only during creation | Yes — run after any edit | Yes — regenerate anytime |

> **Tip:** Use `/llm-first-reporting` with report type "audit summary" to produce a human-friendly version of the AUDIT_REPORT.md generated by this skill.

## Reference Examples

The [LLM-First Specification](https://github.com/gim-home/llm-first-specs) repo contains case studies that exemplify good methodology compliance — use them as reference when scoring:
- [Case Study 1: SovereignAgent](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_1_SovereignAgent.md) — Specs as queryable knowledge
- [Case Study 2: MultiTeam](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_2_MultiTeam.md) — Multi-team coordination
- [Case Study 4: Methodology Capture](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_4_Methodology.md) — Methodology capture with exit criteria

These are loaded into context at runtime via Phase 0.
