# S4aA260113 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260113_DTMF.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG SA WG4 Audio SWG Meeting on ULBC-MED     S4aA260113

<a id="P001"></a>

Shanghai, Sep 28-30, 2026                                                                Revision of S4-261468

<a id="P002"></a>

Title:    [ULBC-MED] ULBC-9: DTMF with non-IP delivery over NB-IoT NTN

<a id="P004"></a>

Source:    Qualcomm Incorporated, vivo

<a id="P005"></a>

Agenda item:    7.7 ULBC-MED

<a id="P006"></a>

Document for:    Agreement

<a id="P009"></a>

## 1 Background

<a id="P010"></a>

It was agreed in TR 26.940 that DTMF will be supported for the non-IP transport of IMS voice over NB-IoT NTN:

<a id="P012"></a>

For IMS voice over NB-IoT NTN, Dual Tone Multi-frequency (DTMF) is required to be supported [3]. Morever, according to [26], for "non-IP" mechanism to transport voice packets, the modified RTP header in non-IP has to be able to support DTMF.

<a id="P014"></a>

Specifically, the reference “[3]”, TR23.700-19, in the above quote concluded the “Study on Integration of satellite components in the 5G architecture; Phase 4” with the following conclusion in clause 8.2:

<a id="P016"></a>

-    Dual-Tone Multi-Frequency (DTMF) is supported for IMS voice over NB IoT NTN and the modified RTP header has to be able to support DTMF.

<a id="P018"></a>

There was a proposal S4-261098 [6] to have a separate work item in parallel to ULBC-MED to specify MTSI system integration for IMS voice over NB-IoT NTN including DTMF. The proposal was merged to ULBC-MED WID but without DTMF being explicitly spelled out. Given the above references TR 26.940 and TR 23.700-19, and the handling of the proposal S4-261098 [6], it is clear that DTMF needs to be supported.

<a id="P020"></a>

Next, we give an overview of DTMF. DTMF conveys the action of a user pressing some key on the user’s terminal. There are 16 keys that need to be supported: 0-9, A, B, C, D, *, #.

<a id="P022"></a>

In some applications, not only the key pressed, but also the duration of the action needs to be conveyed.

<a id="P024"></a>

At SA4 #135-bis-e, design options for DTMF were proposed [1], including the design specified in TS 26.114 for IMS. At SA4 #136, design considerations for DTMF were discussed in [2]. Additionally, TS23.014 [3] specified another design for circuit switching.

<a id="P026"></a>

There are four design options: a DTMF event (i.e., pressing a key) is conveyed

<a id="P027"></a>

as a telephone event, by RTP with the payload type different from voice, as described in TS26.114 Annex G, which is based on RFC 4733 [4].

<a id="P028"></a>

as a single digit, and at the receiver the tone lasts until an indicator (STOP DTMF) is received. The indicator is transmitted only after an acknowledgement from the receiver reaches the sender. This is described in TS23.014.

<a id="P029"></a>

as an audio signal by RTP with the same payload type as voice.

<a id="P030"></a>

in SIP INFO payloads, as described in RFC2976 [5].

<a id="P032"></a>

This paper discusses the DTMF design options.

<a id="P034"></a>

## 2 Analysis and proposal

<a id="P035"></a>

Design option 1 provides a rich set of functionalities including the duration, the event end indicator (the end bit), and volume. The payload size is 4 bytes (RFC 4733), significantly smaller than the smallest voice frame, which is 14 bytes (1.4kbps x 80ms). Considering that a user is likely to be silent when he/she presses a key after a prompt, a DTMF transmission can utilize the otherwise vacant SPS resource during the silence period and thus avoid competing with active voice packets.

<a id="P036"></a>

Design option 2 requires transmitting 2 messages in the UL and 2 messages in the DL for each DTMF event. Besides the communication overhead, this forces the tone duration to be at least 500ms, which is undesirable.

<a id="P037"></a>

Design option 3 requires the voice encoder to encode the tones corresponding to the keys as speech signals. It is unclear how much this will add to the speech codec complexity and impact testing. This uncertainty coupled with the tight timeline of the work item makes this option less desirable.

<a id="P038"></a>

Design option 4 requires the transmission of a SIP message for each DTMF event. Typically, a SIP message is much larger than a ULBC speech frame, leading to a significant communication overhead.

<a id="P039"></a>

Given the analysis, we propose to adopt design option 1 with the additional work to reduce the size of the RTP header.

<a id="P040"></a>

Proposal: To support DTMF with non-IP delivery for IMS voice over NB-IoT NTN with GEO, convey a DTMF event as a telephone event by a header reduced RTP packet.

<a id="P041"></a>

NOTE: FFS how to differentiate DTMF and voice

<a id="P043"></a>

References

<a id="P044"></a>

[1] S4-260824, Support for DTMF and non-IP delivery of IMS voice over NB-IoT NTN, Qualcomm, 3GPP SA4 #135-bis-e.

<a id="P045"></a>

[2] S4-261125, On DTMF, Fraunhofer IIS, 3GPP SA4 #136, Montreal.

<a id="P046"></a>

[3] RFC 4733, RTP Payload for DTMF Digits, Telephony Tones, and Telephony Signals.

<a id="P047"></a>

[4] TS 23.014, Support of Dual Tone Multi-Frequency (DTMF) signalling.

<a id="P048"></a>

[5] RFC 2976, The SIP INFO Method.

<a id="P049"></a>

[6] [Draft] New WID on MTSI integration for IMS Voice over GEO Satellites, SA4-136, Montreal, Qualcomm, vivo, ViaSat, Skylo.
