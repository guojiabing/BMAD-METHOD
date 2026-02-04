---
title: "Brownfield (既有项目) 开发"
description: 如何在现有代码库上使用 BMad Method
---

在处理现有项目和遗留代码库时有效地使用 BMad Method。

## 什么是 Brownfield 开发？

**Brownfield** 指的是在具有已建立的代码库和模式的现有项目上工作，与 **Greenfield**（意味着从零开始，全新的开始）相对。

本指南涵盖了使用 BMad Method 入门 Brownfield 项目的基本工作流。

:::note[先决条件]
- 已安装 BMad Method (`npx bmad-method install`)
- 你想处理的现有代码库
- 访问 AI 驱动的 IDE (Claude Code, Cursor, 或 Windsurf)
:::

## 步骤 1: 清理已完成的规划 Artifacts

如果你已经通过 BMad 流程完成了所有 PRD Epics 和 Stories，请清理这些文件。归档它们，删除它们，或在需要时依赖版本历史。不要将这些文件保留在：

- `docs/`
- `_bmad-output/planning-artifacts/`
- `_bmad-output/implementation-artifacts/`

## 步骤 2: 维护高质量的项目文档

你的 `docs/` 文件夹应包含简洁、组织良好的文档，准确代表你的项目：

- 意图和业务理由
- 业务规则
- 架构
- 任何其他相关的项目信息

对于复杂项目，考虑使用 `document-project` workflow。它提供运行时变体，将扫描你的整个项目并记录其实际当前状态。

## 步骤 3: 获取帮助

根据你的独特需求获取关于下一步做什么的帮助。

当你不知道下一步做什么时，运行 `bmad-help` 获取指导。

### 选择你的方法

根据变更的范围，你有两个主要选项：

| 范围 | 推荐方法 |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **小更新或添加** | 使用 `quick-flow-solo-dev` 创建 tech-spec 并实现变更。完整的四阶段 BMad Method 可能大材小用。 |
| **重大变更或添加** | 从 BMad Method 开始，根据需要应用尽可能多或尽可能少的严格流程。 |

### PRD 创建期间

创建 Brief 或直接跳转到 PRD 时，确保 Agent：

- 查找并分析你现有的项目文档
- 读取关于你当前系统的适当上下文

你可以明确地指导 Agent，但目标是确保新功能与你的现有系统良好集成。

### UX 考虑

UX 工作是可选的。决定不取决于你的项目是否有 UX，而是取决于：

- 你是否要处理 UX 变更
- 是否需要重要的新 UX 设计或模式

如果你的变更是对你满意的现有屏幕进行简单更新，则不需要完整的 UX 流程。

### 架构考虑

做架构时，确保 Architect：

- 使用适当的文档文件
- 扫描现有的代码库

在这里要密切注意，以防止重新发明轮子或做出与你现有架构不一致的决策。

## 更多信息

- **[Brownfield 中的快速修复](/docs/zh-cn/how-to/brownfield/quick-fix-in-brownfield.md)** - Bug 修复和临时变更
- **[Brownfield FAQ](/docs/zh-cn/explanation/brownfield-faq.md)** - 关于 Brownfield 开发的常见问题
