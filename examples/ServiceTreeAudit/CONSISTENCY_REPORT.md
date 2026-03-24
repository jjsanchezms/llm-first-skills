# Consistency Report — Conflicts, Ambiguities, and Gaps {#consistency-report}

> ⚠️ This report must be reviewed and items resolved before the project scaffold
> can be considered reliable. Each item has a severity and resolution path.
>
> **Resolution statuses:** OPEN | RESOLVED | ACCEPTED (gap acknowledged, no action)

---

## 🔴 Conflicts (sources contradict each other)

**CON-1** {#con-1}: Three MAP copies exist — which is canonical?
- **Severity:** High
- **Source A:** `Management Action Plan for FND-55727.docx`
- **Source B:** `Management_Action_Plan_for_FND-55727.docx`
- **Source C:** `Management_Action_Plan_for_FND-55727 (1).docx`
- **Impact:** An agent or auditor cannot know which version to trust. Content appears substantively identical but versioning is unclear.
- **Resolution path:** Identify which was submitted to EGRC. That version is canonical. Archive or delete the others.
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj)
- **Status:** OPEN

**CON-2** {#con-2}: MAP deadline inconsistency
- **Severity:** Medium
- **Source A:** MAP document says "action plan due within 60 days" (→ ~Nov 19, 2024)
- **Source B:** All three meetings reference "end of June 2026" as the deadline
- **Impact:** The "60 days" was for submitting the MAP; "June 2026" is the remediation completion deadline. But this distinction isn't documented anywhere in the artifacts.
- **Resolution path:** Document both dates explicitly: MAP submission deadline (met, Nov 2024) vs. remediation completion deadline (June 30, 2026).
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj)
- **Status:** OPEN

**CON-3** {#con-3}: [ACT-007](ACTIVITIES.md#act-007) owner doesn't match meeting decision
- **Severity:** Medium
- **Source A:** [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker) — may show Chris Netz
- **Source B:** [SRC-MEETING-FEB27](SOURCES.md#src-meeting-feb27) — Andrew took ownership per [DEC-ROW7-OWNER](DECISIONS.md#dec-row7-owner)
- **Impact:** Tracker doesn't reflect the actual decision. Anyone reading the tracker gets wrong information.
- **Resolution path:** Update [ACT-007](ACTIVITIES.md#act-007) to show Andrew Sweeny as owner.
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj)
- **Status:** OPEN

**CON-4** {#con-4}: FY25 H2 commitments vs. team assessment of feasibility
- **Severity:** High
- **Source A:** [SRC-MAP](SOURCES.md#src-map) and [SRC-KEY-ACTIVITIES-NARRATIVE](SOURCES.md#src-key-activities-narrative) — multiple items committed for FY25 H2
- **Source B:** [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20) — team acknowledges "unlikely to be met"
- **Impact:** Formal commitments to audit don't match reality. Needs proactive communication before deadline.
- **Resolution path:** Per [DEC-RESET-EXPECTATIONS](DECISIONS.md#dec-reset-expectations), prepare revised brief showing what was accomplished differently.
- **Owner:** [ENT-DAYSHA](ENTITIES.md#ent-daysha)
- **Status:** OPEN

---

## 🟡 Ambiguities (terms used without shared definition)

**AMB-1** {#amb-1}: "Critical field" has 4 different scoping criteria
- **Severity:** High
- **Usage 1:** [SRC-METADATA-DEFS](SOURCES.md#src-metadata-defs) — "Essential metadata, Classes 1-4" (~12 core fields)
- **Usage 2:** Trust team (via [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20)) — Originally a "wish list" including aspirational fields
- **Usage 3:** [SRC-AUDIT-REPORT](SOURCES.md#src-audit-report) — "19 fields reviewed across ~3,200 services"
- **Usage 4:** Chris Netz ([SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20)) — "What people actually query via Kusto logs"
- **Impact:** Remediation scope is ambiguous. 12 fields vs. 19 fields vs. Trust's wish list vs. actual usage are very different scopes.
- **Resolution path:** Get refreshed critical fields list from Trust (Shivani SJ). Cross-reference with Kusto usage data (Chris). Align with audit's 19-field list. Document the canonical definition in [GLOSSARY.md](GLOSSARY.md#def-critical-field-001).
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj) + [ENT-CHRIS](ENTITIES.md#ent-chris)
- **Status:** OPEN

**AMB-2** {#amb-2}: "Governance" means different things to different teams
- **Severity:** High
- **Usage 1:** Platform team (Chris/Kaushik) — "Not our job. We own data accuracy."
- **Usage 2:** [SRC-MAP](SOURCES.md#src-map) — "Comprehensive governance structure"
- **Usage 3:** [SRC-AUDIT-REPORT](SOURCES.md#src-audit-report) — "Documented roles, responsibilities, and periodic review"
- **Impact:** Key activities assigned to the platform team may actually require E+D management ownership. Nobody owns "governance" as defined by the audit.
- **Resolution path:** Separate MAP items into "data accuracy" (platform team) and "governance" (E+D management). Assign governance owner within E+D. Document the distinction in [GLOSSARY.md](GLOSSARY.md#def-governance-001).
- **Owner:** [ENT-DAYSHA](ENTITIES.md#ent-daysha)
- **Status:** OPEN

**AMB-3** {#amb-3}: "Complete" status has no shared evidence requirement
- **Severity:** Medium
- **Usage 1:** [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker) — Self-reported checkbox
- **Usage 2:** Audit expectation — Evidence uploaded to EGRC
- **Usage 3:** [SRC-MEETING-FEB27](SOURCES.md#src-meeting-feb27) — "Addressed another way" also counts
- **Impact:** Items marked "Complete" on the tracker may not satisfy audit requirements for closure.
- **Resolution path:** Define "Complete" = status + evidence link + verification. Apply to all tracker items. See [GLOSSARY.md](GLOSSARY.md#def-status-complete).
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj)
- **Status:** OPEN

**AMB-4** {#amb-4}: "Service owner" has multiple definitions across systems
- **Severity:** Low (for this project; high for Service Tree generally)
- **Usage 1:** [SRC-METADATA-DEFS](SOURCES.md#src-metadata-defs) — PM Owner + Dev Owner
- **Usage 2:** Meeting context — Group admin who created the entry
- **Usage 3:** [SRC-HYGIENE-WIKI](SOURCES.md#src-hygiene-wiki) — Person who receives S360 action items
- **Impact:** When audit says "28% of Service Admins were inaccurate," which ownership field are they measuring?
- **Resolution path:** Clarify with audit which ownership fields were sampled. Document in glossary.
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj)
- **Status:** OPEN

---

## 🔵 Gaps (information required but not found in any source)

**GAP-1** {#gap-1}: No documented acceptance criteria from Internal Audit for closure
- **Severity:** Critical
- **Impact:** Team is guessing what audit will accept. Decisions ([DEC-PRESENT-GUARDRAILS](DECISIONS.md#dec-present-guardrails), [DEC-SPIRIT-NOT-LETTER](DECISIONS.md#dec-spirit-not-letter)) depend on audit confirming alternative approaches.
- **Resolution path:** Daysha to schedule meeting with audit team; document their acceptance criteria explicitly.
- **Owner:** [ENT-DAYSHA](ENTITIES.md#ent-daysha)
- **Status:** OPEN

**GAP-2** {#gap-2}: No RACI matrix for governance vs. data accuracy ownership
- **Severity:** High
- **Impact:** Chris explicitly said platform team won't own governance. But no one else is assigned. Multiple items in the MAP require a governance owner within E+D that doesn't exist.
- **Resolution path:** Create RACI matrix. Daysha to assign governance ownership or escalate.
- **Owner:** [ENT-DAYSHA](ENTITIES.md#ent-daysha)
- **Status:** OPEN

**GAP-3** {#gap-3}: No cross-reference between tracker rows and MAP sections
- **Severity:** High
- **Impact:** Cannot trace operational work to audit commitments. An auditor reviewing the tracker cannot verify it covers all MAP commitments.
- **Resolution path:** Add a "MAP Section" column to the tracker. Map every row to its corresponding MAP section (1-5). Note: [ACTIVITIES.md](ACTIVITIES.md) now provides a structured cross-reference between activities (ACT-* IDs) and MAP sections, partially addressing this gap.
- **Owner:** [ENT-JJ](ENTITIES.md#ent-jj)
- **Status:** OPEN

**GAP-4** {#gap-4}: No baseline metrics for fields addressed by automation
- **Severity:** Medium
- **Impact:** Tim Buzard's squad "cleared 40-45% of metadata" — but there's no before/after measurement linked to evidence. Audit will want quantified improvement.
- **Resolution path:** Chris to run Kusto queries for baseline (audit time) vs. current field accuracy. Document as evidence.
- **Owner:** [ENT-CHRIS](ENTITIES.md#ent-chris)
- **Status:** OPEN

**GAP-5** {#gap-5}: Audit team contact not established by new owners
- **Severity:** Critical
- **Impact:** Daysha and JJ have no relationship with the audit team. Brian was supposed to provide an intro before departure.
- **Resolution path:** Brian to provide audit team contact name and intro. Daysha to schedule initial meeting.
- **Owner:** [ENT-DAYSHA](ENTITIES.md#ent-daysha) (waiting on [ENT-BRIAN](ENTITIES.md#ent-brian))
- **Status:** OPEN

**GAP-6** {#gap-6}: Critical fields list needs refresh from Trust
- **Severity:** Medium
- **Impact:** The existing critical fields list (~1.5 years old) includes "wish list" items. Trust's needs have changed (per Shivani SJ). Remediation scope may be targeting wrong fields.
- **Resolution path:** Brian meeting with Shivani (scheduled before his departure). Output must be documented and shared.
- **Owner:** [ENT-BRIAN](ENTITIES.md#ent-brian) → [ENT-JJ](ENTITIES.md#ent-jj) (follow-up)
- **Status:** OPEN

**GAP-7** {#gap-7}: No "all consumers × all fields" registry
- **Severity:** Low (long-term, not blocking for FND-55727)
- **Impact:** Per [SRC-PARTNER-USAGE](SOURCES.md#src-partner-usage), field consumption is implicit. No central registry maps which downstream systems break when which fields change.
- **Resolution path:** Out of scope for FND-55727 closure. Document as long-term improvement need.
- **Owner:** N/A
- **Status:** ACCEPTED
