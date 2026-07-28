# Example: From Vague Idea to Action Plan

## Scenario

You have a rough idea: "I want to build a tool that helps me track supplier quality for my procurement work."

## Step 1: Trigger ZHIXI

```
知悉 — 我想做一个供应商质量跟踪工具，能帮我分析和记录供应商的交货质量、响应速度和配合度。
```

## Step 2: 知己 (Self-Knowledge)

ZHIXI will output:

```
表层请求：想做一个供应商质量跟踪工具
已确认事实：
  - 用户从事采购工作
  - 需要跟踪交货质量、响应速度、配合度
目标假设：
  - 用户需要一个系统化的方式来评估和比较供应商
  - 目前可能用 Excel 或记忆来管理
关键模糊点：
  - 数据从哪来？手工录入还是自动采集？
  - 一个人用还是团队共享？
  - 需要和现有系统对接吗？
```

ZHIXI asks 1-3 direction-changing questions:

1. 数据来源：你打算手工记录每次交互，还是希望从邮件/系统中自动采集？
2. 使用场景：只有你一个人用，还是团队共享？
3. 输出期望：你希望最终看到什么样的报告或看板？

## Step 3: 问己 (Self-Questioning)

After your answers, ZHIXI produces a requirements baseline:

```
目标：建立一个供应商质量评估系统
非目标：
  - 不是完整的 ERP 系统
  - 不替代现有的采购审批流程
约束：
  - 需要和现有 Excel 工作流兼容
  - 数据需要可导出
成功标准：
  - 每个供应商有可量化的质量评分
  - 能生成月度对比报告
开放问题：
  - 评分权重是否需要按品类调整？
当前决策：
  - 先用最小可行方案验证，再考虑自动化
```

## Step 4: 明需 (Requirement Clarity)

ZHIXI decomposes into capability units:

```
能力单元 1: 数据录入
  - 输入：供应商名称、日期、交货记录、评分
  - 输出：结构化数据记录
  - 工具：Excel / 表单
  - 验收标准：能在 2 分钟内完成一条记录

能力单元 2: 评分计算
  - 输入：历史交货记录
  - 输出：加权质量评分（0-100）
  - 工具：Python 脚本 / Excel 公式
  - 验收标准：评分结果和手工计算一致

能力单元 3: 报告生成
  - 输入：评分数据
  - 输出：月度对比报告（PDF/Excel）
  - 工具：Python + openpyxl
  - 验收标准：报告包含趋势图和排名
```

## Step 5: 洞意 (Insight & Execution)

ZHIXI executes and produces knowledge fragments:

```markdown
---
type: knowledge-fragment
confidence: 0.8
tags:
  - procurement/supplier-quality
---

# 供应商质量评分权重设计

## 摘要
采购场景下，供应商质量评分的核心维度包括交货准时率（30%）、
产品合格率（40%）、响应速度（20%）和配合度（10%）。

## 事实陈述
- 制造业采购中，产品合格率通常是最高权重维度
- 交货准时率直接影响生产计划

## 推断
- 权重可能需要按品类调整（如关键零部件合格率权重应更高）

## 建议
- 先用统一权重试运行 3 个月，再根据实际数据调整

## 适用边界
- 适用于制造业采购场景
- 未覆盖服务类供应商评估

## 来源
- 当前 Skill 执行结果 + 用户确认
```

## Result

In one conversation, you went from "I want a supplier tracking tool" to:
- A clear requirements baseline
- Decomposed capability units with acceptance criteria
- A working implementation plan
- Reusable knowledge fragments for future reference
