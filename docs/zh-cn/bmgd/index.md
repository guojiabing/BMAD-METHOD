---
title: "BMGD 快速指南"
description: BMad Game Dev Studio 快速参考
---

![BMGD Logo](../../bmgd/bmgd-logo.png)

# BMGD 快速指南

BMad Game Dev Studio (BMGD) 通过游戏特定功能扩展了 BMM。由游戏行业资深人士开发，指导你完成产品研究、技术设计、叙事设计和完整的 Epic 驱动的生产周期。

## 建设中

文档正在紧锣密鼓地建设中，以赶上新的 Beta 版本。我们将尽快完善文档。目前，如果你有任何问题，请在 Discord 的 BMGD 版块提问。

![BMGD Workflow](../../bmgd/workflow.jpg)

## 快速开始

**Install → Game Brief → GDD → (Narrative) → Architecture → Build**

BMGD 是一个通过 BMAD Method 安装的可选模块：`npx bmad-method install`

查看 [How-To 参考](#how-to-reference) 获取命令。

## 开发阶段

| 阶段 | 名称 | 关键活动 |
|-------|------|----------------|
| 1 | **预生产 (Preproduction)** | 游戏头脑风暴，Game Brief，市场研究 |
| 2 | **设计 (Design)** | GDD 创建，叙事设计 (针对故事驱动的游戏) |
| 3 | **技术 (Technical)** | 游戏架构 (引擎，系统，模式) |
| 4 | **生产 (Production)** | Sprint 规划，Story 开发，代码审查，测试 |

## BMGD Agents

| Agent | 目的 |
|-------|---------|
| Game Designer | 游戏机制，平衡，玩家心理 |
| Game Developer | 使用引擎特定模式进行实现 |
| Game Architect | 引擎选择，系统设计，技术结构 |
| Game Scrum Master | Sprint 规划和 Epic 管理 |
| Game QA | 游戏测试，引擎特定测试，性能分析 |
| Game Solo Dev | 针对独立项目的全栈游戏开发 |

## 关键文档

| 文档 | 目的 |
|----------|---------|
| **Game Brief** | 愿景，市场定位，基本面 |
| **GDD** | 核心循环，机制，进程，美术/音频方向 |
| **叙事设计** | 故事结构，角色，世界构建，对话 |
| **架构** | 引擎，系统，模式，项目结构 |

## 游戏类型模板

BMGD 包含 24 种游戏类型模板，可自动配置 GDD 章节：

动作，冒险，解谜，RPG，策略，模拟，体育，赛车，格斗，恐怖，平台，射击等等。

每个模板提供特定流派的 GDD 章节、机制模式、测试考虑因素和需要避免的常见陷阱。

## 解释: BMGD vs BMM

### 何时使用各个模块

| 使用 BMGD | 使用 BMM |
|--------------|-------------|
| 视频游戏 | Web 应用 |
| 交互式体验 | APIs 和服务 |
| 游戏原型设计 | 移动应用 (非游戏) |
| Game Jams | 通用软件项目 |

### 阶段映射

| BMM 阶段 | BMGD 阶段 | 关键差异 |
|-----------|------------|----------------|
| Analysis | Preproduction | 游戏概念，Game Brief 代替 Product Brief |
| Planning | Design | GDD 代替 PRD；可选的叙事设计 |
| Solutioning | Technical | 关注引擎选择，游戏特定模式 |
| Implementation | Production | Game QA 代替 TEA；引擎特定测试 |

### 文档差异

| BMM | BMGD | 备注 |
|-----|------|-------|
| Product Brief | Game Brief | 捕获愿景，市场，基本面 |
| PRD | GDD | 包含机制，平衡，玩家体验 |
| N/A | Narrative Design | 故事，角色，世界 (故事驱动的游戏) |
| Architecture | Architecture | BMGD 版本包含引擎特定模式和考虑因素 |

### 测试差异

**BMM (TEA):** Web 聚焦的测试，使用 Playwright, Cypress, API 测试, E2E (Web 应用)。

**BMGD (Game QA):** 引擎特定框架 (Unity, Unreal, Godot)，游戏玩法测试，性能分析，试玩规划，平衡验证。

## How-To 参考

| 我需要... | 操作 |
|--------------|--------------------------------------------------------------------------------------------------------|
| 安装 BMGD | 运行 `npx bmad-method install` 并在模块安装期间选择 BMGD |
| 开始一个新游戏 | 运行 `/bmad-gds-brainstorm-game`，然后 `/bmad:gds:create-game-brief` |
| 设计我的游戏 | 运行 `/bmad-gds-create-gdd`；如果故事繁重添加 `/bmad:gds:narrative` |
| 规划架构 | 使用 Game Architect 运行 `/bmad-gds-game-architecture` |
| 构建我的游戏 | 使用 Phase 4 生产 Workflows - 运行 `/bmad-help` 查看下一步 |
| 快速测试想法 | 使用 [Quick-Flow](/docs/zh-cn/bmgd/quick-flow-workflows.md) 进行快速原型设计 |

## 延伸阅读

- [游戏类型指南](/docs/zh-cn/bmgd/game-types.md)
- [Quick-Flow 指南](/docs/zh-cn/bmgd/quick-flow-workflows.md)
