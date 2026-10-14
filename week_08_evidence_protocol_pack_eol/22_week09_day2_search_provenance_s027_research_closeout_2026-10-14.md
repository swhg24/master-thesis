# Week 9 Day 2 — Research Closeout and Thesis-Ready Evidence Notes

> 性质：研究归档文档（Research Closeout），服务于后续 Methodology、State of the Art、Pack EoL Case Assessment 与 Discussion 写作；不是工作日报，也不是论文 Results。
> 建立日期：2026-10-14（Week 9 Day 2 收尾）
> 相邻文件：本文件是 [21_export_provenance_manifest_2026-10-13.md](./21_export_provenance_manifest_2026-10-13.md) 的研究总结与 S027 精读延伸；不重复抄写 Manifest，也不复制原始导出数据。
> S027 数据核对基准：本文所有 S027 的实验数值、图号与表号均直接取自 **arXiv v2 manuscript corresponding to the IEEE CASE 2025 publication**（arXiv:2503.09409v2，提取日期 2026-10-14），不依赖旧笔记转述；**未与 IEEE 出版商发布版 PDF 做过逐字比较**，若后续取得出版商 PDF 应做一次数值复核。

---

## 1. Day 2 Research Objective and Status

### 1.1 本轮要解决的问题

Week 9 Day 2 围绕三个相互关联的问题展开：

1. **文献检索如何达到可追溯、可复现**：检索导出从哪来、带什么元数据、能否登记为正式 Query Run；
2. **Source、Claim、研究结论为什么必须分层**：一条来源能支持什么、不支持什么，结论强度不能超过证据强度；
3. **如何从最近邻机器人文献中提取可用于 Pack EoL 评价的证据**：以 S027（汽车中控台连接器插接）为样本，演练"实验现象 → 证据边界 → 对 Pack EoL 任务的迁移条件"的推理链。

### 1.2 完成状态（严格分层）

| 项目 | 状态 |
| --- | --- |
| 历史导出定位与 provenance 审计（Manifest 21 号） | **完成**（检索式/字段/过滤器/命中数仍 UNKNOWN） |
| S027 书目核验（arXiv 预印本 ↔ IEEE CASE 2025 会议版） | **完成**（同一研究；预印本 v1/v2 与会议版均为六位作者） |
| S027 技术精读与实验证据提取（Table I–IV） | **完成**（数值以原文为准，见第 4、5 节） |
| 从 S027 到 Pack EoL 的推理边界演练 | **完成**（见第 6、7 节） |
| 正式数据库检索的可复现登记 | **未完成**（四份导出仍非正式 Query Run） |
| 正式 title/abstract 初筛、引文追踪、账本修复 | **未完成**（列入第 10 节 Open Items） |

**明确不因本总结宣告完成的事项**：WP1、三库正式检索、完整筛选流程、S001–S036 账本修复、"closest-work 引文核对完毕"均不得因本文件而改变其未完成状态。

---

## 2. Historical Search Export Audit（摘要）

详见 [21_export_provenance_manifest_2026-10-13.md](./21_export_provenance_manifest_2026-10-13.md)，本节只保留结论级摘要。

### 2.1 已核实事实（VERIFIED）

- 四份历史导出均在 `~/下载` 恢复：Scopus 1 份（68 行）、IEEE Xplore 3 份（9 / 25 / 3 行）；SHA256 与数据行数已登记在 Manifest §1。
- 原始导出行数合计 **105**；其中 **89** 条带 DOI、**16** 条无 DOI；DOI 去重后 **82** 个唯一 DOI；Scopus 与 IEEE-04.11.21 之间 **7 组跨库 DOI 重复**；初步去重后约 **98** 条不同书目记录。
- **计数口径明确**：98 是初步去重后的书目记录数（105 − 7 组跨库重复；无 DOI 记录内部还需进一步核对），**不是最终纳入论文数**；最终纳入数需经 title/abstract 与 full-text 筛选后单独统计。
- IFToMM 同名两条（Scopus rows 8 & 37）分属 **163 MMS / 164 MMS** 两卷、EID 不同、无 DOI，**保持为两条不同书目记录**，不得自动合并；是否排除由相关性决定，`Conference review` 类型本身不作为充分排除理由。
- 与现有账本的关联：S001、S017 已在账本且出现在 Scopus 导出；S027 的 IEEE CASE 2025 会议版为新发现的派生记录（对应已登记预印本）；`EXP-IEEE-02/03` 的 28 个 DOI 尚未直接匹配账本，未入库。

### 2.2 仍为 UNKNOWN 的检索参数

- 实际 Boolean 检索式：UNKNOWN；
- 检索字段（Scopus/IEEE）：UNKNOWN（12 号 Run Sheet 里的是拟定基准，非执行记录）；
- 过滤器与时间范围：UNKNOWN；
- 命中数（hit count）：UNKNOWN（68/9/25/3 是导出条数，不是命中数）；
- 检索运行时间：UNKNOWN（导出时间戳不等于检索运行时间）；
- 各导出与查询的对应关系：UNKNOWN。

### 2.3 为什么"导出记录数 ≠ 命中数 ≠ 有效文献数"

数据库界面命中数对应的是**检索式在索引中的匹配规模**；导出文件记录的是**当时选择导出的条目数**；有效文献数是**去重、初筛、全文合格之后**的数量。三者口径不同：命中数可能受界面分页/截断影响，导出数只反映下载行为，两者都没有经过 relevance 判断。因此在任何论文表述中都不能写成"三库共检索到 105 篇文献"。

---

## 3. S027 Bibliographic and Evidence Identity

### 3.1 完整书目信息

- **Title**: AI-based Framework for Robust Model-Based Connector Mating in Robotic Wire Harness Installation
- **Authors（六位）**: Claudius Kienle（IAS Lab, TU Darmstadt；ArtiMinds Robotics）、Benjamin Alt（AICOR, Universität Bremen；ArtiMinds Robotics；通信作者；共同一作）、Finn Schneider（IFL, KIT）、Tobias Pertlwieser（IFL, KIT）、Rainer Jäkel（ArtiMinds Robotics）、Rania Rayyes（IFL, KIT）
- **会议版**: 2025 IEEE 21st International Conference on Automation Science and Engineering (CASE)，2025-08-17~21；DOI `10.1109/CASE58245.2025.11164054`
- **预印本**: arXiv `2503.09409`，DOI `10.48550/arxiv.2503.09409`；v1 2025-03-12，v2 2025-06-09；标注 "6 pages, 6 figures, 4 tables, presented at CASE 2025"
- **资助声明**: BMWK 13IK026A；BMBF RobInTime 01IS25002B

### 3.2 版本关系（VERIFIED）

预印本与 IEEE CASE 2025 会议版为**同一研究**；arXiv v1、v2 与会议版作者列表一致，均为**六位作者**。旧 Screening Log 的 S027 行只登记了四位作者，属**不完整的书目登记**；不能据此声称 Rainer Jäkel 与 Rania Rayyes 是会议发表时新增的作者。处理原则：CASE 2025 会议版作为主记录，arXiv 作为预印本版本链接保留，**不创建第二个独立 Source**。

### 3.3 按协议分类

| 维度 | 取值 | 说明 |
| --- | --- | --- |
| production_level | `NON_BATTERY_ANALOG` | 实验对象为汽车中控台线束连接器，非电池制造任务 |
| lifecycle_stage | `GENERAL_METHOD` | 不绑定电池生命周期的方法研究 |
| source_type | `CONFERENCE_PAPER`（主记录）；预印本为版本链接 | 六位作者、IEEE 会议发表 |
| case_relation | `CROSS_INDUSTRY_TASK_ANALOG` | 只能作为跨行业任务机制类比使用 |
| 与 Pack EoL 的关系 | **不是 DIRECT_PACK_EOL 证据** | 不涉及电池、高压、制造端 EoL 工位或测试许可 |

**迁移边界**：S027 证明的是"具体机器人配置（UR5e + 力控 + 视觉 + 学习式程序参数优化）在汽车连接器任务上的技术与优化表现"，不是任何机器人架构的普遍优势，更不是电池 Pack EoL 工位的验证。

### 3.4 待执行的账本维护（本轮不做）

将 S027 账本行更新为会议版书目（补全六位作者、会议版 DOI、版本链接）是后续待执行的维护任务；**本轮不修改 02/03/04 任何 CSV**。

---

## 4. S027 Technical Deep Reading

> 本节全部技术事实以论文原文为准；Section I–VII、Fig. 1–6、Table I–IV 编号与原文一致。

### 4.1 Research Problem（Sec. I, II 摘要）

汽车装配中机器人已广泛应用，但**线束安装（wire harness installation）仍以人工为主**，代价高昂的专用机械方案只是少数替代。原因：线束柔性带来的过程方差、产品变型多、对节拍与稳健性的严格过程要求。线束安装的后期步骤之一是**连接器插合（connector mating）**：连接器几何种类多；插座位于传动系、中控台、仪表板等 6-DoF 机械臂难以到达的位置；线束与安装目标的**预定位存在数量级为几毫米的随机方差**。现有力控/视觉搜索插接方法存在**稳健性与执行时间之间的固有权衡**。S027 的目标是用学习到的前向模型优化搜索策略，在保持稳健性的同时减少搜索开销。

### 4.2 Robot Program and Probe Search（Sec. III-A, Fig. 4）

机器人程序用 **ARTM（ArtiMinds Robot Programming Suite，商用跨平台机器人程序表示）** 编写：任务表示为参数化 skill 组合与控制流原语，每个 skill 的参数化同时作用于运动规划器与运行时控制器。Fig. 4 展示的程序为**两级结构**（框名为 Fig. 4 图形内标签；程序语义由 III-A 正文与图注确认）：

- **顶层序列**：`Move to Point: Approach` → `Probe Search` → `Insert Motion`；
- **Probe Search 内部循环**：对搜索图案中每个点循环执行三个子运动，即
  1. `Move Linear Next Point` — 直线运动到下一个探测位置；
  2. `Move Linear Relative Contact` — 沿局部 Z 轴的力控直线运动，接触表面即停止；
  3. `Move Linear depart` — 沿局部 Z 轴的直线退离运动。

即这三个 Move Linear 动作是 Probe Search skill 的**内部循环动作**，不是 Probe Search 之后的同级步骤。

**搜索成功判据（原文）**：当接触运动"失败"——即由参数 `PointFrom`/`PointTo` 定义的相对运动**在没有超过所定义接触力的情况下被执行完成**——搜索提前结束并返回成功（`valid` 置为 True）。其物理含义是：插头已落入插座孔内，因此 Z 向运动没有遇到预期表面。

**关键区别**：该判据是**触觉/运动层面的机械判据**（相对运动完成且未触发接触力阈值），**不是电气连接确认**。论文的任务边界止于机械插合与插入动作；没有电气导通检测、没有测试许可、没有安全时序。这一区别对第 6、7 节的迁移分析至关重要。

### 4.3 MuTT and Shadow Program（Sec. III-B, Fig. 2, Fig. 3）

框架三阶段（Fig. 2）：**robot programming（ARTM）→ learning（MuTT）→ optimization（SPI）**。

- **Shadow Program** `P̄_ω` 是 ARTM 程序 `P` 的可微、部分学习的模型，由笛卡尔与关节空间可微运动规划器 + 神经网络组合（Fig. 3）。输入：任务参数 `x`（如 `PointTo`）与环境图像 `I`；输出：预测的期望轨迹（关节构型、末端力/力矩）。
- **分层建模（两级）**：由于搜索可能包含大量探测、轨迹时间序列很长，预测学习难度随序列长度显著增加，论文将学习问题拆为两级：
  - **内层（probe-level）模型 m_ω1**：学习单次力控探测运动，训练数据为所有搜索执行中的所有探测运动；
  - **外层（search-level）模型 m_ω2**：学习搜索层语义——当预测末端位姿落入孔内时终止轨迹，并在找到孔时把成功标志置 1；其训练数据中用 m_ω1 的预测替换了轨迹中相应部分的真值。
- 输入输出对应关系：**环境图像 + 初始状态 + 程序参数 →（MuTT 前向预测）预测轨迹、末端力、执行时间与搜索成功**。

### 4.4 SPI Optimization（Sec. III-C）

- **SPI（Shadow Program Inversion）** 是对 shadow program 的一阶优化器：冻结模型权重 `ω`，对任务参数 `x` = {接近运动的 `PointTo`、探测搜索的 `Pattern`} 做梯度下降，目标函数为任务成功与节拍的加权和：`Φ(θ̄) = w_s·Φ_s + w_c·Φ_c`（式 (1)，成功代价 + 节拍代价）。
- **运行时流程**：优化器接收中控台内部图像、当前任务参数与机器人初始状态 → 输出优化后的 `PointTo` 与 `Pattern` → 机器人按优化参数执行 ARTM 程序。
- **必须强调的四点**：
  1. 优化对象是**参数化机器人程序**，不是原始运动命令；
  2. **不回放**神经网络预测的"最优"轨迹，而是用优化后的参数重新执行工业程序；
  3. 实际执行由**工业控制器 + 既有力控程序**完成，从而利用机器人原生安全功能与力控器的稳健性；
  4. 这一"reparameterization"设计**不自动等于系统获得安全认证**——论文只主张可审计、可由专家审核（auditable/certifiable by professionals），认证仍是外部过程。

### 4.5 Figures（与原文一一对应）

| 图号 | 原文图注（核实） | 内容 |
| --- | --- | --- |
| Fig. 1 | Robotic mating of electrical connectors in a center console | 总览：学习模型把搜索图案（红）优化为绿色策略，保证稳健安装且时间开销最小 |
| Fig. 2 | AI-based Framework for Visuotactile Connector Mating | 三阶段框架：工程师用 ARTM 编写程序 → 爬坡期反复执行采集数据 → 训练 MuTT → SPI 以 MuTT 为 sim2real 预测器优化程序参数 |
| Fig. 3 | Shadow program architecture for probe search | 可微运动规划器（蓝）+ 多模态 Transformer（黄）构成可微计算图；前向得到给定 `Pattern`/`PointTo` 的期望轨迹预测 |
| Fig. 4 | Extract of the ARTM robot program | 力控搜索与插入程序抽取；Probe Search 对每个图案点内部循环 approach / contact / depart 三个动作 |
| Fig. 5 | End-effector assembly for force-controlled connector mating | 末端装配：UR5e 内置力-力矩传感器、VISOR V20 相机、Schunk 夹爪与定制铝夹指；连接器加上夹持肋以便形锁合抓取 |
| Fig. 6 | Predicted and ground-truth position and force trajectories for probe search (connector E) | 探测级模型（绿）准确预测单次探测的时序与力轮廓；搜索级模型（蓝）预测找到插座时的时间与力 |

---

## 5. Experimental Evidence and Limitations（Table I–IV 数据取自 arXiv v2 手稿，即与 IEEE CASE 2025 发表对应的 manuscript）

### 5.1 实验设置（Sec. IV）

- 平台：**UR5e**（内置力-力矩传感器）+ 法兰安装 **Sensopart VISOR V20 2D 相机** + **Schunk MPG-plus 32 气动夹爪**；任务为当代车型（current-generation Audi）中控台内的 5 种工业连接器 A–E 与 5 个对应插座。
- 插座朝向：D 开口朝上；A、C、E 约旋转 20°；**B 旋转 90°（侧向开口）**。
- 为便于机器人操作，标准连接器几何被改写，加入**夹持肋（gripping ribs）**配合定制铝制夹指做形锁合抓取（Fig. 5）——即论文同时改变了"工件设计"，这一点对迁移讨论很重要。
- 数据采集：每个插头的程序**执行 4,000 次**用于训练（Table I 各连接器 # train ≈ 3,973–4,000）。
- 位姿扰动：中控台装在线性轴上，每次执行施加均匀随机偏移 **±2 mm**（B 因空间受限为 **±1.5 mm**）；程序参数在预定义域内均匀扰动，包括接近位置（±2 mm）、探测图案（每个探测点围绕接近位姿在 2 mm 内采样）、速度、加速度与接触力阈值。
- 评估：Table III 为**100 个未见环境与程序参数组合**，且**从与训练数据相同的分布生成**（in-distribution evaluation，无跨分布测试）。

### 5.2 Table I — 训练/测试数据分布（Sec. IV）

| 指标 | A | B | C | D | E |
| --- | --- | --- | --- | --- | --- |
| # train | 3,973 | 4,000 | 3,997 | 3,996 | 3,999 |
| # test | 199 | 200 | 200 | 200 | 200 |
| Succ. (fail) | 161 (38) | 104 (96) | 123 (77) | 172 (28) | 134 (66) |
| µL (σL) [points] | 201 (160) | 224 (127) | 173 (131) | 137 (124) | 222 (151) |
| µF (σF) [N] | 0.9 (0.8) | 1.3 (1.4) | 1.2 (1.1) | 1.0 (0.6) | 1.1 (1.1) |

未经优化的基线（纯触觉搜索）在采集数据中本身就有相当比例的搜索失败（Table I Succ/Fail：B 最差，104 成功 / 96 失败），且未优化程序的成功率与节拍随连接器几何差异很大——这正是"同一任务内产品变型驱动性能方差"的直接实验例证。

### 5.3 Table II — Shadow Program 预测精度（Sec. V-A）

| 指标 | A | B | C | D | E |
| --- | --- | --- | --- | --- | --- |
| Success F1 [%] | 99.4 | 94.2 | 98.4 | 98.6 | 98.5 |
| True neg. | 38/38 | 91/96 | 76/77 | 23/28 | 63/66 |
| True pos. | 159/161 | 97/104 | 120/123 | 172/172 | 133/134 |
| MAE_L [points] | 21.77 | 38.47 | 13.58 | 25.01 | 17.92 |
| MAE_P [mm] | 0.76 | 0.71 | 0.43 | 0.71 | 0.75 |
| MAE_F [N] | 0.98 | 1.63 | 1.09 | 0.92 | 1.03 |

论文正文（V-A）表述：末端位置 MAE < 1 mm、末端力偏差约 1 N（与 F/T 传感器噪声同量级）；轨迹长度预测平均偏差约 20 points（≈ 1 s 节拍偏差）；并称成功分类 F1 超过 99%。**注意**：正文"F1 exceed 99%"的笼统表述与 Table II 逐连接器数值（B 仅 94.2）不完全一致，两处均如实记录，引用时应以表值为准并保留该张力。

### 5.4 Table III — SPI + MuTT 在 100 个未见运行上的优化结果（Sec. V-B）

| 指标 | A | B | C | D | E |
| --- | --- | --- | --- | --- | --- |
| CT [s] (前)→(后) | 17→11 | 18→11 | 17→10 | 13→9 | 15→10 |
| # probes (前)→(后) | 10.2→4.9 | 13.8→5.7 | 11.7→3.0 | 6.8→3.2 | 9.7→4.5 |
| SR [%] (前)→(后) | 75→94 | 49→88 | 50→95 | 93→98 | 72→90 |

- 优化后所有连接器成功率提升、节拍下降、探测次数减少；论文将此归因于策略被调整为贴合当前环境与过程噪声分布。
- 论文对差异的解释：A 较大且插座配合余量（play）大 → 初始成功率更高（75%）、探测更少；B、C 公差更紧 → 搜索更久；B 插座旋转 90°、侧向插入且空间受限 → 优化后成功率 88%，低于其他连接器约 95% 的水平。

### 5.5 Table IV — 数据集规模消融（Sec. V-C，200/1,000/2,000/4,000 训练样本）

| 指标 | 200 | 1,000 | 2,000 | 4,000 |
| --- | --- | --- | --- | --- |
| Success F1 [%] | 98.4 | 97.3 | 96.2 | 98.4 |
| True neg. | 5/7 | 6/7 | 5/7 | 6/7 |
| True pos. | 92/93 | 89/93 | 88/93 | 91/93 |
| MAE_L [points] | **1,158.65** | 48.12 | 52.23 | 38.17 |
| MAE_P [mm] | 0.68 | 0.77 | 0.59 | 0.83 |
| MAE_F [N] | **2.48** | 0.96 | 0.95 | 0.96 |
| Optim. CT [s] (前)→(后) | 12.6→13.4 | 12.6→9.21 | 12.6→8.6 | 12.6→9.0 |
| Optim. # probes (前)→(后) | 6.8→7.6 | 6.8→3.5 | 6.8→2.8 | 6.8→3.2 |
| Optim. SR [%] (前)→(后) | **93→80** | 93→95 | **93→98** | 93→98 |

（Table IV 中 1,000 样本列的 CT 后值在 arXiv v2 手稿版面提取中为 9.21 s，表中忠实保留原始值；正文叙述需要取整时按约 9.2 s 引用并注明。）

**核心现象（以原文数值为准）**：

- **200 训练样本**：成功分类 F1 仍高达 98.4、TP 92/93，但轨迹长度预测 MAE 达 1,158.65 points（约 57 倍于其他规模）且力预测 MAE 2.48 N；据此优化的程序**表现反而变差**——SR 93%→80%、节拍 12.6→13.4 s、探测次数 6.8→7.6。
- **2,000 训练样本**：SR 93%→98%、节拍 12.6→8.6 s、探测 6.8→2.8；论文称 2,000 为最优数据集规模，超过 1,000 后收益递减。
- 论文正文（V-C）：收集 1,000 个训练样本在该实验装置上约需 **3 小时**；说明在重复性工业装配任务背景下，数据采集开销是"可管理的"，但仍是爬坡期负担。
- **注意（原始论文未说明、不得当作论文结论）**：论文未指明 Table IV 消融所用的连接器；其基线（12.6 s、SR 93%、6.8 probes）与 Table III 中连接器 D 的基线（13 s、93%、6.8）最接近，这只是**本笔记的推断**，不写入论文结论。

### 5.6 原文其他关键发现（Sec. VI Discussion）

- 相比纯触觉搜索，优化策略在平衡稳健性与节拍上显著更好；对**光照变化**表现出较强稳健性（训练数据跨多日采集，自然包含光照变化——这是论文给出的可能机制，非独立实验证明）。
- 与无模型自监督/强化学习方法相比，本框架**不需要运行期探索**，论文据此主张"训练对工业使用是安全的"（论文自述，不等同于安全认证）。
- **开销与限制**：需要有初始训练阶段（爬坡期效率暂时下降）；用户需定义程序参数采样域；OOD 泛化改进留给未来工作；**每次执行周期的实时优化计算约 1.5 s**（每迭代 20 个探测循环、21 次 MuTT 推理、60 次运动规划器调用）。
- 结论（Sec. VII）：**优化质量在很大程度上取决于学习前向模型的预测精度**；未来方向为跨设置预测精度、OOD 泛化、少样本学习与推理加速。

### 5.7 证据分层总结（本研究笔记口径）

| 层级 | 内容示例 |
| --- | --- |
| 论文直接报告的数据 | Table I–IV 全部数值；±2 mm 扰动条件；4,000 次/连接器采集；优化约 1.5 s/cycle；1,000 样本 ≈ 3 h |
| 论文给出的合理解释 | 连接器几何/配合余量解释成功率差异；多日采集解释光照稳健性；预测误差解释优化质量依赖 |
| 尚未验证的机制假设 | "预测误差大 → 优化器被误导 → 200 样本下表现变差"是**合理推断**：论文同时报告了 200 样本的极高 MAE_L/MAE_F 与优化后退化，但没有独立实验证明该因果链是唯一机制；不得宣称论文已证明该机制 |

---

## 6. S027 to Thesis Framework Mapping

> 映射到当前论文主线：**Task → Requirement → Capability → Condition → Suitability**。S027 只填充"某种机器人配置"的一行，不代表任何架构排名。

| 框架要素 | S027 对应内容 | 对 Pack EoL 的迁移限制 |
| --- | --- | --- |
| **Task** | 顶层 `Move to Point: Approach` → `Probe Search`（内部循环 Move Linear Next Point / Move Linear Relative Contact / Move Linear depart）→ `Insert Motion` | Pack EoL 任务还包含线束归置、插合后电气确认、测试许可与测试后安全断开；S027 只覆盖机械插合段 |
| **Requirement** | 几毫米级预定位随机方差；亚毫米公差对过程敏感；接触力阈值；搜索成功判据（相对运动完成且未触发接触力）；节拍/稳健性权衡 | Pack 连接器几何、允许力、残余位姿误差分布、电学验收判据均为 UNKNOWN；不能代入 S027 的 ±2 mm 或力值 |
| **Capability** | 2D 视觉（VISOR V20）；UR5e 内置 F/T 力控；触觉探测搜索；MuTT 前向模型；SPI 程序参数优化 | 能力存在与"在目标工位可用"是两回事；Pack EoL 的感知/力控/恢复配置需按具体配置重新评价 |
| **Condition** | 产品变型（5 种连接器几何与朝向）；残余位姿不确定性（±2/±1.5 mm）；数据可用性（200–4,000 样本）；爬坡期与重适配负担（数据域定义、~3 h/1,000 样本、~1.5 s/cycle 优化计算） | 数据采集负担、在线优化计算与维护重新适配是**实施条件**，对 Pack 工位同样成立，但具体数值不可迁移 |
| **Suitability** | 在本文配置与 in-distribution 条件下：优化后 SR 49–93%→88–98%、CT 13–18 s→9–11 s | 未与同任务专用自动化或人工方案做同条件比较；不能推出"机器人优于专机"，更不能迁移到 Pack EoL |

**结论句（条件性）**：S027 证明在**特定机器人配置**（UR5e + 视觉 + 内置 F/T 力控 + 学习式参数优化 + 改造后的夹持友好连接器）和**同一分布的 ±2 mm 扰动**下，模型辅助程序参数优化能显著改善汽车连接器插合的搜索成功率与节拍；它证明的是**该配置下的技术与优化表现**，不是机器人架构的普遍优势。

---

## 7. Research Insights from the Student Discussion

以下为本轮讨论形成的分析性认识，以"可检验的研究命题"方式表述，**不是目标企业工位已被测量的结论**：

1. **产品型号多、换型频繁，不足以单独证明机器人更适合。** 变型多是价值机制的候选输入（Condition），必须与残余误差、数据/维护负担、同任务基线一起评价；S027 的 Table I/III 显示不同几何本身带来成功率与节拍的大幅差异（B 仅 49%→88%），说明变型同时是机器人方案的成本来源。
2. **机械浮动、主动视觉定位、力控搜索是并存的误差处理路径。** 专用机构（如 CN109856554A 披露的浮动/导向方案）与机器人（视觉 + 力搜索 + 学习优化）各代表一类配置；评价必须按具体配置比较，不能按"专机 vs 机器人"类别预设答案。
3. **"机械浮动范围大于名义位置偏差"不能单独证明可靠插接。** 浮动仅解决几何容差的一部分；S027 中插座朝向（B 为 90° 侧向）、配合余量（A 大余量）、表面不平整等因素都独立影响成功率，几何容差不是充分判据。
4. **必须进一步检查 X/Y/Z 与姿态误差、机械导向、插入力、卡滞与锁止。** S027 只报告了 Z 向力（µF）与运动完成判据；插合后的锁扣/锁止、卡滞恢复均不在其任务边界内。Pack EoL 同样需要这些字段，且目前 UNKNOWN。
5. **搜索成功 ≠ 机械锁止、电气连接确认与测试许可完成。** S027 的成功判据是"接触运动未触发力阈值即完成"（valid=True），是纯触觉层面判据；电气导通、测试设备接受、许可与安全时序均超出论文范围。这是 Pack EoL 功能分解（第 10 节 Day 3 功能卡）的核心依据。
6. **高模型 F1 不保证优化后的真实机器人程序更好。** Table IV：200 样本时成功分类 F1 = 98.4，但优化后 SR 从 93% 降至 80%、节拍 12.6→13.4 s；而模型指标并不是决策变量——优化器在预测的轨迹/力上优化目标函数，分类准确率高但轨迹/力预测差（MAE_L 1,158.65、MAE_F 2.48）时，程序参数也可能被引向更差方向。评价标准必须落在**真实执行的程序表现**上，而不是模型指标上。
7. **UNKNOWN 不等于 FAIL。** 缺少同任务对比证据只能得出"目前不能判定优劣"（NOT SUPPORTED BY CURRENT EVIDENCE），不能写成"某架构不适合"。S027 没有与专用自动化对比，Pack EoL 的目标参数也未公开——两者都不构成任何架构的否定结论。

---

## 8. Candidate Claims for Future Evidence Matrix

以下 3 条为 **PROPOSED CLAIMS**：先登记为候选，**不分配正式 Claim ID（不占用 C035/C036），不写入 04_pack_eol_claim_evidence_matrix.csv**。待账本修复（S027 会议版入账）后再走正式 claim audit。

### PC-1（模型辅助工业机器人力控搜索参数优化）

- **Claim statement (EN)**: For automotive wire-harness connector mating under pose perturbation of ±2 mm (±1.5 mm for connector B), model-based optimization of a force-controlled robot program (MuTT forward model + SPI, operating on ARTM program parameters) improved search success rate and reduced cycle time across five connector types relative to a tactile-search baseline with the same robot configuration.
- **Source ID**: S027（IEEE CASE 2025 会议版；S027 现账本行为预印本版本）
- **Related RQ**: RQ1; RQ2
- **原文位置**: Sec. V-B; Table III; Fig. 2; Fig. 3; Sec. III-C, Eq. (1)
- **What evidence supports**: Table III 数值（SR 49–93%→88–98%；CT 13–18 s→9–11 s；probes 减半左右）；同一机器人配置的未优化程序作为基线。
- **What evidence does not support**: 与专用自动化/人工的对比；跨连接器泛化（评估与训练同分布）；电气确认与安全许可；任何电池任务表现。
- **Inference and transfer boundary**: 仅支持"该配置、该扰动分布、该任务下程序参数优化有效"；`CROSS_INDUSTRY_TASK_ANALOG`，不能迁移为 Pack EoL 部署结论。
- **Missing evidence**: 目标 Pack 连接器的扰动分布、允许力与几何；同任务其他配置的比较数据。
- **Proposed audit status**: `RETAIN_CONDITIONAL`（备选；待正式登记后决定）。

### PC-2（模型分类指标与真实优化结果的差异）

- **Claim statement (EN)**: High task-success classification performance of a learned forward model does not guarantee that the optimized real robot program performs better: with only 200 training samples, success-classification F1 remained at 98.4 while trajectory-length and force prediction errors rose sharply (MAE_L 1158.65 points, MAE_F 2.48 N), and the optimized program degraded relative to baseline (success rate 93%→80%, cycle time 12.6 s→13.4 s); with 2,000 samples, classification F1 was 96.2 and the optimized program improved (93%→98%, 12.6 s→8.6 s).
- **Source ID**: S027
- **Related RQ**: RQ1; RQ2（作为"预测质量/数据可用性是否为适用条件"的证据）
- **原文位置**: Sec. V-C; Table IV
- **What evidence supports**: Table IV 两组数值并存；论文 VII 的"优化质量取决于预测精度"表述。
- **What evidence does not support**: 因果机制的独立验证（论文未证明"预测误差是优化退化的唯一原因"）；该现象向其他任务/模型的推广。
- **Inference and transfer boundary**: 支持的方法论命题——**以真实执行结果为评价标准、以模型指标为辅**；不放大为"小数据一定失败"。
- **Missing evidence**: 对应 Pack EoL 任务的数据规模-预测质量关系（无数据）。
- **Proposed audit status**: `RETAIN_CONDITIONAL`（备选）。

### PC-3（数据可用性与预测质量作为实施条件）

- **Claim statement (EN)**: Data collection and model-retraining overhead constitute implementation conditions for learned connector-mating optimization: ~4,000 executions per connector were collected for training, 1,000 samples took roughly three hours in the reported setup, online optimization required approximately 1.5 s per execution cycle, and out-of-distribution generalization remained unverified.
- **Source ID**: S027
- **Related RQ**: RQ2; RQ3
- **原文位置**: Sec. IV（4,000 次/连接器；扰动域）；Sec. V-C（≈3 h/1,000 样本）；Sec. VI（~1.5 s/cycle；OOD 开放）
- **What evidence supports**: 上述开销均是该配置的报告值。
- **What evidence does not support**: 数值向其他工位/设备的迁移；爬坡开销与节拍的总体经济比较。
- **Inference and transfer boundary**: 支持把"训练数据负担与在线优化计算"列为架构选型的 Condition 维度；不提供任何 ROI 数值。
- **Missing evidence**: Pack EoL 工位节拍与换型频率下的同类负担评估。
- **Proposed audit status**: `RETAIN_CONDITIONAL`（备选）。

---

## 9. Thesis Writing Reuse Map

| 论文部分 | 可复用内容 |
| --- | --- |
| **State of the Art** | 机器人连接器操作与模型辅助插接的最近邻线（Sun 2010 / Di 2012 / Yumbla 2019 → SPI/MuTT 2021–2024 → S027 CASE 2025）；力控搜索的成功/节拍权衡 |
| **Methodology** | 检索 provenance 纪律（导出 ≠ 命中 ≠ 有效文献）；Source/Claim/结论分层；跨行业机制证据的迁移边界写法；按配置而非按架构类别评价 |
| **Pack EoL Case Assessment** | 残余位姿误差的补偿机制谱系：机械浮动（CN109856554A）、视觉定位（专利/供应商）、力控搜索与学习优化（S027 机制）；S027 table 支持"几何变型 → 性能方差"与"搜索成功 ≠ 电气确认"两个结构点 |
| **Discussion** | 训练数据负担、在线优化开销、预测质量依赖、OOD 未验证——作为实施条件讨论；UNKNOWN ≠ FAIL 的表述纪律 |
| **Limitations** | 缺少现场同工况比较；电气验收与安全许可数据缺失；均为跨行业/跨生命周期迁移 |

**英文 synthesis paragraph（候选素材，措辞审慎）**：

> Recent work on automotive wire-harness installation provides a mechanism-level analogue for the connector-adaptation layer of pack end-of-line test stations, but not direct evidence for them. Kienle et al. (2025) demonstrated on a center-console assembly task that a force-controlled robot program, re-parameterized by model-based optimization over a learned visuotactile forward model, increased search success rates from 49–93% to 88–98% and reduced cycle times from 13–18 s to 9–11 s across five connector types under pose perturbation of ±2 mm for connectors A, C, D and E and ±1.5 mm for connector B (Table III). Their results further show that the benefit of such optimization is conditional on prediction quality: with 200 training samples, high success-classification F1 (98.4) coincided with large trajectory and force prediction errors and a degraded optimized program (93%→80% success), whereas 2,000 samples yielded clear gains (Table IV). These findings characterize a specific robot configuration evaluated within the distribution of its training data; they do not compare robots against dedicated contacting mechanisms, do not include electrical acceptance or test authorization, and cannot be transferred quantitatively to pack end-of-line connector handling, whose target tolerances, permissible forces, acceptance criteria and safety sequences remain unpublished.

---

## 10. Open Items and Day 3 Handover

### 10.1 尚未完成的研究任务

| 任务 | 说明 |
| --- | --- |
| 正式 Scopus/IEEE 可复现检索登记 | 四份导出仍是历史文件，检索式/字段/过滤器/命中数 UNKNOWN；需按协议 §10.1 补记或定向重跑确认对应关系（新日期、新 run ID） |
| WoS 覆盖缺口记录 | Web of Science 从未执行/收到；按协议 §4 二库互补要求决定是否补跑并明确记录访问限制 |
| 去重后的正式 title/abstract 初筛 | 98 条初步不同书目记录尚未逐条筛选；P1 清单见 Manifest §4 |
| S027 会议版书目修复 | 把 S027 账本行升级为 CASE 2025 会议版（六位作者、会议版 DOI、版本链接），本轮未执行 |
| 旧编码与 SEED-W06 关联 | S012 的 `query_run_ids=SEED-W06` 是早期编码，未在 02_query_run_log 中登记；需补记或改指向已登记运行 |
| 最近邻引文追踪 | S027 前向/后向引文（尤其 Sun 2010、Di 2012、Yumbla 2019、MuTT/SPI 前作）未做系统核查 |

### 10.2 Day 3 研究入口（仅入口，未启动、无 Gate 判定）

- **Function Card F1 — Residual Connector Pose Uncertainty**：X/Y/Z 与姿态误差来源、机械导向、视觉定位、力控搜索各自的补偿边界；
- **Function Card F2 — Mechanical Mating, Electrical Acceptance and Test Authorization**：机械插合、锁止确认、电气连接被测试设备接受、测试许可与安全时序之间的功能与责任划分。

两张卡均处于 `OPEN` / 未填写状态；不得提前标记为已完成，不得宣布任何 Gate `PASS`。

---

> 本文档为 Day 2 研究内容的正式归档；学习部分收尾，但正式检索、筛选、账本修复、引文追踪仍是开放任务，不因本文档存在而被视为完成。下一轮从"账本修复 + 初始初筛"或 Day 3 Function Card 开始，按当天优先级选择。