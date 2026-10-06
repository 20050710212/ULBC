# S4aA260154 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260154_ULBC_MED_On_ULBC_model_size.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG Ad-hoc on ULBC-MED    S4aA260154

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Qualcomm Incorporated

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC model size

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P011"></a>

The ULBC Design Constraints Permanent document (ULBC-4) [1] documents various proposals on computational complexity and memory design constraints. In this contribution we focus on model size and memory constraints. In this regard, there are differing proposals on whether model size should be specified per model/bitrate or just as a total for both operating points. The following are some (non-exhaustive) relevant examples from ULBC-4 [1]:

<a id="P012"></a>

“one combined complexity budget and one combined parater[sic] budget for both operating points”.

<a id="P013"></a>

“RAM 6M parameters for one active mode; ROM 24 Mbytes across all modes at 2 bytes per parameter (1580)”

<a id="P015"></a>

The source believes it is important to clarify this aspect and have corresponding language in ULBC-4.

<a id="P017"></a>

## 2. Discussion

<a id="P019"></a>

ROM for model parameters should include the total model parameter count (and/or bytes) for all ULBC modes. This is justified since the storage space required for deploying ULBC on a device must include the entirety of the ULBC codec.

<a id="P020"></a>

RAM for model parameters, however, should only include the model(s) that is(are) being actively used/accessed at any given time, during runtime operation of the codec. This only includes the models needed for one of the two bitrates of ULBC, since only one bit rate can be active at a given point in time. The active bitrate parameters can be loaded into memory and used while that bitrate is active, then unloaded when the other bitrate is invoked, and the other bitrate’s model parameters loaded into RAM memory. Therefore, it is justified to have a per-bit rate RAM model parameter count constraint, to account only for the necessary RAM usage during runtime.

<a id="P022"></a>

## 3. Proposal.

<a id="P024"></a>

We propose the following change to the ULBC Design Constraints permanent document:

<a id="T025"></a>

<a id="T025-R01"></a>
**T025-R01**

- <a id="T025-R01-C01"></a>列 1: Computational complexity and memory<br>Editor's note: suggested to split up
- <a id="T025-R01-C02"></a>列 2: Memory constraints:<br>ROM for NN model parameters <= [X] MB<br>ROM for NN model parameters includes NN model parameters for entirety of ULBC (both bitrates)<br>RAM for NN model parameters <= [Y] #params<br>RAM usage only includes one bitrate’s NN model parameters (the active bitrate’s NN model parameters)<br>The computational complexity and memory footprint shall ensure implementability on standard 3GPP UE platforms. <br>[Specifics FFS]<br>[Computational complexity and memory footprint includes:<br>- sampling rate conversion (1518)<br><br>Positions:<br>- MAC/s primary; approximately 1 GMAC/s; approximately 5M parameters; one combined complexity budget and one combined parater budget for both operating points acounted against the design constraints; complexity additionally as a Figure of Merit (1512, 1514)<br>- GMACs/s rather than parameter count; 2 GMAC/s; A78 at 2.0–2.3 GHz or A76 at 2.2 GHz as baseline core (1516)<br>- C with ML components via an ONNX runtime, no custom operators; inference engine excluded from the count; ROM and RAM counted separately; host lab verifies. Counting method revised by the source (1546)<br>- Model size < 6M parameters and complexity < 1.2 GFLOPS or 600 MMACS; mixed precision not recommended at qualification and selection (1555)<br>- FLOPs primary, parameter count auxiliary; WMOPS, operator count and memory access excluded as hardware-dependent (1559)<br>- RAM constraint of 6M parameters, supported by a listening test across four model sizes at 1.0 kbit/s (1569)<br>- RAM 6M parameters for one active mode; ROM 24 Mbytes across all modes at 2 bytes per parameter (1580)<br>- ≤ 2 GMACs/s; model size plus state memory ≤ 12.5 Mbytes; compute excluding quantization, model size including it; real-time operation on efficiency cores (1586)<br>- P9: ≤ 2.5 GMACs/s using the TR 26.940 clause 6.4.2 convention. P10: report parameter count and model size in bytes (1621)<br>- Definitional clarification required before numerical constraints (1627)<br>- TBD pending clarification on complexity counting (1640)<br>]
- <a id="T025-R01-C03"></a>列 3: Agreed WID objective [2].<br>Editor's note: The complexity metric and the numeric limits are FFS. <br>TR 26.940 clause 6.2 (among other clauses contains an extensive discussion on complexity/memory design constraints, e.g.:<br>Complexity should be defined from AI-oriented measures (MMAC/s, model size in bytes, parameter precision, TOPS/W), not as a multiple of legacy-codec operations; model size should be reported as a tuple (number of parameters, size in bytes).<br>Editor’s note: How the complexity and memory constraints are defined for a ULBC candidate codec supporting two (2) bitrates in a single codec are to be clarified and constraints documented accordingly.

<a id="P028"></a>

## 4. References

<a id="P030"></a>

[1] 3GPP S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4)", v0.2.1, SA4#137-e, August 2026
