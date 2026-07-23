# 02 · Project Lifecycle Basics

Every project — regardless of industry, size, or delivery approach — moves
through the same four broad phases: **Initiation**, **Planning**,
**Execution** (with monitoring and controlling happening continuously
alongside it), and **Closure**. [Module 1](01-what-is-project-management.md)
introduced these as five activities; this module slows down and treats each
phase as a distinct stage with its own entry criteria, exit criteria, and
key deliverables — the skeleton that every later module in this course hangs
work on.

## The four phases

| Phase | Central question | Typical deliverables | Exit criteria |
|---|---|---|---|
| Initiation | Should we do this, and are we authorized to? | Project charter, high-level business case | Charter signed by a sponsor |
| Planning | How exactly will we deliver it? | Scope statement, schedule, budget, risk register, communication plan | Baselines approved by the sponsor/stakeholders |
| Execution & Monitoring/Controlling | Are we building it, and are we still on track? | Status reports, change requests, updated RAID log | Deliverables accepted, scope substantially complete |
| Closure | Is it actually done, and what did we learn? | Acceptance sign-off, lessons learned, final report | Formal sign-off, resources released |

A phase is not a rigid calendar block — on most real projects, planning and
execution overlap (you refine next month's plan while this month's work is
underway), and monitoring/controlling runs continuously from the moment
execution starts until closure. What matters is that each phase has clear
entry and exit criteria: skipping straight to execution without a signed
charter, or calling a project "closed" without a sign-off, is exactly how
scope creep and unresolved disputes happen later.

## Phase 1 — Initiation

Initiation answers one question: *is this project worth doing, and who is
formally authorizing it?* The central artifact is the **project charter** —
a short document, usually one to two pages, that a sponsor signs to
formally authorize the project and give the PM the authority to spend
budget and assign resources. A charter typically includes:

| Charter element | What it captures |
|---|---|
| Project purpose/justification | Why this project exists, in business terms |
| High-level objectives | What success looks like, at a glance |
| Sponsor & key stakeholders | Who is accountable, who has a stake |
| High-level budget & timeline | Rough order-of-magnitude numbers, refined later |
| Assumptions & constraints | What we're taking as given, what limits we're operating under |
| Assigned project manager & authority level | Who's running it, and what they can approve without escalating |

Without a signed charter, a PM has no formal authority — they're running a
project on goodwill, which tends to collapse the first time budget or
priorities get contested.

## Phase 2 — Planning

Planning turns the charter's high-level intent into a concrete, resourced
plan. This is where most of this course's Level 1 modules live: scope
management ([Module 3](03-scope-management-basics.md)) defines exactly what
will and won't be built, scheduling ([Module 4](04-scheduling-basics.md))
sequences the work in time, budgeting ([Module 5](05-budget-cost-basics.md))
attaches real cost to it, risk management
([Module 6](06-risk-management-basics.md)) identifies what could go wrong,
and stakeholder and communication planning
([Modules 7](07-stakeholder-management-basics.md)–[8](08-communication-plans.md))
define who needs to know what, and when. The outputs of planning are
**baselines** — the approved scope, schedule, and budget that execution will
be measured against. A baseline isn't meant to be permanent (real projects
change), but any deviation from it should go through a deliberate change
process rather than quietly drifting.

## Phase 3 — Execution, with Monitoring & Controlling

Execution is where the actual work of the project happens: developers
build, designers design, contractors pour concrete, writers write.
Monitoring & Controlling runs in parallel, continuously, for the entire
duration of execution — it is not a separate later phase. The PM's job
during this stretch is to compare actual progress against the baselines set
in planning, and act early when a gap opens up:

- **Status reporting** — regular, structured updates on scope/schedule/
  budget health (see [Module 8](08-communication-plans.md)).
- **Issue and risk tracking** — a live RAID log (Risks, Assumptions, Issues,
  Dependencies) that gets reviewed on a set cadence, not just when something
  breaks.
- **Change control** — any request to alter the approved scope, schedule, or
  budget goes through a defined process (assess impact → get sponsor
  approval → update the baseline) rather than being absorbed silently.

## Phase 4 — Closure

Closure is the most frequently shortchanged phase — the team is already
mentally on the next project — but skipping it has real cost. Closure
includes:

- **Formal acceptance** — the sponsor or client explicitly confirms the
  deliverable meets the agreed scope (tied back to the exit criteria in the
  charter and scope statement).
- **Administrative closure** — final invoices settled, contracts closed out,
  documentation archived.
- **Lessons learned** — a short retrospective capturing what went well, what
  didn't, and what the team would do differently — the single highest-value,
  lowest-cost activity for improving every future project, and the one most
  often skipped under time pressure.
- **Resource release** — team members and contractors are formally freed to
  move to their next assignment.

## A worked example: opening and closing gates for an office relocation

A company is relocating its 80-person office to a new building in four
months. Walking the lifecycle:

1. **Initiation** — the COO signs a one-page charter: purpose (current lease
   expires, new space is 20% cheaper per square foot), objective (fully
   operational in the new space by the lease end date with zero missed
   business days), sponsor (COO), rough budget ($150K), key constraint
   (must happen over a weekend to avoid downtime).
2. **Planning** — scope statement defines exactly what's in scope (desks,
   IT infrastructure, signage) and out of scope (furniture replacement,
   which is a separate initiative); schedule sequences vendor selection →
   IT cutover → moving weekend → settle-in week; budget breaks the $150K
   into movers, IT contractors, signage, and a 10% contingency; risk
   register flags "moving company double-books the date" as a risk with a
   mitigation of booking 6 weeks early with a signed contract.
3. **Execution & Monitoring** — weekly status reports track vendor
   contracts signed, IT equipment ordered, and packing progress against the
   schedule baseline; when the signage vendor slips two weeks, that's
   caught in week 6's status check, not discovered on moving weekend.
4. **Closure** — the COO signs off that the office is fully operational;
   final vendor invoices are reconciled against the budget baseline; a
   30-minute retro captures that the moving weekend went smoothly but IT
   cutover took longer than planned because access badges weren't
   pre-provisioned — feeding directly into the next relocation this company
   does.

## Exercise

Pick a real or hypothetical project (it can be small — planning a
community event, launching an internal tool, renovating a room). For each
of the four phases, write one concrete sentence describing what the exit
criteria would be — i.e., what specific, checkable condition has to be true
before you'd consider that phase done and move to the next one. Then
identify which phase, if any, your project (or a past project you've been
part of) tends to shortchange, and why.
