# 08 · Project Recovery

A project in trouble doesn't announce it clearly — it shows up as a status
report that's still green two weeks before an obviously missed date, or a
team that's stopped raising risks because raising them hasn't changed
anything. Recovery is a distinct discipline from normal project management:
it starts with an honest diagnosis, often requires re-baselining, and always
requires rebuilding trust with stakeholders who have already been
disappointed once.

## Recognising a project needs recovery, not just correction

| Signal | Normal variance | Recovery territory |
|---|---|---|
| CPI/SPI | 0.90–1.00, recovering | Below 0.80, worsening for 2+ periods |
| Team morale | Normal sprint fatigue | Attrition risk, visible disengagement |
| Stakeholder trust | Occasional pushback | Sponsor has stopped believing status reports |
| Scope | Managed change requests | Scope has silently grown 30%+ with no rebaseline |
| Risk register | Actively used | Abandoned — team has stopped logging because nothing gets actioned |

The abandoned risk register is the most reliable early-warning sign and the
easiest to check in five minutes: pull up the log and see when the last
entry was added. A project with no new risk entries in six weeks isn't
risk-free — it's a project where the team has learned that raising risks
doesn't matter.

## The recovery process

| Phase | Activity | Output |
|---|---|---|
| 1. Stop and assess | Pause new commitments; independent health check (often by PMO or an outside PM) | Honest current-state report |
| 2. Root cause analysis | Why did this happen — not just what's wrong now | Root cause list, distinct from symptoms |
| 3. Rebaseline decision | Can this be recovered on the current baseline, or does scope/schedule/budget need resetting? | Recovery plan with new baseline (if needed) |
| 4. Stakeholder reset | Present the honest picture and the recovery plan together — never the bad news alone | Realigned expectations, renewed (or reduced) sponsorship |
| 5. Execute with tighter controls | Shorter reporting cycles, smaller commitments, visible quick wins | Restored trust, incrementally |
| 6. Exit recovery | Define the criteria that mean the project is "out of recovery" | Return to normal governance cadence |

### Root cause vs. symptom — worked example

| Symptom | Surface explanation | Root cause (after digging) |
|---|---|---|
| Schedule 6 weeks behind | "Development took longer than estimated" | Original estimate was never reviewed by the engineers who'd do the work — it was set to fit a pre-committed launch date |
| Budget 20% over | "Vendor costs ran high" | No change control was enforced on vendor scope for 4 months; change orders were verbally approved and never logged |
| Team morale collapsing | "People are just tired" | Three consecutive re-plans with no explanation given to the team — they've stopped believing plans are real |

Treating the symptom (re-estimate the schedule, cut vendor scope, run a
morale survey) without the root cause guarantees a repeat. The schedule fix
that actually holds is changing *how* estimates get set, not just producing
a new number.

## Worked example: EVM-driven recovery decision

A project is 40% through its planned duration. Status: PV = $400,000, EV =
$280,000, AC = $380,000.

```
python3 -c "
PV, EV, AC, BAC = 400000, 280000, 380000, 1000000
CPI = EV/AC
SPI = EV/PV
EAC = BAC / CPI
VAC = BAC - EAC
print(round(CPI,3), round(SPI,3), round(EAC,2), round(VAC,2))
"
```
Result: CPI = 0.737, SPI = 0.700, EAC ≈ $1,357,143, VAC ≈ −$357,143.

A CPI of 0.737 means every dollar spent has bought 73.7 cents of planned
value — this is deep into recovery territory, not normal variance. The
$357,143 projected overrun, at only 40% complete, is the number that forces
the rebaseline conversation: continuing to report against the original
$1,000,000 budget baseline would mislead every subsequent status report,
because it compares actuals to a target the data already says is
unreachable at current performance.

**Recovery options modeled**:

| Option | Assumption | New EAC | Recommendation |
|---|---|---|---|
| Do nothing | Performance stays at CPI 0.737 | $1,357,143 | Reject — guarantees the overrun |
| Recovery plan A: cut 15% of remaining scope | Remaining work reduced, same efficiency | ~$1,210,571 | Viable if scope is genuinely descopable |
| Recovery plan B: add senior resources to fix root cause (estimating process) | CPI improves to 0.92 on remaining work | ~$1,162,609 | Recommended — addresses root cause, not just symptom |

```
python3 -c "
BAC=1000000; EV=280000; AC=380000
remaining_work = BAC - EV
# Plan A: cut 15% of remaining work
planA_remaining = remaining_work * 0.85
planA_eac = AC + planA_remaining / (EV/AC)
# Plan B: remaining work at improved CPI 0.92
planB_eac = AC + remaining_work / 0.92
print(round(planA_eac,2), round(planB_eac,2))
"
```
→ Plan A ≈ $1,210,571; Plan B ≈ $1,162,609. Both options beat doing nothing
($1,357,143), and Plan B — fixing the root cause of the estimating process
rather than just cutting scope — comes out ahead numerically as well. The
choice between them is still a judgment call on scope-cut risk (Plan A)
versus execution-fix cost and time-to-effect (Plan B), not a foregone
conclusion from the numbers alone.

## Rebuilding stakeholder trust

| Mistake | Why it fails | What works instead |
|---|---|---|
| Presenting only the recovery plan, not the honest current state | Sponsor has usually already sensed something's wrong; hiding the extent reads as more bad faith when it surfaces later | Lead with the number (VAC, delay), then the plan |
| Promising an aggressive recovery timeline to rebuild confidence fast | Missing a second recovery deadline is worse than the original miss | Commit to a conservative recovery date with a visible early milestone |
| Reverting to long reporting cycles once "things feel better" | Trust was lost through opacity; restoring it needs sustained visibility, not a return to normal | Keep tightened (e.g., weekly) reporting until 2–3 consecutive periods hit plan |

## Exercise

A project shows PV = $600,000, EV = $390,000, AC = $520,000, BAC =
$1,500,000 at the 40% mark.

1. Calculate CPI, SPI, EAC, and VAC, verifying with `python3 -c`. State
   whether this qualifies as recovery territory using the thresholds in
   this module's first table.
2. Write one symptom → surface explanation → root cause chain (like the
   worked example) for a plausible cause of this specific CPI/SPI
   combination.
3. Model two recovery options (a scope cut and a performance-improvement
   plan) with `python3 -c`, and recommend one with a one-paragraph
   justification.
