# 03 · Earned Value Management Basics

Ask a project manager "are we on budget?" and the weak answer compares money
spent against money planned. That comparison is close to meaningless: a team
that has spent 60% of the budget might be 80% complete and thriving, or 30%
complete and in serious trouble. Both look identical on a spend-versus-plan
chart. **Earned Value Management (EVM) fixes this by introducing a third
number — the value of the work actually completed — so that cost performance
and schedule performance can be separated and measured in the same units.**

Every number in this module is computed from the same scenario, so you can
verify each formula as it appears.

## The three base measures

Everything in EVM derives from three quantities, all expressed in currency.

| Term | Full name | Plain meaning |
|---|---|---|
| **PV** | Planned Value | Budgeted cost of the work **scheduled** to be done by now |
| **EV** | Earned Value | Budgeted cost of the work **actually completed** by now |
| **AC** | Actual Cost | What was **actually spent** to complete that work |
| **BAC** | Budget at Completion | The total approved budget for the whole project |

The critical subtlety is that **EV is measured in budgeted currency, not
actual currency**. If a task was budgeted at $10,000 and it is now finished,
it has earned $10,000 of value — even if it cost $18,000 to complete. The
$8,000 overrun shows up in AC, not in EV. Keeping those separate is what
makes the whole method work.

EV requires a rule for crediting partially-complete work. Pick one and apply
it consistently:

| Rule | How it credits | Best for |
|---|---|---|
| 0/100 | Nothing until complete, then 100% | Short tasks; most conservative |
| 50/50 | 50% at start, 50% at completion | Medium tasks, high volume |
| % complete | Assessor's judgement of progress | Long tasks — but easy to game |
| Milestone weighted | Fixed credit at defined milestones | Long tasks with verifiable checkpoints |

The `% complete` rule is the most common and the most abused. "It's 90% done"
for three consecutive months is the classic failure, and it corrupts every
downstream number. Milestone-weighted credit is the usual cure.

## The formula reference

Keep this table; it is the entire method on one page.

| Metric | Formula | Reads as |
|---|---|---|
| Cost Variance | `CV = EV − AC` | Negative = over budget |
| Schedule Variance | `SV = EV − PV` | Negative = behind schedule |
| Cost Performance Index | `CPI = EV ÷ AC` | Below 1.0 = over budget |
| Schedule Performance Index | `SPI = EV ÷ PV` | Below 1.0 = behind schedule |
| EAC — current rate continues | `EAC = BAC ÷ CPI` | Default forecast |
| EAC — variance was one-off | `EAC = AC + (BAC − EV)` | Optimistic forecast |
| EAC — cost *and* schedule pressure | `EAC = AC + (BAC − EV) ÷ (CPI × SPI)` | Pessimistic forecast |
| Estimate to Complete | `ETC = EAC − AC` | Cash still required |
| Variance at Completion | `VAC = BAC − EAC` | Projected final over/underrun |
| To-Complete Performance Index | `TCPI = (BAC − EV) ÷ (BAC − AC)` | Efficiency now required |

Two memory aids make these hard to get wrong. **Everything starts with EV** —
every variance and index has EV as its first term. And **variances subtract,
indices divide**; if the word is "variance" the answer is in currency, if it
is "index" the answer is a ratio around 1.0.

## A fully worked example

A 12-month office relocation programme. **BAC = $480,000.** At the end of
month 4, the reporting pack shows:

| Measure | Value | Where it comes from |
|---|---|---|
| **PV** | $180,000 | The baseline says $180,000 of work should be done by now |
| **EV** | $150,000 | Completed work, valued at its budgeted cost |
| **AC** | $175,000 | Invoices and timesheets actually booked |

**Step 1 — variances.**

```
CV = EV − AC = 150,000 − 175,000 = −$25,000   (over budget)
SV = EV − PV = 150,000 − 180,000 = −$30,000   (behind schedule)
```

**Step 2 — performance indices.**

```
CPI = EV ÷ AC = 150,000 ÷ 175,000 = 0.857
SPI = EV ÷ PV = 150,000 ÷ 180,000 = 0.833
```

Read those out loud, because this is the sentence that goes in the status
report: **we are getting 85.7 cents of value for every dollar we spend, and
we are progressing at 83.3% of the planned rate.** Both are below 1.0, so the
project is over budget *and* behind schedule simultaneously — the worst of
the four quadrants.

**Step 3 — sanity-check against the naive view.**

| View | Calculation | Result |
|---|---|---|
| Work complete | 150,000 ÷ 480,000 | **31.25%** |
| Budget spent | 175,000 ÷ 480,000 | **36.46%** |
| Work planned | 180,000 ÷ 480,000 | **37.50%** |

A manager reporting only "we've spent 36% of budget in month 4 of 12" would
sound comfortably ahead. In fact only 31.25% of the work is done. The gap
between 36.46% and 31.25% is precisely the problem EVM exists to expose.

**Step 4 — forecast the final cost.** Three EAC formulas, three assumptions:

| Assumption | Formula | Calculation | EAC | VAC |
|---|---|---|---|---|
| Overrun was a one-off | `AC + (BAC − EV)` | 175,000 + 330,000 | **$505,000** | −$25,000 |
| Current CPI continues | `BAC ÷ CPI` | 480,000 ÷ 0.857 | **$560,000** | −$80,000 |
| CPI *and* SPI pressure | `AC + (BAC−EV) ÷ (CPI×SPI)` | 175,000 + 330,000 ÷ 0.714 | **$637,000** | −$157,000 |

The spread between $505,000 and $637,000 is the honest uncertainty, and the
right move is to present all three with their assumptions rather than pick
one. That said, the middle figure is the default for a reason: decades of
programme data show that **CPI tends to stabilise after roughly 20% of the
work is complete and rarely recovers on its own**. At 31% complete, the
$560,000 forecast is the one to plan against. `ETC = 560,000 − 175,000 =
$385,000` is the cash still needed.

**Step 5 — how good would we have to become?**

```
TCPI = (BAC − EV) ÷ (BAC − AC)
     = (480,000 − 150,000) ÷ (480,000 − 175,000)
     = 330,000 ÷ 305,000
     = 1.082
```

To land on the original $480,000 budget, the remaining work must be delivered
at **1.082 efficiency** — by a team that has so far demonstrated 0.857. That
is a required 26% improvement in cost efficiency, sustained for eight months,
with no plan change. **A TCPI more than about 5% above the demonstrated CPI
is the signal to re-baseline rather than promise recovery.** Reporting "we
will catch up" here is not optimism, it is a forecast contradicted by your
own data.

**Step 6 — schedule forecast.** If the SPI trend holds, 12 ÷ 0.833 = **14.4
months**, so roughly 2.4 months late. Treat this as an indicator, not a
schedule: EVM measures schedule in currency, so it cannot tell whether the
slippage is on the critical path. Always confirm against the network
(module 02) before quoting a date.

## Reading the four quadrants

Two indices give four situations, each with a different response.

| CPI | SPI | Situation | Typical response |
|---|---|---|---|
| ≥ 1.0 | ≥ 1.0 | Under budget, ahead | Verify EV isn't inflated by a loose % complete rule |
| ≥ 1.0 | < 1.0 | Under budget, behind | Resources available — consider crashing |
| < 1.0 | ≥ 1.0 | Over budget, ahead | Often bought speed with overtime; check it's deliberate |
| < 1.0 | < 1.0 | Over budget, behind | Escalate; re-baseline is likely |

The second row is the useful one. Being under budget and behind schedule
usually means you are under-resourced, not efficient — and the money to fix
it is already in the budget.

!!! warning "EVM is only as honest as the EV number"
    Every figure above descends from EV. If teams self-report percent
    complete against no verifiable criteria, EV inflates, CPI and SPI both
    look healthier than reality, and the EAC understates the overrun until
    it is too late to act. Tie EV credit to the same Definition of Done or
    milestone acceptance you use elsewhere. An EVM report built on optimistic
    self-assessment is worse than no report, because it carries false
    authority.

## Exercise

Set up EVM for a project of your own with at least eight work packages.

1. Build the cost baseline: list each work package with its budgeted cost,
   and state your BAC. Spread the budget across at least six reporting
   periods to produce the PV curve.
2. State which EV credit rule you are using for partially-complete work, and
   justify it in one sentence.
3. Pick a status date roughly one third of the way through and record PV, EV
   and AC. Then compute, showing every step: **CV, SV, CPI, SPI**.
4. Compute all three **EAC** variants, plus **ETC** and **VAC** for each.
   State which one you would report to the sponsor and why.
5. Compute **TCPI** against BAC. Compare it to your demonstrated CPI and
   state plainly whether recovery to the original budget is credible — if it
   is not, say what you would re-baseline to.
6. Write the three-sentence status paragraph you would actually send. It must
   quote CPI and SPI in plain language ("we are getting X cents of value per
   dollar"), give the forecast final cost, and name one corrective action.
