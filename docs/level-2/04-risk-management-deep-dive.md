# 04 · Risk Management Deep Dive

Level 1 introduced the risk register and the probability/impact grid. That is
qualitative risk analysis, and it answers "which risks should we worry about
first?" This module goes further: it covers how to write a risk statement
that is actually actionable, how to calibrate a scoring scale so two people
score the same risk the same way, and — the part most PMs never learn — how
to convert a risk register into a **defensible contingency reserve number**
using expected monetary value and decision trees.

## Writing a risk that can be managed

Most risk registers fail at the first column. "Resourcing" is not a risk; it
is a topic. A usable risk statement has three parts:

> **Cause** → **Uncertain event** → **Effect on an objective**

> *Because* the hardware vendor is a single source with no contractual
> delivery date, *the servers may arrive after the integration window opens*,
> *which would delay go-live and incur data-centre holding costs.*

The test is simple: if you cannot name the objective it threatens (cost,
schedule, scope, quality, benefit), you have not written a risk. Note also
that risks include **opportunities** — uncertain events with positive effect.
A register containing only threats is half a register.

| Category | Prompts to generate risks |
|---|---|
| Technical | Unproven technology, integration complexity, performance limits |
| External | Vendors, regulation, market, weather, geopolitics |
| Organisational | Funding stability, competing priorities, key person dependency |
| Project management | Estimating accuracy, poor requirements, unrealistic baseline |

## The risk register template

This is the working artefact. Columns to the left of the double line are
identification; to the right are analysis and response.

| ID | Risk statement (cause → event → effect) | Category | Owner | P | I | Score | Response | Action | Trigger | Residual |
|---|---|---|---|---|---|---|---|---|---|---|
| R1 | Single-source vendor has no contractual date → servers arrive late → go-live slips | External | Ops Lead | 0.30 | 4 | 1.2 | Mitigate | Add contractual delivery date + penalty; qualify second supplier | Vendor misses design freeze | 0.10 × 4 |
| R2 | Only one architect knows the payments module → they leave → rework and delay | Organisational | PM | 0.20 | 3 | 0.6 | Mitigate | Pair a second engineer; document interfaces by month 3 | Resignation, or 2 weeks leave | 0.10 × 3 |
| R3 | Regulator consulting on new data rules → spec changes mid-build → major rework | External | Sponsor | 0.15 | 5 | 0.75 | Accept (active) | Contingency reserve; monitor consultation | Draft rules published | 0.15 × 5 |
| R4 | Interfaces defined late → integration defects → retest cycles | Technical | Tech Lead | 0.40 | 2 | 0.8 | Mitigate | Contract-first interface design; CI from week 2 | Interface spec late by 1 week | 0.20 × 2 |
| R5 | Vendor offers discount for signing before Q3 → lower licence cost | External | PM | 0.50 | +2 | — | Exploit (opportunity) | Bring the approval gate forward two weeks | Vendor confirms offer | — |

Five columns are the ones people omit and then regret. **Owner** must be a
named person, never a team. **Trigger** is the observable event that says the
risk is materialising — without it, nobody knows when to execute the
response. **Residual** is the risk that remains *after* the response, which
is what you actually carry. And responses must be distinct actions, not
restatements of the risk.

| Response (threats) | Meaning | Response (opportunities) | Meaning |
|---|---|---|---|
| Avoid | Change the plan so the risk cannot occur | Exploit | Change the plan so it certainly occurs |
| Transfer | Move impact to a third party (insurance, fixed-price contract) | Share | Partner with someone better placed to capture it |
| Mitigate | Reduce probability or impact | Enhance | Increase probability or impact |
| Accept | Take it knowingly — with a reserve (active) or not (passive) | Accept | Take the upside if it arrives |

## Calibrating the scales

Qualitative scoring is worthless if "high impact" means different things to
different people. Define the scale **in project-specific units** before the
first workshop.

| Score | Probability | Cost impact | Schedule impact |
|---|---|---|---|
| 1 — Very low | < 10% | < $10k | < 3 days |
| 2 — Low | 10–30% | $10k–50k | 3–10 days |
| 3 — Moderate | 30–50% | $50k–150k | 10–20 days |
| 4 — High | 50–70% | $150k–400k | 20–40 days |
| 5 — Very high | > 70% | > $400k | > 40 days |

Score against the **highest** applicable dimension: a risk that costs $20k
but delays 30 days is a 4, not a 2. And score **impact if it occurs**, never
impact discounted by likelihood — probability is already the other axis, and
discounting twice buries genuinely severe risks.

## Quantitative analysis: expected monetary value

Qualitative scoring ranks risks. It cannot tell you how much contingency to
hold. **Expected monetary value (EMV) = probability × impact in currency**,
which converts the register into money.

| Risk | Probability | Impact ($) | EMV ($) |
|---|---|---|---|
| R1 Vendor hardware delay | 0.30 | −120,000 | **−36,000** |
| R2 Lead architect leaves | 0.20 | −60,000 | **−12,000** |
| R3 Regulatory spec change | 0.15 | −200,000 | **−30,000** |
| R4 Integration rework | 0.40 | −45,000 | **−18,000** |
| R5 Early-signing licence discount | 0.50 | +40,000 | **+20,000** |
| **Net EMV** | | | **−76,000** |

Check R1: 0.30 × (−$120,000) = −$36,000. Threats alone total **−$96,000**;
the single opportunity offsets $20,000 of that, giving a net exposure of
**$76,000**.

That number is the contingency reserve request, and this is the whole reason
to do the arithmetic. "We'd like a 10% contingency" invites a negotiation
down to 5%. "**We need $76,000, and here is the line-by-line derivation**" is
a different conversation — and when a risk closes without occurring, you can
release its EMV back to the sponsor, which builds the credibility to ask
again next time.

Two cautions. EMV is an average across many projects, and **your project runs
once**: the $76,000 reserve does not cover the $200,000 regulatory hit if it
lands. Reserve against the *portfolio* of risks, and escalate any single risk
whose impact exceeds the whole reserve. Second, contingency reserve covers
**identified** risks and sits inside the cost baseline, under the PM's
control. **Management reserve** covers unknown-unknowns, sits outside the
baseline, and needs sponsor approval to access. Never conflate them.

## Decision trees

When a choice must be made under uncertainty, EMV extends to comparing whole
options. The team must decide whether to build a payments module in-house or
buy a vendor product.

| Option | Outcome | Probability | Total cost | Weighted |
|---|---|---|---|---|
| **Build** | Goes well | 0.60 | −$900,000 | −$540,000 |
| | Overruns | 0.40 | −$1,400,000 | −$560,000 |
| | **EMV** | | | **−$1,100,000** |
| **Buy** | Integrates cleanly | 0.80 | −$1,050,000 | −$840,000 |
| | Needs customisation | 0.20 | −$1,250,000 | −$250,000 |
| | **EMV** | | | **−$1,090,000** |

Buy wins — by **$10,000**, which is 0.9% of the decision. The honest
conclusion is not "buy is better"; it is **"on cost, these options are
indistinguishable, so decide on the factors the tree doesn't model."** Buy
has a much narrower spread ($1.05m–$1.25m versus $0.9m–$1.4m), so it is the
lower-variance choice — which matters if a $1.4m outcome would breach the
funding envelope. Build retains in-house capability. Present the tree, then
argue those points explicitly; a decision tree is an input to judgement, not
a replacement for it.

If the tree had come out $300,000 apart, the arithmetic would be decisive.
Knowing the difference between a decisive and an indistinguishable result is
the skill.

!!! warning "A register nobody reviews is documentation, not management"
    The most common failure in risk management is not bad analysis — it is a
    register built during initiation and never opened again. Put a risk
    review on a fixed cadence (weekly for the top 5, monthly for the full
    register), and at every review do three things: re-score existing risks,
    check whether any **triggers** have fired, and add newly identified ones.
    Risk scores are perishable, and a stale register gives false comfort.

## Exercise

Build a full risk analysis for a project of your own.

1. Identify at least 10 risks — including **at least two opportunities** —
   written in strict cause → event → effect form. If you cannot name the
   objective threatened, rewrite the risk.
2. Define your own calibrated probability and impact scales in
   project-specific units, as in the table above.
3. Complete the full register template, including **owner, trigger, response
   type, action and residual score** for every risk. Ensure each response is
   an action, not a restatement.
4. Convert your top 6 risks to currency and compute the **EMV of each and the
   net EMV**. State the contingency reserve you would request and how you
   would justify it to a sponsor who asks you to halve it.
5. Identify one genuine either/or decision on your project, build a decision
   tree with at least two outcomes per branch, and compute the EMV of each
   option. State whether the result is **decisive or indistinguishable**, and
   if indistinguishable, name the non-cost factors you would decide on.
6. State your risk review cadence and who attends.
