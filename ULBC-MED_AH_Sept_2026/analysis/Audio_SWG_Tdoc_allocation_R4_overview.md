# Audio SWG Tdoc allocation R4 —  Overview 与 topic 分析路线

> 分析对象：`draft/Audio SWG Tdoc allocation R4.docx`。本文件基于 R4 的正文、议题表、状态图例、页眉和脚注整理。技术问题与阅读顺序是后续分析建议，不代表原文已经给出技术结论。初始 overview 仅核对了关联 ZIP 文件名；后续已完成 175/176 正文及 110/156/158 输入的 Step 1 分析，详见下方链接。Step 2 已完成 180 及相关性能贡献分析，Step 3 已按 A–F 完成 ULBC-4 的 18 个技术主题；其余四个主题亦完成，入口见下方。

> 2026-10-08 评审：已复核结论的证据范围、明确/待定状态及引用；详见[评审记录](Review_2026-10-08.md)。依据仍是本地 2026 年 9 月材料，不推定后续会议结果。


- [原文 Markdown](Audio_SWG_Tdoc_allocation_R4_source.md)
- 本地辅助文件：`Audio_SWG_Tdoc_allocation_R4_structure.json`（原始议题表结构；仅 Markdown 发布不包含该附件）
- [Step 1：ULBC-1 / ULBC-2 项目范围、阶段与时间线分析](step01_project_plan/Step01_ULBC1_ULBC2_analysis.md)（已完成）
- [Step 2：ULBC-3 性能要求分析](step02_performance_requirements/Step02_ULBC3_performance_analysis.md)（已完成）
- [Step 3：ULBC-4 章节清点与分析目录](step03_design_constraints/Step03_ULBC4_chapter_plan.md)（A–F 六份分析已完成，覆盖 18 个技术主题）
- [Step 6：数据集与训练/测试分离](remaining_topics/Topic06_datasets_and_separation.md)（已完成，含维护边界）
- [Step 7：测试与处理流程](remaining_topics/Topic07_testing_and_processing.md)（已完成，含 EVS 模板残留检查）
- [Step 8：资格与选拔规则](remaining_topics/Topic08_qualification_and_selection.md)（已完成，保留 FoM/程序 TBD）
- [Step 9：传输开销与既有系统集成](remaining_topics/Topic09_transport_and_system_integration.md)（已完成，含 179 本地 r1 对照）
- 分析日期：2026-10-05。

## 1. 这份文档是什么

这是一份 **Audio SWG 会议议程、Tdoc 分配及处理状态索引**。文内标题为 `Draft Audio SWG Agenda`，来源为 Audio SWG Chair，脚注注明 Tomas Toftgård（Ericsson LM），所属议程项为 2。页眉为 `3GPP TSG SA WG4 Audio SWG AH`，会议地点上海，时间 2026 年 9 月 28–30 日。开会时间为 28 日 09:00，最迟于 30 日 16:00 结束，均为会议当地时间。

文档先说明用途，再用一个三列表格列出议题编号、议题名称、分配文档。核心议题是 **4. ULBC-MED**，下设 4.1–4.10。其他部分包括开会、议程批准、IPR/反垄断/共识原则提醒、其他事项和闭会。

它可以回答“讨论了什么、哪些公司提交相关文档、各文档标了什么状态、编号转移到哪里”。技术阈值、完整提案、实验结果、修改后的规范条款需要阅读相应 Tdoc 正文，不能由议题标题推导出来。

## 2. 状态和编号怎么读

| 标记 | 原文含义 | 阅读时的处理 |
|---|---|---|
| `n` | noted | 已记录/知悉；不能据此认定提案已被采用 |
| `a` | agreed | 条目标记为同意；具体同意范围需核对对应正文及会议记录 |
| `p` | parked | 暂置 |
| `pl` | for plenary | 提交全会处理 |
| `pp` | postponed | 延期；继续保留为后续跟踪项 |
| `r` | revised | 修订 |
| `rp` | replied | 已回复 |
| `m` | merged | 合并；沿目标编号查找内容 |
| `w` | withdrawn | 撤回 |
| `app` | 图例未定义 | 出现在议程和日程条目；结合议题语境可能指 approved，但这是解释，需核实 |

`159->168a` 表示原文给出从 159 到 168 的编号转移，终点条目标为 `a`。Overview 用 `159 → 168 [a]` 提高可读性；箭头本身不证明两版文本一致，也不解释修订原因。

本文中的三位编号对应本地 `S4aA260xxx` 系列，例如 `168` 对应 `S4aA260168`。这一映射已通过相关本地 ZIP 文件名交叉核对，但不把短编号当作跨会议通用标识。

### 统计口径

按议题表内“以三位编号开头的一段”计数；一条编号转移链计为一条。ULBC-MED 共有 **76 条**有效编号条目：`n` 50 条、`a` 20 条、`pp` 5 条、`m` 1 条。另有带删除线且无状态的 `127`，单独保留，不计入 76 条。再加会议管理部分的 `129n`、`090app`、`091→165app`，全表共有 79 条有效编号条目。

统计是条目数，不是独立文档数、提案通过率或最终规范条款数；例如 `151` 合并到 `171`，不能当成两项独立技术成果。

## 3. 全局 topic 地图

| 议题 | Topic | 主干文档/入口 | 有效条目数 | 后续分析目标 |
|---|---|---|---:|---|
| 4.1 | 其他组/会议报告与联络 | 原文未列文档 | 0 | 若涉及外部依赖，再查联络函与会议记录 |
| 4.2 | 项目计划/时间线 | 175 `[a]` ULBC-1；176 `[a]` ULBC-2 | 5 | 理解项目阶段、里程碑和资格/选拔安排 |
| 4.3 | 性能要求 | 180 `[a]` ULBC-3 | 8 | 明确质量目标、场景和验证指标 |
| 4.4 | 设计约束 | 184 `[a]` ULBC-4 | 30 | 明确候选实现的参数、资源和运行边界 |
| 4.5 | 资格/选拔规则 | 182 `[a]` ULBC-5 | 8 | 明确如何判定资格与比较候选方案 |
| 4.6 | 交付物 | 原文未列文档 | 0 | 从主干文档中核对交付要求，不能因空白认定没有要求 |
| 4.7 | 处理计划 | 128 → 181 `[a]`，ULBC-7 v0.2.0 | 1 | 核对处理流程与可复现性要求 |
| 4.8 | 测试计划 | 157 → 167 `[a]`，ULBC-8a v0.1.0 | 8 | 明确实验、测试材料和数据覆盖 |
| 4.9 | RTP 头压缩与系统集成 | 179 `[n]` ULBC-9 | 8 | 分析传输开销及系统相关议题 |
| 4.10 | 其他：数据集、维护等 | 170、172、173 `[a]` 等 | 8 | 分析训练数据、数据要求和维护安排 |

ULBC-1/2/3/4/5/7/8a/9 的对应关系来自 R4 表内标注；R4 未在 4.6 列出 ULBC-6。后续 Step 1 从 175 / ULBC-1 v0.2.0 确认 ULBC-6 为 Deliverables，editor 为 Lei Li，并要求参加 selection 的候选完整、及时且合格地提供交付物；仍未找到其单独正文，R4 也未提供其状态。

从分析工作量看，4.4 最密集，应拆为带宽/采样率、资源/复杂度、码率切换、DTX、时延/帧长、DTMF/JBM 六组。4.10 虽名为 Other，但训练数据、数据要求与维护值得独立分析。

## 4. 各 topic 的文档索引与下一步问题

本节完整覆盖 4.2–4.10 的编号条目；仅原文已有状态写入方括号。中文说明用于导航，英文关键词保留以便检索。

### 4.2 项目计划与时间线

- **主干：** 175 `[a]` ULBC-1；176 `[a]` ULBC-2。
- **相关输入：** 110 `[n]` Huawei，qualification phase；156 `[n]` Fraunhofer，selection alternatives；158 `[n]` VoiceAge，qualification phase。
- **后续问题：** qualification 与 selection 各自解决什么问题？里程碑、提交条件、冻结点在哪里？不同选拔路径有什么前提？
- **建议产出：** 阶段—输入—输出—日期—依赖关系表。R4 没有列出这些日期，应从 ULBC-1/2 正文提取。

### 4.3 性能要求

| 子 topic | R4 文档索引 | 后续需要核对 |
|---|---|---|
| 总体要求 | 180 `[a]` ULBC-3；121 `[n]` Dolby，requirements/noise types；143 `[n]` Apple，requirements | 适用场景、比较基准、质量指标和要求措辞 |
| Tandeming（串接编解码） | 120 `[n]` Fraunhofer；162 `[n]` Lenovo/Motorola | 串接场景、参考链路与评价方法 |
| Quality stairs | 148 `[a]` Fraunhofer | 阶梯的具体定义、比较维度和要求 |
| SNR | 153 `[n]` Qualcomm | SNR 在提案中的定义、用途、计算方法 |
| 输出能量验证 | 159 → 168 `[a]` VoiceAge | 验证目的、测量方法与判定规则 |

**建议产出：** 要求矩阵，逐条记录场景、指标、基准、阈值、验证方法和出处。标题无法说明阈值，也无法确认所有输入均写入 180。

### 4.4 设计约束

主干文档为 **184 `[a]` ULBC-4**。先建立约束清单，再按下面的子 topic 对照贡献文档。

| 子 topic | R4 文档索引 | 后续需要核对 |
|---|---|---|
| 决策顺序 | 111 `[n]` Huawei | 哪些参数需先确定，后续约束如何依赖它们 |
| 采样率与音频带宽 | 101 `[n]` NTT/Panasonic；092 `[n]` vivo；118 `[n]` Huawei；149 `[n]` Fraunhofer；161 `[n]` Lenovo/Motorola | 输入/输出采样率、有效带宽、模式及条件如何区分 |
| RTF、复杂度与内存 | 095 `[n]` Spreadtrum/China telecom；102 `[n]` Samsung；115 `[n]` Huawei；132 `[n]` Fraunhofer（profiling ONNX）；133 `[n]` Fraunhofer（complexity principles）；138 `[n]` Nokia；160 `[n]` Lenovo/Motorola（RTF） | 测量平台、运行条件、统计口径和预算；RTF 与其他复杂度指标的关系 |
| 模型大小 | 139 `[n]` Nokia；154 `[n]` Qualcomm | 参数/文件大小的定义，以及与运行内存的区别 |
| Rate/bundling switching | 096 → 164 → 169 `[a]` vivo/Qualcomm | rate 与 bundling 分别指什么、切换机制及约束 |
| DTX、AFR、SID | 097 `[n]` vivo；100 `[pp]` vivo（AFR）；117 `[n]` Huawei；122 `[n]` Dolby；134 `[n]` Fraunhofer；163 `[n]` Ericsson（SID frames） | 静音时的发送机制、SID 行为及 AFR 的定义/统计口径 |
| 算法时延与帧长 | 116 `[n]` Huawei；155 `[n]` Qualcomm；136 `[n]` Fraunhofer | 时延组成、帧长、前视以及切换是否影响时延 |
| DTMF / JBM | 123 `[pp]` Fraunhofer（DTMF）；126 `[pp]` Fraunhofer（JBM） | 后续恢复讨论时需要解决的需求与边界 |
| 总体约束 | 141 `[n]` Orange；144 `[n]` Apple | 总体建议与 184 最终文本的对应关系 |

**建议产出：** “约束名称—最终措辞—数值/条件—测量方式—相关贡献—未决点”矩阵。R4 自身只支持主题分组与状态识别；184 主干中的接口、带宽、码率等已另在 Step 3 核对，资源与额外时延门槛仍有未决项。

### 4.5 Qualification / Selection rules

- **主干：** 182 `[a]` ULBC-5。
- **资源指标与权重：** 093 `[n]` vivo，complexity/memory FoM；094 `[n]` vivo，weighing factors。
- **测试材料分离：** 105 → 183 `[a]` Samsung，separate test material。
- **资格规则：** 135 `[n]` Nokia，qualification rules；150 `[n]` Fraunhofer，FoM qualification。
- **选拔与感知指标：** 147 `[a]` Orange，selection rules；152 `[n]` Fraunhofer，Perceptual FoM。
- **后续问题：** 哪些指标是资格门槛，哪些用于排序？FoM 的组成、归一化、权重和适用阶段是什么？材料分离如何与数据集管理衔接？
- **建议产出：** 资格判断流程、选拔比较流程和 FoM 定义表。公式与权重必须读取正文。

### 4.6 Deliverables

原文保留了该议题，但分配文档栏为空。下一步应从项目计划、处理计划、测试计划和数据集相关文档中核对交付内容、格式、版本、责任方与时间。此处不补写交付清单。

### 4.7 Processing plan

- 128 → 181 `[a]` Ericsson，ULBC-7 v0.2.0。
- `127` 带删除线，无明确状态。不能仅凭删除线把它解释成 withdrawn 或 merged。
- **后续问题：** 原始材料到测试输入的处理步骤是什么？哪些参数、工具、配置及版本需要统一？如何校验结果并复现处理过程？
- **建议产出：** 处理流程图和输入/输出/配置/检查项清单。实际流程需读取 181。

### 4.8 Test plan

| 子 topic | R4 文档索引 | 后续需要核对 |
|---|---|---|
| 测试计划主体 | 157 → 167 `[a]` ULBC-8a v0.1.0；145 `[n]` Apple/Samsung，qualification test plan | 资格测试与选拔测试的覆盖、方法和差异 |
| 实验设计 | 125 → 166 `[a]` Fraunhofer | 比较条件、实验组织及统计分析要求 |
| 客观评价数据库 | 119 → 177 `[a]` Fraunhofer | 数据库覆盖、使用条件与评价方法 |
| 噪声材料 | 114 `[n]` Panasonic，non-stationary noise；146 → 171 `[a]` Orange；151 `[m]` → 171 Fraunhofer，test samples | 噪声类别、材料收集及合并内容 |
| 语言覆盖 | 103 `[n]` Samsung | 语言覆盖目标与样本分配 |

**建议产出：** 测试矩阵与材料清单，并追踪每个性能要求是否存在对应测试。`151m→171` 表示合并路径，需读取 171 才能确认哪些内容被纳入。

### 4.9 RTP 头压缩与系统集成

- **主干：** 179 `[n]` ULBC-9；注意该条在 R4 中不是 `a`。
- **头部与开销：** 098 → 178 `[a]` vivo，header reduction；104 → 174 `[a]` Samsung，header analysis。
- **规范与传输：** 109 `[n]` Qualcomm，CR 26.940；124 `[n]` Fraunhofer，IP and RoHC；130 `[n]` China Mobile，transport options。
- **延期项：** 112 `[pp]` Qualcomm，delay characteristics；113 `[pp]` Qualcomm，DTMF。
- **后续问题：** codec payload 与传输头开销分别占多少？bundling、发送频率和压缩机制如何影响实际传输？时延和 DTMF 在系统层面需要哪些处理？
- **建议产出：** 端到端数据路径、开销计算假设表和规范影响列表。R4 没有提供包头字节数、收益或 CR 修改内容。

### 4.10 数据集与维护

- **训练数据及共用数据：** 099 → 170 `[a]` vivo；107 `[n]` Samsung，training data；108 `[n]` Samsung，prepare common data；137 `[n]` Nokia，training data for codecs；106 `[n]` Samsung，training data deliverables。
- **数据处理与要求：** 131 `[n]` Dolby/Novamint/Verizon，handling datasets；142 → 173 `[a]` Nokia，dataset requirements。
- **维护：** 140 → 172 `[a]` Nokia，maintenance。
- **后续问题：** 数据来源、允许用途、训练与测试分离、公共数据准备及交付边界是什么？维护提案针对哪些对象、流程和版本？
- **建议产出：** 数据集生命周期与责任矩阵。尤其需要与 4.5 的材料分离、4.8 的测试材料交叉核对。

## 5. 优先读取的编号转移与主干文件

以下入口链接改为仓库中可阅读的原文 Markdown。原始 ZIP 位于本地 `doc/`，179 DOCX 位于 `draft/`，本次仅 Markdown 发布不包含它们。ZIP 内存在 clean/redline 或 cl/rm 版本时，先读 clean/cl 建立基线，再读标记版了解修改；不能仅凭文件名认为版本内容完全等价。

| Topic | 推荐入口 | R4 状态 | 可阅读来源 |
|---|---|---|---|
| 开发概览 | 175 / ULBC-1 | a | [S4aA260175 原文 Markdown](step01_project_plan/S4aA260175_clean_source.md) |
| 时间线 | 176 / ULBC-2 | a | [S4aA260176 原文 Markdown](step01_project_plan/S4aA260176_clean_source.md) |
| 性能要求 | 180 / ULBC-3 | a | [S4aA260180 原文 Markdown](step02_performance_requirements/S4aA260180_source.md) |
| 设计约束 | 184 / ULBC-4 | a | [S4aA260184 原文 Markdown](step03_design_constraints/S4aA260184_source.md) |
| 资格/选拔规则 | 182 / ULBC-5 | a | [S4aA260182 原文 Markdown](remaining_topics/sources/S4aA260182_source.md) |
| 处理计划 | 128 → 181 / ULBC-7 | a | [S4aA260181 原文 Markdown](remaining_topics/sources/S4aA260181_source.md) |
| 测试计划 | 157 → 167 / ULBC-8a | a | [S4aA260167 原文 Markdown](remaining_topics/sources/S4aA260167_source.md) |
| 输出能量验证 | 159 → 168 | a | [S4aA260168 原文 Markdown](step02_performance_requirements/S4aA260168_source.md) |
| 码率/bundling 切换 | 096 → 164 → 169 | a | [S4aA260169 原文 Markdown](step03_design_constraints/S4aA260169_source.md) |
| 测试材料分离 | 105 → 183 | a | [S4aA260183 原文 Markdown](remaining_topics/sources/S4aA260183_source.md) |
| 实验设计 | 125 → 166 | a | [S4aA260166 原文 Markdown](remaining_topics/sources/S4aA260166_source.md) |
| 客观评价数据库 | 119 → 177 | a | [S4aA260177 原文 Markdown](remaining_topics/sources/S4aA260177_source.md) |
| 噪声材料 | 146 → 171；151 m → 171 | a / m | [S4aA260171 原文 Markdown](remaining_topics/sources/S4aA260171_source.md) |
| 系统集成主干 | 179 / ULBC-9 | n | [S4aA260179 原文 Markdown](remaining_topics/sources/S4aA260179_source.md) |
| 头部压缩更新 | 098 → 178 | a | [S4aA260178 原文 Markdown](remaining_topics/sources/S4aA260178_source.md) |
| 头部分析 | 104 → 174 | a | [S4aA260174 原文 Markdown](remaining_topics/sources/S4aA260174_source.md) |
| 训练数据 | 099 → 170 | a | [S4aA260170 原文 Markdown](remaining_topics/sources/S4aA260170_source.md) |
| 维护 | 140 → 172 | a | [S4aA260172 原文 Markdown](remaining_topics/sources/S4aA260172_source.md) |
| 数据要求 | 142 → 173 | a | [S4aA260173 原文 Markdown](remaining_topics/sources/S4aA260173_source.md) |

还有 `091 → 165 [app]` 的会议日程转移。该项属于会议管理，暂不纳入技术阅读路线。

## 6. 建议的 step-by-step 分析顺序

这份路线是为了建立理解依赖而安排的阅读顺序，属于分析建议，不是会议原定处理顺序。

**后续目录调整：** 按用户要求，将原路线 Step 3–5 中的 ULBC-4 内容统一放入 Step 3 总任务，拆为 3.00 前导与 3.01–3.18 共 18 个技术小章节。下表保留最初的主题安排，实际展开以 Step 3 新目录为准；不重复分析相同内容。

| Step | 分析范围 | 优先文档 | 完成标志 |
|---:|---|---|---|
| 1 | 项目范围、阶段与时间线（4.2） | 175、176；再对照 110/156/158 | 能说明项目目标、阶段、里程碑和进入条件 |
| 2 | 性能要求（4.3） | 180；再对照 148/168 等 | 每个要求都有定义、场景、基准和验证出处 |
| 3 | 采样率/带宽与决策依赖（4.4） | 184；111/101/092/118/149/161 | 形成明确的接口与模式参数表 |
| 4 | 复杂度、RTF、内存、模型大小（4.4） | 184；095/102/115/132/133/138/139/154/160 | 分清测量指标、平台条件和预算 |
| 5 | 时延、帧长、切换与 DTX（4.4） | 184、169；116/155/136/097/117/122/134/163 | 描述运行模式及其关联约束；AFR/DTMF/JBM 单独跟踪 |
| 6 | 数据集与训练/测试分离（4.10 + 4.5） | 170、173、183；107/108/131/137/106 | 明确数据来源、使用边界和交付责任 |
| 7 | 测试与处理流程（4.8 + 4.7） | 167、181、166、177、171；145/114/103 | 能把要求映射到数据、处理步骤和实验 |
| 8 | 资格与选拔规则（4.5） | 182、147；093/094/135/150/152 | 分清门槛与排序，核对 FoM 定义与适用阶段 |
| 9 | 传输开销与系统集成（4.9） | 179、178、174；109/124/130 | 建立开销模型与系统/规范影响清单 |
| 10 | 交付、维护和未决项（4.6 + 4.10） | 172，并交叉核对主干文档 | 形成交付清单、维护安排与未决问题列表 |

每一步建议遵循同一分析流程：

1. **读取终点版本/主干正文**：先列出范围、术语、明确要求和开放问题，记录文档编号、版本、章节及表号。
2. **核对相关贡献**：提取具体提议、理由、数据与修改文本；必要时沿旧编号比较变化。
3. **对照主干**：逐条确认哪些内容已经写入主干，哪些仅是相关输入；区分议程状态与条款落实情况。
4. **分析影响和依赖**：说明对 codec、数据、测试、资源、传输或流程的影响，只使用已核实的前提。
5. **输出结论与待核实项**：形成 topic Markdown，保留证据定位和不确定性，更新统一跟踪表。

## 7. 后续 topic Markdown 模板

```markdown
# Topic XX — 主题名称

## 分析范围与来源
- R4 议题编号：
- 主干文件 / 版本 / 章节：
- 贡献文档 / 编号链 / 议程状态：

## 术语与当前基线
明确术语定义，列出主干文本中的要求；每条记录章节或表号。

## 各方提案与证据
按文档提取问题、提议、理由、数据和建议修改；区分原文与分析解释。

## 与主干文本的对应
逐条记录：已写入 / 部分对应 / 未找到 / 待核实。状态 a 或 n 单独记录。

## 技术影响与依赖
说明指标、参数、测试或流程之间的关系，并标明分析假设。

## 结论与下一步
- 已核实结论：
- 分歧 / 未决项：
- 需要补查的材料：
```

## 8. 核对记录与解释边界

- 已检查全部正文和议题表内容，连同页眉及实际脚注；没有图片/绘图，没有 OOXML tracked insertion/deletion，也没有 comments.xml。
- `096 → 164 → 169` 的第二个箭头来自 Word 的 Wingdings `F0E0` 符号，转换时显式保留，避免普通文本提取误写为 `164169`。
- `127` 的删除线来自 run 格式，并非修订删除记录，转换为 `~~127~~`。
- 保留 `151m→171` 的合并语义，保留五项延期记录：100、123、126、112、113。
- 原文保留 Draft 标题，因此本 overview 不把该议程索引当成完整正式会议纪要。
- Markdown 是内容与结构转换，未复刻原 DOCX 的颜色、字体或页面布局；本次核对基于 OOXML，没有开展逐页渲染视觉检查。
- 关联 draft 文件可能是早期版本或 online edits。深入分析优先核对终点编号 ZIP 的版本与正文，避免直接把旧稿内容当成终点版本。

**进度：Step 1 已完成。** 175/176 已同意采用的当前工作假设为跳过独立 qualification、直接 selection；已记录 LoI/交付物条件、计划时间线与未决项。详见 Step 1 分析。**Step 2 也已完成。** 180 是保留方括号及多套提案的性能要求基线，已建立场景矩阵、来源对照与 16 项追踪表。**Step 3 本轮分析已完成：** 原文 6 个大章、15 个设计约束条目，拆为 18 个技术主题并按 A–F 输出六份 Markdown；3.00 共同读法与依赖放在总索引。保留所有未决门槛和贡献分歧，不将分析完成等同于规范定案。


**本轮新增四主题分析已完成。** 数据集主题覆盖 170/173/183、训练透明度/再生成提案和 172 维护目标；测试主题核对 167/181、166/177/171 及模板残留；规则主题核对 182 和 FoM 输入；传输主题完整读取本地 179 并对照 r1、174/178、124/130 与延期项。分析完成不代表文档中的 TBD/FFS 已解决。

原路线 Step 10 的维护方向已在数据集主题中分析，交付义务已交叉覆盖；完整 ULBC-6 独立主干正文仍缺失，不能据现有材料补造正式完整交付清单。本轮来源正文及修订提取位于 `remaining_topics/sources`；四份文件之间已建立交叉链接。
