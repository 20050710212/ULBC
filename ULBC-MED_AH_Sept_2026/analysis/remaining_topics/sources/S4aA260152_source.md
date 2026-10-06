# S4aA260152 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260152-ULBC_FoM_Perceptual_Quality.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Fraunhofer IIS

<a id="P001"></a>

Title:    Proposed FoM on Perceptual Evaluation Criterion

<a id="P002"></a>

Document for:    Agreement

<a id="P003"></a>

Agenda Item:    4.2

<a id="P005"></a>

## 1. Introduction

<a id="P006"></a>

In contribution [1], the source proposes to introduce the concept of quality stairs as an objective in the ULBC performance requirements. This contribution makes a proposal on how to take this concept into account for the perceptual-evaluation-based selection rule of the FoM for the ULBC test campaigns, for qualification and selection phase.

<a id="P007"></a>

## 2. Proposal

<a id="P008"></a>

## 2.1 Requirements as elimination criterion

<a id="P009"></a>

Similar as in the performance requirements for previous speech coding work-items, [1] distinguishes between “Requirements” and “Objectives (Quality Stairs)”. As the name implies, requirements are proposed to be treated as minimum requirements for the proposed codec. It is thus proposed to treat this as an elimination criterion in the FoM: As soon as a candidate consistently fails one of the requirements (i.e. if it consistently fails the requirement across all labs this condition has been tested), it shall be eliminated.

<a id="P010"></a>

## 2.2 Points per quality stair reached

<a id="P011"></a>

The surviving candidates shall be ranked based on a point scheme. Per tested operating point and per quality stair reached, the candidate shall receive one point. Additionally, a weighting scheme might be applied for different operating points. The candidate with the most points shall be selected.

<a id="P012"></a>

Since the scoring of the reference codecs might not always be 100% linear, the order of the reference conditions doesn’t need to be taken into account for the distribution of points. In case the tests are carried out in multiple labs, points should be given per achieved quality stair per lab.

<a id="P013"></a>

## 3. Example

<a id="P014"></a>

For clean speech at 1.0 kbit/s WB, the following performance requirements are defined (for simplicity, and to purely illustrate the concept, several columns detailing the table from the original contribution [1] have been removed):

<a id="T015"></a>

<a id="T015-R01"></a>
**T015-R01**

- <a id="T015-R01-C01"></a>列 1: Category
- <a id="T015-R01-C02"></a>列 2: BW
- <a id="T015-R01-C03"></a>列 3: Bitrate (kbit/s)
- <a id="T015-R01-C04"></a>列 4: Requirements
- <a id="T015-R01-C05"></a>列 5: Objectives <br>(Quality stairs)

<a id="T015-R02"></a>
**T015-R02**

- <a id="T015-R02-C01"></a>列 1: Clean speech<br>-26,-16,-36 dBov
- <a id="T015-R02-C02"></a>列 2: WB
- <a id="T015-R02-C03"></a>列 3: 1.0
- <a id="T015-R02-C04"></a>列 4: NWT AMR-WB @ 8.85
- <a id="T015-R02-C05"></a>列 5: NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="P016"></a>

Candidate A doesn’t reach the requirement “NWT AMR-WB @ 8.85” and thus gets eliminated

<a id="P017"></a>

Candidate B reaches the requirement “NWT AMR-WB @ 8.85”. Additionally, Candidate B reaches the quality step “NWT AMR-WB @ 12.65” and thus receives 1 point.

<a id="P018"></a>

Candidate C reaches the requirement “NWT AMR-WB @ 8.85”. Additionally, Candidate C reaches the quality steps “NWT AMR-WB @ 12.65” and “NWT AMR-WB @ 14.25” and thus receives 2 points.

<a id="P019"></a>

## 4. Conclusion

<a id="P020"></a>

It is proposed to agree to the proposals made in clause 2 and include this in the ULBC-5a and ULBC-5b Pdocs.

<a id="P022"></a>

References

<a id="P023"></a>

S4aA260148 - Use of Quality Stairs as an Objective in Performance Requirements

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH    Tdoc S4aA260152<br>    Shanghai, China, September 28-30, 2026
