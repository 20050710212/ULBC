# S4aA260136 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260136  On ULBC4 Frame size.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWG Ad-hoc on ULBC-MED    S4aA260136

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    On ULBC-4: Frame size

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Agreement

<a id="P009"></a>

Introduction

<a id="P010"></a>

The present document proposes clarifications and updates for design constraints Pdoc ULBC-4 (S4-261847). The focus in this document is on the ULBC frame size.

<a id="P013"></a>

The latest version of ULBC-4 (S4-261847) contains the following proposal on frame length:

<a id="T015"></a>

<a id="T015-R01"></a>
**T015-R01**

- <a id="T015-R01-C01"></a>列 1: [ Frame length
- <a id="T015-R01-C02"></a>列 2: The codec frame length shall be one of 20, 40, 80 ms
- <a id="T015-R01-C03"></a>列 3: ]

<a id="P017"></a>

The frame length has no direct impact on the algorithmic delay of ULBC as this is related to the bundling period, as defined in ULBC-4 by

<a id="P019"></a>

Algorithmic codec delay: Bundling-time buffering delay plus any other delays inherent in the codec algorithm (e.g. look-ahead, sample-rate conversion, decoder post-processing).

<a id="P021"></a>

However, in real world applications the frame length of the codec influences of the mouth-to-ear delay due to the processing delay as described in TR 26.940 clause 5.1.2.2 and 5.1.3 and in more detail in S4-251382. With shorter frame lengths in relation to the bundling time, the encoder needs to collect less audio sample to start the encoding process and only the processing of the last frame of the bundling period is a real contribution to the mouth to ear delay. Similar to the encoder side, the decoder can start the playout already after the first codec frame has been decoded. Here only the first is causing a the contribution to the mouth to ear delay.

<a id="P024"></a>

The source is aware that in theory the processing delay can be zero and for this case, having shorter frames or not has no influence on the mouth to ear delay. However, in the worst case scenario as outlined in TR 26.940, twice the delay of the frame size is added to the mouth-to-ear-delay, which corresponds to a 80ms difference comparing the frame length 80ms to 40ms.

<a id="P026"></a>

To avoid such worst case scenario, the source sees 40ms frame length as the upper limit as for instance also proposed by S4-261621. It proposed to agree on the following box for ULBC-4:

<a id="T029"></a>

<a id="T029-R01"></a>
**T029-R01**

- <a id="T029-R01-C01"></a>列 1: Frame length
- <a id="T029-R01-C02"></a>列 2: The codec frame length shall be one of 20 or 40 ms
- <a id="T029-R01-C03"></a>列 3: 
