# S4aA260107 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260107 [ULBC-MED] Training data way forward.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260107

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Way forward on ULBC training data

<a id="P005"></a>

Agenda item:    4.2

<a id="P006"></a>

Document for:    Agreement

<a id="P008"></a>

## 1.     Introduction

<a id="P009"></a>

At TSG SA#112, TSG SA requested the SA4 Chair to allocate time to discuss whether technical training-dataset requirements are needed for ULBC candidate codecs and to report progress to future TSG meetings. This request remains in effect.

<a id="P010"></a>

At SA4#137-e, the Chair’s survey (S4-261674, reported in SP-260909) found no consensus on the overall need for technical training-dataset requirements. It did, however, identify broad agreement on specific elements: 20 of 24 responding companies supported an explicit requirement that qualification, selection and characterization material shall not be used for training, and 18 companies supported a proponent declaration mechanism.

<a id="P011"></a>

At TSG SA#113 (Madrid, 15–18 September 2026), the SA4 Chair report (SP-260909) and the related discussion papers (SP-260912, SP-260919) were noted, and no liaison to SA4 was agreed. The SA4 Chair was instead asked to inform SA4 of the PCG discussions directly. PCG will further review the legal aspects of AI training datasets in October 2026, with updated information expected at TSG SA#114 in December 2026. The plenary discussion also recorded that the work in SA4 should not be stopped while this issue is discussed and should aim to meet the schedule of the work item.

<a id="P012"></a>

At the PCG#56bis ad hoc (3 September 2026), no conclusion was reached between a common and a proprietary training-dataset approach; an ad hoc group on the legal aspects was created (ETSI-led), and the summary recorded that there are legal requirements applicable to all scenarios and that there is no consensus on the way forward for either a common training dataset or use of proprietary datasets.

<a id="P013"></a>

Consequently, the legal aspects of training data are progressing in PCG on their own track, while the technical aspects remain with SA4 under the standing TSG SA#112 request. Whilst this document addresses the technical aspects, the dependency on PCG legal guidance is also discussed, with a proposed way forward to avoid binding submission-procedure decisions that PCG may invalidate later.

<a id="P014"></a>

## 2.    Discussion

<a id="P015"></a>

## 2.1    What problem each technical related instrument solves

<a id="P016"></a>

A concern recorded in the SA4 and TSG SA discussions is that it is unclear what problem technical training-dataset requirements would solve. Samsung considers this a fair request for precision. The candidate instruments address distinct, identifiable problems, and each can be adopted independently of the others and independently of any legal decision:

<a id="P017"></a>

Separation of training data from test material controls leakage of test conditions into training and protects the validity of the qualification and selection comparison. (Broad support already recorded: 20 of 24.)

<a id="P018"></a>

Documentation and disclosure of training material controls opacity: it allows SA4 and implementers to understand what a submitted result rests on, and provides the evidence implementers increasingly require for products placed on regulated markets.

<a id="P019"></a>

Availability of training material and training process for the selected candidate controls long-term maintainability: it preserves the ability of 3GPP to investigate and, where needed, regenerate the standardized model independently of any single company.

<a id="P020"></a>

Performance requirement dimensions in ULBC-3 (languages/language families, talker demographics, acoustic environments) control robustness and bias at the outcome level, verified in testing, whatever training data was used.

<a id="P021"></a>

Common training material controls the data advantage itself, ensuring the comparison measures codec technology rather than historical access to speech corpora. PCG discussed this with no conclusion.

<a id="P022"></a>

## 2.2    Addressing the concerns raised

<a id="P023"></a>

The following concerns were recorded during the SA4#137-e and TSG SA#113 discussions and are addressed as follows:

<a id="P024"></a>

“Access to common training data is not sufficient to replicate training.” Agreed. Availability of the training material is a necessary but not sufficient condition for regeneration of a model. Regeneration additionally requires the training process description (scripts or equivalent, augmentation, hyperparameters, software environment, quantization steps) and an agreed tolerance for what counts as regenerated. This is why the training process is proposed as a deliverable of the selected candidate, rather than claiming that data alone suffices.

<a id="P025"></a>

“Retraining raises questions on maintaining interoperability.” Agreed. A retrained model is a new decoder version; deployed devices continue to use the reference weights. The proposals therefore concern the capability to investigate and regenerate the model for maintenance and future evolution of the specification, not any in-service change of standardized weights.

<a id="P026"></a>

“Timing and schedule impacts.” All proposed text and recommendations land in permanent documents already targeted for this ad hoc meeting or SA4#138 (ULBC-3, ULBC-5a/5b, ULBC-6, ULBC-8a/8b). No new milestone, document or process is created.

<a id="P027"></a>

“Legal aspects are outside SA4.” Agreed. Legal requirements (licensing, IP, privacy) are being developed by PCG, with a report expected at TSG SA#114. Nothing in this document defines legal requirements; the technical instruments above are valid under any PCG outcome. However, there is dependency between PCG guidance and its inclusion into the relevant permanent documents.

<a id="P028"></a>

## 2.3    Practice in other standardization bodies

<a id="P029"></a>

The proposed instruments follow practice already in force in comparable codec standardization:

<a id="P030"></a>

The JVET/MPEG Joint Call for Proposals on video compression beyond VVC (July 2026) requires that no part of the test sequences be used as a training set, makes it mandatory to report which material was used to train each part of the algorithm, and expects training material to be made available for further investigation and verification, or re-training to be conducted using alternative material available to JVET. Training scripts may form part of the submitted technology.

<a id="P031"></a>

JPEG AI (ITU-T T.840.1 | ISO/IEC 6048-1), the first published learned image-coding standard with normative trained parameters, mandated a common training dataset for the compared results and permitted additional data only where described in detail, licensed, and submitted with the proposal.

<a id="P032"></a>

The IETF neural speech-codec work (mlcodec) normatively bars training on its test clips.

<a id="P033"></a>

These working precedents demonstrate that the technical instruments are implementable within a candidate-based codec selection. Legal and liability governance of training corpora has not been taken on by any of these bodies and remains, for 3GPP, with PCG.

<a id="P034"></a>

## 2.4    A working definition of transparency

<a id="P035"></a>

Irrespective of whether common or proprietary, the term “transparency” has been used with different meanings in the dataset discussion so far. To avoid it being understood as publication of proprietary data or as 3GPP custody of a corpus, Samsung proposes the following working definition for ULBC purposes: transparency of training data means (a) documentation of the training material and its use (i.e. identification of the datasets, versions/releases and the manner of their use, not provision of the material itself), provided with the candidate submission, and (b) for the selected candidate, availability of the training material and training process for the purpose of maintenance of the specification, under conditions agreed by SA4 (including public reference, or deposit/escrow arrangements for proprietary material). Transparency does not require publication of proprietary datasets and does not require 3GPP to own or host any data.

<a id="P036"></a>

## 2.5    Placement of technical instruments discussed in the existing permanent documents

<a id="P037"></a>

Separation from test material: ULBC-5a/5b (qualification/selection rules) and ULBC-8a/8b (test plans).

<a id="P038"></a>

Robustness requirement dimensions: ULBC-3 (performance requirements) – languages/language families, talker demographics, acoustic environments, verified in testing.

<a id="P039"></a>

Training-data documentation and regeneration deliverables of the selected candidate: ULBC-6 (deliverables).

<a id="P040"></a>

## 2.6    No binding submission-procedure decisions before PCG guidance

<a id="P041"></a>

Regarding the legal aspects of training data, SA4 can expect guidance from PCG no earlier than the conclusion of PCG#57 in October 2026, with a report to TSG SA#114 in December 2026. According to the discussions during the PCG#56bis ad hoc, it can be expected that PCG guidance to SA4 contains 1) legal requirements for training datasets used, and 2) process related guidance for potential requirement verification, dataset management, and maintenance issues. The dependency on this guidance in relation to the ongoing work in SA4 is discussed:

<a id="P042"></a>

Legal requirements for the training datasets should be included into ULBC-5a/5b. Further, legal requirements need to be available before candidate submission for qualification/selection such that proponents can do a first check for compliance before submission. Not knowing the legal requirements before submission creates material rework risk for all proponents, since proponents themselves cannot verify whether they satisfy the requirements. The PCG#56bis summary further records that there are legal requirements applicable to all scenarios; a submission made before these requirements are known is therefore at risk under any PCG outcome, whether based on common or proprietary training data.

<a id="P043"></a>

Process related guidance should be reflected into ULBC-6. Such guidance may include topics such as dataset submission, management, verification against legal requirements, codec maintenance, and the corresponding responsible entities.

<a id="P045"></a>

This approach is consistent with the TSG SA#113 guidance that the work in SA4 should not be stopped: all technical instruments in clauses 2.1–2.5 proceed without any dependency on PCG, and only the incorporation of the legal requirements into the submission procedure awaits the guidance on which it, by definition, depends.

<a id="P046"></a>

## 3.    Proposals

<a id="P047"></a>

It is proposed that SA4:

<a id="P048"></a>

Proposal 1a: agree that the legal requirements from the forthcoming PCG guidance shall be incorporated into ULBC-5a/5b.

<a id="P049"></a>

Proposal 1b: agree that these legal requirements shall be available to proponents before candidate submission for qualification/selection, such that proponents can verify compliance before submitting.

<a id="P050"></a>

Proposal 2: reflect process related PCG guidance (such as dataset submission, management, verification against legal requirements, codec maintenance etc.) into ULBC-6.

<a id="P051"></a>

Proposal 3: agree the problem-to-instrument mapping in clause 2.1 as the framework for the further work on training-data technical aspects.

<a id="P052"></a>

Proposal 4: agree the separation of training data from test material and include corresponding text for ULBC-5a/5b and ULBC-8a/8b (S4aA260105).

<a id="P053"></a>

Proposal 5: agree that ULBC-6 includes training-data documentation and model-regeneration deliverables for the selected candidate (S4aA260106).

<a id="P054"></a>

Proposal 6: agree to develop robustness requirement dimensions (languages, talker demographics, acoustic environments) in ULBC-3, verified in qualification/selection testing.

<a id="P055"></a>

Proposal 7: note the working definition of transparency in clause 2.4, and confirm that legal aspects remain with PCG pending its report to TSG SA#114.

<a id="P056"></a>

## 4  References

<a id="P057"></a>

SP-260696, “New WID on Ultra Low Bitrate Speech Codec for Voice over GEO”, incl. TSG SA#112 guidance to SA4

<a id="P058"></a>

SP-260909, “SA WG4 Chair report on Training Data Requirements for ULBC Candidate Codecs” (noted at TSG SA#113)

<a id="P059"></a>

SP-260919, “Ensuring a deployable and maintainable ULBC codec” (noted at TSG SA#113; carries S4-261674 annex figures)

<a id="P060"></a>

SP-260907, “ULBC-MED Progress Report to TSG SA#113” (work plan and P-doc status)

<a id="P061"></a>

TSG SA#113 draft meeting report (disposition of agenda item 3.4)

<a id="P062"></a>

PCG#56bis draft meeting report (decision D-PCG56-Bis/01; SA Chair summary)

<a id="P063"></a>

JVET-AQ2021, “Joint Call for Proposals on Video Compression with Capability beyond VVC”

<a id="P064"></a>

JPEG AI Final Call for Proposals (wg1n100095); ITU-T T.840.1 | ISO/IEC 6048-1
