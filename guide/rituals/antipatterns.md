# Antipatterns

Common failure modes in AI-assisted development. Knowing these patterns helps you detect them early and course-correct before they cause real damage.

## 1. Same-Mind Self-Praise

**What**: The same agent that built the code reviews it, finds real issues, then rationalizes them away. "This is technically incomplete, but it's fine for now because..."

**Why it happens**: The builder has context and emotional attachment. It remembers why each shortcut was taken and finds those reasons compelling in hindsight.

**Detection**: Claude marks tasks `[x]` that are actually stubs, deferred, or partially implemented. Audit reports consistently find gaps that the builder missed.

**Prevention**: Use a separate verification agent (zen-audit, zen-review) with its own context window. It reads the task contract and the code cold, with no planning context.

## 2. Context Amnesia

**What**: Knowledge, corrections, and insights from one session are lost when the context resets. The next session makes the same mistakes, asks the same questions, and rediscovers the same gotchas.

**Why it happens**: Context resets (`/clear`, new session) destroy everything not written down. Conversation history is ephemeral.

**Detection**: You find yourself saying "I already told you this" or re-explaining decisions from a previous session.

**Prevention**: Always run `/update-dev-docs` before `/clear`. The handoff prompt captures insights, corrections, and current state. Paste it into the next session.

## 3. Architecture Drift

**What**: Implementation gradually diverges from the agreed design. No single change is wrong, but the cumulative effect creates inconsistency.

**Why it happens**: Each session makes locally reasonable decisions without checking the plan. Over time, the code no longer matches the architecture.

**Detection**: Code review finds patterns inconsistent with the plan. New components don't follow established conventions.

**Prevention**: Read the plan at the start of each session. Check architectural decisions against ADRs. Run periodic architecture reviews with `/system-architecture`.

## 4. Premature Optimization

**What**: Optimizing code that doesn't need it. Adding caching, async, or complex patterns before measuring whether there's a problem.

**Why it happens**: AI tends toward comprehensive solutions. "While we're here, let's also add..." spirals into over-engineering.

**Detection**: Code complexity exceeds what the requirements demand. Abstractions exist for hypothetical future needs.

**Prevention**: Start simple. Measure before optimizing. Three similar lines are better than a premature abstraction. Add complexity only when requirements demand it.

## 5. Documentation Drift

**What**: Code changes but documentation doesn't. ADRs describe decisions that were later reversed. Guides reference APIs that changed.

**Why it happens**: Documentation updates feel like overhead. "I'll update the docs later" becomes "I forgot."

**Detection**: New sessions read stale docs and make wrong assumptions. Show & Tell reveals gaps between docs and reality.

**Prevention**: Update docs as part of the task, not after. The validation checklist includes "existing docs updated." Use `/capture` to persist insights into permanent docs immediately.

## 6. Scope Creep Through AI

**What**: AI suggests improvements beyond what was asked. A bug fix becomes a refactor. A feature becomes an architecture overhaul.

**Why it happens**: AI sees opportunities for improvement and offers them proactively. Each suggestion is reasonable in isolation, but the cumulative scope explodes.

**Detection**: Tasks take much longer than estimated. The diff is 10x larger than the original scope. Unrelated files are modified.

**Prevention**: Define scope in tasks.md before starting. Stick to the task. If you discover something worth doing, capture it in backlog (`/add-backlog`) instead of doing it now.

## 7. Cargo Cult Testing

**What**: Tests exist but don't actually validate behavior. High coverage numbers with low defect detection. Tests that pass when the code is broken.

**Why it happens**: AI generates tests that match the implementation rather than the specification. Tests become mirrors of the code instead of independent validators.

**Detection**: Tests pass but the feature doesn't work when used manually. Test names describe implementation details, not behavior.

**Prevention**: Write tests from the specification, not the implementation. Test behavior ("when I send to this address, the balance decreases") not internals ("function X calls function Y with parameter Z").

## 8. Security Theater

**What**: Security measures that look good but don't actually protect. Encrypted storage with the key next to the lock. Input validation on the client but not the server.

**Why it happens**: Security requires deep thinking about threat models. AI may implement the visible parts (encryption, validation) without understanding the threat being mitigated.

**Detection**: Security review finds measures that don't actually prevent the stated threat. "Defense in depth" is actually "the same defense repeated."

**Prevention**: Start with the threat model: what are we protecting, from whom, under what conditions? Then implement defenses that specifically address those threats. Use the security standard as a checklist.

## 9. Tool Worship

**What**: Assuming the AI tool is always right. Not questioning generated code. Accepting explanations without verification.

**Why it happens**: AI sounds confident even when wrong. Over time, you stop checking.

**Detection**: Bugs that a simple test would have caught. Incorrect API usage that a quick `--help` would have revealed. Wrong library versions.

**Prevention**: Verify before implementing. Test CLI tools before coding against their APIs. Check library versions. Run the code. Trust but verify.

## 10. Session Addiction

**What**: Keeping a session alive far too long to avoid the pain of context reset. The context window fills with irrelevant history. Responses degrade in quality.

**Why it happens**: Context resets feel expensive (they are, without proper handoff). So you avoid them, even when the session is clearly degrading.

**Detection**: Claude starts repeating itself. Responses become less focused. You're scrolling through old conversation to find what was decided.

**Prevention**: Checkpoint frequently with `/update-dev-docs`. Clear proactively. A fresh session with a good handoff prompt is better than a bloated session with degraded focus.

## Using This List

Don't memorize these. Instead:

1. **Review before starting a new feature** — remind yourself what to watch for
2. **Reference during code review** — check if any antipatterns crept in
3. **Add your own** — every project discovers patterns specific to its domain. When you find one, add it here
