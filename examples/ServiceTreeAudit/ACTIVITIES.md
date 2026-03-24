# Activities — Remediation Work Items {#activities}

> Every remediation activity from the FND-55727 Management Action Plan.
> Each activity has a stable ACT-* ID that replaces fragile row numbers.
> These IDs are the canonical references used across all project files.

---

## MAP Section 1: Roles & Responsibilities

**ACT-001** {#act-001}: Document Service Tree consumption programs and responsibilities
- **MAP Section:** [DEC-MAP-SECTION-1](DECISIONS.md#dec-map-section-1)
- **Owner:** [ENT-TEAM-EC](ENTITIES.md#ent-team-ec)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** E+C to document consumption programs and identified responsibilities. Part of the formal MAP commitment for Section 1.

**ACT-002** {#act-002}: Monitor BCDR champion coverage
- **MAP Section:** [DEC-MAP-SECTION-1](DECISIONS.md#dec-map-section-1)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** ES365 monitoring BCDR champion assignment and coverage across services.

**ACT-003** {#act-003}: Expand ownership attestation to all E+D
- **MAP Section:** [DEC-MAP-SECTION-1](DECISIONS.md#dec-map-section-1)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** Researching — see [DEC-SPIRIT-NOT-LETTER](DECISIONS.md#dec-spirit-not-letter)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Expand existing ownership attestation mechanisms to cover all of E+D. Status listed as "Researching" in tracker; scope and approach still under evaluation.

**ACT-004** {#act-004}: Entitlements based on Service Tree roles
- **MAP Section:** [DEC-MAP-SECTION-1](DECISIONS.md#dec-map-section-1)
- **Owner:** [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started)
- **Evidence:** (none linked)
- **Original ETA:** FY26
- **Current ETA:** FY26
- **Notes:** Role-based entitlements derived from Service Tree ownership data. Scheduled for FY26 delivery by AEP.

**ACT-005** {#act-005}: (Reserved — no additional Section 1 activity identified)
- **MAP Section:** [DEC-MAP-SECTION-1](DECISIONS.md#dec-map-section-1)
- **Owner:** N/A
- **Status:** N/A
- **Evidence:** N/A
- **Original ETA:** N/A
- **Current ETA:** N/A
- **Notes:** Placeholder. If an additional Section 1 activity is identified during reconciliation, assign it this ID. Otherwise, Section 2 begins at ACT-006.

---

## MAP Section 2: Entry Requirements for Service Tree

**ACT-006** {#act-006}: Publish guidance on granular service types
- **MAP Section:** [DEC-MAP-SECTION-2](DECISIONS.md#dec-map-section-2)
- **Owner:** [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep)
- **Status:** [Complete](GLOSSARY.md#def-status-complete)
- **Evidence:** (none linked — evidence required per [AMB-3](CONSISTENCY_REPORT.md#amb-3))
- **Original ETA:** FY25 H2
- **Current ETA:** Complete
- **Notes:** Published guidance on granular service types (Doc/Wiki, Software Code Only, ICM Only, etc.). Marked complete in tracker but evidence link needed for audit closure.

**ACT-007** {#act-007}: Identify large services, assess modeling improvements
- **MAP Section:** [DEC-MAP-SECTION-2](DECISIONS.md#dec-map-section-2)
- **Owner:** [ENT-ANDREW](ENTITIES.md#ent-andrew) (reassigned per [DEC-ROW7-OWNER](DECISIONS.md#dec-row7-owner))
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress) — ⚠️ **flagged unlikely to meet deadline**
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** At risk — see [CON-4](CONSISTENCY_REPORT.md#con-4)
- **Notes:** Breaking up large/monolithic services. Andrew has Cycle 2 squad plan to address. ICM limitations block some granularity work (can't programmatically create teams). Previously assigned to Chris Netz — tracker may not yet reflect reassignment ([CON-3](CONSISTENCY_REPORT.md#con-3)).

**ACT-008** {#act-008}: Educate group admins, add approval guardrails
- **MAP Section:** [DEC-MAP-SECTION-2](DECISIONS.md#dec-map-section-2)
- **Owner:** [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep) + [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started) — philosophical debate on approach
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Subject of philosophical debate: whether to build new guardrails or present existing mechanisms. See [DEC-PRESENT-GUARDRAILS](DECISIONS.md#dec-present-guardrails). Approach depends on audit team acceptance — see [GAP-1](CONSISTENCY_REPORT.md#gap-1).

**ACT-009** {#act-009}: Continue attributing code to services
- **MAP Section:** [DEC-MAP-SECTION-2](DECISIONS.md#dec-map-section-2)
- **Owner:** [ENT-TEAM-1ES](ENTITIES.md#ent-team-1es) + [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep) + [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [Complete](GLOSSARY.md#def-status-complete)
- **Evidence:** (none linked — evidence required per [AMB-3](CONSISTENCY_REPORT.md#amb-3))
- **Original ETA:** FY25 H2
- **Current ETA:** Complete
- **Notes:** Code-to-service attribution via 1ES code ownership initiatives. Marked complete in tracker but evidence link needed for audit closure.

---

## MAP Section 3: Periodic Review of Service Tree Entries

**ACT-010** {#act-010}: Distribute service metadata health reports
- **MAP Section:** [DEC-MAP-SECTION-3](DECISIONS.md#dec-map-section-3)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Distribute periodic health reports to service owners showing metadata completeness and quality. S360 DHE KPIs may partially address this — see [DEC-PRESENT-GUARDRAILS](DECISIONS.md#dec-present-guardrails).

**ACT-011** {#act-011}: Implement monitoring rules for critical fields
- **MAP Section:** [DEC-MAP-SECTION-3](DECISIONS.md#dec-map-section-3)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Monitoring rules for critical metadata fields. Scope depends on resolution of [AMB-1](CONSISTENCY_REPORT.md#amb-1) — "critical field" definition.

**ACT-012** {#act-012}: Expand automation to reduce human input
- **MAP Section:** [DEC-MAP-SECTION-3](DECISIONS.md#dec-map-section-3)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Tim Buzard's squad "cleared 40-45% of metadata" via automation — but no before/after metrics linked as evidence. See [GAP-4](CONSISTENCY_REPORT.md#gap-4) for baseline measurement gap.

---

## MAP Section 4: Service Tree Metadata Fields

**ACT-013** {#act-013}: Improve documentation for key metadata fields
- **MAP Section:** [DEC-MAP-SECTION-4](DECISIONS.md#dec-map-section-4)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365) / [ENT-KAUSHIK](ENTITIES.md#ent-kaushik)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Improving documentation for key metadata fields. Kaushik involved as governance/compliance lead from AEP.

**ACT-014** {#act-014}: Implement monitoring/automation — 90% reduction target top 20 fields
- **MAP Section:** [DEC-MAP-SECTION-4](DECISIONS.md#dec-map-section-4)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** Researching — ⚠️ **[DISPUTED](GLOSSARY.md#def-status-disputed)** by [ENT-KAUSHIK](ENTITIES.md#ent-kaushik)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Kaushik disputes this item: "I didn't sign up to doing this... I don't even agree that this is the right thing to do." See [DEC-KAUSHIK-DISPUTES](DECISIONS.md#dec-kaushik-disputes). Resolution deferred to next sync.

**ACT-015** {#act-015}: Define required fields for each Service Type
- **MAP Section:** [DEC-MAP-SECTION-4](DECISIONS.md#dec-map-section-4)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365) + [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep)
- **Status:** Researching — ⚠️ **[DISPUTED](GLOSSARY.md#def-status-disputed)** by [ENT-KAUSHIK](ENTITIES.md#ent-kaushik)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Kaushik disputes this item along with ACT-014. See [DEC-KAUSHIK-DISPUTES](DECISIONS.md#dec-kaushik-disputes). Requires resolution of which fields are truly "required" per service type — depends on [AMB-1](CONSISTENCY_REPORT.md#amb-1).

**ACT-016** {#act-016}: Create Service Tree view for required fields
- **MAP Section:** [DEC-MAP-SECTION-4](DECISIONS.md#dec-map-section-4)
- **Owner:** [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Depends on ACT-015 (defining which fields are required per service type). Cannot proceed until field requirements are defined.

**ACT-017** {#act-017}: Upgrade Service Tree Metadata Policy engine
- **MAP Section:** [DEC-MAP-SECTION-4](DECISIONS.md#dec-map-section-4)
- **Owner:** [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started) — ⚠️ **flagged unlikely to meet deadline**
- **Evidence:** ADO [#9691491](SOURCES.md#src-ado-policy-engine) — User Story created but no progress
- **Original ETA:** FY26
- **Current ETA:** At risk — never prioritized
- **Notes:** "Enable collecting metadata based upon Service Type, SubType, Lifecycle stage and other metadata attributes." ADO item has no acceptance criteria defined, status "New" with no progress since creation (Jan 2025). See [SRC-ADO-POLICY-ENGINE](SOURCES.md#src-ado-policy-engine).

---

## MAP Section 5: Data Quality Monitoring

**ACT-018** {#act-018}: Require field owners to provide business logic
- **MAP Section:** [DEC-MAP-SECTION-5](DECISIONS.md#dec-map-section-5)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Requiring field owners to provide business logic/justification for each metadata field they own. Enables better governance by clarifying why fields exist.

**ACT-019** {#act-019}: Require monitoring plans before adding new fields
- **MAP Section:** [DEC-MAP-SECTION-5](DECISIONS.md#dec-map-section-5)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365) + [ENT-TEAM-AEP](ENTITIES.md#ent-team-aep)
- **Status:** [In Progress](GLOSSARY.md#def-status-in-progress)
- **Evidence:** (none linked)
- **Original ETA:** FY25 H2
- **Current ETA:** (unknown)
- **Notes:** Preventive control: no new metadata fields added without a monitoring plan. Joint responsibility between ES365 (monitoring) and AEP (platform).

**ACT-020** {#act-020}: Establish ICM escalation path for overdue action items
- **MAP Section:** [DEC-MAP-SECTION-5](DECISIONS.md#dec-map-section-5)
- **Owner:** [ENT-TEAM-EC](ENTITIES.md#ent-team-ec)
- **Status:** [Complete](GLOSSARY.md#def-status-complete)
- **Evidence:** (none linked — evidence required per [AMB-3](CONSISTENCY_REPORT.md#amb-3))
- **Original ETA:** FY25 H2
- **Current ETA:** Complete
- **Notes:** ICM escalation path established for overdue metadata hygiene action items. Marked complete in tracker but evidence link needed for audit closure.

**ACT-021** {#act-021}: Expand monitoring to additional fields
- **MAP Section:** [DEC-MAP-SECTION-5](DECISIONS.md#dec-map-section-5)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started)
- **Evidence:** (none linked)
- **Original ETA:** FY26
- **Current ETA:** FY26
- **Notes:** Expand monitoring beyond critical fields to additional metadata fields. Scheduled for FY26. Depends on ACT-011 (monitoring rules for critical fields) being established first.

**ACT-022** {#act-022}: Expand automation beyond critical fields
- **MAP Section:** [DEC-MAP-SECTION-5](DECISIONS.md#dec-map-section-5)
- **Owner:** [ENT-TEAM-ES365](ENTITIES.md#ent-team-es365)
- **Status:** [Not Started](GLOSSARY.md#def-status-not-started)
- **Evidence:** (none linked)
- **Original ETA:** FY26
- **Current ETA:** FY26
- **Notes:** Expand automation to reduce human input beyond critical fields. Scheduled for FY26. Depends on ACT-012 (automation for critical fields) demonstrating results.
