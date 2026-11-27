# FDE Academy — 12-Week Intensive
## Error & Log Management Module (Proposed Addendum v1.0)

**For the program lead, both lead instructors and the lab engineer. Companion to the Program Handbook v2.0 and the Instructor & Lab Operations Guide v2.0.**

| | |
|---|---|
| **Status** | Proposed addendum — not yet merged into the Core |
| **Net new instruction** | 3.5 hrs, absorbed into existing blocks — no new week |
| **Net new lab hours** | 13 hrs across Weeks 1, 4, 6 and 11 |
| **New fault scenarios** | 8 (`LOG-*`), taking the library from 32 to 40 |
| **Gates touched** | G1 (one new pass criterion), G2 (one new artifact), G4 (one new injection class) |

---

## 1. Why this module exists

The current program treats logs as one third of the observability pillar in Week 4 and as a line item in Lab 2.1 ("structured JSON logs with correlation IDs"). That is correct as far as it goes, and it is not far enough for this role. Three reasons, each specific to forward deployment rather than to SRE generally.

**1. Logs are the only telemetry you are given on day one.** Metrics and traces require a code change, an agent rollout and a security review — in a regulated client that is a four-to-six-week path. Logs already exist, in every environment, before the FDE arrives. An engineer who can only diagnose from a Grafana dashboard they instrumented themselves is unproductive for the first month of an engagement. The program currently trains the instrumented case thoroughly and the inherited case not at all.

**2. Logs are the compliance evidence.** The G2 panel question bank already contains *"Show me the log that would prove this control was working last Tuesday."* Nothing in the twelve weeks teaches a learner to build the system that answers it. The question is asked and the capability is not taught.

**3. Logs are where the data-residency commitment is won or lost.** The published position for Healthcare is that zero PHI leaves the client environment. Week 4 teaches Datadog. In the field those two facts collide the first time someone points an agent at a namespace holding clinical data, and the resolution — what may egress, what must stay, what a redacting collector can and cannot guarantee — is a design conversation the FDE leads. It is not currently taught.

**Provenance.** Consistent with fault library design principle 4, every scenario proposed below is drawn from a failure class that recurs in regulated client estates. None is invented for the lab.

---

## 2. Where it slots in — no new weeks

Compression is the constraint the whole program is built around, so this module adds no week and moves no gate. It takes 3.5 hours from existing instruction blocks and 13 hours of lab time that is already allocated to the weeks named.

| Week | Block | Added | Displaces |
|---|---|---|---|
| **1** | Instruction — production Python | 1.5 hrs | Trim API versioning depth; it recurs in Week 11 handover |
| **1** | Lab 2.3 (new) | 2 hrs | Net new — Week 1 has the most lab slack |
| **4** | Instruction — observability | 1.0 hr | Trim the profiling survey; Pyroscope stays a named tool, not a taught one |
| **4** | Lab 8.3 (new) | 4 hrs | Net new |
| **6** | Instruction — compliance evidence | 0.5 hr | Absorbed into Lab 11.3 briefing |
| **6** | Lab 11.6 (new) | 3 hrs | Net new |
| **10** | Simulation injections | 0 hrs | Two `LOG-*` injections replace two existing `PROD-SIM` injections |
| **11** | Instruction — field troubleshooting | 0.5 hr | Absorbed into the Lab 22.3 briefing |
| **11** | Lab 22.3 (new) | 4 hrs | Net new |

**If the 13 lab hours cannot be found,** cut Lab 22.3 first and Lab 11.6 second. Do not cut Lab 8.3 — it is the one that carries the pipeline competency, and without it this module is a style guide rather than an engineering discipline.

---

## 3. Instruction content

### 3.1 Log discipline at the source — Week 1, 1.5 hrs

**Levels, and the error that is not one.** What `DEBUG`, `INFO`, `WARN`, `ERROR` and `FATAL` are each for, and the single most common defect in enterprise code: `ERROR` used for handled conditions. A log line that says `ERROR` for a retried timeout trains every operator who reads it to ignore `ERROR`, and by the time a real one appears the channel is dead. The rule taught: a level is a promise about who must act, not a description of how the developer felt.

**Event, not sentence.** A stable message string with the variable data in structured fields, never interpolated into the message. `user_id=4821 not found` produces one distinct message per user and is ungroupable; `{"msg":"user not found","user_id":4821}` produces one message and a field. This is the difference between a log store that can be aggregated and one that can only be grepped, and it is decided at the call site by the engineer, not later by the platform team.

**Correlation.** Trace ID and span ID on every record, propagated across process boundaries; the W3C `traceparent` header; what to do when the client's existing framework emits an unrelated request ID and both must be carried. Correlation is what makes a log pivot to a trace, and a log store with no correlation ID is a search engine rather than a diagnostic tool.

**What must never be logged.** Credentials, tokens, full payloads, authorization headers, PII, PHI, cardholder data. Taught as an allowlist discipline — serialize named fields, never whole objects — because a denylist regex in the pipeline fails the moment someone adds a field, and that failure is silent and retroactive.

**OpenTelemetry, accurately.** The logs data model and the Logs Bridge API are stable in the specification, and the Bridge API is deliberately not the interface application developers call — it exists for appenders that bridge an existing logging framework into OTel. Per-language SDK maturity varies considerably and changes between cohorts; the lab engineer verifies the current status table at `opentelemetry.io/docs/specs/status/` at T−2 weeks and briefs the instructor. The field rule taught is the same whatever the table says: **bridge the client's existing logging framework, do not rewrite their logging.** A rewrite is a six-week negotiation; a bridge is an afternoon.

### 3.2 The log pipeline — Week 4, 1.0 hr

**Architecture.** Application → collector (node agent or sidecar) → processor → sink, and why the collector is where volume policy belongs: it is the one place that can be changed without a redeploy, and in a client environment a redeploy needs a change window.

**Backpressure, and the day logging took production down.** What happens when the sink is unreachable. Blocking writes that stall request threads; unbounded in-memory buffers that OOM the pod; disk buffers that fill the node and trigger `DiskPressure` eviction — which is already fault `K8S-DISKPRESSURE` in the library, now taught with its most common real cause rather than as an abstract disk fault. The rule: logging must degrade by dropping, never by blocking, and the drop must itself be counted and exported as a metric.

**Volume and cost.** Log bytes per request as a unit-economics figure alongside the `$/1k requests` already taught in FinOps. Where the money actually goes — ingest, not storage, in most commercial pricing. Sampling that keeps all errors and samples successes. Converting high-volume logs to metrics at the collector and dropping the record, which is the single highest-leverage cost reduction available and the one clients most often have not done.

**Retention and tiering.** Hot, warm and cold tiers against query latency and cost; the distinction between the retention the business wants, the retention the regulator requires as a floor, and the retention the law requires as a ceiling under data-minimization rules. Three different numbers that are routinely conflated into one.

**Residency.** Which sinks are legal for which data classes. What a redacting processor guarantees and what it cannot: it cannot guarantee a field added next sprint is redacted, so the architecture must fail closed on unknown fields when the data class demands it. This is the Healthcare conversation from §1.3, taught explicitly.

### 3.3 Audit logs and evidence — Week 6, 0.5 hr

**An audit log is not an application log** and must not share its pipeline. Different retention, different access control, different integrity requirement, different deletion authority.

| Property | Application log | Audit log |
|---|---|---|
| Purpose | Diagnosis | Proof |
| Mutable | Effectively yes | Must be append-only |
| Who may delete | Platform team | Nobody, until retention expires |
| Integrity | Not required | Signed, timestamped, hash-chained |
| Retention driver | Cost | Regulation |
| Completeness | Best effort | Gap must be detectable |

**Gap detection** is the property engineers miss. An audit log that can lose records silently proves nothing, because an auditor cannot distinguish "the control was not exercised" from "the record was lost". Sequence numbering and hash chaining make a gap visible, and that visibility is the whole point. This connects directly to the immutable evidence store already built in Lab 11.3.

### 3.4 Logs under field constraints — Week 11, threaded

**No access.** The constraint is already named in the Week 11 instruction ("no direct log access... customer-mediated access"). What to do about it is not. Taught here: the diagnostic bundle as a first-class deliverable — what to collect, how to bound its size, how to redact it before it crosses an organizational boundary, and how to write the one-page instruction that lets a client operator who has never met you run the collection correctly on the first attempt.

**Air-gapped.** No SaaS sink, no egress, local retention with a hard disk budget, and the export path for getting a redacted bundle out through whatever review process the client operates.

---

## 4. The log failure taxonomy

Five categories. Taught the same way as the RAG failure taxonomy in Week 7, and memorized to the same standard — the point is that a learner facing a log problem names the category before touching anything.

| # | Category | Symptom | Root cause class | Fixed at |
|---|---|---|---|---|
| **L1** | **Ungroupable** | Millions of distinct messages; aggregation useless | Variable data interpolated into the message string | Source |
| **L2** | **Uncorrelatable** | Records exist but cannot be joined across services | No trace/span ID, or ID dropped at a boundary | Source + propagation |
| **L3** | **Unsearchable** | Records arrive but queries time out or miss | Unparsed text, wrong index, no schema, field explosion | Pipeline |
| **L4** | **Untrustworthy** | Records are missing, late, or duplicated | Backpressure drop, buffer loss, clock skew, at-least-once delivery | Pipeline |
| **L5** | **Unlawful** | Records contain data that may not be where it is | Over-serialization at source, denylist redaction, wrong sink | Source + architecture |

**Why the taxonomy is ordered this way.** L1 and L2 can only be fixed in the client's code, which means a change request, which means weeks. L3 and L4 can be fixed in the pipeline, which the FDE usually controls, which means days. L5 is an architecture decision that must be made before any data flows at all. An engineer who correctly identifies the category knows immediately whose calendar the fix lives on — and that, not the fix itself, is the judgment the field rewards.

---

## 5. New labs

| Lab | Wk | Name | Domain | Hrs | Environment | Pass criteria |
|---|---|---|---|---|---|---|
| **2.3** | 1 | Make a hostile log readable | D1 | 2 | Local — `FAULT` | Given a service emitting L1 and L2 defects, refactor to stable messages with structured fields and propagated correlation IDs. Aggregation query that was impossible before now returns in under 2s. |
| **8.3** | 4 | Build the log pipeline | D2 | 4 | Collector + store + app | Collector-based pipeline with sampling, log-to-metric conversion, allowlist redaction and bounded buffering. **Sink is killed during assessment: the app must not block, must not OOM, and the drop count must be exported as a metric.** |
| **11.6** | 6 | The audit log that survives a challenge | D3/D4 | 3 | Evidence store + CI | Append-only, hash-chained, signed audit trail for 5 controls. Assessor deletes a record out of band; the learner's gap detection must surface it. Learner answers the G2 question "prove this control was working last Tuesday" from the store alone. |
| **22.3** | 11 | The bundle you cannot collect yourself | D6 | 4 | No access — operator proxy | Diagnose a fault with no log access. Produce a collection instruction a non-expert operator executes correctly first time, bound the bundle under a stated size cap, redact it to a named data class, and reach root cause. |

**Lab 8.3 is the one that matters.** Killing the sink mid-assessment is the entire exercise. Every learner builds a pipeline that works; the separation between a learner who has understood logging and one who has configured it appears only when the sink goes away. It is also the single most common production incident caused by observability tooling, which makes it the lab with the strongest field provenance in this module.

---

## 6. New fault library scenarios

Appended to the 32-scenario library. Same design principles: defined as code, one fault per learning scenario, randomized variants, reset under 5 minutes.

| # | ID | Lab | Fault | Taxonomy | Variants | Reset |
|---|---|---|---|---|---|---|
| 33 | `LOG-INTERP` | 2.3 | Variable data interpolated into message strings; cardinality explosion on ingest | L1 | 3 | 1 min |
| 34 | `LOG-NOCORR` | 2.3 | Correlation ID dropped at one service boundary out of four | L2 | 4 | 1 min |
| 35 | `LOG-UNPARSED` | 8.3 | Multiline stack traces split into one record per line | L3 | 3 | 2 min |
| 36 | `LOG-BLOCKING` | 8.3 | Unreachable sink; synchronous appender stalls request threads | L4 | 3 | 2 min |
| 37 | `LOG-DISKFULL` | 8.3 | Unbounded disk buffer fills the node, evicting pods | L4 | 3 | 4 min |
| 38 | `LOG-SKEW` | 8.3 | Clock skew on one node; events appear out of order and a timeline cannot be built | L4 | 3 | 2 min |
| 39 | `LOG-PII` | 11.6 | Whole-object serialization leaks PII past a denylist redactor after a new field is added | L5 | 4 | 2 min |
| 40 | `LOG-GAP` | 11.6 | Audit records silently lost in a retry window; no sequence numbering to reveal it | L4 | 3 | 3 min |

**`LOG-SKEW` is the sleeper.** It is the fault learners find hardest because every record looks individually correct and only the ordering is wrong. It is also common in client estates where one node missed an NTP configuration, and it defeats any engineer whose diagnostic method depends on reading a timeline rather than reasoning about causality.

**Reuse at gates.** `LOG-BLOCKING` and `LOG-GAP` layer well with existing faults at G4. `LOG-PII` is the natural layered partner for the G2 security review.

---

## 7. Gate integration

| Gate | Change | Rationale |
|---|---|---|
| **G1** Day 20 | Add pass criterion: *structured, correlated and aggregatable logs — the assessor reconstructs one request end to end across services using the correlation ID alone* | The existing failure-mode note already says "logs that are unstructured and therefore unsearchable" is a common failure, but no criterion tests it. This closes that. |
| **G2** Day 30 | Add to the required artifact list: *log and audit design — data classes, sinks, retention per class, redaction method, and the residency argument* | Makes artifact count 8. It is the artifact a real enterprise security questionnaire asks for and the current set omits. |
| **G4** Day 50 | Two of five injections drawn from `LOG-*` | Operating under failure when your telemetry is itself degraded is the realistic case, and currently the simulation assumes working observability throughout. |

**G1 criterion wording matters.** It must be stated as a reconstruction the *assessor* performs, not as a property the learner asserts. "Logs are structured" is unfalsifiable in the room; "the assessor followed one request across four services in under two minutes" is not.

---

## 8. Assessment additions

Added to the existing scored dimensions rather than creating a new rubric.

| Gate | Dimension | 1 | 3 | 5 |
|---|---|---|---|---|
| G1 | Diagnosability | Logs exist | Structured and correlated | A stranger diagnoses a fault from logs alone, unaided |
| G2 | Evidence integrity | Logs retained | Retention per data class justified | Tamper-evident, gap-detecting, defensible to a hostile auditor |
| G4 | Degraded-telemetry operation | Blocked when telemetry degraded | Worked around it | Detected the telemetry failure itself as an incident and handled it as one |

**The G4 dimension is the discriminating one.** When logs stop arriving, the majority response is to keep debugging the application. The engineer who recognizes within minutes that the *observability system* is the incident, says so, and switches diagnostic strategy is demonstrating the judgment this gate exists to find.

---

## 9. Build requirements for the lab engineer

| Item | Spec | Due |
|---|---|---|
| Log stack | Collector + store + query UI, same stack as Week 4 observability. One stack, not two. | T−5 weeks |
| Sink-kill harness | Scripted sink failure for Lab 8.3, triggerable mid-assessment, reversible in under 60s | T−4 weeks |
| Evidence store | Append-only with hash chaining; an out-of-band deletion tool for the assessor | T−4 weeks |
| Hostile log corpus | ~2M records carrying L1–L4 defects, generated not hand-written, so it regenerates per cohort | T−4 weeks |
| Redaction test set | Synthetic PII/PHI records that a denylist passes and an allowlist catches | T−3 weeks |
| OTel status check | Re-read the specification status page; brief instructors on current per-language maturity | T−2 weeks, every cohort |

**Nothing here needs new infrastructure.** Every component runs on the existing per-learner sandbox and the Week 4 observability stack. The recurring cost is the storage for the hostile corpus, which is trivial at this volume, and the recurring effort is the T−2 status check, which is 30 minutes.

---

## 10. What this module deliberately does not cover

Stated so that reviewers do not read the omissions as oversights.

- **SIEM engineering.** Already Week 6, Lab 11.1. This module stops at the point where logs are handed to a SIEM.
- **Profiling.** Stays a named tool. Compression does not permit it as a taught discipline, and it is the lowest-value pillar for field work.
- **Vendor-specific query languages.** Categories are taught, instances are named. Consistent with the program's stated position that a client will mandate a tool nobody has used.
- **Log-based anomaly detection with ML.** Belongs to the Advanced DevSecOps specialization, not the Core.

---

*FDE Academy — 12-Week Intensive · Error & Log Management Module v1.0 · Proposed addendum, pending program lead review. Document ends.*
