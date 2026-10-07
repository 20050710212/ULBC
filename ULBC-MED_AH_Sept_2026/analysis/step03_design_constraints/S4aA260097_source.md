# S4aA260097 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260097_[ULBC-MED] On perspective of DTX.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Meeting#137ad    S4aA260097

<a id="P001"></a>

Shanghai, P.R.China, 28-30 September 2026

<a id="P003"></a>

Source:    vivo Mobile Communication Co.,Ltd

<a id="P004"></a>

Title:    [ULBC-MED] On perspective of DTX

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

The ULBC-MED work item description SP-260696 [1] lists "Supporting DTX/CNG" under objective 1. At SA4#137-e, the design constraints permanent document ULBC-4 v0.2.1 (S4-261847 [2]) agreed the DTX/CNG framework:

<a id="T011"></a>

<a id="T011-R01"></a>
**T011-R01**

- <a id="T011-R01-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T011-R01-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).
- <a id="T011-R01-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.

<a id="P013"></a>

This contribution aims to complete the DTX/CNG design constraint.

<a id="P014"></a>

## 2    Discussion

<a id="P015"></a>

## 2.1    SID/DTX interval

<a id="P016"></a>

In AMR the SID/DTX interval is fixed at 8 frames, i.e. 160 ms [4]; AMR-WB followed the AMR design [3][4]. In EVS the design constraints only set a maximum, at most one SID update per 8 frames [5]; the specification then allowed default 8, fixed 3–100 and adaptive 8–50 frames [6].

<a id="P017"></a>

ULBC has two length units: the codec frame and the bundling period [2]. The bundling period is a transport unit chosen to reduce the protocol overhead; SID generation happens per codec frame at the encoder, so the SID interval should be defined in frames, with 8 frames as a fixed value (AMR/AMR-WB) or as the maximum update rate (EVS).

<a id="P018"></a>

With the three frame lengths on the table, 20, 40 and 80 ms, 8 frames correspond to 160, 320 and 640 ms. 320 ms is the value to aim at: it is a multiple of both bundling periods (4 × 80 ms, 2 × 160 ms), so a SID always falls on an SPS occasion and the occasions in between are skipped; it equals 8 frames of 40 ms (16 × 20 ms, 4 × 80 ms); and, as shown in the Annex, it skips 71 % of the inactive occasions with 80 ms bundling and 40 % with 160 ms, whereas 160 ms gives little or no saving. A 320 ms SID interval is therefore proposed as the reference, independent of the frame length finally selected.

<a id="P019"></a>

Proposal#1: Follow AMR/AMR-WB or EVS mechanism: SID update interval at fixed or most 320ms.

<a id="P020"></a>

## 2.2    SID frame size

<a id="P021"></a>

AMR and AMR-WB use a 35-bit SID, EVS a 48-bit SID, all on 20 ms frames [4][6]. EVS-4 did not fix the size either; it only required the SID not to exceed 56 bits gross, well below the smallest speech frame of 144 bits at 7.2 kbps [5]. The principle in both generations is that a SID is never larger than a speech frame, so a SID packet fits wherever a speech packet fits and needs no separate transport handling.

<a id="P022"></a>

For ULBC the same principle can be kept without fixing a number. The reference is the speech payload of the operating point in use, i.e. bit rate × bundling period [2]. A SID payload not exceeding this size reuses the speech transport block of the same operating point; the actual SID size is left to the candidate codecs.

<a id="P023"></a>

Proposal#2: SID payload not exceeding the speech payload of the operating point in use (bit rate × bundling period).

<a id="P024"></a>

## 2.3    Hangover and AFR

<a id="P025"></a>

Two different mechanisms are called “hangover”:

<a id="P026"></a>

VAD hangover: Part of the VAD. It extends the speech decision after speech ends to avoid clipping low-energy speech tails. It is adaptive in both AMR-WB [13] and EVS [6].

<a id="P027"></a>

DTX hangover: Part of the DTX handler. After VAD becomes inactive, the encoder sends a few additional speech frames so the decoder can derive initial comfort-noise parameters: fixed 7 frames in AMR and AMR-WB [4], adaptive in EVS [6].

<a id="P028"></a>

Neither hangover was ever a design constraint: neither WB-4 nor EVS-4 constrained either of them [3][5]. What bounds them is the Active Frame Ratio, since frames sent during either hangover are counted as active: EVS-3 required e.g. AFR(EVS) < AFR(AMR-WB) + 1 [7].

<a id="P029"></a>

ULBC-3 already carries the same requirement, in brackets: AFR(ULBC) < AFR(AMR-WB) + 1 % [10] or AFR(ULBC-MED) < AFR(EVS) + 1 [9], with a bundle counted as active if any frame in it is active [8]. Per-bundle counting quantises the AFR cost of any hangover to the bundle length – one extra 80 ms (160 ms) bundle costs as much AFR as four (eight) EVS frames – so the AFR requirement already penalises hangover more strongly than in EVS. Whether a DTX hangover is needed at all depends on the SID design, and ULBC-4 should leave that choice to the candidate codecs.

<a id="P030"></a>

Proposal#3: No constraint on VAD hangover or DTX hangover in ULBC-4; DTX performance is evaluated through the AFR requirement in ULBC-3.

<a id="P031"></a>

## 3    Proposal

<a id="P032"></a>

Based on Proposals 1 to 3, the DTX/CNG row of ULBC-4 is proposed to be updated as follows (new text underlined, deleted text in strikethrough):

<a id="T033"></a>

<a id="T033-R01"></a>
**T033-R01**

- <a id="T033-R01-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T033-R01-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG). It shall be possible to operate the codec with DTX on or DTX off with all operating points.<br>SID update frames shall be sent with a frequency not exceeding, or fixed at, once per 320 ms (i.e. 8 frames of 40 ms).<br>The SID payload shall not exceed the speech payload of the operating point in use (bit rate × bundling period).
- <a id="T033-R01-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>~~Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.~~

<a id="P035"></a>

## 4    References

<a id="P036"></a>

[1]    SP-260696, "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", SA WG4, TSG SA#112, June 2026.

<a id="P037"></a>

[2]    S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4)", v0.2.1, Fraunhofer IIS (Interim ULBC-4 Editor), SA4#137-e, August 2026.

<a id="P038"></a>

[3]    S4-000087 (Tdoc S4/SMG11 87/00), "Permanent project document WB-4: Design Constraints, v.1.0", joint TSG-S4#9 – SMG11#14, January 2000.

<a id="P039"></a>

[4]    3GPP TS 26.093, "AMR speech codec; Source controlled rate operation"; 3GPP TS 26.193, "AMR-WB speech codec; Source controlled rate operation".

<a id="P040"></a>

[5]    S4-130778, "EVS Permanent Document #4 (EVS-4): EVS design constraints", v1.2, SA4#74, July 2013.

<a id="P041"></a>

[6]    3GPP TS 26.445, "Codec for Enhanced Voice Services (EVS); Detailed algorithmic description".

<a id="P042"></a>

[7]    S4-130522, "EVS Permanent Document #3 (EVS-3): EVS performance requirements", draft v1.4, SA4#73, April 2013.

<a id="P043"></a>

[8]    S4-261771, "[ULBC-MED] ULBC Performance requirements (ULBC-3)", v0.1.0, ULBC-3 Editor, SA4#137-e, August 2026.

<a id="P044"></a>

[9]    S4-261723 (revision of S4-261557), "[ULBC-MED] Active Frame Rate", Huawei, SA4#137-e, August 2026.

<a id="P045"></a>

[10]    S4-261641, "Dolby Proposal on ULBC performance requirements", Dolby Laboratories, SA4#137-e, August 2026.

<a id="P046"></a>

[11]    3GPP TR 26.940 V20.0.0, "Study on Ultra Low Bitrate Speech Codec".

<a id="P047"></a>

[12]    S4-261716, "[ULBC-MED] On RTP Payload Format for ULBC - Architecture and Three-Mode Adaptive Framework", Tencent, SA4#137-e, August 2026.

<a id="P048"></a>

[13]    3GPP TS 26.094, "AMR speech codec; Voice Activity Detector (VAD)"; 3GPP TS 26.194, "AMR-WB speech codec; Voice Activity Detector (VAD)".

<a id="P049"></a>

Annex-1:    Example of DTX with 80ms bundling

<a id="P050"></a>

The figure shows one second of ULBC uplink at 1.4 kbps with 40 ms frames and 80 ms bundling, one bundle per SPS occasion, with RoHC. The three rows use a SID interval of 80, 160 and 320 ms. Occasions without data are skipped (RAN2 SPS with skip), so the longer the SID interval, the more occasions are skipped: 0 %, 43 % and 71 % of the inactive occasions, i.e. 209, 170 and 140 bytes in this second. The SID bundle stays smaller than the speech bundle and uses the same transport block.

<a id="P052"></a>

Figure A.1: ULBC DTX with SPS skip and RoHC, SID interval 80 / 160 / 320 ms

<a id="P053"></a>

Annex-2:    Example of DTX with 160ms bundling

<a id="P054"></a>

Figure A.2 shows the same for 1.0 kbps with 160 ms bundling over 1.28 s, with a SID interval of 160 and 320 ms: 0 % and 40 % of the inactive occasions are skipped, i.e. 155 and 129 bytes. The saving per skipped occasion is larger than with 80 ms bundling because each occasion carries a bigger speech bundle, while the SID bundle stays the same size.

<a id="P056"></a>

Figure A.2: ULBC DTX with SPS skip and RoHC, 1.0 kbps, 160 ms bundling, SID interval 160 / 320 ms
