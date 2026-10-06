# S4aA260145 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260145 ULBC Qualification-Phase Testing.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Apple Inc., Samsung Electronics Co., Ltd.

<a id="P001"></a>

Title:    [ULBC-MED] ULBC Qualification-Phase Testing

<a id="P002"></a>

Spec:    ULBC-8a Qualification Test Plan

<a id="P003"></a>

Document for:    Discussion and Agreement

<a id="P004"></a>

Agenda item:    4.8

<a id="P007"></a>

Discussion

<a id="P008"></a>

Whether the ULBC selection includes a qualification phase — i.e., a screening round that reduces the field of 20 candidates to a manageable number (≤5) before the intensive selection tests — has been open since SA4#135-bis-e meeting.

<a id="P010"></a>

This contribution proposes a concrete, fair and statistically sound qualification design so the phase can be judged on its merits. The design assumes on the order of 20 candidate submissions from 20 proponents, each proponent also acting as an independent ITU-T P.800 listening lab, consistent with the distributed-lab model used in prior 3GPP EVS Codec Qualification Phase. A fully worked, tool-reproducible example for 20 candidates, 20 labs and 60 total P.800 DCR tests is provided in the Annex.

<a id="P012"></a>

Qualification Test Plan

<a id="P013"></a>

All the tests are proposed to be based on ITU-T P.800 DCR test methodology. Each of the tests include at least 30 systems or test conditions:

<a id="P014"></a>

## 12 fixed anchor/reference conditions (exact anchors to be agreed), identical in every test:

<a id="P015"></a>

Reference WB or SWB

<a id="P016"></a>

## 5 × WB or SWB-MNRUs at Q-values (e.g., 12, 17, 22, 27, and 32 dB for scale calibration)

<a id="P017"></a>

AMR 12.2

<a id="P018"></a>

AMR-WB 8.85

<a id="P019"></a>

AMR-WB 12.65

<a id="P020"></a>

EVS-WB 7.2

<a id="P021"></a>

EVS-WB 13.2 Channel Aware or EVS-WB 13.2

<a id="P022"></a>

AMR-WB 12.65->12.65 Transcode

<a id="P023"></a>

12 candidate conditions — 6 candidate codecs × 2 operating points (at 1 kbps and 1.4 kbps, exact bitrates TBD)

<a id="P024"></a>

## 6 candidate conditions with AMR-WB transcoding e.g., AMR-WB 12.65 -> ULBC 1kbps or 1.4kbps

<a id="P026"></a>

The anchors are the backbone of the method, as every test carries the same anchors, candidate scores are consistent across tests even though the candidate groupings differ — DCR measures degradation against the reference, not against panel-mates.

<a id="P028"></a>

Experimental Design — Balanced, Randomized, Cross-lab

<a id="P029"></a>

Candidates are distributed across labs as a randomized cross-lab assignment with uniform per-candidate lab coverage and balanced pairwise co-occurrence. In particular,

<a id="P031"></a>

Each candidate is evaluated by exactly 18 different labs — uniform coverage

<a id="P032"></a>

Every pair of candidates appears together approximately the same number of times — no candidate is systematically always paired with strong or weak opponents

<a id="P033"></a>

Cross-lab replication: each candidate gets 18 independent measurements from 18 different labs.

<a id="P034"></a>

## 20 labs, each conduct 3 tests (e.g., clean speech, noisy speech, and frame erasures)

<a id="P035"></a>

Clean speech and Noisy speech tests use non-Channel Aware variants of EVS-WB 13.2; FER tests use Channel Aware 13.2kbps.

<a id="P036"></a>

Randomized, non-fixed groupings — a candidate is grouped with different co-candidates across the labs that test it, so no candidate is locked into a fixed comparison set;

<a id="P037"></a>

Balanced co-occurrence — every pair of candidates shares a panel a near-constant number of times, removing grouping bias;

<a id="P038"></a>

No self-grading — no lab is ever assigned a panel containing its own candidate (enforced structurally).

<a id="P039"></a>

As elaborated in Table 1, each candidate/operating-point seen by ~432 listeners, in multiple languages. If we consider (8 female + 8 male talkers) × 2 sentences = 32 sentence pairs across 18 labs (e.g., 576 sentence pair evaluations per candidate) giving sufficient test coverage and robustness to ML codec testing.

<a id="P040"></a>

Randomization protocol: the design is produced by a to-be-agreed open script (e.g., provided as a qualification deliverable); the random seed is drawn from a public source fixed after the submission deadline, so the groupings are auditable and cannot be gamed. Candidates are blind-coded, and stimuli are centrally processed (or generated with verified reference tooling) so all labs present bit-identical audio. A fully worked instance is given in the Annex.

<a id="P042"></a>

Table 1. Qualification testing - design and capacity summary

<a id="T044"></a>

<a id="T044-R01"></a>
**T044-R01**

- <a id="T044-R01-C01"></a>列 1: Candidates
- <a id="T044-R01-C02"></a>列 2: 20

<a id="T044-R02"></a>
**T044-R02**

- <a id="T044-R02-C01"></a>列 1: Labs
- <a id="T044-R02-C02"></a>列 2: 20 (one per proponent)

<a id="T044-R03"></a>
**T044-R03**

- <a id="T044-R03-C01"></a>列 1: Tests per lab
- <a id="T044-R03-C02"></a>列 2: 3 – one clean speech, one noisy speech, and one frame erasure

<a id="T044-R04"></a>
**T044-R04**

- <a id="T044-R04-C01"></a>列 1: Conditions per test
- <a id="T044-R04-C02"></a>列 2: 30 (12 Ref/Anchor/Legacy + 18 candidates)

<a id="T044-R05"></a>
**T044-R05**

- <a id="T044-R05-C01"></a>列 1: Labs evaluating each candidate
- <a id="T044-R05-C02"></a>列 2: 18

<a id="T044-R06"></a>
**T044-R06**

- <a id="T044-R06-C01"></a>列 1: Number of candidates each lab evaluates
- <a id="T044-R06-C02"></a>列 2: 6 candidates x 3 tests = 18

<a id="T044-R07"></a>
**T044-R07**

- <a id="T044-R07-C01"></a>列 1: Listener scores per candidate / operating point
- <a id="T044-R07-C02"></a>列 2: ~18 labs × 24 listeners ≈ 432

<a id="T044-R08"></a>
**T044-R08**

- <a id="T044-R08-C01"></a>列 1: No self-evaluation
- <a id="T044-R08-C02"></a>列 2: Yes

<a id="T044-R09"></a>
**T044-R09**

- <a id="T044-R09-C01"></a>列 1: No lab repeats a candidate
- <a id="T044-R09-C02"></a>列 2: 6 x 3 = 18 < 19

<a id="P047"></a>

Language Diversity and Evaluation Bias

<a id="P048"></a>

## 4.1. Background

<a id="P050"></a>

Each proponent lab is expected to run its qualification test using listeners and speech material in its own local language. This is a deliberate feature of the distributed-lab model: it ensures codec quality is evaluated across a wide range of languages, talker characteristics, and acoustic environments — important for a codec intended for global deployment. Restricting all labs to a common language corpus would defeat this purpose.

<a id="P052"></a>

However, the distribution of declared proponents is not language-uniform. Of the 19 labs that have declared interest, 7 operate in Mandarin Chinese, 4 in English, 2 in French, 2 in Japanese, and one each in Swedish, Finnish, German, Dutch, and Korean. Without deliberate countermeasures, the natural result of a purely random assignment is that some candidates — particularly those submitted by non-Mandarin proponents — could be systematically evaluated by a disproportionate number of Mandarin-language labs, and vice versa. This would introduce a language-group bias into the qualification scores that is unrelated to codec quality.

<a id="P054"></a>

## 4.2. The problem is not language diversity itself — it is language concentration

<a id="P056"></a>

The goal is not to eliminate language variation across labs evaluating a given candidate. On the contrary, each candidate should be evaluated by a spread of languages, reflecting the intended global use of the codec. The problem arises specifically when one language group is over-represented among the labs evaluating a particular candidate in a particular test type. If, for example, all 6 labs evaluating a candidate in the CS condition happen to be Mandarin-language labs, that candidate's CS score reflects only Mandarin listener judgements — an unrepresentative sample.

<a id="P058"></a>

## 4.3. Language-stratified assignment

<a id="P060"></a>

The randomization algorithm enforces a language-balance constraint as part of the cost function minimized during design generation. For each candidate and each test type (CS, NS, FER), the number of evaluating labs from any single language group is capped at its proportional share in the overall lab pool, rounded up:

<a id="P062"></a>

- Mandarin (7/19 of pool): cap of 3 labs per candidate per test type

<a id="P063"></a>

- English (4/19): cap of 2 labs per candidate per test type

<a id="P064"></a>

- All other languages (1–2/19 each): cap of 2 labs per candidate per test type

<a id="P066"></a>

This ensures no candidate is systematically over- or under-evaluated in any one language, while preserving the full use of each lab's local-language material and listener panels. The constraint is enforced simultaneously with the co-occurrence balance and per-type coverage constraints already in the design.

<a id="P068"></a>

## 4.4. Verified in the Annex example

<a id="P070"></a>

The worked example in Annex A.4 demonstrates that the language-stratified assignment achieves the cap for all 20 candidates across all three test types, with Mandarin representation ranging from 1 to 3 labs per candidate per test type (cap: 3), and no other language group exceeding its proportional cap.

<a id="P073"></a>

Scoring and Normalization

<a id="P074"></a>

Per condition: DCR DMOS on the 5-point degradation scale, averaged over listeners in each lab. The recommendation is to use 8 female talkers and 8 male talkers, and 2 sentence-pairs per talker, split into 2 panels in each test in order provide sufficient coverage, generalization and diversity which may be necessary when testing ML codecs.

<a id="P076"></a>

Cross-lab calibration: All labs shall use the same P.800 DCR test setup (e.g., headphone consistency, hoth noise preparation), following the process adopted in the EVS Qualification phase.  The expectation is that every proponent has the capability to conduct P.800 DCR listening tests in house. If this is not the case, the proponents can also contract individually external labs for testing. Crowd-source testing should not be used.

<a id="P078"></a>

Objective metrics are not used for the pass/fail decision (subjective DCR is the reference), consistent with TR 26.940 clause 9.1.4.3.

<a id="P082"></a>

Fairness Safeguards

<a id="P083"></a>

Some safeguards to make sure there is no bias in the qualification testing:

<a id="P084"></a>

No lab grades its own candidate (structural).

<a id="P085"></a>

Blind-coded candidates; identical anchor systems in every test; centrally verified stimuli.

<a id="P086"></a>

Balanced co-occurrence — no candidate systematically paired with, or isolated from, any other.

<a id="P087"></a>

Public post-deadline randomization seed + fixed open tooling — auditable, non-manipulable.

<a id="P089"></a>

Proposals

<a id="T091"></a>

<a id="T091-R01"></a>
**T091-R01**

- <a id="T091-R01-C01"></a>列 1: #
- <a id="T091-R01-C02"></a>列 2: Proposal

<a id="T091-R02"></a>
**T091-R02**

- <a id="T091-R02-C01"></a>列 1: P1
- <a id="T091-R02-C02"></a>列 2: Adopt a qualification phase that screens the candidate field to ≤5 before the selection phase.

<a id="T091-R03"></a>
**T091-R03**

- <a id="T091-R03-C01"></a>列 1: P2
- <a id="T091-R03-C02"></a>列 2: Qualification tests are P.800 DCR experiments of 6 candidates × 2 operating points.

<a id="T091-R04"></a>
**T091-R04**

- <a id="T091-R04-C01"></a>列 1: P3
- <a id="T091-R04-C02"></a>列 2: Distribute candidates by a balanced, randomized, cross-lab design — each candidate at 18 labs, balanced co-occurrence, no self-grading, blind-coded, public post-deadline seed.

<a id="T091-R05"></a>
**T091-R05**

- <a id="T091-R05-C01"></a>列 1: P4
- <a id="T091-R05-C02"></a>列 2: Upon agreement of the qualification phase, provide the open design/randomization tool as a qualification deliverable.

<a id="T091-R06"></a>
**T091-R06**

- <a id="T091-R06-C01"></a>列 1: P5
- <a id="T091-R06-C02"></a>列 2: Each lab shall conduct its qualification tests using its own local-language speech material and listener panels, preserving evaluation diversity across languages.

<a id="T091-R07"></a>
**T091-R07**

- <a id="T091-R07-C01"></a>列 1: P6
- <a id="T091-R07-C02"></a>列 2: The randomization algorithm shall enforce a language-balance constraint limiting the number of same-language labs evaluating any single candidate in any single test type to the proportional share of that language group in the overall lab pool (rounded up), ensuring no candidate is systematically concentrated in any one language group.

<a id="P093"></a>

It is proposed to agree to qualification testing phase P1 and the framework P2–P7.

<a id="P094"></a>

It is proposed to include Clauses 2-7 in the ULBC-8a Qualification Test Plan Permanent Document along with the example in Annex A.

<a id="P096"></a>

Annex A (informative):  Worked example — 20 candidates, 20 labs, 60 tests

<a id="P098"></a>

Generated by an open tool with seed 2026 (illustrative); the tool will be shared upon agreement of the phase. The design is a pure function of (parameters, seed) — any party can independently verify the properties in A.4 from first principles.

<a id="P099"></a>

C01–C20 = candidates from 20 proponents;

<a id="P100"></a>

L01–L20 = labs;

<a id="P101"></a>

E01–E60 = tests.

<a id="P102"></a>

In this illustration proponent-i owns C(i) and runs lab L(i); in the real run, candidate codes are decoupled from lab identities, and the seed is drawn post-deadline. Running the tool with the same seed reproduces this Annex exactly.

<a id="P105"></a>

A.1 One test in full — E01 (as the lab receives it, blind-coded)

<a id="P107"></a>

Host lab: L01   |   Panel candidates: C02, C08, C10, C13, C15, C16

<a id="T109"></a>

<a id="T109-R01"></a>
**T109-R01**

- <a id="T109-R01-C01"></a>列 1（跨列:4）: E01 — CS test, host lab: L01 | 30 conditions (12 anchor + 6×Rate1 + 6×Rate2) | Note: in the actual test, order is randomized per listener session.

<a id="T109-R02"></a>
**T109-R02**

- <a id="T109-R02-C01"></a>列 1: S-code
- <a id="T109-R02-C02"></a>列 2: Condition
- <a id="T109-R02-C03"></a>列 3: Category
- <a id="T109-R02-C04"></a>列 4: Op. point

<a id="T109-R03"></a>
**T109-R03**

- <a id="T109-R03-C01"></a>列 1: S01
- <a id="T109-R03-C02"></a>列 2: Ref-WB or Ref-SWB
- <a id="T109-R03-C03"></a>列 3: Anchor/Ref
- <a id="T109-R03-C04"></a>列 4: —

<a id="T109-R04"></a>
**T109-R04**

- <a id="T109-R04-C01"></a>列 1: S02
- <a id="T109-R04-C02"></a>列 2: MNRU-Q12
- <a id="T109-R04-C03"></a>列 3: Anchor/Ref
- <a id="T109-R04-C04"></a>列 4: —

<a id="T109-R05"></a>
**T109-R05**

- <a id="T109-R05-C01"></a>列 1: S03
- <a id="T109-R05-C02"></a>列 2: MNRU-Q17
- <a id="T109-R05-C03"></a>列 3: Anchor/Ref
- <a id="T109-R05-C04"></a>列 4: —

<a id="T109-R06"></a>
**T109-R06**

- <a id="T109-R06-C01"></a>列 1: S04
- <a id="T109-R06-C02"></a>列 2: MNRU-Q22
- <a id="T109-R06-C03"></a>列 3: Anchor/Ref
- <a id="T109-R06-C04"></a>列 4: —

<a id="T109-R07"></a>
**T109-R07**

- <a id="T109-R07-C01"></a>列 1: S05
- <a id="T109-R07-C02"></a>列 2: MNRU-Q27
- <a id="T109-R07-C03"></a>列 3: Anchor/Ref
- <a id="T109-R07-C04"></a>列 4: —

<a id="T109-R08"></a>
**T109-R08**

- <a id="T109-R08-C01"></a>列 1: S06
- <a id="T109-R08-C02"></a>列 2: MNRU-Q32
- <a id="T109-R08-C03"></a>列 3: Anchor/Ref
- <a id="T109-R08-C04"></a>列 4: —

<a id="T109-R09"></a>
**T109-R09**

- <a id="T109-R09-C01"></a>列 1: S07
- <a id="T109-R09-C02"></a>列 2: AMR-12.2
- <a id="T109-R09-C03"></a>列 3: Anchor/Ref
- <a id="T109-R09-C04"></a>列 4: —

<a id="T109-R10"></a>
**T109-R10**

- <a id="T109-R10-C01"></a>列 1: S08
- <a id="T109-R10-C02"></a>列 2: AMR-WB-8.85
- <a id="T109-R10-C03"></a>列 3: Anchor/Ref
- <a id="T109-R10-C04"></a>列 4: —

<a id="T109-R11"></a>
**T109-R11**

- <a id="T109-R11-C01"></a>列 1: S09
- <a id="T109-R11-C02"></a>列 2: AMR-WB-12.65
- <a id="T109-R11-C03"></a>列 3: Anchor/Ref
- <a id="T109-R11-C04"></a>列 4: —

<a id="T109-R12"></a>
**T109-R12**

- <a id="T109-R12-C01"></a>列 1: S10
- <a id="T109-R12-C02"></a>列 2: EVS-WB-7.2
- <a id="T109-R12-C03"></a>列 3: Anchor/Ref
- <a id="T109-R12-C04"></a>列 4: —

<a id="T109-R13"></a>
**T109-R13**

- <a id="T109-R13-C01"></a>列 1: S11
- <a id="T109-R13-C02"></a>列 2: EVS-WB-13.2
- <a id="T109-R13-C03"></a>列 3: Anchor/Ref
- <a id="T109-R13-C04"></a>列 4: —

<a id="T109-R14"></a>
**T109-R14**

- <a id="T109-R14-C01"></a>列 1: S12
- <a id="T109-R14-C02"></a>列 2: AMR-WB 12.65->12.65
- <a id="T109-R14-C03"></a>列 3: Anchor/Ref
- <a id="T109-R14-C04"></a>列 4: —

<a id="T109-R15"></a>
**T109-R15**

- <a id="T109-R15-C01"></a>列 1: S13
- <a id="T109-R15-C02"></a>列 2: C02 @ Rate1 1kbps
- <a id="T109-R15-C03"></a>列 3: Candidate
- <a id="T109-R15-C04"></a>列 4: 1kbps

<a id="T109-R16"></a>
**T109-R16**

- <a id="T109-R16-C01"></a>列 1: S14
- <a id="T109-R16-C02"></a>列 2: C08 @ Rate1 1kbps
- <a id="T109-R16-C03"></a>列 3: Candidate
- <a id="T109-R16-C04"></a>列 4: 1kbps

<a id="T109-R17"></a>
**T109-R17**

- <a id="T109-R17-C01"></a>列 1: S15
- <a id="T109-R17-C02"></a>列 2: C10 @ Rate1 1kbps
- <a id="T109-R17-C03"></a>列 3: Candidate
- <a id="T109-R17-C04"></a>列 4: 1kbps

<a id="T109-R18"></a>
**T109-R18**

- <a id="T109-R18-C01"></a>列 1: S16
- <a id="T109-R18-C02"></a>列 2: C13 @ Rate1 1kbps
- <a id="T109-R18-C03"></a>列 3: Candidate
- <a id="T109-R18-C04"></a>列 4: 1kbps

<a id="T109-R19"></a>
**T109-R19**

- <a id="T109-R19-C01"></a>列 1: S17
- <a id="T109-R19-C02"></a>列 2: C15 @ Rate1 1kbps
- <a id="T109-R19-C03"></a>列 3: Candidate
- <a id="T109-R19-C04"></a>列 4: 1kbps

<a id="T109-R20"></a>
**T109-R20**

- <a id="T109-R20-C01"></a>列 1: S18
- <a id="T109-R20-C02"></a>列 2: C16 @ Rate1 1kbps
- <a id="T109-R20-C03"></a>列 3: Candidate
- <a id="T109-R20-C04"></a>列 4: 1kbps

<a id="T109-R21"></a>
**T109-R21**

- <a id="T109-R21-C01"></a>列 1: S19
- <a id="T109-R21-C02"></a>列 2: C02 @ Rate2 1.4kbps
- <a id="T109-R21-C03"></a>列 3: Candidate
- <a id="T109-R21-C04"></a>列 4: 1.4kbps

<a id="T109-R22"></a>
**T109-R22**

- <a id="T109-R22-C01"></a>列 1: S20
- <a id="T109-R22-C02"></a>列 2: C08 @ Rate2 1.4kbps
- <a id="T109-R22-C03"></a>列 3: Candidate
- <a id="T109-R22-C04"></a>列 4: 1.4kbps

<a id="T109-R23"></a>
**T109-R23**

- <a id="T109-R23-C01"></a>列 1: S21
- <a id="T109-R23-C02"></a>列 2: C10 @ Rate2 1.4kbps
- <a id="T109-R23-C03"></a>列 3: Candidate
- <a id="T109-R23-C04"></a>列 4: 1.4kbps

<a id="T109-R24"></a>
**T109-R24**

- <a id="T109-R24-C01"></a>列 1: S22
- <a id="T109-R24-C02"></a>列 2: C13 @ Rate2 1.4kbps
- <a id="T109-R24-C03"></a>列 3: Candidate
- <a id="T109-R24-C04"></a>列 4: 1.4kbps

<a id="T109-R25"></a>
**T109-R25**

- <a id="T109-R25-C01"></a>列 1: S23
- <a id="T109-R25-C02"></a>列 2: C15 @ Rate2 1.4kbps
- <a id="T109-R25-C03"></a>列 3: Candidate
- <a id="T109-R25-C04"></a>列 4: 1.4kbps

<a id="T109-R26"></a>
**T109-R26**

- <a id="T109-R26-C01"></a>列 1: S24
- <a id="T109-R26-C02"></a>列 2: C16 @ Rate2 1.4kbps
- <a id="T109-R26-C03"></a>列 3: Candidate
- <a id="T109-R26-C04"></a>列 4: 1.4kbps

<a id="T109-R27"></a>
**T109-R27**

- <a id="T109-R27-C01"></a>列 1: S25
- <a id="T109-R27-C02"></a>列 2: C02 @ AMR-WB 12.65 -> ULBC
- <a id="T109-R27-C03"></a>列 3: Candidate
- <a id="T109-R27-C04"></a>列 4: 1 or 1.4 kbps

<a id="T109-R28"></a>
**T109-R28**

- <a id="T109-R28-C01"></a>列 1: S26
- <a id="T109-R28-C02"></a>列 2: C08 @ AMR-WB 12.65 -> ULBC
- <a id="T109-R28-C03"></a>列 3: Candidate
- <a id="T109-R28-C04"></a>列 4: 1 or 1.4 kbps

<a id="T109-R29"></a>
**T109-R29**

- <a id="T109-R29-C01"></a>列 1: S27
- <a id="T109-R29-C02"></a>列 2: C10 @ AMR-WB 12.65 -> ULBC
- <a id="T109-R29-C03"></a>列 3: Candidate
- <a id="T109-R29-C04"></a>列 4: 1 or 1.4 kbps

<a id="T109-R30"></a>
**T109-R30**

- <a id="T109-R30-C01"></a>列 1: S28
- <a id="T109-R30-C02"></a>列 2: C13 @ AMR-WB 12.65 -> ULBC
- <a id="T109-R30-C03"></a>列 3: Candidate
- <a id="T109-R30-C04"></a>列 4: 1 or 1.4 kbps

<a id="T109-R31"></a>
**T109-R31**

- <a id="T109-R31-C01"></a>列 1: S29
- <a id="T109-R31-C02"></a>列 2: C15 @ AMR-WB 12.65 -> ULBC
- <a id="T109-R31-C03"></a>列 3: Candidate
- <a id="T109-R31-C04"></a>列 4: 1 or 1.4 kbps

<a id="T109-R32"></a>
**T109-R32**

- <a id="T109-R32-C01"></a>列 1: S30
- <a id="T109-R32-C02"></a>列 2: C16 @ AMR-WB 12.65 -> ULBC
- <a id="T109-R32-C03"></a>列 3: Candidate
- <a id="T109-R32-C04"></a>列 4: 1 or 1.4 kbps

<a id="P112"></a>

A.2 Full test roster (E01–E60)

<a id="T114"></a>

<a id="T114-R01"></a>
**T114-R01**

- <a id="T114-R01-C01"></a>列 1: Test
- <a id="T114-R01-C02"></a>列 2: Type
- <a id="T114-R01-C03"></a>列 3: Lab
- <a id="T114-R01-C04"></a>列 4: C1
- <a id="T114-R01-C05"></a>列 5: C2
- <a id="T114-R01-C06"></a>列 6: C3
- <a id="T114-R01-C07"></a>列 7: C4
- <a id="T114-R01-C08"></a>列 8: C5
- <a id="T114-R01-C09"></a>列 9: C6

<a id="T114-R02"></a>
**T114-R02**

- <a id="T114-R02-C01"></a>列 1: E01
- <a id="T114-R02-C02"></a>列 2: CS
- <a id="T114-R02-C03"></a>列 3: L01
- <a id="T114-R02-C04"></a>列 4: C02
- <a id="T114-R02-C05"></a>列 5: C08
- <a id="T114-R02-C06"></a>列 6: C10
- <a id="T114-R02-C07"></a>列 7: C13
- <a id="T114-R02-C08"></a>列 8: C15
- <a id="T114-R02-C09"></a>列 9: C16

<a id="T114-R03"></a>
**T114-R03**

- <a id="T114-R03-C01"></a>列 1: E02
- <a id="T114-R03-C02"></a>列 2: NS
- <a id="T114-R03-C03"></a>列 3: L01
- <a id="T114-R03-C04"></a>列 4: C03
- <a id="T114-R03-C05"></a>列 5: C05
- <a id="T114-R03-C06"></a>列 6: C07
- <a id="T114-R03-C07"></a>列 7: C09
- <a id="T114-R03-C08"></a>列 8: C11
- <a id="T114-R03-C09"></a>列 9: C18

<a id="T114-R04"></a>
**T114-R04**

- <a id="T114-R04-C01"></a>列 1: E03
- <a id="T114-R04-C02"></a>列 2: FER
- <a id="T114-R04-C03"></a>列 3: L01
- <a id="T114-R04-C04"></a>列 4: C04
- <a id="T114-R04-C05"></a>列 5: C06
- <a id="T114-R04-C06"></a>列 6: C12
- <a id="T114-R04-C07"></a>列 7: C14
- <a id="T114-R04-C08"></a>列 8: C17
- <a id="T114-R04-C09"></a>列 9: C20

<a id="T114-R05"></a>
**T114-R05**

- <a id="T114-R05-C01"></a>列 1: E04
- <a id="T114-R05-C02"></a>列 2: CS
- <a id="T114-R05-C03"></a>列 3: L02
- <a id="T114-R05-C04"></a>列 4: C05
- <a id="T114-R05-C05"></a>列 5: C11
- <a id="T114-R05-C06"></a>列 6: C14
- <a id="T114-R05-C07"></a>列 7: C15
- <a id="T114-R05-C08"></a>列 8: C19
- <a id="T114-R05-C09"></a>列 9: C20

<a id="T114-R06"></a>
**T114-R06**

- <a id="T114-R06-C01"></a>列 1: E05
- <a id="T114-R06-C02"></a>列 2: NS
- <a id="T114-R06-C03"></a>列 3: L02
- <a id="T114-R06-C04"></a>列 4: C03
- <a id="T114-R06-C05"></a>列 5: C06
- <a id="T114-R06-C06"></a>列 6: C09
- <a id="T114-R06-C07"></a>列 7: C12
- <a id="T114-R06-C08"></a>列 8: C16
- <a id="T114-R06-C09"></a>列 9: C17

<a id="T114-R07"></a>
**T114-R07**

- <a id="T114-R07-C01"></a>列 1: E06
- <a id="T114-R07-C02"></a>列 2: FER
- <a id="T114-R07-C03"></a>列 3: L02
- <a id="T114-R07-C04"></a>列 4: C01
- <a id="T114-R07-C05"></a>列 5: C04
- <a id="T114-R07-C06"></a>列 6: C08
- <a id="T114-R07-C07"></a>列 7: C10
- <a id="T114-R07-C08"></a>列 8: C13
- <a id="T114-R07-C09"></a>列 9: C18

<a id="T114-R08"></a>
**T114-R08**

- <a id="T114-R08-C01"></a>列 1: E07
- <a id="T114-R08-C02"></a>列 2: CS
- <a id="T114-R08-C03"></a>列 3: L03
- <a id="T114-R08-C04"></a>列 4: C01
- <a id="T114-R08-C05"></a>列 5: C07
- <a id="T114-R08-C06"></a>列 6: C08
- <a id="T114-R08-C07"></a>列 7: C12
- <a id="T114-R08-C08"></a>列 8: C13
- <a id="T114-R08-C09"></a>列 9: C20

<a id="T114-R09"></a>
**T114-R09**

- <a id="T114-R09-C01"></a>列 1: E08
- <a id="T114-R09-C02"></a>列 2: NS
- <a id="T114-R09-C03"></a>列 3: L03
- <a id="T114-R09-C04"></a>列 4: C02
- <a id="T114-R09-C05"></a>列 5: C05
- <a id="T114-R09-C06"></a>列 6: C10
- <a id="T114-R09-C07"></a>列 7: C11
- <a id="T114-R09-C08"></a>列 8: C17
- <a id="T114-R09-C09"></a>列 9: C19

<a id="T114-R10"></a>
**T114-R10**

- <a id="T114-R10-C01"></a>列 1: E09
- <a id="T114-R10-C02"></a>列 2: FER
- <a id="T114-R10-C03"></a>列 3: L03
- <a id="T114-R10-C04"></a>列 4: C04
- <a id="T114-R10-C05"></a>列 5: C09
- <a id="T114-R10-C06"></a>列 6: C14
- <a id="T114-R10-C07"></a>列 7: C15
- <a id="T114-R10-C08"></a>列 8: C16
- <a id="T114-R10-C09"></a>列 9: C18

<a id="T114-R11"></a>
**T114-R11**

- <a id="T114-R11-C01"></a>列 1: E10
- <a id="T114-R11-C02"></a>列 2: CS
- <a id="T114-R11-C03"></a>列 3: L04
- <a id="T114-R11-C04"></a>列 4: C03
- <a id="T114-R11-C05"></a>列 5: C10
- <a id="T114-R11-C06"></a>列 6: C15
- <a id="T114-R11-C07"></a>列 7: C16
- <a id="T114-R11-C08"></a>列 8: C17
- <a id="T114-R11-C09"></a>列 9: C18

<a id="T114-R12"></a>
**T114-R12**

- <a id="T114-R12-C01"></a>列 1: E11
- <a id="T114-R12-C02"></a>列 2: NS
- <a id="T114-R12-C03"></a>列 3: L04
- <a id="T114-R12-C04"></a>列 4: C01
- <a id="T114-R12-C05"></a>列 5: C07
- <a id="T114-R12-C06"></a>列 6: C12
- <a id="T114-R12-C07"></a>列 7: C13
- <a id="T114-R12-C08"></a>列 8: C19
- <a id="T114-R12-C09"></a>列 9: C20

<a id="T114-R13"></a>
**T114-R13**

- <a id="T114-R13-C01"></a>列 1: E12
- <a id="T114-R13-C02"></a>列 2: FER
- <a id="T114-R13-C03"></a>列 3: L04
- <a id="T114-R13-C04"></a>列 4: C05
- <a id="T114-R13-C05"></a>列 5: C06
- <a id="T114-R13-C06"></a>列 6: C08
- <a id="T114-R13-C07"></a>列 7: C09
- <a id="T114-R13-C08"></a>列 8: C11
- <a id="T114-R13-C09"></a>列 9: C14

<a id="T114-R14"></a>
**T114-R14**

- <a id="T114-R14-C01"></a>列 1: E13
- <a id="T114-R14-C02"></a>列 2: CS
- <a id="T114-R14-C03"></a>列 3: L05
- <a id="T114-R14-C04"></a>列 4: C08
- <a id="T114-R14-C05"></a>列 5: C09
- <a id="T114-R14-C06"></a>列 6: C14
- <a id="T114-R14-C07"></a>列 7: C17
- <a id="T114-R14-C08"></a>列 8: C18
- <a id="T114-R14-C09"></a>列 9: C19

<a id="T114-R15"></a>
**T114-R15**

- <a id="T114-R15-C01"></a>列 1: E14
- <a id="T114-R15-C02"></a>列 2: NS
- <a id="T114-R15-C03"></a>列 3: L05
- <a id="T114-R15-C04"></a>列 4: C01
- <a id="T114-R15-C05"></a>列 5: C03
- <a id="T114-R15-C06"></a>列 6: C06
- <a id="T114-R15-C07"></a>列 7: C11
- <a id="T114-R15-C08"></a>列 8: C13
- <a id="T114-R15-C09"></a>列 9: C16

<a id="T114-R16"></a>
**T114-R16**

- <a id="T114-R16-C01"></a>列 1: E15
- <a id="T114-R16-C02"></a>列 2: FER
- <a id="T114-R16-C03"></a>列 3: L05
- <a id="T114-R16-C04"></a>列 4: C02
- <a id="T114-R16-C05"></a>列 5: C04
- <a id="T114-R16-C06"></a>列 6: C07
- <a id="T114-R16-C07"></a>列 7: C10
- <a id="T114-R16-C08"></a>列 8: C15
- <a id="T114-R16-C09"></a>列 9: C20

<a id="T114-R17"></a>
**T114-R17**

- <a id="T114-R17-C01"></a>列 1: E16
- <a id="T114-R17-C02"></a>列 2: CS
- <a id="T114-R17-C03"></a>列 3: L06
- <a id="T114-R17-C04"></a>列 4: C04
- <a id="T114-R17-C05"></a>列 5: C07
- <a id="T114-R17-C06"></a>列 6: C08
- <a id="T114-R17-C07"></a>列 7: C11
- <a id="T114-R17-C08"></a>列 8: C12
- <a id="T114-R17-C09"></a>列 9: C15

<a id="T114-R18"></a>
**T114-R18**

- <a id="T114-R18-C01"></a>列 1: E17
- <a id="T114-R18-C02"></a>列 2: NS
- <a id="T114-R18-C03"></a>列 3: L06
- <a id="T114-R18-C04"></a>列 4: C10
- <a id="T114-R18-C05"></a>列 5: C14
- <a id="T114-R18-C06"></a>列 6: C16
- <a id="T114-R18-C07"></a>列 7: C18
- <a id="T114-R18-C08"></a>列 8: C19
- <a id="T114-R18-C09"></a>列 9: C20

<a id="T114-R19"></a>
**T114-R19**

- <a id="T114-R19-C01"></a>列 1: E18
- <a id="T114-R19-C02"></a>列 2: FER
- <a id="T114-R19-C03"></a>列 3: L06
- <a id="T114-R19-C04"></a>列 4: C01
- <a id="T114-R19-C05"></a>列 5: C02
- <a id="T114-R19-C06"></a>列 6: C05
- <a id="T114-R19-C07"></a>列 7: C09
- <a id="T114-R19-C08"></a>列 8: C13
- <a id="T114-R19-C09"></a>列 9: C17

<a id="T114-R20"></a>
**T114-R20**

- <a id="T114-R20-C01"></a>列 1: E19
- <a id="T114-R20-C02"></a>列 2: CS
- <a id="T114-R20-C03"></a>列 3: L07
- <a id="T114-R20-C04"></a>列 4: C03
- <a id="T114-R20-C05"></a>列 5: C06
- <a id="T114-R20-C06"></a>列 6: C10
- <a id="T114-R20-C07"></a>列 7: C12
- <a id="T114-R20-C08"></a>列 8: C14
- <a id="T114-R20-C09"></a>列 9: C15

<a id="T114-R21"></a>
**T114-R21**

- <a id="T114-R21-C01"></a>列 1: E20
- <a id="T114-R21-C02"></a>列 2: NS
- <a id="T114-R21-C03"></a>列 3: L07
- <a id="T114-R21-C04"></a>列 4: C04
- <a id="T114-R21-C05"></a>列 5: C11
- <a id="T114-R21-C06"></a>列 6: C13
- <a id="T114-R21-C07"></a>列 7: C17
- <a id="T114-R21-C08"></a>列 8: C18
- <a id="T114-R21-C09"></a>列 9: C20

<a id="T114-R22"></a>
**T114-R22**

- <a id="T114-R22-C01"></a>列 1: E21
- <a id="T114-R22-C02"></a>列 2: FER
- <a id="T114-R22-C03"></a>列 3: L07
- <a id="T114-R22-C04"></a>列 4: C01
- <a id="T114-R22-C05"></a>列 5: C02
- <a id="T114-R22-C06"></a>列 6: C08
- <a id="T114-R22-C07"></a>列 7: C09
- <a id="T114-R22-C08"></a>列 8: C16
- <a id="T114-R22-C09"></a>列 9: C19

<a id="T114-R23"></a>
**T114-R23**

- <a id="T114-R23-C01"></a>列 1: E22
- <a id="T114-R23-C02"></a>列 2: CS
- <a id="T114-R23-C03"></a>列 3: L08
- <a id="T114-R23-C04"></a>列 4: C01
- <a id="T114-R23-C05"></a>列 5: C03
- <a id="T114-R23-C06"></a>列 6: C09
- <a id="T114-R23-C07"></a>列 7: C14
- <a id="T114-R23-C08"></a>列 8: C18
- <a id="T114-R23-C09"></a>列 9: C20

<a id="T114-R24"></a>
**T114-R24**

- <a id="T114-R24-C01"></a>列 1: E23
- <a id="T114-R24-C02"></a>列 2: NS
- <a id="T114-R24-C03"></a>列 3: L08
- <a id="T114-R24-C04"></a>列 4: C02
- <a id="T114-R24-C05"></a>列 5: C04
- <a id="T114-R24-C06"></a>列 6: C12
- <a id="T114-R24-C07"></a>列 7: C13
- <a id="T114-R24-C08"></a>列 8: C15
- <a id="T114-R24-C09"></a>列 9: C19

<a id="T114-R25"></a>
**T114-R25**

- <a id="T114-R25-C01"></a>列 1: E24
- <a id="T114-R25-C02"></a>列 2: FER
- <a id="T114-R25-C03"></a>列 3: L08
- <a id="T114-R25-C04"></a>列 4: C05
- <a id="T114-R25-C05"></a>列 5: C06
- <a id="T114-R25-C06"></a>列 6: C07
- <a id="T114-R25-C07"></a>列 7: C10
- <a id="T114-R25-C08"></a>列 8: C11
- <a id="T114-R25-C09"></a>列 9: C16

<a id="T114-R26"></a>
**T114-R26**

- <a id="T114-R26-C01"></a>列 1: E25
- <a id="T114-R26-C02"></a>列 2: CS
- <a id="T114-R26-C03"></a>列 3: L09
- <a id="T114-R26-C04"></a>列 4: C06
- <a id="T114-R26-C05"></a>列 5: C08
- <a id="T114-R26-C06"></a>列 6: C12
- <a id="T114-R26-C07"></a>列 7: C16
- <a id="T114-R26-C08"></a>列 8: C17
- <a id="T114-R26-C09"></a>列 9: C20

<a id="T114-R27"></a>
**T114-R27**

- <a id="T114-R27-C01"></a>列 1: E26
- <a id="T114-R27-C02"></a>列 2: NS
- <a id="T114-R27-C03"></a>列 3: L09
- <a id="T114-R27-C04"></a>列 4: C01
- <a id="T114-R27-C05"></a>列 5: C02
- <a id="T114-R27-C06"></a>列 6: C05
- <a id="T114-R27-C07"></a>列 7: C07
- <a id="T114-R27-C08"></a>列 8: C15
- <a id="T114-R27-C09"></a>列 9: C18

<a id="T114-R28"></a>
**T114-R28**

- <a id="T114-R28-C01"></a>列 1: E27
- <a id="T114-R28-C02"></a>列 2: FER
- <a id="T114-R28-C03"></a>列 3: L09
- <a id="T114-R28-C04"></a>列 4: C03
- <a id="T114-R28-C05"></a>列 5: C10
- <a id="T114-R28-C06"></a>列 6: C11
- <a id="T114-R28-C07"></a>列 7: C13
- <a id="T114-R28-C08"></a>列 8: C14
- <a id="T114-R28-C09"></a>列 9: C19

<a id="T114-R29"></a>
**T114-R29**

- <a id="T114-R29-C01"></a>列 1: E28
- <a id="T114-R29-C02"></a>列 2: CS
- <a id="T114-R29-C03"></a>列 3: L10
- <a id="T114-R29-C04"></a>列 4: C01
- <a id="T114-R29-C05"></a>列 5: C02
- <a id="T114-R29-C06"></a>列 6: C03
- <a id="T114-R29-C07"></a>列 7: C04
- <a id="T114-R29-C08"></a>列 8: C12
- <a id="T114-R29-C09"></a>列 9: C19

<a id="T114-R30"></a>
**T114-R30**

- <a id="T114-R30-C01"></a>列 1: E29
- <a id="T114-R30-C02"></a>列 2: NS
- <a id="T114-R30-C03"></a>列 3: L10
- <a id="T114-R30-C04"></a>列 4: C05
- <a id="T114-R30-C05"></a>列 5: C08
- <a id="T114-R30-C06"></a>列 6: C16
- <a id="T114-R30-C07"></a>列 7: C17
- <a id="T114-R30-C08"></a>列 8: C18
- <a id="T114-R30-C09"></a>列 9: C20

<a id="T114-R31"></a>
**T114-R31**

- <a id="T114-R31-C01"></a>列 1: E30
- <a id="T114-R31-C02"></a>列 2: FER
- <a id="T114-R31-C03"></a>列 3: L10
- <a id="T114-R31-C04"></a>列 4: C06
- <a id="T114-R31-C05"></a>列 5: C07
- <a id="T114-R31-C06"></a>列 6: C09
- <a id="T114-R31-C07"></a>列 7: C11
- <a id="T114-R31-C08"></a>列 8: C13
- <a id="T114-R31-C09"></a>列 9: C15

<a id="T114-R32"></a>
**T114-R32**

- <a id="T114-R32-C01"></a>列 1: E31
- <a id="T114-R32-C02"></a>列 2: CS
- <a id="T114-R32-C03"></a>列 3: L11
- <a id="T114-R32-C04"></a>列 4: C06
- <a id="T114-R32-C05"></a>列 5: C09
- <a id="T114-R32-C06"></a>列 6: C13
- <a id="T114-R32-C07"></a>列 7: C16
- <a id="T114-R32-C08"></a>列 8: C19
- <a id="T114-R32-C09"></a>列 9: C20

<a id="T114-R33"></a>
**T114-R33**

- <a id="T114-R33-C01"></a>列 1: E32
- <a id="T114-R33-C02"></a>列 2: NS
- <a id="T114-R33-C03"></a>列 3: L11
- <a id="T114-R33-C04"></a>列 4: C01
- <a id="T114-R33-C05"></a>列 5: C03
- <a id="T114-R33-C06"></a>列 6: C04
- <a id="T114-R33-C07"></a>列 7: C07
- <a id="T114-R33-C08"></a>列 8: C14
- <a id="T114-R33-C09"></a>列 9: C17

<a id="T114-R34"></a>
**T114-R34**

- <a id="T114-R34-C01"></a>列 1: E33
- <a id="T114-R34-C02"></a>列 2: FER
- <a id="T114-R34-C03"></a>列 3: L11
- <a id="T114-R34-C04"></a>列 4: C02
- <a id="T114-R34-C05"></a>列 5: C05
- <a id="T114-R34-C06"></a>列 6: C08
- <a id="T114-R34-C07"></a>列 7: C10
- <a id="T114-R34-C08"></a>列 8: C12
- <a id="T114-R34-C09"></a>列 9: C18

<a id="T114-R35"></a>
**T114-R35**

- <a id="T114-R35-C01"></a>列 1: E34
- <a id="T114-R35-C02"></a>列 2: CS
- <a id="T114-R35-C03"></a>列 3: L12
- <a id="T114-R35-C04"></a>列 4: C01
- <a id="T114-R35-C05"></a>列 5: C05
- <a id="T114-R35-C06"></a>列 6: C06
- <a id="T114-R35-C07"></a>列 7: C07
- <a id="T114-R35-C08"></a>列 8: C15
- <a id="T114-R35-C09"></a>列 9: C17

<a id="T114-R36"></a>
**T114-R36**

- <a id="T114-R36-C01"></a>列 1: E35
- <a id="T114-R36-C02"></a>列 2: NS
- <a id="T114-R36-C03"></a>列 3: L12
- <a id="T114-R36-C04"></a>列 4: C02
- <a id="T114-R36-C05"></a>列 5: C04
- <a id="T114-R36-C06"></a>列 6: C10
- <a id="T114-R36-C07"></a>列 7: C13
- <a id="T114-R36-C08"></a>列 8: C14
- <a id="T114-R36-C09"></a>列 9: C16

<a id="T114-R37"></a>
**T114-R37**

- <a id="T114-R37-C01"></a>列 1: E36
- <a id="T114-R37-C02"></a>列 2: FER
- <a id="T114-R37-C03"></a>列 3: L12
- <a id="T114-R37-C04"></a>列 4: C03
- <a id="T114-R37-C05"></a>列 5: C08
- <a id="T114-R37-C06"></a>列 6: C11
- <a id="T114-R37-C07"></a>列 7: C18
- <a id="T114-R37-C08"></a>列 8: C19
- <a id="T114-R37-C09"></a>列 9: C20

<a id="T114-R38"></a>
**T114-R38**

- <a id="T114-R38-C01"></a>列 1: E37
- <a id="T114-R38-C02"></a>列 2: CS
- <a id="T114-R38-C03"></a>列 3: L13
- <a id="T114-R38-C04"></a>列 4: C01
- <a id="T114-R38-C05"></a>列 5: C04
- <a id="T114-R38-C06"></a>列 6: C09
- <a id="T114-R38-C07"></a>列 7: C10
- <a id="T114-R38-C08"></a>列 8: C11
- <a id="T114-R38-C09"></a>列 9: C20

<a id="T114-R39"></a>
**T114-R39**

- <a id="T114-R39-C01"></a>列 1: E38
- <a id="T114-R39-C02"></a>列 2: NS
- <a id="T114-R39-C03"></a>列 3: L13
- <a id="T114-R39-C04"></a>列 4: C03
- <a id="T114-R39-C05"></a>列 5: C05
- <a id="T114-R39-C06"></a>列 6: C06
- <a id="T114-R39-C07"></a>列 7: C08
- <a id="T114-R39-C08"></a>列 8: C15
- <a id="T114-R39-C09"></a>列 9: C19

<a id="T114-R40"></a>
**T114-R40**

- <a id="T114-R40-C01"></a>列 1: E39
- <a id="T114-R40-C02"></a>列 2: FER
- <a id="T114-R40-C03"></a>列 3: L13
- <a id="T114-R40-C04"></a>列 4: C02
- <a id="T114-R40-C05"></a>列 5: C07
- <a id="T114-R40-C06"></a>列 6: C12
- <a id="T114-R40-C07"></a>列 7: C14
- <a id="T114-R40-C08"></a>列 8: C17
- <a id="T114-R40-C09"></a>列 9: C18

<a id="T114-R41"></a>
**T114-R41**

- <a id="T114-R41-C01"></a>列 1: E40
- <a id="T114-R41-C02"></a>列 2: CS
- <a id="T114-R41-C03"></a>列 3: L14
- <a id="T114-R41-C04"></a>列 4: C04
- <a id="T114-R41-C05"></a>列 5: C05
- <a id="T114-R41-C06"></a>列 6: C07
- <a id="T114-R41-C07"></a>列 7: C09
- <a id="T114-R41-C08"></a>列 8: C16
- <a id="T114-R41-C09"></a>列 9: C19

<a id="T114-R42"></a>
**T114-R42**

- <a id="T114-R42-C01"></a>列 1: E41
- <a id="T114-R42-C02"></a>列 2: NS
- <a id="T114-R42-C03"></a>列 3: L14
- <a id="T114-R42-C04"></a>列 4: C01
- <a id="T114-R42-C05"></a>列 5: C08
- <a id="T114-R42-C06"></a>列 6: C10
- <a id="T114-R42-C07"></a>列 7: C11
- <a id="T114-R42-C08"></a>列 8: C15
- <a id="T114-R42-C09"></a>列 9: C17

<a id="T114-R43"></a>
**T114-R43**

- <a id="T114-R43-C01"></a>列 1: E42
- <a id="T114-R43-C02"></a>列 2: FER
- <a id="T114-R43-C03"></a>列 3: L14
- <a id="T114-R43-C04"></a>列 4: C02
- <a id="T114-R43-C05"></a>列 5: C03
- <a id="T114-R43-C06"></a>列 6: C06
- <a id="T114-R43-C07"></a>列 7: C12
- <a id="T114-R43-C08"></a>列 8: C18
- <a id="T114-R43-C09"></a>列 9: C20

<a id="T114-R44"></a>
**T114-R44**

- <a id="T114-R44-C01"></a>列 1: E43
- <a id="T114-R44-C02"></a>列 2: CS
- <a id="T114-R44-C03"></a>列 3: L15
- <a id="T114-R44-C04"></a>列 4: C04
- <a id="T114-R44-C05"></a>列 5: C05
- <a id="T114-R44-C06"></a>列 6: C06
- <a id="T114-R44-C07"></a>列 7: C13
- <a id="T114-R44-C08"></a>列 8: C18
- <a id="T114-R44-C09"></a>列 9: C19

<a id="T114-R45"></a>
**T114-R45**

- <a id="T114-R45-C01"></a>列 1: E44
- <a id="T114-R45-C02"></a>列 2: NS
- <a id="T114-R45-C03"></a>列 3: L15
- <a id="T114-R45-C04"></a>列 4: C02
- <a id="T114-R45-C05"></a>列 5: C03
- <a id="T114-R45-C06"></a>列 6: C07
- <a id="T114-R45-C07"></a>列 7: C08
- <a id="T114-R45-C08"></a>列 8: C09
- <a id="T114-R45-C09"></a>列 9: C20

<a id="T114-R46"></a>
**T114-R46**

- <a id="T114-R46-C01"></a>列 1: E45
- <a id="T114-R46-C02"></a>列 2: FER
- <a id="T114-R46-C03"></a>列 3: L15
- <a id="T114-R46-C04"></a>列 4: C01
- <a id="T114-R46-C05"></a>列 5: C11
- <a id="T114-R46-C06"></a>列 6: C12
- <a id="T114-R46-C07"></a>列 7: C14
- <a id="T114-R46-C08"></a>列 8: C16
- <a id="T114-R46-C09"></a>列 9: C17

<a id="T114-R47"></a>
**T114-R47**

- <a id="T114-R47-C01"></a>列 1: E46
- <a id="T114-R47-C02"></a>列 2: CS
- <a id="T114-R47-C03"></a>列 3: L16
- <a id="T114-R47-C04"></a>列 4: C02
- <a id="T114-R47-C05"></a>列 5: C09
- <a id="T114-R47-C06"></a>列 6: C10
- <a id="T114-R47-C07"></a>列 7: C11
- <a id="T114-R47-C08"></a>列 8: C12
- <a id="T114-R47-C09"></a>列 9: C17

<a id="T114-R48"></a>
**T114-R48**

- <a id="T114-R48-C01"></a>列 1: E47
- <a id="T114-R48-C02"></a>列 2: NS
- <a id="T114-R48-C03"></a>列 3: L16
- <a id="T114-R48-C04"></a>列 4: C04
- <a id="T114-R48-C05"></a>列 5: C06
- <a id="T114-R48-C06"></a>列 6: C07
- <a id="T114-R48-C07"></a>列 7: C08
- <a id="T114-R48-C08"></a>列 8: C14
- <a id="T114-R48-C09"></a>列 9: C19

<a id="T114-R49"></a>
**T114-R49**

- <a id="T114-R49-C01"></a>列 1: E48
- <a id="T114-R49-C02"></a>列 2: FER
- <a id="T114-R49-C03"></a>列 3: L16
- <a id="T114-R49-C04"></a>列 4: C01
- <a id="T114-R49-C05"></a>列 5: C03
- <a id="T114-R49-C06"></a>列 6: C05
- <a id="T114-R49-C07"></a>列 7: C13
- <a id="T114-R49-C08"></a>列 8: C15
- <a id="T114-R49-C09"></a>列 9: C20

<a id="T114-R50"></a>
**T114-R50**

- <a id="T114-R50-C01"></a>列 1: E49
- <a id="T114-R50-C02"></a>列 2: CS
- <a id="T114-R50-C03"></a>列 3: L17
- <a id="T114-R50-C04"></a>列 4: C01
- <a id="T114-R50-C05"></a>列 5: C02
- <a id="T114-R50-C06"></a>列 6: C04
- <a id="T114-R50-C07"></a>列 7: C06
- <a id="T114-R50-C08"></a>列 8: C11
- <a id="T114-R50-C09"></a>列 9: C18

<a id="T114-R51"></a>
**T114-R51**

- <a id="T114-R51-C01"></a>列 1: E50
- <a id="T114-R51-C02"></a>列 2: NS
- <a id="T114-R51-C03"></a>列 3: L17
- <a id="T114-R51-C04"></a>列 4: C05
- <a id="T114-R51-C05"></a>列 5: C09
- <a id="T114-R51-C06"></a>列 6: C10
- <a id="T114-R51-C07"></a>列 7: C12
- <a id="T114-R51-C08"></a>列 8: C14
- <a id="T114-R51-C09"></a>列 9: C20

<a id="T114-R52"></a>
**T114-R52**

- <a id="T114-R52-C01"></a>列 1: E51
- <a id="T114-R52-C02"></a>列 2: FER
- <a id="T114-R52-C03"></a>列 3: L17
- <a id="T114-R52-C04"></a>列 4: C03
- <a id="T114-R52-C05"></a>列 5: C07
- <a id="T114-R52-C06"></a>列 6: C13
- <a id="T114-R52-C07"></a>列 7: C15
- <a id="T114-R52-C08"></a>列 8: C16
- <a id="T114-R52-C09"></a>列 9: C19

<a id="T114-R53"></a>
**T114-R53**

- <a id="T114-R53-C01"></a>列 1: E52
- <a id="T114-R53-C02"></a>列 2: CS
- <a id="T114-R53-C03"></a>列 3: L18
- <a id="T114-R53-C04"></a>列 4: C02
- <a id="T114-R53-C05"></a>列 5: C03
- <a id="T114-R53-C06"></a>列 6: C05
- <a id="T114-R53-C07"></a>列 7: C08
- <a id="T114-R53-C08"></a>列 8: C13
- <a id="T114-R53-C09"></a>列 9: C14

<a id="T114-R54"></a>
**T114-R54**

- <a id="T114-R54-C01"></a>列 1: E53
- <a id="T114-R54-C02"></a>列 2: NS
- <a id="T114-R54-C03"></a>列 3: L18
- <a id="T114-R54-C04"></a>列 4: C04
- <a id="T114-R54-C05"></a>列 5: C09
- <a id="T114-R54-C06"></a>列 6: C11
- <a id="T114-R54-C07"></a>列 7: C12
- <a id="T114-R54-C08"></a>列 8: C15
- <a id="T114-R54-C09"></a>列 9: C16

<a id="T114-R55"></a>
**T114-R55**

- <a id="T114-R55-C01"></a>列 1: E54
- <a id="T114-R55-C02"></a>列 2: FER
- <a id="T114-R55-C03"></a>列 3: L18
- <a id="T114-R55-C04"></a>列 4: C06
- <a id="T114-R55-C05"></a>列 5: C07
- <a id="T114-R55-C06"></a>列 6: C10
- <a id="T114-R55-C07"></a>列 7: C17
- <a id="T114-R55-C08"></a>列 8: C19
- <a id="T114-R55-C09"></a>列 9: C20

<a id="T114-R56"></a>
**T114-R56**

- <a id="T114-R56-C01"></a>列 1: E55
- <a id="T114-R56-C02"></a>列 2: CS
- <a id="T114-R56-C03"></a>列 3: L19
- <a id="T114-R56-C04"></a>列 4: C02
- <a id="T114-R56-C05"></a>列 5: C05
- <a id="T114-R56-C06"></a>列 6: C07
- <a id="T114-R56-C07"></a>列 7: C11
- <a id="T114-R56-C08"></a>列 8: C14
- <a id="T114-R56-C09"></a>列 9: C16

<a id="T114-R57"></a>
**T114-R57**

- <a id="T114-R57-C01"></a>列 1: E56
- <a id="T114-R57-C02"></a>列 2: NS
- <a id="T114-R57-C03"></a>列 3: L19
- <a id="T114-R57-C04"></a>列 4: C01
- <a id="T114-R57-C05"></a>列 5: C06
- <a id="T114-R57-C06"></a>列 6: C10
- <a id="T114-R57-C07"></a>列 7: C12
- <a id="T114-R57-C08"></a>列 8: C13
- <a id="T114-R57-C09"></a>列 9: C18

<a id="T114-R58"></a>
**T114-R58**

- <a id="T114-R58-C01"></a>列 1: E57
- <a id="T114-R58-C02"></a>列 2: FER
- <a id="T114-R58-C03"></a>列 3: L19
- <a id="T114-R58-C04"></a>列 4: C03
- <a id="T114-R58-C05"></a>列 5: C04
- <a id="T114-R58-C06"></a>列 6: C08
- <a id="T114-R58-C07"></a>列 7: C09
- <a id="T114-R58-C08"></a>列 8: C15
- <a id="T114-R58-C09"></a>列 9: C17

<a id="T114-R59"></a>
**T114-R59**

- <a id="T114-R59-C01"></a>列 1: E58
- <a id="T114-R59-C02"></a>列 2: CS
- <a id="T114-R59-C03"></a>列 3: L20
- <a id="T114-R59-C04"></a>列 4: C03
- <a id="T114-R59-C05"></a>列 5: C07
- <a id="T114-R59-C06"></a>列 6: C10
- <a id="T114-R59-C07"></a>列 7: C13
- <a id="T114-R59-C08"></a>列 8: C17
- <a id="T114-R59-C09"></a>列 9: C18

<a id="T114-R60"></a>
**T114-R60**

- <a id="T114-R60-C01"></a>列 1: E59
- <a id="T114-R60-C02"></a>列 2: NS
- <a id="T114-R60-C03"></a>列 3: L20
- <a id="T114-R60-C04"></a>列 4: C02
- <a id="T114-R60-C05"></a>列 5: C06
- <a id="T114-R60-C06"></a>列 6: C08
- <a id="T114-R60-C07"></a>列 7: C09
- <a id="T114-R60-C08"></a>列 8: C14
- <a id="T114-R60-C09"></a>列 9: C15

<a id="T114-R61"></a>
**T114-R61**

- <a id="T114-R61-C01"></a>列 1: E60
- <a id="T114-R61-C02"></a>列 2: FER
- <a id="T114-R61-C03"></a>列 3: L20
- <a id="T114-R61-C04"></a>列 4: C01
- <a id="T114-R61-C05"></a>列 5: C04
- <a id="T114-R61-C06"></a>列 6: C05
- <a id="T114-R61-C07"></a>列 7: C12
- <a id="T114-R61-C08"></a>列 8: C16
- <a id="T114-R61-C09"></a>列 9: C19

<a id="P118"></a>

A.3 Per-candidate coverage (each evaluated in 18 labs)

<a id="T120"></a>

<a id="T120-R01"></a>
**T120-R01**

- <a id="T120-R01-C01"></a>列 1: Candidate
- <a id="T120-R01-C02"></a>列 2: #CS labs
- <a id="T120-R01-C03"></a>列 3: #NS labs
- <a id="T120-R01-C04"></a>列 4: #FER labs
- <a id="T120-R01-C05"></a>列 5: #Total labs
- <a id="T120-R01-C06"></a>列 6: CS labs (host labs for CS tests)
- <a id="T120-R01-C07"></a>列 7: NS labs (host labs for NS tests)
- <a id="T120-R01-C08"></a>列 8: FER labs (host labs for FER tests)

<a id="T120-R02"></a>
**T120-R02**

- <a id="T120-R02-C01"></a>列 1: C01
- <a id="T120-R02-C02"></a>列 2: 6
- <a id="T120-R02-C03"></a>列 3: 6
- <a id="T120-R02-C04"></a>列 4: 6
- <a id="T120-R02-C05"></a>列 5: 18
- <a id="T120-R02-C06"></a>列 6: L03, L08, L10, L12, L13, L17
- <a id="T120-R02-C07"></a>列 7: L04, L05, L09, L11, L14, L19
- <a id="T120-R02-C08"></a>列 8: L02, L06, L07, L15, L16, L20

<a id="T120-R03"></a>
**T120-R03**

- <a id="T120-R03-C01"></a>列 1: C02
- <a id="T120-R03-C02"></a>列 2: 6
- <a id="T120-R03-C03"></a>列 3: 6
- <a id="T120-R03-C04"></a>列 4: 6
- <a id="T120-R03-C05"></a>列 5: 18
- <a id="T120-R03-C06"></a>列 6: L01, L10, L16, L17, L18, L19
- <a id="T120-R03-C07"></a>列 7: L03, L08, L09, L12, L15, L20
- <a id="T120-R03-C08"></a>列 8: L05, L06, L07, L11, L13, L14

<a id="T120-R04"></a>
**T120-R04**

- <a id="T120-R04-C01"></a>列 1: C03
- <a id="T120-R04-C02"></a>列 2: 6
- <a id="T120-R04-C03"></a>列 3: 6
- <a id="T120-R04-C04"></a>列 4: 6
- <a id="T120-R04-C05"></a>列 5: 18
- <a id="T120-R04-C06"></a>列 6: L04, L07, L08, L10, L18, L20
- <a id="T120-R04-C07"></a>列 7: L01, L02, L05, L11, L13, L15
- <a id="T120-R04-C08"></a>列 8: L09, L12, L14, L16, L17, L19

<a id="T120-R05"></a>
**T120-R05**

- <a id="T120-R05-C01"></a>列 1: C04
- <a id="T120-R05-C02"></a>列 2: 6
- <a id="T120-R05-C03"></a>列 3: 6
- <a id="T120-R05-C04"></a>列 4: 6
- <a id="T120-R05-C05"></a>列 5: 18
- <a id="T120-R05-C06"></a>列 6: L06, L10, L13, L14, L15, L17
- <a id="T120-R05-C07"></a>列 7: L07, L08, L11, L12, L16, L18
- <a id="T120-R05-C08"></a>列 8: L01, L02, L03, L05, L19, L20

<a id="T120-R06"></a>
**T120-R06**

- <a id="T120-R06-C01"></a>列 1: C05
- <a id="T120-R06-C02"></a>列 2: 6
- <a id="T120-R06-C03"></a>列 3: 6
- <a id="T120-R06-C04"></a>列 4: 6
- <a id="T120-R06-C05"></a>列 5: 18
- <a id="T120-R06-C06"></a>列 6: L02, L12, L14, L15, L18, L19
- <a id="T120-R06-C07"></a>列 7: L01, L03, L09, L10, L13, L17
- <a id="T120-R06-C08"></a>列 8: L04, L06, L08, L11, L16, L20

<a id="T120-R07"></a>
**T120-R07**

- <a id="T120-R07-C01"></a>列 1: C06
- <a id="T120-R07-C02"></a>列 2: 6
- <a id="T120-R07-C03"></a>列 3: 6
- <a id="T120-R07-C04"></a>列 4: 6
- <a id="T120-R07-C05"></a>列 5: 18
- <a id="T120-R07-C06"></a>列 6: L07, L09, L11, L12, L15, L17
- <a id="T120-R07-C07"></a>列 7: L02, L05, L13, L16, L19, L20
- <a id="T120-R07-C08"></a>列 8: L01, L04, L08, L10, L14, L18

<a id="T120-R08"></a>
**T120-R08**

- <a id="T120-R08-C01"></a>列 1: C07
- <a id="T120-R08-C02"></a>列 2: 6
- <a id="T120-R08-C03"></a>列 3: 6
- <a id="T120-R08-C04"></a>列 4: 6
- <a id="T120-R08-C05"></a>列 5: 18
- <a id="T120-R08-C06"></a>列 6: L03, L06, L12, L14, L19, L20
- <a id="T120-R08-C07"></a>列 7: L01, L04, L09, L11, L15, L16
- <a id="T120-R08-C08"></a>列 8: L05, L08, L10, L13, L17, L18

<a id="T120-R09"></a>
**T120-R09**

- <a id="T120-R09-C01"></a>列 1: C08
- <a id="T120-R09-C02"></a>列 2: 6
- <a id="T120-R09-C03"></a>列 3: 6
- <a id="T120-R09-C04"></a>列 4: 6
- <a id="T120-R09-C05"></a>列 5: 18
- <a id="T120-R09-C06"></a>列 6: L01, L03, L05, L06, L09, L18
- <a id="T120-R09-C07"></a>列 7: L10, L13, L14, L15, L16, L20
- <a id="T120-R09-C08"></a>列 8: L02, L04, L07, L11, L12, L19

<a id="T120-R10"></a>
**T120-R10**

- <a id="T120-R10-C01"></a>列 1: C09
- <a id="T120-R10-C02"></a>列 2: 6
- <a id="T120-R10-C03"></a>列 3: 6
- <a id="T120-R10-C04"></a>列 4: 6
- <a id="T120-R10-C05"></a>列 5: 18
- <a id="T120-R10-C06"></a>列 6: L05, L08, L11, L13, L14, L16
- <a id="T120-R10-C07"></a>列 7: L01, L02, L15, L17, L18, L20
- <a id="T120-R10-C08"></a>列 8: L03, L04, L06, L07, L10, L19

<a id="T120-R11"></a>
**T120-R11**

- <a id="T120-R11-C01"></a>列 1: C10
- <a id="T120-R11-C02"></a>列 2: 6
- <a id="T120-R11-C03"></a>列 3: 6
- <a id="T120-R11-C04"></a>列 4: 6
- <a id="T120-R11-C05"></a>列 5: 18
- <a id="T120-R11-C06"></a>列 6: L01, L04, L07, L13, L16, L20
- <a id="T120-R11-C07"></a>列 7: L03, L06, L12, L14, L17, L19
- <a id="T120-R11-C08"></a>列 8: L02, L05, L08, L09, L11, L18

<a id="T120-R12"></a>
**T120-R12**

- <a id="T120-R12-C01"></a>列 1: C11
- <a id="T120-R12-C02"></a>列 2: 6
- <a id="T120-R12-C03"></a>列 3: 6
- <a id="T120-R12-C04"></a>列 4: 6
- <a id="T120-R12-C05"></a>列 5: 18
- <a id="T120-R12-C06"></a>列 6: L02, L06, L13, L16, L17, L19
- <a id="T120-R12-C07"></a>列 7: L01, L03, L05, L07, L14, L18
- <a id="T120-R12-C08"></a>列 8: L04, L08, L09, L10, L12, L15

<a id="T120-R13"></a>
**T120-R13**

- <a id="T120-R13-C01"></a>列 1: C12
- <a id="T120-R13-C02"></a>列 2: 6
- <a id="T120-R13-C03"></a>列 3: 6
- <a id="T120-R13-C04"></a>列 4: 6
- <a id="T120-R13-C05"></a>列 5: 18
- <a id="T120-R13-C06"></a>列 6: L03, L06, L07, L09, L10, L16
- <a id="T120-R13-C07"></a>列 7: L02, L04, L08, L17, L18, L19
- <a id="T120-R13-C08"></a>列 8: L01, L11, L13, L14, L15, L20

<a id="T120-R14"></a>
**T120-R14**

- <a id="T120-R14-C01"></a>列 1: C13
- <a id="T120-R14-C02"></a>列 2: 6
- <a id="T120-R14-C03"></a>列 3: 6
- <a id="T120-R14-C04"></a>列 4: 6
- <a id="T120-R14-C05"></a>列 5: 18
- <a id="T120-R14-C06"></a>列 6: L01, L03, L11, L15, L18, L20
- <a id="T120-R14-C07"></a>列 7: L04, L05, L07, L08, L12, L19
- <a id="T120-R14-C08"></a>列 8: L02, L06, L09, L10, L16, L17

<a id="T120-R15"></a>
**T120-R15**

- <a id="T120-R15-C01"></a>列 1: C14
- <a id="T120-R15-C02"></a>列 2: 6
- <a id="T120-R15-C03"></a>列 3: 6
- <a id="T120-R15-C04"></a>列 4: 6
- <a id="T120-R15-C05"></a>列 5: 18
- <a id="T120-R15-C06"></a>列 6: L02, L05, L07, L08, L18, L19
- <a id="T120-R15-C07"></a>列 7: L06, L11, L12, L16, L17, L20
- <a id="T120-R15-C08"></a>列 8: L01, L03, L04, L09, L13, L15

<a id="T120-R16"></a>
**T120-R16**

- <a id="T120-R16-C01"></a>列 1: C15
- <a id="T120-R16-C02"></a>列 2: 6
- <a id="T120-R16-C03"></a>列 3: 6
- <a id="T120-R16-C04"></a>列 4: 6
- <a id="T120-R16-C05"></a>列 5: 18
- <a id="T120-R16-C06"></a>列 6: L01, L02, L04, L06, L07, L12
- <a id="T120-R16-C07"></a>列 7: L08, L09, L13, L14, L18, L20
- <a id="T120-R16-C08"></a>列 8: L03, L05, L10, L16, L17, L19

<a id="T120-R17"></a>
**T120-R17**

- <a id="T120-R17-C01"></a>列 1: C16
- <a id="T120-R17-C02"></a>列 2: 6
- <a id="T120-R17-C03"></a>列 3: 6
- <a id="T120-R17-C04"></a>列 4: 6
- <a id="T120-R17-C05"></a>列 5: 18
- <a id="T120-R17-C06"></a>列 6: L01, L04, L09, L11, L14, L19
- <a id="T120-R17-C07"></a>列 7: L02, L05, L06, L10, L12, L18
- <a id="T120-R17-C08"></a>列 8: L03, L07, L08, L15, L17, L20

<a id="T120-R18"></a>
**T120-R18**

- <a id="T120-R18-C01"></a>列 1: C17
- <a id="T120-R18-C02"></a>列 2: 6
- <a id="T120-R18-C03"></a>列 3: 6
- <a id="T120-R18-C04"></a>列 4: 6
- <a id="T120-R18-C05"></a>列 5: 18
- <a id="T120-R18-C06"></a>列 6: L04, L05, L09, L12, L16, L20
- <a id="T120-R18-C07"></a>列 7: L02, L03, L07, L10, L11, L14
- <a id="T120-R18-C08"></a>列 8: L01, L06, L13, L15, L18, L19

<a id="T120-R19"></a>
**T120-R19**

- <a id="T120-R19-C01"></a>列 1: C18
- <a id="T120-R19-C02"></a>列 2: 6
- <a id="T120-R19-C03"></a>列 3: 6
- <a id="T120-R19-C04"></a>列 4: 6
- <a id="T120-R19-C05"></a>列 5: 18
- <a id="T120-R19-C06"></a>列 6: L04, L05, L08, L15, L17, L20
- <a id="T120-R19-C07"></a>列 7: L01, L06, L07, L09, L10, L19
- <a id="T120-R19-C08"></a>列 8: L02, L03, L11, L12, L13, L14

<a id="T120-R20"></a>
**T120-R20**

- <a id="T120-R20-C01"></a>列 1: C19
- <a id="T120-R20-C02"></a>列 2: 6
- <a id="T120-R20-C03"></a>列 3: 6
- <a id="T120-R20-C04"></a>列 4: 6
- <a id="T120-R20-C05"></a>列 5: 18
- <a id="T120-R20-C06"></a>列 6: L02, L05, L10, L11, L14, L15
- <a id="T120-R20-C07"></a>列 7: L03, L04, L06, L08, L13, L16
- <a id="T120-R20-C08"></a>列 8: L07, L09, L12, L17, L18, L20

<a id="T120-R21"></a>
**T120-R21**

- <a id="T120-R21-C01"></a>列 1: C20
- <a id="T120-R21-C02"></a>列 2: 6
- <a id="T120-R21-C03"></a>列 3: 6
- <a id="T120-R21-C04"></a>列 4: 6
- <a id="T120-R21-C05"></a>列 5: 18
- <a id="T120-R21-C06"></a>列 6: L02, L03, L08, L09, L11, L13
- <a id="T120-R21-C07"></a>列 7: L04, L06, L07, L10, L15, L17
- <a id="T120-R21-C08"></a>列 8: L01, L05, L12, L14, L16, L18

<a id="P123"></a>

A.4 Language Diversity/Balance Design

<a id="P125"></a>

## 1. Coverage — every candidate evaluated by exactly 18 labs, 6 per test type (CS/NS/FER)

<a id="P126"></a>

## 2. No self-grading — no lab evaluates its own candidate

<a id="P127"></a>

## 3. No repeat — no lab evaluates the same candidate twice

<a id="P128"></a>

## 4. Co-occurrence balance — every candidate pair appears together a near-constant number of times

<a id="P129"></a>

## 5. Language cap — no language group exceeds 3 labs per candidate per test type

<a id="P130"></a>

6. Language diversity — every candidate × test type slot has at least 4 distinct language groups among its 6 evaluating labs (5 in most cases)

<a id="P131"></a>

The test design below is an example and can be configurable based on language spread.

<a id="T133"></a>

<a id="T133-R01"></a>
**T133-R01**

- <a id="T133-R01-C01"></a>列 1: Candidate
- <a id="T133-R01-C02"></a>列 2: Type
- <a id="T133-R01-C03"></a>列 3: #Langs
- <a id="T133-R01-C04"></a>列 4: Mandarin<br>pool=7 cap=3
- <a id="T133-R01-C05"></a>列 5: English<br>pool=4 cap=2
- <a id="T133-R01-C06"></a>列 6: French<br>pool=2 cap=1
- <a id="T133-R01-C07"></a>列 7: Japanese<br>pool=2 cap=1
- <a id="T133-R01-C08"></a>列 8: Swedish<br>pool=1 cap=1
- <a id="T133-R01-C09"></a>列 9: Finnish<br>pool=1 cap=1
- <a id="T133-R01-C10"></a>列 10: German<br>pool=1 cap=1
- <a id="T133-R01-C11"></a>列 11: Dutch<br>pool=1 cap=1
- <a id="T133-R01-C12"></a>列 12: Korean<br>pool=1 cap=1

<a id="T133-R02"></a>
**T133-R02**

- <a id="T133-R02-C01"></a>列 1: C01
- <a id="T133-R02-C02"></a>列 2: CS
- <a id="T133-R02-C03"></a>列 3: 4
- <a id="T133-R02-C04"></a>列 4: 3
- <a id="T133-R02-C05"></a>列 5: 1
- <a id="T133-R02-C06"></a>列 6: 
- <a id="T133-R02-C07"></a>列 7: 1
- <a id="T133-R02-C08"></a>列 8: 
- <a id="T133-R02-C09"></a>列 9: 
- <a id="T133-R02-C10"></a>列 10: 
- <a id="T133-R02-C11"></a>列 11: 1
- <a id="T133-R02-C12"></a>列 12: 

<a id="T133-R03"></a>
**T133-R03**

- <a id="T133-R03-C01"></a>列 1: C01
- <a id="T133-R03-C02"></a>列 2: NS
- <a id="T133-R03-C03"></a>列 3: 4
- <a id="T133-R03-C04"></a>列 4: 3
- <a id="T133-R03-C05"></a>列 5: 1
- <a id="T133-R03-C06"></a>列 6: 1
- <a id="T133-R03-C07"></a>列 7: 
- <a id="T133-R03-C08"></a>列 8: 
- <a id="T133-R03-C09"></a>列 9: 1
- <a id="T133-R03-C10"></a>列 10: 
- <a id="T133-R03-C11"></a>列 11: 
- <a id="T133-R03-C12"></a>列 12: 

<a id="T133-R04"></a>
**T133-R04**

- <a id="T133-R04-C01"></a>列 1: C01
- <a id="T133-R04-C02"></a>列 2: FER
- <a id="T133-R04-C03"></a>列 3: 5
- <a id="T133-R04-C04"></a>列 4: 1
- <a id="T133-R04-C05"></a>列 5: 2
- <a id="T133-R04-C06"></a>列 6: 1
- <a id="T133-R04-C07"></a>列 7: 1
- <a id="T133-R04-C08"></a>列 8: 
- <a id="T133-R04-C09"></a>列 9: 
- <a id="T133-R04-C10"></a>列 10: 1
- <a id="T133-R04-C11"></a>列 11: 
- <a id="T133-R04-C12"></a>列 12: 

<a id="T133-R05"></a>
**T133-R05**

- <a id="T133-R05-C01"></a>列 1: C02
- <a id="T133-R05-C02"></a>列 2: CS
- <a id="T133-R05-C03"></a>列 3: 5
- <a id="T133-R05-C04"></a>列 4: 2
- <a id="T133-R05-C05"></a>列 5: 1
- <a id="T133-R05-C06"></a>列 6: 1
- <a id="T133-R05-C07"></a>列 7: 1
- <a id="T133-R05-C08"></a>列 8: 
- <a id="T133-R05-C09"></a>列 9: 
- <a id="T133-R05-C10"></a>列 10: 1
- <a id="T133-R05-C11"></a>列 11: 
- <a id="T133-R05-C12"></a>列 12: 

<a id="T133-R06"></a>
**T133-R06**

- <a id="T133-R06-C01"></a>列 1: C02
- <a id="T133-R06-C02"></a>列 2: NS
- <a id="T133-R06-C03"></a>列 3: 5
- <a id="T133-R06-C04"></a>列 4: 2
- <a id="T133-R06-C05"></a>列 5: 1
- <a id="T133-R06-C06"></a>列 6: 1
- <a id="T133-R06-C07"></a>列 7: 1
- <a id="T133-R06-C08"></a>列 8: 
- <a id="T133-R06-C09"></a>列 9: 
- <a id="T133-R06-C10"></a>列 10: 
- <a id="T133-R06-C11"></a>列 11: 
- <a id="T133-R06-C12"></a>列 12: 1

<a id="T133-R07"></a>
**T133-R07**

- <a id="T133-R07-C01"></a>列 1: C02
- <a id="T133-R07-C02"></a>列 2: FER
- <a id="T133-R07-C03"></a>列 3: 5
- <a id="T133-R07-C04"></a>列 4: 2
- <a id="T133-R07-C05"></a>列 5: 1
- <a id="T133-R07-C06"></a>列 6: 
- <a id="T133-R07-C07"></a>列 7: 
- <a id="T133-R07-C08"></a>列 8: 1
- <a id="T133-R07-C09"></a>列 9: 1
- <a id="T133-R07-C10"></a>列 10: 
- <a id="T133-R07-C11"></a>列 11: 1
- <a id="T133-R07-C12"></a>列 12: 

<a id="T133-R08"></a>
**T133-R08**

- <a id="T133-R08-C01"></a>列 1: C03
- <a id="T133-R08-C02"></a>列 2: CS
- <a id="T133-R08-C03"></a>列 3: 5
- <a id="T133-R08-C04"></a>列 4: 1
- <a id="T133-R08-C05"></a>列 5: 2
- <a id="T133-R08-C06"></a>列 6: 
- <a id="T133-R08-C07"></a>列 7: 1
- <a id="T133-R08-C08"></a>列 8: 1
- <a id="T133-R08-C09"></a>列 9: 
- <a id="T133-R08-C10"></a>列 10: 
- <a id="T133-R08-C11"></a>列 11: 1
- <a id="T133-R08-C12"></a>列 12: 

<a id="T133-R09"></a>
**T133-R09**

- <a id="T133-R09-C01"></a>列 1: C03
- <a id="T133-R09-C02"></a>列 2: NS
- <a id="T133-R09-C03"></a>列 3: 5
- <a id="T133-R09-C04"></a>列 4: 2
- <a id="T133-R09-C05"></a>列 5: 1
- <a id="T133-R09-C06"></a>列 6: 1
- <a id="T133-R09-C07"></a>列 7: 1
- <a id="T133-R09-C08"></a>列 8: 
- <a id="T133-R09-C09"></a>列 9: 
- <a id="T133-R09-C10"></a>列 10: 1
- <a id="T133-R09-C11"></a>列 11: 
- <a id="T133-R09-C12"></a>列 12: 

<a id="T133-R10"></a>
**T133-R10**

- <a id="T133-R10-C01"></a>列 1: C03
- <a id="T133-R10-C02"></a>列 2: FER
- <a id="T133-R10-C03"></a>列 3: 4
- <a id="T133-R10-C04"></a>列 4: 3
- <a id="T133-R10-C05"></a>列 5: 1
- <a id="T133-R10-C06"></a>列 6: 1
- <a id="T133-R10-C07"></a>列 7: 
- <a id="T133-R10-C08"></a>列 8: 
- <a id="T133-R10-C09"></a>列 9: 
- <a id="T133-R10-C10"></a>列 10: 
- <a id="T133-R10-C11"></a>列 11: 
- <a id="T133-R10-C12"></a>列 12: 1

<a id="T133-R11"></a>
**T133-R11**

- <a id="T133-R11-C01"></a>列 1: C04
- <a id="T133-R11-C02"></a>列 2: CS
- <a id="T133-R11-C03"></a>列 3: 5
- <a id="T133-R11-C04"></a>列 4: 2
- <a id="T133-R11-C05"></a>列 5: 1
- <a id="T133-R11-C06"></a>列 6: 1
- <a id="T133-R11-C07"></a>列 7: 1
- <a id="T133-R11-C08"></a>列 8: 
- <a id="T133-R11-C09"></a>列 9: 1
- <a id="T133-R11-C10"></a>列 10: 
- <a id="T133-R11-C11"></a>列 11: 
- <a id="T133-R11-C12"></a>列 12: 

<a id="T133-R12"></a>
**T133-R12**

- <a id="T133-R12-C01"></a>列 1: C04
- <a id="T133-R12-C02"></a>列 2: NS
- <a id="T133-R12-C03"></a>列 3: 5
- <a id="T133-R12-C04"></a>列 4: 2
- <a id="T133-R12-C05"></a>列 5: 1
- <a id="T133-R12-C06"></a>列 6: 1
- <a id="T133-R12-C07"></a>列 7: 
- <a id="T133-R12-C08"></a>列 8: 
- <a id="T133-R12-C09"></a>列 9: 
- <a id="T133-R12-C10"></a>列 10: 1
- <a id="T133-R12-C11"></a>列 11: 1
- <a id="T133-R12-C12"></a>列 12: 

<a id="T133-R13"></a>
**T133-R13**

- <a id="T133-R13-C01"></a>列 1: C04
- <a id="T133-R13-C02"></a>列 2: FER
- <a id="T133-R13-C03"></a>列 3: 5
- <a id="T133-R13-C04"></a>列 4: 2
- <a id="T133-R13-C05"></a>列 5: 1
- <a id="T133-R13-C06"></a>列 6: 
- <a id="T133-R13-C07"></a>列 7: 1
- <a id="T133-R13-C08"></a>列 8: 1
- <a id="T133-R13-C09"></a>列 9: 
- <a id="T133-R13-C10"></a>列 10: 
- <a id="T133-R13-C11"></a>列 11: 
- <a id="T133-R13-C12"></a>列 12: 1

<a id="T133-R14"></a>
**T133-R14**

- <a id="T133-R14-C01"></a>列 1: C05
- <a id="T133-R14-C02"></a>列 2: CS
- <a id="T133-R14-C03"></a>列 3: 5
- <a id="T133-R14-C04"></a>列 4: 2
- <a id="T133-R14-C05"></a>列 5: 1
- <a id="T133-R14-C06"></a>列 6: 1
- <a id="T133-R14-C07"></a>列 7: 1
- <a id="T133-R14-C08"></a>列 8: 1
- <a id="T133-R14-C09"></a>列 9: 
- <a id="T133-R14-C10"></a>列 10: 
- <a id="T133-R14-C11"></a>列 11: 
- <a id="T133-R14-C12"></a>列 12: 

<a id="T133-R15"></a>
**T133-R15**

- <a id="T133-R15-C01"></a>列 1: C05
- <a id="T133-R15-C02"></a>列 2: NS
- <a id="T133-R15-C03"></a>列 3: 4
- <a id="T133-R15-C04"></a>列 4: 3
- <a id="T133-R15-C05"></a>列 5: 1
- <a id="T133-R15-C06"></a>列 6: 1
- <a id="T133-R15-C07"></a>列 7: 
- <a id="T133-R15-C08"></a>列 8: 
- <a id="T133-R15-C09"></a>列 9: 1
- <a id="T133-R15-C10"></a>列 10: 
- <a id="T133-R15-C11"></a>列 11: 
- <a id="T133-R15-C12"></a>列 12: 

<a id="T133-R16"></a>
**T133-R16**

- <a id="T133-R16-C01"></a>列 1: C05
- <a id="T133-R16-C02"></a>列 2: FER
- <a id="T133-R16-C03"></a>列 3: 5
- <a id="T133-R16-C04"></a>列 4: 2
- <a id="T133-R16-C05"></a>列 5: 1
- <a id="T133-R16-C06"></a>列 6: 
- <a id="T133-R16-C07"></a>列 7: 
- <a id="T133-R16-C08"></a>列 8: 
- <a id="T133-R16-C09"></a>列 9: 
- <a id="T133-R16-C10"></a>列 10: 1
- <a id="T133-R16-C11"></a>列 11: 1
- <a id="T133-R16-C12"></a>列 12: 1

<a id="T133-R17"></a>
**T133-R17**

- <a id="T133-R17-C01"></a>列 1: C06
- <a id="T133-R17-C02"></a>列 2: CS
- <a id="T133-R17-C03"></a>列 3: 5
- <a id="T133-R17-C04"></a>列 4: 1
- <a id="T133-R17-C05"></a>列 5: 2
- <a id="T133-R17-C06"></a>列 6: 
- <a id="T133-R17-C07"></a>列 7: 
- <a id="T133-R17-C08"></a>列 8: 1
- <a id="T133-R17-C09"></a>列 9: 
- <a id="T133-R17-C10"></a>列 10: 1
- <a id="T133-R17-C11"></a>列 11: 
- <a id="T133-R17-C12"></a>列 12: 1

<a id="T133-R18"></a>
**T133-R18**

- <a id="T133-R18-C01"></a>列 1: C06
- <a id="T133-R18-C02"></a>列 2: NS
- <a id="T133-R18-C03"></a>列 3: 5
- <a id="T133-R18-C04"></a>列 4: 2
- <a id="T133-R18-C05"></a>列 5: 1
- <a id="T133-R18-C06"></a>列 6: 1
- <a id="T133-R18-C07"></a>列 7: 1
- <a id="T133-R18-C08"></a>列 8: 
- <a id="T133-R18-C09"></a>列 9: 1
- <a id="T133-R18-C10"></a>列 10: 
- <a id="T133-R18-C11"></a>列 11: 
- <a id="T133-R18-C12"></a>列 12: 

<a id="T133-R19"></a>
**T133-R19**

- <a id="T133-R19-C01"></a>列 1: C06
- <a id="T133-R19-C02"></a>列 2: FER
- <a id="T133-R19-C03"></a>列 3: 4
- <a id="T133-R19-C04"></a>列 4: 3
- <a id="T133-R19-C05"></a>列 5: 1
- <a id="T133-R19-C06"></a>列 6: 1
- <a id="T133-R19-C07"></a>列 7: 1
- <a id="T133-R19-C08"></a>列 8: 
- <a id="T133-R19-C09"></a>列 9: 
- <a id="T133-R19-C10"></a>列 10: 
- <a id="T133-R19-C11"></a>列 11: 
- <a id="T133-R19-C12"></a>列 12: 

<a id="T133-R20"></a>
**T133-R20**

- <a id="T133-R20-C01"></a>列 1: C07
- <a id="T133-R20-C02"></a>列 2: CS
- <a id="T133-R20-C03"></a>列 3: 5
- <a id="T133-R20-C04"></a>列 4: 2
- <a id="T133-R20-C05"></a>列 5: 1
- <a id="T133-R20-C06"></a>列 6: 1
- <a id="T133-R20-C07"></a>列 7: 
- <a id="T133-R20-C08"></a>列 8: 1
- <a id="T133-R20-C09"></a>列 9: 
- <a id="T133-R20-C10"></a>列 10: 
- <a id="T133-R20-C11"></a>列 11: 
- <a id="T133-R20-C12"></a>列 12: 1

<a id="T133-R21"></a>
**T133-R21**

- <a id="T133-R21-C01"></a>列 1: C07
- <a id="T133-R21-C02"></a>列 2: NS
- <a id="T133-R21-C03"></a>列 3: 5
- <a id="T133-R21-C04"></a>列 4: 2
- <a id="T133-R21-C05"></a>列 5: 1
- <a id="T133-R21-C06"></a>列 6: 1
- <a id="T133-R21-C07"></a>列 7: 1
- <a id="T133-R21-C08"></a>列 8: 
- <a id="T133-R21-C09"></a>列 9: 
- <a id="T133-R21-C10"></a>列 10: 
- <a id="T133-R21-C11"></a>列 11: 1
- <a id="T133-R21-C12"></a>列 12: 

<a id="T133-R22"></a>
**T133-R22**

- <a id="T133-R22-C01"></a>列 1: C07
- <a id="T133-R22-C02"></a>列 2: FER
- <a id="T133-R22-C03"></a>列 3: 5
- <a id="T133-R22-C04"></a>列 4: 2
- <a id="T133-R22-C05"></a>列 5: 1
- <a id="T133-R22-C06"></a>列 6: 
- <a id="T133-R22-C07"></a>列 7: 1
- <a id="T133-R22-C08"></a>列 8: 
- <a id="T133-R22-C09"></a>列 9: 1
- <a id="T133-R22-C10"></a>列 10: 1
- <a id="T133-R22-C11"></a>列 11: 
- <a id="T133-R22-C12"></a>列 12: 

<a id="T133-R23"></a>
**T133-R23**

- <a id="T133-R23-C01"></a>列 1: C08
- <a id="T133-R23-C02"></a>列 2: CS
- <a id="T133-R23-C03"></a>列 3: 5
- <a id="T133-R23-C04"></a>列 4: 2
- <a id="T133-R23-C05"></a>列 5: 1
- <a id="T133-R23-C06"></a>列 6: 1
- <a id="T133-R23-C07"></a>列 7: 
- <a id="T133-R23-C08"></a>列 8: 
- <a id="T133-R23-C09"></a>列 9: 
- <a id="T133-R23-C10"></a>列 10: 1
- <a id="T133-R23-C11"></a>列 11: 1
- <a id="T133-R23-C12"></a>列 12: 

<a id="T133-R24"></a>
**T133-R24**

- <a id="T133-R24-C01"></a>列 1: C08
- <a id="T133-R24-C02"></a>列 2: NS
- <a id="T133-R24-C03"></a>列 3: 4
- <a id="T133-R24-C04"></a>列 4: 2
- <a id="T133-R24-C05"></a>列 5: 2
- <a id="T133-R24-C06"></a>列 6: 
- <a id="T133-R24-C07"></a>列 7: 1
- <a id="T133-R24-C08"></a>列 8: 
- <a id="T133-R24-C09"></a>列 9: 1
- <a id="T133-R24-C10"></a>列 10: 
- <a id="T133-R24-C11"></a>列 11: 
- <a id="T133-R24-C12"></a>列 12: 

<a id="T133-R25"></a>
**T133-R25**

- <a id="T133-R25-C01"></a>列 1: C08
- <a id="T133-R25-C02"></a>列 2: FER
- <a id="T133-R25-C03"></a>列 3: 5
- <a id="T133-R25-C04"></a>列 4: 2
- <a id="T133-R25-C05"></a>列 5: 1
- <a id="T133-R25-C06"></a>列 6: 1
- <a id="T133-R25-C07"></a>列 7: 1
- <a id="T133-R25-C08"></a>列 8: 
- <a id="T133-R25-C09"></a>列 9: 
- <a id="T133-R25-C10"></a>列 10: 
- <a id="T133-R25-C11"></a>列 11: 
- <a id="T133-R25-C12"></a>列 12: 1

<a id="T133-R26"></a>
**T133-R26**

- <a id="T133-R26-C01"></a>列 1: C09
- <a id="T133-R26-C02"></a>列 2: CS
- <a id="T133-R26-C03"></a>列 3: 5
- <a id="T133-R26-C04"></a>列 4: 2
- <a id="T133-R26-C05"></a>列 5: 1
- <a id="T133-R26-C06"></a>列 6: 
- <a id="T133-R26-C07"></a>列 7: 1
- <a id="T133-R26-C08"></a>列 8: 
- <a id="T133-R26-C09"></a>列 9: 
- <a id="T133-R26-C10"></a>列 10: 1
- <a id="T133-R26-C11"></a>列 11: 1
- <a id="T133-R26-C12"></a>列 12: 

<a id="T133-R27"></a>
**T133-R27**

- <a id="T133-R27-C01"></a>列 1: C09
- <a id="T133-R27-C02"></a>列 2: NS
- <a id="T133-R27-C03"></a>列 3: 4
- <a id="T133-R27-C04"></a>列 4: 3
- <a id="T133-R27-C05"></a>列 5: 1
- <a id="T133-R27-C06"></a>列 6: 
- <a id="T133-R27-C07"></a>列 7: 
- <a id="T133-R27-C08"></a>列 8: 1
- <a id="T133-R27-C09"></a>列 9: 
- <a id="T133-R27-C10"></a>列 10: 
- <a id="T133-R27-C11"></a>列 11: 
- <a id="T133-R27-C12"></a>列 12: 1

<a id="T133-R28"></a>
**T133-R28**

- <a id="T133-R28-C01"></a>列 1: C09
- <a id="T133-R28-C02"></a>列 2: FER
- <a id="T133-R28-C03"></a>列 3: 5
- <a id="T133-R28-C04"></a>列 4: 1
- <a id="T133-R28-C05"></a>列 5: 2
- <a id="T133-R28-C06"></a>列 6: 1
- <a id="T133-R28-C07"></a>列 7: 1
- <a id="T133-R28-C08"></a>列 8: 
- <a id="T133-R28-C09"></a>列 9: 1
- <a id="T133-R28-C10"></a>列 10: 
- <a id="T133-R28-C11"></a>列 11: 
- <a id="T133-R28-C12"></a>列 12: 

<a id="T133-R29"></a>
**T133-R29**

- <a id="T133-R29-C01"></a>列 1: C10
- <a id="T133-R29-C02"></a>列 2: CS
- <a id="T133-R29-C03"></a>列 3: 4
- <a id="T133-R29-C04"></a>列 4: 3
- <a id="T133-R29-C05"></a>列 5: 1
- <a id="T133-R29-C06"></a>列 6: 
- <a id="T133-R29-C07"></a>列 7: 1
- <a id="T133-R29-C08"></a>列 8: 
- <a id="T133-R29-C09"></a>列 9: 1
- <a id="T133-R29-C10"></a>列 10: 
- <a id="T133-R29-C11"></a>列 11: 
- <a id="T133-R29-C12"></a>列 12: 

<a id="T133-R30"></a>
**T133-R30**

- <a id="T133-R30-C01"></a>列 1: C10
- <a id="T133-R30-C02"></a>列 2: NS
- <a id="T133-R30-C03"></a>列 3: 5
- <a id="T133-R30-C04"></a>列 4: 2
- <a id="T133-R30-C05"></a>列 5: 1
- <a id="T133-R30-C06"></a>列 6: 
- <a id="T133-R30-C07"></a>列 7: 
- <a id="T133-R30-C08"></a>列 8: 1
- <a id="T133-R30-C09"></a>列 9: 
- <a id="T133-R30-C10"></a>列 10: 1
- <a id="T133-R30-C11"></a>列 11: 1
- <a id="T133-R30-C12"></a>列 12: 

<a id="T133-R31"></a>
**T133-R31**

- <a id="T133-R31-C01"></a>列 1: C10
- <a id="T133-R31-C02"></a>列 2: FER
- <a id="T133-R31-C03"></a>列 3: 5
- <a id="T133-R31-C04"></a>列 4: 2
- <a id="T133-R31-C05"></a>列 5: 1
- <a id="T133-R31-C06"></a>列 6: 1
- <a id="T133-R31-C07"></a>列 7: 1
- <a id="T133-R31-C08"></a>列 8: 
- <a id="T133-R31-C09"></a>列 9: 
- <a id="T133-R31-C10"></a>列 10: 
- <a id="T133-R31-C11"></a>列 11: 
- <a id="T133-R31-C12"></a>列 12: 1

<a id="T133-R32"></a>
**T133-R32**

- <a id="T133-R32-C01"></a>列 1: C11
- <a id="T133-R32-C02"></a>列 2: CS
- <a id="T133-R32-C03"></a>列 3: 4
- <a id="T133-R32-C04"></a>列 4: 3
- <a id="T133-R32-C05"></a>列 5: 1
- <a id="T133-R32-C06"></a>列 6: 
- <a id="T133-R32-C07"></a>列 7: 
- <a id="T133-R32-C08"></a>列 8: 
- <a id="T133-R32-C09"></a>列 9: 1
- <a id="T133-R32-C10"></a>列 10: 
- <a id="T133-R32-C11"></a>列 11: 
- <a id="T133-R32-C12"></a>列 12: 1

<a id="T133-R33"></a>
**T133-R33**

- <a id="T133-R33-C01"></a>列 1: C11
- <a id="T133-R33-C02"></a>列 2: NS
- <a id="T133-R33-C03"></a>列 3: 5
- <a id="T133-R33-C04"></a>列 4: 1
- <a id="T133-R33-C05"></a>列 5: 2
- <a id="T133-R33-C06"></a>列 6: 1
- <a id="T133-R33-C07"></a>列 7: 1
- <a id="T133-R33-C08"></a>列 8: 1
- <a id="T133-R33-C09"></a>列 9: 
- <a id="T133-R33-C10"></a>列 10: 
- <a id="T133-R33-C11"></a>列 11: 
- <a id="T133-R33-C12"></a>列 12: 

<a id="T133-R34"></a>
**T133-R34**

- <a id="T133-R34-C01"></a>列 1: C11
- <a id="T133-R34-C02"></a>列 2: FER
- <a id="T133-R34-C03"></a>列 3: 5
- <a id="T133-R34-C04"></a>列 4: 2
- <a id="T133-R34-C05"></a>列 5: 1
- <a id="T133-R34-C06"></a>列 6: 1
- <a id="T133-R34-C07"></a>列 7: 1
- <a id="T133-R34-C08"></a>列 8: 
- <a id="T133-R34-C09"></a>列 9: 
- <a id="T133-R34-C10"></a>列 10: 
- <a id="T133-R34-C11"></a>列 11: 1
- <a id="T133-R34-C12"></a>列 12: 

<a id="T133-R35"></a>
**T133-R35**

- <a id="T133-R35-C01"></a>列 1: C12
- <a id="T133-R35-C02"></a>列 2: CS
- <a id="T133-R35-C03"></a>列 3: 4
- <a id="T133-R35-C04"></a>列 4: 2
- <a id="T133-R35-C05"></a>列 5: 2
- <a id="T133-R35-C06"></a>列 6: 1
- <a id="T133-R35-C07"></a>列 7: 
- <a id="T133-R35-C08"></a>列 8: 
- <a id="T133-R35-C09"></a>列 9: 
- <a id="T133-R35-C10"></a>列 10: 1
- <a id="T133-R35-C11"></a>列 11: 
- <a id="T133-R35-C12"></a>列 12: 

<a id="T133-R36"></a>
**T133-R36**

- <a id="T133-R36-C01"></a>列 1: C12
- <a id="T133-R36-C02"></a>列 2: NS
- <a id="T133-R36-C03"></a>列 3: 5
- <a id="T133-R36-C04"></a>列 4: 2
- <a id="T133-R36-C05"></a>列 5: 1
- <a id="T133-R36-C06"></a>列 6: 
- <a id="T133-R36-C07"></a>列 7: 1
- <a id="T133-R36-C08"></a>列 8: 
- <a id="T133-R36-C09"></a>列 9: 1
- <a id="T133-R36-C10"></a>列 10: 
- <a id="T133-R36-C11"></a>列 11: 
- <a id="T133-R36-C12"></a>列 12: 1

<a id="T133-R37"></a>
**T133-R37**

- <a id="T133-R37-C01"></a>列 1: C12
- <a id="T133-R37-C02"></a>列 2: FER
- <a id="T133-R37-C03"></a>列 3: 5
- <a id="T133-R37-C04"></a>列 4: 2
- <a id="T133-R37-C05"></a>列 5: 1
- <a id="T133-R37-C06"></a>列 6: 1
- <a id="T133-R37-C07"></a>列 7: 
- <a id="T133-R37-C08"></a>列 8: 1
- <a id="T133-R37-C09"></a>列 9: 
- <a id="T133-R37-C10"></a>列 10: 
- <a id="T133-R37-C11"></a>列 11: 1
- <a id="T133-R37-C12"></a>列 12: 

<a id="T133-R38"></a>
**T133-R38**

- <a id="T133-R38-C01"></a>列 1: C13
- <a id="T133-R38-C02"></a>列 2: CS
- <a id="T133-R38-C03"></a>列 3: 5
- <a id="T133-R38-C04"></a>列 4: 2
- <a id="T133-R38-C05"></a>列 5: 1
- <a id="T133-R38-C06"></a>列 6: 
- <a id="T133-R38-C07"></a>列 7: 1
- <a id="T133-R38-C08"></a>列 8: 1
- <a id="T133-R38-C09"></a>列 9: 
- <a id="T133-R38-C10"></a>列 10: 
- <a id="T133-R38-C11"></a>列 11: 1
- <a id="T133-R38-C12"></a>列 12: 

<a id="T133-R39"></a>
**T133-R39**

- <a id="T133-R39-C01"></a>列 1: C13
- <a id="T133-R39-C02"></a>列 2: NS
- <a id="T133-R39-C03"></a>列 3: 5
- <a id="T133-R39-C04"></a>列 4: 2
- <a id="T133-R39-C05"></a>列 5: 1
- <a id="T133-R39-C06"></a>列 6: 1
- <a id="T133-R39-C07"></a>列 7: 1
- <a id="T133-R39-C08"></a>列 8: 
- <a id="T133-R39-C09"></a>列 9: 
- <a id="T133-R39-C10"></a>列 10: 1
- <a id="T133-R39-C11"></a>列 11: 
- <a id="T133-R39-C12"></a>列 12: 

<a id="T133-R40"></a>
**T133-R40**

- <a id="T133-R40-C01"></a>列 1: C13
- <a id="T133-R40-C02"></a>列 2: FER
- <a id="T133-R40-C03"></a>列 3: 4
- <a id="T133-R40-C04"></a>列 4: 3
- <a id="T133-R40-C05"></a>列 5: 1
- <a id="T133-R40-C06"></a>列 6: 1
- <a id="T133-R40-C07"></a>列 7: 
- <a id="T133-R40-C08"></a>列 8: 
- <a id="T133-R40-C09"></a>列 9: 
- <a id="T133-R40-C10"></a>列 10: 
- <a id="T133-R40-C11"></a>列 11: 
- <a id="T133-R40-C12"></a>列 12: 1

<a id="T133-R41"></a>
**T133-R41**

- <a id="T133-R41-C01"></a>列 1: C14
- <a id="T133-R41-C02"></a>列 2: CS
- <a id="T133-R41-C03"></a>列 3: 5
- <a id="T133-R41-C04"></a>列 4: 2
- <a id="T133-R41-C05"></a>列 5: 1
- <a id="T133-R41-C06"></a>列 6: 1
- <a id="T133-R41-C07"></a>列 7: 
- <a id="T133-R41-C08"></a>列 8: 
- <a id="T133-R41-C09"></a>列 9: 1
- <a id="T133-R41-C10"></a>列 10: 
- <a id="T133-R41-C11"></a>列 11: 
- <a id="T133-R41-C12"></a>列 12: 1

<a id="T133-R42"></a>
**T133-R42**

- <a id="T133-R42-C01"></a>列 1: C14
- <a id="T133-R42-C02"></a>列 2: NS
- <a id="T133-R42-C03"></a>列 3: 4
- <a id="T133-R42-C04"></a>列 4: 2
- <a id="T133-R42-C05"></a>列 5: 2
- <a id="T133-R42-C06"></a>列 6: 
- <a id="T133-R42-C07"></a>列 7: 1
- <a id="T133-R42-C08"></a>列 8: 1
- <a id="T133-R42-C09"></a>列 9: 
- <a id="T133-R42-C10"></a>列 10: 
- <a id="T133-R42-C11"></a>列 11: 
- <a id="T133-R42-C12"></a>列 12: 

<a id="T133-R43"></a>
**T133-R43**

- <a id="T133-R43-C01"></a>列 1: C14
- <a id="T133-R43-C02"></a>列 2: FER
- <a id="T133-R43-C03"></a>列 3: 4
- <a id="T133-R43-C04"></a>列 4: 3
- <a id="T133-R43-C05"></a>列 5: 1
- <a id="T133-R43-C06"></a>列 6: 
- <a id="T133-R43-C07"></a>列 7: 1
- <a id="T133-R43-C08"></a>列 8: 
- <a id="T133-R43-C09"></a>列 9: 
- <a id="T133-R43-C10"></a>列 10: 1
- <a id="T133-R43-C11"></a>列 11: 
- <a id="T133-R43-C12"></a>列 12: 

<a id="T133-R44"></a>
**T133-R44**

- <a id="T133-R44-C01"></a>列 1: C15
- <a id="T133-R44-C02"></a>列 2: CS
- <a id="T133-R44-C03"></a>列 3: 5
- <a id="T133-R44-C04"></a>列 4: 1
- <a id="T133-R44-C05"></a>列 5: 2
- <a id="T133-R44-C06"></a>列 6: 1
- <a id="T133-R44-C07"></a>列 7: 1
- <a id="T133-R44-C08"></a>列 8: 
- <a id="T133-R44-C09"></a>列 9: 
- <a id="T133-R44-C10"></a>列 10: 
- <a id="T133-R44-C11"></a>列 11: 1
- <a id="T133-R44-C12"></a>列 12: 

<a id="T133-R45"></a>
**T133-R45**

- <a id="T133-R45-C01"></a>列 1: C15
- <a id="T133-R45-C02"></a>列 2: NS
- <a id="T133-R45-C03"></a>列 3: 4
- <a id="T133-R45-C04"></a>列 4: 3
- <a id="T133-R45-C05"></a>列 5: 1
- <a id="T133-R45-C06"></a>列 6: 
- <a id="T133-R45-C07"></a>列 7: 
- <a id="T133-R45-C08"></a>列 8: 1
- <a id="T133-R45-C09"></a>列 9: 
- <a id="T133-R45-C10"></a>列 10: 
- <a id="T133-R45-C11"></a>列 11: 
- <a id="T133-R45-C12"></a>列 12: 1

<a id="T133-R46"></a>
**T133-R46**

- <a id="T133-R46-C01"></a>列 1: C15
- <a id="T133-R46-C02"></a>列 2: FER
- <a id="T133-R46-C03"></a>列 3: 5
- <a id="T133-R46-C04"></a>列 4: 2
- <a id="T133-R46-C05"></a>列 5: 1
- <a id="T133-R46-C06"></a>列 6: 1
- <a id="T133-R46-C07"></a>列 7: 
- <a id="T133-R46-C08"></a>列 8: 
- <a id="T133-R46-C09"></a>列 9: 1
- <a id="T133-R46-C10"></a>列 10: 1
- <a id="T133-R46-C11"></a>列 11: 
- <a id="T133-R46-C12"></a>列 12: 

<a id="T133-R47"></a>
**T133-R47**

- <a id="T133-R47-C01"></a>列 1: C16
- <a id="T133-R47-C02"></a>列 2: CS
- <a id="T133-R47-C03"></a>列 3: 5
- <a id="T133-R47-C04"></a>列 4: 2
- <a id="T133-R47-C05"></a>列 5: 1
- <a id="T133-R47-C06"></a>列 6: 1
- <a id="T133-R47-C07"></a>列 7: 
- <a id="T133-R47-C08"></a>列 8: 
- <a id="T133-R47-C09"></a>列 9: 
- <a id="T133-R47-C10"></a>列 10: 1
- <a id="T133-R47-C11"></a>列 11: 
- <a id="T133-R47-C12"></a>列 12: 1

<a id="T133-R48"></a>
**T133-R48**

- <a id="T133-R48-C01"></a>列 1: C16
- <a id="T133-R48-C02"></a>列 2: NS
- <a id="T133-R48-C03"></a>列 3: 5
- <a id="T133-R48-C04"></a>列 4: 1
- <a id="T133-R48-C05"></a>列 5: 2
- <a id="T133-R48-C06"></a>列 6: 1
- <a id="T133-R48-C07"></a>列 7: 1
- <a id="T133-R48-C08"></a>列 8: 
- <a id="T133-R48-C09"></a>列 9: 
- <a id="T133-R48-C10"></a>列 10: 
- <a id="T133-R48-C11"></a>列 11: 1
- <a id="T133-R48-C12"></a>列 12: 

<a id="T133-R49"></a>
**T133-R49**

- <a id="T133-R49-C01"></a>列 1: C16
- <a id="T133-R49-C02"></a>列 2: FER
- <a id="T133-R49-C03"></a>列 3: 5
- <a id="T133-R49-C04"></a>列 4: 2
- <a id="T133-R49-C05"></a>列 5: 1
- <a id="T133-R49-C06"></a>列 6: 
- <a id="T133-R49-C07"></a>列 7: 1
- <a id="T133-R49-C08"></a>列 8: 1
- <a id="T133-R49-C09"></a>列 9: 1
- <a id="T133-R49-C10"></a>列 10: 
- <a id="T133-R49-C11"></a>列 11: 
- <a id="T133-R49-C12"></a>列 12: 

<a id="T133-R50"></a>
**T133-R50**

- <a id="T133-R50-C01"></a>列 1: C17
- <a id="T133-R50-C02"></a>列 2: CS
- <a id="T133-R50-C03"></a>列 3: 4
- <a id="T133-R50-C04"></a>列 4: 3
- <a id="T133-R50-C05"></a>列 5: 1
- <a id="T133-R50-C06"></a>列 6: 1
- <a id="T133-R50-C07"></a>列 7: 1
- <a id="T133-R50-C08"></a>列 8: 
- <a id="T133-R50-C09"></a>列 9: 
- <a id="T133-R50-C10"></a>列 10: 
- <a id="T133-R50-C11"></a>列 11: 
- <a id="T133-R50-C12"></a>列 12: 

<a id="T133-R51"></a>
**T133-R51**

- <a id="T133-R51-C01"></a>列 1: C17
- <a id="T133-R51-C02"></a>列 2: NS
- <a id="T133-R51-C03"></a>列 3: 5
- <a id="T133-R51-C04"></a>列 4: 2
- <a id="T133-R51-C05"></a>列 5: 1
- <a id="T133-R51-C06"></a>列 6: 
- <a id="T133-R51-C07"></a>列 7: 
- <a id="T133-R51-C08"></a>列 8: 1
- <a id="T133-R51-C09"></a>列 9: 1
- <a id="T133-R51-C10"></a>列 10: 
- <a id="T133-R51-C11"></a>列 11: 1
- <a id="T133-R51-C12"></a>列 12: 

<a id="T133-R52"></a>
**T133-R52**

- <a id="T133-R52-C01"></a>列 1: C17
- <a id="T133-R52-C02"></a>列 2: FER
- <a id="T133-R52-C03"></a>列 3: 5
- <a id="T133-R52-C04"></a>列 4: 2
- <a id="T133-R52-C05"></a>列 5: 1
- <a id="T133-R52-C06"></a>列 6: 1
- <a id="T133-R52-C07"></a>列 7: 1
- <a id="T133-R52-C08"></a>列 8: 
- <a id="T133-R52-C09"></a>列 9: 
- <a id="T133-R52-C10"></a>列 10: 1
- <a id="T133-R52-C11"></a>列 11: 
- <a id="T133-R52-C12"></a>列 12: 

<a id="T133-R53"></a>
**T133-R53**

- <a id="T133-R53-C01"></a>列 1: C18
- <a id="T133-R53-C02"></a>列 2: CS
- <a id="T133-R53-C03"></a>列 3: 5
- <a id="T133-R53-C04"></a>列 4: 2
- <a id="T133-R53-C05"></a>列 5: 1
- <a id="T133-R53-C06"></a>列 6: 
- <a id="T133-R53-C07"></a>列 7: 1
- <a id="T133-R53-C08"></a>列 8: 1
- <a id="T133-R53-C09"></a>列 9: 1
- <a id="T133-R53-C10"></a>列 10: 
- <a id="T133-R53-C11"></a>列 11: 
- <a id="T133-R53-C12"></a>列 12: 

<a id="T133-R54"></a>
**T133-R54**

- <a id="T133-R54-C01"></a>列 1: C18
- <a id="T133-R54-C02"></a>列 2: NS
- <a id="T133-R54-C03"></a>列 3: 5
- <a id="T133-R54-C04"></a>列 4: 2
- <a id="T133-R54-C05"></a>列 5: 1
- <a id="T133-R54-C06"></a>列 6: 1
- <a id="T133-R54-C07"></a>列 7: 1
- <a id="T133-R54-C08"></a>列 8: 
- <a id="T133-R54-C09"></a>列 9: 
- <a id="T133-R54-C10"></a>列 10: 
- <a id="T133-R54-C11"></a>列 11: 
- <a id="T133-R54-C12"></a>列 12: 1

<a id="T133-R55"></a>
**T133-R55**

- <a id="T133-R55-C01"></a>列 1: C18
- <a id="T133-R55-C02"></a>列 2: FER
- <a id="T133-R55-C03"></a>列 3: 4
- <a id="T133-R55-C04"></a>列 4: 2
- <a id="T133-R55-C05"></a>列 5: 2
- <a id="T133-R55-C06"></a>列 6: 1
- <a id="T133-R55-C07"></a>列 7: 
- <a id="T133-R55-C08"></a>列 8: 
- <a id="T133-R55-C09"></a>列 9: 
- <a id="T133-R55-C10"></a>列 10: 
- <a id="T133-R55-C11"></a>列 11: 1
- <a id="T133-R55-C12"></a>列 12: 

<a id="T133-R56"></a>
**T133-R56**

- <a id="T133-R56-C01"></a>列 1: C19
- <a id="T133-R56-C02"></a>列 2: CS
- <a id="T133-R56-C03"></a>列 3: 5
- <a id="T133-R56-C04"></a>列 4: 2
- <a id="T133-R56-C05"></a>列 5: 1
- <a id="T133-R56-C06"></a>列 6: 1
- <a id="T133-R56-C07"></a>列 7: 1
- <a id="T133-R56-C08"></a>列 8: 
- <a id="T133-R56-C09"></a>列 9: 
- <a id="T133-R56-C10"></a>列 10: 
- <a id="T133-R56-C11"></a>列 11: 
- <a id="T133-R56-C12"></a>列 12: 1

<a id="T133-R57"></a>
**T133-R57**

- <a id="T133-R57-C01"></a>列 1: C19
- <a id="T133-R57-C02"></a>列 2: NS
- <a id="T133-R57-C03"></a>列 3: 5
- <a id="T133-R57-C04"></a>列 4: 2
- <a id="T133-R57-C05"></a>列 5: 1
- <a id="T133-R57-C06"></a>列 6: 
- <a id="T133-R57-C07"></a>列 7: 1
- <a id="T133-R57-C08"></a>列 8: 
- <a id="T133-R57-C09"></a>列 9: 
- <a id="T133-R57-C10"></a>列 10: 1
- <a id="T133-R57-C11"></a>列 11: 1
- <a id="T133-R57-C12"></a>列 12: 

<a id="T133-R58"></a>
**T133-R58**

- <a id="T133-R58-C01"></a>列 1: C19
- <a id="T133-R58-C02"></a>列 2: FER
- <a id="T133-R58-C03"></a>列 3: 4
- <a id="T133-R58-C04"></a>列 4: 3
- <a id="T133-R58-C05"></a>列 5: 1
- <a id="T133-R58-C06"></a>列 6: 
- <a id="T133-R58-C07"></a>列 7: 
- <a id="T133-R58-C08"></a>列 8: 1
- <a id="T133-R58-C09"></a>列 9: 1
- <a id="T133-R58-C10"></a>列 10: 
- <a id="T133-R58-C11"></a>列 11: 
- <a id="T133-R58-C12"></a>列 12: 

<a id="T133-R59"></a>
**T133-R59**

- <a id="T133-R59-C01"></a>列 1: C20
- <a id="T133-R59-C02"></a>列 2: CS
- <a id="T133-R59-C03"></a>列 3: 4
- <a id="T133-R59-C04"></a>列 4: 3
- <a id="T133-R59-C05"></a>列 5: 1
- <a id="T133-R59-C06"></a>列 6: 1
- <a id="T133-R59-C07"></a>列 7: 
- <a id="T133-R59-C08"></a>列 8: 
- <a id="T133-R59-C09"></a>列 9: 1
- <a id="T133-R59-C10"></a>列 10: 
- <a id="T133-R59-C11"></a>列 11: 
- <a id="T133-R59-C12"></a>列 12: 

<a id="T133-R60"></a>
**T133-R60**

- <a id="T133-R60-C01"></a>列 1: C20
- <a id="T133-R60-C02"></a>列 2: NS
- <a id="T133-R60-C03"></a>列 3: 5
- <a id="T133-R60-C04"></a>列 4: 2
- <a id="T133-R60-C05"></a>列 5: 1
- <a id="T133-R60-C06"></a>列 6: 1
- <a id="T133-R60-C07"></a>列 7: 
- <a id="T133-R60-C08"></a>列 8: 
- <a id="T133-R60-C09"></a>列 9: 
- <a id="T133-R60-C10"></a>列 10: 1
- <a id="T133-R60-C11"></a>列 11: 
- <a id="T133-R60-C12"></a>列 12: 1

<a id="T133-R61"></a>
**T133-R61**

- <a id="T133-R61-C01"></a>列 1: C20
- <a id="T133-R61-C02"></a>列 2: FER
- <a id="T133-R61-C03"></a>列 3: 5
- <a id="T133-R61-C04"></a>列 4: 1
- <a id="T133-R61-C05"></a>列 5: 2
- <a id="T133-R61-C06"></a>列 6: 
- <a id="T133-R61-C07"></a>列 7: 1
- <a id="T133-R61-C08"></a>列 8: 1
- <a id="T133-R61-C09"></a>列 9: 
- <a id="T133-R61-C10"></a>列 10: 
- <a id="T133-R61-C11"></a>列 11: 1
- <a id="T133-R61-C12"></a>列 12: 

<a id="T133-R62"></a>
**T133-R62**

- <a id="T133-R62-C01"></a>列 1: 
- <a id="T133-R62-C02"></a>列 2: 
- <a id="T133-R62-C03"></a>列 3: 
- <a id="T133-R62-C04"></a>列 4: 
- <a id="T133-R62-C05"></a>列 5: 
- <a id="T133-R62-C06"></a>列 6: 
- <a id="T133-R62-C07"></a>列 7: 
- <a id="T133-R62-C08"></a>列 8: 
- <a id="T133-R62-C09"></a>列 9: 
- <a id="T133-R62-C10"></a>列 10: 
- <a id="T133-R62-C11"></a>列 11: 
- <a id="T133-R62-C12"></a>列 12: 

<a id="T133-R63"></a>
**T133-R63**

- <a id="T133-R63-C01"></a>列 1（跨列:12）: Lab language assignments: L01=Swedish  |  L02=Mandarin  |  L03=Finnish  |  L04=Mandarin  |  L05=English  |  L06=Mandarin  |  L07=English  |  L08=Mandarin  |  L09=French  |  L10=French  |  L11=German  |  L12=Japanese  |  L13=English  |  L14=Dutch  |  L15=Japanese  |  L16=Mandarin  |  L17=Korean  |  L18=Mandarin  |  L19=English  |  L20=Mandarin

**原文页眉：** 3GPP TSG-SA WG4 Audio SWG AdHoc Meeting on ULBC-MED    S4aA260145<br>Shanghai, China, Sept. 28–30, 2026                                           revision of S4-261622
