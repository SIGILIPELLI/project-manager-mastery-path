# 09 · Reporting & Dashboards

Most project reports fail in the same way: they describe activity rather than
answer a question. Three pages of "the team continued integration work" tells
a sponsor nothing they can act on. **A report exists to support a decision —
if nothing in it could change what anyone does, it should not have been
written.** This module covers how to design a report around its audience,
which metrics belong on a dashboard, how to set red/amber/green thresholds
that mean something, and how to read a milestone trend that is quietly
telling you the forecast is fiction.

## Start with the decision, not the data

Before designing anything, answer three questions for each audience: what
decisions do they make, at what frequency, and what is the smallest set of
numbers that lets them make those decisions well?

| Audience | Decision they make | Cadence | Depth | Format |
|---|---|---|---|---|
| Delivery team | What do I work on next; what is blocked | Daily | Task level | Board + stand-up |
| Project manager | Where to intervene this week | Weekly | Work package | Full dashboard |
| Sponsor | Approve changes, remove obstacles, fund | Fortnightly | Milestone + EVM | 1 page + exceptions |
| Steering committee | Continue / adjust / stop; approve major change | Monthly | Objectives + risk | 1 page + decision log |
| Portfolio office | Compare against other projects | Monthly | Standard indices only | Automated feed |

The mistake is producing one report and sending it to everyone. The team's
board is meaningless to a steering committee, and the steering pack is far
too coarse for the team. **Same underlying data, different aggregation.**

## What belongs on a one-page dashboard

Nine panels are enough. More than that and the reader stops scanning and
starts skipping.

| Panel | Content | Answers |
|---|---|---|
| Overall RAG | One letter, plus a one-line reason | Is this project in trouble? |
| Schedule | SPI, next milestone, forecast vs baseline date | Will it land on time? |
| Cost | CPI, AC vs BAC, EAC and VAC | Will it land on budget? |
| Scope | Stories/deliverables done vs total; approved changes | Are we still building the same thing? |
| Quality | Open defects by severity, escaped defects | Will it actually work? |
| Top risks | Top 5 by exposure, with owner and next action | What could still go wrong? |
| Issues | Open issues past due, with owner | What has already gone wrong? |
| Decisions needed | Decision, options, cost of delay, needed-by date | What do you need from me? |
| Milestone trend | Forecast date for one key milestone, period by period | Is the forecast credible? |

The **Decisions needed** panel is the one that makes sponsors read the
report. If every report you send asks for nothing, you have trained your
audience that your reports are optional.

## The status report template

| Field | Content |
|---|---|
| Project / period | Warehouse Management System rollout — Period 8, w/e 24 Oct |
| Overall status | **Amber** — schedule slipping; cost favourable; one decision required |
| Status last period | Amber (2nd consecutive period) |
| Achieved this period | Site 3 cutover complete; integration test cycle 2 passed |
| Planned next period | Site 4 cutover; UAT entry review; performance retest |
| **Schedule** | SPI 0.92; UAT complete forecast 21 Oct vs baseline 30 Sep (**15 working days late**) |
| **Cost** | CPI 1.15; AC $400,000 of BAC $1,000,000; EAC $869,565 (**VAC +$130,435**) |
| Scope | 46% complete by value; 3 changes approved, 1 rejected this period |
| Quality | 18 open defects (2 severity-1); 9 escaped from the last release |
| Top risk | Site 4 network upgrade may slip — owner: Infrastructure Lead |
| Issue past due | Master data cleansing 6 days late — owner: Ops Manager |
| **Decision required** | Approve 2 extra testers ($34,000) **by 31 Oct** or UAT slips a further 10 days |

Note that the report is honest about the *second consecutive amber* and gives
the decision a deadline with a stated consequence. "Please advise" is not a
decision request; "approve by 31 Oct or lose 10 days" is.

## Worked example — the EVM panel

Everything in the cost and schedule rows above comes from four numbers taken
at the end of Period 8.

| Measure | Value |
|---|---|
| BAC — Budget at Completion | $1,000,000 |
| PV — Planned Value | $500,000 |
| EV — Earned Value | $460,000 |
| AC — Actual Cost | $400,000 |

Everything else is derived:

| Derived metric | Formula | Calculation | Result |
|---|---|---|---|
| Cost Variance | EV − AC | 460,000 − 400,000 | **+$60,000** |
| Schedule Variance | EV − PV | 460,000 − 500,000 | **−$40,000** |
| CPI | EV ÷ AC | 460,000 ÷ 400,000 | **1.15** |
| SPI | EV ÷ PV | 460,000 ÷ 500,000 | **0.92** |
| EAC (typical variance) | BAC ÷ CPI | 1,000,000 ÷ 1.15 | **$869,565** |
| ETC | EAC − AC | 869,565 − 400,000 | **$469,565** |
| VAC | BAC − EAC | 1,000,000 − 869,565 | **+$130,435** |
| TCPI (to BAC) | (BAC − EV) ÷ (BAC − AC) | 540,000 ÷ 600,000 | **0.90** |

Three ratios also belong on the panel because together they tell the story at
a glance:

- **Percent complete** = EV ÷ BAC = 46.0%
- **Percent spent** = AC ÷ BAC = 40.0%
- **Percent scheduled** = PV ÷ BAC = 50.0%

Read them in that order: we planned to be 50% through, we are 46% through,
and we have spent 40%. **The project is behind schedule and getting good
value for money.** TCPI of 0.90 says the remaining work may be delivered at
90% of the budgeted rate and still hit BAC — there is genuine cost headroom,
which is exactly why the $34,000 tester request is affordable.

!!! warning "Distrust a very favourable CPI early on"
    A CPI well above 1.0 in the first third of a project is more often an
    artefact than an achievement. The usual causes are supplier invoices that
    have not yet been accrued, timesheets booked to the wrong code, or work
    being claimed complete more generously than the completion rules allow.
    Before reporting CPI 1.15 as good news, check accruals and check how
    percent-complete was claimed. **Report the number, but report the
    caveat with it.**

## RAG thresholds that mean something

Most RAG statuses are a feeling. Publish the rules instead, agree them with
the sponsor at kickoff, and apply them mechanically.

| Dimension | Green | Amber | Red |
|---|---|---|---|
| Schedule (SPI) | ≥ 0.95 | 0.90 – 0.94 | < 0.90 |
| Cost (CPI) | ≥ 0.95 | 0.90 – 0.94 | < 0.90 |
| Key milestone | On or ahead of baseline | 1–10 working days late | > 10 working days late |
| Open severity-1 defects | 0 | 1–2 | 3 or more |
| Risk exposure vs reserve | < 60% of reserve | 60–90% | > 90% |
| Overall | All green | Any amber | Any red, **or** amber twice running with no recovery plan |

Applying the rules to the worked example: SPI 0.92 → **Amber**. CPI 1.15 →
Green. Key milestone 15 working days late → **Red**. Two severity-1 defects →
Amber. Overall status is therefore **Red by the milestone rule**, even though
the report above says Amber — which is precisely the argument the PM must
have with themselves before publishing. **If your rules say red, report red.**

!!! warning "Watermelon reporting"
    Green on the outside, red on the inside. It happens when status is set by
    judgement rather than rule, and it always ends the same way: a project
    that was green for eleven months goes red in month twelve and the
    sponsor's first question is why nobody told them. Mechanical thresholds
    exist to protect you from your own optimism — and from the pressure to be
    green that every reporting culture applies.

## Milestone trend analysis

The single most revealing chart on any dashboard is not a burndown. It is the
**forecast date for one key milestone, recorded once per reporting period**.

| Period reported | Forecast for "UAT complete" | Slip vs baseline (working days) | Slip added this period |
|---|---|---|---|
| P4 | 30 Sep | 0 | — |
| P5 | 30 Sep | 0 | 0 |
| P6 | 7 Oct | +5 | +5 |
| P7 | 14 Oct | +10 | +5 |
| P8 | 21 Oct | +15 | +5 |

This table says something no single-period status can: the milestone is
slipping **one week per week**, and has done so three periods running. A
forecast that moves by exactly one period every period is not a forecast at
all — it is the team reporting that they have not started the recovery.
Extrapolating the trend, the milestone will not be met until the underlying
cause is addressed, regardless of what date is currently written down.

Ask two questions whenever you see this shape: what changed in P6 to start
the slide, and what specific action is meant to stop it? "The team will work
harder" is not an answer; "two testers approved by 31 Oct" is.

## Leading and lagging indicators

Most dashboards are entirely lagging — they measure what has already
happened. Add at least two leading indicators, which move *before* the
outcome does.

| Type | Metric | What it tells you |
|---|---|---|
| Lagging | SPI, CPI, milestones met, defects escaped | Where you ended up |
| Leading | Requirements still unapproved | Future rework and change requests |
| Leading | Average age of open blockers | Whether impediment removal is working |
| Leading | Test cases written vs stories accepted | Whether QA will become the bottleneck |
| Leading | Risks with no owner or no next action | Whether risk management is real or ceremonial |
| Leading | Unplanned work as % of capacity | Whether the plan is being overrun by interrupts |

A rising average blocker age is visible weeks before it shows up as a fallen
SPI. That gap is the entire value of a leading indicator.

## Reporting anti-patterns

| Anti-pattern | Why it fails | Fix |
|---|---|---|
| Percent complete by task count | 90 of 100 tasks done says nothing about remaining effort | Weight by value or effort; use EV |
| Narrative with no numbers | Cannot be compared period to period | Every claim gets a metric |
| Numbers with no narrative | Reader cannot tell cause from noise | One sentence of *why* per red or amber |
| Report built by hand each period | Consumes a day; drifts in definition | Automate extraction; hand-write only commentary |
| Metrics used to judge people | People manage the metric, not the work | Report at project level, never individual level |
| Everything green until it isn't | Judgement-based status | Published thresholds, applied mechanically |

The last row of that table is the one worth writing on the wall. **Define
each metric in writing once — what counts as "done", which cost codes feed
AC, how percent-complete is claimed — and never change the definition
mid-project without saying so on the report.** A metric whose definition
moves silently is worse than no metric, because it looks comparable when it
is not.

## Exercise

Design the reporting for a real project.

1. Build the audience table for your project with at least four audiences,
   each with the specific decision they make, the cadence, and the format.
   Identify one report you currently produce that no listed audience needs.
2. Take a real reporting period and compute the full EVM panel: CV, SV, CPI,
   SPI, EAC, ETC, VAC and TCPI, showing the arithmetic. Then write the three
   ratios (percent complete, spent, scheduled) and the **one sentence** you
   would put on the dashboard to explain them.
3. Publish your RAG thresholds as a table covering at least four dimensions,
   with a rule for overall status. Apply them mechanically to your current
   period and state whether the honest colour differs from the one you would
   have chosen by instinct.
4. Build a milestone trend table for one key milestone across at least five
   past periods. State the per-period slip rate and what it predicts.
5. Choose three leading indicators for your project and explain, for each,
   how many weeks ahead of SPI or CPI you expect it to move.
6. Write one complete status report against the template. Include a
   **Decision required** row with the options, the cost of each, and the
   date beyond which the decision costs schedule.
