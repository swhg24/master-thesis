# 2026-09-29 过程记录：Candidate A 公开资料初筛

> 记录性质：Week 08 的 `F0–F3` 初筛和反例审计；不是论文 Results，也不是 Candidate A 完整准入或架构选型。
> 当前案例角色：Pack EoL 测试接插件操作仍是深参考案例；Candidate A 是待准入的相邻案例。只使用公开资料。

## 1. 本轮具体问题与可评价对象

问题：**电芯识别、筛查、调向和入模组任务中，哪些要求来自具体电池产品与工装，哪些要求真正区分机器人或专用自动化配置？**

主锚点是 ABB Baden 的**锂离子电池模组制造**单元，不是电芯制造。ABB 2020 年企业案例披露：工人通过托盘送入电芯和模组壳体；IRB 4600 所在装配单元读取单颗电芯 QR 码、测量电压、检查极性并按需翻转，然后以专用夹具把电芯放入相应模组壳体；IRB 6620 执行后续激光焊接。ABB 披露电芯之间仅留数毫米且在该设计中不得相互接触；这不是公开的放置公差。[A1，§“Automation solutions”](https://new.abb.com/news/detail/66300/robots-for-sustainable-mobility)。

为避免将整线能力归给机器人本体，保留两个嵌套边界：

1. **工位功能链**：工人送入电芯与壳体 → 身份/电压/极性检查及不合格品排除 → 必要的调向 → 电芯入壳 → 后续人工接线及激光焊接。用于检查各功能由谁承担；不将整线产能算作单次抓放性能。
2. **核心比较任务**：已经通过相应筛查且方向正确的电芯，从待定义的供料状态进入指定模组壳体位置，保持该产品规定的无损伤、间距/接触状态，并取得可定义的放置完成确认。此为分析性边界；ABB 未披露完整放置验收信号或公差，不能把该描述冒充现场验收规范。异常路线至少包括不合格电芯排除，但具体回流/返工流程未知。

ABB 的 2023 年 BORDLINE ESS 文章描述高功率方形 LTO 电芯及 Baden 半自动模组线；它为产品/产线语境提供线索，但没有逐件证明 2020 年案例中的每个电芯或每种工况都是同一配置。[A2，§“Modular high-performance batteries”及“Production and testing of modules”](https://www.abb.com/global/en/company/innovation/news/bordline-ess)。

## 2. `F0–F3` 初筛结果

| Gate | 当前结论与证据身份 | 仍需查清的最小字段 |
| --- | --- | --- |
| `F0` 生产层级与机器人相关性 | **PASS（案例存在层）**：ABB 直接披露模组制造中的 IRB 4600 电芯入壳任务；工业机器人确实是可评价的执行者。[A1，§“The application”及“Automation solutions”](https://new.abb.com/news/detail/66300/robots-for-sustainable-mobility) | 具体模组/电芯配置及生产变型范围。 |
| `F1` 对象、源/目标与完成 | **PARTIAL / OPEN（目标部署层）**：电芯来自工人送入的容器/托盘，目标是相应模组壳体；QR、电压和极性检查、排除与调向有披露。公开资料没有给出单颗电芯放置的信号、几何验收、损伤判据或异常后状态。[A1，§“Automation solutions”](https://new.abb.com/news/detail/66300/robots-for-sustainable-mobility) | 源端位姿范围、目标槽位/工装约束、放置确认信号、排除/返工流向。 |
| `F2` 动作与责任边界 | **PARTIAL**：ABB 披露工人送入、IRB 4600 装配、IRB 6620 焊接、扫描器识别托盘放入，以及人工后续接线；未披露各传感器、夹具、PLC 与机器人控制器在放置确认和恢复中的详细责任。[A1，§“Automation solutions”及“Smooth commissioning”](https://new.abb.com/news/detail/66300/robots-for-sustainable-mobility) | 抓取面/接触限制、工具动作、位置确认和失败恢复责任。 |
| `F3` 电池特异影响、反例与比较基线 | **有条件支持，仍 OPEN**：ABB 的带电敏感电芯和该模组的不得接触约束会影响抓取/放置与安全设计；但这种电芯间关系不是通则。TUM 模组研究中的方形 PHEV1 液冷设计要求电芯直接接触。[A1，§“Automation solutions”](https://new.abb.com/news/detail/66300/robots-for-sustainable-mobility)；[A3，§4.1–4.3，PDF pp.4–5](https://wrap.warwick.ac.uk/id/eprint/88360/3/WRAP-application-physical-flexibility-software-reconfigurability-Ahmad-2017.pdf) | ABB 具体间距/接触/无损伤验收；不同配置在同条件下的实现和数据。 |

**准入决定：** Candidate A 的机器人相关性已通过初筛，足以继续公开资料的任务与证据调查；`F1/F2/F3` 的关键验收和条件字段仍 OPEN，因此**尚未进入完整架构适用性分析**，也没有跨案例验证 Framework v1.0。缺失信息不能记作技术不可行。与本库 `11`、`13`、`14` 的一致性检查表明 Pack EoL 的目标 Task/Condition/Safety Gate 仍 OPEN；`11` 的旧表述必须按其第 8 节纠偏阅读。[Pack 公开资料检查点](14_public_source_checkpoint_2026-09-28.md)。

## 3. 反例与可迁移边界

- [A4 Rosendahl BMe STACK，产品页“expertise”](https://rosendahlnextrom.com/bm/products/lithium-ion-machines/stacking/)同时列出堆叠机器人和龙门系统用于电芯抓放，并列出对齐/堆叠、压紧及入壳等子工序。**供应商方案披露**足以推翻“方形电芯必需六轴机器人”的一般性主张；不证明龙门系统在 ABB 的相同工装和验收条件下能完成全部任务。
- [A5 Marposs 方形电芯模组线入线检测方案，DESCRIPTION](https://www.marposs.com/eng/application/automatic-line-for-prismatic-cells-electrical-testing)把视觉表面/极性检查、笛卡尔机械手调向与电性能测试安排在不同站。**供应商方案披露**说明检测/调向可由工位系统分担；该设备没有披露“将单颗电芯放入 ABB 模组壳体”，不能作为完整同任务性能比较。
- [A3 Chinnathai 等，Procedia CIRP 63 (2017)，DOI 10.1016/j.procir.2017.03.128，§4.1–4.3，PDF pp.4–5](https://wrap.warwick.ac.uk/id/eprint/88360/3/WRAP-application-physical-flexibility-software-reconfigurability-Ahmad-2017.pdf)描述 TUM 实验模组单元的机器人、线性轴和可调真空夹具，以及因液冷而要求电芯接触的产品设计。**同行评审实验/相邻模组案例**支持“产品设计改变抓取与装配要求”；不提供 ABB 工位的数值或六轴必要性。
- [A6 上汽集团 2026-03-27 官方披露，§“从‘实习生’到‘正式工’”](https://www.saicmotor.com/m/xwzx/xwk/2026/64052.shtml)把“能仔 1 号”的电芯抓取/上料明确放在 E7 **Pack 制造**语境。公开页面和已核看的剪辑没有给出最终接收设备或放下后的验收状态。它是另一个部署语境，不能拼接 ABB 的**模组**目标路径；上汽公布的效率、定位与占地数值仅为企业自述，不进入同条件性能比较。

## 4. 当前可写的推论与停止点

目前能提出的**待检验机制**是：若检测、调向和定位已由独立设备消除大部分不确定性，核心搬放任务可能适合较受约束的机构；若同一单元需承担多种姿态调整与工序复用，配置灵活性可能有价值。这些是分析推论，缺少同边界条件与性能证据，不能写成六轴、龙门、移动双臂或人形的优劣结果。对单一封闭工位，也未见跨工位移动或双臂协作价值已被证实。

**下一次唯一学习问题：** 同一“已筛查电芯 → 指定模组位置”任务下，抓取面、姿态变化、工装定位、放置确认与异常处理分别由什么配置承担？最低目标是找到或明确否定公开资料能否给出放置完成的可观察判据，并保持 ABB 与其他供应商方案的任务边界分离。若找不到，继续标 `UNKNOWN`，只保留条件性比较；不追造现场节拍、成本或精度。
