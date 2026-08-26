# 08 · Global/Distributed Team Project Management

A project team spread across four time zones isn't a co-located team with a
video call added — the coordination mechanisms that work face-to-face
(overhearing a hallway conversation, reading body language in a status
meeting, a quick tap on the shoulder) don't degrade gracefully across
distance, they disappear, and have to be deliberately replaced with
something else.

## What actually breaks with distance

| Co-located mechanism | What it silently provides | Distributed replacement needed |
|---|---|---|
| Overhearing nearby conversations | Ambient awareness of related work | Shared, visible work-tracking tool everyone actually checks |
| Hallway/water-cooler decisions | Fast informal alignment | An explicit norm: decisions made informally must be written down within the day, or they don't count |
| Reading a room in a meeting | Sensing unspoken disagreement | Deliberately asking quieter/remote voices directly, not just the loudest in-room voice |
| Same-timezone "quick call" | Fast clarification | Async-first default; synchronous only for genuinely time-sensitive items |

Teams that fail at distributed work usually aren't missing tools — they're
missing the deliberate replacement for what the tools can't provide on
their own, like a written norm that a decision isn't final until it's
documented somewhere everyone can see it.

## Time zone overlap planning

| Team | Location | Working hours (local) | Working hours (UTC) |
|---|---|---|---|
| Product | San Francisco | 9am–5pm PT | 17:00–01:00 UTC |
| Engineering (core) | Bengaluru | 9am–6pm IST | 03:30–12:30 UTC |
| Engineering (secondary) | Warsaw | 9am–5pm CET | 08:00–16:00 UTC |
| QA | Manila | 9am–6pm PHT | 01:00–10:00 UTC |

```
python3 -c "
sf = set(range(17,24)) | set(range(0,1))  # 17:00-01:00 UTC wraps midnight
blr = set(range(4,13))  # approx 03:30-12:30 rounded
waw = set(range(8,16))
mnl = set(range(1,10))
overlap_all = sf & blr & waw & mnl
print(sorted(overlap_all))
"
```
Result: **empty set** — there is no hour where all four teams are
simultaneously working. This is the honest starting fact a distributed
program has to confront before scheduling a single meeting: any "all-hands"
sync is asking someone to attend outside their working hours, every time,
without exception.

The actual overlap that exists: Bengaluru and Warsaw share roughly 08:00–
12:30 UTC; Bengaluru and Manila share roughly 04:00–10:00 UTC. The practical
answer is a **rotating core-hours meeting** — no single fixed time is fair
to everyone, so the meeting time rotates on a schedule (e.g., alternating
which team takes the inconvenient slot) rather than permanently
disadvantaging whichever team is furthest from San Francisco.

## Designing for asynchronous-first coordination

| Practice | What it replaces | Discipline required |
|---|---|---|
| Written decision log, updated same-day | The hallway conversation that used to finalize a decision | Someone owns writing it down — not "whoever remembers" |
| Recorded async updates (video or written) instead of a live status meeting | The daily standup no timezone set fully attends | Genuine brevity — a rambling 10-minute recording is worse than a live meeting |
| Explicit response-time SLAs by channel (e.g., "urgent" Slack = 2 hours, ticket = 1 business day) | The implicit "someone will notice and respond" of a shared office | Written and actually honored, or trust in the async system collapses |
| "Decision owner" named on every open question in the tracker | Someone catching a stalled decision in a hallway | A visible field in the tracker — an unowned question with no update for a week is a process failure, not bad luck |

## Cultural and working-norm differences

Distance amplifies communication-style mismatches that co-location often
papers over:

| Dimension | Risk if unmanaged | Mitigation |
|---|---|---|
| Direct vs. indirect disagreement styles | A team member says "this might be a small concern" meaning "this is a serious blocker," and it's read as minor | Explicitly ask "on a scale of blocker to nice-to-fix, where does this sit?" rather than inferring tone |
| Hierarchy and speaking up to seniority | Junior distributed team members stay silent in mixed-seniority calls | PM explicitly solicits input by name, not just "any concerns?" to the room |
| Holiday/working-day calendars | A deadline lands on a regional holiday nobody in the planning meeting knew about | Maintain one shared calendar of all sites' holidays, checked during planning, not discovered at the deadline |

## Worked example: a distributed RACI adjustment

A standard RACI (Level 1) assumes the Accountable person can be reached
quickly to unblock the Responsible person. Across time zones with minimal
overlap, that assumption breaks:

| Task | R | A | Standard risk | Distributed adjustment |
|---|---|---|---|---|
| Approve architecture change | Bengaluru engineer | SF-based architect | Bengaluru finishes their day before SF starts — a same-day approval is impossible | Pre-delegate a same-timezone backup approver with clear boundaries on what they can approve without escalating |

## Exercise

You run a project with engineers in Austin (UTC−6) and Tokyo (UTC+9), with
no team member overlap window during either team's normal working hours.

1. Calculate the UTC working-hour ranges for a 9am–5pm local day in both
   cities and confirm with `python3` whether any overlap exists.
2. Propose one async-first coordination practice (from the table above)
   specifically suited to this zero-overlap pair, and describe what
   discipline it requires to actually work.
3. Adjust a RACI row for a task where the Responsible person is in Austin
   and the Accountable approver is in Tokyo, following the worked
   example's pattern.
