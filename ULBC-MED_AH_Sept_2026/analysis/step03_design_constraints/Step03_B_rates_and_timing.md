# Step 3B：码率、打包、帧长与算法时延

> 范围：3.04 Bit rates、3.05 Bundling time、3.06 Frame length、3.07 Algorithmic codec delay。以 184 当前主干为准，对照 169、136、116、155、144、141 附件。计算示例是分析推导，不是新增要求。

> 2026-10-08 评审：已复核结论的证据范围、明确/待定状态及引用；详见[评审记录](../Review_2026-10-08.md)。依据仍是本地 2026 年 9 月材料，不推定后续会议结果。


## 1. 当前基线

| 主题 | 当前条文 | 未决部分 |
|---|---|---|
| 3.04 码率 | 1.0 和 1.4 kbit/s | gross payload 定义的编辑说明带括号 |
| 3.05 打包 | 支持 80/160 ms，并能 packetize/depacketize | 能力范围与选择测试组合需区分 |
| 3.06 帧长 | 20、40、80 ms 之一 | single frame length 带括号 |
| 3.07 算法时延 | 候选上限为 bundling time + x | 上限整条带括号，x 未定 |

来源：[码率](S4aA260184_source.md#T019-R05)、[打包](S4aA260184_source.md#T019-R06)、[帧长](S4aA260184_source.md#T019-R07)、[时延](S4aA260184_source.md#T019-R09)。

## 2. 3.04：先明确码率的统计边界

两个运行码率已写入无括号条文。编辑说明拟把它们定义为 ULBC payload gross rate：包含 codec payload header 和语音比特，排除 RTP、UDP 等协议头；说明仍在括号中，最终措辞未完全冻结。

若采用该口径，内部头字段会占用语音比特预算。减少 RTP 头能降低传输开销，但不能据此声称 codec 自身码率下降。SID 预算也应与此边界对齐。

### 2.1 支持两个码率不等于支持会话中切换

184 注释描述码率在会话内固定。[169](S4aA260169_source.md)是 096→164→169 链的后续文件，明确提出不支持会话中码率切换，也不支持会话中改变 bundling period。

建立会话时如何选择码率、双向是否可不同、改变配置需要何种协商，还需系统规则。不能由“两种码率”推导出完整自适应协议。

## 3. 3.05：支持范围与选择测试运行点

184 要求 80/160 ms 打包，注释对应 `a=ptime`。选择测试注释只考虑：

| 运行点 | 按 gross payload 口径计算 | 169 的 TBS 示例 |
|---|---:|---:|
| 1.0 kbit/s、160 ms | 160 bit = 20 byte | 224 bit |
| 1.4 kbit/s、80 ms | 112 bit = 14 byte | 176 bit |

payload = 比特率 × 打包时间。TBS 包含贡献中的协议和接入层开销假设，不是 codec payload。169 的 1.0/80 ms 第三个运行点仍带括号，不能提升为同等确定的选择测试条件。

能力条文没有改成“每个码率只支持唯一周期”。只测两个组合，不等于禁止其他组合，也不代表四组合互操作规则已全部明确。候选能力验证和性能选择测试需要分别列矩阵。

## 4. 3.06：frame 与 bundle 的区别

codec frame 是算法时间单位；bundle 是聚合成一个 packet 的时间单位，见[184 定义](S4aA260184_source.md#P021)。

| codec frame | 80 ms bundle 内帧数 | 160 ms bundle 内帧数 |
|---:|---:|---:|
| 20 ms | 4 | 8 |
| 40 ms | 2 | 4 |
| 80 ms | 1 | 2 |

这是固定帧长、完整填满 bundle 的算术结果。丢一个 160 ms 包会影响整个 bundle，不能当作只丢其中一个 20 ms frame。PLC、AFR、SID 和 RTP 时间戳必须明确使用哪个单位。

[136，Fraunhofer](S4aA260136_source.md)提议只考虑 20/40 ms，184 仍保留 80 ms，未原样采纳该限制。“single frame length”仍有括号；既不能声称候选必须支持三种帧长，也不能声称单一帧长范围已经定案。

## 5. 3.07：算法时延已包含 bundling

[184 定义](S4aA260184_source.md#P022)的无括号首句把 bundling 缓冲以及算法固有 look-ahead、解码后处理等纳入算法时延。**排除实际计算运行时间和信道传输时延的句子仍在方括号内**，因此不能把这一排除口径写成本版本已冻结的规定；sample-rate conversion 的纳入/排除也仍有保留。

若未来采用 `D_algorithmic ≤ B + x`，B 已包含在 D_algorithmic 中。端到端估算不能再重复加完整 B；JBM 缓冲、实际计算、传播与调度等待须依各自边界另行处理。

例如 B=160 ms、x=40 ms 时，该公式上限为 200 ms。这只是示例：184 没有选定 x=40，也不意味着通话端到端单向时延仅 200 ms。

### 5.1 x 的不同提案

| 文件/主干记录 | 提议 | 状态 |
|---|---|---|
| 184 中 a144 及旧贡献记录 | 0–5 ms | 未定 |
| [155，Qualcomm](S4aA260155_source.md) | 40 ms 折中方案 | 未定 |
| [116，Huawei](S4aA260116_source.md) | 不超过 80 ms | 未定 |
| 184 email 方案 | EVS range | 本主干未形成明确数值 |

[144，Apple](S4aA260144_source.md)讨论中有 40 ms 帧、80 ms 方向及 causal 条件下少量额外时延等不同上下文。应按 184 保留的方案读，不能简化成全文唯一的一个数字。

### 5.2 重采样的定义需协调

采样率行排除 16/32 kHz 转换时延；定义段保留 sample-rate conversion 相关括号和基于 SINGLE sample rate 的旧表达。双接口主干与旧表达需要统一。A/B/C 应共用转换边界，避免候选选择不同统计口径。

## 6. 下一层决策

1. 明确 gross rate 和 SID 预算边界。
2. 分开候选能力、选择测试、会话协商三种运行点矩阵。
3. 明确 single frame length 适用于候选、码率还是会话。
4. 冻结 x 和算法时延测量法。
5. 统一不同帧长下的丢包、DTX 和 AFR 时间网格。

时间单位与比特预算未先固定，C 的每秒计算量、D 的 SID/AFR、E 的头开销都难以公平比较。

## 7. 继续阅读

[C](Step03_C_compute_and_memory.md)、[D](Step03_D_channel_and_dtx.md)、[E](Step03_E_rtp_and_transport.md)、[总索引](Step03_ULBC4_chapter_plan.md)。
