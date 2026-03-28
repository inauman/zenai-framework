# ZenAI Framework

A battle-tested framework for AI-assisted software development on long-running, complex projects. Built for Claude Code. Validated over months on production systems.

**Skills for interactive work. Agents for verification. Documents for continuity.**

## The Workflow

```
Plan → Execute → Verify → Fix → Review → Show & Tell → Archive
```

| Phase | Who | Purpose |
|---|---|---|
| **Plan** | Default agent + skills | Interactive planning, produce dev-docs |
| **Execute** | Default agent + skills | Build features, checkpoint with handoff prompts |
| **Verify** | zen-audit + zen-review | Independent verification (separate context) |
| **Fix** | Default agent | Triage findings, execute fixes |
| **Review** | Default agent + code-review skill | Interactive code review ceremony |
| **Show & Tell** | Default agent + show-n-tell skill | Final quality gate before completion |

## What's Inside

```
guide/
├── 01-philosophy.md           Why this framework exists
├── 02-workflow.md             The core workflow (start here)
├── 03-skills-and-agents.md    Skills vs. subagents architecture
├── 04-session-continuity.md   Dev-docs system + handoff prompts
├── 05-adoption-guide.md       30-minute setup for any project
├── rituals/                   4 surviving ceremonies
├── standards/                 Security, testing, logging, error handling
└── insights/                  Hard-won lessons from real usage

templates/
├── skill-template.md          How to write a skill
├── agent-template.md          How to write a verification agent
├── dev-docs-*.md              Plan, context, and tasks templates
├── handoff-prompt.md          Session handoff prompt template
└── project-setup/             Starter files to copy into your project

examples/
└── workflow-walkthrough.md    End-to-end example of one full cycle
```

## Key Concepts

**Skills** load knowledge into the default agent's context. You use them for interactive work — planning, coding, reviewing. They enrich the conversation without context switching.

**Verification agents** (zen-audit, zen-review) run in isolated context windows. They read the task contract and the code cold, with no memory of the planning discussion. This solves the [same-mind self-praise problem](guide/insights/same-mind-self-praise.md).

**Dev-docs** (plan.md, context.md, tasks.md) are the handoff contract between sessions. The session handoff prompt — generated before every context reset — captures insights, corrections, and current state so the next session starts informed, not from zero.

## Getting Started

1. Read [02-workflow.md](guide/02-workflow.md) — the core workflow (5 minutes)
2. Follow [05-adoption-guide.md](guide/05-adoption-guide.md) — set up on your project (30 minutes)
3. Copy starter files from [templates/project-setup/](templates/project-setup/) into your project
4. Run your first full cycle

## What This Is Not

- Not a prompt library (it's a workflow framework)
- Not tool-specific (Claude Code first, but principles apply to any AI assistant)
- Not theoretical (every pattern survived months of real usage)
- Not prescriptive about your tech stack (works with any language/framework)

## Origin

This framework evolved from the ZenAI Programming Rituals v1, which was designed around a 12-agent orchestration model. Real-world usage proved that most of that complexity didn't survive contact with reality. The v2 framework is radically simpler — only including what actually works. See [insights/what-didnt-work.md](guide/insights/what-didnt-work.md) for the honest postmortem.

## License

MIT — see [LICENSE](LICENSE)
