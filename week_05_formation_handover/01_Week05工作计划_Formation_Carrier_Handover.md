# Week 05 工作计划：Formation Carrier Handover 可行性审计

> 制定日期：2026-08-07
> 依据：Thomas 的 Week 02/03 反馈、Week 03–04 已完成成果、GPT 对最新 `main` 的外部审查、`docs/collaboration_and_pacing.md`。
> 状态：经 Codex 核查后的执行计划。它不是最终 research gap、最终研究问题、最终论文题目或 PEM/RWTH 官方要求。

---

## 1. 先定位：整个项目走到了哪里

```text
Week 01  电池制造与机器人基础
    ↓
Week 02  process → problem → task → robotic role 证据地图
    ↓ Thomas：层级仍过高，应选一个案例逐步深入
Week 03  formation–aging–testing tray flow 学习案例
    ↓
Week 04  state of the art、最强反例与 problem-area 审计
    ↓
Week 05  一个具体 carrier–equipment handover 的现实性与可验证性
    ↓ 若通过决策门
Later    practical problem → research question → method → validation
```

当前不是“刚开始了解课题”，也还没有进入正式建模阶段。项目正处于：

> **从 candidate problem 走向可研究、可验证问题的可行性门槛。**

Week 05 的职责不是继续扩大知识面，而是让最优先候选问题接受技术证据和现实验证的压力测试。

---

## 2. Week 04 给 Week 05 留下了什么

### 2.1 已有证据支持

1. 特定 cell-finishing 配置采用 tray/product carrier 处理成组电芯。
2. 公开资料至少展示了人工 tray transport 和 fully automated tray-based process 两类配置。
3. Formation carrier 不一定只是物流容器：
   - Schomburg et al. (2024) 支持 product carrier 承担 formation-equipment contact 功能；
   - Deng et al. (2026) 支持 formation tray 作为 fixture、施加受控压力，并存在 cell–tray–charging-channel physical interfaces。
4. Deng et al. (2026) 已经把部分 intralogistics transitions 纳入 cell-finishing 配置模型。

### 2.2 已被反例推翻或必须停止使用的宽泛说法

- “Cell-finishing 研究完全没有考虑 intralogistics。”
- “Carrier 只是被动物流容器。”
- “Fully automated 就等于 AGV transport。”
- “Handover 有操作动作，所以必须使用 humanoid。”
- “某篇论文没有写 handover，所以整个领域存在 gap。”

### 2.3 当前第一候选

Week 04 暂时保留：

> **Candidate A — Process-aware carrier handover at operation level**

谨慎含义是：现有来源已经表达 carrier 的工艺接口功能和部分 intralogistics，但一个具体 carrier 怎样完成 transfer、positioning、contact 和 equipment acceptance，仍需结合设备实现证据核验。Failure/recovery 本周只登记为未知，不重建异常状态。

它目前仍是 `candidate problem`，不是 `established research gap`。

---

## 3. Week 05 唯一核心问题

> **Can a concrete formation-carrier handover be reconstructed with clear evidence boundaries and a credible validation route, so that it remains a feasible thesis case?**

中文：

> **能否从公开技术证据中重建一个边界清楚的 formation-carrier handover，识别有直接支持的 battery-specific 条件，并建立可信的验证路径，使它继续成为可行的硕士论文案例？**

### 人话版本

本周只想弄清一件事：

> 关于一个 formation carrier 从“外部物流系统仍在负责它”到“formation equipment 接收它”的过程，公开证据明确描述了哪些动作和状态，哪些仍需要现实验证？

---

## 4. Reference interface 与范围边界

### 4.1 本周只研究

```text
UPSTREAM INTRALOGISTICS
          ↓
FORMATION CARRIER
          ↓
[TRANSFER / POSITION / CONTACT / ACCEPTANCE]
          ↓
FORMATION EQUIPMENT
```

### 4.2 本周不同时研究

- aging warehouse 的完整出入库系统；
- EoL、grading 和 packaging 的所有接口；
- 所有 cell format；
- AGV fleet、routing、dispatching 或 parking；
- humanoid；
- thermal-runaway 完整处置系统；
- 自主设计新的机械 handover；
- 全行业专利 landscape。

### 4.3 防止“拼装工厂”的规则

本周至少会阅读 Deng、Schomburg 和两项专利，但不同来源不得被自动合并为同一工厂：

- Deng 的 fixture/pressure/interface 证据不自动属于 Chroma 的 pallet-rack 结构；
- 一项专利中的 carrier 不自动等于 Wanner 的 256-cell tray；
- 二次化成系统不自动代表所有首次 formation 路线；
- 来源没有明确写 electrical contact 时，不得把“送入柜体”改写为“电气接触完成”。

每一种设备结构先建立独立 architecture card。Day 1通过准入检查后，只选择一个`PRIMARY REFERENCE ARCHITECTURE`进行深读和状态建模；第二项只作为轻量`COMPARATOR / COUNTEREXAMPLE`。

只有跨来源共同出现的功能，才可在更高层形成analytical checklist。该checklist只是分析工具，不是已观察到的统一architecture，更不是一条实际生产线。

---

## 5. Week 05 的起始证据池

### 5.1 学术与机构基础

| 来源 | 对本周接口直接支持什么 | 不能支持什么 |
| --- | --- | --- |
| Schomburg et al. (2024) | Product carrier 可承担 formation-equipment contact 功能 | 具体 transfer mechanism、接口时序和完整路线 |
| Deng et al. (2026) | Formation tray 可作为 fixture、施加受控压力；存在 physical interfaces 和部分 intralogistics transitions | 某一真实工厂的完整 handover state machine |
| Wanner et al. (2022) | Tray 进入 formation resource；存在 tray-level production flow | AGV、机械接口和 acceptance logic |
| FFB 2023 poster | 人工和全自动 tray-based configuration | 全自动配置的具体 transport technology 与 handover architecture |

### 5.2 Architecture A：Conveyor → Multi-layer tray rack → Formation cabinet

- 文献：Chroma/致茂电子，`TWM639367U`，2023-04-01公开；另有后续同族申请。
- 公开结构包括 conveyor-belt module、multi-layer synchronous tray rack、formation cabinet 和 controller。
- 摘要/说明支持：控制器协调 tray rack 从 conveyor 获取待化成载荷并置入 formation cabinet。
- 证据用途：重建一种 conveyor-to-cabinet transfer architecture。
- 证据边界：专利公开的是技术方案，不是长期工厂运行验证；“battery module”的具体 flow-object 含义必须结合全文和图纸核查。

原始入口：<https://patents.google.com/patent/TWM639367U/en>

### 5.3 Architecture B：Secondary-formation integrated transfer system

- 文献：`CN118970237A`，2024-11-15公开；PCT同族 `WO2026026868A1` 于2026-02-05公开。
- GPT外部检索与当前专利记录提供的初步线索显示，该专利可能涉及 conveying、carrier、transfer、formation、positioning、high-temperature environment、sorting/identification 等系统元素；这些功能在Day 1核对原文、图纸和claims以前均标为`PRELIMINARY LEAD`，不能写入研究结论。
- 证据用途：检查 transfer、positioning、identification 和异常/回流在一个专利系统中已被描述到什么粒度。
- 证据边界：这是专利申请，不是同行评审研究或生产部署报告；它研究 secondary formation，不能自动代表所有 cell-finishing formation configuration。

原始入口：<https://patents.google.com/patent/WO2026026868A1/fr>

### 5.4 Patent evidence 的统一使用规则

专利可以支持：

- 某种机构或系统结构已经被公开描述；
- 某个 transfer/positioning/identification 元素在实施例或权利要求中存在；
- Candidate A 存在更强的工程反例。

专利不能单独支持：

- 该方案已规模化部署；
- 该方案代表行业标准；
- 专利申请人的性能主张已经独立验证；
- 该问题在工业中仍未解决；
- 我们已经找到 research gap。

---

## 6. 本周最低完成目标

Week 05只维护一个综合case dossier。只完成以下三项，即达到最低目标：

1. **一个primary architecture的完整card，加一个轻量comparator card**
   - 谁拥有/移动 carrier；
   - 从哪里 transfer 到哪里；
   - 使用什么机构；
   - 来源、图号/权利要求/段落；
   - `SOURCE-EXPLICIT / ENGINEERING INFERENCE / UNKNOWN`；
   - evidence type与validation status。

2. **一张只对应primary architecture的evidence-bounded handover state diagram**
   - 至少区分 arrival、transfer、position/contact 和 equipment acceptance；
   - 每个状态或箭头标记 `SOURCE-EXPLICIT / ENGINEERING INFERENCE / UNKNOWN`；
   - `SOURCE-EXPLICIT`继续注明`peer-reviewed statement / patent claim / patent embodiment`；
   - 另列validation status，例如`disclosed/proposed—not deployment-validated`；
   - 不把不同来源拼成一个已存在系统。

3. **一次 Candidate A 压力测试**
   - 已有技术证据解释了什么；
   - 哪些内容仍然未知；
   - 剩余问题是否 battery-specific；
   - 是否有具体、可执行的credible validation route；
   - 最终作出 `KEEP / NARROW / ABANDON / CONTINUE LEARNING` 决定。

本周不以专利数量、讲义数量或页面长度衡量成功。

---

## 7. 学习与研究顺序

Day 1–5 仍表示逻辑顺序，不是必须每天生成一个文件，也不是硬性日历。

### Orientation checkpoint — 先恢复全局方向

开始技术阅读前，口头用五句话确认：

1. Thomas 为什么要求从高层地图转向一个案例；
2. Week 03 选择了什么学习案例；
3. Week 04 的 Deng 反例推翻了什么；
4. Candidate A 现在具体指什么；
5. Week 05 为什么是在验证候选，而不是开始仿真。

这一环节只需5分钟，不单独形成文件；只纠正研究主线，不再逐项考试术语。

### Day 1 — 锁定接口并建立 source register

核心问题：

> 我们研究的究竟是哪一个 handover boundary？

任务：

- 固定 `upstream intralogistics → formation carrier → formation equipment`；
- 在综合dossier附表中建立4–6个核心来源的source–claim register；
- 核对两项专利的申请人、公开日、family、图号、claims/description；
- 明确每个来源中的flow object究竟是cell、tray、battery module还是未充分定义；
- 对Architecture A和B分别执行准入检查；
- 选出一个primary architecture，另一个只作comparator；
- 在dossier中画一张最小边界图，不画完整工厂。

#### Day 1案例准入门

一个来源只有同时满足以下条件，才可成为primary case：

1. 明确属于lithium-ion **cell manufacturing / formation**，不是module/pack装配或其他电池使用场景；
2. 被transfer的load/carrier object可以辨识，或至少其边界能够可靠解释；
3. 来源明确描述load/carrier进入formation equipment，而不是只在附近运输；
4. 关键结构可追溯到原始图、claims或description。

每项记录`YES / NO / UNKNOWN + exact evidence`。如果两项专利都不能通过，不得为了凑card而扩展到module/pack；本周可以得出“公开primary case不足”。

最低产出：在综合dossier内完成准入表并选定primary；不增加独立文件。

### Day 2 — 深读primary，轻量检查comparator

核心问题：

> 公开设备结构实际上怎样把载荷送入formation equipment？

Primary完整填写，comparator只填写能够形成反例的必要字段：

```text
Source:
Cell / load object:
Upstream equipment:
Transfer actor/mechanism:
Destination equipment:
Positioning or detection:
Control/acceptance evidence:
Validation stage:
Source-explicit evidence type:
Source-explicit content:
Engineering inference:
Unknown:
```

最低产出：primary完整card和comparator轻量card，均留在同一dossier。第三种supplier architecture只作为可选扩展。

### Day 3 — 建立 evidence-bounded handover states

核心问题：

> 运输任务在什么条件下才真正完成？

起始状态骨架：

```text
Carrier arrives at interface
→ identity / load condition checked?
→ destination available?
→ transfer mechanism engages
→ carrier/load physically transferred
→ positioned / locked?
→ process interface established?
→ equipment acceptance signal?
→ ownership/state updated
→ handover completed
```

规则：

- 问号表示不能自动假定；
- 状态图只对应primary architecture，不把comparator内容补入图中；
- 每条箭头必须能够回到primary来源，或明确写为engineering inference；
- 专利明确披露的动作标记为`SOURCE-EXPLICIT—PATENT CLAIM/EMBODIMENT`，不标记为现实部署`FACT`；
- 图旁单列validation status；
- `physically delivered` 与 `equipment accepted` 分开；
- `positioned`、`mechanically locked`、`pressure applied` 和 `electrically contacted` 不得合并成一个模糊动作；
- comparator如有不同，只在对照card中记录，不强行形成统一流程。

最低产出：在综合dossier中加入一张可编辑primary state diagram及其evidence table。此处不写SimPy。

### Day 4 — 检查battery-specific requirement

核心问题：

> 哪些handover要求来自cell formation，而不是一般pallet logistics？

优先检查：

| 候选维度 | 假设/证据起点 | 是否适用于primary？ | 必须继续确认 |
| --- | --- | --- | --- |
| Carrier contact | Schomburg支持某类carrier contact功能 | `YES / NO / UNKNOWN + source` | 接触由carrier、cabinet还是独立机构完成 |
| Fixture/pressure | Deng支持其案例中的tray fixture与受控施压 | `YES / NO / UNKNOWN + source` | 施压是否属于primary的transfer、process或二者之间 |
| Identity mapping | 专利线索可能包含carrier identification | `YES / NO / UNKNOWN + source` | Primary是否需要cell–slot–tray–channel一致性，以及谁校验 |
| Process readiness | Working hypothesis：工艺开始可能需要状态许可 | `YES / NO / UNKNOWN + source` | Primary是否公开release/acceptance条件；未找到前不得当作事实 |

判断标准：

- 如果只剩“到站—定位—放货—确认”，且没有cell-specific约束，Candidate A的论文价值下降；
- 如果工艺接触、压力、身份或process readiness确实改变handover状态，继续检查其研究与验证价值；
- thermal runaway、泄漏和隔离只记录为secondary branch，本周不展开安全系统设计。

最低产出：把`general logistics vs battery-specific`判断合入Candidate A压力测试，不另建文件。

### Day 5 — Candidate A压力测试与Thomas汇报

核心问题：

> 看完具体设备证据后，Candidate A还剩下什么？

必须回答：

1. 公开技术已经描述到了哪些机械/信息/控制状态？
2. 剩余未知是科学问题、工程实施细节、商业保密，还是我们的检索不足？
3. 剩余问题是否会影响可靠交接、质量、设备可用性或系统集成？
4. 是否能通过真实设备资料或专家获得验证？
5. 这个候选是否符合Master Thesis范围？

最低产出：综合dossier中的一页Candidate A decision memo；Thomas meeting brief从这一页裁剪，不算额外最低产出。

---

## 8. 给Thomas的四个决定性问题

1. **Do we have access to a concrete formation carrier or equipment interface at FFB/PEM that could serve as a reference case?**
2. **Is the operational handover between intralogistics and formation equipment a sufficiently relevant technical problem, or is it already a mature engineering detail from your perspective?**
3. **Is there an equipment or intralogistics expert who could validate the actual transfer, positioning, process-contact and acceptance sequence?**
4. **Should this carrier-interface case be narrowed further as a possible thesis case, or remain only a learning case while another battery-specific problem is considered?**

若组会尚未发生，计划不能假装已经有验证入口；应将其状态写为`pending supervisor/expert confirmation`。

---

## 9. Week 05周末决策门

### A. KEEP — 继续进入problem definition

对以下四项逐一记录`YES / NO / UNKNOWN + evidence`：

| KEEP条件 | 必须达到的含义 |
| --- | --- |
| Concrete reference interface | Primary通过Day 1准入门，并能追溯其对象、transfer和destination |
| Directly supported battery-specific condition | 至少一个不是普通pallet logistics的条件直接适用于primary |
| Meaningful problem | 剩余问题会实际影响可靠交接、质量、可用性或系统集成，而不只是资料写得少 |
| Credible validation route | 已识别具体专家、FFB/设备接口资料或另一种可执行验证方法；不能只写“以后问Thomas” |

只有四项均为`YES`，才进入KEEP。

Week 06才可以开始认真写：

```text
practical problem
→ candidate research question
→ suitable method
→ validation plan
```

即使KEEP，也不自动等于需要离散事件仿真。

### B. NARROW — 进一步缩小

适用情况：

- 整体handover过宽，但某一个子问题（例如equipment acceptance condition）具有直接证据、明确意义和可信验证路径；
- information/identity只需保留为handover completion condition，而不应独立扩成大课题；
- 需要删除无证据或无验证路径的transfer/contact子层，只保留可研究部分。

### C. ABANDON / ADJUST — 放弃或换候选

适用情况：

- 技术资料与Thomas均表明它已经成熟，而且没有剩余的重要可研究问题；
- 没有重要的battery-specific requirement；
- 无法获得任何设备、专家或其他验证入口；
- 研究价值只能靠“公开论文没写”维持。

此时返回Week 04 problem-area map，重新评估exception-triggered carrier flow或其他更可验证问题，不为了保留原计划而强行继续。

### D. CONTINUE LEARNING — 允许短期延长

适用情况：接口理解明显变清楚，但组会/专家确认尚未发生。最多允许一个受控延长周期，不无限增加专利或相邻案例。

---

## 10. 有余力再做

只有三项最低成果完成后，才可选择以下一项扩展：

- 补充第三种formation-equipment architecture，但必须有比供应商营销概述更具体的结构证据；
- 追踪一项关键专利的family/citations，检查是否存在更早、更强的直接反例；
- 在主handover状态图旁登记reject/rework需要哪些未知状态，但本周仍不重建异常流程；
- 将最终状态图整理成一页Thomas组会图。

以上均不是Week 05成功条件，不得同时全部开展。

---

## 11. 本周明确不做

- 不写SimPy或其他仿真代码；
- 不做AGV fleet sizing、dispatching、routing或parking；
- 不做AGV与humanoid比较；
- 不设计自己的formation cabinet、tray或transfer mechanism；
- 不把专利性能主张当作验证结果；
- 不把两项专利拼成一条实际生产线；
- 不做完整专利landscape；
- 不计算ROI、成本节省或产能提升；
- 不建立thermal-runaway应急系统；
- 不宣布最终research gap、最终research question或最终题目；
- 不因资料来自battery formation就自动认定所有状态都是battery-specific。

---

## 12. 工作方式调整：提速但不跳步

Week 05不再为Day 1–5分别制作大型HTML讲义。只维护一个综合case dossier，并按研究节点更新。

### 加速的部分

- 不再反复填空复述direct/adjacent等已经掌握的原则；
- 不扩展humanoid和泛化AGV知识；
- 不以页面数量衡量进度；
- 学生先尝试完整解释一张设备图，Codex只修正关键断点；
- 每次学习结束明确记录“这项证据怎样改变Candidate A”。

### 仍需慢下来的部分

- 原始专利图、claims和description的准确对应；
- flow object与cell/manufacturing scope；
- transfer、positioning、contact和acceptance的分界；
- 专利公开、工业部署与学术验证的区别；
- 专家/设备验证入口是否真实存在。

---

## 13. 三方职责

### 学生

- 能够从头讲清primary architecture中载荷怎样进入formation equipment，并说明comparator在哪一点形成反例；
- 主动指出图中哪些是transport、transfer、position/contact和acceptance；
- 不要求背专利号，但应知道每项结论来自哪一类证据；
- 在组会中提出四个决定性问题，并尽可能原样带回Thomas反馈；
- 参与`KEEP / NARROW / ABANDON / CONTINUE LEARNING`决定。

### Codex

- 精读专利原文和图纸，核对申请人、family、公开时间、claims与description；
- 建立独立architecture cards，禁止跨来源拼接；
- 绘制只对应primary的可编辑state diagram与evidence table；
- 区分peer-reviewed statement、patent claim/embodiment、engineering inference和unknown，并单列validation status；
- 控制范围与学习节奏；
- 根据Thomas反馈更新决策记录，但不擅自宣布gap。

### GPT

- 作为外部审查者检查Candidate A是否在技术反例后仍成立；
- 检查是否把专利误当现场部署，或把多个来源误拼；
- Week 05成果push后审查`KEEP / NARROW / ABANDON`决定；
- 不自动引入optimization、ROI、robustness或新技术支线。

---

## 14. 计划完成标准

Week 05计划执行完成时，学生应能用自己的话回答：

> 一个formation载荷如何从外部物流进入设备，哪些动作有来源支持，哪些接触/确认仍未知，哪些要求真正来自电芯formation，以及为什么该接口应该被保留或放弃为论文候选案例。

如果只能复述专利结构，却不能解释它怎样改变Candidate A，则本周仍未完成。

如果Candidate A最终被反例推翻或被Thomas判断为成熟工程细节，只要证据链和决策透明，Week 05仍然成功。
