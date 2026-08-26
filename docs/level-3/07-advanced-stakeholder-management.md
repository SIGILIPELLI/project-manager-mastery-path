# 07 · Advanced Stakeholder Management

Basic stakeholder management plots people on a power/interest grid once at
project start and calls it done. Advanced stakeholder management treats that
grid as a living model: stakeholders move between quadrants as the project
progresses, coalitions form and shift, and the real skill is managing
influence networks, not just a static list of names and titles.

## The power/interest grid (recap and extension)

| | Low interest | High interest |
|---|---|---|
| **High power** | Keep satisfied | Manage closely |
| **Low power** | Monitor | Keep informed |

The extension advanced practice adds: track **direction of movement**, not
just current position. A stakeholder moving from "keep informed" toward
"manage closely" (rising interest, power unchanged) is a signal something
changed — often that they've realised the project affects them more than
they first thought.

## Stakeholder register with trend tracking

| Stakeholder | Power | Interest (this quarter) | Interest (last quarter) | Trend | Engagement strategy |
|---|---|---|---|---|---|
| CFO | High | High | Medium | ↑ Rising | Escalate to Manage closely; schedule monthly 1:1 |
| Head of Sales | High | Low | Low | Stable | Keep satisfied; brief only at milestones |
| Regional Ops Lead | Medium | High | Medium | ↑ Rising | Watch — may be building a coalition, engage directly |
| Data Privacy Officer | Medium | Medium | High | ↓ Falling | Investigate why interest dropped — may mean risk went unaddressed silently, not resolved |
| End users (support team) | Low | High | High | Stable | Keep informed; use as a feedback channel |

The Data Privacy Officer's **falling** interest is the entry that should
worry a PM more than any rising one — a stakeholder who used to push hard on
a concern and has gone quiet either got satisfied (good) or gave up on being
heard (very bad, and it resurfaces later as an escalation or a blocked
sign-off). The right response is a direct check-in, not relief that they've
stopped raising issues.

## Stakeholder influence mapping (network, not grid)

A power/interest grid treats every stakeholder as an independent dot. A
network map shows who actually influences whom — critical when a
low-power/high-interest stakeholder turns out to be the person three
high-power stakeholders privately trust before making a decision.

| Stakeholder | Formally reports to | Actually influences (informal) |
|---|---|---|
| Senior Architect (mid-level, IC) | Engineering Director | CFO and VP Eng both ask her opinion before approving technical spend |
| Regional Ops Lead | COO | Three other regional leads follow her position on rollout timing |
| VP Eng | CEO | Formal authority only — team reports low trust in his technical judgement |

The practical consequence: the Senior Architect, who a power/interest grid
would place in "keep informed" (low formal power), is actually a
gatekeeper whose disapproval can quietly stall a CFO sign-off. A PM who
never engages her directly and only briefs the CFO is managing the wrong
node in the network.

## Coalition and resistance patterns

| Pattern | What it looks like | Response |
|---|---|---|
| Silent resistance | Stakeholder agrees in meetings, doesn't act on commitments | Follow up 1:1, ask directly what's blocking action |
| Coalition building | Multiple stakeholders start raising the same objection independently | Address the root concern publicly — a coordinated response, not five separate one-on-ones |
| Sponsor withdrawal | Sponsor stops attending steering committee, delegates to a deputy | Escalate immediately — a project without an engaged sponsor loses its authority to resolve cross-team conflict |
| Malicious compliance | Stakeholder follows the letter of a request in a way designed to prove it won't work | Rare, but real — usually a sign the stakeholder was overruled on the underlying decision and never actually bought in |

## RACI at the stakeholder-network level

For a decision touching multiple stakeholder groups, a single RACI often
undersells how contested a decision actually is. Extend it with a
**position** column showing where each party currently stands:

| Stakeholder | R/A/C/I | Position | Note |
|---|---|---|---|
| CFO | A (Accountable) | Supportive | Wants cost control confirmed before sign-off |
| VP Eng | R (Responsible) | Supportive | Owns delivery |
| Data Privacy Officer | C (Consulted) | **Blocking** | Will not approve without a data residency review completed first |
| Regional Ops Lead | C (Consulted) | Neutral, leaning against | Concerned about rollout disruption to regional teams |
| End users | I (Informed) | N/A | Not consulted on this decision, only notified |

Listing the Data Privacy Officer's position as **Blocking** rather than
burying it as one row among five is what prevents a PM from bringing a
decision to the steering committee assuming consensus and being surprised
by a veto in the room.

## Worked example: engagement plan for a rising-risk stakeholder

The Regional Ops Lead (medium power, rising interest, informally influences
three peers) has started raising rollout-timing concerns in side
conversations rather than in the project's formal forums — a coalition
pattern in its early stage.

**Response plan**:
1. Schedule a 1:1 within the week — don't wait for the next steering
   committee meeting; by then the concern may have hardened into a
   position she can't back down from publicly.
2. Ask directly what specifically about the rollout timing is a problem,
   and whether the other two regional leads share the concern.
3. If the concern is legitimate (e.g., rollout coincides with the regions'
   own quarter-end close), bring a revised timeline option to the *next*
   steering committee as a joint recommendation — with her, not around her.
4. Update the stakeholder register: move her trend to "engaged," and log
   the resolution so it doesn't quietly resurface as unaddressed resistance
   two months later.

## Exercise

Your project has a stakeholder — a department head with medium formal
power — whose meeting attendance has dropped from every steering committee
to zero over three consecutive months, while two of her direct reports have
independently emailed you the same concern about the project's impact on
their team's workload.

1. Classify this using the coalition/resistance pattern table — which
   pattern is this, and what makes you confident it's that one rather than
   simple disengagement?
2. Build a stakeholder register row (power, interest, trend, engagement
   strategy) for this department head.
3. Write the first two sentences of what you would actually say to her in a
   1:1 to re-engage her, specifically referencing what her reports told you
   without making them feel like they were reported on.
