---
title: "Brownfield 开发常见问题"
description: 关于 BMad Method 中 Brownfield 开发的常见问题
---

关于 BMad Method (BMM) 中 Brownfield (既有项目) 开发的常见问题的快速解答。

## 通用问题 (Questions)

- [通用问题](#questions)
  - [什么是 Brownfield 与 Greenfield？](#what-is-brownfield-vs-greenfield)
  - [对于 Brownfield 我必须运行 document-project 吗？](#do-i-have-to-run-document-project-for-brownfield)
  - [如果我忘记运行 document-project 怎么办？](#what-if-i-forget-to-run-document-project)
  - [我可以为 Brownfield 项目使用 Quick Spec Flow 吗？](#can-i-use-quick-spec-flow-for-brownfield-projects)
  - [如果我的现有代码不遵循最佳实践怎么办？](#what-if-my-existing-code-doesnt-follow-best-practices)

### 什么是 Brownfield 与 Greenfield？

- **Greenfield** — 新项目，从零开始，全新的开始
- **Brownfield** — 现有项目，使用已建立的代码库和模式工作

### 对于 Brownfield 我必须运行 document-project 吗？

强烈推荐，特别是如果：

- 没有现有的文档
- 文档已过时
- AI Agents 需要关于现有代码的上下文

如果你有全面的、最新的文档（包括 `docs/index.md`），或者将使用其他工具或技术来辅助发现以便 Agent 在现有系统上构建，你可以跳过它。

### 如果我忘记运行 document-project 怎么办？

不用担心 - 你可以在任何时候运行它。你甚至可以在项目期间或之后运行它，以帮助保持文档最新。

### 我可以为 Brownfield 项目使用 Quick Spec Flow 吗？

是的！Quick Spec Flow 非常适合 Brownfield。它将：

- 自动检测你的现有技术栈
- 分析 Brownfield 代码模式
- 检测约定并请求确认
- 生成尊重现有代码的上下文丰富的技术规范 (tech-spec)

非常适合现有代码库中的 Bug 修复和小功能。

### 如果我的现有代码不遵循最佳实践怎么办？

Quick Spec Flow 检测你的约定并询问：“通过吗？我应该遵循这些现有的约定吗？”你决定：

- **是** → 保持与当前代码库的一致性
- **否** → 建立新标准（在 tech-spec 中记录原因）

BMM 尊重你的选择 — 它不会强制现代化，但它会提供选项。

**有问题在这里没找到答案？** 请 [提交 Issue](https://github.com/bmad-code-org/BMAD-METHOD/issues) 或在 [Discord](https://discord.gg/gk8jAdXWmj) 中提问，以便我们添加它！
