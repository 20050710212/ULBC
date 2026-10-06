# S4aA260169 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260169_[ULBC-MED] On perspective of rate and_or bundling switching.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Meeting#137ad    S4aA260169

<a id="P001"></a>

Shanghai, P.R.China, 28-30 September 2026    (revision of S4aA260096, 0164)

<a id="P003"></a>

Source:    vivo Mobile Communication Co.,Ltd, Qualcomm Japan LLC

<a id="P004"></a>

Title:    [ULBC-MED] On perspective of rate and/or bundling switching

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

Two forms of in-session adaptation are supported by the previous 3GPP speech codecs.

<a id="P011"></a>

Rate switching is supported. In EVS the bit rate, or the bit rate range, is negotiated in the SDP offer and answer through the br media type parameter carried in the a=fmtp attribute, and within what has been negotiated a Codec Mode Request selects the bit rate during the session [4]. Its purpose is to let the encoder follow the state of the transmission link, lowering the bit rate to buy robustness when the link degrades and returning when it recovers.

<a id="P012"></a>

Bundling switching is supported, whose purpose is different from that of rate switching. Frame aggregation reduces the IP/UDP/RTP overhead by carrying more speech frames in one packet, and it is applied as a packet rate back-off when the operating conditions are packet rate limited and the codec bit rate can no longer be reduced [5], clauses 18.5 and 18.7.

<a id="P013"></a>

TS 26.114 refers to it as frame aggregation and defines an in-session request for it:

<a id="T014"></a>

<a id="T014-R01"></a>
**T014-R01**

- <a id="T014-R01-C01"></a>列 1: "RTCP_APP_REQ_AGG: Request for a change of frame aggregation."<br>- TS 26.114 [5], clause 10.2.1.4

<a id="P016"></a>

ULBC-4 [2] does not yet state whether ULBC supports rate switching and bundling switching for active speech during a session. This contribution addresses both and proposes the corresponding text for ULBC-4.

<a id="P017"></a>

## 2    Discussion

<a id="P018"></a>

## 2.1    The three ULBC operating points and the possible switches

<a id="P019"></a>

In EVS the bit rate and the packetisation interval are independent parameters, and either may be adapted without affecting the other. In ULBC they are paired: 1.0 kbps is realised by TBS 224 at 160 ms bundling and 1.4 kbps by TBS 176 at 80 ms bundling. There are 3 operating points, the third of which is not yet resolved.

<a id="P020"></a>

Table 1: ULBC operating points

<a id="T021"></a>

<a id="T021-R01"></a>
**T021-R01**

- <a id="T021-R01-C01"></a>列 1: Operating point
- <a id="T021-R01-C02"></a>列 2: Bit rate
- <a id="T021-R01-C03"></a>列 3: Bundling period
- <a id="T021-R01-C04"></a>列 4: Transport block size [7]

<a id="T021-R02"></a>
**T021-R02**

- <a id="T021-R02-C01"></a>列 1: Capacity point
- <a id="T021-R02-C02"></a>列 2: 1.0 kbps
- <a id="T021-R02-C03"></a>列 3: 160 ms
- <a id="T021-R02-C04"></a>列 4: TBS 224

<a id="T021-R03"></a>
**T021-R03**

- <a id="T021-R03-C01"></a>列 1: Quality point
- <a id="T021-R03-C02"></a>列 2: 1.4 kbps
- <a id="T021-R03-C03"></a>列 3: 80 ms
- <a id="T021-R03-C04"></a>列 4: TBS 176

<a id="T021-R04"></a>
**T021-R04**

- <a id="T021-R04-C01"></a>列 1: [ Third point
- <a id="T021-R04-C02"></a>列 2: 1.0 kbps
- <a id="T021-R04-C03"></a>列 3: 80 ms
- <a id="T021-R04-C04"></a>列 4: TBS 144 ]

<a id="P023"></a>

Case#1: rate switching only, at 80 ms bundling, between 1.4 kbps and 1.0 kbps.

<a id="P024"></a>

Case#2: bundling switching only, at 1.0 kbps, between 160 ms and 80 ms.

<a id="P025"></a>

Case#3: rate and bundling switching together, i.e. between 1.4 kbps with 80 ms and 1.0 kbps with 160 ms.

<a id="P026"></a>

NOTE: Case#1 is addressed in clause 2.2 and case#2 in clause 2.3. Case#3 is the combination of the two and is therefore subject to both.

<a id="P027"></a>

## 2.2    Case#1: rate switching

<a id="P028"></a>

The benefit of rate switching depends on the transmission link changing within a session. On a GEO link it does not. The satellite is geostationary, so the elevation angle, the slant range and the free-space path loss are constant for the duration of the session and the Doppler contribution due to satellite motion is negligible [6]. The UE antenna gain, the additional loss and the power class are properties of the device and its deployment. The conditions that determine which bit rate is appropriate are therefore fixed at session setup.

<a id="P029"></a>

The remaining variation is local blockage. Blockage shorter than the adaptation loop delay, approximately 540 ms between UE and gNB over a bent-pipe GEO link [6], has ended before a new bit rate takes effect. Blockage of a longer duration is a coverage outage, which a change of 0.4 kbps does not resolve.

<a id="P030"></a>

Realisation is also more difficult than in the codecs for which rate switching was defined. The Codec Mode Request is end-to-end feedback from the far-end receiver [4]. The constraint that would trigger a change in ULBC is the uplink budget of the sending UE. No interface is defined between the NB-IoT NTN radio layer and the codec by which the lower layer could indicate that condition to the upper layer, and such a mechanism would have to be introduced first.

<a id="P031"></a>

The capacity and quality difference between the two operating points is given in Annex B for reference.

<a id="P032"></a>

Observation#1: the conditions under which rate switching was introduced do not apply to ULBC, since the transmission link does not change materially within a session, and its realisation would require an interface between the radio layer and the codec that is not defined.

<a id="P033"></a>

Proposal#1: Rate switching between the ULBC bit rates within a session is not supported. The codec bit rate is fixed for the duration of a session.

<a id="P034"></a>

## 2.3    Case#2: bundling switching

<a id="P035"></a>

The benefit of bundling switching does not apply to ULBC either, for two reasons.

<a id="P036"></a>

First, the frame aggregation is used in the increasing direction, as a packet rate back-off, and a request in the decreasing direction may be rejected:

<a id="T037"></a>

<a id="T037-R01"></a>
**T037-R01**

- <a id="T037-R01-C01"></a>列 1: "Request completely ignored: An example is a request for 1 frame/packet which might be rejected as the MTSI client decides that the default mode of operation 2 frames/packet or more and a frame aggregation reduction compared to the default state is not allowed."<br>- TS 26.114 [5], Annex C

<a id="P039"></a>

Second, ROHC is used in an IP deployment, and a change of bundling period works against the overhead reduction that frame aggregation is intended to provide. ROHC compresses the RTP timestamp using the timestamp stride, which is part of the compression context [12]:

<a id="T040"></a>

<a id="T040-R01"></a>
**T040-R01**

- <a id="T040-R01-C01"></a>列 1: "The timestamp stride (TS_STRIDE) is the expected increase in the timestamp value between two RTP packets with consecutive sequence numbers."<br>- RFC 3095 [12], clause 3.1

<a id="P042"></a>

A change in the number of speech frames per packet changes the increase between consecutive packets. The established stride no longer applies and the dynamic part of the context is re-initialised, during which the compressed header is larger. TS 26.114 states the same conclusion for this configuration:

<a id="T043"></a>

<a id="T043-R01"></a>
**T043-R01**

- <a id="T043-R01-C01"></a>列 1: "It is then possible to use frame aggregation to reduce the IP/UDP/RTP overhead. However, if the limitation is in the RAN, where ROHC is used, then this will have limited effect, possibly even no effect at all."<br>- TS 26.114 [5], clause 19.2, NOTE 2

<a id="P045"></a>

Realisation is also difficult. The request is carried in RTCP-APP [5]. RFC 3550 recommends that the fraction of the session bandwidth added for RTCP be fixed at 5%, with one quarter dedicated to data senders, and the minimum report interval can be reduced only above 72 kb/s:

<a id="T046"></a>

<a id="T046-R01"></a>
**T046-R01**

- <a id="T046-R01-C01"></a>列 1: "The RECOMMENDED value for the reduced minimum in seconds is 360 divided by the session bandwidth in kilobits/second. This minimum is smaller than 5 seconds for bandwidths greater than 72 kb/s."<br>- RFC 3550 [9], clause 6.2

<a id="P048"></a>

A ULBC session is of the order of at most 3 kbit/s, so the report interval cannot be reduced below the 5 second default and the RTCP share is a few tens of bit/s. TS 26.114 further notes that reception of RTCP-APP packets is not guaranteed and that they may be delayed [5].

<a id="P049"></a>

The capacity and quality difference between the two bundling periods is given in Annex B for reference.

<a id="P050"></a>

Observation#2: the conditions under which frame aggregation was introduced do not apply to ULBC, since the changing direction required may be refused by the sender and a change of bundling period lengthens the compressed header instead of shortening it, and its realisation would require an RTCP feedback path that a link of 1 to 2 kbit/s cannot provide.

<a id="P051"></a>

Proposal#2: Bundling switching within a session is not supported. The bundling period is fixed for the duration of a session.

<a id="P052"></a>

## 3    Proposal

<a id="P053"></a>

Based on Proposals 1 and 2, the bit rate and bundling rows of ULBC-4 (S4-261847) are proposed to be updated as follows:

<a id="P054"></a>

==============First change==============

<a id="T056"></a>

<a id="T056-R01"></a>
**T056-R01**

- <a id="T056-R01-C01"></a>列 1: Bit rates
- <a id="T056-R01-C02"></a>列 2: The ULBC codec shall operate at the two bit rates 1.0 and 1.4kbps. [ Editor's note: Bitrates are gross bit rates for the ULBC payload comprising the codec payload header and the speech bits, excluding the protocol headers (e.g. RTP, UDP, ...) ]
- <a id="T056-R01-C03"></a>列 3: Agreed WID objective [1].<br>The codec bit rate is fixed for the duration of a session.<br><br>Editor's note: One vs two operating points and the specific rate(s) were FFS (no study-phase conclusion) at SA4#136. At SP#112 it was concluded that two rates shall be provided.

<a id="T056-R02"></a>
**T056-R02**

- <a id="T056-R02-C01"></a>列 1: Bundling
- <a id="T056-R02-C02"></a>列 2: [ The ULBC codec packetization shall support bundling for 80ms and 160ms and be able to packetize/depacketize the frames to fit the bundling periods.]
- <a id="T056-R02-C03"></a>列 3: The bundling period is fixed for the duration of a session.<br>Editor’s: note: For selection testing, 1.0 kbps will be operated with 160 ms bundling and 1.4 kbps will be operated with 80 ms bundling.<br>Editor's note: This reflects a=ptime

<a id="T056-R03"></a>
**T056-R03**

- <a id="T056-R03-C01"></a>列 1: Frame length
- <a id="T056-R03-C02"></a>列 2: [The codec frame length shall be one of 20, 40, 80 ms ]
- <a id="T056-R03-C03"></a>列 3: 

<a id="P057"></a>

==============End of change==============

<a id="P059"></a>

## 4    References

<a id="P060"></a>

[1]    SP-260696, "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite", SA WG4, TSG SA#112, June 2026.

<a id="P061"></a>

[2]    S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4)", v0.2.1, Fraunhofer IIS (Interim ULBC-4 Editor), SA4#137-e, August 2026.

<a id="P062"></a>

[3]    IETF RFC 4867, "RTP Payload Format and File Storage Format for the Adaptive Multi-Rate (AMR) and Adaptive Multi-Rate Wideband (AMR-WB) Audio Codecs", clauses 4.3 and 4.4 (payload structure), clause 4.3.1 (Codec Mode Request).

<a id="P063"></a>

[4]    3GPP TS 26.445, "Codec for Enhanced Voice Services (EVS); Detailed algorithmic description", Annex A (EVS RTP payload format).

<a id="P064"></a>

[5]    3GPP TS 26.114, "IP Multimedia Subsystem (IMS); Multimedia Telephony; Media handling and interaction".

<a id="P065"></a>

[6]    3GPP TR 38.821, "Solutions for NR to support non-terrestrial networks (NTN)", clause 4.2 (GEO propagation delay and Doppler).

<a id="P066"></a>

[7]    cross-checked_RAN_simulation.xlsx, attachment to 3GPP TR 26.940, clause 5.3.5.

<a id="P067"></a>

[8]    S2-2605087, "LS with questions on IMS voice over NB-IoT NTN", SA2, June 2026.

<a id="P068"></a>

[9]    IETF RFC 3550, "RTP: A Transport Protocol for Real-Time Applications", clause 6.2.

<a id="P069"></a>

[10]    IETF RFC 4566, "SDP: Session Description Protocol", clause 6 (a=ptime, a=maxptime).

<a id="P070"></a>

[11]    S4-130127, "EVS Permanent Document #8a (EVS-8a): Qualification test plan", SA4#72, January 2013.

<a id="P071"></a>

[12]    IETF RFC 3095, "RObust Header Compression (ROHC): Framework and four profiles", clauses 3.1 and 4.5.3.

<a id="P072"></a>

[13]     S4-260522, " On perspective of codec bit rates"

<a id="P073"></a>

Annex A: Payload header structures of AMR, AMR-WB and EVS

<a id="P074"></a>

This annex collects the payload header formats of the previous 3GPP speech codecs, to support clause 1. In every case the Codec Mode Request field that carries the rate switching request is part of the payload header and is therefore taken from the codec budget [3], [4].

<a id="P076"></a>

Figure A.1: Payload header structures and field definitions

<a id="P077"></a>

Annex B: Capacity of the ULBC operating points

<a id="P078"></a>

This annex gives, for reference, the capacity difference associated with each of the three cases of clause 2.1. The values are taken from the cross-checked RAN simulations [7], vivo results, which are the only results covering all three combinations. Capacity is expressed in UEs per pair of UL and DL 200 kHz carriers, at 31 dBm and the 2% BLER target, for the four test cases in which the combinations concerned were simulated. The vertical label inside each bar is the lowest UE transmit power at which the operating point is feasible.

<a id="P080"></a>

Figure B.1: Case#1, rate switching at 80 ms bundling, 1.4 kbps against 1.0 kbps

<a id="P082"></a>

Figure B.2: Case#2, bundling switching at 1.0 kbps, 80 ms against 160 ms

<a id="P084"></a>

Figure B.3: Case#3, quality point against capacity point
