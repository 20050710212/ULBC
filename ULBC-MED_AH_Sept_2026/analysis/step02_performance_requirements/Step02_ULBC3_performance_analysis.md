# Step 2 — ULBC-3 v0.2.0 性能要求分析

> 主干：S4aA260180 / ULBC-3 v0.2.0；R4 议题 4.3，标记 `a`。分析日期：2026-10-05。本报告分析本地会议版本，不判断后续版本或实际测试结果。先保留原文的方括号、合并提案与未决点，再建立要求索引。

- [180 原文 Markdown](S4aA260180_source.md)
- [180 tracked-before → 当前文字的修订差异](S4aA260180_changes.diff)
- [返回总体 Overview](../Audio_SWG_Tdoc_allocation_R4_overview.md)

## 1. 先读懂这份主干的成熟度

**180 是性能要求的合并工作基线，尚不能直接变成单一最终验收标准。** §4.1、§4.2、§5.1、§5.2 均有方括号包围，§4 开头明确表示 WB 与 SWB 是否分别设要求仍在讨论；不少单元格同时保留多组参考门槛、FER 和 AFR 表达式，SWB 表的 Requirements / Objectives 列为空。[180 §4 编辑注](S4aA260180_source.md#P037)

文档历史说明：v0.1.1 于 2026-09-29 合并 120、162、121、122、143、148、153 的提案，v0.2.0 于 09-30 基于该合并版本进行会中 online updates。R4 的 `a` 是整份文档的议程状态，不能抹去正文中的方括号或证明每个备选提案均获采用。[180 History](S4aA260180_source.md#T127)

当前能清楚建立的是：

1. **主观质量评价：** 以参考 codec / DIRECT 比较，覆盖 clean/noisy speech 与信道损失，并讨论 quality stairs。
2. **互通质量：** 与 AMR-WB、EVS 串接，比较链路与测试阶段存在多套方案。
3. **客观行为评价：** DTX 的 AFR，以及非活动语音区间的背景噪声衰减。
4. **处理与测试依赖：** 输入电平、SNR、损失模式、同步、DTX 模式、统计判定与测量工具必须由相关 Pdoc 补齐。

**最关键的未决项：** 1.0/1.4 kbps 各自的门槛、WB/SWB 区分、FER 点集、DTX on/off 的测试范围、串接是否进入 selection、AFR 的参考与容差，以及噪声衰减阈值。

## 2. 阅读来源与判读方法

| 文档 | 来源 / R4 状态 | 在本步的用途 |
|---|---|---|
| [180](S4aA260180_source.md) | ULBC-3 editor / `a` | 完整主干、12 张物理表、修订文字与 23 条批注 |
| [148](S4aA260148_source.md) | Fraunhofer / `a` | Quality stairs 的目的和提案 |
| [168](S4aA260168_source.md) | VoiceAge / `a`，159 → 168 | 输出能量验证的范围与工具归属 |
| [120](S4aA260120_source.md) | Fraunhofer / `n` | FER 与串接参考构造 |
| [162](S4aA260162_source.md) | Lenovo/Motorola / `n` | 将串接测试提前到选拔阶段的提案 |
| [121](S4aA260121_source.md) | Dolby / `n` | 质量门槛、噪声类别、DTX 与噪声衰减 |
| [143](S4aA260143_source.md) | Apple / `n` | 1.0/1.4 kbps 门槛及参考 codec 列表 |
| [153](S4aA260153_source.md) | Qualcomm / `n` | 固定 noisy-speech SNR 的提案 |
| [122](S4aA260122_source.md) | Dolby / `n`，R4 位于 4.4 | 主干历史与批注明确引用其 AFR 提案，故纳入本步 |

判读分成“正文记录的通用表述”“主干中存在但有方括号/冲突的条目”“贡献文件中的提案”和“本报告分析”四层。出现于合并主干只证明该文字被纳入讨论，不自动等于定案。

原文多次重复 Table 1 / Table 2。为避免误引，本报告使用提取标记 T018、T041 等定位；例如 T041-R02-C07 是按正文顺序提取的表、行、列编号，**不是原文正式条款号或页码**。

## 3. 术语与总体判定原则

| 术语 | 这里应如何读 |
|---|---|
| Requirements | 表格中的性能要求栏；当前有不少未决或合并内容 |
| Objectives | 目标栏，与最低要求分开；148 明确提出用 stairs 补充最低门槛 |
| NWT | Not Worse Than，143 正文明确展开；即“不劣于”对应参考条件 |
| DIRECT | §1 原文使用的比较条件，本文件未给出其构建、滤波、带宽及电平处理细节 |
| FER / BLER | 主干不同表分别使用这两个标签；当前未提供两者的映射，不能自动视为同一量 |
| DCR / ACR | 原文分别引用的 P.800 主观测试方法标签；不能直接混合其评分或统计结果 |
| AFR | Active Frame Ratio，§5.1 定义的活跃帧比例 |
| CuT | 原文用于被测 codec 的标签；在本报告中称被测候选 |

### 所有要求与目标都有 DIRECT 备选表述

180 §1 明确写道：所有 requirements / objectives 都应包含 **“OR NWT DIRECT (in the respective input bandwidth)”**。这是读任何表格时都要带上的限定，不能只复制参考 codec 名称而漏掉 DIRECT 分支。[180 §1](S4aA260180_source.md#P012)

阅读上可把某项参考比较概括为“满足该参考比较 **或** 在相应输入带宽下 NWT DIRECT”；但具体适用方式、DIRECT 制备及统计检验仍需测试/处理/选拔规则定义。这份文档没有提供 NWT 的置信水平、容许差异、显著性检验或 pass/fail 算法，不能用“平均 MOS 大于等于参考”替代完整判定。特别是这一通用句怎样适用于 §5 的 AFR/能量客观要求，当前文字并未解释；不能自行用主观 NWT DIRECT 替代客观检查。

## 4. 参考 codec：最低比较、anchors 与互通不能混为一谈

| 位置 | 当前表中文字 | 需要保留的限定 |
|---|---|---|
| §2.1，T018 | AMR-WB；操作点 `[8.85、12.65 kbps]`；`[EVS]` / `[EVS-WB 7.2、13.2]`；`[AMR]` / `[12.2]` | AMR-WB 名称未括起，但其使用说明有方括号；其余 codec 名称也括起 |
| §2.2，T023 | `[AMR-WB]`、`[EVS]`、`[AMR]` 及同类操作点 | 互通参考表整体保留较多未决标记 |
| §4.1 Objectives / 148 | AMR-WB 12.65、14.25、15.85；EVS-WB 13.2 | 用于 quality stairs 的目标，不能全部当成最低要求 |
| §4.2 | AMR-WB 12.65、EVS-SWB 13.2 的串接链路 | EVS-WB 与 EVS-SWB 是不同的表内标识，不能统一缩写后误读 |

证据：[180 §2.1](S4aA260180_source.md#T018)、[§2.2](S4aA260180_source.md#T023)、[§4.1](S4aA260180_source.md#T041)、[§4.2](S4aA260180_source.md#T073)。

## 5. 主观性能要求矩阵：先拆场景，再核对门槛

### 5.1 测试条件与仍有分歧的参数

| 维度 | 当前 180 文字 | 成熟度 / 下一步 |
|---|---|---|
| ULBC 码率 | 表中使用 1.0、1.4 kbit/s | 可作为本次要求表的工作操作点；设计参数还需核对 ULBC-4 |
| 带宽 | WB 表中仍保留 SWB/WB/WB 文字；另列 SWB 表 | §4 编辑注确认拆分仍在讨论 |
| 无损 clean speech 电平 | -36、-26、-16 dBov | §3 编辑注记录 SA4#137-e 同意该电平测试；语句仍包含 qualification |
| 损失信道 clean speech 电平 | -26 dBov | 存在于方括号要求表中 |
| Noisy speech 电平 | -26 dBov | 噪声类别、SNR 与测试方法尚未统一 |
| Bundling | 1.0：`[80ms/160ms]`；1.4：80ms | 不把 bundling 时间等同于 frame size 或完整算法时延 |
| FER 点集 | 同格出现 `2%,6%`、`1%,6%`、`[1%,2%,6%,10%]` | 不能任选一组作为全部场景最终点集 |
| DTX | 多张表写 On/Off；备注又写 selection 预期 DTX On only | 测试覆盖范围待统一；参考 codec 备注写 DTX on |
| 损失模式 | 代表 NB-IoT NTN over GEO，按 TR 26.940 原则生成 packet loss patterns | 不能只用相同平均损失百分比替代指定模式 |

证据：[180 §3](S4aA260180_source.md#P029)、[WB 表](S4aA260180_source.md#T041)、[损失模式](S4aA260180_source.md#P047)、[DTX 备注](S4aA260180_source.md#P053)。

### 5.2 WB 要求栏里的参考门槛

以下是 **T041 Requirements 单元格内容的去重索引**，不是替会议选定最终门槛。对损失场景保留 `@x FER` 的有无差异；重复提案不计为多个独立要求。每行还应带上 §1 的 DIRECT 分支。

| 场景 | 1.0 kbps 栏当前内容 | 1.4 kbps 栏当前内容 |
|---|---|---|
| Clean speech，FER=0 | NWT AMR-WB 12.65；NWT AMR-WB 8.85 | NWT AMR-WB 12.65；NWT AMR-WB 15.85；NWT EVS-WB 13.2 |
| Clean speech，FER=x | NWT AMR-WB 12.65 @x FER；NWT AMR-WB 8.85（此处未写 @x FER） | NWT AMR-WB 12.65 / 15.85 / EVS-WB 13.2，均带 @x FER |
| Noisy speech，FER=0 | NWT AMR-WB 12.65；NWT AMR-WB 8.85 | NWT AMR-WB 12.65；NWT EVS-WB 13.2 |
| Noisy speech，FER=x | NWT AMR-WB 12.65 / 8.85，均带 @x FER | NWT AMR-WB 12.65 / EVS-WB 13.2，均带 @x FER |
| Mixed content / music，FER=0 | Graceful behaviour | Graceful behaviour |

证据：[T041-R02–R11](S4aA260180_source.md#T041)。这里最重要的区别是：1.0 kbps 的 8.85 与 12.65、1.4 kbps 的 12.65/15.85/EVS 13.2 来自不同意见，不能仅因它们出现在同格就把它们解释成必须同时满足的多个门槛。

Mixed content/music 的 graceful behaviour 仍是 `[Graceful behaviour means …]` 占位文字；主干预期在 characterization 检查。它没有给出可执行的通过阈值。[180 备注](S4aA260180_source.md#P046)

### 5.3 Dolby 另一套条件表：与 WB 主表并存

T050 由批注 `DLB(121)` 标出，其行内容不能覆盖或消除 T041。

| 条件 | T050 当前文字 |
|---|---|
| 1.0 kbps，clean/noisy speech，零损失或 noisy channel | NWT AMRWB 12.65 kbps |
| 1.4 kbps，clean/noisy speech，零损失或 BLER <6% | NWT AMRWB 12.65 kbps |
| 1.4 kbps，clean/noisy speech，BLER ≥6% | **NWT AMRWB-IO 12.65 kbps** |

121 原贡献在 ≥6% 条件下写的是 **BT AMRWB 12.65 kbps**；180 当前文字改为 **NWT AMRWB-IO**。180 没有解释 `-IO` 的含义，不能自行改回 BT，或擅自把它解释为某种 codec 模式。[180 T050](S4aA260180_source.md#T050)、[121 提案表](S4aA260121_source.md#T042)

同一贡献强调：额外的 0.4 kbps 应体现于信道鲁棒性，并扩展 sirens、forest noise、general audio/music 等测试。180 保留了这些噪声类别的 ACR 提议，但 §3 的表仍引用 DCR，两种方法的范围与对照关系需要测试计划统一。

### 5.4 SWB：目前是空白门槛框架

T065 列出 1.0/1.4 kbps、clean/noisy speech、零/非零 FER、bundling 和 DTX 等维度，**Requirements 与 Objectives 列没有具体内容**。这不证明 SWB 没有要求，而说明这个主干版本尚未填写其具体比较门槛。[180 SWB 表](S4aA260180_source.md#T065)

## 6. Noisy speech：噪声、SNR 与损失是三条不同轴

- **噪声类型：** 180 §3 列 car（stationary）、street/office（non-stationary）。T041/T105 还并存 car/office/street 与 car/street 两组文字；Dolby 扩展提议另有 sirens、forest noise、general audio/music。
- **SNR：** §3 同格保留 car 的 15–20 dB 范围与 `[20 dB]`，street/office 的 20–25 dB 范围与 `[25 dB]`；T041/T105 又有 SNR=20 dB 的旧文字。没有统一成最终的每类噪声值。
- **信道损失：** noisy speech 可以再叠加 FER/BLER 条件；不能把背景噪声和丢包都归为同一类 noisy condition。

153 提议固定为 car 20 dB、street/office 25 dB，理由是 codec 输入应对应前端降噪后的残余噪声。180 的批注 `QC(153)` 对应这两个新增括号值；**出现于主干且仍有方括号**。[153 提案](S4aA260153_source.md#T027)、[180 SNR 表](S4aA260180_source.md#T032)

120 提议取消 10% FER，理由是其认为 6% 已代表较差服务条件；180 当前仍保留包含 10% 的点集，所以不能写成“10% 已正式取消”。[120](S4aA260120_source.md#P010)

分析影响：确认测试矩阵时应逐项记录“speech/noise material → 输入电平 → SNR → bundling/ptime → loss pattern → DTX → reference processing → subjective method”。目前这些维度没有全部冻结，不能直接将每个列表做笛卡尔积计算最终实验数。

## 7. Quality stairs：最低门槛之外如何比较好坏

148 的目标是：候选都越过最低 pass/fail 门槛后，再用 AMR-WB/EVS anchors 提升候选区分能力、跨条件/实验室比较能力，并为 FoM 聚合提供参照。**148 明确表示不修改已有最低要求。** 这些效果是贡献中的论证，不是本次独立实验验证。[148 Motivation](S4aA260148_source.md#P012)、[Conclusion](S4aA260148_source.md#P045)

其 stairs 为 AMR-WB 12.65、14.25、15.85 与 EVS-WB 13.2。180 将相关文字合并进 T041 Objectives 栏，批注 `FhG(148)` 标明来源。主干还保留 **“Objective not relevant for 1.4 kbps”** 备注，但 1.4 行仍可看到复制的 stairs 内容，后续应统一表与备注。[180 Objectives](S4aA260180_source.md#T041-R02-C08)、[1.4 备注](S4aA260180_source.md#P043)

原文中的 `12.65` 后带上标 `1`，指向该备注；转换版保留 `<sup>1</sup>`。不能误读为 **12.651 kbps**。

本报告的分析：最低门槛解决“是否达标”，stairs 用于进一步比较“达标之后相对 anchors 的位置”。但是 FoM 公式、跨条件权重、NWT 判断、anchors 的损失/DTX 配置尚未由此文档完整定义，需与 ULBC-5、ULBC-8a 对照。

## 8. Tandeming / interworking：三个版本并列的议题

180 §4.2 被方括号包围，同时保留三张表，不能直接当成三组同时生效的独立规范。

| 方案/表 | 参考比较方式 | 测试阶段/未决项 |
|---|---|---|
| T073：原有串接表 | ULBC 与 AMR-WB 12.65 / EVS-SWB 13.2，双向串接，codec 间 Linear 16 PCM；两码率要求 NWT AMR-WB 12.65 自串接，目标栏分别有 AMR-WB/EVS 自串接 | 备注为 characterization；同步交给 processing plan |
| T081：Fraunhofer 120 | 同一 legacy codec 与“ULBC 对应码率/带宽的性能参考 codec”串接，作为比较参考 | 把串接门槛与单 codec 的 WB/SWB 门槛关联；这些主门槛仍待定；备注为 characterization |
| T084：Lenovo/Motorola 162 | 至少 ULBC–AMR-WB 12.65 串接，参考 self-tandeming；EVS 部分仍带方括号、目标栏保留括号 | 明确主张在 qualification、selection、characterization 测试；与主干其他表的阶段安排不一致 |

证据：[180 T073](S4aA260180_source.md#T073)、[T081](S4aA260180_source.md#T081)、[T084](S4aA260180_source.md#T084)。

120 的问题是：旧门槛未体现两码率差异，且 SWB 的串接最低要求不足；它提出沿用相应 WB/SWB 门槛来构造串接 reference。[120 一般规则](S4aA260120_source.md#P020)

162 的问题是：卫星 ULBC 与 legacy/紧急呼叫互通十分重要，因此不应等获胜后 characterization 才首次测试；其互通门槛仍写 FFS。[162](S4aA260162_source.md#P020)

**跨 Step 1 的冲突：** 175/176 当前工作假设跳过独立 qualification，但 180 的 general/tandeming 文字仍包含 qualification。应核对哪些是历史文字、哪些代表需要继续执行的 selection 检查，不能据此认为资格阶段恢复。

## 9. Delay-loss 与 JBM 的边界

§4.3 说明，包含 NB-IoT GEO 的代表性端到端损失/时延性能已纳入 §4.1 的 clean/noisy FER 条件；**未定义 ULBC 的专门 JBM 要求**。[180 §4.3](S4aA260180_source.md#P091)

这句话不等于不需要处理抖动或迟到包，也没有给出算法时延数值。121 中“decoder 可以看未来一个 bundle（假设其已在 jitter buffer）”属于 design-constraint 提案，需在 ULBC-4 步骤核对；不能直接把该能力当作 180 已确定的时延要求。

## 10. AFR：客观 DTX 指标及容差未决

### 定义与材料

180 §5.1 给出的定义是：

```text
AFR(%) = 100 × 非 SID 且非 NO DATA 的帧数 / DTX-off 运行时的帧数
```

计算不含测试 preamble；数据为约 10–30 分钟 speech/noisy speech，P.56 clean-speech 活跃度约 40%；noisy speech 从对应 clean speech 加噪构造。详细 objective evaluation 交给 processing plan。[180 定义](S4aA260180_source.md#P098)、[材料](S4aA260180_source.md#P102)

这里“材料约 40%”描述测试数据库构造目标，**不是要求所有候选 AFR 必须等于 40%**。

### 三组参考表达式仍在同一要求格中

| 当前文字 | 解释边界 |
|---|---|
| `AFR(ULBC) < AFR(AMR-WB) + 1%` | 旧表达式；未在本格完整指定参考码率/材料 |
| `AFR(ULBC-MED) < AFR(EVS) + 1` | 未标注这个 1 的单位，不能擅自改写成最终容差 |
| `AFR(ULBC) ≤ AFR(AMR-WB@12.65, clean speech) + [x]%` | Dolby 122 加入；使用对应 clean speech 参考；`[x]` 未定 |

§5.1 整段有方括号，上述表达式不能被合并成最终的三重通过条件。[180 AFR 表](S4aA260180_source.md#T105-R02-C06)

122 明确提议容差是 **percentage points**，意图避免使用 legacy codec 在噪声下偏保守的 VAD 所产生的高 AFR 作为宽松参考。[122 Proposal 3](S4aA260122_source.md#P034)

计数需使用相同 ptime：一个 bundle 内任意一帧 active，整个 bundle 计为 active。[180 ptime 注](S4aA260180_source.md#P107) 因此实现比较时需统一计数单位，不能拿 codec 内部小帧计数与 bundle 计数直接对比。AFR 也不统计全部 SID 传输开销，不能直接当成最终链路码率或功耗；SID 更新间隔需在设计约束/系统集成中核对。

## 11. 非活动区背景噪声衰减：阈值保留方括号

§5.2 比较 inactive regions 的输入背景噪声与解码输出，要求输出不要过度衰减。这里限定 **-26 dBov**。

| 场景 | DTX Off | DTX On | 当前成熟度 |
|---|---:|---:|---|
| Clean speech 的非活动区 | 最大衰减 `[6] dB` | 最大衰减 `[12] dB` | 整节与阈值均有方括号 |
| Noisy speech，各测试 noise type 的非活动区 | 最大衰减 `[4] dB` | 最大衰减 `[12] dB` | 整节与阈值均有方括号 |

测量 clean speech 时忽略极低能量的录音背景噪声帧。[180 §5.2](S4aA260180_source.md#P113)

“最大衰减”限制降噪/门控的程度，不能把 `[6] dB` 改成“至少降低 6 dB”。窗口、inactive-region 划分、低能量排除阈值、聚合方式等尚未在本节定义，需要 ULBC-7 工具说明。

### 168：哪些输出能量行为应做客观验证

168 的最终提案明确分配如下：[168 Proposals](S4aA260168_source.md#P023)

| 验证方面 | 168 提案的方法 | 与 180 对应 |
|---|---|---|
| 输出相对输入的最大放大 | ULBC-7 objective tool | 180 未提供专门的完整阈值/方法 |
| 最低 WB 带宽 / 带内最大衰减 | 不用专门 objective tool；预期由合适的 P.800 DCR 隐式验证 | WB 范围 7 kHz/8 kHz 仍是 168 提出的待澄清项 |
| 输入不存在的高频部分人工带宽扩展/最大放大 | ULBC-7 objective tool | 180 没有对应完整量化条款 |
| Inactive clean speech 最大衰减 | ULBC-7 objective tool | 对应 180 §5.2 的括号阈值 |
| Inactive noisy speech 最大衰减 | ULBC-7 objective tool | 对应 180 §5.2 的括号阈值 |

168 还讨论是否用 BS.1770/P.56 缩放输出以避免主观评分被增益影响，但未在其最终提案中选择一个具体缩放工具。本步不把“讨论过缩放”写成“已确定输出归一化”。

168 在 R4 标记 `a`，但 180 的 History 合并来源列表未列出 168，本次也未发现 §5.2 之外覆盖全部能量验证的文字；**议程同意与逐条落实到 180/ULBC-7 是两个需要分别核对的问题。**

## 12. 要求追踪表：后续每步要补齐什么

下面的编号为本报告自建追踪 ID，不是原文要求编号。

| ID | 范围 / 当前指标 | 主要来源 | 当前缺口 / 后续落点 |
|---|---|---|---|
| PR-01 | 通用 `OR NWT DIRECT` | §1 P012 | DIRECT 制备与 NWT 判定：ULBC-7/8a/5 |
| PR-02 | clean speech 三输入电平 | §3 P030 | 测试材料/归一化与执行范围：ULBC-7/8a |
| PR-03 | 参考 codec / 操作点 | §2 T018/T023 | 方括号与 anchors/最低门槛分工：ULBC-3/8a |
| PR-04 | WB clean speech，1.0 | §4.1 T041 R02/R04 | 8.85 vs 12.65；FER 配置：ULBC-3/8a |
| PR-05 | WB clean speech，1.4 | T041 R03/R05 | 12.65/15.85/EVS 13.2：ULBC-3 |
| PR-06 | WB noisy speech，两码率 | T041 R06–R09 | 门槛、类别、SNR：ULBC-3/8a |
| PR-07 | FER/BLER、损失模式 | T041/T050/P047 | 点集、映射、模式：ULBC-7/8a |
| PR-08 | DTX On/Off 及 reference DTX | T041/P045/P053 | On-only 范围与阶段：ULBC-8a |
| PR-09 | SWB 质量门槛 | T065 | Requirements/Objectives 空白：ULBC-3/4 |
| PR-10 | Quality stairs | T041/P043、148 | 1.4 适用性、FoM、统计方法：ULBC-5/8a |
| PR-11 | Mixed content/music | T041/P046/P048 | Graceful behaviour 未定义：ULBC-3/characterization |
| PR-12 | Tandeming / interworking | T073/T081/T084 | 三套 reference、阶段、同步：ULBC-3/7/8a |
| PR-13 | Delay-loss / JBM | §4.3 P091 | 专门 JBM 要求未定义；对照 ULBC-4/9 |
| PR-14 | AFR | §5.1 T105/P107、122 | 参考、`[x]`、单位、ptime：ULBC-3/7/8a |
| PR-15 | Inactive noise attenuation | §5.2、168 | `[6]/[12]/[4]`、窗口与排除方法：ULBC-3/7 |
| PR-16 | Active gain / 人工高频扩展 | 168 | Objective tool、阈值与归一化：ULBC-4/7 |

## 13. 文档一致性与后续阅读顺序

优先核对以下事项：

1. **质量门槛先统一：** 1.0/1.4 的 reference、DIRECT、WB/SWB，然后才能解释 tandem reference 或 pass/fail。
2. **测试矩阵再冻结：** FER/BLER、SNR、DTX、bundling、DCR/ACR、噪声类别；不能从当前多列表直接计算最终工作量。
3. **串接阶段需决定：** T073/T081 的 characterization 与 T084 的前置测试冲突，同时去除/解释 qualification 残留。
4. **客观判定补齐：** AFR 的 `[x]` 和单位、相同 ptime、能量窗口、衰减阈值与工具版本。
5. **来源与格式清理：** 主文仍写 Agenda item 7.7，页眉仍标 SA4#137-e / 8 月，但 History 与 R4 对应 9 月 v0.2.0；应以本次编号/正文历史识别来源，不能因旧页眉当成另外一次会议的最终版本。§4.1 的 `[7]`、`[9]` 未在该文件列出完整 References，需回溯 121 等贡献，不能假定参考编号已全局统一。

本次已完成性能要求的结构分析和要求追踪，**没有候选的测量结果可用于判定达标**。下一步进入 **Step 3：184 / ULBC-4 的采样率、音频带宽与决策依赖**，重点与 PR-09、PR-16 和带宽条件交叉核对；随后再分析资源与时延/DTX 约束。

### 提取与核对记录

使用用户指定的 `D:\Program\miniforge3\python.exe` 和标准库，读取 180 及八份贡献；保留来源 DOCX 和 Markdown，未修改 ZIP。180 包含 12 张物理表（其中 T058 是空表）、23 条批注、441 个插入节点、39 个删除节点；这些数字描述文件结构，不是定案事项数量。

转换保留表格 vMerge/gridSpan、上标、方括号和批注定位，并生成当前文字/修订前文字差异。采用 OOXML 内容检查，未做 DOCX 页面渲染，不提供推测页码；原文字体颜色没有转换成正式状态标签。TR 26.940、SP-260696、P.800、P.56、BS.1770 等引用文件正文未在本步另行核实，本报告不扩展其条文内容。
