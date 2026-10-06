# S4aA260158 — 原文 Markdown

> 来源 ZIP 内文件：`S4aA260158-VoiceAge-Proposal to skip the Qualification Phase.docx`。按当前文本转换；选择 OOXML 主显示分支以消除图形 fallback 重复。保留图形文本与方括号，图形连接和原页面布局不复刻。段落/表行定位标记是提取索引，不是原文编号。

<a id="P000"></a>

Source: · VoiceAge Corporation

<a id="P001"></a>

Title: · Proposal to skip the Qualification Phase

<a id="P002"></a>

Document for: · Discussion and Agreement

<a id="P003"></a>

Agenda Item: · x

<a id="P005"></a>

Introduction

<a id="P006"></a>

Historically, the Qualification phase played an important role as the first phase of candidate evaluation in speech codec standardization process. The Qualification phase was generally less comprehensive than the subsequent Selection and Characterization phases. The evaluation was often less rigorous in the sense that it usually involved in-house testing rather than evaluation in independent listening laboratories (LLs) and the evaluation was usually done by comparing the candidates to Terms of Reference rather than comparing them directly to each other. The Qualification served several purposes, notably:

<a id="P007"></a>

Reduction of the number of candidates going into a more comprehensive Selection test.

<a id="P008"></a>

Benchmarking of the candidate codecs with respect to each other, such that proponents of candidate solutions with clearly inferior performance could save on further investment in the code development.

<a id="P009"></a>

Potential collaboration phase among the qualified candidates

<a id="P010"></a>

On the other hand, organization and realization of any additional testing phase requires additional time and additional resources.

<a id="P011"></a>

Discussion

<a id="P012"></a>

The Qualification phase has been proposed also for the standardization of the ULBC-MED codec. The original proposal comprised quite a limited evaluation of just three test scenarios (the usual term “conditions” is avoided here to differentiate from test “conditions” within an experiment), tested at one codec bitrate, in one LL. Further, the question of potential collaboration phase was conceivable.

<a id="P013"></a>

Since the original proposal, it became clear that the extremely challenging time schedule for the ULBC-MED standardization does not allow for any meaningful collaboration phase between the Qualification and Selection. Thus, the Qualification phase was reduced to a “pre-Selection” where the assumption is that not only any collaboration phase in unrealistic, but the candidate codecs cannot even be modified.

<a id="P014"></a>

Further, several companies requested to extend the Qualification test to cover additional test scenarios, test the candidate codecs at both ULBC-MED bitrates, and x-check the experiments in two LLs, thus significantly extending the scope of the test. These requests have been compiled in [1] by the ULBC-MED rapporteur accounting to a minimum of 6 test scenarios (1 clean speech, 2 noisy speech, 2 noisy channel and one tandem), possibly more. Considering 2 bitrates and 2 LLs, the scope of the Qualification test approaches the scope of the Selection.

<a id="P015"></a>

As the competition is strong, it has been further requested to contract external LLs and to use a test set-up that compares the candidate codecs with respect to each other. Considering the P.800 DCR methodology and 20 candidate codecs, this basically translates to one test scenario per experiment (an experiment design to accomplish this was presented in [2]).

<a id="P016"></a>

Finally, benchmarking candidate codec proponents to save further development resources becomes irrelevant when the codec cannot be modified between Qualification and Selection. Besides, when Qualification was done in floating-point and Selection in fixed-point this argument was strong to avoid tedious float-to-fixe conversion for candidates not achieving the basic performance already with the floating-point code base. This conversion step between Qualification and Selection is not foreseen for the ULBC-MED standardization either.

<a id="P017"></a>

Proposal

<a id="P018"></a>

Considering the discussion above, we propose to skip the Qualification phase. Below is a preliminary example of how the Selection phase might look like, acknowledging that several aspects have not been decided yet, and some assumptions may change.

<a id="P019"></a>

Draft Selection Outline

<a id="P020"></a>

Based on [ ], we have at minimum the following scenarios:

<a id="P021"></a>

## 1 x clean speech - assuming different input levels within one experiment

<a id="P022"></a>

## 2 x noisy speech (street, car) – assuming DTX on and off within the same experiment

<a id="P023"></a>

## 1 x tandem (AMR-WB -> ULBC) – assuming just one tandem direction

<a id="P024"></a>

## 2 x channel errors (2% and 6%)

<a id="P025"></a>

Assuming the experimental design of [2], this would correspond to 6 DCR experiments. Assuming further that all the test scenarios need to be tested at both 1.0 and 1.4 kbps, and x-checked in 2 LLs (using two different languages), we have 24 experiments in total - as the very minimum.

<a id="P026"></a>

Following the last version of the Time Plan [2], the codec candidate Selection is March 19. This gives 9 weeks before the Selection SA4 May meeting. Reserving one week for compilation results by the Global Analysis Lab (GAL), and allowing the GAL contribution to be late (similarly as done in the IVAS standardization), and assuming further that the processing task can be pipelined with the task of the LLs, we would have 8 weeks to run the test.

<a id="P027"></a>

At the time of writing this contribution, two experienced independent LLs indicated an interest to take part in the ULBC-MED evaluation – Mesaqin and Force. Both indicated that they could run 2-3 experiments per week. Taking the conservative estimate of 2 experiments per week, we would still have room for 32 experiments. There is thus some margin for additional test scenarios and/or some time to reserve for the Host Laboratory tasks.

<a id="P028"></a>

References

<a id="P029"></a>

S4-261536 – Two-phase approach to select the ULBC candidate, source ULBC-MED Rapporteur.

<a id="P030"></a>

S4-261531 - Pair-balanced experiment design for ULBC qualification testing, source Fraunhofer IIS.

<a id="P031"></a>

S4-261745 - Permanent Document ULBC-2: Timeline for ULBC-MED, source ULBC-MED Rapporteur.

**页眉：** | 3GPP TSG SA WG4 Audio SWG AH | Tdoc S4aA260158
 | Shanghai, China, September 28-30, 2026 |
