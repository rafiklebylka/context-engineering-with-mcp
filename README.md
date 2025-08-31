# 🧩 Context Engineering with MCP — Smart Enterprise-Light

Welcome to the **Smart Enterprise-Light Project Skeleton**. This repository provides a **unified Markdown-first structure** designed to work seamlessly with **MCP servers** while scaling from **solo developers → startups → enterprise teams** without ever needing to switch skeletons.

> ⚠️ **Note**: This project is still under development and testing. It is not yet complete, and the structure or files may change.

---

## 🎯 Core Principles

1. **Consistency** → One skeleton for all team sizes.
2. **No Code Mistakes** → Built-in acceptance criteria + CI pipelines.
3. **Context Engineering Compliance** → All 9 layers covered.
4. **MCP-Native Design** → Context7, TaskManager, ClearThought, SequentialThinking, MemoryBank all integrated.
5. **Progressive Disclosure** → Current decisions & milestones visible, history collapsible.
6. **Smart Templates** → BUSINESS.md scales from solo quick-capture → enterprise full model.
7. **Selective Context Loading** → Prevents context pollution and context window bloat.

---

## 📦 What You’ll Find

This seed repository starts with just **3 core files** (`README.md`, `system_prompt.md`, `project_skeleton.md`).

When you run initialization, it expands into the **full Smart Enterprise-Light skeleton**:

* **Unified project skeleton** ready for all scales (solo → enterprise).
* **Context-first structure** with CONTEXT.md referencing BUSINESS.md.
* **Task and workflow tracking** with TASKS.md + WORKFLOW\.md.
* **Decision logging** with progressive disclosure in DECISIONS.md.
* **Roadmap planning** with ROADMAP.md milestones.
* **Architecture documentation** for technical designs.
* **meta/ folder** with MCP logs, memory management, prompts, and archiving.
* **CI/CD pipelines** to prevent mistakes.
* **docs/** folder with extended documentation (usage, setup, glossary, API).

---

## 📂 Repository Structure

```
project-name/
├── README.md
├── CONTEXT.md          # Always references BUSINESS.md
├── TASKS.md            # Phased tasks with MCP tags
├── PROMPTS.md          # Role definitions + AI examples
├── WORKFLOW.md         # Sequential steps, process flows
├── DECISIONS.md        # Progressive disclosure of choices
├── ROADMAP.md          # Milestones + history collapsible
├── ARCHITECTURE.md     # Technical design (when relevant)
├── NOTES.md            # Scratchpad
├── BUSINESS.md         # Tiered template (solo → enterprise)
│
├── docs/               # Extended documentation
│   ├── INTRO.md
│   ├── SETUP.md
│   ├── USAGE.md
│   ├── API.md
│   └── GLOSSARY.md
│
├── .github/            # CI/CD pipelines & templates
│   └── workflows/
│       ├── ci-build-test.yml
│       └── release.yml
│
├── ci/                 # Local scripts
│   └── run_all_checks.sh
│
└── meta/               # Context engineering logs
    ├── CONTEXT7_LOG.md
    ├── TASKMANAGER_LOG.md
    ├── SEQUENTIAL_FLOW.md
    ├── CLEARTHOUGHT_LOG.md
    ├── MEMORYBANK_LOG.md
    ├── GLOBAL_MEMORY.md
    ├── GLOBAL_PROMPTS.md
    └── ARCHIVE/
```

## 🧑‍💻 Before You Begin (Required Knowledge)

To use this skeleton effectively, you should be comfortable with:

* **MCP servers** (Context7, TaskManager, ClearThought, SequentialThinking, MemoryBank).
* **Basic CI/CD** concepts (YAML-based workflows).
* **Project documentation discipline** (keeping logs, tasks, and context updated).

Optional but helpful:

* **Agile workflows** (scrum, kanban) for TASKS.md.
* **Basic architecture design** for ARCHITECTURE.md.

---

## ⚙️ Setup

1. **Clone this repo**

```bash
git clone https://github.com/rafiklebylka/context-engineering-with-mcp.git
cd context-engineering-with-mcp
```

2. **Install Node.js (>=18) and npm**
   [Download Node.js](https://nodejs.org) if you don’t already have it.

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
```

4. **Configure your AI assistant (e.g., Copilot, Claude Desktop, etc.)**
   Example MCP config snippet:

```json
{
  "servers": {
    "Context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"],
      "type": "stdio"
    },
    "SequentialThinking": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"],
      "type": "stdio"
    },
    "TaskManager": {
      "command": "npx",
      "args": ["-y", "@kazuph/mcp-taskmanager"],
      "type": "stdio"
    },
    "ClearThought": {
      "type": "stdio",
      "command": "node",
      "args": ["[Path]/clear-thought-mcp-server/dist/index.js"]
    },
    "MemoryBank": {
      "command": "node",
      "args": ["[Path]/memory-bank-mcp/dist/main/index.js"],
      "env": {},
      "type": "stdio"
    }
  }
}
```

---

## 🚀 Usage

### 0. Initialize a New Project

Type in your AI assistant this prompt:

```bash
initialize project
```

* If the folder is empty → you’ll be asked interactive questions.
* If the folder has `prd.md` → the PRD is parsed into CONTEXT.md, TASKS.md, ROADMAP.md.
* If the folder has multiple `.md` instructions → they’ll be parsed for context, missing info will be asked.
* If the folder already has files → you’ll be asked to reuse or overwrite.

✅ Result: A full project skeleton + docs + meta logs will be created.

> 💡 **Example Walkthrough:**
>
> * **Q:** Project name? → `ShopEasy`
> * **Q:** Short description? → `An e-commerce MVP for local shops`
> * **Q:** Team size? → `2 developers`
> * **Q:** Business context? → `Startup`
>   ✅ Generated files: `README.md`, `CONTEXT.md` (linked to BUSINESS.md), `TASKS.md`, `ROADMAP.md`, `BUSINESS.md`, plus meta logs.

### 1. Managing Tasks

Execute tasks inside MCP:

```bash
TaskManager: execute all tasks
TaskManager: run Phase 1 tasks
TaskManager: mark 'Gather requirements' as complete
```

All updates are written back into `TASKS.md`.

### 2. Adding, Editing, Fixing, Deleting

Use natural prompts — system applies **meta/GLOBAL\_PROMPTS.md**:

```bash
add user authentication feature
fix error in login route
edit README.md to add quickstart section
delete obsolete utils/logger.js
```

### 3. Advanced Examples Prompts

```bash
initialize project using prd.md
initialize project from ./requirements/instructions.md
add workflow step: integrate CI/CD with GitHub Actions
delete payment gateway integration
```

---

## 🧠 9 Context Engineering Layers — Compliance

| Layer                 | Implementation             | Evidence                                                            |
| --------------------- | -------------------------- | ------------------------------------------------------------------- |
| 1. Short-Term Memory  | Active logs                | meta/CONTEXT7\_LOG.md, ACTIVE\_CONTEXT.md                           |
| 2. Long-Term Memory   | Persistent + global memory | MEMORYBANK\_LOG.md, GLOBAL\_MEMORY.md                               |
| 3. Tool Calling       | Full MCP integration       | Context7, TaskManager, SequentialThinking, ClearThought, MemoryBank |
| 4. RAG Implementation | Selective context loading  | system\_prompt rules, CONTEXT.md references                         |
| 5. Context Isolation  | Clear separation           | meta/ folder, progressive disclosure, ARCHIVE rules                 |
| 6. Summarization      | Structured logs            | ClearThought decisions, SequentialThinking traces                   |
| 7. Deep Research      | Workflow + tasks           | WORKFLOW\.md, phased TASKS.md                                       |
| 8. Formatting         | Markdown-first             | All files standardized                                              |
| 9. Trimming           | Smart archiving            | >200 lines or >50KB → archive oldest 50%                            |

---

### 🚀 Scaling Behavior

* **Solo Devs** → Minimal BUSINESS.md quick capture, only active files needed.
* **Startups / Small Teams** → Add stakeholders, ROADMAP, DECISIONS active.
* **Enterprise Teams** → Full BUSINESS.md model, ARCHITECTURE.md, extended docs, compliance sections.



## 🏆 Best Practices

* Keep **BUSINESS.md** updated with the correct tier.
* Always link **CONTEXT.md** to business goals.
* Archive logs regularly.
* Use **progressive disclosure** to manage history.
* Run `ci/run_all_checks.sh` before commits.
* Use global prompt macros for consistent actions.

---

## ✅ Acceptance Criteria

1. All skeleton files exist.
2. README.md includes overview.
3. CONTEXT.md references BUSINESS.md.
4. TASKS.md phased with MCP tags.
5. WORKFLOW\.md ≥3 seeded steps.
6. DECISIONS.md progressive disclosure.
7. ROADMAP.md progressive disclosure.
8. BUSINESS.md tiered template.
9. docs/USAGE.md explains scaling.
10. meta/ARCHIVE/ with rules.
11. CI/CD pipelines configured.

---

## 🏆 Why Smart Enterprise-Light?

* **Solos** → Not overwhelmed, still professional.
* **Startups** → Seamless scaling.
* **Enterprises** → Ready for compliance & governance.
* **AI Agents** → Optimized context engineering.

---

## 📌 Next Steps

* Fill **CONTEXT.md → Project Initialization**.
* Complete **BUSINESS.md** quick capture.
* Track progress in **TASKS.md**.
* Log choices in **DECISIONS.md**.
* Expand naturally as project/team grows.

---

## 🤝 Contributions

⚡ **Contributions Welcome**: Improve documentation, enhance MCP integration, or propose new features. Every contribution makes this system stronger.

---

## 🎯 The Goal

This repository’s goal is to **unify context engineering best practices with MCP-native project skeletons** so developers, startups, and enterprises can work with **one structure that adapts intelligently** to their scale — eliminating mistakes, context pollution, and migration pain.

---

## 📜 License

Licensed under the **MIT License**. Free for personal and commercial use, with attribution.

---

## 🔗 References

* [System Prompt Canvas](system_prompt.md)
* [Project Skeleton Canvas](project_skeleton.md)
* [9 Layers of Context Engineering](https://www.theaiautomators.com/context-engineering-strategies-to-build-better-ai-agents/)
