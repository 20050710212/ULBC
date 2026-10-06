# S4aA260116 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260116[ULBC-MED] On ULBC Algorithmic Delay.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 SWG (AH) Meeting    S4-260116

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Huawei Technologies Co., Ltd

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC Algorithmic Delay

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

## 1 Introduction

<a id="P010"></a>

The algorithmic delay constraint in ULBC-4 v0.2.0 [1] has three options in brackets: bundling time + 0-5 ms, bundling time + up to 80ms, and the EVS range. This contribution proposes the constraint "bundling time + 80ms algorithmic delay". To prove this, we use published evidence that look-ahead measurably improves neural codec quality and show that extra 80ms influence to ULBD scenario is small.

<a id="P011"></a>

## 2 Discussion

<a id="P012"></a>

## 2.1 Paper evidence that look-ahead improves AI-based codec quality

<a id="P013"></a>

The quality benefit of non-causal processing (look-ahead / future context) in neural audio codecs is well documented in the literature:

<a id="P014"></a>

EnCodec (Défossez et al., arXiv:2210.13438): the streamable model uses one-sided (causal) padding while the non-streamable model splits convolution padding equally before and after each frame, i.e. uses future context. In the paper's Table 3 (6 kbps), the non-streamable configuration outperforms the streamable one: SI-SNR 7.46 vs 6.67 and ViSQOL 4.39 vs 4.35. The authors note "a small degradation switching from non-streamable to streamable" - directly quantifying the quality cost of giving up look-ahead [2];

<a id="P015"></a>

StreamCodec (Jiang et al., arXiv:2504.06561, IEEE SPL 2025): states that structural causality causes audio quality loss, and its residual scalar-vector quantizer is explicitly designed to "compensate for the audio quality loss caused by structural causality" - acknowledging that a fully causal codec is inherently quality-limited relative to a non-causal one [3];

<a id="P016"></a>

In the ULBC operating point (1.0 and 1.4 kbps), the quantization noise has higer level vs 6 kbps-class evaluations; the codec's ability to use future context (which change model task from blind to non-blind prediction) is one of the few remaining options to improve perceptual quality. So, using short-term look ahead (lower than bundling time) allows to increase perceptual quality, which is important for ULBC.

<a id="P017"></a>

Also, we need to mention that look-ahead should be independent of the bundling period, because look-ahead is fixed by model architecture.

<a id="P019"></a>

## 2.2 Delay budget analysis

<a id="P020"></a>

The one-way GEO propagation delay is ~270-285ms and the bundling period is 80/160ms. These are fixed system properties that codec design can reduce. The additional end-to-end delay of 80ms look-ahead keeps the mouth-to-ear delay in a range of conversational voice service.

<a id="P021"></a>

It is clear that 400ms limit (shown in [5] as delay limit) is already overcomed in ULBC by propagation + bundling time (285+160=445ms), so the impact of codec look-ahead is small compared to what is gained in quality.

<a id="P022"></a>

According to [4] and [5] delay 150-400ms is still acceptable, so extra 80ms looks like miserable increase of total delay.

<a id="P023"></a>

By contrast, the quality gains from look-ahead will help ULBC to be NWT AMR-WB @ 12.65 at 1.0/1.4 kbps.

<a id="P024"></a>

## 2.3 Proposed constraint

<a id="P025"></a>

The codec delay shall not exceed the bundling time + 80 ms, where the 80 ms covers look-ahead and any other algorithmic delays beyond frame buffering (resampling, decoder post-processing), following the EVS-4 definition of algorithmic delay (frame-size buffering delay plus delays inherent in the codec algorithm; processing runtime and channel delays excluded).

<a id="P026"></a>

The constraint is independent of the bundling period: bundling is a transport/packetization concept outside the codec, while algorithmic delay belongs to codec.

<a id="P027"></a>

## 3 Proposals

<a id="P028"></a>

Proposal 1: In ULBC-4, agree the algorithmic delay constraint: the algorithmic codec delay shall not exceed the bundling time + 80 ms (look-ahead, resampling and decoder post-processing included; processing runtime and channel delays excluded, following the EVS-4 definition) and keep the additional delay independent of the bundling period constraint

<a id="P029"></a>

Based on Proposal 1, the Algorithmic codec delay row of ULBC-4 is proposed to be updated as follows (new text underlined, deleted text in strikethrough):

<a id="T030"></a>

<a id="T030-R01"></a>
**T030-R01**

- <a id="T030-R01-C01"></a>列 1: Algorithmic codec delay
- <a id="T030-R01-C02"></a>列 2: ~~[~~The algorithmic codec delay shall not exceed the bundling time + x ms.~~<br>- x=0 to 5ms (1621)~~<br>- x<=80ms ~~(1547)~~<br>~~- x=EVS range (email)~~~~<br>]~~
- <a id="T030-R01-C03"></a>列 3: Editor's note: the value of x is FFS. One-way GEO propagation is ~270 ms; the algorithmic codec delay and the bundling period are the controllable codec-layer contributions.<br>The algorithmic codec delay shall not exceed the bundling time + 80ms.<br>Additional delay is independent of the bundling period

<a id="P032"></a>

## 4 References

<a id="P033"></a>

[1] S4-261739, [ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.0

<a id="P034"></a>

[2] A. Défossez, J. Copet, A. Synnaeve, Y. Adi, "High Fidelity Neural Audio Compression", arXiv:2210.13438

<a id="P035"></a>

[3] X.-H. Jiang, Y. Ai, R.-C. Zheng, Z.-H. Ling, "A Streamable Neural Audio Codec with Residual Scalar-Vector Quantization for Real-Time Communication", IEEE SPL 2025, arXiv:2504.06561

<a id="P036"></a>

[4] Daniel Noworatzky "Employing VoIP over satellite links", Employing VoIP over satellite links

<a id="P037"></a>

[5] ITU G.114: One-way transmission time
