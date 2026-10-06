# S4aA260102 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260102 [ULBC-MED] Clarification of MACs metric and combined budgets.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260102

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Clarification of the MAC/s complexity metric and combined complexity and memory budgets

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Agreement

<a id="P008"></a>

## 1.    Introduction

<a id="P009"></a>

In S4-261514 [1], Samsung proposed MAC/s as the primary hardware-independent metric for the computational complexity of neural-network-based ULBC candidates, with approximately 1 GMAC/s or less as the initial complexity target and approximately 5 million parameters or less as the initial reference for neural model size, complemented by common-platform measurements of execution time and peak memory usage.

<a id="P010"></a>

In the discussion at SA4#137-e, the direction of working towards a clear definition of the complexity metric was supported, and clarification of the MAC/s metric was requested. In particular, the following questions were raised: whether only the neural-network operators are counted; whether ALU operations and activation functions are counted; whether memory movement is counted; and how other DSP components are taken into account. It was also observed that complexity proposals from companies span a wide numerical range, while the metric itself has not yet been precisely defined.

<a id="P011"></a>

This contribution follows up on [1] by (i) proposing a precise definition of the MAC/s metric that answers the questions raised, (ii) proposing that the complexity and parameter budgets each be defined as one combined budget across the two mandatory bitrate operating points, and (iii) substantiating the proposed numerical value of approximately 1 GMAC/s with a case study based on a widely deployed commercial processor.

<a id="P012"></a>

## 2.    Discussion

<a id="P013"></a>

## 2.1    Definition of the MAC/s metric

<a id="P014"></a>

A definition for the MAC/s metric is presented below. The definition follows the practice commonly used for reporting neural-network inference complexity, while remaining compatible with the established WMOPS methodology for conventional codec components.

<a id="P015"></a>

Counted operations. MAC/s is the number of multiply-accumulate operations executed by the trained neural-network operators of the codec per second of processed speech, evaluated in the worst-case operating configuration. All trained operators are counted: convolutional layers, fully-connected layers and matrix multiplications, recurrent layers (all gate and candidate computations), and attention mechanisms (projections, score computation and context aggregation). A multiplication without a corresponding accumulation is counted as one MAC. Defined in this way, MAC/s is a property of the codec architecture alone, independent of processor, compiler or implementation optimization, which is precisely the purpose of a hardware-independent design-constraint metric.

<a id="P016"></a>

Element-wise ALU operations and activation functions. Element-wise additions and multiplications, activation functions (e.g. tanh, sigmoid, ReLU, softmax), normalization layers and sampling operations are not counted in MAC/s. For typical neural speech-codec architectures these operations represent a small fraction of the multiply-accumulate workload, and their cost is strongly implementation-dependent (e.g. look-up table versus polynomial evaluation), so excluding them keeps the metric simple and comparable across candidates. As a safeguard, if the number of such operations of a candidate exceeds 10% of its MAC count, the candidate should additionally report this operation count separately (in operations per second).

<a id="P017"></a>

Memory movement. Memory movement is not counted in MAC/s. The cost of parameter and activation transfers depends on the memory hierarchy, data layout and SIMD width of a particular platform and cannot be expressed in a hardware-independent way. Memory behaviour is instead characterized by the complementary measures already proposed in [1]: parameter count, working and state memory, and common-platform measurements of execution time and peak memory usage during candidate evaluation. The common-platform execution-time measurement in particular reflects the true cost of memory movement on a representative implementation.

<a id="P018"></a>

Other DSP components. Conventional (non-neural) signal-processing components, e.g. resampling, filtering, windowing and transforms, and bitstream handling, are counted using the established WMOPS methodology based on ITU-T STL basic operators and are accounted against the WMOPS part of the complexity budget (clause 2.2). For ULBC candidates these components are expected to be small relative to the neural-network budget, and the common-platform runtime measurement captures the total including these components. This split avoids defining a speculative conversion factor between WMOPS and MAC/s while ensuring that all components of a candidate are accounted for.

<a id="P019"></a>

Accounting basis. Consistent with the EVS design constraints, where the complexity ceiling applied to encoder and decoder combined, the ULBC complexity budget should apply to encoder and decoder combined, evaluated per second of real-time processed speech in the worst-case operating configuration, including worst-case frame types and error-concealment operation at the decoder.

<a id="P020"></a>

## 2.2    One combined budget across the two mandatory operating points

<a id="P021"></a>

ULBC will define two mandatory bitrate operating points. In S4-261512 [2], Samsung proposed that these represent operating modes of a single codec using the same neural-network architecture and trained parameters. Independent of the conclusion on that proposal, the complexity and parameter budgets should each be defined as one combined budget rather than as per-operating-point budgets:

<a id="P022"></a>

–    Computational complexity: one combined budget, applied as the worst case across both mandatory operating points, comprising 1 GMAC/s or less for neural-network components, counted in MAC/s as defined in clause 2.1, together with [X, to be agreed] WMOPS or less for conventional (non-neural) signal-processing components, counted using ITU-T STL basic operators. Both parts of the budget apply to every candidate and at every operating configuration, irrespective of the coding technology used at each operating point. In particular, a candidate employing a neural-network-based solution at one operating point and a conventional signal-processing solution at the other is accounted under the same two-part budget: at each operating point, its neural components are counted against the MAC/s part and its conventional components against the WMOPS part. Since only one operating point is active at a time, the budget is not summed across operating points; the codec must remain within both parts of the budget in every operating configuration.

<a id="P023"></a>

–    Model parameters: one budget of approximately 5 million parameters or less, counting the total set of neural-network parameters required to support both mandatory operating points. Parameters shared between operating points are counted once; parameters used by only one operating point are counted in full against the same budget.

<a id="P024"></a>

Defining the complexity budget in this two-part form ensures that the design constraint is technology-neutral. A budget expressed only in MAC/s would constrain purely neural candidates while leaving conventional or hybrid candidates without a defined complexity envelope at some or all operating points. The two-part budget closes this gap without requiring any speculative conversion factor between WMOPS and MAC/s: each technology is measured in its established metric, and every candidate is subject to both limits.

<a id="P025"></a>

A combined parameter budget reflects the memory that an implementation must actually provision: a terminal supporting ULBC must store all parameters needed for both mandatory operating points, regardless of which is active at a given time. It also ensures that candidates using a common model across operating points and candidates using per-operating-point parameter sets are compared on an equal implementation-cost basis.

<a id="P026"></a>

## 2.3    Feasibility of the proposed budget: Arm Cortex-A55 case study

<a id="P027"></a>

To substantiate that approximately 1 GMAC/s is an appropriate computational envelope, i.e. sufficient for the targeted service while implementable across the relevant terminal base, it is useful to translate the budget onto a concrete, widely deployed processor. The Arm Cortex-A55 [3] is selected as the reference for this analysis because it is among the most widely deployed 64-bit application-processor cores currently in the market: it serves as the efficiency core of most recent smartphone SoCs and as the main CPU of wearable, automotive and IoT platforms. These device classes correspond directly to candidate terminal types for the targeted GEO-satellite conversational voice service: satellite-capable smartphones, wearables, automotive telematics units providing voice service where terrestrial coverage is unavailable (e.g. emergency voice), and satellite IoT terminals. The Cortex-A55 is furthermore an in-order, power-optimized core, so the analysis represents a conservative lower bound: the out-of-order cores (Cortex-A7x class and later) and neural accelerators present in many of the same SoCs only increase the available margin.

<a id="P028"></a>

Per core, the Cortex-A55 provides two 64-bit Advanced SIMD (NEON) pipelines, giving a peak throughput of 4 single-precision (FP32) MACs per cycle, 8 FP16 MACs per cycle, and 16 8-bit integer MACs per cycle where the Int8 dot-product instructions are implemented [3]. Optimized on-device inference libraries typically sustain on the order of 40–60% of this peak for speech-sized neural workloads. Table 1 lists examples of commercial SoCs built on Cortex-A55 clusters, together with the fraction of a single core that a 1 GMAC/s codec (encoder and decoder combined) would occupy in single-precision floating point, assuming 40–50% sustained efficiency. Automotive telematics and in-vehicle infotainment platforms similarly integrate dual- or quad-core Cortex-A55 clusters clocked in the 1.5–2.0 GHz range.

<a id="T029"></a>

<a id="T029-R01"></a>
**T029-R01**

- <a id="T029-R01-C01"></a>列 1: Device class
- <a id="T029-R01-C02"></a>列 2: Example SoC
- <a id="T029-R01-C03"></a>列 3: Cortex-A55 configuration
- <a id="T029-R01-C04"></a>列 4: Peak FP32 MAC rate per core
- <a id="T029-R01-C05"></a>列 5: Share of one core for 1 GMAC/s (FP32, 40–50% sustained)

<a id="T029-R02"></a>
**T029-R02**

- <a id="T029-R02-C01"></a>列 1: Smartphone (entry/mid)
- <a id="T029-R02-C02"></a>列 2: MediaTek Helio G99
- <a id="T029-R02-C03"></a>列 3: 6 × A55 @ 2.0 GHz (+ 2 × A76)
- <a id="T029-R02-C04"></a>列 4: 8.0 GMAC/s
- <a id="T029-R02-C05"></a>列 5: 25–31%

<a id="T029-R03"></a>
**T029-R03**

- <a id="T029-R03-C01"></a>列 1: Smartphone (efficiency-only)
- <a id="T029-R03-C02"></a>列 2: Samsung Exynos 850
- <a id="T029-R03-C03"></a>列 3: 8 × A55 @ 2.0 GHz
- <a id="T029-R03-C04"></a>列 4: 8.0 GMAC/s
- <a id="T029-R03-C05"></a>列 5: 25–31%

<a id="T029-R04"></a>
**T029-R04**

- <a id="T029-R04-C01"></a>列 1: Wearable
- <a id="T029-R04-C02"></a>列 2: Samsung Exynos W930
- <a id="T029-R04-C03"></a>列 3: 2 × A55 @ 1.4 GHz
- <a id="T029-R04-C04"></a>列 4: 5.6 GMAC/s
- <a id="T029-R04-C05"></a>列 5: 36–45%

<a id="T029-R05"></a>
**T029-R05**

- <a id="T029-R05-C01"></a>列 1: Automotive / industrial gateway
- <a id="T029-R05-C02"></a>列 2: NXP i.MX 93
- <a id="T029-R05-C03"></a>列 3: 2 × A55 @ 1.7 GHz
- <a id="T029-R05-C04"></a>列 4: 6.8 GMAC/s
- <a id="T029-R05-C05"></a>列 5: 29–37%

<a id="T029-R06"></a>
**T029-R06**

- <a id="T029-R06-C01"></a>列 1: Automotive / embedded vision
- <a id="T029-R06-C02"></a>列 2: Renesas RZ/V2N
- <a id="T029-R06-C03"></a>列 3: 4 × A55 @ 1.8 GHz
- <a id="T029-R06-C04"></a>列 4: 7.2 GMAC/s
- <a id="T029-R06-C05"></a>列 5: 28–35%

<a id="P030"></a>

Table 1: Commercial Cortex-A55-based SoCs and the per-core load implied by a 1 GMAC/s codec

<a id="P031"></a>

A 1 GMAC/s codec thus requires approximately 500–625 MHz-equivalent of one Cortex-A55 core in single-precision floating point, i.e. roughly one quarter to one half of a single efficiency core depending on device class, out of clusters of two to eight such cores. With 8-bit quantization the same budget requires less than 10% of a single core. In all listed device classes, the remaining cores and the large majority of the CPU capability stay available for the operating system, protocol stacks and applications, and the sustained per-core load is compatible with the thermal and battery constraints of a continuous voice call even on wearable-class devices.

<a id="P032"></a>

Two further observations are relevant to the numerical value of the budget:

<a id="P033"></a>

–    1 GMAC/s corresponds to approximately 2×10⁹ arithmetic operations per second, which is already more than an order of magnitude above the complexity ceiling of EVS (88 WMOPS, encoder plus decoder). The proposed budget is therefore not restrictive relative to legacy conversational codecs; it is a generous, contemporary envelope.

<a id="P034"></a>

–    Conversely, budgets substantially above 1 GMAC/s change the implementation class. At 2.5 GMAC/s in single precision, the sustained load approaches or exceeds one full Cortex-A55 core on wearable-class devices, with corresponding consequences for power consumption in a sustained call and for coexistence with the rest of the system. Since ULBC targets a specific satellite voice service with a defined performance objective relative to AMR-WB at 12.65 kbit/s, such additional complexity should be justified by a corresponding benefit to the targeted service, as discussed in [1].

<a id="P035"></a>

The case study confirms that approximately 1 GMAC/s or less is simultaneously (i) implementable with comfortable margin across the full range of relevant terminal classes, using only a fraction of one CPU efficiency core, and (ii) a computational envelope well beyond legacy conversational codecs, providing ample resources for a high-quality neural codec design.

<a id="P036"></a>

## 3.    Conclusion and proposals

<a id="P037"></a>

It is proposed to:

<a id="P038"></a>

–    define MAC/s as the number of multiply-accumulate operations executed by the trained neural-network operators of the codec per second of processed speech, evaluated in the worst-case operating configuration, counting all trained operators (convolutional, fully-connected/matrix-multiplication, recurrent and attention operators);

<a id="P039"></a>

–    exclude element-wise ALU operations and activation functions from the MAC/s count, with separate reporting (in operations per second) where they exceed 10% of the MAC count of a candidate;

<a id="P040"></a>

–    exclude memory movement from the MAC/s count and characterize memory behaviour through parameter count, working and state memory, and common-platform measurements of execution time and peak memory usage;

<a id="P041"></a>

–    count conventional (non-neural) signal-processing components separately using the WMOPS methodology based on ITU-T STL basic operators and accounted against the WMOPS part of the budget;

<a id="P042"></a>

–    apply the computational complexity budget to encoder and decoder combined, consistent with EVS practice;

<a id="P043"></a>

–    define one combined complexity budget of 1 GMAC/s or less and [X, to be agreed] WMOPs or less or conventional (non-neural) signal-processing components, applied as the worst case across both mandatory bitrate operating points, and one combined parameter budget of approximately 5 million parameters or less, covering the total set of parameters required to support both mandatory operating points; and

<a id="P044"></a>

–    capture the corresponding text in ULBC-4.

<a id="P045"></a>

## 4.    References

<a id="P046"></a>

[1]    S4-261514, “[ULBC-MED] Considerations on complexity and memory constraints for ULBC”, Samsung Electronics Iberia SA, 3GPP TSG-SA4#137-e.

<a id="P047"></a>

[2]    S4-261512, “[ULBC-MED] Design constraints for the two ULBC bitrates”, Samsung Electronics Iberia SA, 3GPP TSG-SA4#137-e.

<a id="P048"></a>

[3]    Arm, “Cortex-A55 Core Technical Reference Manual”; Arm, “Cortex-A55 Software Optimization Guide”.
