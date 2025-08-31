# 📂 Project Skeleton — Smart Enterprise-Light (Markdown-first)

```
project-name/
│
├── README.md                  # Project overview, purpose, quickstart
├── CONTEXT.md                 # Context log (#context7, background, constraints, links to BUSINESS.md)
├── TASKS.md                   # Task breakdown (#TaskManager friendly, phased)
├── PROMPTS.md                 # System prompts, AI instructions, context-engineering
├── WORKFLOW.md                # Sequential thinking steps, process flows (templated)
├── DECISIONS.md               # ClearThought log: decisions & rationale (progressive disclosure)
├── ROADMAP.md                 # High-level milestones & timeline (progressive disclosure)
├── ARCHITECTURE.md            # If technical: system design, diagrams (placeholder)
├── NOTES.md                   # Scratchpad, ideas, references
├── BUSINESS.md                # Business context (with tiered templates for solo/startup/enterprise)
│
├── docs/                      # Extended documentation
│   ├── INTRO.md               # Project intro and elevator pitch
│   ├── SETUP.md               # Repro steps: install, build, run, env
│   ├── USAGE.md               # How to use the project + MCP workflows (filled)
│   ├── API.md                 # If project has endpoints (examples + tests)
│   └── GLOSSARY.md            # Terms & definitions
│
├── .github/                   # GitHub configs, issue templates, CI/CD
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
    ├── GLOBAL_MEMORY.md       # Cross-project memory (never archived)
    ├── GLOBAL_PROMPTS.md      # Templates for add/edit/fix/delete operations
    └── ARCHIVE/               # Reference-only logs (archive rules to prevent context overload)
```

---

## 🔑 File Purposes (with Smart Templates)

* **README.md** → Always present. Project name, description, frameworks, CI badge. Adapt via template prompts.
* **CONTEXT.md** → Always links to BUSINESS.md. Stores background, goals, constraints, and Project Initialization answers.
* **TASKS.md** → Always phased (Phase 1–3). MCP tags for TaskManager.
* **PROMPTS.md** → Role definitions + examples.
* **WORKFLOW\.md** → Prepopulated step-by-step table.
* **DECISIONS.md** → Progressive disclosure: Active decisions visible, archive collapsed.
* **ROADMAP.md** → Active milestones visible, archive collapsed.
* **ARCHITECTURE.md** → Placeholder for technical projects, expands when complexity grows.
* **NOTES.md** → Scratchpad.
* **BUSINESS.md** → Tiered templates:

  * **Solo/Small Teams (1–5):** Quick capture (problem, users, success metrics).
  * **Growing Teams (5+):** Add stakeholders, revenue model, competitive analysis.
  * **Enterprise:** Full model (market, compliance, governance, risks).
* **meta/** → Strict context layering. Active logs vs archive rules.

---

## 📌 Example TASKS.md (Smart Enterprise-Light)

```md
# TASKS

## Phase 1: Setup
- [ ] Define scope in CONTEXT.md  #mcp:Context7
  - [ ] Gather requirements  #mcp:TaskManager priority:high
  - [ ] Identify constraints (link BUSINESS.md if applicable)  #mcp:TaskManager
- [ ] Initialize repo skeleton  #mcp:TaskManager
- [ ] Setup MCP integrations (#TaskManager, #Context7, #MemoryBank)  #mcp:TaskManager

## Phase 2: Core Work
- [ ] Write PROMPTS.md with examples  #mcp:TaskManager
- [ ] Map sequential steps in WORKFLOW.md  #mcp:SequentialThinking
- [ ] Draft first README.md  #mcp:TaskManager

## Phase 3: Expansion
- [ ] Document APIs in docs/API.md  #mcp:TaskManager
- [ ] Add roadmap milestones  #mcp:TaskManager
- [ ] Log decisions in DECISIONS.md  #mcp:ClearThought
- [ ] Refine BUSINESS.md and link into CONTEXT.md  #mcp:TaskManager
```

---

## ⚙️ Progressive Disclosure in DECISIONS.md

```md
# DECISIONS

## Active Decisions
| Date | Decision ID | Decision | Rationale | Author | Related Tasks | ClearThought Log |
|------|-------------|----------|-----------|--------|---------------|------------------|
| YYYY-MM-DD | D-0001 | Choose QwikJS for frontend | SSR + hydration needs | <name> | TASK-1 | #clearthought:entry-id |

<details>
<summary>Archived Decisions</summary>

| Date | Decision ID | Decision | Rationale | Author | Related Tasks | ClearThought Log |
|------|-------------|----------|-----------|--------|---------------|------------------|
| YYYY-MM-DD | D-0000 | Use monorepo | Simplicity | <name> | TASK-0 | #clearthought:archived |

</details>
```

---

## ⚙️ Context Loading Rules (MCP-Aware)

* **Dev work** → CONTEXT.md + TASKS.md + WORKFLOW\.md
* **Business talk** → CONTEXT.md + BUSINESS.md
* **Planning session** → ROADMAP.md + DECISIONS.md
* **Enterprise** → Always load full set
* **Archive** → Loaded only on demand

---

## 📘 docs/USAGE.md (Key Sections)

```
# USAGE

## Quickstart
1. Read CONTEXT.md → project goals & constraints.
2. Open TASKS.md → claim tasks (#mcp:TaskManager).
3. Run `ci/run_all_checks.sh` → verify environment.

## Team Scaling Notes
- Solo → Fill only minimal BUSINESS.md section.
- Small Team → Add stakeholders + roadmap.
- Enterprise → Fill all templates.

## MCP Context Loading
- Context7 → load CONTEXT.md + BUSINESS.md
- TaskManager → TASKS.md
- SequentialThinking → WORKFLOW.md
- ClearThought → DECISIONS.md
- MemoryBank → MEMORYBANK_LOG.md
```

---

## ✅ Acceptance Criteria (Unified)

1. All skeleton files exist.
2. README.md has project name + description.
3. CONTEXT.md always links to BUSINESS.md.
4. TASKS.md phased + MCP tags.
5. WORKFLOW\.md has ≥3 seeded steps.
6. DECISIONS.md progressive disclosure active.
7. BUSINESS.md has tiered template.
8. docs/USAGE.md explains scaling.
9. meta/ARCHIVE/ exists with rules.
10. CI/CD pipelines exist in .github.

---

## Notes

* Unified skeleton → no branching for team size.
* Lightweight templates prevent adoption issues.
* MCP selective loading prevents context window bloat.
* Progressive disclosure keeps files lean but scalable.
* Enterprise rigor available from day one without overwhelming solos/startups.
