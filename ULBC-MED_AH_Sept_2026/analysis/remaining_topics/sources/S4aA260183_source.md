# S4aA260183 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260183.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260183 rev ofS4aA260105

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Separation of training data from test material

<a id="P005"></a>

Spec:    ULBC-5a/5b and ULBC-8a/8b

<a id="P006"></a>

Agenda item:    4.5

<a id="P007"></a>

Document for:    Agreement

<a id="P009"></a>

## 1.    Introduction

<a id="P010"></a>

In the SA4#137-e survey, 20 of 24 responding companies supported an explicit requirement that material used for qualification, selection and characterization testing shall not be used for training. This was the most widely supported element of the survey and the only one approaching unanimity.

<a id="P011"></a>

The same rule is standard practice elsewhere: the JVET/MPEG joint call beyond VVC states that no part of the test sequences shall be used as a training set; the IETF neural speech-codec work normatively bars training on its test clips; JPEG AI withholds its test set from proponents. The requirement is independent of any legal question, is verifiable within the existing testing process, and has no schedule impact.

<a id="P012"></a>

This contribution proposes concrete text for incorporation into ULBC-5a/5b (qualification and selection rules) and ULBC-8a/8b (test plans), all of which are targeted for this ad hoc meeting or SA4#138.

<a id="P013"></a>

## 2.    Discussion

<a id="P014"></a>

## 2.1    Scope of the separated material

<a id="P015"></a>

For a speech codec tested under the agreed conditions (input levels of −36/−26/−16 dBov; background noise types and SNRs for qualification), the material to be separated is not limited to speech. Test conditions are generated from speech material, background-noise recordings, and potentially impulse responses and channel/room material. Leakage through any of these components compromises the comparison equally. Publicly available corpora that combine speech and noise components (e.g. noise-suppression challenge datasets) present a particular overlap risk where similar material could appear on both the training and testing side.

<a id="P016"></a>

## 2.2    Level of separation

<a id="P017"></a>

Separation at the level of individual files is not sufficient: the same talker or the same source recording may appear in different files or processed variants. Separation should therefore apply at the level of talkers and source recordings/content. Validation data used during candidate development belongs to the training side.

<a id="P018"></a>

## 2.3    Mechanism

<a id="P019"></a>

Test material should be held by the test laboratories / host laboratory and not distributed to proponents beyond what the test plans require. Each candidate submission should include a declaration of compliance with the separation requirement. Since a trained model cannot be “untrained”, a breach cannot be remedied after the fact; a submission without the declaration, or found to be in breach, should be invalid for the corresponding phase.

<a id="P020"></a>

## 3.    Proposed text

<a id="P021"></a>

It is proposed to include the following text within brackets in ULBC-8a:

<a id="P022"></a>

x.1 Requirements on test laboratories – sourcing. Material used to generate test conditions for  selection testing — including speech material, background-noise recordings, for subjective evaluation — shall be material that is newly recorded or otherwise not publicly available, and that has not been published. Talkers used for newly recorded speech material should not, to the laboratory’s knowledge, be talkers whose recordings are contained in publicly available speech corpora.

<a id="P023"></a>

x.2 Requirements on test laboratories – written commitment. Each test laboratory shall provide, as part of its engagement for ULBC testing, a written commitment to SA4 confirming that the material it uses complies with clause x.1 and identifying the origin of each material component (newly recorded / non-public laboratory material).

<a id="P024"></a>

x.3 Requirements on test laboratories – non-disclosure. Test material shall not be disclosed to proponents before completion of the respective test phase.

<a id="P025"></a>

x.4 In-house testing. Where testing (e.g. characterization) is performed by proponents in-house, the material used is known to the proponent, and the proponent shall declare that such material was not used for training or development of the submitted candidate.

<a id="P030"></a>

## 4.    Proposal

<a id="P031"></a>

It is proposed to agree the text in clause 3 and to request the editors of ULBC-5a, ULBC-5b, ULBC-8a and ULBC-8b to incorporate it in the next versions of the respective permanent documents.
