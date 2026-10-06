# S4aA260100 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260100_[ULBC-MED]On the Active Frame Rate metric.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPPSA4-(AH) Audio SWG     S4aA260100

<a id="P001"></a>

Shanghai, China, 28 - 30 September 2026

<a id="P004"></a>

Source:    vivo Mobile Communication Co.

<a id="P005"></a>

Title:    [ULBC-MED] On the Active Frame Rate metric: measurements with AMR-WB and EVS

<a id="P006"></a>

Document for:    Discussion and Agreement

<a id="P007"></a>

Agenda item:    4.4

<a id="P009"></a>

## 1    Introduction

<a id="P010"></a>

S4-261557 [1] proposes to add an Active Frame Rate (AFR) requirement to the ULBC-3 performance requirements [2], in the form:

<a id="P011"></a>

AFR(ULBC-MED) < AFR(EVS) + 1 %   (clean speech)

<a id="P012"></a>

AFR(ULBC-MED) < AFR(EVS) + 1 %   (car noise)

<a id="P013"></a>

AFR(ULBC-MED) < AFR(EVS) - 1 %   (street noise)

<a id="P014"></a>

the source agrees with the intent of [1]. The VAD/DTX behaviour of ULBC-MED should be constrained by an objective metric, and AFR is the natural candidate because it is the metric the EVS performance requirements [3] used for the same purpose.

<a id="P015"></a>

In support of the work proposed in [1], the source carried out the measurement. We ran the AMR-WB and EVS reference encoders as complete codecs with DTX enabled over a 48-item corpus and over the full condition matrix of Table 14 of [3], and examined how reproducible the resulting number is. This contribution reports those measurements and identifies the parameters that, in the source's experience, need to be fixed for AFR to give the same answer in any laboratory.

<a id="P016"></a>

The main findings are:

<a id="P017"></a>

-    With DTX on, the AFR at the encoder output is 20 to 30 percentage points above the voice activity factor of the same material (clause 3.2).

<a id="P018"></a>

-    Taking AFR at the VAD decision or at the encoder output changes the indication in 5 of the 18 conditions tested, so the requirement needs to say which is meant (clause 3.3).

<a id="P019"></a>

-    ULBC-MED may use a 40 ms frame with 80/160 ms packetization. Re-gridding the identical 20 ms decisions of EVS onto 40/80/160 ms raises the AFR by 2.2/5.3/10.4 to 2.6/6.4/12.2 percentage points, and the increase depends on the item and on the condition. There is at present no defined method for comparing the AFR of a 40 ms codec against a 20 ms reference (clause 3.4) either in 80/160 ms packetization.

<a id="P020"></a>

-    Different maintenance versions of the EVS reference code give AFRs that differ by up to 5.9 percentage points on the same material, and the sign of the difference reverses with SNR (clause 3.5).

<a id="P021"></a>

-    Feeding EVS at 32 kHz instead of 16 kHz changes the AFR by up to 6.4 percentage points on the same material, even though the encoder selects NB coding in both cases (clause 3.6).

<a id="P022"></a>

-    The spread between items is much larger than the ±1 point margin, so the corpus and the number of items need to be part of the requirement (clause 3.7).

<a id="P023"></a>

Each of these is larger than the ±1 % margin under discussion. On that evidence the source suggests reporting AFR for information rather than using it as a pass/fail requirement (clause 3.8).

<a id="P024"></a>

## 2  Measurement set-up

<a id="P025"></a>

## 2.1  Material

<a id="P026"></a>

48 channels drawn from Switchboard-2 Phase II [11], selected so that the manual audit scores for echo, background noise and distortion are all zero, the speaker gender metadata is consistent, and both sides of the conversation are genuinely speaking. The selection is stratified by gender pairing and across six discs. The P.56 active speech level activity factor of the 48 items has a median of 41.8 % (mean 43.6 %, range 21.6 % to 76.4 %), which matches the "AFR of approximately 40 %" stated for the EVS evaluation database in [3].

<a id="P027"></a>

Each item is 300 s long. The first 60 s is treated as warm-up and is not scored, because the noise estimators of both codecs are still converging: within the first 30 s window the measured activity can be up to 12 percentage points off its settled value. The scoring window is the remaining 240 s, i.e. 12 000 frames of 20 ms.

<a id="P028"></a>

Switchboard-2 is telephone-band material sampled at 8 kHz. Measured over the 48 items, 99 % of the long-term speech energy lies below 3.13 kHz and 99.9 % below 3.66 kHz; the long-term spectrum is 20 dB below its peak at 3.51 kHz. There is no content at all above 4 kHz. This matters for clause 3.6.

<a id="P029"></a>

Switchboard-2 Phase II has no transcription and no time alignment, so no per-frame speech/non-speech ground truth exists. The study therefore makes only relative comparisons, which is also the form used in [3]: the requirement there is AFR(EVS) < min(AFR(AMR VADs)) ± 1 and does not depend on ground truth either.

<a id="P030"></a>

## 2.2  Processing chain

<a id="P031"></a>

Speech is first normalised with ITU-T P.56 [9] to −26 dBov. The clean condition is additionally run at −16 and −36 dBov, obtained by scaling the normalised signal by ±10 dB.

<a id="P032"></a>

Noise is the car, office and street recordings of ITU-T P.501 [10]. Each is downsampled from 32 kHz to 8 kHz and then band-pass filtered to 300–3400 Hz before mixing, so that the nominal SNR is the in-band telephone SNR. Without this band-limiting the SNR axis shifts by a different amount for each noise type, by up to 25.8 dB, because the out-of-band energy of the three noises differs.

<a id="P033"></a>

Mixing is performed at 8 kHz and the mixture is then upsampled to 16 kHz (AMR-WB and the EVS 16 kHz input) or to 32 kHz (the EVS 32 kHz input).

<a id="P034"></a>

Condition matrix: 3 noise types × 5 SNRs (10, 15, 20, 25, 30 dB, all at −26 dBov) plus 3 clean levels (−16, −26, −36 dBov) = 18 conditions per item. With 48 items and 3 systems this is 2 592 encodings.

<a id="P035"></a>

## 2.3  Codecs and reference code versions

<a id="P036"></a>

Table 1: Systems under test.

<a id="T037"></a>

<a id="T037-R01"></a>
**T037-R01**

- <a id="T037-R01-C01"></a>列 1: System
- <a id="T037-R01-C02"></a>列 2: Reference code
- <a id="T037-R01-C03"></a>列 3: Version
- <a id="T037-R01-C04"></a>列 4: Operating point
- <a id="T037-R01-C05"></a>列 5: DTX

<a id="T037-R02"></a>
**T037-R02**

- <a id="T037-R02-C01"></a>列 1: AMR-WB
- <a id="T037-R02-C02"></a>列 2: TS 26.173 [6]
- <a id="T037-R02-C03"></a>列 3: as published
- <a id="T037-R02-C04"></a>列 4: 12.65 kbit/s, 16 kHz input
- <a id="T037-R02-C05"></a>列 5: on (-dtx 2)

<a id="T037-R03"></a>
**T037-R03**

- <a id="T037-R03-C01"></a>列 1: EVS (16 kHz input)
- <a id="T037-R03-C02"></a>列 2: TS 26.442 [4] fixed-point
- <a id="T037-R03-C03"></a>列 3: 16.4.0 (26442-cc0_da0_e60_f40_g40)
- <a id="T037-R03-C04"></a>列 4: 13.2 kbit/s, 16 kHz input
- <a id="T037-R03-C05"></a>列 5: on, adaptive SID (-dtx 0)

<a id="T037-R04"></a>
**T037-R04**

- <a id="T037-R04-C01"></a>列 1: EVS (32 kHz input)
- <a id="T037-R04-C02"></a>列 2: TS 26.442 [4] fixed-point
- <a id="T037-R04-C03"></a>列 3: 16.4.0
- <a id="T037-R04-C04"></a>列 4: 13.2 kbit/s, 32 kHz input
- <a id="T037-R04-C05"></a>列 5: on, adaptive SID (-dtx 0)

<a id="P039"></a>

The fixed-point reference code was chosen because it is bit-exact across architectures, which makes the result reproducible. The floating-point code is not bit-exact across architectures; the resulting AFR differs by 0.05 to 0.12 percentage points between arm64 and x86, with identical per-frame VAD decisions. The encoder sources of fixed-point 16.3.0 and 16.4.0 are identical apart from the version identification lines, and the two produce identical bitstreams.

<a id="P040"></a>

Build validation: the AMR-WB build reproduces the 3GPP test vectors byte for byte for all 9 modes and for the DTX vector, and the 3 decoder vectors. The EVS build carries a single fprintf added after dtx_hangover_addition(), enabled by an environment variable and touching no encoding logic; its bitstream is byte-identical to that of the un-instrumented build.

<a id="P041"></a>

## 2.4  The three quantities reported

<a id="P042"></a>

A VAD decision and what the encoder actually transmits are separated by the DTX state machine, which continues to send speech frames for some time after the VAD has gone inactive and decides when to send SID. The two are not the same number, so this study reports three quantities separately:

<a id="P043"></a>

Table 2: The three quantities.

<a id="T044"></a>

<a id="T044-R01"></a>
**T044-R01**

- <a id="T044-R01-C01"></a>列 1: Quantity
- <a id="T044-R01-C02"></a>列 2: Meaning
- <a id="T044-R01-C03"></a>列 3: How it is obtained

<a id="T044-R02"></a>
**T044-R02**

- <a id="T044-R02-C01"></a>列 1: AFR(raw VAD)
- <a id="T044-R02-C02"></a>列 2: VAD decision before any hangover
- <a id="T044-R02-C03"></a>列 3: EVS: instrumented localVAD. AMR-WB: not exposed by the reference code.

<a id="T044-R03"></a>
**T044-R03**

- <a id="T044-R03-C01"></a>列 1: AFR(VAD)
- <a id="T044-R03-C02"></a>列 2: VAD decision including the VAD's own hangover
- <a id="T044-R03-C03"></a>列 3: AMR-WB: carried in the bitstream — vad_flag is the first parameter of every non-DTX frame. EVS: instrumented vad_flag.

<a id="T044-R04"></a>
**T044-R04**

- <a id="T044-R04-C01"></a>列 1: AFR(transmitted)
- <a id="T044-R04-C02"></a>列 2: Speech frames actually emitted, as a fraction of all frames; SID and NO_DATA excluded
- <a id="T044-R04-C03"></a>列 3: AMR-WB: bitstream frame type. EVS: G.192 frame length (264 bits speech, 48 bits SID, 0 bits NO_DATA).

<a id="P046"></a>

The difference AFR(transmitted) − AFR(VAD) is the contribution of the DTX layer. In AMR-WB it comes from DTX_HANG_CONST = 7 frames in dtx.c, applied conditionally by tx_dtx_handler. In EVS it comes from dtx_hangover_addition() in lib_enc/vad.c.

<a id="P047"></a>

## 3  Results

<a id="P048"></a>

## 3.1  Baseline over the full matrix

<a id="P049"></a>

All figures are percentages of frames in the 240 s scoring window, averaged over the 48 items. EVS is the fixed-point 16.4.0 reference at 13.2 kbit/s.

<a id="P050"></a>

Table 3: AFR of AMR-WB 12.65 kbit/s and EVS 13.2 kbit/s over the full matrix (48 items, 240 s each, DTX on).

<a id="T051"></a>

<a id="T051-R01"></a>
**T051-R01**

- <a id="T051-R01-C01"></a>列 1: Condition
- <a id="T051-R01-C02"></a>列 2: AMR-WB VAD
- <a id="T051-R01-C03"></a>列 3: AMR-WB Tx
- <a id="T051-R01-C04"></a>列 4: AMR-WB DTX layer
- <a id="T051-R01-C05"></a>列 5: EVS 16k raw VAD
- <a id="T051-R01-C06"></a>列 6: EVS 16k VAD
- <a id="T051-R01-C07"></a>列 7: EVS 16k Tx
- <a id="T051-R01-C08"></a>列 8: EVS 16k DTX layer
- <a id="T051-R01-C09"></a>列 9: EVS 32k Tx
- <a id="T051-R01-C10"></a>列 10: EVS 16k − AMR-WB
- <a id="T051-R01-C11"></a>列 11: EVS 32k − AMR-WB

<a id="T051-R02"></a>
**T051-R02**

- <a id="T051-R02-C01"></a>列 1: clean −16 dBov
- <a id="T051-R02-C02"></a>列 2: 73.3
- <a id="T051-R02-C03"></a>列 3: 79.0
- <a id="T051-R02-C04"></a>列 4: +5.6
- <a id="T051-R02-C05"></a>列 5: 78.6
- <a id="T051-R02-C06"></a>列 6: 81.0
- <a id="T051-R02-C07"></a>列 7: 82.8
- <a id="T051-R02-C08"></a>列 8: +1.8
- <a id="T051-R02-C09"></a>列 9: 82.1
- <a id="T051-R02-C10"></a>列 10: +3.8
- <a id="T051-R02-C11"></a>列 11: +3.2

<a id="T051-R03"></a>
**T051-R03**

- <a id="T051-R03-C01"></a>列 1: clean −26 dBov
- <a id="T051-R03-C02"></a>列 2: 56.1
- <a id="T051-R03-C03"></a>列 3: 61.4
- <a id="T051-R03-C04"></a>列 4: +5.2
- <a id="T051-R03-C05"></a>列 5: 67.0
- <a id="T051-R03-C06"></a>列 6: 70.0
- <a id="T051-R03-C07"></a>列 7: 71.5
- <a id="T051-R03-C08"></a>列 8: +1.5
- <a id="T051-R03-C09"></a>列 9: 70.4
- <a id="T051-R03-C10"></a>列 10: +10.1
- <a id="T051-R03-C11"></a>列 11: +9.0

<a id="T051-R04"></a>
**T051-R04**

- <a id="T051-R04-C01"></a>列 1: clean −36 dBov
- <a id="T051-R04-C02"></a>列 2: 44.6
- <a id="T051-R04-C03"></a>列 3: 49.6
- <a id="T051-R04-C04"></a>列 4: +5.0
- <a id="T051-R04-C05"></a>列 5: 55.2
- <a id="T051-R04-C06"></a>列 6: 58.8
- <a id="T051-R04-C07"></a>列 7: 59.6
- <a id="T051-R04-C08"></a>列 8: +0.9
- <a id="T051-R04-C09"></a>列 9: 60.6
- <a id="T051-R04-C10"></a>列 10: +10.0
- <a id="T051-R04-C11"></a>列 11: +11.0

<a id="T051-R05"></a>
**T051-R05**

- <a id="T051-R05-C01"></a>列 1: car 10 dB
- <a id="T051-R05-C02"></a>列 2: 54.4
- <a id="T051-R05-C03"></a>列 3: 58.8
- <a id="T051-R05-C04"></a>列 4: +4.5
- <a id="T051-R05-C05"></a>列 5: 30.8
- <a id="T051-R05-C06"></a>列 6: 42.7
- <a id="T051-R05-C07"></a>列 7: 43.9
- <a id="T051-R05-C08"></a>列 8: +1.2
- <a id="T051-R05-C09"></a>列 9: 42.8
- <a id="T051-R05-C10"></a>列 10: −15.0
- <a id="T051-R05-C11"></a>列 11: −16.1

<a id="T051-R06"></a>
**T051-R06**

- <a id="T051-R06-C01"></a>列 1: car 15 dB
- <a id="T051-R06-C02"></a>列 2: 50.7
- <a id="T051-R06-C03"></a>列 3: 55.0
- <a id="T051-R06-C04"></a>列 4: +4.4
- <a id="T051-R06-C05"></a>列 5: 33.8
- <a id="T051-R06-C06"></a>列 6: 44.1
- <a id="T051-R06-C07"></a>列 7: 44.9
- <a id="T051-R06-C08"></a>列 8: +0.8
- <a id="T051-R06-C09"></a>列 9: 44.4
- <a id="T051-R06-C10"></a>列 10: −10.1
- <a id="T051-R06-C11"></a>列 11: −10.6

<a id="T051-R07"></a>
**T051-R07**

- <a id="T051-R07-C01"></a>列 1: car 20 dB
- <a id="T051-R07-C02"></a>列 2: 50.3
- <a id="T051-R07-C03"></a>列 3: 54.7
- <a id="T051-R07-C04"></a>列 4: +4.4
- <a id="T051-R07-C05"></a>列 5: 36.5
- <a id="T051-R07-C06"></a>列 6: 45.4
- <a id="T051-R07-C07"></a>列 7: 45.7
- <a id="T051-R07-C08"></a>列 8: +0.3
- <a id="T051-R07-C09"></a>列 9: 45.8
- <a id="T051-R07-C10"></a>列 10: −9.1
- <a id="T051-R07-C11"></a>列 11: −8.9

<a id="T051-R08"></a>
**T051-R08**

- <a id="T051-R08-C01"></a>列 1: car 25 dB
- <a id="T051-R08-C02"></a>列 2: 51.3
- <a id="T051-R08-C03"></a>列 3: 55.7
- <a id="T051-R08-C04"></a>列 4: +4.5
- <a id="T051-R08-C05"></a>列 5: 38.5
- <a id="T051-R08-C06"></a>列 6: 46.5
- <a id="T051-R08-C07"></a>列 7: 46.6
- <a id="T051-R08-C08"></a>列 8: +0.1
- <a id="T051-R08-C09"></a>列 9: 47.1
- <a id="T051-R08-C10"></a>列 10: −9.1
- <a id="T051-R08-C11"></a>列 11: −8.6

<a id="T051-R09"></a>
**T051-R09**

- <a id="T051-R09-C01"></a>列 1: car 30 dB
- <a id="T051-R09-C02"></a>列 2: 52.3
- <a id="T051-R09-C03"></a>列 3: 57.0
- <a id="T051-R09-C04"></a>列 4: +4.7
- <a id="T051-R09-C05"></a>列 5: 40.0
- <a id="T051-R09-C06"></a>列 6: 47.9
- <a id="T051-R09-C07"></a>列 7: 48.0
- <a id="T051-R09-C08"></a>列 8: +0.1
- <a id="T051-R09-C09"></a>列 9: 48.7
- <a id="T051-R09-C10"></a>列 10: −9.1
- <a id="T051-R09-C11"></a>列 11: −8.3

<a id="T051-R10"></a>
**T051-R10**

- <a id="T051-R10-C01"></a>列 1: office 10 dB
- <a id="T051-R10-C02"></a>列 2: 62.0
- <a id="T051-R10-C03"></a>列 3: 67.3
- <a id="T051-R10-C04"></a>列 4: +5.4
- <a id="T051-R10-C05"></a>列 5: 35.2
- <a id="T051-R10-C06"></a>列 6: 50.9
- <a id="T051-R10-C07"></a>列 7: 51.6
- <a id="T051-R10-C08"></a>列 8: +0.7
- <a id="T051-R10-C09"></a>列 9: 47.1
- <a id="T051-R10-C10"></a>列 10: −15.7
- <a id="T051-R10-C11"></a>列 11: −20.3

<a id="T051-R11"></a>
**T051-R11**

- <a id="T051-R11-C01"></a>列 1: office 15 dB
- <a id="T051-R11-C02"></a>列 2: 56.7
- <a id="T051-R11-C03"></a>列 3: 61.8
- <a id="T051-R11-C04"></a>列 4: +5.1
- <a id="T051-R11-C05"></a>列 5: 37.2
- <a id="T051-R11-C06"></a>列 6: 50.7
- <a id="T051-R11-C07"></a>列 7: 51.3
- <a id="T051-R11-C08"></a>列 8: +0.6
- <a id="T051-R11-C09"></a>列 9: 48.3
- <a id="T051-R11-C10"></a>列 10: −10.5
- <a id="T051-R11-C11"></a>列 11: −13.5

<a id="T051-R12"></a>
**T051-R12**

- <a id="T051-R12-C01"></a>列 1: office 20 dB
- <a id="T051-R12-C02"></a>列 2: 51.9
- <a id="T051-R12-C03"></a>列 3: 56.5
- <a id="T051-R12-C04"></a>列 4: +4.6
- <a id="T051-R12-C05"></a>列 5: 39.4
- <a id="T051-R12-C06"></a>列 6: 50.9
- <a id="T051-R12-C07"></a>列 7: 51.2
- <a id="T051-R12-C08"></a>列 8: +0.3
- <a id="T051-R12-C09"></a>列 9: 49.8
- <a id="T051-R12-C10"></a>列 10: −5.3
- <a id="T051-R12-C11"></a>列 11: −6.7

<a id="T051-R13"></a>
**T051-R13**

- <a id="T051-R13-C01"></a>列 1: office 25 dB
- <a id="T051-R13-C02"></a>列 2: 49.8
- <a id="T051-R13-C03"></a>列 3: 54.3
- <a id="T051-R13-C04"></a>列 4: +4.4
- <a id="T051-R13-C05"></a>列 5: 40.2
- <a id="T051-R13-C06"></a>列 6: 50.8
- <a id="T051-R13-C07"></a>列 7: 50.9
- <a id="T051-R13-C08"></a>列 8: +0.1
- <a id="T051-R13-C09"></a>列 9: 50.5
- <a id="T051-R13-C10"></a>列 10: −3.3
- <a id="T051-R13-C11"></a>列 11: −3.8

<a id="T051-R14"></a>
**T051-R14**

- <a id="T051-R14-C01"></a>列 1: office 30 dB
- <a id="T051-R14-C02"></a>列 2: 49.8
- <a id="T051-R14-C03"></a>列 3: 54.3
- <a id="T051-R14-C04"></a>列 4: +4.5
- <a id="T051-R14-C05"></a>列 5: 39.7
- <a id="T051-R14-C06"></a>列 6: 49.7
- <a id="T051-R14-C07"></a>列 7: 49.8
- <a id="T051-R14-C08"></a>列 8: +0.0
- <a id="T051-R14-C09"></a>列 9: 50.0
- <a id="T051-R14-C10"></a>列 10: −4.5
- <a id="T051-R14-C11"></a>列 11: −4.2

<a id="T051-R15"></a>
**T051-R15**

- <a id="T051-R15-C01"></a>列 1: street 10 dB
- <a id="T051-R15-C02"></a>列 2: 59.3
- <a id="T051-R15-C03"></a>列 3: 63.4
- <a id="T051-R15-C04"></a>列 4: +4.1
- <a id="T051-R15-C05"></a>列 5: 36.9
- <a id="T051-R15-C06"></a>列 6: 48.4
- <a id="T051-R15-C07"></a>列 7: 50.6
- <a id="T051-R15-C08"></a>列 8: +2.3
- <a id="T051-R15-C09"></a>列 9: 44.3
- <a id="T051-R15-C10"></a>列 10: −12.7
- <a id="T051-R15-C11"></a>列 11: −19.1

<a id="T051-R16"></a>
**T051-R16**

- <a id="T051-R16-C01"></a>列 1: street 15 dB
- <a id="T051-R16-C02"></a>列 2: 49.5
- <a id="T051-R16-C03"></a>列 3: 53.7
- <a id="T051-R16-C04"></a>列 4: +4.1
- <a id="T051-R16-C05"></a>列 5: 38.5
- <a id="T051-R16-C06"></a>列 6: 49.7
- <a id="T051-R16-C07"></a>列 7: 50.8
- <a id="T051-R16-C08"></a>列 8: +1.1
- <a id="T051-R16-C09"></a>列 9: 45.4
- <a id="T051-R16-C10"></a>列 10: −2.9
- <a id="T051-R16-C11"></a>列 11: −8.3

<a id="T051-R17"></a>
**T051-R17**

- <a id="T051-R17-C01"></a>列 1: street 20 dB
- <a id="T051-R17-C02"></a>列 2: 47.3
- <a id="T051-R17-C03"></a>列 3: 51.5
- <a id="T051-R17-C04"></a>列 4: +4.2
- <a id="T051-R17-C05"></a>列 5: 38.2
- <a id="T051-R17-C06"></a>列 6: 48.5
- <a id="T051-R17-C07"></a>列 7: 48.8
- <a id="T051-R17-C08"></a>列 8: +0.4
- <a id="T051-R17-C09"></a>列 9: 46.3
- <a id="T051-R17-C10"></a>列 10: −2.7
- <a id="T051-R17-C11"></a>列 11: −5.2

<a id="T051-R18"></a>
**T051-R18**

- <a id="T051-R18-C01"></a>列 1: street 25 dB
- <a id="T051-R18-C02"></a>列 2: 47.6
- <a id="T051-R18-C03"></a>列 3: 51.9
- <a id="T051-R18-C04"></a>列 4: +4.3
- <a id="T051-R18-C05"></a>列 5: 38.1
- <a id="T051-R18-C06"></a>列 6: 47.6
- <a id="T051-R18-C07"></a>列 7: 47.7
- <a id="T051-R18-C08"></a>列 8: +0.1
- <a id="T051-R18-C09"></a>列 9: 47.1
- <a id="T051-R18-C10"></a>列 10: −4.2
- <a id="T051-R18-C11"></a>列 11: −4.8

<a id="T051-R19"></a>
**T051-R19**

- <a id="T051-R19-C01"></a>列 1: street 30 dB
- <a id="T051-R19-C02"></a>列 2: 48.6
- <a id="T051-R19-C03"></a>列 3: 53.0
- <a id="T051-R19-C04"></a>列 4: +4.5
- <a id="T051-R19-C05"></a>列 5: 38.9
- <a id="T051-R19-C06"></a>列 6: 47.7
- <a id="T051-R19-C07"></a>列 7: 47.9
- <a id="T051-R19-C08"></a>列 8: +0.1
- <a id="T051-R19-C09"></a>列 9: 48.2
- <a id="T051-R19-C10"></a>列 10: −5.2
- <a id="T051-R19-C11"></a>列 11: −4.8

<a id="P052"></a>

The last two columns are the mean of the per-item paired difference at the transmitted layer. AMR-WB's reference code does not expose the raw VAD decision, so it can only be split into two layers.

<a id="P053"></a>

Two features of the baseline are worth noting. In noise neither codec's AFR varies much with SNR: over 10 to 30 dB EVS stays within 43.9 % to 51.6 % and AMR-WB within 51.5 % to 67.3 %. In EVS two effects cancel — the raw VAD decision rises with SNR (car: 30.8 % to 40.0 %) while the VAD hangover falls (+11.9 to +7.9 points). In clean speech EVS exceeds AMR-WB by +3.8 to +10.1 points, most at the lower levels.

<a id="P054"></a>

## 3.2  AFR is not the voice activity factor

<a id="P055"></a>

AFR is commonly described as closely related to the Voice Activity Factor (VAF), and [1] notes the relationship. The measurement shows that, for a complete encoder with DTX on, the two differ substantially. On the same 48 items, whose P.56 activity factor has a median of 41.8 %, the transmitted AFR at clean −26 dBov is 61.4 % for AMR-WB and 71.5 % for EVS: about 20 and about 30 percentage points above the VAF respectively.

<a id="P056"></a>

The gap is the two hangover layers. For EVS at clean −26 dBov the chain is 67.0 % raw VAD, +3.0 points of VAD hangover, +1.5 points of DTX hangover. In noise the VAD layer dominates: at office 10 dB the raw VAD is 35.2 % and the VAD hangover adds 15.7 points.

<a id="P057"></a>

It is worth noting that [3] itself uses the word "AFR" in two senses: for the P.56 activity of the evaluation database ("an AFR of approximately 40 %"), and, in the requirement rows of Table 14, for the codec output. These are two different quantities, and the source suggests that the ULBC-MED requirement use distinct terms for them.

<a id="P058"></a>

## 3.3  What is constrained: the VAD, or the whole VAD/DTX chain?

<a id="P059"></a>

The measurement point is not stated explicitly in Table 14 of [3]. That table names the reference as AFR(AMR-VAD1), AFR(AMR-VAD2) and AFR(AMR-WB) — i.e. VAD algorithms [7][8] — while the same rows also specify "DTX On". Both readings are defensible and they do not give the same answer, so the ULBC-MED requirement will have to choose between them.

<a id="P060"></a>

Table 4 evaluates the comparison of Table 14 of [3] at both measurement points, using the margins of Table 14 (clean +1, car +1, office −1, street 0).

<a id="P061"></a>

Table 4: The same comparison evaluated at the VAD decision and at the encoder output. Mean of the per-item paired difference in percentage points, ± 95 % confidence half-width over the 48 items.

<a id="T062"></a>

<a id="T062-R01"></a>
**T062-R01**

- <a id="T062-R01-C01"></a>列 1: Condition
- <a id="T062-R01-C02"></a>列 2: Margin (points)
- <a id="T062-R01-C03"></a>列 3: EVS − AMR-WB at the VAD decision
- <a id="T062-R01-C04"></a>列 4: Meets margin
- <a id="T062-R01-C05"></a>列 5: EVS − AMR-WB at the encoder output
- <a id="T062-R01-C06"></a>列 6: Meets margin
- <a id="T062-R01-C07"></a>列 7: Verdict

<a id="T062-R02"></a>
**T062-R02**

- <a id="T062-R02-C01"></a>列 1: clean −16 dBov
- <a id="T062-R02-C02"></a>列 2: +1
- <a id="T062-R02-C03"></a>列 3: +7.62 ± 1.88
- <a id="T062-R02-C04"></a>列 4: no
- <a id="T062-R02-C05"></a>列 5: +3.84 ± 1.93
- <a id="T062-R02-C06"></a>列 6: no
- <a id="T062-R02-C07"></a>列 7: 

<a id="T062-R03"></a>
**T062-R03**

- <a id="T062-R03-C01"></a>列 1: clean −26 dBov
- <a id="T062-R03-C02"></a>列 2: +1
- <a id="T062-R03-C03"></a>列 3: +13.83 ± 2.06
- <a id="T062-R03-C04"></a>列 4: no
- <a id="T062-R03-C05"></a>列 5: +10.12 ± 2.28
- <a id="T062-R03-C06"></a>列 6: no
- <a id="T062-R03-C07"></a>列 7: 

<a id="T062-R04"></a>
**T062-R04**

- <a id="T062-R04-C01"></a>列 1: clean −36 dBov
- <a id="T062-R04-C02"></a>列 2: +1
- <a id="T062-R04-C03"></a>列 3: +14.18 ± 1.22
- <a id="T062-R04-C04"></a>列 4: no
- <a id="T062-R04-C05"></a>列 5: +10.04 ± 1.43
- <a id="T062-R04-C06"></a>列 6: no
- <a id="T062-R04-C07"></a>列 7: 

<a id="T062-R05"></a>
**T062-R05**

- <a id="T062-R05-C01"></a>列 1: car 10 dB
- <a id="T062-R05-C02"></a>列 2: +1
- <a id="T062-R05-C03"></a>列 3: −11.70 ± 3.09
- <a id="T062-R05-C04"></a>列 4: yes
- <a id="T062-R05-C05"></a>列 5: −14.98 ± 3.24
- <a id="T062-R05-C06"></a>列 6: yes
- <a id="T062-R05-C07"></a>列 7: 

<a id="T062-R06"></a>
**T062-R06**

- <a id="T062-R06-C01"></a>列 1: car 15 dB
- <a id="T062-R06-C02"></a>列 2: +1
- <a id="T062-R06-C03"></a>列 3: −6.63 ± 1.86
- <a id="T062-R06-C04"></a>列 4: yes
- <a id="T062-R06-C05"></a>列 5: −10.14 ± 2.05
- <a id="T062-R06-C06"></a>列 6: yes
- <a id="T062-R06-C07"></a>列 7: 

<a id="T062-R07"></a>
**T062-R07**

- <a id="T062-R07-C01"></a>列 1: car 20 dB
- <a id="T062-R07-C02"></a>列 2: +1
- <a id="T062-R07-C03"></a>列 3: −4.97 ± 1.54
- <a id="T062-R07-C04"></a>列 4: yes
- <a id="T062-R07-C05"></a>列 5: −9.05 ± 1.75
- <a id="T062-R07-C06"></a>列 6: yes
- <a id="T062-R07-C07"></a>列 7: 

<a id="T062-R08"></a>
**T062-R08**

- <a id="T062-R08-C01"></a>列 1: car 25 dB
- <a id="T062-R08-C02"></a>列 2: +1
- <a id="T062-R08-C03"></a>列 3: −4.72 ± 1.48
- <a id="T062-R08-C04"></a>列 4: yes
- <a id="T062-R08-C05"></a>列 5: −9.15 ± 1.64
- <a id="T062-R08-C06"></a>列 6: yes
- <a id="T062-R08-C07"></a>列 7: 

<a id="T062-R09"></a>
**T062-R09**

- <a id="T062-R09-C01"></a>列 1: car 30 dB
- <a id="T062-R09-C02"></a>列 2: +1
- <a id="T062-R09-C03"></a>列 3: −4.39 ± 1.41
- <a id="T062-R09-C04"></a>列 4: yes
- <a id="T062-R09-C05"></a>列 5: −9.05 ± 1.55
- <a id="T062-R09-C06"></a>列 6: yes
- <a id="T062-R09-C07"></a>列 7: 

<a id="T062-R10"></a>
**T062-R10**

- <a id="T062-R10-C01"></a>列 1: office 10 dB
- <a id="T062-R10-C02"></a>列 2: −1
- <a id="T062-R10-C03"></a>列 3: −11.11 ± 2.18
- <a id="T062-R10-C04"></a>列 4: yes
- <a id="T062-R10-C05"></a>列 5: −15.74 ± 2.23
- <a id="T062-R10-C06"></a>列 6: yes
- <a id="T062-R10-C07"></a>列 7: 

<a id="T062-R11"></a>
**T062-R11**

- <a id="T062-R11-C01"></a>列 1: office 15 dB
- <a id="T062-R11-C02"></a>列 2: −1
- <a id="T062-R11-C03"></a>列 3: −5.99 ± 1.72
- <a id="T062-R11-C04"></a>列 4: yes
- <a id="T062-R11-C05"></a>列 5: −10.49 ± 1.79
- <a id="T062-R11-C06"></a>列 6: yes
- <a id="T062-R11-C07"></a>列 7: 

<a id="T062-R12"></a>
**T062-R12**

- <a id="T062-R12-C01"></a>列 1: office 20 dB
- <a id="T062-R12-C02"></a>列 2: −1
- <a id="T062-R12-C03"></a>列 3: −1.01 ± 1.38
- <a id="T062-R12-C04"></a>列 4: yes
- <a id="T062-R12-C05"></a>列 5: −5.29 ± 1.56
- <a id="T062-R12-C06"></a>列 6: yes
- <a id="T062-R12-C07"></a>列 7: 

<a id="T062-R13"></a>
**T062-R13**

- <a id="T062-R13-C01"></a>列 1: office 25 dB
- <a id="T062-R13-C02"></a>列 2: −1
- <a id="T062-R13-C03"></a>列 3: +0.97 ± 1.01
- <a id="T062-R13-C04"></a>列 4: no
- <a id="T062-R13-C05"></a>列 5: −3.34 ± 1.21
- <a id="T062-R13-C06"></a>列 6: yes
- <a id="T062-R13-C07"></a>列 7: flips

<a id="T062-R14"></a>
**T062-R14**

- <a id="T062-R14-C01"></a>列 1: office 30 dB
- <a id="T062-R14-C02"></a>列 2: −1
- <a id="T062-R14-C03"></a>列 3: −0.01 ± 0.85
- <a id="T062-R14-C04"></a>列 4: no
- <a id="T062-R14-C05"></a>列 5: −4.47 ± 1.04
- <a id="T062-R14-C06"></a>列 6: yes
- <a id="T062-R14-C07"></a>列 7: flips

<a id="T062-R15"></a>
**T062-R15**

- <a id="T062-R15-C01"></a>列 1: street 10 dB
- <a id="T062-R15-C02"></a>列 2: 0
- <a id="T062-R15-C03"></a>列 3: −10.92 ± 2.86
- <a id="T062-R15-C04"></a>列 4: yes
- <a id="T062-R15-C05"></a>列 5: −12.74 ± 2.92
- <a id="T062-R15-C06"></a>列 6: yes
- <a id="T062-R15-C07"></a>列 7: 

<a id="T062-R16"></a>
**T062-R16**

- <a id="T062-R16-C01"></a>列 1: street 15 dB
- <a id="T062-R16-C02"></a>列 2: 0
- <a id="T062-R16-C03"></a>列 3: +0.11 ± 1.99
- <a id="T062-R16-C04"></a>列 4: no
- <a id="T062-R16-C05"></a>列 5: −2.92 ± 2.15
- <a id="T062-R16-C06"></a>列 6: yes
- <a id="T062-R16-C07"></a>列 7: flips

<a id="T062-R17"></a>
**T062-R17**

- <a id="T062-R17-C01"></a>列 1: street 20 dB
- <a id="T062-R17-C02"></a>列 2: 0
- <a id="T062-R17-C03"></a>列 3: +1.15 ± 1.37
- <a id="T062-R17-C04"></a>列 4: no
- <a id="T062-R17-C05"></a>列 5: −2.65 ± 1.59
- <a id="T062-R17-C06"></a>列 6: yes
- <a id="T062-R17-C07"></a>列 7: flips

<a id="T062-R18"></a>
**T062-R18**

- <a id="T062-R18-C01"></a>列 1: street 25 dB
- <a id="T062-R18-C02"></a>列 2: 0
- <a id="T062-R18-C03"></a>列 3: +0.00 ± 1.13
- <a id="T062-R18-C04"></a>列 4: no
- <a id="T062-R18-C05"></a>列 5: −4.18 ± 1.34
- <a id="T062-R18-C06"></a>列 6: yes
- <a id="T062-R18-C07"></a>列 7: flips

<a id="T062-R19"></a>
**T062-R19**

- <a id="T062-R19-C01"></a>列 1: street 30 dB
- <a id="T062-R19-C02"></a>列 2: 0
- <a id="T062-R19-C03"></a>列 3: −0.81 ± 0.84
- <a id="T062-R19-C04"></a>列 4: yes
- <a id="T062-R19-C05"></a>列 5: −5.15 ± 1.05
- <a id="T062-R19-C06"></a>列 6: yes
- <a id="T062-R19-C07"></a>列 7: 

<a id="P063"></a>

This is an indication relative to AMR-WB only. Table 14 of [3] takes the minimum over AMR-VAD1, AMR-VAD2 and AMR-WB; adding the two narrowband AMR VADs can only lower the reference, so the indication above is the favourable case and is not a compliance statement about EVS.

<a id="P064"></a>

The measurement point changes the indication in 5 of the 18 conditions, all in office and street noise where the margin is tightest. Table 3 shows why: the DTX layer adds +4.1 to +5.6 points in AMR-WB, whose hangover is a fixed 7-frame constant, but +0.0 to +2.3 points in EVS at the 16 kHz input and +1.3 to +3.7 points at 32 kHz, where dtx_hangover_addition() is adaptive. Per condition the two differ by up to 4.7 points in the DTX layer alone, and that difference does not appear at the VAD decision.

<a id="P065"></a>

the source’s view: the requirement should constrain the encoder output with DTX enabled, and should say so. Both purposes given in [1] — the transmission and power saving of clause 2.4 and the clipping risk of clause 2.3 — are properties of what is sent. The VAD-only figure is useful for diagnosis but need not be the pass/fail quantity.

<a id="P066"></a>

## 3.4  Frame length and packetisation

<a id="P067"></a>

AMR-WB and EVS both use a 20 ms frame. ULBC-MED is likely expected to use a 40 ms frame, with packetisation of 80 ms or 160 ms. AFR is a count of frames, so the denominator and the resolution of the numerator both change with the frame length, and the quantity is not comparable across codecs with different frame lengths.

<a id="P068"></a>

The size of the effect can be shown from the existing data. A codec whose frame is N × 20 ms cannot resolve activity below its own frame: with detection as good as the 20 ms reference, the best it can do is mark its frame active when any of its 20 ms sub-intervals is active. The same applies to an RTP packet of ptime = N × 20 ms. Aggregating the recorded 20 ms EVS decisions this way therefore gives a lower bound for a coarser-grid codec of equal detection quality.

<a id="P069"></a>

Table 5: The identical EVS 20 ms decisions re-gridded onto coarser frame/packet grids (EVS fixed-point 16.4.0, 16 kHz input, 13.2 kbit/s, 240 s scoring window). Increase relative to the 20 ms grid in brackets, in percentage points.

<a id="T070"></a>

<a id="T070-R01"></a>
**T070-R01**

- <a id="T070-R01-C01"></a>列 1: Item and condition
- <a id="T070-R01-C02"></a>列 2: Measured at
- <a id="T070-R01-C03"></a>列 3: 20 ms
- <a id="T070-R01-C04"></a>列 4: 40 ms
- <a id="T070-R01-C05"></a>列 5: 80 ms
- <a id="T070-R01-C06"></a>列 6: 160 ms

<a id="T070-R02"></a>
**T070-R02**

- <a id="T070-R02-C01"></a>列 1: sw_20203_B, street 10 dB
- <a id="T070-R02-C02"></a>列 2: encoder output
- <a id="T070-R02-C03"></a>列 3: 52.63
- <a id="T070-R02-C04"></a>列 4: 55.18  (+2.55)
- <a id="T070-R02-C05"></a>列 5: 59.00  (+6.37)
- <a id="T070-R02-C06"></a>列 6: 64.80  (+12.17)

<a id="T070-R03"></a>
**T070-R03**

- <a id="T070-R03-C01"></a>列 1: sw_20203_A, office 15 dB
- <a id="T070-R03-C02"></a>列 2: encoder output
- <a id="T070-R03-C03"></a>列 3: 51.90
- <a id="T070-R03-C04"></a>列 4: 54.08  (+2.18)
- <a id="T070-R03-C05"></a>列 5: 57.17  (+5.27)
- <a id="T070-R03-C06"></a>列 6: 62.33  (+10.43)

<a id="T070-R04"></a>
**T070-R04**

- <a id="T070-R04-C01"></a>列 1: sw_20203_B, street 10 dB
- <a id="T070-R04-C02"></a>列 2: VAD decision
- <a id="T070-R04-C03"></a>列 3: 50.52
- <a id="T070-R04-C04"></a>列 4: 53.25  (+2.73)
- <a id="T070-R04-C05"></a>列 5: 57.37  (+6.84)
- <a id="T070-R04-C06"></a>列 6: 63.33  (+12.81)

<a id="T070-R05"></a>
**T070-R05**

- <a id="T070-R05-C01"></a>列 1: sw_20203_A, office 15 dB
- <a id="T070-R05-C02"></a>列 2: VAD decision
- <a id="T070-R05-C03"></a>列 3: 51.37
- <a id="T070-R05-C04"></a>列 4: 53.63  (+2.27)
- <a id="T070-R05-C05"></a>列 5: 56.80  (+5.43)
- <a id="T070-R05-C06"></a>列 6: 62.13  (+10.77)

<a id="T070-R06"></a>
**T070-R06**

- <a id="T070-R06-C01"></a>列 1: sw_20203_B, street 10 dB
- <a id="T070-R06-C02"></a>列 2: raw VAD
- <a id="T070-R06-C03"></a>列 3: 38.90
- <a id="T070-R06-C04"></a>列 4: 42.68  (+3.78)
- <a id="T070-R06-C05"></a>列 5: 48.90  (+10.00)
- <a id="T070-R06-C06"></a>列 6: 56.73  (+17.83)

<a id="T070-R07"></a>
**T070-R07**

- <a id="T070-R07-C01"></a>列 1: sw_20203_A, office 15 dB
- <a id="T070-R07-C02"></a>列 2: raw VAD
- <a id="T070-R07-C03"></a>列 3: 37.98
- <a id="T070-R07-C04"></a>列 4: 41.73  (+3.75)
- <a id="T070-R07-C05"></a>列 5: 47.87  (+9.88)
- <a id="T070-R07-C06"></a>列 6: 55.67  (+17.68)

<a id="P071"></a>

Illustrative. These are two items of the 48 — the two sides of one conversation — so they are not an independent sample; they are shown to establish the order of magnitude, not a corpus average.

<a id="P072"></a>

The inflation is large relative to the margin: 40 ms adds 2.2 to 2.6 points at the encoder output with no change in detection quality, 80 ms adds 5.3 to 6.4 points and 160 ms adds 10.4 to 12.2 points.

<a id="P073"></a>

It is not a constant that could be absorbed into a fixed offset. Between these two items it varies by 0.4 points at 40 ms, 1.1 at 80 ms and 1.7 at 160 ms, and it depends on where the measurement is taken: at the raw VAD decision, whose pattern is more fragmented, the 40 ms penalty is 3.8 points rather than 2.2 to 2.7. It follows the run-length structure of the activity pattern, which changes with noise type, SNR, talker and hangover design.

<a id="P074"></a>

The cause is that many inactive intervals are shorter than the coarser frame. In these two items 14.5 % and 19.3 % are shorter than 40 ms, 31.7 % and 36.3 % shorter than 80 ms, and about 50 % shorter than 160 ms.

<a id="P075"></a>

A method for comparing AFR at 40 ms with AFR at 20 ms under a ±1 point margin therefore still has to be agreed. Two options:

<a id="P076"></a>

-    evaluate both the candidate and the reference after aggregation onto the same, coarser grid, and state the grid with the result; or

<a id="P077"></a>

-    define the metric in the time domain, as the fraction of time covered by transmitted active frames, and accept that the hangover tails of the two codecs are then quantised differently.

<a id="P078"></a>

Either way the grid needs to be part of the requirement, together with whether the metric is per codec frame or per RTP packet: clause 2.4 of [1] counts transmission opportunities, which for ptime 80/160 ms are packets, and Table 5 shows the two answers differ by 5 to 12 points.

<a id="P079"></a>

## 3.5  Dependence on the EVS reference code version

<a id="P080"></a>

Where AFR(EVS) is used as the reference, the reference code version is part of the answer. The VAD of the EVS reference code was re-tuned between maintenance versions, and the effect on AFR is larger than the margin under discussion.

<a id="P081"></a>

Table 6: AFR at the encoder output, EVS 13.2 kbit/s, 16 kHz input, across reference code versions (48 items).

<a id="T082"></a>

<a id="T082-R01"></a>
**T082-R01**

- <a id="T082-R01-C01"></a>列 1: Condition
- <a id="T082-R01-C02"></a>列 2: float 16.1.0
- <a id="T082-R01-C03"></a>列 3: float 16.3.0
- <a id="T082-R01-C04"></a>列 4: fixed 16.4.0
- <a id="T082-R01-C05"></a>列 5: 16.3.0 − 16.1.0 (paired, points)
- <a id="T082-R01-C06"></a>列 6: per-item min / max

<a id="T082-R02"></a>
**T082-R02**

- <a id="T082-R02-C01"></a>列 1: clean −16 dBov
- <a id="T082-R02-C02"></a>列 2: 80.8
- <a id="T082-R02-C03"></a>列 3: 82.7
- <a id="T082-R02-C04"></a>列 4: 82.8
- <a id="T082-R02-C05"></a>列 5: +1.85 ± 2.17
- <a id="T082-R02-C06"></a>列 6: −7.0 / +37.3

<a id="T082-R03"></a>
**T082-R03**

- <a id="T082-R03-C01"></a>列 1: clean −26 dBov
- <a id="T082-R03-C02"></a>列 2: 68.4
- <a id="T082-R03-C03"></a>列 3: 71.9
- <a id="T082-R03-C04"></a>列 4: 71.5
- <a id="T082-R03-C05"></a>列 5: +3.50 ± 2.18
- <a id="T082-R03-C06"></a>列 6: −7.6 / +25.5

<a id="T082-R04"></a>
**T082-R04**

- <a id="T082-R04-C01"></a>列 1: clean −36 dBov
- <a id="T082-R04-C02"></a>列 2: 55.7
- <a id="T082-R04-C03"></a>列 3: 61.6
- <a id="T082-R04-C04"></a>列 4: 59.6
- <a id="T082-R04-C05"></a>列 5: +5.85 ± 1.56
- <a id="T082-R04-C06"></a>列 6: −7.1 / +18.2

<a id="T082-R05"></a>
**T082-R05**

- <a id="T082-R05-C01"></a>列 1: car 10 dB
- <a id="T082-R05-C02"></a>列 2: 42.6
- <a id="T082-R05-C03"></a>列 3: 44.3
- <a id="T082-R05-C04"></a>列 4: 43.9
- <a id="T082-R05-C05"></a>列 5: +1.67 ± 0.41
- <a id="T082-R05-C06"></a>列 6: −2.3 / +4.8

<a id="T082-R06"></a>
**T082-R06**

- <a id="T082-R06-C01"></a>列 1: car 15 dB
- <a id="T082-R06-C02"></a>列 2: 44.9
- <a id="T082-R06-C03"></a>列 3: 45.2
- <a id="T082-R06-C04"></a>列 4: 44.9
- <a id="T082-R06-C05"></a>列 5: +0.29 ± 0.56
- <a id="T082-R06-C06"></a>列 6: −10.7 / +3.1

<a id="T082-R07"></a>
**T082-R07**

- <a id="T082-R07-C01"></a>列 1: car 20 dB
- <a id="T082-R07-C02"></a>列 2: 46.7
- <a id="T082-R07-C03"></a>列 3: 45.8
- <a id="T082-R07-C04"></a>列 4: 45.7
- <a id="T082-R07-C05"></a>列 5: −0.95 ± 0.94
- <a id="T082-R07-C06"></a>列 6: −22.7 / +2.1

<a id="T082-R08"></a>
**T082-R08**

- <a id="T082-R08-C01"></a>列 1: car 25 dB
- <a id="T082-R08-C02"></a>列 2: 48.5
- <a id="T082-R08-C03"></a>列 3: 46.6
- <a id="T082-R08-C04"></a>列 4: 46.6
- <a id="T082-R08-C05"></a>列 5: −1.93 ± 0.78
- <a id="T082-R08-C06"></a>列 6: −19.6 / +0.5

<a id="T082-R09"></a>
**T082-R09**

- <a id="T082-R09-C01"></a>列 1: car 30 dB
- <a id="T082-R09-C02"></a>列 2: 50.8
- <a id="T082-R09-C03"></a>列 3: 48.0
- <a id="T082-R09-C04"></a>列 4: 48.0
- <a id="T082-R09-C05"></a>列 5: −2.79 ± 0.66
- <a id="T082-R09-C06"></a>列 6: −16.8 / −0.6

<a id="T082-R10"></a>
**T082-R10**

- <a id="T082-R10-C01"></a>列 1: office 10 dB
- <a id="T082-R10-C02"></a>列 2: 51.6
- <a id="T082-R10-C03"></a>列 3: 52.7
- <a id="T082-R10-C04"></a>列 4: 51.6
- <a id="T082-R10-C05"></a>列 5: +1.06 ± 0.62
- <a id="T082-R10-C06"></a>列 6: −3.4 / +6.5

<a id="T082-R11"></a>
**T082-R11**

- <a id="T082-R11-C01"></a>列 1: office 15 dB
- <a id="T082-R11-C02"></a>列 2: 51.9
- <a id="T082-R11-C03"></a>列 3: 52.5
- <a id="T082-R11-C04"></a>列 4: 51.3
- <a id="T082-R11-C05"></a>列 5: +0.60 ± 0.49
- <a id="T082-R11-C06"></a>列 6: −3.5 / +4.5

<a id="T082-R12"></a>
**T082-R12**

- <a id="T082-R12-C01"></a>列 1: office 20 dB
- <a id="T082-R12-C02"></a>列 2: 51.8
- <a id="T082-R12-C03"></a>列 3: 51.9
- <a id="T082-R12-C04"></a>列 4: 51.2
- <a id="T082-R12-C05"></a>列 5: +0.11 ± 0.49
- <a id="T082-R12-C06"></a>列 6: −5.4 / +3.9

<a id="T082-R13"></a>
**T082-R13**

- <a id="T082-R13-C01"></a>列 1: office 25 dB
- <a id="T082-R13-C02"></a>列 2: 52.5
- <a id="T082-R13-C03"></a>列 3: 51.2
- <a id="T082-R13-C04"></a>列 4: 50.9
- <a id="T082-R13-C05"></a>列 5: −1.28 ± 0.63
- <a id="T082-R13-C06"></a>列 6: −11.1 / +2.6

<a id="T082-R14"></a>
**T082-R14**

- <a id="T082-R14-C01"></a>列 1: office 30 dB
- <a id="T082-R14-C02"></a>列 2: 53.3
- <a id="T082-R14-C03"></a>列 3: 49.8
- <a id="T082-R14-C04"></a>列 4: 49.8
- <a id="T082-R14-C05"></a>列 5: −3.49 ± 0.73
- <a id="T082-R14-C06"></a>列 6: −16.6 / −0.1

<a id="T082-R15"></a>
**T082-R15**

- <a id="T082-R15-C01"></a>列 1: street 10 dB
- <a id="T082-R15-C02"></a>列 2: 45.1
- <a id="T082-R15-C03"></a>列 3: 50.6
- <a id="T082-R15-C04"></a>列 4: 50.6
- <a id="T082-R15-C05"></a>列 5: +5.47 ± 0.82
- <a id="T082-R15-C06"></a>列 6: −0.6 / +14.3

<a id="T082-R16"></a>
**T082-R16**

- <a id="T082-R16-C01"></a>列 1: street 15 dB
- <a id="T082-R16-C02"></a>列 2: 45.9
- <a id="T082-R16-C03"></a>列 3: 51.6
- <a id="T082-R16-C04"></a>列 4: 50.8
- <a id="T082-R16-C05"></a>列 5: +5.65 ± 1.05
- <a id="T082-R16-C06"></a>列 6: −2.0 / +13.6

<a id="T082-R17"></a>
**T082-R17**

- <a id="T082-R17-C01"></a>列 1: street 20 dB
- <a id="T082-R17-C02"></a>列 2: 46.2
- <a id="T082-R17-C03"></a>列 3: 49.5
- <a id="T082-R17-C04"></a>列 4: 48.8
- <a id="T082-R17-C05"></a>列 5: +3.33 ± 1.05
- <a id="T082-R17-C06"></a>列 6: −2.5 / +13.2

<a id="T082-R18"></a>
**T082-R18**

- <a id="T082-R18-C01"></a>列 1: street 25 dB
- <a id="T082-R18-C02"></a>列 2: 47.7
- <a id="T082-R18-C03"></a>列 3: 47.8
- <a id="T082-R18-C04"></a>列 4: 47.7
- <a id="T082-R18-C05"></a>列 5: +0.15 ± 1.01
- <a id="T082-R18-C06"></a>列 6: −17.0 / +8.2

<a id="T082-R19"></a>
**T082-R19**

- <a id="T082-R19-C01"></a>列 1: street 30 dB
- <a id="T082-R19-C02"></a>列 2: 49.7
- <a id="T082-R19-C03"></a>列 3: 47.8
- <a id="T082-R19-C04"></a>列 4: 47.9
- <a id="T082-R19-C05"></a>列 5: −1.85 ± 0.97
- <a id="T082-R19-C06"></a>列 6: −20.5 / +3.0

<a id="P083"></a>

Floating-point package [5] Rel-16 ends at 16.3.0; the fixed-point package [4] ends at 16.4.0. The two most recent releases of the two implementations agree to within 1.3 points in all 15 noise conditions and 3.0 points in the clean conditions.

<a id="P084"></a>

The sign of the difference reverses with SNR: the newer version is more sensitive in difficult conditions (street 10 dB +5.5 points, clean −36 dBov +5.9) and more conservative in easy ones (car 30 dB −2.8, office 30 dB −3.5).

<a id="P085"></a>

The changes are in comvad_decision.c. The SNR threshold was split by bandwidth and lowered, from tsnr > 4.0 to tsnr > 2.8 for wideband and 2.6 otherwise; the background-noise update condition was relaxed from requiring both vad_flag and vada_flag to be zero to requiring only vad_flag; and several snr_flux thresholds changed, in opposite directions in the floating-point and fixed-point code. The first makes an active decision more likely and the second lowers the estimated SNR, which is consistent with the observed sign reversal. No per-change ablation was run.

<a id="P086"></a>

On single items the difference reaches +14.3 points (sw_20203_B, street 10 dB) against a 48-item mean of +5.5 ± 0.8 for that condition, so a version comparison needs the whole corpus.

<a id="P087"></a>

## 3.6  Bandwidth, input sampling rate, and the bandwidth of the corpus

<a id="P088"></a>

Table 14 of [3] has separate NB, WB and SWB rows with different references — for WB the two narrowband AMR VADs are run on the NB part, for SWB the AMR-WB VAD is additionally run on the WB part. The measurement below indicates that this bandwidth dimension is worth carrying over into the ULBC-MED requirement rather than collapsing it into a single row.

<a id="P089"></a>

First, the operating bandwidth changes the answer. Table 7 gives the paired difference between the 32 kHz and 16 kHz input of the same EVS encoder on identical material.

<a id="P090"></a>

Table 7: Effect of the input sampling rate on the AFR of the same EVS encoder, same items, same mixture (48 items, paired).

<a id="T091"></a>

<a id="T091-R01"></a>
**T091-R01**

- <a id="T091-R01-C01"></a>列 1: Condition
- <a id="T091-R01-C02"></a>列 2: 32 kHz input − 16 kHz input, at the encoder output (points)
- <a id="T091-R01-C03"></a>列 3: … at the VAD decision (points)

<a id="T091-R02"></a>
**T091-R02**

- <a id="T091-R02-C01"></a>列 1: clean −16 dBov
- <a id="T091-R02-C02"></a>列 2: −0.66 ± 0.81
- <a id="T091-R02-C03"></a>列 3: −1.24

<a id="T091-R03"></a>
**T091-R03**

- <a id="T091-R03-C01"></a>列 1: clean −26 dBov
- <a id="T091-R03-C02"></a>列 2: −1.11 ± 0.78
- <a id="T091-R03-C03"></a>列 3: −2.30

<a id="T091-R04"></a>
**T091-R04**

- <a id="T091-R04-C01"></a>列 1: clean −36 dBov
- <a id="T091-R04-C02"></a>列 2: +0.94 ± 0.62
- <a id="T091-R04-C03"></a>列 3: −0.55

<a id="T091-R05"></a>
**T091-R05**

- <a id="T091-R05-C01"></a>列 1: car 10 dB
- <a id="T091-R05-C02"></a>列 2: −1.09 ± 0.19
- <a id="T091-R05-C03"></a>列 3: −2.36

<a id="T091-R06"></a>
**T091-R06**

- <a id="T091-R06-C01"></a>列 1: car 15 dB
- <a id="T091-R06-C02"></a>列 2: −0.47 ± 0.23
- <a id="T091-R06-C03"></a>列 3: −1.60

<a id="T091-R07"></a>
**T091-R07**

- <a id="T091-R07-C01"></a>列 1: car 20 dB
- <a id="T091-R07-C02"></a>列 2: +0.13 ± 0.24
- <a id="T091-R07-C03"></a>列 3: −1.16

<a id="T091-R08"></a>
**T091-R08**

- <a id="T091-R08-C01"></a>列 1: car 25 dB
- <a id="T091-R08-C02"></a>列 2: +0.54 ± 0.18
- <a id="T091-R08-C03"></a>列 3: −0.84

<a id="T091-R09"></a>
**T091-R09**

- <a id="T091-R09-C01"></a>列 1: car 30 dB
- <a id="T091-R09-C02"></a>列 2: +0.71 ± 0.15
- <a id="T091-R09-C03"></a>列 3: −0.68

<a id="T091-R10"></a>
**T091-R10**

- <a id="T091-R10-C01"></a>列 1: office 10 dB
- <a id="T091-R10-C02"></a>列 2: −4.52 ± 0.40
- <a id="T091-R10-C03"></a>列 3: −5.89

<a id="T091-R11"></a>
**T091-R11**

- <a id="T091-R11-C01"></a>列 1: office 15 dB
- <a id="T091-R11-C02"></a>列 2: −3.00 ± 0.29
- <a id="T091-R11-C03"></a>列 3: −4.14

<a id="T091-R12"></a>
**T091-R12**

- <a id="T091-R12-C01"></a>列 1: office 20 dB
- <a id="T091-R12-C02"></a>列 2: −1.42 ± 0.22
- <a id="T091-R12-C03"></a>列 3: −2.64

<a id="T091-R13"></a>
**T091-R13**

- <a id="T091-R13-C01"></a>列 1: office 25 dB
- <a id="T091-R13-C02"></a>列 2: −0.42 ± 0.23
- <a id="T091-R13-C03"></a>列 3: −1.67

<a id="T091-R14"></a>
**T091-R14**

- <a id="T091-R14-C01"></a>列 1: office 30 dB
- <a id="T091-R14-C02"></a>列 2: +0.25 ± 0.16
- <a id="T091-R14-C03"></a>列 3: −1.04

<a id="T091-R15"></a>
**T091-R15**

- <a id="T091-R15-C01"></a>列 1: street 10 dB
- <a id="T091-R15-C02"></a>列 2: −6.36 ± 0.66
- <a id="T091-R15-C03"></a>列 3: −7.81

<a id="T091-R16"></a>
**T091-R16**

- <a id="T091-R16-C01"></a>列 1: street 15 dB
- <a id="T091-R16-C02"></a>列 2: −5.41 ± 0.72
- <a id="T091-R16-C03"></a>列 3: −6.83

<a id="T091-R17"></a>
**T091-R17**

- <a id="T091-R17-C01"></a>列 1: street 20 dB
- <a id="T091-R17-C02"></a>列 2: −2.55 ± 0.60
- <a id="T091-R17-C03"></a>列 3: −3.89

<a id="T091-R18"></a>
**T091-R18**

- <a id="T091-R18-C01"></a>列 1: street 25 dB
- <a id="T091-R18-C02"></a>列 2: −0.61 ± 0.27
- <a id="T091-R18-C03"></a>列 3: −1.94

<a id="T091-R19"></a>
**T091-R19**

- <a id="T091-R19-C01"></a>列 1: street 30 dB
- <a id="T091-R19-C02"></a>列 2: +0.34 ± 0.22
- <a id="T091-R19-C03"></a>列 3: −0.95

<a id="P093"></a>

Second, on this corpus the EVS bandwidth detector classifies the input as NB in 100 % of the scored frames and the encoder codes it as NB, for the 16 kHz and the 32 kHz input alike. The labels "WB" and "SWB" therefore describe the input sampling rate of the test, not the coded bandwidth. Two consequences:

<a id="P094"></a>

-    the differences in Table 7 come from the front end — the CLDFB analysis and the CLDFB-based VAD addition work over a different number of bands at a different sampling rate — not from the coded bandwidth. AFR(EVS) therefore depends on the input sampling rate even at constant coded bandwidth, which is a further parameter to declare;

<a id="P095"></a>

-    for this material the applicable row of Table 14 of [3] would be the NB row, whose reference is min(AFR(AMR-VAD1), AFR(AMR-VAD2)) [7] rather than AMR-WB, so the comparison basis is itself open when the corpus is telephone-band.

<a id="P096"></a>

Third, the corpus has to contain content in the declared band. Switchboard-2 is telephone-band: 99.9 % of its long-term speech energy is below 3.66 kHz and there is nothing above 4 kHz. This applies to the present measurements as much as to any other, and is the main limitation of this data set: the figures here are valid for telephone-band input and should not be read as WB or SWB results.

<a id="P097"></a>

## 3.7  Per-item spread and the size of the margin

<a id="P098"></a>

Table 8 gives the distribution over the 48 items of the same paired difference whose mean appears in Table 3.

<a id="P099"></a>

Table 8: Distribution over the 48 items of the per-item difference EVS(16 kHz) − AMR-WB at the encoder output, in percentage points.

<a id="T100"></a>

<a id="T100-R01"></a>
**T100-R01**

- <a id="T100-R01-C01"></a>列 1: Condition
- <a id="T100-R01-C02"></a>列 2: Margin
- <a id="T100-R01-C03"></a>列 3: Mean
- <a id="T100-R01-C04"></a>列 4: Min
- <a id="T100-R01-C05"></a>列 5: Max
- <a id="T100-R01-C06"></a>列 6: s.d.
- <a id="T100-R01-C07"></a>列 7: Items that would fail on their own

<a id="T100-R02"></a>
**T100-R02**

- <a id="T100-R02-C01"></a>列 1: clean −16 dBov
- <a id="T100-R02-C02"></a>列 2: +1
- <a id="T100-R02-C03"></a>列 3: +3.84
- <a id="T100-R02-C04"></a>列 4: −9.40
- <a id="T100-R02-C05"></a>列 5: +29.43
- <a id="T100-R02-C06"></a>列 6: 6.82
- <a id="T100-R02-C07"></a>列 7: 28 / 48

<a id="T100-R03"></a>
**T100-R03**

- <a id="T100-R03-C01"></a>列 1: clean −26 dBov
- <a id="T100-R03-C02"></a>列 2: +1
- <a id="T100-R03-C03"></a>列 3: +10.12
- <a id="T100-R03-C04"></a>列 4: −5.88
- <a id="T100-R03-C05"></a>列 5: +25.48
- <a id="T100-R03-C06"></a>列 6: 8.06
- <a id="T100-R03-C07"></a>列 7: 40 / 48

<a id="T100-R04"></a>
**T100-R04**

- <a id="T100-R04-C01"></a>列 1: clean −36 dBov
- <a id="T100-R04-C02"></a>列 2: +1
- <a id="T100-R04-C03"></a>列 3: +10.04
- <a id="T100-R04-C04"></a>列 4: −1.03
- <a id="T100-R04-C05"></a>列 5: +20.45
- <a id="T100-R04-C06"></a>列 6: 5.06
- <a id="T100-R04-C07"></a>列 7: 46 / 48

<a id="T100-R05"></a>
**T100-R05**

- <a id="T100-R05-C01"></a>列 1: car 10 dB
- <a id="T100-R05-C02"></a>列 2: +1
- <a id="T100-R05-C03"></a>列 3: −14.98
- <a id="T100-R05-C04"></a>列 4: −55.79
- <a id="T100-R05-C05"></a>列 5: −4.15
- <a id="T100-R05-C06"></a>列 6: 11.46
- <a id="T100-R05-C07"></a>列 7: 0 / 48

<a id="T100-R06"></a>
**T100-R06**

- <a id="T100-R06-C01"></a>列 1: car 15 dB
- <a id="T100-R06-C02"></a>列 2: +1
- <a id="T100-R06-C03"></a>列 3: −10.14
- <a id="T100-R06-C04"></a>列 4: −35.45
- <a id="T100-R06-C05"></a>列 5: −2.92
- <a id="T100-R06-C06"></a>列 6: 7.25
- <a id="T100-R06-C07"></a>列 7: 0 / 48

<a id="T100-R07"></a>
**T100-R07**

- <a id="T100-R07-C01"></a>列 1: car 20 dB
- <a id="T100-R07-C02"></a>列 2: +1
- <a id="T100-R07-C03"></a>列 3: −9.05
- <a id="T100-R07-C04"></a>列 4: −34.26
- <a id="T100-R07-C05"></a>列 5: −2.37
- <a id="T100-R07-C06"></a>列 6: 6.19
- <a id="T100-R07-C07"></a>列 7: 0 / 48

<a id="T100-R08"></a>
**T100-R08**

- <a id="T100-R08-C01"></a>列 1: car 25 dB
- <a id="T100-R08-C02"></a>列 2: +1
- <a id="T100-R08-C03"></a>列 3: −9.15
- <a id="T100-R08-C04"></a>列 4: −28.28
- <a id="T100-R08-C05"></a>列 5: −2.40
- <a id="T100-R08-C06"></a>列 6: 5.81
- <a id="T100-R08-C07"></a>列 7: 0 / 48

<a id="T100-R09"></a>
**T100-R09**

- <a id="T100-R09-C01"></a>列 1: car 30 dB
- <a id="T100-R09-C02"></a>列 2: +1
- <a id="T100-R09-C03"></a>列 3: −9.05
- <a id="T100-R09-C04"></a>列 4: −27.29
- <a id="T100-R09-C05"></a>列 5: −2.77
- <a id="T100-R09-C06"></a>列 6: 5.47
- <a id="T100-R09-C07"></a>列 7: 0 / 48

<a id="T100-R10"></a>
**T100-R10**

- <a id="T100-R10-C01"></a>列 1: office 10 dB
- <a id="T100-R10-C02"></a>列 2: −1
- <a id="T100-R10-C03"></a>列 3: −15.74
- <a id="T100-R10-C04"></a>列 4: −46.44
- <a id="T100-R10-C05"></a>列 5: −3.62
- <a id="T100-R10-C06"></a>列 6: 7.89
- <a id="T100-R10-C07"></a>列 7: 0 / 48

<a id="T100-R11"></a>
**T100-R11**

- <a id="T100-R11-C01"></a>列 1: office 15 dB
- <a id="T100-R11-C02"></a>列 2: −1
- <a id="T100-R11-C03"></a>列 3: −10.49
- <a id="T100-R11-C04"></a>列 4: −37.42
- <a id="T100-R11-C05"></a>列 5: −0.85
- <a id="T100-R11-C06"></a>列 6: 6.34
- <a id="T100-R11-C07"></a>列 7: 1 / 48

<a id="T100-R12"></a>
**T100-R12**

- <a id="T100-R12-C01"></a>列 1: office 20 dB
- <a id="T100-R12-C02"></a>列 2: −1
- <a id="T100-R12-C03"></a>列 3: −5.29
- <a id="T100-R12-C04"></a>列 4: −24.73
- <a id="T100-R12-C05"></a>列 5: +4.87
- <a id="T100-R12-C06"></a>列 6: 5.50
- <a id="T100-R12-C07"></a>列 7: 5 / 48

<a id="T100-R13"></a>
**T100-R13**

- <a id="T100-R13-C01"></a>列 1: office 25 dB
- <a id="T100-R13-C02"></a>列 2: −1
- <a id="T100-R13-C03"></a>列 3: −3.34
- <a id="T100-R13-C04"></a>列 4: −17.04
- <a id="T100-R13-C05"></a>列 5: +5.02
- <a id="T100-R13-C06"></a>列 6: 4.27
- <a id="T100-R13-C07"></a>列 7: 14 / 48

<a id="T100-R14"></a>
**T100-R14**

- <a id="T100-R14-C01"></a>列 1: office 30 dB
- <a id="T100-R14-C02"></a>列 2: −1
- <a id="T100-R14-C03"></a>列 3: −4.47
- <a id="T100-R14-C04"></a>列 4: −18.95
- <a id="T100-R14-C05"></a>列 5: +0.84
- <a id="T100-R14-C06"></a>列 6: 3.69
- <a id="T100-R14-C07"></a>列 7: 5 / 48

<a id="T100-R15"></a>
**T100-R15**

- <a id="T100-R15-C01"></a>列 1: street 10 dB
- <a id="T100-R15-C02"></a>列 2: 0
- <a id="T100-R15-C03"></a>列 3: −12.74
- <a id="T100-R15-C04"></a>列 4: −43.75
- <a id="T100-R15-C05"></a>列 5: +8.65
- <a id="T100-R15-C06"></a>列 6: 10.30
- <a id="T100-R15-C07"></a>列 7: 3 / 48

<a id="T100-R16"></a>
**T100-R16**

- <a id="T100-R16-C01"></a>列 1: street 15 dB
- <a id="T100-R16-C02"></a>列 2: 0
- <a id="T100-R16-C03"></a>列 3: −2.92
- <a id="T100-R16-C04"></a>列 4: −28.41
- <a id="T100-R16-C05"></a>列 5: +13.00
- <a id="T100-R16-C06"></a>列 6: 7.60
- <a id="T100-R16-C07"></a>列 7: 17 / 48

<a id="T100-R17"></a>
**T100-R17**

- <a id="T100-R17-C01"></a>列 1: street 20 dB
- <a id="T100-R17-C02"></a>列 2: 0
- <a id="T100-R17-C03"></a>列 3: −2.65
- <a id="T100-R17-C04"></a>列 4: −18.74
- <a id="T100-R17-C05"></a>列 5: +8.94
- <a id="T100-R17-C06"></a>列 6: 5.62
- <a id="T100-R17-C07"></a>列 7: 15 / 48

<a id="T100-R18"></a>
**T100-R18**

- <a id="T100-R18-C01"></a>列 1: street 25 dB
- <a id="T100-R18-C02"></a>列 2: 0
- <a id="T100-R18-C03"></a>列 3: −4.18
- <a id="T100-R18-C04"></a>列 4: −20.73
- <a id="T100-R18-C05"></a>列 5: +4.70
- <a id="T100-R18-C06"></a>列 6: 4.74
- <a id="T100-R18-C07"></a>列 7: 4 / 48

<a id="T100-R19"></a>
**T100-R19**

- <a id="T100-R19-C01"></a>列 1: street 30 dB
- <a id="T100-R19-C02"></a>列 2: 0
- <a id="T100-R19-C03"></a>列 3: −5.15
- <a id="T100-R19-C04"></a>列 4: −19.23
- <a id="T100-R19-C05"></a>列 5: +0.72
- <a id="T100-R19-C06"></a>列 6: 3.72
- <a id="T100-R19-C07"></a>列 7: 2 / 48

<a id="P102"></a>

At street 15 dB the mean is −2.92 points while the per-item values run from −28.4 to +13.0, and 17 of the 48 items would exceed the margin on their own. A margin of this size is therefore only meaningful if the corpus, the item length and the number of items are fixed, and if the result is reported as a mean with a confidence interval. On this corpus the 95 % confidence half-width of the per-condition mean is 1.04 to 3.24 points.

<a id="P103"></a>

## 3.8  AFR as a pass/fail requirement

<a id="P104"></a>

Clauses 3.3 to 3.7 quantify five things that move AFR without any change in the quality of the voice activity detection. Table 9 collects them against the ±1 point margin.

<a id="P105"></a>

Table 9: What moves AFR, compared with the margin.

<a id="T106"></a>

<a id="T106-R01"></a>
**T106-R01**

- <a id="T106-R01-C01"></a>列 1: Source of variation
- <a id="T106-R01-C02"></a>列 2: Measured effect on AFR
- <a id="T106-R01-C03"></a>列 3: Clause

<a id="T106-R02"></a>
**T106-R02**

- <a id="T106-R02-C01"></a>列 1: Measurement point: VAD decision or encoder output
- <a id="T106-R02-C02"></a>列 2: up to 4.7 points; changes the indication in 5 of the 18 conditions
- <a id="T106-R02-C03"></a>列 3: 3.3

<a id="T106-R03"></a>
**T106-R03**

- <a id="T106-R03-C01"></a>列 1: Frame and packet grid: 20 ms to 40 / 80 / 160 ms
- <a id="T106-R03-C02"></a>列 2: +2.2 to +2.6 / +5.3 to +6.4 / +10.4 to +12.2 points
- <a id="T106-R03-C03"></a>列 3: 3.4

<a id="T106-R04"></a>
**T106-R04**

- <a id="T106-R04-C01"></a>列 1: EVS reference code version
- <a id="T106-R04-C02"></a>列 2: up to 5.9 points, sign reversing with SNR
- <a id="T106-R04-C03"></a>列 3: 3.5

<a id="T106-R05"></a>
**T106-R05**

- <a id="T106-R05-C01"></a>列 1: EVS input sampling rate, coded bandwidth unchanged
- <a id="T106-R05-C02"></a>列 2: up to 6.4 points
- <a id="T106-R05-C03"></a>列 3: 3.6

<a id="T106-R06"></a>
**T106-R06**

- <a id="T106-R06-C01"></a>列 1: Item sampling: 95 % confidence half-width over 48 items
- <a id="T106-R06-C02"></a>列 2: 1.0 to 3.2 points
- <a id="T106-R06-C03"></a>列 3: 3.7

<a id="T106-R07"></a>
**T106-R07**

- <a id="T106-R07-C01"></a>列 1: Choice of reference codec: AMR-WB or EVS
- <a id="T106-R07-C02"></a>列 2: up to 15.7 points
- <a id="T106-R07-C03"></a>列 3: Table 3

<a id="T106-R08"></a>
**T106-R08**

- <a id="T106-R08-C01"></a>列 1: Margin under discussion
- <a id="T106-R08-C02"></a>列 2: ±1 point
- <a id="T106-R08-C03"></a>列 3: [1], [3]

<a id="P108"></a>

Two points follow.

<a id="P109"></a>

First, on this corpus the comparison in Table 14 of [3] is not met in clean speech by the codec it was written for. At the encoder output EVS at 13.2 kbit/s exceeds AMR-WB by +3.8, +10.1 and +10.0 points at −16, −26 and −36 dBov against a +1 point margin, and at the VAD decision by +7.6, +13.8 and +14.2 points (Table 4). Table 14 takes the minimum over three reference VADs, so adding AMR-VAD1 and AMR-VAD2 could only lower the reference and widen the gap.

<a id="P110"></a>

This is not a compliance statement about EVS. The verification EVS passed used the EVS selection database and processing plan, not this corpus. What it shows is that the same requirement text returns a different answer on a different but reasonable database — one that matches the description given in [3], 48 items with a median P.56 activity of 41.8 %. The outcome is therefore a property of the database and the processing chain as much as of the codec.

<a id="P111"></a>

Second, every entry in Table 9 is larger than the ±1 point margin, the largest by ten to fifteen points. A pass/fail bound would need the corpus, the item count, the processing chain, the measurement point, the frame and packet grid, the reference codec, its reference code version, the bandwidth and the input sampling rate all to be fixed, and then verified for every bit rate and every level. Even with all of that fixed, the 95 % confidence half-width on 48 items is 1.04 to 3.24 points, so the margin would still lie inside the confidence interval of the measurement itself.

<a id="P112"></a>

The source therefore suggests reporting AFR for information rather than using it as a pass/fail requirement for ULBC-MED. AFR remains useful as a diagnostic: it is cheap to compute, it makes the behaviour of the DTX chain visible, and a large deviation from a reference is worth following up. What the measurements do not support is a ±1 point bound, which would call for test and specification work out of proportion to what the number can resolve.

<a id="P113"></a>

## 4  Proposal

<a id="P114"></a>

The source offers the following proposals.

<a id="P115"></a>

Proposal 1:    AFR shall be reported for information for ULBC-MED over a defined set of conditions, rather than used as a pass/fail requirement. The VAD/DTX/CNG design is then assessed through the quality evaluation.

<a id="P116"></a>

Proposal 2:    AFR shall be measured on the frames or bundling time emitted by the encoder with DTX enabled. The VAD-decision figure may be reported alongside it.

<a id="P117"></a>

Editor’s Note: If a pass/fail bound is adopted not withstanding Proposal 1, the source proposes that the following be fixed first.

<a id="P118"></a>

[

<a id="P119"></a>

Proposal 3:    The candidate and the reference shall be evaluated on a common time grid, stated with the result, and it shall be stated whether the metric is per codec frame or per RTP packet. Without an agreed grid, AFR values from codecs with different frame lengths should not be compared against a [±1] point margin.

<a id="P120"></a>

Proposal 4:    AMR-WB at 12.65 kbit/s with DTX on is proposed as the reference for VAD, DTX and CNG to follow the current WID statement.

<a id="P121"></a>

Proposal 5:    Every reference shall be identified by specification, Release and reference code version, recorded with the result. For EVS the source proposes the TS 26.442 [4] fixed-point code, which is bit-exact across platforms.

<a id="P122"></a>

Proposal 6:    The operating bandwidth and the input sampling rate of the candidate and of each reference shall be declared, and the test corpus shall contain content in the declared band.

<a id="P123"></a>

Proposal 7:    The corpus, the item length, the number of items, the warm-up interval, the level normalisation, the noise band-limiting and the definition of SNR shall be part of the requirement. Results shall be reported as the mean per-item paired difference with a 95 % confidence interval, and the margin shall be larger than that interval.

<a id="P124"></a>

Proposal 8:    The AFR requirement shall be stated together with the quality requirement it is paired with.

<a id="P125"></a>

]

<a id="P126"></a>

The source can contribute the measurement framework of clause 2 and the per-item results behind Tables 3 to 8, and can extend the measurement to a corpus with genuine wideband content if a WB or SWB requirement is agreed.

<a id="P127"></a>

## 5  References

<a id="P128"></a>

[1]    S4-261557, "[ULBC-MED] Active Frame Rate", Huawei Technologies Co., Ltd., 3GPP TSG-SA4 Meeting #137-e.

<a id="P129"></a>

[2]    3GPP TR 26.940, "Study on Ultra Low Bit Rate Speech Codecs".

<a id="P130"></a>

[3]    S4-130522, "EVS Permanent document (EVS-3): EVS performance requirements".

<a id="P131"></a>

[4]    3GPP TS 26.442, "Codec for Enhanced Voice Services (EVS); ANSI C code (fixed-point)".

<a id="P132"></a>

[5]    3GPP TS 26.443, "Codec for Enhanced Voice Services (EVS); ANSI C code (floating-point)".

<a id="P133"></a>

[6]    3GPP TS 26.173, "Adaptive Multi-Rate - Wideband (AMR-WB) speech codec; ANSI-C code".

<a id="P134"></a>

[7]    3GPP TS 26.094, "Mandatory speech codec speech processing functions; Adaptive Multi-Rate (AMR) speech codec; Voice Activity Detector (VAD)".

<a id="P135"></a>

[8]    3GPP TS 26.194, "Speech codec speech processing functions; Adaptive Multi-Rate - Wideband (AMR-WB) speech codec; Voice Activity Detector (VAD)".

<a id="P136"></a>

[9]    ITU-T Recommendation P.56, "Objective measurement of active speech level".

<a id="P137"></a>

[10]    ITU-T Recommendation P.501, "Test signals for use in telephonometry".

<a id="P138"></a>

[11]    Linguistic Data Consortium, Switchboard-2 Phase II (LDC99S79).

<a id="P139"></a>

[12]    3GPP TS 26.192, "Speech codec speech processing functions; Adaptive Multi-Rate - Wideband (AMR-WB) speech codec; Comfort noise aspects".

<a id="P140"></a>

[13]    3GPP TS 26.193, "Speech codec speech processing functions; Adaptive Multi-Rate - Wideband (AMR-WB) speech codec; Source controlled rate operation".

<a id="P141"></a>

[14]    3GPP TS 26.174, "Speech codec speech processing functions; Adaptive Multi-Rate - Wideband (AMR-WB) speech codec; Test sequences".
