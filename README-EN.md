<div align="center">

# TaskCaptain

### The AI captain for autonomous task delivery

**Turn goals into running execution until results are delivered.**

[English](./README-EN.md) | [中文](./README.md)

</div>

---

## What is TaskCaptain?

**TaskCaptain is an autonomous execution layer for Codex.**

It is not another chat window.
It does not stop after giving suggestions.
It takes ownership of a task, decides the next step, keeps execution moving, and pushes the work toward an actual delivered outcome.

If you do not want to babysit AI tools, repeatedly type “continue”, or manually keep work on track, TaskCaptain is built for exactly that.

---

## Core positioning

**TaskCaptain is an AI execution lead that keeps a task moving until the result is delivered.**

In simpler terms:

- It is responsible for progress, not just replies.
- It is responsible for directing work, not just suggesting ideas.
- It is responsible for delivery, not just producing a draft.

---

## Why it is different

### 1. It keeps running, not just replying

TaskCaptain does not stop at “here is a good approach”.
It keeps the task moving until there is a real result, or a clear failure boundary.

### 2. It directs Codex automatically

It breaks work down, decides the next move, directs Codex step by step, and keeps the execution flow under control.

### 3. It keeps moving without supervision

Work can keep running while you sleep, switch context, or leave the keyboard.

---

## How it works

TaskCaptain makes the execution flow visible through 3 separate layers:

- **User ↔ Agent** dialogue
- **Agent ↔ Codex** dialogue
- **raw execution logs**

That gives you a system that is easier to inspect, debug, and trust.

You can see:

- how a task is being driven forward
- how the Agent is directing Codex
- what Codex actually returns
- where the flow slows down or fails

Each task gets isolated:
- config
- state
- logs
- Agent profile
- Codex session

---

## What it is good for

TaskCaptain is a good fit when:

- you have a clear goal and want AI to keep moving toward it
- you want Codex to execute work, not just answer questions
- you want tasks to continue in the background
- you want to reuse a strong Agent identity across tasks
- you want a local workflow you can inspect and modify

---

## Features

- local browser UI
- isolated per-task state
- reusable Agent Profiles
- self-test
- start / continue run
- stop run
- save current Agent identity as reusable profile
- append new instructions mid-task
- bilingual UI (Chinese / English)
- separate dialogue views + raw logs
- no frontend build step

---

## Interface structure

TaskCaptain is designed around execution, not around chat.

### Home
- task list
- Agent Profiles list
- create task panel
- create profile panel

### Task detail page
- configuration details
- User ↔ Agent dialogue
- Agent ↔ Codex dialogue
- self-test results
- Agent log
- Codex log

---

## Quick start

### 1. Clone the repo

```bash
git clone https://github.com/LongWeihan/taskcaptain.git
cd taskcaptain
```

### 2. Start

```bash
./run.sh
```

Open:

```text
http://127.0.0.1:8765
```

### 3. Optional local config

```bash
cp .env.example .env
set -a
source .env
set +a
./run.sh
```

---

## Common launch patterns

### One-line start

```bash
git clone https://github.com/LongWeihan/taskcaptain.git && cd taskcaptain && chmod +x run.sh restart.sh && ./run.sh
```

### With explicit `acpx` path

```bash
export ACPX_BIN=/absolute/path/to/acpx
./run.sh
```

### With custom port / endpoint

```bash
export PRODUCTS_UI_PORT=8877
export PRODUCTS_UI_DEFAULT_OPENAI_BASE_URL=http://127.0.0.1:8317/v1
./run.sh
```

---

## Repository layout

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

## Docs

- [Chinese README](./README.md)
- [User Guide](./docs/USER_GUIDE.md)
- [Deployment](./docs/DEPLOYMENT.md)
- [Architecture](./docs/ARCHITECTURE.md)
- [Data Model](./docs/DATA_MODEL.md)
- [Brand Notes](./docs/BRAND.md)

---

## Brand voice

TaskCaptain should not feel like “a clever assistant”.
It should feel like “someone actually responsible for getting the work done”.

The voice should be:

- **Calm**
- **Commanding**
- **Outcome-driven**

Words it should naturally lean toward:

- run
- drive
- direct
- move
- deliver
- finish
- ship
- own

Words it should avoid overusing:

- magical
- revolutionary
- next-generation
- intelligent assistant
- productivity booster

---

## License

MIT
