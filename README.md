<div align="center">

# TaskCaptain

### 自动推进任务直到交付的 AI captain

**把目标变成持续执行，直到交付结果。**

[English](./README-EN.md) | [中文](./README.md)

</div>

---

## TaskCaptain 是什么？

**TaskCaptain 是一层面向 Codex 的自治执行系统。**

它不是再给你一个聊天窗口，也不是给你几条建议后就结束。
它会接管任务、判断下一步、持续推动执行，并尽可能把事情一路推进到真正交付。

如果你不想一直盯着 AI 工具，不想反复催它“继续”“再试一次”“把剩下的做完”，TaskCaptain 就是为这种场景设计的。

---

## 核心定位

**TaskCaptain 是一个自动推进任务直到交付结果的 AI 执行负责人。**

更简洁一点：

- 它负责推进，不只负责回答。
- 它负责调度，不只负责建议。
- 它负责交付，不只负责生成草稿。

---

## 为什么不一样

### 1. 持续执行，不是一次性回答

TaskCaptain 不会停在“这是一个不错的思路”。
它会继续推进任务，直到有结果，或者明确失败边界。

### 2. 自动指挥 Codex

它会把任务拆开、安排下一步、驱动 Codex 分步执行，并持续管理执行流程。

### 3. 无人值守也能推进

即使你去忙别的、切换上下文、离开键盘，任务也可以继续向前跑。

---

## 工作方式

TaskCaptain 把流程拆成 3 层，而且都能看见：

- **User ↔ Agent** 对话
- **Agent ↔ Codex** 对话
- **原始执行日志**

这带来几个直接好处：

- 你能看清任务是怎么被推进的
- 你能看清 Agent 是怎么指挥 Codex 的
- 你能看清 Codex 回了什么、卡在什么地方
- 你不用在一个混杂窗口里猜测系统到底干了什么

每个任务都有独立的：
- 配置
- 状态
- 日志
- Agent Profile
- Codex 会话

---

## 适合什么场景

TaskCaptain 适合这些场景：

- 你有一个明确目标，希望 AI 持续往前推进
- 你想让 Codex 不只是“回答问题”，而是真正执行任务
- 你希望任务在后台继续跑，而不是一直人工盯着
- 你想复用一个调得很顺手的 Agent 身份
- 你想保留完整过程，便于复盘、调试、继续推进

---

## 功能

- 本地浏览器 UI
- 每个任务独立状态
- 可复用 Agent Profiles
- 自检（Self-Test）
- Start / Continue Run
- Stop Run
- 把当前 Agent 保存为可复用 Profile
- 任务中途追加新要求
- 中英双语 UI
- 对话视图与原始日志并存
- 无前端构建步骤

---

## 界面结构

TaskCaptain 的主页和任务页都强调“执行视角”，而不是“聊天视角”。

你会看到：

### 首页
- 任务列表
- Agent Profiles 列表
- 创建任务面板
- 创建 Profile 面板

### 任务详情页
- 配置详情
- User ↔ Agent 对话区
- Agent ↔ Codex 对话区
- Self-Test 结果
- Agent 日志
- Codex 日志

---

## 快速开始

### 1. 克隆仓库

```bash
git clone https://github.com/LongWeihan/taskcaptain.git
cd taskcaptain
```

### 2. 启动

```bash
./run.sh
```

打开：

```text
http://127.0.0.1:8765
```

### 3. 可选：本地配置

```bash
cp .env.example .env
set -a
source .env
set +a
./run.sh
```

---

## 常用启动方式

### 一行启动

```bash
git clone https://github.com/LongWeihan/taskcaptain.git && cd taskcaptain && chmod +x run.sh restart.sh && ./run.sh
```

### 指定 `acpx` 路径

```bash
export ACPX_BIN=/absolute/path/to/acpx
./run.sh
```

### 自定义端口 / endpoint

```bash
export PRODUCTS_UI_PORT=8877
export PRODUCTS_UI_DEFAULT_OPENAI_BASE_URL=http://127.0.0.1:8317/v1
./run.sh
```

---

## 仓库结构

```text
taskcaptain/
├── app/
│   └── server.py
├── data/
│   ├── claw-profiles/
│   ├── products/
│   └── trash/
├── docs/
│   ├── ARCHITECTURE.md
│   ├── BRAND.md
│   ├── DATA_MODEL.md
│   ├── DEPLOYMENT.md
│   └── USER_GUIDE.md
├── logs/
├── runs/
├── workspace/
├── .env.example
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── Makefile
├── README.md
├── README-EN.md
├── restart.sh
└── run.sh
```

---

## 文档

- [英文 README](./README-EN.md)
- [用户指南](./docs/USER_GUIDE.md)
- [部署说明](./docs/DEPLOYMENT.md)
- [架构说明](./docs/ARCHITECTURE.md)
- [数据模型](./docs/DATA_MODEL.md)
- [品牌文案](./docs/BRAND.md)

---

## 品牌语气

TaskCaptain 不应该像“一个聪明助手”。
它应该像“一个真正负责的人”。

推荐的品牌语气：

- **Calm**：冷静，不夸张
- **Commanding**：有掌控感，像真的在负责推进
- **Outcome-driven**：始终强调结果，不强调概念

更适合 TaskCaptain 的词：

- run
- drive
- direct
- move
- deliver
- finish
- ship
- own

不建议过度使用的词：

- magical
- revolutionary
- next-generation
- intelligent assistant
- productivity booster

---

## License

MIT
