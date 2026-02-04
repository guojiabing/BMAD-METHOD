---
title: "为什么 Solutioning 很重要"
description: 理解为什么 Solutioning 阶段对于多 Epic 项目至关重要
---

第三阶段 (Phase 3 - Solutioning) 将**做什么** (What to build, 来自 Planning 阶段) 转化为**通过什么方式** (How to build it, 技术设计)。此阶段通过在开始实现之前记录架构决策，防止多 Epic 项目中的 Agent 冲突。

## 没有 Solutioning 的问题

```
Agent 1 使用 REST API 实现 Epic 1
Agent 2 使用 GraphQL 实现 Epic 2
结果: 不一致的 API 设计，集成的噩梦
```

当多个 Agents 在没有共享架构指导的情况下实现系统的不同部分时，它们会做出可能冲突的独立技术决策。

## 有 Solutioning 的解决方案

```
architecture workflow 决定: "所有 API 都使用 GraphQL"
所有 Agents 遵循架构决策
结果: 一致的实现，无冲突
```

通过明确记录技术决策，所有 Agents 都能一致地实现，集成变得简单直接。

## Solutioning vs Planning

| 方面 | Planning (阶段 2) | Solutioning (阶段 3) |
| -------- | ----------------------- | --------------------------------- |
| 问题 | 做什么 (What) 和为什么 (Why)？ | 怎么做 (How)？然后是哪些工作单元？ |
| 输出 | FRs/NFRs (需求) | 架构 + Epics/Stories |
| Agent    | PM                      | Architect → PM                    |
| 受众 | 利益相关者 (Stakeholders) | 开发者 |
| 文档 | PRD (FRs/NFRs)          | 架构 + Epic 文件 |
| 层级 | 业务逻辑 | 技术设计 + 工作分解 |

## 关键原则

**使技术决策明确并记录在案**，以便所有 Agents 一致地实现。

这防止了：

- API 风格冲突 (REST vs GraphQL)
- 数据库设计不一致
- 状态管理分歧
- 命名约定不匹配
- 安全方法差异

## 何时需要 Solutioning

| 轨道 (Track) | 需要 Solutioning 吗？ |
|-------|----------------------|
| Quick Flow | 否 - 完全跳过 |
| BMad Method Simple | 可选 |
| BMad Method Complex | 是 |
| Enterprise | 是 |

:::tip[经验法则]
如果你有多个 Epics 可能由不同的 Agents 实现，你需要 Solutioning。
:::

## 跳过的代价

在复杂项目上跳过 Solutioning 会导致：

- Sprint 中途发现**集成问题**
- 因实现冲突导致的**返工**
- 总体**更长的开发时间**
- 因模式不一致导致的**技术债务**

:::caution[成本乘数]
在 Solutioning 中发现一致性问题比在实现过程中发现快 10 倍。
:::
