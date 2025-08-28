# context-engineering-with-mcp

**Autonomous Project Skeleton + System Prompt**

This repository provides a **Context-Engineering–based project skeleton** and a **System Prompt Initializer** designed for use with **Model Context Protocol (MCP) servers**.

The goal: give you a **repeatable, error-free way to initialize and run any project** — with tasks, context, workflows, and decisions all logged in Markdown, and powered by autonomous agents like GitHub Copilot or other MCP-aware tools.

---

## 📚 What You'll Find

1. **project_skeleton.md** → Defines the Markdown-first folder/file structure (README, CONTEXT, TASKS, WORKFLOW, DECISIONS, ROADMAP, docs, meta, etc.).
2. **system_prompt.md** → Defines how to initialize new projects using MCPs, including handling PRDs, instructions.md folders, or any .md files.

Together, these files let you bootstrap new projects in minutes, with built-in context-engineering best practices.

## 🏗️ Project Skeleton Deep Dive

The project_skeleton.md defines a comprehensive 23-file structure that turns any empty folder into a fully-organized, MCP-ready project:

1. **Core Files (Root Level)**
   ```bash
   README.md - Project overview with badges, quickstart, and framework declarations
   CONTEXT.md - Background, goals, constraints, and project initialization log
   TASKS.md - Task breakdown with MCP tags (#mcp:TaskManager priority:high)
   WORKFLOW.md - Sequential steps template with Input/Action/Output/MCPs/Tests columns
   DECISIONS.md - Decision log with rationale and ClearThought references
   ROADMAP.md - Milestones with concrete deliverables and acceptance criteria
   ```

2. **Documentation Folder (docs/)**
   ```bash
   SETUP.md - Complete reproduction steps (install, build, run, environment)
   USAGE.md - How to use the project + MCP workflow integration guides
   API.md - Endpoints with examples and tests (if applicable)
   GLOSSARY.md - Terms and definitions
   ```

3. **Meta Control Folder (meta/)**
   ```bash
   PROMPT_PROFILE.md - Master AI role definition for the project
   GLOBAL_PROMPTS.md - Reusable templates for add/edit/fix/delete operations
   CONTEXT7_LOG.md - Context memory entries and framework templates
   TASKMANAGER_LOG.md - Task execution history and status tracking
   MEMORYBANK_LOG.md - Persistent facts and cross-project knowledge
   ```

4. **Quality Assurance**
   * CI workflows - GitHub Actions for build/test/lint pipelines
   * Template enforcement - Code comment standards and file headers
   * MCP integration points - Explicit tags and parsing hints throughout

The skeleton ensures every generated project is buildable, testable, and fully documented from day one.

## 🤖 System Prompt Architecture
The system_prompt.md creates an autonomous project architect that handles multiple initialization scenarios:

1. **Intelligent Context Detection**
   * Empty folder → Full interactive Q&A (name, frameworks, constraints, audience)
   * PRD.md present → Auto-parse goals, features, milestones into CONTEXT/TASKS/ROADMAP
   * Multiple instructions.md → Parse all docs, ask only for missing details
   * Existing project → Offer to reuse files or start fresh

2. **MCP Integration Workflow**
   * Context7 → Maintains global context and framework knowledge
   * TaskManager → Handles task creation, priorities, and status updates
   * SequentialThinking → Maps dependencies and execution order
   * ClearThought → Logs decisions with rationale and alternatives
   * MemoryBank → Persists important facts across sessions

3. **Built-in Quality Gates**
   * Acceptance criteria → 10-point checklist ensures complete initialization
   * Template consistency → Uses meta/GLOBAL_PROMPTS.md for all operations
   * Error prevention → Files must be buildable, testable, with inline documentation
   * Traceability → Every action logs to appropriate MCP server

4. **Universal Command Interface**
   Once initialized, the system responds to natural language:
   * add user authentication → Creates feature + updates tasks/decisions/roadmap
   * fix login error → Applies debugging template + logs resolution
   * edit README quickstart → Updates docs + syncs related files
   * delete payment gateway → Removes feature + cleans up dependencies

The prompt transforms any AI assistant into a context-aware project manager that maintains consistency across all files and decisions.


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
   git clone https://github.com/rafiklebylka/context-engineering-with-mcp.git
   cd context-engineering-with-mcp
   ```

2. **Install Node.js (>=18) and npm**

   * [Download Node.js](https://nodejs.org) if you don’t already have it.

3. **Install the MCP servers you want** :

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
   ```

4. **Configure your AI assistant (e.g., Copilot, Claude Desktop, etc.)**

   * Point it to the MCP config JSON where your servers are registered.
   * Example config snippet:

     ```json
     {
       "servers": {
         "Context7": {
             "command": "npx",
             "args": [
                 "-y",
                 "@upstash/context7-mcp@latest"
             ],
             "type": "stdio"
         },
         "SequentialThinking": {
             "command": "npx",
             "args": [
                 "-y",
                 "@modelcontextprotocol/server-sequential-thinking"
             ],
             "type": "stdio"
         },
         "TaskManager": {
             "command": "npx",
             "args": [
                 "-y",
                 "@kazuph/mcp-taskmanager"
             ],
             "type": "stdio"
         },
         "ClearThought": {
             "type": "stdio",
             "command": "node",
             "args": [
                 "[PATH]/clear-thought-mcp-server/dist/index.js"
             ]
         },
         "MemoryBank": {
             "command": "node",
             "args": [
                 "[PATH]/memory-bank-mcp/dist/main/index.js"
             ],
             "env": {},
             "type": "stdio"
         },
       }
     }
     ```

---

## 🚀 Usage

### 1. Initialize a New Project

Type in your AI assistant:

```
initialize project
```

* If the folder is empty → you’ll be asked interactive questions.
* If the folder has `prd.md` → the PRD is parsed into CONTEXT.md, TASKS.md, ROADMAP.md.
* If the folder has multiple `.md` instructions → they’ll be parsed for context, missing info will be asked.
* If the folder already has files → you’ll be asked to reuse or overwrite.

✅ Result: A full project skeleton + docs + meta logs will be created.

---

### 2. Managing Tasks

* Execute all tasks:

  ```
  TaskManager: execute all tasks
  ```
* Run a specific phase:

  ```
  TaskManager: run Phase 1 tasks
  ```
* Complete a task:

  ```
  TaskManager: mark 'Gather requirements' as complete
  ```

All updates are written back into `TASKS.md`.

---

### 3. Adding, Editing, Fixing, Deleting

Use simple prompts — the system will apply **meta/GLOBAL\_PROMPTS.md** templates automatically:

* Add feature:

  ```
  add user authentication feature
  ```
* Fix error:

  ```
  fix error in login route
  ```
* Edit:

  ```
  edit README.md to add quickstart section
  ```
* Delete:

  ```
  delete obsolete utils/logger.js
  ```

The system will update tasks, decisions, context, and docs consistently.

---

### 4. Advanced Examples

* Initialize from PRD.md only:

  ```
  initialize project using prd.md
  ```
* Initialize from multiple docs:

  ```
  initialize project from ./requirements/instructions.md
  ```
* Add a new workflow step:

  ```
  add workflow step: integrate CI/CD with GitHub Actions
  ```
* Delete a feature + auto-update roadmap:

  ```
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
* Commit your changes often.

---

## 📜 License

MIT License — free to use, modify, and share.
