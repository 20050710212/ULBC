# S4aA260124 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260124_IP_RoHC.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWG post 137    S4aA260124

<a id="P001"></a>

28-30 September 2026, Shanghai, China

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    [ULBC-MED] ULBC-9: IP transport mechanism and RoHC configuration

<a id="P005"></a>

Agenda item:    1.7

<a id="P006"></a>

Document for:    Agreement

<a id="P007"></a>

Work Item:    ULBC-MED

<a id="P009"></a>

Introduction

<a id="P010"></a>

TR 26.940 [1], clause 5.2.1, identifies two Layer-3 transport mechanisms for IMS voice over NB-IoT NTN. The IP mechanism is mandatory, and Robust Header Compression (RoHC) is recommended to reduce the RTP/UDP/IP header overhead. The non-IP mechanism is optional for both the UE and the network. However, the ULBC-9 skeleton in S4-261722 [2], agreed at SA4#137-e, contains text on reduced RTP headers and UHRR bearer aspects but does not identify the dependencies of the mandatory IP mechanism. This contribution therefore evaluates a possible IP/RoHC configuration, identifies the decisions required from other working groups, and proposes how SA4 should handle these dependencies before agreeing normative ULBC-9 text.

<a id="P011"></a>

Transport assumptions

<a id="P012"></a>

Table 1 summarizes the assumptions used in the evaluation. A transport block is the unit of data scheduled over the radio interface for one transmission opportunity. The access-stratum overhead is the combined PDCP, RLC and MAC overhead added below IP. Five of the six assumptions are taken from TR 26.940; the IP version is evaluated for both IPv4 and IPv6.

<a id="P013"></a>

Table 1: Transport assumptions and their sources

<a id="T014"></a>

<a id="T014-R01"></a>
**T014-R01**

- <a id="T014-R01-C01"></a>列 1: Field
- <a id="T014-R01-C02"></a>列 2: Value
- <a id="T014-R01-C03"></a>列 3: Source

<a id="T014-R02"></a>
**T014-R02**

- <a id="T014-R02-C01"></a>列 1: Transport
- <a id="T014-R02-C02"></a>列 2: IP over the user plane, one PDN connection
- <a id="T014-R02-C03"></a>列 3: TR 26.940 clause 5.2.1

<a id="T014-R03"></a>
**T014-R03**

- <a id="T014-R03-C01"></a>列 1: Compressed header
- <a id="T014-R03-C02"></a>列 2: RoHC profile 0x0001, 3 octets
- <a id="T014-R03-C03"></a>列 3: Evaluation assumption; TR 26.940 clause 5.2.3 assumes 3 octets

<a id="T014-R04"></a>
**T014-R04**

- <a id="T014-R04-C01"></a>列 1: Access stratum
- <a id="T014-R04-C02"></a>列 2: 5 octets: 1 PDCP, 1 RLC, 3 MAC
- <a id="T014-R04-C03"></a>列 3: TR 26.940 clause 5.2.3

<a id="T014-R05"></a>
**T014-R05**

- <a id="T014-R05-C01"></a>列 1: Transport block
- <a id="T014-R05-C02"></a>列 2: Smallest value of TS 36.213 [3] table 16.5.1.2-2 holding payload and overhead
- <a id="T014-R05-C03"></a>列 3: TR 26.940 clause 5.3.4

<a id="T014-R06"></a>
**T014-R06**

- <a id="T014-R06-C01"></a>列 1: Blocks per voice packet
- <a id="T014-R06-C02"></a>列 2: 1
- <a id="T014-R06-C03"></a>列 3: TR 26.940 clause 5.3.4, NOTE 1

<a id="T014-R07"></a>
**T014-R07**

- <a id="T014-R07-C01"></a>列 1: IP version
- <a id="T014-R07-C02"></a>列 2: IPv4 or IPv6, both evaluated
- <a id="T014-R07-C03"></a>列 3: This contribution, clause 3.3

<a id="P016"></a>

TR 26.940, clause 5.2.3, assumes 8 octets of protocol overhead for IP transport: 3 octets for RoHC and 5 octets for the radio-protocol layers (1 PDCP, 1 RLC and 3 MAC). This contribution uses the same 8-octet budget. The RoHC measurement in clause 3.3 confirms the 3-octet steady-state value. The 3-octet MAC value is conservative: RAN2 reported a range of 1 to 3 octets in S4-260015 [4].

<a id="P017"></a>

A key limitation is that NB-IoT cannot currently signal the required RTP RoHC profile. Profile 0x0001 is not included in PDCP-Config-NB-r13 in TS 36.331 [5]. RAN2 contributions R2-2508188 [6] and R2-2600884 [7] proposed adding RTP profiles, but neither proposal was agreed. R2-2600884 instead identifies this support as a Rel-20 work-item objective. Profile 0x0001 is therefore an evaluation assumption only and cannot yet be specified normatively in ULBC-9.

<a id="P018"></a>

A second limitation concerns packets that are larger than the steady-state packet. Such packets occur, for example, when speech resumes after a silence period or when RoHC refreshes its compression context. A semi-persistent grant is normally dimensioned for the regular packet size and does not by itself define how a larger packet is transmitted. Clauses 5.4 and 5.5 quantify this issue for the evaluated uplink. The required radio-layer procedure remains for RAN2 to define.

<a id="P019"></a>

The protocol stack in clause 3.2 is derived from the referenced specifications. The RoHC sizes in clause 3.3 were measured using the source's RFC 3095 [8] implementation for constant-rate voice flows at both ULBC bundling periods and for every configuration retained in clause 4. Each compressed flow was decompressed and checked for mismatches. The IR encoding was also compared with libROHC. Both implementations produced a 3-octet steady-state header; the IR size differed by 2 octets when an explicit timestamp stride was included. The transport-block sizes are calculated directly from Table 1 and do not result from a radio simulation. Because the results have not been validated with UE or network equipment, they are analytical implementation results rather than conformance evidence.

<a id="P020"></a>

Evaluated IP transport path

<a id="P021"></a>

Bearer and architecture

<a id="P022"></a>

The evaluation assumes one Packet Data Network (PDN) connection for both IMS signalling and voice, as specified in TR 26.940, clause 5.2.1. Within that connection, IMS signalling and the voice stream are mapped to separate Data Radio Bearers (DRBs). TS 36.331 permits at most two DRBs for an NB-IoT UE, so this assumption uses the full available number. Each DRB has its own Packet Data Convergence Protocol (PDCP) entity and, under TS 36.323 [9], clause 5.5.3, its own RoHC channel and context-identifier space.

<a id="P023"></a>

The uplink evaluation uses a semi-persistent grant: radio resources are reserved at regular intervals without a separate scheduling request for every packet. The grant period equals the ULBC bundling period, either 80 ms or 160 ms, as reported in RP-261082 [10]. During steady-state speech, one voice packet occupies one transport block. This assumption is used in clauses 4.2 and 5.1.

<a id="P024"></a>

This contribution evaluates the uplink only. The downlink bearer configuration, scheduling and transport-block selection require a separate RAN assessment before a bidirectional profile can be specified.

<a id="P025"></a>

Protocol stack

<a id="P026"></a>

Figure 1 shows the user-plane protocol stack from the UE to the remote endpoint, and Table 2 gives each layer of the UE stack with the clause that fixes its header.

<a id="P028"></a>

Figure 1: User-plane protocol stack for IMS voice over NB-IoT NTN

<a id="P029"></a>

RTP, UDP and IP extend end to end between the UE and the remote endpoint. The network does not remove or reconstruct these headers. This differs from the non-IP mechanism in TR 26.940, clause 5.2.1: in that mechanism, the PGW removes and restores the UDP and IP headers, and the UE removes and restores the RTP header. For IP transport, RoHC compression applies only across the radio interface between the PDCP entities in the UE and eNB. The eNB reconstructs the original headers before forwarding the packet over S1-U.

<a id="P030"></a>

Table 2: The uplink protocol stack of the IP transport mechanism

<a id="T031"></a>

<a id="T031-R01"></a>
**T031-R01**

- <a id="T031-R01-C01"></a>列 1: Layer
- <a id="T031-R01-C02"></a>列 2: PDU
- <a id="T031-R01-C03"></a>列 3: Header
- <a id="T031-R01-C04"></a>列 4: Reference

<a id="T031-R02"></a>
**T031-R02**

- <a id="T031-R02-C01"></a>列 1: ULBC codec
- <a id="T031-R02-C02"></a>列 2: Speech frames of one bundling period
- <a id="T031-R02-C03"></a>列 3: –
- <a id="T031-R02-C04"></a>列 4: TR 26.940 clause 5.3.4

<a id="T031-R03"></a>
**T031-R03**

- <a id="T031-R03-C01"></a>列 1: RTP
- <a id="T031-R03-C02"></a>列 2: RTP packet
- <a id="T031-R03-C03"></a>列 3: 12 octets
- <a id="T031-R03-C04"></a>列 4: RFC 3550 [11] clause 5.1, no CSRC and no extension

<a id="T031-R04"></a>
**T031-R04**

- <a id="T031-R04-C01"></a>列 1: UDP
- <a id="T031-R04-C02"></a>列 2: UDP datagram
- <a id="T031-R04-C03"></a>列 3: 8 octets
- <a id="T031-R04-C04"></a>列 4: RFC 768 [12]

<a id="T031-R05"></a>
**T031-R05**

- <a id="T031-R05-C01"></a>列 1: IP
- <a id="T031-R05-C02"></a>列 2: IP packet, the PDCP SDU
- <a id="T031-R05-C03"></a>列 3: 20 or 40 octets
- <a id="T031-R05-C04"></a>列 4: RFC 791 [13], RFC 8200 [14]

<a id="T031-R06"></a>
**T031-R06**

- <a id="T031-R06-C01"></a>列 1: PDCP
- <a id="T031-R06-C02"></a>列 2: PDCP Data PDU
- <a id="T031-R06-C03"></a>列 3: 1 octet
- <a id="T031-R06-C04"></a>列 4: TS 36.323 clauses 5.5, 6.2.4 and 6.3.2

<a id="T031-R07"></a>
**T031-R07**

- <a id="T031-R07-C01"></a>列 1: RLC UM
- <a id="T031-R07-C02"></a>列 2: UMD PDU
- <a id="T031-R07-C03"></a>列 3: 1 octet
- <a id="T031-R07-C04"></a>列 4: TS 36.322 [15] clause 6.2.1.3

<a id="T031-R08"></a>
**T031-R08**

- <a id="T031-R08-C01"></a>列 1: MAC
- <a id="T031-R08-C02"></a>列 2: MAC PDU, the transport block
- <a id="T031-R08-C03"></a>列 3: 1 to 3 octets
- <a id="T031-R08-C04"></a>列 4: TS 36.321 [16] clause 6.1.2

<a id="T031-R09"></a>
**T031-R09**

- <a id="T031-R09-C01"></a>列 1: NPUSCH
- <a id="T031-R09-C02"></a>列 2: Transport block
- <a id="T031-R09-C03"></a>列 3: –
- <a id="T031-R09-C04"></a>列 4: TS 36.213 clause 16.5.1.2, format 1

<a id="P033"></a>

The PDCP and RLC header sizes are fixed for NB-IoT rather than configured. TS 36.323, clause 6.3.2, specifies a 7-bit PDCP sequence number for an NB-IoT DRB, resulting in a 1-octet PDCP header. TS 36.322, clause 6.2.1.3, specifies a 5-bit sequence number for an NB-IoT UM RLC entity, resulting in a 1-octet fixed UMD PDU header when one PDCP PDU fills one UMD PDU. TS 36.321, clause 6.1.2, omits the length field from the final MAC subheader, so a MAC PDU carrying one SDU adds 1 octet. This minimum case therefore adds 3 octets of access-stratum overhead, 2 octets less than the conservative 5-octet assumption in Table 1.

<a id="P034"></a>

RoHC

<a id="P035"></a>

RoHC reduces the RTP/UDP/IP header chain by maintaining shared context at the compressor and decompressor. For the flow evaluated here, the uncompressed chain is 40 octets with IPv4 and 60 octets with IPv6. An Initialization and Refresh (IR) packet establishes the context by carrying static and dynamic header information. An IR-DYN packet updates dynamic information. After the context has stabilized, the compressor sends a short UO-0 packet containing encoded sequence-number information and a cyclic redundancy check. Figure 2 shows the measured sizes for profile 0x0001, context identifier (CID) 0, a carried UDP checksum and an established timestamp stride. It also shows the two larger packet forms that occur when speech resumes after silence; these are discussed in clause 5.5.

<a id="P037"></a>

Figure 2: Octets ahead of the ULBC payload, per IP version and RoHC packet type

<a id="P038"></a>

Two alternative encodings are relevant. If the compressor allows the decompressor to infer the timestamp stride instead of carrying it, the IR size is 39 octets for IPv4 and 62 octets for IPv6. If the IPv4 UDP checksum is elided, the steady-state compressed header is 1 octet.

<a id="P039"></a>

With the UDP checksum carried, the steady-state compressed header is 3 octets for both IP versions, confirming the value assumed in TR 26.940, clause 5.2.3. For IPv6, the absence of the IPv4 Identification field saves 2 octets, while the mandatory UDP checksum adds 2 octets; these effects cancel in steady state. They do not cancel for an IR packet, which is 23 octets larger for IPv6 than for IPv4.

<a id="P040"></a>

Evaluated configuration

<a id="P041"></a>

IP transport parameters

<a id="P042"></a>

Table 3 lists the parameters used in the evaluation and identifies which organization or protocol entity controls each one. Of the 22 parameters, five are fixed by existing specifications, six are configured by Radio Resource Control (RRC), four are determined by another working group or by an endpoint, and seven have no specified assignment. The table is intended to separate SA4 decisions from RAN2, SA2, endpoint and implementation decisions; it does not propose that SA4 specify parameters outside its scope.

<a id="P043"></a>

Table 3: IP transport mechanism parameters

<a id="T044"></a>

<a id="T044-R01"></a>
**T044-R01**

- <a id="T044-R01-C01"></a>列 1: Parameter
- <a id="T044-R01-C02"></a>列 2: Assumed value
- <a id="T044-R01-C03"></a>列 3: Responsible entity or mechanism
- <a id="T044-R01-C04"></a>列 4: Reference and status

<a id="T044-R02"></a>
**T044-R02**

- <a id="T044-R02-C01"></a>列 1: Transport mechanism
- <a id="T044-R02-C02"></a>列 2: IP, user plane
- <a id="T044-R02-C03"></a>列 3: SA2
- <a id="T044-R02-C04"></a>列 4: TR 26.940 clause 5.2.1, required

<a id="T044-R03"></a>
**T044-R03**

- <a id="T044-R03-C01"></a>列 1: IP version
- <a id="T044-R03-C02"></a>列 2: IPv4 or IPv6
- <a id="T044-R03-C03"></a>列 3: Operator
- <a id="T044-R03-C04"></a>列 4: Both evaluated, steady state equal

<a id="T044-R04"></a>
**T044-R04**

- <a id="T044-R04-C01"></a>列 1: UDP checksum
- <a id="T044-R04-C02"></a>列 2: Carried
- <a id="T044-R04-C03"></a>列 3: Endpoint, SDP
- <a id="T044-R04-C04"></a>列 4: Unassigned, clause 4.2

<a id="T044-R05"></a>
**T044-R05**

- <a id="T044-R05-C01"></a>列 1: RTP header
- <a id="T044-R05-C02"></a>列 2: One payload type, no CSRC, no extension
- <a id="T044-R05-C03"></a>列 3: SA4
- <a id="T044-R05-C04"></a>列 4: RFC 3550 clause 5.1

<a id="T044-R06"></a>
**T044-R06**

- <a id="T044-R06-C01"></a>列 1: RTCP
- <a id="T044-R06-C02"></a>列 2: Not carried on the voice bearer
- <a id="T044-R06-C03"></a>列 3: SA2, SA4
- <a id="T044-R06-C04"></a>列 4: Evaluation assumption; under discussion, clause 4.1

<a id="T044-R07"></a>
**T044-R07**

- <a id="T044-R07-C01"></a>列 1: RoHC profile
- <a id="T044-R07-C02"></a>列 2: 0x0001, with 0x0000
- <a id="T044-R07-C03"></a>列 3: RRC, profiles
- <a id="T044-R07-C04"></a>列 4: Not signallable today, clause 2

<a id="T044-R08"></a>
**T044-R08**

- <a id="T044-R08-C01"></a>列 1: Profile tie-break
- <a id="T044-R08-C02"></a>列 2: 0x0001 signalled alone
- <a id="T044-R08-C03"></a>列 3: RRC, profiles
- <a id="T044-R08-C04"></a>列 4: TS 36.331, higher identifier applies

<a id="T044-R09"></a>
**T044-R09**

- <a id="T044-R09-C01"></a>列 1: MAX_CID
- <a id="T044-R09-C02"></a>列 2: 1
- <a id="T044-R09-C03"></a>列 3: RRC, maxCID
- <a id="T044-R09-C04"></a>列 4: Range 1 to 16383, default 15

<a id="T044-R10"></a>
**T044-R10**

- <a id="T044-R10-C01"></a>列 1: Voice context CID
- <a id="T044-R10-C02"></a>列 2: 0
- <a id="T044-R10-C03"></a>列 3: Compressor
- <a id="T044-R10-C04"></a>列 4: Unassigned, clause 4.2

<a id="T044-R11"></a>
**T044-R11**

- <a id="T044-R11-C01"></a>列 1: LARGE_CIDS
- <a id="T044-R11-C02"></a>列 2: FALSE
- <a id="T044-R11-C03"></a>列 3: Inferred
- <a id="T044-R11-C04"></a>列 4: TS 36.323 clause 5.5.3, from MAX_CID

<a id="T044-R12"></a>
**T044-R12**

- <a id="T044-R12-C01"></a>列 1: RoHC channel
- <a id="T044-R12-C02"></a>列 2: Bidirectional
- <a id="T044-R12-C03"></a>列 3: NB-IoT PDCP configuration
- <a id="T044-R12-C04"></a>列 4: PDCP-Config-NB-r13 has no uplink-only choice

<a id="T044-R13"></a>
**T044-R13**

- <a id="T044-R13-C01"></a>列 1: RoHC operating mode
- <a id="T044-R13-C02"></a>列 2: O-mode
- <a id="T044-R13-C03"></a>列 3: Compressor and decompressor, in band
- <a id="T044-R13-C04"></a>列 4: Unassigned, clause 5.3

<a id="T044-R14"></a>
**T044-R14**

- <a id="T044-R14-C01"></a>列 1: MRRU
- <a id="T044-R14-C02"></a>列 2: Not used
- <a id="T044-R14-C03"></a>列 3: Specification
- <a id="T044-R14-C04"></a>列 4: TS 36.323 clause 5.5.3, no segmentation

<a id="T044-R15"></a>
**T044-R15**

- <a id="T044-R15-C01"></a>列 1: PACKET_SIZES_ALLOWED
- <a id="T044-R15-C02"></a>列 2: The configured block
- <a id="T044-R15-C03"></a>列 3: External configuration; not specified
- <a id="T044-R15-C04"></a>列 4: Outside TS 36.323, clause 4.3

<a id="T044-R16"></a>
**T044-R16**

- <a id="T044-R16-C01"></a>列 1: TS_STRIDE
- <a id="T044-R16-C02"></a>列 2: Clock rate times bundling period
- <a id="T044-R16-C03"></a>列 3: Compressor, in band
- <a id="T044-R16-C04"></a>列 4: Unassigned, clause 4.2

<a id="T044-R17"></a>
**T044-R17**

- <a id="T044-R17-C01"></a>列 1: Periodic refresh interval
- <a id="T044-R17-C02"></a>列 2: Not used in O-mode
- <a id="T044-R17-C03"></a>列 3: Compressor
- <a id="T044-R17-C04"></a>列 4: U-mode only, clause 5.4

<a id="T044-R18"></a>
**T044-R18**

- <a id="T044-R18-C01"></a>列 1: PDCP SN
- <a id="T044-R18-C02"></a>列 2: 7 bits
- <a id="T044-R18-C03"></a>列 3: Specification
- <a id="T044-R18-C04"></a>列 4: TS 36.323 clause 6.3.2, NB-IoT

<a id="T044-R19"></a>
**T044-R19**

- <a id="T044-R19-C01"></a>列 1: PDCP discard timer
- <a id="T044-R19-C02"></a>列 2: Longer than one bundling period
- <a id="T044-R19-C03"></a>列 3: RRC, discardTimer
- <a id="T044-R19-C04"></a>列 4: TS 36.331, ms5120 to infinity

<a id="T044-R20"></a>
**T044-R20**

- <a id="T044-R20-C01"></a>列 1: Ciphering
- <a id="T044-R20-C02"></a>列 2: Applied
- <a id="T044-R20-C03"></a>列 3: RRC
- <a id="T044-R20-C04"></a>列 4: cipheringDisabled needs 5GC

<a id="T044-R21"></a>
**T044-R21**

- <a id="T044-R21-C01"></a>列 1: RLC mode
- <a id="T044-R21-C02"></a>列 2: UM, bidirectional
- <a id="T044-R21-C03"></a>列 3: RRC, rlc-Config
- <a id="T044-R21-C04"></a>列 4: TS 36.331, um-Bi-Directional-r15

<a id="T044-R22"></a>
**T044-R22**

- <a id="T044-R22-C01"></a>列 1: Access stratum
- <a id="T044-R22-C02"></a>列 2: 5 octets
- <a id="T044-R22-C03"></a>列 3: RAN2
- <a id="T044-R22-C04"></a>列 4: TR 26.940 clause 5.2.3

<a id="T044-R23"></a>
**T044-R23**

- <a id="T044-R23-C01"></a>列 1: Blocks per voice packet
- <a id="T044-R23-C02"></a>列 2: 1
- <a id="T044-R23-C03"></a>列 3: Evaluation assumption
- <a id="T044-R23-C04"></a>列 4: TR 26.940 clause 5.3.4

<a id="P046"></a>

Two entries in Table 3 resolve issues left open in earlier discussions. First, the RoHC channel direction is not selectable for an NB-IoT bearer. TS 36.323, clause 5.5.2, defines both headerCompression and uplinkOnlyHeaderCompression, but PDCP-Config-NB-r13 supports only headerCompression. RoHC is therefore bidirectional whenever configured. If the decompressor loses context, it can request a refresh using an interspersed PDCP Control PDU under TS 36.323, clause 5.5.6; this control PDU is unciphered and has no PDCP sequence number. Second, the ASN.1 definition gives MAX_CID a minimum value of 1. The smallest configuration therefore provides two context identifiers, one of which is reserved for uncompressed flows under TS 36.323, clause 5.5.

<a id="P047"></a>

Whether RTCP is sent during the voice call is being clarified by SA2. S4-261524 [17] lists it among the scope restrictions relevant to the RTP header design, in square brackets and alongside suspension of the data service and SRTP integrity protection, so the restriction is not yet agreed. This contribution assumes RTCP is not carried on the evaluated bearer; it does not propose an RTCP restriction for ULBC-9.

<a id="P048"></a>

The RoHC operating mode is listed separately because it determines how a context refresh is triggered. A bidirectional channel is a precondition for O-mode and does not by itself select it; clause 5.3 addresses the selection.

<a id="P049"></a>

Observation 1: Seven of the 22 parameters in the evaluated IP/RoHC configuration are not assigned by an existing specification: the context identifier, UDP-checksum treatment, RTCP use, permitted packet sizes, timestamp stride, RoHC operating mode and periodic refresh interval. Three of these parameters add overhead to individual packets. For at least one evaluated bitrate and bundling period, each of those three parameters requires a larger transport block.

<a id="P050"></a>

Cost of unassigned values

<a id="P051"></a>

The selected transport block is sensitive to even one additional header octet. Figure 3 maps each compressed-header size to the resulting transport block for every evaluated bitrate and bundling period. Table 4 then shows the effect of the three currently unassigned parameters that add overhead to each packet.

<a id="P053"></a>

Figure 3: Transport block selected per RoHC compressed header size, 5-octet access stratum

<a id="P054"></a>

Table 4: Cost of the three unassigned per-packet parameters, profile 0x0001

<a id="T055"></a>

<a id="T055-R01"></a>
**T055-R01**

- <a id="T055-R01-C01"></a>列 1: Parameter
- <a id="T055-R01-C02"></a>列 2: Cost per packet
- <a id="T055-R01-C03"></a>列 3: Affected combinations
- <a id="T055-R01-C04"></a>列 4: Note

<a id="T055-R02"></a>
**T055-R02**

- <a id="T055-R02-C01"></a>列 1: Context identifier
- <a id="T055-R02-C02"></a>列 2: 1 octet on CID 1 to 15, none on CID 0
- <a id="T055-R02-C03"></a>列 3: 3 of 4
- <a id="T055-R02-C04"></a>列 4: 144 to 152, 176 to 208, 224 to 256 bits

<a id="T055-R03"></a>
**T055-R03**

- <a id="T055-R03-C01"></a>列 1: UDP checksum
- <a id="T055-R03-C02"></a>列 2: 2 octets when carried
- <a id="T055-R03-C03"></a>列 3: 2 of 4
- <a id="T055-R03-C04"></a>列 4: 136 to 144 bits, and 208 to 224 bits

<a id="T055-R04"></a>
**T055-R04**

- <a id="T055-R04-C01"></a>列 1: Timestamp stride
- <a id="T055-R04-C02"></a>列 2: None on 0x0001, 1 octet on 0x0101
- <a id="T055-R04-C03"></a>列 3: 3 of 4, on 0x0101
- <a id="T055-R04-C04"></a>列 4: 0x0001 infers the stride within four packets

<a id="P057"></a>

A voice context on CID 0 carries no Add-CID octet. RFC 3095, clause 5.2, assigns that octet to CIDs 1 to 15, so a context on any other CID carries it in every packet. TS 36.323, clause 5.5.3, requires one CID value to be reserved for uncompressed flows and does not state that the reserved value is CID 0.

<a id="P058"></a>

The UDP checksum contributes two octets per packet. Checksum elision is available for IPv4 only, since RFC 8200, clause 8.1, requires an IPv6 receiver to discard a UDP datagram with a zero checksum.

<a id="P059"></a>

The timestamp stride adds no steady-state overhead with profile 0x0001, whether or not the stride is supplied explicitly. With profile 0x0101, the steady-state header is 4 octets if the stride is not supplied and 3 octets after it is established. RFC 5225 [18] defines an initial stride of 160 for profile 0x0101, corresponding to 20 ms at an 8 kHz clock rate; neither ULBC bundling period uses this interval. TS 36.331 selects the higher identifier when two profiles share their eight least significant bits. Signalling both 0x0001 and 0x0101 would therefore select 0x0101 and add one octet per packet until the stride is established.

<a id="P060"></a>

Parameters outside TS 36.323

<a id="P061"></a>

TS 36.323, clause 5.5.3, enumerates five RoHC channel parameters. Two parameters defined in RFC 3095 do not appear in that list.

<a id="P062"></a>

PACKET_SIZES_ALLOWED is an RoHC control defined in RFC 3095, clause 6.3.1. It allows a lower layer to restrict the packet sizes that the compressor may produce. For the evaluated semi-persistent grant, the permitted set would contain only the configured transport-block size. RFC 3095 also requires this set to include a size that can carry a complete IR header unless RoHC segmentation is enabled through MRRU. TS 36.323 specifies that MRRU is not used, so this exception is unavailable. Across the evaluated combinations and both IP versions, an IR packet with payload and access-stratum overhead requires 2.0 to 4.4 times the configured transport block. The steady-state grant therefore cannot satisfy the RFC requirement by itself.

<a id="P063"></a>

TS_STRIDE is a per-context control field set in band by the compressor. RRC provides no corresponding parameter, so the value is specified by the ULBC profile.

<a id="P064"></a>

Observation 2: A semi-persistent grant sized for a steady-state compressed packet cannot carry a complete RoHC IR packet. RoHC segmentation is disabled by TS 36.323, and the measured IR packet requires between 2.0 and 4.4 times the configured transport block. RAN2 therefore needs to determine how RLC and scheduling can carry the packet within the voice-delay budget.

<a id="P065"></a>

Properties of the configured path

<a id="P066"></a>

Occupancy of the transport block

<a id="P067"></a>

Table 5 gives the transport block at each evaluated combination, computed from the assumptions of Table 1, and states whether TR 26.940 has simulated that block.

<a id="P068"></a>

Table 5: Occupancy of the transport block

<a id="T069"></a>

<a id="T069-R01"></a>
**T069-R01**

- <a id="T069-R01-C01"></a>列 1: Bitrate and bundling
- <a id="T069-R01-C02"></a>列 2: Payload
- <a id="T069-R01-C03"></a>列 3: With 8 octets of overhead
- <a id="T069-R01-C04"></a>列 4: Block
- <a id="T069-R01-C05"></a>列 5: Spare
- <a id="T069-R01-C06"></a>列 6: Simulated in TR 26.940

<a id="T069-R02"></a>
**T069-R02**

- <a id="T069-R02-C01"></a>列 1: 1.0 kbit/s, 80 ms
- <a id="T069-R02-C02"></a>列 2: 10 octets
- <a id="T069-R02-C03"></a>列 3: 18 octets
- <a id="T069-R02-C04"></a>列 4: 144 bits
- <a id="T069-R02-C05"></a>列 5: 0 octets
- <a id="T069-R02-C06"></a>列 6: table 5.3.4-1

<a id="T069-R03"></a>
**T069-R03**

- <a id="T069-R03-C01"></a>列 1: 1.4 kbit/s, 80 ms
- <a id="T069-R03-C02"></a>列 2: 14 octets
- <a id="T069-R03-C03"></a>列 3: 22 octets
- <a id="T069-R03-C04"></a>列 4: 176 bits
- <a id="T069-R03-C05"></a>列 5: 0 octets
- <a id="T069-R03-C06"></a>列 6: table 5.3.4-1

<a id="T069-R04"></a>
**T069-R04**

- <a id="T069-R04-C01"></a>列 1: 1.0 kbit/s, 160 ms
- <a id="T069-R04-C02"></a>列 2: 20 octets
- <a id="T069-R04-C03"></a>列 3: 28 octets
- <a id="T069-R04-C04"></a>列 4: 224 bits
- <a id="T069-R04-C05"></a>列 5: 0 octets
- <a id="T069-R04-C06"></a>列 6: clause 5.3.5, test case 8

<a id="T069-R05"></a>
**T069-R05**

- <a id="T069-R05-C01"></a>列 1: 1.4 kbit/s, 160 ms
- <a id="T069-R05-C02"></a>列 2: 28 octets
- <a id="T069-R05-C03"></a>列 3: 36 octets
- <a id="T069-R05-C04"></a>列 4: 296 bits
- <a id="T069-R05-C05"></a>列 5: 1 octet
- <a id="T069-R05-C06"></a>列 6: not simulated

<a id="P071"></a>

For three of the four combinations the transport block is fully occupied by the payload, the compressed header and the access stratum, with no spare octet. The parameters of clause 4.2 therefore change the selected transport block rather than the amount of padding.

<a id="P072"></a>

TR 26.940, table 5.3.4-2, lists transport-block sizes of 208, 256, 424, 600 and 808 bits for 160 ms bundling, corresponding to codec bitrates from 0.9 to 4.65 kbit/s. ULBC-4 v0.2.1 [19] subsequently fixed the codec bitrates at 1.0 and 1.4 kbit/s. The 1.4 kbit/s, 160 ms combination therefore falls between the tabulated simulation points. RAN2 agreed the bundling period in RP-261082 [10]; the required 296-bit transport block follows directly from the bitrate, bundling period and overhead assumptions. The missing item is thus a capacity and coverage result, not support for the transport-block size itself.

<a id="P073"></a>

Observation 3: TR 26.940 includes simulation results for three of the four bitrate and bundling-period combinations in scope. The remaining combination, 1.4 kbit/s with 160 ms bundling, requires a 296-bit transport block. This block is technically selectable, but TR 26.940 provides no capacity or coverage result for it.

<a id="P074"></a>

This contribution states the transport block size only. The resource-unit count, repetition number and air time are selected per company in the cross-checked results of clause 5.3.5 of TR 26.940, and are a RAN matter; the header budget does not depend on them.

<a id="P075"></a>

Table 5 uses the smallest transport block that can contain the payload and assumed overhead. A deployment may select a larger block to meet coverage requirements, producing additional spare capacity. That coverage-driven choice is separate from the minimum header-budget calculation reported here.

<a id="P076"></a>

Context robustness

<a id="P077"></a>

For the evaluated constant-rate flow, UO-0 packets permitted recovery after up to 13 consecutive packet losses; decompression failed after 14 consecutive losses. This result was observed for both evaluated bundling periods. A UO-0 packet carries four bits of sequence-number information, which bounds the gap that a decompressor can bridge without a refresh.

<a id="P078"></a>

Context refresh triggers

<a id="P079"></a>

RFC 3095, clause 5.3.1.1.2, requires the compressor to return periodically to lower compression states during operation in Unidirectional mode. This requirement does not apply to Bidirectional Optimistic mode. RFC 3095, clause 4.4.2, states that periodic refreshes are not used in O-mode, and clause 5.4.1.1 specifies that O-mode has no timeouts. In O-mode, decompressor feedback triggers the required repair: a STATIC-NACK causes the compressor to send an IR packet, whereas a NACK causes it to send an IR-DYN packet.

<a id="P080"></a>

The bearer provides the feedback channel required by O-mode. Decompressor feedback is carried as an interspersed PDCP Control PDU, as specified in clause 5.5.6 of TS 36.323, and clause 4.1 establishes that PDCP-Config-NB-r13 provides no uplink-only alternative. RFC 3095, clause 5.6.2, states that the decompressor may initiate the transition from Unidirectional to Bidirectional Optimistic mode at any time when a feedback channel is available, and clause 5.6 assigns that decision to the decompressor.

<a id="P081"></a>

The mode is not among the channel parameters configured under TS 36.323, clause 5.5.3, and RFC 3095, clause 5.6, transitions it in band. The mode and timestamp stride are implementation parameters for the evaluated profile; this contribution does not propose that ULBC-9 specify either value.

<a id="P082"></a>

Observation 4: The periodic refresh required by RFC 3095 applies to Unidirectional mode, and the evaluated bearer is bidirectional by construction. Bidirectional Optimistic mode uses no periodic refresh, so the evaluated configuration has no refresh interval. Selecting an operating mode remains an implementation and cross-WG matter.

<a id="P083"></a>

Refresh interval

<a id="P084"></a>

RFC 2507 [20], clause 3.3.4, is sometimes interpreted as defining a minimum refresh interval. If the full header is H octets, the compressed header is C octets and a refresh occurs every f packets, the average header size is (H − C)/f + C. Applying the RFC's example criterion—that full headers contribute less than 1 octet to the average—gives 39 packets for IPv4 and 62 packets for IPv6. This contribution does not use those values as requirements, for the reasons below.

<a id="P085"></a>

First, the RFC criterion limits average header overhead and assumes that the link can allocate capacity according to that average. The evaluated bearer instead provides one fixed transport block per bundling period. An IR packet does not fit in that block regardless of how rarely it is sent. It would require RLC segmentation across multiple occasions or an additional grant, and the required procedure has not been specified for this profile.

<a id="P086"></a>

Second, a minimum interval would limit how frequently the compressor may refresh the context. More frequent refresh can improve robustness. In O-mode, this function is instead controlled by decompressor feedback when context repair is required.

<a id="P087"></a>

Table 6 gives the average header size across a range of intervals, so that an interval selected for a Unidirectional mode fallback can be evaluated against its cost.

<a id="P088"></a>

Table 6: Average header size in octets against periodic refresh interval, profile 0x0001 on CID 0

<a id="T089"></a>

<a id="T089-R01"></a>
**T089-R01**

- <a id="T089-R01-C01"></a>列 1: Interval
- <a id="T089-R01-C02"></a>列 2: 10 packets
- <a id="T089-R01-C03"></a>列 3: 20 packets
- <a id="T089-R01-C04"></a>列 4: 39 packets
- <a id="T089-R01-C05"></a>列 5: 62 packets
- <a id="T089-R01-C06"></a>列 6: 256 packets

<a id="T089-R02"></a>
**T089-R02**

- <a id="T089-R02-C01"></a>列 1: IPv4, IR of 41 octets
- <a id="T089-R02-C02"></a>列 2: 6.80
- <a id="T089-R02-C03"></a>列 3: 4.90
- <a id="T089-R02-C04"></a>列 4: 3.97
- <a id="T089-R02-C05"></a>列 5: 3.61
- <a id="T089-R02-C06"></a>列 6: 3.15

<a id="T089-R03"></a>
**T089-R03**

- <a id="T089-R03-C01"></a>列 1: IPv6, IR of 64 octets
- <a id="T089-R03-C02"></a>列 2: 9.10
- <a id="T089-R03-C03"></a>列 3: 6.05
- <a id="T089-R03-C04"></a>列 4: 4.56
- <a id="T089-R03-C05"></a>列 5: 3.98
- <a id="T089-R03-C06"></a>列 6: 3.24

<a id="P091"></a>

Observation 5: The RFC 2507 criterion bounds average header size, which is not the quantity a fixed semi-persistent grant allocates. This contribution therefore states the cost of an interval and specifies none.

<a id="P092"></a>

Delay variation

<a id="P093"></a>

This clause concerns the packet-size variation that header compression introduces. Other origins of delay variation on this bearer, and what a receiver has to absorb, are outside its scope.

<a id="P094"></a>

Once the context has settled, every packet of a constant-rate flow is a UO-0 packet of 3 octets. The measurement records one distinct compressed size at each evaluated combination, so header compression adds no variation of its own to a constant-rate flow.

<a id="P095"></a>

Three events produce a larger header. An IR packet is sent when the context is established. An IR or IR-DYN packet is sent when the decompressor requests context repair. A larger compressed header also occurs when speech resumes after discontinuous transmission, which TR 26.940, clause 6.1, identifies as a ULBC design constraint. At talkspurt onset, the RTP timestamp has advanced by more than the sequence-number progression predicts, so UO-0 cannot represent the update. Table 7 shows the measured packet types and sizes.

<a id="P096"></a>

Table 7: Compressed header at a talkspurt onset, and the block it requires

<a id="T097"></a>

<a id="T097-R01"></a>
**T097-R01**

- <a id="T097-R01-C01"></a>列 1: Bitrate and bundling
- <a id="T097-R01-C02"></a>列 2: Pause
- <a id="T097-R01-C03"></a>列 3: Onset packet
- <a id="T097-R01-C04"></a>列 4: Header
- <a id="T097-R01-C05"></a>列 5: Needs
- <a id="T097-R01-C06"></a>列 6: Configured block

<a id="T097-R02"></a>
**T097-R02**

- <a id="T097-R02-C01"></a>列 1: 1.0 kbit/s, 80 ms
- <a id="T097-R02-C02"></a>列 2: 80 ms to 1840 ms
- <a id="T097-R02-C03"></a>列 3: UO-1-TS
- <a id="T097-R02-C04"></a>列 4: 4 octets
- <a id="T097-R02-C05"></a>列 5: 152 bits
- <a id="T097-R02-C06"></a>列 6: 144 bits

<a id="T097-R03"></a>
**T097-R03**

- <a id="T097-R03-C01"></a>列 1: 1.0 kbit/s, 80 ms
- <a id="T097-R03-C02"></a>列 2: 1920 ms or more
- <a id="T097-R03-C03"></a>列 3: UOR-2-TS
- <a id="T097-R03-C04"></a>列 4: 6 octets
- <a id="T097-R03-C05"></a>列 5: 168 bits
- <a id="T097-R03-C06"></a>列 6: 144 bits

<a id="T097-R04"></a>
**T097-R04**

- <a id="T097-R04-C01"></a>列 1: 1.4 kbit/s, 80 ms
- <a id="T097-R04-C02"></a>列 2: 80 ms to 1840 ms
- <a id="T097-R04-C03"></a>列 3: UO-1-TS
- <a id="T097-R04-C04"></a>列 4: 4 octets
- <a id="T097-R04-C05"></a>列 5: 184 bits
- <a id="T097-R04-C06"></a>列 6: 176 bits

<a id="T097-R05"></a>
**T097-R05**

- <a id="T097-R05-C01"></a>列 1: 1.4 kbit/s, 80 ms
- <a id="T097-R05-C02"></a>列 2: 1920 ms or more
- <a id="T097-R05-C03"></a>列 3: UOR-2-TS
- <a id="T097-R05-C04"></a>列 4: 6 octets
- <a id="T097-R05-C05"></a>列 5: 200 bits
- <a id="T097-R05-C06"></a>列 6: 176 bits

<a id="T097-R06"></a>
**T097-R06**

- <a id="T097-R06-C01"></a>列 1: 1.0 kbit/s, 160 ms
- <a id="T097-R06-C02"></a>列 2: 160 ms to 3680 ms
- <a id="T097-R06-C03"></a>列 3: UO-1-TS
- <a id="T097-R06-C04"></a>列 4: 4 octets
- <a id="T097-R06-C05"></a>列 5: 232 bits
- <a id="T097-R06-C06"></a>列 6: 224 bits

<a id="T097-R07"></a>
**T097-R07**

- <a id="T097-R07-C01"></a>列 1: 1.0 kbit/s, 160 ms
- <a id="T097-R07-C02"></a>列 2: 3840 ms or more
- <a id="T097-R07-C03"></a>列 3: UOR-2-TS
- <a id="T097-R07-C04"></a>列 4: 6 octets
- <a id="T097-R07-C05"></a>列 5: 248 bits
- <a id="T097-R07-C06"></a>列 6: 224 bits

<a id="T097-R08"></a>
**T097-R08**

- <a id="T097-R08-C01"></a>列 1: 1.4 kbit/s, 160 ms
- <a id="T097-R08-C02"></a>列 2: 160 ms to 3680 ms
- <a id="T097-R08-C03"></a>列 3: UO-1-TS
- <a id="T097-R08-C04"></a>列 4: 4 octets
- <a id="T097-R08-C05"></a>列 5: 296 bits
- <a id="T097-R08-C06"></a>列 6: 296 bits

<a id="T097-R09"></a>
**T097-R09**

- <a id="T097-R09-C01"></a>列 1: 1.4 kbit/s, 160 ms
- <a id="T097-R09-C02"></a>列 2: 3840 ms or more
- <a id="T097-R09-C03"></a>列 3: UOR-2-TS
- <a id="T097-R09-C04"></a>列 4: 6 octets
- <a id="T097-R09-C05"></a>列 5: 312 bits
- <a id="T097-R09-C06"></a>列 6: 296 bits

<a id="P099"></a>

Seven of the eight cases exceed the configured block. The exception is 1.4 kbit/s at 160 ms after a pause shorter than 3840 ms, where the packet occupies 296 bits exactly: the one spare octet of Table 5 is the octet a talkspurt onset needs.

<a id="P100"></a>

Observation 6: When speech resumes after silence, the RoHC header is larger than in steady state. In seven of the eight measured cases, the resulting packet exceeds the configured transport block. A bearer dimensioned for steady-state packets therefore requires a RAN-defined procedure for the first packet of a talkspurt. This contribution does not assume that RLC segmentation over successive semi-persistent occasions satisfies the voice-delay requirement.

<a id="P101"></a>

Coverage of the two mechanisms in ULBC-9

<a id="P102"></a>

Table 8 maps the two transport mechanisms to the clause structure agreed in S4-261722.

<a id="P103"></a>

Table 8: The ULBC-9 clause structure against the two transport mechanisms

<a id="T104"></a>

<a id="T104-R01"></a>
**T104-R01**

- <a id="T104-R01-C01"></a>列 1: Clause of S4-261722
- <a id="T104-R01-C02"></a>列 2: IP mechanism
- <a id="T104-R01-C03"></a>列 3: Non-IP mechanism

<a id="T104-R02"></a>
**T104-R02**

- <a id="T104-R02-C01"></a>列 1: 2, transport options and protocol overhead
- <a id="T104-R02-C02"></a>列 2: both, as a comparison
- <a id="T104-R02-C03"></a>列 3: both, as a comparison

<a id="T104-R03"></a>
**T104-R03**

- <a id="T104-R03-C01"></a>列 1: Applicability of RTP header reduction
- <a id="T104-R03-C02"></a>列 2: not applicable, RoHC compresses the RTP header
- <a id="T104-R03-C03"></a>列 3: applicable

<a id="T104-R04"></a>
**T104-R04**

- <a id="T104-R04-C01"></a>列 1: 3 to 6, RTP header fields, analysis, guidelines, format
- <a id="T104-R04-C02"></a>列 2: not applicable
- <a id="T104-R04-C03"></a>列 3: applicable

<a id="T104-R05"></a>
**T104-R05**

- <a id="T104-R05-C01"></a>列 1: 7, SDP parameters and negotiation
- <a id="T104-R05-C02"></a>列 2: partly
- <a id="T104-R05-C03"></a>列 3: partly

<a id="T104-R06"></a>
**T104-R06**

- <a id="T104-R06-C01"></a>列 1: 8, UHRR and bearer aspects
- <a id="T104-R06-C02"></a>列 2: none
- <a id="T104-R06-C03"></a>列 3: applicable

<a id="T104-R07"></a>
**T104-R07**

- <a id="T104-R07-C01"></a>列 1: 9, IMS negotiation and IMS-AGW
- <a id="T104-R07-C02"></a>列 2: partly
- <a id="T104-R07-C03"></a>列 3: partly

<a id="P106"></a>

The current ULBC-9 structure gives substantially more detail to the optional non-IP mechanism than to the mandatory IP mechanism. Five of the nine numbered clauses, together with the unnumbered applicability section, address functions that are specific to the non-IP mechanism. By contrast, the IP mechanism appears only in the transport comparison in clause 2 and has no clause describing its prerequisites or unresolved dependencies.

<a id="P107"></a>

Observation 7: As currently structured, ULBC-9 would not describe the dependencies of the mandatory IP mechanism. The missing items are: (1) RAN2 support for signalling RTP/UDP/IP RoHC profiles on NB-IoT bearers; (2) a radio-layer procedure for RoHC refresh packets and talkspurt-onset packets that exceed the steady-state transport block, in both uplink and downlink; and (3) an SA2 decision on whether RTCP is carried during the call.

<a id="P108"></a>

Conclusion

<a id="P109"></a>

The evaluation confirms that RoHC profile 0x0001 can reduce a 40-octet IPv4 or 60-octet IPv6 RTP/UDP/IP header chain to 3 octets in steady state. With the 5-octet access-stratum assumption from TR 26.940, the evaluated uplink requires transport blocks from 144 to 296 bits. However, the result is not yet suitable for normative ULBC-9 configuration text. NB-IoT cannot currently signal the RTP RoHC profile; several configuration values are not assigned by existing specifications; and RoHC refresh packets and most talkspurt-onset packets exceed a grant sized for steady-state traffic. ULBC-9 should document these dependencies, while normative configuration is deferred until RAN2 and SA2 resolve the items identified in the proposals.

<a id="P110"></a>

Proposal

<a id="P111"></a>

Proposal 1: Agree that the IP/RoHC results in this contribution are evaluation results and shall not yet be used as normative ULBC-9 configuration requirements.

<a id="P112"></a>

Proposal 2: Send a liaison statement to RAN2 requesting: (1) support for signalling RTP/UDP/IP RoHC profiles on NB-IoT bearers; and (2) procedures for carrying media packets and RoHC packets that exceed the steady-state fixed-grant size in both uplink and downlink.

<a id="P113"></a>

Proposal 3: Request SA2 to confirm whether RTCP is carried for IMS voice over NB-IoT NTN before ULBC-9 specifies related SDP behaviour.

<a id="P114"></a>

Proposal 4: Keep the candidate text in Annex A for further discussion, but defer agreement until the RAN2 and SA2 dependencies in Proposals 2 and 3 are resolved.

<a id="P115"></a>

References

<a id="P116"></a>

3GPP TR 26.940: "Study on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite".

<a id="P117"></a>

S4-261722, "[ULBC-MED] ULBC-9 skeleton v0.0.1", China Mobile, SA4#137-e.

<a id="P118"></a>

3GPP TS 36.213: "Evolved Universal Terrestrial Radio Access (E-UTRA); Physical layer procedures".

<a id="P119"></a>

S4-260015, "Reply LS on the RAN simulation assumptions, bundling period and SPS for ULBC", RAN2, SA4#135.

<a id="P120"></a>

3GPP TS 36.331: "Evolved Universal Terrestrial Radio Access (E-UTRA); Radio Resource Control (RRC); Protocol specification".

<a id="P121"></a>

R2-2508188, "RAN2 impacts for supporting voice over NB-IoT NTN", ZTE Corporation, Sanechips, RAN2#132.

<a id="P122"></a>

R2-2600884, "NB-IoT NTN voice over GSO adaptations", Ericsson, RAN2#133.

<a id="P123"></a>

IETF RFC 3095: "RObust Header Compression (ROHC): Framework and four profiles: RTP, UDP, ESP, and uncompressed".

<a id="P124"></a>

3GPP TS 36.323: "Evolved Universal Terrestrial Radio Access (E-UTRA); Packet Data Convergence Protocol (PDCP) specification".

<a id="P125"></a>

RP-261082, "Status report for WI Core part: Non-Terrestrial Networks (NTN) for Internet of Things (IoT) Phase 4", vivo, TSG RAN#112.

<a id="P126"></a>

IETF RFC 3550: "RTP: A Transport Protocol for Real-Time Applications".

<a id="P127"></a>

IETF RFC 768: "User Datagram Protocol".

<a id="P128"></a>

IETF RFC 791: "Internet Protocol".

<a id="P129"></a>

IETF RFC 8200: "Internet Protocol, Version 6 (IPv6) Specification".

<a id="P130"></a>

3GPP TS 36.322: "Evolved Universal Terrestrial Radio Access (E-UTRA); Radio Link Control (RLC) protocol specification".

<a id="P131"></a>

3GPP TS 36.321: "Evolved Universal Terrestrial Radio Access (E-UTRA); Medium Access Control (MAC) protocol specification".

<a id="P132"></a>

S4-261524, "[ULBC-MED] ULBC-9 RTP header reduction and system integration", vivo, SA4#137-e.

<a id="P133"></a>

IETF RFC 5225: "RObust Header Compression Version 2 (ROHCv2): Profiles for RTP, UDP, IP, ESP and UDP-Lite".

<a id="P134"></a>

S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.1", Fraunhofer IIS, SA4#137-e.

<a id="P135"></a>

IETF RFC 2507: "IP Header Compression".

<a id="P136"></a>

Annex A References cited by the proposed clause

<a id="P137"></a>

The conditional candidate text cites the entries below. It is retained for further discussion and is not proposed for agreement in this contribution.

<a id="P138"></a>

Table 9: References cited by the proposed clause

<a id="T139"></a>

<a id="T139-R01"></a>
**T139-R01**

- <a id="T139-R01-C01"></a>列 1: Placeholder
- <a id="T139-R01-C02"></a>列 2: Entry

<a id="T139-R02"></a>
**T139-R02**

- <a id="T139-R02-C01"></a>列 1: [x1]
- <a id="T139-R02-C02"></a>列 2: 3GPP TR 26.940: "Study on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite".

<a id="T139-R03"></a>
**T139-R03**

- <a id="T139-R03-C01"></a>列 1: [x2]
- <a id="T139-R03-C02"></a>列 2: 3GPP TS 36.323: "Evolved Universal Terrestrial Radio Access (E-UTRA); Packet Data Convergence Protocol (PDCP) specification".

<a id="T139-R04"></a>
**T139-R04**

- <a id="T139-R04-C01"></a>列 1: [x3]
- <a id="T139-R04-C02"></a>列 2: 3GPP TS 36.322: "Evolved Universal Terrestrial Radio Access (E-UTRA); Radio Link Control (RLC) protocol specification".

<a id="T139-R05"></a>
**T139-R05**

- <a id="T139-R05-C01"></a>列 1: [x4]
- <a id="T139-R05-C02"></a>列 2: 3GPP TS 36.321: "Evolved Universal Terrestrial Radio Access (E-UTRA); Medium Access Control (MAC) protocol specification".

<a id="T139-R06"></a>
**T139-R06**

- <a id="T139-R06-C01"></a>列 1: [x5]
- <a id="T139-R06-C02"></a>列 2: 3GPP TS 36.331: "Evolved Universal Terrestrial Radio Access (E-UTRA); Radio Resource Control (RRC); Protocol specification".

<a id="T139-R07"></a>
**T139-R07**

- <a id="T139-R07-C01"></a>列 1: [x6]
- <a id="T139-R07-C02"></a>列 2: IETF RFC 5225: "RObust Header Compression Version 2 (ROHCv2): Profiles for RTP, UDP, IP, ESP and UDP-Lite".

<a id="T139-R08"></a>
**T139-R08**

- <a id="T139-R08-C01"></a>列 1: [x7]
- <a id="T139-R08-C02"></a>列 2: IETF RFC 3095: "RObust Header Compression (ROHC): Framework and four profiles: RTP, UDP, ESP, and uncompressed".

<a id="T139-R09"></a>
**T139-R09**

- <a id="T139-R09-C01"></a>列 1: [x8]
- <a id="T139-R09-C02"></a>列 2: IETF RFC 8200: "Internet Protocol, Version 6 (IPv6) Specification".

<a id="T139-R10"></a>
**T139-R10**

- <a id="T139-R10-C01"></a>列 1: [x9]
- <a id="T139-R10-C02"></a>列 2: 3GPP TS 26.114: "IP Multimedia Subsystem (IMS); Multimedia telephony; Media handling and interaction".

<a id="T139-R11"></a>
**T139-R11**

- <a id="T139-R11-C01"></a>列 1: [x10]
- <a id="T139-R11-C02"></a>列 2: IETF RFC 2507: "IP Header Compression".

<a id="T139-R12"></a>
**T139-R12**

- <a id="T139-R12-C01"></a>列 1: [x11]
- <a id="T139-R12-C02"></a>列 2: 3GPP TS 36.213: "Evolved Universal Terrestrial Radio Access (E-UTRA); Physical layer procedures".

<a id="P141"></a>

* * * First Change * * *

<a id="P142"></a>

Editor's note: This candidate text is FFS pending: (1) RAN2 agreement on signalling RTP/UDP/IP RoHC profiles for NB-IoT; (2) RAN2 agreement on the handling of packets that exceed the steady-state transport block in both directions; and (3) SA2 confirmation of the RTCP scope.

<a id="P143"></a>

## 3    IP transport mechanism

<a id="P144"></a>

## 3.1    General

<a id="P145"></a>

The IP transport mechanism shall be supported, as required by clause 5.2.1 of TR 26.940 [x1].

<a id="P146"></a>

A ULBC voice packet shall be carried as RTP over UDP over IP on a user-plane radio bearer. If RAN2 specifies support for RTP/UDP/IP RoHC profiles on NB-IoT bearers, RoHC may compress the header chain between the PDCP entities in the UE and eNB in accordance with TS 36.323 [x2], clause 5.5. The eNB shall reconstruct the original RTP/UDP/IP packet before forwarding it over S1-U.

<a id="P147"></a>

NOTE 1:  The non-IP mechanism in TR 26.940 [x1], clause 5.2.1, is optional for both the UE and the network. Under that mechanism, the PGW removes and restores the UDP and IP headers, while the UE removes and restores the RTP header. A UE or network that does not support the optional non-IP mechanism uses the mandatory IP mechanism defined in this clause.

<a id="P148"></a>

## 3.2    Protocol stack

<a id="P149"></a>

The user-plane protocol stack is shown in figure 3.2-1. The protocol layers are the same in the uplink and in the downlink; RAN2 specifies the bearer configuration and transport-block selection in each direction.

<a id="P151"></a>

Figure 3.2-1: User-plane protocol stack for IMS voice over NB-IoT NTN

<a id="P152"></a>

RTP, UDP and IP are peers between the UE and the remote endpoint. No network element removes or rewrites them. Header compression is applied only between the PDCP entity of the UE and that of the eNB.

<a id="P153"></a>

The uncompressed protocol headers are 12 octets for RTP, 8 octets for UDP, 20 octets for IPv4 and 40 octets for IPv6. The radio-protocol layers add 1 octet of PDCP header, 1 octet of RLC UM header and 1 to 3 octets of MAC header.

<a id="P154"></a>

NOTE 2:    Clause 6.3.2 of TS 36.323 [x2] fixes the PDCP SN at 7 bits for an NB-IoT DRB, and clause 6.2.1.3 of TS 36.322 [x3] fixes the RLC UM SN at 5 bits with a one-octet fixed header. Neither value is configurable for this bearer. Clause 6.1.2 of TS 36.321 [x4] omits the L field from the last subheader of a MAC PDU, so a MAC PDU carrying one SDU adds one octet. Clause 5.2.3 of TR 26.940 [x1] assumes 3 octets for the MAC header.

<a id="P155"></a>

## 3.3    Evaluated radio bearer

<a id="P156"></a>

For the configuration evaluated in this clause, the ULBC media stream and IMS signalling are mapped to separate DRBs of the same PDN connection.

<a id="P157"></a>

The evaluated uplink DRB uses RLC UM and a semi-persistent grant whose period equals the bundling period.

<a id="P158"></a>

One steady-state ULBC voice packet occupies one transport block.

<a id="P159"></a>

NOTE 3:    TS 36.331 [x5] limits an NB-IoT UE to two DRBs (maxDRB-NB-r13), which is the number this configuration uses. A separate DRB gives the media stream its own PDCP entity and therefore, under clause 5.5.3 of TS 36.323 [x2], its own RoHC channel and its own context identifier space.

<a id="P160"></a>

The evaluated PDCP discard timer is greater than one bundling period.

<a id="P161"></a>

NOTE 4:    A packet awaiting its configured occasion is otherwise discarded before it can be sent.

<a id="P162"></a>

## 3.4    Evaluated RoHC profile

<a id="P163"></a>

The evaluation uses RoHC profile 0x0001 in addition to profile 0x0000, as specified in clause 5.5.1 of TS 36.323 [x2].

<a id="P164"></a>

Where both profile 0x0001 and profile 0x0101 are supported by the UE and the network, the evaluation signals only profile 0x0001.

<a id="P165"></a>

NOTE 5:    TS 36.331 [x5] applies the higher profile identifier when two profiles share their eight least significant bits. Profile 0x0101 settles one octet above profile 0x0001 at the ULBC packetisation intervals unless its timestamp stride is established, because RFC 5225 [x6] gives it an initial stride of 160, which corresponds to 20 ms at 8 kHz.

<a id="P166"></a>

## 3.5    Evaluated channel parameters

<a id="P167"></a>

Table 3.5-1 lists the values used in the evaluation and the entity or mechanism that controls each value. Values controlled by RRC, the endpoints or the RoHC implementation are evaluation assumptions and are not SA4 requirements.

<a id="P168"></a>

Table 3.5-1: RoHC configuration for the ULBC bearer

<a id="T169"></a>

<a id="T169-R01"></a>
**T169-R01**

- <a id="T169-R01-C01"></a>列 1: Parameter
- <a id="T169-R01-C02"></a>列 2: Value
- <a id="T169-R01-C03"></a>列 3: Responsible entity or mechanism

<a id="T169-R02"></a>
**T169-R02**

- <a id="T169-R02-C01"></a>列 1: RoHC profile
- <a id="T169-R02-C02"></a>列 2: 0x0001, with 0x0000
- <a id="T169-R02-C03"></a>列 3: RRC, profiles

<a id="T169-R03"></a>
**T169-R03**

- <a id="T169-R03-C01"></a>列 1: MAX_CID
- <a id="T169-R03-C02"></a>列 2: 1
- <a id="T169-R03-C03"></a>列 3: RRC, maxCID

<a id="T169-R04"></a>
**T169-R04**

- <a id="T169-R04-C01"></a>列 1: Voice context CID
- <a id="T169-R04-C02"></a>列 2: 0
- <a id="T169-R04-C03"></a>列 3: Compressor

<a id="T169-R05"></a>
**T169-R05**

- <a id="T169-R05-C01"></a>列 1: LARGE_CIDS
- <a id="T169-R05-C02"></a>列 2: FALSE
- <a id="T169-R05-C03"></a>列 3: Inferred from MAX_CID

<a id="T169-R06"></a>
**T169-R06**

- <a id="T169-R06-C01"></a>列 1: RoHC channel
- <a id="T169-R06-C02"></a>列 2: Bidirectional
- <a id="T169-R06-C03"></a>列 3: PDCP-Config-NB-r13

<a id="T169-R07"></a>
**T169-R07**

- <a id="T169-R07-C01"></a>列 1: RoHC operating mode
- <a id="T169-R07-C02"></a>列 2: O-mode
- <a id="T169-R07-C03"></a>列 3: Compressor and decompressor, in band

<a id="T169-R08"></a>
**T169-R08**

- <a id="T169-R08-C01"></a>列 1: MRRU
- <a id="T169-R08-C02"></a>列 2: Not used
- <a id="T169-R08-C03"></a>列 3: TS 36.323 [x2]

<a id="T169-R09"></a>
**T169-R09**

- <a id="T169-R09-C01"></a>列 1: TS_STRIDE
- <a id="T169-R09-C02"></a>列 2: Clock rate times bundling period
- <a id="T169-R09-C03"></a>列 3: Compressor, in band

<a id="T169-R10"></a>
**T169-R10**

- <a id="T169-R10-C01"></a>列 1: UDP checksum
- <a id="T169-R10-C02"></a>列 2: Carried
- <a id="T169-R10-C03"></a>列 3: Session description

<a id="T169-R11"></a>
**T169-R11**

- <a id="T169-R11-C01"></a>列 1: RTCP
- <a id="T169-R11-C02"></a>列 2: Not carried on this bearer
- <a id="T169-R11-C03"></a>列 3: Evaluation assumption

<a id="T169-R12"></a>
**T169-R12**

- <a id="T169-R12-C01"></a>列 1: PDCP SN
- <a id="T169-R12-C02"></a>列 2: 7 bits
- <a id="T169-R12-C03"></a>列 3: Fixed for NB-IoT

<a id="T169-R13"></a>
**T169-R13**

- <a id="T169-R13-C01"></a>列 1: RLC mode
- <a id="T169-R13-C02"></a>列 2: UM, bidirectional
- <a id="T169-R13-C03"></a>列 3: RRC, rlc-Config

<a id="P171"></a>

The evaluation uses CID 0 for the context carrying the ULBC media stream.

<a id="P172"></a>

NOTE 6:    A context on a CID other than 0 carries an Add-CID octet in every packet under clause 5.2 of RFC 3095 [x7]. This adds one octet per packet and changes the selected transport block for three of the four bitrate and bundling-period combinations in table 3.10-2.

<a id="P173"></a>

NOTE 7:  TS 36.323 [x2], clause 5.5.3, requires one CID value to be reserved for uncompressed flows. The evaluation assigns CID 0 to the ULBC media context and CID 1 to the reserved uncompressed context.

<a id="P174"></a>

NOTE 8:    PDCP-Config-NB-r13 offers headerCompression and no uplink-only alternative, so the channel is bidirectional for this bearer and is not a configuration choice. Decompressor feedback is carried as an interspersed PDCP Control PDU under clause 5.5.6 of TS 36.323 [x2], which carries no PDCP SN and is not ciphered.

<a id="P175"></a>

## 3.6    Evaluated timestamp stride

<a id="P176"></a>

The evaluation establishes a timestamp stride equal to the RTP clock rate multiplied by the bundling period, and re-establishes it when the bundling period changes. At an 8 kHz clock rate the stride is 640 for 80 ms bundling and 1280 for 160 ms bundling.

<a id="P177"></a>

NOTE 9:    TS_STRIDE is not among the channel parameters configured under clause 5.5.3 of TS 36.323 [x2]. It is a per-context control field set in band by the compressor and is therefore specified here rather than signalled by RRC.

<a id="P178"></a>

## 3.7    IP version and UDP checksum

<a id="P179"></a>

The session description and UDP-checksum treatment are outside the scope of this candidate text. The evaluation identifies the IP version used for the media flow and carries the UDP checksum.

<a id="P180"></a>

UDP checksum elision is not used with IPv6.

<a id="P181"></a>

NOTE 10:    A carried checksum contributes two octets per compressed packet. Clause 8.1 of RFC 8200 [x8] requires an IPv6 receiver to discard a UDP datagram with a zero checksum, so elision is available for IPv4 only.

<a id="P182"></a>

NOTE 11:    When the UDP checksum is carried, the steady-state compressed header is 3 octets for both IPv4 and IPv6, so the IP version does not change the steady-state header budget. It does change the size of an IR packet, as shown in table 3.10-1.

<a id="P183"></a>

If SA2 specifies that RTCP is not sent during the voice call, the session description shall set the RTCP bandwidth modifiers RR and RS to zero.

<a id="P184"></a>

NOTE 12: TS 26.114 [x9], clause 7.3.1, permits RTCP to be disabled for a point-to-point speech-only session by setting RR and RS to zero, and recommends renegotiating RR above zero while media is on hold. Carrying RTCP on the evaluated bearer would require an additional UDP flow and RoHC context and is outside the packet budget evaluated in this clause.

<a id="P185"></a>

## 3.8    Evaluated operating mode and context refresh

<a id="P186"></a>

The evaluation uses Bidirectional Optimistic mode (O-mode), as specified in clause 5.4 of RFC 3095 [x7].

<a id="P187"></a>

A context refresh is sent in response to decompressor feedback. No periodic refresh interval is evaluated for this bearer.

<a id="P188"></a>

NOTE 13:    Clause 4.4.2 of RFC 3095 [x7] states that periodic refreshes are not used in Bidirectional Optimistic mode, and clause 5.4.1.1 that the mode uses no timeouts. The compressor sends an IR on a STATIC-NACK and an IR-DYN on a NACK.

<a id="P189"></a>

Unidirectional mode applies until the decompressor initiates the mode transition in accordance with clause 5.6.2 of RFC 3095 [x7]. Where the decompressor does not initiate the transition, the compressor refreshes the context periodically as required by clause 5.3.1.1.2 of RFC 3095 [x7], with an interval that is an implementation matter.

<a id="P190"></a>

NOTE 14: A criterion based on average header size, such as RFC 2507 [x10], clause 3.3.4, does not determine the required transport block for this bearer. The bearer allocates one fixed transport block per bundling period, not an average bit rate.

<a id="P191"></a>

The handling of a RoHC packet larger than the transport block is FFS by RAN2. The evaluation does not assume that RLC segmentation over successive semi-persistent occasions meets the voice-delay budget.

<a id="P192"></a>

NOTE 15: TS 36.323 [x2], clause 5.5.3, specifies that MRRU is not used, so RoHC cannot segment its own packets. Across the combinations in table 3.10-2 and both IP versions, an IR packet requires 2.0 to 4.4 times the configured transport block, corresponding to two to five steady-state grant occasions. RAN2 needs to specify the scheduling and delay behaviour for such packets.

<a id="P193"></a>

NOTE 16: In the implementation measurement, the decompressor recovered after up to 13 consecutive packet losses and failed after 14. This result is implementation evidence only and does not define a normative threshold for requesting a refresh.

<a id="P194"></a>

## 3.9    Delay variation

<a id="P195"></a>

After the RoHC context is established, each packet of an evaluated constant-rate media flow uses a 3-octet UO-0 header. Header compression therefore introduces no packet-size variation during steady-state speech.

<a id="P196"></a>

NOTE 17:    The packet size changes at context establishment, when the decompressor requests a refresh, and at the onset of a talkspurt where discontinuous transmission is used.

<a id="P197"></a>

At talkspurt onset, the RTP timestamp advances by more than the sequence-number progression predicts. In the implementation measurement, the compressor emitted UO-1-TS after a pause shorter than 24 packet intervals and UOR-2-TS after a longer pause. These headers were 4 and 6 octets, respectively, compared with 3 octets in steady state.

<a id="P198"></a>

NOTE 18: The resulting packet exceeds the transport block in table 3.10-2 for all evaluated cases except 1.4 kbit/s with 160 ms bundling and a pause shorter than 24 packet intervals, where it exactly fills the block. TR 26.940 [x1], clause 6.1, identifies discontinuous transmission as a ULBC design constraint; oversized talkspurt-onset packets can therefore occur during normal operation. Their handling is FFS by RAN2.

<a id="P199"></a>

## 3.10    Resulting header and transport block sizes

<a id="P200"></a>

Table 3.10-1 lists the measured RoHC packet sizes for the configuration in clauses 3.4 to 3.8. Table 3.10-2 gives the resulting minimum transport block for steady-state speech.

<a id="P201"></a>

Table 3.10-1: Size of each RoHC packet type

<a id="T202"></a>

<a id="T202-R01"></a>
**T202-R01**

- <a id="T202-R01-C01"></a>列 1: Packet
- <a id="T202-R01-C02"></a>列 2: IPv4
- <a id="T202-R01-C03"></a>列 3: IPv6
- <a id="T202-R01-C04"></a>列 4: Sent when

<a id="T202-R02"></a>
**T202-R02**

- <a id="T202-R02-C01"></a>列 1: IR
- <a id="T202-R02-C02"></a>列 2: 41 octets
- <a id="T202-R02-C03"></a>列 3: 64 octets
- <a id="T202-R02-C04"></a>列 4: at context establishment and on a STATIC-NACK

<a id="T202-R03"></a>
**T202-R03**

- <a id="T202-R03-C01"></a>列 1: IR-DYN
- <a id="T202-R03-C02"></a>列 2: 23 octets
- <a id="T202-R03-C03"></a>列 3: 20 octets
- <a id="T202-R03-C04"></a>列 4: when a dynamic field changes, and on a NACK

<a id="T202-R04"></a>
**T202-R04**

- <a id="T202-R04-C01"></a>列 1: Compressed
- <a id="T202-R04-C02"></a>列 2: 3 octets
- <a id="T202-R04-C03"></a>列 3: 3 octets
- <a id="T202-R04-C04"></a>列 4: on every other packet of a constant-rate voice flow

<a id="P204"></a>

NOTE 19:    The compressed size is 1 octet for IPv4 where the UDP checksum is elided. The IR is 39 octets for IPv4 and 62 octets for IPv6 where the compressor does not carry the timestamp stride and the decompressor infers it.

<a id="P205"></a>

Table 3.10-2: Transport block per bitrate and bundling period, at 8 octets of overhead

<a id="T206"></a>

<a id="T206-R01"></a>
**T206-R01**

- <a id="T206-R01-C01"></a>列 1: Bitrate and bundling
- <a id="T206-R01-C02"></a>列 2: Payload
- <a id="T206-R01-C03"></a>列 3: With overhead
- <a id="T206-R01-C04"></a>列 4: Transport block
- <a id="T206-R01-C05"></a>列 5: Spare

<a id="T206-R02"></a>
**T206-R02**

- <a id="T206-R02-C01"></a>列 1: 1.0 kbit/s, 80 ms
- <a id="T206-R02-C02"></a>列 2: 10 octets
- <a id="T206-R02-C03"></a>列 3: 18 octets
- <a id="T206-R02-C04"></a>列 4: 144 bits
- <a id="T206-R02-C05"></a>列 5: 0 octets

<a id="T206-R03"></a>
**T206-R03**

- <a id="T206-R03-C01"></a>列 1: 1.4 kbit/s, 80 ms
- <a id="T206-R03-C02"></a>列 2: 14 octets
- <a id="T206-R03-C03"></a>列 3: 22 octets
- <a id="T206-R03-C04"></a>列 4: 176 bits
- <a id="T206-R03-C05"></a>列 5: 0 octets

<a id="T206-R04"></a>
**T206-R04**

- <a id="T206-R04-C01"></a>列 1: 1.0 kbit/s, 160 ms
- <a id="T206-R04-C02"></a>列 2: 20 octets
- <a id="T206-R04-C03"></a>列 3: 28 octets
- <a id="T206-R04-C04"></a>列 4: 224 bits
- <a id="T206-R04-C05"></a>列 5: 0 octets

<a id="T206-R05"></a>
**T206-R05**

- <a id="T206-R05-C01"></a>列 1: 1.4 kbit/s, 160 ms
- <a id="T206-R05-C02"></a>列 2: 28 octets
- <a id="T206-R05-C03"></a>列 3: 36 octets
- <a id="T206-R05-C04"></a>列 4: 296 bits
- <a id="T206-R05-C05"></a>列 5: 1 octet

<a id="P208"></a>

NOTE 20:    The transport block is the smallest value of table 16.5.1.2-2 of TS 36.213 [x11] that holds the payload and the 8 octets of overhead assumed in clause 5.2.3 of TR 26.940 [x1]. The resource-unit count, repetition number and air time that carry the block are not specified in this clause.

<a id="P209"></a>

* * * End of Changes * * *
