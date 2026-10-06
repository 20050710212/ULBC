# S4aA260160 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260160.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG Ad-Hoc Meeting on ULBC-MED    S4aA260160

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Lenovo, Motorola Mobility

<a id="P004"></a>

Title:    [ULBC-MED] On utilizing RTF for ULBC complexity measurement

<a id="P005"></a>

Spec:    ULBC permanent documents (ULBC-4)

<a id="P006"></a>

Agenda item:    4.4

<a id="P007"></a>

Document for:    Agreement

<a id="P009"></a>

## 1. Introduction

<a id="P011"></a>

The ULBC-MED Work Item targets a deployable codec for IMS voice over NB-IoT GEO satellite access. The “codec computational complexity and memory footprint ensuring implementability on UE platforms”. The UE platforms in question discussed during the study have been currently deployed and upcoming mobile handsets, vehicles and wearable terminals.

<a id="P012"></a>

Given the different UE terminals for ULBC and growing heterogeneous compute offerings in modern chipsets and devices for AI-based solutions, it was so far difficult to determine a set of complexity requirements and metrics for ULBC. Various proposals list different requirements on compute and memory ranging from 0.6 GMACs/S to 2.5 GMACs/S for compute and up to 24 MB for the memory footprint, or 6M parameters.

<a id="P013"></a>

All these thresholds have been so far proposed and discussed rather separately than quality and runtime, although there is a common understanding that model size and number of parameters increase a neural coder’s robustness and quality at 16 kHz WB as per TR 26.940 [1]. This also does increase complexity, yet the later increase is specific to the model architecture, type of operations, precision and blocks used throughout the coder, and hence not directly comparable across candidates based on static metrics such as GMACs/S or number of parameters alone. This opens a gap that requires a more practical approach of measuring complexity considering a common baseline in terms of hardware, software and metric scale.

<a id="P015"></a>

## 2. Discussion

<a id="P016"></a>

As captured in TR 26.940 [1], MACs/S (or GMACs/S), and similarly FLOPS, count statically based on a graph trace the arithmetic computational load of neural inference. MACs/S are therefore useful to get a HW-independent rough estimate of the compute budget necessary to run an inference graph, but this does not account for non-arithmetic operations such as memory operations, tensor-level manipulations (e.g., slicing, concatenating etc.). As such, for low arithmetic intensity solutions where architectures and neural blocks become memory-bound rather than compute-bound, a higher MACs/S count is executed faster at runtime than a smaller MACs/S count, rendering the MACs/S metric inaccurate for total runtime complexity.

<a id="P017"></a>

RTF as complexity metric

<a id="P018"></a>

In the light of above, a more dynamic metric is necessary to capture all operations that consume cycles (including memory and tensor manipulations) in running inference. There have been proposals [2] in the past to consider HW-independent counting of such operations, but such dedicating tooling requires consensus on what to measure, how to measure and time to develop and validate. On the other hand, RTF evaluations as a dynamic and complete metric based on a common reference HW which can be set up, verified, and executed during codec evaluations by 3<sup>rd</sup> party listening labs with relative ease and low preparation based on automated testing scripts. The RTF metric simplifies thus counting by making the common reference a HW baseline and the metric scale the time normalized by the audio frame duration. It is also naturally bound and connected to the real-time constraint (<1.0), although more conservative RTF targets may be set.

<a id="P019"></a>

RTF can be aggregated as a single metric, , aggregating the encoder and decoder processing time, relative to the processed audio frame duration.

<a id="P020"></a>

Proposal 1: Utilize RTF, i.e., ( encoder_time + decoder_time ) / audio_frame_time, as a metric to directly compare complexity of codec candidates on a common baseline HW platform during evaluation (qualification and/or selection). The setup is to be executed and benchmarked by 3<sup>rd</sup> party host lab based on SA4-defined processing rules as objective complexity tests.

<a id="P022"></a>

GMACs/S, WMOPS (when applicable for non-neural signal processing elements) and ROM memory footprint are still relevant to understanding complexity as a whole and should be reported as part of the deliverables using agreed upon tooling. On the other hand, RAM can be monitored during runtime together with the RTF and relevant statistics thereof should be logged per ULBC candidate. The relevant statistics can be left for further discussion, for example, MEAN, P50, STDDEV, MAX, as necessary for both RTF and RAM metrics across the runtime evaluation of a candidate.

<a id="P023"></a>

Proposal 2: Capture and log dynamic RTF and RAM metrics and their statistics (e.g., MEAN, P50, STDDEV, MAX) for the objective complexity tests. GMACs/S, WMOPS (when applicable for non-neural signal processing elements) and ROM reports are to be provided together with the deliverables based on yet to be agreed tooling. The complexity limits on GMACs/S, WMOPS, ROM and RAM remain FFS for the bounds of the design space.

<a id="P025"></a>

RTF testing common platform

<a id="P026"></a>

A key aspect of using RTF as a metric for objectively measuring complexity across ULBC candidates is the baseline HW platform. Given that ULBC focus should be selecting the best coder, any HW-specific optimizations baked into the deliverables for runtime are premature. Therefore, we regard candidates that are capable to run in real-time on a general purpose mobile single thread CPU typical of a UE as potential ULBC candidate. ARM processors have been predominantly deployed across all mobile vendors. Over the last 6+ years ARM Cortex-A53/A55 cores (for efficiency, low-compute) and ARM Cortex-A76/A77/A78 cores (for performance, medium- & high-compute) have already become a legacy reference for low-power, high-performance compute based on ARM instruction set for multi-core processors. These are present in many past and present entry-level, mainstream and few flagship products spanning both wearable and mobile handset devices. Although these cores and corresponding ISAs are already surpassed in computing capabilities by current and upcoming flagship chipsets, they are expected to serve as a mature and well understood compute baseline, leaving room to implementers for accelerator- or ISA-specific optimizations for dedicated and/or better hardware, e.g., DSP, NPU/GPU, or CPUs.

<a id="P027"></a>

A common, openly available, reference HW platform based on an ARM Cortex-A76 operating at typical mobile chipset frequencies would be desirable to ease preparation and execution of RTF complexity evaluation across ULBC candidates. Furthermore, such a setup would correlate well with the results already captured in TR 26.940, Clause 7.6 [1], as well as other SotA neural coders, e.g., SoundStream as benchmarked on the Pixel 4’s A76 core [3]. A well supported platform, widely available, satisfying such desiderata is the Raspberry Pi 5 [4]:

<a id="T028"></a>

<a id="T028-R01"></a>
**T028-R01**

- <a id="T028-R01-C01"></a>列 1: Platform
- <a id="T028-R01-C02"></a>列 2: Processor
- <a id="T028-R01-C03"></a>列 3: Memory

<a id="T028-R02"></a>
**T028-R02**

- <a id="T028-R02-C01"></a>列 1: Raspberry Pi 5
- <a id="T028-R02-C02"></a>列 2: Broadcom BCM2712 2.4GHz quad-core 64-bit Arm Cortex-A76 CPU, 512KB per-core L2 caches, and a 2MB shared L3 cache
- <a id="T028-R02-C03"></a>列 3: LPDDR4X-4267 SDRAM (options for 1GB, 2GB, 4GB, 8GB and 16GB)

<a id="P029"></a>

Another key aspect is the SW inference runtime pipeline. Many runtimes and SW toolkits for inference are detailed in TR 26.940, Clause 10. However, so far no decision was reached on either model format for intermediate representation/sharing or inference runtime. Given the breadth of potential compute environments and vendor-specific toolkits for end deployments, we regard ONNX model format with a fixed set of operations best to allow for later HW-specific or ISA-specific optimizations. Regarding, the runtime for the RTF and common platform it comes therefore natural to rely on the ONNX Runtime (ONNX RT) with the CPU Execution Provider given the single-threaded baseline setup previously described. The configuration details for the ONNX model format (i.e., precision, operation set etc.) and ONNX RT with CPU EP are beyond the scope of this contribution and left FFS pending agreement of the below proposal.

<a id="P031"></a>

Proposal 3: Select the Raspberry Pi 5 as a common, openly available ARM Cortex-A76 HW platform for single-threaded CPU RTF complexity objective tests across all ULBC candidates. Resort to utilizing ONNX model format representation for ULBC candidates with a fixed opset and the ONNX Runtime with CPU Execution Provider. Further details on the configuration of the platform and ONNX representation format and runtime are FFS as part of the processing rules and deliverables.

<a id="P033"></a>

The full measurement methodology (build instructions, runtime versions, HW/SW configs, measurement scripts) is outside the scope of this contribution and further study of it is conditioned on the agreement on the main proposals above. The full measurement methodology should be agreed and captured as part of processing rules. As such, any party could run same setup and independently reproduce its own candidate and other candidate’s RTF and complexity numbers verifying the outcomes of the reported 3<sup>rd</sup> party host lab.

<a id="P034"></a>

Non-goals

<a id="P035"></a>

As disclaimer, the usage of RTF measurements and above platform and runtime are:

<a id="P036"></a>

Not intended to predict absolute latency, power draw, or thermal behavior on dedicated NPUs/DSPs/accelerators.

<a id="P037"></a>

Not intended to arbitrate which hardware vendor's execution engine is "better".

<a id="P039"></a>

## 3. Conclusion and proposal

<a id="P040"></a>

This contribution proposes utilizing RTF as a dynamic and relative complexity metric among candidates in complement of other static metrics discussed so far (i.e., GMACs/S, WMOPS and ROM/RAM). Applying a common RTF methodology, generic hardware and software, the purpose is to provide a comprehensive “measuring stick” for all candidates without relying simply on static complexity counts that discount certain operations.

<a id="P041"></a>

The paper proposals aim at agreeing first principles of utilizing RTF as complexity metric and full details and supporting tools (HW/SW configurations, scripts, etc.) and processing rules are to be further provided once key principles are agreed as follows:

<a id="P042"></a>

Proposal 1: Utilize RTF, i.e., ( encoder_time + decoder_time ) / audio_frame_time, as a metric to directly compare complexity of codec candidates on a common baseline HW platform during evaluation (qualification and/or selection). The setup is to be executed and benchmarked by 3<sup>rd</sup> party host lab based on SA4-defined processing rules as objective complexity tests.

<a id="P043"></a>

Proposal 2: Capture and log dynamic RTF and RAM metrics and their statistics (e.g., MEAN, P50, STDDEV, MAX) for the objective complexity tests. GMACs/S, WMOPS (when applicable for non-neural signal processing elements) and ROM reports are to be provided together with the deliverables based on yet to be agreed tooling. The complexity limits on GMACs/S, WMOPS, ROM and RAM remain FFS for the bounds of the design space.

<a id="P044"></a>

Proposal 3: Select the Raspberry Pi 5 as a common, openly available ARM Cortex-A76 HW platform for single-threaded CPU RTF complexity objective tests across all ULBC candidates. Resort to utilizing ONNX model format representation for ULBC candidates with a fixed opset and the ONNX Runtime with CPU Execution Provider. Further details on the configuration of the platform and ONNX representation format and runtime are FFS as part of the processing rules and deliverables.

<a id="P046"></a>

## 4. References

<a id="P047"></a>

[1] 3GPP TR 26.940: Study on supporting Ultra-Low Bitrate speech Codec (ULBC) for satellite access, V20.0.0, June 2026.

<a id="P048"></a>

[2] Tdoc S4-260721: Proposals for ULBC Codec Complexity Measurement. Status: Noted, Meeting SA4#135e, April 2026.

<a id="P049"></a>

[3] Zeghidour, Neil, Alejandro Luebs, Ahmed Omran, Jan Skoglund, and Marco Tagliasacchi. "Soundstream: An end-to-end neural audio codec." IEEE/ACM Transactions on Audio, Speech, and Language Processing 30 (2021): 495-507.

<a id="P050"></a>

[4] Raspberry Pi 5 Product Datasheet, Available: Online - RP-008348-DS-6-raspberry-pi-5-product-brief.pdf
