# S4aA260108 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260108 [ULBC-MED] Preparation of common training material pending PCG guidance.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260108

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Preparation of common training material pending PCG guidance

<a id="P005"></a>

Agenda item:    4.10

<a id="P006"></a>

Document for:    Agreement

<a id="P008"></a>

## 1.    Introduction

<a id="P009"></a>

At TSG SA#112, TSG SA requested SA4 to discuss whether technical training-dataset requirements are needed for AI-based ULBC candidate codecs. In the SA4#137-e Chair’s survey (S4-261674, reported in SP-260909), 12 of 24 responding companies supported the definition of common training data, with one further company supporting it as an optional instrument — a majority of the positions expressed, although not a consensus. Samsung’s corresponding proposals at SA4#137-e are documented in S4-261510 and S4-261511.

<a id="P010"></a>

At the PCG#56bis ad hoc (3 September 2026), no conclusion was reached between a common and a proprietary training-dataset approach. The summary recorded that legal requirements are applicable to all scenarios, and an ad hoc group on the legal aspects was created. Guidance is expected to be reported towards TSG SA#114 (December 2026).

<a id="P011"></a>

Consequently, both a common and a proprietary approach remain possible outcomes of the PCG process. Rather than deciding between them now, SA4 should prepare so that either outcome can be implemented without schedule impact once the guidance is available. This contribution elaborates the “common training material” instrument of the problem-to-instrument mapping in [S4aA26xxxx, Way forward on ULBC training data] and proposes concrete, low-cost preparatory steps: a call for candidate publicly available datasets, a dataset inventory, and the principle that training material is assessed against the PCG legal requirements before use in candidate development.

<a id="P012"></a>

## 2.    Discussion

<a id="P013"></a>

## 2.1    Benefits previously identified

<a id="P014"></a>

The technical benefits of common training material were presented in S4-261510 and are only summarized here: it ensures that the qualification and selection comparison measures codec technology (architecture, training methodology, augmentation) rather than historical access to proprietary speech corpora; it provides all proponents with equal access to diverse speech material across languages, talkers and recording conditions; and it supports long-term maintainability of a specification whose normative model parameters derive from the training data. These benefits are unchanged and are not re-argued in this document.

<a id="P015"></a>

## 2.2    Developments since SA4#137-e

<a id="P016"></a>

Two developments from the PCG#56bis discussion are directly relevant to the common-versus-proprietary question:

<a id="P017"></a>

Legal efficiency. PCG recorded that legal requirements apply to all scenarios, and the ETSI legal analysis noted that a simple declaration alone is not sufficient and must be accompanied by substantial documentation. Under a common pool, the legal assessment is performed once, on a single set of known, publicly available material, and its result benefits every proponent and every implementer. Under a proprietary approach, an equivalent assessment burden arises separately for each proponent’s undisclosed corpus, with the associated documentation obligations. Whatever the content of the forthcoming guidance, a common pool is therefore the lowest-cost path to demonstrable compliance for proponents, for implementers and for 3GPP.

<a id="P018"></a>

Implementer and user expectations. Views expressed in the context of the PCG discussion, including from the user community, indicate an expectation that at least a common, inspectable set of training material should be available for validating the correct operation of the standardized codec, independent of any additional material a proponent may use.

<a id="P019"></a>

## 2.3    Compatibility with either PCG outcome

<a id="P020"></a>

Preparing a common training-data pool does not prejudge the PCG outcome:

<a id="P021"></a>

If the guidance supports common training material, the preparatory work in clause 2.4 enables SA4 to implement it without delay.

<a id="P022"></a>

If the guidance permits proprietary material, the pool remains valuable as commonly available baseline material, and it simplifies the training-data deliverables of the selected candidate [S4aA260106]: material drawn from the pool is publicly identified by construction, requiring no escrow or alternative-material arrangements.

<a id="P023"></a>

A common pool is also compatible with frameworks based on post-selection disclosure, and does not preclude documented supplementary material where the applicable requirements permit it. This corresponds to the JPEG AI precedent, where a common training dataset was mandated for the compared results and additional data was permitted only where described in detail, licensed and submitted with the proposal.

<a id="P024"></a>

## 2.4    Preparatory process

<a id="P025"></a>

The preparation can proceed in the following steps, primarily based on existing publicly available datasets:

<a id="P026"></a>

1)    Define the minimum technical characteristics required of common ULBC training material (language and speaker diversity, amount, sampling rate/bandwidth, source quality, acoustic characteristics, separation from test material).

<a id="P027"></a>

2)    Issue a call for candidate publicly available datasets using the template in clause 2.5.

<a id="P028"></a>

3)    Compile an inventory of the proposed datasets and their relevant technical characteristics.

<a id="P029"></a>

4)    Perform a gap analysis against the agreed characteristics, distinguishing gaps that must be present in the source material from gaps that may appropriately be addressed by agreed data-augmentation principles.

<a id="P030"></a>

5)    Assess the candidate datasets against the applicable PCG legal requirements once these are available.

<a id="P031"></a>

6)    Agree and document the common ULBC training-data pool in the applicable permanent document.

<a id="P032"></a>

Steps 1) to 4) are administrative and can start immediately at no cost to the technical work plan. Finalization of the pool follows the availability of the PCG legal requirements, since the candidate datasets must be assessed against them before use in candidate development.

<a id="P033"></a>

## 2.5    Dataset information template

<a id="P034"></a>

To simplify the review, candidate datasets should be proposed using the following template (extended from S4-261511 with license information relevant to the legal assessment):

<a id="T035"></a>

<a id="T035-R01"></a>
**T035-R01**

- <a id="T035-R01-C01"></a>列 1: Information
- <a id="T035-R01-C02"></a>列 2: Description

<a id="T035-R02"></a>
**T035-R02**

- <a id="T035-R02-C01"></a>列 1: Dataset name / version
- <a id="T035-R02-C02"></a>列 2: Public dataset identifier and release/version

<a id="T035-R03"></a>
**T035-R03**

- <a id="T035-R03-C01"></a>列 1: Source
- <a id="T035-R03-C02"></a>列 2: Location from which the dataset is publicly obtainable

<a id="T035-R04"></a>
**T035-R04**

- <a id="T035-R04-C01"></a>列 1: License / terms of use
- <a id="T035-R04-C02"></a>列 2: Applicable license(s) and any known conditions or restrictions

<a id="T035-R05"></a>
**T035-R05**

- <a id="T035-R05-C01"></a>列 1: Approximate duration
- <a id="T035-R05-C02"></a>列 2: Hours of speech

<a id="T035-R06"></a>
**T035-R06**

- <a id="T035-R06-C01"></a>列 1: Languages
- <a id="T035-R06-C02"></a>列 2: Languages and distribution, where available

<a id="T035-R07"></a>
**T035-R07**

- <a id="T035-R07-C01"></a>列 1: Speakers
- <a id="T035-R07-C02"></a>列 2: Number and relevant characteristics, where available

<a id="T035-R08"></a>
**T035-R08**

- <a id="T035-R08-C01"></a>列 1: Sampling rate / bandwidth
- <a id="T035-R08-C02"></a>列 2: Available audio sampling rates and bandwidth

<a id="T035-R09"></a>
**T035-R09**

- <a id="T035-R09-C01"></a>列 1: Audio format
- <a id="T035-R09-C02"></a>列 2: WAV, FLAC, MP3, etc.

<a id="T035-R10"></a>
**T035-R10**

- <a id="T035-R10-C01"></a>列 1: Recording conditions
- <a id="T035-R10-C02"></a>列 2: Clean, noisy, read/conversational speech, etc.

<a id="T035-R11"></a>
**T035-R11**

- <a id="T035-R11-C01"></a>列 1: Relevant metadata
- <a id="T035-R11-C02"></a>列 2: Transcripts, speaker information, etc.

<a id="T035-R12"></a>
**T035-R12**

- <a id="T035-R12-C01"></a>列 1: Proposed ULBC use
- <a id="T035-R12-C02"></a>列 2: Core speech, language diversity, higher-bandwidth material, etc.

<a id="T035-R13"></a>
**T035-R13**

- <a id="T035-R13-C01"></a>列 1: Known limitations
- <a id="T035-R13-C02"></a>列 2: Relevant technical or licensing limitations of the dataset

<a id="P037"></a>

## 3.    Proposals

<a id="P038"></a>

It is proposed that SA4:

<a id="P039"></a>

Proposal 1: agree that common training material remains a candidate instrument for the ULBC training-data technical work, per the problem-to-instrument mapping in [S4aA260107] pending the PCG guidance.

<a id="P040"></a>

Proposal 2: issue a call for candidate publicly available datasets using the template in clause 2.5, and maintain the resulting dataset inventory as a standing input to the training-data agenda item.

<a id="P041"></a>

Proposal 3: agree that any common training-data pool, and any training material used by any candidate, shall be assessed against the applicable PCG legal requirements before use in candidate development.
