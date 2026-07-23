# 09 · Tools Overview (Jira, MS Project, Asana)

Every module so far has built a framework — a scope statement, a schedule,
a budget, a risk register, a stakeholder register, a communication plan —
using nothing more than tables and structured documents. That's deliberate:
the frameworks are what matter, and they work in any tool, including plain
spreadsheets. This module surveys the software most PMs actually use to run
these frameworks day to day, so the concepts you've learned map onto real
tool choices when you start working on an actual team.

## The three tools, at a glance

| Tool | Best fit | Core model | Weakest fit |
|---|---|---|---|
| **Jira** | Software/agile teams | Issues/tickets moving through a workflow (backlog → in progress → done) | Non-technical stakeholders often find it cluttered |
| **Microsoft Project** | Traditional, schedule-heavy predictive projects | Gantt-chart-first, with deep critical-path/resource-leveling support | Overkill and steep learning curve for small or agile teams |
| **Asana** | General-purpose cross-functional teams | Tasks/projects with flexible views (list, board, timeline, calendar) | Less depth than Jira for engineering-specific workflows, less depth than MS Project for complex scheduling math |

None of these is "the best" in an absolute sense — the right tool depends
on the project's shape (predictive vs. agile, from
[Module 1](01-what-is-project-management.md)), the team's technical
background, and what the rest of the organization already standardizes on.
A PM's job is to pick the tool that fits the *work*, not to force the work
to fit whatever tool is trendiest.

## Jira

Jira, built by Atlassian, is the dominant tool in software development
because its core unit — the **issue** (a bug, a story, a task) — maps
directly onto how software teams already think about work, and because it
natively supports agile frameworks like Scrum and Kanban (fully covered in
Level 2, Module 1).

| Concept | What it means in Jira |
|---|---|
| Issue | A single unit of work — a story, bug, task, or epic |
| Board | A visual view of issues moving through workflow states (To Do → In Progress → Done) |
| Sprint | A fixed time-box (commonly 2 weeks) of committed work, if using Scrum |
| Epic | A large body of work grouping multiple related issues |
| Backlog | The prioritized list of not-yet-started issues |

A PM (or, on many agile teams, a Scrum Master/Product Owner working
alongside a PM) uses Jira primarily for day-to-day execution tracking
rather than upfront long-range scheduling — its native strength is showing
what's actively in flight and what's blocked, not producing a critical-path
Gantt chart, though Jira does offer add-ons/plugins for that.

## Microsoft Project

Microsoft Project is the tool most closely built around the concepts in
[Module 4](04-scheduling-basics.md) — it treats the schedule, with its
dependencies and critical path, as the central object, and calculates the
critical path and float automatically once tasks and dependencies are
entered.

| Concept | What it means in MS Project |
|---|---|
| Task | A single line-item of work, with a duration |
| Predecessor | A dependency link to a prior task (FS/SS/FF/SF, from Module 4) |
| Gantt chart | The default, always-visible view of the whole schedule |
| Critical path | Automatically calculated and highlightable once tasks/dependencies are entered |
| Resource | A person or asset assigned to a task, with an availability calendar |

MS Project's real strength shows up on large, predictive (waterfall-style)
projects with many interdependent tasks and shared resources across
multiple workstreams — construction, infrastructure rollouts, large
enterprise implementations — where the automatic critical-path and resource-
leveling calculations (covered in depth in Level 2, Module 2) save real
manual effort. It's a poor fit for a small agile team that just needs a
shared task board.

## Asana

Asana sits deliberately in the middle: general-purpose enough for
marketing, operations, HR, and cross-functional teams that don't want
Jira's engineering-specific vocabulary or MS Project's scheduling depth, but
still structured enough to track real project work.

| Concept | What it means in Asana |
|---|---|
| Task | A unit of work, assignable to one person, with a due date |
| Project | A collection of tasks, viewable as a list, board, timeline, or calendar |
| Section | A grouping within a project (e.g., "To Do," "In Review," "Done") |
| Timeline view | Asana's Gantt-style view, showing tasks and dependencies over time |
| Portfolio | A roll-up view across multiple projects (relevant again in Level 3's program/portfolio modules) |

Asana's flexibility to switch between list, board, and timeline views of
the *same* underlying tasks is its signature strength — a marketing team
running a mixed agile/ad hoc workflow can use the board view day to day
while the PM switches to timeline view for a sponsor-facing schedule
conversation, without maintaining two separate systems.

## Choosing a tool: a decision guide

| If your project is... | Lean toward |
|---|---|
| Software development using Scrum/Kanban | Jira |
| A large predictive project with complex, interdependent scheduling and resource constraints | Microsoft Project |
| Cross-functional (marketing, ops, general business) with a mix of ad hoc and structured work | Asana |
| Small, informal, or you're just starting out | Any of the three, or even a well-structured spreadsheet — the framework matters more than the tool at small scale |

## A worked example: the same schedule, and why the tool choice mattered

A company runs two projects simultaneously: a software feature build using
Scrum, and an office relocation (the same one used as a worked example in
Module 2). The software team runs entirely in Jira — sprints, a backlog,
and a board — because their work is naturally issue-shaped and iterative,
and no one on that team needs a Gantt chart to know what to do next. The
relocation project, by contrast, is run in Microsoft Project, because it has
dozens of interdependent tasks across vendors (movers, IT contractors, sign
installers) with hard dependencies and a fixed, immovable weekend deadline
— exactly the shape MS Project's critical-path engine is built for. When
the relocation's signage vendor slips two weeks (as it did in Module 2's
example), MS Project immediately recalculates whether that slip touches the
critical path — it did not, because signage had float — sparing the PM a
manual recalculation under time pressure. Using Jira for the relocation, or
MS Project for the sprint-based software work, would have been a mismatch
in both directions: forcing a schedule-first tool onto iterative work, or an
issue-tracker onto a project that lives and dies by its critical path.

## Exercise

For the project you've been developing through this level's exercises,
decide which of the three tools (Jira, MS Project, or Asana) would fit it
best, and write three sentences justifying the choice using the decision
guide above — referencing whether your project is more predictive or more
agile-shaped (Module 1), how complex its dependencies are (Module 4), and
how technical its audience is. Then list which of the concepts from your
chosen tool's table (issue/epic, task/predecessor, task/section) would map
onto items you've already created in this level's exercises — your WBS work
packages, for instance.
