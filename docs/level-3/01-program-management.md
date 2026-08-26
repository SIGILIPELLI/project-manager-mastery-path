# 01 · Program Management

A project delivers an output. A **program** delivers a set of related outputs
that only add up to something when managed together. If you can cancel one
piece without touching the business case for the rest, you have a portfolio
of independent projects, not a program. The test that matters: does the
program exist to capture **benefits** that no single project in it could
claim on its own? If yes, you need program management, not just more PMs
reporting up to one director.

## Project vs. program vs. portfolio

| | Project | Program | Portfolio |
|---|---|---|---|
| Unit of work | Deliverable | Set of related deliverables | Set of initiatives (may be unrelated) |
| Success measure | On time/budget/scope | Benefits realised | Strategic alignment, ROI mix |
| Time horizon | Fixed end date | Often rolling, benefit-driven | Continuous |
| Manager cares about | The plan | The plans, and the seams between them | The mix and the trade-offs |
| Typical artefact | Project charter | Program roadmap + benefits map | Portfolio scoring model |

## The benefits map

The single artefact that justifies a program's existence is the map from
projects to benefits. Build it before you build a program roadmap — a
roadmap with no benefits map is just a shared calendar.

| Benefit | Target value | Owner | Contributing projects | Realisation date |
|---|---|---|---|---|
| Reduce order-to-cash cycle | 12 days → 5 days | VP Finance | Billing API rework, Collections workflow | Q3 |
| Cut support ticket volume | −30% | Head of Support | Self-serve portal, Knowledge base migration | Q2 |
| Enable EU market entry | Launch in 3 countries | VP Sales | Localisation platform, GDPR data residency | Q4 |

Notice that "Cut support ticket volume" needs **two** projects finishing
roughly together — the portal without the knowledge base migration leaves
customers self-serving into an empty search index. That interdependency is
the entire reason this work is a program: a project manager on either piece,
managing to their own charter alone, has no visibility into the other and no
incentive to sequence around it.

## The program manager's real job: managing the seams

Individual project managers own their project's scope, schedule, budget, and
risk. The program manager owns what falls **between** projects:

- **Shared resources** — the two best backend engineers are needed by both
  Billing API rework and Collections workflow in the same sprint.
- **Cross-project dependencies** — Collections workflow cannot start
  integration testing until Billing API rework ships its new events.
- **Consolidated risk** — a risk that's "medium" on each of three projects
  individually might be "severe" for the program if all three would be hit by
  the same root cause (e.g., all three depend on the same vendor API).
- **Benefits tracking** — projects report "done." Only the program tracks
  whether "done" produced the 12-to-5-day cycle time reduction six months
  later.
- **Change arbitration** — when a change request on one project would blow a
  dependency another project relies on, someone above both PMs has to decide.

### Program dependency map

| From project | To project | Dependency | Type | Slack |
|---|---|---|---|---|
| Billing API rework | Collections workflow | New payment-status events | Finish-to-start | 0 weeks (critical) |
| Localisation platform | GDPR data residency | Shared EU database schema | Start-to-start | 2 weeks |
| Self-serve portal | Knowledge base migration | None (parallel, converge at launch) | Finish-to-finish | 3 weeks |

A finish-to-start dependency with **zero slack** is the program's real
critical path, even though it crosses a project boundary that neither
individual project schedule shows. This is why program-level schedules exist
separately from project schedules: rolling up three Gantt charts side by side
does not surface a cross-project dependency with no slack — you have to draw
the arrow explicitly.

## Worked example: sequencing a 3-project program

A retail company runs a program with three projects targeting the benefits
map above. Capacity is fixed at 14 senior engineers across the program.

| Project | Engineers needed | Duration | Depends on |
|---|---|---|---|
| Billing API rework | 6 | 8 weeks | — |
| Collections workflow | 5 | 6 weeks | Billing API rework (finish-to-start) |
| Localisation platform | 8 | 10 weeks | — |
| GDPR data residency | 4 | 5 weeks | Localisation platform (start-to-start, 2wk offset) |
| Self-serve portal | 5 | 7 weeks | — |
| Knowledge base migration | 3 | 4 weeks | — |

Running everything in parallel needs 6+5+8+4+5+3 = 31 engineers at peak —
more than double the 14 available. The program manager's job is to sequence,
not to staff up:

- **Weeks 1–8**: Billing API rework (6) + Self-serve portal (5) = 11 engineers.
  Knowledge base migration (3) fits in the remaining capacity → 14 total.
- **Weeks 3–13**: Localisation platform (8) starts at week 3, overlapping the
  above only from week 3–8 (8 + 11 = 19, over capacity) — so Localisation
  platform must instead start at week 9, after Billing API rework and
  Knowledge base migration free up capacity.
- **Weeks 9–19**: Localisation platform (8) + Collections workflow (5, starts
  week 9 once Billing API rework finishes) = 13 engineers. Fits.
- **Weeks 11–16**: GDPR data residency (4) starts 2 weeks after Localisation
  platform begins (week 11) → 8 + 4 = 12 at that overlap, plus Collections
  workflow's 5 ending at week 15 → peaks at 17. Still over.

The fix the program manager actually makes: delay GDPR data residency's start
by 3 more weeks (week 14, once Collections workflow has released its 5
engineers), bringing the peak back to 12. This is exactly the kind of
trade-off a project-level schedule can't see — it only becomes visible when
all six schedules sit on one resource-constrained timeline.

## RAID log at program level

Program risk registers track items that span or exceed any single project's
register:

| ID | Type | Description | Affects | Impact | Owner | Response |
|---|---|---|---|---|---|---|
| PR-01 | Risk | Payment gateway vendor shared by two projects has had 3 outages this quarter | Billing API rework, Collections workflow | High | Program manager | Negotiate SLA credit clause; build retry queue in both projects |
| PR-02 | Assumption | EU data residency requirements won't change before Q4 launch | Localisation platform, GDPR data residency | High | Legal lead | Monthly legal review; escalate if regulation drafts change |
| PR-03 | Issue | Two projects both assumed they'd get the same 2 senior QA engineers in week 9 | Collections workflow, GDPR data residency | Medium | Program manager | Reallocate one from Self-serve portal (has 1-week slack) |
| PR-04 | Dependency | Collections workflow blocked entirely until Billing API rework ships events | Collections workflow | Critical | Program manager | Zero slack — track weekly, no buffer available |

## Exercise

You are the program manager for a program with three projects: Project A (40
days, needs 4 engineers), Project B (25 days, needs 3 engineers, cannot start
until Project A is 50% complete), and Project C (30 days, needs 5 engineers,
fully independent). Your organisation can staff a maximum of 8 engineers
across the program at any time.

1. Build a benefits map: invent one plausible benefit that requires both
   Project A and Project B to be complete, and one benefit that Project C
   alone delivers.
2. Draw the dependency table (from/to/type/slack) for A → B.
3. Sequence the three projects across the 8-engineer cap. State which weeks
   each project runs, and show the peak headcount in every overlapping
   window to prove you never exceed 8.
4. Write two program-level RAID entries (one risk, one dependency) that
   would not appear on any single project's own register.
