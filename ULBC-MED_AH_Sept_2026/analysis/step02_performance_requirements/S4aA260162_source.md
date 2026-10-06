# S4aA260162 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260162.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG Ad-Hoc Meeting on ULBC-MED    S4aA260162

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Lenovo, Motorola Mobility

<a id="P004"></a>

Title:    [ULBC-MED] ULBC tandeming

<a id="P005"></a>

Spec:    ULBC permanent documents (ULBC-3)

<a id="P006"></a>

Agenda item:    4.3

<a id="P007"></a>

Document for:    Agreement

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

The ULBC-MED Work Item targets a deployable codec for IMS voice over NB-IoT GEO satellite access. This includes both integration in the IMS subsystem, as well as inter-working with legacy 3GPP and landline/emergency call codecs.

<a id="P012"></a>

## 2. Discussion

<a id="P013"></a>

The importance of ULBC tandem/interworking with legacy 3GPP speech codecs cannot be overstated.  Essentially 100% of GEO-based ULBC emergency calls will require interworking with legacy 3GPP codecs [1].  In addition, all TN calls connected to legacy UEs will require tandem connections since those do not support ULBC.

<a id="P014"></a>

This is in sharp contrast to EVS deployment where it was possible to negotiate through SDP a “fallback” codec as supported by both UE transport links, e.g., AMR-WB 12.65 kbps.  For GEO, however, there is no common fallback codec. Therefore, the only option is a tandem connection.

<a id="P015"></a>

This issue was recognized during the ULBC feasibility study TR 26.940 [2], which states:

<a id="P016"></a>

## 11.1.5    Interworking considerations

<a id="P017"></a>

## 11.1.5.1    Transcoding

<a id="P018"></a>

Transcoding remains a necessary interworking mechanism in scenarios where end-to-end ULBC operation cannot be ensured, e.g. when GEO NTN users communicate with terrestrial users operating legacy codecs. Transcoding is required in such cases where end-to-end ULBC operation is not possible and is expected to be an important criterion for the service quality.

<a id="P020"></a>

Based on these facts, the authors find it unacceptable to wait until the characterization phase of the ULBC standardization process to test the respective interworking audio quality. We therefore propose to include at least ULBC tandem with AMR-WB 12.65 kbps as part of the qualification phase, as well as the selection and characterization phases.

<a id="P021"></a>

Specific interworking performance requirements are FFS.

<a id="P023"></a>

## 3. Conclusion and proposal

<a id="P024"></a>

The following proposal is up to agreement:

<a id="P025"></a>

Proposal: Include at least ULBC tandeming with AMR-WB 12.65 kbps as part of the qualification phase, as well as the selection and characterization phases.

<a id="P026"></a>

The corresponding changes to the ULBC-3 – Performance Requirements PDoc are additionally proposed:

<a id="P028"></a>

* * * First Change * * * *

<a id="P029"></a>

## 4.2 ULBC Performance Requirements on Interworking

<a id="P031"></a>

Table 11: Interworking requirements.

<a id="T032"></a>

<a id="T032-R01"></a>
**T032-R01**

- <a id="T032-R01-C01"></a>列 1: Category
- <a id="T032-R01-C02"></a>列 2: FER<br>Jitter
- <a id="T032-R01-C03"></a>列 3: DTX
- <a id="T032-R01-C04"></a>列 4: Bitrate (kbit/s)
- <a id="T032-R01-C05"></a>列 5: Tandeming Condition
- <a id="T032-R01-C06"></a>列 6: Requirements
- <a id="T032-R01-C07"></a>列 7: Objectives
- <a id="T032-R01-C08"></a>列 8: Notes

<a id="T032-R02"></a>
**T032-R02**

- <a id="T032-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-26 dBov), Noisy Speech  (-26dBov)<br>Noise types and SNR to be detailed in test plan
- <a id="T032-R02-C02"></a>列 2（纵向合并:restart）: 0%<br>FER
- <a id="T032-R02-C03"></a>列 3（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T032-R02-C04"></a>列 4（纵向合并:restart）: 1.0
- <a id="T032-R02-C05"></a>列 5: [Tandeming between ULBC and EVS-SWB 13.2 kbps (both tandems, with Linear 16 PCM  between codecs)]
- <a id="T032-R02-C06"></a>列 6: 
- <a id="T032-R02-C07"></a>列 7: [NWT AMR-WB@12.65  self-tandeming]
- <a id="T032-R02-C08"></a>列 8（纵向合并:restart）: Transcoding remains a necessary interworking mechanism in scenarios where end-to-end ULBC operation cannot be ensured, e.g. when GEO NTN users communicate with terrestrial users operating legacy codecs. Transcoding is required in such cases where end-to-end ULBC operation is not possible (e.g., E911 calls) and is expected to be an important criterion for the service quality.<br><br>Transcoding is to be tested in qualification, selection, and characterization.<br><br>Synchronization of tandems is to be defined in the processing plan<br><br>The details of tandeming test sets for qualification/selection are described in the corresponding test plan.

<a id="T032-R03"></a>
**T032-R03**

- <a id="T032-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T032-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T032-R03-C03"></a>列 3（纵向合并:continue）: 
- <a id="T032-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T032-R03-C05"></a>列 5: Tandeming between ULBC and AMR-WB 12.65 kbps (both tandems, with Linear 16 PCM  between codecs)
- <a id="T032-R03-C06"></a>列 6: [NWT AMR-WB@12.65  self-tandeming]
- <a id="T032-R03-C07"></a>列 7: 
- <a id="T032-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="T032-R04"></a>
**T032-R04**

- <a id="T032-R04-C01"></a>列 1（纵向合并:continue）: 
- <a id="T032-R04-C02"></a>列 2（纵向合并:continue）: 
- <a id="T032-R04-C03"></a>列 3（纵向合并:continue）: 
- <a id="T032-R04-C04"></a>列 4（纵向合并:restart）: 1.4
- <a id="T032-R04-C05"></a>列 5: [Tandeming between ULBC and EVS-SWB 13.2 kbps (both tandems, with Linear 16 PCM  between codecs)]
- <a id="T032-R04-C06"></a>列 6: 
- <a id="T032-R04-C07"></a>列 7: [NWT EVS-SWB@13.2  self-tandeming]
- <a id="T032-R04-C08"></a>列 8（纵向合并:continue）: 

<a id="T032-R05"></a>
**T032-R05**

- <a id="T032-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T032-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T032-R05-C03"></a>列 3（纵向合并:continue）: 
- <a id="T032-R05-C04"></a>列 4（纵向合并:continue）: 
- <a id="T032-R05-C05"></a>列 5: Tandeming between ULBC and AMR-WB 12.65 kbps (both tandems, with Linear 16 PCM  between codecs)
- <a id="T032-R05-C06"></a>列 6: [NWT AMR-WB@12.65  self-tandeming]
- <a id="T032-R05-C07"></a>列 7: 
- <a id="T032-R05-C08"></a>列 8（纵向合并:continue）: 

<a id="P035"></a>

Notes:

<a id="P036"></a>

<sup>† </sup>Reference codecs with DTX on

<a id="P038"></a>

More tandeming cases (e.g., G.711) could be considered during characterization, including self-tandeming of ULBC.

<a id="P040"></a>

* * * End of Changes * * * *

<a id="P043"></a>

## 4. References

<a id="P044"></a>

[1] Tdoc S4-261615: [ULBC_MED] On ULBC tandeming, Source: Lenovo, Motorola Mobility, Status: Noted, Meeting SA4#137e, August 2026.

<a id="P045"></a>

[2] 3GPP TR 26.940: Study on supporting Ultra-Low Bitrate speech Codec (ULBC) for satellite access, V20.0.0, June 2026.
