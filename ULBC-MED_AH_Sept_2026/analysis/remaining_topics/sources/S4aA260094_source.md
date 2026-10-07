# S4aA260094 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260094 [ULBC-MED] Test conditions and weighting factors for ULBC FoM.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP SA4-(AH) Audio SWG on ULBC-MED    Tdoc S4aA260094

<a id="P001"></a>

Shanghai, China, 28 - 30 September 2026

<a id="P003"></a>

Source:    vivo Mobile Communication Co.

<a id="P004"></a>

Title:    [ULBC-MED] Test conditions and weighting factors for ULBC FoM

<a id="P005"></a>

Agenda item:    4.5, 4.8

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

Introduction

<a id="P011"></a>

In the current process of defining requirements and verification procedures for ULBC selection involving up to 20 participants, one thing is inevitable: comparing candidates across different scenarios to get multi-faceted/multi-dimensional performance metrics, such as voice quality under different application conditions. One effective way to enable a fair and equitable selection is to use uneven weighting factors on these parameters to get the so-called FoM (figure of merit), which is basically a weighted average of the test results.

<a id="P013"></a>

This contribution proposes a set of initial weights for consideration.

<a id="P015"></a>

Discussions

<a id="P017"></a>

Below table contains the following proposals:

<a id="P018"></a>

Test conditions for Qualification phase (if such a qualification phase is determined to be necessary);

<a id="P019"></a>

Corresponding weights to be applied on MOS results of those qualification test conditions to obtain the FoM;

<a id="P020"></a>

Test conditions for Selection phase;

<a id="P021"></a>

Weights for Selection tests;

<a id="P022"></a>

List of languages to be used for tests


<a id="EMF-table-transcription"></a>

## 嵌入表格文字转录（2026-10-08 评审补充）

以下根据原 DOCX 的 EMF 表格渲染图逐行人工转录，不是原文新增章节。原始图保留于本地 `094_media/image1.png`；此转录使仅发布 Markdown 时仍能检查论据。X 表示原表勾选，— 表示空白。合并权重单元格用“组：百分比”表示，**同组权重只计一次**，不是每行各占该百分比。

| Mode | Test conditions | Noise level | Qualification | Qualification weight | Selection | Selection weight | Languages |
|---|---|---|---|---|---|---|---|
| ULBC 1.4 kb/s | -16 dBov | Clean | — | — | X | clean 组：20% | Mandarin, German |
| ULBC 1.4 kb/s | -26 dBov | Clean | X | 25% | X | 同 clean 组 | Eng, Fr, Jap |
| ULBC 1.4 kb/s | -36 dBov | Clean | — | — | X | 同 clean 组 | Arabic, Span |
| ULBC 1.4 kb/s | Street | 15 dB SNR | X | 10% | X | noise 组：10% | Eng |
| ULBC 1.4 kb/s | Office | 20 dB SNR | — | — | X | 同 noise 组 | Fr |
| ULBC 1.4 kb/s | -26 dBov @2%_80 | Clean | X | 10% | X | loss 组：10% | Span |
| ULBC 1.4 kb/s | -26 dBov @6%_160 | Clean | — | — | X | 同 loss 组 | Eng |
| ULBC 1.4 kb/s | Tandem: AMR WB@12.65 kb/s => ULBC | Clean | X | 5% | X | 5% | Jap |
| ULBC 1.4 kb/s | DTX/CNG Street noise | 15 dB SNR | — | — | X | 5% | German |
| ULBC 1.0 kb/s | -16 dBov | Clean | — | — | X | clean 组：20% | Eng, Fr |
| ULBC 1.0 kb/s | -26 dBov | Clean | X | 25% | X | 同 clean 组 | Arabic, German |
| ULBC 1.0 kb/s | -36 dBov | Clean | — | — | X | 同 clean 组 | Mandarin, Span |
| ULBC 1.0 kb/s | Street | 15 dB SNR | — | — | X | noise 组：10% | Jap |
| ULBC 1.0 kb/s | Office | 20 dB SNR | X | 10% | X | 同 noise 组 | Fr |
| ULBC 1.0 kb/s | -26 dBov @2%_80 | Clean | — | — | X | loss 组：10% | Eng |
| ULBC 1.0 kb/s | -26 dBov @6%_160 | Clean | X | 10% | X | 同 loss 组 | German |
| ULBC 1.0 kb/s | Tandem: AMR WB@12.65 kb/s => ULBC | Clean | — | — | X | 5% | Mandarin |
| ULBC 1.0 kb/s | DTX/CNG Street noise | 15 dB SNR | X | 5% | X | 5% | Arabic |
| Total weight for FoM | 两码率合计 | — | — | 100% | — | 100% | — |

表中的 qualification 以原文“若该阶段被确定必要”为前提。该贡献在 R4 为 n；条件、语言及百分比均是提案，不能当作最终 ULBC-5/8a 的要求。@2%_80 / @6%_160 保留原表标签，不据此推定所有场景的 loss pattern。表格没有给出组内多条件的完整汇总算法。

<a id="P028"></a>

Proposal

<a id="P030"></a>

It is proposed to take into account contents in Clause 2 in developing a suitable FoM formulation in ULBC-5a/5b and test plan in ULBC-8a/8b for ULBC Qualification/Selection phases.
