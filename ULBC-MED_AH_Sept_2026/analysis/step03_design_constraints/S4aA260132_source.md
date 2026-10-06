# S4aA260132 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260132 Complexity Profiling of ONNX Models.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWG Ad-hoc on ULBC-MED    S4aA260132

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P002"></a>

Source:    Fraunhofer IIS

<a id="P003"></a>

Title:    [ULBC-MED] Complexity Profiling of ONNX Models

<a id="P004"></a>

Document for:    Discussion

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

## 1    Introduction

<a id="P007"></a>

The ULBC work item [1] requires computational complexity and memory footprint constraints that ensures implementability on UE platforms. Although the ULBC design constraints ULBC-4 v0.2.1 [3] were agreed at SA4#137-e,  the computational complexity and memory clause is still open. Especially, comments were raised that a stable and well-defined metric regarding complexity is required before agreeing in any concrete numbers for the design constraints.

<a id="P008"></a>

As part of this task, the present document reports on a graph-level profiling tool that directly analyzes an ONNX model and derives, from one file, the figures requested across  the different positions under discussion: MACs and FLOPs per second, the operator profile in the four categories defined in [4], parameter count, ROM in bytes per stored precision, and the peak and average activation working set of one inference. Results are given for the four DAC configurations of [9]. The purpose is to demonstrate feasibility and to collect feedback on the set of reported figures before the counting method of ULBC-4 is fixed. The tool itself is not part of this contribution.

<a id="P009"></a>

## 2    Background

<a id="P010"></a>

## 2.1    Proposed complexity metrices for ULBC

<a id="P011"></a>

Table 1 lists different positions recorded in ULBC-4 v0.2.1 [3]. It collects what a candidate would have to measure and report for its ML components.

<a id="P012"></a>

Table 1: Proposed complexity metrices for ULBC

<a id="T013"></a>

<a id="T013-R01"></a>
**T013-R01**

- <a id="T013-R01-C01"></a>列 1: Figure
- <a id="T013-R01-C02"></a>列 2: Reference

<a id="T013-R02"></a>
**T013-R02**

- <a id="T013-R02-C01"></a>列 1: MAC/s (GMAC/s) of the ML components
- <a id="T013-R02-C02"></a>列 2: [3] [8] [10] [11]

<a id="T013-R03"></a>
**T013-R03**

- <a id="T013-R03-C01"></a>列 1: FLOP/s including all operators, not only MAC layers
- <a id="T013-R03-C02"></a>列 2: [12] [13]

<a id="T013-R04"></a>
**T013-R04**

- <a id="T013-R04-C01"></a>列 1: Number of parameters
- <a id="T013-R04-C02"></a>列 2: [3] [9] [12]

<a id="T013-R05"></a>
**T013-R05**

- <a id="T013-R05-C01"></a>列 1: Model size in bytes according to the stored precision
- <a id="T013-R05-C02"></a>列 2: [2] [3] [8]

<a id="T013-R06"></a>
**T013-R06**

- <a id="T013-R06-C01"></a>列 1: Operator profile in four categories (data reorganisation, NN MAC, vector ALU, activation)
- <a id="T013-R06-C02"></a>列 2: [4] [5]

<a id="T013-R07"></a>
**T013-R07**

- <a id="T013-R07-C01"></a>列 1: Dominant arithmetic precision per NN MAC layer, precision-weighted MACs
- <a id="T013-R07-C02"></a>列 2: [4]

<a id="T013-R08"></a>
**T013-R08**

- <a id="T013-R08-C01"></a>列 1: Static ROM, peak and average dynamic memory, persistent state
- <a id="T013-R08-C02"></a>列 2: [4] [8] [11]

<a id="T013-R09"></a>
**T013-R09**

- <a id="T013-R09-C01"></a>列 1: Encoder and decoder reported separately
- <a id="T013-R09-C02"></a>列 2: [5]

<a id="P015"></a>

## 2.2    ONNX as the interchange format

<a id="P016"></a>

TR 26.940 [2], based on [6], concludes that a reference implementation based on a model format separates the algorithm definition from the hardware-specific implementation. It names ONNX as common delivery format and the development format (PyTorch or Tensorflow) as additional framework to ease deployment.

<a id="P017"></a>

The choice for ONNX relies in the stability of the format. While other formats are more often revised and incompatibility may occur over time, ONNX is known to be stable and backwards compatible regarding operator sets. In that sense, it is reasonable to take ONNX as the basis for measuring the ML complexity to ensure that also in the future the measurements can be verified.

<a id="P018"></a>

## 2.3    Why graph-level profiling?

<a id="P019"></a>

An ONNX model is a static graph with fixed operations, tensor shapes, and trained weights. Once input length and batch size are fixed, shape inference derives all intermediate tensor shapes. This means the proposed profiling can be reproduced by anyone from the submitted files alone, making it suitable for verification by independent entities.

<a id="P020"></a>

## 3    Graph-level profiling of ONNX models

<a id="P021"></a>

## 3.1    Processing

<a id="P022"></a>

The tool loads the ONNX file and runs ONNX shape inference. All declared inputs must have static shapes and a fixed batch size; dynamic or symbolic axes are rejected with an explicit error, which prevents incorrect operation counts. Each node of the graph is then processed as follows:

<a id="P023"></a>

Classification: Each operator type is mapped to one of the four categories defined in [4]: NN MAC layers, vector ALU operations, activation functions, and data reorganization. Currently 100 of the 202 operators in the ONNX standard operator set are mapped, covering most layers commonly used in DNNs, which can be extended as per requirement.

<a id="P024"></a>

MAC: For NN MAC layers, the number of MAC is derived from the resolved input, output, and weight shapes. Bias additions in convolution layers are not counted as MAC.

<a id="P025"></a>

FLOP: Non-MAC operators (e.g. Pow, Exp, Reduce) are counted as FLOP. The total is computed as 2 × MAC + non-MAC FLOP.

<a id="P026"></a>

Memory: ROM is the total size in bytes of all parameter tensors stored in the file, reported separately per data type. Each tensor is counted once; metadata is excluded. The parameter count is the total number of elements in the same tensors.

<a id="P027"></a>

Coverage: Unmapped operators, and NN MAC layers whose tensor shapes cannot be resolved, are counted as zero and listed explicitly in the coverage report. The analysis is not aborted in these cases, so an incomplete profile remains visible.

<a id="P029"></a>

Encoder, quantizer and decoder can be profiled as separate graphs, so that the per-component report of [5] and [8] is obtained directly.

<a id="P030"></a>

## 3.2    Scope and limitations

<a id="P031"></a>

The profile gives a static, hardware-independent characterization of the graph. It does not replace a cycle count on a target platform, nor does it predict runtime performance. The current version of the tool has the following limitations:

<a id="P032"></a>

Only static shapes and batch size one is supported; graphs with control flow (Loop, If, Scan) are not traversed.

<a id="P033"></a>

Quantized operators (QLinearConv, MatMulInteger, and related) are not yet counted, although the stored weight precision is reported for all data types, including FP16 and INT8.

<a id="P034"></a>

Bias terms are not counted as MACs; this is the main reason for small differences compared to tools that do count them.

<a id="P035"></a>

## 3.3    Static and run-time quantities

<a id="P036"></a>

All figures produced by the tool are static properties of the graph for a given input shape. Table 2 indicates, for each quantity, whether it is fully determined by the graph or whether it depends on runtime, platform, or input signal.

<a id="P037"></a>

Because shapes are static, and no control flow is present, every inference executes the same operations on tensors of the same size. For a single ML component, there is therefore no difference between typical and worst-case inference. A worst case can only arise from control flow inside the graph, dynamic shapes, or a varying number of calls to an ML component per bundling period. The first two are outside the tool's scope; the last lies outside the graph and is captured by the per-call counting proposed in [8].

<a id="P038"></a>

Table 2: Static versus run-time quantities

<a id="T039"></a>

<a id="T039-R01"></a>
**T039-R01**

- <a id="T039-R01-C01"></a>列 1: Quantity
- <a id="T039-R01-C02"></a>列 2: Determined by
- <a id="T039-R01-C03"></a>列 3: Note

<a id="T039-R02"></a>
**T039-R02**

- <a id="T039-R02-C01"></a>列 1: MAC, FLOP per inference
- <a id="T039-R02-C02"></a>列 2: Graph (static)
- <a id="T039-R02-C03"></a>列 3: Independent of platform/input; FLOPs depend on cost convention

<a id="T039-R03"></a>
**T039-R03**

- <a id="T039-R03-C01"></a>列 1: MAC/s, FLOP/s
- <a id="T039-R03-C02"></a>列 2: Graph + frame duration (static)
- <a id="T039-R03-C03"></a>列 3: Per-inference count divided by the audio duration of one input

<a id="T039-R04"></a>
**T039-R04**

- <a id="T039-R04-C01"></a>列 1: Operator profile per category
- <a id="T039-R04-C02"></a>列 2: Graph (static)
- <a id="T039-R04-C03"></a>列 3: Depends on the export path (framework, exporter, opset), not on the run-time

<a id="T039-R05"></a>
**T039-R05**

- <a id="T039-R05-C01"></a>列 1: Parameter count, ROM per data type
- <a id="T039-R05-C02"></a>列 2: Graph (static)
- <a id="T039-R05-C03"></a>列 3: As stored in file; may be re-packed/re-quantized at load

<a id="T039-R06"></a>
**T039-R06**

- <a id="T039-R06-C01"></a>列 1: Number of inference calls per bundling period
- <a id="T039-R06-C02"></a>列 2: Codec logic (run-time)
- <a id="T039-R06-C03"></a>列 3: Outside graph; counted per call, as proposed in [8]

<a id="P041"></a>

## 4    Results for DAC

<a id="P042"></a>

## 4.1    Set-up

<a id="P043"></a>

The four Descript Audio Codec (DAC) [17] configurations evaluated in [9] were used: 16 kHz sampling rate, encoder rates [2, 4, 5, 8], decoder rates [8, 5, 4, 2], and two codebooks of 1024 entries — i.e. 1.0 kbit/s at a 50 Hz frame rate. The encoder and decoder dimensions yield roughly 1 M, 3 M, 6 M, and 9 M parameters. Encoder, residual vector quantizer, and decoder were exported from PyTorch to ONNX [18] (opset 17) with weight normalization folded. Each was exported twice: once for a 1 s input, to obtain per-second rates, and once for an 80 ms input — the shorter bundling period of [3] — to obtain the working set of a single inference. The profile depends only on the architecture and the input length, not on the trained weights, and is therefore identical for all trained models evaluated in [9]. For every exported graph, ONNX Runtime was verified to reproduce the PyTorch output to within 1e-6.

<a id="P044"></a>

## 4.2    Totals per configuration

<a id="P045"></a>

Table 3: Per-second totals of encoder + quantizer + decoder (FP32 export)

<a id="T046"></a>

<a id="T046-R01"></a>
**T046-R01**

- <a id="T046-R01-C01"></a>列 1: Model
- <a id="T046-R01-C02"></a>列 2: ONNX profiling tool<br><br>GMAC/s
- <a id="T046-R01-C03"></a>列 3: ONNX profiling tool<br><br>GFLOP/s
- <a id="T046-R01-C04"></a>列 4: ONNX <br>profiling tool<br><br>Parameters (M)
- <a id="T046-R01-C05"></a>列 5: ONNX <br>profiling tool<br><br>ROM FP32 (MB)
- <a id="T046-R01-C06"></a>列 6: ptflops <br><br><br>GMAC/s
- <a id="T046-R01-C07"></a>列 7: GMAC/s Difference (onnx profiling tool - ptflops)

<a id="T046-R02"></a>
**T046-R02**

- <a id="T046-R02-C01"></a>列 1: DAC 1M
- <a id="T046-R02-C02"></a>列 2: 0.547
- <a id="T046-R02-C03"></a>列 3: 1.185
- <a id="T046-R02-C04"></a>列 4: 1.08
- <a id="T046-R02-C05"></a>列 5: 4.31
- <a id="T046-R02-C06"></a>列 6: 0.552
- <a id="T046-R02-C07"></a>列 7: -0.8 %

<a id="T046-R03"></a>
**T046-R03**

- <a id="T046-R03-C01"></a>列 1: DAC 3M
- <a id="T046-R03-C02"></a>列 2: 1.640
- <a id="T046-R03-C03"></a>列 3: 3.440
- <a id="T046-R03-C04"></a>列 4: 3.01
- <a id="T046-R03-C05"></a>列 5: 12.06
- <a id="T046-R03-C06"></a>列 6: 1.649
- <a id="T046-R03-C07"></a>列 7: -0.6 %

<a id="T046-R04"></a>
**T046-R04**

- <a id="T046-R04-C01"></a>列 1: DAC 6M
- <a id="T046-R04-C02"></a>列 2: 3.498
- <a id="T046-R04-C03"></a>列 3: 7.217
- <a id="T046-R04-C04"></a>列 4: 6.07
- <a id="T046-R04-C05"></a>列 5: 24.29
- <a id="T046-R04-C06"></a>列 6: 3.511
- <a id="T046-R04-C07"></a>列 7: -0.4 %

<a id="T046-R05"></a>
**T046-R05**

- <a id="T046-R05-C01"></a>列 1: DAC 9M
- <a id="T046-R05-C02"></a>列 2: 4.828
- <a id="T046-R05-C03"></a>列 3: 9.936
- <a id="T046-R05-C04"></a>列 4: 9.04
- <a id="T046-R05-C05"></a>列 5: 36.16
- <a id="T046-R05-C06"></a>列 6: 4.845
- <a id="T046-R05-C07"></a>列 7: -0.3 %

<a id="P048"></a>

The MAC counts agree with the ptflops figures obtained from the PyTorch models to within one percent; the remaining difference is the bias addition in the convolutional layers, which ptflops counts as a MAC. The FLOP figure is about 2.1 times the MAC figure, i.e. non-MAC operators contribute between 3 % and 8 % of the FLOPs in these graphs (see clause 4.4). At FP32 precision, the ROM is four bytes per parameter.

<a id="P049"></a>

## 4.3    Per-component figures

<a id="P050"></a>

Table 4: Per-component figures; rates for 1 s of audio, working set for one 80 ms inference

<a id="T051"></a>

<a id="T051-R01"></a>
**T051-R01**

- <a id="T051-R01-C01"></a>列 1: Model
- <a id="T051-R01-C02"></a>列 2: Part
- <a id="T051-R01-C03"></a>列 3: GMAC/s
- <a id="T051-R01-C04"></a>列 4: GFLOP/s
- <a id="T051-R01-C05"></a>列 5: Parameters
- <a id="T051-R01-C06"></a>列 6: ROM FP32 (MB)

<a id="T051-R02"></a>
**T051-R02**

- <a id="T051-R02-C01"></a>列 1: DAC 1M
- <a id="T051-R02-C02"></a>列 2: encoder
- <a id="T051-R02-C03"></a>列 3: 0.433
- <a id="T051-R02-C04"></a>列 4: 0.925
- <a id="T051-R02-C05"></a>列 5: 760 k
- <a id="T051-R02-C06"></a>列 6: 3.04

<a id="T051-R03"></a>
**T051-R03**

- <a id="T051-R03-C01"></a>列 1: 
- <a id="T051-R03-C02"></a>列 2: quantizer
- <a id="T051-R03-C03"></a>列 3: 0.001
- <a id="T051-R03-C04"></a>列 4: 0.003
- <a id="T051-R03-C05"></a>列 5: 25 k
- <a id="T051-R03-C06"></a>列 6: 0.10

<a id="T051-R04"></a>
**T051-R04**

- <a id="T051-R04-C01"></a>列 1: 
- <a id="T051-R04-C02"></a>列 2: decoder
- <a id="T051-R04-C03"></a>列 3: 0.114
- <a id="T051-R04-C04"></a>列 4: 0.257
- <a id="T051-R04-C05"></a>列 5: 293 k
- <a id="T051-R04-C06"></a>列 6: 1.17

<a id="T051-R05"></a>
**T051-R05**

- <a id="T051-R05-C01"></a>列 1: DAC 3M
- <a id="T051-R05-C02"></a>列 2: encoder
- <a id="T051-R05-C03"></a>列 3: 0.433
- <a id="T051-R05-C04"></a>列 4: 0.925
- <a id="T051-R05-C05"></a>列 5: 760 k
- <a id="T051-R05-C06"></a>列 6: 3.04

<a id="T051-R06"></a>
**T051-R06**

- <a id="T051-R06-C01"></a>列 1: 
- <a id="T051-R06-C02"></a>列 2: quantizer
- <a id="T051-R06-C03"></a>列 3: 0.001
- <a id="T051-R06-C04"></a>列 4: 0.003
- <a id="T051-R06-C05"></a>列 5: 25 k
- <a id="T051-R06-C06"></a>列 6: 0.10

<a id="T051-R07"></a>
**T051-R07**

- <a id="T051-R07-C01"></a>列 1: 
- <a id="T051-R07-C02"></a>列 2: decoder
- <a id="T051-R07-C03"></a>列 3: 1.206
- <a id="T051-R07-C04"></a>列 4: 2.512
- <a id="T051-R07-C05"></a>列 5: 2.23 M
- <a id="T051-R07-C06"></a>列 6: 8.92

<a id="T051-R08"></a>
**T051-R08**

- <a id="T051-R08-C01"></a>列 1: DAC 6M
- <a id="T051-R08-C02"></a>列 2: encoder
- <a id="T051-R08-C03"></a>列 3: 0.433
- <a id="T051-R08-C04"></a>列 4: 0.925
- <a id="T051-R08-C05"></a>列 5: 760 k
- <a id="T051-R08-C06"></a>列 6: 3.04

<a id="T051-R09"></a>
**T051-R09**

- <a id="T051-R09-C01"></a>列 1: 
- <a id="T051-R09-C02"></a>列 2: quantizer
- <a id="T051-R09-C03"></a>列 3: 0.001
- <a id="T051-R09-C04"></a>列 4: 0.003
- <a id="T051-R09-C05"></a>列 5: 25 k
- <a id="T051-R09-C06"></a>列 6: 0.10

<a id="T051-R10"></a>
**T051-R10**

- <a id="T051-R10-C01"></a>列 1: 
- <a id="T051-R10-C02"></a>列 2: decoder
- <a id="T051-R10-C03"></a>列 3: 3.065
- <a id="T051-R10-C04"></a>列 4: 6.289
- <a id="T051-R10-C05"></a>列 5: 5.29 M
- <a id="T051-R10-C06"></a>列 6: 21.15

<a id="T051-R11"></a>
**T051-R11**

- <a id="T051-R11-C01"></a>列 1: DAC 9M
- <a id="T051-R11-C02"></a>列 2: encoder
- <a id="T051-R11-C03"></a>列 3: 1.728
- <a id="T051-R11-C04"></a>列 4: 3.575
- <a id="T051-R11-C05"></a>列 5: 3.03 M
- <a id="T051-R11-C06"></a>列 6: 12.13

<a id="T051-R12"></a>
**T051-R12**

- <a id="T051-R12-C01"></a>列 1: 
- <a id="T051-R12-C02"></a>列 2: quantizer
- <a id="T051-R12-C03"></a>列 3: 0.001
- <a id="T051-R12-C04"></a>列 4: 0.003
- <a id="T051-R12-C05"></a>列 5: 32 k
- <a id="T051-R12-C06"></a>列 6: 0.13

<a id="T051-R13"></a>
**T051-R13**

- <a id="T051-R13-C01"></a>列 1: 
- <a id="T051-R13-C02"></a>列 2: decoder
- <a id="T051-R13-C03"></a>列 3: 3.099
- <a id="T051-R13-C04"></a>列 4: 6.358
- <a id="T051-R13-C05"></a>列 5: 5.98 M
- <a id="T051-R13-C06"></a>列 6: 23.90

<a id="P053"></a>

The decoder dominates the complexity of all configurations except the smallest one; the residual vector quantizer is negligible in MACs but contributes the data-reorganization operators (ArgMax, Gather, Expand, Transpose) that a MAC-only count does not see.

<a id="P054"></a>

## 4.4 Stored precision

<a id="P055"></a>

Table 5. Compares the FP32 export of DAC 6M with the same graph converted to FP16 weights and activations. The MAC count is unchanged, while ROM and working set are halved. The stored precision is reported per initializer, which provides both the per-layer precision requested in [4] and the size based on stored precision requested in [8]. A precision-weighted MAC count as proposed in [4] is obtained by multiplying the per-layer MAC by the agreed factor for the reported data type.

<a id="P056"></a>

Table 5: DAC 6M, 80 ms inference: FP32 export versus FP16 conversion

<a id="T057"></a>

<a id="T057-R01"></a>
**T057-R01**

- <a id="T057-R01-C01"></a>列 1: Component
- <a id="T057-R01-C02"></a>列 2: Export
- <a id="T057-R01-C03"></a>列 3: Reported weight type
- <a id="T057-R01-C04"></a>列 4: MACs
- <a id="T057-R01-C05"></a>列 5: Parameters
- <a id="T057-R01-C06"></a>列 6: ROM (MB)

<a id="T057-R02"></a>
**T057-R02**

- <a id="T057-R02-C01"></a>列 1: encoder
- <a id="T057-R02-C02"></a>列 2: FP32
- <a id="T057-R02-C03"></a>列 3: FLOAT
- <a id="T057-R02-C04"></a>列 4: 34,612,224
- <a id="T057-R02-C05"></a>列 5: 760,344
- <a id="T057-R02-C06"></a>列 6: 3.04

<a id="T057-R03"></a>
**T057-R03**

- <a id="T057-R03-C01"></a>列 1: 
- <a id="T057-R03-C02"></a>列 2: FP16
- <a id="T057-R03-C03"></a>列 3: FLOAT16
- <a id="T057-R03-C04"></a>列 4: 34,612,224
- <a id="T057-R03-C05"></a>列 5: 760,344
- <a id="T057-R03-C06"></a>列 6: 1.52

<a id="T057-R04"></a>
**T057-R04**

- <a id="T057-R04-C01"></a>列 1: decoder
- <a id="T057-R04-C02"></a>列 2: FP32
- <a id="T057-R04-C03"></a>列 3: FLOAT
- <a id="T057-R04-C04"></a>列 4: 244,177,152
- <a id="T057-R04-C05"></a>列 5: 5,287,489
- <a id="T057-R04-C06"></a>列 6: 21.15

<a id="T057-R05"></a>
**T057-R05**

- <a id="T057-R05-C01"></a>列 1: 
- <a id="T057-R05-C02"></a>列 2: FP16
- <a id="T057-R05-C03"></a>列 3: FLOAT16
- <a id="T057-R05-C04"></a>列 4: 244,177,152
- <a id="T057-R05-C05"></a>列 5: 5,287,489
- <a id="T057-R05-C06"></a>列 6: 10.57

<a id="P059"></a>

## 4.5    Cross-check against other profiling tools

<a id="P060"></a>

The profile of DAC 6M for one 80 ms inference was compared with two publicly available tools: ptflops [19], which counts on the PyTorch module and was used for the DAC figures in [14], and onnx-tool [20], which reads the ONNX graph like the present tool. Table 10 compares the MAC count of the NN MAC layers and the parameter count per component; Table 6 compares the per-element cost assumed for the decoder's element-wise operators.

<a id="P061"></a>

Table 6: DAC 6M, 80 ms inference: NN MAC layers and parameters, proposed tool verses onnx-tool and ptflops

<a id="T062"></a>

<a id="T062-R01"></a>
**T062-R01**

- <a id="T062-R01-C01"></a>列 1: Component
- <a id="T062-R01-C02"></a>列 2: Operator
- <a id="T062-R01-C03"></a>列 3: This tool
- <a id="T062-R01-C04"></a>列 4: onnx-tool [20]
- <a id="T062-R01-C05"></a>列 5: ptflops [19]

<a id="T062-R02"></a>
**T062-R02**

- <a id="T062-R02-C01"></a>列 1: encoder
- <a id="T062-R02-C02"></a>列 2: Conv
- <a id="T062-R02-C03"></a>列 3: 34,612,224
- <a id="T062-R02-C04"></a>列 4: 34,904,064
- <a id="T062-R02-C05"></a>列 5: 

<a id="T062-R03"></a>
**T062-R03**

- <a id="T062-R03-C01"></a>列 1: 
- <a id="T062-R03-C02"></a>列 2: all NN MAC layers
- <a id="T062-R03-C03"></a>列 3: 34,612,224
- <a id="T062-R03-C04"></a>列 4: 34,904,064
- <a id="T062-R03-C05"></a>列 5: 34,904,064

<a id="T062-R04"></a>
**T062-R04**

- <a id="T062-R04-C01"></a>列 1: 
- <a id="T062-R04-C02"></a>列 2: parameters
- <a id="T062-R04-C03"></a>列 3: 760,344
- <a id="T062-R04-C04"></a>列 4: 760,344
- <a id="T062-R04-C05"></a>列 5: 758,892

<a id="T062-R05"></a>
**T062-R05**

- <a id="T062-R05-C01"></a>列 1: quantizer
- <a id="T062-R05-C02"></a>列 2: Conv
- <a id="T062-R05-C03"></a>列 3: 24,576
- <a id="T062-R05-C04"></a>列 4: 26,176
- <a id="T062-R05-C05"></a>列 5: 

<a id="T062-R06"></a>
**T062-R06**

- <a id="T062-R06-C01"></a>列 1: 
- <a id="T062-R06-C02"></a>列 2: MatMul
- <a id="T062-R06-C03"></a>列 3: 65,536
- <a id="T062-R06-C04"></a>列 4: 65,536
- <a id="T062-R06-C05"></a>列 5: 

<a id="T062-R07"></a>
**T062-R07**

- <a id="T062-R07-C01"></a>列 1: 
- <a id="T062-R07-C02"></a>列 2: all NN MAC layers
- <a id="T062-R07-C03"></a>列 3: 90,112
- <a id="T062-R07-C04"></a>列 4: 91,712
- <a id="T062-R07-C05"></a>列 5: 26,176

<a id="T062-R08"></a>
**T062-R08**

- <a id="T062-R08-C01"></a>列 1: 
- <a id="T062-R08-C02"></a>列 2: parameters
- <a id="T062-R08-C03"></a>列 3: 24,976
- <a id="T062-R08-C04"></a>列 4: 24,978
- <a id="T062-R08-C05"></a>列 5: 22,928

<a id="T062-R09"></a>
**T062-R09**

- <a id="T062-R09-C01"></a>列 1: decoder
- <a id="T062-R09-C02"></a>列 2: Conv
- <a id="T062-R09-C03"></a>列 3: 209,672,448
- <a id="T062-R09-C04"></a>列 4: 210,335,480
- <a id="T062-R09-C05"></a>列 5: 

<a id="T062-R10"></a>
**T062-R10**

- <a id="T062-R10-C01"></a>列 1: 
- <a id="T062-R10-C02"></a>列 2: ConvTranspose
- <a id="T062-R10-C03"></a>列 3: 34,504,704
- <a id="T062-R10-C04"></a>列 4: 85,765,504
- <a id="T062-R10-C05"></a>列 5: 

<a id="T062-R11"></a>
**T062-R11**

- <a id="T062-R11-C01"></a>列 1: 
- <a id="T062-R11-C02"></a>列 2: all NN MAC layers
- <a id="T062-R11-C03"></a>列 3: 244,177,152
- <a id="T062-R11-C04"></a>列 4: 296,100,984
- <a id="T062-R11-C05"></a>列 5: 244,950,136

<a id="T062-R12"></a>
**T062-R12**

- <a id="T062-R12-C01"></a>列 1: 
- <a id="T062-R12-C02"></a>列 2: parameters
- <a id="T062-R12-C03"></a>列 3: 5,287,489
- <a id="T062-R12-C04"></a>列 4: 5,287,489
- <a id="T062-R12-C05"></a>列 5: 5,283,617

<a id="P064"></a>

Observations:

<a id="P065"></a>

-    Parameter counts agree within 8.2% across all three tools, and within 0.2% except for the quantizer. The proposed tool reports identical parameter counts to onnx-tool for the encoder and decoder and differs by only 0.01% for the quantizer..

<a id="P066"></a>

-    For Conv  onnx-tool and ptflops count one additional MAC per output element for the bias addition. The Conv MAC of the encoder are otherwise identical.

<a id="P067"></a>

-    For ConvTranspose the two ONNX-based tools differ by the upsampling stride: onnx-tool multiplies by the output spatial volume, which overstates transposed convolutions by their stride. ptflops agrees with the proposed tool within the bias term, which confirms the input-volume formula used here.

<a id="P068"></a>

-    ptflops does not see the codebook distance search of the quantizer, which is a functional MatMul outside any module; ONNX-based tools count it. This is a general limitation of module-hook-based tools and one reason to count on the exported graph.

<a id="P069"></a>

Table 7: Assumed (example) cost per output element of element-wise operators, this tool versus onnx-tool

<a id="T070"></a>

<a id="T070-R01"></a>
**T070-R01**

- <a id="T070-R01-C01"></a>列 1: Operator
- <a id="T070-R01-C02"></a>列 2: Proposed tool (FLOPs per element)
- <a id="T070-R01-C03"></a>列 3: onnx-tool ("MACs" per element)

<a id="T070-R02"></a>
**T070-R02**

- <a id="T070-R02-C01"></a>列 1: Mul
- <a id="T070-R02-C02"></a>列 2: 1
- <a id="T070-R02-C03"></a>列 3: 1

<a id="T070-R03"></a>
**T070-R03**

- <a id="T070-R03-C01"></a>列 1: Add
- <a id="T070-R03-C02"></a>列 2: 1
- <a id="T070-R03-C03"></a>列 3: 1

<a id="T070-R04"></a>
**T070-R04**

- <a id="T070-R04-C01"></a>列 1: Reciprocal
- <a id="T070-R04-C02"></a>列 2: 1
- <a id="T070-R04-C03"></a>列 3: 4

<a id="T070-R05"></a>
**T070-R05**

- <a id="T070-R05-C01"></a>列 1: Pow
- <a id="T070-R05-C02"></a>列 2: 1
- <a id="T070-R05-C03"></a>列 3: 32

<a id="T070-R06"></a>
**T070-R06**

- <a id="T070-R06-C01"></a>列 1: Sin
- <a id="T070-R06-C02"></a>列 2: 12
- <a id="T070-R06-C03"></a>列 3: 39

<a id="T070-R07"></a>
**T070-R07**

- <a id="T070-R07-C01"></a>列 1: Tanh
- <a id="T070-R07-C02"></a>列 2: 13
- <a id="T070-R07-C03"></a>列 3: 76

<a id="P072"></a>

For transcendental functions, the element-wise cost tables of the two ONNX-based tools differ significantly, and onnx-tool reports these costs as MAC. Consequently, the two tools report totals differing by more than 30 % for the same graph, even though their NN MAC layer counts and parameter counts agree.

<a id="P073"></a>

Totals from different tools are therefore not comparable unless the per-operator's cost convention is agreed. These supports reporting the MACs of the NN MAC layers and the parameter count as the primary figures and fixing the convention for the remaining operators in ULBC-4.

<a id="P074"></a>

## 5    Proposal

<a id="P075"></a>

It is proposed that the complexity and memory figures of the ML components of a ULBC candidate are derived from the submitted ONNX models by a common graph-level profiling tool, with static shapes, given batch size and the duration of the input tensor, so that the figures are reproducible and verifiable from the deliverable itself.

<a id="P076"></a>

It is proposed that the profile reports, per ML component: MAC/s, FLOP/s, the number of nodes and FLOPs per operator category (NN MAC, vector ALU, activation, data reorganization), the parameter count, the ROM in bytes per stored data type, and the peak and average activation working set of one inference, and that any weighting per category or per precision is applied to this profile once agreed in ULBC-4.

<a id="P077"></a>

This proposal does not contain any rule regarding the complexity counting of ULBC itself, it rather proposes only a tool for evaluating the complexity ML components. The tool can be adapted to any needs.

<a id="P078"></a>

The source invites feedback on the set of reported figures, on the required operator coverage and on the counting rules and will consider making the tool available to SA4 for the qualification and selection phase depending on this feedback.

<a id="P079"></a>

References

<a id="P080"></a>

[1]     SP-260696: "New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite (ULBC-MED)".

<a id="P081"></a>

[2]     3GPP TR 26.940: "Study on Ultra Low Bit rate Speech Codecs".

<a id="P082"></a>

[3]    S4-261847: "[ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.1", Fraunhofer IIS (Interim ULBC-4 Editor), SA4#137-e.

<a id="P083"></a>

[4]    S4-260831: "Proposals for ULBC Codec Complexity Measurement", Cadence Design Systems Inc., SA4#135-bis-e.

<a id="P084"></a>

[5]     S4-261193: "[FS_ULBC] ULBC Complexity proposal based on SoundStream AI codec", Cadence Design Systems Inc., SA4#136.

<a id="P085"></a>

[6]     S4-260233: "On reference code and model format", Fraunhofer IIS, Apple Inc., SA4#135.

<a id="P086"></a>

[7]    S4-261140: "Selection deliverables", Fraunhofer IIS, SA4#136.

<a id="P087"></a>

[8]    S4-261546: "[ULBC-MED] On ULBC design constraints", Fraunhofer IIS, SA4#137-e.

<a id="P088"></a>

[9]    S4-261569: "[ULBC-MED] On model sizes for ULBC", Fraunhofer IIS, SA4#137-e.

<a id="P089"></a>

[10]    S4-261514: "[ULBC-MED] Considerations on complexity and memory constraints for ULBC", Samsung Electronics, SA4#137-e.

<a id="P090"></a>

[11]    S4-261516: "[ULBC-MED] Spreadtrum views on ULBC complexity", Spreadtrum, SA4#137-e.

<a id="P091"></a>

[12]    S4-261559: "[ULBC-MED] The generic Complexity metric for ULBC Selection", Huawei Technologies, SA4#137-e.

<a id="P092"></a>

[13]    S4-261555: "[ULBC-MED] Complexity and memory constraints for ULBC", Huawei Technologies, SA4#137-e.

<a id="P093"></a>

[14]    S4-260165: "[FS_ULBC] On ULBC complexity and RTF analysis", Dolby Laboratories Inc., Novamint, Nokia, SA4#135.

<a id="P094"></a>

[15]    S4-261011: "[FS_ULBC] Discussion and proposal on the reference C code generation methodology for AI-based ULBC", vivo, SA4#136.

<a id="P095"></a>

[16]    S4-261627: "On ULBC complexity requirements", Nokia, SA4#137-e.

<a id="P096"></a>

[17]    R. Kumar, P. Seetharaman, A. Luebs, I. Kumar, K. Kumar: "High-Fidelity Audio Compression with Improved RVQGAN", NeurIPS 2023.

<a id="P097"></a>

[18]    ONNX: Open Neural Network Exchange, https://onnx.ai, operator set version 17.

<a id="P098"></a>

[19]    ptflops: FLOPs counter for convolutional networks in PyTorch, https://pypi.org/project/ptflops/.

<a id="P099"></a>

[20]    onnx-tool: A parser, editor and profiler tool for ONNX models, https://github.com/ThanatosShinji/onnx-tool.
