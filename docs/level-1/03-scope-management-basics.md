# 03 · Scope Management Basics

**Scope** is the sum of all the work — and only the work — required to
deliver a project's objectives. Scope management is the discipline of
defining that boundary clearly enough that everyone (sponsor, team,
stakeholders) agrees on what "done" means, and then protecting that boundary
as the project runs, so it doesn't quietly expand without a corresponding
adjustment to schedule, budget, or quality. Nearly every project failure
story you've heard — "it took twice as long as planned," "it cost way more
than budgeted" — traces back, at least in part, to scope that wasn't defined
tightly enough up front or wasn't protected once work began.

## Defining scope: the scope statement

Where the [charter](02-project-lifecycle-basics.md) states *why* a project
exists at a high level, the **scope statement** states, in detail, *what*
will and won't be delivered. A solid scope statement includes:

| Element | Purpose |
|---|---|
| Product scope description | What the deliverable itself is and does |
| Deliverables list | The specific, tangible outputs the project produces |
| Acceptance criteria | The specific conditions each deliverable must meet to be accepted |
| Exclusions | Explicitly what is *not* included — often the most valuable line in the whole document |
| Constraints | Fixed limits the project must work within (budget, deadline, regulation) |
| Assumptions | Things being taken as true without proof, which if wrong would change the plan |

The **exclusions** section deserves special attention: most scope disputes
happen not because something was never discussed, but because it was
discussed informally and everyone walked away with a different
understanding of whether it was "in." Writing "not included: furniture
replacement, cabling for floors 3-5 (handled by a separate project)"
explicitly closes that gap before it becomes a fight in month three.

## Breaking scope down: the Work Breakdown Structure (WBS)

A **Work Breakdown Structure** decomposes the total scope into progressively
smaller, more manageable pieces, until you reach a level of detail — called
a **work package** — small enough to estimate, assign, and track reliably
(a common rule of thumb is the "8/80 rule": no work package should take less
than 8 hours or more than 80 hours of effort). A WBS is typically drawn as a
hierarchy or shown as an indented outline:

| Level | Example (website redesign project) |
|---|---|
| 1.0 Project | Company Website Redesign |
| 1.1 Deliverable | Design |
| 1.1.1 Work package | Wireframes |
| 1.1.2 Work package | Visual design mockups |
| 1.2 Deliverable | Development |
| 1.2.1 Work package | Front-end build |
| 1.2.2 Work package | CMS integration |
| 1.3 Deliverable | Content |
| 1.3.1 Work package | Copywriting |
| 1.3.2 Work package | Photography |
| 1.4 Deliverable | Launch |
| 1.4.1 Work package | QA & testing |
| 1.4.2 Work package | DNS cutover |

The WBS becomes the backbone for everything downstream: each work package
gets an estimate and a schedule position (Module 4), a cost (Module 5), and
an owner. If a piece of work doesn't appear anywhere on the WBS, it's
either genuinely out of scope, or it's been forgotten — and finding out
which, before execution starts, is exactly the point of building one.

## Scope creep and how to control it

**Scope creep** is the uncontrolled expansion of scope without corresponding
adjustments to time, cost, or resources — the single most common cause of
projects running over budget and over schedule. It rarely arrives as one
dramatic addition; it accumulates from many small, individually reasonable-
sounding requests: "can we just also add a search bar," "while you're in
there, can it also export to PDF." Each one seems minor in isolation, which
is exactly why they're dangerous in aggregate.

The defense against scope creep is not saying "no" to every request — it's
having a **change control process** that makes the trade-off visible before
saying yes:

1. Request is submitted (in writing, even briefly) with what's being asked
   for.
2. PM assesses impact on schedule, budget, and quality — this is the step
   scope creep skips.
3. Impact and options are presented to the sponsor/change control board: do
   this and extend the deadline, do this and drop something else, or don't
   do this now.
4. Decision is documented, and if approved, the scope statement, schedule,
   and budget baselines are formally updated to reflect it.

This turns "can we just also add..." from a free add-on into a visible
trade-off decision — which is very often enough, by itself, to make people
reconsider whether the addition is actually worth it.

## A worked example: a scope statement with a costly missing exclusion

A marketing team commissions a project to "build a customer feedback
survey tool." The verbal brief mentions building the survey form and a
results dashboard. Two different scope statements might result:

**Weak version** — "Build a tool to collect and display customer feedback."
No exclusions listed. Three weeks into execution, the requester assumes
the tool naturally includes automated email reminders to non-responders,
because "collecting feedback" implies following up. The PM had never
scoped or estimated that feature. This becomes a scope-creep argument
precisely because it was never made explicit either way.

**Strong version** — Deliverables: (1) web-based survey form with five
question types, (2) results dashboard with filter-by-date and export-to-CSV.
Exclusions: automated reminder emails to non-responders (out of scope for
this phase — noted as a candidate for a future project), integration with
the CRM (out of scope), mobile app version (out of scope). Assumptions:
survey responses stored for 12 months only. With this version, when the
"what about reminder emails" question comes up, it's a two-second answer —
"explicitly excluded, here's why, want to raise it as a change request?" —
instead of a dispute about what was implicitly promised.

## Exercise

Write a one-page scope statement for a project of your choosing (examples:
"organize a 50-person conference," "build a personal budgeting spreadsheet
system," "launch a small online store"). Include all six elements from the
table above — product scope, deliverables, acceptance criteria, exclusions,
constraints, and assumptions — with at least three specific items in the
exclusions section. Then sketch a two-level WBS (deliverables, then work
packages under each) for the same project.
