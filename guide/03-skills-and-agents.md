# Skills and Agents

The most important architectural decision in ZenAI: **skills for interactive work, subagents only for fire-and-forget verification.**

This replaces the old model of specialized agent personas. It's simpler, more practical, and solves the self-evaluation problem that the multi-agent approach couldn't.

## Why Skills Beat Subagents for Interactive Work

A **skill** loads knowledge into the default agent's context window. You continue talking to the same agent — it just knows more. You can interrupt, redirect, ask follow-up questions, and iterate naturally. The skill enriches the conversation without switching context.

A **subagent** runs in a completely separate context window. It doesn't see your conversation history. It can't be interrupted for clarification. When it finishes, it returns a summary and its internal context is gone. It's delegation, not conversation.

For planning, execution, code review, and demos — where you need back-and-forth, shared context, and the ability to say "wait, also consider this" — skills are the right tool. Subagents are wrong because you lose visibility and control.

For verification — where you explicitly want fresh eyes without the builder's bias — subagents are the right tool. Skills are wrong because they share the context that creates the bias.

## Skill Tiers

Organize skills by purpose using a prefix convention:

### a-tier: Utility (anytime helpers)
Tools you invoke at any point in the workflow.

| Skill | Purpose |
|---|---|
| `/capture` | Persist session insights into project docs (auto-suggested after deep discussions) |
| `/deep-research` | Research external topics — APIs, protocols, regulations |
| `/explore-project` | Explore and explain project internals |
| `/visualize-codebase` | Generate interactive codebase tree view |

### b-tier: Engineering Quality (workflow ceremonies)
Skills tied to specific phases of the development workflow.

| Skill | Purpose |
|---|---|
| `/rust-backend` | Rust engineering principles, I3 philosophy, verify-first protocol |
| `/system-architecture` | Design patterns, security checklists, Release It! stability patterns |
| `/code-review` | Multi-dimensional code review (architecture, security, tests, tech debt) |
| `/show-n-tell` | Interactive demo ceremony — final quality gate |

### d-tier: Domain Expertise (project-specific knowledge)
Deep knowledge for your project's technology domains.

**Examples** (from real projects):

| Skill | Purpose |
|---|---|
| `/d-graphql` | Schema design, resolvers, N+1 prevention |
| `/d-postgres` | Query optimization, migrations, indexing |
| `/d-auth` | JWT, OAuth, session management, RBAC |
| `/d-cli` | Agent-first CLI design — exit codes, JSON output |

**Create your own d-tier skills** for your project's technology domains. The key is deep, reusable knowledge that the default agent doesn't have natively.

### Project-level skills (workflow automation)
Skills that automate the dev-docs system. These live in your project's `.claude/skills/` directory, not globally.

| Skill | Purpose |
|---|---|
| `/create-dev-docs` | Create 3-file plan after planning phase |
| `/update-dev-docs` | Checkpoint progress + generate session handoff prompt |
| `/add-backlog` | Quick capture to `docs/plan/backlog/` |
| `/fix-plan` | Triage audit+review findings into fix docs |

## Verification Agents

Two subagents, both fire-and-forget, both read-only:

### zen-audit — Adversarial Sprint Auditor

**Purpose**: For every task marked complete, prove it's genuinely complete — or prove it's not.

**How it works**:
1. Reads ALL files in the phase's `docs/plan/active/<feature>/` directory
2. For each `[x]` task, greps/reads the codebase to verify the implementation exists
3. Flags: deferred tasks, TODO comments, stub implementations, missing tests
4. Writes report to `handoff/<feature>-audit-<MMDD>-<i>.md`
5. NEVER modifies source code

**Key rule**: A deferred task is a failed task. A TODO is a failed task. A stub is a failed task.

**Model**: Use the most capable model available — audit quality is a critical gate.

### zen-review — Cold Code Reviewer

**Purpose**: Review code changes against quality standards without the builder's cognitive bias.

**How it works**:
1. Reads phase docs and recent git history
2. Loads domain skill references on-demand (based on your instructions)
3. Applies review methodology: architecture, security, protocol correctness, test quality, logging, docs, tech debt, stability patterns
4. Writes report to `handoff/<feature>-review-<MMDD>-<i>.md`
5. NEVER modifies source code

**Skills loaded**: code-review + system-architecture (review methodology). Domain skills read on-demand via `Read` tool when you tell it what domain to focus on.

## Writing Your Own Skills

A skill is a markdown file (`SKILL.md`) inside a directory under `.claude/skills/`:

```
.claude/skills/my-skill/
├── SKILL.md          # Required, under 500 lines
└── references/       # Optional, loaded on-demand
    ├── api-details.md
    └── patterns.md
```

**SKILL.md frontmatter:**
```yaml
---
name: my-skill
description: One-line description — drives when Claude auto-suggests this skill
---
```

**Guidelines:**
- Keep SKILL.md under 500 lines — it loads into context when invoked
- Move detailed reference material to `references/` — loaded on-demand, not at startup
- Write the description clearly — it determines when Claude offers to use the skill
- Set `disable-model-invocation: true` only for skills with side effects (deploys, releases)

See [templates/skill-template.md](../templates/skill-template.md) for a complete template.

## Writing Verification Agents

An agent is a markdown file in `.claude/agents/`:

```yaml
---
name: zen-audit
description: "Adversarial sprint completion auditor..."
model: opus
tools: Read, Grep, Glob, Bash, Write
---
```

**Key design choices:**
- **Tools**: Grant Read, Grep, Glob, Bash (for running tests), Write (for reports). Never grant Edit — verification agents don't modify source code.
- **Skills**: zen-audit loads NO skills (audits cold, no knowledge bias). zen-review loads review methodology skills.
- **Model**: Use the most capable model for quality gates.
- **Output**: Always write to `handoff/` directory with structured report format.

See [templates/agent-template.md](../templates/agent-template.md) for a complete template.

## The Mental Model

```
Skills    = knowledge that enriches your conversation
            (loaded into default agent, full visibility, interactive)

Agents    = independent workers for verification
            (separate context, fire-and-forget, return a report)

Dev-docs  = the handoff contract between sessions and phases
            (plan, context, tasks — the source of truth)
```

No overlap. No confusion about who you're talking to. Skills for thinking-with, agents for checking-against.
