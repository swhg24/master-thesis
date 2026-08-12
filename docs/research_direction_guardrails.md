# Research Direction Guardrails / 研究方向与防跑偏护栏

> 维护日期：2026-08-12
> 用途：本文件是 GPT、Codex 与学生在选择案例、制定周计划、收缩研究问题和判断论文相关性时的**必读项目规则**。
> 状态：项目内部方向协议，不是 PEM/RWTH 官方文件，也不是最终注册题目、最终 research question 或 Thomas 的逐字书面决定。

## 1. 最高方向锚点

### 1.1 研究方向优先级

本项目在**研究方向与scope**上的依据顺序是：

```text
Thomas最新明确反馈
→ Thomas原始任务说明 `abschlussarbeiten_42444.pdf`
→ 本方向护栏
→ 周计划与case dossier
→ 当前工作假设
```

低层文件与高层依据冲突时，应修改低层文件；不得为了保留旧候选而重新解释Thomas的原始任务。PEM/RWTH/ZPA的正式规定另行约束注册、写作、提交与答辩，不与上述研究方向顺序混淆。

### 1.2 Thomas原始任务说明

Thomas 最初给出的 working title 是：

> **Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies**

因此，本论文无论怎样收缩，都必须同时保留三个要素：

1. **Battery manufacturing**：核心场景属于锂离子电池制造，并明确处于cell、module还是pack层级；标题与任务段落对生产层级的表述宽窄不同，因此由Thomas确认，内部规则不得预先排除module/pack；
2. **Robotic systems**：必须存在可辨认或可被可信评价的机器人系统角色；
3. **Potentials / applications / implementation**：研究必须落到机器人为何适合、承担什么任务、受什么约束以及怎样集成和验证，而不只是描述电池设备。

本论文不是为了设计机器人本体，也不是为了证明某一种机器人必然最好。它研究的是：

> 电池制造中的具体问题怎样形成机器人任务；电池工艺、产品、环境和设备接口怎样约束机器人系统；选定机器人应用在什么条件下具有价值并能够工业实施。

根据`abschlussarbeiten_42444.pdf`，原始任务轮廓是：先理解制造工艺及要求，再识别工业机器人、协作机器人和移动系统的合适应用，随后从自动化潜力、成本、质量影响和可扩展性等维度开展技术经济评价，把选定use case发展成具体应用场景，并形成未来趋势与实施建议。PDF任务段落写有`battery cell production value chain`，标题写有`Battery Manufacturing`；module/pack是否可成为正式核心必须向Thomas确认。工艺学习只是机器人应用研究的输入，不是独立终点。

## 2. 信息类型必须分开

### 2.1 Thomas 明确或较可靠的指导

- 原始 working title 聚焦 `Robotic Systems in Battery Manufacturing`；
- 不能停留在宏观机器人应用目录，应选择一个 use case step by step 深入；
- 需要同时理解电池工艺和机器人系统，再判断机器人能否解决具体问题；
- scope、case 和数据需求应随问题与证据逐步形成；
- 文献之外最终需要专家、设备资料、案例或数据支撑；
- Week 03 组会字幕整理显示 Thomas 认可继续聚焦 transported material，并要求先看 state of the art 与 battery-specific problem。

注意：后两项部分依据 Teams 字幕/OCR 整理，属于对导师反馈的可靠解释，不应冒充逐字书面要求。

### 2.2 项目中整理的 PEM 工作参考

- 科学逻辑应为：practical problem → state of research/gap → approach/method → validation → conclusion；
- 机器人系统不只是机械臂，还包括 end effector、sensor/vision、fixture、safety、process-equipment interface、MES/traceability、material flow 和 operating environment；
- 应区分 core process equipment 与周边适合机器人承担的 handling、transport、inspection、sampling 和 data tasks。

正式注册、提交或答辩前仍须核验最新 PEM/RWTH/ZPA 规定。

### 2.3 文献支持的当前认识

- 特定 cell-finishing 配置使用 tray/product carrier 处理成组电芯；
- formation carrier 在特定来源中可能承担 contact、fixture 或 controlled-pressure 功能；
- 已有配置研究把部分 physical interfaces 与 intralogistics transitions 纳入模型；
- 公开配置包括人工与全自动 tray-based process，但 fully automated 不等于 AGV；
- 存在真实记录驱动的 rechargeable-battery production AGV 研究，但公开证据未证明其服务 formation tray flow。

这些来源不是同一工厂，不得拼接为一条已存在生产线。

### 2.4 当前工作假设

- 模组/Pack制造的电芯上料、高压接插件测试与多工位搬运是当前有直接humanoid企业案例的任务，不等于性能主张已经独立验证；
- cell/module/pack geometry、带电状态、高压风险、柔性线束、来料位置变化、product mix和traceability可能改变末端执行器、感知、力控、task allocation与设备集成要求；
- 人形或移动操作机器人的潜在价值可能只出现在多任务、多站点、既有human-oriented layout或高变型场景；稳定高节拍主流工况可能仍由专用自动化或固定工业机器人占优；
- 当前尚未找到针对上述企业humanoid deployment本身的同行评审论文；相关论文主要支持任务、柔性装配与传统机器人baseline。

以上均是下一阶段待核验的working hypotheses，不得写成事实、已证优势或established gap。

### 2.5 2026-08-11 外部 GPT 审查与 Codex 复核记录

本次外部审查中，以下建议被项目正式吸收：

- B2足以作为学习显微镜和fixed-automation baseline，但证据充分不等于论文价值充分；
- 越接近B3，潜在battery-specificity越强，但直接证据与现实验证越弱；
- 不继续细化堆垛机机构、PLC sequence或未披露端口；
- 任何候选必须同时通过practical relevance、battery specificity、robotics relevance与validation access；
- `patent unknown`或`paper unknown`不等于industrial problem或research gap；
- Week 05不进入simulation；Candidate A失败时返回problem map，不自动跳Candidate B或AGV fleet sizing。

以下建议经复核后被**收紧**：

- `process-aware carrier handover`只保留为待检验的feasibility hypothesis，不作为已经成立的研究问题；
- B2与B3之间是否存在独立acceptance condition必须由同一配置的直接证据或专家确认，不能因formation理论上需要contact/readiness而补画；
- 最小state model不是Day 3的必做主产出。先确认是否存在被battery requirement改变的robotic-system task；只有通过这一门，状态表示才有意义；
- `automation interface`不自动等于`robotics thesis problem`。fixed stacker crane是否可作为论文核心robotic system，仍需Thomas明确边界。

以下内容不得从外部审查意见转写成事实：

- 真实目标系统存在AGV；
- AGV把tray交给入库机；
- position、contact、pressure、identity与readiness均跨越物流—工艺边界；
- B3一定比B2更值得研究；
- Candidate A已经存活或已经成为最终论文方向。

## 3. 从 Week 01 到 Week 05 的稳定主线

```text
Week 01  电池基础 → 工艺要求 → 初始机器人机会
    ↓
Week 02  process → problem → task → robotic role
    ↓ Thomas：层级仍高，pick one case and go step by step
Week 03  formation–aging–testing carrier/tray flow学习案例
          工艺语义、条件性任务、AGV系统与接口unknown
    ↓
Week 04  state of the art + counterexample audit
          已有配置/接口研究；保留Candidate A/B但不宣布gap
    ↓
Week 05  用具体formation-loading公开架构填补一个interface unknown
          检验它是否真的产生battery-specific + robotics-relevant问题
    ↓ 只有通过现实性、机器人相关性和验证门后
Later    practical problem → candidate RQ → method → validation
```

Week 03 的 tray-flow 案例是把宏观题目放到具体技术对象上的学习显微镜。Week 05 的一项专利又只是该学习案例中的一个更小显微镜。后者不得取代整条机器人研究逻辑。

## 4. 2026-08-12方向重置与候选决策阶段

### 4.1 已结束的旧候选路径

Week 05 Day 3责任审计没有找到直接证据证明formation-specific condition改变了B2堆垛机任务。B2因此保留为：

> **non-AGV fixed-automation baseline / counterexample / learning case**

它退出当前thesis-candidate path。除非未来出现一个真实可验证的robotic target case，不再继续细化B2的PLC、contact、positioning、acceptance或handover state。

### 4.2 Thomas决策短名单（尚未选定）

在进一步case deep dive前，仅比较以下三个有直接企业证据的候选：

1. **A—电芯识别、抓取与模组/Pack装配上料**：上汽`能仔1号`量产线案例直接支持来料识别、路径规划、抓取与上料；sorting、matching和kitting尚不是该案例直接事实，只能作为待核验扩展。
2. **B—Pack EoL/DCR高压测试接插件柔性插拔**：CATL/千寻智能`小墨`案例直接支持高压测试插头插接、柔性线束处理与连接状态检查；需与固定双工业机器人方案比较，而不能预设humanoid优势。
3. **C—模组/Pack多工位搬运与拣选**：CATL Galbot S1直接支持module/pack中的material handling与picking，但公开任务、flow object和接口粒度仍过低，暂不具备直接deep-dive条件。

`cell-EoL终检/分选`不再是已选case；`module/pack`也不再被内部规则预先排除。正式边界由Thomas结合原始PDF和最新humanoid反馈确认。

### 4.3 当前唯一中心问题

> **A、B、C中哪一个case最符合Thomas预期的battery-manufacturing scope，并同时具有足够清楚的robot task、battery-specific requirement、比较baseline、研究方法与验证入口，可以被正式锁定？**

这一阶段的产出是给Thomas的evidence-bounded case-selection brief，不是新一轮宽泛landscape，也不是直接宣布research gap。

### 4.4 尚未确定

- 最终论文是否以humanoid为主对象，还是把它作为一种候选robot architecture；
- A、B、C中哪个成为primary case；
- cell format与生产环境如何进一步收缩；
- 最终 practical problem、research gap、research question、method 和 validation design；
- 是否存在可访问的FFB/PEM/industry reference case与专家验证入口。

### 4.5 Case Lock与变更控制

Thomas与学生确认后建立一页`case charter`，至少固定：production level、system boundary、flow object、robot task、comparison baseline、central question、evidence minimum和validation route。每日学习只能填充这些字段，不能静默改变case。

锁定case只有在以下任一条件出现时才允许正式调整：

1. Thomas明确改向；
2. 直接证据否定关键可行性或robotics-relevance gate；
3. 在预先定义的检索与专家路径完成后，仍不存在可执行的validation route。

调整必须写出`原case → 新case、触发证据、对已完成工作的影响、学生/Thomas决定`；不得靠周计划连续性或新热点隐性换题。

## 5. Week 05 Architecture B 的正确身份

Architecture B（CN118970237A）公开了：

```text
主输送机构1
→ 第五移载装置25
→ 第三输送部26
→ 入库机27
→ 堆垛机28
→ 化成装置3
```

Week 05 暂时审计的 B2 是：

```text
Source equipment: 入库机27
Transfer actor: 堆垛机28
Destination equipment: 化成装置3
```

它的身份必须写成：

> **non-AGV fixed-automation reference/baseline and counterexample**

它能够帮助：

- 证明“送入formation”可能由多个设备分段完成；
- 区分区域运输、固定入库、最终上料与工艺接入；
- 反驳“AGV必然直接把tray送入化成设备”；
- 提取未来机器人系统需要面对的功能和接口检查项。

它不能证明：

- 目标工厂使用堆垛机或 AGV；
- 堆垛机课题就是本论文题目；
- 未披露的position/contact/acceptance是工业问题或research gap；
- Deng/Schomburg中的fixture、pressure、contact属于这项专利；
- B2与B3之间必然存在独立的process-aware acceptance layer。

## 6. Technical neutrality ≠ robotics neutrality

不要为了保留机器人主题而把 AGV 强行画进没有 AGV 的来源。但是，也不能因为“技术中立”而把机器人系统完全从研究问题中移除。

一个潜在 thesis case 至少必须回答：

```text
Battery-manufacturing problem是什么？
→ 被处理对象与工艺约束是什么？
→ 哪个机器人系统承担什么任务，或哪项机器人集成决策受到固定自动化接口影响？
→ 工艺约束怎样改变其能力、接口或控制要求？
→ 需要作出什么机器人系统设计/实施决定？
→ 用什么现实证据验证？
```

如果只能回答“某台设备把tray从A送到B”，它是架构描述，不足以成为机器人论文问题。

## 7. Robotics Relevance Gate / 机器人相关性硬门

任何候选进入 thesis-problem path 前，逐项记录 `YES / NO / UNKNOWN + evidence`：

| Gate | 必须证明的内容 |
| --- | --- |
| Direct battery-manufacturing evidence | 属于明确的lithium-ion cell、module或pack制造配置，生产层级与scope状态已标明，而不是泛物流 |
| Identifiable robotic-system relevance | 存在明确robot actor，或有现实理由评价一种robotic solution；不是只有process equipment内部动作 |
| Battery-specific effect on the robot task | 至少一项工艺条件直接改变载荷处理、定位、感知、交接、确认、异常行为或其他机器人任务要求 |
| Meaningful system decision | 存在可研究的task allocation、architecture selection、interface design或implementation decision，而不只是资料没写 |
| Practical consequence | 问题影响可靠性、质量、安全、可用性、柔性或系统集成 |
| Credible validation route | 有具体专家、设备资料、真实/规划案例、日志、实验或其他可执行验证入口 |

前五项不能至少形成可信 `YES` 候选、或 validation route 仍完全不存在时，不得宣布 KEEP、gap 或 RQ。

## 8. 对候选条件的责任审计

Position、contact、pressure、identity 和 readiness 只是筛选项，不是五个并列研究主题。每项先填：

| 字段 | 问题 |
| --- | --- |
| Direct evidence in the selected case | 当前同一来源是否明确支持？ |
| Cross-source evidence | 是否只在另一配置出现，因而不能移植？ |
| Responsible subsystem | mobile robot、fixed transfer、carrier、formation equipment、MES/PLC还是unknown？ |
| Effect on robotic task | 是否真正改变机器人系统，还是由formation equipment内部消化？ |
| Practical consequence | 失败为什么重要？是否有直接证据？ |
| Validation | 谁或什么资料可以确认？ |

如果某项要求全部由 formation equipment 内部负责，它可以作为工艺背景，但不自动属于机器人 handover 研究。

## 9. 当前明确不做

- 不把 B2 堆垛机机构继续细化为论文中心；
- 不把 fixed automation 自动称为 robotics contribution；
- 不预设 AGV 直接进入 formation equipment；
- 不在transport technology、任务、数据和验证未确认时做fleet sizing、dispatching、routing、parking或robustness；
- 不把position、contact、pressure、identity、readiness全部捆成一个大课题；
- 不研究formation电化学配方、cabinet内部详细机构或PLC报文实现；
- 不扩大到整厂或recycling；module/pack可进入Thomas决策短名单，但在导师确认前不冒充已锁定scope；
- 不因为humanoid热门或Thomas建议关注就预设其优于工业机器人/专用自动化，也不进入步态、运动控制或foundation-model算法开发；
- 允许把humanoid作为重点候选机器人类别，但必须绑定具体battery-manufacturing task、比较baseline、battery-specific requirement、实施决策与验证路径；
- 不因专利/论文未披露就宣布industrial problem或research gap；
- 不自动从Candidate A跳到Candidate B；候选失败后返回problem map重新按证据选择。

## 10. Week 05 之后的决策

### 2026-08-12已作决定

`B2 formation handover`已执行`ABANDON / RETURN TO MAP`：作为baseline保留，但退出thesis-candidate path。下一阶段不是自动选择humanoid，也不是直接宣布新gap，而是完成第4节A/B/C短名单的同口径证据卡并交由Thomas与学生选择。

### KEEP / NARROW

只有机器人相关性硬门、battery-specific effect、practical relevance和validation均有证据时，才允许选择一个要求继续窄化。

### CONTINUE LEARNING

机器人actor或真实接口尚待Thomas/专家确认，但已经明确缺什么事实；允许短期补证，不无限增加专利。

### ABANDON / RETURN TO MAP

如果 B2 只是普通固定搬运，或所有formation-specific要求均由设备内部处理，或没有验证入口，则：

- 保留Week 05作为fixed-automation baseline学习成果；
- 不继续为了连续性研究handover；
- 返回Week 02/04 problem map，重新比较exception flow、vision-guided loading/inspection、机器人上下料或其他有更清楚robotics relevance的候选；
- 不自动回到AGV fleet simulation。

## 11. 向 Thomas 必须确认的方向问题

1. **Does the intended scope of “Battery Manufacturing” include module and pack production as a possible primary case, despite the task paragraph's wording “battery cell production value chain”?**
2. **Which case should we deepen: (A) cell identification/grasping/loading for module or pack assembly, (B) flexible high-voltage test-connector handling at pack EoL/DCR testing, or (C) multi-station material handling and picking in module/pack production?**
3. **Should humanoid robots be the primary technology under evaluation, one candidate within a technology comparison, or mainly a future-trend scenario?**
4. **Which concrete FFB/PEM/industry station, expert, equipment specification, or dataset could validate the selected task requirements and current automation pain points?**
5. **After selecting the case, which product format and production environment should form the first concrete application scenario?**

## 12. 每周计划前的强制自检

GPT/Codex 在提出下一周或下一日工作前，必须回答：

1. 本任务怎样连接 Thomas 的原始 robotic-systems 题目？
2. 本任务研究的是 battery-manufacturing problem，还是只在描述一台设备？
3. 可辨认的robotic actor或robotic-system decision是什么？
4. 哪条直接证据说明battery requirement会改变机器人任务？
5. 是否把另一来源的工艺功能错误移植到当前case？
6. 本周是否只推进一个中心问题？
7. 哪个结果会让我们停止或放弃该候选？

任一核心问题答不出来时，应先进行方向校准，不继续增加设备细节、状态图或仿真。
