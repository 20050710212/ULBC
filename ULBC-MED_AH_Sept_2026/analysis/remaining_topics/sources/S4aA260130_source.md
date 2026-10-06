# S4aA260130 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260130.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    China Mobile

<a id="P001"></a>

Title:    [ULBC-MED] Transport Options and Protocol Overhead

<a id="P002"></a>

Document for:    Discussion and agreement

<a id="P003"></a>

Agenda Item:    4.9

<a id="P005"></a>

Introduction

<a id="P006"></a>

This document captures the transport options agreed by SA2 for GEO voice and identifies in which case the RTP header needs to be reduced.

<a id="P008"></a>

Transport Options and Protocol Overhead

<a id="P009"></a>

## 2.1  Transport Options

<a id="P010"></a>

Two primary transport options are identified for GEO voice:

<a id="P011"></a>

Option A : IP-based transport with ROHC (mandatory)

<a id="P012"></a>

Option B: UDP/IP Header Removal & Restoration (UHRR）transport (optional)

<a id="P014"></a>

Option A — IP-based Transport with ROHC (mandatory)

<a id="P015"></a>

In this option, voice packets traverse the satellite link in their standard IP/UDP/RTP form, with ROHC applied over the satellite radio interface to compress the protocol headers.

<a id="P016"></a>

Protocol stack without ROHC，

<a id="P017"></a>

+------------------------+

<a id="P018"></a>

|     Voice Payload      |

<a id="P019"></a>

+------------------------+

<a id="P020"></a>

|          RTP           |  12 bytes

<a id="P021"></a>

+------------------------+

<a id="P022"></a>

|          UDP           |   8 bytes

<a id="P023"></a>

+------------------------+

<a id="P024"></a>

|      IPv6 / IPv4       |  40 bytes (IPv6) / 20 bytes (IPv4)

<a id="P025"></a>

+------------------------+

<a id="P026"></a>

|    Satellite Radio     |  LTE/NR PHY + satellite layers

<a id="P027"></a>

+------------------------+

<a id="P028"></a>

Protocol stack with ROHC,

<a id="P029"></a>

+------------------------+

<a id="P030"></a>

|     Voice Payload      |

<a id="P031"></a>

+------------------------+

<a id="P032"></a>

|     ROHC                 |  ~1–5 Bytes

<a id="P033"></a>

+------------------------+

<a id="P034"></a>

|    Satellite Radio     |  LTE/NR PHY + satellite layers

<a id="P036"></a>

ROHC profile applicability:

<a id="P037"></a>

ROHC RTP Profile (Profile 0x0001) — Used for RTP/UDP/IP compression.

<a id="P038"></a>

The ROHC configuration (e.g. header size modes) is negotiated at session establishment or via RRC signalling.

<a id="P041"></a>

Protocol overhead per packet (Option A, assuming IPv6, ROHC, voice payload of 10 bytes — ULBC at 1.0 kbps, 80 ms frame)

<a id="P042"></a>

Table 2.2.1  Protocol Overhead per Packet — Option A

<a id="T043"></a>

<a id="T043-R01"></a>
**T043-R01**

- <a id="T043-R01-C01"></a>列 1: Component
- <a id="T043-R01-C02"></a>列 2: Size (bytes)
- <a id="T043-R01-C03"></a>列 3: Notes

<a id="T043-R02"></a>
**T043-R02**

- <a id="T043-R02-C01"></a>列 1: Voice payload
- <a id="T043-R02-C02"></a>列 2: 10
- <a id="T043-R02-C03"></a>列 3: ULBC 1.0kbps, 80 ms

<a id="T043-R03"></a>
**T043-R03**

- <a id="T043-R03-C01"></a>列 1: RTP header
- <a id="T043-R03-C02"></a>列 2: 12
- <a id="T043-R03-C03"></a>列 3: Fixed RTP header

<a id="T043-R04"></a>
**T043-R04**

- <a id="T043-R04-C01"></a>列 1: UDP header
- <a id="T043-R04-C02"></a>列 2: 8
- <a id="T043-R04-C03"></a>列 3: -

<a id="T043-R05"></a>
**T043-R05**

- <a id="T043-R05-C01"></a>列 1: IPv6 header
- <a id="T043-R05-C02"></a>列 2: 40
- <a id="T043-R05-C03"></a>列 3: -

<a id="T043-R06"></a>
**T043-R06**

- <a id="T043-R06-C01"></a>列 1: ROHC overhead
- <a id="T043-R06-C02"></a>列 2: 1-5
- <a id="T043-R06-C03"></a>列 3: long-term average

<a id="T043-R07"></a>
**T043-R07**

- <a id="T043-R07-C01"></a>列 1: Total (end-to-end)
- <a id="T043-R07-C02"></a>列 2: 70
- <a id="T043-R07-C03"></a>列 3: Standard header

<a id="T043-R08"></a>
**T043-R08**

- <a id="T043-R08-C01"></a>列 1: Total over satellite link
- <a id="T043-R08-C02"></a>列 2: ~13
- <a id="T043-R08-C03"></a>列 3: With ROHC compression

<a id="P045"></a>

Option B — UHRR-enabled Transport (optional)

<a id="P046"></a>

UHRR is a header reduction mechanism defined in TS 23.401. UHRR replaces the full RTP/UDP/IP header stack with a compact reduction header over the air/satellite interface.

<a id="P047"></a>

Protocol stack

<a id="P048"></a>

+------------------------+

<a id="P049"></a>

|     Voice Payload      |

<a id="P050"></a>

+------------------------+

<a id="P051"></a>

|     UHRR Header        |

<a id="P052"></a>

+------------------------+

<a id="P053"></a>

|    Satellite Radio     |  LTE/NR PHY + satellite layers

<a id="P054"></a>

Protocol overhead per packet (Option B, voice payload 10 bytes):

<a id="P055"></a>

Table 2.2.2 Protocol Overhead per Packet — Option B

<a id="T057"></a>

<a id="T057-R01"></a>
**T057-R01**

- <a id="T057-R01-C01"></a>列 1: Component
- <a id="T057-R01-C02"></a>列 2: Size (bytes)
- <a id="T057-R01-C03"></a>列 3: Notes

<a id="T057-R02"></a>
**T057-R02**

- <a id="T057-R02-C01"></a>列 1: Voice payload
- <a id="T057-R02-C02"></a>列 2: 10
- <a id="T057-R02-C03"></a>列 3: ULBC 1.0kbps, 80 ms

<a id="T057-R03"></a>
**T057-R03**

- <a id="T057-R03-C01"></a>列 1: UHRR header
- <a id="T057-R03-C02"></a>列 2: 3
- <a id="T057-R03-C03"></a>列 3: Compact reduction header

<a id="T057-R04"></a>
**T057-R04**

- <a id="T057-R04-C01"></a>列 1: Total over satellite link
- <a id="T057-R04-C02"></a>列 2: ~13
- <a id="T057-R04-C03"></a>列 3: —

<a id="P060"></a>

## 2.2   Criteria for Applicability

<a id="P061"></a>

UHRR is applicable for GEO voice when all of the following conditions are satisfied:

<a id="P062"></a>

Access type: The voice session is established over a GEO satellite access.

<a id="P063"></a>

Bandwidth constraint: The available satellite bandwidth is limited, and the reduction in protocol overhead provides a meaningful bandwidth saving (e.g. in bandwidth-constrained beam scenarios or when serving a large number of concurrent voice users).

<a id="P064"></a>

UE capability: The UE is UHRR-enabled and has indicated UHRR support in its capability signalling.

<a id="P065"></a>

Network support: The gateways support UHRR functionality and are configured to enable header reduction for the applicable QoS flows.

<a id="P066"></a>

Payload type compatibility: The voice codec payload type is known at session establishment and is among the payload types for which UHRR context can be established..

<a id="P067"></a>

Session stability: The voice session is expected to be stable (i.e. the flow is not expected to change RTP payload type frequently), as UHRR context renegotiation introduces overhead and delay.

<a id="P069"></a>

When the voice session involves handover across both terrestrial and GEO satellite access paths or frequent payload type switching, the UHRR context renegotiation overhead may outweigh the header reduction benefit.In fallback scenarios, the session continues with ROHC or standard RTP/UDP/IP transport as a fallback due to UHRR mismatch.

<a id="P071"></a>

proposal

<a id="P072"></a>

For transport options and protocol overhead, update clause 2 in ULBC-9.

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH    Tdoc S4aA260130<br>    Shanghai, China, September 28-30, 2026
