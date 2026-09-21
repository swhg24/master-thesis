# Evidence Protocol v1.0：机器人系统在电池制造中的任务驱动评价

> 版本：1.0  
> 冻结日期：2026-09-20  
> 协议性质：面向硕士论文的 structured and reproducible evidence search，不在完成前自称完整 systematic review 或 PRISMA review  
> 当前优先案例：Battery-pack EoL test-connector handling  
> 后续准入候选：Candidate A — cell identification, grasping and loading

## 1. 协议目标

本协议用于建立可追溯证据库，以回答当前三个研究问题：

1. 哪些 task/process characteristics 决定不同 robotic-system architectures 的 suitability？
2. 在哪些 technical、economic、quality、safety 与 integration conditions 下，各架构相对 dedicated automation 和 manual references 适用？
3. 比较案例能够导出哪些 implementation strategies 与 remaining research needs？

协议同时服务四个任务：

- 识别 closest work，防止虚构 novelty；
- 为 Pack EoL deep case 建立 claim-level evidence chain；
- 为 Framework v1.0 提供可操作化字段；
- 为后续 adjacent-case gate 和 cross-case comparison 提供同一检索与证据纪律。

## 2. Review boundary

### 2.1 Included production scope

- lithium-ion battery **cell manufacturing**；
- lithium-ion battery **module manufacturing**；
- lithium-ion battery **pack manufacturing**；
- Pack end-of-line testing when the studied task belongs to manufacturing completion, testing, handling, integration, or release；
- non-battery tasks only when used as explicitly bounded cross-industry analogues for a physical or system capability.

Production-level label must be one of:

| Label | Meaning |
| --- | --- |
| `CELL` | 电芯制造或电芯级生产任务 |
| `MODULE` | 模组装配或模组级测试/处理 |
| `PACK` | 电池包装配、EoL测试或Pack级处理 |
| `CROSS_LEVEL` | 来源明确跨越多个生产层级，且无法合理拆分 |
| `NON_BATTERY_ANALOG` | 跨行业或非电池任务，只用于受限迁移 |
| `UNRESOLVED` | 当前资料不足以判断，必须后续核实 |

Production level must be recorded separately from lifecycle stage:

| Lifecycle label | Meaning |
| --- | --- |
| `MANUFACTURING` | 新电池cell/module/pack制造、装配与制造端end-of-line testing |
| `USE_OR_SERVICE` | 服役、维修、充换电或现场服务 |
| `END_OF_FIRST_LIFE` | 退役电池诊断、分级、second-life前处理 |
| `RECYCLING_OR_DISASSEMBLY` | 回收、拆解或材料循环阶段 |
| `GENERAL_METHOD` | 不绑定具体电池生命周期的机器人方法 |
| `UNRESOLVED` | 来源不足以可靠判断 |

`EoL` is ambiguous. It may mean manufacturing **end-of-line** or battery **end-of-life**. Never classify an `EoL` record without reading the surrounding text and assigning a lifecycle label. End-of-life battery testing may support task mechanics or safety by bounded transfer, but it is not direct evidence for a manufacturing end-of-line station.

### 2.2 Included robotic-system scope

- dedicated/fixed-purpose automation as reference architecture；
- fixed industrial robot and fixed dual-arm robot；
- collaborative robot；
- mobile robot when manipulation or task allocation is relevant；
- mobile manipulator；
- humanoid or mobile dual-arm system；
- manual operation only as a reference solution or current-state baseline.

Pure process equipment is included only when it supplies a comparator, interface, or manufacturing requirement that changes a robotic-system decision.

### 2.3 Out of core scope

- battery recycling/disassembly, except a clearly documented task-method analogue；
- vehicle maintenance, charging, field repair, or battery swapping outside manufacturing；
- electrochemical testing algorithms with no robotic manipulation, architecture, or integration relevance；
- detailed motion-planning, grasp-learning, VLA, control or robot-body development not needed to answer the RQs；
- general factory logistics without a battery-manufacturing requirement that changes the robot task；
- unsupported ROI, takt, yield, success-rate or maturity ranking.

## 3. Evidence questions

Formal searches and extraction should answer the following rather than merely collect papers:

### EQ1 — Manufacturing task and boundary

- What object is manipulated?
- What are the source state, destination state, completion criterion and failure consequences?
- Which subsystem owns each action and decision?

### EQ2 — Task/process characteristics

- Which geometric, material, contact, electrical, safety, quality, traceability, variation, takt and layout conditions change the robot task?
- Which are direct Pack EoL facts, adjacent battery requirements, cross-industry mechanisms, or unverified assumptions?

### EQ3 — Architecture capability and comparator

- How does each evaluated configuration satisfy the requirement: mechanical constraint, sensing, compliance/force control, tooling, dual-arm coordination, mobility, safety interface, software integration, or human intervention?
- What is the like-for-like reference solution?

### EQ4 — Conditional suitability

- Under which product mix, volume/takt, changeover, station count, brownfield, safety, reliability, scalability and integration conditions is an architecture supported, conditional, unsupported by current evidence, or unknown?

### EQ5 — Implementation and evidence limits

- What implementation barriers, staged introduction strategies and remaining research needs follow?
- Which claims require expert, equipment, experimental, economic or field evidence beyond public literature?

## 4. Evidence streams and databases

The search uses separate streams because peer-reviewed research, standards, patents and company disclosures support different claim types.

### Stream A — Peer-reviewed academic evidence

Primary databases:

1. **Scopus** — interdisciplinary engineering and manufacturing coverage; primary title/abstract screening source when institutional access is available;
2. **Web of Science Core Collection** — independent interdisciplinary coverage and citation chaining;
3. **IEEE Xplore** — robotics, automation, sensing, force control, safety and integration;
4. **OpenAlex** — open cross-disciplinary discovery, citation links and coverage checking;
5. **Crossref** — DOI and bibliographic metadata verification, not relevance judgement.

Targeted supplementary platforms:

- ScienceDirect, SpringerLink and Wiley for known journals or publisher-hosted full text;
- arXiv for recent robotics/computer-vision preprints, kept distinct from peer-reviewed versions;
- DBLP for computer-science metadata checks;
- Google Scholar only for supplementary discovery and forward citation chasing because ranking and result counts are not stable enough to be the sole reproducible search source.

Minimum coverage before calling the academic search reasonably complete for this thesis stage:

- at least two complementary interdisciplinary/index databases among Scopus, Web of Science and OpenAlex;
- IEEE Xplore for robotics/automation coverage;
- backward and forward citation chasing for the closest direct papers;
- exact query strings, dates, filters and hit counts recorded.

If Scopus or Web of Science access is unavailable, record that limitation and do not claim systematic-review completeness.

### Stream B — Standards and manufacturing guidance

Targeted sources include official ISO, IEC, DIN/VDE, VDA, VDMA, EU or authoritative institutional/industry-association documents where relevant. Standards support safety, interfaces, terminology or manufacturing requirements; they do not by themselves demonstrate a particular robot deployment.

### Stream C — Patents and equipment baselines

Use Espacenet, Google Patents, official equipment-provider documentation and technical manuals to establish disclosed architectures or interfaces. A patent establishes a disclosed design, not actual deployment, performance or commercial maturity.

### Stream D — Direct company and industrial case disclosures

Use the original company, integrator or equipment-provider publication where possible. Secondary news may be retained only as a discovery pointer. Company claims are tagged as disclosure and cannot independently establish reliability, speed, economic benefit, scale or superiority.

## 5. Search period and languages

### 5.1 Time range

- Primary database range: **2000-01-01 to the date of each search run**;
- prioritize 2015 onward during screening for current industrial architectures;
- allow pre-2000 foundational connector insertion, compliant assembly or safety work only through backward citation chasing and only when it remains conceptually necessary;
- company/industrial deployment evidence should normally be the latest available version, with publication and event dates distinguished.

This range is a review-design choice, not a claim that relevant robotics began in 2000.

### 5.2 Languages

- English, German and Chinese sources may be included;
- the language is recorded for every item;
- non-English claims used in the thesis require a verifiable original passage and an accurate working translation;
- Chinese company disclosures and patents may support industrial anchoring but do not replace peer-reviewed scientific evidence;
- sources in other languages may enter only if essential metadata and the relevant claim can be reliably verified.

## 6. Query blocks

Each database query must be saved verbatim in a query-run log. Syntax may be adapted to database fields, but the conceptual blocks and changes must be recorded.

### QB1 — Broad battery-manufacturing robotics map

```text
("lithium-ion batter*" OR "battery cell*" OR "battery module*" OR "battery pack*")
AND
(manufactur* OR production OR assembl* OR testing)
AND
(robot* OR cobot* OR "industrial robot*" OR "mobile manipulator*"
 OR humanoid* OR "dual-arm" OR automation)
```

Purpose: identify direct battery-manufacturing robotic applications and reviews.

### QB2 — Manufacturing end-of-line and robotic battery-testing closest work

Run QB2a and QB2b separately to prevent `EoL` ambiguity.

#### QB2a — Manufacturing end-of-line

```text
("battery pack*" OR "EV batter*" OR "electric vehicle batter*")
AND
("end-of-line" OR "end of line" OR "production test*" OR "manufacturing test*")
AND
(robot* OR automat* OR manipulat*)
```

Purpose: find direct manufacturing-end-of-line work.

#### QB2b — Robotic battery testing, lifecycle open during discovery

```text
("battery pack*" OR "battery module*" OR "EV batter*" OR "lithium-ion batter*")
AND
(test* OR diagnos* OR "state of health" OR validation)
AND
(robot* OR automat* OR manipulat*)
```

Purpose: find the closest physical testing tasks even when the lifecycle stage is not encoded in the title. Each result must then be labelled `MANUFACTURING`, `END_OF_FIRST_LIFE`, `RECYCLING_OR_DISASSEMBLY`, or another lifecycle value. Do not require `connector` in every run because relevant testing papers may describe physical contact differently.

### QB3 — Connector and harness handling within battery testing

```text
("battery pack*" OR "EV batter*" OR "lithium-ion batter*")
AND
(connector* OR plug* OR socket* OR cable* OR harness* OR terminal*)
AND
(insert* OR connect* OR disconnect* OR handling OR manipulation)
AND
(robot* OR automat*)
```

Purpose: identify direct or adjacent connector/harness handling evidence.

### QB4 — Cross-industry task mechanics

Run as separate subqueries rather than one oversized string:

```text
(robot* OR automat*) AND (connector insertion OR plug insertion OR mating) AND (force OR compliance OR contact)
```

```text
(robot* OR automat*) AND ("wire harness" OR cable OR "deformable linear object*") AND (handling OR manipulation OR assembly)
```

```text
(robot* OR automat*) AND (connection verification OR insertion verification OR connector detection)
```

Purpose: support physical mechanisms and capability definitions. Results are `NON_BATTERY_ANALOG` unless a battery application is explicit; performance numbers do not transfer automatically.

### QB5 — Architecture assessment and implementation

```text
(robot* OR "robotic system*" OR automation)
AND
("task-based assessment" OR "technology assessment" OR suitability
 OR "architecture selection" OR "capability mapping" OR "task allocation")
AND
(manufactur* OR assembl*)
```

Purpose: identify methods and decision criteria; it does not substitute for battery-specific evidence.

### QB6 — Candidate A, inactive until its gate begins

```text
("battery cell*" OR "lithium-ion cell*")
AND
(identification OR detection OR grasp* OR pick* OR handling OR loading OR placement)
AND
(robot* OR automat* OR vision)
AND
(module OR pack OR assembl* OR manufactur*)
```

Do not run a full Candidate A search before the Pack EoL minimum target is met. QB6 is frozen here only to prevent later query drift.

## 7. Inclusion criteria

An item may enter the evidence corpus when it meets all applicable conditions:

| ID | Criterion |
| --- | --- |
| `I1` | It addresses an in-scope battery-manufacturing task, or a clearly bounded cross-industry analogue. |
| `I2` | It identifies a robotic/automation actor, capability, comparator, interface or implementation decision relevant to RQ1–RQ3. |
| `I3` | It contributes evidence about task characteristics, process/production requirements, architecture capability, conditional suitability, implementation barrier or assessment method. |
| `I4` | Source identity, date and bibliographic or organizational provenance can be verified. |
| `I5` | For claim extraction, the relevant full-text passage, page/section, figure/table or exact official disclosure is accessible. Abstract-only records may remain in the screening/closest-work map but cannot support detailed technical claims. |
| `I6` | Cross-industry evidence explicitly records equivalence, non-equivalence, allowed inference and forbidden inference. |

## 8. Exclusion criteria and reason codes

Every excluded record receives one primary reason:

| Code | Exclusion reason |
| --- | --- |
| `E1_WRONG_DOMAIN` | Not lithium-ion battery manufacturing and not a useful bounded analogue. |
| `E2_WRONG_STAGE` | Recycling, vehicle service/charging or another out-of-scope lifecycle stage without an approved transfer role. |
| `E3_NO_ROBOTICS_DECISION` | Describes process equipment or electrochemical testing without a relevant robotic/automation task, comparator or interface. |
| `E4_WRONG_TASK` | Robotics content exists but does not inform the selected task, framework or implementation questions. |
| `E5_NO_VERIFIABLE_SOURCE` | Provenance, metadata or original publication cannot be verified. |
| `E6_NO_EXTRACTABLE_EVIDENCE` | Only title/abstract/secondary summary is available for a detailed claim; may remain as a discovery pointer. |
| `E7_DUPLICATE` | Duplicate of a retained record. |
| `E8_MARKETING_ONLY` | Pure promotional material with no identifiable task detail; detailed company disclosures may instead be retained with strict limits. |
| `E9_LANGUAGE_UNVERIFIABLE` | Relevant passage cannot be reliably read or translated. |
| `E10_SUPERSEDED` | Superseded version; the latest or peer-reviewed version is retained. |

Do not exclude a source merely because it contradicts the expected conclusion. Counterexamples and negative findings are retained and tagged.

## 9. Source classification: two independent axes

Do not collapse source quality and case proximity into one label.

### 9.1 Source type

- `PEER_REVIEWED_ARTICLE`
- `PEER_REVIEWED_REVIEW`
- `CONFERENCE_PAPER`
- `PREPRINT`
- `STANDARD_OR_GUIDELINE`
- `PATENT`
- `INDUSTRY_ASSOCIATION_REPORT`
- `INDUSTRIAL_EQUIPMENT_DOCUMENTATION`
- `DIRECT_COMPANY_DISCLOSURE`
- `ACADEMIC_THESIS_OR_REPORT`
- `SECONDARY_MEDIA`
- `ENGINEERING_INFERENCE`

### 9.2 Relation to the deep case

- `DIRECT_PACK_EOL`
- `DIRECT_BATTERY_TESTING_OTHER_LEVEL_OR_SETUP`
- `ADJACENT_BATTERY_MANUFACTURING`
- `CROSS_LIFECYCLE_BATTERY_ANALOG`
- `CROSS_INDUSTRY_TASK_ANALOG`
- `METHOD_ONLY`
- `CONTEXT_ONLY`

A peer-reviewed paper can still be only a cross-industry analogue; a company disclosure can be directly about the target task but weak for performance claims.

## 10. Search, deduplication and screening workflow

### 10.1 Query-run record

For each run record:

- `query_run_id`;
- database/platform;
- exact query as executed;
- searched fields;
- date and time;
- coverage years and filters;
- hit count;
- export format and file;
- adaptations or errors.

Never overwrite an old query run. Revised strings receive a new ID and a change reason.

### 10.2 Deduplication order

1. exact DOI;
2. exact arXiv ID, patent family ID or standard number;
3. normalized title + year + first author/organization;
4. manual comparison for conference/preprint/journal extensions.

Keep the peer-reviewed version as the primary record when it supersedes a preprint, while preserving links between versions. Record `E7_DUPLICATE` or `E10_SUPERSEDED`; do not silently delete records.

### 10.3 Screening stages

1. **Discovery/metadata check** — verify identity and deduplicate;
2. **Title/abstract screening** — `include / exclude / maybe`, with reason code for exclusions;
3. **Full-text eligibility** — verify the relevant evidence is extractable;
4. **Claim extraction** — connect exact evidence to one or more claims;
5. **Citation chasing** — backward and forward search from closest direct papers;
6. **Saturation check** — record whether new searches still add new task characteristics, architectures, requirements or counterexamples.

One student/researcher performs screening in this thesis. To reduce inconsistency, all `maybe` records and all exclusions from the closest-work set receive a second self-check on a later pass; this is not presented as independent dual-reviewer screening.

## 11. Metadata and traceability rules

Bibliographic records should include at least:

- title, authors/organization, year, publication date, publication type and venue;
- DOI, arXiv ID, patent/standard identifier where applicable;
- abstract/summary, language and source platform;
- OA/full-text status and local file path where legally available;
- production level, lifecycle stage, task family and architecture category;
- screening decision and exclusion reason;
- search run and retrieval date.

### Exact-location rule

Every thesis-relevant claim should record:

- printed page number when present;
- PDF page index when different;
- section/subsection;
- figure/table/patent paragraph/claim number when applicable;
- a short evidence extract or close paraphrase for internal checking;
- what the passage supports and what it does not support.

If an HTML page has no stable page number, record heading, paragraph context, publication/update date, URL and access date. A search-result snippet is never an acceptable final evidence location.

## 12. Claim audit decision rules

Each Week 06 claim receives one current outcome:

| Status | Chinese meaning | Rule |
| --- | --- | --- |
| `RETAIN_DIRECT` | 保留 | Direct, extractable evidence supports the specific claim in the relevant battery task/configuration. |
| `RETAIN_CONDITIONAL` | 条件保留 | Adjacent or cross-industry evidence supports the mechanism or capability, with explicit transfer limits and conditional wording. |
| `DOWNGRADE_ASSUMPTION` | 降级 | Useful only as a scenario input, design assumption or research question; not an observed fact. |
| `REMOVE_UNSUPPORTED` | 删除 | No reliable source or defensible inference supports the claim, or the statement overgeneralizes a technology class. |
| `PENDING_FULLTEXT` | 等待全文 | Metadata/abstract suggests relevance but the exact claim cannot yet be verified. |

Decision principles:

- missing evidence does not prove impossibility;
- one deployment does not prove general suitability;
- cross-industry performance values do not transfer to Pack EoL without equivalence evidence;
- company disclosure proves that the company made the disclosure, not that the performance claim is independently validated;
- exact numbers require the original source, unit, condition and applicable configuration;
- architecture claims must describe the evaluated configuration, not stereotype the whole technology class;
- safety-critical claims cannot be upgraded by plausibility alone.

## 13. Evidence extraction schema

The claim matrix contains at least:

```text
Claim ID
→ RQ and case
→ claim text and scope
→ production level
→ lifecycle stage
→ source ID and source type
→ relation to case
→ exact location
→ evidence extract/paraphrase
→ inference chain
→ supported conclusion
→ non-supported extension / transfer limit
→ current decision
→ unresolved evidence need
```

Where a claim relies on several sources, enter one row per claim–source link. Do not compress several sources into one untraceable citation bundle.

## 14. Quality and applicability checks

### Academic source

- Is the task/configuration actually comparable?
- Are method, sample/system and evaluation conditions reported?
- Does the result show feasibility, comparative performance, or only a conceptual proposal?
- Is the cited statement a measured result, author interpretation or background claim?

### Company/equipment source

- Is it the original company/equipment-provider source?
- Is the task visible or explicitly described?
- Are performance conditions and denominators disclosed?
- Could the statement be promotional or selectively reported?
- Which claim can be retained only as `company-reported`?

### Patent

- Is the cited material in the description, drawing or claim?
- Does it describe a possible embodiment or a required feature?
- Is deployment or performance independently shown? Normally no.

### Cross-industry transfer

- What is physically/systemically equivalent?
- What differs in connector geometry, cable state, safety, electrical condition, takt, quality criterion and maturity?
- What is the maximum allowed inference?

## 15. Search stopping and update rules

The initial Pack EoL search may stop when all are true:

1. minimum database coverage in Section 4 is met or access limitations are explicitly recorded;
2. all query strings, dates, filters and hit counts are logged;
3. closest direct papers have backward/forward citation chasing;
4. two successive targeted query/citation-chasing iterations add no new major requirement group, architecture class or direct counterexample;
5. every high-impact Week 06 claim has a decision or a specific unresolved evidence need;
6. excluded closest-looking records have explicit reason codes.

Stopping means the thesis evidence base is adequate for the current case stage, not that all literature worldwide has been found.

Re-run date-sensitive searches before final submission and record the new run rather than overwriting v1 results.

## 16. Reproducibility outputs

Maintain together:

- this protocol and its version history;
- query-run log;
- raw exports where licensing permits;
- deduplicated screening log;
- bibliography/BibTeX database;
- lawful full-text/OA manifest and local paths;
- claim–evidence matrix;
- exclusion decisions;
- closest-work and counterexample list;
- protocol deviations and reasons.

## 17. Known limitations of v1.0

- Institutional access to Scopus/Web of Science and some full texts has not yet been verified;
- a single researcher conducts screening, so decisions require transparent reason codes and later self-checks;
- terminology for industrial Pack EoL connector handling is not standardized, so citation chasing and query variants are essential;
- public industrial data may omit takt, failures, cost and safety implementation details;
- this protocol does not by itself validate Framework v1.0 or prove novelty.

## 18. Version control

- `v1.0 — 2026-09-20`: initial frozen protocol following registration-baseline synchronization;
- later changes must state: changed field/rule, trigger evidence, effect on already screened records, and whether re-screening is required.
