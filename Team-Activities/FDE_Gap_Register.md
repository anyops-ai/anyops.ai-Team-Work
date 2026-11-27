# FDE Academy
## Gap Register & Review Notes (v1.1)

**For the program lead. Findings from a full read of the document set on 2026-11-26.**

| | |
|---|---|
| **Scope reviewed** | 8 markdown documents (4,755 lines), 4 workbooks (36 sheets), 4 decks (87 slides) |
| **Findings** | 11 — 3 high, 4 medium, 4 low |
| **Addressed by this review** | 4 — G-01, G-02 and G-03 by the three companion addenda; G-10 by the README index |
| **Open for your decision** | 7 — six open (G-04, G-05, G-07, G-08, G-09, G-11) plus G-06 partially addressed |

**On the quality of what exists.** The gaps below are narrow because the document set is strong. The competency model, the gate structure, the fault library and the telemetry layers are coherent and unusually specific, and the design principle that training mirrors delivery is carried consistently through all four documents rather than asserted once. Several findings below are only visible *because* the rest is rigorous enough to make an omission conspicuous.

---

## High

### G-01 · No error and log management discipline
**Evidence.** Logs appear as one third of the observability pillar (Week 4) and as a line item in Lab 2.1. There is no instruction on log pipeline architecture, volume and cost, retention tiering, redaction, or audit-log integrity. The G2 panel question bank asks *"Show me the log that would prove this control was working last Tuesday"* (`FDE_12Week_Assessment_Pack.md:173`) and nothing in the curriculum teaches a learner to build the system that answers it.

**Why it matters for this role specifically.** Logs are the only telemetry an FDE is given on day one of an engagement — metrics and traces need a code change, an agent rollout and a security review. The program trains the instrumented case thoroughly and the inherited case not at all.

**Status.** → **Addressed.** `FDE_Log_Management_Module.md` — 3.5 hrs instruction, 4 labs, 8 new fault scenarios, no new week.

---

### G-02 · No hands-on practice resources anywhere in the document set
**Evidence.** Exactly one URL exists across all 4,755 lines of the reviewed documents, and it is an example hostname inside a lab description (`FDE_Training_Program_Roadmap.md:169`). The Student Handbook's "Study resources by domain" (Part III §4) is reading only. "Bandit" appears in the documents solely as the Python SAST tool.

**Why it matters.** Instructors have no prescribed intervention for a logged stall point beyond a hint and a 1:1, and learners have nowhere to go on the evening they are stuck on one specific thing.

**Status.** → **Addressed.** `FDE_External_Practice_Resource_Map.md` — mapped by domain and week, explicitly non-assessed, with an instructor stall-point lookup.

**One finding inside it deserves your attention directly.** SadServers is the best external platform for this program and must **not** be recommended before Day 2. It is a timed Linux diagnosis exercise and the Day 2 practical is a timed layered-fault diagnosis exercise scored on method. Learners who rehearse on it arrive with a method, score above their true level, get routed into a lane that removes the support they need, and finish with an inflated baseline — exactly the failure the Prep Guide warns about. Bandit is safe pre-program because fluency is not what the baseline measures.

---

### G-03 · Backup, restore and disaster recovery do not appear at all
**Evidence.** Zero occurrences of `backup`, `restore`, `disaster recovery`, `RTO`, `RPO`, `business continuity` or `point-in-time recovery` anywhere in the document set as reviewed — all 8 markdown documents, 4 workbooks, 4 decks and the .docx. *(To reproduce after this review: the addenda added by it naturally contain these words, so scope the search to the state at commit `954b1b8`.)*

**Why it matters.** G4 certifies an engineer to operate a production system for five days under daily failure injection, and G5 certifies them to hand a system to a client's operators. Neither currently requires that the system can be restored. The Week 11 handover pack contains ADRs and an operator runbook but no recovery procedure, and the industries named publicly — Government & Defense, Healthcare, financial services — all carry contractual recovery obligations. An FDE who cannot answer "what is your RPO?" in a client architecture review is not credible in the room, and that question is asked in every one.

**Recommendation.** Smallest viable fix, roughly 3 hours total:
- Week 3, instruction: RPO/RTO as design inputs; backup of stateful workloads; what a managed database's guarantees actually cover.
- Week 9 or 10, new lab: **restore under time pressure** — the learner restores from a backup they did not take, to a stated RPO, and reports actual recovery time against target.
- G4: one of five injections is data loss requiring a restore.
- G5 handover deliverable checklist: add a recovery procedure, making it ten items rather than nine.
- Fault library: `DATA-RESTORE` — a backup that exists but is unrestorable (wrong version, missing key, untested procedure), which is the realistic failure and the one that teaches the lesson.

**The untested-backup variant is the one that matters.** Learners will take the existence of a backup as evidence of recoverability. Watching that assumption fail once is worth more than the instruction block.

**Status.** → **Addressed.** `FDE_Backup_Recovery_Module.md` — 3.0 hrs instruction, 3 labs, an R1–R5 recovery failure taxonomy, 7 new `DR-*` fault scenarios taking the library 40→47, and changes to G2, G4 and G5. No new week.

**One finding from writing it, worth surfacing here.** The compliance map lists DORA/NIS2 as *"Executive accountability, cryptographic risk — Wk 5 awareness."* DORA's cryptographic provisions are the smaller half; Articles 11 and 12 cover ICT response and recovery, documented backup and restoration procedures, and **periodic testing of them**. HIPAA contingency planning and SOC 2 availability carry comparable obligations. The map should be corrected whether or not the module is adopted — it currently understates a commitment already made publicly. *(Article references are from secondary commentary; confirm against EUR-Lex before any client-facing use.)*

---

## Medium

### G-04 · No Active Directory, Kerberos or Windows-estate content
**Evidence.** Zero occurrences of `Kerberos`, `Active Directory`, `NTLM` or `Group Policy` across all markdown, workbooks and decks as reviewed at commit `954b1b8`. `LDAP` appears once, as a G2 panel question — *"Our IdP is LDAP, not OIDC. What changes?"* (`FDE_12Week_Assessment_Pack.md:169`) — which the curriculum does not prepare learners to answer. Identity is taught as OIDC, OAuth2, SAML, SCIM and workload identity.

**Why it matters.** The enterprise and government estates the program targets are overwhelmingly AD-backed. An FDE deploying inside a client perimeter meets Kerberos, GPO-managed hosts and domain-joined service accounts in the first week, and the program's own gate asks about it.

**Recommendation.** Half a day in Week 5, scoped tightly to the integration surface rather than to AD administration: Kerberos at the level needed to debug a failed SSO flow, AD-to-cloud federation patterns, why a domain-joined host behaves differently, and what "use a service account" means on a Windows estate. Pair it with a `IDENT-KRB` fault — a service account whose ticket renewal fails under a specific clock or SPN condition — which is both realistic and genuinely hard.

---

### G-05 · The public lab count is inconsistent across artifacts
**Evidence.**

| Artifact | Figure |
|---|---|
| Web content — marked as a figure to publish | 42 |
| Program Handbook | 42 assessed labs (~158 hrs) |
| Program Architecture markdown | 42 |
| **Academy Deck (slide 1)** | **45 labs shipped** |
| **Curriculum Matrix, Lab Catalog sheet** | **45 labs, 169.5 hrs** |
| 26-week deck | 44 |

**Why it matters.** `anyops_FDE_Academy_Web_Content.md:361` explicitly instructs the web team to publish 42 as a program fact needing no disclaimer, while the deck shown to the same audience says 45 and the underlying catalog totals 45 at 169.5 hours. Two numbers, both sourced from your own documents, differing by 11.5 lab hours.

**Recommendation.** Decide which is canonical — most likely 45 catalog entries of which 43 are assessed, since Labs 0.1 and 0.2 are diagnostic — then state the rule once in the Handbook and propagate. Adding the four labs in the log module changes this again, so fix the definition before fixing the number.

---

### G-06 · Telemetry residency contradicts the published Healthcare position
**Evidence.** The published Healthcare commitment is that zero PHI leaves the client environment. Week 4 teaches Datadog and Splunk Observability as mainline observability tooling, and Week 6 teaches Splunk and Sentinel as SIEM.

**Why it matters.** These are not in conflict as taught, but they collide in the field the first time an engineer points a collector at a namespace holding clinical data, and the FDE leads that conversation. The program should teach the resolution rather than leave learners to discover the contradiction in front of a client's privacy officer.

**Status.** → **Partially addressed** in the log module (§3.2, residency; Lab 11.6). **Still open** for SIEM and for the Week 6 CSPM tooling, where the same question applies to security telemetry and has a different answer.

---

### G-07 · The RAG corpus has an unstated provenance and consent position
**Evidence.** The corpus is specified as 5,000 documents of "anonymized enterprise policy, procedure and claims documents" (`FDE_12Week_Instructor_Lab_Ops_Guide.md`, §4). Nothing states where they come from, who anonymized them, to what standard, or under which client agreement.

**Why it matters.** "Claims documents" implies insurance or healthcare source material. Using real client documents in a training corpus — even anonymized — is a contractual and data-protection question before it is an engineering one, and re-identification risk in a 5,000-document corpus is not negligible. This is also the kind of question a client's security team asks about *your* program during a procurement review, and the answer needs to exist before it is asked.

**Recommendation.** Add a provenance and consent line to the corpus specification: source, legal basis, anonymization method, who signed off, and review date. If the documents are synthetic or public, say so explicitly — it costs one line and removes the question permanently.

---

## Low

### G-08 · Learner sustainability has no equivalent to the instructor rules
**Evidence.** The Instructor & Lab Operations Guide sets explicit sustainability rules for instructors — a 0.8 FTE ceiling, a prep ratio, no single lead across all twelve weeks. Learners carry 40 hours a week for twelve weeks, with six gates, evening remediation and a five-day simulation, and the only protections are attendance clauses that remove them from the cohort.

**Why it matters.** Every learner-side provision in the cohort contract protects the *program* from the learner's absence. None protects the learner from the program. The Week-4 intervention ("reduce lab scope, not lab count") is the one humane provision and it is reactive, triggered after someone is already failing.

**Recommendation.** Two lines, no structural change. A stated weekly ceiling on assigned evening remediation — two hours, as proposed in the practice map — and a named, non-punitive route for a learner to say they are underwater before it shows up in the telemetry. Both cost nothing and both are things a cohort will notice the absence of.

### G-09 · Two program generations coexist without a status marker
**Evidence.** The 26-week roadmap (v1.0, gates G1–G6 plus capstone) and the 12-week intensive (v2.0, gates G0–G5) sit side by side with overlapping names and incompatible gate numbering. `FDE_Training_Program_Roadmap.md` and `FDE_Training_Program.pptx` describe a different program from the rest of the set, and the 12-week documents reference the 26-week track as a live fallback for learners who fail twice.

**Why it matters.** It is a live reference, not an archive, so the ambiguity is operational: "G4" means different things in the two documents, and a reader who does not already know which generation they are holding cannot tell.

**Recommendation.** One status line in each document header — `Current` / `Superseded by v2.0, retained as the part-time track` — and a note wherever gate identifiers appear in the 26-week set.

### G-10 · The repository has no index
**Evidence.** `README.md` contains the single line `# Projects`. Twelve substantial documents in a flat directory, four of them generated views of the same content, two program generations, and no statement of which document is authoritative for what.

**Recommendation.** A README table: document, audience, status, what it is authoritative for. Fifteen minutes, and it is the first thing anyone new to the repo needs.

---

### G-11 · No method for auditing a client's existing DR estate
**Evidence.** Raised by the backup/DR module itself (§11). That module teaches graduates to build recoverable systems and to recover systems they inherit. It does not teach them to assess forty years of accumulated recovery arrangements in a bank and produce a defensible written opinion.

**Why it matters.** This is plausibly what a mature regulated client asks an FDE to do *first* — before any new system exists. It is a consulting method with its own structure, closer to the Week 11 environment-intake triage than to any engineering lab.

**Recommendation.** Specialization territory — Advanced DevSecOps or Cloud Security Architecture — not the Core. Logged so the boundary is a recorded decision rather than an oversight.

---

## Summary

| ID | Finding | Severity | Status |
|---|---|---|---|
| G-01 | No error/log management discipline | High | Addressed — see log module |
| G-02 | No hands-on practice resources | High | Addressed — see practice map |
| G-03 | Backup, restore and DR absent entirely | High | Addressed — see backup/DR module |
| G-04 | No Active Directory / Kerberos content | Medium | Open |
| G-05 | Public lab count inconsistent (42 / 44 / 45) | Medium | **Open — affects published website copy** |
| G-06 | Telemetry residency vs Healthcare commitment | Medium | Partially addressed |
| G-07 | RAG corpus provenance unstated | Medium | Open |
| G-08 | No learner sustainability provision | Low | Open |
| G-09 | Two program generations, no status marker | Low | Open |
| G-10 | Repository has no index | Low | Addressed — README index |
| G-11 | No method for auditing a client's existing DR estate | Low | Open |

**If only two things are actioned before Cohort 1:** **G-05**, because it is a factual inconsistency already instructed for publication on the website, and **G-04**, because the G2 panel asks an Active Directory question the curriculum does not prepare anyone to answer.

**The three addenda are proposals, not decisions.** They change gate criteria, the G5 deliverable checklist and the fault library size, none of which are the reviewer's call. They are written to be adopted, amended or rejected as whole units.

---

*FDE Academy · Gap Register v1.1 · Review conducted 2026-11-26, updated with the backup/DR module against the document set at commit `954b1b8`. Document ends.*
