# Week 2 Group Meeting Slides Outline / 第二周组会 PPT 提纲

**Thesis:** Robotic Systems in Battery Manufacturing: Potentials, Applications, and Implementation Strategies  
**Meeting date (working assumption):** 2026-07-22  
**Recommended length:** 9–11 slides; 10–12 minutes

> 这是明天制作 PPT 的内容骨架，不是正式论文结论。当前目标是汇报 Week 2 如何建立 evidence-based process/problem/robotics map，而不是宣布最终案例排名或 ROI。

## Slide 1 — From Battery Manufacturing Processes to Evidence-Based Robotic Use Cases

Subtitle: Week 2 progress: process requirements, robotic roles, evidence gaps, and candidate cases

中文开场：这一周我没有急着选择最终案例，而是沿着电极制造、电芯装配和电芯后处理建立“工艺目标—质量风险—任务—机器人角色—所需证据”的分析链。今天汇报系统理解、四个候选场景，以及下一步需要的专家和数据。

## Slide 2 — Research Direction Updated After Last Meeting

**Key message:** Scope, method, and cases should emerge from evidence rather than be fixed prematurely.

- 导师反馈：不能只依赖文献，还需专家观点和/或生产数据。
- 电芯制造范围内暂时保持开放；cases 是候选，不是最终结果。
- 新增评价维度：data availability 与 expert accessibility。

```text
旧倾向：先定 scope → 选案例 → 找支持材料
新路径：映射问题 → 收集证据/数据 → 比较研究价值 → 收敛 scope
```

证据标签：**Supervisor guidance**，见 `supervisor_meeting_growth_log.md`。

## Slide 3 — Week 2 Learning Logic

```text
Process objective → quality/safety risk → required task
→ robotic role → system interfaces → evidence and missing data
```

1. Day 1: Process–problem map
2. Day 2: Electrode manufacturing
3. Day 3: Cell assembly
4. Day 4: Cell finishing and intralogistics
5. Day 5: Vision-guided inspection and loading

讲法：五天不是五个孤立主题，而是用同一语法读每个工序，避免看到机器人动作就直接判断“适合自动化”。

## Slide 4 — Three Production Stages, Three Robotics Logics

| Stage | Material state | Main logic | Likely robotic role | Main constraint |
| --- | --- | --- | --- | --- |
| Electrode manufacturing | Powder, slurry, foil, web | Continuous stability | Logistics, sampling, inline inspection support | Speed, defect traceability, dry/clean conditions |
| Cell assembly | Thin sheets, separator, stack/jelly roll | Precision, damage-free assembly | Vision handling, positioning, insertion, inspection | Flexibility, alignment, particles, format |
| Cell finishing | Sealed cells, trays, racks | Activation, testing, storage, sorting | Tray handling, test loading, AMR/AGV | WIP, scheduling, safety, identity/data |

讲法：电极制造由连续专机主导；装配核心是薄软与精度；后处理对象更标准，但物流、追溯和异常安全突出。

## Slide 5 — Evidence-Based Process–Problem–Robotics Map

| Process problem | Required task | Robotic/system role | Evidence gap |
| --- | --- | --- | --- |
| Electrode defects propagate | Detect early, retain position | Inline vision + traceability | Natural defects at target speed |
| Thin sheets deform/misalign | Locate, grip, place, verify | Vision + compliant gripper + post-check | Format cycle time, long-run reliability |
| Formation/aging creates WIP | Move/schedule trays | Handling + AS/RS + AMR/AGV + MES | Flow, availability, abnormal cells |
| EoL decision must match cell | Inspect, identify, sort | Vision + robot + quality gate | FN cost, integration, recovery |

讲法：这张表是本周核心产出。每个机会对应真实问题，并明确证据缺口；否则会把工程推论写成事实。

## Slide 6 — Deep Dive: Formation/Testing Tray Handling

**Key message:** 价值来自标准化对象与复杂系统物流，不是单次 pick-and-place。

- 密封电芯/托盘接口比散装极片清晰。
- Formation、aging、EoL 连接长停留、并行通道、存储、分选。
- 物理流必须与 cell/tray/channel 身份和测试数据同步。
- 异常发热、膨胀、电压或损伤需要隔离策略。
- VDMA 2026 描述专用托盘与 formation racks；其数字是情景值，不是通用值。

缺失数据：任务峰值、质量/公差、WIP、阻塞、恢复、投资和运行成本。

## Slide 7 — Deep Dive: Vision-Guided Inspection and Loading

```text
Imaging → detection/pose → PLC decision → robot action
   ↑                                  ↓
model/version ← QMS/MES record ← recheck/isolation
```

- Choudhary et al. (2022)：882 张图；80/20；precision 88%；recall 84%；模型推理 9.5 ms。
- 边界：图像来自 1.0 m/min、人工引入缺陷的孤立涂布实验；不证明完整量产系统表现。
- 推理时间 ≠ 工作站周期；实验采集速度 ≠ 量产验证速度。

讲法：完整系统还包括照明、标定、传输、机器人、复检、异常分流和 MES。

## Slide 8 — Why “Accuracy” Is Not Enough

| Metric | Meaning | Production implication |
| --- | --- | --- |
| Recall | Real defects detected | Low recall = defect escape |
| Precision | Alarms that are real | Low precision = recheck/scrap/stops |
| POD vs. size | Probability at defined size | Capability limit for NDT |
| End-to-end latency | Image to physical action | Whether takt is met |
| Availability/recovery | Long-run operation | Real throughput, not demo speed |

Evidence: Zangerle et al. (2025) 显示光学与激光热成像对点、颗粒和线缺陷能力不同；选传感器要从缺陷物理出发。

## Slide 9 — Candidate Cases: Compare Without Ranking

| Candidate | Potential value | Main challenge | Evidence status |
| --- | --- | --- | --- |
| Formation/testing tray | Handling, traceability, flow | Scheduling, interface, abnormal cells | Strong process; weak public performance |
| AMR/AGV | Flexible transport, WIP | Fleet, handover, dry-room/fire safety | Broad industry; battery data needed |
| Vision + loading | Quality gate + sorting | Observability, FN, calibration, drift | Good sensing; few complete robot cases |
| Stacking/insertion | Precision, damage prevention | Flexible sheets, particles, speed | Clear need; scarce public parameters |

> These are candidate research cases. No final priority or ROI is claimed.

## Slide 10 — Emerging Evaluation Framework

1. Manufacturing problem severity and relevance
2. Technical feasibility under battery conditions
3. Quality and safety contribution
4. Integration complexity
5. Flexibility and scalability
6. Economic value mechanism
7. Evidence quality
8. Data availability and expert accessibility

- 暂不分配权重或最终评分；先定义指标、证据等级、最低数据要求。
- 分开“potential high”与“confidence in evidence high”。

## Slide 11 — Next Steps and Questions for Supervisor

Next steps:

- Consolidate four cases into one evidence matrix.
- Maintain claim → source → page/section → battery implication → robotics implication.
- Identify PEM/eLab or industry experts in process, quality, logistics and integration.
- Draft interview/data request guide before final case selection.
- Define minimum evidence before scoring or ROI.

Questions:

1. 可接触哪些 formation logistics、machine vision、assembly 或 intralogistics 专家/设施？
2. 是否有可聚合或匿名分享的 pilot/production data？
3. 更适合三个对比案例，还是一个主案例加对照？
4. 下一里程碑优先访谈设计，还是评价框架？

结尾：本周的进展不是选出“最好案例”，而是建立了能说明问题来源、系统边界、证据质量和数据缺口的分析方法。下一步把它转化为可验证的方法论。

## Backup A — Evidence Hierarchy

| Evidence | Use | Limitation |
| --- | --- | --- |
| Peer-reviewed | Mechanism/method/experiment | Often pilot/lab |
| Research institute | Demonstrator/development | Not necessarily series production |
| Industry association | Process architecture/context | Scenario assumptions |
| Vendor case | Existence/integration example | Claims need independent validation |
| Expert/internal data | Real constraints/values | Access, confidentiality, bias |

## Backup B — Data Request Checklist

- Product format, tray geometry, mass, tolerances
- Sequence, average/peak rate, takt distribution
- Defect taxonomy, prevalence, criticality
- Confusion matrix/POD under target conditions
- Pick/place success, repeated failures, recovery
- WIP, waiting, blocking/starving, changeover
- Abnormal-product route and manual intervention
- CAPEX, integration, maintenance, validation, data costs

## Sources for the Actual PPT

- Choudhary et al. (2022): https://doi.org/10.1002/aisy.202200142
- Zangerle et al. (2025): https://doi.org/10.1007/s10921-025-01208-7
- Masuch et al. (2023): https://doi.org/10.3390/pr11010010
- Wessel et al. (2023): https://doi.org/10.1002/ente.202200911
- Kampker et al. (2023): https://doi.org/10.3390/wevj14040096
- VDMA Battery Production (2026), *Production Process of a Lithium-Ion Battery Cell*

> 明天制作正式 PPT 时优先重绘流程图和矩阵，不截图论文图片；数据页在页脚标来源。正式汇报前确认导师期望时长与是否有固定周报模板。
