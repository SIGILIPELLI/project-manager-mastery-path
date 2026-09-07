# 06 · Risk Management Basics

A **risk** is an uncertain event or condition that, if it occurs, has an
effect — positive or negative — on at least one project objective (scope,
schedule, cost, or quality). Most of the working vocabulary treats "risk" as
synonymous with "threat," but the formal definition includes **opportunities**
too (a positive risk — e.g., "a new library ships early and could cut our
development time") even though threats dominate day-to-day attention. Risk
management is not about eliminating uncertainty — that's impossible on any
project worth doing — it's about identifying it early, deciding deliberately
what to do about each risk, and tracking it so nothing important is
forgotten. This module covers the foundational tools: identification, the
probability/impact grid, and the RAID log. A deeper, more quantitative
treatment (qualitative and quantitative risk analysis) is in Level 2.

## Identifying risks

Risk identification works best as a structured, repeatable exercise rather
than a one-time brainstorm at kickoff — new risks surface throughout a
project's life as more becomes known. Common techniques:

| Technique | How it works |
|---|---|
| Brainstorming | Team session listing anything that could go wrong (or right) |
| Checklist review | Compare against a standing list of risks common to this type of project |
| Assumption analysis | Examine every assumption from the scope statement — if it's wrong, what happens? |
| Expert judgment | Ask people who've run similar projects what bit them |
| SWOT analysis | Strengths/Weaknesses/Opportunities/Threats, viewed from the project's angle |

A well-written risk statement follows a simple structure: **"Because of
[cause], [risk event] may occur, which would lead to [effect]."** For
example: "Because the vendor has never integrated with our specific payment
processor before, the integration may take longer than estimated, which
would lead to a schedule slip on the launch date." This structure forces
you past a vague worry ("the vendor integration is risky") into something
specific enough to actually plan around.

## Assessing risks: the probability/impact grid

Once risks are identified, they need to be prioritized — not every risk
deserves the same attention. The standard tool is a **probability/impact
grid**, plotting how likely a risk is against how severe its effect would be:

| | Low Impact | Medium Impact | High Impact |
|---|---|---|---|
| **High Probability** | Medium priority | High priority | Critical priority |
| **Medium Probability** | Low priority | Medium priority | High priority |
| **Low Probability** | Low priority | Low priority | Medium priority |

Placing each identified risk into this grid does two things: it tells you
where to spend your limited planning time (Critical and High-priority
risks need an active response plan; Low-priority risks may just need to be
watched), and it gives you a defensible, repeatable way to explain to a
sponsor why one risk is being actively managed and another is being
accepted without action.

## The four response strategies

For each risk that warrants active management, there are four standard
response strategies (the same four apply to opportunities, framed
positively — see the note below):

| Strategy | What it means | Example |
|---|---|---|
| Avoid | Change the plan to eliminate the risk entirely | Choose a vendor with a proven integration instead of an unproven one |
| Mitigate | Reduce the probability or impact | Run an early technical spike with the vendor to surface integration problems before they're on the critical path |
| Transfer | Shift the risk (or its financial consequence) to a third party | Buy insurance, or write a fixed-price contract that puts overrun risk on the vendor |
| Accept | Acknowledge the risk and do nothing proactive (usually reserved for low-priority risks) | Note it in the log and revisit if it starts to materialize |

!!! info "The same four strategies apply to opportunities"
    For positive risks, the mirror strategies are **Exploit** (make it
    happen), **Enhance** (increase the probability/impact), **Share**
    (partner with a third party to help it happen), and **Accept**
    (welcome it if it comes, but don't chase it).

## The RAID log

A **RAID log** is the single running document that ties risk management
into the rest of project execution — it stands for **R**isks,
**A**ssumptions, **I**ssues, and **D**ependencies, tracked together because
they're closely related: an unmanaged assumption often *becomes* a risk, and
an unmanaged risk that materializes *becomes* an issue.

| Type | Definition | Example entry |
|---|---|---|
| Risk | Something that *might* happen | "Vendor integration may take longer than estimated" |
| Assumption | Something being taken as true without proof | "Assuming the vendor's sandbox environment is available for testing by week 2" |
| Issue | Something that *has already* happened and needs resolving now | "Vendor's sandbox environment is not yet available — blocking integration testing" |
| Dependency | Something the project relies on from outside its own control | "Legal sign-off on the vendor contract, owned by the Legal team" |

Reviewing the RAID log on a fixed cadence (weekly, on most projects) is what
keeps risk management from becoming a one-time kickoff exercise that gathers
dust — the log should visibly change every review, with new entries added,
statuses updated, and closed items moved to a resolved section rather than
deleted (deleted history is lost learning).

## A worked example: a risk that was identified but not actively managed, and what happened

A construction project's risk register flags, in week 1: "Because the site
has known soil-stability issues from a prior geological survey, foundation
work may require additional engineering, which would lead to a schedule
delay." Probability is assessed as Medium, impact as High — landing in the
**High-priority** cell of the grid. The response strategy chosen is
**Mitigate**: commission an updated geotechnical survey before foundation
work begins, at a cost of $8,000, specifically to reduce the probability of
discovering the issue mid-excavation (which would be far more expensive to
address once equipment is already mobilized).

Contrast this with a second, hypothetical version of the same project where
the same risk was identified but assigned "Accept" by default, because no
one wanted to spend the $8,000 up front. Three weeks into excavation, the
soil issue does materialize — it has now become an **Issue** in the RAID
log, not a risk — and remediation costs $45,000 and adds three weeks to the
schedule, because it's being solved reactively with equipment already
mobilized and idle, rather than proactively with a clean survey result in
hand. The $8,000 mitigation, in the real version of this project, was cheap
insurance against a downside that was over five times as expensive to
absorb after the fact — which is the general pattern that makes proactive
risk management worth the up-front time it costs.

## How It Actually Works

A probability/impact matrix isn't just a visual sorting tool — the risk
score it produces, `Score = Probability × Impact`, is a simplified **Expected
Monetary Value (EMV)** calculation, the same math used quantitatively in
Level 2. If probability and impact are each scored 1–5, a risk rated
(4, 4) = 16 "should" outrank one rated (5, 2) = 10 on the heat map, but that
ordinal multiplication silently distorts real dollar risk: a 20% chance of a
$500,000 loss (EMV = $100,000) can rate lower on a 1–5 heat map than an 80%
chance of a $50,000 loss (EMV = $40,000) if the ordinal buckets are drawn
carelessly, even though the first is 2.5× worse in real expected-dollar terms.
This is exactly why qualitative scoring is a **triage** step, not a final
answer — it exists to cheaply rank dozens of risks so you know which handful
deserve the more expensive quantitative EMV or Monte Carlo treatment (Level
2 Module 4, Level 3 Module 3). The RAID log's four categories map to four
different control actions with different mechanics: Risks are managed by
changing probability or impact *before* they occur, Issues (materialized
risks) are managed by containment and recovery cost *after* the fact, which
is why an issue's true cost is always closer to its full impact than its
pre-event EMV — the probability term has collapsed to 1.

## Exercise

For the project you've been building through this level's exercises,
identify five risks using the "because of [cause], [risk event] may occur,
which would lead to [effect]" structure. Place each on the probability/
impact grid and note its priority level. For the two highest-priority
risks, write which of the four response strategies (avoid/mitigate/
transfer/accept) you'd choose and why. Then start a RAID log with at least
one entry in each of the four categories (risk, assumption, issue,
dependency) for your project.
