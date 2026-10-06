# S4aA260126 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260126_JBM.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWG on ULBC-MED    S4aA260126

<a id="P001"></a>

28-30 September 2026, Shanghai, China

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    [ULBC-MED] Jitter buffer management as a design constraint for ULBC

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Agreement

<a id="P007"></a>

Work Item:    ULBC-MED

<a id="P009"></a>

Introduction

<a id="P010"></a>

ULBC-4 v0.2.1 [1] contains, in square brackets, the design constraint “The ULBC candidate codecs shall support JBM”. S4-261717 [2] assumes negligible delay variation on the GEO radio link. This contribution accepts that radio-link assumption and shows that, even under constant radio propagation delay, IMS packet voice over NB-IoT GEO can present variable packet-arrival times at the receiving terminal because of packet transport and scheduling. The source therefore proposes retaining the constraint and evaluating each candidate JBM using representative packet-arrival patterns.

<a id="P011"></a>

Packet-arrival variation on the GEO bearer

<a id="P012"></a>

Service and radio assumptions

<a id="P013"></a>

Voice over NB-IoT GEO is an IMS packet service. The decoder receives RTP packets rather than a circuit-switched speech channel with a fixed end-to-end timing relationship, so a constant GEO propagation delay does not by itself give constant packet arrival times at the decoder.

<a id="P014"></a>

The source accepts the radio-link assumption of S4-261717 [2]. GEO propagation varies by less than 6 µs per minute, and TR 36.763 [3] records the delay variation of a GEO link as negligible. The effects below arise before that link, after it, or at its scheduling boundary.

<a id="P015"></a>

The evaluated bearer uses semi-persistent scheduling (SPS), consistent with the NB-IoT NTN voice work described in RP-261082 [4]. In the evaluated configuration, one transport occasion is configured per voice bundle, with a period P of 80 ms or 160 ms. The occasion follows the radio-frame clock and need not be phase-aligned with the RTP packet stream. If a packet reaches the downlink eNB after its configured occasion, it is carried at a later occasion; in the single-occasion configuration evaluated here, this adds one period P to its delivery time.

<a id="P016"></a>

Figures 1 and 4 use the non-IP transport mechanism described in clause 5.2.1 of TR 26.940 [5]. In the evaluated model, UDP/IP header removal and restoration (UHRR) leaves a reduced RTP header of constant size. This removes packet-size variation due to RoHC and isolates the timing effect of the configured occasion. The same scheduling-boundary effect also applies to the IP transport mechanism as long as each packet fits within the configured transport block; clause 3 discusses packets that do not.

<a id="P017"></a>

Table 1 lists the packet-arrival effects relevant to the JBM. It separates the near-constant radio propagation term from the variation that packet transport and scheduling add.

<a id="P018"></a>

Table 1: Packet-arrival effects at the receiving terminal

<a id="T019"></a>

<a id="T019-R01"></a>
**T019-R01**

- <a id="T019-R01-C01"></a>列 1: Source
- <a id="T019-R01-C02"></a>列 2: Direction
- <a id="T019-R01-C03"></a>列 3: Packet-arrival effect
- <a id="T019-R01-C04"></a>列 4: JBM-relevant result

<a id="T019-R02"></a>
**T019-R02**

- <a id="T019-R02-C01"></a>列 1: GEO propagation
- <a id="T019-R02-C02"></a>列 2: both
- <a id="T019-R02-C03"></a>列 3: less than 6 µs variation per minute
- <a id="T019-R02-C04"></a>列 4: negligible

<a id="T019-R03"></a>
**T019-R03**

- <a id="T019-R03-C01"></a>列 1: Core-network or transcoder timing relative to the downlink SPS occasion
- <a id="T019-R03-C02"></a>列 2: downlink
- <a id="T019-R03-C03"></a>列 3: packet misses its occasion
- <a id="T019-R03-C04"></a>列 4: step of one P

<a id="T019-R04"></a>
**T019-R04**

- <a id="T019-R04-C01"></a>列 1: Clock difference between packet source and eNB
- <a id="T019-R04-C02"></a>列 2: downlink
- <a id="T019-R04-C03"></a>列 3: arrival phase moves slowly
- <a id="T019-R04-C04"></a>列 4: ramp, then a step of one P

<a id="T019-R05"></a>
**T019-R05**

- <a id="T019-R05-C01"></a>列 1: SPS activation or re-activation
- <a id="T019-R05-C02"></a>列 2: either
- <a id="T019-R05-C03"></a>列 3: the occasion obtains a new phase
- <a id="T019-R05-C04"></a>列 4: step of 0 to P

<a id="T019-R06"></a>
**T019-R06**

- <a id="T019-R06-C01"></a>列 1: RoHC context or talkspurt event
- <a id="T019-R06-C02"></a>列 2: either
- <a id="T019-R06-C03"></a>列 3: packet exceeds the steady-state transport block
- <a id="T019-R06-C04"></a>列 4: one or more further occasions, unless RAN specifies another procedure

<a id="P021"></a>

Downlink scheduling steps

<a id="P022"></a>

The source simulated a relayed call over an uplink SPS leg, a core-network term and an independently timed downlink SPS leg. The radio link was lossless and its propagation delay constant. Figure 1 shows the delay of the downlink leg.

<a id="P023"></a>

For the simulated 250-packet sequence, with uniformly distributed core-network jitter of ±3 ms and a nominal 2 ms margin before the downlink occasion, 248 packets were delivered one 160 ms period later than the baseline. With uniformly distributed jitter of ±20 ms and an 18 ms nominal margin, 213 packets were delivered one period later. Once a packet is shifted to the next occasion, the following packet may compete for that occasion; in the evaluated single-occasion model, the delay step can therefore persist for the remainder of the talkspurt.

<a id="P025"></a>

Figure 1: Downlink leg delay in the simulated relayed call: (a) core-network jitter against the downlink occasion, (b) network-side packet source running 50 ppm slow

<a id="P026"></a>

A small clock difference between the RTP packet source and the eNB produces the same step. The arrival phase moves gradually until a packet misses its occasion. Figure 1(b) shows that crossing, and the 160 ms step it costs, for a source running 50 ppm slow. Clause 8.2.2 of TS 26.114 [6] requires every speech JBM to handle clock drift between the encoding and decoding end-points.

<a id="P027"></a>

SPS re-activation

<a id="P028"></a>

SPS activation, release and a change of periodicity each give the occasion a new phase, unrelated to the phase of the RTP packet stream. Figure 2 shows the distribution of the resulting step for independent old and new phases.

<a id="P029"></a>

For independent old and new SPS phases uniformly distributed over one 160 ms period, 39 % of re-activations change the delivered delay by more than 60 ms. This 60 ms value is also used in clause 8.2.3.2.2 of TS 26.114 [6] when shifting the CDF of the reference delay-computation algorithm to derive the threshold for a JBM under test. The two quantities arise in different contexts, but the comparison shows that an SPS re-activation can create a delay change of a magnitude relevant to JBM evaluation, even when GEO propagation-delay variation is negligible.

<a id="P031"></a>

Figure 2: Step in delivered delay at an SPS (re-)activation, for independent old and new phases

<a id="P032"></a>

RoHC packet-size events

<a id="P033"></a>

Steady state and exceptional packets

<a id="P034"></a>

Clause 5.2.1 of TR 26.940 [5] requires support for the IP transport mechanism and recommends RoHC. In the configuration the source measured for the companion contribution on the IP transport mechanism, the steady-state RoHC header is 3 octets. Three events produce a larger packet.

<a id="P035"></a>

In the measured configuration, an initialisation and refresh (IR) packet establishes the context, with a 41-octet compressed header for IPv4 and a 64-octet compressed header for IPv6. A STATIC-NACK from the decompressor triggers another IR packet, whereas a NACK triggers an IR-DYN packet. At talkspurt onset, the relationship between the RTP timestamp increment and the sequence-number increment changes; in the measurements this increased the compressed header to 4 or 6 octets.

<a id="P036"></a>

In seven of the eight measured combinations of codec bitrate, bundling period and pause length, a transport block sized for steady-state packets was insufficient for the packet at talkspurt onset. In the same configuration, an IR packet required capacity equivalent to two to five configured occasions. The actual delivery time depends on the RAN procedure used for such packets; these measurements establish the size mismatch but do not by themselves specify the resulting delay.

<a id="P037"></a>

Figure 3 gives the measured header sizes. The 3-octet steady state applies to neither context establishment, context repair nor talkspurt onset. The figure assigns no delivered delay to the larger packets, because the procedure that carries them is not specified.

<a id="P039"></a>

Figure 3: Measured RoHC header sizes for the evaluated IP configuration, profile 0x0001 on CID 0

<a id="P040"></a>

Effect on JBM input

<a id="P041"></a>

RAN2 has identified variable-size voice packets and silent periods as scheduling issues for NB-IoT NTN [7]. In the material reviewed for this contribution, no agreed procedure was identified for carrying a media or RoHC packet that exceeds the configured SPS transport block, in either direction.

<a id="P042"></a>

Possible RAN procedures include segmenting the packet across later occasions, providing a supplementary grant, configuring a larger transport block, or using a shorter SPS period. These alternatives would produce different packet-arrival times. The RAN procedure is outside SA4’s remit, but the JBM evaluation should use the packet-arrival transient produced by the procedure ultimately specified.

<a id="P043"></a>

Observation 1: RoHC context establishment, context repair and talkspurt onset each create a packet-arrival transient. Assuming negligible jitter on the GEO radio link does not remove these events from the JBM input.

<a id="P044"></a>

Dynamic scheduling

<a id="P045"></a>

A dynamically scheduled downlink has no fixed occasion. The eNB schedules each packet after it arrives, subject to the timing of the control channel. Figure 4 compares the delivered delay of the two schemes on the simulated chain, with the constant-size header of clause 2.1.

<a id="P046"></a>

In the evaluated downlink model, dynamic scheduling removed the one-period step. With uniformly distributed core-network jitter of ±20 ms, the SPS case had a mean delivered delay of 457 ms. Dynamic scheduling delivered packets at 285 ms when the UE monitored the relevant control occasion, and between 289 ms and 353 ms when the search-space period was 64 subframes. In the evaluated uplink cases, dynamic scheduling did not provide the same benefit: a pre-assigned downlink control indication per block remained within 25 ms of the aligned SPS case for search-space periods up to 64 subframes, whereas the reactive grant-request procedure added 850 ms to the mean delay and produced a 626 ms range. In that reactive model, each grant is received one assumed GEO round-trip time of 560 ms after the buffer-status report that requests it.

<a id="P048"></a>

Figure 4: Delivered delay under semi-persistent and dynamic scheduling: (a) uplink leg, (b) downlink leg with ±20 ms of core jitter

<a id="P049"></a>

Dynamic scheduling also consumes downlink control resources for each packet, while NB-IoT time-multiplexes control and data on the same carrier. Applying the capacity model of S4-261174 [8] and charging this control time, the evaluated anchor-carrier pair supports 6, 5 and 4 UEs for downlink DCI repetition levels of 1, 4 and 8, respectively, compared with 7 UEs for SPS. These figures are specific to the assumptions of that capacity model. The choice between SPS and dynamic scheduling is a RAN and system-design matter; neither choice removes the need to characterize the packet-arrival process seen by the JBM.

<a id="P050"></a>

Conclusion

<a id="P051"></a>

Negligible variation in GEO propagation delay does not imply constant RTP packet-arrival times at the decoder. In the evaluated configurations, scheduling boundaries, clock difference, SPS re-activation and RoHC-related packet-size events produce steps, ramps and discrete transients at the JBM input. TS 26.114 [6] already requires a speech JBM and requires handling of clock drift between the encoding and decoding end-points. ULBC should therefore retain the JBM design constraint and evaluate candidate codecs using packet-arrival patterns that cover the effects summarized in Table 1.

<a id="P052"></a>

Proposal

<a id="P053"></a>

Proposal 1: Remove the square brackets from the JBM design constraint in ULBC-4 and retain the text: “The ULBC candidate codecs shall support JBM.”

<a id="P054"></a>

Proposal 2: Consider asking RAN2 to clarify the handling and the timing of media and RoHC packets larger than the SPS transport block in each direction, and to make the resulting packet-arrival behaviour available for SA4 JBM evaluation.

<a id="P055"></a>

References

<a id="P056"></a>

S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.1", Fraunhofer IIS (ULBC-4 Editor), SA4#137-e.

<a id="P057"></a>

S4-261717, "[ULBC-MED] ULBC-9: Assumptions for RTP header reduction and MTSI integration", Qualcomm, SA4#137-e.

<a id="P058"></a>

3GPP TR 36.763: "Study on Narrow-Band Internet of Things (NB-IoT) / enhanced Machine Type Communication (eMTC) support for Non-Terrestrial Networks (NTN)".

<a id="P059"></a>

RP-261082, "Status report for WI Core part: Non-Terrestrial Networks (NTN) for Internet of Things (IoT) Phase 4", vivo, TSG RAN#112.

<a id="P060"></a>

3GPP TR 26.940: "Study on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite".

<a id="P061"></a>

3GPP TS 26.114: "IP Multimedia Subsystem (IMS); Multimedia Telephony; Media handling and interaction".

<a id="P062"></a>

R2-2600884, "NB-IoT NTN voice over GSO adaptations", Ericsson, RAN2#133.

<a id="P063"></a>

S4-261174, "[FS_ULBC] Cross-checked RAN simulation results for ULBC", Qualcomm Japan, vivo, Xiaomi, Huawei, SA4#136.
