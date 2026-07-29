# Week 03 — Cell Finishing × AGV 基础学习

## 本周定位

第三周不是“证明 AGV 是最佳方案”，也不是开始计算 ROI 或建立复杂仿真。

本周只做一件事：把 **化成—老化—终检之间的托盘物流** 这个学习型案例读懂，使后续能够提出一个具体、可验证的问题。

当前场景边界：

```text
完成cell assembly并进入后处理的电芯
→ soaking / pre-charge / formation
→ aging and EoL testing
→ grading / sorting

研究关注：承载电芯的 tray / goods carrier 在设备、缓存区和存储区之间的运输。
研究暂不关注：化成电流协议优化、电化学模型、AGV底盘控制算法、整厂所有物流。
注意：注液、临时封口、排气、二次注液和最终封口的顺序依工艺路线而变，Day 2再依据原文核查。
```

## 本周学习目标

1. 能用自己的话解释 cell finishing 各工序的目的、输入、输出和先后关系。
2. 区分 cell、tray、formation channel、formation cabinet/rack、buffer、aging storage 和 EoL test station。
3. 理解 AGV 系统的基本构成：车辆、路网、取放接口、调度系统、充电、停车和安全。
4. 画出第一版托盘运输任务链，但不填未经证实的节拍、载荷和成本数字。
5. 把“已知事实、工程推断、未知数据、候选 research gap”分开记录。

## 本周明确不做

- 不建立 AGV 数量优化模型；
- 不比较很多调度算法；
- 不承诺最终论文一定以 AGV 为唯一对象；
- 不把供应商节省比例当作学术结论；
- 不强迫自己在第三周写出最终 research gap。

## 文件

- `01_导师所说的gap是什么.md`：解释 gap 的含义和当前候选缺口。
- `02_第三周学习计划.md`：本周正式工作规划，包含唯一核心问题、Day 1–5、最低目标、可选扩展和三方职责。
- `03_核心文献阅读地图.md`：cell finishing 与 AGV 两侧的核心来源和阅读问题。
- `04_进度与决策日志.md`：记录当前进度、已作决定和暂缓决定。
- `05_GPT_Codex共同研究结论.md`：整合两位 AI 研究同事的共识、分歧与阶段性路线。
- `day1_scope_evidence_learning_guide.html`：Day 1师兄带教版导学笔记，训练研究边界与证据纪律。
- `day2_cell_finishing_process_learning_guide.html`：Day 2工艺带教笔记，理解formation、aging、EoL及其条件性物流含义。
- `day3_tray_flow_and_transport_events_learning_guide.html`：Day 3托盘流带教笔记，拆解满/空托盘、运输任务生命周期、四种时间及blocking/starvation。
- `day4_agv_system_and_handover_learning_guide.html`：Day 4 AGV系统带教笔记，区分生产控制、车队决策、车辆执行与设备交接，并说明VDA 5050的作用与边界。
- `day5_real_battery_agv_case_learning_guide.html`：Day 5真实充电电池工厂AGV案例导学笔记，区分真实记录、模拟器验证、报告结果与不可外推内容。
- `06_Week03总结_Week04计划_组会PPT提纲.md`：Week 03研究总结、可直接拆页的组会PPT提纲，以及Week 04最近邻文献/反例检索计划。

## 本周完成标准

第三周结束时，能够不借助宏观术语回答：

> 一盘电芯为什么需要从 A 点运到 B 点？运输请求何时产生？谁发出请求？AGV 与什么设备交接？迟到、送错、无缓存或车辆不可用分别会造成什么后果？其中哪些事实已有文献支持，哪些仍需要专家确认？
