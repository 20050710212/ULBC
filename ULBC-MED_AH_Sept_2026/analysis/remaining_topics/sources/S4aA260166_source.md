# S4aA260166 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260166_pair_balanced_experiment_design.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP SA4 (AH) Audio SWG on ULBC-MED    S4aA260166

<a id="P001"></a>

28-30 September 2026, Shanghai, China     revision of S4aA260125

<a id="P003"></a>

Source:    Fraunhofer IIS

<a id="P004"></a>

Title:    [ULBC-MED] Pair-balanced experiment design: responses and randomization tables

<a id="P005"></a>

Agenda item:    TBC

<a id="P006"></a>

Document for:    Discussion and Agreement

<a id="P007"></a>

Work Item:    ULBC-MED

<a id="P009"></a>

Introduction

<a id="P010"></a>

This contribution proposes a separate test for each operating point for the ULBC testing campaign, especially if a qualification phase is necessary, and the pair-balanced material assignment as the baseline experiment design [1].

<a id="P011"></a>

The pair-balanced experiment design for ULBC qualification testing was presented in S4-261531 [1] at SA4#137-e and was noted [2]. The discussion raised three questions: individual randomization for each listener, laboratory implementation and cost, and the handling of the two bit rates. This contribution addresses these questions and provides the randomization tables used in the verification campaign as an electronic attachment.

<a id="P012"></a>

Individual randomization per listener

<a id="P013"></a>

Each listener receives a distinct playlist to ensure uniform paired evidence. For each listener, every one of the 25 point-relevant conditions is presented with six of the 30 source items. Each of the 300 condition pairs therefore occurs with exactly one shared source item, so all pairs receive equal evidence.

<a id="P014"></a>

If a group of listeners uses a common playlist, the shared source items are fixed for that group. The conditions must then be partitioned into alignment groups, as in the EVS designs. This produces stronger evidence for condition pairs within an alignment group and weaker evidence for pairs across groups. Consequently, a candidate’s score depends partly on the alignment group to which it is assigned, as discussed in clause 2.2 of [1]. Placing all candidates in one alignment group would instead require approximately 20 presentations of the same source item per session, compared with a maximum of 11 in previous practice.

<a id="P015"></a>

The 25 playlists are rotations of a single construction rather than 25 independent randomizations. The rotation avoids both unequal pair evidence and excessive repetition of source items and the panel is therefore balanced as a whole, while each listener retains complete pair coverage.

<a id="P016"></a>

Laboratory delivery and cost

<a id="P017"></a>

The playlists are generated as part of the test design (see clause 6 of this document), fixed before the test, and delivered unchanged. Their preparation and delivery therefore add no laboratory cost. The operational impact arises only when a listener must be replaced.

<a id="P018"></a>

When a listener group shares one playlist, a listener who fails screening can be replaced from a common pool because every listener in the group evaluates the same material. In the pair-balanced design, each rotation contributes a specific share of the pair coverage. A rejected session must therefore be repeated using the same rotation. It is out of scope how a laboratory schedules and assigns listeners, however there may be a slight burden as the laboratory must screen results as they become available and assign a replacement listener to the affected rotation instead of waiting until the end of the campaign. This is a scheduling requirement, not a change to the playback system.

<a id="P019"></a>

Handling of the two bit rates

<a id="P020"></a>

At SA4#137-e, the group agreed on the two bit rates of 1.0 kbps and 1.4 kbps [2], [3]. The design in [1] assigns all candidates at one operating point to one test, as derived from the inter-laboratory analysis in clause 2.1 of [1].

<a id="P021"></a>

Including both bit rates in one test would double the number of conditions and make the test too large for a single laboratory. Splitting such a test across laboratories would introduce laboratory offsets into the comparison, where they could be mistaken for codec differences. A common test is intended to avoid this effect. In the EVS qualification exercise, identical reference conditions measured by at least three laboratories differed by 0.19 MOS at the median and 0.35 MOS at the 95th percentile. These differences are comparable to the 0.05–0.3 MOS candidate differences that a best-of-m decision might have to resolve. The source therefore proposes that each test contain all candidates at exactly one operating point.

<a id="P022"></a>

A combined verdict for each candidate across both bit rates is a matter of ULBC-5a/b, not a material-assignment issue. ULBC-5a/b should define how the two test results are combined. This decision does not require changes to the playlists.

<a id="P023"></a>

Condition list and the number of tests

<a id="P024"></a>

One test carries 25 point-relevant conditions at one operating point. In the verification campaign these were 20 candidates, four AMR-WB rates and the unprocessed DIRECT, with the five MNRU anchors outside the ranking.

<a id="P025"></a>

One test can accommodate 25 relevant conditions that are compared against each other. The selected qualification conditions therefore determine the number of tests required. Each additional operating point, background-noise type, or input level requires a separate test because all candidates must also be evaluated under that condition. For example, two bit rates combined with one additional signal condition require four tests.

<a id="P026"></a>

Electronic attachment

<a id="P027"></a>

The attached file rand_DCR_P800_pairbalanced_L25.csv contains the 25 playlists used in the verification campaign, unchanged from their delivered form. Each playlist contains six blocks of 30 trials, giving 180 trials per listener and 4,500 trials across the panel. Each trial identifier comprises the prefix an1, a category, a sample, and a condition; for example, an1a4s1.c17. Categories range from a1 to a5, samples from s1 to s6, and conditions from c01 to c30.

<a id="P028"></a>

The design constrains five talker categories but does not constrain their contents. The verification campaign used three female and two male talkers, labelled f1 to f3 and m1 to m2. In the attached table, these labels are replaced by the neutral labels a1 to a5 using the mapping f1→a1, f2→a2, f3→a3, m1→a4, and m2→a5. Assigning a gender to each category is therefore a test-plan decision rather than a property of the randomization. The gender-balance mitigation in clause 10 of [1] varies the split across tests at one operating point and can be applied using the same table. Under these neutral labels, block 1 for listener 1 is the playlist reproduced in Annex B of [1].

<a id="P029"></a>

An additional verification against the design properties specified in Annex C of [1] was run again on the attached file. All checks pass. The verified properties are:

<a id="P030"></a>

one shared item for each of the 300 point-relevant pairs, per listener;

<a id="P031"></a>

uniform coverage of five listeners over all 750 condition-item cells;

<a id="P032"></a>

## 25 distinct rotations;

<a id="P033"></a>

no same-talker adjacency, block boundaries included;

<a id="P034"></a>

a per-condition mean-position range of 0.54 on a scale of 1 to 30.

<a id="P035"></a>

Proposal

<a id="P036"></a>

Proposal 1: all codec candidates are evaluated in the same test

<a id="P040"></a>

Proposal 2: each operation point is evaluated in a separate test if the number of candidates is larger or equal to X.

<a id="P041"></a>

Note: X might be 13 (TBC).

<a id="P042"></a>

Proposal 3: endorse a controlled laboratory P.800 [5] test as the method for the ULBC selection testing campaign, run by non-candidate laboratories.

<a id="P043"></a>

References

<a id="P044"></a>

S4-261531, "[ULBC-MED] Pair-balanced experiment design for ULBC qualification testing", Fraunhofer IIS, SA4#137-e.

<a id="P045"></a>

S4-261670, "Report from Audio SWG during 3GPP SA4#137-e", SA4 Audio SWG Chair and Vice-Chair, SA4#137-e.

<a id="P046"></a>

S4-261847, "[ULBC-MED] ULBC Design Constraints (ULBC-4) v0.2.1", Fraunhofer IIS (ULBC-4 Editor), SA4#137-e.

<a id="P047"></a>

S4-261771, "[ULBC-MED] ULBC Performance requirements (ULBC-3), v0.1.0", Dolby Laboratories Inc., SA4#137-e.

<a id="P048"></a>

ITU-T Recommendation P.800: "Methods for subjective determination of transmission quality".
