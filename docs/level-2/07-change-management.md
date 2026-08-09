# 07 · Change Management for Projects

"Change management" means two genuinely different disciplines, and conflating
them causes real damage. **Change control** is the governance process for
deciding whether a requested modification to the baseline gets approved.
**Organisational change management** is the people-side work of getting the
delivered product actually adopted. A project can execute flawless change
control and still fail because nobody uses what it built. This module covers
both, in that order.

## Part 1 — Change control

The purpose of change control is not to prevent change. It is to ensure that
every change is **assessed for its full impact and approved by someone with
the authority to accept that impact** before it is built.

Uncontrolled change has two forms worth naming separately:

| Term | What it is | Root cause |
|---|---|---|
| **Scope creep** | Uncontrolled additions from stakeholders, unassessed | No baseline, or no change process |
| **Gold plating** | The *team* adds unrequested polish | Team believes it knows better than the spec |

Both bypass the process. Both consume budget that was allocated to something
else. Gold plating is the more insidious because it feels like generosity.

### The change request template

| Field | Content |
|---|---|
| CR ID | CR-047 |
| Title | Add SSO via corporate identity provider |
| Raised by / date | Head of Security, 12 March |
| Type | Scope addition |
| Description | Replace local username/password with corporate SSO for all users |
| Business justification | Security policy mandates SSO for systems holding customer data by Q4 |
| **Cost impact** | +$62,000 (3 dev-weeks, IdP licence, security retest) |
| **Schedule impact** | +9 days on the critical path (integration → UAT) |
| **Scope impact** | Adds 4 stories; removes the local password reset story (−2 days) |
| **Quality impact** | Requires new penetration test before go-live |
| **Risk impact** | New: IdP team availability. Closes: R7 credential-storage risk |
| Options considered | (a) Full SSO now (b) SSO after go-live (c) Do nothing — breaches policy |
| Recommendation | Option (a): the policy deadline precedes our go-live |
| Decision / date / approver | Approved, 19 March, Steering Committee |

The five impact rows are the entire value of the form. A change request that
says "add SSO" with no impact assessment is not a change request, it is a
wish — and approving it commits the project to a cost nobody quantified.
Note that the assessment includes what the change **removes** (a story, a
risk), not just what it adds.

### The change control workflow

| Step | Who | Action | Output |
|---|---|---|---|
| 1. Submit | Anyone | Raise CR with description and justification | Logged CR, status *Submitted* |
| 2. Log | PM | Enter in the change log, assign an ID | Unique reference |
| 3. Assess | PM + leads | Full impact analysis on cost, schedule, scope, quality, risk | Completed CR |
| 4. Decide | CCB or delegated authority | Approve / reject / defer / request more info | Decision recorded |
| 5. Update baseline | PM | Re-baseline schedule, budget, scope; version the plan | New baseline |
| 6. Communicate | PM | Tell everyone affected what changed and why | Updated plan issued |
| 7. Verify | PM | Confirm the change was implemented as approved | Closed CR |

Step 5 is the one most often skipped, and skipping it silently destroys your
performance reporting. If a change adds $62,000 and 9 days but the baseline
is never updated, then from the next reporting period onward your EVM figures
(module 03) compare actuals against a plan that no longer exists — CPI and
SPI both degrade, and the cause is invisible. **An approved change that has
not been re-baselined will show up as poor performance.**

### Approval authority

Not every change needs a committee. Publish the thresholds:

| Change size | Authority | Target turnaround |
|---|---|---|
| < $5,000 and < 2 days, no scope change | Project Manager | 1 working day |
| < $25,000 and < 5 days | PM + Product Owner | 3 working days |
| < $100,000 and < 15 days | Change Control Board | Weekly CCB |
| Above that, or any change to project objectives | Sponsor / Steering Committee | Monthly, or called |

Turnaround times are a genuine part of the design. A CCB that meets monthly
and takes three weeks to decide will be bypassed by teams who need an answer,
and once it is routinely bypassed it exists on paper only. **Match the
cadence to the pace of delivery, or delegate more.**

### The change log

| CR | Title | Raised | Cost | Sched | Status | Decision date |
|---|---|---|---|---|---|---|
| 044 | Extra approval step in workflow | 02 Mar | +$8,000 | +2 d | Approved | 07 Mar |
| 045 | Custom branding on reports | 05 Mar | +$14,000 | +3 d | **Rejected** | 07 Mar |
| 046 | Extend data retention to 7 years | 09 Mar | +$21,000 | +4 d | Deferred to phase 2 | 14 Mar |
| 047 | Add SSO | 12 Mar | +$62,000 | +9 d | Approved | 19 Mar |
| 048 | Additional Spanish localisation | 20 Mar | +$38,000 | +12 d | Under assessment | — |
| | **Approved to date** | | **+$70,000** | **+11 d** | | |

Keep the rejected and deferred rows. When someone asks in month 8 why the
Spanish version does not exist, the log answers it. And the cumulative row is
the number that goes on the status report: **$70,000 and 11 days of approved
change** is a fact about the project that must be visible, or the eventual
overrun looks like poor delivery rather than accepted scope growth.

## Part 2 — Organisational change management

Delivering the product is not the objective; the benefit is realised only if
people change how they work. The standard model is **ADKAR** — five states
each individual must pass through, in order.

| Stage | The person must... | Fails when | Intervention |
|---|---|---|---|
| **A**wareness | Know why the change is happening | "Nobody told us this was coming" | Sponsor communication, town halls |
| **D**esire | Want to participate | "I understand it, but it's worse for me" | Address WIIFM, involve in design |
| **K**nowledge | Know how to work the new way | "I don't know how to do X now" | Training, documentation, job aids |
| **A**bility | Be able to do it in practice | "I did the training, but I'm slow and error-prone" | Floor-walking, practice environment, coaching |
| **R**einforcement | Keep doing it | Quiet reversion to the old system | Metrics, recognition, retire the old system |

The diagnostic power of ADKAR is that **it identifies which stage is
blocked** — and each has a different fix. If adoption is poor because people
do not want the change (Desire), more training (Knowledge) is wasted money;
the fix is addressing what they lose. Most failed rollouts respond to every
adoption problem with more training, because training is the easiest thing to
buy.

The most-skipped stage is **Reinforcement**. Teams celebrate go-live,
disband, and three months later half the users are back on spreadsheets. If
the old system is still available, some people will keep using it — a
decommissioning date is a change management intervention, not an IT task.

### Stakeholder resistance analysis

| Group | Current | Target | Main concern | Intervention | Owner |
|---|---|---|---|---|---|
| Branch staff (200) | Resistant | Supportive | "Slower than the old screens at first" | Practice environment 4 weeks early; super-users on the floor for 2 weeks | Ops Lead |
| Team leaders (24) | Neutral | Advocate | Accountable for team throughput during dip | Brief on expected 3-week productivity dip; adjust targets | Sponsor |
| Finance (12) | Supportive | Supportive | Month-end close must not slip | Dry-run a full close in parallel before cutover | Finance Lead |
| Regional managers (6) | Resistant | Neutral | Loss of local reporting customisation | Show new self-service reports; agree 3 must-have local reports | PM |

Being explicit that some groups only need to reach **Neutral** matters.
Trying to convert every stakeholder into an advocate wastes effort that
should go to the group whose resistance actually blocks go-live. Note also
the branch staff intervention: their concern is real, not irrational — the
new system *will* be slower for them at first, and a plan that denies this
loses credibility immediately.

!!! warning "Never assess a change request by cost alone"
    A $5,000 change that adds 9 days to the critical path is far more
    damaging than a $40,000 change that consumes float on a parallel path.
    Always assess schedule impact **against the network** (module 02), not
    against the effort estimate. The question is not "how much work is this?"
    but "does this move the end date?" — and only the critical path can
    answer that.

## Exercise

Build a complete change management approach for a project of your own.

1. Write your approval authority table with at least three tiers, giving
   monetary and schedule thresholds, the deciding body, and a **committed
   turnaround time** for each.
2. Take a realistic change request for your project and complete the full
   template, including all five impact rows. Assess the **schedule impact
   against your critical path** — state whether it consumes float or moves
   the end date, and by how many days.
3. Give the change at least two genuine alternative options and a
   recommendation with reasoning.
4. Build a change log with at least six CRs including at least one rejected
   and one deferred, and compute the **cumulative approved cost and schedule
   impact**. Write the one sentence about it you would put in a status
   report.
5. Pick one stakeholder group that will resist. Diagnose which **ADKAR stage
   they are blocked at**, justify the diagnosis, and design an intervention
   that targets that specific stage — then state why the obvious response
   (more training) would or would not work.
6. Build the resistance analysis table for at least four groups, with current
   and target positions, and state explicitly which groups you are *not*
   trying to convert to advocates and why.
