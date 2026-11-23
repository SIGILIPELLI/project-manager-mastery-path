---
title: "Project Manager Cheat Sheet: Quick Reference, Beginner to Advanced"
description: "A free Project Manager cheat sheet: 40 quick-reference tables from every level of the Project Manager Mastery Path, each linked to its full lesson."
---

# Project Manager Cheat Sheet

Quick-reference tables from **40 lessons** of the free Project Manager Mastery Path, in course order from beginner to advanced. Each section links to the full lesson with explanations and runnable examples.

## Level 1 · Entry

### [01 · What Is Project Management?](level-1/01-what-is-project-management.md)

*What a project manager actually does*

| Activity | Plain-language version |
|---|---|
| Define | What are we building, and what does "done" look like? |
| Plan | Who does what, by when, for how much? |
| Execute | Get the work done, coordinate the people doing it |
| Monitor & Control | Is it still on scope, on schedule, on budget? Course-correct early |
| Close | Confirm it's actually done, capture lessons, release the team |

### [02 · Project Lifecycle Basics](level-1/02-project-lifecycle-basics.md)

*The four phases*

| Phase | Central question | Typical deliverables | Exit criteria |
|---|---|---|---|
| Initiation | Should we do this, and are we authorized to? | Project charter, high-level business case | Charter signed by a sponsor |
| Planning | How exactly will we deliver it? | Scope statement, schedule, budget, risk register, communication plan | Baselines approved by the sponsor/stakeholders |
| Execution & Monitoring/Controlling | Are we building it, and are we still on track? | Status reports, change requests, updated RAID log | Deliverables accepted, scope substantially complete |
| Closure | Is it actually done, and what did we learn? | Acceptance sign-off, lessons learned, final report | Formal sign-off, resources released |

### [03 · Scope Management Basics](level-1/03-scope-management-basics.md)

*Defining scope: the scope statement*

| Element | Purpose |
|---|---|
| Product scope description | What the deliverable itself is and does |
| Deliverables list | The specific, tangible outputs the project produces |
| Acceptance criteria | The specific conditions each deliverable must meet to be accepted |
| Exclusions | Explicitly what is *not* included — often the most valuable line in the whole document |
| Constraints | Fixed limits the project must work within (budget, deadline, regulation) |
| Assumptions | Things being taken as true without proof, which if wrong would change the plan |

### [04 · Scheduling Basics](level-1/04-scheduling-basics.md)

*From WBS to schedule: durations and dependencies*

| Dependency type | Meaning | Example |
|---|---|---|
| Finish-to-Start (FS) | Task B can't start until Task A finishes | Can't paint a wall until drywall is up |
| Start-to-Start (SS) | Task B can't start until Task A starts | QA test-writing can start once development starts |
| Finish-to-Finish (FF) | Task B can't finish until Task A finishes | Final proofreading can't finish until final edits finish |
| Start-to-Finish (SF) | Task B can't finish until Task A starts | Rare — e.g., old system can't be shut down until new system starts running |

### [05 · Budget &amp; Cost Basics](level-1/05-budget-cost-basics.md)

*Estimating techniques*

| Technique | How it works | Accuracy | When to use it |
|---|---|---|---|
| Analogous estimating | Base the estimate on a similar past project's actual cost | Low (±25-75%) | Early on, when little detail is known yet |
| Parametric estimating | Use a rate × quantity formula (e.g., $150/hour × estimated hours) | Medium | Once you know quantities but not full detail |
| Bottom-up estimating | Estimate every work package individually, then sum them | High (±5-10%) | Once the WBS ([Module 3](level-1/03-scope-management-basics.md)) is detailed |
| Three-point estimating | Combine optimistic, most-likely, and pessimistic estimates | Medium-high | When there's real uncertainty on a given task |

### [06 · Risk Management Basics](level-1/06-risk-management-basics.md)

*Identifying risks*

| Technique | How it works |
|---|---|
| Brainstorming | Team session listing anything that could go wrong (or right) |
| Checklist review | Compare against a standing list of risks common to this type of project |
| Assumption analysis | Examine every assumption from the scope statement — if it's wrong, what happens? |
| Expert judgment | Ask people who've run similar projects what bit them |
| SWOT analysis | Strengths/Weaknesses/Opportunities/Threats, viewed from the project's angle |

### [07 · Stakeholder Management Basics](level-1/07-stakeholder-management-basics.md)

*Identifying stakeholders*

| Category | Examples |
|---|---|
| Internal, direct | Sponsor, project team, functional managers who supply resources |
| Internal, indirect | Adjacent teams affected by the outcome, compliance/legal/finance reviewers |
| External | Customers, end users, vendors, contractors |
| External, less obvious | Regulators, industry groups, the media, a community group affected by a physical project |

### [08 · Communication Plans](level-1/08-communication-plans.md)

*The elements of a communication plan*

| Element | Question it answers |
|---|---|
| Audience | Who receives this communication? |
| Content | What information does it contain? |
| Format | Email, live meeting, dashboard, written report? |
| Frequency | How often — daily, weekly, at milestones? |
| Owner | Who is responsible for producing and sending it? |

### [09 · Tools Overview (Jira, MS Project, Asana)](level-1/09-tools-overview.md)

*The three tools, at a glance*

| Tool | Best fit | Core model | Weakest fit |
|---|---|---|---|
| **Jira** | Software/agile teams | Issues/tickets moving through a workflow (backlog → in progress → done) | Non-technical stakeholders often find it cluttered |
| **Microsoft Project** | Traditional, schedule-heavy predictive projects | Gantt-chart-first, with deep critical-path/resource-leveling support | Overkill and steep learning curve for small or agile teams |
| **Asana** | General-purpose cross-functional teams | Tasks/projects with flexible views (list, board, timeline, calendar) | Less depth than Jira for engineering-specific workflows, less depth than MS Project for complex scheduling math |

### [10 · Project — Full Project Charter &amp; Schedule](level-1/10-project-charter-schedule.md)

*Project Charter*

| Element | Content |
|---|---|
| Purpose | Increase new customer acquisition through existing customer referrals, at lower cost-per-acquisition than paid marketing |
| Objectives | Launch a functioning referral portal within 10 weeks; achieve at least 50 completed referrals in the first quarter post-launch |
| Sponsor | VP of Marketing |
| Key stakeholders | Marketing, Engineering, Billing/Finance, Customer Support |
| High-level budget | $45,000 |
| High-level timeline | 10 weeks |
| Assumptions | Existing billing system has an API the portal can integrate with |
| Constraints | Must not require any change to the core billing system's data model |
| Assigned PM | [You] |

## Level 2 · Intermediate

### [01 · Agile Project Management](level-2/01-agile-project-management.md)

*When agile fits, and when it doesn't*

| Condition | Predictive fits | Agile fits |
|---|---|---|
| Requirements clarity | Well understood, stable | Emerging, expected to change |
| Feedback loop | Value only visible at the end | Partial product is usable and testable early |
| Regulatory/contract constraint | Fixed scope contractually mandated | Scope negotiable within a fixed budget |
| Cost of change late | Very high (physical build, hardware) | Low (software, content, service design) |
| Stakeholder availability | Sign-off at gates | Continuous, weekly involvement |

### [02 · Advanced Scheduling](level-2/02-advanced-scheduling.md)

*The network diagram*

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

### [03 · Earned Value Management Basics](level-2/03-earned-value-management.md)

*The three base measures*

| Term | Full name | Plain meaning |
|---|---|---|
| **PV** | Planned Value | Budgeted cost of the work **scheduled** to be done by now |
| **EV** | Earned Value | Budgeted cost of the work **actually completed** by now |
| **AC** | Actual Cost | What was **actually spent** to complete that work |
| **BAC** | Budget at Completion | The total approved budget for the whole project |

### [04 · Risk Management Deep Dive](level-2/04-risk-management-deep-dive.md)

*Writing a risk that can be managed*

| Category | Prompts to generate risks |
|---|---|
| Technical | Unproven technology, integration complexity, performance limits |
| External | Vendors, regulation, market, weather, geopolitics |
| Organisational | Funding stability, competing priorities, key person dependency |
| Project management | Estimating accuracy, poor requirements, unrealistic baseline |

### [05 · Procurement Basics](level-2/05-procurement-basics.md)

*The procurement lifecycle*

| Phase | Key activity | Output |
|---|---|---|
| Plan | Make-or-buy analysis, choose contract type | Procurement management plan |
| Conduct | Issue solicitation, evaluate, negotiate, award | Signed contract, SOW |
| Control | Manage performance, changes, payments, disputes | Performance reports, change orders |
| Close | Verify deliverables, settle claims, release retention | Closure certificate, lessons learned |

### [06 · Quality Management Basics](level-2/06-quality-management-basics.md)

*Three processes, three different questions*

| Process | Question it answers | Focus | Typical output |
|---|---|---|---|
| **Plan Quality** | What does "good" mean here, and how will we know? | Standards and metrics | Quality management plan, checklists |
| **Manage Quality** (assurance) | Is our **process** capable of producing good work? | Process audit | Process improvements, audit findings |
| **Control Quality** (control) | Is this specific **deliverable** acceptable? | Inspecting outputs | Verified deliverables, defect log |

### [07 · Change Management for Projects](level-2/07-change-management.md)

*Part 1 — Change control*

| Term | What it is | Root cause |
|---|---|---|
| **Scope creep** | Uncontrolled additions from stakeholders, unassessed | No baseline, or no change process |
| **Gold plating** | The *team* adds unrequested polish | Team believes it knows better than the spec |

### [08 · Team Management &amp; Conflict Resolution](level-2/08-team-management-conflict.md)

*The authority gap*

| Structure | PM authority | Team reports to | Practical consequence |
|---|---|---|---|
| Functional | Little or none | Functional manager | You negotiate for every hour; escalation goes through their boss |
| Weak matrix | Limited | Functional manager | You coordinate; you cannot set priorities |
| Balanced matrix | Shared | Both | Constant dual-priority conflict; needs explicit agreements |
| Strong matrix | High | PM (mostly) | You set work priorities; manager still owns career and pay |
| Projectised | Almost total | PM | Full control; you also own the post-project redeployment problem |

### [09 · Reporting &amp; Dashboards](level-2/09-reporting-dashboards.md)

*Start with the decision, not the data*

| Audience | Decision they make | Cadence | Depth | Format |
|---|---|---|---|---|
| Delivery team | What do I work on next; what is blocked | Daily | Task level | Board + stand-up |
| Project manager | Where to intervene this week | Weekly | Work package | Full dashboard |
| Sponsor | Approve changes, remove obstacles, fund | Fortnightly | Milestone + EVM | 1 page + exceptions |
| Steering committee | Continue / adjust / stop; approve major change | Monthly | Objectives + risk | 1 page + decision log |
| Portfolio office | Compare against other projects | Monthly | Standard indices only | Automated feed |

### [10 · Project — Agile Plan with Sprint Schedule](level-2/10-project-agile-sprint-plan.md)

*The worked project*

| Attribute | Value |
|---|---|
| Project | MemberHub — customer self-service portal (replaces phone-only servicing) |
| Sponsor | Director of Customer Operations |
| Delivery model | Scrum, 2-week sprints, 5 sprints planned (10 weeks / 50 working days) |
| Team | 6 people: PO, Scrum Master, 3 developers, 1 tester |
| Backlog at baseline | 200 story points, estimated by planning poker |
| Cost baseline (BAC) | $200,000 — a flat team burn of $40,000 per sprint |
| Derived rate | $200,000 ÷ 200 points = **$1,000 per story point** |
| Contingency reserve | $52,000 (sized in the risk register below) |
| Management reserve | $20,000, sponsor-controlled |
| Total funding envelope | $272,000 |

## Level 3 · Advanced

### [01 · Program Management](level-3/01-program-management.md)

*Project vs. program vs. portfolio*

| | Project | Program | Portfolio |
|---|---|---|---|
| Unit of work | Deliverable | Set of related deliverables | Set of initiatives (may be unrelated) |
| Success measure | On time/budget/scope | Benefits realised | Strategic alignment, ROI mix |
| Time horizon | Fixed end date | Often rolling, benefit-driven | Continuous |
| Manager cares about | The plan | The plans, and the seams between them | The mix and the trade-offs |
| Typical artefact | Project charter | Program roadmap + benefits map | Portfolio scoring model |

### [02 · Portfolio Management Basics](level-3/02-portfolio-management-basics.md)

*Portfolio vs. program vs. project (recap)*

| | Project | Program | Portfolio |
|---|---|---|---|
| Question answered | How do we deliver this? | How do these related things add up to a benefit? | Which things should we fund? |
| Scope | Fixed | Related set | Organisation-wide, may be unrelated |
| Owner | Project manager | Program manager | Portfolio manager / PMO / executive committee |

### [03 · Advanced Risk &amp; Issue Management](level-3/03-advanced-risk-issue-management.md)

*Qualitative vs. quantitative risk analysis*

| | Qualitative | Quantitative |
|---|---|---|
| Output | Probability × Impact score, heat map | Expected monetary value, contingency reserve |
| Use | Fast triage of a long list | Justifying reserve, comparing response options in dollars |
| Effort | Low | Higher — needs estimates or simulation |
| When | Every risk, every review | Top-tier risks, or whole-project reserve sizing |

### [04 · Vendor &amp; Contract Management](level-3/04-vendor-contract-management.md)

*Contract types and where the risk sits*

| Contract type | How payment works | Risk sits with | Best for |
|---|---|---|---|
| Fixed-price (FP) | One agreed total for defined scope | Vendor (they eat cost overruns) | Well-defined, stable scope |
| Time & materials (T&M) | Pay for hours + materials actually used | Buyer (you eat overruns) | Uncertain or evolving scope |
| Cost-plus-fixed-fee (CPFF) | Costs reimbursed + fixed fee | Buyer, with vendor's margin protected | R&D, scope genuinely unknown upfront |
| Fixed-price-incentive-fee (FPIF) | Fixed price + bonus/penalty vs. a target | Shared, weighted by the incentive formula | Well-defined scope where performance matters |

### [05 · PMO Fundamentals](level-3/05-pmo-fundamentals.md)

*Three PMO types*

| Type | Authority level | Typical role | Risk if overdone |
|---|---|---|---|
| **Supportive** | Low — advisory only | Templates, training, a repository of lessons learned | Ignored; no real influence |
| **Controlling** | Medium — requires compliance | Enforces methodology, governance gates, mandatory reporting | Bureaucratic drag if gates outnumber the value they add |
| **Directive** | High — PMs report into the PMO | PMO directly manages projects; PMs are PMO staff assigned out | Can become a bottleneck; local context gets lost |

### [06 · Scaling Agile (SAFe, LeSS)](level-3/06-scaling-agile.md)

*Do you actually need to scale?*

| Symptom | Root cause | Right response |
|---|---|---|
| Teams keep discovering shared dependencies late | No cross-team visibility mechanism | Add a lightweight sync (Scrum of Scrums), not a full framework |
| Teams disagree on shared architecture | No shared technical governance | Add a Chief Engineer / architecture guild role |
| Releases are blocked because teams finish at different times | No shared cadence | Align sprint length and release train dates |
| Leadership can't see aggregate progress toward one goal | No program-level backlog | Add a program backlog and PI-level planning |

### [07 · Advanced Stakeholder Management](level-3/07-advanced-stakeholder-management.md)

*The power/interest grid (recap and extension)*

| | Low interest | High interest |
|---|---|---|
| **High power** | Keep satisfied | Manage closely |
| **Low power** | Monitor | Keep informed |

### [08 · Project Recovery](level-3/08-project-recovery.md)

*Recognising a project needs recovery, not just correction*

| Signal | Normal variance | Recovery territory |
|---|---|---|
| CPI/SPI | 0.90–1.00, recovering | Below 0.80, worsening for 2+ periods |
| Team morale | Normal sprint fatigue | Attrition risk, visible disengagement |
| Stakeholder trust | Occasional pushback | Sponsor has stopped believing status reports |
| Scope | Managed change requests | Scope has silently grown 30%+ with no rebaseline |
| Risk register | Actively used | Abandoned — team has stopped logging because nothing gets actioned |

### [09 · Advanced Metrics (EVM Deep Dive &amp; Forecasting)](level-3/09-advanced-metrics.md)

*The complete EVM formula reference*

| Metric | Formula | Meaning |
|---|---|---|
| PV (Planned Value) | Budgeted cost of work scheduled | What you planned to have spent by now |
| EV (Earned Value) | Budgeted cost of work actually performed | What the completed work is "worth" |
| AC (Actual Cost) | Actual cost of work performed | What you actually spent |
| CV (Cost Variance) | EV − AC | Positive = under budget |
| SV (Schedule Variance) | EV − PV | Positive = ahead of schedule |
| CPI (Cost Performance Index) | EV / AC | >1 = efficient spending |
| SPI (Schedule Performance Index) | EV / PV | >1 = ahead of schedule |
| BAC (Budget at Completion) | Total planned budget | The original target |
| EAC (Estimate at Completion) | See three methods below | Projected final cost |
| ETC (Estimate to Complete) | EAC − AC | Projected remaining cost |
| VAC (Variance at Completion) | BAC − EAC | Projected final over/under |
| TCPI (To-Complete Performance Index) | (BAC − EV) / (BAC − AC) | CPI required on remaining work to hit BAC |

### [10 · Project — Program Plan for 3 Related Projects](level-3/10-project-program-plan.md)

*Step 1 — Benefits map*

| Benefit | Target | Owner | Contributing projects |
|---|---|---|---|
| Increase repeat purchase rate | +8 percentage points within 2 quarters of launch | VP Marketing | Loyalty platform, Marketing launch |
| Reduce checkout friction for enrolled members | Under 5 extra seconds at POS | Head of Retail Ops | POS integration |
| Grow email-marketable customer base | +50,000 opted-in customers | VP Marketing | Marketing launch |

## Level 4 · Master

### [01 · Leading PMOs](level-4/01-leading-pmos.md)

*The PMO leader's actual scorecard*

| PMO metric | What it should move | How you'd know it worked |
|---|---|---|
| Portfolio-level forecast accuracy | Fewer surprise overruns reaching the executive team | Variance between quarterly forecast and actual shrinks over 3–4 quarters |
| Time-to-decision on cross-project conflicts | Faster resource conflict resolution | Median days from conflict raised to resolved drops |
| Project recovery rate | Fewer projects reaching Level 3's recovery territory (module 08) unnoticed | Number of projects caught at Amber before they hit Red rises |
| Executive trust proxy | Whether leadership uses the PMO dashboard to make real decisions, or works around it | Direct observation — are decisions made in the room referencing your numbers? |

### [02 · Enterprise Portfolio Management](level-4/02-enterprise-portfolio-management.md)

*The enterprise portfolio hierarchy*

| Level | Scope | Owner | Decision made |
|---|---|---|---|
| Enterprise portfolio | All investment across the company | Executive committee / CFO | How much capital goes to each business unit's portfolio |
| Business unit portfolio | One BU's initiatives | BU portfolio board | Which of the BU's own candidate projects get funded |
| Program | Related projects within a BU | Program manager | Sequencing and cross-project trade-offs |
| Project | Single deliverable | Project manager | Execution |

### [03 · Digital Transformation Programs](level-4/03-digital-transformation-programs.md)

*Why transformation programs are structurally different*

| | Typical IT project | Digital transformation program |
|---|---|---|
| Primary deliverable | Working software | Changed ways of working, enabled by software |
| Success measure | System is live | Old process is retired and new one is the default |
| Main risk | Technical delivery | Adoption, change fatigue, competing incentives |
| Timeline | Fixed, bounded | Often multi-year, benefit-driven (Level 3, module 01) |
| Sponsor's job | Approve budget | Actively model and mandate the new behaviour |

### [04 · Crisis &amp; Turnaround Project Leadership](level-4/04-crisis-turnaround-leadership.md)

*Recovery vs. crisis — different clocks*

| | Standard recovery (L3, module 08) | Crisis leadership |
|---|---|---|
| Timeframe to first action | Days to weeks | Hours |
| Primary tool | Root cause analysis, rebaseline | Triage, containment, communication |
| Decision style | Consultative, data-driven | Directive, best-available-information |
| Communication cadence | Weekly status | Hourly or continuous until stabilised |
| Success in the moment | A credible recovery plan | Damage contained, trust that someone is in control |

### [05 · Executive Reporting &amp; Governance](level-4/05-executive-reporting-governance.md)

*The exception report principle*

| Project | Status | Executive attention needed? |
|---|---|---|
| Platform migration | Green, on track | No — one line: "On track, no action needed" |
| Vendor integration | Amber, vendor SLA breach | **Yes** — needs a decision on whether to invoke the penalty clause |
| Mobile relaunch | Green, ahead of schedule | No — one line |
| Compliance update | Red, blocked on legal sign-off | **Yes** — needs an escalation to unblock legal |

### [06 · Building PM Culture &amp; Capability](level-4/06-building-pm-culture-capability.md)

*A PM competency framework*

| Competency | Level 1 (Associate) | Level 2 (PM) | Level 3 (Senior PM) | Level 4 (Program/Portfolio) |
|---|---|---|---|---|
| Planning | Follows a template with guidance | Builds a plan independently | Builds plans others learn from | Sequences plans across programs |
| Risk management | Logs risks when told to | Runs qualitative risk process unprompted | Runs quantitative EMV analysis | Aggregates risk across a portfolio |
| Stakeholder management | Executes assigned communication | Manages own stakeholder map | Manages resistance and coalitions | Manages board/exec relationships |
| Crisis response | Escalates immediately | Contains with support | Leads incident command | Sets organisational crisis protocol |
| Judgment under ambiguity | Needs explicit instruction | Makes reasonable calls, checks big ones | Makes calls others would've escalated | Sets the standard for what needs escalating |

### [07 · AI Tools for Project Management](level-4/07-ai-tools-for-pm.md)

*A framework: delegate, assist, or reserve*

| Task category | Delegate (AI does it, human spot-checks) | Assist (AI drafts, human decides) | Reserve for humans entirely |
|---|---|---|---|
| Status report drafting from raw data | Yes — summarising structured data into prose is low-risk and easy to verify | | |
| Risk register brainstorming | | Yes — AI proposes candidate risks from similar past projects; PM judges relevance and rates probability/impact | |
| EVM calculation from PV/EV/AC inputs | Yes — arithmetic is exactly where AI is reliable, still worth a spot-check | | |
| Stakeholder resistance diagnosis | | | Reserve — reading a specific person's political motivations requires context an AI doesn't have and shouldn't guess at |
| Meeting notes summarisation | Yes | | |
| Contract negotiation strategy | | Yes — AI can draft a term sheet or model an FPIF scenario, but the actual negotiation call is a human's | |
| Go/no-go recommendation on a gate review | | | Reserve — a gate decision (Level 3, module 05) carries accountability that shouldn't be laundered through a tool's output |
| Schedule dependency detection from a large plan | | Yes — AI is good at flagging *candidate* dependencies humans miss in a large plan, bad at judging which ones actually matter |

### [08 · Global/Distributed Team Project Management](level-4/08-global-distributed-teams.md)

*What actually breaks with distance*

| Co-located mechanism | What it silently provides | Distributed replacement needed |
|---|---|---|
| Overhearing nearby conversations | Ambient awareness of related work | Shared, visible work-tracking tool everyone actually checks |
| Hallway/water-cooler decisions | Fast informal alignment | An explicit norm: decisions made informally must be written down within the day, or they don't count |
| Reading a room in a meeting | Sensing unspoken disagreement | Deliberately asking quieter/remote voices directly, not just the loudest in-room voice |
| Same-timezone "quick call" | Fast clarification | Async-first default; synchronous only for genuinely time-sensitive items |

### [09 · Career Growth: PM to Program/Portfolio Director](level-4/09-career-growth-pm-to-director.md)

*What actually changes*

| Dimension | Senior Project Manager | Program/Portfolio Director |
|---|---|---|
| Primary tool | The plan, the risk register, direct execution | People, priorities, capital allocation decisions |
| Success measure | This project delivers | The portfolio/program delivers its aggregate benefit (Level 3, module 01–02) |
| Time horizon | Weeks to a year | Multiple years, benefit realisation curves (Level 4, module 03) |
| Where judgment is exercised | On this project's specific risks and trade-offs | On which PMs to trust with autonomy, and when to intervene |
| Biggest risk of over-indexing on old strengths | Micromanaging PMs the way you used to manage your own tasks | Losing the ability to spot a real crisis early because you're no longer close to the detail |

### [10 · Capstone — Full Program Charter &amp; Governance Model](level-4/10-capstone-program-charter-governance.md)

*Section 1 — Program charter*

| Field | Content |
|---|---|
| Program name | Unified Patient Platform (UPP) |
| Sponsor | Chief Operating Officer |
| Program Director | Newly promoted from Senior PM (module 09 transition in progress) |
| Duration | 3 years, 6 six-month phases |
| Budget | $18,000,000 |
| Primary benefit | Reduce average patient intake time from 22 minutes to 8 minutes across all 12 clinics |
| Secondary benefits | Cut billing error rate from 6% to under 1.5%; enable single patient record across clinics |
| Constituent projects | (1) Core platform build, (2) Clinic-by-clinic rollout (12 waves), (3) Billing system integration, (4) Clinical staff training & change management |

---

Go deeper with the full [Project Manager Mastery Path](index.md) curriculum or test yourself with the [interview questions](interview-questions.md).
