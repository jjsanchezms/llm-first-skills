# Acceptance Criteria — llm-first-audit

## Must-Pass Criteria

| # | Criterion | How to Verify |
|---|-----------|---------------|
| AC-1 | Produces `AUDIT_REPORT.md` in the target directory | File exists after skill completes |
| AC-2 | Report contains an Alignment Scorecard with all 7 principles scored 1-5 | Check report has 7 rows, each with numeric score and evidence text |
| AC-3 | Report contains Failure Mode Assessment with all 10 modes rated | Check report has 10 items each rated PROTECTED, PARTIALLY PROTECTED, or VULNERABLE |
| AC-4 | Report contains Structural Issues section with specific findings | Section present; if no issues found, explicitly states "No structural issues found" |
| AC-5 | Report contains Improvement Opportunities ranked by impact | Each opportunity tagged High/Medium/Low |
| AC-6 | Skill is read-only — no project files modified or created (except AUDIT_REPORT.md) | Compare file checksums before/after audit |
| AC-7 | Works on projects NOT created by `/llm-first-init` | Run against a plain markdown project with no LLM-First structure |
| AC-8 | Loads `references/evaluation-criteria.md` during execution | Criteria from all 4 dimensions (A–D) reflected in report |

## Test Scenarios

### Scenario 1: Audit an llm-first-init scaffold
- **Input:** Any project directory scaffolded by `/llm-first-init` (10 markdown files with stable IDs, cross-file links, and structural guarantees)
- **Expected:** High scores (4-5) on most principles, most failure modes PROTECTED, few structural issues
- **Validates:** AC-1, AC-2, AC-3, AC-4, AC-5

### Scenario 2: Audit a plain markdown project
- **Input:** A directory with 3 markdown files, no stable IDs, no cross-file links
- **Expected:** Low scores (1-2) on principles, most failure modes VULNERABLE, many improvement opportunities
- **Validates:** AC-7, AC-2, AC-3, AC-5

### Scenario 3: Audit a project with broken links
- **Input:** A scaffold where some cross-file links point to non-existent anchors
- **Expected:** Structural Issues section lists each broken link with file and line
- **Validates:** AC-4, AC-8

### Scenario 4: Read-only guarantee
- **Input:** Any project directory
- **Expected:** Only `AUDIT_REPORT.md` is created; all other files unchanged
- **Validates:** AC-6
