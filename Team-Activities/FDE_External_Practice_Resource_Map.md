# FDE Academy — 12-Week Intensive
## External Practice & CTF Resource Map (Proposed Addendum v1.0)

**For the program lead, instructors and mentors. Companion to the Student Roadmap & Handbook Part III §4 and the Instructor & Lab Operations Guide v2.0.**

| | |
|---|---|
| **Status** | Proposed addendum — not yet merged |
| **Purpose** | Give instructors and learners a mapped set of external hands-on platforms for conditioning and remediation |
| **Assessed** | **No.** Nothing on this list is ever scored, gated, or required |
| **Verification date** | 2026-11-26 — see §7 before relying on any figure |

---

## 1. The policy, before the list

The fault library is the assessment instrument and nothing on this list changes that. Design principle 4 is explicit: every fault in the library has occurred in a real customer engagement, and if it has not, it does not belong. Public CTF challenges are built to be interesting, not to be representative. They are excellent conditioning and they are not evidence of field capability.

**Three permitted uses, and one prohibition.**

| | Use | Who decides |
|---|---|---|
| ✅ | **Pre-program conditioning** — building shell and tooling fluency before Day 1 | Learner, optional |
| ✅ | **Targeted remediation** — assigned against a specific logged stall point | Instructor, in the Wednesday 1:1 |
| ✅ | **Warm-up** — 20 minutes before a hard lab, to get hands moving | Instructor |
| ❌ | **Assessment, gate content, or a substitute for a fault-library lab** | Nobody. This is a policy, not a judgment call. |

**Why the prohibition is absolute.** The certification's only value is that it predicts field performance, and that prediction rests on assessing against faults with real provenance. A gate that could be passed by someone who had seen the same public challenge is a gate that measures exposure rather than capability. This is the same reasoning that already forbids reusing a learning-lab environment at a gate.

**The remediation rule.** An external exercise is assigned against a *named stall point from the telemetry*, never as general homework. "You lost nineteen minutes on `/etc/resolv.conf` in Lab 1.1 — do these two scenarios before Thursday" is useful. "Do some SadServers this week" is the kind of unfocused evening work that the compressed model has no room for and that burns learners out by Week 6.

---

## 2. The pre-program question — and why SadServers is not the answer

The Prep Guide's central argument is that cramming hurts, because the Day 2 baseline routes a learner into a lane and sets the number their Day 60 growth is measured against. That argument applies to external practice platforms with more force than it applies to reading, and the distinction is sharp enough to be worth stating precisely.

| Platform | Pre-program? | Reasoning |
|---|---|---|
| **OverTheWire Bandit** | ✅ **Recommended** | Builds shell fluency — pipes, redirection, `find`, `grep`, SSH keys, file permissions. Fluency is not what the baseline measures, so it cannot inflate the lane assignment. It removes the friction that otherwise consumes Week 1. |
| **SadServers** | ❌ **Do not recommend** | It is a timed single-server Linux diagnosis exercise. The Day 2 practical (Lab 0.1) is a timed layered-fault diagnosis exercise scored on **method**. A learner who has done thirty SadServers scenarios arrives with a rehearsed method, scores above their true level, is routed into a lane that removes the support they need, and ends the program with an inflated baseline. This is precisely the failure the Prep Guide warns about. |

**This distinction is the most important line in this document.** SadServers is the single best external platform for this program and it must not be recommended before Day 2. Introduce it on Day 3, once the baseline is captured, and it becomes the strongest remediation tool available.

**Proposed Prep Guide change.** Add one bullet to Section 3 (Optional):

> - If you want hands on a keyboard before Day 1, work through OverTheWire Bandit (`overthewire.org/wargames/bandit/`). It is free, it takes a few evenings, and it builds the shell fluency you will use every day. **Do not seek out Linux troubleshooting challenge sites before the baseline** — the Day 2 practical measures your diagnostic method, and arriving with a rehearsed one gets you routed into the wrong lane.

Being explicit about *why* is what makes learners comply. "Do not prepare" reads as false modesty; "preparing in this specific way will get you placed wrong and cost you the support you need" is a reason people act on.

---

## 3. The map

Mapped to the six domains and the week where each is most useful. **Cost column is per learner.**

### D1 — Systems & Software Engineering

| Platform | What it actually builds | Cost | Best used | Honest limitation |
|---|---|---|---|---|
| **OverTheWire Bandit** | Shell fluency, file/permission handling, SSH key mechanics, encodings, basic networking via SSH-delivered levels | Free | **Pre-program** | Puzzle-flavored. Teaches commands, not diagnosis. Stop after the SSH-key levels; later levels drift into CTF trivia with low field transfer. |
| **SadServers** | Single-server Linux diagnosis under a clock — the closest public analogue to Lab 1.1 | Paid individual tier; business/white-label tier exists | **Week 1 remediation, Day 3 onward** | Single server, single fault, no distributed layer. Does not reach the `K8S-*` or multi-service classes. See §2 — never pre-program. |
| **Linux man pages + `tldr`** | The habit the Student Handbook already prescribes | Free | Throughout | Not a platform; listed because instructors forget to prescribe it. |

### D2 — Cloud & Platform

| Platform | What it actually builds | Cost | Best used | Honest limitation |
|---|---|---|---|---|
| **Killercoda** | Browser Kubernetes scenarios on throwaway VMs; CKA/CKAD-shaped paths | Free tier | **Week 3 remediation**, before Lab 6.1 | Scenarios are exam-shaped, not failure-shaped. Good for `kubectl` fluency, weak for the autopsy faults, which the library covers properly. |
| **iximiuz Labs** | Containers, networking and Kubernetes internals as guided playgrounds | Freemium | Week 2–3 remediation | Depth varies by scenario. |
| **Local `kind`/`k3d`** | A cluster to break on purpose, on the learner's own machine | Free | Throughout | No GPU, no cloud IAM. Already implied by the toolchain in the Prep Guide. |

### D3 — Secure Delivery

| Platform | What it actually builds | Cost | Best used | Honest limitation |
|---|---|---|---|---|
| **PortSwigger Web Security Academy** | Web vulnerability classes with working labs — the broadest free application-security training available | Free | **Week 5 remediation** | Application-layer focus. The program's D3 centre of gravity is supply chain and admission control, which this does not touch. |
| **OWASP Juice Shop** | A deliberately vulnerable application to attack and then to scan in a pipeline | Free, self-hosted | Week 5, as a scan target for Lab 9.1 | **Most valuable here as a target, not a CTF** — it gives the scanning suite something with real findings instead of a toy repo. |
| **Kubernetes Goat** | Intentionally vulnerable Kubernetes cluster with a guided workbook; runs on GKE/EKS/AKS/K3S | Free, self-hosted | **Week 5**, pairs directly with Lab 10.1 | Self-hosted — the lab engineer owns the teardown. Attacker-oriented; Lab 10.1 remains the remediation exercise. |
| **CloudGoat** | AWS attack-path scenarios, Python over Terraform | Free, self-hosted | Week 5 | Deploys real billable AWS resources into the learner sandbox. Must be inside the $500 cap and the tagging policy. |
| **flaws.cloud / flaws2.cloud** | AWS misconfiguration CTF, author-hosted; flaws2 has attacker and defender paths | Free | Week 5 warm-up | Older service coverage. Use the defender path — it is the one that matches the role. |

### D4 — Security Operations

| Platform | What it actually builds | Cost | Best used | Honest limitation |
|---|---|---|---|---|
| **ControlPlane Simulator** | Kubernetes security CTF scenarios; deploys a cluster into your own AWS account | Open source; hosted tier separate | Week 6, alongside Lab 11.4 | Requires AWS and real spend. Highest setup cost on this list — justified only if Week 6 stall telemetry says it is needed. |
| **Vendor SIEM free tiers** | Query-language fluency before Lab 11.1 | Free tiers vary | Week 6 warm-up | Each vendor's query language is specific; the program teaches the category. Use for fluency only. |
| **Public postmortem archives** | The Prep Guide already prescribes reading one | Free | Throughout | Reading, not practice. Listed for completeness. |

### D5 — AI/ML & MLOps

| Platform | What it actually builds | Cost | Best used | Honest limitation |
|---|---|---|---|---|
| **Lakera Gandalf** | Prompt injection by escalating difficulty levels — extract a secret passphrase against progressively harder defenses | Free | **Week 7–8 warm-up**, before Lab 11.5 | Single-turn extraction against a chatbot. The program's threat model is *indirect* injection through an ingested document (`AI-INJECT-INDIRECT`), which Gandalf does not cover. Excellent for intuition, not for the taxonomy. |
| **HackAPrompt dataset & writeups** | Catalogued real prompt-attack patterns at scale | Free | Week 8, Lab 19.2 preparation | A dataset and competition writeups, not an environment. Use it as a source of adversarial prompts for the red-team lab's 50-prompt set. |
| **OWASP LLM Top 10** | Already prescribed in the Student Handbook | Free | Week 7–8 | Reference, not practice. |

### D6 — FDE Craft

No external platform exists for this domain. Discovery calls, steering committees and handover packs are role-play exercises with human panels, and no public resource substitutes. **This is worth saying out loud to learners** — the domain that most differentiates the role is the one they cannot self-study, which is an argument for the Friday craft block rather than against it.

---

## 4. Instructor playbook — stall point to exercise

The lookup an instructor uses in a Wednesday 1:1. Assign one, name the stall point, set a deadline before the next lab in that domain.

| Logged stall point | Assign | Dose |
|---|---|---|
| Lost time in shell mechanics — quoting, pipes, `find`, permissions | Bandit, levels 0–15 | 2 evenings |
| Did not check `/etc/resolv.conf`, `/etc/hosts`, or proxy env vars | SadServers, 2 network scenarios | 1 evening |
| Fixated on the application layer; never bisected the stack | SadServers, 3 mixed scenarios, **narrating out loud** | 2 evenings |
| Slow `kubectl` navigation in Lab 6.1 | Killercoda CKA path | 1 evening |
| Could not read a scan finding and decide if it was reachable | PortSwigger, the relevant vulnerability class | 1 evening |
| Hardened the symptom, not the class, in Lab 10.1 | Kubernetes Goat, 2 scenarios | 1 evening |
| Injection defenses were superstition rather than layered design | Gandalf to level 5, then re-read the OWASP LLM Top 10 | 1 evening |

**Cap at one assignment per learner per week.** The cohort contract already assumes full-time attention; evening remediation that exceeds two hours a week is a sign the learner needs lab scope reduced, which is the documented Week-4 intervention — not more homework.

---

## 5. Constraints instructors must know

**Air-gapped lab.** Nothing on this list works inside it. Every platform here needs egress, and the air-gapped lab has none by design. Remediation assigned during Week 2 or Week 11 must be done outside the air-gapped environment.

**Cost.** CloudGoat, Kubernetes Goat and Simulator deploy real cloud resources into the learner's sandbox. They are subject to the $500/month cap, the `cohort`/`learner`/`lab_id` tagging policy and the nightly reaper. The lab engineer adds a `lab_id` of `EXT-<platform>` so external practice spend is separable in the cost report.

**Content drift.** These are third-party services. Scenarios change, pricing changes, projects are archived. **No lab, gate or pass criterion may depend on any of them** — which is already guaranteed by the policy in §1, and is restated here because it is the practical reason that policy exists.

**Terms of use.** Using a third-party platform as part of a commercial training program is a different licence question from an individual practising on it. Before any paid platform appears in learner-facing material, the business tier and its terms need checking — several of these offer explicit organization or white-label tiers precisely because the free terms do not cover commercial training use. **This is a commercial review item, not an engineering one.**

**Attribution.** Where an external exercise informs a fault-library scenario, the scenario's README must say so in the Real-world provenance section. A fault inspired by a public CTF has different provenance from one drawn from an engagement, and principle 4 means that distinction has to be recorded honestly rather than quietly blurred.

---

## 6. Proposed change to the Student Handbook

Part III §4 currently lists reading only. Add one column and one note.

| Domain | Where to go | Hands-on |
|---|---|---|
| **D1 Systems** | *(unchanged)* | Bandit before Day 1; SadServers from Day 3 |
| **D2 Kubernetes** | *(unchanged)* | Killercoda; a local `kind` cluster you break on purpose |
| **D3 Security** | *(unchanged)* | PortSwigger Web Security Academy; Kubernetes Goat |
| **D4 Security Ops** | *(unchanged)* | A SIEM free tier, for query fluency only |
| **D4 LLM/RAG** | *(unchanged)* | Gandalf, to build injection intuition before Week 7 |
| **D6 Craft** | *(unchanged)* | **Nothing. This domain cannot be self-studied — which is why Friday exists.** |

> **A note on external practice.** None of this is assessed and none of it is required. It is here for the evening when you are stuck on one specific thing. Practising the thing you already do well is how people feel productive without improving; the value is in going straight at the stall point your instructor named.

---

## 7. Verification status

Checked against public sources on **2026-11-26**. Marked honestly, because several of these change often and a stale figure in learner-facing material is worse than no figure.

| Item | Status |
|---|---|
| SadServers paid individual tier, 100+ scenarios, business/white-label tier exists | Confirmed; exact price moves — **do not print a price in learner material** |
| Bandit is free, SSH-delivered, level-to-level password progression | Confirmed; published sources disagree on total level count (33 vs 34) |
| Killercoda free tier, CKA/CKAD paths, throwaway VMs, not an exam simulator | Confirmed |
| Kubernetes Goat self-hosted on GKE/EKS/AKS/K3S with guided workbook | Confirmed |
| CloudGoat AWS, Python over Terraform, self-hosted | Confirmed |
| flaws.cloud / flaws2.cloud author-hosted, attacker and defender paths | Confirmed |
| ControlPlane Simulator deploys into your own AWS account; hosted tier separate | Confirmed |
| Lakera Gandalf free, level-based passphrase extraction | Confirmed |
| PortSwigger Web Security Academy free | Reported by a secondary source — **confirm on portswigger.net before publishing** |
| OWASP Juice Shop free and self-hosted | **Not confirmed in this review** — long-standing OWASP flagship project, but verify before publishing |
| HackAPrompt dataset availability and licence | **Not confirmed** — licence matters if prompts are reused in Lab 19.2; check before use |
| iximiuz Labs freemium model | **Not confirmed** |

**Re-verify at T−4 weeks each cohort,** in the same pass as the OTel specification status check in the Error & Log Management Module. Budget 30 minutes for both.

---

*FDE Academy — 12-Week Intensive · External Practice & CTF Resource Map v1.0 · Proposed addendum, pending program lead and commercial review. Document ends.*
