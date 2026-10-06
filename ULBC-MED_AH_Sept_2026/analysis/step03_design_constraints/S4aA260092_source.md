# S4aA26092 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260092 [ULBC-MED] On ULBC Audio Sampling Rate and Audio Frequency Bandwidth Design Constraints.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP SA4-(AH) Audio SWG on ULBC-MED    Tdoc S4aA260092

<a id="P001"></a>

Shanghai, China, 28 - 30 September 2026

<a id="P004"></a>

Source:    vivo Mobile Communication Co.

<a id="P005"></a>

Title:    [ULBC-MED] On ULBC Audio Sampling Rate and Audio Frequency Bandwidth Design Constraints

<a id="P006"></a>

Document for:    Discussion and Agreement

<a id="P007"></a>

Agenda item:    4.4

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

In current ULBC-4 Design constraints v0.2.1 [1] the input/output audio signal sampling rates and the audio frequency bandwidth design constraints are not yet agreed. The reason for this remains unresolved might be due to the fact that the sampling rate and the frequency bandwidth are tightly coupled, i.e., agreeing to the 16kHz sampling rate implies that the audio frequency bandwidth for the ULBC codec would be up to 8 kHz, while agreeing to 32kHz sampling rate means that 16kHz frequency band needs to be supported.

<a id="P011"></a>

Since it is explicitly requested in the WID [2] that ULBC should deliver quality “not worse than commercially deployed 3GPP WB services,…”, it is unquestionable that NWT WB quality is required for ULBC, but that does not prevent NWT SWB (or equivalent to SWB) be set as an objective and see if some candidates can deliver such better performances.

<a id="P012"></a>

## 2    Discussion

<a id="P013"></a>

The source is of the opinion that design constraints and quality requirement are two different aspects, reason why we have two dedicated Pdocs to document them. For example, while we can require that the codec must work with input/output audio signal at 32kHz sampling rate as a design constraint, we can leave the actual frequency bandwidth as a design choice for proponents, and rely on the subjective tests to determine which proponent delivers the best overall subjective voice quality.

<a id="P014"></a>

This arrangement will allow proponents to maximize performances of their designs based on their available technologies and knowhow, will also allow SA4 to select the best overall candidate amongst all proponents.

<a id="P015"></a>

In particular, for candidates supporting reduced bandwidths, DCR test methodology will allow listeners to factor in the impact as some sort of degradation, resulting in a fair and equitable competition frame work that truly favours candidate delivering the best user perceived voice quality.

<a id="P016"></a>

## 3    Proposed changes to ULBC-4 v0.2.1

<a id="P017"></a>

The following changes are proposed:

<a id="T019"></a>

<a id="T019-R01"></a>
**T019-R01**

- <a id="T019-R01-C01"></a>列 1: Parameter
- <a id="T019-R01-C02"></a>列 2: Design constraint
- <a id="T019-R01-C03"></a>列 3: Note

<a id="T019-R02"></a>
**T019-R02**

- <a id="T019-R02-C01"></a>列 1: Sampling Frequency
- <a id="T019-R02-C02"></a>列 2: The ULBC codec shall support PCM audio at the encoder input and at the decoder output at a sampling rate of 32kHz
- <a id="T019-R02-C03"></a>列 3: Editor's note: Competing proposals that ask for internal sampling rate being equal to input/output sampling rate (1567) vs. sampling-rate conversion being allowed but counted (1518).<br>Note: the idea is to disassociate the input/output sampling rates from the frequency bandwidth

<a id="T019-R03"></a>
**T019-R03**

- <a id="T019-R03-C01"></a>列 1: Audio bandwidth
- <a id="T019-R03-C02"></a>列 2: For input signals containing up to SWB audio the ULBC codec shall achieve at least wideband (WB or 8kHz frequency band) audio, and preferably up to super-wideband (SWB or 16kHz frequency band) audio, or anything in between.
- <a id="T019-R03-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: the sample rate (e.g. 16 kHz, or 32 kHz) and whether super-wideband or fullband is required or optional are FFS.<br>TR 26.940 [1] evaluated various bandwidths; WB solutions at ~1 kb/s matched AMR-WB 12.65 kb/s on clean speech.<br><br>Bandwidth of the audio material to be detailed in ULBC-8a (1562, 1513)<br>Note: the idea is to keep the actual frequency bandwidth a design choice and evaluate its impact as part of the qualification/selection tests

<a id="P020"></a>

## 4    References

<a id="P021"></a>

[1]    S4-261847: “[ULBC-MED] ULBC Design Constraints (ULBC-4)”, v0.2.1, May 2026

<a id="P022"></a>

[2]        SP-260696: "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", June 2026
