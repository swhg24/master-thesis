# 今日组会 PPT 逻辑说明

## 整体规划

这版 PPT 的核心目标不是把所有材料都讲完，而是让导师快速看到三件事：

1. 你这一周不是空泛阅读，而是已经把题目边界、工艺流程、机器人应用方向初步搭起来了。
2. 你已经形成了一个合理判断：机器人应用不能脱离电池制造工艺要求，尤其是干燥环境、污染控制、精密定位、安全和追溯。
3. 你需要导师帮你拍板几个关键问题，然后下周就能进入 use case 筛选和评价框架。

整体叙事顺序是：

`我做了什么 -> 我现在怎么理解课题 -> 为什么电池基础会影响机器人 -> 制造流程怎么分 -> 哪些 use case 值得做 -> 需要导师确认什么 -> 下周怎么推进`

这样安排的好处是：先展示工作量，再展示理解深度，最后把导师引导到你真正需要反馈的问题上。

## Slide 1 - Today

这一页是开场页，不是内容页。它告诉导师今天汇报的结构：我做了什么、我发现了什么、我需要什么反馈。

页面中的核心句子是：

> I am turning a broad robotics topic into a process-aware evaluation framework.

这句话的意思是：你不是泛泛谈机器人，而是把机器人应用放回电池制造流程里评价。

## Slide 2 - Work done

这一页回答“我做了什么”。我没有只列任务，而是用三列说明：

- Output：产出了什么
- What I did：具体做了什么
- Why it matters：为什么这个产出对论文有用

这样导师会觉得你不是在堆材料，而是在建立论文结构。

## Slide 3 - Thesis understanding

这一页回答“我现在怎么理解题目”。重点是划清边界：

- 包括：电芯制造、机器人系统、技术和经济评价
- 暂不包括：机器人控制算法、详细电化学设计、电池包和回收

这页很重要，因为硕士论文最怕范围太大。你主动把边界讲清楚，导师会更容易给你反馈。

## Slide 4 - Battery basics

这一页解释为什么导师让你先看电池基础是有意义的。

逻辑是：

`电池材料/结构特点 -> 制造要求 -> 对机器人系统的影响`

例如：

- 电解液怕水 -> 需要干燥环境 -> 机器人要适应干房
- 隔膜和极片很薄 -> 需要轻柔和精密搬运 -> 需要视觉和专用夹爪
- 化成影响寿命 -> 需要托盘搬运和数据追溯

这页的作用是展示你已经开始把电池知识转化成机器人论文的问题。

## Slide 5 - Process map

这一页是论文主线的工艺地图。你把电芯制造分成三段：

1. Electrode manufacturing
2. Cell assembly
3. Cell finishing

每一段对应不同的机器人潜力和难度。

这一页的结论是：cell finishing 和 intralogistics（内部物流） 是比较现实的起点；cell assembly 技术潜力高，但难度也高。

## Slide 6 - Candidate use cases

这一页回答“哪些应用值得继续研究”。我把 use case 从四个压成三个主方向：

1. AMR / AGV intralogistics
2. Formation / testing tray handling
3. Vision-guided inspection + loading

最后补一句：stacking / housing insertion 可以作为技术难度案例，但不一定适合作为主案例。

这样讲比较稳，因为它既体现技术深度，又不会把论文带到太难落地的方向。

## Slide 7 - Questions

这一页是给导师“拍板”的页面。问题分成三类：

- Scope：研究范围怎么定
- Method：评价方法怎么做
- Use cases：最终选哪些案例

这样比零散提问更清楚，也能让导师更容易逐项回答。

## Slide 8 - Next week

这一页是收尾页，告诉导师你下一周会怎么推进。

下周计划是三步：

1. 补文献
2. 缩小 use case
3. 建评价表

最后的 expected output 是：use-case shortlist 和 first evaluation table。这个输出很具体，导师会知道你下周会交付什么。
