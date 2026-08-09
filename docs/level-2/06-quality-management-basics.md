# 06 · Quality Management Basics

Quality is the most commonly misunderstood knowledge area in project
management, because the everyday meaning of the word ("excellent") is not the
project meaning. **Quality is conformance to requirements — the degree to
which the deliverable does what it was specified to do.** A cheap plastic pen
that writes reliably is high quality and low grade. A luxury pen that leaks
is low quality and high grade. Low grade is a legitimate business decision;
low quality is always a defect.

This module covers the three quality processes, the cost of quality model
that justifies prevention spending, and the analytical tools — Pareto,
fishbone, control charts — that turn a complaint into a root cause.

## Three processes, three different questions

| Process | Question it answers | Focus | Typical output |
|---|---|---|---|
| **Plan Quality** | What does "good" mean here, and how will we know? | Standards and metrics | Quality management plan, checklists |
| **Manage Quality** (assurance) | Is our **process** capable of producing good work? | Process audit | Process improvements, audit findings |
| **Control Quality** (control) | Is this specific **deliverable** acceptable? | Inspecting outputs | Verified deliverables, defect log |

The distinction people get wrong is assurance versus control. **Assurance
looks at the process; control looks at the product.** Finding a defect in
testing is control. Asking why the process let that defect reach testing is
assurance. Projects that only do control fix the same class of defect
repeatedly, forever, because nothing ever changes upstream.

## The quality metrics template

Vague standards ("the system must be fast") are unenforceable. Every quality
requirement needs a metric, a target, a measurement method and an owner.

| Requirement | Metric | Target | Measured by | Frequency | Owner |
|---|---|---|---|---|---|
| System is responsive | 95th-percentile page load | ≤ 2.0 s | Load test suite | Each release | Tech Lead |
| Data migrates accurately | Records failing reconciliation | 0 critical, ≤ 0.1% minor | Automated reconciliation report | Each migration run | Data Lead |
| Code is maintainable | Unit test line coverage | ≥ 80% | CI pipeline | Every commit | Tech Lead |
| Users can complete core task | Task completion rate, unassisted | ≥ 90% | Usability test, n=12 | Pre-UAT | UX Lead |
| Release is stable | Severity 1 defects in production | 0 in first 30 days | Incident log | Monthly | Ops Lead |
| Documentation is usable | Runbook steps failing dry-run | 0 | Ops dry-run rehearsal | Pre go-live | Ops Lead |

Two properties make this table work. Every target is a **number someone can
check** — "responsive" became "95th percentile ≤ 2.0 s". And every row has a
named owner, because a metric nobody owns is not measured.

## Cost of quality

Cost of quality (COQ) is the total cost of both achieving quality and failing
to. It splits four ways, and the split is the argument for prevention.

| Category | Type | Items | Cost |
|---|---|---|---|
| **Prevention** | Conformance | Training $45k, standards definition $20k, design reviews $35k | **$100,000** |
| **Appraisal** | Conformance | Test automation $60k, inspections and audits $25k, QA execution $80k | **$165,000** |
| **Internal failure** | Non-conformance | Rework before release $110k, retesting $40k | **$150,000** |
| **External failure** | Non-conformance | Production defect fixes $260k, support escalations $90k, SLA credits $75k | **$425,000** |
| **Cost of conformance** | | Prevention + appraisal | **$265,000** |
| **Cost of non-conformance** | | Internal + external failure | **$575,000** |
| **Total COQ** | | | **$840,000** |

Read the shape, not just the total. Non-conformance is **$575,000 — 68% of
all quality spending** — and external failure alone is $425,000, more than
prevention and appraisal combined. This is the classic signature of a project
that inspects quality in at the end instead of building it in.

The governing rule is the **cost of a defect multiplies with the stage it
escapes to**: a requirements defect caught in review costs a conversation;
caught in testing it costs rework and a retest cycle; caught in production it
costs an incident, a hotfix, a regression test, a customer apology, and
possibly an SLA credit. Roughly an order of magnitude at each hop.

So the business case writes itself: **if $50,000 more prevention spending
eliminates a third of external failure, that is $141,667 saved for $50,000
spent.** This table is how you win the argument for design reviews and test
automation when a sponsor asks why QA costs so much — you show that QA is not
the expensive part. Failure is.

## Analysing defects: Pareto

When defects arrive, the instinct is to fix them in the order reported. A
**Pareto chart** orders them by frequency instead, exposing the vital few.
450 defects logged during system testing:

| Defect category | Count | % of total | Cumulative % |
|---|---|---|---|
| Data validation errors | 187 | 41.6% | 41.6% |
| Session timeout / auth | 94 | 20.9% | **62.4%** |
| Report formatting | 61 | 13.6% | **76.0%** |
| Slow page load | 38 | 8.4% | 84.4% |
| Import mapping | 27 | 6.0% | 90.4% |
| UI label / copy | 19 | 4.2% | 94.7% |
| Export encoding | 12 | 2.7% | 97.3% |
| Miscellaneous | 12 | 2.7% | 100.0% |

Check: 187 ÷ 450 = 41.6%; cumulative through the third row =
(187 + 94 + 61) ÷ 450 = 342 ÷ 450 = **76.0%**.

**Three categories out of eight account for 76% of all defects.** Fixing the
root cause of data validation errors alone removes more defects than the
bottom five categories combined. That is where the team goes first — not
because those defects are individually worse, but because the leverage is
there.

## Analysing causes: fishbone and the five whys

Pareto tells you *what* to attack. Root cause analysis tells you *why*. A
fishbone (Ishikawa) diagram organises candidate causes by category:

| Category | Candidate causes for "data validation errors" |
|---|---|
| **People** | Developers unfamiliar with the domain rules |
| **Process** | No shared validation spec; rules written per screen |
| **Technology** | Validation implemented separately in UI and API |
| **Materials/Data** | Source data dictionary incomplete and out of date |
| **Environment** | Test data does not resemble production edge cases |
| **Measurement** | No automated check that UI and API rules agree |

Then drive one branch down with the **five whys**:

1. Why do validation defects occur? Because UI and API reject different data.
2. Why do they differ? Because each was implemented from a separate reading
   of the requirements.
3. Why separate readings? Because there is no single machine-readable
   validation specification.
4. Why not? Because the data dictionary was never completed after the source
   system changed.
5. Why not? Because no one owns the data dictionary.

**Root cause: unowned data dictionary.** The fix is an owner and a
single-source validation spec — not 187 individual defect tickets. Note that
the answer at level 5 is an *organisational* cause, which is typical; stopping
at level 2 would have produced "developers should be more careful", which
fixes nothing.

## Control charts

Control charts distinguish **common cause** variation (normal noise in a
stable process) from **special cause** variation (something actually changed).
Defects found per build over ten builds:

`12, 15, 11, 14, 13, 16, 12, 14, 13, 15`

```
Mean (centre line) = 135 ÷ 10           = 13.5
Standard deviation                       = 1.5
UCL = mean + 3σ = 13.5 + 4.5           = 18.0
LCL = mean − 3σ = 13.5 − 4.5           =  9.0
```

Every point falls between 9.0 and 18.0, so this process is **in control** at
13.5 defects per build. That is an uncomfortable but valuable conclusion: the
process is *stably bad*. Reacting to the 16 as though it were a problem —
and to the 11 as though it were an improvement — is **tampering**, and
tampering with a stable process reliably makes it worse.

To reduce defects here you must change the process itself, not respond to
individual points. But if build 11 produced 24 defects, that is outside the
UCL, a special cause, and worth investigating immediately. Two further
signals matter even inside the limits: **seven consecutive points on one side
of the mean**, or a steady trend of seven, indicates a shift even when no
point breaches a limit — the **rule of seven**.

!!! warning "Gold plating is a quality failure, not a bonus"
    Adding unrequested features or polish beyond the specification is not
    high quality — it is uncontrolled scope. It consumes budget, adds
    untested code paths and defect surface, and delivers value nobody asked
    for or will maintain. Conformance to requirements means meeting them, not
    exceeding them. If the extra is genuinely valuable, raise it as a change
    request (module 07) and let it be assessed like anything else.

## Exercise

Build a quality management plan for a project of your own.

1. Write a quality metrics table with at least six requirements. Every row
   needs a **numeric target**, a measurement method, a frequency and a named
   owner. Rewrite any subjective requirement until it is checkable.
2. State one deliverable and write its **acceptance criteria** as a checklist
   a reviewer could tick without asking you a question.
3. Build a cost of quality table with realistic figures in all four
   categories. Compute the cost of conformance, cost of non-conformance and
   total COQ, and state the percentage that is non-conformance. Then make the
   business case: propose a specific prevention investment and estimate the
   failure cost it avoids.
4. Invent a realistic defect distribution across at least seven categories.
   Build the **Pareto table** with percentage and cumulative percentage
   columns, and identify the vital few driving roughly 80% of defects.
5. Take your top category, build a **fishbone** with at least four categories
   of candidate cause, then run the **five whys** on the most likely branch
   until you reach an organisational root cause. State the fix.
6. Invent 10 periods of a quality measure. Compute the mean, σ, UCL and LCL,
   state whether the process is in control, and say what you would do
   differently if it is in control but performing badly.
