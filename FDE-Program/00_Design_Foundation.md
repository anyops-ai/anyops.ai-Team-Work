# FDE Program Design — Shared Foundation (00)

**Status:** Draft v0.1 for review · **Date:** 2026-11-25 · **Audience:** program sponsor, program lead, the two plan writers, instructors
**Companion documents:** `FDE_12Week_Plan.md` · `FDE_24Week_Plan.md` (both build on this file) · `research/01–05` (evidence) · `../Projects/` (downloaded repo, reference only, never edited)

### Label legend (used on every number and non-obvious claim)

| Label | Meaning |
|---|---|
| **[Sourced]** | Comes from a cited external source in `research/` (file number given, e.g. R3 = `03_pedagogy_and_bootcamp_methods.md`). Source quality varies; the research notes carry the per-claim caveats. |
| **[Repo]** | Reused or adapted from the downloaded `anyops-ai/Projects` material (file named). |
| **[Judgment]** | A design call made in this document. Not a published benchmark. |
| **[Assumption]** | A planning figure that must be validated in the pilot (cost, staffing, hours). |

Research file keys: **R1** AI courses · **R2** cloud/software/DevOps courses · **R3** pedagogy and bootcamp methods · **R4** FDE role and customer skills · **R5** applied-AI topic depth.

### Contents
1. Purpose, scope and provenance · 2. The FDE role · 3. Competency model · 4. Design principles · 5. Rhythm, cohort, staffing · 6. Assessment and gates · 7. Hours budget (AI-first) · 8. Carried customers and project spine · 9. Lab environment and fault library · 10. Tooling stack · 11. Budget and staffing outline · 12. Risks, open questions, pilot plan · 13. Appendix A: repo reconciliation · 14. Appendix B: decisions needed from you

---

## 1. Purpose, scope and provenance

### 1.1 What this document is

The single source of truth for decisions that are **common to both programs**: who the learner is, what "ready" means, how the program is run and assessed, how hours are budgeted, which customers and projects run through it, and how the lab is built. The two plan documents then only have to say *what happens in which week*.

If a plan document and this file disagree, this file wins until it is revised. Revise this file first, then the plans.

### 1.2 Binding decisions already made by the sponsor

| # | Decision | Consequence in this design |
|---|---|---|
| 1 | Learners are **new grads / early-career** (0–2 years) | Fundamentals are taught, not assumed (but CS-literate: no CS-theory detours, per R2) |
| 2 | **Fresh design, informed by the repo** | We reuse what is good and fix its contradictions (Appendix A) |
| 3 | Content order: **software + cloud → AI (most emphasis) → customer-facing scoping → projects** | AI is the single largest block (§7). Customer craft is nevertheless a *thread* from week 1, not only a last-month module (§4, P7) |
| 4 | Two programs, **both full-time at 40 h/week**: 12 weeks = 480 h, 24 weeks = 960 h | 24-week is deeper and more practised, not slower (§7.2) |
| 5 | **AWS** is the primary cloud | Labs, sandboxes and IaC target AWS; other clouds are covered conceptually |
| 6 | AI labs are **provider-neutral, Claude as the default**; open-source / local models for local and air-gapped labs; **never hard-code model IDs** | Model names live in config; every AI lab runs against ≥2 endpoints (R5 principle 5) |
| 7 | **No certifications** | Cert-aligned content is used as syllabus (e.g. AWS SAA domains, CKA troubleshooting weighting) but no exam is funded, taken or gated. Learners may self-fund optional exams. |
| 8 | Use top courses' methods | See §1.4 |

### 1.3 What this document does not fix

Weekly timetables, lab-by-lab instructions, exact dates, and per-week hours: those belong in the two plan documents. Dollar budgets are outlined (§11) but remain assumptions until a pilot runs.

### 1.4 What we borrowed from where

| Source (research file) | What we borrowed | Where it lands |
|---|---|---|
| fast.ai Part 1 (R1) | Top-down: ship something real in week 1, then peel back layers | P2; Week-1 ship (§4, §5) |
| Maven "AI Evals" (Husain/Shankar) (R1, R5) | One evolving agent, error analysis on real traces, validated binary judges, CI regression evals | AI Core spine; G3 criteria (§6) |
| DeepLearning.AI short courses (R1) | One concept → one lab → one checkpoint; tracing before evals | Lab format (§4, P1/P5) |
| Hugging Face Agents/LLM courses (R1) | "How to ask for help" chapter; objective leaderboard-style capstone component; same fundamentals in several frameworks | Onboarding block; capstone eval; tool-independence |
| Stanford CS224N (R1) | Staged project deliverables (proposal → milestone → demo → report) | Capstone staging (§8) |
| Nana DevOps Bootcamp, Udacity Cloud DevOps (R2) | Project-per-module chain; "do it manually first, then automate" | DevOps/IaC sequencing |
| KodeKloud, CKA exam (R2) | Short lecture → browser/CLI lab → auto-check; time-boxed live-cluster troubleshooting (30% of CKA) as the model for break-fix assessment | Lab format; G1 and G4 style |
| Cloud Resume Challenge (R2) | One end-to-end "IaC + CI/CD + tests + write-up" capstone shape | P1 |
| Google SRE Workbook, SRE training book (R2, R3) | SLOs, incident response, blameless postmortems; **Breakage Service**, groups of three, Build/Stretch/Reach scaffold, Wheel of Misfortune, behaviourally anchored self-rating | §4, §5, §6, §9 |
| OWASP LLM Top 10 (2025), Juice Shop, DevSecOps guideline (R2, R5) | Security syllabus and a free target app | D3 labs; G2/G4 |
| Hack Reactor / Turing catalogs (R3) | Lab-heavy hour ratio; midpoint "would we put this person in front of a customer?" gate; published rubrics; "no category below Meets" | §4 P1, §6 |
| Etsy debrief guide, AWS game-day guidance (R3) | Facilitated blameless debriefs; game days must include non-engineer voices | §5, §8 |
| Palantir/Ramp/OpenAI/Anthropic role evidence, Latent Space, SVPG (R4) | Role definition, failure modes, "pattern vs bespoke" discipline | §2 |
| Mom Test, JTBD, issue trees, Minto/PR-FAQ, SRE PRR handover (R4) | The customer-skill thread, simulations and rubrics | §6.4, §8 |
| **Repo: 12-Week Handbook** (`FDE_12Week_Program_Handbook.md`) | L0–L4 scale; deployment-ready rule; six-gate shape; six data-capture layers; 9-dimension craft rubric; carried-system idea; protected Friday craft block; lanes A/B/C; floating-instructor escalation ladder | §3, §5, §6 |
| **Repo: Assessment Pack** | G1 "rebuild from scratch"; G2 mock security review with pre-submitted artifacts and hidden question bank; G3 thresholds; G4 injected-failure week; two assessors and calibration; novel environment at every gate | §6 |
| **Repo: Ops Guide** | 32-scenario fault library design; sandbox/GPU/air-gap/RAG-corpus specs; cohort contract; "one change" retro rule; 40% stall-point rule | §5, §6, §9 |
| **Repo: Architecture / Matrix** | Security-as-a-thread idea; specializations idea (parked as future electives); compliance map concept | §7.5 (deferred), §10 |

**Not reused:** the 26-week phase structure (the 24-week plan here is a different design, not a stretch of it); the anyops "Security Operations" domain (D4 in the anyops files), because SIEM/CSPM operations is a specialization, not new-grad core; the instruction to take retakes in evenings and weekends (conflicts with the wellbeing rules in §5.4).

---

## 2. The FDE role

### 2.1 Working definition

> A Forward Deployed Engineer is a software engineer embedded with, or deployed to, a specific customer. They diagnose the real problem behind the stated one, build and ship a working production solution inside the customer's constraints (data, security, systems, people), own the outcome through adoption and handover, and turn what was learned into reusable patterns. **[Sourced: R4 §1.1, proposed wording grounded in Palantir, OpenAI, Anthropic and Ramp material]**

### 2.2 Honest caveats about the title

- "FDE" is a **contested title**. Palantir created it; a16z calls the wider use "title arbitrage"; Latent Space says it is stretched to cover almost any customer-facing job **[Sourced: R4 §0]**. We define our own FDE rather than borrow a market definition.
- Public postings for AI-lab FDE roles ask for 3–5+ years (OpenAI 5+, Anthropic 3+); Palantir hires new-grad FDSEs **[Sourced: R4]**. A new-grad program therefore follows the **Palantir model**: hire strong generalists, train them, then embed them under senior FDEs in pods.
- **Palantir's internal training is not public** **[Sourced: R3 §1.7, R4]**. This program must never claim to replicate it.

### 2.3 Failure modes the program is designed against

| Failure mode | Source | Built-in counter-measure |
|---|---|---|
| **Consulting drift**: solve one customer's problem, nothing compounds | R4 (Latent Space, SVPG) | Every project ends with a **product-feedback memo** ("what generalises, what to throw away") |
| **Octopus code**: customer-specific tentacles on a shared core | R4 (Ramp) | Code-review checklist item "pattern or bespoke?"; bespoke code is tagged in the repo |
| **Orphaned hacks** that become years of maintenance | R4 | Temporary scripts must have an expiry note and an owner; checked in handover review |
| **Silent wrong encodings**: schema shows what is stored, not what is meant | R4 | Project P2 ("the report that is always wrong"); fault scenario family DATA-* |
| **Overstating capability** when an evaluator probes limits | R4 | Demo rubric requires a "what it cannot do" page; G3 includes a hostile technical evaluator |
| **Unbounded scope creep** | R4 (First Round) | Scope-negotiation role-plays; "out of scope and riskiest assumption" mandatory in every scope doc |
| **Two jobs in one; cannot say no** | R4 | Judgment overlay (R9) scored at every gate |

### 2.4 Skills taxonomy and the junior bar

The "good at junior level" column is **[Judgment]**, calibrated against Ramp's "junior FDEs focus on execution" and Palantir's new-grad posting "small teams with minimal supervision" **[Sourced: R4 §1.5]**. No company publishes new-grad FDE benchmarks.

| Axis | Skill | Junior "good" looks like | Domain (§3) |
|---|---|---|---|
| Technical | Production coding, tests, git, review | Ships a clean, tested, reviewed week-sized change without rework from basic errors | D1 |
| Technical | Messy data | Profiles an unfamiliar dataset and finds where schema and business meaning diverge | D1, D4 |
| Technical | Cloud and infrastructure | Deploys to a given environment from a runbook; reads logs and metrics; debugs a failed deploy | D2 |
| Technical | Integration | Builds a working integration against a flaky documented API with retries, auth, idempotency | D1, D2 |
| Technical | AI systems | Builds the simplest workflow first; writes an eval set and reports a number, not a vibe | D4 |
| Technical | Security hygiene | Asks "where does this data go?" unprompted; no secrets in repos; explains a constraint plainly | D3 |
| Technical | Operability | Delivers a runbook another person can follow cold | D5 |
| Customer | Discovery | Elicits specific past events, not opinions; talks under ~40% of the time; leaves with facts and next steps | D6 |
| Customer | Scoping | Turns a vague ask into a one-page scope: user, decision, metric, constraints, out-of-scope, riskiest assumption | D6 |
| Customer | Writing and demos | Answer-first one-pager readable in 2 minutes; rehearsed demo on realistic data; says "not yet" honestly | D6 |
| Customer | Expectation management | Surfaces risk early with options, never surprises the customer | D6 |
| Judgment | Scoping discipline | Articulates the trade-off and escalates rather than silently absorbing scope | D6 |
| Judgment | Pattern vs bespoke | Flags "this looks like a pattern"; discards temporary hacks | D1, D6 |
| Judgment | Escalation and uncertainty | Names uncertainty early; escalates at the right time | D6 |
| Judgment | Risk and ethics | Raises data, safety or accuracy concerns; never overstates AI capability | D3, D4 |

### 2.5 What a graduate can and cannot do (the Day-90 target)

**Caveat: this is reasoned estimation. No public company benchmark exists for new-grad FDE Day-90 performance** **[Judgment, informed by R4 §4]**.

**Target: a "trusted junior on a senior-led engagement"**, who owns a *workstream* but never the *relationship*.

| Can do | Cannot yet do reliably |
|---|---|
| Run a structured 30–45 min discovery conversation with a friendly contact and write a one-page scope a senior FDE accepts with edits | Own a strategic account or be the sole technical voice with executives |
| Build and deploy a contained, tested piece (integration, pipeline, LLM workflow with an eval set) under code review; debug a deploy from logs | Negotiate scope, price or timelines without senior review |
| Deliver a rehearsed demo on realistic data and answer "what are the limits?" honestly | Navigate accreditation, regulated procurement or political dynamics alone |
| Write answer-first status updates and a usable runbook | Architect a multi-system solution under heavy constraints |
| Recognise (not always resolve) security/compliance constraints and escalate | Diagnose ambiguous failures in an unfamiliar customer environment without help |
| Notice repeated patterns and flag them | Decide alone when a customer request should be refused |

**Difference between the two programs on exit** **[Judgment]**:
- **12-week graduate:** "ready to start under supervision". Typically *Ready — Supervised* (§6.5), with a strong minority reaching *Workstream Owner*.
- **24-week graduate:** "near-independent on routine engagements". Typically *Workstream Owner*, having also done embedded pod work on real low-risk tasks.

### 2.6 Role names (decoupled from competency levels)

To remove the repo's name collisions (Appendix A), **competency levels are `L0–L4`** (§3.3) and **role names never use `L`**:

| Role | Typical timing | Notes |
|---|---|---|
| Trainee FDE | During the program | |
| **FDE** (entry) | Program exit | Maps to repo "FDE Associate" (Family B) and "L1 Junior FDE" (anyops Family C) |
| Senior FDE | Field experience | Maps to repo "FDE Professional" / "L2–L3" |
| Principal FDE / Deployment Architect | Field only | Never reached in a classroom (repo Handbook §2) |

Post-program field transition **[Repo: Handbook §7]**: shadow (2 engagements) → reverse shadow (2) → solo with backstop (3 months) → independent.

---

## 3. Competency model (one model, replacing both repo variants)

### 3.1 Design choices

- **Six domains** (kept from the repo: it is the right granularity for assessment), but re-cut for an **AI-first program** and to remove the repo's internal conflict (Family B and Family C used different D3/D4/D5).
- **D4 is now Applied AI** (LLMs, RAG, agents, MCP, evals), not "Data & ML Engineering". Classical ML training is "just enough" (R5 T1) and fine-tuning is an elective, because FDE work is overwhelmingly prompting, retrieval, tools and evals on API models **[Sourced: R1 B1, R5 T10]**.
- **AI operations get their own domain (D5)** because the largest production risk in AI work is not building but operating: cost, latency, drift, incidents **[Judgment, supported by R5 cross-cutting finding 5]**.
- **Security is one domain (D3) covering classical and AI-specific security**, so a learner is not scored twice for the same habit. Boundary rule: **D3 = design, threat-model, evidence; D5 = run, monitor, respond.**

### 3.2 The six domains

| # | Domain | Coverage | Boundary rule |
|---|---|---|---|
| **D1** | **Software Engineering** | Python (+ one other language read-fluently), APIs, testing, git/code review, Linux and networking, SQL and data modeling, debugging, reading unfamiliar code | Anything about *writing correct code* |
| **D2** | **Cloud & Platform** | AWS core (IAM, VPC, compute, storage, managed data), containers, CI/CD, Terraform, Kubernetes, observability, SRE basics, cost | Anything about *where and how it runs* |
| **D3** | **Secure Delivery & Compliance** | IAM least privilege, secrets, supply chain (SBOM, signing), scanning (SAST/SCA/DAST/IaC), threat modeling, **AI security** (prompt injection, agent least privilege, MCP security), privacy and compliance evidence, responsible-AI documentation | Design and evidence |
| **D4** | **Applied AI** | LLM fundamentals, prompting and structured outputs, tool use, RAG, **evals**, agents, MCP, context engineering, fine-tune-vs-RAG decisions, ML "just enough" | Building AI behaviour |
| **D5** | **AI Operations & Reliability** | LLMOps (tracing, caching, routing, cost/latency), AI deployment (K8s, GPU awareness, open-model serving), guardrails as runtime controls, human-in-the-loop operations, data pipelines, incident response for AI systems | Running AI behaviour |
| **D6** | **Customer Craft** | Discovery, scoping, decomposition, written and verbal communication, demos, stakeholder management, expectation management, enterprise integration planning (SSO, legacy), handover and runbooks, product feedback | Everything customer-facing |

### 3.3 One level scale: L0–L4, behaviour-anchored

Kept from the repo (L0–L4) **[Repo: Handbook §2]** and anchored to Google's behavioural self-rating, which they adopted because 7-point scales were "too noisy" **[Sourced: R3 §1.6]**.

| Level | Label | Behaviour anchor | Evidence required |
|---|---|---|---|
| **L0** | Unaware | "No idea where to start" | None |
| **L1** | Aware | Can do it *with help*; follows a runbook; defines terms | Passes knowledge check; lab completed with hints |
| **L2** | Practitioner | Can do a known task *unaided from docs* in a *known* environment | Lab completed within SLA, no hints; assessor-scored |
| **L3** | Independent | Solves a *novel* problem in an *unfamiliar* environment from memory and judgment | Passes a gate in a fresh environment with randomised fault variant |
| **L4** | Authority | Could *teach it*; sets patterns; has authored a reusable asset used by 2+ deployments | Reusable asset adopted; teaches a session |

**Scored three times:** baseline (Day 2), midpoint, exit. Midpoint = Day 30, scored at G2 (12-week) / Day 60, the consolidation review (24-week).

### 3.4 Domain-specific anchors at the levels that decide readiness

| Domain | L1 (with help) | L2 (unaided, known env) | L3 (novel env) |
|---|---|---|---|
| D1 | Follows a tutorial to build and test a small service | Builds a tested service from a spec; writes clean PRs | Debugs a failing unfamiliar codebase; finds root cause in a race or network fault |
| D2 | Deploys from a runbook | Provisions a stack with Terraform and a CI pipeline from docs | Rebuilds a working, observable stack in a fresh account under time pressure (G1) |
| D3 | Names common risks | Externalises secrets, scans images, writes IAM least-privilege | Defends an architecture in a live security review; threat-models an agent with tools |
| D4 | Calls an LLM API; runs a given RAG sample | Builds RAG/agent with an eval set; reports retrieval and answer metrics | Diagnoses *why* an unfamiliar AI system fails, using traces and a failure taxonomy |
| D5 | Reads a dashboard | Instruments traces and cost; writes a runbook | Operates a degrading AI system for days; detects and mitigates incidents before the customer |
| D6 | Writes a status update | Runs a scripted discovery call; writes a scope doc | Elicits the unstated driver from a vague, adversarial client and gets a scope agreed |

### 3.5 Target exit profiles (median learner) **[Judgment]**

| Domain | 12-week exit target | 24-week exit target |
|---|---|---|
| D1 Software Engineering | L2 (L3 stretch) | L3 |
| D2 Cloud & Platform | L2 | L3 |
| D3 Secure Delivery | L2 | L2 (L3 stretch) |
| D4 Applied AI | **L3** | **L3** (L4 for strong learners, via an authored reusable asset) |
| D5 AI Ops & Reliability | L2 | L3 |
| D6 Customer Craft | L2 | L3 |

Rationale: the program is AI-first, so D4 is the one domain where even the 12-week graduate is expected to be *independent*.

### 3.6 Readiness rule

Kept from the repo **[Repo: Handbook §2]**: **L2+ in all six domains AND L3+ in at least three** makes a learner **Ready — Workstream Owner**. A lower, explicit tier (**Ready — Supervised**) is added because the research shows a 12-week program cannot honestly promise the upper tier to most new grads. Full outcome table: §6.5.

### 3.7 Translating the repo's models

| Repo (Family B: 12-Week Handbook) | This design | Change |
|---|---|---|
| D1 Software & Systems Engineering | **D1 Software Engineering** | Same; Linux/networking kept |
| D2 Cloud & Platform (DevOps) | **D2 Cloud & Platform** | Same; AWS-specific |
| D3 Security & Compliance (DevSecOps) | **D3 Secure Delivery & Compliance** | Same; AI security moves in here |
| D4 Data & ML Engineering | **D4 Applied AI** | Narrowed to LLM/RAG/agents/evals; training and classical ML reduced |
| D5 MLOps / LLMOps | **D5 AI Operations & Reliability** | LLMOps kept; classical MLOps reduced; incident response added |
| D6 Customer Engineering (FDE craft) | **D6 Customer Craft** | Same; enterprise-integration planning explicit |

| Repo (Family C: anyops Matrix/Architecture/Deck) | This design | Change |
|---|---|---|
| D3 Secure Delivery | D3 | Same name |
| D4 Security Operations (SIEM/CSPM) | *Not a core domain* | Deferred as a future specialization/elective (§7.5) |
| D5 Applied AI & MLOps | Split into **D4 + D5** | AI is the focus, so it gets two domains |
| P0–P4 proficiency scale | **L0–L4** | Treated as the same five levels; verify the wording against the Matrix README before publishing |
| Readiness: P2 everywhere + P3 *specifically in D2, D3, D6* | Any three domains at L3 | We do not hard-wire which domains; D4 is expected to be one |
| Ladder: L0 Student / L1 Junior / L2 Mid / L3 Senior | Role names (§2.6) | Role names no longer collide with competency levels |

---
## 4. Design principles (with evidence strength)

Evidence key (from R3): **A** = meta-analysis or multiple controlled studies · **B** = single strong study or well-replicated effect, transfer uncertain · **C** = practitioner consensus / observational · **J** = our design judgment, no direct evidence. Note that most evidence is from undergraduate STEM or bootcamp settings, not FDE training; transfer is assumed, not proven.

| # | Principle | What it means in practice | Evidence |
|---|---|---|---|
| P1 | **Lab-heavy, short lectures** | Target mix **15% instruction / 60% labs and projects / 15% customer craft and simulation / 10% assessment** **[Repo: Handbook/Architecture split]**. No lecture block longer than ~30 min without an interactive check. | **A** (Freeman 2014: failure 21.8% active vs 33.8% lecture); Hack Reactor catalog is ~9–23% lecture **[Sourced: R3]** |
| P2 | **Ship in week 1** | Every learner deploys something real (a small AWS-hosted service that calls an LLM API) before the first Friday. Then dig into internals. | **C** (fast.ai top-down; Shopify/Fowler "time to first deploy"; Meta first-week ship) **[Sourced: R1, R3]** |
| P3 | **Guided → faded → independent** | Each unit moves: worked example → paired attempt → solo attempt → customer-style variant (Google Build/Stretch/Reach). Guidance fades per learner; fast-track allowed. | **A/B** (worked examples; expertise-reversal) **[Sourced: R3 #4]** |
| P4 | **One carried system and one carried customer** | A single evolving system (§8) runs from the AI block to handover, instead of disconnected toy projects. | **C** (Maven evals; DLAI "Evaluating AI Agents"; repo carried-system idea) **[Sourced: R1; Repo]** |
| P5 | **Eval-first AI spine** | Evals are introduced the first time a learner builds anything with an LLM. Every AI lab ships with an eval and a one-paragraph "what the numbers say". A lab does not pass without eval and trace evidence. | **C** (Husain, Anthropic Jan 2026; practitioner consensus, not controlled studies) **[Sourced: R5 §1, §3]** |
| P6 | **Direct API before frameworks** | A hand-written tool loop precedes LangGraph or any agent SDK; frameworks are compared on the same fundamentals so skills stay tool-independent. | **C** (Anthropic "start with the simplest solution"; HF Agents course) **[Sourced: R1, R5]** |
| P7 | **Customer thread from week 1** | One ~2–3 h Customer Lab per week with a written artifact, simulated client, debrief and **one retry within 48 h** (the delta between attempts is graded). Not a final-month module. | **J** (no independent evidence the methods work; sources are vendor/practitioner) **[Sourced: R4 §3, §5]** |
| P8 | **Protected craft and communication time** | The Friday block is protected by policy and never reallocated to catch up on technical labs. | **J** (repo Handbook policy; Hack Reactor grades soft skills explicitly **[Sourced: R3]**) |
| P9 | **Retrieval practice and spacing** | A low-stakes cold-start question every morning; a weekly quiz containing items from 1, 3 and 6 weeks earlier (more spacing steps in the 24-week version). | **A** (Dunlosky 2013; Cepeda 2006; mostly recall tasks, so skills transfer is **B**) **[Sourced: R3]** |
| P10 | **Mastery gates with rubrics, in novel environments** | Each gate uses a fresh environment with a randomised fault variant so memory is not what is tested. Rubrics are published in advance. | **A (moderate effect)** mastery learning; repo principle **[Sourced: R3 #6; Repo: Assessment Pack]** |
| P11 | **Real tools, real breakage, no gimmick labs** | Labs use production-grade tools and a breakable sandbox system (Google's "Breakage Service"); faults come from real engagements. | **C** **[Sourced: R3 §1.6; Repo: Ops Guide]** |
| P12 | **Trios, mixed experience** | Pods of three, mixed by baseline; rotate driver/navigator every 20–30 min; individual output assessed separately. | **B** (Hannay 2009; Google's group-of-three finding) **[Sourced: R3 #7, §5]** |
| P13 | **Blameless, facilitated debriefs** | Every game day and incident drill ends with a facilitated debrief and a written postmortem (not dumped solely on the student). | **B** (psychological safety is observational) **[Sourced: R3 #12]** |
| P14 | **Wellbeing by design** | ~40 scheduled hours; **no required work after 17:45 or on weekends**; one lighter consolidation week per ~6 weeks; named wellbeing lead; weekly anonymous pulse. | **B/C** (bootcamp burnout study; hours–output evidence from a WWI-era dataset, imperfect analogue) **[Sourced: R3 §3]** |
| P15 | **Security is a thread, not a lecture** | Least privilege, secrets and the "lethal trifecta" (private data + untrusted content + external communication) appear in the first week they are relevant and are revisited. | **C** (OWASP LLM Top 10 2025; Willison) **[Sourced: R5]** |
| P16 | **Vendor-neutral and swappable** | Model IDs in config only; every AI lab runs against ≥2 endpoints (a hosted frontier model plus an OpenAI-compatible hosted/local one). | **J** (customers mandate different providers) **[Sourced: R5 principle 5]** |
| P17 | **Measure the program, not just the learner** | Surveys before, after, 30 days and 6 months; manager survey at 30 days and 6 months; behavioural indicators (time to first merged PR, review turnaround). | **C** (Google SRE EDU) **[Sourced: R3 #14]** |
| P18 | **Honest outcomes** | Report cohort outcomes with full denominators and pre-declared definitions of "ready" and "placed". | **C** (CFPB action against BloomTech shows the failure mode) **[Sourced: R3 §3]** |

---

## 5. Rhythm, cohort and staffing

### 5.1 The 40-hour day

Scheduled net learning time is **8.0 h/day × 5 days = 40 h/week**, both programs. Core hours 09:00–17:45 with a 45-minute lunch; hard stop at 17:45 **[Judgment, derived from R3 §4.2]**.

| Time | Net h | Block | Notes |
|---|---|---|---|
| 09:00–09:20 | 0.33 | Stand-up + **retrieval warm-up** | One cold question from earlier weeks, no notes; log stuck points |
| 09:20–10:30 | 1.17 | **Instruction**: ≤30 min lecture, then worked example or live coding, then an interactive check | Anthropic/DLAI "one concept, one lab" cadence |
| 10:30–12:30 | 2.00 | **Pair/trio lab** | Driver/navigator swap every 20–30 min |
| 12:30–13:15 | — | Lunch (not counted) | |
| 13:15–15:45 | 2.50 | **Project / carried-system block** | Floating instructor in coach mode |
| 15:45–16:45 | 1.00 | **Review block**: code review or incident drill (alternate days) | Reviews also teach (R3 #10, evidence C) |
| 16:45–17:30 | 0.75 | Lab continuation / office hours / remediation | Where retakes and catch-up live |
| 17:30–17:45 | 0.25 | **Written reflection**: shipped / stuck / learned + next-day plan | Doubles as early-warning signal |
| **Total** | **8.00** | | |

**Floating-instructor escalation ladder** **[Repo: Handbook/Ops Guide]**: 0–10 min stuck, instructor does nothing · 10–25 min, asks a question · 25–40 min, gives a hint · 40+ min, gives direct help. Hint count and stall point are logged.

### 5.2 The Friday pattern (protected)

| Block | Content |
|---|---|
| Morning | Weekly checkpoint and **demo** (each pod shows what shipped); weekly retrieval quiz |
| Afternoon, alternating | **Customer Lab** (simulated client) on odd weeks · **incident game day / Wheel of Misfortune** on even weeks |
| Last 45 min | Blameless retro; pulse survey |

### 5.3 Weekly protected items

One 30-min 1:1 with the technical mentor · one peer code-review pairing · one retrieval quiz · one written artifact graded on a rubric · one Customer Lab with a retry window.

### 5.4 Wellbeing safeguards

1. Scheduled load ~40 h; **no required work beyond 17:45 or on weekends**, stated in an expectations session on Day 1.
2. **Consolidation weeks:** at least one week per ~6 with ≥12 h of the week allocated to slack/consolidation (these hours are budgeted as the "Slack" row in §7, so total hours stay at 40/week).
3. Named wellbeing lead plus an external counselling/EAP referral list (Recurse Center's manual states they have no mental-health staff **[Sourced: R3 §1.1]**; we do not copy that gap).
4. Weekly anonymous pulse (stress, load, belonging), reviewed by staff within 48 h.
5. **Pre-brief before every drill:** "troubleshooting is a series of failures; it is fine not to solve it" (Google "play to learn"). A no-stakes first drill.
6. Social norms adopted from Recurse Center: no feigned surprise, no "well-actuallys", no back-seat driving, no subtle -isms, plus a code of conduct.
7. Early-warning indicators (missed check-ins, falling retrieval scores, rising stall time) trigger a supportive outreach script, not a penalty.
8. Retakes happen inside scheduled slack hours, **never as unpaid evening or weekend work** (this deliberately reverses the repo's "deliberate friction" policy; see Appendix A).

### 5.5 Cohort size and staffing (pilot) **[Assumption: to be validated in the pilot]**

R3 found **no rigorous evidence for an optimal instructor ratio**; the numbers below triangulate vendor claims (1:10, under 1:12, class cap ~20) and one practitioner finding (Google: groups of three).

| Item | 12-week pilot | 24-week pilot |
|---|---|---|
| Learners | **15** (5 trios) | **15** (5 trios) |
| Why 15 | Fits the cap-~20 opinion and trio structure; small enough for individual observation | Same |
| Lead instructors / facilitators | 2 (≈1 per 8 learners) | 2–3 |
| Technical mentors | 1 per 3 learners first half, tapering to 1 per 4–5 in last phase | Same, plus senior FDE mentors for the embedded pod phase |
| Other | 1 program manager, 1 lab/platform engineer, 1 wellbeing lead (part-time), 1–2 alumni TAs, external assessor panel at gates G2/G4/G5 | Same |
| Client actors | Staff and volunteers (see §8.4) | Same, plus real internal/partner stakeholders in the pod phase |

### 5.6 Mentor model

- **Two layers:** (a) a **technical mentor** with 2–3 mentees per mentor (Meta's secondhand figure, **[Sourced: R3 §1.5; weak]**), who runs a weekly 1:1, reviews PRs and co-runs shadowing; (b) a **peer trio**.
- **Shadow → reverse-shadow → solo** for customer-facing tasks, mirroring Google on-call training **[Sourced: R3 §1.6]**.
- **Alumni/near-peer teaching** from earlier cohorts (Google "crowd-sourced instructors"), with a few hours per week at most and recognition **[Sourced: R3]**.
- **Mentor training:** debrief facilitation (Etsy guide), feedback delivery, and rubric calibration **[Sourced: R3]**. Mentors do **not** assess their own mentees' gates **[Repo: Ops Guide "mentors do not assess"]**.

### 5.7 How the two programs differ in rhythm

| Aspect | 12-week | 24-week |
|---|---|---|
| Scaffold fade | Fast: guided in weeks 1–4, coach by weeks 5–8, independent in 9–12 | Gradual: spaced worked examples, more repetitions; breakage 0→3 spread across phases |
| Retrieval spacing | Items from 1, 3, 6 weeks earlier | Adds 12-week review |
| Slack | Consolidation inside weeks | A **two-week consolidation window** after the platform phase (weeks 11–12) with remediation |
| Real work | Simulated clients only | Adds an **embedded pod phase** on low-risk real internal/partner work with a senior FDE mentor (Ramp pod model, **[Sourced: R3 §1.7]**) |
| Honest promise | "Ready to start under supervision" | "Near-independent on routine engagements" |

---

## 6. Assessment and gate framework

### 6.1 Three layers

| Layer | What | Frequency | Counts toward |
|---|---|---|---|
| **1. Continuous lab checks** | Auto-checks and rubric feedback; every AI lab requires eval + trace evidence; weekly retrieval quiz; telemetry captured (see §6.9) | Daily/weekly | Lab score; remediation triggers (formative, not gating) |
| **2. Gates (summative)** | Work-sample assessments in **novel environments**, rubric-scored, two assessors where marked | Six gates (G0–G5) | Readiness outcome |
| **3. Capstone and readiness panel** | Flagship end-to-end engagement ending in a defence to a four-person panel (G5); in the 24-week version also a pod review | End | Readiness outcome |

### 6.2 Gate placements (concept; the plans fix dates)

| Gate | Concept name | 12-week (Day) | 24-week (Day) | What it assesses | Primary domains |
|---|---|---|---|---|---|
| **G0** | Baseline | 2 | 2 | Diagnostic only (no pass/fail): 60-question exam, broken-environment practical, mock discovery call. Routes to lane A/B/C and an Individual Learning Plan **[Repo]** | all |
| **G1** | **Platform: rebuild from scratch** | 20 | 40 | Fresh AWS sandbox → observable, containerised service via IaC + CI | D1, D2 |
| **G2** | **Secure delivery review** | 30 | 50 | Mock enterprise security review panel; also the **midpoint readiness question** ("would we put this person in front of a low-risk customer?") | D3, D2, D6 |
| *Mid* | *Consolidation and midpoint review (24-week only)* | — | 60 | Skills self-rating, competency re-score, remediation planning | all |
| **G3** | **AI build** | 45 | 90 | An AI system delivered against a business metric with evals in CI | D4, D6 |
| **G4** | **Operate under failure** | 55 | 105 | Multi-day production simulation with injected failures | D5, D3, D2 |
| *Pod* | *Embedded pod review (24-week only)* | — | 115 | Real low-risk work with a senior mentor; mentor and client feedback | D6, all |
| **G5** | **Capstone defence and readiness panel** | 60 | 120 | Flagship engagement build, handover and defence | all |

Day counting: Week 1 starts on Day 1 (Monday); 12 weeks = 60 teaching days, 24 weeks = 120. **G0 happens on Day 2 inside Week 1** (no separate "Week 0", which removes the repo's day-numbering collision).

### 6.3 Gate specifications

| Gate | Setup and required evidence | Pass criteria (reused numbers marked) |
|---|---|---|
| **G1** | Novel sandbox + randomised fault variant; stopwatch | Under **60 min** · **zero console actions** · **3 SLOs live** · **≥70% test coverage** · basic scans green **[Repo: Pack G1]**. In the 24-week version add autoscaling and a Kubernetes deployment. |
| **G2** | Panel of 2–3 plays an enterprise security team; **45 min** defence. Artifacts submitted 24 h before: architecture and data-flow diagram with trust boundaries; SBOM matching the deployed image digest; scan reports with triage rationale; secrets-management design; IAM/RBAC matrix; control-to-framework mapping; incident response plan **[Repo: Pack §4]**. Hidden bank of ~30 questions, 12 asked, including AI-specific ("What stops a document in our corpus from instructing your model?") | Every artifact present and valid; zero critical CVEs; no secret resolvable from the repo; "I don't know" scores higher than a fabricated answer **[Repo]** |
| **G3** | Delivered AI system, 100-question held-out golden set plus 50-question dev set (never used for tuning); hostile technical evaluator in the demo | **≥85% faithfulness**; **context precision ≥70%**; **cost/transaction within 20% of target** **[Repo: Pack G3]**; judge calibrated to human labels (**TPR and TNR ≥0.85**) **[Sourced: R5 T6]**; regression suite in CI that **fails on a deliberately injected prompt regression**; **0 cross-user leaks on an adversarial ACL set** **[Sourced: R5 T5/T21]**; limitations page and error-analysis report |
| **G4** | Multi-day production simulation (5 days in the 24-week program, compressed in the 12-week program); a role-played customer demands status. Injections drawn from the fault library: provider outage, poisoned document, 10× traffic spike, prompt regression, 6× cost burn **[Repo: Pack G4]** | **≥99% availability** · every incident **self-detected** · runbooks complete · unit economics reported **[Repo]**. 24-week adds an OWASP LLM01–10 control map with evidence. |
| **G5** | Teams of two (12-week) or individual-plus-pod (24-week) receive a brief with **exactly three planted complications**; four-person panel (a senior FDE, a security lead, an ML lead, a customer-facing leader) **[Repo: Handbook Week 12]**. Defence: 30 min presentation, 30 min technical deep dive, 20 min adversarial questions, 10 min business framing | All nine deliverables (§8.5); craft average ≥3.5 (for *Workstream Owner*); panel decision on readiness outcome |

### 6.4 Rubric templates

**Template A: technical work-sample rubric** (used for module checks and gates). Four behaviour-anchored levels per criterion; 5–7 criteria per task; published in advance; double-marked at G2/G4/G5 **[Judgment; Turing "no category Below" rule from R3 §1.3]**.

| Criterion (example) | 1 Not evidenced | 2 Partial | 3 Demonstrated | 4 Strong |
|---|---|---|---|---|
| Correctness | Does not work | Works on the happy path only | Works on stated cases with tests | Works on edge cases; tests for failure modes |
| Method | Random changes | Some systematic steps | Systematic isolation to root cause | Fixes the class of problem, not the instance |
| Evidence | Claims without data | Partial metrics | Metrics reported with method | Metrics reproducible from a record |
| Security | Afterthought | Some controls | Baseline controls with evidence | Anticipates the reviewer's objections |
| Communication | Cannot explain choices | Explains what, not why | Explains trade-offs | Adjusts to audience; honest about limits |

Rule: **"Meets" (3) required in every core criterion; no criterion at 1** to pass a module gate.

**Template B: the craft rubric** (summative; scored at G2, G4, G5; two independent assessors). Nine dimensions on a 1–5 scale **[Repo: Handbook Layer 4]**:

| Dimension | 1: Unacceptable | 3: Competent | 5: Exemplary |
|---|---|---|---|
| Discovery | Accepts the stated problem at face value | Asks clarifying questions, finds main constraints | Surfaces the unstated business driver and reframes |
| Scoping | Vague or unfalsifiable criteria | Measurable criteria, explicit out-of-scope | Tied to a metric the customer is accountable for |
| Architecture | Copies the reference design | Sound design fitting constraints | Adapts to the customer's operating capability; trade-offs documented |
| Execution | Blocked repeatedly, needs rescue | Working system on schedule | Early; anticipates blockers |
| Troubleshooting | Random changes | Systematic isolation, root cause | Fast root cause; fixes the class of problem |
| Security posture | Afterthought | Baseline controls, evidence available | Pre-empts the review with compensating controls |
| Communication | Jargon-heavy, buries the lede | Clear, audience-appropriate, timely | Adjusts register per stakeholder; bad news lands well |
| Judgment | Escalates too late or never | Escalates appropriately | Calibrated risk calls; knows what to refuse |
| Handover | Customer cannot operate it | Runbooks exist and are usable | Customer team genuinely self-sufficient |

**Template C: formative customer-skill rubrics R1–R9** (weekly; 4-level; non-gating; from R4 §3.3): R1 discovery interview · R2 scope document / PR-FAQ · R3 decomposition · R4 demo · R5 written update / executive brief · R6 expectation management / bad news · R7 security and compliance conduct · R8 handover (a cold operator can deploy, monitor, roll back and handle two seeded incidents using only the pack) · R9 judgment overlay. **Conversion rule so there is only one summative scale:** Strong = 4–5, Demonstrated = 3, Partial = 2, Not evidenced = 1, used as *evidence* by the assessor, never averaged into the craft score directly. Rubric validity is unproven in the public literature **[Sourced: R4 §3.3]**; calibrate on recorded examples before the first cohort.

### 6.5 Readiness outcomes (an internal credential only; no vendor certification)

| Outcome | Rule | Next step |
|---|---|---|
| **Ready — Workstream Owner** | L2+ in all six, **L3+ in at least three**, craft ≥3.5, all gates passed **[Repo: deployment-ready rule]** | Shadow stage shortened; owns a workstream on a senior-led engagement; reverse-shadow soon after |
| **Ready — Supervised** | L2+ in all six, L3 in 1–2, craft ≥3.0 | Paired assignment for ~90 days with a named senior |
| **Conditional** | One domain at L1, or craft 2.5–3.0 | 4–6 weeks targeted remediation, then re-defence at a mini-G5 |
| **Not yet ready** | Multiple gaps | Role-fit conversation; deferral to a later cohort; documented exit path |

The labels reuse the repo's four outcomes (Independent / Supervised / Conditional / Not certified) with names changed to avoid confusion with external certification. **Craft threshold for Workstream Owner stays at 3.5 (repo); Supervised is set at 3.0 [Judgment].**

### 6.6 Retake and remediation policy (less punitive than the repo and commercial bootcamps)

Reconciles the repo's "two failures → exit to the 26-week track" **[Repo]** with Hack Reactor's PIP-then-dismissal pattern, which has no evidence of improving outcomes **[Sourced: R3 §3]**. Mastery-learning evidence is positive (A, moderate effect). Published in Week 1 **[Judgment]**.

1. **First miss on a gate:** 1 week of targeted remediation inside scheduled slack with a mentor-owned, rubric-anchored plan; re-assessment on a **parallel task** (same rubric, different environment/fault variant, to avoid memorisation).
2. **Second miss (any gate):** formal growth plan; pairing with a senior tutor; **options, not automatic exit**: (a) continue with a documented conditional outcome, (b) defer to the next cohort at the same gate without penalty, (c) transfer to the other program length if a seat exists.
3. **Third miss or sustained non-engagement:** a fit conversation with a documented exit path and role alternatives where employer-sponsored.
4. Soft-skill concerns follow the same path, with written behavioural feedback within 48 h.
5. Total cohort time for completers is capped at **1.25× program length** so outcomes can be reported fairly **[Sourced: R3 §4.4]**.
6. A **one-retry-in-48-hours rule** applies to formative Customer Lab simulations (R4 call-audit pattern).

### 6.7 Cohort contract (revised from the repo)

Signed before Day 1 by learner (and manager, if employer-sponsored) **[Repo: Ops Guide §8, modified]**:

| # | Clause | Change from repo |
|---|---|---|
| 1 | Learner is unavailable for customer or operational work for the full program | Kept |
| 2 | Absence beyond three cumulative days moves the learner to the next cohort, with a documented exception path for illness or caregiving | Added exception path |
| 3 | Learner sits every gate; no partial-credential path | Kept |
| 4 | Gate failures follow the published retake policy (§6.6) | **Replaces** "two failures move to the 26-week track" |
| 5 | The readiness outcome determines assignment eligibility; the manager cannot override it | Kept (prevents training theater) |
| 6 | Learner contributes at least one reusable asset (fault scenario, runbook, pattern) by the final gate | Kept |
| 7 | Scheduled hours are ~40/week; no required work after 17:45 or at weekends | **New** |
| 8 | Program publishes cohort outcomes with full denominators | **New** |

### 6.8 Calibration and gate health

| Metric | Target | Action on breach | Source |
|---|---|---|---|
| Gate first-attempt pass rate | **70–85%** | Below: curriculum too steep. Above: too easy | **[Repo: Layer 3]** |
| Inter-assessor delta (5-point craft rubric) | **≤1.0** | Above: calibration session before the next gate | **[Repo]** |
| Stall-point rule | If **>40%** of a cohort stalls at the same point in the same lab → curriculum defect, owner and fix date logged | Fix before the next cohort | **[Repo: Handbook Layer 2]** |
| Lab completion within SLA | ≥80% | Re-scope the lab | **[Repo]** |
| Competency lift, baseline → exit | ≥1.5 levels (12-week); ≥2.0 (24-week) | Review instruction-to-lab ratio | Repo 1.5; 2.0 is **[Assumption]** |
| Cohort completion | ≥85% | Review schedule protection | **[Repo]** |
| Learner-reported readiness | ≥4.0/5 | Investigate phase | **[Repo]** |
| Assessors | **Two independent** at G2, G4, G5; calibration on recorded examples before each cohort | | **[Repo; Sourced R3]** |

### 6.9 Data model

Reuse the repo's **six capture layers** (per-learner competency; per-lab telemetry; per-gate; craft rubric; program health; business outcomes) and the Working Plan Workbook design, with renamed domain fields (`d1_swe … d6_craft`) **[Repo: Handbook Part III]**. **Add AI-specific telemetry fields** (our addition **[Judgment]**): `eval_pass_rate`, `trace_url`, `cost_per_run`, `prompt_version`, `model_config_id` (never a hard-coded model name), `judge_tpr_tnr`. Keep the key fields `time_to_first_signal`, `stall_point` (enum with known stall points per fault) and `hints_taken`.

### 6.10 Composite score weights (for support and ranking only; the outcome uses thresholds) **[Judgment]**

| Component | Weight | Note |
|---|---|---|
| Gate assessments (G1–G5) | 45% | Repo used 55% |
| Lab checks | 20% | Repo used 25% |
| Craft rubric | **20%** | Raised from the repo's 10% because customer craft is a first-class outcome (R3 §4.1, R4) |
| Portfolio artifacts | 10% | |
| Peer code-review participation | 5% | Repo used 10% |

### 6.11 Repo assets reused at gates

| Asset | Used in |
|---|---|
| "Rebuild from scratch in a fresh account" | G1 |
| Mock security review with pre-submitted artifacts and hidden question bank | G2 |
| 85%-faithfulness golden-set gate and cost-per-transaction limit | G3 |
| Injected-failure production simulation with availability threshold | G4 |
| Four-person capstone panel with three planted complications and nine deliverables | G5 |
| 32-scenario fault library (renumbered and extended to 40, §9.6) | G0, G1, G3, G4 |

---
## 7. Hours budget (AI-first)

### 7.1 Ground rules

- **12-week = 480 h, 24-week = 960 h** (40 h/week; §5.1). Tables below sum **exactly** to these totals.
- Hours are **learner contact time**: guided instruction, labs, pairing, projects, reviews, assessments. Self-study is not counted and is not required (§5.4).
- "AI" means **AI Core (D4) + AI Operations & Security (D5/D3)**, topics T1–T21 from R5. Every AI-centric *project* hour is shown separately so the AI share is not overstated.
- All allocations are **[Judgment]**, compressed from the research hour estimates (which are themselves the researchers' judgment, anchored on provider-stated course lengths). Phase feasibility is checked in §7.6.

### 7.2 Master hours table

| # | Block | 12-week h | % | 24-week h | % | Main domains |
|---|---|---|---|---|---|---|
| 1 | Onboarding and baseline (G0, accounts, norms, week-1 ship) | 10 | 2.1 | 16 | 1.7 | all |
| 2 | Software fundamentals | 32 | 6.7 | 56 | 5.8 | D1 |
| 3 | Cloud / AWS | 36 | 7.5 | 72 | 7.5 | D2 |
| 4 | DevOps / Kubernetes (containers, CI/CD, IaC, K8s, observability/SRE) | 48 | 10.0 | 104 | 10.8 | D2, D5 |
| 5 | DevSecOps | 20 | 4.2 | 44 | 4.6 | D3 |
| | **Subtotal: foundations** | **146** | **30.4** | **292** | **30.4** | |
| 6 | **AI Core** (T1–T10: LLM basics, prompting, tools, RAG, evals, agents, MCP, context, FT decision) | **100** | 20.8 | **190** | 19.8 | D4 |
| 7 | **AI Operations & Security** (T11–T21: LLMOps, deployment, guardrails, AI security, privacy, HITL, enterprise integration) | **52** | 10.8 | **110** | 11.5 | D5, D3, D6 |
| | **Subtotal: AI** (largest block group) | **152** | **31.7** | **300** | **31.3** | |
| 8 | Customer thread: dedicated Customer Labs | 32 | 6.7 | 72 | 7.5 | D6 |
| 9 | Projects and capstone (includes embedded customer simulation) | 84 | 17.5 | 184 | 19.2 | all |
| 10 | Assessment and gates | 28 | 5.8 | 48 | 5.0 | all |
| 11 | Slack: consolidation, remediation, retros | 38 | 7.9 | 64 | 6.7 | all |
| | **TOTAL** | **480** | **100** | **960** | **100** | |

Percentages are rounded; they may not sum exactly. **Check:** 146+152+32+84+28+38 = 480 ✓ · 292+300+72+184+48+64 = 960 ✓.

**Memo lines (not additional hours; they sit inside the rows above):**

| Memo | 12-week | 24-week |
|---|---|---|
| Embedded customer-craft hours inside Projects and Assessment (client simulation, scoping, demos, handover) **[Judgment]** | ≈30 | ≈70 |
| **Total customer-craft exposure** (dedicated + embedded) | ≈62 h (≈13%) | ≈142 h (≈15%) |
| AI-centric project hours (P5, P6, P8; §8.3) | 56 | 112 |
| **Effective AI exposure** (AI block + AI-centric projects) | **208 h (≈43%)** | **412 h (≈43%)** |

**AI is the largest block group in both versions.** The AI blocks outweigh the entire foundations stack (152 vs 146; 300 vs 292), and once AI-centric projects are counted, AI is ~43% of every hour.

### 7.3 AI block detail (topic hours from R5's T1–T21)

R5 estimated ~154 h at "intro" depth and ~418 h at "deep" depth, excluding capstone. Our budgets compress these as shown. **[Judgment]**

**AI Core (D4)**

| T | Topic | 12-wk h | 24-wk h | R5 intro | R5 deep |
|---|---|---|---|---|---|
| T1 | ML/DL "just enough": tokens, embeddings, context, overfitting, metrics, classifier-vs-LLM | 6 | 14 | 10 | 30 |
| T2 | Python for data and AI (pydantic, async + retries, pandas/DuckDB, pytest, FastAPI) | 8 | 16 | 12 | 24 |
| T3 | Prompting and structured outputs (schema-constrained) | 10 | 16 | 8 | 16 |
| T4 | Tool use / function calling; hand-written tool loop | 7 | 12 | 6 | 14 |
| T5 | RAG: ingestion, chunking, hybrid + rerank, retrieval metrics, ACL | 18 | 36 | 14 | 36 |
| T6 | **Evals**: error analysis, golden sets, validated judges, CI regression gate | 18 | 30 | 12 | 30 |
| T7 | Agents and multi-agent patterns; bounded agents | 16 | 26 | 12 | 32 |
| T8 | MCP: server, auth, threat model | 8 | 14 | 6 | 16 |
| T9 | Context engineering and prompt caching | 5 | 10 | 5 | 12 |
| T10 | Fine-tune vs RAG vs prompting (decision memo; LoRA lab in 24-wk) | 4 | 16 | 4 | 24 |
| | **Sum** | **100** | **190** | 89 | 234 |

**AI Operations & Security (D5, D3, D6)**

| T | Topic | 12-wk h | 24-wk h | R5 intro | R5 deep |
|---|---|---|---|---|---|
| T11 | Small/open models and local inference (Ollama, vLLM, sizing) | 4 | 12 | 6 | 18 |
| T12 | Multimodal (vision/docs/audio) | 0 (elective) | 6 | 4 | 12 |
| T13 | LLMOps: tracing, cost/latency, caching, routing, reliability harness | 10 | 18 | 10 | 24 |
| T14 | AI deployment: containers, K8s, GPU basics (AI-specific increment) | 6 | 12 | 8 | 28 |
| T15 | MLOps and data pipelines (incremental sync, quality gates) | 2 | 10 | 6 | 20 |
| T16 | Guardrails | 4 | 6 | 4 | 10 |
| T17 | Prompt injection and AI security; red-teaming | 8 | 14 | 8 | 20 |
| T18 | Privacy and compliance (data-flow diagram, PII, deletion) | 4 | 5 | 4 | 10 |
| T19 | Responsible AI (system card, slice analysis) | 2 | 3 | 3 | 8 |
| T20 | Human-in-the-loop design | 4 | 4 | 4 | 10 |
| T21 | Enterprise integration (OIDC/SSO, per-user ACL, connectors, legacy adapters) | 8 | 20 | 8 | 24 |
| | **Sum** | **52** | **110** | 65 | 184 |

(R5's intro column sums to 154 across both tables and its deep column to 418. Ours: 12-week 152 total, 24-week 300 total.)

### 7.4 Foundations block detail

**12-week foundations (146 h)**

| Block | Topics | Hours |
|---|---|---|
| Onboarding and baseline (10) | Accounts, tooling, norms (4) · **G0**: 60-Q exam, broken-env practical, mock discovery call (6) | 10 |
| Software fundamentals (32) | Dev toolkit: shell, git, editor, debugging (6) · Python for ops + pytest (8) · Linux, networking, DNS/TLS/HTTP (10) · SQL, API design, data modeling, "report that's always wrong" mini-lab (8) | 32 |
| Cloud / AWS (36) | IAM, VPC, compute, storage, managed databases, serverless, billing and cost controls (AWS core, cloud-practitioner/SAA domains as *syllabus*, no exam) | 36 |
| DevOps / K8s (48) | Docker (8) · CI/CD with GitHub Actions (10) · Terraform (12) · Kubernetes: workloads, services, troubleshooting (12) · observability and SRE basics: SLOs, alerts, postmortems (6) | 48 |
| DevSecOps (20) | IAM least privilege, secrets, image scanning (6) · pipeline security: SAST, SCA, DAST, IaC scan, SBOM (8) · threat modeling and security-review rehearsal (6) | 20 |

**24-week foundations (292 h)**

| Block | Topics | Hours |
|---|---|---|
| Onboarding and baseline (16) | Setup and norms (6) · **G0** (6) · AI-assisted development practice and "how to ask for help / write a good issue" (4) | 16 |
| Software fundamentals (56) | Toolkit (8) · Python + testing (14) · Linux/networking/web (16) · SQL, API, data modeling (12) · **reading unfamiliar codebases and code review** (6) | 56 |
| Cloud / AWS (72) | AWS core (40) · networking and IAM in depth (16) · managed data, serverless, FinOps and cost allocation (16) | 72 |
| DevOps / K8s (104) | Docker (12) · CI/CD (20) · Terraform incl. state, modules, multi-environment (28) · Kubernetes incl. CKA-style troubleshooting drills, no exam (32) · observability, SRE, incident response, fault injection (12) | 104 |
| DevSecOps (44) | Secure SDLC and pipeline (14) · supply chain, secrets, IAM (10) · Kubernetes and cloud security (10) · threat modeling and security-review defence (10) | 44 |

### 7.5 How research inputs were compressed, and what is cut or deferred

**Input vs budget**

| Area | Research input | 12-week budget | 24-week budget | How it was compressed |
|---|---|---|---|---|
| Software + cloud + DevOps + DevSecOps | R2: ~256 h for a 12-week "deployable and secure" core (incl. ~40 h capstone); ~515–575 h for 24 weeks incl. cert prep and CKA | 146 h + P1 (8) | 292 h + P1–P4 (56) | CS-literate learners (no CS50-style theory, no "learn Python"); **no cert prep** (~60–80 h in R2's 24-week plan); GitHub Actions only (Jenkins/Nexus/Ansible dropped as dated); K8s taught to troubleshooting depth, not CKA exam speed; one end-to-end project replaces the Cloud Resume Challenge capstone |
| AI | R5 Option A: ~190–210 h in ~5.5–6 weeks; Option B: ~385 h in ~10–12 weeks (both incl. capstone) | 152 h + 56 AI-centric project h = **208 h** | 300 + 112 = **412 h** | Matches R5's range; labs run on one running case study; direct-API-first avoids framework re-teaching |
| Customer craft | R4: ~3 h/week Customer Lab across ~26 weeks (~78 h) | 32 + ≈30 embedded | 72 + ≈70 embedded | Same weekly cadence, shorter horizon |
| Pedagogy | R3: gating, slack and consolidation | 28 + 38 h | 48 + 64 h | Slack is explicit and ring-fenced |

**What the 12-week program cuts or defers, and what the 24-week program keeps**

| Topic | 12-week | 24-week |
|---|---|---|
| Fine-tuning (T10) | Decision memo only; no training run | Decision memo + LoRA/QLoRA lab on an open model ≤8B; distillation optional |
| Multimodal (T12) | Elective only | 6 h: invoice extraction with vision-LLM vs OCR |
| MLOps pipelines (T15) | 2 h, folded into the RAG sync lab | 10 h: incremental sync, quality gates, versioned eval artifacts |
| Kubernetes autoscaling on queue depth, GPU serving (T14) | Demo / reading | Hands-on, shared GPU pool |
| Multi-agent orchestrator-workers lab (T7) | Reading + cost-multiple discussion | Lab with pre-declared margin and cost multiple |
| ML/DL from scratch (T1 deep) | None | Optional walkthrough |
| Open-model sizing and load test (T11) | Instructor demo | Hands-on |
| Terraform multi-env state, module authoring | Basics only | Full |
| Privacy drills (DPIA-lite, right-to-delete) | Conceptual + data-flow diagram | Hands-on drills |
| Responsible-AI slice analysis | Dropped | Included |
| Embedded pod on real low-risk work | Not available | Weeks 22–23 |
| Specializations (e.g. Security Operations, Quantum-safe, Cloud Security Architecture from the anyops files) | **Deferred**, post-program | **Deferred**, post-program electives |
| External certifications | None funded or gated (cert-aligned syllabus only) | Same |
| EU AI Act specifics | Conceptual only; dates are in flux **[Sourced: R5 flags]** | Same |
| Other clouds | Conceptual comparison only | Same |

### 7.6 Feasibility check: hours by phase

Each program is split into five phases whose capacity (40 h × weeks) is filled exactly. **Phase boundaries and gate days are indicative; the plans fix them.**

**12-week (480 h)**

| Phase (weeks) | A Foundations (1–4) | B Secure + AI on-ramp (5–6) | C AI build (7–9) | D Operate + enterprise (10–11) | E Capstone (12) | Total |
|---|---|---|---|---|---|---|
| Onboarding | 10 | | | | | 10 |
| Software fundamentals | 32 | | | | | 32 |
| Cloud / AWS | 36 | | | | | 36 |
| DevOps / K8s | 42 | 6 | | | | 48 |
| DevSecOps | 6 | 14 | | | | 20 |
| AI Core | | 37 | 63 | | | 100 |
| AI Ops and Security | | 4 | 18 | 30 | | 52 |
| Customer Labs | 10 | 5 | 8 | 9 | | 32 |
| Projects | 8 (P1) | | 24 (P5, P6) | 20 (P3+4, P7) | 32 (P8) | 84 |
| Assessment | 5 (G1) | 4 (G2) | 6 (G3) | 5 (G4) | 8 (G5) | 28 |
| Slack | 11 | 10 | 1 | 16 | | 38 |
| **Phase total** | **160** | **80** | **120** | **80** | **40** | **480** |
| **Gate at end** | G1 Day 20 | G2 Day 30 | G3 Day 45 | G4 Day 55 | G5 Day 60 | |

**24-week (960 h)**

| Phase (weeks) | A Foundations (1–10) | B Consolidate + AI on-ramp (11–12) | C1 AI Core (13–18) | C2 AI Ops (19–21) | D Customer and pod (22–24) | Total |
|---|---|---|---|---|---|---|
| Onboarding | 16 | | | | | 16 |
| Software fundamentals | 56 | | | | | 56 |
| Cloud / AWS | 72 | | | | | 72 |
| DevOps / K8s | 104 | | | | | 104 |
| DevSecOps | 44 | | | | | 44 |
| AI Core | | 30 | 160 | | | 190 |
| AI Ops and Security | | | 30 | 80 | | 110 |
| Customer Labs | 30 | 6 | 18 | 8 | 10 | 72 |
| Projects | 40 (P1–P3) | 16 (P4) | 24 (P5) | 24 (P6) | 80 (P7, P8) | 184 |
| Assessment | 11 (G1, G2) | 4 (mid) | 8 (G3) | 8 (G4) | 17 (pod, G5) | 48 |
| Slack | 27 | 24 | 0 | 0 | 13 | 64 |
| **Phase total** | **400** | **80** | **240** | **120** | **120** | **960** |
| **Gate at end** | G1 Day 40, G2 Day 50 | Mid review Day 60 | G3 Day 90 | G4 Day 105 | Pod Day 115, G5 Day 120 | |

Row and column sums verified: every block row equals §7.2, and every phase column equals 40 h × its weeks.

**Two honest warnings:** (1) The 24-week AI phases are fully booked with zero slack; a stall in AI Core has no buffer except the consolidation window already spent earlier, so the plans should move some of phase A's 27 slack hours later if the pilot shows AI overrun. (2) In the 12-week program, weeks 7–9 carry a heavy 63-hour AI Core load; this is the most likely place for the "40% of the cohort stalls" rule (§6.8) to trigger.

---

## 8. Carried customers and project spine

### 8.1 Two fictional customers (synthetic; no real company data) **[Judgment]**

Two customers rather than one: a commercial, cost-sensitive one for early work, and a regulated one for the AI and security work. Details are invented for training and may be adapted.

| | **Kestrel Freight** (commercial) | **Linden Claims Services** (regulated) |
|---|---|---|
| Business | Regional freight and warehousing, ~600 staff | Claims administrator for regional insurers, ~1,200 staff |
| Estate | Spreadsheets and email; a legacy warehouse system with a flaky SOAP API and fixed batch windows; an executive KPI dashboard nobody trusts | 5,000+ documents: SOPs, policy wording, scanned claims, spreadsheets, HTML/DOCX (mirrors the repo corpus mix **[Repo: Ops Guide §4]**); a legacy claims system exporting SFTP batch files |
| Constraints | Cost-sensitive; cloud-friendly (AWS); one overworked IT lead | SSO (OIDC) over an LDAP-backed legacy; data must stay in-region; an air-gapped analyst enclave; SOC 2 / ISO 27001 questionnaires; an outsourced platform provider with a five-day change SLA **[Repo: Handbook Week 12 example]** |
| Stakeholder personas | COO sponsor (wants speed) · warehouse supervisor (knows the reality) · IT lead (overloaded) · finance analyst (owns the "wrong report") | VP Claims Operations (sponsor) · CISO delegate (blocks on data) · senior adjuster (end user, reveals truth only to good questions) · compliance officer · outsourced platform manager |
| Used in | P1, P2, P3, P7 | P4, P5, P6, P7 (a prospect), P8 (**the carried system**) |

### 8.2 The eight projects (from R4 §3.5, adapted to AWS and to AI-first emphasis)

| ID | Project | Customer | What it tests | Deliverables |
|---|---|---|---|---|
| **P1** | *Lift the spreadsheet*: discover, scope, then deploy a minimal secured cloud app (IaC, auth, backups, cost cap) | Kestrel | Discovery (Mom Test), IaC, basic operability | Scope one-pager, deployed service, cost and risk note, runbook |
| **P2** | *The report that is always wrong*: trace provenance, find schema-vs-meaning gaps, build a validated pipeline | Kestrel | Root-cause with evidence (5 Whys with limits), data quality | Answer-first findings memo, pipeline, tests |
| **P3** | *Integration with a hostile legacy system*: resilient adapter with retries, idempotency, monitoring, rollback; requirement changes mid-project | Kestrel | Integration, expectation management, scope negotiation | Adapter, monitoring, change log, scope-negotiation note |
| **P4** | *Constrained environment*: run the service (a) offline in an air-gapped lab and (b) under a data-residency rule; a role-played CISO reviews the data flow | Linden | Security and compliance conduct; the "tooling assumes internet" reality | Threat model, offline deployment guide, accreditation-style checklist |
| **P5** | *LLM workflow for a document-heavy process* (claims/SOP assistant): define "good" with the client, labelled eval set, simple workflow before an agent, report accuracy/cost/latency | Linden | Honest capability framing, evals, RAG | Eval report, demo, "what it cannot do" page |
| **P6** | *Agent with tools (MCP)*: read-only first, then write with human approval; provenance, audit logs, guardrails | Linden | Tool design, agent safety, adoption planning | Architecture, safety review (lethal-trifecta audit), user-training session |
| **P7** | *Scoping sprint* (no build): three vague prospects, discovery calls, a PR/FAQ and a 2-page staged proposal for one; panel defence | Kestrel expansion + two new vignettes | Scoping, stakeholder mapping, executive communication | PR/FAQ, proposal, defence |
| **P8** | *Flagship end-to-end engagement with handover*: discovery → scope → build → demo → security review → production → handover to a role-played ops team that runs it for a week and files two seeded incidents | Linden (the carried system) | Everything | Handover pack, retrospective, product-feedback memo, the nine deliverables (§8.5) |

Optional extension: **reverse engagement**, where a learner inherits another learner's project via the handover pack and must keep it running (tests runbook quality from the receiving side) **[Sourced: R4 §3.5]**.

### 8.3 Mapping to each program

**12-week (84 project hours)**

| Project | Weeks | Hours | Notes | Linked gate |
|---|---|---|---|---|
| P1 Lift the spreadsheet | 1–4 | 8 | Minimal version; ship-in-week-1 is its first slice | G1 |
| P2 Report always wrong | n/a | 0 | **Folded into the software-fundamentals data mini-lab** (inside block 2 hours) | |
| P5 Document workflow with evals | 7–8 | 14 | The carried system starts here | G3 |
| P6 Agent with tools / MCP | 8–9 | 10 | Extends the carried system | G3 |
| P3 + P4 combined "Linden enclave" | 10 | 12 | Legacy batch adapter + OIDC/ACL + air-gap/residency, on the carried system | G4 |
| P7 Scoping sprint | 10–11 | 8 | | |
| P8 Capstone | 12 | 32 | The Linden carried system taken to a production-grade handover; Mon brief → Fri defence (**[Repo: Week 12 structure]**) | G5 |
| **Total** | | **84** | AI-centric (P5, P6, P8) = **56 h** | |

**24-week (184 project hours)**

| Project | Weeks | Hours | Linked gate |
|---|---|---|---|
| P1 Lift the spreadsheet | 4–8 | 12 | G1 |
| P2 Report always wrong | 6–7 | 12 | |
| P3 Hostile legacy integration | 9–10 | 16 | |
| P4 Constrained environment | 11–12 | 16 | Mid review |
| P5 Document workflow with evals | 13–18 | 24 | G3 |
| P6 Agent with tools / MCP | 19–21 | 24 | G4 |
| P7 Scoping sprint | 22 | 16 | |
| P8 Flagship engagement (includes the embedded pod phase on real low-risk internal/partner work, weeks 22–23) | 22–24 | 64 | Pod review, G5 |
| **Total** | | **184** | AI-centric (P5, P6, P8) = **112 h** |

### 8.4 The simulated-client format **[Sourced: R4 §3.2; Judgment on staffing]**

**Escalating realism:**

| Stage | 12-week | 24-week | Format |
|---|---|---|---|
| 1. Scripted-vague client | Weeks 1–6 | Weeks 1–10 | Actor holds a hidden "real problem" sheet; reveals facts only to well-formed questions (specific past events); politely flatters bad questions (counters the "colleague actors are too helpful" problem) |
| 2. Adversarial stakeholders | Weeks 7–10 | Weeks 11–18 | Panel of three: sponsor (wants speed), skeptical technical lead (probes limits), compliance owner (blocks on data); the learner must produce one aligned plan |
| 3. Living client across a project | Weeks 9–12 (the carried system) | Weeks 13–24 | One persistent client changes requirements mid-build, goes quiet, escalates, runs a security review |
| 4. Real-world exposure | Not available | Weeks 22–23 | Embedded pod on low-risk real internal or partner work with a senior FDE mentor |
| 5. Fresh-eyes review | Capstone | Capstone and P3 | A different person operates the learner's handover pack (runbook cold-test), borrowing SRE onboarding practice |

**Rules common to all stages**
- **Retry rule:** one retry within 48 h after feedback; the delta between attempts is graded (call-audit practice from sales-engineering enablement, **[Sourced: R4 §2.6, vendor sources]**).
- **Who plays the client:** facilitators, program staff, and trained volunteers (alumni or colleagues). Actors are *trained* to be unhelpful in realistic ways and use hidden-fact sheets. **[Assumption: expect ~1 actor-hour per pod-hour of simulation; budget in §11.]**
- **Game days include non-engineer voices** (AWS Well-Architected guidance, **[Sourced: R3]**): a role-played customer demanding status during G4.
- **AI role-play** is a supplement for extra reps only, never a substitute for humans (no efficacy evidence found).
- Calibrate assessors on recorded examples before each cohort.

### 8.5 The nine capstone deliverables **[Repo: Handbook Week 12, adapted]**

| # | Deliverable | Domains | Adaptation |
|---|---|---|---|
| 1 | Scoping document with measurable success criteria | D6 | Must include out-of-scope and riskiest assumption |
| 2 | Architecture document with ADRs and security control mapping | D2, D3, D6 | |
| 3 | Working system deployed via IaC, meeting a stated **eval threshold** | D2, D4 | Thresholds as G3 (§6.3) |
| 4 | CI/CD pipeline | D2, D4 | **Includes the eval regression gate** |
| 5 | Observability with SLOs and burn-rate alerts | D2, D5 | **Plus LLM tracing and a cost/latency dashboard** |
| 6 | Security evidence pack: SBOM, scans, IAM matrix, threat model | D3 | **Plus OWASP LLM01–10 control map and a system card** |
| 7 | Cost model with unit economics | D5 | |
| 8 | Operator runbook and handover plan | D5, D6 | **Plus product-feedback memo** ("pattern vs bespoke") |
| 9 | One-page non-technical executive summary | D6 | |

**Three planted complications** in the G5 brief, capped at three **[Repo]**. Example complication families: a residency or air-gap rule, an unreliable legacy source, a stakeholder who was never told.

---
## 9. Lab environment and fault library

### 9.1 Principles

1. **Real tools, real breakage, in a sandbox that can be reset in minutes** (Google's Breakage Service idea **[Sourced: R3 §1.6]**; repo fault library **[Repo: Ops Guide §3]**).
2. **Every gate uses a novel environment with a randomised fault variant.**
3. **Cost is a controlled variable**, not an afterthought: guardrails are layered (§9.2).
4. **No real customer data, ever.** All corpora, documents and personas are synthetic or licensed.
5. **Everything is provider-swappable** (P16): model IDs in config; labs run against ≥2 endpoints.

### 9.2 AWS sandbox model **[design suggestions, not sourced facts, except where marked]**

| Item | Design |
|---|---|
| Isolation | One **AWS account per learner** under a cohort OU in AWS Organizations; no cross-account access **[Repo: "dedicated account", adapted to AWS]** |
| Budget | **$500/month hard cap** with alerts at 60% and 85% **[Repo: Ops Guide §4]**. **Caveat:** AWS Budgets can run automatic actions (apply an IAM policy or SCP, stop EC2/RDS) but data lag is not stated, so a Budget alone is *not* an instantaneous hard cap **[Sourced: R2 §3.3]**. Therefore use layers below. |
| Layer 1: SCP deny-list | Region lock; instance-type and size caps; expensive services denied by default (NAT gateways, large GPU instances, EKS control planes) and enabled only inside scheduled lab windows |
| Layer 2: Budgets actions | At 50/80% attach a deny policy via Budgets action |
| Layer 3: tagging | `cohort`, `learner`, `lab_id` required on create; untagged resources reaped **[Repo]** |
| Layer 4: teardown | Nightly **aws-nuke** on non-persistent resources, **dry-run first**; the carried system is persistent. Verify aws-nuke's safety features (alias check, dry-run) on the current release before use; the fetched README did not show them **[Sourced: R2 §3.3]** |
| Kubernetes | **kind/minikube locally** for most K8s labs; managed EKS only in scheduled windows to control cost **[Judgment]** |
| Supplementary free labs | AWS Builder Labs / Builder Sandbox (8 h temporary accounts) as extra practice, not as a dependency **[Sourced: R2 §3.3]** |
| Fault injection | **AWS FIS** and **LitmusChaos** run from pre-approved templates with stop conditions tied to alarms; run in pre-production first **[Sourced: R2 §3.3]** |
| AI keys and spend | Provider keys held in a **gateway** with per-learner spend caps; no keys in repos or notebooks; cap reviewed weekly **[Judgment]** |
| Isolation of the "carried system" | Each pod's carried system runs in its own account and namespace so one pod's failure cannot cascade |

### 9.3 Compute for AI: laptops, shared GPU, managed endpoints

| Layer | Spec | Notes |
|---|---|---|
| Laptops | 16 GB RAM, 100 GB free disk **[Repo: Prep Guide]** | Small quantised open models run locally via Ollama/llama.cpp |
| Managed endpoints | Claude via the provider API or Amazon Bedrock; ≥1 OpenAI-compatible endpoint | Provider-neutral requirement (P16) |
| Shared GPU pool | **4 × A100 40GB or 8 × L4 for a cohort of 10**, queued via a scheduler; utilisation target 60–85% **[Repo: Ops Guide §4]**. For a cohort of 15 resize to roughly 1.5× **[Assumption]**, or rent on demand. | Queueing teaches quota discipline. Peak use: open-model serving and LoRA weeks. 12-week use is small (demos and one sizing exercise); 24-week use is heavy |
| Model licences | Open-weight models have different licences (e.g. Llama Community Licence terms need legal review) **[Sourced: R5 T11]** | Include the licence check in the T11 lab |

### 9.4 Air-gapped lab **[Repo: Ops Guide §4, extended for AI]**

| Item | Spec |
|---|---|
| Isolation | A genuinely isolated VPC with **no egress at all**: a missing route, not a restrictive security group. A firewall rule can be discovered and worked around; a missing route cannot. |
| Registry and packages | Internal mirror pre-seeded with approved images; internal PyPI and npm mirrors |
| Access | Bastion with no outbound route |
| **AI additions** | Pre-staged open-model weights, a local embedding model, and an offline vector database; the learning is in the **pre-staging discipline** |
| Used by | P4 (constrained environment), the Linden enclave, `FIELD-AIRGAP` |

### 9.5 Data and RAG corpora

| Item | Spec |
|---|---|
| Starter corpus | ~200 documents (PDFs, HTML, a messy Word export) for the first RAG labs, with 40+ hand-written questions and gold source passages **[Sourced: R5 T5 lab 1]** |
| Main corpus | **5,000 synthetic enterprise documents**: 40% clean PDFs · 30% scanned PDFs of varying quality · 20% spreadsheets · 10% inconsistent HTML/DOCX **[Repo: Ops Guide §4]**; built T−4 weeks |
| Golden set | 100 questions with human-verified answers and citations; **held out entirely**; plus a **separate 50-question dev set**; built by a **different person** from whoever tunes retrieval **[Repo]** |
| Extras | Planted PII for redaction labs; department tags for ACL labs; a separate "poisoned" document set for injection scenarios |
| Provenance | Synthetic or licensed content only; documents record their origin |

### 9.6 Fault library v2: 40 scenarios (32 inherited and renumbered + 8 new) **[Repo: Ops Guide §3; extensions are Judgment]**

**Design rules (unchanged from the repo):** every fault has occurred in a real engagement (or a documented real failure class); 3–5 variants per fault, randomly assigned per learner; **reset in under 5 minutes** (air-gap excepted at ~20 min); Terraform or Kustomize defined; each fault has a README with Symptom, Root cause, Expected diagnostic path, **Known stall points (an enumerated list, so telemetry is comparable)**, Real-world provenance, and a one-line Reset command. Without an enumerated stall-point list the 40% rule (§6.8) cannot be computed.

**Key change:** scenarios are keyed by **stable names, not numeric lab IDs**, because the repo's lab numbering is inherited from the 26-week program and collides (Appendix A). Plans reference scenario names.

| Family | IDs | Count | 12-wk | 24-wk | Origin |
|---|---|---|---|---|---|
| Network | `NET-PROXY`, `NET-CA`, `NET-DNS`, `NET-MTU`, `NET-IPV6` | 5 | 5 | 5 | Repo |
| App | `APP-RACE` | 1 | 1 | 1 | Repo |
| IaC | `IAC-DRIFT` | 1 | 1 | 1 | Repo |
| Kubernetes | `K8S-IMGPULL`, `-CRASHLOOP`, `-PENDING-GPU`, `-OOM`, `-NETPOL-DNS`, `-WEBHOOK-CERT`, `-PVC-TERM`, `-DISKPRESSURE`, `-HPA-NOMETRICS`, `-WEBHOOK-REJECT` | 10 | **6** (IMGPULL, CRASHLOOP, PENDING-GPU, OOM, NETPOL-DNS, HPA-NOMETRICS) | 10 | Repo |
| Game day | `GAMEDAY-1..5` | 1 | 1 | 1 | Repo |
| Security | `SEC-ROOT`, `-SECRETS`, `-RBAC`, `-NETPOL-OPEN`, `-UNENCRYPTED` (re-expressed for AWS IAM and K8s) | 5 | 5 | 5 | Repo |
| Injection | `AI-INJECT-INDIRECT` (Repo), **`AI-INJECT-TOOL`** (injection via a tool result) | 2 | 2 | 2 | Repo + New |
| MCP | **`MCP-TOKEN`** (token passthrough / over-scoped server) | 1 | 1 | 1 | New |
| RAG | `RAG-FAIL-1..6` (one set per failure-taxonomy category), **`RAG-ACL`** (cross-user leak) | 2 | 2 | 2 | Repo + New |
| LLM behaviour | **`LLM-REGRESS`** (silent prompt/model-version regression), **`LLM-CTX`** (context overflow / truncation), **`LLM-PROVIDER`** (429s and outage: failover), **`LLM-COSTBURN`** (runaway agent loop, 6× spend) | 4 | 4 | 4 | New |
| Evals | **`EVAL-JUDGE`** (miscalibrated LLM judge) | 1 | 0 | 1 | New |
| ML/data | `ML-LEAKAGE`, `DATA-SKEW`, `DATA-SILENT` (renamed from MLOPS-SKEW/-SILENT) | 3 | 0 | 3 | Repo |
| Production sim | `PROD-SIM-1..5` (AI injections: provider outage, poisoned document, 10× spike, prompt regression, 6× cost burn) | 1 | 1 | 1 | Repo (injections as in Assessment Pack G4) |
| Field | `FIELD-AIRGAP` (six-constraint environment), `FIELD-BLIND` (diagnosable only via an operator proxy) | 2 | 2 | 2 | Repo |
| Baseline | `G0-LAYERED` (three layered faults) | 1 | 1 | 1 | Repo |
| **Total** | | **40** | **32** | **40** | 32 Repo + 8 New |

**Build sequence [Repo: T−8 to T−1; Assumption on effort]:** build the **12-week subset of 32 first** by T−8 weeks; the 8 new AI scenarios need AI corpora and tracing in place, so schedule them after the RAG corpus (T−4). Fault-library build is the single largest pre-launch effort (§11).

### 9.7 Cost placeholders **[Assumption; order-of-magnitude only; validate in the pilot]**

| Line | 12-week, 15 learners | 24-week, 15 learners | Basis |
|---|---|---|---|
| AWS sandboxes | $7k–$14k | $14k–$27k | Expected spend $150–300/learner/month against the $500 cap |
| LLM API spend | $1.5k–$4k | $3k–$8k | $100–250 and $200–500 per learner |
| GPU (pool or on-demand) | $8k–$20k | $15k–$35k | Repo reference: **$23k** GPU line for a cohort of 10, 12-week **[Repo: 12-Week Deck]**; 12-week AI use here is lighter |
| Air-gap lab and tooling | $4k–$8k | $6k–$12k | Repo reference: $2k air-gap + $6k tooling **[Repo]** |

Repo reference totals for a **cohort of 10, 12-week:** about **$41–51k** (Handbook) and **$46k infrastructure** (Deck) **[Repo]**. The repo's Handbook gave a cost metric of ≤$600/learner/month while its Ops Guide capped at $500; this design uses **$500** (Appendix A).

---

## 10. Tooling stack

Status flags come from R2 and R5: **[V]** verified on a primary page · **[S]** search snippet / secondary source · **[U]** unverified or from background knowledge, re-check before a syllabus. **Model names, framework versions, prices and spec revisions move fast; re-verify at delivery.**

| Layer | Default | Alternatives / notes | Status |
|---|---|---|---|
| Language and dev | Python 3.12+, `uv`, pytest, ruff, pydantic v2, FastAPI, httpx; Git + GitHub; GitHub Actions | A second language is read-only fluency | Standard, not re-verified [U] |
| Data | Postgres (+ `pgvector`), DuckDB, pandas or polars | | [U] |
| Cloud | **AWS**: IAM, VPC, EC2, S3, RDS, Lambda, ECS/EKS, CloudWatch; Bedrock optional for managed models | Azure/GCP: conceptual comparison only | [V] (AWS certification domains used as syllabus) |
| IaC | Terraform | OpenTofu for customers avoiding HashiCorp licensing: **not researched** | Terraform [V]; OpenTofu [U] |
| Containers / K8s | Docker; kind/minikube; EKS in scheduled windows; Helm/Kustomize | Argo CD / Flux [U] | [V] for K8s exam structure; rest [U] |
| Observability | Prometheus, Grafana, CloudWatch, OpenTelemetry | | [U] |
| AI tracing and observability | **Langfuse** (OTel-native in v4) or **Arize Phoenix** (choose one per cohort) | **OpenTelemetry GenAI semantic conventions are still experimental**; content capture is opt-in | [S] |
| DevSecOps | SAST (Semgrep), SCA/image scan (Trivy), secrets scan (gitleaks/TruffleHog), SBOM (CycloneDX), DAST (OWASP ZAP), policy-as-code (OPA) | **OWASP Juice Shop** as the free target; OWASP DevSecOps Guideline as the pipeline checklist | Juice Shop and OWASP guideline [V]; tool names [U] / **[Repo]** |
| Chaos and cleanup | AWS FIS, LitmusChaos, aws-nuke | Verify aws-nuke safety features | [V] (page read; safety features not shown) |
| LLM access | **Claude as default** (direct API or Bedrock) + ≥1 OpenAI-compatible endpoint (hosted or local) | **Model IDs in config only.** Caching, pricing and model lists change quickly | [V] for Anthropic docs read; model lists volatile |
| Structured output | Provider schema-constrained output (Anthropic: `json_schema`, strict tool use) | Instructor (API models), Outlines (self-hosted) | Anthropic [V]; Instructor/Outlines [V via Applied LLMs] |
| Agents | **Hand-written tool loop first**, then **LangGraph** (reported 1.0) | Read one vendor SDK (Claude Agent SDK, OpenAI Agents SDK) | LangGraph [S]; SDK claims [S]/[U] |
| MCP | Official Python/TypeScript SDKs, MCP Inspector | **Spec revision `2026-07-28`: stateless; roots, sampling, protocol logging and dynamic client registration deprecated; Tasks and MCP Apps are extensions; token passthrough forbidden.** **Pre-2026 tutorials are out of date.** | [V] |
| RAG | `pgvector` default; BM25 via Postgres FTS/OpenSearch; hybrid with reciprocal rank fusion; a reranker; contextual chunking | Qdrant (filtered search), Weaviate (hybrid), Chroma (prototyping); parsers: unstructured, docling, PyMuPDF; Cohere Rerank or open cross-encoders. Vector DB benchmarks conflict: test on own data | Mixed [S]/[U] |
| Evals | **pytest and plain Python first**; then a platform | Promptfoo (**ownership claim unverified**), DeepEval, Inspect AI, Ragas; versions conflict across sources | [S]/[U] |
| Local and open models | Ollama (dev), llama.cpp (edge), **vLLM** (concurrent serving) | KServe + llm-d as advanced awareness only | [S] |
| Gateway | LiteLLM or equivalent for retries, fallbacks, per-learner budgets | Cloud gateways | [S] |
| Guardrails | pydantic/JSON-schema validators, Presidio (PII), provider moderation endpoints | NeMo Guardrails, Guardrails AI, Llama Guard / Prompt Guard | [S]/[U] |
| Identity (labs) | Keycloak or an Auth0/Entra test tenant | | [U] |
| Program telemetry | Working Plan Workbook design from the repo (§6.9), adding AI fields | A BI tool later | **[Repo]** |

**Do not teach or depend on:**
- **OpenAI Assistants API**: scheduled shutdown 26 Aug 2026 **[S]**.
- **Pre-2026 MCP tutorials** (session IDs, sampling): out of date **[V]**.
- **LLM Guard**: reported archived Jul 2026 **[U]**; Guardrails AI acquisition claim **[U]**.
- **Jenkins/Nexus/Ansible as the main stack**: dated relative to GitHub Actions and IaC-first workflows **[Judgment, R2 §1.10]**.
- **Detectors as a security boundary**: adaptive attacks bypassed 12 published defences at >90% success **[V: Willison summary, R5]**.
- **Hard-coded model IDs** in labs.

**Standards referenced:** **OWASP Top 10 for LLM Applications 2025** (LLM01 Prompt Injection … LLM10 Unbounded Consumption) **[V]** · NIST AI RMF and the GenAI Profile (AI 600-1), noted as under revision **[V]** · EU AI Act: provisional "Digital Omnibus" deal reported May 2026 to delay high-risk obligations; **final adoption and GPAI obligations not verified** **[S]/[U]**: teach conceptually only.

---

## 11. Budget and staffing outline (pilot) **[Assumption: all figures are to be validated]**

No salary figures are included. Staffing is in FTE so you can price it internally.

### 11.1 FTE by role

| Role | 12-week | 24-week | Notes |
|---|---|---|---|
| Program lead | 0.4 | 0.4 | **[Repo: 0.4]** |
| Lead instructors | 1.6 (2 × 0.8: an AI lead and a platform lead) | 2.4 (3 × 0.8) | ≈1 per 8 learners (R3 ranges); **[Repo: 2 leads at 0.8]** |
| Customer-craft coach | 0.5 | 0.5 | **[Repo: craft coach 0.5]**; owns the customer thread and client-actor training |
| Lab / platform engineer | 0.8 | 0.8 | **[Repo: 0.8]**; owns sandboxes, fault library, corpora |
| Technical mentors | ≈0.5 (5 × 0.1) | ≈0.5 first half, ≈0.75 in the pod phase (5 senior FDEs × 0.15) | **[Repo: mentors 0.1 each]**; 1 mentor per 3 learners |
| Program manager | 0.3 | 0.3 | **[Assumption]** |
| Wellbeing lead | 0.1 | 0.1 | **[Assumption]**; plus an external referral list |
| Alumni TAs | 0.2–0.4 | 0.4 | **[Assumption]** |
| Client actors | Staff and volunteer time, ≈1 actor-hour per pod simulation hour | Same, plus real stakeholders in the pod phase | **[Assumption]** |
| **Approx. total** | **≈4.6 FTE for 12 weeks (~55 FTE-weeks)** | **≈5.5 FTE average for 24 weeks (~133 FTE-weeks)** | For comparison, repo figures: 4.0 FTE (12-week Deck) and 4.5 FTE (anyops Architecture) |

### 11.2 Pre-launch build effort **[Assumption]**

| Item | Effort | Timing |
|---|---|---|
| Fault library (32 core, then +8) | The largest item; plan ≈4–6 FTE-weeks for the 32 and ≈2 more for the 8 | Start T−8 weeks |
| RAG corpus (5,000 synthetic documents, golden and dev sets) | ≈2–3 FTE-weeks including labelling by someone other than the retrieval tuner | By T−4 weeks |
| AWS org, SCPs, budgets, nuke pipeline, gateway | ≈2 FTE-weeks | T−6 |
| Rubric calibration and client-actor scripts (hidden-fact sheets) | ≈2 FTE-weeks | T−2 |
| Workbook / telemetry (adapt the repo Working Plan) | ≈1–2 FTE-weeks | T−3 |

Build sequence T−8 → Day 1 follows the repo **[Repo: Handbook Part IV]**.

### 11.3 Infrastructure and run costs

See §9.7 for placeholders and the repo reference of $41–51k (12-week, 10 learners). **No total is stated here because the AI API, GPU and sandbox lines are the least certain; replace placeholders with measured values after the first two weeks of the pilot.**

---
## 12. Risks, open questions, unverified items and the pilot plan

### 12.1 Risk register

| # | Risk | Why it matters | Mitigation | Basis |
|---|---|---|---|---|
| 1 | **12-week AI overload**: weeks 7–9 carry 63 h of AI Core plus projects | The most likely place for a >40% cohort stall (§6.8) | Pre-work in weeks 5–6 (T1–T4 already done); move T9/T10 to reading if the stall rule fires; keep P5/P6 scope small | [Judgment] (§7.6) |
| 2 | **24-week AI phases have zero slack** | A stall in AI Core has no buffer | Shift some of phase A's 27 slack hours later after the pilot shows where overrun occurs | [Judgment] (§7.6) |
| 3 | **The customer-skill thread is unproven** | No public curriculum or independent evidence exists that these methods improve FDE outcomes | Treat as a pilot hypothesis; measure pre/post (§12.4); keep rubrics lightweight | [Sourced: R4 §0, §5] |
| 4 | **Cloud and AI cost overrun** | Budgets are not instantaneous caps; agents can loop | Layered controls (§9.2); gateway spend caps; weekly review | [Sourced: R2 §3.3; Judgment] |
| 5 | **Fault-library build effort** is the largest pre-launch item | Late build means gates run on untested environments | Build the 32-scenario core first by T−8; AI scenarios after the corpus | [Repo; Assumption] |
| 6 | **Assessor and mentor quality** | Rubric validity is unproven; inter-assessor drift | Two assessors at G2/G4/G5; calibration on recorded examples; delta >1.0 triggers calibration | [Repo; Sourced R3, R4] |
| 7 | **Tooling churn** (MCP, agent SDKs, acquisitions, model names) | Labs and slides go stale | Config-only model IDs; teach concepts + a thin SDK; re-verify the §10 flags at T−4 | [Sourced: R5 §1] |
| 8 | **Burnout and dropout** | Bootcamp students report 10–16 h days; time constraints are the top barrier to completion | §5.4 safeguards; mentor from Day 1; early-warning indicators | [Sourced: R3 §3; observational evidence] |
| 9 | **Over-claiming** (e.g. "replicates Palantir's bootcamp"; marketing placement rates) | Palantir's internal method is not public; CFPB action shows the failure mode | Do not claim replication; publish outcomes with full denominators | [Sourced: R3 §1.7, §3] |
| 10 | **Weak evidence transfer** | Most pedagogy evidence comes from undergraduate STEM and bootcamps, not FDE work | Pilot with measurement; prefer reversible choices | [Sourced: R3 §0] |
| 11 | **Simulated clients are too easy** | Colleague actors give helpful answers | Hidden-fact sheets; adversarial personas; actor training | [Sourced: R4 §2.6] |
| 12 | **Agent/red-team safety in labs** | Agents with tools and injected content can cause real side effects | Sandbox accounts, egress controls, read-only first, human approval gates, lethal-trifecta audits | [Sourced: R5 T17] |
| 13 | **Baseline variance among new grads** | Mixed baselines slow a trio | Lanes A/B/C from G0; mixed-experience trios; fast-track tasks | [Repo; Sourced R3 expertise-reversal] |
| 14 | **Divergence from the anyops (Family C) documents** | Stakeholders may read conflicting numbers | Appendix A; state explicitly that this design supersedes them for program design | [Judgment] |
| 15 | **Licensing and provenance** (open-weight model terms, synthetic corpora) | Legal exposure | Licence check inside T11; provenance recorded per document | [Sourced: R5 T11] |
| 16 | **Cohort size and staffing assumptions** (15 learners; 1 facilitator per 8) | No rigorous evidence for ratios | Pilot, then adjust from mentor-load and gate data | [Sourced: R3 §5] |

### 12.2 Unverified items, consolidated from the research

Nothing below should be presented as fact in program materials until checked.

**R1 (AI courses):** Anthropic API-course module list comes from a Coursera mirror and a third-party write-up (the Skilljar pages returned 403); Maven syllabus has an 8-vs-9-week conflict and the full syllabus was not readable; Udacity entry rests on a third-party review; CS329S has no confirmed current offering; Berkeley Agentic AI MOOC not assessed; OpenAI Cookbook categories not confirmed; Zero To Mastery sections 10–21 not itemised; all enrolment and rating numbers are vendor self-reported.

**R2 (cloud/DevOps):** SANS course page returned 404; Full Stack Open parts 11–12 section lists unreadable; Skill Builder prices and tiers, Azure exam prices and the Terraform exam price are third-party only; SAA-C04 appears only on reseller sites; Builder Labs provisioning/teardown details not stated; aws-nuke safety features not visible on the fetched page; AWS Budgets data lag not stated; all trainee-hour figures are the researcher's estimates.

**R3 (pedagogy):** Palantir internal training not public; no current bootcamp placement or graduation rates retrieved; no rigorous evidence on instructor ratios; Meta Bootcamp's current status uncertain; several effect sizes (Kulik, Sackett, Dochy, Hannay) come from secondary summaries; **no controlled evidence found for simulated-client capstones or for novices learning from code review**; Maven completion rates are vendor claims; the mentorship finding is an observational survey (n=524, 21.4% response).

**R4 (FDE role):** no public customer-skill curriculum; Day-90 expectations are an estimate; fde.academy's weekly arc is vendor material and unsourced; Bloomberg and McKinsey pages unreachable; "Project Frontline" uncorroborated; Scale, Glean and Cohere postings not found; Databricks "not for new grads" wording from a snippet only; **no independent evidence that Mom Test, JTBD, issue trees or role-play improve FDE outcomes**.

**R5 (applied AI):** Promptfoo acquisition, LLM Guard archival and Guardrails AI acquisition are single-source claims; Microsoft Agent Framework 1.0, Google ADK GA and OpenAI Agents SDK sandbox claims are single secondary sources; EU AI Act omnibus final adoption and GPAI obligations unverified; LlamaIndex 2026 status unknown; OpenAI's agents-guide PDF unreadable; Google SAIF, provider data-retention terms and current model/price tables not covered; **all hour estimates are judgment**.

**This document:** the AI-centric project hours and embedded customer-hour memo lines (§7.2); the mapping of anyops P0–P4 to L0–L4 (needs a check against the Matrix README); every staffing, cost and cohort-size figure (labelled [Assumption]).

### 12.3 Where the research notes conflict, and how this design resolved each

| Conflict | Resolution |
|---|---|
| R2 recommends funding AWS CLF/SAA, CKA and Terraform exams (~$765/trainee) and counts cert-prep hours; the sponsor chose **no certifications** | Cert-aligned content used as syllabus only; cert-prep hours removed from budgets (§7.5) |
| R1's AI tracks (~130 h for 12 weeks; ~260–300 h for 24) vs R5's (~190–210 h; ~385 h) | R1 counts ~10–12 AI h/week; R5 ~35 h/week. This design follows **R5's volumes**, because AI is the main emphasis; R1 supplies the method patterns |
| R1 and R5 both start the AI block with an API call in week 1; the sponsor's order puts foundations first | Foundations first by sponsor decision; compensated by the **week-1 ship** (a small deployed service calling an LLM) and by seeding security and evals earlier than the AI block proper |
| R3 recommends cohorts of 16–24 with 1 facilitator per ~8 learners; the repo used 8–12 in pods of 3–4 | Pilot cohort **15** (five trios) **[Assumption]**; facilitator ratio ≈1:8 |
| R3 recommends "one reduced-load week per ~6 weeks"; the sponsor fixed 40 h/week | Reduced-load weeks are implemented as slack hours inside the 40, not as fewer scheduled hours (§5.4) |
| R4 assumes ~26 weeks and ~3 h/week Customer Lab; the sponsor wants 12 and 24 | Same weekly cadence; dedicated hours scale to 32 (12-week) and 72 (24-week) |
| R2's 12-week cloud path (~256 h) plus R5's AI path (~190–210 h) already exceed 480 h before customer work, projects and gates | Compressed per §7.5; accepted that depth is lower in the 12-week program (the honest promise in §2.5) |

### 12.4 Pilot and measurement plan

Because most customer-skill and gating choices rest on practitioner consensus rather than controlled evidence, **the first cohort is a measured pilot, not a launch.**

| What to measure | How | When | Target / decision rule |
|---|---|---|---|
| Competency lift | L0–L4 scores by two assessors | Day 2, midpoint, exit | ≥1.5 levels (12-week); ≥2.0 (24-week) [Assumption] |
| Gate health | First-attempt pass rate; inter-assessor delta; stall points | Every gate | 70–85%; delta ≤1.0; >40% stall triggers a curriculum fix **[Repo]** |
| **Customer-skill effect** (the weakest evidence) | Repeat the *same persona type* simulation at G0 (mock discovery call) and at G5; blind double-marked on recorded sessions; also R1–R9 deltas between an early and a late Customer Lab (R4 suggests week 6 vs week 20) | G0 vs G5; early vs late labs | A positive delta ≥1 level on discovery and scoping dimensions; if absent, revise the thread **[Judgment]** |
| Behavioural indicators | Time to first merged PR; PR review turnaround; time to first signal on faults; hints taken | Continuous | First merged PR in week 1 **[Sourced: R3 (Fowler/Shopify), evidence C]** |
| Eval quality | Judge TPR/TNR, regression-gate catch rate, golden-set faithfulness | G3, G4 | TPR and TNR ≥0.85; injected regression caught |
| Wellbeing | Weekly anonymous pulse; actual hours logged vs scheduled; attendance; dropout reasons | Weekly | Median logged hours ≤44/week [Assumption]; follow up on any stress spike within 48 h |
| Program health | Cost per learner vs $500 cap; GPU utilisation; instructor hours per learner-week; cohort completion | Weekly | ≤$500; 60–85%; ≤4.0; ≥85% **[Repo]** |
| Post-program | Manager survey and Day-90 supervisor rating against "trusted junior on a senior-led engagement"; 30-day and 6-month surveys (Google SRE EDU pattern) | 30 days, 90 days, 6 months | Report honestly, including shortfalls |
| Outcomes reporting | Publish cohort outcomes with full denominators and pre-declared definitions | After each cohort | **[Sourced: R3: CFPB lesson]** |

**Decision after the pilot:** adopt, adjust, or cut each element using the thresholds above. Elements that most deserve scrutiny: the 40-hour AI-heavy weeks 7–9 (12-week), the customer thread's measured effect, the 15-learner/1:8 staffing assumption, and the retake policy's effect on completion.

---

## 13. Appendix A: repo reconciliation

Each row is a contradiction found when reviewing the downloaded repo (the 12-week suite, the student kit, the 26-week set and the anyops files). "Resolution" is what this design does; the plans must follow it.

| # | Contradiction in the repo | Where | Resolution here |
|---|---|---|---|
| 1 | **Domain models differ**: Family B D3 Security & Compliance / D4 Data & ML / D5 MLOps vs Family C D3 Secure Delivery / D4 Security Operations / D5 Applied AI & MLOps | Handbook vs anyops Matrix/Architecture/Deck | One model D1–D6 (§3.2); SecOps deferred |
| 2 | **Proficiency scale and ladder collide**: L0–L4 (competency) vs P0–P4 (anyops) vs L0–L3 career ladder in anyops | Handbook, Matrix | Competency = L0–L4 only; role names carry no `L` (§2.6, §3.7) |
| 3 | **Readiness rules differ**: L2 all + L3 in any three vs P2 all + P3 in D2/D3/D6; and *Certified-Independent* needed L3 in ≥4 domains while the readiness rule said ≥3 | Handbook (two places), Matrix | One rule (L2 all + L3 in any three) = *Workstream Owner*; a lower *Supervised* tier (§6.5) |
| 4 | **Lab counts differ**: 44 (26-week), 42 (12-week), 45 (anyops) | Workbooks, decks, DOCX | No global lab count is hard-coded here; the plans define labs. Fault library is 40 (32 core for 12-week) |
| 5 | **Gate counts and wording differ**: 8 gates (G0–G7) vs 6 (G0–G5); "two of our five gates" vs six listed | Roadmap vs Handbook; Web Content/Architecture | **Six gates:** G0 diagnostic + **five assessed gates G1–G5**; wording standardised |
| 6 | **Retake rules differ**: 2-week remediation (26-week); next-week evening/weekend slack, "deliberate friction"; "two failures → other track"; anyops gate retakes at Day 25/35/45/55, G5 +6 weeks | Roadmap, Handbook, DOCX | Retakes only in scheduled slack; tiered policy with options, no automatic exit (§6.6) |
| 7 | **Day numbering**: Week 0 (Days 1–2) overlaps Week 1; "60 teaching days + 2 calibration days"; G0 on "Day 2" collides with Week 1; the Working Plan puts Day 1 at start+7 while its own Build Sequence uses start+0 | Handbook, Working Plan, Student Workbook | **No Week 0**: Week 1 starts Day 1; G0 runs Day 1 PM–Day 2 and is recorded as Day 2; 60 or 120 teaching days exactly (§6.2) |
| 8 | **Student Workbook vs Working Plan date offsets** (Day 60 at start+81 vs start+88) | Both workbooks | One start-date-driven calendar; Day 1 = the start date in every workbook (the plans' workbook spec must follow) |
| 9 | **Lab IDs collide** (e.g. 11.1 = "Break and defend your own RAG" in one file, "SIEM integration" in another; numbering inherited from the 26-week program) | Working Plan, Matrix, DOCX, Handbook | Faults keyed by stable names (§9.6); plan labs use `W{week}-L{n}` IDs |
| 10 | **Lab cost cap**: ≤$600/learner/month (Handbook metric) vs $500 cap (Ops Guide, Working Plan) | Handbook vs Ops Guide | **$500 hard cap, layered controls** (§9.2) |
| 11 | **Staffing**: 4.0 FTE (12-week Deck/Working Plan) vs 4.5 FTE (anyops); the 26-week deck smaller again | Decks, DOCX | FTE by role with a pilot estimate ≈4.6 / ≈5.5 (§11) |
| 12 | **Instruction split**: 15% vs 20% | Architecture vs Roadmap | 15/60/15/10 (§4 P1) |
| 13 | **Fault library size**: 32 (12-week, anyops) vs 40+ (26-week) | | 40 total; 32 for 12-week (§9.6) |
| 14 | **Specialization length**: "optional 3-week" in one place vs 4 weeks everywhere else | anyops Architecture §1 | Specializations are out of scope (deferred, §7.5) |
| 15 | **Week content conflicts**: Week 6 = ML/LLMs vs Security Operations; AI security in Week 7 vs Week 8; Week 10 owners differ | Handbook/decks vs anyops Deck/Matrix/DOCX | One sequence (§7.6); AI security seeded from the first AI week |
| 16 | **Craft rubric**: scored at G6+G7 (26-week) vs G2, G4, G5; threshold "≥3.5 average across all dimensions and all three events" although G2 scores only 3 of 9 dimensions | Roadmap vs Handbook; Pack | Craft scored at G2, G4, G5; **each event declares which dimensions it scores**; the threshold applies to the mean of all scored dimension-events, with no single dimension's mean below 3.0 **[Judgment]** |
| 17 | **Role ladders**: Associate / Professional / Principal / Deployment Architect vs Student / Junior / Mid / Senior (L0–L3) | Handbook vs anyops | §2.6 |
| 18 | **Orientation deck vs Handbook/Prep Guide**: "tomorrow is a baseline" vs baseline on Day 1 PM; `make verify` on Day 1 vs before Day 1; "Do the Prep Guide. Nothing else." vs the Prep Guide also asking for Handbook reading | Orientation deck, Student Handbook, Prep Guide | One instruction: pre-work = setup + light reading only; G0 runs Day 1 PM–Day 2 |
| 19 | **G1 and G3 criteria differ** between Handbook and Assessment Pack; panel-time assumptions differ; the Pack's context-precision and cost tolerance missing from the Handbook | Handbook vs Pack | Pack numbers adopted (§6.3) |
| 20 | **Minor errors**: Prep Guide says "all eight commands" but lists seven; Program Workbook README cites "cell B3" (actual C3); Handbook Layer 5 conflicts with Ops Guide on cost | various | Not carried forward; fix at source if those files are reused |
| 21 | **Overlap and duplication**: the 26-week Roadmap and the anyops Architecture share most of Weeks 1–9 verbatim; the Web Content duplicates the Architecture in marketing language | Roadmap, Architecture, Web Content | This design is **not** derived from the Roadmap; the Architecture's marketing numbers (e.g. "42 labs", "46 → 16 weeks") must not be reused without verification |

---

## 14. Appendix B: decisions needed from you

These do not block the two plan documents, which use the defaults shown, but each changes numbers if you disagree.

| # | Decision | Default used here |
|---|---|---|
| 1 | **Pilot cohort size** | 15 learners in five trios [Assumption] |
| 2 | **Pilot sequencing**: run the 12-week first and use its data to refine the 24-week? (A 24-week pilot takes ~6 months.) | 12-week first, then 24-week with changes |
| 3 | **Who funds and sponsors learners**: employer-sponsored (manager signature) or individual? | Employer-sponsored cohort contract (§6.7), adaptable |
| 4 | **Client actors**: internal staff, alumni, or paid external actors? | Staff and volunteers; budget ≈1 actor-hour per simulation pod-hour |
| 5 | **Optional self-funded exams**: mention them to learners at all? | A short note only; no funding, scheduling or gating |
| 6 | **Provider commercial terms**: Claude via the Anthropic API, Bedrock, or both? | Both allowed; gateway with spend caps |
| 7 | **Outcome publication**: publish cohort outcomes externally? | Yes, with full denominators (P18); can be internal-only |
| 8 | **Branding**: generic "FDE Academy" or anyops-branded? | Generic in this design |
| 9 | **Future specializations** (Security Operations, Cloud Security Architecture, Quantum-safe from the anyops files) | Deferred; no hours reserved |
| 10 | **Stipend and learner pay** | Not addressed in this design |

---

*FDE Program Design — Shared Foundation v0.1 · Draft for review · Document ends.*
