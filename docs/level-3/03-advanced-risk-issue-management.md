# 03 · Advanced Risk & Issue Management

Basic risk management identifies risks and rates them high/medium/low.
Advanced risk management **quantifies** them, so that a $2M reserve request
is backed by arithmetic instead of a gut feeling, and so that ten
medium-severity risks with correlated causes don't quietly hide the fact
that they're one severe risk wearing ten disguises.

## Qualitative vs. quantitative risk analysis

| | Qualitative | Quantitative |
|---|---|---|
| Output | Probability × Impact score, heat map | Expected monetary value, contingency reserve |
| Use | Fast triage of a long list | Justifying reserve, comparing response options in dollars |
| Effort | Low | Higher — needs estimates or simulation |
| When | Every risk, every review | Top-tier risks, or whole-project reserve sizing |

## Expected monetary value (EMV)

EMV = Probability × Impact (in dollars). It lets you compare risks that
differ in both likelihood and size on one scale, and it's the standard input
to a contingency reserve calculation.

### Worked example: risk register with EMV

| ID | Risk | Probability | Impact if it occurs | EMV | Response |
|---|---|---|---|---|---|
| R1 | Key vendor misses integration deadline | 30% | $150,000 (schedule + rework) | $45,000 | Mitigate: dual-source a fallback API |
| R2 | Critical senior engineer resigns mid-project | 15% | $200,000 (ramp-up + delay) | $30,000 | Mitigate: cross-train a backup now |
| R3 | Regulatory requirement changes scope | 10% | $400,000 (rework + legal) | $40,000 | Accept + monitor: too costly to hedge in advance |
| R4 | Cloud cost estimate is understated | 40% | $60,000 | $24,000 | Accept: within normal budget variance |
| R5 | Two vendors (R1's fallback included) share the same upstream sub-processor | 20% | $500,000 (both fail together) | $100,000 | Transfer: contract penalty clause + insurance |

Verified: `0.30*150000=45000`, `0.15*200000=30000`, `0.10*400000=40000`,
`0.40*60000=24000`, `0.20*500000=100000`.

**Total EMV = $45,000 + $30,000 + $40,000 + $24,000 + $100,000 = $239,000.**
This sum is your recommended contingency reserve — the amount that, averaged
over many projects facing this same risk profile, covers the expected cost
of the risks that materialise. It is not a guarantee any single project
needs exactly $239,000; it's the actuarially sound number to hold.

R5 is the entry that catches people who skip the "is this really
independent?" check: it exists because R1's mitigation (a fallback vendor)
turned out to share a sub-processor with the original vendor, so the two
"different" vendor risks are correlated — if the sub-processor fails, both
vendors fail together. That correlation is why R5's impact ($500,000) is
larger than R1 or its fallback alone: it's the combined-failure scenario.
Discovering this kind of hidden correlation is exactly what advanced risk
analysis is for; a simple heat map, treating R1 and its fallback as two
independent low risks, would have missed it entirely.

## Decision tree analysis

When a risk response is itself a decision with a cost and a probability of
success, a decision tree makes the expected value of each path explicit.

**Scenario**: R1 (vendor misses deadline, 30% probability, $150,000 impact).
Two response options:

- **Option A — do nothing**: EMV = 0.30 × $150,000 = $45,000 expected cost.
- **Option B — pay $20,000 now for a fallback API integration** that reduces
  the probability of the deadline miss mattering to 5% (fallback absorbs
  most scenarios) but doesn't eliminate it (5% chance both vendor and
  fallback are late):
  Cost = $20,000 (certain) + 0.05 × $150,000 (residual expected impact)
  = $20,000 + $7,500 = **$27,500 expected total cost.**

```
python3 -c "print(0.30*150000, 20000 + 0.05*150000)"
→ 45000.0  27500.0
```

Option B is cheaper in expectation ($27,500 vs $45,000) even though it
requires spending real money up front — this is the calculation that turns
"should we invest in mitigation" from a debate into arithmetic.

## Issue escalation and the risk-to-issue transition

A risk that materialises becomes an **issue** — it has stopped being a
possibility and started being a fact that needs resolving now, not a
probability to plan around. The register entry doesn't disappear; it
transitions.

| Field | As a risk | As an issue (after triggering) |
|---|---|---|
| Status | Open, monitored | Active, being resolved |
| Probability | 30% | N/A — it happened |
| Impact | Estimated $150,000 | Actual cost being tracked |
| Owner | Risk owner | Issue owner (may be same or reassigned to whoever fixes it) |
| Response | Planned mitigation | Corrective action in progress |
| Reserve | Drawn from at trigger | Reserve now reduced by the drawdown |

### Issue log

| ID | Issue | Trigger date | Root risk | Actual cost so far | Status | Owner |
|---|---|---|---|---|---|---|
| I-09 | Vendor missed integration deadline by 3 weeks | 14 May | R1 | $52,000 | Active — fallback API being finalised | PM |
| I-10 | Cloud spend 45% over estimate in month 2 | 02 Jun | R4 | $27,000 | Resolved — auto-scaling rules added | Eng lead |

I-09's actual cost ($52,000) running above R1's estimated impact ($150,000
was the ceiling, not a fixed number) is normal — the estimate was a range
input to EMV, not a prediction of the exact number. What matters is drawing
down the $239,000 reserve by the actual cost as issues resolve, so the
remaining reserve stays honest.

## Reserve burn-down tracking

| Period | Reserve remaining | Drawn this period | Reason |
|---|---|---|---|
| Start | $239,000 | — | — |
| Month 2 | $187,000 | $52,000 | I-09 (vendor delay) |
| Month 3 | $160,000 | $27,000 | I-10 (cloud overrun) |

A reserve burning down faster than the project's percent-complete is an
early warning independent of EVM — it means realised risk is outpacing plan
even if cost and schedule variance still look fine.

## Exercise

A project has three risks: (1) 25% probability, $80,000 impact; (2) 50%
probability, $30,000 impact; (3) 10% probability, $300,000 impact, and risk
3 shares a root cause with risk 1 (both depend on the same third-party data
feed going down).

1. Calculate EMV for each risk and the total recommended reserve, verified
   with `python3 -c`.
2. Explain, in your own words, why the shared root cause between risk 1 and
   risk 3 means the simple sum of their EMVs may understate the actual
   combined exposure, and propose one way to represent that in the register.
3. For risk 3, propose a mitigation costing $15,000 up front that would
   drop its probability to 3%. Compute whether that mitigation is worth it
   in expected-value terms.
