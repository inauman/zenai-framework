# Insight: What Didn't Work

An honest postmortem of v1 framework concepts that didn't survive real usage. Knowing why things failed is as valuable as knowing what works.

## 12 Specialized Agent Personas

**The idea**: 12 AI agents with distinct personalities and expertise (Architect, Security Engineer, Rustecean, etc.) coordinated by a ZenMaster orchestrator.

**Why it failed**: Subagents can't have interactive conversations. Real development work is deeply conversational — you discuss, iterate, redirect, and build shared understanding. Delegating to isolated agents that can't be interrupted or redirected created more friction than value. The ZenMaster routing concept never materialized — you always just talked to the default agent and occasionally invoked a specialist.

**What replaced it**: Skills loaded into the default agent. Same knowledge, interactive conversation, no context switching.

## 3-Layer Context Hierarchy

**The idea**: Master Context (project overview), Domain Context (area-specific), Detail Context (task-specific), with "evolution chains" tracking how context changed over time.

**Why it failed**: Too complex to maintain. The real problem wasn't loading project overview (that's what CLAUDE.md does). The real problem was preserving session-specific insights — corrections, gotchas, design decisions — that live in conversation and die with context resets. No hierarchy addresses that.

**What replaced it**: A simple 3-file dev-docs system (plan.md, context.md, tasks.md) with a session handoff prompt. The handoff prompt captures exactly the knowledge that would be lost — insights, corrections, current state — in a format you can paste into a new session.

## Agent I/O Contracts

**The idea**: Formal input/output specifications for each agent, defining what they accept and produce, with structured handoff documents between them.

**Why it failed**: Over-engineered for the actual interaction pattern. In practice, you tell the agent what to do in natural language. The "contract" is the dev-docs (plan, context, tasks) — not a formal I/O specification. Agents that work well (zen-audit, zen-review) have simple prompts in their agent definition file, not separate contract documents.

**What replaced it**: Agent definitions with role, input, workflow, output, and constraints sections — all in one markdown file. The dev-docs are the implicit contract.

## Context Evolution Chains

**The idea**: Track how context documents evolve across sessions, maintaining a history of what changed and why.

**Why it failed**: Git already does this. Every commit captures what changed and why (if the commit message is good). Maintaining a separate "evolution chain" was redundant work that nobody actually read.

**What replaced it**: Git history + `/update-dev-docs` before each `/clear`. The context.md file is the living document. Git tracks its evolution.

## Cursor-Specific Tooling

**The idea**: `.cursorrules` behavioral contract defining how the AI editor should behave, with specific Cursor IDE integration.

**Why it failed**: The framework was meant to be open-source and tool-agnostic, but .cursorrules tied it to one specific tool. When the user moved to Claude Code, the .cursorrules file became irrelevant.

**What replaced it**: `.claude/skills/` and `.claude/agents/` — the native extension mechanism for Claude Code. The framework now uses Claude Code as the primary reference implementation but keeps principles tool-agnostic.

## Complex Ritual Ceremonies

**The idea**: 10 rituals covering every aspect of development — project documentation, test strategy, technical blueprint, validation, context management, agent handoff, interface design, retrospective, show & tell, and antipatterns.

**Why it failed**: Too many rituals. Most were either subsumed by the natural workflow (context management → dev-docs), replaced by skills (technical blueprint → system-architecture skill), or too heavy for practical use (agent handoff → dev-docs handoff prompt).

**What survived**: 4 rituals that address genuine needs not covered by the workflow itself:
- Show & Tell (quality gate before completion)
- Retrospective (structured learning)
- Validation Checklist (pre-completion checks)
- Antipatterns (awareness of failure modes)

## The "Sub-2-Minute Context Loading" Metric

**The idea**: Reduce context reconstruction time from 25-35 minutes to under 2 minutes through hierarchical context documents.

**Why it failed**: The metric measured the wrong thing. The real cost isn't loading project overview (CLAUDE.md handles that). The real cost is losing session-specific knowledge — corrections, insights, API quirks, design decisions — that take hours to rediscover. You can load CLAUDE.md in 2 seconds but still waste 30 minutes re-explaining why you chose approach A over approach B.

**What replaced it**: The metric is now "zero repeated explanations." A good handoff prompt means the next session knows everything the previous session knew, without the human having to repeat anything.

## The Takeaway

Every failed concept had a legitimate problem it was trying to solve. The solutions were over-engineered because they were designed in theory, not battle-tested in practice. The v2 framework is simpler because it only includes what survived months of real usage on a complex production project.

When in doubt, start simple. Add complexity only when a specific pain point demands it. Three similar lines are better than a premature abstraction — this applies to frameworks too.
