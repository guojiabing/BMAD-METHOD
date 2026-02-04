---
title: "如何升级到 v6"
description: 从 BMad v4 迁移到 v6
---

使用 BMad 安装程序从 v4 升级到 v6，其中包括自动检测旧版安装和迁移辅助。

## 何时使用

- 你安装了 BMad v4 (`.bmad-method` 文件夹)
- 你想迁移到新的 v6 架构
- 你有需要保留的现有规划 Artifacts

:::note[先决条件]
- Node.js 20+
- 现有的 BMad v4 安装
:::

## 步骤

### 1. 运行安装程序

```bash
npx bmad-method install
```

安装程序自动检测：

- **旧版 v4 文件夹**: `.bmad-method`
- **IDE 命令 Artifacts**: `.claude/commands/`, `.cursor/commands/` 等中的旧版 bmad 文件夹

### 2. 处理旧版安装

检测到 v4 时，你可以：

- 允许安装程序备份并删除 `.bmad-method`
- 退出并手动处理清理
- 保留两者 (对于同一项目不推荐)

### 3. 清理 IDE 命令

手动删除旧版 v4 IDE 命令：

- `.claude/commands/BMad/agents`
- `.claude/commands/BMad/tasks`

新的 v6 命令将位于 `.claude/commands/bmad/<module>/agents|workflows`。

:::tip[意外删除了命令？]
如果你删除了错误的命令，重新运行安装程序并选择 "quick update" 以恢复它们。
:::

### 4. 迁移规划 Artifacts

**如果你有规划文档 (Brief/PRD/UX/Architecture):**

移动它们到 `_bmad-output/planning-artifacts/` 并使用描述性名称：

- 对于 PRD 文档，文件名中包含 `PRD`
- 相应地包含 `brief`, `architecture`, 或 `ux-design`
- 分片文档可以放在命名的子文件夹中

**如果你正处于规划中期:** 考虑使用 v6 Workflows 重新开始。使用你现有的文档作为输入—带有网络搜索和 IDE 计划模式的新渐进式发现 Workflows 会产生更好的结果。

### 5. 迁移进行中的开发

如果你已创建或实现了 Stories:

1. 完成 v6 安装
2. 将 `epics.md` 或 `epics/epic*.md` 放在 `_bmad-output/planning-artifacts/` 中
3. 运行 Scrum Master 的 `sprint-planning` workflow
4. 告诉 SM 哪些 Epics/Stories 已经完成

### 6. 迁移 Agent 自定义

**v4:** 直接在 `_bmad-*` 文件夹中修改 Agent 文件

**v6:** 所有自定义都在 `_bmad/_config/agents/` 中使用 customize 文件：

```yaml
# _bmad/_config/agents/bmm-pm.customize.yaml
persona:
  name: 'Captain Jack'
  role: 'Swashbuckling Product Owner'
  communication_style: |
    - Talk like a pirate
    - Use nautical metaphors
```

修改自定义文件后，重新运行安装程序并选择 "rebuild all agents" 或 "quick update"。

## 你会得到什么

**v6 统一结构:**

```
your-project/
└── _bmad/               # 单一安装文件夹
    ├── _config/         # 你的自定义
    │   └── agents/      # Agent 自定义文件
    ├── core/            # 通用核心框架
    ├── bmm/             # BMad Method 模块
    ├── bmb/             # BMad Builder
    └── cis/             # 创意智能套件 (Creative Intelligence Suite)
├── _bmad-output/        # 输出文件夹 (在 v4 中是 doc 文件夹)
```

## 模块迁移

| v4 模块 | v6 状态 |
|-----------|-----------|
| `_bmad-2d-phaser-game-dev` | 集成到 BMGD 模块 |
| `_bmad-2d-unity-game-dev` | 集成到 BMGD 模块 |
| `_bmad-godot-game-dev` | 集成到 BMGD 模块 |
| `_bmad-infrastructure-devops` | 已弃用 — 新的 DevOps Agent 即将推出 |
| `_bmad-creative-writing` | 未适配 — 新的 v6 模块即将推出 |

## 关键变更

| 概念 | v4 | v6 |
|---------|----|----|
| **Core** | `_bmad-core` 实际上是 BMad Method | `_bmad/core/` 是通用框架 |
| **Method** | `_bmad-method` | `_bmad/bmm/` |
| **Config** | 直接修改文件 | 每个模块 `config.yaml` |
| **Documents** | 需要分片或未分片的设置 | 完全灵活，自动扫描 |

## 提示

- **先备份** — 保留你的 v4 安装直到你验证 v6 正常工作
- **使用 v6 Workflows** — 即使是部分的规划文档也能从 v6 改进的发现中受益
- **自定义后重建** — 更改 customize 文件后始终运行安装程序
