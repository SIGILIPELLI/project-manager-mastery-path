# 08 · Team Management & Conflict Resolution

Every other module in this level deals with numbers on a page — floats, cost
indices, expected monetary values. This one deals with the only resource that
can decide, on its own, not to cooperate. A project plan is executed by
people who have competing loyalties, unequal information, private opinions
about whether the project is worth doing, and line managers who are not you.
**The project manager's authority over the team is usually far weaker than
their accountability for the outcome**, and closing that gap is what team
management actually is. This module covers how teams develop, how to size
what a team can really deliver, why conflict is a signal rather than a
failure, and the five ways to resolve it.

## The authority gap

Start by naming your structure honestly, because it determines how much of
your effort has to go into influence rather than instruction.

| Structure | PM authority | Team reports to | Practical consequence |
|---|---|---|---|
| Functional | Little or none | Functional manager | You negotiate for every hour; escalation goes through their boss |
| Weak matrix | Limited | Functional manager | You coordinate; you cannot set priorities |
| Balanced matrix | Shared | Both | Constant dual-priority conflict; needs explicit agreements |
| Strong matrix | High | PM (mostly) | You set work priorities; manager still owns career and pay |
| Projectised | Almost total | PM | Full control; you also own the post-project redeployment problem |

If you are in a weak or balanced matrix, a plan that assumes people will do
what you ask because you asked is not a plan. The counter-measure is a
written resource agreement with each functional manager: named person, named
percentage, named dates, countersigned. "Priya, 60%, 4 May to 31 July" is
enforceable in a way that "some backend support" never is.

## Tuckman's stages — and what the PM does in each

Teams do not become productive on day one, and the dip in the middle is
normal rather than a sign you picked the wrong people.

| Stage | What it looks like | Productivity | What the PM must do |
|---|---|---|---|
| **Forming** | Polite, cautious, questions directed at you | Low | Set direction, clarify roles, remove ambiguity |
| **Storming** | Disagreement over approach, roles, ownership | **Lowest** | Do *not* suppress it; facilitate, hold decisions to criteria |
| **Norming** | Working agreements emerge, conflict handled internally | Rising | Step back, let the team own process decisions |
| **Performing** | Self-organising, solves problems without you | Highest | Protect from outside disruption, remove impediments |
| **Adjourning** | Wind-down, anxiety about what's next | Falling | Recognise contribution, help with redeployment early |

Two practical consequences. First, **any change of membership sends a team
back toward forming** — swapping two of six people mid-project is not a
neutral act, and the plan should carry a productivity dip after it. Second,
storming is where the team decides how it will make decisions. A PM who
smooths it over to keep the peace gets a team that avoids conflict, which
means disagreements go underground and surface later as missed commitments.

## Sizing what a team can really deliver

Optimistic capacity planning is one of the most common causes of a schedule
that was never achievable. Here is a full capacity calculation for a
six-person team over a ten-working-day sprint.

| Line | Calculation | Hours |
|---|---|---|
| Gross capacity | 6 people × 10 days × 8 h | **480.0** |
| − Public holiday | 6 people × 1 day × 8 h | −48.0 |
| − Booked annual leave | Priya 3 days + Tom 2 days = 5 days × 8 h | −40.0 |
| − Ceremonies | (4 + 2 + 1.5 + 2.25) = 9.75 h × 6 people | −58.5 |
| − Production support rota | 1 person × 5 days × 8 h | −40.0 |
| **Net available capacity** | | **293.5** |

The ceremony line is planning (4 h), review (2 h), retrospective (1.5 h) and
nine daily stand-ups at 15 minutes (2.25 h). The **focus factor** is
293.5 ÷ 480 = **61.1%** — and that is a healthy team, not a dysfunctional
one. If the team's historical throughput is 7.5 hours per story point, the
defensible commitment is 293.5 ÷ 7.5 ≈ **39 points**, not the 48 points a
naive "6 people × 8 points each" calculation would produce.

!!! warning "The 100% utilisation trap"
    Planning people at 100% guarantees you are late. As utilisation
    approaches 100%, queue time rises without limit — any variation at all
    (an illness, a production incident, a late input) has nowhere to be
    absorbed. A team planned at 100% has no capacity to respond to the very
    variation that projects are made of. Plan to the net figure, and hold
    the difference as a deliberate buffer rather than letting it be silently
    consumed.

## Why bigger teams are slower per person

Communication overhead grows quadratically with headcount. The number of
two-way channels in a team of *n* people is *n*(*n* − 1) ÷ 2.

| Team size | Communication channels | Change |
|---|---|---|
| 6 | 15 | baseline |
| 10 | 45 | **+30 channels (+200%)** |

Adding four people to a team of six is a **67% increase in headcount and a
200% increase in communication channels**. This is why adding people to a
late project usually makes it later: the new members consume experienced
members' time for onboarding, and every existing member now has more
coordination to do. The mitigation is not to refuse extra people but to
**split into sub-teams with defined interfaces**, so the channel count inside
each group stays small.

## The team charter

Write the working agreements down at the start, while nobody is angry. A
charter agreed under pressure is a negotiation; agreed early, it is just
housekeeping.

| Section | Example content |
|---|---|
| Purpose | Deliver the customer self-service portal by 30 November |
| Core hours | 10:00–15:00 overlap; outside that, asynchronous |
| Meeting rules | Agenda 24 h ahead or the meeting is cancelled |
| Decision rule | Consent within the team; PM decides if unresolved after 2 days |
| Definition of Done | Code reviewed, tests passing, docs updated, deployed to staging |
| Response times | Direct question 4 h, review request 1 working day |
| Escalation path | Team lead → PM → sponsor; 2 working days at each level |
| Conflict norm | Disagree in the meeting, commit after it; no re-litigating in DMs |
| How we handle a miss | Flag early with no blame; a surprise on the due date is the failure |

The last row is the highest-value line in the charter. **A team that is
punished for early bad news will give you late bad news**, and late bad news
is the one thing a schedule cannot absorb.

## Conflict: sources and modes

Conflict is not a sign of a broken team. Its complete absence usually means
either the work is trivial or people have stopped saying what they think.
The classic ranking of conflict sources on projects, most frequent first:

1. Schedules
2. Project priorities
3. Resources
4. Technical opinions
5. Administrative procedures
6. Cost
7. **Personality**

Note that personality is *last*, but it is the first explanation most people
reach for. **Diagnosing a resource conflict as a personality clash is the
single most common mistake in project team management** — it makes the
problem unsolvable, because you cannot renegotiate someone's personality,
whereas you can renegotiate an allocation.

The five conflict-handling modes, and when each is actually correct:

| Mode | What it does | Use it when | Cost |
|---|---|---|---|
| **Collaborate / problem-solve** | Finds a solution meeting both sets of needs | Stakes high, time available, relationship ongoing | Slow; needs trust |
| **Compromise** | Both sides concede something | Equal power, moderate stakes, deadline pressure | Nobody fully satisfied; becomes a lazy default |
| **Smooth / accommodate** | Emphasise agreement, concede your point | The issue matters far more to them than to you | Repeated use destroys your credibility |
| **Force / direct** | Impose a decision by authority | Safety, compliance, or deadlock on the critical path | Creates losers; spend this sparingly |
| **Withdraw / avoid** | Defer or step away | Emotions too high right now, or the issue is trivial | Unresolved issues resurface, usually worse |

Collaborate produces the most durable outcome and is the default to aim for.
Withdraw is the weakest — but "let's both sleep on this and reconvene at 9am
with the data" is a legitimate, deliberate use of it.

## Worked scenario — diagnose before you intervene

The QA lead says the developers "keep throwing untested rubbish over the
wall." The dev lead says QA "invent blocking defects to protect their own
timeline." Two months of this. Everyone calls it a personality clash.

The PM investigates before intervening and finds the facts:

| Finding | Evidence |
|---|---|
| QA capacity is 40% of what the plan assumed | 1 tester allocated; plan assumed 2.5 |
| The Definition of Done never mentioned unit test coverage | Charter reviewed |
| QA bonus is tied to defects found; dev bonus to stories closed | Objective sheets |
| Neither lead has attended the other's planning session | Calendars |

None of these is a personality problem. Three are structural and one is an
information problem. The interventions follow directly:

| Root cause | Intervention | Mode used |
|---|---|---|
| QA under-resourced | Escalate a resource request carrying the 40% figure | Collaborate (with sponsor) |
| Ambiguous Definition of Done | Rewrite the DoD jointly; both leads sign | Collaborate |
| Conflicting incentives | Ask the sponsor to set one shared quality objective | Force (only they can) |
| No shared context | Both leads attend both ceremonies | Smooth (low cost, high signal) |

Four weeks later, escaped defects fell from 31 to 9 per release and neither
lead's personality had changed at all. **The conflict was the symptom; the
incentive structure was the disease.**

## The conflict log

For anything that persists past one conversation, log it. It keeps you honest
about whether interventions worked, and it is the evidence base if you ever
have to escalate.

| ID | Parties | Source (of the 7) | Raised | Intervention | Mode | Status | Reviewed |
|---|---|---|---|---|---|---|---|
| C-01 | QA lead / Dev lead | Resources + procedures | 4 Mar | Resource request + DoD rewrite | Collaborate | Resolved | 8 Apr |
| C-02 | Vendor PM / Architect | Technical opinion | 19 Mar | Design bake-off against agreed criteria | Collaborate | Resolved | 2 Apr |
| C-03 | Finance / Sponsor | Priorities | 27 Mar | Sponsor ruled; recorded in steering minutes | Force | Resolved | 27 Mar |
| C-04 | Ops manager / PM | Schedule | 3 Apr | Freeze window moved 1 week into float (module 02) | Compromise | Open | 17 Apr |

!!! note "Escalate the issue, never the person"
    A good escalation states the decision required, the options, the cost of
    each, and the date by which the decision must be made to avoid schedule
    impact. A bad escalation states that someone is being difficult. The
    first gets you a decision; the second gets you a reputation and no
    decision.

## Motivation, briefly but usefully

Two models earn their keep. **Herzberg** separates *hygiene* factors (salary,
conditions, job security, policy) from *motivators* (achievement,
recognition, responsibility, growth). Fixing hygiene removes dissatisfaction
but does not create motivation — a bigger desk will not make anyone care
about the deliverable. **McClelland** identifies three dominant needs, and
matching assignment to need costs nothing:

| Dominant need | Give them | Do not give them |
|---|---|---|
| Achievement | A hard problem with clear success criteria and autonomy | Vague, unmeasurable work |
| Affiliation | Pairing, facilitation, cross-team liaison roles | Isolated solo work with no feedback |
| Power / influence | Ownership of a workstream, representing the team externally | Work with no visible ownership |

For a project manager with no control over pay, **assignment design is the
main motivational lever you actually hold.** Use it deliberately.

## Exercise

Work with a real team — current or recent — throughout.

1. Identify your organisational structure from the authority table, then
   write the specific sentence describing where your authority actually ends.
   Name one thing you have been assuming you control that you do not.
2. Build the full capacity calculation for one iteration of your team's work:
   gross hours, every deduction with its arithmetic, net capacity, and the
   resulting **focus factor as a percentage**. Compare it against the
   commitment that was actually made, and state the gap.
3. Compute the communication channels for your team today and for your team
   plus three people. State the percentage increase in each, then describe
   the sub-team split you would use to contain it.
4. Draft a team charter with at least seven rows, including a decision rule,
   a committed response time, and an explicit norm for raising a missed
   commitment early.
5. Take a live conflict. Classify it against the seven sources — and if your
   first instinct was "personality", find the structural cause underneath it.
   List at least three pieces of **evidence** you would gather before
   intervening.
6. For that conflict, choose a resolution mode, justify why the other four
   are wrong here, and write the intervention. Then state the measurable
   outcome you will check in four weeks to know whether it actually worked.
