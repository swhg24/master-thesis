# Week 05 Case Dossier — Formation Carrier Handover

> 状态：学习与可行性审计进行中；不是最终 research gap、research question 或论文题目。
> Primary reference：CN118970237A（公开专利申请；disclosed/proposed，未由本项目验证实际部署）。

## 1. Day 1 已完成的证据定位

- Flow object：承载若干电池的承载装置；实施例优选为电池托盘。
- 设备链：主输送机构1 → 第五移载装置25 → 第三输送部26 → 入库机27 → 堆垛机28 → 化成装置3。
- 直接证据：说明书[0061]明确第五移载装置25在主输送机构1与第三输送部26之间转移承载装置；[0062]明确堆垛机28在入库机27与化成装置3之间转移承载装置。
- 证据边界：具体pickup/receiving port、化成装置内部positioning/contact、equipment acceptance与process-start handshake未被该来源完整披露。
- 技术边界：该架构为固定输送/入库/堆垛方案，不是direct AGV case。

## 2. Revised Day 2 — 责任边界选择

### 2.1 今日核心问题

> “送入化成装置”包含哪些不同设备责任；Week 5应选择其中哪一个最小接口继续审计？

### 2.2 设备级与系统级接口

- T1（source-explicit）：第五移载装置25把承载装置从主输送机构1转移到第三输送部26。
- T2（部分明确）：第三输送部26与入库机27沿入库方向依次布置；来源未详细说明二者之间的具体交接机构、端口和信号。
- T3（source-explicit）：堆垛机28把承载装置在入库机27与化成装置3之间转移。

不能把“入库链方向”与“直接接收设备”混写；也不能把设备级目的地“化成装置3”扩写为未披露的具体工艺位置。

### 2.3 候选边界审计

| 边界 | 当前证据 | 暂不作为primary的原因 / 选择理由 |
| --- | --- | --- |
| B1：主输送机构 → 第三输送部 | 转移执行者与两端设备明确 | 更接近通用输送线接驳；当前battery/formation-specific relevance较弱。简单本身不是排除理由。 |
| **B2：入库机 → 化成装置（堆垛机执行）** | actor、source equipment、destination equipment明确 | **暂选Week 5 primary boundary**：直接连接formation equipment，且仍有可审计的接口未知。 |
| B3：化成装置入口 → 内部工艺位置/接口 | positioning/contact/acceptance未完整披露 | 重要但直接证据与现实验证入口不足；不得依靠工程常识补成已知流程。 |

学生的阶段判断：选择B2；B1的主要限制是formation-specific relevance不足，B3的主要限制是专利证据与可验证性不足。

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

这只是Week 5的reference boundary，不证明未来论文目标系统使用堆垛机，也不证明AGV直接或间接参与该接口。

### 2.5 功能、参考实现与未来目标系统

必须分开三个层级：

1. **研究功能**：载具从formation上料侧进入formation equipment的设备间转移；
2. **本周参考实现**：Architecture B采用入库机27、堆垛机28和化成装置3；
3. **未来目标系统**：尚无真实布局与接口资料，transport technology及AGV是否存在均为UNKNOWN。

假设性的`AGV → 入库机 → 堆垛机 → 化成装置`只用于解释功能分配：AGV可承担上游区域运输，堆垛机可承担固定最终上料。它不是Architecture B的source-explicit事实，也不是目标系统结论。

### 2.6 Revised Day 2 学习结果

学生能够说明：

- “formation area”只是区域名称，不能作为完整、可验证的运输任务终点；
- 接口必须至少识别flow object、pickup equipment、transfer actor和destination equipment；
- B2因具有直接专利证据、明确actor/source/destination且直接连接formation equipment，被暂选为Week 5 reference boundary；
- Architecture B中B2的执行者是堆垛机28；
- 一项non-AGV专利只能证明一种公开实现，不能确定尚无现场资料的目标系统使用或不使用AGV。

Day 2形成的是设备责任与范围边界，不是handover completion state machine。后者留给Day 3。

## 3. 当前待推进

- 将宽泛Candidate A暂时收缩为只对应B2的可审计工作表述：`operational carrier transfer at one specified formation-loading interface`。这仍是working formulation，不是最终research question。
- Day 3再检查B2在什么条件下可以称为完成；Day 2不提前构造acceptance state machine。
- Day 4再判断B2剩余条件是否真正来自cell formation，而不是一般pallet logistics。
