# 05 · Procurement Basics

Most projects buy something — contractors, software licences, hardware,
professional services. The moment money crosses an organisational boundary,
the project manager's informal authority disappears and is replaced by a
contract. This module covers the contract types and what each one does to
**risk allocation**, how to run a defensible vendor selection, and the
arithmetic of incentive contracts that catches out PMs who sign a
fixed-price-incentive deal without knowing where its ceiling bites.

## The procurement lifecycle

| Phase | Key activity | Output |
|---|---|---|
| Plan | Make-or-buy analysis, choose contract type | Procurement management plan |
| Conduct | Issue solicitation, evaluate, negotiate, award | Signed contract, SOW |
| Control | Manage performance, changes, payments, disputes | Performance reports, change orders |
| Close | Verify deliverables, settle claims, release retention | Closure certificate, lessons learned |

The three solicitation documents are not interchangeable, and using the wrong
one wastes weeks:

| Document | Use when | You are asking for |
|---|---|---|
| **RFI** — Request for Information | You don't yet know what the market offers | Capability information, no commitment |
| **RFQ** — Request for Quotation | The requirement is fully specified and standard | A price |
| **RFP** — Request for Proposal | You know the problem, not the solution | A proposed approach *and* a price |

If you issue an RFQ for something you cannot fully specify, you will receive
cheap quotes against a specification that turns out to be wrong, then pay for
every gap through change orders. Issue an RFP.

## Contract types and where the risk sits

This is the central table of the module. The contract type is a **risk
allocation decision**, not a payment mechanism.

| Type | Buyer pays | Cost-overrun risk | Use when |
|---|---|---|---|
| **FFP** — Firm Fixed Price | A fixed sum | **Seller** | Scope is precisely defined and stable |
| **FPIF** — Fixed Price Incentive Fee | Cost + fee, sharing over/underrun, capped by a ceiling | **Shared**, then seller above ceiling | Scope defined, but you want a cost incentive |
| **FP-EPA** — Fixed Price with Economic Price Adjustment | Fixed, indexed to inflation/FX | Shared on macro factors | Multi-year deals with commodity or FX exposure |
| **CPFF** — Cost Plus Fixed Fee | All allowable costs + a fixed fee | **Buyer** | R&D; scope genuinely unknown at signature |
| **CPIF** — Cost Plus Incentive Fee | Costs + fee that varies with performance | **Buyer**, partly shared | Unknown scope, but cost control matters |
| **CPAF** — Cost Plus Award Fee | Costs + subjective award fee | **Buyer** | Long services deals judged on quality |
| **T&M** — Time and Materials | Agreed rates × hours + materials | **Buyer** | Staff augmentation, small or urgent work |

Three practical rules follow from this table.

**A fixed price does not remove risk; it converts it into price and
adversarial behaviour.** The seller prices in a contingency you cannot see,
and the moment your requirement moves, every clarification becomes a change
order with a margin attached. FFP is right when scope is genuinely stable —
and expensive when it is not.

**Cost-plus contracts require you to audit.** You are paying actual costs, so
"allowable cost" must be defined in the contract and someone on your side
must check invoices. A CPFF contract with no cost verification is an open
cheque book.

**T&M must always be capped.** Include a not-to-exceed value and a review
point, or it becomes cost-plus with no fee ceiling. T&M is for small or
urgent work; if it runs longer than a quarter, convert it.

## Worked example: where an FPIF contract actually bites

You award an FPIF contract on these terms:

| Parameter | Value |
|---|---|
| Target cost | $800,000 |
| Target fee | $90,000 |
| Target price | $890,000 |
| Ceiling price | $1,000,000 |
| Share ratio (buyer / seller) | 80 / 20 |

The share ratio means that for every dollar of overrun, the **buyer** absorbs
80 cents and the **seller** 20 cents — until the ceiling, above which the
seller absorbs everything. The seller's fee is:

```
Fee   = Target fee + (Target cost − Actual cost) × seller share
Price = Actual cost + Fee
```

| Actual cost | Fee calculation | Fee | Final price |
|---|---|---|---|
| $750,000 | 90,000 + (800,000−750,000) × 0.20 | $100,000 | **$850,000** |
| $800,000 | 90,000 + 0 | $90,000 | **$890,000** |
| $850,000 | 90,000 + (800,000−850,000) × 0.20 | $80,000 | **$930,000** |
| $937,500 | 90,000 + (800,000−937,500) × 0.20 | $62,500 | **$1,000,000** |
| $980,000 | 90,000 + (800,000−980,000) × 0.20 | $54,000 | ~~$1,034,000~~ **$1,000,000** |

The number that matters is the **Point of Total Assumption (PTA)** — the
actual cost above which the seller absorbs 100% of every further dollar:

```
PTA = ((Ceiling price − Target price) / buyer share) + Target cost
    = ((1,000,000 − 890,000) / 0.80) + 800,000
    = 137,500 + 800,000
    = $937,500
```

The fourth row confirms it: at an actual cost of exactly $937,500 the final
price hits the $1,000,000 ceiling precisely. At $980,000 the formula would
give $1,034,000, but the ceiling holds the buyer at $1,000,000 — the seller
eats the $34,000.

**Why you must know your PTA.** Below it, the seller loses only 20 cents per
dollar of overrun, so cost discipline is weak. Above it, the seller loses a
full dollar per dollar — and a seller heading past PTA on a large contract is
a seller who may cut quality, staff the job down, dispute scope aggressively,
or in the worst case walk away. **PTA is not just a pricing number; it is an
early-warning threshold.** Track the seller's actual costs against it and
treat approaching PTA as a risk trigger with a named response, exactly as in
module 04.

## Vendor selection: weighted scoring

Awarding on price alone is how projects acquire cheap vendors who cannot
deliver. Publish the criteria and weights **before** you open the responses.

| Criterion | Weight | Vendor A | Vendor B | Vendor C |
|---|---|---|---|---|
| Technical approach | 0.30 | 9 → 2.70 | 7 → 2.10 | 8 → 2.40 |
| Relevant experience | 0.20 | 8 → 1.60 | 6 → 1.20 | 9 → 1.80 |
| Price | 0.25 | 6 → 1.50 | 9 → 2.25 | 7 → 1.75 |
| Delivery timeline | 0.15 | 7 → 1.05 | 8 → 1.20 | 6 → 0.90 |
| Support model | 0.10 | 8 → 0.80 | 7 → 0.70 | 9 → 0.90 |
| **Weighted total** | **1.00** | **7.65** | **7.45** | **7.75** |

Check Vendor C: (0.30×8) + (0.20×9) + (0.25×7) + (0.15×6) + (0.10×9) =
2.40 + 1.80 + 1.75 + 0.90 + 0.90 = **7.75**.

**Vendor C wins, and Vendor B — the cheapest — comes last.** B scored a 9 on
price, the single highest score anywhere in the table, and still lost because
price carries only a quarter of the weight while its technical approach and
experience were weakest. That is the model working as designed.

Two disciplines make this defensible rather than decorative. Set the weights
before seeing the bids, or you will unconsciously tune them toward a
preferred vendor. And note the spread: 7.75 versus 7.65 is 1.3% — too close
to call on the scores alone. When the top two are within a few percent, say
so, and break the tie with a reference call, a paid proof-of-concept, or a
risk assessment. Also apply **screening criteria** (mandatory pass/fail:
insurance, certifications, financial stability) *before* scoring, so an
unqualified bidder cannot score its way in.

!!! warning "The contract is the scope baseline once it is signed"
    Anything not in the statement of work is a change order, priced by the
    seller when they have no competition left. Before signature, walk the SOW
    against your WBS line by line and confirm every deliverable, acceptance
    criterion, and interface is named. An hour spent here is worth more than
    any amount of contract management afterwards.

## Exercise

Plan a real procurement for a project of your own.

1. Write a make-or-buy analysis for one significant component, with at least
   three factors on each side and a stated recommendation.
2. Choose a contract type from the table and **justify it by naming who
   carries the cost-overrun risk and why that is the right allocation here.**
   State what would have to change for you to choose differently.
3. Draft the solicitation: state whether it is an RFI, RFQ or RFP and why,
   and write a statement of work with at least five deliverables, each with a
   testable acceptance criterion.
4. Build a weighted scoring matrix with at least five criteria, weights
   summing to 1.00, and three hypothetical vendors. Compute every weighted
   score and the totals. State the winner, and whether the margin is
   decisive or too close to call.
5. Set up an FPIF deal of your own with a target cost, target fee, ceiling
   and share ratio. **Compute the PTA**, then compute the final price at
   three actual-cost levels — one below target, one between target and PTA,
   and one above PTA. Confirm your PTA is right by checking that the price at
   that cost equals the ceiling exactly.
6. Name the one contract clause you would most want in place before signing,
   and what it protects you from.
