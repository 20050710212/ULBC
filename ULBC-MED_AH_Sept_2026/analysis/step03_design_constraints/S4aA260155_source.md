# S4aA260155 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260155_ULBC_MED_On_ULBC_algorithmic_delay.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG Ad-hoc on ULBC-MED    S4aA260155

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Qualcomm Incorporated

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC algorithmic delay

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P011"></a>

The ULBC Design Constraints Permanent document (ULBC-4) [1] contains the following draft (bracketed) constraint for algorithmic codec delay: “[The algorithmic codec delay shall not exceed the bundling time + x ms]”. At the SA4#137-e meeting, the following proposals were made for the value of x, and listed in ULBC-4 as draft (bracketed) proposals:

<a id="P012"></a>

- x=0 to 5ms (1621)

<a id="P013"></a>

- x<=80ms (1547)

<a id="P014"></a>

- x=EVS range (email)

<a id="P016"></a>

## 2. Discussion

<a id="P018"></a>

In S4-261621 [2], a value of x = 0-5ms was proposed, with the justification that there is limited evidence that additional look-ahead improves subjective quality at 1–1.4 kbps for ML-based codecs. However, a literature reference for this assertion was not provided in S4-261621, such as, for example, a study/paper that varies the lookahead x of an ML-based codec operating at or around ULBC bitrates and shows no speech quality benefit for x > 0-5ms. Even if such study exists, it is unlikely to cover all possible ML codec architectures and designs. It will be inherently limited to certain types and architectures of ML-based codecs. From an information theoretical perspective, it is expected that lookahead into future data improves the coding efficiency. With an appropriate codec design, this benefit should be obtainable. It is, therefore, not justified to disallow lookahead or ULBC.

<a id="P020"></a>

In S4-261547 [3], it was proposed to allow a value of x as high as 80ms with the following justification: NB-NTN via GEO satellite radio interface round-trip propagation delay alone is high (541.46 ms), so an increase to the codec algorithmic delay is justified if this can improve codec performance. It is true that in a high latency system, more leeway can be given to the codec algorithmic delay with smaller relative impact to the mouth-to-ear delay. However, this needs to be balanced with the need to keep delay as low as practically possible and not overly increase the mouth-to-ear delay of an already delay-laden system.

<a id="P022"></a>

In an email discussion during SA4#137-e, a proposal of x = “EVS range” was also made, as documented (in brackets) in ULBC-4 [1]. This is less restrictive than the proposal in S4-261621 [1]. However, it may still be low, given the high latencies inherent in the NB-NTN over GEO system.

<a id="P024"></a>

We believe a compromise can be reached between the conflicting needs to keep algorithmic delay low and simultaneously allow enough algorithmic delay to improve quality at the low bit rates at which ULBC needs to operate. Given the high delay inherent in NB-NTN GEO radio interface, we believe higher value for x than existing 3GPP codecs is justified. However, we propose a value x=40ms, as a compromise with the need to keep mouth-to-ear delay as low as practically possible and justified.

<a id="P026"></a>

## 3. Proposal.

<a id="P028"></a>

We propose the following change to the ULBC Design Constraints permanent document:

<a id="T029"></a>

<a id="T029-R01"></a>
**T029-R01**

- <a id="T029-R01-C01"></a>列 1: Algorithmic codec delay
- <a id="T029-R01-C02"></a>列 2: The algorithmic codec delay shall not exceed the bundling time + 40 ms.
- <a id="T029-R01-C03"></a>列 3: Editor's note: the value of x is FFS. One-way GEO propagation is ~270 ms; the algorithmic codec delay and the bundling period are the controllable codec-layer contributions.

<a id="P032"></a>

## 4. References

<a id="P034"></a>

[1] 3GPP S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4)", v0.2.1, SA4#137-e, August 2026

<a id="P035"></a>

[2] Tdoc S4-261621, "[ULBC-MED] ULBC Design Constraints", SA4#137-e, August 2026

<a id="P036"></a>

[3] Tdoc S4-261547, "[ULBC-MED] On Algorithmic Delay of ULBC-MED", SA4#137-e, August 2026
