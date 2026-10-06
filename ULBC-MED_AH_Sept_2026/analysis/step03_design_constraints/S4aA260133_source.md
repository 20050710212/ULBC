# S4aA260133 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260133 [ULBC-MED] Complexity Principles.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWG Ad-hoc on ULBC-MED    S4aA260133

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    [ULBC-MED] Complexity Principles

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    Discussion/Agreement

<a id="P010"></a>

Introduction

<a id="P011"></a>

This document aims to propose some principles on complexity counting for ULBC and to clarify open issues on this matter, which a pre-requisite to set up design constraints on complexity.

<a id="P013"></a>

Principles on complexity counting

<a id="P014"></a>

Architecture

<a id="P016"></a>

TR 26.940 (clause 10.1.6) recommends that the reference implementation should be based on an ML model format for the ML components and C code for any auxiliary signal processing functions. Concretely, the model-format deliverable should state its operator set and version, and ONNX should be provided as common format as part of the reference implementation, so the reference can be used for integration, verification, and testing.

<a id="P018"></a>

It is expected that ULBC will be realized as C implementation with a hybrid architecture, meaning a conventional part for DSP processing and codec framework plus a machine-learning (ML) part for coding and processing ML components. As ONNX is the common format independent of the development format, the ONNX models will be inferred via the ONNX C runtime library and the inferences called from the C code.

<a id="P023"></a>

Principle 1: The complexity of both the C code and  the ML components shall be counted

<a id="P025"></a>

Principle 2: Common ML model format is ONNX

<a id="P027"></a>

C-code complexity

<a id="P030"></a>

Complexity characterization of C code has been part of 3GPP speech/audio codec work (e.g. AMR-WB, EVS, IVAS), performed using the ITU-T G.191 Software Tool Library (STL) weighted-operation counting methodology, giving a single WMOPS (weighted million operations per second) figure per codec function. This methodology assumes sequential execution of scalar “basic operators” on a defined reference processor model, and is well suited to the fixed/floating-point DSP-style C code.

<a id="P032"></a>

Principle 3: The C part is measured using the WMOPS counting using the WMC tool available in the ITU-T G.191 STL.

<a id="P034"></a>

The WMC tool provides PROM, ROM, RAM and WMOPS as metrices.

<a id="P037"></a>

ML model complexity

<a id="P039"></a>

PROM

<a id="P041"></a>

As the ML model will always be inferenced using a dedicated inference engine – especially later for deployment where it is expected that optimized inference engines are available on the UE, there is no need to count the program size of the inference engine.

<a id="P043"></a>

Principle 4: PROM is not counted for ML components. To treat C and ML part equally, PROM from C code is also not counted.

<a id="P046"></a>

ROM

<a id="P048"></a>

Independent of the platform used for execution, the model weights can be stored compressed, meaning in any supported format and mapped to a suitable data type for inference depending on the platform. Therefore, the ROM for a ML component is determined by the total size of its weights in bytes.

<a id="P050"></a>

Principle 5: For ML components, ROM footprint of the  ML components is determined by summing the number of parameters weighted by the corresponding byte depth of the data type.

<a id="P053"></a>

RAM

<a id="P055"></a>

It should be noted that even in today’s mid-range class processors (A55[1] and also in later CPUs) the SDOT/UDOT dot-product instructions set realizing the full SIMD support of compressed data (e.g. INT8) is still an optional feature of the core, while the floating point SIMD operation is mandatory. In case the specific accelerator is not present, a significantly better RTF may be achieved by converting the model to FP32 to make use of a floating point SIMD instruction set. However, this may come with the cost due to a higher demand for RAM.

<a id="P057"></a>

As a performant integration of the compressed weights cannot be guaranteed, a mapping to FP32 needs to be assumed in the worst case. This means the design constraint on RAM needs to take into account the case where the weights are mapped to FP32. Consequently, the number of parameters for the used ML component adds to the RAM size.

<a id="P059"></a>

Principle 6: For ML components, RAM for ML components is determined by number of parameters used for inference.

<a id="P062"></a>

Computational Complexity

<a id="P064"></a>

For reporting the computational complexity of the ML components TR 26.940 clause 6.4.2 recommends the categorization of the operators as listed in the Table below.

<a id="T066"></a>

<a id="T066-R01"></a>
**T066-R01**

- <a id="T066-R01-C01"></a>列 1: Category k
- <a id="T066-R01-C02"></a>列 2: Example Operators

<a id="T066-R02"></a>
**T066-R02**

- <a id="T066-R02-C01"></a>列 1: NN MAC Dominating Layers
- <a id="T066-R02-C02"></a>列 2: Conv2D, DepthwiseConv, FullyConnected, SVDF, TransposeConv, LSTM, BatchMatMul, …

<a id="T066-R03"></a>
**T066-R03**

- <a id="T066-R03-C01"></a>列 1: Vector (ALU) operations
- <a id="T066-R03-C02"></a>列 2: Add, Sub, Mul, Exp, Abs, Sum, SegmentSum, Neg, SquaredDifference, …

<a id="T066-R04"></a>
**T066-R04**

- <a id="T066-R04-C01"></a>列 1: Activation Functions
- <a id="T066-R04-C02"></a>列 2: ReLU, Logistic, Tanh, Softmax, ELU, GeLU, LeakyReLU, PReLU, LogSoftmax, …

<a id="T066-R05"></a>
**T066-R05**

- <a id="T066-R05-C01"></a>列 1: Data Reorganisation operations
- <a id="T066-R05-C02"></a>列 2: Transpose, Pad, Slice, DepthToSpace, Reshape, StridedSlice, Pack, OneHot, …

<a id="P068"></a>

While the categorization is clear and an automatic tool is discussed in S4aA260132, the question remains, how to count each individual operation. For the following discussion, a floating point operation (FLOP) to describe the computational complexity of an operation is used.

<a id="P070"></a>

NN MAC Layers

<a id="P072"></a>

Principle 7:  The multiplication and add (MAC) operation is counted as 2 FLOP.

<a id="P074"></a>

Vector ALU operation

<a id="P076"></a>

The operators may contain simple operation like ADD, SUB, MUL, … but also typically more complex operations such as LOG, SQRT, POW,… . The STL toolbox, which was used in the past for assessing the complexity, provides specific weights per operation, e.g. simple operation weight 1, 2 or weight 25 for LOG,… .

<a id="P078"></a>

To ease the discussion on the weights, it is proposed that every ALU operation gets the same weight as the MAC, meaning 2 FLOPS.

<a id="P080"></a>

Principle 8: Every ALU operation gets the same weight as the MAC, meaning 2 FLOPS.

<a id="P082"></a>

Activation Functions

<a id="P084"></a>

Similar to verctor ALU operations, to ease the discussion on the weights, it is proposed that every ALU operation gets the same weight as the MAC, meaning 2 FLOPS.

<a id="P086"></a>

Principle 9: Every activation function gets the same weight as the MAC, meaning 2 FLOPS.

<a id="P089"></a>

Data Reorganisation operations

<a id="P091"></a>

This category is considered as heavily implementation dependent and can be optimized later for deployment, while the other three categories can be considered as intrinsic complexity. It is therefore proposed to ignore this category for complexity.

<a id="P093"></a>

Note: To align this with the WMC tool, the weight for move16/32() needs to be zero.

<a id="P095"></a>

Principle 10: Data moves are not counted

<a id="P098"></a>

Custom operators

<a id="P100"></a>

To ensure that each operator can be implemented in an efficient way, only standard ONNX operators shall be allowed. This constraint enables reasonable counting, as the real implementation effort of custom operators may be much more costly than reflected by any assumed default FLOP number. Restricting the ML modules to ONNX default (standard) operators is also preferred because deployment will not stop at ONNX Runtime: chipset vendors convert models into their own native runtime formats, and these converters only recognize a defined subset of the standard ONNX opset. A custom operator has no native mapping on these targets. Standard operators, by contrast, are already implemented, tested and performance-tuned by each vendor's own toolchain, giving predictable numerical behavior and hardware-accelerated execution across the full range of devices.

<a id="P102"></a>

Principle 11: All operations required for ML inference shall be standard ONNX operators defined in a given opset version. No custom operators shall be permitted.

<a id="P105"></a>

Summarized complexity for ML component

<a id="P107"></a>

After clarification on the counting, the sum of all FLOPs and further the FLOPs/Sec for one ML component can be determined.

<a id="P109"></a>

All these counting are considered as static, meaning each inference will provide the same complexity and therefore a dedicated tool can be used. The source strongly favors the usage of a dedicated tool for measuring the ML complexity as brings the advantage of providing a clear implementation of the rules and eases the verification of ULBC. An example implementation is described in S4aA260132.

<a id="P111"></a>

Interplay C code and ML components

<a id="P113"></a>

As outlined above, the ML components will be interfaced within a C framework. As several, different ML components may be used and some may be inferenced several times per bundling time, these dynamics need to be captured. A tool can provide the static analysis per ML model in terms of flops, number of parameters, and so on.

<a id="P115"></a>

As WMC is already used for the C-code, the complexity counter just needs to be updated whenever an ML model is inferenced, e.g. the number of FLOPs are added to complexity counter and the number of parameter x 4 bytes are added to the RAM.

<a id="P119"></a>

With this, a manageable framework can be established bringing together the complexity estimation for the C code and the ML components. This gives clear guidelines on measuring the complexity for the proponents, while minimizing the risk of errors by manual counting. The optimization effort for the inference engine is also excluded from counting, as only basic parameters of the ML components count, but not the actual implementation.

<a id="P121"></a>

Principle 12: Metrices from C code and ML components shall be combined to a single figure

<a id="P123"></a>

Proposal

<a id="P124"></a>

The source proposes to establish the ULBC complexity principles presented above for both conventional C processing and machine-learning components:

<a id="P125"></a>

Principle 1: Both the complexity of the C code and the complexity of the ML components shall be counted.

<a id="P126"></a>

Principle 2: The common ML model format shall be ONNX.

<a id="P127"></a>

Principle 3: The C part shall be measured using WMOPS counting with the WMC tool available in the ITU-T G.191 STL

<a id="P128"></a>

Principle 4: PROM shall not be counted for ML components; to treat the C and ML parts equally, PROM from the C code shall also not be counted.

<a id="P129"></a>

Principle 5: For ML components, ROM shall be determined by summing the number of parameters weighted by the byte-depth of their corresponding data type.

<a id="P130"></a>

Principle 6: For ML components, RAM shall be determined by the number of parameters used for inference.

<a id="P131"></a>

Principle 7: A multiply-accumulate (MAC) operation shall be counted as 2 FLOPs.

<a id="P132"></a>

Principle 8: Every ALU operation gets the same weight as the MAC, meaning 2 FLOPS.

<a id="P133"></a>

Principle 9: Every activation function gets the same weight as the MAC, meaning 2 FLOPS.

<a id="P134"></a>

Principle 10: Data moves are not counted

<a id="P135"></a>

Principle 11: All operations required for ML inference shall be standard ONNX operators defined in a given opset version. No custom operators shall be permitted.

<a id="P136"></a>

Principle 12: Metrices from C code and ML components shall be combined to a single figure

<a id="P139"></a>

References

<a id="P140"></a>

[1] https://documentation-service.arm.com/static/5e7e09f6a3736a0d2e862d2f
