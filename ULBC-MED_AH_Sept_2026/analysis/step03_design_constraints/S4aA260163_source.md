# S4aA260163 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260163_SID_frames.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Ericsson LM

<a id="P001"></a>

Title:    ULBC SID frames

<a id="P002"></a>

Document for:    Discussion and Agreement

<a id="P003"></a>

Agenda Item:    4.4

<a id="P004"></a>

## 1    Introduction

<a id="P005"></a>

In accordance with TR 26.940, it has been agreed that ULBC shall provide a framework for discontinuous transmission (DTX) and comfort noise generation (CNG). This contribution brings some related questions for discussion.

<a id="P006"></a>

## 2    Discussion

<a id="P007"></a>

The draft design constraints for ULBC in ULBC-4 [1] capture the requirement of DTX support as follows:

<a id="T008"></a>

<a id="T008-R01"></a>
**T008-R01**

- <a id="T008-R01-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T008-R01-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).
- <a id="T008-R01-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.

<a id="P010"></a>

It is noted that the details of the DTX functionality are still to be defined, e.g. SID interval. Another aspect is the allowed SID packet size, which is not yet specified.

<a id="P011"></a>

Due to the nature of the semi-persistent scheduling, applicable to ULBC, it may be assumed that the active speech frame grant can also be used for SID frames as long as the SID frame packet size is equal or less than the active speech frame packets. In that case, there would not be any gain in reducing the SID packets further. This should however be clarified.

<a id="P012"></a>

Related discussions have taken place in RAN2, see e.g. RAN2#133 meeting report [2], and SA4 might want to get confirmation on potential assumptions from the RAN groups.

<a id="P013"></a>

## 3    Proposal

<a id="P014"></a>

It is proposed that the allowed SID packet size is discussed and that a requirement would be captured as an additional design constraint. Confirmation of potential assumptions might need confirmation by RAN, and it should be agreed how to proceed defining such design constraint for ULBC.

<a id="P015"></a>

## 4    References

<a id="P016"></a>

Tdoc S4-261847: ULBC Design Constraints (ULBC-4), v0.2.1

<a id="P017"></a>

Tdoc R2-2601402: Report of 3GPP TSG RAN WG2 meeting #133

**原文页眉：** Page 4<br>Draft prETS 300 ???: Month YYYY

**原文页眉：** 3GPP TSG-SA WG4 Audio SWG AH    S4aA260163<br>Shanghai, China, 28 – 30 September, 2026
