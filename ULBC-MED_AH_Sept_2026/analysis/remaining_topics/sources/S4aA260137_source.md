# S4aA260137 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260137 Training datasets of deployed codecs.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA WG4 Audio SWB Ad Hoc Meeting on ULBC-MED    S4aA260137

<a id="P001"></a>

28-30 September 2026, Shanghai, China

<a id="P003"></a>

Source:    Nokia

<a id="P004"></a>

Title:    On training datasets of deployed 3GPP voice codecs and ULBC

<a id="P005"></a>

Agenda item:    4.10 – Other (ULBC-MED)

<a id="P006"></a>

Document for:    DISCUSSION

<a id="P009"></a>

## 1. Introduction

<a id="P010"></a>

ULBC-MED WID was approved in June. As already concluded during the FS_ULBC study, it is the common understanding that a potential ULBC solution will need to be AI-based. Therefore, ULBC is likely to utilize AI model training data, e.g., in the form of speech and other relevant audio signals.

<a id="P012"></a>

There has already been significant discussion relating to training datasets to be used for ULBC on various levels and fora, including technical and legal considerations, in SA4, SA, and PCG. During these discussions, it has appeared to the source that there may be significant misunderstandings about the role of training data for 3GPP voice codecs.

<a id="P014"></a>

In addition to training datasets that are typically the domain of the codec developer, ULBC-MED will consider test datasets, where at least implicit requirements will be imposed on the test material to ensure that the candidate solutions generalize over different languages, talkers, and other variations in the input material (e.g., background noise types). Training datasets are discussed in more detail in other inputs to this meeting.

<a id="P016"></a>

This input provides some clarifications relating to use of training datasets for 3GPP voice codecs, both those already deployed and the expected ULBC solution.

<a id="P019"></a>

## 2. Discussion

<a id="P020"></a>

There is a common understanding that an AI-based ULBC solution will need training data. During various discussions, the source has concluded that some parties consider this as a new property relating to AI-based solutions only. However, use of training datasets for voice codec development is not new.

<a id="P022"></a>

Training datasets have been extensively used in past voice codec developments, including previous 3GPP voice codecs that have been successfully deployed. For example, linear predictive (LP) model coefficients, voice activity detection (VAD), speech/music classification, and other functionalities and parameters have been trained fully or in part using large and varied training datasets, taking into account, e.g., different languages, large number of talkers, background noise types, music genres, and so on. While it can be easily argued that training and setting of key codec parameters based on training datasets encompass many more areas, the following discussion provides a simplified view focusing on one set of parameters and their significance on the overall codec solutions: LP parameter codebooks.

<a id="P024"></a>

Tables 1 and 2 summarize the bitrates allocated for LP information (LSF for AMR, ISP for AMR-WB) relative to codec bitrates for AMR and AMR-WB codecs, respectively.

<a id="P026"></a>

Table 1 – AMR bit usage for spectral model based on training data

<a id="T028"></a>

<a id="T028-R01"></a>
**T028-R01**

- <a id="T028-R01-C01"></a>列 1: Bitrate, kbps
- <a id="T028-R01-C02"></a>列 2: Bits (frame)
- <a id="T028-R01-C03"></a>列 3: Bits (LSF)
- <a id="T028-R01-C04"></a>列 4: LSF of total

<a id="T028-R02"></a>
**T028-R02**

- <a id="T028-R02-C01"></a>列 1: 12.2
- <a id="T028-R02-C02"></a>列 2: 244
- <a id="T028-R02-C03"></a>列 3: 38
- <a id="T028-R02-C04"></a>列 4: 15.57%

<a id="T028-R03"></a>
**T028-R03**

- <a id="T028-R03-C01"></a>列 1: 10.2
- <a id="T028-R03-C02"></a>列 2: 204
- <a id="T028-R03-C03"></a>列 3: 26
- <a id="T028-R03-C04"></a>列 4: 12.75%

<a id="T028-R04"></a>
**T028-R04**

- <a id="T028-R04-C01"></a>列 1: 7.95
- <a id="T028-R04-C02"></a>列 2: 159
- <a id="T028-R04-C03"></a>列 3: 27
- <a id="T028-R04-C04"></a>列 4: 16.98%

<a id="T028-R05"></a>
**T028-R05**

- <a id="T028-R05-C01"></a>列 1: 7.4
- <a id="T028-R05-C02"></a>列 2: 148
- <a id="T028-R05-C03"></a>列 3: 26
- <a id="T028-R05-C04"></a>列 4: 17.57%

<a id="T028-R06"></a>
**T028-R06**

- <a id="T028-R06-C01"></a>列 1: 6.7
- <a id="T028-R06-C02"></a>列 2: 134
- <a id="T028-R06-C03"></a>列 3: 26
- <a id="T028-R06-C04"></a>列 4: 19.40%

<a id="T028-R07"></a>
**T028-R07**

- <a id="T028-R07-C01"></a>列 1: 5.9
- <a id="T028-R07-C02"></a>列 2: 118
- <a id="T028-R07-C03"></a>列 3: 26
- <a id="T028-R07-C04"></a>列 4: 22.03%

<a id="T028-R08"></a>
**T028-R08**

- <a id="T028-R08-C01"></a>列 1: 5.15
- <a id="T028-R08-C02"></a>列 2: 103
- <a id="T028-R08-C03"></a>列 3: 23
- <a id="T028-R08-C04"></a>列 4: 22.33%

<a id="T028-R09"></a>
**T028-R09**

- <a id="T028-R09-C01"></a>列 1: 4.75
- <a id="T028-R09-C02"></a>列 2: 95
- <a id="T028-R09-C03"></a>列 3: 23
- <a id="T028-R09-C04"></a>列 4: 24.21%

<a id="P031"></a>

Table 2 – AMR-WB bit usage for spectral model based on training data

<a id="T033"></a>

<a id="T033-R01"></a>
**T033-R01**

- <a id="T033-R01-C01"></a>列 1: Bitrate, kbps
- <a id="T033-R01-C02"></a>列 2: Bits (frame)
- <a id="T033-R01-C03"></a>列 3: Bits (ISP)
- <a id="T033-R01-C04"></a>列 4: ISP of total

<a id="T033-R02"></a>
**T033-R02**

- <a id="T033-R02-C01"></a>列 1: 23.85
- <a id="T033-R02-C02"></a>列 2: 477
- <a id="T033-R02-C03"></a>列 3: 46
- <a id="T033-R02-C04"></a>列 4: 9.64%

<a id="T033-R03"></a>
**T033-R03**

- <a id="T033-R03-C01"></a>列 1: 23.05
- <a id="T033-R03-C02"></a>列 2: 461
- <a id="T033-R03-C03"></a>列 3: 46
- <a id="T033-R03-C04"></a>列 4: 9.98%

<a id="T033-R04"></a>
**T033-R04**

- <a id="T033-R04-C01"></a>列 1: 19.85
- <a id="T033-R04-C02"></a>列 2: 397
- <a id="T033-R04-C03"></a>列 3: 46
- <a id="T033-R04-C04"></a>列 4: 11.59%

<a id="T033-R05"></a>
**T033-R05**

- <a id="T033-R05-C01"></a>列 1: 18.25
- <a id="T033-R05-C02"></a>列 2: 365
- <a id="T033-R05-C03"></a>列 3: 46
- <a id="T033-R05-C04"></a>列 4: 12.60%

<a id="T033-R06"></a>
**T033-R06**

- <a id="T033-R06-C01"></a>列 1: 15.85
- <a id="T033-R06-C02"></a>列 2: 317
- <a id="T033-R06-C03"></a>列 3: 46
- <a id="T033-R06-C04"></a>列 4: 14.51%

<a id="T033-R07"></a>
**T033-R07**

- <a id="T033-R07-C01"></a>列 1: 14.25
- <a id="T033-R07-C02"></a>列 2: 285
- <a id="T033-R07-C03"></a>列 3: 46
- <a id="T033-R07-C04"></a>列 4: 16.14%

<a id="T033-R08"></a>
**T033-R08**

- <a id="T033-R08-C01"></a>列 1: 12.65
- <a id="T033-R08-C02"></a>列 2: 253
- <a id="T033-R08-C03"></a>列 3: 46
- <a id="T033-R08-C04"></a>列 4: 18.18%

<a id="T033-R09"></a>
**T033-R09**

- <a id="T033-R09-C01"></a>列 1: 8.85
- <a id="T033-R09-C02"></a>列 2: 177
- <a id="T033-R09-C03"></a>列 3: 46
- <a id="T033-R09-C04"></a>列 4: 25.99%

<a id="T033-R10"></a>
**T033-R10**

- <a id="T033-R10-C01"></a>列 1: 6.6
- <a id="T033-R10-C02"></a>列 2: 132
- <a id="T033-R10-C03"></a>列 3: 36
- <a id="T033-R10-C04"></a>列 4: 27.27%

<a id="P036"></a>

ULBC will differ from AMR and AMR-WB in two main aspects relevant for current discussion: the bitrates (1.0 and 1.4 kbps) supported by it will be significantly lower, and there is the expectation that the solution will be AI-based. Concerning the first aspect, it can be useful to approximate how AMR/AMR-WB bit allocation might behave if such traditional approach could be simply extrapolated to ULBC bitrates.

<a id="P038"></a>

Figures 1 and 2 present three simple trendline approximations based on AMR and AMR-WB bit allocations (see Tables 1 and 2), respectively. These estimates put the approaches at least in the 30-60% ballpark for training-based spectral model parameters, even reaching 100% for AMR-WB. As discussed above, there was always a dependency on training datasets for voice codecs. These estimates may suggest that this dependency could be considered more or less the same for traditional codec approaches and AI-based approaches at the extremely low bitrate range that the ULBC-MED work item targets.

<a id="P042"></a>

Figure 1 – AMR training dataset -based spectral model parameters extrapolated to ULBC bitrates (default Excel linear, logarithmic, power trendlines)

<a id="P046"></a>

Figure 2 – AMR-WB training dataset -based spectral model parameters extrapolated to ULBC bitrates (default Excel linear, logarithmic, power trendlines)

<a id="P049"></a>

An important note for the training datasets is that to be effective, robust, and without bias, they generally must include a large set of talkers, languages, and non-speech audio data. Properly preparing and selecting the training datasets is a skill in itself, and this process has a lot of room for innovation. These tried-and-true principles hold also for ULBC standardization.

<a id="P052"></a>

## 3. Summary

<a id="P053"></a>

This input provides clarification on the role of training datasets in previous 3GPP voice codecs. For example, LP parameter codebooks are typically trained using vast training datasets covering multiple languages, talkers, background signal types and levels, and even music and other generic sounds. For a traditional voice codec, operating at significantly higher bitrate than ULBC, such spectral model parameters derived based on training datasets and training procedures account for roughly 10-30% of the overall bitrate. With decreasing bitrate, this share gets larger.

<a id="P055"></a>

While ULBC will differ from previous codecs in some ways, e.g., being AI-based and operating at significantly lower bitrates, the basic principle of using a large amount of varied training data for the codec models is similar.
