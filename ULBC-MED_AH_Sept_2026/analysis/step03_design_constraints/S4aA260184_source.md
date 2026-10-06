# S4aA260184 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260184_ULBC-4_v0.3.0.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 (AH) Audio SWG on ULBC-MED    Tdoc S4aA26xxxx

<a id="P001"></a>

Shanghai, China, 28 - 30 September 2026

<a id="P004"></a>

Source:    Fraunhofer IIS (Interim ULBC-4 Editor)

<a id="P005"></a>

Title:    [ULBC-MED] ULBC Design Constraints (ULBC-4)

<a id="P006"></a>

Version:    0.3.0 (draft)

<a id="P007"></a>

Document for:    Discussion and Agreement

<a id="P008"></a>

Agenda item:    4.4

<a id="P009"></a>

Work Item:    ULBC-MED

<a id="P011"></a>

## 1    Scope

<a id="P012"></a>

This initial permanent document presents the proposed starting point for the design constraints of the Ultra Low Bitrate speech Codec (ULBC) within 3GPP SA4. The ULBC work item specifies an ultra-low bit rate codec supporting the Voice over NB-IoT GEO feature; the study phase concluded at SA4#136 with TR 26.940. The design constraints below provide a framework that shall be fulfilled by candidate ULBC solutions at a minimum.

<a id="P013"></a>

## 2    Introduction

<a id="P014"></a>

The objective of the ULBC work item is to specify an ultra-low bit rate codec for IMS voice call over GEO access, realised by a single codec with a limited set of necessary functionalities sufficient to support the Voice over NB-IoT GEO feature. The design constraints derive from the agreed conclusions of TR 26.940 [1] and the agreed ULBC WID [2].

<a id="P015"></a>

Design constraints that are not yet agreed are shown in square brackets and are accompanied by an Editor's note identifying the open question and the proposals under consideration; these are to be resolved during the normative phase. Constraints given without brackets are agreed.

<a id="P016"></a>

## 3    ULBC codec design constraints

<a id="P017"></a>

Table 1 lists the ULBC codec design constraints.<br>
Numbers in parentheses refer to S4-26xxxx contributions to SA4#137-e, email or SWG online discussion. Numbers of the form axxx refer to contributions S4aA260xxx to the SA4 Audio SWG AH (Shanghai, September 2026).

<a id="P018"></a>

Table 1: ULBC codec design constraints

<a id="T019"></a>

<a id="T019-R01"></a>
**T019-R01**

- <a id="T019-R01-C01"></a>列 1: Parameter
- <a id="T019-R01-C02"></a>列 2: Design constraint
- <a id="T019-R01-C03"></a>列 3: Note

<a id="T019-R02"></a>
**T019-R02**

- <a id="T019-R02-C01"></a>列 1: Sampling Frequency
- <a id="T019-R02-C02"></a>列 2: The ULBC candidate codecs shall support PCM audio at the encoder input and at the decoder output at a sampling rate of <br><br><br><br>16kHz and 32kHz
- <a id="T019-R02-C03"></a>列 3: NOTE: resampling between 16kHz and 32kHz is not counted as part of complexity and algorithmic delay

<a id="T019-R03"></a>
**T019-R03**

- <a id="T019-R03-C01"></a>列 1: Audio bandwidth
- <a id="T019-R03-C02"></a>列 2: The ULBC candidate codecs shall support wideband (WB).<br>The ULBC candidate codecs may support super-wideband (SWB).
- <a id="T019-R03-C03"></a>列 3: NOTE: selection testing will be using WB[-only; limited amount of SWB tests are considered]<br><br>NOTE: SWB, if provided, needs to be tested against SWB reference, e.g. EVS-SWB<br><br><br><br>NOTE: if multiple bandwidths are supported the SDP negotiation should be clarified

<a id="T019-R04"></a>
**T019-R04**

- <a id="T019-R04-C01"></a>列 1: Number of audio channels
- <a id="T019-R04-C02"></a>列 2: The ULBC candidate codecs shall support mono coding with one channel input and one channel output.
- <a id="T019-R04-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).

<a id="T019-R05"></a>
**T019-R05**

- <a id="T019-R05-C01"></a>列 1: Bit rates
- <a id="T019-R05-C02"></a>列 2: The ULBC codec shall operate at the two bit rates 1.0 and 1.4kbps.<br>[<br>Editor's note: <br>Bitrates are gross bit rates for the ULBC payload comprising the codec payload header and the speech bits, excluding the protocol headers (e.g. RTP, UDP, …) <br>]
- <a id="T019-R05-C03"></a>列 3: Agreed WID objective [2].<br><br>The bit rate is fixed for the session (a164).<br><br>Editor's note: One vs two operating points and the specific rate(s) were FFS (no study-phase conclusion) at SA4#136. At SP#112 it was concluded that two rates shall be provided.

<a id="T019-R06"></a>
**T019-R06**

- <a id="T019-R06-C01"></a>列 1: Bundling
- <a id="T019-R06-C02"></a>列 2: The ULBC codec packetization shall support bundling for 80ms and 160ms and be able to packetize/depacketize the frames to fit the bundling periods.
- <a id="T019-R06-C03"></a>列 3: The bundling period is fixed for the session. (a164).<br><br>Editor’s note: For selection testing only 1.0kbps/160ms and 1.4kbps/80ms are considered.<br>Editor's note: This reflects a=ptime

<a id="T019-R07"></a>
**T019-R07**

- <a id="T019-R07-C01"></a>列 1: Frame length
- <a id="T019-R07-C02"></a>列 2: [The ULBC candidate codecs shall use a single frame length.] The codec frame length shall be <br>one of 20, 40, 80 ms
- <a id="T019-R07-C03"></a>列 3: 

<a id="T019-R08"></a>
**T019-R08**

- <a id="T019-R08-C01"></a>列 1: 
- <a id="T019-R08-C02"></a>列 2: 
- <a id="T019-R08-C03"></a>列 3: 

<a id="T019-R09"></a>
**T019-R09**

- <a id="T019-R09-C01"></a>列 1: Algorithmic codec delay
- <a id="T019-R09-C02"></a>列 2: [The algorithmic codec delay shall not exceed the bundling time + x ms.<br>- x=0 to 5ms (a144,1621)<br>- x=40ms (a155)<br>- x<=80ms (a116,1547)<br>- x=EVS range (email)<br>]
- <a id="T019-R09-C03"></a>列 3: Editor's note: the value of x is FFS. One-way GEO propagation is ~270 ms; the algorithmic codec delay and the bundling period are the controllable codec-layer contributions.

<a id="T019-R10"></a>
**T019-R10**

- <a id="T019-R10-C01"></a>列 1: Computational complexity
- <a id="T019-R10-C02"></a>列 2: The computational complexity and memory footprint shall ensure implementability on standard 3GPP UE platforms. <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>Positions – to be verified:<br>[<br>The computational complexity shall not exceed<br>- 0.6 GMAC/s (a115, 1555)<br>- 1 GMAC/s + [X] WMOPS (a102, 1514)<br>- 2 GMAC/s (1516, 1586)<br>- 2.5 GMAC/s (a141, a144, 1621)<br>- 3.0 GMAC/s (a138)<br>- Real-time factor as principal metric (a095) / in addition to the limit (a160)<br>]
- <a id="T019-R10-C03"></a>列 3: Agreed WID objective [2].

<a id="T019-R11"></a>
**T019-R11**

- <a id="T019-R11-C01"></a>列 1: Memory
- <a id="T019-R11-C02"></a>列 2: The memory footprint shall ensure implementability on standard 3GPP UE platforms.<br><br>ROM for NN model parameters <= [X] MB<br>ROM for NN model parameters includes NN model parameters for entirety of ULBC (both bitrates)<br><br>RAM for NN model parameters <= [Y] #params<br>Editor’s note: RAM for data path is TBD.[RAM usage only includes one bitrate’s NN model parameters (the active bitrate’s NN model parameters)]<br><br>Positions – to be verified:<br>[<br>Limits proposed:<br>ROM:<br>- 5 M parameters (a102, a144, 1514)<br>- 6 M parameters (1555)<br>- 7.5 M parameters (a139)<br>- 12 MB at 2 bytes per parameter (a115)<br>- 12 MB at 4 bytes per parameter (a141)<br>- 24 MB at 2 bytes per parameter (1580)<br><br>RAM<br>- 3 M parameters (a141?)<br>- 5 M parameters (a102?, a144?, 1514?)<br>- 6 M parameters (1569, 1580)<br>- 12 M parameters (1580)<br>- 12.5 MB including state memory (1586)<br>].
- <a id="T019-R11-C03"></a>列 3: Agreed WID objective [2].<br><br>NOTE: RAM and ROM are counted separately.

<a id="T019-R12"></a>
**T019-R12**

- <a id="T019-R12-C01"></a>列 1: [Jitter buffer management (JBM)
- <a id="T019-R12-C02"></a>列 2: The ULBC candidate codecs shall support JBM.
- <a id="T019-R12-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: whether the JBM requirements in TS 26.114 [3] need adjustment for Voice over NB-IoT GEO is FFS.<br>JBM-induced delay was traditionally not part of algorithmic delay.<br>]

<a id="T019-R13"></a>
**T019-R13**

- <a id="T019-R13-C01"></a>列 1: Packet loss concealment (PLC)
- <a id="T019-R13-C02"></a>列 2: The ULBC candidate codecs shall support PLC.
- <a id="T019-R13-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: loss rates are FFS.

<a id="T019-R14"></a>
**T019-R14**

- <a id="T019-R14-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T019-R14-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).
- <a id="T019-R14-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.

<a id="T019-R15"></a>
**T019-R15**

- <a id="T019-R15-C01"></a>列 1: 
- <a id="T019-R15-C02"></a>列 2: 
- <a id="T019-R15-C03"></a>列 3: 

<a id="T019-R16"></a>
**T019-R16**

- <a id="T019-R16-C01"></a>列 1: 
- <a id="T019-R16-C02"></a>列 2: 
- <a id="T019-R16-C03"></a>列 3: 

<a id="T019-R17"></a>
**T019-R17**

- <a id="T019-R17-C01"></a>列 1: 
- <a id="T019-R17-C02"></a>列 2: 
- <a id="T019-R17-C03"></a>列 3: 

<a id="T019-R18"></a>
**T019-R18**

- <a id="T019-R18-C01"></a>列 1: RTP payload format and header reduction
- <a id="T019-R18-C02"></a>列 2: An RTP payload format shall be specified, together with the essential fields for RTP header reduction.<br>[Packetizer/depacketizer to handle ULBC payloads (1546)]<br>Editor’s note: A proposal to be considered was made by Qualcomm, which relates to the frame length.
- <a id="T019-R18-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: may also be handled in the dedicated permanent document (ULBC-9), covering RTP header reduction and system integration; the header size affects the payload budget available to the codec.

<a id="T019-R19"></a>
**T019-R19**

- <a id="T019-R19-C01"></a>列 1: [ Noise suppression and robustness to non-speech input
- <a id="T019-R19-C02"></a>列 2: [FFS]<br>[<br>- == remove as part of output gain tolerance (1546)<br>- == remove as as handled in ULBC-3 (1586)<br>]
- <a id="T019-R19-C03"></a>列 3: Editor's note: may also need to be addressed in the performance requirements (ULBC-3) or as part of output gain tolerance. ]

<a id="T019-R20"></a>
**T019-R20**

- <a id="T019-R20-C01"></a>列 1: Output gain tolerance
- <a id="T019-R20-C02"></a>列 2: [The ULBC candidate codec should neither amplify nor attenuate the output signal significantly relative to the input signal.]<br>[<br>- ==rediscuss as not in WID or TR (email),<br>- per subband 0-8 [and 8-16]kHz with a tolerance of [0.5dB] (1548)<br>]
- <a id="T019-R20-C03"></a>列 3: Editor's note: limits and measurement methodology are FFS; to be defined with the processing plan (ULBC-7) and performance requirements (ULBC-3).

<a id="P020"></a>

## 4    Definitions

<a id="P021"></a>

Bundling period (packetization time): the time interval over which multiple speech frames are grouped for transmission as a single packet.

<a id="P022"></a>

Algorithmic codec delay: Bundling-time buffering delay plus any other delays inherent in the codec algorithm (e.g. look-ahead, [sample-rate conversion, ]decoder post-processing). [No resampling delay is included given single sample rate operation. The algorithmic delay of the ULBC candidate codecs excludes processing delay (e.g., runtime of the DSP to process the speech frame at encoder and decoder), and channel transmission delays. (a141)]

<a id="P024"></a>

## 5    Revision history

<a id="P025"></a>

Table 2: Revision history

<a id="T026"></a>

<a id="T026-R01"></a>
**T026-R01**

- <a id="T026-R01-C01"></a>列 1: Date
- <a id="T026-R01-C02"></a>列 2: Meeting
- <a id="T026-R01-C03"></a>列 3: Subject / comment
- <a id="T026-R01-C04"></a>列 4: Revision of
- <a id="T026-R01-C05"></a>列 5: Version

<a id="T026-R02"></a>
**T026-R02**

- <a id="T026-R02-C01"></a>列 1: 2026-08
- <a id="T026-R02-C02"></a>列 2: SA4#137-e
- <a id="T026-R02-C03"></a>列 3: Initial ULBC-4 baseline created by interim editor from agreed TR 26.940 (Table 6.1-1) and agreed WID objectives (SP-260696).
- <a id="T026-R02-C04"></a>列 4: -
- <a id="T026-R02-C05"></a>列 5: 0.1.0

<a id="T026-R03"></a>
**T026-R03**

- <a id="T026-R03-C01"></a>列 1: 2026-08
- <a id="T026-R03-C02"></a>列 2: SA4#137-e
- <a id="T026-R03-C03"></a>列 3: Referencing inputs to SA4#137-e.<br>Capturing agreements on<br>- bit rate (1.0 &B 1.4 kbps)
- <a id="T026-R03-C04"></a>列 4: 0.1.0
- <a id="T026-R03-C05"></a>列 5: 0.2.0

<a id="T026-R04"></a>
**T026-R04**

- <a id="T026-R04-C01"></a>列 1: 2026-08
- <a id="T026-R04-C02"></a>列 2: S4-#137-e
- <a id="T026-R04-C03"></a>列 3: Editorial correction in definition of algorithmic delay
- <a id="T026-R04-C04"></a>列 4: 0.2.0
- <a id="T026-R04-C05"></a>列 5: 0.2.1

<a id="T026-R05"></a>
**T026-R05**

- <a id="T026-R05-C01"></a>列 1: 2026-09
- <a id="T026-R05-C02"></a>列 2: SA4 Audio SWG AH, Shanghai
- <a id="T026-R05-C03"></a>列 3: Capturing agreements on<br>Sampling frequency<br>Audio bandwidth<br>Bit rates<br>Bundling<br>Frame Length<br>AH inputs consolidated with SA4#137-e positions on complexity/memory and algorithmic delay;<br>Refinement on algorithmic delays
- <a id="T026-R05-C04"></a>列 4: 0.2.1
- <a id="T026-R05-C05"></a>列 5: 0.3.0

<a id="P027"></a>

## 6    References

<a id="P028"></a>

[1]    3GPP TR 26.940 v20.0.0 : "Study on Ultra Low Bit rate Speech Codecs".

<a id="P029"></a>

[2]    SP-260696: "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", June 2026.

<a id="P030"></a>

[3]    3GPP TS 26.114: "IP Multimedia Subsystem (IMS); Multimedia telephony; Media handling and interaction".

<a id="P031"></a>

[4]    ITU-T Recommendation G.191: "Software tools for speech and audio coding standardization".
