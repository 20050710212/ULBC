# S4aA260167 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260167-Permanent Document ULBC-8a - Test Plan for Selection - v.0.1.0.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    ULBC-8a Editor

<a id="P001"></a>

Title:    Permanent Document ULBC-8a - Test Plan for Selection

<a id="P002"></a>

Version:    v.0.1.0

<a id="P003"></a>

Agenda Item:    4.8

<a id="P005"></a>

Document History:

<a id="T007"></a>

<a id="T007-R01"></a>
**T007-R01**

- <a id="T007-R01-C01"></a>列 1: v.0.0.1
- <a id="T007-R01-C02"></a>列 2: 28 September 2026
- <a id="T007-R01-C03"></a>列 3: Skeleton; Table of Permanent documents as agreed in S4-261425

<a id="T007-R02"></a>
**T007-R02**

- <a id="T007-R02-C01"></a>列 1: V0.1.0
- <a id="T007-R02-C02"></a>列 2: 30 September 2026
- <a id="T007-R02-C03"></a>列 3: Replacing Qualification with Selection to reflect the working agreement, insertion preliminary list of requested test languages, integration of agreed proposals from S4aA260166

<a id="T007-R03"></a>
**T007-R03**

- <a id="T007-R03-C01"></a>列 1: 
- <a id="T007-R03-C02"></a>列 2: 
- <a id="T007-R03-C03"></a>列 3: 

<a id="T007-R04"></a>
**T007-R04**

- <a id="T007-R04-C01"></a>列 1: 
- <a id="T007-R04-C02"></a>列 2: 
- <a id="T007-R04-C03"></a>列 3: 

<a id="P008"></a>

Introduction

<a id="P009"></a>

This document contains the Test Plan for the Selection Phase of the ULBC Codec.

<a id="P011"></a>

References and Conventions

<a id="P012"></a>

Permanent Documents

<a id="P013"></a>

The following documents provide additional information on the ULBC codec development project.

<a id="T014"></a>

<a id="T014-R01"></a>
**T014-R01**

- <a id="T014-R01-C01"></a>列 1: P-doc
- <a id="T014-R01-C02"></a>列 2: Title

<a id="T014-R02"></a>
**T014-R02**

- <a id="T014-R02-C01"></a>列 1: ULBC-1
- <a id="T014-R02-C02"></a>列 2: Overview

<a id="T014-R03"></a>
**T014-R03**

- <a id="T014-R03-C01"></a>列 1: ULBC-2
- <a id="T014-R03-C02"></a>列 2: Project Plan

<a id="T014-R04"></a>
**T014-R04**

- <a id="T014-R04-C01"></a>列 1: ULBC-3
- <a id="T014-R04-C02"></a>列 2: Performance Requirements

<a id="T014-R05"></a>
**T014-R05**

- <a id="T014-R05-C01"></a>列 1: ULBC-4
- <a id="T014-R05-C02"></a>列 2: Design Constraints

<a id="T014-R06"></a>
**T014-R06**

- <a id="T014-R06-C01"></a>列 1: 
- <a id="T014-R06-C02"></a>列 2: 

<a id="T014-R07"></a>
**T014-R07**

- <a id="T014-R07-C01"></a>列 1: ULBC-5
- <a id="T014-R07-C02"></a>列 2: Selection Rules

<a id="T014-R08"></a>
**T014-R08**

- <a id="T014-R08-C01"></a>列 1: ULBC-6
- <a id="T014-R08-C02"></a>列 2: Deliverables

<a id="T014-R09"></a>
**T014-R09**

- <a id="T014-R09-C01"></a>列 1: ULBC-7
- <a id="T014-R09-C02"></a>列 2: Processing Plan

<a id="T014-R10"></a>
**T014-R10**

- <a id="T014-R10-C01"></a>列 1: 
- <a id="T014-R10-C02"></a>列 2: 

<a id="T014-R11"></a>
**T014-R11**

- <a id="T014-R11-C01"></a>列 1: ULBC-8a
- <a id="T014-R11-C02"></a>列 2: Test Plan for Selection Phase

<a id="T014-R12"></a>
**T014-R12**

- <a id="T014-R12-C01"></a>列 1: ULBC-9
- <a id="T014-R12-C02"></a>列 2: RTP header system integration

<a id="P016"></a>

The latest version of these documents can be found in the following link.

<a id="P017"></a>

https://www.3gpp.org/ftp/tsg_sa/WG4_CODEC/ULBC_Permanent_Documents

<a id="P019"></a>

Reference Documents

<a id="P020"></a>

Recommendation ITU-T P.800 (08/1996): Methods for subjective determination of transmission quality.

<a id="P021"></a>

ITU-T Handbook of subjective testing practical procedures, 2011.

<a id="P022"></a>

Recommendation ITU-T P.191 (03/2023): Software tools for speech and audio coding standardization.

<a id="P023"></a>

Recommendation ITU-R BS.1770-4 (10/2015): Algorithms to measure audio programme loudness and true-peak audio level.

<a id="P024"></a>

Audio File Format Specifications: WAVE, https://www-mmsp.ece.mcgill.ca/Documents/AudioFormats/WAVE/WAVE.html

<a id="P026"></a>

Key Acronyms

<a id="P027"></a>

CL        Cross-check Laboratory

<a id="P028"></a>

CuT        Codec under Test

<a id="P029"></a>

DCR        Degradation Category Rating

<a id="P030"></a>

DTX        Discontinuous transmission

<a id="P031"></a>

EVS        Enhanced Voice Services

<a id="P032"></a>

FE        Frame Erasure

<a id="P033"></a>

FER        Frame Error Rate

<a id="P034"></a>

GAL        Global Analysis Laboratory

<a id="P035"></a>

HL        Host Laboratory

<a id="P036"></a>

LKFS        Loudness, K-weighted, relative to Full Scale

<a id="P037"></a>

LL        Listening Laboratory

<a id="P038"></a>

MNRU        Modulated Noise Reference Unit

<a id="P039"></a>

PC        Proponent Company

<a id="P040"></a>

SNR        Signal-to-Noise Ratio

<a id="P041"></a>

SPL         Sound Pressure Level

<a id="P042"></a>

SWB        Super Wide Band

<a id="P043"></a>

ToR        Terms of Reference

<a id="P044"></a>

WB        Wide Band

<a id="P047"></a>

Roles and Responsibilities

<a id="P048"></a>

Overview of the Selection Test Process

<a id="P049"></a>

The execution of the ULBC Selection subjective testing is under the responsibility of the LLs participating in the Selection Phase.

<a id="P050"></a>

SA4 shall select the LLs to perform the subjective listening tests described in this document. [ETSI will contract the external laboratories.] SA4 shall select the languages used in each experiment conducted by each LL. SA4 shall further select the HL, the CL, and the GAL to perform respective tasks defined in this document, and ETSI will contract the GAL.

<a id="P051"></a>

The LLs shall provide unprocessed [48 kHz] sampled clean speech [and background material]. [The format of the material is WAVE [5], 16-bit little endian format.]

<a id="P052"></a>

The PCs are responsible for delivery of the ULBC executables to HL and CL.

<a id="P053"></a>

The LLs shall insert the raw voting data into the workbook provided by the GAL and forward the workbook directly to the GAL. In addition, each LL must provide a report of experiments to SA4 no later than the document submission deadline for the Selection meeting.

<a id="P055"></a>

Allocation of Additional Roles

<a id="P056"></a>

External LLs: [Mesaqin.com, FORCE Technology]

<a id="P057"></a>

HL:

<a id="P058"></a>

CL:

<a id="P059"></a>

GAL:

<a id="P061"></a>

Responsibilities

<a id="P062"></a>

Many of the procedures to be followed are defined in this test plan, with further information being given in ULBC Processing Plan for Selection Phase (ULBC-7). The tasks have to be conducted and completed following the schedule for the ULBC Selection Phase defined in ULBC-2.

<a id="P063"></a>

Proponent Companies

<a id="P065"></a>

Listening Laboratories

<a id="P067"></a>

Host Laboratory

<a id="P069"></a>

Cross-check Laboratory

<a id="P071"></a>

Global Analysis Laboratory

<a id="P072"></a>

Tasks

<a id="P074"></a>

Statistical analysis of results

<a id="P076"></a>

SA4

<a id="P078"></a>

Information relevant to all Experiments

<a id="P079"></a>

General Technical Notes

<a id="P080"></a>

Any and all deviations from the specifications contained in this document and the ULBC Processing Plan for Characterization Phase (ULBC-7) must be documented and submitted to SA4 along with the experimental report.

<a id="P081"></a>

Methodology

<a id="P082"></a>

The P.800 DCR test methodology [1] shall be used in the ULBC Selection test. High-level configuration of experiments for envisaged methodologies is outlined below.

<a id="P083"></a>

Test duration should not exceed 2 hours per listening panel. The typical value of voting period was used for estimation of test durations, but actual voting period is not specified.

<a id="P084"></a>

Randomizations constructed under partially-balanced/randomized blocks experimental design described in [2].

<a id="P085"></a>

Each speech experiment is performed twice and is tested in two different LLs in two different languages with native listeners.

<a id="P086"></a>

P.800 experiments are performed with native listeners of the tested language.

<a id="P087"></a>

[2X categories (talkers) - X male talkers, X female talkers.

<a id="P088"></a>

Y listening panels.

<a id="P089"></a>

Y+1 samples/talker (1 sample/talker for each of Y listening panels plus 1 sample/talker for preliminaries).

<a id="P090"></a>

Z listeners/panel.

<a id="P091"></a>

Total number of listeners: Y panels x Z listeners/panel, each panel with an independent randomization.

<a id="P092"></a>

Total number of votes per condition:2X talkers x Y panels x Z listeners/panel.

<a id="P093"></a>

Number of conditions for each experiment: W.

<a id="P094"></a>

Number of trials: W test conditions x 2X talkers.]

<a id="P095"></a>

Initially the experimenter should provide a written copy of the experiment instructions to the listeners. When the listeners have acknowledged that they understand the instructions, they will be presented with a practice session to rate the preliminary conditions. After the practice session has been completed, the experimenter should ask if there are any questions. Only questions about the rating procedures or the meaning of the instructions should be answered. Any technical questions on matters such as the experimental methodology or details of the types of distortions they are rating must not be answered.

<a id="P096"></a>

Opinion Scales

<a id="P097"></a>

Table 1 defines opinion scale used for ITU-T P.800 DCR test. Instructions in English for the P.800 tests are provided in Annex A:.

<a id="P099"></a>

Table 1: Opinion scale for ITU-T P.800 DCR test

<a id="T100"></a>

<a id="T100-R01"></a>
**T100-R01**

- <a id="T100-R01-C01"></a>列 1: Degradation
- <a id="T100-R01-C02"></a>列 2: Scale

<a id="T100-R02"></a>
**T100-R02**

- <a id="T100-R02-C01"></a>列 1: Degradation is inaudible
- <a id="T100-R02-C02"></a>列 2: 5

<a id="T100-R03"></a>
**T100-R03**

- <a id="T100-R03-C01"></a>列 1: Degradation is audible but not annoying
- <a id="T100-R03-C02"></a>列 2: 4

<a id="T100-R04"></a>
**T100-R04**

- <a id="T100-R04-C01"></a>列 1: Degradation is slightly annoying
- <a id="T100-R04-C02"></a>列 2: 3

<a id="T100-R05"></a>
**T100-R05**

- <a id="T100-R05-C01"></a>列 1: Degradation is annoying
- <a id="T100-R05-C02"></a>列 2: 2

<a id="T100-R06"></a>
**T100-R06**

- <a id="T100-R06-C01"></a>列 1: Degradation is very annoying
- <a id="T100-R06-C02"></a>列 2: 1

<a id="P102"></a>

Material

<a id="P103"></a>

The speech material is to be delivered to the HL as [16-bit little endian WAVE format files, sampled at 48 kHz], following the naming convention provided in the Processing Plan (ULBC-7).

<a id="P104"></a>

Speech Material

<a id="P105"></a>

The format of the speech samples shall follow the definition in clause 5.1.1.1 and 5.1.1.2 of [2], and the duration of each sample shall last exactly 8 seconds. Figure 1 depicts the structure for a sentence-pair.

<a id="P108"></a>

Figure 1: Structure of sentence-pair

<a id="P110"></a>

In constructing the speech sample, the silence period between the sentences should be at least 0.5 sec. The leading and trailing silence periods should also be at least 0.5 sec. For the speech samples, “silence” is the recording noise. [The amount of material to be provided by each LL is at least Y+1 speech samples for each of three X male and X female talkers. This results in (Y+1) x X files in total.] Recording noise level shall be compliant with the ITU-T P.800.

<a id="P111"></a>

Background Noise Material

<a id="P114"></a>

Listening Systems and Listening Environments

<a id="P116"></a>

Subjective Experiments

<a id="P117"></a>

General Consideration of Experiments

<a id="P118"></a>

The main goal of the ULBC Selection Test is ...

<a id="P119"></a>

All codec candidates are evaluated in the same test.

<a id="P120"></a>

Each operation point is evaluated in a separate test if the number of candidates is larger or equal to X.

<a id="P121"></a>

Note: X might be 13 (TBC).

<a id="P122"></a>

P.800 DCR test methodology [1] will be used for the ULBC Selection testing campaign, run by non-candidate laboratories.

<a id="P124"></a>

P.800 DCR listening test layout

<a id="P125"></a>

The following layout is a generic layout. The actual layouts of P.800 DCR experiments may be slightly different. They are described in Annex E:.

<a id="P126"></a>

[

<a id="P127"></a>

Table 2: P.800 DCR test layout

<a id="T128"></a>

<a id="T128-R01"></a>
**T128-R01**

- <a id="T128-R01-C01"></a>列 1: Label
- <a id="T128-R01-C02"></a>列 2: Condition
- <a id="T128-R01-C03"></a>列 3: Bitrate [kbps]
- <a id="T128-R01-C04"></a>列 4: DTX
- <a id="T128-R01-C05"></a>列 5: Input Level
- <a id="T128-R01-C06"></a>列 6: FER/Profile

<a id="T128-R02"></a>
**T128-R02**

- <a id="T128-R02-C01"></a>列 1: c01
- <a id="T128-R02-C02"></a>列 2: Reference
- <a id="T128-R02-C03"></a>列 3: -
- <a id="T128-R02-C04"></a>列 4: -
- <a id="T128-R02-C05"></a>列 5: -
- <a id="T128-R02-C06"></a>列 6: -

<a id="T128-R03"></a>
**T128-R03**

- <a id="T128-R03-C01"></a>列 1: c02
- <a id="T128-R03-C02"></a>列 2: MNRU Q = xx dB
- <a id="T128-R03-C03"></a>列 3: -
- <a id="T128-R03-C04"></a>列 4: -
- <a id="T128-R03-C05"></a>列 5: -
- <a id="T128-R03-C06"></a>列 6: -

<a id="T128-R04"></a>
**T128-R04**

- <a id="T128-R04-C01"></a>列 1: c03
- <a id="T128-R04-C02"></a>列 2: MNRU Q = xx dB
- <a id="T128-R04-C03"></a>列 3: -
- <a id="T128-R04-C04"></a>列 4: -
- <a id="T128-R04-C05"></a>列 5: -
- <a id="T128-R04-C06"></a>列 6: -

<a id="T128-R05"></a>
**T128-R05**

- <a id="T128-R05-C01"></a>列 1: c04
- <a id="T128-R05-C02"></a>列 2: MNRU Q = xx dB
- <a id="T128-R05-C03"></a>列 3: -
- <a id="T128-R05-C04"></a>列 4: -
- <a id="T128-R05-C05"></a>列 5: -
- <a id="T128-R05-C06"></a>列 6: -

<a id="T128-R06"></a>
**T128-R06**

- <a id="T128-R06-C01"></a>列 1: c05
- <a id="T128-R06-C02"></a>列 2: MNRU Q = xx dB
- <a id="T128-R06-C03"></a>列 3: -
- <a id="T128-R06-C04"></a>列 4: -
- <a id="T128-R06-C05"></a>列 5: -
- <a id="T128-R06-C06"></a>列 6: -

<a id="T128-R07"></a>
**T128-R07**

- <a id="T128-R07-C01"></a>列 1: c06
- <a id="T128-R07-C02"></a>列 2: MNRU Q = xx dB
- <a id="T128-R07-C03"></a>列 3: -
- <a id="T128-R07-C04"></a>列 4: -
- <a id="T128-R07-C05"></a>列 5: -
- <a id="T128-R07-C06"></a>列 6: -

<a id="T128-R08"></a>
**T128-R08**

- <a id="T128-R08-C01"></a>列 1: c07
- <a id="T128-R08-C02"></a>列 2: 
- <a id="T128-R08-C03"></a>列 3: 
- <a id="T128-R08-C04"></a>列 4: 
- <a id="T128-R08-C05"></a>列 5: 
- <a id="T128-R08-C06"></a>列 6: 

<a id="T128-R09"></a>
**T128-R09**

- <a id="T128-R09-C01"></a>列 1: c08
- <a id="T128-R09-C02"></a>列 2: 
- <a id="T128-R09-C03"></a>列 3: 
- <a id="T128-R09-C04"></a>列 4: 
- <a id="T128-R09-C05"></a>列 5: 
- <a id="T128-R09-C06"></a>列 6: 

<a id="T128-R10"></a>
**T128-R10**

- <a id="T128-R10-C01"></a>列 1: C09
- <a id="T128-R10-C02"></a>列 2: 
- <a id="T128-R10-C03"></a>列 3: 
- <a id="T128-R10-C04"></a>列 4: 
- <a id="T128-R10-C05"></a>列 5: 
- <a id="T128-R10-C06"></a>列 6: 

<a id="T128-R11"></a>
**T128-R11**

- <a id="T128-R11-C01"></a>列 1: c10
- <a id="T128-R11-C02"></a>列 2: 
- <a id="T128-R11-C03"></a>列 3: 
- <a id="T128-R11-C04"></a>列 4: 
- <a id="T128-R11-C05"></a>列 5: 
- <a id="T128-R11-C06"></a>列 6: 

<a id="T128-R12"></a>
**T128-R12**

- <a id="T128-R12-C01"></a>列 1: c11
- <a id="T128-R12-C02"></a>列 2: 
- <a id="T128-R12-C03"></a>列 3: 
- <a id="T128-R12-C04"></a>列 4: 
- <a id="T128-R12-C05"></a>列 5: 
- <a id="T128-R12-C06"></a>列 6: 

<a id="T128-R13"></a>
**T128-R13**

- <a id="T128-R13-C01"></a>列 1: c12
- <a id="T128-R13-C02"></a>列 2: 
- <a id="T128-R13-C03"></a>列 3: 
- <a id="T128-R13-C04"></a>列 4: 
- <a id="T128-R13-C05"></a>列 5: 
- <a id="T128-R13-C06"></a>列 6: 

<a id="T128-R14"></a>
**T128-R14**

- <a id="T128-R14-C01"></a>列 1: c13
- <a id="T128-R14-C02"></a>列 2: 
- <a id="T128-R14-C03"></a>列 3: 
- <a id="T128-R14-C04"></a>列 4: 
- <a id="T128-R14-C05"></a>列 5: 
- <a id="T128-R14-C06"></a>列 6: 

<a id="T128-R15"></a>
**T128-R15**

- <a id="T128-R15-C01"></a>列 1: c14
- <a id="T128-R15-C02"></a>列 2: 
- <a id="T128-R15-C03"></a>列 3: 
- <a id="T128-R15-C04"></a>列 4: 
- <a id="T128-R15-C05"></a>列 5: 
- <a id="T128-R15-C06"></a>列 6: 

<a id="T128-R16"></a>
**T128-R16**

- <a id="T128-R16-C01"></a>列 1: c15
- <a id="T128-R16-C02"></a>列 2: 
- <a id="T128-R16-C03"></a>列 3: 
- <a id="T128-R16-C04"></a>列 4: 
- <a id="T128-R16-C05"></a>列 5: 
- <a id="T128-R16-C06"></a>列 6: 

<a id="T128-R17"></a>
**T128-R17**

- <a id="T128-R17-C01"></a>列 1: c16
- <a id="T128-R17-C02"></a>列 2: 
- <a id="T128-R17-C03"></a>列 3: 
- <a id="T128-R17-C04"></a>列 4: 
- <a id="T128-R17-C05"></a>列 5: 
- <a id="T128-R17-C06"></a>列 6: 

<a id="T128-R18"></a>
**T128-R18**

- <a id="T128-R18-C01"></a>列 1: c17
- <a id="T128-R18-C02"></a>列 2: 
- <a id="T128-R18-C03"></a>列 3: 
- <a id="T128-R18-C04"></a>列 4: 
- <a id="T128-R18-C05"></a>列 5: 
- <a id="T128-R18-C06"></a>列 6: 

<a id="T128-R19"></a>
**T128-R19**

- <a id="T128-R19-C01"></a>列 1: c18
- <a id="T128-R19-C02"></a>列 2: 
- <a id="T128-R19-C03"></a>列 3: 
- <a id="T128-R19-C04"></a>列 4: 
- <a id="T128-R19-C05"></a>列 5: 
- <a id="T128-R19-C06"></a>列 6: 

<a id="T128-R20"></a>
**T128-R20**

- <a id="T128-R20-C01"></a>列 1: c19
- <a id="T128-R20-C02"></a>列 2: 
- <a id="T128-R20-C03"></a>列 3: 
- <a id="T128-R20-C04"></a>列 4: 
- <a id="T128-R20-C05"></a>列 5: 
- <a id="T128-R20-C06"></a>列 6: 

<a id="T128-R21"></a>
**T128-R21**

- <a id="T128-R21-C01"></a>列 1: c20
- <a id="T128-R21-C02"></a>列 2: 
- <a id="T128-R21-C03"></a>列 3: 
- <a id="T128-R21-C04"></a>列 4: 
- <a id="T128-R21-C05"></a>列 5: 
- <a id="T128-R21-C06"></a>列 6: 

<a id="T128-R22"></a>
**T128-R22**

- <a id="T128-R22-C01"></a>列 1: c21
- <a id="T128-R22-C02"></a>列 2: 
- <a id="T128-R22-C03"></a>列 3: 
- <a id="T128-R22-C04"></a>列 4: 
- <a id="T128-R22-C05"></a>列 5: 
- <a id="T128-R22-C06"></a>列 6: 

<a id="T128-R23"></a>
**T128-R23**

- <a id="T128-R23-C01"></a>列 1: c22
- <a id="T128-R23-C02"></a>列 2: 
- <a id="T128-R23-C03"></a>列 3: 
- <a id="T128-R23-C04"></a>列 4: 
- <a id="T128-R23-C05"></a>列 5: 
- <a id="T128-R23-C06"></a>列 6: 

<a id="T128-R24"></a>
**T128-R24**

- <a id="T128-R24-C01"></a>列 1: c23
- <a id="T128-R24-C02"></a>列 2: 
- <a id="T128-R24-C03"></a>列 3: 
- <a id="T128-R24-C04"></a>列 4: 
- <a id="T128-R24-C05"></a>列 5: 
- <a id="T128-R24-C06"></a>列 6: 

<a id="T128-R25"></a>
**T128-R25**

- <a id="T128-R25-C01"></a>列 1: c24
- <a id="T128-R25-C02"></a>列 2: 
- <a id="T128-R25-C03"></a>列 3: 
- <a id="T128-R25-C04"></a>列 4: 
- <a id="T128-R25-C05"></a>列 5: 
- <a id="T128-R25-C06"></a>列 6: 

<a id="T128-R26"></a>
**T128-R26**

- <a id="T128-R26-C01"></a>列 1: c25
- <a id="T128-R26-C02"></a>列 2: 
- <a id="T128-R26-C03"></a>列 3: 
- <a id="T128-R26-C04"></a>列 4: 
- <a id="T128-R26-C05"></a>列 5: 
- <a id="T128-R26-C06"></a>列 6: 

<a id="T128-R27"></a>
**T128-R27**

- <a id="T128-R27-C01"></a>列 1: c26
- <a id="T128-R27-C02"></a>列 2: 
- <a id="T128-R27-C03"></a>列 3: 
- <a id="T128-R27-C04"></a>列 4: 
- <a id="T128-R27-C05"></a>列 5: 
- <a id="T128-R27-C06"></a>列 6: 

<a id="T128-R28"></a>
**T128-R28**

- <a id="T128-R28-C01"></a>列 1: c27
- <a id="T128-R28-C02"></a>列 2: 
- <a id="T128-R28-C03"></a>列 3: 
- <a id="T128-R28-C04"></a>列 4: 
- <a id="T128-R28-C05"></a>列 5: 
- <a id="T128-R28-C06"></a>列 6: 

<a id="T128-R29"></a>
**T128-R29**

- <a id="T128-R29-C01"></a>列 1: c28
- <a id="T128-R29-C02"></a>列 2: 
- <a id="T128-R29-C03"></a>列 3: 
- <a id="T128-R29-C04"></a>列 4: 
- <a id="T128-R29-C05"></a>列 5: 
- <a id="T128-R29-C06"></a>列 6: 

<a id="T128-R30"></a>
**T128-R30**

- <a id="T128-R30-C01"></a>列 1: c29
- <a id="T128-R30-C02"></a>列 2: 
- <a id="T128-R30-C03"></a>列 3: 
- <a id="T128-R30-C04"></a>列 4: 
- <a id="T128-R30-C05"></a>列 5: 
- <a id="T128-R30-C06"></a>列 6: 

<a id="T128-R31"></a>
**T128-R31**

- <a id="T128-R31-C01"></a>列 1: c30
- <a id="T128-R31-C02"></a>列 2: 
- <a id="T128-R31-C03"></a>列 3: 
- <a id="T128-R31-C04"></a>列 4: 
- <a id="T128-R31-C05"></a>列 5: 
- <a id="T128-R31-C06"></a>列 6: 

<a id="T128-R32"></a>
**T128-R32**

- <a id="T128-R32-C01"></a>列 1: c31
- <a id="T128-R32-C02"></a>列 2: 
- <a id="T128-R32-C03"></a>列 3: 
- <a id="T128-R32-C04"></a>列 4: 
- <a id="T128-R32-C05"></a>列 5: 
- <a id="T128-R32-C06"></a>列 6: 

<a id="T128-R33"></a>
**T128-R33**

- <a id="T128-R33-C01"></a>列 1: c32
- <a id="T128-R33-C02"></a>列 2: 
- <a id="T128-R33-C03"></a>列 3: 
- <a id="T128-R33-C04"></a>列 4: 
- <a id="T128-R33-C05"></a>列 5: 
- <a id="T128-R33-C06"></a>列 6: 

<a id="T128-R34"></a>
**T128-R34**

- <a id="T128-R34-C01"></a>列 1: c33
- <a id="T128-R34-C02"></a>列 2: 
- <a id="T128-R34-C03"></a>列 3: 
- <a id="T128-R34-C04"></a>列 4: 
- <a id="T128-R34-C05"></a>列 5: 
- <a id="T128-R34-C06"></a>列 6: 

<a id="T128-R35"></a>
**T128-R35**

- <a id="T128-R35-C01"></a>列 1: c34
- <a id="T128-R35-C02"></a>列 2: 
- <a id="T128-R35-C03"></a>列 3: 
- <a id="T128-R35-C04"></a>列 4: 
- <a id="T128-R35-C05"></a>列 5: 
- <a id="T128-R35-C06"></a>列 6: 

<a id="T128-R36"></a>
**T128-R36**

- <a id="T128-R36-C01"></a>列 1: c35
- <a id="T128-R36-C02"></a>列 2: 
- <a id="T128-R36-C03"></a>列 3: 
- <a id="T128-R36-C04"></a>列 4: 
- <a id="T128-R36-C05"></a>列 5: 
- <a id="T128-R36-C06"></a>列 6: 

<a id="T128-R37"></a>
**T128-R37**

- <a id="T128-R37-C01"></a>列 1: c36
- <a id="T128-R37-C02"></a>列 2: 
- <a id="T128-R37-C03"></a>列 3: 
- <a id="T128-R37-C04"></a>列 4: 
- <a id="T128-R37-C05"></a>列 5: 
- <a id="T128-R37-C06"></a>列 6: 

<a id="P129"></a>

]

<a id="P131"></a>

Allocation of experiments and test languages

<a id="P132"></a>

The following table shows high-level overview of the experiments with allocation of experiments to LLs with languages used for each experiment. Detail conditions for each subjective experiment are defined in Annex E:.

<a id="P133"></a>

The pricing for external LLs and GAL is as

<a id="P134"></a>

[18000] Euros for LLs per P.800 DCR test

<a id="P135"></a>

[1000] Euros per talker for recording new speech samples

<a id="P136"></a>

[14000] Euros for GAL tasks.

<a id="P138"></a>

List of Test languages:

<a id="P139"></a>

UK and US English

<a id="P140"></a>

Mandarin

<a id="P141"></a>

Spanish

<a id="P142"></a>

French

<a id="P143"></a>

Hindi

<a id="P144"></a>

Arabic

<a id="P145"></a>

[German]

<a id="P146"></a>

[A Slavic language]

<a id="P147"></a>

[Japanese]

<a id="P148"></a>

[Danish]

<a id="P149"></a>

[Swedish]

<a id="P151"></a>

[Table 3: Allocation of P.800 DCR experiments to LLs and corresponding languages

<a id="T152"></a>

<a id="T152-R01"></a>
**T152-R01**

- <a id="T152-R01-C01"></a>列 1: Exp
- <a id="T152-R01-C02"></a>列 2: LL-1
- <a id="T152-R01-C03"></a>列 3: Language-1
- <a id="T152-R01-C04"></a>列 4: LL-2
- <a id="T152-R01-C05"></a>列 5: Language-2

<a id="T152-R02"></a>
**T152-R02**

- <a id="T152-R02-C01"></a>列 1: DCR-1
- <a id="T152-R02-C02"></a>列 2: 
- <a id="T152-R02-C03"></a>列 3: 
- <a id="T152-R02-C04"></a>列 4: 
- <a id="T152-R02-C05"></a>列 5: 

<a id="T152-R03"></a>
**T152-R03**

- <a id="T152-R03-C01"></a>列 1: DCR-2
- <a id="T152-R03-C02"></a>列 2: 
- <a id="T152-R03-C03"></a>列 3: 
- <a id="T152-R03-C04"></a>列 4: 
- <a id="T152-R03-C05"></a>列 5: 

<a id="T152-R04"></a>
**T152-R04**

- <a id="T152-R04-C01"></a>列 1: DCR-3
- <a id="T152-R04-C02"></a>列 2: 
- <a id="T152-R04-C03"></a>列 3: 
- <a id="T152-R04-C04"></a>列 4: 
- <a id="T152-R04-C05"></a>列 5: 

<a id="T152-R05"></a>
**T152-R05**

- <a id="T152-R05-C01"></a>列 1: DCR-4
- <a id="T152-R05-C02"></a>列 2: 
- <a id="T152-R05-C03"></a>列 3: 
- <a id="T152-R05-C04"></a>列 4: 
- <a id="T152-R05-C05"></a>列 5: 

<a id="T152-R06"></a>
**T152-R06**

- <a id="T152-R06-C01"></a>列 1: DCR-5
- <a id="T152-R06-C02"></a>列 2: 
- <a id="T152-R06-C03"></a>列 3: 
- <a id="T152-R06-C04"></a>列 4: 
- <a id="T152-R06-C05"></a>列 5: 

<a id="T152-R07"></a>
**T152-R07**

- <a id="T152-R07-C01"></a>列 1: DCR-6
- <a id="T152-R07-C02"></a>列 2: 
- <a id="T152-R07-C03"></a>列 3: 
- <a id="T152-R07-C04"></a>列 4: 
- <a id="T152-R07-C05"></a>列 5: 

<a id="T152-R08"></a>
**T152-R08**

- <a id="T152-R08-C01"></a>列 1: DCR-7
- <a id="T152-R08-C02"></a>列 2: 
- <a id="T152-R08-C03"></a>列 3: 
- <a id="T152-R08-C04"></a>列 4: 
- <a id="T152-R08-C05"></a>列 5: 

<a id="T152-R09"></a>
**T152-R09**

- <a id="T152-R09-C01"></a>列 1: DCR-8
- <a id="T152-R09-C02"></a>列 2: 
- <a id="T152-R09-C03"></a>列 3: 
- <a id="T152-R09-C04"></a>列 4: 
- <a id="T152-R09-C05"></a>列 5: 

<a id="T152-R10"></a>
**T152-R10**

- <a id="T152-R10-C01"></a>列 1: DCR-9
- <a id="T152-R10-C02"></a>列 2: 
- <a id="T152-R10-C03"></a>列 3: 
- <a id="T152-R10-C04"></a>列 4: 
- <a id="T152-R10-C05"></a>列 5: 

<a id="T152-R11"></a>
**T152-R11**

- <a id="T152-R11-C01"></a>列 1: DCR-10
- <a id="T152-R11-C02"></a>列 2: 
- <a id="T152-R11-C03"></a>列 3: 
- <a id="T152-R11-C04"></a>列 4: 
- <a id="T152-R11-C05"></a>列 5: 

<a id="T152-R12"></a>
**T152-R12**

- <a id="T152-R12-C01"></a>列 1: DCR-11
- <a id="T152-R12-C02"></a>列 2: 
- <a id="T152-R12-C03"></a>列 3: 
- <a id="T152-R12-C04"></a>列 4: 
- <a id="T152-R12-C05"></a>列 5: 

<a id="T152-R13"></a>
**T152-R13**

- <a id="T152-R13-C01"></a>列 1: DCR-12
- <a id="T152-R13-C02"></a>列 2: 
- <a id="T152-R13-C03"></a>列 3: 
- <a id="T152-R13-C04"></a>列 4: 
- <a id="T152-R13-C05"></a>列 5: 

<a id="T152-R14"></a>
**T152-R14**

- <a id="T152-R14-C01"></a>列 1: DCR-13
- <a id="T152-R14-C02"></a>列 2: 
- <a id="T152-R14-C03"></a>列 3: 
- <a id="T152-R14-C04"></a>列 4: 
- <a id="T152-R14-C05"></a>列 5: 

<a id="T152-R15"></a>
**T152-R15**

- <a id="T152-R15-C01"></a>列 1: DCR-14
- <a id="T152-R15-C02"></a>列 2: 
- <a id="T152-R15-C03"></a>列 3: 
- <a id="T152-R15-C04"></a>列 4: 
- <a id="T152-R15-C05"></a>列 5: 

<a id="T152-R16"></a>
**T152-R16**

- <a id="T152-R16-C01"></a>列 1: DCR-15
- <a id="T152-R16-C02"></a>列 2: 
- <a id="T152-R16-C03"></a>列 3: 
- <a id="T152-R16-C04"></a>列 4: 
- <a id="T152-R16-C05"></a>列 5: 

<a id="T152-R17"></a>
**T152-R17**

- <a id="T152-R17-C01"></a>列 1: DCR-16
- <a id="T152-R17-C02"></a>列 2: 
- <a id="T152-R17-C03"></a>列 3: 
- <a id="T152-R17-C04"></a>列 4: 
- <a id="T152-R17-C05"></a>列 5: 

<a id="T152-R18"></a>
**T152-R18**

- <a id="T152-R18-C01"></a>列 1: DCR-17
- <a id="T152-R18-C02"></a>列 2: 
- <a id="T152-R18-C03"></a>列 3: 
- <a id="T152-R18-C04"></a>列 4: 
- <a id="T152-R18-C05"></a>列 5: 

<a id="T152-R19"></a>
**T152-R19**

- <a id="T152-R19-C01"></a>列 1: DCR-18
- <a id="T152-R19-C02"></a>列 2: 
- <a id="T152-R19-C03"></a>列 3: 
- <a id="T152-R19-C04"></a>列 4: 
- <a id="T152-R19-C05"></a>列 5: 

<a id="T152-R20"></a>
**T152-R20**

- <a id="T152-R20-C01"></a>列 1: DCR-19
- <a id="T152-R20-C02"></a>列 2: 
- <a id="T152-R20-C03"></a>列 3: 
- <a id="T152-R20-C04"></a>列 4: 
- <a id="T152-R20-C05"></a>列 5: 

<a id="T152-R21"></a>
**T152-R21**

- <a id="T152-R21-C01"></a>列 1: DCR-20
- <a id="T152-R21-C02"></a>列 2: 
- <a id="T152-R21-C03"></a>列 3: 
- <a id="T152-R21-C04"></a>列 4: 
- <a id="T152-R21-C05"></a>列 5: 

<a id="T152-R22"></a>
**T152-R22**

- <a id="T152-R22-C01"></a>列 1: DCR-21
- <a id="T152-R22-C02"></a>列 2: 
- <a id="T152-R22-C03"></a>列 3: 
- <a id="T152-R22-C04"></a>列 4: 
- <a id="T152-R22-C05"></a>列 5: 

<a id="T152-R23"></a>
**T152-R23**

- <a id="T152-R23-C01"></a>列 1: DCR-22
- <a id="T152-R23-C02"></a>列 2: 
- <a id="T152-R23-C03"></a>列 3: 
- <a id="T152-R23-C04"></a>列 4: 
- <a id="T152-R23-C05"></a>列 5: 

<a id="T152-R24"></a>
**T152-R24**

- <a id="T152-R24-C01"></a>列 1: DCR-23
- <a id="T152-R24-C02"></a>列 2: 
- <a id="T152-R24-C03"></a>列 3: 
- <a id="T152-R24-C04"></a>列 4: 
- <a id="T152-R24-C05"></a>列 5: 

<a id="P153"></a>

]

<a id="P162"></a>

Sample Instructions to Subjects

<a id="P163"></a>

These instructions shall be translated properly to the LL’s language and be given to the listeners. The instructions given to the listeners shall be provided for information in the LL report.

<a id="T164"></a>

<a id="T164-R01"></a>
**T164-R01**

- <a id="T164-R01-C01"></a>列 1: SAMPLE INSTRUCTIONS TO SUBJECTS FOR THE DCR<br><br>In this experiment we are evaluating systems that might be used for telecommunication services.<br>The experiment involves a number of trials and each trial includes two samples -- where each sample is [two sentences] [an audio sample]. The first sample in each trial will be the reference sample. The second sample in each trial will be same sample after it has been passed through a telecommunications system.<br>You should listen carefully to both samples within a trial. When they have finished, please record your opinion of any degradation you can perceive in the second sample relative to the first sample using the following rating scale :<br>5  Degradation is inaudible<br>4  Degradation is audible but not annoying<br>3  Degradation is slightly annoying<br>2  Degradation is annoying<br>1  Degradation is very annoying<br><br>Please remember that your task is to judge the amount of degradation in the second “test” sample relative to the first “reference” sample. After listening to the two samples, please indicate your appropriate response.<br>Please do not discuss your opinions with other listeners participating in the experiment.

<a id="P166"></a>

P.800 DCR Presentation Orders

<a id="P167"></a>

[

<a id="P168"></a>

The PC will provide the Presentation Order for each P.800 DCR experiment to the Listening Lab assigned to conduct the test. The presentation order for each experiment has been developed by the PC using a randomized-blocks experimental design and sample allocation for conducting Independent Groups Student T-tests for the specified References. Each Presentation Order includes 2X blocks, corresponding to 2X categories and includes a separate presentation sequence for each of Y panels of subjects. The Presentation Orders will be delivered to the Listening Labs in the form of Data Delivery Excel spreadsheets which are attached to this document. Presentation Orders will be cross-checked before the actual listening tests start.

<a id="P169"></a>

]

<a id="P171"></a>

Data to be Provided by LL

<a id="P172"></a>

[

<a id="P173"></a>

The GAL will provide a Data Delivery spreadsheet for each experiment to the Listening Lab assigned to conduct the test. For each trial, the table shows both the Reference file (condition c01) and the Test file (conditions c01-c36) followed by 5 data cells, one per subject, to be filled by the Listening Lab with the raw voting data provided by the subjects. The file naming convention is as follows:

<a id="P174"></a>

leeeayszz.cnn.wav l = Listening Lab, eee = Experiment, ay = Category, szz = Sample, cnn = Condition (see ULBC-7)

<a id="P175"></a>

]

<a id="P176"></a>

Selection Testing Timeline

<a id="P177"></a>

Table D.1: Testing Timeline

<a id="T178"></a>

<a id="T178-R01"></a>
**T178-R01**

- <a id="T178-R01-C01"></a>列 1: Date
- <a id="T178-R01-C02"></a>列 2: Task
- <a id="T178-R01-C03"></a>列 3: Active Parties

<a id="T178-R02"></a>
**T178-R02**

- <a id="T178-R02-C01"></a>列 1: 
- <a id="T178-R02-C02"></a>列 2: 
- <a id="T178-R02-C03"></a>列 3: 

<a id="T178-R03"></a>
**T178-R03**

- <a id="T178-R03-C01"></a>列 1: 
- <a id="T178-R03-C02"></a>列 2: 
- <a id="T178-R03-C03"></a>列 3: 

<a id="T178-R04"></a>
**T178-R04**

- <a id="T178-R04-C01"></a>列 1: 
- <a id="T178-R04-C02"></a>列 2: 
- <a id="T178-R04-C03"></a>列 3: 

<a id="T178-R05"></a>
**T178-R05**

- <a id="T178-R05-C01"></a>列 1: 
- <a id="T178-R05-C02"></a>列 2: 
- <a id="T178-R05-C03"></a>列 3: 

<a id="T178-R06"></a>
**T178-R06**

- <a id="T178-R06-C01"></a>列 1: 
- <a id="T178-R06-C02"></a>列 2: 
- <a id="T178-R06-C03"></a>列 3: 

<a id="T178-R07"></a>
**T178-R07**

- <a id="T178-R07-C01"></a>列 1: 
- <a id="T178-R07-C02"></a>列 2: 
- <a id="T178-R07-C03"></a>列 3: 

<a id="T178-R08"></a>
**T178-R08**

- <a id="T178-R08-C01"></a>列 1: 
- <a id="T178-R08-C02"></a>列 2: 
- <a id="T178-R08-C03"></a>列 3: 

<a id="T178-R09"></a>
**T178-R09**

- <a id="T178-R09-C01"></a>列 1: 
- <a id="T178-R09-C02"></a>列 2: 
- <a id="T178-R09-C03"></a>列 3: 

<a id="T178-R10"></a>
**T178-R10**

- <a id="T178-R10-C01"></a>列 1: 
- <a id="T178-R10-C02"></a>列 2: 
- <a id="T178-R10-C03"></a>列 3: 

<a id="T178-R11"></a>
**T178-R11**

- <a id="T178-R11-C01"></a>列 1: 
- <a id="T178-R11-C02"></a>列 2: 
- <a id="T178-R11-C03"></a>列 3: 

<a id="T178-R12"></a>
**T178-R12**

- <a id="T178-R12-C01"></a>列 1: 
- <a id="T178-R12-C02"></a>列 2: 
- <a id="T178-R12-C03"></a>列 3: 

<a id="T178-R13"></a>
**T178-R13**

- <a id="T178-R13-C01"></a>列 1: 
- <a id="T178-R13-C02"></a>列 2: 
- <a id="T178-R13-C03"></a>列 3: 

<a id="T178-R14"></a>
**T178-R14**

- <a id="T178-R14-C01"></a>列 1: 
- <a id="T178-R14-C02"></a>列 2: 
- <a id="T178-R14-C03"></a>列 3: 

<a id="T178-R15"></a>
**T178-R15**

- <a id="T178-R15-C01"></a>列 1: 
- <a id="T178-R15-C02"></a>列 2: 
- <a id="T178-R15-C03"></a>列 3: 

<a id="T178-R16"></a>
**T178-R16**

- <a id="T178-R16-C01"></a>列 1: 
- <a id="T178-R16-C02"></a>列 2: 
- <a id="T178-R16-C03"></a>列 3: 

<a id="T178-R17"></a>
**T178-R17**

- <a id="T178-R17-C01"></a>列 1: 
- <a id="T178-R17-C02"></a>列 2: 
- <a id="T178-R17-C03"></a>列 3: 

<a id="T178-R18"></a>
**T178-R18**

- <a id="T178-R18-C01"></a>列 1: 
- <a id="T178-R18-C02"></a>列 2: 
- <a id="T178-R18-C03"></a>列 3: 

<a id="T178-R19"></a>
**T178-R19**

- <a id="T178-R19-C01"></a>列 1: 
- <a id="T178-R19-C02"></a>列 2: 
- <a id="T178-R19-C03"></a>列 3: 

<a id="T178-R20"></a>
**T178-R20**

- <a id="T178-R20-C01"></a>列 1: 
- <a id="T178-R20-C02"></a>列 2: 
- <a id="T178-R20-C03"></a>列 3: 

<a id="T178-R21"></a>
**T178-R21**

- <a id="T178-R21-C01"></a>列 1: 
- <a id="T178-R21-C02"></a>列 2: 
- <a id="T178-R21-C03"></a>列 3: 

<a id="T178-R22"></a>
**T178-R22**

- <a id="T178-R22-C01"></a>列 1: 
- <a id="T178-R22-C02"></a>列 2: 
- <a id="T178-R22-C03"></a>列 3: 

<a id="T178-R23"></a>
**T178-R23**

- <a id="T178-R23-C01"></a>列 1: 
- <a id="T178-R23-C02"></a>列 2: 
- <a id="T178-R23-C03"></a>列 3: 

<a id="T178-R24"></a>
**T178-R24**

- <a id="T178-R24-C01"></a>列 1: 
- <a id="T178-R24-C02"></a>列 2: 
- <a id="T178-R24-C03"></a>列 3: 

<a id="T178-R25"></a>
**T178-R25**

- <a id="T178-R25-C01"></a>列 1: 
- <a id="T178-R25-C02"></a>列 2: 
- <a id="T178-R25-C03"></a>列 3: 

<a id="T178-R26"></a>
**T178-R26**

- <a id="T178-R26-C01"></a>列 1: 
- <a id="T178-R26-C02"></a>列 2: 
- <a id="T178-R26-C03"></a>列 3: 

<a id="P181"></a>

P.800 DCR Experiments

<a id="P183"></a>

Experiment DCR-1:

<a id="P184"></a>

[

<a id="P185"></a>

Tables  E.1.1 to  E.1.5 show conditions to be used for this experiment, list of preliminaries ,full list of conditions, and definition of Speech categories.

<a id="P187"></a>

Table E.1.1: Factors and Conditions for Experiment DCR-1

<a id="T188"></a>

<a id="T188-R01"></a>
**T188-R01**

- <a id="T188-R01-C01"></a>列 1: Main Codec Conditions
- <a id="T188-R01-C02"></a>列 2: 
- <a id="T188-R01-C03"></a>列 3: 

<a id="T188-R02"></a>
**T188-R02**

- <a id="T188-R02-C01"></a>列 1: Candidates
- <a id="T188-R02-C02"></a>列 2: 
- <a id="T188-R02-C03"></a>列 3: 

<a id="T188-R03"></a>
**T188-R03**

- <a id="T188-R03-C01"></a>列 1: Operating modes
- <a id="T188-R03-C02"></a>列 2: 
- <a id="T188-R03-C03"></a>列 3: 

<a id="T188-R04"></a>
**T188-R04**

- <a id="T188-R04-C01"></a>列 1: Input level
- <a id="T188-R04-C02"></a>列 2: 
- <a id="T188-R04-C03"></a>列 3: 

<a id="T188-R05"></a>
**T188-R05**

- <a id="T188-R05-C01"></a>列 1: Input frequency mask
- <a id="T188-R05-C02"></a>列 2: 
- <a id="T188-R05-C03"></a>列 3: 

<a id="T188-R06"></a>
**T188-R06**

- <a id="T188-R06-C01"></a>列 1: Noise
- <a id="T188-R06-C02"></a>列 2: 
- <a id="T188-R06-C03"></a>列 3: 

<a id="T188-R07"></a>
**T188-R07**

- <a id="T188-R07-C01"></a>列 1: Error Conditions
- <a id="T188-R07-C02"></a>列 2: 
- <a id="T188-R07-C03"></a>列 3: 

<a id="T188-R08"></a>
**T188-R08**

- <a id="T188-R08-C01"></a>列 1: 
- <a id="T188-R08-C02"></a>列 2: 
- <a id="T188-R08-C03"></a>列 3: 

<a id="T188-R09"></a>
**T188-R09**

- <a id="T188-R09-C01"></a>列 1: Codec references
- <a id="T188-R09-C02"></a>列 2: 
- <a id="T188-R09-C03"></a>列 3: 

<a id="T188-R10"></a>
**T188-R10**

- <a id="T188-R10-C01"></a>列 1: Codec references
- <a id="T188-R10-C02"></a>列 2: 
- <a id="T188-R10-C03"></a>列 3: 

<a id="T188-R11"></a>
**T188-R11**

- <a id="T188-R11-C01"></a>列 1: Input level
- <a id="T188-R11-C02"></a>列 2: 
- <a id="T188-R11-C03"></a>列 3: 

<a id="T188-R12"></a>
**T188-R12**

- <a id="T188-R12-C01"></a>列 1: Input frequency mask
- <a id="T188-R12-C02"></a>列 2: 
- <a id="T188-R12-C03"></a>列 3: 

<a id="T188-R13"></a>
**T188-R13**

- <a id="T188-R13-C01"></a>列 1: Noise
- <a id="T188-R13-C02"></a>列 2: 
- <a id="T188-R13-C03"></a>列 3: 

<a id="T188-R14"></a>
**T188-R14**

- <a id="T188-R14-C01"></a>列 1: Error Conditions
- <a id="T188-R14-C02"></a>列 2: 
- <a id="T188-R14-C03"></a>列 3: 

<a id="T188-R15"></a>
**T188-R15**

- <a id="T188-R15-C01"></a>列 1: 
- <a id="T188-R15-C02"></a>列 2: 
- <a id="T188-R15-C03"></a>列 3: 

<a id="T188-R16"></a>
**T188-R16**

- <a id="T188-R16-C01"></a>列 1: Other references
- <a id="T188-R16-C02"></a>列 2: 
- <a id="T188-R16-C03"></a>列 3: 

<a id="T188-R17"></a>
**T188-R17**

- <a id="T188-R17-C01"></a>列 1: Direct
- <a id="T188-R17-C02"></a>列 2: 
- <a id="T188-R17-C03"></a>列 3: 

<a id="T188-R18"></a>
**T188-R18**

- <a id="T188-R18-C01"></a>列 1: MNRU
- <a id="T188-R18-C02"></a>列 2: 
- <a id="T188-R18-C03"></a>列 3: 

<a id="T188-R19"></a>
**T188-R19**

- <a id="T188-R19-C01"></a>列 1: Input frequency mask
- <a id="T188-R19-C02"></a>列 2: 
- <a id="T188-R19-C03"></a>列 3: 

<a id="T188-R20"></a>
**T188-R20**

- <a id="T188-R20-C01"></a>列 1: 
- <a id="T188-R20-C02"></a>列 2: 
- <a id="T188-R20-C03"></a>列 3: 

<a id="T188-R21"></a>
**T188-R21**

- <a id="T188-R21-C01"></a>列 1: Common Conditions
- <a id="T188-R21-C02"></a>列 2: 
- <a id="T188-R21-C03"></a>列 3: 

<a id="T188-R22"></a>
**T188-R22**

- <a id="T188-R22-C01"></a>列 1: Number of talkers
- <a id="T188-R22-C02"></a>列 2: 
- <a id="T188-R22-C03"></a>列 3: 

<a id="T188-R23"></a>
**T188-R23**

- <a id="T188-R23-C01"></a>列 1: Number of speech samples
- <a id="T188-R23-C02"></a>列 2: 
- <a id="T188-R23-C03"></a>列 3: 

<a id="T188-R24"></a>
**T188-R24**

- <a id="T188-R24-C01"></a>列 1: Listening Level
- <a id="T188-R24-C02"></a>列 2: 
- <a id="T188-R24-C03"></a>列 3: 

<a id="T188-R25"></a>
**T188-R25**

- <a id="T188-R25-C01"></a>列 1: Listeners
- <a id="T188-R25-C02"></a>列 2: 
- <a id="T188-R25-C03"></a>列 3: 

<a id="T188-R26"></a>
**T188-R26**

- <a id="T188-R26-C01"></a>列 1: Randomizations
- <a id="T188-R26-C02"></a>列 2: 
- <a id="T188-R26-C03"></a>列 3: 

<a id="T188-R27"></a>
**T188-R27**

- <a id="T188-R27-C01"></a>列 1: Rating Scale
- <a id="T188-R27-C02"></a>列 2: 
- <a id="T188-R27-C03"></a>列 3: 

<a id="T188-R28"></a>
**T188-R28**

- <a id="T188-R28-C01"></a>列 1: Listening System
- <a id="T188-R28-C02"></a>列 2: 
- <a id="T188-R28-C03"></a>列 3: 

<a id="T188-R29"></a>
**T188-R29**

- <a id="T188-R29-C01"></a>列 1: Listening Environment
- <a id="T188-R29-C02"></a>列 2: 
- <a id="T188-R29-C03"></a>列 3: 

<a id="P190"></a>

Table E.1.2: Preliminaries for Experiment P800-1

<a id="T191"></a>

<a id="T191-R01"></a>
**T191-R01**

- <a id="T191-R01-C01"></a>列 1: Trial #
- <a id="T191-R01-C02"></a>列 2: Label
- <a id="T191-R01-C03"></a>列 3: Talker
- <a id="T191-R01-C04"></a>列 4: Condition
- <a id="T191-R01-C05"></a>列 5: Bitrate [kbps]
- <a id="T191-R01-C06"></a>列 6: DTX
- <a id="T191-R01-C07"></a>列 7: Input Level
- <a id="T191-R01-C08"></a>列 8: FER/Profile

<a id="T191-R02"></a>
**T191-R02**

- <a id="T191-R02-C01"></a>列 1: 1
- <a id="T191-R02-C02"></a>列 2: 
- <a id="T191-R02-C03"></a>列 3: 
- <a id="T191-R02-C04"></a>列 4: 
- <a id="T191-R02-C05"></a>列 5: 
- <a id="T191-R02-C06"></a>列 6: 
- <a id="T191-R02-C07"></a>列 7: 
- <a id="T191-R02-C08"></a>列 8: 

<a id="T191-R03"></a>
**T191-R03**

- <a id="T191-R03-C01"></a>列 1: 2
- <a id="T191-R03-C02"></a>列 2: 
- <a id="T191-R03-C03"></a>列 3: 
- <a id="T191-R03-C04"></a>列 4: 
- <a id="T191-R03-C05"></a>列 5: 
- <a id="T191-R03-C06"></a>列 6: 
- <a id="T191-R03-C07"></a>列 7: 
- <a id="T191-R03-C08"></a>列 8: 

<a id="T191-R04"></a>
**T191-R04**

- <a id="T191-R04-C01"></a>列 1: 3
- <a id="T191-R04-C02"></a>列 2: 
- <a id="T191-R04-C03"></a>列 3: 
- <a id="T191-R04-C04"></a>列 4: 
- <a id="T191-R04-C05"></a>列 5: 
- <a id="T191-R04-C06"></a>列 6: 
- <a id="T191-R04-C07"></a>列 7: 
- <a id="T191-R04-C08"></a>列 8: 

<a id="T191-R05"></a>
**T191-R05**

- <a id="T191-R05-C01"></a>列 1: 4
- <a id="T191-R05-C02"></a>列 2: 
- <a id="T191-R05-C03"></a>列 3: 
- <a id="T191-R05-C04"></a>列 4: 
- <a id="T191-R05-C05"></a>列 5: 
- <a id="T191-R05-C06"></a>列 6: 
- <a id="T191-R05-C07"></a>列 7: 
- <a id="T191-R05-C08"></a>列 8: 

<a id="T191-R06"></a>
**T191-R06**

- <a id="T191-R06-C01"></a>列 1: 5
- <a id="T191-R06-C02"></a>列 2: 
- <a id="T191-R06-C03"></a>列 3: 
- <a id="T191-R06-C04"></a>列 4: 
- <a id="T191-R06-C05"></a>列 5: 
- <a id="T191-R06-C06"></a>列 6: 
- <a id="T191-R06-C07"></a>列 7: 
- <a id="T191-R06-C08"></a>列 8: 

<a id="T191-R07"></a>
**T191-R07**

- <a id="T191-R07-C01"></a>列 1: 6
- <a id="T191-R07-C02"></a>列 2: 
- <a id="T191-R07-C03"></a>列 3: 
- <a id="T191-R07-C04"></a>列 4: 
- <a id="T191-R07-C05"></a>列 5: 
- <a id="T191-R07-C06"></a>列 6: 
- <a id="T191-R07-C07"></a>列 7: 
- <a id="T191-R07-C08"></a>列 8: 

<a id="T191-R08"></a>
**T191-R08**

- <a id="T191-R08-C01"></a>列 1: 7
- <a id="T191-R08-C02"></a>列 2: 
- <a id="T191-R08-C03"></a>列 3: 
- <a id="T191-R08-C04"></a>列 4: 
- <a id="T191-R08-C05"></a>列 5: 
- <a id="T191-R08-C06"></a>列 6: 
- <a id="T191-R08-C07"></a>列 7: 
- <a id="T191-R08-C08"></a>列 8: 

<a id="T191-R09"></a>
**T191-R09**

- <a id="T191-R09-C01"></a>列 1: 8
- <a id="T191-R09-C02"></a>列 2: 
- <a id="T191-R09-C03"></a>列 3: 
- <a id="T191-R09-C04"></a>列 4: 
- <a id="T191-R09-C05"></a>列 5: 
- <a id="T191-R09-C06"></a>列 6: 
- <a id="T191-R09-C07"></a>列 7: 
- <a id="T191-R09-C08"></a>列 8: 

<a id="T191-R10"></a>
**T191-R10**

- <a id="T191-R10-C01"></a>列 1: 9
- <a id="T191-R10-C02"></a>列 2: 
- <a id="T191-R10-C03"></a>列 3: 
- <a id="T191-R10-C04"></a>列 4: 
- <a id="T191-R10-C05"></a>列 5: 
- <a id="T191-R10-C06"></a>列 6: 
- <a id="T191-R10-C07"></a>列 7: 
- <a id="T191-R10-C08"></a>列 8: 

<a id="T191-R11"></a>
**T191-R11**

- <a id="T191-R11-C01"></a>列 1: 10
- <a id="T191-R11-C02"></a>列 2: 
- <a id="T191-R11-C03"></a>列 3: 
- <a id="T191-R11-C04"></a>列 4: 
- <a id="T191-R11-C05"></a>列 5: 
- <a id="T191-R11-C06"></a>列 6: 
- <a id="T191-R11-C07"></a>列 7: 
- <a id="T191-R11-C08"></a>列 8: 

<a id="T191-R12"></a>
**T191-R12**

- <a id="T191-R12-C01"></a>列 1: 11
- <a id="T191-R12-C02"></a>列 2: 
- <a id="T191-R12-C03"></a>列 3: 
- <a id="T191-R12-C04"></a>列 4: 
- <a id="T191-R12-C05"></a>列 5: 
- <a id="T191-R12-C06"></a>列 6: 
- <a id="T191-R12-C07"></a>列 7: 
- <a id="T191-R12-C08"></a>列 8: 

<a id="T191-R13"></a>
**T191-R13**

- <a id="T191-R13-C01"></a>列 1: 12
- <a id="T191-R13-C02"></a>列 2: 
- <a id="T191-R13-C03"></a>列 3: 
- <a id="T191-R13-C04"></a>列 4: 
- <a id="T191-R13-C05"></a>列 5: 
- <a id="T191-R13-C06"></a>列 6: 
- <a id="T191-R13-C07"></a>列 7: 
- <a id="T191-R13-C08"></a>列 8: 

<a id="P193"></a>

Table E.1.3: Test conditions for Experiment P800-1,<br>
stereo speech and music and mixed content under clean channel conditions

<a id="P194"></a>

Table E.1.3: P.800 DCR test layout

<a id="T195"></a>

<a id="T195-R01"></a>
**T195-R01**

- <a id="T195-R01-C01"></a>列 1: Label
- <a id="T195-R01-C02"></a>列 2: Condition
- <a id="T195-R01-C03"></a>列 3: Bitrate [kbps]
- <a id="T195-R01-C04"></a>列 4: DTX
- <a id="T195-R01-C05"></a>列 5: Input Level
- <a id="T195-R01-C06"></a>列 6: FER/Profile

<a id="T195-R02"></a>
**T195-R02**

- <a id="T195-R02-C01"></a>列 1: c01
- <a id="T195-R02-C02"></a>列 2: Reference
- <a id="T195-R02-C03"></a>列 3: -
- <a id="T195-R02-C04"></a>列 4: -
- <a id="T195-R02-C05"></a>列 5: -
- <a id="T195-R02-C06"></a>列 6: -

<a id="T195-R03"></a>
**T195-R03**

- <a id="T195-R03-C01"></a>列 1: c02
- <a id="T195-R03-C02"></a>列 2: MNRU Q = xx dB
- <a id="T195-R03-C03"></a>列 3: -
- <a id="T195-R03-C04"></a>列 4: -
- <a id="T195-R03-C05"></a>列 5: -
- <a id="T195-R03-C06"></a>列 6: -

<a id="T195-R04"></a>
**T195-R04**

- <a id="T195-R04-C01"></a>列 1: c03
- <a id="T195-R04-C02"></a>列 2: MNRU Q = xx dB
- <a id="T195-R04-C03"></a>列 3: -
- <a id="T195-R04-C04"></a>列 4: -
- <a id="T195-R04-C05"></a>列 5: -
- <a id="T195-R04-C06"></a>列 6: -

<a id="T195-R05"></a>
**T195-R05**

- <a id="T195-R05-C01"></a>列 1: c04
- <a id="T195-R05-C02"></a>列 2: MNRU Q = xx dB
- <a id="T195-R05-C03"></a>列 3: -
- <a id="T195-R05-C04"></a>列 4: -
- <a id="T195-R05-C05"></a>列 5: -
- <a id="T195-R05-C06"></a>列 6: -

<a id="T195-R06"></a>
**T195-R06**

- <a id="T195-R06-C01"></a>列 1: c05
- <a id="T195-R06-C02"></a>列 2: MNRU Q = xx dB
- <a id="T195-R06-C03"></a>列 3: -
- <a id="T195-R06-C04"></a>列 4: -
- <a id="T195-R06-C05"></a>列 5: -
- <a id="T195-R06-C06"></a>列 6: -

<a id="T195-R07"></a>
**T195-R07**

- <a id="T195-R07-C01"></a>列 1: c06
- <a id="T195-R07-C02"></a>列 2: MNRU Q = xx dB
- <a id="T195-R07-C03"></a>列 3: -
- <a id="T195-R07-C04"></a>列 4: -
- <a id="T195-R07-C05"></a>列 5: -
- <a id="T195-R07-C06"></a>列 6: -

<a id="T195-R08"></a>
**T195-R08**

- <a id="T195-R08-C01"></a>列 1: c07
- <a id="T195-R08-C02"></a>列 2: 
- <a id="T195-R08-C03"></a>列 3: 
- <a id="T195-R08-C04"></a>列 4: 
- <a id="T195-R08-C05"></a>列 5: 
- <a id="T195-R08-C06"></a>列 6: 

<a id="T195-R09"></a>
**T195-R09**

- <a id="T195-R09-C01"></a>列 1: c08
- <a id="T195-R09-C02"></a>列 2: 
- <a id="T195-R09-C03"></a>列 3: 
- <a id="T195-R09-C04"></a>列 4: 
- <a id="T195-R09-C05"></a>列 5: 
- <a id="T195-R09-C06"></a>列 6: 

<a id="T195-R10"></a>
**T195-R10**

- <a id="T195-R10-C01"></a>列 1: C09
- <a id="T195-R10-C02"></a>列 2: 
- <a id="T195-R10-C03"></a>列 3: 
- <a id="T195-R10-C04"></a>列 4: 
- <a id="T195-R10-C05"></a>列 5: 
- <a id="T195-R10-C06"></a>列 6: 

<a id="T195-R11"></a>
**T195-R11**

- <a id="T195-R11-C01"></a>列 1: c10
- <a id="T195-R11-C02"></a>列 2: 
- <a id="T195-R11-C03"></a>列 3: 
- <a id="T195-R11-C04"></a>列 4: 
- <a id="T195-R11-C05"></a>列 5: 
- <a id="T195-R11-C06"></a>列 6: 

<a id="T195-R12"></a>
**T195-R12**

- <a id="T195-R12-C01"></a>列 1: c11
- <a id="T195-R12-C02"></a>列 2: 
- <a id="T195-R12-C03"></a>列 3: 
- <a id="T195-R12-C04"></a>列 4: 
- <a id="T195-R12-C05"></a>列 5: 
- <a id="T195-R12-C06"></a>列 6: 

<a id="T195-R13"></a>
**T195-R13**

- <a id="T195-R13-C01"></a>列 1: c12
- <a id="T195-R13-C02"></a>列 2: 
- <a id="T195-R13-C03"></a>列 3: 
- <a id="T195-R13-C04"></a>列 4: 
- <a id="T195-R13-C05"></a>列 5: 
- <a id="T195-R13-C06"></a>列 6: 

<a id="T195-R14"></a>
**T195-R14**

- <a id="T195-R14-C01"></a>列 1: c13
- <a id="T195-R14-C02"></a>列 2: 
- <a id="T195-R14-C03"></a>列 3: 
- <a id="T195-R14-C04"></a>列 4: 
- <a id="T195-R14-C05"></a>列 5: 
- <a id="T195-R14-C06"></a>列 6: 

<a id="T195-R15"></a>
**T195-R15**

- <a id="T195-R15-C01"></a>列 1: c14
- <a id="T195-R15-C02"></a>列 2: 
- <a id="T195-R15-C03"></a>列 3: 
- <a id="T195-R15-C04"></a>列 4: 
- <a id="T195-R15-C05"></a>列 5: 
- <a id="T195-R15-C06"></a>列 6: 

<a id="T195-R16"></a>
**T195-R16**

- <a id="T195-R16-C01"></a>列 1: c15
- <a id="T195-R16-C02"></a>列 2: 
- <a id="T195-R16-C03"></a>列 3: 
- <a id="T195-R16-C04"></a>列 4: 
- <a id="T195-R16-C05"></a>列 5: 
- <a id="T195-R16-C06"></a>列 6: 

<a id="T195-R17"></a>
**T195-R17**

- <a id="T195-R17-C01"></a>列 1: c16
- <a id="T195-R17-C02"></a>列 2: 
- <a id="T195-R17-C03"></a>列 3: 
- <a id="T195-R17-C04"></a>列 4: 
- <a id="T195-R17-C05"></a>列 5: 
- <a id="T195-R17-C06"></a>列 6: 

<a id="T195-R18"></a>
**T195-R18**

- <a id="T195-R18-C01"></a>列 1: c17
- <a id="T195-R18-C02"></a>列 2: 
- <a id="T195-R18-C03"></a>列 3: 
- <a id="T195-R18-C04"></a>列 4: 
- <a id="T195-R18-C05"></a>列 5: 
- <a id="T195-R18-C06"></a>列 6: 

<a id="T195-R19"></a>
**T195-R19**

- <a id="T195-R19-C01"></a>列 1: c18
- <a id="T195-R19-C02"></a>列 2: 
- <a id="T195-R19-C03"></a>列 3: 
- <a id="T195-R19-C04"></a>列 4: 
- <a id="T195-R19-C05"></a>列 5: 
- <a id="T195-R19-C06"></a>列 6: 

<a id="T195-R20"></a>
**T195-R20**

- <a id="T195-R20-C01"></a>列 1: c19
- <a id="T195-R20-C02"></a>列 2: 
- <a id="T195-R20-C03"></a>列 3: 
- <a id="T195-R20-C04"></a>列 4: 
- <a id="T195-R20-C05"></a>列 5: 
- <a id="T195-R20-C06"></a>列 6: 

<a id="T195-R21"></a>
**T195-R21**

- <a id="T195-R21-C01"></a>列 1: c20
- <a id="T195-R21-C02"></a>列 2: 
- <a id="T195-R21-C03"></a>列 3: 
- <a id="T195-R21-C04"></a>列 4: 
- <a id="T195-R21-C05"></a>列 5: 
- <a id="T195-R21-C06"></a>列 6: 

<a id="T195-R22"></a>
**T195-R22**

- <a id="T195-R22-C01"></a>列 1: c21
- <a id="T195-R22-C02"></a>列 2: 
- <a id="T195-R22-C03"></a>列 3: 
- <a id="T195-R22-C04"></a>列 4: 
- <a id="T195-R22-C05"></a>列 5: 
- <a id="T195-R22-C06"></a>列 6: 

<a id="T195-R23"></a>
**T195-R23**

- <a id="T195-R23-C01"></a>列 1: c22
- <a id="T195-R23-C02"></a>列 2: 
- <a id="T195-R23-C03"></a>列 3: 
- <a id="T195-R23-C04"></a>列 4: 
- <a id="T195-R23-C05"></a>列 5: 
- <a id="T195-R23-C06"></a>列 6: 

<a id="T195-R24"></a>
**T195-R24**

- <a id="T195-R24-C01"></a>列 1: c23
- <a id="T195-R24-C02"></a>列 2: 
- <a id="T195-R24-C03"></a>列 3: 
- <a id="T195-R24-C04"></a>列 4: 
- <a id="T195-R24-C05"></a>列 5: 
- <a id="T195-R24-C06"></a>列 6: 

<a id="T195-R25"></a>
**T195-R25**

- <a id="T195-R25-C01"></a>列 1: c24
- <a id="T195-R25-C02"></a>列 2: 
- <a id="T195-R25-C03"></a>列 3: 
- <a id="T195-R25-C04"></a>列 4: 
- <a id="T195-R25-C05"></a>列 5: 
- <a id="T195-R25-C06"></a>列 6: 

<a id="T195-R26"></a>
**T195-R26**

- <a id="T195-R26-C01"></a>列 1: c25
- <a id="T195-R26-C02"></a>列 2: 
- <a id="T195-R26-C03"></a>列 3: 
- <a id="T195-R26-C04"></a>列 4: 
- <a id="T195-R26-C05"></a>列 5: 
- <a id="T195-R26-C06"></a>列 6: 

<a id="T195-R27"></a>
**T195-R27**

- <a id="T195-R27-C01"></a>列 1: c26
- <a id="T195-R27-C02"></a>列 2: 
- <a id="T195-R27-C03"></a>列 3: 
- <a id="T195-R27-C04"></a>列 4: 
- <a id="T195-R27-C05"></a>列 5: 
- <a id="T195-R27-C06"></a>列 6: 

<a id="T195-R28"></a>
**T195-R28**

- <a id="T195-R28-C01"></a>列 1: c27
- <a id="T195-R28-C02"></a>列 2: 
- <a id="T195-R28-C03"></a>列 3: 
- <a id="T195-R28-C04"></a>列 4: 
- <a id="T195-R28-C05"></a>列 5: 
- <a id="T195-R28-C06"></a>列 6: 

<a id="T195-R29"></a>
**T195-R29**

- <a id="T195-R29-C01"></a>列 1: c28
- <a id="T195-R29-C02"></a>列 2: 
- <a id="T195-R29-C03"></a>列 3: 
- <a id="T195-R29-C04"></a>列 4: 
- <a id="T195-R29-C05"></a>列 5: 
- <a id="T195-R29-C06"></a>列 6: 

<a id="T195-R30"></a>
**T195-R30**

- <a id="T195-R30-C01"></a>列 1: c29
- <a id="T195-R30-C02"></a>列 2: 
- <a id="T195-R30-C03"></a>列 3: 
- <a id="T195-R30-C04"></a>列 4: 
- <a id="T195-R30-C05"></a>列 5: 
- <a id="T195-R30-C06"></a>列 6: 

<a id="T195-R31"></a>
**T195-R31**

- <a id="T195-R31-C01"></a>列 1: c30
- <a id="T195-R31-C02"></a>列 2: 
- <a id="T195-R31-C03"></a>列 3: 
- <a id="T195-R31-C04"></a>列 4: 
- <a id="T195-R31-C05"></a>列 5: 
- <a id="T195-R31-C06"></a>列 6: 

<a id="T195-R32"></a>
**T195-R32**

- <a id="T195-R32-C01"></a>列 1: c31
- <a id="T195-R32-C02"></a>列 2: 
- <a id="T195-R32-C03"></a>列 3: 
- <a id="T195-R32-C04"></a>列 4: 
- <a id="T195-R32-C05"></a>列 5: 
- <a id="T195-R32-C06"></a>列 6: 

<a id="T195-R33"></a>
**T195-R33**

- <a id="T195-R33-C01"></a>列 1: c32
- <a id="T195-R33-C02"></a>列 2: 
- <a id="T195-R33-C03"></a>列 3: 
- <a id="T195-R33-C04"></a>列 4: 
- <a id="T195-R33-C05"></a>列 5: 
- <a id="T195-R33-C06"></a>列 6: 

<a id="T195-R34"></a>
**T195-R34**

- <a id="T195-R34-C01"></a>列 1: c33
- <a id="T195-R34-C02"></a>列 2: 
- <a id="T195-R34-C03"></a>列 3: 
- <a id="T195-R34-C04"></a>列 4: 
- <a id="T195-R34-C05"></a>列 5: 
- <a id="T195-R34-C06"></a>列 6: 

<a id="T195-R35"></a>
**T195-R35**

- <a id="T195-R35-C01"></a>列 1: c34
- <a id="T195-R35-C02"></a>列 2: 
- <a id="T195-R35-C03"></a>列 3: 
- <a id="T195-R35-C04"></a>列 4: 
- <a id="T195-R35-C05"></a>列 5: 
- <a id="T195-R35-C06"></a>列 6: 

<a id="T195-R36"></a>
**T195-R36**

- <a id="T195-R36-C01"></a>列 1: c35
- <a id="T195-R36-C02"></a>列 2: 
- <a id="T195-R36-C03"></a>列 3: 
- <a id="T195-R36-C04"></a>列 4: 
- <a id="T195-R36-C05"></a>列 5: 
- <a id="T195-R36-C06"></a>列 6: 

<a id="T195-R37"></a>
**T195-R37**

- <a id="T195-R37-C01"></a>列 1: c36
- <a id="T195-R37-C02"></a>列 2: 
- <a id="T195-R37-C03"></a>列 3: 
- <a id="T195-R37-C04"></a>列 4: 
- <a id="T195-R37-C05"></a>列 5: 
- <a id="T195-R37-C06"></a>列 6: 

<a id="P196"></a>

]

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH    Tdoc S4aA260167<br>    Shanghai, China, September 28-30, 2026    rev. of S4aA260157
