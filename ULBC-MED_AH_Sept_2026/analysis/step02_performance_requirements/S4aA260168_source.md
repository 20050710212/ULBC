# S4aA260168 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260168-VoiceAge-Verification of the output signal energy.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    VoiceAge Corporation

<a id="P001"></a>

Title:    Verification of the ULBC output signal energy

<a id="P002"></a>

Document for:    Discussion and Agreement

<a id="P003"></a>

Agenda Item:    4.3

<a id="P005"></a>

Introduction

<a id="P006"></a>

This input addresses potential need for verification of different aspects of the ULBC codec candidates output energy. First, one of the ULBC-MED WID objectives [1] specifies “Achieving at least WB voice coding/decoding”. Second, the ULBC Design Constraints (DC) Permanent Document (Pdoc) [2] comprises a constraint, currently in square brackets, on Output gain tolerance, requiring that "The ULBC candidate codec should neither amplify nor attenuate the output signal significantly relative to the input signal.”. This is further detailed for inactive-speech segments in the Performance Requirements Pdoc [3], also in square brackets.

<a id="P007"></a>

Discussion

<a id="P008"></a>

The following output-signal energy related aspects are of potential interest for gain check:

<a id="P009"></a>

Maximum amplification of the output signal wrt the input signal to prevent MOS score boosting by artificially amplifying active speech signal.

<a id="P010"></a>

Minimum BW, i.e. max attenuation wrt to the input, up to the WB bandwidth, to satisfy the WID objective of “Achieving at least WB voice coding/decoding”.

<a id="P011"></a>

Note: The exact definition of what is WB bandwidth still needs to be clarified, i.e. whether WB is understood up to 7 kHz or up to 8 kHz.

<a id="P012"></a>

Artificial bandwidth extension, i.e. maximum amplification of the higher part of the output signal spectrum which is not present in the input signal.

<a id="P013"></a>

Maximum attenuation for inactive clean speech segments to prevent artificial MOS score boosting by noise gating. Tentative targets for this verifications are included in the ULBC Performance requirements (ULBC-3) for DTX on and DTX off [in square brackets].

<a id="P014"></a>

Maximum attenuation for inactive noisy speech segments to prevent artificial MOS score boosting by noise suppression. Tentative targets for this verifications are included in the ULBC Performance requirements (ULBC-3) for DTX on and DTX off [in square brackets].

<a id="P015"></a>

These aspects can be verified by objective measurement of the output signal energy. Some of them can be evaluated for the whole output signal bandwidth or per frequency bands.

<a id="P016"></a>

Alternatively, it can be assumed that some of the ULBC output signal energy issues are dealt with by proper subjective evaluation methodology. I.e., assuming P.800 DCR test methodology where the CuT is compared to the reference, any deviation from the original signal energy might be penalized as a degradation - to some extent.

<a id="P017"></a>

Finaly, there are two aspects related to the output signal gain:

<a id="P018"></a>

Proper evaluation of candidate codecs that eliminates artificial score improvement by amplifying active signal segments or attenuating inactive signal segments. This issue can be partially addressed by scaling the synthesis signals by means of BS.1770 or P.56.

<a id="P019"></a>

Proper out signal energy for in-field operation of the codec.

<a id="P020"></a>

Open questions

<a id="P021"></a>

Do we need objective verification of the output signal energy? If so, what aspects should be verified?

<a id="P022"></a>

Do we want to scale the output synthesis for the evaluation of the candidate codecs? If so, by which tool?

<a id="P023"></a>

Proposals

<a id="P024"></a>

Maximum amplification of the output signal wrt the input signal - to be verified by an objective tool, specified in the ULBC Processing Plan (ULBC-7).

<a id="P025"></a>

Minimum BW, i.e. max attenuation with respect to the input, up to the WB bandwidth – not to be verified by an objective tool. Implicit verification is expected to be done by the appropriate subjective test methodology (P.800 DCR).

<a id="P026"></a>

Artificial bandwidth extension, i.e. maximum amplification of the higher part of the output signal spectrum which is not present in the input signal - to be verified by an objective tool, specified in the ULBC Processing Plan (ULBC-7).

<a id="P027"></a>

Maximum attenuation for inactive clean speech segments - to be verified by an objective tool, specified in the ULBC Processing Plan (ULBC-7).

<a id="P028"></a>

Maximum attenuation for inactive noisy speech segments - to be verified by an objective tool, specified in the ULBC Processing Plan (ULBC-7).

<a id="P030"></a>

References

<a id="P031"></a>

SP-260696 – New WID on Ultra Low Bitrate Speech Codec for IMS Voice Call over NB-IoT NTN via GEO Satellite.

<a id="P032"></a>

S4-261847 - ULBC Design Constraints (ULBC-4).

<a id="P033"></a>

S4-261771 - ULBC Performance requirements (ULBC-3).

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH    Tdoc S4aA260168<br>    Shanghai, China, September 28-30, 2026    rev of S4aA260159
