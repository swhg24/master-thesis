# 正式三库 Boolean 检索 Run Sheet（Scopus / Web of Science / IEEE Xplore）

状态（2026-09-28）：**部分执行、尚未完成逐条可复现登记**。学生已提供 Scopus 一组 68 条和 IEEE Xplore 三组 9/25/3 条导出；Web of Science 正式结果未收到。各组与下文基准检索式的精确对应、过滤器及去重筛选仍需核对，不能把已执行的部分检索或截图命中数记作整个三库检索完成。过程记录见 `14_public_source_checkpoint_2026-09-28.md`；本文件保留原拟定检索基准。

## 0. 执行前统一设置（三库一致）

- 时间范围：`2000-01-01` 至 `2026-09-28`
- 语言：不限（初筛后再标语言）
- 文档类型：不限（先全量，不在检索层过滤）
- 检索字段：Scopus=`TITLE-ABS-KEY`；Web of Science=`TS=`；IEEE Xplore=`Abstract`
- 布尔符一律大写 `AND` / `OR`；星号 `*` 为词尾通配；短语用半角双引号。

## 1. 出手顺序（登录一个库 → 跑完该库全部 QB → 再切库）

1. Scopus：QB3 → QB2a → QB2b → QB1
2. Web of Science：QB3 → QB2a → QB2b → QB1
3. IEEE Xplore：QB2b → QB3 → QB4

原则：先跑命中小、最贴近深案例的 QB3/QB2a，再跑宽的 QB1；QB1 仅记 hit 数作覆盖面检查，不做逐条筛选。

## 2. 检索式

### Scopus（TITLE-ABS-KEY）

**SCOPUS-QB3-01**
```
TITLE-ABS-KEY ( ( "battery pack*" OR "EV batter*" OR "lithium-ion batter*" ) AND ( connector* OR plug* OR socket* OR cable* OR harness* OR terminal* ) AND ( insert* OR connect* OR disconnect* OR handling OR manipulation ) AND ( robot* OR automat* ) )
```

**SCOPUS-QB2A-01**
```
TITLE-ABS-KEY ( ( "battery pack*" OR "EV batter*" OR "electric vehicle batter*" ) AND ( "end-of-line" OR "end of line" OR "production test*" OR "manufacturing test*" ) AND ( robot* OR automat* OR manipulat* ) )
```

**SCOPUS-QB2B-01**
```
TITLE-ABS-KEY ( ( "battery pack*" OR "battery module*" OR "EV batter*" OR "lithium-ion batter*" ) AND ( test* OR diagnos* OR "state of health" OR validation ) AND ( robot* OR automat* OR manipulat* ) )
```

**SCOPUS-QB1-01**
```
TITLE-ABS-KEY ( ( "lithium-ion batter*" OR "battery cell*" OR "battery module*" OR "battery pack*" ) AND ( manufactur* OR production OR assembl* OR testing ) AND ( robot* OR cobot* OR "industrial robot*" OR "mobile manipulator*" OR humanoid* OR "dual-arm" OR automation ) )
```

### Web of Science（TS=）

**WOS-QB3-01**
```
TS=(("battery pack*" OR "EV batter*" OR "lithium-ion batter*") AND (connector* OR plug* OR socket* OR cable* OR harness* OR terminal*) AND (insert* OR connect* OR disconnect* OR handling OR manipulation) AND (robot* OR automat*))
```

**WOS-QB2A-01**
```
TS=(("battery pack*" OR "EV batter*" OR "electric vehicle batter*") AND ("end-of-line" OR "end of line" OR "production test*" OR "manufacturing test*") AND (robot* OR automat* OR manipulat*))
```

**WOS-QB2B-01**
```
TS=(("battery pack*" OR "battery module*" OR "EV batter*" OR "lithium-ion batter*") AND (test* OR diagnos* OR "state of health" OR validation) AND (robot* OR automat* OR manipulat*))
```

**WOS-QB1-01**
```
TS=(("lithium-ion batter*" OR "battery cell*" OR "battery module*" OR "battery pack*") AND (manufactur* OR production OR assembl* OR testing) AND (robot* OR cobot* OR "industrial robot*" OR "mobile manipulator*" OR humanoid* OR "dual-arm" OR automation))
```

### IEEE Xplore（Abstract 字段）

> 注意：IEEE Xplore command search 的字段名随界面版本浮动（`Abstract` / `All Metadata`）。若 `"Abstract"` 被拒，改用 `"All Metadata"`，逻辑块不变，并把改动回报。

**IEEE-QB2B-01**
```
("Abstract":"battery pack*" OR "Abstract":"battery module*" OR "Abstract":"EV batter*" OR "Abstract":"lithium-ion batter*") AND ("Abstract":"test*" OR "Abstract":"diagnos*" OR "Abstract":"state of health" OR "Abstract":"validation") AND ("Abstract":"robot*" OR "Abstract":"automat*" OR "Abstract":"manipulat*")
```

**IEEE-QB3-01**
```
("Abstract":"battery pack*" OR "Abstract":"EV batter*" OR "Abstract":"lithium-ion batter*") AND ("Abstract":"connector*" OR "Abstract":"plug*" OR "Abstract":"harness*" OR "Abstract":"terminal*") AND ("Abstract":"insert*" OR "Abstract":"connect*" OR "Abstract":"manipulat*" OR "Abstract":"handling") AND ("Abstract":"robot*" OR "Abstract":"automat*")
```

**IEEE-QB4-01**
```
("Abstract":"connector insertion" OR "Abstract":"connector mating" OR "Abstract":"plug insertion") AND ("Abstract":"robot*" OR "Abstract":"automat*") AND ("Abstract":"force" OR "Abstract":"compliance" OR "Abstract":"recovery")
```

## 3. 回报模板

每跑完一条，按下面格式回报（可一次报完，也可分批）：

```text
query_id | 库 | hit 数 | 备注
```

备注里写清：语法是否报错/字段名是否调整、是否识别出已知源（如 S011/S018）、是否有明显新线索。

命中规则：
- hit 数 ≤ 50：可导出结果（或截标题页）给我做逐条初筛；
- hit 数 > 200：先只报数字，我判断收窄方向后再动手；
- hit 数 = 0：照样回报，零命中本身就是结果（对 QB2a 尤其关键）。

## 4. 已知源对照（命中时帮我勾一下）

出现这些已知 DOI/源请标注：S011（Spirit AI 披露，非库内）、S018（adjacent battery robotics）、S021–S034（跨行业连接器/线束机制线）。