# S4aA260103 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260103 [ULBC-MED] Language coverage for ULBC qualification and selection testing.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 ULBC Ad-hoc Meeting    S4aA260103

<a id="P001"></a>

Shanghai, China, 28 – 30 September 2026

<a id="P003"></a>

Source:    Samsung Electronics Co., Ltd.

<a id="P004"></a>

Title:    [ULBC-MED] Language coverage for ULBC qualification and selection

<a id="P005"></a>

Agenda item:    4.7

<a id="P006"></a>

Document for:    Agreement

<a id="P008"></a>

## 1.    Introduction

<a id="P009"></a>

The ULBC test plans for the qualification and selection phases and the associated processing plan (ULBC-7) are under development, and engagement with candidate listening laboratories has started following the agreements at SA4#137-e. In previous 3GPP codec developments, the set of languages used in subjective testing was in practice largely determined by the capabilities of the appointed listening laboratories. During SA4#137-e it was similarly suggested, in the context of engaging with laboratories, to ask candidate laboratories which languages they support and to start from there.

<a id="P010"></a>

This contribution proposes the opposite order: SA4 should first agree the set of languages in which ULBC candidates are to be tested, based on service-relevant criteria – in particular the number of speakers of languages in the world and the market forecasts for GEO satellite voice services – and the appointment of listening laboratories should then follow the agreed language requirements. The tested languages should not depend on the location or default language capabilities of the laboratories that happen to be available.

<a id="P011"></a>

## 2.    Discussion

<a id="P012"></a>

## 2.1    Language coverage should be a service requirement, not a procurement outcome

<a id="P013"></a>

For EVS, the subjective selection testing comprised 24 experiments, each conducted in two languages, covering ten languages in total [3]. The composition of that language set, however, essentially reflected the locations of the proponents and the contracted listening laboratories rather than the expected user population: six of the ten languages were European, while languages such as Hindi, Arabic, Bengali, Indonesian, Portuguese and Urdu – each with more speakers than most of the tested European languages – were not part of the selection testing. For a classical signal-processing codec initially deployed in VoLTE networks in Europe, North America and East Asia, this carried limited risk, since the coding algorithms are largely language-agnostic by construction and testing could reasonably be extrapolated to other languages.

<a id="P014"></a>

If the same procurement-driven approach is applied to ULBC, the tested languages will effectively be a by-product of which laboratories respond to the call and where they are located. Established P.800 listening laboratories are concentrated in North America and Europe, whereas, as discussed in clause 2.2, the forecast markets for GEO satellite voice services are concentrated elsewhere. The languages most relevant to the ULBC service would then be exactly those least likely to be tested.

<a id="P015"></a>

## 2.2    The forecast GEO service markets and the languages of their users

<a id="P016"></a>

TR 26.940 [1] documents the application scenarios for ultra-low bitrate communication services with a primary focus on voice over GEO. The value of GEO satellite voice lies where terrestrial coverage is absent or unreliable: remote and rural areas, island and archipelago geographies, deserts and mountainous regions, disaster-prone regions, and maritime use.

<a id="P017"></a>

Market forecasts for satellite direct-to-device and NTN services consistently identify Asia-Pacific as the fastest-adopting region – driven by large mobile subscriber bases, island geographies, remote areas, disaster-prone regions and maritime activity – and Sub-Saharan Africa and the Middle East as high-growth regions with the largest untapped addressable markets, with the overall satellite D2D market forecast to grow at a CAGR of approximately 35% towards 2030 [5]. The user populations of these markets speak, among others, Hindi, Bengali, Urdu, Indonesian, Mandarin Chinese, Arabic, Swahili, Hausa, Spanish, Portuguese and French. Annex A lists candidate languages together with their numbers of speakers [6] and their relevance to the forecast GEO service markets.

<a id="P018"></a>

Seven of the ten most spoken languages in the world are predominantly spoken in regions identified as primary growth markets for satellite voice services. A language set inherited from the locations of available listening laboratories would cover few, if any, of them.

<a id="P019"></a>

## 2.3    Language robustness of an AI-based codec can only be evidenced by testing

<a id="P020"></a>

Unlike classical codecs, an AI-based codec standardizes trained model parameters, and its behaviour can depend on the phonetic, prosodic and tonal characteristics of the input speech relative to the material the model was trained on. Phenomena that are absent or under-represented in training – for example lexical tone, particular phoneme inventories, or speaking styles – may degrade in ways that do not occur for signal-processing codecs.

<a id="P021"></a>

In the SA4#137-e survey on ULBC training data, robustness across languages and avoidance of bias towards specific speech or language conditions were widely identified as main technical objectives [4]. It was also noted in the discussion that language distribution concerns are ultimately better handled as part of the testing: whether a language is represented in the training data does not by itself indicate whether the codec performs well in it. Subjective testing is thus the mechanism by which language robustness is actually evidenced.

<a id="P022"></a>

A language that is not tested contributes no evidence. If a systematic weakness in a major service-market language is discovered only after deployment, the model parameters are already standardized and any correction may require retraining, with the associated maintenance difficulties. The test language set should therefore be selected deliberately, covering both the languages of the forecast service markets and adequate typological diversity, including at least one tonal language.

<a id="P023"></a>

## 2.4    Decoupling the tested languages from laboratory location is practical

<a id="P024"></a>

Testing a language does not require a listening laboratory located where that language is spoken:

<a id="P025"></a>

Source material: speech recordings by native talkers can be commissioned and procured independently of the listening laboratory. The processing plan already foresees newly recorded, unpublished material to avoid overlap with training data [2]; the recording effort can be directed to the agreed languages.

<a id="P026"></a>

Listening panels: native listeners can be recruited by laboratories from local communities, through partner organisations, or through supervised remote arrangements. Experience from previous codec testing shows that laboratories can run experiments in languages other than that of their location.

<a id="P027"></a>

Call for laboratories: the call should enumerate the agreed languages and ask laboratories to declare which of them they can support, alone or in partnership, and at what cost – rather than deriving the language set from the laboratories’ replies.

<a id="P028"></a>

Cost and schedule impacts can be managed by agreeing a compact mandatory language set for the qualification phase and a broader set for the selection and characterization phases, in line with the overall funding discussion.

<a id="P029"></a>

## 3.    Proposal

<a id="P030"></a>

Samsung proposes the following:

<a id="P031"></a>

Proposal 1: SA4 agrees the set of languages for ULBC qualification and selection testing based on service-relevant criteria – including the number of speakers worldwide, the forecast markets for GEO satellite voice services, and phonetic/typological diversity (including at least one tonal language) – independent of the location or currently available language capabilities of candidate listening laboratories.

<a id="P032"></a>

Proposal 2: The call for listening laboratories enumerates the agreed languages and requests laboratories to indicate which of these languages they can support, including through partnerships or remote recruitment of native listeners. Laboratory appointment follows the agreed language requirements, not the reverse.

<a id="P033"></a>

Proposal 3: As a working assumption, ULBC candidates are evaluated in at least [X] languages in the qualification phase and at least [Y] languages in the selection phase, drawn from the candidate language list in Annex A, with the remaining languages of Annex A considered for the characterization phase.

<a id="P034"></a>

Proposal 4: The agreed language set is captured in the ULBC qualification and selection test plans, and the responsibilities and process for sourcing speech material in the agreed languages, independent of listening-laboratory location, are captured in the ULBC-7 processing plan.

<a id="P036"></a>

## 4.    References

<a id="P037"></a>

[1]    3GPP TR 26.940, “Study on performance requirements for a codec supporting IMS voice services over GEO satellite”.

<a id="P038"></a>

[2]    S4-261728, “ULBC Permanent document (ULBC-7): Processing plan”, v0.1.0.

<a id="P039"></a>

[3]    3GPP TR 26.952, “Codec for Enhanced Voice Services (EVS); Performance characterization”.

<a id="P040"></a>

[4]    S4-261382, “Survey on technical considerations related to training and validation datasets for ULBC candidate codecs”, and the related discussion in S4-261670, “Report from Audio SWG during 3GPP SA4#137-e”.

<a id="P041"></a>

[5]    See e.g. MarketsandMarkets, “Satellite Direct-to-Device (D2D) Market, Forecast to 2030”; Global Market Insights, “Satellite NTN Market”; Omdia, smartphone satellite D2D service revenue forecast (2030).

<a id="P042"></a>

[6]    Ethnologue: Languages of the World, 2026 edition (total L1+L2 speakers).

<a id="P044"></a>

Annex A:    Candidate languages for ULBC subjective testing

<a id="P045"></a>

The table below lists candidate languages ordered by total number of speakers, together with their relevance to the forecast GEO satellite voice service markets. The list is a starting point for discussion and is not exhaustive.

<a id="T046"></a>

<a id="T046-R01"></a>
**T046-R01**

- <a id="T046-R01-C01"></a>列 1: Language
- <a id="T046-R01-C02"></a>列 2: Total speakers (million)  [6]
- <a id="T046-R01-C03"></a>列 3: Relevance for GEO satellite voice services
- <a id="T046-R01-C04"></a>列 4: Typological note

<a id="T046-R02"></a>
**T046-R02**

- <a id="T046-R02-C01"></a>列 1: English
- <a id="T046-R02-C02"></a>列 2: 1 528
- <a id="T046-R02-C03"></a>列 3: Global lingua franca; widely used second language across all forecast GEO service regions; maritime and aeronautical communication
- <a id="T046-R02-C04"></a>列 4: Non-tonal

<a id="T046-R03"></a>
**T046-R03**

- <a id="T046-R03-C01"></a>列 1: Mandarin Chinese
- <a id="T046-R03-C02"></a>列 2: 1 184
- <a id="T046-R03-C03"></a>列 3: Large rural and remote terrestrial coverage gaps; strong regional NTN/D2D activity
- <a id="T046-R03-C04"></a>列 4: Tonal

<a id="T046-R04"></a>
**T046-R04**

- <a id="T046-R04-C01"></a>列 1: Hindi
- <a id="T046-R04-C02"></a>列 2: 611
- <a id="T046-R04-C03"></a>列 3: South Asia; among the largest forecast growth markets for satellite D2D with substantial terrestrial coverage gaps
- <a id="T046-R04-C04"></a>列 4: Non-tonal

<a id="T046-R05"></a>
**T046-R05**

- <a id="T046-R05-C01"></a>列 1: Spanish
- <a id="T046-R05-C02"></a>列 2: 561
- <a id="T046-R05-C03"></a>列 3: Latin America, including remote Andean and Amazon regions with limited terrestrial coverage
- <a id="T046-R05-C04"></a>列 4: Non-tonal

<a id="T046-R06"></a>
**T046-R06**

- <a id="T046-R06-C01"></a>列 1: Arabic
- <a id="T046-R06-C02"></a>列 2: 335
- <a id="T046-R06-C03"></a>列 3: Middle East and North Africa; desert and remote geography, energy-sector operations
- <a id="T046-R06-C04"></a>列 4: Non-tonal; multiple regional varieties

<a id="T046-R07"></a>
**T046-R07**

- <a id="T046-R07-C01"></a>列 1: French
- <a id="T046-R07-C02"></a>列 2: 334
- <a id="T046-R07-C03"></a>列 3: Sub-Saharan and North Africa; maritime
- <a id="T046-R07-C04"></a>列 4: Non-tonal

<a id="T046-R08"></a>
**T046-R08**

- <a id="T046-R08-C01"></a>列 1: Bengali
- <a id="T046-R08-C02"></a>列 2: 274
- <a id="T046-R08-C03"></a>列 3: South Asia; densely populated, disaster-prone delta regions where resilient connectivity is a driver
- <a id="T046-R08-C04"></a>列 4: Non-tonal

<a id="T046-R09"></a>
**T046-R09**

- <a id="T046-R09-C01"></a>列 1: Portuguese
- <a id="T046-R09-C02"></a>列 2: 269
- <a id="T046-R09-C03"></a>列 3: Brazil, including the Amazon region; Sub-Saharan Africa
- <a id="T046-R09-C04"></a>列 4: Non-tonal

<a id="T046-R10"></a>
**T046-R10**

- <a id="T046-R10-C01"></a>列 1: Indonesian
- <a id="T046-R10-C02"></a>列 2: 255
- <a id="T046-R10-C03"></a>列 3: Archipelago geography; maritime activity; disaster-prone region
- <a id="T046-R10-C04"></a>列 4: Non-tonal

<a id="T046-R11"></a>
**T046-R11**

- <a id="T046-R11-C01"></a>列 1: Urdu
- <a id="T046-R11-C02"></a>列 2: 246
- <a id="T046-R11-C03"></a>列 3: South Asia; mountainous and remote regions
- <a id="T046-R11-C04"></a>列 4: Non-tonal
