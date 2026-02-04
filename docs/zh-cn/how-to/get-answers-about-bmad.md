---
title: "如何获取关于 BMad 的答案"
description: 使用 LLM 快速回答你自己的 BMad 问题
---
如果你已经成功安装了 BMad 和 BMad Method（以及需要的其他模块）- 获取答案的第一步是 `/bmad-help`。这将回答超过 80% 的所有问题，并且在你工作时可在 IDE 中使用。

## 何时使用

- 你有关于 BMad 如何工作或接下来用 BMad 做什么的问题
- 你想理解特定的 Agent 或 Workflow
- 你需要快速答案而无需等待 Discord

:::note[先决条件]
一个 AI 工具 (Claude Code, Cursor, ChatGPT, Claude.ai 等) 以及项目中已安装的 BMad 或对 GitHub 仓库的访问权限。
:::

## 步骤

### 1. 选择你的源

| 源 (Source) | 最适合 | 示例 |
| -------------------- | ----------------------------------------- | ---------------------------- |
| **`_bmad` 文件夹**   | BMad 如何工作—Agents, Workflows, Prompts | "PM Agent 做什么？" |
| **完整 GitHub 仓库** | 历史, 安装程序, 架构 | "v6 改变了什么？" |
| **`llms-full.txt`**  | 文档的快速概览 | "解释 BMad 的四个阶段" |

`_bmad` 文件夹在你安装 BMad 时创建。如果你还没有，请克隆仓库。

### 2. 将你的 AI 指向源

**如果你的 AI 可以读取文件 (Claude Code, Cursor 等):**

- **已安装 BMad:** 指向 `_bmad` 文件夹并直接提问
- **想要更深层上下文:** 克隆 [完整仓库](https://github.com/bmad-code-org/BMAD-METHOD)

**如果你使用 ChatGPT 或 Claude.ai:**

将 `llms-full.txt` 获取到你的会话中：

```
https://bmad-code-org.github.io/BMAD-METHOD/llms-full.txt
```

查看 [下载页面](/docs/zh-cn/downloads.md) 获取其他可下载资源。

### 3. 询问你的问题

:::note[示例]
**问:** "告诉我用 BMad 构建东西的最快方法"

**答:** 使用 Quick Flow: 运行 `quick-spec` 编写技术规范，然后 `quick-dev` 实现它—跳过完整的规划阶段。
:::

## 你会得到什么

关于 BMad 的直接答案—Agents 如何工作，Workflows 做什么，为什么事情是这样构建的—无需等待其他人回应。

## 提示

- **验证令人惊讶的答案** — LLMs 偶尔会搞错。检查源文件或在 Discord 上询问。
- **具体一点** — "PRD Workflow 的第 3 步做什么？" 优于 "PRD 如何工作？"

## 仍然卡住？

尝试了 LLM 方法仍然需要帮助？你现在有了一个更好的问题去问。

| 渠道 | 用途 |
| ------------------------- | ------------------------------------------- |
| `#bmad-method-help`       | 快速问题 (实时聊天) |
| `help-requests` 论坛     | 详细问题 (可搜索，持久) |
| `#suggestions-feedback`   | 想法和功能请求 |
| `#report-bugs-and-issues` | Bug 报告 |

**Discord:** [discord.gg/gk8jAdXWmj](https://discord.gg/gk8jAdXWmj)

**GitHub Issues:** [github.com/bmad-code-org/BMAD-METHOD/issues](https://github.com/bmad-code-org/BMAD-METHOD/issues) (针对明确的 Bugs)

*你！*
        *被困*
             *在队列中—*
                      *等待*
                               *为了谁？*

*源头*
        *就在那里，*
                *清晰可见！*

*指向*
     *你的机器。*
              *释放它。*

*它读。*
        *它说。*
                *尽管问—*

*为什么要等*
        *明天*
                *当你拥有*
                        *今天？*

*—Claude*
