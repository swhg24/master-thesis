# Framework v1.0 输入：Pack EoL 任务、要求与判定字段

> 日期：2026-09-20  
> 状态：`FRAMEWORK INPUT — NOT YET FRAMEWORK v1.0 RESULT`  
> 来源：Week 06 任务原型 + Week 08 第一、二轮 claim audit

## 1. 本文件的作用

本文件把 Week 06 的描述性内容转换为下一阶段可以重复使用的评价字段。它不宣布任何架构胜出，也不把未知信息补成现场事实。

## 2. 统一分析单元

每个案例和每个候选配置必须先填写：

| 字段 | Pack EoL 当前值 |
| --- | --- |
| production level | `PACK` |
| lifecycle stage | `MANUFACTURING` |
| process | manufacturing end-of-line testing；DCR 暂为 adjacent |
| manipulated object | test connector + flexible harness；具体配置未知 |
| source state | connector/harness available but not connected；供料和姿态范围未知 |
| destination state | connection accepted for the required test；接受判据未知 |
| return state | safely disconnected and restored for Pack release/next cycle；归位方式未知 |
| actor boundary | physical connection/disconnection system；测试本体不属于 robot task |
| comparator set | manual reference where applicable；dedicated contact automation；configured fixed robot cell；configured mobile/dual-arm system |

## 3. Task Gate：任务是否定义完整

只有以下字段均可回答，候选配置才进入能力比较：

1. 操作对象；
2. 起始状态；
3. 目标状态；
4. 完成判据；
5. 关键失败后果；
6. robot 与 tester/fixture/controller 的责任边界。

若只能回答“机器人插接插件”，则 Task Gate 未通过。

## 4. Requirement fields：六组可审计问题

| ID | 应评价的变量 | 可接受证据 | 当前 Pack EoL 状态 | 不允许的默认推断 |
| --- | --- | --- | --- | --- |
| R1 | 接插件/线束初始状态变化；抓取后位姿变化；线束支撑、张力、缠绕、工作空间约束 | 目标工位/设备资料优先；直接公司披露可证明任务特征；相邻线束论文仅支持机制 | 柔性线束插拔存在；几何、刚度、供料、支撑、双臂需求未知 | 线束存在 ⇒ 必须双臂、完整 DLO 感知或张力闭环 |
| R2 | 预对准后的残余位姿误差；导向结构；允许力/力矩；卡滞检测和恢复 | 目标 connector 数据；同类插合实验；具体工具和控制配置 | 接触插合是合理评价维度；目标误差、力和几何未知 | 插接 ⇒ 必须六维 F/T 或某一算法；某论文参数可迁移 |
| R3 | 接口电气状态；动作许可；安全功能；故障响应；适用规范 | 制造设备/安全设计/标准/同配置资料；相邻电池 cell 仅作机制参考 | HV/electrical safety 相关；实际 safe sequence、HVIL、energization、责任未知 | 数百伏语境 ⇒ 已证明带电插拔；Week 06 PLC 时序是真实现场 |
| R4 | 产品和接口变型；变化频率；换型内容与资源；混线方式 | 生产组合和换型记录；设备变型能力；透明情景假设 | 多产品/灵活性为公司披露语境；型号数、接口差异和换型频率未知 | 多型号披露 ⇒ 已证明 connector 自动换型或跨工位优势 |
| R5 | 连接完成判据；判据所有者；false accept/false reject 后果；失败恢复 | 目标验收规范；设备/测试方案；直接状态检查披露；相邻电气接触检查 | connection-status inspection 存在；传感方式、阈值、锁止和重试未知 | 连接检查 ⇒ 必须四模态融合或由机器人独立决定 |
| R6 | ID/recipe/permission/result 的数据流；接口所有者；记录粒度；通信故障处理 | 工位架构、PLC/MES 接口和质量追溯文件 | EoL 需要身份—配方—结果闭环；目标拓扑和机器人直连关系未知 | Robot 必须直接连接 MES；参考泳道等于 CATL 现场 |

## 5. Production-condition fields：与任务能力分开评价

R4 主要属于生产条件。Framework v1.0 应进一步使用以下独立字段：

| ID | 条件 | 为什么改变架构选择 |
| --- | --- | --- |
| P1 | 产品/接口多样性 | 决定机械专用化、参数化和工具兼容的价值 |
| P2 | 变型频率与批量结构 | 决定换型时间与换型资源是否重要 |
| P3 | 产量、允许节拍和波动 | 决定单循环性能、缓冲和并行化需求 |
| P4 | 单工位或多工位任务组合 | 决定移动性和跨任务复用是否被实际利用 |
| P5 | greenfield / brownfield 与可改造空间 | 决定工装、围护、传感器和机器人布局的实施代价 |
| P6 | 可用率、维护与人工介入目标 | 决定复杂感知/控制带来的收益能否覆盖恢复和维护负担 |
| P7 | 产品生命周期与未来变更不确定性 | 决定固定投资与可重构性的长期价值 |

任何数值区间都必须有来源或明确写成 sensitivity assumption。Week 06 的 `1–2 / 3–5 / 5+` 不作为事实边界。

## 6. Configuration card：不再按类别名称猜能力

每个实际候选方案必须先拆成五个系统层：`transport architecture`、`Pack positioning`、`connector adaptation`、`test/safety cell`、`information architecture`。Pack 由 AGV 运输不代表接插件由移动机器人操作；输送线也可以搭配自动接触。随后填写配置卡：

| 能力域 | 必填问题 |
| --- | --- |
| localization | 对象和接口怎样定位？精度、遮挡和失败检测依据是什么？ |
| end effector | 抓取点、工具兼容范围、锁止/解锁动作怎样实现？ |
| uncertainty reduction | 哪些误差由 fixture/guide 消除，哪些由在线感知或柔顺处理？ |
| contact handling | 是否有被动/主动柔顺、力限制、接触检测和卡滞恢复？ |
| completion confirmation | 用什么信号确认机械/电气任务完成？谁作最终判定？ |
| safety integration | 许可、互锁、停止、故障和恢复怎样闭合？ |
| information integration | 参数从哪里来，结果到哪里去，通信失败怎样处理？ |
| workspace/mobility | 任务是否真正需要移动、多工位或双臂并行/协同？ |
| performance evidence | 节拍、成功率、介入率、可用率在什么配置和条件下测得？ |
| economic evidence | 投资、工程集成、换型、维护、占地和利用率有哪些透明输入？ |

`industrial robot`、`humanoid`、`dedicated automation`只描述架构族，不自动填充上述任何能力。

## 7. 四个 Gate 的 v1.0 输入规则

### Task Gate

任务、对象、状态转换、完成判据和责任边界不完整，则停止架构比较。

### Condition Gate

技术上能做但没有相应生产条件价值，只能判为“feasible but no demonstrated selection advantage”，不能判为更适合。

### Safety Gate

若目标安全功能已知而配置明确不能满足，则该部署路径不适用。若关键安全信息缺失，则结果是 `UNKNOWN / deployment decision blocked`，不是“已证明不适用”。

### Evidence Gate

- `SUPPORTED FOR THIS CONFIGURATION`：目标任务与具体配置有直接、可核验支持；
- `CONDITIONAL`：机制有支持，但至少一个关键任务或条件轴需要验证；
- `NOT SUPPORTED BY CURRENT EVIDENCE`：当前主张没有足够支持，不能写成结果；
- `MECHANISM CONFLICT`：存在明确物理/系统冲突，需要说明冲突链；
- `UNKNOWN`：所需信息未公开或尚未取得，不能转换成正面或负面事实。

## 8. 当前三个配置的正确比较起点

| 配置 | 当前可提出的价值机制 | 当前不能宣称 |
| --- | --- | --- |
| 专用接触自动化 | 用工装、导向和专用机构降低不确定性；在稳定任务下可能形成简单可靠的闭环 | 天然没有传感、确认或恢复；天然不能换型 |
| 固定工业机器人单元 | 通过可配置的感知、工具、柔顺和控制接口处理一定变化 | 类别本身就有 F/T、恢复、可靠性或经济优势 |
| 移动/双臂/人形系统 | 当跨工位、双臂管理线束或多任务复用真实存在时，可能减少重复设备或适配既有布局 | 已证明优于固定机器人；已证明 brownfield、成本、安全和成熟度优势 |

## 9. Framework v1.0 尚缺的关键输入

优先级从高到低：

1. 目标或同类制造 Pack EoL 接口的电气状态、安全功能和连接/断开许可逻辑；
2. 目标 connector/harness 的几何、供料、支撑、残余位姿误差和完成判据；
3. 现实 dedicated/manual/fixed-robot baseline 的同任务配置；
4. 产品/接口变化发生在哪一层、变化频率和换型资源；
5. 各配置在同等任务边界下的节拍、介入、可靠性、集成和成本数据；
6. 机器人、PLC/cell controller、tester 和 MES 的实际功能与数据责任。

## 10. 本阶段判定

`FRAMEWORK INPUT READY — PARTIAL`

R1、R2、R3、R5 已有足够证据成为评价字段，但没有足够目标参数得出架构结论。R4、R6 的概念有效，但目标生产条件和系统实现仍弱。下一步应以这些缺口驱动定向证据检索和设备基线审计，然后形成 Framework v1.0 的正式 decision table。
