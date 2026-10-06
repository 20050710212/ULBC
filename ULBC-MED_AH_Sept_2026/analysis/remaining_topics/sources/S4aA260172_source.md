# S4aA260172 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260172 ULBC maintenance.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWB Ad Hoc Meeting on ULBC-MED    S4aA260172

<a id="P001"></a>

28-30 September 2026, Shanghai, China    revision of S4aA260140

<a id="P003"></a>

Source:    Nokia

<a id="P004"></a>

Title:    On ULBC maintenance

<a id="P005"></a>

Agenda item:    4.10 – Other (ULBC-MED)

<a id="P006"></a>

Document for:    DISCUSSION and AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

ULBC-MED WID was approved in June. As already concluded during the FS_ULBC study, it is the common understanding that a potential ULBC solution will need to be AI-based. Therefore, ULBC is likely to utilize AI model training data, e.g., in the form of speech and other relevant audio signals.

<a id="P012"></a>

There has already been significant discussion relating to training datasets to be used for ULBC on various levels and fora, including technical and legal considerations, in SA4, SA, and PCG. During these discussions, some concerns about ULBC maintenance due to its AI-based nature have appeared.

<a id="P014"></a>

This input discusses ULBC maintenance, including views on whether any significant maintenance aspects directly concern training datasets. In view of the source, these concerns are premature. SA4 already has an effective maintenance process in place. The focus of the work should be on developing and selecting a high-quality standard fulfilling the WID objectives.

<a id="P017"></a>

## 2. ULBC maintenance considerations

<a id="P018"></a>

3GPP has a good track record of maintaining their specifications, including the SA4 voice codec specifications. For example, as recently as for the June SA Plenary, important fixes [1] were identified and approved for the AMR codec source code. AMR was originally standardized in 1999, and some time had already passed even since the previous correction. Examples like this highlight the successful process, SA4 expertise, and the long-term commitment of proponent companies in producing and maintaining high-quality codec specifications.

<a id="P020"></a>

Maintenance of the codecs helps to ensure correctness of implementations. The corrections can relate to general stability improvements (fix crashes, ensure no memory leaks, etc.) and in some cases fixing of algorithmic inconsistencies or issues that can have caused, e.g., specific input signals resulting in somehow distorted output.

<a id="P022"></a>

As with existing codecs, the target of maintenance for ULBC (and other future AI-based solutions) should be to maintain bit exactness and, when bit exactness is not possible, backwards compatibility. When bit exactness is lost, it may still be maintained for some test vectors or operating points, e.g., not associated with the operations relating to the correction. Bit exactness, on one hand, helps to ensure that the codec solution, and its quality, do not deviate from what was selected and characterized.

<a id="P024"></a>

While it may not be possible to rule out some larger updates, e.g., including retraining of an AI-based solution such as ULBC, as part of the specification maintenance, a first expectation can be that such changes will not be common. Retraining may typically be limited to, e.g., the decoder, with the model maintained for the encoder and bitstream. Moreover, updates of this nature are likely to be thoroughly discussed and well planned, including considerations pertaining to what the training dataset should cover (e.g., what kind of deficiency in original training dataset might have caused the need for retraining, typically backed up by evidence) and how the training procedure should be designed. Retraining of ULBC, or any future AI-based solution, is basically a guaranteed loss of bit exactness and, generally, loss of (correct) backwards compatibility. At least in some cases, retraining may, in practice, be equal with generation of a new codec. It should be discussed whether in such case it may rather be necessary to open a new work item to develop a codec addressing the identified deficiencies of the existing solutions.

<a id="P026"></a>

As ULBC-MED is still in its very early phases, it seems premature to speculate too much about maintenance. Rather the focus in SA4 should now remain on developing a high-quality standard according to the WID objectives. To this purpose, the source considers it important to invite the best industry insights and most innovative solutions in competitive development process. Naturally, this does not mean maintenance can be only an afterthought. However, we should avoid putting the cart before the horse.

<a id="P029"></a>

## 3. Summary

<a id="P030"></a>

This input provides discussion on ULBC maintenance expectations, partly in light of recent concerns on training dataset availability for maintenance. The targets of voice codec maintenance should remain bit exactness and backwards compatibility. Focusing on retraining of an AI-based solution seems to largely abandon these essential targets.

<a id="P032"></a>

Overall, it seems premature to speculate too much on maintenance at this stage of the work. The current focus of the work item should be to enable the development and selection of a high-quality standard fulfilling the WID objectives.

<a id="P034"></a>

The source asks SA4 to agree that:

<a id="P036"></a>

ULBC maintenance will have the target of backwards compatibility (e.g., bitstream interoperability) and preferably as small modification as possible within the conformance criteria.

<a id="P040"></a>

References

<a id="P041"></a>

[1]    S4-261199: Correction of homing frame handling, Nokia
