# Supervisor Reading Plan / 导师推荐文献学习计划

Source:

Email from Thomas Fey, 2026-07-07.

目的：

导师推荐的文献主要用于补齐 lithium-ion battery fundamentals，也就是锂离子电池基础。我们的 thesis topic 是 robotics in battery manufacturing，但在进入机器人应用之前，必须先理解电芯结构、材料、工作原理、制造流程和质量控制。

## 1. What the Supervisor Is Really Asking For / 导师真正想让我们补什么

The email is not asking us to immediately become electrochemistry experts. It is asking us to build enough battery knowledge to understand manufacturing requirements.

导师不是要求我们立刻变成电化学专家，而是希望我们先具备足够的电池基础，能理解为什么电池制造对环境、精度、质量和过程控制要求这么高。

The key learning bridge is:

```text
Battery fundamentals 电池基础
  -> Process requirements 工艺要求
  -> Robotics opportunities 机器人机会
  -> Implementation strategy 落地策略
```

For example:

```text
SEI formation matters
SEI 形成很重要
  -> formation process is critical
  -> 化成工序很关键
  -> formation logistics and traceability matter
  -> 化成物流和数据追溯很重要
  -> robots can support tray handling and data-linked automation
  -> 机器人可以支持托盘搬运和数据化自动化
```

## 2. Recommended Papers from Supervisor / 导师推荐文献

| Paper / 文献 | Role in learning / 学习作用 | How to read / 怎么读 |
| --- | --- | --- |
| Lithium-ion Battery Fundamentals and Exploration of Cathode Materials: A Review (2024) | Battery fundamentals and cathode materials / 锂电基础和正极材料 | Read for battery components, cathode types, basic working principles. / 重点看电池组成、正极材料类型、基本工作原理。 |
| A Review on Design Parameters for Full-Cell Lithium-Ion Batteries (2024) | Full-cell design, balancing, cell formats / 全电芯设计、容量匹配、电芯形式 | Read for anode/cathode balance, format differences, and design constraints. / 重点看正负极匹配、电芯形式差异、设计约束。 |
| Goodenough, J. B., & Park, K. S. - The Li-Ion Rechargeable Battery: A Perspective (2013) | Classic Li-ion battery overview / 经典锂电综述 | Read to understand why Li-ion batteries work and how the technology developed. / 理解锂电池为什么能工作，以及技术发展脉络。 |
| Tarascon, J. M., & Armand, M. - Issues and Challenges Facing Rechargeable Lithium Batteries (2001) | Classic challenges and fundamentals / 经典挑战综述 | Read for fundamental challenges: safety, materials, energy density, stability. / 重点看安全、材料、能量密度和稳定性问题。 |
| Xu, K. - Electrolytes and Interphases in Li-Ion Batteries and Beyond | Electrolytes, interphases, SEI / 电解液、界面、SEI | Read selectively. Focus on electrolyte and SEI, not every chemistry detail. / 选择性阅读，重点理解电解液和 SEI，不必深挖所有化学细节。 |

Note:

The two 2024 paper titles should be verified with DOI or PDF links later, because quick web search did not clearly identify exact matches from the title alone.

备注：

前两篇 2024 文献最好后续向导师或数据库确认 DOI/PDF，因为仅凭标题快速搜索没有非常明确地定位到精确版本。

## 3. Topics Recommended by Supervisor / 导师建议熟悉的主题

| Topic / 主题 | Chinese / 中文 | Why it matters for our thesis / 为什么对本课题重要 |
| --- | --- | --- |
| Operating principles of lithium-ion batteries | 锂离子电池工作原理 | Helps explain why moisture, electrolyte, SEI, and formation matter. / 帮助理解水分、电解液、SEI、化成为什么重要。 |
| Cell components | 电芯组成 | Anode, cathode, separator, electrolyte define handling and process requirements. / 正极、负极、隔膜、电解液决定搬运和工艺要求。 |
| Cell formats | 电芯形式 | Coin, pouch, cylindrical, prismatic formats lead to different robotic handling strategies. / 扣式、软包、圆柱、方形电芯对应不同机器人搬运策略。 |
| Electrode manufacturing | 电极制造 | Mixing, coating, drying, calendering determine quality and defect risks. / 混料、涂布、干燥、辊压决定质量和缺陷风险。 |
| Cell assembly | 电芯装配 | Thin and sensitive materials make robotics difficult but valuable. / 薄软敏感材料使机器人落地困难但有价值。 |
| Formation and aging | 化成和老化 | Critical for performance, safety, quality screening, and traceability. / 影响性能、安全、质量筛选和追溯。 |
| Manufacturing processes and quality control | 制造过程与质量控制 | Connects directly to robotics, vision inspection, MES, and automation strategy. / 直接连接机器人、视觉检测、MES 和自动化策略。 |

## 4. Reading Priority / 阅读优先级

Do not read everything equally deeply.

不要平均用力。建议按三层读：

### Level 1: Must Understand / 必须理解

- Battery components: anode, cathode, separator, electrolyte
- Basic charging/discharging principle
- Cell formats: pouch, cylindrical, prismatic, coin
- Electrode manufacturing: mixing, coating, drying, calendering
- Cell assembly and finishing
- Formation, aging, SEI

### Level 2: Useful for Thesis / 对论文很有用

- Why moisture control is important
- Why electrolyte filling and SEI formation matter
- Why electrode defects affect cell quality
- Why formation and testing require traceability
- How different cell formats affect robotic handling

### Level 3: Nice but Not Central / 可了解但不是主线

- Detailed cathode crystal chemistry
- Full electrochemical reaction modeling
- Advanced electrolyte additive mechanisms
- Detailed degradation equations
- Lab-scale coin cell methodology

## 5. How to Read Each Paper / 每篇文献怎么读

For each paper, capture only five things:

每篇文献先只抓五件事：

1. What are the main cell components?
   主要电芯组成是什么？

2. Which manufacturing process does this paper help explain?
   它帮助解释哪个制造工序？

3. Which quality or safety issue does it mention?
   它提到什么质量或安全问题？

4. What does it imply for robotics or automation?
   它对机器人或自动化有什么启发？

5. Which thesis section can use it?
   它可以放到论文哪一章？

## 6. Connection to Our Thesis / 和我们课题的连接

| Battery concept / 电池概念 | Manufacturing implication / 制造含义 | Robotics implication / 机器人含义 |
| --- | --- | --- |
| Separator is thin and delicate / 隔膜薄且敏感 | Cell assembly requires gentle handling. / 电芯装配需要温和搬运。 | Gripper design and vision-guided placement are important. / 夹爪和视觉定位重要。 |
| Electrolyte is moisture-sensitive / 电解液怕水 | Filling and assembly need dry room. / 注液和装配需要干房。 | Robots must be dry-room compatible. / 机器人要干房兼容。 |
| SEI formation affects lifetime / SEI 影响寿命 | Formation process is quality-critical. / 化成是质量关键工序。 | Formation tray handling and data tracking are strong use cases. / 化成托盘搬运和数据追踪是强案例。 |
| Electrode defects affect performance and safety / 极片缺陷影响性能和安全 | Coating, drying, slitting need inspection. / 涂布、干燥、分切需要检测。 | Vision inspection and automated sampling are relevant. / 视觉检测和自动取样相关。 |
| Cell formats differ / 电芯形式不同 | Handling, fixtures, and assembly differ. / 搬运、夹具和装配不同。 | Use cases must specify pouch, cylindrical, or prismatic cells. / 案例必须说明电芯形式。 |

## 7. Updated Week 1 Plan with Supervisor Input / 根据导师建议更新第一周计划

| Day | Focus / 重点 | Output / 产出 |
| --- | --- | --- |
| Day 1 | Scope and research questions / 研究范围和问题 | `scope_and_research_questions.md` |
| Day 2 | Battery fundamentals and components / 电池基础和组成 | `battery_fundamentals_cn_en.md` |
| Day 3 | Cell formats and manufacturing process / 电芯形式和制造流程 | `battery_cell_process_chain.md`, `process_to_robotics_map.md` |
| Day 4 | Manufacturing requirements and quality control / 制造要求和质量控制 | `process_requirement_table.md` |
| Day 5 | Robot types and application areas / 机器人类型和应用区域 | `robot_system_types.md`, `robotics_application_matrix.md` |
| Day 6 | Literature log and source summaries / 文献记录和总结 | `literature_log.md` |
| Day 7 | Supervisor discussion brief / 导师沟通简报 | `supervisor_brief.md` |

## 8. Immediate Next Step / 立即下一步

Create a battery fundamentals learning file covering:

下一步应建立一个电池基础学习文件，覆盖：

- anode / 负极
- cathode / 正极
- separator / 隔膜
- electrolyte / 电解液
- lithium-ion movement / 锂离子移动
- electron flow / 电子流
- SEI / 固态电解质界面膜
- cell formats / 电芯形式
- why these concepts matter for manufacturing and robotics / 为什么这些概念影响制造和机器人应用

This will become the foundation before continuing to robotics-specific literature.

这会成为我们继续进入机器人应用文献前的基础。
