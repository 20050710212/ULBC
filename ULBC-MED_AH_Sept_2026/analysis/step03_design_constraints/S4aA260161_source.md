# S4aA260161 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260161.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG Ad-Hoc Meeting on ULBC-MED    S4aA260161

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Lenovo, Motorola Mobility

<a id="P004"></a>

Title:    [ULBC-MED] ULBC audio bandwidth and sampling rate requirements

<a id="P005"></a>

Spec:    ULBC permanent documents (ULBC-4)

<a id="P006"></a>

Agenda item:    4.4

<a id="P007"></a>

Document for:    Agreement

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

The ULBC-MED Work Item targets a deployable codec for IMS voice over NB-IoT GEO satellite access. The WID requires at least wideband (WB) voice coding with quality not worse than AMR-WB at 12.65 kbit/s. The operating bandwidth and input/output sampling rate are part of normative phase discussions. However, despite the clear mandatory WB support, the recent SA4#137e meeting could not conclude on the required sampling and audio bandwidth requirements, with both 16 kHz (WB) and 32 kHz (up-to-SWB) operation being considered, including a proposal to use only a single 32 kHz input/output so that proponents may exploit SWB capability.

<a id="P012"></a>

## 2. Discussion

<a id="P013"></a>

As captured by the WID, the native audio bandwidth mandatory to support is WB (16 kHz sampling rate), whereas beyond WB support is optional. Furthermore, the performance and quality threshold agreed at WID-level for ULBC is that of at least AMR-WB 12.65 kbps, an operation mode which is already capable of delivering HD voice quality and is currently the work horse of deployed IMS speech codecs.

<a id="P014"></a>

## 16 kHz I/O perspective

<a id="P015"></a>

The proposal for a 16 kHz I/O sampling rate has seen majority support under solid favorable arguments, e.g., [1], [2], over 32 kHz I/O sampling rate. To avoid repetition of past discussion points, we highlight just top three of the most important technical arguments raised for 16 kHz I/O, ignoring and scheduling and logistic aspects of evaluation:

<a id="P016"></a>

Simple and best alignment with WB WID target. Allowing a single 32 kHz I/O requires first a foremost a full end-to-end 32 kHz audio pipeline to achieve WB-equivalent quality. This comes with impact onto real products that should be well backed by a corresponding quality bump well beyond WB (i.e., that of an equivalent SWB deployed codec, e.g., EVS-SWB 13.2 kbps). 32 kHz I/O offers additionally an unfair advantage only to coders exploiting signals beyond WB to reach same WB quality target when compared to more robust coders operating at WB. Therefore, any mixed bandwidth testing is highly fundamentally questionable and unreasonable if 32 kHz I/O were to be considered at all against a WB-only quality target.

<a id="P017"></a>

Inter-working with legacy mobile and landline systems is still primarily WB-focused. Most importantly for ULBC, the emergency services are traditionally dependent on NB coders, and only slowly evolve to rely at most on WB coders, such as AMR-WB. Thus, the extra audio bandwidth advantage of an SWB ULBC coder is lost in some of its most important applications (e.g., E911/E112 calls etc.), while complexity and costs associated with SWB are maintained.

<a id="P018"></a>

Mixed bandwidth lab evaluation of WB vs SWB speech is not well reflective of the quality perceived in the real-world. Realistic terminal electro-acoustic and Physics constraints considerably limit the lab perceived quality gap between WB and SWB, which diminishes in reality the additional high fidelity that SWB is supposed to offer on top of WB. Such diminishing returns are also statistically confirmed by clean speech P.800 ACR5 and P.808 ACR/DCR limited tests as captured in TR 26.940, Clauses 7.2.3 and 7.4.2.4 [1]. Therefore, ignoring realistic terminal electro-acoustic input/output masking in testing can misleadingly skew perceived quality gap between WB and SWB in the favor of the latter, which becomes a blocking concern when evaluating WB and SWB coders against the same performance target.

<a id="P020"></a>

## 32 kHz I/O perspective

<a id="P021"></a>

On the other hand, the proposal for a 32 kHz I/O sampling rate has been supported by several companies under the main argument of a “technically elegant solution to sampling rate interface, providing design freedom to proponents”.

<a id="P023"></a>

Way forward

<a id="P024"></a>

Given the above, the source is of the opinion that:

<a id="P025"></a>

Proposal 1: 16 kHz I/O sampling rate is mandatory and should reach on its own merit (i.e., not based on additional bandwidth beyond WB) the not worse than AMR-WB 12.65 kbps quality as agreed in the WID.

<a id="P027"></a>

Proposal 2: If a second 32 kHz I/O sampling rate interface is to be further considered at all, this should be done based on a clear set of principles ensuring a fair and value-adding codec evaluation:

<a id="P028"></a>

No mixed bandwidth testing between WB and SWB is to be performed. Tests and evaluation of WB and SWB codec modes are to be separated based on the I/O sampling rate.

<a id="P029"></a>

If a sampling rate enabling SWB audio content is agreed, a considerable bump in quality beyond WB is expected and a SWB mode needs to be not worse than a deployed SWB 3GPP codec operation point, superior to AMR-WB 12.65 kbps.

<a id="P030"></a>

NOTE: Such SWB quality targets, such as EVS-SWB 13.2 kbps or others, are up for further discussions.

<a id="P032"></a>

## 3. Conclusion and proposal

<a id="P033"></a>

The following proposals are up to agreement:

<a id="P034"></a>

Proposal 1: 16 kHz I/O sampling rate is mandatory and should reach on its own merit (i.e., not based on additional bandwidth beyond WB) the not worse than AMR-WB 12.65 kbps quality as agreed in the WID.

<a id="P036"></a>

Proposal 2: If a second 32 kHz I/O sampling rate interface is to be further considered at all, this should be done based on a clear set of principles ensuring a fair and value-adding codec evaluation:

<a id="P037"></a>

No mixed bandwidth testing between WB and SWB is to be performed. Tests and evaluation of WB and SWB codec modes are to be separated based on the I/O sampling rate.

<a id="P038"></a>

If a sampling rate enabling SWB audio content is agreed, a considerable bump in quality beyond WB is expected and a SWB mode needs to be not worse than a deployed SWB 3GPP codec operation point, superior to AMR-WB 12.65 kbps.

<a id="P039"></a>

NOTE: Such SWB quality targets, such as EVS-SWB 13.2 kbps or others. are up for further discussions.

<a id="P041"></a>

The corresponding changes to the ULBC-4 – Design Constraints PDoc are additionally proposed for agreement:

<a id="P042"></a>

* * * First Change * * * *

<a id="P043"></a>

## 3    ULBC codec design constraints

<a id="P044"></a>

Table 1 lists the ULBC codec design constraints.<br>
Numbers in parentheses refer to S4-26xxxx contributions to SA4#137-e, email or SWG online discussion.

<a id="P045"></a>

Table 1: ULBC codec design constraints

<a id="T046"></a>

<a id="T046-R01"></a>
**T046-R01**

- <a id="T046-R01-C01"></a>列 1: Parameter
- <a id="T046-R01-C02"></a>列 2: Design constraint
- <a id="T046-R01-C03"></a>列 3: Note

<a id="T046-R02"></a>
**T046-R02**

- <a id="T046-R02-C01"></a>列 1: Sampling Frequency
- <a id="T046-R02-C02"></a>列 2: The ULBC codec shall support PCM audio at the encoder input and at the decoder output at a sampling rate of 16 kHz.
- <a id="T046-R02-C03"></a>列 3: Editor's note: Additional I/O sampling rates are FFS.

<a id="T046-R03"></a>
**T046-R03**

- <a id="T046-R03-C01"></a>列 1: Audio bandwidth
- <a id="T046-R03-C02"></a>列 2: The ULBC codec shall achieve at least wideband (WB) audio. [Specifics FFS]
- <a id="T046-R03-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: Whether super-wideband or fullband is required or optional are FFS. Corresponding quality targets of ULBC modes above WB, if any, are FFS.<br>TR 26.940 [1] evaluated various bandwidths; WB solutions at ~1 kb/s matched AMR-WB 12.65 kb/s on clean speech.<br><br>Bandwidth of the audio material to be detailed in ULBC-8a (1562, 1513)

<a id="T046-R04"></a>
**T046-R04**

- <a id="T046-R04-C01"></a>列 1: Number of audio channels
- <a id="T046-R04-C02"></a>列 2: The ULBC candidate codecs shall support mono coding with one channel input and one channel output.
- <a id="T046-R04-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).

<a id="T046-R05"></a>
**T046-R05**

- <a id="T046-R05-C01"></a>列 1: Bit rates
- <a id="T046-R05-C02"></a>列 2: The ULBC codec shall operate at the two bit rates 1.0 and 1.4kbps.<br>[<br>Editor's note: <br>Bitrates are gross bit rates for the ULBC payload comprising the codec payload header and the speech bits, excluding the protocol headers (e.g. RTP, UDP, …) <br>]
- <a id="T046-R05-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: One vs two operating points and the specific rate(s) were FFS (no study-phase conclusion) at SA4#136. At SP#112 it was concluded that two rates shall be provided.

<a id="T046-R06"></a>
**T046-R06**

- <a id="T046-R06-C01"></a>列 1: [<br>Bundling
- <a id="T046-R06-C02"></a>列 2: The ULBC codec packetization shall support bundling for 80ms and 160ms and be able to packetize/depacketize the frames to fit the bundling periods.
- <a id="T046-R06-C03"></a>列 3: Editor's note: This reflects a=ptime

<a id="T046-R07"></a>
**T046-R07**

- <a id="T046-R07-C01"></a>列 1: Frame length
- <a id="T046-R07-C02"></a>列 2: The codec frame length shall be one of 20, 40, 80 ms
- <a id="T046-R07-C03"></a>列 3: ]

<a id="T046-R08"></a>
**T046-R08**

- <a id="T046-R08-C01"></a>列 1: 
- <a id="T046-R08-C02"></a>列 2: 
- <a id="T046-R08-C03"></a>列 3: 

<a id="T046-R09"></a>
**T046-R09**

- <a id="T046-R09-C01"></a>列 1: Algorithmic codec delay
- <a id="T046-R09-C02"></a>列 2: [The algorithmic codec delay shall not exceed the bundling time + x ms.<br>- x=0 to 5ms (1621)<br>- x<=80ms (1547)<br>- x=EVS range (email)<br>]
- <a id="T046-R09-C03"></a>列 3: Editor's note: the value of x is FFS. One-way GEO propagation is ~270 ms; the algorithmic codec delay and the bundling period are the controllable codec-layer contributions.

<a id="T046-R10"></a>
**T046-R10**

- <a id="T046-R10-C01"></a>列 1: Computational complexity and memory<br>Editor's note: suggested to split up
- <a id="T046-R10-C02"></a>列 2: The computational complexity and memory footprint shall ensure implementability on standard 3GPP UE platforms. <br>[Specifics FFS]<br>[Computational complexity and memory footprint includes:<br>- sampling rate conversion (1518)<br><br>Positions:<br>- MAC/s primary; approximately 1 GMAC/s; approximately 5M parameters; one combined complexity budget and one combined parater budget for both operating points acounted against the design constraints; complexity additionally as a Figure of Merit (1512, 1514)<br>- GMACs/s rather than parameter count; 2 GMAC/s; A78 at 2.0–2.3 GHz or A76 at 2.2 GHz as baseline core (1516)<br>- C with ML components via an ONNX runtime, no custom operators; inference engine excluded from the count; ROM and RAM counted separately; host lab verifies. Counting method revised by the source (1546)<br>- Model size < 6M parameters and complexity < 1.2 GFLOPS or 600 MMACS; mixed precision not recommended at qualification and selection (1555)<br>- FLOPs primary, parameter count auxiliary; WMOPS, operator count and memory access excluded as hardware-dependent (1559)<br>- RAM constraint of 6M parameters, supported by a listening test across four model sizes at 1.0 kbit/s (1569)<br>- RAM 6M parameters for one active mode; ROM 24 Mbytes across all modes at 2 bytes per parameter (1580)<br>- ≤ 2 GMACs/s; model size plus state memory ≤ 12.5 Mbytes; compute excluding quantization, model size including it; real-time operation on efficiency cores (1586)<br>- P9: ≤ 2.5 GMACs/s using the TR 26.940 clause 6.4.2 convention. P10: report parameter count and model size in bytes (1621)<br>- Definitional clarification required before numerical constraints (1627)<br>- TBD pending clarification on complexity counting (1640)<br>]
- <a id="T046-R10-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: The complexity metric and the numeric limits are FFS. <br>TR 26.940 clause 6.2 (among other clauses contains an extensive discussion on complexity/memory design constraints, e.g.:<br>Complexity should be defined from AI-oriented measures (MMAC/s, model size in bytes, parameter precision, TOPS/W), not as a multiple of legacy-codec operations; model size should be reported as a tuple (number of parameters, size in bytes).<br>Editor’s note: How the complexity and memory constraints are defined for a ULBC candidate codec supporting two (2) bitrates in a single codec are to be clarified and constraints documented accordingly.

<a id="T046-R11"></a>
**T046-R11**

- <a id="T046-R11-C01"></a>列 1: [Jitter buffer management (JBM)
- <a id="T046-R11-C02"></a>列 2: The ULBC candidate codecs shall support JBM.
- <a id="T046-R11-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: whether the JBM requirements in TS 26.114 [3] need adjustment for Voice over NB-IoT GEO is FFS.<br>JBM-induced delay was traditionally not part of algorithmic delay.<br>]

<a id="T046-R12"></a>
**T046-R12**

- <a id="T046-R12-C01"></a>列 1: Packet loss concealment (PLC)
- <a id="T046-R12-C02"></a>列 2: The ULBC candidate codecs shall support PLC.
- <a id="T046-R12-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: loss rates are FFS.

<a id="T046-R13"></a>
**T046-R13**

- <a id="T046-R13-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T046-R13-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).
- <a id="T046-R13-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.

<a id="T046-R14"></a>
**T046-R14**

- <a id="T046-R14-C01"></a>列 1: 
- <a id="T046-R14-C02"></a>列 2: ~~ ~~
- <a id="T046-R14-C03"></a>列 3: 

<a id="T046-R15"></a>
**T046-R15**

- <a id="T046-R15-C01"></a>列 1: 
- <a id="T046-R15-C02"></a>列 2: 
- <a id="T046-R15-C03"></a>列 3: 

<a id="T046-R16"></a>
**T046-R16**

- <a id="T046-R16-C01"></a>列 1: RTP payload format and header reduction
- <a id="T046-R16-C02"></a>列 2: An RTP payload format shall be specified, together with the essential fields for RTP header reduction.<br>[Packetizer/depacketizer to handle ULBC payloads (1546)]
- <a id="T046-R16-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: may also be handled in the dedicated permanent document (ULBC-9), covering RTP header reduction and system integration; the header size affects the payload budget available to the codec.

<a id="T046-R17"></a>
**T046-R17**

- <a id="T046-R17-C01"></a>列 1: [ Noise suppression and robustness to non-speech input
- <a id="T046-R17-C02"></a>列 2: [FFS]<br>[<br>- == remove as part of output gain tolerance (1546)<br>- == remove as as handled in ULBC-3 (1586)<br>]
- <a id="T046-R17-C03"></a>列 3: Editor's note: may also need to be addressed in the performance requirements (ULBC-3) or as part of output gain tolerance. ]

<a id="T046-R18"></a>
**T046-R18**

- <a id="T046-R18-C01"></a>列 1: Output gain tolerance
- <a id="T046-R18-C02"></a>列 2: [The ULBC candidate codec should neither amplify nor attenuate the output signal significantly relative to the input signal.]<br>[<br>- ==rediscuss as not in WID or TR (email),<br>- per subband 0-8 [and 8-16]kHz with a tolerance of [0.5dB] (1548)<br>]
- <a id="T046-R18-C03"></a>列 3: Editor's note: limits and measurement methodology are FFS; to be defined with the processing plan (ULBC-7) and performance requirements (ULBC-3).

<a id="P048"></a>

* * * End of Changes * * * *

<a id="P050"></a>

## 4. References

<a id="P051"></a>

[1] Tdoc S4-261513, [ULBC-MED] On ULBC wideband native operating point and evaluation focus, Source: Samsung, Qualcomm, ByteDance. Status: Noted, Meeting: SA4 #137e.

<a id="P052"></a>

[2] Tdoc S4-261616, [ULBC-MED] On ULBC audio bandwidth and sampling rate, Source: Lenovo, Motorola Mobility, Status: Noted, Meeting: SA4#137e.

<a id="P053"></a>

[3] Tdoc S4-261518, [ULBC-MED] Inclusion of 16 kHz input/output testing for ULBC, Source: China Telecommunications, Status: Noted, Meeting SA4#137e.
