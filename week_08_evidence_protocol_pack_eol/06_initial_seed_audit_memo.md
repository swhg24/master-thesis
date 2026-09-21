# Pack EoL Initial Seed Audit Memo

> 日期：2026-09-20  
> 性质：seed audit + 第一轮OpenAlex检索校准；不是最终文献综述或完整证据审计  
> 输入：Week 06 已引用来源、已知最近邻论文、2026-09-20 元数据与全文核对

## 1. 已完成的最小动作

- 首轮登记 18 个 initial screening records；same-task设备基线审计后增至20个；
- 建立 17 个 unique claim IDs、21 条 claim–source links；
- 对来源同时标注 production level 与 lifecycle stage；
- 将 direct Pack manufacturing EoL、退役电池 testing、跨行业 connector/harness evidence 分开；
- 首次对 Week 06 的技术类别概括和场景阈值作出删除/降级决定。

这些记录用于启动正式审计。OpenAlex title search与四组field-search pilot已经执行，但广检索噪声很高；这不代表Scopus、Web of Science、IEEE Xplore或正式Boolean field search已经完成。

## 2. 当前最重要发现

### 2.1 Pack EoL任务存在性目前主要由企业直接披露支持

Spirit AI公开页面直接描述了：

- PACK production line；
- manufacturing EOL/DCR final functional testing；
- battery connector insertion；
- flexible wiring-harness plugging/unplugging；
- connection-status inspection。

因此，“该机器人任务被企业公开披露”可以保留。但成功率、节拍、工作量和规模仍只是 company-reported claims，不能作为独立验证的性能证据。

### 2.2 最近的同行评审机器人电池测试研究不是制造端Pack EoL

2021与2025两项robotic EIS battery testing研究非常接近“机器人接触电池端子并执行测试”的物理任务，但研究对象是退役电池/second-life诊断场景，主要位于module level。

它们可以支持：

- robotized battery testing已有先例；
- terminal localization/contact与compliant control可以被研究；
- industrial/collaborative robot testing architecture存在。

它们不能直接支持：

- 新电池制造端Pack EoL的现场流程；
- flexible test connector/harness与battery terminal contact完全等价；
- CATL工位的节拍、安全逻辑或经济性；
- 本论文是第一个研究机器人电池测试的工作。

### 2.3 `EoL`必须强制消歧

制造领域的`end-of-line`与循环经济领域的`end-of-life`会被同一个缩写混淆。后续筛选必须同时记录：

- production level；
- lifecycle stage；
- task relation to the Pack EoL deep case。

只看到标题中的`EoL`不得分类。

### 2.4 跨行业论文目前支持“机制”，不支持Pack EoL性能

汽车线束与电气连接器研究可以支持：

- connector detection；
- in-hand pose uncertainty；
- sensitive/force-guided mating；
- cable separation、entanglement与tension management；
- single-arm/dual-arm handling strategies。

但这些证据目前只能条件保留或等待全文。它们不能直接证明Pack EoL的：

- connector geometry与clearance；
- permissible force；
- harness physical properties；
- cycle time；
- electrical safety；
- industrial reliability。

### 2.5 第一组OpenAlex结果只用于校准检索，不证明文献不存在

- `title.search:robotic battery testing`得到6条，其中两条是当前closest work、一条重复记录、三条是“机器人设备所用电池的测试”而非机器人执行电池测试；
- `title.search:battery pack end-of-line`得到0条；
- `title.search:battery connector robotic`得到1条，为end-of-life EV battery connector disassembly，而非manufacturing end-of-line connector insertion；
- 较宽的`testing lithium-ion batteries`得到575条且绝大多数没有robotics relevance，因此被标为pilot-too-broad，不能作为最终query。

零命中只说明该数据库、该字段和该字符串没有返回结果，不允许写成“没有相关研究”。下一步必须继续field search、同义词扩展、其他数据库和citation chasing。

### 2.6 全文核查进一步缩小了可迁移范围

S004汽车多分支线束全文显示，双臂、视觉、腕部力/力矩、专用夹爪、夹具和任务级编程是在一个具体线束装配配置中组合使用的。该论文直接支持把deformation-dependent perception、cable separation、tension、error detection和entanglement列为候选能力维度；但它不证明Pack EoL具有相同线束结构，也不证明双臂必要或性能数字可迁移。

S018则证明，同行评审的EV电池制造研究已经采用过`process requirement → robot selection → work-cell design → simulation`路线，并把testing/certification放在广义battery-system assembly末端。它的详细对象是module assembly仿真工作单元，而非Pack EoL柔性接插件现场案例。因此，本论文不能把“做task decomposition或设计机器人工作单元”本身当作创新，仍需突出跨架构、条件性和证据边界明确的评价方法。

S006的IEEE官方摘要和引言开头已经核实，但合法开放全文仍未找到，详细偏差范围、实验条件和结果继续保持`PENDING_FULLTEXT`。Unpaywall要求研究者自有电子邮箱；本轮没有伪造邮箱，因此OA状态以OpenAlex和官方平台为当前记录，并保留该限制。

## 3. 第一批审计决定

按 claim–source row 统计的第一轮状态快照：

| 状态 | 数量 | 代表内容 |
| --- | ---: | --- |
| `RETAIN_DIRECT` | 8 | company-reported task/deployment、closest-work存在性、相邻battery-manufacturing方法先例，以及明确标注为企业说法的性能披露 |
| `RETAIN_CONDITIONAL` | 5 | HV/electrical safety、connector mating、flexible-harness mechanism、connection confirmation和cell-safety integration的受限迁移 |
| `DOWNGRADE_ASSUMPTION` | 3 | Week 06责任分配、humanoid适用场景、数值化产品/换型阈值 |
| `REMOVE_UNSUPPORTED` | 2 | “专机天然无感知/力控/恢复”“工业机器人天然具备力控/恢复”等技术类别概括 |
| `PENDING_FULLTEXT` | 3 | 两条仍待全文/详细核查的flexible-harness claim–source links和一条尚待机构全文的connector-mating来源 |

同一个claim可能连接多个来源并得到不同row-level状态。例如C006已经由开放全文S005获得条件保留，但S006仍等待全文。

## 4. 对论文创新性表述的直接影响

当前不能写：

> Robotized battery testing or connector contact has not been studied.

当前可继续检验的research need是：

> Existing studies and industrial disclosures address particular battery-testing or connector-manipulation configurations, while evidence remains fragmented across lifecycle stages, task boundaries and architecture types. A transparent task-based comparison is needed to identify conditional suitability relative to dedicated automation and manual references in selected battery-manufacturing applications.

这仍是待正式数据库检索验证的research-need wording，不是已经证明的novelty claim。

## 5. Framework v1.0已经明确需要修正的地方

1. 增加 `lifecycle_stage`，与production level分开；
2. 架构能力必须按具体configuration审计，不能从类别名称推断；
3. scenario thresholds 默认是assumptions，不是经验边界；
4. `company-reported`必须进入结论语言；
5. cross-industry evidence只能迁移机制/评价维度，不能自动迁移性能；
6. closest-work map必须包含退役电池robotic testing，并说明与manufacturing Pack EoL的差异。

## 6. 第二轮 Week 06 工程主张审计（2026-09-20）

在第一轮来源审计之后，又对 R1–R6 中从“机制”跳到“指定实现”的高影响主张进行了复核。新增 6 条 claim rows：

- `C018`：删除“柔性线束必然要求完整 DLO 状态估计、张力闭环和双臂”；这些是候选方案，不是普遍必要条件；
- `C019`：删除“连接器插合必然要求六维 F/T 和力—位置混合控制”；Framework 应评价功能，而不是预选技术；
- `C020`：将 Week 06 的 PLC/HVIL 时序降级为 reference state model；
- `C021`：将“多型号披露”到“自动换接插件、混线和多工位优势”的推断降级为生产情景；
- `C022`：将 Robot–MES–PLC–Tester 的具体通信拓扑降级为参考架构；
- `C023`：删除“高压安全只存在于电池制造、R3 是唯一完全 battery-specific 要求”的排他性表述。

第二轮后的核心修正不是弱化案例，而是把评价对象从架构标签和预选技术，转为可验证功能：对象状态、残余误差、完成判据、安全许可、异常恢复和信息闭环。

## 7. Same-task设备基线审计（2026-09-20）

Marposs与thyssenkrupp官方Pack EoL资料进一步确认：Pack运输和connector adaptation是两个可独立组合的系统层。公开组合包括`trolley/conveyor/AGV`上料与`manual/automatic HV and communication connection`。这直接反驳了“AGV上料等于移动机器人接线”或“自动接线必然属于某一机器人类别”的隐含假设。

新增S019–S020、C024–C025后，当前总计为：20个screening records、25个unique claims、31条claim–source links；row-level状态为10个`RETAIN_DIRECT`、7个`RETAIN_CONDITIONAL`、6个`DOWNGRADE_ASSUMPTION`、5个`REMOVE_UNSUPPORTED`和3个`PENDING_FULLTEXT`。

Framework v1.0据此新增五层系统分解：

```text
transport
→ Pack positioning
→ connector adaptation
→ test / safety cell
→ information architecture
```

详见`10_same_task_equipment_baseline_learning_note.md`。

## 8. 下一批具体工作

1. 直接使用`08_pack_eol_task_requirements_learning_guide.md`继续学习任务循环和工程机理；`07`的证据判断改为可选自测；
2. 按`09_framework_v1_input_requirements.md`继续定向查找制造端 Pack EoL 安全、连接确认、系统集成和更详细的automatic-adaptation设计；
3. 按QB1、QB2a、QB2b、QB3在Scopus/Web of Science/IEEE Xplore运行正式Boolean检索并登记命中数；
4. 通过RWTH机构权限或作者版本核查S006全文；
5. 用目标参数和设备基线完成 Framework v1.0 decision rules；
6. 在以上工作完成前，不进入Candidate A完整比较。
