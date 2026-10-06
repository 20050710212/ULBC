# S4aA260111 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260111_[ULBC-MED] On decision sequencing of the project.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG (AH) Meeting    S4aA260111

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P004"></a>

Source:    Huawei Technologies Co., Ltd.

<a id="P005"></a>

Title:    [ULBC-MED] On decision sequencing of the project

<a id="P006"></a>

Agenda item:    4.2

<a id="P007"></a>

Document for:    Discussion and Agreement

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

The schedule for finalizing the Rel-20 ULBC-MED Pdoc is extremely tight, comprising only four meetings: the Shanghai ad-hoc meeting, two telco meetings in October, and SA4#138. In such a schedule, an out-of-order decision is not merely inefficient: If the key root node cannot be finalized, it will result in downstream tasks always being TBD, and consequently, the project will not be able to move forward. SA4#137-e already demonstrated both outcomes: the bit-rate decision was converged in one session, while ULBC-3 could only be agreed as a fully bracketed skeleton precisely because its upstream dependencies (bandwidth, complexity) were still open. [1][3]

<a id="P011"></a>

This contribution maps the decision dependencies across the ULBC permanent documents and within ULBC-4 itself, and derives a guided decision order together with a meeting-by-meeting schedule.

<a id="P012"></a>

## 2    Pdoc-level dependencies

<a id="P013"></a>

Table 1 captures the dependency relations as they stand after SA4#137-e. The chain reads: ULBC-4 (design constraints) feeds ULBC-3 (performance requirements); ULBC-3 feeds ULBC-5a/5b (rules) and ULBC-8a/8b (test plans); ULBC-7 (processing) adapts once ULBC-3 reference codecs and ULBC-4 methodologies are fixed; ULBC-6 (deliverables) de-brackets after the qualification decision; ULBC-9's payload-format part follows frame length and SID sizes while its system-integration part runs in parallel.

<a id="P014"></a>

Table 1: Pdoc dependency matrix

<a id="T015"></a>

<a id="T015-R01"></a>
**T015-R01**

- <a id="T015-R01-C01"></a>列 1: Pdoc
- <a id="T015-R01-C02"></a>列 2: Depends on (upstream)
- <a id="T015-R01-C03"></a>列 3: Blocks (downstream)
- <a id="T015-R01-C04"></a>列 4: Status after SA4#137-e

<a id="T015-R02"></a>
**T015-R02**

- <a id="T015-R02-C01"></a>列 1: ULBC-4<br>Design Constraints
- <a id="T015-R02-C02"></a>列 2: None (root)
- <a id="T015-R02-C03"></a>列 3: ULBC-3 (bandwidth, AFR, test conditions); ULBC-5a (Rule 1 compliance scope); ULBC-9 (header design); ULBC-7 (gain measurement)
- <a id="T015-R02-C04"></a>列 4: Bit rates 1.0/1.4 kbps (gross) and bundling 80/160 ms agreed; the rest bracketed [2]

<a id="T015-R03"></a>
**T015-R03**

- <a id="T015-R03-C01"></a>列 1: ULBC-3<br>Performance Requirements
- <a id="T015-R03-C02"></a>列 2: ULBC-4 (bandwidth, complexity)
- <a id="T015-R03-C03"></a>列 3: ULBC-5a/5b (FoM weights); ULBC-8a/8b (experiments instantiate the requirement conditions); ULBC-7 (reference-codec processing)
- <a id="T015-R03-C04"></a>列 4: v0.1.0 framework agreed; all values bracketed; editor's note: WB/SWB split open [3]

<a id="T015-R04"></a>
**T015-R04**

- <a id="T015-R04-C01"></a>列 1: Qualification-phase decision<br>(in ULBC-2)
- <a id="T015-R04-C02"></a>列 2: None (root)
- <a id="T015-R04-C03"></a>列 3: Creation/finalization of ULBC-5a and ULBC-8a; de-bracketing of ULBC-6
- <a id="T015-R04-C04"></a>列 4: Bracketed; final decision at SA4#138 [10],

<a id="T015-R05"></a>
**T015-R05**

- <a id="T015-R05-C01"></a>列 1: ULBC-5a / 5b<br>Rules
- <a id="T015-R05-C02"></a>列 2: ULBC-3 (test sets, FoM over requirements); ULBC-4 (Rule 1 compliance items); ULBC-5a additionally gated by the qualification decision
- <a id="T015-R05-C03"></a>列 3: Qualification/selection execution
- <a id="T015-R05-C04"></a>列 4: Not created.

<a id="T015-R06"></a>
**T015-R06**

- <a id="T015-R06-C01"></a>列 1: ULBC-8a / 8b<br>Test Plans
- <a id="T015-R06-C02"></a>列 2: ULBC-3 (conditions), ULBC-7 (processing functions); ULBC-8a additionally gated by the qualification decision
- <a id="T015-R06-C03"></a>列 3: Test execution; objective-evaluation scope in ULBC-6
- <a id="T015-R06-C04"></a>列 4: Not created.

<a id="T015-R07"></a>
**T015-R07**

- <a id="T015-R07-C01"></a>列 1: ULBC-7<br>Processing Plan
- <a id="T015-R07-C02"></a>列 2: ULBC-3 (reference codecs and their command lines); ULBC-4 (gain measurement)
- <a id="T015-R07-C03"></a>列 3: Condition processing for 8a/8b; objective-evaluation scripts
- <a id="T015-R07-C04"></a>列 4: v0.1.0 agreed; bracketed EVS copy awaiting adaptation [6]

<a id="T015-R08"></a>
**T015-R08**

- <a id="T015-R08-C01"></a>列 1: ULBC-6<br>Deliverables
- <a id="T015-R08-C02"></a>列 2: ULBC-5/8 (objective-evaluation scope); qualification decision
- <a id="T015-R08-C03"></a>列 3: Candidate submission readiness
- <a id="T015-R08-C04"></a>列 4: v0.2.0 agreed; qualification stage bracketed [5]

<a id="T015-R09"></a>
**T015-R09**

- <a id="T015-R09-C01"></a>列 1: ULBC-9<br>RTP / System Integration
- <a id="T015-R09-C02"></a>列 2: ULBC-4 (DTX/CNG design).
- <a id="T015-R09-C03"></a>列 3: RTP payload format TS drafting
- <a id="T015-R09-C04"></a>列 4: v0.0.1 agreed; parallel track [7]

<a id="P016"></a>

## 3    Decision order within ULBC-4

<a id="P017"></a>

ULBC-4 is the root of the dependency tree, and its own rows are interdependent. The internal order proposed in Table 2 rests on one central coupling: for AI-based codecs, moving from 16 kHz/WB to 32 kHz may potentially increase the model complexity, so the bandwidth decision should be taken inside a known complexity envelope, not before it.

<a id="P018"></a>

Table 2: Guided decision order within ULBC-4

<a id="T019"></a>

<a id="T019-R01"></a>
**T019-R01**

- <a id="T019-R01-C01"></a>列 1: Step
- <a id="T019-R01-C02"></a>列 2: Decision
- <a id="T019-R01-C03"></a>列 3: Depends on (within ULBC-4)
- <a id="T019-R01-C04"></a>列 4: Rationale

<a id="T019-R02"></a>
**T019-R02**

- <a id="T019-R02-C01"></a>列 1: 0
- <a id="T019-R02-C02"></a>列 2: Bit rates 1.0/1.4 kbps (gross), bundling 80/160 ms, mono, ≥WB
- <a id="T019-R02-C03"></a>列 3: -
- <a id="T019-R02-C04"></a>列 4: Agreed at SA4#137-e. [2]

<a id="T019-R03"></a>
**T019-R03**

- <a id="T019-R03-C01"></a>列 1: 1
- <a id="T019-R03-C02"></a>列 2: Complexity metric definition
- <a id="T019-R03-C03"></a>列 3: (root)
- <a id="T019-R03-C04"></a>列 4: "Definition before numbers" (S4-261627 [8], agreed as an editor's note; S4-261640 [9]). GMACs vs FLOPs vs implementation accounting must be settled before any numeric limit can be meaningful.

<a id="T019-R04"></a>
**T019-R04**

- <a id="T019-R04-C01"></a>列 1: 2
- <a id="T019-R04-C02"></a>列 2: Complexity numeric limits (the envelope)
- <a id="T019-R04-C03"></a>列 3: Step 1
- <a id="T019-R04-C04"></a>列 4: Worst-case per-second complexity, parameter/memory budget, combined budget for both operating points – well-defined only after metric is known

<a id="T019-R05"></a>
**T019-R05**

- <a id="T019-R05-C01"></a>列 1: 3
- <a id="T019-R05-C02"></a>列 2: Sampling rate / bandwidth (16 vs 32 kHz)
- <a id="T019-R05-C03"></a>列 3: Step 2
- <a id="T019-R05-C04"></a>列 4: Decided after complexity, at which point it becomes a quantified quality-vs-cost trade-off; it unblocks the ULBC-3 table structure (WB-only vs WB+SWB)

<a id="T019-R06"></a>
**T019-R06**

- <a id="T019-R06-C01"></a>列 1: 4
- <a id="T019-R06-C02"></a>列 2: Algorithmic delay (frame + x ms)
- <a id="T019-R06-C03"></a>列 3: Low coupling
- <a id="T019-R06-C04"></a>列 4: Expressed as frame length plus look-ahead. [2]

<a id="T019-R07"></a>
**T019-R07**

- <a id="T019-R07-C01"></a>列 1: 5
- <a id="T019-R07-C02"></a>列 2: SID / DTX frame budget
- <a id="T019-R07-C03"></a>列 3: Low coupling
- <a id="T019-R07-C04"></a>列 4: Frequency-first constraint (companion contribution); sizes within the per-operating-point payload budget.

<a id="T019-R08"></a>
**T019-R08**

- <a id="T019-R08-C01"></a>列 1: 6
- <a id="T019-R08-C02"></a>列 2: JBM keep/drop + delay budget
- <a id="T019-R08-C03"></a>列 3: Low coupling
- <a id="T019-R08-C04"></a>列 4: Scoping per companion contribution; the JBM delay question raised at SA4#137-e presupposes the delay budget.

<a id="T019-R09"></a>
**T019-R09**

- <a id="T019-R09-C01"></a>列 1: 7
- <a id="T019-R09-C02"></a>列 2: Output gain / noise suppression
- <a id="T019-R09-C03"></a>列 3: Low coupling
- <a id="T019-R09-C04"></a>列 4: Measurement methodology lands in ULBC-7 (companion contribution) [6]; can trail without blocking others.

<a id="P020"></a>

A note on the Shanghai agenda: the sampling rate/bandwidth debate is the headline topic of the F2F meeting. Per the order above, the complexity items (Steps 1–2) should be decided before the bandwidth decision is taken, ideally earlier in the same meeting, so that the 16 vs 32 kHz debate is conducted with the complexity envelope on the table.

<a id="P021"></a>

## 4    Guided decision schedules

<a id="P022"></a>

Mapping the dependency order onto the available sessions yields the schedule of Table 3. The design intent is that everything upstream closes as early as possible, so that each subsequent session spends its time on decisions that are actually unblocked.

<a id="P023"></a>

Table 3: Decision schedule mapped to the remaining sessions

<a id="T024"></a>

<a id="T024-R01"></a>
**T024-R01**

- <a id="T024-R01-C01"></a>列 1: Session
- <a id="T024-R01-C02"></a>列 2: Decisions to close
- <a id="T024-R01-C03"></a>列 3: Why in this session

<a id="T024-R02"></a>
**T024-R02**

- <a id="T024-R02-C01"></a>列 1: Shanghai AH<br>28–30 Sep 2026
- <a id="T024-R02-C02"></a>列 2: Stage 1 (ULBC-4 core): complexity metric; complexity limits; sampling rate/bandwidth. If possible, an early qualification-phase decision per the companion framework [10]
- <a id="T024-R02-C03"></a>列 3: The headline Shanghai topic (bandwidth) becomes fully decidable once the complexity is known; closing Stage 1 here unblocks ULBC-3 population for the whole October window

<a id="T024-R03"></a>
**T024-R03**

- <a id="T024-R03-C01"></a>列 1: Telco #1<br>14 Oct 2026
- <a id="T024-R03-C02"></a>列 2: Stage 2a (ULBC-4 tail + ULBC-3 start): algorithmic delay; SID/DTX budget; JBM; begin filling in the specific values for ULBC-3.
- <a id="T024-R03-C03"></a>列 3: ULBC-3 unblocked once bandwidth is settled at Shanghai

<a id="T024-R04"></a>
**T024-R04**

- <a id="T024-R04-C01"></a>列 1: Telco #2<br>28 Oct 2026
- <a id="T024-R04-C02"></a>列 2: Stage 2b (downstream drafting): ULBC-3 value convergence; ULBC-5a/5b and ULBC-8a/8b drafting (if qualification tentatively kept); ULBC-7 adaptation starts (reference codecs, gain methodology)
- <a id="T024-R04-C03"></a>列 3: Rules and test plans need ULBC-3 test sets [3]; the October drafts are the precondition for SA4#138 approval; ULBC-9 payload-format work proceeds in parallel from SID sizes

<a id="T024-R05"></a>
**T024-R05**

- <a id="T024-R05-C01"></a>列 1: SA4#138<br>16–20 Nov 2026
- <a id="T024-R05-C02"></a>列 2: Stage 3 (gates and approvals): final qualification decision (candidate-count framework) [10]; agree / de-bracket ULBC-3 and ULBC-4; ULBC-5/8 agree path; funding estimate and lab engagement; ULBC-6 de-bracketing
- <a id="T024-R05-C03"></a>列 3: Per the ULBC-2 schedule [4], the Letter of Intent (LoI) hard trigger of 23 December follows one month later as the override.

<a id="P025"></a>

## 5    Conclusion

<a id="P026"></a>

The dependency analysis yields a single, unambiguous guided order: close ULBC-4 from the inside out (complexity metric → complexity limits → bandwidth → others), then populate ULBC-3, then draft ULBC-5/8 on top of ULBC-3 with the qualification decision as the gate, with ULBC-7 adapting in parallel and ULBC-6 de-bracketing at the gate. Mapped onto the four remaining sessions, the critical path runs through the Shanghai meeting: the complexity items and the bandwidth decision taken there in the right order determine whether the October telco meetings can converge values or will be consumed by rework. We propose that SA4 adopt this guided order explicitly and reflect it in the meeting agendas.

<a id="P027"></a>

## 6    Proposals

<a id="P028"></a>

Proposal 1: Adopt the following Pdoc-level sequence: ULBC-4 (remaining items) → ULBC-3 (specific values) → ULBC-5a/5b and ULBC-8a/8b (rules and test plans, with the qualification-phase decision as the gate for 5a/8a per the companion framework); ULBC-7 adapts in parallel once the ULBC-3 reference codecs and the ULBC-4 gain methodology are fixed; ULBC-9's payload-format part follows SID sizes while its system-integration part continues in parallel; ULBC-6 de-brackets after the qualification decision.

<a id="P029"></a>

Proposal 2: Adopt the ULBC-4 internal order: complexity metric → complexity limits → sampling rate/bandwidth.

<a id="P030"></a>

Proposal 3: Adopt the decision schedule: Stage 1 (ULBC-4 core + early qualification attempt) at the Shanghai AH; Stage 2 (ULBC-4 tail, ULBC-3 values, ULBC-5/8 drafting, ULBC-7 adaptation) across the two October telcos; Stage 3 (qualification decision, funding, final P-docs) at SA4#138.

<a id="P031"></a>

Proposal 4: Record Proposals 1-3 as an editorial note in ULBC-2.

<a id="P032"></a>

## 7    References

<a id="P033"></a>

[1] S4-261670, Report from Audio SWG during 3GPP SA4#137-e

<a id="P034"></a>

[2]    S4-261739, [ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.1, SA4#137-e

<a id="P035"></a>

[3]    S4-261771, [ULBC-MED] ULBC Performance requirements (ULBC-3) v0.1.0, SA4#137-e

<a id="P036"></a>

[4] S4-261745, [ULBC-MED] ULBC-2 Timeline v0.1.0, SA4#137-e

<a id="P037"></a>

[5] S4-261729, [ULBC-MED] ULBC-6 Deliverables v0.2.0, SA4#137-e

<a id="P038"></a>

[6] S4-261728, ULBC-7 Processing plan v0.1.0, SA4#137-e (bracketed EVS copy)

<a id="P039"></a>

[7] S4-261722, ULBC-9 RTP Header Reduction and System Integration skeleton v0.0.1, SA4#137-e

<a id="P040"></a>

[8] S4-261627, On ULBC complexity requirements, Nokia, SA4#137-e

<a id="P041"></a>

[9] S4-261640, Proposed ULBC-MED design constraints, Orange, SA4#137-e

<a id="P042"></a>

[10] S4-261523, [ULBC-MED] On methodologies for qualification phase, vivo, Bytedance, SA4#137-e
