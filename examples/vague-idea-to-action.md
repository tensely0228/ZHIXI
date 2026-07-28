---
type: knowledge-fragment
status: candidate
privacy: sanitized
source: "ZHIXI example session output"
confidence: 0.6
tags:
  - example/workflow
---

# Example: From Vague Idea to Action Plan

## Scenario

You have a rough idea: "I want to build a tool that helps me track my reading habits and organize book notes."

## Step 1: Trigger ZHIXI

```
知悉 — 我想做一个读书笔记管理工具，能帮我记录读过的书、整理笔记和回顾核心观点。
```

## Step 2: 知己 (Self-Knowledge)

ZHIXI will output:

```
表层请求：想做一个读书笔记管理工具
已确认事实：
  - 用户有阅读习惯
  - 需要记录书籍、整理笔记、回顾观点
目标假设：
  - 用户需要一个系统化的方式来管理和检索阅读内容
  - 目前可能用零散的方式（备忘录、纸质笔记）来管理
关键模糊点：
  - 记录粒度：只记书名和评分，还是逐章笔记？
  - 检索方式：按标签、时间线还是知识图谱？
  - 输出形式：个人回顾还是可分享的读书报告？
```

ZHIXI asks 1-3 direction-changing questions:

1. 记录粒度：你希望每本书记录到什么程度？简单评分还是详细章节笔记？
2. 检索需求：你更多是按主题找笔记，还是按时间线回顾？
3. 输出期望：你希望最终看到什么样的总结或报告？

## Step 3: 问己 (Self-Questioning)

After your answers, ZHIXI produces a requirements baseline:

```
目标：建立一个个人阅读笔记管理系统
非目标：
  - 不是社交读书平台
  - 不替代专业的文献管理工具（如 Zotero）
约束：
  - 数据需要可导出
  - 支持离线使用
成功标准：
  - 每本书有结构化的笔记记录
  - 能按主题快速检索相关笔记
  - 能生成季度阅读回顾报告
开放问题：
  - 是否需要和现有笔记工具（Obsidian、Notion）集成？
当前决策：
  - 先用最小可行方案验证，再考虑工具集成
```

## Step 4: 明需 (Requirement Clarity)

ZHIXI decomposes into capability units:

```
能力单元 1: 书籍录入
  - 输入：书名、作者、分类、阅读日期
  - 输出：结构化书籍记录
  - 工具：表单 / Markdown 模板
  - 验收标准：能在 1 分钟内完成一条记录

能力单元 2: 笔记管理
  - 输入：章节笔记、关键摘录、个人感悟
  - 输出：按书籍组织的结构化笔记
  - 工具：Markdown 文件 + 标签系统
  - 验收标准：支持按标签和书名双向检索

能力单元 3: 回顾报告
  - 输入：阅读记录和笔记数据
  - 输出：季度阅读回顾报告
  - 工具：Python 脚本 / 模板引擎
  - 验收标准：报告包含阅读统计、高频主题和精选笔记
```

## Step 5: 洞意 (Insight & Execution)

ZHIXI executes and produces knowledge fragments:

```markdown
---
type: knowledge-fragment
status: candidate
privacy: sanitized
source: "ZHIXI session execution result"
confidence: 0.6
tags:
  - personal-knowledge/reading-notes
---

# 读书笔记标签体系设计

## 摘要
个人阅读笔记管理中，标签体系应包含三个维度：
主题领域（30%）、内容类型（40%）、实用程度（30%）。

## 事实陈述
- 多维度标签比单一分类检索效率更高
- 实用程度标签有助于快速定位可行动的知识

## 推断
- 标签数量控制在 20 个以内，过多会导致分类疲劳
- 主题标签应随阅读范围动态扩展

## 建议
- 先设 5-8 个核心标签，阅读 20 本书后再扩展
- 定期合并相似标签，保持体系精简

## 适用边界
- 适用于非虚构类书籍管理
- 未覆盖学术论文和小说类书籍

## 来源
- 当前 Skill 执行结果 + 用户确认
```

## Result

In one conversation, you went from "I want a reading note tool" to:
- A clear requirements baseline
- Decomposed capability units with acceptance criteria
- A working implementation plan
- Reusable knowledge fragments for future reference
