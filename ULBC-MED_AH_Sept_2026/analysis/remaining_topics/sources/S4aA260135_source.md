# S4aA260135 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260135 Selection rules for qualification.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWB Ad Hoc Meeting on ULBC-MED    S4aA260135

<a id="P001"></a>

28-30 September 2026, Shanghai, China

<a id="P003"></a>

Source:    Nokia

<a id="P004"></a>

Title:    Selection rules for ULBC qualification phase

<a id="P005"></a>

Agenda item:    4.5 - Qualification/Selection rules (ULBC-MED)

<a id="P006"></a>

Document for:    DISCUSSION and AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

ULBC-MED work item [1] was approved by SA Plenary in June. ULBC-MED addresses IMS voice call over GEO access in Rel-20. This timeline is considered challenging for comprehensive codec work. Given the large number of parties interested in submitting a candidate, it seems important to run a Qualification Phase. Due to the tight timeline, there is also strong interest by some parties to look for ways to potentially skip Qualification and go directly to a Selection Phase.

<a id="P012"></a>

In a previous input [2], the source discussed ULBC Qualification and Selection Rules and Deliverables.

<a id="P014"></a>

This input includes in its Annex an Editor’s input on potential ULBC-5a Pdoc on Selection Rules for Qualification Phase. It is for consideration in case Qualification Phase is confirmed.

<a id="P016"></a>

The source considers that Qualification Phase is preferable to reduce the number of candidates and avoid complexities and potential additional test costs associated with skipping the Qualification and running Selection tests with a very large number of codecs under test.

<a id="P018"></a>

## 2. Discussion

<a id="P019"></a>

The approach of using two main Rules, Rule 1 and Rule 2, has received some support. Rule 1 is an elimination rule, while Rule 2 uses Figure(s) of Merit to analyse and compare performance of candidate solutions across relevant criteria.

<a id="P021"></a>

The source considers the following approaches for FoMs, discussed previously in [2]:

<a id="P023"></a>

Percentage of passed requirements. This could include weights for various requirement categories that are still TBD.

<a id="P024"></a>

Percentage of passed objectives. For Qualification, one possibility would be to use this potential FoM only as a tie-breaker condition to limit the number of candidates progressing to Selection Phase to the desired number.

<a id="P025"></a>

FoM relating to complexity. For example, somewhat relaxed maximum limits for memory use and computational complexity would be defined as part of the ULBC Design Constraints. This FoM would then favour those candidate codecs that provide required performance at lower complexity (memory use, computational complexity). Details are TBD. This approach assumes an agreed practical simulation, e.g., based on ONNX frameworks. Self-reported complexity numbers are not applicable.

<a id="P027"></a>

## 3. Summary and proposal

<a id="P028"></a>

Annex A provides a proposed starting point for Permanent Document ULBC-5a on Selection Rules for Qualification Phase. According to the proposed procedure, at most five candidates would proceed to ULBC Selection Phase. This is for consideration in case Qualification Phase is confirmed.

<a id="P030"></a>

Under current assumptions, it is the preference of the source to Qualification Phase. There are certain open items and risks, e.g., potentially increased test costs for Selection test experiments with a very large number of codecs under test and the possibility of catastrophically bad candidate codecs affecting the Selection results (that would also form at least a part of ULBC Characterization report), which should be clarified to consider skipping Qualification.

<a id="P034"></a>

References

<a id="P035"></a>

[1]    SP-260696, “Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite” (ULBC-MED)

<a id="P036"></a>

[2]    S4-261578, “On ULBC qualification and selection rules and deliverables”, Nokia

<a id="P040"></a>

Annex A – Skeleton proposal for ULBC-5a

<a id="P042"></a>

Source:    Editor

<a id="P043"></a>

Title:    ULBC-5a: Selection Rules for Qualification Phase

<a id="P044"></a>

Version:    0.0

<a id="P048"></a>

## 1.    Introduction

<a id="P050"></a>

This Permanent Document describes the Selection Rules for the ULBC Qualification Phase.

<a id="P052"></a>

## 2.    Objectives

<a id="P054"></a>

The objectives of the Qualification are to eliminate candidates presenting performances well below the average, and, if necessary, to reduce and to limit the number of candidates to a manageable number for the more comprehensive Selection Phase.

<a id="P056"></a>

## 3.    Qualification Rules

<a id="P058"></a>

Two main Rules, Rule 1 and Rule 2, are employed. Rule 1 is an elimination rule, while Rule 2 uses Figure(s) of Merit to analyse and compare performance of candidate solutions across relevant criteria.

<a id="P060"></a>

Rule 1:

<a id="P061"></a>

Demonstration of full [reported/verified] compliance with the Design Constraints and other Qualification requirements set in ULBC-6 Deliverables:

<a id="P062"></a>

...

<a id="P064"></a>

Rule 2:

<a id="P065"></a>

Ranking of the candidate solutions is performed according to the following Figure(s) of Merit (FoM(s)):

<a id="T067"></a>

<a id="T067-R01"></a>
**T067-R01**

- <a id="T067-R01-C01"></a>列 1: Figure of Merit (FoM)
- <a id="T067-R01-C02"></a>列 2: Description

<a id="T067-R02"></a>
**T067-R02**

- <a id="T067-R02-C01"></a>列 1: FoM 1<br>[Percentage of passed requirements]
- <a id="T067-R02-C02"></a>列 2: [Note: Potentially consider weighting for balancing categories]

<a id="T067-R03"></a>
**T067-R03**

- <a id="T067-R03-C01"></a>列 1: ...
- <a id="T067-R03-C02"></a>列 2: ...

<a id="P069"></a>

Table 1: Figure(s) of Merit (FoM(s))

<a id="P072"></a>

## 4.    Qualification Procedure

<a id="P074"></a>

The Qualification procedure will consist of the following steps:

<a id="P075"></a>

[

<a id="P076"></a>

Option 1:

<a id="P077"></a>

A neutral entity [(the Host Lab)] will perform the blinding of candidates. The blinding is used for the Qualification tests.

<a id="P078"></a>

The Qualification test results will be presented and analysed while keeping secret the identity of the candidates. Qualification Rule 2 will be applied and its results documented for the blinded candidates.

<a id="P079"></a>

Following the review and discussion of the test results in Qualification test GAL report and application of Rule 2, SA4 will try to reach a consensus on a quality ranking of the candidates.

<a id="P080"></a>

Each candidate will present its solution according to the Qualification requirements set in ULBC-6 Deliverables and show the compliance with the Design Constraints, as set in Qualification Rule 1.

<a id="P081"></a>

The blinding assigned to each candidate will be revealed [by the Host Lab].

<a id="P082"></a>

A final discussion and review of the solution characteristics and test results will take place.

<a id="P083"></a>

SA4 will identify [at most five (5)] candidates to advance to the Selection Phase.

<a id="P086"></a>

Option 2:

<a id="P088"></a>

A [first] neutral entity [(the Host Lab)] will perform the blinding of candidates. The blinding is used for the Qualification tests, including grouping of the candidates for each experiment by a [second] neutral entity [(the Host Lab)].

<a id="P089"></a>

The Qualification test results will be presented and analysed while keeping secret the identity of the candidates. Qualification Rule 2 will be applied and its results documented for the blinded candidates.

<a id="P090"></a>

Following the review and discussion of the test results in Qualification test GAL report and application of Rule 2, SA4 will try to reach a consensus on a quality ranking of the candidates.

<a id="P091"></a>

Each candidate will present its solution according to the Qualification requirements set in ULBC-6 Deliverables and show the compliance with the Design Constraints, as set in Qualification Rule 1.

<a id="P092"></a>

The blinding assigned to each candidate will be revealed [by the Host Lab].

<a id="P093"></a>

A final discussion and review of the solution characteristics and test results will take place.

<a id="P094"></a>

SA4 will identify [at most five (5)] candidates to advance to the Selection Phase.

<a id="P095"></a>

]
