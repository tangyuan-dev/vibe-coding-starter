# 03. 第一个 Vibe Coding 项目

手把手教你用 AI 完成第一个项目：一个待办事项应用。

## 项目目标

创建一个功能完整的待办事项应用，包含：
- 添加任务
- 标记完成
- 删除任务
- 本地存储

## 工具准备

本教程使用 **OpenClaw** + **Cursor** 组合：

```bash
# 1. 安装 OpenClaw
npm install -g openclaw

# 2. 初始化
openclaw init

# 3. 启动
openclaw start
```

## 步骤 1：创建项目

**用 OpenClaw：**

```
"帮我创建一个 todo-app 文件夹，里面有一个 index.html，实现待办事项应用"
```

OpenClaw 会帮你：
- 创建目录结构
- 生成 HTML + CSS + JS
- 实现基本功能

## 步骤 2：优化功能

**继续对话：**

```
"添加本地存储功能，刷新页面后数据不丢失"
```

```
"添加暗黑模式切换按钮"
```

```
"添加批量删除已完成任务的功能"
```

## 步骤 3：完善代码

**用 Cursor 打开项目：**

```bash
cd todo-app
cursor .
```

让 Cursor 帮你：
- 添加输入验证
- 优化 UI 动画
- 修复潜在 bug

## 最终代码

### HTML

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>待办事项</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h1>📝 待办事项</h1>
    <div class="input-group">
      <input type="text" id="todoInput" placeholder="添加新任务...">
      <button id="addBtn">添加</button>
    </div>
    <ul id="todoList"></ul>
    <div class="stats">
      <span id="remaining">0</span> 项待完成
      <button id="clearCompleted">清除已完成</button>
    </div>
  </div>
  <script src="app.js"></script>
</body>
</html>
```

### JavaScript (app.js)

```javascript
// 获取 DOM 元素
const input = document.getElementById('todoInput');
const addBtn = document.getElementById('addBtn');
const list = document.getElementById('todoList');
const remaining = document.getElementById('remaining');
const clearBtn = document.getElementById('clearCompleted');

// 初始化
let todos = JSON.parse(localStorage.getItem('todos')) || [];
render();

// 添加任务
addBtn.addEventListener('click', () => {
  const text = input.value.trim();
  if (!text) return;
  
  todos.push({ text, done: false });
  save();
  render();
  input.value = '';
});

// 渲染列表
function render() {
  list.innerHTML = todos.map((todo, i) => `
    <li class="${todo.done ? 'done' : ''}">
      <input type="checkbox" ${todo.done ? 'checked' : ''} 
             onchange="toggle(${i})">
      <span>${todo.text}</span>
      <button onclick="remove(${i})">×</button>
    </li>
  `).join('');
  
  remaining.textContent = todos.filter(t => !t.done).length;
}

// 切换状态
function toggle(index) {
  todos[index].done = !todos[index].done;
  save();
  render();
}

// 删除任务
function remove(index) {
  todos.splice(index, 1);
  save();
  render();
}

// 清除已完成
clearBtn.addEventListener('click', () => {
  todos = todos.filter(t => !t.done);
  save();
  render();
});

// 本地存储
function save() {
  localStorage.setItem('todos', JSON.stringify(todos));
}
```

## 运行效果

```
📝 待办事项
[_______________] [添加]

☐ 买牛奶
☐ 写代码
☐ 健身

2 项待完成 [清除已完成]
```

## 下一步

- [04. Web 应用开发](./04-webapp.md) — 进阶 Web 开发
- [05. API 开发](./05-api.md) — 后端 API 开发
