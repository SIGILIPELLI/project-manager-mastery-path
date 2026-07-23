# 04 · Scheduling Basics

Once scope is broken down into work packages ([Module 3](03-scope-management-basics.md)),
the next question is: in what order, and by when? Scheduling turns a list of
work into a time-bound plan by sequencing tasks, estimating durations,
identifying dependencies between them, and surfacing the **critical path** —
the sequence of tasks that determines the earliest the whole project can
finish. This module covers the foundational tools: Gantt charts, task
dependencies, and a first pass at critical path thinking (a full treatment,
including resource leveling, is in Level 2).

## From WBS to schedule: durations and dependencies

Each work package from the WBS needs two things before it can be placed on a
timeline: an **estimated duration** (how long it takes) and its
**dependencies** (what has to happen before it can start, and what's waiting
on it to finish). There are four standard dependency types:

| Dependency type | Meaning | Example |
|---|---|---|
| Finish-to-Start (FS) | Task B can't start until Task A finishes | Can't paint a wall until drywall is up |
| Start-to-Start (SS) | Task B can't start until Task A starts | QA test-writing can start once development starts |
| Finish-to-Finish (FF) | Task B can't finish until Task A finishes | Final proofreading can't finish until final edits finish |
| Start-to-Finish (SF) | Task B can't finish until Task A starts | Rare — e.g., old system can't be shut down until new system starts running |

Finish-to-Start is by far the most common dependency in everyday project
schedules; the other three matter mainly when work genuinely overlaps.

## Gantt charts

A **Gantt chart** is the standard visual for a project schedule: each task
is a horizontal bar, positioned along a timeline, with its length showing
duration and its position showing when it starts and ends. Dependencies are
usually shown as arrows connecting the end of one bar to the start of
another.

A simplified Gantt chart for a small product launch, shown as a table
(each `█` represents roughly one week):

| Task | Wk1 | Wk2 | Wk3 | Wk4 | Wk5 | Wk6 |
|---|---|---|---|---|---|---|
| Finalize requirements | █ | | | | | |
| Design | | █ | █ | | | |
| Development | | | █ | █ | █ | |
| Testing | | | | | █ | █ |
| Launch prep | | | | | | █ |

Reading this: Development can't start until Design has produced enough to
build against (an FS or SS dependency), Testing overlaps the tail end of
Development (an SS dependency, since some testing can begin on completed
pieces before all development finishes), and Launch prep is the final task,
dependent on Testing finishing. The chart makes the whole sequence — and
where things overlap versus wait — visible at a glance, which is exactly
why it remains the default view in almost every scheduling tool covered in
[Module 9](09-tools-overview.md).

## Critical path: the sequence that sets your finish date

Not every task delay pushes out the project's end date — only delays to
tasks on the **critical path** do. The critical path is the longest
sequence of dependent tasks from start to finish; it determines the
shortest possible time the project can take. Tasks *not* on the critical
path have **float** (also called **slack**) — some amount of time they can
slip without affecting the finish date.

Take a small example with four tasks and their durations and dependencies:

| Task | Duration | Depends on |
|---|---|---|
| A — Requirements | 3 days | — |
| B — Design | 5 days | A |
| C — Content writing | 2 days | A |
| D — Development | 4 days | B |
| E — Launch | 1 day | C, D |

There are two paths from start to finish:

- **A → B → D → E**: 3 + 5 + 4 + 1 = **13 days**
- **A → C → E**: 3 + 2 + 1 = **6 days**

The longest path, A → B → D → E at 13 days, is the **critical path** — this
is the true minimum project duration. Task C (Content writing) has
13 − 6 = **7 days of float**: it could take up to 7 extra days without
pushing the launch date out, because it's not on the path that determines
the finish. But if Task B (Design) slips by even one day, the whole
project slips by one day, because it sits directly on the critical path.
This is why an experienced PM doesn't chase every yellow flag equally —
they watch the critical path far more closely than tasks sitting on slack.
A full method for calculating float mathematically (the Critical Path
Method, with forward and backward passes) is covered in Level 2, Module 2;
this module's goal is the concept: know which tasks actually control your
finish date.

## A worked example: a schedule that looked fine until the critical path shifted

A team is building a mobile app feature with four work packages: API
design (2 days), backend build (6 days, depends on API design), UI design
(3 days, no dependency — can start immediately), and front-end build
(5 days, depends on both backend build and UI design being far enough
along). At the project kickoff, the PM eyeballs the schedule and assumes
the backend build — the longest single task — is the thing to watch.

Running the two paths: **API design → backend build → front-end build** =
2 + 6 + 5 = 13 days. **UI design → front-end build** = 3 + 5 = 8 days.
The critical path is the first one, through backend build, confirming the
PM's instinct — for now. Two weeks in, backend build finishes a day early
(5 days instead of 6), but UI design — which had 13 − 8 = 5 days of float —
slips by 6 days due to a designer being pulled onto a different fire. The
UI design path is now 3 + 6 = 9 days late-start-adjusted, versus the
backend path's 2 + 5 = 7 days: **the critical path has shifted to run
through UI design.** A PM who kept watching only the backend build (their
original assumption) would have missed this until front-end build was
blocked waiting on a UI design that was quietly eating all its float. The
lesson: the critical path isn't fixed at kickoff — it has to be
re-evaluated any time a task's actual progress deviates from plan.

## Exercise

Using the four-task example structure above (a small set of dependent
tasks), sketch your own five-task schedule for a project of your choice —
list each task, its estimated duration, and what it depends on. Identify
every path from start to finish, calculate each path's total duration, and
name the critical path. Then pick one non-critical task and state how much
float it has, and one critical task and explain, in a sentence, what would
happen to the finish date if it slipped by three days.
