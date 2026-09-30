# 2026-09-30 研究札记：完成证据与下一状态放行责任

> 工作状态：针对 [16 号批判性审核](16_function_responsibility_audit_pilot_2026-09-30.md)末尾的唯一问题开展定向公开资料研究。Pack EoL 是制造端 **pack** 深参考案例；Candidate A 是 **module** 生产中 ABB Baden 单颗电芯入壳的相邻案例。这里的其他专利、供应商方案与退役电池实验均不是 ABB 或目标 Pack 工位的组成部分。本札记不更动 title、RQ、Framework 文件，也不作架构排名。

## 1. 收窄后的研究问题与答案

原问题问“哪一个最小的完成/接受信号能把机械动作已完成与产品/测试系统已接受分开”。检索后的答案是：**目前无法指定跨两个案例通用的单一最小信号**。首先必须指定要证明的状态以及这个状态允许谁做什么。一个信号只对其直接观测的状态有效；放行规则还需要指定判定者及失败路径。此为 `ANALYTICAL INFERENCE`，不是新理论或已核实的行业通则。

在两个案例中至少应分辨：

1. **动作结束**：执行器完成程序或停止运动；只证明控制动作状态。
2. **物理完成**：插头达到所设机械位置，或电芯在指定接收位置；应由能观测该状态的机制支持。
3. **功能/质量接受**：例如连接可用于所需电气测量，或模组装配满足被定义的质量要求。其接受范围取决于实际测试。
4. **下一状态放行**：测试仪/工位控制/MES/人工按照特定条件允许上电、测试、转序或出站。它是决策，不等同于上面任一个传感器读数。

这个分层是**查证清单**，不是主张所有工厂都装四组独立传感器，亦不表示存在统一许可时序。

## 2. Pack EoL：能够证实什么

| 来源身份及定位 | 公开资料具体支持 | 它没有证明什么 |
| --- | --- | --- |
| [CN117718986B，权利要求 1、方法实施方式与 S1203–S1205](https://patents.google.com/patent/CN117718986B/zh)：制造端 Pack 测试**专利设计** | 机械臂、导引面、力传感共同对插；部分实施方式以插接方向力与相对距离的条件判断完全插入并停止插接（说明书第 186–191 行）；插接后测试终端执行电性能测试（第 75–84、128–135 行）。异常力变化时退回重插属另一披露实施方式（第 167–174 行）。`EVIDENCED MECHANISM` | 力加距离不是电接触质量、BMS 通讯、绝缘、安全互锁或独立测试许可的证明；未披露目标工位实测成功率及完整联锁链。 |
| [CN109856554A，“具体实施方式”](https://patents.google.com/patent/CN109856554A/zh)：制造端 Pack 测试**专利设计** | 第三传感器感应片用于判定测试对插头“完全插入”（第 145 行），第一/第二传感器检测浮动超限并要求人工干预（第 157、170 行）。详细运行流程（第 173–174 行）是 Pack 先接测试托盘的**中转插头**，随后工位对插中转接口。`EVIDENCED MECHANISM` | 其第 135、145 行也用“插入电池包”作概括表述，不能抹掉详细流程的托盘边界。该传感器是所设机械状态的代理信号，不证明电气接受；也不能将此配置与 CATL 直接 Pack 接口作同条件胜负比较。 |
| [CN115493647A，摘要及步骤 1–3](https://patents.google.com/patent/CN115493647A/zh)：制造端 Pack EoL **测试流程专利** | 先连接线束和气密工装；扫码后，气密设备充气完成，下线测试系统发出 BMS 上电指令并执行 EOL；其后列有 HVIL 等测试项目。`EVIDENCED MECHANISM` | 文本未给出“线束已可靠插合”如何独立验收，也未给出这个信号怎样进入 BMS 上电许可。步骤相邻不等于许可因果链；HVIL 是所列**测试项目**，不可擅自写成所有测试前的许可输入。 |
| [DMC，Example System – End of Line Functional Testing](https://www.dmcinfo.com/blog/20983/everything-you-need-to-know-about-ev-battery-and-bms-testing-in-validation-and-production-scenarios-2/)：Pack 测试**供应商示例** | 可配置的 Pack EoL 测试序列把“Pack Connection Check”列于绝缘、端子、HVIL/BMS 等项目之前。`SUPPLIER DISCLOSURE` | 没有说明连接检查的测量原理、阈值、与下一个测试的联锁关系或哪个实际工厂部署。它不能填 CATL 专利缺少的许可逻辑。 |
| [Repower，Pack integrated test line 的 Layout 和设备清单](https://www.repowerstock.com/battery-pack-integrated-test-line.php?lang=en)：**供应商方案** | Pack EOL 站分别列出定位/自动对插、扫码访问流程、自动测试、MES 上传；设备清单另有 harness homing detection 与 safety detection module。`SUPPLIER DISCLOSURE` | 页面同时有气密、EOL、DCR 站；没有公开单一工位的传感器到测试许可的因果时序。不能把清单存在解释为已验证的安全功能。 |
| [Rastegarpanah et al. 2021，§Experimental setup，PDF p. 6（PDF 页索引 5）](https://publications.aston.ac.uk/id/eprint/48004/1/rastegarpanah-et-al-2021-towards-robotizing-the-processes-of-testing-lithium-ion-batteries.pdf)：**同行评审相邻研究** | 对**退役模块**做机器人 EIS 测试；腕部电连接报警以灯/蜂鸣提示，然后方法正文写由**操作员**运行测试软件。它直接显示“已观测电连接”和“谁启动测试”可分属不同环节。`PEER-REVIEWED ADJACENT MECHANISM` | 这是退役模块实验，不是制造端 Pack EoL；报警逻辑未证明目标工位的自动许可或安全互锁。论文摘要“no human intervention”的概括强于方法正文，本文按具体方法保守解读。 |

**Pack 推论。** 对插完成证据在不同设计中可以是力/距离或感应片；这些只覆盖各自定义的机械状态。DMC 的连接检查示例和退役模块 EIS 实验支持“另设电气接触确认是可行/已有先例”，但不能证明目标 Pack 工位一定需要独立电气确认，更不能证明它已把该确认连接到高压/功能测试许可。目标 Pack 的接口类型、允许力、接触验证、测试仪接受信号、许可判定者、互锁以及断开时序均为 `UNKNOWN`。因此 Pack Safety Gate 与 Evidence Gate 在这些细项仍 OPEN。

## 3. Candidate A：能够证实什么

| 来源身份及定位 | 公开资料具体支持 | 它没有证明什么 |
| --- | --- | --- |
| [ABB Baden，Automation solutions 段](https://new.abb.com/news/detail/66300/robots-for-sustainable-mobility)：**企业实际配置披露** | IRB 4600 做来料扫码/测电压/极性检查及按需翻转，随后以专用夹具将电芯装入模组；另一机器人负责激光焊。文中也提及工人装托盘、激光焊之前的 scanner、人工接 connector、MOM/MES。`DIRECT COMPANY DISCLOSURE` | 没有公开每颗电芯释放后的几何确认、完成位、损伤检出、焊接前的 cell-placement 接受条件或放置失败恢复。前置 scanner 和来料 NOK 排除均不能充当放置确认。 |
| [US8519715B2，说明书的 monitoring device、权利要求 16–18](https://patents.google.com/patent/US8519715B2/en)：**不同模组设计专利** | 在电芯插入前监视接收位是否空，释放后监视是否正确插入；camera、laser、ultrasonic、weight 为可选机制。`EVIDENCED MECHANISM` | 是多颗纵向电芯/接收孔方案，不是 ABB 单颗入壳的实装证明，也没有 ABB 的误检率或放行时序。 |
| [CN115207432B，权利要求和方法步骤二、三](https://patents.google.com/patent/CN115207432B/zh)：**方形模组工作站专利** | 机器人逐件摆放，堆叠工装约束放置后位置，后续整形工作台以压力/位移控制整体几何；质量责任可在放置和后续整形之间分布。`EVIDENCED MECHANISM` | 不应把工装“保障位置度”改写为“逐颗释放后有测量验收”；也不证明 ABB 使用同一工装或整形流程。该专利中“100%”等效果声明未经独立现场验证。 |
| [CN117010678B，说明书步骤 4031–4032、4051–4055、501–518 和应用段](https://patents.google.com/patent/CN117010678B/zh)：**另一模组装配数据复核专利** | 装配后相机按顺序读电芯 ID，PLC 对照预存顺序；控制设备/MES 查工艺数据完整性及绑定资格，结果返回 PLC 决定正常出站或 NG。`EVIDENCED MECHANISM` | 编码/顺序和工艺记录复核不等同于几何公差、无损伤或焊接质量验收；不是 ABB 的 MES 逻辑。此专利已有“信息检查后放行”的较直接先例，不能把它当成本论文的新发现。 |

**Candidate A 推论。** “电芯被放入”至少可能涉及三个不同接受对象：该接收位置的实物是否正确、整体 stack geometry 是否满足后续工艺要求、标识与工艺记录是否允许模组出站。上述专利分别给出机制先例，**不是一个整合产线**。ABB 只支持其机器人作业和部分上下游操作；其逐颗/整堆放置确认、焊接前具体放行者及不合格恢复仍为 `UNKNOWN`。Candidate A 可用来检验 Framework 是否会误将入壳动作等同于最终质量接受，但现阶段不能据此比较 ABB 与其他架构的验收能力。

## 4. 两案共用的最小记录办法

建议只在现有 Week 08 功能卡里，针对**每个可能影响下一动作的状态**补一条短记录，不另立一套庞大模型：

| 字段 | 必答的问题 |
| --- | --- |
| `State claim` | 究竟断言什么已完成？连接已插合、接触已被测试仪接受、电芯在接收位、还是记录允许出站？ |
| `Observable evidence` | 哪一个信号实际观测了该状态？来源是否是目标配置？`UNKNOWN` 可以保留。 |
| `Decision owner / next action` | 谁依据什么规则允许哪一步？只知道传感器而不知道判定者时，放行链仍 `UNKNOWN`。 |
| `Failure route / blind spot` | 未通过会停止、重试、人工介入还是流入 NG？该信号**无法**看见何种重要失效？ |

`State claim` 与 `Decision owner` 属于功能/验收责任映射的操作化内容，与已有 PPR、质量关口和控制系统思想相邻；**不主张“completion/acceptance authority”是新概念**。它的项目价值仅在于提高现有 Task/Condition/Safety/Evidence Gates 的填报准确性，防止将执行器能力误认为测试或生产系统的放行能力。若下一轮对两个案例都无法稳定填写这些字段，应删除该新增字段，保留现有框架。

## 5. 决策与下一步唯一核心问题

1. 对原问题作**修正**：不存在经这些资料确认的跨案例“一个最小信号”。应先指定要放行的下一动作，再追溯其所需的可观测状态、决策者与未覆盖的失效模式。`ANALYTICAL INFERENCE`
2. Pack EoL 的最重要证据缺口：**同一具体工位**从机械插接判断，经电气/通信接受，到测试或上电许可的完整条件链。`UNKNOWN`
3. Candidate A 的最重要证据缺口：**ABB 配置**中单颗放置/模组状态如何在焊接前确认、谁允许转序以及失败如何处置。`UNKNOWN`
4. 当前不能据此回答哪类机械臂、专机或人工作业更优；不得用专利效果语句、供应商清单或相邻退役模块实验证明同条件性能。`ANALYTICAL INFERENCE`

**下一步唯一核心问题**：在现有资料可及性下，能否找到**一个明确配置内**的“传感/测试输出 → 判定规则 → 允许的下一动作 → 异常路径”证据链，足以把一个 Gate 从 OPEN 改为可审查的条件判断？先检查 Pack EoL；若始终无同工位证据，就把它列为实施时必须向工厂索取的接口信息，不继续用跨来源拼接填空。

## 6. 检索范围和局限

2026-09-30 使用公开网页作**定向**复核，围绕“connector seating / connection check / test permission”和“cell placement verification / module discharge / MES”搜查：先查已有 Week 08 文献与专利的权利要求和实施方式，再沿同任务 Pack EoL 流程、模块装配质量专利、同行评审相邻测试实验找反例。逐项对照直接对象、生产层级、生命周期、可观测量、放行者。未做数据库全量检索、引文网络穷尽或系统综述；Web of Science 访问受限，不能据此作“无研究”结论。专利只证明公开设计；公司网页只证明其披露；同行评审退役模块实验仅支持边界明确的机制迁移。
