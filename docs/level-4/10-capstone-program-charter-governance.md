# 10 · Capstone — Full Program Charter & Governance Model

This capstone integrates the entire course: a full program charter and
governance model for a realistic, multi-year initiative, applying program
structure (L3 M1), portfolio-style prioritisation (L3 M2), quantified risk
(L3 M3), vendor terms (L3 M4), PMO governance (L3 M5, L4 M1), transformation
adoption planning (L4 M3), crisis protocols (L4 M4), and executive reporting
(L4 M5) as one coherent deliverable.

## The scenario

A regional healthcare provider is running a 3-year digital transformation
program to replace paper-based patient intake with a unified digital
platform across 12 clinics, integrating scheduling, billing, and clinical
records. This is precisely the kind of program where the technology is the
easier half and adoption is the real risk (Level 4, module 03).

## Section 1 — Program charter

| Field | Content |
|---|---|
| Program name | Unified Patient Platform (UPP) |
| Sponsor | Chief Operating Officer |
| Program Director | Newly promoted from Senior PM (module 09 transition in progress) |
| Duration | 3 years, 6 six-month phases |
| Budget | $18,000,000 |
| Primary benefit | Reduce average patient intake time from 22 minutes to 8 minutes across all 12 clinics |
| Secondary benefits | Cut billing error rate from 6% to under 1.5%; enable single patient record across clinics |
| Constituent projects | (1) Core platform build, (2) Clinic-by-clinic rollout (12 waves), (3) Billing system integration, (4) Clinical staff training & change management |

## Section 2 — Benefits map

| Benefit | Target | Owner | Contributing projects | Realisation checkpoint |
|---|---|---|---|---|
| Intake time reduction | 22min → 8min | COO | Core platform, Rollout, Training | Measured per clinic, 3 months post-go-live |
| Billing error reduction | 6% → 1.5% | CFO | Billing integration, Training | Measured quarterly post-go-live |
| Unified patient record | 100% of clinics on one record | CMO | Core platform, Rollout | At full rollout completion (end of year 2) |

## Section 3 — Governance structure

| Layer | Body | Cadence | Decision authority |
|---|---|---|---|
| Program team | Program Director + 4 project leads | Weekly | Operational trade-offs |
| Steering committee | COO, CFO, CMO, Program Director | Monthly | Cross-project resourcing, scope changes over $50,000 |
| Executive sponsor review | COO + CEO | Quarterly | Exception report only (L4 M5) — go/no-go on next phase funding |
| Stage gates | Per Level 3 M5 model | End of each 6-month phase | Phase funding release |

### Stage-gate criteria (applied to this program)

| Gate | Phase | Criteria to pass |
|---|---|---|
| G1 | End of Phase 1 (core platform design) | Architecture approved; pilot clinic identified; vendor contract for billing integration signed |
| G2 | End of Phase 2 (pilot clinic go-live) | Pilot clinic intake time under 12 minutes (interim target, not final 8); adoption metrics tracked per L4 M3 |
| G3 | End of Phase 3 (waves 2–5) | 5 clinics live; billing error rate trending toward target; no unresolved Red risk |
| G4 | End of Phase 4 (waves 6–12) | All 12 clinics live; full-rollout benefit data collected |

## Section 4 — Quantified risk register (program level)

| ID | Risk | Probability | Impact | EMV | Response |
|---|---|---|---|---|---|
| R1 | Clinical staff resist new intake workflow (adoption trough, L4 M3) | 45% | $600,000 (extended parallel running, lost efficiency) | $270,000 | Mitigate: dedicated change management workstream, phased cutover per clinic |
| R2 | Billing integration vendor underestimates legacy system complexity | 30% | $400,000 (change order) | $120,000 | Mitigate: fixed-price contract with a completed legacy-system audit precondition (L3 M4 pattern) |
| R3 | Patient data migration error causes a compliance incident | 8% | $2,000,000 (regulatory fine + reputational, L4 M4 crisis territory) | $160,000 | Avoid: staged migration with validation gate per clinic, no big-bang cutover |

```
python3 -c "print(0.45*600000, 0.30*400000, 0.08*2000000, 0.45*600000+0.30*400000+0.08*2000000)"
```
→ $270,000 + $120,000 + $160,000 = **$550,000 total program contingency
reserve.**

## Section 5 — Adoption plan (per Level 4, module 03)

| Clinic wave | Go-live | Parallel running window | Hard cutover date | Incentive |
|---|---|---|---|---|
| Pilot | Month 7 | 4 weeks | Month 8 | Front-desk staff recognition + workflow-efficiency bonus pool |
| Waves 2–5 | Months 10–16 | 3 weeks each | 3 weeks post go-live per clinic | Same, tuned from pilot learnings |
| Waves 6–12 | Months 19–30 | 2 weeks each (learning curve shortened by experience) | 2 weeks post go-live per clinic | Same |

## Section 6 — Crisis protocol (pre-defined, per Level 4, module 04)

| Scenario | Incident Commander | First action |
|---|---|---|
| Patient data breach | CISO | Contain, notify legal (regulatory clock), holding statement within 2 hours |
| Platform outage during clinic hours | Core platform tech lead's manager (not the on-call engineer) | Fail back to paper intake per pre-built contingency procedure, communicate to affected clinics immediately |
| Billing integration produces systematic overcharges | CFO | Halt affected billing runs, initiate patient-facing correction communication within 24 hours |

Pre-defining these three scenarios *before* the program goes live, rather
than improvising incident command structure during an actual crisis, is the
single governance decision most likely to determine whether a real incident
during this 3-year program is a contained event or a compounding one.

## Section 7 — Executive reporting cadence (per Level 4, module 05)

Quarterly exception report to the CEO covers only: (1) phase gate status
(pass/fail/at-risk), (2) reserve balance against the $550,000 total, (3) any
Red-rated risk, (4) adoption metrics against the intake-time target. Every
other data point stays at the steering committee level, not the executive
level — consistent with this level's principle that reporting detail should
shrink, not stay constant, as it moves up the governance layers.

## Stretch goals

- Build a full EVM tracking table for Phase 1 (invent plausible PV/EV/AC
  figures against a $3,000,000 Phase 1 budget) and calculate CPI, SPI, and
  EAC using the "both" method from Level 3, module 09 — verify with
  `python3 -c`.
- Extend the risk register with a fourth, program-spanning risk that
  correlates R1 and R2 (e.g., a shared root cause in change-management
  bandwidth), and recompute the total reserve.
- Draft the G2 stage-gate review memo as if the pilot clinic's actual
  intake time came in at 14 minutes against a 12-minute interim target —
  decide, with justification, whether the program passes G2, passes
  conditionally, or is sent to the recovery process from Level 3, module
  08.
