# Step 3 ULBC-4 总索引与分析目录

> 来源：S4aA260184_ULBC-4_v0.3.0.docx，正文标为 0.3.0 (draft)，对应 R4 议题 4.4，状态 `a`。已按 A–F 输出六份技术分析，覆盖 18 个分析主题；本文件保留结构清点与共同前导。日期：2026-10-05。

- [184 原文 Markdown](S4aA260184_source.md)
- [184 修订差异](S4aA260184_changes.diff)
- [返回总体 Overview](../Audio_SWG_Tdoc_allocation_R4_overview.md)

## A–F 分析文档

| 文档 | 内容 | 分析编号 |
|---|---|---|
| [A：接口与音频范围](Step03_A_audio_interfaces.md) | 采样率、WB/SWB、mono | 3.01–3.03 |
| [B：码率与时间结构](Step03_B_rates_and_timing.md) | 码率、bundle、帧长、算法时延 | 3.04–3.07 |
| [C：计算与存储资源](Step03_C_compute_and_memory.md) | 计数、预算、profiling/RTF、ROM、RAM | 3.08–3.12 |
| [D：信道与静音运行](Step03_D_channel_and_dtx.md) | JBM、PLC、VAD/DTX/CNG/SID | 3.13–3.15 |
| [E：传输接口](Step03_E_rtp_and_transport.md) | RTP payload、头缩减、协商与集成 | 3.16 |
| [F：信号行为与验证](Step03_F_signal_behavior.md) | 降噪/非语音鲁棒性、增益及能量检查 | 3.17–3.18 |

六份文档包含主干状态、术语解释、贡献对照、技术影响和待决项。它们完成本轮分析，不表示全部规范问题已经定案。

## 1. 有多少个章节

可以按三个口径回答：

| 口径 | 数量 | 含义 |
|---|---:|---|
| 原文编号大章 | **6** | Scope、Introduction、约束表、Definitions、Revision history、References |
| 原文设计约束条目 | **15** | §3 Table 1 中 Parameter 列非空的技术条目，不含表头与空行 |
| 建议逐项分析的小章节 | **18** | 复杂度拆为 3 节、内存拆为 2 节，其他 13 个条目各 1 节 |

另设 **3.00 文档读法与决策依赖**，作为分析前导，不计入 18 个技术小章节。因此目录总共是 **1 个前导 + 18 个技术章节**。

本次按用户要求，将 Step 3 扩展为 **整个 ULBC-4 的分析总任务**。原 overview 的 Step 3（采样率/带宽）、Step 4（资源）、Step 5（时延/切换/DTX）会由这份目录覆盖；以后这些内容无需按旧编号重复分析。ULBC-5/7/8a/9 和数据集等后续主题继续保留。

## 2. 原文的大章

| 原章节 | 名称 | 内容位置/作用 |
|---|---|---|
| §1 | Scope | 设计约束的范围与最低要求背景 |
| §2 | Introduction | 工作目标、来源依据和 agreed / square brackets 的读法 |
| §3 | ULBC codec design constraints | 核心 Table 1，15 个参数条目 |
| §4 | Definitions | Bundling period、algorithmic codec delay 的定义 |
| §5 | Revision history | 0.1.0 → 0.2.0 → 0.2.1 → 0.3.0 的版本记录 |
| §6 | References | TR 26.940、WID、TS 26.114、G.191 的引用列表 |

原文没有为 Table 1 中每个参数建立独立的 3.1、3.2 子章节。下面的 3.01–3.18 是为后续分析新建的目录编号，不能作为原文条款编号引用。

## 3. 原文 15 个约束条目清单

Table 1 的提取定位为 **T019**，共 20 个物理行：1 行表头、15 行非空参数、4 行空白。空白行是 R08、R15、R16、R17，不能计为新的技术主题。每项的后续阅读包含 Design constraint 与 Note 两列。

| 序号 | 原文 Parameter | 中文导航 | 原文位置 | 对应分析章节 |
|---:|---|---|---|---|
| 1 | Sampling Frequency | 采样率及 PCM 接口 | [T019-R02](S4aA260184_source.md#T019-R02) | 3.01 |
| 2 | Audio bandwidth | 音频带宽 | [T019-R03](S4aA260184_source.md#T019-R03) | 3.02 |
| 3 | Number of audio channels | 声道数量 | [T019-R04](S4aA260184_source.md#T019-R04) | 3.03 |
| 4 | Bit rates | 码率与 payload 口径 | [T019-R05](S4aA260184_source.md#T019-R05) | 3.04 |
| 5 | Bundling | 打包周期与 packetization | [T019-R06](S4aA260184_source.md#T019-R06) | 3.05 |
| 6 | Frame length | 帧长 | [T019-R07](S4aA260184_source.md#T019-R07) | 3.06 |
| 7 | Algorithmic codec delay | 算法时延 | [T019-R09](S4aA260184_source.md#T019-R09) | 3.07 |
| 8 | Computational complexity | 计算复杂度 | [T019-R10](S4aA260184_source.md#T019-R10) | 3.08–3.10 |
| 9 | Memory | 内存与模型存储 | [T019-R11](S4aA260184_source.md#T019-R11) | 3.11–3.12 |
| 10 | Jitter buffer management (JBM) | 抖动缓冲管理 | [T019-R12](S4aA260184_source.md#T019-R12) | 3.13 |
| 11 | Packet loss concealment (PLC) | 丢包隐藏 | [T019-R13](S4aA260184_source.md#T019-R13) | 3.14 |
| 12 | Discontinuous transmission (DTX / CNG) | VAD、DTX 与舒适噪声 | [T019-R14](S4aA260184_source.md#T019-R14) | 3.15 |
| 13 | RTP payload format and header reduction | RTP 载荷与头压缩 | [T019-R18](S4aA260184_source.md#T019-R18) | 3.16 |
| 14 | Noise suppression and robustness to non-speech input | 降噪与非语音输入鲁棒性 | [T019-R19](S4aA260184_source.md#T019-R19) | 3.17 |
| 15 | Output gain tolerance | 输出增益容差 | [T019-R20](S4aA260184_source.md#T019-R20) | 3.18 |

此清单用于统计和导航；具体数值与提案状态详见 A–F，不把备选数字视为已定案。JBM、noise suppression 的参数名称本身带有未闭合在同格内的方括号，完整括号范围需连同该行其他列读取；导航名称在这里省略外层括号，原文转换版保留。

## 4. 建议分析目录

### 3.00 前导 文档读法与决策依赖

读取 §1、§2、§4、§5，并结合 111（decision sequence）和 141/144（overall constraints）建立统一读法：

- 区分 unbracketed baseline、square brackets、Editor's note、Positions – to be verified。
- 区分原文参数要求、测量方法、测试计划注释与会中贡献。
- 对照 Step 1 的直接 selection 路线、Step 2 的性能要求与未决项。
- 建立采样率/带宽、码率/bundling/帧长、复杂度/存储、时延/运行行为之间需要核实的依赖。

§2 明确说明：尚未同意的约束以方括号表示，未括起的约束为 agreed。具体分析时还要看 Note 和修订内容，不能只读一个脱离上下文的数值。

### 3.00 的共同结论与决策依赖

[111 decision sequence](S4aA260111_source.md)主张先明确服务/codec 范围，再定资源预算和音频范围，以便向性能要求及测试计划传递稳定输入。这是贡献提出的决策顺序，不是要求用户必须按唯一顺序阅读。其早期 qualification 表述须与 Step 1 当前直接 selection 路线区分。

[141 主文件](S4aA260141_source.md)主要指向附件，本轮另提取了 [141 附件](S4aA260141_attachment_source.md)，不能仅凭封面归属数值。[144 overall constraints](S4aA260144_source.md)覆盖音频、时延与资源；其建议并非全部进入 184。

| 决策输入 | 传递至 | 主要影响 |
|---|---|---|
| A 的接口/带宽 | B/C/F、ULBC-3/7 | 转换统计、参考信号、频带检查 |
| B 的码率/frame/bundle | C/D/E、ULBC-5/7/8 | 每秒计算、丢包时间、SID 和包预算 |
| C 的指标/预算 | 算法实现、测试与交付 | 可实现性和可重复测量 |
| D 的 JBM/PLC/DTX | B/C/E/F | 到达时序、峰值开销、时间字段、CNG |
| E 的传输及恢复规则 | D、ULBC-9/系统工作 | 头开销、时间戳、异常包与协商 |
| F 的信号行为原则 | ULBC-3/7/5/8 | 阈值、测量工具和评分处理 |

阅读中分别标记“184 无括号基线”“184 未决项”“贡献提案”“本分析推论”。R4 的 a/n/pp 是议程处理状态，不能单独证明贡献中每个细节成为主干约束。100（AFR）与 126（JBM）在 R4 为 postponed；引用其技术内容用于解释分歧，不作已采纳结论。

### A 接口与音频范围 3 节

| 编号 | 小章节 | 下一步阅读问题 | 优先相关输入（短编号） |
|---|---|---|---|
| 3.01 | 采样率与 PCM 输入输出 | 支持哪些采样率？编码器/解码器接口如何规定？重采样是否计入复杂度/时延？ | 118、149、161 |
| 3.02 | WB 与 SWB 音频带宽 | shall / may 的范围是什么？WB/SWB 的测试、reference 与 SDP 注释如何解释？ | 101、092、149、161；交叉 Step 2 |
| 3.03 | Mono 与声道数量 | 输入/输出声道约束是什么？需记录哪些接口边界？ | 184 主干 |

### B 码率与时间组织 4 节

| 编号 | 小章节 | 下一步阅读问题 | 优先相关输入 |
|---|---|---|---|
| 3.04 | 两码率与 payload 预算 | 码率包含哪些 bits？哪些 header 被排除？session 固定码率与 switching 提案如何对应？ | 096 → 164 → 169；交叉 174/178 |
| 3.05 | Bundling 与 packetization | 支持周期与 selection 测试组合如何区分？ptime 与 session 固定 bundling 如何规定？ | 164/169；交叉 ULBC-7/8a |
| 3.06 | Frame length | 候选帧长集合与 single frame length 语句的状态是什么？与 bundling 如何配合？ | 136 |
| 3.07 | Algorithmic codec delay | 如何定义和计数？上限中的 x 有哪些方案？buffering、重采样、processing/channel delay 如何区分？ | 116、155；141、144；§4 Definitions |

### C 计算与存储资源 5 节

| 编号 | 小章节 | 下一步阅读问题 | 优先相关输入 |
|---|---|---|---|
| 3.08 | 复杂度指标与计数原则 | GMAC/s、WMOPS 与 RTF 的角色如何区分？如何覆盖 NN 与其他计算？ | 133、102、115 |
| 3.09 | 复杂度预算与 UE 平台 | 各预算提案的前提是什么？standard 3GPP UE implementability 如何落实？ | 102、115、138、141、144 |
| 3.10 | 复杂度测量 profiling 与 RTF | ONNX profiling 与实际运行时间怎样验证？平台、配置、并行与码率如何统一？ | 132、095、160 |
| 3.11 | ROM 模型大小与参数存储 | 两码率模型是否都计入？参数数量、bytes/parameter、MB 如何对应？ | 139、154、102、115、141、144 |
| 3.12 | RAM 工作内存与状态 | Active bitrate 的模型、data path 与 state memory 各怎么计数？与 ROM 是否独立？ | 102、115、138、139、154、141、144 |

这里把原文 Computational complexity 拆成 3 节、Memory 拆成 2 节，是为了分别处理定义、预算和验证；不是增加新约束。某些测量问题来自相关贡献的 topic，而非主干已经给出的完整方法。

### D 信道与静音运行 3 节

| 编号 | 小章节 | 下一步阅读问题 | 优先相关输入 |
|---|---|---|---|
| 3.13 | JBM 与时延边界 | JBM 支持要求、方括号和 TS 26.114 注释怎样读？是否计入算法时延？ | 126；交叉 Step 2 §4.3 |
| 3.14 | PLC 与丢包鲁棒性 | 支持 PLC 与具体 loss-rate 要求如何区分？与 bundling、loss pattern 的依赖是什么？ | 184；交叉 Step 2、ULBC-7/8a |
| 3.15 | VAD DTX CNG 与 SID 行为 | SID interval、hangover、AFR 与 Rel-20 phasing 如何分工？哪些项仍 FFS？ | 097、100、117、122、134、163 |

### E 传输接口 1 节

| 编号 | 小章节 | 下一步阅读问题 | 优先相关输入 |
|---|---|---|---|
| 3.16 | RTP payload 与 header reduction | Codec payload、packetizer 与 protocol overhead 的边界是什么？哪些工作转交 ULBC-9？ | 169；交叉 174、178、179 |

### F 信号行为与验证 2 节

| 编号 | 小章节 | 下一步阅读问题 | 优先相关输入 |
|---|---|---|---|
| 3.17 | 降噪与非语音输入鲁棒性 | 是否保留为独立约束？与 ULBC-3 或 output gain tolerance 怎样分工？ | 184；交叉 121、180 |
| 3.18 | 输出增益容差与能量验证 | 频带、容差与测量工具如何定义？主观评分处理与运行时信号行为如何区分？ | 168；交叉 ULBC-3/7 |

## 5. R4 里的 topic 与原文条目并非一一对应

需要单独保留以下关联，避免误把贡献标题当成 ULBC-4 新条款：

- **111 decision sequence：** 作为 3.00 的决策依赖输入，不是 Table 1 的独立参数行。
- **096 → 164 → 169 rate/bundling switching：** 对应 3.04/3.05 共同阅读，不额外计一个原文参数。
- **132 profiling ONNX、133 complexity principles、095/160 RTF：** 都属于复杂度条目的不同分析层面。
- **139/154 model size：** 主要放在 3.11/3.12 的参数与存储核对中。
- **100 AFR：** R4 标为 postponed；Step 2 同时存在 AFR 主干与 122 的贡献，需要按文档区分状态，不能将 100 的延期状态套用于所有 AFR 内容。
- **123 DTMF：** R4 标为 postponed，184 当前 Table 1 未单列 DTMF 参数。先作为跨文档待查项，后续对照 ULBC-9 / R4 的 113，暂不加入 18 个技术章节。
- **141/144 overall constraints：** 在 3.00 建立整体视角，并在相关预算、时延章节交叉读取。

## 6. 建议的实际展开顺序

采用 **3.00 → 3.01–3.03 → 3.04–3.07 → 3.08–3.12 → 3.13–3.15 → 3.16–3.18** 的顺序。

每次先处理一个小章节，保持相同产出结构：

1. 主干原文及状态，精确到 T019 的行/列与 Note。
2. 术语、参数和测量口径。
3. 对应贡献的提案与前提。
4. 与主干的对应、与其他小章节/Pdoc 的依赖。
5. 已核实结论、未决问题和后续核对项。

本轮已按上述结构完成 A–F 六份分析。后续可逐份讨论或继续 ULBC-5/7/8a/9；本索引的“阅读问题”保留为各组的追踪问题。

## 7. 核对记录

使用用户指定的 `D:\Program\miniforge3\python.exe` 与标准库读取 ZIP 中的正文文件；已读取所有正文、表格、Definitions、版本历史和 References。文件有 2 张物理表，235 个插入节点、103 个删除节点；这些是 OOXML 结构数，不是独立议题数量。没有 comments.xml 批注。

当前 Markdown 显示现存修订文本并保留方括号、上标和合并信息；差异文件保留可识别的修订前/后文字。未修改原 ZIP，未做 DOCX 页面渲染。当前正文仍标 `draft`，页首 Tdoc 仍写 `S4aA26xxxx`，目录按 ZIP 来源识别为 184，暂不自行改写原文字。

## 8. 本轮来源与验证范围

已提取 184 主干以及 30 个相关贡献，另读取 141 ZIP 中的实际约束附件。F 复用 Step 2 的 168/121/180；本轮未替代后续 ULBC-9 全文分析。相关提取文件包含正文、表格、修订差异与批注信息；定位标记是提取索引，不是页码或正式条款号。

以 OOXML 内容和表格核对为主，未逐页渲染 DOCX，未复现实验、运行 codec 或独立核验图中曲线。原生公式对象及嵌入图不能保证被普通文本提取完整表达；分析采用明确可读的正文、表格及定义，不据此臆造图形数据。原始 ZIP/DOCX 保留。使用用户指定 Python 解释器完成提取与链接核对。
