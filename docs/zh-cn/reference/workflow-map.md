---
title: "Workflow Map"
description: BMad Method Workflow 阶段和输出的视觉参考
---

BMad Method (BMM) 是 BMad 生态系统中的一个模块，旨在遵循上下文工程 (Context Engineering) 和规划的最佳实践。AI Agents 在拥有清晰、结构化的上下文时工作效果最佳。BMM 系统跨 4 个不同的阶段逐步构建该上下文 - 每个阶段，以及每个阶段内的多个可选 Workflows，都会生成通知下一个阶段的文档，因此 Agents 始终知道构建什么以及为什么。

基本原理和概念来自在整个行业中作为思维框架取得巨大成功的敏捷方法论。

如果你在任何时候不确定该做什么，`/bmad-help` 命令将帮助你保持正轨或知道下一步做什么。你也可以随时参考这个 - 但如果你已经安装了 BMadMethod，/bmad-help 是完全交互式的，而且快得多。此外，如果你正在使用扩展了 BMad Method 或添加了其他互补非扩展模块的不同模块 - /bmad-help 会进化以了解所有可用的内容，从而为你提供当下最好的建议。

最后的重要说明：下面的每个 Workflow 都可以通过 Slash Command 直接使用你选择的工具运行，或者通过先加载 Agent 并使用 Agents 菜单中的条目来运行。

<iframe src="/workflow-map-diagram.html" width="100%" height="100%" frameborder="0" style="border-radius: 8px; border: 1px solid #334155; min-height: 900px;"></iframe>

*[交互式图表 - 将鼠标悬停在输出上以查看 Artifact 流向]*

## 阶段 1: 分析 (可选)

在致力于规划之前探索问题空间并验证想法。

| Workflow               | 目的                                                                    | 产生                  |
| ---------------------- | -------------------------------------------------------------------------- | ------------------------- |
| `brainstorm`           | 在头脑风暴教练的引导下头脑风暴项目想法 | `brainstorming-report.md` |
| `research`             | 验证市场、技术或领域假设                          | 研究发现         |
| `create-product-brief` | 捕获战略愿景                                                   | `product-brief.md`        |

## 阶段 2: 规划

定义构建什么以及为谁构建。

| Workflow           | 目的                                  | 产生     |
| ------------------ | ---------------------------------------- | ------------ |
| `create-prd`       | 定义需求 (FRs/NFRs)           | `PRD.md`     |
| `create-ux-design` | 设计用户体验 (当 UX 很重要时) | `ux-spec.md` |

## 阶段 3: Solutioning

决定如何构建它并将工作分解为 Stories。

| Workflow                         | 目的                                    | 产生                    |
| -------------------------------- | ------------------------------------------ | --------------------------- |
| `create-architecture`            | 使技术决策明确          | 带 ADRs 的 `architecture.md` |
| `create-epics-and-stories`       | 将需求分解为可实现的工作 | 带有 Stories 的 Epic 文件     |
| `check-implementation-readiness` | 实现前的把关检查 (Gate check)           | PASS/CONCERNS/FAIL 决定 |

## 阶段 4: 实现

构建它，一次一个 Story。

| Workflow          | 目的                                | 产生                      |
| ----------------- | -------------------------------------- | ----------------------------- |
| `sprint-planning` | 初始化跟踪 (每个项目一次) | `sprint-status.yaml`          |
| `create-story`    | 准备下一个要实现的 Story  | `story-[slug].md`             |
| `dev-story`       | 实现 Story                    | 工作代码 + 测试          |
| `automate` (QA)   | 为现有功能生成测试   | 测试套件                    |
| `code-review`     | 验证实现质量        | 批准或请求更改 |
| `correct-course`  | 处理重大的中途 Sprint 变更  | 更新的计划或重新路由    |
| `retrospective`   | Epic 完成后审查           | 经验教训               |

**Quinn (QA Agent):** 用于测试自动化的内置 QA Agent。使用 `QA` 或 `bmad-bmm-qa-automate` 触发。使用你项目的测试框架生成标准 API 和 E2E 测试。适合初学者，无需配置。对于高级测试策略，请安装 [Test Architect (TEA)](https://bmad-code-org.github.io/bmad-method-test-architecture-enterprise/) 模块。

## Quick Flow (并行轨道)

对于小型、易于理解的工作，跳过阶段 1-3。

| Workflow     | 目的                                    | 产生                                      |
| ------------ | ------------------------------------------ | --------------------------------------------- |
| `quick-spec` | 定义临时变更                    | `tech-spec.md` (用于小变更的 Story 文件) |
| `quick-dev`  | 根据规范或直接指令实现 | 工作代码 + 测试                          |

## 上下文管理

每个文档都成为下一阶段的上下文。PRD 告诉 Architect 哪些约束很重要。Architecture 告诉 Dev Agent 遵循哪些模式。Story 文件为实现提供专注、完整的上下文。没有这种结构，Agents 会做出不一致的决策。

对于 Brownfield 项目，`document-project` 创建或更新 `project-context.md` - 代码库中存在什么以及所有实现 Workflows 必须遵守的规则。仅在阶段 4 之前运行它，并在发生重大变化时（结构、架构或那些规则）再次运行它。你也可以手动编辑 `project-context.md`。

如果存在，所有实现 Workflows 都会加载 `project-context.md`。每个 Workflow 的额外上下文：

| Workflow       | 同时加载                   |
| -------------- | ---------------------------- |
| `create-story` | epics, PRD, architecture, UX |
| `dev-story`    | story file                   |
| `code-review`  | architecture, story file     |
| `quick-spec`   | planning docs (如果存在)     |
| `quick-dev`    | tech-spec                    |
