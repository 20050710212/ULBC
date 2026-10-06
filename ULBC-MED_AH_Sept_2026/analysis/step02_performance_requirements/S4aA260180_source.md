# S4aA260180 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260180 -ULBC-MED- ULBC Performance requirements (ULBC-3),v0.2.0.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P001"></a>

Source:        ULBC-3 Editor

<a id="P002"></a>

Title:            [ULBC-MED] ULBC Performance requirements (ULBC-3)

<a id="P003"></a>

Version:        0.2.0

<a id="P004"></a>

Document for:    Discussion and Agreement

<a id="P005"></a>

Agenda item:    7.7

<a id="P006"></a>

Work Item:        ULBC-MED

<a id="P008"></a>

## 1. Scope

<a id="P009"></a>

This document presents the Ultra Low Bitrate Codec (ULBC) performance requirements within 3GPP TSG SA4. As a background, TR 26.940 studies performance requirements for a codec supporting the use case of IMS voice services over GEO. It also documents the application scenarios for ultra-low bit rate communication services with a primary focus on Voice over GEO and studies GEO channel features and characteristics.

<a id="P010"></a>

The ULBC performance requirements and objectives specified in this document shall follow the objectives of the ULBC-MED WID, Tdoc SP-260696.

<a id="P012"></a>

All requirements and objectives defined in this document shall be understood as including the statement ‘OR NWT DIRECT (in the respective input bandwidth)’.

<a id="P014"></a>

## 2. Agreed reference codecs

<a id="P015"></a>

## 2.1 Reference codecs for ULBC performance requirements

<a id="P016"></a>

The codecs agreed as reference codecs for ULBC performance requirements are listed the table below.

<a id="P017"></a>

Table 1: Reference codecs for ULBC performance requirements

<a id="T018"></a>

<a id="T018-R01"></a>
**T018-R01**

- <a id="T018-R01-C01"></a>列 1: Reference codec
- <a id="T018-R01-C02"></a>列 2: Important note on usage

<a id="T018-R02"></a>
**T018-R02**

- <a id="T018-R02-C01"></a>列 1: AMR-WB
- <a id="T018-R02-C02"></a>列 2: [The following operating points shall be considered for clean speech and noisy speech testing (where appropriate for transcoding and non-transcoding testing).<br>AMR-WB: 8.85kbps and 12.65kbps]

<a id="T018-R03"></a>
**T018-R03**

- <a id="T018-R03-C01"></a>列 1: [EVS]
- <a id="T018-R03-C02"></a>列 2: [The following operating points shall be considered for clean speech and noisy speech testing (where appropriate for transcoding and non-transcoding testing).<br>EVS-WB: 7.2kbps and 13.2kbps]

<a id="T018-R04"></a>
**T018-R04**

- <a id="T018-R04-C01"></a>列 1: [AMR]
- <a id="T018-R04-C02"></a>列 2: [The following operating points shall be considered for clean speech and noisy speech testing (where appropriate for transcoding and non-transcoding testing).<br>12.2kbps]

<a id="P020"></a>

## 2.2 Reference codecs for ULBC interworking scenarios with existing IMS voice codecs

<a id="P021"></a>

The agreed reference codecs used in ULBC interworking scenarios are listed the table below.

<a id="P022"></a>

Table 2: Reference codecs for ULBC interworking scenarios

<a id="T023"></a>

<a id="T023-R01"></a>
**T023-R01**

- <a id="T023-R01-C01"></a>列 1: Reference codec
- <a id="T023-R01-C02"></a>列 2: Important note on usage

<a id="T023-R02"></a>
**T023-R02**

- <a id="T023-R02-C01"></a>列 1: [AMR-WB]
- <a id="T023-R02-C02"></a>列 2: [The following operating points shall be considered for clean speech and noisy speech testing (where appropriate for transcoding and non-transcoding testing).<br>AMR-WB: 8.85kbps and 12.65kbps]

<a id="T023-R03"></a>
**T023-R03**

- <a id="T023-R03-C01"></a>列 1: [EVS]
- <a id="T023-R03-C02"></a>列 2: [The following operating points shall be considered for clean speech and noisy speech testing (where appropriate for transcoding and non-transcoding testing).<br>EVS-WB: 7.2kbps and 13.2kbps]

<a id="T023-R04"></a>
**T023-R04**

- <a id="T023-R04-C01"></a>列 1: [AMR]
- <a id="T023-R04-C02"></a>列 2: [The following operating points shall be considered for clean speech and noisy speech testing (where appropriate for transcoding and non-transcoding testing).<br>12.2kbps]

<a id="P027"></a>

## 3. General

<a id="P028"></a>

The following considerations apply to performance requirements for the required ULBC bitrate operation modes.

<a id="P029"></a>

Editor’s note: It was agreed at SA4#137-e:

<a id="P030"></a>

Include the testing of -36 dBov, -26 dBov and -16 dBov input signal levels for ULBC qualification and selection testing for clean speech.

<a id="P031"></a>

For background noise types and levels, in qualification applies the principles outlined in Table 1.<br>
<br>
Table 1: Background noise types and levels for ULBC testing of noisy speech

<a id="T032"></a>

<a id="T032-R01"></a>
**T032-R01**

- <a id="T032-R01-C01"></a>列 1: Source Material
- <a id="T032-R01-C02"></a>列 2: Noise type
- <a id="T032-R01-C03"></a>列 3: SNRs
- <a id="T032-R01-C04"></a>列 4: Subjective test methodology

<a id="T032-R02"></a>
**T032-R02**

- <a id="T032-R02-C01"></a>列 1: Speech + Noise
- <a id="T032-R02-C02"></a>列 2: Stationary noise (car)
- <a id="T032-R02-C03"></a>列 3: 15 - 20 dB<br>[20 dB]
- <a id="T032-R02-C04"></a>列 4: ITU-T P.800 DCR

<a id="T032-R03"></a>
**T032-R03**

- <a id="T032-R03-C01"></a>列 1: Speech + Noise
- <a id="T032-R03-C02"></a>列 2: Non-stationary noise (street, office)
- <a id="T032-R03-C03"></a>列 3: 20 - 25 dB<br>[25 dB]
- <a id="T032-R03-C04"></a>列 4: ITU-T P.800 DCR

<a id="P035"></a>

## 4. ULBC Performance Requirements

<a id="P036"></a>

[

<a id="P037"></a>

Editor’s note: It is still under discussion to have separate performance requirements for WB and SWB.

<a id="P038"></a>

## 4.1 Performance Requirements in WB clean and noisy (FER) conditions

<a id="P040"></a>

Table 2: ULBC requirements

<a id="T041"></a>

<a id="T041-R01"></a>
**T041-R01**

- <a id="T041-R01-C01"></a>列 1: Category
- <a id="T041-R01-C02"></a>列 2: Max. BW<br>BW
- <a id="T041-R01-C03"></a>列 3: Bitrate (kbit/s)
- <a id="T041-R01-C04"></a>列 4: Bundling time
- <a id="T041-R01-C05"></a>列 5: FER
- <a id="T041-R01-C06"></a>列 6: DTX
- <a id="T041-R01-C07"></a>列 7: Requirements
- <a id="T041-R01-C08"></a>列 8: Objectives

<a id="T041-R02"></a>
**T041-R02**

- <a id="T041-R02-C01"></a>列 1（纵向合并:restart）: Clean speech<br>-26,-16,-36 dBov
- <a id="T041-R02-C02"></a>列 2（纵向合并:restart）: SWB<br>WB<br>WB
- <a id="T041-R02-C03"></a>列 3: 1.0
- <a id="T041-R02-C04"></a>列 4: [80ms/160ms]
- <a id="T041-R02-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T041-R02-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T041-R02-C07"></a>列 7: NWT AMR-WB @ 12.65<br>NWT AMR-WB @ 8.85
- <a id="T041-R02-C08"></a>列 8: NWT AMR-WB @ 12.65<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R03"></a>
**T041-R03**

- <a id="T041-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T041-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T041-R03-C03"></a>列 3: 1.4
- <a id="T041-R03-C04"></a>列 4: 80ms
- <a id="T041-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T041-R03-C06"></a>列 6（纵向合并:continue）: 
- <a id="T041-R03-C07"></a>列 7: NWT AMR-WB @ 12.65<br>NWT AMR-WB @15.85<br>NWT EVS-WB 13.2 kbps<br>NWT AMR-WB @ 12.65
- <a id="T041-R03-C08"></a>列 8: NWT AMR-WB @ 14.25<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R04"></a>
**T041-R04**

- <a id="T041-R04-C01"></a>列 1（纵向合并:restart）: Clean speech<br> -26 dBov
- <a id="T041-R04-C02"></a>列 2（纵向合并:restart）: SWB<br>WB<br>WB
- <a id="T041-R04-C03"></a>列 3: 1.0
- <a id="T041-R04-C04"></a>列 4: [80ms/160ms]
- <a id="T041-R04-C05"></a>列 5（纵向合并:restart）: x=2%, 6% <br>x=1%, 6% <br>x=[1%, 2% 6%, 10%]
- <a id="T041-R04-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T041-R04-C07"></a>列 7: NWT AMR-WB @ 12.65@x FER<br>NWT AMR-WB @ 8.85
- <a id="T041-R04-C08"></a>列 8: NWT AMR-WB @ 12.65<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R05"></a>
**T041-R05**

- <a id="T041-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T041-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T041-R05-C03"></a>列 3: 1.4
- <a id="T041-R05-C04"></a>列 4: 80ms
- <a id="T041-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T041-R05-C06"></a>列 6（纵向合并:continue）: 
- <a id="T041-R05-C07"></a>列 7: NWT AMR-WB @ 12.65@x FER<br>NWT AMR-WB @15.85@x FER<br>NWT EVS-WB 13.2 kbps@x FER<br>NWT AMR-WB @ 12.65@x FER
- <a id="T041-R05-C08"></a>列 8: NWT AMR-WB @ 14.25<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R06"></a>
**T041-R06**

- <a id="T041-R06-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov, <br>SNR=20dB<br>Noisy speech (Car, Street)<br>-26dBov
- <a id="T041-R06-C02"></a>列 2（纵向合并:restart）: SWB<br>WB<br>WB
- <a id="T041-R06-C03"></a>列 3: 1.0
- <a id="T041-R06-C04"></a>列 4: [80ms/160ms]
- <a id="T041-R06-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T041-R06-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T041-R06-C07"></a>列 7: NWT AMR-WB @ 12.65<br>NWT AMR-WB @8.85<br>NWT AMR-WB @ 8.85
- <a id="T041-R06-C08"></a>列 8: NWT AMR-WB @ 12.65<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R07"></a>
**T041-R07**

- <a id="T041-R07-C01"></a>列 1（纵向合并:continue）: 
- <a id="T041-R07-C02"></a>列 2（纵向合并:continue）: 
- <a id="T041-R07-C03"></a>列 3: 1.4
- <a id="T041-R07-C04"></a>列 4: 80ms
- <a id="T041-R07-C05"></a>列 5（纵向合并:continue）: 
- <a id="T041-R07-C06"></a>列 6（纵向合并:continue）: 
- <a id="T041-R07-C07"></a>列 7: NWT AMR-WB @ 12.65<br>NWT AMR-WB @12.65<br>NWT EVS-WB 13.2 kbps<br>NWT AMR-WB @ 12.65
- <a id="T041-R07-C08"></a>列 8: NWT AMR-WB @ 14.25<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R08"></a>
**T041-R08**

- <a id="T041-R08-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov, <br>SNR=20dB <br>Noisy speech (Car, Street)<br>-26dBov
- <a id="T041-R08-C02"></a>列 2（纵向合并:restart）: SWB<br>WB<br>WB
- <a id="T041-R08-C03"></a>列 3: 1.0
- <a id="T041-R08-C04"></a>列 4: [80ms/160ms]
- <a id="T041-R08-C05"></a>列 5（纵向合并:restart）: x=2%, 6% <br>x=1%, 6%<br>x=[1%, 2% 6%, 10%]
- <a id="T041-R08-C06"></a>列 6（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T041-R08-C07"></a>列 7: NWT AMR-WB @ 12.65@x FER<br>NWT AMR-WB @8.85@x FER
- <a id="T041-R08-C08"></a>列 8: NWT AMR-WB @ 12.65<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R09"></a>
**T041-R09**

- <a id="T041-R09-C01"></a>列 1（纵向合并:continue）: 
- <a id="T041-R09-C02"></a>列 2（纵向合并:continue）: 
- <a id="T041-R09-C03"></a>列 3: 1.4
- <a id="T041-R09-C04"></a>列 4: 80ms
- <a id="T041-R09-C05"></a>列 5（纵向合并:continue）: 
- <a id="T041-R09-C06"></a>列 6（纵向合并:continue）: 
- <a id="T041-R09-C07"></a>列 7: NWT AMR-WB @ 12.65@x FER<br>NWT AMR-WB @12.65@x FER<br>NWT EVS-WB 13.2 kbps@x FER
- <a id="T041-R09-C08"></a>列 8: NWT AMR-WB @ 14.25<br>NWT     AMR-WB @ 12.65<sup>1</sup><br>AMR-WB @ 14.25<br>AMR-WB @ 15.85<br>EVS – WB @ 13.2

<a id="T041-R10"></a>
**T041-R10**

- <a id="T041-R10-C01"></a>列 1（纵向合并:restart）: Mixed content and music<br>single level
- <a id="T041-R10-C02"></a>列 2: SWB<br>WB<br>WB
- <a id="T041-R10-C03"></a>列 3: 1.0
- <a id="T041-R10-C04"></a>列 4: [80ms/160ms]
- <a id="T041-R10-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T041-R10-C06"></a>列 6（纵向合并:restart）: On/Off
- <a id="T041-R10-C07"></a>列 7: Graceful behaviour<sup>‡</sup>
- <a id="T041-R10-C08"></a>列 8: 

<a id="T041-R11"></a>
**T041-R11**

- <a id="T041-R11-C01"></a>列 1（纵向合并:continue）: 
- <a id="T041-R11-C02"></a>列 2: SWB<br>WB<br>WB
- <a id="T041-R11-C03"></a>列 3: 1.4
- <a id="T041-R11-C04"></a>列 4: 80ms
- <a id="T041-R11-C05"></a>列 5（纵向合并:continue）: 
- <a id="T041-R11-C06"></a>列 6（纵向合并:continue）: 
- <a id="T041-R11-C07"></a>列 7: Graceful behaviour<sup>‡</sup>
- <a id="T041-R11-C08"></a>列 8: 

<a id="P042"></a>

Notes:

<a id="P043"></a>

Objective not relevant for 1.4 kbps

<a id="P045"></a>

<sup>† </sup>Reference codecs with DTX on

<a id="P046"></a>

[<sup>‡</sup> Graceful behaviour means …]

<a id="P047"></a>

The FER conditions are simulated with packet loss patterns representative of relevant NB-IoT NTN over GEO channel characteristics at the given FER x. The packet loss patterns are derived according to the principles laid out in TR 26.940.

<a id="P048"></a>

It is anticipated that the compliance of the ULBC with the performance requirement for mixed content and music will be checked during characterization.

<a id="T050"></a>

<a id="T050-R01"></a>
**T050-R01**

- <a id="T050-R01-C01"></a>列 1: Conditions
- <a id="T050-R01-C02"></a>列 2: bitrate
- <a id="T050-R01-C03"></a>列 3: requirements
- <a id="T050-R01-C04"></a>列 4: DTX

<a id="T050-R02"></a>
**T050-R02**

- <a id="T050-R02-C01"></a>列 1: Clean speech 0% BLER
- <a id="T050-R02-C02"></a>列 2: 1 kbps
- <a id="T050-R02-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R02-C04"></a>列 4: On/Off†

<a id="T050-R03"></a>
**T050-R03**

- <a id="T050-R03-C01"></a>列 1: Clean speech, noisy channel
- <a id="T050-R03-C02"></a>列 2: 1 kbps
- <a id="T050-R03-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R03-C04"></a>列 4: On/Off†

<a id="T050-R04"></a>
**T050-R04**

- <a id="T050-R04-C01"></a>列 1: Clean speech 0% BLER
- <a id="T050-R04-C02"></a>列 2: 1.4 kbps
- <a id="T050-R04-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R04-C04"></a>列 4: On/Off†

<a id="T050-R05"></a>
**T050-R05**

- <a id="T050-R05-C01"></a>列 1: Clean speech, noisy channel with < 6% BLER
- <a id="T050-R05-C02"></a>列 2: 1.4 kbps
- <a id="T050-R05-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R05-C04"></a>列 4: On/Off†

<a id="T050-R06"></a>
**T050-R06**

- <a id="T050-R06-C01"></a>列 1: Clean speech, noisy channel with >= 6% BLER
- <a id="T050-R06-C02"></a>列 2: 1.4 kbps
- <a id="T050-R06-C03"></a>列 3: NWT AMRWB-IO 12.65 kbps
- <a id="T050-R06-C04"></a>列 4: On/Off†

<a id="T050-R07"></a>
**T050-R07**

- <a id="T050-R07-C01"></a>列 1: Noisy speech (, 0% BLER
- <a id="T050-R07-C02"></a>列 2: 1 kbps
- <a id="T050-R07-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R07-C04"></a>列 4: On/Off†

<a id="T050-R08"></a>
**T050-R08**

- <a id="T050-R08-C01"></a>列 1: Noisy speech, Noisy channel
- <a id="T050-R08-C02"></a>列 2: 1 kbps
- <a id="T050-R08-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R08-C04"></a>列 4: On/Off†

<a id="T050-R09"></a>
**T050-R09**

- <a id="T050-R09-C01"></a>列 1: Noisy speech, 0% BLER
- <a id="T050-R09-C02"></a>列 2: 1.4 kbps
- <a id="T050-R09-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R09-C04"></a>列 4: On/Off†

<a id="T050-R10"></a>
**T050-R10**

- <a id="T050-R10-C01"></a>列 1: Noisy speech, noisy channel with < 6% BLER
- <a id="T050-R10-C02"></a>列 2: 1.4 kbps
- <a id="T050-R10-C03"></a>列 3: NWT AMRWB 12.65 kbps
- <a id="T050-R10-C04"></a>列 4: On/Off†

<a id="T050-R11"></a>
**T050-R11**

- <a id="T050-R11-C01"></a>列 1: Noisy speech, noisy channel with >= 6% BLER
- <a id="T050-R11-C02"></a>列 2: 1.4 kbps
- <a id="T050-R11-C03"></a>列 3: NWT AMRWB-IO 12.65 kbps
- <a id="T050-R11-C04"></a>列 4: On/Off†

<a id="P051"></a>

Notes:

<a id="P052"></a>

<sup>† </sup>Reference codecs with DTX on [7]

<a id="P053"></a>

The proposal expects selection testing to be done with DTX On mode only [9]

<a id="P054"></a>

Tandeming cases, including, self-tandeming of ULBC should be considered during characterization.

<a id="P055"></a>

The following noise types are proposed to be tested with P.800 ACR: Car, street, office, emergency sirens, forest noise, general audio and music

<a id="T058"></a>

<a id="T058-R01"></a>
**T058-R01**

- <a id="T058-R01-C01"></a>列 1: 
- <a id="T058-R01-C02"></a>列 2: 
- <a id="T058-R01-C03"></a>列 3: 
- <a id="T058-R01-C04"></a>列 4: 

<a id="T058-R02"></a>
**T058-R02**

- <a id="T058-R02-C01"></a>列 1: 
- <a id="T058-R02-C02"></a>列 2: 
- <a id="T058-R02-C03"></a>列 3: 
- <a id="T058-R02-C04"></a>列 4: 

<a id="T058-R03"></a>
**T058-R03**

- <a id="T058-R03-C01"></a>列 1: 
- <a id="T058-R03-C02"></a>列 2: 
- <a id="T058-R03-C03"></a>列 3: 
- <a id="T058-R03-C04"></a>列 4: 

<a id="P062"></a>

Performance Requirements in SWB clean and noisy (FER) conditions

<a id="P064"></a>

Table 2: ULBC requirements

<a id="T065"></a>

<a id="T065-R01"></a>
**T065-R01**

- <a id="T065-R01-C01"></a>列 1: Category
- <a id="T065-R01-C02"></a>列 2: BW
- <a id="T065-R01-C03"></a>列 3: Bitrate (kbit/s)
- <a id="T065-R01-C04"></a>列 4: Bundling time
- <a id="T065-R01-C05"></a>列 5: FER
- <a id="T065-R01-C06"></a>列 6: DTX
- <a id="T065-R01-C07"></a>列 7: Requirements
- <a id="T065-R01-C08"></a>列 8: Objectives

<a id="T065-R02"></a>
**T065-R02**

- <a id="T065-R02-C01"></a>列 1（纵向合并:restart）: Clean speech<br>-26,-16,-36 dBov
- <a id="T065-R02-C02"></a>列 2（纵向合并:restart）: SWB
- <a id="T065-R02-C03"></a>列 3: 1.0
- <a id="T065-R02-C04"></a>列 4: [80ms/160ms]
- <a id="T065-R02-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T065-R02-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T065-R02-C07"></a>列 7: 
- <a id="T065-R02-C08"></a>列 8: 

<a id="T065-R03"></a>
**T065-R03**

- <a id="T065-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T065-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T065-R03-C03"></a>列 3: 1.4
- <a id="T065-R03-C04"></a>列 4: 80ms
- <a id="T065-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T065-R03-C06"></a>列 6（纵向合并:continue）: 
- <a id="T065-R03-C07"></a>列 7: 
- <a id="T065-R03-C08"></a>列 8: 

<a id="T065-R04"></a>
**T065-R04**

- <a id="T065-R04-C01"></a>列 1（纵向合并:restart）: Clean speech<br> -26 dBov
- <a id="T065-R04-C02"></a>列 2（纵向合并:restart）: SWB
- <a id="T065-R04-C03"></a>列 3: 1.0
- <a id="T065-R04-C04"></a>列 4: [80ms/160ms]
- <a id="T065-R04-C05"></a>列 5（纵向合并:restart）: x%= [1%, 2% 6%, 10%]
- <a id="T065-R04-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T065-R04-C07"></a>列 7: 
- <a id="T065-R04-C08"></a>列 8: 

<a id="T065-R05"></a>
**T065-R05**

- <a id="T065-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T065-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T065-R05-C03"></a>列 3: 1.4
- <a id="T065-R05-C04"></a>列 4: 80ms
- <a id="T065-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T065-R05-C06"></a>列 6（纵向合并:continue）: 
- <a id="T065-R05-C07"></a>列 7: 
- <a id="T065-R05-C08"></a>列 8: 

<a id="T065-R06"></a>
**T065-R06**

- <a id="T065-R06-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov<br><br>.
- <a id="T065-R06-C02"></a>列 2（纵向合并:restart）: SWB
- <a id="T065-R06-C03"></a>列 3: 1.0
- <a id="T065-R06-C04"></a>列 4: [80ms/160ms]
- <a id="T065-R06-C05"></a>列 5（纵向合并:restart）: 0%
- <a id="T065-R06-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T065-R06-C07"></a>列 7: 
- <a id="T065-R06-C08"></a>列 8: 

<a id="T065-R07"></a>
**T065-R07**

- <a id="T065-R07-C01"></a>列 1（纵向合并:continue）: 
- <a id="T065-R07-C02"></a>列 2（纵向合并:continue）: 
- <a id="T065-R07-C03"></a>列 3: 1.4
- <a id="T065-R07-C04"></a>列 4: 80ms
- <a id="T065-R07-C05"></a>列 5（纵向合并:continue）: 
- <a id="T065-R07-C06"></a>列 6（纵向合并:continue）: 
- <a id="T065-R07-C07"></a>列 7: 
- <a id="T065-R07-C08"></a>列 8: 

<a id="T065-R08"></a>
**T065-R08**

- <a id="T065-R08-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office, Street)<br>-26dBov
- <a id="T065-R08-C02"></a>列 2（纵向合并:restart）: SWB
- <a id="T065-R08-C03"></a>列 3: 1.0
- <a id="T065-R08-C04"></a>列 4: [80ms/160ms]
- <a id="T065-R08-C05"></a>列 5（纵向合并:restart）: x%=[1%, 2% 6%, 10%]
- <a id="T065-R08-C06"></a>列 6（纵向合并:restart）: [On/Off<sup>†</sup>]
- <a id="T065-R08-C07"></a>列 7: 
- <a id="T065-R08-C08"></a>列 8: 

<a id="T065-R09"></a>
**T065-R09**

- <a id="T065-R09-C01"></a>列 1（纵向合并:continue）: 
- <a id="T065-R09-C02"></a>列 2（纵向合并:continue）: 
- <a id="T065-R09-C03"></a>列 3: 1.4
- <a id="T065-R09-C04"></a>列 4: 80ms
- <a id="T065-R09-C05"></a>列 5（纵向合并:continue）: 
- <a id="T065-R09-C06"></a>列 6（纵向合并:continue）: 
- <a id="T065-R09-C07"></a>列 7: 
- <a id="T065-R09-C08"></a>列 8: 

<a id="P066"></a>

Notes:

<a id="P067"></a>

<sup>† </sup>Reference codecs with DTX on

<a id="P068"></a>

]

<a id="P070"></a>

## 4.2 ULBC Performance Requirements on Interworking

<a id="P071"></a>

[

<a id="P072"></a>

Table 11: Interworking requirements.

<a id="T073"></a>

<a id="T073-R01"></a>
**T073-R01**

- <a id="T073-R01-C01"></a>列 1: Category
- <a id="T073-R01-C02"></a>列 2: Bitrate (kbit/s)
- <a id="T073-R01-C03"></a>列 3: Tandeming Condition
- <a id="T073-R01-C04"></a>列 4: FER<br>Jitter
- <a id="T073-R01-C05"></a>列 5: DTX
- <a id="T073-R01-C06"></a>列 6: Requirements
- <a id="T073-R01-C07"></a>列 7: Objectives
- <a id="T073-R01-C08"></a>列 8: Notes

<a id="T073-R02"></a>
**T073-R02**

- <a id="T073-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-26 dBov), Noisy Speech  (-26dBov)<br>Noise types and SNR to be detailed in test plan
- <a id="T073-R02-C02"></a>列 2: 1.0
- <a id="T073-R02-C03"></a>列 3: Tandeming between ULBC and EVS-SWB 13.2 (both tandems, with Linear 16 PCM  between codecs)<br>Tandeming between ULBC and AMR-WB 12.65 (both tandems, with Linear 16 PCM  between codecs)
- <a id="T073-R02-C04"></a>列 4（纵向合并:restart）: 0% FER
- <a id="T073-R02-C05"></a>列 5（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T073-R02-C06"></a>列 6: NWT AMR-WB@12.65  self-tandeming
- <a id="T073-R02-C07"></a>列 7: NWT AMR-WB@12.65  self-tandeming
- <a id="T073-R02-C08"></a>列 8（纵向合并:restart）: To be tested in  characterization.<br>Synchronization of tandems to be defined in processing plan

<a id="T073-R03"></a>
**T073-R03**

- <a id="T073-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T073-R03-C02"></a>列 2: 1.4
- <a id="T073-R03-C03"></a>列 3: Tandeming between ULBC and EVS-SWB 13.2 (both tandems, with Linear 16 PCM  between codecs)<br>Tandeming between ULBC and AMR-WB 12.65 (both tandems, with Linear 16 PCM  between codecs)
- <a id="T073-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T073-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T073-R03-C06"></a>列 6: NWT AMR-WB@12.65  self-tandeming
- <a id="T073-R03-C07"></a>列 7: NWT EVS-SWB@13.2  self-tandeming
- <a id="T073-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="P076"></a>

Notes:

<a id="P077"></a>

<sup>† </sup>Reference codecs with DTX on

<a id="P079"></a>

More tandeming cases could be considered during characterization, including self-tandeming of ULBC.

<a id="T081"></a>

<a id="T081-R01"></a>
**T081-R01**

- <a id="T081-R01-C01"></a>列 1: Category
- <a id="T081-R01-C02"></a>列 2: Bitrate (kbit/s)
- <a id="T081-R01-C03"></a>列 3: Tandeming Codec<sup>1</sup>
- <a id="T081-R01-C04"></a>列 4: FER<br>Jitter
- <a id="T081-R01-C05"></a>列 5: DTX
- <a id="T081-R01-C06"></a>列 6: Requirements
- <a id="T081-R01-C07"></a>列 7: Objectives
- <a id="T081-R01-C08"></a>列 8: Notes

<a id="T081-R02"></a>
**T081-R02**

- <a id="T081-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-26 dBov), Noisy Speech  (-26dBov)<br>Noise types and SNR to be detailed in test plan
- <a id="T081-R02-C02"></a>列 2（纵向合并:restart）: 1.0
- <a id="T081-R02-C03"></a>列 3: AMR-WB 12.65
- <a id="T081-R02-C04"></a>列 4（纵向合并:restart）: 0% FER
- <a id="T081-R02-C05"></a>列 5（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T081-R02-C06"></a>列 6: NWT AMR-WB@12.65  tandeming with  ULBC WB requirement at 1.0 kbps
- <a id="T081-R02-C07"></a>列 7: 
- <a id="T081-R02-C08"></a>列 8（纵向合并:restart）: To be tested in  characterization.<br>Synchronization of tandems to be defined in processing plan

<a id="T081-R03"></a>
**T081-R03**

- <a id="T081-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T081-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T081-R03-C03"></a>列 3: EVS-SWB 13.2
- <a id="T081-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T081-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T081-R03-C06"></a>列 6: NWT EVS-SWB@13.2  tandeming with ULBC SWB requirement at 1.0 kbps
- <a id="T081-R03-C07"></a>列 7: 
- <a id="T081-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="T081-R04"></a>
**T081-R04**

- <a id="T081-R04-C01"></a>列 1（纵向合并:continue）: 
- <a id="T081-R04-C02"></a>列 2（纵向合并:restart）: 1.4
- <a id="T081-R04-C03"></a>列 3: AMR-WB 12.65
- <a id="T081-R04-C04"></a>列 4（纵向合并:continue）: 
- <a id="T081-R04-C05"></a>列 5（纵向合并:continue）: 
- <a id="T081-R04-C06"></a>列 6: NWT AMR-WB@12.65  tandeming with ULBC WB requirement at 1.4 kbps
- <a id="T081-R04-C07"></a>列 7: 
- <a id="T081-R04-C08"></a>列 8（纵向合并:continue）: 

<a id="T081-R05"></a>
**T081-R05**

- <a id="T081-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T081-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T081-R05-C03"></a>列 3: EVS-SWB 13.2
- <a id="T081-R05-C04"></a>列 4（纵向合并:continue）: 
- <a id="T081-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T081-R05-C06"></a>列 6: NWT EVS-SWB@13.2 tandeming with ULBC SWB requirement at 1.4 kbps
- <a id="T081-R05-C07"></a>列 7: 
- <a id="T081-R05-C08"></a>列 8（纵向合并:continue）: 

<a id="P082"></a>

<sup>1</sup><sup> </sup>Tandeming between ULBC and Tandeming Codec (both tandems, with Linear 16 PCM  between codecs)

<a id="T084"></a>

<a id="T084-R01"></a>
**T084-R01**

- <a id="T084-R01-C01"></a>列 1: Category
- <a id="T084-R01-C02"></a>列 2: FER<br>Jitter
- <a id="T084-R01-C03"></a>列 3: DTX
- <a id="T084-R01-C04"></a>列 4: Bitrate (kbit/s)
- <a id="T084-R01-C05"></a>列 5: Tandeming Condition
- <a id="T084-R01-C06"></a>列 6: Requirements
- <a id="T084-R01-C07"></a>列 7: Objectives
- <a id="T084-R01-C08"></a>列 8: Notes

<a id="T084-R02"></a>
**T084-R02**

- <a id="T084-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-26 dBov), Noisy Speech  (-26dBov)<br>Noise types and SNR to be detailed in test plan
- <a id="T084-R02-C02"></a>列 2（纵向合并:restart）: 0%<br>FER
- <a id="T084-R02-C03"></a>列 3（纵向合并:restart）: On/Off<sup>†</sup>
- <a id="T084-R02-C04"></a>列 4（纵向合并:restart）: 1.0
- <a id="T084-R02-C05"></a>列 5: [Tandeming between ULBC and EVS-SWB 13.2 kbps (both tandems, with Linear 16 PCM  between codecs)]
- <a id="T084-R02-C06"></a>列 6: 
- <a id="T084-R02-C07"></a>列 7: [NWT AMR-WB@12.65  self-tandeming]
- <a id="T084-R02-C08"></a>列 8（纵向合并:restart）: Transcoding remains a necessary interworking mechanism in scenarios where end-to-end ULBC operation cannot be ensured, e.g. when GEO NTN users communicate with terrestrial users operating legacy codecs. Transcoding is required in such cases where end-to-end ULBC operation is not possible (e.g., E911 calls) and is expected to be an important criterion for the service quality.<br><br>Transcoding is to be tested in qualification, selection, and characterization.<br><br>Synchronization of tandems is to be defined in the processing plan<br><br>The details of tandeming test sets for qualification/selection are described in the corresponding test plan.

<a id="T084-R03"></a>
**T084-R03**

- <a id="T084-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T084-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T084-R03-C03"></a>列 3（纵向合并:continue）: 
- <a id="T084-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T084-R03-C05"></a>列 5: Tandeming between ULBC and AMR-WB 12.65 kbps (both tandems, with Linear 16 PCM  between codecs)
- <a id="T084-R03-C06"></a>列 6: [NWT AMR-WB@12.65  self-tandeming]
- <a id="T084-R03-C07"></a>列 7: 
- <a id="T084-R03-C08"></a>列 8（纵向合并:continue）: 

<a id="T084-R04"></a>
**T084-R04**

- <a id="T084-R04-C01"></a>列 1（纵向合并:continue）: 
- <a id="T084-R04-C02"></a>列 2（纵向合并:continue）: 
- <a id="T084-R04-C03"></a>列 3（纵向合并:continue）: 
- <a id="T084-R04-C04"></a>列 4（纵向合并:restart）: 1.4
- <a id="T084-R04-C05"></a>列 5: [Tandeming between ULBC and EVS-SWB 13.2 kbps (both tandems, with Linear 16 PCM  between codecs)]
- <a id="T084-R04-C06"></a>列 6: 
- <a id="T084-R04-C07"></a>列 7: [NWT EVS-SWB@13.2  self-tandeming]
- <a id="T084-R04-C08"></a>列 8（纵向合并:continue）: 

<a id="T084-R05"></a>
**T084-R05**

- <a id="T084-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T084-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T084-R05-C03"></a>列 3（纵向合并:continue）: 
- <a id="T084-R05-C04"></a>列 4（纵向合并:continue）: 
- <a id="T084-R05-C05"></a>列 5: Tandeming between ULBC and AMR-WB 12.65 kbps (both tandems, with Linear 16 PCM  between codecs)
- <a id="T084-R05-C06"></a>列 6: [NWT AMR-WB@12.65  self-tandeming]
- <a id="T084-R05-C07"></a>列 7: 
- <a id="T084-R05-C08"></a>列 8（纵向合并:continue）: 

<a id="P087"></a>

]

<a id="P089"></a>

## 4.3 Performance Requirements under delay-loss conditions:

<a id="P091"></a>

Note: Performance requirements under representative end-to-end loss and delay characteristics including the NB-IoT GEO channel are defined as part of the performance requirements in clean and noisy (FER) conditions, see section 4.1. Specific JBM requirements for ULBC are not defined.

<a id="P094"></a>

## 5. ULBC Objective Performance Requirements

<a id="P095"></a>

## 5.1. ULBC Objective Performance Requirements for DTX operation

<a id="P096"></a>

[

<a id="P097"></a>

Definition of AFR (Active Frame Ratio):

<a id="P098"></a>

AFR (in percentage) = 100 x (# frames that are neither SID nor NO DATA) / (# frames in DTX-off operation)

<a id="P099"></a>

Note: AFR computation does not include the preamble used in the test.

<a id="P101"></a>

Requirements for objective evaluation:

<a id="P102"></a>

This part of the evaluation is based on a large database of speech and noisy speech of length (approximately 10 to 30 min) with an AFR of approximately 40% (AFR is based on P.56 measured on clean speech). The noisy speech database shall be constructed from a clean speech database through addition of noise. The  objective evaluation is detailed in the processing plan.

<a id="P104"></a>

Table 14: AFR requirements for ULBC DTX operation (speech, noisy speech)

<a id="T105"></a>

<a id="T105-R01"></a>
**T105-R01**

- <a id="T105-R01-C01"></a>列 1: Category
- <a id="T105-R01-C02"></a>列 2: Max. BW<br>BW
- <a id="T105-R01-C03"></a>列 3: Bitrate (kbit/s)
- <a id="T105-R01-C04"></a>列 4: FER
- <a id="T105-R01-C05"></a>列 5: DTX
- <a id="T105-R01-C06"></a>列 6: Requirements

<a id="T105-R02"></a>
**T105-R02**

- <a id="T105-R02-C01"></a>列 1（纵向合并:restart）: Clean speech (-16, -26, -36 d Bov)<br>Note: The AFR requirement is verified for every bit rate and every level
- <a id="T105-R02-C02"></a>列 2（纵向合并:restart）: SWB<br>WB
- <a id="T105-R02-C03"></a>列 3: 1.0
- <a id="T105-R02-C04"></a>列 4（纵向合并:restart）: 0% FER
- <a id="T105-R02-C05"></a>列 5（纵向合并:restart）: On
- <a id="T105-R02-C06"></a>列 6（纵向合并:restart）: AFR(ULBC) < AFR(AMR-WB)+ 1%<br>AFR(ULBC-MED) < AFR(EVS) +1<br>AFR(ULBC) ≤ AFR(AMR-WB@12.65 kbit/s, clean speech) + [x] %

<a id="T105-R03"></a>
**T105-R03**

- <a id="T105-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T105-R03-C02"></a>列 2（纵向合并:continue）: 
- <a id="T105-R03-C03"></a>列 3: 1.4
- <a id="T105-R03-C04"></a>列 4（纵向合并:continue）: 
- <a id="T105-R03-C05"></a>列 5（纵向合并:continue）: 
- <a id="T105-R03-C06"></a>列 6（纵向合并:continue）: 

<a id="T105-R04"></a>
**T105-R04**

- <a id="T105-R04-C01"></a>列 1（纵向合并:restart）: Noisy Speech (Car, Office,  Street)  <br>-26 dBov, SNR=20dB<br>Note: For characterization additional SNR levels from 10 to 30 dB and noise types can be added<br>Noisy Speech (Car, Street)  <br>-26 dBov
- <a id="T105-R04-C02"></a>列 2（纵向合并:restart）: SWB<br>WB
- <a id="T105-R04-C03"></a>列 3: 1.0
- <a id="T105-R04-C04"></a>列 4（纵向合并:restart）: 0% FER
- <a id="T105-R04-C05"></a>列 5（纵向合并:restart）: On
- <a id="T105-R04-C06"></a>列 6（纵向合并:restart）: AFR(ULBC) < AFR(AMR-WB)+ 1%<br>AFR(ULBC-MED) < AFR(EVS) +1<br>AFR(ULBC) ≤ AFR(AMR-WB@12.65 kbit/s, clean speech) + [x] %

<a id="T105-R05"></a>
**T105-R05**

- <a id="T105-R05-C01"></a>列 1（纵向合并:continue）: 
- <a id="T105-R05-C02"></a>列 2（纵向合并:continue）: 
- <a id="T105-R05-C03"></a>列 3: 1.4
- <a id="T105-R05-C04"></a>列 4（纵向合并:continue）: 
- <a id="T105-R05-C05"></a>列 5（纵向合并:continue）: 
- <a id="T105-R05-C06"></a>列 6（纵向合并:continue）: 

<a id="P107"></a>

Note: When measuring AFR for comparability, the same ptime as for AMR-WB and ULBC needs to be assumed, where a corresponding bundle of frames is counted as active frame if any of the frames within the bundle is active.

<a id="P108"></a>

]

<a id="P110"></a>

## 5.2. ULBC Objective Performance Requirements on background noise handling

<a id="P111"></a>

[

<a id="P113"></a>

For clean speech (-26 dBov) the following requirements apply:

<a id="P114"></a>

For DTX turned off, the background noise level during inactive regions of the CuT shall be attenuated by no more than [6] dB, at the decoder output, compared to the background noise level during inactive regions of the input signal.

<a id="P115"></a>

For DTX turned on, the background noise level during inactive regions of the CuT shall be attenuated by no more than [12] dB, at the decoder output, as compared to the background noise level during inactive regions of the input signal.

<a id="P116"></a>

The measurement method for attenuation in inactive regions shall ignore very low energy frames of (recording) background noise in clean speech.

<a id="P118"></a>

For noisy speech (-26 dBov) and each tested noise type the following requirements apply:

<a id="P119"></a>

For DTX turned off, the background noise level during inactive regions of the CuT shall be attenuated by no more than [4] dB, at the decoder output, compared to the background noise level during inactive regions of the input signal.

<a id="P120"></a>

For DTX turned on, the background noise level during inactive regions of the CuT shall be attenuated by no more than [12] dB, at the decoder output, as compared to the background noise level during inactive regions of the input signal.

<a id="P121"></a>

]

<a id="P125"></a>

History

<a id="T127"></a>

<a id="T127-R01"></a>
**T127-R01**

- <a id="T127-R01-C01"></a>列 1: Version
- <a id="T127-R01-C02"></a>列 2: Date
- <a id="T127-R01-C03"></a>列 3: Tdoc
- <a id="T127-R01-C04"></a>列 4: Comment

<a id="T127-R02"></a>
**T127-R02**

- <a id="T127-R02-C01"></a>列 1: 0.0.1
- <a id="T127-R02-C02"></a>列 2: 
- <a id="T127-R02-C03"></a>列 3: S4-261708
- <a id="T127-R02-C04"></a>列 4: Initial version

<a id="T127-R03"></a>
**T127-R03**

- <a id="T127-R03-C01"></a>列 1: 0.1.0
- <a id="T127-R03-C02"></a>列 2: 2026-08-26
- <a id="T127-R03-C03"></a>列 3: S4-261771
- <a id="T127-R03-C04"></a>列 4: Merge version incorporation proposals from Tdocs 1552, 1620, 1566, 1641

<a id="T127-R04"></a>
**T127-R04**

- <a id="T127-R04-C01"></a>列 1: 0.1.1
- <a id="T127-R04-C02"></a>列 2: 2026-09-29
- <a id="T127-R04-C03"></a>列 3: 
- <a id="T127-R04-C04"></a>列 4: Merge version incorporation proposals from Tdocs 120 (Fraunhofer, tandeming) 162 (Lenovo/Motorola, tandeming) 121 (Dolby, requirements, noise types) 122 (Dolby, AFR requirements) 143 (Apple, requirements) 148 (Fraunhofer, quality stairs) 153 (Qualcomm, SNR)

<a id="T127-R05"></a>
**T127-R05**

- <a id="T127-R05-C01"></a>列 1: 0.2.0
- <a id="T127-R05-C02"></a>列 2: 2026-09-30
- <a id="T127-R05-C03"></a>列 3: S4aA260180
- <a id="T127-R05-C04"></a>列 4: Online updates during Audio SWG session based on v0.1.1

## 原文批注与定位

- 批注 2：Apple(143)；位置：T018-R02-C02
- 批注 10：Apple(143)；位置：T018-R03-C02
- 批注 17：Apple(143)；位置：T018-R04-C02
- 批注 25：Apple(143)；位置：T023-R02-C02
- 批注 31：Apple(143)；位置：T023-R03-C02
- 批注 38：Apple(143)；位置：T023-R04-C02
- 批注 44：QC(153)；位置：T032-R02-C03
- 批注 49：QC(153)；位置：T032-R03-C03
- 批注 53：FhG(148)；位置：T041-R02-C08
- 批注 63：FhG(148)；位置：T041-R03-C08
- 批注 74：FhG(148)；位置：T041-R04-C08
- 批注 84：FhG(148)；位置：T041-R05-C08
- 批注 94：FhG(148)；位置：T041-R06-C08
- 批注 105：FhG(148)；位置：T041-R07-C08
- 批注 116：FhG(148)；位置：T041-R08-C08
- 批注 132：FhG(148)；位置：T041-R09-C08
- 批注 142：FhG(148)；位置：P043
- 批注 146：DLB(121)；位置：P060, T050-R01-C01
- 批注 340：FhG(120)；位置：P082, T081-R01-C01
- 批注 420：Lenovo/Mot(162)；位置：T084-R01-C01, T084-R05-C06
- 批注 511：DLB(122)；位置：P102
- 批注 514：DLB(122)；位置：T105-R02-C06
- 批注 516：DLB(122)；位置：T105-R04-C06

**原文页眉：** 3GPP TSG- SA4 Meeting # 137-e    S4aA260180<br>    24<sup>th</sup> - 28<sup>th</sup> August 2026, Online    Revision of S4-261771
