# LLM-First Skills

Skills for [Agency Copilot CLI](https://docs.github.com/copilot/how-tos/copilot-cli) that scaffold and audit projects using the [LLM-First Specification methodology](https://github.com/gim-home/llm-first-specs).

## Skills

### `/llm-first-init` — Project Scaffolding
Creates LLM-First projects from real-world inputs (documents, meetings, data).
Produces structured, traceable, agent-comprehensible project scaffolds.

**[Skill Definition →](skills/llm-first-init/SKILL.md)**

### `/llm-first-audit` — Methodology Compliance Audit
Audits any project against the LLM-First methodology.
Identifies principle misalignment, failure mode vulnerabilities, and structural issues.

**[Skill Definition →](skills/llm-first-audit/SKILL.md)**

### `/llm-first-reporting` — Human-Readable Report Generation
Generates prose-first reports from LLM-First projects for human audiences.
Supports status briefs, executive summaries, team briefings, progress reports, and audit summaries.

**[Skill Definition →](skills/llm-first-reporting/SKILL.md)**

## Methodology

These skills implement the methodology defined in [LLM-First Specification](https://github.com/gim-home/llm-first-specs):
- **Whitepaper:** [From Chaos to Clarity](https://github.com/gim-home/llm-first-specs/blob/main/WHITEPAPER_LLM_Driven_Specification.md)
- **Case Studies:** 5 validated patterns (SovereignAgent, Multi-Team, Docs at Scale, Methodology Capture, SQL in-Context)
- **Research:** [Why Structure Reduces Hallucination](https://github.com/gim-home/llm-first-specs/blob/main/references/structured-data-and-llm-grounding.md)

The methodology repo is the authoritative reference. These skills reference it; they do not duplicate it.

> **Runtime dependency:** Both skills load the methodology repo content into context before execution (Phase 0). If the user cannot access `gim-home/llm-first-specs`, the skills will not run.

## Architecture

```
llm-first-skills/
├── README.md                          # This file
└── skills/
    ├── llm-first-init/
    │   ├── SKILL.md                   # Skill definition
    │   └── references/                # Schema and acceptance criteria
    ├── llm-first-audit/
    │   ├── SKILL.md                   # Skill definition
    │   └── references/                # Evaluation and acceptance criteria
    └── llm-first-reporting/
        ├── SKILL.md                   # Skill definition
        └── references/                # Formatting conventions and acceptance criteria
```

## Requirements

- Agency Copilot CLI
- WorkIQ MCP tool (for authenticated source retrieval and discovery)
- Graceful degradation when WorkIQ unavailable (manual input, discovery skipped)
