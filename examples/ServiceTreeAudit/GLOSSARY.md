# Glossary — Canonical Definitions {#glossary}

> Every term used inconsistently or ambiguously across sources is defined here.
> These definitions are authoritative for this project.
> LLM agents: use ONLY these definitions when reasoning about this project.

---

## Audit & Compliance

**DEF-FINDING-001** {#def-finding-001}: An observation issued by Internal Audit identifying a control deficiency or governance gap. Each finding has a unique ID (e.g., FND-55727), a risk level, an owner, and a remediation deadline. Findings are tracked in [EGRC](#def-egrc-001).

**DEF-MAP-001** {#def-map-001}: Management Action Plan. The formal document submitted to Internal Audit in response to a finding, committing to specific corrective actions with owners and timelines. The canonical MAP for this project is [SRC-MAP](SOURCES.md#src-map). See: [CON-1](CONSISTENCY_REPORT.md#con-1) for duplicate MAP issue.

**DEF-EGRC-001** {#def-egrc-001}: Enterprise Governance, Risk, and Compliance portal. The system where MAPs are submitted, evidence is uploaded, and findings are tracked to closure. Evidence must be uploaded to EGRC before requesting finding closure.

**DEF-CLOSURE-001** {#def-closure-001}: The state where Internal Audit confirms a finding has been adequately remediated. Requires: (a) evidence uploaded to EGRC, (b) audit team review, (c) confirmation that commitments are met or acceptably addressed through alternative means. See: [GAP-1](CONSISTENCY_REPORT.md#gap-1) — acceptance criteria from audit team not yet documented.

---

## Service Tree

**DEF-SERVICE-TREE-001** {#def-service-tree-001}: Microsoft's authoritative internal directory that maps engineering assets to service names. Contains ~3,200 services with ~350 metadata fields. Serves as system of record for ownership, compliance, security, and operational data. Source: [SRC-ST-OVERVIEW](SOURCES.md#src-st-overview).

**DEF-METADATA-FIELD-001** {#def-metadata-field-001}: An attribute associated with a Service Tree entry. There are ~350 distinct fields, grouped into 4 classes of "essential metadata" per [SRC-METADATA-DEFS](SOURCES.md#src-metadata-defs). Not all fields apply to all services — applicability varies by org, program, and service type.

**DEF-CRITICAL-FIELD-001** {#def-critical-field-001}: A Service Tree metadata field classified as essential for compliance, security, or operations. **⚠️ AMBIGUOUS — see [AMB-1](CONSISTENCY_REPORT.md#amb-1)**. Multiple definitions exist:
- Metadata Definitions doc: "Essential metadata, Classes 1-4" (~12 core fields)
- Trust team: Originally a "wish list" including aspirational fields
- Internal Audit: "19 fields reviewed across ~3,200 services"
- Chris Netz: "Fields people actually query via Kusto logs"
**Resolution required before using this term in audit communications.**

**DEF-SERVICE-TYPE-001** {#def-service-type-001}: Classification of what a Service Tree entry represents. Granular types include: Doc/Wiki, Software Code Only, ICM Only. Published guidance exists per [SRC-MAP](SOURCES.md#src-map) Key Activity for entry requirements.

**DEF-SERVICE-OWNER-001** {#def-service-owner-001}: The person(s) accountable for a Service Tree entry. **⚠️ AMBIGUOUS — see [AMB-4](CONSISTENCY_REPORT.md#amb-4)**. Multiple definitions:
- Metadata Definitions: PM Owner (`Contact_PMOwner`) + Dev Owner (`Contact_DevOwner`)
- S360: Person who receives action items
- Meeting context: Group admin who created the entry

---

## Governance & Hygiene

**DEF-GOVERNANCE-001** {#def-governance-001}: The processes, documentation, and accountability structures ensuring Service Tree data is accurate and complete. **⚠️ AMBIGUOUS — see [AMB-2](CONSISTENCY_REPORT.md#amb-2)**. Multiple interpretations:
- Platform team (Chris/Kaushik): "Not our job — we own data accuracy, not governance"
- MAP: "Comprehensive governance structure" over Service Tree
- Audit: "Documented roles, responsibilities, and periodic review"

**DEF-DATA-ACCURACY-001** {#def-data-accuracy-001}: The correctness of values in Service Tree metadata fields. Distinguished from [governance](#def-governance-001) — data accuracy is a platform team concern; governance is a management concern. Source: Mar 20 meeting, Chris Netz.

**DEF-METADATA-HYGIENE-001** {#def-metadata-hygiene-001}: The practice of keeping Service Tree metadata accurate, complete, and current. Measured by coverage (% of services with field populated) and quality (% validated via audit or guardrails). Monthly review expected. Directly drives S360 DHE KPIs. Source: [SRC-HYGIENE-WIKI](SOURCES.md#src-hygiene-wiki).

**DEF-DVF-001** {#def-dvf-001}: Data Validation Framework. Validates Service Tree metadata against a source of truth. Currently identifies invalid entries only after they are entered (post-entry alerting via S360 KPI). Source: [SRC-GOVERNANCE-DOC](SOURCES.md#src-governance-doc).

**DEF-S360-001** {#def-s360-001}: Service 360. Dashboard and action layer that surfaces metadata hygiene issues as KPIs and action items. Consumes Service Tree fields including: Service Tree ID, Service Type, Lifecycle Stage, Owners, Org hierarchy, Compliance metadata. Source: [SRC-HYGIENE-WIKI](SOURCES.md#src-hygiene-wiki).

**DEF-DHE-001** {#def-dhe-001}: Digital Hygiene & Excellence. The S360 KPI category that tracks metadata quality. DHE KPIs are auto-generated when required metadata is missing, inconsistent, or stale. Resolving the underlying data issue is the only way to close DHE action items. Source: [SRC-HYGIENE-WIKI](SOURCES.md#src-hygiene-wiki).

---

## Project Statuses

**DEF-STATUS-NOT-STARTED** {#def-status-not-started}: Activity has not begun. No evidence exists.

**DEF-STATUS-IN-PROGRESS** {#def-status-in-progress}: Activity has begun but is not complete. Partial evidence may exist.

**DEF-STATUS-COMPLETE** {#def-status-complete}: Activity is done AND evidence is linked. See: [AMB-3](CONSISTENCY_REPORT.md#amb-3) — "Complete" must include evidence reference, not just self-report.

**DEF-STATUS-BLOCKED** {#def-status-blocked}: Activity cannot proceed due to a dependency or external constraint. Blocker must be documented.

**DEF-STATUS-DISPUTED** {#def-status-disputed}: Activity's scope, ownership, or necessity is contested by a named party. Must include: who disputes, rationale, and resolution path.

**DEF-STATUS-REPLACED** {#def-status-replaced}: Activity has been superseded by alternative approach. Must include: what replaced it and why it satisfies the original commitment.

---

## Teams

**DEF-ES365-001** {#def-es365-001}: Engineering Systems 365. Responsible for Service Tree data hygiene, monitoring automation, and health reporting. Key people: [Chris Netz](ENTITIES.md#ent-chris), [Andrew Sweeny](ENTITIES.md#ent-andrew).

**DEF-AEP-001** {#def-aep-001}: Azure Engineering Platform (now Azure Core). Responsible for Service Tree platform, metadata policy engine, service type guidance. Key person: [Kaushik Pushpavanam](ENTITIES.md#ent-kaushik).

**DEF-EC-001** {#def-ec-001}: Engineering + Compliance (E+C). Responsible for escalation paths, consumption program documentation, BCDR champion monitoring. Key person: [Brian Day](ENTITIES.md#ent-brian) (departing), [Daysha Carter](ENTITIES.md#ent-daysha) (new).

**DEF-1ES-001** {#def-1es-001}: One Engineering System. Responsible for code-to-service attribution as part of code ownership initiatives.
