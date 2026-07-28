# Example: Knowledge Fragments for Technology Migration Decisions

## Scenario

A 15-person engineering team evaluates migrating their monolith to microservices. The CTO asks: "We're outgrowing the monolith, should we go microservices?"

## Steps 1-4: 知己 → 问己 → 明需

**知己** — 表层请求：评估从单体迁移到微服务。已确认事实：15 人团队，单体应用，维护困难感增加。目标假设：真实痛点可能是部署耦合、协作冲突或性能瓶颈。关键模糊点：部署频率？DevOps 能力？数据耦合度？

**问己** — 目标：评估是否值得迁移。约束：不能停服，15 人无法同时支撑两条架构线，周期 < 12 个月。当前决策：先做风险和能力评估。

**明需** — 三个能力单元：架构风险评估 → 风险矩阵、团队能力评估 → DevOps 就绪度、迁移决策框架 → 判断规则。

## Step 5: 洞意 (Insight & Execution)

ZHIXI produces four knowledge fragments with different `kind` values:

### Fragment 1: risk_boundary — 数据一致性风险

```markdown
---
type: knowledge-fragment
kind: risk_boundary
status: verified
privacy: sanitized
source: "module dependency analysis + database query audit"
confidence: 0.85
tags:
  - architecture/microservice
  - risk/data-consistency
---

# 微服务拆分的数据一致性风险边界

## 摘要 (Summary)
订单-库存-支付三域的强一致性事务是最大技术风险。
跨域查询占 35%，拆分后需引入 Saga 或事件溯源。

## 事实陈述 (Facts)
- 订单与库存共享 12 张表，5 张双向写入
- 跨域事务占写操作 28%，高峰期 35%
- 拆分后跨域延迟从 5ms 增至 50-200ms

## 推断 (Inferences)
- 直接拆分会导致超卖风险
- Saga 补偿复杂度可能抵消拆分收益
- 用户域耦合度低，可优先独立拆分

## 建议 (Suggestions)
- 第一阶段只拆用户域和通知域
- 订单-库存-支付暂保持单体，内部做模块化隔离
- 引入 CDC 监控跨域数据依赖

## 适用边界 (Applicability Boundaries)
- 基于当前数据耦合分析，依赖关系可能随业务变化
- 未考虑事件驱动架构引入后的变化

## 来源 (Sources)
- 30 天慢查询日志 + 代码静态分析
```

### Fragment 2: open_question — DevOps 能力就绪度

```markdown
---
type: knowledge-fragment
kind: open_question
status: candidate
privacy: sanitized
source: "ZHIXI session execution result"
confidence: 0.5
tags:
  - team/devops-readiness
  - architecture/microservice
---

# 团队是否具备微服务运维的 DevOps 能力？

## 摘要 (Summary)
15 人团队无专职 DevOps，运维由后端轮值。容器编排、分布式追踪
和自动化部署能力尚属空白。这是迁移成败的关键未解问题。

## 事实陈述 (Facts)
- 单机部署 + 手动发布，无容器化经验
- 仅 2 人了解 Docker 基础，无人有 K8s 生产经验
- 监控仅覆盖应用层

## 推断 (Inferences)
- 补齐能力缺口预计需 3-6 个月 + 1 名有经验的 SRE
- 云厂商托管 K8s 可降低运维门槛

## 建议 (Suggestions)
- 迁移前先用非核心服务做容器化试验
- 将 DevOps 就绪度设为迁移前置门控

## 适用边界 (Applicability Boundaries)
- 基于团队自评，未经实操验证
- 未考虑外部招聘或外包运维

## 来源 (Sources)
- 当前 Skill 执行结果 + 团队技能矩阵问卷
```

### Fragment 3: decision_rule — 何时拆、何时不拆

```markdown
---
type: knowledge-fragment
kind: decision_rule
status: verified
privacy: sanitized
source: "derived from risk assessment + capability evaluation"
confidence: 0.8
tags:
  - architecture/microservice
  - decision/migration-timing
---

# 微服务拆分时机决策规则

## 摘要 (Summary)
取决于三个维度：业务耦合度、DevOps 能力、部署痛点。
任意两个达到"就绪"才可启动。

## 事实陈述 (Facts)
- 团队 < 10 人时微服务运维成本通常高于收益
- 跨域查询 > 30% 时拆分复杂度超过模块化改造
- 无专职 DevOps 的团队故障恢复时间平均长 3 倍

## 推断 (Inferences)
- 当前团队尚不满足启动条件
- 建议先走"模块化单体"路线，6 个月后重新评估

## 建议 (Suggestions)
| 维度 | 不拆 | 延迟拆 | 可以拆 |
|---|---|---|---|
| 跨域查询 | > 40% | 20%-40% | < 20% |
| DevOps | 无容器经验 | 有基础无生产经验 | 生产级运维 |
| 部署痛点 | 月发布可接受 | 周发布偶冲突 | 日发布频繁阻塞 |
| 团队规模 | < 10 人 | 10-20 人 | > 20 人按域分组 |

当前：跨域 35%（延迟）、DevOps 无经验（不拆）→ **延迟拆**

## 适用边界 (Applicability Boundaries)
- 阈值基于本次评估，不同场景需调整
- 未考虑合规驱动的强制拆分

## 来源 (Sources)
- Fragment 1 + Fragment 2 + Martin Fowler "MonolithFirst"
```

### Fragment 4: deprecated — 旧部署流程

```markdown
---
type: knowledge-fragment
kind: procedure
status: deprecated
privacy: sanitized
source: "replaced by modular monolith deployment procedure"
confidence: 0.9
tags:
  - process/deployment
  - deprecated
---

# 旧部署流程：全量手动发布（已弃用）

## 摘要 (Summary)
已被替代的全量手动部署。全量构建+测试+部署耗时 45 分钟，
回滚需人工介入。已被模块化增量部署替代。

## 事实陈述 (Facts)
- 拉取代码 → 全量构建(15min) → 测试(20min) → 停机部署(10min)
- 月均 2 次发布，需 1 人全程值守

## 推断 (Inferences)
- 低频发布直接导致特性交付延迟
- 手动回滚是不敢频繁发布的核心原因

## 建议 (Suggestions)
- 保留碎片用于追溯架构演进
- 参考新流程（modular-monolith-deploy）

## 适用边界 (Applicability Boundaries)
- 仅作历史记录，不适用于当前部署

## 来源 (Sources)
- ./scripts/deploy-legacy.sh
- 被 modular-monolith-deploy 碎片替代
```

ZHIXI turns "should we go microservices?" into a structured decision framework — each fragment kind captures a different dimension of the decision, with every uncertainty tracked and every claim traceable to evidence.
