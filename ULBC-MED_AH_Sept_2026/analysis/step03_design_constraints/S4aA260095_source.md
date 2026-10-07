# S4aA260095 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260095 [ULBC-MED] Proposal on RTF-based Complexity Evaluation for ULBC.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。2026-10-08 复核时从 OMML 补回 P022 公式及 P023 变量，使用可读线性记法。

<a id="P000"></a>

3GPP TSG-SA4 Adhoc Audio SWG                                                               S4aA260095

<a id="P001"></a>

Shanghai, 28-30 September 2026

<a id="P003"></a>

Source:    Spreadtrum, China telecom

<a id="P004"></a>

Title:    [ULBC-MED] Proposal on RTF-based Complexity Evaluation for ULBC

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Discussion & Agreement

<a id="P008"></a>

## 1 Introduction

<a id="P009"></a>

The ULBC-MED Work Item was approved at TSG SA#112 in SP-260696 [1]. Computational complexity is one of the design constraints addressed under ULBC-4. TR 26.940 [2] identifies operation count, model size and real-time factor (RTF) as relevant complexity metrics for AI-based speech codecs.

<a id="P010"></a>

This contribution proposes using measured RTF on a common reference platform to assess the practical execution complexity of ULBC candidates. GMACs/s remains useful as a measure of computational workload, but operation counts alone do not show whether a complete codec implementation can meet its real-time processing budget.

<a id="P011"></a>

The objective of this contribution is to seek agreement on the use of RTF and on the scope of its measurement, covering complete encoder and decoder processing, including codec-internal packet loss concealment (PLC) and other necessary codec operations. Candidate reference platforms and basic evaluation principles are outlined below. Numerical acceptance thresholds and the detailed test procedure remain for further study (FFS).

<a id="P012"></a>

## 2 Discussion

<a id="P013"></a>

## 2.1 Limitations of operation counts alone

<a id="P014"></a>

TR 26.940 Clause 7.6.4.2 [2] reports a correlation between GMACs/s and RTF for the evaluated DAC configurations. This supports using GMACs/s to describe computational complexity. However, Clause 7.6.6.4 explicitly limits the RTF analysis to the DAC architecture and leaves the impact of different ML architectures FFS. The observed relationship therefore does not establish a universal mapping from GMACs/s to execution time for all ULBC candidates.

<a id="P015"></a>

Actual execution time also depends on data dependencies, memory access patterns, operator mapping and kernel implementation. For example, recurrent computation may depend on outputs from preceding time steps, whereas other computations may expose greater parallelism to optimized CPU kernels. The resulting execution efficiency depends on the actual model and implementation; the architecture type alone does not determine it. Therefore, candidates with similar operation counts may still have different execution times on the same CPU.

<a id="P016"></a>

The same principle applies to accelerator deployment: operator support and the mapping of a model to the hardware can affect execution efficiency. A full accelerator comparison is outside the scope of this contribution. The proposed CPU baseline provides a common assessment point while leaving product implementations free to use DSPs, NPUs or other accelerators.

<a id="P017"></a>

TR 26.940 Clause 6.2.2.6 [2] already identifies RTF as a possible metric for ULBC design constraints, while noting the need for accessible test platforms and avoidance of bias from platform-specific optimizations. A common RTF evaluation would address this open issue and complement the theoretical workload information provided by GMACs/s.

<a id="P018"></a>

Observation 1: GMACs/s describes theoretical computational complexity, but does not fully represent the architecture-dependent execution efficiency of a  codec implementation. Candidate codecs with similar GMACs/s may have different measured RTF on the same reference platform.

<a id="P019"></a>

## 2.2 RTF for the complete codec processing path

<a id="P020"></a>

RTF is defined here as the CPU execution time required for complete codec processing divided by the duration of the corresponding audio. CPU execution time includes neural-network inference, all required non-neural codec operations and runtime overhead attributable to codec execution. Time for which codec compute threads are descheduled or blocked due to unrelated system activity is excluded.

<a id="P021"></a>

For one encoder frame and one decoder frame corresponding to the same audio duration, the combined RTF is defined as:

<a id="P022"></a>

`RTF_i = (T_enc,i + T_dec,i) / T_frame`

<a id="P023"></a>

Here, T_enc,i and T_dec,i denote the CPU execution time for complete encoder and decoder processing during evaluation interval i. T_dec,i includes codec-internal PLC and recovery processing whenever these paths are invoked; their time is not added a second time. The denominator is one frame duration, representing the combined budget for one outgoing encoder stream and one incoming decoder stream.

<a id="P024"></a>

The measurement scope should extend beyond neural-network inference alone. Measuring only model inference time would omit processing required to generate a usable bitstream or reconstructed speech and could therefore give an incomplete view of deployment complexity. Table 1 defines the proposed measurement scope.

<a id="P025"></a>

Table 1  Scope of the combined RTF measurement

<a id="T026"></a>

<a id="T026-R01"></a>
**T026-R01**

- <a id="T026-R01-C01"></a>列 1: Component
- <a id="T026-R01-C02"></a>列 2: Processing boundary

<a id="T026-R02"></a>
**T026-R02**

- <a id="T026-R02-C01"></a>列 1: Encoder
- <a id="T026-R02-C02"></a>列 2: All processing required to convert the input audio frame into the codec bitstream, including codec-internal preprocessing, feature extraction, neural inference, quantization and entropy coding, where applicable.

<a id="T026-R03"></a>
**T026-R03**

- <a id="T026-R03-C01"></a>列 1: Decoder
- <a id="T026-R03-C02"></a>列 2: All processing required to produce the output audio frame, including bitstream parsing, entropy decoding, neural inference, synthesis and codec-internal postprocessing, where applicable.

<a id="T026-R04"></a>
**T026-R04**

- <a id="T026-R04-C01"></a>列 1: Loss and recovery
- <a id="T026-R04-C02"></a>列 2: Codec-internal PLC, including AI-based PLC, and processing required when decoding resumes after loss. These are included in the applicable decoder path, not treated as an additional cost on every normal frame.

<a id="T026-R05"></a>
**T026-R05**

- <a id="T026-R05-C01"></a>列 1: Outside the scope
- <a id="T026-R05-C02"></a>列 2: Audio capture and playback waiting, network transport, frame pacing, and external voice functions such as AEC or noise suppression that are not part of the candidate codec.

<a id="P027"></a>

This complete-path definition provides a common accounting boundary for candidates that divide their processing differently between neural models and conventional signal-processing code. Encoder and decoder times may also be reported separately to explain the combined result.

<a id="P028"></a>

An individual combined RTF below 1 means that, under the dedicated single-core test condition, the complete codec consumes less than one frame period of CPU execution time. It is a necessary compute-capacity condition, but does not by itself guarantee real-time operation of a complete voice system sharing CPU resources. RTF characterizes the implementation on the agreed platform; it is not a platform-independent property of the model or a measure of algorithmic delay.

<a id="P029"></a>

RTF close to 1 leaves little CPU-execution-time margin for other system processing when the same core is shared. The final numerical threshold remains FFS.

<a id="P030"></a>

## 2.3 Common reference platform

<a id="P031"></a>

Comparable RTF measurements require an agreed physical platform and software configuration. Specifying only a CPU architecture is insufficient because operating frequency, memory system and software settings can affect the result. The selected device and operating conditions should therefore be documented and reproducible across laboratories.

<a id="P032"></a>

A Cortex-A76 or Cortex-A78 performance core may be considered as a candidate CPU class, consistent with the performance-core evaluations discussed in TR 26.940 Clause 7.6 [2]. Table 2 illustrates that these mature performance cores are available in entry-level or mainstream mobile platforms, rather than only in current flagship products. Raspberry Pi 5, which uses Cortex-A76 cores [3], may be considered as an accessible common reference device. Representative commercial smartphones may provide supplementary validation. The final platform and operating point are FFS.

<a id="P033"></a>

Table 2  Examples of accessible Cortex-A76 and Cortex-A78 platforms

<a id="T034"></a>

<a id="T034-R01"></a>
**T034-R01**

- <a id="T034-R01-C01"></a>列 1: Platform
- <a id="T034-R01-C02"></a>列 2: Performance core
- <a id="T034-R01-C03"></a>列 3: Public release
- <a id="T034-R01-C04"></a>列 4: Availability example

<a id="T034-R02"></a>
**T034-R02**

- <a id="T034-R02-C01"></a>列 1: Raspberry Pi 5
- <a id="T034-R02-C02"></a>列 2: Cortex-A76, 4 × 2.4 GHz
- <a id="T034-R02-C03"></a>列 3: 2023
- <a id="T034-R02-C04"></a>列 4: Publicly available reference device

<a id="T034-R03"></a>
**T034-R03**

- <a id="T034-R03-C01"></a>列 1: Dimensity 6100+
- <a id="T034-R03-C02"></a>列 2: Cortex-A76, 2 × 2.2 GHz
- <a id="T034-R03-C03"></a>列 3: 2023
- <a id="T034-R03-C04"></a>列 4: Entry and mainstream Android SoCs

<a id="T034-R04"></a>
**T034-R04**

- <a id="T034-R04-C01"></a>列 1: Snapdragon 4s Gen 2
- <a id="T034-R04-C02"></a>列 2: Cortex-A78, 2 × 2.0 GHz
- <a id="T034-R04-C03"></a>列 3: 2024
- <a id="T034-R04-C04"></a>列 4: Entry-level 5G Android SoCs

<a id="T034-R05"></a>
**T034-R05**

- <a id="T034-R05-C01"></a>列 1: UNISOC T8300
- <a id="T034-R05-C02"></a>列 2: Cortex-A78, 2 × 2.2 GHz
- <a id="T034-R05-C03"></a>列 3: 2024
- <a id="T034-R05-C04"></a>列 4: Mainstream Android SoCs

<a id="P035"></a>

The common measurement should use CPU-only execution restricted to one selected performance core. All codec and runtime compute threads should be confined to that core, and the thread configuration should be reported. This bounds the CPU resources available to each candidate without prescribing its internal software thread structure. RTF shall be derived from the accumulated CPU execution time of all codec and runtime compute threads; off-CPU delay caused by system scheduling or unrelated activity shall not be included.

<a id="P036"></a>

A publicly available inference runtime, such as ONNX Runtime Mobile [4] or LiteRT [5], may provide the software baseline. Table 3 summarizes the basic CPU inference paths and public mobile access offered by these runtimes. The runtime version, CPU backend and execution settings should be agreed and fixed, with model numerical precision and relevant implementation settings reported.

<a id="P037"></a>

Table 3  Examples of publicly available mobile inference runtimes

<a id="T038"></a>

<a id="T038-R01"></a>
**T038-R01**

- <a id="T038-R01-C01"></a>列 1: Runtime
- <a id="T038-R01-C02"></a>列 2: Model format
- <a id="T038-R01-C03"></a>列 3: CPU inference path
- <a id="T038-R01-C04"></a>列 4: Public access

<a id="T038-R02"></a>
**T038-R02**

- <a id="T038-R02-C01"></a>列 1: ONNX Runtime Mobile
- <a id="T038-R02-C02"></a>列 2: ONNX
- <a id="T038-R02-C03"></a>列 3: CPU Execution Provider; XNNPACK Execution Provider for optimized CPU inference
- <a id="T038-R02-C04"></a>列 4: Public Android and iOS packages; cross-platform runtime

<a id="T038-R03"></a>
**T038-R03**

- <a id="T038-R03-C01"></a>列 1: LiteRT
- <a id="T038-R03-C02"></a>列 2: LiteRT / TFLite
- <a id="T038-R03-C03"></a>列 3: CPU Interpreter API; CPU option in the CompiledModel API
- <a id="T038-R03-C04"></a>列 4: Public Android runtime and APIs; CPU inference path available

<a id="P039"></a>

The treatment of custom operators and candidate-specific optimizations is FFS; the adopted rules should remain reproducible and should not omit required codec processing. A common software stack supports consistent comparison, but does not ensure that every architecture benefits equally from optimization. Results should therefore be interpreted as performance on the agreed baseline. The CPU-only baseline does not restrict product implementations from using accelerators or other platform-specific optimizations.

<a id="P040"></a>

Observation 2: A common CPU baseline based on an accessible Cortex-A76/A78 performance core, together with a fixed publicly available inference runtime and CPU configuration, can expose all candidates to the same available software optimizations and support reproducible RTF measurements. The result characterizes deployment on that baseline.

<a id="P041"></a>

## 2.4 Evaluation and reporting principles

<a id="P042"></a>

The evaluation should measure the CPU execution time required for complete encoder and decoder processing sequentially on the selected core and calculate a combined RTF for each audio-frame interval. Results for normal operation and agreed packet loss and recovery conditions should be reported separately so that codec-internal PLC costs remain visible.

<a id="P043"></a>

P50 and P99 combined RTF values are suggested to characterize typical and upper-tail codec execution demand, respectively. Because CPU-execution-time accounting excludes OS scheduling delay, P99 should not be interpreted as a system-level tail-latency metric. These statistics should be calculated directly from per-frame combined RTF measurements, rather than by adding independently calculated encoder and decoder percentiles. Their final use in Qualification remains FFS.

<a id="P044"></a>

GMACs/s, parameter count, model size and peak runtime memory should be reported as complementary information. Detailed procedures, including warm-up, test duration, operating conditions and reporting format, can be coordinated with ULBC-7 and ULBC-8a. These details should follow agreement on the metric, its complete processing scope and the common reference baseline.

<a id="P045"></a>

## 3 Conclusions and proposals

<a id="P046"></a>

Operation counts describe theoretical workload, while measured RTF reflects the CPU execution time of a complete codec implementation on an agreed platform. RTF below 1 is a necessary compute-capacity condition for the dedicated single-core test condition; it does not by itself guarantee system-level real-time operation. The final Qualification threshold remains FFS.

<a id="P048"></a>

Proposal 1: Adopt measured RTF, calculated from complete-codec CPU execution time on a common reference hardware and software platform, as a principal metric for assessing the implementation-level computational complexity of ULBC candidates during Qualification. The numerical acceptance threshold remains FFS. Retain GMACs/s, parameter count, model size and peak runtime memory as complementary metrics.

<a id="P049"></a>

Proposal 2: Define the RTF measurement scope to cover complete encoder and decoder processing, including codec-internal PLC, recovery and all other necessary codec operations, whether neural or non-neural. Report combined encoder and decoder RTF, including applicable loss and recovery conditions, to provide an overall assessment of codec processing complexity.

<a id="P050"></a>

Proposal 3: Establish a reproducible CPU-only reference baseline using a single selected performance core and agreed software settings. RTF measurements should be based on accumulated CPU execution time across all codec and runtime compute threads, excluding off-CPU time due to system scheduling or unrelated system activity. Cortex-A76/A78 devices, including Raspberry Pi 5 as a candidate common reference device, may be considered. The final platform, detailed measurement and reporting procedure, and numerical acceptance thresholds remain FFS.

<a id="P051"></a>

## 4 References

<a id="P052"></a>

[1] SP-260696, New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite, June 2026.

<a id="P053"></a>

[2] 3GPP TR 26.940 V20.0.0, Study on Ultra Low Bit Rate Speech Codecs, Clauses 6.2.2.6, 7.6.4.2 and 7.6.6.4.

<a id="P054"></a>

[3] Raspberry Pi, Raspberry Pi 5 product information.<br>
https://www.raspberrypi.com/products/raspberry-pi-5/

<a id="P055"></a>

[4] ONNX Runtime, Deploy on mobile and XNNPACK Execution Provider documentation.<br>
https://onnxruntime.ai/docs/tutorials/mobile/

<a id="P056"></a>

[5] Google AI Edge, LiteRT for Android.<br>
https://developers.google.com/edge/litert/android

<a id="P057"></a>

[6] Qualcomm, Snapdragon 4s Gen 2 product announcement, September 2024.<br>
https://www.qualcomm.com/news/releases/2024/07/qualcomm-unveils-snapdragon-4s-gen-2-mobile-platform

<a id="P058"></a>

[7] MediaTek, Dimensity 6100+ product announcement, March 2023.<br>
https://www.mediatek.com/news-events/press-releases/mediatek-launches-dimensity-6100-plus

<a id="P059"></a>

[8] UNISOC, 5G SoC T8300 product news, September 2024.<br>
https://www.unisoc.com/en_us/home/News/detail/id/578.html
