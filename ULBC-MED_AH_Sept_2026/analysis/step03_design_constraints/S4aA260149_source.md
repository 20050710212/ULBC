# S4aA260149 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260149-ULBC_Bandwidth_Samplingrate.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Fraunhofer IIS

<a id="P001"></a>

Title:    On Audio Bandwidth and Sampling Rates

<a id="P002"></a>

Document for:    Agreement

<a id="P003"></a>

Agenda Item:    4.4

<a id="P005"></a>

## 1. Introduction

<a id="P006"></a>

At the 3GPP SA4#137-e meeting, various contributions ([1][2][3][4][5][6][7][8][9][10]) have addressed the design constraint on audio bandwidth and sampling rates for the ULBC codec. The different views have been summarized in [11].

<a id="P007"></a>

This contribution aims to discuss the arguments brought forward in these documents and summarizes the Fraunhofer position on this question.

<a id="P008"></a>

## 2. Proposal

<a id="P009"></a>

It is proposed that ULBC accepts 16 kHz and 32 kHz input and output sample rate. The ULBC audio bandwidth should be at least wideband. This broad definition allows all kind of test configurations for qualification or selection, meaning either dedicated WB/SWB tests or mixed bandwidth tests.

<a id="T010"></a>

<a id="T010-R01"></a>
**T010-R01**

- <a id="T010-R01-C01"></a>列 1: Parameter
- <a id="T010-R01-C02"></a>列 2: Design constraint
- <a id="T010-R01-C03"></a>列 3: Note

<a id="T010-R02"></a>
**T010-R02**

- <a id="T010-R02-C01"></a>列 1: Sampling Frequency
- <a id="T010-R02-C02"></a>列 2: The ULBC codec shall support PCM audio at the encoder input and at the decoder output at a sampling rate of <br><br>- 16kHz <br>- 32kHz <br>.
- <a id="T010-R02-C03"></a>列 3: 

<a id="T010-R03"></a>
**T010-R03**

- <a id="T010-R03-C01"></a>列 1: Audio bandwidth
- <a id="T010-R03-C02"></a>列 2: The ULBC codec shall achieve at least wideband (WB) audio.
- <a id="T010-R03-C03"></a>列 3: Agreed WID objective [2].<br><br><br><br>Bandwidth of the audio material to be detailed in ULBC-8a (1562, 1513)

<a id="P012"></a>

## 3. Discussion

<a id="P013"></a>

## 3.1 Sampling Frequency

<a id="P014"></a>

It is proposed for the ULBC codec to natively support sampling frequencies of 16 and 32 kHz. Precedence for the support of multiple audio sampling frequencies is already established since EVS. From codec perspective, the overhead for the support of two input/output sampling frequencies can be considered very low, and this facilitates the deployment of the codec in environments, whether audio processing at either 16 or 32 kHz is available.

<a id="P016"></a>

According to our insights, UEs also typically support various sampling rates up to 48 kHz – however, there might be limitations for telephony applications especially due to limitations in the acoustic frontend or in the wireless audio link, which might be restricted to 16 or 32 kHz audio sampling rate only on certain devices.

<a id="P017"></a>

For this reason, we consider it as the safest approach if ULBC could support both sampling rates.

<a id="P018"></a>

## 3.2 Audio Bandwidth

<a id="P019"></a>

It is proposed that the ULBC codec shall support at least WB audio. For 32 kHz sampling rate, a higher audio bandwidth may be supported.

<a id="P020"></a>

Given the proposed support for 16 and 32 kHz sampling frequencies, the source doesn’t see the need to negotiate the bandwidth via SDP. As long as the bitstream is self-contained in this aspect, the encoder could simply encode the max. bandwidth supported by the device. The same concept applies to the decoder.

<a id="P021"></a>

In the past concerns were raised due to missing clarity on the bandwidth for such a scenario. The source however has to state that this is also the case with current codecs as soon as wireless audio links come into play. Still many devices support only connections using Bluetooth HFP (hands-free profile), where even in the latest version 1.9 SWB is just an optional feature, and no TMAP (Telephony and Media Audio Profile) for low energy audio which limits the audio bandwidth for the wireless link to either NB or WB audio – for such cases also today, the negotiated bandwidth may still limited by the max. supported bandwidth of the additional wireless equipment. Thus, the source doesn’t see a significant degradation compared to today’s situation.

<a id="P022"></a>

## 4. Conclusion

<a id="P023"></a>

It is proposed to agree on the proposal made in Clause 2.

<a id="P025"></a>

References

<a id="P027"></a>

S4-261513 - [ULBC-MED] On ULBC wideband native operating point and evaluation focus

<a id="P029"></a>

S4-261517 - [ULBC-MED] Spreadtrum_views_on_ULBC_sampling_rate

<a id="P031"></a>

S4-261518 - [ULBC-MED] Inclusion of 16 kHz input/output testing for ULBC

<a id="P033"></a>

S4-261546 - [ULBC-MED] On ULBC design constraints

<a id="P035"></a>

S4-261562 - [ULBC-MED] On input/output sampling rate and audio bandwidth for the ULBC design constraints and qualification phase

<a id="P037"></a>

S4-261567 - [ULBC-MED]Sample rate of ULBC-MED

<a id="P039"></a>

S4-261586 - [ULBC-MED] On ULBC Design Constraints

<a id="P041"></a>

S4-261616 - [ULBC-MED] On ULBC audio bandwidth and sampling rate

<a id="P043"></a>

S4-261621 - [ULBC-MED] ULBC Design Constraints

<a id="P045"></a>

S4-261640 - Proposed ULBC-MED design constraints

<a id="P047"></a>

S4-261847 - [ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.1

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH    Tdoc S4aA260149<br>    Shanghai, China, September 28-30, 2026
