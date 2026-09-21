# Day 1 学习引导：一篇“很接近”的论文到底能证明什么？

> 日期：2026-09-20  
> 对应本周核心问题：把固定 RQ 转化为可复现、不过度外推的证据协议  
> 今天的唯一学习目标：**能够根据证据身份决定一句话应当直接保留、条件保留、降级、删除还是等待全文。**

## 1. 今天先记住一句话

> **“与案例很像”不是一个完整的证据判断。必须分别比较生命周期、生产层级、物理任务和要支持的主张。**

同一篇论文可能：

- 对“某个物理机制存在”是强证据；
- 对“CATL 的实际工位就是这样”完全不是证据；
- 对“某架构比另一架构更好”仍然没有证据。

因此，证据不是简单的“强/弱”一条线，而是“这条来源对这条具体 claim 是否匹配”。

## 2. 四轴判断法

每读一条来源，先填下面四项，再讨论它是否支持论文结论。

| 轴 | 必问问题 | Pack EoL 当前目标值 |
| --- | --- | --- |
| 生命周期 `lifecycle` | 是制造端 end-of-line，还是退役/回收端 end-of-life？ | `MANUFACTURING` |
| 生产层级 `production level` | cell、module、pack，还是非电池类比？ | `PACK` |
| 物理任务 `physical task` | 插入、拔出、端子接触、线束布置、检测，还是只做电化学测试？ | test connector / flexible harness plugging–unplugging / confirmation |
| 主张类型 `claim type` | 要证明任务存在、机制相关、性能数值、比较优势，还是实施方法？ | 必须逐条指定 |

辅助规则：

1. 四轴高度匹配，且有可核验全文/官方披露，才可能直接支持当前具体 claim；
2. 一个或多个轴不同，但物理机制可解释地相通，只能 `RETAIN_CONDITIONAL`；
3. 来源只启发了一个未来场景，而没有比较或现场数据，使用 `DOWNGRADE_ASSUMPTION`；
4. 从技术类别名称直接推断能力，或把别的场景数值搬过来，通常应 `REMOVE_UNSUPPORTED`；
5. 只有摘要而详细条件决定结论时，保持 `PENDING_FULLTEXT`。

## 3. 五张来源卡：它们分别处在什么位置？

### Card A — Spirit AI / CATL 的直接企业披露（S011）

- 生命周期：`MANUFACTURING`
- 层级：`PACK`
- 任务：EOL/DCR 测试接插件插接、柔性线束插拔、连接状态检查
- 来源身份：直接公司披露，不是独立同行评审验证

可以证明：

> Spirit AI **公开披露**了 Moz 在 PACK 生产线执行上述任务。

不能证明：

> 该架构已被独立证明具有 99% 以上成功率、优于固定机器人、经济可行或适合所有 Pack EoL 工位。

### Card B — 退役电池机器人测试（S001/S002）

- 生命周期：`END_OF_FIRST_LIFE`
- 层级：`MODULE`
- 任务：机器人接触电池端子并执行 EIS 测试
- 来源身份：同行评审的 closest work

可以证明：

> 机器人电池测试、柔顺端子接触、连接检查和具体测试单元安全集成已有同行评审先例。

不能证明：

> 退役模组端子接触等同于制造端 Pack 柔性测试接插件插入；论文中的力、时间和成功率可以迁移到 Pack EoL。

### Card C — 汽车多分支线束双臂装配（S004）

- 生命周期：`GENERAL_METHOD`
- 层级：`NON_BATTERY_ANALOG`
- 任务：多分支线束的分离、布置、张力控制与防缠绕
- 来源身份：同行评审、开放全文、跨行业物理机制类比

全文显示，该配置使用固定双臂工业机器人、相机、腕部力/力矩传感器、专用夹爪和夹具，并在两种完整装配序列中暴露出 cable separation、calibration 和 entanglement 的累积失败问题（article pp. 578, 588–595）。

可以证明：

> 对某些多分支工业线束任务，变形相关感知、抓取点选择、线缆分离、张力管理、错误检测和防缠绕是实际评价维度。

不能证明：

> Pack EoL 的测试线束具有同样的分支结构和运动范围；双臂是必要条件；该文 55%/73% 的完整序列结果可以迁移到电池生产。

### Card D — 高压电连接器敏感装配（S005/S006）

- 生命周期：`GENERAL_METHOD`
- 层级：`NON_BATTERY_ANALOG`
- 任务：电连接器插入、接触状态与位姿偏差处理
- 来源身份：跨行业 connector-mating mechanism

S005 开放全文直接支持：在其三种高压连接器、特定夹爪和位姿不确定性范围内，敏感/柔顺装配能够补偿大部分测试偏差。作者也明确限制了向更小公差连接器和完整电连接状态迁移的范围。

S006 的 IEEE 官方摘要支持“在受限/遮挡条件下采用几何与力信息”的研究方向，但全文当前需要机构访问，所以详细性能仍为 `PENDING_FULLTEXT`。

可以证明：

> 当目标连接器确实存在位姿不确定性、接触约束或视觉遮挡时，compliance、F/T sensing 和 contact-state reasoning 是应检查的配置能力。

不能证明：

> CATL 目标连接器一定需要相同策略、相同力参数，或任何机器人只要安装 F/T 传感器就能可靠完成任务。

### Card E — EV 电池模组机器人装配（S018）

- 生命周期：`MANUFACTURING`
- 层级：详细工作单元是 `MODULE`
- 任务：工艺分解、机器人需求选择、工作单元设计与仿真；广义流程把 testing/certification 放在最后阶段
- 来源身份：同行评审的相邻电池制造研究

可以证明：

> 电池制造领域已有从工艺要求到机器人配置和工作单元设计的研究先例；“泛泛做 task decomposition”不能单独作为本论文创新。

不能证明：

> 文中已经研究了 Pack EoL 柔性接插件、真实部署性能，或 dedicated/fixed/humanoid 架构的条件性比较。

## 4. 当前 evidence map

```text
S011  公司直接披露
  └─ 直接支持：目标任务被公开披露
     └─ 不直接支持：真实性能、经济性、比较优势

S001/S002  退役电池机器人测试
  └─ 直接支持：closest work 存在
     └─ 条件迁移：接触、确认、安全集成机制

S004/S005/S006  跨行业线束与连接器
  └─ 条件迁移：物理机制和待评价能力
     └─ 禁止迁移：Pack 工况、性能数字、架构优越性

S018  电池模组制造机器人工作单元
  └─ 直接支持：相邻制造方法先例
     └─ 不直接支持：Pack EoL connector case
```

这张图也解释了为什么本论文当前可检验的 research need 不是“没人研究机器人电池测试”，而是：

> 现有证据分散在不同生命周期、生产层级、任务边界和机器人配置中，尚需一个透明的任务驱动比较方法，把这些证据转化为对选定电池制造应用的条件性适用判断。

这仍是待 Scopus、Web of Science、IEEE Xplore 正式检索继续检验的表述，不是已经宣布的 novelty。

## 5. 论文句子的安全写法

### 直接披露

> Spirit AI reports that its Moz system performs connector insertion and harness connection-status inspection in PACK-line EOL/DCR testing.

不要改成：

> Humanoid robots have proven superior performance in battery-pack EoL testing.

### 跨生命周期 closest work

> Robotized terminal contact has been demonstrated for end-of-first-life battery-module testing; this establishes a technical precedent for compliant contact and connection checking, but not direct evidence for manufacturing Pack EoL connector handling.

### 跨行业机制

> Experiments in automotive wire-harness assembly indicate that deformation-dependent perception, cable separation and entanglement management can become relevant capability dimensions. Their relevance to Pack EoL must be verified against the target harness geometry and task boundary.

### 相邻电池制造方法

> Prior work has derived and simulated fixed-robot work cells from EV battery-module assembly requirements. The present thesis therefore does not claim novelty from task decomposition alone, but investigates a transparent cross-architecture assessment under application-specific conditions.

## 6. 可选练习（不作为研究推进门槛）

不要重新读完所有论文。只根据上面五张来源卡，判断下面五句话：

| 句子 | 你的决定 | 你的理由 |
| --- | --- | --- |
| 1. `Robotized battery testing has not been studied.` | `?` | 哪个来源构成反例？ |
| 2. `Force/compliance capability should be checked for the target connector configuration.` | `?` | 是事实、条件性维度还是假设？ |
| 3. `A dual-arm system is superior for Pack EoL because S004 used two arms.` | `?` | 哪几个轴不匹配？ |
| 4. `Testing and certification can be placed inside the broad battery-manufacturing process boundary.` | `?` | 哪个来源支持到什么程度？ |
| 5. `The Pack EoL system should achieve the 73% success rate reported in S004.` | `?` | 为什么数字不能迁移？ |

如果你想单独训练证据边界，可以回复下面三项；不完成也不阻止我们继续进入 Pack EoL 工程内容和 Framework v1.0：

1. 五句话分别给出一个状态：`RETAIN_DIRECT / RETAIN_CONDITIONAL / DOWNGRADE_ASSUMPTION / REMOVE_UNSUPPORTED / PENDING_FULLTEXT`；
2. 任选一句，改写成可以进入论文的严谨表达；
3. 写出一个你认为 Pack EoL 仍必须查清的 `UNKNOWN`。

## 7. 自检标准

完成后，你应该能够解释：

- 为什么 company source 对“公司披露过某任务”可以是直接证据，但对性能优越性不是；
- 为什么同行评审论文也可能只能条件迁移；
- 为什么“双臂”“humanoid”“industrial robot”等架构名称本身不等于能力；
- 为什么直接证据不足时应缩小 claim，而不是用多个相邻来源拼成一个现场事实。

研究主线已直接继续到下一步：**把 R1–R6 从描述性 requirement group 改写成 Framework v1.0 的可审计问题。** 本练习只用于自测，不再作为前置闸门。
