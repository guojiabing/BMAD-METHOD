---
title: "Quick Flow Workflows"
---

如何使用 Quick Flow 创建技术规范并执行实现。

## 选择 Workflow

| 情况 | Workflow | 命令 |
|-----------|----------|---------|
| 实现前需要文档 | Quick-Spec | `/bmad-gds-quick-spec` |
| 多种方法需评估 | Quick-Spec | `/bmad-gds-quick-spec` |
| 已有完成的 tech-spec | Quick-Dev | `/bmad-gds-quick-dev path/to/spec.md` |
| 有清晰直接的指令 | Quick-Dev | `/bmad-gds-quick-dev` |
| 构建完整游戏系统 | Full GDS | `/bmad-gds-workflow-init` |
| Epic 级功能 | Full GDS | `/bmad-gds-workflow-init` |

---

## 如何创建技术规范 (Quick-Spec)

### 步骤 1: 启动 Workflow

```bash
/bmad-gds-quick-spec
```

### 步骤 2: 描述你的需求

提供你的功能请求。Agent 扫描代码库并提出澄清问题。

**检查点选项:**
- `[a]` 高级启发 (Advanced Elicitation) - 更深入探索需求
- `[c]` 继续调查
- `[p]` 派对模式 (Party Mode) - 咨询专家 Agents

### 步骤 3: 审查调查发现

Agent 分析代码库的模式、约束和类似实现。审查发现。

**检查点选项:**
- `[c]` 继续生成规范
- `[p]` 派对模式 (Party Mode) - 获取技术审查

### 步骤 4: 审查生成的规范

Agent 创建带有文件路径和验收标准的有序任务列表。验证完整性。

**检查点选项:**
- `[c]` 继续进行最终审查
- `[p]` 派对模式 (Party Mode) - 技术审查

### 步骤 5: 完成

确认规范符合这些标准：
- 每个任务都有文件路径和具体操作
- 任务按依赖关系排序
- 验收标准采用 Given/When/Then 格式
- 没有占位符或 TBD 章节

**选项:**
- `[d]` 立即开始 Quick-Dev
- `[done]` 保存规范并退出

**输出:** `{planning_artifacts}/tech-spec-{slug}.md`

---

## 如何执行实现 (Quick-Dev)

### 使用 Tech-Spec

```bash
/bmad-gds-quick-dev path/to/tech-spec-feature.md
```

Agent 将：
1. 捕获基线 git commit
2. 加载并验证规范
3. 按顺序执行任务
4. 运行自检
5. 执行对抗性审查
6. 解决发现的问题
7. 根据验收标准进行验证

### 使用直接指令

```bash
/bmad-gds-quick-dev
```

然后描述你想实现什么：
1. 捕获基线 git commit
2. 评估复杂性（可能会建议规划）
3. 从代码库收集上下文
4. 执行实现
5. 运行自检和对抗性审查
6. 解决发现的问题

**升级 (Escalation):** 如果 Agent 检测到复杂性（多个组件，系统级范围，不确定性），它会提供：
- `[t]` 先创建 tech-spec
- `[w]` 使用完整的 GDS Workflow
- `[e]` 无论如何都执行

---

## 故障排除

### 规范有占位符或 TBD 章节

返回调查步骤。完成缺失的研究，内联所有发现，重新运行审查。

### Workflow 中途丢失上下文

检查 Frontmatter 的 `stepsCompleted`。从最后完成的步骤恢复。

### Agent 建议规划但你想执行

你可以用 `[e]` 覆盖，但要记录你的假设。升级启发式的存在是因为规划可以节省复杂任务的时间。

### 实现后测试失败

返回“解决发现”步骤。审查失败，修复问题，确保测试预期正确，重新运行完整套件。

### 需要帮助

```bash
/bmad-help
```

---

## 参考

### 文件位置

| 文件 | 位置 |
|------|----------|
| 进行中 (WIP) | `{implementation_artifacts}/tech-spec-wip.md` |
| 已完成规范 | `{planning_artifacts}/tech-spec-{slug}.md` |
| 已归档规范 | `{implementation_artifacts}/tech-spec-{slug}-archived-{date}.md` |
| Workflow 文件 | `_bmad/gds/workflows/gds-quick-flow/` |

### 验证标准

**自检 (对抗性审查前):**
- 所有任务/指令已完成
- 测试已编写并通过
- 遵循现有模式
- 无明显 Bugs
- 满足验收标准
- 代码可读

**对抗性审查:**
- 正确性
- 安全性
- 性能
- 可维护性
- 测试覆盖率
- 错误处理
