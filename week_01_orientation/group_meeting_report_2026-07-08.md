# Group Meeting Report / 组会报告

Date: 2026-07-08  
Student: Fuhan Liao  
Topic: Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies

## 1. Current Understanding of the Thesis Topic / 当前课题理解

The thesis investigates how robotic systems can be applied along the lithium-ion battery cell manufacturing value chain. The focus is not on designing a robot controller, but on identifying promising application areas, evaluating their technical and economic potential, and developing implementation strategies for industrial battery manufacturing.

本课题研究机器人系统如何应用于锂离子电芯制造价值链。重点不是设计机器人控制算法，而是识别有潜力的应用场景，评价其技术和经济价值，并提出工业落地策略。

The current working scope is:

```text
Electrode manufacturing 电极制造
  -> Cell assembly 电芯装配
  -> Cell finishing 电芯后处理
  -> Intralogistics 厂内物流
```

Excluded for now:

- Battery pack assembly / 电池包装配
- Battery recycling / 电池回收
- Detailed robot control algorithms / 机器人控制算法细节
- Detailed electrochemical cell design / 详细电化学设计

## 2. Supervisor Input and Updated Learning Direction / 导师建议与学习方向调整

The supervisor recommended starting with lithium-ion battery fundamentals before moving deeper into robotics-specific topics. This is important because many robotic implementation challenges come directly from battery materials and manufacturing requirements.

导师建议先学习锂离子电池基础，再进入机器人应用。这很重要，因为机器人落地难点很多来自电池材料和制造工艺本身。

Recommended topics:

- Operating principles of lithium-ion batteries / 锂离子电池工作原理
- Cell components: anode, cathode, separator, electrolyte / 电芯组成：负极、正极、隔膜、电解液
- Cell formats: coin, pouch, cylindrical, prismatic / 电芯形式：扣式、软包、圆柱、方形
- Electrode manufacturing: slurry mixing, coating, drying, calendering / 电极制造：混料、涂布、干燥、辊压
- Cell assembly / 电芯装配
- Formation and aging / 化成与老化
- Battery manufacturing processes and quality control / 电池制造过程和质量控制

Key learning bridge:

```text
Battery fundamentals
  -> Process requirements
  -> Robotics opportunities
  -> Implementation strategy
```

Example:

```text
Electrolyte is moisture-sensitive
  -> dry room is required
  -> manual access should be reduced
  -> dry-room-compatible robots and AMRs become relevant
```

## 3. Battery Manufacturing Process Chain / 电芯制造流程链

The cell manufacturing process can be divided into three main stages.

### 3.1 Electrode Manufacturing / 电极制造

Main process:

```text
Mixing 混料
  -> Coating 涂布
  -> Drying 干燥
  -> Calendering 辊压
  -> Slitting 分切
  -> Vacuum drying 真空干燥
```

Interpretation:

Electrode manufacturing is quality-critical and strongly affects cell performance. However, the core process is usually dominated by specialized continuous process equipment. Robotics is mainly relevant for surrounding tasks such as material feeding, roll handling, sampling, inspection support, and logistics.

电极制造对电芯性能非常关键，但核心过程通常由连续化专用设备主导。机器人主要在外围任务中有价值，例如物料投放、卷材搬运、取样、检测辅助和物流。

### 3.2 Cell Assembly / 电芯装配

Main process:

```text
Notching/Cutting 模切/裁切
  -> Stacking or Winding 叠片或卷绕
  -> Tab welding 极耳焊接
  -> Housing insertion 入壳
  -> Electrolyte filling 注液
  -> Sealing 封口
```

Interpretation:

Cell assembly has high robotics potential because it involves handling, positioning, joining, and inspection. However, implementation is challenging due to thin electrodes, flexible separators, dry room conditions, contamination control, and high alignment accuracy.

电芯装配中有大量搬运、定位、连接和检测任务，因此机器人潜力高。但由于极片薄、隔膜软、干房环境、污染控制和高精度对齐要求，落地难度也较高。

### 3.3 Cell Finishing / 电芯后处理

Main process:

```text
Formation 化成
  -> Aging 老化
  -> Testing 测试
  -> Grading/Sorting 分级/分选
  -> Packaging/Logistics 包装/物流
```

Interpretation:

Cell finishing is currently one of the most promising areas for robotic implementation. Cells are already sealed, usually handled in standardized trays, and the process involves high-volume repetitive logistics, testing, sorting, and traceability.

电芯后处理是当前最有机器人落地潜力的区域之一。此时电芯已经封装，通常以标准托盘承载，流程中有大量重复物流、测试、分选和追溯需求。

## 4. Key Manufacturing Requirements for Robotics / 影响机器人的关键制造要求

| Requirement | 中文 | Relevance for Robotics |
| --- | --- | --- |
| Dry room compatibility | 干房兼容性 | Robots must operate reliably in low-humidity environments. |
| Contamination control | 污染控制 | Robots, grippers, cables, and moving parts must not introduce particles or oil. |
| Delicate material handling | 精细材料搬运 | Electrodes and separators are thin, flexible, and damage-sensitive. |
| Precision positioning | 精密定位 | Stacking, welding, and insertion require accurate and repeatable placement. |
| Cycle time | 节拍 | Robots must not become production bottlenecks. |
| Safety | 安全 | Battery cells, electrolyte, high-power equipment, and human-robot interaction create safety requirements. |
| Traceability | 可追溯性 | Robots should connect handling actions with product IDs, quality data, and MES. |

## 5. Industry and Literature Signals / 工业与文献信号

### 5.1 CATL Smart Manufacturing / 宁德时代智能制造

CATL's official smart manufacturing information emphasizes AI, image recognition, machine learning, 5G, equipment interconnection, real-time quality control, and lifecycle traceability. CATL reports 95% production equipment interconnection, more than 7,000 quality control points monitored in real time, and long-term lifecycle quality tracking.

This indicates that robotics in battery manufacturing should be understood as part of an integrated intelligent manufacturing system, not as isolated robot arms.

Source: CATL Smart Manufacturing  
https://www.catl.com/en/manufacture/

### 5.2 CATL and Humanoid Robots / 宁德时代与人形机器人

CATL announced a strategic cooperation with Galbot in 2026 for smart manufacturing line upgrades and AI humanoid robot applications. The reported application is mainly in module and battery pack manufacturing, especially material handling and picking.

This is useful as a future trend, but not the core of the current thesis, because the thesis focuses on battery cell manufacturing.

Source: CATL News, 2026-06-24  
https://www.catl.com/en/news/6881.html

### 5.3 IFR World Robotics 2025 / 全球工业机器人背景

The IFR World Robotics 2025 Executive Summary reports 542,076 industrial robots installed globally in 2024 and an operational stock of 4,663,698 units. It also emphasizes that successful robot deployment depends not only on robots, but also on peripherals, vision, process design, and system integration.

This supports adding integration complexity, vision, process design, and system integration to the evaluation framework.

Source: IFR World Robotics 2025 Executive Summary  
https://ifr.org/img/worldrobotics/Executive_Summary_WR_2025_Industrial_Robots.pdf

## 6. Preliminary Process-to-Robotics Mapping / 初步工序-机器人映射

| Production Area | Strong Robotics Opportunities | Main Challenge | Initial Priority |
| --- | --- | --- | --- |
| Electrode manufacturing | Roll handling, sampling, inspection support, material logistics | Continuous process equipment, contamination, roll handling | Medium |
| Cell assembly | Vision-guided handling, stacking support, tab welding positioning, housing insertion | Thin/flexible materials, precision, dry room, cycle time | High but difficult |
| Cell finishing | Formation tray handling, test loading/unloading, sorting, AMR/AGV logistics | Equipment interface, traceability, scheduling | High |
| Intralogistics | AMR/AGV transport, tray flow, material supply, empty carrier return | Fleet management, MES integration, dry room compatibility | High |

## 7. Candidate Use Cases for Further Study / 后续重点案例

### Use Case 1: AMR/AGV Intralogistics

Why promising:

- Supports scalable material flow
- Reduces manual transport
- Relevant for dry room and sensitive production areas
- Strong connection to MES and traceability

### Use Case 2: Formation and Testing Tray Handling

Why promising:

- Cells are already sealed and easier to handle
- Standardized trays enable automation
- High-volume repetitive process
- Strong economic and traceability potential

### Use Case 3: Vision-Guided Inspection and Robot Loading

Why promising:

- Quality control is central in battery manufacturing
- Can combine robotics, machine vision, AI, and data integration
- Relevant for electrode inspection, weld inspection, cell surface inspection, and test loading

### Use Case 4: Vision-Guided Stacking or Housing Insertion

Why promising:

- Strong technical depth
- Direct link to cell assembly quality

Main risk:

- High difficulty due to thin materials, alignment accuracy, cycle time, and contamination control

## 8. Preliminary Research Questions / 初步研究问题

1. Which process steps in lithium-ion battery cell manufacturing are suitable for robotic automation?
2. What technical and environmental requirements must robotic systems satisfy in battery cell production?
3. Which robotic use cases offer the highest potential regarding quality, efficiency, cost, and scalability?
4. How do different robotic systems, such as industrial robots, collaborative robots, AMRs/AGVs, and vision-guided systems, fit different battery production tasks?
5. What implementation strategies can support successful industrial deployment of robotics in battery manufacturing?

## 9. Next Steps / 下一步计划

Short-term:

- Read supervisor-recommended battery fundamentals literature.
- Build a stronger glossary for battery components, cell formats, SEI, formation, and quality control.
- Verify the exact DOI/PDF of the two 2024 review papers recommended by the supervisor.
- Refine the process-to-robotics map based on literature.

Medium-term:

- Select 3 use cases for detailed evaluation.
- Build a semi-quantitative evaluation framework with dimensions such as automation potential, technical feasibility, quality impact, economic potential, scalability, integration complexity, safety, and traceability.
- Search for more industrial examples from battery manufacturers and robotics suppliers.

## 10. Questions for Discussion / 组会讨论问题

1. Should the thesis focus on one cell format, such as pouch, cylindrical, or prismatic cells?
2. Should the analysis include only battery cell manufacturing, or also adjacent module/pack examples as future trends?
3. Is a literature-based semi-quantitative evaluation sufficient, or should expert interviews/case studies be included?
4. Which use cases are most relevant for PEM/eLab or available industrial examples?
5. How detailed should the economic evaluation be?

## 11. Current Working Conclusion / 当前阶段结论

Robotic systems in battery cell manufacturing should not be treated as isolated machines replacing manual labor. A stronger framing is that robotic systems create value when integrated with process equipment, dry/clean production environments, vision-based quality control, material flow systems, and traceability infrastructure.

电芯制造中的机器人系统不应被理解为单纯替代人工的孤立设备。更准确的理解是：机器人系统只有与工艺设备、干燥/洁净环境、视觉质量控制、物料流系统和追溯基础设施集成时，才能真正创造价值。
