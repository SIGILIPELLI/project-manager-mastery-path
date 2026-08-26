# 07 · AI Tools for Project Management

AI tools are genuinely useful in project management for a narrow, specific
set of tasks — and actively dangerous when applied past that boundary
without a human checking the output. The skill this module teaches isn't
"how to use an AI tool" (that's product-specific and changes constantly);
it's how to judge which PM tasks are safe to delegate to a model, and which
ones only look automatable.

## A framework: delegate, assist, or reserve

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

The dividing line running through this table isn't complexity — EVM
arithmetic and gate go/no-go decisions can both be described in a few
sentences — it's **accountability and context**. Arithmetic has one correct
answer that's easy to verify. A gate decision is a judgment call that
someone specific is accountable for, and using an AI recommendation as cover
("the tool said go") doesn't remove that accountability, it just obscures it
until something goes wrong.

## Worked example: using AI safely for a status report

**Raw inputs a PM has**: BAC $500,000, PV $220,000, EV $195,000, AC
$210,000, three open risks, one blocked dependency.

**What's safe to delegate**: asking a tool to draft the EVM section of the
status report from these numbers, and to summarise the three risks and one
dependency into readable prose from the PM's own risk register entries.

```
python3 -c "
BAC, PV, EV, AC = 500000, 220000, 195000, 210000
CPI = EV/AC
SPI = EV/PV
print(round(CPI,4), round(SPI,4))
"
```
→ CPI = 0.9286, SPI = 0.8864. A PM should independently verify any
AI-generated arithmetic against a direct calculation exactly like this one
— not because AI is unreliable at arithmetic specifically, but because the
cost of an unverified wrong number reaching an executive report (module 05)
is much higher than the ten seconds it takes to check.

**What's not safe to delegate**: the report's "Ask" section — the
recommendation for what the steering committee should decide given CPI
0.9286 and SPI 0.8864. That recommendation depends on context an AI tool
doesn't have (how the sponsor has reacted to past Amber reports, what
political capital exists, whether this project's Amber status is
tolerable given other portfolio pressures) — exactly the kind of judgment
this level's other modules are about.

## Common failure modes

| Failure | What it looks like | Fix |
|---|---|---|
| Automation bias | Accepting an AI-drafted risk register as complete because it looks thorough | Treat AI-generated risks as a starting brainstorm, not a final register — the PM's own project knowledge still has to add and validate entries |
| Laundering accountability | "The AI recommended it" used to justify a decision that went wrong | Every AI-assisted recommendation still needs a named human decision-maker who owns the outcome |
| Context blindness | AI drafts a stakeholder communication using a tone or fact pattern that doesn't fit the specific relationship history | Human review specifically for context, not just correctness |
| Stale data | AI summarising a document that's since been updated, producing a confidently wrong report | Point tools at the current source of truth, verify the timestamp |

## A practical adoption checklist for a PMO

| Question | Why it matters |
|---|---|
| Is the task's output independently verifiable (like arithmetic) or a judgment call? | Determines delegate vs. assist vs. reserve |
| Does using the tool here require putting confidential project data into a system outside our data governance? | A tool that's fast but leaks vendor pricing data is not actually a net gain |
| Who is accountable if the AI-assisted output is wrong? | Must be a named human, every time |
| Does relying on this tool erode a skill the PM organisation needs to keep (module 06's capability framework)? | An associate PM who never learns to draft a risk register manually because a tool always does it first arrives at Senior PM with a skill gap |

## Exercise

Your PMO is evaluating whether to let an AI tool auto-generate the weekly
portfolio rollup dashboard (Level 3, module 05) directly from each project's
raw EVM data, with no PM review before it's sent to executives.

1. Using the delegate/assist/reserve framework, classify this specific
   proposal (auto-generate *and auto-send*, no review) and justify your
   classification.
2. Identify which row of the adoption checklist this proposal fails most
   clearly, and explain why.
3. Propose a modified version of the same idea that would move it from a
   failing proposal to something you'd approve — be specific about what
   step you'd insert and where.
