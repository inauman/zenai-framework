# Handoff Prompt Template

This is a standalone template for the session handoff prompt. In practice, `/update-dev-docs` generates this as the last section of `context.md`. Use this template when writing the prompt manually.

---

```markdown
## Session Handoff Prompt

> Paste this into a new session to continue where we left off.

You are continuing work on [FEATURE] for [PROJECT].

**Read these files first (in order):**
1. `CLAUDE.md` — project rules and architecture
2. `docs/plan/active/[feature]/context.md` — session knowledge and decisions
3. `docs/plan/active/[feature]/tasks.md` — current task status
4. `docs/plan/active/[feature]/plan.md` — implementation approach
5. `[source-file-1]` — [why this file matters]
6. `[source-file-2]` — [why this file matters]

**Key insights you MUST know (do NOT rediscover these):**
- [Insight 1: the non-obvious thing that took time to figure out]
- [Insight 2: an API quirk or integration discovery]
- [Insight 3: an architectural decision and the reasoning]

**Corrections — do NOT repeat these mistakes:**
- [Wrong approach → correct approach]
- [Wrong assumption → what actually works]

**Current state:**
- Working: [what's functional and tested]
- In progress: [what's partially done, exact file/function]
- Blocked: [what needs resolution]
- Uncommitted changes: [any pending work not yet committed]

**Your next steps:**
- Task [X.Y.Z] from tasks.md: [description — first thing to do]
- Task [X.Y.Z+1]: [description — then this]

**Process reminders:**
- [Testing guide to follow: docs/guides/...]
- [Reset steps: how to set up test environment]
- [Build command: make validate / npm test / etc.]

**External references to consult:**
- [URL 1] — [why it's needed]
- [URL 2] — [why it's needed]
```

## Quality Checklist

A good handoff prompt:

- [ ] Is self-contained (assumes zero prior context)
- [ ] Can be pasted directly into a new session
- [ ] Includes ALL insights from the session (not just the obvious ones)
- [ ] Includes ALL corrections (prevents repeated mistakes)
- [ ] Lists files in reading order (most important first)
- [ ] Specifies the exact next step (not vague "continue working")
- [ ] Includes process reminders (testing steps, build commands)
- [ ] Is under 100 lines (dense and actionable, not a novel)

**The test:** If you read only this prompt and the files it references, could you continue the work without asking the user to repeat anything?
