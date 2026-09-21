# Thesis Registration Consensus and Research Route / 论文注册共识与总体研究路线

> 初始记录日期：2026-08-20
> 最近同步：2026-09-20
> 当前状态：**2026-09-18 注册材料已经记录当前题目、摘要、RQ、范围与工作包；学生于 2026-09-20 确认题目、基本摘要和方向已经确定。它们是当前研究基线，不再作为开放选题提案。**
> 行政边界：仓库中的注册表仍未显示导师、教授或 ZPA 签字，不据此声称正式注册、正式开始日期或截止日期已经生效。
> 适用阶段：注册方案设计完成后、正式研究执行开始。
> 研究方向依据优先级：Thomas 最新明确反馈 → `abschlussarbeiten_42444.pdf` → `docs/research_direction_guardrails.md` → 本记录 → 周计划与工作假设。

## 0. 本次决策的结论

本项目已从 Week 01–02 的宏观应用梳理、Week 03–05 的 formation/tray-flow 学习与反例审计、Week 06 的 Pack EoL 方法原型，推进到注册方案设计完成并开始正式建立证据基础与研究方法的阶段。

当前研究基线为：

1. 论文应保持 `robotic systems in battery manufacturing` 的上位范围，而不是注册成单一品牌、单一机器人或单一 Pack EoL 工位研究；
2. 论文核心不是开发机器人算法或证明 humanoid 更优，而是建立并应用一套透明、可复核的任务驱动评价方法；
3. Pack EoL test-connector handling 作为第一个 deep reference case，用于建立方法原型，但不等于最终题目只研究 Pack EoL；
4. humanoid/mobile dual-arm system 是被评价的候选架构之一，必须与 dedicated automation、fixed industrial robot、cobot/mobile system 等方案进行条件化比较；
5. 论文应采用一个 deep case 加一至两个证据足够的 adjacent cases，通过 cross-case comparison 检验方法的适用范围；
6. 论文结论必须回答“在什么任务和生产条件下适合、为什么适合、怎样实施”，而不是制作机器人应用目录或品牌排名；
7. 2026-09-18 材料已经明确 scope covers selected lithium-ion battery cell, module, and pack manufacturing；这允许跨层级选择案例，但不要求每个层级各选一个，也不允许无迁移论证地混用不同层级证据。

## 1. 当前论文题目

### English

> **Task-Based Assessment of Robotic Systems in Battery Manufacturing: Application Potential and Implementation Strategies**

### Deutsch

> **Aufgabenbasierte Bewertung von Robotersystemen in der Batteriefertigung: Anwendungspotenziale und Implementierungsstrategien**

### 中文理解

> **面向电池制造的机器人系统任务驱动评估：应用潜力与实施策略**

### 题目选择理由

- `Robotic Systems in Battery Manufacturing` 保留 Thomas 原始 working title 的研究对象与工业场景；
- `Application Potential and Implementation Strategies` 保留 Thomas 要求的应用识别、技术经济评价和工业实施导向；
- `Task-Based Assessment` 明确论文的方法主线，又不把方法锁死成某一种评分模型、算法或实验；
- 题目不把 Pack EoL 或 humanoid 写死，因此相邻案例可以根据后续证据和 Thomas 反馈调整；
- 题目足够具体，能够区别于一般性的 battery manufacturing 或 robotics overview，同时仍适合普通硕士论文的工作量。

### 暂不采用的题目方向

- 不采用 `Humanoid Robots in Battery Manufacturing...`：会预设机器人形态是答案，且直接同行评审和独立工业证据仍不足；
- 不采用 `Robotic Connector Handling in Battery-Pack EoL Testing...`：对注册题目而言过窄，无法完整覆盖 Thomas 原始任务与 cross-case comparison；
- 不采用 AGV fleet sizing、formation handover 或控制算法题目：Week 03–05 的证据审计没有把这些方向建立成当前机器人论文核心；
- 不采用纯 `Overview/Review of Robotics...`：容易退化成应用目录，无法体现透明、可复用的分析方法。

## 2. 当前三个研究问题

### RQ1 — Task and requirements

> **Which task and process characteristics determine the suitability of different robotic system architectures in selected battery manufacturing applications?**

中文：

> 哪些任务与工艺特征决定不同机器人系统架构在选定电池制造应用中的适用性？

RQ1 用于识别和结构化：制造任务、操作对象、工艺边界、质量与安全要求、节拍与产品变化、系统责任和机器人能力需求。

### RQ2 — Architecture comparison and conditional suitability

> **Under which technical, economic, quality, safety, and integration conditions are the considered robotic architectures suitable compared with dedicated automation and manual reference solutions?**

中文：

> 在哪些技术、经济、质量、安全与集成条件下，所研究的机器人架构相对于专用自动化和人工参考方案是适用的？

RQ2 不产生脱离场景的全局排名，而是比较 dedicated fixed-purpose automation、fixed industrial robots、cobots、mobile robots/mobile manipulators、humanoid/mobile dual-arm systems，以及必要时的 manual baseline 在不同条件下的 suitability boundary。

### RQ3 — Industrial implementation

> **Which implementation strategies and remaining research needs can be derived from the comparative case assessment?**

中文：

> 可以从比较案例评价中导出哪些实施策略和仍待研究的问题？

RQ3 用于形成：工程边界、安全与质量保障条件、机器人与 PLC/MES/测试设备的责任划分、成本驱动因素、分阶段实施路线、试点需求和未来研究建议。

三个 RQ 构成递进链：

```text
RQ1: Which task/process characteristics determine suitability?
  ↓
RQ2: Under which conditions is each architecture suitable relative to the references?
  ↓
RQ3: Which implementation strategies and remaining research needs follow?
```

## 3. 论文要解决的 practical problem 与 research need

### 3.1 Practical problem

电池制造企业面对 dedicated automation、fixed industrial robots、cobots、mobile manipulators 和 humanoid/mobile dual-arm systems 等不同方案时，不能仅根据“柔性”“智能”或单一企业案例完成技术选择。电池制造任务同时受到产品层级、操作对象、质量、安全、节拍、产品变化、设备接口、工厂布局和经济条件约束。

因此，实际决策问题是：

> 如何把具体 battery-manufacturing task 及其 process/production requirements 转化为可比较的 robotic capabilities，并据此判断不同架构在什么条件下值得采用、继续评价或排除？

### 3.2 Research need

当前可用证据分散在 battery-process literature、production-system research、general robotics literature、industrial/equipment baselines、patents 和 company disclosures 中，证据层级、任务边界和评价指标并不一致。这使 task-level cross-architecture comparison 与 implementation decision 难以保持透明和可追溯。

注册阶段应把这一点写为 **research need / unresolved problem**，而不是未经系统检索就宣称：

> `No framework exists` 或 `This is the first study`。

精确的 closest work 与 novelty boundary 必须在正式 scoped/systematic literature search 后确认。

### 3.3 Research objective

> Develop and apply a transparent, task-based assessment approach that links battery-manufacturing requirements to robotic-system capabilities, compares alternative architectures conditionally, and derives evidence-bounded industrial implementation strategies.

中文：

> 建立并应用一套透明的任务驱动评价方法，将电池制造要求映射到机器人系统能力，比较不同架构的条件化适用性，并形成具有证据边界的工业实施策略。

## 4. 论文类型、研究范围与案例路线

### 4.1 Thesis profile

本论文定位为：

> **Evidence-based prospective robotics application assessment in battery manufacturing**

它以文献、工业案例、任务与生产要求分析、机器人能力评价、条件化场景和实施策略为核心，不要求以新算法、控制器、机器人硬件、真机平台、大规模数据或仿真作为成立前提。

### 4.2 Deep reference case

第一个 deep reference case：

> **Battery-pack EoL test-connector handling**

主要分析对象是 connector 与 flexible harness 的物理处理任务，不是 EoL 电气测试算法本身。Robot、test equipment、PLC/safety、MES/traceability 和 fixture/station 的责任必须分开。

Pack EoL 能集中呈现：

- flexible-object handling；
- contact-rich insertion/removal；
- high-voltage safety interface；
- connector-state/connection-quality confirmation；
- product variation and changeover；
- PLC、MES、测试设备和机器人集成。

CATL/Spirit AI `Xiaomo/Moz` 仅作为 direct industrial disclosure 和现实锚点，不是论文研究对象，也不独立证明成功率、节拍、成熟度或经济优势。DCR 保持 adjacent，除非证据确认它与 EoL 使用相同任务抽象、connector、station 或 robot。

### 4.3 Adjacent cases

使用一至两个证据足够的相邻案例检验框架迁移：

1. **Candidate A — cell identification, grasping and loading**：当前领先的 adjacent case；
2. **Candidate C — multi-station material handling and picking**：只有在 flow object、任务边界和证据足够具体时才进入；
3. 其他案例只有通过 robotics-relevance gate 与 evidence minimum 后才可替换或加入。

不同时打开所有案例。案例数量服从证据质量、论文篇幅和 cross-case comparison 的实际需要。

### 4.4 Current production-level boundary

2026-09-18 注册摘要和注册表明确写明 scope covers selected lithium-ion battery **cell, module, and pack manufacturing**。当前执行规则是：

- Pack EoL test-connector handling 在 pack 层级作为 detailed reference case；
- adjacent applications 根据证据选择，可位于 cell、module 或 pack 层级；
- 每个 claim 和 case 必须标注 production level；
- 不要求最终案例组合覆盖全部三个层级；
- 跨层级转移要求、能力或结论时，必须说明等价条件、非等价条件和迁移限制。

### 4.5 Out of core scope

- battery recycling/disassembly，除非 Thomas 正式扩展范围；
- detailed robot-control、VLA training、motion-planning 或 grasping algorithm development；
- robot body/end-effector hardware development；
- AGV fleet sizing/dispatching，除非以后明确服务于某个 RQ；
- 无可靠输入的 quantitative ROI、cycle time、yield 或 maturity ranking；
- 只为产生“实验结果”而构造的 simulation。

## 5. 分析方法与证据纪律

### 5.1 Core analytical chain

```text
Manufacturing task
→ Task characteristics and responsibility boundary
→ Process / production requirements
→ Existing automation and manual baseline
→ Required robotic-system capabilities
→ Task–capability matching
→ Conditional suitability under production scenarios
→ Technical, economic and integration barriers
→ Implementation strategies and future potential
```

Week 06 的 `Task → Requirement → Capability → Suitability` 是方法原型，不是论文最终贡献。论文需要继续完成指标操作化、系统文献证据、deep-case application、adjacent-case transfer、counterexample analysis 和 cross-case synthesis。

### 5.2 Current method

当前采用：

> **Evidence-based comparative multiple-case assessment**

主要步骤：

1. 开展 scoped/systematic evidence search，记录数据库、关键词和纳入排除规则；
2. 使用 robotics relevance、case boundary 和 evidence sufficiency 选择案例；
3. 分解 task cycle、manipulated object、failure modes 和 system responsibility；
4. 提取 task、process 和 production requirements；
5. 把 requirements 映射到 sensing、manipulation、mobility、safety、integration 和 operational capabilities；
6. 比较不同 robotic architectures 与 fixed-purpose automation baseline；
7. 在 product mix、volume/takt、changeover、multi-station、brownfield、quality、safety 和 scalability 条件下形成 conditional suitability；
8. 分析技术、经济和集成障碍；
9. 通过 adjacent cases 检验并修正框架；
10. 导出 implementation strategies、decision rules、limitations 和 future research。

### 5.3 Evidence classes

关键判断必须标注证据身份：

- `PEER-REVIEWED EVIDENCE`；
- `DIRECT COMPANY DISCLOSURE`；
- `INDUSTRIAL / EQUIPMENT BASELINE`；
- `PATENT EVIDENCE`；
- `CROSS-INDUSTRY EVIDENCE`；
- `ENGINEERING INFERENCE`；
- `UNKNOWN`。

继续使用：

```text
Claim
→ Source
→ Exact page/section where available
→ Evidence type
→ Battery-manufacturing implication
→ Robotics implication
→ Transfer limit / unknown
```

并在综合判断中区分：

```text
Known / Inferred / Unknown
```

### 5.4 Economic assessment boundary

经济评价优先分析：equipment and integration investment、end effector/peripherals、safety、commissioning、changeover、maintenance、training、utilization、reuse potential、product mix 和 production volume。

有可靠数字时才使用范围或情景计算；没有可靠数字时采用透明的 cost-driver/scenario-based qualitative assessment，不虚构 ROI。

### 5.5 Validation and credibility

论文可信度可由以下组合建立：

- peer-reviewed battery and robotics literature；
- industrial/equipment baselines；
- direct company disclosures with explicit limits；
- bounded cross-industry transfer；
- transparent engineering reasoning；
- cross-case replication and counterexamples；
- scenario/sensitivity checks；
- optional expert review、simulation 或 quantitative analysis。

专家访谈、真机实验或仿真属于可选增强项，不是当前题目成立的普遍硬门。

## 6. 预期贡献与论文输出

合理、可交付的贡献是：

1. 一套可追溯的 task-based robotics application assessment procedure；
2. Pack EoL connector-handling deep case 的任务、要求、能力与架构比较；
3. 一至两个 adjacent cases 对方法可迁移部分和边界的检验；
4. 不同机器人架构相对于 fixed-purpose automation 的 conditional suitability map；
5. 面向 selected applications 的技术、经济和集成实施策略；
6. 对证据不足、不能迁移和仍需工业验证问题的明确说明。

预期研究工件包括：

- evidence and claim matrix；
- case charter and task/responsibility maps；
- requirement catalogue；
- architecture capability profiles；
- scenario-based suitability matrix；
- cross-case comparison；
- implementation roadmap and research recommendations。

论文不声称创造新机器人算法、证明 humanoid 普遍优越或给出无数据支撑的统一架构排名。

## 7. 论文主故事与章节草案

```text
Practical industrial decision problem
→ Fragmented evidence and task-level comparison need
→ Task-based assessment approach
→ Deep Pack EoL reference case
→ Adjacent-case transfer and comparison
→ Conditional suitability findings
→ Technical/economic/integration strategies
→ Limitations, future robotics trends and recommendations
```

暂定章节：

1. Introduction；
2. Battery Manufacturing and Robotic Systems；
3. State of Research and Research Need；
4. Research Methodology；
5. Deep Reference Case: Pack EoL Test-Connector Handling；
6. Assessment of Adjacent Applications；
7. Cross-Case Discussion and Implementation Strategies；
8. Conclusion and Outlook。

正式写作时可根据篇幅合并 Chapter 2/3 或 Chapter 5/6，但不得破坏 practical problem → method → evidence → findings → implementation 的逻辑链。

## 8. Week 01–06 如何汇入论文

```text
Week 01
Battery fundamentals → process requirements → initial robotics opportunities
  ↓
Week 02
Process/problem/robotics map；Thomas指出仍过于宏观
  ↓
Week 03
Formation–aging–testing tray flow；学会任务、事件、系统边界和unknown
  ↓
Week 04
Nearest-neighbour and counterexample audit；不把资料空白冒充gap
  ↓
Week 05
Fixed formation-loading architecture；证明automation interface不自动等于robotics problem
  ↓
2026-08-12 direction reset
回到Thomas的industry-forward robotics applications，并关注humanoid但不预设优势
  ↓
Week 06
Pack EoL connector handling deep case；形成Task–Requirement–Capability–Suitability方法原型
  ↓
Registration and formal research
系统检索 → 方法操作化 → deep case → adjacent cases → cross-case findings → implementation strategies
```

Week 03–05 不是失败或应删除的旧工作。它们形成了本论文的重要研究纪律：不拼接不同工厂、不把 automated equipment 自动称为 robot、不把 unknown 自动称为 gap、先检验机器人相关性再深化接口细节。

## 9. 逻辑一致性审查

### Thesis positioning

本论文不是 benchmark、算法 Technique paper 或纯综述。它更接近 applied engineering assessment / new decision setting：把 task-based technology assessment 应用于 selected battery-manufacturing robotic applications，并通过多个案例形成可审计的决策逻辑。

### Current limitations

1. 电池制造、机器人能力与工业披露之间的证据分散，任务边界和评价指标不统一；
2. 单个企业 deployment 不能回答 architecture suitability 和 general implementation 条件；
3. humanoid 与新型 mobile manipulation 的直接、独立工业性能和经济数据不足。

### Goal

建立并应用透明的 task-based comparative assessment，在不超出证据的前提下形成 conditional suitability 和 implementation strategies。

### Challenges → method modules

| Challenge | Method module |
| --- | --- |
| 不同来源的任务边界与证据等级不一致 | Evidence contract + task/responsibility decomposition |
| 制造要求无法直接等同于机器人宣传的“能力” | Requirement extraction + capability mapping |
| suitability 随产量、品种、换型、布局、安全和集成条件变化 | Scenario-based architecture comparison + cross-case analysis |

### Consistency result

- Limitations → Goal：PASS；
- Goal → Challenges：PASS；
- Challenges → Methodology：PASS；
- Methodology → Contributions：PASS。

目前没有阻止当前研究基线继续执行的 critical chain break。Evidence sufficiency、closest-work boundary、框架操作化和相邻案例准入是正式研究阶段需要管理的 major risks，不是当前需要重新选题的理由。

## 10. 当前确认状态与行政待办

### 已进入当前研究基线

1. 当前英文/德文题目；
2. 2026-09-18 材料中的 RQ1–RQ3；
3. selected cell/module/pack manufacturing applications 的范围；
4. Pack EoL test-connector handling 作为 detailed reference case；
5. 一至两个 evidence-based adjacent applications；
6. humanoid/mobile dual-arm 作为比较候选架构之一，而非预设答案；
7. structured literature and case analysis + comparative multiple-case assessment 的总体方法。

### 仍需行政确认或外部状态更新

1. 导师、教授和必要审批人的签字状态；
2. ZPA 是否已完成注册；
3. 正式开始日期和提交截止日期；
4. 当前适用的 PEM/RWTH/ZPA 模板、程序、考试规则和引用要求；
5. 是否存在可用 expert/industry access；若没有，继续采用已设计的 secondary-evidence strategy。

上述行政未确认事项不得被重新解释为题目、RQ 或案例方向仍处于开放选择状态。

## 11. 下一阶段总体路线

### Fixed execution order

1. **研究基线冻结**：同步当前题目、RQ、范围、案例角色与确认/注册状态，并保留变更记录；
2. **正式证据协议**：建立可复现的检索、筛选、去重、证据分类和页码追踪规则；
3. **Pack EoL 证据审计**：逐条形成 `retain / retain conditionally / downgrade / remove` 决定；
4. **Framework v1.0**：操作化任务特征、生产要求、机器人能力、评价维度、判断规则和证据门；
5. **相邻案例闸门**：先对 Candidate A 执行 `F0`–`F3`，通过后才开展完整第二案例；
6. **跨案例与实施策略**：使用同一框架比较案例，并形成有证据边界的技术、经济、安全、质量、可扩展性与集成建议；
7. **论文写作**：Method 可在协议与 Framework v1.0 稳定后起草，Results/Discussion 必须等待证据矩阵和案例评价完成。

当前立即执行步骤是第 2 项。第 1 项以本文件、`AGENTS.md` 和 `docs/research_direction_guardrails.md` 同步完成为结束条件。

## 12. 变更控制

本文件起源于 2026-08-20 的注册提案，并于 2026-09-20 同步为当前研究基线。今后若 Thomas 修改题目、RQ、生产层级、案例路线或方法，应同时更新：

1. 本文件的状态与变更记录；
2. `AGENTS.md` 的 registration checkpoint；
3. `docs/research_direction_guardrails.md` 中受影响的边界；
4. 当前周计划和 case charter。

不得因新新闻、单一企业案例、某个 Skill 的模板或为了保持周计划连续性而静默改变题目与研究问题。

### 变更记录

- **2026-08-20**：形成学生–GPT–Codex 注册提案；题目、RQ 和 production-level boundary 尚待确认。
- **2026-09-18**：最新 abstract 和 Masterarbeit registration-form review copy 记录当前题目、修订后的 RQ1–RQ3、cell/module/pack scope、Pack EoL reference case、一个至两个 adjacent applications、四个工作包和 18 周计划。
- **2026-09-20**：学生确认题目、基本摘要和方向已经确定；本文件由历史提案升级为当前内部研究基线。行政注册状态仍单独保留为未验证。

## 13. 关键项目来源

- `abschlussarbeiten_42444.pdf`：Thomas 原始 working title、任务轮廓和评价维度；
- `week_06_candidate_b_pack_eol/00_2026-08-12_Thomas组会反馈.md`：Pack EoL 被认可为可继续方向、跨行业证据与注册准备反馈；
- `week_06_candidate_b_pack_eol/01_Week06工作计划_Candidate_B_Pack_EoL.md`：deep-case 边界和方法原型；
- `week_06_candidate_b_pack_eol/day1_pack_eol_robotics_chinese_learning_guide.html` 至 `day5_deep_case_synthesis_framework_chinese_learning_guide.html`：Pack EoL 任务、要求、架构和框架学习链；
- `week_07_registration/Fuhan_Liao_PEM_Abstract_Full_Thomas_Review.pdf`：2026-09-18 当前摘要、RQ、scope 和 work packages；
- `week_07_registration/Fuhan_Liao_Erfassungsbogen_Masterarbeit_Thomas_Review.pdf`：2026-09-18 当前题目、任务说明和 18 周工作计划；
- `docs/research_direction_guardrails.md`：项目方向、案例状态与证据纪律；
- `docs/pem_thesis_requirements.md`：注册 abstract、写作、引用、图表、提交与答辩要求；
- `docs/collaboration_and_pacing.md`：六个月节奏、周计划与协作方式；
- `AGENTS.md`：长期执行约束和 Skill 路由。
