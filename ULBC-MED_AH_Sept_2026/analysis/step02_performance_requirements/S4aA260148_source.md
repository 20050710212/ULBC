# S4aA260148 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260148-Use of Quality Stairs.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG SA WG4 Audio SWG AH    S4aA260148

<a id="P001"></a>

Shanghai, China, September 28-30, 2026

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    Use of Quality Stairs as an Objective in Performance Requirements

<a id="P005"></a>

Agenda item:    4.3

<a id="P006"></a>

Document for:    AGREEMENT

<a id="P009"></a>

Introduction

<a id="P010"></a>

This contribution proposes to add, as an objective, the use of quality stairs anchored on AMR-WB and EVS as part of the performance evaluation methodology for the ULBC-MED selection. The complementary to the minimum performance requirement aims at improving the discriminative power of the subjective test campaign used to select the best-performing candidate.

<a id="P012"></a>

## 2. Motivation

<a id="P013"></a>

A minimum requirement establishes a pass/fail threshold. Once multiple candidates clear this threshold, MOS scores among them tend to cluster in the upper region of the quality scale, where the P.800 DCR MOS scale is known to be compressive. This makes it statistically difficult to distinguish "good" candidates from the "best" candidate using minimum-requirement compliance alone.

<a id="P014"></a>

Quality stairs, i.e., a set of reference/anchor conditions spanning a range of known quality levels, generated using previously standardized codecs such as AMR-WB, were used during  the qualification, selection and characterization  phases of EVS, and provide the following benefits:

<a id="P016"></a>

Improved resolution near the top of the scale: Anchors placed close to and above the minimum requirement's target quality stretch the effective resolution of the MOS scale exactly where candidate differentiation is needed.

<a id="P017"></a>

Cross-condition and cross-lab normalization: With 20 candidates evaluated across multiple test conditions run in different sessions/labs/panels, anchors allow raw MOS scores to be normalized into anchor-relative quality metrics. This is essential for constructing a single Figure of Merit (FoM) that aggregates performance fairly across heterogeneous conditions.

<a id="P018"></a>

Statistical robustness: Anchor-relative scoring helps distinguish genuine quality differences between candidates from listening-panel/session variability.

<a id="P019"></a>

Avoiding a "race to the minimum": An objective based on stairs incentivizes proponents to demonstrate superiority beyond the pass/fail bar.

<a id="P021"></a>

With two bitrate points but many test conditions and many candidates, the primary discriminative challenge lies in comparing many candidates fairly across many conditions. Anchors from AMR-WB and EVS at comparable or bracketing bitrates provide the fixed reference points needed to normalize scores condition-wise, enabling meaningful aggregation into a single FoM across all conditions.

<a id="P022"></a>

Apart of the aforementioned benefits the overall performance of the ULBC codec demonstrating quality relative to these established anchors supports adoption of the codec.

<a id="P025"></a>

## 3. Proposal

<a id="P026"></a>

It is proposed to add, as an objective in the Performance Requirements document, the use of quality stairs built from AMR-WB and EVS reference conditions, to be used in conjunction with the P.800 DCR tests during the selection phase.

<a id="P027"></a>

Specifically, to add in the objectives in the performance requirements [1] quality stairs as follows:

<a id="T033"></a>

<a id="T033-R01"></a>
**T033-R01**

- <a id="T033-R01-C01"></a>列 1: Category
- <a id="T033-R01-C02"></a>列 2: BW
- <a id="T033-R01-C03"></a>列 3: Bitrate (kbit/s)
- <a id="T033-R01-C04"></a>列 4: Bundling time
- <a id="T033-R01-C05"></a>列 5: FER
- <a id="T033-R01-C06"></a>列 6: DTX
- <a id="T033-R01-C07"></a>列 7: Requirements
- <a id="T033-R01-C08"></a>列 8: Objectives <br>(Quality stairs)

<a id="T033-R02"></a>
**T033-R02**

- <a id="T033-R02-C01"></a>列 1（纵向合并:restart）: Clean speech<br>-26,-16,-36 dBov
- <a id="T033-R02-C02"></a>列 2（纵向合并:restart）: WB
- <a id="T033-R02-C03"></a>列 3: 1.0
- <a id="T033-R02-C04"></a>列 4: [80ms/160ms]
- <a id="T033-R02-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T033-R02-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T033-R02-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T033-R02-C08"></a>列 8（纵向合并:restart）: NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T033-R03"></a>
**T033-R03**

- <a id="T033-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T033-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T033-R03-C03"></a>列 3: 1.4
- <a id="T033-R03-C04"></a>列 4: 80ms
- <a id="T033-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T033-R03-C06"></a>列 6（纵向合并:continue）: 
- <a id="T033-R03-C07"></a>列 7: NWT AMR-WB @ 12.65
- <a id="T033-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="T033-R04"></a>
**T033-R04**

- <a id="T033-R04-C01"></a>列 1（纵向合并:restart）: Clean speech<br> -26 dBov
- <a id="T033-R04-C02"></a>列 2（纵向合并:restart）: WB
- <a id="T033-R04-C03"></a>列 3: 1.0
- <a id="T033-R04-C04"></a>列 4: [80ms/160ms]
- <a id="T033-R04-C05"></a>列 5（纵向合并:restart）: x%= [1%, 2% 6%, 10%]
- <a id="T033-R04-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T033-R04-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T033-R04-C08"></a>列 8（纵向合并:restart）: NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T033-R05"></a>
**T033-R05**

- <a id="T033-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T033-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T033-R05-C03"></a>列 3: 1.4
- <a id="T033-R05-C04"></a>列 4: 80ms
- <a id="T033-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T033-R05-C06"></a>列 6（纵向合并:continue）: 
- <a id="T033-R05-C07"></a>列 7: NWT AMR-WB @ 12.65
- <a id="T033-R05-C08"></a>列 8（纵向合并:continue）: 

<a id="T033-R06"></a>
**T033-R06**

- <a id="T033-R06-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov<br><br>.
- <a id="T033-R06-C02"></a>列 2（纵向合并:restart）: WB
- <a id="T033-R06-C03"></a>列 3: 1.0
- <a id="T033-R06-C04"></a>列 4: [80ms/160ms]
- <a id="T033-R06-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T033-R06-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T033-R06-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T033-R06-C08"></a>列 8（纵向合并:restart）: NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T033-R07"></a>
**T033-R07**

- <a id="T033-R07-C01"></a>列 1（纵向合并:continue）: 
- <a id="T033-R07-C02"></a>列 2（纵向合并:continue）: 
- <a id="T033-R07-C03"></a>列 3: 1.4
- <a id="T033-R07-C04"></a>列 4: 80ms
- <a id="T033-R07-C05"></a>列 5（纵向合并:continue）: 
- <a id="T033-R07-C06"></a>列 6（纵向合并:continue）: 
- <a id="T033-R07-C07"></a>列 7: NWT AMR-WB @ 12.65
- <a id="T033-R07-C08"></a>列 8（纵向合并:continue）: 

<a id="T033-R08"></a>
**T033-R08**

- <a id="T033-R08-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov
- <a id="T033-R08-C02"></a>列 2（纵向合并:restart）: WB
- <a id="T033-R08-C03"></a>列 3: 1.0
- <a id="T033-R08-C04"></a>列 4: [80ms/160ms]
- <a id="T033-R08-C05"></a>列 5（纵向合并:restart）: x%=[1%, 2% 6%, 10%]
- <a id="T033-R08-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T033-R08-C07"></a>列 7: NWT AMR-WB @ 8.85
- <a id="T033-R08-C08"></a>列 8（纵向合并:restart）: NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T033-R09"></a>
**T033-R09**

- <a id="T033-R09-C01"></a>列 1（纵向合并:continue）: 
- <a id="T033-R09-C02"></a>列 2（纵向合并:continue）: 
- <a id="T033-R09-C03"></a>列 3: 1.4
- <a id="T033-R09-C04"></a>列 4: 80ms
- <a id="T033-R09-C05"></a>列 5（纵向合并:continue）: 
- <a id="T033-R09-C06"></a>列 6（纵向合并:continue）: 
- <a id="T033-R09-C07"></a>列 7: NWT AMR-WB @ 12.65
- <a id="T033-R09-C08"></a>列 8（纵向合并:continue）: 

<a id="P035"></a>

Objective not relevant for 1.4 kbps

<a id="P044"></a>

## 5. Conclusion

<a id="P045"></a>

This contribution proposes to add the use of quality stairs, anchored on AMR-WB and EVS as an objective in the performance requirements for ULBC-MED. This is expected to improve the discriminative power of the P.800 DCR-based selection test campaign and to support the construction of a robust Figure of Merit for candidate ranking, without altering the existing minimum requirement.

<a id="P046"></a>

It is proposed that the Audio SWG agrees on the principle described above and include the changes in ULBC-3[1].

<a id="P049"></a>

## 6. References

<a id="P051"></a>

S4-261771 - [ULBC-MED] ULBC Performance requirements (ULBC-3),v0.1.0
