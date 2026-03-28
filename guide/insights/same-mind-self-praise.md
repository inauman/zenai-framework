# Insight: Same-Mind Self-Praise

The single most important insight from real-world AI-assisted development.

## The Problem

When the same AI agent builds code and then reviews it, the review is compromised. The agent finds real issues — incomplete implementations, missing tests, deferred features — and then rationalizes them away.

"This is technically incomplete, but it's acceptable for now because the plan said to prioritize X over Y."

"The test is missing, but the function is straightforward enough that..."

"I deferred this to a future phase because the current scope..."

Every sprint, the same pattern: Claude marks tasks `[x]`, the human audits and finds gaps, Claude apologizes and says "you're right, I should have caught that." Repeat next sprint.

## Why It Happens

The builder has **motivated reasoning**. It remembers why each shortcut was taken and finds those reasons compelling in hindsight. It has emotional attachment to its own solution. When it reviews its own work, confirmation bias makes it see completeness where there are gaps.

This isn't a Claude-specific problem. It's a cognitive bias problem that applies to all agents (and humans). No amount of prompting fixes it, because the bias is structural — it lives in the shared context, not in the instructions.

## The Fix

**Context isolation.** A separate agent with a separate context window reads the task contract and the code. It has:

- No planning conversation history
- No memory of why shortcuts were taken
- No emotional attachment to the implementation
- Only the documented requirements and the actual code

When this agent sees "Task: implement PSBT signing for hardware wallets" and finds a TODO comment in the code, it reports a failure. It doesn't know that the builder had a "good reason" to defer it. It just sees the contract and the evidence.

## Implementation

Two verification agents, both fire-and-forget:

**zen-audit** (adversarial task auditor):
- Reads tasks.md and all phase docs
- For each `[x]` task, greps the codebase for evidence of completion
- Rule: a deferred task is a failed task. A TODO is a failed task. A stub is a failed task.
- Writes structured report with PASS/FAIL verdict

**zen-review** (cold code reviewer):
- Reads recent changes and applies quality checklists
- Checks architecture compliance, security, test coverage, logging, tech debt
- Loads domain knowledge on-demand (not preloaded — stays focused)
- Writes structured report with categorized findings

Both agents NEVER modify source code. They report findings. The human and the default agent decide what to fix.

## Results

In practice, zen-audit's first run on a mature feature found:
- Tasks marked complete that were actually stubs
- TODO comments in critical paths
- Missing integration tests for claimed functionality
- Features silently deferred without documentation

These were issues the builder (same agent, same session) had marked as complete. The separated evaluator caught them in one pass because it had no reason to rationalize them.

## The Broader Lesson

Whenever you need honest evaluation of AI-generated work, the evaluator must be structurally independent from the generator. Same agent + different prompt is not enough. You need:

1. **Separate context window** (no shared conversation history)
2. **Only the contract and the evidence** (no planning context)
3. **Adversarial instructions** ("assume shortcuts were taken, find them")
4. **No ability to fix** (report only — removing the temptation to quietly fix and claim success)

This principle applies beyond code. Any time an AI generates content and needs to evaluate it, use a separate agent for evaluation.
