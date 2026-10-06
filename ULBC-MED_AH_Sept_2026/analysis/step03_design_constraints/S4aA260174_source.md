# S4aA260174 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260174 [ULBC-MED] RTP header field analysis and transport overhead.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260174 rev of S4aA260104

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] RTP header field analysis and transport overhead

<a id="P005"></a>

Spec:    ULBC-9

<a id="P006"></a>

Agenda item:    4.9

<a id="P007"></a>

Document for:    Agreement

<a id="P010"></a>

## 1.    Introduction

<a id="P011"></a>

The ULBC-MED Work Item [1] includes the objective of specifying an RTP payload format for the ULBC codec and determining the essential fields for RTP header reduction. At SA4#137-e, the skeleton of the corresponding permanent document ULBC-9 [2] was agreed, including placeholder clauses for the transport options and protocol overhead, and for a field-by-field analysis of the RTP header under the agreed service scope.

<a id="P012"></a>

This contribution provides proposed text for these clauses. The analysis reviews each RTP header field defined in RFC 3550 [5] against the constraints of the agreed service scope (IMS voice over NB-IoT (GEO)), and classifies each field as removed, compressed, or reconstructed, following the taxonomy of the ULBC-9 skeleton. The proposed text intentionally does not preselect a reduced RTP header format; format definition and SDP negotiation are addressed by separate clauses of ULBC-9 and are left for subsequent contributions.

<a id="P013"></a>

## 2.    Discussion

<a id="P014"></a>

## 2.1    Transport options and protocol overhead

<a id="P015"></a>

SA2 has agreed stage-2 support for IMS voice over NB-IoT (GEO), including UDP/IP Header Removal and Restoration (UHRR) in TS 23.401 [3] and RTP-header-optimized media negotiation in TS 23.228 [4]. Two transport configurations are therefore relevant to the ULBC media stream:

<a id="P016"></a>

IP-based transport, in which RTP/UDP/IP packets are carried over the radio bearer, optionally with RObust Header Compression (ROHC) [6] applied on the radio link; and

<a id="P017"></a>

UHRR-enabled transport, in which the UDP/IP headers are removed before transmission over the radio link and restored by the network, leaving the RTP header and payload on the radio link.

<a id="P018"></a>

At the ULBC gross bitrates of 1.0 and 1.4 kbit/s, protocol header overhead is not a secondary effect but a multiple of the media bitrate. At 1.0 kbit/s with 160 ms packetization, each packet carries a 20-octet ULBC payload; an uncompressed IPv4/UDP/RTP header (40 octets) alone corresponds to 2.0 kbit/s, i.e. 200% of the codec rate. The comparison across the transport configurations is summarized in the proposed text (clause 3, Table X.1).

<a id="P019"></a>

Two consequences follow. First, ROHC applies only to the IP-based transport and operates per link: it compresses the headers over the radio link but requires context establishment and repair between compressor and decompressor. Over a GEO link with a one-way delay in the order of 250–300 ms, context damage results in extended error propagation or costly context refresh with full-header packets. Second, and more importantly for SA4: under the UHRR-enabled transport, no IP or UDP header remains, but the uncompressed 12-octet RTP header still corresponds to 60% of the codec rate at 160 ms packetization (120% at 80 ms). UHRR alone therefore does not resolve the overhead problem; a reduction of the RTP header itself is required, which is the subject of the WID objective assigned to SA4.

<a id="P020"></a>

## 2.2    RTP header field analysis

<a id="P021"></a>

The applicability of RTP header reduction should be derived from the agreed service scope rather than from a generic transport scenario. The following service scope constraints are relevant:

<a id="P022"></a>

a single mono speech stream (one audio media description) per media transport session;

<a id="P023"></a>

a point-to-point media path between the UE and the network media endpoint on the leg where the reduced header applies; no RTP mixers or translators contribute to the stream on this leg;

<a id="P024"></a>

a single RTP payload format for ULBC per session, with payload format parameters established in SDP at session setup;

<a id="P025"></a>

a fixed codec frame length with fixed packetization/bundling times (80 ms or 160 ms), resulting in a constant nominal timestamp increment per packet during continuous transmission;

<a id="P026"></a>

FFS: DTX operation, DTMF events (RFC 4733 [7]), application-layer FEC (RFC 8627 [8]), and the handling of RTCP.

<a id="P027"></a>

Under these constraints, each field of the RFC 3550 RTP header is analysed in the proposed text (clause 3, Table X.2). The analysis leads to two observations:

<a id="P028"></a>

Observation 1: The fields V, P, X, CC, PT and SSRC (and M, pending the DTX discussion) are invariant for the lifetime of the session under the agreed service scope. Session-invariant fields do not need to be transmitted in every packet: their values can be established once at session establishment and are then known to both endpoints for the duration of the session.

<a id="P029"></a>

Observation 2: The remaining fields (SN, TS) are dynamic but highly predictable (if DTX is used, however, TS may be non-predictable). The new information conveyed per packet is limited to a small increment relative to state that both endpoints can maintain; a reduced header therefore needs to carry only enough information to detect packet loss and to resolve timing discontinuities, rather than the full 16-bit and 32-bit field values.

<a id="P030"></a>

These observations bound the design space for the reduced RTP header format(s) without preselecting a particular format: any candidate format can be assessed by which per-packet information it retains for the dynamic fields and how the session-invariant values are established.

<a id="P031"></a>

## 3.    Proposal

<a id="P032"></a>

It is proposed to agree the following:

<a id="P033"></a>

Proposal 1: Capture the transport options and protocol overhead comparison of clause 2.1 (Table X.1) in the ULBC-9 clause “Transport options and protocol overhead”.

<a id="P034"></a>

Proposal 2: Capture the service scope constraints, the field-by-field analysis (Table X.2) and Observations 1 and 2 in the ULBC-9 clause “RTP header field analysis”.

<a id="P035"></a>

The proposed text is provided below. Clause and table numbering follows the ULBC-9 skeleton [2] and is to be adapted by the editor.

<a id="P036"></a>

## 4.    Proposed text for ULBC-9

<a id="P037"></a>

* * * * Change 1 (all new text): Transport options and protocol overhead * * * *

<a id="P038"></a>

X    Transport of GEO voice and applicability of RTP header reduction

<a id="P039"></a>

X.2    Transport options and protocol overhead

<a id="P040"></a>

Two transport configurations are relevant to the ULBC media stream, in line with the stage-2 architecture agreed by SA2 [TS 23.401], [TS 23.228]:

<a id="P041"></a>

IP-based transport: RTP/UDP/IP packets are carried over the radio bearer. ROHC [RFC 3095] may be applied on the radio link, compressing the IP/UDP/RTP headers between the link-local compressor and decompressor.

<a id="P042"></a>

UHRR-enabled transport: the UDP/IP headers are removed before transmission over the radio link and restored by the network (UHRR). The RTP header and the RTP payload remain on the radio link.

<a id="P043"></a>

Table X.1 compares the protocol header overhead of the transport configurations for the ULBC codec operating at 1.0 kbit/s with 80 ms and 160 ms packetization. Percentages are relative to the 1.0 kbit/s gross codec bitrate.

<a id="P044"></a>

Table X.1: Protocol header overhead per transport configuration (ULBC at 1.0 kbit/s)

<a id="T045"></a>

<a id="T045-R01"></a>
**T045-R01**

- <a id="T045-R01-C01"></a>列 1: Protocol configuration
- <a id="T045-R01-C02"></a>列 2: Header size per packet
- <a id="T045-R01-C03"></a>列 3: Header overhead bitrate, 80 ms packetization
- <a id="T045-R01-C04"></a>列 4: Header overhead bitrate, 160 ms packetization

<a id="T045-R02"></a>
**T045-R02**

- <a id="T045-R02-C01"></a>列 1: IPv6/UDP/RTP, uncompressed
- <a id="T045-R02-C02"></a>列 2: 60 octets
- <a id="T045-R02-C03"></a>列 3: 6.0 kbit/s (600%)
- <a id="T045-R02-C04"></a>列 4: 3.0 kbit/s (300%)

<a id="T045-R03"></a>
**T045-R03**

- <a id="T045-R03-C01"></a>列 1: IPv4/UDP/RTP, uncompressed
- <a id="T045-R03-C02"></a>列 2: 40 octets
- <a id="T045-R03-C03"></a>列 3: 4.0 kbit/s (400%)
- <a id="T045-R03-C04"></a>列 4: 2.0 kbit/s (200%)

<a id="T045-R04"></a>
**T045-R04**

- <a id="T045-R04-C01"></a>列 1: IP-based transport with ROHC (steady state, NOTE 1)
- <a id="T045-R04-C02"></a>列 2: ~3–4 octets
- <a id="T045-R04-C03"></a>列 3: ~0.3–0.4 kbit/s (30–40%)
- <a id="T045-R04-C04"></a>列 4: ~0.15–0.2 kbit/s (15–20%)

<a id="T045-R05"></a>
**T045-R05**

- <a id="T045-R05-C01"></a>列 1: UHRR-enabled transport, uncompressed RTP header
- <a id="T045-R05-C02"></a>列 2: 12 octets
- <a id="T045-R05-C03"></a>列 3: 1.2 kbit/s (120%)
- <a id="T045-R05-C04"></a>列 4: 0.6 kbit/s (60%)

<a id="T045-R06"></a>
**T045-R06**

- <a id="T045-R06-C01"></a>列 1: UHRR-enabled transport, reduced RTP header
- <a id="T045-R06-C02"></a>列 2: 
- <a id="T045-R06-C03"></a>列 3: 
- <a id="T045-R06-C04"></a>列 4: 

<a id="P046"></a>

NOTE 1:    ROHC steady-state second-order state; context initialization and repair use larger context-establishing packets. ROHC operates per link and is applicable to the IP-based transport only.

<a id="P048"></a>

For the IP-based transport, ROHC reduces the header overhead in steady state, but context establishment and repair between the link-local compressor and decompressor are penalized by the GEO one-way delay in the order of 250–300 ms: context damage leads to extended packet discard or context refresh with full headers.

<a id="P049"></a>

For the UHRR-enabled transport, no IP or UDP header remains on the radio link; however, the uncompressed 12-octet RTP header alone corresponds to 60% of the codec rate at 160 ms packetization and 120% at 80 ms packetization. RTP header reduction is therefore necessary for the UHRR-enabled transport to preserve the payload budget available to the codec.

<a id="P050"></a>

* * * * Change 2 (all new text): RTP header field analysis * * * *

<a id="P051"></a>

To be considered for ULBC-9 editing

<a id="P052"></a>

Y    RTP header field analysis

<a id="P053"></a>

Y.1    Service scope constraints

<a id="P054"></a>

The analysis in this clause applies under the following constraints derived from the agreed service scope (IMS voice over NB-IoT (GEO)):

<a id="P055"></a>

a single mono speech stream (one audio media description) per media transport session;

<a id="P056"></a>

a point-to-point media path between the UE and the network media endpoint on the leg where the reduced header applies; no RTP mixers or translators contribute to the stream on this leg;

<a id="P057"></a>

a single ULBC payload format per session, with payload format parameters established in SDP at session setup;

<a id="P058"></a>

a fixed codec frame length with fixed packetization/bundling times (80 ms or 160 ms).

<a id="P059"></a>

Editor's note:    The applicability of DTX, DTMF events [RFC 4733], application-layer FEC [RFC 8627] and the handling of RTCP within the reduced-header service scope are FFS.

<a id="P060"></a>

Y.2    Field-by-field analysis

<a id="P061"></a>

Table X.2 reviews each field of the RTP fixed header [RFC 3550] and classifies it as removed, compressed, or reconstructed under the service scope constraints of clause Y.1.

<a id="P062"></a>

Table X.2: RTP header field analysis under the agreed service scope

<a id="T063"></a>

<a id="T063-R01"></a>
**T063-R01**

- <a id="T063-R01-C01"></a>列 1: RTP header field
- <a id="T063-R01-C02"></a>列 2: Size (bits)
- <a id="T063-R01-C03"></a>列 3: Function (RFC 3550)
- <a id="T063-R01-C04"></a>列 4: Analysis under the agreed service scope
- <a id="T063-R01-C05"></a>列 5: Classification

<a id="T063-R02"></a>
**T063-R02**

- <a id="T063-R02-C01"></a>列 1: version (V)
- <a id="T063-R02-C02"></a>列 2: 2
- <a id="T063-R02-C03"></a>列 3: RTP version; always 2 for RFC 3550.
- <a id="T063-R02-C04"></a>列 4: Constant for all packets of the session. The value is known a priori by both endpoints.
- <a id="T063-R02-C05"></a>列 5: Removed

<a id="T063-R03"></a>
**T063-R03**

- <a id="T063-R03-C01"></a>列 1: padding (P)
- <a id="T063-R03-C02"></a>列 2: 1
- <a id="T063-R03-C03"></a>列 3: Indicates presence of padding octets at the end of the payload.
- <a id="T063-R03-C04"></a>列 4: Padding is not required for speech payloads in the agreed service scope. If the absence of padding is established for the session, the field is invariant.
- <a id="T063-R03-C05"></a>列 5: Removed

<a id="T063-R04"></a>
**T063-R04**

- <a id="T063-R04-C01"></a>列 1: extension (X)
- <a id="T063-R04-C02"></a>列 2: 1
- <a id="T063-R04-C03"></a>列 3: Indicates presence of an RTP header extension.
- <a id="T063-R04-C04"></a>列 4: No RTP header extension is identified as necessary within the service scope. If the absence of header extensions is established for the session, the field is invariant.
- <a id="T063-R04-C05"></a>列 5: Removed

<a id="T063-R05"></a>
**T063-R05**

- <a id="T063-R05-C01"></a>列 1: CSRC count (CC)
- <a id="T063-R05-C02"></a>列 2: 4
- <a id="T063-R05-C03"></a>列 3: Number of CSRC identifiers following the fixed header.
- <a id="T063-R05-C04"></a>列 4: The media path is point-to-point between the UE and the network media endpoint; no RTP mixers contribute to the stream on this leg. CC is always 0 and no CSRC list is present.
- <a id="T063-R05-C05"></a>列 5: Removed

<a id="T063-R06"></a>
**T063-R06**

- <a id="T063-R06-C01"></a>列 1: marker (M)
- <a id="T063-R06-C02"></a>列 2: 1
- <a id="T063-R06-C03"></a>列 3: Profile-defined; for audio, typically set on the first packet after a silence interval (talk-spurt onset).
- <a id="T063-R06-C04"></a>列 4: Depends on deployment scenario and implementation aspects.
- <a id="T063-R06-C05"></a>列 5: FFS (Removed or retained)

<a id="T063-R07"></a>
**T063-R07**

- <a id="T063-R07-C01"></a>列 1: payload type (PT)
- <a id="T063-R07-C02"></a>列 2: 7
- <a id="T063-R07-C03"></a>列 3: Identifies the RTP payload format.
- <a id="T063-R07-C04"></a>列 4: A single ULBC payload type per media transport session is established in SDP; the value is invariant. NOTE: additional payload types (e.g. DTMF events per RFC 4733, FEC per RFC 8627) would require the PT information to be retained in some form; their applicability within the reduced-header service scope is FFS.
- <a id="T063-R07-C05"></a>列 5: Removed (single PT); FFS otherwise

<a id="T063-R08"></a>
**T063-R08**

- <a id="T063-R08-C01"></a>列 1: sequence number (SN)
- <a id="T063-R08-C02"></a>列 2: 16
- <a id="T063-R08-C03"></a>列 3: Increments by one per packet; used for loss detection and sequence restoration.
- <a id="T063-R08-C04"></a>列 4: Packet loss detection remains necessary over the GEO radio link. However, the new information per packet is limited to a small increment; long-term ambiguity can be resolved from session state. The full 16-bit field need not be carried in every packet.
- <a id="T063-R08-C05"></a>列 5: Compressed

<a id="T063-R09"></a>
**T063-R09**

- <a id="T063-R09-C01"></a>列 1: timestamp (TS)
- <a id="T063-R09-C02"></a>列 2: 32
- <a id="T063-R09-C03"></a>列 3: Sampling instant of the first octet of the media data.
- <a id="T063-R09-C04"></a>列 4: With a fixed codec frame length and a fixed packetization/bundling time, the TS advances by a constant nominal increment per packet and is largely derivable from the SN during continuous transmission. Discontinuities (e.g. across DTX gaps, if applicable) require explicit signalling of the increment.
- <a id="T063-R09-C05"></a>列 5: Compressed / reconstructed

<a id="T063-R10"></a>
**T063-R10**

- <a id="T063-R10-C01"></a>列 1: SSRC
- <a id="T063-R10-C02"></a>列 2: 32
- <a id="T063-R10-C03"></a>列 3: Identifies the synchronization source; enables demultiplexing of multiple RTP streams and collision detection.
- <a id="T063-R10-C04"></a>列 4: A single RTP stream is carried per media transport session, and the stream identity is unambiguously provided by the transport session / bearer context. SSRC-based demultiplexing and collision detection are not required on the point-to-point leg.
- <a id="T063-R10-C05"></a>列 5: Removed

<a id="T063-R11"></a>
**T063-R11**

- <a id="T063-R11-C01"></a>列 1: CSRC list
- <a id="T063-R11-C02"></a>列 2: 32 per entry
- <a id="T063-R11-C03"></a>列 3: Identifies contributing sources inserted by mixers.
- <a id="T063-R11-C04"></a>列 4: Not present, since CC = 0 (see above).
- <a id="T063-R11-C05"></a>列 5: Removed

<a id="P064"></a>

The analysis leads to the following observations:

<a id="P065"></a>

Observation 1: the fields V, P, X, CC, PT and SSRC (and M, pending the DTX discussion) are invariant for the lifetime of the session under the agreed service scope. Session-invariant fields do not need to be transmitted in every packet: their values can be established once at session establishment and are then known to both endpoints for the duration of the session.

<a id="P066"></a>

Observation 2: the remaining fields (SN, TS) are dynamic but highly predictable: the new information conveyed per packet is limited to a small increment relative to state that both endpoints can maintain. A reduced header needs to carry only enough information to detect packet loss and to resolve timing discontinuities, rather than the full 16-bit and 32-bit field values.

<a id="P067"></a>

* * * * End of Changes * * * *

<a id="P068"></a>

## 5.    References

<a id="P069"></a>

[1]    SP-260696, “New WID on Ultra Low Bitrate Speech Codec for Voice over GEO”.

<a id="P070"></a>

[2]    S4-261722, “ULBC RTP Header Reduction and System Integration (ULBC-9)”, v0.0.1.

<a id="P071"></a>

[3]    S2-2605080, “Support of IMS voice over NB-IoT(GEO)” (CR to TS 23.401), approved at SA2#175.

<a id="P072"></a>

[4]    S2-2605628, “GEO voice RTP header optimized media negotiation” (CR to TS 23.228), approved at SA2#175.

<a id="P073"></a>

[5]    IETF RFC 3550, “RTP: A Transport Protocol for Real-Time Applications”.

<a id="P074"></a>

[6]    IETF RFC 3095, “RObust Header Compression (ROHC)”.

<a id="P075"></a>

[7]    IETF RFC 4733, “RTP Payload for DTMF Digits, Telephony Tones, and Telephony Signals”.

<a id="P076"></a>

[8]    IETF RFC 8627, “RTP Payload Format for Flexible Forward Error Correction (FEC)”.
