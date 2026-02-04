---
title: "如何安装 BMad"
description: 在你的项目中安装 BMad 的分步指南
---

使用 `npx bmad-method install` 命令在你的项目中安装 BMad，并选择你需要的模块和 AI 工具。

## 何时使用

- 开始一个 BMad 新项目
- 将 BMad 添加到现有代码库
- 更新现有的 BMad 安装

:::note[先决条件]
- **Node.js** 20+ (安装程序需要)
- **Git** (推荐)
- **AI 工具** (Claude Code, Cursor, Windsurf 或类似工具)
:::

## 步骤

### 1. 运行安装程序

```bash
npx bmad-method install
```

### 2. 选择安装位置

安装程序会询问将 BMad 文件安装在哪里：

- 当前目录 (推荐用于新项目，如果你自己创建了目录并在其中运行)
- 自定义路径

### 3. 选择你的 AI 工具

选择你使用的 AI 工具：

- Claude Code
- Cursor
- Windsurf
- 其他 (Others)

每个工具都有自己的集成命令方式。安装程序会创建微小的 prompt 文件来激活 Workflows 和 Agents — 它只是把它们放在你的工具期望找到它们的地方。

### 4. 选择模块

安装程序显示可用模块。选择你需要的模块 — 大多数用户只需要 **BMad Method** (软件开发模块)。

### 5. 跟随提示

安装程序会引导你完成剩余部分 — 自定义内容、设置等。

## 你会得到什么

```
your-project/
├── _bmad/
├── _bmad/
│   ├── bmm/            # 你选择的模块
│   │   └── config.yaml # 模块设置 (如果你需要更改它们)
│   ├── core/           # 必需的核心模块
│   └── ...
├── _bmad-output/       # 生成的 Artifacts
└── .claude/            # Claude Code 命令 (如果使用 Claude Code)
```

## 验证安装

运行 `help` workflow (在大多数平台上是 `/bmad-help`) 来验证一切正常，并查看下一步做什么。

**来自 main 分支的最新版:**

```bash
npx github:bmad-code-org/BMAD-METHOD install
```

如果你想在正式发布前使用最新功能，可以使用这些。可能会有不稳定。

## 故障排除

**安装程序报错** — 将输出复制粘贴到你的 AI 助手中，让它弄清楚。

**安装程序正常工作但稍后某些东西无法工作** — 你的 AI 需要 BMad 上下文来帮助。查看 [如何获取关于 BMad 的答案](../get-answers-about-bmad.md) 了解如何将你的 AI 指向正确的源。
