# 04 · Crisis & Turnaround Project Leadership

Project recovery (Level 3, module 08) is a process for a project that's
significantly off track but still fundamentally salvageable on a longer
timeline. A crisis is different in kind, not just degree: something has
happened — a major outage, a safety incident, a data breach, a public
commitment publicly missed — and the organisation needs a decision and
visible action within hours, not the multi-week recovery diagnosis process.
This module is about leading in that compressed window.

## Recovery vs. crisis — different clocks

| | Standard recovery (L3, module 08) | Crisis leadership |
|---|---|---|
| Timeframe to first action | Days to weeks | Hours |
| Primary tool | Root cause analysis, rebaseline | Triage, containment, communication |
| Decision style | Consultative, data-driven | Directive, best-available-information |
| Communication cadence | Weekly status | Hourly or continuous until stabilised |
| Success in the moment | A credible recovery plan | Damage contained, trust that someone is in control |

Applying the standard recovery process's pace to an active crisis — commission
a root cause analysis, schedule a steering committee for next week — reads
as abdication of leadership during the hours that matter most, even if the
same analysis is exactly right a week later.

## The first-hour triage framework

| Question | Why it's first | Example answer |
|---|---|---|
| Is this still happening, or has it already happened? | Determines whether you're containing or cleaning up | Data exposure is ongoing — containment first |
| Who needs to know in the next 30 minutes? | Legal/compliance/PR obligations often have real deadlines | Legal (breach notification clock), affected customers' account team |
| What's the single next decision, and who has authority to make it? | Crises stall when nobody knows who can say yes | Take the affected service offline — CTO has authority, on call now |
| What do we say publicly, and when? | Silence reads as either hiding something or not knowing — both erode trust | Holding statement within 2 hours; full statement once facts confirmed |

### Worked example: incident command structure

A payment processing outage affects 40% of transactions during peak hours.
The organisation stands up an incident command structure rather than
routing the decision through the normal project governance chain:

| Role | Who | Responsibility during the incident |
|---|---|---|
| Incident Commander | Senior eng director (not the on-call engineer actually fixing it) | Single point of decision authority; not doing the technical work themselves |
| Technical lead | On-call senior engineer | Diagnoses and directs the fix |
| Communications lead | Comms/PR | Owns all external and internal-wide messaging, single voice |
| Scribe | PMO analyst | Timestamped log of every decision and action — this becomes the post-incident record |

The separation between Incident Commander and Technical lead is the design
detail that fails most often when skipped: the person best placed to fix the
technical problem is rarely also well placed to manage stakeholder
communication, resourcing, and the next decision simultaneously — combining
the roles slows the technical fix and produces worse communication.

## Communication during a crisis

| Principle | What it means in practice |
|---|---|
| Say what you know, what you don't, and when you'll know more | "We've identified the affected systems; we do not yet know the full customer impact; next update in 60 minutes" is honest and buys trust |
| Never guess at scope to sound more in control | An early wrong number, corrected later, damages trust worse than an honest "we're still assessing" |
| One communications lead, one channel of truth | Multiple people answering questions produces contradictory statements, which reads as chaos even if each individual answer is accurate |
| Overcommunicate cadence even with no new information | "No change since the last update, next check-in in 30 minutes" is still valuable — silence during a live crisis is read as bad news |

## After the crisis: the post-incident review

A crisis handled well still needs the root-cause discipline from module 08
— just after stabilisation, not during it.

| Section | Content |
|---|---|
| Timeline | Minute-by-minute reconstruction from the scribe's log |
| What went well | Specific — "the incident commander/technical lead split let the fix and comms proceed in parallel" |
| What went wrong | Specific — "no pre-agreed holding statement template cost 45 minutes before the first public update" |
| Root cause | The underlying failure, not the trigger — a payment outage's root cause is rarely "a server crashed," it's whatever allowed the crash to have no redundancy |
| Action items with owners and dates | Each item traceable to a specific gap surfaced above |

### Worked example: root cause vs. trigger

| Trigger | Surface fix | Root cause | Real fix |
|---|---|---|---|
| Database connection pool exhausted during peak load | Restart the service | No load testing at realistic peak volume before launch | Add load testing to the release gate criteria (Level 3, module 05's stage-gate model) |

Fixing only the trigger (restart, add more connections) guarantees a repeat
under the next load spike; the real fix changes the gate that let an
untested system reach production load in the first place.

## Exercise

Your organisation's customer-facing app goes down completely during a major
marketing campaign's launch hour, driven by a spike in signups the system
wasn't sized for.

1. Design a first-hour triage using the four-question framework — write a
   specific, plausible answer to each question for this scenario.
2. Assign the four incident command roles to plausible people/titles at a
   mid-size company, and explain in one sentence why the Incident Commander
   should not also be the engineer fixing the database.
3. Draft a two-sentence holding statement following the "say what you know,
   what you don't, and when you'll know more" principle.
4. Write the root cause vs. trigger row for this incident (what's the
   surface fix, and what's the actual root cause a post-incident review
   should surface).
