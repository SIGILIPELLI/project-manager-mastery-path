# 04 · Vendor & Contract Management

Most projects past a certain size depend on at least one external vendor,
and a vendor relationship managed only at signature time — contract filed
away, checked again at renewal — is how a "trusted partner" quietly becomes
your single largest source of schedule risk. This module covers selecting a
vendor, choosing a contract type that puts risk where it belongs, and
running the relationship actively while the contract is live.

## Contract types and where the risk sits

| Contract type | How payment works | Risk sits with | Best for |
|---|---|---|---|
| Fixed-price (FP) | One agreed total for defined scope | Vendor (they eat cost overruns) | Well-defined, stable scope |
| Time & materials (T&M) | Pay for hours + materials actually used | Buyer (you eat overruns) | Uncertain or evolving scope |
| Cost-plus-fixed-fee (CPFF) | Costs reimbursed + fixed fee | Buyer, with vendor's margin protected | R&D, scope genuinely unknown upfront |
| Fixed-price-incentive-fee (FPIF) | Fixed price + bonus/penalty vs. a target | Shared, weighted by the incentive formula | Well-defined scope where performance matters |

The choice is a risk-transfer decision, not a cost-minimisation one — a
fixed-price contract on a poorly-defined scope doesn't eliminate the risk of
that ambiguity, it just guarantees the vendor prices it in as a large
contingency margin, or worse, floods you with change orders once the "fixed"
price scope turns out to have been ambiguous.

## Worked example: FPIF payout calculation

A vendor contract for a data-migration project has:

- Target cost: $400,000
- Target fee: $50,000
- Price ceiling: $500,000
- Share ratio: 70/30 (buyer/vendor) for cost under or over target

The vendor completes the work for an actual cost of $360,000 (came in
**under** target by $40,000).

```
python3 -c "
target_cost, target_fee, ceiling = 400000, 50000, 500000
actual_cost = 360000
savings = target_cost - actual_cost
vendor_share = savings * 0.30
final_fee = target_fee + vendor_share
final_price = actual_cost + final_fee
print(savings, vendor_share, final_fee, final_price)
"
```

Result: savings = $40,000; vendor's 30% share of savings = $12,000; final
fee = $50,000 + $12,000 = $62,000; **final price = $360,000 + $62,000 =
$422,000** — below the $500,000 ceiling, so it's paid in full. The vendor
earned $12,000 more than their base fee specifically because they came in
under target, which is the incentive structure doing its job: it rewards
efficiency without the buyer having to police it line by line.

If the vendor had instead overrun to $450,000 (an overrun of $50,000), the
buyer would absorb 70% of that overrun in a reduced fee: fee reduction =
$50,000 × 0.70 = $35,000, final fee = $50,000 − $35,000 = $15,000, final
price = $450,000 + $15,000 = $465,000 — still under the $500,000 ceiling, so
the buyer pays the full $465,000. Only overruns that push the calculated
price past the ceiling get capped at the ceiling, at which point the vendor
absorbs everything beyond it.

## Vendor scorecard

Run this quarterly for any vendor above a materiality threshold — it turns
"the vendor relationship feels fine" into a tracked, comparable number.

| Criterion | Weight | This quarter | Last quarter |
|---|---|---|---|
| On-time delivery | 25% | 4/5 | 3/5 |
| Quality (defect rate, rework) | 25% | 3/5 | 4/5 |
| Cost control (change order frequency/size) | 20% | 4/5 | 4/5 |
| Responsiveness / communication | 15% | 5/5 | 3/5 |
| Compliance (security, contractual terms) | 15% | 5/5 | 5/5 |

Weighted score this quarter:

```
python3 -c "print((4*0.25+3*0.25+4*0.20+5*0.15+5*0.15)*20)"
```
→ **81.0** (out of 100), up from a comparable last-quarter calculation of
**75.0** (`(3*0.25+4*0.25+4*0.20+3*0.15+5*0.15)*20`). The trend, not just
the absolute score, is what drives the renewal conversation — a vendor
improving from 75 to 81 gets a different conversation than one flat at 81
for four straight quarters (complacency) or one that dropped from 90 to 81
(early warning).

## The vendor selection process (RFP to award)

| Stage | Activity | Output |
|---|---|---|
| 1. Define requirements | Scope, acceptance criteria, SLAs | Statement of Work (SOW) draft |
| 2. Issue RFP | Send to shortlisted vendors, set Q&A window | RFP document, vendor questions log |
| 3. Evaluate proposals | Score against weighted criteria (cost, capability, references, risk) | Evaluation matrix |
| 4. Negotiate | Terms, SLAs, penalty/incentive clauses, exit terms | Negotiated draft contract |
| 5. Award | Legal review, signature | Executed contract |
| 6. Onboard | Kickoff, access provisioning, integrate into project plan | Vendor added to RAID log and schedule |

### Evaluation matrix example

| Vendor | Cost (30%) | Technical fit (30%) | References (20%) | Risk profile (20%) |
|---|---|---|---|---|
| Vendor X | 5 | 3 | 4 | 4 |
| Vendor Y | 3 | 5 | 5 | 3 |
| Vendor Z | 4 | 4 | 3 | 5 |

```
python3 -c "
X=(5*0.30+3*0.30+4*0.20+4*0.20)*20
Y=(3*0.30+5*0.30+5*0.20+3*0.20)*20
Z=(4*0.30+4*0.30+3*0.20+5*0.20)*20
print(X,Y,Z)
"
```
→ X = 80.0, Y = 80.0, Z = 80.0 — a three-way tie, despite each vendor
having a visibly different profile (X is cheap but a weaker technical fit;
Y is the strongest technically but priciest; Z is balanced with the best
risk profile). This is the model correctly showing that all three are
defensible choices at these weights, and that the real decision comes down
to which criterion the buying organisation trusts least to reverse itself —
here, risk profile, which favors Z, since technical fit can often be
improved with support hours but a poor risk profile is harder to fix
mid-contract.

## Managing the contract while it's live

- **SLA tracking**: log every SLA breach with date, impact, and whether a
  penalty clause applies — don't wait for renewal to reconstruct history.
- **Change order log**: every scope change to a vendor contract needs the
  same cost/schedule impact assessment as an internal change request (see
  Level 2, module 07), plus a contractual amendment.
- **Exit/transition clause**: know, in writing, what happens if you
  terminate — data return timelines, transition assistance obligations,
  early-termination fees. Read this clause *before* you need it, not during
  a dispute.

## Exercise

A fixed-price-incentive-fee contract has target cost $250,000, target fee
$40,000, ceiling $320,000, share ratio 60/40 (buyer/vendor). The vendor
finishes at an actual cost of $280,000 (a $30,000 overrun).

1. Calculate the fee reduction, final fee, and final price, verifying with
   `python3 -c`. State whether the ceiling caps the final price.
2. Build a vendor scorecard for a hypothetical vendor with your own 5
   criteria and weights (must sum to 100%), score them 1–5 on each, and
   compute the weighted total.
3. Name one contract type from the table that you would refuse to sign for
   a project whose scope is still actively changing, and explain the
   specific risk it would expose you to.
