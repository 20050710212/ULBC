# S4aA260101 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260101-DesignConstraints_and_PerformanceRequirements_AudioBandwidth_ULBC.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Title:    [ULBC-MED] Design Constraints and Performance Requirements Regarding Audio Bandwidth for ULBC

<a id="P001"></a>

Source:    NTT, Inc., Panasonic Holdings Corporation

<a id="P002"></a>

Document for:    Discussion & Agreement

<a id="P003"></a>

Agenda item:    4.3, 4.4

<a id="P005"></a>

Introduction

<a id="P007"></a>

At SA4#137-e, ULBC-3 on performance requirements and ULBC-4 on design constraints have been discussed and agreed as initial permanent documents in S4-261771 and S4-261847, respectively. Both documents keep the audio bandwidth and sampling frequency open.

<a id="P008"></a>

ULBC-4 requires at least WB audio but records competing options for 16 kHz or 32 kHz input/output and for WB-only, optional SWB, or bandwidth design freedom. ULBC-3 records that it is still under discussion whether separate WB and SWB performance requirements are needed.

<a id="P009"></a>

The discussion has therefore mixed three different parameters: the external input/output sampling rate, the coded audio bandwidth selected by a candidate system, and the audio bandwidth of the test material (as a performance requirement).

<a id="P010"></a>

This contribution proposes to separate three parameters. A common 32 kHz external interface should be used for qualification and selection testing, while WB, SSWB, or SWB coding should remain a proponent design choice subject to the common ULBC constraints. The audio bandwidth of the existing codec, as a representative of the performance requirements, can differ from those that ULBC chose.

<a id="P011"></a>

Note that once a single winning codec for ULBC is selected, the external interface sampling frequency can be adjusted to that of the winning system.

<a id="P012"></a>

Discussion

<a id="P014"></a>

The WID defines a minimum capacity, not a maximum bandwidth.

<a id="P015"></a>

The ULBC-MED WID requires at least WB voice coding and sets the performance objective for a commercially deployed WB service. “At least WB” establishes a floor. It does not require WB-only operation and does not exclude SSWB or SWB when a candidate can meet the agreed bitrate, complexity, memory, delay, and robustness constraints.

<a id="P016"></a>

Constraining every candidate to WB would determine the bandwidth-architecture trade-off before evaluation. At ultra-low bitrate, one candidate may allocate resources to a stronger WB core, while another may obtain better end-to-end quality by reconstructing useful energy above WB. The common resource constraints already make that trade-off visible. The evaluation should determine which solution provides the best performance for the ULBC service.

<a id="P017"></a>

Sampling frequency and coded bandwidth are different parameters

<a id="P018"></a>

Using a single 32 kHz external interface (for qualification and selection) can avoid candidate-specific test interfaces while preserving WB, SSWB, and SWB design options. Any candidate-specific sampling-rate conversion is part of the submitted processing chain and should be included in the applicable complexity, memory, and delay assessment. However, once a winning system is selected, the sampling conversion may no longer be needed because the champion's native operating sampling frequency will become the ULBC’s official operating sampling frequency.

<a id="P019"></a>

Audio bandwidth is part of codec performance

<a id="P020"></a>

It has been argued that a mixed-bandwidth evaluation could favor candidates that reproduce a wider audio bandwidth, even if this does not reflect better coding performance within the WB range. This concern assumes that performance within the WB range should be evaluated independently of the candidate’s end-to-end audio bandwidth. However, the objective of the selection is not to compare an isolated WB core or a particular internal coding structure. It is to identify the candidate that provides the best overall end-to-end performance while satisfying the same bitrate, complexity, memory, delay, and robustness constraints.

<a id="P021"></a>

Each proponent may decide how to allocate the common resource budget between coding accuracy within the WB range and reconstruction of useful energy above WB. A wider-band candidate receives no additional resource budget. Any trade-off between WB accuracy, robustness, and the reproduction of higher-frequency content, therefore, remains part of the resulting end-to-end performance. Reproduced audio bandwidth should be treated as one aspect of overall codec performance, rather than as an advantage that must be removed before candidates are compared.

<a id="P022"></a>

The purpose of the common experiment is not to make audio bandwidth perceptually neutral. Rather, it is to assess any benefits or disadvantages resulting from a candidate’s bandwidth design choice, along with its effects on speech fidelity, robustness, and other relevant performance dimensions, under the same resource constraints.

<a id="P023"></a>

Note that EVS selection supports mixed-bandwidth testing; therefore, conditions across different bandwidths can be included in the same experiment, and statistical comparisons can be performed within a single test.

<a id="P024"></a>

Separate WB and SWB qualification branches are unnecessary

<a id="P025"></a>

Separating the WB and SWB branches would duplicate the test conditions. This duplicates the coding bandwidth as a selectable functionality of a ULBC, which is not stated in the WID. This may complicate the situation. They would require an additional rule to combine the branches into a single figure of merit. The relative weighting of WB and SWB has no unique technical answer. Besides, if one of the two sounds better to the other, only the better one would suffice our need.

<a id="P026"></a>

A unified experiment with a common 32 kHz interface avoids this problem. Candidate conditions, applicable codec references, and direct references are placed in the same experiment. The declared maximum audio bandwidth of each candidate is reported for transparency and may be used for diagnostic analysis, but it does not create a separate qualification branch (i.e., for the noisy speech condition, SWB oracle noisy speech can be used as a reference for DCR).

<a id="P027"></a>

Responses to concerns raised at SA4#137-e

<a id="P028"></a>

Interworking with deployed WB services: AMR-WB tandeming is important and could be tested where applicable, but it is one end-to-end path in the application scenario. It should not limit native ULBC capability for ULBC-to-ULBC or SWB-capable endpoints. Note that by the time ULBC is deployed and widespread, a larger number of EVS SWB terminals will be deployed worldwide.

<a id="P029"></a>

Complexity and power: Since a wider-band solution receives no extra complexity or delay budget. If it cannot provide any advantage within the common constraints, it will not benefit in evaluation. Prohibiting it in advance is unnecessary.

<a id="P030"></a>

Fairness: The appropriate definition of fairness depends on the purpose of the selection. If the purpose were to compare coding efficiency strictly within the WB range, equalizing the reproduced bandwidth would be appropriate. The purpose of ULBC selection, however, is to identify the candidate that provides the best overall end-to-end user experience and service performance for the target use cases under the agreed-upon common constraints. Under this objective, reproduced audio bandwidth is a legitimate performance dimension, provided that all candidates are subject to the same resource limits, test procedures, and decision rules. Therefore, fairness should be achieved through common inputs, common processing rules, common resource limits, reference conditions within the same experiment, and a common decision rule. Requiring identical bandwidth would instead remove a legitimate performance dimension.

<a id="P031"></a>

Schedule and test cost: A common interface and one unified set of requirements are simpler than duplicated WB and SWB branches, and avoid a new FoM-weighing discussion.

<a id="P032"></a>

Terminal bandwidth: Some devices or interworking paths may limit bandwidth, while headsets, hands-free terminals, and future devices may benefit from SSWB or SWB. The most important thing is to select the system with the best trade-off between performance and quality.

<a id="P034"></a>

Conclusion and proposals

<a id="P038"></a>

The source proposes the following:

<a id="P039"></a>

Proposal 1: A common 32 kHz PCM input/output interface shall be used for ULBC qualification and selection.

<a id="P040"></a>

Proposal 2: Internal sampling rate and sampling-rate conversion shall be the proponent's design choice. Candidate-specific conversion, additionally required for supporting 32 kHz input, shall be reported separately in the submitted processing chain and in the applicable complexity, memory, and delay budget when it is purely extra.

<a id="P041"></a>

Proposal 3: Every candidate shall support at least WB audio. The maximum coded audio bandwidth may be WB, SSWB, or SWB and shall be a design choice of the proponent. It may differ between the two mandatory bitrate operating points.

<a id="P042"></a>

Proposal 4: ULBC-3 shall define a single set of performance requirements applicable regardless of the candidate audio bandwidth. Separate WB and SWB pass/fail branches shall not be introduced to limit the testing complexity.

<a id="P043"></a>

Proposal 5: Candidate and applicable reference conditions shall be assessed within the same subjective experiment. The candidate bandwidth shall be declared and reported, but shall not determine a separate qualification branch.

<a id="P045"></a>

Proposed changes to ULBC-4

<a id="P047"></a>

Proposed Sampling Frequency and Audio bandwidth.

<a id="T048"></a>

<a id="T048-R01"></a>
**T048-R01**

- <a id="T048-R01-C01"></a>列 1: Parameter
- <a id="T048-R01-C02"></a>列 2: Design constraint
- <a id="T048-R01-C03"></a>列 3: Note

<a id="T048-R02"></a>
**T048-R02**

- <a id="T048-R02-C01"></a>列 1: Sampling Frequency
- <a id="T048-R02-C02"></a>列 2: The ULBC codec shall support PCM audio at the encoder input and at the decoder output at a sampling rate of 16 kHz or 32 kHz. <br><br>However, the ULBC candidate codec shall support PCM audio at encoder input and the decoder output at a sampling rate of 32 kHz for ULBC qualification and selection testing. The internal sampling rate and the use of sampling-rate conversion are design choices of the proponent. Any candidate-specific sampling-rate conversion additionally required between the external interface and the internal processing in the submitted candidate processing chain shall be reported separately from the applicable computational complexity, memory, and algorithmic-delay constraints when it is purely extra. Once the ULBC codec is selected, the native operating sampling frequency of the winning system will be that of the native. Therefore, no sampling conversion may be needed in the end.
- <a id="T048-R02-C03"></a>列 3: Editor's note: Competing proposals that ask for internal sampling rate being equal to input/output sampling rate (1567) vs. sampling-rate conversion being allowed but counted (1518).

<a id="T048-R03"></a>
**T048-R03**

- <a id="T048-R03-C01"></a>列 1: Audio bandwidth
- <a id="T048-R03-C02"></a>列 2: The ULBC codec shall achieve at least wideband (WB) audio. <br><br>- bandwidth design freedom assessed by evaluation.<br><br>Subject to the common ULBC design constraints and performance requirements, the maximum audio bandwidth of a candidate operating point may be WB, SSWB, or SWB, and is a design choice of the proponent. (The maximum audio bandwidth may differ between the two mandatory bitrate operating points.)<br>The proponent shall declare the maximum audio bandwidth for each mandatory bitrate operating point. A 32 kHz external input/output sampling rate shall not be interpreted as a requirement for SWB coding.
- <a id="T048-R03-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: the sample rate (e.g. 16 kHz, or 32 kHz) and whether super-wideband or fullband is required or optional are FFS.<br>TR 26.940 [1] evaluated various bandwidths; WB solutions at ~1 kb/s matched AMR-WB 12.65 kb/s on clean speech.<br><br>Bandwidth of the audio material to be detailed in ULBC-8a (1562, 1513)

<a id="P052"></a>

Proposed changes to ULBC-3

<a id="P054"></a>

General treatment of audio bandwidth

<a id="P055"></a>

The ULBC performance requirements shall apply irrespective of whether a candidate’s operating point provides WB, SSWB, or SWB audio bandwidth. Separate bandwidth-specific pass/fail branches shall not be defined.

<a id="P056"></a>

Candidate conditions, their applicable codecs, and direct reference conditions shall be included in the same subjective experiment.

<a id="P057"></a>

The detailed audio bandwidth of the source material and reference conditions shall be specified in the applicable test plan.

<a id="P059"></a>

Performance Requirements in mixed WB, SSWB, SWB clean and noisy (FER) conditions

<a id="P061"></a>

Table 2: ULBC requirements (for mixed WB, SSWB, SWB clean and noisy (FER))

<a id="T062"></a>

<a id="T062-R01"></a>
**T062-R01**

- <a id="T062-R01-C01"></a>列 1: Category
- <a id="T062-R01-C02"></a>列 2: Max. BW
- <a id="T062-R01-C03"></a>列 3: Bitrate (kbit/s)
- <a id="T062-R01-C04"></a>列 4: Bundling time
- <a id="T062-R01-C05"></a>列 5: FER
- <a id="T062-R01-C06"></a>列 6: DTX
- <a id="T062-R01-C07"></a>列 7: Requirements
- <a id="T062-R01-C08"></a>列 8: Objectives

<a id="T062-R02"></a>
**T062-R02**

- <a id="T062-R02-C01"></a>列 1（纵向合并:restart）: Clean speech<br>-26,-16,-36 dBov
- <a id="T062-R02-C02"></a>列 2（纵向合并:restart）: SWB/SSWB/WB
- <a id="T062-R02-C03"></a>列 3: 1.0
- <a id="T062-R02-C04"></a>列 4: [80ms/160ms]
- <a id="T062-R02-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T062-R02-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T062-R02-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T062-R02-C08"></a>列 8: NWT AMR-WB @ 12.65

<a id="T062-R03"></a>
**T062-R03**

- <a id="T062-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T062-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T062-R03-C03"></a>列 3: 1.4
- <a id="T062-R03-C04"></a>列 4: 80ms
- <a id="T062-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T062-R03-C06"></a>列 6（纵向合并:continue）: 
- <a id="T062-R03-C07"></a>列 7: NWT AMR-WB @ 12.65
- <a id="T062-R03-C08"></a>列 8: NWT EVS-WB 13.2 kbps

<a id="T062-R04"></a>
**T062-R04**

- <a id="T062-R04-C01"></a>列 1（纵向合并:restart）: Clean speech<br> -26 dBov
- <a id="T062-R04-C02"></a>列 2（纵向合并:restart）: SWB/SSWB/WB
- <a id="T062-R04-C03"></a>列 3: 1.0
- <a id="T062-R04-C04"></a>列 4: [80ms/160ms]
- <a id="T062-R04-C05"></a>列 5（纵向合并:restart）: x=2%, 6% <br>x=1%, 6% <br>x=[1%, 2% 6%, 10%]
- <a id="T062-R04-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T062-R04-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T062-R04-C08"></a>列 8: NWT AMR-WB @ 12.65

<a id="T062-R05"></a>
**T062-R05**

- <a id="T062-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T062-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T062-R05-C03"></a>列 3: 1.4
- <a id="T062-R05-C04"></a>列 4: 80ms
- <a id="T062-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T062-R05-C06"></a>列 6（纵向合并:continue）: 
- <a id="T062-R05-C07"></a>列 7: NWT AMR-WB @ 12.65@x FER
- <a id="T062-R05-C08"></a>列 8: NWT EVS-WB 13.2 kbps@x FER

<a id="T062-R06"></a>
**T062-R06**

- <a id="T062-R06-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov, <br>SNR=20dB<br>Noisy speech (Car, Street)<br>-26dBov
- <a id="T062-R06-C02"></a>列 2（纵向合并:restart）: SWB/SSWB/WB
- <a id="T062-R06-C03"></a>列 3: 1.0
- <a id="T062-R06-C04"></a>列 4: [80ms/160ms]
- <a id="T062-R06-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T062-R06-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T062-R06-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T062-R06-C08"></a>列 8: NWT AMR-WB @ 12.65

<a id="T062-R07"></a>
**T062-R07**

- <a id="T062-R07-C01"></a>列 1（纵向合并:continue）: 
- <a id="T062-R07-C02"></a>列 2（纵向合并:continue）: 
- <a id="T062-R07-C03"></a>列 3: 1.4
- <a id="T062-R07-C04"></a>列 4: 80ms
- <a id="T062-R07-C05"></a>列 5（纵向合并:continue）: 
- <a id="T062-R07-C06"></a>列 6（纵向合并:continue）: 
- <a id="T062-R07-C07"></a>列 7: NWT AMR-WB @ 12.65
- <a id="T062-R07-C08"></a>列 8: NWT EVS-WB 13.2 kbps

<a id="T062-R08"></a>
**T062-R08**

- <a id="T062-R08-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov, <br>SNR=20dB <br>Noisy speech (Car, Street)<br>-26dBov
- <a id="T062-R08-C02"></a>列 2（纵向合并:restart）: SWB/SSWB/WB
- <a id="T062-R08-C03"></a>列 3: 1.0
- <a id="T062-R08-C04"></a>列 4: [80ms/160ms]
- <a id="T062-R08-C05"></a>列 5（纵向合并:restart）: x=2%, 6% <br>x=1%, 6%<br>x=[1%, 2% 6%, 10%]
- <a id="T062-R08-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T062-R08-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T062-R08-C08"></a>列 8: NWT AMR-WB @ 12.65

<a id="T062-R09"></a>
**T062-R09**

- <a id="T062-R09-C01"></a>列 1（纵向合并:continue）: 
- <a id="T062-R09-C02"></a>列 2（纵向合并:continue）: 
- <a id="T062-R09-C03"></a>列 3: 1.4
- <a id="T062-R09-C04"></a>列 4: 80ms
- <a id="T062-R09-C05"></a>列 5（纵向合并:continue）: 
- <a id="T062-R09-C06"></a>列 6（纵向合并:continue）: 
- <a id="T062-R09-C07"></a>列 7: NWT AMR-WB @ 12.65@x FER
- <a id="T062-R09-C08"></a>列 8: NWT EVS-WB 13.2 kbps@x FER

<a id="T062-R10"></a>
**T062-R10**

- <a id="T062-R10-C01"></a>列 1（纵向合并:restart）: Mixed content and music<br>single level
- <a id="T062-R10-C02"></a>列 2: SWB/SSWB/WB
- <a id="T062-R10-C03"></a>列 3: 1.0
- <a id="T062-R10-C04"></a>列 4: [80ms/160ms]
- <a id="T062-R10-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T062-R10-C06"></a>列 6（纵向合并:restart）: On/Off
- <a id="T062-R10-C07"></a>列 7: Graceful behaviour<sup>‡</sup>
- <a id="T062-R10-C08"></a>列 8: 

<a id="T062-R11"></a>
**T062-R11**

- <a id="T062-R11-C01"></a>列 1（纵向合并:continue）: 
- <a id="T062-R11-C02"></a>列 2: SWB/SSWB/WB
- <a id="T062-R11-C03"></a>列 3: 1.4
- <a id="T062-R11-C04"></a>列 4: 80ms
- <a id="T062-R11-C05"></a>列 5（纵向合并:continue）: 
- <a id="T062-R11-C06"></a>列 6（纵向合并:continue）: 
- <a id="T062-R11-C07"></a>列 7: Graceful behaviour<sup>‡</sup>
- <a id="T062-R11-C08"></a>列 8: 

<a id="P064"></a>

Notes:

<a id="P065"></a>

<sup>† </sup>Reference codecs with DTX on

<a id="P066"></a>

[<sup>‡</sup> Graceful behaviour means …]

<a id="P067"></a>

The FER conditions are simulated with packet loss patterns representative of relevant NB-IoT NTN over GEO channel characteristics at the given FER x. The packet loss patterns are derived according to the principles laid out in TR 26.940.

<a id="P068"></a>

It is anticipated that the compliance of the ULBC with the performance requirement for mixed content and music will be checked during characterization.

<a id="P072"></a>

References

<a id="P073"></a>

3GPP, “Study on Ultra Low Bit rate Speech Codecs (Release 20),” TR 26.940 V20.0.0 (2026-06), June 2026.

<a id="P074"></a>

ULBC-3 Editor, “[ULBC-MED] ULBC Performance Requirements (ULBC-3), Version 0.1.0,” S4-261771, 3GPP TSG SA4 Meeting #137-e, 24 – 28 August 2026, Online.

<a id="P075"></a>

ULBC-4 Editor, “[ULBC-MED] ULBC Design Constraints (ULBC-4), Version 0.2.0,” S4-261739, 3GPP TSG SA4 Meeting #137-e, 24 – 28 August 2026, Online.

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH                　　Tdoc S4aA260101<br>Shanghai, China, September 28-30, 2026
