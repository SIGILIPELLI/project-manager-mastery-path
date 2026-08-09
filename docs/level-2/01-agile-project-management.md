# 01 · Agile Project Management

Level 1 described the **predictive** (waterfall) lifecycle: define scope up
front, plan the whole schedule, then execute against it. Agile inverts the
assumption. Instead of treating scope as fixed and letting cost and schedule
absorb uncertainty, agile fixes cost and schedule (a team of a known size,
working in fixed-length iterations) and lets **scope** flex — you deliver the
highest-value slice of the backlog that fits, and re-decide what's next every
iteration. This module covers the two dominant agile frameworks a PM actually
encounters — Scrum and Kanban — plus the estimation and forecasting math that
makes an agile plan defensible to a sponsor who wants a date.

## When agile fits, and when it doesn't

Agile is not universally superior; it's a fit for a particular kind of
uncertainty. The practical test is: **is the requirement stable enough to
plan in detail six months out?**

| Condition | Predictive fits | Agile fits |
|---|---|---|
| Requirements clarity | Well understood, stable | Emerging, expected to change |
| Feedback loop | Value only visible at the end | Partial product is usable and testable early |
| Regulatory/contract constraint | Fixed scope contractually mandated | Scope negotiable within a fixed budget |
| Cost of change late | Very high (physical build, hardware) | Low (software, content, service design) |
| Stakeholder availability | Sign-off at gates | Continuous, weekly involvement |

Most real portfolios are **hybrid**: an agile delivery team inside a
predictive governance wrapper (fixed annual budget, stage-gate funding,
milestone reporting to a steering committee). Knowing how to translate
between the two — velocity into a forecast date, story points into a spend
rate — is the core PM skill in this module.

## Scrum: roles, events, artifacts

Scrum is a lightweight framework built around fixed-length iterations called
**sprints** (typically 2 weeks).

| Element | Type | Purpose |
|---|---|---|
| Product Owner | Role | Owns and orders the product backlog; single voice on priority and acceptance |
| Scrum Master | Role | Facilitates the process, removes impediments, protects the team from mid-sprint churn |
| Developers | Role | The people who build the increment; self-managing on *how* the work gets done |
| Sprint Planning | Event | Team pulls the top of the backlog into a sprint goal and sprint backlog |
| Daily Scrum | Event | 15-minute team sync on progress toward the sprint goal and blockers |
| Sprint Review | Event | Demo the increment to stakeholders; gather feedback that reshapes the backlog |
| Sprint Retrospective | Event | Team inspects its own process and commits to one or two concrete improvements |
| Product Backlog | Artifact | Ordered list of everything wanted in the product |
| Sprint Backlog | Artifact | The subset pulled into this sprint, plus the plan to deliver it |
| Increment | Artifact | The working, potentially releasable output of the sprint |

Two rules do most of the work: the **sprint goal doesn't change mid-sprint**
(new requests go to the backlog for the next planning session), and the
increment must meet the team's **Definition of Done** — a standing checklist
of what "done" means (code reviewed, tests passing, documentation updated,
deployed to staging). Without a Definition of Done, velocity is measuring
partially-finished work, and every forecast built on it is fiction.

## Kanban: flow instead of iterations

Kanban has no sprints. Work moves continuously across a board, and the
control mechanism is a **work-in-progress (WIP) limit** on each column.

| Backlog | Ready (WIP 5) | In Progress (WIP 3) | Review (WIP 2) | Done |
|---|---|---|---|---|
| 40+ items | 4 items | 3 items | 2 items | — |

When "In Progress" is at its limit of 3, nobody may start a fourth item —
the team must first help finish something already in flight. That is the
entire point: WIP limits convert a team's instinct to *start* work into an
instinct to *finish* work, which is what actually reduces cycle time.

| Metric | Definition | What it tells you |
|---|---|---|
| Lead time | Request accepted → delivered | What a stakeholder experiences |
| Cycle time | Work started → delivered | The team's actual throughput speed |
| Throughput | Items completed per week | Capacity, for forecasting |
| WIP | Items in flight right now | Early warning — rising WIP predicts rising cycle time |

| | Scrum | Kanban |
|---|---|---|
| Cadence | Fixed sprints | Continuous flow |
| Commitment | Sprint goal per iteration | Per-item, pull-based |
| Change mid-cycle | Discouraged | Allowed any time, respecting WIP |
| Core metric | Velocity | Cycle time / throughput |
| Best for | Feature development against a roadmap | Support, ops, maintenance, unpredictable arrival of work |

## Estimation: story points and capacity

Story points are a **relative** measure of size (complexity + effort +
uncertainty), not hours. They work because humans compare well ("this is
about twice that") and forecast absolute durations badly. Teams typically
estimate on a modified Fibonacci scale — 1, 2, 3, 5, 8, 13 — where the
widening gaps encode the fact that big things are estimated less precisely.

Capacity is the separate, concrete question of how many person-hours the
sprint actually contains. For a 2-week (10 working day) sprint:

| Person | Days available | Productive hours (6/day) |
|---|---|---|
| Dev 1 | 10 | 60 |
| Dev 2 | 8 (2 days PTO) | 48 |
| Dev 3 | 10 | 60 |
| QA | 9 (1 day training) | 54 |
| Designer | 7 (3 days on another project) | 42 |
| Product Owner (part-time) | 5 | 30 |
| **Total** | | **294 hours** |

Note the six-productive-hours-per-day assumption: an 8-hour day contains
meetings, email, and interruptions. Applying a **focus factor** of 0.8 to
absorb unplanned support work gives 294 × 0.8 ≈ **235 hours** of real sprint
capacity. A team that plans against 6 people × 10 days × 8 hours = 480 hours
will over-commit by roughly a factor of two and miss every sprint.

## A worked example: forecasting a release date from velocity

A team has completed five sprints. Velocity (story points accepted, meeting
the Definition of Done) per sprint:

| Sprint | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Velocity | 23 | 31 | 28 | 34 | 29 |

Average velocity = (23 + 31 + 28 + 34 + 29) ÷ 5 = 145 ÷ 5 = **29 points per
sprint**. The remaining backlog for the release is estimated at **260
points**.

- **Expected case** (average velocity 29): 260 ÷ 29 = 8.97 → **9 sprints**
- **Optimistic case** (best observed, 34): 260 ÷ 34 = 7.65 → **8 sprints**
- **Pessimistic case** (worst observed, 23): 260 ÷ 23 = 11.30 → **12 sprints**

With 2-week sprints, that is a forecast range of **16 to 24 weeks, most
likely 18 weeks**. This is the correct way to answer "when will it be done?"
in an agile context: a range grounded in the team's own measured throughput,
not a single date grounded in optimism. Reporting only the 18-week figure
hides the fact that a run of sprints at the low end pushes the release out by
a further six weeks.

Two things invalidate this forecast, and watching for both is the PM's job.
First, **scope growth**: if the backlog grows by 40 points during those
sprints, the expected case becomes (260 + 40) ÷ 29 = 10.34 → 11 sprints, so
the forecast must be recalculated every sprint against the *current* backlog,
not the original one. Second, an **inconsistent Definition of Done**: if
sprint 4's 34 points included two stories that were demoed but never actually
tested, the real velocity was closer to 26, and the whole forecast rests on
an inflated number. Velocity is a forecasting instrument only when "done"
means the same thing every sprint.

## Reporting agile work to a predictive governance layer

A steering committee that funds by quarter does not want story points. The
translation table below is what a PM prepares before that meeting:

| Sponsor's question | Agile evidence | Translation |
|---|---|---|
| When will it be done? | Velocity 29, range 23–34; backlog 260 points | "18 weeks expected, 16–24 week range" |
| What will it cost? | Budget ÷ total points = cost per point | Remaining points × cost per point |
| What are we getting? | Sprint review demo | A working increment, not a status slide |
| Is scope under control? | Backlog size trend per sprint | A rising backlog means scope growth — flag it |
| Are we on track? | Velocity trend plus burndown slope | Declining velocity is the leading indicator |

!!! warning "Velocity is a planning tool, not a performance target"
    The moment velocity becomes a number the team is judged on, it inflates:
    estimates drift upward, the same work gets scored 8 instead of 5, and the
    metric stops predicting anything. Compare a team only against its own
    history, never against another team's points, and never set a velocity
    target in a performance review.

## Exercise

Take a project you know and set it up as an agile delivery. (1) Write a
product backlog of at least 12 items, estimated in story points on the
1/2/3/5/8/13 scale, and state the relative reasoning for two of them ("this
is a 5 because it's about twice the 3 we did last sprint"). (2) Build a
capacity table for a 2-week sprint with a realistic team, applying a
productive-hours assumption and a focus factor — show your arithmetic. (3)
Write a Definition of Done with at least five checkable criteria. (4) Invent
five sprints of plausible velocity, compute the average, and produce a
three-point release forecast (optimistic / expected / pessimistic) in sprints
*and* in weeks for your remaining backlog. (5) Finally, state whether Scrum or
Kanban is the better fit for your project, and defend the choice against the
"when agile fits" table above.
