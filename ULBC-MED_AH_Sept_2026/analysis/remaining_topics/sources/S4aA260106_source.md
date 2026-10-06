# S4aA260106 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260106 [ULBC-MED] Training data and regeneration deliverables.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260106

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Training data and model regeneration deliverables for the selected candidate

<a id="P005"></a>

Spec:    ULBC-6

<a id="P006"></a>

Agenda item:    4.6

<a id="P007"></a>

Document for:    Agreement

<a id="P010"></a>

## 1.    Introduction

<a id="P011"></a>

For every previous 3GPP speech codec, the information required to maintain the specification is fully contained in the specification and its deliverables (reference software, test vectors). For an AI-based codec whose trained model parameters are normative, this no longer holds automatically: future maintenance or evolution of the specification may require investigation, modification or regeneration of the standardized model. Operators deploy voice services for decades and rely on 3GPP, not on any single company, to maintain what they deploy — a point which was not contested at TSG SA#113.

<a id="P012"></a>

This contribution proposes to close the gap where it naturally belongs: in ULBC-6 (Deliverables), as obligations of the selected candidate only. During qualification and selection, no proponent is required to disclose proprietary training material; the obligations attach at the point where a candidate becomes the 3GPP codec. ULBC-6 is targeted for SA4#138, so this proposal has no schedule impact.

<a id="P013"></a>

## 2.    Discussion

<a id="P014"></a>

## 2.1    Regeneration needs more than the data

<a id="P015"></a>

It was correctly observed at SA4#137-e that access to training data is not sufficient to replicate training. Regenerating a trained model requires, in addition to the exact data version: the preprocessing and augmentation steps; the training code or an equivalent description with hyperparameters; the software framework and relevant environment information; the quantization/export steps; and an agreed tolerance defining what counts as a successful regeneration, since bit-exact reproduction of training is generally not achievable.

<a id="P016"></a>

This is established practice in JVET: candidates for adoption to the NNVC exploration are required to undergo training cross-check by a party other than the proponent, training scripts (including the model quantizing algorithm) must be made available, and re-training results are reported against a tolerance. The joint call beyond VVC extends the same discipline to an open competition.

<a id="P017"></a>

## 2.2    Interoperability is preserved

<a id="P018"></a>

A regenerated model is a new version; deployed decoders continue to use the reference weights, which remain the conformance target. The deliverables proposed here provide 3GPP with the capability to investigate and regenerate the model for maintenance and future evolution of the specification. They do not enable or imply any in-service change of standardized weights.

<a id="P019"></a>

## 2.3    Availability options, including escrow

<a id="P020"></a>

Availability of the training material for maintenance purposes can be satisfied in several ways, in increasing order of protection of proprietary material:

<a id="P021"></a>

Public material: identification by dataset name, release/version and checksums. 3GPP does not host or redistribute the material; each party obtains it from the public source under its terms.

<a id="P022"></a>

Escrow of proprietary material: deposit of the training material and training process with a neutral custodian, under confidentiality and access conditions agreed by SA4, with use limited to maintenance of the specification. Escrow secures access by contract rather than by 3GPP custody, and therefore places no hosting burden or data-controller role on 3GPP or the Organizational Partners.

<a id="P023"></a>

Documented alternative material: where neither of the above is possible for part of the material, identification of equivalent alternative material available for maintenance re-training, following the approach of the JVET joint call (re-training conducted using alternative material available to the body).

<a id="P024"></a>

Which option applies to which part of the selected candidate’s training material can be recorded in the deliverables at selection. Legal conditions applicable to the material itself (licensing, privacy) follow the PCG outcome and are not defined here.

<a id="P025"></a>

## 3.    Proposed text for ULBC-6

<a id="P026"></a>

It is proposed to include the following deliverables of the selected candidate in ULBC-6, in addition to the specification text, reference software and conformance deliverables:

<a id="P027"></a>

y.1 Training data description: an identification and description of all training data used to produce the standardized model, including dataset names, versions/releases, composition summary, and a manifest with integrity checksums where applicable.

<a id="P028"></a>

y.2 Training process description: training scripts or an equivalent description sufficient to regenerate a functionally equivalent model, including preprocessing and data-augmentation steps, hyperparameters, relevant software framework and environment information, and quantization/export steps.

<a id="P029"></a>

y.3 Availability for maintenance: each part of the training data shall be (a) publicly identified per clause y.1 such that it can be independently obtained, or (b) deposited with a neutral custodian under escrow and access conditions agreed by SA4, or (c) where neither (a) nor (b) is possible, complemented by identification of equivalent alternative material available for maintenance re-training, subject to SA4 agreement on the equivalence of such material.

<a id="P030"></a>

y.4 Regeneration tolerance: the criteria under which a regenerated model is considered functionally equivalent to the standardized model are [TBD by SA4].

<a id="P031"></a>

## 4.    Proposal

<a id="P032"></a>

It is proposed to agree the inclusion of clauses y.1–y.4 in ULBC-6 at this ad hoc meeting or at the latest at SA4#138, applicable to the selected candidate only.
