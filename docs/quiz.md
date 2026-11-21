---
title: "Final Quiz"
description: "Test what you have learned across all four levels of Project Manager Mastery Path with a 19-question final quiz."
---

# Final Quiz

19 questions drawn from all four levels of this course. You need **70% (14 out of 19)** to pass —
you can retake it as many times as you like. Your best result is saved in this browser.

<div id="mp-quiz-root"></div>

<script type="application/json" id="mp-quiz-data">
[
  {
    "question": "Tasks: A(4d) → B(6d), A → C(3d), B and C → D(2d). What is the project duration and which task has float?\n```python\nd={'A':4,'B':6,'C':3,'D':2}\nprint(4+6+2, 'C float', (4+6)-(4+3))\n```\n",
    "options": [
      "12 C float 3",
      "10 C float 3",
      "9 C float 0",
      "12 B float 3"
    ],
    "correctIndex": 0,
    "explanation": "The critical path is A-B-D; C can slip 3 days. Verified by running it."
  },
  {
    "question": "EV 60000, AC 72000, PV 66000. What are CPI and SPI?\n```python\nprint(round(60000/72000,2), round(60000/66000,2))\n```\n",
    "options": [
      "1.2 1.1",
      "0.91 0.83",
      "0.83 1.1",
      "0.83 0.91"
    ],
    "correctIndex": 3,
    "explanation": "Both below 1: over budget and behind. Verified by running it."
  },
  {
    "question": "BAC 300000, CPI 0.75. What does the EAC say about the overrun?\n```python\neac=300000/0.75\nprint(eac, eac-300000)\n```\n",
    "options": [
      "375000.0 75000.0",
      "300000.0 0.0",
      "400000.0 100000.0",
      "225000.0 -75000.0"
    ],
    "correctIndex": 2,
    "explanation": "If current efficiency continues. Verified by running it."
  },
  {
    "question": "Risk A: 20% × 80000; Risk B: 50% × 30000. Total EMV?\n```python\nprint(0.2*80000+0.5*30000)\n```\n",
    "options": [
      "31000.0",
      "62000.0",
      "15500.0",
      "110000.0"
    ],
    "correctIndex": 0,
    "explanation": "Sum of probability × impact. Verified by running it."
  },
  {
    "question": "PERT O=6, M=9, P=18. Expected duration?\n```python\nprint((6+4*9+18)/6)\n```\n",
    "options": [
      "12.0",
      "11.0",
      "9.0",
      "10.0"
    ],
    "correctIndex": 3,
    "explanation": "(O+4M+P)/6. Verified by running it."
  },
  {
    "question": "A 12-person team vs a 5-person team: how many communication channels each?\n```python\nprint(12*11//2, 5*4//2)\n```\n",
    "options": [
      "66 10",
      "132 20",
      "12 5",
      "24 10"
    ],
    "correctIndex": 0,
    "explanation": "n(n−1)/2. Verified by running it."
  },
  {
    "question": "A stakeholder asks for a 'small' addition mid-project. What do you do?",
    "options": [
      "Add it",
      "Hide it",
      "Assess the impact and run it through change control",
      "Refuse"
    ],
    "correctIndex": 2,
    "explanation": "Protect the baseline."
  },
  {
    "question": "A project is red on schedule. Adding people late may make it later. Why?",
    "options": [
      "Cost",
      "Onboarding and communication overhead (Brooks's law)",
      "Law",
      "Style"
    ],
    "correctIndex": 1,
    "explanation": "Reassess options."
  },
  {
    "question": "A risk's trigger is observed. What do you do?",
    "options": [
      "Ignore",
      "Close",
      "Activate the planned response and update the register",
      "Wait"
    ],
    "correctIndex": 2,
    "explanation": "Proactive."
  },
  {
    "question": "What distinguishes a program from a large project?",
    "options": [
      "Coordinated management of related projects to realize combined benefits",
      "Size",
      "Time",
      "Cost"
    ],
    "correctIndex": 0,
    "explanation": "Benefits."
  },
  {
    "question": "The status report is green but the team says it's failing. What is it?",
    "options": [
      "Rare",
      "A watermelon report; fix reporting with objective thresholds",
      "Late",
      "Fine"
    ],
    "correctIndex": 1,
    "explanation": "Honest status."
  },
  {
    "question": "What does fast-tracking add?",
    "options": [
      "Cost only",
      "Schedule compression through parallel work, with more risk and rework",
      "Float",
      "Quality"
    ],
    "correctIndex": 1,
    "explanation": "Trade-off."
  },
  {
    "question": "Which contract places most cost risk on the seller?",
    "options": [
      "T&M",
      "Fixed price",
      "Reimbursable",
      "Cost-plus"
    ],
    "correctIndex": 1,
    "explanation": "Scope must be clear."
  },
  {
    "question": "What should a change request include?",
    "options": [
      "Name",
      "Date",
      "Cost",
      "Rationale and impacts on scope, schedule, cost and risk"
    ],
    "correctIndex": 3,
    "explanation": "Decision-ready."
  },
  {
    "question": "What is the purpose of a retrospective?",
    "options": [
      "Improve the way of working through reflection and actions",
      "Demo",
      "Blame",
      "Report"
    ],
    "correctIndex": 0,
    "explanation": "Continuous improvement."
  },
  {
    "question": "In stakeholder grids, high power and high interest means?",
    "options": [
      "Monitor",
      "Manage closely",
      "Inform",
      "Ignore"
    ],
    "correctIndex": 1,
    "explanation": "Engagement."
  },
  {
    "question": "What makes a PMO valuable?",
    "options": [
      "Rules",
      "Audits",
      "Templates",
      "Improved delivery predictability and benefits realized"
    ],
    "correctIndex": 3,
    "explanation": "Outcomes."
  },
  {
    "question": "What guards against optimistic estimates?",
    "options": [
      "One number",
      "Padding",
      "More pressure",
      "Three-point estimates, reference classes and reserves"
    ],
    "correctIndex": 3,
    "explanation": "Evidence."
  },
  {
    "question": "What is the right first move when taking over a failing project?",
    "options": [
      "Blame",
      "Add staff",
      "Assess real status and root causes before replanning",
      "Replan"
    ],
    "correctIndex": 2,
    "explanation": "Diagnose."
  }
]
</script>

## Coding challenges

Try these on your own computer, then compare your output. Nothing you write is sent anywhere.

### A critical path scheduler

Implement schedule(): a topological order, forward pass (earliest start/finish), backward pass (latest start/finish from the project end) and float. Print the table, the critical path and the slack tasks, then see how a 3-day slip on the critical Procure task changes the project duration.

**Starter code**

```python
# Critical Path Method: forward pass, backward pass, float and the critical path.
TASKS = {            # name: (duration in days, predecessors)
    "Requirements": (5, []),
    "Design":       (7, ["Requirements"]),
    "Procure":      (10, ["Requirements"]),
    "Build":        (12, ["Design", "Procure"]),
    "Docs":         (6, ["Design"]),
    "Test":         (6, ["Build"]),
    "Train":        (4, ["Docs", "Build"]),
    "Go-live":      (1, ["Test", "Train"]),
}

def schedule(tasks):
    # return (order, es, ef, ls, lf, float_, end): a topological order, forward pass (ES/EF),
    # backward pass (LS/LF from the project end), float = LS - ES and the project duration
    return [], {}, {}, {}, {}, {}, 0

def critical_path(order, float_, tasks):
    # tasks with zero float, in schedule order
    return []

order, es, ef, ls, lf, float_, end

def critical_path(order, float_, tasks):
    return [t for t in order if float_[t] == 0]

order, es, ef, ls, lf, fl, end = schedule(TASKS)
print(f"{'task':13s}{'ES':>4s}{'EF':>4s}{'LS':>4s}{'LF':>4s}{'float':>6s}")
for t in order:
    print(f"{t:13s}{es[t]:4d}{ef[t]:4d}{ls[t]:4d}{lf[t]:4d}{fl[t]:6d}")
print("duration:", end, "days")
print("critical path:", " -> ".join(critical_path(order, fl, TASKS)))
print("slack tasks:", ", ".join(f"{t}({fl[t]})" for t in order if fl[t] > 0))

# What if Procure slips by 3 days?
slipped = dict(TASKS); slipped["Procure"] = (13, ["Requirements"])
_, _, _, _, _, fl2, end2 = schedule(slipped)
print("with Procure +3d -> duration:", end2, "| critical:", " -> ".join(t for t in schedule(slipped)[0] if fl2[t] == 0))
```

**Expected output**

```text
task           ES  EF  LS  LF float
Requirements    0   5   0   5     0
Design          5  12   8  15     3
Procure         5  15   5  15     0
Build          15  27  15  27     0
Docs           12  18  23  29    11
Test           27  33  27  33     0
Train          27  31  29  33     2
Go-live        33  34  33  34     0
duration: 34 days
critical path: Requirements -> Procure -> Build -> Test -> Go-live
slack tasks: Design(3), Docs(11), Train(2)
with Procure +3d -> duration: 37 | critical: Requirements -> Procure -> Build -> Test -> Go-live
```

<details><summary>Show solution and explanation</summary>

<pre><code># Critical Path Method: forward pass, backward pass, float and the critical path.
TASKS = {            # name: (duration in days, predecessors)
    &quot;Requirements&quot;: (5, []),
    &quot;Design&quot;:       (7, [&quot;Requirements&quot;]),
    &quot;Procure&quot;:      (10, [&quot;Requirements&quot;]),
    &quot;Build&quot;:        (12, [&quot;Design&quot;, &quot;Procure&quot;]),
    &quot;Docs&quot;:         (6, [&quot;Design&quot;]),
    &quot;Test&quot;:         (6, [&quot;Build&quot;]),
    &quot;Train&quot;:        (4, [&quot;Docs&quot;, &quot;Build&quot;]),
    &quot;Go-live&quot;:      (1, [&quot;Test&quot;, &quot;Train&quot;]),
}

def schedule(tasks):
    order, done = [], set()
    while len(order) &lt; len(tasks):                      # topological order
        for t, (_, preds) in tasks.items():
            if t not in done and all(p in done for p in preds):
                order.append(t); done.add(t)
    es, ef = {}, {}
    for t in order:                                     # forward pass
        dur, preds = tasks[t]
        es[t] = max((ef[p] for p in preds), default=0)
        ef[t] = es[t] + dur
    end = max(ef.values())
    succ = {t: [u for u, (_, ps) in tasks.items() if t in ps] for t in tasks}
    ls, lf = {}, {}
    for t in reversed(order):                           # backward pass
        lf[t] = min((ls[s] for s in succ[t]), default=end)
        ls[t] = lf[t] - tasks[t][0]
    float_ = {t: ls[t] - es[t] for t in tasks}
    return order, es, ef, ls, lf, float_, end

def critical_path(order, float_, tasks):
    return [t for t in order if float_[t] == 0]

order, es, ef, ls, lf, fl, end = schedule(TASKS)
print(f&quot;{&#x27;task&#x27;:13s}{&#x27;ES&#x27;:&gt;4s}{&#x27;EF&#x27;:&gt;4s}{&#x27;LS&#x27;:&gt;4s}{&#x27;LF&#x27;:&gt;4s}{&#x27;float&#x27;:&gt;6s}&quot;)
for t in order:
    print(f&quot;{t:13s}{es[t]:4d}{ef[t]:4d}{ls[t]:4d}{lf[t]:4d}{fl[t]:6d}&quot;)
print(&quot;duration:&quot;, end, &quot;days&quot;)
print(&quot;critical path:&quot;, &quot; -&gt; &quot;.join(critical_path(order, fl, TASKS)))
print(&quot;slack tasks:&quot;, &quot;, &quot;.join(f&quot;{t}({fl[t]})&quot; for t in order if fl[t] &gt; 0))

# What if Procure slips by 3 days?
slipped = dict(TASKS); slipped[&quot;Procure&quot;] = (13, [&quot;Requirements&quot;])
_, _, _, _, _, fl2, end2 = schedule(slipped)
print(&quot;with Procure +3d -&gt; duration:&quot;, end2, &quot;| critical:&quot;, &quot; -&gt; &quot;.join(t for t in schedule(slipped)[0] if fl2[t] == 0))
</code></pre>

<p>Forward pass gives earliest times, the backward pass gives latest allowable times, and zero-float tasks form the critical path. A slip on a non-critical task consumes its float, but beyond it the path shifts. Verified by running the Python implementation.</p>
</details>

### Earned value report, forecast and PERT range

Compute PV, EV, AC, CV, SV, CPI, SPI, EAC, ETC, VAC and TCPI from monthly progress, give each month a RAG status, forecast the overrun as a percentage of BAC and compute a PERT total with a ~95% range for three phases.

**Starter code**

```python
# Earned value management, forecasts and a PERT estimate.
BAC = 500_000
REPORTS = [            # month, planned % complete, actual % complete, actual cost to date
    (1, 10, 10, 48_000), (2, 25, 22, 120_000), (3, 40, 33, 205_000), (4, 55, 44, 290_000),
]
def evm(month_row):
    # return a dict with PV, EV, AC, CV (EV-AC), SV (EV-PV), CPI (EV/AC), SPI (EV/PV),
    # EAC (BAC/CPI), ETC (EAC-AC), VAC (BAC-EAC) and TCPI ((BAC-EV)/(BAC-AC))
    return {}

def status(cpi, spi):
    # GREEN if both >= 0.95, AMBER if both >= 0.85, otherwise RED
    return ""

def pert(o, m, p):
    # (expected duration (O+4M+P)/6, standard deviation (P-O)/6)
    return 0, 0

# TODO: print a table of the four monthly reports (PV, EV, AC, CPI, SPI, EAC, status), then the latest CV, SV, VAC, TCPI
#       and the overrun forecast as a percentage of BAC.
# TODO: PERT for phases = {"Design": (8, 10, 18), "Build": (20, 26, 44), "Test": (6, 8, 16)}:
#       total mean, total standard deviation (square root of the sum of variances) and the ~95% range (mean +/- 2 sd).
```

**Expected output**

```text
month   PV      EV      AC      CPI   SPI   EAC       status
    1  50,000  50,000  48,000  1.04  1.00   480,000  GREEN
    2 125,000 110,000 120,000  0.92  0.88   545,455  AMBER
    3 200,000 165,000 205,000  0.80  0.82   621,212  RED
    4 275,000 220,000 290,000  0.76  0.80   659,091  RED
latest: CV=-70,000 SV=-55,000 VAC=-159,091 TCPI=1.33
overrun forecast: 31.8% of BAC
PERT total: 48.0 days, sd 4.6; 95% range 38.7-57.3
```

<details><summary>Show solution and explanation</summary>

<pre><code># Earned value management, forecasts and a PERT estimate.
BAC = 500_000
REPORTS = [            # month, planned % complete, actual % complete, actual cost to date
    (1, 10, 10, 48_000), (2, 25, 22, 120_000), (3, 40, 33, 205_000), (4, 55, 44, 290_000),
]
def evm(month_row):
    m, planned, actual, ac = month_row
    pv, ev = BAC * planned / 100, BAC * actual / 100
    cpi, spi = ev / ac, ev / pv
    eac = BAC / cpi                              # current efficiency continues
    etc = eac - ac
    tcpi = (BAC - ev) / (BAC - ac)
    return {&quot;PV&quot;: pv, &quot;EV&quot;: ev, &quot;AC&quot;: ac, &quot;CV&quot;: ev - ac, &quot;SV&quot;: ev - pv, &quot;CPI&quot;: cpi, &quot;SPI&quot;: spi, &quot;EAC&quot;: eac, &quot;ETC&quot;: etc, &quot;VAC&quot;: BAC - eac, &quot;TCPI&quot;: tcpi}

def status(cpi, spi):
    if cpi &gt;= 0.95 and spi &gt;= 0.95: return &quot;GREEN&quot;
    if cpi &gt;= 0.85 and spi &gt;= 0.85: return &quot;AMBER&quot;
    return &quot;RED&quot;

print(&quot;month   PV      EV      AC      CPI   SPI   EAC       status&quot;)
for r in REPORTS:
    e = evm(r)
    print(f&quot;{r[0]:&gt;5d} {e[&#x27;PV&#x27;]:7,.0f} {e[&#x27;EV&#x27;]:7,.0f} {e[&#x27;AC&#x27;]:7,.0f}  {e[&#x27;CPI&#x27;]:.2f}  {e[&#x27;SPI&#x27;]:.2f}  {e[&#x27;EAC&#x27;]:8,.0f}  {status(e[&#x27;CPI&#x27;], e[&#x27;SPI&#x27;])}&quot;)
last = evm(REPORTS[-1])
print(f&quot;latest: CV={last[&#x27;CV&#x27;]:,.0f} SV={last[&#x27;SV&#x27;]:,.0f} VAC={last[&#x27;VAC&#x27;]:,.0f} TCPI={last[&#x27;TCPI&#x27;]:.2f}&quot;)
print(&quot;overrun forecast:&quot;, f&quot;{-last[&#x27;VAC&#x27;] / BAC * 100:.1f}% of BAC&quot;)

def pert(o, m, p):
    return (o + 4 * m + p) / 6, (p - o) / 6
phases = {&quot;Design&quot;: (8, 10, 18), &quot;Build&quot;: (20, 26, 44), &quot;Test&quot;: (6, 8, 16)}
total_mean = sum(pert(*v)[0] for v in phases.values())
total_sd = sum(pert(*v)[1] ** 2 for v in phases.values()) ** 0.5
print(f&quot;PERT total: {total_mean:.1f} days, sd {total_sd:.1f}; 95% range {total_mean - 2 * total_sd:.1f}-{total_mean + 2 * total_sd:.1f}&quot;)
</code></pre>

<p>EVM compares what was planned, earned and spent; CPI and SPI show efficiency, and EAC = BAC ÷ CPI assumes current efficiency continues. PERT adds expected values and combines variances for the range. The numbers are illustrative. Verified by running it.</p>
</details>
