# Example: Team Process Improvement Under Conflicting Constraints

## Scenario

A 10-person engineering team wants to adopt code review. The team lead says: "We need to roll out code review across the team." But there are real obstacles: three senior engineers think reviews slow them down, two juniors feel intimidated, sprint velocity is already tight, and the team can't agree on which tool to use.

## Step 1: Trigger ZHIXI

```
知悉 — 我们是一个 10 人的开发团队，想推广代码审查流程，但大家意见不统一、时间也紧，帮我理一理怎么推进。
```

## Step 2: 知己 (Self-Knowledge)

```
表层请求：在 10 人团队推广代码审查流程
已确认事实：
  - 团队有 10 名成员，技术水平有差异
  - 当前没有正式的代码审查流程
  - 存在成员抵触和时间压力
目标假设：
  - 表层目标是"推广代码审查"，但真实目标可能是提升代码质量和促进知识传承
  - 团队可能还面临关键人风险（只有少数人理解核心模块）
关键模糊点：
  - 抵触的具体原因：是觉得浪费时间，还是担心被挑错？
  - 时间紧张的量化：每周能额外投入多少时间在审查上？
  - 工具争议：分歧在哪几个工具之间，争议点是什么？
```

ZHIXI asks direction-changing questions:

1. 团队推广代码审查，你最想解决的问题是线上缺陷多、还是关键人知识集中？
2. 每周每个人额外花在审查上的时间上限是多少？
3. 工具争议具体是哪几个候选，大家卡在哪里？

## Step 3: 问己 (Self-Questioning)

```
目标：通过轻量级代码审查提升代码质量并促进团队知识传承
非目标：
  - 不追求 100% 代码审查覆盖率
  - 不引入重量级的合规审计流程
约束：
  - 每人每周额外时间 < 2 小时
  - 不能拖慢现有两周一个迭代的交付节奏
  - 需要兼容现有 GitLab 工作流
成功标准：
  - 核心模块代码审查覆盖率 > 70%（三个月内）
  - 审查反馈时效 < 24 小时
  - 至少 3 名成员能独立审查非自己编写的模块
当前决策：
  - 先在核心模块试点，再逐步推广
  - 工具选型优先集成成本而非功能丰富度
```

## Step 4: 明需 (Requirement Clarity)

```
能力单元 1: 审查流程设计
  - 输入：团队规模、迭代节奏、模块分布
  - 输出：分级审查策略（必审/抽审/自审）
  - 验收标准：流程文档经全组评审通过，试用两周后反馈调整
  - 降级路径：退回"所有 PR 至少一人审查"

能力单元 2: 工具选型与配置
  - 工具对比：
    | 维度 | GitLab MR Review | Gerrit | PullApprove |
    |---|---|---|---|
    | 集成成本 | 低（已有） | 高（需部署） | 中（需对接） |
    | 学习曲线 | 低 | 高 | 中 |
    | 适合场景 | 10 人以下团队 | 大型开源项目 | 中型团队精细管控 |
  - 决策：选 GitLab MR Review（集成成本最低，团队已熟悉）
  - 降级路径：评估 PullApprove

能力单元 3: 培训材料与文化建设
  - 输出：审查指南 + 审查者清单 + 首次培训会议
  - 验收标准：培训后每人能独立完成一次审查，反馈正向率 > 60%
  - 降级路径：改为"结对审查"（senior 带 junior）
```

## Step 5: 洞意 (Insight & Execution)

ZHIXI executes and produces knowledge fragments:

### Fragment 1: 分级代码审查流程

```markdown
---
type: knowledge-fragment
kind: procedure
status: verified
privacy: sanitized
source: "ZHIXI session execution result + team pilot feedback"
confidence: 0.8
tags:
  - process/code-review
  - team/10-person
---

# 分级代码审查流程：10 人团队实践

## 摘要 (Summary)
10 人团队推广代码审查时，采用三级分类策略（必审/抽审/自审）
比一刀切的全面审查更可持续。核心模块必审、常规功能抽审、
紧急修复自审加事后补审，每周人均额外投入控制在 1.5 小时以内。

## 事实陈述 (Facts)
- 试点 4 周，核心模块审查覆盖率达 75%
- 人均每周审查时间 1.2 小时，低于 2 小时上限
- 审查反馈平均时效 8 小时，优于 24 小时目标
- 第 3 周起 junior 成员开始独立审查非核心模块

## 推断 (Inferences)
- 分级策略降低了抵触——不是每次提交都被"检查"
- 知识传承 4 周内初步显现：junior 对核心模块理解度自评从 3/10 到 6/10

## 建议 (Suggestions)
- 第 1-2 周：只审查核心模块，适应节奏
- 第 3-4 周：扩大到所有新增功能 MR
- 第 5 周起：引入轮值审查者制度
- 每月回顾分级标准，按模块成熟度调整

## 适用边界 (Applicability Boundaries)
- 适用于 5-15 人、使用 GitLab 的开发团队
- 未覆盖跨时区异步团队和合规严格（金融/医疗）场景

## 来源 (Sources)
- 团队试点 4 周执行数据
- 审查者反馈问卷（10/10 回复）
```

### Fragment 2: 审查抵触应对策略

```markdown
---
type: knowledge-fragment
kind: decision_rule
status: candidate
privacy: sanitized
source: "ZHIXI session execution result"
confidence: 0.65
tags:
  - process/code-review
  - team/culture
---

# 代码审查抵触应对决策规则

## 摘要 (Summary)
团队成员对代码审查的抵触通常源于三类原因，需对症下药：
时间压力型用分级策略缓解、心理压力型用结对审查过渡、
工具摩擦型用流程简化消除。

## 事实陈述 (Facts)
- 试点前：3 名 senior 担心效率下降，2 名 junior 害怕被评判
- 试点后：senior 效率感知从"拖慢 30%"修正为"额外 10%，但返工减少"
- junior 参与度在引入模板清单后显著提升

## 推断 (Inferences)
- "被评判"的恐惧可通过标准化审查清单缓解——审查的是代码而非人
- senior 的效率担忧在实际数据面前自然消解，关键是先体验而非说服

## 建议 (Suggestions)
- 时间压力型：展示审查减少返工的数据，用事实替代说教
- 心理压力型：先安排结对审查，建立安全感后再独立审查
- 工具摩擦型：提供 5 分钟快速上手指引

## 适用边界 (Applicability Boundaries)
- 基于单次 10 人团队试点观察
- 未覆盖管理者强制推行导致的系统性抵触

## 来源 (Sources)
- 当前 Skill 执行结果 + 团队试点反馈
```

## Result

In one conversation, the team lead went from "we need code review" to:
- A clear understanding that the real goal was code quality + knowledge transfer
- A requirements baseline with explicit constraints (2 hours/week, no 100% coverage)
- Three decomposed capability units with tool tradeoff analysis
- A graded review procedure the team actually adopted
- Reusable knowledge fragments for future process rollouts
