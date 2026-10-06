# S4aA260118 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260118[ULBC-MED] On ULBC Sample Rate.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

3GPP TSG-SA4 Audio SWG (AH) Meeting    S4-260118

<a id="P001"></a>

Shanghai, China, 28-30 September 2026

<a id="P003"></a>

Source:    Huawei Technologies Co., Ltd

<a id="P004"></a>

Title:    [ULBC-MED] On ULBC Sample Rate

<a id="P005"></a>

Agenda item:    4.4

<a id="P006"></a>

Document for:    DISCUSSION & AGREEMENT

<a id="P009"></a>

## 1 Introduction

<a id="P010"></a>

At SA4#137-e, the sampling rate and audio bandwidth discussion has different opinions, so 16 kHz and 32 kHz were both kept in square brackets in ULBC-4 v0.2.0, and the topic was deferred to the Shanghai Audio SWG (AH) meeting. This contribution provides our vision for selecting 16 kHz as the single input/output sampling rate for the Rel-20 ULBC codec.

<a id="P011"></a>

## 2 Discussion

<a id="P012"></a>

## 2.1 Quality considerations at ultra-low bit rates

<a id="P013"></a>

ULBC-3 [6] states that ULBC performance objective is quality not worse than AMR-WB @ 12.65 kbps on all bitrates. For the WB codec. Extending the bandwidth above WB at 1.0-1.4 kbps follow to significant share of the already extremely small bit budget from the most perceptually relevant 50-8000 Hz range to the 8-16 kHz range.

<a id="P014"></a>

Only about 1.5% of the energy of super-wideband speech signals is located in the 8–16 kHz extension band. This average is only exceeded in less than 25% of all active frames. For speech signals transparent quality is acceptable on WB, because almost all energy in human speech is below 8000 Hz. [5]

<a id="P015"></a>

## 2.2 Interoperability with the deployed terrestrial baseline

<a id="P016"></a>

The terrestrial IMS voice baseline is WB: GSMA IR.92 mandates AMR-WB while EVS-SWB is optional, and the ULBC call will commonly terminate towards a terrestrial network or device using AMR-WB.

<a id="P017"></a>

Main part of market (NB/WB)<br>
The structure of current digital broadcasting market is shown on Fig.2. We can see that main part of technologies are still use WB

<a id="P025"></a>

Figure 2. SR used in digital broadcasting [2]

<a id="P027"></a>

Now let’s see these parts of Market and used codecs in more details:

<a id="P028"></a>

WB solutions:

<a id="P029"></a>

VoIP Market → G.722 & AMR-WB (Wideband) [3]

<a id="P030"></a>

Mobile / VoLTE Market → AMR-WB & EVS WB (Wideband) [2]

<a id="P031"></a>

WebRTC → AMR-WB & G.722 (Wideband) [4]

<a id="P033"></a>

SWB: New VoLTE (HD+) → EVS(SWB) [2]

<a id="P034"></a>

So, main part of market belongs to WB. SWB is perspective, but now not big part of market believes in it. In this case it looks reasonable to check in Rel-20 ULBC quality in WB and use other SRs (SWB, FB) in propriet solutions.

<a id="P035"></a>

## 2.3 Internal sampling rate and conversion

<a id="P036"></a>

The input/output sampling rate and the internal (codec) sampling rate shall be equal (16 kHz) and not allow internal down-sampling/up-sampling complicates the complexity (resampling cost) and the comparability of candidates. A single I/O and internal SR make test material development and the reference comparison (AMR-WB is 16 kHz) simple and reproducible.

<a id="P037"></a>

## 2.4 Treatment of SWB capability

<a id="P038"></a>

Candidates may be architected to deliver SR above WB. Such capability can be assessed during characterization, following the EVS practice where modes above the mandatory baseline were characterized rather than gated in qualification/selection. This preserves proponent design freedom, but keep WB a mandatory qualification/selection dimension.

<a id="P039"></a>

## 2.5 Complexity issues using SWB

<a id="P040"></a>

For AI-based codecs, doubling the internal sampling rate approximately doubles the model complexity (e.g., number of strides for a 2x wider band). Under the still-open complexity constraints, using SWB risks either excluding resource-constrained devices or consuming the complexity budget on bandwidth rather than on speech quality and robustness.

<a id="P041"></a>

Of course, it is design-dependent, but reduction of complexity always follows to quality degradation and in SWB case we need to reduce complexity 2 times - not big chance that it will be possible to keep subjective quality.

<a id="P042"></a>

Need to mention that BWE is a way to use SWB without change the model, but quality of BWE is not equal to real SWB and BWE also have some extra complexity.

<a id="P044"></a>

## 2.6 3A algorithm influence to SR

<a id="P045"></a>

During ULBC call the situation when user call from loud outdoor place is really possible. In this case, smartphone 3A algorithm will works to reduce noise and echo, and regularly this algorithm uses WB for voice call [6] (of course, real sampling is on 48kHz or more). More than that, for modern AI-based noise reduction - change from WB to SWB follow to full retraining on new dataset and the same as for ULBC - it follows to double of the complexity. So, it is not looks reasonable, because SWB don’t influence to speech intelligibility.

<a id="P046"></a>

And if vendors will not change their 3A algorithms - all SWB part will be removed, because 3A can’t work with it.

<a id="P048"></a>

## 2.6 Conclusion

<a id="P049"></a>

Using SWB allow to increase signal bandwidth in 2 times and for audiosignal it makes sense, but in speech signal there is only 1.5% of energy concentrated upper 8kHz and almost no parts of phonemes which influence to speech intelligibility are located there.

<a id="P050"></a>

From the other hand - increase bandwidth in 2 times follow to 2x complexity or strong complexity reduction which will highly likely influence to speech quality, including frequencies lower 8kHz (and especially lower 2 kHz) - which are extremely important to speech subjective quality and intelligibility.

<a id="P051"></a>

Also, most part of current voice call 3A algorithms are WB and will remove SWB part.

<a id="P052"></a>

So, it looks not very reasonable for Speech codec like ULBC try to cover high frequencies band, which not consist useful speech information and pay for this by possibility of speech quality and intelligibility degradation.

<a id="P053"></a>

From this point of view - WB looks as enough SR for ULBC. Of course, any codec can have SWB mode, but it is not looks reasonable to evaluate ULBC proponents on SR higher than WB.

<a id="P055"></a>

## 3 Proposals

<a id="P056"></a>

Proposal 1：Combine SR with complexity requirements, or make final decision for SR after ULBC complexity will be agreed.

<a id="P057"></a>

Proposal 2: In ULBC-4, set the mandatory input/output sampling rate of the ULBC codec to 16 kHz, with the internal (codec) sampling rate equal to the I/O sampling rate.

<a id="P058"></a>

Proposal 3: In ULBC-4, keep the mandatory audio bandwidth as at least wideband (WB); coded audio bandwidth above WB is left as proponent design freedom and is assessed, if at all, during the characterization phase, not in qualification/selection testing.

<a id="P059"></a>

Based on Proposals 2 & 3, the Sampling Frequency row of ULBC-4 is proposed to be updated as follows (new text underlined, deleted text in strikethrough):

<a id="T061"></a>

<a id="T061-R01"></a>
**T061-R01**

- <a id="T061-R01-C01"></a>列 1: Parameter
- <a id="T061-R01-C02"></a>列 2: Design constraint
- <a id="T061-R01-C03"></a>列 3: Note

<a id="T061-R02"></a>
**T061-R02**

- <a id="T061-R02-C01"></a>列 1: Sampling Frequency
- <a id="T061-R02-C02"></a>列 2: The ULBC codec shall support PCM audio at the encoder input and at the decoder output at a sampling rate of<br>~~[~~<br>- 16kHz ~~(1513, 1517, 1518, 1564, 1567, 1616)~~<br>~~- 32kHz (1562, 1564, 1586, 1621)~~<br>~~].~~
- <a id="T061-R02-C03"></a>列 3: Editor's note: Competing proposals that ask for internal sampling rate being equal to input/output sampling rate (1567) vs. sampling-rate conversion being allowed but counted (1518).<br>16 kHz and internal (codec) sampling rate equal to the I/O sampling rate.<br>Higher sample rate can be used in ULBC proponents, but will not be evaluated during qualification/selection testing

<a id="P063"></a>

Proposal 4: In ULBC-8 test plans, define the test material bandwidth as WB (16 kHz), directly comparable with the AMR-WB @ 12.65 reference condition; no 32 kHz input condition is foreseen for qualification or selection testing.

<a id="P064"></a>

References

<a id="P066"></a>

[1] 3GPP TR 26.940, "Study on Ultra Low Bit rate Speech Codecs"

<a id="P067"></a>

[2] Transmission of High-quality Sound via Networks Using Speech/Audio Codecs, https://www.ntt-review.jp/archive/ntttechnical.php?contents=ntr201611fa2_s.html

<a id="P068"></a>

[3] Codecs Used in Voice over IP Technologies, https://vocal.com/voip/codecs-used-in-voice-over-ip-technologies/

<a id="P069"></a>

[4] Additional WebRTC Audio Codecs for Interoperability, https://www.rfc-editor.org/rfc/rfc7875.html

<a id="P070"></a>

[5] The perceptual significance of high-frequency energy in the human voice, https://pmc.ncbi.nlm.nih.gov/ articles/PMC4059169/

<a id="P071"></a>

[6] 3GPP TS 26.190 V19.0.0, https://portal.3gpp.org/desktopmodules/Specifications/Specification Details.aspx?specificationId=1424
