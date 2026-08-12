# Week 04–05 Research Transition and Case-Selection Brief

> 用途：后续组会汇报、PPT制作和case lock的共同母稿
> 整理日期：2026-08-12
> 当前状态：**case-selection checkpoint；尚未形成最终题目、最终research gap或最终research question**
> 最高研究方向依据：[Thomas原始课题说明](../abschlussarbeiten_42444.pdf)
> 内部护栏：[AGENTS.md](../AGENTS.md) · [research_direction_guardrails.md](../docs/research_direction_guardrails.md)

---

## 0. 一页结论

Thomas给出的working title是：

> **Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies**

Week 04–05没有“白做”，但完成的是一次必要的**候选压力测试与退出决策**：

1. Week 04重建了cell-finishing carrier flow的state of the art，并主动寻找反例；
2. Week 05用一个具体formation-loading专利架构检查运行层handover是否能够形成battery-specific且robotics-relevant的问题；
3. 审计结果显示，`入库机27 → 堆垛机28 → 化成装置3`只是有证据的固定自动化搬运baseline；没有直接证据证明formation-specific condition改变了堆垛机任务；
4. 因此旧formation-handover候选退出论文候选路径，但作为fixed-automation baseline和方法论反例保留；
5. 研究返回Thomas原始的机器人应用主线，并结合Thomas近期对humanoid的关注，形成三个module/pack制造候选；
6. 当前建议是：

```text
Primary, conditional:  B — Pack EoL/DCR测试接插件柔性插拔
Strong backup:         A — 电芯识别、抓取与模组/Pack上料
Exploratory:           C — 模组/Pack多工位搬运与拣选
```

这里的B不是“研究千寻智能宣传案例”，而是研究一个具体制造任务：

> **多品种电池PACK EoL/DCR测试中的柔性测试接插件处理，并比较专用自动化、固定工业机器人和轮式人形/移动双臂机器人三种实施架构。**

在正式锁定B之前，Thomas需要确认module/pack scope；项目还需补足工序视频、设备资料或专家验证入口。

---

## 1. 研究方向判据

### 1.1 Thomas原始任务要求

Thomas的原始PDF要求研究：

```text
current manufacturing processes and requirements
→ suitable robotics applications
→ technical and economic assessment
→ concrete application scenarios
→ future trends and industrial implementation recommendations
```

PDF明确列出的机器人类型包括：

- industrial robots；
- collaborative robots；
- mobile systems。

明确列出的应用包括：

- material handling；
- automated inspection；
- flexible assembly；
- intralogistics。

明确列出的评价维度包括：

- automation potential；
- cost；
- quality impact；
- scalability。

因此，候选不能只证明“电池工厂里有一台设备”，而应建立：

```text
具体battery-manufacturing problem
→ 明确robot actor与task
→ battery requirement怎样改变robot task
→ 需要比较或决定什么系统架构
→ 如何验证与实施
```

### 1.2 Scope仍需Thomas确认

PDF标题使用`Battery Manufacturing`，任务段落使用`along the battery cell production value chain`。当前最强humanoid案例位于module/pack制造。因此：

> module/pack是可以交给Thomas选择的合法候选范围，但在Thomas确认前不能冒充已经锁定的正式scope。

### 1.3 证据标签

后续PPT和论文材料统一区分：

| 标签 | 含义 |
| --- | --- |
| `PEER-REVIEWED` | 同行评审研究；仍需注意研究配置和外推边界 |
| `DIRECT COMPANY DISCLOSURE` | 企业直接披露的任务或部署；可以证明企业作出该声明，不能自动证明性能和成熟度 |
| `ENGINEERING BASELINE` | 设备商、集成商或相邻案例公开的可比较技术架构 |
| `ENGINEERING INFERENCE` | 根据已知系统架构作出的合理推断；不是当前case的直接事实 |
| `UNKNOWN` | 来源未公开或尚未核实 |

---

## 2. Week 04做了什么

### 2.1 Week 04中心问题

> 电芯及其载具在cell finishing中运输的现有方式是什么？现有证据能够支持哪些电池场景特有的问题区？

Week 04响应了Thomas当时的反馈顺序：

```text
找实例
→ 写清state of the art
→ 识别problem areas
→ 主动寻找反例
→ 再判断是否存在candidate gap
```

### 2.2 Week 04实际工作

| Day | 完成内容 | 对研究决策的作用 |
| --- | --- | --- |
| Day 1 | 建立direct / adjacent / false-match证据分类，定义flow object、工序、运输方案、接口和验证字段 | 防止“同时出现battery和AGV”就被当成直接案例 |
| Day 2 | 重建人工与全自动tray-based reference configurations | 证明fully automated不等于AGV，运输技术不能靠想象补充 |
| Day 3 | 精读Deng等强反例，检查配置、physical interfaces和intralogistics transitions | 推翻“cell-finishing研究完全没有考虑物流/接口”的宽泛gap |
| Day 4 | 按任务而非按热点检查AGV与humanoid边界 | 没有证据支持humanoid进入formation carrier flow，也不能先做泛化AGV-vs-humanoid比较 |
| Day 5 | 综合state of the art、候选问题、最强反例和验证缺口 | 保留最多两个待验证问题，不宣布最终gap，不进入simulation |

### 2.3 Week 04关键证据与结论

| 来源 | 直接支持 | 不能支持 |
| --- | --- | --- |
| Wanner et al. (2022) | cell-finishing tray production flow与DES | 具体AGV、handover机构和异常流 |
| Schomburg et al. (2024) | formation product carrier可能承担工艺接触功能 | 完整物流路线、移动主体和交接时序 |
| FFB Fab (2023) | 人工与fully automated tray-based配置、continuous traceability规划 | fully automated所采用的具体运输技术 |
| Deng et al. (2026) | 配置模型、physical interfaces、formation tray夹具/施压、部分intralogistics transitions | 完整运行层handover、队列、实时状态和异常恢复 |
| Lee et al. (2024) | rechargeable-battery production中的真实AGV任务记录与运行策略研究 | AGV服务formation tray flow或具体cell-finishing语义 |

Week 04建立的主要认识：

- cell-finishing已经存在tray/product-carrier、存储和部分intralogistics研究；
- carrier不一定只是被动物流容器，某些配置还承担接触、fixture或受控施压功能；
- 已有研究并未完全忽略接口，因此不能把“首次连接cell finishing与物流”作为gap；
- 真实目标系统是否使用AGV、任务怎样交接、发生什么异常，仍未被当前证据确认；
- 没有真实任务、时间、buffer和验证数据时，不应开始fleet sizing、dispatching或SimPy。

### 2.4 Week 04留下的旧候选

为避免与当前A/B/C短名单混淆，以下统一称为`W4-A`和`W4-B`：

#### W4-A — Operation-level process-aware carrier handover

设想：在一个具体formation-loading接口中，研究移载、定位、锁定、接触、acceptance、失败与恢复。

状态：`CANDIDATE—NOT ESTABLISHED GAP`。

最强反例：Deng已经研究physical interfaces和intralogistics transitions；Schomburg已经支持carrier contact功能。因此不能声称接口从未被研究，只能继续检查是否存在未被设备内部消化的robotics-relevant运行问题。

#### W4-B — Exception-triggered carrier flow

设想：研究异常电芯、隔离、热事件等如何改变载具流。

状态：低优先级、验证困难。

原因：安全SOP、设备逻辑和异常数据可能不公开；检测存在不等于运输处置形成了可研究问题；高风险验证容易超出硕士论文可行范围。

### 2.5 Week 04阶段决定

> `CONTINUE LEARNING`：用一个具体formation-loading公开架构检查W4-A，而不是开始AGV仿真或宣布research gap。

Week 04详细材料：

- [Week 04工作计划](../week_04_state_of_art_audit/01_Week04工作计划_基于Thomas反馈.md)
- [Week 04 Day 5综合讲义](../week_04_state_of_art_audit/day5_synthesis_candidate_gap_and_decision_learning_guide.html)

---

## 3. Week 05做了什么

### 3.1 Week 05中心问题

> 在一个有来源的formation-loading配置中，是否存在一项直接支持的formation-specific condition，会改变可辨认的机器人任务或具体robot–equipment integration decision？

Week 05不是研究堆垛机本体，而是用具体架构检验W4-A能否通过robotics-relevance gate。

### 3.2 Week 05 reference architecture

主参考来源为公开专利申请`CN118970237A`。来源明确支持：

```text
主输送机构1
→ 第五移载装置25
→ 第三输送部26
→ 入库机27
→ 堆垛机28
→ 化成装置3
```

被重点审计的最小边界B2是：

```text
Flow object:         承载若干电池的承载装置/电池托盘
Source equipment:    入库机27
Transfer actor:      堆垛机28
Destination:         化成装置3
Exact pickup port:   UNKNOWN
Receiving port:      UNKNOWN
Final contact:       UNKNOWN
Acceptance/start:    UNKNOWN
```

B2的正确身份始终是：

> **non-AGV fixed-automation reference/baseline**

它不是AGV案例，也不是论文题目。

### 3.3 Week 05实际学习结果

1. 区分了“formation area”“化成装置”和具体receiving/process position；
2. 区分了区域运输、固定入库、最终上料和设备内部工艺接入；
3. 确认Architecture B中的B2由堆垛机执行，不能把AGV补画进来源；
4. 审计position、locking、contact、identity、readiness由谁负责，以及它们是否改变robot task；
5. 学生能够识别运输需求与工艺需求的区别，并指出精定位/contact更可能由formation equipment内部完成；
6. 识别到继续研究PLC、position、contact和acceptance只会深化电池设备接口，并不会自动恢复Thomas所需的机器人应用主线。

### 3.4 为什么旧formation-handover候选退出

| Gate | 审计结果 |
| --- | --- |
| Direct battery-manufacturing evidence | `YES`：属于formation-loading架构 |
| Identifiable robotic-system task | `NO/INSUFFICIENT`：直接actor是固定堆垛机，任务只是载具转移 |
| Battery-specific effect on actor task | `NO DIRECT EVIDENCE`：扫码只确认身份；locking/contact/precision未在同一case中证明改变堆垛机任务 |
| Meaningful implementation decision | `INSUFFICIENT`：没有建立超出普通固定搬运的机器人系统选型或集成问题 |
| Practical consequence | `UNKNOWN`：没有直接证据说明候选状态失败怎样影响该机器人任务 |
| Credible validation route | `NOT ESTABLISHED`：尚无具体设备、专家或现场接口数据 |

最终决定：

> **ABANDON AS THESIS CANDIDATE / RETAIN AS FIXED-AUTOMATION BASELINE / RETURN TO ROBOTICS APPLICATION MAP**

这次退出不是因为“搬运技术不高级”，而是因为没有证据证明电池工艺要求真正改变了一个机器人系统任务。继续细化会跑向formation设备或PLC接口，与Thomas的原始机器人系统题目逐渐脱离。

Week 05详细材料：

- [Week 05工作计划](01_Week05工作计划_Formation_Carrier_Handover.md)
- [Week 05 case dossier](02_Week05_case_dossier.md)

---

## 4. 为什么现在更换候选case

### 4.1 触发原因

```text
Week 03：用carrier flow学习工艺—物流—控制关系
→ Week 04：发现已有配置研究和强反例，宽泛gap不能成立
→ Week 05：用具体专利架构检验运行层handover
→ Day 3审计：没有formation-specific condition直接改变堆垛机任务
→ 学生指出研究正滑向电池设备接口，而非机器人系统应用
→ 返回Thomas原始PDF及其humanoid反馈
→ 建立有明确robot actor和battery task的新短名单
```

### 4.2 更换不是因为新技术更热门

候选变化依据是：

- 旧case未通过battery-specific effect与robotics-relevance gate；
- 旧case缺少现实验证入口；
- 新case具有直接机器人actor、明确制造任务和可比较baseline；
- Thomas近期建议更多关注humanoid，但并未要求预设humanoid优于工业机器人；
- Thomas原始PDF允许选择工业机器人、协作机器人、移动系统及未来趋势，并进行技术经济评价。

### 4.3 Week 04–05仍然怎样服务新方向

Week 04–05留下了可复用的方法：

- 不把供应商宣传当作独立验证；
- 不把另一来源的功能拼入当前case；
- 区分process equipment、fixed automation和robotic actor；
- 每个候选必须有具体对象、动作、接口、约束、baseline和validation route；
- `unknown in literature`不等于industrial problem或research gap；
- 候选失败时保留baseline与证据链，不靠文件连续性强行继续。

---

## 5. 当前三个候选的同口径证据卡

## 5.1 Shortlist A — 电芯识别、抓取与模组/Pack上料

### Case definition

| 字段 | 当前内容 |
| --- | --- |
| Production level | module/pack manufacturing；正式scope待Thomas确认 |
| Flow object | 单体电芯；具体format尚未公开确认 |
| Exact robot task | 识别来料、规划抓取路径、抓取电芯并上料 |
| Robot actor | 上汽通用/智元轮式人形机器人“能仔1号” |
| Direct industrial evidence | 上汽集团官方称其进入别克至境E7电池量产线，承担电芯抓取与上料 |
| Battery-specific requirements | 电芯几何/方向、带电操作风险、避免损伤、定位与装配要求；具体哪项改变robot task仍需补证 |
| Comparison baseline | 专用上料机、视觉引导固定工业机器人、人工 |
| Possible thesis method | 任务需求分解＋系统架构比较＋不同来料变异/产品组合下的application scenarios＋技术经济评价 |
| Validation route | 原始工序视频、上汽演讲/工程资料、module/pack设备专家、传统上料方案资料 |

### Evidence boundary

`DIRECT COMPANY DISCLOSURE`：上汽官方明确支持量产线、电芯抓取、上料、来料识别和路径规划。

`UNKNOWN / UNVERIFIED`：

- 电芯从什么容器取出；
- 上料的具体destination和接口；
- 是否存在精密插入、极性/方向确认和失败恢复；
- 企业公布的精度、节拍、占地和量产表现是否有独立验证；
- 当前尚未找到可核验完整周期的上汽原始工序视频。

Sorting、matching和kitting不是上汽案例的source-explicit事实，不得写入case title。

### Current judgment

> **STRONG BACKUP**：直接企业任务证据相对较强，但如果无法证明上料接口如何受到电芯要求影响，可能退化为一般vision-guided pick-and-place。

主要来源：

- 上汽集团，2026-03-27：[上汽集团率先实现人形机器人量产线应用](https://www.saicmotor.com/chinese/xwzx/xwk/2026/64051.shtml)

---

## 5.2 Shortlist B — Pack EoL/DCR测试接插件柔性插拔

### Case definition

| 字段 | 当前内容 |
| --- | --- |
| Production level | battery-pack manufacturing；正式scope待Thomas确认 |
| Flow object | EoL/DCR高/低压测试接插件与柔性线束；具体CATL connector geometry未公开 |
| Exact robot task | 定位测试接口、处理柔性线束、对准/插入、确认连接、测试后拔出、异常上报 |
| Robot actor | CATL/千寻智能轮式人形/移动双臂机器人“小墨” |
| Direct industrial evidence | 千寻官方称其部署于CATL中州基地PACK线EoL/DCR工序，处理测试接插件并检查线束连接状态 |
| Battery-specific requirements | 高压安全与互锁、柔性线束、connector防损伤、连接可靠性、多型号/小批量、接口位置变化、EoL/DCR节拍与traceability |
| Comparison baseline | 专用自动插接/test harness adapter；固定工业机器人柔性connector handling；人工 |
| Possible thesis method | 工序/任务分解＋三种架构的技术经济比较＋产品组合与既有工位条件下的application scenarios＋实施与验证框架 |
| Validation route | 完整工序视频；EoL/DCR设备资料；PACK测试/自动化专家；PEM/FFB可用站点；不依赖CATL内部数据的场景评价或实验 |

### Likely industrial task sequence

以下是基于公开PACK测试线的`ENGINEERING REFERENCE`，不是CATL现场已验证时序：

```text
PACK进入测试工位
→ 定位
→ 扫码/调用产品测试程序
→ 无电状态下插接测试线束
→ 连接与安全互锁确认
→ 测试柜执行EoL或DCR测试
→ 测试结果上传MES
→ 断电/安全确认
→ 拔出线束
→ PACK流转或进入rework
```

机器人合理的责任是物理连接、解除连接和状态检查；测试设备负责电气测量，PLC/安全系统负责互锁，MES负责recipe与traceability。

### Evidence boundary

`DIRECT COMPANY DISCLOSURE`：千寻官方明确支持EoL/DCR、高压测试插头、柔性线束处理、位置变化适应和连接状态检查。

`DIRECT VISUAL EVIDENCE—LIMITED`：官方页面只有静态图；唯一现场图显示轮式人形机器人在PACK工位旁操作线束，但看不清connector、port和完整插拔周期。

`UNKNOWN / UNVERIFIED`：

- CATL现场完整工序和安全时序；
- connector属于高压、低压还是一体化测试接口；
- 一台机器人是否跨EoL/DCR工位移动；
- 插接成功率、节拍、单日工作量和部署数量的独立验证；
- 当前尚未找到千寻/CATL发布的完整连续工序视频。

### Comparison architecture

| Architecture | 当前直接作用 | 证据边界 |
| --- | --- | --- |
| Dedicated automation | RePower等公开了定位、自动插接、扫码、测试、MES和流转的PACK测试线 | 设备商方案；不代表CATL现场 |
| Fixed industrial robots | KUKA双工业机器人处理高压电池包柔性plug-in module connectors | 技术邻近baseline；属于battery-pack assembly，不是同一EoL/DCR站 |
| Wheeled humanoid/mobile manipulator | 千寻称可应对来料位置/插接点变化并处理柔性线束 | 企业披露；实际性能和经济性未独立验证 |

### Current judgment

> **CONDITIONAL PRIMARY**：三个候选中具有最清楚的battery-specific task、最强humanoid特征和最完整的架构比较空间；但不能把CATL/千寻宣传直接当作实证结果。

推荐研究表述：

> **Comparative assessment and implementation strategy for flexible robotic test-connector handling in multi-variant battery-pack EoL/DCR testing.**

不推荐表述：

> Study of Xiaomo in CATL.

主要来源：

- 千寻智能：[A World First! Embodied AI Robots Achieve Large-Scale Deployment in CATL Battery Production Line](https://www.spirit-ai.com/en/news/23)
- 北京国际科技创新中心转载：[全球首条！北京人形具身智能机器人，在这条产线规模化“上岗”](https://www.ncsti.gov.cn/kjdt/xwjj/202512/t20251219_232737.html)
- KUKA：[Robot-based assembly of flexible plug-in module connectors](https://www.kuka.com/en-us/industries/solutions-database/2023/05/liebherr-battery-pack-assembly%2C-high-voltage-battery)
- RePower：[Battery Pack Automated Production Line Solutions, printed pp. 27–28](https://www.repowerstock.com/data/downloads/6a0e820412482.pdf)
- Marposs：[Battery Module Electrical Test Systems](https://www.marposs.com/eng/application/electrical-test-battery-modules)

---

## 5.3 Shortlist C — 模组/Pack多工位搬运与拣选

### Case definition

| 字段 | 当前内容 |
| --- | --- |
| Production level | module/pack manufacturing；正式scope待Thomas确认 |
| Flow object | `UNKNOWN`：公开披露未说明具体是module、pack、料箱还是其他物料 |
| Exact robot task | CATL只公开material handling、picking和extended autonomous operation |
| Robot actor | CATL/Galbot重载人形机器人Galbot S1 |
| Direct industrial evidence | CATL官方称其进入智慧产线，在module/pack制造中承担搬运和拣选 |
| Battery-specific requirements | 当前`UNKNOWN`；可能包括载荷、重心、抓持安全、多高度取放、设备交接和traceability，尚未由同一case直接支持 |
| Comparison baseline | conveyor、forklift、AGV/AMR、移动机械臂、固定工业机器人、人工 |
| Possible thesis method | 只有锁定具体object、source、destination和handover后，才能开展多工位移动操作架构比较 |
| Validation route | CATL/Galbot具体任务视频、工位资料、专家或可访问的重载module/pack handling station |

### Evidence boundary

`DIRECT COMPANY DISCLOSURE`：CATL官方明确支持Galbot S1在module/pack制造中的material handling和picking。

`UNKNOWN / INSUFFICIENT`：

- 具体搬运对象；
- source与destination；
- 是否需要姿态调整、精定位或设备交接；
- battery requirement怎样改变robot task；
- 产品发布视频是否对应CATL具体电池工序。

### Current judgment

> **EXPLORATORY / NEEDS TASK EVIDENCE**：问题不是“搬运太简单”，而是当前任务边界太宽。如果以后证明机器人搬运50 kg级模组、跨多个human-oriented stations并完成精确交接，研究价值可以显著提高；在此之前容易退化为一般重载物流。

主要来源：

- CATL：[First Heavy-Duty Humanoid Robot Powered by CATL Batteries Goes Live in CATL Factory](https://www.catl.com/en/news/6881.html)
- Galbot产品发布视频：[银河通用机器人工业级具身智能重载机器人Galbot S1](https://www.bilibili.com/video/BV1StzfB1EYd/)

---

## 6. 为什么不把第四候选D提交为同级候选

第四候选是电芯制造中的机器人微环境/极片处理研究。

其优点：

- 最贴近PDF任务段落中的battery cell production value chain；
- 能连接dry-room、敏感材料、极片handling等Thomas原始PDF明确提出的挑战；
- 学术文献基础可能比直接humanoid deployment更强。

当前限制：

- 尚未建立与humanoid强相关的直接工业deployment；
- 与Thomas近期希望重点关注humanoid的反馈连接较弱；
- 可能更适合作为cell-manufacturing academic/future scenario，而不是本轮最务实的产业案例。

因此本轮只提交A/B/C。若Thomas明确要求论文核心必须限于cell manufacturing，D或其他cell-level robotics案例需要重新进入比较。

---

## 7. A/B/C的最终比较结论

### 7.1 若只比较直接企业任务证据

```text
A > B > C
```

- A的上汽官方描述明确到量产线、电芯识别、抓取和上料；
- B的工序和动作较清楚，但主要来自机器人公司披露，现场视觉证据有限；
- C由CATL直接披露，但任务仍停留在搬运/拣选类别。

### 7.2 若比较与Thomas论文结构的匹配度

```text
B > A > C
```

B更容易完整形成：

```text
practical problem
→ specific robot task
→ battery-specific safety/flexibility requirements
→ alternative architectures
→ technical-economic assessment
→ concrete application scenarios
→ implementation recommendations
```

### 7.3 当前决策

| Candidate | 当前状态 | 进入下一阶段的条件 |
| --- | --- | --- |
| B | `CONDITIONAL PRIMARY` | Thomas接受pack scope；补足工序/视频/专家证据；建立不依赖CATL内部数据的验证路径 |
| A | `STRONG BACKUP` | 说明具体上料destination/interface；证明battery requirement怎样改变robot task |
| C | `EXPLORATORY` | 获得具体flow object、source、destination、handover和battery-specific requirement |

---

## 8. B的case-lock条件

B只有以下条件达到后才能建立正式case charter：

1. Thomas确认module/pack可成为primary manufacturing scope；
2. Thomas确认humanoid是主要评价对象、比较方案之一，还是future-trend scenario；
3. 至少获得以下三类证据中的两类：
   - 可识别完整动作周期的原始工序视频；
   - EoL/DCR设备、测试线、安全互锁和connector资料；
   - PACK测试/机器人集成专家或可访问站点确认；
4. 比较baseline保持准确：专用自动插接是直接功能baseline，KUKA是柔性connector handling的技术邻近baseline；
5. thesis validation不依赖获得CATL专有日志或未承诺的企业数据；
6. 明确一个停止条件：如果无法确认实际任务、battery-specific effect或可执行validation route，B不锁题，返回A或problem map。

---

## 9. 建议向Thomas提出的问题

1. **Does the intended scope of “Battery Manufacturing” allow module and pack manufacturing to become the primary case, despite the phrase “battery cell production value chain” in the task paragraph?**
2. **Which case should be deepened: A—cell recognition/grasping/loading, B—flexible test-connector handling at Pack EoL/DCR, or C—multi-station module/pack handling and picking?**
3. **Should humanoid robots be the primary technology under evaluation, one architecture within a comparison, or mainly a future-trend scenario?**
4. **For candidate B, is there an accessible PEM/FFB/industry test station, equipment expert or integration expert who can confirm the real process, connector and safety requirements?**
5. **Would a comparative implementation study of dedicated automation, fixed industrial robots and humanoid/mobile manipulators satisfy the expected technical and economic depth?**

---

## 10. 后续组会PPT建议结构

这份brief可以裁剪为7页，不需要把所有技术细节搬进PPT：

1. **Thomas original thesis anchor**
   working title、原始task sequence、近期humanoid反馈。

2. **Week 04 — State of the art and counterexample audit**
   说明已有研究覆盖什么；Deng反例推翻什么；为什么没有直接进入AGV simulation。

3. **Week 05 — Formation handover feasibility test**
   展示`入库机27 → 堆垛机28 → 化成装置3`，明确它是fixed-automation baseline。

4. **Why the old candidate exited**
   一张robotics-relevance gate表：没有直接battery-specific effect改变堆垛机任务。

5. **Direction reset without losing prior work**
   解释Week 04–05如何建立证据审计方法，并返回Thomas原始robotics application map。

6. **A/B/C comparison**
   同口径展示direct case、task、baseline、evidence gap和validation route。

7. **Recommendation and supervisor decision**
   B conditional primary、A backup、C exploratory；提出scope、humanoid role和validation access问题。

---

## 11. 可直接放入组会的一分钟口头总结

> In Week 4, I reviewed the state of the art for carrier flow in cell finishing and actively searched for counterexamples. The review showed that configuration research already includes trays, some physical interfaces and intralogistics transitions, so I could not claim that cell-finishing logistics had not been studied. In Week 5, I examined one disclosed formation-loading architecture in detail. It clarified the fixed-automation chain from an inbound machine through a stacker crane to the formation equipment, but I found no direct evidence that a formation-specific requirement changed the stacker-crane task. Therefore, I retained this architecture as a baseline and stopped treating it as a thesis candidate. I then returned to the original thesis objective and compared three concrete humanoid-related battery-manufacturing cases. My current recommendation is Pack EoL/DCR test-connector handling, because it has a specific battery task and enables a comparison among dedicated automation, fixed industrial robots and humanoid/mobile manipulators. However, the public CATL–Spirit AI evidence is still mainly company disclosure, so I would like to confirm the module/pack scope and the available validation route before locking the case.

---

## 12. 当前不应写成的结论

- 不写“Week 04证明cell-finishing物流没有被研究”；
- 不写“Week 05研究了AGV进入formation设备”；
- 不写“堆垛机是论文机器人系统主角”；
- 不写“千寻小墨已经被独立证明优于工业机器人”；
- 不写“KUKA已经在相同EoL/DCR工位部署相同方案”；
- 不写“Galbot S1已经完成具体电池模组跨站精确交接”；
- 不写“humanoid一定比专用自动化更灵活或更经济”；
- 不把企业声称的精度、节拍、成功率、工作量或规模化部署写成独立验证结果；
- 不在Thomas确认前把module/pack冒充为已锁定scope；
- 不在获得任务、baseline和validation route前宣布最终research gap或题目。
