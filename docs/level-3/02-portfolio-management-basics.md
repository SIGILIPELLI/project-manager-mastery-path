# 02 · Portfolio Management Basics

A portfolio is the full set of projects and programs an organisation is
funding at once — often unrelated to each other, competing for the same
pool of money and people. Portfolio management answers one question the
project or program level cannot: **given limited capacity, which of these
should we be doing at all?** Get this wrong and your best project managers
deliver flawless projects that nobody should have funded.

## Portfolio vs. program vs. project (recap)

| | Project | Program | Portfolio |
|---|---|---|---|
| Question answered | How do we deliver this? | How do these related things add up to a benefit? | Which things should we fund? |
| Scope | Fixed | Related set | Organisation-wide, may be unrelated |
| Owner | Project manager | Program manager | Portfolio manager / PMO / executive committee |

## A scoring model for prioritisation

Comparing a compliance project to a growth project to a cost-cutting project
on "which is more important" is a values argument dressed up as analysis
unless you have a shared scoring model. A simple weighted model:

| Criterion | Weight | What it measures |
|---|---|---|
| Strategic alignment | 30% | Does this map to a named strategic objective this year? |
| Financial value (NPV/ROI band) | 25% | Expected return relative to cost |
| Risk (inverted — lower risk scores higher) | 15% | Likelihood of failure or major overrun |
| Urgency / cost of delay | 15% | What happens if we wait a year? |
| Resource feasibility | 15% | Can we actually staff it without gutting something else? |

Each criterion is scored 1–5 by a review board, weighted, and summed to a
100-point scale.

### Worked example: scoring four candidate projects

| Project | Alignment (30%) | Value (25%) | Risk (15%, inverted) | Urgency (15%) | Feasibility (15%) |
|---|---|---|---|---|---|
| A: Core platform migration | 5 | 3 | 2 | 3 | 3 |
| B: New mobile app | 3 | 5 | 3 | 4 | 4 |
| C: Regulatory compliance update | 5 | 2 | 5 | 5 | 5 |
| D: Internal tooling refresh | 2 | 3 | 4 | 2 | 5 |

Weighted score = Σ(criterion score × weight) × 20 (to put on a 100 scale
since raw scores are out of 5):

```
A = (5*0.30 + 3*0.25 + 2*0.15 + 3*0.15 + 3*0.15) * 20
B = (3*0.30 + 5*0.25 + 3*0.15 + 4*0.15 + 4*0.15) * 20
C = (5*0.30 + 2*0.25 + 5*0.15 + 5*0.15 + 5*0.15) * 20
D = (2*0.30 + 3*0.25 + 4*0.15 + 2*0.15 + 5*0.15) * 20
```

Verified with `python3`:

| Project | Weighted score |
|---|---|
| A | 69.0 |
| B | 76.0 |
| C | 85.0 |
| D | 60.0 |

C (compliance) clearly outranks the others despite lower financial value,
because its risk, urgency, and feasibility scores are high — this is the
model correctly capturing that a compliance deadline with heavy
non-compliance penalties outranks a nice-to-have growth bet, even though a
value-only ranking would have put B first.

## The balance: not just the top-N by score

Ranking alone produces a portfolio that's all one type of bet. A mature
portfolio review balances the ranked list against a target mix:

| Category | Target % of budget | Current % | Gap |
|---|---|---|---|
| Run-the-business (keep-the-lights-on) | 40% | 55% | Over by 15pts |
| Grow-the-business (new revenue) | 35% | 20% | Under by 15pts |
| Transform-the-business (strategic bets) | 25% | 25% | On target |

A portfolio 55% run-the-business is starving growth even if every
individual score is defensible — the review board's job is to notice the mix
problem the scoring model alone won't surface, and deliberately fund a
lower-scoring growth project over a higher-scoring maintenance one to correct
the balance.

## Capacity-constrained selection

With a ranked list and a fixed budget, selection is a constrained
optimisation, not just "fund the top of the list until money runs out" —
that greedy approach can leave large amounts unspent or lock out a
high-value project that needs a big-but-not-huge slice.

| Project | Score | Cost ($k) | Score per $k |
|---|---|---|---|
| C | 85.0 | 300 | 0.283 |
| B | 76.0 | 900 | 0.084 |
| A | 69.0 | 600 | 0.115 |
| D | 60.0 | 150 | 0.400 |

With a $1,000k budget: funding by raw score (C, B) uses $1,200k — over
budget, so B is dropped, leaving $700k unspent capacity idle. Funding by
score-per-dollar instead (D, C, A) uses $1,050k — still slightly over. The
actual decision a review board makes: fund D + C + A minus a $50k trim on
A's scope, capturing three initiatives instead of two, and getting more
total strategic value per dollar than chasing the single highest-scoring
project.

## Portfolio dashboard

| Project | Score | Status | Budget used | Schedule | Risk trend |
|---|---|---|---|---|---|
| A | 69.0 | Active | 40% | On track | Stable |
| C | 85.0 | Active | 15% | On track | Improving |
| D | 60.0 | Active | 60% | 2 weeks late | Stable |
| B | 76.0 | Deferred to next cycle | — | — | — |

## Exercise

Score two new candidate projects using the weighted model above (alignment
30%, value 25%, risk 15% inverted, urgency 15%, feasibility 15%): Project E
(alignment 4, value 4, risk 3, urgency 2, feasibility 4) and Project F
(alignment 2, value 5, risk 1, urgency 5, feasibility 2).

1. Compute each weighted score on the 100-point scale and verify your
   arithmetic with `python3 -c`.
2. Given a portfolio already spending 55% on run-the-business against a 40%
   target, argue for or against funding whichever of E/F scores higher,
   using the category-mix table as part of your reasoning, not just the
   score.
3. List one thing the scoring model in this module cannot tell you that a
   human review board still has to judge.
