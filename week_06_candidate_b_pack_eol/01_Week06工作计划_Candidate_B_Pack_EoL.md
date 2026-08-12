# Week 06工作计划：Candidate B——Pack EoL/DCR柔性测试接插件处理

> 制定依据：2026-08-12 Thomas组会录屏、`abschlussarbeiten_42444.pdf`、`docs/research_direction_guardrails.md`、`docs/collaboration_and_pacing.md`和Week 04–05研究成果。
> 当前状态：**Thomas认可继续深化的暂定单案例；不是最终题目、最终research gap、最终RQ或永久case lock。**
> Production level：**battery-pack manufacturing**。Thomas已表示Pack EoL testing方向可以，但正式注册边界仍须在abstract中明确。

---

## 0. 一页结论

Week 06不再同时推进A/B/C，也不返回formation handover。只推进一个中心问题：

> **在battery-pack EoL/DCR测试中，柔性测试接插件处理需要哪些任务能力和battery-specific constraints；这些要求在什么条件下支持、条件性支持或不支持humanoid/mobile dual-arm system，而不是专用自动化或固定工业机器人？**

本周不是证明humanoid更好，而是完成一份可解释的Candidate B可行性判断：

```text
Pack EoL/DCR制造任务
→ connector/线束处理动作与责任边界
→ battery-specific safety、quality和integration要求
→ dedicated / fixed robot / humanoid-mobile方案比较
→ 跨行业证据能迁移到哪一步
→ validation route与case decision
```

最低产出是一份轻量`Candidate B feasibility pack`，包含任务边界、证据矩阵、要求—能力比较和一页决策说明。注册abstract是并行行政任务，不应挤掉本周唯一研究问题。

---

## 1. 为什么现在研究它

### 来自Thomas的最新反馈

- Pack EoL testing方向可以；
- 选题最终由学生决定，必须能够解释自己的选择；
- 直接humanoid资料少时，可以从其他行业迁移细节；
- 可以总结humanoid属性，判断适用和不适用的场景；
- 新闻报道不足以承担技术结论；
- 学生提出继续Candidate B和补充详细文献，Thomas认可该计划。

### 来自原始任务PDF

Thomas的原始任务要求：

```text
制造工艺与要求
→ 合适机器人应用
→ 技术与经济评价
→ 具体应用场景
→ 实施建议和未来趋势
```

Candidate B能够承载这一结构，但前提是研究对象是**机器人系统实施决策**，而不是千寻“小墨”的企业新闻，也不是测试设备内部电气测量原理。

### 来自Week 04–05的教训

- 直接企业披露不等于独立验证；
- 一项来源没写，不等于领域不存在；
- 不同来源不能拼成同一工厂；
- battery requirement必须真正改变robot task或robot–equipment integration decision；
- 没有task、baseline和validation route时，不建模、不算ROI、不宣布gap。

---

## 2. 暂定case boundary

### 2.1 Included

| 字段 | Week 06暂定边界 |
| --- | --- |
| Production level | battery-pack manufacturing |
| Process | Pack EoL和/或DCR测试工位；两者关系待原始证据确认 |
| Flow object | 测试接插件、柔性线束和battery-pack test interface |
| Robot task | 找到接口、处理线束、对准、插入、确认连接、测试后拔出、异常上报/安全退出 |
| Main technology under evaluation | wheeled humanoid或mobile dual-arm manipulator |
| Direct function baseline | dedicated automatic connector/test-harness mechanism |
| Robotics baseline | fixed industrial robot或dual-arm industrial robot；cobot/mobile manipulator按证据纳入 |
| System interfaces | test equipment、PLC/safety interlock、MES/traceability、fixture/station、human intervention |

### 2.2 Responsibility boundary

```text
Robot / automation system
  → physical connector and flexible-harness handling

Test equipment
  → electrical measurement and test execution

PLC / safety system
  → de-energized state, interlock, permission and safe stop

MES / traceability
  → product identity, recipe and result association
```

该责任划分当前是分析框架。CATL/千寻现场的实际责任必须由同一case直接资料或专家确认。

### 2.3 Explicitly excluded this week

- 不深挖Candidate A或C；A只保留为失败后的backup；
- 不返回B2 formation stacker-crane/PLC/contact细节；
- 不研究测试设备内部测量算法、电池电气模型或高压测试标准全文；
- 不研究humanoid步态、全身控制、foundation model或抓取算法开发；
- 不建立产线仿真、节拍优化或ROI模型；
- 不给架构打无证据的数字分数；
- 不把公司公布的性能、规模、节拍和成功率当作独立事实。

---

## 3. Week 06必须牢记的注意事项

### 3.1 Thomas认可方向，不等于Thomas替我们完成选择

本周必须建立一棵`decision/explanation tree`，解释：

```text
为什么选择B
→ 为什么是pack EoL/DCR
→ 为什么connector handling具有机器人研究价值
→ 为什么需要比较humanoid与其他架构
→ 需要什么证据才能继续
→ 哪个结果会让B退出
```

### 3.2 “资料少”只能成为检索信号

Thomas认为资料少可能意味着研究空间，但项目不得把它直接写成gap。每个缺口必须检查：

- 是否只是企业保密或未公开；
- 是否已有专用自动化解决；
- 是否在相邻行业已有成熟方法；
- 是否能够转移到battery context；
- 是否能用专家、设备资料、实验或场景评价验证。

### 3.3 跨行业迁移必须经过等价性检查

每条transfer evidence至少记录：

| 字段 | 必须回答 |
| --- | --- |
| Source task | 原行业究竟处理什么对象和接口？ |
| Relevant attribute | 证明了视觉、线束处理、force control、插接还是移动？ |
| Battery equivalence | 与Pack EoL/DCR任务相同的物理或系统要求是什么？ |
| Non-equivalence | 高压安全、接口几何、节拍、环境或验证阶段哪里不同？ |
| Allowed inference | 可以迁移到能力/方法/评价维度的哪一层？ |
| Forbidden inference | 哪些性能数字和部署结论不能迁移？ |

### 3.4 企业新闻只能证明“企业声称”

千寻/CATL/SAIC/Galbot等一手披露可以证明任务和部署说法的存在，但不能独立证明：

- 插接成功率和长期可靠性；
- 节拍和产能；
- 经济优势；
- 相对于工业机器人的优越性；
- “规模化部署”的具体数量和持续运行表现。

### 3.5 结论使用条件语言

优先使用：

- `supported under the following conditions`；
- `conditionally suitable`；
- `not supported by the current evidence`；
- `unknown / requires validation`。

避免使用没有足够证据的绝对表达：

- `humanoid is better`；
- `humanoid cannot be used`；
- `the task is impossible for industrial robots`；
- `this is an established research gap`。

### 3.6 图和专利必须让听众看得懂

任何`27 / 28 / device 3`或专利编号必须同时给出：原图、来源、图号/段落、设备名称和高亮边界。可编辑重绘图可以用于解释，但不能替代原始证据。

### 3.7 注册任务与研究判断分开

Thomas要求准备abstract，但abstract不能为了注册而提前把working hypothesis写成事实。正式注册前必须核对Thomas即将提供的最新信息以及PEM/RWTH/ZPA当前流程。

---

## 4. Day 1–5学习顺序

Day 1–5表示逻辑顺序，不是硬性日历。前一步没有回答清楚时，不为凑五天进入下一步。

### Day 1 — 冻结暂定边界与决策树

核心问题：

> 我们选择B，究竟是在研究什么机器人系统决定？

任务：

- 建立Candidate B `case charter v0.1`；
- 固定production level、flow object、task、actor、baseline和unknown；
- 画出Thomas要求的selection/explanation tree；
- 将CATL/千寻直接披露逐条登记为`DIRECT COMPANY DISCLOSURE`；
- 寻找原始完整视频、图或技术说明，并记录“找到/未找到”，不把缺失写成gap。

最低结果：能够用两分钟解释为什么选B，以及哪个证据会让B退出。

### Day 2 — 重建任务周期与责任边界

核心问题：

> 一个测试connector从未连接到安全拔出，哪些步骤由机器人负责，哪些由测试设备、PLC和MES负责？

任务：

- 建立最小task sequence；
- 逐步标记`SOURCE-EXPLICIT / ENGINEERING REFERENCE / INFERENCE / UNKNOWN`；
- 区分定位、线束处理、插接、连接确认、电气测试、断电许可和拔出；
- 列出可能的failure modes，但只保留有来源或需要专家确认的项；
- 不把KUKA assembly connector案例写成同一EoL/DCR工位。

最低结果：一张robot/test-equipment/PLC/MES responsibility map。

### Day 3 — Humanoid属性与跨行业证据迁移

核心问题：

> 哪些humanoid/mobile-manipulation能力与B直接相关，哪些只是一般机器人宣传？

优先属性：

- 视觉定位和来料位置变化；
- 柔性线束抓取、支撑和形变管理；
- contact-rich insertion、force/torque sensing和连接状态确认；
- 双臂协同或一臂理线、一臂插接；
- 工位间移动、多型号changeover和既有人工作业空间复用；
- 安全互锁、失效退出、traceability和人工接管。

证据顺序：

1. 同行评审或工程论文；
2. 原始工业技术资料/完整任务视频；
3. 设备商或机器人厂商案例；
4. 新闻转载仅作线索。

最低结果：一张`source task → transferable attribute → battery boundary`证据表。

### Day 4 — 三类架构的条件性比较

核心问题：

> 在什么任务和生产条件下，各架构更有理由进入候选？

比较对象：

1. dedicated connector/test-harness automation；
2. fixed industrial robot或dual-arm robot；
3. humanoid/mobile dual-arm manipulator。

沿用Thomas原始PDF维度：

- automation potential；
- cost及所需成本证据；
- quality impact mechanism；
- scalability。

补充本case必要维度：

- HV safety/interlock；
- flexible-harness handling；
- product-variant/changeover；
- station integration与占地；
- connector protection和异常恢复；
- evidence maturity与validation access。

本周只使用`SUPPORTED / CONDITIONAL / NOT SUPPORTED / UNKNOWN`，不设置无依据权重或数字评分。

最低结果：一张requirement-to-architecture matrix，并能解释至少一个“humanoid可能有价值”和一个“专用/固定自动化可能更合理”的条件。

### Day 5 — Case decision、validation route与abstract入口

核心问题：

> Candidate B现在是否具备继续形成正式case charter和注册abstract的证据条件？

任务：

- 输出`KEEP / NARROW / HOLD AS FUTURE TREND / RETURN TO A`判断；
- 写出最强支持证据、最强反例、核心unknown和退出条件；
- 形成5–8个只针对事实缺口的专家/设备问题；
- 明确一个现实validation route及备选route；
- 收到Thomas的注册信息后，按最新要求制作约1–2页working abstract；
- abstract内容至少覆盖题目、motivation/problem、objective、unresolved problem、candidate RQ、method、work packages、desired results和proposed structure。

最低结果：一页Candidate B decision memo和一条可执行validation route。注册abstract不因资料未到而仓促定稿。

---

## 5. 本周最低完成目标

Week 06达到以下四项即可视为合格：

1. 一个能让学生独立解释的Candidate B边界和selection tree；
2. 一张带证据状态的connector-handling task/responsibility map；
3. 一张humanoid属性迁移与三类架构条件比较表；
4. 一个透明的case decision：继续什么、仍缺什么、怎样验证、什么情况下退出。

不以文献数量或文件长度衡量成功。少量强来源、清楚的迁移逻辑和一个现实验证入口，比收集很多新闻更重要。

---

## 6. 有余力再做

最低目标完成后，只选择一项：

- 针对一种明确的connector/pack format画第一版具体application scenario；
- 为专家访谈制作一页图和结构化问题；
- 建立注册abstract v0.1；
- 检查Candidate A是否仍是可靠backup，但不开展第二个deep dive。

---

## 7. Case B进入正式锁定的最低证据

| Evidence block | Week 06要求 |
| --- | --- |
| Direct battery task | 至少一个一手来源能明确支持Pack EoL/DCR和connector/线束处理任务 |
| Conventional baseline | 至少一个专用自动化或固定工业机器人资料支持可比较的connector handling功能，并标明是否同工序 |
| Task-capability evidence | 至少一个同行评审或工程来源支持关键能力，如柔性线束处理、插接/力控或连接确认 |
| Humanoid/mobile evidence | 至少一个一手工业或技术来源支持相关属性；若来自其他行业，完成迁移边界表 |
| Validation route | 明确可联系的专家/站点/设备资料，或一个不依赖CATL内部数据的可执行验证方案 |

前四项不能形成可信证据链，或validation route仍完全不存在时，不得宣布final gap/RQ或正式永久锁定B。

---

## 8. 退出与变更条件

出现以下任一情况，Week 06应停止继续扩大B：

1. 无法确认直接案例的具体robot task和connector-handling边界；
2. battery-specific requirements没有改变任何robot task或implementation decision；
3. 所有关键能力只来自营销文字，无法建立可迁移的技术证据；
4. 比较始终停留在“humanoid更灵活/工业机器人更稳定”的泛化口号；
5. 完成预定检索和联系路径后仍无credible validation route。

可能决定：

- `KEEP`：B通过证据与验证门，进入正式case charter；
- `NARROW`：只保留一项明确任务，例如柔性测试connector插拔与连接确认；
- `HOLD AS FUTURE TREND`：humanoid证据不足，把它降为future scenario，主研究转为架构比较；
- `RETURN TO A`：B任务/验证不可行时，按已定义规则返回A，不自动跳C或AGV仿真。

---

## 9. 学生本周应能用自己的话回答

1. Pack EoL/DCR工位在测试什么，机器人为什么只负责物理连接而不是电气测量？
2. 柔性线束和测试connector为什么可能改变机器人感知、抓取、力控和确认要求？
3. 什么条件下专用自动化或固定工业机器人比humanoid更合理？
4. 什么条件下移动、双臂和既有人工工位复用可能使humanoid/mobile manipulator值得评价？
5. 哪些结论来自CATL/千寻直接披露，哪些来自相邻行业，哪些仍是未知？
6. 为什么“公开信息少”不等于已经找到research gap？
7. 哪个证据或验证失败会让我们放弃或降级Candidate B？

---

## 10. 下次向Thomas汇报的最小结构

不需要再次展示宽泛application map。建议只汇报四件事：

1. **My decision and explanation tree**：为什么暂选B；
2. **What the task actually is**：connector handling的动作和责任边界；
3. **Where humanoid may or may not fit**：三类架构的条件比较和证据边界；
4. **What I need to validate**：一个具体专家/站点/资料入口，以及注册abstract状态。

建议只向Thomas确认：

- 他即将提供的注册abstract模板、日期和流程；
- 是否能介绍Pack testing、automation integration或connector-handling相关专家/设备；
- 当前“humanoid为重点评价对象＋专用/固定机器人为baseline”的比较结构是否符合预期。

不再把“A/B/C选哪一个”原样交回Thomas，因为本次会议已明确要求学生作出并解释自己的决定。

---

## 11. 注册abstract并行任务

收到Thomas的新信息后，按最新要求准备working draft。仓库内的PEM资料显示abstract通常需要约1.5页，并包含德英题目、motivation、objective、gap/unresolved problem、RQ、method、work packages、desired results和structure；但该资料包含2022/2025版本。

因此：

> **先起草，后按Thomas/PEM/ZPA最新模板、截止时间、院系流程和引用要求核验；未经核验不进行正式注册提交。**
