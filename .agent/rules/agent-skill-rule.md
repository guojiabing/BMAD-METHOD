---
trigger: always_on
---

# Agent Skills 编写规范 

本文档定义了 Agent Skills 的标准目录结构、文件格式和编写规范，适用于所有需要创建 Agent Skills 的场景。

## 版本信息

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| 1.0.0 | 2026-01-11 | 初始版本，定义核心规范 |

---

## 一、Skills 分类

Agent Skills 分为两大类型：

### 1.1 官方规范 Skills（自动触发）

**特征**：
- 文件名：**必须**是 `SKILL.md`（区分大小写）
- 触发方式：AI 助手根据对话内容**自动发现和触发**
- 适用场景：代码分析、审查、优化、重构等质量检查类任务
- 部署位置：`.claude/skills/` 或 `.agent/skills/`

**命名约定**：
- 目录名使用 `kebab-case`（小写连字符）
- 建议前缀：`quality-`（质量检查类）、`dify-`（项目特定）、`ui-ux-`（设计类）
- 示例：`quality-code-reviewer/`、`dify-component-refactoring/`

### 1.2 SKILL-KITS 工具包（手动引用）

**特征**：
- 文件名：`*.md`（任意名称）
- 触发方式：需要在对话中**手动引用**文件路径
- 适用场景：代码生成模板、参考指南、最佳实践文档
- 部署位置：任意位置（建议 `SKILL-KITS/` 目录）

**命名约定**：
- 文件名使用 `kebab-case`
- 建议前缀：`gen-`（生成类）、`review-`（审查类）、`refactor-`（重构类）
- 示例：`gen-api.md`、`review-code.md`、`refactor-optimize.md`

---

## 二、目录结构规范

### 2.1 官方规范 Skills 目录结构

```
{skill-name}/                    # Skill 根目录（kebab-case）
├── SKILL.md                     # 必需：Skill 定义文件（中文）
├── SKILL_en.md                  # 可选：英文版本
├── references/                  # 可选：参考文档目录
│   ├── {topic-1}.md            # 主题参考文档
│   ├── {topic-2}.md
│   └── ...
├── assets/                      # 可选：资源文件目录
│   ├── {template}.template.tsx # 模板文件
│   ├── {image}.png             # 图片资源
│   └── .gitkeep                # 保持空目录
├── data/                        # 可选：数据文件目录
│   ├── {data}.csv              # CSV 数据
│   ├── {data}.json             # JSON 数据
│   └── ...
└── scripts/                     # 可选：脚本目录
    ├── {script}.py             # Python 脚本
    ├── {script}.js             # JavaScript 脚本
    └── ...
```

**目录说明**：
- `SKILL.md`：**必需**，Skill 的核心定义文件
- `references/`：存放详细的参考文档、检查清单、模式说明等
- `assets/`：存放模板文件、图片等静态资源
- `data/`：存放 CSV、JSON 等数据文件
- `scripts/`：存放辅助脚本（如搜索、分析工具）

### 2.2 SKILL-KITS 目录结构

```
SKILL-KITS/                      # 工具包根目录
├── README.md                    # 必需：工具包说明文档
├── {category-1}/                # 分类目录（按功能分类）
│   ├── {skill-1}.md            # 技能文档
│   ├── {skill-2}.md
│   └── ...
├── {category-2}/
│   └── ...
└── ...
```

**常见分类**：
- `code-generation/`：代码生成模板
- `code-review/`：代码审查指南
- `test-generation/`：测试生成模板
- `refactoring/`：重构辅助指南
- `debugging/`：调试辅助指南

---

## 三、SKILL.md 文件格式

### 3.1 必需的 YAML 前置部分

```yaml
---
name: skill-name                 # 必需：Skill 名称（kebab-case）
description: |                   # 必需：Skill 功能描述（AI 用于判断何时触发）
  简短描述 Skill 的功能和触发场景。
  可以多行描述，但应保持简洁明确。
allowed-tools:                   # 可选：允许使用的工具列表
  - Read                         # 读取文件
  - Edit                         # 编辑文件
  - Write                        # 写入文件
  - Grep                         # 搜索文件内容
  - Glob                         # 文件模式匹配
model: inherit                   # 可选：模型配置（通常使用 inherit）
---
```

**YAML 字段说明**：

| 字段 | 必需 | 说明 |
|------|------|------|
| `name` | ✅ | Skill 唯一标识符，使用 kebab-case |
| `description` | ✅ | 功能描述，AI 根据此判断何时触发 Skill |
| `allowed-tools` | ⚠️ | 允许的工具列表，建议明确指定 |
| `model` | ❌ | 模型配置，通常使用 `inherit` |

### 3.2 Markdown 内容结构

```markdown
# Skill 标题

简短的角色描述和核心原则（1-2 段）。

## Instructions

详细的执行步骤，使用有序列表：

1. **步骤 1** - 描述第一步操作
2. **步骤 2** - 描述第二步操作
3. **步骤 3** - 描述第三步操作
...

## 核心概念/原则（可选）

说明 Skill 遵循的核心概念或原则。

## 检查维度/模式（可选）

详细说明检查的维度或使用的模式。

## 附加资源（可选）

- 参考文档链接
- 相关 Skill 链接

## Examples

### 示例 1：场景描述

\```
用户请求示例
\```

### 示例 2：场景描述

\```
用户请求示例
\```

## 输出格式（可选）

如果 Skill 需要特定的输出格式，在此说明。
```

**内容编写原则**：
- **简洁明确**：避免冗长描述，直击要点
- **结构清晰**：使用标题层级组织内容
- **可操作性**：Instructions 应该是可执行的步骤
- **示例丰富**：提供 2-3 个典型使用场景示例

---

## 四、IDE 兼容性规范

### 4.1 支持的 IDE 和路径

| IDE | 原生支持路径 | 兼容处理方法 |
|-----|-------------|-------------|
| **Cursor** | `.cursor/skills`<br>`.claude/skills`<br>`.agent/skills` | 在 `.cursorrules` 中声明路径 |
| **Claude Code 2.1+** | `.claude/skills`<br>`.agent/skills` | 在 `CLAUDE.md` 中声明路径 |
| **Antigravity** | `.agent/skills` | 在 `GEMINI.md` 中声明路径 |
| **OpenCode** | `.claude/skills`<br>`.agent/skills`<br>`.opencode/skill` | 无需额外配置 |
| **Kilo Code** | `.claude/skills`<br>`.kilocode/skills` | 在自定义指令中声明路径 |

### 4.2 最大兼容性部署

为确保最大兼容性，建议同时部署到两个目录：

```bash
# 项目级部署（团队共享）
cp -r {skill-name}/ .claude/skills/
cp -r {skill-name}/ .agent/skills/

# 个人级部署
cp -r {skill-name}/ ~/.claude/skills/
cp -r {skill-name}/ ~/.agent/skills/
```

---

## 五、编写规范

### 5.1 命名规范

**目录命名**：
- 使用 `kebab-case`（小写连字符）
- 名称应清晰表达功能
- 建议使用前缀分类：
  - `quality-*`：质量检查类
  - `dify-*`：项目特定类
  - `ui-ux-*`：设计类

**文件命名**：
- 官方规范 Skills：**必须**使用 `SKILL.md`
- 参考文档：使用 `kebab-case.md`
- 模板文件：使用 `{name}.template.{ext}`

### 5.2 Description 编写规范

`description` 是 AI 判断何时触发 Skill 的关键，应该：

✅ **好的 description**：
```yaml
description: |
  注释质量分析 Agent，检查 Go 代码中的注释质量，包括 godoc 规范、
  注释完整性、注释与代码一致性等。当用户要求检查注释、改进文档、
  分析注释质量时触发。
```

❌ **不好的 description**：
```yaml
description: 这是一个注释检查工具
```

**编写要点**：
- 明确说明功能范围
- 列出触发关键词（如"检查注释"、"改进文档"）
- 说明适用场景
- 保持简洁（2-3 句话）

### 5.3 Instructions 编写规范

Instructions 应该是**可执行的步骤**，而非抽象描述：

✅ **好的 Instructions**：
```markdown
## Instructions

1. **读取代码文件** - 使用 Glob 查找目标 Go 文件，使用 Read 读取内容
2. **检查 Godoc 规范** - 验证包注释、导出函数注释是否符合规范
3. **检查注释完整性** - 确认所有导出元素都有注释
4. **生成报告** - 输出结构化的注释质量分析报告
```

❌ **不好的 Instructions**：
```markdown
## Instructions

1. 分析代码
2. 检查问题
3. 给出建议
```

### 5.4 Examples 编写规范

每个 Skill 应提供 **2-3 个典型使用场景示例**：

```markdown
## Examples

### 示例 1：分析单个文件

\```
请分析 internal/service/user_service.go 文件的注释质量
\```

### 示例 2：分析整个目录

\```
请分析 internal/domain/ 目录下所有 Go 文件的注释质量
\```

### 示例 3：生成改进建议

\```
检查 internal/service/ 中的注释，并给出改进建议
\```
```

---

## 六、质量检查清单

创建 Skill 后，使用以下清单检查：

### 6.1 文件结构检查

- [ ] 目录名使用 `kebab-case`
- [ ] 包含 `SKILL.md` 文件（官方规范 Skills）
- [ ] YAML 前置部分格式正确
- [ ] `name` 和 `description` 字段完整
- [ ] 目录结构符合规范

### 6.2 内容质量检查

- [ ] Description 清晰描述功能和触发场景
- [ ] Instructions 是可执行的步骤
- [ ] 包含 2-3 个使用示例
- [ ] 示例覆盖典型使用场景
- [ ] 内容简洁明确，无冗余描述

### 6.3 兼容性检查

- [ ] 部署到 `.claude/skills/` 或 `.agent/skills/`
- [ ] 在 IDE 中验证 Skill 可被识别
- [ ] 测试自动触发功能（官方规范 Skills）
- [ ] 测试手动引用功能（SKILL-KITS）

---

## 七、最佳实践

### 7.1 官方规范 Skills 最佳实践

1. **专注单一职责**：每个 Skill 只做一件事，做好一件事
2. **清晰的触发条件**：在 description 中明确说明触发场景
3. **结构化输出**：使用统一的报告格式，便于阅读
4. **提供参考文档**：将详细规则放在 `references/` 目录
5. **包含示例**：提供多个典型使用场景示例

### 7.2 SKILL-KITS 最佳实践

1. **模板化**：提供完整的代码模板，减少手动编写
2. **注释详细**：在模板中添加详细注释说明
3. **分类清晰**：按功能分类组织文件
4. **易于引用**：文件路径简短清晰
5. **保持更新**：随项目规范更新模板

### 7.3 通用最佳实践

1. **版本控制**：在 README 中记录版本历史
2. **文档完整**：提供使用指南和常见问题解答
3. **团队协作**：Skills 应该是团队共享的知识资产
4. **持续改进**：根据使用反馈不断优化
5. **测试验证**：创建后充分测试各种场景

---

## 八、参考资源

### 8.1 官方文档

- [Agent Skills 使用文档](https://code.claude.com/docs/zh-CN/skills)
- [Agent Skills 最佳实践](https://platform.claude.com/docs/zh-CN/agents-and-tools/agent-skills/overview)

### 8.2 示例 Skills

**后端 Skills**：
- [`be-common-skills/quality-code-reviewer/`](../../be-common-skills/quality-code-reviewer/) - 代码审查
- [`be-common-skills/quality-comment-analyzer/`](../../be-common-skills/quality-comment-analyzer/) - 注释分析
- [`be-common-skills/SKILL-KITS/`](../../be-common-skills/SKILL-KITS/) - 代码生成模板

**前端 Skills**：
- [`fe-common-skills/dify-frontend-code-review/`](../../fe-common-skills/dify-frontend-code-review/) - 前端代码审查
- [`fe-common-skills/dify-component-refactoring/`](../../fe-common-skills/dify-component-refactoring/) - 组件重构
- [`fe-common-skills/ui-ux-pro-max/`](../../fe-common-skills/ui-ux-pro-max/) - UI/UX 设计

### 8.3 相关规范

- [项目编码规范](../guidelines/)
- [代码模板](../templates/)
- [DDD 架构规范](../languages/golang/ddd-coding-standards.md)

---

## 九、常见问题

### Q1: 官方规范 Skills 和 SKILL-KITS 如何选择？

**A**: 根据使用场景选择：
- **代码分析、审查、优化** → 使用官方规范 Skills（自动触发）
- **代码生成、模板参考** → 使用 SKILL-KITS（手动引用）

### Q2: 如何确保 Skill 被 AI 正确触发？

**A**: 关键在于 `description` 的编写：
- 明确说明功能范围
- 列出触发关键词
- 提供典型使用场景
- 测试不同的用户请求表述

### Q3: 一个 Skill 应该包含多少功能？

**A**: 遵循**单一职责原则**：
- 一个 Skill 只做一件事
- 如果功能复杂，拆分为多个 Skills
- 通过 `references/` 提供详细文档

### Q4: 如何组织复杂的 Skill？

**A**: 使用分层结构：
- `SKILL.md`：核心定义和执行流程
- `references/`：详细的检查规则、模式说明
- `assets/`：模板文件、示例代码
- `data/`：数据文件、配置文件

### Q5: 如何测试 Skill 是否正常工作？

**A**: 测试步骤：
1. 部署到 `.claude/skills/` 或 `.agent/skills/`
2. 使用 `What Skills are available?` 确认加载
3. 使用示例中的请求测试触发
4. 验证输出是否符合预期
5. 测试边界情况和错误处理

---

## 十、更新日志

| 版本 | 日期 | 更新内容 | 作者 |
|------|------|----------|------|
| 1.0.0 | 2026-01-11 | 初始版本，定义核心规范 | AIPO 小组 |

---

**维护者**: AIPO 小组 和 业务基建小组  
**最后更新**: 2026-01-11