# S4aA260117 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260117[ULBC-MED] on ULBC DTX CNG.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG (AH) Meeting    S4-260117

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Huawei Technologies Co., Ltd

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC DTX/CNG

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

## 1 Introduction

<a id="P010"></a>

The VAD/DTX/CNG framework is an agreed ULBC-4 design constraint, based on RAN2 operation with SPS. However, neither the size of the SID (Silence Insertion Descriptor) frames nor their update frequency is constrained in ULBC-4 v0.2.0, but the DTX effectiveness is directly depend on them. This contribution analyses where the DTX gains actually come from, and concludes that the SID update frequency - not the SID frame size - is the controlling parameter for bit budget and power savings. Based on this analysis, we propose a constrain, of how often SID should be taken.

<a id="P011"></a>

## 2 Discussion

<a id="P012"></a>

## 2.1 The EVS precedent

<a id="P013"></a>

EVS-4 constrains [4] the SID frame not exceeding 56 bits per frame and requires to send SID frames not frequently than once per 8 frames; the AMR-WB interoperable mode uses a 40-bit SID.

<a id="P014"></a>

The SID constraints are objectively verifiable from the candidate executable and should be part of the design-constraint.

<a id="P015"></a>

## 2.2 Under fixed-TBS SPS, DTX cannot benefit from reducing SID size

<a id="P016"></a>

The transport model of IMS voice over NB-IoT NTN with GEO is semi-persistent scheduling with a transport block size fixed for the call. The TBS values from the RAN simulations [2] in TR 26.940 [3] are:

<a id="P017"></a>

TBS 144 bits (18 bytes) at 1.0 kbps / 80 ms: 3 B RTP header + 10 B codec payload (the 1.0 kbps gross rate) + 5 B AS overhead (PDCP 1 + RLC 1 + MAC 3);

<a id="P018"></a>

TBS 176 bits (22 bytes) at 1.4 kbps / 80 ms: 3 B + 14 B + 5 B;

<a id="P019"></a>

TBS 224 bits (28 bytes) at 1.0 kbps / 160 ms: 3 B + 20 B + 5 B;

<a id="P020"></a>

TBS 288 bits (36 bytes) at 1.4 kbps / 160 ms: 3 B + 28 B + 5 B.

<a id="P021"></a>

As a result:

<a id="P022"></a>

A smaller SID frame does NOT save any bit budget: a 4-byte SID occupies exactly the same transport block (and the same transmission power) as a 10-byte speech frame;

<a id="P023"></a>

The radio-resource and power savings of DTX come from the frames that are NOT used: during NO_DATA periods the UE skips the SPS transmissions (per the RAN2 report [5] the UE antenna is not used during DTX no-data periods), which reduces UE power consumption (approximately 275 mW at 31 dBm antenna power, prolonging GEO voice calls by ~27%, and up to ~50% at 34 dBm;

<a id="P024"></a>

During silent periods with SID updates, the SID update FREQUENCY (and not SID size) control DTX effectiveness: at a maximum of one SID_UPDATE per 8 frames, the usage during silence is 1/8 of the active-speech usage. The SID update frequency should be the controlling parameter for the DTX gains.

<a id="P025"></a>

Note: frame here has the same speech length as bundling time.

<a id="P027"></a>

## 3 Proposals

<a id="P028"></a>

Proposal 1: In ULBC-4, add a DTX/CNG constraint with the SID update frequency as the primary parameter: SID_UPDATE frames shall be sent not frequently than one SID_UPDATE per [640] ms; NO_DATA frames are not transmitted, and the decoder maintains comfort noise from its CNG between updates.

<a id="P029"></a>

Proposal 2: In ULBC-4, add the secondary SID size constraint: the SID payload (including any payload-format header) shall fit within the codec payload budget of the respective operating point (10 B at 1.0 kbps / 80 ms; 14 B at 1.4 kbps / 80 ms; 20 B at 1.0 kbps / 160 ms; 28 B at 1.4 kbps / 160 ms).

<a id="P030"></a>

Based on Proposals 1 & 2, the Sampling Frequency row of ULBC-4 is proposed to be updated as follows (new text underlined, deleted text in strikethrough):

<a id="T031"></a>

<a id="T031-R01"></a>
**T031-R01**

- <a id="T031-R01-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T031-R01-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).<br>SID_UPDATE frames shall be sent not frequently than one SID_UPDATE per [640] ms; NO_DATA frames are not transmitted;<br>The SID payload (including any payload-format header) shall fit within the codec payload budget of the respective operating point (10 B at 1.0 kbps / 80 ms; 14 B at 1.4 kbps / 80 ms; 20 B at 1.0 kbps / 160 ms; 28 B at 1.4 kbps / 160 ms)
- <a id="T031-R01-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.

<a id="P034"></a>

Proposal 3: Include the SID update frequency and frame sizes in the design-constraint compliance report and in the objective evaluation (ULBC-8), verifiable it from the candidate executable.

<a id="P035"></a>

## 4 References

<a id="P036"></a>

[1] S4-261739, [ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.0

<a id="P037"></a>

[2] S4-261717, [ULBC-MED] ULBC-9: Assumptions for RTP header reduction and MTSI integration, Qualcomm, SA4#137-e

<a id="P038"></a>

[3] 3GPP TR 26.940, "Study on Ultra Low Bit rate Speech Codecs"

<a id="P039"></a>

[4] EVS-4 (S4-130778), EVS Design Constraints

<a id="P040"></a>

[5] 3GPP R2-133bis_NR-NTN_IoT-NTN_(Sergio)_EOM, https://www.3gpp.org/ftp/Meetings_3GPP _SYNC/ RAN2/ Inbox/Chair_Notes/R2-133bis_NR-NTN_IoT-NTN_(Sergio)_EOM.docx
