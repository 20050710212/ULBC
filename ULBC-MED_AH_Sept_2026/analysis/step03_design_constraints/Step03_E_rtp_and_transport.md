# Step 3E：RTP payload、头缩减与传输集成

> 范围：3.16 RTP payload format and header reduction。分析 184 的设计接口及 174/178 的相关贡献；这是 ULBC-4 对传输工作的依赖分析，未替代后续 ULBC-9 的完整格式审查。外部 RFC/TS 的状态按贡献所述引用，本次未在线核验。

## 1. 184 已规定什么

[184 对应行](S4aA260184_source.md#T019-R18)要求为 ULBC 指定 RTP payload format，并确定 RTP header reduction 的 essential fields。这一工作要求无括号，但 packetizer 部分仍有括号及编辑问题。

它没有冻结 reduced header 的完整比特布局、字节上限或全部 SDP 参数。不能因“要求指定格式”而声称格式已经指定完毕。

## 2. 先区分三个数据层次

| 层次 | 内容 | 与码率的关系 |
|---|---|---|
| ULBC payload | codec payload header、speech/SID 信息 | B 中拟议 gross codec rate 边界 |
| RTP/UDP/IP | 传输协议头 | 不等同于 codec payload |
| 无线接入层/TBS | PDCP/RLC/MAC 等及传输块资源 | 受具体传输与调度假设影响 |

减少 payload 内部头占用能增加同一 codec rate 下的语音预算；减少 RTP 头则降低传输开销。两者可共同优化，但不能合并成一个不说明边界的码率数字。

## 3. 为什么头开销是关键设计因素

[174，Samsung](S4aA260174_source.md#T045)在 1.0 kbit/s 下列出：

| 头部假设 | byte/packet | 80 ms 头开销 | 160 ms 头开销 |
|---|---:|---:|---:|
| 未压缩 IPv4/UDP/RTP | 40 | 4.0 kbit/s | 2.0 kbit/s |
| 未压缩 IPv6/UDP/RTP | 60 | 6.0 kbit/s | 3.0 kbit/s |
| 去掉 UDP/IP 后的普通 RTP | 12 | 1.2 kbit/s | 0.6 kbit/s |

数值按 `8 × header bytes / packet period` 核算。相比 1.0 kbit/s 的 codec，12 byte RTP 头仍分别占 120%/60%，所以只去掉 UDP/IP 并未解决全部开销。

174 的 reduced RTP 行仍为空；不能拿示例中的 3 byte 无条件填进去作为已选 header size。

## 4. IP+RoHC 与 UHRR 路线

[174](S4aA260174_source.md)区分 IP-based transport 与 UHRR-enabled transport；[178，vivo](S4aA260178_source.md)继续讨论两路线及系统集成。

| 路线 | 贡献描述的作用 | 仍需说明 |
|---|---|---|
| IP + RoHC | 压缩无线链路上的 IP/UDP/RTP 头 | 上下文初始化、修复、talkspurt 瞬态 |
| UHRR + RTP reduction | 去除/恢复 UDP/IP，并进一步缩减 RTP | UE/网络恢复上下文、协商和异常处理 |

174 以约 3–4 byte 描述 RoHC 稳态，178 附录提到 1–3 byte，并采用 3 byte 作预算示例。它们的示例口径不能提升为任何包恒定 3 byte 的保证。初始化、修复和静默后的首包可能不同，需与 D 的 JBM 输入联动。

贡献所述 SA2 支持和相关 TS 架构是本地来源报告。本分析没有独立审查相应 CR 或现行标准，因此不额外断言所有架构细节均已闭合。

## 5. 字段缩减依赖于服务范围

[174 字段表](S4aA260174_source.md#T063)给出以下提案分类：

| 字段 | 提案处理 | 条件或未决项 |
|---|---|---|
| V/P/X/CC | 去除 | 版本与 padding/extension/CSRC 条件成立 |
| PT | 单一 payload type 下可去除 | DTMF/FEC 等额外类型会改变前提 |
| SSRC | 在指定点到点 leg 上去除 | 依赖 session/bearer 的流身份恢复 |
| SN | 压缩 | 仍需损失检测和序号恢复 |
| TS | 压缩/恢复 | 连续发送较可预测，DTX 间隙需额外处理 |
| M | FFS | talkspurt、DTMF 等影响其必要性 |

这是服务范围下的设计提案，不是任意 RTP 场景都能删除这些字段。mono 不足以单独证明 PT、SSRC、M 永远不需要传输。

### 5.1 174 与 178 的实质差异

174 强调单 ULBC payload type、固定周期的简化前提，把 DTX、DTMF、FEC、RTCP 适用性留作 FFS。178 明确列入 active speech、SID 与 DTMF 范围，并对 multi-call、SRTP integrity、RTCP/FEC 提出指导原则或 FFS。

因此不能从 174 的单 PT 简化直接推出 178 覆盖 DTMF 后也无须区分类型。这些应在 ULBC-9 汇总稿确认，而不是由本分析擅自合并成一个格式。

### 5.2 DTX 对时间戳恢复的影响

固定 ptime 使连续发送的时间推进较可预测。DTX 停止发送后，媒体时间仍继续推进；收到的 packet 序号与媒体时间的关系需要另外处理。仅凭“固定 bundle”不能证明 TS 永远可由 SN 恢复。

方案应说明静默结束、首个 SID 丢失、首个 speech 包丢失、长间隙及上下文失同步如何恢复时间与帧类型。上述是分析追踪项，不是当前已定格式。

## 6. Payload 与 SDP 尚需一起闭合

B 的 frame/bundle/rate 决定每包预算；D 的 SID/NO_DATA 决定包内容；A 的带宽能力决定接收能力协商。packetizer 需要定义内部帧顺序、长度、类型以及 padding 等边界，不能由编码帧长单独确定。

178 仍留有 format definition、SDP negotiation、UHRR/bearer、IMS-AGW 等编辑占位。这与 184 的工作分工一致：明确任务，不代表结果已完成。

建议后续 ULBC-9 逐项检查：

1. 包类型和 reduced-header 适用 leg。
2. 静态字段如何建立、动态字段如何恢复。
3. 丢包、DTX、重排和上下文异常的行为。
4. 全部运行点及特殊包的 bit/byte 预算。
5. SDP offer/answer 参数及不支持时的行为。

## 7. 本组结论

头开销必须纳入系统预算；ULBC payload gross rate、RTP 开销和 TBS 应分别报告。184 未给出可直接实现的最终 reduced RTP 格式，174/178 的简化前提及范围也尚需统一。

[B](Step03_B_rates_and_timing.md)、[D](Step03_D_channel_and_dtx.md)、[总索引](Step03_ULBC4_chapter_plan.md)。


## 8. 后续主干核对

本轮已继续完成 [179 / ULBC-9 与完整传输主题分析](../remaining_topics/Topic09_transport_and_system_integration.md)。179 在 R4 为 n，其字段表将 M/PT/SN/TS/SSRC 保留为 FFS；不能用本文件列出的 174 提案分类替代 179 的主干状态。新增分析还覆盖 IP/RoHC 异常包预算和系统组依赖。
