# Week 05 Case Dossier — Formation Carrier Handover

> 方向锚点：Thomas给出的working title是 **“Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies.”**
> 状态：学习与可行性审计进行中；不是最终 research gap、research question 或论文题目。
> Week 05 reference/baseline：CN118970237A（公开专利申请；non-AGV fixed automation；disclosed/proposed，未由本项目验证实际部署）。
> 2026-08-11校准：B2不得继续演变为堆垛机或一般设备接口课题。后续先检查battery requirement是否真正改变robotic-system task或robot–equipment integration decision。

## 0. 这份 dossier 在论文主线中的位置

### 0.1 总论文方向

本论文研究的是：

> 机器人系统在锂离子电芯制造中的应用潜力、具体应用与工业实施策略。

当前具体工作方向是：

> cell finishing中的机器人载具处理与厂内物流集成，特别检查formation上料要求是否改变移动机器人、固定上料设备与化成设备之间的任务和接口责任。

### 0.2 Week 05的角色

Week 05只使用一个公开formation-loading架构填补Week 03–04留下的interface unknown，并检验它能否支持一个battery-specific且robotics-relevant的问题。

层级不得混淆：

```text
Thomas working title / thesis anchor
    Robotic Systems in Battery Manufacturing
        ↓
Current learning use case
    Cell-finishing carrier/tray handling and intralogistics
        ↓
Week 05 evidence probe
    One disclosed non-AGV formation-loading architecture
        ↓
B2 fixed-automation baseline
    入库机27 → 堆垛机28 → 化成装置3
```

B2位于最底层。它不能反向取代上面的论文方向。

### 0.3 当前唯一可行性问题

> 在这个或未来可验证的formation-loading配置中，是否有一项直接支持的工艺条件，会改变可辨认的机器人系统任务，或改变机器人与固定上料/工艺设备之间的具体集成决策？

若没有，B2完成了学习和反例作用，但退出thesis-candidate path。

### 0.4 B2到底是什么：四句话说明

1. **它是什么**：Architecture B中由堆垛机28执行的`入库机27 → 化成装置3`载具转移段。
2. **我们确实知道什么**：flow object是承载多个电池的承载装置/托盘；source equipment、transfer actor和destination equipment有专利直接证据。
3. **我们不知道什么**：具体pickup/receiving port、最终position/contact、control ownership、equipment acceptance与process start均未被完整证明。
4. **为什么还看它**：它用于区分区域运输、固定最终上料和工艺接入，并检验是否有formation-specific requirement真正改变robotic-system task或robot–equipment integration decision；它本身不是AGV案例，也不是已经选定的论文课题。

当前结论可以压缩为：

> **B2作为reference足够清楚；作为robotics thesis problem证据不足。**

## 1. Day 1 已完成的reference evidence定位

- Flow object：承载若干电池的承载装置；实施例优选为电池托盘。
- 设备链：主输送机构1 → 第五移载装置25 → 第三输送部26 → 入库机27 → 堆垛机28 → 化成装置3。
- 直接证据：说明书[0061]明确第五移载装置25在主输送机构1与第三输送部26之间转移承载装置；[0062]明确堆垛机28在入库机27与化成装置3之间转移承载装置。
- 证据边界：具体pickup/receiving port、化成装置内部positioning/contact、equipment acceptance与process-start handshake未被该来源完整披露。
- 技术边界：该架构为固定输送/入库/堆垛方案，不是direct AGV case。
- 论文边界：它说明一种fixed-automation solution已经被公开，但尚未形成一个robotics research problem。

## 2. Revised Day 2 — 责任边界选择

### 2.1 今日核心问题

> “送入化成装置”包含哪些不同设备责任；Week 5应选择其中哪一个最小接口继续审计？

### 2.2 设备级与系统级接口

- T1（source-explicit）：第五移载装置25把承载装置从主输送机构1转移到第三输送部26。
- T2（部分明确）：第三输送部26与入库机27沿入库方向依次布置；来源未详细说明二者之间的具体交接机构、端口和信号。
- T3（source-explicit）：堆垛机28把承载装置在入库机27与化成装置3之间转移。

不能把“入库链方向”与“直接接收设备”混写；也不能把设备级目的地“化成装置3”扩写为未披露的具体工艺位置。

### 2.3 候选边界审计

| 边界 | 当前证据 | Week 5选择判断 |
| --- | --- | --- |
| B1：主输送机构 → 第三输送部 | 转移执行者与两端设备明确 | 更接近通用输送线接驳；当前battery/formation-specific relevance较弱。简单本身不是排除理由。 |
| **B2：入库机 → 化成装置（堆垛机执行）** | actor、source equipment、destination equipment明确 | **暂选Week 5 main reference boundary / fixed-automation baseline**：直接连接formation equipment，供责任与robotics-relevance审计；不是thesis primary case。 |
| B3：化成装置入口 → 内部工艺位置/接口 | positioning/contact/acceptance未完整披露 | 重要但直接证据与现实验证入口不足；不得依靠工程常识补成已知流程。 |

学生的阶段判断：选择B2作为Week 5学习边界；B1的主要限制是formation-specific relevance不足，B3的主要限制是专利证据、责任主体与可验证性不足。这个选择不等于选择堆垛机作为论文对象。

### 2.4 B2最小接口定义

```text
Flow object: 承载若干电池的承载装置 / tray
Pickup equipment: 入库机27
Transfer actor: 堆垛机28
Destination equipment: 化成装置3
Exact pickup port: UNKNOWN
Exact receiving port: UNKNOWN
Final positioning/contact: UNKNOWN
Equipment acceptance/process start: UNKNOWN
```

这只是Week 5的fixed-automation reference boundary，不证明未来论文目标系统使用堆垛机，也不证明AGV直接或间接参与该接口。固定堆垛机是否符合Thomas对本论文`robotic system`的预期，也仍待导师确认。

### 2.5 功能、参考实现与未来目标系统

必须分开三个层级：

1. **论文方向**：robotic systems in lithium-ion battery cell manufacturing；
2. **当前学习功能**：formation上料中区域运输、固定移载与工艺设备之间的责任分配；
3. **本周参考实现**：Architecture B采用入库机27、堆垛机28和化成装置3；
4. **未来目标系统**：尚无真实布局与接口资料，transport technology及AGV是否存在均为UNKNOWN。

假设性的`AGV → 入库机 → 堆垛机 → 化成装置`只用于解释功能分配：AGV可承担上游区域运输，堆垛机可承担固定最终上料。它不是Architecture B的source-explicit事实，也不是目标系统结论。

### 2.6 Revised Day 2 学习结果

学生能够说明：

- “formation area”只是区域名称，不能作为完整、可验证的运输任务终点；
- 接口必须至少识别flow object、pickup equipment、transfer actor和destination equipment；
- B2因具有直接专利证据、明确actor/source/destination且直接连接formation equipment，被暂选为Week 5 reference boundary；
- Architecture B中B2的执行者是堆垛机28；
- 一项non-AGV专利只能证明一种公开实现，不能确定尚无现场资料的目标系统使用或不使用AGV。

Day 2形成的是设备责任与范围边界，不是handover completion state machine。方向校准后，Day 3先做robotics-relevance责任审计；只有至少一项跨系统条件通过初筛，才考虑最小状态表示。

这里的“责任”当前仅指source equipment、transfer actor与destination equipment的**功能分配**。Architecture B没有完整建立control command、state ownership或process acceptance责任，不能把这些写成Day 2已经确认的结果。

## 3. 方向校准后的 Day 3：Robotics Relevance Responsibility Matrix

旧工作表述`operational carrier transfer at one specified formation-loading interface`不再单独承担方向定义，因为它没有明确robotic-system relevance。

当前工作问题改为：

> 哪一项formation-specific condition（如果存在）真正改变了机器人系统任务或robot–equipment integration decision，而不是只属于固定搬运或化成设备内部？

### 3.1 待填写责任矩阵

| 候选条件 | Architecture B直接证据 | 其他来源线索（不可移植） | 可能责任主体 | 是否改变robot task / robot–equipment decision | 实际后果证据 | 验证入口 | 当前判断 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Exact pickup/receiving position | 未公开具体port | Architecture A有伸缩臂到位检测 | 堆垛机/固定接口/formation equipment/unknown | 待证 | 待证 | 待确认 | UNKNOWN |
| Mechanical locking / fixture | Main reference未披露 | Deng特定配置支持tray fixture | carrier/formation equipment/unknown | 不可跨来源推定 | 待证 | 待确认 | UNKNOWN |
| Electrical/process contact | Main reference未披露 | Schomburg支持某类carrier contact功能 | formation equipment/独立机构/unknown | 待证；可能完全process-internal | 待证 | 待确认 | UNKNOWN |
| Identity mapping | Main reference只支持carrier识别和所处工序判断 | 其他配置有traceability线索 | scanner/MES/PLC/equipment/unknown | 待证 | 待证 | 待确认 | UNKNOWN |
| Acceptance/readiness | Main reference只支持数量满足时设备“可启用” | 不能推出carrier acceptance handshake | formation control/handling control/unknown | 待证 | 待证 | 待确认 | UNKNOWN |

### 3.2 Day 3判断规则

- 上表不是五个研究主题，只用于筛选并排除；
- 只有同一case有直接证据、确实改变robotic-system task或robot–equipment integration decision、具有实际后果且有验证入口的条件，才允许继续；
- 若要求完全由formation equipment内部处理，标记`PROCESS-INTERNAL`，不作为机器人课题；
- 若只是普通pallet物流要求，标记`GENERIC`；
- 若只在其他来源出现，标记`CROSS-SOURCE—DO NOT TRANSFER`；
- 若没有任何条件通过，B2标记`FIXED-AUTOMATION BASELINE—EXIT THESIS CANDIDATE`；
- evidence-bounded state diagram只在至少一项条件通过初筛后制作，并且只画最小必要状态。

## 4. Candidate A 当前状态

### 4.1 不能写成

- “formation handover没有被研究”；
- “B2与B3之间一定存在process-aware acceptance”；
- “pressure/contact/identity/readiness都属于堆垛机handover”；
- “堆垛机接口就是本论文的robotic system”；
- “目标系统使用AGV，且AGV把tray交给入库机”。

### 4.2 目前只能写成

> `Candidate A remains a feasibility hypothesis: test whether one directly supported formation-specific requirement changes an identifiable robotic-system task or a concrete robot–equipment integration decision at one validated loading interface.`

中文：

> Candidate A仍是可行性假设：检验在一个经过验证的化成上料接口中，是否有一项直接支持的formation-specific requirement会改变可辨认的机器人系统任务，或改变机器人与固定上料/工艺设备之间的具体集成决策。

### 4.3 生死门

只有以下各项均为`YES + evidence`才可继续：

1. direct cell-manufacturing case；
2. identifiable robotic-system actor或有现实理由评价的robotic solution；
3. battery-specific condition直接改变该系统的任务/接口/完成判据；
4. meaningful implementation decision与实际后果；
5. credible expert/equipment/case validation；
6. Thomas确认仍符合原始`Robotic Systems in Battery Manufacturing`方向。

### 4.4 2026-08-12最终方向决定

结合Day 3责任审计与学生对robotics relevance的复核：

- 扫码/identity只确认carrier身份，未证明它改变堆垛机的搬运任务；
- locking/contact/precision等候选要求没有Architecture B的直接证据，且现有理解更可能属于formation equipment内部责任；
- B2明确说明了一段固定自动化搬运，但没有建立符合Thomas原始任务意图的机器人应用问题；
- 继续补画position、contact、acceptance或PLC state只会深化电池设备接口，不会自动恢复robotics relevance。

因此当前决定改为：

> **ABANDON AS THESIS CANDIDATE / RETAIN AS FIXED-AUTOMATION BASELINE / RETURN TO ROBOTICS APPLICATION MAP**

B2作为Week 05学习成果与反例保留，但退出thesis-candidate path。下一阶段按照Thomas的原始任务说明重新窄化一个具有明确robot actor、battery-manufacturing task、比较baseline和实施决策的use case；不得因文件连续性继续研究B2。
