# 05. API 开发

学习设计和实现后端 API 服务。

## 什么是 API？

API（Application Programming Interface）是前后端通信的桥梁。

```
用户 → 前端 → API → 数据库
       ←    ←
```

## RESTful API 设计

### 常用 HTTP 方法

| 方法 | 用途 | 示例 |
|------|------|------|
| GET | 获取资源 | GET /users |
| POST | 创建资源 | POST /users |
| PUT | 更新资源 | PUT /users/1 |
| DELETE | 删除资源 | DELETE /users/1 |

### URL 命名规范

```
# 资源命名
GET /tasks          # 获取任务列表
POST /tasks          # 创建任务
GET /tasks/1         # 获取单个任务
PUT /tasks/1         # 更新任务
DELETE /tasks/1       # 删除任务

# 复数形式
/users, /products, /orders
```

## 使用 AI 开发 API

### 创建 API 框架

```
使用 Node.js + Express 创建一个 RESTful API：

1. 用户管理 API（CRUD）
2. 任务管理 API（CRUD）

数据库使用 SQLite，文件名为 database.db
```

### 添加认证

```
在现有 API 基础上添加 JWT 认证：
1. 注册接口 POST /auth/register
2. 登录接口 POST /auth/login
3. 中间件验证 token
```

### 添加分页和搜索

```
为用户列表添加：
1. 分页 ?page=1&limit=10
2. 搜索 ?search=关键词
3. 排序 ?sort=createdAt&order=desc
```

## 常见后端框架

| 框架 | 语言 | 特点 |
|------|------|------|
| Express | Node.js | 简单灵活 |
| FastAPI | Python | 自动文档 |
| Gin | Go | 高性能 |
| Spring Boot | Java | 企业级 |

## Vibe Coding 技巧

### 让 AI 生成完整 API

```
创建一个用户管理 API，包含：

用户模型：
- id (自增)
- username (字符串，必填)
- email (邮箱，唯一)
- password (加密存储)
- created_at

API 端点：
- GET /api/users - 列表（分页、搜索）
- GET /api/users/:id - 详情
- POST /api/users - 创建
- PUT /api/users/:id - 更新
- DELETE /api/users/:id - 删除

使用 Node.js + Express + SQLite
```

### 测试 API

```
帮我用 curl 测试这些 API：
1. 创建用户
2. 获取用户列表
3. 更新用户
4. 删除用户
```

---

## 下一步

- [06. 数据处理](./06-data.md) - AI 数据分析
- [04. Web 应用开发](./04-webapp.md) - 返回前端开发