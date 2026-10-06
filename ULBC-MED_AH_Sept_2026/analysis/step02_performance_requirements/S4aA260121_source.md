# S4aA260121 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260121_ULBC_Performance_req.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

SA4-(AH) Audio SWG on ULBC-MED                                             Tdoc S4aA260121

<a id="P001"></a>

## 28 - 30 September 2026

<a id="P004"></a>

Source:    Dolby Laboratories Inc.

<a id="P005"></a>

Title:    [ULBC-MED] On ULBC Performance requirements and design constraints

<a id="P006"></a>

Document for:    Discussion and Agreement

<a id="P007"></a>

Agenda item:    4.3

<a id="P008"></a>

Work Item:    ULBC-MED

<a id="P011"></a>

## 1    Introduction

<a id="P012"></a>

ULBC WID [1] sets the performance requirement for ULBC to be NWT AMRWB 12.65 kbps. There have been in-depth discussions around the bitrates to be supported for ULBC and the performance requirement at those bitrates. In [2], the design constraint to support two bitrates 1 kbps and 1.4 kbps was agreed however, the question of performance requirements at each of these two bitrates remains. During previous meetings, following proposals were made:

<a id="P013"></a>

Clean speech

<a id="P014"></a>

ULBC 1kbps requirement

<a id="P015"></a>

NWT AMR WB 12.65 kbps [3], [7], [8]

<a id="P016"></a>

NWT AMR WB 8.85 kbps [4]

<a id="P017"></a>

ULBC 1.4 kbps requirement

<a id="P018"></a>

NWT AMR WB 15.85 kbps [3]

<a id="P019"></a>

NWT AMR WB 12.65 kbps [4], [7]

<a id="P020"></a>

NWT EVS WB 13.2 kbps [8]

<a id="P021"></a>

Noisy speech

<a id="P022"></a>

ULBC 1kbps requirement

<a id="P023"></a>

NWT AMR WB 8.85 kbps [3], [4]

<a id="P024"></a>

NWT AMR WB 12.65 kbps [7], [8]

<a id="P025"></a>

ULBC 1.4 kbps requirement

<a id="P026"></a>

NWT AMR WB 12.65 kbps [3], [4], [7]

<a id="P027"></a>

NWT EVS WB 13.2 kbps [8]

<a id="P030"></a>

The AMRWB performance characterization TR [5] provides a detailed report on AMRWB performance at each bitrate. While AMR WB 12.65 kbps provides significant improvement over 8.85 kbps, the improvement with 14.25 and 15.85 kbps over 12.65 kbps is marginal. The quality difference between AMRWB 15.85 kbps and 12.65 kbps may be even less when subjected to ULBC loss patterns (with bulk 80ms or 160ms loss). On the other hand, while EVS 13.2 kbps WB should offer substantial quality benefit over AMR WB 12.65 kbps, it is very optimistic requirement and there is no evidence that such a requirement can be fulfilled. For voice over GEO scenario, the quality degradations due to packet loss can assumed to be the most substantial challenge. Hence, the source is of the opinion that quality requirements for ULBC 1.4 kbps shall be set in a way that they address a quality dimension where the largest benefit can be expected when moving from 1.0 kbps to 1.4 kbps. More specifically, the source is of the opinion that the performance requirements should be set such that there is a substantial quality benefit over 1 kbps for at least some of the noisy channel conditions, which are envisioned for ULBC primary use case (Voice call over GEO satellite).

<a id="P032"></a>

Noisy channel conditions

<a id="P033"></a>

Performance under noisy channel conditions is one of the major challenges for ULBC with 80ms and 160 ms bundling period. While the AI based codecs can potentially deliver a better packet loss concealment performance, a loss of 80ms of 160ms or multiples thereof in case of burst errors is still very substantial. Depending on the loss pattern, it can cause serious issues w.r.t speech intelligibility especially if the loss happens at the onset of speech. At 1.4 kbps, solutions leveraging on the extra bitrate over 1.0 kbps may be considered to make the codec more robust to noisy channel conditions, the performance requirements should be set accordingly (e.g. BT AMR-WB 12.65 kbps). The proposal is captured in Table 1 of clause 2.1. Moreover, the source is of the opinion that the design constraint for channel robustness should be set such that the ULBC decoder has the possibility to look one bundle into the future (assuming availability of this bundle in jitter buffer). The proposal is captured in Table 3 of clause 2.2.

<a id="P036"></a>

Performance requirements with noisy speech

<a id="P037"></a>

In [6], for qualification phase, it was proposed and agreed to have car, street and office noise types for noisy speech testing. These noise types have been used for the testing of previously standardized 3GPP speech codecs. For ULBC, given that the codec is envisioned to be an AI based codec, it is very important to know how the codec will perform when subjected to some other noise types, for e.g. with tonal noises like emergency sirens and the noise types that will be more likely encountered when there is no terrestrial network coverage like forest noise including birds chirping, wind noise. Moreover, while speech with music background is a less likely scenario for voice over GEO scenario, it should be ensured that ULBC is robust to such backgrounds and still preserves speech intelligibility. Higher demands should apply when operating at 1.4 kbps. While it is very important to ensure that ULBC preserves speech quality under noisy conditions with variety of noise types, the source also understands the need for setting realistic performance requirements and ensuring that noise levels are not being supressed beyond the limits that were set during the standardization of previous 3GPP codecs like EVS. The proposal is captured in clause 2.1.1 and 2.1.2.

<a id="P039"></a>

## 2    Proposal

<a id="P040"></a>

## 2.1. On performance requirements

<a id="P041"></a>

Table 1: ULBC requirements

<a id="T042"></a>

<a id="T042-R01"></a>
**T042-R01**

- <a id="T042-R01-C01"></a>列 1: Conditions
- <a id="T042-R01-C02"></a>列 2: bitrate
- <a id="T042-R01-C03"></a>列 3: requirements
- <a id="T042-R01-C04"></a>列 4: DTX

<a id="T042-R02"></a>
**T042-R02**

- <a id="T042-R02-C01"></a>列 1: Clean speech 0% BLER
- <a id="T042-R02-C02"></a>列 2: 1 kbps
- <a id="T042-R02-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R02-C04"></a>列 4: On/Off†

<a id="T042-R03"></a>
**T042-R03**

- <a id="T042-R03-C01"></a>列 1: Clean speech, noisy channel
- <a id="T042-R03-C02"></a>列 2: 1 kbps
- <a id="T042-R03-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R03-C04"></a>列 4: On/Off†

<a id="T042-R04"></a>
**T042-R04**

- <a id="T042-R04-C01"></a>列 1: Clean speech 0% BLER
- <a id="T042-R04-C02"></a>列 2: 1.4 kbps
- <a id="T042-R04-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R04-C04"></a>列 4: On/Off†

<a id="T042-R05"></a>
**T042-R05**

- <a id="T042-R05-C01"></a>列 1: Clean speech, noisy channel with < 6% BLER
- <a id="T042-R05-C02"></a>列 2: 1.4 kbps
- <a id="T042-R05-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R05-C04"></a>列 4: On/Off†

<a id="T042-R06"></a>
**T042-R06**

- <a id="T042-R06-C01"></a>列 1: Clean speech, noisy channel with >= 6% BLER
- <a id="T042-R06-C02"></a>列 2: 1.4 kbps
- <a id="T042-R06-C03"></a>列 3: BT AMRWB 12.65 kbps
- <a id="T042-R06-C04"></a>列 4: On/Off†

<a id="T042-R07"></a>
**T042-R07**

- <a id="T042-R07-C01"></a>列 1: Noisy speech, 0% BLER
- <a id="T042-R07-C02"></a>列 2: 1 kbps
- <a id="T042-R07-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R07-C04"></a>列 4: On/Off†

<a id="T042-R08"></a>
**T042-R08**

- <a id="T042-R08-C01"></a>列 1: Noisy speech, Noisy channel
- <a id="T042-R08-C02"></a>列 2: 1 kbps
- <a id="T042-R08-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R08-C04"></a>列 4: On/Off†

<a id="T042-R09"></a>
**T042-R09**

- <a id="T042-R09-C01"></a>列 1: Noisy speech, 0% BLER
- <a id="T042-R09-C02"></a>列 2: 1.4 kbps
- <a id="T042-R09-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R09-C04"></a>列 4: On/Off†

<a id="T042-R10"></a>
**T042-R10**

- <a id="T042-R10-C01"></a>列 1: Noisy speech, noisy channel with < 6% BLER
- <a id="T042-R10-C02"></a>列 2: 1.4 kbps
- <a id="T042-R10-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T042-R10-C04"></a>列 4: On/Off†

<a id="T042-R11"></a>
**T042-R11**

- <a id="T042-R11-C01"></a>列 1: Noisy speech, noisy channel with >= 6% BLER
- <a id="T042-R11-C02"></a>列 2: 1.4 kbps
- <a id="T042-R11-C03"></a>列 3: BT AMRWB 12.65 kbps
- <a id="T042-R11-C04"></a>列 4: On/Off†

<a id="P043"></a>

Notes:

<a id="P044"></a>

<sup>† </sup>Reference codecs with DTX on [7]

<a id="P045"></a>

Source expects selection and qualification testing to be done with DTX On mode only [9]

<a id="P046"></a>

Tandeming cases, including, self-tandeming of ULBC should be considered during characterization.

<a id="P048"></a>

## 2.1.1. Noise types

<a id="P049"></a>

The following proposal is made in combination with the proposal in clause 2.1.2 to ensure that noise levels are not getting supressed outside a certain range.

<a id="P050"></a>

Table 2: Noise types for noisy speech tests and requirements

<a id="T051"></a>

<a id="T051-R01"></a>
**T051-R01**

- <a id="T051-R01-C01"></a>列 1: Bitrate
- <a id="T051-R01-C02"></a>列 2: Noise type
- <a id="T051-R01-C03"></a>列 3: Performance requirements
- <a id="T051-R01-C04"></a>列 4: Testing methodology

<a id="T051-R02"></a>
**T051-R02**

- <a id="T051-R02-C01"></a>列 1: 1 kbps
- <a id="T051-R02-C02"></a>列 2: Car, street, office, emergency sirens, forest noise, general audio and music
- <a id="T051-R02-C03"></a>列 3: As mentioned in Table 1 above
- <a id="T051-R02-C04"></a>列 4: P800 ACR

<a id="T051-R03"></a>
**T051-R03**

- <a id="T051-R03-C01"></a>列 1: 1.4 kbps
- <a id="T051-R03-C02"></a>列 2: Car, street, office, emergency sirens, forest noise, general audio and music
- <a id="T051-R03-C03"></a>列 3: As mentioned in Table 1 above
- <a id="T051-R03-C04"></a>列 4: P800 ACR

<a id="P053"></a>

## 2.1.2.  ULBC Objective Performance Requirements on background noise handling

<a id="P054"></a>

The following requirements were proposed in [7] during previous meeting as well.

<a id="P055"></a>

For clean speech (-26 dBov) the following requirements apply:

<a id="P056"></a>

For DTX turned off, the background noise level during inactive regions of the CuT shall be attenuated by no more than 6 dB, at the decoder output, compared to the background noise level during inactive regions of the input signal.

<a id="P057"></a>

For DTX turned on, the background noise level during inactive regions of the CuT shall be attenuated by no more than 12 dB, at the decoder output, as compared to the background noise level during inactive regions of the input signal.

<a id="P058"></a>

The measurement method for attenuation in inactive regions shall ignore very low energy frames of (recording) background noise in clean speech.

<a id="P060"></a>

For noisy speech (-26 dBov) and each tested noise type the following requirements apply:

<a id="P061"></a>

For DTX turned off, the background noise level during inactive regions of the CuT shall be attenuated by no more than 4 dB, at the decoder output, compared to the background noise level during inactive regions of the input signal.

<a id="P062"></a>

For DTX turned on, the background noise level during inactive regions of the CuT shall be attenuated by no more than 12 dB, at the decoder output, as compared to the background noise level during inactive regions of the input signal.

<a id="P064"></a>

## 2.2. On design constraints

<a id="P065"></a>

Table 3: ULBC codec design constraints

<a id="T066"></a>

<a id="T066-R01"></a>
**T066-R01**

- <a id="T066-R01-C01"></a>列 1: Parameter
- <a id="T066-R01-C02"></a>列 2: Design constraint
- <a id="T066-R01-C03"></a>列 3: Note

<a id="T066-R02"></a>
**T066-R02**

- <a id="T066-R02-C01"></a>列 1: Channel robustness
- <a id="T066-R02-C02"></a>列 2: The ULBC decoder shall have the possibility to look one bundle into the future assuming availability of this bundle in jitter buffer
- <a id="T066-R02-C03"></a>列 3: Editor's note: Such a functionality can be tested with a simple sequence number mechanism, no need for fully functional JBM.

<a id="P068"></a>

## 3    References

<a id="P069"></a>

[1]    SP-260696: "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", June 2026.

<a id="P070"></a>

[2]    3GPP TDOC S4-261739: “ULBC Design Constraints (ULBC-4)”

<a id="P071"></a>

[3]    3GPP TDOC S4-261552: “On Performance Requirements for ULBC-MED”

<a id="P072"></a>

[4]    3GPP TDOC S4-261566: “On ULBC performance requirements”

<a id="P073"></a>

[5]        3GPP TR 26976: “Performance characterization of the Adaptive Multi-Rate Wideband (AMR-WB) speech codec”

<a id="P074"></a>

[6]     S4-261595: “Backgrounds for Noisy Speech Testing”

<a id="P075"></a>

[7]    S4-261641: “Dolby Proposal on ULBC performance requirements”

<a id="P076"></a>

[8]    S4-261620: “ULBC-3 Performance Requirements”

<a id="P077"></a>

[9]    S4aA260122: “On DTX requirements”
