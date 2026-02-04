---
title: "防止 Agent 冲突"
description: 在多个 Agents 实现系统时，架构如何防止冲突
---

当多个 AI Agents 实现系统的不同部分时，它们可能会做出相互冲突的技术决策。架构文档通过建立共享标准来防止这种情况。

## 常见冲突类型

### API 风格冲突

没有架构：

- Agent A 使用 REST 的 `/users/{id}`
- Agent B 使用 GraphQL mutations
- 结果：不一致的 API 模式，困惑的消费者

有架构：

- ADR 指定：“所有客户端-服务器通信使用 GraphQL”
- 所有 Agents 遵循相同的模式

### 数据库设计冲突

没有架构：

- Agent A 使用 snake_case 列名
- Agent B 使用 camelCase 列名
- 结果：不一致的 Schema，令人困惑的查询

有架构：

- 标准文档指定命名约定
- 所有 Agents 遵循相同的模式

### 状态管理冲突

没有架构：

- Agent A 使用 Redux 进行全局状态管理
- Agent B 使用 React Context
- 结果：多种状态管理方法，复杂性

有架构：

- ADR 指定状态管理方法
- 所有 Agents 一致实现

## 架构如何防止冲突

### 1. 通过 ADRs 做出明确决策

每个重要的技术选择都记录有：

- 此时此地 (Context)（为什么这个决定很重要）
- 考虑的选项 (Options considered)（存在哪些替代方案）
- 决定 (Decision)（我们选择了什么）
- 理由 (Rationale)（为什么通过选择它）
- 后果 (Consequences)（接受的权衡）

### 2. FR/NFR 特定指导

架构将每个功能需求 (FR) 映射到技术方法：

- FR-001: 用户管理 → GraphQL mutations
- FR-002: 移动应用 → 优化查询

### 3. 标准和约定

明确记录：

- 目录结构
- 命名约定
- 代码组织
- 测试模式

## 架构作为共享上下文

将架构视为所有 Agents 在实现之前阅读的共享上下文：

```
PRD: "做什么 (What to build)"
     ↓
架构: "怎么做 (How to build it)"
     ↓
Agent A 阅读架构 → 实现 Epic 1
Agent B 阅读架构 → 实现 Epic 2
Agent C 阅读架构 → 实现 Epic 3
     ↓
结果: 一致的实现
```

## 关键 ADR 主题

建立防止冲突的常见决策：

| 主题 | 决策示例 |
| ---------------- | -------------------------------------------- |
| API 风格 | GraphQL vs REST vs gRPC                      |
| 数据库 | PostgreSQL vs MongoDB                        |
| 认证 (Auth) | JWT vs Sessions                              |
| 状态管理 | Redux vs Context vs Zustand                  |
| 样式 | CSS Modules vs Tailwind vs Styled Components |
| 测试 | Jest + Playwright vs Vitest + Cypress        |

## 应避免的反模式

:::caution[常见错误]
- **隐式决策** — “我们边做边弄 API 风格”导致不一致
- **过度文档化** — 记录每一个细微的选择导致分析瘫痪
- **陈旧的架构** — 写一次就不再更新的文档导致 Agents 遵循过时的模式
:::

:::tip[正确方法]
- 记录跨越 Epic 边界的决策
- 关注容易冲突的领域
- 边学边更新架构
- 对于重大变更使用 `correct-course`
:::
