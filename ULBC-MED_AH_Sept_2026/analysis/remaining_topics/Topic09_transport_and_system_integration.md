# 传输开销与既有系统集成分析

> 对应原 Overview Step 9，覆盖 R4 4.9。本文件将用户所说“系统继承”理解为继承既有 IMS/NB-IoT NTN 架构与规范机制，并分析 ULBC 的系统集成。主干为本地 draft 179 / ULBC-9 v0.1.0，R4 为 n；对照 174/178、109、124、130、112/113 和 Step 3B/D/E。

> 2026-10-08 评审：已复核结论的证据范围、明确/待定状态及引用；详见[评审记录](../Review_2026-10-08.md)。依据仍是本地 2026 年 9 月材料，不推定后续会议结果。


## 1. 本主题的结论

ULBC 需要同时处理 codec payload 和传输头开销。资料描述 IP transport 必须支持、UHRR 路线可选，但 **最终 reduced RTP 格式、动态字段恢复和系统协商仍未冻结**。RoHC 的稳态小头不能代替初始化、恢复或 DTX 后首包预算。

既有系统机制可以提供架构起点，不能据此推定 RTP profile 信令、特殊大包调度、RTCP 和端到端抖动条件均已解决。本分析描述本地贡献中的标准引用和假设，没有在线核验现行规范或进行设备实验。

## 2. 主干版本与状态

| 来源 | R4 状态 | 本轮发现 |
|---|---|---|
| [179：ULBC-9 v0.1.0](sources/S4aA260179_source.md) | n | 已合入 transport table、scope、field analysis，solutions/format/SDP/system 多处占位 |
| [174：header analysis](sources/S4aA260174_source.md) | a，104→174 | 传输开销和字段简化提案 |
| [178：ULBC-9 updates](sources/S4aA260178_source.md) | a，098→178 | speech/SID/DTMF 范围及系统集成方向 |
| [109 CR](sources/S4aA260109_source.md) | n | TR 26.940 引入 UHRR 术语和架构对齐提案 |
| [124 IP/RoHC](sources/S4aA260124_source.md)、[130 transport](sources/S4aA260130_source.md) | n | IP 的具体评估与较粗预算方案 |
| [112 delay](sources/S4aA260112_source.md)、[113 DTMF](sources/S4aA260113_source.md) | pp | 延期技术输入，不作为已采纳条件 |

本地没有 179 ZIP，基于明确命名的 draft DOCX 阅读。另有 [179 r1](sources/S4aA260179_draft_r1_source.md)，两份当前正文及本地差异文件 `sources/S4aA260179_draft_to_r1.diff` 显示 r1 简化 transport 描述并删除 applicability 标题；主要开销表与 FFS 仍保留。它是另一 local draft，不凭后缀声称已被会议批准。

## 3. 系统继承的边界

```mermaid
flowchart LR
  U[UE 的 ULBC 与 RTP] --> R[NB IoT NTN GEO 无线段]
  R --> N[eNB 与核心网]
  N --> G[IMS 网关与媒体端点]
  G --> E[远端语音服务]
```

图仅表示概念路径，实际 header removal/restoration 的节点依所选机制确定。

### 3.1 IP transport

179 附录和 109 提案描述 IP 路线为 mandatory，RoHC recommended；174/179 正文用 may applied 表述链路压缩。不能把 130 的“IP with RoHC mandatory”标题解释为所有 RoHC 配置均已强制冻结。

[124](sources/S4aA260124_source.md#P029)描述 IP/UDP/RTP 端到端存在，RoHC 只在 UE/eNB 的 PDCP 无线段压缩与恢复；网络继续转发原协议包。其 one PDN、separate signalling/voice DRB 等是特定评估与引用背景，需要由系统/RAN 配套确定。

### 3.2 UHRR 与 reduced RTP

[179](sources/S4aA260179_source.md#P045)描述 UHRR 去除/恢复 UDP/IP，RTP header 和 payload 仍存在；附录进一步讨论 UE/PGW 的 UDP/IP 恢复，以及 UE/AGW 的 RTP 缩减/恢复。

UHRR 不应简单等同“整个 RTP/UDP/IP 头自动压到 3 byte”。130 使用 3 byte compact header 的方案描述比较粗；179 reduced RTP 行仍 FFS，所以以 179 分层边界为准。

[109 CR](sources/S4aA260109_source.md#T006)提议更新 TR 26.940 §2、§3.3、§5.2.1，引入 TS 23.228 reference、UHRR abbreviation 和架构图编辑。其 n 状态不能视为 CR 已最终批准。

## 4. 开销计算需先固定层次

设 codec gross payload rate 为 r bit/s，bundle 为 B 秒，每包 header H byte：

```text
payload bit/packet = r × B
header rate = 8 × H / B
payload + header rate = r + 8 × H / B
```

这只是媒体包逻辑预算，不含无线重发、repetition、PHY/control、离散 TBS padding 或 scheduling 空闲机会。B 的 gross payload 内部头定义在 184 仍带编辑括号，计算时需声明采用该口径。

### 4.1 179 的协议头比较

| 配置 | H byte/packet | 80 ms header rate | 160 ms header rate |
|---|---:|---:|---:|
| IPv6/UDP/RTP 未压缩 | 60 | 6.0 kbit/s | 3.0 kbit/s |
| IPv4/UDP/RTP 未压缩 | 40 | 4.0 kbit/s | 2.0 kbit/s |
| IP+RoHC 稳态示例 | ~3–4 | ~0.3–0.4 kbit/s | ~0.15–0.2 kbit/s |
| UHRR 后普通 RTP | 12 | 1.2 kbit/s | 0.6 kbit/s |
| UHRR 后 reduced RTP | FFS | FFS | FFS |

来源：[179 Table 1](sources/S4aA260179_source.md#T048)。1.0 kbit/s 时，12 byte RTP 头分别相当于 120%/60% codec rate；1.4 kbit/s、80 ms 时相当于约 85.7%，比例分母须随码率变化。

延长 bundle 减少 packets/second，但 B 已说明 buffering/algorithmic delay 和更长丢失跨度的代价。不能只看 header rate 选择 160 ms，也不能忽略 selection 目前主要考察 1.0/160 与 1.4/80 两运行点。

### 4.2 接入层与 TBS 是另一层

[124 Table 5](sources/S4aA260124_source.md#T069)在 3 byte RoHC + 5 byte access stratum 假设下计算：

| 运行点 | ULBC payload | 加 8 byte 后 | 贡献选择的 TBS | 余量 |
|---|---:|---:|---:|---:|
| 1.0 kbit/s、80 ms | 10 byte | 18 byte | 144 bit | 0 |
| 1.4 kbit/s、80 ms | 14 byte | 22 byte | 176 bit | 0 |
| 1.0 kbit/s、160 ms | 20 byte | 28 byte | 224 bit | 0 |
| 1.4 kbit/s、160 ms | 28 byte | 36 byte | 296 bit | 1 byte |

36 byte 是 288 bit 原始需求，124 按允许的离散 TBS 表选 296 bit，而非将相乘结果算成 296。117 的四组合讨论写 288 bit，属于预算与最终 TBS 选择口径差异；不能混用。

一个额外 header byte 可能让 TBS 跳档，收益不一定线性。124 报告 1.4/160 的 296 bit 缺少其引用 TR 中的容量/覆盖仿真结果；这不等于该块尺寸不能配置，也不能用 payload 字节数替代实际无线资源。

## 5. RoHC 稳态与异常包

[124](sources/S4aA260124_source.md#P019)报告自己的 RFC 3095 实现和 libROHC 对比；明确结果未经 UE/网络设备验证，不是 conformance evidence。本分析未复现这些实现。

其所评估 profile 0x0001、CID 0、携带 UDP checksum 与 timestamp stride 条件下：[Table 3.10-1](sources/S4aA260124_source.md#T202)为 IPv4/IPv6 IR 41/64 byte、IR-DYN 23/20 byte，稳态 3/3 byte。不同 checksum/stride 条件可改变大小。

### 5.1 固定 grant 无法靠平均值解决大包

124 报告 IR 包加 payload/access overhead 需要约 2.0–4.4 倍稳态 TBS；它没有据此规定实际要等待多少个周期。是否 RLC segmentation、额外 grant、较大 TBS 或其他调度，需要 RAN 定义。

其平均 header 公式 `C + (H−C)/f` 仅估算每 f 包刷新一次的平均成本；不能证明每个大包都能塞入固定 SPS grant。U-mode periodic refresh 和 O-mode feedback-driven repair 也不能混为一个已选定的刷新周期。

### 5.2 DTX 后首包可能增大

[124 Table 7](sources/S4aA260124_source.md#T097)报告其模型中 talkspurt onset 的 header 为 4/6 byte，8 种 pause/运行点组合有 7 种超过稳态 TBS。这是评估条件结果，不是任意部署的必然计数。

DTX 降低发送频率，同时改变 RTP timestamp 与 sequence number 的关系。若恢复首包丢失或 RoHC context 损坏，需要能区分发送静默、网络丢包及恢复失败，否则 codec PLC 和系统丢包会互相掩盖。

## 6. RTP 字段的主干状态比贡献更保守

[179 Table 2](sources/S4aA260179_source.md#T063)中 V/P/X/CC 为 static can be removed，CSRC list 为 removed；M、PT、SN、TS、SSRC 均仍 FFS。

174 曾给 SN compressed、TS compressed/reconstructed 和 SSRC removed 的提案；不能用这些提案分类覆盖 179 当前的 FFS。scope 包括 speech、SID 与 DTMF，所以也不能只凭 single ULBC format 推导出“PT 信息永远无须存在”。

179 guidelines 的 single mono、指定 point-to-point leg、session 参数固定等，是字段简化前提。RTCP/FEC 仍 FFS，SRTP integrity protection 在该指导范围中写不支持；不能扩大成所有安全或 ciphering 一律关闭。

format definitions、SDP parameters、UHRR/bearer 和 IMS-AGW 集成仍 editor's notes。179 尚不是可直接实现的 reduced-header specification。

## 7. DTMF 与时延假设

### 7.1 DTMF 不要求一定经语音编码器传输

[113](sources/S4aA260113_source.md)讨论 telephone-event RTP、digit/STOP、音频编码与 SIP INFO 四路线，倾向用 header-reduced RTP telephone-event。其 4 byte payload、duration/end/volume 等是贡献论据，尚未形成当前 reduced header layout。

113 为 postponed，并明确 FFS 如何区分 DTMF 与 voice；179 虽列 DTMF scope，也不能视为 113 完整方案已通过。113 把 14 byte 描述为最小 voice frame，应限定其 1.4/80 等上下文；不能忽略其他组合的 10 byte payload。

### 7.2 小传播抖动不等于端到端包到达恒定

[112](sources/S4aA260112_source.md)提议 GEO 无线 jitter <0.1 ms、UE–AGW <3 ms 等假设，并写明 non-normative；R4 为 postponed。

[Step 3D / 126](../step03_design_constraints/Step03_D_channel_and_dtx.md)说明调度边界、clock drift、SPS reactivation 及大包可以产生额外到达瞬态。两者观察的对象不同：链路传播/网络抖动与调度后解码端到达变化不能直接替代。

分析端到端 delay 时建议分别列账 codec algorithmic delay（184 定义首句已包含 bundling）、实际处理、调度等待、传播/网络及 JBM buffering，并确保边界互不重复。184 定义中排除 processing/channel delay 的句子仍带方括号，本段是预算分析建议，不声称完整排除口径已冻结。不能重复加完整 bundling，或把 112 的小 jitter 假设当成无需 JBM 的证明。

## 8. DTX 的系统节省要按发送机会算

在简化固定 TBS 模型下，若 active bundle 比例为 A、inactive 段每 I 秒一个 SID、SPS 周期为 B，且忽略 hangover/转换事件，可近似写：

```text
occupied occasion ratio ≈ A + (1−A) × B/I
```

例如 A=0.4、B=80 ms、I=320 ms，比例约 0.55。它不是电池节省 45% 的实测结论；控制、接收、热行为、SID/speech 混包等未计入。I 在 ULBC-4 仍未选值，不能用这个例子替代 320/640/480 或 8 bundles 的争论。

固定 TBS 下较小 SID 可能仍占完整一次机会；短 payload 平均码率和实际 grant duty cycle 必须分别报告。

## 9. 需要其他组配套的事项

| 层次/责任 | 本地材料提示的依赖 | 当前状态 |
|---|---|---|
| SA4 | payload、essential fields、frame/bundle、DTMF 类型和时间语义 | 多项 FFS |
| RAN/RAN2 | NB-IoT RTP RoHC profiles 的信令、SPS/TBS、大包双向承载 | 124 提出澄清/联络建议，未证实已解决 |
| SA2 | UHRR 架构、voice bearer、RTCP 使用与系统范围 | 按贡献引用背景，仍有待确认项 |
| CT1/IMS | SDP offer/answer、TS 24.229 对接 | 179 明确协作/占位 |
| UE/网关实现 | context、checksums、runtime 和恢复机制 | 需要互操作检查 |

124 报告其引用版本中 PDCP-Config-NB-r13 尚无法信令所评估 RTP profile；这里归属为作者的规格核对结果，不推广为未经核验的现行所有版本结论。130 的 handover/fallback 思路也是提案，不能当作 179 已定义的自动回退流程。

## 10. 建议的系统验证顺序

1. 固定服务范围、双向运行点和两种 transport 的适用 leg。
2. 确认每种 header/AS 假设，以及 discrete TBS 的余量。
3. 覆盖初始化、context repair、连续 loss、DTX 恢复和 DTMF 包。
4. 由 RAN/system 给出实际到达时序及大包处理后果。
5. 定义 SDP 和不支持能力时的行为，再做端到端互操作检查。
6. 将所得 profiles 传递到 ULBC-7/8 的 JBM/PLC 测试。

目前能建立可审查的开销模型与依赖清单，不能声称已经完成 reduced RTP bit layout、无线仿真或实际系统验证。

[测试与处理](Topic07_testing_and_processing.md)、[Step 3B](../step03_design_constraints/Step03_B_rates_and_timing.md)、[Step 3D](../step03_design_constraints/Step03_D_channel_and_dtx.md)、[Step 3E](../step03_design_constraints/Step03_E_rtp_and_transport.md)、[总体 Overview](../Audio_SWG_Tdoc_allocation_R4_overview.md)。
