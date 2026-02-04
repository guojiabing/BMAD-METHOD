---
title: "BMad Method 自定义指南"
---

根据你的需求自定义 BMad Method 及其核心，同时仍能获取更新和增强，是 BMad 生态系统中的一个关键理念。

这里概述的自定义指南虽然针对理解 BMad Method 自定义，但也适用于 BMad Method 中的任何其他模块使用。

## 自定义类型

自定义包括 Agent 自定义、Workflow/Skill 自定义，以及添加供现有 Agents 使用的新 MCPs 或 Skills。除此之外，另一个完全不同的自定义领域涉及创建/添加你自己相关的 BMad Builder Workflows、Skills、Agents，甚至可能是你自己的用以补充 BMad Method 模块的全新模块。

警告：按照本指南规定的方式进行自定义，将允许你继续获取更新，而无需担心丢失你的自定义更改。通过随着 BMad 模块的发展继续获取更新，你将能够随着系统的改进而不断进化。

## Agent 自定义

### Agent 自定义领域

- 更改 Agent 名称、角色 (Persona) 或说话方式
- 添加项目特定的记忆 (Memories) 或上下文
- 向自定义或内联 Prompts、Skills 或自定义 BMad Workflows 添加自定义菜单项
- 定义 Agent 启动时发生的关键操作 (Critical Actions) 以保持行为一致

## 如何自定义 Agent

**1. 定位自定义文件**

安装后，在以下位置找到 Agent 自定义文件：

```
_bmad/_config/agents/
├── core-bmad-master.customize.yaml
├── bmm-dev.customize.yaml
├── bmm-pm.customize.yaml
└── ... (每个安装的 Agent 一个文件)
```

**2. 编辑任何 Agent**

打开你想修改的 Agent 的 `.customize.yaml` 文件。所有部分都是可选的 - 仅自定义你需要的部分。

**3. 重建 Agent**

编辑后，**至关重要**的是重建 Agent 以应用更改：

```bash
npx bmad-method install
```

然后你可以：

- 选择 `Quick Update` - 这还将确保所有包都是最新的，并编译所有 Agents 以包含任何更新或自定义
- 选择 `Rebuild Agents` - 这将仅重建并应用自定义到 Agents，而不拉取最新内容

Beta 发布后不久将会有额外的工具，允许安装单个 Agents、Workflows、Skills 和模块，而无需使用完整的 BMad 安装程序。

### 可以自定义哪些 Agent 属性？

#### Agent 名称

更改 Agent 如何介绍自己：

```yaml
agent:
  metadata:
    name: 'Spongebob' # 默认: "Amelia"
```

#### 角色 (Persona)

替换 Agent 的个性、角色和沟通风格：

```yaml
persona:
  role: 'Senior Full-Stack Engineer'
  identity: 'Lives in a pineapple (under the sea)'
  communication_style: 'Spongebob annoying'
  principles:
    - 'Never Nester, Spongebob Devs hate nesting more than 2 levels deep'
    - 'Favor composition over inheritance'
```

**注意：** Persona 部分会替换整个默认角色（不会合并）。

#### 记忆 (Memories)

添加 Agent 永远记住的持久上下文：

```yaml
memories:
  - 'Works at Krusty Krab'
  - 'Favorite Celebrity: David Hasslehoff'
  - 'Learned in Epic 1 that its not cool to just pretend that tests have passed'
```

### 自定义菜单项

你在这里添加的任何自定义项都将包含在 Agents 显示菜单中。

```yaml
menu:
  - trigger: my-workflow
    workflow: '{project-root}/my-custom/workflows/my-workflow.yaml'
    description: My custom workflow
  - trigger: deploy
    action: '#deploy-prompt'
    description: Deploy to production
```

### 关键操作 (Critical Actions)

添加在 Agent 启动前执行的指令：

```yaml
critical_actions:
  - 'Check the CI Pipelines with the XYZ Skill and alert user on wake if anything is urgently needing attention'
```

### 自定义 Prompts

为 `action="#id"` 菜单处理程序定义可重用的 Prompts：

```yaml
prompts:
  - id: deploy-prompt
    content: |
      Deploy the current branch to production:
      1. Run all tests
      2. Build the project
      3. Execute deployment script
```

## 故障排除

**更改没出现？**

- 确保你在编辑后运行了 `npx bmad-method build <agent-name>`
- 检查 YAML 语法是否有效（缩进很重要！）
- 验证 Agent 名称与文件名模式匹配

**Agent 没加载？**

- 检查 YAML 语法错误
- 如果你取消了注释，确保必需字段没有留空
- 尝试恢复到模板并重建

**需要重置？**

- 从 `.customize.yaml` 文件中删除内容（或删除文件）
- 运行 `npx bmad-method build <agent-name>` 以重新生成默认值

## Workflow 自定义

关于自定义现有 BMad Method Workflows 和 Skills 的信息即将推出。

## 模块自定义

关于如何构建增强 BMad 的扩展模块，或进行其他现有模块自定义的信息即将推出。
