# S4aA26093 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260093 [ULBC-MED] Thoughts on complexity and memory adjusted FoM.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP SA4-(AH) Audio SWG on ULBC-MED    Tdoc S4aA260093

<a id="P001"></a>

Shanghai, China, 28 - 30 September 2026

<a id="P004"></a>

Source:    vivo Mobile Communication Co.

<a id="P005"></a>

Title:    [ULBC-MED] Thoughts on complexity and memory adjusted FoM

<a id="P006"></a>

Document for:    Discussion and Agreement

<a id="P007"></a>

Agenda item:    4.5

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

In current ULBC-4 [1] the complexity and memory design constraints are still open. In order to get prepared for the upcoming F2F meeting in Shanghai, the source would like to share the following thoughts.

<a id="P011"></a>

There are two aspects concerning the complexity: (1) how to measure the computational complexity of an AI based codec, taking into account the current or future terminal capabilities that are rapidly evolving over time, and (2) how to set the limits/constraints that are fair and equitable to the need of selecting the best overall candidate. This contribution addresses the latter point (2).

<a id="P012"></a>

## 2    Discussion

<a id="P013"></a>

It is expected that different candidate codec will have different complexity and memory requirements, setting up hard limits that eventually rule out some candidates prematurely should be avoided. However larger complexity and memory requirements do increase manufacturers cost of implementation, increase power consumption that brings a set of other new issues, so in the selection of ULBC candidate we need to be able to factor in the complexity aspect in the decision making process. Simply put, if audio qualities are similar between two candidates, then the one with lower complexity should win. Similarly, if a candidate needs a higher complexity and/or larger memory footprints, then it should deliver some speech quality advantage to be justified.

<a id="P014"></a>

Conceptually, the above statement might be agreeable.

<a id="P015"></a>

## 3    Proposal

<a id="P016"></a>

The following complexity and memory adjusted FoM formulation is proposed:

<a id="P017"></a>

FoMFinal = α x FoMMOS

<a id="P018"></a>

Where FoMMOS is the FoM obtained based on weighted average of subjective test results, and the complexity adjustment factor α is obtained by the following:

<a id="P019"></a>

α = 1.0

<a id="P020"></a>

if(Memory ≤[10]MB .AND. Complexity≤[1.5]GFLOPS, then

<a id="P021"></a>

α=1.0

<a id="P022"></a>

else

<a id="P023"></a>

if (Memory>[10]MB) α=α*(1-[0.05]*(Memory-10)/10), and

<a id="P024"></a>

if (Complexity>1.5GFLOPS) α=α*(1-[0.02]*(Complexity-1.5)/1.5)

<a id="P025"></a>

endif

<a id="P026"></a>

## 4    References

<a id="P027"></a>

[1]    S4-261847: “[ULBC-MED] ULBC Design Constraints (ULBC-4)”, v0.2.1, May 2026

<a id="P028"></a>

[2]        SP-260696: "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", June 2026
