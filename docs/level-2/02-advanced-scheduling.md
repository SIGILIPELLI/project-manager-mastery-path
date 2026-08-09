# 02 · Advanced Scheduling

Level 1 covered building a task list, sequencing it, and drawing a Gantt
chart. That gets you a schedule. It does not tell you **which tasks actually
control the end date**, how much slack the others really have, or what it
costs to finish sooner. This module covers the Critical Path Method (CPM),
the two kinds of float, PERT three-point estimation, schedule compression by
crashing and fast-tracking, and resource levelling. Every number below is
computed, so you can check the arithmetic yourself.

## The network diagram

CPM works on a **network** of activities linked by dependencies, not on a bar
chart. Here is the schedule used throughout this module — an office systems
rollout.

| ID | Activity | Duration (days) | Predecessors |
|---|---|---|---|
| A | Requirements sign-off | 5 | — |
| B | Solution design | 8 | A |
| C | Procure hardware | 12 | A |
| D | Build backend | 10 | B |
| E | Build frontend | 7 | B |
| F | Install hardware | 4 | C |
| G | Integration | 6 | D, E, F |
| H | User acceptance testing | 5 | G |
| I | Write training material | 3 | H |
| J | Data migration | 4 | H |
| K | Go-live | 2 | I, J |

Four dependency types exist; finish-to-start is the default and by far the
most common.

| Type | Meaning | Example |
|---|---|---|
| Finish-to-Start (FS) | B can't start until A finishes | Design after requirements |
| Start-to-Start (SS) | B can't start until A starts | Testing starts 3 days after coding starts |
| Finish-to-Finish (FF) | B can't finish until A finishes | Documentation finishes when the build finishes |
| Start-to-Finish (SF) | B can't finish until A starts | Old system retires once the new one runs |

**Lead** is negative lag — overlapping activities, such as starting testing 3
days before coding ends. **Lag** is enforced waiting time — concrete cures
for 7 days between pour and load. Both are properties of the *relationship*,
not of the activity.

## Forward pass, backward pass, float

The **forward pass** computes the earliest each activity can happen, moving
left to right:

- `ES` (early start) = the latest `EF` among all predecessors, or 0 if none
- `EF` (early finish) = `ES + duration`

The **backward pass** computes the latest each can happen without delaying
the project, moving right to left from the project duration:

- `LF` (late finish) = the earliest `LS` among all successors, or the project
  duration if none
- `LS` (late start) = `LF − duration`

Float then falls out of the difference:

- **Total float** `TF = LS − ES` — how long the activity can slip before the
  **project end date** moves.
- **Free float** `FF = (earliest ES of successors) − EF` — how long it can
  slip before **the next activity's** early start moves.

Running both passes over the table above gives:

| ID | Dur | ES | EF | LS | LF | Total float | Free float | Critical? |
|---|---|---|---|---|---|---|---|---|
| A | 5 | 0 | 5 | 0 | 5 | 0 | 0 | **Yes** |
| B | 8 | 5 | 13 | 5 | 13 | 0 | 0 | **Yes** |
| C | 12 | 5 | 17 | 7 | 19 | 2 | 0 | No |
| D | 10 | 13 | 23 | 13 | 23 | 0 | 0 | **Yes** |
| E | 7 | 13 | 20 | 16 | 23 | 3 | 3 | No |
| F | 4 | 17 | 21 | 19 | 23 | 2 | 2 | No |
| G | 6 | 23 | 29 | 23 | 29 | 0 | 0 | **Yes** |
| H | 5 | 29 | 34 | 29 | 34 | 0 | 0 | **Yes** |
| I | 3 | 34 | 37 | 35 | 38 | 1 | 1 | No |
| J | 4 | 34 | 38 | 34 | 38 | 0 | 0 | **Yes** |
| K | 2 | 38 | 40 | 38 | 40 | 0 | 0 | **Yes** |

**Critical path: A → B → D → G → H → J → K**, and
5 + 8 + 10 + 6 + 5 + 4 + 2 = **40 days**. The critical path is simply the
chain of zero-float activities — the longest path through the network. Delay
any one of them by a day and the project finishes a day later.

Activity **C is the reason both float types matter**. It has 2 days of total
float but **zero free float**. C can slip 2 days without moving go-live, but
it cannot slip even one day without pushing F's start. If you tell the
procurement manager "you have 2 days of slack" and they take it, the
installation crew's start date moves — and they may already have been booked.
Report free float to the person doing the work; report total float to the
sponsor.

!!! warning "Float belongs to the project, not to the activity owner"
    Total float is a shared buffer along a path. If C consumes all 2 days, F
    has none left. Three activity owners each "using their slack" on the same
    path will overrun the project even though none of them individually
    exceeded the float they were told about. Track float consumption on the
    *path*, not per activity.

## PERT: three-point estimation

Single-point durations hide uncertainty. PERT asks for three estimates per
activity and computes a **beta-weighted expected duration**:

```
te  = (O + 4M + P) / 6
sd  = (P − O) / 6
var = sd²
```

where `O` is optimistic, `M` most likely, and `P` pessimistic. Applying this
to the critical path activities:

| Act | O | M | P | `te` | σ | Variance |
|---|---|---|---|---|---|---|
| A | 3 | 5 | 13 | 6.00 | 1.667 | 2.778 |
| B | 5 | 8 | 11 | 8.00 | 1.000 | 1.000 |
| D | 7 | 9 | 17 | 10.00 | 1.667 | 2.778 |
| G | 4 | 6 | 8 | 6.00 | 0.667 | 0.444 |
| H | 4 | 5 | 6 | 5.00 | 0.333 | 0.111 |
| J | 3 | 4 | 5 | 4.00 | 0.333 | 0.111 |
| K | 1 | 2 | 3 | 2.00 | 0.333 | 0.111 |
| **Path** | | | | **41.00** | **2.708** | **7.333** |

Check A: (3 + 4×5 + 13) ÷ 6 = 36 ÷ 6 = 6.00. Its most likely duration is 5
days, but the pessimistic tail runs to 13, so the *expected* duration is 6.
That one skewed activity is why **the PERT path is 41 days while the
deterministic CPM path was 40**. Single-point estimates silently assume the
most likely case is the expected case, which is false whenever risk is
one-sided — and on real projects it nearly always is.

Path standard deviation is the square root of the **sum of the variances**,
not the sum of the standard deviations: √7.333 = **2.708 days**. That gives a
confidence range:

| Confidence | Calculation | Duration |
|---|---|---|
| 50% | 41.00 | 41.0 days |
| 84% (+1σ) | 41.00 + 2.708 | 43.7 days |
| 95% (+1.645σ) | 41.00 + 1.645 × 2.708 | 45.5 days |
| 97.7% (+2σ) | 41.00 + 2 × 2.708 | 46.4 days |

It also answers the sponsor's real question: **what is the chance of hitting
the original 40-day date?** z = (40 − 41.00) ÷ 2.708 = **−0.369**, which on
the normal curve is about **36%**. Committing to 40 days is committing to a
date you will miss roughly two times in three. Committing to 46 days is a
promise you keep 97 times in 100. Choosing between those is a business
decision — but it has to be made with the number visible.

## Compressing the schedule

When 40 days is too long, there are exactly two legitimate techniques.

| Technique | Method | Adds | Does not add |
|---|---|---|---|
| **Crashing** | Add resources to critical activities | Cost | Rework risk (usually) |
| **Fast-tracking** | Overlap activities normally done in sequence | Rework risk | Direct cost |

Crashing decisions are driven by the **cost slope** — the cost per day saved:

```
Cost slope = (Crash cost − Normal cost) / (Normal duration − Crash duration)
```

| Act | Normal dur | Crash dur | Max days | Normal cost | Crash cost | Cost slope |
|---|---|---|---|---|---|---|
| B | 8 | 6 | 2 | $40,000 | $44,000 | **$2,000/day** |
| D | 10 | 7 | 3 | $90,000 | $103,500 | $4,500/day |
| G | 6 | 5 | 1 | $30,000 | $36,000 | $6,000/day |
| H | 5 | 4 | 1 | $25,000 | $26,200 | **$1,200/day** |
| J | 4 | 3 | 1 | $20,000 | $28,000 | $8,000/day |

Check H: ($26,200 − $25,000) ÷ (5 − 4) = $1,200 ÷ 1 = $1,200 per day.

**Worked example — compress 40 days to 37 days at least cost.** Always crash
the cheapest activity *that is on the critical path*, one day at a time, and
re-run the network after each step.

| Step | Crash | Cost | New duration | Critical path after the step |
|---|---|---|---|---|
| 1 | H by 1 day | $1,200 | 39 days | A-B-D-G-H-J-K (unchanged) |
| 2 | B by 1 day | $2,000 | 38 days | A-B-D-G-H-J-K (unchanged) |
| 3 | B by 1 day | $2,000 | 37 days | A-B-D-G-H-J-K **and** A-C-F-G-H-J-K |
| | **Total** | **$5,200** | **37 days** | two parallel critical paths |

Three days bought for **$5,200**, an average of $1,733 per day. Note what
happened at step 3: crashing B twice consumed all of C's 2 days of total
float, so the procurement path became critical as well. **Any further
compression now requires shortening both paths at once** — either an activity
they share (G, H, J or K) or one activity on each. Crashing B a third time
would buy nothing at all, because the C-F path would hold the project at 37
days regardless.

That is the single most common crashing mistake: someone buys another day of
the activity that worked last time, pays for it, and the end date does not
move. Recompute the network after every compression decision.

Fast-tracking the same schedule might start integration (G) when the backend
(D) is 80% complete rather than 100%. That saves days at no direct cost, but
if the backend interface changes in its final 20%, the integration work is
redone — and rework late in a schedule costs far more than the crash would
have. Fast-track only where the predecessor's remaining work is unlikely to
invalidate the successor's.

## Resource levelling and smoothing

CPM assumes infinite resources. Reality does not. Suppose activities D
(backend) and E (frontend) both need the same senior developer, and they
overlap from day 13 to day 20.

| Approach | What it does | Effect on the end date |
|---|---|---|
| **Resource smoothing** | Shifts activities within their float only | **Never extends** the project |
| **Resource levelling** | Delays activities to respect a hard resource limit | **May extend** the project |

E has 3 days of total float, so smoothing is available: delay E to start on
day 16 instead of 13, finishing on day 23 — exactly its late finish, still
not delaying G. But that only staggers the overlap; the developer would still
be on both D and E from day 16 to 23. If one person genuinely cannot do both,
levelling is required: run E after D, from day 23 to day 30, which pushes G,
H, J and K and extends the project to **47 days**.

That number is the whole point of this section. The 40-day critical path was
never real if one person had to do both D and E. Always level against
actual named resources before publishing a date — a resource-infeasible
critical path is not a plan, it is a wish.

## Exercise

Build and analyse a schedule of your own with at least 10 activities and at
least two parallel paths that merge.

1. Write the activity table with durations and predecessors, then draw the
   network.
2. Run the forward and backward pass by hand. Produce the full ES/EF/LS/LF
   table, compute **total float and free float** for every activity, and
   identify the critical path. Confirm the critical path durations sum to
   your project duration.
3. Find one activity where total float and free float differ, and explain in
   one sentence what that difference means to the person doing the work.
4. Add optimistic and pessimistic estimates for your critical path
   activities. Compute `te` and variance for each, then the path `te`, path
   variance and path σ. State the 50%, 84% and 95% confidence durations, and
   compute the probability of hitting your original deterministic date.
5. Assign a cost slope to at least four activities, then compress your
   schedule by 3 days at minimum cost. Show the step-by-step table and
   **re-identify the critical path after each step**, stating explicitly if
   and when a second path becomes critical.
6. Finally, assume two of your parallel activities need the same person.
   Decide whether smoothing is sufficient or levelling is required, and give
   the resulting end date.
