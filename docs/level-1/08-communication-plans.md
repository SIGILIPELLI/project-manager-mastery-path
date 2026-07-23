# 08 · Communication Plans

Identifying stakeholders and understanding their power and interest
([Module 7](07-stakeholder-management-basics.md)) only pays off if it's
turned into a concrete plan for *what* gets communicated to *whom*, *how
often*, and *in what format*. Studies of project failure consistently point
to poor communication — not technical failure — as one of the most common
root causes: the work was fine, but the right people didn't know the right
things at the right time. A **communication plan** is the artifact that
makes communication deliberate rather than ad hoc.

## The elements of a communication plan

A communication plan answers five questions for every recurring
communication on the project:

| Element | Question it answers |
|---|---|
| Audience | Who receives this communication? |
| Content | What information does it contain? |
| Format | Email, live meeting, dashboard, written report? |
| Frequency | How often — daily, weekly, at milestones? |
| Owner | Who is responsible for producing and sending it? |

Turning the stakeholder register from Module 7 into a communication plan
looks like this:

| Audience | Content | Format | Frequency | Owner |
|---|---|---|---|---|
| Sponsor (VP of Sales) | Overall status: scope/schedule/budget health, top risks | 1:1 meeting + 1-page summary | Weekly | PM |
| Full project team | Detailed task status, blockers, upcoming work | Stand-up meeting | Daily (15 min) | PM / Scrum Master |
| Legal/Compliance | Data-handling design decisions relevant to their approval | Written brief | At two fixed checkpoints | PM |
| Customer Support team | Feature demos, edge cases needing their input | Live demo | Bi-weekly | Product/PM |
| All stakeholders | High-level status, milestones hit, upcoming milestones | Written status report | Weekly | PM |

Notice each row's frequency and format is deliberately different — the
sponsor doesn't need a daily stand-up, and the full team doesn't need a
weekly 1:1 with the PM; the plan tunes communication to what each audience
actually needs, echoing the power/interest logic from Module 7.

## The status report: the PM's most frequent communication

The single most common recurring artifact a PM produces is the **status
report** — and a good one follows a consistent structure so readers can
scan it quickly and compare week to week:

| Section | Content |
|---|---|
| Overall status | A single at-a-glance indicator — commonly Red/Yellow/Green |
| Scope status | On track / at risk / off track, with specifics if not on track |
| Schedule status | On track / at risk / off track vs. the baseline, key milestones hit or missed |
| Budget status | Spend vs. baseline, any projected overrun |
| Top risks/issues | The two or three items that most need stakeholder awareness right now |
| Upcoming | What's happening in the next reporting period |
| Decisions needed | Anything requiring a stakeholder to act or decide |

The **Red/Yellow/Green (RAG) status** deserves particular discipline: it
should reflect an honest assessment against the baseline, not an optimistic
guess or a "everything's fine" reflex. A PM who reports Green every week
right up until a project misses its deadline has trained stakeholders to
stop trusting the status report — which defeats its entire purpose. A
useful discipline: Yellow means "at risk, here's specifically what I'm
watching and what would need to happen to recover it"; Red means "off
track, here's the impact and the options."

## Communication channels and when to use each

Different situations call for different channels, and picking the wrong one
is a common, avoidable failure:

| Situation | Better channel | Why |
|---|---|---|
| Routine weekly status | Written report | Async, scannable, creates a record |
| A blocking issue needs a fast decision | Direct message or call | Speed matters more than a record right now |
| A sensitive or nuanced disagreement | Live conversation (in person or video) | Tone and nuance are lost in text; risk of misinterpretation is high |
| A decision that needs to be referenceable later | Written, with the decision explicitly documented | "We agreed on X in a hallway chat" isn't accountable later |
| Broad awareness across many stakeholders | Dashboard or broadcast email | One-to-many, doesn't require individual replies |

A common mistake is defaulting to email for everything, including sensitive
disagreements that would resolve in five minutes on a call but instead
spiral into a multi-day, tone-ambiguous thread.

## A worked example: the same status, communicated well vs. poorly

A software project's schedule has slipped one week because a third-party
API integration is taking longer than estimated (a risk that was actually
flagged in the risk register — see Module 6).

**Poorly communicated version** — the weekly status email says "Development
is progressing, some integration challenges, overall still on track" — with
overall status marked Green. This is technically not a lie, but it
obscures the fact that the schedule baseline has already slipped, and gives
the sponsor no opportunity to weigh in on trade-offs while there's still
time to make a choice.

**Well-communicated version** — the status report marks overall status
Yellow, states plainly: "The [Vendor] API integration is taking longer than
estimated (originally 6 days, now tracking to 11) due to undocumented rate
limits we discovered this week. This is on the critical path and, if
unresolved, pushes launch from March 15 to March 20. We're mitigating by
adding a second engineer to the integration starting Monday. Decision
needed: are you comfortable with a potential 5-day slip, or would you
prefer we cut a lower-priority feature to protect the original date?" This
version gives the sponsor the same information a week earlier than they'd
otherwise get it, frames it against the specific risk already on record,
and puts a real decision in front of them while there's still time to act
on it — which is the entire point of a communication plan.

## Exercise

Build a communication plan table (audience, content, format, frequency,
owner) for the project you've been developing through this level's
exercises, using your Module 7 stakeholder register as the input. Include
at least four distinct audiences with different formats/frequencies. Then
draft one full weekly status report for your project, including an honest
RAG status and at least one specific risk or issue framed the way the
"well-communicated version" above is — naming the specific cause, the
specific impact, and a specific decision needed from a stakeholder.
