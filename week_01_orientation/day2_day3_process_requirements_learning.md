# Day 2-3 Learning Note: Process Chain + Requirements

Day 2-3 goal:

把电芯制造流程和工序要求连起来理解。

In simple words:

```text
What is the process?
这个工序在做什么？

Why is it difficult?
它难在哪里？

Where can robotics help?
机器人在哪里可能有用？
```

## 0. Big Picture / 总图

Battery cell manufacturing can be understood as three connected stages:

电芯制造可以理解成三个连续阶段：

```text
1. Electrode manufacturing 电极制造
   Make anode and cathode sheets.
   做正极片和负极片。

2. Cell assembly 电芯装配
   Assemble electrodes, separator, electrolyte, and housing into a cell.
   把电极、隔膜、电解液、壳体组装成电芯。

3. Cell finishing 电芯后处理
   Activate, stabilize, test, and sort the cell.
   对电芯进行化成、老化、测试和分选。
```

## 1. Electrode Manufacturing / 电极制造

### Main Story / 主线

Electrode manufacturing turns powder-like raw materials into long, coated electrode rolls.

电极制造就是把粉末状原材料做成长卷状的电极片。

```text
Mixing 混料
  -> Coating 涂布
  -> Drying 干燥
  -> Calendering 辊压
  -> Slitting 分切
  -> Vacuum drying 真空干燥
```

### Process-by-Process Understanding / 分工序理解

| Step / 工序 | What happens? / 做什么 | Why difficult? / 难在哪里 | Robotics relevance / 机器人相关性 |
| --- | --- | --- | --- |
| Mixing / 混料 | Powders and liquids are mixed into slurry. / 粉末和液体混成浆料。 | Dust, recipe accuracy, contamination. / 粉尘、配方准确性、污染控制。 | Material feeding, container handling. / 原料投放、容器搬运。 |
| Coating / 涂布 | Slurry is coated onto copper/aluminum foil. / 浆料涂到铜箔或铝箔上。 | Uniform thickness, continuous web, defects. / 厚度均匀、连续卷材、缺陷控制。 | Roll handling, sampling, inspection support. / 卷材搬运、取样、检测辅助。 |
| Drying / 干燥 | Solvent or water is removed. / 去除溶剂或水分。 | Temperature control, cracking risk. / 温度控制、开裂风险。 | Limited direct role. / 机器人直接作用有限。 |
| Calendering / 辊压 | Electrode is compressed to target thickness and density. / 压实电极，控制厚度和密度。 | Mechanical pressure, thickness uniformity. / 压力控制、厚度一致性。 | Roll loading/unloading. / 卷材上下料。 |
| Slitting / 分切 | Wide electrode roll is cut into narrow rolls. / 宽卷切成窄卷。 | Burrs, particles, edge quality. / 毛刺、颗粒、边缘质量。 | Roll handling, sample inspection. / 卷材搬运、样品检测。 |
| Vacuum drying / 真空干燥 | Residual moisture is reduced. / 进一步去除残余水分。 | Moisture sensitivity, dry environment. / 水分敏感、干燥环境。 | Automated loading/unloading. / 自动上下料。 |

### Robotics Takeaway / 机器人判断

Electrode manufacturing is dominated by specialized process equipment. Robots are useful mainly around the process, not inside the core process.

电极制造主要由专用工艺设备主导。机器人更多在外围有用，而不是直接替代核心工艺设备。

Good robotics candidates:

- Roll transport / 卷材运输
- Roll loading and unloading / 卷材上下料
- Sampling / 取样
- Inline inspection support / 在线检测辅助
- Material logistics / 物料物流

## 2. Cell Assembly / 电芯装配

### Main Story / 主线

Cell assembly turns electrode rolls or sheets into a sealed cell.

电芯装配就是把电极卷或电极片变成密封电芯。

```text
Notching/Cutting 模切/裁切
  -> Stacking or Winding 叠片或卷绕
  -> Tab welding 极耳焊接
  -> Housing insertion 入壳
  -> Electrolyte filling 注液
  -> Sealing 封口
```

### Process-by-Process Understanding / 分工序理解

| Step / 工序 | What happens? / 做什么 | Why difficult? / 难在哪里 | Robotics relevance / 机器人相关性 |
| --- | --- | --- | --- |
| Notching/Cutting / 模切或裁切 | Electrodes are cut into required shapes. / 极片切成需要的形状。 | Burrs, particles, geometry accuracy. / 毛刺、颗粒、几何精度。 | Machine loading, inspection. / 设备上下料、检测。 |
| Stacking / 叠片 | Anode, separator, cathode are stacked layer by layer. / 正极、隔膜、负极一层层叠起来。 | Thin materials, alignment accuracy, speed. / 材料薄、对齐精度高、速度要求高。 | Vision-guided handling and alignment. / 视觉引导搬运和对齐。 |
| Winding / 卷绕 | Electrode and separator are wound into a roll. / 电极和隔膜卷成卷芯。 | Tension control, high-speed integration. / 张力控制、高速集成。 | Mostly process-machine support. / 多为专用设备辅助。 |
| Tab welding / 极耳焊接 | Electrical tabs are welded. / 焊接导电极耳。 | Weld quality, thermal effects, positioning. / 焊接质量、热影响、定位。 | Positioning, weld inspection. / 定位、焊点检测。 |
| Housing insertion / 入壳 | Cell core is inserted into pouch/can/prismatic housing. / 电芯核心放入软包、圆柱壳或方壳。 | Deformation, tight tolerances, format dependency. / 易变形、公差紧、受电芯形式影响。 | Pick-and-place, fixture loading. / 抓取放置、夹具上料。 |
| Electrolyte filling / 注液 | Electrolyte is dosed into the cell. / 向电芯注入电解液。 | Dry room, chemical safety, dosing accuracy. / 干房、化学安全、剂量准确。 | Loading/unloading around filling equipment. / 注液设备周边上下料。 |
| Sealing / 封口 | Cell is sealed. / 电芯密封。 | Leak-tightness, contamination, quality inspection. / 密封性、污染、质量检测。 | Positioning, post-seal inspection. / 定位、封口后检测。 |

### Robotics Takeaway / 机器人判断

Cell assembly has high robotics potential, but also high technical difficulty.

电芯装配的机器人潜力很高，但技术难度也高。

Good robotics candidates:

- Vision-guided stacking support / 视觉引导叠片辅助
- Tab welding positioning and inspection / 极耳焊接定位和检测
- Housing insertion / 入壳
- Loading/unloading for filling and sealing / 注液和封口上下料

Main risks:

- Thin and flexible materials / 薄而柔软的材料
- High alignment accuracy / 高对齐精度
- Dry room and contamination control / 干房和污染控制
- High cycle time requirements / 高节拍要求

## 3. Cell Finishing / 电芯后处理

### Main Story / 主线

Cell finishing turns a sealed cell into a qualified and classified product.

电芯后处理就是把密封电芯变成合格且完成分类的产品。

```text
Formation 化成
  -> Aging 老化
  -> Testing 测试
  -> Grading/Sorting 分级/分选
  -> Packaging/Logistics 包装/物流
```

### Process-by-Process Understanding / 分工序理解

| Step / 工序 | What happens? / 做什么 | Why difficult? / 难在哪里 | Robotics relevance / 机器人相关性 |
| --- | --- | --- | --- |
| Formation / 化成 | First controlled charge/discharge cycles activate the cell. / 第一次受控充放电，激活电芯。 | Long process time, many cells, safety, traceability. / 时间长、电芯多、安全和追溯要求高。 | Tray loading/unloading, AMR transport. / 托盘上下料、AMR 运输。 |
| Aging / 老化 | Cells rest under controlled conditions. / 电芯静置，观察稳定性。 | Large storage area, inventory tracking. / 占地大、库存追踪复杂。 | Automated storage, AGV/AMR logistics. / 自动存取、AGV/AMR 物流。 |
| Testing / 测试 | Electrical and visual properties are measured. / 测容量、电压、内阻、外观等。 | High volume, data connection, quality reliability. / 数量大、数据连接、质量可靠性。 | Automated test loading, inspection. / 自动测试上下料、检测。 |
| Grading/Sorting / 分级或分选 | Cells are sorted into quality classes. / 电芯按质量和性能分类。 | Fast decision-making, traceability. / 快速判断、可追溯。 | Robot sorting, barcode/data handling. / 机器人分选、条码和数据处理。 |
| Packaging/Logistics / 包装或物流 | Cells are buffered or moved to next stage. / 电芯缓存或送到下游。 | Material flow stability. / 物流稳定性。 | AMR/AGV, automated buffering. / AMR/AGV、自动缓存。 |

### Robotics Takeaway / 机器人判断

Cell finishing is one of the most promising areas for near-term robotic implementation.

电芯后处理是短期内最有机器人落地潜力的区域之一。

Why:

- Cells are already sealed and easier to handle. / 电芯已经密封，更容易搬运。
- Products can be placed in standardized trays. / 可以用标准托盘承载。
- Processes are repetitive and high-volume. / 工序重复、大批量。
- Traceability and data integration are valuable. / 可追溯和数据集成价值高。

Good robotics candidates:

- Formation tray handling / 化成托盘搬运
- Aging logistics / 老化物流
- Test station loading/unloading / 测试工位上下料
- Sorting after grading / 分级后分选
- AMR/AGV intralogistics / AMR/AGV 厂内物流

## 4. Cross-Process Requirements / 跨工序共性要求

These requirements appear repeatedly across the process chain.

这些要求会反复出现在不同工序中。

| Requirement / 要求 | Meaning / 含义 | Why it matters for robotics / 为什么影响机器人 |
| --- | --- | --- |
| Dry room compatibility / 干房兼容性 | Equipment must work in very low humidity. / 设备要能在低湿度环境运行。 | Lubrication, static electricity, maintenance, material aging. / 润滑、静电、维护、材料老化都会受影响。 |
| Contamination control / 污染控制 | Avoid particles, oil, dust, moisture. / 避免颗粒、油污、灰尘、水分。 | Robot grippers, cables, and moving parts may generate contamination. / 夹爪、电缆、运动部件可能带来污染。 |
| Delicate material handling / 精细材料搬运 | Handle thin and sensitive materials gently. / 温和处理薄而敏感的材料。 | Wrong gripping can damage electrodes or separators. / 抓取不当会损伤极片或隔膜。 |
| Precision positioning / 精密定位 | Place parts accurately and repeatably. / 准确、重复地放置部件。 | Stacking, welding, and insertion need high accuracy. / 叠片、焊接、入壳需要高精度。 |
| Cycle time / 节拍 | Process speed per unit. / 单件处理速度。 | Robot must not become the bottleneck. / 机器人不能成为产线瓶颈。 |
| Safety / 安全 | Protect people, products, and equipment. / 保护人员、产品和设备。 | Battery cells, electrolyte, and high-power equipment create risks. / 电芯、电解液和高功率设备有风险。 |
| Traceability / 可追溯性 | Link each cell to process and quality data. / 每个电芯关联工艺和质量数据。 | Robots should connect to MES, barcode, and inspection data. / 机器人应连接 MES、条码和检测数据。 |

## 5. First Case Selection Logic / 初步案例选择逻辑

For the thesis, not every use case should be studied equally deeply.

论文里不需要平均研究每一个机器人应用。应该先广泛扫描，再选择重点案例。

| Potential / 潜力 | Difficulty / 难度 | Meaning / 含义 |
| --- | --- | --- |
| High | Medium | Strong candidate for detailed analysis. / 很适合作为重点案例。 |
| High | High | Technically interesting, but risky. / 有技术深度，但风险较高。 |
| Medium | Medium | Useful as supporting case. / 可作为辅助案例。 |
| Medium | High | Usually not first priority. / 通常不是第一优先级。 |

Recommended first focus:

建议第一批重点关注：

1. AMR/AGV intralogistics / AMR/AGV 厂内物流
2. Formation and testing tray handling / 化成和测试托盘搬运
3. Vision-guided inspection and loading/unloading / 视觉检测与上下料

These three are balanced: logistics, production handling, and quality/data.

这三个方向比较平衡：一个偏物流，一个偏生产搬运，一个偏质量和数据。
