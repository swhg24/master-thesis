# Evidence Protocol v1.0：快速代码表

本文件只用于执行时快速查看；定义以 `01_evidence_protocol_v1.md` 为准。

## Screening decisions

- `include`
- `exclude`
- `maybe`

## Exclusion reasons

- `E1_WRONG_DOMAIN`
- `E2_WRONG_STAGE`
- `E3_NO_ROBOTICS_DECISION`
- `E4_WRONG_TASK`
- `E5_NO_VERIFIABLE_SOURCE`
- `E6_NO_EXTRACTABLE_EVIDENCE`
- `E7_DUPLICATE`
- `E8_MARKETING_ONLY`
- `E9_LANGUAGE_UNVERIFIABLE`
- `E10_SUPERSEDED`

## Production levels

- `CELL`
- `MODULE`
- `PACK`
- `CROSS_LEVEL`
- `NON_BATTERY_ANALOG`
- `UNRESOLVED`

## Source types

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

## Lifecycle stages

- `MANUFACTURING`
- `USE_OR_SERVICE`
- `END_OF_FIRST_LIFE`
- `RECYCLING_OR_DISASSEMBLY`
- `GENERAL_METHOD`
- `UNRESOLVED`

`EoL`必须结合上下文消歧：manufacturing end-of-line 与 battery end-of-life 不能视为同一阶段。

## Relation to Pack EoL deep case

- `DIRECT_PACK_EOL`
- `DIRECT_BATTERY_TESTING_OTHER_LEVEL_OR_SETUP`
- `ADJACENT_BATTERY_MANUFACTURING`
- `CROSS_LIFECYCLE_BATTERY_ANALOG`
- `CROSS_INDUSTRY_TASK_ANALOG`
- `METHOD_ONLY`
- `CONTEXT_ONLY`

## Claim audit status

- `RETAIN_DIRECT` — 直接证据足以保留当前具体主张；
- `RETAIN_CONDITIONAL` — 机制或能力有相邻/跨行业证据，必须附迁移边界；
- `DOWNGRADE_ASSUMPTION` — 只能保留为scenario或待检验假设；
- `REMOVE_UNSUPPORTED` — 没有可靠支持或属于技术类别过度概括；
- `PENDING_FULLTEXT` — 需要全文才能决定。

## Full-text status

- `open_pdf`
- `needs_institution`
- `no_open_pdf`
- `anti_bot_blocked`
- `html_not_pdf`
- `unknown`
