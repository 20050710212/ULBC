# S4aA260144 — 原文 Markdown（当前修订文本）

> 来源：`S4aA260144 ULBC Design Constraints.docx`。仅显示当前修订文本，保留方括号、直接格式删除线、批注和单元格合并元数据。接受修订用于读取当前文字，不代表所有条款已定案。定位标记为提取索引，不是原文条款号。

<a id="P000"></a>

Source:    Apple Inc.

<a id="P001"></a>

Title:    [ULBC-MED] ULBC Design Constraints

<a id="P002"></a>

Spec:    ULBC-4 Design Constraints

<a id="P003"></a>

Document for:    Discussion and Agreement

<a id="P004"></a>

Agenda item:    4.4

<a id="P007"></a>

## 1.    Discussion

<a id="P008"></a>

Given the envisioned application scenarios of ULBC codec in Clause 4, TR 26.940 targeting IMS voice service over GEO and NGSO, the codec needs to meet a quality bar that the end users have come to expect based on the deployed VoLTE IMS voice services. The source recommends the following technical requirements to be considered for ULBC codec Design Constraints.

<a id="P010"></a>

The following design constraints reflecting some of the ULBC WID objectives were generally agreed and included below for completeness.

<a id="P011"></a>

80ms and 160ms bundling support

<a id="P012"></a>

Mono input/output (single channel)

<a id="P013"></a>

Support for packet loss concealment

<a id="P014"></a>

DTX support (with SID and NODATA handling)

<a id="P015"></a>

Jitter buffer support (reference implementation from EVS can be used)

<a id="P016"></a>

The high-level requirements extending the ULBC WID objectives (S4-261336) are proposed below.

<a id="P019"></a>

## 1.1    High-level Technical Requirements

<a id="P020"></a>

## 1.1.1    Bit rates

<a id="P021"></a>

During the SA4 #137-e meeting, it was agreed that the ULBC codec shall support 1 kbps and 1.4kbps as per Table 1.

<a id="P023"></a>

Table 1. ULBC codec supported bitrates and TBS values

<a id="T024"></a>

<a id="T024-R01"></a>
**T024-R01**

- <a id="T024-R01-C01"></a>列 1: 
- <a id="T024-R01-C02"></a>列 2: TBS
- <a id="T024-R01-C03"></a>列 3: 80ms frame (PHY: 64 bits)
- <a id="T024-R01-C04"></a>列 4: 160ms frame (PHY: 64 bits)

<a id="T024-R02"></a>
**T024-R02**

- <a id="T024-R02-C01"></a>列 1（纵向合并:restart）: Active speech
- <a id="T024-R02-C02"></a>列 2: 144
- <a id="T024-R02-C03"></a>列 3: Payload: 80 bits, 1kbps;
- <a id="T024-R02-C04"></a>列 4: -

<a id="T024-R03"></a>
**T024-R03**

- <a id="T024-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T024-R03-C02"></a>列 2: 176
- <a id="T024-R03-C03"></a>列 3: Payload: 112 bits, 1.4kbps
- <a id="T024-R03-C04"></a>列 4: -

<a id="T024-R04"></a>
**T024-R04**

- <a id="T024-R04-C01"></a>列 1（纵向合并:continue）: 
- <a id="T024-R04-C02"></a>列 2: 224
- <a id="T024-R04-C03"></a>列 3: -
- <a id="T024-R04-C04"></a>列 4: Payload: 160 bits, 1 kbps

<a id="P026"></a>

It is also important to specify the encode/decode bitrates for the DTX/SID frame. There are two options:

<a id="P027"></a>

## 1. The DTX/SID frame may use the same bitrate as that of the active speech frame, or

<a id="P028"></a>

2. The DTX/SID frame may use the lower of the two bitrates, while meeting the TBS requirements and values that are considered as feasible form the RAN simulation (TR 26.940).

<a id="P029"></a>

For consistency across the 80ms and 160ms, we propose that the DTX/SID frames shall operate at 1kbps, which may also provide efficiency gains at 80ms operating point.

<a id="P031"></a>

Table 2. Bitrate proposal for DTX/SID

<a id="T032"></a>

<a id="T032-R01"></a>
**T032-R01**

- <a id="T032-R01-C01"></a>列 1: 
- <a id="T032-R01-C02"></a>列 2: TBS
- <a id="T032-R01-C03"></a>列 3: 80ms frame (PHY: 64 bits)
- <a id="T032-R01-C04"></a>列 4: 160ms frame (PHY: 64 bits)

<a id="T032-R02"></a>
**T032-R02**

- <a id="T032-R02-C01"></a>列 1（纵向合并:restart）: DTX/SID
- <a id="T032-R02-C02"></a>列 2: 144
- <a id="T032-R02-C03"></a>列 3: Payload: 80 bits, 1kbps;
- <a id="T032-R02-C04"></a>列 4: -

<a id="T032-R03"></a>
**T032-R03**

- <a id="T032-R03-C01"></a>列 1（纵向合并:continue）: 
- <a id="T032-R03-C02"></a>列 2: 224
- <a id="T032-R03-C03"></a>列 3: -
- <a id="T032-R03-C04"></a>列 4: Payload: 160 bits, 1 kbps

<a id="P034"></a>

Proposals:

<a id="P035"></a>

P1: The ULBC codec shall support encode/decode of active speech frames at 1kbps and 1.4kbps.

<a id="P036"></a>

P2: The ULBC codec shall support DTX SID encode/decode at 1kbps.

<a id="P038"></a>

## 1.1.2    Sample rate and Bandwidth

<a id="P039"></a>

It will be a step back if ULBC supports only NB coding as the end-users have come to expect HD voice quality within the IMS Voice services.

<a id="P040"></a>

Proposals:

<a id="P041"></a>

P3: Given that the performance requirements for 1kbps and 1.4kbps are being discussed to be NWT WB codecs, it seems natural that the internal bandwidth of the codec shall be at least WB.

<a id="P042"></a>

P4: To give flexibility to the proponents to encode/decode at bandwidths at or above WB, it is recommended that the ULBC codec shall operate at a single input/output sampling rate of 32 kHz.

<a id="P044"></a>

## 1.1.3    Algorithmic delay, Frame length

<a id="P045"></a>

The codec delay contributes directly to the total one-way latency of a ULBC voice call over a GEO satellite link, which is already substantially above the ITU-T G.114 preferred limit of 400ms. A typical one-way delay budget includes GEO propagation (~270ms), packet bundling (80–160ms), codec framing (40ms), and JBM and processing overhead (~40–80ms), giving an approximate total above the range of 550-700ms (TR 26.940, Clause 5.1.3). Any additional algorithmic delay added beyond the frame boundary adds to an already constrained system budget with no guaranteed return.

<a id="P046"></a>

Frame length and bundling:

<a id="P047"></a>

A 40ms frame length is proposed for ULBC. In VoLTE, a 40ms DRX configuration has been shown to improve scheduling efficiency and power savings compared to 20ms cycles. The codec shall support bundling at both 80ms (2 frames) and 160ms (4 frames) configurations.

<a id="P048"></a>

Algorithmic delay:

<a id="P049"></a>

Total codec delay comprises two components: framing delay and algorithmic delay (look-ahead, resamplers, and filter processing beyond the frame boundary). The algorithmic delay in AMR-WB (~5ms) and EVS (~12ms) is inherent to LP-based parametric coding, where pitch and LPC analysis require signal context beyond the frame boundary. A causal neural network operating on a 40ms frame has sufficient temporal context for prediction, quantization, and entropy coding without requiring additional signal beyond the frame boundary. There is limited evidence that additional look-ahead improves subjective quality at 1–1.4 kbps for ML-based codecs. Adding further delay to ULBC by analogy to parametric codec precedent is not technically justified and would push the total codec delay well above AMR-WB and EVS with no demonstrated benefit.

<a id="P050"></a>

Based on the discussions from 137-e meeting, there is convergence that the ULBC codec frame length be 80ms.

<a id="P051"></a>

Proposals:

<a id="P052"></a>

P5: The ULBC codec frame length shall be 80ms.

<a id="P053"></a>

P6: The codec shall support bundling at 80ms and 160ms configurations.

<a id="P054"></a>

P7: The ULBC codec should target zero additional algorithmic delay beyond the 80ms frame (fully causal within the frame).

<a id="P055"></a>

P8:  If additional algorithmic delay is considered for the ULBC codec design, it shall not exceed 5ms beyond the frame boundary (for any resamplers, overlap/add, etc).

<a id="P057"></a>

## 1.1.4    Complexity

<a id="P058"></a>

The ULBC codec is intended for deployment on a wide range of devices supporting NB-IoT GEO satellite voice, including low-power handsets and IoT terminals. These devices operate under strict real-time, power, and thermal budgets. The codec must sustain continuous real-time operation during a GEO satellite call — which can impose prolonged PA thermal loads — while sharing compute resources with the radio stack, JBM, PLC, and other concurrent audio processing units. The complexity constraints below are set to ensure the codec is practically deployable across this range of devices.

<a id="P060"></a>

Compute (dynamic complexity):

<a id="P062"></a>

The GMACs/s ceiling is the operative deployability constraint. A ceiling of 2.5 GMACs/s is proposed to ensure the codec can sustain real-time execution on a single efficiency core or DSP without exceeding power and thermal budgets under continuous GEO satellite call conditions. Based on first-principles profiling of reference neural codec architectures at 16 kHz sampling with a 40 ms frame, this ceiling corresponds to models around 5M parameter range — the range demonstrated to achieve the ULBC quality targets efficiently on constrained devices. Models significantly below this compute ceiling risk insufficient capacity for wideband quality at 1–1.4 kbps; models exceeding it require sustained high-throughput execution incompatible with efficiency-core or DSP deployment across the full target device class. It is proposed that the total compute of the ULBC codec shall not exceed 2.5 GMACs/s, measured using the MAC-counting convention and non-MAC operator weighting defined in TR 26.940 clause 6.4.2.

<a id="P064"></a>

Model size (static complexity):

<a id="P066"></a>

The (params, bytes) metric agreed in TR 26.940 clause 6.4.2 shall be reported for each candidate codec as part of the static complexity declaration. To meet the 2.5GMACs/s compute requirement, and power/thermal constraints, the total ULBC codec model size is expected to be around 5M parameters (assuming the model runs once per frame); the GMACs/s ceiling above constitutes the binding constraint on model size.

<a id="P068"></a>

Real-time execution:

<a id="P070"></a>

Both constraints together target a real-time factor (RTF) well below 1.0 on a single efficiency core at the target device class, leaving headroom for concurrent audio processing and ensuring the codec does not become the thermal or latency bottleneck during a GEO satellite call with 80–160ms bundling periods.

<a id="P072"></a>

Proposals:

<a id="P074"></a>

P9: The total compute of the ULBC codec shall not exceed 2.5 GMACs/s (dynamic complexity, measured using the MAC-counting convention and non-MAC operator weighting defined in TR 26.940 clause 6.4.2).

<a id="P076"></a>

P10: Each candidate codec shall report its ML model parameter count and model size in bytes as part of the static complexity declaration, using the agreed (params, bytes) metric defined in TR 26.940 clause 6.4.2. It is recommended that the ULBC codec model size in its entirety should be around 5M parameters.

<a id="P079"></a>

## 2.    Proposal

<a id="P080"></a>

It is proposed to agree to above proposals P1-P10 and adopt as design constraints for ULBC codec in ULBC-4 Permanent document.

**原文页眉：** 3GPP TSG-SA WG4 Audio SWG AdHoc Meeting on ULBC-MED    S4aA260144<br>Shanghai, China, Sept. 28–30, 2026                                                        revision of S4-261621
