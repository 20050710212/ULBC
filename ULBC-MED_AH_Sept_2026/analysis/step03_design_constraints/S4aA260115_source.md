# S4aA260115 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260115[ULBC-MED] Complexity and memory constraints for ULBC.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG (AH) Meeting    S4aA260115

<a id="P001"></a>

Shanghai,China, 28-30 September 2026

<a id="P003"></a>

Source:    Huawei Technologies Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Complexity and memory design constraints for ULBC

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Discussion and Agreement

<a id="P008"></a>

## 1 Introduction

<a id="P009"></a>

In SA4#137-e, the computational complexity and memory constraints of ULBC-4 v0.2.0 remain entirely undetermined, and no agreement has been reached on the metrics or numerical limits. This document provides further evidence to justify the proposed complexity.

<a id="P010"></a>

## 2 Discussion

<a id="P011"></a>

According to TR 26.940 [1], ULBC should cover a wide range of terminals such as smartphones, wearables and IoT devices. For key-parameter design constraints of the ULBC codec, complexity and memory should fit hardware limits to support real-time voice calls in case it may exclude many resource-constrained devices. High complexity and large storage will directly increase power consumption, causes device overheating and shorter standby time and poor user experience.it also increase costs for vendors, since large memory requirements drive up hardware cost for chips and storage, which will affect the real‑world deployment of the codec. For the above‑mentioned reasons and make ULBC standard commercially successful we suggest that complexity and memory footprint shall be minimized, while satisfying call quality and ensuring long call duration.

<a id="P013"></a>

## 2.1 Appropriate metrics for Codec qualification and selection

<a id="P014"></a>

Different hardware platforms show inconsistent optimization performance on various operators. Hardware-dependent metrics are not suitable for Codec qualification and selection, as it needs to cover many different devices which include different chipset type, we recommend using MACS or FLOPS as the complexity metric both of them are theoretical metric derived from mathematical multiplication and hardware-agnostic.

<a id="P016"></a>

## 2.2 Auxiliary metric: number of model parameters

<a id="P017"></a>

TR 26.940 [1] notes that large models not only require large storage but also increase power consumption significantly,

<a id="P018"></a>

“Larger codec models, although potentially more capable, pose significant challenges:

<a id="P020"></a>

-    Memory Access and Usage: Increased memory footprint requires more frequent access to DRAM, which can lead to higher power consumption.

<a id="P021"></a>

-    Power Overhead from DRAM: Not negligible, as larger models may necessitate additional power to maintain data flow between the processor and memory, impacting overall device performance and usability.”

<a id="P023"></a>

Proposal [3] states that "With the power efficient CPU cores (efficiency cores), at max a model of 3 million parameters can run within real time constraints." Based on this, we believe that 6M parameters are sufficient to cover multiple modes of the ULBC codec, it achieves a good balance between storage and power consumption.

<a id="P024"></a>

Two-byte quantization provides sufficient dynamic range for speech signals, achieving a good trade-off between quantization distortion and memory consumption in audio codec implementations, ROM should less than12 Mbyte. RAM As RAM footprint depends on multiple implementation factors, specific values are FFS.

<a id="P026"></a>

## 2.3 Complexity design constraints [4][5][6]

<a id="T027"></a>

<a id="T027-R01"></a>
**T027-R01**

- <a id="T027-R01-C01"></a>列 1: Chip Model
- <a id="T027-R01-C02"></a>列 2: CPU Architecture
- <a id="T027-R01-C03"></a>列 3: Typical Frequency
- <a id="T027-R01-C04"></a>列 4: MAC per cycle (INT16)
- <a id="T027-R01-C05"></a>列 5: Core Count
- <a id="T027-R01-C06"></a>列 6: Peak MMACS
- <a id="T027-R01-C07"></a>列 7: Available MMACS (Speech Codec)
- <a id="T027-R01-C08"></a>列 8: Typical Products

<a id="T027-R02"></a>
**T027-R02**

- <a id="T027-R02-C01"></a>列 1: BES2700BP
- <a id="T027-R02-C02"></a>列 2: Singlecore CortexM55 + Singlecore STARMC1
- <a id="T027-R02-C03"></a>列 3: 200 MHz
- <a id="T027-R02-C04"></a>列 4: M55:4 / STARMC1:1
- <a id="T027-R02-C05"></a>列 5: 2
- <a id="T027-R02-C06"></a>列 6: 1000
- <a id="T027-R02-C07"></a>列 7: 300~400
- <a id="T027-R02-C08"></a>列 8: Smart watch / smart glasses

<a id="T027-R03"></a>
**T027-R03**

- <a id="T027-R03-C01"></a>列 1: 8910DM
- <a id="T027-R03-C02"></a>列 2: Dualcore CortexA5
- <a id="T027-R03-C03"></a>列 3: 500 MHz
- <a id="T027-R03-C04"></a>列 4: 1
- <a id="T027-R03-C05"></a>列 5: 2
- <a id="T027-R03-C06"></a>列 6: 1000
- <a id="T027-R03-C07"></a>列 7: 300~400
- <a id="T027-R03-C08"></a>列 8: Cat.1 voiceintercom IoT device

<a id="T027-R04"></a>
**T027-R04**

- <a id="T027-R04-C01"></a>列 1: BES2800HP
- <a id="T027-R04-C02"></a>列 2: Dualcore CortexM55 + Dualcore STARMC1
- <a id="T027-R04-C03"></a>列 3: 200 MHz
- <a id="T027-R04-C04"></a>列 4: M55:4 / STARMC1:1
- <a id="T027-R04-C05"></a>列 5: 4
- <a id="T027-R04-C06"></a>列 6: 2000
- <a id="T027-R04-C07"></a>列 7: 600~800
- <a id="T027-R04-C08"></a>列 8: Flagship smart watch / glasses

<a id="P028"></a>

Formula of calculate MMACS:

<a id="P029"></a>

Peak MMACS = Frequency (MHz) * 1 MAC/cycle * Number of CPU cores

<a id="P030"></a>

For cores with SIMD vector acceleration (NEON / Helium): use IP‑specified INT16 MAC‑per‑cycle value

<a id="P031"></a>

For cores without vector unit: use scalar 1 MAC/cycle

<a id="P032"></a>

Available MMACS: practical compute budget for speech codec after OS, protocol stack and background tasks. Wearable/IoT: 30%‑40% of peak

<a id="P033"></a>

Bestechnic chips which include BES serious are mainstream SoC solutions for mid-to-high-end wearable devices, Huawei wearable devices already support satellite communication features.

<a id="P034"></a>

From the table above, it can be seen that even with current flagship wearables products the available computational complexity would be less than 800 MMACS, this echoes our previous proposal that Complexity should less than 600MMACS.

<a id="P035"></a>

If the codec complexity becomes too high, such wearables cannot maintain satellite communication capability, which is not acceptable. This conflicts with the ULBC project objective of supporting a broad range of end products [1] and will have an influence on commercial success of the ULBC standard.

<a id="P037"></a>

## 3 Proposal

<a id="P038"></a>

Based on the discussion above, it is proposed to document the following contents into the ULBC-4 design constraints in an appropriate form:

<a id="P039"></a>

Proposal 1:

<a id="P040"></a>

The total complexity constraint is less than 600 MMACS(or 1200MFLOPs), and the total number of model parameters is less than 6M which needs to cover all modes of the ULBC.

<a id="P041"></a>

Proposal 2:

<a id="P042"></a>

ROM should less than12 Mbytes (2byte quantization for each parameter), RAM TBD

<a id="T044"></a>

<a id="T044-R01"></a>
**T044-R01**

- <a id="T044-R01-C01"></a>列 1: Computational complexity and memory
- <a id="T044-R01-C02"></a>列 2: The computational complexity and memory footprint shall ensure implementability on standard 3GPP UE platforms. <br> complexity constraint:<br><br>- The total complexity constraint < 600MMACS(or 1200MFLOPS)<br>- the total number of model parameters < 6M<br><br>memory footprint constraint:<br>- RAM: TBD<br>- RAM: <12Mbytes
- <a id="T044-R01-C03"></a>列 3: The total complexity constraint is less than 600 MMACS(or 1200MFLOPs), and the total number of model parameters is less than 6M which needs to cover all modes of the ULBC.

<a id="P047"></a>

References

<a id="P048"></a>

[1] TR 26.940, “Study on Ultra Low Bit rate Speech Codecs”

<a id="P049"></a>

[2] SC29-WG1_wg1n100250-096-REQ-Report on the JPEG AI Call for Proposals Results

<a id="P050"></a>

[3] S4-261024, "ULBC design constraints"

<a id="P051"></a>

[4] BES2700BP, https://www.bestechnic.com/article/52/11.html

<a id="P052"></a>

[5] 8910DM ,https://www.unisoc.com/cn/product/WA-IoT/8910DM

<a id="P053"></a>

[6] BES2800HP, https://www.bestechnic.com/article/72/56.html
