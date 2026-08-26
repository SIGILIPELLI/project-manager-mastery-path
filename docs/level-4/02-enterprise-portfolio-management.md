# 02 · Enterprise Portfolio Management

Level 3's portfolio module scored and selected a handful of candidate
projects against a budget. At enterprise scale — dozens of portfolios,
hundreds of initiatives, multiple business units each with their own
priorities — the hard problem shifts from "how do we score projects" to
"how do we allocate capital and capacity across portfolios that don't trust
each other's scoring, and don't want to."

## The enterprise portfolio hierarchy

| Level | Scope | Owner | Decision made |
|---|---|---|---|
| Enterprise portfolio | All investment across the company | Executive committee / CFO | How much capital goes to each business unit's portfolio |
| Business unit portfolio | One BU's initiatives | BU portfolio board | Which of the BU's own candidate projects get funded |
| Program | Related projects within a BU | Program manager | Sequencing and cross-project trade-offs |
| Project | Single deliverable | Project manager | Execution |

The failure mode unique to this scale: a BU's internally-consistent scoring
model (module 02, Level 3) ranks its own projects fairly relative to each
other, but scores from two different BUs are **not comparable** unless
someone normalises them — a BU that scores generously to protect its own
budget will always outrank a BU that scores conservatively, independent of
actual value.

## Normalising cross-BU scores

| BU | Self-reported top project score | BU's average project score (all projects) | Normalised score (top project relative to own baseline) |
|---|---|---|---|
| Retail Ops | 88 | 71 | 88 − 71 = **17** above own average |
| Digital | 92 | 85 | 92 − 85 = **7** above own average |
| Supply Chain | 75 | 58 | 75 − 58 = **17** above own average |

Comparing raw scores (92 > 88 > 75) would rank Digital's top project first.
Comparing each project against its *own* BU's baseline reveals Retail Ops
and Supply Chain's top projects are actually standout bets relative to what
those BUs normally propose, while Digital's "92" is only middling by
Digital's own generous standards. This relative-ranking technique is the
standard fix for cross-BU scoring inflation, and it's the calculation an
enterprise PMO runs before capital allocation, not the raw scores BUs submit.

## Capital allocation models

| Model | How it works | Best for |
|---|---|---|
| Zero-based | Every BU re-justifies its full ask from $0 each cycle | Rapidly changing strategy, willingness to disrupt |
| Incremental | Prior year's allocation ± a negotiated delta | Stable, mature portfolios |
| Strategic buckets | Fixed % to pre-defined themes (e.g., 40% growth, 35% run, 25% transform) regardless of BU | Enforcing a strategic mix top-down (Level 3, module 02's mix table, at enterprise scale) |
| Venture-style staged funding | Small initial tranche; more released only after a project clears defined milestones | High-uncertainty bets (new markets, unproven tech) |

### Worked example: staged funding decision

A digital transformation initiative requests $4,000,000 upfront. The
portfolio board instead approves **staged funding**:

| Stage | Funding released | Milestone required to unlock next stage |
|---|---|---|
| Stage 1 | $600,000 | Proof-of-concept validated with 2 pilot customers |
| Stage 2 | $1,400,000 | Pilot shows ≥15% efficiency gain, technical architecture approved |
| Stage 3 | $2,000,000 | Stage 2 milestone hit on time and within 10% of stage budget |

```
python3 -c "print(600000+1400000+2000000)"
```
→ $4,000,000 total, matching the original ask — but the enterprise never
has more than $600,000 at risk until the concept is proven, and can redirect
the remaining $3,400,000 to another initiative at any stage gate if the
milestone isn't met. This is the mechanism that lets an enterprise portfolio
take on genuinely uncertain bets without betting the full amount on day one.

## Enterprise risk aggregation

A risk rated "medium" independently in five different BU portfolios can be
a severe enterprise risk if it shares a root cause across all five — the
same pattern as Level 3 module 03's correlated-risk example, at portfolio
scale.

| Risk | BUs affected | Independent BU rating | Aggregated enterprise rating |
|---|---|---|---|
| Single cloud provider outage | Retail Ops, Digital, Supply Chain, Finance | Medium (each BU has "some" mitigation) | **Severe** — an outage would hit all four simultaneously |
| Key regulatory change (data residency) | Digital, Supply Chain | Medium | High — same root cause, correlated timing |
| Senior engineering talent shortage | All five BUs | Low individually | Medium-High in aggregate — they're all competing for the same limited talent pool |

An enterprise PMO's distinct value here is exactly this aggregation step:
no single BU portfolio board can see that its "medium" cloud-outage risk is
one of four identical bets on the same infrastructure.

## Exercise

Three business units report their top project scores: BU X scores its top
project 80 (BU average 68), BU Y scores its top project 95 (BU average 90),
BU Z scores its top project 72 (BU average 50).

1. Normalise each BU's top project score against its own baseline and rank
   the three. State which BU's raw score is most inflated relative to its
   own typical proposals.
2. Design a 3-stage staged-funding plan for a $2,500,000 initiative,
   specifying the dollar amount and the milestone required at each stage,
   verifying the stages sum to $2,500,000 with `python3 -c`.
3. Propose one risk that could plausibly be rated "low" or "medium" in each
   of three separate BU portfolios but should be aggregated to "high" or
   "severe" at the enterprise level — explain the shared root cause.
