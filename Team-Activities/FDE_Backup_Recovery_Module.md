# FDE Academy — 12-Week Intensive
## Backup, Restore & Disaster Recovery Module (Proposed Addendum v1.0)

**For the program lead, both lead instructors and the lab engineer. Companion to the Program Handbook v2.0 and the Instructor & Lab Operations Guide v2.0. Addresses gap register finding G-03.**

| | |
|---|---|
| **Status** | Proposed addendum — not yet merged into the Core |
| **Net new instruction** | 3.0 hrs, absorbed into existing blocks — no new week |
| **Net new lab hours** | 8 hrs across Weeks 3, 9 and 11 |
| **New fault scenarios** | 7 (`DR-*`), taking the library from 40 to 47 |
| **Gates touched** | G2 (two panel questions), G4 (one injection sequence variant), G5 (tenth deliverable) |

---

## 1. Why this module exists

The words `backup`, `restore`, `disaster recovery`, `RTO`, `RPO` and `business continuity` do not appear anywhere in the current document set. Not in the curriculum, not in the fault library, not in the gate criteria, not in the handover deliverables. This is the largest single omission in an otherwise unusually complete program, and it is conspicuous precisely because everything around it is rigorous.

**1. Two gates certify operation without ever requiring recoverability.** G4 certifies an engineer to run a production system for five days under daily failure injection. G5 certifies them to hand that system to a client's operators. Neither asks whether the system can be brought back. An engineer can currently hold anyops certification, be assigned to a regulated client, and have never once restored anything.

**2. The question is asked in every client architecture review.** "What is your RPO?" is not an advanced question. It is the third or fourth question a client's infrastructure lead asks, it is asked in front of the sponsor, and an FDE who cannot answer it fluently loses technical credibility in a room where credibility is the whole asset. The program trains for the G2 security panel in detail and leaves this one unrehearsed.

**3. The compliance map already commits to it, and currently maps only half of it.** The published framework list includes DORA/NIS2, positioned as *"Executive accountability, cryptographic risk — Wk 5 awareness."* DORA's cryptographic provisions are the smaller half. Articles 11 and 12 cover ICT response and recovery, a documented backup policy with frequency tied to criticality, documented restoration procedures, and **periodic testing of those procedures.** HIPAA's contingency-plan requirements carry a similar testing obligation, and SOC 2's availability criteria rest on it. The program teaches the evidence engineering for SOC 2 and ISO 27001 thoroughly and does not teach the control that four of its named frameworks require.

> **Verification note.** The DORA article references above come from secondary commentary, not the Official Journal text. Before any of this reaches client-facing material, confirm against EUR-Lex — Regulation (EU) 2022/2554, OJ L 333, 27 December 2022. The *teaching* point does not depend on exact article numbers; a compliance claim would.

**4. GitOps creates a false sense of recoverability, and the program teaches GitOps.** Week 4 teaches Argo CD app-of-apps, drift correction and automated rollback. The reasonable inference a learner draws is that the system is reconstructible from git. The cluster is. The data is not, the secrets are not, the object store is not, and the vector index is not. Teaching declarative reconstruction without teaching its boundary actively produces the misconception. **This is the single strongest argument for the module: the current curriculum does not merely omit recovery, it inadvertently teaches that recovery is already solved.**

**Provenance.** Every fault below is drawn from a failure class that recurs in regulated estates, consistent with fault library design principle 4.

---

## 2. Where it slots in — no new weeks

| Week | Block | Added | Displaces |
|---|---|---|---|
| **3** | Instruction — Kubernetes storage, stateful trade-offs | 1.5 hrs | Trim Istio to a named option; it is already qualified as "when justified" |
| **3** | Lab 5.3 (new) | 2 hrs | Net new |
| **5** | Instruction — data protection, KMS and BYOK/HYOK | 0.5 hr | Absorbed; the key-blast-radius point belongs with the key material anyway |
| **9** | Instruction — reproducibility | 0.5 hr | Absorbed into the Lab 17.1 briefing |
| **9** | Lab 17.3 (new) | 4 hrs | Net new |
| **11** | Instruction — handover | 0.5 hr | Absorbed into the Lab 23.1 briefing |
| **11** | Lab 23.3 (new) | 2 hrs | Net new |

**If the 8 lab hours cannot be found,** cut Lab 23.3 first — its cold-execution test can be folded into the existing Lab 23.1 handover pack. **Do not cut Lab 17.3.** It is the only exercise in the program where a learner performs a restore, and without it this module is a design seminar.

---

## 3. Instruction content

### 3.1 Recovery as a design input — Week 3, 1.5 hrs

**RPO and RTO as numbers someone agreed to.** What each means, who sets them (the business, not the engineer), and why an FDE's job is to surface the gap between the RPO a client *states* and the RPO their current architecture *delivers* — which in a legacy estate is routinely a factor of ten apart and has never been measured. Introduce the distinction between target and actual: **RPO and RTO are targets; RPA and RTA are what a stopwatch said during the last real restore.** Only the second pair is evidence, and most clients have only the first.

**Snapshots are not backups.** A snapshot in the same account, in the same region, deletable by the same credentials that run the workload, is a convenience feature. It protects against `DROP TABLE`. It does not protect against a deleted account, a compromised identity, a region loss, or a ransomware event where the attacker's first action is enumerating and deleting recovery points. The distinguishing property is not the technology but the **blast radius**: a backup is a copy that survives the failure of the thing it is backing up.

**Scope — the question nobody asks until the restore.** A modern application's state is not one database. It is the database, the object store, the secrets, the message queue position, the search or vector index, the IaC state, and the registry. Learners enumerate the state surface of their own Week 3 platform module and discover how much of it they would have lost. This enumeration is the single most transferable artifact in the module, because the FDE performs exactly this exercise in a client's environment in engagement week one.

**Terraform state is a recovery dependency.** Week 3 already teaches remote backends and locking. Add the consequence: lose the state and the platform module cannot reconcile, `import` becomes a multi-day archaeology exercise, and the "we can rebuild from code" story collapses. State needs versioning, backup and a documented recovery path like any other datastore.

**Backup of stateful workloads on Kubernetes.** Cluster state versus application state versus volume data as three separate problems with three separate tools. Control-plane state recovery; application-level backup for namespace and cross-cluster recovery; CSI volume snapshots and their critical limitation — a volume snapshot is usually crash-consistent, not application-consistent, so a database restored from one may come back needing recovery or not at all. Where the quiesce has to happen, and why "the snapshot succeeded" says nothing about whether the data is usable.

**The 3-2-1 family.** Three copies, two media, one off-site; the newer vendor formulations extend this to one immutable or offline copy and zero errors confirmed by restore testing. **Taught as a heuristic with its origin named honestly:** this is backup-vendor framing, not a standard from a standards body. The durable ideas inside it are blast-radius separation and verification-by-restore, and those are what the learner should carry; the digits are a mnemonic.

### 3.2 Keys, immutability and the adversary — Week 5, 0.5 hr

Slots directly into the existing data-protection block, alongside KMS with BYOK/HYOK and key rotation.

**The backup you cannot decrypt.** If the backup is encrypted with a KMS key held in the same account, under the same identity, with the same deletion authority as the workload, then account compromise or key deletion destroys the backup as effectively as deleting it — and more quietly, because the object is still sitting there looking fine. Key custody is a recovery control, and it is the one that BYOK and HYOK discussions with a client are actually about. **An FDE who can connect "where does the key live" to "can you recover" is having a different and better conversation than one who treats them as separate topics.**

**Immutability.** Object-lock and WORM retention as the control that makes a recovery point survive a credentialed attacker. The configuration trap worth teaching explicitly: on several platforms object lock must be enabled at bucket creation and cannot be retrofitted, so this is an architecture decision made once, early, under time pressure — exactly the kind of decision an FDE is asked to make in engagement week one and cannot revisit in week six.

**Retention versus deletion authority.** Who can shorten a retention period is a more important question than what the retention period is. Covered in the same breath as the audit-log integrity material in the log management module, because it is the same control reasoning applied to different data.

### 3.3 What is reproducible and what must be kept — Week 9, 0.5 hr

Briefing attached to Lab 17.1, and the point that makes this module fit the AI program rather than sit beside it.

Lab 17.1 already requires a **bit-reproducible training pipeline** — an assessor regenerates the exact artifact and metrics on a clean machine. That property is a recovery strategy, and naming it as one changes how learners think about both.

| State | Reproducible? | Therefore |
|---|---|---|
| Model weights | Yes, if the pipeline is bit-reproducible | Back up the **inputs and the pipeline**, not the artifact — but measure the regeneration time against RTO |
| Vector index | Yes, from the corpus | Rebuildable — but 5,000 documents takes hours, and that number *is* your RTO contribution |
| Feature store, online | Yes, from offline | Rebuild path must exist and be timed |
| Training corpus / client documents | **No** | Must be backed up. This is usually the client's only copy. |
| Labels and golden sets | **No** | Human-generated, expensive, irreplaceable. Routinely unbacked. |
| Experiment metadata and registry | **No** | Loses the provenance chain that the governance pack depends on |

**The judgment taught:** reproducibility converts a storage problem into a time problem, and that is only a win if the time fits inside the RTO. An engineer who says "we don't need to back up the index, we can rebuild it" has made a correct architectural statement and an incomplete operational one until they have timed the rebuild.

### 3.4 Recovery in the field — Week 11, 0.5 hr

**You are recovering someone else's system, with their tools, under their change process.** The FDE rarely owns the backup estate. The skills are: establishing what recovery capability actually exists as opposed to what the runbook claims, testing a restore without a non-production environment to test it in, and writing a recovery procedure that a client operator can execute at 3 a.m. without you.

**The air-gapped case.** No cross-region copy, no cloud-provider backup service, and the recovery media are physical. Pre-staging discipline, same as the Week 2 air-gap lab.

**The conversation, not the configuration.** How to tell a sponsor that the recovery capability they believe they have does not exist — which is a Week 11 communication skill, is assessed on the craft rubric, and is one of the more common unwelcome findings an FDE has to deliver.

---

## 4. The recovery failure taxonomy

Five categories. Taught and memorized like the RAG failure taxonomy in Week 7 and the log failure taxonomy. A learner facing a recovery problem names the category before touching anything.

| # | Category | What happened | Root cause class | Found at |
|---|---|---|---|---|
| **R1** | **No copy** | The thing that was lost was never backed up | Scope gap — the database was backed up, the object store was not | Design |
| **R2** | **Unrestorable copy** | The backup exists and will not restore | Missing key, version or engine mismatch, format drift, procedure never executed | First real restore |
| **R3** | **Unreachable copy** | The backup died with the thing it protected | Same account, region, credentials or deletion authority — blast radius not separated | During the incident |
| **R4** | **Too slow** | The restore works and misses the RTO | Never measured; transfer bandwidth, rebuild time or serial dependencies | During the incident |
| **R5** | **Inconsistent copy** | Each piece restores; the system does not | No application-consistent quiesce; components restored from different points; referential integrity broken | After the restore "succeeds" |

**R5 is the one that separates engineers.** R1 through R4 announce themselves. R5 produces a system that starts cleanly, passes health checks, serves traffic, and is subtly wrong — a database referencing objects that do not exist, an index pointing at deleted documents, a queue replaying work already done. It is the distributed-systems failure mode, it is the one that survives a naive restore test, and it is the reason application-consistent snapshots and a documented restore *order* exist.

**Why the ordering matters operationally.** R1 and R3 are design defects, fixable only before the incident. R2 and R5 are procedure defects, found only by rehearsal. R4 is a measurement defect. An engineer who names the category knows immediately whether this incident is survivable or whether they are now writing the postmortem — and that is the judgment the gate exists to find.

---

## 5. New labs

| Lab | Wk | Name | Domain | Hrs | Environment | Pass criteria |
|---|---|---|---|---|---|---|
| **5.3** | 3 | Make the platform module recoverable | D2 | 2 | Extends Lab 5.1 | Enumerate the full state surface. Add backup with stated RPO, point-in-time recovery for the database, immutable retention, a copy outside the blast radius, and a documented recovery order. **Prove it by restoring, not by configuring it.** |
| **17.3** | 9 | Restore what you did not back up | D2/D5 | 4 | `FAULT` — another pod's stack | Given another learner's system, its runbook and a stated RPO/RTO, recover after destructive loss. Report measured RPA and RTA against target, and name the taxonomy category of every obstacle hit. |
| **23.3** | 11 | The 3 a.m. recovery procedure | D6 | 2 | Cold execution, cross-pod | Another pod executes your recovery procedure with no author contact and no clarifying questions. Scored on their success, not on your document. |

**Lab 17.3 is the module.** Three design choices make it work and all three should survive review:

- **It is someone else's system.** Restoring your own system tests memory. Restoring a stranger's tests method, and tests whether *their* runbook was written for a reader — which is the same lesson the Week 10 design note already identifies as the one most learners discover too late.
- **Measured, not asserted.** RPA and RTA are stopwatch numbers reported against targets. This is the only place in the program where a learner produces recovery evidence rather than a recovery plan.
- **Obstacles are named by taxonomy.** Forces diagnosis to be categorical rather than narrative, and makes stall points comparable across learners — the same property the fault library README's enumerated stall points exist to provide.

---

## 6. New fault library scenarios

Appended to the library as extended by the log management module (33–40). Same design principles.

> **Adoption dependency.** These numbers assume the log management module is adopted first. If this module is adopted alone, renumber 41–47 as 33–39; the IDs (`DR-*`) are what the harness references, not the ordinals.

| # | ID | Lab | Fault | Taxonomy | Variants | Reset |
|---|---|---|---|---|---|---|
| 41 | `DR-SCOPE` | 17.3 | Database backed up, object store not; restore yields rows referencing blobs that no longer exist | R1 | 3 | 3 min |
| 42 | `DR-NOKEY` | 17.3 | Backup intact, KMS key deleted with the account | R2 | 3 | 2 min |
| 43 | `DR-VERSION` | 17.3 | Dump restores only into an engine version no longer available | R2 | 3 | 3 min |
| 44 | `DR-BLAST` | 5.3 | Only recovery point lives in the account being recovered, deletable by the same identity | R3 | 2 | 2 min |
| 45 | `DR-SLOW` | 17.3 | Restore succeeds at four times the stated RTO; bottleneck must be found and argued | R4 | 3 | 4 min |
| 46 | `DR-SKEW` | 17.3 | Database and object store restored from points 40 minutes apart; referential integrity silently broken | R5 | 4 | 4 min |
| 47 | `DR-STATE` | 5.3 | Terraform state lost; platform cannot reconcile and `import` is the only path | R2 | 3 | 5 min |

**`DR-SKEW` is the one to protect in review.** It is the hardest, the most realistic, and the only fault in the library that teaches R5. Learners will declare success — the system is up, health checks pass, queries return — and the assessor's job is to ask for one specific record and let them find the dangling reference themselves. Instructors should expect a 40%+ stall rate on first exposure and should **not** treat that as a curriculum defect under the 40% rule; it is the intended difficulty. Flag it in the fault README so the weekly retro does not try to fix it.

**`DR-NOKEY` pairs with Week 5.** Run it after the KMS block, not before, or the lesson lands as a trick rather than as a consequence of key custody.

---

## 7. Gate integration

| Gate | Change | Rationale |
|---|---|---|
| **G2** Day 30 | Two additions to the panel question bank: *"What is your RPO and RTO, and when did you last measure them?"* and *"Your backups are encrypted. Where is the key, and who can delete it?"* | No new artifact. These are questions a real regulated client's security team asks, and the bank already contains the LDAP question of exactly this shape. |
| **G4** Day 50 | A fourth `PROD-SIM` sequence variant in which one of the five injections is destructive data loss requiring a restore to a stated RPO | Adds a variant rather than displacing an injection. The existing five are all availability or quality incidents; none requires recovery. |
| **G5** Day 60 | Tenth deliverable: **recovery procedure with measured RTO/RPO.** Reject if the figures are targets rather than measurements, or if it fails the cold-execution test applied to deliverable 8 | Makes the handover pack honest. A handover that cannot be recovered from is not a handover. |

**On the G5 reject condition.** "Reject if the figures are targets rather than measurements" is the operative clause and it should be worded exactly that way. Every learner will produce a number; the gate is testing whether a stopwatch was involved.

---

## 8. Assessment additions

Added to existing scored dimensions. No new rubric.

| Gate | Dimension | 1 | 3 | 5 |
|---|---|---|---|---|
| G4 | Recovery execution | Could not recover; escalated | Recovered, exceeded RTO, could not say by how much | Recovered within RTO, reported measured RPA/RTA, named what would have made it faster |
| G5 | Recoverability evidence | Backup configured | Recovery procedure documented | Procedure executed cold by another party, with evidence and measured figures |

**The level-3 wording on G4 is deliberately specific.** "Recovered but could not say by how much" is the most common real-world outcome and it is a genuine middle score, not a failure. The step to 5 is measurement discipline, not technical skill, which is the point the dimension exists to make.

---

## 9. Build requirements for the lab engineer

| Item | Spec | Due |
|---|---|---|
| Backup target | Object storage with immutable retention and versioning, outside the learner sandbox account | T−5 weeks |
| Destruction harness | Scripted destructive loss for Lab 17.3 — reproducible, scoped, and incapable of touching another learner's sandbox | T−4 weeks |
| Cross-pod assignment | Harness extension assigning each learner another pod's stack for 17.3, with the owner's runbook and no author contact | T−4 weeks |
| Timing capture | `rpa_measured`, `rta_measured`, `rto_target`, `rpo_target` added to Lab Telemetry | T−4 weeks |
| Stale engine image | A database engine version no longer offered by the managed service, for `DR-VERSION` | T−3 weeks |
| Key deletion simulation | Revoke access to a KMS key without a 30-day waiting period blocking the reset | T−3 weeks |

**The destruction harness is the one with real risk.** It must be impossible for a learner to trigger destruction outside their own assigned sandbox, and the blast-radius guard needs testing before Cohort 1 rather than discovering its limits during one. Scope it by the `learner` tag the environment policy already enforces.

**Telemetry note.** `rta_measured` against `rto_target` is the most valuable new field here. Across a cohort it reveals whether the program is teaching recovery design or recovery theatre, and it is directly comparable between cohorts in a way qualitative assessor scores are not.

---

## 10. What this module deliberately does not cover

- **Full business continuity management.** Crisis communications, succession, facilities. That is a client's BCM function, not an FDE deliverable.
- **Multi-region active-active architecture.** That is an availability architecture decision, taught in Week 3 as a trade-off. Recovery is the subject here.
- **Backup product evaluation.** Categories taught, instances named — consistent with the program's standing position that clients mandate tools nobody has used.
- **Ransomware incident response.** Week 6 owns incident response and the PICERL framework. This module contributes only the recovery-point integrity half.
- **Formal DR plan authoring to a regulatory template.** Specialization territory, alongside the deeper DORA and NERC CIP work.

---

## 11. Residual gap after this module

Honest note for the gap register. This module makes graduates competent at **recovering a system they built or inherited**. It does not make them competent at **auditing a client's existing DR estate** — walking into a bank with forty years of accumulated recovery arrangements and producing a defensible assessment. That is a consulting skill with its own method, it is plausibly what a mature client actually asks an FDE to do first, and it belongs in the Advanced DevSecOps or Cloud Security specialization rather than the Core.

**Recommend logging it as a new finding (G-11, low) rather than widening this module.** The Core's job is to produce engineers who do not ship unrecoverable systems. It is worth stating that boundary explicitly so the omission is a decision rather than an oversight.

---

*FDE Academy — 12-Week Intensive · Backup, Restore & Disaster Recovery Module v1.0 · Proposed addendum, pending program lead review. Addresses gap register G-03. Document ends.*
