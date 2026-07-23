# 10 · Project — Full Project Charter & Schedule

This capstone project pulls together every framework from Level 1 into one
coherent deliverable for a single sample project: a project charter, scope
statement, WBS, schedule with critical path, budget, risk register, and
stakeholder/communication plan. Read through the worked example below —
it's a complete, realistic deliverable — then produce your own version for
a project of your choosing in the Exercise.

## The sample project: "Launch a Customer Referral Program"

A mid-size subscription software company (120 employees) wants to launch a
customer referral program: existing customers get a discount for referring
new customers, tracked through a small web portal integrated with the
existing billing system. Below is the full set of Level 1 deliverables for
this project.

### 1. Project Charter

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

### 2. Scope Statement

- **Deliverables:** (1) referral portal (customer-facing page to generate
  and share a referral link), (2) billing integration (apply discount
  automatically when a referred customer subscribes), (3) admin dashboard
  (Marketing can see referral counts and program performance).
- **Acceptance criteria:** a customer can generate a unique referral link,
  a new customer signing up via that link triggers an automatic discount
  for both parties, and Marketing can view real-time referral counts in the
  dashboard.
- **Exclusions:** no changes to the core billing data model (per the
  charter's constraint); no mobile app version (web only, this phase); no
  multi-tier/multi-level referral rewards (single-level only, this phase).
- **Constraints:** fixed $45,000 budget; must not touch the billing data
  model; must launch before the start of Marketing's Q3 campaign push.
- **Assumptions:** the existing billing system's API supports applying a
  discount code programmatically without a data-model change.

### 3. Work Breakdown Structure

| WBS ID | Deliverable / Work package |
|---|---|
| 1.1 | Design — referral portal UX |
| 1.2 | Design — admin dashboard UX |
| 2.1 | Development — referral link generation |
| 2.2 | Development — billing API integration |
| 2.3 | Development — admin dashboard |
| 3.1 | Testing — end-to-end referral flow |
| 3.2 | Testing — dashboard accuracy |
| 4.1 | Launch — soft launch to 10% of customers |
| 4.2 | Launch — full rollout |

### 4. Schedule and Critical Path

| Task | Duration | Depends on |
|---|---|---|
| 1.1 Portal design | 1 week | — |
| 1.2 Dashboard design | 1 week | — |
| 2.1 Link generation dev | 2 weeks | 1.1 |
| 2.2 Billing integration dev | 3 weeks | 1.1 |
| 2.3 Dashboard dev | 2 weeks | 1.2 |
| 3.1 End-to-end testing | 1 week | 2.1, 2.2 |
| 3.2 Dashboard testing | 1 week | 2.3 |
| 4.1 Soft launch | 1 week | 3.1, 3.2 |
| 4.2 Full rollout | 1 week | 4.1 |

Tracing the paths: **1.1 → 2.2 → 3.1 → 4.1 → 4.2** = 1+3+1+1+1 = **7 weeks**
is the longest path (the billing integration, at 3 weeks, is the single
longest task and sits on the critical path). The path through the dashboard
(**1.2 → 2.3 → 3.2 → 4.1 → 4.2** = 1+2+1+1+1 = 6 weeks) has 1 week of float
— meaning dashboard work could slip by up to a week without affecting the
overall 7-week finish, but the billing integration cannot slip at all
without pushing the launch date.

### 5. Budget

| Item | Cost |
|---|---|
| Design (portal + dashboard) | $6,000 |
| Development (link gen + billing integration + dashboard) | $26,000 |
| Testing | $4,000 |
| Launch (soft + full rollout support) | $3,000 |
| **Subtotal** | **$39,000** |
| Contingency (sized from risk register below: $2,400 + $1,600 + $1,000 ≈ $5,000, rounded) | $5,000 |
| **Wait — check against charter budget** | **$44,000 ≤ $45,000 ✓** |

### 6. Risk Register

| Risk | Probability | Impact | Priority | Response |
|---|---|---|---|---|
| Because the billing API has never been used for real-time discount application, integration may take longer than the 3-week estimate | Medium | High | High | Mitigate — run a 2-day technical spike in week 1 to validate the API can do this before committing the full 3-week estimate |
| Because Customer Support hasn't been consulted on the referral flow, they may be unprepared for related support tickets at launch | Medium | Medium | Medium | Mitigate — include Support in the soft-launch review before full rollout |
| Because this is the team's first referral program, the discount abuse potential (e.g., self-referral) may not be fully covered by initial design | Low | High | Medium | Mitigate — explicit design review step for abuse cases before dev sign-off |

### 7. Stakeholder & Communication Plan

| Stakeholder | Power | Interest | Engagement | Format/Frequency |
|---|---|---|---|---|
| VP of Marketing (sponsor) | High | High | Manage closely | Weekly 1:1 |
| Engineering lead | High | High | Manage closely | Daily stand-up + weekly 1:1 with PM |
| Billing/Finance | High | Medium | Involve early, brief at checkpoints | Written brief at design sign-off and pre-launch |
| Customer Support | Low | High | Keep informed, gather input | Bi-weekly demo, included in soft-launch review |
| Executive leadership | High | Low | Keep satisfied | Single summary at kickoff and at full rollout |

## Exercise

Produce your own complete Level 1 capstone for a project of your choice —
reuse and refine the scope statement, risk register, and stakeholder
register you built in this level's earlier module exercises if they fit,
or start fresh with a new project idea. Your deliverable must include all
seven sections shown above: charter, scope statement, WBS, schedule with an
explicitly calculated critical path (show the path calculations, not just
the final answer), budget (with contingency tied to specific risks, not a
flat percentage), risk register, and stakeholder/communication plan. Keep
it realistic and internally consistent — the budget should reflect the
WBS, the schedule should reflect the WBS, and the risk register's
contingency sizing should trace back to specific line items in the risk
register, the way the worked example above does.
