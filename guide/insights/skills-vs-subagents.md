# Insight: Skills vs. Subagents

Why the 12-agent model failed and what replaced it.

## The Original Vision

The v1 framework defined 12 specialized AI agent personas: Architect, Security Engineer, Rustecean, UX Engineer, Test Automation Engineer, Operations Engineer, Product Owner, Designer, and ZenMaster as the orchestrator. The idea was that each agent would have specialized knowledge and behavioral traits, and ZenMaster would route tasks to the right specialist.

On paper, this looked like a well-organized team. In practice, it collapsed.

## What Went Wrong

### Subagents Can't Converse

A subagent runs in an isolated context window. It doesn't see your conversation history. It can't be interrupted. It can't ask clarifying questions mid-task. When it finishes, it returns a summary and its context is gone.

This means you can't say "wait, also consider the caching layer we discussed earlier." The subagent never heard that discussion. You'd have to re-explain everything in the initial prompt, which defeats the purpose of specialization.

For planning (which is deeply conversational), for execution (where you interrupt and redirect constantly), and for code review (where you discuss findings interactively) — subagents are the wrong tool.

### The "Which Agent Am I Talking To?" Problem

With multiple agents, you lose track of context. Did I tell the Architect about the API change, or was that the Security Engineer? If I ask a question now, who answers — the default agent or the last specialist I invoked?

In Claude Code, subagents don't work like "rooms you enter." They work like "people you delegate to." You always talk to the default agent. You can invoke a subagent with `@agent-name`, but after it finishes, you're back with the default agent. There's no persistent agent state.

This confusion caused real problems. In one incident, a subagent without proper tool permissions was auto-invoked for a refactoring task and tried to edit files using shell commands (`cat`) instead of the editor tool, creating a mess that had to be manually cleaned up.

### Tool Permission Hazards

Subagents inherit or are granted tool permissions. An execution-oriented subagent needs full tool access (read, write, edit, bash, git). But giving a subagent full autonomy means:
- It can make changes you don't see in real-time
- It might use workarounds when permissions are misconfigured
- It operates without your ability to pause and redirect

This is fine for verification (where you want independence) but dangerous for execution (where you want visibility).

## What Replaced It

### Skills for Interactive Work

A **skill** loads knowledge into the default agent's context. You continue talking to the same agent — it just knows more. This means:

- Full conversation history is preserved
- You can interrupt, redirect, and ask follow-ups
- You see every step in real-time
- You maintain one continuous context

Instead of 12 specialized agents, you have skills organized by purpose:
- **a-tier (utility)**: capture, deep-research, explore-project
- **b-tier (engineering quality)**: rust-backend, system-architecture, code-review, show-n-tell
- **d-tier (domain expertise)**: your project's specific technology domains

You invoke them with `/skill-name` and they enrich the conversation. No context switch, no isolation, no confusion.

### Subagents Only for Verification

The one place where subagents shine: **when you explicitly want the agent to NOT share your context.** Verification is that case.

A fresh agent reading tasks.md and grepping the codebase, with no memory of the planning discussion, provides genuinely independent evaluation. The context isolation that makes subagents bad for interactive work makes them perfect for honest assessment.

Two verification agents replaced all 12 personas:
- **zen-audit**: adversarial task completion auditor
- **zen-review**: cold code reviewer

Both run in their own context, write reports to `handoff/`, and never modify source code.

## The Taxonomy

```
Skills    = knowledge you think with (interactive, shared context)
Subagents = workers you check against (isolated, fire-and-forget)
```

If you need back-and-forth → skill.
If you need fresh eyes → subagent.
If you're not sure → skill (default to interactive).

## When Subagents Might Expand

The 2-agent model (audit + review) covers the primary verification use case. You might add more subagents for:

- **Security scanning**: Automated vulnerability checks (read-only, separate context)
- **Performance profiling**: Run benchmarks and report (fire-and-forget)
- **Documentation audit**: Check docs match code (read-only)

The pattern is always the same: fire-and-forget, read-only, write to handoff, never modify source. If it needs conversation, make it a skill.
