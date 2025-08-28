# 📂 Project Skeleton (Markdown-first)

```
project-name/
│
├── README.md                  # Project overview, purpose, quickstart
├── CONTEXT.md                 # Context log (#context7, background, constraints)
├── TASKS.md                   # Task breakdown (#TaskManager friendly)
├── PROMPTS.md                 # System prompts, AI instructions, context-engineering
├── WORKFLOW.md                # Sequential thinking steps, process flows (templated)
├── DECISIONS.md               # ClearThought log: decisions & rationale (templated)
├── ROADMAP.md                 # High-level milestones & timeline
├── ARCHITECTURE.md            # If technical: system design, diagrams (placeholder)
├── NOTES.md                   # Scratchpad, ideas, references
│
├── docs/                      # Extended documentation
│   ├── INTRO.md               # Project intro and elevator pitch
│   ├── SETUP.md               # Repro steps: install, build, run, env
│   ├── USAGE.md               # How to use the project + MCP workflows (filled)
│   ├── API.md                 # If project has endpoints (examples + tests)
│   └── GLOSSARY.md            # Terms & definitions
│
├── .github/                   # GitHub configs, issue templates, CI
│   ├── ISSUE_TEMPLATE.md
│   └── workflows/
│       ├── ci-build-test.yml  # Build + lint + test pipeline
│       └── release.yml        # Release pipeline (optional)
│
├── ci/                        # Local CI helpers (scripts)
│   └── run_all_checks.sh
│
└── meta/                      # Meta control (for MCP / automation)
    ├── PROMPT_PROFILE.md      # Master prompt definition (AI role)
    ├── GLOBAL_PROMPTS.md      # Global prompts for add/edit/fix/delete workflows
    ├── CONTEXT7_LOG.md        # Context7 log, includes framework templates from prior projects
    ├── TASKMANAGER_LOG.md
    ├── SEQUENTIAL_FLOW.md
    ├── CLEARTHOUGHT_LOG.md
    ├── MEMORYBANK_LOG.md      # persistent memory entries
    └── GLOBAL_MEMORY.md       # cross-project memory (always created)
```

---

## 🔑 File Purposes (upgraded)

* **README.md** → minimal project description + badges + quickstart (install/build/run/test). Include explicit `Frameworks` block and `CI status` badge.
* **CONTEXT.md** → capture background, goals, audience, constraints, default frameworks. Include a `Project Initialization` section that records answers from the interactive init.
* **TASKS.md** → Tasks + subtasks using checkboxes. Include a `TaskManager` header with parsing hints (explicit tags like `#mcp:TaskManager priority:high`).
* **PROMPTS.md** → store system prompts, PRPs, prompt versions and `example_calls/` (inputs/outputs).
* **WORKFLOW\.md** → templated sequential steps: each step includes `Input | Action | Output | MCPs involved | Tests`.
* **DECISIONS.md** → templated decision table: `Date | Decision ID | Decision | Rationale | Author | Related Tasks | MCP:ClearThought entry`.
* **ROADMAP.md** → milestones with concrete deliverables and acceptance criteria.
* **ARCHITECTURE.md** → sections for frontend/backend/db, CI, deployment, and `build & run` matrix for supported frameworks.
* **NOTES.md** → scratchpad for ideas, links, meeting notes.
* **PROMPT\_PROFILE.md** → master prompt definition (AI role as skilled developer).
* **GLOBAL\_PROMPTS.md** → reusable macros for add/edit/fix/delete workflows.

---

## 📌 Example TASKS.md (augmented for TaskManager parsing)

```md
# TASKS

## Phase 1: Setup
- [ ] Define project scope in CONTEXT.md  #mcp:Context7
  - [ ] Gather requirements  #mcp:TaskManager priority:high
  - [ ] Identify constraints  #mcp:TaskManager priority:high
- [ ] Initialize repo skeleton  #mcp:TaskManager
- [ ] Setup MCP integrations (#TaskManager, #Context7, #MemoryBank)  #mcp:TaskManager

## Phase 2: Core Work
- [ ] Write initial PROMPTS.md  #mcp:TaskManager
  - [ ] Draft system prompts  #mcp:TaskManager
  - [ ] Add PRP examples  #mcp:TaskManager
- [ ] Map sequential steps in WORKFLOW.md  #mcp:SequentialThinking
- [ ] Draft first version of README.md  #mcp:TaskManager

## Phase 3: Expansion
- [ ] Document APIs in docs/API.md  #mcp:TaskManager
  - [ ] Define endpoints  #mcp:TaskManager
  - [ ] Add usage examples & tests  #mcp:TaskManager
- [ ] Add roadmap milestones  #mcp:TaskManager
- [ ] Log decisions in DECISIONS.md  #mcp:ClearThought
```

---

## ⚙️ WORKFLOW\.md template (prepopulated)

```md
# WORKFLOW — Sequential Steps (Template)

| Step | Input | Action | Output | MCPs Involved | Tests / Acceptance Criteria |
|------|-------|--------|--------|---------------|----------------------------|
| 1 | Project Initialization (answers) | Create skeleton files | All md files generated with placeholders | TaskManager, Context7 | Files exist; README contains project name |
| 2 | CONTEXT.md | Validate constraints & frameworks | Confirmed context | SequentialThinking, MemoryBank | CONTEXT.md contains Frameworks section |
| 3 | TASKS.md | Seed tasks & subtasks | Task list synced to TaskManager | TaskManager | Tasks appear in TaskManager UI |
| 4 | PROMPTS.md | Add base prompts | Prompt library ready | MemoryBank, ClearThought | Prompts pass static lint rules |
```

---

## ⚙️ DECISIONS.md template

```md
# DECISIONS

| Date | Decision ID | Decision | Rationale | Author | Related Tasks | ClearThought Log |
|------|-------------|----------|-----------|--------|---------------|------------------|
| YYYY-MM-DD | D-0001 | Choose QwikJS for frontend | Fast hydration + SSR needs | <name> | TASK-1 | #clearthought:entry-id |
```

---

## 📘 docs/USAGE.md (pre-filled key sections)

```
# USAGE — How to work with this project

## Quickstart
1. Read CONTEXT.md to understand goals & constraints.
2. Open TASKS.md — start claiming tasks and tagging them with `#mcp:TaskManager` if needed.
3. Run `ci/run_all_checks.sh` to verify local environment.

## MCP integration guide
- When you edit CONTEXT.md, add an entry to `meta/CONTEXT7_LOG.md` with the date and a short summary (Context7 will ingest this file). Use `#context7` tags inside headings.
- For tasks, add `#mcp:TaskManager` tags inside TASKS.md lines for automatic parsing.
- For decisions, always append a row to DECISIONS.md and add a `#clearthought` reference.
- Store persistent facts and reference materials in `meta/MEMORYBANK_LOG.md`. Use `global:` prefix for cross-project facts (if using GLOBAL_MEMORY.md).

## Code & Documentation standards
- All code must contain inline comments and a file header explaining purpose, inputs, outputs, and side-effects.
- Every module must include a minimal unit test and a build step in CI.
- Follow the code_comment_template.md for consistent commenting.

## How to initialize a new project
1. Run the Project Initializer (system prompt via Copilot or orchestrator). 
2. Provide answers to interactive questions, or allow it to parse instructions.md / prd.md if present.
3. The initializer will create the repo and pre-fill CONTEXT.md and TASKS.md with MCP tags.
```

---

## 🔁 CI & Quality (suggested files)

* `.github/workflows/ci-build-test.yml` → runs lint, typecheck (if TS), build, unit tests. Blocks merges on failure.
* `ci/run_all_checks.sh` → developer helper to run same checks locally.
* `templates/code_comment_template.md` → enforces a header for new files.

---

## ✅ Acceptance Criteria (for the initializer)

When the initializer runs, the result must satisfy all of the following:

1. All files listed in the skeleton are created.
2. `README.md` contains `<PROJECT_NAME>`, `<SHORT_DESCRIPTION>`, and `Frameworks` block.
3. `CONTEXT.md` includes the frameworks, goals, audience, and constraints collected from the interactive phase or parsed PRD.
4. `TASKS.md` contains Phase 1 tasks with `#mcp:TaskManager` tags.
5. `WORKFLOW.md` contains the templated table and at least 3 seeded steps.
6. `DECISIONS.md` contains the table header.
7. `docs/USAGE.md` is populated with the quickstart and MCP integration guide.
8. `meta/MEMORYBANK_LOG.md` exists and contains an initial entry linking to the project initialization.
9. If PRD.md exists, its contents are parsed into CONTEXT.md and ROADMAP.md automatically.
