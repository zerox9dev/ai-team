# AGENTS.md

You are an AI agent working as part of a product development team. Before doing anything, read this file completely.

## How This Works

This repo contains an AI-powered product team. Each agent has a role, reads a prompt file, and produces output that feeds into the next agent.

You operate inside a **pipeline** — a sequential chain of specialists that turns a raw task into production-ready code.

## Your Team

| Role | Prompt | Responsibility |
|------|--------|---------------|
| Product Manager | `.agents/PM.md` | Analyzes the problem, writes PRD |
| Designer | `.agents/DESIGNER.md` | Designs UX/UI based on PRD |
| Engineer | `.agents/ENGINEER.md` | Writes working code |
| QA | `.agents/QA.md` | Tests and finds bugs |
| Reviewer | `.agents/REVIEWER.md` | Final quality gate |

## Pipeline

```
Operator creates task → .pipeline/XXX-task.md
  │
  ▼
[PM] → reads task → writes PRD → .pipeline/XXX-prd.md
  │
  ▼
[Designer] → reads PRD → writes UI spec → .pipeline/XXX-design.md
  │
  ▼
[Engineer] → reads PRD + design → writes code → .pipeline/XXX-code.md
  │
  ▼
[QA] → reads everything → tests → .pipeline/XXX-qa.md
  │
  ▼
[Reviewer] → final check → .pipeline/XXX-review.md
  │
  ▼
Done or back to specific stage
```

## Orchestration Rules

### Order
1. Read the task from `.pipeline/`
2. Run agents **sequentially** — each reads their `.agents/*.md` prompt
3. Each agent saves output to `.pipeline/`
4. Next agent ALWAYS reads all previous outputs

### Skills (shared context)
Before starting, read relevant files from `.skills/`:

| Skill | Used by | Contains |
|-------|---------|----------|
| `.skills/STACK.md` | Engineer, QA | Tech stack, structure, dependencies |
| `.skills/STYLEGUIDE.md` | Designer, Engineer | Design system, colors, components |
| `.skills/CODESTANDARDS.md` | Engineer, QA | Code style, naming, patterns |

Add your own — any `.md` in `.skills/` is available to all agents.

### Handoff between agents
- Each agent receives: task + ALL previous results
- Each agent writes ONLY their own file
- Output format: markdown

### Loops and rework
- QA finds bugs → back to Engineer with bug report
- Reviewer has comments → back to specific stage
- Max 3 rework cycles per task — then escalate to operator

### Operator review
- After EVERY stage, ask operator: "Continue or any changes?"
- Operator says "next" / "ok" / "go" → proceed
- Operator gives feedback → re-run current stage with feedback

### Never
- Skip stages
- Run agents in parallel
- Invent requirements not in the task
- Modify files from previous stages

## Quick Start

Tell your AI:

```
Read AGENTS.md and all files in .agents/ and .skills/.
Task: .pipeline/001-task.md
Start with PM.
```

## Adding Custom Agents

Create a new `.md` file in `.agents/` with:
1. Role description
2. Input (what files to read)
3. Output (what file to write)
4. Format template
5. Rules

Then add the agent to the pipeline in this file.

### Examples of custom agents:
- `.agents/COPYWRITER.md` — writes marketing copy
- `.agents/DEVOPS.md` — writes Docker/CI configs
- `.agents/DATA.md` — designs database schemas
- `.agents/SECURITY.md` — security audit
