# 11. 技术选型

本文介绍 Vibe Coding 时代如何选择合适的技术方案。

## 为什么技术选型重要？

选对技术栈可以：
- 加快开发速度
- 降低维护成本
- 提高产品稳定性

## Vibe Coding 时代的技术选型

### 1. 前端选型

| 场景 | 推荐 | 原因 |
|------|------|------|
| 快速原型 | HTML + Tailwind | 简单，AI 容易生成 |
| 复杂交互 | React/Vue | 生态成熟 |
| AI 生成 | v0 + React | 天然适配 |

### 2. 后端选型

| 场景 | 推荐 | 原因 |
|------|------|------|
| 快速原型 | Node.js + Express | 简单，AI 熟悉 |
| API 服务 | Python FastAPI | AI 相关库多 |
| 企业级 | Java Spring AI | 稳定 |

### 3. 数据库选型

| 场景 | 推荐 |
|------|------|
| 原型 | SQLite / JSON 文件 |
| 小型应用 | PostgreSQL |
| 向量数据 | pgvector |

### 4. AI 选型

| 需求 | 推荐 |
|------|------|
| 通用编程 | Claude / GPT-4 |
| 中文优化 | DeepSeek |
| 本地部署 | Ollama |
| 免费额度 | Claude Haiku / GPT-4o mini |

## 选型决策树

```
需要用户系统吗？
  │
  ├─ 是 → 需要数据库吗？
  │         │
  │         ├─ 是 → PostgreSQL
  │         │
  │         └─ 否 → 简单 JSON 存储
  │
  └─ 否 → 纯前端即可
          (HTML + JS)
```

## 常见组合

### 最小可行产品 (MVP)
```
前端：HTML + Tailwind CSS
后端：无 / Serverless
数据库：JSON 文件
AI：DeepSeek / Claude
```

### 快速上线
```
前端：Next.js + v0
后端：Next.js API Routes
数据库：Vercel Postgres
AI：OpenAI / Claude
```

### 企业级
```
前端：React + TypeScript
后端：Spring AI / Python FastAPI
数据库：PostgreSQL + pgvector
AI：按需选择
```

## 注意事项

1. **不要过度设计** — MVP 阶段够用就好
2. **优先选熟悉的** — 遇到问题容易解决
3. **考虑 AI 能力** — 选择 AI 擅长的技术

---

## 下一步

- [12. 发布与运营](./12-launch.md) — 从 0 到 1 发布产品
