# Week 06工作计划：用Pack EoL接插件处理建立论文分析方法原型

> 校准日期：2026-08-13
>
> 制定依据：Thomas原始课题PDF、2026-08-12组会反馈、Week 01–05成果、`AGENTS.md`、`docs/research_direction_guardrails.md`、`docs/collaboration_and_pacing.md`以及学生与GPT对论文定位的进一步讨论。
>
> 当前状态：**Battery-Pack EoL test-connector handling是第一个deep reference case；不是整篇论文唯一case，也不是最终注册题目、最终gap或最终RQ。**
>
> Production level：**battery-pack manufacturing**。Thomas已认可Pack EoL testing作为可继续研究的方向；注册abstract仍须明确其与原始`battery cell production value chain`措辞的关系。

---

## 0. Week 06结论先行

Week 06不再承担“Candidate B能否成为唯一最终case”的生死审查。它的作用是：

> **把Pack EoL test-connector handling作为第一个深度案例，第一次完整跑通并提炼整篇论文可迁移的分析方法。**

本周唯一核心问题：

> **For battery-pack EoL test-connector handling, what task and production requirements determine the suitability of dedicated automation, fixed industrial robots, and humanoid/mobile dual-arm systems?**

中文：

> **对于Battery Pack EoL测试接插件处理任务，哪些任务特征和生产要求决定了专用自动化、固定工业机器人以及人形/移动双臂机器人各自的适用性？**

本周的核心逻辑是：

```text
Manufacturing task
→ Task characteristics
→ Process / production requirements
→ Existing automation baseline
→ Required robotic capabilities
→ Task–capability matching
→ Conditional suitability
→ Implementation barriers and scenarios
```

不是问“humanoid能不能做”，也不是比较品牌，而是回答：

> **在什么条件下，哪一种机器人/自动化架构更有理由被采用或继续评价？**

---

## 1. 这篇论文现在应被理解成什么

当前thesis更接近：

> **Evidence-based prospective robotics application assessment in battery manufacturing**

论文主要依靠：

- literature review；
- industrial cases与equipment baselines；
- robotics technology assessment；
- battery-manufacturing task analysis；
- task–capability matching；
- scenario-based conditional assessment；
- implementation strategy与future potential。

论文不以以下内容为必要成果：

- 新robot algorithm、controller或foundation model；
- 新robot hardware或end effector设计；
- 大型代码项目；
- 真机平台与大量实验数据；
- 为了得到结果而构造的产线仿真；
- 必须获得CATL或其他企业的内部数据。

Expert review、实验、simulation或quantitative analysis如果以后确实能回答一个明确问题，可以作为增强证据；没有它们不代表论文不成立。

但偏综述不等于纯描述。最终必须从“有哪些机器人”推进到：

> **为什么某类机器人在某种电池制造任务和生产条件下适合、不适合或值得进一步研究，以及这个判断为何可信。**

---

## 2. 整篇论文的暂定研究路线

当前采用：

> **1个deep reference case + 2–3个adjacent battery-manufacturing cases**

```text
Week 06
Deep case: Pack EoL test-connector handling
→ 建立Task–Requirement–Capability–Suitability Framework v0.1

Week 07（暂定，须由Week 06结果确认）
Adjacent case 1: cell recognition / grasping / loading
→ 用同一框架检验可迁移性

Week 08及以后（不是硬计划）
Adjacent case 2: multi-station handling / picking或证据更强的任务
→ cross-case comparison
→ task characteristics favoring different robotic systems
→ application potential、implementation barriers、future trends和recommendations
```

CATL/千寻“小墨”只是Candidate B的现实industrial anchor，不是论文研究对象。论文研究对象是更一般的：

> **Pack EoL测试接插件处理任务中的机器人系统适用条件和实施选择。**

---

## 3. Deep-case边界

### 3.1 Included

| 字段 | Week 06边界 |
| --- | --- |
| Production level | Battery Pack |
| Primary process | Pack End-of-Line testing |
| DCR | adjacent / possibly related；不默认与EoL使用同一工位、connector或robot |
| Manipulated object | test connector + flexible harness |
| Physical task | locate → grasp/support harness → align → insert → confirm → remove → return |
| Compared architectures | dedicated automation / fixed industrial robot / humanoid or mobile dual-arm system |
| Human operation | reality reference，不作为目标架构 |
| Deep-case purpose | 建立可迁移的task–requirement–capability–suitability方法原型 |

### 3.2 Responsibility boundary

```text
Robot / connector automation
→ physical connector and harness manipulation

Test equipment
→ electrical measurement and test execution

PLC / safety system
→ permission, interlock, safe state and safe stop

MES / traceability
→ pack identity, test recipe and result association

Fixture / station
→ pack positioning and physical station support
```

这是分析框架。CATL/千寻现场的实际责任分配仍须标记为`UNKNOWN`，除非同一case的直接资料支持。

### 3.3 本周不研究

- CATL“小墨”的性能评测或品牌研究；
- DCR电气测量模型和EoL测试标准全文；
- humanoid步态、全身控制、VLA训练、轨迹规划和抓取算法开发；
- connector的虚构几何、力值、节拍、成本或成功率；
- formation handover、AGV fleet sizing或dispatching；
- final title、final gap、final RQ和定量ROI；
- 缺乏现实输入、只为产生“实验结果”的仿真。

---

## 4. Evidence strategy

Week 06使用`credible evaluation / evidence strategy`，不是“必须找到实验验证入口”。

### 4.1 证据层级

| 标签 | 用途与边界 |
| --- | --- |
| `PEER-REVIEWED EVIDENCE` | 支持任务物理、机器人能力、方法或已研究限制；不得脱离原配置外推性能 |
| `DIRECT COMPANY DISCLOSURE` | 支持企业声称的任务或部署；不独立证明可靠性、节拍、经济性或优越性 |
| `INDUSTRIAL / EQUIPMENT BASELINE` | 支持传统设备或机器人方案确实存在；需标明是否为相同工序 |
| `CROSS-INDUSTRY EVIDENCE` | 支持可迁移的物理能力或评价维度；必须记录等价与不等价之处 |
| `ENGINEERING INFERENCE` | 透明推理；不能冒充已观察现场事实 |
| `UNKNOWN` | 当前证据不能回答；不自动等于research gap |

### 4.2 可组合的可信证据

```text
Battery manufacturing / testing literature
+ robotics manipulation literature
+ industrial equipment baselines
+ direct humanoid industrial disclosures
+ bounded cross-industry transfer
+ transparent task–capability reasoning
+ scenario-based assessment
+ optional expert review / simulation
```

每个关键结论至少应记录：

```text
Claim
→ Source and exact section/page where possible
→ Evidence type
→ Battery-manufacturing implication
→ Robotics implication
→ Transfer limit / unknown
```

### 4.3 跨行业迁移检查

| 字段 | 必须回答 |
| --- | --- |
| Source task | 原行业处理什么对象、接口和工作环境？ |
| Transferable attribute | 它支持视觉、柔性物体处理、force control、插接、双臂还是移动？ |
| Battery equivalence | 与Pack EoL相同的物理或系统要求是什么？ |
| Non-equivalence | 高压、安全、connector geometry、节拍和成熟度哪里不同？ |
| Allowed inference | 能迁移到能力、方法或评价维度的哪一层？ |
| Forbidden inference | 哪些性能数字和部署结论不能迁移？ |

---

## 5. Day 1–5学习顺序

Day 1–5表示逻辑顺序，不是硬性日历。前一步未理解时可以跨天，不以文件数量衡量进度。

### Day 1 — Deep-case charter与selection logic

核心问题：

> **为什么选择Pack EoL connector handling作为第一个deep reference case？**

任务：

- 建立`Case Charter v0.1`；
- 固定EoL为primary process，DCR保留为adjacent unknown；
- 固定flow object、physical task、三类architecture和系统边界；
- 登记CATL/千寻直接披露及其证据限制；
- 建立Thomas要求的selection/explanation tree。

建议决策树：

```text
Why battery manufacturing?
→ Why Pack EoL?
→ Why connector and harness handling?
→ Why is this a robotic-system task?
→ Why compare architectures?
→ Why is humanoid/mobile dual-arm worth evaluating?
→ What evidence supports and limits the analysis?
```

最低结果：学生能够用两分钟解释为什么用B建立第一个方法原型，并说明B不等于CATL案例研究。

### Day 2 — Task cycle与responsibility map

核心问题：

> **一个测试connector从未连接到安全拔出，中间发生什么，各子系统分别负责什么？**

参考任务周期：

```text
Pack arrives and is identified
→ Pack positioned
→ Safe state / connection permission
→ Connector located
→ Harness grasped or supported
→ Connector aligned and inserted
→ Connection confirmed
→ Test permission
→ EoL test executed by test equipment
→ De-energized / safe release confirmed
→ Connector removed and harness returned
→ Result associated and Pack released
```

任务：

- 每一步标记`DIRECT / BASELINE / CROSS-INDUSTRY / INFERENCE / UNKNOWN`；
- 明确robot、test equipment、PLC/safety、MES和fixture责任；
- 只登记有来源或值得核实的failure modes；
- 不把KUKA battery assembly connector案例写成相同EoL工位。

最低结果：一张可演化为thesis figure的`Task + Responsibility Map`。

### Day 3 — Battery-specific task requirements

核心问题：

> **为什么这个任务不能简单等同于普通pick-and-place或“插一个插头”？**

只研究六类要求：

1. flexible-harness handling；
2. contact-rich connector insertion；
3. electrical / HV safety interface；
4. pack / connector variation与changeover；
5. connection-quality confirmation；
6. traceability与system integration。

每项回答：

```text
Evidence
→ Why it matters
→ Effect on robot task
→ Required capability
→ Current unknown
```

这里不先从humanoid属性出发。如果产品多样性、接口变化或高压状态没有直接证据，就保留`UNKNOWN`。

最低结果：一张`Requirement → Robot-task Effect → Required Capability`表。

### Day 4 — Architecture conditional-suitability comparison

核心问题：

> **面对Day 3的requirements，三类architecture分别在什么生产条件下更合理？**

比较：

1. dedicated connector/test-harness automation；
2. fixed industrial robot / fixed dual-arm robot；
3. humanoid / mobile dual-arm manipulator。

主要条件：

- product and connector variety；
- flexible-harness complexity；
- volume / takt；
- changeover frequency；
- fixed vs multi-station task；
- brownfield / human-oriented layout；
- safety and integration；
- quality mechanism；
- scalability；
- cost evidence availability与maturity。

结论只使用：

- `SUPPORTED`；
- `CONDITIONALLY SUITABLE`；
- `NOT SUPPORTED BY CURRENT EVIDENCE`；
- `UNKNOWN`。

不使用品牌排名、无证据权重或数字总分。可能形成但必须由证据检验的条件假设包括：

```text
low variety + high volume + fixed interface
→ dedicated automation may be favored

moderate variation + fixed workstation
→ fixed industrial robot may be attractive

high variation + multiple stations + legacy human-oriented layout
→ mobile dual-arm / humanoid becomes worth evaluating
```

最低结果：一张`Requirement / Production Condition → Architecture Suitability`矩阵，并能解释至少一个humanoid可能有价值和一个传统方案更合理的条件。

### Day 5 — Deep-case synthesis与Method Framework v0.1

核心问题：

> **Pack EoL案例是否已经帮助我们形成一套可迁移到其他battery-manufacturing tasks的分析方法？**

任务：

1. 用`Task → Requirements → Baseline → Capabilities → Suitability conditions`总结deep case；
2. 提取`Task–Requirement–Capability–Suitability Framework v0.1`：
   - manufacturing-task identification；
   - task / production-requirement extraction；
   - existing automation baseline；
   - robotic-capability mapping；
   - conditional-suitability assessment；
   - implementation-barrier analysis；
   - scenario-based evaluation；
3. 评估哪些框架字段能够迁移、哪些只属于Pack EoL；
4. 决定Week 07是否把框架应用到`cell recognition / grasping / loading`；
5. 如果B的humanoid直接证据仍弱，缩小主张或把humanoid标成future scenario，而不是宣布整条论文路线失败。

最低结果：`Framework v0.1 + deep-case synthesis memo + Week 07单一入口`。

---

## 6. Week 06最低完成目标

完成以下四项即为合格：

1. **Deep Case Charter v0.1 + selection/explanation tree**；
2. **Pack EoL connector-handling Task + Responsibility Map**；
3. **Requirement → Capability → Architecture conditional-suitability matrix**；
4. **Task–Requirement–Capability–Suitability Framework v0.1**。

本周不以文献数量、新闻数量、网页数量、讲义长度、代码或实验数据衡量成功。学生是否能独立解释分析链条，是首要标准。

---

## 7. 有余力再做

最低目标完成后，只选一项：

- 用一种透明的Pack/connector variation假设建立scenario examples，但不得冒充CATL现场；
- 为可选专家review制作一页任务图和事实问题；
- 根据Thomas提供的最新模板起草registration abstract v0.1；
- 轻量检查Candidate A的直接证据是否足以作为Week 07入口，不开始第二个deep dive。

---

## 8. Week 06结束时怎样判断进展

Week 06不再只做`KEEP / ABANDON`二元判断。应记录：

| 决定 | 含义 |
| --- | --- |
| `DEEP CASE CONTINUES` | B足以继续支撑方法与场景分析 |
| `NARROW CLAIM` | 只保留证据能够支撑的connector/harness任务或architecture comparison |
| `HUMANOID AS FUTURE SCENARIO` | humanoid部署证据不足，但任务与架构比较仍有研究价值 |
| `FRAMEWORK TRANSFER READY` | 方法字段足够清楚，可进入一个adjacent case |
| `RETURN TO CASE MAP` | 连battery-specific task或robotics decision都无法建立时才返回候选地图 |

停止扩大B的条件：

- 无法确认connector/harness handling是直接battery-manufacturing task；
- battery-specific requirements没有改变任何robot task或implementation decision；
- 比较始终停留在“humanoid更灵活/industrial robot更稳定”的口号；
- 证据组合无法支撑目标主张，且缩小主张后仍无可信分析内容。

缺少专家、现场或实验本身不再自动触发放弃；应先判断文献、工业baseline、跨行业证据和scenario analysis能否形成可信组合。

---

## 9. 学生本周应能回答

1. 为什么Pack EoL connector handling是一个robotic-system application，而不是电气测试设备研究？
2. Robot、test equipment、PLC/safety、MES和fixture分别负责什么？
3. Flexible harness、contact-rich insertion和安全互锁怎样改变robot task？
4. 什么生产条件可能支持dedicated automation、fixed robot或humanoid/mobile dual-arm？
5. 哪些结论来自直接企业披露，哪些来自设备baseline或跨行业证据，哪些仍是unknown？
6. 为什么company news不等于技术验证，资料少也不等于research gap？
7. `Task–Requirement–Capability–Suitability Framework`如何迁移到cell loading等其他case？
8. 为什么偏综述的论文仍需要方法，而不一定需要新算法或仿真？

---

## 10. 下次向Thomas汇报的最小结构

只汇报五件事：

1. **My selection logic**：为什么用Pack EoL作为第一个deep reference case；
2. **What the task actually is**：任务周期与系统责任；
3. **What requirements drive robot selection**：battery-specific task requirements；
4. **Under which conditions each architecture fits**：条件性比较，而非humanoid优越性；
5. **The reusable method and next case**：Framework v0.1及是否迁移到cell loading。

可以请Thomas审查：

- 这种`deep case → transferable framework → adjacent cases → cross-case comparison`是否符合他的预期；
- 当前Pack scope和registration abstract如何准确表述；
- 是否有可选的Pack testing / automation expert可增强证据。

不要再让Thomas替学生从A/B/C中选题，也不要把专家入口说成论文成立的唯一前提。

---

## 11. Registration abstract并行任务

Thomas提出可开始准备约1–2页/张的abstract。根据仓库内PEM参考，它应是compact research proposal，并可能包括德英题目、motivation/problem、objective、unresolved problem、candidate RQ、method、work packages、desired results和structure。

但本地PEM材料包含2022/2025版本。正式注册前必须等待Thomas最新信息，并向Thomas/PEM/ZPA确认：

- 当前模板与语言；
- 实际篇幅与格式；
- Faculty 4/Faculty 6流程；
- 注册日期、签字和提交要求；
- 当前引用与格式要求。

Week 06可以起草working draft，但不得为了注册提前把working hypothesis写成事实，也不得在未核验前正式提交。
