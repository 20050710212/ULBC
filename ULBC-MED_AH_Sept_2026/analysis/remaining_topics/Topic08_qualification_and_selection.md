# 资格与选拔规则分析

> 对应原 Overview Step 8，覆盖 R4 4.5。主干为 182 / ULBC-5 v0.0.1，相关输入为 147、093、094、135、150、152，交叉 Step 1 的 175/176、性能主干 180、设计约束 184 和分离文件 183。

> 2026-10-08 评审：已复核结论的证据范围、明确/待定状态及引用；详见[评审记录](../Review_2026-10-08.md)。依据仍是本地 2026 年 9 月材料，不推定后续会议结果。


## 1. 本主题的结论

项目当前工作假设是跳过独立 qualification，直接 selection；候选仍需满足提交、交付及设计约束条件。**182 只给出尚带括号的“两条规则”框架，FoM 及完整程序仍 TBD**，目前不能计算官方排名或声称最多五个候选晋级是现行规则。

应把三类判断分开：能否进入测试、是否因不合规被淘汰、合格候选如何排名。它们不能互相替代。

## 2. 当前主干与入口条件

| 来源 | 明确内容 | 阅读边界 |
|---|---|---|
| [Step 1 / 175](../step01_project_plan/Step01_ULBC1_ULBC2_analysis.md) | 按 ULBC-6 完整、及时、合格提供交付物才能参加 selection | 完整 ULBC-6 正文仍未找到 |
| 同上 / 176 | binding LoI 是候选提交必要条件；当前版本规定最迟 2026-12-23 收到 | 签 LoI 不强制实际提交，不能以 LoI 数等同候选数 |
| [182](sources/S4aA260182_source.md#P017) | Rule 1 淘汰、Rule 2 FoM 排名框架 | §3 整段括号；具体 FoM TBD |
| [167](sources/S4aA260167_source.md) | Selection test plan、DCR、非候选 LL | 实验矩阵和细节尚未齐备 |

182 在 R4 为 a，但其正文不因此成为无占位的最终规则。147 在 R4 也为 a，主要提供初始 template，不是另一套已完成规则。

## 3. 182 的两条规则逐条看

### 3.1 Rule 1 是合规淘汰方向

[Rule 1](sources/S4aA260182_source.md#P018)拟淘汰不满足 ULBC-4 Design Constraints 及 ULBC-6 other Selection requirements 的候选。

它没有逐条列出 180 性能要求的失败如何导致淘汰，也没有完整列出数据分离违规、无声明、测试中崩溃等事件的判定程序。不能据此补写“任何一项听测低于参考，立即淘汰”或“任何数据问题自动无效”的现行规则。

最终门槛还取决于 184 中未定的复杂度、RAM/ROM、额外时延等值。若硬门槛未先明确，规则无法公平作用于全部候选。

### 3.2 Rule 2 尚不能用于实际排名

[Rule 2](sources/S4aA260182_source.md#P019)写 FoM(s): TBD。编辑注释继续保留：

- complexity 仅作 tie-breaker，或映射到 FoM；若设计约束足够低，可能无需 complexity FoM。
- 不同 test conditions 不同权重，或每 experiment 相同权重。
- systematic failures 如何计数仍 FFS。

[Selection Procedure](sources/S4aA260182_source.md#P034)直接为 TBD。因此没有已经冻结的 blinding/unblinding、分数合并、tie 处理、排除后重算或正式投票流程。

## 4. 135 的 qualification 方案为什么不是当前主干

[135，Nokia](sources/S4aA260135_source.md)建议在 qualification 保留时，用合规排除和 FoM 筛选，最多 [5] 个候选进入 selection；讨论 requirement/objective 通过比例及 complexity FoM，附两个 blind-coded 程序选项。

文件自身限定“in case Qualification Phase is confirmed”。175/176 当前移除了该独立阶段，182 标题也为 Selection。故最多五个晋级、qualification 两种程序、135 的 pass-percentage 不能直接变成当前规则。

这并不取消其对候选池过大、测试费用、异常低质候选影响评价的关注；这些风险应由当前 selection 测试容量及系统性失败规则处理。

## 5. 资源因素进入排名的两条路线

### 5.1 093 的乘法调整提案

[093，vivo](sources/S4aA260093_source.md#P017)提议：

```text
FoM_final = α × FoM_MOS
α 初始化为 1
若 Memory > 10 MB：α *= 1 − 0.05 × (Memory−10)/10
若 Complexity > 1.5 GFLOPS：α *= 1 − 0.02 × (Complexity−1.5)/1.5
```

原文阈值 [10] MB、[1.5] GFLOPS 及系数 [0.05]/[0.02] 是候选数字，未被 182 冻结。按该例 M=20 MB、C=3 GFLOPS 时 α=0.95×0.98=0.931；同等原始 FoM 下调整分降低 6.9%。这是算术说明，不是实际候选结果。

需要补齐的问题包括：

1. Memory 指 ROM、RAM、峰值、还是某种总值。
2. GFLOPS 的算子权重及与 Step 3C 的 GMAC/WMOPS/RTF 怎样统一。
3. 是否同时保留不可突破的资源硬上限。
4. 大资源值下线性乘子可能为零/负，是否需要范围限制。
5. MOS FoM 的尺度与平均方法是否适合乘法调整。

不能把 093 的 1.5 GFLOPS 直接当成 184 的 1.5 GMAC/s。

### 5.2 150 的“硬约束后只比较感知质量”

[150，Fraunhofer](sources/S4aA260150_source.md#P015)主张设计约束负责淘汰，排名仅基于 perceptual performance，反对难以解释的资源/音质折算权重。

两路线的差别是：资源开销到底是可交易的得分因素，还是先满足的部署门槛。182 保留两种方向及 tie-breaker，没有选定。资源 penalty 不应被默认为允许突破硬约束的许可证。

## 6. 152 的 Quality Stairs 排分提案

[152，Fraunhofer](sources/S4aA260152_source.md#P009)提出：若候选在某 requirement 上跨所有测试该条件的 labs 一致失败，则淘汰；存活者按每 operating point 达到的每个 quality stair 每 lab 得一分，可加运行点权重。

它特别说明参考系统分数可能不完全线性，不必按参考名义码率形成严格连续阶梯。因此应分别判断每个 NWT 对比，不能假定达到高码率阶梯就数学上必然达到所有低阶梯。

原文 A/B/C 例子仅用于解释：A 未过最低参考而淘汰；B 多过一个 stair 得 1；C 多过两个得 2。例中 1.0 kbit/s、AMR-WB 8.85 等没有冻结 180 全部场景的最低门槛。

152 在 R4 为 n。148 的 quality stairs 概念为 a，并进入性能讨论，不等于 152 的淘汰和计分方案已被 182 采纳。182 留下 systematic failures FFS，正说明跨 labs 判定尚需补齐。

## 7. 094 的权重表及其边界

094 的测试/权重表是嵌入 EMF，普通段落提取不会显示。本轮复核原始渲染图后，已补入[完整表格文字转录](sources/S4aA260094_source.md#EMF-table-transcription)，供仅有 Markdown 的 GitHub 仓库直接审查。原始图保留于本地 `sources/094_media/image1.png`，以下是 selection 列的分类汇总：

| 每个码率下的类别 | 该码率对应权重 |
|---|---:|
| clean speech 三个输入电平作为一组 | 20% |
| street/office noisy speech 作为一组 | 10% |
| 2%_80 / 6%_160 loss 条件作为一组 | 10% |
| AMR-WB 12.65→ULBC tandem | 5% |
| DTX/CNG street noise | 5% |
| 每个码率合计 | 50% |

两个码率合计 100%。这不是每个单独 clean row 都给 20%；组内多电平、多条件如何平均仍需定义。表中语言、Street 15 dB SNR 和 loss 组合也是其提案，不能覆盖 180/167 的当前条件。

qualification 列只选部分条件，两个码率的选取也不同；它不是当前直接 selection 的实验必测表。094 为 n，182 明确 FoM weights FFS，不能把这些百分比当作已采纳。

### 7.1 “每个实验同权”与“每类条件同权”不同

如果同一噪声类别因两语言、两运行点拆成多个实验，每实验同权可能放大该类别实际权重；按类别同权则需要在类别内部汇总。候选数量触发的拆分不应无意改变质量偏好。

NWT、BT 和 consistent failure 还依赖统计置信标准；单看平均 DMOS 排序不足以宣布达到最低要求。当前 182/167 尚未提供完整的合并、显著性和多重比较决策方案。

## 8. 建议的决策流程

下表是便于理解的建议框架，不能视为 §4 已完成的官方程序：

| 步骤 | 输入 | 判断 |
|---|---|---|
| 进入检查 | LoI、按期提交、ULBC-6 运行与交付包 | 能否参与测试 |
| 身份冻结和盲化 | 候选程序/模型/参数、编号映射 | 全部实验比较同一版本 |
| 合规检查 | ULBC-4 与最终其他门槛 | Rule 1 排除条件及申诉/纠正范围 |
| 质量分析 | LL 原始结果、GAL、ULBC-3 | NWT/BT/consistent failure |
| 排名 | 最终 FoM 与权重 | 单/多码率、跨 lab 的汇总 |
| 结果讨论 | 统计不确定性、资源及交付检查 | tie、异常条件、获选程序 |
| 获选交付 | 最终规范/软件/向量及批准的额外项 | 不等同于允许测试后任意修改模型 |

训练数据分离条文 183 的主干纳入与违规后果尚需确认；107/106/131 的获选后数据和训练过程义务也不能先行塞进 Rule 1。

## 9. 待冻结事项

1. ULBC-4 硬门槛与 ULBC-6 交付要求。
2. ULBC-3 requirement 是否及怎样用于淘汰。
3. systematic failure 的跨 lab/语言定义。
4. 排名 FoM：MOS 汇总、stairs points、资源映射或 tie-breaker。
5. 类别、实验、运行点与语言的权重及缺测处理。
6. 统计判据、blinding、复核、tie 与正式选择程序。
7. 183 数据分离、异常提交与获选后义务。

本主题已完成对当前规则与备选提案的分析；因为主干尚有 TBD，无法给出官方可执行排名公式。

[数据集](Topic06_datasets_and_separation.md)、[测试与处理](Topic07_testing_and_processing.md)、[Step 1](../step01_project_plan/Step01_ULBC1_ULBC2_analysis.md)、[总体 Overview](../Audio_SWG_Tdoc_allocation_R4_overview.md)。
