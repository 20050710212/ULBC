# S4aA260110 — 原文 Markdown

> 来源 ZIP 内文件：`S4aA260110_[ULBC-MED] On the qualification-phase decision.docx`。按当前文本转换；选择 OOXML 主显示分支以消除图形 fallback 重复。保留图形文本与方括号，图形连接和原页面布局不复刻。段落/表行定位标记是提取索引，不是原文编号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG (AH) Meeting · S4aA260110

<a id="P001"></a>

Shanghai, China, 28 - 30 September 2026

<a id="P004"></a>

Source: · Huawei Technologies Co., Ltd.

<a id="P005"></a>

Title: · [ULBC-MED] On the qualification-phase decision

<a id="P006"></a>

Agenda item: · 4.2

<a id="P007"></a>

Document for: · Discussion and Agreement

<a id="P009"></a>

## 1 · Introduction

<a id="P010"></a>

At SA4#137-e, the qualification phase was kept as a bracketed option in ULBC-2 v0.1.0 [1]: the Shanghai AH meeting is invited to take an early decision "if possible", and SA4#138 (Calgary, 16-20 November 2026) takes the final decision. The discussion so far has been mostly positional - keep versus skip. This contribution provides a structured decision analysis: it lays out the two candidate paths, assesses them from five angles (experimental design, cost, timeline, risk, historical precedent), and derives a decision framework coupled to the candidate count.

<a id="P011"></a>

## 2 · The decision and the two paths

<a id="P012"></a>

The qualification decision determines how the field of candidates is narrowed before the selection test:

<a id="P013"></a>

Path A - with qualification (default in the current ULBC-2 brackets): binding LoI by 23 December 2026; candidate submission and qualification testing in January 2027; qualification decision at SA4#139 (February 2027, up to 5 candidates advance); selection submission on 19 March 2027; selection tests from March to May; winning candidate at SA4#140 (May 2027).

<a id="P014"></a>

Path B - without qualification: binding LoI by 23 December 2026; all binding candidates proceed directly to the selection submission on 19 March 2027; selection tests from March to May; winning candidate at SA4#140.

<a id="P015"></a>

Both paths converge on the same selection window (19 March - May 2027) and the same Rel-20 completion target. The essential difference is the size of the candidate field entering the selection phase.

<a id="P016"></a>

## 3 · Multi-angle analysis

<a id="P017"></a>

## 3.1 · Experimental design and statistical discrimination

<a id="P018"></a>

The indication-of-interest round of June 2026 and the working assumption in S4-261523 [2] point to a field of roughly 20 potential candidates. A single selection experiment carrying 20 candidates x 2 bitrates + anchors amount to ~46 conditions, exceeding the recommended DCR cap of ~36-40 conditions and collapsing the anchor share to ~13% (the historical range in 3GPP selection tests is 29-50%). A defensible ranking of 20 candidates in one campaign is without precedent (AMR 11→5, AMR-WB 7→5, EVS 13→5). Testing the 20 candidates in groups would inevitably compromise the precision of the results, and it seems more logical for such a reduction in precision to occur during the qualification stage.

<a id="P019"></a>

## 3.2 · Cost and funding

<a id="P020"></a>

A simplified organizational approach may be adopted during the qualification phase to reduce costs; for instance, each candidate conducts its own internal listening tests while performing partial cross-testing on another candidate, with only the functions of the neutral "Host Lab" and "Global Analysis Lab" being outsourced [6]. The objective evaluation (design-constraint compliance, AFR, attenuation, gain) is in-house by nature. The qualification cost is therefore a small fraction of the selection cost.

<a id="P021"></a>

The selection phase is the opposite: it is the dominant funded item, executed by contracted listening labs, and its cost scales with the number of CuT conditions and experiments. The EVS selection-and-characterization budget was 1.2 M EUR [8], dimensioned for a field that had already been narrowed to five qualified candidates. Running selection with an unfiltered field of ~20 candidates would multiply the dominant cost item roughly fourfold as a total.

<a id="P022"></a>

## 3.3 · Timeline and critical path

<a id="P023"></a>

Path A inserts ~6-8 weeks between the LoI deadline and the selection start (January qualification testing, February decision at SA4#139). EVS needed about four months for the same step (executable submission November 2012 to qualification meeting March 2013) [6]; the ULBC compression to ~6 weeks is aggressive but it could be addressed by the lean design: a reduced condition matrix, in-house labs, and objective evaluation that proceeds in parallel.

<a id="P024"></a>

Path B saves those weeks upfront but concentrates all testing into the March to May window with a larger field: more candidates mean more experiments or more parallel labs, longer processing and analysis, and a real risk that the selection campaign does not fit the window at all.

<a id="P025"></a>

## 3.4 · Risk asymmetry

<a id="P026"></a>

The two error modes of the decision are not symmetric:

<a id="P027"></a>

Keep qualification, but few candidates materialize: the waste is a neutral HL/GAL fee and proponent in-house effort on a small field. The decision framework below (hard trigger on the binding LoI count) caps this error mode explicitly.

<a id="P028"></a>

Skip qualification, but a large field materializes: the selection test is either statistically infeasible (~46 conditions vs the DCR cap) or blows the budget (~4x on the dominant cost item). Additionally, there is a risk of delaying the release schedule for R20 ULBC.

<a id="P029"></a>

A decision under uncertainty should favour the option whose downside is bounded. On this criterion, keeping the qualification phase as the default dominates.

<a id="P030"></a>

## 3.5 · Historical precedent

<a id="P031"></a>

AMR, AMR-WB and EVS all ran a competitive qualification phase before selection [2]; IVAS entered selection directly - with a single joint candidate and no competitive entry field. The differentiator across all four cases is the expected number of competing candidates, not a doctrinal preference. The June 2026 indications point to a competitive field for ULBC.

<a id="P032"></a>

## 4 · Synthesis: comparison and decision framework

<a id="P033"></a>

Table 1: Multi-criteria comparison of the two paths

<a id="T034"></a>

**T034-R01**

- 列 1: Criterion
- 列 2: Path A - with qualification
- 列 3: Path B - without qualification

**T034-R02**

- 列 1: Statistical feasibility of selection
- 列 2: ≤5 candidates x 2 rates + anchors ≈ 16 conditions - within the DCR cap
- 列 3: ~20 candidates ≈ 46 conditions vs cap ~36-40; anchor share ~13% (historical 29-50%)

**T034-R03**

- 列 1: Selection cost
- 列 2: Dimensioned for ≤5 candidates
- 列 3: Scales with the field; ~4x the dominant funded item at ~20 candidates

**T034-R04**

- 列 1: Timeline
- 列 2: 6-8 weeks before 19 March; EVS needed ~4 months - addressed by the lean design [6]
- 列 3: Saves the weeks but risks overfilling the March to May selection window itself

<a id="P036"></a>

Furthermore, the decision on whether a qualification stage is required depends on the number of LoIs; the binding LoI count of 23 December is the hard trigger, one month after the SA4#138 final decision, so the framework must let SA4#138 decide on the best available signals and let the LoI count act as the override:

<a id="P037"></a>

Table 2: Decision framework coupled to the candidate count

<a id="T038"></a>

**T038-R01**

- 列 1: Signal
- 列 2: Timing
- 列 3: Reading
- 列 4: Action

**T038-R02**

- 列 1: Indication of interest (SA4 reflector)
- 列 2: 19 June 2026 (observed)
- 列 3: 20 potential candidates
- 列 4: Baseline expectation: competitive field; qualification remains the default plan

**T038-R03**

- 列 1: Binding LoI count (hard trigger)
- 列 2: 23 December 2026
- 列 3: <5
- 列 4: Qualification dropped by email agreement; direct selection (IVS path); ULBC-2 brackets resolved; ULBC-5a/8a content migrates into ULBC-5b/8b

**T038-R04**

- 列 1: Binding LoI count (hard trigger)
- 列 2: 23 December 2026
- 列 3: ≥5
- 列 4: Proceed per the SA4#138 decision (default: qualification kept)

<a id="P039"></a>

## 5 · Conclusion

<a id="P040"></a>

Weighing all five angles: Experimental design and cost analysis indicate that within a single selection window, there are numerous difficulties in testing approximately 20 unscreened candidate solutions using reasonable methods or affordable prices; the timeline analysis shows that skipping qualification does not reliably save calendar but concentrates risk into the selection stage; the risk analysis shows a bounded, recoverable downside for keeping qualification against an unbounded downside for skipping it; the precedents show that qualification is the norm exactly when a competitive field is expected. We therefore conclude that the qualification phase should be kept as the default plan for Rel-20, executed in the lean organization, with an automatic exit if fewer than 5 binding LoIs are received by 23 December 2026.

<a id="P041"></a>

## 6 · Proposals

<a id="P042"></a>

Proposal 1: the qualification phase should be kept as the default plan for Rel-20, executed in the lean organization, with an automatic exit if fewer than 5 binding LoIs are received by 23 December 2026.

<a id="P043"></a>

## 7 · References

<a id="P044"></a>

[1] S4-261745, [ULBC-MED] ULBC-2 Timeline v0.1.0, SA4#137-e

<a id="P045"></a>

[2] S4-261523, [ULBC-MED] On methodologies for qualification phase, vivo, Bytedance, SA4#137-e

<a id="P046"></a>

[3] S4-261549, [ULBC-MED] On Qualification Test Plan for ULBC-MED, Huawei, SA4#137-e

<a id="P047"></a>

[4] S4-261502, [ULBC-MED] Maintaining a fallback and contingency activity for Rel-20 ULBC, Qualcomm, SA4#137-e

<a id="P048"></a>

[5] S4-261583, [ULBC-MED] On funding of the qualification phase, Fraunhofer IIS, SA4#137-e

<a id="P049"></a>

[6] EVS-2 (S4-141411), EVS Project plan

<a id="P050"></a>

[7] EVS-5a (S4-121249), EVS Selection Rules for Qualification Phase

<a id="P051"></a>

[8] EVS-6b (S4-140630), EVS Selection Deliverables
