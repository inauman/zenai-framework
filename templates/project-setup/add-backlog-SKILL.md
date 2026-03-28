# /add-backlog Skill — Starter Template

Copy to `.claude/skills/add-backlog/SKILL.md` and customize.

---

```yaml
---
name: add-backlog
description: Quickly capture a backlog item mid-session without interrupting flow. Creates a lightweight doc in docs/plan/backlog/.
argument-hint: Brief title or description of the backlog item
---
```

```markdown
Capture a backlog item quickly and return to current work.

## Process
1. Derive a filename from the argument (lowercase, hyphens)
2. Check for duplicates in docs/plan/backlog/
3. Write the file using the template below
4. Confirm with one-line summary, then stop

## Template

# [Title]

**Origin**: [Phase/session that surfaced this]
**Date**: YYYY-MM-DD
**Priority**: Low | Medium | High

## What
[1-3 sentences: what needs to be done]

## Why
[1-3 sentences: why it matters]

## Scope
[Rough estimate: areas affected, how big]

## Notes
[Additional context, links, related items]

## Rules
- Keep it lightweight — 10-20 lines ideal
- Capture the "why" — the title alone won't be enough later
- Include origin — helps prioritize
- Return to work immediately — this should take 30 seconds

## Additional Context: $ARGUMENTS
```
