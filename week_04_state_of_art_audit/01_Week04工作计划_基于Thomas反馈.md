# Week 04 工作计划：Cell-finishing carrier flow 的现状与问题区

> 制定日期：2026-07-30  
> 依据：2026-07-29 Week 03 组会录像中的 Teams 自动字幕、Week 03 本地成果、`docs/collaboration_and_pacing.md`。  
> 状态：交给 GPT 外部审查前的 Codex 工作稿，不是最终 research gap、最终论文题目或 PEM/RWTH 官方要求。

---

## 1. 组会反馈闭环

本文件按照当前三方闭环形成：

```text
Thomas 的原始反馈（录像/Teams 字幕）
→ Codex 对照 Week 03 成果并整理证据边界
→ GPT 读取 GitHub 周成果，审查方向和工作量
→ 学生确认理解并决定是否执行/调整
```

Teams 字幕存在误识别，所以下文只把含义稳定、上下文一致的内容列为 Thomas 的明确反馈；不确定词句不作为逐字引语。

## 2. Thomas 的反馈整理

### 2.1 可以较明确确认的反馈

1. 当前聚焦于 cell finishing 中被运输的物料/载具是一个好的方向；Thomas 对学生所说的“focus on the material transported”表示认可。
2. Week 03 的拆解深度已经基本合适，没有陷入过多细节。
3. 下一步应寻找更多实例，包括电池生产中的实例以及其他工业领域的相邻实例。
4. 不能只收集“用了 AGV”的案例；需要追问：
   - 案例解决了什么问题？
   - 电池场景有什么特殊性？
5. Thomas 举出的 battery-specific problem 示例是热失控：如果被运输的电池发生 thermal runaway，甚至导致承载/运输系统起火，系统怎样应对？
6. 应先找出 cell-finishing carrier flow 的 state of the art，解释并写下当前状态，再识别其中的 problem areas。
7. 在了解现状后，才从中选择一个问题，判断是解决该问题，还是先把尚未被充分说明的问题识别清楚。
8. Thomas 提到 humanoid robotics 的工业关注度上升，并以 Tesla、Boston Dynamics 以及“AGV 与 humanoid robotic system 的比较”为可能的文献/案例探索例子。
9. Thomas 对本周工作总体评价积极，并认可继续检索文献、再向 gap 深挖的节奏。

### 2.2 Thomas 的示例，不应自动扩展为硬性要求

- thermal runaway / burning AGV 是帮助理解“battery-specific problem”的示例，不等于 Thomas 已指定安全或热失控为最终主题。
- humanoid robotics 是 Thomas 主动提出的探索方向，但录像没有确认要把 humanoid 设为论文主对象。
- “AGV 与 humanoid 比较”目前应作为受控的反例/技术边界检查，而不是立即建立完整比较框架。
- 录像没有要求 Week 04 开始仿真、优化、ROI 或算法比较。

### 2.3 当前仍未确定

- 最终研究对象是否只限 AGV；
- humanoid 是否只是邻近技术，还是后续需要正式纳入；
- thermal runaway 是否会成为核心约束；
- 目标载具是 tray、rack、pallet、单体 cell carrier，还是多种载具组合；
- 公开文献能否支持一个具体、可验证的 cell-finishing transport problem；
- 后续是否具备专家、设备资料或现场数据验证路径。

---

## 3. 对原 Week 04 草案的修正

Week 03 原计划把 Week 04 定义为“最近邻文献与反例审计”。这个方向仍然成立，但需要根据 Thomas 的反馈调整重点：

```text
原重点：验证“cell-finishing 工艺—载具流—AGV 设计连接不足”是否为 gap

修正后：先重建 carrier flow 的 state of the art
        → 比较真实解决方案及其问题
        → 提取 battery-specific problem areas
        → 再判断是否存在 candidate gap
```

也就是说，Week 04 不从预设 gap 出发。它先回答“行业和研究现在怎样做”，再谈“不足”。

---

## 4. Week 04 唯一核心问题

> **What is the current state of the art for transporting cells and carriers through cell finishing, and which battery-specific problem areas can be supported by existing evidence?**

中文：

> **电芯及其载具在 cell finishing 中运输的现有方式是什么？现有证据能够支持哪些电池场景特有的问题区？**

### 为什么现在研究它

Week 03 已经建立了 formation、aging、EoL、运输请求、等待、交接、blocking/starvation 等基础概念，但形成的仍是条件性流程，不是已确认的工厂架构。

Thomas 的最新反馈把下一步顺序说得更清楚：

```text
找实例
→ 写清 state of the art
→ 识别 problem areas
→ 再选择可继续深入的问题/gap
```

因此本周应把“我们推测运输可能怎样发生”推进为“公开证据显示实际采用了哪些载具和运输方案、为何采用、暴露了什么问题”。

---

## 5. 本周最低完成目标

完成以下四项，Week 04 即达到最低目标：

1. 一张 `cell-finishing carrier-flow state-of-the-art` 表，至少能区分工序、运输对象、运输方案、接口、解决的问题和证据来源。
2. 精读少量最接近的案例，至少包括：
   - cell finishing / battery cell production 的直接案例；
   - 一个能帮助解释运输/载具问题的相邻工业案例。
3. 形成一份 battery-specific problem-area 清单，每项都标明：文献事实、作者判断、我们的推断或未知。
4. 保留最多 1–2 个 candidate gap，并为每个 gap 写出最强反例；证据不足时允许本周不留下 gap。

本周成功不以论文数量衡量。能讲清两三个强案例，比罗列很多关键词命中更重要。

---

## 6. Day 1–5 学习顺序

Day 1–5 是学习顺序，不是硬性日历。某一步没有读懂时可以跨天，不为填满五天自动前进。

### Day 1 — 定义“现有方式”要观察什么

核心学习问题：

> 一篇资料需要给出哪些内容，才足以描述 cell-finishing carrier flow 的一种现有方式？

任务：

- 以 Week 03 概念模型为底稿，确定 state-of-the-art 表的字段；
- 明确 flow object：cell、tray、rack、pallet、goods carrier 或未披露；
- 明确 transport solution：人工、conveyor、AS/RS、AGV/AMR、其他移动机器人或组合系统；
- 记录工序边界、release condition、buffer/storage、handover 和异常流；
- 建立 direct / adjacent / false match 纳入标准。

学生应能用自己的话解释：为什么“论文同时写了 battery 和 AGV”仍不一定是直接案例。

### Day 2 — 重建 cell-finishing carrier-flow state of the art

核心学习问题：

> 公开资料显示，formation、aging 和 EoL 周围的电芯/载具实际上怎样移动和存储？

任务：

- 优先精读 cell-finishing planning、equipment、layout、material-flow 或 simulation 资料；
- 寻找 tray/rack/carrier 的装载、转运、存储、出入库和换载信息；
- 区分通用工艺流程与某个设备商/工厂的特定架构；
- 写出至少两种有来源支持的解决方案形态；若证据不存在，明确记录未知。

避免把 Week 03 的条件性 `formation → AGV → aging rack` 图当成行业标准流程。

### Day 3 — 从案例中找 problem areas

核心学习问题：

> 这些运输方案在电池场景中解决了什么问题，又产生或保留了什么问题？

优先检查：

- 长时间 aging、并行设备与高 WIP 对载具/存储的影响；
- 追溯、错料、载具识别和状态同步；
- handover、buffer、blocking/starvation；
- 异常品、隔离和回流；
- thermal runaway、起火载荷和应急处置是否有直接证据；
- cell format、载具形式和设备集成差异。

每个 problem area 使用以下证据链：

```text
问题陈述
→ 来源与准确页码/章节
→ 原文直接支持了什么
→ 对电池制造的含义
→ 对机器人/运输系统的含义
→ 仍未知什么
```

### Day 4 — 受控检查 AGV 与 humanoid 的边界

核心学习问题：

> 对当前 cell-finishing 运输任务而言，humanoid 是已有工业方案、未来概念，还是不适用的相邻技术？

任务：

- 查找 Thomas 提到的 Tesla、Boston Dynamics 或其他一手/学术资料；
- 只比较与当前运输任务直接相关的能力边界，例如载荷、取放接口、环境适应、安全、成熟度和证据类型；
- 区分演示、试点、生产部署和同行评审研究；
- 检查 humanoid 是否真正解决当前 carrier-flow problem，而不是因话题热门而纳入。

这一日的最低产出是一段有证据边界的判断，不要求制作完整技术排名。若找不到 cell-manufacturing 直接证据，应写成证据缺口，而不是宣称 humanoid 更先进或更灵活。

### Day 5 — 综合、反例与下一步决策

核心学习问题：

> 现有研究已经解释了什么，哪个问题仍值得继续，下一步需要什么验证？

任务：

- 完成 state-of-the-art 对照表；
- 将 problem areas 按“直接证据强度”和“与 cell finishing 的相关性”筛选；
- 最多提出 1–2 个 candidate gap；
- 为每个 candidate gap 主动寻找最强反例；
- 把公开资料无法回答的内容改写为 5–8 个专家/设备资料问题；
- 做 `continue / continue learning / adjust` 决策，不写仿真代码。

---

## 7. 建议的 state-of-the-art 表字段

| 字段 | 阅读时要回答的问题 |
| --- | --- |
| Manufacturing scope | cell / module / pack / unspecified？ |
| Process step | formation / aging / EoL / grading / other？ |
| Flow object | cell / tray / rack / pallet / unspecified？ |
| Current solution | manual / conveyor / AS/RS / AGV/AMR / other？ |
| Route and release logic | 何时、从哪里、到哪里移动？ |
| Storage/buffer | 如何存储、缓存和释放？ |
| Handover | 与设备怎样物理交接？ |
| Problem addressed | 为什么采用该方案？ |
| Battery-specific constraint | 哪一点不是一般物流问题？ |
| Failure/exception | 错料、隔离、故障或热事件怎样处理？ |
| Evidence type | peer-reviewed / industrial / vendor / inference？ |
| Validation | live deployment / logs / simulation / lab / claim？ |
| Exact evidence | DOI、页码/章节、原文支持边界 |

---

## 8. 当前只允许作为 working hypotheses 的问题区

以下内容是 Week 04 的检索入口，不是已经成立的研究结论：

1. **Process–transport coupling**：cell-finishing 工艺研究可能描述设备和工序，但没有充分描述移动运输系统；AGV 研究可能描述车队，但不公开 battery-process semantics。
2. **Exception and safety handling**：通用 AGV KPI 可能不足以表达异常电芯、隔离和 thermal-runaway response。
3. **Carrier/handover architecture**：tray、rack、buffer 和设备接口可能决定运输任务，但公开研究未必披露到这一层。
4. **Technology-boundary question**：humanoid 是否对当前任务提供真实优势，可能缺少生产级证据。

其中任何一项都必须经过反例搜索才能保留为 candidate gap。

---

## 9. 本周明确不做

- 不开始 SimPy 或其他离散事件仿真；
- 不优化 AGV 数量、dispatching、routing 或 parking；
- 不填造节拍、距离、托盘容量、故障率和成本；
- 不把 thermal runaway 自动定为论文主问题；
- 不把 humanoid 扩展成独立的大型研究主题；
- 不做泛化的“AGV vs humanoid 谁更好”比较；
- 不宣布最终 research gap 或最终研究问题；
- 不因直接文献少而把主范围扩大到 module/pack、recycling 或整厂物流；
- 不用供应商营销材料替代学术 state of the art。

---

## 10. 有余力再做

- 找一个公开设备布局或 handover 图，重绘成内部学习图并标出证据边界；
- 补充一种 cell format 对载具方案的影响；
- 为 Thomas 的 thermal-runaway 示例做一页“已有证据/未知/专家问题”；
- 将 AGV、固定输送/存储系统和 humanoid 放在一张任务适配表中，但只使用有来源的属性。

这些内容不是最低完成要求。

---

## 11. 三方职责

### GPT：周方向与外部审查

- 读取本计划和 Week 03 已推送成果；
- 审查本周唯一核心问题是否足够具体；
- 检查是否过度放大 humanoid 或 thermal-runaway 示例；
- 检查工作量是否符合 Master-Thesis 周节奏；
- 不在审查时自动增加 optimization、ROI、robustness 等新变量。

### Codex：执行与证据审计

- 执行定向检索和全文精读；
- 核查 DOI、页码/章节和证据边界；
- 维护 direct / adjacent / false match 分类；
- 把 Thomas 的示例与正式研究结论分开；
- 制作 state-of-the-art 表和 problem-area 证据链；
- 在学生确认前不自动 commit/push。

### 学生：学习者与最终决策者

- 用自己的话复述两三个最接近案例怎样搬运 cell/carrier；
- 能说清一般物流问题与 battery-specific problem 的区别；
- 判断 humanoid 支线是否与自己的论文理解一致；
- 确认本周成果和下一步决策后，再交由 Codex 推送给 GPT 审查。

---

## 12. 周末检查点

### Continue

公开证据能够定义至少一种可信的 cell-finishing carrier flow，并支持一个尚未被充分回答、且有验证路径的问题区。

### Continue learning

state of the art 已更清楚，但 carrier/interface、安全异常或工业证据仍不足；再补一周基础证据。

### Adjust

强反例已完整覆盖候选问题，或公开证据无法支撑可信的 cell-finishing 场景；调整问题或案例。

完成 Week 04 不代表自动进入仿真。

---

## 13. 给 GPT 的审查入口

可以把本文件和 Week 03 成果交给 GPT，并请它只回答：

1. 这个计划是否忠实响应了 Thomas 的“state of the art → problem areas → gap”顺序？
2. humanoid 和 thermal-runaway 是否被控制在合适范围，而没有抢走 cell-finishing carrier-flow 主线？
3. 最低完成目标是否适合一周，哪些内容应删除而不是继续增加？
4. 在不预设 gap 的前提下，Day 1–5 的证据链是否足以支撑周末决策？

---

## 最后一句

> Week 04 的任务不是证明 AGV 或 humanoid 更好，而是先说明 cell-finishing carrier flow 现在怎样实现、为什么这样实现、暴露了哪些具有电池特殊性的真实问题。
