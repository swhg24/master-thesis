# Week 08：正式证据协议与 Pack EoL 证据审计启动

> 建立日期：2026-09-20  
> 当前阶段：注册方案设计完成 → 正式研究执行开始  
> 对应注册工作包：WP1 — Scope definition and evidence base  
> 前置基线：`AGENTS.md`、`docs/thesis_registration_consensus_2026-08-20.md`、`docs/research_direction_guardrails.md`、2026-09-18 registration materials

## 0. 当前进度

- 研究基线同步：`COMPLETE — 2026-09-20`；
- Evidence Protocol v1.0与执行模板：`ESTABLISHED — 2026-09-20`；
- Day 1 evidence-reasoning学习材料：`AVAILABLE AS OPTIONAL SELF-CHECK — 07_day1_evidence_reasoning_learning_guide.md`；
- Pack EoL任务与R1–R6工程学习主线：`COMPLETE — 08_pack_eol_task_requirements_learning_guide.md`；
- Framework v1.0需求输入：`PARTIALLY READY — 09_framework_v1_input_requirements.md`；
- Same-task Pack EoL设备基线：`STARTED — 10_same_task_equipment_baseline_learning_note.md; Marposs与thyssenkrupp官方配置已核对`；
- 初始screening：`STARTED — 20 records`；
- Pack EoL claim audit：`STARTED — 25 unique claims / 31 claim–source links; six academic core sources and two same-task official equipment baselines checked; second-round R1–R6 engineering-claim audit complete`；
- 核心数据库正式检索：`STARTED — OpenAlex title searches and four field-search pilots complete; broad field strings proved too noisy; Scopus/WoS/IEEE formal runs still pending`；
- Framework v1.0：`INPUT PREPARATION IN PROGRESS — R1–R6已改写为可审计问题，目标参数与正式decision rules仍待补齐`；
- Candidate A gate：`NOT OPEN`。

## 1. 本周唯一核心问题

> **How can the fixed RQs be converted into a reproducible evidence and case-assessment protocol, and which Week 06 Pack EoL claims survive source-level verification?**

中文：

> **怎样把已经固定的研究问题转化为可复现的证据与案例评价协议，并判断 Week 06 Pack EoL 的哪些主张能够通过来源级验证？**

当前直接带教的内容子问题是：

> **怎样把 Pack EoL 接插件循环拆成可观察的任务状态和系统功能，并在不从架构标签预设能力的前提下，形成有证据边界的配置评价要求？**

本周不重新讨论题目，不重新比较 A/B/C，也不尝试提前得出哪一种机器人架构最好。

## 2. 为什么现在做这一步

Week 06 已经形成：

- Pack EoL connector-handling 的任务边界；
- Robot、tester、PLC/safety、MES 与 fixture 的责任划分原型；
- R1–R6 requirement groups；
- 三类架构的条件化比较；
- `F0`–`F7` Framework v0.1。

但这些成果中混合存在直接证据、相邻证据、跨行业证据、企业披露、工程推断和说明性阈值。若不先完成证据协议和 claim audit，就无法把学习材料可靠地转化为论文 Method、Results 或 Discussion。

## 3. Day 1–5 建议顺序

Day 1–5 是逻辑顺序，不是硬性每日 KPI；前一步没有理解时可以跨天。

### Day 1 — 读懂 Evidence Protocol v1（证据判断练习可选）

- 理解数据库、query block、纳入排除、双轨证据、去重和筛选规则；
- 能解释为什么 Google Scholar 和企业新闻不能单独构成可复现学术证据库；
- 用自己的话区分 `source type`、`case relation` 和 `production level`。

### Day 2 — 建立检索运行记录与 screening log

- 为每个数据库建立 `query_run_id`；
- 原样保存检索式、检索日期、过滤器和命中数；
- 将已有 Week 06 来源先作为 seed records 登记，不把它们自动判为 included。

### Day 3 — 最近邻与 direct Pack EoL 证据优先

- 优先审计 robotized lithium-ion/EV battery testing、Pack EoL、test connector handling；
- 做 backward/forward citation chasing；
- 在最近邻证据审计完成前，不写 `no prior work`、`first framework` 或类似 novelty claim。

### Day 4 — Week 06 高影响 claim 审计

- 先审计 R1–R6、task cycle、responsibility boundary 和三类架构的关键能力主张；
- 每条记录来源、准确位置、支持范围和不可外推边界；
- 分配 `RETAIN_DIRECT / RETAIN_CONDITIONAL / DOWNGRADE_ASSUMPTION / REMOVE_UNSUPPORTED / PENDING_FULLTEXT`。

本轮已额外完成：不再把 R1–R6 当作六条既定事实，而是按任务机理改写为可审计问题；已区分“线束/插接/确认/安全”的任务维度与“变型频率/多工位/brownfield”的生产条件维度。

### Day 5 — 周末检查与 Framework v1.0 输入

- 汇总哪些 claim 可以进入正式案例；
- 哪些只能成为 scenario assumption；
- 哪些字段仍缺证据；
- 将 unresolved fields 交给下一阶段 Framework v1.0，而不是凭常识补齐。

## 4. 最低完成目标

完成以下内容，本周即为合格：

1. `01_evidence_protocol_v1.md` 经学生理解并冻结为 v1.0；
2. 每次正式搜索都有可复现的 query-run 记录；
3. `02_screening_log.csv` 开始登记 seed sources 和新检索结果；
4. `04_pack_eol_claim_evidence_matrix.csv` 至少完成 Week 06 最高影响 claims 的第一批审计；
5. 形成一份 retain/downgrade/remove 决定摘要和 Framework v1.0 unresolved-field 清单。

## 5. 有余力再做

- 对 Candidate A 只执行一次小规模 `F0`–`F3` 准入检查；
- 不进行 Candidate A 的完整架构比较；
- 不打开 Candidate C。

## 6. 本周明确不做

- 不更换题目、RQ 或 Pack EoL deep-case role；
- 不把企业成功率、速度或规模宣传当作独立性能事实；
- 不编造 connector geometry、插拔力、节拍、成本、ROI 或成熟度；
- 不按技术类别预设 dedicated automation 没有感知、industrial robot 一定有力控、humanoid 一定更灵活；
- 不因没有检索到论文就宣布研究空白；
- 不为了形成“结果”而进入仿真或加权总分。

## 7. 学生本周应真正学会什么

周末时，学生应能够不用文件回答：

1. 为什么 source type 与 case relation 是两个不同维度？
2. 什么证据足以支持“该任务存在”，什么证据才可能支持“该架构适用”？
3. 为什么跨行业 connector insertion 论文可以支持物理机制，却不能直接证明 Pack EoL 的节拍或安全性？
4. 为什么 `UNKNOWN` 不等于“不可能”，也不等于 research gap？
5. 一条 thesis claim 怎样追溯到具体来源、页码、证据身份和适用边界？

## 8. 周末决策点

- `PROTOCOL READY`：规则清楚且能够重复执行，进入全面检索与 claim audit；
- `PROTOCOL REVISE`：字段或筛选规则无法稳定使用，先修订协议；
- `EVIDENCE NARROW`：直接证据不足，缩小 Pack EoL 主张，不自动更换 deep case；
- `FRAMEWORK INPUT READY`：已有足够的 verified requirements 和 unresolved fields，进入 Framework v1.0。
