# Framework v1.0：三张同任务 baseline card 与判定规则草稿

> 日期：2026-09-22
> 状态：`FRAMEWORK INPUT — BASELINE CARDS DRAFT`（不是 Framework v1.0 结论）
> 上位文件：`09_framework_v1_input_requirements.md`
> 用途：把"同一任务、三种 connector-adaptation 配置"落到可审计证据卡，作为判定规则 0–4 的直接依据

> **2026-09-28 纠偏：** 下文第 3–4 节保留 2026-09-22 草稿原貌，涉及“专机内部全 UNKNOWN”和“机器人只有跨行业机制”的概括，已被第 8 节的 Pack 同任务公开资料纠正；引用时以后者为准。

## 1. 作用与边界

本文档承接 [09 号文件 §6 配置卡与 §8 比较起点](09_framework_v1_input_requirements.md)，产出三张同任务 baseline card：

1. **Manual connector adaptation**（人工接线）
2. **Dedicated automatic contact**（专用自动接触机构）
3. **Configured robot manipulation**（可配置机器人接插件操作）

三张卡都固定在 `connector adaptation` 层。`transport architecture`、`Pack positioning`、`test/safety cell`、`information architecture` 四层作为独立轴，不与 adaptation 混为一谈。任何一格必须带证据身份，禁止从"人工 / 专机 / 机器人"类别标签反推能力。

## 2. 六个闭环（评估单元）

每张卡按六个闭环填写，并区分两层：

- **接触层**（connector-adaptation 固有，差异发生在这里）：`1 对象状态`、`2 接触插合`、`3 完成确认`、`5a 失败重试`
- **工位层**（test-station 固有，与 adaptation 选择正交）：`4 安全许可`、`6 信息闭环`、`5b 放行/返修`

当前证据下，工位层三张卡主要引用同一证据池；但具体安全与信息接口的实现、验证负担和成本可能随配置变化。接触层是当前最直接的功能差异来源，也恰是证据最薄的一层。

## 3. 三张 baseline card

### 3.1 Manual connector adaptation（人工接线）

| 闭环 | 谁关闭 | 证据身份 | 目前 UNKNOWN |
| --- | --- | --- | --- |
| 1 对象状态 | 操作员（取件—插接—归位） | `RETAIN_DIRECT`（Marposs: operator connects/disconnects） | 接口可达性、动作规范、节拍 |
| 2 接触插合 | 操作员手眼协同 | `RETAIN_DIRECT`（人工基线本身性质） | 力度/触觉无人量化，无法与机器人数值对比 |
| 3 完成确认 | 操作员（目视/触觉判断物理插接到位）+ 测试系统（接受该连接才允许测试） | `RETAIN_DIRECT` 仅限"插接由人完成"；系统接受判据 → `UNKNOWN` | 判据是人目视、锁止机构还是 tester 电气接受；false accept/reject 后果 |
| 4 安全许可 | 工位安全系统（围栏/门/区域监控），不是操作员 | `RETAIN_DIRECT`（thyssenkrupp manual 行 safety guarding；Marposs 舱内连接安全、电路开断）+ `RETAIN_CONDITIONAL`（S002 跨生命周期 interlock） | 目标时序、去能量、是否带电插拔、标准合规 |
| 5 异常恢复 | 操作员（即时微调/重插）+ 工位（放行/返修判定） | `RETAIN_DIRECT` 仅限"人工可即时重试" | 系统级异常协议、重试上限、失败 Pack 返修/隔离流向 |
| 6 信息闭环 | 工位/PLC/MES，不是操作员 | `RETAIN_CONDITIONAL`（Marposs 示例舱 CAN/data logging；该舱为自动方案，与人工方案对应未明示） | 身份—配方—结果数据流、操作员是否录入、MES 接口 |

**要点**：真正由人关闭的只有第 1、2 行和 5a 半行；第 4（安全）、6（信息）在人工模式下仍由工位/PLC/MES 闭环。manual baseline 本身是一个完整系统，不是"零自动化"。

### 3.2 Dedicated automatic contact（专用自动接触机构）

| 闭环 | 谁关闭 | 证据身份 | 目前 UNKNOWN |
| --- | --- | --- | --- |
| 1 对象状态 | 专用接触机构（自动取/插/归） | `RETAIN_DIRECT` 仅限**方案存在**（Marposs: fully automated wiring without intervention；thyssenkrupp: conveyor+automatic HV/communication connection、AGV+automatic adaptation unit） | 机构内部结构、动作分工、与 Pack 定位如何耦合 |
| 2 接触插合 | 机构/工装 | `UNKNOWN`（供应商不公开内部机构；不能反向假定它靠导向/浮动消除误差，也不能假定它没有感知/柔顺） | 误差消除方式、导向/力限制、卡滞处理 |
| 3 完成确认 | 机构 + 测试系统 | `UNKNOWN` | 判据、判据所有者、false accept/reject |
| 4 安全许可 | 工位安全系统（围栏/门/区域监控） | `RETAIN_DIRECT`（thyssenkrupp 围栏/门/区域监控；Marposs 舱电路开断/防火）+ `RETAIN_CONDITIONAL`（S002） | 目标时序、去能量、带电状态、标准合规 |
| 5 异常恢复 | 机构（重试）+ 工位（放行/返修） | `UNKNOWN` | 是否有卡滞检测/重试、介入方式 |
| 6 信息闭环 | 工位/PLC/MES | `RETAIN_CONDITIONAL`（与 manual 卡同源，Marposs CAN/data logging） | 数据流、接口、追溯粒度 |

**要点**：与 manual 卡形成镜像反差——manual 卡的"手"透明（人怎么做可描述），专机卡的"手"是黑盒（供应商不公开内部）。唯一硬证据是第 1、4 行（方案存在 + 安全单元存在），第 2、3、5 行纯 `UNKNOWN`。

### 3.3 Configured robot manipulation（机器人接插件操作）

| 闭环 | 谁关闭 | 证据身份 | 目前 UNKNOWN |
| --- | --- | --- | --- |
| 1 对象状态 | 机器人（取/插/归） | `RETAIN_DIRECT` 仅限 company-reported 任务存在（S011 披露 Moz 插接+检查）；`RETAIN_CONDITIONAL`（S033 综述 C030/C031——线束装配 cobot 化任务地图聚焦 spot-taping/routing、连接器 mating 薄弱、11 篇全无成本/节拍量化；S034 案例 C032/C033——UR5+RG2+Cognex 视觉定位孔位做扎带放置，但夹爪未开发、放置未验证、人负责放线束本体） | 目标工位机器人实际配置、供料、位姿范围；成功率/节拍无独立验证 |
| 2 接触插合 | 机器人 + 工具/柔顺/F-T | `RETAIN_CONDITIONAL`（S005/S006/S008 跨行业电气连接器机制；S001/S002 电池测试柔顺接触；S017 电池连接器接触；S031 C027 两阶段力上限+阻抗在线辨识+safe stop、C029 ±0.5 mm 位姿识别+重识别确认） | 目标 connector 几何、残差量级、力上限、导向；不得预设"必用 F/T/力控"（C019 已删） |
| 3 完成确认 | 机器人（检查）+ 测试系统 | `RETAIN_CONDITIONAL`（S011 披露 connection-status inspection；S001 的 OCV/connectivity check 机制；S024 的相对位移 PWA 模型 + 力上限 F̄ + set-membership 在线监测，区分完成与卡滞） | 判据、传感模态、判据所有者、false accept/reject |
| 4 安全许可 | 工位安全系统 | `RETAIN_DIRECT`（工位）+ `RETAIN_CONDITIONAL`（S002 更直接：机器人电池测试的 cell-door interlock + T1 + admittance force threshold） | 目标时序、去能量、带电状态、标准合规 |
| 5 异常恢复 | 机器人（检测/重试）+ 工位（放行） | `RETAIN_CONDITIONAL`（S005 sensitive joining 补偿/failure；S004 error detection；S031 C028 三阶段错误恢复——位置-力异常阈值+spiral/probing/binary 选择） | 目标工位恢复协议、重试上限、介入方式 |
| 6 信息闭环 | 工位/PLC/MES（机器人可能参与） | `RETAIN_CONDITIONAL`（与另两卡同源）+ 注意 C022：Robot–MES 直连已降级为假设 | 机器人是否直连 MES、数据流、接口 |

**要点**：机器人的"厚"只厚在接触层机制来源多（第 2、3、5a 行有跨行业/跨生命周期补丁），但它没有任何一格比另两张更接近现场事实——第 1 行仍是"企业这么说"。

## 4. 三张卡合成

```text
             Manual          Dedicated            Robot
接触层
 1 对象状态  DIRECT(人)      DIRECT(方案存在,机构UNKNOWN)   DIRECT(company-reported)
 2 接触插合  DIRECT(手眼)    UNKNOWN              CONDITIONAL(机制)
 3 完成确认  DIRECT(人)+UNKNOWN(判据)  UNKNOWN      CONDITIONAL(检查+机理,判据UNKNOWN)
 5a 失败重试 UNKNOWN         UNKNOWN              CONDITIONAL(机制)
——————————————————————————————————————————
工位层
 4 安全许可  DIRECT(工位)+COND  同左              DIRECT(工位)+COND(更强,S002)
 6 信息闭环  CONDITIONAL     CONDITIONAL          CONDITIONAL(+C022降级)
 5b 放行返修 工位            工位                工位
```

两个硬的观察：

1. 当前可见的主要功能差异在**接触层**（第 1、2、3、5a 行）；工位层（第 4、6、5b 行）是共同要求，但实现方式、验证负担和集成成本仍可能形成配置差异。
2. 接触层恰是证据最薄的一层：manual 透明、专机黑盒、机器人只有机制无现场；目标参数（残差、力、判据、恢复协议）当前全部 `UNKNOWN`。

## 5. 判定规则草稿（规则 0–4）

- **规则 0 — 分层与证据身份**：每个配置的结论必须分"接触层 / 工位层"两维给出，且每格带证据身份；禁止从类别标签填能力。
- **规则 1 — 工位层共同要求**：第 4（安全）、6（信息）、5b（放行）是三种配置都必须满足的测试工位要求。只有在实现、验证负担和代价确实等价时，它们才不区分配置；若机器人形态、人员进入方式、布局或控制接口改变了这些负担，就必须纳入 selection 评价。
- **规则 2 — 接触层是区分轴，但当前资格不足**：真正区分三种 adaptation 的是第 1、2、3、5a 行；而目标参数（残差、力、判据、恢复协议）目前全部 `UNKNOWN`，故当前只能给"价值机制"的 `CONDITIONAL` 结论，不能给"选 X 架构"的结果。
- **规则 3 — 升级门槛**：接触层任何一格要从 `CONDITIONAL/UNKNOWN` 升到"支持某配置"，必须补上同级目标参数；禁止拿"某配置在别的论文里成功过"跨门槛。
- **规则 4 — Safety Gate 特例**：第 4 行虽属工位层，但在缺少目标安全时序（去能量/带电/互锁）时，任何配置的部署判断都记 `UNKNOWN / deployment blocked`，而不是"已证明安全/不安全"。

## 6. 目标参数缺口 → 定向检索清单

规则 2/3 里所有 `CONDITIONAL/UNKNOWN` 都收敛到同一组缺口。据此派生的定向检索（OpenAlex `title_and_abstract.search` 布尔语法，结果先按 `NON_BATTERY_ANALOG`/`DIRECT_BATTERY_TESTING` 分流再判关系）：

| Query ID | 目标 | 上游 QB | 检索串（可执行） | 预期证据关系 |
| --- | --- | --- | --- | --- |
| R2-Q1 | 残差/力/对中/卡滞恢复 | QB4 | `"connector insertion" OR "connector mating"` AND `(robot OR robotic OR automation)` AND `(force OR alignment OR compliance OR recovery)` | `CROSS_INDUSTRY_TASK_ANALOG` 为主 |
| R5-Q2 | 连接/插入完成判据 | QB4+QB3 | `("insertion verification" OR "connection verification" OR "mating detection")` AND `(connector OR plug OR harness)` | `CROSS_INDUSTRY_TASK_ANALOG` 为主 |
| R3-Q3 | 电池测试 HV/互锁安全 | QB2b | `("battery test" OR "battery testing")` AND `("high voltage" OR "high-voltage" OR interlock)` AND `(robot OR automation)` | `DIRECT_BATTERY_TESTING_*` 为主 |
| R1-Q4 | 线束/柔性件机制 | QB4 | `("wire harness" OR "cable harness" OR "deformable linear object")` AND `(robot OR automation)` AND `(manipulation OR assembly OR handling)` | `CROSS_INDUSTRY_TASK_ANALOG` 为主 |
| R2-Q5 | 力控 + 连接器插合 | QB4 | `("force control" OR "admittance control" OR "impedance control")` AND `(connector OR plug OR socket)` | `CROSS_INDUSTRY_TASK_ANALOG` 为主 |

执行顺序：本轮先跑 R2-Q1、R5-Q2、R3-Q3，视命中再决定 R1-Q4、R2-Q5。所有命中必须过 [01 协议 §10 筛选流程](01_evidence_protocol_v1.md)，并记录到 `02_query_run_log.csv`。

## 7. 本阶段判定

`FRAMEWORK INPUT — BASELINE CARDS DRAFT`

三张卡把 [09 §8 比较起点](09_framework_v1_input_requirements.md) 落到了证据网格上，规则 0–4 是它的直接推论。下一步是拿 §6 的检索清单去补接触层目标参数；在此之前，任何"X 架构更优"都停在 `CONDITIONAL`，不升级为结果。
## 8. 公开资料近邻带来的基线纠偏（2026-09-28）

此节是对前述历史草稿的显式修正，证据链和搜索执行状态见 `14_public_source_checkpoint_2026-09-28.md`。

- **专用自动接触的接触层**：`CN109856554A` 权利要求 1、7、10 和实施方式公开了一种 Pack 测试自动对插设计，带水平/竖直浮动与位置检测。因此，前述表格的“第 2、3、5 行纯 UNKNOWN”仅能指 **Marposs/thyssenkrupp 特定供应商配置未公开内部细节**；不能指所有专用机构缺少公开机制。专利对第 2 行提供设计级直接证据，对到位检测提供部分第 3 行证据；其测试许可判据和故障恢复全流程仍未建立。
- **机器人接触层**：`CN117718986B` 权利要求 1、说明书实施方式披露机械臂、导引装置、力监测和测试插头操作；ROKAE 公开协作机器人、三维视觉及力控 Pack 测试插接配置。前述“第 2 行只有跨行业机制”已不完整。证据强度为具体设计或企业配置披露，不是独立部署性能。
- **比较单位仍是配置**：上述专机与机器人资料来自不同来源和条件，不能直接比较节拍、良率、成本或安全。人/专机/机器人三张卡只在相同任务状态、对象和生产条件下比较；机械到位、系统接受连接、测试许可、断开安全分别记录。目标工位 Task/Condition/Safety Gate 仍 OPEN。
