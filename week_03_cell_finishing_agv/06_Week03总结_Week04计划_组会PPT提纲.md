# Week 03 总结、Week 04 计划与组会 PPT 提纲

> 用途：总结第三周真正学到的内容，作为下一次组会PPT的可拆页提纲，并为Week 04提供一个节奏较慢、证据导向的工作计划。
> 状态：研究过程文件，不是正式论文结论，也不是PEM/RWTH官方模板。
> 当前日期：2026-07-29

---

## 0. 一页结论

### Week 03做了什么

根据Thomas第二周“不要停留在high-level、选择一个use case逐步深入”的反馈，本周选择了：

> **Formation–aging–EoL之间的托盘/载具运输**

作为学习型案例，而不是最终确定的论文题目。

本周从四个层次建立了第一版理解：

```text
Cell-finishing工艺功能
→ 物理位置与载具变化
→ 运输请求、等待和设备交接
→ AGV车队控制与车辆执行
```

### Week 03最重要的结论

1. `Formation → Aging → EoL`只是教学简化；真实路线会随制造商、cell format和设备集成方式变化。
2. 两个相邻工序不自动产生一次运输；只有设备/区域分离且载具需要改变位置时，才产生候选运输任务。
3. Aging长期占用的是cell、tray/carrier和storage position，不是AGV。
4. 运输任务不能以“车辆到达”为结束；还需要物理交接、目的地接收和系统状态更新。
5. AGV系统需要区分fleet sizing、dispatching、routing、traffic control和handover，不能统称为“调度”。
6. 已有真实充电电池工厂AGV案例，但公开论文没有证明其属于cell finishing或运输tray。

### 现在仍然不能下的结论

- 不能说目标场景一定使用AGV；
- 不能说同一tray贯穿formation、aging和EoL；
- 不能确定cell format、托盘容量、接口、布局、节拍或AGV数量；
- 不能把fleet size、dispatching、parking或robustness宣布为最终research gap；
- 不能开始复制案例参数建立SimPy模型。

### Week 04建议方向

> **主动寻找最接近的研究和反例，判断“cell-finishing工艺逻辑—托盘物流—AGV系统设计”是否已经被现有文献充分连接。**

Week 04仍然是文献边界和概念验证周，不是仿真周。

---

# Part A — 组会PPT提纲

## 使用建议

- 建议长度：9–10页；
- 建议讲述：约8–12分钟，具体以Thomas的组会安排为准；
- 每页只传递一个结论；
- 流程图和表格应根据本提纲重绘为可编辑图形，不截图HTML或论文；
- 页脚保留作者、年份和准确页码；
- 这是普通组会提纲，不套用正式colloquium要求。正式colloquium仍需核对最新PEM模板和流程。

---

## Slide 1 — Title / 本周研究对象

### 标题

**From Cell-Finishing Processes to AGV Transport Tasks**
*Week 03 learning case: formation–aging–EoL tray flow*

### 本页中心句

> I selected one learning case and moved from a high-level robotics map to process-specific transport tasks and interfaces.

### 页面内容

- Thesis context: robotic systems in battery cell manufacturing；
- Week 03 learning case: formation–aging–EoL carrier flow；
- Current stage: conceptual understanding, not simulation or optimization。

### 中文讲法

根据上次反馈，我没有继续比较多个机器人案例，而是选择cell finishing中的托盘运输作为学习型案例，从工艺、对象、任务和接口逐步往下拆。目前还没有宣布最终题目，也没有进入仿真。

---

## Slide 2 — How I Responded to the Supervisor Feedback / 对Thomas反馈的回应

### 本页中心句

> The work changed from “which robotics case is best?” to “what actually happens inside one case?”

### 建议视觉

```text
Week 02: process map + four candidates
                   ↓ Thomas: too high-level; pick one and go step by step
Week 03: one cell-finishing tray-flow case
```

### 页面内容

- Thomas明确反馈：先学习基础，选择一个use case，进入工序内部；
- 当前响应：formation–aging–EoL tray transport；
- 数据、专家访谈和模型变量排在具体问题之后；
- 该案例是学习入口，不等于最终scope。

### 信息类型

- **Supervisor guidance**：选择一个案例逐步深入；
- **Project decision**：本周采用托盘物流作为学习案例；
- **Not decided**：最终论文是否只研究AGV。

### 来源

`week_02_robotics_evidence/第二周导师反馈.md`，Sections 3–4。

---

## Slide 3 — Week 03 Core Question and Boundary / 核心问题与边界

### 本页中心句

> What transport tasks, interfaces, and constraints characterize tray flows between formation, aging, and EoL testing?

### Included

- formation、RT aging、EoL testing和grading；
- carrier/tray、rack、buffer和storage position；
- request、waiting、pickup、delivery和handover；
- normal、reject/quarantine和条件性的empty-carrier flow。

### Excluded for now

- formation电化学协议优化；
- AGV底盘、SLAM和避障算法；
- fleet optimization、robustness和ROI；
- 未经证实的cell format、节拍、托盘数和布局。

### 中文讲法

本周不回答“几台AGV最好”，而是先回答现实系统里究竟有哪些对象、事件、接口和等待。如果这些内容不清楚，直接仿真只会得到一个与cell finishing脱节的编程练习。

---

## Slide 4 — Cell-Finishing Process Logic / 工艺先决定物流

### 本页中心句

> Process configuration generates the logistics network; the logistics network should not be assumed first.

### 建议视觉

```text
First filling
→ Wetting / soaking
→ Formation
→ [route-dependent: degassing / second filling / sealing / HT aging]
→ RT aging
→ EoL testing
→ Grading / output
```

在条件性节点上用虚线，并标注：`cell-format / manufacturer dependent`。

### 四个记忆动词

| Process | Function |
| --- | --- |
| Formation | establish/stabilize initial electrochemical interface state |
| RT aging | wait and observe stability/self-discharge |
| EoL | measure quality and performance |
| Grading | convert measurement results into destinations |

### 本页不要讲错

- SEI不是separator；
- formation不是普通“把电池充满”；
- EoL后通常不能先假定返回formation/aging；
- 路线没有统一标准顺序。

### 文献证据

- Kampker et al. (2023), Sections 2–2.3.2, PDF pp. 2–10；
- Plumeyer et al. (2023), Sections 3.1–3.5, PDF pp. 3–6。

---

## Slide 5 — From Process Completion to a Transport Task / 一项运输任务怎样形成

### 本页中心句

> Process completion, load release, request creation, vehicle service and downstream acceptance are different events.

### 建议视觉

```text
Process completed
→ Equipment safely releases load
→ Destination / buffer can receive
→ Request created
→ Wait for service
→ Empty travel + pickup
→ Loaded travel + delivery
→ Destination accepts + system state updates
```

### 完成条件

```text
Task completed
= physical handover
+ destination acceptance
+ state update
```

### 四种时间

| Time | Example |
| --- | --- |
| Process time | formation或EoL实际处理 |
| Storage time | RT-aging按计划观察 |
| Transport time | 空驶、取货、载货、交付 |
| Waiting time | tray已ready但车辆/接口/目标不可用 |

### 中文讲法

Formation结束不等于运输请求已经产生；车辆到达也不等于任务完成。这个拆分决定了未来模型应该记录哪些时间和状态。

---

## Slide 6 — Why Logistics Delays Matter / 延迟怎样影响工艺系统

### 本页中心句

> A transport delay can create tray waiting, upstream blocking and downstream starvation, but only under specific buffer and interface conditions.

### 建议视觉

```text
Formation completed tray waits for transport
          ├─ if output cannot release → Formation blocking
          └─ if EoL is idle without input → EoL starvation
```

### 概念区别

- **WIP**：系统内尚未成为最终输出的在制品，不自动等于故障；
- **Waiting**：对象ready但所需资源/条件不可用；
- **Blocking**：上游完成但无法卸出；
- **Starvation**：下游可工作但没有合格输入；
- **Storage-capacity blocking**：目标aging/storage没有可用位置。

### 重要限制

下游设备正在忙，不自动代表上游blocking；如果input buffer仍有空间，上游可能正常释放。

### 概念依据

Hall & Sriskandarajah (1996), *Operations Research* 44(3), 510–525；本案例使用操作性定义，尚未建立正式排队模型。

---

## Slide 7 — AGV System Responsibilities and Handover / AGV不是一个单独的小车

### 本页中心句

> Production control creates the need; fleet control organizes the fleet; the robot executes; the handover interface transfers the load.

### 建议视觉

```text
Process / production control
→ transport need and priority

Fleet control
→ assignment, route, traffic, charging

Mobile robot
→ localization, movement, pick/drop, state reporting

Handover / fixed equipment
→ conveyor, lift, gantry, port or direct transfer
```

### 核心概念

| Concept | Question |
| --- | --- |
| Fleet sizing | How many vehicles? |
| Dispatching | Which vehicle / which task first? |
| Routing | Which path? |
| Traffic control | How are shared routes coordinated? |
| Handover | How is the tray physically transferred? |

### VDA 5050边界

- 支持fleet control与mobile robot交换order/state；
- 不提供最佳调度/交通算法；
- 不定义安全、外围设备或MES/PLC/WMS接口；
- 不能证明目标电池工厂采用该规范。

### 来源

- Vis (2006), pp. 677–709；
- De Ryck et al. (2020), pp. 152–173；
- VDA 5050 v3.0.0 (2026), Sections 2、4.3、5–6, PDF pp. 6–38。

---

## Slide 8 — Real Rechargeable-Battery AGV Case / 最近邻工业案例

### 本页中心句

> The WSC case is real-record-driven evidence for an AGV system in battery production, not direct evidence for cell-finishing tray transport.

### 论文做了什么

```text
Actual-site job records + site configuration
→ DAIM Factory Emulator
→ Greedy vs Bruno idle-parking policy
→ AWT / ATT / ADT / utilization / charging
```

### 公开规模

- uni-directional layout；
- approximately 200 nodes；
- 100 ports；
- 4 charging stations；
- 9 AGVs。

### 结果阅读边界

- 案例报告AWT约下降17%、ADT约下降9%；
- charging占比上升，存在trade-off；
- 作者对ATT/charging原因使用推测性语言；
- 没有在线部署A/B证据，也没有统计不确定性细节。

### 未公开

- cell/module/其他物料；
- formation、aging、EoL；
- tray/rack/carrier和handover；
- 异常品和空盘回流。

### 来源

Lee, Park & Jang (2024), WSC 2024, PDF pp. 1–2。

---

## Slide 9 — What We Know, Infer, and Still Do Not Know / 证据边界

### 本页中心句

> Week 03 produced a conceptual vocabulary and conditional task model, not a confirmed factory layout.

| Evidence status | Current conclusion |
| --- | --- |
| **Literature-supported fact** | Cell-finishing路线具有制造商/format差异；RT aging涉及长期存储；AGV系统有独立的设计与控制问题；电池生产中存在真实AGV案例。 |
| **Engineering inference** | 若formation、aging和EoL物理分离且载具换位置，则产生运输；物流延迟可能经buffer条件导致blocking/starvation。 |
| **Unknown** | cell format、运输单位、tray是否贯穿、设备接口、请求发起者、layout、节拍、空盘流、车辆数量及是否使用AGV。 |
| **Working gap hypothesis** | Cell-finishing工艺模型与AGV系统设计之间可能缺少充分连接；尚未经过反例检索验证。 |

### 中文讲法

我们现在有一个可供检索和专家验证的conceptual model，但不是一个已经确认的工厂模型。最大的进展是能够明确说出不知道什么，而不是用假设补齐流程。

---

## Slide 10 — Week 04 and Questions for Thomas / 下一步与导师问题

### 本页中心句

> Next week I will test the literature boundary and actively search for counterexamples before defining a research gap or simulation.

### Week 04最低任务

1. 定向搜索最接近的cell-finishing logistics / AGV研究；
2. 建立一张最近邻研究对照表；
3. 主动寻找已经完成“工艺—载具—AGV”连接的反例；
4. 形成1–2个有证据边界的candidate gap；
5. 把公开资料无法回答的内容转化为具体专家问题。

### 暂不做

- SimPy；
- AGV数量或调度算法比较；
- optimization、robustness或ROI；
- 最终研究问题和最终gap。

### 建议向Thomas确认

1. Is this level of process/task decomposition sufficiently concrete for the selected learning case?
2. For the next step, should I prioritize academic counterexample search or industrial interface evidence?
3. Are there PEM/eLab experts or equipment sources who could later validate tray/carrier and handover assumptions?
4. Is it acceptable to keep this as a learning case while the final thesis scope remains open?

---

# Part B — Week 03研究总结

## 1. Week 03核心问题的阶段性回答

### 问题

> 化成、老化和终检之间的托盘流包含哪些运输任务、设备接口和工艺约束？

### 当前可以给出的答案

公开文献能够支持formation、RT aging、EoL和grading等工艺功能，也能支持某些路线变化会增加或删除物流环节。例如，测量位置外置或second filling跨区域布置会增加运输与接口需求。

但是，公开来源没有给出一个统一的`formation tray → AGV → aging rack → AGV → EoL`标准架构。因此，当前只能形成条件性任务：

| Candidate task | Trigger | Completion | Evidence status |
| --- | --- | --- | --- |
| Formation → RT-aging storage | formation完成、载荷可释放、目标可接收 | 入库接收并更新状态 | conditional inference |
| RT-aging storage → EoL | aging/观察条件完成、可出库 | EoL侧接收并更新状态 | conditional inference |
| EoL → normal/grading output | 检测和分类完成 | 对应输出位置接收 | branch supported, interface unknown |
| EoL → reject/quarantine | 不满足要求或需隔离 | 异常位置接收并保持追溯 | architecture unknown |
| EoL → re-test | 规则要求复测 | 复测位置接收 | universal existence unverified |
| Empty carrier → pool/loading point | 产品卸下、载具可复用 | 空盘池/装载点接收 | return structure unknown |

这张表是conceptual-model入口，不是目标工厂任务清单。

## 2. 本周建立的底层概念

### 产品与资源

- Cell：具有工艺和质量状态的产品；
- Slot：设备/载具中的单cell位置，具体结构未知；
- Tray/goods carrier：候选物流单元，是否贯穿流程未知；
- Rack/storage position：长期存储资源；
- Equipment channel/fixture：工艺/测试位置；
- Transport resource：AGV或其他搬运设备；
- Handover resource：port、conveyor、lift、gantry或直接接口。

### 事件

- process complete；
- equipment/load release；
- transport request creation；
- waiting for service；
- empty travel and pickup；
- loaded travel and delivery；
- destination acceptance；
- state update。

### 系统状态

- process/storage/transport/waiting time；
- vehicle idle与task waiting；
- WIP、blocking、starvation和storage-capacity blocking。

## 3. 学生本周实际掌握的内容

通过Day 1–5复述与针对性场景判断，当前已经能够：

- 区分practical problem、research gap和data gap；
- 解释formation、RT aging、EoL和grading的不同功能；
- 判断两个相邻工序为什么不一定产生运输；
- 区分运输请求、车辆到达和任务完成；
- 区分waiting、idle、blocking和starvation；
- 区分fleet sizing、dispatching、routing、traffic和handover；
- 区分真实记录驱动模拟与真实工厂上线验证；
- 区分reported result、author interpretation和our inference。

后续学习检查采用一句话或少量场景判断，避免重复整份笔记。

## 4. Week 03对Thomas反馈的响应程度

### 已响应

- 从四案例横向比较收缩到一个学习案例；
- 从机器人类型下降到工序、对象、事件和接口；
- 先学习工艺与AGV基础，再讨论数据；
- 形成可向专家验证的具体unknown，而不是泛泛问“哪个案例好”。

### 仍需继续

- 公开工业证据仍没有填充真实tray/interface；
- 尚未系统核查最接近的academic counterexamples；
- 尚未形成经过state-of-research论证的research gap；
- 尚未确定需要何种专家/数据来验证哪个命题。

---

# Part C — Week 04工作计划

## 1. Week 04唯一核心问题

> **What is the closest existing research connecting cell-finishing process logic, carrier flows, and AGV/material-handling system design, and what remains insufficiently addressed?**

中文：

> **现有研究中，哪些工作最接近“cell-finishing工艺逻辑—载具流—AGV/物流系统设计”的连接？它们已经解决了什么，还没有充分解决什么？**

## 2. 为什么现在研究它

Week 03建立了conceptual vocabulary和条件性任务，但还不能确认：

- 这些任务是否已有文献完整建模；
- “工艺—物流—AGV之间连接不足”是不是research gap；
- fleet sizing与dispatching是否比parking、buffer或其他变量更相关；
- 公开证据是否足以支持后续离散事件模型。

因此Week 04先检验最接近研究和反例，不靠“我没有找到”宣布gap。

## 3. 最低完成目标

完成以下四项，Week 04就算合格：

1. 一份可复现的定向检索记录；
2. 一张最近邻文献对照表，能够区分direct、adjacent和not applicable；
3. 至少一个candidate gap及其最强反例/反对证据；
4. 一份只针对公开资料无法回答内容的专家验证问题初稿。

不以论文数量作为成功标准；优先读最接近的少量文献。

## 4. Day 1–5学习顺序

Day 1–5仍然是顺序，不是硬性日历。

### Day 1 — 定义检索边界和反例标准

学习问题：

> 什么样的论文才算真正连接了cell finishing和AGV，而不是只同时出现两个关键词？

Codex任务：

- 建立关键词组合与纳入/排除规则；
- 定义direct / adjacent / false match；
- 预先建立证据矩阵字段；
- 不把“没有全文”或“没有数据”记为research gap。

学生应学会：

- 如何判断一篇论文是否真正回答本案例；
- 为什么要主动寻找推翻candidate gap的反例。

### Day 2 — Cell-finishing logistics最近邻研究

学习问题：

> Cell-finishing研究如何表达carrier、batch、rack、buffer、layout和material flow？

Codex任务：

- 定向精读最接近的cell-finishing planning/simulation论文；
- 记录工序、产品/载具、资源、buffer和验证；
- 查明是否包含移动运输或只研究工艺设备；
- 核对Wanner等论文及其引用/被引研究。

### Day 3 — Battery AGV与一般AGV最近邻研究

学习问题：

> 电池生产AGV论文公开了多少工艺语义，一般AGV研究又忽略了哪些battery-specific constraints？

Codex任务：

- 检索rechargeable-battery / cell-manufacturing AGV案例；
- 记录物料、工序、接口、决策变量、KPI、数据和验证；
- 区分cell、module/pack和未披露对象；
- 主动找已经连接工艺与AGV的强反例。

### Day 4 — 研究对照与candidate gap

学习问题：

> 最接近的研究之间，真正不重叠的知识缺口是什么？

Codex任务：

- 完成对照矩阵；
- 为每个candidate gap写支持证据和反对证据；
- 区分knowledge gap、evidence limitation、industrial confidentiality和data need；
- 最多保留1–2个candidate gap，不做复杂框架。

### Day 5 — 可行性与专家问题

学习问题：

> 如果继续这个方向，哪些事实必须由专家或工业资料验证？

Codex任务：

- 把unknown转成5–8个具体问题；
- 判断每个问题需要文献、设备资料、专家还是现场数据；
- 初步检查离散事件仿真的实体、事件和参数是否可定义；
- 只做go / continue learning / adjust判断，不写SimPy。

## 5. 文献对照表建议字段

| Field | Reading question |
| --- | --- |
| Manufacturing scope | cell / module / pack / unspecified? |
| Process scope | formation / aging / EoL / other? |
| Flow object | cell / tray / rack / pallet / unspecified? |
| Process logic | routes, release conditions, batches? |
| Material handling | AGV / conveyor / OHT / ASRS / unspecified? |
| Interface | direct / port / conveyor / lift / unknown? |
| Decision variable | fleet size / dispatch / routing / parking / buffer / layout? |
| KPI | waiting / delivery / blocking / throughput / utilization / charging? |
| Data | real logs / synthetic / literature / expert? |
| Validation | live / emulator / DES / analytical / expert? |
| Evidence boundary | what cannot be inferred? |

## 6. Candidate gap的写法

### Candidate A — Process-logistics coupling

> Existing cell-finishing studies may represent process equipment and production flow, while AGV studies may represent fleet decisions without disclosing battery-process semantics. The coupling between process-specific release/storage constraints and mobile transport-system design may be insufficiently addressed.

状态：**working hypothesis**。Week 04必须寻找反例。

### Candidate B — Process-level consequences of transport decisions

> It remains to be tested whether AGV configuration decisions are evaluated against cell-finishing-specific consequences such as storage-capacity blocking and equipment starvation, rather than only generic transport KPIs.

状态：**later candidate**。需要先确认相关文献和可验证参数。

### 不能当作gap

- “我们没有工厂数据”；
- “Lee没有公开tray”；
- “很少有中文资料”；
- “还没有人使用SimPy”；
- “我们不知道AGV数量”。

## 7. Week 04明确不做

- 不开始仿真代码；
- 不填造节拍、距离、AGV数和托盘容量；
- 不比较算法性能；
- 不把parking自动加入最终变量；
- 不宣布最终research question/gap；
- 不做中欧宏观比较；
- 不把供应商案例当作学术state of the art；
- 不因检索结果少就扩大到module/pack或整厂物流。

## 8. 有余力再做

- 补充一种cell format对载具/排气路线的影响；
- 找一份设备商或工厂公开的handover图进行证据边界分析；
- 把最近邻文献画成二维地图；
- 整理一页可向Thomas展示的专家问题。

以上不是最低要求。

## 9. 三方职责

### GPT

- 读取GitHub上的Week 03成果；
- 审查Week 04核心问题是否仍然具体；
- 检查candidate gap是否被过早确定；
- 在Week 04结束后根据远端成果提出外部反馈。

### Codex

- 执行检索、精读和页码核查；
- 维护direct/adjacent/false match分类；
- 主动找反例；
- 制作对照表与学习材料；
- 把交互中发现的理解缺口回填导学笔记；
- 在学生确认后再commit/push。

### 学生

- 能用自己的话解释最近邻论文的研究对象和边界；
- 判断candidate gap是否符合自己的理解；
- 参加组会并尽量原样带回Thomas反馈；
- 不需要背论文数量或算法名称。

### Thomas

- 反馈当前案例拆解是否达到合适技术层级；
- 指出PEM/eLab可能接触的流程、物流或设备接口专家；
- 决定是否继续深挖该学习案例或调整方向。

## 10. Week 04结束时的决策门

只做以下三选一判断：

### Continue

最接近文献仍未充分连接工艺约束和移动物流决策，并且存在可获得的验证路径。

### Continue learning

候选问题有价值，但carrier/interface/parameter证据仍不足，再补一周基础证据。

### Adjust

强反例已经完整解决候选问题，或无法建立可信的cell-finishing物流场景，则调整问题或案例。

不因为完成Week 04就自动进入SimPy。

---

# Part D — 组会后闭环

组会后请尽量原样记录Thomas的反馈，并按以下四类整理：

| 类型 | 记录内容 |
| --- | --- |
| Thomas明确要求 | 原句或尽量接近原意的转述 |
| 我们的理解 | GPT/Codex/学生怎样解释反馈 |
| 当前工作假设 | 尚未被导师或文献确认的判断 |
| 尚未确定 | 需要继续检索、专家或数据验证的问题 |

下一周调整顺序：

```text
Thomas原始反馈
→ Codex整理证据边界
→ GPT读取GitHub进行外部审查
→ 学生确认理解
→ 再制定或修正下一周计划
```

---

# 核心引用

1. Kampker, A. et al. (2023). *Optimizing the Cell Finishing Process: An Overview of Steps, Technologies, and Trends*. World Electric Vehicle Journal, 14(4), 96. Sections 2–2.3.2, PDF pp. 2–10.
2. Plumeyer, M. et al. (2023). *A Review of Process Innovations in the Cell Finishing of Lithium-Ion Batteries in Large-Scale Production*. CPSL 2023. Sections 3.1–3.5, PDF pp. 3–6.
3. Vis, I. F. A. (2006). *Survey of Research in the Design and Control of Automated Guided Vehicle Systems*. European Journal of Operational Research, 170(3), 677–709.
4. De Ryck, M., Versteyhe, M., & Debrouwere, F. (2020). *Automated Guided Vehicle Systems, State-of-the-Art Control Algorithms and Techniques*. Journal of Manufacturing Systems, 54, 152–173.
5. VDA/VDMA (2026). *VDA 5050 Version 3.0.0*. Sections 2、4.3、5–6, PDF pp. 6–38. Industrial recommendation, not peer-reviewed research or a safety standard.
6. Lee, J., Park, J., & Jang, Y. J. (2024). *Idle Vehicle Allocation Problem in Automated Material Handling Systems: A Case Study in Rechargeable Battery Production*. WSC 2024, PDF pp. 1–2.
7. Hall, N. G., & Sriskandarajah, C. (1996). *A Survey of Machine Scheduling Problems with Blocking and No-Wait in Process*. Operations Research, 44(3), 510–525.

---

## 最后一句

> Week 03 did not produce a final AGV model. It produced a process-specific vocabulary, a conditional transport-task model, and a clear list of assumptions that must be challenged in Week 04.
