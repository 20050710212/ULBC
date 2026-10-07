# Step 3D：JBM、PLC 与 VAD/DTX/CNG

> 范围：3.13 Jitter buffer management、3.14 Packet loss concealment、3.15 VAD/DTX/CNG 与 SID。本组同时涉及 codec 能力、发送调度和性能测试，需要与 B/E 交叉阅读。

> 2026-10-08 评审：已复核结论的证据范围、明确/待定状态及引用；详见[评审记录](../Review_2026-10-08.md)。依据仍是本地 2026 年 9 月材料，不推定后续会议结果。


## 1. 主干状态

| 主题 | 184 当前状态 | 不能提前认定的内容 |
|---|---|---|
| 3.13 JBM | 要求仍在方括号中；注释写历史 Agreed/TR 依据 | 当前条文已无保留冻结 |
| 3.14 PLC | shall support PLC 无括号 | 具体 FER 矩阵已全部确定 |
| 3.15 DTX/CNG | VAD/DTX/CNG framework 无括号 | SID 间隔、hangover、Rel-20 分期已确定 |

来源：[JBM](S4aA260184_source.md#T019-R12)、[PLC](S4aA260184_source.md#T019-R13)、[DTX](S4aA260184_source.md#T019-R14)。JBM 的历史依据和当前括号应同时保留，不能任选一个替代另一个。

R4 将 100（AFR）和 126（JBM）标为 postponed；下文引用其技术论证，不表示其提案已采纳。

## 2. 3.13：GEO 传播稳定仍不能直接取消 JBM

JBM 管理的是解码端收到包的时间变化，而不只是卫星传播时延。[126，Fraunhofer](S4aA260126_source.md)接受 GEO 无线传播变化很小的假设，但讨论核心网定时、SPS 边界、时钟偏差、重激活和 RoHC 大包事件。

在其单一 SPS occasion 模型中，包错过一次机会可能等到下一个 80/160 ms 周期；因此微小到达抖动可以在调度边界变成较大的离散延迟变化。这是该贡献模型中的结果，不能推广为所有实际调度方案必然发生同等延迟。

126 提议去掉 JBM 约束括号，并考虑向 RAN2 澄清超过 TBS 的包如何承载。184 尚保留括号，因此本分析把它作为待决提案。

### 2.1 JBM 应处理哪些输入

| 到达模式 | 来源或影响 |
|---|---|
| 小幅连续抖动 | 核心网/处理定时 |
| ramp 后跳变 | 源与调度时钟偏差 |
| 周期级阶跃 | SPS occasion 边界或重激活 |
| 上下文恢复瞬态 | RoHC 初始化/修复的大包 |
| 静默后恢复 | DTX 的时间跳跃与 talkspurt |

184 注释说明 TS 26.114 的 JBM 要求可能需适配 NB-IoT voice。不能直接把传统 jitter/loss profile 当作已选 ULBC profile。JBM 缓冲延迟也不能混入 B 的算法时延预算而不说明口径。

## 3. 3.14：PLC 支持能力与失包测试条件

PLC 的 shall 已明确；具体 loss rates 仍 FFS，与 Step 2 中 FER 方案未定相呼应。

B 已说明 packet 可以包含多个内部 frame。应区分：

1. 丢失 RTP/bundled packet，导致相应全部 codec frames 不可用。
2. 内部帧损坏或解码失败。
3. 包晚到，被 JBM 判定为不可播放。
4. DTX NO_DATA，属于有意无发送，不能一概作为丢包。

[141 附件](S4aA260141_attachment_source.md#T019)明确提议以 bundle 为 erasure 单位，并提出内部/外部 JBM 等组织方式；这些补充不能全部视为 184 已纳入。

只给平均 FER 还不足以定义测试。随机损失、连续 burst、不同 bundle 长度和恢复后的音质都影响 PLC。丢一次 160 ms bundle 与一次 20 ms frame 的影响时间不同，百分比相同也不等于事件模式相同。

PLC 还可能触发额外 decoder 计算及状态缓冲，C 的最坏计算/RAM 统计应覆盖最终要求中的丢包模式。

## 4. 3.15：把 DTX 的几种机制分开

- VAD 判断是否为语音，可能含 VAD hangover 防止截断语音尾部。
- DTX handler 决定发送 speech、SID 或 NO_DATA，可能另有 DTX hangover。
- SID 携带背景噪声更新信息；CNG 在接收端生成舒适噪声。
- SPS/无线调度决定没有数据时能否跳过发送，以及一个 SID 包占用多少资源。

codec 层少发比特与无线层少用一次发送机会不是同一个计量结果。固定 TBS 假设下，SID 即使更小也可能仍占相同 transport block；更长更新间隔会减少发送机会，但可能降低背景变化跟踪能力。这需要质量与系统假设共同评价。

### 4.1 SID 更新间隔的提案对照

| 文件 | 提议 | 单位与解读 |
|---|---|---|
| [097，vivo](S4aA260097_source.md#T033-R01-C02) | 固定每 320 ms 一次，或更新频率不超过每 320 ms 一次（间隔至少 320 ms） | 按最终建议表的 frequency 读，避免把 maximum update rate 误译为最大间隔；不依赖最终 frame 长度 |
| [117，Huawei](S4aA260117_source.md) | 不频于每 [640] ms 一次 | 以发送节省为主要论据 |
| [122，Dolby](S4aA260122_source.md) | 1.0 kbit/s [640] ms；1.4 kbit/s [480] ms | 按码率提出不同值 |
| [134，Fraunhofer](S4aA260134_source.md) | 不频于每 [8] bundled packets 一次 | 80 ms 时 640 ms，160 ms 时 1280 ms |
| [163，Ericsson](S4aA260163_source.md) | 讨论 SID 包大小并确认 RAN 假设 | 没有定具体更新间隔 |

320 ms、640 ms、“8 frames”和“8 bundles”不能混用。例如 8 个 20 ms frames 是 160 ms，8 个 160 ms bundles 是 1280 ms。184 仍未选值，不能拼出一个不存在的折中结论。

### 4.2 SID 大小提案

097 主张 SID payload 不超过运行点的 speech payload；117 明确包含 payload-format header，并列出 10/14/20/28 byte 的四组合预算。163 强调需要确认固定 TBS 等系统假设。

选择测试的两个运行点，对应 B 的 20 byte 与 14 byte 预算；其他组合的算术预算不能直接提升为已决定测试配置。SID 是否混在 speech bundle 中、多个内部 frame 类型如何标记、是否允许不同 packet 大小，需与 E 的 payload 格式一起闭合。

### 4.3 Hangover、AFR 与 DTX 默认模式

097 和 122 提出不另设 hangover 硬限制，交由 AFR 捕获发送开销。122 还主张以 DTX-on 为主要评测模式；097 的修订提议保留所有运行点 DTX on/off 能力。184 的 framework 要求不能替代这些运行细节决策。

[100，vivo](S4aA260100_source.md)报告测量点、网格、参考代码、采样率及材料对 AFR 的影响，提出将 AFR 用作信息报告，反对尚不稳定的 ±1 点 pass/fail。122 则提出用对应 clean speech 的 AMR-WB AFR 加 [x] 点作为 noisy speech 参考。它们与 Step 2 的多个候选公式存在真实分歧。

本分析引用贡献文字和表格结论，未复现实验或独立核验嵌入图中的曲线。AFR 是 active transmission 比例指标，不能单独证明 CNG 质量、语音尾部完整性或实际电池节省。

## 5. 待闭合的协议和测试状态

应覆盖 speech→hangover→SID→NO_DATA→speech 的转换，并分别定义 SID 丢失、静默后首包丢失、时间戳跳跃和 PLC/CNG 状态恢复。这里是分析建议，当前主干没有完整状态机。

| 决策 | 对应依赖 |
|---|---|
| JBM 约束及到达 profile | ULBC-9/RAN 系统输入，ULBC-5/8 测试 |
| bundle 级 erasure 与 FER/burst | B 的周期，Step 2 质量门槛 |
| SID 时间单位、更新率、大小 | B 的预算，E 的类型和时间字段 |
| AFR 定义、参考和通过标准 | ULBC-3/7/8 |
| CNG 保留背景的要求 | F 的能量/噪声评价 |

## 6. 继续阅读

[B](Step03_B_rates_and_timing.md)、[C](Step03_C_compute_and_memory.md)、[E](Step03_E_rtp_and_transport.md)、[F](Step03_F_signal_behavior.md)、[总索引](Step03_ULBC4_chapter_plan.md)。
