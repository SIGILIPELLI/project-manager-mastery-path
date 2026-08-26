# 05 · PMO Fundamentals

A Project Management Office (PMO) exists to solve a problem that shows up
only once an organisation runs more than a handful of projects at once:
every project reinvents its own templates, reports status in a different
format, and escalates risk in its own voice — so nobody above the individual
PM level can actually compare, prioritize, or intervene. A PMO's job is
standardisation and visibility, not doing the projects' work for them.

## Three PMO types

| Type | Authority level | Typical role | Risk if overdone |
|---|---|---|---|
| **Supportive** | Low — advisory only | Templates, training, a repository of lessons learned | Ignored; no real influence |
| **Controlling** | Medium — requires compliance | Enforces methodology, governance gates, mandatory reporting | Bureaucratic drag if gates outnumber the value they add |
| **Directive** | High — PMs report into the PMO | PMO directly manages projects; PMs are PMO staff assigned out | Can become a bottleneck; local context gets lost |

Most organisations land on controlling: enough teeth to make standards
stick, not so much that it owns delivery risk it can't actually see day to
day.

## What a PMO actually delivers

| Function | Deliverable | Cadence |
|---|---|---|
| Governance | Stage-gate criteria, escalation thresholds | Set once, reviewed annually |
| Standardisation | Templates (charter, risk register, status report) | Maintained continuously |
| Portfolio reporting | Roll-up dashboard across all active projects | Weekly or monthly |
| Resource coordination | Capacity view across projects, conflict resolution | Ongoing |
| Methodology support | Training, coaching, embedded PM support | Ongoing |
| Lessons learned | Cross-project retrospective repository | After every project close |

## The PMO dashboard — rolling up projects with different metrics

The hardest technical problem a PMO solves is comparability: Project A
reports CPI/SPI, Project B is a small Kanban team with no EVM at all. A PMO
dashboard needs a **common status taxonomy** layered on top of whatever each
project natively tracks.

| Project | Method | Native metric | Normalised RAG* | Budget health | Schedule health |
|---|---|---|---|---|---|
| Platform migration | Waterfall/EVM | CPI 0.91, SPI 0.95 | Amber | Amber (9% over) | Amber (5% behind) |
| Mobile app v2 | Scrum | Velocity 34 vs. plan 40 | Amber | Green | Amber (15% under velocity) |
| Compliance update | Waterfall | On schedule, on budget | Green | Green | Green |
| Internal tooling | Kanban | Cycle time 6d vs. target 4d | Red | Green | Red (50% over cycle time target) |

*RAG = Red/Amber/Green, the PMO's translation layer. The rule for deriving
RAG from CPI/SPI (module 09 covers this in depth): CPI or SPI below 0.90 is
Red, 0.90–0.95 is Amber, above 0.95 is Green — and the equivalent bands are
defined once for velocity-shortfall percentage and cycle-time overrun so a
Scrum team and a Waterfall team roll up onto the same dashboard color.

## Stage-gate governance

| Gate | Question answered | Who approves | Typical criteria |
|---|---|---|---|
| G0: Idea | Is this worth scoping? | Portfolio board | Aligns to a strategic theme |
| G1: Charter | Should we commit resources to plan it? | Sponsor | Charter signed, rough budget/timeline |
| G2: Plan | Should we fund execution? | Steering committee | Baseline plan, risk register, resourcing confirmed |
| G3: Mid-point | Is this still on track to deliver the benefit? | PMO + sponsor | EVM within thresholds, top risks mitigated |
| G4: Close | Did it deliver, and what did we learn? | Sponsor + PMO | Acceptance signed off, lessons logged |

A controlling PMO enforces that a project cannot draw its next funding
tranche without clearing the relevant gate — this is the mechanism, not the
dashboard, that gives the PMO real teeth. The dashboard informs; the gate
enforces.

## Worked example: PMO capacity conflict resolution

Three active projects each request the same specialised database engineer
for the same two-week window:

| Project | Priority score (module 02 model) | Weeks requested | Business impact of delay |
|---|---|---|---|
| Platform migration | 85 | Weeks 10–11 | Delays a compliance deadline |
| Mobile app v2 | 76 | Weeks 10–11 | Slips a marketing launch by 2 weeks |
| Internal tooling | 60 | Weeks 10–11 | Slips an internal-only milestone, no external commitment |

The PMO does not average the requests or split the engineer's time three
ways (which would delay all three) — it applies the portfolio priority
ranking already agreed at the portfolio level (module 02) and assigns the
engineer to Platform migration (85) first, offers Mobile app v2 (76) the
following two weeks with an explicit 2-week schedule impact logged as an
issue, and tells Internal tooling (60) it will need to source the skill
elsewhere or slip. This is the PMO doing its actual job: resolving a
resource conflict using a pre-agreed, defensible ranking instead of
whichever PM escalates loudest.

## PMO maturity self-assessment

| Dimension | Level 1: Ad hoc | Level 2: Standardised | Level 3: Managed | Level 4: Optimised |
|---|---|---|---|---|
| Templates | None, every PM invents their own | Common templates exist | Templates enforced via gate | Templates auto-populate from data |
| Reporting | Manual, inconsistent | Common RAG taxonomy | Live dashboard | Predictive (forecasts, not just status) |
| Resourcing | No visibility | Spreadsheet tracked | Tool-tracked, conflicts surfaced | Capacity modeled ahead of demand |
| Lessons learned | Not captured | Captured, rarely reused | Reviewed at project start | Fed into estimation models |

Most PMOs overestimate their own maturity level by one full column — a
useful gut check is asking whether the PMO's *own* processes have ever been
retrospected using the lessons-learned template it mandates for projects.

## Exercise

Your organisation runs 6 concurrent projects with no PMO today: reporting
formats differ, two projects have quietly missed their compliance deadlines
because nobody rolled up risk across them, and PMs regularly fight over the
same two data engineers.

1. Recommend a PMO type (supportive/controlling/directive) for this
   situation and justify it in 3–4 sentences using the specific symptoms
   given.
2. Design a 4-row RAG-normalisation table (like the one above) for two
   Waterfall projects and two Agile projects, defining the numeric
   threshold that produces each color for both methodologies.
3. Using the priority-score-based resolution approach shown above, resolve
   a conflict where three projects with scores 90, 55, and 55 all need the
   same engineer for the same week — state the outcome and why ties (55/55)
   need a second tiebreaker criterion beyond the score.
