# Week 9 Day 3 — Pack EoL Function Cards：F1 残余位姿误差 / F2 插合完成与测试许可

> 性质：研究草稿（Research Draft v0.2），是把总部案中两个功能的初版分析落成可复用 Function Card；不是论文 Results、不是正式 Claim、不是架构比较结论。
> 建立日期：2026-10-14（Week 9 Day 3 学习阶段收尾）
> 状态：`OPEN` —— 功能分解成立，具体工位参数与许可链证据仍缺失；不据此判任何 Gate `PASS`，也不判 `FAIL`。
> 相邻文件：本文复用现有框架字段，不新建 Framework。依赖 [09_framework_v1_input_requirements.md](./09_framework_v1_input_requirements.md)、[11_framework_v1_baseline_cards.md](./11_framework_v1_baseline_cards.md)、[13_framework_v1_decision_table_draft.md](./13_framework_v1_decision_table_draft.md)、[16_function_responsibility_audit_pilot_2026-09-30.md](./16_function_responsibility_audit_pilot_2026-09-30.md)、[17_completion_acceptance_authority_research_2026-09-30.md](./17_completion_acceptance_authority_research_2026-09-30.md)、[18_pack_eol_same_configuration_release_chain_audit_2026-09-30.md](./18_pack_eol_same_configuration_release_chain_audit_2026-09-30.md)、[20_pack_eol_target_unknown_search_and_variant_boundary_2026-09-30.md](./20_pack_eol_target_unknown_search_and_variant_boundary_2026-09-30.md)、[22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)。
> 证据分级纪律：本文件任何机制证据都标注证据身份（专利=设计披露；供应商页=供应商披露；跨行业论文=受限迁移机制）；`Candidate responsible component` 是候选责任者，不等于目标工位已确认的设备组成。

---

## 1. Day 3 Research Objective

### 1.1 为什么按「end state → function → responsibility → acceptance → selection-relevant condition」的顺序分析

直接比较“机器人 vs 专用机构”会犯类别标签错误：`industrial robot`、`humanoid`、`dedicated automation` 只是架构族名称，不自动携带能力（这是 [13 号文件](./13_framework_v1_decision_table_draft.md) 与 `C007/C008` 已定下的纠偏原则）。因此本案例不先问“谁更好”，而先问“任务要求得到什么目标状态（end state）”。

从目标状态出发，顺序等价于：

1. **required end state** —— 连接器/工位必须到达的最终状态（如“插头落入插座达到机械行程终点”“接口被测试仪接受”）；
2. **required function** —— 为达到该状态，系统必须完成的抽象功能（定位、导向、插合、检测、许可），不预设技术实现；
3. **responsibility allocation** —— 公开资料披露了哪些组件承担哪些功能，哪些留空；
4. **acceptance evidence** —— 什么信号/规则证明该功能已满足；
5. **selection-relevant condition** —— 该功能在什么生产/任务条件下才会成为架构选择的区分项，而非所有配置共同要求。

这样得到的是**可查证的功能与责任分配表**，而不是一个不可复现的“技术类别排名”。这直接服务 `13` 第 2 节固定填写顺序的第 4 步（功能卡）与第 5 步（Gate 判定）。

### 1.2 与已有 Framework 的关系（避免重复建设）

本文件**不是**一套新 Framework，只是在已有字段上填写两张具体的 Function Card：

- 任务/要求输入来自 [09](./09_framework_v1_input_requirements.md)：统一分析单元、R1–R6 可审计问题、P1–P7 生产条件、五层系统（transport / positioning / connector adaptation / test-safety cell / information）。
- 判定规则来自 [13](./13_framework_v1_decision_table_draft.md)：Task / Condition / Safety / Evidence 四 Gate 及其 `PASS / OPEN / FAIL` 语义；`OPEN` 时只允许功能分解与待证字段，不得作目标工位选型。
- 责任填法沿用 [16](./16_function_responsibility_audit_pilot_2026-09-30.md) 的九行试填与 [17](./17_completion_acceptance_authority_research_2026-09-30.md) 的四个字段（State claim / Observable evidence / Decision owner-next action / Failure route），以及 [18](./18_pack_eol_same_configuration_release_chain_audit_2026-09-30.md) 的六字段接口一致性（source configuration / physical interface / measured state / decision owner / permitted next action / failure route）。
- 责任分配的想法本身已见于 PPR / function allocation / capability-based allocation 等既有方法（见 [16 第 4 节](./16_function_responsibility_audit_pilot_2026-09-30.md)），**不主张“functional responsibility mapping”是项目原创理论**。

因此 F1、F2 只是把上述字段第一次落到「残余位姿误差」和「插合完成与测试许可」两个具体功能上，作为后续跨案例复用的样板，不新增 Gate、不新增 Claim ID、不新增评分权重。

### 1.3 本轮形成并可复用的两条评价逻辑

1. **F1 逻辑**：不能把上游已解决的定位问题全部归功于机器人；也不能因为机械浮动行程足够大就推断插接可靠。
2. **F2 逻辑**：不能把“机器人动作完成”“机械到位信号”“电气接受”“测试许可”视为同一个状态。

这两条逻辑直接服务 RQ1（哪些 task/process characteristics 决定 architecture suitability）与 RQ2（在哪些 technical/economic/quality/safety/integration conditions 下适用）。

---

## 2. F1 — Residual Connector Pose Uncertainty

### 2.1 功能目标

识别连接器在**接触前定位**与**接触过程中的受控对准**两个阶段实际面对的残余位姿误差，厘清该误差由哪一环节消除、消除到什么程度、仍残留什么，并判断“残余误差是否落入某配置可处理范围”；其**结束状态**是“满足进一步插入所需的对准条件”，而非“插合完成”。这是一个**定位/几何状态功能**，不是“机器人是否够准”的笼统问题。

### 2.2 关键区别 1：上游定位后的残余误差 ≠ 实际插头–插座相对误差

- **上游定位后的残余误差**：托盘/夹具/Pack 定位机构把连接器或插座带到某名义位姿后，实际位姿与名义位姿的偏差。它由“定位链”产生（如托盘重复精度、导向间隙、Pack 来料偏差）。
- **实际插头–插座相对误差**：插头坐标系相对插座坐标系的真实六维偏差，是“两者组合后的结果”——它取决于上游定位结果**和**插头抓取位姿、线束张力、连接器本身公差、插座朝向等共同作用。

二者不是同一个量。`ANALYTICAL INFERENCE`（源自 [22 第 7 节](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md) 第 1 条与 S027 的预定位方差讨论）：目标接口的这两个量当前均 `UNKNOWN`，不能把某配置的上游定位精度直接写成“插头–插座相对误差”。

### 2.3 坐标与误差维度（X/Y/Z、Roll/Pitch/Yaw）

需要指定的量（当前全部 `UNKNOWN`，不得虚构目标 Pack 工位数值）：

- 参考坐标系：机器人基座系 / 夹具系 / 插座本体系，三者必须声明，否则任何误差值无意义；
- 平移分量 X、Y、Z；
- 姿态分量 Roll（绕 X）、Pitch（绕 Y）、Yaw（绕 Z）；
- 误差的**范围**与**分布**（是均匀 ±2 mm 还是带偏置、带相关性的分布）——这决定用“最坏值”还是“概率”评价捕获范围。

唯一可引用的**具体数值先例**是 S027（跨行业）：该实验对中控台施加 `±2 mm`（连接器 B 因空间受限为 `±1.5 mm`）的均匀随机扰动（[22 §5.1](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)）。这是**该实验的设定值**，不是 Pack EoL 的误差参数，不能迁移。

### 2.4 候选责任分配（谁消除哪部分误差）

| 候选责任环节 | 候选负责组件 | 消除的误差类型 | 现有证据身份 |
| --- | --- | --- | --- |
| 托盘/夹具定位 | 定位销、托盘、夹具（`09` 五层中的 Positioning） | 大幅平移+部分姿态 | `UNKNOWN`（目标配置）；供应商方案只披露“存在定位”（Marposs/thyssenkrupp, `C024/S019–S020`） |
| 导向结构 | 引导面、插口倒角、浮动机构 | 引导面可吸收的姿态/平移错位 | `EVIDENCED MECHANISM`：[CN109856554A](https://patents.google.com/patent/CN109856554A/zh) 的水平/竖直浮动+位置检测 |
| 主动视觉定位 | 视觉系统 + 机器人 | 残余平移（及部分姿态） | `EVIDENCED MECHANISM`：[WO2025194672A1](https://patents.google.com/patent/WO2025194672A1/en)（S036）视觉测连接器位置后对插；S027 的 VISOR V20 二维视觉 |
| 力控/柔顺搜索 | 力传感 + 力控/柔顺 + 机器人 | 视觉/导向覆盖之后的剩余误差（通过“搜索—接触—判别”吸收） | `EVIDENCED MECHANISM`：[CN117718986B](https://patents.google.com/patent/CN117718986B/zh) 力传感+机械臂修正；S027 的 Probe Search 力控搜索 |

要点：上述是**并存的误差处理路径**（见 [22 §7 第 2 条](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)），不是互斥选项。评价必须按具体配置说明“哪一层消除哪部分误差”，而不是按“专机 vs 机器人”预设答案。

### 2.5 关键区别 2：标称浮动行程 ≠ 实际有效捕获范围

`ANALYTICAL INFERENCE`：

- **标称浮动行程**是机构的机械设计量（如导向面能滑动的物理距离）；
- **实际有效捕获范围**是“在给定插头姿态、线束张力、接触力限制下，浮动机构／视觉／力控真正能稳妥捕获并导向对齐的范围”。

二者可能相差很大：姿态偏差、线束侧向力、插口倒角形状、允许接触力都会缩小“有效”范围。因此**“浮动行程 ≥ 名义位置偏差”不能单独推出“可靠插接”**（对应 [22 §7 第 3 条](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)）。S027 中插座朝向（B 为 90° 侧向开口）与配合余量（A 大余量）独立影响成功率，即是几何容差之外还有朝向/余量/表面状态等维度的直接实验例证。

### 2.6 接触力、卡滞、对准判据、超限处理

- **允许接触力**：目标值 `UNKNOWN`；仅 S027 报告了 Z 向力统计（µF，逐连接器见 [22 §5.2 Table I](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)），为跨行业值，不迁移。
- **卡滞（jam）与误判**：[S024](https://doi.org/10.20965/jrm.2012.p0666) 用“相对位移 PWA 模型 + 力上限 + 多传感器监测”区分**完成 vs 卡滞**（`C026/RETAIN_CONDITIONAL`），是机制级先例，不是目标工位判据。
- **对准判据**：不同设计给不同判据（见 F2 的机械完成判据）；F1 只关注“对准是否达成”，对准与“插合完成”分属两层。
- **超限处理**：[CN109856554A](https://patents.google.com/patent/CN109856554A/zh) 披露位置超差转人工干预（第 157、170 行）；[CN117718986B](https://patents.google.com/patent/CN117718986B/zh) 披露异常力变化退回重插（S1108、S1203–S1205）。二者是不同配置、不同接口的处置方式，`EVIDENCED MECHANISM`，不可互相拼接为目标工位行为。

### 2.7 部件贡献与功能可替代性如何评价

一个误差消除功能是否“机器人独有/不可替代”，必须看**贡献归属**与**可比功能**：

- **贡献归属**：某残差减小是托盘定位、导向、浮动还是机器人在线感知产生的？若上游工装已消除大部分，机器人只承担小余量，就不能把“整条链的定位成果”记到机器人头上（F1 第 1 条逻辑）。
- **功能可替代性**：[S029](https://doi.org/10.23919/iccas47443.2019.8971644)（Yumbla et al., 2019）主张当连接器公差超过机器人位置误差、且夹持位姿已知时，可考虑纯位置控制+精密夹爪插合、未必需要力控或被动柔顺，是“力控并非必需”的**条件性**反例。说明“消除同一残余误差”存在可替代技术路径，但选型不能只由残差/公差决定，还必须结合接触约束、节拍、异常恢复、换型与集成负担综合判断。**注意：S029 在 Screening Log 的 full-text 状态仍为 `needs_institution`，本条目前仅以作者公开摘要层面登记，属条件性技术观点，不得写成充分验证的普遍性能结论；且现有 `C029` 实际关联 S031（三维视觉重复识别），与 S029 无关，不在此交叉引用。**

### 2.8 三层级机制证据（不同层级，非同工况比较）

| 证据 | 层级 | 披露的机制 | 具体来源定位 | 对 F1 的贡献 | 明确不能用于 |
| --- | --- | --- | --- | --- | --- |
| CN109856554A | 专用机构（浮动/导向） | 水平/竖直浮动 + 第一/第二位置检测，超差人工干预 | 说明书“具体实施方式”，第 135、145、157、170、173–174 行；PDF `[0043][0051][0059][0061]–[0063]` | 专用机构也能以“浮动+检测”消除残余误差并做到位代理；托盘/中转接口边界存在 | 其对接的是**托盘中转插头**，与直接对 Pack 插座机器人专利不是同物理接口，不可作同工况 head-to-head |
| CN117718986B | 机器人+力传感（主动补偿） | 机械臂+导引面+力传感对插；部分实施方式以“插接力+相对距离”条件停止插接 | 权利要求 1、方法实施方式 S1108、S1203–S1205；说明书第 75–84、128–135、167–174、186–191 行 | 机器人以力/距离反馈做主动补偿与机械完成代理 | 力+距离判断不是电气接触质量证明；未披露目标工位实测成功率与完整联锁 |
| S027（arXiv:2503.09409v2 / IEEE CASE 2025，DOI `10.1109/CASE58245.2025.11164054`） | 机器人+视觉+力控+学习优化（系统/方法） | 预定位随机方差（±2 mm；B 为 ±1.5 mm）下，用 ARTM 程序 + MuTT 前向模型 + SPI 程序参数优化降低搜索开销 | Sec. III-A（Fig. 4 程序）、Sec. IV（表 I，扰动域）、Sec. V-B（Table III） | 证明“残差不确定性”是一个可建模、可优化的显式条件轴；几何/朝向方差驱动成功率与节拍差异 | 是汽车中控台连接器，`CROSS_INDUSTRY_TASK_ANALOG`；其 ±2 mm、力值、成功率均不可迁移到 Pack 工位 |

### 2.9 禁止推断（F1）

- 不得把两个专利视为同插座、同工况的 head-to-head（`16`）。
- 不得虚构目标 Pack 工位的六维误差、公差、接触约束与验证数据（`09` R2 规则）。
- 不得把“浮动行程大”或“视觉定位完成”直接写成“残余误差已被消除到可插合”。
- 不得把 S027 的扰动/力值填入 Pack EoL 性能栏（`22`）。

---

## 3. F2 — Mechanical Mating, Electrical Acceptance and Test Authorization

### 3.1 功能目标

识别连接器是否达到所需机械状态，确认适用的连接验收条件，并明确**哪个控制系统依据什么规则允许后续测试**。核心是把“物理插接动作”与“系统接受/放行”拆开，避免把多级状态压成一个信号（F2 第 2 条逻辑）。

### 3.2 必须分离的状态（六项：物理可观测状态、控制判定与异常处理规则需区分）

`ANALYTICAL INFERENCE`（延续 [17 第 1 节](./17_completion_acceptance_authority_research_2026-09-30.md) 与 [22 §7 第 5 条](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)）：

1. **机器人/执行器动作完成**——程序完成或运动停止；只证明控制动作状态；
2. **机械到位**（必要时 + 机械锁止确认）——插头达到所设机械位置/锁扣；由能观测该状态的机制支持；
3. **电气/通信连接接受**——连接可用于所需电气测量或通信；接收范围取决于实际测试；
4. **测试请求/许可**——PLC/测试控制器/安全系统按条件允许上电或执行测试；是决策，不是传感器读数；
5. **启动接受**——测试设备收到命令后给出状态反馈、实际开始执行；
6. **异常处置**——失败、超时、互锁变化时的停止/断能/退回/人工介入。

注意：这六项**不是**六个一一对应的独立传感器。机械到位/接触力是物理可观测状态；测试请求/许可与启动接受是控制判定与设备应答；异常处置是异常路径规则，需多个证据/规则共同确定，而非单一传感器读数。

S027 提供一个有力的机制级证据：其搜索成功判据是“相对运动在未超过接触力阈值下完成”（`valid=True`），是**触觉/运动层判据**，论文任务边界止于机械插合，无电气导通、无测试许可、无安全时序（[22 §4.2](./22_week09_day2_search_provenance_s027_research_closeout_2026-10-14.md)）。即：**“搜索成功”≠“机械锁止”≠“电气确认”≠“测试许可”**。

### 3.3 子功能与候选责任分配（初版表）

| 子功能 | 候选责任者 | 所需证据（待证字段） |
| --- | --- | --- |
| 机械插合检测 | 到位传感器 / 机器人 / 专用检测机构 | 检测量（行程/距离/力/感应片）、阈值及有效性 |
| 机械锁止确认 | 锁止检测系统（如适用） | 锁止状态及验收要求 |
| 电气或通信接受 | 测试仪 / 检测模块 | 适用的连接检查项与通过条件 |
| 测试请求/许可 | PLC / 测试控制器 / 相关安全控制系统 | 条件逻辑、授权责任与**撤销方式** |
| 启动接受 | 测试设备 | 命令响应、状态反馈 |
| 异常处置 | 控制系统 / 设备 / 人员 | 停止、超时、故障恢复与安全状态 |

`Candidate responsible component` 是候选责任者，**不等于已确认的目标工位设备组成**。其中“机械插合检测”一行的机制先例是：CN109856554A 的第三传感器感应片（第 145 行）、CN117718986B 的力/距离判断（第 186–191 行）、S024 的相对位移+力上限完成判据（`C026`）；“测试请求/许可”一行的先例是 WO2024259675A1 的“到位信号→控制器许可/禁止测试”（但其到位点是**测试设备内部可换探针安装接口**，非 Pack 外部插头，见 `18` P4）。

### 3.4 假设 PLC 逻辑（教学反例，HYPOTHETICAL）

```text
IF Mating_OK AND MES_Ready THEN
    Test_Start = TRUE
END_IF
```

**这是 HYPOTHETICAL 教学反例，不得登记为实际工业证据**（延续 [18 第 3 节](./18_pack_eol_same_configuration_release_chain_audit_2026-09-30.md) 的“分析者构造的理想系统”警告）。它只说明：

1. 两个条件同时成立时 `Test_Start` 被置 TRUE；
2. **它没有说明当 `Mating_OK` 重新变 FALSE 时 `Test_Start` 会怎样**。若这就是完整赋值且输出状态保持，则：

| 时刻 | Mating_OK | MES_Ready | 执行结果 |
| --- | --- | --- | --- |
| T1 | TRUE | TRUE | 置 `Test_Start = TRUE` |
| T2 | FALSE | TRUE | 该代码不执行赋值（若输出保持，`Test_Start` 仍可能为 TRUE） |

**结论**：只看到启动条件 ≠ 已验证许可的**撤销条件**。对于存在危险测试动作的系统，许可的**保持、撤销和异常响应**都影响安全评价（Safety Gate）。这提示 F2 必须把“许可撤销/异常复位”列为待证字段，而不是默认“条件消失即自动撤销”。

### 3.5 同配置证据边界（引用 17/18/20 已有时，不拼接）

已有证据只能支持**每个配置内部的局部链**，不能拼成目标工位完整许可链：

| 配置/来源 | 能支持的局部链 | 断点 |
| --- | --- | --- |
| P1 CN117718986B | 力/距离→停止插接；异常力→退回重插 | 力/距离结果如何成为测试仪许可输入；无电气/通信/HV 检查链 |
| P2 CN109856554A | 第三传感器到位→未到位人工干预 | 对接中转接口的边界张力；是否硬联锁测试开始、是否验证电气接触——未说明 |
| P3 CN117970112A | 通信反馈→下一检测/失败显示；HVIL 回路反馈→该项通过（人工接线+人机确认） | 人工接线方案，不能外推为 P1/P2 许可输入；HVIL 是该方案测试项，非所有测试的先验许可 |
| P4 WO2024259675A1 | 到位信号→控制器许可/禁止测试 | 到位点是设备内部可换探针安装接口，非 Pack 外部插头，任务边界不同 |
| P5 WO2025194672A1 | 换型/视觉定位/插头对插机制 | 未找到机械完成信号→测试许可、异常恢复、同工位安全联锁 |
| P6 Festo/HAHN | 功能可在设备层集成（处理+相机+电气/机械/光学/泄漏） | 无对插传感器、完成判据、许可规则、故障路径 |
| 退役模块 Rastegarpanah S001 | “已观测电连接”（灯/蜂鸣报警）与“谁启动测试”（操作员）分属不同环节 | 退役模块实验，非制造端 Pack EoL；摘要与方法正文表述存在差异，需保守解读 |
| DMC 技术文章（可配置示例，见 [blog/20983](https://www.dmcinfo.com/blog/20983/everything-you-need-to-know-about-ev-battery-and-bms-testing-in-validation-and-production-scenarios-2/)） | Example System 的 End of Line Functional Testing 测试序列中列有 `Pack Connection Check` | 属**可配置测试序列示例**，非已交付工位，不代表“连接检测→放行”链已被验证 |
| DMC 已交付 Pack EoL 项目（见 [our-work](https://www.dmcinfo.com/our-work/electric-vehicle-pack-end-of-line-test-with-dmcs-battery-production-tester/)） | 披露 MES 测试资格查询、按料号选择测试序列、部分测试系统硬件与互锁 | 未披露外部插头由谁连、是否检测物理锁止、机械完成到测试许可的完整链 |

**禁止拼接**（沿用 `18`）：`P1 力/距离 + P3 BMS 应答 + P4 探针联锁 + P6 清单 = 目标机器人自动许可链 ❌`。

### 3.6 禁止推断（F2）

- 不得把“机器人动作完成”“机械到位信号”“电气接受”“测试许可”合并为一个状态；
- 不得把供应商/专利/测试工位信号拼成一个已验证系统（`18`）；
- 不得把 `IF Mating_OK AND MES_Ready THEN Test_Start=TRUE` 写成真实现场逻辑；
- 不得把 HVIL 测试项当作测试前的先验许可输入（`18` 第 4 节第 3 点）；
- 不得把 WO2024259675A1 的内部探针联锁移植为 Pack 外部插头的许可链。

---

## 4. Functional Responsibility Matrix（F1 / F2）

`Candidate responsible component` 是候选责任者，**不等于已确认目标工位设备组成**；`Target configuration UNKNOWN` 列统一标记目标部署信息缺失。证据身份沿用现有账本标签（`PATENT` = 设计披露；`EQUIPMENT_SUPPLIER` = 供应商披露；`PEER_REVIEWED_ARTICLE` = 跨行业/跨生命周期机制；`CONFERENCE_PAPER` 同前）。**注意：这些标签（含 `EQUIPMENT_SUPPLIER`）与正式代码表存在待修复差异（pending codebook reconciliation），本文仅作为现有账本标签引用，不视为已标准化的协议 `source_type`。** `Decision owner / next action` 列只填写：已披露的判定者与下一步动作（标注来源）、候选判定者（标注“假设”）、或 `UNKNOWN`，不凭工程常识指定 PLC 或其他设备。

### 4.1 F1 — Residual Connector Pose Uncertainty

| Required end state | Required function | Observable evidence | Candidate responsible component | Decision owner / next action | Failure or exception path | Source ID and evidence type | Target configuration UNKNOWN | Selection relevance |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 连接器到达插合机构可处理的对准范围 | 托盘/夹具定位（大幅平移+部分姿态） | 定位后实测位姿 vs 名义位姿（残差量、分布） | 托盘/定位销/夹具 | 工装设计决定残差下限（设计层）；运行时判定者 `UNKNOWN` | 超差→人工干预或下一层补偿 | S019–S020（供应商方案存在定位）；残差值缺 | 定位残差的方向、数值、分布 | 上游残差决定后续环节负担，是条件轴，非机器人独有 |
| 导向可吸收残余错位 | 引导/浮动（几何捕获） | 浮动行程、导向面几何、位置检测阈值 | 导向面/浮动机构/定位检测 | 机构设计是否覆盖目标残差（设计层）；运行时判定者 `UNKNOWN` | 浮动超限→人工干预 | CN109856554A（第 157、170 行；`PATENT`） | 目标浮动行程与有效捕获范围 | 专机浮动已覆盖残差时，机器人主动纠偏在该功能维度的增量价值可能降低；整体适用性仍取决于换型/节拍/接触力/异常处理/集成等条件 |
| 获得用于后续插接的接口位姿估计 | 主动视觉定位 | 视觉识别精度、遮挡/姿态范围 | 视觉系统 + 机器人 | 候选：视觉系统判定识别成功并触发重识别（假设） | 识别失败→重识别/弃件（S031 例外） | WO2025194672A1（视觉对插，`PATENT`）；S027 视觉（`CONFERENCE_PAPER`）；S031 `C029` | 目标是否具备可用视觉特征与光照 | 仅当目标需要视觉换型/定位时才有选型差异 |
| 视觉/导向之后剩余误差被吸收 | 力控/柔顺搜索 | 接触力统计、搜索成功判据、探测次数 | 力传感 + 力控/柔顺 + 机器人 | 候选：S027 以接触未超力判定 Probe Search“搜索成功”（F1 搜索定位机制，`CONFERENCE_PAPER`）；CN117718986B 的力/距离停止插接条件属 F2 机械完成判据（其细节与来源见 §4.2），不在此与搜索成功混为同一状态 | 异常力→退回重试/人工 | CN117718986B（第 186–191 行；S1108）；S027 Probe Search（`CONFERENCE_PAPER`）；S024 `C026` | 目标允许力、卡滞判据 | 当专用机构已满足目标残余误差及相关任务约束时，机器人主动补偿在该功能维度的增量价值可能降低；但整体配置适用性仍需结合其他功能和实施条件评价 |
| 无损伤地达到对准 | 接触力/卡滞/超限控制 | 允许力、卡滞检出、超限处置 | 机器人/机构/设备 | 运行时判定者 `UNKNOWN`（S024/CN 专利仅披露机制，未指定工位判定者） | 卡滞/超限→停止/退回/人工 | S024（`C026`）；CN109856554A 超限人工；S031 `C028` | 目标允许力与故障频率 | 假阳性后果未知，不能判任一恢复方式更优 |

### 4.2 F2 — Mechanical Mating, Electrical Acceptance and Test Authorization

| Required end state | Required function | Observable evidence | Candidate responsible component | Decision owner / next action | Failure or exception path | Source ID and evidence type | Target configuration UNKNOWN | Selection relevance |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 插头达到所设机械位置 | 机械插合检测 | 检测量及阈值（行程/距离/力/感应片） | 到位传感器/机器人/专用检测机构 | 运行时判定者 `UNKNOWN`（专利仅披露判据，未披露目标工位判定者） | 未到位→人工干预或重试 | CN109856554A 第三传感器（第 145 行）；CN117718986B 力/距离（第 186–191 行）；`PATENT` | 目标判据量、阈值、假阳性率 | 机械完成判据不同会区分配置 |
| 锁止到位（如适用） | 机械锁止确认 | 锁止状态/验收要求 | 锁止检测系统 | `UNKNOWN`（是否需独立锁止检测未披露） | 未锁止→停止/重插 | 目标锁扣结构/判据 `UNKNOWN` | 是否需独立锁止确认 | 仅当锁止影响后续电气/安全时相关 |
| 连接可用于电气/通信 | 电气/通信接受 | 连接检查项与通过条件 | 测试仪/检测模块 | 候选：测试仪/检测模块据检查项判定放行（假设） | 未通过→报警/停止 | Rastegarpanah S001（连接报警 vs 操作员启动，`PEER_REVIEWED_ARTICLE`）；DMC 技术文章 Pack Connection Check（可配置示例，供应商披露）；`C015` | 目标电气验收判据、责任者 | 电气接受独立于机械完成，是区分项 |
| 上电/测试被允许 | 测试请求/许可 + 许可撤销 | 条件逻辑、授权责任、撤销方式 | PLC/测试控制器/安全控制系统 | `UNKNOWN`（有 WO 内部探针联锁先例，无 Pack 外部插头放行规则） | 条件不满足→禁止；条件消失→是否自动撤销（3.4 例） | WO2024259675A1 到位→许可（内部探针，`PATENT`）；DMC 已交付项目 MES ready 查询（供应商披露） | 目标许可逻辑、互锁时序、撤销 | 安全许可逻辑是 Safety Gate 核心输入 |
| 测试设备实际启动 | 启动接受 | 命令响应、状态反馈 | 测试设备 | 候选执行者：测试设备；目标工位的启动判定者、应答反馈与完整规则 `UNKNOWN` | 无响应→超时/终止 | 目标设备握手/超时 `UNKNOWN` | 命令-响应协议 | 区分“已许可”与“已启动” |
| 异常被安全终止 | 异常处置 | 停止/断能/退回/人工介入 | 控制系统/设备/人员 | `UNKNOWN`（安全控制系统为候选，假设；停测/断能权未披露） | 超时/互锁变化→安全状态 | WO2024259675A1 安全光栅报警停止（特定实施方式，`PATENT`，不得迁移为目标工位的安全停机/断能功能） | 目标故障响应与时序 | 异常链决定安全部署可行性 |

---

## 5. Framework Mapping

### 5.1 F1/F2 如何作为四个 Gate 的输入

沿用 [13 第 3 节](./13_framework_v1_decision_table_draft.md) 的四 Gate，不新增：

- **Task Gate**：F1 明确“残余位姿误差消除”与 F2 明确“机械完成→电气接受→许可→启动→异常”的状态链，二者把“任务定义是否完整”的字段（对象源/目标/完成判据/责任边界）落到可查证项。缺失字段写 `UNKNOWN`，不能靠工程常识补上。
- **Condition Gate**：F1 的“上游残差 vs 允许力 vs 有效捕获范围”与 F2 的“许可/撤销逻辑”是区分 `feasible` 与 `selection advantage` 的**条件输入**；在目标条件未知时只写“可检验的价值机制”，不写选择优势。
- **Safety Gate**：F2 的“许可保持/撤销/异常处置”直接作为 Safety Gate 的核验字段；目标安全功能缺失时结果为 `UNKNOWN / deployment decision blocked`。
- **Evidence Gate**：F1/F2 每个机制结论都标 `PATENT / SUPPLIER / PEER_REVIEWED` 与迁移边界，落入第 4 节的主张证据状态（`CONDITIONAL` 为主），不升级为 `SUPPORTED FOR THIS CONFIGURATION`。

### 5.2 目标部署层 Gate 现状

目标部署层 Task / Condition / Safety Gate 继续 `OPEN`，除非出现新的**同配置直接证据**满足原协议（[13](./13_framework_v1_decision_table_draft.md)、[18](./18_pack_eol_same_configuration_release_chain_audit_2026-09-30.md)）。功能分解可以成立（本文），但不得据此判 PASS 或 FAIL。

### 5.3 边界声明

本文件**不新增 Gate、不新增评分权重、不声称提出全新的功能分配理论**。责任分配思想已见于 PPR / function allocation / capability-based allocation（[16 第 4 节](./16_function_responsibility_audit_pilot_2026-09-30.md)）。F1/F2 只是把这些既有字段首次用于 Pack EoL 的「残余误差」与「插合完成-许可」两个功能。

---

## 6. Thesis Writing Reuse

区分**已披露机制**（可直接归因到源）与**方法性推论**（本项目分析框架，需以 "we treat / we distinguish" 表述，不与披露事实混同）。以下仅为措辞素材，非论文段落。

**（A）已披露机制（disclosed mechanism）** —— 可归因到具体来源：

> Patents on pack end-of-line testing disclose distinct ways of absorbing residual connector misalignment. A dedicated contacting unit uses horizontal and vertical floating guides with position detection and manual intervention on over-travel (CN109856554A, description, ¶135, 157, 170). A robot-based design uses guidance surfaces and force sensing, stopping insertion when the insertion force and relative distance satisfy a defined condition and retracting on abnormal force (CN117718986B, claims and method steps S1108, S1203–S1205).

> A recent automotive connector-mating study reported that, under ±2 mm pose perturbation (±1.5 mm for one connector), model-based optimization of a force-controlled robot program raised search success from 49–93% to 88–98% and reduced cycle time from 13–18 s to 9–11 s; its search-success criterion is tactile/motion-level (the contact motion completes without exceeding a defined force), with no electrical verification or test authorization (Kienle et al. 2025, Table III).

**（B）方法性推论（methodological inference）** —— ours, not a disclosed fact：

> We treat the upstream positioning residual and the actual plug-to-socket relative error as distinct quantities, and we treat nominal floating travel as distinct from effective capture range; neither equality can be assumed without measuring the connector's orientation, cable state, permissible force and tolerance.

> We distinguish action completion from physical seating/latching, electrical/communication acceptance, test authorization, and equipment start confirmation; observing one does not license the others. A start condition alone does not establish the corresponding revocation or fault behavior.

---

## 7. Open Items（最小待证据清单）

| # | 待证字段 | 现状 | 对应的框架字段 |
| --- | --- | --- | --- |
| 1 | 目标连接器接口与测量坐标系（机构/夹具/插座本体） | `UNKNOWN` | F1 / Task Gate |
| 2 | 残余六维位姿误差（X/Y/Z、Roll/Pitch/Yaw 的范围与分布） | `UNKNOWN` | F1 / R2 |
| 3 | 允许接触力与有效补偿范围（因朝向/线束/公差缩小） | `UNKNOWN` | F1 / R2 |
| 4 | 机械插合与锁止判据（检测量、阈值、假阳性率、锁止要求） | `UNKNOWN`（有机制先例，无目标值） | F2 / R5 |
| 5 | 电气接受及测试许可逻辑（判定者、互锁、许可**撤销**方式） | `UNKNOWN`（有局部链先例，无完整链） | F2 / R3 |
| 6 | 故障与安全响应（停止/断能/退回/超时/复位时序） | `UNKNOWN` | F2 / R3·Safety Gate |
| 7 | 同任务下各配置（人工/专机/机器人）的可比指标（节拍、失败、介入、换型、成本） | `UNKNOWN` | Condition / Evidence Gate |

---

> 结论与状态：F1、F2 的第一次功能分析已完成到可归档的初版研究卡程度，功能分解成立；但目标工位参数、许可链与异常链仍缺证据。**保留 `OPEN` 状态**，等待人工审核后再决定是否提交。不 commit、不 push、不修改 02/03/04 或其他研究记录、不分配正式 Claim ID、不宣布任何架构优胜。