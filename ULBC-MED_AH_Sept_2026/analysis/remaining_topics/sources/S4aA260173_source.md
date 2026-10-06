# S4aA260173 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260173 Dataset requirements.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWB Ad Hoc Meeting on ULBC-MED    S4aA260173

<a id="P001"></a>

28-30 September 2026, Shanghai, China    revision of S4aA260142

<a id="P003"></a>

Source:    Nokia

<a id="P004"></a>

Title:    On ULBC dataset requirements

<a id="P005"></a>

Agenda item:    4.10 – Other (ULBC-MED)

<a id="P006"></a>

Document for:    DISCUSSION and AGREEMENT

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

ULBC-MED WID was approved in June. As already concluded during the FS_ULBC study, it is the common understanding that a potential ULBC solution will need to be AI-based.

<a id="P012"></a>

There has already been significant discussion relating to training and testing datasets to be used for ULBC on various levels and fora, including technical and legal considerations, in SA4, SA, and PCG.

<a id="P014"></a>

This input discusses requirements for various speech and non-speech datasets that can be relevant for the work. In general, the source observes that these requirements primarily relate to verification of the codec capabilities, tested by subjective means. Thus, we propose that these requirements are dealt with in ULBC performance requirements, test plan, and potential additional deliverables, e.g., “demo tapes”. Thus, some material requirements may be set for the listening labs.

<a id="P016"></a>

Some aspects covered in this discussion are more relevant for legal considerations, and it is not the intention to discuss those in detail in this technical context. We note that SA4 may later receive specific PCG guidance on legal matters.

<a id="P018"></a>

## 2. Dataset requirements

<a id="P019"></a>

## 2.1 Bias – robustness

<a id="P021"></a>

Any voice codec suitable for mobile services, including voice over GEO, should perform consistently for various relevant inputs. This means the codec solution should be free of bias (e.g., exhibiting no strong language dependencies or other such bias) and robust against adverse signal and channel conditions (e.g., various background noise types and non-speech signals during and between speech utterances, packet losses, etc.).

<a id="P023"></a>

Specific considerations to ensure no bias and achieving robustness based on input signals include:

<a id="P024"></a>

Large number of tested and verified languages, including dialects and accents from all continents and language groups

<a id="P025"></a>

Variations of talker characteristics, including sufficient number of different talkers, balanced in gender, age (including also children and elderly people), and covering different speaking styles (e.g., cadence, pauses, sighs/breathing noise, emotion, intonation patterns)

<a id="P026"></a>

Overlapping speech

<a id="P027"></a>

Background signals, including several common noise types (e.g., car, traffic, street, office, nature, babble, music) and distinct background sounds (e.g., sirens, buzzers, crashes, bangs, engine and device sounds, background talkers)

<a id="P028"></a>

Other non-speech content, e.g., isolated instruments as critical samples

<a id="P029"></a>

Technical characteristics and limitations, e.g., bandwidth limitations, microphone frequency responses, levels (e.g., -16, -26, -36 dBov)

<a id="P031"></a>

## 2.2 Training dataset requirements

<a id="P033"></a>

Training datasets should be designed such that the codec achieves the required performance level, avoids bias, and is robust. Training dataset design is a skill in itself, an area to innovate in, and a critical component of the competitive approach. The source considers there is no motivation to set particular technical training dataset requirements as part of the ULBC-MED work.

<a id="P035"></a>

## 2.3 Test dataset requirements

<a id="P037"></a>

The main requirement for test datasets used for ULBC testing is that they must be unknown to candidate codec proponents. One obvious reason is fairness, another reason is to ensure no overfit, e.g., to specific background noises.

<a id="P039"></a>

In previous exercises, some background signals have been collected in SA4, e.g., through a Material Collection Entity. For ULBC-MED, this approach does not appear valid. On the other hand, this implies some more requirements for the participating test labs.

<a id="P041"></a>

Test labs should be required to provide clean speech signals and the agreed background signals (see 2.4). For clean speech signals, specific requirements may relate to agreed languages, number of talkers, etc. For background noises, the requirements may relate to description of what each background noise should and should not include, e.g., how the recording environment is set up, as well as minimum length of the sample(s).

<a id="P043"></a>

## 2.4 Planning of testing activities

<a id="P045"></a>

All the above considerations are relevant for subjective test material and subjective test coverage. However, in practice there is a limit to what can be afforded (time and cost) for the ULBC Qualification/Selection/Characterization phase testing. Therefore, only a limited set of languages and background noises can be covered as part of the testing. These should be selected based on listening lab capabilities and expert views on variability and representativeness.

<a id="P047"></a>

This planning exercise primarily covers the development of ULBC Terms of Reference, especially Performance Requirements, and the Test Plan(s) and the Processing Plan(s).

<a id="P049"></a>

In addition to what the subjective testing campaign covers, additional measures may be considered to ensure at least basic expert checks for more languages, background noise types, etc. can be performed prior to Selection. For example, latest at the ULBC Selection meeting, it could be considered a type of “demo tape” verification, where parties can check for consistent codec behaviour based on their own speech data. For example, an Audio AH meeting could be considered for this purpose.

<a id="P051"></a>

## 2.5 Legal considerations and requirements

<a id="P053"></a>

Legal requirements are beyond the scope of the current input and the group’s expertise. SA4 may still receive some legal guidance, e.g., from PCG relating to datasets. It is understood that proponents may therefore need to follow specific requirements that are currently still not known. Some such requirements could require further attention on SA4 level.

<a id="P055"></a>

In case of ULBC, at least the following technical considerations can be discussed relating to legal matters:

<a id="P057"></a>

Full talker privacy can generally be expected, since any codec candidate that overfits, e.g., preserving a specific talker or reconstructing whole training segments cannot be expected to meet the performance criteria set for ULBC.

<a id="P058"></a>

In this sense, a neural audio codec is safer than, e.g., a generative text-to-speech (TTS) system. Its purpose is to compress new speech (and other inputs), not recreate training material, which could happen with a TTS system.

<a id="P059"></a>

When training datasets and test datasets remain hidden, there is no exposure of talker identities and voices to the public.

<a id="P060"></a>

Publication of any datasets including speech will expose those talker identities and voices in public. If the data becomes public, it may be taken into non-3GPP use without permission.

<a id="P063"></a>

## 3. Summary & Proposal

<a id="P064"></a>

This input discusses various audio dataset requirements in scope of ULBC-MED.

<a id="P066"></a>

The source proposes to agree on the following aspects, discussed in this document:

<a id="P069"></a>

All subjective test datasets, including background noise signals, need to be unknown to candidate codec proponents.

<a id="P070"></a>

Dataset considerations on bias, representativeness, and robustness are taken directly into account in development of ULBC Test Plan(s), and Processing Plan(s).
