# Discovery — Search Log {#discovery}

> What was searched, what was found, and what was included/excluded.
> This log ensures no future participant wonders "did anyone look for X?"

---

## Discovery Queries Executed

**DISC-QUERY-1** {#disc-query-1}: Related documents by entity and keyword
- **Tool:** WorkIQ
- **Query:** "Find all documents, emails, chats, and files related to FND-55727 or 'Service Tree audit' or 'Service Tree governance'. Include documents from Brian Day, Daysha Carter, Chris Netz, Kaushik Pushpavanam, Ryan Zacher, or Andrew Sweeny."
- **Date:** 2026-03-24
- **Results:** 6 items (3 meetings, 2 documents, 1 transition file)
- **Notable finding:** No standalone emails or chat threads about FND-55727 — all communication via meetings

**DISC-QUERY-2** {#disc-query-2}: Service Tree metadata/governance documents
- **Tool:** WorkIQ
- **Query:** "Find documents about 'Service Tree metadata' OR 'Service Tree critical fields' OR 'Service Tree data quality' OR 'metadata hygiene' OR 'S360 Service Tree'"
- **Date:** 2026-03-24
- **Results:** 15 items (policy docs, dashboards, wikis, guides, decks)
- **Notable finding:** Rich ecosystem of governance docs that the project team wasn't referencing

**DISC-QUERY-3** {#disc-query-3}: ADO work items
- **Tool:** WorkIQ
- **Query:** "Find any Azure DevOps work items related to 'FND-55727' OR 'Service Tree governance' OR 'metadata policy engine'. Also items assigned to Chris Netz or Kaushik."
- **Date:** 2026-03-24
- **Results:** 6 ADO items found
- **Notable finding:** FND-55727 itself is NOT tracked as an ADO work item. ADO #9691491 (Metadata Policy Engine) has no acceptance criteria despite being a MAP commitment.

**DISC-QUERY-4** {#disc-query-4}: Communications (email, chat, meetings)
- **Tool:** WorkIQ
- **Query:** "Find any emails or Teams chats about FND-55727 from the last 6 months"
- **Date:** 2026-03-24
- **Results:** 0 email threads, 0 chat threads
- **Notable finding:** All FND-55727 communication has been synchronous (meetings only). This confirms the "knowledge trapped in meetings" risk.

---

## Triage Decisions

### Included (High Relevance)

**DISC-INC-1** {#disc-inc-1}: Transition Materials.xlsx (Brian Day)
- **Rationale:** Brian's handoff doc — contains EGRC portal link and strategic context
- **Source ID:** [SRC-TRANSITION](SOURCES.md#src-transition)

**DISC-INC-2** {#disc-inc-2}: Service Tree Metadata Governance.docx
- **Rationale:** Defines "reliable metadata" — directly addresses audit gap
- **Source ID:** [SRC-GOVERNANCE-DOC](SOURCES.md#src-governance-doc)

**DISC-INC-3** {#disc-inc-3}: ServiceTree Metadata Definitions.docx
- **Rationale:** Canonical field definitions — the glossary audit said was missing
- **Source ID:** [SRC-METADATA-DEFS](SOURCES.md#src-metadata-defs)

**DISC-INC-4** {#disc-inc-4}: Service Tree Partner Field Usage (wiki)
- **Rationale:** Maps which downstream systems consume which fields
- **Source ID:** [SRC-PARTNER-USAGE](SOURCES.md#src-partner-usage)

**DISC-INC-5** {#disc-inc-5}: ADO #9691491: Metadata Policy Engine
- **Rationale:** Only ADO item for a MAP commitment — [ACT-017](ACTIVITIES.md#act-017)
- **Source ID:** [SRC-ADO-POLICY-ENGINE](SOURCES.md#src-ado-policy-engine)

### Included (Medium Relevance — Context)

**DISC-INC-6** {#disc-inc-6}: STRC Metadata Quality & Hygiene Playbook
- **Rationale:** Remediation workflow and accountability model
- **Source ID:** [SRC-STRC-PLAYBOOK](SOURCES.md#src-strc-playbook)

**DISC-INC-7** {#disc-inc-7}: Metadata Hygiene wiki (eng.ms)
- **Rationale:** Monthly hygiene expectations and S360/DHE connection
- **Source ID:** [SRC-HYGIENE-WIKI](SOURCES.md#src-hygiene-wiki)

**DISC-INC-8** {#disc-inc-8}: Service Tree Overview.pptx
- **Rationale:** Platform context for stakeholder alignment
- **Source ID:** [SRC-ST-OVERVIEW](SOURCES.md#src-st-overview)

### Excluded (Low Relevance)

**DISC-EXC-1** {#disc-exc-1}: Service Tree Query Guide (Kusto)
- **Rationale:** Engineering reference — not needed for project scaffold

**DISC-EXC-2** {#disc-exc-2}: Introduction to Service Tree.pptx
- **Rationale:** Onboarding deck — duplicates overview content

**DISC-EXC-3** {#disc-exc-3}: ARM Manifest Metadata Guide
- **Rationale:** Azure Core-specific, too narrow

**DISC-EXC-4** {#disc-exc-4}: Metadata Hygiene Program (2021 deck)
- **Rationale:** Historical, potentially outdated

**DISC-EXC-5** {#disc-exc-5}: ADO #2141972 (TFL audit/updates)
- **Rationale:** Different team, different scope

**DISC-EXC-6** {#disc-exc-6}: ADO #3617384 (Entry requirements)
- **Rationale:** Closed, different org

**DISC-EXC-7** {#disc-exc-7}: ADO #4935612 (S360 hygiene bug)
- **Rationale:** Specific bug, not governance

**DISC-EXC-8** {#disc-exc-8}: ADO #11310420 / #11273465 (DHE compliance)
- **Rationale:** Different org (RDX), operational not strategic

**DISC-EXC-9** {#disc-exc-9}: AI Projects.xlsx (Daysha)
- **Rationale:** References Service Tree MCP Server but not audit-relevant

### Not Searched (Potential Future Discovery)

**DISC-FUTURE-1** {#disc-future-1}: EGRC portal contents
- **Rationale:** Requires EGRC access — not yet available
- **When to search:** When preparing closure evidence

**DISC-FUTURE-2** {#disc-future-2}: S360 DHE dashboard data
- **Rationale:** Requires S360 access — not yet available
- **When to search:** When quantifying hygiene improvement

**DISC-FUTURE-3** {#disc-future-3}: Service Tree Kusto logs
- **Rationale:** Requires Chris's access — see [ENT-CHRIS](ENTITIES.md#ent-chris)
- **When to search:** When validating actual field usage

**DISC-FUTURE-4** {#disc-future-4}: Prior audit findings (FY22-24)
- **Rationale:** 17 referenced in Appendix 4 of [SRC-AUDIT-REPORT](SOURCES.md#src-audit-report)
- **When to search:** When assessing pattern of recurring issues
