# 10 · Project — Agile Plan with Sprint Schedule

Everything in Level 2 has been taught one discipline at a time: sprints in
one module, float in another, earned value in a third, risk and quality and
reporting each in their own. Real projects do not arrive in that shape. They
arrive as one delivery that has to be planned, sequenced, de-risked,
quality-gated and reported on **at the same time, from the same set of
numbers**.

This capstone builds a complete agile delivery plan for one project and then
demands the thing that separates a plan from a document: **internal
consistency**. The velocity in the sprint plan must produce the forecast in
the dashboard. The contingency reserve must be sized by the risk register,
not chosen. The defect data behind the quality gate must be the same data the
dashboard reports. If you can change one number in one artefact and nothing
else moves, the artefacts are not connected and the plan is decoration.

## The worked project

| Attribute | Value |
|---|---|
| Project | MemberHub — customer self-service portal (replaces phone-only servicing) |
| Sponsor | Director of Customer Operations |
| Delivery model | Scrum, 2-week sprints, 5 sprints planned (10 weeks / 50 working days) |
| Team | 6 people: PO, Scrum Master, 3 developers, 1 tester |
| Backlog at baseline | 200 story points, estimated by planning poker |
| Cost baseline (BAC) | $200,000 — a flat team burn of $40,000 per sprint |
| Derived rate | $200,000 ÷ 200 points = **$1,000 per story point** |
| Contingency reserve | $52,000 (sized in the risk register below) |
| Management reserve | $20,000, sponsor-controlled |
| Total funding envelope | $272,000 |

The $1,000-per-point rate is what makes agile delivery legible to earned
value. Points are the measure of work; the rate converts accepted points into
earned value without inventing a second tracking system.

---

## Artefact 1 — the release and sprint plan

| Sprint | Dates (working days) | Sprint goal | Planned points | Cumulative planned |
|---|---|---|---|---|
| 1 | 1–10 | Login, account view, audit logging | 40 | 40 |
| 2 | 11–20 | Payment history, statement download | 40 | 80 |
| 3 | 21–30 | Update payment method, address change | 40 | 120 |
| 4 | 31–40 | Claims submission, document upload | 40 | 160 |
| 5 | 41–50 | Notifications, accessibility fixes, hardening | 40 | 200 |

The plan assumes a baseline velocity of 40 points per sprint. That is a
**forecast, not a commitment** — the only honest thing to do with it is to
replace it with measured velocity as soon as three sprints of real data
exist, which is exactly what happens below.

### Sprint backlog template

One sprint is planned in detail; the rest are goals only. Planning all five
sprints to task level would be four sprints of waste.

| Story ID | Story | Points | Acceptance criteria | Owner | Status |
|---|---|---|---|---|---|
| MH-104 | As a member I can view my payment history for 24 months | 8 | 24 months returned; paginated at 12; empty state handled | Dev A | Done |
| MH-105 | As a member I can download a statement as PDF | 5 | PDF matches the on-screen figures; generated < 3 s | Dev B | Done |
| MH-109 | As a member I can filter payments by date range | 3 | Invalid ranges rejected with a message; defaults to 12 months | Dev A | In test |
| MH-112 | As an agent I can see what a member saw, for support calls | 8 | Read-only; access written to the audit log | Dev C | In progress |

## Velocity and the forecast it produces

After three sprints there is real data, and it does not match the plan.

| Sprint | Committed | Accepted | Variance | Note |
|---|---|---|---|---|
| 1 | 40 | 36 | −4 | Environment access lost 2 days |
| 2 | 40 | 41 | +1 | Recovered one carried story |
| 3 | 40 | 35 | −5 | Two developers pulled to a production incident |

- Total accepted after 3 sprints = 36 + 41 + 35 = **112 points**
- Measured average velocity = 112 ÷ 3 = **37.3 points per sprint**
- Backlog remaining = 200 − 112 = **88 points**
- Sprints still required = 88 ÷ 37.3 = **2.36 sprints**
- Total forecast = 3 + 2.36 = **5.36 sprints** against a 5-sprint plan

The forecast overruns by 0.36 of a sprint — about **4 working days** — but
sprints are not divisible, so in practice this is a **sixth sprint** or a
scope reduction of roughly 14 points. Say that to the sponsor in those terms.
"We are tracking slightly behind" is not a decision; "one more sprint at
$40,000, or cut 14 points from Sprint 5" is.

## Artefact 1b — the enabling track, critical path and float

Not everything in a delivery is a story. The enabling work — environments,
contracts, security testing, cutover — is a dependency network and behaves
like one. This track starts on **day 11** (the start of Sprint 2) and gates a
go-live review on **day 50**.

| ID | Activity | Duration | Predecessor | ES | EF | LS | LF | Float |
|---|---|---|---|---|---|---|---|---|
| A | Provision environments | 5 | — | 0 | 5 | 0 | 5 | **0** |
| B | Identity / SSO integration | 10 | A | 5 | 15 | 5 | 15 | **0** |
| C | Payment gateway contract + sandbox | 12 | A | 5 | 17 | 11 | 23 | 6 |
| D | Data migration build | 8 | B | 15 | 23 | 15 | 23 | **0** |
| E | Security penetration test | 6 | C, D | 23 | 29 | 23 | 29 | **0** |
| F | Production cutover rehearsal | 3 | E | 29 | 32 | 29 | 32 | **0** |

Days are counted from the start of the track. Reading the network:

- **Critical path = A → B → D → E → F**, total 5 + 10 + 8 + 6 + 3 = **32 days**.
- Activity **C has 6 days of free float**: it can finish as late as day 23
  without moving E, because D also feeds E and D does not finish until day 23.
- The track starts on day 11, so cutover rehearsal completes on project day
  11 + 32 = **day 43**, against a go-live gate on **day 50** — **7 days of
  project-level slack**.

Those 7 days are the entire buffer protecting go-live, and the velocity
forecast above already wants 4 of them. **The buffer is 3 days deep, not 7.**
Two independent artefacts are pointing at the same conclusion, which is what
consistency looks like when it is working.

---

## Artefact 2 — the risk register

Probability is a decimal, impact is a cost, and **EMV = probability ×
impact**. The register is sorted by EMV because that is the order in which
attention is worth spending.

| ID | Risk (cause → event → effect) | P | Impact | EMV | Response | Owner |
|---|---|---|---|---|---|---|
| R1 | Because the gateway vendor certifies in monthly windows, certification may miss the window, delaying payment stories | 0.40 | $30,000 | **$12,000** | Mitigate — book the window in Sprint 1, not Sprint 3 | PM |
| R3 | Because the portal is the first internet-facing service, pen testing may find severity-1 findings needing rework | 0.50 | $24,000 | **$12,000** | Mitigate — threat-model in Sprint 2; pre-scan before formal test | Security Lead |
| R2 | Because one developer holds all legacy billing knowledge, their loss would stall integration | 0.20 | $45,000 | **$9,000** | Mitigate — pair on all billing stories; document the interface | Eng Manager |
| R5 | Because sprint demos attract new stakeholders, scope may grow beyond the 200-point baseline | 0.60 | $15,000 | **$9,000** | Mitigate — all demo requests enter the backlog, none enter the sprint | PO |
| R4 | Because legacy address data was never validated, migration quality may be worse than sampled | 0.30 | $20,000 | **$6,000** | Mitigate — profile 100% of records in Sprint 2, not a sample | Data Lead |
| R6 | Because load profiles are estimated, the portal may fail the 2-second SLA at peak | 0.25 | $16,000 | **$4,000** | Mitigate — load test from Sprint 3, not at the end | Tech Lead |
| | **Total expected monetary value** | | | **$52,000** | | |

The contingency reserve is **$52,000 because the register says $52,000** —
not because someone applied 25% to the budget and it felt about right. When
a risk closes, its EMV is released from the reserve and the number moves.
A reserve that never changes is not being managed.

---

## Artefact 3 — the quality plan

### Definition of Done

A story is not done until every line is true. This is a gate, not a
preference — one unchecked line means the story is not accepted and its
points are not earned.

| # | Criterion | Evidence |
|---|---|---|
| 1 | Acceptance criteria demonstrated by the tester, not the developer | Test run recorded against the story |
| 2 | Peer review complete, comments resolved | Approved review on the change |
| 3 | Unit and integration tests pass in CI | Green pipeline on the merge commit |
| 4 | No new severity-1 or severity-2 defects | Defect tracker query attached |
| 5 | Accessibility checked (keyboard, contrast, labels) | Checklist per screen |
| 6 | Response time within SLA under the standard load profile | Load test result |
| 7 | Audit logging present for any data change | Log sample |
| 8 | User-facing text reviewed by Customer Operations | Sign-off in the story |

### Release readiness checklist (go-live gate, day 50)

| Gate | Threshold | Status at Sprint 3 |
|---|---|---|
| Severity-1 defects open | 0 | 2 — **not met** |
| Severity-2 defects open | ≤ 3 | 5 — **not met** |
| Pen test findings closed | 100% of high | Test not yet run (day 29 of track) |
| Data migration accuracy | ≥ 99.5% on full run | 97.8% on profile run — **not met** |
| Rollback rehearsed | Once, end to end | Scheduled day 32 |
| Support team trained | 100% of tier-1 agents | 0% — starts Sprint 4 |

### Pareto analysis of defect causes

200 defects have been raised across the first three sprints. Sorted by
frequency:

| Cause | Defects | % of total | Cumulative % |
|---|---|---|---|
| Ambiguous acceptance criteria | 76 | 38.0% | 38.0% |
| Test data not representative of production | 48 | 24.0% | 62.0% |
| Third-party API behaviour changed | 30 | 15.0% | 77.0% |
| Browser / device compatibility | 20 | 10.0% | 87.0% |
| Performance under load | 14 | 7.0% | 94.0% |
| Copy and content errors | 8 | 4.0% | 98.0% |
| Other | 4 | 2.0% | 100.0% |
| **Total** | **200** | **100%** | |

**Three causes out of seven produce 154 of 200 defects — 77%.** The action
that follows is not "improve quality"; it is to fix acceptance-criteria
writing and test data, because those two alone account for 62%. Note the
loop back to Artefact 1: ambiguous acceptance criteria is a *refinement*
failure, so the fix lives in the sprint process, not in the test phase.

---

## Artefact 4 — the reporting dashboard

### Earned value at the end of Sprint 3

Points convert to money at $1,000 per point, so the EVM inputs fall straight
out of the velocity table.

| Input | Derivation | Value |
|---|---|---|
| BAC | 200 points × $1,000 | $200,000 |
| PV | 120 points planned × $1,000 | $120,000 |
| EV | 112 points accepted × $1,000 | $112,000 |
| AC | Actuals from timesheets and contractor invoices | $128,000 |

| Metric | Formula | Calculation | Result |
|---|---|---|---|
| Cost Variance | EV − AC | 112,000 − 128,000 | **−$16,000** |
| Schedule Variance | EV − PV | 112,000 − 120,000 | **−$8,000** |
| CPI | EV ÷ AC | 112,000 ÷ 128,000 | **0.875** |
| SPI | EV ÷ PV | 112,000 ÷ 120,000 | **0.933** |
| EAC | BAC ÷ CPI | 200,000 ÷ 0.875 | **$228,571** |
| ETC | EAC − AC | 228,571 − 128,000 | **$100,571** |
| VAC | BAC − EAC | 200,000 − 228,571 | **−$28,571** |
| TCPI (to BAC) | (BAC − EV) ÷ (BAC − AC) | 88,000 ÷ 72,000 | **1.222** |

Read the three ratios in order: **planned 60% complete** (PV ÷ BAC),
**actually 56% complete** (EV ÷ BAC), **spent 64%** (AC ÷ BAC). Behind and
overspent, both mildly, both in the same direction.

Two cross-checks confirm the artefacts agree:

- SPI 0.933 implies a duration of 5 ÷ 0.933 = **5.36 sprints** — the exact
  figure the velocity forecast produced independently.
- The VAC of $28,571 consumes 28,571 ÷ 52,000 = **55% of the contingency
  reserve**, which by the risk-exposure threshold below is amber, not red.

TCPI 1.222 is the number to argue about. It says every remaining dollar must
buy 22% more work than every dollar so far has bought. Nothing in the
velocity data suggests the team is about to become 22% more efficient.
**Report EAC $228,571 as the forecast, and treat "we'll recover it" as a
claim requiring evidence.**

### The one-page sprint dashboard

| Panel | Value at Sprint 3 | Rule | Status |
|---|---|---|---|
| Overall | Behind, overspent, quality gates failing | See below | **Red** |
| Schedule | SPI 0.933; forecast 5.36 sprints vs 5 planned | Amber 0.90–0.94 | Amber |
| Cost | CPI 0.875; EAC $228,571; VAC −$28,571 | Red < 0.90 | **Red** |
| Scope | 112 of 200 points accepted (56%); 0 changes approved | — | Green |
| Quality | 2 severity-1 open; migration accuracy 97.8% vs 99.5% | Red ≥ 3 sev-1 | Amber |
| Risk | Reserve consumed 55% ($28,571 of $52,000) | Amber 60–90% | Green |
| Float | Enabling track has 7 days; forecast wants 4 | < 5 days spare = amber | Amber |
| Decision needed | Approve Sprint 6 ($40,000) **or** cut 14 points by day 30 | — | Open |

Overall is **Red on the CPI rule**, and stays red however uncomfortable the
conversation is. The decision panel is what makes the report worth sending:
it names two options, prices both, and gives the date beyond which the choice
is made by default.

## Exercise

Build the same four connected artefacts for a project of your own — reuse the
backlog, risk register or dashboard you produced in this level's earlier
exercises if they fit, or start fresh.

1. **Sprint plan.** Define a backlog in points, a baseline velocity, a sprint
   count and a cost baseline. Derive your cost-per-point and state it
   explicitly. Plan one sprint to story level with acceptance criteria; plan
   the rest to goal level only.
2. **Velocity forecast.** Invent (or use real) accepted points for the first
   three sprints. Compute measured velocity, remaining backlog, sprints
   required and total forecast sprints. Convert the overrun into either a
   cost or a scope reduction, in numbers.
3. **Enabling track.** Build a network of at least six non-story activities
   with dependencies. Do the forward and backward pass, identify the critical
   path, and find at least one activity with float. State how much project
   slack protects go-live and how much of it the velocity forecast consumes.
4. **Risk register.** At least six risks in cause → event → effect form, each
   with probability, cost impact, EMV and a named owner. Total the EMV and
   set your contingency reserve to that total.
5. **Quality plan.** Write a Definition of Done of at least eight checkable
   lines with evidence for each, a release-readiness gate with thresholds,
   and a Pareto table of defect causes whose percentages sum to 100%. State
   which few causes give you the majority of the defects, and what you will
   change because of it.
6. **Dashboard.** Compute CV, SV, CPI, SPI, EAC, ETC, VAC and TCPI from your
   own points and actuals. Then prove consistency two ways: show that
   sprints ÷ SPI matches your velocity forecast, and that your VAC as a
   percentage of the contingency reserve matches your risk panel.
7. **The consistency test.** Change your Sprint 3 accepted points by ±5 and
   list every number across all four artefacts that must move. If fewer than
   six numbers move, your artefacts are not yet connected — find the
   disconnection and fix it.

## Stretch goals

- **Re-baseline properly.** Sprint 6 is approved. Produce the revised
  baseline: new BAC, new sprint plan, and the change record explaining what
  was approved, by whom and on what date. Then compute EVM against the *new*
  baseline and against the *original* one, and explain to a sponsor why the
  second number still matters.
- **Model the risk instead of averaging it.** Take your six risks and run a
  simple three-point analysis on total exposure: best case (no risk occurs),
  expected case (EMV total), worst case (all risks occur). Compare the worst
  case against your contingency reserve and state what you would tell the
  sponsor about reserve adequacy.
- **Add a leading indicator.** Choose one metric that would have predicted
  the Sprint 3 velocity drop *before* it happened — unplanned work as a
  percentage of capacity is a good candidate. Backfill it for three sprints
  and show whether it moved first.
- **Kill a story.** Identify the 14 points you would cut instead of funding
  Sprint 6, justify each cut against the sponsor's original business
  objective, and write the two-paragraph recommendation you would actually
  send.
