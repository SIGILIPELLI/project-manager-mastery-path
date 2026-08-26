# 03 · Digital Transformation Programs

A digital transformation program is not a large IT project wearing a bigger
title — it's a program whose primary deliverable is organisational change,
where the technology is often the easier half. Programs in this category
fail overwhelmingly on adoption, not on delivery: the new system ships on
time, and eighteen months later half the organisation is still running the
old process in parallel because nobody made the old way actually stop
working.

## Why transformation programs are structurally different

| | Typical IT project | Digital transformation program |
|---|---|---|
| Primary deliverable | Working software | Changed ways of working, enabled by software |
| Success measure | System is live | Old process is retired and new one is the default |
| Main risk | Technical delivery | Adoption, change fatigue, competing incentives |
| Timeline | Fixed, bounded | Often multi-year, benefit-driven (Level 3, module 01) |
| Sponsor's job | Approve budget | Actively model and mandate the new behaviour |

## The transformation benefits realisation curve

Technology go-live and benefit realisation are not the same event, and the
gap between them is where most transformation programs lose executive
patience.

| Phase | What happens | Typical duration post-go-live |
|---|---|---|
| Go-live | System is technically available | Day 0 |
| Adoption trough | Productivity often *dips* below the old-process baseline as people relearn | 4–12 weeks |
| Parallel running | Some teams use old + new simultaneously "just in case" | 1–3 months if not actively shut down |
| Old process retirement | Old system/process access is formally removed | Must be a deliberate decision, not a drift |
| Benefit realisation | Measured gains appear | 3–12 months post-go-live, depending on benefit type |

The adoption trough is not a sign the program failed — it's an expected,
temporary productivity dip while people relearn a new way of working, and a
sponsor who panics and reverts at week 3 of the trough guarantees the
program never reaches realisation. The program's job is forecasting the
trough explicitly, in the plan, so it isn't mistaken for failure when it
arrives on schedule.

## Worked example: adoption curve with a forced cutover decision

A finance transformation program replaces a manual approval process with an
automated workflow. Three months post-go-live, 60% of approvals still go
through the old manual path in parallel.

| Option | Action | Trade-off |
|---|---|---|
| Continue parallel running indefinitely | Let usage migrate "naturally" | Never happens — data from comparable programs shows parallel systems plateau, they don't self-resolve; the old path stays a permanent crutch |
| Set a hard cutover date, communicated 6 weeks ahead | Old system access revoked on a fixed date | Short-term pain spike, but forces the adoption the parallel period was supposed to produce |
| Incentivise the new path | Recognition/targets tied to new-process usage | Slower, but lower-friction; often combined with a cutover date as a backstop |

The programs that actually retire the old process combine both of the last
two: a communicated deadline (removes the option to defer indefinitely) plus
incentives in the weeks before it (reduces the deadline's felt harshness).
A cutover date alone, with no support, produces a spike in help-desk tickets
and a credibility hit; incentives alone, with no deadline, produce the
indefinite-parallel outcome.

## Change management workstream (parallel to delivery)

| Workstream | Delivery-side owner | Change-side owner | Key artefact |
|---|---|---|---|
| Technical build | Program manager / engineering lead | — | Architecture, test plan |
| Communication | — | Change lead | Comms calendar, key messages by audience |
| Training | — | Change lead | Role-based training plan, completion tracking |
| Resistance management | — | Change lead + sponsor | Stakeholder resistance log (Level 3, module 07 patterns, applied at scale) |
| Incentive/mandate design | Sponsor | Change lead | Cutover plan, incentive structure |

Treating change management as a separate, adequately-resourced workstream —
not a communications afterthought added in the final sprint — is the single
structural decision that most correlates with transformation programs that
actually realise their benefits map.

## Measuring adoption, not just usage

| Metric | What it actually tells you | Common mistake |
|---|---|---|
| Login count | System is being opened | Doesn't mean the *process* changed — people log in and still do the old workaround |
| % of approvals through new workflow | True adoption of the new process | The metric that actually matters |
| Help-desk ticket volume trend | Whether friction is decreasing over time | Rising tickets in week 1–2 is normal; rising in month 3 is a real signal |
| Manager survey: "which process do you actually use day to day" | Self-reported reality, catches shadow processes | Only as honest as psychological safety allows — anonymise it |

## Exercise

A transformation program replacing a legacy CRM goes live on schedule. Three
months later, login counts to the new system are high, but sales reps are
reportedly still exporting data to spreadsheets to do their actual
forecasting work — a shadow process the login metric doesn't catch.

1. Identify which phase of the benefits realisation curve this program is
   actually in, and explain why login count alone would have masked the
   real problem.
2. Design one better adoption metric (using the "measuring adoption, not
   usage" table's logic) that would have caught the shadow spreadsheet
   process earlier.
3. Propose a cutover plan (deadline + incentive, per the worked example)
   to retire the shadow process, including what you'd communicate to
   sales reps and how far ahead of the deadline.
