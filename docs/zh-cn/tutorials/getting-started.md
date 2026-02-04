---
title: "BMad 入门 (Getting Started)"
description: 安装 BMad 并构建你的第一个项目
---

使用 AI 驱动的 Workflows 和专门的 Agents，指导你完成规划、架构和实现，从而更快地构建软件。

## 你将学到什么

- 为新项目安装并初始化 BMad Method
- 为你的项目规模选择正确的规划轨道 (Planning Track)
- 在从需求到工作代码的各个阶段中取得进展
- 有效地使用 Agents 和 Workflows

:::note[先决条件]
- **Node.js 20+** — 安装程序需要
- **Git** — 推荐用于版本控制
- **AI 驱动的 IDE** — Claude Code, Cursor, Windsurf 或类似工具
- **一个项目想法** — 即使是一个简单的想法也适合学习
:::

:::tip[快速路径]
**安装 (Install)** → `npx bmad-method install`
**规划 (Plan)** → PM 创建 PRD，Architect 创建架构
**构建 (Build)** → SM 管理 Sprints，DEV 实现 Stories
每个 Workflow 使用 **Fresh chats (新对话)** 以避免上下文问题。
:::

## 理解 BMad

BMad 帮助你通过带有专门 AI Agents 的引导式 Workflows 来构建软件。该过程遵循四个阶段：

| 阶段 | 名称 | 发生了什么 |
| ----- | -------------- | --------------------------------------------------- |
| 1     | Analysis       | 头脑风暴，研究，产品简报 (Product Brief) *(可选)* |
| 2     | Planning       | 创建需求 (PRD 或 tech-spec)              |
| 3     | Solutioning    | 设计架构 *(仅限 BMad Method/Enterprise)* |
| 4     | Implementation | 一个接一个 Epic，一个接一个 Story 地构建 |

**[打开 Workflow Map](/docs/zh-cn/reference/workflow-map.md)** 以探索阶段、Workflows 和上下文管理。

根据你的项目复杂性，BMad 提供三个规划轨道：

| 轨道 (Track) | 最适合 | 创建的文档 |
| --------------- | ------------------------------------------------------ | -------------------------------------- |
| **Quick Flow**  | Bug 修复，简单功能，清晰范围 (1-15 stories) | 仅 Tech-spec |
| **BMad Method** | 产品，平台，复杂功能 (10-50+ stories) | PRD + Architecture + UX                |
| **Enterprise**  | 合规性，多租户系统 (30+ stories)         | PRD + Architecture + Security + DevOps |

:::note
Story 数量仅供参考，并非定义。根据规划需求选择你的轨道，而不是 Story 数学。
:::

## 安装

在你的项目目录中打开终端并运行：

```bash
npx bmad-method install
```

提示选择模块时，选择 **BMad Method**。

安装程序创建两个文件夹：
- `_bmad/` — agents, workflows, tasks, 和配置
- `_bmad-output/` — 目前为空，但这将是你保存 Artifacts 的地方

在项目文件夹中打开你的 AI IDE。运行 `help` workflow (`/bmad-help`) 查看下一步做什么 — 它会检测你已经完成了什么并推荐下一步。

:::note[如何加载 Agents 并运行 Workflows]
每个 Workflow 都有一个你在 IDE 中运行的 **Slash Command** (例如 `/bmad-bmm-create-prd`)。运行 Workflow 命令会自动加载适当的 Agent — 你不需要单独加载 Agents。你也可以直接加载 Agent 进行一般对话 (例如 `/bmad-agent-bmm-pm` 加载 PM Agent)。
:::

:::caution[新对话 (Fresh Chats)]
始终为每个 Workflow 开始一个新的对话。这可以防止上下文限制导致的问题。
:::

## 步骤 1: 创建你的计划

完成阶段 1-3。**为每个 Workflow 使用新对话。**

### 阶段 1: 分析 (可选)

此阶段的所有 Workflows 都是可选的：
- **brainstorming** (`/bmad-brainstorming`) — 引导式构思
- **research** (`/bmad-bmm-research`) — 市场和技术研究
- **create-product-brief** (`/bmad-bmm-create-product-brief`) — 推荐的基础文档

### 阶段 2: 规划 (必需)

**对于 BMad Method 和 Enterprise 轨道:**
1. 在新对话中加载 **PM Agent** (`/bmad-agent-bmm-pm`)
2. 运行 `prd` workflow (`/bmad-bmm-create-prd`)
3. 输出: `PRD.md`

**对于 Quick Flow 轨道:**
- 使用 `quick-spec` workflow (`/bmad-bmm-quick-spec`) 代替 PRD，然后跳至实现

:::note[UX 设计 (可选)]
如果你的项目有用户界面，加载 **UX-Designer Agent** (`/bmad-agent-bmm-ux-designer`) 并创建 PRD 后运行 UX 设计 workflow (`/bmad-bmm-create-ux-design`)。
:::

### 阶段 3: Solutioning (BMad Method/Enterprise)

**创建架构**
1. 在新对话中加载 **Architect Agent** (`/bmad-agent-bmm-architect`)
2. 运行 `create-architecture` (`/bmad-bmm-create-architecture`)
3. 输出: 包含技术决策的架构文档

**创建 Epics 和 Stories**

:::tip[V6 改进]
Epics 和 Stories 现在在架构*之后*创建。这会产生更高质量的 Stories，因为架构决策（数据库、API 模式、技术栈）直接影响工作的拆解方式。
:::

1. 在新对话中加载 **PM Agent** (`/bmad-agent-bmm-pm`)
2. 运行 `create-epics-and-stories` (`/bmad-bmm-create-epics-and-stories`)
3. Workflow 使用 PRD 和 Architecture 来创建技术上知情的 Stories

**实现准备就绪检查** *(强烈推荐)*
1. 在新对话中加载 **Architect Agent** (`/bmad-agent-bmm-architect`)
2. 运行 `check-implementation-readiness` (`/bmad-bmm-check-implementation-readiness`)
3. 验证所有规划文档的一致性

## 步骤 2: 构建你的项目

一旦规划完成，进入实现阶段。**每个 Workflow 应在新对话中运行。**

### 初始化 Sprint 规划

加载 **SM Agent** (`/bmad-agent-bmm-sm`) 并运行 `sprint-planning` (`/bmad-bmm-sprint-planning`)。这会创建 `sprint-status.yaml` 来跟踪所有 Epics 和 Stories。

### 构建周期 (Build Cycle)

对于每个 Story，用新对话重复此循环：

| 步骤 | Agent | Workflow       | 命令                    | 目的                            |
| ---- | ----- | -------------- | -------------------------- | ---------------------------------- |
| 1    | SM    | `create-story` | `/bmad-bmm-create-story`  | 从 Epic 创建 Story 文件        |
| 2    | DEV   | `dev-story`    | `/bmad-bmm-dev-story`     | 实现 Story                |
| 3    | DEV   | `code-review`  | `/bmad-bmm-code-review`   | 质量验证 *(推荐)* |

完成 Epic 中的所有 Stories 后，加载 **SM Agent** (`/bmad-agent-bmm-sm`) 并运行 `retrospective` (`/bmad-bmm-retrospective`).

## 你完成了什么

你已经学习了使用 BMad 构建的基础知识：

- 安装 BMad 并为你的 IDE 配置它
- 使用你选择的规划轨道初始化项目
- 创建规划文档 (PRD, Architecture, Epics & Stories)
- 理解实现的构建周期

你的项目现在有：

```
your-project/
├── _bmad/                         # BMad 配置
├── _bmad-output/
│   ├── PRD.md                     # 你的需求文档
│   ├── architecture.md            # 技术决策
│   ├── epics/                     # Epic 和 Story 文件
│   └── sprint-status.yaml         # Sprint 跟踪
└── ...
```

## 快速参考

| Workflow                         | Command                                    | Agent     | Purpose                              |
| -------------------------------- | ------------------------------------------ | --------- | ------------------------------------ |
| `help`                           | `/bmad-help`                               | Any       | 获取下一步指导      |
| `prd`                            | `/bmad-bmm-create-prd`                     | PM        | 创建产品需求文档 |
| `create-architecture`            | `/bmad-bmm-create-architecture`            | Architect | 创建架构文档         |
| `create-epics-and-stories`       | `/bmad-bmm-create-epics-and-stories`       | PM        | 将 PRD 分解为 Epics            |
| `check-implementation-readiness` | `/bmad-bmm-check-implementation-readiness` | Architect | 验证规划一致性           |
| `sprint-planning`                | `/bmad-bmm-sprint-planning`                | SM        | 初始化 Sprint 跟踪           |
| `create-story`                   | `/bmad-bmm-create-story`                   | SM        | 创建 Story 文件                  |
| `dev-story`                      | `/bmad-bmm-dev-story`                      | DEV       | 实现 Story                    |
| `code-review`                    | `/bmad-bmm-code-review`                    | DEV       | 审查实现的代码              |

## 常见问题

**我是否总是需要架构？**
仅限 BMad Method 和 Enterprise 轨道。Quick Flow 从 tech-spec 跳至实现。

**以后可以更改计划吗？**
可以。SM Agent 有一个 `correct-course` workflow (`/bmad-bmm-correct-course`) 用于处理范围变更。

**如果我想先头脑风暴怎么办？**
在开始 PRD 之前，加载 Analyst Agent (`/bmad-agent-bmm-analyst`) 并运行 `brainstorming` (`/bmad-brainstorming`)。

**我需要遵循严格的顺序吗？**
不严格。一旦你掌握了流程，你可以使用上面的快速参考直接运行 Workflows。

## 获取帮助

- **在 Workflows 期间** — Agents 通过问题和解释指导你
- **社区** — [Discord](https://discord.gg/gk8jAdXWmj) (#bmad-method-help, #report-bugs-and-issues)
- **卡住了？** — 运行 `help` (`/bmad-help`) 查看下一步做什么

## 关键要点

:::tip[记住这些]
- **始终使用 Fresh Chats (新对话)** — 为每个 Workflow 开始一个新对话
- **Track (轨道) 很重要** — Quick Flow 使用 quick-spec; Method/Enterprise 需要 PRD 和 Architecture
- **卡住时使用 `help` (`/bmad-help`)** — 它检测你的进度并建议下一步
:::

准备好开始了吗？安装 BMad 并让 Agents 指导你完成你的第一个项目。
