# 05 · Executive Reporting & Governance

A status report written for a project team and one written for a steering
committee are different documents, not the same document with fewer words.
Executives need a decision-ready summary — what's the ask, what's the risk,
what happens if we do nothing — while a team status report is appropriately
full of the operational detail an executive should never have to wade
through to find the one number that matters.

## The exception report principle

The single biggest failure mode in executive reporting is symmetry: giving
every project equal space regardless of whether it needs executive
attention. An exception report inverts this — silence (or a single line) for
projects on track, detail only for projects that need a decision.

| Project | Status | Executive attention needed? |
|---|---|---|
| Platform migration | Green, on track | No — one line: "On track, no action needed" |
| Vendor integration | Amber, vendor SLA breach | **Yes** — needs a decision on whether to invoke the penalty clause |
| Mobile relaunch | Green, ahead of schedule | No — one line |
| Compliance update | Red, blocked on legal sign-off | **Yes** — needs an escalation to unblock legal |

A one-page executive report from this portfolio devotes maybe 80% of its
space to the two Amber/Red items and a single line each to the two Green
ones — the opposite of a report that spends equal space on all four out of
a sense of fairness to each PM.

## The executive summary structure that works

| Section | Length | Content |
|---|---|---|
| Headline | 1 sentence | The single most important fact this period |
| Ask | 1–2 sentences | What decision or action is needed from this audience, specifically |
| Evidence | 2–4 bullets, quantified | The numbers that support the ask (CPI/SPI, cost, date) |
| Options (if a decision is needed) | 2–3 rows | What the executive is actually choosing between |
| What happens if no decision is made | 1 sentence | The cost of inaction, stated plainly |

### Worked example: an executive ask, built from the structure

> **Headline**: The vendor integration project will miss its go-live date by
> 5 weeks unless we act this week.
>
> **Ask**: Approve invoking the contract's penalty clause and reallocating
> $40,000 to bring in a second integration team.
>
> **Evidence**: CPI 0.82, SPI 0.79 (Red per standard thresholds); vendor has
> confirmed the delay is due to understaffing on their side, not scope
> ambiguity on ours; penalty clause entitles us to 1% of contract value per
> week late.
>
> **Options**:

| Option | Cost | Effect |
|---|---|---|
| Do nothing, absorb the delay | $0 now | 5-week slip, no penalty recovered |
| Invoke penalty clause only | $0 (recovers ~$15,500, per contract terms) | Recovers cost, doesn't fix the delay |
| Invoke penalty + fund a second team | $40,000 | Recovers cost partially, cuts delay to ~2 weeks |

> **If no decision is made this week**: the vendor's current staffing plan
> means the 5-week delay becomes locked in past the point a second team
> could still help.

This is what makes a report "decision-ready": an executive can read it in
90 seconds and know exactly what's being asked of them, compared to a
narrative status update they'd have to interpret into a decision themselves.

## Governance cadence by audience

| Audience | Cadence | Format | Focus |
|---|---|---|---|
| Project team | Daily/weekly | Detailed status, backlog, blockers | Operational |
| Program steering committee | Bi-weekly/monthly | Program rollup, cross-project dependencies | Tactical decisions |
| Executive committee | Monthly/quarterly | Exception report, portfolio health | Strategic decisions, capital allocation |
| Board | Quarterly | Portfolio-level trends only, major risks | Oversight, not operational decisions |

Reporting the same level of detail up every layer of this table is a common
governance failure — a board does not need CPI/SPI numbers for individual
projects, and giving it to them either buries the actual strategic question
or invites the board into operational decisions that aren't theirs to make.

## Governance escalation thresholds

| Trigger | Escalates to | Response time expected |
|---|---|---|
| CPI or SPI below 0.85 for 2+ consecutive periods | Steering committee | Within the next scheduled cycle |
| Projected budget overrun > 15% of total project budget | Executive committee | Within 1 week |
| Any safety, legal, or regulatory exposure | Executive committee + legal, immediately | Same day |
| Sponsor disengagement (module 07, Level 3 pattern) | PMO Director | Within 2 weeks |

Publishing these thresholds in advance — rather than deciding case by case
whether something is "bad enough" to escalate — is what protects a PM from
the two symmetric failure modes: escalating too much (noise, executives
stop reading) and escalating too little (a real problem reaches the board
only when it's already a crisis, per module 04).

## Exercise

You manage the monthly executive rollup for a portfolio of 5 projects: 3
are Green, 1 is Amber (schedule slip, no cost impact, self-correcting per
the PM), and 1 is Red (CPI 0.79, needs a $200,000 reserve draw to avoid a
scope cut).

1. Draft the one-page structure (headline/ask/evidence/options/cost-of-
   inaction) for the Red project only, inventing plausible specific numbers
   consistent with CPI 0.79.
2. Write the one-line treatment each of the 3 Green projects and the 1
   Amber project would get in an exception report, and justify why the
   Amber project doesn't need the full five-part structure.
3. Using the escalation thresholds table, state which two thresholds (if
   any) this Red project has already crossed, and to which audience it
   should be escalated.
