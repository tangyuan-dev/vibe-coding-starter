# 08. 上下文管理

本文介绍如何在 Vibe Coding 中有效管理项目上下文。

## 什么是上下文？

上下文是 AI 理解任务所需的信息，包括：
- 项目结构
- 技术栈
- 已完成的工作
- 用户的偏好

## 为什么要管理上下文？

AI 没有"记忆"，每次对话都是独立的。
如果不提供上下文，AI 会：
- 忘记之前的修改
- 做出不一致的决定
- 生成冲突的代码

## 上下文管理技巧

### 1. 明确项目结构

❌ 不好：
```
帮我添加用户认证
```

✅ 好的：
```
在当前 Node.js + Express 项目中，添加 JWT 用户认证：
- 用户表已存在（users 表）
- 使用 bcrypt 加密密码
- 生成 JWT token
```

### 2. 提供文件路径

```markdown
修改 src/auth/login.js 文件，添加登录验证逻辑：
- 验证邮箱格式
- 验证密码强度
- 返回 JWT token
```

### 3. 列出相关文件

```markdown
需要修改的文件：
- src/models/User.js
- src/routes/auth.js
- src/middleware/auth.js

请确保修改保持一致性
```

## 最佳实践

### 1. 使用上下文文件

创建 `CLAUDE.md` 或 `CONTEXT.md`：

```markdown
# 项目上下文

## 技术栈
- Node.js 18
- Express 4
- PostgreSQL 15

## 项目结构
- src/models/ - 数据模型
- src/routes/ - 路由
- src/middleware/ - 中间件

## 约定
- 使用 async/await
- 错误返回 { error: 'message' }
- 日志使用 console.info
```

### 2. 会话开头说明项目

每次新会话：

```markdown
# 当前项目

这是一个 Node.js + Express 的博客系统，正在开发后台管理功能。
```

### 3. 重要修改做记录

```markdown
# 修改记录

## 2026-03-16
- 添加了用户认证
- 使用 JWT token
```

## 常见问题

### Q: 上下文太长怎么办？

A: 分段提供，先给核心信息

### Q: AI 忘了之前的要求怎么办？

A: 在新对话中简要回顾之前的工作

### Q: 项目很大怎么办？

A: 使用 CLAUDE.md 持续记录关键信息

## 下一步

- [09. 幻觉处理](./09-hallucination.md) — 识别和处理 AI 幻觉
