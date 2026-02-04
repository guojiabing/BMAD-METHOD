---
title: "如何在 Brownfield 项目中快速修复"
description: 如何在 Brownfield 项目中进行快速修复和临时变更
---

对于不需要完整 BMad Method 或 Quick Flow 的 Bug 修复、重构或小规模针对性变更，直接使用 **DEV Agent**。

## 何时使用

- 简单的 Bug 修复
- 不需要广泛构思、规划或架构转变的小型重构和变更
- 结合内置工具规划和执行模式的大型重构或改进，或者更好的是使用 Quick Flow
- 学习你的代码库

## 步骤

### 1. 加载一个 Agent

对于快速修复，你可以使用：

- **DEV Agent** - 用于以实现为中心的工作
- **Quick Flow Solo Dev** - 用于稍大一点的变更，仍需要 quick-spec 以保持 Agent 与规划和标准对齐

### 2. 描述变更

只需告诉 Agent 你需要什么：

```
Fix the login validation bug that allows empty passwords
```

或

```
Refactor the UserService to use async/await instead of callbacks
```

### 3. 让 Agent 工作

Agent 将：

- 分析相关代码
- 提出解决方案
- 实现变更
- 运行测试 (如果可用)

### 4. 审查并提交

审查所做的更改并在满意时提交。

## 学习你的代码库

这种方法也非常适合探索不熟悉的代码：

```
Explain how the authentication system works in this codebase
```

```
Show me where error handling happens in the API layer
```

无论代码是否由 AI 生成，LLMs 都非常擅长解释和分析代码。使用 Agent 来：

- 了解你的项目
- 理解事物是如何构建的
- 探索代码库中不熟悉的部分

## 何时升级到正式规划

当出现以下情况时，考虑使用 Quick Flow 或完整的 BMad Method：

- 变更影响多个文件或系统
- 你不确定范围
- 修复的复杂性不断增长
- 你需要为变更提供文档
