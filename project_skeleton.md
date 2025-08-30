# 📂 Project Skeleton (Markdown-first)

```
project-name/
│
├── README.md                  # Project overview, purpose, quickstart
├── CONTEXT.md                 # Context log (#context7, background, constraints, links to BUSINESS.md)
├── TASKS.md                   # Task breakdown (#TaskManager friendly, phased)
├── PROMPTS.md                 # System prompts, AI instructions, context-engineering
├── WORKFLOW.md                # Sequential thinking steps, process flows (templated)
├── DECISIONS.md               # ClearThought log: decisions & rationale (templated)
├── ROADMAP.md                 # High-level milestones & timeline
├── ARCHITECTURE.md            # If technical: system design, diagrams (placeholder)
├── NOTES.md                   # Scratchpad, ideas, references
├── BUSINESS.md                # Business context (model, market, stakeholders, linked in CONTEXT.md)
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
├── templates/                 # Reusable templates & forms
│   ├── code_comment_template.md
│   └── pull_request_template.md
│
└── meta/                      # Meta control (for MCP / automation)
    ├── CONTEXT7_LOG.md        # Active context (working memory)
    ├── TASKMANAGER_LOG.md     # Task execution history
    ├── SEQUENTIAL_FLOW.md     # SequentialThinking traces
    ├── CLEARTHOUGHT_LOG.md    # Decision traces
    ├── MEMORYBANK_LOG.md      # Persistent memory entries (long-term)
    ├── GLOBAL_MEMORY.md       # Optional: cross-project memory (boilerplate)
    ├── GLOBAL_PROMPTS.md      # Templates for add/edit/fix/delete operations
    └── ARCHIVE/               # Reference-only logs (archive rules to prevent context overload)
```

---

## 🔑 File Purposes (cleaned & upgraded)

* **README.md** → Project description + badges + quickstart (install/build/run/test). Include `Frameworks` block and `CI status` badge. Adapt content based on team size.
* **CONTEXT.md** → Background, goals, audience, constraints, frameworks. Includes `Project Initialization` answers. Must include a **section linking key business insights from BUSINESS.md** to technical constraints.
* **TASKS.md** → Tasks + subtasks with checkboxes. Use MCP tags (e.g., `#mcp:TaskManager priority:high`). Clearly divided into **Phase 1–3**.
* **PROMPTS.md** → System prompts, role definitions, example calls (input/output).
* **WORKFLOW\.md** → Prepopulated table with: `Input | Action | Output | MCPs involved | Tests`.
* **DECISIONS.md** → Table with: `Date | Decision ID | Decision | Rationale | Author | Related Tasks | ClearThought reference`.
* **ROADMAP.md** → Milestones, deliverables, acceptance criteria.
* **ARCHITECTURE.md** → System design sections (frontend/backend/db, CI/CD, build matrix).
* **NOTES.md** → Scratchpad for research/ideas.
* **BUSINESS.md** → Business model, market, stakeholders, constraints. Must include a **section “Technical Impact” that maps business requirements into CONTEXT.md**.
* **docs/** → Onboarding and reference (INTRO, SETUP, USAGE, API, GLOSSARY).
* **meta/** → Logs, memory, prompts, and MCP traces. Split between **active** (for current context) and **ARCHIVE/** (reference only, avoids pollution with clear archive rules).
* **.github/** and **templates/** → CI, contribution guidelines, and reusable templates ensure consistency across teams.

---

## 📌 Example TASKS.md (cleaned)

```md
# TASKS

## Phase 1: Setup
- [ ] Define project scope in CONTEXT.md  #mcp:Context7
  - [ ] Gather requirements  #mcp:TaskManager priority:high
  - [ ] Identify constraints (link from BUSINESS.md where applicable)  #mcp:TaskManager priority:high
- [ ] Initialize repo skeleton  #mcp:TaskManager
- [ ] Setup MCP integrations (#TaskManager, #Context7, #MemoryBank)  #mcp:TaskManager

## Phase 2: Core Work
- [ ] Write initial PROMPTS.md  #mcp:TaskManager
  - [ ] Draft system prompts  #mcp:TaskManager
  - [ ] Add prompt examples  #mcp:TaskManager
- [ ] Map sequential steps in WORKFLOW.md  #mcp:SequentialThinking
- [ ] Draft first version of README.md  #mcp:TaskManager

## Phase 3: Expansion
- [ ] Document APIs in docs/API.md  #mcp:TaskManager
  - [ ] Define endpoints  #mcp:TaskManager
  - [ ] Add usage examples & tests  #mcp:TaskManager
- [ ] Add roadmap milestones  #mcp:TaskManager
- [ ] Log decisions in DECISIONS.md  #mcp:ClearThought
- [ ] Document business context in BUSINESS.md and cross-link to CONTEXT.md  #mcp:TaskManager
```

---

## ⚙️ WORKFLOW\.md template (prepopulated)

```md
# WORKFLOW — Sequential Steps (Template)

| Step | Input | Action | Output | MCPs Involved | Tests / Acceptance Criteria |
|------|-------|--------|--------|---------------|----------------------------|
| 1 | Project Initialization (answers) | Create skeleton files | All md files generated with placeholders | TaskManager, Context7 | Files exist; README contains project name |
| 2 | CONTEXT.md + BUSINESS.md | Validate constraints & frameworks | Confirmed context (business-to-technical mapping) | SequentialThinking, MemoryBank | CONTEXT.md has “Business Link” section referencing BUSINESS.md |
| 3 | TASKS.md | Seed tasks & subtasks | Task list synced to TaskManager | TaskManager | TASKS.md matches MCP-parsed tasks |
| 4 | PROMPTS.md | Add base prompts | Prompt library ready | MemoryBank, ClearThought | Prompts are stored and versioned |
| 5 | BUSINESS.md | Add business model & stakeholders | Business context documented + linked | TaskManager | BUSINESS.md contains Technical Impact section |
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
1. Read CONTEXT.md to understand goals, constraints, and linked BUSINESS.md insights.
2. Open TASKS.md — start claiming tasks and tagging them with `#mcp:TaskManager`.
3. Run `ci/run_all_checks.sh` to verify local environment.

## MCP integration guide
- For context, add entries to `meta/CONTEXT7_LOG.md` with date + summary. Use `#context7` tags.
- For tasks, add `#mcp:TaskManager` tags to TASKS.md lines.
- For decisions, log rows in DECISIONS.md and add `#clearthought` reference.
- For persistent facts, use `meta/MEMORYBANK_LOG.md`. Use `global:` prefix for cross-project facts.
- For business, log in `BUSINESS.md` and reference in CONTEXT.md under “Business Link”.

## Code & Documentation standards
- Inline comments and file headers required for all code.
- Each module must include minimal unit test + build step.
- Follow `templates/code_comment_template.md` for consistency.

## How to initialize a new project
1. Run initializer (via system prompt in Copilot or orchestrator).
2. Answer interactive questions.
3. Repo skeleton is generated with pre-filled CONTEXT.md, TASKS.md, and BUSINESS.md (linked together).
```

---

## ✅ Acceptance Criteria

1. All files listed in skeleton exist.
2. `README.md` contains project name, description, frameworks.
3. `CONTEXT.md` has frameworks, goals, audience, constraints, **and a Business Link section referencing BUSINESS.md**.
4. `TASKS.md` contains Phase 1 tasks with MCP tags.
5. `WORKFLOW.md` has table + at least 3 seeded steps, one referencing BUSINESS.md.
6. `DECISIONS.md` has table header.
7. `docs/USAGE.md` contains quickstart + MCP guide linking business → context.
8. `meta/MEMORYBANK_LOG.md` exists with initialization entry.
9. `BUSINESS.md` exists with market, model, stakeholders, and Technical Impact section.
10. `meta/ARCHIVE/` contains reference logs with archive rules defined to avoid context pollution.
11. CI pipelines and templates exist in `.github/` and `templates/` folders.

---

## Notes

* Designed for **automation + auditability**.
* Ensures no unused MCP logs.
* Avoids context pollution by strict file purposes, separating **active** vs **reference** context, and enforcing archive rules.
* Business context always informs technical constraints via explicit CONTEXT.md ↔ BUSINESS.md link.
* Adaptable for solo, small team, or enterprise-scale projects.
