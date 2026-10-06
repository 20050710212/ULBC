# S4aA260141 attachment — 当前修订文本

S4-26xxx_Revision of ULBC-4_ULBC_Design_Constraints_v0.2.1.docx

<a id="P000"></a>
3GPP TSG-SA4 AH Meeting on ULBC    Tdoc S4-26xxx

<a id="P001"></a>
Shanghai, PRC, 28 - 30 September 2026    revision of S4-261847

<a id="P004"></a>
Source:    Editor (Fraunhofer IIS)

<a id="P005"></a>
Title:    [ULBC-MED] ULBC Design Constraints (ULBC-4)

<a id="P006"></a>
Version:    Revision of 0.2.1

<a id="P008"></a>
Agenda item:    tbd

<a id="P011"></a>
1    Scope

<a id="P012"></a>
This initial permanent document presents the proposed starting point for the design constraints of the Ultra Low Bitrate speech Codec (ULBC) within 3GPP SA4. The ULBC work item specifies an ultra-low bit rate codec supporting the Voice over NB-IoT GEO feature; the study phase concluded at SA4#136 with TR 26.940. The design constraints below provide a framework that shall be fulfilled by candidate ULBC solutions at a minimum.

<a id="P013"></a>
2    Introduction

<a id="P014"></a>
The objective of the ULBC work item is to specify an ultra-low bit rate codec for IMS voice call over GEO access, realised by a single codec with a limited set of necessary functionalities sufficient to support the Voice over NB-IoT GEO feature. The design constraints derive from the agreed conclusions of TR 26.940 [1] and the agreed ULBC WID [2].

<a id="P015"></a>
Design constraints that are not yet agreed are shown in square brackets and are accompanied by an Editor's note identifying the open question and the proposals under consideration; these are to be resolved during the normative phase. Constraints given without brackets are agreed.

<a id="P016"></a>
3    ULBC codec design constraints

<a id="T019"></a>
Parameter | Design constraint | Note
Sampling Frequency | The ULBC codec shall support PCM audio at the encoder input and at the decoder output at a sampling rate of 16 kHz OR 32 kHz | 
Audio bandwidth | The ULBC codec shall support wideband (WB) audio 
OR superwideband (SWB) audio | Agreed WID objective [2].
Number of audio channels | The ULBC candidate codecs shall support mono coding with one channel input and one channel output. | Agreed (TR 26.940 [1] Table 6.1-1).
Bit rates | The ULBC codec shall operate at the two bit rates 1.0 and 1.4kbps.

NOTE:
Bitrates are gross bit rates for the ULBC payload comprising the codec payload header and the speech bits, excluding the protocol headers (e.g. RTP, UDP, …) | Agreed WID objective [2].
.
Bundling time | The ULBC codec packetization shall support bundling for 80ms and 160ms and be able to packetize/depacketize the frames to fit the bundling periods.
NOTE: Bundling time reflects a=ptime | 
Frame length | The codec frame length shall be one of 20, 40, 80 ms | NOTE: for fair comparison purpose among candidates and reference codecs, all packet loss conditions shall be evaluated with the same bundling time
 |  | 
Algorithmic codec delay | See definition below
[The algorithmic codec delay shall not exceed the bundling time + x ms.
- x=0 to 5ms (1621)
- x<=80ms (1547)
- x=EVS range (email)
] | Editor's note: the value of x is FFS. One-way GEO propagation is ~270 ms; the algorithmic codec delay and the bundling period are the controllable codec-layer contributions.
Computational complexity and memory | Computational complexity: 






≤ 2.5 GMACs/s using the TR 26.940 clause 6.4.2 convention.
Memory: ≤ 3M parameters (assuming float32).

C implementation with ML components via an ONNX runtime shall be supported (for RTT measurement). | Agreed WID objective [2].
Editor's note: The complexity metric and the numeric limits are FFS. 
TR 26.940 clause 6.2 (among other clauses contains an extensive discussion on complexity/memory design constraints, e.g.:
Complexity should be defined from AI-oriented measures (MMAC/s, model size in bytes, parameter precision, TOPS/W), not as a multiple of legacy-codec operations; model size should be reported as a tuple (number of parameters, size in bytes).
Editor’s note: How the complexity and memory constraints are defined for a ULBC candidate codec supporting two (2) bitrates in a single codec are to be clarified and constraints documented accordingly.
Jitter buffer management (JBM) | The ULBC candidate codecs shall support JBM.
The JBM may be provided as an internal JBM or an external JBM. | Agreed (TR 26.940 [1] Table 6.1-1).
JBM requirements in 26.114 may have to be adjusted to Voice over Nb-IOT
End to end delay/loss profiles are missing for Nb-IOT voice service 
Testing of JBM is expected in characterization phase
Packet loss concealment (PLC) | The ULBC candidate codecs shall support PLC.
NOTE: Erasures apply at the time bundle level (not internal codec frame level) | Agreed (TR 26.940 [1] Table 6.1-1).
Discontinuous transmission (DTX / CNG) | The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).
The SID transmission shall use the same bundling time as active speech. SID update rate TBD | Agreed (TR 26.940 [1] Table 6.1-1).
Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.
 |  | 
 |  | 
 |  | 
Noise suppression and robustness to non-speech input | The ULBC codec shall not attenuate the level of the noisy speech input signal (in both active and inactive frames). Limits and objective testing to be defined in ULBC-3 and ULBC-7, respectively.

If a ULBC candidate supports activating noise suppression at the command line level, this option shall be disabled by default. | Emergency call use case justifies preserving background noise in appropriate way as documented in TR 26.940.
Output gain tolerance | The ULBC candidate codec should neither amplify nor attenuate the output signal significantly relative to the input signal. Limits and objective testing to be defined in ULBC-3 and ULBC-7, respectively.




] | 
<a id="P020"></a>
4    Definitions

<a id="P021"></a>
Bundling period (packetization time): the time interval over which multiple speech frames are grouped for transmission as a single packet.

<a id="P022"></a>
Algorithmic codec delay: Bundling-time buffering delay plus any other delays inherent in the codec algorithm (e.g. look-ahead, decoder post-processing). No resampling delay is included given single sample rate operation. The algorithmic delay of the ULBC candidate codecs excludes processing delay (e.g., runtime of the DSP to process the speech frame at encoder and decoder), and channel transmission delays.

<a id="P023"></a>
5    Revision history

<a id="P024"></a>
Table 2: Revision history

<a id="T025"></a>
Date | Meeting | Subject / comment | Revision of | Version
2026-08 | SA4#137-e | Initial ULBC-4 baseline created by interim editor from agreed TR 26.940 (Table 6.1-1) and agreed WID objectives (SP-260696). | - | 0.1.0
2026-08 | SA4#137-e | Referencing inputs to SA4#137-e.
Capturing agreements on
- bit rate (1.0 &B 1.4 kbps) | 0.1.0 | 0.2.0
2026-08 | S4-#137-e | Editorial correction in definition of algorithmic delay | 0.2.0 | 0.2.1
2026-09 | AH Meeting on ULBC |  |  | 
<a id="P026"></a>
6    References

<a id="P027"></a>
[1]    3GPP TR 26.940 v20.0.0 : "Study on Ultra Low Bit rate Speech Codecs".

<a id="P028"></a>
[2]    SP-260696: "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", June 2026.

<a id="P029"></a>
[3]    3GPP TS 26.114: "IP Multimedia Subsystem (IMS); Multimedia telephony; Media handling and interaction".
