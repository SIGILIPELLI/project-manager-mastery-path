# 06 · Scaling Agile (SAFe, LeSS)

One Scrum team of 7 people can self-organise its way past most coordination
problems by talking to each other daily. Eight teams building one product
cannot — the coordination overhead that a single standup absorbs at team
scale needs explicit structure once you cross roughly 3–5 teams working
toward the same release. This module covers the two most common scaling
frameworks and, more importantly, when scaling is solving a real problem
versus adding ceremony to problems that don't need it.

## Do you actually need to scale?

Before adopting a framework, check the actual symptom:

| Symptom | Root cause | Right response |
|---|---|---|
| Teams keep discovering shared dependencies late | No cross-team visibility mechanism | Add a lightweight sync (Scrum of Scrums), not a full framework |
| Teams disagree on shared architecture | No shared technical governance | Add a Chief Engineer / architecture guild role |
| Releases are blocked because teams finish at different times | No shared cadence | Align sprint length and release train dates |
| Leadership can't see aggregate progress toward one goal | No program-level backlog | Add a program backlog and PI-level planning |

If none of these are true, scaling frameworks add ceremony without solving
anything — the most common scaling mistake is imposing SAFe on 2 teams that
were already coordinating fine over Slack.

## SAFe (Scaled Agile Framework) essentials

| Concept | What it is | Cadence |
|---|---|---|
| Agile Release Train (ART) | 5–12 teams (50–125 people) delivering one product/value stream | Continuous |
| Program Increment (PI) | A fixed planning horizon, usually 4–6 sprints | Every 8–12 weeks |
| PI Planning | A 2-day event where all teams plan the PI together, surface cross-team dependencies live | Once per PI |
| Program backlog | Features (bigger than a story, smaller than an epic) prioritised for the ART | Continuously groomed |
| System Demo | All teams demo integrated work together | Every sprint |
| Inspect & Adapt | Retrospective at the ART level | End of each PI |

### PI planning dependency board — worked example

Four teams plan a PI together. Each proposes features; dependencies surface
live during planning:

| Team | Feature | Depends on | Status after planning |
|---|---|---|---|
| Checkout | Support saved payment methods | Payments team's tokenisation API | Committed — API confirmed ready Sprint 2 |
| Payments | Tokenisation API | — | Committed, Sprint 1–2 |
| Search | Faceted filtering | — | Committed, no dependencies |
| Mobile | Native checkout flow | Checkout team's saved payment methods | **Risk** — Checkout won't finish until Sprint 4, Mobile wanted Sprint 3 |

The Mobile/Checkout conflict, caught live in the room during PI planning
rather than discovered in Sprint 3 stand-up, is the entire value proposition
of the event: Mobile either resequences its own backlog to pull the native
checkout story to Sprint 5, or the ART negotiates Checkout pulling its work
forward — a trade-off made once, deliberately, by both teams' POs in the
same room, instead of an unplanned scramble mid-PI.

## LeSS (Large-Scale Scrum) essentials

LeSS scales by **removing** structure rather than adding it — the core bet
is that most coordination problems are better solved by fewer artificial
boundaries, not more roles.

| Concept | SAFe equivalent | LeSS approach |
|---|---|---|
| Backlog | Program backlog + team backlogs | **One** product backlog for all teams |
| Planning | PI Planning (2 days, all teams) | Sprint Planning 1 (joint, prioritise together) + Sprint Planning 2 (per-team, per-feature) |
| Roles | RTE, Product Manager, per-team PO | One Product Owner for the whole product, area POs optional at larger scale |
| Cross-team sync | Scrum of Scrums | Overall Retrospective + informal "just talk to the other team" norm |
| Team size supported | 5–12 teams typical | 2–8 teams (LeSS), 8+ teams (LeSS Huge) |

LeSS is a better fit when teams work on a genuinely shared codebase and can
self-organise around a single backlog; SAFe's heavier structure earns its
keep when teams are more independent (separate services, separate release
cadences) and need an explicit train to stay synchronised.

## Framework comparison

| | SAFe | LeSS |
|---|---|---|
| Philosophy | Add structure to coordinate at scale | Remove structure, extend Scrum's simplicity |
| Best for | 5+ teams, complex dependencies, regulated environments wanting visible governance | 2–8 teams, shared codebase, strong existing agile culture |
| Overhead | Higher (dedicated RTE, PI events) | Lower, relies on team discipline |
| Common failure mode | "SAFe theatre" — ceremonies without behaviour change | Underestimating the discipline a single backlog demands at scale |

## Scrum of Scrums (the lightweight middle ground)

For organisations not ready to adopt a full framework, a Scrum of Scrums is
often the right-sized answer: one representative per team, meeting 2–3 times
a week, discussing only cross-team blockers — not a status report.

| Team | Rep | This week's cross-team item |
|---|---|---|
| Checkout | Priya | Waiting on Payments' API — on track for Sprint 2 |
| Payments | Dev | No blockers, flagging early: API contract may add one more field |
| Search | Omar | None |
| Mobile | Lin | Flagging risk on Checkout dependency — see PI board above |

## Exercise

A 60-person product organisation runs 6 Scrum teams. Three teams share one
codebase and coordinate constantly already; the other three build
independent services with separate release cadences and frequently
discover shared dependencies only after a sprint has started.

1. Recommend LeSS, SAFe, or a mixed approach, and justify using the specific
   difference between the two groups of teams described.
2. Build a PI-planning-style dependency board (like the worked example)
   with 3 invented features across 3 of the independent-service teams,
   including at least one cross-team dependency that would only surface if
   discovered live in planning.
3. Name one concrete symptom from the "do you actually need to scale?"
   table that would tell you this organisation should scale down its
   process instead of up.
