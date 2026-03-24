# Relationships — Explicit Link Map {#relationships}

> Every entity-to-entity connection in this project.
> LLM agents: use this map for graph traversal queries.

---

## Finding → Commitment → Activity Chain

[SRC-AUDIT-REPORT](SOURCES.md#src-audit-report) (FND-55727)

### [DEC-MAP-SECTION-1](DECISIONS.md#dec-map-section-1): Roles & Responsibilities

- **[ACT-001](SOURCES.md#act-001) – [ACT-005](SOURCES.md#act-005):** Consumption & Ownership activities
  - Owner: [ENT-TEAM-EC](ENTITIES.md#ent-team-ec) (ACT-001–ACT-002), [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365) (ACT-003–ACT-004), [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep) (ACT-005)
  - Status: Mixed (Complete, In Progress, Researching)
- Evidence: Pending linkage

### [DEC-MAP-SECTION-2](DECISIONS.md#dec-map-section-2): Entry Requirements

- **[ACT-006](SOURCES.md#act-006):** Ownership Hub coverage → Owner: [ENT-CHRIS](ENTITIES.md#ent-chris)
- **[ACT-007](SOURCES.md#act-007):** Break up large services → Owner: [ENT-ANDREW](ENTITIES.md#ent-andrew) (per [DEC-ROW7-OWNER](DECISIONS.md#dec-row7-owner))
- **[ACT-008](SOURCES.md#act-008):** Educate group admins / guardrails → Owner: [ENT-KAUSHIK](ENTITIES.md#ent-kaushik)
- **[ACT-009](SOURCES.md#act-009):** Code ownership → Owner: [ENT-KAUSHIK](ENTITIES.md#ent-kaushik) (closable)

### [DEC-MAP-SECTION-3](DECISIONS.md#dec-map-section-3): Periodic Review

- **[ACT-010](SOURCES.md#act-010):** Distribute health reports → Owner: [ENT-CHRIS](ENTITIES.md#ent-chris) (not started)
- **[ACT-011](SOURCES.md#act-011), [ACT-012](SOURCES.md#act-012):** Monitoring rules / automation → Owner: [ENT-CHRIS](ENTITIES.md#ent-chris)

### [DEC-MAP-SECTION-4](DECISIONS.md#dec-map-section-4): Metadata Fields

- **[ACT-013](SOURCES.md#act-013):** Documentation for key fields → Owner: [ENT-KAUSHIK](ENTITIES.md#ent-kaushik)
- **[ACT-014](SOURCES.md#act-014), [ACT-015](SOURCES.md#act-015):** Monitoring/automation (DISPUTED by [ENT-KAUSHIK](ENTITIES.md#ent-kaushik))
- **[ACT-016](SOURCES.md#act-016):** Service review / required fields view → Owner: [ENT-CHRIS](ENTITIES.md#ent-chris)
- **[ACT-017](SOURCES.md#act-017):** Policy Engine upgrade → [ENT-KAUSHIK](ENTITIES.md#ent-kaushik) / [SRC-ADO-POLICY-ENGINE](SOURCES.md#src-ado-policy-engine)
  - ADO #9691491 (Status: New, no acceptance criteria)

### [DEC-MAP-SECTION-5](DECISIONS.md#dec-map-section-5): Data Quality Monitoring

- **[ACT-018](SOURCES.md#act-018), [ACT-019](SOURCES.md#act-019), [ACT-020](SOURCES.md#act-020):** Business logic, governance, escalation
  - Owner: [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365), [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep), [ENT-TEAM-EC](ENTITIES.md#ent-team-ec)
- **[ACT-021](SOURCES.md#act-021), [ACT-022](SOURCES.md#act-022):** Expand monitoring (FY26)
  - Owner: [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)

---

## Ownership Map

| Entity | Owns | Reports To |
|--------|------|-----------|
| [ENT-DAYSHA](ENTITIES.md#ent-daysha) | Finding remediation (primary) | Leadership (Rajesh Jha via Parul) |
| [ENT-JJ](ENTITIES.md#ent-jj) | Day-to-day coordination | [ENT-DAYSHA](ENTITIES.md#ent-daysha) |
| [ENT-CHRIS](ENTITIES.md#ent-chris) | Data hygiene automation, monitoring rules | [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365) |
| [ENT-KAUSHIK](ENTITIES.md#ent-kaushik) | Platform governance, policy engine | [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep) |
| [ENT-ANDREW](ENTITIES.md#ent-andrew) | Granularity / large services work | [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365) |
| [ENT-TEAM-AUDIT](ENTITIES.md#ent-team-audit) | Finding issuance, closure approval | Microsoft Board |

---

## System Dependencies

[ENT-SYS-SERVICE-TREE](ENTITIES.md#ent-sys-service-tree) — source of truth for service metadata

- **[ENT-SYS-S360](ENTITIES.md#ent-sys-s360)** — consumes: Service Type, Lifecycle, Owners, Org hierarchy
  - Surfaces DHE KPIs based on metadata quality
- **[ENT-SYS-ICM](ENTITIES.md#ent-sys-icm)** — consumes: IcM Tenant, IcM Team, Emergency Broadcast
  - Limitation: can't programmatically create teams
- **[ENT-SYS-DVF](ENTITIES.md#ent-sys-dvf)** — validates: metadata against source of truth
  - Limitation: post-entry only, not at point of entry
- **[ENT-SYS-KUSTO](ENTITIES.md#ent-sys-kusto)** — logs: actual field queries by consumers
  - [ENT-CHRIS](ENTITIES.md#ent-chris) has access — can validate actual vs. claimed usage
- **[ENT-SYS-EGRC](ENTITIES.md#ent-sys-egrc)** — tracks: findings, MAPs, evidence for closure

---

## Document Relationships

| Source | Derived From | Feeds Into |
|--------|-------------|-----------|
| [SRC-AUDIT-REPORT](SOURCES.md#src-audit-report) | Internal Audit investigation | [SRC-MAP](SOURCES.md#src-map) |
| [SRC-MAP](SOURCES.md#src-map) | SRC-AUDIT-REPORT findings | [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker) |
| [SRC-KEY-ACTIVITIES-NARRATIVE](SOURCES.md#src-key-activities-narrative) | SRC-MAP sections | (explanatory, not operational) |
| [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker) | SRC-MAP commitments | Evidence collection for EGRC |
| [SRC-GOVERNANCE-DOC](SOURCES.md#src-governance-doc) | Service Tree platform design | SRC-AUDIT-REPORT (audit evaluated against this) |
| [SRC-METADATA-DEFS](SOURCES.md#src-metadata-defs) | Service Tree platform design | SRC-GOVERNANCE-DOC (defines what's governed) |

---

## Decision Impact Map

| Decision | Affects |
|----------|---------|
| [DEC-OWNERSHIP-TRANSITION](DECISIONS.md#dec-ownership-transition) | All activities — new contacts |
| [DEC-ROW7-OWNER](DECISIONS.md#dec-row7-owner) | [ACT-007](SOURCES.md#act-007) owner |
| [DEC-PRESENT-GUARDRAILS](DECISIONS.md#dec-present-guardrails) | [ACT-008](SOURCES.md#act-008), [ACT-011](SOURCES.md#act-011)–[ACT-012](SOURCES.md#act-012) strategy |
| [DEC-SPIRIT-NOT-LETTER](DECISIONS.md#dec-spirit-not-letter) | All 5 MAP sections |
| [DEC-RESET-EXPECTATIONS](DECISIONS.md#dec-reset-expectations) | Audit team meeting agenda |
| [DEC-KAUSHIK-DISPUTES](DECISIONS.md#dec-kaushik-disputes) | [ACT-014](SOURCES.md#act-014)–[ACT-015](SOURCES.md#act-015) resolution |
| [DEC-GOVERNANCE-NOT-PLATFORM](DECISIONS.md#dec-governance-not-platform) | All governance items need E+D owner |
