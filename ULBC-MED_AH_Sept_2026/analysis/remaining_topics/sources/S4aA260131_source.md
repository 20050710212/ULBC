# S4aA260131 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260131_Way_forward_ULBC.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:         Dolby Laboratories, Inc., Novamint, Verizon<br>
Title:         Interim handling of training dataset matters in the ULBC-MED technical work<br>
Agenda item:     4.10 (ULBC-MED)<br>
Document for:     Discussion and Agreement

<a id="P001"></a>

## 1  Introduction

<a id="P002"></a>

Disclaimer: The key requirement underlying this contribution is that the training dataset of the selected candidate is visible and inspectable at the end of the selection process, and that it remains available for inspection and for maintenance purposes thereafter. Until PCG has taken a decision, this is considered best business practice. The proposal made in this contribution may be adjusted subject to recommendations from PCG, for example should such a recommendation entail that the training dataset be made available at an earlier stage. The exact legal framework under which this could happen would, however, depend on the guidance ultimately issued.

<a id="P003"></a>

SA#112 requested SA4 to discuss training dataset requirements for AI-based ULBC codecs. SA4 considered this at SA4#137-e; PCG and Organizational Partners are currently examining legal dimensions. No further guidance has been issued. This contribution proposes a concrete compromise: proponents keep their development freedom; the winning proponent discloses its dataset after selection; a frozen reference is preserved for legal review and future ULBC specification maintenance; and an independent entity verifies the dataset produces the standardized model parameters before SA approval. This compromise proposal balances two legitimate interests: the proponents' interest in protecting non-licensable know-how in AI training dataset creation, curation and augmentation, and the implementers' interest in transparency of the training data actually used, without imposing a common training dataset on all candidates or requiring SA4 to define legal requirements.

<a id="P004"></a>

## 2  Framework

<a id="P005"></a>

1 · CANDIDATE DEVELOPMENT (proponent)<br>
2 · EVALUATION AND SELECTION (SA4)<br>
3 · POST-SELECTION OBLIGATIONS (winning proponent)<br>
4 · APPROVAL AND MAINTENANCE<br>
Candidate development<br>
Own datasets, curation and training procedure<br>
Submission and binding commitment<br>
Frozen codec · declarations · post-selection pledge<br>
SA4 technical evaluation<br>
Listening tests · common requirements and criteria<br>
SA4 selects winning candidate<br>
Unsuccessful proponents disclose nothing<br>
Winner discloses dataset and opens procedure<br>
Public reference or non-public data under suitable terms<br>
Frozen dataset reference<br>
Preserved via 3GPP / Organizational Partner<br>
Independent verification (NDA)<br>
Dataset + procedure reproduce model parameters<br>
Legal compliance verification<br>
Open to any party · outside SA4 scope<br>
SA approval of ULBC specification<br>
Subject to legal clearance by the competent bodies<br>
Maintenance / authorized retraining<br>
Uses the frozen reference; winner cooperates<br>
Figure 1 – ULBC-MED codec-selection lifecycle

<a id="P006"></a>

The framework has six linked elements (see Figure 1):

<a id="P007"></a>

(a) Development freedom.  Each proponent may use any datasets, curation and training procedures. No common dataset is imposed.

<a id="P008"></a>

(b) Post-selection disclosure.  Winner discloses the dataset by precise public reference or by making non-public material available under suitable terms.

<a id="P009"></a>

(c) Frozen reference.  Controlled copy preserved via 3GPP or Organizational Partner mechanism. Liability stays with the proponent.

<a id="P010"></a>

(d) Legal compliance verification.  Frozen dataset made available to any party wishing to verify compliance with the legal dataset requirements specified by SA, PCG and/or the Organizational Partners. SA4 does not define or assess legal requirements.

<a id="P011"></a>

(e) Independent verification.  Trusted entity verifies under NDA that dataset + procedure reproduce the standardized model parameters, per SA4-defined reproducibility criteria.

<a id="P012"></a>

(f) Maintenance.  Frozen dataset available for authorized future maintenance; winner provides required cooperation.

<a id="P013"></a>

NOTE: Characterization activities, including end-to-end performance evaluations, should typically be conducted only after codec selection and ratification of that selection by SA. Since ULBC codec selection is expected late in Rel-20, these post-selection activities would therefore very likely take place in the Rel-21 timeframe.

<a id="P014"></a>

Proposal 1: SA4 should agree this post-selection disclosure, frozen-reference, independent-verification and maintenance framework, subject to future legal guidance from PCG.

<a id="P015"></a>

## 3  Rationale

<a id="P016"></a>

Proponents<br>
Choose own training datasets<br>
Responsible for legal compliance<br>
Winner discloses dataset, opens procedure<br>
SA4 — technical scope only<br>
Technical requirements and test conditions<br>
Candidate evaluation and codec selection<br>
Reproducibility criteria for verification<br>
Independent trusted entity<br>
Verifies dataset + procedure reproduce model<br>
Works under NDA; know-how stays protected<br>
SA / PCG / Organizational Partners<br>
Specify the legal dataset requirements<br>
No dataset access; no per-dataset assessment<br>
External verifying parties<br>
Any party may check the frozen dataset against those requirements<br>
submission<br>
dataset + procedure, NDA<br>
legal requirements<br>
frozen dataset<br>
Proponents<br>
SA4<br>
Trusted entity<br>
External verifiers<br>
SA / PCG / OP

<a id="P017"></a>

Figure 2 – Responsibility boundaries

<a id="P018"></a>

## 3.1  SA4 scope (see Figure 2)

<a id="P019"></a>

SA4 covers technical specification, evaluation and selection. The evaluation campaign as part of the selection shall be designed to exclude candidates suffering from technical deficiencies such as language dependency or other kind of bias. Ensuring that candidates generalise across languages and other sources of variability is therefore a matter of proper ULBC selection test design rather than of training dataset regulation: the test conditions shall expose the candidate codecs to a representative range of languages and language variations, talker variations (including gender, age and speaking style), and variations of the input signal characteristics, e.g. different microphone and filter characteristics, recording levels, and background noise types and levels. This is in line with established 3GPP SA4 practice in the design of speech codec selection tests, where candidates have consistently been evaluated over multiple languages, talkers and input conditions. Candidates that perform adequately only for a subset of these conditions are thereby identified and excluded through the selection tests themselves. PCG and the Organizational Partners specify the legal dataset requirements.

<a id="P020"></a>

Proposal 2: SA4 specifies and, through proper selection test design, addresses technical requirements, including coverage of language, talker and input-condition variations in the selection test conditions. SA4 also addresses the technical parts of post-selection verification and maintenance. SA4 does not define legal dataset requirements while the PCG evaluation is ongoing.

<a id="P021"></a>

## 3.2  No common dataset required

<a id="P022"></a>

No evidence supports a common-dataset mandate. Performance depends on architecture, curation, augmentation and AI system training know-how, not dataset alone. Fairness is achieved through common test conditions. A mandated dataset would constrain innovation and add legal cost without resolving legal questions.

<a id="P023"></a>

Proposal 3: SA4 should not require a common training dataset for ULBC candidate development.

<a id="P024"></a>

## 3.3  Proponent responsibility

<a id="P025"></a>

Each proponent is responsible for its own data choices and training procedure. Submissions must include a declaration of eligibility, conformance, and commitment to fulfil the post-selection obligations in clause 2.

<a id="P026"></a>

Proposal 4: SA4 shall require each proponent to commit at submission that, if selected, it will fulfil the post-selection dataset disclosure, independent verification and maintenance obligations in clause 2.

<a id="P027"></a>

## 3.4  Training / test data separation

<a id="P028"></a>

Hidden selection test material must not be used for training, fine-tuning or parameter optimization. Proportionate safeguards (undisclosed recordings, duplicate checks, controlled distribution) shall be defined in the test procedures.

<a id="P029"></a>

Proposal 5: The ULBC selection and test procedures shall define strict technical separation between candidate-development data and hidden selection test material, with appropriate declarations and controlled handling.

<a id="P030"></a>

## 3.5  Submission information requirements

<a id="P031"></a>

Submissions need only the information required to identify, execute and verify the frozen candidate: versions, checksums, parameters, runtime dependencies and operating instructions. Training datasets are not required at submission stage and are disclosed only by the winning proponent after selection. Each submission shall also include a declaration of eligibility, conformance and commitment to fulfil the post-selection obligations in clause 2.

<a id="P032"></a>

Proposal 6: Candidate submissions shall provide the technical information needed to identify, execute and verify the frozen candidate. Training datasets are disclosed only by the winning proponent after selection, per clause 2.

<a id="P033"></a>

## 3.6  Independence from pending legal work

<a id="P034"></a>

Technical ULBC-MED work not dependent on legal outcomes proceeds without delay. SA4 may add a neutral reservation indicating that later legal guidance may affect the final work item outcome. SA4 should not define speculative legal procedures or commit prematurely to dataset-hosting mechanisms.

<a id="P035"></a>

Proposal 7: SA4 shall continue all ULBC-MED technical work independent of the PCG legal evaluation, incorporating the post-selection obligations into the candidate selection framework, explicitly subject to later legal requirements from the competent bodies.

<a id="P036"></a>

## 4  Framework

<a id="P037"></a>

The Audio SWG is suggested to agree the following framework:

<a id="P038"></a>

No common training dataset is required for ULBC candidate development.

<a id="P039"></a>

Each proponent may use its own public, proprietary, generated or synthetic training material and procedures, subject to its responsibility for applicable legal, contractual and licensing obligations.

<a id="P040"></a>

Each candidate submission shall include a binding commitment that, if selected, the proponent will disclose the training dataset (by precise public reference or by making non-public material available under suitable terms).

<a id="P041"></a>

The winning proponent shall open its training procedure for verification by a trusted independent entity under NDA.

<a id="P042"></a>

After selection, the disclosed dataset shall be frozen through a mechanism designated by 3GPP or an Organizational Partner; responsibility and liability remain with the winning proponent.

<a id="P043"></a>

The frozen dataset shall be available to any party for assessment of compliance with the legal dataset requirements set by PCG; SA4 shall not define or perform legal assessment.

<a id="P044"></a>

Before SA approval, a trusted independent entity shall verify under NDA that the disclosed dataset and training procedure produce the standardized ULBC model parameters, per SA4-defined reproducibility criteria.

<a id="P045"></a>

The winning proponent provides cooperation for independent verification without publicly disclosing protected know-how.

<a id="P046"></a>

The frozen dataset may be used for maintenance or authorized retraining if SA4 decides this is necessary.

<a id="P047"></a>

Candidate codecs shall be frozen and self-contained and shall not access training data or unapproved external services during test execution.

<a id="P048"></a>

Hidden selection test material shall not be used for training or optimization; suitable safeguards shall be defined.

<a id="P049"></a>

Candidate submissions shall provide the technical information needed to identify, execute and verify the submitted codec.

<a id="P050"></a>

Legal requirements remain subject to future guidance from PCG.

<a id="P051"></a>

SA4 shall continue progressing all ULBC-MED technical documents not dependent on the legal evaluation.

<a id="P052"></a>

## 5  Proposed text for the candidate submission procedure

<a id="P053"></a>

The following text is proposed for inclusion in the ULBC candidate submission procedure:

<a id="P054"></a>

The candidate codec, including its trained model parameters, shall be frozen at submission. The candidate shall not access training data, remote training services or other unapproved external resources during qualification or selection testing.

<a id="P055"></a>

The proponent shall provide the information required to identify, execute and technically verify the submitted candidate, including model and executable versions, checksums, fixed parameters, runtime dependencies and operating instructions.

<a id="P056"></a>

The proponent shall declare that hidden ULBC qualification or selection test material has not been used for training, fine-tuning, model selection or parameter optimization.

<a id="P057"></a>

The proponent shall declare that it has the right to submit the candidate for evaluation and standardization and that, if selected, it will provide the cooperation and additional information required to complete the 3GPP specifications and to satisfy any applicable requirements subsequently agreed by SA or the competent 3GPP governance bodies.

<a id="P058"></a>

The proponent shall commit that, if its candidate is selected, it will: (a) disclose the training dataset under appropriate terms; (b) permit a frozen reference to be preserved for legal compliance verification and maintenance; (c) cooperate with trusted independent verification under NDA, including making the training procedure available to the trusted entity; and (d) provide cooperation and protected know-how required for maintenance or authorized retraining.

<a id="P059"></a>

Acceptance of a candidate submission by SA4 constitutes neither a legal assessment of the training material nor a warranty by 3GPP or its Organizational Partners.

<a id="P060"></a>

## 6  Conclusion

<a id="P061"></a>

The framework delivers development freedom, post-selection accountability, and immediate technical progress — without forcing a common dataset or requiring SA4 to take legal positions. Proponents retain their know-how during competition; the winner provides transparency through dataset disclosure, independent verification, and maintenance support. SA4 finalizes the technical framework now; legal details are settled by the competent bodies before SA approval.

<a id="P062"></a>

The Audio SWG is invited to:

<a id="P063"></a>

agree the framework in clause 2 as the basis for handling ULBC training datasets;

<a id="P064"></a>

agree the consolidated framework in clause 4;

<a id="P065"></a>

agree the candidate-submission commitment in clause 5 for integration into the relevant ULBC governing document; and

<a id="P066"></a>

continue finalizing technical ULBC-MED documents without prejudging the legal requirements under discussion in PCG.

<a id="P067"></a>

## 7  References

<a id="P068"></a>

SP-260696, "New WID on Ultra Low Bitrate Speech Codec for IMS voice service over NB-IoT (GEO)," TSG SA#112, June 2026.

<a id="P069"></a>

SA#112 meeting report and guidance on technical training dataset requirements for ULBC candidate codecs.

<a id="P070"></a>

SA4#137-e Audio SWG report and related contributions on technical training dataset requirements.

<a id="P071"></a>

PCG56Bis_03, "Legal considerations on AI/ML training datasets," ETSI legal input to PCG#56 bis ad hoc, 3 September 2026.

<a id="P072"></a>

PCG#56 bis ad hoc meeting report, 3 September 2026.

<a id="P073"></a>

S4-261087, "[FS_ULBC] Proposed Ad Hoc Meeting for Rel-20 ULBC."

<a id="P074"></a>

Applicable ULBC-MED permanent documents on design constraints, performance requirements, test procedures, complexity evaluation and codec selection.

**原文页眉：** 3GPP TSG-SA WG4 (SA4) Audio SWG Ad Hoc Meeting on ULBC-MED    S4aA260131<br>Shanghai, China, 28–30 September 2026
