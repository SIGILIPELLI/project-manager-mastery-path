# 07 · Stakeholder Management Basics

A **stakeholder** is anyone who can affect, or be affected by, the project —
a far broader group than just "the people on the project team." Sponsors,
end users, regulators, adjacent teams whose work depends on yours, even a
vocal critic with no formal authority who can shape opinion against the
project — all are stakeholders. Stakeholder management is the discipline of
identifying who these people are, understanding what they need and how much
influence they hold, and engaging each of them at the right level — because
a technically excellent project can still fail if the people who needed to
be on board weren't.

## Identifying stakeholders

Stakeholder identification works best as a structured pass across several
categories, since it's easy to default to only the obvious names (the
sponsor, the immediate team) and miss quieter but still-critical
stakeholders:

| Category | Examples |
|---|---|
| Internal, direct | Sponsor, project team, functional managers who supply resources |
| Internal, indirect | Adjacent teams affected by the outcome, compliance/legal/finance reviewers |
| External | Customers, end users, vendors, contractors |
| External, less obvious | Regulators, industry groups, the media, a community group affected by a physical project |

A useful habit: for every deliverable in the WBS ([Module 3](03-scope-management-basics.md)),
ask "who has to approve this, who has to use it, and who could block it?" —
this reliably surfaces stakeholders that a purely org-chart-based list
misses.

## Prioritizing stakeholders: the power/interest grid

Not every stakeholder needs the same level of engagement — treating a
low-power, low-interest stakeholder with the same intensive management as a
high-power sponsor wastes effort that's needed elsewhere. The standard
prioritization tool is the **power/interest grid**:

| | Low Interest | High Interest |
|---|---|---|
| **High Power** | Keep satisfied — enough info to stay comfortable, but don't overload them | Manage closely — your most important stakeholders; engage frequently and in depth |
| **Low Power** | Monitor — minimal effort, watch for changes | Keep informed — regular updates, but they don't need decision-making involvement |

Placing every identified stakeholder into one of these four quadrants turns
"we should talk to people about this project" into a concrete plan: the
sponsor and a key regulatory body (high power, high interest) get a
recurring one-on-one; a mildly interested adjacent team (low power, high
interest) gets added to the regular status email distribution; a stakeholder
with high formal authority but low day-to-day interest — say, a VP who
signed off once and moved on — gets a brief, well-timed update rather than
being flooded with details they didn't ask for. (Level 3, Module 7 extends
this into a RACI chart and deeper power-mapping for larger, multi-stakeholder
programs.)

## Building a stakeholder register

The working artifact that ties identification and prioritization together
is the **stakeholder register** — a living document, not a one-time list:

| Stakeholder | Role/interest | Power | Interest | Engagement approach |
|---|---|---|---|---|
| VP of Sales (sponsor) | Funds the project, needs it to boost Q3 numbers | High | High | Weekly 1:1, escalate any risk to the Q3 deadline immediately |
| Legal/Compliance | Must approve the customer data handling | High | Low | Brief them at two fixed checkpoints; don't loop them into daily details |
| Customer Support team | Will field tickets once this launches | Low | High | Include in bi-weekly demo, gather their input on edge cases |
| End users (surveyed sample) | Will use the resulting tool daily | Low | High | Usability test at the prototype stage, not just at launch |
| IT Security | Approves architecture before go-live | High | Medium | Involve early in design review, not as a late gate |

Note how the "engagement approach" column differs meaningfully by quadrant
— it's not just a contact list, it's a plan for *how much and how often*
each stakeholder needs to hear from the project, tuned to their actual
power and interest rather than a one-size-fits-all update cadence.

## A worked example: a stakeholder missed at kickoff, and the cost of catching it late

A hospital IT project rolls out a new patient scheduling system. The
stakeholder register at kickoff lists the Chief Medical Officer (sponsor),
the scheduling department, and IT security — all correctly identified as
high power/high interest or high power stakeholders, and all engaged
closely from day one. What's missing: the **billing department**, whose
existing workflows depend on data fields the scheduling system currently
plans to restructure.

Because billing wasn't in the original stakeholder register, they weren't
consulted during design. Two weeks before go-live, a billing manager —
attending a demo out of general curiosity, not because they were on any
distribution list — realizes the new system doesn't carry over a field
their team relies on for insurance claims. This surfaces as a late,
high-urgency scramble: a design change close to launch, under time
pressure, is far more expensive and risky than the same conversation would
have been in week 2 of a 12-week project. Re-running the stakeholder
identification pass with the "who has to use this, who could block it"
question against the billing-related deliverable, at kickoff, would have
caught this stakeholder before the register was ever finalized — which is
exactly why identification deserves a deliberate, structured pass rather
than relying on whoever happens to be in the kickoff meeting.

## Exercise

For the project you've been building through this level's exercises, list
at least six stakeholders, making sure to include at least one from each
category in the identification table above (internal direct, internal
indirect, external, external/less-obvious). Place each on the power/
interest grid, and build a stakeholder register with a specific engagement
approach for each — not a generic "keep them updated," but a concrete
statement of frequency and format (e.g., "bi-weekly 15-minute demo,"
"single email at project kickoff and at go-live").
