# Week 9 Day 4 — Selection-Relevant Conditions：P1–P7 条件矩阵与四情景检验

> 性质：研究归档（Research Closeout Draft）。把 [09 §5](./09_framework_v1_input_requirements.md) 的七个生产条件字段（P1–P7）作操作化试填，并用四个**分析性情景**检验 Framework v1.0 能否解释"同一任务下相对适用性如何随条件变化"。不是论文 Results、不是四个真实工厂案例、不是对 Framework 工业有效性的实证验证、不是仿真。
> 建立日期：2026-10-15（Week 9 Day 4）
> 状态：`OPEN` —— 条件推理结构成立；目标工位参数与同条件性能仍缺；不判任何目标部署 Gate `PASS`/`FAIL`，不选架构赢家。提交与推送状态：最终修订版已通过人工审核，获准单独提交。
> 相邻文件：承接 [22](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)（S027 证据与迁移边界）、[23](./23_week09_day3_pack_eol_function_cards_f1_f2_2026-10-14.md)（F1/F2 功能卡）；条件定义来自 [09](./09_framework_v1_input_requirements.md)，判定规则来自 [13](./13_framework_v1_decision_table_draft.md)，基线卡来自 [11](./11_framework_v1_baseline_cards.md)；增量审计基准是 [19](./19_selection_relevance_counterexample_pilot_2026-09-30.md) 与 [20](./20_pack_eol_target_unknown_search_and_variant_boundary_2026-09-30.md)。证据纪律沿用 [01](./01_evidence_protocol_v1.md)。

---

## 1. Day 4 Research Objective and Boundary

### 1.1 本轮唯一核心问题

> **Under which task and production conditions can different robotic-system configurations become more or less suitable for the same battery-manufacturing task, and what evidence is required to support such conditional judgments?**

中文理解：在相同制造任务要求下，哪些任务与生产条件会改变机器人、专用自动化及其他参考配置的相对适用性？现有证据允许得出什么结论，哪些判断还需要验证？

服务对象：**RQ1**（哪些 task/process characteristics 决定 architecture suitability）、**RQ2**（在哪些 technical/economic/quality/safety/integration conditions 下适用）；并为 **RQ3**（implementation strategies）提供输入。本轮目标不是总结机器人优势，而是检验 Framework v1.0 条件字段能否产出可追踪、可复核的条件性判断。

### 1.2 相对 19 号文件与 Day 3 的增量价值（防重复声明）

19 号文件依据已核实机制**研究指出**：单一条件轴（产品/接口多样性）不单独支持机器人选型（这是分析性推论，不是实证证明）。Day 4 不重复该结论，增量是三件事：

1. **范围扩展**：把 19 号的结论从 P1/R4 一条轴推广为 09 §5 全部七条生产条件轴（P1–P7），逐条给出机制、边界、反例与验证需求；
2. **评价结构固定**：每条条件落成同构的 8 字段记录（§3），可直接并入 [13](./13_framework_v1_decision_table_draft.md) 第 2 步"条件卡"与 Condition Gate；
3. **框架能力检验**：用四个保持任务边界不变、改变生产条件取值或配置性能假设的情景（§4），检验四 Gate 能否产出"条件/假设变化 → 相对优势方向变化"的可追踪结论。这展示的只是 Framework 条件字段的**内部适用性与初步区分能力**，不构成对其工业决策有效性、评价充分性或外部效度的证明。

本文件不新增 Gate、不新增评分权重、不新增正式 Claim ID、不修改 09/11/13 框架文件与 02/03/04 账本，也不把论文改成机器人控制算法开发、强制仿真或没有证据的设备选型报告。

### 1.3 边界声明

- 四个情景是**分析性情景检验**（transparent scenario exercise），所有数值均为显式 `HYPOTHETICAL`；不是仿真、不是四家工厂、不预测 Pack EoL 真实性能；
- 目标部署层 Task/Condition/Safety/Evidence Gate 保持 `OPEN`（延续 13/18/20/23 的判定）；
- 比较对象是"同一任务边界下的具体配置"（人工 / 专用自动接触 / 配置化机器人），不是架构类别名称。

---

## 2. 研究输入核对与命名消歧

### 2.1 输入性质

P1–P7 七项条件性认识来自本轮交互研究，属**待审查的研究输入**。本节逐条对照 Framework 定义（09 §5）、原始证据与可写结论强度；聊天中的教学推论不自动成为工业研究发现。

### 2.2 命名消歧（必读）

- **本文件的 P1–P7** = [09 §5](./09_framework_v1_input_requirements.md) 的七个**生产条件字段**。
- **17/18/20/23 号文件中的 P1–P6** = **专利/配置编号**（P1=CN117718986B、P2=CN109856554A、P3=CN117970112A、P4=WO2024259675A1、P5=WO2025194672A1、P6=Festo/HAHN），与本文件 P 编号无关。

### 2.3 本文件引用的非 S-ID 原始来源（一次性登记，逐项注明首核出处）

| 来源 | 证据身份 | 用途 | 首核出处 |
| --- | --- | --- | --- |
| [CN212872555U](https://patents.google.com/patent/CN212872555U/zh) | `PATENT` 设计披露 | 专用设备预装三插头、移动 Pack 选插——P1/P2/P7 反例 | 19 号 §2 |
| [CN117031093B](https://patents.google.com/patent/CN117031093B/zh) | `PATENT` 设计披露 | 可切换插接连接器（模组实例）——P1/P7 反例 | 19 号 §2 |
| [CN117054877A](https://patents.google.com/patent/CN117054877A/zh) | `PATENT` 设计披露 | 测试柜按电池类型切换电气路径——变化落在电气层的例证 | 20 号 §2 |
| [DMC blog/20983](https://www.dmcinfo.com/blog/20983/everything-you-need-to-know-about-ev-battery-and-bms-testing-in-validation-and-production-scenarios-2/) | `SUPPLIER DISCLOSURE` | 可配置测试序列示例（列有 Pack Connection Check） | 17 号 §2（Example System 行） |
| [DMC our-work](https://www.dmcinfo.com/our-work/electric-vehicle-pack-end-of-line-test-with-dmcs-battery-production-tester/) | `SUPPLIER DISCLOSURE` | 已交付项目：MES 流程就绪查询、按料号选测试序列——配方层变化的例证；**不证明外部插头机械完成、电气接受或高压安全许可** | 20 号 §2 |

两个 DMC 来源互不拼接为同一工位许可链（23 §3.5 纪律）。其余引用全部使用已有正式 Source/Claim ID：S011、S019–S020、S024、S027、S031、S036；C009、C024、C026、C028。

---

## 3. P1–P7 条件性评价矩阵

矩阵每行固定 8 个字段：①Framework 原有定义；②生产条件如何变化；③可能产生价值的配置能力；④替代配置反例；⑤使潜在优势消失或反转的因素；⑥最小验证数据；⑦允许的证据身份与当前结论强度；⑧与 RQ1/RQ2/RQ3 的关系。结论强度取所需字段中最弱一项的强度（[13 §4](./13_framework_v1_decision_table_draft.md)）。

| 条件 | ①Framework 定义（09 §5） | ②条件变化轴 | ③可能产生价值的配置能力 | ④替代配置反例 | ⑤价值消失/反转因素 | ⑥最小验证数据 | ⑦证据身份与当前结论强度 | ⑧RQ 关系 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P1 产品/接口多样性 | 决定机械专用化、参数化和工具兼容的价值（关联 R4） | 三层各自变化：机械接口（形状/位置/姿态）；电气连接与测试路径；软件配方/MES/流程（20 §3） | 机器人快换插头+视觉对插（S036=WO2025194672A1）+可重编程，适配**机械层**在线变化 | 专用预装多插头+移动 Pack 选插（CN212872555U）；可切换插头（CN117031093B）；电气层由测试柜切换（CN117054877A）；配方层由 MES 流程就绪查询+按料号选序列办理（DMC；与插头机械完成/电气接受/许可判据无关） | 变化只落在电气/配方层→机械柔性不相关；机械变化超出机器人视觉/工具能力→同样失效；变型本身制造机器人性能方差（S027 Table III：连接器 B 优化前搜索成功率 49%，22 §5.4） | 目标产品组合的分层变化清单、每类变化频率、每配置适配动作与实测时间 | `EVIDENCED MECHANISM`（多来源设计先例）+`ANALYTICAL INFERENCE`（19/20）；强度 `CONDITIONAL`：多样性单独不能支持选型 | RQ1（task characteristic）；RQ2（condition） |
| P2 换型频率与批量结构 | 决定换型时间与换型资源是否重要 | 换型次数 K、批量、换型时长与人力/工具资源、换型后再标定/再验证负担 | 短换型配置在高频换型下摊薄换型损失（§4.1 机制）；可重编程缩短配方/电气层换型 | 专用预装多插头把"换型"变成 Pack 定位切换（CN212872555U）；机器人学习方案另有数据与在线优化负担（S027：≈3 h/1,000 样本、≈1.5 s/周期，22 PC-3） | K 低/大批量时单件节拍权重上升（§4.1 K=2 反转）；机器人换型若含再标定/安全再验证，短换型假设即失效 | 真实换型频率与批量、每配置换型时间（含人员/工具/验证）、换型后验证代价 | `HYPOTHETICAL` 数值演示 +`ANALYTICAL INFERENCE`；强度 `CONDITIONAL`，双方都不能证明总体更优 | RQ1/RQ2；换型经济结构→RQ3 |
| P3 节拍/周期/波动 | 决定单循环性能、缓冲和并行化需求 | 五类时间分开记账：正常任务时间；换型停机；失败重试与恢复；调度等待与瓶颈；工位产出 vs 整线产出 | 无类别固有优势；单件节拍是配置属性（S027 优化后 9–11 s 只属该配置，不可迁移） | 节拍优势可被换型/重试/调度抵消（§4.1/§4.2 机制）；单件快≠周期总时间短 | 失败恢复时间大→有效节拍恶化；其他工位是瓶颈时本工位节拍不敏感 | 同任务边界下各配置五类时间及波动分布 | 机制 `ANALYTICAL INFERENCE`；同口径目标数值全部 `UNKNOWN`；强度 `CONDITIONAL` | RQ2 |
| P4 单工位 vs 多工位组合 | 决定移动性和跨任务复用是否被实际利用 | 各工位请求时刻与重叠；服务占用；跨站移动/对位；允许等待与缓冲；共享故障范围 | 移动机器人跨工位资源复用（潜在价值来自复用，不来自"能移动"本身） | 三台独立机构各自保有服务容量；"移动⇒优势"未被证实（C009 已 `DOWNGRADE_ASSUMPTION`） | 请求重叠+允许等待短→峰值冲突；跨站重定位要求按站重新满足 F1 定位与误差条件；共享机器人故障可能影响全部依赖站点（是否全站停取决于缓冲/应急/调度，§4.4） | 请求时序与重叠统计、服务占用与移动时间、允许等待/缓冲、故障隔离要求 | repo 无共享机器人三工位 Pack EoL 直接证据；`HYPOTHETICAL` 情景为主；不得写"移动⇒已证优势" | RQ1/RQ2；调度策略→RQ3 |
| P5 greenfield/brownfield 集成 | 决定工装、围护、传感器和机器人布局的实施代价 | 安装与运动空间；既有托盘/工装兼容；与 PLC/测试仪/MES 集成；安全围护互锁；调试、验证与停线；运营损失 | 机器人或可复用既有 human-oriented 布局（候选机制，C009 降级后仅作候选） | 专用模块局部升级可能免于重建围护与全站再验证；手工/自动接线与 trolley/conveyor/AGV 上料可组合（C024/S019–S020）——改造轴与 adaptation 轴独立 | 机器人导入需新空间、围护、集成与停线，改造更贵时反转；但不得默认"所有专机改造都更简单"（11 规则 0） | 同站两方案的空间、围护、集成、验证与停线代价（含安全再验证） | `RETAIN_DIRECT`（S019–S020 组合性）+`ANALYTICAL INFERENCE`；强度 `CONDITIONAL`，无 brownfield 同条件对比数据 | RQ2；实施路径→RQ3 |
| P6 可用率/维护/人工介入 | 决定复杂感知/控制的收益能否覆盖恢复和维护负担 | 六指标分开记账：First-attempt Success Rate；Final Completion Rate；Task Recovery Time；MTTR；Manual Intervention Rate；Operational Availability | 无类别固有优势；差异在失败检测、自动重试与介入路径（CN117718986B 退回重插 vs CN109856554A 超差人工干预——不同设计，非同条件比较） | 复杂感知/控制增加故障模式与维护；求高首次成功率≠高完成率/可用率（§4.2 机制）；共享设备故障影响范围更大（耦合 P4） | 失败落入长人工恢复时，首次成功率优势可能被少数失败事件的高恢复代价吃掉；六指标口径不对齐则"成功率"不可比 | 同条件下六指标各自数值、恢复时间分布、每个失败路径的许可撤销与复位时间 | `CONDITIONAL`（机制先例 C026/C028、S024/S031）；目标数值 `UNKNOWN` | RQ2；维护策略→RQ3 |
| P7 产品生命周期与未来变化不确定性 | 决定固定投资与可重构性的长期价值 | 未来变化类型（软件配方/电气路径/机械几何/新工具模块）与发生概率；再标定、再验证与停线代价；设备长期复用范围 | 机器人换工具+重编程对机械界面变化的候选价值（S036） | 模块化专机可重构（CN212872555U 预装、CN117031093B 切换）；配方/电气层变化由 MES/测试柜吸收，无需物理重构；不确定性本身不构成机器人长期价值证据 | 变化集中于电气/配方层→机械可重构无关；任何触及 HV/许可路径的变更两方案均需再验证；生命周期成本优势无法单凭构型证明 | 分层变化预测（类型+概率）、每配置适应成本（含再验证与停线） | `CONDITIONAL`/`ANALYTICAL INFERENCE`；生命周期成本对比 `UNKNOWN`；必须比较模块化专机与可重构机器人 | RQ2；长期实施→RQ3 |

**矩阵结论**（`ANALYTICAL INFERENCE`）：七条条件轴共同点的可写形式是"变化落在哪一层、由谁吸收、剩余负担是什么、同条件实测是多少"（继承 19/20），而不是"机器人更灵活/换型更快"之类的类别常识。任何单轴上的可行性都不能直接升级为总体配置优势。

**变量类型区分（反混淆规则）**：P1–P7 给出的**外部生产条件**（批量、换型频率、请求分布、布局与维护目标、未来变化）必须与**配置相关性能输入**（某配置的成功率、恢复能力、换型时间、节拍）分开记账。矩阵中"目标数值 `UNKNOWN`"指前者缺观测、后者缺同条件测量；四情景中 8 s/12 s/99%/96% 等是**为演示机制而设定的配置性能假设**，不是外部生产条件的观测值。混淆二者会把条件性情景变成变相排名。

---

## 4. 四个有区分能力的情景测试

### 4.0 情景纪律

- 每个情景针对**同一任务边界**的一个分析性问题；比较对象保持配置级；
- 全部数值 `HYPOTHETICAL`：只演示机制方向与反转，不是工厂观测、不是预测；
- 每个情景固定输出 8 项：同一任务边界与比较对象 / 变化的输入（生产条件取值或配置性能假设） / 保持不变的条件 / 相对优势如何变化 / 推翻当前倾向的额外条件 / 对应 Function Card 与 P 条件 / Gate status 与 Claim evidence status / 下一步最小验证数据；
- 三种状态分开标注：Gate status 只取 `PASS/OPEN/FAIL`（指目标部署层）；`CONDITIONAL` 等属于主张证据状态（13 §4），不是 Gate 状态；四个情景的 Scenario identity 一律为 `HYPOTHETICAL`；
- 四个情景**不是**严格控制变量的真实工业实验，而是同构的透明假设推演，只用于检查评价规则能否解释相对适用性的方向变化；
- 情景结论不改变任何目标部署 Gate 状态（仍 `OPEN`）。

### 4.1 Scenario A — Changeover vs Cycle Time（换型频率 vs 单件节拍）

**任务边界**：同一 Pack EoL 工位的**连接器插接任务段**（connector adaptation），总产量 N=6,000 件；比较"专用自动接触机构"与"配置化机器人操作"。模式：`T = N × t_cycle + K × t_changeover`（单位全部秒）。

**时间口径声明**：t_cycle=8 s/12 s 仅代表**插接任务段**的同口径单件时间（`HYPOTHETICAL`），不是完整 EoL 周期。连接状态检测、测试许可、断开与归位、等待/缓冲等其他时长**未独立计入**；若要比较完整周期，必须显式假设两配置在这些段及其时长上相同。`T` 因此不是整线产能预测，不得写成真实产能或实际设备选型结论（在给定假设下计算与临界点 K*=14.2857 成立，不更换模型）。

| 配置 | N | t_cycle | t_changeover | K=2 计算 | K=2 合计 | K=20 计算 | K=20 合计 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 专机 | 6,000 | 8 s | 1,800 s（30 min） | 48,000 + 3,600 | 51,600 s = 860 min ≈ 14.33 h | 48,000 + 36,000 | 84,000 s = 1,400 min ≈ 23.33 h |
| 机器人 | 6,000 | 12 s | 120 s（2 min） | 72,000 + 240 | 72,240 s = 1,204 min ≈ 20.07 h | 72,000 + 2,400 | 74,400 s = 1,240 min ≈ 20.67 h |
| 差值 | — | +4 s | −1,680 s | — | 专机短 20,640 s（344 min ≈ 5.73 h） | — | 机器人短 9,600 s（160 min ≈ 2.67 h） |

**临界点核对**（`HYPOTHETICAL` + `ANALYTICAL INFERENCE`）：

- 无差别条件：48,000 + 1,800K = 72,000 + 120K → 1,680K = 24,000 → **K\* = 14.2857…**
- 整数校验：K=14 → 专机 73,200 s vs 机器人 73,680 s（专机短 480 s）；K=15 → 专机 75,000 s vs 机器人 73,800 s（机器人短 1,200 s）。
- 模型内结论：**K ≤ 14 专机短；K ≥ 15 机器人短**。一般式 K\* = N·(t_R − t_D)/(t_D,c − t_R,c)，K\* 随 N 增大而升高。

**读取方式（机制，不是预测）**：高频换型把 1,680 s/次的换型差放大为优势来源；低频大批量把单件 4 s 差放大。换型差本身配置相关：专用预装多插头把一部分"换型"变成 Pack 定位切换（CN212872555U，`EVIDENCED MECHANISM`）；机器人换型若含再标定/再验证，120 s 假设即失效。**模型未包括**：失败恢复、并行作业/重叠换型、设备可用率、其他工位瓶颈与整线产出、经济成本（投资/人员/工具）。

| 固定输出项 | 内容 |
| --- | --- |
| 同一任务边界与比较对象 | 同站连接任务、同 N=6,000、同产品组合；专机 vs 配置化机器人 |
| 变化的生产条件 | 换型次数 K（2 次 vs 20 次） |
| 保持不变的条件 | 单件节拍、换型时长、质量/安全条件、单一串联资源 |
| 相对优势如何变化 | K=2 → 专机短 ≈5.73 h；K=20 → 机器人短 ≈2.67 h；优势方向反转 |
| 推翻当前倾向的额外条件 | 机器人换型含再验证；专机改预装多插头（换型≈定位）；失败/恢复不对称；其他工位是瓶颈 |
| 对应 Function Card 和 P 条件 | 机械接口/定位变化→可能改变 F1 要求；电气路径与配方变化→不一定改变 F1，改查测试系统与 F2 条件（§5 与 P1/P7 三层）；条件 P2、P3 |
| Gate status / Claim evidence status | Gate（目标部署层）全部 `OPEN`（功能层 Task 可描述）；可写结论强度 `CONDITIONAL`；Scenario identity = `HYPOTHETICAL`，推演非部署判定 |
| 下一步最小验证数据 | 同任务下两配置真实 t_cycle 与 t_changeover（含换型资源与再验证）、真实 K 分布 |

### 4.2 Scenario B — Success Rate vs Recovery Burden（首次成功率 vs 恢复负担）

**任务边界**：同一连接任务。`HYPOTHETICAL` 输入：机器人首次成功率 99%、失败后需较长人工恢复；专机 96%、可快速自动重试——以上为**配置性能假设**（configuration-performance inputs），不是外部生产条件。**题目未提供最终完成率与统计口径 → 不得自行推算最终完成率（保持 `UNKNOWN`）**。

分析要点：

- **度量分离（P6）**：99% 与 96% 只是 First-attempt Success Rate。工业适用性还取决于 Final Completion Rate、恢复时长、MTTR、介入率、可用率。"99%>96% ⇒ 机器人更适合"属于单一指标放大，禁用。
- **恢复负担不对称的机制示意（`HYPOTHETICAL`）**：记 r_R、r_D 为每失败任务的恢复耗时，期望恢复负担 ≈ 1%·r_R vs 4%·r_D；当 **r_R > 4·r_D** 时机器人期望恢复负担更大。3 个百分点的首次成功率优势是否足额，取决于每失败事件的代价（含安全复位），该代价目标值 `UNKNOWN`。该示意**依赖**三个假设：失败事件相互独立、每次失败对应同一定义的单次恢复事件、成功率与恢复时长取自同一统计口径（均为 `HYPOTHETICAL`）；若恢复发生重叠或连续重试或口径不一致，该比较不成立。**不得由首次成功率直接推算最终完成率**（保持 `UNKNOWN`）。
- **F1 耦合**：谁判定"失败"？S027 搜索成功判据是触觉/运动层的（相对运动未触发力阈值即 `valid=True`），不等于插合完成（23 §3.2）；不同判据的"失败率"不可直接比较。
- **F2 耦合**："插入未失败"不等于电气接受/测试许可；失败后的恢复路径还包括许可撤销、停测/断能、安全退回——这正是"机器人失败需较长人工恢复"的候选机制来源。CN117718986B 自动退回重插与 CN109856554A 超差人工干预是不同设计的披露，非同条件比较。
- **P3 耦合**：恢复时长进入有效周期与波动，逾期恢复形成工位瓶颈。

| 固定输出项 | 内容 |
| --- | --- |
| 同一任务边界与比较对象 | 同站连接任务；两配置各带假定的失败与恢复路径 |
| 变化的输入（配置性能假设，非外部生产条件） | 首次成功率（99% vs 96%）与恢复方式（长人工恢复 vs 快速自动重试），均为 `HYPOTHETICAL` 配置性能输入 |
| 保持不变的条件 | 任务内容、正常节拍、质量/安全要求 |
| 相对优势如何变化 | 单看成功率倾向机器人；纳入恢复负担后排序取决于 r_R/r_D 与失败后果，方向可能反转 |
| 推翻当前倾向的额外条件 | 机器人失败后现场可达性差、需断电复位、恢复含安全再验证；专机自动重试可能掩盖电气层失败（F2：机械完成≠电气接受）；统计口径不对齐时数值不可比 |
| 对应 Function Card 和 P 条件 | F1（失败检测/卡滞判据）、F2（机械/电气/许可/异常处置六状态）；条件 P3、P6 |
| Gate status / Claim evidence status | Gate（目标部署层）全部 `OPEN`；可写结论强度 `CONDITIONAL`；本情景演示 Evidence Gate 对"单一指标放大"的拦截规则；最终完成率 `UNKNOWN`，不得推算 |
| 下一步最小验证数据 | 两配置的首次与最终完成率（对齐到同一状态定义）、恢复时间分布、介入率、每失败路径的许可撤销与安全复位时间 |

### 4.3 Scenario C — Retrofit vs Lifecycle Reconfigurability（改造 vs 生命周期可重构）

**任务边界**：既有 Pack EoL 工位升级连接/换型能力；比较"专用模块局部升级"与"导入机器人系统"。保持不变：现有工位、测试柜与安全壳的基本约束。

- **当前负担（P5）**：安装与运动空间、既有工装兼容、PLC/测试仪/MES 集成、安全围护互锁、调试验证与停线。局部升级可能保留既有围护与工装；导入机器人通常要求新增运动空间、安全外设与全站再验证——但不得默认专机改造一律更轻（11 规则 0：不凭类别标签填能力）。
- **未来负担（P7）**：变化分三层。电气路径由测试柜切换（CN117054877A）、配方流程由 MES 就绪查询与按料号选序列（DMC）吸收，不要求物理重构——二者均**不证明插头机械完成、电气接受或高压安全许可**；只有机械几何层才有"模块化专机（CN212872555U/CN117031093B） vs 机器人快换+视觉（S036）"之争。未来不确定性本身不构成机器人长期价值证据（19/20 纪律）。
- **F2 门槛**：任何触及 HV/安全许可路径的变更，两方案都要重新验证许可链与撤销逻辑（23 §3.2/§4.2），该代价目标值 `UNKNOWN`。
- **可写的条件性倾向**：机械接口变化少而稳定 → 倾向评估专机模块升级（验证负担可能更低，`CONDITIONAL`）；机械界面高频宽谱变化且有场地 → 机器人适配进入候选（`CONDITIONAL`）。**不可证明**：生命周期成本谁低、未来变化概率与范围（`UNKNOWN`）。

| 固定输出项 | 内容 |
| --- | --- |
| 同一任务边界与比较对象 | 既有工位升级连接/换型能力；专机模块升级 vs 导入机器人系统 |
| 变化的生产条件 | 当前改造负担（空间/围护/集成/停线）；未来变化层级与不确定性 |
| 保持不变的条件 | 现有工位、测试柜、安全壳基本约束、任务内容 |
| 相对优势如何变化 | 变化集中在配方/电气层 → 两方案物理层都无需重构，差异缩小；机械层高频宽谱变化 → 机器人适配更具候选价值 |
| 推翻当前倾向的额外条件 | 未来变化集中在电气/配方层；机械变化超出机器人适配能力；专机模块升级本身需全站安全再验证 |
| 对应 Function Card 和 P 条件 | F1（新接口定位与工装兼容）、F2（变更后的安全再验证与许可链审计）；条件 P5、P7 |
| Gate status / Claim evidence status | Gate（目标部署层）全部 `OPEN`；可写结论强度 `CONDITIONAL`；生命周期成本与未来变化概率 `UNKNOWN` |
| 下一步最小验证数据 | 同站两方案空间/围护/集成/验证/停线代价；分层变化预测与每配置适应成本 |

### 4.4 Scenario D — Three-station Resource Sharing（三工位资源共享）

**任务边界**：三个同型 Pack EoL 测试工位的连接任务；比较"三台独立专用机构"与"一台共享移动机器人"。保持不变：每工位任务内容、每件服务内容、总需求。

- **子条件 (a)**：请求经常重叠、允许等待短 → 共享机器人峰值需求+跨站移动可能突破等待上限，三台独立机构各自保有容量；
- **子条件 (b)**：请求可错峰、存在服务窗口 → 共享机器人**可能**减少重复设备与占地。这是**机制性判断**（Claim evidence status `CONDITIONAL` + `HYPOTHETICAL`）：仅当各站允许等待与缓冲能吸收跨站移动/对接时间、且该配置的移动与对接能力满足要求时才成立，不是已证优势。
- **必分析量**：请求时刻与重叠统计、服务占用时间、跨站移动/对位/重定位时间、允许等待与缓冲、故障传播。每站具有**自身的定位与误差条件**（每站来料/工装可能不同），移动服务需要**按站重新满足 F1 要求**，而非移动动作必然产生同样的残余误差。
- **安全（F2）**：移动机器人跨 HV 测试区 → 多点许可/围护与许可撤销复杂度随站点数增长。
- **故障影响范围（P6）**：共享设备故障**可能**影响多个依赖其连接/断开服务的工位；是否造成三站完全停产，取决于任务阶段、缓冲、备用设备、人员应急路径与调度机制（均 `UNKNOWN`）。独立机构故障通常只直接影响本工位。共享度的代价是故障影响范围**可能**扩大，但不等于三站必然完全停产。共享服务中断**不必然改变**各工位**已有**的测试许可状态：许可与安全状态由各站控制系统独立决定（目标逻辑 `UNKNOWN`）。
- **禁止**：用机器人平均利用率替代峰值请求冲突与最大等待分析（平均利用率高 ≠ 峰值不违约）；不得把"能移动"写成已证优势（C009 已降级）。

| 固定输出项 | 内容 |
| --- | --- |
| 同一任务边界与比较对象 | 三个同型工位的同一连接任务；三台独立专机 vs 一台共享移动机器人 |
| 变化的生产条件 | 请求重叠程度与允许等待（子条件 a/b） |
| 保持不变的条件 | 每工位任务与服务内容、总需求、单件服务时间 |
| 相对优势如何变化 | 错峰+宽松窗口 → 共享复用**可能**具候选价值（机制判断 `CONDITIONAL`，`HYPOTHETICAL`）；重叠+短等待 → 峰值冲突与跨站移动成本可能使独立机构占优 |
| 推翻当前倾向的额外条件 | 跨站移动/对位时间大；共享机器人故障造成的多工位停机损失高（是否全停取决于缓冲与应急路径）；多点安全许可与围护显著抬高集成成本 |
| 对应 Function Card 和 P 条件 | F1（每站具有自身定位与误差条件，移动服务需按站重新满足）、F2（多点许可/撤销/异常处置）；条件 P4、P3、P6 |
| Gate status / Claim evidence status | Gate（目标部署层）全部 `OPEN`；机制性复用价值：`CONDITIONAL`（`HYPOTHETICAL`）；实际部署优势：`NOT SUPPORTED BY CURRENT EVIDENCE`（无同任务、同工况直接证据）；情景整体 `HYPOTHETICAL`，不得产出"移动⇒优势"结论 |
| 下一步最小验证数据 | 请求时序/重叠统计、服务占用与跨站移动时间、允许等待与缓冲、故障隔离与停机损失 |

---

## 5. F1/F2 复用（Day 3 → Day 4 的连接，不重抄功能卡）

| 情景 | F1 — Residual Connector Pose Uncertainty 的角色 | F2 — 机械完成/电气接受/测试许可 的角色 |
| --- | --- | --- |
| A 换型 vs 节拍 | 机械接口/定位变化→可能改变 F1 要求（新的上游定位与插头–插座相对误差条件，浮动/视觉/力控分工进入换型代价评估）；电气路径与配方变化→不一定改变 F1 | 电气路径/配方变化→改查测试系统与 F2 条件；换型后机械完成判据与许可链是否随型号变化、是否需重新验证，取决于受影响的功能与许可链（23 §7 待证字段 4/5） |
| B 成功率 vs 恢复 | 失败检测、卡滞判据与"搜索成功"口径属于 F1；判据口径决定"失败率"可比性 | 机械完成≠电气接受；恢复路径含许可撤销、停测/断能与安全退回；六状态不可合并 |
| C 改造 vs 生命周期 | 新接口的定位方式与工装兼容性决定改造代价 | 变更后许可链与安全功能需重新审计；不能默认旧许可继续有效 |
| D 三工位共享 | 每站有自身定位与误差条件，移动服务需按站重新满足 F1 要求；浮动/视觉/力控按站重新评价 | 多点许可/围护、逐站许可撤销与异常处置；共享故障**可能**使多个依赖该服务的工位停等（是否全停取决于缓冲/应急/调度），但不推断共享故障必然改变各工位**已有**的测试许可状态（各站许可由本站控制系统决定，`UNKNOWN`） |

**禁止推断（沿用 23 §3.6 与本轮输入）**：

1. 不得把机械插合成功当作测试安全许可；
2. 不得将跨专利的机械检测、电气检查与 PLC 信号拼成一个已验证工位（18 §3）；
3. 不得从专利设计直接得出可靠性、成本或部署成熟度（01 §14.3）。

---

## 6. Framework v1.0 条件性评价能力检验

### 6.1 四情景对四 Gate 的检验结果（三类状态分开标注）

三类状态语义：**Gate status** 只取 `PASS/OPEN/FAIL`（下表均指目标部署层；功能层 Task 可描述）；**Claim evidence status** 取 `SUPPORTED FOR THIS CONFIGURATION / CONDITIONAL / NOT SUPPORTED BY CURRENT EVIDENCE / UNKNOWN` 等（13 §4），不是 Gate 状态；**Scenario identity** 一律 `HYPOTHETICAL`。

| 情景 | Scenario identity | 目标部署层 Gate status（Task / Condition / Safety / Evidence） | 本情景可写结论的 Claim evidence status |
| --- | --- | --- | --- |
| A | `HYPOTHETICAL` | 全部 `OPEN`；Condition Gate 规则在情景层得到演示（换型频率反转） | `CONDITIONAL`：给定假设下换型频率改变同口径任务段总时间的方向；不得外推为整线产能 |
| B | `HYPOTHETICAL` | 全部 `OPEN`；Safety 待证项=恢复中的许可撤销 | `CONDITIONAL`：恢复负担被显式条件化；最终完成率 `UNKNOWN`，不得推算 |
| C | `HYPOTHETICAL` | 全部 `OPEN`；Safety 待证项=变更后的安全再验证 | `CONDITIONAL`：变化层级决定物理重构需求；生命周期成本 `UNKNOWN` |
| D | `HYPOTHETICAL` | 全部 `OPEN`；Safety 待证项=多点许可 | 机制性复用价值 `CONDITIONAL`（`HYPOTHETICAL`）；实际部署优势 `NOT SUPPORTED BY CURRENT EVIDENCE`（无同任务、同工况直接证据），不主张共享机器人部署更优 |

### 6.2 现有规则能解释什么

- 条件取值或配置性能假设变化 → 相对优势方向反转（Scenario A/B）；
- 单一指标不能决定适用性，必须对齐统计口径与状态定义（Scenario B）；
- 变化层级决定选型相关层：电气/配方层变化不产生物理重构需求（Scenario C，继承 20 §3）；
- 共享度同时带来资源复用与单点故障，移动性必须被任务实际使用才有价值（Scenario D，C009 纪律）。

即 [13](./13_framework_v1_decision_table_draft.md) 的 Condition Gate 规则（"技术可行 ≠ selection advantage"）在**情景层得到演示**：四情景都能写出"若条件 X，则倾向方向 Y"的可追踪句子，且都能指出推翻条件与最小验证数据；这是内部适用性的演示，不是外部效度证据。

### 6.3 不能解释/不能做的

- 缺目标参数时无法产出 `SUPPORTED FOR THIS CONFIGURATION`（13 §4）；
- 不能给权重、评分或架构排名；四情景不是对 Framework 工业有效性的实证验证；
- 方法学结论（`ANALYTICAL INFERENCE`）：四个透明假设情景展示了 Framework v1.0 条件字段的**内部适用性与初步区分能力**；不能独立证明 Framework 的工业决策有效性、评价充分性或外部效度；目标部署层四 Gate 仍 `OPEN`；情景假设不构成任何架构的部署证据。

---

## 7. 证据分层纪律（四层内容）

| 层 | 名称 | 定义与要求 |
| --- | --- | --- |
| L1 | `SOURCE-SUPPORTED FACT / EVIDENCED MECHANISM` | 仓库真实来源支持；注明 Source ID、具体文献/专利与页码、章节或位置（01 §11 精确位置规则）。专利=设计披露，不等于部署/性能 |
| L2 | `ANALYTICAL INFERENCE` | 本项目方法性推理；必须标注并给推理链，不得与披露事实混同（例：K\* 一般式、P4 峰值冲突分析） |
| L3 | `HYPOTHETICAL SCENARIO INPUT` | 显式情景假设数值，仅用于演示机制方向与反转；不得当作工厂观测（例：Scenario A 全部数值、Scenario B 的 99%/96%） |
| L4 | `UNKNOWN` | 必需输入未公开/未取得；不得转写为正面或负面事实；`UNKNOWN ≠ FAIL`（13 §4） |

使用规则：每个可写句先标层；结论强度由所需字段中最弱层决定；跨层/跨来源拼接禁止（18 §3）；本文件 Scenario A/B/D 的全部数值均属 L3，任何论文使用都必须随附"假设值 + 未包含因素"的完整声明。

（注：L1 定义沿用本轮指示原文；L2–L4 与仓库既有分层纪律一致——16 §3 的 FACT/推理/UNKNOWN、22 §5.7、23 头部的证据分级。若原指示对 L2–L4 有不同命名，以原指示为准。）

---

## 8. Thesis Writing Reuse

### 8.1 映射表

| 论文部分 | 可复用内容 |
| --- | --- |
| Methodology | Condition Gate 的 8 字段条件记录；`HYPOTHETICAL` 情景检验技术（透明输入、显式排除项）；证据四层与写句强度规则 |
| Pack EoL Case Assessment | P1–P7 矩阵骨架作为条件卡模板；Scenario A/B 作为"换型频率反转、单一指标放大"的条件性演示 |
| Discussion / Implementation | P5/P7 改造 vs 生命周期策略；P6 恢复负担与可用性管理；P4 共享度权衡（RQ3 输入） |
| Limitations | 情景非实证；目标参数与同条件性能 `UNKNOWN`；四 Gate 目标部署层未闭合 |

### 8.2 英文候选素材（措辞审慎）

> Whether a robot adds value at a pack end-of-line connector station depends on which condition changes and who absorbs the change. Interface variety alone does not favour robots: dedicated designs with pre-installed or switchable plugs and test cabinets that route electrical paths also absorb variation (CN212872555U; CN117031093B; CN117054877A). A transparent two-term model, T = N·t_cycle + K·t_changeover, shows that the direction of a time advantage can reverse with changeover frequency and that the result holds only within the stated assumptions, excluding failure recovery, parallel work, availability, line bottlenecks and cost (hypothetical inputs).

> Production-condition inputs must remain separated from configuration-performance inputs: batch size, changeover frequency and request distribution are external production conditions, whereas success rate, recovery capability and changeover time are properties of a specific configuration; mixing the two turns a conditional scenario into a disguised ranking (analytical inference, not an observed result).

> A three-layer view of product change — mechanical interface geometry, electrical paths, and software recipes — restricts which flexibility actually matters. Mechanical changes can alter the pose-alignment function (F1); electrical-path changes may be absorbed by the tester and recipe changes by MES-driven readiness checks and test-sequence selection. Neither demonstrates plug seating, electrical acceptance or high-voltage permission, which remain F2 conditions requiring their own evidence (analytical inference).

> Shared-mobility advantage is conditional, not categorical: whether one robot serving several stations outranks independent mechanisms depends on request overlap, travel and re-docking time, allowable waiting and buffers, and the scope of failure propagation; average utilization cannot substitute for peak-conflict and maximum-waiting analysis (hypothetical scenario reasoning).

> First-attempt success rate alone cannot rank configurations: with hypothetical rates of 99% under long manual recovery versus 96% under fast automatic retry, the comparison depends on the recovery burden per failure and on which state "success" refers to — tactile/motion-level search success is distinct from mechanical seating, electrical acceptance and test authorization (Kienle et al. 2025; F1/F2 function cards).

---

## 9. Open Items 与交接

### 9.1 Day 4 新增的最小待证数据（五类，全部 `UNKNOWN`，在 23 §7 七项之上）

| # | 待证数据 | 对应条件/情景 |
| --- | --- | --- |
| D1 | 真实换型频率、批量与每配置换型时长（含换型后验证代价） | P2 / Scenario A |
| D2 | 同口径五类时间分解：任务段 / 换型 / 失败恢复 / 调度等待与瓶颈 / 工位–整线 | P3 / Scenario A、B |
| D3 | 恢复统计：首次与最终完成率（对齐到同一状态定义）、恢复时间分布、介入率 | P6 / Scenario B |
| D4 | brownfield 同站改造代价：空间 / 围护 / 集成 / 验证 / 停线 | P5 / Scenario C |
| D5 | 三站共享的请求时序与重叠、服务占用与跨站移动/对位时间、允许等待与缓冲 | P4 / Scenario D |

"同条件可比指标集"由 D2/D3 合并承载。23 §7 的七项待证字段保持原样，不因本文档改变。

### 9.2 Day 4 结论状态

条件推理结构与四情景检验完成（`ANALYTICAL INFERENCE`）；四情景展示了 Framework v1.0 条件字段的内部适用性与初步区分能力，不能独立证明其工业决策有效性、评价充分性或外部效度；目标部署层四 Gate 继续 `OPEN`；不选架构赢家；不新增 Gate/权重/Claim ID。本文档已获准单独提交；下一阶段研究方向仍待人工审核决定。

### 9.3 Day 5 Evaluation Input Handoff（候选输入卡，不启动 Day 5）

下列卡片只把 Day 4 的条件矩阵与四情景转化为下一轮可检查的评价问题；**不预设架构优胜、不启动 Candidate A 全量分析、不替用户决定研究路线**。

| 字段 | 内容（候选起点） |
| --- | --- |
| Evaluation question | 在同一任务边界与可比条件下，人工 / 专用自动接触 / 配置化机器人在对接成功判据、恢复负担与换型负担上的差异，是否达到可被生产条件区分的大小？ |
| Same-task boundary | 制造端 `PACK`：测试连接器由待连接状态操作到被测试系统接受、测试后安全断开归位；完成判据与许可链目标值仍 `UNKNOWN`（23 §4 任务边界） |
| 比较对象 | Manual；Dedicated Automatic Contact；Configured Robot（三张基线卡 11 §3，同口径比较） |
| 何时才考虑共享移动机器人 | 仅当多工位请求可错峰、各站允许等待与缓冲能吸收跨站移动/对位时间、且多站受影响故障范围可接受时，作为**附加候选**；否则维持情景层讨论（C009 降级纪律、§4.4） |
| F1/F2 可复用的任务要求 | F1：上游定位残差、插头–插座相对误差、有效捕获范围、接触力、按站重新满足定位要求；F2：机械完成/电气接受/测试许可/启动反馈/许可撤销/异常处置六状态与判定者分离（23） |
| 优先测试的 P 条件组合 | P2×P3（换型频率×节拍，Scenario A 机制）；P3×P6（节拍×恢复，Scenario B）；P5×P7（改造×生命周期，Scenario C）；P4 仅在多工位假设成立后启用 |
| 已有直接来源与机制先例 | 直接：S011（任务存在性）、S019–S020（人工/自动并存，C024）、DMC our-work（MES 流程就绪查询+按料号选序列；不证明插头机械完成/电气接受/高压许可）；机制先例：S024/S027/S031（C026–C029）、S036 与 CN212872555U/CN117031093B/CN117054877A（设计披露，§2.3） |
| 所有关键 UNKNOWN | 23 §7 七项 + §9.1 D1–D5 |
| 最小新增证据清单 | 同站"信号与状态表"（18 §5 四问：对接接口归属、完成信号、各测试项许可条件、失败时谁停测/断能/退回）+ 同条件六指标（P6） |
| 现有 Gate 状态 | 功能层 Task 可描述；目标部署层 Task/Condition/Safety/Evidence 全部 `OPEN` |
| 下次研究必须回答的唯一关键问题 | 在相同 Pack EoL 连接任务和可比生产条件下，现有 F1/F2、P1–P7 和四 Gate 能否为人工、专用自动化、配置化机器人形成证据有界的相对适用性评价，并识别限制判断的最小证据缺口？（关键子问题保留：同配置的机械插合、电气接受、测试许可及失败恢复完整链——是否存在这样一份资料足以把一个目标部署 Gate 从 `OPEN` 转为可审查？） |

RQ3 实施策略入口（P5/P7 改造与生命周期、P6 可用性管理、P4 调度）与 Candidate A 的 `F0`–`F3` 准入保持挂起；按 `docs/collaboration_and_pacing.md` 每周一个核心问题的节奏，由下一周计划决定。
