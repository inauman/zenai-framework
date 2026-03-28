# /update-dev-docs Skill — Starter Template

Copy to `.claude/skills/update-dev-docs/SKILL.md` and customize.

---

```yaml
---
name: update-dev-docs
description: Checkpoint session progress and capture knowledge for seamless session continuity. Run anytime — mid-session, before /clear, before ending a session.
argument-hint: Optional — specific feature name or focus area
---
```

```markdown
Checkpoint current session and capture knowledge for: $ARGUMENTS

## When to Run
- Before every /clear (non-negotiable)
- After breakthroughs or important discoveries
- Before switching topics
- Before ending a session
- After major milestones

## Required Updates

### 1. Update Task Progress
Update tasks.md with current status ([ ] → [x], [~], [!]).

### 2. Capture Session Knowledge
Update context.md with:

**Required Reading List** — files for next session, in order
**External References** — URLs consulted and why
**Session Insights** — non-obvious discoveries
**Design Decisions** — choices made and WHY
**Corrections & Gotchas** — mistakes caught and corrected
**Process Insights** — testing steps, reset procedures, tool usage
**Current State** — what's working, in progress, blocked

### 3. Generate Session Handoff Prompt
Write a ready-to-paste prompt as the LAST section of context.md.

The prompt must be:
- Self-contained (assumes zero prior context)
- Copy-pasteable into a new session
- Under 100 lines
- Includes ALL insights and corrections

**Test:** "If I read only this prompt and the referenced files, could I continue without repeating anything?"
```
