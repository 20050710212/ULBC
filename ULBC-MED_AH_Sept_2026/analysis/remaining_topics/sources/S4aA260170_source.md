# S4aA260170 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260170_ULBC_status_and_way_forward_on_training_dataset.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG AH    S4aA260170

<a id="P001"></a>

Shanghai, P.R.China, 28-30 September 2026    (revision of S4aA260099)

<a id="P003"></a>

Source:    vivo Mobile Communication Co.,Ltd

<a id="P004"></a>

Title:    [ULBC-MED] Status and way forward on the ULBC training dataset topic

<a id="P005"></a>

Agenda item:    4.10

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

At SA4#137-e, the SA WG4 Chair surveyed training-data requirements for ULBC candidate codecs [1]. Responses split: some companies proposed new technical requirements/guidance, others opposed any additional dataset-governance mechanism. Per the SA4 Audio Chair's overview [2], SA4 has no consensus on introducing a common training dataset.

<a id="P011"></a>

In parallel, PCG held an extraordinary meeting (PCG#56-Bis, 3 September 2026) on 3GPP's involvement and legal requirements for AI/ML training datasets [3]. PCG's guidance is expected to be available around PCG's next meeting on 21 October 2026.

<a id="P012"></a>

At SA#113, agenda item 3.4 covered the SA WG4 Chair report [4], Samsung's paper on next steps on ULBC [5] with its accompanying LS on guidance [6], and Verizon's paper on a deployable and maintainable ULBC codec [7]. SA#113 reached no conclusion and sent no LS to SA4; operators' technical requirements were noted as within SA4's scope.

<a id="P013"></a>

This contribution reviews the current state of the training-dataset topic and proposes a way forward for SA4-Audio SWG on the ULBC-MED permanent documents, the pending PCG guidance, and operators' technical requirements.

<a id="P014"></a>

## 2    Discussion

<a id="P015"></a>

## 2.1    ULBC-1 to ULBC-8 are independent of the training-dataset question

<a id="P016"></a>

The ULBC-MED permanent documents ULBC-1 (Overview) through ULBC-8 (Qualification/Selection test plans) define the rules of the ULBC candidate-selection process — project overview, timeline, performance requirements, design constraints, qualification/selection rules, deliverables and processing/test plans — i.e. how candidates are qualified, tested and compared. ULBC candidates are AI/ML-based codecs: the training dataset is an input to each proponent's own algorithm-development process, not a condition of the selection process itself, and this holds even if a common training dataset is eventually required — that would be a separate requirement on the training process, unrelated to how candidates are qualified and selected. None of ULBC-1 through ULBC-8 therefore specifies, or depends on, which training dataset a candidate uses.

<a id="P017"></a>

Whether a common dataset is eventually used for ULBC is therefore unrelated to ULBC-1 through ULBC-8, and none of that work should be paused, or reshaped in anticipation of the pending PCG guidance.

<a id="P018"></a>

Proposal#1: ULBC-1 through ULBC-8 continue on their normal timeline, independent of the training-dataset question.

<a id="P019"></a>

## 2.2    Legal requirements: SA4 follows any PCG guidance on training datasets, common or private

<a id="P020"></a>

As currently drafted, PCG's legal discussion does not distinguish between a common dataset and (multiple) proprietary datasets in terms of legal risk — the same legal requirements (e.g. licensing terms, documented privacy details) are expected to apply whichever is used [3]. PCG's guidance is also not specific to ULBC: it is intended to cover AI/ML-related training-data topics across 3GPP generally.

<a id="P021"></a>

Given this, SA4's commitment does not depend on which outcome PCG reaches: once PCG issues guidance on AI/ML training datasets — whether it concludes in favour of a common dataset, a proprietary/self-declared approach, or something else — SA4 will follow it. Such guidance is expected around PCG's next meeting on 21 October 2026.

<a id="P022"></a>

## 2.3    Technical requirements raised by operators are within SA4’s technical scope

<a id="P023"></a>

Verizon's SP-260919 [7] raises language/accent robustness and dataset-transparency/maintenance requirements for ULBC candidate codecs, in the context of the broader SA#113 discussion on next steps and guidance for ULBC (Samsung, [5][6]). These are legitimate SA4 technical requirements, independent of whether the training dataset used by any given candidate is common or proprietary. AI/ML-based codecs also raise other technical requirements that operators have not explicitly raised — e.g. version interoperability during maintenance/updates — which SA4 should address on the same basis. SA4-Audio SWG should address these within its normal ULBC-MED technical work (e.g. test-language coverage, see Annex A; possible post-selection dataset disclosure), and welcomes contributions proposing solutions.

<a id="P024"></a>

Proposal#2: The technical requirements are within SA4's current technical scope and should be considered; contributions proposing solutions are welcome.

<a id="P025"></a>

## 3    Proposal

<a id="P026"></a>

It is proposed to agree above listed 2 proposals.

<a id="P027"></a>

## 4    References

<a id="P028"></a>

[1]    S4-261674, "SA WG4 Chair survey on Training Data Requirements for ULBC Candidate Codecs", SA WG4 Chair, SA4#137-e, August 2026.

<a id="P029"></a>

[2]    https://www.3gpp.org/ftp/tsg_sa/WG4_CODEC/TSGS4_137-e/Inbox/Drafts/Audio/Technical%20requirements%20and%20common%20dataset.docx

<a id="P030"></a>

[3]    https://www.3gpp.org/ftp/PCG/PCG_56_Bis/Report/PCG57_xx%20-%20PCG56-Bis%20Draft%20Meeting%20Report%20v.1.3.docx

<a id="P031"></a>

[4]    SP-260909, SA WG4 Chair report on Training Data Requirements for ULBC Candidate Codecs, TSG SA#113, September 2026.

<a id="P032"></a>

[5]    SP-260912, "Next steps on ULBC", Samsung, TSG SA#113, September 2026.

<a id="P033"></a>

[6]    SP-260913, "LS on guidance on ULBC", Samsung, TSG SA#113, September 2026.

<a id="P034"></a>

[7]    SP-260919, "Ensuring a deployable and maintainable ULBC codec", Verizon, TSG SA#113, September 2026.

<a id="P035"></a>

[8]    S4-000087 (Tdoc S4/SMG11 87/00), "Permanent project document WB-4: Design Constraints, v.1.0", joint TSG-S4#9 – SMG11#14, January 2000.

<a id="P036"></a>

[9]    S4-130778, "EVS Permanent Document #4 (EVS-4): EVS design constraints", v1.2, SA4#74, July 2013.

<a id="P037"></a>

[10]    3GPP TR 26.976 V8.0.0, "Performance characterization of the Adaptive Multi-Rate Wideband (AMR-WB) speech codec", December 2008.

<a id="P038"></a>

[11]    3GPP TR 26.952 V13.0.0, "Codec for Enhanced Voice Services (EVS); Performance characterization", January 2016.

<a id="P039"></a>

[12]    M. S. Dryer and M. Haspelmath (eds.), The World Atlas of Language Structures Online, Feature 2A: "Vowel Quality Inventories", Max Planck Institute for Evolutionary Anthropology, Leipzig, https://wals.info/chapter/2.

<a id="P040"></a>

[13]    M. S. Dryer and M. Haspelmath (eds.), The World Atlas of Language Structures Online, Feature 10A: "Vowel Nasalization", Max Planck Institute for Evolutionary Anthropology, Leipzig, https://wals.info/chapter/10.

<a id="P041"></a>

[14]    M. S. Dryer and M. Haspelmath (eds.), The World Atlas of Language Structures Online, Feature 13A: "Tone", Max Planck Institute for Evolutionary Anthropology, Leipzig, https://wals.info/chapter/13.

<a id="P042"></a>

[15]    M. S. Dryer and M. Haspelmath (eds.), The World Atlas of Language Structures Online, Feature 12A: "Syllable Structure", Max Planck Institute for Evolutionary Anthropology, Leipzig, https://wals.info/chapter/12.

<a id="P043"></a>

Annex A:    Phonetic-typological basis for language generalization in codec testing

<a id="P044"></a>

Language robustness can be demonstrated by covering the main acoustic-phonetic dimensions along which speech-codec performance is known to vary, rather than by testing many languages individually. Table A.1 classifies representative test languages by these stress dimensions, aligned with the typological features defined in the World Atlas of Language Structures (WALS) [12]-[15], consistent with the language set already used in AMR-WB and EVS characterization testing (TR 26.976 [10], TR 26.952 [11]).

<a id="T045"></a>

<a id="T045-R01"></a>
**T045-R01**

- <a id="T045-R01-C01"></a>列 1: Stress dimension
- <a id="T045-R01-C02"></a>列 2: Typological range
- <a id="T045-R01-C03"></a>列 3: Representative language(s)

<a id="T045-R02"></a>
**T045-R02**

- <a id="T045-R02-C01"></a>列 1: Baseline (moderate on all dimensions)
- <a id="T045-R02-C02"></a>列 2: —
- <a id="T045-R02-C03"></a>列 3: English, Spanish

<a id="T045-R03"></a>
**T045-R03**

- <a id="T045-R03-C01"></a>列 1: Lexical tone / F0 fidelity (WALS Feature 13A: Tone)
- <a id="T045-R03-C02"></a>列 2: No tone (most western Eurasian languages) to complex contour-tone systems (concentrated in East/Southeast Asia)
- <a id="T045-R03-C03"></a>列 3: Mandarin Chinese (also Cantonese, Vietnamese, Thai)

<a id="T045-R04"></a>
**T045-R04**

- <a id="T045-R04-C01"></a>列 1: Laryngeal contrast in stop consonants
- <a id="T045-R04-C02"></a>列 2: Two-way (voiced/voiceless or aspirated/unaspirated) contrast in most languages above vs. three-way tense/lax/aspirated contrast
- <a id="T045-R04-C03"></a>列 3: Korean

<a id="T045-R05"></a>
**T045-R05**

- <a id="T045-R05-C01"></a>列 1: Rhythm/timing
- <a id="T045-R05-C02"></a>列 2: Stress-timed, syllable-timed and mora-timed languages stress temporal modelling differently
- <a id="T045-R05-C03"></a>列 3: Japanese (mora-timed)

<a id="T045-R06"></a>
**T045-R06**

- <a id="T045-R06-C01"></a>列 1: Consonant clusters / sibilant density (WALS Feature 12A: Syllable Structure)
- <a id="T045-R06-C02"></a>列 2: Simple (C)V syllables to complex multi-consonant onsets/codas
- <a id="T045-R06-C03"></a>列 3: Slavic (Russian/Polish); German

<a id="T045-R07"></a>
**T045-R07**

- <a id="T045-R07-C01"></a>列 1: Emphatic/pharyngeal consonants
- <a id="T045-R07-C02"></a>列 2: Spectral content largely absent from most European languages
- <a id="T045-R07-C03"></a>列 3: Arabic

<a id="T045-R08"></a>
**T045-R08**

- <a id="T045-R08-C01"></a>列 1: Retroflex vs. dental consonant contrast
- <a id="T045-R08-C02"></a>列 2: Retroflex (apical post-alveolar) consonants contrasting with dental consonants at the same manner of articulation; largely absent from European and East Asian languages
- <a id="T045-R08-C03"></a>列 3: Hindi (also other Indo-Aryan and Dravidian languages)

<a id="T045-R09"></a>
**T045-R09**

- <a id="T045-R09-C01"></a>列 1: Vowel nasalization (WALS Feature 10A)
- <a id="T045-R09-C02"></a>列 2: Contrastive nasal vs. oral vowels, present in a minority of languages
- <a id="T045-R09-C03"></a>列 3: French

<a id="T045-R10"></a>
**T045-R10**

- <a id="T045-R10-C01"></a>列 1: Vowel inventory size / length (WALS Feature 2A)
- <a id="T045-R10-C02"></a>列 2: Small/average (e.g. 5 vowels) to large or length-contrasting systems
- <a id="T045-R10-C03"></a>列 3: Finnish (also Swedish, Danish); Spanish (small)

<a id="T045-R11"></a>
**T045-R11**

- <a id="T045-R11-C01"></a>列 1: [Within-language dialectal/accent variation
- <a id="T045-R11-C02"></a>列 2: Regional accent variation (vowel quality, rhoticity, intonation) within a single widely-spoken, pluricentric language
- <a id="T045-R11-C03"></a>列 3: English: US (California, Texas, Alabama, New Jersey), UK (East London, Scottish, West Midlands)]

<a id="P047"></a>

Languages that share the same stress dimension can be represented by a single language in this set rather than tested individually; this is consistent with AMR-WB and EVS characterization testing, which likewise used a representative set of languages rather than exhaustive per-language coverage.
