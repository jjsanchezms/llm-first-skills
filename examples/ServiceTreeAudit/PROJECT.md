# Service Tree Audit — FND-55727 Remediation {#project}

> **LLM-First Project** — Scaffolded 2026-03-24 via `/llm-first-init`
> This project is structured for both human and agent comprehension.
> Point your LLM agent at this directory — it can read and reason across all files.

**Methodology:** [LLM-First Specification](https://github.com/gim-home/llm-first-specs) — This project follows the LLM-First methodology. The methodology repo is the authoritative reference; it is not duplicated here.

## Project Summary

**Finding:** [FND-55727](#src-audit-report) — Service Tree Governance
**Risk Level:** Medium
**Enterprise Risk:** Software and Services Quality and Availability
**Issued:** September 19, 2024
**Deadline:** June 30, 2026 (FY26 end)
**Overall Rating:** Needs Moderate Improvement

**Problem:** The E+D organization lacks a comprehensive governance structure over Service Tree, resulting in incomplete and inaccurate metadata fields that undermine compliance, security, accountability, and incident response.

**Scope:** Five audit themes requiring remediation:
1. [Roles & Responsibilities](#dec-map-section-1)
2. [Entry Requirements for Service Tree](#dec-map-section-2)
3. [Periodic Review of Service Tree Entries](#dec-map-section-3)
4. [Service Tree Metadata Fields](#dec-map-section-4)
5. [Data Quality Monitoring](#dec-map-section-5)

## Project Artifacts

| Artifact | Purpose | Link |
|----------|---------|------|
| [GLOSSARY.md](GLOSSARY.md) | Canonical definitions for all project terms | `DEF-*` IDs |
| [ENTITIES.md](ENTITIES.md) | People, teams, systems, artifacts | `ENT-*` IDs |
| [RELATIONSHIPS.md](RELATIONSHIPS.md) | Explicit links between all entities | Navigable graph |
| [DECISIONS.md](DECISIONS.md) | Strategic decisions from meetings and docs | `DEC-*` IDs |
| [SOURCES.md](SOURCES.md) | Catalog of all input sources | `SRC-*` IDs |
| [DISCOVERY.md](DISCOVERY.md) | What was searched, found, included/excluded | `DISC-*` IDs |
| [CONSISTENCY_REPORT.md](CONSISTENCY_REPORT.md) | Conflicts, ambiguities, and gaps requiring resolution | `CON-*`, `AMB-*`, `GAP-*` IDs |
| [ACTIVITIES.md](ACTIVITIES.md) | All 22 remediation work items with stable IDs | `ACT-*` IDs |
| [STATUS_BRIEF.md](STATUS_BRIEF.md) | Audit-facing projection of current remediation status | Generated view |

## Canonical Source Declaration

As of 2026-03-24, this markdown scaffold is the **Plan of Record** for FND-55727 remediation. The original Word documents and Excel tracker ([SRC-MAP](SOURCES.md#src-map), [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker)) are historical inputs preserved as source references. All updates happen in this scaffold; Word/Excel files are not maintained.

## Key People

| Person | Role | Entity ID |
|--------|------|-----------|
| Brian Day | Departing owner, transitioning to Copilot Extensions/WorkIQ | [ENT-BRIAN](#ent-brian) |
| Daysha Carter | New primary owner | [ENT-DAYSHA](#ent-daysha) |
| JJ Sánchez | Operational/day-to-day support | [ENT-JJ](#ent-jj) |
| Chris Netz | Service Tree platform, data quality (ES365) | [ENT-CHRIS](#ent-chris) |
| Kaushik Pushpavanam | Service Tree governance (Azure Core) | [ENT-KAUSHIK](#ent-kaushik) |
| Andrew Sweeny | Granularity/entry requirements (ES365) | [ENT-ANDREW](#ent-andrew) |
| Ryan Zacher | Named finding owner in audit report | [ENT-RYAN](#ent-ryan) |

## Current Status (as of 2026-03-24)

- **MAP submitted:** Nov 2024 (60-day response to Sep 2024 finding)
- **Tracking cadence:** No regular check-ins for 16 months; resumed Feb 2026
- **Ownership transition:** Brian → Daysha + JJ (Mar 2026)
- **Audit team contact:** Not yet established by new owners
- **Items complete:** Several per tracker, but evidence not linked
- **Items at risk:** Row 7 (large services), Row 17 (policy engine) — flagged as unlikely to meet deadline
- **Disputed items:** Rows 14-15 flagged by Kaushik

## Exit Criteria for FND-55727 Closure {#exit-criteria}

- [ ] All ACT-* items are status COMPLETE, REPLACED, or ACCEPTED
- [ ] Evidence linked for every COMPLETE activity
- [ ] Evidence uploaded to [EGRC](ENTITIES.md#ent-sys-egrc)
- [ ] Audit team confirms acceptance (resolves [GAP-1](CONSISTENCY_REPORT.md#gap-1))
- [ ] All CON-* items RESOLVED
- [ ] All AMB-* items RESOLVED (canonical definitions agreed)
- [ ] All critical GAP-* items RESOLVED or ACCEPTED
- [ ] [STATUS_BRIEF.md](STATUS_BRIEF.md) regenerated and reviewed

## How to Use This Project

**For a new participant:**
1. Read this file (PROJECT.md) for orientation
2. Read [GLOSSARY.md](GLOSSARY.md) to understand terms
3. Read [CONSISTENCY_REPORT.md](CONSISTENCY_REPORT.md) to see what's unresolved
4. Read [DECISIONS.md](DECISIONS.md) to understand strategic choices made

**For an LLM agent:**
1. Load this directory as context
2. Use stable IDs to traverse: Finding → Commitment → Activity → Evidence
3. Use [RELATIONSHIPS.md](RELATIONSHIPS.md) for dependency graph traversal
4. Use [GLOSSARY.md](GLOSSARY.md) to resolve any ambiguous terms

**For audit preparation:**
1. Review [CONSISTENCY_REPORT.md](CONSISTENCY_REPORT.md) — resolve all CON-* and AMB-* items
2. Ensure every activity in [ACTIVITIES.md](ACTIVITIES.md) has evidence linked
3. Review [STATUS_BRIEF.md](STATUS_BRIEF.md) — the audit-facing projection

## Verification Prompts

Run these with your LLM agent to validate structural integrity:

1. "Check all cross-file links in this directory — do all [ID](FILE.md#anchor) targets exist?"
2. "Find entities mentioned in prose but without ENT-* entries in ENTITIES.md."
3. "List all ACT-* items in ACTIVITIES.md without evidence links."
4. "Are there any GLOSSARY terms used in other files that don't match their canonical definition?"
5. "Regenerate STATUS_BRIEF.md from the current ACTIVITIES.md and DECISIONS.md."
