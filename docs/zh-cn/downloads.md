---
title: 下载
---

下载 BMad Method 资源用于离线使用、AI 训练或集成。

## 源码包

从文档站点的 `downloads/` 文件夹下载这些文件。

| 文件 | 描述 |
| ------------------ | ------------------------------- |
| `bmad-sources.zip` | 完整的 BMad 源码文件 |
| `bmad-prompts.zip` | 仅 Agents 和 Workflows 的 Prompts |

## LLM 优化文件

这些文件是专为 AI 消费设计的 - 非常适合加载到 Claude、ChatGPT 或任何 LLM 上下文窗口中。查看下方的 [API 访问](#api-access) 获取 URL。

| 文件 | 描述 | 用例 |
| --------------- | ----------------------------------- | -------------------------- |
| `llms.txt`      | 带摘要的文档索引 | 快速概览，导航 |
| `llms-full.txt` | 连接的完整文档 | 完整上下文加载 |

### 在 LLMs 中使用

**Claude Projects:**

```
上传 llms-full.txt 作为项目知识 (Project Knowledge)
```

**ChatGPT:**

```
粘贴 llms.txt 用于导航，或根据需要粘贴 llms-full.txt 中的部分
```

**API 使用:**

```python
import requests
docs = requests.get("https://bmad-code-org.github.io/BMAD-METHOD/llms-full.txt").text
# 包含在你的 System Prompt 或 Context 中
```

## 安装选项

```bash
npx bmad-method install
```

[更多详情](/docs/zh-cn/how-to/install-bmad.md)

## 版本信息

- **当前版本:** 见 [CHANGELOG](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/CHANGELOG.md)
- **发布说明:** 可在 [GitHub Releases](https://github.com/bmad-code-org/BMAD-METHOD/releases) 上查看

## API 访问

获取 BMad 文档的编程访问：

```bash
# 获取文档索引
curl https://bmad-code-org.github.io/BMAD-METHOD/llms.txt

# 获取完整文档
curl https://bmad-code-org.github.io/BMAD-METHOD/llms-full.txt
```

## 贡献

想要改进 BMad Method？查看：

- [贡献指南](https://github.com/bmad-code-org/BMAD-METHOD/blob/main/CONTRIBUTING.md)
- [GitHub 仓库](https://github.com/bmad-code-org/BMAD-METHOD)
