# 保留英文原文的术语清单

本文档列出在翻译计算机技术文档时**必须保留英文原文**的专业术语。这些术语在中文技术社区中已被广泛接受直接使用英文。

---

## 通用编程术语

| 术语 | 说明 |
|------|------|
| API | Application Programming Interface |
| SDK | Software Development Kit |
| CLI | Command Line Interface |
| GUI | Graphical User Interface |
| IDE | Integrated Development Environment |
| JSON | JavaScript Object Notation |
| YAML | YAML Ain't Markup Language |
| XML | Extensible Markup Language |
| REST | Representational State Transfer |
| GraphQL | - |
| WebSocket | - |
| OAuth | Open Authorization |
| JWT | JSON Web Token |
| URL / URI | - |
| HTTP / HTTPS | - |
| TCP / UDP / IP | - |

---

## 版本控制 & DevOps

| 术语 | 说明 |
|------|------|
| Git | - |
| GitHub / GitLab / Bitbucket | 平台名称 |
| CI/CD | Continuous Integration / Continuous Deployment |
| Pipeline | - |
| Webhook | - |
| Pull Request (PR) | - |
| Merge Request (MR) | - |
| Commit | - |
| Branch | - |
| Tag | - |

---

## 容器 & 云原生

| 术语 | 说明 |
|------|------|
| Docker | - |
| Kubernetes (K8s) | - |
| Pod | - |
| Service | 作为 K8s 资源时保留 |
| Deployment | 作为 K8s 资源时保留 |
| ConfigMap | - |
| Secret | 作为 K8s 资源时保留 |
| Ingress | - |
| Helm | - |
| Service Mesh | - |
| Istio / Envoy / Linkerd | 产品名称 |

---

## 前端技术

| 术语 | 说明 |
|------|------|
| React / Vue / Angular | 框架名称 |
| Next.js / Nuxt.js / Vite | 框架/工具名称 |
| SSR / SSG / ISR | Server-Side Rendering 等 |
| DOM | Document Object Model |
| HTML / CSS / JavaScript | - |
| TypeScript | - |
| Webpack / Rollup / esbuild | 工具名称 |
| npm / yarn / pnpm | 包管理器 |
| Node.js / Deno / Bun | 运行时 |

---

## 后端 & 数据库

| 术语 | 说明 |
|------|------|
| SQL / NoSQL | - |
| MySQL / PostgreSQL / MongoDB | 数据库名称 |
| Redis / Memcached | - |
| ORM | Object-Relational Mapping |
| CRUD | Create, Read, Update, Delete |
| Middleware | - |
| Microservices | - |
| gRPC | - |
| RabbitMQ / Kafka | 消息队列 |

---

## AI & 机器学习

| 术语 | 说明 |
|------|------|
| LLM | Large Language Model |
| GPT / Transformer | - |
| Prompt | - |
| Token | - |
| Embedding | - |
| Fine-tuning | - |
| RAG | Retrieval-Augmented Generation |
| Agent | 作为 AI Agent 时保留 |
| TensorFlow / PyTorch | 框架名称 |

---

## 测试 & 质量

| 术语 | 说明 |
|------|------|
| Unit Test | - |
| E2E (End-to-End) | - |
| Mock | - |
| Stub | - |
| Lint / Linter | - |
| Code Review | - |
| Coverage | - |

---


## 需结合语境翻译的术语 (Context-Aware Terms)

| 术语 | 语境/含义 | 建议译法/处理方式 |
|------|-----------|-------------------|
| Architect | 作为职位/角色名称 | 架构师 (或保持英文, 如 Solution Architect) |
| | 作为动词 (to architect) | 设计、构建、规划 |
| PM | 职位 (Product Manager) | 产品经理 |
| | BMad Agent 角色 | PM Agent (或保持原样) |
| SM | 职位 (Scrum Master) | Scrum Master / 敏捷教练 |
| | BMad Agent 角色 | SM Agent (或保持原样) |
| UX Designer | 职位 | UX 设计师 / 用户体验设计师 |
| | BMad Agent 角色 | UX Designer Agent (或保持原样) |
| Contributor | 开源社区贡献者 | 贡献者 |
| Maintainer | 项目维护者 | 维护者 |
| Application | 软件应用 | 应用程序 / 应用 |
| | 申请表格/流程 | 申请 |
| Client | 网络拓扑中的客户端 | 客户端 |
| | 商业/业务中的客户 | 客户 / 委托人 |
| User | 系统使用者 | 用户 |
| Scheme | URL Scheme | 协议 / 方案 |
| Driver | 驱动程序 (硬件/软件) | 驱动 |
| | 推动因素 (Business Driver) | 驱动力 / 推动因素 |
| Native | Native App (原生应用) | 原生 |
| | Cloud Native (云原生) | 云原生 |

---

## 使用原则

1. **产品/品牌名称**：始终保留（如 Docker, Kubernetes, React）
2. **缩写词**：保留且通常大写（如 API, SDK, CI/CD）
3. **无公认中文翻译**：保留英文（如 Webhook, Middleware）
4. **中文翻译反而造成歧义**：保留英文（如 Token 可能被误译为"令牌"而丢失语境）
5. **代码中的关键字**：绝对保留（如 `async`, `await`, `const`）

---

> **注意**：此清单为常见术语参考，实际翻译中应根据上下文灵活判断。
