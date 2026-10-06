# S4aA260112 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260112_delay_characteristics.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG SA WG4 Audio SWG Meeting on ULBC-MED    S4aA260112

<a id="P001"></a>

Shanghai, Sep 28-30, 2026                                   Revision of S4-261646

<a id="P002"></a>

Title:    [ULBC-MED] ULBC-9: Delay Characteristics for RTP Header Reduction and MTSI Integration

<a id="P004"></a>

Source:    Qualcomm Incorporated

<a id="P005"></a>

Agenda item:    4.9

<a id="P006"></a>

Document for:    Agreement

<a id="P009"></a>

## 1 Introduction

<a id="P010"></a>

The delay characteristics of the voice packets affect the design choice of the RTP header reduction and MTSI integration for IMS voice over NB-IoT NTN with GEO. This paper proposes to agree to two assumptions on the delay characteristics and note that they are not normative.

<a id="P014"></a>

## 2 GEO channel delay characteristics

<a id="P016"></a>

TR 26.940 adopts HARQ feedback disabling for the data radio bearer which carries voice packets, due to the large delay over the GEO channel, and therefore, there is no HARQ caused out-of-order delivery over the GEO channel.

<a id="P017"></a>

Also, the variation of the propagation delay between a GEO satellite and a UE is negligible (see Table 7.1-1 in [1]). As an example, for 100km/h UE, the delay drift is less than 6µs per minute. Therefore, the delay jitter over the GEO channel is negligible compared to SPS periodicity. We propose to agree to the following assumption.

<a id="P019"></a>

Assumption 1: The delay jitter for voice packets carried by the non-IP delivery mechanism over the GEO channel (between the UE and the eNB) is negligible (less than 0.1ms) compared to SPS periodicity.

<a id="P035"></a>

## 3 Network delay characteristics

<a id="P036"></a>

The network path between the eNB and the PGW and the path between the PGW and the AGW contribute to the E2E delay and we assume that the aggregate delay of the two paths is less than 20ms. The two paths are controlled by the network operator and can be optimized to reduce the delay jitter, which is less than 3ms. Also, the delay jitter over the GEO channel is negligible, as little as 6µs per minute even for a 100km/h UE. Given that the SPS periodicity is 80ms or higher, we can assume that the jitter between the UE at the GEO link and the AGW is negligible compared to the SPS periodicity.

<a id="P038"></a>

We propose to agree to the following assumption.

<a id="P039"></a>

Assumption 2: For IMS voice carried by the non-IP delivery mechanism over NB-IoT NTN with GEO, the delay jitter of the network between the UE at the GEO link and the AGW is negligible (less than 3ms) compared to the SPS periodicity.

<a id="P041"></a>

## 4. Proposal

<a id="P042"></a>

To summarize, we have the following proposal.

<a id="P044"></a>

Proposal: we propose to agree to and document in P-Doc ULBC-9 the following assumptions for RTP header reduction and MTSI integration for IMS voice over NB-IoT NTN with GEO:

<a id="P045"></a>

Assumption 1: The delay jitter for voice packets carried by the non-IP delivery mechanism over the GEO channel is negligible (less than 0.1ms) compared to the SPS periodicity.

<a id="P051"></a>

Assumption 2: For IMS voice carried by the non-IP delivery mechanism over NB-IoT NTN with GEO, the delay jitter of the network between the UE at the GEO link and the AGW is negligible (less than 3ms) compared to the SPS periodicity.

<a id="P053"></a>

NOTE: the assumptions are not normative.

<a id="P057"></a>

References

<a id="P061"></a>

[1] TR 38.821, Solutions for NR to support Non-Terrestrial Networks (NTN).
