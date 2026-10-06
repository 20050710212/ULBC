# S4aA260153 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260153_ULBC_MED_On_SNRs_for_ULBC_noisy_speech_testing.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG Ad-hoc on ULBC-MED    S4aA260153

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Qualcomm Incorporated

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC noisy speech testing: SNRs for noisy speech testing

<a id="P005"></a>

Agenda item:    4.3

<a id="P006"></a>

Document for:    AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P011"></a>

During SA4#137-e meeting, the following general principle regarding SNRs for ULBC noisy speech testing was agreed and documented in the ULBC Performance requirements permanent document (ULBC-3) [1]:

<a id="P012"></a>

“For background noise types and levels, in qualification applies[sic] the principles outlined in Table 1.<br>
Table 1: Background noise types and levels for ULBC testing of noisy speech

<a id="T013"></a>

<a id="T013-R01"></a>
**T013-R01**

- <a id="T013-R01-C01"></a>列 1: Source Material
- <a id="T013-R01-C02"></a>列 2: Noise type
- <a id="T013-R01-C03"></a>列 3: SNRs
- <a id="T013-R01-C04"></a>列 4: Subjective test methodology

<a id="T013-R02"></a>
**T013-R02**

- <a id="T013-R02-C01"></a>列 1: Speech + Noise
- <a id="T013-R02-C02"></a>列 2: Stationary noise (car)
- <a id="T013-R02-C03"></a>列 3: 15 - 20 dB
- <a id="T013-R02-C04"></a>列 4: ITU-T P.800 DCR

<a id="T013-R03"></a>
**T013-R03**

- <a id="T013-R03-C01"></a>列 1: Speech + Noise
- <a id="T013-R03-C02"></a>列 2: Non-stationary noise (street, office)
- <a id="T013-R03-C03"></a>列 3: 20 - 25 dB
- <a id="T013-R03-C04"></a>列 4: ITU-T P.800 DCR

<a id="P014"></a>

“

<a id="P015"></a>

The above table provides general guidance on SNRs for noisy speech testing, specifying a range of possible SNRs values that could be chosen for testing. It does not specify the exact SNRs. In this contribution, we discuss and propose specific SNRs for noisy speech testing, for both stationary and non-stationary noise.

<a id="P017"></a>

## 2. Discussion

<a id="P019"></a>

It is expected that a front-end audio pipeline with noise suppression will be available on the UEs on which ULBC will be deployed/implemented. The inclusion of a front-end noise suppressor in a voice call front-end audio processing path is common practice. At the input to the speech codec, the SNR is expected to be at a level that matches the residual noise post the front-end noise suppressor, rather than the SNR at the input microphone. Speech codecs are typically tested at the SNR level expected at the input to the codec.

<a id="P020"></a>

EVS noisy speech testing was conducted at 15dB SNR for stationary and 20dB SNR for non-stationary noise [2]. Since the standardization of EVS, there have been major advancements in front-end noise suppression systems, yielding improved noise suppression performance and higher SNRs at the front-end noise suppressor output. Given these advancements, the SNR at the input to the speech codec is expected to be higher than the representative values used during EVS standardization. We, therefore, propose to fix the SNRs for ULBC noisy speech testing to the higher end of the ranges in the table above, namely 20dB for stationary and 25dB for non-stationary noise.

<a id="P022"></a>

## 3. Proposal.

<a id="P024"></a>

We propose the following change to the ULBC Performance requirements permanent document (ULBC-3) permanent document:

<a id="P026"></a>

Table 1: Background noise types and levels for ULBC testing of noisy speech

<a id="T027"></a>

<a id="T027-R01"></a>
**T027-R01**

- <a id="T027-R01-C01"></a>列 1: Source Material
- <a id="T027-R01-C02"></a>列 2: Noise type
- <a id="T027-R01-C03"></a>列 3: SNRs
- <a id="T027-R01-C04"></a>列 4: Subjective test methodology

<a id="T027-R02"></a>
**T027-R02**

- <a id="T027-R02-C01"></a>列 1: Speech + Noise
- <a id="T027-R02-C02"></a>列 2: Stationary noise (car)
- <a id="T027-R02-C03"></a>列 3: 20 dB
- <a id="T027-R02-C04"></a>列 4: ITU-T P.800 DCR

<a id="T027-R03"></a>
**T027-R03**

- <a id="T027-R03-C01"></a>列 1: Speech + Noise
- <a id="T027-R03-C02"></a>列 2: Non-stationary noise (street, office)
- <a id="T027-R03-C03"></a>列 3: 25 dB
- <a id="T027-R03-C04"></a>列 4: ITU-T P.800 DCR

<a id="P028"></a>

Any references to SNRs in the performance requirement tables in ULBC-3 to be changed accordingly.

<a id="P029"></a>

## 4. References

<a id="P031"></a>

[1] 3GPP S4-261771, "[ULBC-MED] ULBC Performance requirements (ULBC-3)", v0.1.0, SA4#137-e, August 2026

<a id="P032"></a>

[2] 3GPP S4-130522,", v1.4, SA4#73, April 2013
