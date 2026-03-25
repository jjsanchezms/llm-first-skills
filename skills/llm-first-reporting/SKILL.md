---
name: llm-first-reporting
description: >
  Generate human-readable reports from LLM-First projects.
  Produces prose-first documents with minimal bracket references for agent traceability.
  WHEN: status report, executive summary, team briefing, progress update, project summary,
  human-readable view, audience-specific projection, reformat audit report,
  generate status brief, create executive summary.
---

# /llm-first-reporting — Human-Readable Report Generation

## Purpose

LLM-First structured files are optimized for agent comprehension: inline IDs, full-path cross-file links, anchors on every entity. Humans need readable prose. This skill bridges the gap — it reads structured project files and generates reports that prioritize human readability while preserving lightweight traceability for the agent round-trip.

## Formatting Convention

Load `references/formatting-conventions.md` for the full rules. The key principles:

- **Prose first** — write for human readers; natural language, not database dumps
- **Bracket tags sparingly** — use `[ACT-023]` only where a human might comment or want to trace back
- **No inline links** — never `[ACT-023](ACTIVITIES.md#ACT-023)` in the report body
- **Tags are for the agent** — when the report is fed back, the agent resolves bracket tags to structured entries

### Round-Trip Flow

```
Structured files ──→ /llm-first-reporting ──→ Human-readable report
                                                      │
                                                      ▼
                                              Human reads & annotates
                                                      │
                                                      ▼
                                              Feed back to agent
                                                      │
                                                      ▼
                                        Agent resolves [ACT-023] → ACTIVITIES.md#ACT-023
                                        Agent updates structured files
```

## Report Types

| Type | Description | Typical Audience |
|------|-------------|-----------------|
| **Status Brief** | Project status snapshot — what's on track, what's blocked, what needs attention | Leadership, stakeholders |
| **Executive Summary** | High-level project overview — goals, scope, key findings, recommendations | Executives, sponsors |
| **Team Briefing** | Focused view for a specific team or workstream — their activities, blockers, dependencies | Team leads, ICs |
| **Progress Report** | What changed since a reference point — completed items, new blockers, emerging risks | Project managers, stakeholders |
| **Audit Summary** | Human-readable reformatting of an AUDIT_REPORT.md — scores, findings, actions needed | Anyone reviewing audit results |

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
- Load `references/formatting-conventions.md` for output formatting rules
**Output:** Methodology context loaded, formatting conventions loaded
**Gate:** None — proceeds to Phase 1 (or stops if access check fails)

### Phase 1: READ PROJECT
**Trigger:** Phase 0 complete
**Actions:**
- Read all markdown files in the target project directory
- Build an inventory of: entities (ENT-*), activities (ACT-*), decisions (DEC-*), definitions (DEF-*), sources (SRC-*), consistency items (CON-*, AMB-*, GAP-*)
- Identify project status: which activities are complete, in progress, blocked
- If AUDIT_REPORT.md exists and report type is "Audit Summary", read and parse it
**Output:** Project context loaded
**Gate:** None — proceeds to Phase 2

### Phase 2: AUDIENCE & TYPE
**Trigger:** Phase 1 complete
**Actions:**
- Ask user: What type of report? (status brief, executive summary, team briefing, progress report, audit summary)
- Ask user: Who is the audience? (e.g., "VP of Engineering", "ServiceTree migration team", "external auditors")
- Ask user: Any specific focus areas? (optional — e.g., "focus on blocked items", "highlight decisions from last week")
- If "progress report", ask: What is the reference point? (e.g., "since last week", "since the last STATUS_BRIEF.md")
**Output:** Report parameters captured
**Gate:** None — proceeds to Phase 3

### Phase 3: GENERATE
**Trigger:** Phase 2 complete
**Actions:**
- Generate the report following formatting conventions:
  - Write in natural prose, structured with clear headers
  - Use bracket tags `[ACT-023]` sparingly — only on items a reader might want to comment on or trace
  - Never use full markdown links in the body
  - Tailor language and detail level to the stated audience
  - Prioritize: what matters to this audience → what's changed → what needs action
- For each report type, follow the structure defined in `references/formatting-conventions.md`
**Output:** Draft report
**Gate:** Present draft to user → user reviews

### Phase 4: REVIEW
**Trigger:** Phase 3 complete
**Actions:**
- Present the generated report to the user
- Accept feedback and iterate:
  - "Too detailed" → condense
  - "Missing X" → add coverage
  - "Wrong tone" → adjust for audience
  - "Add more/fewer bracket tags" → adjust traceability density
- When user approves, write the final report to the project directory
**Output:** Final report file written
**Gate:** User confirms → done

## Inputs

| Input | Required | Description |
|-------|----------|-------------|
| Target directory | Yes | Path to the LLM-First project |
| Report type | Prompted | One of: status brief, executive summary, team briefing, progress report, audit summary |
| Audience | Prompted | Description of who will read the report |
| Focus areas | No | Specific topics, entities, or activities to emphasize |
| Reference point | If progress report | When to measure progress from |

## Outputs

| Report Type | Output File | Placement |
|-------------|-------------|-----------|
| Status Brief | `STATUS_BRIEF.md` | Project directory |
| Executive Summary | `EXECUTIVE_SUMMARY.md` | Project directory |
| Team Briefing | `TEAM_BRIEFING_<team>.md` | Project directory |
| Progress Report | `PROGRESS_REPORT.md` | Project directory |
| Audit Summary | `AUDIT_SUMMARY.md` | Project directory |

## Non-Goals

- Does NOT modify structured project files — read-only on project data
- Does NOT create or update entities, activities, or decisions
- Does NOT replace `/llm-first-audit` — that skill performs the analysis; this skill can reformat its output
- Does NOT generate LLM-optimized files — that's `/llm-first-init`'s job

## Relationship to Other Skills

| Concern | `/llm-first-init` | `/llm-first-audit` | `/llm-first-reporting` |
|---------|-------------------|---------------------|------------------------|
| Purpose | Create structured project scaffold | Audit methodology compliance | Generate human-readable reports |
| Output format | LLM-optimized (IDs, links, anchors) | LLM-optimized with formatting conventions | Human-optimized (prose, bracket tags) |
| Audience | Agents, LLMs | Agents, methodology reviewers | Humans — executives, teams, stakeholders |
| Modifies project | Yes — creates all files | No — read-only + AUDIT_REPORT.md | No — read-only + report file |

## Reference Examples

The [LLM-First Specification](https://github.com/gim-home/llm-first-specs) repo contains case studies that demonstrate the Projection Pattern (Principle 4) — the foundation for this skill:
- [Case Study 3: Documentation at Scale](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_3_Documentation.md) — Multi-audience views from structured source
- [Case Study 4: Methodology Capture](https://github.com/gim-home/llm-first-specs/blob/main/CASE_STUDY_4_Methodology.md) — Audience-specific projections

These are loaded into context at runtime via Phase 0.
