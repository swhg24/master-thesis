# Scope and Research Questions / 研究范围与研究问题

This file defines what the thesis is about, what it is not about, and which questions the thesis should answer.

这个文件的作用是先把课题边界定住：我们到底研究什么、不研究什么、最后要回答哪些问题。

## Working Title / 暂定题目

Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies

中文理解：

机器人系统在电池制造中的潜力、应用场景与实施策略研究。

这里的重点不是设计一个机器人本体，而是分析机器人在电池制造中的应用价值和落地方式。

## Initial Scope / 初始研究范围

This thesis focuses on robotic systems along the lithium-ion battery cell manufacturing value chain.

本论文关注锂离子电芯制造价值链中的机器人系统应用。

The main focus is cell production, not module assembly, pack assembly, battery use-phase operation, or recycling. These neighboring areas may be mentioned briefly if they help clarify boundaries, but they should not become the core of the thesis unless the supervisor explicitly redirects the scope.

研究重点是电芯制造，而不是模组装配、电池包装配、电池使用阶段或回收。相关领域可以简要提到，但不应成为论文核心，除非导师明确要求。

Simple boundary / 简单边界：

```text
Included 研究：
raw material -> electrode -> cell assembly -> formation/testing -> finished cell

Not the main focus 暂不作为核心：
cell -> module -> pack -> vehicle/system -> recycling
```

## System Boundary / 系统边界

Included:

- Electrode manufacturing / 电极制造
- Cell assembly / 电芯装配
- Cell finishing, formation, aging, testing, grading, and intralogistics / 电芯后处理、化成、老化、测试、分选和厂内物流
- Industrial robots / 工业机器人
- Collaborative robots / 协作机器人
- Mobile robots such as AGVs and AMRs / AGV、AMR 等移动机器人
- Vision-guided handling and inspection systems / 视觉引导搬运和检测系统

Excluded for now:

- Battery pack assembly / 电池包装配
- Battery recycling and disassembly / 电池回收和拆解
- Detailed robot control algorithms / 具体机器人控制算法
- Detailed electrochemical cell design / 详细电化学电芯设计
- Full factory simulation / 完整工厂仿真

Why exclude these? / 为什么先排除？

Because the topic is already broad. If the thesis includes pack assembly, recycling, robot control, and electrochemical design at the same time, the scope becomes too large and the analysis will become shallow.

因为这个课题本身已经很大。如果同时写电池包、回收、机器人控制算法和电化学设计，范围会失控，最后容易变成泛泛而谈。

## Main Research Objective / 主要研究目标

The objective is to analyze and evaluate where robotic systems can create value in battery cell manufacturing and how selected use cases can be implemented in industrial environments.

中文理解：

本论文要分析机器人系统在电芯制造哪些环节能创造价值，并评价选定应用场景在工业环境中如何落地。

In simple words / 人话版本：

```text
Where can robots be useful in battery cell manufacturing?
机器人在电芯制造哪里有用？

Which applications are worth doing?
哪些应用值得做？

How can they be implemented in real factories?
它们怎么在真实工厂里落地？
```

## Draft Research Questions / 初版研究问题

1. Which process steps in lithium-ion battery cell manufacturing are suitable for robotic automation?
   哪些锂离子电芯制造工序适合机器人自动化？

2. What technical and environmental requirements must robotic systems satisfy in battery cell production?
   机器人系统在电芯生产中必须满足哪些技术和环境要求？

3. Which robotic use cases offer the highest potential regarding quality, efficiency, cost, and scalability?
   哪些机器人应用场景在质量、效率、成本和可扩展性方面潜力最高？

4. How do different robotic systems, such as industrial robots, collaborative robots, and mobile robots, fit different production tasks?
   工业机器人、协作机器人、移动机器人等不同系统分别适合哪些生产任务？

5. What implementation strategies can support successful industrial deployment of robotics in battery manufacturing?
   哪些实施策略可以支持机器人在电池制造中的工业落地？

## Possible Evaluation Dimensions / 可能的评价维度

- Automation potential / 自动化潜力：这个任务是否重复、标准化、适合自动化？
- Technical feasibility / 技术可行性：机器人是否能稳定完成动作和精度要求？
- Quality impact / 质量影响：是否能减少缺陷、提高一致性？
- Economic potential / 经济潜力：是否能降低人工、废品、停机或物流成本？
- Scalability / 可扩展性：是否能从试点扩展到大规模量产？
- Integration complexity / 集成复杂度：是否难以接入现有设备、产线、MES 或安全系统？
- Safety and environmental compatibility / 安全和环境兼容性：是否适应干房、洁净度、防静电和化学安全要求？
- Data integration and traceability potential / 数据集成和追溯潜力：是否能产生和连接有用的生产数据？

## Key Terms / 核心术语

See `glossary_cn_en.md`.

见 `glossary_cn_en.md`。

## First Working Hypothesis / 初步研究假设

Robotics will not have the same value in every battery manufacturing step. The highest near-term implementation potential is likely in intralogistics, tray handling, automated loading/unloading, testing, sorting, and quality inspection. More delicate assembly tasks, such as stacking and housing insertion, may have high technical potential but also higher implementation difficulty.

机器人在每个电池制造工序中的价值并不一样。短期内最容易落地的方向可能是厂内物流、托盘搬运、自动上下料、测试、分选和质量检测。叠片、入壳等精细装配任务技术潜力高，但落地难度也更高。
