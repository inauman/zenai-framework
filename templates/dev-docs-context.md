# Dev-Docs Context Template

Use this template for `[feature]-context.md` in `docs/plan/active/<feature>/`. This is the most critical file for session continuity — update it every session.

---

```markdown
# Context: [Feature Name]
**Last Updated**: YYYY-MM-DD

## Required Reading List
Files to read at the start of every session, in order:
1. `CLAUDE.md` — project rules and architecture
2. `docs/plan/active/<feature>/context.md` — this file
3. `docs/plan/active/<feature>/tasks.md` — task status
4. `docs/plan/active/<feature>/plan.md` — approach
5. [Other critical source files]

## External References
URLs and docs consulted — include why each is relevant:
- [URL] — [why it matters]

## Session Insights
Non-obvious discoveries that can't be derived from code:
- [Insight + reasoning]

## Design Decisions & Rationale
Choices made and WHY:
- [Decision: what was chosen, what was rejected, why]

## Corrections & Gotchas
Things that were wrong and corrected:
- [Mistake → correct approach]

## Current State
- Working: [what's functional]
- In progress: [what's partially done]
- Blocked: [what's stuck and why]

## Files Modified
[Key files changed this session and why]

## Session Handoff Prompt

> Paste this into a new session to continue where we left off.

You are continuing work on [feature] for [project].

**Read these files first (in order):**
1. [ordered file list]

**Key insights you MUST know:**
- [insight 1]
- [insight 2]

**Corrections — do NOT repeat these mistakes:**
- [correction 1]

**Current state:**
- [summary]

**Next steps:**
- [task X.Y.Z — first thing to do]
```
