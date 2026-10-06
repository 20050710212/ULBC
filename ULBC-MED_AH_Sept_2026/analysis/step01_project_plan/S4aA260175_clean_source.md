# S4aA260175 — 原文 Markdown

> 来源 ZIP 内文件：`S4aA260175 ULBC development overview (ULBC-1) v0.2.0.docx`。按当前文本转换；选择 OOXML 主显示分支以消除图形 fallback 重复。保留图形文本与方括号，图形连接和原页面布局不复刻。段落/表行定位标记是提取索引，不是原文编号。

<a id="P000"></a>

Source: · Editor[^1]

<a id="P001"></a>

Title: · ULBC Permanent document (ULBC-1): Development overview

<a id="P002"></a>

Version: · 0.2.0

<a id="P003"></a>

Agenda Item: · 4.2

<a id="P005"></a>

## 1. Scope

<a id="P006"></a>

This document presents an overview of the development of Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite (ULBC) within 3GPP TSG SA4. The ULBC-MED development was initiated at SA4 #136 with the work item description in SP-260696 as approved at SA#112 in June 2026. The work is currently targeting completion in Release-20.

<a id="P007"></a>

Section 2 of this document describes a set of permanent documents serving as basis for the ULBC-MED standardization.

<a id="P008"></a>

## 2. ULBC Permanent Documents

<a id="P009"></a>

The standardisation of the ULBC will be documented in a series of permanent documents (Pdocs) each assigned with a responsible editor. They contain the most important guidelines, rules and decisions. The names of the documents are given below with a list of editors. This list may be amended as necessary during the ULBC standardization project.

<a id="P010"></a>

Editor’s note: Based on agreement at Audio SWG AH on ULBC-MED, the working assumption is to skip qualification phase and directly go for selection phase.

<a id="P011"></a>

Document name · Doc. Number · Editor

<a id="P012"></a>

1) · Overview · ULBC-1 · Audio SWG chair, Tomas Toftgård <br> · tomas.toftgard@ericsson.com

<a id="P013"></a>

2) · Time plan · ULBC-2 · ULBC-MED rapporteur, Huan-yu Su<br> · suhuanyu@vivo.com

<a id="P014"></a>

3) · Performance requirements · ULBC-3 · Stefan Bruhn<br> · stefan.bruhn@dolby.com

<a id="P015"></a>

4) · Design constraints · ULBC-4 · Stefan Döhla

<a id="P016"></a>

stefan.doehla@iis.fraunhofer.de

<a id="P017"></a>

5)

<a id="P018"></a>

Selection rules · ULBC-5 · Stéphane Ragot<br> · stephane.ragot@orange.com

<a id="P019"></a>

6) · Deliverables · ULBC-6 · Lei Li<br> · lilei348@huawei.com

<a id="P020"></a>

7) · Processing plan · ULBC-7 · Erik Norvell<br> · erik.norvell@ericsson.com

<a id="P021"></a>

8) · Test plan for selection phase · ULBC-8a · Milan Jelinek<br> · milan.jelinek@USherbrooke.ca

<a id="P022"></a>

9) · RTP header compression & system integration · ULBC-9 · Yujian Yin<br> · yinyujian@chinamobile.com

<a id="P023"></a>

<a id="P024"></a>

[

<a id="P025"></a>

## 3. ULBC standardization framework

<a id="P026"></a>

<a id="P027"></a>

1 · CANDIDATE DEVELOPMENT (proponent)<br>
2 · EVALUATION AND SELECTION (SA4)<br>
3 · POST-SELECTION OBLIGATIONS (winning proponent)<br>
4 · APPROVAL AND MAINTENANCE<br>
Candidate development<br>
Own datasets, curation and training procedure<br>
Submission and binding commitment<br>
Frozen codec · declarations · post-selection pledge<br>
SA4 technical evaluation<br>
Listening tests · common requirements and criteria<br>
SA4 selects winning candidate<br>
Unsuccessful proponents disclose nothing<br>
Winner discloses dataset and opens procedure<br>
Public reference or non-public data under suitable terms<br>
Frozen dataset reference<br>
Preserved via 3GPP / Organizational Partner<br>
Independent verification (NDA)<br>
Dataset + procedure reproduce model parameters<br>
Legal compliance verification<br>
Open to any party · outside SA4 scope<br>
SA approval of ULBC specification<br>
Subject to legal clearance by the competent bodies<br>
Maintenance / authorized retraining<br>
Uses the frozen reference; winner cooperates<br>
<br>Figure 1 – ULBC-MED codec-selection lifecycle

<a id="P028"></a>

Disclaimer: One key aspect is that the training dataset of the selected candidate is visible and inspectable at the end of the selection process, and that it remains available for inspection and for maintenance purposes thereafter. Until PCG has taken a decision, this is considered best business practice. This framework may be adjusted subject to recommendations from PCG, for example should such a recommendation entail that the training dataset be made available at an earlier stage. The exact legal framework under which this could happen would, however, depend on the guidance ultimately issued.<br>]

<a id="P029"></a>

<br>

<a id="P030"></a>

ULBC-1 gives an overview of the ULBC development organization for the work item.

<a id="P031"></a>

ULBC-2 gives a detailed time plan of the work item.

<a id="P032"></a>

ULBC-3 describes performance requirements for ULBC.

<a id="P033"></a>

ULBC-4 describes design constraints, which define a mandatory set of functional requirements for ULBC, e.g. sampling frequency/audio bandwidth, bitrates, complexity and algorithmic delay.

<a id="P034"></a>

ULBC-5 contains a set of codec selection rules. For the selection phase, the rules specify how to evaluate the best ULBC candidate among the ones submitted for selection.

<a id="P035"></a>

ULBC-6 defines the deliverables which the codec proponents have to deliver for the selection phase. The codec selection will be carried out only with codec candidates for which the full set of deliverables have been satisfactory provided in time in accordance with ULBC-6.

<a id="P036"></a>

ULBC-7 describes the processing plans for the selection tests.

<a id="P037"></a>

ULBC-8a describes the test plan for the selection phase.

<a id="P038"></a>

ULBC-9 captures agreed proposals and consolidated solutions on RTP header compression and ULBC system integration, aimed for inclusion in relevant technical specifications.

<a id="P039"></a>

<a id="P040"></a>

**页眉：** |  | 3GPP TSG-SA WG4 Audio SWG AH |  | S4aA260175
 | September 28-30, 2026 |

[^1]: Tomas Toftgård, tomas.toftgard@ericsson.com
