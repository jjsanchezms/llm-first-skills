# Decisions — Strategic Decision Log {#decisions}

> Every significant decision made during this project, extracted from meetings and documents.
> Each decision has a stable ID, date, participants, rationale, and affected items.

---

## Ownership & Governance

**DEC-OWNERSHIP-TRANSITION** {#dec-ownership-transition}: Daysha Carter becomes primary owner; JJ Sánchez provides operational support
- **Date:** 2026-03-20
- **Source:** [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20)
- **Participants:** Brian Day, Daysha Carter, Chris Netz, Kaushik Pushpavanam
- **Rationale:** Brian departing to Copilot Extensions/WorkIQ. Daysha is Brian's manager and already in Cloud Fundamentals role.
- **Affects:** All key activities — new point of contact for audit team, Service Tree team, and leadership
- **Action required:** Brian to brief JJ; Brian to provide intro to audit team contact

**DEC-ROW7-OWNER** {#dec-row7-owner}: Andrew Sweeny takes ownership of ACT-007 (breaking up large/monolithic services)
- **Date:** 2026-02-27
- **Source:** [SRC-MEETING-FEB27](SOURCES.md#src-meeting-feb27)
- **Participants:** Andrew Sweeny, Brian Day, Daysha Carter, Chris Netz
- **Rationale:** Andrew has Cycle 2 squad plan to address blocking issues. Chris doesn't have capacity.
- **Affects:** [SRC-KEY-ACTIVITIES-TRACKER](SOURCES.md#src-key-activities-tracker) ACT-007
- **⚠️ Note:** [CON-3](CONSISTENCY_REPORT.md#con-3) — Tracker may still show Chris as owner

---

## Audit Strategy

**DEC-PRESENT-GUARDRAILS** {#dec-present-guardrails}: Present existing guardrails to audit instead of building new features
- **Date:** 2026-02-27
- **Source:** [SRC-MEETING-FEB27](SOURCES.md#src-meeting-feb27)
- **Participants:** Daysha Carter, Brian Day, Kaushik Pushpavanam
- **Rationale:** Some activities may already be addressed through automation, field deprecation, or existing processes that didn't exist when the MAP was written (Nov 2024). Building new features under time pressure is risky.
- **Affects:** Multiple tracker rows — particularly ACT-008 (approval guardrails), ACT-011–ACT-012 (monitoring/automation)
- **Risk:** Audit team may not accept alternative approaches — see [GAP-1](CONSISTENCY_REPORT.md#gap-1)

**DEC-SPIRIT-NOT-LETTER** {#dec-spirit-not-letter}: Address spirit of the finding, not verbatim MAP commitments
- **Date:** 2026-03-20
- **Source:** [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20)
- **Participants:** Brian Day, Daysha Carter, Kaushik Pushpavanam
- **Rationale:** Original MAP was written under time pressure. Some commitments don't reflect how the Service Tree team actually operates. Kaushik: "The auditor doesn't care about the means, they only care about the ends."
- **Affects:** All 5 MAP sections — each needs a "how we met this" narrative, not necessarily verbatim execution
- **Requires:** Audit team confirmation — see [GAP-1](CONSISTENCY_REPORT.md#gap-1)

**DEC-RESET-EXPECTATIONS** {#dec-reset-expectations}: Reset expectations with Internal Audit on what was accomplished vs. originally planned
- **Date:** 2026-03-23
- **Source:** [SRC-MEETING-MAR23](SOURCES.md#src-meeting-mar23)
- **Participants:** Brian Day, JJ Sánchez
- **Rationale:** Documentation and narrative clarity are as important as technical fixes. Need to reconcile what audit flagged with what Service Tree believes is already fixed.
- **Affects:** Requires preparing a revised brief for audit
- **Action required:** Daysha to schedule meeting with audit contact

---

## Disputed Items

**DEC-KAUSHIK-DISPUTES** {#dec-kaushik-disputes}: Kaushik disputes items 14-15 on tracker
- **Date:** 2026-03-20
- **Source:** [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20)
- **Participants:** Kaushik Pushpavanam
- **Rationale:** "I didn't sign up to doing this... I don't even agree that this is the right thing to do." Items tagged "discuss" on tracker.
- **Affects:** ACT-014–ACT-015
- **Resolution:** Deferred to next sync (Kaushik unavailable next week — MVP week)
- **Kaushik's posture:** "Disagree and commit is not a problem for me. Let's be thoughtful."

**DEC-GOVERNANCE-NOT-PLATFORM** {#dec-governance-not-platform}: Platform team will not own governance items
- **Date:** 2026-03-20
- **Source:** [SRC-MEETING-MAR20](SOURCES.md#src-meeting-mar20)
- **Participants:** Chris Netz
- **Rationale:** "A number of things on there are not data accuracy issues — they are overall management, which is not something the platform team is ever going to own."
- **Affects:** Items requiring an accountable party within E+D for governance (not data accuracy)
- **⚠️ Note:** [GAP-2](CONSISTENCY_REPORT.md#gap-2) — No RACI exists for governance vs. data accuracy

---

## MAP Section Commitments (from formal MAP)

**DEC-MAP-SECTION-1** {#dec-map-section-1}: Roles & Responsibilities
- **Source:** [SRC-MAP](SOURCES.md#src-map) Section 1
- **Teams:** ES365, AEP, E+C
- **Commitments:** Document consumption programs (E+C, FY25H2), monitor BCDR champ (ES365, FY25H2), expand attestation (ES365, FY25H2), entitlements on ST roles (AEP, FY26)

**DEC-MAP-SECTION-2** {#dec-map-section-2}: Entry Requirements for Service Tree
- **Source:** [SRC-MAP](SOURCES.md#src-map) Section 2
- **Teams:** AEP, ES365, 1ES
- **Commitments:** Publish service type guidance (AEP, FY25H2), identify large services (ES365, FY25H2), educate group admins (AEP+ES365, FY25H2), code attribution (1ES+AEP+ES365, FY25H2)

**DEC-MAP-SECTION-3** {#dec-map-section-3}: Periodic Review of Service Tree Entries
- **Source:** [SRC-MAP](SOURCES.md#src-map) Section 3
- **Teams:** ES365
- **Commitments:** Distribute health reports (ES365, FY25H2), implement monitoring rules (ES365, FY25H2), expand automation (ES365, FY26)

**DEC-MAP-SECTION-4** {#dec-map-section-4}: Service Tree Metadata Fields
- **Source:** [SRC-MAP](SOURCES.md#src-map) Section 4
- **Teams:** ES365, AEP
- **Commitments:** Improve documentation (ES365, FY25H2), monitoring+automation 90% reduction target (ES365, FY25H2), define required fields by type (ES365+AEP, FY25H2), Service Tree view (AEP, FY25H2), upgrade policy engine (AEP, FY26), expand to less critical fields (ES365, FY26)

**DEC-MAP-SECTION-5** {#dec-map-section-5}: Data Quality Monitoring
- **Source:** [SRC-MAP](SOURCES.md#src-map) Section 5
- **Teams:** ES365, AEP, E+C
- **Commitments:** Require business logic from field owners (ES365, FY25H2), require monitoring plans before new fields (ES365+AEP, FY25H2), ICM escalation path (E+C, FY25H2), expand monitoring (ES365, FY26)
