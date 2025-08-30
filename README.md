# context-engineering-with-mcp

**Autonomous Project Skeleton + System Prompt**

This repository provides a **Context-Engineering–based project skeleton** and a **System Prompt Initializer** designed for use with **Model Context Protocol (MCP) servers**.

The goal: give you a **repeatable, error-free way to initialize and run any project** — with tasks, context, workflows, and decisions all logged in Markdown, and powered by autonomous agents like GitHub Copilot or other MCP-aware tools.

> ⚡ **Contributions Welcome**: It will be very helpful if you contribute by improving or fixing any part of this repository — from documentation clarity to new MCP integrations. Every improvement makes this system more powerful for everyone.

---

## 📚 What You’ll Find

* `project_skeleton.md` → Defines the Markdown-first folder/file structure (README, CONTEXT, TASKS, WORKFLOW, DECISIONS, ROADMAP, docs, meta, BUSINESS.md, etc.).
* `system_prompt.md` → Defines how to initialize new projects using MCPs, including handling PRDs, `instructions.md` folders, or any `.md` files.

Together, these files let you **bootstrap new projects in minutes**, with built-in context-engineering best practices.

---

## 🔑 Before You Begin (Required Knowledge)

1. **Understand MCP (Model Context Protocol):**

   * MCP connects AI assistants to tools, memory, and context.

2. **Know how to install MCP servers locally:**

   * MCP servers are processes you run locally (via `npx` or `node`).

3. **Basic Git & Markdown familiarity**

   * You’ll edit `.md` files as the single source of truth.

4. **Tested in VSCode with Copilot**

---

## ⚙️ Setup

1. **Clone this repo**

    ```bash
      git clone [https://github.com/rafiklebylka/context-engineering-with-mcp.git](https://github.com/rafiklebylka/context-engineering-with-mcp.git)

    ````
    ```bash
      cd context-engineering-with-mcp
    ````


2. **Install Node.js (>=18) and npm**
   * [Download Node.js](https://nodejs.org) if you don’t already have it.

3. **Install the MCP servers you want** (example set):
  ```bash
    # Context7 (context memory)
    npx -y @upstash/context7-mcp@latest

    # Sequential Thinking
    npx -y @modelcontextprotocol/server-sequential-thinking

    # Task Manager
    npx -y @kazuph/mcp-taskmanager

    # ClearThought
    git clone https://github.com/chirag127/clear-thought-mcp-server
    cd clear-thought-mcp-server && npm install && npm run build

    # Memory Bank
    git clone https://github.com/alioshr/memory-bank-mcp
    cd memory-bank-mcp && npm install && npm run build
  ````

4. **Configure your AI assistant (e.g., Copilot, Claude Desktop, etc.)**

   * Point it to the MCP config JSON where your servers are registered.
   * Example config snippet:

   ```json
    {
      "servers": {
        "Context7": {
          "command": "npx",
          "args": \["-y", "@upstash/context7-mcp\@latest"],
          "type": "stdio"
        },
        "SequentialThinking": {
          "command": "npx",
          "args": \["-y", "@modelcontextprotocol/server-sequential-thinking"],
          "type": "stdio"
        },
        "TaskManager": {
          "command": "npx",
          "args": \["-y", "@kazuph/mcp-taskmanager"],
          "type": "stdio"
        },
        "ClearThought": {
          "type": "stdio",
          "command": "node",
          "args": \["\[Path]/clear-thought-mcp-server/dist/index.js"]
        },
        "MemoryBank": {
          "command": "node",
          "args": \["\[Path]/memory-bank-mcp/dist/main/index.js"],
          "env": {},
          "type": "stdio"
        }
      }
    }
  ````

## 🚀 Usage

### 1. Initialize a New Project
Type in your AI assistant:
```bash
initialize project
````

* If the folder is empty → you’ll be asked interactive questions.
* If the folder has `prd.md` → the PRD is parsed into CONTEXT.md, TASKS.md, ROADMAP.md.
* If the folder has multiple `.md` instructions → they’ll be parsed for context, missing info will be asked.
* If the folder already has files → you’ll be asked to reuse or overwrite.

✅ Result: A full project skeleton + docs + meta logs will be created.

> 💡 **Team Size Awareness:** The initialization flow adapts:
>
> * Solo dev → Lightweight setup, fewer docs.
> * Small/medium team → Balanced skeleton with context logs.
> * Large/enterprise → Full structure with ROADMAP, DECISIONS, BUSINESS.md, and meta logs.

> 💡 **Business Awareness:** If your project has market, customer, or client considerations, a **BUSINESS.md** file will be generated to capture business goals, stakeholders, and constraints. This file will always be referenced inside **CONTEXT.md**, ensuring business goals flow directly into technical context.

> 💡 **Example Walkthrough:**
>
> * **Q:** Project name? → `ShopEasy`
> * **Q:** Short description? → `An e-commerce MVP for local shops`
> * **Q:** Team size? → `2 developers`
> * **Q:** Business context? → `Startup`
>   ✅ Generated files: `README.md`, `CONTEXT.md` (linked to BUSINESS.md), `TASKS.md`, `ROADMAP.md`, `BUSINESS.md`, plus meta logs.

---

### 2. Managing Tasks

* Execute all tasks:

```bash
TaskManager: execute all tasks
```

* Run a specific phase:

```bash
TaskManager: run Phase 1 tasks
```

* Complete a task:

```bash
TaskManager: mark 'Gather requirements' as complete
```

All updates are written back into `TASKS.md`.

---

### 3. Adding, Editing, Fixing, Deleting

Use simple prompts — the system will apply **meta/GLOBAL\_PROMPTS.md** templates automatically:

* Add feature:

```bash
add user authentication feature
```

* Fix error:

```bash
fix error in login route
```

* Edit:

```bash
edit README.md to add quickstart section
```

* Delete:

```bash
delete obsolete utils/logger.js
```

The system will update tasks, decisions, context, and docs consistently.

---

### 4. Advanced Examples

* Initialize from PRD.md only:

```bash
initialize project using prd.md
```

* Initialize from multiple docs:

```bash
initialize project from ./requirements/instructions.md
```

* Add a new workflow step:

```bash
add workflow step: integrate CI/CD with GitHub Actions
```

* Delete a feature + auto-update roadmap:

```bash
delete payment gateway integration
```

---

## 🧩 Customizing Your MCP Stack

* Edit `system_prompt.md` if you want to change the initialization flow.
* Edit `meta/PROMPT_PROFILE.md` to adjust the AI’s role/persona.
* Add or remove MCPs in your config file to match your environment.

---

## ✅ Best Practices

* Keep **all project state in Markdown files** (no hidden memory).
* Always tag tasks with `#mcp:TaskManager`.
* Always log decisions in `DECISIONS.md`.
* Use `meta/MEMORYBANK_LOG.md` for persistent knowledge.
* Use **context layering**: keep `meta/ACTIVE_CONTEXT.md` for current work, and move old logs into `meta/ARCHIVE/` when phases are completed. This prevents context pollution and ensures only relevant logs are active.
* Commit your changes often.

---

## 📜 License

MIT License — free to use, modify, and share.
