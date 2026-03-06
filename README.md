# AI Team 🤖

Open-source AI product team. Five agents work sequentially — from idea to production-ready code.

No frameworks. No infrastructure. Just `.md` files and any AI.

## How it works

```
You (operator)
  │
  ▼ task
[PM Agent] → analyzes problem → writes PRD
  │
  ▼
[Designer Agent] → reads PRD → writes UI/UX spec
  │
  ▼
[Engineer Agent] → reads PRD + design → writes code
  │
  ▼
[QA Agent] → tests everything → PASS or FAIL
  │
  ▼
[Reviewer Agent] → final check → SHIP, REWORK, or REJECT
```

You review after each step. You're the boss — agents do the work.

## Quick Start

1. Clone the repo
2. Describe your task in `.pipeline/001-task.md`
3. Open any AI (Cursor, Claude, ChatGPT, Codex)
4. Say:

```
Read AGENTS.md and all files in .agents/ and .skills/.
Task: .pipeline/001-task.md
Start with PM.
```

5. Review each step → say "next" to continue

That's it. No setup, no API keys, no config.

## Structure

```
├── AGENTS.md                # Entry point — pipeline, roles, orchestration
├── .agents/
│   ├── PM.md                # Product Manager agent
│   ├── DESIGNER.md          # Product Designer agent
│   ├── ENGINEER.md          # Developer agent
│   ├── QA.md                # QA Engineer agent
│   └── REVIEWER.md          # Senior Reviewer agent
├── .skills/
│   ├── STACK.md             # Project tech stack context
│   ├── STYLEGUIDE.md        # Design system & UI rules
│   └── CODESTANDARDS.md     # Coding conventions
└── .pipeline/
    └── 001-task.md          # Task template
```

## Agents

| Agent | Input | Output | Role |
|-------|-------|--------|------|
| **PM** | Task | PRD | Defines what to build and why |
| **Designer** | PRD | UI/UX spec | Defines how it looks and works |
| **Engineer** | PRD + Design | Working code | Builds the feature |
| **QA** | All above | Bug report | Finds everything that's wrong |
| **Reviewer** | All above | Final verdict | Last checkpoint before ship |

## Skills

Skills are shared context files that any agent can read. Put your project-specific knowledge here:

| Skill | What it provides |
|-------|-----------------|
| `.skills/STACK.md` | Tech stack, dependencies, project structure |
| `.skills/STYLEGUIDE.md` | Design tokens, components, UI patterns |
| `.skills/CODESTANDARDS.md` | Code style, naming, file structure rules |

Add your own skills — any `.md` file in `.skills/` is available to all agents.

## Pipeline Rules

- Agents work **sequentially**, never in parallel
- Each agent reads **all previous results**
- Operator reviews **after every step**
- Max **3 rework cycles** per task, then escalate
- QA FAIL → back to Engineer → QA re-checks
- Reviewer REWORK → back to specific stage

## Works With

- [Cursor](https://cursor.sh)
- [Claude](https://claude.ai)
- [ChatGPT](https://chat.openai.com)
- [OpenAI Codex](https://openai.com/codex)
- [Windsurf](https://codeium.com/windsurf)
- Any AI that can read markdown

## Examples

### Example: Add a feature to a SaaS

```markdown
# Task 001: Natural language time entry

## Context
Logr — time tracking SaaS. Stack: Next.js 16, React 19, Supabase, Vercel.

## Task
User types "2 hours design for Acme" and the system 
auto-creates a time entry with client, project, and duration.

## Result
Working feature with UI, API route, and AI parsing logic.
```

### Example: Build a landing page

```markdown
# Task 002: Landing page for product launch

## Context
New SaaS product. No existing code. Need a landing page for Product Hunt launch.

## Task
Hero section, features, pricing, CTA. Dark theme, modern SaaS look.

## Stack
Next.js, Tailwind, shadcn/ui, Vercel.

## Result  
Complete page.tsx with all sections, responsive, ready to deploy.
```

## Why .md?

- **Zero setup** — no Docker, no servers, no API keys
- **Works everywhere** — any AI, any IDE, any OS
- **Version controlled** — every step is a git commit
- **Human readable** — anyone can review the pipeline
- **Forkable** — customize agents for your team

## Contributing

PRs welcome. Keep it simple — the whole point is `.md` files.

## License

[MIT](LICENSE)

---

Built by [@zerox9dev](https://zerox9dev.com)
