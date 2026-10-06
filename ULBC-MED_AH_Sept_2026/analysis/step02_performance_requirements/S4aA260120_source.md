# S4aA260120 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260120 [ULBC-MED] Update on ULBC Performance Requirements.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Fraunhofer IIS

<a id="P001"></a>

Title:    [ULBC_MED] Update on ULBC performance requirements

<a id="P002"></a>

Agenda Item:    4.3

<a id="P003"></a>

Document for:    Agreement

<a id="P006"></a>

Introduction

<a id="P007"></a>

The present document proposes an update of the performance requirements for the ULBC based on S4-261566. The proposals contain updates regarding frame error rate and tandeming:

<a id="P009"></a>

Frame error rate

<a id="P010"></a>

In S4-261566, all FER rate, i.e. 1%, 2%, 6% and 10% were included. It is proposed to not to consider the 10% FER as the 6% FER already represents some kind of worst case scenario for the service.

<a id="P012"></a>

Tandeming

<a id="P013"></a>

The following table lists the current proposals for the tandeming conditions as provided in S4-261771.

<a id="T014"></a>

<a id="T014-R01"></a>
**T014-R01**

- <a id="T014-R01-C01"></a>列 1: Category
- <a id="T014-R01-C02"></a>列 2: Bitrate (kbit/s)
- <a id="T014-R01-C03"></a>列 3: Tandeming Condition
- <a id="T014-R01-C04"></a>列 4: FER<br>Jitter
- <a id="T014-R01-C05"></a>列 5: DTX
- <a id="T014-R01-C06"></a>列 6: Requirements
- <a id="T014-R01-C07"></a>列 7: Objectives
- <a id="T014-R01-C08"></a>列 8: Notes

<a id="T014-R02"></a>
**T014-R02**

- <a id="T014-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-26 dBov), Noisy Speech  (-26dBov)<br>Noise types and SNR to be detailed in test plan
- <a id="T014-R02-C02"></a>列 2: 1.0
- <a id="T014-R02-C03"></a>列 3: Tandeming between ULBC and EVS-SWB 13.2 (both tandems, with Linear 16 PCM  between codecs)<br>Tandeming between ULBC and AMR-WB 12.65 (both tandems, with Linear 16 PCM  between codecs)
- <a id="T014-R02-C04"></a>列 4（纵向合并:restart）: 0% FER
- <a id="T014-R02-C05"></a>列 5（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T014-R02-C06"></a>列 6: NWT AMR-WB@12.65  self-tandeming
- <a id="T014-R02-C07"></a>列 7: NWT AMR-WB@12.65  self-tandeming
- <a id="T014-R02-C08"></a>列 8（纵向合并:restart）: To be tested in  characterization.<br>Synchronization of tandems to be defined in processing plan

<a id="T014-R03"></a>
**T014-R03**

- <a id="T014-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T014-R03-C02"></a>列 2: 1.4
- <a id="T014-R03-C03"></a>列 3: Tandeming between ULBC and EVS-SWB 13.2 (both tandems, with Linear 16 PCM  between codecs)<br>Tandeming between ULBC and AMR-WB 12.65 (both tandems, with Linear 16 PCM  between codecs)
- <a id="T014-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T014-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T014-R03-C06"></a>列 6: NWT AMR-WB@12.65  self-tandeming
- <a id="T014-R03-C07"></a>列 7: NWT EVS-SWB@13.2  self-tandeming
- <a id="T014-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="P016"></a>

Observed issues:

<a id="P017"></a>

There is no quality differentiation between 1.0 and 1.4 kbps. If the requirement for the intrinsic performance depending on the bitrate differ, the tandeming requirement should reflect this as well.

<a id="P018"></a>

There is currently no requirement ensuring that SWB tandeming works at all. For EVS-SWB tandeming, only an objective is proposed.

<a id="P019"></a>

Proposed general rule:

<a id="P020"></a>

Instead of setting up individual performance requirements which may be disentangled from the intrinsic ULBC performance, it is proposed to re-use the WB or SWB performance requirement for the tandeming condition. As an example, when looking for the tandeming requirement for ULBC 1.4 kbps in tandeming with AMR-WB 12.65 kbps, the requirement is derived by the ULBC performance requirement for WB at 1.4 kbps (currently proposed AMR-WB @ 12.65, AMR-WB @15.85, EVS-WB 13.2 kbps) in tandem operation with AMR-WB 12.65 kbps.

<a id="P021"></a>

This general concept can be extended to all kind of tandeming codec including also EVS-SWB. The following table implements this proposal for transfer into ULBC-3.

<a id="T023"></a>

<a id="T023-R01"></a>
**T023-R01**

- <a id="T023-R01-C01"></a>列 1: Category
- <a id="T023-R01-C02"></a>列 2: Bitrate (kbit/s)
- <a id="T023-R01-C03"></a>列 3: Tandeming Codec<sup>1</sup>
- <a id="T023-R01-C04"></a>列 4: FER<br>Jitter
- <a id="T023-R01-C05"></a>列 5: DTX
- <a id="T023-R01-C06"></a>列 6: Requirements
- <a id="T023-R01-C07"></a>列 7: Objectives
- <a id="T023-R01-C08"></a>列 8: Notes

<a id="T023-R02"></a>
**T023-R02**

- <a id="T023-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-26 dBov), Noisy Speech  (-26dBov)<br>Noise types and SNR to be detailed in test plan
- <a id="T023-R02-C02"></a>列 2（纵向合并:restart）: 1.0
- <a id="T023-R02-C03"></a>列 3: AMR-WB 12.65
- <a id="T023-R02-C04"></a>列 4（纵向合并:restart）: 0% FER
- <a id="T023-R02-C05"></a>列 5（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T023-R02-C06"></a>列 6: NWT AMR-WB@12.65  tandeming with  ULBC WB requirement at 1.0 kbps
- <a id="T023-R02-C07"></a>列 7: 
- <a id="T023-R02-C08"></a>列 8（纵向合并:restart）: To be tested in  characterization.<br>Synchronization of tandems to be defined in processing plan

<a id="T023-R03"></a>
**T023-R03**

- <a id="T023-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T023-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T023-R03-C03"></a>列 3: EVS-SWB 13.2
- <a id="T023-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T023-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T023-R03-C06"></a>列 6: NWT EVS-SWB@13.2  tandeming with ULBC SWB requirement at 1.0 kbps
- <a id="T023-R03-C07"></a>列 7: 
- <a id="T023-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="T023-R04"></a>
**T023-R04**

- <a id="T023-R04-C01"></a>列 1（纵向合并:continue）: 
- <a id="T023-R04-C02"></a>列 2（纵向合并:restart）: 1.4
- <a id="T023-R04-C03"></a>列 3: AMR-WB 12.65
- <a id="T023-R04-C04"></a>列 4（纵向合并:continue）: 
- <a id="T023-R04-C05"></a>列 5（纵向合并:continue）: 
- <a id="T023-R04-C06"></a>列 6: NWT AMR-WB@12.65  tandeming with ULBC WB requirement at 1.4 kbps
- <a id="T023-R04-C07"></a>列 7: 
- <a id="T023-R04-C08"></a>列 8（纵向合并:continue）: 

<a id="T023-R05"></a>
**T023-R05**

- <a id="T023-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T023-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T023-R05-C03"></a>列 3: EVS-SWB 13.2
- <a id="T023-R05-C04"></a>列 4（纵向合并:continue）: 
- <a id="T023-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T023-R05-C06"></a>列 6: NWT EVS-SWB@13.2 tandeming with ULBC SWB requirement at 1.4 kbps
- <a id="T023-R05-C07"></a>列 7: 
- <a id="T023-R05-C08"></a>列 8（纵向合并:continue）: 

<a id="P024"></a>

<sup>1</sup><sup> </sup>Tandeming between ULBC and Tandeming Codec (both tandems, with Linear 16 PCM  between codecs)

<a id="P027"></a>

Proposal

<a id="P028"></a>

It is proposed to start the discussion on performance requirement and to seek for agreement on the key proposals.

**原文页眉：** 3GPP TSG-SA WG4 Audio SWG Ad-hoc on ULBC-MED                    S4aA260120<br>    Shanghai, China, 28 – 30 September 2026
