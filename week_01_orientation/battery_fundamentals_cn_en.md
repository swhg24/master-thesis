# Battery Fundamentals CN-EN / 锂离子电池基础中英对照

Purpose:

This file builds the minimum battery knowledge needed for the robotics-in-battery-manufacturing thesis.

目的：

这个文件不是深入电化学，而是建立研究机器人电池制造所必需的电池基础。

## 1. What Is a Lithium-Ion Battery Cell? / 什么是锂离子电芯？

A lithium-ion battery cell stores and releases energy through the movement of lithium ions between two electrodes.

锂离子电芯通过锂离子在两个电极之间往返移动来储存和释放能量。

Main components:

主要组成：

| Component / 部件 | 中文 | Function / 作用 | Manufacturing relevance / 制造相关性 |
| --- | --- | --- | --- |
| Anode | 负极 | Stores lithium during charging; usually graphite-based. / 充电时储存锂，通常以石墨为主。 | Needs coating, drying, calendering, precise electrode quality. / 需要涂布、干燥、辊压和稳定质量。 |
| Cathode | 正极 | Provides lithium source; often NMC, LFP, LCO, etc. / 提供锂源，常见材料有 NMC、LFP、LCO 等。 | Cathode material affects cost, safety, energy density. / 正极材料影响成本、安全和能量密度。 |
| Separator | 隔膜 | Physically separates anode and cathode while allowing ion transport. / 隔开正负极，同时允许锂离子通过。 | Thin and delicate; difficult for robotic handling. / 很薄很敏感，机器人搬运难。 |
| Electrolyte | 电解液 | Allows lithium ions to move between electrodes. / 让锂离子在正负极之间移动。 | Moisture-sensitive; filling needs dry room. / 怕水，注液需要干房。 |
| Current collector | 集流体 | Conducts electrons from electrodes to external circuit. / 把电子从电极导到外部电路。 | Usually copper for anode and aluminum for cathode. / 负极常用铜箔，正极常用铝箔。 |
| Housing | 壳体/封装 | Mechanically protects and seals the cell. / 保护并密封电芯。 | Format-dependent handling: pouch, cylindrical, prismatic. / 搬运方式取决于软包、圆柱或方形。 |

## 2. Charging and Discharging / 充电和放电

During discharge:

放电时：

```text
Lithium ions move from anode to cathode through electrolyte.
锂离子通过电解液从负极移动到正极。

Electrons move through the external circuit and provide power.
电子通过外部电路流动，对外供电。
```

During charge:

充电时：

```text
Lithium ions move from cathode back to anode.
锂离子从正极回到负极。

External electrical energy is stored as chemical energy.
外部电能被储存为化学能。
```

Simple memory:

简单记忆：

```text
Ions move inside the cell.
离子在电芯内部走。

Electrons move outside through the circuit.
电子在外部电路走。
```

## 3. Why Electrodes Matter / 为什么电极很重要？

Electrodes determine a large part of battery performance:

电极很大程度上决定电池性能：

- energy density / 能量密度
- power capability / 功率能力
- lifetime / 寿命
- safety / 安全
- cost / 成本

Manufacturing implications:

制造含义：

- Coating thickness must be uniform. / 涂层厚度要均匀。
- Electrode porosity and density must be controlled. / 孔隙率和密度要控制。
- Cracks, particles, and burrs can cause defects. / 裂纹、颗粒、毛刺会造成缺陷。
- Drying and calendering affect microstructure. / 干燥和辊压影响微观结构。

Robotics implication:

机器人含义：

Robots may support electrode manufacturing mainly through roll handling, sampling, inspection, and logistics rather than replacing coating or calendering equipment.

机器人在电极制造中的作用更多是卷材搬运、取样、检测和物流，而不是替代涂布机或辊压机。

## 4. What Is SEI? / 什么是 SEI？

SEI = Solid Electrolyte Interphase.

SEI = 固态电解质界面膜。

It is a thin layer formed mainly on the anode surface during the first charging cycles.

它主要在第一次充电过程中形成于负极表面。

Why it matters:

为什么重要：

- It protects the electrode surface. / 保护电极表面。
- It affects battery lifetime. / 影响电池寿命。
- It affects safety and efficiency. / 影响安全和效率。
- It is strongly linked to formation. / 与化成工序强相关。

Manufacturing implication:

制造含义：

Formation is not just "charging the cell". It is a quality-critical process that helps create a stable interphase.

化成不是简单给电池充电，而是帮助形成稳定界面的质量关键工序。

Robotics implication:

机器人含义：

Formation involves many sealed cells, trays, test channels, long process time, and traceability. This makes formation tray handling a strong robotics use case.

化成涉及大量密封电芯、托盘、测试通道、长时间过程和追溯，因此化成托盘搬运是很强的机器人应用案例。

## 5. Cell Formats / 电芯形式

Different cell formats lead to different manufacturing and robotic handling requirements.

不同电芯形式会导致不同制造和机器人搬运要求。

| Format / 形式 | 中文 | Characteristics / 特点 | Robotics relevance / 机器人相关性 |
| --- | --- | --- | --- |
| Coin cell | 扣式电池 | Small lab-scale format. / 小型实验室电芯。 | Useful for research, not main industrial production focus. / 适合科研，不是量产主线。 |
| Pouch cell | 软包电芯 | Flexible pouch packaging, high packaging efficiency. / 软包装，封装效率高。 | Soft and deformable; handling is difficult. / 软且易变形，搬运难。 |
| Cylindrical cell | 圆柱电芯 | Rigid metal can, standardized shape. / 金属壳，形状标准。 | Easier to grip and sort; high-volume automation common. / 更易抓取和分选，适合大批量自动化。 |
| Prismatic cell | 方形电芯 | Rigid rectangular housing, large format. / 方形硬壳，尺寸较大。 | Requires strong fixtures and precise orientation. / 需要可靠夹具和方向定位。 |

Thesis implication:

论文含义：

When discussing a robotic use case, specify the cell format whenever possible. A solution for cylindrical cells may not work for pouch cells.

讨论机器人应用时尽量说明电芯形式。适合圆柱电芯的方案不一定适合软包电芯。

## 6. Why Dry Room Matters / 为什么干房重要？

Some battery materials and processes are moisture-sensitive, especially electrolyte filling and later cell assembly steps.

一些电池材料和工序对水分敏感，尤其是注液和后续装配环节。

Dry room means:

干房意味着：

- very low humidity / 极低湿度
- high operating cost / 运行成本高
- strict equipment compatibility / 设备兼容要求高
- reduced human access preferred / 尽量减少人工进入

Robotics implication:

机器人含义：

Robots can reduce human traffic in dry rooms, but the robots themselves must be compatible with dry, clean, and often ESD-sensitive environments.

机器人可以减少人员进入干房，但机器人本身必须适应低湿、洁净和防静电环境。

## 7. Why Quality Control Matters / 为什么质量控制重要？

Battery defects can affect performance, lifetime, and safety.

电池缺陷会影响性能、寿命和安全。

Typical defect sources:

常见缺陷来源：

- coating defects / 涂布缺陷
- particles / 颗粒
- burrs / 毛刺
- misalignment / 错位
- weld defects / 焊接缺陷
- leakage / 泄漏
- abnormal formation behavior / 化成异常

Robotics implication:

机器人含义：

Robotics in battery manufacturing should often be combined with inspection and data tracking. A robot that moves cells without recording quality data is less valuable than a robot integrated with inspection and traceability.

电池制造中的机器人最好和检测、数据追踪结合。只搬运但不记录质量数据的机器人，价值不如能和检测及追溯系统集成的机器人。

## 8. Key Learning Bridge / 核心学习桥梁

This is the connection between battery fundamentals and the thesis topic:

这是电池基础和论文课题之间的连接：

| Battery fact / 电池事实 | Manufacturing requirement / 制造要求 | Robotics opportunity / 机器人机会 |
| --- | --- | --- |
| Electrodes are quality-critical. / 电极质量关键。 | Precise coating, drying, calendering, inspection. / 精密涂布、干燥、辊压、检测。 | Roll handling, sampling, visual inspection support. / 卷材搬运、取样、视觉检测辅助。 |
| Separator is thin and fragile. / 隔膜薄且脆弱。 | Gentle handling and accurate alignment. / 温和搬运和精确对齐。 | Vision-guided handling, special grippers. / 视觉引导搬运和专用夹爪。 |
| Electrolyte is moisture-sensitive. / 电解液怕水。 | Dry room and clean handling. / 干房和洁净搬运。 | Dry-room-compatible robots, reduced manual traffic. / 干房机器人、减少人工进入。 |
| SEI forms during formation. / SEI 在化成中形成。 | Formation process must be controlled and traceable. / 化成过程要受控且可追溯。 | Tray handling, automated loading, data-linked logistics. / 托盘搬运、自动上下料、数据化物流。 |
| Different cell formats behave differently. / 不同电芯形式差异大。 | Fixtures and handling differ. / 夹具和搬运方式不同。 | Use-case-specific robot design. / 针对具体案例设计机器人方案。 |

## 9. Minimum Vocabulary Checklist / 最小词汇清单

You should be comfortable with these terms before deep robotics analysis:

深入机器人分析前，应先熟悉这些词：

- anode / 负极
- cathode / 正极
- separator / 隔膜
- electrolyte / 电解液
- current collector / 集流体
- pouch cell / 软包电芯
- cylindrical cell / 圆柱电芯
- prismatic cell / 方形电芯
- SEI / 固态电解质界面膜
- formation / 化成
- aging / 老化
- dry room / 干房
- coating / 涂布
- calendering / 辊压
- slitting / 分切
- traceability / 可追溯性
