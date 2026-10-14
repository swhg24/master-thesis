# 历史检索导出 Provenance Manifest（轻量登记，非正式 Query Run 登记）

> 性质：只读溯源整理记录；不是论文 Results，不是正式 Query Run 登记。
> 建立日期：2026-10-13（Week 9 Day 2）
> 范围：四份历史 Scopus / IEEE Xplore 导出文件的 provenance 登记；不含全量文献筛选、不含 Claim Matrix 更新、不含架构比较。
> 约束：四份原始导出保存在本地私有目录，**不提交公共 GitHub**；本 manifest 只记录溯源信息，不含完整导出数据。

## 1. 导出文件清单（Manifest）

| 本地 ID | 数据库 | 本地私有路径 | SHA256 | 数据行数 | 非空 DOI | 空 DOI | 导出时间戳（文件名） | 文件 mtime（本地） |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `EXP-SCOPUS-01` | Scopus | `/home/cjh528132/下载/export_233a87f0-836c-41cb-9056-836d016f1eae_2026-09-28T074657.104670074.csv` | `cbf80aac…f31cbf8` | 68 | 52 | 16 | `2026-09-28T07:46:57.104`(UTC) | 2026-09-28 15:47 |
| `EXP-IEEE-01` | IEEE Xplore | `/home/cjh528132/下载/export2026.09.28-04.11.21.csv` | `8235ad4e…5e5dffef` | 9 | 9 | 0 | `2026.09.28-04.11.21` | 2026-09-28 16:11 |
| `EXP-IEEE-02` | IEEE Xplore | `/home/cjh528132/下载/export2026.09.28-04.13.29.csv` | `c7b4d793…dce798646` | 25 | 25 | 0 | `2026.09.28-04.13.29` | 2026-09-28 16:13 |
| `EXP-IEEE-03` | IEEE Xplore | `/home/cjh528132/下载/export2026.09.28-04.16.20.csv` | `9fddfefa…8d0aa431` | 3 | 3 | 0 | `2026.09.28-04.16.20` | 2026-09-28 16:16 |

SHA256 全值：

- `EXP-SCOPUS-01` = `cbf80aac683e5f50a5254ddde2202303faa16f5f18071271f39b84848f31cbf8`
- `EXP-IEEE-01` = `8235ad4ebec2a462928f85d50bb571c1f69ce74f358e71481b8575fa5e5dffef`
- `EXP-IEEE-02` = `c7b4d793912513d00385899ed8c7a5b611e928b63da74a99f0b4f09dce798646`
- `EXP-IEEE-03` = `9fddfefabb12489b56c5c5cc0c8366d661f31d0dcc4aff25bc36221c8d0aa431`

表头标识字段（已只读核对）：

- Scopus：`Authors, Author full names, Author(s) ID, Title, Year, Source title, Volume, Issue, Art. No., Page start, Page end, Cited by, DOI, Link, Abstract, Author Keywords, Index Keywords, Document Type, Publication Stage, Open Access, Source, EID`
- IEEE（三份一致）：`Document Title, Authors, Author Affiliations, Publication Title, Date Added To Xplore, Publication Year, Volume, Issue, Start Page, End Page, Abstract, ISSN, ISBNs, DOI, …, Document Identifier`

## 2. 检索参数状态（严格区分 VERIFIED / PARTIALLY VERIFIED / UNKNOWN）

| 参数 | 状态 | 说明 |
| --- | --- | --- |
| 导出文件存在 + SHA256 | **VERIFIED** | 已找到并只读取 SHA256 |
| 数据行数 | **VERIFIED** | 68 / 9 / 25 / 3，与 [14_public_source_checkpoint](./14_public_source_checkpoint_2026-09-28.md) 一致 |
| 导出日期 | **VERIFIED** | 文件名时间戳 + 文件 mtime 均为 2026-09-28 |
| 检索运行时间 | **UNKNOWN** | 导出时间戳**不等于**实际检索运行时间 |
| 实际 Boolean 检索式 | **UNKNOWN** | 未在任何文件记录 |
| 实际检索字段 | **UNKNOWN** | `TITLE-ABS-KEY`/`Abstract` 仅为 [12_three_database_run_sheet.md](./12_three_database_run_sheet.md) 的拟定基准，非执行记录 |
| 过滤器 / 时间范围 | **UNKNOWN** | 未记录；`EXP-SCOPUS-01` 内年份分布为 1989 至 2026（修正见下方 1989 年记录注） |
| 命中数（hit count） | **UNKNOWN** | 68 是导出行数，非命中数 |
| 各导出 ↔ 查询对应关系 | **UNKNOWN** | 无任何映射记录 |

**日期证据等级（明确区分）**：导出日期（文件名时间戳 + 本地 mtime，本地时区）为**直接文件级证据**：VERIFIED；检索实际运行时间为 UNKNOWN——文件 mtime 只能证明文件写入时间，不能证明查询执行时间，二者不得混用。

**1989 年 Scopus 记录修正（VERIFIED）**：`EXP-SCOPUS-01` 含 1 条 1989 年记录——`Speak up for quality`，Source title = Manufacturing Engineering，Vol. 103，pp. 67–68，Document Type = Article，无 DOI，EID `2-s2.0-0024754794`。该记录超出协议检索边界 `2000-01-01` 下限，说明该导出**未按协议时间下限截断**（协议拟定的 2000–2026 范围未在该导出中得到执行证据支持）。处理：screening 时按"超出时间范围 + 主题无关"单独登记（预期 `E1_WRONG_DOMAIN`），不静默计入有效文献，当前仍计入 68 行总数。

**结论：这四份文件是"历史导出文件"，不是满足协议 §10.1 可复现要求的正式 Query Run。** 不得将其登记为已完成的正式检索，也不得以导出时间冒充检索运行时间。

## 3. 重复与版本关联核验结果

### 3.0 计数口径

- 原始导出行数合计 = 68 + 9 + 25 + 3 = **105 行**。
- 初步去重后不同书目记录数 ≈ **98**（105 − 7 组跨库 DOI 重复）；其中 82 个唯一 DOI、16 条无 DOI。
- **"98 / 82"是初步去重后的书目记录数与唯一 DOI 数，不是最终纳入论文数。** 最终纳入论文数需经 title/abstract 与 full-text 筛选后另行统计，且不等于 98。

### 3.1 跨库 DOI 重复（VERIFIED：7 组）

`EXP-SCOPUS-01` 与 `EXP-IEEE-01` 共有 **7 个相同 DOI**；其余两两组合为 0：

- `10.1109/access.2024.3402553`
- `10.1109/icesc60852.2024.10690142`
- `10.1109/icesc65114.2025.11212501`
- `10.1109/icsgce.2018.8556831`
- `10.1109/iementech202669403.2026.11434113`
- `10.1109/jestpe.2018.2852218`
- `10.1109/pedes61459.2024.10961241`

### 3.2 Scopus 内部同名记录（rows 8 & 37）—— 非真重复，保持为不同书目记录

| 字段 | 记录 A | 记录 B |
| --- | --- | --- |
| Title | 5th International Conference of IFToMM Italy, IFIT 2024 | （同名） |
| Year | 2024 | 2024 |
| Document Type | Conference review | Conference review |
| Source title | Mechanisms and Machine Science | Mechanisms and Machine Science |
| Volume | **163 MMS** | **164 MMS** |
| EID | `2-s2.0-85201209526` | `2-s2.0-85200785606` |
| DOI | （空） | （空） |

**判定：不是同一条目的重复。** 两条均为同一会议（IFToMM Italy IFIT 2024）的 proceedings 综述条目（`Conference review`），但分属两个不同卷次 163 MMS 与 164 MMS，EID 不同、无 DOI、无作者。**保持为两条不同书目记录，不得自动合并或删除。** 是否排除，在 screening 时按研究相关性决定；`Conference review` 类型本身不作为充分排除理由，如确需排除则按实际主题登记相应原因码（如 `E3_NO_ROBOTICS_DECISION` 或 `E4_WRONG_TASK`）。

### 3.3 S027 版本关联（VERIFIED：预印本 → 正式发表）

- 正式发表版（主记录）：`EXP-IEEE-02` 中 **AI-based Framework for Robust Model-Based Connector Mating in Robotic Wire Harness Installation**，DOI `10.1109/CASE58245.2025.11164054`，IEEE CASE 2025（17–21 Aug. 2025）。
- 预印本：arXiv `10.48550/arxiv.2503.09409`（`2503.09409`）。

**判定：同一研究，预印本 → IEEE CASE 2025 正式发表版本。** 处理：CASE 2025 作为 primary/peer-reviewed 主记录，arXiv `2503.09409` 作为预印本版本链接保留；**不新建第二独立 Source**（版本链接关系，而非两条并列来源）。

> 作者说明：arXiv `2503.09409` 的 v1（2025-03-12）与 v2 均与 IEEE CASE 2025 记录一致，列出**六位作者**——Claudius Kienle、Benjamin Alt、Finn Schneider、Tobias Pertlwieser、Rainer Jäkel、Rania Rayyes。旧 Screening Log 中 S027 仅登记四位作者，属**不完整的书目登记**；因此不能用作者人数差异声称 Rainer Jäkel 与 Rania Rayyes 是会议发表时新增的作者。

### 3.4 与现有账本的关联核验（VERIFIED）

- **S001** `10.1177/0959651821998599`（Rastegarpanah 2021, roboting testing of Li-ion batteries）→ 已存在于账本，且出现在 `EXP-SCOPUS-01`。**无新增。**
- **S017** `10.1016/j.rcim.2025.103183`（Huang 2026, snap-fit plug connector disassembly）→ 已存在于账本，且出现在 `EXP-SCOPUS-01`。**无新增。**
- **S027** 的 CASE 2025 发表版为新增派生记录（见 3.3），其 arXiv 预印本已在账本。
- 现有账本 26 个唯一 DOI；`EXP-IEEE-02` 与 `EXP-IEEE-03` 的 28 个 DOI **尚未直接匹配现有账本**；其中至少 S027 的 CASE 2025 发表版对应已登记预印本 `2503.09409`，其余为候选、未入库。

## 4. 建议优先初筛清单（仅列候选，不批量入库、不判相关性）

**P0 — 版本链接动作（先行）**

- S027 CASE 2025 发表版 `10.1109/CASE58245.2025.11164054` —— 与 S027 合并为主记录（预印本→发表版），不建新 Source。

**P1 — 连接器/插入机制候选（来自 `EXP-IEEE-02` 与 `EXP-IEEE-03`，均尚未入账本，待 title/abstract 初筛）**

连接器/插接直接相关：

- Vision-based Six-Dimensional Peg-in-Hole for Practical Connector Insertion — `10.1109/icra48891.2023.10161116` (2023)
- Efficient Online Learning of Contact Force Models for Connector Insertion — `10.1109/icra55743.2025.11127717` (2025)
- Tactile-Sensitive NewtonianVAE for High-Accuracy Industrial Connector Insertion — `10.1109/iros47612.2022.9981610` (2022)
- Estimation of connector insertion state based on phase spectrum of waves — `10.1109/sdf-mfi59545.2023.10361474` (2023)
- Tactile-Guided In-Contact Robotic Insertion via Physically Consistent Force-Array — `10.1109/lra.2026.3734929` (2026)
- Preprocessing-Based Planning for Contacts in Semi-Structured High-Precision Insertion — `10.1109/lra.2023.3309592` (2023)
- Zero-Shot Peg Insertion: Identifying Mating Holes and Estimating SE(2) Poses — `10.1109/iros60139.2025.11246336` (2025)
- A Novel Connector-and-Gripper Design for Precision Robotic Peg-in-Hole — `10.1109/ieem63636.2025.11357806` (2025)
- Enhanced Real-Time Robotic Assembly Mating Success Detection — `10.1109/aim65483.2026.11658260` (2026)

装配/接触机制相关（次优先）：

- Force Plates for Analyzing, Recording and Teaching Forces of Dis-/Assembly — `10.1109/case58245.2025.11163935` (2025)
- Improved Contact Stability for Admittance Control of Industrial Robots — `10.1109/iros58592.2024.10802440` (2024)
- Industrial Cabling in Constrained Environments — `10.1109/sii59315.2025.10870901` (2025)
- Precision Assembly and Positioning System for Industrial Robots Based on Machine Vision — `10.1109/iciics67880.2026.11483492` (2026)

**P2 — 暂缓/低优先级**

- `EXP-SCOPUS-01` 68 条宽检索：先完成内部无 DOI 去重与 IFToMM 两卷人核，再逐条初筛。
- `EXP-IEEE-01` 9 条：与 Scopus 有 7 条重复，其余多为误检（见 14 号笔记），低优先级。
- `EXP-IEEE-02` 中明显偏题的 ROV/充电站/门开启/水下 UVMS/运动规划类记录：初筛时按 `E3`/`E4` 快速排除，不进入 P1。

## 5. 立即不做的事

- 不批量向 Screening Log 新增来源（仅保留本 manifest，作为后续筛查的输入）。
- 不更新 Claim Matrix。
- 不进行任何架构比较。
- 不 commit / 不 push（本文件为未跟踪新文件，待审核）。