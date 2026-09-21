# Pack EoL 现实设备基线：运输方式与接线方式必须拆开

> 日期：2026-09-20  
> 性质：same-task industry baseline learning note  
> 证据身份：官方设备商资料；可支持所披露方案和配置存在，不能替代同行评审性能证据或目标工厂数据。

## 1. 为什么这是架构比较的关键一步

Week 06 容易把选择写成：

```text
专用自动化 vs 固定工业机器人 vs 人形/移动双臂
```

现实 Pack EoL 设备表明，这个分类还不够精确。一个测试单元至少有两个可独立选择的子系统：

```text
Pack transportation / positioning
×
electrical and communication connector adaptation
```

因此，同一个站可能是：

- AGV 运输 + 人工接线；
- AGV 运输 + 自动接触单元；
- 输送线运输 + 自动高压/通信接线；
- 小车人工上料 + 人工接线；
- 固定机器人或移动操作系统 + 柔性接插件操作。

如果不拆开这两个轴，就会错误地把“AGV”“自动接线”和“移动机器人操作”当成同一件事。

## 2. Baseline A：Marposs 的 Pack EoL 配置族

官方 Pack electrical-test 页面披露：

- 半自动方案由操作员连接和断开；
- 全自动方案可以由 AGV 搬运 Pack，并在无人介入下完成 wiring；
- 产品版本明确区分 manual/automatic part handling 与 manual/automatic power-and-signal cable connection；
- 示例测试舱把连接安全、电路开断、热监测、防火、测试、CAN 日志和数据记录放在同一系统边界内。

来源：<https://www.marposs.com/eng/application/electrical-test-battery-pack>

这直接告诉我们：

1. 人工接线和自动接线都是现实 Pack EoL baseline；
2. `handling` 与 `connection` 是两个独立配置决策；
3. 连接器操作不能脱离测试舱安全、测试功能和数据记录单独评价；
4. 官方页面给出的 3–30 min 是 pulse-power test cycle 范围，不是连接器插拔节拍，不能用于机器人动作比较。

## 3. Baseline B：thyssenkrupp 的三种上料/接线组合

thyssenkrupp System Engineering 的 Battery End of Line test 资料在同一页列出：

| Pack 上料方式 | 接线方式 | 其他公开特征 |
| --- | --- | --- |
| friction roller conveyor + pallet | high-voltage 和 communication plug 自动连接 | 自动适配、充电循环、flashing、标准测量柜 |
| AGV | high-voltage 和 communication plug 可用人工或自动 adaptation unit | 围栏、门和区域监控；可设 pre-test stop |
| trolley 手动上料 | high-voltage 和 communication plug 人工连接 | 安全防护；一个 test stand 可有多个 test places |

来源：<https://ucpcdn.thyssenkrupp.com/_legacy/UCPthyssenkruppBAISSystemEngineering/assets.files/automobilindustrie/future-automotive-factory/tech-days/06_testingsolutions.pdf>，PDF p.3。

另一份官方资料还把产品范围写成“manual loading and manual electrical connections up to full automatic test equipment”，说明方案选择本来就是连续谱，而不是机器人/非机器人二分。

来源：<https://ucpcdn.thyssenkrupp.com/_legacy/UCPthyssenkruppBAISSystemEngineering/assets.files/automobilindustrie/testsysteme/eol-test-for-battery_en.pdf>，PDF p.2。

## 4. 对论文分类方式的修正

Framework v1.0 不应只记录一个 `architecture_category`，至少应拆成下面五层：

| 层 | 示例值 |
| --- | --- |
| transport architecture | trolley / conveyor / AGV / AMR |
| Pack positioning | pallet datum / fixture / vision-corrected pose |
| connector adaptation | manual / dedicated automatic contact / fixed robot / mobile manipulator |
| test and safety cell | open assisted station / guarded station / enclosed automatic cabin |
| information architecture | tester-local / PLC-cell control / production-database or MES integration |

这会产生一个重要方法优势：

> 我们可以比较“同一个连接任务由什么 connector-adaptation configuration 完成”，而不是把整条产线所有子系统都归因于机器人形态。

## 5. 对三类候选配置的重新理解

### 专用自动接触机构

它的优势可能来自：Pack 和接口通过 pallet/fixture 被高重复定位，自动 adaptation unit 只需要完成受约束的接触动作。它可以与 conveyor 或 AGV 任一运输方式组合，也可以具备 PLC、安全和状态确认。

因此不能再写“专机没有感知、恢复或灵活性”。必须查具体 adaptation unit 怎样定位、确认和换型。

### 固定工业机器人单元

它改变的是 connector-adaptation layer，而不一定改变 Pack transportation、tester 或 MES。它可能比专用接触机构处理更大的接口位姿变化，但也可能引入更复杂的工具、感知和恢复需求。

### 移动/双臂/人形系统

它同时可能影响 transport/workspace 和 connector manipulation，但只有在机器人确实跨站移动、复用任务或利用双臂管理线束时，这些自由度才形成选择价值。若 Pack 已由 AGV 送到固定测试舱、接插件也在固定位置，移动底盘可能没有被任务利用。

## 6. 我们现在能下的结论

`RETAIN DIRECT AS INDUSTRY BASELINE`：

- Pack EoL 存在人工接线、自动接线以及不同 Pack 运输方式的公开设备方案；
- Pack transportation 与 connector adaptation 可以独立组合；
- 自动接线并不等于必须使用通用机器人；
- AGV 上料也不等于必须使用移动操作机器人。

`UNKNOWN / NOT YET COMPARABLE`：

- 自动 adaptation unit 的内部机构、允许接口变型和换型时间；
- 与固定机器人或移动双臂完成同一任务时的节拍、介入率、可用率和成本；
- CATL/Spirit AI 目标工位采用哪一种 Pack transport、fixture、test cabin 和控制拓扑；
- 人形系统的移动性和双臂在该工位是否真实产生了系统收益。

## 7. 下一步怎样使用这项知识

Framework v1.0 的 configuration card 应先拆分 transport、positioning、connector adaptation、safety/test cell 和 information architecture，再评价 R1–R6。随后建立三个同边界 baseline cards：

1. manual connector adaptation；
2. dedicated automatic adaptation；
3. configured robot manipulation。

固定机器人和移动/双臂系统只在第三类内部继续比较。这样比较对象才处于同一个功能层级。

