# 09 · Advanced Metrics (EVM Deep Dive & Forecasting)

Level 2 introduced CPI and SPI as a health check. This module goes further:
the full family of EVM formulas, three different EAC forecasting methods
that give different answers depending on what you assume about the future,
and the To-Complete Performance Index that tells you exactly how hard the
remaining work has to go to hit a target.

## The complete EVM formula reference

| Metric | Formula | Meaning |
|---|---|---|
| PV (Planned Value) | Budgeted cost of work scheduled | What you planned to have spent by now |
| EV (Earned Value) | Budgeted cost of work actually performed | What the completed work is "worth" |
| AC (Actual Cost) | Actual cost of work performed | What you actually spent |
| CV (Cost Variance) | EV − AC | Positive = under budget |
| SV (Schedule Variance) | EV − PV | Positive = ahead of schedule |
| CPI (Cost Performance Index) | EV / AC | >1 = efficient spending |
| SPI (Schedule Performance Index) | EV / PV | >1 = ahead of schedule |
| BAC (Budget at Completion) | Total planned budget | The original target |
| EAC (Estimate at Completion) | See three methods below | Projected final cost |
| ETC (Estimate to Complete) | EAC − AC | Projected remaining cost |
| VAC (Variance at Completion) | BAC − EAC | Projected final over/under |
| TCPI (To-Complete Performance Index) | (BAC − EV) / (BAC − AC) | CPI required on remaining work to hit BAC |

## Three EAC forecasting methods

The choice of EAC formula is a statement about what you believe caused past
variance and whether it will continue.

| Method | Formula | Assumption |
|---|---|---|
| EAC (typical variance) | BAC / CPI | Past cost performance will continue exactly as-is |
| EAC (atypical variance) | AC + (BAC − EV) | The variance so far was a one-off; remaining work proceeds at the original budget rate |
| EAC (both CPI and SPI matter) | AC + [(BAC − EV) / (CPI × SPI)] | Both cost *and* schedule performance will continue to affect remaining cost |

### Worked example: three EACs from one dataset

A project: BAC = $2,000,000, PV = $900,000, EV = $750,000, AC = $825,000.

```
python3 -c "
BAC, PV, EV, AC = 2000000, 900000, 750000, 825000
CPI = EV/AC
SPI = EV/PV
eac_typical = BAC / CPI
eac_atypical = AC + (BAC - EV)
eac_both = AC + (BAC - EV) / (CPI * SPI)
print(round(CPI,4), round(SPI,4))
print(round(eac_typical,2), round(eac_atypical,2), round(eac_both,2))
"
```
Result: CPI = 0.9091, SPI = 0.8333.

| Method | EAC |
|---|---|
| Typical variance (BAC/CPI) | $2,200,000 |
| Atypical variance (AC + BAC − EV) | $2,075,000 |
| Both CPI and SPI (AC + (BAC−EV)/(CPI×SPI)) | $2,475,000 |

The spread between $2,075,000 and $2,475,000 — a $400,000 difference from
the same underlying data — is exactly why a PM must state which method and
which assumption they're using whenever they quote an EAC. Reporting
"$2.2M" with no method named lets the number quietly become "the number"
without anyone checking whether the underlying assumption (past performance
persists unchanged) still holds. The "both" method is the most conservative
here and the right default when a project is both over budget and behind
schedule, since it assumes neither problem self-corrects.

## TCPI — what the remaining work must achieve

```
python3 -c "
BAC, EV, AC = 2000000, 750000, 825000
tcpi_to_bac = (BAC - EV) / (BAC - AC)
print(round(tcpi_to_bac,4))
"
```
→ TCPI = 1.0638. To still hit the original $2,000,000 budget, every
remaining dollar spent must return $1.0638 of planned value — a CPI 6.38%
*better* than the original plan assumed, on the harder, later part of the
project. Compare this to the current CPI of 0.9091: the team would need to
improve performance by roughly 17% just to hit the original number. This is
the single number that tells a steering committee whether "we'll still hit
budget" is a plan or a hope — a TCPI more than about 5–10% above the
project's demonstrated CPI is a hope.

## Variance thresholds and RAG bands

| Metric | Green | Amber | Red |
|---|---|---|---|
| CPI | ≥ 0.95 | 0.90 – 0.94 | < 0.90 |
| SPI | ≥ 0.95 | 0.90 – 0.94 | < 0.90 |
| TCPI vs. current CPI gap | ≤ 3% harder | 3–10% harder | > 10% harder |

At CPI 0.9091 (Red) and a TCPI-vs-CPI gap of about 17 percentage points
(Red), this project's dashboard entry is unambiguous: it needs the recovery
process from module 08, not a "monitor and continue" note.

## Forecasting with a trend, not a single snapshot

A single period's CPI can be noise. Track it across periods before treating
it as a trend:

| Period | CPI | SPI | Trend interpretation |
|---|---|---|---|
| Month 1 | 0.98 | 0.97 | Normal |
| Month 2 | 0.95 | 0.93 | Slight softening — watch |
| Month 3 | 0.91 | 0.88 | Consistent decline — this is a trend, not noise |
| Month 4 | 0.91 | 0.83 | Confirmed — trigger recovery review |

Three consecutive periods of decline (months 2–4) is the general rule of
thumb for distinguishing a trend from a single bad sprint — one bad month
after five good ones is usually noise; three in a row is a signal.

## Exercise

A project: BAC = $1,200,000, PV = $500,000, EV = $410,000, AC = $470,000.

1. Calculate CPI, SPI, and all three EAC methods, verifying every step with
   `python3 -c`. State which method you'd report to a steering committee
   and why, given this project's specific CPI/SPI combination.
2. Calculate TCPI to BAC, and compare it to the current CPI to say whether
   hitting the original budget is realistic.
3. Assign this project's CPI and SPI a RAG color using the thresholds
   table, and state what additional data (beyond this one snapshot) you'd
   want before recommending a full recovery process.
