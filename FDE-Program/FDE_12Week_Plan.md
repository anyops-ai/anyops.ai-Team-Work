# FDE Program: 12-Week Plan (full-time, 480 hours)

**Status:** Draft v0.1 for review · **Date:** 2026-11-25 · **Audience:** program lead, instructors, lab engineer, assessors, sponsor
**Parent document (binding):** `00_Design_Foundation.md`. If this plan and the foundation disagree, the foundation wins until it is revised (foundation §1.1). **Sibling:** `FDE_24Week_Plan.md` (written in parallel). **Evidence:** `research/01-05`. **Reference only, never edited:** `../Projects/` (the downloaded repo).

### Label legend (as in the foundation)

| Label | Meaning |
|---|---|
| **[Sourced]** | From a cited source in `research/` (R1 AI courses, R2 cloud/DevOps, R3 pedagogy, R4 FDE role and customer skills, R5 applied-AI depth). Source quality varies; the research notes carry per-claim caveats |
| **[Repo]** | Reused or adapted from the downloaded `anyops-ai/Projects` material |
| **[Judgment]** | A design call made here. Not a published benchmark |
| **[Assumption]** | A planning figure to validate in the pilot |

Tool and spec statuses (MCP revision, vendor acquisitions, model names, prices) move fast. Anything marked unverified in the research stays unverified here; **re-verify at T-4 weeks**.

### Contents

**Part I: Snapshot and conventions** (§1 snapshot, §2 how to read the schedule) · **Part II: Week-by-week plan** (Weeks 1-12) · **Part III: Reference** (§3 gates, §4 capstone, §5 lab catalogue and fault library, §6 measurement and pilot, §7 preparation and checklists, §8 risks, Day-60 graduate and Day 61-90 ramp, §9 traceability to the foundation)

---

# Part I: Snapshot and conventions

## 1. Program snapshot

### 1.1 Promise and outcomes

A 12-week, full-time (40 h/week, **480 h, 60 teaching days**) program that takes new graduates from software and cloud fundamentals, through a heavily weighted **applied-AI** core, to customer-facing scoping and a capstone engagement. It trains a *trusted junior on a senior-led engagement* **[Judgment: foundation §2.5]**.

**Honest exit promise:** graduates are **ready to start under supervision**, typically *Ready: Supervised*, with a strong minority reaching *Ready: Workstream Owner*. They are not independent on routine engagements; that is the 24-week plan's promise **[Judgment: foundation §2.5]**.

**Target exit profile for the median learner [Judgment: foundation §3.5]:**

| D1 Software Eng. | D2 Cloud & Platform | D3 Secure Delivery | **D4 Applied AI** | D5 AI Ops & Reliability | D6 Customer Craft |
|---|---|---|---|---|---|
| L2 (L3 stretch) | L2 | L2 | **L3** | L2 | L2 |

The program is AI-first, so D4 is the one domain where even a 12-week graduate is expected to be *independent*. Levels are L0-L4 with behaviour anchors (foundation §3.3). The Ready: Workstream Owner rule is *L2+ in all six and L3+ in at least three*; Ready: Supervised is *L2+ in all six, L3 in 1-2, craft >= 3.0*.

### 1.2 Who it is for and entry requirements

| Item | Requirement |
|---|---|
| Learner | New graduates and early-career engineers (0-2 years) who can already program in one language **[Foundation decision 1]** |
| Skills assumed | Basic git and command line; can write a small program. CS theory is *not* taught (no CS50-style detours) |
| Hardware | Laptop with 16 GB RAM and 100 GB free disk **[Repo: Prep Guide]** |
| Time | Full-time for 12 weeks; scheduled load is 40 h/week; **no required work after 17:45 or at weekends** (foundation §5.4) |
| Contract | Cohort contract signed before Day 1 (foundation §6.7); manager signature if employer-sponsored |
| Pre-work | Setup and light reading only, about 8 h, sent four weeks before Day 1 (§7.1). **Do not cram**: it inflates the baseline |
| Selection | No entrance exam. G0 is diagnostic and cannot be failed; it routes learners to lanes and builds an ILP |
| Cohort (pilot) | 15 learners in five trios **[Assumption: foundation §5.5]** |
| Cloud and AI stack | AWS primary; provider-neutral AI labs with Claude as the default and an OpenAI-compatible endpoint for portability; **no certifications** (cert-aligned content is used as syllabus only) |

### 1.3 Hours (reconciled to the foundation)

The schedule in Part II is generated from a single data file and checked by script: every day is 8.0 h, every week is 40 h, and every block and phase total matches foundation §7.2 and §7.6 exactly.

| # | Block | Foundation budget (h) | This plan (h) | % of 480 |
|---|---|---|---|---|
| 1 | Onboarding & baseline (`ONB`) | 10 | 10 | 2.1 |
| 2 | Software fundamentals (`SWF`) | 32 | 32 | 6.7 |
| 3 | Cloud / AWS (`CLD`) | 36 | 36 | 7.5 |
| 4 | DevOps / K8s (`DEV`) | 48 | 48 | 10.0 |
| 5 | DevSecOps (`SEC`) | 20 | 20 | 4.2 |
| 6 | AI Core (`AIC`) | 100 | 100 | 20.8 |
| 7 | AI Ops & Security (`AIO`) | 52 | 52 | 10.8 |
| 8 | Customer Labs (`CUS`) | 32 | 32 | 6.7 |
| 9 | Projects & capstone (`PRJ`) | 84 | 84 | 17.5 |
| 10 | Assessment & gates (`ASM`) | 28 | 28 | 5.8 |
| 11 | Slack / consolidation (`SLK`) | 38 | 38 | 7.9 |
| | **Total** | **480** | **480** | **100** |

**Check:** 10+32+36+48+20+100+52+32+84+28+38 = 480. **AI** (AI Core + AI Ops & Security) = 100 + 52 = **152 h**, the largest block group, exceeding the entire foundations stack (146 h). Counting AI-centric project hours (P5, P6 and the capstone: 56 h) gives an **effective AI exposure of 208 h (about 43%)**. Total customer-craft exposure is about 62 h (32 dedicated + about 30 embedded in projects and assessment) **[Judgment: foundation §7.2 memo]**.

### 1.4 Phases and gates

| Phase | Weeks | Capacity (h) | Blocks in phase (hours) | Gate at end |
|---|---|---|---|---|
| A Foundations | 1-4 | 160 | ONB 10 · SWF 32 · CLD 36 · DEV 42 · SEC 6 · CUS 10 · PRJ 8 · ASM 5 · SLK 11 | G1 (Day 20) |
| B Secure + AI on-ramp | 5-6 | 80 | DEV 6 · SEC 14 · AIC 37 · AIO 4 · CUS 5 · ASM 4 · SLK 10 | G2 (Day 30) |
| C AI build | 7-9 | 120 | AIC 63 · AIO 18 · CUS 8 · PRJ 24 · ASM 6 · SLK 1 | G3 (Day 45) |
| D Operate + enterprise | 10-11 | 80 | AIO 30 · CUS 9 · PRJ 20 · ASM 5 · SLK 16 | G4 (Day 55) |
| E Capstone | 12 | 40 | PRJ 32 · ASM 8 | G5 (Day 60) |

### 1.5 Hours by week and block

| Wk | ONB | SWF | CLD | DEV | SEC | AIC | AIO | CUS | PRJ | ASM | SLK | Total |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 10 | 11 | 6 | 4 | 2 | · | · | 3 | 3 | · | 1 | 40 |
| 2 | · | 10 | 12 | 13 | · | · | · | 2.5 | · | · | 2.5 | 40 |
| 3 | · | 7 | 10 | 14 | 2 | · | · | 2.5 | 2 | · | 2.5 | 40 |
| 4 | · | 4 | 8 | 11 | 2 | · | · | 2 | 3 | 5 | 5 | 40 |
| 5 | · | · | · | 4 | 8 | 21 | · | 2.5 | · | · | 4.5 | 40 |
| 6 | · | · | · | 2 | 6 | 16 | 4 | 2.5 | · | 4 | 5.5 | 40 |
| 7 | · | · | · | · | · | 24 | 4 | 3 | 9 | · | · | 40 |
| 8 | · | · | · | · | · | 24 | 4 | 2.5 | 8.5 | · | 1 | 40 |
| 9 | · | · | · | · | · | 15 | 10 | 2.5 | 6.5 | 6 | · | 40 |
| 10 | · | · | · | · | · | · | 20 | 4.5 | 12 | · | 3.5 | 40 |
| 11 | · | · | · | · | · | · | 10 | 4.5 | 8 | 5 | 12.5 | 40 |
| 12 | · | · | · | · | · | · | · | · | 32 | 8 | · | 40 |
| **Σ** | **10** | **32** | **36** | **48** | **20** | **100** | **52** | **32** | **84** | **28** | **38** | **480** |

Block codes: ONB onboarding and baseline · SWF software fundamentals · CLD cloud/AWS · DEV DevOps/K8s · SEC DevSecOps · AIC AI Core · AIO AI Ops and Security · CUS customer labs · PRJ projects · ASM assessment and gates · SLK slack.

### 1.6 Activity mix (reported, not adjusted)

| Activity type | Hours | % of 480 | Foundation target (P1) |
|---|---|---|---|
| Instruction | 68.5 | 14.3 | 15% instruction |
| Lab (pair/trio) | 229 | 47.7 | 60% labs and projects (LAB + PRJ) |
| Project | 79 | 16.5 | (counted with labs) |
| Customer simulation | 32 | 6.7 | 15% customer craft and simulation (dedicated + embedded) |
| Assessment | 33.5 | 7.0 | 10% assessment |
| Slack/consolidation | 38 | 7.9 | (slack; not in P1 mix) |
| *Labs + projects combined* | 308 | 64.2 | 60% |

How this compares with the foundation's 15 / 60 / 15 / 10 target (P1): instruction is close to target; labs and projects run above it (hands-on bias); *dedicated* customer simulation is below 15% because the foundation's own memo counts about 30 more customer-craft hours embedded in projects and assessment (total exposure about 13%, not 15%); assessment is below 10% because G0's 5.5 h sits in the onboarding block (it is counted under the ASM *type*, not the ASM block); and slack is separate from the P1 mix. These are reported as they are rather than tuned to the target.

### 1.7 Week at a glance

| Wk | Days | Theme | Domain focus | Project milestone(s) | Gate | Labs (new) | Labs h |
|---|---|---|---|---|---|---|---|
| 1 | 1-5 | Ship in week one: toolkit, first AWS deploy, baseline (G0) | D1, D2, D3, D6 | P1-M1 | G0 (Days 1-2) | 9 | 21.5 |
| 2 | 6-10 | Networks, compute and the first pipeline | D1, D2, D3 | none (customer: stakeholder map) | none (weekly quiz) | 12 | 26.5 |
| 3 | 11-15 | Infrastructure as code and the first real scope | D1, D2, D3, D6 | P1-M2 | none | 11 | 25 |
| 4 | 16-20 | Observe, operate and prove it (G1) | D1, D2, D3, D5 | P1-M3 | G1 (Day 20) | 10 | 21 |
| 5 | 21-25 | Secure the pipeline; first contact with LLMs | D3, D4, D2 | none (customer: Linden contact) | none (G1 retakes in slack) | 14 | 29.5 |
| 6 | 26-30 | Tools, evals-first and the security review (G2) | D3, D4, D5, D6 | none (G2 artifact pack) | G2 (Day 30); midpoint re-score | 10 | 25 |
| 7 | 31-35 | RAG on the Linden corpus; golden sets and tracing | D4, D5, D3 | P5-M1 (carried system begins) | none | 8 | 26.5 |
| 8 | 36-40 | Agents, MCP and calibrated judges | D4, D3, D5, D6 | P5-M2, P6-M1 | none | 9 | 27 |
| 9 | 41-45 | Reliability, context, open models and guardrails (G3) | D4, D5, D3, D6 | P6-M2 | G3 (Day 45) | 8 | 22 |
| 10 | 46-50 | Enterprise integration and the Linden enclave | D3, D5, D1, D6 | P3+P4 enclave (P34-M1, M2) | none (red/blue game day) | 9 | 25.5 |
| 11 | 51-55 | Operate under failure (G4), privacy, and the scoping sprint | D5, D3, D6 | P7-M1, M2 | G4 (Day 55) | 7 | 23 |
| 12 | 56-60 | Capstone and readiness panel (G5) | all | P8-M1..M4 | G5 (Day 60) | 0 | 0 |

### 1.8 Gate calendar

| Gate | Day | Week / weekday | Assessment hours | What |
|---|---|---|---|---|
| G0 Baseline | 1-2 | 1 / Mon-Tue | 6 | Diagnostic only: written exam, layered-fault practical, mock discovery call |
| G1 Platform: rebuild from scratch | 20 | 4 / Fri | 5 | Fresh AWS sandbox -> observable containerised service via IaC + CI in <60 min |
| G2 Secure delivery review | 30 | 6 / Fri | 4 | Mock enterprise security review; midpoint readiness question |
| G3 AI build | 45 | 9 / Fri | 6 | AI system against a business metric, evals in CI, hostile evaluator |
| G4 Operate under failure | 55 | 11 / Fri | 5 | Five-injection production simulation, runbook cold-test |
| G5 Capstone defence and readiness panel | 60 | 12 / Fri | 8 | Capstone defence, handover cold-test, readiness outcome |

Day numbering: **Week 1 starts on Day 1 (Monday). There is no Week 0.** G0 runs Day 1 afternoon to Day 2 and is recorded as Day 2 (foundation §6.2; this removes the repo's day-numbering collision). 12 weeks = 60 teaching days.

### 1.9 Projects and the carried system

Two fictional, synthetic customers run through the program (foundation §8.1): **Kestrel Freight** (commercial, cost-sensitive; Weeks 1-4 and the scoping sprint) and **Linden Claims Services** (regulated; the AI work and the capstone). The AI work uses a **carried system** (a Linden claims assistant) that grows from Week 7 to the capstone.

| Project (foundation §8.3) | Foundation hours | This plan | Milestones | Weeks |
|---|---|---|---|---|
| P1 Lift the spreadsheet | 8 | 8 | P1-M1, P1-M2, P1-M3 | 1-4 |
| P5 Document workflow with evals | 14 | 14 | P5-M1, P5-M2 | 7-8 |
| P6 Agent with tools / MCP | 10 | 10 | P6-M1, P6-M2 | 8-9 |
| P3+P4 Linden enclave | 12 | 12 | P34-M1, P34-M2 | 10-10 |
| P7 Scoping sprint | 8 | 8 | P7-M1, P7-M2 | 11-11 |
| P8 Capstone | 32 | 32 | P8-M1, P8-M2, P8-M3, P8-M4 | 12-12 |
| **Total** | **84** | **84** | | |

P2 (the report that is always wrong) is folded into the software-fundamentals data mini-lab (`W4-L1`), per the foundation.

## 2. How to read the schedule

**Blocks and types.** Every scheduled segment carries a *block* (which foundation budget line it counts against) and a *type* (INS instruction, LAB pair/trio lab, PRJ project, CUS customer simulation, ASM assessment, SLK slack/consolidation). Lab and project IDs appear in backticks, for example `W2-L3` (the third lab first scheduled in Week 2) or `P1-M1` (project P1, milestone 1). Lab IDs are sequential per week and replace the repo's inherited 26-week numbering (foundation Appendix A #9).

**Day.** 09:00-17:45, 8.0 net hours: a 3.5 h morning, a 45-minute lunch (not counted) and a 4.5 h afternoon. The foundation's day template (§5.1) is the shape of every day: a stand-up and retrieval warm-up in the first 20 minutes of the morning block, an instruction slot, a pair/trio lab, a project block, a review block, a lab-continuation/office-hours slot, and a 15-minute written reflection at the end. The warm-up and the reflection sit *inside* the segment they bookend and are not separate rows.

**The Friday pattern (foundation §5.2).** Friday morning is the weekly checkpoint and demo; the afternoon is a Customer Lab in odd weeks. In even weeks the Customer Lab moves to Wednesday (with a 30-min retry on Thursday), and Friday afternoon is a game day or a gate. In gate weeks the weekly retrieval quiz moves to Thursday.

**Customer Lab retry rule.** Every graded Customer Lab allows one retry within two working days of feedback; the *delta* between attempts is graded. Retries are 0.5 h and appear as separate rows (they carry the original lab's ID). **Lab hours in the weekly lab tables are totals across every row carrying that lab's ID, including retries scheduled in a later week.**

**Where slack is zero.** Weeks 7 and 9 have no slack in the foundation budget and Week 8 has 1 h. In those weeks the Friday retro and the weekly 1:1 are held inside the project block and noted in the row.

**Escalation ladder (floating instructor) [Repo]:** 0-10 min stuck: the instructor does nothing; 10-25 min: asks a question; 25-40 min: gives a hint; 40+ min: gives direct help. Hint counts and stall points are logged against an enumerated list per lab, so the 40% stall rule (foundation §6.8) can be computed.

**Weekly protected items (foundation §5.3).** One 30-min mentor 1:1; one peer code-review pairing; one retrieval quiz; one written artifact graded on a rubric; one Customer Lab with a retry window.

**Model IDs.** No lab hard-codes a model name. Model, provider and base URL live in config; every AI lab is run against two endpoints (hosted Claude default plus an OpenAI-compatible one) **[Foundation P16]**.


---

# Part II: Week-by-week plan

## Week 1: Ship in week one: toolkit, first AWS deploy, baseline (G0)

*Days 1-5 · Phase A Foundations · Gate: G0 (Days 1-2) · Project: P1-M1*

### W1.1 Objectives

By Friday 17:45 a learner can:

- State the program contract: the 40-hour rule, the six gates, the published rubrics, the retake policy, and the 0/10/25/40-minute escalation ladder for asking for help.
- Use the shell, git and a pull-request review loop; write and test a small typed Python program; debug with a debugger and logs instead of guessing.
- Create and use a sandbox AWS account safely (billing alarm, least-privilege role, root never used) and deploy a function by hand.
- Run a container and keep secrets out of repositories (secret scanning, Secrets Manager).
- **Ship a real thing:** an AWS-hosted service that turns a free-text delivery-exception note into structured JSON through an LLM, with model/provider chosen in config (not in code) and a 20-case assertion file (P1-M1). This is the foundation's "ship in week 1" principle (P2) and the first slice of project P1 **[Judgment: foundation §4 P2, §8.3]**.
- Run a first scripted discovery call and rewrite leading or hypothetical questions into questions about specific past events.

**Baseline recorded (G0):** L0-L4 score per domain from the exam, the layered-fault practical and the mock discovery call; a lane (A/B/C) and an Individual Learning Plan (ILP) issued by Day 3.

### W1.2 Hours and day-by-day schedule

**Hours this week:** ONB 10 · SWF 11 · CLD 6 · DEV 4 · SEC 2 · CUS 3 · PRJ 3 · SLK 1 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D1) | 09:00-10:30 | 1.5 | ONB | INS | Welcome; program promise; 40-hour rule and no-work-after-17:45 norm; cohort contract signed; gates, rubrics and retake policy published |
|  | 10:30-12:30 | 2 | ONB | LAB | Accounts and toolchain: SSO to AWS sandbox, GitHub, LLM gateway key, `make verify`; temporary trios |
|  | 13:15-13:45 | 0.5 | ONB | INS | How to ask for help: write a good issue; the 0/10/25/40-minute escalation ladder |
|  | 13:45-15:45 | 2 | ONB | ASM | G0-A written baseline exam (60 questions; routing only, not pass/fail) |
|  | 15:45-17:45 | 2 | SWF | LAB | Shell, git and the PR loop (part 1) `W1-L1` |
| Tue (D2) | 09:00-12:00 | 3 | ONB | ASM | G0-B layered-fault practical (G0-LAYERED), observed, 3 h |
|  | 12:00-12:30 | 0.5 | ONB | INS | Baseline self-rating on the behavioural L0-L4 scale (D1-D6) |
|  | 13:15-13:45 | 0.5 | ONB | ASM | G0-C 30-min mock discovery call slot (scripted-vague Kestrel COO), recorded |
|  | 13:45-15:45 | 2 | SWF | LAB | Shell, git and the PR loop (part 2): review a partner's PR `W1-L1` |
|  | 15:45-17:45 | 2 | SWF | LAB | Linux and the network from the shell `W1-L2` |
| Wed (D3) | 09:00-09:30 | 0.5 | SLK | SLK | Final trios (mixed by G0 lane); ILP walkthrough with mentor |
|  | 09:30-10:30 | 1 | SWF | INS | Python for ops: types, pydantic, pytest: worked example |
|  | 10:30-12:30 | 2 | SWF | LAB | Typed Python CLI with tests `W1-L3` |
|  | 13:15-15:15 | 2 | CLD | INS | AWS core model: accounts, regions/AZs, IAM principals and policies, shared responsibility, billing |
|  | 15:15-17:45 | 2.5 | CLD | LAB | AWS first steps by hand `W1-L4` |
| Thu (D4) | 09:00-11:00 | 2 | SWF | LAB | Debugging and code quality `W1-L5` |
|  | 11:00-12:30 | 1.5 | CLD | LAB | Serverless 'hello' by hand `W1-L6` |
|  | 13:15-15:45 | 2.5 | PRJ | PRJ | P1-M1 Ship: build the exception-note triage service on the starter repo (0.5 h "LLM API in 30 min" mini-lecture inside), 20-case assertion file, deploy `P1-M1` |
|  | 15:45-17:15 | 1.5 | DEV | INS | Containers: images, layers, Docker concepts: worked example |
|  | 17:15-17:45 | 0.5 | SEC | INS | How secrets leak; least privilege; the "lethal trifecta" seed (10 min) |
| Fri (D5) | 09:00-09:30 | 0.5 | PRJ | PRJ | P1-M1 demo: each trio shows its deployed endpoint and what it cannot do `P1-M1` |
|  | 09:30-12:00 | 2.5 | DEV | LAB | Docker 101 `W1-L7` |
|  | 12:00-12:30 | 0.5 | SEC | LAB | Secrets and least privilege (part 1) `W1-L8` |
|  | 13:15-16:15 | 3 | CUS | CUS | Customer Lab 1 (Kestrel COO): micro-lesson, question-rewrite drill, recorded call, debrief `W1-L9` |
|  | 16:15-17:15 | 1 | SEC | LAB | Secrets and least privilege (part 2) `W1-L8` |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Friday retro (blameless) + anonymous pulse survey |

### W1.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| Program contract and norms | 40-hour rule, no required work after 17:45 or at weekends, gates and retake policy, social norms (no feigned surprise, no "well-actuallys"), how to ask for help (write a good issue) | 30-min talk, then Q&A; contract signed in the room; norms adapted from Recurse Center **[Sourced: R3 §1.1]** |
| G0 baseline | Diagnostic only: 60-question exam, practical `G0-LAYERED` (crash-looping pod from a missing ConfigMap key, DNS blocked by a NetworkPolicy, a readiness probe that returns 200 with an unhealthy body), 30-min mock discovery call | Observed, no help; log `time_to_first_signal`, faults found/fixed, `method_score`, hints **[Repo: Assessment Pack §2]**. The written score is provisional and the practical overrides it |
| Lane assignment | Lane A if (D1+D2)/2 >= 2.5 and (D4+D5)/2 <= 1.5; Lane B if D4 >= 2.5 and (D2+D3)/2 <= 1.5; else Lane C | Repo formula **[Repo: Assessment Pack §2.4]**; D4/D5 now mean Applied AI / AI Ops. Thresholds are a starting point, recalibrate in the pilot **[Judgment]** |
| Shell, git, PR loop | Branching, rebase vs merge, review comments, protected `main`, `make verify` | Pair work, driver/navigator swap every 20-30 min; review a partner's PR (code review is a taught skill) |
| Debugging and quality | Debugger, structured logging, ruff, type-checking, reading stack traces | Three seeded bugs; the failing test comes first |
| Linux and network from the shell | Processes, ports, `curl -v`, `dig`, TLS handshake | Five seeded symptoms; instructor shows one live then steps back (fault `NET-PROXY` variant) |
| Python for ops | Types, pydantic, pytest fixtures | 10-min worked example, then solo with pair review |
| AWS core model | Accounts, regions/AZs, IAM principals and policies, shared responsibility, billing | Console walk-through, then a hands-on build "by hand" (manual first, automate in Weeks 3-4: the Nana Janashia bootcamp order **[Sourced: R2 §1.10]**) |
| Containers | Image vs container, layers, multi-stage, non-root | Worked example, then lab; image scan introduced |
| Secrets and least privilege | How keys leak, pre-commit scanning, Secrets Manager, scoped roles; the "lethal trifecta" named in 10 minutes | Planted key blocked by gitleaks; this is the first appearance of AI security in the program (principle P15) |
| The ship (P1-M1) | LLM call as an HTTP contract; schema-constrained output; assertions before opinions | Starter repo `fde-academy-starter` **[Repo: Prep Guide]** gives a config-driven LLM client wired to two endpoints (hosted Claude default plus one OpenAI-compatible endpoint, hosted or local); learners write the prompt, schema, deploy and assertions |

### W1.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W1-L1` | Shell, git and the PR loop | D1 | 4 | Repo with 3 PRs opened, reviewed by a trio partner, merged | All 3 PRs merged only after a review comment is resolved; no force-push to main; `make verify` green on a clean clone |  |
| `W1-L2` | Linux and the network from the shell | D1 | 2 | Diagnosis notes for 5 seeded symptoms (ports, DNS, proxy, TLS, permissions) | >=4/5 symptoms root-caused using `ss/curl -v/dig/openssl` within 90 min; each with the command that proved it | FAULT: NET-PROXY (variant) |
| `W1-L3` | Typed Python CLI with pytest | D1 | 2 | Small CLI that parses and validates delivery-exception CSV rows | >=8 pytest cases incl. 3 malformed-input cases; ruff + type-check clean; coverage >=80% |  |
| `W1-L5` | Debugging and code quality | D1 | 2 | 3 seeded bugs fixed, each with a regression test | Each root cause explained in <=3 sentences using debugger/log evidence; no fix without a failing-then-passing test |  |
| `W1-L4` | AWS first steps by hand | D2, D3 | 2.5 | Sandbox account configured by hand: billing alarm, scoped role, private S3 bucket | Billing alarm active; role denied outside its bucket (policy simulator screenshot); bucket private; root user never used (CloudTrail check) | FAULT: SEC-ROOT (seeded) |
| `W1-L6` | Serverless 'hello' by hand | D2 | 1.5 | Lambda function with a function URL deployed from the CLI | Public URL returns 200; logs visible in CloudWatch; cold vs warm latency recorded; deployed from CLI in <20 min |  |
| `W1-L7` | Docker 101 | D2 | 2.5 | Multi-stage image of the Kestrel service | Image <200 MB, runs as non-root, `docker run` works from a clean machine; scan report shows 0 critical findings |  |
| `W1-L8` | Secrets and least privilege | D3 | 1.5 | Pre-commit secret scan + secret moved to Secrets Manager/SSM + scoped role | gitleaks blocks a planted key; app reads the secret at runtime; IAM policy simulator proves the role can read only that secret | FAULT: SEC-SECRETS (seeded) |
| `W1-L9` | Customer Lab 1: what an FDE is; the Mom Test; first discovery call | D6 | 3.5 | Recorded 15-min discovery call with the scripted-vague Kestrel COO + 5 rewritten questions | R1 >=3 on: past events not hypotheticals; underlying problem surfaced or probed; learner talk share <=40% | CUSTOMER (R1) |

### W1.5 Customer thread and project milestone

**Customer Lab 1 (Friday, 3 h):** 30-min micro-lesson (the three Mom Test rules: talk about the customer's life, ask about specific past events, talk less), 45-min question-rewrite drill, 60-min recorded discovery call with the scripted-vague client, 45-min debrief. The retry is Monday (0.5 h, counted in Week 2).

**Persona (synthetic, Kestrel Freight COO) [Judgment: foundation §8.1]:**

| | |
|---|---|
| Stated ask | "We want an AI chatbot for our customers." |
| Hidden real problem (revealed only to good questions) | Drivers send delivery-exception notes by WhatsApp and email; supervisors retype them into a shared spreadsheet; the on-time KPI the COO sees every Monday is wrong; late penalties cost real money |
| Flatters bad questions | "Great question!" then a vague answer to any leading or hypothetical question |
| Rubric | R1: asked about specific past events; surfaced or probed the underlying problem; learner talk share <= ~40%; confirmed understanding back; did not pitch a solution **[Sourced: R4 §3.3]** |

The week-1 ship is deliberately the *first slice* of what this client really needs (structuring the exception notes), so learners see the call and the build connect.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P1-M1` Ship: Kestrel exception-note triage service (week-1 ship) | Kestrel | 3 | Public HTTPS endpoint on AWS that turns a free-text delivery-exception note into structured JSON via an LLM; repo; 20-case assertion file; 5-min trio demo | Endpoint returns schema-valid JSON on >=18/20 assertion cases; provider/base-URL/model come from config and the same code passes the file on 2 endpoints (hosted Claude default + one OpenAI-compatible); zero secrets in repo (gitleaks clean); demo says what it cannot do |

### W1.6 Resources

- MIT Missing Semester, 2026 edition (shell, editor, git, debugging, packaging, code quality) https://missing.csail.mit.edu/ **[Sourced: R2 §1.1, V]**
- Anthropic structured outputs (schema-constrained output; no recursive schemas; extra latency on the first request with a new schema) https://platform.claude.com/docs/en/build-with-claude/structured-outputs **[Sourced: R5 T3, V]**
- AWS Free plan (for learners who want to practise outside the sandbox; sandboxed accounts are the primary route) https://aws.amazon.com/free/ **[Sourced: R2 §3.3, V]**
- The Mom Test summaries (secondary sources; the book itself was not read in the research) https://mtlynch.io/book-reports/the-mom-test/ **[Sourced: R4 §2.1]**
- For instructors: Google's *Training Site Reliability Engineers*, chapter 4 on pre-briefing drills ("it is OK not to solve it") https://sre.google/static/pdf/TrainingSiteReliabilityEngineers.pdf **[Sourced: R3 §1.6]**

### W1.7 Stall points and instructor notes

**Likely stall points (log each as an enumerated value so the 40% rule can be computed):**

1. SSO and AWS CLI profile set-up: pre-stage a working profile check in `make verify`; budget 20 minutes of floating-instructor time on Day 1.
2. Git rebase vs merge confusion in the PR loop: hand out a one-page "git panic card".
3. The ship slips because of LLM key limits or quota: the gateway holds per-learner caps; a local Ollama endpoint is the fallback so no trio is blocked.
4. Learners write "vibe" assertions ("answer looks right"): coach toward deterministic checks (valid JSON, required fields present, enum values, refusal cases).
5. G0 anxiety: say twice, in the room and in writing, that G0 cannot be failed and is used only to route and personalise.

**Instructor notes**

- Do not coach during the G0 practical; hints are recorded with timestamps, not withheld unkindly.
- Trios on Day 1 are random; rebalance on Day 3 by lane (mixed experience, Google's group-of-three finding **[Sourced: R3 §1.6]**).
- The Lambda function URL is public by default: the starter template requires a bearer token from Secrets Manager. Tell learners why; it is the first least-privilege decision they make for a customer **[Judgment]**.
- Provider-neutral rule from day one: no model ID in code; config only. Reject PRs that hard-code one.
- Week 1 is the highest-risk week for an unrealistic pace. Check the end-of-day reflection notes each evening and follow up with anyone writing "behind".

### W1.8 Exit checklist

- [ ] G0 exam, practical and mock call done; lane and ILP issued; baseline L0-L4 on file
- [ ] Cohort contract signed; escalation ladder and norms understood
- [ ] Every learner has merged >= 3 reviewed PRs and passes `make verify` on a clean clone
- [ ] Billing alarm active; no root-account use (CloudTrail check)
- [ ] P1-M1 ship demonstrated by every trio with its 20-case assertion file
- [ ] gitleaks blocks a planted key; a secret lives in Secrets Manager
- [ ] First discovery call recorded and scored on R1

### W1.9 Cut or reduced compared with the 24-week plan

The 24-week plan gives onboarding 16 h instead of 10 (adds 4 h of AI-assisted development practice and "how to ask for help / write a good issue") and a 56-h software block, so Week 1 is lighter and the week-1 ship has more scaffolding time **[Sourced: foundation §7.4]**. Here the ship, G0 and onboarding all fit in one week; the 12-week schedule trades repetition for pace.

---

## Week 2: Networks, compute and the first pipeline

*Days 6-10 · Phase A Foundations · Gate: none (weekly quiz) · Project: none (customer: stakeholder map)*

### W2.1 Objectives

By Friday 17:45 a learner can:

- Build a VPC by hand and prove with Reachability Analyzer which paths are allowed and which are denied; explain security groups vs NACLs, NAT and routing.
- Run an EC2 instance with an instance profile (no static keys), read a single S3 prefix, and use presigned URLs.
- Containerise a service, scan it, and push it to ECR with an immutable tag.
- Build a CI pipeline (lint, test, build, push) that authenticates to AWS with OIDC, and add quality and security gates (coverage >= 70%, secret scan, image scan).
- Write a resilient HTTP client (timeouts, retries with jitter, mocks) and a bounded-concurrency, checkpointed batch script.
- Run a service under systemd, read logs, fix permission faults; diagnose DNS and certificate problems with an instructor driving (Breakage 0).
- Produce a stakeholder map and a one-page problem statement for the Kestrel client.

### W2.2 Hours and day-by-day schedule

**Hours this week:** SWF 10 · CLD 12 · DEV 13 · CUS 2.5 · SLK 2.5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D6) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: re-run the Week-1 discovery call with feedback applied (graded on the delta) `W1-L9` |
|  | 09:30-10:30 | 1 | SWF | INS | HTTP clients: timeouts, retries with jitter, idempotency, mocking: worked example |
|  | 10:30-12:30 | 2 | SWF | LAB | Resilient API client `W2-L1` |
|  | 13:15-15:15 | 2 | CLD | INS | VPC: subnets, route tables, IGW/NAT, security groups vs NACLs: worked example |
|  | 15:15-17:45 | 2.5 | CLD | LAB | VPC by hand `W2-L2` |
| Tue (D7) | 09:00-10:00 | 1 | SWF | INS | Linux ops: processes, permissions, systemd, journald |
|  | 10:00-12:00 | 2 | SWF | LAB | Linux ops: services, permissions, logs `W2-L3` |
|  | 12:00-12:30 | 0.5 | DEV | INS | Container recap; registries and ECR |
|  | 13:15-14:15 | 1 | DEV | INS | Docker deeper: multi-stage builds, compose, image scanning |
|  | 14:15-17:15 | 3 | DEV | LAB | Containerise, scan and push to ECR `W2-L4` |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Weekly 1:1 with technical mentor |
| Wed (D8) | 09:00-10:30 | 1.5 | CLD | INS | EC2, EBS, S3 and storage classes; instance profiles and STS |
|  | 10:30-12:30 | 2 | CLD | LAB | EC2 + instance profile + S3 `W2-L5` |
|  | 13:15-14:15 | 1 | DEV | INS | GitHub Actions: workflows, runners, secrets, OIDC to AWS |
|  | 14:15-16:15 | 2 | DEV | LAB | GitHub Actions pipeline with OIDC `W2-L6` |
|  | 16:15-17:45 | 1.5 | CUS | CUS | Customer Lab 2 (Kestrel warehouse supervisor, finance analyst): stakeholder map, problem statement `W2-L7` |
| Thu (D9) | 09:00-10:00 | 1 | DEV | INS | CI quality and security gates; branch protection |
|  | 10:00-12:30 | 2.5 | DEV | LAB | CI quality and security gates `W2-L8` |
|  | 13:15-15:15 | 2 | SWF | LAB | Bounded concurrency and checkpointing `W2-L9` |
|  | 15:15-17:15 | 2 | DEV | LAB | Terraform first steps `W2-L10` |
|  | 17:15-17:45 | 0.5 | CLD | INS | DNS, Route 53 and TLS certificates (concepts; ACM discussed, not built) |
| Fri (D10) | 09:00-10:00 | 1 | CLD | INS | Load balancing and auto scaling: ALB, target groups, ASG |
|  | 10:00-12:30 | 2.5 | CLD | LAB | ALB + auto-scaling group `W2-L11` |
|  | 13:15-15:15 | 2 | SWF | LAB | Breakage 0 (instructor drives; pre-brief: "it is fine not to solve it") `W2-L12` |
|  | 15:15-15:45 | 0.5 | CUS | CUS | Retry: problem statement revised after feedback `W2-L7` |
|  | 15:45-16:15 | 0.5 | SLK | SLK | Weekly retrieval quiz (items from Weeks 1-2) |
|  | 16:15-17:15 | 1 | SLK | SLK | Consolidation: catch up on VPC / CI labs with mentor drop-in |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Friday retro + pulse survey |

### W2.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| HTTP clients and resilience | Timeouts, retries with exponential backoff and jitter, idempotency keys, mocking a flaky server | Worked example with a fake server returning 429s and timeouts; the same pattern returns in Week 9 for LLM calls |
| VPC and networking | Subnets, route tables, IGW/NAT, SG vs NACL, least-privilege rules | Instructor builds a VPC live once; learners rebuild by hand and verify with Reachability Analyzer |
| Linux operations | Processes, permissions, systemd units, journald | Fix three seeded permission faults on a service; `kill -9` the service and watch it restart |
| Docker deeper | Multi-stage builds, compose, scanning, registries (ECR) | Short lecture then lab; "do it manually first, then automate" |
| EC2, EBS, S3, IAM roles and STS | Instance profiles, assume-role, S3 policies, presigned URLs, encryption (`SEC-UNENCRYPTED` seeded) | Lab with a seeded unencrypted bucket the learner must find |
| GitHub Actions | Workflows, runners, secrets, OIDC to AWS, branch protection | Build the pipeline to ECR; reject any long-lived AWS key in repo secrets |
| CI gates | Coverage threshold, gitleaks, Trivy, protected `main` | Seed a secret and a critical CVE; both must fail the build |
| Terraform first steps | `init/plan/apply/destroy`, state concept | Small stack; second `apply` shows no changes |
| ALB and ASG | Target groups, health checks, recovery across AZs | Terminate an instance and measure recovery time |
| Breakage 0 | Network faults `NET-DNS`, `NET-CA`, `NET-IPV6` with the instructor driving the diagnosis ("Sage on the stage") | Pre-brief: "troubleshooting is a series of failures; it is fine not to solve it"; scaffold 0 of Google's Breakage 0-3 **[Sourced: R3 §1.6]** |

### W2.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W2-L1` | Resilient API client | D1 | 2 | HTTP client with timeouts, retries and mocks, tested against a flaky fake server | With a fake server returning 30% 429/timeouts all 100 requests succeed; backoff has jitter (verified from timestamps); >=10 tests |  |
| `W2-L2` | VPC by hand | D2 | 2.5 | VPC with public/private subnets, IGW/NAT, security groups | Reachability Analyzer confirms 4 given paths (2 allowed, 2 denied); private instance reaches the internet only via NAT; no SG open to 0.0.0.0/0 except 443 on the ALB |  |
| `W2-L3` | Linux ops: services, permissions, logs | D1 | 2 | Service run under systemd with restart policy and rotated logs | Unit restarts after `kill -9` within 10 s; 3 seeded permission faults fixed; journald query isolates the failing request |  |
| `W2-L4` | Containerise, scan and push to ECR | D2 | 3 | Image + compose file (app + Postgres) pushed to ECR with an immutable tag | Reproducible build; healthcheck works; Trivy shows 0 critical; compose up works on a clean machine |  |
| `W2-L5` | EC2 + instance profile + S3 | D2, D3 | 2 | EC2 instance reading one S3 prefix via an instance profile | No static keys on the instance; role can read only its prefix (denied elsewhere); presigned URL expires in 5 min; bucket encrypted | FAULT: SEC-UNENCRYPTED (seeded) |
| `W2-L6` | GitHub Actions pipeline with OIDC | D2, D3 | 2 | Workflow: lint -> test -> build -> push to ECR using OIDC (no long-lived AWS keys) | Pipeline <8 min; a failing test blocks the merge; no AWS access key stored in GitHub secrets |  |
| `W2-L8` | CI quality and security gates | D2, D3 | 2.5 | Coverage, secret-scan and image-scan gates in the pipeline; branch protection | Build fails on a seeded secret and on a seeded critical CVE; coverage gate >=70% enforced; main protected |  |
| `W2-L10` | Terraform first steps | D2 | 2 | Terraform for an S3 bucket + role | Second `apply` reports no changes; `destroy` leaves no resources; state location explained |  |
| `W2-L9` | Bounded concurrency and checkpointing | D1 | 2 | Script that processes 500 items with a semaphore, retries and checkpoints | Crash mid-run, resume with zero duplicate calls (from logs); throughput >=5x sequential |  |
| `W2-L11` | ALB + auto-scaling group | D2 | 2.5 | Two-AZ ALB with an ASG behind it | Terminate an instance and traffic recovers <3 min; health checks correct; 5xx rate recorded during the event |  |
| `W2-L12` | Breakage 0: network faults (instructor-driven) | D1, D2 | 2 | Diagnostic checklist completed with the instructor + 5-line blameless postmortem | Checklist followed in order; time_to_first_signal and stall point logged; postmortem names root cause and the signal that proved it | FAULT: NET-DNS, NET-CA, NET-IPV6 |
| `W2-L7` | Customer Lab 2: stakeholder map and problem statement | D6 | 2 | Stakeholder map + 1-page problem statement after a role-played observation of the warehouse supervisor | R1 >=3; problem statement names user, decision and current workaround; no solution proposed | CUSTOMER (R1, R2) |

### W2.5 Customer thread and project milestone

**Customer Lab 2 (Wednesday, 1.5 h) with a 30-min retry on Friday:** learners play the discovery lead for Kestrel; the *warehouse supervisor* and the *finance analyst* personas answer. Exercise: watch the supervisor retype an exception note (role-played observation), then write a stakeholder map (who decides, who is affected, who can block) and a one-page problem statement. The problem statement must name the user, the decision they make, and the current workaround, and **must not propose a solution** (rubrics R1, R2).

Also this week: the Monday retry of Customer Lab 1 (re-run the discovery call with the feedback applied; the *delta* is graded).

No project milestone is scheduled; the build work is the pipeline and container the Kestrel exception tracker will reuse in Weeks 3-4.

### W2.6 Resources

- AWS Certified Cloud Practitioner exam guide: use its domains (cloud concepts, security, services, billing) as a vocabulary checklist only; no exam is funded or gated https://docs.aws.amazon.com/aws-certification/latest/cloud-practitioner-02/cloud-practitioner-02.html **[Sourced: R2 §1.5, V]**
- AWS Solutions Architect Associate exam guide, domains "secure / resilient / high-performing / cost-optimised" as a design checklist https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html **[Sourced: R2 §1.5, V]**
- Full Stack Open, parts 11 (CI/CD) and 12 (containers); exercises submitted through GitHub are a method worth copying https://fullstackopen.com/en/ **[Sourced: R2 §1.3]**. The research could not read the section lists of parts 11-12, so review them before use
- KodeKloud's lecture -> browser lab -> auto-check -> mock-exam loop is the lab format to imitate https://kodekloud.com/learning-path **[Sourced: R2 §1.8]**
- Cloud Resume Challenge (16-step IaC + CI/CD + tests + write-up) as the shape of the Week-4 project https://cloudresumechallenge.dev/docs/the-challenge/ **[Sourced: R2 §1.16]**

### W2.7 Stall points and instructor notes

**Likely stall points:**

1. VPC route-table mistakes (a subnet that is "public" in name only): give the Reachability Analyzer outputs a vocabulary early.
2. OIDC trust-policy syntax between GitHub and AWS: hand out a working trust policy skeleton; the learning is *why no static keys*, not the JSON.
3. Docker image bloat and root users: the scan report is the teacher.
4. Retry loops without jitter in `W2-L1`: show the timestamp plot of a thundering herd.
5. Breakage 0: learners freeze when an instructor "drives"; invite predictions ("what do you expect to see?") before each command.

**Instructor notes**

- First weekly retrieval quiz on Friday (items from Weeks 1-2); keep it low-stakes, 15 minutes, five items.
- Weekly 1:1 mentor slots (30 min) start this week; the mentor does not assess the mentee's gates **[Repo: Ops Guide]**.
- AWS sandbox guardrails (SCP deny-list, tag-on-create) must be live before Monday; verify NAT gateways and large instance types are denied by default and enabled only in lab windows **[Judgment: foundation §9.2]**.
- ACM and Route 53 are discussed, not built (no domain is provisioned); say so explicitly to avoid learners assuming TLS "just works".

### W2.8 Exit checklist

- [ ] A VPC the learner built passes 4 Reachability Analyzer path checks
- [ ] EC2 instance reads only its own S3 prefix with no static keys
- [ ] Image scanned, pushed to ECR with an immutable tag; compose runs on a clean machine
- [ ] CI pipeline uses OIDC; a seeded secret and a seeded critical CVE both fail the build
- [ ] `W2-L1` survives a 30% failure fake server; `W2-L9` resumes after a crash with zero duplicates
- [ ] ALB + ASG recovers from an instance termination in under 3 minutes
- [ ] Stakeholder map and problem statement scored R1/R2 >= 3

### W2.9 Cut or reduced compared with the 24-week plan

The 24-week plan gives Weeks 1-10 a 400-hour foundations phase with deeper AWS networking and IAM (16 h) and full Terraform multi-environment work; here ALB/ASG is a single lab, networking is taught to "reason about reachability" depth, and Terraform is only introduced **[Sourced: foundation §7.4, §7.5]**.

---

## Week 3: Infrastructure as code and the first real scope

*Days 11-15 · Phase A Foundations · Gate: none · Project: P1-M2*

### W3.1 Objectives

By Friday 17:45 a learner can:

- Model a small business domain in SQL (constraints, migrations), write reporting queries, and design a REST API with pagination, idempotency keys and one error model.
- Provision RDS Postgres in private subnets with automated backups and **prove a restore works**.
- Run the Kestrel container on ECS Fargate behind an ALB **by hand first**, then replace the manual build with Terraform modules and remote state, with `terraform plan` running in CI.
- Explain when serverless/event-driven fits and build an S3 -> SQS -> Lambda import with a dead-letter queue.
- Deploy the service to a local Kubernetes cluster (kind) with a rolling update, probes and externalised secrets.
- Tighten IAM policies using the policy simulator and Access Analyzer; scan the image and IaC in CI.
- Write a **one-page scope (PR/FAQ style)** for the Kestrel exception tracker with an explicit out-of-scope list and riskiest assumption, and negotiate it when a change request arrives mid-session.

### W3.2 Hours and day-by-day schedule

**Hours this week:** SWF 7 · CLD 10 · DEV 14 · SEC 2 · CUS 2.5 · PRJ 2 · SLK 2.5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D11) | 09:00-10:00 | 1 | SWF | INS | SQL and data modelling: keys, joins, constraints, migrations |
|  | 10:00-12:00 | 2 | SWF | LAB | SQL and data modelling for Kestrel exceptions `W3-L1` |
|  | 12:00-12:30 | 0.5 | CLD | INS | Where data lives on AWS: relational, key-value, object |
|  | 13:15-14:15 | 1 | CLD | INS | RDS: backups, Multi-AZ, parameter groups, secrets |
|  | 14:15-16:15 | 2 | CLD | LAB | RDS Postgres: private, backed up, restorable `W3-L2` |
|  | 16:15-17:45 | 1.5 | DEV | INS | Terraform: modules, variables, outputs, remote state and locking |
| Tue (D12) | 09:00-12:30 | 3.5 | DEV | LAB | Terraform modules and remote state `W3-L3` |
|  | 13:15-14:45 | 1.5 | CLD | INS | ECS and Fargate: task definitions, services, ALB integration, logs |
|  | 14:45-16:45 | 2 | CLD | LAB | ECS Fargate service behind an ALB (by hand) `W3-L4` |
|  | 16:45-17:45 | 1 | SEC | LAB | IAM least privilege: policy simulator and Access Analyzer `W3-L5` |
| Wed (D13) | 09:00-12:30 | 3.5 | DEV | LAB | Terraform the whole stack `W3-L6` |
|  | 13:15-14:15 | 1 | SWF | INS | API design: resources, pagination, idempotency, error model, OpenAPI |
|  | 14:15-16:15 | 2 | SWF | LAB | API design: resources, pagination, idempotency, errors `W3-L7` |
|  | 16:15-17:45 | 1.5 | DEV | INS | CD to ECS with Actions + OIDC; environments; rollback |
| Thu (D14) | 09:00-10:30 | 1.5 | CLD | INS | Serverless and event-driven patterns: Lambda, API Gateway, SQS/SNS, EventBridge: when not to |
|  | 10:30-12:00 | 1.5 | CLD | LAB | Event-driven mini-pipeline `W3-L8` |
|  | 12:00-12:30 | 0.5 | SWF | INS | HTTP/TLS/DNS debugging recap: curl -v, openssl s_client |
|  | 13:15-13:45 | 0.5 | SWF | LAB | HTTP/TLS/DNS debugging drill (inside the API lab fixtures) `W3-L7` |
|  | 13:45-14:45 | 1 | DEV | INS | Kubernetes: Pods, Deployments, Services, config and secrets |
|  | 14:45-17:45 | 3 | DEV | LAB | Kubernetes intro on kind `W3-L9` |
| Fri (D15) | 09:00-10:00 | 1 | SEC | LAB | Image and IaC scanning in CI `W3-L10` |
|  | 10:00-12:00 | 2 | PRJ | PRJ | P1-M2 Scope and design: architecture one-pager, Terraform skeleton plan, agreed out-of-scope `P1-M2` |
|  | 12:00-12:30 | 0.5 | SLK | SLK | Weekly retrieval quiz (items from Weeks 1-3) |
|  | 13:15-15:45 | 2.5 | CUS | CUS | Customer Lab 3 (Kestrel IT lead, COO): scope doc / PR-FAQ; mid-session change request `W3-L11` |
|  | 15:45-16:45 | 1 | SLK | SLK | Consolidation: finish the Terraform stack; mentor drop-in |
|  | 16:45-17:15 | 0.5 | SLK | SLK | Weekly 1:1 with technical mentor |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Friday retro + pulse survey |

### W3.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| SQL and data modelling | Keys, joins, constraints as business rules, migrations | Model Kestrel's exceptions; three business rules must be enforced by constraints, not application code |
| RDS | Backups, Multi-AZ, parameter groups, secrets in Secrets Manager, private access via SSM | Backup-and-restore drill: restore a snapshot to a new instance and compare row counts |
| Terraform modules and state | Variables, outputs, modules, remote state in S3 with locking | Instructor shows state corruption once so the lock is understood |
| ECS Fargate | Task definitions, services, ALB integration, task roles, logs | Build in the console first and write the steps down; that list becomes the Terraform to-do |
| Terraform the stack | VPC, ECS service, ALB and RDS as code; plan in CI | Destroy and re-create from code only; no console actions |
| IAM least privilege | Policy simulator, Access Analyzer, over-broad policy reduction (`SEC-RBAC` seeded) | Three over-broad policies given; learners cut each with simulator evidence |
| API design | Resources, pagination, idempotency keys, error model, OpenAPI | A replayed POST must produce one row |
| Serverless/event-driven | Lambda, API Gateway, SQS/SNS, EventBridge; when *not* to use them | 1,000-row spreadsheet import; a poison message must land in the DLQ |
| CD to ECS and rollback | Actions + OIDC, environments, rollback | Tie into the Terraform pipeline; practise a rollback |
| Kubernetes intro on kind | Pods, Deployments, Services, ConfigMaps/Secrets, probes | Local cluster only; EKS is reserved for scheduled windows (cost guardrail) **[Judgment: foundation §9.2]** |
| Scanning in CI | Trivy image + config scan | Pipeline fails on a seeded critical; suppression needs written rationale |

### W3.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W3-L1` | SQL and data modelling for Kestrel exceptions | D1 | 2 | Schema, constraints, migration and 6 reporting queries | Schema enforces 3 business rules via constraints; migration is re-runnable; queries return the expected rows on a fixture |  |
| `W3-L2` | RDS Postgres: private, backed up, restorable | D2 | 2 | RDS instance in private subnets reached via SSM; automated backups on | Restore a snapshot to a new instance and verify row counts; no public endpoint; credentials from Secrets Manager |  |
| `W3-L3` | Terraform modules and remote state | D2 | 3.5 | VPC and ECS service skeleton as modules with remote state | `terraform plan` is clean on second run; state in S3 with locking; module inputs/outputs documented |  |
| `W3-L5` | IAM least privilege: policy simulator and Access Analyzer | D3 | 1 | Tightened IAM policies for the stack | Access Analyzer shows no unintended external access; 3 over-broad policies reduced with simulator evidence | FAULT: SEC-RBAC (seeded) |
| `W3-L4` | ECS Fargate service behind an ALB (by hand) | D2 | 2 | Kestrel container running on Fargate behind an ALB, built in the console first | Service healthy behind ALB; logs in CloudWatch; task role is least-privilege; steps written down as the Terraform to-do list |  |
| `W3-L6` | Terraform the whole stack | D2 | 3.5 | ECS + ALB + RDS defined in Terraform, replacing the manual build | Destroy and re-create succeeds from code only; no console action; plan runs in CI on pull requests |  |
| `W3-L7` | API design: resources, pagination, idempotency, errors | D1 | 2.5 | OpenAPI spec and implementation for the exception tracker | Spec lints clean; POST is idempotent via key (replay gives 1 row); errors follow one model; pagination tested |  |
| `W3-L8` | Event-driven mini-pipeline | D2 | 1.5 | S3 upload -> SQS -> Lambda -> database import of a spreadsheet export | Re-delivered message does not duplicate rows; poison message lands in a DLQ; end-to-end import of 1,000 rows |  |
| `W3-L9` | Kubernetes intro on kind | D2 | 3 | Kestrel service as Deployment + Service + ConfigMap + Secret with probes | Rolling update with zero failed requests under light load; readiness probe gates traffic; secret not in image or ConfigMap |  |
| `W3-L10` | Image and IaC scanning in CI | D3 | 1 | Trivy image + config scan wired into the pipeline | Pipeline fails on a seeded critical; findings triaged with written rationale for every suppression |  |
| `W3-L11` | Customer Lab 3: scope document / PR-FAQ and scope negotiation | D6 | 3 | One-page scope (PR/FAQ style) for the Kestrel exception tracker; negotiated with the IT lead | R2 >=3 on every criterion incl. out-of-scope and riskiest assumption; answer-first; readable in 2 minutes | CUSTOMER (R2, R6) |

### W3.5 Customer thread and project milestone

**Customer Lab 3 (Friday, 2.5 h, Kestrel IT lead and COO):** learners write a one-page scope in answer-first / PR-FAQ style, then negotiate it. Mid-session the IT lead raises a change request ("can it also take WhatsApp messages directly?") that tests scope discipline: the correct response names the trade-off, offers a staged option and escalates rather than silently absorbing it.

**R2 criteria:** user, decision and success metric named and measurable; constraints (data, security, systems, people) explicit; out-of-scope and riskiest assumption stated; answer-first and readable in 2 minutes; options with trade-offs and a recommendation **[Sourced: R4 §3.3]**. The retry is Monday of Week 4.

Teach few frameworks and practise many: Minto answer-first writing and the PR/FAQ template only. Impact mapping and Wardley maps are not taught here (the research found no evidence they are used in FDE training **[Sourced: R4 §2.5]**).

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P1-M2` Scope and design the Kestrel exception tracker | Kestrel | 2 | Architecture one-pager + Terraform skeleton plan; scope agreed with out-of-scope and riskiest assumption | Customer-Lab rubric R2 >=3 on every criterion; design names data stored, auth approach, backup and cost cap |

### W3.6 Resources

- HashiCorp Terraform Associate review guide, used as a syllabus checklist (state, modules, providers, plan/apply); no exam is taken https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004 **[Sourced: R2 §1.13; listed, not fully read]**
- AWS Solutions Architect Associate domains (secure, resilient, high-performing, cost-optimised) as the review checklist for the stack https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html **[Sourced: R2 §1.5, V]**
- Minto pyramid / SCQA https://managementconsulted.com/pyramid-principle/ and Amazon Working Backwards PR/FAQ https://aboutamazon.com/news/workplace/an-insider-look-at-amazons-culture-and-processes **[Sourced: R4 §2.4]**; critics note working backwards can over-simplify learning goals
- Udacity's Cloud DevOps nanodegree arc (static site, HA app with IaC, microservice, pipeline) is a useful model for the Week 3-4 project chain https://www.udacity.com/course/cloud-devops-engineer-nanodegree--nd9991 **[Sourced: R2 §1.15; uses CloudFormation, not Terraform]**

### W3.7 Stall points and instructor notes

**Likely stall points:**

1. Terraform state errors and "resource already exists" after the manual build: teach `import` once and otherwise insist on destroy and re-create.
2. RDS reachability from ECS (security-group references vs CIDRs).
3. IAM policy simulator syntax; give two worked examples.
4. API idempotency design: learners confuse PUT semantics with idempotency keys.
5. Scope document written as a solution description: re-read the problem statement from Week 2 and ask "what would make this wrong?".

**Instructor notes**

- Week 3 is the heaviest *foundations* week (14 h DevOps). If more than 40% of the cohort stalls at the same point in the same lab, log it as a curriculum defect with owner and fix date and use Friday consolidation to repair it **[Repo: Handbook Layer 2]**.
- The Kestrel exception tracker is deliberately small: ECS service + ALB + RDS + token auth. Resist adding Cognito or SSO; real OIDC arrives in Week 10.
- Check that every lab ends with a `terraform destroy`; orphaned resources are the main cost risk this week.

### W3.8 Exit checklist

- [ ] RDS restore drill done and verified; no public endpoint
- [ ] Whole Kestrel stack re-creates from Terraform only; plan runs on PRs
- [ ] A replayed POST yields one row; spec lints clean
- [ ] S3 -> SQS -> Lambda import deduplicates and routes a poison message to the DLQ
- [ ] Kubernetes rolling update with zero failed requests; secret not in image or ConfigMap
- [ ] Pipeline fails on a seeded critical finding
- [ ] Scope one-pager scored R2 >= 3 on every criterion (including out-of-scope and riskiest assumption)

### W3.9 Cut or reduced compared with the 24-week plan

The 24-week plan spends 72 h on cloud and 104 h on DevOps/K8s (Terraform state, modules and multi-environment in full; Kubernetes with CKA-style troubleshooting drills; EKS) and has more repetitions of scope-writing across P1-P4 **[Sourced: foundation §7.4]**. Here Kubernetes is a single-day introduction on kind and serverless is one lab.

---

## Week 4: Observe, operate and prove it (G1)

*Days 16-20 · Phase A Foundations · Gate: G1 (Day 20) · Project: P1-M3*

### W4.1 Objectives

By Friday 17:45 a learner can:

- Instrument a service on AWS (structured logs, a custom metric, a dashboard, an alarm that really fires) and define **three SLOs with burn-rate alerts as code**.
- Reason about reporting data: reconcile two sources and find where "what the schema stores" differs from "what the report means" (the "report that is always wrong" mini-lab).
- Troubleshoot Kubernetes faults systematically on kind (`K8S-CRASHLOOP`, `K8S-IMGPULL`) with a coach, logging stall points.
- Apply FinOps basics: tags, Budgets with an action, Cost Explorer, safe cleanup (dry-run first).
- Run Terraform in CI (plan on PR, apply on merge, drift detection) and add autoscaling to the service.
- Scan dependencies and write a STRIDE-lite threat model.
- **Pass G1:** rebuild the Kestrel stack in a fresh sandbox from `git clone` in under 60 minutes with zero console actions.
- Hand the Kestrel exception tracker to the IT-lead persona with a runbook, cost note and risk note (P1-M3).

### W4.2 Hours and day-by-day schedule

**Hours this week:** SWF 4 · CLD 8 · DEV 11 · SEC 2 · CUS 2 · PRJ 3 · ASM 5 · SLK 5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D16) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: scope doc revised after feedback `W3-L11` |
|  | 09:30-10:30 | 1 | SWF | INS | SQL for operations: joins, windows, data-quality checks |
|  | 10:30-12:30 | 2 | SWF | LAB | The report that is always wrong (mini) `W4-L1` |
|  | 13:15-14:15 | 1 | CLD | INS | CloudWatch: metrics, logs, alarms, dashboards |
|  | 14:15-16:45 | 2.5 | CLD | LAB | Observability on AWS: logs, metrics, dashboard, alarm `W4-L2` |
|  | 16:45-17:45 | 1 | DEV | INS | SLIs, SLOs, error budgets, burn-rate alerting (SRE Workbook ch. 2/5) |
| Tue (D17) | 09:00-11:30 | 2.5 | DEV | LAB | Three SLOs with burn-rate alerts as code `W4-L3` |
|  | 11:30-12:30 | 1 | SWF | LAB | The report that is always wrong (mini): tests and write-up `W4-L1` |
|  | 13:15-14:15 | 1 | DEV | INS | Kubernetes troubleshooting method: describe, events, logs, exec, network policy |
|  | 14:15-17:15 | 3 | DEV | LAB | Breakage 1 (coach mode): crash loops and image pulls `W4-L4` |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Weekly 1:1 with technical mentor |
| Wed (D18) | 09:00-10:00 | 1 | CLD | INS | FinOps basics: tags, budgets, rightsizing, teardown |
|  | 10:00-12:00 | 2 | CLD | LAB | Cost controls and tagging `W4-L5` |
|  | 12:00-12:30 | 0.5 | SEC | INS | Threat modelling lite: STRIDE on a data-flow diagram |
|  | 13:15-14:15 | 1 | CUS | CUS | Customer Lab 4 (Kestrel COO): status update + bad-news call `W4-L6` |
|  | 14:15-15:15 | 1 | PRJ | PRJ | P1-M3 build: restore-from-backup drill, auth token rotation, budget cap `P1-M3` |
|  | 15:15-17:45 | 2.5 | DEV | LAB | Terraform in CI: plan on PR, apply on merge, drift `W4-L7` |
| Thu (D19) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: bad-news call re-recorded `W4-L6` |
|  | 09:30-10:00 | 0.5 | CLD | INS | Autoscaling and resilience: Well-Architected lens |
|  | 10:00-11:00 | 1 | CLD | LAB | ECS target-tracking autoscaling `W4-L8` |
|  | 11:00-12:30 | 1.5 | SEC | LAB | Dependency scanning and threat model (lite) `W4-L9` |
|  | 13:15-14:15 | 1 | DEV | INS | G1 briefing: fresh-sandbox rules, zero-console rule, checklist, parallel-task retake |
|  | 14:15-16:15 | 2 | PRJ | PRJ | P1-M3 hand over: runbook, cost/risk note, cold-follow by a peer `P1-M3` |
|  | 16:15-17:45 | 1.5 | SLK | SLK | Consolidation: G1 practice run (timed, fresh sandbox) `W4-L10` |
| Fri (D20) | 09:00-12:30 | 3.5 | ASM | ASM | G1 Platform: rebuild from scratch (staggered 60-min windows, novel sandbox, randomised fault variant, screen-recorded) |
|  | 13:15-14:45 | 1.5 | ASM | ASM | G1 rubric debrief and individual feedback; parallel-task retakes booked for Week 5 slack |
|  | 14:45-15:15 | 0.5 | SLK | SLK | Weekly retrieval quiz (items from Weeks 1-4) |
|  | 15:15-16:15 | 1 | SLK | SLK | Consolidation: mentor 1:1, remediation plan |
|  | 16:15-17:15 | 1 | SLK | SLK | Friday retro + pulse survey; Week-5 preview |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Buffer: finish open labs |

### W4.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| SQL for operations and the "wrong report" | Joins, window functions, data-quality checks, five-whys **with its limits** (single chain, only as good as the answers; validate each "why" with evidence) | Reconcile two Kestrel sources; six data tests; the learner must show evidence for every "why" **[Sourced: R4 §2.5]** |
| CloudWatch observability | Metrics, logs, alarms, dashboards; structured logging with a request id | The alarm must fire in a deliberate failure test |
| SLIs, SLOs, burn-rate alerts | Error budgets, multi-window burn rates, what an operator needs on a dashboard | SRE Workbook chapters 2 and 5 as reading; build three SLOs (availability, latency, error budget) in Terraform |
| Kubernetes troubleshooting method | `describe`, events, logs, `exec`, network policy; hypothesis, test, narrow | Breakage 1 (coach mode): two seeded faults with instructor questions; stall points logged **[Sourced: R3 §1.6, Build/Stretch/Reach]** |
| FinOps | Tags, Budgets with actions, rightsizing, teardown | Show that Budgets act with lag and are not an instantaneous cap (layered controls) **[Sourced: R2 §3.3]**; nuke dry-run only |
| Terraform in CI and drift | Plan on PR, apply on merge, scheduled drift plan (`IAC-DRIFT`) | A teammate "clicks in the console"; the scheduled plan must catch it |
| Autoscaling and resilience | ECS target tracking; Well-Architected lens | Load test; no 5xx beyond SLO during scale-out |
| Threat modelling lite | STRIDE on a data-flow diagram | Six threats, each with a control or an accepted risk |
| G1 briefing | Fresh-sandbox rules, zero-console rule, checklist, parallel-task retake policy | Pre-brief on Thursday; timed practice run on Thursday afternoon |

### W4.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W4-L1` | The report that is always wrong (mini) | D1 | 3 | Reconciliation of two Kestrel sources with schema-vs-meaning gaps found and tested | Finds >=3 gaps between what the schema stores and what the report means; 6 data tests added; 5-whys with evidence for each (not speculation) | DATA-QUALITY (silent-encoding case; full DATA-* faults are 24-week only) |
| `W4-L2` | Observability on AWS: logs, metrics, dashboard, alarm | D2, D5 | 2.5 | Structured logs, one custom metric, a dashboard and an alarm for the Kestrel stack | Alarm fires in a deliberate failure test; dashboard shows request rate, errors and p95 latency; logs queryable by request id |  |
| `W4-L3` | Three SLOs with burn-rate alerts as code | D2, D5 | 2.5 | 3 SLOs (availability, latency, error budget) with burn-rate alerts in Terraform | Each alert fires in a synthetic test; an operator who did not build it can state the SLO from the dashboard alone |  |
| `W4-L4` | Breakage 1 (coach mode): crash loops and image pulls | D2 | 3 | Two seeded faults on kind diagnosed and fixed; stall points logged | Both faults fixed with systematic isolation (describe/events/logs); hints taken logged; 3-line blameless note each | FAULT: K8S-CRASHLOOP, K8S-IMGPULL |
| `W4-L5` | Cost controls and tagging | D2 | 2 | Tag policy, Budgets with an action, Cost Explorer view; dry-run of resource cleanup | Untagged resource is flagged; budget action attaches a deny policy in a test; nuke dry-run lists only learner-tagged resources |  |
| `W4-L7` | Terraform in CI: plan on PR, apply on merge, drift | D2 | 2.5 | Pipeline that plans on PR and applies on merge; drift detected and reconciled | A console change is detected by scheduled plan; plan output posted on the PR; apply is gated on review | FAULT: IAC-DRIFT |
| `W4-L8` | ECS target-tracking autoscaling | D2 | 1 | Autoscaling policy on the Kestrel service with a load test | Replicas scale out under load and back in; no 5xx beyond SLO during scale-out |  |
| `W4-L9` | Dependency scanning and threat model (lite) | D3 | 1.5 | SCA scan in CI + STRIDE-lite threat model of the Kestrel app | Zero unreviewed high findings; threat model lists 6 threats each with a control or accepted risk | FAULT: SEC-NETPOL-OPEN (variant) |
| `W4-L10` | G1 practice run (timed, fresh sandbox) | D2 | 1.5 | One timed rebuild of the Kestrel stack in a new sandbox, observed by a peer | Time recorded; peer fills the G1 checklist; gaps become the remediation list | FAULT: IAC-DRIFT (variant) |
| `W4-L6` | Customer Lab 4: status update and bad-news call | D6 | 1.5 | Answer-first status update + a recorded bad-news call (cost overrun) with the Kestrel COO | R5 >=3 (bottom line first, risk with options); R6 >=3 (raised early, options + recommendation, concrete next step) | CUSTOMER (R5, R6) |

### W4.5 Customer thread and project milestone

**Customer Lab 4 (Wednesday, 1 h, Kestrel COO):** an answer-first status update and a recorded *bad-news call*: the build cost has overrun the cap. Retry on Thursday (0.5 h). **R5:** bottom line first, risk with options, no surprise relative to the last update. **R6:** raised early, owned without blame or over-promising, options plus a recommendation, a concrete next step **[Sourced: R4 §3.3]**.

**Project P1-M3 (3 h across Wednesday-Thursday)** closes project P1: backup-restore drill, token rotation, budget cap, runbook, cost and risk note, and a *cold-follow by a peer* (a different trio runs the deploy and rollback from the runbook only). Handover acceptance is the IT-lead persona's sign-off (R8 >= 3).

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P1-M3` Build, harden and hand over the Kestrel exception tracker (minimal) | Kestrel | 3 | Terraform-defined ECS Fargate service + ALB + RDS Postgres (backups on, token auth from Secrets Manager, budget cap), CI pipeline, runbook, cost/risk note | Stack rebuilds from `git clone` by Terraform + CI only; restore-from-backup drill done; runbook followed cold by a peer for deploy + rollback; cost note within the $ cap; the IT-lead persona accepts the handover (R8 >=3) |

### W4.6 Resources

- Google SRE Workbook table of contents (Implementing SLOs; Alerting on SLOs; Incident Response; Postmortem Culture) https://sre.google/workbook/table-of-contents/ **[Sourced: R2 §1.11, V]**
- AWS Budgets actions (apply an IAM policy or SCP, or stop EC2/RDS at a threshold; data lag is not stated, so do not treat Budgets as an instant cap) https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/budgets-controls.html **[Sourced: R2 §3.3, V]**
- Linux Foundation "Introduction to Kubernetes" (free; 15-20 h; architecture, Minikube, services, storage, ConfigMaps/Secrets, Ingress) https://training.linuxfoundation.org/training/introduction-to-kubernetes/ **[Sourced: R2 §1.9, V]**
- *Training Site Reliability Engineers* for the Breakage Service and Build/Stretch/Reach scaffold https://sre.google/static/pdf/TrainingSiteReliabilityEngineers.pdf **[Sourced: R3 §1.6]**

### W4.7 Stall points and instructor notes

**Likely stall points:**

1. Burn-rate alert math (two windows, thresholds): give a worked example and a calculator sheet.
2. Alerts that are syntactically valid but never fire (a common G1 failure per the repo): the lab requires a test that makes the alert fire.
3. K8s `NetworkPolicy` and DNS interplay.
4. G1 nerves and console reflexes: learners click when the clock runs. Practise on Thursday with the stopwatch visible.
5. Terraform apply ordering for ECS + ALB + RDS: pre-provide the dependency diagram.

**Instructor notes**

- **G1 is on Friday (Day 20).** Use a *fresh, empty* sandbox account per learner and a *randomised fault variant* (an `IAC-DRIFT`-family variant) so memory is not what is tested **[Repo: Assessment Pack G1]**.
- Parallel-task retakes use the same rubric in a different environment or fault variant, scheduled in Week 5 slack, never evenings or weekends.
- Check that G1 assessors are independent of the mentor relationship.

### W4.8 Exit checklist

- [ ] Three SLOs live with alerts proved to fire; an outsider can read the SLO from the dashboard
- [ ] "Wrong report" findings with evidence for each why
- [ ] Two K8s faults fixed with systematic isolation; stall points logged
- [ ] Drift is detected by the scheduled plan; plan output posted on the PR
- [ ] STRIDE-lite threat model with six threats and controls
- [ ] P1 handed over; runbook followed cold by a peer; R8 >= 3
- [ ] G1 attempted; individual feedback delivered; any retake booked for Week 5

### W4.9 Cut or reduced compared with the 24-week plan

The 24-week G1 is stricter (add autoscaling and a Kubernetes deployment) and comes at Day 40 after a 10-week foundations phase; Kubernetes includes CKA-style troubleshooting drills (no exam) and the SRE block adds incident response and fault injection with AWS FIS/Litmus **[Sourced: foundation §6.3, §7.4]**. Here Kubernetes troubleshooting is two coached faults and G1 does not require Kubernetes.

---

## Week 5: Secure the pipeline; first contact with LLMs

*Days 21-25 · Phase B Secure + AI on-ramp · Gate: none (G1 retakes in slack) · Project: none (customer: Linden contact)*

### W5.1 Objectives

By Friday 17:45 a learner can:

- Add SAST (Semgrep), SCA + SBOM (CycloneDX), DAST (OWASP ZAP against Juice Shop) and IaC/policy scanning (Checkov/Trivy config + OPA/conftest) to a pipeline, triage findings with written rationale, and explain what an SBOM does *and does not* tell you.
- Explain how an LLM works well enough to debug it: tokens, context windows, sampling, embeddings, why models fail; choose between a classifier and an LLM using accuracy, latency and cost.
- Write asynchronous, bounded-concurrency, checkpointed LLM batch jobs and a tested, validated data module (pydantic/pandera).
- Wrap an LLM function as a typed FastAPI service with provider/model in config.
- Use schema-constrained structured output, measure the prompt-only vs constrained difference, and improve a prompt over three scored iterations without overfitting (held-out check).
- Fix two more coached Kubernetes faults, including an unsatisfiable resource request (`K8S-PENDING-GPU`) and DNS blocked by a NetworkPolicy.
- Decompose a vague customer problem on the Linden vignette and run a first discovery call with the VP Claims Operations.

**This is the AI on-ramp week** (21 h of AI Core, 8 h of security pipeline). It is the pre-work that makes the heavy Week 7-9 AI load survivable (foundation risk 1).

### W5.2 Hours and day-by-day schedule

**Hours this week:** DEV 4 · SEC 8 · AIC 21 · CUS 2.5 · SLK 4.5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D21) | 09:00-10:30 | 1.5 | AIC | INS | How LLMs work for FDEs: tokens, context, sampling, embeddings, why models fail; provider-neutral API tour (2 endpoints) |
|  | 10:30-12:30 | 2 | AIC | LAB | Tokens, embeddings and nearest-neighbour search `W5-L1` |
|  | 13:15-15:45 | 2.5 | AIC | LAB | LLM vs classifier bake-off `W5-L2` |
|  | 15:45-16:15 | 0.5 | SEC | INS | SAST: how it works, what it misses |
|  | 16:15-17:45 | 1.5 | SEC | LAB | SAST in the pipeline (Semgrep) `W5-L3` |
| Tue (D22) | 09:00-10:00 | 1 | AIC | INS | Python for AI work: pydantic contracts, async + bounded concurrency, pandas/DuckDB |
|  | 10:00-12:30 | 2.5 | AIC | LAB | Batch an LLM job: async, retries, checkpoints `W5-L4` |
|  | 13:15-15:45 | 2.5 | AIC | LAB | Messy CSV to validated Parquet module `W5-L5` |
|  | 15:45-16:15 | 0.5 | SEC | INS | SCA and SBOMs: what an SBOM does and does not tell you |
|  | 16:15-17:45 | 1.5 | SEC | LAB | SCA and a signed-style SBOM `W5-L6` |
| Wed (D23) | 09:00-11:00 | 2 | AIC | LAB | Wrap the LLM function as a FastAPI service `W5-L7` |
|  | 11:00-12:30 | 1.5 | AIC | INS | Prompting patterns; structured outputs (schema-constrained); retry-with-error-feedback; prompts versioned in git |
|  | 13:15-15:45 | 2.5 | AIC | LAB | Structured extraction: prompt-only vs schema-constrained `W5-L8` |
|  | 15:45-16:15 | 0.5 | DEV | INS | K8s faults as classes: scheduling, networking, resources |
|  | 16:15-17:45 | 1.5 | DEV | LAB | Breakage 2 (guide on the side): OOM and HPA with no metrics `W5-L9` |
| Thu (D24) | 09:00-12:00 | 3 | AIC | LAB | Prompt A/B on a held-out set `W5-L10` |
|  | 12:00-12:30 | 0.5 | SLK | SLK | Weekly 1:1 with technical mentor |
|  | 13:15-13:45 | 0.5 | SEC | INS | DAST: what runtime scanning finds; Juice Shop scoreboard |
|  | 13:45-15:15 | 1.5 | SEC | LAB | DAST against OWASP Juice Shop `W5-L11` |
|  | 15:15-17:15 | 2 | DEV | LAB | Breakage 2b: DNS blocked by NetworkPolicy and unschedulable pod `W5-L12` |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Weekly retrieval quiz (items from Weeks 2, 4, 5) |
| Fri (D25) | 09:00-09:30 | 0.5 | SEC | INS | IaC scanning and policy as code |
|  | 09:30-11:00 | 1.5 | SEC | LAB | IaC scanning and policy as code `W5-L13` |
|  | 11:00-12:30 | 1.5 | SLK | SLK | Consolidation: second attempts on prompt A/B and extraction |
|  | 13:15-15:45 | 2.5 | CUS | CUS | Customer Lab 5 (Linden VP Claims Ops): decomposition drill, first discovery call `W5-L14` |
|  | 15:45-16:45 | 1 | SLK | SLK | G1 retakes on a parallel task (only learners who need them) |
|  | 16:45-17:15 | 0.5 | SLK | SLK | Friday retro + pulse survey |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Pre-reading for Week 6 (tool use, evals) |

### W5.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| How LLMs work (for FDEs) | Tokens, context, sampling, embeddings, causes of failure, the provider-neutral API (two endpoints: hosted Claude default plus one OpenAI-compatible) | 20-min lecture; every later lab runs against both endpoints (principle P16) **[Sourced: R5 §3 principle 5]** |
| Embeddings and nearest-neighbour search | Cosine similarity; what retrieval can and cannot do | Tokenise 20 awkward strings (numbers, code, non-English); 500-doc search; learners explain three failure cases |
| Classifier vs LLM | Base rates, class imbalance, why accuracy misleads, when a TF-IDF + logistic regression beats an LLM | 300-ticket bake-off; the table must justify the recommendation on accuracy, latency *and* cost **[Sourced: R5 T1 lab 3]** |
| Python for AI work | pydantic contracts, async with bounded concurrency, pandas/DuckDB, no notebook as deliverable | Crash a batch job mid-run and resume with zero duplicate calls |
| Prompting and structured output | Role/task/constraints/examples/schema; schema-constrained output vs "please return JSON"; retry with error feedback; prompts versioned in git | Measure prompt-only vs constrained schema-validity on 100 documents; Anthropic's strict mode has schema limits (no recursive schemas) **[Sourced: R5 T3, V]** |
| Prompt iteration discipline | Score every change on the same set; check a different holdout | Three iterations on a 50-example set; the 25-example holdout catches overfitting |
| SAST, SCA/SBOM, DAST, IaC policy | Semgrep, CycloneDX, ZAP, Checkov/Trivy, OPA/conftest; triage and suppression rules | Pipeline stages in order (secrets -> SCA -> SAST -> DAST -> IaC) follow the OWASP DevSecOps Guideline and the Practical DevSecOps module order **[Sourced: R2 §1.14]** |
| Kubernetes faults as classes | Scheduling, networking, resources: `K8S-OOM`, `K8S-HPA-NOMETRICS`, `K8S-NETPOL-DNS`, `K8S-PENDING-GPU` | Breakage 2 (guide on the side): the instructor only asks questions **[Sourced: R3 §1.6]** |

### W5.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W5-L1` | Tokens, embeddings and nearest-neighbour search | D4 | 2 | Notebook: tokenise 20 awkward strings; embed 500 docs; cosine search | Correct top-1 on a 20-query hand-labelled set >=70%; learner explains 3 failure cases in their own words |  |
| `W5-L2` | LLM vs classifier bake-off | D4 | 2.5 | 300 labelled support tickets classified three ways (TF-IDF+LR, zero-shot LLM, few-shot LLM) | One table of accuracy, p50 latency and cost per 1k items; recommendation justified on all three axes (a classifier winning is an acceptable answer) | AI-EVAL |
| `W5-L4` | Batch an LLM job: async, retries, checkpoints | D1, D4 | 2.5 | Async pipeline over 2,000 documents with a schema-constrained LLM call | Crash mid-run then resume with zero duplicate calls (from logs); throughput >=5x sequential; failures routed to a retry file | AI-EVAL |
| `W5-L5` | Messy CSV to validated Parquet module | D1, D4 | 2.5 | Notebook turned into a tested module (pydantic/pandera) | >=10 pytest cases incl. 3 malformed-input cases; schema validated; CI green |  |
| `W5-L7` | Wrap the LLM function as a FastAPI service | D1, D4 | 2 | Typed endpoint, health check, container | OpenAPI schema generated; invalid payload returns 422; container builds and runs; provider/model read from config |  |
| `W5-L8` | Structured extraction: prompt-only vs schema-constrained | D4 | 2.5 | 100-document extraction to a pydantic schema | >=98% schema-valid with constrained output (prompt-only rate measured and compared); field-level accuracy >=90% against gold labels | AI-EVAL |
| `W5-L10` | Prompt A/B on a held-out set | D4 | 3 | Classification prompt improved over 3 iterations | Every iteration scored on the same 50-example set; no iteration merged without a score; final beats baseline by a pre-declared margin AND passes a different 25-example holdout | AI-EVAL |
| `W5-L3` | SAST in the pipeline (Semgrep) | D3 | 1.5 | Semgrep rules in CI over the Kestrel code | Each seeded vulnerability class detected; every suppression has a written rationale; one finding fixed and re-scanned |  |
| `W5-L6` | SCA and a signed-style SBOM | D3 | 1.5 | CycloneDX SBOM generated for the image; SCA triage | SBOM matches the deployed image digest (checked by script); zero untriaged high/critical findings |  |
| `W5-L9` | Breakage 2 (guide on the side): OOM and HPA with no metrics | D2 | 1.5 | Two seeded faults fixed with instructor only asking questions | Each fixed within 25 min with <=1 hint; stall points logged; fix explained as a class of problem | FAULT: K8S-OOM, K8S-HPA-NOMETRICS |
| `W5-L12` | Breakage 2b: DNS blocked by NetworkPolicy and unschedulable pod | D2 | 2 | Two more seeded faults, including an unsatisfiable resource request | Each fixed within 25 min with <=1 hint; learner states how the symptom differed from the cause | FAULT: K8S-NETPOL-DNS, K8S-PENDING-GPU |
| `W5-L11` | DAST against OWASP Juice Shop | D3 | 1.5 | ZAP baseline scan in CI against Juice Shop; findings triaged | >=5 findings triaged with severity and exploitability reasoning; one class fixed in the learner's own app and re-scanned |  |
| `W5-L13` | IaC scanning and policy as code | D3 | 1.5 | Checkov/Trivy config scan + OPA/conftest policies in CI | Pipeline blocks a public S3 bucket and an open security group (2 policy tests); policy has a documented exception path |  |
| `W5-L14` | Customer Lab 5: decomposition and first Linden contact | D6 | 3 | Narrated issue-tree for "claims backlog is growing" + first discovery call with the Linden VP Claims Operations | R3 >=3: clarified user and decision before solving; prioritised branches with reasons; executable first slice; 40% talk-share ceiling held | CUSTOMER (R3, R1) |

### W5.5 Customer thread and project milestone

**Customer Lab 5 (Friday, 2.5 h) introduces the second client, Linden Claims Services** (regulated, 1,200 staff, 5,000+ documents, SSO over an LDAP-backed legacy, an air-gapped analyst enclave **[Judgment: foundation §8.1]**). Exercise: a narrated **issue-tree decomposition** of "claims backlog is growing" (clarify the user and decision before solving; prioritise branches with reasons; model the entities; propose an executable first slice; plan validation), followed by a first discovery call with the VP Claims Operations persona. **R3** criteria and the 40% talk-share ceiling apply. The retry is Monday of Week 6.

Decomposition is taught as a weekly 45-minute drill in the style of Palantir's decomposition interview; the research notes that the five-dimension checklist is course-authored, not Palantir's rubric, so do not attribute it to Palantir **[Sourced: R4 §2.3]**.

### W5.6 Resources

- Google Machine Learning Crash Course (embeddings, LLMs, production ML) https://developers.google.com/machine-learning/crash-course **[Sourced: R5 T1, V]**
- Hugging Face LLM Course, chapter 1 (transformers, tokenisers) https://huggingface.co/learn/llm-course/chapter1/1 **[Sourced: R5 T1, V]**
- Applied LLMs (tactical section: prompting, structured output; Instructor/Outlines for structured output) https://applied-llms.org/ **[Sourced: R5 T3, V]**
- Eugene Yan, *Patterns for Building LLM-based Systems & Products* https://eugeneyan.com/writing/llm-patterns/ **[Sourced: R5 T3, V]**
- OWASP DevSecOps Guideline (pipeline checklist) https://owasp.org/www-project-devsecops-guideline/ and OWASP Juice Shop (free target) https://owasp.org/www-project-juice-shop/ **[Sourced: R2 §1.14, V]**

### W5.7 Stall points and instructor notes

**Likely stall points (this is the 12-week program's second-highest-risk week):**

1. Async + semaphore + checkpoint design: show a minimal correct skeleton and have learners extend it.
2. pandera/pydantic error messages: write the failing test first.
3. "Prompt A/B improved but the holdout did not": treat this as the lesson, not a failure.
4. Semgrep/ZAP false positives eating the lab: cap triage at 5 findings; the skill is rationale.
5. LLM provider rate limits at cohort scale: the gateway enforces per-learner caps; stagger heavy labs across trios.

**Instructor notes**

- G1 parallel-task retakes happen Friday (1 h in slack); schedule assessors who did not mark the original attempt.
- Begin logging AI telemetry fields this week: `eval_pass_rate`, `trace_url`, `cost_per_run`, `prompt_version`, `model_config_id` (never a hard-coded model name) **[Judgment: foundation §6.9]**.
- Remind learners that the Week-1 assertion file now becomes a prompt-regression harness (Week 6).
- Re-verify the tool flags in foundation §10 at T-4 weeks: Semgrep, Trivy, ZAP, CycloneDX are standard but were not re-verified in the research **[Sourced: R5 flags]**.

### W5.8 Exit checklist

- [ ] All four security stages (SAST, SCA/SBOM, DAST, IaC policy) run in one pipeline; every suppression has a rationale
- [ ] SBOM matches the deployed image digest
- [ ] Bake-off table with a justified recommendation
- [ ] Batch job resumes after a forced crash with zero duplicate calls
- [ ] Prompt iteration: three scored runs, holdout checked
- [ ] Constrained extraction >= 98% schema-valid; field accuracy >= 90%
- [ ] Four K8s faults fixed over Weeks 4-5 with stall points logged
- [ ] Decomposition drill scored R3 >= 3

### W5.9 Cut or reduced compared with the 24-week plan

The 24-week plan runs AI Core as 190 h (T1 14 h, T2 16 h, T3 16 h) and starts it in Weeks 11-12 after a full foundations phase, with extra worked examples and a classical-ML walkthrough; here T1-T3 total 21 h in one week and ML "from scratch" is dropped **[Sourced: foundation §7.3, §7.5]**.

---

## Week 6: Tools, evals-first and the security review (G2)

*Days 26-30 · Phase B Secure + AI on-ramp · Gate: G2 (Day 30); midpoint re-score · Project: none (G2 artifact pack)*

### W6.1 Objectives

By Friday 17:45 a learner can:

- Build a hand-written tool loop (no framework), design tool descriptions that reduce wrong-tool calls, and add a safe write tool (idempotency key, dry-run, per-call authorisation enforced in code).
- Run **error analysis** on real traces (open coding, taxonomy, counts) and convert the taxonomy into deterministic assertions.
- Audit an agent architecture against the **lethal trifecta** (private data + untrusted content + external communication) and redesign it.
- Assemble the **seven G2 artifacts** for the Kestrel stack and defend them in a 45-minute mock enterprise security review, answering with evidence or an honest "I don't know".
- Run a blameless incident drill (Wheel of Misfortune) as primary/secondary on-call.
- Explain a security block to a CISO delegate in plain language and propose a compliant path.
- **Pass G2** and record the **midpoint competency re-score**.

### W6.2 Hours and day-by-day schedule

**Hours this week:** DEV 2 · SEC 6 · AIC 16 · AIO 4 · CUS 2.5 · ASM 4 · SLK 5.5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D26) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: decomposition + discovery re-run with feedback `W5-L14` |
|  | 09:30-10:00 | 0.5 | AIC | INS | Break-it framing: how AI systems fail on the unexpected |
|  | 10:00-12:30 | 2.5 | AIC | LAB | Break-it lab: schemas and malformed inputs `W6-L1` |
|  | 13:15-14:45 | 1.5 | AIC | INS | Tool use and agent-computer interfaces: writing tools like docstrings for a junior developer |
|  | 14:45-17:45 | 3 | AIC | LAB | Hand-written tool loop (no framework) `W6-L2` |
| Tue (D27) | 09:00-10:30 | 1.5 | AIC | LAB | Tool-description tuning `W6-L3` |
|  | 10:30-11:30 | 1 | AIC | LAB | A safe write tool `W6-L4` |
|  | 11:30-12:30 | 1 | SEC | INS | Threat modelling: STRIDE on a data-flow diagram; OWASP LLM Top 10 (2025) as a checklist |
|  | 13:15-14:45 | 1.5 | AIC | INS | Evals: read traces first; open/axial coding; binary labels; assertions before judges |
|  | 14:45-17:45 | 3 | AIC | LAB | Error-analysis sprint `W6-L5` |
| Wed (D28) | 09:00-10:30 | 1.5 | AIC | LAB | Assertions first: 20 cases for the Week-1 service `W6-L6` |
|  | 10:30-11:00 | 0.5 | AIO | INS | Prompt injection: direct vs indirect; the lethal trifecta; why detectors are not a boundary |
|  | 11:00-12:30 | 1.5 | AIO | LAB | Lethal-trifecta audit and injection basics (part 1) `W6-L7` |
|  | 13:15-14:45 | 1.5 | CUS | CUS | Customer Lab 6 (Linden CISO delegate): plain-language "no", compliant path, honest "I don't know" `W6-L8` |
|  | 14:45-17:45 | 3 | SEC | LAB | Security-review rehearsal (G2 mock): assemble artifacts, mock panel `W6-L9` |
| Thu (D29) | 09:00-10:00 | 1 | ASM | ASM | G2 artifact pack frozen and automatically checked (24 h before the panel) |
|  | 10:00-12:00 | 2 | AIO | LAB | Lethal-trifecta audit and injection basics (part 2) `W6-L7` |
|  | 12:00-12:30 | 0.5 | CUS | CUS | Retry: security-review conduct role-play `W6-L8` |
|  | 13:15-15:15 | 2 | SEC | LAB | Security-review rehearsal (second mock, different panel) `W6-L9` |
|  | 15:15-17:15 | 2 | DEV | LAB | Wheel of Misfortune #1: incident drill and blameless debrief `W6-L10` |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Weekly retrieval quiz (moved to Thursday in gate weeks) |
| Fri (D30) | 09:00-12:00 | 3 | ASM | ASM | G2 Secure delivery review: 45-min panel defence, feedback, and peer-observation scoring of two other defences |
|  | 12:00-12:30 | 0.5 | SLK | SLK | Mentor 1:1 |
|  | 13:15-14:15 | 1 | SLK | SLK | Midpoint competency re-score (self-rating vs assessor) and ILP update |
|  | 14:15-15:45 | 1.5 | SLK | SLK | Consolidation: remediation on G2 gaps (parallel-task retake booked for Week 8 Friday if needed) |
|  | 15:45-16:45 | 1 | SLK | SLK | Consolidation: catch up on open AI labs |
|  | 16:45-17:15 | 0.5 | SLK | SLK | Pre-reading for Week 7 (RAG, contextual retrieval) |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Friday retro + pulse survey |

### W6.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| Break-it: schemas and malformed inputs | Empty, huge, multilingual and injected inputs; retry loops; "needs human" route | 10 adversarial inputs; validator must catch 100% |
| Tool use and agent-computer interface | Tool design "as docstrings for a junior developer"; consolidate tools; return meaningful context; errors that tell the agent how to fix the call | Hand-written loop first (principle P6), then description tuning on a deliberately ambiguous 6-tool set **[Sourced: R5 T4, V: Anthropic "Writing tools for agents"]** |
| Safe write tools | Idempotency keys, dry-run, authorisation in code | Replay a call: exactly one side effect |
| Evals: read traces first | Open/axial coding, binary labels, assertions before judges | 60-trace error-analysis sprint on a provided support bot; counts decide priorities **[Sourced: R5 T6]** |
| Assertions first | Turn the taxonomy into 20 deterministic checks for the Week-1 service | Two cases must fail when the prompt is deliberately broken |
| Threat modelling | STRIDE on data-flow diagrams; OWASP LLM Top 10 (2025) as a checklist (LLM01 Prompt Injection ... LLM10 Unbounded Consumption) | Map each learner's Kestrel threat model to 3 LLM items |
| Prompt injection and the lethal trifecta | Direct vs indirect injection; why detectors are not a security boundary (adaptive attacks bypassed 12 published defences at >90% success, per Willison's summary) | Audit three architectures; remove or gate one leg of each |
| G2 security-review rehearsal | The seven artifacts; hidden question bank; "I don't know" scores higher than a fabricated answer | Two mock panels with different compositions **[Repo: Assessment Pack §4]** |
| Wheel of Misfortune #1 | Primary/secondary on-call, a game master, a facilitated blameless debrief | Faults `GAMEDAY`, `APP-RACE`, `NET-MTU`; the debrief is facilitated, not left to the student **[Sourced: R3 §1.6, §1.9; Etsy debrief guide]** |

### W6.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W6-L1` | Break-it lab: schemas and malformed inputs | D4 | 2.5 | 10 adversarial inputs (empty, huge, multilingual, injected) against the extraction service | Validator catches 100% of schema violations; retry loop recovers >=70%; the rest route to a "needs human" bucket | AI-EVAL |
| `W6-L2` | Hand-written tool loop (no framework) | D4 | 3 | Tool loop with 3 tools against a mock order-management API | 20/20 scripted scenarios complete; invalid-argument error lets the model self-correct within 1 retry in >=80% of runs |  |
| `W6-L3` | Tool-description tuning | D4 | 1.5 | Ambiguous 6-tool set rewritten; 30-task run before/after | Wrong-tool rate drops >=50%; tokens-per-task does not rise >20% | AI-EVAL |
| `W6-L4` | A safe write tool | D4, D3 | 1 | Refund/update tool with idempotency key, dry-run and per-call authorisation | Replayed call causes exactly one side effect; unauthorised user context rejected in code (not by the prompt) |  |
| `W6-L5` | Error-analysis sprint | D4 | 3 | 60 traces from a provided support bot, open-coded into a taxonomy | >=5 named failure modes with counts; top-2 modes account for >=50% of failures; each has an example trace and a proposed fix | AI-EVAL; FAULT: RAG-FAIL (taxonomy seeds) |
| `W6-L6` | Assertions first: 20 cases for the Week-1 service | D4 | 1.5 | 20 deterministic checks mapped to failure modes, run in CI | Runs <60 s; each case maps to a named failure mode; two cases fail on a deliberately broken prompt | AI-EVAL |
| `W6-L7` | Lethal-trifecta audit and injection basics | D3, D4 | 3.5 | Audit of 3 provided agent architectures + one live injection demo | Correctly identifies which legs (private data, untrusted content, external communication) are present; redesign removes or gates one leg each; instructor rubric >=80% | AI-SEC |
| `W6-L9` | Security-review rehearsal (G2 mock) | D3, D6 | 5 | All 7 G2 artifacts assembled for the Kestrel stack + two mock panels with hidden questions | All 7 artifacts valid (see G2 section); >=8 of 12 mock questions answered with evidence or an honest "I don't know, I will find out by Thursday"; zero fabricated answers |  |
| `W6-L10` | Wheel of Misfortune #1 (blameless incident drill) | D2, D5 | 2 | Role-played incident (primary/secondary on-call, game master) with facilitated debrief | Timeline and 3 follow-up actions written; no blame language in the postmortem; stall points logged | FAULT: GAMEDAY, APP-RACE, NET-MTU |
| `W6-L8` | Customer Lab 6: security-review conduct | D6 | 2 | Role-play with the Linden CISO delegate: explain a block in plain language; propose a compliant path | R7 >=3: data classes and flows identified unprompted; block explained plainly; compliant alternative proposed; "I don't know" used rather than a bluff | CUSTOMER (R7) |

### W6.5 Customer thread and project milestone

**Customer Lab 6 (Wednesday, 1.5 h, Linden CISO delegate):** security-review conduct. The learner must (1) identify data classes and flows unprompted, (2) explain a block ("we cannot allow egress") in plain language, (3) propose a compliant alternative, and (4) say "I don't know, I will find out and come back by Thursday" rather than bluff. **R7** applies. Retry on Thursday (0.5 h).

This lab is deliberately placed before G2 so the *conduct* is practised before the *artifacts* are judged. G2 also scores Communication and Judgment on the craft rubric.

### W6.6 Resources

- Anthropic, *Writing tools for agents* https://www.anthropic.com/engineering/writing-tools-for-agents **[Sourced: R5 T4, V]**; *Building effective agents* https://www.anthropic.com/engineering/building-effective-agents **[Sourced: R5 §1, V]**
- Hamel Husain, *Your AI product needs evals* https://hamel.dev/blog/posts/evals/ **[Sourced: R5 T6, V]**; Anthropic, *Demystifying evals for AI agents* https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents **[Sourced: R5 T6, V]**
- Simon Willison, *The lethal trifecta* https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/ and *New prompt injection papers* https://simonwillison.net/2025/Nov/2/new-prompt-injection-papers/ **[Sourced: R5 T17, V]**
- OWASP Top 10 for LLM Applications (2025) https://genai.owasp.org/llm-top-10/ and LLM01 https://genai.owasp.org/llmrisk/llm01-prompt-injection/ **[Sourced: R5, V]**
- Google SRE Book ch. 28, Wheel of Misfortune https://sre.google/sre-book/accelerating-sre-on-call/ ; scenario repo https://github.com/dastergon/wheel-of-misfortune ; Etsy debrief facilitation guide https://codeascraft.com/2016/11/17/debriefing-facilitation-guide/ **[Sourced: R3 §1.6, §1.9]**

### W6.7 Stall points and instructor notes

**Likely stall points:**

1. Open/axial coding feels subjective: use two learners coding the same 10 traces and compare.
2. Tool-loop error handling (what to return when arguments are wrong).
3. G2 artifact #2: the SBOM must match the *deployed* image digest; automatic rejection otherwise.
4. G2 artifact #6: mapping at least 15 controls to SOC 2 / ISO 27001; give a template.
5. Fabrication under pressure in mock panels: panelists probe until the edge of the learner's knowledge, on purpose.

**Instructor notes**

- **G2 is Day 30.** Artifacts freeze Thursday morning (24 hours before), automated checks run; rejected artifacts are listed but do not block the defence **[Repo: Assessment Pack §4]**.
- Two independent assessors per defence; calibrate on one recorded mock before Friday (delta > 1.0 forces calibration) **[Repo: Pack §9]**.
- In gate weeks the weekly retrieval quiz moves to Thursday.
- The midpoint re-score (Friday, 1 h) compares self-rating with assessor rating on all six domains; any domain still at L1 enters a targeted remediation plan.
- The `W6-L7` lab is the first of three places where AI security recurs (Weeks 6, 8, 10).

### W6.8 Exit checklist

- [ ] Tool loop passes 20/20 scenarios; wrong-tool rate down >= 50% after description tuning
- [ ] Error taxonomy with >= 5 failure modes and counts; 20 assertions mapped to them
- [ ] Three trifecta redesigns reviewed >= 80%
- [ ] All seven G2 artifacts valid; zero critical CVEs unexplained; no secret resolvable from the repo
- [ ] G2 defence done; craft dimensions Security posture, Communication, Judgment scored by two assessors
- [ ] Midpoint re-score and ILP updated; remediation booked for any gap
- [ ] First Wheel of Misfortune debrief completed with 3 follow-up actions

### W6.9 Cut or reduced compared with the 24-week plan

The 24-week plan places G2 at Day 50 and adds a Day-60 consolidation review; AI security begins later and in more depth (T17 14 h vs 8 h). Here the G2 defence and the first AI security lab share a week; the 24-week plan keeps them in different weeks **[Sourced: foundation §6.2, §7.3]**.

---

## Week 7: RAG on the Linden corpus; golden sets and tracing

*Days 31-35 · Phase C AI build · Gate: none · Project: P5-M1 (carried system begins)*

### W7.1 Objectives

By Friday 17:45 a learner can:

- Build an end-to-end RAG pipeline (parse, clean, chunk with metadata, embed, retrieve, rerank, answer) and **evaluate retrieval separately from generation** (recall@k, MRR) before judging answers.
- Compare dense, BM25, hybrid (reciprocal rank fusion), hybrid + reranker and contextual chunks on their own data, and recommend a configuration from numbers.
- Parse messy documents (tables, HTML, a messy DOCX export, a scanned PDF with OCR) and catalogue parse failures.
- Enforce per-user access control **in the retrieval query**, not in the prompt, and prove it with an adversarial set.
- Produce grounded answers with verifiable citations and abstain when the corpus has no answer; decide when to skip RAG (stuff the prompt plus caching).
- Instrument the app with traces (prompt version, tokens, cost, latency) and find a real bug from a trace.
- Build a 40-case golden set and a **CI regression gate** that fails on a deliberately injected prompt regression.
- Start the **carried system**: a Linden claims assistant (P5-M1).

**This is the heaviest AI week (24 h AI Core + 4 h AI Ops).** It is the first place the foundation's 40%-stall rule is likely to trigger (risk 1).

### W7.2 Hours and day-by-day schedule

**Hours this week:** AIC 24 · AIO 4 · CUS 3 · PRJ 9 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D31) | 09:00-11:00 | 2 | AIC | INS | RAG end to end: ingest, chunk, embed, retrieve, rerank, answer; metrics for retrieval vs generation |
|  | 11:00-12:30 | 1.5 | AIC | LAB | Baseline RAG over a 200-document corpus (part 1) `W7-L1` |
|  | 13:15-15:15 | 2 | AIC | LAB | Baseline RAG over a 200-document corpus (part 2) `W7-L1` |
|  | 15:15-17:45 | 2.5 | PRJ | PRJ | P5-M1: Linden brief, hypotheses on "good", carried-system repo and environment `P5-M1` |
| Tue (D32) | 09:00-10:00 | 1 | AIC | INS | Hybrid search, reciprocal rank fusion, rerankers, contextual retrieval (vendor-reported numbers, test on your data) |
|  | 10:00-12:00 | 2 | AIC | LAB | Parsing messy documents (tables, HTML, DOCX, scans) `W7-L2` |
|  | 12:00-12:30 | 0.5 | AIC | LAB | Retrieval ablation (setup) `W7-L3` |
|  | 13:15-15:15 | 2 | AIC | LAB | Retrieval ablation `W7-L3` |
|  | 15:15-17:45 | 2.5 | PRJ | PRJ | P5-M1: ingestion pipeline on the Linden corpus subset (carried system v0) `P5-M1` |
| Wed (D33) | 09:00-10:30 | 1.5 | AIC | LAB | Retrieval ablation (results table) `W7-L3` |
|  | 10:30-12:30 | 2 | AIC | LAB | Access-controlled RAG `W7-L4` |
|  | 13:15-14:15 | 1 | AIC | LAB | Access-controlled RAG (adversarial set) `W7-L4` |
|  | 14:15-15:15 | 1 | AIO | INS | LLM observability: traces, spans, versions; OTel GenAI conventions are still experimental; content capture is opt-in |
|  | 15:15-17:45 | 2.5 | AIO | LAB | Tracing the RAG app (Langfuse or Phoenix) `W7-L5` |
| Thu (D34) | 09:00-11:30 | 2.5 | AIC | LAB | Grounded answers: citations, abstention, stuff-vs-retrieve `W7-L6` |
|  | 11:30-12:30 | 1 | AIC | INS | Golden sets, assertions then judges, CI regression gates, pass@k vs pass^k |
|  | 13:15-16:15 | 3 | AIC | LAB | Golden set and CI regression gate (part 1) `W7-L7` |
|  | 16:15-16:45 | 0.5 | AIO | LAB | Tracing the RAG app: finding a bug from traces `W7-L5` |
|  | 16:45-17:45 | 1 | PRJ | PRJ | P5-M1: wire tracing and the dev-set harness into the carried system `P5-M1` |
| Fri (D35) | 09:00-11:00 | 2 | AIC | LAB | Golden set and CI regression gate (part 2) `W7-L7` |
|  | 11:00-12:30 | 1.5 | PRJ | PRJ | P5-M1: baseline RAG v0 numbers; prepare the demo and limitations page `P5-M1` |
|  | 13:15-16:15 | 3 | CUS | CUS | Customer Lab 7 (Linden senior adjuster, VP Claims Ops): JTBD timeline interview; define "good" `W7-L8` |
|  | 16:15-17:45 | 1.5 | PRJ | PRJ | P5-M1: trio demo to the VP persona; Friday retro + pulse survey (recorded against Projects, Slack is exhausted) `P5-M1` |

### W7.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| RAG end to end | Ingest, chunk, embed, retrieve, rerank, answer; retrieval vs generation metrics | Baseline RAG on a 200-document starter corpus (PDFs, HTML, messy Word export) with 40+ hand-written questions and gold passages **[Sourced: R5 T5 lab 1]** |
| Hybrid search, reranking, contextual retrieval | BM25 as a strong baseline; reciprocal rank fusion; cross-encoder rerankers; Anthropic's contextual retrieval (top-20 failure 5.7% -> 3.7% -> 2.9% -> 1.9% with embeddings, BM25 and reranking; vendor-reported numbers on their datasets) | Ablation table on the learner's own data; hybrid + rerank must be justified or rejected by numbers **[Sourced: R5 T5, V]**. Vector DB benchmarks conflict across sources: test on your own data; `pgvector` is the default |
| Parsing messy documents | PDF tables, HTML, DOCX, OCR | Four hard document types; parse failures catalogued with causes (garbage in, garbage out) |
| Access-controlled RAG | Metadata/ACL filtering in the query; OWASP LLM08 (vector and embedding weaknesses) | 50 adversarial queries including "ignore filters" prompts; 0 leaks; fault `RAG-ACL` |
| Grounded answers and abstention | Citations that resolve; "I don't know"; long context vs RAG (for corpora under ~200k tokens consider stuffing the prompt with caching) | Decision table for three corpus sizes **[Sourced: R5 T5, V]** |
| LLM observability | Traces and spans; OpenTelemetry GenAI conventions are still experimental; content capture is opt-in (privacy) | Langfuse (OTel-native in v4) or Arize Phoenix, one per cohort **[Sourced: R5 flags, S]** |
| Golden sets and CI gates | Assertions first, then one LLM judge criterion; 10 adversarial and 10 should-refuse cases; flake rate | GitHub Actions run on every prompt/model change; an injected regression must fail the build (`LLM-REGRESS`) **[Sourced: R5 T6 lab 2]** |

### W7.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W7-L1` | Baseline RAG over a 200-document corpus | D4 | 3.5 | Ingest -> chunk -> embed -> retrieve -> answer, with 40+ hand-written questions and gold passages | recall@5/@10 and answer correctness reported; citations resolve to the right chunk >=85% of the time | FAULT: RAG-FAIL (taxonomy) |
| `W7-L2` | Parsing messy documents (tables, HTML, DOCX, scans) | D4 | 2 | Parsing comparison on 4 hard document types incl. a scanned PDF (OCR) | >=90% of 20 target facts recoverable from parsed text; every parse failure catalogued with a cause | FAULT: RAG-FAIL (taxonomy) |
| `W7-L3` | Retrieval ablation | D4 | 4 | dense vs BM25 vs hybrid (RRF) vs hybrid+rerank vs contextual chunks; 3 chunk sizes | One table of recall@10, MRR, p95 latency, cost/query; one config recommended with the data; hybrid+rerank justified or rejected by numbers | AI-EVAL |
| `W7-L4` | Access-controlled RAG | D4, D3 | 3 | Department-tagged documents; per-user retrieval filter enforced in the retrieval query | 0 leaks across 50 adversarial queries (incl. "ignore filters" prompts); "not in corpus" queries answer "I don't know" >=90% | FAULT: RAG-ACL |
| `W7-L5` | Tracing the RAG app (Langfuse or Phoenix) | D5 | 3 | Every LLM/tool/retrieval call traced with prompt version, tokens, cost; dashboard | 100% of calls traced; dashboard shows p50/p95 latency and $/request; one real bug found from traces and documented | AI-EVAL |
| `W7-L6` | Grounded answers: citations, abstention, stuff-vs-retrieve | D4 | 2.5 | Answer synthesis with verifiable citations and abstention; decision table for corpus size | Every cited span verifiable; abstains on >=90% of 20 unanswerable questions; decision table for 3 corpus sizes (when to skip RAG) | AI-EVAL |
| `W7-L7` | Golden set and CI regression gate | D4 | 5 | 40-case golden set (10 adversarial, 10 should-refuse/escalate) with assertions + one LLM-judge criterion, run in GitHub Actions | A deliberately injected prompt regression fails the build; flake rate <5% across 3 runs on deterministic checks | AI-EVAL; FAULT: LLM-REGRESS |
| `W7-L8` | Customer Lab 7: JTBD interview and defining "good" | D6 | 3.5 | JTBD timeline interview with the senior adjuster; one-page definition of "good" agreed with the VP Claims Ops | R1 >=3 (reconstructed a real recent case; found the anxiety/habit forces); definition names metric, threshold and cost of a wrong answer | CUSTOMER (R1, R3) |

### W7.5 Customer thread and project milestone

**Customer Lab 7 (Friday, 3 h, Linden senior adjuster and VP Claims Operations):** a **Jobs-to-be-done timeline interview** ("tell me about the last time a claim answer was wrong"), then defining *good* with the client: a metric, a threshold and the cost of a wrong answer. The senior adjuster reveals the truth only to specific-past-event questions. The adversarial three-stakeholder panel (stage 2 of the simulated-client format) is introduced at the end. Output: a one-page definition of *good* agreed with the VP, used as the dev-set criteria in Week 8. Retry on Monday.

JTBD switch interviews come from a course-selling site with no independent validation; teach the timeline and the anxiety/habit forces, which map directly to adoption risk, and treat the method as a pilot hypothesis **[Sourced: R4 §2.2]**.

**Carried-system milestone P5-M1 (9 h):** discovery readout, repo and environment, ingestion pipeline on a Linden corpus subset, baseline RAG v0 with numbers, trio demo to the VP persona.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P5-M1` Linden claims assistant: discovery readout and baseline RAG v0 (the carried system begins) | Linden | 9 | Repo for the carried system; ingestion of a Linden corpus subset; baseline RAG v0 with numbers; trio demo to the VP Claims Ops persona | Baseline recall@5 and answer correctness reported on the 50-question dev set; every answer cites a chunk; limitations page started |

### W7.6 Resources

- Anthropic, *Contextual retrieval* https://www.anthropic.com/engineering/contextual-retrieval **[Sourced: R5 T5, V]**
- Hamel Husain and Shreya Shankar, evals FAQ (RAG evaluation; chunk size; error analysis) https://hamel.dev/blog/posts/evals-faq/ **[Sourced: R5 T6; headings only were readable]**
- Anthropic, *Demystifying evals for AI agents* (start with 20-50 tasks from real failures; capability vs regression suites) https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents **[Sourced: R5 T6, V]**
- Langfuse OpenTelemetry docs https://langfuse.com/docs/opentelemetry/introduction **[Sourced: R5 T13, S]**
- JTBD switch interview and timeline https://jobstobedone.org/switch-interview/ and https://jobstobedone.org/the-timeline/ **[Sourced: R4 §2.2]**

### W7.7 Stall points and instructor notes

**Likely stall points (watch the 40% rule):**

1. PDF table parsing: provide pre-parsed fallbacks after 40 minutes so retrieval work is not blocked.
2. Chunking and metadata design: learners over-tune chunk size; fix the evaluation first.
3. Reranker setup and API quotas.
4. Judging final answers before checking retrieval: enforce "retrieval first" in every review.
5. ACL leaks through caches or summaries: ask "where else did that document's text travel?"
6. Trace volume and PII in trace content: show how to turn content capture off.

**Instructor notes**

- The held-out 100-question golden set for G3 is built by a *different person* from anyone who tunes retrieval; learners only ever see a 50-question dev set **[Repo: Ops Guide §4]**.
- Slack is zero this week. Friday's retro is recorded against Projects. If more than 40% of the cohort stalls at the same lab, defer the lowest-value half of `W7-L3` to Week 10 slack (the nearest slack) and log it **[Judgment: foundation §12 risk 1]**.
- Corpus: build the main 5,000-document synthetic corpus (40% clean PDFs, 30% scanned PDFs, 20% spreadsheets, 10% inconsistent HTML/DOCX) at T-4 weeks; Week 7 uses a Linden subset.
- Keep model IDs in config; Anthropic caching docs list models up to the "5.x" family, and names change fast.

### W7.8 Exit checklist

- [ ] Baseline RAG reports recall@5/@10 and answer correctness; citations resolve >= 85%
- [ ] Ablation table delivered with a recommendation
- [ ] 0 ACL leaks on 50 adversarial queries; "not in corpus" abstention >= 90%
- [ ] 100% of calls traced; one bug found from traces
- [ ] Golden set (40 cases) gates CI; injected regression fails the build; flake < 5%
- [ ] Definition of "good" agreed with the VP persona (metric, threshold, cost of wrong)
- [ ] P5-M1 baseline RAG v0 demonstrated with numbers

### W7.9 Cut or reduced compared with the 24-week plan

The 24-week plan gives RAG 36 h inside its AI Core phase (Weeks 13-18 per foundation §7.6; parsing/OCR in depth, incremental re-indexing, multilingual, agentic retrieval) and evals 30 h; here RAG is 18 h and evals continue into Weeks 8-9 **[Sourced: foundation §7.3, R5 Option B]**. GraphRAG and agentic retrieval are dropped.

---

## Week 8: Agents, MCP and calibrated judges

*Days 36-40 · Phase C AI build · Gate: none · Project: P5-M2, P6-M1*

### W8.1 Objectives

By Friday 17:45 a learner can:

- Choose between a fixed workflow and an agent using a measured bake-off (success rate, steps, tokens, p95 latency) and justify "the chain wins" when it does.
- Build a **bounded agent**: budget caps, a human-approval gate that prompt text cannot bypass, and checkpoint/resume with no repeated side effects.
- Build an **MCP server** against the current spec revision, test it with MCP Inspector and a real client, add scoped-token authorisation with no token passthrough, and threat-model a third-party MCP server before installing it.
- Calibrate an **LLM judge** against human labels (TPR and TNR both >= 0.85 on a held-out set) and state its biases.
- Design a human-in-the-loop flow: risk-tiered approvals, review queues, and reviewer edits that become new golden cases.
- Raise the carried system to the agreed bar (P5-M2) and give it read-only MCP tools (P6-M1).
- Survive **Breakage 2** on the carried system (provider failure and context overflow).

### W8.2 Hours and day-by-day schedule

**Hours this week:** AIC 24 · AIO 4 · CUS 2.5 · PRJ 8.5 · SLK 1 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D36) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: JTBD interview re-run with feedback `W7-L8` |
|  | 09:30-11:30 | 2 | AIC | INS | Agents: workflows vs agents, the five patterns, simplest-solution-first, budgets and stop conditions |
|  | 11:30-12:30 | 1 | AIC | LAB | Workflow vs agent bake-off (part 1) `W8-L1` |
|  | 13:15-16:15 | 3 | AIC | LAB | Workflow vs agent bake-off (part 2) `W8-L1` |
|  | 16:15-17:45 | 1.5 | PRJ | PRJ | P5-M2: turn the "definition of good" into dev-set criteria; grow dev set to 50 `P5-M2` |
| Tue (D37) | 09:00-10:30 | 1.5 | AIC | INS | MCP architecture (spec revision 2026-07-28): host/client/server, stateless requests, tools/resources; older tutorials are out of date |
|  | 10:30-12:30 | 2 | AIC | LAB | Build an MCP server (part 1) `W8-L2` |
|  | 13:15-14:15 | 1 | AIC | LAB | Build an MCP server (part 2) `W8-L2` |
|  | 14:15-16:15 | 2 | AIC | LAB | MCP authorisation: scoped tokens, no passthrough `W8-L3` |
|  | 16:15-16:45 | 0.5 | PRJ | PRJ | P6-M1: design the read-only claims tools; mentor 1:1 held inside the project block (no slack this week) `P6-M1` |
|  | 16:45-17:15 | 0.5 | PRJ | PRJ | P5-M2: error analysis of the top-2 failure modes `P5-M2` |
|  | 17:15-17:45 | 0.5 | PRJ | PRJ | P6-M1: read-only tool contracts and tests `P6-M1` |
| Wed (D38) | 09:00-10:30 | 1.5 | AIC | LAB | Threat-model a third-party MCP server `W8-L4` |
|  | 10:30-11:30 | 1 | AIC | INS | LLM-as-judge: binary labels, TPR/TNR, known biases |
|  | 11:30-12:30 | 1 | AIC | LAB | Calibrating an LLM judge (labelling) `W8-L5` |
|  | 13:15-14:45 | 1.5 | CUS | CUS | Customer Lab 8 (Linden skeptical technical lead): demo, hard "limits" question `W8-L6` |
|  | 14:45-17:45 | 3 | PRJ | PRJ | P5-M2: improve retrieval/prompt against the dev set; error analysis and fixes `P5-M2` |
| Thu (D39) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: demo re-run with feedback applied `W8-L6` |
|  | 09:30-12:30 | 3 | AIC | LAB | Calibrating an LLM judge (tuning to TPR/TNR >=0.85) `W8-L5` |
|  | 13:15-14:15 | 1 | AIC | LAB | Calibrating an LLM judge (held-out check) `W8-L5` |
|  | 14:15-16:15 | 2 | AIC | LAB | Bounded agent with approvals and crash-resume (part 1) `W8-L7` |
|  | 16:15-17:15 | 1 | AIO | INS | Human-in-the-loop design: autonomy levels, review queues, feedback as labels |
|  | 17:15-17:45 | 0.5 | AIO | LAB | Human-in-the-loop flow (setup) `W8-L8` |
| Fri (D40) | 09:00-11:00 | 2 | AIC | LAB | Bounded agent with approvals and crash-resume (part 2) `W8-L7` |
|  | 11:00-12:30 | 1.5 | AIO | LAB | Human-in-the-loop flow with a feedback flywheel `W8-L8` |
|  | 13:15-15:45 | 2.5 | PRJ | PRJ | P6-M1 + Breakage 2 (guide on the side) on the carried system: LLM-PROVIDER and LLM-CTX `W8-L9` `P6-M1` |
|  | 15:45-16:45 | 1 | AIO | LAB | Human-in-the-loop flow: edits to golden cases `W8-L8` |
|  | 16:45-17:45 | 1 | SLK | SLK | G2 parallel-task retake panels (45 min, only learners who need them); everyone else: mentor 1:1 and Friday retro + pulse survey |

### W8.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| Workflows vs agents | Anthropic's five patterns (prompt chaining, routing, parallelisation, orchestrator-workers, evaluator-optimiser); "start with the simplest solution"; budgets and stop conditions | Same task built as a fixed chain and a ReAct-style agent; 50-task eval; the expected answer may be "the chain wins" **[Sourced: R5 T7, V]** |
| Bounded agents | Step/cost caps, human approval, checkpointing, resume | Kill the process mid-run; resume must not repeat a side effect; the approval gate must survive adversarial prompt text |
| MCP | Host/client/server; tools/resources; stdio and Streamable HTTP; spec revision `2026-07-28` is stateless; roots, sampling, protocol logging and dynamic client registration are deprecated; Tasks and MCP Apps are extensions | **Pre-2026 tutorials (session IDs, `initialize` handshake, sampling) are out of date**; check the revision a library implements **[Sourced: R5 T8, V]** |
| MCP security | Token passthrough is forbidden; audience validation; scope minimisation; confused deputy; SSRF in OAuth discovery; local-server compromise | Six negative tests (wrong audience, expired, over-scoped) must return 401/403; fault `MCP-TOKEN` |
| LLM-as-judge | Binary pass/fail over Likert; validate the judge against humans; raw agreement misleads on imbalanced classes; position and length bias | Two learners label 100 outputs; tune the judge to TPR/TNR >= 0.85 on a held-out 50 **[Sourced: R5 T6, V]** |
| Human-in-the-loop design | Suggest -> approve -> auto with audit; reviewer decision time; capture edits and reasons as labels; defensive UX | Review UI provided; 10 edits become new golden cases (regression suite grows) **[Sourced: R5 T20]** |
| Carried system v1 | Apply the "good" definition to dev-set criteria; error analysis on the top-2 failure modes; read-only tools via MCP | P5-M2 then P6-M1; tracing and the CI gate stay on |
| Breakage 2 on the carried system | `LLM-PROVIDER` (429s/outage) and `LLM-CTX` (overflow/truncation) injected; detect from traces | Guide-on-the-side; blameless postmortem |

### W8.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W8-L1` | Workflow vs agent bake-off | D4 | 4 | Triage + draft-reply task built as (a) fixed chain and (b) ReAct-style agent; 50-task eval | Table of success rate, mean steps, tokens, p95 latency; written recommendation (the expected answer may be "the chain wins") | AI-EVAL |
| `W8-L7` | Bounded agent with approvals and crash-resume | D4, D3 | 4 | Agent with budget caps, a human-approval gate and checkpoint/resume | Budget (10 tool calls, $0.50/task) never exceeded across 30 runs; crash-resume repeats no side effects; approval gate cannot be bypassed by prompt text |  |
| `W8-L2` | Build an MCP server | D4 | 3 | MCP server wrapping a mock internal API: 3-5 tools + 1 resource | Works in MCP Inspector and one real client; <10% wrong-tool on 20 tasks; stdout never polluted (logs to stderr); built against the current spec revision |  |
| `W8-L3` | MCP authorisation: scoped tokens, no passthrough | D3, D4 | 2 | Remote (Streamable HTTP) server with scoped-token auth | 6 negative tests pass (wrong audience, expired, over-scoped -> 401/403); no token passthrough downstream; minimal scopes | FAULT: MCP-TOKEN |
| `W8-L4` | Threat-model a third-party MCP server | D3 | 1.5 | One-page pre-install review + sandboxed run | Names the command executed, filesystem/network reach and scopes; go/no-go decision; run in a container with restricted mounts | AI-SEC |
| `W8-L5` | Calibrating an LLM judge | D4 | 5 | 100 outputs hand-labelled binary by two learners; judge prompt tuned | Judge TPR and TNR both >=0.85 vs human consensus on a held-out 50; inter-rater agreement reported; note on position/length/self-preference bias | AI-EVAL |
| `W8-L8` | Human-in-the-loop flow with a feedback flywheel | D5, D4 | 3 | Risk-tiered approvals (auto / sampled / approve) and edit capture on a provided review UI | 0 high-risk actions executed without approval across 50 runs; median reviewer decision <30 s; all decisions logged; 10 reviewer edits converted into new golden cases |  |
| `W8-L9` | Breakage 2 on the carried system: provider failure and context overflow | D5, D4 | 2.5 | Two AI faults injected into the carried system; detected and mitigated | Both detected from traces (not from users); failover/truncation strategy implemented; blameless postmortem; stall points logged | FAULT: LLM-PROVIDER, LLM-CTX |
| `W8-L6` | Customer Lab 8: demo craft and honest capability framing | D6 | 2 | 5-min demo of the carried system to the Linden skeptical technical lead + "what it cannot do" page | R4 >=3: tailored to audience data; narrative not feature tour; handled a hard limits question honestly; evidence (a number) not vibes | CUSTOMER (R4) |

### W8.5 Customer thread and project milestone

**Customer Lab 8 (Wednesday, 1.5 h, Linden skeptical technical lead):** demo craft and **honest capability framing**. A 5-minute demo of the carried system, then a hard limits question ("what does it get wrong?"). Learners write a one-page *what it cannot do* sheet. **R4:** tailored to the audience's data; a narrative (problem -> result -> how), not a feature tour; handled interruption and a hard question honestly; evidence (a number) rather than vibes; a clear next step **[Sourced: R4 §3.3]**. Retry on Thursday (0.5 h).

The research flags the failure mode this lab counters: demos that overstate capability when an evaluator probes limits **[Sourced: foundation §2.3]**.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P5-M2` Raise the carried system to the agreed bar (eval-gated) | Linden | 5 | Dev set of 50 questions, error-analysis report, calibrated judge, regression gate in CI | Top-2 failure modes fixed and verified on the dev set; judge TPR/TNR >=0.85; deliberate regression fails the build |
| `P6-M1` Carried system gains read-only tools via an MCP server | Linden | 3.5 | MCP server exposing 3-5 read-only claims tools; agent loop with step and cost caps; Breakage 2 survived | Agent completes 20 scripted tasks within budget; wrong-tool rate <10%; LLM-PROVIDER and LLM-CTX faults detected from traces |

### W8.6 Resources

- Anthropic, *Building effective agents* https://www.anthropic.com/engineering/building-effective-agents and *How we built our multi-agent research system* (agents ~4x and multi-agent ~15x chat tokens; token usage explained ~80% of BrowseComp variance) https://www.anthropic.com/engineering/multi-agent-research-system **[Sourced: R5 T7, V]**
- MCP: introduction https://modelcontextprotocol.io/docs/getting-started/intro ; architecture (2026-07-28) https://modelcontextprotocol.io/docs/2026-07-28/learn/architecture.md ; security best practices https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/security_best_practices.md **[Sourced: R5 T8, V]**. Re-verify the revision number at T-4 weeks
- Hamel Husain, evals https://hamel.dev/blog/posts/evals/ (binary labels; validate the judge) **[Sourced: R5 T6, V]**
- Applied LLMs on feedback and defensive UX https://applied-llms.org/ **[Sourced: R5 T20, V]**
- Anthropic Academy "Introduction to Model Context Protocol" course (module list came from a mirror; the Skilljar page returned 403) https://anthropic.skilljar.com/introduction-to-model-context-protocol **[Sourced: R5 T8, S]**

### W8.7 Stall points and instructor notes

**Likely stall points:**

1. Agent loops that never terminate: demand the step/cost cap *before* the first run.
2. MCP stdout pollution (logs on stdout break the protocol); log to stderr.
3. MCP OAuth negative tests: learners return 200 for an expired token because a client library masks the error.
4. Two-rater labelling disagreements: expected; report inter-rater agreement, do not hide it.
5. Judge TPR/TNR stuck at 0.75: the likely cause is an under-specified criterion, not a weak model; coach the rubric text.
6. Breakage 2: trace volume; point learners at the `prompt_version` and `model_config_id` fields.

**Instructor notes**

- Run every AI lab against the hosted default and one OpenAI-compatible endpoint (principle P16).
- The Friday game day is *guide on the side*: ask questions, do not drive. A role-played customer asks for status once during the drill.
- The OpenAI Assistants API is scheduled for shutdown (26 Aug 2026, search-snippet level): do not teach it **[Sourced: R5 flags, S]**. Agent SDK status claims (Microsoft Agent Framework 1.0, Google ADK GA, OpenAI Agents SDK sandbox) rest on single secondary sources; teach the loop from scratch and *read* one vendor SDK.
- **Friday's 1 h of slack is the G2 retake window** (parallel questionnaire, different panel composition). Phase C has only 1 h of slack in the foundation budget, so Weeks 7-9 cannot host evening-free remediation beyond this; see the gate section.
- Multi-agent orchestrator-workers is a Week 9 *reading and cost-multiple discussion* in the 12-week program; the lab exists only in the 24-week plan.

### W8.8 Exit checklist

- [ ] Bake-off table + recommendation
- [ ] Bounded agent: budget never exceeded in 30 runs; crash-resume repeats no side effect
- [ ] MCP server works in Inspector + one real client; 6 negative auth tests pass
- [ ] Judge TPR and TNR both >= 0.85 on the held-out 50
- [ ] HITL: 0 high-risk actions without approval in 50 runs; 10 edits -> golden cases
- [ ] Carried system: top-2 failure modes fixed and verified on the dev set
- [ ] Breakage 2 detected from traces; postmortem written
- [ ] Demo scored R4 >= 3 incl. a "what it cannot do" page

### W8.9 Cut or reduced compared with the 24-week plan

The 24-week plan runs agents/MCP inside its AI Core and AI Ops phases (Weeks 13-21 per foundation §7.6) with a multi-agent orchestrator lab (T7 deep, with a pre-declared margin and reported cost multiple), a full MCP authorisation lab and a trajectory-eval lab; here agents are 10 h and MCP is 8 h, multi-agent is reading only **[Sourced: foundation §7.3, §7.5]**.

---

## Week 9: Reliability, context, open models and guardrails (G3)

*Days 41-45 · Phase C AI build · Gate: G3 (Day 45) · Project: P6-M2*

### W9.1 Objectives

By Friday 17:45 a learner can:

- Measure an agent's reliability with outcome and trajectory evals (pass@1 vs pass^k), report cost per task, and fix failure modes found in traces.
- Budget a context window, apply compaction, notes and just-in-time retrieval, and lay out prompts for provider caching (>= 80% cache-hit ratio on a 100-request replay).
- Write a decision memo choosing prompting, RAG or fine-tuning for a customer scenario and name the measurement that would change the answer (no training run in this plan).
- Build a reliability harness for LLM calls (backoff with jitter, timeouts, circuit breaker, fallback) that hides <= 20% injected errors from users.
- Compare a hosted frontier model with a local open model (~7-8B, quantised) on the same eval, and switch providers by changing only base URL and model name.
- Build a layered guard stack and report attack success (< 10%) and benign over-block (< 5%).
- Finish the carried system's write actions with approvals and a safety review (P6-M2).
- **Pass G3:** deliver the AI system against a business metric, with evals in CI, in front of a hostile technical evaluator.

### W9.2 Hours and day-by-day schedule

**Hours this week:** AIC 15 · AIO 10 · CUS 2.5 · PRJ 6.5 · ASM 6 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D41) | 09:00-10:00 | 1 | AIC | INS | Reliability of agents: pass@k vs pass^k; multi-agent patterns (reading) and the cost multiple |
|  | 10:00-12:30 | 2.5 | AIC | LAB | Outcome and trajectory evals for the carried-system agent (part 1) `W9-L1` |
|  | 13:15-15:45 | 2.5 | AIC | LAB | Outcome and trajectory evals for the carried-system agent (part 2) `W9-L1` |
|  | 15:45-16:45 | 1 | AIC | INS | Context engineering: budgets, compaction, notes, just-in-time retrieval |
|  | 16:45-17:45 | 1 | AIC | LAB | Context-budget audit (part 1) `W9-L2` |
| Tue (D42) | 09:00-10:00 | 1 | AIC | LAB | Context-budget audit (part 2) `W9-L2` |
|  | 10:00-12:00 | 2 | AIC | LAB | Cache-friendly prompt layout `W9-L3` |
|  | 12:00-12:30 | 0.5 | AIC | INS | Fine-tune vs RAG vs prompting: the layer model (part 1) |
|  | 13:15-13:45 | 0.5 | AIC | INS | Fine-tune vs RAG vs prompting: when each fails (part 2) |
|  | 13:45-16:45 | 3 | AIC | LAB | Fine-tune vs RAG vs prompting: decision memos `W9-L4` |
|  | 16:45-17:45 | 1 | PRJ | PRJ | P6-M2: write tool + approval gate design for the carried system `P6-M2` |
| Wed (D43) | 09:00-09:30 | 0.5 | AIO | INS | Reliability engineering for LLM calls: backoff with jitter, timeouts, breakers, fallbacks |
|  | 09:30-11:00 | 1.5 | AIO | LAB | Reliability harness: 429s, timeouts, malformed replies `W9-L5` |
|  | 11:00-12:00 | 1 | AIO | INS | Open-weight and local models: sizing (VRAM + KV cache), quantisation, serving; licence terms need legal review |
|  | 12:00-12:30 | 0.5 | AIO | LAB | Hosted vs local open model on the same eval (setup) `W9-L6` |
|  | 13:15-15:15 | 2 | CUS | CUS | Customer Lab 9 (Linden skeptical technical lead, VP): G3 demo rehearsal, exec brief, bad-news segment `W9-L7` |
|  | 15:15-17:45 | 2.5 | PRJ | PRJ | P6-M2: write tool, approvals, trifecta audit of own agent `P6-M2` |
| Thu (D44) | 09:00-10:30 | 1.5 | ASM | ASM | G3 readiness: assessors cold-run the held-out golden-set harness against each trio's deployed system (learners fix packaging only) |
|  | 10:30-12:30 | 2 | AIO | LAB | Hosted vs local open model on the same eval `W9-L6` |
|  | 13:15-13:45 | 0.5 | AIO | LAB | Hosted vs local open model: write-up and licence check `W9-L6` |
|  | 13:45-14:45 | 1 | AIO | INS | Guardrails vs evaluators; layered defences; output is untrusted input |
|  | 14:45-15:15 | 0.5 | CUS | CUS | Retry: G3 demo segment re-run `W9-L7` |
|  | 15:15-17:45 | 2.5 | PRJ | PRJ | P6-M2: safety review pack, user-training session outline, limitations page `P6-M2` |
| Fri (D45) | 09:00-12:30 | 3.5 | ASM | ASM | G3 AI build: 30-min trio demo with a hostile technical evaluator, individual 15-min technical examinations, peer scoring of two other trios |
|  | 13:15-14:15 | 1 | ASM | ASM | G3 panel feedback and metric read-out |
|  | 14:15-17:15 | 3 | AIO | LAB | Layered guard stack `W9-L8` |
|  | 17:15-17:45 | 0.5 | PRJ | PRJ | Retro (against Projects) and carry-over list for Weeks 10-11 `P6-M2` |

### W9.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| Agent reliability | pass@1 vs pass^k (customer-facing agents should be judged on consistency); trajectory vs outcome; multi-agent patterns as **reading** with the cost multiple (agents ~4x, multi-agent ~15x chat tokens) | 30-run evaluation of the carried-system agent; traces drive fixes **[Sourced: R5 T7, V]** |
| Context engineering | Context rot; attention budget; compaction; structured notes; sub-agents return condensed summaries; just-in-time retrieval | Instrument tokens by category over a 30-turn run; cut tokens/task >= 30% with no eval drop **[Sourced: R5 T9, V]** |
| Prompt caching | Prefix order tools -> system -> messages; changes to tool definitions invalidate the cache; per-request timestamps before the breakpoint kill hit rate; TTL and minimum cacheable length vary by model | 100-request replay; read hits from usage fields; model IDs stay in config; check the provider's current rules **[Sourced: R5 T9, V]** |
| Fine-tune vs RAG vs prompting | Layer model: prompting changes the input, RAG changes available information, fine-tuning changes weights; compare on the same eval set | Five scenario memos; instructor rubric >= 80%; hands-on LoRA is a 24-week lab **[Sourced: R5 T10]**. Cost-crossover blog numbers are one author's estimate; do not teach them as fact |
| LLM reliability engineering | Retries with jitter, timeouts, circuit breakers, fallbacks (track the fallback rate, since fallbacks multiply cost/latency) | Fake provider injecting 429s, timeouts, malformed replies; fault `LLM-PROVIDER` variant **[Sourced: R5 T13]** |
| Open and local models | VRAM ~ parameters x bytes/parameter + KV cache; Ollama for dev, llama.cpp for edge, vLLM for concurrent serving; licences differ and need legal review | Same 100-prompt eval hosted vs local; table of quality, latency, cost per 1k requests; vLLM load test is an instructor demo here **[Sourced: R5 T11, S]** |
| Guardrails vs evaluators | Inline guards (block/repair) vs sampled evaluators; output is untrusted input; detectors are not a boundary | Layered stack on the support bot with a 100-case red-team set (50 benign, 50 attack) **[Sourced: R5 T16]** |
| Carried system: write actions and safety review | Approval gate, trifecta audit of one's own agent, user-training outline | P6-M2 |

### W9.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W9-L1` | Outcome and trajectory evals for the carried-system agent | D4, D5 | 5 | 30-run reliability evaluation of the agent with pass@1 vs pass^k, cost per task and an error analysis | Report pass@1 and pass^k; >=2 failure modes found from traces and fixed; fix verified on the dev set; cost per task reported | AI-EVAL |
| `W9-L2` | Context-budget audit | D4 | 2 | Token-by-category instrumentation of a 30-turn agent run | A change that cuts tokens/task >=30% with no drop on the eval set, shown from traces | AI-EVAL |
| `W9-L3` | Cache-friendly prompt layout | D4, D5 | 2 | Prompt layout restructured for provider prompt caching (or the provider's equivalent) | Cache-hit ratio >=80% on a 100-request replay (from usage fields) with a before/after cost number; model IDs stay in config | AI-EVAL |
| `W9-L4` | Fine-tune vs RAG vs prompting: decision memos | D4 | 3 | 5 customer scenarios -> recommended approach, eval plan and cost sketch | Instructor rubric >=80%; each memo names the failing layer and the measurement that would change the recommendation (no training run in the 12-week program) |  |
| `W9-L5` | Reliability harness: 429s, timeouts, malformed replies | D5 | 1.5 | Fake provider injecting failures; retries, timeouts, circuit breaker, fallback | No user-visible failure at <=20% injected errors; backoff has jitter (from timestamps); breaker opens and recovers; fallback rate reported | FAULT: LLM-PROVIDER (variant) |
| `W9-L6` | Hosted vs local open model on the same eval | D5, D4 | 3 | Same 100-prompt eval on a hosted frontier model and a local ~7-8B quantised model | Table of quality, latency, cost per 1k requests; states which tasks the small model passes; app switches provider by changing only base URL + model name; licence check noted | AI-EVAL |
| `W9-L8` | Layered guard stack | D3, D5 | 3 | Input filter, schema check, PII scrub and action allow-list on the support bot; 100-case red-team set | End-to-end attack success <10% AND benign over-block <5%; per-layer block rate and p95 added latency reported | AI-SEC |
| `W9-L7` | Customer Lab 9: hostile technical evaluator and executive brief (G3 rehearsal) | D6 | 2.5 | G3 demo rehearsal + answer-first executive brief + a bad-news segment on a missed metric | R4 >=3 (limits question handled honestly); R5 >=3 (bottom line first); R6 >=3 (missed metric reported early with options) | CUSTOMER (R4, R5, R6) |

### W9.5 Customer thread and project milestone

**Customer Lab 9 (Wednesday, 2 h) is the G3 rehearsal:** a demo to a *hostile technical evaluator* (the Linden skeptical lead probes limits), an answer-first executive brief for the VP, and a *bad-news segment* about a missed metric. **R4, R5 and R6 >= 3.** Retry on Thursday (0.5 h) so the delta is graded before the gate.

**G3 is a customer-facing event as much as a technical one.** The disqualifying conditions from the repo apply: an engineer who hits the metric but *cannot explain why the architecture was chosen* does not pass, and a golden set built from the documents used to tune retrieval is void **[Repo: Assessment Pack §5]**.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P6-M2` Agent write actions with human approval; safety review (G3 build) | Linden | 6.5 | Write tool behind an approval gate; trifecta audit of the learner's own agent; user-training session outline | Zero high-risk actions without approval across 50 runs; audit shows which trifecta leg was removed or gated; training outline reviewed by the persona |

### W9.6 Resources

- Anthropic, *Effective context engineering for AI agents* https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents **[Sourced: R5 T9, V]**; prompt caching docs https://platform.claude.com/docs/en/build-with-claude/prompt-caching **[Sourced: R5 T9, V; multipliers and model lists change]**
- LiteLLM reliability and routing docs https://docs.litellm.ai/docs/router/learn/reliability **[Sourced: R5 T13, S]**
- Red Hat, llama.cpp vs vLLM https://developers.redhat.com/articles/2026/06/15/llamacpp-vs-vllm-choosing-right-local-llm-inference-engine **[Sourced: R5 T11, S; benchmark numbers vary widely by version and hardware, measure yourself]**
- OWASP LLM Top 10 (2025) LLM05 Improper Output Handling and LLM06 Excessive Agency https://genai.owasp.org/llm-top-10/ **[Sourced: R5 T16, V]**
- Hugging Face LLM Course, fine-tuning chapters (for the decision memos) https://huggingface.co/learn/llm-course/chapter1/1 **[Sourced: R5 T10, V]**

### W9.7 Stall points and instructor notes

**Likely stall points (second 40%-rule watch):**

1. pass^k vs pass@k confusion: draw the two curves.
2. Cache-hit ratio stuck low because a timestamp or tool definition changes the prefix.
3. Local model memory: laptops have 16 GB; use a small quantised model and the shared GPU pool only for the sizing demo.
4. Guard over-blocking: learners tune toward zero attacks and block benign traffic; the pass criterion is *both* rates.
5. G3 packaging problems (a missing dependency in the clean environment); the Thursday cold run exists to catch this.

**Instructor notes**

- **G3 is Day 45.** Thursday morning assessors cold-run the held-out harness against each trio's deployed system; learners may fix packaging only. The 100-question held-out set and the 50-question dev set stay separate **[Repo: Ops Guide §4]**.
- Two assessors for the G3 technical exam; ask every trio member at least one "why this architecture?" question.
- Foundation criteria: faithfulness >= 85%, context precision >= 70%, cost per transaction reported within 20%, judge TPR/TNR >= 0.85, regression suite in CI that fails on an injected regression, 0 cross-user leaks on an adversarial ACL set, limitations page and error-analysis report **[Sourced: foundation §6.3]**.
- If more than 40% of the cohort misses G3, treat it as a curriculum defect (Week 7-9 load) before treating it as a learner defect.

### W9.8 Exit checklist

- [ ] pass@1 and pass^k reported; >= 2 failure modes fixed and verified
- [ ] Token/task cut >= 30% with no eval drop; cache-hit ratio >= 80%
- [ ] Five decision memos >= 80%
- [ ] Reliability harness shows no user-visible failure at <= 20% injected errors
- [ ] Hosted vs local table delivered; provider switch is config-only
- [ ] Guard stack: attack success < 10%, benign over-block < 5%
- [ ] G3 attempted; metric read-out and feedback delivered
- [ ] Carried system documented: limitations page, error analysis, safety review

### W9.9 Cut or reduced compared with the 24-week plan

The 24-week plan inserts a hands-on **LoRA/QLoRA lab** on an open model <= 8B, a multi-agent orchestrator lab, a hands-on vLLM load test and sizing exercise, and runs the equivalent gate at Day 90 with more evaluation time; here fine-tuning is a decision memo only and open-model serving is a demo **[Sourced: foundation §7.5, §6.2]**.

---

## Week 10: Enterprise integration and the Linden enclave

*Days 46-50 · Phase D Operate + enterprise · Gate: none (red/blue game day) · Project: P3+P4 enclave (P34-M1, M2)*

### W10.1 Objectives

By Friday 17:45 a learner can:

- Put **OIDC/SSO** in front of an AI system and propagate the *end user's* identity to retrieval and tools (no god-mode service account), with 0 leaks across a 20-test ACL set.
- Build a connector to a messy paginated, rate-limited, webhook-emitting source that survives 429s and a mid-sync crash, and a **legacy batch adapter** (SFTP/SOAP) that quarantines malformed payloads.
- Package and deploy the AI service (Helm on kind, ECS variant) with externalised secrets and zero failed requests in a rolling update.
- Build an idempotent incremental sync pipeline where deletes propagate to the vector index within one run.
- Run a **red/blue game day** on peer systems and prove from action logs that no injected instruction caused a consequential action.
- Deploy the carried system in an **air-gapped, residency-constrained** environment and pass a role-played CISO data-flow review.
- Run scope negotiation with a *living client* who changes a requirement, goes quiet and escalates.

### W10.2 Hours and day-by-day schedule

**Hours this week:** AIO 20 · CUS 4.5 · PRJ 12 · SLK 3.5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D46) | 09:00-10:00 | 1 | AIO | INS | Enterprise integration: OIDC/OAuth, SSO, per-user identity to retrieval and tools, token exchange (not god-mode service accounts) |
|  | 10:00-12:30 | 2.5 | AIO | LAB | OIDC login with per-user retrieval ACLs (part 1) `W10-L1` |
|  | 13:15-13:45 | 0.5 | AIO | LAB | OIDC login with per-user retrieval ACLs (part 2) `W10-L1` |
|  | 13:45-15:15 | 1.5 | AIO | LAB | Connector to a messy source (part 1) `W10-L2` |
|  | 15:15-17:45 | 2.5 | PRJ | PRJ | P34-M1: integrate OIDC/ACL and the connector into the carried system `P34-M1` |
| Tue (D47) | 09:00-10:30 | 1.5 | CUS | CUS | Scoping-sprint discovery calls: three vague prospects, 30 min each `W10-L3` |
|  | 10:30-11:00 | 0.5 | AIO | LAB | Connector to a messy source (part 2) `W10-L2` |
|  | 11:00-12:00 | 1 | AIO | INS | AI deployment: containers, Kubernetes/ECS, secrets, autoscaling on queue depth, managed vs self-hosted model endpoints |
|  | 12:00-12:30 | 0.5 | SLK | SLK | Weekly 1:1 with technical mentor |
|  | 13:15-15:15 | 2 | AIO | LAB | Deploy the AI service (Helm on kind; ECS variant) (part 1) `W10-L4` |
|  | 15:15-17:45 | 2.5 | PRJ | PRJ | P34-M1: legacy batch adapter on the carried system `P34-M1` |
| Wed (D48) | 09:00-11:00 | 2 | AIO | LAB | Deploy the AI service (Helm on kind; ECS variant) (part 2) `W10-L4` |
|  | 11:00-12:30 | 1.5 | AIO | LAB | Legacy batch adapter (SFTP/SOAP -> typed API and MCP tool) (part 1) `W10-L5` |
|  | 13:15-15:45 | 2.5 | CUS | CUS | Customer Lab 10 (Linden living client): requirement change, silence, escalation `W10-L6` |
|  | 15:45-16:45 | 1 | PRJ | PRJ | P34-M1: contract tests and rollback plan `P34-M1` |
|  | 16:45-17:45 | 1 | PRJ | LAB | P34-M2: read the air-gap brief; staged mirror and model weights checklist `W10-L7` `P34-M2` |
| Thu (D49) | 09:00-09:30 | 0.5 | CUS | CUS | Retry: scope negotiation re-run `W10-L6` |
|  | 09:30-10:00 | 0.5 | AIO | LAB | Legacy batch adapter (part 2) `W10-L5` |
|  | 10:00-10:30 | 0.5 | AIO | INS | Data pipelines for AI: incremental sync, deletes, quality gates, versioned eval artefacts |
|  | 10:30-12:00 | 1.5 | AIO | LAB | Incremental document-sync pipeline `W10-L8` |
|  | 12:00-12:30 | 0.5 | AIO | INS | GPU and model serving awareness (instructor demo: vLLM metrics, KV cache, queueing) |
|  | 13:15-13:45 | 0.5 | AIO | INS | GPU awareness demo (part 2): sizing exercise discussed, not graded |
|  | 13:45-16:15 | 2.5 | PRJ | LAB | P34-M2: air-gapped and residency-constrained deployment `W10-L7` `P34-M2` |
|  | 16:15-17:45 | 1.5 | SLK | SLK | G3 parallel-task retakes (1 h, only learners who need them) + open labs and mentor drop-in (0.5 h) |
| Fri (D50) | 09:00-09:30 | 0.5 | AIO | INS | Red/blue game-day framing: pre-brief ("it is fine not to solve it"), rules of engagement, sandbox limits |
|  | 09:30-11:00 | 1.5 | AIO | LAB | Red/blue game day (red-team preparation and attacks) `W10-L9` |
|  | 11:00-12:30 | 1.5 | PRJ | LAB | P34-M2: offline guide, CISO data-flow review preparation `W10-L7` `P34-M2` |
|  | 13:15-15:15 | 2 | AIO | LAB | Red/blue game day on peer systems and facilitated debrief `W10-L9` |
|  | 15:15-16:15 | 1 | PRJ | PRJ | P34-M2: CISO persona review of the data-flow `P34-M2` |
|  | 16:15-17:15 | 1 | SLK | SLK | Consolidation: open labs; G4 briefing (rules, on-call, the role-played customer) |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Friday retro + pulse survey |

### W10.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| Enterprise integration | OIDC/OAuth, SSO, token exchange or on-behalf-of, per-user ACLs at retrieval, SAML/SCIM concepts | Keycloak or a test tenant in front of the carried system; shared service accounts are a defect **[Sourced: R5 T21]** |
| Connectors | Pagination, rate limits, webhooks, idempotency, retries, delete events | Full sync of 10k records with no duplicates; kill the sync mid-run |
| Legacy adapters | SOAP/SFTP-batch wrappers; quarantine rather than drop | Contract tests, then a 1-hour replayed load; expose the adapter as a typed API and an MCP tool |
| AI deployment | Containerise the AI service; Helm/Kustomize or ECS; probes; secrets; autoscale on queue depth not CPU; managed vs self-hosted model endpoints | Rolling update under load; no secret in image layers (scanned) **[Sourced: R5 T14]** |
| GPU and serving awareness | VRAM, KV-cache, batching; vLLM metrics; KServe/llm-d as awareness only | **Instructor demo** (1 h); not graded in the 12-week plan |
| Data pipelines for AI | Incremental sync, delete propagation, quality gates, versioned eval artefacts | 10% bad-file injection quarantined and reported |
| Red/blue game day | Injection planted in a document, an email and a tool result; blue team defends; measure *actions*, not model text | >= 15 attempts logged; faults `AI-INJECT-INDIRECT`, `AI-INJECT-TOOL`. Pre-brief: this is a no-stakes first drill **[Sourced: R3 §1.6 "play to learn"]** |
| Air-gap and data residency | A missing route (not a restrictive security group) means no egress; pre-staged registry mirror, models, embeddings and offline vector DB; the learning is in the pre-staging discipline | `FIELD-AIRGAP` environment (~20 min reset; air-gap is the foundation's exception to the 5-minute rule); `FIELD-BLIND` where one fault is diagnosable only through an operator proxy **[Repo: Ops Guide §4; Sourced: R4 §2.10]** |

### W10.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W10-L1` | OIDC login with per-user retrieval ACLs | D3, D6 | 3 | OIDC login (Keycloak or a test tenant) in front of the carried system; user identity propagated to retrieval | 20 tests, 0 leaks (user A never retrieves user B's documents); expiry/refresh handled; logout clears the session; no shared service-account access to documents | FAULT: RAG-ACL (token-claim variant) |
| `W10-L2` | Connector to a messy source | D1, D6 | 2 | Paginated REST source with rate limits and webhooks synced into the index | Full sync of 10k records with no duplicates; survives 429s and a mid-sync crash; delete events propagate |  |
| `W10-L5` | Legacy batch adapter (SFTP/SOAP -> typed API and MCP tool) | D1, D6 | 2 | Adapter around a mock legacy claims export | Contract tests pass; malformed payloads quarantined, not dropped; 1-hour replayed load with no data loss |  |
| `W10-L4` | Deploy the AI service (Helm on kind; ECS variant) | D5, D2 | 4 | Carried system packaged and deployed with externalised secrets | Rolling update with zero failed requests under load; readiness probe gates traffic; no secret in image layers (scanned) |  |
| `W10-L8` | Incremental document-sync pipeline | D5, D1 | 1.5 | Idempotent ingest of new/changed/deleted files into the vector index | Re-run is idempotent; deletion removes vectors within one run; a 10% bad-file injection is quarantined and reported |  |
| `W10-L9` | Red/blue game day on peer systems | D3, D5 | 3.5 | Red team plants injected instructions in a document, an email and a tool result; blue team defends | >=15 distinct attempts logged; after mitigations no attempt triggers a consequential action (state change or data egress) in the sandbox, measured from action logs not model text | FAULT: AI-INJECT-INDIRECT, AI-INJECT-TOOL |
| `W10-L7` | Air-gapped and residency-constrained deployment | D3, D2 | 5 | Carried system deployed in the no-egress VPC with pre-staged models, mirrored packages and an offline vector DB; offline deployment guide | Six-constraint checklist met; system works with no egress; a peer follows the guide; diagnosing one fault is done only via an operator proxy (FIELD-BLIND) | FAULT: FIELD-AIRGAP, FIELD-BLIND |
| `W10-L3` | Scoping-sprint discovery calls (3 vague prospects) | D6 | 1.5 | Three 30-min discovery calls with notes and a stakeholder map for each prospect | R1 >=3 on each call; one prospect chosen with a reasoned riskiest assumption | CUSTOMER (R1, R2) |
| `W10-L6` | Customer Lab 10: the living client | D6 | 3 | Linden persona changes a requirement mid-build, goes quiet, then escalates; learner runs scope negotiation and an escalation note | R6 >=3 and R9 >=3: traded scope explicitly; named uncertainty; escalated at the right time; distinguished reusable from bespoke work | CUSTOMER (R6, R9) |

### W10.5 Customer thread and project milestone

**Customer Lab 10 (Wednesday, 2.5 h) is the *living client* (stage 3 of the simulated-client format):** the Linden persona changes a requirement mid-build, goes quiet for part of the session, then escalates. The learner runs scope negotiation (trade scope explicitly, never silently absorb), names uncertainty and escalates at the right time. **R6 and R9 >= 3.** Retry on Thursday (0.5 h).

**Scoping sprint, discovery calls (Tuesday, 1.5 h):** three vague prospects, 30 minutes each, stakeholder map per prospect; learners choose one and name its riskiest assumption. These calls feed P7 in Week 11. The air-gap work includes a role-played CISO review of the data flow and a plain-language explanation of why the offline package set is the way it is (R7).

**Carried-system milestones P34-M1 and P34-M2 (12 h):** the foundation combines projects P3 (hostile legacy integration) and P4 (constrained environment) into one "Linden enclave" on the carried system.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P34-M1` Linden enclave (part 1): legacy adapter and SSO/ACL on the carried system | Linden | 6 | Legacy batch adapter and OIDC/ACL integrated into the carried system; connector for the messy source | Adapter contract tests green; 0 ACL leaks on the adversarial set; deployment via IaC/Helm repeatable |
| `P34-M2` Linden enclave (part 2): air-gap and data-residency deployment | Linden | 6 | Offline deployment guide; accreditation-style checklist; role-played CISO data-flow review | System runs with no egress; CISO persona review finds <=2 gaps; a peer deploys from the guide alone |

### W10.6 Resources

- MCP authorisation tutorial (2026-07-28) https://modelcontextprotocol.io/docs/2026-07-28/tutorials/security/authorization.md **[Sourced: R5 T21; path from llms.txt, not read in full]**
- KServe 0.17 release notes (LLMInferenceService on llm-d, vLLM metrics) https://kserve.github.io/website/blog/kserve-0.17-release **[Sourced: R5 T14, S; awareness only]**
- Air-gapped AI deployment: https://fde.academy/blog/air-gapped-ai-deployment-guide-for-fdes and https://decagon.ai/blog/what-an-air-gapped-ai-deployment-actually-requires **[Sourced: R4 §2.10; vendor sources, no hands-on teaching method was found, so the lab is our design]**
- Willison's trifecta/Rule-of-Two posts (see Week 6) for the red/blue briefing **[Sourced: R5 T17, V]**

### W10.7 Stall points and instructor notes

**Likely stall points:**

1. OIDC redirect and token-claim debugging: provide a working realm export and teach decoding a JWT.
2. Per-user ACL via claims into the retrieval filter: draw the data path once on the whiteboard.
3. Legacy adapter encodings and malformed batch files: this is *the* realistic mess; do not clean the fixtures.
4. Air-gap: tooling assumes internet (package managers, model downloads). Give the pre-staging checklist before the lab starts.
5. Red team success measured by model *words*: coach to measure by action logs.

**Instructor notes**

- The air-gap VPC must have **no egress route at all** (a missing route, not a rule) **[Repo: Ops Guide §4]**.
- Week 10 slack (3.5 h) is for the open labs; Week 11 slack (12.5 h) is the on-call window for G4. Do not let Week 10 overrun into it.
- Thursday's slack hosts the **G3 parallel-task retakes** (1 h; a different business metric and held-out set, same rubric).
- G4 briefing happens Friday (rules, on-call, the role-played customer).
- The GPU walk-through is a demo; if no GPU pool exists, show vLLM metrics from a recorded session.

### W10.8 Exit checklist

- [ ] 20 ACL tests, 0 leaks; token expiry/refresh handled; logout clears the session
- [ ] 10k-record sync is duplicate-free, survives 429s and a mid-sync crash
- [ ] Adapter contract tests green; malformed payloads quarantined
- [ ] Rolling update with zero failed requests; no secrets in image layers
- [ ] Sync pipeline idempotent; deletions propagate
- [ ] Red/blue: >= 15 attempts logged; no consequential action from any
- [ ] Offline deployment guide followed by a peer; CISO persona review finds <= 2 gaps
- [ ] Scope negotiation scored R6/R9 >= 3

### W10.9 Cut or reduced compared with the 24-week plan

The 24-week plan splits this into P3 (hostile legacy integration, 16 h) and P4 (constrained environment, 16 h) as separate projects, runs hands-on privacy and enterprise-integration drills (T21 at 20 h vs 8 h) and GPU serving in a shared pool; here they are combined into one enclave project with a demo-level GPU walk-through **[Sourced: foundation §7.5, §8.3]**.

---

## Week 11: Operate under failure (G4), privacy, and the scoping sprint

*Days 51-55 · Phase D Operate + enterprise · Gate: G4 (Day 55) · Project: P7-M1, M2*

### W11.1 Objectives

By Friday 17:45 a learner can:

- **Operate the carried system through five injected failures** (provider outage, poisoned document, 10x traffic spike, prompt regression, 6x cost burn) alongside normal work, self-detecting every incident and writing blameless postmortems within 24 hours.
- Cut cost per transaction >= 40% via caching, routing and prompt trimming with <= 2 points of eval drop, and alarm on a runaway-loop cost burn within an hour.
- Produce a data-flow diagram and DPIA-lite covering every hop (user, app, vector DB, LLM provider, logs, traces), redact PII (>= 95% recall on 5 entity types) before the LLM and before trace storage, and prove a right-to-delete across vectors, caches and traces.
- Write a system card whose every claim has evidence.
- Communicate during an incident: answer-first status updates and an executive cost question handled without surprising the customer.
- Complete a **scoping sprint** (no build): discovery to PR/FAQ to a two-page staged proposal, defended to an adversarial three-stakeholder panel.
- **Pass G4**, including a runbook cold-execution test by another pod.

### W11.2 Hours and day-by-day schedule

**Hours this week:** AIO 10 · CUS 4.5 · PRJ 8 · ASM 5 · SLK 12.5 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D51) | 09:00-09:30 | 0.5 | AIO | INS | Cost and latency levers: caching, routing, prompt trimming, output tokens; unit economics |
|  | 09:30-12:30 | 3 | AIO | LAB | Cost and latency optimisation (part 1) `W11-L1` |
|  | 13:15-14:15 | 1 | CUS | CUS | Scoping sprint: round-2 call with the chosen prospect `W11-L2` |
|  | 14:15-14:45 | 0.5 | PRJ | PRJ | P7-M1: record the riskiest assumption and the call plan `P7-M1` |
|  | 14:45-17:45 | 3 | SLK | SLK | G4 on-call window 1 (Mon): model-provider outage injected; detect <=5 min, mitigate, update the customer persona `W11-L3` |
| Tue (D52) | 09:00-09:30 | 0.5 | AIO | LAB | Cost and latency optimisation (part 2) `W11-L1` |
|  | 09:30-10:00 | 0.5 | AIO | INS | Privacy and compliance for AI: data classes, retention, residency, deletion across vectors, caches and traces |
|  | 10:00-11:30 | 1.5 | AIO | LAB | Data-flow diagram, DPIA-lite, PII redaction, deletion (part 1) `W11-L4` |
|  | 11:30-12:30 | 1 | PRJ | PRJ | P7-M1: PR/FAQ draft `P7-M1` |
|  | 13:15-14:45 | 1.5 | CUS | CUS | Customer Lab 11: adversarial three-stakeholder panel on the draft proposal `W11-L5` |
|  | 14:45-15:45 | 1 | PRJ | PRJ | P7-M1: revise after panel feedback `P7-M1` |
|  | 15:45-17:45 | 2 | SLK | SLK | G4 on-call window 2 (Tue): poisoned document planted in the index; detect <=4 h with no labels `W11-L3` |
| Wed (D53) | 09:00-11:00 | 2 | AIO | LAB | Data-flow diagram, DPIA-lite, PII redaction, deletion (part 2) `W11-L4` |
|  | 11:00-11:30 | 0.5 | AIO | LAB | System card for the carried system (part 1) `W11-L6` |
|  | 11:30-12:30 | 1 | SLK | SLK | G4 on-call window 3 (Wed): 10x traffic spike; detect <=3 min `W11-L3` |
|  | 13:15-14:45 | 1.5 | CUS | CUS | Customer Lab 12: communicating under incident (status updates, executive cost question) `W11-L7` |
|  | 14:45-16:15 | 1.5 | PRJ | PRJ | P7-M1: finalise the PR/FAQ `P7-M1` |
|  | 16:15-16:45 | 0.5 | PRJ | PRJ | P7-M2: outline the staged proposal `P7-M2` |
|  | 16:45-17:45 | 1 | SLK | SLK | Postmortems for incidents 1-3 due within 24 h (blameless, facilitated) `W11-L3` |
| Thu (D54) | 09:00-10:30 | 1.5 | AIO | LAB | System card for the carried system (part 2) `W11-L6` |
|  | 10:30-11:00 | 0.5 | CUS | CUS | Retry: incident status update re-run `W11-L7` |
|  | 11:00-12:30 | 1.5 | PRJ | PRJ | P7-M2: 2-page staged proposal with success metrics `P7-M2` |
|  | 13:15-15:15 | 2 | PRJ | PRJ | P7-M2: panel defence preparation and run-through `P7-M2` |
|  | 15:15-17:45 | 2.5 | SLK | SLK | G4 on-call window 4 (Thu): prompt regression merged by a teammate bot; should be blocked in CI, else detect <=30 min; runbook finalisation `W11-L3` |
| Fri (D55) | 09:00-10:00 | 1 | ASM | ASM | G4 on-call window 5 (Fri): 6x cost-burn anomaly (detect <=1 h); unit-economics review |
|  | 10:00-12:30 | 2.5 | ASM | ASM | G4 runbook cold-execution test: another pod operates your system from your runbook only |
|  | 13:15-14:45 | 1.5 | ASM | ASM | G4 postmortem review, customer-communication review and individual feedback |
|  | 14:45-15:15 | 0.5 | SLK | SLK | Weekly retrieval quiz (items from Weeks 5-10) |
|  | 15:15-16:15 | 1 | SLK | SLK | G5 brief handed out (reading only) and teams of two formed |
|  | 16:15-17:15 | 1 | SLK | SLK | Consolidation: remediation on any G4 gaps; mentor drop-in |
|  | 17:15-17:45 | 0.5 | SLK | SLK | Friday retro + pulse survey |

### W11.3 What to teach and how

| Topic | What to teach | How |
|---|---|---|
| Cost and latency | Caching, model routing, prompt trimming, output tokens (usually the expensive ones), unit economics; fallbacks multiply cost | Before/after table from traces; eval gate must stay green; fault `LLM-COSTBURN` **[Sourced: R5 T13]** |
| Privacy and compliance for AI | Data classes, minimisation, retention, region, subprocessors; read the provider's current retention terms (the research did not verify provider terms); deletion must reach vectors, caches, traces and derived summaries | DPIA-lite and a right-to-delete drill **[Sourced: R5 T18]**. EU AI Act: conceptual only; dates and GPAI obligations are in flux and unverified **[Sourced: R5 flags, S/U]** |
| System card (responsible AI) | NIST AI RMF functions (Govern, Map, Measure, Manage) as a checklist; measured numbers, not adjectives | System card for the carried system; slice analysis is dropped in the 12-week plan |
| Operating under failure | On-call, detection from SLOs and traces, mitigation before diagnosis, postmortems | G4 simulation runs inside normal work (below) |
| Scoping sprint | Discovery, stakeholder maps, riskiest assumption, PR/FAQ, staged proposal, defending cost and risk | Three prospects from Week 10; one chosen; adversarial panel on the draft |

**G4 on-call schedule (compressed from the repo's five-day simulation).** Each injection lands at an unannounced time inside its window; a role-played customer asks for status once a day; an executive asks about cost on day 3 **[Repo: Assessment Pack §6]**.

| Day | Injection (family) | Detection expected within |
|---|---|---|
| Mon | Model-provider outage (`LLM-PROVIDER`) | 5 min |
| Tue | Poisoned document in the index (`AI-INJECT-INDIRECT` / `RAG-FAIL` variant), no labels available | 4 h |
| Wed | 10x traffic spike | 3 min |
| Thu | Prompt regression merged by a teammate bot (`LLM-REGRESS`) | Blocked in CI; if merged, 30 min |
| Fri morning | 6x cost-burn anomaly (`LLM-COSTBURN`) | 1 h |

### W11.4 Labs

| ID | Lab | Domain | Hours | Deliverable | Pass criteria (measurable) | Flag |
|---|---|---|---|---|---|---|
| `W11-L1` | Cost and latency optimisation | D5, D4 | 3.5 | Baseline pipeline cut in cost via caching, routing and prompt trimming; runaway-loop alarm | Cost cut >=40% with <=2-point drop on the eval set, shown from traces; a budget alarm fires within 1 h on a simulated 6x burn | FAULT: LLM-COSTBURN |
| `W11-L4` | Data-flow diagram, DPIA-lite, PII redaction, deletion | D3 | 3.5 | Diagram of every hop (user, app, vector DB, LLM provider, logs, traces) with data classes, retention, region, subprocessor; PII redaction before the LLM and before trace storage; one right-to-delete drill | No hop with undeclared PII; reviewer finds <=2 gaps; redaction recall >=95% on a labelled set (5 entity types); deletion verified in vectors, caches and traces |  |
| `W11-L6` | System card for the carried system | D3, D4 | 2 | System card: purpose, data, limits, known failure modes with measured numbers, human-oversight design | Every claim has evidence (a number or a test); reviewer can find evidence for each in <2 min; limitations page matches G3 findings |  |
| `W11-L2` | Scoping sprint: round-2 call with the chosen prospect | D6 | 1 | Second discovery call testing the riskiest assumption | R1 >=3; the riskiest assumption is confirmed, refuted or reframed with evidence | CUSTOMER (R1, R2) |
| `W11-L5` | Customer Lab 11: adversarial three-stakeholder panel | D6 | 1.5 | Panel (sponsor, skeptical technical lead, compliance owner) on the draft proposal; one aligned plan | R2 >=3 and R9 >=3: one plan all three can sign, with explicit trade-offs and a "no" where needed | CUSTOMER (R2, R9) |
| `W11-L7` | Customer Lab 12: communicating under incident | D6 | 2 | Status updates and an executive cost question handled while the G4 simulation runs | R5 >=3 (bottom line first, no surprises vs last update); R6 >=3 (early, owned, options and next step) | CUSTOMER (R5, R6) |
| `W11-L3` | G4 production simulation: five injected failures (on-call windows) | D5, D3, D2 | 9.5 | Carried system operated through Monday-Friday injections with runbooks, postmortems and customer updates | See G4 section: >=99% availability, 5/5 self-detected, postmortem within 24 h each, runbooks executable by another pod, unit economics reported | FAULT: PROD-SIM (provider outage, poisoned document, 10x spike, prompt regression, 6x cost burn) |

### W11.5 Customer thread and project milestone

**Four customer interactions this week (4.5 h):** the scoping-sprint round-2 call (Mon), the adversarial three-stakeholder panel on the draft proposal (Tue; sponsor wants speed, the skeptical technical lead probes limits, the compliance owner blocks on data; the learner must produce *one aligned plan*), communicating under incident (Wed; **R5, R6**), and the Thursday retry. G4 itself weights **communication equally with the technical response**: an engineer who silently fixes an outage while the customer escalates internally has failed the exercise **[Repo: Assessment Pack §6]**.

**P7 (8 h)** deliverables: stakeholder maps, riskiest-assumption test, PR/FAQ, 2-page staged proposal with success metrics, panel defence. Teach only Minto and PR/FAQ here; do not add frameworks.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P7-M1` Scoping sprint: discovery to PR/FAQ draft | Kestrel expansion + 2 vignettes | 4 | Stakeholder maps, riskiest-assumption test, PR/FAQ draft for one chosen prospect | R2 >=3: user, decision, metric, constraints, out-of-scope and riskiest assumption all named |
| `P7-M2` Scoping sprint: staged proposal and panel defence | Kestrel expansion + 2 vignettes | 4 | 2-page staged proposal with success metrics; panel defence of cost and risk | Panel finds the plan staged and falsifiable; trade-offs and a "not yet" stated; defence answers the sponsor, technical lead and compliance owner |

### W11.6 Resources

- AWS Fault Injection Service (experiment templates with stop conditions tied to alarms; run in pre-production first) https://docs.aws.amazon.com/fis/latest/userguide/what-is.html **[Sourced: R2 §3.3, V]**; AWS Well-Architected game-day guidance (include non-engineer voices; document lessons) https://docs.aws.amazon.com/wellarchitected/latest/framework/rel12-bp05.html **[Sourced: R3 §1.9]**
- NIST AI Risk Management Framework https://www.nist.gov/itl/ai-risk-management-framework **[Sourced: R5 T19, V]**
- Amazon Working Backwards PR/FAQ https://aboutamazon.com/news/workplace/an-insider-look-at-amazons-culture-and-processes **[Sourced: R4 §2.4]**; impact mapping (reference only) https://www.amplitude.com/blog/impact-map **[Sourced: R4 §2.5, V]**
- Google SRE Book, *Evolving the SRE engagement model* (production readiness review; onboarding a service) https://sre.google/sre-book/evolving-sre-engagement-model/ **[Sourced: R4 §2.9]**
- Etsy debrief facilitation guide https://codeascraft.com/2016/11/17/debriefing-facilitation-guide/ **[Sourced: R3 §1.9]**

### W11.7 Stall points and instructor notes

**Likely stall points:**

1. Alert fatigue and missing detection: learners watch dashboards instead of alerts; remind them of the SLO burn-rate alerts from Week 4.
2. Postmortems written as blame or as narrative: use a fixed template (timeline, contributing factors, detection signal, three actions).
3. Right-to-delete misses derived data (embeddings, caches, eval sets, summaries).
4. The scoping sprint expands into design: enforce "no build", only a plan.
5. Runbooks that rely on the author's head: the cold-execution test exposes them; that is the point.

**Instructor notes**

- Week 11 slack is 12.5 h: it is the on-call and response time that the G4 injections consume, plus consolidation. Report the actual hours spent so the pilot can recalibrate this figure.
- Injections must be reproducible (randomised variants per learner) and reset in minutes **[Repo: Ops Guide §3]**.
- Pre-brief before the first injection: "troubleshooting is a series of failures; it is fine not to solve it" (Google "play to learn"). A game day with only engineers misses coordination and communication, so the role-played customer is mandatory **[Sourced: R3 §1.9]**.
- The G5 brief is handed out Friday as reading only; teams of two formed.

### W11.8 Exit checklist

- [ ] Availability >= 99% across the five-day window; 5/5 incidents self-detected
- [ ] 5/5 postmortems delivered within 24 h; runbooks executed cold by another pod
- [ ] Cost cut >= 40% with <= 2 points eval drop; 6x burn alarm fires within 1 h
- [ ] Data-flow diagram complete; PII redaction recall >= 95%; right-to-delete verified
- [ ] System card: every claim evidenced
- [ ] P7 proposal defended; one aligned plan produced for the panel
- [ ] Status updates scored R5/R6 >= 3

### W11.9 Cut or reduced compared with the 24-week plan

The 24-week plan runs G4 as a **full five-day** production simulation at Day 105 and adds an OWASP LLM01-10 control map with evidence at G4; privacy drills (DPIA-lite, right-to-delete) and responsible-AI slice analysis are hands-on. Here G4 is compressed into normal work, privacy is one lab, and slice analysis is dropped **[Sourced: foundation §6.3, §7.5]**.

---

## Week 12: Capstone and readiness panel (G5)

*Days 56-60 · Phase E Capstone · Gate: G5 (Day 60) · Project: P8-M1..M4*

### W12.1 Objectives

By Friday 17:45 a team of two can:

- Take an engagement brief with **exactly three planted complications** and, in four working days, deliver a production-grade system on the carried Linden platform: scoped, built to the eval threshold, secured with evidence, costed, and handed over.
- Produce all **nine deliverables** (see the capstone section) and present them to a four-person panel.
- Defend technical choices under adversarial questioning and explain the engagement to a non-technical customer-facing leader.
- Operate a *peer team's* system from its handover pack alone, including two seeded incidents.

Each learner leaves with a **provisional readiness outcome** (Ready: Workstream Owner / Ready: Supervised / Conditional / Not yet ready), confirmed after the panel deliberates.

### W12.2 Hours and day-by-day schedule

**Hours this week:** PRJ 32 · ASM 8 = **40 h**

| Day | Time | h | Block | Type | Activity |
|---|---|---|---|---|---|
| Mon (D56) | 09:00-10:00 | 1 | PRJ | PRJ | P8-M1: engagement brief from the Linden persona; three planted complications; teams of two start `P8-M1` |
|  | 10:00-12:30 | 2.5 | PRJ | PRJ | P8-M1: discovery with the persona; scoping document with measurable success criteria `P8-M1` |
|  | 13:15-17:45 | 4.5 | PRJ | PRJ | P8-M1: architecture, ADRs, control mapping; plan and cut-line agreed with the persona `P8-M1` |
| Tue (D57) | 09:00-12:30 | 3.5 | PRJ | PRJ | P8-M2: build the system (IaC, service, retrieval/agent, auth) `P8-M2` |
|  | 13:15-17:45 | 4.5 | PRJ | PRJ | P8-M2: eval harness, regression gate in CI, tracing and SLOs `P8-M2` |
| Wed (D58) | 09:00-12:30 | 3.5 | PRJ | PRJ | P8-M2: run evals against the fresh held-out set; fix failure modes; cost per transaction `P8-M2` |
|  | 13:15-17:45 | 4.5 | PRJ | PRJ | P8-M3: security evidence pack, OWASP LLM01-10 map, system card, cost model `P8-M3` |
| Thu (D59) | 09:00-12:30 | 3.5 | PRJ | PRJ | P8-M4: operator runbook, handover plan, product-feedback memo, executive summary `P8-M4` |
|  | 13:15-17:45 | 4.5 | PRJ | PRJ | P8-M4: dress rehearsal with a staff panel; freeze at 15:45; final polish of deliverables `P8-M4` |
| Fri (D60) | 09:00-11:00 | 2 | ASM | ASM | G5 handover cold-test: operate a peer team's system from its pack only; two seeded incidents |
|  | 11:00-12:30 | 1.5 | ASM | ASM | G5 defence block 1: half the teams defend to Panels A/B; the others observe and score |
|  | 13:15-14:45 | 1.5 | ASM | ASM | G5 defence block 2: remaining teams defend; the others observe and score |
|  | 14:45-16:45 | 2 | ASM | ASM | G5 peer scoring and calibration against the panel rubric |
|  | 16:45-17:45 | 1 | ASM | ASM | Individual readiness conversation (provisional outcome), programme survey, Day 61-90 ramp briefing |

### W12.3 What to teach and how

| Day | Focus | Teaching method |
|---|---|---|
| Mon (Day 56) | **Brief, discovery, scoping, architecture.** The Linden persona delivers the brief; the three complications are revealed as they would be in the field (one up front, one in discovery, one when asked the right question). Scope document with measurable success criteria; ADRs; control mapping; plan and cut-line | Teams of two; coaching on demand only; instructors act as the client, not as teachers |
| Tue (Day 57) | **Build.** IaC, service, retrieval/agent, auth; eval harness, CI regression gate, tracing and SLOs | Floating instructor in coach mode; stall points logged |
| Wed (Day 58) | **Evals and evidence.** Run against a fresh held-out set; fix failure modes; cost per transaction; security evidence pack, OWASP LLM01-10 control map, system card, cost model | Pair review across teams |
| Thu (Day 59) | **Handover.** Operator runbook, handover plan, product-feedback memo (pattern vs bespoke), one-page executive summary; dress rehearsal with a staff panel; **freeze at 15:45** | Staff panel rehearsal gives feedback only, no coaching on content after freeze |
| Fri (Day 60) | **G5.** Handover cold-test, two defence blocks (half the teams defend while the others observe and score), peer scoring and calibration, individual readiness conversation | See the G5 section |

**Planted-complication families (choose three per team; capped at three) [Repo: Handbook Week 12; Judgment on specifics]:** a data-residency or air-gap rule, an unreliable legacy source, a stakeholder who was never told, a provider outage or price change mid-week, a corpus with conflicting versions of the same SOP. Use scenarios the cohort has not seen (`FIELD-AIRGAP`, `FIELD-BLIND`, `AI-INJECT-TOOL` variants).

### W12.4 Labs

*No new labs this week; capstone work is tracked as project milestones.*

### W12.5 Customer thread and project milestone

Customer craft is embedded throughout: discovery with the persona (Mon), a scope negotiation when complication 2 lands, a status update midweek, and the business-framing block at the panel. The panel's craft rubric scores all nine dimensions (Discovery, Scoping, Architecture, Execution, Troubleshooting, Security posture, Communication, Judgment, Handover) by two independent assessors **[Sourced: foundation §6.4 Template B]**.

The Friday handover cold-test is the **fresh-eyes review** from the simulated-client format: a different team operates your system from your runbook only, deploys, monitors, rolls back and handles two seeded incidents (**R8**) **[Sourced: R4 §3.2, §2.9]**.

| Milestone | Customer | Hours (this week) | Deliverable | Acceptance |
|---|---|---|---|---|
| `P8-M1` Capstone: scoping, discovery and architecture | Linden (carried system) | 8 | Scoping document with measurable success criteria (out-of-scope + riskiest assumption); architecture document with ADRs and control mapping | All success criteria falsifiable; >=3 ADRs incl. the response to each planted complication; trust boundaries marked |
| `P8-M2` Capstone: build to the eval threshold | Linden (carried system) | 11.5 | Working system deployed via IaC meeting the stated eval thresholds; CI/CD with the eval regression gate; observability with SLOs and LLM tracing | G3 thresholds met on a fresh held-out set (faithfulness >=85%, context precision >=70%); regression gate fails on an injected regression; SLO dashboards live |
| `P8-M3` Capstone: security evidence, cost model and operations | Linden (carried system) | 4.5 | Security evidence pack (SBOM, scans, IAM matrix, threat model, OWASP LLM01-10 control map, system card); cost model with unit economics | All 10 OWASP LLM items addressed with a test/config or an explicit accepted risk; unit economics within 20% of the stated target |
| `P8-M4` Capstone: handover, executive summary and rehearsal | Linden (carried system) | 8 | Operator runbook + handover plan; product-feedback memo (pattern vs bespoke); one-page executive summary; defence rehearsal | Runbook follows R8 (cold operator can deploy, monitor, roll back and handle two seeded incidents); memo classifies each custom piece; summary readable by a non-technical leader in 2 minutes |

### W12.6 Resources

- Foundation §8.5 for the nine deliverables and §6.3 for G5; Assessment Pack §7 for the panel format **[Repo]**
- Google SRE Book, *Evolving the SRE engagement model* (handover and onboarding of a service) https://sre.google/sre-book/evolving-sre-engagement-model/ **[Sourced: R4 §2.9]**
- OWASP LLM Top 10 (2025) for the control map https://genai.owasp.org/llm-top-10/ ; NIST AI RMF for the system card https://www.nist.gov/itl/ai-risk-management-framework **[Sourced: R5, V]**
- Anthropic, *Demystifying evals for AI agents* for the evidence format https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents **[Sourced: R5 T6, V]**
- The Cloud Resume Challenge and Udacity's pipeline project as reminders of the end-to-end IaC + CI/CD + tests + write-up shape https://cloudresumechallenge.dev/docs/the-challenge/ **[Sourced: R2 §1.16]**

### W12.7 Stall points and instructor notes

**Likely stall points:**

1. Scope creep in the first four hours: hold the cut-line agreed on Monday.
2. Eval threshold shortfall on Wednesday: spend the remaining hours on the *top failure mode*, not on a rewrite.
3. Handover pack written last and badly: schedule Thursday's runbook block before the build is "finished".
4. Team of two split into two non-integrating halves: require a joint 15-minute daily integration.
5. Exhaustion: the schedule ends at 17:45 and there is no required work after it; enforce the cut-line rather than evening work (wellbeing safeguard 1).

**Instructor notes**

- **Two of four panelists score the craft rubric independently**; record the inter-assessor delta (target <= 1.0). Panel: a senior FDE, a security lead, an ML lead, a customer-facing leader **[Repo: Assessment Pack §7]**.
- Run the panel in two parallel rooms (Panels A/B) so half the teams defend in each block; observers score with the same rubric as calibration practice.
- Do not tell teams which complications will be chosen; they are drawn at brief time.
- Outcomes are provisional until the panel deliberates; communicate within two working days. Learners are told the decision rule in advance.

### W12.8 Exit checklist

- [ ] Nine deliverables submitted before freeze
- [ ] Capstone meets G3-level eval thresholds on a fresh held-out set
- [ ] Peer runbook cold-test executed
- [ ] Defence delivered; craft rubric scored by two assessors
- [ ] Readiness outcome and next steps recorded; Day 61-90 ramp briefing delivered
- [ ] Programme survey completed; 30-day and 6-month surveys scheduled

### W12.9 Cut or reduced compared with the 24-week plan

The 24-week capstone has an **individual-plus-pod** structure over weeks 22-24 (64 project hours including the embedded pod phase on real low-risk work and a Day-115 pod review) and a flagship engagement that includes P7 as a separate 16-hour project; here the capstone is four days with teams of two and simulated clients only **[Sourced: foundation §6.3, §8.3]**.

---

# Part III: Reference

## 3. Gates (G0-G5)

Three assessment layers (foundation §6.1): continuous lab checks (formative; every AI lab needs eval and trace evidence), the six gates below (summative; work-sample tasks in **novel environments**, rubric-scored, published in advance), and the capstone and readiness panel (G5). Every gate uses a fresh environment with a randomised fault variant so memory is not what is tested **[Repo: Assessment Pack §1; foundation P10]**. Two independent assessors score G2, G4 and G5; calibrate on a recorded example before each cohort, and a delta above 1.0 forces a calibration session. **Mentors do not assess their own mentees' gates [Repo: Ops Guide]**.

### 3.1 G0: Baseline (Days 1-2; diagnostic, no pass or fail)

| Component | Format | Output |
|---|---|---|
| G0-A Written exam | 60 questions, 2 h, Day 1 PM. Routing only; the only written instrument in the program | Provisional level per domain |
| G0-B Layered-fault practical | 3 h, Day 2 AM, observed. `G0-LAYERED`: one obvious fault (crash loop from a missing ConfigMap key), one moderate (a NetworkPolicy blocking DNS), one subtle (a readiness probe returning 200 with an unhealthy body) | `time_to_first_signal`, faults found/fixed (0-3), `method_score` (1-5), hints taken with timestamps |
| G0-C Mock discovery call | 30 min, Day 2 PM; scripted-vague Kestrel COO, recorded; scored on Discovery and Scoping only | D6 provisional level |
| Self-rating | 30 min; behavioural L0-L4 scale per domain | Baseline self-rating (Google's behavioural scale replaced a 7-point scale that was "too noisy" **[Sourced: R3 §1.6]**) |

**Exam blueprint (adapted from the repo to the new domains; question counts unchanged) [Repo: Assessment Pack §2.1]:**

| Domain | Qs | L1 recall | L2 applied | L3 scenario | Example question type (adapted) |
|---|---|---|---|---|---|
| D1 Software Eng. | 12 | 3 | 5 | 4 | Diagnose a process at 100% CPU with no obvious hot loop |
| D2 Cloud & Platform | 12 | 3 | 5 | 4 | Explain why a pod is `Pending` when events show no node matches |
| D3 Secure Delivery | 8 | 3 | 3 | 2 | State what an SBOM does and does not tell you |
| **D4 Applied AI** | 12 | 3 | 5 | 4 | Choose between prompting, RAG and fine-tuning for a stated case, with justification |
| D5 AI Ops | 8 | 3 | 3 | 2 | A model provider returns 429s for ten minutes: what should the app do and what should you alert on? *(replaces the repo's drift question [Judgment])* |
| D6 Customer Craft | 8 | 2 | 3 | 3 | Given a customer email demanding scope creep, choose and justify a response |

Provisional levels: 0-24% L0 · 25-44% L1 · 45-69% L2 · 70-89% L3 · 90%+ L4 (confirm by interview). **The practical overrides the written score** (written performance overstates D1 and D2): 3 faults fixed unaided -> L3 D2; 2 -> L2; 1 or heavy hinting -> L1; 0 -> L0. Mock call: surfaces the hidden problem and reframes -> L3 D6; good clarifying questions but takes the stated problem at face value -> L2; order-taking -> L1.

**Lanes.** A: (D1+D2)/2 >= 2.5 and (D4+D5)/2 <= 1.5 (platform-strong) · B: D4 >= 2.5 and (D2+D3)/2 <= 1.5 (AI-strong) · C: otherwise (balanced). A and B learners are paired within a trio; C is paired with an A or a B. Thresholds are a starting point to recalibrate in the pilot **[Repo; Judgment]**. The ILP is issued by Day 3.

### 3.2 G1: Platform, rebuild from scratch (Day 20)

**Setup.** A fresh, empty AWS sandbox account the learner has never touched; a git repo with the Kestrel application; a randomised fault variant (`IAC-DRIFT` family); screen-recorded and timed from `git clone`. Staggered 60-minute windows within a 3.5 h block, then a 1.5 h debrief.

| # | Criterion (all required) | Verification |
|---|---|---|
| 1 | Under **60 minutes** end to end | Timer |
| 2 | **Zero manual console actions** (automatic fail otherwise) | Screen recording + CloudTrail |
| 3 | Service serving traffic and passing health checks (ECS Fargate behind an ALB) | Assessor `curl` |
| 4 | **Three SLOs** with burn-rate alerts that would actually fire | Alert rules present; one is exercised |
| 5 | Test coverage **>= 70%** | CI output |
| 6 | Security defaults: non-root, resource limits, no hard-coded secrets, image scan clean | Assessor inspection |
| 7 | Cost sanity: tagged, no oversized resources, no orphans | Assessor review |

Scored dimensions (1-5): speed, reproducibility (a second `apply` shows an empty plan), security defaults, observability quality (an operator who did not build it can diagnose a fault from the output), cost sanity **[Repo: Assessment Pack §3]**. *Differences from the repo and from the 24-week plan:* the repo also required autoscaling and Kubernetes; the foundation puts both in the 24-week G1 only **[Sourced: foundation §6.3]**. Common failures: console-clicking under time pressure, alerts that are valid but never fire, unstructured logs, a non-idempotent plan.

### 3.3 G2: Secure delivery review (Day 30)

A panel of two to three plays an enterprise security team; **45-minute** defence, with a Linden-style questionnaire. **Seven artifacts are submitted 24 hours in advance** (frozen Thursday morning in the week-6 schedule):

| # | Artifact | Rejection condition |
|---|---|---|
| 1 | Architecture and data-flow diagram | Trust boundaries not marked |
| 2 | SBOM (CycloneDX) | Does not match the deployed image digest |
| 3 | Scan reports with triage rationale | Suppression without written justification |
| 4 | Secrets-management design | Any secret resolvable from the repo |
| 5 | IAM/RBAC matrix | An admin-level grant without justification |
| 6 | Control-to-framework mapping (SOC 2 / ISO 27001) | Fewer than 15 controls mapped |
| 7 | Incident-response plan | No named roles or severity definitions |

**Live defence:** the panel draws 12 questions from a hidden bank of about 30 (categories: supply chain, secrets, identity, data, **AI-specific** such as "what stops a document in our corpus from instructing your model?", compensating controls, evidence). **Pass:** every artifact present and valid; zero critical CVEs (or each explained with a reachability argument and date); no secret resolvable from the repo; every control claim evidenced on demand; compensating controls proposed where a requirement cannot be met; **"I don't know, I will find out by Thursday" scores higher than a fabricated answer** **[Repo: Assessment Pack §4]**. Craft dimensions scored: Security posture, Communication, Judgment. **This gate also carries the midpoint question, "would we put this person in front of a low-risk customer?"** and the midpoint competency re-score **[Sourced: foundation §6.2; R3 §1.2 midpoint gate]**.

### 3.4 G3: AI build (Day 45)

The delivered carried system against a stated business metric: 30-minute trio demo to a *hostile technical evaluator* plus an individual 15-minute technical examination per learner. A 100-question **held-out golden set** (built by someone other than the retrieval tuner) and a separate 50-question dev set; the harness is cold-run by assessors on Thursday.

| # | Criterion | Threshold |
|---|---|---|
| 1 | Faithfulness on the held-out set | **>= 85%** |
| 2 | Context precision | **>= 70%** |
| 3 | Cost per transaction reported | Present and correct within **20%** |
| 4 | Latency at p50 and p99 | Present |
| 5 | LLM judge calibrated to human labels | **TPR and TNR >= 0.85** |
| 6 | Regression suite in CI | **Fails on a deliberately injected prompt regression** |
| 7 | Cross-user leaks on an adversarial ACL set | **0** |
| 8 | Limitations page and error-analysis report | Honest and complete |
| 9 | Architecture justified (why this design, why not an agent/framework) | Assessor-judged |

**Disqualifying conditions:** the metric is met but the learner cannot explain why the architecture was chosen; or the golden set leaked from the tuning documents (the result is void) **[Repo: Assessment Pack §5; Sourced: R5 T5/T6/T21]**. Scored: metric achievement, evaluation rigour, honesty about limitations, cost awareness, architectural justification.

### 3.5 G4: Operate under failure (Day 55)

The five-injection production simulation of the week-11 schedule (compressed; the 24-week plan runs five full days). A role-played customer demands status daily and an executive questions cost on day 3. **Communication is weighted equally with the technical response** **[Repo: Assessment Pack §6]**.

| # | Criterion | Threshold |
|---|---|---|
| 1 | Availability across the window | **>= 99%** |
| 2 | Incidents **self-detected** before the instructor reports them | 5 of 5 (day 4 may be blocked in CI) |
| 3 | Postmortem per incident within 24 h | 5 of 5 |
| 4 | Runbooks complete and executable by another pod | Cold-execution test (Fri, 2.5 h) |
| 5 | Cost report with unit economics, anomaly explained | Present |
| 6 | Customer communication during each incident | Assessor-judged (R5, R6) |

Craft dimensions: Troubleshooting, Execution, Communication, Judgment, Handover. The OWASP LLM01-10 control map is a 24-week G4 requirement and a 12-week *capstone* requirement.

### 3.6 G5: Capstone defence and readiness panel (Day 60)

See §4. Four-person panel (a senior FDE, a security lead, an ML lead, a customer-facing leader); two independently score the nine-dimension craft rubric; inter-assessor delta recorded.

### 3.7 Retake and remediation in this plan

The foundation's policy (§6.6) is *tiered and non-punitive*: first miss = one week of targeted remediation **inside scheduled slack** and a re-assessment on a **parallel task** (same rubric, different environment or fault variant); second miss = a formal growth plan with options (continue conditional, defer to the next cohort at the same gate, or transfer to the other program length); third miss or sustained non-engagement = a fit conversation with a documented exit path. Total cohort time for a completer is capped at **1.25x program length** (15 weeks). Retakes are never unpaid evening or weekend work.

**This plan can only honour that policy where the schedule has slack.** The foundation's phase budget leaves very little in Weeks 7-9. The retake windows that exist are:

| Gate | Retake window in this schedule | Hours | Note |
|---|---|---|---|
| G1 (Day 20) | Week 5 Friday | 1.0 | Parallel task, assessors who did not mark the first attempt |
| G2 (Day 30) | Week 8 Friday | 1.0 (45-min panel) | Two weeks after the gate, not one: Phase C has only 1 h of slack in the foundation's budget |
| G3 (Day 45) | Week 10 Thursday | 1.0 | Parallel business metric and held-out set |
| G4 (Day 55) | **None inside the 12 weeks** | n/a | Proceed to G5 with a documented gap; the gap becomes a *Conditional* condition if the capstone does not close it (a targeted parallel injection day in the post-program remediation window) |
| G5 (Day 60) | **None inside the 12 weeks** | n/a | *Conditional* outcome: 4-6 weeks targeted remediation then a re-defence at a mini-G5 (foundation §6.5) |

Flag this to the sponsor: if retakes are expected to be common, ask the foundation to move slack from Weeks 10-11 earlier (see §8, risk 2).

### 3.8 Readiness outcomes (an internal credential; no vendor certification)

| Outcome | Rule | Next step |
|---|---|---|
| **Ready: Workstream Owner** | L2+ in all six, L3+ in at least three, craft >= 3.5, all gates passed | Shortened shadow stage; owns a workstream on a senior-led engagement |
| **Ready: Supervised** | L2+ in all six, L3 in 1-2, craft >= 3.0 | Paired assignment for about 90 days with a named senior |
| **Conditional** | One domain at L1, or craft 2.5-3.0 | 4-6 weeks targeted remediation then a mini-G5 |
| **Not yet ready** | Multiple gaps | Fit conversation; deferral; documented exit path |

Craft threshold for Workstream Owner is **>= 3.5** (repo); the threshold applies to the mean of all scored dimension-events with no single dimension's mean below 3.0, and each event declares which dimensions it scores **[Judgment: foundation Appendix A #16]**. Composite weights for support and ranking only (outcomes use thresholds): gates 45%, lab checks 20%, craft rubric 20%, portfolio artifacts 10%, peer code-review participation 5% **[Judgment: foundation §6.10]**.

### 3.9 Calibration and gate health

| Metric | Target | Action on breach |
|---|---|---|
| First-attempt pass rate per gate | 70-85% | Below: too steep. Above: too easy |
| Inter-assessor delta (craft) | <= 1.0 | Calibration session before the next gate |
| Stall rule | If > 40% of the cohort stalls at the same point in the same lab | Curriculum defect: owner and fix date logged |
| Lab completion within SLA | >= 80% | Re-scope the lab |
| Competency lift, baseline -> exit | >= 1.5 levels | Review the instruction-to-lab ratio |
| Cohort completion | >= 85% | Review schedule protection |
| Learner-reported readiness | >= 4.0 / 5 | Investigate the phase |

## 4. Capstone (P8) and the G5 defence

### 4.1 Brief and client

**Engagement.** Teams of two (seven teams plus one trio for a cohort of 15) take a brief from the **Linden Claims Services** persona and deliver an end-to-end engagement on the carried system, Monday to Friday of Week 12 (32 project hours Monday-Thursday, G5 on Friday; **[Repo: Handbook Week 12 structure]**). The brief states a business outcome (for example: *cut the time senior adjusters spend finding the right SOP clause; keep data in-region; no cross-department leakage*), a budget, a timeline and constraints, and is deliberately incomplete.

**Client persona (synthetic).** Linden's VP Claims Operations is the sponsor; the CISO delegate blocks on data; the senior adjuster (end user) reveals the truth only to good questions; the compliance officer wants evidence; the outsourced platform manager has a five-day change SLA **[Judgment: foundation §8.1; Repo: Handbook Week 12 example]**.

**Exactly three planted complications** per team, drawn at brief time and never named in advance (family list in W12.3). Three is a hard cap **[Repo]**.

### 4.2 The nine deliverables

| # | Deliverable | Domains | Reject if |
|---|---|---|---|
| 1 | Scoping document with measurable success criteria | D6 | Any criterion is unfalsifiable; no out-of-scope list or riskiest assumption |
| 2 | Architecture document with ADRs and security control mapping | D2, D3, D6 | Fewer than three ADRs, or no response to each complication |
| 3 | Working system deployed via IaC, meeting a stated **eval threshold** | D2, D4 | Thresholds met only on the dev set |
| 4 | CI/CD pipeline **including the eval regression gate** | D2, D4 | The gate does not fail on an injected regression |
| 5 | Observability with SLOs and burn-rate alerts **plus LLM tracing and a cost/latency dashboard** | D2, D5 | Alerts never fire |
| 6 | Security evidence pack: SBOM, scans, IAM matrix, threat model, **OWASP LLM01-10 control map, system card** | D3 | Any of the 10 items unaddressed or unevidenced |
| 7 | Cost model with unit economics | D5 | Not within 20% of the stated target |
| 8 | Operator runbook and handover plan **plus a product-feedback memo** (pattern vs bespoke) | D5, D6 | A cold operator cannot deploy, monitor, roll back and handle two seeded incidents |
| 9 | One-page non-technical executive summary | D6 | Not readable by a non-technical leader in 2 minutes |

### 4.3 Defence format (Friday)

| Block | Duration | Focus |
|---|---|---|
| Presentation | 30 min | The engagement: problem, approach, outcome |
| Technical deep dive | 30 min | The panel selects two deliverables and examines them |
| Adversarial questioning | 20 min | The panel probes the weakest point deliberately |
| Business framing | 10 min | Non-technical explanation to the customer-facing leader |

Preceded by the **handover cold-test** (2 h): each team operates a peer team's system from its pack only and handles two seeded incidents. Two defence rooms run in parallel; teams not defending observe and score with the same rubric (calibration practice). Panel: a senior FDE, a security lead, an ML lead, a customer-facing leader **[Repo: Assessment Pack §7]**.

### 4.4 Scoring and decision

**Capstone weighting (proposed; no public source gives this split) [Sourced: R4 §3.5b, labelled inference by the researcher]:** technical outcome 30% · customer artifacts 30% · handover cold-test 20% · judgment and ownership 20%. This is a *support* weighting for discussion at the panel; the outcome uses the thresholds in §3.8.

| Dimension (craft rubric, 1-5; two independent assessors) | 1 Unacceptable | 3 Competent | 5 Exemplary |
|---|---|---|---|
| Discovery | Accepts the stated problem at face value | Asks clarifying questions, finds main constraints | Surfaces the unstated business driver and reframes |
| Scoping | Vague or unfalsifiable criteria | Measurable criteria, explicit out-of-scope | Tied to a metric the customer is accountable for |
| Architecture | Copies the reference design | Sound design fitting the constraints | Adapts to the customer's operating capability |
| Execution | Blocked repeatedly | Working system on schedule | Early; anticipates blockers |
| Troubleshooting | Random changes | Systematic isolation | Fixes the class of problem |
| Security posture | Afterthought | Baseline controls with evidence | Pre-empts the reviewer's objections |
| Communication | Jargon-heavy, buries the lede | Clear, audience-appropriate | Adjusts register per stakeholder; bad news lands well |
| Judgment | Escalates too late or never | Escalates appropriately | Calibrated risk calls; knows what to refuse |
| Handover | Customer cannot operate it | Runbooks exist and are usable | Customer team genuinely self-sufficient |

**Decision rule.** The panel confirms the readiness outcome of §3.8. A **Conditional** result lists exactly which domains or criteria are open, with a re-defence date inside the 1.25x time cap (15 weeks) where possible. Outcomes are communicated within two working days of the panel.

## 5. Lab catalogue and fault library

### 5.1 Lab catalogue

All labs, in ID order. Hours are the **total scheduled** across every segment that carries the lab's ID (including Customer Lab retries). IDs are `W{week}-L{n}`, assigned in order of first appearance. There is **no hard-coded "lab count" target** (foundation Appendix A #4): the repo's 42/44/45 figures are not reused; this plan has 107 labs of 272.5 h in total, most 1.5-3 h, because the 12-week format favours many short, auto-checkable exercises.

| ID | Lab | Domain | Weeks scheduled | Hours | Blocks | AI-eval / fault / customer flag |
|---|---|---|---|---|---|---|
| `W1-L1` | Shell, git and the PR loop | D1 | 1 | 4 | SWF |  |
| `W1-L2` | Linux and the network from the shell | D1 | 1 | 2 | SWF | FAULT: NET-PROXY (variant) |
| `W1-L3` | Typed Python CLI with pytest | D1 | 1 | 2 | SWF |  |
| `W1-L4` | AWS first steps by hand | D2, D3 | 1 | 2.5 | CLD | FAULT: SEC-ROOT (seeded) |
| `W1-L5` | Debugging and code quality | D1 | 1 | 2 | SWF |  |
| `W1-L6` | Serverless 'hello' by hand | D2 | 1 | 1.5 | CLD |  |
| `W1-L7` | Docker 101 | D2 | 1 | 2.5 | DEV |  |
| `W1-L8` | Secrets and least privilege | D3 | 1 | 1.5 | SEC | FAULT: SEC-SECRETS (seeded) |
| `W1-L9` | Customer Lab 1: what an FDE is; the Mom Test; first discovery call | D6 | 1,2 | 3.5 | CUS | CUSTOMER (R1) |
| `W2-L1` | Resilient API client | D1 | 2 | 2 | SWF |  |
| `W2-L2` | VPC by hand | D2 | 2 | 2.5 | CLD |  |
| `W2-L3` | Linux ops: services, permissions, logs | D1 | 2 | 2 | SWF |  |
| `W2-L4` | Containerise, scan and push to ECR | D2 | 2 | 3 | DEV |  |
| `W2-L5` | EC2 + instance profile + S3 | D2, D3 | 2 | 2 | CLD | FAULT: SEC-UNENCRYPTED (seeded) |
| `W2-L6` | GitHub Actions pipeline with OIDC | D2, D3 | 2 | 2 | DEV |  |
| `W2-L7` | Customer Lab 2: stakeholder map and problem statement | D6 | 2 | 2 | CUS | CUSTOMER (R1, R2) |
| `W2-L8` | CI quality and security gates | D2, D3 | 2 | 2.5 | DEV |  |
| `W2-L9` | Bounded concurrency and checkpointing | D1 | 2 | 2 | SWF |  |
| `W2-L10` | Terraform first steps | D2 | 2 | 2 | DEV |  |
| `W2-L11` | ALB + auto-scaling group | D2 | 2 | 2.5 | CLD |  |
| `W2-L12` | Breakage 0: network faults (instructor-driven) | D1, D2 | 2 | 2 | SWF | FAULT: NET-DNS, NET-CA, NET-IPV6 |
| `W3-L1` | SQL and data modelling for Kestrel exceptions | D1 | 3 | 2 | SWF |  |
| `W3-L2` | RDS Postgres: private, backed up, restorable | D2 | 3 | 2 | CLD |  |
| `W3-L3` | Terraform modules and remote state | D2 | 3 | 3.5 | DEV |  |
| `W3-L4` | ECS Fargate service behind an ALB (by hand) | D2 | 3 | 2 | CLD |  |
| `W3-L5` | IAM least privilege: policy simulator and Access Analyzer | D3 | 3 | 1 | SEC | FAULT: SEC-RBAC (seeded) |
| `W3-L6` | Terraform the whole stack | D2 | 3 | 3.5 | DEV |  |
| `W3-L7` | API design: resources, pagination, idempotency, errors | D1 | 3 | 2.5 | SWF |  |
| `W3-L8` | Event-driven mini-pipeline | D2 | 3 | 1.5 | CLD |  |
| `W3-L9` | Kubernetes intro on kind | D2 | 3 | 3 | DEV |  |
| `W3-L10` | Image and IaC scanning in CI | D3 | 3 | 1 | SEC |  |
| `W3-L11` | Customer Lab 3: scope document / PR-FAQ and scope negotiation | D6 | 3,4 | 3 | CUS | CUSTOMER (R2, R6) |
| `W4-L1` | The report that is always wrong (mini) | D1 | 4 | 3 | SWF | DATA-QUALITY (silent-encoding case; full DATA-* faults are 24-week only) |
| `W4-L2` | Observability on AWS: logs, metrics, dashboard, alarm | D2, D5 | 4 | 2.5 | CLD |  |
| `W4-L3` | Three SLOs with burn-rate alerts as code | D2, D5 | 4 | 2.5 | DEV |  |
| `W4-L4` | Breakage 1 (coach mode): crash loops and image pulls | D2 | 4 | 3 | DEV | FAULT: K8S-CRASHLOOP, K8S-IMGPULL |
| `W4-L5` | Cost controls and tagging | D2 | 4 | 2 | CLD |  |
| `W4-L6` | Customer Lab 4: status update and bad-news call | D6 | 4 | 1.5 | CUS | CUSTOMER (R5, R6) |
| `W4-L7` | Terraform in CI: plan on PR, apply on merge, drift | D2 | 4 | 2.5 | DEV | FAULT: IAC-DRIFT |
| `W4-L8` | ECS target-tracking autoscaling | D2 | 4 | 1 | CLD |  |
| `W4-L9` | Dependency scanning and threat model (lite) | D3 | 4 | 1.5 | SEC | FAULT: SEC-NETPOL-OPEN (variant) |
| `W4-L10` | G1 practice run (timed, fresh sandbox) | D2 | 4 | 1.5 | SLK | FAULT: IAC-DRIFT (variant) |
| `W5-L1` | Tokens, embeddings and nearest-neighbour search | D4 | 5 | 2 | AIC |  |
| `W5-L2` | LLM vs classifier bake-off | D4 | 5 | 2.5 | AIC | AI-EVAL |
| `W5-L3` | SAST in the pipeline (Semgrep) | D3 | 5 | 1.5 | SEC |  |
| `W5-L4` | Batch an LLM job: async, retries, checkpoints | D1, D4 | 5 | 2.5 | AIC | AI-EVAL |
| `W5-L5` | Messy CSV to validated Parquet module | D1, D4 | 5 | 2.5 | AIC |  |
| `W5-L6` | SCA and a signed-style SBOM | D3 | 5 | 1.5 | SEC |  |
| `W5-L7` | Wrap the LLM function as a FastAPI service | D1, D4 | 5 | 2 | AIC |  |
| `W5-L8` | Structured extraction: prompt-only vs schema-constrained | D4 | 5 | 2.5 | AIC | AI-EVAL |
| `W5-L9` | Breakage 2 (guide on the side): OOM and HPA with no metrics | D2 | 5 | 1.5 | DEV | FAULT: K8S-OOM, K8S-HPA-NOMETRICS |
| `W5-L10` | Prompt A/B on a held-out set | D4 | 5 | 3 | AIC | AI-EVAL |
| `W5-L11` | DAST against OWASP Juice Shop | D3 | 5 | 1.5 | SEC |  |
| `W5-L12` | Breakage 2b: DNS blocked by NetworkPolicy and unschedulable pod | D2 | 5 | 2 | DEV | FAULT: K8S-NETPOL-DNS, K8S-PENDING-GPU |
| `W5-L13` | IaC scanning and policy as code | D3 | 5 | 1.5 | SEC |  |
| `W5-L14` | Customer Lab 5: decomposition and first Linden contact | D6 | 5,6 | 3 | CUS | CUSTOMER (R3, R1) |
| `W6-L1` | Break-it lab: schemas and malformed inputs | D4 | 6 | 2.5 | AIC | AI-EVAL |
| `W6-L2` | Hand-written tool loop (no framework) | D4 | 6 | 3 | AIC |  |
| `W6-L3` | Tool-description tuning | D4 | 6 | 1.5 | AIC | AI-EVAL |
| `W6-L4` | A safe write tool | D4, D3 | 6 | 1 | AIC |  |
| `W6-L5` | Error-analysis sprint | D4 | 6 | 3 | AIC | AI-EVAL; FAULT: RAG-FAIL (taxonomy seeds) |
| `W6-L6` | Assertions first: 20 cases for the Week-1 service | D4 | 6 | 1.5 | AIC | AI-EVAL |
| `W6-L7` | Lethal-trifecta audit and injection basics | D3, D4 | 6 | 3.5 | AIO | AI-SEC |
| `W6-L8` | Customer Lab 6: security-review conduct | D6 | 6 | 2 | CUS | CUSTOMER (R7) |
| `W6-L9` | Security-review rehearsal (G2 mock) | D3, D6 | 6 | 5 | SEC |  |
| `W6-L10` | Wheel of Misfortune #1 (blameless incident drill) | D2, D5 | 6 | 2 | DEV | FAULT: GAMEDAY, APP-RACE, NET-MTU |
| `W7-L1` | Baseline RAG over a 200-document corpus | D4 | 7 | 3.5 | AIC | FAULT: RAG-FAIL (taxonomy) |
| `W7-L2` | Parsing messy documents (tables, HTML, DOCX, scans) | D4 | 7 | 2 | AIC | FAULT: RAG-FAIL (taxonomy) |
| `W7-L3` | Retrieval ablation | D4 | 7 | 4 | AIC | AI-EVAL |
| `W7-L4` | Access-controlled RAG | D4, D3 | 7 | 3 | AIC | FAULT: RAG-ACL |
| `W7-L5` | Tracing the RAG app (Langfuse or Phoenix) | D5 | 7 | 3 | AIO | AI-EVAL |
| `W7-L6` | Grounded answers: citations, abstention, stuff-vs-retrieve | D4 | 7 | 2.5 | AIC | AI-EVAL |
| `W7-L7` | Golden set and CI regression gate | D4 | 7 | 5 | AIC | AI-EVAL; FAULT: LLM-REGRESS |
| `W7-L8` | Customer Lab 7: JTBD interview and defining "good" | D6 | 7,8 | 3.5 | CUS | CUSTOMER (R1, R3) |
| `W8-L1` | Workflow vs agent bake-off | D4 | 8 | 4 | AIC | AI-EVAL |
| `W8-L2` | Build an MCP server | D4 | 8 | 3 | AIC |  |
| `W8-L3` | MCP authorisation: scoped tokens, no passthrough | D3, D4 | 8 | 2 | AIC | FAULT: MCP-TOKEN |
| `W8-L4` | Threat-model a third-party MCP server | D3 | 8 | 1.5 | AIC | AI-SEC |
| `W8-L5` | Calibrating an LLM judge | D4 | 8 | 5 | AIC | AI-EVAL |
| `W8-L6` | Customer Lab 8: demo craft and honest capability framing | D6 | 8 | 2 | CUS | CUSTOMER (R4) |
| `W8-L7` | Bounded agent with approvals and crash-resume | D4, D3 | 8 | 4 | AIC |  |
| `W8-L8` | Human-in-the-loop flow with a feedback flywheel | D5, D4 | 8 | 3 | AIO |  |
| `W8-L9` | Breakage 2 on the carried system: provider failure and context overflow | D5, D4 | 8 | 2.5 | PRJ | FAULT: LLM-PROVIDER, LLM-CTX |
| `W9-L1` | Outcome and trajectory evals for the carried-system agent | D4, D5 | 9 | 5 | AIC | AI-EVAL |
| `W9-L2` | Context-budget audit | D4 | 9 | 2 | AIC | AI-EVAL |
| `W9-L3` | Cache-friendly prompt layout | D4, D5 | 9 | 2 | AIC | AI-EVAL |
| `W9-L4` | Fine-tune vs RAG vs prompting: decision memos | D4 | 9 | 3 | AIC |  |
| `W9-L5` | Reliability harness: 429s, timeouts, malformed replies | D5 | 9 | 1.5 | AIO | FAULT: LLM-PROVIDER (variant) |
| `W9-L6` | Hosted vs local open model on the same eval | D5, D4 | 9 | 3 | AIO | AI-EVAL |
| `W9-L7` | Customer Lab 9: hostile technical evaluator and executive brief (G3 rehearsal) | D6 | 9 | 2.5 | CUS | CUSTOMER (R4, R5, R6) |
| `W9-L8` | Layered guard stack | D3, D5 | 9 | 3 | AIO | AI-SEC |
| `W10-L1` | OIDC login with per-user retrieval ACLs | D3, D6 | 10 | 3 | AIO | FAULT: RAG-ACL (token-claim variant) |
| `W10-L2` | Connector to a messy source | D1, D6 | 10 | 2 | AIO |  |
| `W10-L3` | Scoping-sprint discovery calls (3 vague prospects) | D6 | 10 | 1.5 | CUS | CUSTOMER (R1, R2) |
| `W10-L4` | Deploy the AI service (Helm on kind; ECS variant) | D5, D2 | 10 | 4 | AIO |  |
| `W10-L5` | Legacy batch adapter (SFTP/SOAP -> typed API and MCP tool) | D1, D6 | 10 | 2 | AIO |  |
| `W10-L6` | Customer Lab 10: the living client | D6 | 10 | 3 | CUS | CUSTOMER (R6, R9) |
| `W10-L7` | Air-gapped and residency-constrained deployment | D3, D2 | 10 | 5 | PRJ | FAULT: FIELD-AIRGAP, FIELD-BLIND |
| `W10-L8` | Incremental document-sync pipeline | D5, D1 | 10 | 1.5 | AIO |  |
| `W10-L9` | Red/blue game day on peer systems | D3, D5 | 10 | 3.5 | AIO | FAULT: AI-INJECT-INDIRECT, AI-INJECT-TOOL |
| `W11-L1` | Cost and latency optimisation | D5, D4 | 11 | 3.5 | AIO | FAULT: LLM-COSTBURN |
| `W11-L2` | Scoping sprint: round-2 call with the chosen prospect | D6 | 11 | 1 | CUS | CUSTOMER (R1, R2) |
| `W11-L3` | G4 production simulation: five injected failures (on-call windows) | D5, D3, D2 | 11 | 9.5 | SLK | FAULT: PROD-SIM (provider outage, poisoned document, 10x spike, prompt regression, 6x cost burn) |
| `W11-L4` | Data-flow diagram, DPIA-lite, PII redaction, deletion | D3 | 11 | 3.5 | AIO |  |
| `W11-L5` | Customer Lab 11: adversarial three-stakeholder panel | D6 | 11 | 1.5 | CUS | CUSTOMER (R2, R9) |
| `W11-L6` | System card for the carried system | D3, D4 | 11 | 2 | AIO |  |
| `W11-L7` | Customer Lab 12: communicating under incident | D6 | 11 | 2 | CUS | CUSTOMER (R5, R6) |
| | **107 labs in total** | | | **272.5** | | |

**Reconciliation.** The 272.5 lab hours above are a subset of the 480 h. The remainder is instruction, projects (the 84 h Projects block), customer simulation not tied to a numbered lab, assessment, onboarding and slack; see the activity-mix table in §1.6 and the week-by-week schedules in Part II. Lab hours by budget block are in the catalogue's *Blocks* column; block totals are verified in §1.3.

### 5.2 Fault library: 32-scenario 12-week subset

The foundation's **v2 fault library has 40 scenarios (32 inherited and renumbered + 8 new); the 12-week program uses the 32-scenario subset** (foundation §9.6). Scenarios are keyed by **stable names, never by numeric lab ID** (the repo's lab IDs collide). Every fault has occurred in a real engagement or a documented real failure class; has 3-5 variants randomly assigned per learner; resets in under 5 minutes (the air-gap lab is the exception, at about 20 minutes); is defined in Terraform or Kustomize; and ships a README with Symptom, Root cause, Expected diagnostic path, **Known stall points (enumerated)**, Real-world provenance and a one-line reset command **[Repo: Ops Guide §3]**.

| # | Scenario | Used in | Gate use |
|---|---|---|---|
| 1 | `NET-PROXY` | `W1-L2` |  |
| 2 | `NET-CA` | `W2-L12` |  |
| 3 | `NET-DNS` | `W2-L12` |  |
| 4 | `NET-MTU` | `W6-L10` |  |
| 5 | `NET-IPV6` | `W2-L12` |  |
| 6 | `APP-RACE` | `W6-L10` |  |
| 7 | `IAC-DRIFT` | `W4-L7`, `W4-L10` | G1 (randomised variant) |
| 8 | `K8S-IMGPULL` | `W4-L4` |  |
| 9 | `K8S-CRASHLOOP` | `W4-L4` |  |
| 10 | `K8S-PENDING-GPU` | `W5-L12` |  |
| 11 | `K8S-OOM` | `W5-L9` |  |
| 12 | `K8S-NETPOL-DNS` | `W5-L12` |  |
| 13 | `K8S-HPA-NOMETRICS` | `W5-L9` |  |
| 14 | `GAMEDAY` | `W6-L10` |  |
| 15 | `SEC-ROOT` | `W1-L4` |  |
| 16 | `SEC-SECRETS` | `W1-L8` |  |
| 17 | `SEC-RBAC` | `W3-L5` |  |
| 18 | `SEC-NETPOL-OPEN` | `W4-L9` |  |
| 19 | `SEC-UNENCRYPTED` | `W2-L5` |  |
| 20 | `AI-INJECT-INDIRECT` | `W10-L9` | G4 (day 2 variant) |
| 21 | `AI-INJECT-TOOL` | `W10-L9` | G5 complication option |
| 22 | `MCP-TOKEN` | `W8-L3` |  |
| 23 | `RAG-FAIL` | `W6-L5`, `W7-L1`, `W7-L2` |  |
| 24 | `RAG-ACL` | `W7-L4`, `W10-L1` | G3 (adversarial ACL set) |
| 25 | `LLM-REGRESS` | `W7-L7` | G3 (injected regression) |
| 26 | `LLM-CTX` | `W8-L9` |  |
| 27 | `LLM-PROVIDER` | `W8-L9`, `W9-L5` | G4 (day 1) |
| 28 | `LLM-COSTBURN` | `W11-L1` | G4 (day 5) |
| 29 | `PROD-SIM` | `W11-L3`, G4 (Days 51-55) | G4 |
| 30 | `FIELD-AIRGAP` | `W10-L7` | G5 complication option |
| 31 | `FIELD-BLIND` | `W10-L7` | G5 complication option |
| 32 | `G0-LAYERED` | G0 practical (Day 2) | G0 |

**The 8 scenarios deferred to the 24-week library:** `K8S-WEBHOOK-CERT`, `K8S-PVC-TERM`, `K8S-DISKPRESSURE`, `K8S-WEBHOOK-REJECT`, `EVAL-JUDGE`, `ML-LEAKAGE`, `DATA-SKEW`, `DATA-SILENT` (foundation §9.6). Two of the 12-week labs *teach the concept* of a deferred scenario without using it as a fault (`W4-L1` for `DATA-SILENT`; `W8-L5` for `EVAL-JUDGE`).

**Build order [Repo: T-8 to T-1; Assumption on effort]:** build all 32 by T-8 weeks except the AI-dependent ones (`RAG-*`, `LLM-*`, `AI-INJECT-*`, `MCP-TOKEN`, `PROD-SIM`), which need the RAG corpus (T-4) and tracing in place. This is the largest pre-launch effort (foundation §11.2).

## 6. Weekly telemetry, measurement and the pilot

The first cohort is a **measured pilot, not a launch** (foundation §12.4): most customer-skill and gating choices rest on practitioner consensus, not controlled evidence.

### 6.1 What is captured (six layers, adapted from the repo)

| Layer | What | When | Where |
|---|---|---|---|
| 1 Competency | L0-L4 per domain (`d1_swe ... d6_craft`) by two assessors | Day 2, Day 30 (G2 midpoint), Day 60 | Working-plan workbook |
| 2 Lab telemetry | One row per learner per lab attempt: `time_to_first_signal`, `stall_point` (enumerated per fault), `hints_taken`, plus **AI fields** `eval_pass_rate`, `trace_url`, `cost_per_run`, `prompt_version`, `model_config_id` (never a hard-coded model name), `judge_tpr_tnr` | Every lab | Workbook / sandbox |
| 3 Gates | Attempt, result, assessors, delta | Each gate | Workbook |
| 4 Craft rubric | Nine dimensions, two assessors, scored events declared per gate | G2, G4, G5 | Workbook |
| 5 Programme health | Pass rate, stall rate, completion, cost per learner, GPU utilisation, instructor hours per learner-week | Weekly | Workbook |
| 6 Outcomes | Day-90 supervisor rating; 30-day and 6-month learner and manager surveys | After the program | Survey tool |

The repo's Working Plan Workbook (10 sheets) is the model for the workbook **[Repo]**. The schedule in Part II is generated from structured data and can be exported to the 60-day plan sheet. **Fix before reuse:** one start-date cell drives *all* dates (Day 1 = start date) so the instructor and student workbooks cannot drift by up to a week (foundation Appendix A #7-8).

### 6.2 Weekly data pull (instructor checklist)

1. Friday 16:30: stall points per lab (count by enumerated value; flag any lab with > 40% at one point).
2. Hours actually logged vs 40 scheduled (median target <= 44).
3. Weekly anonymous pulse (stress, load, belonging): reviewed within 48 h.
4. Cost per learner (AWS + LLM) against the $500/month cap; GPU utilisation (target 60-85%).
5. Early-warning indicators: missed check-ins, falling retrieval-quiz scores, rising stall time -> supportive outreach, not a penalty.
6. Update the ILP and the curriculum-defect log (owner, fix date).

### 6.3 Hypotheses this 12-week pilot should test

| # | Hypothesis | How to test | Decision rule |
|---|---|---|---|
| H1 | The Weeks 7-9 AI load (63 h of AI Core + projects) is survivable | Stall rate per lab; hours logged; pulse | If > 40% stall at one point twice, move T9/T10 to reading or defer `W7-L3` half; revisit foundation §7.6 |
| H2 | One lab per concept with an eval gives measurable D4 growth | D4 baseline -> Day 60 lift; G3 first-attempt pass rate | Lift >= 1.5 levels; pass rate 70-85% |
| H3 | The customer thread produces a measurable gain | Same persona type at G0 (mock call) and G5, blind double-marked; R1-R9 deltas between an early (Week 2) and a late (Week 10) Customer Lab | A positive delta >= 1 level on discovery and scoping; otherwise revise the thread **[Judgment: foundation §12.4]** |
| H4 | A compressed, work-alongside G4 is a valid proxy for a five-day simulation | Compare G4 outcomes with Day-90 supervisor ratings; interview assessors | If G4 passers fail in the field on operations, extend G4 |
| H5 | The retake windows are enough | Number of Conditional outcomes after G2/G3; retake pass rate | If > 20% need a retake with no slack, ask the foundation to move slack earlier |
| H6 | The lane thresholds route learners well | Lane vs final D1/D2/D4/D5 | Recalibrate thresholds |
| H7 | Trios of mixed baseline help | Pairing data; learner survey | Keep or re-pair |
| H8 | The foundation hours are accurate | Lab SLA completion; actual vs scheduled hours | Re-scope any lab with < 80% SLA completion |

### 6.4 Decision after the pilot

Adopt, adjust or cut each element using the thresholds above. The elements most deserving scrutiny: the 40-hour weeks 7-9, the customer thread's measured effect, the 15-learner / 1:8 staffing assumption, the compressed G4, and the retake windows **[Judgment: foundation §12.4]**. Publish cohort outcomes with **full denominators** and pre-declared definitions of "ready" (foundation P18; the CFPB action against one bootcamp shows the failure mode **[Sourced: R3 §3]**).

## 7. Preparation and checklists

### 7.1 Pre-program prep for learners (light; sent four weeks before Day 1)

About 8 hours in total: **setup helps, cramming hurts** (it inflates the Day-2 baseline and the distortion costs the learner for twelve weeks) **[Repo: Prep Guide, Student Handbook]**.

| Item | Detail | Time |
|---|---|---|
| Hardware | 16 GB RAM, 100 GB free disk | n/a |
| Accounts | GitHub, SSO to the AWS sandbox org, LLM gateway key, SSH key, VPN if needed | ~1.5 h |
| Toolchain | Install: `git`, `docker`, `kubectl`, `helm`, `terraform`, `python3`, `uv`, `aws` (CLI). `make verify` in the starter repo returns a version for **all eight** | ~2.5 h |
| `make verify` | Smoke test of the toolchain plus an AWS profile check; also proves the gateway key works | ~0.5 h |
| Cohort contract | Signed; manager signature if employer-sponsored; calendar blocked; on-call duties removed | ~0.5 h |
| Light reading | Missing Semester lectures 1-3 (shell, environment, dev tools) https://missing.csail.mit.edu/ ; the Week 1-2 outline of this plan | ~3 h |

The repo's Prep Guide says "all eight commands" but lists seven; this checklist lists eight explicitly **[Repo defect, Appendix A #20]**. **Do not** ask learners to study AI topics in advance. Optional reading is allowed but no graded work depends on it.

### 7.2 Accounts and tooling readiness (program staff, T-minus)

| Item | Owner | Due | Verify |
|---|---|---|---|
| AWS Organization, cohort OU, per-learner accounts, SCP deny-list (region lock; instance-type caps; NAT gateways, large GPU and EKS control planes denied by default), tag-on-create | Lab engineer | T-6 | A learner role cannot launch a denied resource **[Judgment: foundation §9.2]** |
| Budgets with actions at 50/80% + weekly review; nightly aws-nuke (dry-run first) on non-persistent resources | Lab engineer | T-6 | Dry-run lists only learner-tagged resources; verify aws-nuke's safety features on the current release (the fetched README did not show them **[Sourced: R2 §3.3]**) |
| LLM gateway with per-learner spend caps; two endpoints (hosted Claude default; OpenAI-compatible hosted/local) | Lab engineer | T-4 | Caps tested; Ollama fallback works on a learner laptop |
| Tracing backend (Langfuse or Phoenix; one per cohort) | Lab engineer | T-3 | A trace shows prompt version, tokens, cost |
| Identity for labs (Keycloak or an Auth0/Entra test tenant) | Lab engineer | T-3 | OIDC login works for 15 learners |
| Air-gapped VPC (no egress route at all), registry and package mirrors, pre-staged model weights and embedding model, offline vector DB | Lab engineer | T-4 | Pull from the mirror succeeds; any outbound call fails |
| RAG corpus: ~200-doc starter and 5,000-doc synthetic main set (40% clean PDFs, 30% scans, 20% spreadsheets, 10% HTML/DOCX); 100-question held-out golden set built by a **different person** from whoever tunes retrieval; 50-question dev set | Lab engineer + a labeller | T-4 | Provenance recorded per document; golden set not visible to learners |
| Fault library: the 32-scenario subset (§5.2) | Lab engineer | T-8 (AI-dependent ones after the corpus) | Each fault resets in < 5 min and has an enumerated stall-point list |
| Rubrics calibrated on recorded examples; client-actor scripts and hidden-fact sheets (Kestrel COO, warehouse supervisor, finance analyst, IT lead; Linden VP, CISO delegate, senior adjuster, compliance officer, platform manager, hostile technical lead) | Customer-craft coach | T-2 | Two assessors within delta 1.0 on a recorded sample |
| Starter repo `fde-academy-starter` with the LLM client, the Week-1 service template and `make verify` | Lead instructor (platform) | T-3 | Fresh clone passes `make verify` on all supported laptops |

**Pre-launch build effort [Assumption: foundation §11.2]:** fault library about 4-6 FTE-weeks for the 32 (largest item); RAG corpus 2-3; AWS org and nuke pipeline about 2; rubric calibration and actor scripts about 2; workbook and telemetry 1-2.

### 7.3 Instructor and assessor preparation per week

| Week | Prepare before Monday |
|---|---|
| 1 | Starter repo and `make verify`; G0 exam (60 Qs), `G0-LAYERED` environments, mock-call actors (3 in parallel); lane formula in the workbook; cohort-contract originals; wellbeing norms briefing |
| 2 | VPC and OIDC trust-policy skeletons; `NET-DNS`/`NET-CA`/`NET-IPV6` breakage environments; first retrieval quiz (5 items) |
| 3 | RDS and Terraform base modules; seeded IAM over-broad policies; Kestrel IT-lead and COO scripts incl. the WhatsApp change request |
| 4 | SLO calculator sheet; `K8S-CRASHLOOP`/`K8S-IMGPULL` variants; **G1**: fresh sandboxes, randomised `IAC-DRIFT` variants, assessor roster, screen recording; G1 retake task for Week 5 |
| 5 | Semgrep/ZAP/Trivy/Checkov/OPA images; 300-ticket and 100-doc datasets; `K8S-OOM`, `K8S-HPA-NOMETRICS`, `K8S-NETPOL-DNS`, `K8S-PENDING-GPU`; Linden persona scripts; G1 retake assessors |
| 6 | Mock-panel rosters (two compositions); 60-trace support-bot set; three agent architectures for the trifecta audit; G2 hidden question bank (~30) and rubric; Wheel of Misfortune scenario (`GAMEDAY`, `APP-RACE`, `NET-MTU`); **G2 panels** (2 assessors each) |
| 7 | 200-doc starter corpus + Linden subset; dev set; tracing backend; golden-set harness for CI; JTBD actors; retake plan |
| 8 | Mock internal API for tools and MCP; MCP Inspector; judge-labelling sheets; review UI; `LLM-PROVIDER`/`LLM-CTX` injections; **G2 retake** assessors |
| 9 | 100-question held-out harness (cold-run Thursday); hostile technical evaluator brief; local model images; red-team set (50 benign / 50 attack); **G3** assessors (2 per exam) |
| 10 | Keycloak realm; mock legacy SFTP/SOAP system; air-gap VPC; red/blue scenarios; three prospect personas; living-client script; **G3 retake** assessors |
| 11 | **G4 injection scripts for five days** with randomised variants and unannounced times; role-played customer and executive; runbook cold-test pairings; P7 panel actors |
| 12 | G5 briefs with three-complication draw; panel of four; two rooms; seeded incidents for the cold-test; outcome-decision template |

### 7.4 Policy decisions needed from the sponsor before launch

1. **AI-assisted coding policy** *(the research does not settle it)*: this plan assumes AI coding tools are **allowed in labs and projects with disclosure** and **disallowed in G0, G1 and the G2/G3 oral components** (which test recall and reasoning), but the sponsor should decide. The MIT Missing Semester 2026 edition folds agentic coding into its lectures **[Sourced: R2 §1.1]**.
2. Whether learners may keep their sandboxes' IaC and projects as portfolio items (licence and customer-data boundary: all data is synthetic).
3. Who plays clients (staff, alumni or paid actors) and how many actor-hours the budget supports (about 1 actor-hour per pod-hour of simulation **[Assumption: foundation §8.4]**).

## 8. Risks, the Day-60 graduate, and the Day 61-90 ramp

### 8.1 Risks specific to the compressed 12-week format

The foundation's full register (§12.1) applies; these are the ones this schedule makes sharper.

| # | Risk | Why it is sharper here | Mitigation | Basis |
|---|---|---|---|---|
| 1 | **Weeks 7-9 AI overload**: 63 h of AI Core plus 24 project hours in three weeks, 1 h of slack in total | The most likely place for a >40% stall (foundation risk 1) | Pre-work in Weeks 5-6 (T1-T4 done before Week 7); defer the lowest-value half of `W7-L3` and move T9/T10 to reading if the stall rule fires; keep P5/P6 scope small | [Judgment] |
| 2 | **No slack for retakes in Weeks 7-9**, and none at all for G4/G5 | The tiered retake policy (foundation §6.6) assumes scheduled slack; the phase budget provides 1 h in Phase C | Explicit retake windows (§3.7); G4/G5 misses route to *Conditional*; ask the sponsor to rebalance slack from Weeks 10-11 into Weeks 7-9 if the pilot shows retakes are needed | [Judgment] |
| 3 | **Compressed G4**: five injections run *alongside* normal work, not a dedicated five days | Validity as a proxy for a real operating week is untested | Hypothesis H4; keep the role-played customer and the cold-execution test; consider extending G4 if Day-90 ratings disagree | [Judgment] |
| 4 | **Foundation depth is thin**: 36 h of AWS, 12 h of Kubernetes, 12 h of Terraform | Learners meet each tool once; L2 not L3 in D2 | Reuse the same Kestrel stack across Weeks 2-4 and G1; make the capstone IaC-first; state plainly that D2 exits at L2 | [Judgment] |
| 5 | **Teams of two in the capstone** may hide a weak member | Four days, shared deliverables | Individual technical examination in G3; individual readiness conversation in G5; joint daily integration; per-learner commit and review telemetry | [Judgment] |
| 6 | **Burnout** in the heaviest weeks | 40 scheduled hours but real load tends to exceed schedule | No required work after 17:45 or at weekends; weekly pulse; Week-5/6 and Week-11 slack; named wellbeing lead; log actual hours (median <= 44) | [Sourced: R3 §3] |
| 7 | **Cost overrun** from AI labs and agent loops | 15 learners x 12 weeks with batch jobs and open-model experiments | Gateway spend caps; layered AWS controls (Budgets are not an instant cap); `LLM-COSTBURN` taught before G4 | [Sourced: R2 §3.3; Judgment] |
| 8 | **Tool churn** (MCP revision, SDK status, acquisitions, model names, EU AI Act dates) | Labs and slides go stale quickly | Model IDs in config; teach concepts plus a thin SDK; re-verify the flags at T-4 | [Sourced: R5 flags] |
| 9 | **Fault-library readiness** | 32 scenarios, many AI-dependent, by T-4/T-8 | Build the platform subset first; gate the AI subset on the corpus; do not start the cohort without G0, G1, `K8S-*` and `PROD-SIM` tested | [Repo; Assumption] |
| 10 | **Customer-skill methods unproven** | No independent evidence the methods improve FDE outcomes | Hypothesis H3; teach few frameworks and practise many; blind double-marking | [Sourced: R4 §3.6, §5] |
| 11 | **Retake/Conditional load** concentrated at the end | G4 and G5 have no in-program retake | A clear Conditional pathway and a post-program remediation window; communicate the rule in Week 1 | [Judgment] |
| 12 | **Baseline variance** among new grads | A weak D1/D2 learner struggles in Weeks 3-5 | Lanes from G0; mixed trios; fast-track tasks; ILP follow-up in Week 3 and Week 6 | [Repo; Sourced: R3] |

### 8.2 What a graduate can and cannot do at Day 60

**Caveat: reasoned estimate; no public company benchmark exists for new-grad FDE performance [Judgment, informed by R4 §4].**

| Can do (typically at L2, D4 at L3) | Cannot yet do reliably |
|---|---|
| Run a structured 30-45 min discovery call with a friendly contact and write a one-page scope a senior FDE accepts with edits | Own a strategic account or be the sole technical voice with executives |
| Build and deploy a contained, tested piece (integration, pipeline, LLM workflow with an eval set) under code review; debug a deploy from logs | Negotiate scope, price or timelines without senior review |
| Build RAG and a bounded agent with evals, traces and a regression gate; report a number, not a vibe | Architect a multi-system AI solution under heavy constraints |
| Deliver a rehearsed demo on realistic data and answer "what are the limits?" honestly | Navigate regulated procurement, accreditation or politics alone |
| Write answer-first status updates and a runbook a cold operator can follow | Diagnose ambiguous failures in an unfamiliar customer environment without help |
| Recognise security and compliance constraints and escalate | Decide alone when a customer request should be refused |

The 12-week graduate is *ready to start under supervision*; the 24-week graduate is *near-independent on routine engagements* (foundation §2.5).

### 8.3 Recommended Day 61-90 on-the-job ramp

The program does not own this stage; it recommends it **[Judgment]**. The foundation's field transition (shadow -> reverse shadow -> solo with backstop -> independent **[Repo: Handbook §7]**) is applied to a 30-day window, with the research's ramp shape as a loose guide (weeks 1-2 shadowing; 3-4 small scoped work; the "wall" in weeks 5-8 tests judgment; a first visible win by week 12; an unsourced vendor generalisation **[Sourced: R4 §4]**).

| Days | Stage | Expectation |
|---|---|---|
| 61-70 | **Shadow**: sit in on two engagements with a named senior FDE; keep a field-notes log (pattern vs bespoke) | Attend discovery and review meetings; write the status update afterwards for the senior to correct |
| 71-80 | **Reverse shadow**: lead part of two engagement activities with the senior observing and not intervening unless safety requires | Run a discovery call or a demo; the senior gives feedback within 24 h |
| 81-90 | **Own a contained workstream** under supervision (an integration, an eval set, a runbook) with a backstop | A shipped, reviewed piece; a 30-minute retrospective with the senior and the program lead |
| 90 | **Review** | Manager/supervisor rating against "trusted junior on a senior-led engagement"; 30-day and 90-day surveys; feed shortfalls back into the curriculum-defect log |

*Ready: Workstream Owner* graduates shorten the shadow stage; *Ready: Supervised* graduates follow the full ramp; *Conditional* graduates do their remediation window before starting. A **Day-90 supervisor rating** is a pilot metric (§6.1, layer 6).

## 9. Traceability to the foundation, deviations and open items

### 9.1 What was honoured

| Foundation requirement | Where honoured in this plan |
|---|---|
| 12 weeks, 480 h, 60 teaching days, 40 h/week; no Week 0 | §1; every week sums to 40 h; day numbering §1.8 |
| Block hours (§7.2) and phase hours (§7.6) exactly | §1.3-§1.5; checked by script |
| AI is the largest block group | 152 h of AI blocks vs 146 h of foundations; ~43% effective AI exposure |
| One competency model D1-D6, L0-L4; one readiness rule; role names carry no `L` | §1.1, §3.8; lanes and rubrics use D1-D6 |
| Six gates G0-G5 at Days 2/20/30/45/55/60 | §1.8, §3 |
| Gate criteria from the Assessment Pack (G1 <60 min, zero console, 3 SLOs, >=70% coverage; G2 seven artifacts; G3 85%/70%/20%; G4 five injections, >=99%; G5 nine deliverables, four-person panel) | §3, §4 |
| Tiered non-punitive retake policy, slack-only retakes | §3.7 (windows only where slack exists; see §9.2) |
| Carried system; Kestrel and Linden; P1, P5, P6, P3+P4, P7, P8 | §1.9, project tables in Part II |
| Customer thread weekly with a 48-hour retry | Customer Lab each week; retry rows |
| Protected craft/communication time | Friday blocks and Customer Labs; never reallocated to catch up on technical labs |
| Provider-neutral AI labs; model IDs in config; >= 2 endpoints | §2 and Weeks 1, 5-9 |
| AWS sandbox model; layered cost controls | §7.2 |
| 32-scenario fault subset, stable names, enumerated stall points | §5.2 |
| No certifications | Cert-aligned content used as syllabus only (Weeks 2-3) |
| Weekly pulse, hours logged, wellbeing safeguards | §6.2, §8.1 risk 6 |
| Open-model, fine-tuning, multimodal, MLOps scope cut for 12-week | Week 9 (decision memos only), Week 10 (demo-level GPU), multimodal dropped |

### 9.2 Deviations and judgement calls (each should be checked by the sponsor)

1. **Retake windows are limited by slack.** The foundation's Phase C slack is 1 h; G2 gets a Week-8 window (two weeks later, not one); G4 and G5 have no in-program window and route to *Conditional* (§3.7). Suggest moving slack earlier if the pilot shows retakes are common.
2. **Friday pattern adaptation.** The foundation places the Customer Lab on odd Fridays and the game day on even Fridays. Even-week Customer Labs are on Wednesdays (retry Thursday); game days sit in Weeks 2, 6, 8 and 10; in gate weeks the quiz moves to Thursday.
3. **Weekly 1:1 and retros in Weeks 7-9** are held inside the project block because the weekly slack is zero (Weeks 7, 9) or 1 h (Week 8).
4. **Activity mix** (§1.6) is reported as scheduled and is not tuned to the 15/60/15/10 target; dedicated customer simulation is 32 h (6.7%) and the foundation counts about 30 more embedded hours.
5. **G4 is compressed** to five unannounced windows inside normal work; slack in Week 11 (12.5 h) is the on-call and response time. Day 5 (cost burn) runs Friday morning inside the G4 assessment block.
6. **G1 uses ECS Fargate, not Kubernetes or autoscaling** (the foundation moves both to the 24-week G1); Kubernetes is taught on kind and used for troubleshooting only.
7. **Sub-topic hours inside a block are approximate** (for example, "Docker about 8 h; CI/CD about 10 h; Terraform about 12 h; Kubernetes about 12 h; observability/SRE about 6 h" in DevOps/K8s); only the block totals are binding. Observability and SLOs are taught in Week 4 (before G1), and SRE incident/postmortem work moves to the Week-6 Wheel of Misfortune, so the Phase A/B DevOps split is 42/6 as in the foundation but the topic mix differs from the foundation's indicative list.
8. **AI telemetry fields** (`eval_pass_rate`, `trace_url`, `cost_per_run`, `prompt_version`, `model_config_id`, `judge_tpr_tnr`) are the foundation's addition; this plan uses them from Week 5.
9. **Lab counts**: no target; 107 short labs (most 1.5-3 h) instead of the repo's 42-45 longer ones. This is a design choice, not a contradiction of the foundation.
10. **Week-1 ship is attached to P1** (Kestrel) rather than shown as a separate project; the foundation says "ship-in-week-1 is its first slice" **[Sourced: foundation §8.3]**.

### 9.3 Repo assets reused (and defects not carried forward)

**Reused:** G0 exam blueprint and practical design; G1 rebuild-from-scratch and its criteria; G2 mock security review with 7 artifacts and hidden bank; G3 thresholds; G4 injections and communication weighting; G5 panel and nine deliverables; the craft rubric (nine dimensions); lane logic; escalation ladder; 40%-stall rule; cohort contract; fault-library design rules; air-gap lab spec; RAG corpus mix and held-out golden-set rule; the six data-capture layers; `fde-academy-starter` and `make verify`.

**Not carried forward:** the 26-week phase structure; inherited 26-week lab IDs; the evening/weekend retake policy; "two failures move to the 26-week track" (replaced by the tiered policy); the anyops "Security Operations" domain; the repo's lab counts; and the repo defects listed in foundation Appendix A (day-numbering, $600 vs $500 cap, "eight commands" with seven listed, README cell reference errors).

### 9.4 Unverified items that touch this plan

Treat as unverified until checked: the Anthropic API course module list and certificate claims; Maven evals syllabus details; Udacity page details; the MCP spec revision number beyond the day it was read; the OpenAI Assistants API shutdown date; vendor acquisition claims (Promptfoo, LLM Guard, Guardrails AI); Microsoft Agent Framework 1.0, Google ADK GA and OpenAI Agents SDK sandbox claims; EU AI Act omnibus adoption and GPAI obligations; aws-nuke's safety features and AWS Budgets data lag; Skill Builder, Terraform exam and Azure prices (not used here because no certifications are funded); Full Stack Open parts 11-12 section lists; Palantir's internal training (not public; this plan never claims to replicate it); all hour estimates (judgment, anchored on provider-stated course lengths); and all new-grad Day-90 expectations **[Sourced: R1-R5 verification sections; foundation §12.2]**.

### 9.5 Open decisions for the sponsor (defaults used)

| # | Decision | Default used |
|---|---|---|
| 1 | Pilot cohort size | 15 learners, five trios [Assumption] |
| 2 | Pilot sequencing | 12-week first, then use the data to refine the 24-week plan |
| 3 | Who sponsors learners | Employer-sponsored cohort contract (manager signature); adaptable |
| 4 | Client actors | Staff and volunteers; about 1 actor-hour per simulated pod-hour |
| 5 | AI-assisted coding policy | Allowed in labs/projects with disclosure; closed-tool in G0, G1 and oral components (§7.4) |
| 6 | Provider terms | Claude via the Anthropic API and/or Amazon Bedrock; gateway with spend caps |
| 7 | Retake slack | Keep as is; revisit after the pilot (§9.2 #1) |
| 8 | Outcome publication | Publish with full denominators; may be internal only |
| 9 | Branding | Generic "FDE Academy" |

---

*FDE Program Design: 12-Week Plan v0.1 · Draft for review · Document ends.*
