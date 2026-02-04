---
title: "文档分片指南 (Document Sharding Guide)"
---

使用 `shard-doc` 工具将大型 Markdown 文件拆分为更小的、有组织的文件，以便更好地管理上下文。

## 何时使用

- 非常大且复杂的 PRD
- 具有多个系统层的架构文档
- 包含 4+ Epics 的 Epic 文件 (特别是对于 Phase 4)
- 覆盖多个子系统的 UX 设计规范

## 什么是文档分片？

文档分片根据 2 级标题 (`## Heading`) 将大型 Markdown 文件拆分为更小的、有组织的文件。这实现了：

- **选择性加载** - Workflow 仅加载它们需要的部分
- **减少 Token 使用** - 大型项目的巨大效率提升
- **更好的组织** - 基于逻辑章节的文件结构
- **保持上下文** - 索引文件保留文档结构

### 架构

```
分片前:
docs/
└── PRD.md (巨大的 50k token 文件)

分片后:
docs/
└── prd/
    ├── index.md                    # 带描述的目录
    ├── overview.md                 # 第 1 节
    ├── user-requirements.md        # 第 2 节
    ├── technical-requirements.md   # 第 3 节
    └── ...                         # 额外章节
```

## 步骤

### 1. 运行 Shard-Doc 工具

```bash
/bmad:core:tools:shard-doc
```

### 2. 跟随交互式过程

```
Agent: Which document would you like to shard?
User: docs/PRD.md

Agent: Default destination: docs/prd/
       Accept default? [y/n]
User: y

Agent: Sharding PRD.md...
       ✓ Created 12 section files
       ✓ Generated index.md
       ✓ Complete!
```

## 你会得到什么

**index.md 结构:**

```markdown

## Sections

1. [Overview](/docs/zh-cn/how-to/overview.md) - Project vision and objectives
2. [User Requirements](/docs/zh-cn/how-to/user-requirements.md) - Feature specifications
3. [Epic 1: Authentication](/docs/zh-cn/how-to/epic-1-authentication.md) - User auth system
4. [Epic 2: Dashboard](/docs/zh-cn/how-to/epic-2-dashboard.md) - Main dashboard UI
   ...
```

**单独的章节文件:**

- 根据标题文本命名 (kebab-case)
- 包含完整的章节内容
- 保留所有 Markdown 格式
- 可独立阅读

## Workflow 发现如何工作

BMad Workflows 使用 **双重发现系统**:

1. **先尝试整个文档** - 寻找 `document-name.md`
2. **检查分片版本** - 寻找 `document-name/index.md`
3. **优先级规则** - 如果两者都存在，整个文档优先 - 如果你想使用分片的，请删除整个文档

## Workflow 支持

所有 BMM Workflows 支持两种格式：

- 整个文档
- 分片文档
- 自动检测
- 对用户透明
