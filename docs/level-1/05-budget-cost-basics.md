# 05 · Budget & Cost Basics

A schedule tells you *when* work happens; a budget tells you *what it costs*
to make it happen. Cost management is the discipline of estimating,
budgeting, and controlling costs so the project finishes within the approved
funding — and, just as importantly, of being able to say with confidence,
partway through, whether you're actually on track to do so. This module
covers estimating techniques, building a cost baseline, and the concept of
contingency reserve; a deeper, quantitative technique for tracking cost
performance mid-project (Earned Value Management) is covered in Level 2.

## Estimating techniques

Not all estimates are made the same way, and knowing which technique you're
using — and how reliable it is — matters as much as the number itself.

| Technique | How it works | Accuracy | When to use it |
|---|---|---|---|
| Analogous estimating | Base the estimate on a similar past project's actual cost | Low (±25-75%) | Early on, when little detail is known yet |
| Parametric estimating | Use a rate × quantity formula (e.g., $150/hour × estimated hours) | Medium | Once you know quantities but not full detail |
| Bottom-up estimating | Estimate every work package individually, then sum them | High (±5-10%) | Once the WBS ([Module 3](03-scope-management-basics.md)) is detailed |
| Three-point estimating | Combine optimistic, most-likely, and pessimistic estimates | Medium-high | When there's real uncertainty on a given task |

**Three-point estimating** deserves a closer look because it's the most
common way experienced PMs handle uncertainty honestly, rather than picking
one number and hoping. The standard formula (a simplified PERT weighting) is:

```
Expected estimate = (Optimistic + 4 × Most Likely + Pessimistic) / 6
```

For example, a task estimated at Optimistic = 4 days, Most Likely = 6 days,
Pessimistic = 14 days gives:

```
(4 + 4×6 + 14) / 6 = (4 + 24 + 14) / 6 = 42 / 6 = 7 days
```

Note the expected estimate (7 days) leans toward the most-likely case but is
pulled upward by the wide pessimistic tail — which is realistic, since
things that go wrong tend to go more wrong than things that go right go
right.

## Building the cost baseline

The **cost baseline** is the approved, time-phased budget used to measure
and monitor actual spend against — it's the cost equivalent of the schedule
baseline from Module 4. Building one typically works bottom-up from the WBS:

| WBS item | Estimate |
|---|---|
| Design | $18,000 |
| Development | $42,000 |
| Content | $9,000 |
| Testing & Launch | $11,000 |
| **Subtotal** | **$80,000** |
| Contingency reserve (15%) | $12,000 |
| **Total project budget** | **$92,000** |

The subtotal is the sum of every work package's bottom-up estimate; the
**contingency reserve** is added on top to cover *known* risks that might
materialize — it's calculated, not guessed, and is typically informed
directly by the risk register (Module 6). A separate, usually smaller
**management reserve** is sometimes held by the sponsor/organization above
this, to cover *unknown* risks — the PM doesn't control it directly and
needs sponsor approval to draw on it.

## Fixed vs. variable costs, and direct vs. indirect costs

Two useful cost distinctions that affect how you build and defend a budget:

| Distinction | Category A | Category B |
|---|---|---|
| Fixed vs. Variable | Fixed — doesn't change with project scale (e.g., a one-time software license) | Variable — scales with project size (e.g., contractor hours) |
| Direct vs. Indirect | Direct — attributable to this project specifically (e.g., a dedicated developer's salary for the project's duration) | Indirect — shared overhead allocated across projects (e.g., a portion of the office's utility bill) |

Understanding which of your line items are variable matters directly for
change control: if scope grows (Module 3), variable costs grow with it —
which is exactly the leverage a PM uses in a change-request conversation
("adding this feature adds roughly 80 developer-hours, which at our
contractor rate is $12,000 — do we want to add that to the budget, or trade
it against something else?").

## A worked example: contingency reserve sized from the risk register, not a gut feeling

A software project has a bottom-up subtotal of $200,000. Rather than
tacking on a generic "10% for safety," the PM sizes contingency directly
from three identified risks (a technique that connects directly to
[Module 6](06-risk-management-basics.md)):

| Risk | Estimated cost impact if it happens | Probability | Expected value |
|---|---|---|---|
| Third-party API integration takes longer than estimated | $15,000 | 40% | $6,000 |
| Key contractor becomes unavailable mid-project | $20,000 | 20% | $4,000 |
| Security review requires rework | $10,000 | 30% | $3,000 |
| **Total contingency reserve** | | | **$13,000** |

The resulting budget — $200,000 subtotal + $13,000 contingency = $213,000 —
is defensible in a sponsor conversation in a way a flat "add 10%" isn't: if
the sponsor asks "why $13,000 and not $20,000," the PM can point to the
specific risks and their expected costs, and can also explain that this
reserve is meant to be *spent down* as risks resolve (if the API
integration finishes on time, that $6,000 portion is released, not kept as
slush).

## Exercise

For the project you scoped in Module 3's exercise, build a bottom-up cost
estimate: assign a rough dollar cost to each deliverable from your WBS (make
reasonable assumptions about rates if this is hypothetical), sum them to a
subtotal, then identify two or three specific risks that could increase
cost and size a contingency reserve using an expected-value calculation
like the one above (impact × probability, summed). State your final total
project budget and be ready to explain, in one sentence per risk, why each
contingency line is the size it is.
