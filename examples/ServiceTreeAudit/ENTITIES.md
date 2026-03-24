# Entities — People, Teams, Systems, Artifacts {#entities}

> Every named entity in this project with a stable ID, role, and relationships.
> Use these IDs when referencing entities in any project artifact.

---

## People

**ENT-BRIAN** {#ent-brian}: Brian Day
- **Role:** Departing owner of FND-55727 remediation
- **Team:** [ENT-TEAM-EC](#ent-team-ec) (transitioning to Copilot Extensions/WorkIQ)
- **Status:** Departing week of Mar 24, 2026
- **Owns:** [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker), [SRC-TRANSITION](SOURCES.md#src-transition)
- **Context:** Created the tracking spreadsheet from the original MAP. His name is on the audit item as owner. Has institutional knowledge about the audit team contact and the full finding history.
- **Risk:** Key-person departure — see [DEC-OWNERSHIP-TRANSITION](DECISIONS.md#dec-ownership-transition)

**ENT-DAYSHA** {#ent-daysha}: Daysha Carter
- **Role:** New primary owner of FND-55727 remediation
- **Team:** [ENT-TEAM-EC](#ent-team-ec)
- **Status:** Active — taking over ownership
- **Owns:** Audit team relationship, escalation management
- **Context:** Was not on the team when finding was issued. Learned of it ~Feb 2026. ~2-3 months in broader Cloud Fundamentals role.
- **Actions pending:** Establish audit team contact, schedule audit status meeting

**ENT-JJ** {#ent-jj}: JJ Sánchez
- **Role:** Operational/day-to-day support for FND-55727
- **Team:** [ENT-TEAM-EC](#ent-team-ec)
- **Status:** Active — ramping up
- **Owns:** Day-to-day tracking, coordination with Service Tree team
- **Context:** Joined project Mar 23, 2026 via knowledge transfer from Brian.

**ENT-CHRIS** {#ent-chris}: Chris Netz
- **Role:** Service Tree platform / data quality lead
- **Team:** [ENT-TEAM-ES365](#ent-team-es365)
- **Status:** Active
- **Owns:** Data hygiene automation, monitoring rules, Kusto log access, [SRC-ADO-POLICY-ENGINE](SOURCES.md#src-ado-policy-engine)
- **Context:** Helped compose original key activities list but didn't realize formal commitments were made. Can validate actual field usage via Kusto logs. Emphasizes data accuracy ≠ governance.
- **Activities:** [ACT-006](ACTIVITIES.md#act-006), [ACT-011](ACTIVITIES.md#act-011), [ACT-012](ACTIVITIES.md#act-012), [ACT-013](ACTIVITIES.md#act-013), [ACT-016](ACTIVITIES.md#act-016) (some reassigned)

**ENT-KAUSHIK** {#ent-kaushik}: Kaushik Pushpavanam
- **Role:** Service Tree governance/compliance lead
- **Team:** [ENT-TEAM-AEP](#ent-team-aep) (Azure Core)
- **Status:** Active — disputes some items
- **Owns:** Audit response experience, policies page, service creation philosophy
- **Context:** Previously closed a separate audit finding (~20 months with monthly follow-ups). Currently in another audit. Disputes [ACT-014](ACTIVITIES.md#act-014) and [ACT-015](ACTIVITIES.md#act-015). Team of ~10 people.
- **Activities:** [ACT-008](ACTIVITIES.md#act-008), [ACT-009](ACTIVITIES.md#act-009), [ACT-014](ACTIVITIES.md#act-014), [ACT-015](ACTIVITIES.md#act-015), [ACT-017](ACTIVITIES.md#act-017)

**ENT-ANDREW** {#ent-andrew}: Andrew Sweeny
- **Role:** Granularity/entry requirements lead
- **Team:** [ENT-TEAM-ES365](#ent-team-es365)
- **Status:** Active
- **Owns:** Large services/granularity work (Cycle 2 squad plan)
- **Context:** Had not previously seen the findings list. Took ownership of [ACT-007](ACTIVITIES.md#act-007) (breaking up monolithic services) per [DEC-ROW7-OWNER](DECISIONS.md#dec-row7-owner).
- **Activities:** [ACT-007](ACTIVITIES.md#act-007), [ACT-008](ACTIVITIES.md#act-008)

**ENT-RYAN** {#ent-ryan}: Ryan Zacher
- **Role:** Named finding owner in audit report
- **Title:** Principal GPM, Enterprise Cloud Service Core
- **Context:** Named in [SRC-AUDIT-REPORT](SOURCES.md#src-audit-report) as the official owner. Remediation timeline: action plan due by Nov 19, 2024.

**ENT-SHIVANI** {#ent-shivani}: Shivani SJ
- **Role:** Trust org representative
- **Context:** Brian met with her about critical fields list. Trust's needs have changed significantly since original list was created. Refresh needed. Source: [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20).


**ENT-TIM** {#ent-tim}: Tim Buzard
- **Role:** Led AI-string squad for metadata cleanup
- **Team:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Context:** Squad cleared 40-45% of all metadata issues. Key evidence for remediation progress. Source: [SRC-MEETING-FEB27](SOURCES.md#src-meeting-feb27).

**ENT-RAJESH** {#ent-rajesh}: Rajesh Jha
- **Role:** EVP, E+D — executive escalation target
- **Context:** Would receive stern mail if audit is failed. Named in [SRC-AUDIT-REPORT](SOURCES.md#src-audit-report) as primary recipient.

**ENT-PARUL** {#ent-parul}: Parul Manek
- **Role:** Intermediate leadership — escalation chain between Daysha and Rajesh
- **Context:** Referenced in [SRC-MEETING-FEB27](SOURCES.md#src-meeting-feb27) and [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20).

---

## Teams

**ENT-TEAM-ES365** {#ent-team-es365}: Engineering Systems 365
- **Scope:** Service Tree data hygiene, monitoring/automation, health reporting, code ownership
- **Key people:** [Chris Netz](#ent-chris), [Andrew Sweeny](#ent-andrew)
- **MAP responsibilities:** Sections 1-5 (shared with AEP and E+C)
- **Definition:** [DEF-ES365-001](GLOSSARY.md#def-es365-001)

**ENT-TEAM-AEP** {#ent-team-aep}: Azure Engineering Platform (Azure Core)
- **Scope:** Service Tree platform, metadata policy engine, service type guidance, approval guardrails
- **Key people:** [Kaushik Pushpavanam](#ent-kaushik)
- **Size:** ~10 people
- **MAP responsibilities:** Sections 1, 2, 4, 5
- **Definition:** [DEF-AEP-001](GLOSSARY.md#def-aep-001)

**ENT-TEAM-EC** {#ent-team-ec}: Engineering + Compliance (E+C)
- **Scope:** Consumption program documentation, BCDR champion monitoring, escalation paths
- **Key people:** [Brian Day](#ent-brian), [Daysha Carter](#ent-daysha), [JJ Sánchez](#ent-jj)
- **MAP responsibilities:** Sections 1, 5
- **Definition:** [DEF-EC-001](GLOSSARY.md#def-ec-001)

**ENT-TEAM-1ES** {#ent-team-1es}: One Engineering System
- **Scope:** Code-to-service attribution
- **MAP responsibilities:** Section 2 (code ownership)
- **Definition:** [DEF-1ES-001](GLOSSARY.md#def-1es-001)

**ENT-TEAM-AUDIT** {#ent-team-audit}: Microsoft Internal Audit
- **Scope:** Issues findings, reviews MAP, accepts/rejects closure evidence
- **Reports to:** Microsoft Board
- **Context:** Audit team contact not yet established by new owners — see [GAP-1](CONSISTENCY_REPORT.md#gap-1)

**ENT-TEAM-TRUST** {#ent-team-trust}: Trust Organization
- **Scope:** Compliance (FedRamp, SOC), security field requirements
- **Key people:** [Shivani SJ](#ent-shivani)
- **Context:** Needs have changed significantly since critical fields list was created

---

## Systems

**ENT-SYS-SERVICE-TREE** {#ent-sys-service-tree}: Service Tree
- **Definition:** [DEF-SERVICE-TREE-001](GLOSSARY.md#def-service-tree-001)
- **Scale:** ~3,200 services, ~350 metadata fields
- **Consumers:** [S360](#ent-sys-s360), [IcM](#ent-sys-icm), SDL, Azure Spend, Telemetry, BCDR

**ENT-SYS-S360** {#ent-sys-s360}: Service 360
- **Definition:** [DEF-S360-001](GLOSSARY.md#def-s360-001)
- **Relationship:** Consumes Service Tree metadata; surfaces DHE KPIs

**ENT-SYS-EGRC** {#ent-sys-egrc}: EGRC Portal
- **Definition:** [DEF-EGRC-001](GLOSSARY.md#def-egrc-001)
- **Relationship:** Where MAP was submitted; where evidence must be uploaded for closure

**ENT-SYS-ICM** {#ent-sys-icm}: Incident Communications Manager
- **Relationship:** Consumes Service Tree IcM tenant/team fields; required for security incident routing
- **Context:** ICM limitations block granularity work (can't programmatically create teams)

**ENT-SYS-DVF** {#ent-sys-dvf}: Data Validation Framework
- **Definition:** [DEF-DVF-001](GLOSSARY.md#def-dvf-001)
- **Relationship:** Validates Service Tree metadata; currently post-entry only

**ENT-SYS-KUSTO** {#ent-sys-kusto}: Service Tree Kusto Logs
- **Relationship:** Chris Netz has access; can validate actual field usage vs. claimed needs
- **Context:** New capability not available during earlier rounds of critical fields assessment
