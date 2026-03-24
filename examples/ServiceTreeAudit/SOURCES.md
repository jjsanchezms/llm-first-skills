# Sources — Input Catalog {#sources}

> Every source used to build this project scaffold.
> Each source has a stable ID, type, retrieval method, and content summary.

---

## Original Sources (User-Provided)

**SRC-AUDIT-REPORT** {#src-audit-report}: E+D Business Continuity Management and Service Tree Report - Final 1.docx
- **Type:** Word document (audit report)
- **Location:** [SharePoint — EDInventoryManagement](https://microsoft.sharepoint-df.com/teams/EDInventoryManagement/Shared%20Documents/General/Service%20Tree/Internal%20Audit%20Findings/)
- **Date:** September 19, 2024
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Full internal audit report. Two findings: FND-55727 (Service Tree Governance, Medium) and FND-55726 (W+D BCM, Medium). Includes observations, risk ratings, remediation requirements, appendices with past findings and data quality analysis.
- **Key data:** 361 metadata values checked; 10% inaccurate, 14% unknown accuracy; 35% of key fields unpopulated; 82% of hygiene action items overdue by avg 53 days.

**SRC-MAP** {#src-map}: Management Action Plan for FND-55727.docx
- **Type:** Word document (compliance response)
- **Location:** [SharePoint — FND-55727 folder](https://microsoft.sharepoint-df.com/teams/EDInventoryManagement/Shared%20Documents/General/Service%20Tree/Internal%20Audit%20Findings/FND-55727/)
- **Date:** ~November 2024 (60-day response)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Formal audit-facing action plan with 5 sections: Roles & Responsibilities, Entry Requirements, Periodic Review, Metadata Fields, Data Quality Monitoring. Commitments by ES365, AEP, E+C with FY25 H2 and FY26 timelines.
- **⚠️ Note:** [CON-1](CONSISTENCY_REPORT.md#con-1) — Two additional copies exist in same folder.

**SRC-KEY-ACTIVITIES-NARRATIVE** {#src-key-activities-narrative}: FND-55727 key activities.docx
- **Type:** Word document (narrative)
- **Location:** [SharePoint — FND-55727 folder](https://microsoft.sharepoint-df.com/teams/EDInventoryManagement/Shared%20Documents/General/Service%20Tree/Internal%20Audit%20Findings/FND-55727/)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Narrative breakdown of engineering commitments grouped by audit theme. More granular than MAP but lacks operational tracking fields. Covers same 5 themes as MAP with specific engineering actions.

**SRC-KEY-ACTIVITIES-TRACKER** {#src-key-activities-tracker}: FND-55727 Key Activities.xlsx
- **Type:** Excel workbook (operational tracker)
- **Location:** [SharePoint — FND-55727 folder](https://microsoft.sharepoint-df.com/teams/EDInventoryManagement/Shared%20Documents/General/Service%20Tree/Internal%20Audit%20Findings/FND-55727/)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** 22+ rows of action items with columns: Area, Key Activity, Status, Replaced By, Evidence Link, Original ETA, Current ETA, Team(s) Responsible, Assigned To, Date Assigned, Due Date, Notes. Status reference sheet with 8 values.
- **⚠️ Note:** [CON-3](CONSISTENCY_REPORT.md#con-3) — Some row owners don't match meeting-assigned owners.

**SRC-MEETING-FEB27** {#src-meeting-feb27}: Check in on FND-55727 (February 27, 2026)
- **Type:** Meeting transcript (.vtt)
- **Duration:** ~59 minutes
- **Participants:** Brian Day, Kaushik Pushpavanam, Daysha Carter, Andrew Sweeny, Chris Netz
- **Retrieved:** 2026-03-24 (user-provided .vtt file)
- **Content:** First "recovery" meeting. Team discovers awareness gaps — multiple people unaware of commitments. Item-by-item tracker review. Philosophical debate on governance approach. Brian begins drafting response document.

**SRC-MEETING-MAR20** {#src-meeting-mar20}: Quick sync on FND-55727 (March 20, 2026)
- **Type:** Meeting transcript (.vtt)
- **Duration:** ~30 minutes
- **Participants:** Brian Day, Daysha Carter, Chris Netz, Kaushik Pushpavanam
- **Retrieved:** 2026-03-24 (user-provided .vtt file)
- **Content:** Brian's departure meeting. Ownership transition: Daysha primary, JJ operational. Critical fields list discussion — Trust needs refresh. Data accuracy vs. governance distinction. Next sync to include JJ.

**SRC-MEETING-MAR23** {#src-meeting-mar23}: Quick sync on Service Tree (March 23, 2026)
- **Type:** Meeting transcript (Teams)
- **Duration:** ~45 minutes
- **Participants:** Brian Day, JJ Sánchez
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Brian-JJ knowledge transfer. Full audit context, MAP status, Service Tree architecture, governance gaps. Decision to reset expectations with audit. Action: share prior recordings with JJ.

---

## Discovered Sources (via WorkIQ Search)

**SRC-TRANSITION** {#src-transition}: Transition Materials.xlsx (Brian Day)
- **Type:** Excel workbook (handoff tracker)
- **Location:** Brian Day's OneDrive
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Brian's project handoff document. Includes: file cleanup status, feature rationalization, audit materials for FND-55727, EGRC portal link, business program contacts, critical fields list (under review), strategic business needs (Cloud Scope, PSL, Trust).

**SRC-GOVERNANCE-DOC** {#src-governance-doc}: Service Tree Metadata Governance.docx
- **Type:** Word document (policy)
- **Location:** [SharePoint — WAG/EngSys](https://microsoft.sharepoint.com/teams/WAG/EngSys/)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Defines "reliable metadata" (externally mastered OR internally validated/attested). Documents DVF and S360 attestation mechanisms. Acknowledges governance gaps: post-entry-only validation, time-based attestation, high service owner burden, ~220 fields with incomplete governance. Vision: no ungoverned metadata.

**SRC-METADATA-DEFS** {#src-metadata-defs}: ServiceTree Metadata Definitions.docx
- **Type:** Word document (reference)
- **Location:** [SharePoint — WAG/EngSys](https://microsoft.sharepoint.com/teams/WAG/EngSys/)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Canonical reference for essential metadata. ~350 fields, subset classified as essential in 4 classes: (1) S360 action items, (2) Security response, (3) Regulatory compliance, (4) Division-specific. Defines 12 core fields with hygiene measurement (coverage, quality, guardrails, external checks).

**SRC-PARTNER-USAGE** {#src-partner-usage}: Service Tree Partner Field Usage (federated wiki)
- **Type:** Distributed wiki documentation
- **Location:** Multiple (ADO wikis, eng.ms, osgwiki)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** No single canonical doc exists. Federated mapping of 7 downstream consumers (IcM, S360, SDL/Security, Azure Spend, Telemetry, BCDR, Repo/Engineering) to Service Tree fields. Key insight: field consumption is implicit, not declared via a registry.

**SRC-ADO-POLICY-ENGINE** {#src-ado-policy-engine}: ADO #9691491 — Metadata Policy Engine
- **Type:** Azure DevOps User Story
- **Location:** [Office/OE/Compliance/Service Tree](https://dev.azure.com/office/35d89fa2-df50-4442-9cb8-cc8679898172/_workitems/edit/9691491)
- **Created:** January 15, 2025 by Chris Netz
- **Status:** New (no progress)
- **Content:** "Enable collecting metadata based upon Service Type, SubType, Lifecycle stage and other metadata attributes." No acceptance criteria defined. Tagged: consumer, PartnerAsk, Semester:Br. Parent: #9691369. Corresponds to tracker Row 17.

**SRC-STRC-PLAYBOOK** {#src-strc-playbook}: STRC Metadata Quality & Hygiene Playbook
- **Type:** Working governance package (OneNote + spreadsheets)
- **Location:** SharePoint — Aznet team
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Step-by-step S360 hygiene remediation workflow: Issue identification → Triage/scoping → Ownership confirmation → Remediation execution → Validation/closure → Long-term fix documentation. Wave-based trackers. Accountability: service teams own metadata correctness, not STRC/platform.

**SRC-HYGIENE-WIKI** {#src-hygiene-wiki}: Metadata Hygiene wiki (eng.ms)
- **Type:** Wiki guidance page
- **Location:** eng.ms / SFI Automation Service wiki
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Defines metadata hygiene, monthly review expectation, and link to S360 DHE KPIs. Key message: "Fixing most hygiene issues takes minutes — but missing them can cost weeks of unplanned work." DHE KPIs are auto-generated when required metadata is missing/stale.

**SRC-ST-OVERVIEW** {#src-st-overview}: Service Tree Overview.pptx
- **Type:** PowerPoint deck
- **Location:** [SharePoint — WAG/EngSys/ServiceTree](https://microsoft.sharepoint.com/teams/WAG/EngSys/ServiceMgmt/ServiceTree/)
- **Retrieved:** 2026-03-24 via WorkIQ
- **Content:** Service Tree as single source of truth for service modeling. Metadata extensibility (custom, common, dependency-driven fields). Dependency mapping for risk assessment, compliance, fault tolerance. Compliance programs depend on critical fields and metadata subscriptions.
