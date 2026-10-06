# S4aA260181 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260181-ULBC-7_Processing_plan_v020_cl.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Editor[^1]

<a id="P001"></a>

Title:    ULBC Permanent document (ULBC-7): Processing plan

<a id="P002"></a>

Version:    0.2.0

<a id="P003"></a>

Agenda Item:    4.7

<a id="P005"></a>

Revision history:

<a id="T006"></a>

<a id="T006-R01"></a>
**T006-R01**

- <a id="T006-R01-C01"></a>列 1: Date
- <a id="T006-R01-C02"></a>列 2: Meeting
- <a id="T006-R01-C03"></a>列 3: Subject/Comment
- <a id="T006-R01-C04"></a>列 4: Old
- <a id="T006-R01-C05"></a>列 5: New

<a id="T006-R02"></a>
**T006-R02**

- <a id="T006-R02-C01"></a>列 1: 2026-08-27
- <a id="T006-R02-C02"></a>列 2: SA4#137-e
- <a id="T006-R02-C03"></a>列 3: Initial version based on S4-141392 (EVS-7c Processing plan), S4-261018, S4-261625
- <a id="T006-R02-C04"></a>列 4: N/A
- <a id="T006-R02-C05"></a>列 5: 0.1.0

<a id="T006-R03"></a>
**T006-R03**

- <a id="T006-R03-C01"></a>列 1: 2026-09-28
- <a id="T006-R03-C02"></a>列 2: Audio SWG AH on ULBC
- <a id="T006-R03-C03"></a>列 3: Editorial updates in S4aA260128
- <a id="T006-R03-C04"></a>列 4: 0.1.0
- <a id="T006-R03-C05"></a>列 5: 0.1.1

<a id="T006-R04"></a>
**T006-R04**

- <a id="T006-R04-C01"></a>列 1: 2026-09-28
- <a id="T006-R04-C02"></a>列 2: Audio SWG AH on ULBC
- <a id="T006-R04-C03"></a>列 3: S4aA260119 on objective testing database included in clause 5.6.
- <a id="T006-R04-C04"></a>列 4: 0.1.1
- <a id="T006-R04-C05"></a>列 5: 0.2.0

<a id="P008"></a>

[

<a id="P009"></a>

Introduction

<a id="P010"></a>

This document defines how audio material must be prepared for the [qualification and selection tests] of the 3GPP ULBC codec and provides details on the software modules and files required. It should be read in conjunction with its associated ULBC [qualification and selection phase test plans respectively] [X].

<a id="P012"></a>

Editor’s note: The contents are largely imported from the EVS 7c processing plan and everything needs further review.

<a id="P015"></a>

Responsibilities

<a id="P016"></a>

Editor’s note: Clarify responsibilities of involved entities such as host lab, processing lab, listening labs, etc.

<a id="P017"></a>

Editor’s note: Listening labs must provide unknown/newly recorded audio samples to avoid any overlap with potential training data of ML tools.

<a id="P019"></a>

Definitions and formats

<a id="P020"></a>

The following filename convention is used for source material:

<a id="P021"></a>

Input<Fs>.wav    Fs (in kHz) is the input sampling frequency to a processing module (or sequence of modules). Fs is either .8k, .16k, .32k or .48k.

<a id="P022"></a>

Output<Fs>.wav    Fs (in kHz) is the output sampling frequency from a processing module (or sequence of modules). Fs is either .8k, .16k, .32k or .48k.

<a id="P023"></a>

Noise<Fs>.wav    Fs (in kHz) is the noise sampling frequency to a processing module (or sequences of modules). Fs is either .8k, .16k, .32k or .48k.

<a id="P024"></a>

The format of the above files is 16-bit integer WAV format. Other command line filenames and variables will be described in the relevant part of the document.

<a id="P025"></a>

The codecs will use the ITU-T G.192 [2] format as a common bit-stream interface, if available.

<a id="P026"></a>

All executables are in the [Win32 format, i.e. are native binaries for the 32-bit Microsoft Windows platform.]

<a id="P027"></a>

Editor’s note: Processing platform is TBD, but it will likely not be Win32 binary format.

<a id="P029"></a>

Processing Stages for the ULBC [Qualification and Selection Phases]

<a id="P030"></a>

General

<a id="P031"></a>

This section defines, in the form of diagrams, the processing stages required by the ULBC candidate codec under test. Version [XXX] of the ITU-T Software Tool Library [X] is used for this processing. Further tools used for this exercise are listed in Annex A.

<a id="P032"></a>

Editor’s note: Annex A to be added.

<a id="P033"></a>

Experiments and experiment designators

<a id="P034"></a>

Editor’s note: Outline of the experiments from the test plan

<a id="P035"></a>

Source material pre-processing requirements

<a id="P036"></a>

General

<a id="P037"></a>

The source material shall be 48-kHz sampled with 16-bit integer resolution. The format shall be WAVE, compatible for use with ITU-T Software Tool Library [X]. The source material shall have an audio bandwidth corresponding to the bandwidth to be tested.

<a id="P038"></a>

Listening lab designators

<a id="P039"></a>

The following table lists the responsible listening labs (LL) with their dedicated LL designator to be used for the file naming convention.

<a id="P040"></a>

Editor’s note: Add table listing listening labs, experiments and the corresponding LL designators (as described above).

<a id="P041"></a>

Naming examples of the input files and processed output files

<a id="P042"></a>

General

<a id="P043"></a>

The selection test plan [X] gives the file name extensions of the processed files, as they are needed for listening presentation. The following sections describe the file naming conventions where all letters in blue indicate variables in the filename while black letters indicate constants.

<a id="P044"></a>

Input speech files

<a id="P045"></a>

The filenames of the input speech samples are represented by:

<a id="P046"></a>

speech\leegysz.48k

<a id="P047"></a>

where:

<a id="P048"></a>

l stands for the listening lab designator (a through c according to Table 2)

<a id="P049"></a>

ee stands for the experiment designator, e.g. n1 (see Table 1)

<a id="P050"></a>

g is gender of talker (i.e. f for female and m for male) and y is the talker number: 1, 2, 3

<a id="P051"></a>

s stands for sample and z is the sample number; 1, 2, 3, 4, 5 where 5 is the preliminary

<a id="P053"></a>

Input music and mixed content files

<a id="P054"></a>

The filenames of the input music and mixed content samples are represented by:

<a id="P055"></a>

mixedmusic\leeaysz.48k

<a id="P056"></a>

where:

<a id="P057"></a>

l stands for the listening lab designator (a through c according to Table 2)

<a id="P058"></a>

ee stands for the experiment designator, e.g. n1 (see Table 1)

<a id="P059"></a>

a stands for music/mixed audio, and y is the category where

<a id="P060"></a>

## 1 stands for classical music

<a id="P061"></a>

## 2 stands for modern instrumental music

<a id="P062"></a>

## 3 stands for modern vocal music

<a id="P063"></a>

## 4 stands for radio jingle, movie trailer, advertisement

<a id="P064"></a>

## 5 stands for on hold content / answering machine message

<a id="P065"></a>

## 6 stands for speech over background music

<a id="P066"></a>

s stands for sample and z is the sample number; 1, 2, 3, 4, 5  where 5 is the preliminary

<a id="P068"></a>

Editor’s note: If applicable. Otherwise, this clause might become void.

<a id="P069"></a>

Noise files

<a id="P070"></a>

The filenames of the input noise samples are represented by:

<a id="P071"></a>

noise\nx.48k

<a id="P072"></a>

where:

<a id="P073"></a>

n stands for noise, and x is [c for car noise, s for street noise and o for office noise].

<a id="P074"></a>

Processed speech files

<a id="P075"></a>

The filenames of the processed speech samples are represented by:

<a id="P076"></a>

leegysz.cnn

<a id="P077"></a>

where:

<a id="P078"></a>

l stands for the listening lab designator (a through c according to Table 2)

<a id="P079"></a>

ee stands for the experiment designator, e.g. n1 (see Table 1)

<a id="P080"></a>

g is gender of talker (i.e. f for female and m for male) and y is the talker number: 1, 2, 3

<a id="P081"></a>

s stands for sample and z is the sample number; 1, 2, 3, 4, 5 where 5 is the preliminary

<a id="P082"></a>

c stands for the condition with the number nn = 01, 02, .. as specified in the test plan [X]

<a id="P084"></a>

Processed music and mixed content files

<a id="P085"></a>

The filenames of the processed music and mixed content items are represented by

<a id="P086"></a>

leeaysz.cnn

<a id="P087"></a>

where:

<a id="P088"></a>

l stands for the proponent designator (a through c according to Table 2)

<a id="P089"></a>

ee stands for the experiment designator, e.g. n1 (see Table 1)

<a id="P090"></a>

a stands for music/mixed audio, and y is the category where

<a id="P091"></a>

## 1 stands for classical music

<a id="P092"></a>

## 2 stands for modern instrumental music

<a id="P093"></a>

## 3 stands for modern vocal music

<a id="P094"></a>

## 4 stands for radio jingle, movie trailer, advertisement

<a id="P095"></a>

## 5 stands for on hold content / answering machine message

<a id="P096"></a>

## 6 stands for speech over background music

<a id="P097"></a>

s stands for sample and z is the sample number; 1, 2, 3, 4, 5 where 5 is the preliminary

<a id="P098"></a>

c stands for the condition with the number nn = 01, 02, .. as specified in the test plan [X]

<a id="P100"></a>

Editor’s note: If applicable. Otherwise, this section might become void.

<a id="P101"></a>

File concatenation, separation, sequences and module initialisation

<a id="P102"></a>

Concatenated sequences processing

<a id="P103"></a>

In all Experiments, the pre-processed material will be processed in concatenated files comprising a preamble and a series of sentences for speech or a series of samples for mixed /music. The preamble for speech and mixed/music concatenation will be 10 seconds long.

<a id="P104"></a>

Preamble definition

<a id="P105"></a>

The preamble in the speech/music path shall not be digital silence (i.e. 16-bit samples equal to zero), but a low-level random noise with amplitude between +4 and -4.

<a id="P106"></a>

Required samples and required sample lengths

<a id="P107"></a>

The definition of the speech, music and mixed content samples and the corresponding sample length can be found in the selection test plan, section X.

<a id="P108"></a>

Editor’s note: Adapt the highlighted text.

<a id="P109"></a>

Noise recordings

<a id="P110"></a>

A description of the available noise files is given in the [the test plan, Section 4.4.2 “Noise material”]. For each noisy speech experiment, one noise file from the list of available files per type [car noise, street noise and office noise] will be selected randomly, according to [Annex X]. The selected files will be used for the processing of the subjective experiments. [The test plan [X] describes the allocation of the noise type and the SNR level per experiment.]

<a id="P111"></a>

Editor’s note: Currently unclear, how far ULBC wants to follow the EVS test plan in these aspects. Adapt the highlighted text.

<a id="P112"></a>

Editor’s note: Noise types are TBD.

<a id="P114"></a>

Frame error application

<a id="P115"></a>

In frame erasure conditions, the erasures shall affect the same segments of speech signal for the ULBC candidate and reference codes. This shall be done by compensating for all encoder-side delays (or for all encoder-side delays of the core layer in case of embedded codecs). The ULBC encoder and decoder executables shall compensate the delay of the output files. The delay of reference codecs shall be compensated prior to the processing by the reference encoder, as specified in 5.2.5.

<a id="P116"></a>

Note: No delay compensation is applied for jitter related delay.

<a id="P117"></a>

Note: Exact delay compensation might not be possible.

<a id="P118"></a>

Editor’s note: May need to be adapted to the frame length and bundling to be used for ULBC. For instance, different patterns would need to be prepared for ULBC and AMR-WB due to differing frame length.

<a id="P119"></a>

File naming error patterns

<a id="P120"></a>

Frame erasure files will have the name “patterns\eefrr.g192”, where:

<a id="P121"></a>

ee stands for the experiment designator, e.g. n1 (see Table 1)

<a id="P122"></a>

f stands for frame loss pattern file

<a id="P123"></a>

rr stands for the frame loss rate in per cent, i.e. 03, 06, or 10. 4.4.7 File naming jitter profiles

<a id="P124"></a>

According to [26.114], the MTSI jitter profiles have the file names “patterns\dly_error_profile_x.dat” where x is the profile number, i.e. 1,2,3,4,5,6,7,8,9,10.

<a id="P125"></a>

File naming jitter derived error patterns

<a id="P126"></a>

The error patterns which are derived from the MTSI jitter profiles have the file names “patterns\f_profile_x.g192”, where:

<a id="P127"></a>

f stands for frame loss pattern file

<a id="P128"></a>

profile_x stands for the number of the MTSI jitter profile, see 4.3.7.

<a id="P129"></a>

File naming rate switching profiles

<a id="P130"></a>

Rate switching profiles  will have the name “patterns\eersx”, where:

<a id="P131"></a>

ee stands for the experiment designator, e.g. n1 (see Table 1)

<a id="P132"></a>

rs stands for rate switching file

<a id="P133"></a>

x stands for the sequence in the experiment, i.e. 1, 2, etc.

<a id="P134"></a>

Editor’s note: If applicable. Otherwise, this section might become void.

<a id="P135"></a>

Concatenation setup

<a id="P136"></a>

Speech and music files are concatenated after level adjustment. For concatenation order, see Table 3 and Table 4 below where all samples are concatenated from left to right and line by line. For speech files, the concatenation order is therefore m1s1, f1s1, m2s1, f2s1, m3s1, f3s1, m2s2, f2s2, etc.. The final concatenated speech file results in one 250 seconds long sequence (10 sec preamble + 6x5x8 sec speech/music file). For mixed content and music the total length may vary. For conditions that include background noise, the speech files must be concatenated prior to the addition of the background noise which will be provided in 300-second long files. The starting sample (offset) of the noise file is chosen randomly as described in Annex C.1.4. The concatenated music and mixed content files need to be 20ms block aligned for further processing. Therefore, the concatenated sequence needs to be padded at the end with the first samples of the preamble to reach an integer number of 20ms blocks.

<a id="P137"></a>

As reported in AHEVS-226, the VAD of AMR-WB might need an unexpected long adaptation time to produce reliable results. Therefore, the concatenated input sequence for the AMR-WB encoder conditions (AMR-WB codec, AMR-WB encoder/G.718-IO decoder, AMR-WB encoder/EVS-IO decoder) with DTX on in noisy speech experiments shall be extended by the repetition of the preamble and the concatenated speech files. This leads to a total length of 500 sec for those concatenated sequences, i.e. twice the sequence consisting of a 10 sec preamble plus 6x5x8 sec for the speech samples.

<a id="P138"></a>

Table 3: Concatenation order of speech files

<a id="T139"></a>

<a id="T139-R01"></a>
**T139-R01**

- <a id="T139-R01-C01"></a>列 1: Sample
- <a id="T139-R01-C02"></a>列 2（跨列:6）: Talker sequence in concatenated files

<a id="T139-R02"></a>
**T139-R02**

- <a id="T139-R02-C01"></a>列 1: 1
- <a id="T139-R02-C02"></a>列 2: m1
- <a id="T139-R02-C03"></a>列 3: f1
- <a id="T139-R02-C04"></a>列 4: m2
- <a id="T139-R02-C05"></a>列 5: f2
- <a id="T139-R02-C06"></a>列 6: m3
- <a id="T139-R02-C07"></a>列 7: f3

<a id="T139-R03"></a>
**T139-R03**

- <a id="T139-R03-C01"></a>列 1: 2
- <a id="T139-R03-C02"></a>列 2: m2
- <a id="T139-R03-C03"></a>列 3: f2
- <a id="T139-R03-C04"></a>列 4: m1
- <a id="T139-R03-C05"></a>列 5: f1
- <a id="T139-R03-C06"></a>列 6: f3
- <a id="T139-R03-C07"></a>列 7: m3

<a id="T139-R04"></a>
**T139-R04**

- <a id="T139-R04-C01"></a>列 1: 3
- <a id="T139-R04-C02"></a>列 2: m1
- <a id="T139-R04-C03"></a>列 3: f3
- <a id="T139-R04-C04"></a>列 4: m3
- <a id="T139-R04-C05"></a>列 5: m2
- <a id="T139-R04-C06"></a>列 6: f2
- <a id="T139-R04-C07"></a>列 7: f1

<a id="T139-R05"></a>
**T139-R05**

- <a id="T139-R05-C01"></a>列 1: 4
- <a id="T139-R05-C02"></a>列 2: m3
- <a id="T139-R05-C03"></a>列 3: f1
- <a id="T139-R05-C04"></a>列 4: f2
- <a id="T139-R05-C05"></a>列 5: m2
- <a id="T139-R05-C06"></a>列 6: f3
- <a id="T139-R05-C07"></a>列 7: m1

<a id="T139-R06"></a>
**T139-R06**

- <a id="T139-R06-C01"></a>列 1: 5
- <a id="T139-R06-C02"></a>列 2: m3
- <a id="T139-R06-C03"></a>列 3: f2
- <a id="T139-R06-C04"></a>列 4: m1
- <a id="T139-R06-C05"></a>列 5: f1
- <a id="T139-R06-C06"></a>列 6: m2
- <a id="T139-R06-C07"></a>列 7: f3

<a id="P140"></a>

Table 4: Concatenation order of mixed content and music files

<a id="T141"></a>

<a id="T141-R01"></a>
**T141-R01**

- <a id="T141-R01-C01"></a>列 1: Sample
- <a id="T141-R01-C02"></a>列 2（跨列:6）: Mixed content/music sequence in concatenated files

<a id="T141-R02"></a>
**T141-R02**

- <a id="T141-R02-C01"></a>列 1: 1
- <a id="T141-R02-C02"></a>列 2: a1
- <a id="T141-R02-C03"></a>列 3: a3
- <a id="T141-R02-C04"></a>列 4: a2
- <a id="T141-R02-C05"></a>列 5: a4
- <a id="T141-R02-C06"></a>列 6: a5
- <a id="T141-R02-C07"></a>列 7: a6

<a id="T141-R03"></a>
**T141-R03**

- <a id="T141-R03-C01"></a>列 1: 2
- <a id="T141-R03-C02"></a>列 2: a2
- <a id="T141-R03-C03"></a>列 3: a4
- <a id="T141-R03-C04"></a>列 4: a1
- <a id="T141-R03-C05"></a>列 5: a5
- <a id="T141-R03-C06"></a>列 6: a3
- <a id="T141-R03-C07"></a>列 7: a6

<a id="T141-R04"></a>
**T141-R04**

- <a id="T141-R04-C01"></a>列 1: 3
- <a id="T141-R04-C02"></a>列 2: a1
- <a id="T141-R04-C03"></a>列 3: a6
- <a id="T141-R04-C04"></a>列 4: a3
- <a id="T141-R04-C05"></a>列 5: a5
- <a id="T141-R04-C06"></a>列 6: a2
- <a id="T141-R04-C07"></a>列 7: a4

<a id="T141-R05"></a>
**T141-R05**

- <a id="T141-R05-C01"></a>列 1: 4
- <a id="T141-R05-C02"></a>列 2: a2
- <a id="T141-R05-C03"></a>列 3: a5
- <a id="T141-R05-C04"></a>列 4: a6
- <a id="T141-R05-C05"></a>列 5: a1
- <a id="T141-R05-C06"></a>列 6: a3
- <a id="T141-R05-C07"></a>列 7: a4

<a id="T141-R06"></a>
**T141-R06**

- <a id="T141-R06-C01"></a>列 1: 5
- <a id="T141-R06-C02"></a>列 2: a3
- <a id="T141-R06-C03"></a>列 3: a2
- <a id="T141-R06-C04"></a>列 4: a1
- <a id="T141-R06-C05"></a>列 5: a6
- <a id="T141-R06-C06"></a>列 6: a5
- <a id="T141-R06-C07"></a>列 7: a4

<a id="P143"></a>

For all Experiments, the processed concatenated files should be divided into separate speech/music samples and named with the according file extension as specified in the test plan. This must be performed before final up-sampling stage, and a cosine (Hanning) window of duration 100ms must be applied to the start and end of the separated files. The procedure for splitting and windowing concatenated files is described in 5.1.10.

<a id="P144"></a>

For the AMR-WB encoder conditions with DTX on where a repeated concatenated sequence is used as input, the second half of the duplicate sequence needs to be extracted first without any windowing and the single files needs to be further separated from that portion as described above.

<a id="P145"></a>

For the mixed content and music experiments where ULBC is tested in the context of JBM testing, 0.2 sec of pure digital silence will be added before and after each audio sample during concatenation.

<a id="P146"></a>

General processing for background noise

<a id="P147"></a>

The offset of the noise file shall be removed using the astrip tool before any processing starts.

<a id="P149"></a>

The following steps are relevant for processing of narrowband, wideband and super-wideband conditions where a scaling factor F is applied to the background noise.

<a id="P150"></a>

The scaling factor F (in dB) to be applied to the MSIN or HP50 filtered noise signal is calculated as:

<a id="P152"></a>

F = - (R + S + 26)

<a id="P154"></a>

where R denotes the R.M.S. signal level of the MSIN filtered noise signal at a 8 kHz sampling rate expressed in dBov (see Figure 1) and S denotes the target SNR in dB.

<a id="P155"></a>

For NB experiments, the following method will be used for measuring the RMS level:

<a id="P157"></a>

For WB and SWB experiments, the following method will be used for measuring the RMS level:

<a id="P160"></a>

Figure 1: Measuring of RMS level

<a id="P161"></a>

Note: The test plan [X] describes which noise type and SNR level will be used for the noisy speech experiments.

<a id="P162"></a>

Processing for narrowband (NB) conditions

<a id="P163"></a>

As described in Pdoc EVS-7c [1], section 4.5. The processing of the ULBC codec candidate follows the processing of the EVS codec.

<a id="P164"></a>

Editor’s note: If applicable. Otherwise, this section might become void.

<a id="P165"></a>

Processing for wideband (WB) conditions

<a id="P166"></a>

Pre-processing stages (16-kHz sampling)

<a id="P167"></a>

Pre-processing for 16-kHz sampling file generation

<a id="P169"></a>

Figure 15: Pre-processing for speech file generation, 16-kHz sampling.

<a id="P170"></a>

Pre-processing for WB Clean speech conditions (16-kHz sampling)

<a id="P172"></a>

Figure 16: Pre-processing for WB Clean speech condition files, 16-kHz sampling.

<a id="P173"></a>

Pre-processing for speech mixed with background noise (16-kHz sampling)

<a id="P176"></a>

Figure 17: Pre-processing for speech mixed with<br>
background noise, 16-kHz sampling.

<a id="P177"></a>

The scaling factor F shall be calculated for the noise file to which it is applied.

<a id="P178"></a>

Pre-processing for mixed content and music (16-kHz sampling)

<a id="P180"></a>

Figure 18: Pre-processing for WB mixed content and music condition files, 16-kHz sampling.

<a id="P181"></a>

General processing stages (16-kHz sampling)

<a id="P182"></a>

Direct conditions (16-kHz sampling)

<a id="P184"></a>

Figure 19: Processing of Direct condition (16-kHz sampling).

<a id="P185"></a>

Processing for MNRU reference conditions (16-kHz sampling)

<a id="P187"></a>

Figure 20: Processing of MNRU anchors at Y dB (16-kHz sampling).

<a id="P188"></a>

AMR-WB and G.722 conditions

<a id="P190"></a>

Figure 21: Processing by AMR-WB and G.722, the EID is bypassed for error-free conditions, (16-kHz sampling).

<a id="P191"></a>

AMR-WB encoder - G.718-IO / EVS-IO decoder conditions

<a id="P193"></a>

Figure 22: Processing by AMR-WB encoder and G.718 IO / EVS-IO decoder (16-kHz sampling).

<a id="P195"></a>

EVS-IO encoder - AMR-WB decoder conditions

<a id="P197"></a>

Figure 23: Processing by EVS-IO encoder – AMR-WB decoder, the EID is bypassed for error-free conditions, (16-kHz sampling).

<a id="P199"></a>

G.718, G.711.1 and G.722.1 conditions

<a id="P201"></a>

Figure 24: Processing by G.718 and G.722.1, the EID is bypassed for error-free conditions, (16-kHz sampling).

<a id="P202"></a>

ULBC Codec (16-kHz sampling) (non-JBM case)

<a id="P206"></a>

Figure 25: Processing by the ULBC. The EID is bypassed for error-free conditions.

<a id="P207"></a>

ULBC Codec (16-kHz sampling) (JBM case)

<a id="P211"></a>

Figure 26: Processing by the ULBC with jitter.

<a id="P214"></a>

Tandeming conditions (16-kHz sampling)

<a id="P216"></a>

Figure 12: Processing by a first codec tandemed with a second codec (16-kHz sampling).

<a id="P217"></a>

The two codec stages are each the complete general processing stage from an 16-kHz sampling input file to an 16-kHz sampling output file as outlined in 4.6.2. Please note that no encoder/decoder delay compensations are applied.

<a id="P218"></a>

Post-processing (16-kHz sampling)

<a id="P221"></a>

Figure 27: Post-processing of 16-kHz sampled files.

<a id="P222"></a>

Post-processing (16-kHz sampling) (ULBC JBM case)

<a id="P225"></a>

Figure 28: Post-processing of 16-kHz sampled files ULBC conditions with JBM.

<a id="P226"></a>

Note: Cutting tool should use astrip in the same as in the regular way.

<a id="P228"></a>

Processing for super-wideband conditions

<a id="P229"></a>

Pre-processing (32-kHz sampling)

<a id="P230"></a>

Pre-processing for 32-kHz sampling file generation

<a id="P232"></a>

Figure 29: Pre-processing for speech file generation, 32-kHz sampling.Pre-processing for SWB Clean speech conditions (32 kHz sampling)

<a id="P234"></a>

Figure 30: Pre-processing for SWB Clean speech condition files, (32 kHz sampling).

<a id="P235"></a>

Pre-processing for speech mixed with background noise (32 kHz sampling)

<a id="P238"></a>

Figure 31: Pre-processing for SWB speech mixed with<br>
background noise (32 kHz sampling).

<a id="P239"></a>

The scaling factor F shall be calculated for the noise file to which it is applied.

<a id="P240"></a>

Pre-processing for mixed content and music (32-kHz sampling)

<a id="P242"></a>

Figure 32: Pre-processing for SWB mixed content and music condition files, (32 kHz sampling).

<a id="P243"></a>

General processing stages (32 kHz)

<a id="P244"></a>

Direct conditions (32 kHz sampling)

<a id="P246"></a>

Figure 33: Processing of Direct condition (32-kHz sampling).

<a id="P247"></a>

Processing for MNRU reference conditions (32 kHz sampling)

<a id="P249"></a>

Figure 34: Processing of P.50 MNRU anchors at Y dB (32-kHz sampling).

<a id="P250"></a>

G.718 Annex B and G.722.1 Annex C conditions

<a id="P252"></a>

Figure 35: Processing by G718 Annex B and G.722.1C, the EID is bypassed for error-free conditions, (32 kHz).

<a id="P253"></a>

AMR-WB conditions in SWB

<a id="P256"></a>

Figure 36: Processing by AMR-WB conditions for SWB signals (32 kHz), the EID is bypassed for error-free conditions

<a id="P257"></a>

Note: The rate-change step from 16 to 32 kHz is required to apply the segmentation of in the same domain as the concatenation.

<a id="P258"></a>

AMR-WB+ conditions

<a id="P260"></a>

Figure 37: Processing by AMR-WB+ conditions

<a id="P261"></a>

(32kHz)

<a id="P262"></a>

G.719 conditions

<a id="P264"></a>

Figure 38: Processing by G.719, the EID is bypassed for error-free conditions, (32 kHz).

<a id="P265"></a>

ULBC Codec (32-kHz sampling) (non-JBM case)

<a id="P269"></a>

Figure 39: Processing by the ULBC. The EID is bypassed for error-free conditions.

<a id="P271"></a>

ULBC Codec (32-kHz sampling) (JBM case)

<a id="P275"></a>

Figure 40: Processing by the ULBC with jitter.

<a id="P277"></a>

Post-processing (32-kHz sampling)

<a id="P280"></a>

Figure 41: Post-processing of 32-kHz sampled files.

<a id="P282"></a>

Post-processing (32-kHz sampling) (ULBC JBM case)

<a id="P283"></a>

Figure 42: Post-processing of 32-kHz sampled files ULBC conditions with JBM.

<a id="P284"></a>

Note: Cutting tool should use astrip in the same as in the regular way.

<a id="P286"></a>

Processing for full-band conditions

<a id="P287"></a>

As described in Pdoc EVS-7c [1], section 4.8. The processing of the ULBC codec candidate follows the processing of the EVS codec.

<a id="P288"></a>

Editor’s note: If applicable. Otherwise, this section might become void.

<a id="P289"></a>

Processing for multi-bandwidth conditions

<a id="P290"></a>

As described in Pdoc EVS-7c [1], section 4.9. The processing of the ULBC codec candidate follows the processing of the EVS codec.

<a id="P291"></a>

Editor’s note: If applicable. Otherwise, this section might become void.

<a id="P293"></a>

Processing Modules

<a id="P294"></a>

General

<a id="P295"></a>

This section describes the modules that must be used in the processing of speech, mixed content and music material.

<a id="P296"></a>

Pre- and Post-Processing Operations

<a id="P297"></a>

General delay compensation for the STL filter tool

<a id="P298"></a>

All filtering steps include a delay compensation step. For preparing the delay compensation, samples of the preamble are added to the end of the input file before applying the filter step. After completion of the filtering step, the samples are to be removed from the beginning of the filtered file.

<a id="P299"></a>

Filtering operations

<a id="P300"></a>

HP50_48KHZ filtering

<a id="P301"></a>

To produce a 50Hz high pass filtered 48kHz sampling file use:

<a id="P302"></a>

filter.exe HP50_48KHZ Input48 Output48 960

<a id="P303"></a>

MSIN filtering

<a id="P304"></a>

To produce an MSIN high pass filtered 16kHz sampling file use:

<a id="P305"></a>

filter.exe MSIN Input16 Output16 320

<a id="P306"></a>

P.56 level adjustment

<a id="P307"></a>

P.56 active speech level adjustment

<a id="P308"></a>

To normalize the P.56 ASL of an 8-kHz sampling file to -26 dBov, use:

<a id="P309"></a>

sv56demo.exe -lev -26 -sf 8000 Input8 Output8 160

<a id="P310"></a>

To normalize the P.56 ASL of a 16-kHz sampled file to -26 dBov, use:

<a id="P311"></a>

sv56demo.exe -lev -26 -sf 16000 Input16 Output16 320

<a id="P312"></a>

To normalise the P.56 ASL level of a 32-kHz sampled file to -26 dBov, use:

<a id="P313"></a>

sv56demo.exe -lev -26 -sf 32000 Input32 Output32 640

<a id="P314"></a>

In addition to generate artificially mixed content, to normalise the P.56 ASL level of a 48-kHz sampled file to -26 dBov, use:

<a id="P315"></a>

sv56demo.exe -lev -26 -sf 48000 Input48 Output48 960

<a id="P316"></a>

RMS Level adjustment

<a id="P317"></a>

To normalise the r.m.s level of an 8-kHz sampled file, use:

<a id="P318"></a>

sv56demo.exe –rms –lev xx –sf 8000 Input8 Output8 160

<a id="P319"></a>

To normalise the r.m.s level of a 16-kHz sampled file, use:

<a id="P320"></a>

sv56demo.exe –rms –lev xx –sf 16000 Input16 Output16 320

<a id="P321"></a>

To normalise the r.m.s level of a 32-kHz sampled file, use:

<a id="P322"></a>

sv56demo.exe –rms –lev xx –sf 32000 Input32 Output32 640

<a id="P323"></a>

where xx is the desired level.

<a id="P324"></a>

In addition to generate artificially mixed content, to normalise the R.M.S level of a 48-kHz sampled file to -26 dBov, use:

<a id="P325"></a>

sv56demo.exe –rms -lev -26 -sf 48000 Input48 Output48 960

<a id="P326"></a>

RMS Level measuring

<a id="P327"></a>

To measure the r.m.s level of a MSIN filtered noise file, use:

<a id="P328"></a>

actlev.exe –rms –blk 160 –sf 8000 Noise8

<a id="P329"></a>

and extract the dBov value of the Long term energy (rms). This value shall be used as R (see Section 4.4).

<a id="P330"></a>

Scaling by Factor F

<a id="P331"></a>

To scale a noise signal at the sampling rate 8kHz, 16kHz or 32kHz by the Factor F use:

<a id="P332"></a>

scaldemo.exe -dB -gain F -bits 16 -round -nopremask -blk BBB Input Output

<a id="P333"></a>

where BBB is 160 for 8 kHz sampled files, 320 for 16 kHz sampled files and 640 for 32 kHz sampled files. The Factor F is to be determined as described in Section 4.5.

<a id="P334"></a>

Low/High level De-/Scaling

<a id="P335"></a>

In case the speech level shall be -26 dBov, this processing step shall be bypassed. Otherwise, the following gain needs to be applied to the signal:

<a id="T336"></a>

<a id="T336-R01"></a>
**T336-R01**

- <a id="T336-R01-C01"></a>列 1: Speech level
- <a id="T336-R01-C02"></a>列 2: Scaling
- <a id="T336-R01-C03"></a>列 3: Descaling

<a id="T336-R02"></a>
**T336-R02**

- <a id="T336-R02-C01"></a>列 1: -16 dBov
- <a id="T336-R02-C02"></a>列 2: G=10
- <a id="T336-R02-C03"></a>列 3: G=-10

<a id="T336-R03"></a>
**T336-R03**

- <a id="T336-R03-C01"></a>列 1: -36 dBov
- <a id="T336-R03-C02"></a>列 2: G=-10
- <a id="T336-R03-C03"></a>列 3: G=10

<a id="P338"></a>

To apply the scaling operation with the gain G, use:

<a id="P339"></a>

scaldemo.exe -dB -gain G -bits 16 -round –nopremask -blk BBB Input Ouput

<a id="P340"></a>

where BBB is 160 for 8 kHz sampled files, 320 for 16 kHz sampled files and 640 for 32 kHz sampled files.

<a id="P341"></a>

Summation of speech and noise files

<a id="P342"></a>

Summation of a speech and a noise file

<a id="P343"></a>

To add files in the same sampling frequency (8, 16 or 32 kHz), e.g., to produce a 32 kHz speech file mixed with noise file called output32 by summing a 32 kHz speech file called input32 and a 32 kHz noise file called noise32, use:

<a id="P344"></a>

oper.exe –size 0 1 Input32 + 1 Noise32 0 Output32 BBB

<a id="P345"></a>

where BBB is 160 for 8 kHz sampled files, 320 for 16 kHz sampled files and 640 for 32 kHz sampled files.

<a id="P346"></a>

File concatenation

<a id="P347"></a>

To concatenate files, the concat command is used:

<a id="P348"></a>

concat.exe –undo undo_concat.txt file1 [file2 file3 …] catfile

<a id="P349"></a>

Where file1, file2, … are the files to be concatenated and catfile is the concatenated file. The undo_concat.txt contains the parameters for segmentation.

<a id="P351"></a>

In case additional silence sections needs to be inserted before concatenation, use the following for all input files

<a id="P352"></a>

concat.exe silence fileX silence tmp_file

<a id="P353"></a>

copy tmp_file fileX

<a id="P354"></a>

where the silence file contains 0.2 sec of digital silence and fileX is one of the input files.

<a id="P356"></a>

Audio format conversion

<a id="P357"></a>

PCM to WAV conversion

<a id="P358"></a>

To convert a 32kHz sampled PCM file to a WAV file for AMR-WB+, use:

<a id="P359"></a>

CopyAudio.exe -F WAVE-NOEX -P integer16,0,32000,native,1,default -I “” input32 output32.wav

<a id="P360"></a>

WAV to PCM conversion

<a id="P361"></a>

To convert a WAV file to a 32kHz sampled PCM file for AMR-WB+, use:

<a id="P362"></a>

CopyAudio.exe -F noheader -D integer16 input32.wav output32

<a id="P363"></a>

Sampling Rate changes

<a id="P364"></a>

Rate-change from 48- to 8-kHz sampling

<a id="P365"></a>

To produce an 8-kHz sampling file from a 48-kHz sampling file, use:

<a id="P366"></a>

filter.exe –down SHQ3 input48 tmp16 960

<a id="P367"></a>

filter.exe –down SHQ2 tmp16 output8 320

<a id="P368"></a>

Rate-change from 48- to 16-kHz sampling

<a id="P369"></a>

To produce a 16-kHz sampling file from a 48-kHz sampling file, use:

<a id="P370"></a>

filter.exe –down SHQ3 input48 output16 960

<a id="P371"></a>

Rate-change from 48- to 32-kHz sampling

<a id="P372"></a>

To produce a 32 kHz sampling file from a 48 kHz sampling file, use:

<a id="P373"></a>

filter.exe –up SHQ2 input48 tmp96 960

<a id="P374"></a>

filter.exe –down SHQ3 tmp96 output32 1920

<a id="P375"></a>

Rate-change from 8- to 48-kHz sampling

<a id="P376"></a>

To produce a 48 kHz sampling file from an 8 kHz sampling file, use:

<a id="P377"></a>

filter.exe –up SHQ2 input8 tmp16 160

<a id="P378"></a>

filter.exe –up SHQ3 tmp16 output48 320

<a id="P379"></a>

Rate-change from 16- to 48-kHz sampling

<a id="P380"></a>

To produce a 48 kHz sampling file from a 16 kHz sampling file, use:

<a id="P381"></a>

filter.exe –up SHQ3 input16 output48 320

<a id="P382"></a>

Rate-change from 32- to 48-kHz sampling

<a id="P383"></a>

To produce a 48 kHz sampling file from a 32 kHz sampling file, use:

<a id="P384"></a>

filter.exe –up SHQ3 input32 tmp96 640

<a id="P385"></a>

filter.exe –down SHQ2 tmp96 output48 1920

<a id="P386"></a>

Rate-change from 32- to 16-kHz sampling

<a id="P387"></a>

To produce a 16 kHz sampling file from a 32 kHz sampling file, use:

<a id="P388"></a>

filter.exe –down SHQ2 input32 output16 640

<a id="P389"></a>

Rate-change from 32- to 8-kHz sampling

<a id="P390"></a>

To produce a 8 kHz sampling file from a 32 kHz sampling file, use:

<a id="P391"></a>

filter.exe –down SHQ2 input32 output16 640

<a id="P392"></a>

filter.exe –down SHQ2 output16 output8 320

<a id="P393"></a>

Rate-change from 16- to 32-kHz sampling

<a id="P394"></a>

To produce a 32 kHz sampling file from a 16 kHz sampling file, use:

<a id="P395"></a>

filter.exe –up SHQ2 input16 output32 320

<a id="P396"></a>

Rate-change from 8- to 32-kHz sampling

<a id="P397"></a>

To produce a 32 kHz sampling file from a 8 kHz sampling file, use:

<a id="P398"></a>

filter.exe –up SHQ2 input8 output16 160

<a id="P399"></a>

filter.exe –up SHQ2 output16 output32 320

<a id="P400"></a>

Rate-change from 16- to 8-kHz sampling

<a id="P401"></a>

To produce a 8 kHz sampling file from a 16 kHz sampling file, use:

<a id="P402"></a>

filter.exe –down SHQ2 input16 output8 320

<a id="P403"></a>

Windowing and segmentation

<a id="P404"></a>

Segmentation for NB conditions

<a id="P405"></a>

To extract an m sample long file beginning at sample s from a 8 kHz single channel concatenated file, use:

<a id="P406"></a>

astrip.exe –sample –smooth –wlen 800 –start s -n m input8 output8

<a id="P407"></a>

Segmentation for WB conditions

<a id="P408"></a>

To extract an m sample long file beginning at sample s from a 16 kHz single channel concatenated file, use:

<a id="P409"></a>

astrip.exe –sample –smooth –wlen 1600 –start s -n m input16 output16

<a id="P410"></a>

Segmentation for SWB conditions

<a id="P411"></a>

To extract an m sample long file beginning at sample s from a 32 kHz single channel concatenated file, use:

<a id="P412"></a>

astrip.exe –sample –smooth –wlen 3200 –start s -n m input32 output32

<a id="P413"></a>

Initial windowing

<a id="P414"></a>

To apply the initial windowing of a 48kHz input speech or music file, use:

<a id="P415"></a>

astrip.exe –sample –smooth –wlen 4800 –start s -n m input48 output48

<a id="P416"></a>

Bit conversion

<a id="P417"></a>

Conversion from 16 to 13 bits

<a id="P418"></a>

To convert an 8kHz narrowband signal from a 16 bit representation to a 13 bit representation including rounding, use:

<a id="P419"></a>

scaldemo.exe -lin -gain 1 -bits 13 -round -nopremask -blk 160 input8 output8

<a id="P420"></a>

Conversion from 16 to 14 bits

<a id="P421"></a>

To convert a 16kHz wideband signal from a 16 bit representation to a 14 bit representation including rounding, use:

<a id="P422"></a>

scaldemo.exe -lin -gain 1 -bits 14 -round -nopremask -blk 320 input16 output16

<a id="P424"></a>

Processing

<a id="P425"></a>

This section describes the input file and channel operations processing that must be used in the preparation of audio material.

<a id="P426"></a>

MNRU reference conditions

<a id="P427"></a>

To generate an MNRU reference at XXX dB for a file Input8, use:

<a id="P428"></a>

mnrudemo.exe –Q XXX Input8 Output8 160

<a id="P429"></a>

To generate an MNRU reference at XXX dB for a file Input16, use:

<a id="P430"></a>

mnrudemo.exe –Q XXX Input16 Output16 320

<a id="P431"></a>

To generate a P.50 MNRU reference at XXX dB for a file Input48, use:

<a id="P432"></a>

p50mnru.exe Input48 Output48 XXX M

<a id="P433"></a>

Note that the P.50 MNRU processing for SWB conditions requires rate-change steps between 32kHz and 48kHz.

<a id="P434"></a>

Reference codecs for Narrowband conditions

<a id="P435"></a>

AMR

<a id="P436"></a>

To process a file Input8 through the AMR codec at XXX kbit/s, use:

<a id="P437"></a>

amr_cod_vad2.exe [-dtx] BBB Input8 bitstream

<a id="P438"></a>

amr_dec.exe bitstream Output8

<a id="P439"></a>

where BBB is the bitrate mode corresponding to XXX as given in the following table.

<a id="T440"></a>

<a id="T440-R01"></a>
**T440-R01**

- <a id="T440-R01-C01"></a>列 1: XXX [kbit/s]
- <a id="T440-R01-C02"></a>列 2: 4.75
- <a id="T440-R01-C03"></a>列 3: 7.4
- <a id="T440-R01-C04"></a>列 4: 7.95
- <a id="T440-R01-C05"></a>列 5: 10.2
- <a id="T440-R01-C06"></a>列 6: 12.2

<a id="T440-R02"></a>
**T440-R02**

- <a id="T440-R02-C01"></a>列 1: BBB
- <a id="T440-R02-C02"></a>列 2: MR475
- <a id="T440-R02-C03"></a>列 3: MR74
- <a id="T440-R02-C04"></a>列 4: MR795
- <a id="T440-R02-C05"></a>列 5: MR102
- <a id="T440-R02-C06"></a>列 6: MR122

<a id="P441"></a>

Note that AMR operates at 20 ms frame length and has encoder and decoder delay of 5 ms and 0 ms, respectively

<a id="P442"></a>

G.711

<a id="P443"></a>

To process a file Input8 through the G.711codec with 20 ms blocks, use:

<a id="P444"></a>

g711demo.exe LAW lili Input8 Output8 160

<a id="P445"></a>

where LAW is A for A-law and u for u-law. Note that G.711 does not have algorithmic delay.

<a id="P446"></a>

G.718 narrowband mode

<a id="P447"></a>

To process a file Input8 through the G.718 codec in narrowband mode at XXX bit/s, use:

<a id="P448"></a>

g718_enc.exe [-dtx 8] –maxBR XXX 8 Input8 bitstream

<a id="P449"></a>

g718_dec.exe -disabled_NG –maxBR XXX 8 bitstream Output8

<a id="P450"></a>

where XXX is either 8000 or 12000. Note that G.718 operates at 20 ms frame length and has an algorithmic delay of 33.875 ms, when operating on narrowband input and in low-delay mode.

<a id="P451"></a>

Reference codecs for Wideband conditions

<a id="P452"></a>

AMR-WB

<a id="P453"></a>

To process a file Input16 through the AMR-WB codec at XXX kbit/s, use ITU-T G.722.2 as:

<a id="P454"></a>

amrwb_cod.exe [–dtx] –itu BBB Input16 bitstream

<a id="P455"></a>

amrwb_dec.exe -itu bitstream Output16

<a id="P456"></a>

where BBB is the bitrate mode corresponding to XXX as given in the following table.

<a id="T457"></a>

<a id="T457-R01"></a>
**T457-R01**

- <a id="T457-R01-C01"></a>列 1: XXX [kbit/s]
- <a id="T457-R01-C02"></a>列 2: 6.6
- <a id="T457-R01-C03"></a>列 3: 8.85
- <a id="T457-R01-C04"></a>列 4: 12.65
- <a id="T457-R01-C05"></a>列 5: 14.25
- <a id="T457-R01-C06"></a>列 6: 15.85
- <a id="T457-R01-C07"></a>列 7: 18.25
- <a id="T457-R01-C08"></a>列 8: 19.85
- <a id="T457-R01-C09"></a>列 9: 23.05
- <a id="T457-R01-C10"></a>列 10: 23.85

<a id="T457-R02"></a>
**T457-R02**

- <a id="T457-R02-C01"></a>列 1: BBB
- <a id="T457-R02-C02"></a>列 2: 0
- <a id="T457-R02-C03"></a>列 3: 1
- <a id="T457-R02-C04"></a>列 4: 2
- <a id="T457-R02-C05"></a>列 5: 3
- <a id="T457-R02-C06"></a>列 6: 4
- <a id="T457-R02-C07"></a>列 7: 5
- <a id="T457-R02-C08"></a>列 8: 6
- <a id="T457-R02-C09"></a>列 9: 7
- <a id="T457-R02-C10"></a>列 10: 8

<a id="P458"></a>

Note that AMR-WB operates at 20 ms frame length and has encoder and decoder delay of 5 ms and 0.9375 ms, respectively.

<a id="P459"></a>

AMR-WB encoder - G.718 IO decoder

<a id="P460"></a>

To process a file Input16 through the AMR-WB encoder and the G.718 IO decoder at XXX bit/s, use ITU-T G.722.2 as:

<a id="P461"></a>

amrwb_cod.exe [–dtx] –itu BBB Input16 bitstream

<a id="P462"></a>

where BBB is described in 5.2.3.1. For decoding call

<a id="P463"></a>

g718_dec.exe -disabled_NG -IO_G722_2 –maxBR YYY 16 bitstream Output16

<a id="P464"></a>

where YYY is the bitrate mode corresponding to BBB as given in the following table.

<a id="T465"></a>

<a id="T465-R01"></a>
**T465-R01**

- <a id="T465-R01-C01"></a>列 1: BBB
- <a id="T465-R01-C02"></a>列 2: 1
- <a id="T465-R01-C03"></a>列 3: 2
- <a id="T465-R01-C04"></a>列 4: 3
- <a id="T465-R01-C05"></a>列 5: 4
- <a id="T465-R01-C06"></a>列 6: 5
- <a id="T465-R01-C07"></a>列 7: 6
- <a id="T465-R01-C08"></a>列 8: 7
- <a id="T465-R01-C09"></a>列 9: 8

<a id="T465-R02"></a>
**T465-R02**

- <a id="T465-R02-C01"></a>列 1: YYY
- <a id="T465-R02-C02"></a>列 2: 8850
- <a id="T465-R02-C03"></a>列 3: 12650
- <a id="T465-R02-C04"></a>列 4: 14250
- <a id="T465-R02-C05"></a>列 5: 15850
- <a id="T465-R02-C06"></a>列 6: 18250
- <a id="T465-R02-C07"></a>列 7: 19850
- <a id="T465-R02-C08"></a>列 8: 23050
- <a id="T465-R02-C09"></a>列 9: 23850

<a id="P467"></a>

Note that AMR-WB encoder operates at 20 ms frame length and has a delay of 5 ms. G.718 IO decoder operates at 20 ms frame length and has a delay of 1.9375 ms. when operating on wideband input and in low-delay mode.

<a id="P468"></a>

G.718

<a id="P469"></a>

To process a file Input16 through the G.718 codec at XXX bit/s, use:

<a id="P470"></a>

g718_enc.exe –maxBR XXX 16 Input16 bitstream

<a id="P471"></a>

g718_dec.exe -disabled_NG –maxBR XXX 16 bitstream Output16

<a id="P472"></a>

where XXX is 32000.

<a id="P473"></a>

Note that G.718 operates at 20 ms frame length and has an overall algorithmic delay of 42.875 ms, when operating on wideband input.

<a id="P474"></a>

G.722

<a id="P475"></a>

To process a file Input16 through the G.722 codec at XXX kbit/s using 20 ms block size, use:

<a id="P476"></a>

encg722.exe –fsize 320 –mode XXX Input16 bitstream

<a id="P477"></a>

decg722.exe -fsize 320 –mode XXX bitstream Output16

<a id="P478"></a>

where XXX is either 56 or 64. Note that G.722 operates at 20 ms frame length and has an overall algorithmic delay of 1.625 ms.

<a id="P479"></a>

G.722.1

<a id="P480"></a>

To process a file Input16 through the G.722.1 codec at XXX bit/s, use:

<a id="P481"></a>

g7221_enc.exe 1 Input16 bitstream XXX 7000

<a id="P482"></a>

g7221_dec.exe 1 bitstream Output16 XXX 7000

<a id="P483"></a>

where XXX is one of (24000, 32000). Note that G.722.1 operates at 20 ms frame length and has an overall algorithmic delay of 40 ms.

<a id="P484"></a>

G.711.1

<a id="P485"></a>

To process a file Input16 through the G.711.1 codec at 80 bit/s, use:

<a id="P486"></a>

g7111_enc.exe –mode 3 A Input16 bitstream

<a id="P487"></a>

g7111_dec.exe A –mode 3 bitstream Output16

<a id="P488"></a>

Note that G.711.1 operates at 20 ms frame length and has an overall algorithmic delay of 11.875 ms.

<a id="P489"></a>

Reference codecs for Superwideband conditions

<a id="P490"></a>

AMR-WB+

<a id="P491"></a>

To process a file Input32 through the AMR-WB+ codec at XXX kbit/s, use:

<a id="P492"></a>

amrwbplus_cod.exe –rate XXX –ff raw –if Input32.wav –of bitstream

<a id="P493"></a>

amrwbplus_dec.exe –ff raw –if bitstream –fs 32000 –mono –of Output32.wav

<a id="P494"></a>

where XXX is one of 9.75, 12, 16. Note that AMR-WB+ has an overall algorithmic delay of approx. 72/68 ms at 9.75/12kbps.

<a id="P495"></a>

G.718 Annex B

<a id="P496"></a>

To process a file Input32 through the G.718 Annex B codec at 36 kbit/s, use:

<a id="P497"></a>

g718_enc.exe –maxBR 36000 32 Input32 bitstream

<a id="P498"></a>

g718_dec.exe –disabled_NG 32 bitstream Output32

<a id="P499"></a>

Note that G.718 Annex B operates at 20 ms frame length and has an overall algorithmic delay of 49.625 ms.

<a id="P500"></a>

G.719

<a id="P501"></a>

To process a file Input48 through the G.719 codec at XXX bit/s, use:

<a id="P502"></a>

g719_enc.exe –r XXX –i Input48 -o bitstream

<a id="P503"></a>

g719_dec.exe –i bitstream -o Output48

<a id="P504"></a>

where XXX is one of 32000, 48000, 56000, 64000, 80000, 96000, 128000. Note that G.719 operates at 20 ms frame length and has an overall algorithmic delay of 40 ms. G.719 operates at 48kHz which implies resampling steps from and to 32kHz.

<a id="P505"></a>

G.722.1 Annex C

<a id="P506"></a>

To process a file Input32 through the G.722.1 Annex C codec at XXX bit/s, use:

<a id="P507"></a>

g7221_enc.exe 1 Input32 bitstream XXX 14000

<a id="P508"></a>

g7221_dec.exe 1 bitstream Output32 XXX 14000

<a id="P509"></a>

where XXX is one of 24000, 32000 or 48000. Note that G.722.1 Annex C operates at 20 ms frame length and has an overall algorithmic delay of 40 ms.

<a id="P510"></a>

Delay compensation for reference conditions

<a id="P511"></a>

Details on the delay compensation implementation can be found in Annex B.5.

<a id="P512"></a>

ULBC operation (non JBM case)

<a id="P513"></a>

To process a file Input8 through the ULBC  codec at XXX bit/s, use:

<a id="P514"></a>

ULBC_cod.exe [-dtx] [-no_delay_cmp] XXX/SWF 8 Input8 bitstream

<a id="P515"></a>

ULBC_dec.exe [-no_delay_cmp] 8 bitstream Output8

<a id="P516"></a>

where XXX is one of 5900, 7200, 8000, 9600 or 13200. For rate switching operation, XXX is replaced by a switching file (SWF).

<a id="P517"></a>

To process a file Input16 through the ULBC codec at XXX bit/s, use:

<a id="P518"></a>

ULBC_cod.exe [-dtx] [-no_delay_cmp] XXX/SWF 16 Input16 bitstream

<a id="P519"></a>

ULBC_dec.exe [-no_delay_cmp] 16 bitstream Output16

<a id="P520"></a>

where XXX is one of 5900, 7200, 8000, 9600, 13200, 16400, 24400, 32000, 48000, 64000, 96000 for testing non-IO modes or 6600, 8850, 12650, 14250, 15850, 18250, 19850, 23050, 23850 for testing AMR-WB IO modes. For rate switching operation, XXX is replaced by a switching file (SWF).

<a id="P521"></a>

To process a file Input32 through the ULBC codec at XXX bit/s, use:

<a id="P522"></a>

ULBC_cod.exe [-dtx] [-no_delay_cmp] XXX/SWF 32 Input32 bitstream

<a id="P523"></a>

ULBC_dec.exe [-no_delay_cmp] 32 bitstream Output32

<a id="P524"></a>

where XXX is one of 13200, 16400, 24400, 32000, 48000, 64000, 96000, 128000. For rate switching operation, XXX is replaced by a switching file (SWF).

<a id="P525"></a>

To process a file Input48 through the ULBC codec at XXX bit/s, use:

<a id="P526"></a>

ULBC_cod.exe [-dtx] [-no_delay_cmp] –max_band FB XXX/SWF 48 Input48 bitstream

<a id="P527"></a>

ULBC_dec.exe [-no_delay_cmp] 48 bitstream Output48

<a id="P528"></a>

where XXX is one of 16400, 24400, 32000, 48000, 64000, 96000, 128000. For rate switching operation, XXX is replaced by a switching file (SWF).

<a id="P529"></a>

The switching file consists of XXX values indicating the bit rate for each frame in bit/s. These values are stored in binary format using 4 bytes per value.

<a id="P530"></a>

Note: ULBC encoder and decoder shall provide delay compensated output files except if used for tandem conditions, where the option “-no_delay_cmp” is to be enabled.

<a id="P531"></a>

ULBC operation (JBM case)

<a id="P532"></a>

To process a file Input8 through the ULBC codec at XXX bit/s, use:

<a id="P533"></a>

ULBC_cod.exe [-dtx] XXX 8 Input8 bitstream

<a id="P534"></a>

ULBC_dec.exe –Tracefile tracefile_dec –VOIP 8 netsimoutput Output8

<a id="P535"></a>

where XXX is 9600.

<a id="P536"></a>

To process a file Input16 through the ULBC codec at XXX bit/s, use:

<a id="P537"></a>

ULBC_cod.exe [-dtx] XXX 16 Input16 bitstream

<a id="P538"></a>

ULBC_dec.exe –Tracefile tracefile_dec –VOIP 16 netsimoutput Output16

<a id="P539"></a>

where XXX is 13200.

<a id="P540"></a>

To process a file Input32 through the ULBC codec at XXX bit/s, use:

<a id="P541"></a>

ULBC_cod.exe [-dtx] XXX 32 Input32 bitstream

<a id="P542"></a>

ULBC_dec.exe –Tracefile tracefile_dec –VOIP 32 netsimoutput Output32

<a id="P543"></a>

where XXX is one of 13200 or 24400.

<a id="P544"></a>

The tracefile_dec is the tracefile written by the decoder and netsimoutput is the RTP+G.192 input file written by the network simulator.

<a id="P545"></a>

ULBC operation (Channel-aware case)

<a id="P546"></a>

To process a file Input16 through the ULBC codec at XXX bit/s using the channel-aware mode, use:

<a id="P547"></a>

ULBC_cod.exe [-dtx] –rf p o XXX 16 Input16 bitstream

<a id="P548"></a>

ULBC_dec.exe –Tracefile tracefile_dec –VOIP 16 netsimoutput Output16

<a id="P549"></a>

where XXX is 13200.

<a id="P550"></a>

To process a file Input32 through the ULBC codec at XXX bit/s, use:

<a id="P551"></a>

ULBC_cod.exe [-dtx] –rf p o XXX 32 Input32 bitstream

<a id="P552"></a>

ULBC_dec.exe –Tracefile tracefile_dec –VOIP 32 netsimoutput Output32

<a id="P553"></a>

where XXX is  13200.

<a id="P554"></a>

p is a frame erasure rate indicator for the encoder for channel-awareness, having the following values: LO for FER<5% or HI for FER>=5%, and o is the offset (in number of frames) of the partial-redundant frame. p and o are optional parameters with default set to p=HI and o=3. Characterization testing of channel-aware modes is performed with the parameters described in the test plan [X].

<a id="P555"></a>

The tracefile_dec is the tracefile written by the decoder and netsimoutput is the RTP+G.192 input file written by the network simulator.

<a id="P556"></a>

Tandeming conditions

<a id="P557"></a>

To process a file Input8 through a first codec operating in 8-kHz followed by a second codec operating in 8-kHz the respective processing steps of the first codec and the second code are chained. The output file Output8 after the first codec will be the input file Input8 for the second codec.

<a id="P558"></a>

To process a file Input16 through a first codec operating in 16-khz followed by a second codec operating in 16-kHz the respective processing steps of the first codec and the second code are chained. The output file Output16 after the first codec will be the input file Input16 for the second codec.

<a id="P559"></a>

In case tandeming of codecs with different sampling rates is processed the processing for multi-bandwidth conditions is performed.

<a id="P560"></a>

For tandeming conditions the delay-alignment of the involved codecs is disabled and no delay compensation for the codecs is performed. For the ULBC encoder the parameter -no_delay_cmp is added to the encoder and decoder command line, otherwise the .

<a id="P561"></a>

Editor’s note: Typo in EVS 7c [1], needs to be fixed.

<a id="P562"></a>

Encoder and decoder ULBC executable requirements

<a id="P563"></a>

The executables shall be compatible to [Win32].

<a id="P564"></a>

Error Insertion (EID)

<a id="P565"></a>

For the conditions where random frame erasures are desired, frame erasure patterns are applied to the bitstream using tools from the ITU-T STL2009 library.

<a id="P566"></a>

Frame error tool

<a id="P567"></a>

For the AMR codec, the following processing shall be used:

<a id="P568"></a>

eid-amr.exe amrbsin ep.g192 amrbsout

<a id="P569"></a>

where:

<a id="P570"></a>

amrbsin is the AMR input bit stream

<a id="P571"></a>

ep.g192 is the error pattern file

<a id="P572"></a>

amrbsout is the AMR output bit stream

<a id="P573"></a>

For the G.711 A/µ-law, the following processing shall be used:

<a id="P574"></a>

eid-int –ep g192 –factor 2 ep.g192 ep10.g192

<a id="P575"></a>

g711iplc.exe ep10.g192 input.8k ouput.8k

<a id="P576"></a>

where:

<a id="P577"></a>

ep.g192 is the error pattern file assuming 20ms frames and ep10.g192 is the error pattern file for the g711iplc tool where all entries are doubled to take the 10ms frame grid of the g711iplc tool into account.

<a id="P578"></a>

input.8k is the G.711 decoded output file

<a id="P579"></a>

output.8k is the G.711 decoded output file with packet loss concealment

<a id="P581"></a>

For all other reference codecs and ULBC, the following processing shall be used:

<a id="P582"></a>

eid-xor.exe –vbr –fer g192bsin ep.g192 g192bsout

<a id="P583"></a>

where:

<a id="P584"></a>

g192bsin is the input bit stream

<a id="P585"></a>

ep.g192 is the error pattern file

<a id="P586"></a>

g192bsout is the output bit stream

<a id="P587"></a>

Pattern generation

<a id="P588"></a>

Before generating error patterns, the sta file of the gen-patt tool needs to be initialized as specified in Annex C.4.

<a id="P589"></a>

The error patterns used are generated using the gen-patt tool as follows:

<a id="P590"></a>

gen-patt.exe -tailstat -fer -g192 -gamma 0 -rate XXX -tol 0.001      -reset -n LENGTH -start 501 ep.g192

<a id="P591"></a>

where XXX is the required erasure rate, i.e. 0.03 for 3% and 0.06 for 6% FER.

<a id="P592"></a>

Different error patterns should be generated for each experiment. For all speech experiments the parameter LENGTH is exactly 12500,  assuming a 10 sec preamble and 6 talker with 5 samples of 8 sec length each. For the mixed/music experiments, this parameter needs to be adapted to the length of the concatenated sequence.

<a id="P593"></a>

For the AMR-WB encoder conditions with enabled DTX, the error pattern needs to be repeated due to the repetition of the input sequence. To generate an EPF with repetition, use:

<a id="P594"></a>

concate.exe ep.g192 ep.g192 ep.repeated.g192

<a id="P596"></a>

Derive EPFs from jitter profiles

<a id="P597"></a>

To derive an error pattern file from one of the delay and error profiles 1, 2, or 3 given in the MTSI specification, use:

<a id="P598"></a>

dlyerr_2_errpat.exe –d 200 –f 1 –w –s YYY –i dly_err_profile_XXX.dat -o f_profile_XXX.g192

<a id="P599"></a>

where XXX is one of 1, 2, or 3, and YYY is the random offset into the profile.

<a id="P600"></a>

To derive an error pattern file from one of the delay and error profiles 4 or 6 given in the MTSI specification, use:

<a id="P601"></a>

dlyerr_2_errpat.exe –l 1 –f 1 –w –s YYY –i dly_err_profile_XXX.dat -o f_profile_XXX.g192

<a id="P602"></a>

where XXX is one of 4 or 6, and YYY is the random offset into the profile.

<a id="P603"></a>

To derive an error pattern file from one of the delay and error profile 5 given in the MTSI specification, use:

<a id="P604"></a>

dlyerr_2_errpat.exe –l 1 –f 2 –w –s YYY –i dly_err_profile_5.dat -o f_profile_5.g192

<a id="P605"></a>

where YYY is the random offset into the profile.

<a id="P606"></a>

To derive an error pattern file from one of the delay and error profiles 7, 8, or 9 use:

<a id="P607"></a>

dlyerr_2_errpat.exe –d 200 –L 8000 –f 1 –w –s YYY –i dly_err_profile_XXX.dat -o f_profile_XXX.g192

<a id="P608"></a>

where XXX is one of 7, 8, or 9  and YYY is the random offset into the profile.

<a id="P609"></a>

To derive an error pattern file from the delay and error profile 10 use:

<a id="P610"></a>

dlyerr_2_errpat.exe –l 1 –L 8000 –f 1 –w –s YYY –i dly_err_profile_10.dat -o f_profile_10.g192

<a id="P611"></a>

where YYY is the random offset into the profile.

<a id="P612"></a>

Rate switching profile generation

<a id="P613"></a>

To generate rate switching profiles for ULBC conditions, use

<a id="P614"></a>

gen-rate-profile.exe –layers B1,B2,…,Bx SWF 10 B1 LENGTH SEEDx

<a id="P615"></a>

where B1,B2,…,Bx are all bit rates starting from the lowest one (B1) up to the highest one (Bx). The following list shows all possible rates for the ULBC codec:

<a id="P616"></a>

no AMR-WB IO: 7200, 8000, 9600, 13200,  24400, 32000, 48000, 64000, 96000, 128000

<a id="P617"></a>

AMR-WB IO: 6600, 8850, 12650, 14250, 15850, 18250, 19850, 23050, 23850

<a id="P618"></a>

SWF is the file name and SEEDx is a random seed, see C.3. For mixed/music experiments, the parameter LENGTH needs to be adapted to the length of the concatenated sequence. For speech experiments, the parameter LENGTH is exactly 12500.

<a id="P619"></a>

To generate for instance the rate switching profile for a non-IO ULBC condition from 9.6kbps to 64kbps, use

<a id="P620"></a>

gen-rate-profile.exe –layers 9600,13200,16400,24400,32000,48000,64000 SWF 10 9600 LENGTH SEEDx

<a id="P621"></a>

To generate a rate switching profiles consisting only of AMR-WB IO modes, use the Bx rates listed under AMR-WB IO. Mixing the non-IO and IO rates is required in case WB non-IO / IO switching is tested, e.g.to process a switched ULBC non-IO / IO condition from 8.85kbps to 13.2kbps, use

<a id="P622"></a>

gen-rate-profile.exe –layers 8850,9600,12650,13200 SWF 10 8850 LENGTH SEEDx

<a id="P623"></a>

Note: Case B) AMR-WB encoder side rate switching is not supported so far

<a id="P624"></a>

Network simulator for packet jitter generation

<a id="P625"></a>

To simulate packet jitter for ULBC conditions, use

<a id="P626"></a>

network_simulator.exe dly_error_profile_x.dat ULBCbitstream netsimoutput tracefile_sim nFramesPerPacket [offset]

<a id="P627"></a>

where

<a id="P628"></a>

dly_error_profile_x.dat is the MTSI delay and error profile number x

<a id="P629"></a>

ULBCbitstream is the G.192 input bitstream file name

<a id="P630"></a>

netsimoutput is the RTP+G.192 output file name

<a id="P631"></a>

tracefile_sim is the trace output file name of the network simulator

<a id="P632"></a>

nFramesPerPacket is the number of frames per packet (1, 2)

<a id="P633"></a>

offset is the shift/offset in delay and error profile in frames (default: 0)

<a id="P635"></a>

Cutting Tool for JBM tests

<a id="P636"></a>

To trim parameters for the file segmentation after de-jittering, use

<a id="P637"></a>

jbmtrim.exe –file Fs tracefile_dec undo_concat.txt undo_concat_trim.txt

<a id="P638"></a>

where

<a id="P639"></a>

file is to enable the undo_concat.txt support

<a id="P640"></a>

Fs is the operating sampling rate, i.e. 8000, 16000 or 32000

<a id="P641"></a>

tracefile_dec is the trace output file of the ULBC decoder

<a id="P642"></a>

undo_concat.txt is the file name where parameters for segmentation are stored

<a id="P643"></a>

undo_concat_trim.txt is the file name containing the corrected parameters for segmentation using the astrip tool

<a id="P645"></a>

Editor’s note: The error patterns will need to be adapted to the ULBC and reference codecs, in particular if they use different frame length.

<a id="P646"></a>

Processing objective performance requirements

<a id="P647"></a>

Databases for objective evaluation

<a id="P648"></a>

A dataset for objective evaluation is to be defined, consisting of:

<a id="P649"></a>

Clean speech material;

<a id="P650"></a>

Noisy speech material generated by mixing speech with representative background noises;

<a id="P652"></a>

As a baseline ITU-T P.501 [2] is used for the speech. Noise material is TBD.

<a id="P654"></a>

Editor’s note: Noise material might be proposed by 3GPP members, as long as it is donated for the ULBC work and under constraint that it is not allowed to use for the training of candidate codecs.

<a id="P656"></a>

Active Frame Ratio (AFR)

<a id="P657"></a>

…

<a id="P658"></a>

Gain measuring of active frames and inactive frames

<a id="P659"></a>

…

<a id="P661"></a>

Acknowledgements

<a id="P662"></a>

[The Editor thanks all companies for contributing to this document and especially for their help developing the processing scripts and providing the relevant executables.]

<a id="P663"></a>

References

<a id="P664"></a>

[1]    3GPP S4-141392, “EVS Permanent Document EVS-7c: Processing functions for characterization Phase v1.1.0”.

<a id="P665"></a>

[2]    ITU-T P.501 (04/25) Annex C (https://www.itu.int/myworkspace/t-signals/vectors?val=17, https://www.itu.int/rec/T-REC-P.501-202504-I/en)

<a id="P667"></a>

Editor’s note: to be added.

<a id="P668"></a>

]

## 原文批注与定位

- 批注 40：Changed “EVS” to “CuT”.；位置：P205, unlocated
- 批注 41：Changed “EVS” to “CuT”.；位置：P210, unlocated
- 批注 62：Changed “EVS” to “CuT”；位置：P268, unlocated
- 批注 63：Changed “EVS” to “CuT”；位置：P274, unlocated

**原文页眉：** 3GPP TSG SA WG4 Audio SWG AH        S4aA260181<br>        Shanghai, China, September 28-30, 2026<br>    August 24-28, 2026
