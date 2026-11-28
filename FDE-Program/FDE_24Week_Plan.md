# FDE Program — 24-Week Plan (full-time, 960 hours)

**Status:** Draft v0.1 for review · **Date:** 2026-11-25 · **Audience:** program lead, instructors, lab engineer, assessors, sponsor
**Builds on:** `00_Design_Foundation.md` (binding for domains, levels, hours, gates, customers, lab model) · **Sibling:** `FDE_12Week_Plan.md` · **Evidence:** `research/01–05` · **Repo reference (read-only):** `../Projects/`

If this plan and the Foundation disagree, the Foundation wins until revised. Revise the Foundation first, then this plan.

### Label legend

| Label | Meaning |
|---|---|
| **[Sourced: R#]** | From a cited external source in `research/` (R1 AI courses · R2 cloud/DevOps · R3 pedagogy · R4 FDE role/customer skills · R5 applied AI). Source quality varies; the research notes carry the caveats. |
| **[Repo]** | Reused or adapted from the downloaded `anyops-ai/Projects` material. |
| **[Judgment]** | A design call made here. Not a published benchmark. **All pass-criteria thresholds on foundations labs (software, cloud, DevOps, DevSecOps) are [Judgment].** |
| **[Assumption]** | A planning figure to be validated in the pilot. |
| **[U]** | Tool or fact not verified in the research. Re-check before teaching it. |

**Pass criteria on AI labs** adapt the lab definitions in R5 (cited as "R5 T#-n", the n-th lab of topic T#). Their thresholds are R5's own design judgment, not published standards.

### Contents

1. Program snapshot · 2. Weekly plans (Weeks 1–24) · 3. Gates and reviews · 4. Capstone · 5. Lab catalogue · 6. Measurement, mentoring, checkpoints, optional work · 7. Prep checklists, tooling, accounts · 8. Risks, Day-120 profile, on-the-job ramp

---

## 1. Program snapshot

### 1.1 Outcomes

The 24-week program takes a CS-literate new grad (0–2 years) to **"near-independent on routine engagements"**: able to own a workstream on a senior-led engagement, with real (low-risk) embedded experience behind them **[Judgment, Foundation §2.5]**. It is deeper than the 12-week program, not slower: same 40 h/week, twice the practice, wider and deeper AI coverage, an embedded pod phase and a longer capstone.

Target exit profile for the median learner **[Judgment, Foundation §3.5]**:

| Domain | Exit target (L0–L4) | How this plan builds it |
|---|---|---|
| D1 Software Engineering | **L3** | Weeks 1–6 toolkit, Python, Linux/network, SQL/API, code reading; P2 and P3 projects; fault-driven debugging |
| D2 Cloud & Platform | **L3** | Weeks 1–10 AWS, Docker, CI/CD, Terraform, Kubernetes, observability; G1 rebuild from scratch |
| D3 Secure Delivery & Compliance | **L2** (L3 stretch) | Threaded from Week 2; dedicated Weeks 9–10; AI security Weeks 15–19; G2 review |
| D4 Applied AI | **L3** (L4 for strong learners via an authored reusable asset) | Weeks 11–18 AI Core; P5 and P6; G3 |
| D5 AI Operations & Reliability | **L3** | Weeks 13–21 tracing, reliability, serving, integration; G4 |
| D6 Customer Craft | **L3** | One Customer Lab every week (72 h) plus embedded hours; P7, pod phase, P8 |

**Readiness outcomes at G5** (Foundation §6.5): *Ready — Workstream Owner* (L2+ in all six, L3+ in at least three, craft ≥3.5) · *Ready — Supervised* · *Conditional* · *Not yet ready*. The 24-week program is expected to produce mostly Workstream Owners. This is an internal credential only; no vendor certification is funded or gated.

### 1.2 Entry requirements and pre-work

| Item | Requirement |
|---|---|
| Education / experience | New grad or 0–2 years. CS-literate: can write a working program in at least one language, knows basic data structures, has used git. **No cloud, DevOps or AI experience assumed.** |
| Hardware | Laptop with 16 GB RAM and 100 GB free disk **[Repo: Prep Guide]** |
| Cohort contract | Signed before Day 1 (Foundation §6.7), including "no required work after 17:45 or on weekends" |
| Pre-work (4 weeks out) | **One instruction only** (this resolves the repo's contradictory "do the Prep Guide, nothing else" vs. extra reading): complete the setup checklist in §7.1 (about 5 h) and the light reading list (about 3 h). **Do not cram.** Cramming inflates the G0 baseline and hides what the program should teach. |
| Availability | Unavailable for customer or operational work for the full 24 weeks (about 6 months); absence beyond 3 cumulative days moves the learner to the next cohort, with a documented exception path for illness and caregiving **[Foundation §6.7]** |
| Selection signals | A short coding exercise and a conversation about a time they explained something technical to a non-technical person [Judgment]. Not a filter on AI knowledge. |

### 1.3 Hours budget (identical to Foundation §7.2, 24-week column)

| # | Block (code) | Hours | % | Main domains |
|---|---|---|---|---|
| 1 | Onboarding and baseline (`ONB`) | 16 | 1.7 | all |
| 2 | Software fundamentals (`SWF`) | 56 | 5.8 | D1 |
| 3 | Cloud / AWS (`CLD`) | 72 | 7.5 | D2 |
| 4 | DevOps / Kubernetes (`DOP`) | 104 | 10.8 | D2, D5 |
| 5 | DevSecOps (`DSO`) | 44 | 4.6 | D3 |
| | **Foundations subtotal** | **292** | **30.4** | |
| 6 | **AI Core** (`AIC`, T1–T10) | **190** | 19.8 | D4 |
| 7 | **AI Operations & Security** (`AIO`, T11–T21) | **110** | 11.5 | D5, D3, D6 |
| | **AI subtotal** (largest block group) | **300** | **31.3** | |
| 8 | Customer Labs (`CUS`) | 72 | 7.5 | D6 |
| 9 | Projects and capstone (`PRJ`) | 184 | 19.2 | all |
| 10 | Assessment and gates (`ASM`) | 48 | 5.0 | all |
| 11 | Slack: consolidation, remediation, retros (`SLK`) | 64 | 6.7 | all |
| | **TOTAL** | **960** | **100** | |

Check: 292 + 300 + 72 + 184 + 48 + 64 = 960. Every row of this table is re-added from the weekly ledgers by the verification in §5.3. Memo lines (inside the rows above): embedded customer-craft hours inside Projects and Assessment ≈70; total customer-craft exposure ≈142 h (≈15%); AI-centric project hours (P5, P6, P8) = 112; **effective AI exposure ≈412 h (≈43%)** **[Judgment, Foundation §7.2]**.

**Hours by phase (capacity = 40 h × weeks, filled exactly; Foundation §7.6):**

| Phase (weeks) | A Foundations (1–10) | B Consolidate + AI on-ramp (11–12) | C1 AI Core (13–18) | C2 AI Ops (19–21) | D Customer + pod (22–24) | Total |
|---|---|---|---|---|---|---|
| ONB | 16 | | | | | 16 |
| SWF | 56 | | | | | 56 |
| CLD | 72 | | | | | 72 |
| DOP | 104 | | | | | 104 |
| DSO | 44 | | | | | 44 |
| AIC | | 30 | 160 | | | 190 |
| AIO | | | 30 | 80 | | 110 |
| CUS | 30 | 6 | 18 | 8 | 10 | 72 |
| PRJ | 40 | 16 | 24 | 24 | 80 | 184 |
| ASM | 11 | 4 | 8 | 8 | 17 | 48 |
| SLK | 27 | 24 | 0 | 0 | 13 | 64 |
| **Phase total** | **400** | **80** | **240** | **120** | **120** | **960** |

### 1.4 Phase map

| Phase | Weeks (Days) | Purpose | Ends with |
|---|---|---|---|
| **A. Foundations** | 1–10 (1–50) | Software, AWS, containers, CI/CD, Terraform, Kubernetes, observability, DevSecOps. Customer thread starts Week 1. Projects P1 (Lift the spreadsheet), P2 (Report that is always wrong), P3 (Hostile legacy integration). | **G1** Day 40 (Week 8) · **G2** Day 50 (Week 10) |
| **B. Consolidate + AI on-ramp** | 11–12 (51–60) | Remediation window, P4 (Constrained environment), ML "just enough" and Python for AI. First two-week slack window (24 h). | **Mid-program review** Day 60 |
| **C1. AI Core** | 13–18 (61–90) | Prompting, tools, RAG, evals, context, fine-tuning decision, agents, MCP. Tracing and AI security seeded from Week 13. P5 (Document workflow with evals). | **G3** Day 90 |
| **C2. AI Operations** | 19–21 (91–105) | Enterprise integration, safe agents, open models, pipelines, multimodal, serving, reliability. P6 (Agent with tools). | **G4** Day 105 |
| **D. Customer + pod** | 22–24 (106–120) | P7 scoping sprint, embedded pod on real low-risk work, flagship P8, handover. | **Pod review** Day 115 · **G5** Day 120 |

### 1.5 Week at a glance

| Wk | Days | Phase | Theme | Main technical content | Customer thread / project | Gate |
|---|---|---|---|---|---|---|
| 1 | 1–5 | A | Onboard, baseline, ship | Shell, git, debugging, Python start, first AWS deploy, Docker intro | CL1 what an FDE is; Mom Test | **G0** (Day 2) |
| 2 | 6–10 | A | Python for ops, IAM, containers | Python HTTP client, Linux, IAM and S3, Docker, first CI | CL2 listening, stakeholder map | |
| 3 | 11–15 | A | Networks and compute | DNS/TLS/HTTP, EC2/ALB, CI/CD deep, Terraform first steps | CL3 nouns and verbs, 5 Whys | |
| 4 | 16–20 | A | Data, APIs, Terraform | SQL, API design, RDS, Terraform modules/state, SAST | CL4 scoping; **P1 kickoff** | |
| 5 | 21–25 | A | IaC and VPC | Terraform multi-env, VPC, Kubernetes concepts, container scans | CL5 status updates; P1 design | |
| 6 | 26–30 | A | **Consolidation week** | Code reading and review, AWS governance, K8s config; 11 h slack | CL6 decomposition; **P2 kickoff** | |
| 7 | 31–35 | A | Networking/IAM deep, K8s | Private networking, IAM policy, K8s workloads, Prometheus/Grafana/SLOs | CL7 JTBD interview; P1 deploy, P2 build | |
| 8 | 36–40 | A | **G1 week** | K8s HPA/rollouts, burn-rate alerts, game day 1, DAST | CL8 demo; P1 handover | **G1** (Day 40) |
| 9 | 41–45 | A | Serverless, K8s drills, security | Lambda/SQS, timed K8s troubleshooting, RBAC/NetworkPolicy, supply chain, STRIDE | CL9 scope negotiation; **P3** | |
| 10 | 46–50 | A | **G2 week** | FinOps, G2 artifacts, mock security review | CL10 CISO rehearsal; P3 close | **G2** (Day 50) |
| 11 | 51–55 | B | Constrained environment + ML basics | ML "just enough", async Python for AI; offline/residency | CL11 adversarial panel; **P4** | |
| 12 | 56–60 | B | Python for AI, mid-review | Tested data module, FastAPI; consolidation | CL12 bad news; P4 close | **Mid review** (Day 60) |
| 13 | 61–65 | C1 | Prompts, structured outputs, tools | T3 prompting, T4 tool loop, tracing first | CL13 define "good"; **P5 kickoff** | |
| 14 | 66–70 | C1 | RAG I and evals I | T5 baseline RAG, parsing; T6 error analysis, golden set | CL14 executive brief; P5 | |
| 15 | 71–75 | C1 | RAG II and evals II | Hybrid/rerank, ACL, RAG failures; judge calibration; cost | CL15 hostile evaluator; P5 | |
| 16 | 76–80 | C1 | CI evals, context, decisions | Regression gate, context engineering, prompt-vs-RAG-vs-FT; red-teaming | CL16 expectations; P5 | |
| 17 | 81–85 | C1 | LoRA and agents | LoRA lab, bounded agents, LangGraph | CL17 AI compliance conduct; P5 | |
| 18 | 86–90 | C1 | MCP and **G3 week** | Orchestrator-workers, MCP build/auth/threat model, privacy | CL18 G3 rehearsal; P5 | **G3** (Day 90) |
| 19 | 91–95 | C2 | Enterprise integration | OIDC/SSO + ACL, connectors, legacy adapters, HITL, agent threat model | CL19 adoption; **P6 kickoff** | |
| 20 | 96–100 | C2 | Open models, pipelines, multimodal | Local inference, vLLM, sizing, incremental pipelines, vision extraction | CL20 incident comms; P6 | |
| 21 | 101–105 | C2 | Production AI and **G4 week** | AI deployment, GPU, SLOs, failover; G4 simulation | CL21 customer during an incident; P6 close | **G4** (Day 105) |
| 22 | 106–110 | D | Scoping sprint, pod start | Three prospects, PR/FAQ; pod onboarding; flagship scope | CL22 panel defence; **P7**, P8 start | |
| 23 | 111–115 | D | Embedded pod | Real low-risk work; flagship sprint 1 | CL23 real stakeholder updates; P8 | **Pod review** (Day 115) |
| 24 | 116–120 | D | Flagship, handover, defence | Hardening, handover, runbook cold test | CL24 handover meeting, retro | **G5** (Day 120) |

### 1.6 Gate calendar

| Gate | Day | Week / day | Learner-hours (ASM block) | Domains | Assessors |
|---|---|---|---|---|---|
| G0 Baseline (diagnostic) | 2 | Wk 1, Tue (exam Mon PM) | 6 (counted in ONB) | all | Instructors |
| G1 Platform: rebuild from scratch | 40 | Wk 8, Fri | 5 | D1, D2 | 1 assessor + proctor |
| G2 Secure delivery review | 50 | Wk 10, Fri | 6 | D3, D2, D6 | **2 independent** |
| Mid-program review | 60 | Wk 12, Fri | 4 | all | 2 independent |
| G3 AI build | 90 | Wk 18, Fri | 8 | D4, D6 | 1 + external (calibrated) |
| G4 Operate under failure | 105 | Wk 21, Fri | 8 | D5, D3, D2 | **2 independent** |
| Pod review | 115 | Wk 23, Fri | 5 | D6, all | Mentor + client + 1 assessor |
| G5 Capstone defence and readiness panel | 120 | Wk 24, Fri | 12 | all | **4-person panel** |

Day-to-week mapping: Day d is in Week ⌈d/5⌉. There is no Week 0; Week 1 starts on Day 1 (Monday) **[Foundation §6.2]**. Two-assessor gates follow Foundation §6.8 (calibration on recorded examples; inter-assessor delta ≤1.0).

### 1.7 What this plan adds to the 12-week program

Compared against the 12-week budget and the deferral list in Foundation §7.2 and §7.5 (the 12-week plan document itself is written separately):

| Area | 12-week (Foundation) | 24-week (this plan) |
|---|---|---|
| Total hours | 480 | **960** |
| Software fundamentals / Cloud / DevOps / DevSecOps | 32 / 36 / 48 / 20 | **56 / 72 / 104 / 44**: reading unfamiliar code and code review, AWS networking and IAM in depth, FinOps, Terraform state and modules, full Kubernetes incl. timed troubleshooting drills, K8s and cloud security |
| AI Core | 100 | **190**: more repetition on prompting, RAG (36 h), evals (30 h), agents (26 h), MCP (14 h), plus a LoRA fine-tuning lab (T10, 16 h) |
| AI Operations & Security | 52 | **110**: multimodal (6 h, elective in 12-week), MLOps pipelines (10 h vs 2), open-model serving and sizing hands-on (12 h), K8s autoscaling and GPU serving hands-on (12 h), privacy drills, slice analysis |
| Customer Labs | 32 | **72** (weekly for 24 weeks), longer horizon: adversarial panels and "living client" over 12 weeks |
| Projects | 84 | **184**: P2 and P3 separate (folded in the 12-week); P4 stand-alone; P5, P6 twice as long; P7 scoping sprint; **embedded pod on real low-risk work (Weeks 22–23)** |
| Fault library | 32 scenarios | **All 40** (Foundation §9.6) |
| Gates | G0–G5 at Days 2/20/30/45/55/60 | G0–G5 at Days 2/40/50/90/105/120 **plus** Day-60 midpoint review and Day-115 pod review |
| Slack | 38 h | 64 h, including a two-week consolidation window (Weeks 11–12, 24 h) |
| Honest promise | "Ready to start under supervision" | "Near-independent on routine engagements" |
| Deferred in both | Specializations, certifications, other clouds, EU AI Act specifics | Same (Foundation §7.5) |

### 1.8 Conventions used in the weekly plans

**Ledger and IDs.** Every week has an **hours ledger**. Each row is one scheduled activity with an ID, a block code, a type and hours. The week totals 40 h. Block hours roll up to §1.3. IDs: `W{week}-{letter}{n}`: **O** onboarding, **I** instruction, **L** lab, **C** Customer Lab, **J** project session, **A** assessment, **S** slack. Lab IDs `W{week}-L{n}` replace the repo's inherited lab numbering, which collided across files (Foundation Appendix A #9).

| Type | Meaning |
|---|---|
| `INS` | Instruction: ≤30 min lecture, then worked example or live coding, then an interactive check. Counts toward the 15% instruction target. |
| `LAB` | Pair/trio lab or solo lab with auto-checks and rubric. Lab pass criteria are in each week's **Labs** table. |
| `PRJ` | Project session on a carried project (P1–P8). |
| `CUS` | Customer Lab: 30 min micro-lesson, 60 min drill, 60 min simulated client, 30 min debrief; one retry within 48 h. |
| `ASM` / `SLK` / `ONB` | Gate or review time / slack, remediation, consolidation / onboarding. |

Domain column: `D1`–`D6` per Foundation §3.2; `all` where cross-cutting.

**Daily rhythm** (Foundation §5.1): 09:00 stand-up and retrieval warm-up; 09:20–10:30 instruction; 10:30–12:30 pair/trio lab; 13:15–15:45 project or carried-system block; 15:45–16:45 review block (code review or incident drill, alternating); 16:45–17:30 lab continuation, office hours or remediation; 17:30–17:45 written reflection; **hard stop 17:45**. The day-by-day tables show the main activity in each part. Friday morning is the weekly checkpoint, demo and retrieval quiz (charged to the week's largest technical block).

**Customer Lab placement.** Odd weeks: Friday afternoon. Even weeks: Wednesday 13:15–16:15, leaving Friday afternoon for an incident drill (Wheel of Misfortune style) or lab continuation, which keeps the Foundation §5.2 alternation without losing the weekly Customer Lab **[Judgment]**.

**Instruction share.** Instruction rows are about 11.6% of hours; adding the 30-minute micro-lesson inside each Customer Lab gives about 12.8%, below the Foundation's 15% target. This is deliberate in the AI weeks, where labs are the learning, and it is reported honestly rather than adjusted. The realised split is computed in §5.2.

**AI lab rules** (Foundation P5, P6, P16): every AI lab ships with an eval and a one-paragraph "what the numbers say"; a lab does not pass without eval and trace evidence from Week 13. Direct API before frameworks. Model IDs live in config only. Every AI lab runs against two or more endpoints (a hosted frontier model plus an OpenAI-compatible hosted or local one). No real customer data, ever.

**AI coding assistants** **[Judgment: policy decision for the sponsor, see §8.5]**. Taught in W1-O5. Allowed in labs from Week 2; every line must be explainable in the daily review block. G0 and the oral defences in G1 and G2 are assistant-free. G3–G5 permit assistants as in the field, with commit-level attribution.

**Fault scenarios** are named in capitals (for example `NET-DNS`, `K8S-OOM`, `RAG-ACL`) and defined in Foundation §9.6. Each scenario has an enumerated stall-point list so the 40% stall rule can be computed.

**Carried customers** (Foundation §8.1): **Kestrel Freight** (commercial, cost-sensitive) in Phase A; **Linden Claims Services** (regulated) from Phase B onward, including the carried AI system (P5 → P6 → P8). Both are synthetic.

**Source labels in weekly plans.** Resource links come from the research notes. Links marked [U] were not fetched or verified there.

---

## 2. Weekly plans

Each week lists objectives, the hours ledger, a day-by-day table, what to teach and how, labs with pass criteria, the customer thread, the carried project, resources, stall points and an exit checklist. Weeks 6, 11 and 12 contain the larger slack allowances.

# Phase A — Foundations (Weeks 1–10, Days 1–50)

### Week 1 — Onboard, baseline, ship
*Phase A · Days 1–5 · **G0 baseline (Day 2)** · 40 h: ONB 16, SWF 14, CLD 4, DOP 3, CUS 3*

**Objectives.** By Friday the learner can:
1. Work in the shell and git daily (branch, PR, resolve a conflict) and read a stack trace.
2. Explain how this program runs: contract, gates, retake policy, hours, norms, how to ask for help.
3. Have shipped a small containerised service that answers an LLM-backed request, deployed on AWS by a pipeline.
4. Run a 15-minute discovery conversation using specific-past-event questions.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W1-O1 | Welcome, cohort contract, norms, wellbeing lead, trios assigned, accounts, `make verify` | ONB | ONB | all | 6 |
| W1-O2 | G0-a written baseline exam (60 questions) | ONB | ONB | all | 2 |
| W1-O3 | G0-b practical: broken environment (`G0-LAYERED`, three layered faults) | ONB | ONB | all | 3 |
| W1-O4 | G0-c mock discovery call with a Kestrel actor (recorded) | ONB | ONB | D6 | 1 |
| W1-O5 | AI-assisted development practice; how to ask for help and write a good issue | ONB | ONB | D1 | 4 |
| W1-I1 | Instruction: shell, git, editor, debugger | SWF | INS | D1 | 2 |
| W1-L1 | Shell and git workflow lab | SWF | LAB | D1 | 3 |
| W1-L2 | Debugging lab: logs, `pdb`, reading a stack trace | SWF | LAB | D1 | 3 |
| W1-I2 | Instruction: typed Python, pytest, pydantic basics | SWF | INS | D1 | 2 |
| W1-L3 | Python lab: a small CLI with tests | SWF | LAB | D1 | 4 |
| W1-L4 | Ship it I: AWS tour, CLI/SSO, deploy the starter service from a template | CLD | LAB | D2 | 4 |
| W1-L5 | Ship it II: containerise it, trigger CI, add the LLM-backed endpoint through the gateway | DOP | LAB | D2 | 3 |
| W1-C1 | Customer Lab 1: what an FDE is; Mom Test question rewrite; scripted-vague client | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM (09:20–12:30) | PM (13:15–15:45) | Review / craft (15:45–17:45) |
|---|---|---|---|
| Mon (1) | O1 welcome, contract, norms; I1 shell/git | O2 G0 exam (2 h); O1 accounts and `make verify` | Reflection template; first stand-up retro |
| Tue (2) | O3 G0 practical (3 h) | O4 mock discovery call; O5 AI assistants and asking for help | Gate G0 recorded; lane A/B/C and learning plan drafted by staff |
| Wed (3) | L1 shell and git lab (trios) | L2 debugging lab; Customer Lab not today (odd week: Fri) | Review block: swap and review each other's PRs |
| Thu (4) | I2 Python; L3 Python CLI | L4 Ship it I (AWS deploy) | Office hours: unblock AWS access |
| Fri (5) | Weekly checkpoint: demo what shipped; retrieval quiz (baseline) | L5 Ship it II; C1 Customer Lab 1 (15:15–17:45 after L5) | Blameless retro; anonymous pulse; expectations session recap |

**What to teach and how**
- **Norms and wellbeing.** State the Recurse-style social rules (no feigned surprise, no "well-actuallys", no back-seat driving, no subtle -isms) **[Sourced: R3]**; hard stop 17:45; the named wellbeing lead; the retake policy (Foundation §6.6) read aloud. Do this before G0 so the baseline is not a threat.
- **G0.** Diagnostic only, no pass/fail. The written score is overridden by the practical. Outputs: lane A/B/C and an Individual Learning Plan. Pre-brief: "troubleshooting is a series of failures; it is fine not to solve it" **[Sourced: R3, Google "play to learn"]**.
- **AI-assisted development (O5).** Demonstrate good and bad use; rule: you own every line; the daily review block spot-checks. Include HF's "how to ask for help / write a good issue" idea: reproduce, minimise, say what you tried **[Sourced: R1, HF chapter 8]**.
- **Shell/git/debugging.** Live-code a bug hunt; pair rotation (driver/navigator swap every 20–30 min) from the first lab.
- **Ship in week 1** (P2 principle). The template already holds the pieces; the learner's job is to connect them and understand each hop. Never reach for the console after the first deploy: it is the habit G1 will test.

**Labs: deliverables and pass criteria** (all [Judgment])

| ID | Deliverable | Pass criteria |
|---|---|---|
| W1-L1 | A repo with 3 merged PRs from a trio | 8/8 checklist tasks done from the shell; one merge conflict resolved without force-push; PR merged only with a passing check |
| W1-L2 | Debug log (3 seeded bugs) | Each bug located from logs or `pdb` within 90 min total; one-line root cause written for each |
| W1-L3 | Typed CLI with tests | ≥8 pytest cases (≥2 failure paths); ruff clean; input validated by a pydantic model |
| W1-L4 | Starter service live on AWS | Public `/health` returns 200; authenticated via SSO or short-lived credentials; gitleaks finds no keys in the repo |
| W1-L5 | Container + pipeline + LLM endpoint | CI runs on push and is green; `/ask` returns a model answer; **no model ID in code** (grep proves it); the same request succeeds against a second endpoint by config change only |

**Customer thread.** CL1: micro-lesson (what an FDE is and is not; the three Mom Test rules); drill: rewrite five bad questions into past-event questions; simulation: 15-minute scripted-vague call with the Kestrel COO actor (hidden "real problem" sheet); debrief and retry within 48 h; artifact: one-page problem statement. Rubric R1 (formative). The G0 mock call and this lab are the **baseline for the customer-skill measurement** (§6.1).
**Carried project.** None yet. The Week-1 service is the seed of P1.
**Resources.** MIT Missing Semester https://missing.csail.mit.edu/ [Sourced: R2] · Mom Test summary https://mtlynch.io/book-reports/the-mom-test/ (secondary summary) [Sourced: R4] · Hugging Face course (chapter on asking for help) https://huggingface.co/learn/llm-course/chapter1/1 [Sourced: R1] · AWS Free plan facts https://aws.amazon.com/free/ [Sourced: R2]
**Stall points and instructor notes.** Typical: SSO or CLI profile misconfiguration (pre-stage a test login in T−2); Docker daemon problems on locked-down laptops; learners hiding confusion. Watch the first reflection notes for "I don't know where to start" and reach out the same day (§6.3 early-warning script). Log hint counts from Day 1.
**Exit checklist.** [ ] G0 recorded and learning plan agreed [ ] contract signed [ ] service live and pipeline green [ ] `make verify` passes [ ] baseline retrieval quiz taken [ ] pulse survey done.

### Week 2 — Python for ops, IAM and S3, containers, first CI
*Phase A · Days 6–10 · 40 h: SWF 12, CLD 8, DOP 14, DSO 3, CUS 3*

**Objectives.** By Friday the learner can:
1. Write a typed, tested Python client that survives timeouts, retries and bad responses.
2. Explain IAM users, roles and policies and apply least privilege to an S3 use case.
3. Build, scan and publish a container image and drive it from a CI pipeline.
4. Keep secrets out of a repo.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W2-I1 | Instruction: type hints, pydantic, pytest fixtures, httpx | SWF | INS | D1 | 1 |
| W2-L1 | Python lab: resilient HTTP client (timeouts, retries with backoff, tests) | SWF | LAB | D1 | 7 |
| W2-I2 | Instruction: Linux processes, permissions, systemd, logs | SWF | INS | D1 | 1 |
| W2-L2 | Linux lab: permissions and process break-fix | SWF | LAB | D1 | 3 |
| W2-I3 | Instruction: regions/AZs, shared responsibility, IAM, S3 | CLD | INS | D2 | 1 |
| W2-L3 | IAM and S3 lab: roles, policies, bucket policies, presigned URLs | CLD | LAB | D2 | 7 |
| W2-I4 | Instruction: images, layers, Dockerfile, compose, ECR | DOP | INS | D2 | 1 |
| W2-L4 | Docker lab: multi-stage build, compose with Postgres, push to ECR, scan with Trivy | DOP | LAB | D2 | 8 |
| W2-I5 | Instruction: CI concepts and GitHub Actions | DOP | INS | D2 | 1 |
| W2-L5 | CI lab: test, build, push pipeline for the lab service | DOP | LAB | D2 | 4 |
| W2-I6 | Instruction: secrets and least privilege | DSO | INS | D3 | 1 |
| W2-L6 | Secrets lab: gitleaks pre-commit, AWS Secrets Manager (`SEC-SECRETS`) | DSO | LAB | D3 | 2 |
| W2-C1 | Customer Lab 2: active listening; stakeholder map; watch-someone-work | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (6) | I1; L1 Python client (trios) | L1 continues | Review block: code review of L1 PRs |
| Tue (7) | I2; L2 Linux break-fix | I3; L3 IAM and S3 | Incident drill 0: instructor-led (Breakage 0 style) on a Linux fault |
| Wed (8) | L3 continues | C2 Customer Lab 2 (13:15–16:15) | Office hours |
| Thu (9) | I4; L4 Docker lab | L4 continues | Code review of Dockerfiles |
| Fri (10) | Weekly checkpoint; demo; retrieval quiz | I5; L5 CI; I6; L6 secrets | Retro; pulse |

**What to teach and how**
- **Python for ops.** Worked example first: a client that fails safely. Then trios write the same client against a flaky local server; the test suite is the deliverable. Teach "boring, typed, tested" **[Sourced: R5 T2]**.
- **IAM.** Draw the policy-evaluation flow on a whiteboard; let learners write a too-broad policy, then narrow it using access-denied logs. Least privilege is a habit, not a lecture (P15).
- **Docker.** Show layer caching by breaking it. Scan with Trivy and read the CVE output together **[Sourced: R2, tool names [U]]**.
- **CI.** One concept per lab: pipeline = tests + build + push. Insist on a failing test blocking the push.
- **Secrets.** Show a leaked key in git history and what rotation costs.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W2-L1 | Python client + test suite | ≥12 pytest cases incl. timeout, 429, malformed JSON; retries use exponential backoff with jitter (verified from timestamps); ruff and mypy clean |
| W2-L2 | Linux fix log | 4/4 seeded problems fixed using only logs and `ps`/`ls -l`/`journalctl`; permissions fixed without `chmod 777` |
| W2-L3 | IAM role + S3 policy set | A role can read one prefix and nothing else; 6/6 negative tests (other prefix, other bucket, delete) return AccessDenied; presigned URL expires as set |
| W2-L4 | Image + compose stack | Multi-stage image ≤ a stated size budget (instructor sets, e.g. 50% of the naive image); runs as non-root; Trivy shows 0 critical on the final image; pushed to ECR |
| W2-L5 | CI pipeline | Green on a clean push; a deliberately failing test blocks the image push; pipeline time reported |
| W2-L6 | Secrets handling | gitleaks pre-commit blocks a planted key; app reads the secret from Secrets Manager; the planted key is rotated and the history is cleaned |

**Customer thread.** CL2: active listening and the 40% talk-ratio rule; build a stakeholder map; watch-someone-work: observe a role-played warehouse supervisor doing their job (video plus live questions). Artifact: stakeholder map. Rubric R1. Stage 1 simulation (scripted-vague, Weeks 1–10).
**Carried project.** P1 seed: the same service is rebuilt with real storage in Week 4.
**Resources.** CS50 Python https://cs50.harvard.edu/python/ [Sourced: R2] · Full Stack Open CI course https://courses.mooc.fi/org/uh-cs/courses/full-stack-open-continuous-integration [Sourced: R2; section list not read] · AWS SAA exam guide, used as syllabus only https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html [Sourced: R2] · OWASP Juice Shop (target for later weeks) https://owasp.org/www-project-juice-shop/ [Sourced: R2]
**Stall points and instructor notes.** IAM policy syntax; Docker build context; rate-limit confusion in L1. Pair mixed-experience trios; early finishers extend L1 with a circuit breaker. Instructor-led Incident drill 0 teaches the pager habit with no stakes.
**Exit checklist.** [ ] client tests green [ ] role passes all negative tests [ ] image in ECR, 0 critical CVEs [ ] pipeline green [ ] no secrets in history [ ] stakeholder map submitted.

### Week 3 — Networks, compute, CI/CD deep, Terraform first steps
*Phase A · Days 11–15 · 40 h: SWF 12, CLD 8, DOP 14, DSO 3, CUS 3*

**Objectives.** By Friday the learner can:
1. Debug DNS, TLS, proxy and MTU problems with `dig`, `curl`, `openssl` and `tcpdump`.
2. Run a load-balanced, auto-scaled web tier on EC2 behind an ALB.
3. Build a CI/CD pipeline with matrix tests, caching, protected environments and keyless AWS deploy.
4. Describe Terraform's plan/apply/state loop and codify a small stack.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W3-I1 | Instruction: TCP/IP, DNS, TLS, HTTP | SWF | INS | D1 | 2 |
| W3-L1 | Network debugging lab: `dig`, `curl`, `openssl` (`NET-DNS`, `NET-CA`) | SWF | LAB | D1 | 4 |
| W3-L2 | Web lab: reverse proxy, caching headers, certificate chain (`NET-PROXY`) | SWF | LAB | D1 | 3 |
| W3-L3 | Linux networking and load: `ss`, packet capture, load test (`NET-MTU`) | SWF | LAB | D1 | 3 |
| W3-I2 | Instruction: EC2, EBS, ALB, Auto Scaling | CLD | INS | D2 | 1 |
| W3-L4 | Compute lab: EC2 with SSM access, EBS snapshot restore, ALB + ASG with health checks | CLD | LAB | D2 | 7 |
| W3-I3 | Instruction: pipeline design; Terraform plan/apply/state | DOP | INS | D2 | 2 |
| W3-L5 | CI/CD lab: matrix tests, caching, artifacts, protected environments, OIDC keyless deploy | DOP | LAB | D2 | 8 |
| W3-L6 | Terraform first steps: codify the Week-2 IAM/S3 setup; remote state introduced | DOP | LAB | D2 | 4 |
| W3-I4 | Instruction: dependency and pre-commit hygiene | DSO | INS | D3 | 1 |
| W3-L7 | SCA and secrets in CI: dependency audit, gitleaks; fail build on high severity | DSO | LAB | D3 | 2 |
| W3-C1 | Customer Lab 3: nouns and verbs of a business; 5 Whys and its limits | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (11) | I1; L1 DNS/TLS debugging | L1 continues; L2 proxy and caching | Review block: L1 findings write-up |
| Tue (12) | L2; L3 Linux networking | I2; L4 EC2/ALB/ASG | Incident drill (Breakage 1: coach mode) on a `NET-*` variant |
| Wed (13) | L4 continues | I3; L5 CI/CD deep | Review: pipeline security (no long-lived keys) |
| Thu (14) | L5 continues | L6 Terraform first steps; I4; L7 SCA | Office hours |
| Fri (15) | Checkpoint, demo, quiz | C3 Customer Lab 3 (13:15–16:15) | Retro; pulse |

**What to teach and how**
- **Networking.** "Diagnosis by layer" worksheet: name, connect, TLS, HTTP, app. Seed three of the five `NET-*` fault variants; assign randomly per learner and log the stall point **[Repo: fault library design]**.
- **EC2/ALB/ASG.** Learners first click through the console once (to see the object model), then repeat with the CLI. This is the last time they use the console for provisioning.
- **CI/CD.** OIDC to AWS removes stored keys; show the failure when the trust policy is wrong **[Sourced: R2, Full Stack Open CI as method]**.
- **Terraform.** "Manual first, then automate" (Nana's order) **[Sourced: R2]**: they import the thing they already built by hand into code.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W3-L1 | Diagnosis log for 2 assigned faults | Each fault located to the correct layer with command evidence; fix applied; median time to first signal logged |
| W3-L2 | Proxy + cache config | Proxy forwards headers correctly; cached object returns `304`/hit on repeat; expired cert is detected and replaced |
| W3-L3 | Capture + load report | MTU fault located from a capture; load test shows p95 latency at 3 concurrency levels; one bottleneck named with evidence |
| W3-L4 | Web tier on AWS | ALB health checks drive traffic; killing an instance does not drop more than a stated number of requests (≤2 in a 60-s test); EBS snapshot restored and verified |
| W3-L5 | Pipeline | Matrix runs on 2 runtime versions; cache cuts build time ≥30%; deploy uses OIDC (no static keys in repo or secrets); production environment requires approval |
| W3-L6 | Terraform for IAM/S3 | `terraform plan` shows no diff after import; state is remote; re-apply is idempotent |
| W3-L7 | CI security gates | A known-vulnerable dependency and a planted secret each fail the build; both fixed and green |

**Customer thread.** CL3: map the nouns and verbs of the Kestrel business (shipments, pallets, manifests, claims); learn 5 Whys with its documented limits (branch it; verify each "why" with evidence) **[Sourced: R4 §2.5]**. Artifact: process map and one evidence-backed 5-Whys. Rubric R1/R3.
**Carried project.** P1 not yet started. The Terraform repo created here is the P1 repo.
**Resources.** MIT Missing Semester (networking, debugging) https://missing.csail.mit.edu/ [Sourced: R2] · Cloud Resume Challenge (end-to-end shape) https://cloudresumechallenge.dev/docs/the-challenge/ [Sourced: R2] · Terraform Associate review page, used as syllabus only https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004 [Sourced: R2, third-party-confirmed objectives] · KodeKloud learning paths (method reference) https://kodekloud.com/learning-path [Sourced: R2]
**Stall points and instructor notes.** The most common stall is reading the fault at the wrong layer (blaming the app for a DNS problem). OIDC trust policies fail silently; keep a pre-made "broken trust" example. Remind learners the console is retired for provisioning.
**Exit checklist.** [ ] 2 NET faults solved and logged [ ] ASG test passed [ ] pipeline uses OIDC [ ] Terraform state remote and idempotent [ ] SCA/secret gates in CI [ ] process map submitted.

### Week 4 — SQL, APIs, managed data, Terraform modules; P1 kickoff
*Phase A · Days 16–20 · 40 h: SWF 8, CLD 8, DOP 15, DSO 4, PRJ 2, CUS 3*

**Objectives.** By Friday the learner can:
1. Model data in SQL, read an `EXPLAIN`, and design a REST API with pagination and idempotent writes.
2. Run a managed Postgres (RDS) including a restore drill, and put HTTPS in front of a service.
3. Write Terraform with variables, modules and remote state, and run it from a pull request.
4. Run static analysis in CI and triage the findings.
5. Hold a discovery conversation with a real-seeming client and turn it into a one-page scope (P1).

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W4-I1 | Instruction: SQL, indexes, transactions; REST design, pagination, idempotency, OpenAPI | SWF | INS | D1 | 2 |
| W4-L1 | SQL lab: model Kestrel shipments, analytic queries, index with `EXPLAIN` | SWF | LAB | D1 | 3 |
| W4-L2 | API lab: FastAPI CRUD service on Postgres with idempotency keys | SWF | LAB | D1 | 3 |
| W4-I2 | Instruction: RDS, backups, Route 53, CloudFront, ACM | CLD | INS | D2 | 1 |
| W4-L3 | Managed data and edge lab: RDS restore drill; HTTPS via Route 53, CloudFront, ACM | CLD | LAB | D2 | 7 |
| W4-I3 | Instruction: Terraform variables, modules, remote state, workspaces | DOP | INS | D2 | 2 |
| W4-L4 | CI lab: pipeline runs `fmt`, `validate`, `plan` on pull requests | DOP | LAB | D2 | 4 |
| W4-L5 | Terraform lab: the web stack (ALB, ASG, RDS) from code with reusable modules | DOP | LAB | D2 | 9 |
| W4-I4 | Instruction: secure SDLC, SAST, review checklist | DSO | INS | D3 | 1 |
| W4-L6 | SAST lab: Semgrep in CI, triage seeded findings, branch protection | DSO | LAB | D3 | 3 |
| W4-J1 | **P1 kickoff**: discovery calls with the Kestrel COO and warehouse supervisor | PRJ | PRJ | D6 | 2 |
| W4-C1 | Customer Lab 4: scoping; turn notes into a one-page scope (answer-first) | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (16) | I1; L1 SQL | L1 continues; I2 | Review block: SQL review of two peers |
| Tue (17) | L2 API lab | J1 P1 discovery calls (live, recorded) | Debrief of discovery notes |
| Wed (18) | I3; L3 managed data and edge | C4 Customer Lab 4 (13:15–16:15) | Office hours |
| Thu (19) | L4 CI plan-on-PR; L5 Terraform | L5 continues | Code review of Terraform modules |
| Fri (20) | Checkpoint, demo, quiz; I4 | L6 SAST; | Incident drill: `APP-RACE`-style API bug (lab continuation); retro; pulse |

**What to teach and how**
- **SQL and API.** One shared dataset (synthetic Kestrel shipments, ~50k rows). Insist on migrations and an OpenAPI spec the client could read. Teach idempotency as "what happens when the same request arrives twice" with a replay test.
- **RDS and edge.** Provide a Terraform module for RDS to read and modify; the restore drill is the point: a backup you never restored is not a backup.
- **Terraform.** Modules and remote state with locking; run `plan` in CI and read the plan together. Use the Week-3 repo.
- **SAST triage.** Show that most findings are decisions, not bugs: fix, accept with rationale, or suppress with an expiry **[Sourced: R2, OWASP DevSecOps guideline method]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W4-L1 | Schema, queries, index report | Schema has keys and constraints; 8/8 analytic queries return expected results on a seeded DB; one slow query fixed with an index and `EXPLAIN` confirms use (≥10× faster) |
| W4-L2 | API service | OpenAPI schema generated; cursor pagination works; replaying a `POST` with the same idempotency key creates exactly one record; 12/12 contract tests pass |
| W4-L3 | RDS drill + HTTPS | Point-in-time restore recovers a deleted row, verified by query; service reachable over HTTPS with a valid certificate and HTTP redirects to HTTPS |
| W4-L4 | PR pipeline | Every PR runs `fmt`, `validate`, `plan`; plan visible on the PR; `apply` runs only from `main` after approval |
| W4-L5 | Web stack in code | Full stack applied in a fresh sandbox account in ≤30 min; remote state with locking (a second concurrent apply is blocked); 0 hard-coded secrets |
| W4-L6 | SAST triage | 5 seeded findings: 3 fixed, 2 documented as false positives with rationale; merge blocked on failure; CODEOWNERS enforced |

**Customer thread.** CL4: scoping lab. Micro: answer-first writing (Minto/SCQA) **[Sourced: R4 §2.4]**. Drill: compress discovery notes to one page. Simulation: a follow-up call with the Kestrel IT lead (second persona). Artifact: **P1 scope one-pager** (user, decision, metric, constraints, out of scope, riskiest assumption); submitted Friday, retry window to Monday. Rubric R2.
**Carried project: P1 "Lift the spreadsheet" (Kestrel) kicks off.** Kestrel's inbound dock team runs truck-appointment slots from a shared spreadsheet and email. P1 replaces it with a minimal, secured dock-slot tracker (service, auth, backups, cost cap, runbook). The technical labs of Weeks 3–8 produce its building blocks **[Judgment]**.
**Resources.** Terraform Associate review (syllabus only) https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004 [Sourced: R2] · OWASP DevSecOps Guideline https://owasp.org/www-project-devsecops-guideline/ [Sourced: R2] · Minto pyramid https://managementconsulted.com/pyramid-principle/ [Sourced: R4] · AWS Budgets controls (for later weeks) https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-controls.html [Sourced: R2]
**Stall points and instructor notes.** Terraform state locks and provider auth; learners writing monolithic Terraform (push for modules). Restore drills reveal that people never tested backups; allow the failure and debrief it.
**Exit checklist.** [ ] queries and index report done [ ] idempotency replay test green [ ] restore drill verified [ ] PR pipeline live [ ] SAST gate blocking [ ] P1 scope submitted.

### Week 5 — Terraform at scale, VPC, Kubernetes concepts, supply chain
*Phase A · Days 21–25 · 40 h: SWF 4, CLD 8, DOP 19, DSO 4, PRJ 2, CUS 3*

**Objectives.** By Friday the learner can:
1. Clean messy data into a validated store with tests and a quarantine path.
2. Design a VPC (public/private subnets, NAT, endpoints, flow logs) and predict reachability.
3. Structure Terraform for multiple environments, detect drift and import existing resources.
4. Deploy a service on a local Kubernetes cluster and debug a broken manifest.
5. Produce an SBOM and gate a pipeline on container vulnerabilities.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W5-I1 | Instruction: dirty data, validation, quarantine | SWF | INS | D1 | 1 |
| W5-L1 | Data lab: messy CSV/Excel to validated Parquet/Postgres with tests | SWF | LAB | D1 | 3 |
| W5-I2 | Instruction: VPC design, subnets, NAT, endpoints, flow logs | CLD | INS | D2 | 1 |
| W5-L2 | VPC lab: design, build, predict and test reachability | CLD | LAB | D2 | 7 |
| W5-I3 | Instruction: Terraform modules, multi-env layout, testing, drift | DOP | INS | D2 | 2 |
| W5-L3 | Terraform lab: dev and stage from one module set; `IAC-DRIFT` | DOP | LAB | D2 | 8 |
| W5-L4 | Terraform lab: import hand-made resources; tagging policy; clean destroy | DOP | LAB | D2 | 4 |
| W5-I4 | Instruction: Kubernetes concepts (pods, deployments, services) | DOP | INS | D2 | 1 |
| W5-L5 | Kubernetes lab 1: kind cluster, deploy the service, debug a broken manifest | DOP | LAB | D2 | 4 |
| W5-I5 | Instruction: supply chain, SBOM, image scanning, signing concept | DSO | INS | D3 | 1 |
| W5-L6 | Supply-chain lab: SBOM (CycloneDX), CVE gate, pinned base image | DSO | LAB | D3 | 3 |
| W5-J1 | **P1 design review**: IaC plan, auth, backups, cost cap, with mentor | PRJ | PRJ | D2 | 2 |
| W5-C1 | Customer Lab 5: answer-first status update; estimation and risk register | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (21) | I1; L1 data lab | L1 continues; I2 | Review: data tests |
| Tue (22) | L2 VPC lab | L2 continues | Incident drill (Breakage 1): VPC reachability break-fix |
| Wed (23) | I3; L3 Terraform multi-env | L3 continues (`IAC-DRIFT`) | Office hours |
| Thu (24) | L4 import and cleanup; I4 | L5 Kubernetes lab 1 | Code review: module interfaces |
| Fri (25) | Checkpoint, demo, quiz; I5; L6 supply chain | C5 Customer Lab 5 (13:15–16:15) | J1 P1 design review (16:15–17:15); retro; pulse |

**What to teach and how**
- **Data cleaning.** Reconciliation rule: rows in = rows out + rows quarantined. This is also the root of P2's "report that is always wrong".
- **VPC.** Predict first: learners fill a reachability matrix before running tests; wrong predictions are the learning event.
- **Terraform at scale.** Show drift: change a resource in the console deliberately (the last allowed console change), then let `plan` find it. Cleanup discipline: tags `cohort`, `learner`, `lab_id` on everything; untagged resources get reaped **[Repo; Foundation §9.2]**.
- **Kubernetes.** Local `kind` first (cost control). Teach `kubectl describe`/`logs` as the first move, not the last **[Judgment; Foundation §9.2]**.
- **Supply chain.** An SBOM is only useful if it matches the deployed digest; teach pinning by digest.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W5-L1 | Validated data pipeline | ≥10 pytest cases incl. 3 malformed inputs; schema checked by pandera or pydantic; rows in = out + quarantined, with reasons |
| W5-L2 | VPC | Reachability matrix 8/8 correct on prediction-then-test; private instance reaches the internet only through NAT; flow logs show a blocked attempt |
| W5-L3 | Multi-env Terraform | Dev and stage from one module set with different inputs; static IaC scan clean [U tool]; `IAC-DRIFT` found by `plan` and reconciled without data loss |
| W5-L4 | Import and cleanup | 3 hand-made resources imported with no `plan` diff; after `destroy` a tag query returns 0 resources for the learner |
| W5-L5 | Service on kind | Pod deleted recovers ≤30 s; broken manifest fixed from `describe`/`logs` evidence in ≤20 min; `port-forward` test passes |
| W5-L6 | SBOM + gate | SBOM generated and matches the image digest; CI fails on a critical CVE and passes after fix; base image pinned by digest |

**Customer thread.** CL5: write a three-line, bottom-line-first status update; estimate P1 with a risk register (probability, impact, owner). Simulation: present the status to the Kestrel COO actor in 3 minutes. Artifact: weekly status. Rubric R5.
**Carried project.** P1 design review with mentor (J1): confirm scope, the IaC layout, auth choice (managed identity service or OIDC proxy [Judgment]), backup and cost-cap plan.
**Resources.** Kubernetes docs https://kubernetes.io/docs/home/ [U, not fetched in R5] · Kubernetes the Hard Way (read, do not run in full) https://github.com/kelseyhightower/kubernetes-the-hard-way [Sourced: R2] · Linux Foundation Intro to Kubernetes (free) https://training.linuxfoundation.org/training/introduction-to-kubernetes/ [Sourced: R2] · aws-nuke (verify safety features before use) https://github.com/ekristen/aws-nuke [Sourced: R2]
**Stall points and instructor notes.** CIDR planning mistakes; Terraform import syntax; `kind` networking on corporate laptops. Run `aws-nuke` in dry-run first and verify its alias and dry-run safety features on the current release before any live nightly run (R2 could not confirm them).
**Exit checklist.** [ ] data pipeline reconciles [ ] reachability 8/8 [ ] dev and stage applied [ ] imports clean [ ] service on `kind` [ ] SBOM gate live [ ] P1 design reviewed.

### Week 6 — Consolidation week: code reading, AWS governance, Kubernetes config; P2 kickoff
*Phase A · Days 26–30 · 40 h: SWF 6, CLD 8, DOP 4, CUS 3, PRJ 8, SLK 11*

**Objectives.** By Friday the learner can:
1. Read an unfamiliar service and explain how it works; give a code review that teaches.
2. Query CloudTrail, set alarms, enforce a permission boundary and a budget alert.
3. Configure Kubernetes workloads with ConfigMaps, Secrets and Ingress; fix two assigned faults.
4. Decompose a vague problem aloud (issue tree) and observe a user's real workflow (P2).
5. Close gaps from Weeks 1–5 using the 11 h of ring-fenced slack.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W6-I1 | Instruction: reading unfamiliar code; reviews that teach | SWF | INS | D1 | 2 |
| W6-L1 | Code reading and review lab (`APP-RACE` seeded) | SWF | LAB | D1 | 4 |
| W6-I2 | Instruction: CloudTrail, CloudWatch, Organizations, billing; IAM policy evaluation | CLD | INS | D2 | 1 |
| W6-L2 | AWS governance lab: audit trail, alarms, permission boundary, budget action (`SEC-ROOT`) | CLD | LAB | D2 | 7 |
| W6-I3 | Instruction: Kubernetes config, secrets, services, ingress | DOP | INS | D2 | 1 |
| W6-L3 | Kubernetes lab 2: config, secrets, ingress; `K8S-IMGPULL`, `K8S-CRASHLOOP` | DOP | LAB | D2 | 3 |
| W6-J1 | P1 build session: auth, backups, cost cap | PRJ | PRJ | D2 | 2 |
| W6-J2 | **P2 kickoff**: interview the Kestrel finance analyst; watch the report being built | PRJ | PRJ | D6 | 2 |
| W6-J3 | P2 data tracing: provenance of the on-time-delivery KPI | PRJ | PRJ | D1 | 4 |
| W6-C1 | Customer Lab 6: decomposition drill (issue tree), narrated and recorded | CUS | CUS | D6 | 3 |
| W6-S1 | Consolidation clinic: retrieval review of Weeks 1–5; lab backlog; remediation plans | SLK | SLK | all | 6 |
| W6-S2 | Retro, wellbeing check, learning-plan update | SLK | SLK | all | 2 |
| W6-S3 | Open lab and mentor 1:1 block | SLK | SLK | all | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (26) | I1; L1 code reading | L1 continues; J1 P1 build | Review block: peer reviews |
| Tue (27) | I2; L2 AWS governance | L2 continues | Incident drill (Breakage 2: guide on the side) on K8s |
| Wed (28) | I3; L3 Kubernetes lab 2 | C6 Customer Lab 6 (13:15–16:15) | Office hours |
| Thu (29) | J2 P2 interview with finance analyst | J3 P2 data tracing | S3 open lab |
| Fri (30) | Checkpoint, demo, quiz | S1 consolidation clinic; S2 retro | Pulse; hours audit (logged vs scheduled) |

**What to teach and how**
- **Reading code.** Learners write "how it works" before running anything, then compare against a reference. Reviews teach when they explain the *why* **[Sourced: R3 #10, evidence C]**.
- **AWS governance.** Audit trail first ("who did what, when"); permission boundaries as the guardrail for delegated admins; cost controls as a living part of the platform, not a bill surprise.
- **Decomposition.** Palantir-style narrated decomposition: clarify user and decision, prioritise by value and risk, model entities, find a first executable slice, plan iteration **[Sourced: R4 §2.3; candidate-reported format]**. Keep it a tool, not ceremony.
- **Consolidation.** The clinic is led by learner requests. Check hours logged versus scheduled; anyone above 44 h median is followed up **[Foundation §12.4]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W6-L1 | Reviews + system explanation | ≥5 of 6 planted defects found (incl. a race and a security issue) with evidence and a suggested fix; "how it works" matches a reference on ≥80% of key facts |
| W6-L2 | Governance setup | CloudTrail query identifies the actor of a planted deletion (a root-account action, `SEC-ROOT`) and the root login is replaced by a role; an alarm fires on a synthetic error rate; a $1 test budget triggers its action; permission boundary blocks 4/4 out-of-scope actions |
| W6-L3 | Config on Kubernetes | ConfigMap and Secret mounted (secret not in image or manifest in plain text); Ingress routes two paths; `K8S-IMGPULL` and `K8S-CRASHLOOP` each fixed from evidence in ≤20 min |

**Customer thread.** CL6: issue tree on a vague ask ("deliveries are always late"); 45-minute narrated decomposition, recorded; self-score against R3. Artifact: decomposition recording. **This recording is the early point of the customer-skill delta** (§6.1).
**Carried projects.** P1 build (auth, backups, cost cap). **P2 "The report that is always wrong" starts:** Kestrel's finance analyst owns an on-time-delivery KPI that the COO distrusts. Observe and trace; do not build yet.
**Resources.** Google SRE book (engagement and training chapters) https://sre.google/books/ [Sourced: R2] · Palantir-style decomposition write-ups (candidate-reported) https://www.tryexponent.com/blog/decomposition-interview [Sourced: R4; commercial source] · Issue trees https://managementconsulted.com/management-consulting/issue-trees-what-are-they-how-to-use-them/ [Sourced: R4]
**Stall points and instructor notes.** Learners treat a slack week as a day off; make the clinic content visible on Monday. Some will over-structure the issue tree. Staff the open-lab block with the lab engineer for platform questions.
**Exit checklist.** [ ] backlog labs closed or planned [ ] governance lab passed [ ] two K8s faults fixed [ ] P2 interview notes and data provenance map [ ] decomposition recorded [ ] hours audit done.

### Week 7 — Private networking and IAM, Kubernetes workloads, observability; P1 deploy, P2 build
*Phase A · Days 31–35 · 40 h: CLD 8, DOP 17, DSO 3, PRJ 9, CUS 3*

**Objectives.** By Friday the learner can:
1. Run a private workload with no NAT using VPC endpoints; write IAM policies with conditions and assume roles across accounts.
2. Operate a stateful workload on Kubernetes with probes, resource limits and rolling updates; package it with Helm and Kustomize.
3. Define SLIs and three SLOs, build dashboards, and alert on a synthetic failure.
4. Gate infrastructure code with scans and policy-as-code.
5. Interview a user with the Jobs-to-be-Done timeline and ship P2's validated pipeline.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W7-I1 | Instruction: private networking, endpoints, IAM conditions, boundaries, cross-account roles | CLD | INS | D2 | 2 |
| W7-L1 | AWS networking and IAM deep lab (`NET-IPV6` variant) | CLD | LAB | D2 | 6 |
| W7-I2 | Instruction: Kubernetes workloads, storage, scheduling, requests and limits, Helm, Kustomize | DOP | INS | D2 | 2 |
| W7-L2 | Kubernetes lab 3: stateful workload, probes, rolling updates (`K8S-OOM`) | DOP | LAB | D2 | 5 |
| W7-L3 | Kubernetes lab 4: Helm chart and Kustomize overlays for P1 (`K8S-NETPOL-DNS`) | DOP | LAB | D2 | 5 |
| W7-I3 | Instruction: Prometheus, Grafana, OpenTelemetry; SLIs and SLOs | DOP | INS | D5 | 1 |
| W7-L4 | Observability lab: instrument P1, dashboards, three SLOs, alerts | DOP | LAB | D5 | 4 |
| W7-I4 | Instruction: IaC scanning and policy-as-code | DSO | INS | D3 | 1 |
| W7-L5 | IaC scan and policy gate lab (`SEC-UNENCRYPTED`) | DSO | LAB | D3 | 2 |
| W7-J1 | P1 deploy: secure deployment through the pipeline; backup restore drill; cost cap live | PRJ | PRJ | D2 | 3 |
| W7-J2 | P2 build: validated pipeline and data-quality checks (`DATA-SILENT` seeded) | PRJ | PRJ | D1 | 6 |
| W7-C1 | Customer Lab 7: JTBD timeline interview ("the last time this report was wrong") | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (31) | I1; L1 networking and IAM | L1 continues; J2 P2 build | Review block: IAM policy reviews |
| Tue (32) | I2; L2 stateful Kubernetes | L2 continues; L3 Helm/Kustomize | Incident drill (Breakage 2): `K8S-OOM` |
| Wed (33) | L3 continues | I3; L4 observability | Office hours |
| Thu (34) | L4 continues; I4; L5 IaC gate | J1 P1 secure deploy; J2 P2 build | Code review: Helm charts |
| Fri (35) | Checkpoint, demo, quiz | C7 Customer Lab 7 (13:15–16:15) | Retro; pulse |

**What to teach and how**
- **Private networking and IAM.** Remove NAT and make the workload still work: learners discover which calls need endpoints. IAM conditions (for example "only through this VPC endpoint") show least privilege beyond actions and resources.
- **Kubernetes workloads.** Lecture ≤30 min, then a live demo of killing the stateful pod. Requests and limits are the key idea behind `K8S-OOM`. Teach reading events before logs.
- **Observability.** SLI first, SLO second, alert third. Burn-rate alerting is introduced next week. Start from the Google SRE workbook chapters on SLOs **[Sourced: R2]**.
- **JTBD timeline.** Reconstruct a real recent event (the last time the report was wrong): first thought, passive looking, event, active looking, decision; note the four forces (push, pull, anxiety, habit). The anxiety and habit forces predict adoption risk **[Sourced: R4 §2.2; commercial source]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W7-L1 | Private networking and IAM stack | Private workload reads S3 and Secrets Manager with NAT removed; 6/6 IAM negative tests incl. a source-VPC-endpoint condition; cross-account role works with an external ID and fails without it; `NET-IPV6` fault diagnosed in ≤25 min |
| W7-L2 | Stateful service on Kubernetes | Data survives deletion of the pod; a rolling update under a 2-minute load test drops 0 requests; `K8S-OOM` diagnosed from events and fixed with justified requests and limits |
| W7-L3 | Helm chart + overlays | P1 installs in `dev` and `stage` overlays; secrets are not in values files; `K8S-NETPOL-DNS` (DNS blocked by a policy) fixed from evidence in ≤20 min |
| W7-L4 | Dashboards, SLOs, alerts | RED-metric dashboard live; 3 SLOs with stated SLIs and error budgets; an alert fires within 5 min of a synthetic failure and clears after the fix |
| W7-L5 | IaC gate | 8 seeded misconfigurations fixed; the policy gate blocks 3/3 violating PRs (public bucket, open `0.0.0.0/0` rule, unencrypted volume) [scan and policy tool names [U]] |

**Customer thread.** CL7: the JTBD timeline interview with the Kestrel finance analyst actor, 45 minutes, recorded. Artifact: timeline and four-forces sheet. Rubric R1/R3. Retry within 48 h.
**Carried projects.** *P1:* deployed through the pipeline with a restore drill and cost cap. *P2:* a validated pipeline reproduces the KPI and exposes the schema-versus-meaning gap (in this synthetic case "delivered" counts the dock scan, not the customer signature) **[Judgment, synthetic]**.
**Resources.** Google SRE workbook (SLOs, alerting) https://sre.google/workbook/table-of-contents/ [Sourced: R2] · JTBD switch interview https://jobstobedone.org/switch-interview/ and timeline https://jobstobedone.org/the-timeline/ [Sourced: R4; commercial] · Kubernetes docs https://kubernetes.io/docs/home/ [U] · roadmap.sh DevOps (overview) https://roadmap.sh/devops [Sourced: R2]
**Stall points and instructor notes.** VPC endpoint policy syntax; Helm value precedence; learners alerting on causes rather than symptoms. Log the first-signal time in L2 (`time_to_first_signal`).
**Exit checklist.** [ ] networking and IAM lab passed [ ] stateful app survives pod loss [ ] chart deploys in two overlays [ ] 3 SLOs alerting [ ] policy gate blocking [ ] P1 deployed and restored once [ ] P2 pipeline reproduces the KPI.

### Week 8 — G1 week: Kubernetes autoscaling, SRE practice, game day 1, DAST
*Phase A · Days 36–40 · **G1 Platform: rebuild from scratch (Day 40)** · 40 h: CLD 8, DOP 14, DSO 3, PRJ 3, ASM 5, SLK 4, CUS 3*

**Objectives.** By Friday the learner can:
1. Grant humans access through SSO roles only and operate managed databases (restore, parameters).
2. Autoscale and safely roll out on Kubernetes; diagnose missing-metrics autoscaling faults.
3. Take part in an incident under a blameless format: detect, mitigate, write a postmortem.
4. Run a dynamic scan against a deliberately vulnerable app inside a pipeline.
5. **Pass G1:** rebuild a working, observable, containerised service from scratch via IaC and CI in a fresh sandbox.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W8-I1 | Instruction: SSO and role-based human access; RDS operations | CLD | INS | D2 | 2 |
| W8-L1 | Access and data operations lab: SSO roles only, RDS point-in-time restore, parameter groups | CLD | LAB | D2 | 6 |
| W8-I2 | Instruction: Kubernetes HPA, probes, rollouts, disruption budgets | DOP | INS | D2 | 2 |
| W8-L2 | Kubernetes lab 5: HPA under load, disruption budget (`K8S-HPA-NOMETRICS`) | DOP | LAB | D2 | 5 |
| W8-I3 | Instruction: burn-rate alerting, incident response, safe fault injection | DOP | INS | D5 | 1 |
| W8-L3 | Game day 1 (`GAMEDAY-1`): Wheel of Misfortune on the Kestrel stack, then a blameless postmortem | DOP | LAB | D5 | 6 |
| W8-I4 | Instruction: DAST in the pipeline | DSO | INS | D3 | 1 |
| W8-L4 | DAST lab: scan a deliberately vulnerable app in CI and triage | DSO | LAB | D3 | 2 |
| W8-J1 | P1 demo and handover to the Kestrel IT lead; runbook cold-test by a peer | PRJ | PRJ | D6 | 3 |
| W8-A1 | **G1**: two timed stages, artifact submission, debrief | ASM | ASM | D2 | 5 |
| W8-S1 | Mock G1 on a different fault variant (practice, ungraded) | SLK | SLK | D2 | 4 |
| W8-C1 | Customer Lab 8: demo craft; "what it cannot do" page | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (36) | I1; L1 access and data operations | L1 continues; J1 P1 handover prep | Review block: runbook swap |
| Tue (37) | S1 mock G1 (ungraded) | I2; L2 HPA lab | Debrief of the mock |
| Wed (38) | L2 continues; I3 | C8 Customer Lab 8 (13:15–16:15) | Office hours: G1 questions |
| Thu (39) | Checkpoint, demo, quiz (moved up for G1 day); I4; L4 DAST | L3 game day 1 (13:15–17:15 incl. blameless debrief); J1 handover (cold test) | Reflection |
| Fri (40) | **G1 stage A (60 min)**, **stage B (45 min)** | Artifact upload, debrief, results same day | Retro; pulse; gate-health numbers logged |

**What to teach and how**
- **SSO access.** Why long-lived IAM users are a liability; show a credential report before and after.
- **Autoscaling.** Fault first: HPA with no metrics server. Then correct the cause, then discuss queue-depth versus CPU signals (revisited for AI services in Week 21).
- **Game day 1.** Pre-brief: "troubleshooting is a series of failures; it is fine not to solve it" **[Sourced: R3]**. Pre-approve fault templates and set stop conditions tied to alarms before injection (AWS FIS guidance) **[Sourced: R2]**. A role-played Kestrel COO demands status during the game day (non-engineer voice). Debrief with an Etsy-style facilitator; the postmortem is authored by the learners, not dumped on one person **[Sourced: R3]**.
- **G1 prep.** The mock uses a different fault variant than the real G1 so memory is not what is tested (P10).

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W8-L1 | Access and data operations | No IAM users with console access (credential report empty); trio uses SSO roles; RDS snapshot restored and verified in ≤15 min; cost-allocation tag report produced |
| W8-L2 | Autoscaling + disruption budget | HPA scales 1→4 under load and back within 10 min; the budget stops draining the last replica; `K8S-HPA-NOMETRICS` fixed from evidence in ≤20 min |
| W8-L3 | Game day 1 + postmortem | 3 injected faults; median time to detection ≤5 min from alerts; timeline per incident; blameless postmortem with ≥3 action items; stop conditions configured before injection |
| W8-L4 | DAST in CI | Baseline scan of the vulnerable app runs in the pipeline; ≥5 findings triaged with severity and rationale; the gate fails on high severity |

**Customer thread.** CL8: demo craft. Micro: narrative (problem → result → how), tailored to the audience; drill: a "what it cannot do" page; simulation: demo P1 to the Kestrel COO actor, who interrupts and asks "what happens if the sponsor's data is wrong?". Artifact: recorded 5-minute demo. Rubric R4. Retry within 48 h (Monday).
**Carried project.** P1 closes: demo, handover and a runbook that a peer who did not build it can use to deploy, monitor and roll back in ≤45 min (the fresh-eyes cold test) **[Sourced: R4 §2.9, SRE handover method]**.
**G1 (Day 40).** See §3.2 for format and pass criteria. Two stages: A (60 min, repo criteria) and B (45 min, Kubernetes and autoscaling add-on).
**Resources.** AWS Fault Injection Service https://docs.aws.amazon.com/fis/latest/userguide/what-is.html [Sourced: R2] · LitmusChaos https://litmuschaos.io/ [Sourced: R2] · Wheel of Misfortune scenarios https://github.com/dastergon/wheel-of-misfortune [Sourced: R3] · Etsy debriefing guide https://codeascraft.com/2016/11/17/debriefing-facilitation-guide/ [Sourced: R3] · SRE book on training on-call https://sre.google/sre-book/accelerating-sre-on-call/ [Sourced: R3] · Juice Shop https://owasp.org/www-project-juice-shop/ [Sourced: R2]
**Stall points and instructor notes.** Fault injection requires the lab engineer present; never run FIS outside pre-approved templates. Watch pre-G1 anxiety: restate that a first miss triggers remediation, not exit (Foundation §6.6). Calibrate the G1 assessor on a recorded example before Friday.
**Exit checklist.** [ ] G1 attempted and result recorded [ ] game-day postmortem filed [ ] P1 handover signed off by the actor [ ] DAST gate in the pipeline [ ] remediation plan agreed if needed.

### Week 9 — Serverless and queues, Kubernetes drills, security depth; P3 kickoff
*Phase A · Days 41–45 · 40 h: CLD 8, DOP 4, DSO 12, PRJ 8, SLK 5, CUS 3*

**Objectives.** By Friday the learner can:
1. Build an event-driven path with Lambda, queues and dead-letter handling; make consumers idempotent.
2. Solve timed Kubernetes troubleshooting tasks with a repeatable method.
3. Enforce least privilege and default-deny networking in Kubernetes; sign and verify images.
4. Produce a STRIDE threat model with a data-flow diagram.
5. Design a resilient adapter to a hostile legacy system (P3) and negotiate scope when a requirement changes.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W9-I1 | Instruction: Lambda, API Gateway, SQS, SNS, EventBridge; idempotent consumers | CLD | INS | D2 | 2 |
| W9-L1 | Serverless and queues lab: events, dead-letter queues, idempotent consumer | CLD | LAB | D2 | 6 |
| W9-I2 | Instruction: the Kubernetes troubleshooting method (symptom, events, logs, config) | DOP | INS | D2 | 1 |
| W9-L2 | Kubernetes timed drills (`K8S-WEBHOOK-CERT`, `K8S-DISKPRESSURE`, `K8S-PVC-TERM`, `K8S-WEBHOOK-REJECT`) | DOP | LAB | D2 | 3 |
| W9-I3 | Instruction: Kubernetes and cloud security (RBAC, NetworkPolicy, pod security), STRIDE | DSO | INS | D3 | 3 |
| W9-L3 | Kubernetes security lab: least-privilege RBAC and default-deny (`SEC-RBAC`, `SEC-NETPOL-OPEN`) | DSO | LAB | D3 | 3 |
| W9-L4 | Supply-chain lab: sign images in CI, verify at admission | DSO | LAB | D3 | 3 |
| W9-L5 | Threat-model workshop: STRIDE and data-flow for the P3 integration | DSO | LAB | D3 | 3 |
| W9-J1 | **P3 kickoff**: legacy warehouse system, flaky SOAP API, fixed batch windows; adapter design | PRJ | PRJ | D1 | 4 |
| W9-J2 | P3 build: adapter core, retries, idempotency keys | PRJ | PRJ | D1 | 4 |
| W9-S1 | G1 remediation window: targeted plans, parallel-task rehearsal | SLK | SLK | D2 | 3 |
| W9-S2 | Retrieval quiz and clinic (items from 1, 3, 6 weeks earlier) | SLK | SLK | all | 2 |
| W9-C1 | Customer Lab 9: scope negotiation; the client adds work | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (41) | I1; L1 serverless and queues | L1 continues; J1 P3 kickoff | Review block: event-flow reviews |
| Tue (42) | I2; L2 timed K8s drills | J1 P3 design; I3 | Incident drill (Breakage 2) on a K8s drill variant |
| Wed (43) | L3 K8s security | L4 supply chain | S1 remediation sessions (G1 retakers) |
| Thu (44) | L5 threat-model workshop | J2 P3 build | S2 quiz and clinic |
| Fri (45) | Checkpoint, demo, quiz | C9 Customer Lab 9 (13:15–16:15) | Retro; pulse |

**What to teach and how**
- **Queues.** "At-least-once delivery means your consumer must tolerate repeats": the replay test proves it. A poison message is how you teach dead-letter queues.
- **Timed drills.** Method sheet on the wall. The model is the CKA's live-cluster, time-boxed style, where troubleshooting is the largest domain by weight **[Sourced: R2, LF CKA page]**. No exam is taken or funded.
- **K8s security.** Break first: an over-broad role and an open policy are the seeded faults.
- **STRIDE.** Draw trust boundaries before listing threats. Add one question ("what if a document in our data tells the system what to do?") as a preview of AI threat modelling in Weeks 15–19.
- **Scope negotiation.** The actor adds a request on Thursday evening; the learner must trade scope explicitly, never absorb silently **[Foundation §2.3]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W9-L1 | Event-driven path | Same message delivered twice yields exactly 1 side effect; a poison message lands in the DLQ; throughput measured at 3 load levels |
| W9-L2 | 4 timed drills | ≥3 of 4 solved within 20 min each; method sheet used (evidence cited); stall points logged |
| W9-L3 | RBAC and NetworkPolicy | CI service account passes 6/6 least-privilege negative tests; default-deny policy plus only required flows; `SEC-RBAC` and `SEC-NETPOL-OPEN` detected and fixed |
| W9-L4 | Signing and verification | Signed image deploys; unsigned and tampered images rejected at admission (2/2); SBOM attached [signing and admission tool names [U]] |
| W9-L5 | Threat model | ≥10 threats ranked; trust boundaries on the diagram; ≥6 mitigations mapped to controls; reviewer finds ≤3 gaps |

**Customer thread.** CL9: Micro: the scope triangle and "yes, if" trades; drill: reply to a mid-project request in 3 lines; simulation: the Kestrel COO actor demands a new report format before the batch window. Artifact: a one-paragraph change request with impact on time, cost and risk. Rubric R2/R6/R9.
**Carried project: P3 "Integration with a hostile legacy system" (Kestrel).** Build a resilient adapter between the dock tracker and the legacy warehouse system: retries, idempotency, monitoring, rollback; mid-project requirement change in Week 10.
**Resources.** SRE book chapter on engagement and handover https://sre.google/sre-book/evolving-sre-engagement-model/ [Sourced: R4] · LF CKA page (exam structure) https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/ [Sourced: R2; syllabus only] · KodeKloud CKA course (method reference only) https://kodekloud.com/courses/certified-kubernetes-administrator-cka [Sourced: R2] · OWASP DevSecOps Guideline https://owasp.org/www-project-devsecops-guideline/ [Sourced: R2]
**Stall points and instructor notes.** Webhook certificate faults need patience; coach with the method sheet, not the answer (escalation ladder 0/10/25/40 min). This week has the first designated G1-remediation hours: hold the retakers' parallel-task session on Wednesday.
**Exit checklist.** [ ] idempotent consumer passes replay test [ ] ≥3/4 drills [ ] RBAC and NetworkPolicy lab passed [ ] threat model drafted [ ] P3 design signed off [ ] G1 remediation plans in place.

### Week 10 — G2 week: FinOps, security review defence; P3 close
*Phase A · Days 46–50 · **G2 Secure delivery review (Day 50)** · 40 h: CLD 4, DSO 12, PRJ 8, ASM 6, SLK 7, CUS 3*

**Objectives.** By Friday the learner can:
1. Allocate and control cloud cost and state a unit cost for what they run.
2. Assemble a full security-review artifact set and defend it under questioning.
3. Close P3 with monitoring, rollback and a change log after a mid-project requirement change.
4. **Pass G2:** defend an architecture to a role-played enterprise security team.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W10-I1 | Instruction: cost allocation, Budgets actions, rightsizing, unit economics | CLD | INS | D2 | 1 |
| W10-L1 | FinOps lab: tags, budget actions, rightsizing, unit-cost report | CLD | LAB | D2 | 3 |
| W10-I2 | Instruction: how security reviews work; artifacts and the hidden question bank | DSO | INS | D3 | 3 |
| W10-L2 | G2 artifact build: the seven artifacts | DSO | LAB | D3 | 4 |
| W10-L3 | Mock security review 1: panel of staff, 45 minutes | DSO | LAB | D3 | 3 |
| W10-L4 | AI preview: indirect injection demo and the lethal trifecta (`AI-INJECT-INDIRECT`) | DSO | LAB | D3 | 2 |
| W10-J1 | P3 requirement change and scope negotiation with the client actor; adapter update | PRJ | PRJ | D6 | 4 |
| W10-J2 | P3 monitoring, rollback drill, change log, handover note | PRJ | PRJ | D5 | 4 |
| W10-A1 | **G2**: artifact check 24 h ahead, 45-min panel defence, debrief, craft scoring | ASM | ASM | D3 | 6 |
| W10-S1 | G1/G2 remediation sessions on parallel tasks | SLK | SLK | all | 4 |
| W10-S2 | Retro, learning-plan update, hours check, midpoint pre-read | SLK | SLK | all | 3 |
| W10-C1 | Customer Lab 10: security conduct; rehearse with the CISO delegate actor | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (46) | I1; L1 FinOps | I2; L2 G2 artifacts | Review block: artifact peer check |
| Tue (47) | L2 continues; J1 P3 requirement change | J1 continues; S1 remediation sessions | Incident drill: security incident (`SEC-UNENCRYPTED` discovered post-deploy) |
| Wed (48) | L3 mock security review | C10 Customer Lab 10 (13:15–16:15) | L4 AI preview, first 1.5 h (16:15–17:45) |
| Thu (49) | L4 wrap-up (0.5 h); J2 P3 close | Artifacts frozen 13:00 (24 h before G2); S2 retro and hours check | Mock review debrief |
| Fri (50) | Checkpoint (short); panel preparation | **G2 panel (13:15 start)**, debrief, result | Retro; pulse |

**What to teach and how**
- **FinOps.** Cost is a first-class SLO. Learners publish a unit cost for P1 ("cost per booked slot") and sketch the token-cost model that will drive AI cost reviews from Week 13.
- **Security review.** The seven artifacts are in §3.3. Teach "the review is a conversation, not a document hand-over". Rehearse the answer pattern: answer, evidence, limits. "I don't know, and here is how I would find out" scores higher than a fabricated answer **[Repo: Assessment Pack G2]**.
- **AI preview.** Show a poisoned document steering a naive assistant. Name the lethal trifecta (private data, untrusted content, external communication) **[Sourced: R5 T17]**. This seeds the AI questions in the hidden bank.
- **P3 change.** The actor changes the batch window. The learner updates impact on time, cost and risk before touching code.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W10-L1 | FinOps report | Cost-allocation tags cover ≥95% of resources; a Budgets action fires in a test; one rightsizing change applied with before/after cost; unit cost for P1 stated; an answer-first cost update sent to the COO actor |
| W10-L2 | Seven artifacts | All seven present and consistent: data-flow with trust boundaries, SBOM matching the deployed digest, scan reports with triage, secrets design, IAM/RBAC matrix, control-to-framework mapping, incident response plan; peer check finds ≤3 inconsistencies |
| W10-L3 | Mock review 1 | ≥9 of 12 questions scored 3 or higher on the review rubric; no fabricated answers (panel checks); gaps list recorded |
| W10-L4 | Injection demo analysis | All three trifecta legs identified; one design change proposed that removes or gates a leg; 4 AI questions with answers added to the learner's bank |

**Customer thread.** CL10: security and compliance conduct. Micro: explain a block in plain language and offer a compliant path. Simulation: the CISO delegate actor asks where data goes, who can see it, and how long it is kept. Artifact: a one-page plain-language answer sheet. Rubric R7.
**Carried project.** P3 closes: adapter, monitoring, rollback drill, change log, handover note. Acceptance: replayed duplicates cause 0 duplicate side effects; a rollback restores the previous behaviour in ≤10 min; alert fires on a simulated legacy outage within 5 min **[Judgment]**.
**G2 (Day 50).** See §3.3. Two independent assessors; calibrated on recorded examples beforehand.
**Resources.** OWASP DevSecOps Guideline https://owasp.org/www-project-devsecops-guideline/ [Sourced: R2] · OWASP Top 10 for LLM Applications https://genai.owasp.org/llm-top-10/ [Sourced: R5] · Willison on the lethal trifecta https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/ [Sourced: R5] · AWS Budgets controls https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-controls.html [Sourced: R2]
**Stall points and instructor notes.** Artifact inconsistency (SBOM versus deployed digest) is the usual avoidable fail; tell learners the check exists. The 24 h artifact deadline is firm. Keep the G2 panel to the published bank of about 30 questions, 12 asked.
**Exit checklist.** [ ] seven artifacts submitted on time [ ] G2 result recorded [ ] P3 accepted [ ] G1/G2 remediation plans filed [ ] midpoint pre-read done.

# Phase B — Consolidate and AI on-ramp (Weeks 11–12, Days 51–60)

This is the first two-week consolidation window: 24 h of slack for remediation, plus the carried P4 project and the first AI hours. Linden Claims Services (the regulated customer) arrives here.

### Week 11 — ML "just enough", Python for AI, constrained environments; P4 kickoff
*Phase B · Days 51–55 · 40 h: AIC 16, PRJ 8, SLK 13, CUS 3*

**Objectives.** By Friday the learner can:
1. Explain train/validation/test, leakage, imbalance and why accuracy misleads; choose between a classifier and an LLM using data.
2. Compute embeddings and run nearest-neighbour search; read tokens and context limits.
3. Process thousands of API calls with bounded concurrency, retries and checkpoint-resume.
4. Describe what changes when a system runs air-gapped or under a data-residency rule (P4).
5. Use the slack hours to close gaps from Phase A before the AI block.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W11-I1 | Instruction: ML/DL "just enough" (splits, leakage, metrics, embeddings, tokens, context) | AIC | INS | D4 | 3 |
| W11-L1 | Tabular baseline with a leakage trap (`ML-LEAKAGE`) | AIC | LAB | D4 | 3 |
| W11-L2 | Tokenisation and embeddings: nearest-neighbour search over 500 documents | AIC | LAB | D4 | 2 |
| W11-L3 | LLM-versus-classifier bake-off on 300 labelled tickets | AIC | LAB | D4 | 2 |
| W11-I2 | Instruction: Python for AI (async, pydantic, JSONL/Parquet, DuckDB) | AIC | INS | D4 | 2 |
| W11-L4 | Async batch processing with bounded concurrency, retries, resume | AIC | LAB | D4 | 4 |
| W11-J1 | **P4 kickoff**: Linden discovery with the CISO delegate and platform manager; residency rules; threat model | PRJ | PRJ | D6 | 4 |
| W11-J2 | P4 build: offline deployment with no egress route (`FIELD-AIRGAP`, part 1) | PRJ | PRJ | D2 | 4 |
| W11-S1 | Consolidation: backlog labs; retrieval quiz with items from 1, 3, 6 and 12 weeks earlier | SLK | SLK | all | 5 |
| W11-S2 | Remediation clinics: G1/G2 retakers; parallel-task re-assessments | SLK | SLK | all | 4 |
| W11-S3 | Open lab, mentor 1:1s, learning-plan updates, midpoint preparation | SLK | SLK | all | 4 |
| W11-C1 | Customer Lab 11: adversarial stakeholder panel on the P4 plan | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (51) | I1; L1 tabular baseline | L1 continues; L2 embeddings | Review block: peer review of L1 memos |
| Tue (52) | L2 finishes; L3 bake-off | J1 P4 kickoff | Retake clinics (S2) |
| Wed (53) | I2; L4 async batch | L4 continues; J2 P4 offline build | S1 consolidation clinic |
| Thu (54) | J2 P4 build | S3 open lab; mentor 1:1s | Incident drill: `FIELD-AIRGAP` first look |
| Fri (55) | Checkpoint, demo, quiz | C11 Customer Lab 11 (13:15–16:15) | Retro; pulse; AI-environment check |

**What to teach and how**
- **ML "just enough".** A leakage trap makes the point: a model that is too good is suspicious. Do not derive backprop. Karpathy's from-scratch series is an optional reading, not required **[Sourced: R5 T1]**.
- **Bake-off.** The numbers decide, not enthusiasm: accuracy, p50 latency and cost per 1,000 items for TF-IDF + logistic regression, zero-shot LLM and few-shot LLM. "A classifier may win" is a legitimate result.
- **Async Python for AI.** Bounded concurrency prevents 429 storms; checkpoint-resume makes crashes boring **[Sourced: R5 T2]**.
- **Air-gap.** A genuinely isolated VPC means a *missing route*, not a restrictive security group; a firewall rule can be worked around, a missing route cannot **[Repo: Ops Guide §4; Foundation §9.4]**. Pre-stage the internal mirror. The learning is in the pre-staging discipline.
- **Slack discipline.** The clinics are for named gaps, not new content. Remediation happens inside scheduled hours (no evening work).

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W11-L1 | Baseline model and memo | `ML-LEAKAGE` identified and removed; precision and recall reported at a chosen threshold; a one-paragraph "ship / don't ship" memo (R5 T1-1) |
| W11-L2 | Embedding search | ≥70% top-1 on 20 hand-labelled queries over 500 documents; 3 failure cases explained (R5 T1-2) |
| W11-L3 | Bake-off table | Accuracy, p50 latency and $/1k items for 3 approaches on 300 tickets; recommendation justified on all three axes (R5 T1-3) |
| W11-L4 | Async batch job | Crash mid-run then resume without re-calling completed items; 0 duplicate calls (verified from logs); throughput ≥5× sequential (R5 T2-1) |

**Customer thread.** CL11: adversarial stakeholders (stage 2 simulation). Micro: building one plan from three conflicting asks. Simulation: the VP Claims Operations (wants speed), the CISO delegate (blocks on data) and the platform manager (five-day change SLA) meet the learner; produce one aligned P4 plan. Artifact: the plan with named trade-offs. Rubric R2/R7/R9.
**Carried project: P4 "Constrained environment" (Linden).** The same service must run (a) in a no-internet environment (offline bundle, internal registry, manual update approval) and (b) under a data-residency rule; a role-played CISO reviews the data flow **[Sourced: R4 §3.5]**.
**Resources.** Google ML Crash Course https://developers.google.com/machine-learning/crash-course [Sourced: R5] · Karpathy "Zero to Hero" (optional) https://karpathy.ai/zero-to-hero.html [Sourced: R5] · Hugging Face LLM course https://huggingface.co/learn/llm-course/chapter1/1 [Sourced: R5] · What an air-gapped AI deployment requires (vendor blog) https://decagon.ai/blog/what-an-air-gapped-ai-deployment-actually-requires [Sourced: R4; commercial] · FDE air-gap guide (vendor) https://fde.academy/blog/air-gapped-ai-deployment-guide-for-fdes [Sourced: R4; commercial]
**Stall points and instructor notes.** Learners who skipped weeks of foundations will show up here; use the clinic to triage. Watch for learners who treat the "classifier wins" result as a failure. Start telemetry on `stall_point` for `FIELD-AIRGAP`.
**Exit checklist.** [ ] 4 labs passed [ ] G1/G2 retakes scheduled or closed [ ] P4 plan aligned with actors [ ] offline build started [ ] hours audit (median ≤44) [ ] AI environment ready (gateway keys, vector DB, tracing).

### Week 12 — Python for AI, P4 close, Mid-program review
*Phase B · Days 56–60 · **Mid-program review (Day 60)** · 40 h: AIC 14, PRJ 8, ASM 4, SLK 11, CUS 3*

**Objectives.** By Friday the learner can:
1. Read a model card and explain, in client language, why a model fails on a slice.
2. Turn a notebook into a tested module and expose it as a typed API service.
3. Profile a corpus and prepare a human-labelled dev set (labeller is not the person who will tune retrieval).
4. Close P4: offline deployment guide, residency proof and a CISO review.
5. Pass the Mid-program review: a candid, evidence-based readiness conversation.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W12-I1 | Instruction: model cards, drift, base rates | AIC | INS | D4 | 1 |
| W12-L1 | Model card reading and failure explanation for a client | AIC | LAB | D4 | 3 |
| W12-I2 | Instruction: tested modules, typed services, FastAPI | AIC | INS | D4 | 2 |
| W12-L2 | Data-cleaning notebook to a tested module | AIC | LAB | D4 | 3 |
| W12-L3 | FastAPI endpoint with typed I/O, health check, container | AIC | LAB | D4 | 3 |
| W12-L4 | Corpus profiling and dev-set preparation (starter corpus of about 200 documents) | AIC | LAB | D4 | 2 |
| W12-J1 | P4 residency: region lock, data-flow, CISO role-play review | PRJ | PRJ | D3 | 4 |
| W12-J2 | P4 deliverables: offline deployment guide, accreditation-style checklist, threat model | PRJ | PRJ | D3 | 4 |
| W12-A1 | **Mid-program review**: competency re-score, self-rating, discovery re-test, readiness question | ASM | ASM | all | 4 |
| W12-S1 | Last retakes; G1/G2 remediation closure | SLK | SLK | all | 4 |
| W12-S2 | AI environment check and reading list for the AI block | SLK | SLK | all | 3 |
| W12-S3 | Retro, wellbeing, cohort plan reset, learning-plan updates | SLK | SLK | all | 4 |
| W12-C1 | Customer Lab 12: the bad-news call | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (56) | I1; L1 model card lab | L1 continues; J1 P4 residency | Review block: model-card write-ups |
| Tue (57) | I2; L2 notebook to module | L3 FastAPI service | S1 retake sessions |
| Wed (58) | L4 corpus profiling | C12 Customer Lab 12 (13:15–16:15) | J2 P4 deliverables |
| Thu (59) | J2 P4 deliverables; J1 CISO review | S2 AI environment check | S3 retro and cohort plan reset |
| Fri (60) | **A1 Mid-program review** (individual 45-min sessions in rotation; others in open lab) | A1 continues; results meeting | Pulse; clean break before the AI block |

**What to teach and how**
- **Model cards.** Use a real public model card and a deliberately flawed internal one; learners write one paragraph a client can act on **[Judgment]**.
- **Typed Python for AI.** The point is boring reliability: tests, validation, health checks. Notebook-only deliverables are not accepted **[Sourced: R5 T2]**.
- **Dev set discipline.** The labeller is not the retrieval tuner (assignment recorded). The 40+ question dev set with gold source passages is reused in Week 14 **[Repo: Ops Guide; Sourced: R5 T5-1]**.
- **P4 close.** A role-played CISO signs off or lists findings. Practise stating a block in plain words and offering a path (R7).

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W12-L1 | One-page client explanation | ≥2 plausible causes of the slice failure each backed by evidence from the card or data; no jargon an executive cannot follow (instructor rubric ≥80%) [Judgment] |
| W12-L2 | Tested module | ≥10 pytest cases incl. 3 malformed inputs; schema validated by pydantic or pandera; CI green (R5 T2-2) |
| W12-L3 | Typed API service | OpenAPI schema generated; invalid payload returns 422; container builds and runs (R5 T2-3) |
| W12-L4 | Profiled corpus + dev set | ≥40 questions with gold source passages; second-person check agrees on ≥90%; labeller and future tuner are different people (recorded) |

**Customer thread.** CL12: the bad-news call. Micro: raise early, bring options and a recommendation, own the issue without blame. Simulation: the Linden VP Claims is told the offline model cannot meet the hosted model's accuracy. Artifact: a 5-minute call plus a three-line follow-up. Rubric R6. The Mid-program review re-tests discovery (below).
**Carried project.** P4 closes. Acceptance: service runs with no egress (a failed egress test proves it); all installs come from the internal mirror; a policy test blocks an out-of-region bucket; the CISO actor review leaves ≤3 open findings **[Judgment]**.
**Mid-program review (Day 60).** See §3.4. Competency re-score by two independent assessors (L0–L4 per domain), behavioural self-rating, a recorded discovery re-test with the same persona type as G0, and the question "would we put this person in front of a low-risk customer?".
**Resources.** Hugging Face model cards documentation https://huggingface.co/docs/hub [U, not fetched] · pydantic https://docs.pydantic.dev and FastAPI https://fastapi.tiangolo.com [U, not fetched in R5] · Google SRE on-call training (shadow, reverse shadow) https://sre.google/sre-book/accelerating-sre-on-call/ [Sourced: R3]
**Stall points and instructor notes.** The Mid-program review can feel like a verdict; frame it as a map. Do not introduce new technical content on Day 60. Anyone with an unresolved gate remediation gets a named mentor and a dated plan before the AI block starts. The zero-slack AI phases begin Monday: say so plainly.
**Exit checklist.** [ ] all four labs passed [ ] P4 accepted [ ] mid-review done and plans filed [ ] dev set with gold passages ready [ ] tracing stack and gateway keys tested [ ] G1/G2 outcomes closed or plans dated.

# Phase C1 — AI Core (Weeks 13–18, Days 61–90)

The AI phases are fully booked: zero slack (Foundation §7.6 warning). P5 (Linden's "SOP and claims assistant") is the carried system. Each AI week ends with a customer-style demo and an eval number. Every lab needs eval and trace evidence from Week 13 on.

**The P5 system.** Linden's adjusters ask questions about policy wording, SOPs and claim notes. The assistant must answer from the documents, cite sources, say "I don't know" when the corpus is silent, respect per-department access, and cost a known amount per answer. It starts on the starter corpus (about 200 documents) and moves to the main corpus (5,000 synthetic documents) **[Foundation §9.5]**.

### Week 13 — Prompting and structured outputs, tool use, tracing first; P5 kickoff
*Phase C1 · Days 61–65 · 40 h: AIC 28, AIO 5, PRJ 4, CUS 3*

**Objectives.** By Friday the learner can:
1. Get schema-valid, field-accurate structured output from a model and measure it.
2. Improve a prompt with a held-out set without overfitting.
3. Write a tool-calling loop by hand, design tool descriptions, and add a write tool that is safe to retry.
4. Trace every model call (prompt version, tokens, cost) and find a real bug in traces.
5. Agree with the client what "good" means for P5.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W13-I1 | Instruction: prompting, structured outputs, versioning prompts in git | AIC | INS | D4 | 3 |
| W13-L1 | Extraction lab: 100 documents to a pydantic schema; constrained vs prompt-only | AIC | LAB | D4 | 5 |
| W13-L2 | Prompt A/B lab on a held-out set (3 iterations) | AIC | LAB | D4 | 4 |
| W13-L3 | Break-it lab: 10 inputs that violate the schema or confuse the prompt | AIC | LAB | D4 | 4 |
| W13-I2 | Instruction: tool use, the hand-written tool loop, tool design, the lethal trifecta (seed) | AIC | INS | D4 | 2 |
| W13-L4 | Hand-written tool loop with three tools against a mock API | AIC | LAB | D4 | 4 |
| W13-L5 | Tool-description tuning on an ambiguous six-tool set | AIC | LAB | D4 | 3 |
| W13-L6 | Safe-action tool: idempotency key, dry-run, per-call authorisation | AIC | LAB | D4 | 3 |
| W13-I3 | Instruction: tracing before evals (spans, tokens, cost, versions) | AIO | INS | D5 | 1 |
| W13-L7 | Tracing lab: instrument the P5 starter assistant | AIO | LAB | D5 | 4 |
| W13-J1 | **P5 kickoff**: define "good" with the Linden VP Claims and senior adjuster; seed eval cases | PRJ | PRJ | D6 | 4 |
| W13-C1 | Customer Lab 13: define "good" with the client | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (61) | I1; L1 extraction | L1 continues; L2 prompt A/B | Review block: schema and prompt reviews |
| Tue (62) | L2; L3 break-it | J1 P5 kickoff workshop | Reflection: what did the client mean by "good"? |
| Wed (63) | I2; L4 tool loop | L4 continues; L5 tool descriptions | Office hours |
| Thu (64) | L5 finishes; L6 safe-action tool | I3; L7 tracing | Incident drill: trace-based bug hunt |
| Fri (65) | Checkpoint, demo, quiz | C13 Customer Lab 13 (13:15–16:15) | Retro; pulse |

**What to teach and how**
- **Structured outputs.** Teach the schema as the contract between the model and enterprise systems. Provider schema-constrained output is preferred to "please return JSON"; check current limits (recursive schemas and some constraints are unsupported; first use of a new schema adds latency) **[Sourced: R5 T3, Anthropic structured-outputs docs, re-check at delivery]**. Instructor (API models) and Outlines (self-hosted) are alternatives **[Sourced: R5, Applied LLMs]**. Prompts live in git.
- **Prompt discipline.** No iteration merges without a score on the same set; a different holdout checks overfitting.
- **Tool loop first, frameworks later.** Anthropic's guidance is to start with the simplest solution and understand what a framework hides **[Sourced: R5 §1, Building effective agents]**. Teach tool descriptions "as docstrings for a junior developer" and the poka-yoke idea of making wrong arguments hard to express **[Sourced: R5 T4]**.
- **Seed the trifecta.** Show a tool that reads untrusted text and can send email; ask what could go wrong. Revisited in Weeks 15–19.
- **Tracing first** (DeepLearning.AI's "Evaluating AI Agents" teaches tracing before evals) **[Sourced: R1]**.
- **Run every lab against two endpoints** (hosted frontier model and an OpenAI-compatible one) with the model name read from config only.

**Labs: deliverables and pass criteria** (adapted from R5; thresholds are R5's design judgment)

| ID | Deliverable | Pass criteria |
|---|---|---|
| W13-L1 | Extraction pipeline + comparison table | ≥98% schema-valid with constrained output (and the prompt-only rate measured); field-level accuracy ≥90% against gold labels (R5 T3-1) |
| W13-L2 | Prompt iterations log | 3 iterations each scored on the same 50 examples; nothing merged without a score; the final prompt beats baseline by a pre-declared margin and also passes on a *different* 25-example holdout (R5 T3-2) |
| W13-L3 | Break-it report | The validator catches 100% of the 10 schema violations; the retry-with-error loop recovers ≥70%; the rest route to a "needs human" bucket (R5 T3-3) |
| W13-L4 | Tool loop (no framework) | 20/20 scripted scenarios complete; the invalid-argument case returns an error that lets the model self-correct within 1 retry in ≥80% of runs (R5 T4-1) |
| W13-L5 | Tuned tool set | Wrong-tool rate on 30 tasks drops ≥50% and tokens per task rise ≤20% (R5 T4-2) |
| W13-L6 | Safe write tool | A replayed call causes exactly 1 side effect; an unauthorised user context is rejected in code, not by the prompt (R5 T4-3) |
| W13-L7 | Traced assistant | 100% of calls traced with prompt version, tokens and cost; a dashboard shows p50 and p95 latency and $/request; one real bug found from traces and documented (R5 T13-1) |

**Customer thread.** CL13: define "good". Micro: translate business outcomes into measurable criteria; drill: write 10 test questions with the client's words; simulation (stage 3, the living Linden client): VP Claims and a senior adjuster who reveals truth only to good questions. Artifact: a one-page "definition of good" with a metric and 20 real-seeming failure cases to seed the eval set. Rubric R1/R2.
**Carried project: P5 kickoff.** Acceptance this week: scope one-pager signed by the actor; eval seed (20 cases); the starter assistant traced.
**Resources.** Anthropic structured outputs https://platform.claude.com/docs/en/build-with-claude/structured-outputs [Sourced: R5; V] · Writing tools for agents https://www.anthropic.com/engineering/writing-tools-for-agents [Sourced: R5; V] · Building effective agents https://www.anthropic.com/engineering/building-effective-agents [Sourced: R5; V] · Applied LLMs https://applied-llms.org/ [Sourced: R5; V] · Eugene Yan patterns https://eugeneyan.com/writing/llm-patterns/ [Sourced: R5; V] · Langfuse OpenTelemetry docs https://langfuse.com/docs/opentelemetry/introduction [Sourced: R5; S, conventions still evolving] · DeepLearning.AI short courses (method reference) https://www.deeplearning.ai/short-courses/ [Sourced: R1]
**Stall points and instructor notes.** Over-trusting schema-valid output (valid does not mean correct); learners tuning on the test set. The first AI week is also the first zero-slack week: protect the Friday craft block and the 17:45 stop; the escalation ladder applies. Pick **one** tracing tool per cohort (Langfuse or Phoenix).
**Exit checklist.** [ ] 7 labs passed with eval/trace evidence [ ] prompts versioned in git [ ] no model ID in code [ ] P5 scope signed [ ] eval seed (20 cases) [ ] pulse reviewed.

### Week 14 — RAG I, evals I, reliability
*Phase C1 · Days 66–70 · 40 h: AIC 28, AIO 5, PRJ 4, CUS 3*

**Objectives.** By Friday the learner can:
1. Build a baseline RAG pipeline and measure retrieval separately from generation.
2. Parse messy documents with metadata and report failures.
3. Do error analysis on real traces, write a named failure taxonomy, and build a first golden set.
4. Make a client-facing LLM call path survive provider errors.
5. Present an honest executive brief on baseline results.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W14-I1 | Instruction: RAG architecture; retrieval is not generation; metrics | AIC | INS | D4 | 3 |
| W14-L1 | Baseline RAG over the 200-document starter corpus | AIC | LAB | D4 | 5 |
| W14-I2 | Instruction: parsing messy documents; chunking; metadata | AIC | INS | D4 | 1 |
| W14-L2 | Ingestion lab: PDFs, HTML, Word; metadata and parse-failure report | AIC | LAB | D4 | 5 |
| W14-L3 | Answer behaviour lab: citations and "I don't know" | AIC | LAB | D4 | 4 |
| W14-I3 | Instruction: evals: error analysis, binary labels, assertions first | AIC | INS | D4 | 1 |
| W14-L4 | Error-analysis sprint on 60 traces | AIC | LAB | D4 | 4 |
| W14-L5 | Golden set and assertion suite (40 cases) | AIC | LAB | D4 | 5 |
| W14-L6 | Reliability harness: injected 429s, timeouts, malformed responses | AIO | LAB | D5 | 4 |
| W14-I4 | Instruction: privacy basics for AI: data classes, data-flow diagram | AIO | INS | D3 | 1 |
| W14-J1 | P5 baseline: workflow and eval set v1; first "what it cannot do" draft | PRJ | PRJ | D4 | 4 |
| W14-C1 | Customer Lab 14: answer-first executive brief on baseline results | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (66) | I1; L1 baseline RAG | L1 continues; I2 | Review block: retrieval-metric reviews |
| Tue (67) | L2 ingestion | L2 continues; L3 answer behaviour | Reflection |
| Wed (68) | I3; L4 error analysis | C14 Customer Lab 14 (13:15–16:15) | L5 golden set (carry-over) |
| Thu (69) | L5 golden set; L6 reliability harness | L6 continues; J1 P5 baseline; I4 | Office hours |
| Fri (70) | Checkpoint, demo, quiz | Incident drill (`RAG-FAIL` variant: stale document retrieved) | Retro; pulse |

**What to teach and how**
- **RAG.** Parse → clean → chunk with metadata → embed → index. Evaluate retrieval (recall@k) *before* judging answers. Teach "when RAG is unnecessary": a small corpus that fits in the context window, with caching, may not need it **[Sourced: R5 T5, Anthropic Contextual Retrieval note]**.
- **Messy documents.** Use the deliberately messy starter corpus (PDFs, HTML, a Word export). Garbage in, garbage out is the lesson **[Sourced: R5 T5, common mistakes]**.
- **Error analysis.** Read many traces; open-code, then axial-code into a taxonomy; count. Binary good/bad labels over Likert scales; unit-test style assertions first **[Sourced: R5 T6, Husain; Anthropic evals post]**.
- **Reliability.** Backoff with jitter, timeouts, circuit breaker; track the fallback rate **[Sourced: R5 T13]**.
- **Privacy basics.** Draw the data-flow diagram for the P5 system now; refine in Week 18.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W14-L1 | Baseline RAG | 40+ hand-written questions with gold source passages (from W12-L4); recall@5 and recall@10 reported; answer correctness reported; ≥85% of answers carry a citation that resolves to the right chunk (R5 T5-1) |
| W14-L2 | Ingestion pipeline | ≥95% of documents ingested with correct metadata (source, section, department, date); parse-failure report produced; 10-document spot check ≥90% text fidelity [Judgment] |
| W14-L3 | Answer behaviour | Every answer cites a chunk; ≥90% of "not in corpus" questions answered "I don't know" (R5 T5-3 criterion) |
| W14-L4 | Failure taxonomy | ≥5 named failure modes with counts; the top 2 account for ≥50% of failures; each has an example trace and a proposed fix (R5 T6-1) |
| W14-L5 | Golden set and assertions | 40 cases (10 adversarial, 10 "should refuse or escalate"); deterministic assertions; flake rate across 3 runs <5% on deterministic checks (R5 T6-2, CI part in Week 16) |
| W14-L6 | Reliability harness | No user-visible failure at ≤20% injected error rate; backoff has jitter (verified from timestamps); the breaker opens and recovers; fallback rate reported (R5 T13-2) |

**Customer thread.** CL14: executive brief. Micro: Minto/SCQA for results. Drill: summarise the baseline in one page, answer first (accuracy, cost, what fails, ask). Simulation: the VP Claims reads for 2 minutes then asks "so can my adjusters trust it?". Artifact: one-page brief. Rubric R5.
**Carried project.** P5 baseline workflow plus eval set v1, and a draft "what it cannot do" page.
**Resources.** Anthropic Contextual Retrieval https://www.anthropic.com/engineering/contextual-retrieval [Sourced: R5; V, vendor-reported numbers] · Hamel Husain on evals https://hamel.dev/blog/posts/evals/ [Sourced: R5; V] · Evals FAQ (headings only read) https://hamel.dev/blog/posts/evals-faq/ [Sourced: R5] · Anthropic: demystifying evals for AI agents https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents [Sourced: R5; V] · LiteLLM reliability docs https://docs.litellm.ai/docs/router/learn/reliability [Sourced: R5; S] · Maven AI Evals course (method reference) https://maven.com/parlance-labs/evals [Sourced: R1]
**Stall points and instructor notes.** Learners judge final answers only; send them back to retrieval metrics. The most common mistake is fixed 512-token chunks ignoring structure. Choose the vector store once (pgvector by default **[Sourced: R5 T5, community consensus]**). Test your own results: vector DB benchmarks conflict.
**Exit checklist.** [ ] baseline RAG measured [ ] ingestion report [ ] taxonomy with counts [ ] golden set v1 [ ] harness passes [ ] brief delivered [ ] stall-point telemetry for L1 reviewed.

### Week 15 — RAG II, evals II, cost, first injection audit
*Phase C1 · Days 71–75 · 40 h: AIC 28, AIO 5, PRJ 4, CUS 3*

**Objectives.** By Friday the learner can:
1. Choose a retrieval configuration from an ablation table (dense, keyword, hybrid with rank fusion, reranker, contextual chunks).
2. Enforce per-user document access in the retrieval query, and prove zero leaks.
3. Diagnose RAG failures to a taxonomy category from traces.
4. Calibrate an LLM judge against human labels and report TPR and TNR.
5. Identify the legs of the lethal trifecta in an architecture and redesign it.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W15-I1 | Instruction: hybrid search, rank fusion, reranking, contextual retrieval, ACL | AIC | INS | D4 | 3 |
| W15-L1 | Retrieval ablation lab | AIC | LAB | D4 | 5 |
| W15-L2 | Access-controlled RAG lab (`RAG-ACL`) | AIC | LAB | D4 | 5 |
| W15-L3 | RAG failure taxonomy lab (`RAG-FAIL-1..6`) | AIC | LAB | D4 | 5 |
| W15-I2 | Instruction: LLM judges: calibration, bias, pairwise comparison | AIC | INS | D4 | 2 |
| W15-L4 | Judge calibration lab (`EVAL-JUDGE`) | AIC | LAB | D4 | 4 |
| W15-L5 | RAG evals lab: retrieval and generation scored separately | AIC | LAB | D4 | 4 |
| W15-I3 | Instruction: token economics: caching, routing, trimming | AIO | INS | D5 | 1 |
| W15-L6 | Cost lab part 1: token accounting, baseline, caching test | AIO | LAB | D5 | 2 |
| W15-L7 | Trifecta audit of three agent architectures | AIO | LAB | D3 | 2 |
| W15-J1 | P5 improvement: apply the ablation winner; eval v2; error-analysis readout to the client | PRJ | PRJ | D4 | 4 |
| W15-C1 | Customer Lab 15: demo to a hostile technical evaluator | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (71) | I1; L1 ablation | L1 continues; L2 ACL | Review block: ablation table reviews |
| Tue (72) | L2 continues; L3 failure taxonomy | L3 continues | Incident drill: `RAG-ACL` leak found in production |
| Wed (73) | I2; L4 judge calibration | L4 continues; L5 RAG evals | Office hours |
| Thu (74) | L5 continues; I3; L6 cost | L7 trifecta audit; J1 P5 improvement | Reflection |
| Fri (75) | Checkpoint, demo, quiz | C15 Customer Lab 15 (13:15–16:15) | Retro; pulse |

**What to teach and how**
- **Ablation.** One table with recall@10, MRR, p95 latency and cost per query for dense, BM25, hybrid with reciprocal rank fusion, hybrid + reranker and contextual chunks; three chunk sizes. Rank fusion and reranking are commonly recommended but the numbers must justify them on *this* corpus. Vendor-reported figures (for example Anthropic's reported drop in retrieval failures with contextual retrieval) are a prompt to test, not a result **[Sourced: R5 T5]**.
- **ACL.** The filter must live in the query or index, never in the prompt **[Sourced: R5 T5/T21]**. Map to OWASP LLM08 (vector and embedding weaknesses).
- **Judges.** Validate against human labels and report TPR and TNR, not raw agreement. Check position, length and self-preference bias **[Sourced: R5 T6, Husain; Applied LLMs]**.
- **Trifecta.** Private data + untrusted content + external communication: remove or gate one leg **[Sourced: R5 T17, Willison]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W15-L1 | Ablation table + recommendation | One table of recall@10, MRR, p95 latency and $/query across 5 configurations and 3 chunk sizes; recommend one config; hybrid + rerank justified or rejected by the numbers (R5 T5-2) |
| W15-L2 | Access-controlled retrieval | 0 leaks across 50 adversarial queries incl. "ignore filters" attempts; filtering enforced in the query or index, not the prompt; ≥90% of out-of-corpus questions answer "I don't know" (R5 T5-3) |
| W15-L3 | Failure diagnoses | ≥5 of 6 assigned `RAG-FAIL` variants classified to the right taxonomy category with trace evidence and a proposed fix [Judgment] |
| W15-L4 | Calibrated judge | 100 outputs labelled by two learners (agreement reported); judge TPR and TNR ≥0.85 against human consensus on a held-out 50; written bias note; the `EVAL-JUDGE` variant (miscalibrated judge) is detected (R5 T6-3) |
| W15-L5 | RAG eval report | Retrieval and answer metrics reported separately; the report names which stage causes most failures; faithfulness judge validated per L4 [Judgment] |
| W15-L6 | Cost baseline | Per-step token and $ table from traces; prompt-cache test run; ≥20% cost reduction from caching and trimming with ≤2-point drop on the eval set [Judgment; the ≥40% target is set in Week 21] |
| W15-L7 | Trifecta audit | Legs correctly identified in 3 architectures; one redesign each that removes or gates a leg; instructor rubric ≥80% (R5 T17-1) |

**Customer thread.** CL15: the hostile technical evaluator. Micro: handling limits questions honestly; "what it cannot do" is a feature. Simulation: a skeptical technical lead probes the P5 baseline ("what happens with a table in a scanned PDF?"). Artifact: recorded demo plus the limits page. Rubric R4/R9.
**Carried project.** P5 eval v2 with the ablation winner; error-analysis readout to the client in plain language.
**Resources.** Anthropic Contextual Retrieval https://www.anthropic.com/engineering/contextual-retrieval [Sourced: R5] · Hybrid search with rank fusion (arXiv) https://arxiv.org/pdf/2401.07883 [Sourced: R5; S] · OWASP LLM Top 10 https://genai.owasp.org/llm-top-10/ [Sourced: R5; V] · Willison on the lethal trifecta https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/ [Sourced: R5; V] · DeepLearning.AI RAG course (reference) https://www.deeplearning.ai/courses/retrieval-augmented-generation-rag/ [Sourced: R1]
**Stall points and instructor notes.** The biggest time sink is labelling for L4; stagger labelling across trios and use the Week-12 dev-set labellers where possible. The labeller of the golden set (frozen in Week 17) must not be the person tuning retrieval. If more than 40% of the cohort stalls in the same lab, log a curriculum defect and fix it before the next cohort (Foundation §6.8).
**Exit checklist.** [ ] ablation table and chosen config [ ] 0 ACL leaks [ ] judge TPR/TNR ≥0.85 [ ] retrieval/generation reported separately [ ] cost baseline [ ] trifecta audit [ ] demo given to the evaluator actor.

### Week 16 — CI evals, context engineering, the fine-tuning decision, red-teaming
*Phase C1 · Days 76–80 · 40 h: AIC 28, AIO 5, PRJ 4, CUS 3*

**Objectives.** By Friday the learner can:
1. Run evals in CI so a prompt or model change that regresses quality fails the build.
2. Budget and reduce context; compare compaction, notes and sub-agents; lay out prompts for cache hits.
3. Decide among prompting, RAG and fine-tuning with a written, measured argument.
4. Red-team their own system with injected instructions in documents, messages and tool results.
5. Handle a disappointed client honestly (expectation management).

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W16-I1 | Instruction: regression evals in CI; capability vs regression; pass@k vs pass^k | AIC | INS | D4 | 1 |
| W16-L1 | CI regression gate (`LLM-REGRESS`) | AIC | LAB | D4 | 6 |
| W16-L2 | Trajectory eval basics: reading transcripts, grader bugs, consistency | AIC | LAB | D4 | 3 |
| W16-I2 | Instruction: context engineering and prompt caching | AIC | INS | D4 | 2 |
| W16-L3 | Context budget audit of a 30-turn run | AIC | LAB | D4 | 3 |
| W16-L4 | Compaction vs notes vs sub-agent on an overflowing task (`LLM-CTX`) | AIC | LAB | D4 | 3 |
| W16-L5 | Cache-friendly prompt layout | AIC | LAB | D4 | 2 |
| W16-I3 | Instruction: prompting vs RAG vs fine-tuning: the decision | AIC | INS | D4 | 2 |
| W16-L6 | Decision memos for five customer scenarios | AIC | LAB | D4 | 3 |
| W16-L7 | Same-eval comparison: prompt vs few-shot; prepare the training set for the LoRA lab | AIC | LAB | D4 | 3 |
| W16-I4 | Instruction: prompt injection and red-teaming (direct, indirect, adaptive attacks) | AIO | INS | D3 | 1 |
| W16-L8 | Red-team your own RAG and agent (`AI-INJECT-INDIRECT`, `AI-INJECT-TOOL`) | AIO | LAB | D3 | 3 |
| W16-L9 | Layered guard stack: measure each layer | AIO | LAB | D3 | 1 |
| W16-J1 | P5: eval CI gate live in the Linden repo; regression demonstration | PRJ | PRJ | D4 | 4 |
| W16-C1 | Customer Lab 16: expectation management; the model is not a magic wand | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (76) | I1; L1 CI gate | L1 continues; L2 trajectory evals | Review block: pipeline and eval reviews |
| Tue (77) | I2; L3 context audit | L4 compaction vs notes; L5 cache layout | Reflection |
| Wed (78) | I3; L6 decision memos | C16 Customer Lab 16 (13:15–16:15) | L7 comparison (carry-over) |
| Thu (79) | L7 comparison; I4 | L8 red-team; L9 guard stack | Office hours |
| Fri (80) | Checkpoint, demo, quiz | J1 P5 gate demo; incident drill: `LLM-REGRESS` silent regression | Retro; pulse |

**What to teach and how**
- **CI evals.** Capability evals start low; regression evals should be near 100%. A model or prompt change must fail the build when it regresses; prove it by injecting a regression. Report pass@k *and* pass^k for non-deterministic tasks; customer-facing agents are judged on consistency **[Sourced: R5 T6/T7, Anthropic evals post]**. Read transcripts to catch grader bugs.
- **Context.** Context is a scarce resource ("context rot"); compaction, structured notes, sub-agents that return condensed summaries, just-in-time retrieval. Cache-friendly layout: tools, then system, then messages; keep per-request timestamps out of the prefix; check usage fields for hit rate. Cache multipliers and minimum lengths change by model; re-verify before teaching numbers **[Sourced: R5 T9, Anthropic caching docs]**.
- **The decision.** Prompting changes input; RAG changes available information; fine-tuning changes weights (behaviour, format, latency/cost on a narrow high-volume task). Fine-tuning to inject facts is the classic mistake. Fine-tuning before better retrieval is a costly wrong turn **[Sourced: R5 T10; Applied LLMs]**.
- **Red-teaming.** Adaptive attacks have beaten many published defences; detectors are not a security boundary; design so injection cannot cause a consequential action **[Sourced: R5 §1; Willison summary]**. Measure by action logs, not by model text.
- **Guards** are one layer, never the only one. Measure false-positive rate and latency cost of every layer.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W16-L1 | CI eval gate | GitHub Actions runs the suite on every prompt or model change; a deliberately injected prompt regression fails the build; flake rate across 3 runs <5% on deterministic checks (R5 T6-2) |
| W16-L2 | Trajectory eval notes | 30 transcripts read; ≥2 grader bugs found and fixed; pass@k and pass^k reported on 20 tasks [Judgment, from R5 T6 depth items] |
| W16-L3 | Context budget report | Tokens by category per turn; a change that cuts tokens per task ≥30% with no drop on the eval set (R5 T9-1) |
| W16-L4 | Three-way comparison | Compaction, notes and sub-agent variants compared on success rate and cost; ≥1 variant solves a task the naive variant fails (R5 T9-2) |
| W16-L5 | Cache-friendly layout | Cache-hit ratio ≥80% on a 100-request replay (from usage fields) with a before/after cost number (R5 T9-3) |
| W16-L6 | Five decision memos | Instructor rubric ≥80%; each memo names the failing layer and the measurement that would change the recommendation (R5 T10-1) |
| W16-L7 | Comparison + training set | Prompt and few-shot variants scored on the same held-out set; training data and eval data overlap = 0 (hash check); data card written [Judgment; sets up R5 T10-2] |
| W16-L8 | Red-team log | ≥15 distinct attacks logged (document, email and tool-result vectors); after mitigations no attempt causes a state change or data egress in the sandbox (measured by action logs) (R5 T17-2) |
| W16-L9 | Guard stack measurements | Per-layer block rate and false-positive rate on a 100-case set (50 benign, 50 attack); end-to-end attack success <10% and benign over-block <5% with p95 added latency reported [a starter guard harness is provided; R5 T16-1] |

**Customer thread.** CL16: expectation management. Micro: say what the numbers mean, what they do not, and what you recommend. Simulation: the Linden VP Claims is disappointed by 78% accuracy ("my team said it would be magic"). Artifact: a 3-minute explanation and a revised plan. Rubric R6/R9. Retry within 48 h.
**Carried project.** P5: the eval CI gate is live in the Linden repository and its regression catch is demonstrated to the client actor.
**Resources.** Anthropic effective context engineering https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents [Sourced: R5; V] · Anthropic prompt caching docs https://platform.claude.com/docs/en/build-with-claude/prompt-caching [Sourced: R5; V, multipliers change] · OWASP LLM01 https://genai.owasp.org/llmrisk/llm01-prompt-injection/ [Sourced: R5; V] · Willison: new prompt-injection papers https://simonwillison.net/2025/Nov/2/new-prompt-injection-papers/ [Sourced: R5; V] · Hugging Face LLM course (fine-tuning chapters) https://huggingface.co/learn/llm-course/chapter1/1 [Sourced: R5]
**Stall points and instructor notes.** Flaky CI evals from non-deterministic judges: keep the CI suite mostly deterministic checks plus one validated judge. Red-teaming agents carries real side-effect risk: sandbox accounts, egress controls, read-only tools first **[Foundation risk #12]**. Do not hard-code model names in handouts; cache docs list models that change quickly.
**Exit checklist.** [ ] regression caught by CI [ ] context and cache labs passed [ ] 5 decision memos [ ] training set deduplicated and hash-checked [ ] red-team log with no consequential actions after mitigation [ ] guard rates reported [ ] client expectation call done.

### Week 17 — Fine-tuning lab, agents and frameworks, OWASP mapping
*Phase C1 · Days 81–85 · 40 h: AIC 28, AIO 5, PRJ 4, CUS 3*

**Objectives.** By Friday the learner can:
1. Run a small LoRA/QLoRA fine-tune of an open model and compare it fairly with prompting and few-shot.
2. Choose between a fixed workflow and an agent with measurements; build a bounded agent with budgets, approvals and crash-resume.
3. Re-implement the agent in one framework and say what the framework hid.
4. Map an AI system to the OWASP LLM Top 10 with evidence.
5. Freeze a held-out golden set labelled by someone other than the tuner.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W17-I1 | Instruction: LoRA/QLoRA walkthrough; data requirements; catastrophic forgetting | AIC | INS | D4 | 2 |
| W17-L1 | LoRA/QLoRA lab on an open model of up to 8B parameters (shared GPU pool) | AIC | LAB | D4 | 6 |
| W17-I2 | Instruction: agent patterns; workflow vs agent; budgets and approvals | AIC | INS | D4 | 3 |
| W17-L2 | Workflow-versus-agent bake-off on a triage-and-draft task | AIC | LAB | D4 | 5 |
| W17-L3 | Bounded agent with approvals, budgets and crash-resume | AIC | LAB | D4 | 6 |
| W17-I3 | Instruction: frameworks: LangGraph and one vendor SDK (reading) | AIC | INS | D4 | 1 |
| W17-L4 | Re-implement the bounded agent in LangGraph | AIC | LAB | D4 | 5 |
| W17-L5 | OWASP LLM01–10 control mapping for the P5 system | AIO | LAB | D3 | 4 |
| W17-L6 | Output-as-untrusted lab: model output into HTML, SQL, shell | AIO | LAB | D3 | 1 |
| W17-J1 | P5 hardening: ACL, tracing, cost in place; golden set frozen by an independent labeller | PRJ | PRJ | D4 | 4 |
| W17-C1 | Customer Lab 17: AI compliance conduct: the CISO delegate asks about data flows | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (81) | I1; L1 LoRA lab (GPU queue) | L1 continues | Review block: data cards and training-set reviews |
| Tue (82) | I2; L2 bake-off | L2 continues; L3 bounded agent | Incident drill: `LLM-COSTBURN` (runaway loop) first look |
| Wed (83) | L3 continues | L3 continues; I3 | L4 LangGraph (carry-over) |
| Thu (84) | L4 LangGraph; L5 OWASP mapping | L5 continues; L6 output handling; J1 P5 hardening | Office hours |
| Fri (85) | Checkpoint, demo, quiz | C17 Customer Lab 17 (13:15–16:15) | Retro; pulse; golden set frozen 17:00 |

**What to teach and how**
- **LoRA.** A decision tool, not magic. Compare prompt, few-shot and fine-tune on the *same* held-out set; test for regression on a general mini-set; note that model upgrades may erase a fine-tune advantage. GPU access is queued; teach quota discipline **[Sourced: R5 T10; Foundation §9.3]**. Open-weight licence terms differ; do the licence check in Week 20.
- **Agents.** The pattern vocabulary (chaining, routing, parallelisation, orchestrator-workers, evaluator-optimiser) and "start with the simplest solution". The expected result of the bake-off may be that the chain wins **[Sourced: R5 T7, Anthropic]**. Cap steps, tokens and dollars; require approvals for state-changing actions; resume after a crash without repeating side effects.
- **Frameworks.** Hand-written loop first (done in Week 13), then LangGraph (reported 1.0; status [S]) and read one vendor SDK **[Sourced: R5 §1; claims about SDK versions are single-source [U]]**. The skill must stay tool-independent.
- **OWASP mapping.** One page; each of LLM01–LLM10 gets a control or an explicit accepted risk, with a test or a configuration as evidence **[Sourced: R5 T17; OWASP 2025 list]**.
- **Golden set freeze.** The labeller is a different person than the tuner (recorded); the 100-question held-out set is never used for tuning; plus the separate 50-question dev set **[Repo; Foundation §9.5]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W17-L1 | Three-way comparison with LoRA | Prompt, few-shot and fine-tuned variants all scored on the same held-out set; the fine-tuned model checked for regression on a general mini-set; conclusion states with numbers whether fine-tuning is justified (R5 T10-2) |
| W17-L2 | Bake-off table | Fixed chain and ReAct-style agent compared on a 50-task eval: success rate, mean steps, tokens, p95 latency; written recommendation (R5 T7-1) |
| W17-L3 | Bounded agent | Budget (max 10 tool calls, $0.50 per task) never exceeded across 30 runs; a forced crash resumes without repeating side effects; the approval gate cannot be bypassed by prompt text (R5 T7-2) |
| W17-L4 | LangGraph version | Eval parity with the hand-written agent within a pre-declared tolerance; traces comparable; one paragraph on what the framework hid [Judgment] |
| W17-L5 | OWASP map | All ten LLM risks addressed with a test or configuration as evidence, or a named accepted risk (R5 T17-3) |
| W17-L6 | Output handling tests | XSS and SQL-injection payloads emitted by the model neither execute nor reach the database in 10/10 tests (parameterised queries, escaping, allow-lists) (R5 T16-2) |

**Customer thread.** CL17: AI compliance conduct. Micro: the plain-language answer for "where does the data go, who sees it, is it retained, is it used for training, can you delete it?". Simulation: the CISO delegate actor probes the P5 data flow. Artifact: a one-page plain-language answer sheet; do not quote provider retention terms as fact; read the current contract **[Sourced: R5 T18]**. Rubric R7.
**Carried project.** P5 hardening: access control, tracing and cost in place; the golden set is frozen and the labeller recorded.
**Resources.** Anthropic: building effective agents https://www.anthropic.com/engineering/building-effective-agents [Sourced: R5; V] · Multi-agent research system https://www.anthropic.com/engineering/multi-agent-research-system [Sourced: R5; V] · LangGraph v1 release notes https://docs.langchain.com/oss/python/releases/langgraph-v1 [Sourced: R5; S] · Hugging Face Agents course (method reference) https://huggingface.co/learn/agents-course/unit0/introduction [Sourced: R1] · OWASP LLM Top 10 https://genai.owasp.org/llm-top-10/ [Sourced: R5; V]
**Stall points and instructor notes.** GPU queue conflicts: schedule trios in advance and cap each run. Learners fine-tune before testing a better prompt; make them write the memo first. Do not teach the OpenAI Assistants API (scheduled shutdown [S]). Check framework status again at T−4.
**Exit checklist.** [ ] LoRA comparison written [ ] bake-off table [ ] bounded-agent tests pass [ ] LangGraph parity [ ] OWASP map [ ] output-handling 10/10 [ ] golden set frozen, labeller recorded.

### Week 18 — MCP, orchestration, privacy; G3 week
*Phase C1 · Days 86–90 · **G3 AI build (Day 90)** · 40 h: AIC 20, AIO 5, PRJ 4, ASM 8, CUS 3*

**Objectives.** By Friday the learner can:
1. Build, authenticate and threat-model an MCP server using the current spec revision.
2. Decide whether multi-agent orchestration pays for its cost with a measurement.
3. Document the data flows and risks of an AI system (data-flow diagram, DPIA-lite).
4. **Pass G3:** deliver the P5 system against the held-out golden set with evals in CI.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W18-I1 | Instruction: orchestrator-workers and the cost multiple of multi-agent systems | AIC | INS | D4 | 1 |
| W18-L1 | Orchestrator-workers lab on a five-source brief | AIC | LAB | D4 | 5 |
| W18-I2 | Instruction: MCP: host, client, server; primitives; spec 2026-07-28; auth and threats | AIC | INS | D4 | 3 |
| W18-L2 | MCP server wrapping the mock claims API | AIC | LAB | D4 | 4 |
| W18-L3 | Remote MCP server with scoped authorisation (`MCP-TOKEN`) | AIC | LAB | D4 | 4 |
| W18-L4 | Threat-model a third-party MCP server before installing it | AIC | LAB | D3 | 3 |
| W18-L5 | Guard versus evaluator: decide for one failure mode | AIO | LAB | D5 | 1 |
| W18-I3 | Instruction: privacy for AI systems: data classes, retention, deletion, subprocessors | AIO | INS | D3 | 1 |
| W18-L6 | Data-flow diagram and DPIA-lite for the P5 system | AIO | LAB | D3 | 3 |
| W18-J1 | P5 G3 rehearsal: hostile-evaluator demo; limitations page; error-analysis report | PRJ | PRJ | D4 | 4 |
| W18-A1 | **G3**: held-out golden-set run, CI regression test, hostile-evaluator demo, debrief | ASM | ASM | D4 | 8 |
| W18-C1 | Customer Lab 18: G3 rehearsal and adoption plan | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (86) | I1; L1 orchestrator-workers | L1 continues; I2 MCP | Review block: eval-set and CI reviews |
| Tue (87) | L2 MCP server | L3 remote MCP with auth | Reflection |
| Wed (88) | L4 third-party MCP threat model; I3 | C18 Customer Lab 18 (13:15–16:15) | L6 privacy lab (carry-over) |
| Thu (89) | L6 DPIA-lite; L5 guard vs evaluator | J1 G3 rehearsal; evaluation freeze 17:00 | Office hours; mentors on call |
| Fri (90) | **G3**: harness run and demo | G3 debrief and results | Retro; pulse; gate-health numbers |

**What to teach and how**
- **Orchestrator-workers.** Multi-agent systems cost many times a single agent's tokens; they must beat a single agent by a pre-declared margin *and* report the cost multiple, or the learner documents why not to ship **[Sourced: R5 T7, Anthropic multi-agent post; the 15× figure is Anthropic's own measurement]**.
- **MCP.** Use the current spec revision (2026-07-28): stateless requests, roots, sampling, protocol logging and dynamic client registration deprecated, Tasks and MCP Apps as extensions, token passthrough forbidden. **Pre-2026 tutorials are out of date** **[Sourced: R5 §1, V]**. Teach tool descriptions with the Week-13 wrong-tool eval. Security: confused deputy, SSRF in OAuth discovery, state-handle hijacking, local-server compromise (show the exact command before running anything) **[Sourced: R5 T8, MCP security best practices]**.
- **DPIA-lite.** Every hop: user, app, vector DB, model provider, logs, traces; data class, retention, region, subprocessor. Include derived data (embeddings, caches, summaries, eval sets) **[Sourced: R5 T18]**.
- **G3 prep.** Thursday 17:00 is the evaluation freeze. The assessor runs the harness on Friday against the held-out set. Remind: first miss means remediation, not exit.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W18-L1 | Orchestrator-workers vs single agent | Multi-agent beats single-agent on the rubric score by a pre-declared margin *and* the cost multiple is reported; if not, the learner documents why they would not ship it (R5 T7-3) |
| W18-L2 | MCP server | Works in MCP Inspector and one real client; wrong-tool rate <10% on 20 tasks; stdout never polluted (logging to stderr) (R5 T8-1) |
| W18-L3 | Authorised remote server | 6 negative tests (wrong audience, expired, over-scoped) return 401/403; no token passed through downstream; minimal scopes (R5 T8-2; `MCP-TOKEN`) |
| W18-L4 | Third-party server review | One-page review naming the command executed, filesystem and network reach, scopes and a go/no-go; server run in a container with restricted mounts (R5 T8-3) |
| W18-L5 | Decision note | One failure mode from the Week-14 taxonomy converted to an inline guard and a sampled evaluator; a written decision on which fits and why (R5 T16-3) |
| W18-L6 | DFD + DPIA-lite | Every hop documented with class, retention, region and subprocessor; no hop with undeclared PII; a reviewer finds ≤2 gaps (R5 T18-1) |

**Customer thread.** CL18: G3 rehearsal and adoption plan. Micro: what changes for adjusters on Monday, and who owns what. Simulation: rehearse the demo with the hostile technical evaluator; draft a one-page adoption plan (training, feedback loop, owner). Artifact: the rehearsed demo and the adoption plan. Rubric R4/R8.
**Carried project.** P5 closes at G3. Deliverables: system, eval harness, CI gate, error-analysis report, limitations page.
**G3 (Day 90).** See §3.5. Thresholds: ≥85% faithfulness, ≥70% context precision, cost per transaction within 20% of target, judge TPR and TNR ≥0.85, CI regression suite fails on an injected regression, 0 cross-user leaks on the adversarial ACL set **[Repo; Foundation §6.3]**.
**Resources.** MCP intro https://modelcontextprotocol.io/docs/getting-started/intro [Sourced: R5; V] · MCP architecture (2026-07-28) https://modelcontextprotocol.io/docs/2026-07-28/learn/architecture.md [Sourced: R5; V] · MCP security best practices https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/security_best_practices.md [Sourced: R5; V] · Anthropic Academy MCP course (third-party-described; page returned 403 in R1) https://anthropic.skilljar.com/introduction-to-model-context-protocol [Sourced: R5; S] · NIST AI RMF https://www.nist.gov/itl/ai-risk-management-framework [Sourced: R5; V]
**Stall points and instructor notes.** G3 week carries 20 h of new AI content before the gate; the Thursday freeze is non-negotiable. G3 remediation has no dedicated slack in Phases C1 and C2; retakes use office hours and mentor 1:1s inside existing lab hours, with a parallel-task re-assessment in Week 22 (§3.5). If the pilot shows overrun, move 8 h of Phase-A slack later (Foundation §7.6 warning).
**Exit checklist.** [ ] MCP server built, authorised, threat-modelled [ ] orchestrator-workers measured [ ] DFD and DPIA-lite reviewed [ ] G3 result recorded [ ] remediation plan if needed [ ] P5 handed over with limitations page.

# Phase C2 — AI Operations (Weeks 19–21, Days 91–105)

Also zero slack. P6 (an operations agent for Linden) extends the carried system. The phase builds operational skill: enterprise integration, safe agents, open models, pipelines, multimodal, serving, reliability. It ends with **G4**, a week-long production simulation.

**The P6 system.** Linden's claims-operations team wants an agent that answers status questions and, after approval, takes actions in its systems. It starts read-only; write actions require human approval, an audit log and a budget cap. It reuses the MCP server from Week 18.

### Week 19 — Enterprise integration, human-in-the-loop, agent threat model; P6 kickoff
*Phase C2 · Days 91–95 · 40 h: AIO 29, PRJ 8, CUS 3*

**Objectives.** By Friday the learner can:
1. Put OIDC login in front of an AI app and propagate the end user's identity to retrieval and tools (not a god-mode service account).
2. Build a connector to a messy source (pagination, rate limits, webhooks, deletes) and wrap a legacy system as a typed API and an MCP tool.
3. Design risk-tiered human approval and capture reviewer feedback.
4. Threat-model an agent with tools using the trifecta and least privilege.
5. Plan adoption and run a user-training session.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W19-I1 | Instruction: OIDC/OAuth, on-behalf-of identity, SAML/SCIM (concepts), connectors, legacy adapters | AIO | INS | D6 | 3 |
| W19-L1 | OIDC login in front of the RAG app with per-user retrieval ACL | AIO | LAB | D6 | 6 |
| W19-L2 | Connector to a messy source: pagination, rate limits, webhooks, deletes | AIO | LAB | D6 | 5 |
| W19-L3 | Legacy adapter: SOAP/SFTP batch to a typed API and an MCP tool | AIO | LAB | D6 | 6 |
| W19-I2 | Instruction: HITL design: autonomy levels, review queues, feedback loops | AIO | INS | D5 | 1 |
| W19-L4 | Risk-tiered approval workflow | AIO | LAB | D5 | 3 |
| W19-I3 | Instruction: agent threat modelling and least privilege | AIO | INS | D3 | 1 |
| W19-L5 | Agent threat model and trifecta audit of the P6 design (`MCP-TOKEN`, `AI-INJECT-TOOL`) | AIO | LAB | D3 | 3 |
| W19-L6 | Action allow-list and policy enforced in code for the P6 tools | AIO | LAB | D3 | 1 |
| W19-J1 | **P6 kickoff**: Linden operations agent: read-only first; provenance; audit logs | PRJ | PRJ | D4 | 4 |
| W19-J2 | P6 build: tool set, per-user identity, approvals | PRJ | PRJ | D5 | 4 |
| W19-C1 | Customer Lab 19: adoption planning and a user-training session | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (91) | I1; L1 OIDC and ACL | L1 continues; J1 P6 kickoff | Review block: identity-flow reviews |
| Tue (92) | L2 messy connector | L2 continues; J2 P6 build | Incident drill: `RAG-ACL` regression after a token change |
| Wed (93) | L3 legacy adapter | L3 continues | Office hours |
| Thu (94) | I2; L4 approval workflow | I3; L5 agent threat model; L6 allow-list; J2 | Reflection |
| Fri (95) | Checkpoint, demo, quiz | C19 Customer Lab 19 (13:15–16:15) | Retro; pulse |

**What to teach and how**
- **Identity.** The AI should see only what the *user* may see. Demonstrate the leak when a shared service account queries on the user's behalf. Teach OIDC in practice and SAML/SCIM as concepts only **[Sourced: R5 T21; tool names [U]]**. Ask for sandbox access from the customer in week 1 of any real engagement.
- **Connectors.** Pagination, rate limits, webhooks, idempotency, delete propagation. Build against a deliberately flaky mock.
- **Legacy.** Adapters turn SOAP, SFTP and batch files into clean typed APIs, and then into MCP tools for the AI. Malformed payloads are quarantined, not guessed at.
- **HITL.** Choose autonomy per action (suggest, approve, auto with audit). Approval fatigue and rubber-stamping are the failure mode; show the *real action*, not a model summary **[Sourced: R5 T20]**. Edits and reasons become new eval cases.
- **Agent threat model.** Read tools first; every write tool gets approval or a tight scope; no ambient credentials; no arbitrary URL fetch (exfiltration) **[Sourced: R5 T17]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W19-L1 | OIDC + per-user ACL | User A cannot retrieve user B's documents (20 tests, 0 leaks); token expiry and refresh handled; logout clears the session (R5 T21-1) |
| W19-L2 | Connector | Full sync of 10k records without duplicates; survives 429s and a mid-sync crash; delete events propagate (R5 T21-2) |
| W19-L3 | Legacy adapter | Contract tests pass; malformed payloads quarantined; runs 1 hour under replayed load with no data loss (R5 T21-3) |
| W19-L4 | Approval workflow | 0 high-risk actions executed without approval across 50 runs; reviewers' median decision time <30 s on the provided UI; every decision logged (R5 T20-1) |
| W19-L5 | Agent threat model | Threat table with ≥10 entries; the design removes or gates ≥1 trifecta leg; every write tool has approval or a tight scope; instructor rubric ≥80% [Judgment; R5 T17] |
| W19-L6 | Policy in code | 10/10 disallowed actions rejected by code (not by the prompt) in tests [Judgment; R5 T16] |

**Customer thread.** CL19: adoption. Micro: adoption forces (the anxiety and habit forces from the JTBD model) predict resistance. Simulation: run a 10-minute training session for adjuster actors who push back ("I don't trust it"). Artifact: training outline and FAQ. Rubric R8/R4.
**Carried project: P6 "Agent with tools" kicks off.** Read-only first: status questions answered with citations to records and per-user visibility; audit log of every tool call.
**Resources.** MCP authorization tutorial (2026-07-28; path from the docs index, not read in full in R5) https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/authorization.md [Sourced: R5; V path] · How OpenID Connect works https://openid.net/developers/how-connect-works/ [U] · OWASP LLM Top 10 https://genai.owasp.org/llm-top-10/ [Sourced: R5; V] · Applied LLMs https://applied-llms.org/ [Sourced: R5; V] · Anthropic: writing tools for agents https://www.anthropic.com/engineering/writing-tools-for-agents [Sourced: R5; V]
**Stall points and instructor notes.** Most stalls are identity plumbing, not AI. Keycloak or a test identity-provider tenant is the lab default [U]; stage it in advance. Ensure sandbox credentials are never real customer credentials. Watch for approval UIs that show model summaries instead of actions.
**Exit checklist.** [ ] 0 ACL leaks [ ] connector survives crash [ ] adapter and MCP tool run [ ] 0 unapproved high-risk actions [ ] threat model reviewed [ ] P6 read-only slice working [ ] training session delivered.

### Week 20 — Open models, data pipelines, multimodal
*Phase C2 · Days 96–100 · 40 h: AIO 29, PRJ 8, CUS 3*

**Objectives.** By Friday the learner can:
1. Compare a hosted frontier model with a local open model on cost, latency and quality for specific tasks; serve a model behind an OpenAI-compatible endpoint; size hardware.
2. Build an idempotent incremental pipeline with data-quality gates and reproducible eval artifacts.
3. Extract fields from scans with a vision model, route low-confidence results to a human, and compare with OCR + text.
4. Monitor guard behaviour in production.
5. Complete P6's write-with-approval slice.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W20-I1 | Instruction: open models, quantisation, VRAM sizing, local inference engines, licences | AIO | INS | D5 | 2 |
| W20-L1 | Hosted versus local model on the same 100-prompt eval | AIO | LAB | D5 | 4 |
| W20-L2 | Serve with vLLM behind an OpenAI-compatible endpoint; load test | AIO | LAB | D5 | 3 |
| W20-L3 | Sizing exercise and licence check | AIO | LAB | D5 | 3 |
| W20-I2 | Instruction: data pipelines for AI: idempotency, incremental sync, quality gates, versioned artifacts | AIO | INS | D5 | 2 |
| W20-L4 | Incremental document-sync pipeline | AIO | LAB | D5 | 3 |
| W20-L5 | Data-quality gate (`DATA-SKEW`, `DATA-SILENT`) | AIO | LAB | D5 | 3 |
| W20-L6 | Versioned eval and prompt artifacts | AIO | LAB | D5 | 2 |
| W20-I3 | Instruction: multimodal: vision, PDF, audio; OCR versus vision models | AIO | INS | D4 | 1 |
| W20-L7 | Invoice extraction from 100 scans; vision versus OCR comparison | AIO | LAB | D4 | 5 |
| W20-L8 | Guard hit-rate monitoring and a data-driven threshold change | AIO | LAB | D5 | 1 |
| W20-J1 | P6: write actions with approval; audit log; budget caps | PRJ | PRJ | D5 | 4 |
| W20-J2 | P6: user-training session preparation and adoption plan draft | PRJ | PRJ | D6 | 4 |
| W20-C1 | Customer Lab 20: incident communications | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (96) | I1; L1 hosted vs local | L1 continues; L2 vLLM (GPU queue slot) | Review block: eval tables |
| Tue (97) | L2 load test; L3 sizing | L3 continues; J1 P6 write actions | Reflection |
| Wed (98) | I2; L4 incremental pipeline | C20 Customer Lab 20 (13:15–16:15) | L5 data-quality gate (carry-over) |
| Thu (99) | L5; L6 versioned artifacts | I3; L7 invoice extraction | Office hours |
| Fri (100) | Checkpoint, demo, quiz | L7 continues; L8 guard monitoring; J2 | Incident drill: `LLM-COSTBURN`; retro; pulse |

**What to teach and how**
- **Open models.** Ollama for easy local development, llama.cpp for CPU, Apple Silicon and edge, vLLM for concurrent serving on NVIDIA GPUs. Measure; do not quote benchmarks, which vary by version and hardware **[Sourced: R5 T11; S]**. VRAM ≈ parameters × bytes per parameter + KV cache. Read licence terms (for example community licences with conditions) and flag them to legal; do not assume "open" means "free to use" **[Sourced: R5 T11]**. Swapping a provider must be a base-URL and model-name change.
- **Pipelines.** Re-index only what changed; propagate deletes (a forbidden document that is still retrievable is a breach); quarantine bad files; version everything so a past score can be reproduced **[Sourced: R5 T15]**.
- **Multimodal.** Pick between OCR + text LLM, a vision model or a layout parser by accuracy, cost and latency; validate numbers with checksums and totals; route low-confidence extractions to a human; redact PII in images **[Sourced: R5 T12; capabilities change monthly, verify at delivery]**.
- **Guard monitoring.** A guard with an unmonitored hit rate is a false comfort.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W20-L1 | Comparison table | Quality, latency and cost per 1,000 requests for a hosted frontier model and a local quantised model of about 7–8B; a clear statement of which tasks the small model passes (≥ threshold) and which it fails (R5 T11-1) |
| W20-L2 | Served endpoint + load test | p50 and p95 latency and throughput at 1, 8 and 32 concurrent users; the app switches provider by changing only the base URL and model name (R5 T11-2) |
| W20-L3 | Sizing sheet | 3 hardware profiles; fit at 8k and 32k context predicted; one verified by measurement within ~20% of memory; licence terms read and a summary sent to the legal actor (R5 T11-3) |
| W20-L4 | Sync pipeline | A re-run is idempotent (no duplicates); a deletion removes vectors within one run; a 10% bad-file injection is quarantined and reported (R5 T15-1) |
| W20-L5 | Quality gate | The pipeline fails fast with clear messages on 5 injected violations (R5 T15-2; `DATA-SKEW`, `DATA-SILENT`) |
| W20-L6 | Reproducible artifacts | Each eval run records the git SHA, dataset hash, prompt version and model config ID; any past score is reproducible within tolerance (R5 T15-3) |
| W20-L7 | Extraction + comparison | Field-level accuracy ≥90% on clean scans; a degradation report on the 20 degraded; routing catches ≥80% of wrong extractions; accuracy, cost and latency table for OCR + text LLM versus a vision model with a recommendation (R5 T12-1/2) |
| W20-L8 | Guard dashboard | Per-guard block rate visible; a seeded shift in the attack mix is visible in a replay; one threshold change justified with data [Judgment] |

**Customer thread.** CL20: incident communications. Micro: update cadence, bottom line first, no surprises. Simulation: a staged outage; write a status update every 30 minutes, make the bad-news call to the VP Claims, and produce a one-page executive incident summary. Artifact: the updates and summary. Rubric R5/R6. Prepares for G4.
**Carried project.** P6: write actions work with approval, an audit trail and budget caps; training session drafted.
**Resources.** Red Hat on llama.cpp vs vLLM https://developers.redhat.com/articles/2026/06/15/llamacpp-vs-vllm-choosing-right-local-llm-inference-engine [Sourced: R5; S] · Red Hat vLLM vs Ollama https://www.redhat.com/en/topics/ai/vllm-vs-ollama [Sourced: R5; S] · Hugging Face Hub docs https://huggingface.co/docs/hub [U] · Anthropic vision docs https://platform.claude.com/docs/en/build-with-claude/vision [U, not fetched] · Chip Huyen, *Designing Machine Learning Systems* https://www.oreilly.com/library/view/designing-machine-learning/9781098107956/ [Sourced: R5; S]
**Stall points and instructor notes.** GPU pool contention is the main risk this week (a cohort of 15 needs about 1.5× the repo's 10-learner pool, or on-demand rental **[Assumption; Foundation §9.3]**). Book slots per trio on Monday. Model quantisation formats and engine versions change fast: re-verify at T−4.
**Exit checklist.** [ ] local vs hosted table [ ] vLLM load-test report [ ] pipeline idempotent [ ] quality gate fails on violations [ ] extraction ≥90% on clean [ ] P6 write slice with approvals [ ] incident update drill done.

### Week 21 — Production AI, reliability, G4 week
*Phase C2 · Days 101–105 · **G4 Operate under failure (Day 105)** · 40 h: AIO 22, PRJ 8, ASM 8, CUS 2*

**Objectives.** By Friday the learner can:
1. Containerise and deploy an AI service with Helm; scale a worker on queue depth; read GPU and KV-cache metrics.
2. Define SLOs and burn-rate alerts for an AI system and cut cost per request with evals as the guard.
3. Fail over between providers and report the cost of fallbacks.
4. Document a system with a system card and a slice analysis.
5. **Pass G4:** operate the P5/P6 system through five injected failures with ≥99% availability, self-detecting each incident.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W21-I1 | Instruction: deploying AI services: containers, Helm, queue workers, GPU basics, managed vs self-hosted | AIO | INS | D5 | 2 |
| W21-L1 | Deploy the RAG/agent service on kind with Helm | AIO | LAB | D5 | 4 |
| W21-L2 | Queue-based async worker with an autoscaling signal | AIO | LAB | D5 | 3 |
| W21-L3 | GPU walk-through on the shared pool (`K8S-PENDING-GPU`) | AIO | LAB | D5 | 3 |
| W21-I2 | Instruction: SLOs, burn-rate alerts and cost management for AI systems | AIO | INS | D5 | 1 |
| W21-L4 | SLOs, burn-rate alerts, cost dashboard, 40% cost cut | AIO | LAB | D5 | 3 |
| W21-L5 | Provider failover through the gateway (`LLM-PROVIDER`) | AIO | LAB | D5 | 2 |
| W21-I3 | Instruction: responsible AI: system cards, slice analysis, use-case triage | AIO | INS | D3 | 1 |
| W21-L6 | System card and slice analysis for the P5/P6 system | AIO | LAB | D3 | 2 |
| W21-L7 | Guard layering peer review | AIO | LAB | D3 | 1 |
| W21-J1 | P6 final: demo to the Linden operations team; safety review; user-training session | PRJ | PRJ | D4 | 4 |
| W21-J2 | G4 preparation: runbooks, dashboards, rollback, incident roles and rota | PRJ | PRJ | D5 | 4 |
| W21-A1 | **G4**: five injection windows (`PROD-SIM-1..5`), postmortem, debrief | ASM | ASM | D5 | 8 |
| W21-C1 | Customer Lab 21: customer communications during the simulation | CUS | CUS | D6 | 2 |
| | **Week total** | | | | **40** |

**Day by day** (the simulation runs Monday to Thursday inside normal working hours; the assessed windows are the 1-hour injection responses, the postmortem and the debrief)

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (101) | I1; L1 Helm deploy; J2 runbooks | L2 queue workers; **PROD-SIM-1 (provider outage), 1 h window** | Review block: runbook swap |
| Tue (102) | **PROD-SIM-2 (poisoned document), 1 h window**; L3 GPU walk-through | I2; L4 SLOs and cost | Reflection |
| Wed (103) | L4 continues; L5 provider failover | **PROD-SIM-3 (10× traffic spike), 1 h window**; I3; L6 system card | Office hours |
| Thu (104) | **PROD-SIM-4 (prompt regression), 1 h window**; J1 P6 final demo | **PROD-SIM-5 (6× cost burn), 1 h window from 13:15**; then C21 customer communications (15:00–17:00) as the customer keeps demanding updates | L7 guard review (late); J2 |
| Fri (105) | Postmortems (1.5 h) | **G4 debrief (1.5 h)**; results | Retro; pulse |

**What to teach and how**
- **AI deployment.** Package, probe, scale on queue depth rather than CPU for LLM-backed workers; no secrets in image layers; managed endpoints versus self-hosting by constraint. GPU basics: VRAM, batch vs interactive, requests as `nvidia.com/gpu`; KServe and llm-d are awareness-level only **[Sourced: R5 T14; S]**.
- **AI SLOs.** Availability and p95 latency plus a *sampled quality* signal (a validated judge on a trace sample). Cost per request is a first-class metric; the target is ≥40% below the Week-15 baseline with ≤2 points of eval drop **[Judgment; extends R5 T13-3]**.
- **Failover.** Fallbacks multiply cost and latency; track the fallback rate **[Sourced: R5 T13; LiteLLM docs, S]**.
- **System card and slice analysis.** Measured numbers, not adjectives; an average can hide a failing subgroup **[Sourced: R5 T19]**. Starter template and a pre-sliced dataset are provided **[Judgment]**.
- **G4 stance.** A role-played customer demands status during injections. Game days should include a non-engineer voice **[Sourced: R3, AWS Well-Architected guidance]**. Injections come from pre-approved templates, with stop conditions tied to alarms and run inside learners' sandbox accounts **[Sourced: R2]**.

**Labs: deliverables and pass criteria**

| ID | Deliverable | Pass criteria |
|---|---|---|
| W21-L1 | Helm deployment | A rolling update under load causes 0 failed requests; the readiness probe gates traffic; no secret in any image layer (scan proves it) (R5 T14-1) |
| W21-L2 | Queue-driven workers | Scales from 1 to N under backlog and back; no message lost when a worker is killed (R5 T14-2) |
| W21-L3 | GPU analysis | Reads GPU utilisation and KV-cache metrics; names the bottleneck (compute, memory or batching); sizes replicas for N concurrent users; `K8S-PENDING-GPU` diagnosed (R5 T14-3) |
| W21-L4 | SLOs and cost | 3 SLOs with burn-rate alerts (availability, p95 latency, sampled quality); cost per request ≥40% below the Week-15 baseline with ≤2-point eval drop (routing, caching, trimming) (R5 T13-3, extended) |
| W21-L5 | Failover | Primary-provider failure fails over with no user-visible error at ≤20% injected error rate; fallback rate and cost multiple reported (R5 T13-2, extended) |
| W21-L6 | System card + slices | Card contains measured numbers; ≥1 subgroup with a materially worse rate found, mitigated and re-measured (R5 T19-1/2) |
| W21-L7 | Guard review | The peer's guard stack is re-tested on the 100-case set; attack success <10% and over-block <5% still hold; ≥2 gaps found or a written certification [Judgment] |

**Customer thread.** CL21: customer communications during an incident, run live during PROD-SIM-5. Learners keep the customer informed every 30 minutes and file an executive summary. Artifact: the updates and the summary. Rubric R5/R6.
**Carried project.** P6 closes with a demo to the Linden operations actors, a safety review (lethal-trifecta re-audit) and the training session. The G4 preparation produces the runbooks used in the simulation.
**G4 (Day 105).** See §3.6. Thresholds: ≥99% availability, every incident self-detected, runbooks complete, unit economics reported, OWASP LLM01–10 control map with evidence **[Repo; Foundation §6.3]**.
**Resources.** AWS Well-Architected on game days https://docs.aws.amazon.com/wellarchitected/latest/framework/rel12-bp05.html [Sourced: R3] · AWS Fault Injection Service https://docs.aws.amazon.com/fis/latest/userguide/what-is.html [Sourced: R2] · KServe 0.17 (awareness) https://kserve.github.io/website/blog/kserve-0.17-release [Sourced: R5; S] · llm-d (awareness) https://github.com/llm-d/llm-d [Sourced: R5; S] · LiteLLM routing https://docs.litellm.ai/docs/routing [Sourced: R5; S] · NIST AI RMF https://www.nist.gov/itl/ai-risk-management-framework [Sourced: R5; V] · Microsoft responsible-AI principles https://www.microsoft.com/en/ai/principles-and-approach [Sourced: R5; S]
**Stall points and instructor notes.** G4 week has the highest overlap of new content and assessment; stagger lab content around the injection windows. The lab engineer owns injection timing and stop conditions; the customer-craft coach plays the demanding customer. The week ends with a facilitated blameless debrief (Etsy guide) and postmortems authored by the learners **[Sourced: R3]**. Retakes: no dedicated slack until Week 22 (§3.6).
**Exit checklist.** [ ] P6 accepted [ ] G4 result recorded [ ] each incident self-detected or logged as a miss [ ] postmortems filed [ ] system card with measured numbers [ ] remediation plan if needed.

# Phase D — Customer craft and embedded pod (Weeks 22–24, Days 106–120)

No new technical blocks. Hours go to P7 (a scoping sprint with no build), the **embedded pod on real low-risk work** and the flagship P8 engagement ending in G5. The Customer Lab continues every week.

**Pod assumptions [Assumption: to be arranged by T−4].** Five pods of three. Each pod is paired with one senior FDE mentor for 3–5 real, low-risk tickets from an internal or partner team. "Low risk" means: internal users, reversible changes, no customer personal data, no production writes without mentor approval, and read-only access where possible. NDAs and access are arranged before Week 22. The pod model follows Ramp's pod structure **[Sourced: R3 §1.7, secondhand]**. If real work cannot be arranged, the fallback is a stage-4 "living client" simulation with mentor-reviewed internal tickets; record that the real-world exposure was not delivered **[Judgment]**.

### Week 22 — Scoping sprint; pod onboarding; flagship scope
*Phase D · Days 106–110 · 40 h: CUS 4, PRJ 32, SLK 4*

**Objectives.** By Friday the learner can:
1. Run three discovery calls with different prospects, decompose each problem and map stakeholders.
2. Write a PR/FAQ and a two-page staged proposal with success metrics, defence ready.
3. Start a real pod assignment with a mentor: scope tickets, set up access, write the first plan.
4. Merge three individual proposals into one pod scope for the flagship (Linden Phase 2).

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W22-J1 | P7 brief and preparation: three vague prospects; discovery plans | PRJ | PRJ | D6 | 4 |
| W22-J2 | P7 discovery calls with three prospects (recorded), decomposition, stakeholder maps | PRJ | PRJ | D6 | 8 |
| W22-J3 | P7 PR/FAQ and two-page staged proposal for one prospect | PRJ | PRJ | D6 | 4 |
| W22-J4 | P8 pod onboarding: real low-risk tickets with a senior FDE mentor | PRJ | PRJ | all | 10 |
| W22-J5 | P8 flagship: merge proposals into the pod's Linden Phase 2 scope; client sign-off | PRJ | PRJ | D6 | 6 |
| W22-C1 | Customer Lab 22: panel defence of the proposal; scope negotiation with the sponsor | CUS | CUS | D6 | 4 |
| W22-S1 | G3/G4 parallel-task re-assessments for retakers; wellbeing check; mentor introductions | SLK | SLK | all | 4 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (106) | J1 P7 brief; discovery plans | J2 discovery calls 1–2 | Review block: call recordings, peer feedback |
| Tue (107) | J2 discovery call 3; decomposition and stakeholder maps | J4 pod onboarding (mentor kickoff) | Reflection |
| Wed (108) | J3 PR/FAQ and proposal | C22 Customer Lab 22 (13:15–17:15): panel defence and scope negotiation | Office hours |
| Thu (109) | J4 pod onboarding (access, tickets, first plan) | J5 flagship scope: pod merges proposals | S1 retake sessions |
| Fri (110) | Checkpoint, demo, quiz (pod demo of week) | J5 client sign-off; J4 pod plan check | Retro; pulse |

**What to teach and how**
- **Scoping sprint, no build.** The three prospects are synthetic vignettes **[Judgment]**: (A) a Kestrel expansion (cross-dock scheduling), (B) a regional clinic network (no-show reduction with sensitive data), (C) **Linden Phase 2** (claims triage automation). Each has different constraints and stakeholders. Use hidden-fact sheets: facts are revealed only to well-formed, past-event questions; polite flattery for bad questions counters the "colleague actors are too helpful" problem **[Sourced: R4 §3.2]**.
- **PR/FAQ.** Write the launch press release and the hard FAQ before building; iterate the problem definition until clear or drop it **[Sourced: R4 §2.4, Amazon Working Backwards]**. Every scope states out-of-scope and the riskiest assumption.
- **Pod onboarding.** Shadow, then reverse shadow: for the first tickets the mentor drives, then the learner drives with the mentor observing without changing state **[Sourced: R3 §1.6, Google SRE]**. Mentors do not assess their own mentees' gates **[Repo: Ops Guide]**.
- **Merge into one scope.** Three individual proposals become one pod scope; disagreements are resolved by evidence, not seniority.

**Acceptance for project work** (no lab pass-criteria table this week)

| ID | Deliverable | Acceptance |
|---|---|---|
| W22-J1–J3 | P7 outputs | PR/FAQ and a 2-page staged proposal reviewed by two assessors; rubric R2 scores ≥3 on every criterion; a decomposition recording with ≥2 explicit branches and a first executable slice; riskiest assumption testable within 2 weeks |
| W22-J4 | Pod plan | Each pod has a written plan for 3–5 low-risk tickets, access verified, mentor sign-off rules agreed |
| W22-J5 | Flagship scope | Client actor signs a scope that lists the nine deliverables and the out-of-scope items; three planted complications remain hidden |

**Customer thread.** CL22 (4 h): panel defence of the proposal before a mock sponsor, skeptical technical lead and compliance owner (stage 2 adversarial panel, now with the learner's own proposal); then negotiate scope when the sponsor asks for more. Rubric R2/R7/R9. Retry within 48 h.
**Resources.** Pyramid principle https://managementconsulted.com/pyramid-principle/ [Sourced: R4] · Amazon Working Backwards (PDF) https://d1.awsstatic.com/events/reinvent/2020/Working_Backwards_Amazons_approach_to_innovation_INO206.pdf [Sourced: R4] · Impact mapping https://www.amplitude.com/blog/impact-map [Sourced: R4; V] · Latent Space on FDE practice https://latent.space/p/forward-deployed-engineer-best-practices [Sourced: R4] · SVPG on FDEs https://www.svpg.com/forward-deployed-engineers [Sourced: R4] · Pragmatic Engineer on FDEs https://newsletter.pragmaticengineer.com/p/forward-deployed-engineers [Sourced: R4]
**Stall points and instructor notes.** Learners rush to solutions inside discovery calls; stop and replay. Over-structured decomposition: remind them it is a tool. Pod access delays are the top risk; escalate on Day 1 (the lab engineer and program manager own this).
**Exit checklist.** [ ] 3 discovery recordings [ ] PR/FAQ and proposal submitted [ ] pod plan and access ready [ ] flagship scope signed [ ] retake re-assessments scheduled or done.

### Week 23 — Embedded pod; flagship sprint 1; pod review
*Phase D · Days 111–115 · **Pod review (Day 115)** · 40 h: CUS 3, PRJ 26, ASM 5, SLK 6*

**Objectives.** By Friday the learner can:
1. Deliver real low-risk work under mentor review: standups, pull requests, a weekly update to a real stakeholder.
2. Progress the flagship: infrastructure as code and data/RAG extension while a planted complication surfaces.
3. Receive and act on mentor, stakeholder and assessor feedback at the Pod review.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W23-J1 | P8 embedded pod work on real low-risk tickets; mentor standups and PRs; weekly stakeholder update | PRJ | PRJ | all | 18 |
| W23-J2 | P8 flagship sprint 1: IaC and the data/RAG extension; complication 1 revealed | PRJ | PRJ | D2 | 8 |
| W23-A1 | **Pod review**: mentor and stakeholder feedback, work samples, portfolio check, readiness pre-read | ASM | ASM | D6 | 5 |
| W23-S1 | Pod and portfolio catch-up; remediation | SLK | SLK | all | 6 |
| W23-C1 | Customer Lab 23: communicating with a real stakeholder (weekly update, one hard message) | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (111) | J1 pod work (standup 09:15 with mentor) | J1 pod work; J2 flagship sprint | Review block: mentor PR reviews |
| Tue (112) | J2 flagship sprint (complication 1 revealed) | J1 pod work | Incident drill (`FIELD-BLIND`: diagnosable only through an operator proxy) |
| Wed (113) | J1 pod work | J2 flagship sprint | S1 catch-up |
| Thu (114) | J1 pod work; weekly stakeholder update sent | C23 Customer Lab 23 (13:15–16:15; moved from Friday for the pod review) | S1 portfolio preparation |
| Fri (115) | **A1 Pod review**: pod sessions with mentor and stakeholder | A1 individual feedback; portfolio check; readiness pre-read | Pulse; clean break before the final week |

**What to teach and how**
- **Real work discipline.** Every change has a pull request reviewed by the mentor; no production write without approval; read-only first. Bespoke code is tagged "pattern or bespoke?" in review **[Foundation §2.3]**.
- **Honest stakeholder messages.** One weekly written update (answer-first) plus one hard message (a delay or a limitation), reviewed by the customer-craft coach **[Sourced: R4 rubrics R5/R6]**.
- **Fresh-eyes preparation.** Learners swap runbooks across pods and attempt a cold start in Week 24 **[Sourced: R4 §3.2, SRE handover]**.
- **Complication 1 of 3.** Planted complication families: a residency or air-gap rule, an unreliable legacy source, a stakeholder who was never told **[Repo; Foundation §8.5]**.

**Acceptance for project work**

| ID | Deliverable | Acceptance |
|---|---|---|
| W23-J1 | Pod work | ≥3 tickets merged or delivered with mentor-approved PRs; each PR passes tests; weekly stakeholder update sent and acknowledged |
| W23-J2 | Flagship sprint 1 | IaC applies cleanly in a fresh sandbox; data/RAG extension working on the main corpus; complication 1 identified and logged with options |
| W23-A1 | Pod review | Mentor and stakeholder written feedback on the behavioural anchors; work-sample review; portfolio ≥60% complete; readiness pre-read signed |

**Customer thread.** CL23: real-stakeholder communication. Stage 4 (real-world exposure). Rubric R5/R6; the real stakeholder gives feedback in the Pod review.
**Resources.** Google SRE training book (shadowing, reverse shadowing) https://sre.google/static/pdf/TrainingSiteReliabilityEngineers.pdf [Sourced: R3; read first-hand] · SRE book on evolving engagement https://sre.google/sre-book/evolving-sre-engagement-model/ [Sourced: R4] · First Round Review on FDEs https://review.firstround.com/so-you-want-to-hire-a-forward-deployed-engineer/ [Sourced: R4] · a16z on FDE titles https://a16z.com/forward-deployed-job-titles/ [Sourced: R4]
**Stall points and instructor notes.** Learners find real work slower and messier than simulations; this is the point. Mentors need protected hours and calibration on what to review; avoid mentors rewriting rather than coaching. Early-warning indicators (missed check-ins) go to the wellbeing lead within 48 h.
**Exit checklist.** [ ] 3 pod tickets delivered [ ] flagship sprint 1 done [ ] pod review complete [ ] feedback acknowledged [ ] portfolio ≥60%.

### Week 24 — Flagship, handover, G5
*Phase D · Days 116–120 · **G5 Capstone defence and readiness panel (Day 120)** · 40 h: CUS 3, PRJ 22, ASM 12, SLK 3*

**Objectives.** By Friday the learner can:
1. Take a system from scoped build to production-grade handover with the nine deliverables.
2. Hand it to an operations team that runs it for a day and files two seeded incidents.
3. Defend the work and their own readiness to a four-person panel.

**Hours ledger**

| ID | Activity | Block | Type | Dom | h |
|---|---|---|---|---|---|
| W24-J1 | P8 flagship hardening: eval gate, runbook, observability, security evidence; complications 2 and 3 | PRJ | PRJ | all | 12 |
| W24-J2 | P8 handover: ops team operates the system for a day; two seeded incidents; fresh-eyes runbook cold test; retrospective; product-feedback memo; executive summary | PRJ | PRJ | D6 | 10 |
| W24-A1 | **G5**: dress rehearsal, defence, individual technical oral, final competency evidence session, observing two other pods, results and feedback, portfolio submission | ASM | ASM | all | 12 |
| W24-S1 | Retrospective, outcomes survey, alumni and mentor handoff | SLK | SLK | all | 3 |
| W24-C1 | Customer Lab 24: the handover meeting and the product-feedback loop | CUS | CUS | D6 | 3 |
| | **Week total** | | | | **40** |

**Day by day**

| Day | AM | PM | Review / craft |
|---|---|---|---|
| Mon (116) | J1 hardening (complication 2 revealed) | J1 hardening | Review block: security evidence review |
| Tue (117) | J1 hardening (complication 3 revealed) | J2 handover pack ready; runbook swap between pods | Reflection |
| Wed (118) | J2 ops team operates the system; two seeded incidents; cold test | C24 Customer Lab 24 (13:15–16:15): handover meeting | J2 retrospective and feedback memo |
| Thu (119) | A1 dress rehearsal; defences begin (pods 1–2) | A1 defences (pods 3–4) | S1 retrospective (late) |
| Fri (120) | A1 defence (pod 5); individual orals; observe peers | A1 competency evidence; **panel deliberation and readiness decisions**; results and feedback sessions | Portfolio submission; closing circle; pulse |

*Scheduling note.* With five pods and one four-person panel, defences run Thursday afternoon to Friday morning (about 90 minutes per pod plus 20-minute individual orals). The readiness decision is Day 120. This straddles Days 119–120 and is a pragmatic scheduling interpretation of "G5 at Day 120" **[Judgment]**.

**What to teach and how**
- **Hardening.** Reuse the carried P5/P6 system and extend it for Linden Phase 2. Each learner leads one workstream (retrieval and eval; agent and tools; platform and operations) and is individually accountable for matching deliverables **[Judgment]**.
- **Handover.** Use Google's production-readiness stages as the model: engagement, analysis, improvements, training, onboarding, continuous improvement. An ops team that did not build the system must be able to deploy, monitor, roll back and handle two seeded incidents using only the pack **[Sourced: R4 §2.9, §3.3 rubric R8]**. The product-feedback memo classifies each piece of code as pattern or bespoke.
- **Complications.** Exactly three, planted: they test judgment and escalation, not heroics.

**Acceptance for project work**

| ID | Deliverable | Acceptance |
|---|---|---|
| W24-J1 | Production-grade system | All nine deliverables present (§4.3); eval gate meets G3 thresholds on the main corpus; SLOs live; OWASP LLM01–10 control map with evidence; each complication documented with the decision taken and why |
| W24-J2 | Handover | A cold operator completes deploy, monitor and rollback from the pack alone and handles both seeded incidents; known issues and ownership documented; product-feedback memo written |

**Customer thread.** CL24: the handover meeting with the role-played ops team and the retrospective. Rubric R8/R9.
**G5 (Day 120).** See §3.7 and §4. Four-person panel: a senior FDE, a security lead, an ML lead and a customer-facing leader **[Repo; Foundation §6.3]**.
**Resources.** SRE book on engagement and onboarding https://sre.google/sre-book/evolving-sre-engagement-model/ [Sourced: R4] · Etsy debriefing guide https://codeascraft.com/2016/11/17/debriefing-facilitation-guide/ [Sourced: R3] · Pragmatic Engineer on FDEs https://newsletter.pragmaticengineer.com/p/forward-deployed-engineers [Sourced: R4] · NIST AI RMF https://www.nist.gov/itl/ai-risk-management-framework [Sourced: R5; V]
**Stall points and instructor notes.** Learners polish features instead of the handover pack; set the pack deadline on Tuesday evening. The panel must score the individual component, not only the pod. Calibrate assessors on the recorded G3 and G4 examples before Thursday. Remind learners about the retake and outcomes policy (§3.7) before the decision day.
**Exit checklist.** [ ] nine deliverables [ ] cold test passed [ ] defence given [ ] individual oral done [ ] outcome and feedback delivered [ ] portfolio submitted [ ] outcomes survey completed.

---

## 3. Gates and reviews

Gate placement, thresholds and rubric templates come from Foundation §6; this section fixes formats, artifacts and timing for the 24-week program. Pass criteria reused from the repo's Assessment Pack are marked **[Repo]**.

### 3.1 Common rules and G0 (Baseline)

**Rules for every gate** (Foundation P10, §6.4, §6.8)
1. **Novel environment, randomised fault variant**, so memory is not what is tested. Fresh sandbox account for G1 and G4.
2. **Rubrics are published in Week 1.** Template A (technical work sample): "Meets" (3) required in every core criterion; no criterion at 1. Template B (nine-dimension craft rubric) is scored at G2, G4 and G5.
3. **Two independent assessors at G2, G4 and G5**; calibration on recorded examples before each cohort and before each of those gates; an inter-assessor delta above 1.0 forces a calibration session.
4. **Mentors never assess their own mentees' gates** **[Repo: Ops Guide]**.
5. **Healthy first-attempt pass band: 70–85%.** Below means the curriculum is too steep; above means too easy **[Repo]**. More than 40% of the cohort stalling at the same point in the same lab is a curriculum defect logged with an owner and a date.
6. **Retakes** follow Foundation §6.6: remediation inside scheduled slack, a parallel task, options not automatic exit. §3.9 below shows where the slack is in this program.
7. **Gate time is assessment time** (ASM block). G0 is counted in ONB (Foundation §7.2).

**Craft dimensions scored at each event** (Foundation Appendix A #16: each event declares its dimensions; the threshold is the mean of all scored dimension-events, with no single dimension's mean below 3.0) **[Judgment]**:

| Event | Dimensions scored (of the nine in Template B) |
|---|---|
| G2 | Architecture, Security posture, Communication |
| G4 | Troubleshooting, Execution, Judgment, Communication |
| G5 | All nine: Discovery, Scoping, Architecture, Execution, Troubleshooting, Security posture, Communication, Judgment, Handover |

**G0 Baseline (Day 2, diagnostic only)** **[Repo: Assessment Pack, adapted]**

| Part | Time | Content |
|---|---|---|
| Written exam | 2 h (Monday afternoon) | 60 questions. Blueprint [Judgment]: D1 12, D2 12, D3 8, D4 12, D5 6, D6 10. **No multiple-choice above L1**; the written score is overridden by the practical **[Repo]** |
| Practical | 3 h (Tuesday morning) | A broken environment with three layered faults (`G0-LAYERED`); observed and logged: time to first signal, hints, stall points |
| Mock discovery call | 1 h (Tuesday afternoon) | Scripted-vague Kestrel actor; recorded; blind double-marked later; the baseline for the customer-skill measurement |

Outputs: L0–L4 per domain; **lane A (needs the most scaffolding), B (typical) or C (fast-track with extension tasks)** [Judgment; the repo's lane formulas are not reproduced]; an Individual Learning Plan. No pass or fail. Expected baseline for a median new grad [Judgment]: D1 L1–L2, D2 L0–L1, D3 L0–L1, D4 L0–L1, D5 L0, D6 L0–L1.

### 3.2 G1 Platform: rebuild from scratch (Day 40, Week 8)

| Item | Specification |
|---|---|
| Setup | A fresh sandbox account, a randomised fault variant, a stopwatch, a starter repository with application code only |
| **Stage A (60 min)** | Provision and deploy an **observable, containerised service via IaC and CI** from scratch **[Repo: G1]** |
| Stage A pass | Under **60 minutes** · **zero console actions** (checked in the audit trail) · **3 SLOs live** · **≥70% test coverage** · basic scans green **[Repo]** |
| **Stage B (45 min)** | Deploy the same service to a provided Kubernetes cluster; a horizontal autoscaler scales 1→3 under load; a killed pod recovers in ≤30 s; one `K8S-*` fault diagnosed from evidence [Judgment] |
| Why two stages | Foundation §6.3 adds autoscaling and Kubernetes to the 24-week G1 while keeping the 60-minute figure. Running them in the same 60 minutes is not realistic; this plan keeps the repo's 60-minute criteria for Stage A and adds Stage B as a separate timed stage. **Interpretation flagged for the sponsor (§8.5).** |
| Artifacts | Repository, pipeline run URL, dashboard link, runbook stub |
| Debrief | Same day; time to first signal, hints, stall points logged |
| Assessors | One assessor plus a proctor |
| Learner time | 5 h (briefing, Stage A and B, artifacts, debrief) |
| Retake | A first miss: targeted plan in Week 9 slack (3 h), parallel-task re-assessment in Week 10 slack (4 h) on a different fault variant |

### 3.3 G2 Secure delivery review (Day 50, Week 10)

| Item | Specification |
|---|---|
| Format | A panel of 2–3 plays an enterprise security team; a **45-minute** defence **[Repo: Assessment Pack §4]** |
| Artifacts, submitted 24 hours before | (1) architecture and data-flow diagram with trust boundaries; (2) SBOM matching the deployed image digest; (3) scan reports with triage rationale; (4) secrets-management design; (5) IAM/RBAC matrix; (6) control-to-framework mapping; (7) incident response plan **[Repo]** |
| Question bank | About 30 hidden questions, 12 asked, including AI-specific ones ("What stops a document in our corpus from instructing your model?") **[Repo; Foundation §6.3]** |
| Pass | Every artifact present and valid; zero critical CVEs; no secret resolvable from the repository; "I don't know" scores higher than a fabricated answer **[Repo]** |
| Craft | Architecture, Security posture, Communication (two independent assessors) |
| Learner time | 6 h (artifact validation, defence, debrief, scoring session) |
| Retake | Week 10 slack (4 h) and Weeks 11–12 consolidation hours |

### 3.4 Mid-program review (Day 60, Week 12)

Not pass or fail. Its purpose is to map each learner's evidence and plan the AI phase. In the 12-week program this question sits inside G2; in the 24-week program it moves here **[Foundation §3.3]**.

| Part | Time | Content |
|---|---|---|
| Evidence interview | 1.5 h | Two independent assessors score L0–L4 per domain from labs, gates and projects |
| Behavioural self-rating | 0.5 h | Learner rates themselves on the five anchors (Unaware, Aware, Practitioner, Independent, Authority); compared with assessors |
| **Customer-skill re-test** | 1 h | A recorded discovery call with the same persona type as G0, blind double-marked against the G0 recording **[Foundation §12.4]** |
| Planning | 1 h | Updated learning plan; remediation actions with dates; AI-phase support (mentor, lane) |
| Question | | "Would we put this person in front of a low-risk customer?" (Galvanize-style midpoint question, adapted **[Sourced: R3 §4.3]**) |

Expected evidence at Day 60 [Judgment]: D1 L2–L3, D2 L2–L3, D3 L2, D4 L1, D5 L1, D6 L2. A learner below L2 in D1 or D2 gets named support before Week 13 because the AI phases have no slack.

### 3.5 G3 AI build (Day 90, Week 18)

| Item | Specification |
|---|---|
| Subject | The P5 system, delivered against a business metric with evals in CI |
| Setup | A held-out **100-question golden set** (frozen in Week 17; labeller is not the tuner) plus the separate **50-question dev set**; a hostile technical evaluator in the demo **[Repo; Sourced: R5]** |
| Pass criteria | **≥85% faithfulness** · **context precision ≥70%** · **cost per transaction within 20% of target** **[Repo: Pack G3]** · LLM judge calibrated to human labels (**TPR and TNR ≥0.85**) · a regression suite in CI that **fails on a deliberately injected prompt regression** · **0 cross-user leaks on an adversarial ACL set** · a limitations page and an error-analysis report **[Foundation §6.3; Sourced: R5 T5/T6/T21]** |
| Evidence | Harness run by the assessor on Friday; trace links; eval CI run history; cost report from traces |
| Craft | Rubric R4 (demo) and R5 (limitations honesty) as evidence; G3 is assessed on Template A (no craft score) |
| Assessors | One internal plus one external, calibrated beforehand |
| Learner time | 8 h (harness run, demo, error-analysis walk-through, debrief) |
| Retake | No dedicated slack in Phases C1 and C2. Remediation uses office hours and mentor 1:1s inside existing lab hours; **parallel-task re-assessment in Week 22 slack (4 h)**. **Recommendation:** if the pilot shows overrun, move 8 h of Phase-A slack (Weeks 6 and 9) into Week 19 (Foundation §7.6 warning) |
| If G3 is not yet passed | The learner continues P6 using the reference P5 build so the carried system is not blocked (§8.1 risk 6) |

### 3.6 G4 Operate under failure (Day 105, Week 21)

| Item | Specification |
|---|---|
| Subject | The P5/P6 system run for a week with injected failures; a role-played customer demands status |
| Injections | `PROD-SIM-1..5`: provider outage; poisoned document; 10× traffic spike; prompt regression; 6× cost burn **[Repo: Pack G4]**, one per assessed 1-hour window Monday to Thursday, plus a 1.5 h postmortem and a 1.5 h debrief on Friday (total 8 h) |
| Guardrails | Pre-approved templates; stop conditions tied to alarms; runs only inside learners' sandbox accounts **[Sourced: R2, AWS FIS guidance]** |
| Pass | **≥99% availability** · **every incident self-detected** (detected by the learner's alert before the assessor or customer says so) · runbooks complete (alert links to a tested runbook) · unit economics reported (cost per transaction, with the 6× burn explained) **[Repo]** · OWASP LLM01–10 control map with evidence **[Foundation §6.3]** |
| Craft | Troubleshooting, Execution, Judgment, Communication (two independent assessors) |
| Non-engineer voice | The customer-craft coach plays the customer (AWS Well-Architected guidance) **[Sourced: R3]** |
| Retake | **Week 22 slack (4 h)** shared with G3; a 3-hour parallel injection set with a different order and variants |

### 3.7 G5 Capstone defence and readiness panel (Day 120, Week 24)

| Item | Specification |
|---|---|
| Subject | The flagship P8 engagement (§4). Pods of three, each learner leading a workstream and defending individually |
| Brief | **Exactly three planted complications** **[Repo]** |
| Panel | Four people: a senior FDE, a security lead, an ML lead and a customer-facing leader **[Repo; Foundation §6.3]** |
| Format per pod | 30 min presentation · 30 min technical deep dive · 20 min adversarial questions · 10 min business framing; then a 20-minute **individual technical oral** per learner |
| Evidence | Nine deliverables (§4.3); the handover cold-test result; Pod-review feedback; the full portfolio |
| Scoring | Template A on technical criteria, Template B (all nine dimensions), rubric R8 (handover) as evidence; panel deliberation |
| Outcome rules | Foundation §6.5: **Workstream Owner** (L2+ in all six, L3+ in at least three, craft mean ≥3.5, all gates passed, no dimension mean below 3.0) · **Supervised** (L2+ in all six, L3 in one or two, craft ≥3.0) · **Conditional** (one domain at L1 or craft 2.5–3.0) · **Not yet ready** |
| Appeal | One written appeal to an assessor who was not on the panel, within 5 working days [Judgment] |
| Learner time | 12 h |
| Retake | A Conditional outcome gets 4–6 weeks of targeted remediation and a mini-G5 defence; total time for completers is capped at 1.25× program length (30 weeks) so outcomes can be reported fairly **[Foundation §6.6]** |

### 3.8 Pod review (Day 115, Week 23)

Not pass or fail; it is an input to G5. Mentor and stakeholder written feedback on the behavioural anchors; a work-sample review of merged pull requests; a portfolio check (≥60% complete); a readiness pre-read signed by the learner. It projects the likely outcome (Workstream Owner, Supervised or Conditional). A mentor-raised safety or conduct concern triggers an immediate fit conversation. **5 learner hours.**

### 3.9 Where the retake hours are

Remediation happens inside scheduled slack (Foundation §5.4 item 8). Slack in this program (64 h):

| Week | Slack (h) | Main use |
|---|---|---|
| 6 | 11 | Consolidation week |
| 8 | 4 | Mock G1 |
| 9 | 5 | G1 remediation |
| 10 | 7 | G1/G2 remediation, retro |
| 11 | 13 | Consolidation; retakes |
| 12 | 11 | Retakes; AI environment check |
| 22 | 4 | **G3 and G4 re-assessments** |
| 23 | 6 | Pod and portfolio catch-up |
| 24 | 3 | Retrospective |

**Weeks 13–21 hold zero slack by design**, so remediation of G3 and G4 depends on office hours and Week 22. This is the known weak point (Foundation §7.6) and appears in §8.1.

### 3.10 Gate health and calibration

| Metric | Target | Source |
|---|---|---|
| First-attempt pass rate per gate | 70–85% | **[Repo]** |
| Inter-assessor delta (5-point craft rubric) | ≤1.0 | **[Repo]** |
| Stall points >40% of the cohort in one lab | Log defect, owner, fix date before the next cohort | **[Repo]** |
| Lab completion within SLA | ≥80% | **[Repo]** |
| Competency lift, Day 2 to exit | ≥2.0 levels | **[Assumption, Foundation §6.8]** |
| Calibration | Two assessors on recorded examples before the cohort, then before G2, G4 and G5 | **[Repo; Sourced: R3, R4]** |

---

## 4. Capstone: Flagship engagement (P8)

### 4.1 Shape

A longer, multi-phase engagement for **Linden Claims Services, Phase 2**, extending the carried P5/P6 system. It runs Weeks 22–24 (the build and handover) but rests on everything before it: the scoping sprint (P7) gives the scope, the G4 simulation has already tested operations, and the pod review provides real-world feedback. Staged deliverables follow the CS224N pattern (proposal, milestone, demo, report) **[Sourced: R1]**.

| Stage | When | Output |
|---|---|---|
| Discover and scope | Week 22 (P7 plus W22-J5) | PR/FAQ, two-page staged proposal, merged pod scope signed by the client actor |
| Build | Weeks 22–24 (embedded pod work alongside) | Working system on the main corpus; IaC; CI/CD with the eval gate |
| Operate | Weeks 21 (G4) and 24 (ops handover day) | Runbook proven by a cold operator; SLOs live |
| Handover | Week 24 (W24-J2) | Handover pack; seeded-incident exercise; product-feedback memo |
| Defend | Week 24 (G5) | Panel defence and individual oral |

### 4.2 The brief (synthetic; numbers are training assumptions)

Linden's claims intake receives thousands of documents a week. Phase 2 asks for **claims triage automation**: classify and extract fields from incoming documents (including scanned forms), route to the right team, and answer adjusters' SOP questions with citations, all under the Phase-1 constraints (data stays in-region; SSO with per-user access; an air-gapped analyst enclave; a legacy claims system that exports SFTP batches). The sponsor's goal is a reduction in **time to triage per claim**, with a minimum routing accuracy to be agreed during discovery. Learners propose the metric and thresholds in the PR/FAQ; the client actor accepts or negotiates them. **[Judgment, synthetic data only]**

### 4.3 The nine deliverables

| # | Deliverable | Domains | Evidence at G5 |
|---|---|---|---|
| 1 | Scoping document with measurable success criteria, out-of-scope and riskiest assumption | D6 | PR/FAQ and signed scope (W22) |
| 2 | Architecture document with ADRs and security control mapping | D2, D3, D6 | ADRs; threat model; OWASP map |
| 3 | Working system deployed via IaC, meeting a stated eval threshold | D2, D4 | G3 thresholds met on the main corpus |
| 4 | CI/CD pipeline including the eval regression gate | D2, D4 | Pipeline history; injected-regression catch |
| 5 | Observability with SLOs and burn-rate alerts, plus LLM tracing and a cost/latency dashboard | D2, D5 | Live dashboards; alert test |
| 6 | Security evidence pack: SBOM, scans, IAM matrix, threat model, OWASP LLM01–10 map, system card | D3 | Pack reviewed by the security lead |
| 7 | Cost model with unit economics | D5 | Cost per transaction vs target |
| 8 | Operator runbook and handover plan, plus the product-feedback memo ("pattern vs bespoke") | D5, D6 | Cold-test result |
| 9 | One-page non-technical executive summary | D6 | Rubric R5 |

### 4.4 Personas and who plays them

| Persona | Role in the engagement | Played by |
|---|---|---|
| VP Claims Operations | Sponsor; wants speed; sets the metric | Customer-craft coach |
| Senior adjuster | End user; reveals truth only to good questions | Trained volunteer (alumni or staff) |
| CISO delegate | Blocks on data; asks plain-language questions | Security lead or trained volunteer |
| Compliance officer | Not told early (complication 3); asks for a DPIA and human review | Trained volunteer |
| Platform manager (outsourced) | Five-day change SLA; owns the legacy export | Lab engineer |
| Ops team lead and operators | Run the system for a day; file two seeded incidents | Alumni TAs and staff **[Sourced: R4 §3.5]** |
| Real stakeholders | Pod phase: real low-risk tickets | Internal or partner team |

Actors are trained to be unhelpful in realistic ways and use hidden-fact sheets **[Foundation §8.4]**.

### 4.5 The three planted complications [Judgment]

| # | Revealed | Complication | What it tests |
|---|---|---|---|
| 1 | Week 23 | A residency rule: scanned claim images may not leave the enclave, so the extraction model must run locally | Open-model serving (W20), sizing, constrained environments, honest trade-offs on quality |
| 2 | Week 24, Monday | The legacy SFTP batch contains duplicates and late corrections | Idempotent pipelines (W20), deletes, quarantine |
| 3 | Week 24, Tuesday | A compliance stakeholder who was never told demands a DPIA and human review of adverse decisions | HITL design (W19), privacy (W18), stakeholder handling, scope trade |

### 4.6 Team structure and individual accountability

A pod of three; each learner leads one workstream and answers for it in the individual oral:

| Workstream | Scope | Primary domains |
|---|---|---|
| Retrieval and evaluation | Retrieval quality, golden-set discipline, eval gate | D4 |
| Agent, tools and security | Tool design, approvals, injection defences, OWASP map | D4, D3 |
| Platform and operations | IaC, CI/CD, SLOs, cost, runbook, handover | D2, D5 |

All three share the scope, the demo and the handover. Suggestion **[Judgment]**: within each pod, rotate who leads which workstream during P5 and P6 (Weeks 13–21) so every learner has led each one before the capstone.

### 4.7 Panel format

See §3.7. The panel is four people (senior FDE, security lead, ML lead, customer-facing leader) with an external member where possible **[Sourced: R3 §4.9]**. Assessors are calibrated on the recorded G3 and G4 examples before the defences.

### 4.8 Scoring

| Component | Weight | Basis |
|---|---|---|
| Customer artifacts (PR/FAQ, scope, updates, exec summary) | 30% | R4 §3.5b suggestion **[Sourced: R4; inference]** |
| Technical outcome (system, evals, security evidence, SLOs) | 30% | |
| Handover cold test | 20% | Rubric R8 |
| Judgment and ownership (complications, escalation, individual oral) | 20% | Rubric R9 |

These weights describe the P8 component only. Readiness outcomes still follow the threshold rules in §3.7 (the Foundation's composite score is for support and ranking, not the outcome, Foundation §6.10). Early projects weigh the customer thread at least equal to code (Foundation P7).

### 4.9 Portfolio (nine items, shown to employers) **[Sourced: R3 §4.6, adapted]**

1. The customer-style dossier (discovery notes, scope, architecture, delivery plan, status updates, handoff). 2. Two shipped integrations or workflows with tests, README and runbook. 3. Two or more written blameless postmortems (one from G4). 4. A code-review sample (reviews given and received). 5. A recorded 10-minute demo to a non-technical audience. 6. A skills self-rating signed off by a mentor. 7. A system card and an eval report. 8. A reusable asset contributed before the final gate (cohort contract item 6). 9. The product-feedback memo.

---

## 5. Lab catalogue and reconciliation

This section is **generated from the weekly ledgers** by a script, so the catalogue cannot drift from the weekly plans. Lab IDs are `W{week}-L{n}`. Pass criteria are in each week's *Labs* table. Domains follow Foundation §3.2.

### 5.1 Lab catalogue (121 labs, 465 hours)

| ID | Lab | Block | Dom | Wk | h | Fault scenarios |
|---|---|---|---|---|---|---|
| W1-L1 | Shell and git workflow lab | SWF | D1 | 1 | 3 |  |
| W1-L2 | Debugging lab: logs, `pdb`, reading a stack trace | SWF | D1 | 1 | 3 |  |
| W1-L3 | Python lab: a small CLI with tests | SWF | D1 | 1 | 4 |  |
| W1-L4 | Ship it I: AWS tour, CLI/SSO, deploy the starter service from a template | CLD | D2 | 1 | 4 |  |
| W1-L5 | Ship it II: containerise it, trigger CI, add the LLM-backed endpoint through the gateway | DOP | D2 | 1 | 3 |  |
| W2-L1 | Python lab: resilient HTTP client (timeouts, retries with backoff, tests) | SWF | D1 | 2 | 7 |  |
| W2-L2 | Linux lab: permissions and process break-fix | SWF | D1 | 2 | 3 |  |
| W2-L3 | IAM and S3 lab: roles, policies, bucket policies, presigned URLs | CLD | D2 | 2 | 7 |  |
| W2-L4 | Docker lab: multi-stage build, compose with Postgres, push to ECR, scan with Trivy | DOP | D2 | 2 | 8 |  |
| W2-L5 | CI lab: test, build, push pipeline for the lab service | DOP | D2 | 2 | 4 |  |
| W2-L6 | Secrets lab: gitleaks pre-commit, AWS Secrets Manager | DSO | D3 | 2 | 2 | `SEC-SECRETS` |
| W3-L1 | Network debugging lab: `dig`, `curl`, `openssl` | SWF | D1 | 3 | 4 | `NET-CA`, `NET-DNS` |
| W3-L2 | Web lab: reverse proxy, caching headers, certificate chain | SWF | D1 | 3 | 3 | `NET-PROXY` |
| W3-L3 | Linux networking and load: `ss`, packet capture, load test | SWF | D1 | 3 | 3 | `NET-MTU` |
| W3-L4 | Compute lab: EC2 with SSM access, EBS snapshot restore, ALB + ASG with health checks | CLD | D2 | 3 | 7 |  |
| W3-L5 | CI/CD lab: matrix tests, caching, artifacts, protected environments, OIDC keyless deploy | DOP | D2 | 3 | 8 |  |
| W3-L6 | Terraform first steps: codify the Week-2 IAM/S3 setup; remote state introduced | DOP | D2 | 3 | 4 |  |
| W3-L7 | SCA and secrets in CI: dependency audit, gitleaks; fail build on high severity | DSO | D3 | 3 | 2 |  |
| W4-L1 | SQL lab: model Kestrel shipments, analytic queries, index with `EXPLAIN` | SWF | D1 | 4 | 3 |  |
| W4-L2 | API lab: FastAPI CRUD service on Postgres with idempotency keys | SWF | D1 | 4 | 3 |  |
| W4-L3 | Managed data and edge lab: RDS restore drill; HTTPS via Route 53, CloudFront, ACM | CLD | D2 | 4 | 7 |  |
| W4-L4 | CI lab: pipeline runs `fmt`, `validate`, `plan` on pull requests | DOP | D2 | 4 | 4 |  |
| W4-L5 | Terraform lab: the web stack (ALB, ASG, RDS) from code with reusable modules | DOP | D2 | 4 | 9 |  |
| W4-L6 | SAST lab: Semgrep in CI, triage seeded findings, branch protection | DSO | D3 | 4 | 3 |  |
| W5-L1 | Data lab: messy CSV/Excel to validated Parquet/Postgres with tests | SWF | D1 | 5 | 3 |  |
| W5-L2 | VPC lab: design, build, predict and test reachability | CLD | D2 | 5 | 7 |  |
| W5-L3 | Terraform lab: dev and stage from one module set; `IAC-DRIFT` | DOP | D2 | 5 | 8 | `IAC-DRIFT` |
| W5-L4 | Terraform lab: import hand-made resources; tagging policy; clean destroy | DOP | D2 | 5 | 4 |  |
| W5-L5 | Kubernetes lab 1: kind cluster, deploy the service, debug a broken manifest | DOP | D2 | 5 | 4 |  |
| W5-L6 | Supply-chain lab: SBOM (CycloneDX), CVE gate, pinned base image | DSO | D3 | 5 | 3 |  |
| W6-L1 | Code reading and review lab | SWF | D1 | 6 | 4 | `APP-RACE` |
| W6-L2 | AWS governance lab: audit trail, alarms, permission boundary, budget action | CLD | D2 | 6 | 7 | `SEC-ROOT` |
| W6-L3 | Kubernetes lab 2: config, secrets, ingress; `K8S-IMGPULL`, `K8S-CRASHLOOP` | DOP | D2 | 6 | 3 | `K8S-CRASHLOOP`, `K8S-IMGPULL` |
| W7-L1 | AWS networking and IAM deep lab | CLD | D2 | 7 | 6 | `NET-IPV6` |
| W7-L2 | Kubernetes lab 3: stateful workload, probes, rolling updates | DOP | D2 | 7 | 5 | `K8S-OOM` |
| W7-L3 | Kubernetes lab 4: Helm chart and Kustomize overlays for P1 | DOP | D2 | 7 | 5 | `K8S-NETPOL-DNS` |
| W7-L4 | Observability lab: instrument P1, dashboards, three SLOs, alerts | DOP | D5 | 7 | 4 |  |
| W7-L5 | IaC scan and policy gate lab | DSO | D3 | 7 | 2 | `SEC-UNENCRYPTED` |
| W8-L1 | Access and data operations lab: SSO roles only, RDS point-in-time restore, parameter groups | CLD | D2 | 8 | 6 |  |
| W8-L2 | Kubernetes lab 5: HPA under load, disruption budget | DOP | D2 | 8 | 5 | `K8S-HPA-NOMETRICS` |
| W8-L3 | Game day 1 (`GAMEDAY-1`): Wheel of Misfortune on the Kestrel stack, then a blameless postmortem | DOP | D5 | 8 | 6 | `GAMEDAY-1` |
| W8-L4 | DAST lab: scan a deliberately vulnerable app in CI and triage | DSO | D3 | 8 | 2 |  |
| W9-L1 | Serverless and queues lab: events, dead-letter queues, idempotent consumer | CLD | D2 | 9 | 6 |  |
| W9-L2 | Kubernetes timed drills | DOP | D2 | 9 | 3 | `K8S-DISKPRESSURE`, `K8S-PVC-TERM`, `K8S-WEBHOOK-CERT`, `K8S-WEBHOOK-REJECT` |
| W9-L3 | Kubernetes security lab: least-privilege RBAC and default-deny | DSO | D3 | 9 | 3 | `SEC-NETPOL-OPEN`, `SEC-RBAC` |
| W9-L4 | Supply-chain lab: sign images in CI, verify at admission | DSO | D3 | 9 | 3 |  |
| W9-L5 | Threat-model workshop: STRIDE and data-flow for the P3 integration | DSO | D3 | 9 | 3 |  |
| W10-L1 | FinOps lab: tags, budget actions, rightsizing, unit-cost report | CLD | D2 | 10 | 3 |  |
| W10-L2 | G2 artifact build: the seven artifacts | DSO | D3 | 10 | 4 |  |
| W10-L3 | Mock security review 1: panel of staff, 45 minutes | DSO | D3 | 10 | 3 |  |
| W10-L4 | AI preview: indirect injection demo and the lethal trifecta | DSO | D3 | 10 | 2 | `AI-INJECT-INDIRECT` |
| W11-L1 | Tabular baseline with a leakage trap | AIC | D4 | 11 | 3 | `ML-LEAKAGE` |
| W11-L2 | Tokenisation and embeddings: nearest-neighbour search over 500 documents | AIC | D4 | 11 | 2 |  |
| W11-L3 | LLM-versus-classifier bake-off on 300 labelled tickets | AIC | D4 | 11 | 2 |  |
| W11-L4 | Async batch processing with bounded concurrency, retries, resume | AIC | D4 | 11 | 4 |  |
| W12-L1 | Model card reading and failure explanation for a client | AIC | D4 | 12 | 3 |  |
| W12-L2 | Data-cleaning notebook to a tested module | AIC | D4 | 12 | 3 |  |
| W12-L3 | FastAPI endpoint with typed I/O, health check, container | AIC | D4 | 12 | 3 |  |
| W12-L4 | Corpus profiling and dev-set preparation (starter corpus of about 200 documents) | AIC | D4 | 12 | 2 |  |
| W13-L1 | Extraction lab: 100 documents to a pydantic schema; constrained vs prompt-only | AIC | D4 | 13 | 5 |  |
| W13-L2 | Prompt A/B lab on a held-out set (3 iterations) | AIC | D4 | 13 | 4 |  |
| W13-L3 | Break-it lab: 10 inputs that violate the schema or confuse the prompt | AIC | D4 | 13 | 4 |  |
| W13-L4 | Hand-written tool loop with three tools against a mock API | AIC | D4 | 13 | 4 |  |
| W13-L5 | Tool-description tuning on an ambiguous six-tool set | AIC | D4 | 13 | 3 |  |
| W13-L6 | Safe-action tool: idempotency key, dry-run, per-call authorisation | AIC | D4 | 13 | 3 |  |
| W13-L7 | Tracing lab: instrument the P5 starter assistant | AIO | D5 | 13 | 4 |  |
| W14-L1 | Baseline RAG over the 200-document starter corpus | AIC | D4 | 14 | 5 |  |
| W14-L2 | Ingestion lab: PDFs, HTML, Word; metadata and parse-failure report | AIC | D4 | 14 | 5 |  |
| W14-L3 | Answer behaviour lab: citations and "I don't know" | AIC | D4 | 14 | 4 |  |
| W14-L4 | Error-analysis sprint on 60 traces | AIC | D4 | 14 | 4 |  |
| W14-L5 | Golden set and assertion suite (40 cases) | AIC | D4 | 14 | 5 |  |
| W14-L6 | Reliability harness: injected 429s, timeouts, malformed responses | AIO | D5 | 14 | 4 |  |
| W15-L1 | Retrieval ablation lab | AIC | D4 | 15 | 5 |  |
| W15-L2 | Access-controlled RAG lab | AIC | D4 | 15 | 5 | `RAG-ACL` |
| W15-L3 | RAG failure taxonomy lab | AIC | D4 | 15 | 5 |  |
| W15-L4 | Judge calibration lab | AIC | D4 | 15 | 4 | `EVAL-JUDGE` |
| W15-L5 | RAG evals lab: retrieval and generation scored separately | AIC | D4 | 15 | 4 |  |
| W15-L6 | Cost lab part 1: token accounting, baseline, caching test | AIO | D5 | 15 | 2 |  |
| W15-L7 | Trifecta audit of three agent architectures | AIO | D3 | 15 | 2 |  |
| W16-L1 | CI regression gate | AIC | D4 | 16 | 6 | `LLM-REGRESS` |
| W16-L2 | Trajectory eval basics: reading transcripts, grader bugs, consistency | AIC | D4 | 16 | 3 |  |
| W16-L3 | Context budget audit of a 30-turn run | AIC | D4 | 16 | 3 |  |
| W16-L4 | Compaction vs notes vs sub-agent on an overflowing task | AIC | D4 | 16 | 3 | `LLM-CTX` |
| W16-L5 | Cache-friendly prompt layout | AIC | D4 | 16 | 2 |  |
| W16-L6 | Decision memos for five customer scenarios | AIC | D4 | 16 | 3 |  |
| W16-L7 | Same-eval comparison: prompt vs few-shot; prepare the training set for the LoRA lab | AIC | D4 | 16 | 3 |  |
| W16-L8 | Red-team your own RAG and agent | AIO | D3 | 16 | 3 | `AI-INJECT-INDIRECT`, `AI-INJECT-TOOL` |
| W16-L9 | Layered guard stack: measure each layer | AIO | D3 | 16 | 1 |  |
| W17-L1 | LoRA/QLoRA lab on an open model of up to 8B parameters (shared GPU pool) | AIC | D4 | 17 | 6 |  |
| W17-L2 | Workflow-versus-agent bake-off on a triage-and-draft task | AIC | D4 | 17 | 5 |  |
| W17-L3 | Bounded agent with approvals, budgets and crash-resume | AIC | D4 | 17 | 6 |  |
| W17-L4 | Re-implement the bounded agent in LangGraph | AIC | D4 | 17 | 5 |  |
| W17-L5 | OWASP LLM01–10 control mapping for the P5 system | AIO | D3 | 17 | 4 |  |
| W17-L6 | Output-as-untrusted lab: model output into HTML, SQL, shell | AIO | D3 | 17 | 1 |  |
| W18-L1 | Orchestrator-workers lab on a five-source brief | AIC | D4 | 18 | 5 |  |
| W18-L2 | MCP server wrapping the mock claims API | AIC | D4 | 18 | 4 |  |
| W18-L3 | Remote MCP server with scoped authorisation | AIC | D4 | 18 | 4 | `MCP-TOKEN` |
| W18-L4 | Threat-model a third-party MCP server before installing it | AIC | D3 | 18 | 3 |  |
| W18-L5 | Guard versus evaluator: decide for one failure mode | AIO | D5 | 18 | 1 |  |
| W18-L6 | Data-flow diagram and DPIA-lite for the P5 system | AIO | D3 | 18 | 3 |  |
| W19-L1 | OIDC login in front of the RAG app with per-user retrieval ACL | AIO | D6 | 19 | 6 |  |
| W19-L2 | Connector to a messy source: pagination, rate limits, webhooks, deletes | AIO | D6 | 19 | 5 |  |
| W19-L3 | Legacy adapter: SOAP/SFTP batch to a typed API and an MCP tool | AIO | D6 | 19 | 6 |  |
| W19-L4 | Risk-tiered approval workflow | AIO | D5 | 19 | 3 |  |
| W19-L5 | Agent threat model and trifecta audit of the P6 design | AIO | D3 | 19 | 3 | `AI-INJECT-TOOL`, `MCP-TOKEN` |
| W19-L6 | Action allow-list and policy enforced in code for the P6 tools | AIO | D3 | 19 | 1 |  |
| W20-L1 | Hosted versus local model on the same 100-prompt eval | AIO | D5 | 20 | 4 |  |
| W20-L2 | Serve with vLLM behind an OpenAI-compatible endpoint; load test | AIO | D5 | 20 | 3 |  |
| W20-L3 | Sizing exercise and licence check | AIO | D5 | 20 | 3 |  |
| W20-L4 | Incremental document-sync pipeline | AIO | D5 | 20 | 3 |  |
| W20-L5 | Data-quality gate | AIO | D5 | 20 | 3 | `DATA-SILENT`, `DATA-SKEW` |
| W20-L6 | Versioned eval and prompt artifacts | AIO | D5 | 20 | 2 |  |
| W20-L7 | Invoice extraction from 100 scans; vision versus OCR comparison | AIO | D4 | 20 | 5 |  |
| W20-L8 | Guard hit-rate monitoring and a data-driven threshold change | AIO | D5 | 20 | 1 |  |
| W21-L1 | Deploy the RAG/agent service on kind with Helm | AIO | D5 | 21 | 4 |  |
| W21-L2 | Queue-based async worker with an autoscaling signal | AIO | D5 | 21 | 3 |  |
| W21-L3 | GPU walk-through on the shared pool | AIO | D5 | 21 | 3 | `K8S-PENDING-GPU` |
| W21-L4 | SLOs, burn-rate alerts, cost dashboard, 40% cost cut | AIO | D5 | 21 | 3 |  |
| W21-L5 | Provider failover through the gateway | AIO | D5 | 21 | 2 | `LLM-PROVIDER` |
| W21-L6 | System card and slice analysis for the P5/P6 system | AIO | D3 | 21 | 2 |  |
| W21-L7 | Guard layering peer review | AIO | D3 | 21 | 1 |  |

### 5.2 Hours reconciliation

**By block** (ledger total versus the Foundation §7.2 budget):

| Block | Ledger h | Budget h | Match |
|---|---|---|---|
| Onboarding and baseline (`ONB`) | 16 | 16 | yes |
| Software fundamentals (`SWF`) | 56 | 56 | yes |
| Cloud / AWS (`CLD`) | 72 | 72 | yes |
| DevOps / Kubernetes (`DOP`) | 104 | 104 | yes |
| DevSecOps (`DSO`) | 44 | 44 | yes |
| AI Core (`AIC`) | 190 | 190 | yes |
| AI Operations and Security (`AIO`) | 110 | 110 | yes |
| Customer Labs (`CUS`) | 72 | 72 | yes |
| Projects and capstone (`PRJ`) | 184 | 184 | yes |
| Assessment and gates (`ASM`) | 48 | 48 | yes |
| Slack (`SLK`) | 64 | 64 | yes |
| **Total** | **960** | **960** | yes |

**By phase** (capacity = 40 h × weeks):

| Phase | Ledger h | Capacity h |
|---|---|---|
| A (1–10) | 400 | 400 |
| B (11–12) | 80 | 80 |
| C1 (13–18) | 240 | 240 |
| C2 (19–21) | 120 | 120 |
| D (22–24) | 120 | 120 |

**By activity type** (realised mix versus the Foundation's 15 / 60 / 15 / 10 target):

| Type | Hours | % of 960 |
|---|---|---|
| Instruction (`INS`) | 111 | 11.6 |
| Labs (`LAB`) | 465 | 48.4 |
| Project sessions (`PRJ`) | 184 | 19.2 |
| Customer Labs (`CUS`) | 72 | 7.5 |
| Gates and reviews (`ASM`) | 48 | 5.0 |
| Slack (`SLK`) | 64 | 6.7 |
| Onboarding incl. G0 (`ONB`) | 16 | 1.7 |

Instruction including the 30-minute micro-lesson inside each Customer Lab: **123 h (12.8%)**. Labs plus projects: **649 h (67.6%)**. Dedicated assessment is 5.0% because G0 sits in onboarding and gate preparation is charged to labs and slack (the Foundation's own table has assessment at 5.0%). Customer-craft exposure including embedded hours is about 15% (Foundation §7.2 memo).

**Lab hours by domain:** D1 43 h · D2 137 h · D3 56 h · D4 154 h · D5 58 h · D6 17 h.

### 5.3 How this was verified

A script parsed every ledger row (ID, activity, block, type, domain, hours) in the 24 weekly sections and checked that: (1) each week sums to **40 h**; (2) each block equals its Foundation budget (table above); (3) each phase equals 40 h × its weeks and each block within each phase equals Foundation §7.6; (4) every `LAB` row has a pass-criteria row and vice versa; (5) no duplicate IDs. All checks passed for the version of the plan published here. After any edit to a ledger, re-run the script and regenerate this section.

### 5.4 Fault-scenario coverage (Foundation §9.6, all 40 scenarios)

| Scenario | Used in weeks |
|---|---|
| `NET-PROXY` | 3 |
| `NET-CA` | 3 |
| `NET-DNS` | 3 |
| `NET-MTU` | 3 |
| `NET-IPV6` | 7 |
| `APP-RACE` | 4, 6 |
| `IAC-DRIFT` | 5 |
| `K8S-IMGPULL` | 6 |
| `K8S-CRASHLOOP` | 6 |
| `K8S-PENDING-GPU` | 21 |
| `K8S-OOM` | 7 |
| `K8S-NETPOL-DNS` | 7 |
| `K8S-WEBHOOK-CERT` | 9 |
| `K8S-PVC-TERM` | 9 |
| `K8S-DISKPRESSURE` | 9 |
| `K8S-HPA-NOMETRICS` | 8 |
| `K8S-WEBHOOK-REJECT` | 9 |
| `GAMEDAY-1` | 8 |
| `SEC-ROOT` | 6 |
| `SEC-SECRETS` | 2 |
| `SEC-RBAC` | 9 |
| `SEC-NETPOL-OPEN` | 9 |
| `SEC-UNENCRYPTED` | 7, 10 |
| `AI-INJECT-INDIRECT` | 10, 16 |
| `AI-INJECT-TOOL` | 16, 19 |
| `MCP-TOKEN` | 18, 19 |
| `RAG-FAIL` | 14, 15 |
| `RAG-ACL` | 15, 19 |
| `LLM-REGRESS` | 16 |
| `LLM-CTX` | 16 |
| `LLM-PROVIDER` | 21 |
| `LLM-COSTBURN` | 17, 20 |
| `EVAL-JUDGE` | 15 |
| `ML-LEAKAGE` | 11 |
| `DATA-SKEW` | 20 |
| `DATA-SILENT` | 7, 20 |
| `PROD-SIM` | 21 |
| `FIELD-AIRGAP` | 11 |
| `FIELD-BLIND` | 23 |
| `G0-LAYERED` | 1 |

Scenarios keyed by family (`RAG-FAIL` = variants 1..6, `GAMEDAY` = variants 1..5, `PROD-SIM` = injections 1..5) count once each, as in Foundation §9.6. 40 of 40 scenarios appear in this plan. The 8 AI-specific scenarios need the RAG corpus and tracing in place, so they are built after T−4 (§7.2).

---

## 6. Measurement, mentoring, cohort checkpoints and optional work

### 6.1 Telemetry and measurement

Six capture layers, reused from the repo's data model and renamed to this competency model **[Repo: Handbook Part III; Foundation §6.9]**:

| Layer | What is captured | When | Owner |
|---|---|---|---|
| 1. Competency | L0–L4 per domain (`d1_swe … d6_craft`) with assessor evidence | Day 2, Day 60, Day 120 | Assessors |
| 2. Lab telemetry | `time_to_first_signal`, `stall_point` (enumerated per fault), `hints_taken`, attempt count. **AI fields:** `eval_pass_rate`, `trace_url`, `cost_per_run`, `prompt_version`, `model_config_id` (never a model name), `judge_tpr_tnr` | Every lab | Lab engineer |
| 3. Gates | Scores, assessor deltas, retake history, first-attempt pass rate | Every gate and review | Program lead |
| 4. Craft rubric | Nine dimensions by event (§3.1), two assessors | G2, G4, G5 | Customer-craft coach |
| 5. Program health | Completion, logged vs scheduled hours, pulse (stress, load, belonging), cost per learner against the $500 cap, GPU utilisation, instructor hours per learner-week | Weekly | Program manager |
| 6. Outcomes | Manager survey at 30 days and 6 months; supervisor rating at Day 90 after exit; time to first merged PR in the field | After exit | Program lead |

**Customer-skill measurement** (the weakest evidence in the design, so treated as a pilot hypothesis; Foundation §12.4, R4 §5):

| Skill | Early measurement | Late measurement | Method |
|---|---|---|---|
| Discovery (rubric R1) | G0 mock call (Week 1) and Customer Lab 1 | Mid re-test (Week 12) and P7 discovery calls (Week 22) | Recorded; blind, double-marked against the same rubric |
| Decomposition (rubric R3) | Customer Lab 6 (Week 6) | P7 decomposition (Week 22) | Recorded; blind, double-marked |
| Scoping (rubric R2) | Week-4 scope one-pager | P7 PR/FAQ and proposal (Week 22) | Two assessors |
| Handover (rubric R8) | Week-8 P1 handover | Week-24 cold test | Cold operator pass/fail plus rubric |
| Overall | R1–R9 trend across the 72 Customer Lab hours | | Retry deltas recorded |

**Decision rule:** a gain of ≥1 level on discovery and scoping between early and late measurement **[Judgment]**. If absent, revise the thread before the next cohort. No independent evidence exists in the public literature that these methods improve FDE outcomes **[Sourced: R4 §5]**.

**Program metrics** (targets from Foundation §6.8 and §12.4; 24-week specifics marked):

| Metric | Target | Action on breach |
|---|---|---|
| First-attempt gate pass rate | 70–85% | Review difficulty and teaching |
| Inter-assessor delta | ≤1.0 | Calibration session |
| Cohort completion | ≥85% | Review schedule protection and early warning |
| Median logged hours | ≤44 per week | Follow up within 48 h |
| Competency lift Day 2 to Day 120 | ≥2.0 levels [Assumption] | Review instruction-to-lab ratio |
| Learner-reported readiness | ≥4.0 / 5 | Investigate the phase |
| Lab cost | ≤$500 per learner per month | Gateway and SCP review |
| GPU utilisation | 60–85% | Resize pool or reschedule |
| Instructor hours per learner-week | ≤4.0 | Rebalance staffing |

### 6.2 Mentor model and wellbeing

| Element | Specification |
|---|---|
| Layers | (a) **Technical mentor**, one per three learners (a pod); weekly 30-minute 1:1; reviews pull requests; (b) **peer trio**, rotating driver and navigator every 20–30 min **[Foundation §5.6; R3 evidence B for groups of three]** |
| Shadow → reverse shadow → solo | Weeks 1–10: learners watch instructors play and debrief client roles (shadow). Weeks 11–21: learners lead Customer Labs with the coach observing (reverse shadow). Weeks 22–23: real tickets with mentor backstop (solo with backstop) **[Sourced: R3 §1.6, Google on-call training]** |
| Pod phase | Five senior FDE mentors at about 0.15 FTE each (Weeks 22–23) **[Foundation §11.1]** |
| Alumni and near-peer teachers | Two alumni TAs at about 0.2 FTE each; a few hours a week with recognition **[Sourced: R3]** |
| Mentor training | Debrief facilitation (Etsy guide), feedback delivery, rubric calibration **[Sourced: R3]**. Mentors do **not** assess their own mentees' gates **[Repo]** |
| Wellbeing lead | Named, part-time (0.1 FTE); an external counselling and EAP referral list **[Foundation §5.4]** |
| Daily and weekly | Hard stop 17:45; no required weekend work; weekly anonymous pulse (stress, load, belonging) reviewed in 48 h; a 17:30 written reflection every day |
| Consolidation | Slack placed at Weeks 6, 11–12 and again in Weeks 22–24 (§3.9) so there is a lighter week roughly every 6 weeks in Phase A and none during the AI phases, which is stated in advance in the contract |
| Norms | Recurse-style rules and a code of conduct **[Sourced: R3]** |
| Accommodations | Documented path for caregivers and learners with a second job; absence beyond three cumulative days moves a learner to the next cohort with an exception path |

**Long-program note.** The Foundation's burnout evidence is observational and from bootcamps **[Sourced: R3 §3]**. The AI phases (Weeks 13–21) have no slack; the mitigation is protection of the 17:45 stop and the Friday craft block, plus the early-warning script below.

### 6.3 Early-warning indicators and the outreach script

| Indicator [thresholds are Assumptions] | Trigger | Who acts |
|---|---|---|
| Missed stand-up or reflection | 2 in a week | Technical mentor, same day |
| Falling retrieval-quiz scores | 2 consecutive quizzes below the cohort's lower quartile | Mentor, within 48 h |
| Rising stall time | `stall_point` time above 1.5× the cohort median in 2 consecutive labs | Floating instructor |
| Pulse | Stress or load ≥4 / 5 two weeks running, or any "I'm not coping" comment | Wellbeing lead, within 48 h |
| Logged hours | Above 44 h two weeks running | Program manager |

**Outreach script (supportive, not a penalty):** (1) say what was noticed, factually, without judgment; (2) ask how they are and what is getting in the way; (3) agree one small change and a check-in date, and record it in the learning plan. Written, behavioural feedback follows within 48 h **[Foundation §6.6]**.

### 6.4 Cohort checkpoints

| Cadence | Event |
|---|---|
| Daily | Stand-up with a retrieval warm-up (09:00); written reflection (17:30) |
| Weekly | 1:1 mentor; Friday checkpoint, demo and retrieval quiz (items from 1, 3, 6 and 12 weeks earlier); Customer Lab; retro and pulse |
| Game days / drills | Week 8 (Game day 1); incident drills in most weeks (see each week's day table); Week 21 (G4); Week 23 (`FIELD-BLIND`) |
| Calibration | Before the cohort, then before G2 (Week 10), G3 (Week 18), G4 (Week 21) and G5 (Week 24), on recorded examples |
| Phase reviews | End of Phase A (Week 10): gate health and stall points; Week 12: mid review; Week 18: G3 health and stall points; Week 21: operations review; Week 24: outcomes |
| Employer touchpoints (if sponsored) | Manager check-ins at Day 30, 60, 90 and 120; the manager cannot override the readiness outcome **[Foundation §6.7]** |
| Content refresh | At Week 12 and Week 18, re-verify the tooling flags in Foundation §10 (MCP spec revision, framework status, model names) |
| Post-program | 30-day and 6-month surveys (learner and manager); 90-day supervisor rating |

### 6.5 Optional work and electives

**The Foundation reserves no elective hours.** Specializations (Security Operations, Cloud Security Architecture, Quantum-safe) are deferred to post-program (Foundation §7.5). Nothing below is required, and none of it may be assigned outside the 17:45 stop.

| Optional item | Where it fits |
|---|---|
| Extra timed Kubernetes drills | Open-lab blocks in Weeks 6, 11 and 12 |
| Karpathy "Zero to Hero" (from-scratch model building) https://karpathy.ai/zero-to-hero.html [Sourced: R5] | Open lab, Weeks 11–12 |
| Additional red-team and eval-set building | Office hours in Weeks 16–18 |
| Self-funded external exams (AWS, Terraform, Kubernetes) | Mentioned once in Week 1; not funded, scheduled or gated (Foundation §1.2 #7) |
| Reusable asset (fault scenario, runbook, pattern) | Required by the cohort contract by the final gate; time comes from the Week 22–24 slack |

---

## 7. Prep checklists, tooling and accounts

### 7.1 Learner checklist (sent four weeks before Day 1)

| When | Item |
|---|---|
| **4 weeks out** | Read the cohort contract; set a calendar block for the full 24 weeks; (employer-sponsored) manager signs. Confirm hardware: 16 GB RAM, 100 GB free disk. |
| **3 weeks out** | Accept invitations (GitHub organisation, AWS SSO, the cohort chat). Install the toolchain (below). |
| **2 weeks out** | Run `make verify` in the starter repository (about 5 hours of setup in total). Light reading (about 3 hours): two Missing Semester lectures (shell, version control) https://missing.csail.mit.edu/ ; the first modules of Google's Machine Learning Crash Course https://developers.google.com/machine-learning/crash-course ; the cohort handbook, Part 1. |
| **1 week out** | Read the retake policy and the rubrics; send any accessibility or caregiving needs to the program manager. |
| **Day before** | Sleep. **Do not cram**: it inflates the baseline and hides what the program should teach. |

**Toolchain** (all nine commands must return a version in `make verify`): `git`, `docker`, `kubectl`, `kind`, `helm`, `terraform`, `python3`, `uv`, `aws`. (This corrects the repo Prep Guide, which said "all eight commands" but listed seven.) **[Repo: Prep Guide]**

### 7.2 Staff and infrastructure build sequence (T−8 weeks to Day 1) **[Repo: Handbook Part IV; efforts are Assumptions]**

| T− | Item | Notes for 24 weeks |
|---|---|---|
| 8 | Start the **core 32-scenario fault library** (Terraform or Kustomize; 3–5 variants; reset <5 min; enumerated stall points). AWS Organization, cohort OU, SCPs, Budgets actions, tag policy. Verify the **nightly nuke** in dry-run mode first. | Largest pre-launch effort (≈4–6 FTE-weeks) **[Foundation §11.2]** |
| 7 | Identity provider (Keycloak or a test tenant); LLM gateway with per-learner spend caps; pick **one** tracing tool; choose the vector store | |
| 6 | Sandboxes per learner; cohort lab repositories; telemetry workbook (adapt the repo's Working Plan to the L0–L4 and D1–D6 model) | |
| 5 | Start the **Linden synthetic corpus** (5,000 documents: 40% clean PDFs, 30% scanned PDFs of varying quality, 20% spreadsheets, 10% inconsistent HTML/DOCX); the starter corpus (about 200 documents) | **[Repo: Ops Guide §4]** |
| 4 | Golden set (100) and dev set (50), **labelled by someone other than the retrieval tuner**; the 8 AI-specific fault scenarios; **pod arrangements**: partner team, NDAs, access, tickets, mentor recruitment; external assessors booked for G3, G4, G5; GPU pool booked for Weeks 17 and 20–21; re-verify Foundation §10 tooling flags | |
| 3 | Starter code and templates (Weeks 1–5), guard harness, system-card template, pre-sliced slice-analysis dataset | |
| 2 | Rubric calibration on recorded examples; client-actor scripts with hidden-fact sheets; actor training | |
| 1 | Dry run of Week 1 and of the G1 environment; mentor training; `make verify` run on a clean machine; Day-1 readiness checklist signed | |

### 7.3 Tooling by phase (status flags from Foundation §10)

| Phase | Main tools | Notes |
|---|---|---|
| A | Python 3.12+, `uv`, pytest, ruff, pydantic, FastAPI; GitHub Actions; AWS (IAM, VPC, EC2, S3, RDS, Lambda, CloudWatch); Docker; Terraform; Kubernetes (`kind` locally, EKS in scheduled windows); Prometheus, Grafana, OpenTelemetry; Semgrep, Trivy, gitleaks, CycloneDX, OWASP ZAP; OWASP Juice Shop; AWS FIS and LitmusChaos | Mostly [U] for versions; Juice Shop and OWASP guideline [V] |
| B | pandas or polars, DuckDB; scikit-learn; an air-gapped VPC with an internal mirror | |
| C1 | Claude as the default model (direct API or Amazon Bedrock) plus at least one OpenAI-compatible endpoint; `pgvector`; Langfuse or Arize Phoenix (one); promptfoo, DeepEval, Inspect AI or Ragas only after a plain-pytest start; LiteLLM or equivalent gateway; LangGraph; MCP SDKs and Inspector | **Model IDs in config only.** MCP spec `2026-07-28` [V]; OpenTelemetry GenAI conventions still experimental [S]; tool-ownership claims [U] |
| C2 | Keycloak or an identity-provider test tenant; Ollama, llama.cpp, vLLM; Helm; KServe and llm-d (awareness only); Presidio; shared GPU pool | [S]/[U] |
| D | Everything above; production-style dashboards and the runbook | |

**Do not teach or depend on:** the OpenAI Assistants API (scheduled shutdown [S]); pre-2026 MCP tutorials; LLM Guard (archival claim [U]); Jenkins, Nexus or Ansible as the main stack; detectors as a security boundary; hard-coded model IDs **[Foundation §10]**.

**Accounts.** One AWS account per learner under a cohort OU; $500 monthly cap with 60% and 85% alerts, enforced in layers (SCP deny-list, Budgets actions, tagging, nightly teardown); the AWS Budgets lag is not stated in the documentation read, so a Budget alone is not an instantaneous cap **[Foundation §9.2; Sourced: R2]**. Provider keys sit in a gateway, never in repositories or notebooks.

### 7.4 Staffing and cost (pilot; all Assumptions to validate)

| Role | FTE (24-week) |
|---|---|
| Program lead | 0.4 |
| Lead instructors (an AI lead, a platform lead, a third) | 2.4 |
| Customer-craft coach | 0.5 |
| Lab / platform engineer | 0.8 |
| Technical mentors | ≈0.5 first half; ≈0.75 in the pod phase |
| Program manager | 0.3 |
| Wellbeing lead | 0.1 |
| Alumni TAs | 0.4 |
| Client actors | Staff and volunteer time, about one actor-hour per pod simulation hour |
| **Approximate total** | **≈5.5 FTE average (about 133 FTE-weeks)** **[Foundation §11.1]** |

Run-cost placeholders for 15 learners, 24 weeks (Foundation §9.7, order of magnitude only): AWS sandboxes $14k–$27k; model API $3k–$8k; GPU $15k–$35k; air-gap lab and tooling $6k–$12k. **No total is given: the model API, GPU and sandbox lines are the least certain. Replace with measured values after the first two weeks of the pilot.**

---

## 8. Risks, Day-120 profile, on-the-job ramp, open items

### 8.1 Risks specific to a 24-week program

| # | Risk | Mitigation | Basis |
|---|---|---|---|
| 1 | **Fatigue and drop-off** around Weeks 9–12 and 17–21 (six months, the AI phases have no slack) | Hard stop 17:45; Friday craft block protected; consolidation Weeks 6 and 11–12; weekly pulse; early-warning script (§6.3); mentor from Day 1 | [Sourced: R3 §3, observational] |
| 2 | **Zero slack in Weeks 13–21**: a stall in AI Core has no buffer | If the pilot shows overrun, move 8 h of Phase-A slack later (Weeks 6 and 9 into Week 19); pre-teach T1–T2 in Phase B (done) | [Judgment; Foundation §7.6] |
| 3 | **Week 18 crowding**: 20 h of new AI content plus G3 | Thursday 17:00 freeze; MCP labs scheduled Monday to Wednesday; keep G3 scope to RAG, evals and ACL | [Judgment] |
| 4 | **G3 and G4 remediation has no dedicated slack** | Office hours and mentor 1:1s inside lab hours; Week 22 re-assessments (4 h); reference build available | [Judgment] |
| 5 | **Content staleness over six months** (MCP revisions, framework status, model names, tool acquisitions) | Config-only model IDs; teach concepts plus one thin SDK; re-verify tooling flags at T−4, Week 12 and Week 18 | [Sourced: R5 §1] |
| 6 | **Carried-system dependency**: a learner who fails G3 may lack a base for P6 and P8 | The reference P5 build is available to anyone who has not yet passed G3, so P6 is not blocked; their G3 re-assessment is still required | [Judgment] |
| 7 | **Pod work is not available or is unsafe** | Pre-arranged partner team and tickets by T−4; low-risk definition; mentor sign-off; fallback to a stage-4 simulation with an honest label | [Assumption] |
| 8 | **Mentor availability and burnout** | Protected hours (0.15 FTE), recognition, calibration, backup mentors from alumni | [Sourced: R3] |
| 9 | **GPU contention** in Weeks 17 and 20–21 | Per-trio booking, run caps, rental on demand; use managed endpoints where the lesson allows | [Foundation §9.3; Assumption] |
| 10 | **Cost drift over six months** (AI loops, idle clusters) | Layered cost controls; gateway spend caps reviewed weekly; scheduled windows for EKS and GPUs | [Sourced: R2; Judgment] |
| 11 | **Assessor drift** over a long program | Calibration before G2, G3, G4, G5; two assessors where marked; external reviewer at G3 and G5 | [Repo; Sourced R3] |
| 12 | **Trio cohesion** and attrition effects over 24 weeks | Rotate pairs inside the trio; backup pairing; trio re-forming at the Mid review if needed | [Judgment] |
| 13 | **Over-claiming outcomes** | Pre-declare "ready"; publish outcomes with denominators; do not claim to replicate Palantir's bootcamp | [Sourced: R3] |
| 14 | **Weak evidence transfer** (undergraduate STEM and bootcamp evidence, not FDE training) | Treat the first cohort as a measured pilot (§6.1); prefer reversible choices | [Sourced: R3 §0] |

### 8.2 What a Day-120 graduate can and cannot do

**This is reasoned estimation. No public company benchmark exists for new-grad FDE performance** **[Judgment, informed by R4 §4]**. Target: **"near-independent on routine engagements"** (a trusted junior owning a workstream), with real low-risk work behind them.

| Can do | Cannot yet do reliably |
|---|---|
| Run a structured 30–45 minute discovery with a friendly or mildly adversarial contact and produce a scope a senior FDE accepts with edits | Own a strategic account or be the sole technical voice with executives |
| Build, deploy and operate a contained AI workflow end to end (RAG, tools, evals in CI, tracing, SLOs, a cost model) under review | Negotiate scope, price or timelines without senior review |
| Debug a deploy or an incident from logs and traces on a routine system; write a blameless postmortem | Navigate accreditation, regulated procurement or political dynamics alone |
| Deliver a rehearsed demo on realistic data and answer "what are the limits?" honestly | Architect a multi-system solution under heavy constraints |
| Write answer-first status updates and a runbook a cold operator can use; hand over a system | Diagnose ambiguous failures in an unfamiliar customer environment without help |
| Recognise security and compliance constraints (data flow, access, retention, injection risk), explain them plainly and escalate | Decide alone when a customer request should be refused |
| Flag patterns versus bespoke work and write a product-feedback memo | Run an incident as lead on a critical system |

**Against the 12-week graduate:** more reps in every domain, an L3 profile in D1, D2, D5 and D6 rather than L2, real pod experience, and the full 40-scenario fault library behind them.

### 8.3 On-the-job ramp

Adapted from the repo's field transition (shadow, reverse shadow, solo with backstop, independent) **[Repo: Handbook §7; Foundation §2.6]**. Timings are **[Judgment]**.

| Outcome at G5 | Ramp |
|---|---|
| **Ready: Workstream Owner** | Shortened shadow (1 engagement) → reverse shadow (1–2 engagements) → solo with backstop (about 3 months) → independent on routine engagements; owns a workstream, not the relationship, for the first months |
| **Ready: Supervised** | Paired assignment with a named senior for about 90 days, then re-assessment against the Workstream Owner anchors |
| **Conditional** | 4–6 weeks targeted remediation, then a mini-G5 defence |
| **Not yet ready** | Role-fit conversation; deferral to a later cohort; documented exit path |

Checkpoints after exit: manager survey at 30 days and 6 months; supervisor rating at Day 90 against "trusted junior on a senior-led engagement" **[Sourced: R3, Google SRE EDU; Foundation §12.4]**. Promotion to owning an engagement is a later milestone (likely 9–18 months, **[UNVERIFIED, estimate from R4 §4]**).

### 8.4 Unverified items carried into this plan

Nothing here should be presented as fact in program materials until checked. The full list is in Foundation §12.2; those that touch this plan most:

- **Tools and vendors:** Promptfoo ownership claim; LLM Guard archival; Guardrails AI acquisition; Microsoft Agent Framework, Google ADK and OpenAI Agents SDK status claims (each single-source); LangGraph 1.0 date; LlamaIndex status. OpenAI Assistants API shutdown is a search-snippet fact [S].
- **Infrastructure:** AWS Budgets data lag; `aws-nuke` safety features on the current release; Builder Labs provisioning details.
- **Standards:** EU AI Act omnibus final adoption and GPAI obligations; NIST AI RMF is under revision.
- **Sources:** the Anthropic API course module list (from a mirror and third-party write-up); the Maven syllabus (8- vs 9-week conflict); Udacity (third-party only); vendor-reported figures (Contextual Retrieval, multi-agent token multiples) are the vendors' own.
- **Evidence:** no independent evidence that the customer-skill methods improve FDE outcomes; the simulated-client capstone has no controlled evidence; instructor ratios and the 15-learner cohort are assumptions; all hour estimates are judgments.
- **Plan-level judgments to validate in the pilot:** the Day-60 expected levels; lane definitions; G1 Stage B; the 20-minute individual orals; pod availability; early-warning thresholds; the guard harness and slice-analysis starter materials (assumed to be built).

### 8.5 Decisions needed from the sponsor

None blocks the plan; each uses the default shown.

| # | Decision | Default used |
|---|---|---|
| 1 | **AI coding-assistant policy** (§1.8): allowed in labs from Week 2; assistant-free for G0 and for the oral defences at G1 and G2 | As stated |
| 2 | **G1 Stage B** (§3.2): add a Kubernetes and autoscaling stage after the 60-minute platform stage, instead of fitting both into 60 minutes | Two stages (5 learner hours) |
| 3 | **Pod work source** (Phase D introduction): partner team or internal backlog; NDAs and access by T−4 | Internal or partner low-risk tickets; honest fallback to a stage-4 simulation |
| 4 | **G5 scheduling** (§3.7): defences Thursday afternoon to Friday morning, decisions on Day 120 | As stated |
| 5 | **G3 and G4 retake slack**: keep zero slack in Weeks 13–21, or move 8 h of Phase-A slack later | Keep; revisit after the first pilot data |
| 6 | **Pilot sequencing**: run the 12-week first, then the 24-week with changes | 12-week first (Foundation Appendix B #2) |
| 7 | **Cohort size**: 15 learners in five trios | As stated [Assumption] |
| 8 | **Who sponsors learners**: employer-sponsored with manager signature, or individual | Employer-sponsored contract (adaptable) |
| 9 | **Client actors and external assessors**: staff, alumni, or paid external | Staff and volunteers; one external assessor at G3 and G5 |
| 10 | **Outcome publication**: external or internal | External, with full denominators (P18) |

---

*FDE Program Design — 24-Week Plan v0.1 · Draft for review · Document ends.*
