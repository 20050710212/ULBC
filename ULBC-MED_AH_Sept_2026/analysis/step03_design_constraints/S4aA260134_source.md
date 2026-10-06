# S4aA260134 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260134 On ULBC4 Discontinuous transmission.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWG Ad-hoc on ULBC-MED    S4aA260134

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC-4: Discontinuous transmission

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Agreement

<a id="P009"></a>

The present document proposes clarifications and updates for design constraints Pdoc ULBC-4 (S4-261847). The focus in this document is on the design constraint discontinuous transmission.

<a id="P012"></a>

The latest version of ULBC-4 (S4-261847) contains the following proposal on DTX:

<a id="T014"></a>

<a id="T014-R01"></a>
**T014-R01**

- <a id="T014-R01-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T014-R01-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).
- <a id="T014-R01-C03"></a>列 3: Agreed (TR 26.940 [1] Table 6.1-1).<br>Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS.

<a id="P016"></a>

3GPP codecs such as AMR-WB or EVS have a dedicated bitrate/fram size for the SID frame which differs from the regular codec rates for active speech. According to the recent discussion, this is not possible for ULBC over the NTN NB-IoT link, as the TBS stays constant, even for DTX transmission. This means for sending a SID update, an entire packet of bundled frames must be transmitted. The source requests to add this clarification to the definition of the DTX design constraint.

<a id="P018"></a>

Additionally, a SID update rate is proposed based on the EVS design constraint given in EVS-4: “SID update frames shall be sent with a frequency not exceeding once per 8 frames”. To translate the EVS design constraint to ULBC, the timing unit "frame" needs to be replaced by "bundled packet". This should result in a similar active transmission time compared to EVS for a complete session.

<a id="P020"></a>

The following table contains a complete text proposal for updating the ULBC DTX design constraint.

<a id="T022"></a>

<a id="T022-R01"></a>
**T022-R01**

- <a id="T022-R01-C01"></a>列 1: Discontinuous transmission (DTX / CNG)
- <a id="T022-R01-C02"></a>列 2: The ULBC candidate codecs shall provide a framework for voice activity detection (VAD) and discontinuous transmission (DTX) with comfort noise generation (CNG).<br><br>    SID frames shall be transmitted within bundled packets. SID update frames shall be sent with a frequency not exceeding once per [8] bundled packets.
- <a id="T022-R01-C03"></a>列 3: ~~Agreed (TR 26.940 [1] Table 6.1-1).~~<br>~~Editor's note: detailed DTX behaviour (SID interval, hangover) and Rel-20 phasing are FFS. RAN2 agreed DTX with SPS~~.

<a id="P024"></a>

It is proposed to transfer the text to ULBC-4 and agree on the proposal.

<a id="P028"></a>

[1] http://ftp.3gpp.org/tsg_sa/WG4_CODEC/TSGS4_74/Docs/S4-130778.zip
