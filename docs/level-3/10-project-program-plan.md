# 10 · Project — Program Plan for 3 Related Projects

This is the Level 3 capstone project: build a full program plan for three
related projects, applying every module in this level — benefits mapping,
dependency sequencing, quantified risk, vendor terms, PMO-style rollup
reporting, and EVM-based forecasting — as one worked deliverable rather than
ten separate exercises.

## The scenario

A mid-size retailer is launching a loyalty program. It requires three
related projects:

1. **Loyalty platform build** — the core points/rewards engine (internal
   team, 12 weeks, 8 engineers).
2. **POS integration** — connecting in-store checkout systems to the
   loyalty platform (a vendor contract, fixed-price, 8 weeks).
3. **Marketing launch campaign** — customer acquisition and app onboarding
   (internal team, 6 weeks, 4 people, cannot start until the platform is
   feature-complete).

## Step 1 — Benefits map

| Benefit | Target | Owner | Contributing projects |
|---|---|---|---|
| Increase repeat purchase rate | +8 percentage points within 2 quarters of launch | VP Marketing | Loyalty platform, Marketing launch |
| Reduce checkout friction for enrolled members | Under 5 extra seconds at POS | Head of Retail Ops | POS integration |
| Grow email-marketable customer base | +50,000 opted-in customers | VP Marketing | Marketing launch |

## Step 2 — Dependency map and sequencing

| From | To | Dependency | Type | Slack |
|---|---|---|---|---|
| Loyalty platform build | POS integration | Points API must be live for integration testing | Finish-to-start (partial — API portion only) | 1 week |
| Loyalty platform build | Marketing launch | Platform must be feature-complete before campaign can promise real rewards | Finish-to-start | 0 weeks (critical) |
| POS integration | Marketing launch | In-store enrollment must work before in-store campaign push | Finish-to-start | 2 weeks |

Sequencing across a 12-engineer combined internal capacity cap (8 platform +
4 marketing, POS integration is vendor-staffed and doesn't compete for
internal capacity):

| Weeks | Active work |
|---|---|
| 1–10 | Loyalty platform build (8 engineers) |
| 9–16 | POS integration (vendor team, starts once points API is live at week 9, per the 1-week-slack dependency) |
| 11–16 | Marketing launch prep (4 people) — starts once platform is feature-complete (week 11, one week after week-10 completion accounts for a short buffer), runs in parallel with the tail of POS integration since campaign prep doesn't need POS finished, only the platform |
| 17–22 | Marketing launch execution — starts after POS integration completes (week 16) plus 1 week transition, respecting the 2-week-slack dependency |

## Step 3 — Quantified risk register (program level)

| ID | Risk | Probability | Impact | EMV | Response |
|---|---|---|---|---|---|
| R1 | POS vendor's fixed-price estimate was based on incomplete store hardware inventory | 35% | $90,000 (change order) | $31,500 | Mitigate: complete hardware audit before contract signature |
| R2 | Points API design changes after POS integration has started | 20% | $60,000 (vendor rework under change order) | $12,000 | Mitigate: freeze API contract before POS kickoff |
| R3 | Marketing launch date is publicly announced before platform completion is confirmed | 15% | $150,000 (reputational + forced discount to cover a broken promise) | $22,500 | Avoid: no public date until platform hits UAT sign-off |

```
python3 -c "print(0.35*90000, 0.20*60000, 0.15*150000, 0.35*90000+0.20*60000+0.15*150000)"
```
→ $31,500 + $12,000 + $22,500 = **$66,000 total program contingency
reserve**.

## Step 4 — Vendor contract terms (POS integration)

| Term | Value |
|---|---|
| Contract type | Fixed-price |
| Price | $310,000 |
| Milestone payments | 30% on kickoff, 40% on integration test pass, 30% on go-live sign-off |
| SLA | 99.5% uptime for POS-to-platform connection post go-live |
| Penalty clause | 1% of contract value per week late, capped at 10% |
| Exit clause | 30-day data transition assistance if terminated for cause |

Fixed-price is the right call here specifically because R1's mitigation (a
completed hardware audit before signature) removes the main source of scope
ambiguity that would otherwise make fixed-price risky for the vendor to
price accurately — and therefore risky for the buyer to receive change
orders against.

## Step 5 — Program-level EVM tracking (mid-point checkpoint, week 11)

At week 11, combined program figures: BAC = $850,000 (all three projects'
budgets summed), PV = $520,000, EV = $460,000, AC = $505,000.

```
python3 -c "
BAC, PV, EV, AC = 850000, 520000, 460000, 505000
CPI = EV/AC
SPI = EV/PV
EAC_both = AC + (BAC - EV) / (CPI * SPI)
VAC = BAC - EAC_both
print(round(CPI,4), round(SPI,4), round(EAC_both,2), round(VAC,2))
"
```
Result: CPI = 0.9109, SPI = 0.8846, EAC (both) ≈ $988,998, VAC ≈ −$138,998.

Both indices sit in Red/Amber-border territory (module 09's thresholds): a
projected $138,998 overrun on an $850,000 program at only the midpoint is
enough to trigger a program-level review, not just a note in the status
report — consistent with the recovery-readiness signals from module 08.

## Step 6 — Program status rollup (PMO-style dashboard)

| Project | CPI | SPI | RAG | Note |
|---|---|---|---|---|
| Loyalty platform build | 0.93 | 0.90 | Amber | Slight schedule slip, being monitored |
| POS integration | 0.88 | 0.85 | Red | Vendor flagged hardware audit findings adding scope — R1 materialising |
| Marketing launch | Not started | Not started | Green (on plan, not yet due) | — |

R1 (probability 35%, EMV $31,500) is the risk that appears to be
materialising here — the vendor's hardware audit findings driving POS
integration's Red status. The program manager's next action is drawing down
the $66,000 reserve for the actual change-order cost once quantified, and
re-forecasting the program EAC with the updated POS project numbers.

## Stretch goals

- Extend the risk register with a fourth risk that spans two of the three
  projects (a genuine program-level risk, not one that belongs to a single
  project's own register) and calculate its EMV.
- Rebuild the week-11 EVM rollup assuming POS integration's change order
  actually costs $45,000 more than R1's estimated impact — recompute
  program EAC and VAC with `python3 -c` and state the new reserve balance.
- Draft the stage-gate criteria (module 05) this program would need to pass
  at a G3 mid-point gate, using the actual week-11 numbers above to decide
  whether it would pass or be sent back for a recovery plan.
