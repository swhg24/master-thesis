# Week 08：正式证据协议与 Pack EoL 证据审计启动

> 建立日期：2026-09-20  
> 当前阶段：注册方案设计完成 → 正式研究执行开始；最近复核 2026-09-30
> 对应注册工作包：WP1 — Scope definition and evidence base  
> 前置基线：`AGENTS.md`、`docs/thesis_registration_consensus_2026-08-20.md`、`docs/research_direction_guardrails.md`、2026-09-18 registration materials

## 0. 当前进度（2026-09-30）

- 研究基线与 Evidence Protocol v1.0：已固定；题目、RQ 和 Pack EoL 深案例角色不重开。
- Screening log：34 条记录；其中 26 条 title/abstract include、4 条 maybe、4 条 exclude。22 条标为跨行业任务类比，直接 Pack EoL 企业披露 1 条、同任务设备基线 2 条。
- Claim audit：33 个独立 claim、39 条 claim–source links；逐行状态为 10 条 `RETAIN_DIRECT`、15 条 `RETAIN_CONDITIONAL`、6 条 `DOWNGRADE_ASSUMPTION`、5 条 `REMOVE_UNSUPPORTED`、3 条 `PENDING_FULLTEXT`。这些数量是审计进度，不代表结论强度。
- 检索：OpenAlex 定向检索和补充 web discovery 已记录；学生提供 Scopus 一组 68 条、IEEE Xplore 三组 9/25/3 条导出，属于已执行的部分检索，尚未逐组完成可复现检索日志及去重筛选。Web of Science 正式结果未收到。细节见 `14_public_source_checkpoint_2026-09-28.md`；Discovery 零新增不能解释为文献不存在。
- 公开原始资料近邻：宁德时代 `CN117718986B` 披露机械臂操作 Pack 测试插头；`CN109856554A` 披露带浮动及检测的专用自动对插机构；ROKAE 与 Repower 官方资料提供另外的配置/工位功能例。专利是方案披露，企业数据是企业说法；不能推出现场同口径性能比较。证据与边界见 `14_public_source_checkpoint_2026-09-28.md`。
- 框架：`09_framework_v1_input_requirements.md` 提供字段；`11_framework_v1_baseline_cards.md` 是同任务三配置基线草稿；`13_framework_v1_decision_table_draft.md` 已把 Gate、证据状态和 Pack EoL 试填写成可检查规则。新近邻纠正了“专机内部机制全未知、机器人仅有跨行业机制”的笼统表述，但尚无正式 Framework v1.0 案例结果或架构优胜判断。
- Candidate A 的公开资料 `F0–F3` 初筛已启动：ABB Baden 的**模组**电芯入壳任务通过案例存在与机器人相关性检查；放置验收、责任细节及同条件比较仍 OPEN，尚未完整准入或验证 Framework v1.0。上汽 E7 的 **Pack** 上料披露保留为另一语境，不能拼接 ABB 任务路径。详见 `15_candidate_a_public_evidence_checkpoint_2026-09-29.md`。
- 2026-09-30 追加了 [16 功能责任审核](16_function_responsibility_audit_pilot_2026-09-30.md)、[17 完成与放行责任](17_completion_acceptance_authority_research_2026-09-30.md)、[18 同配置许可链](18_pack_eol_same_configuration_release_chain_audit_2026-09-30.md)、[19 选型条件反例](19_selection_relevance_counterexample_pilot_2026-09-30.md)与 [20 目标 UNKNOWN 定向检索](20_pack_eol_target_unknown_search_and_variant_boundary_2026-09-30.md)。这些均为 working notes，不是 Framework v1.0 或论文 Results；`Closure Allocation` 不作为新理论。
- Pack EoL：公开专利与设备案例支持不同插接、换型和测试系统机制；小墨目标工位从插接完成到高压/测试许可的同配置条件链、目标参数与同条件性能比较仍 `UNKNOWN`。Candidate A：ABB 模组入壳任务可作相邻案例试填，但放置完成、失败恢复和同条件比较仍 `UNKNOWN`。
- 下一关口：用 Pack EoL 和 Candidate A 的少量功能，检验现有责任映射与四 Gate 能否生成可追溯的**条件性**机器人适用性判断；同时补齐正式检索记录与 closest-work 引文核对。不为补缺口拼接不同专利或制造性能数据，也不启动架构排名。
- 行政注册、签字、正式开始日期和截止日期仍需独立核对，不由研究材料推定。

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
