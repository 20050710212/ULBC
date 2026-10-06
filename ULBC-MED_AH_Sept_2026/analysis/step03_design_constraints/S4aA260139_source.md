# S4aA260139 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260139 On ULBC model size limit.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWB Ad Hoc Meeting on ULBC-MED    S4aA260139

<a id="P001"></a>

28-30 September 2026, Shanghai, China

<a id="P003"></a>

Source:    Nokia

<a id="P004"></a>

Title:    Proposal on ULBC model size

<a id="P005"></a>

Agenda item:    4.4 - Design constraints (ULBC-MED)

<a id="P006"></a>

Document for:    DISCUSSION and AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

ULBC-MED WID was approved in June. As already concluded during the FS_ULBC study, it is the common understanding that a potential ULBC solution will need to be AI-based.

<a id="P012"></a>

Implementation cost for ULBC is an important consideration. The codec should be deployable on a broad range of devices at different price points, which suggests reasonably strict limits on memory footprint may be necessary. On the other hand, sufficient communications quality, e.g., meeting AMR-WB 12.65 quality, and robustness to varied speech signals (languages) and other relevant signals, including capability to reproduce consistent backgrounds, e.g., in emergency call use cases are important.

<a id="P014"></a>

The source proposes limits on ULBC model size in this document.

<a id="P016"></a>

## 2. Discussion

<a id="P017"></a>

Focus of experiments discussed in connection with proposed ULBC Performance Requirements (e.g., comparison against AMR-WB 12.65 kbps as per WID) and Design Constraints (computational complexity and memory footprint/mode size) has so far been mostly on clean speech and clean channel quality.

<a id="P019"></a>

In view of the source, based on our internal experimentation with various AI-based solutions, acceptable noisy speech performance under packet loss is more difficult to achieve at low complexity and memory footprint than corresponding clean speech/clean channel performance. For example, model robustness against background noise can benefit from additional model size. PLC operations can benefit from additional computations as well as model size.

<a id="P021"></a>

To make sure these required capabilities are properly accounted for, the source proposes to slightly relax the maximum thresholds associated with the memory footprint/model size and computational complexity.

<a id="P023"></a>

In the next section, a proposal is made regarding maximum allowed model size.

<a id="P025"></a>

To encourage memory footprint/model size and computational complexity optimizations, the source proposes to furthermore consider inclusion of at least one Figure of Merit (FoM) (at least in Selection Phase) that favours smaller and less complex ULBC candidate solutions, e.g., according to discussion in [1]. However, at same time, slightly more relaxed design constraints ensure that high-quality operations will be possible. The exact FoMs are TBD.

<a id="P027"></a>

## 3. Proposal

<a id="P028"></a>

The source proposes to agree on the following for ULBC:

<a id="T030"></a>

<a id="T030-R01"></a>
**T030-R01**

- <a id="T030-R01-C01"></a>列 1: Parameter
- <a id="T030-R01-C02"></a>列 2: Design constraint
- <a id="T030-R01-C03"></a>列 3: Note

<a id="T030-R02"></a>
**T030-R02**

- <a id="T030-R02-C01"></a>列 1: Memory
- <a id="T030-R02-C02"></a>列 2: The memory footprint shall ensure implementability on standard 3GPP UE platforms.<br><br>ULBC candidate codecs shall have the maximum model size of 7.5M parameters (ROM).
- <a id="T030-R02-C03"></a>列 3: Agreed WID objective [2].<br><br>Editor's note: Model size to be reported as a tuple (number of parameters, size in bytes).<br><br>Editor’s note: The memory constraint is defined for a ULBC candidate codec supporting two (2) bitrates in a single codec such that the maximum model size includes all model parameters to support both bitrates, irrespective of whether such parameters are shared between the bitrates.

<a id="P033"></a>

References

<a id="P034"></a>

[1]    S4aA260135, “Selection rules for ULBC qualification phase”, Nokia
