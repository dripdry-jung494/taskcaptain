<div align="center">

# TaskCaptain

**Turn goals into running execution until results are delivered.**

TaskCaptain is a local execution console for Codex-driven work.
It separates **User ↔ Agent**, **Agent ↔ Codex**, and **execution logs** into distinct surfaces so task progress remains visible, controllable, and inspectable.

[中文](./README.md) · [User Guide](./docs/USER_GUIDE.md) · [Deployment](./docs/DEPLOYMENT.md)

</div>

![TaskCaptain hero](./hero.png)

---

## Overview

TaskCaptain is not a generic chat interface.

Its purpose is to **take over task supervision, keep Codex moving, and preserve state, dialogue, and logs inside a local workspace that can actually be inspected.**

For work that needs continuous execution, iterative refinement, and mid-run requirement changes, TaskCaptain provides an execution-oriented control surface rather than a one-shot answer box.

---

## Core capabilities

### Continuous execution instead of one-shot replies

TaskCaptain treats work as an ongoing execution flow, not as a single conversational response.

### Clear separation between Agent and Codex

- **Agent**: understands the goal, plans next steps, supervises progress, and folds in new requirements
- **Codex**: executes implementation work inside the task workspace, produces deliverables, and returns execution output

### Inspectable end to end

The interface preserves three categories of information:

- **User ↔ Agent** control dialogue
- **Agent ↔ Codex** execution dialogue
- **raw logs**

That makes it easier to understand why a task continued, why it failed, and where execution became blocked.

### Local-first and disk-backed

Each task keeps isolated:

- config
- state
- logs
- Agent profile
- Codex session

State is persisted on disk so the system remains inspectable, portable, and recoverable.

---

## Good fit for

TaskCaptain is well suited when you need:

- AI to keep moving instead of only answering
- background execution for development or automation work
- a full record for debugging, review, or continuation
- reusable Agent identities across tasks
- a Codex workspace with clear separation between supervision and execution

---

## Product structure

### Home page

The home page provides:

- task list
- Agent Profiles list
- task creation form
- reusable Profile creation form
- bulk deletion for non-running tasks

### Task detail page

Each task page provides:

- configuration details
- User ↔ Agent dialogue
- Agent ↔ Codex dialogue
- self-test results
- Agent log
- Codex log

### Reusable Agent Profiles

Profiles store the default identity and behavioral settings of the supervisory Agent, including:

- model
- thinking
- soul
- skills
- description

Tasks can inherit a profile and override selected fields locally.

---

## Main features

- local browser UI
- isolated per-task state and logs
- reusable Agent Profiles
- self-test
- Start / Continue Run
- Stop Run
- append new instructions mid-run
- save current Agent as reusable profile
- bilingual UI (Chinese / English)
- no frontend build step

---

## Quick start

### 1. Clone the repository

```bash
git clone https://github.com/LongWeihan/taskcaptain.git
cd taskcaptain
```

### 2. Start the service

```bash
chmod +x run.sh restart.sh
./run.sh
```

Default address:

```text
http://127.0.0.1:8765
```

### 3. Optional: load local environment config

```bash
cp .env.example .env
set -a
source .env
set +a
./run.sh
```

---

## Requirements

- Linux / WSL2 recommended
- Python 3.10+
- `bash`
- `ss`
- `acpx` installed, or provided via `ACPX_BIN`

---

## Configuration

TaskCaptain supports environment-variable based startup configuration.

### Common environment variables

```bash
export PRODUCTS_UI_HOST=127.0.0.1
export PRODUCTS_UI_PORT=8765
export PRODUCTS_UI_DEFAULT_LANG=en
export PRODUCTS_UI_DEFAULT_OPENAI_BASE_URL=http://127.0.0.1:8317/v1
export PRODUCTS_UI_DEFAULT_PRODUCT_FOLDER="$PWD/workspace"
export PRODUCTS_UI_PROXY=
export PRODUCTS_UI_NO_PROXY=127.0.0.1,localhost,::1
export ACPX_BIN=/absolute/path/to/acpx
```

### Example

```bash
export PRODUCTS_UI_PORT=8877
export PRODUCTS_UI_DEFAULT_OPENAI_BASE_URL=http://127.0.0.1:8317/v1
./run.sh
```

For deployment notes, see [docs/DEPLOYMENT.md](./docs/DEPLOYMENT.md).

---

## Runtime behavior

### `run.sh`

- starts TaskCaptain in the background when the port is free
- exits cleanly with the current address and log path when the service is already running

### `restart.sh`

- stops the current TaskCaptain process on the configured port
- waits for port release
- force-kills lingering processes when needed
- clears the server log and starts again

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
├── SECURITY.md
├── hero.png
├── restart.sh
└── run.sh
```

---

## Documentation

- [Chinese README](./README.md)
- [User Guide](./docs/USER_GUIDE.md)
- [Deployment](./docs/DEPLOYMENT.md)
- [Architecture](./docs/ARCHITECTURE.md)
- [Data Model](./docs/DATA_MODEL.md)
- [Contributing](./CONTRIBUTING.md)
- [Security Policy](./SECURITY.md)

---

## Security notes

TaskCaptain is currently intended for **trusted local environments**.

The repository does not currently provide:

- multi-user authentication
- permission separation
- public-facing access control

If you need remote access, deploy it behind a reverse proxy and add at minimum:

- authentication
- HTTPS
- IP restrictions
- least-privilege runtime practices

See [SECURITY.md](./SECURITY.md) for guidance.

---

## Open source and project policy

- License: [MIT](./LICENSE)
- Contributing: [CONTRIBUTING.md](./CONTRIBUTING.md)
- Security: [SECURITY.md](./SECURITY.md)

---

## License

This project is released under the [MIT License](./LICENSE).
