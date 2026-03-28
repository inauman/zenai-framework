# /create-dev-docs Skill — Starter Template

Copy to `.claude/skills/create-dev-docs/SKILL.md` and customize.

---

```yaml
---
name: create-dev-docs
description: Create a comprehensive plan with structured task breakdown. If no argument, auto-read Claude's plan file from ~/.claude/plans/ as input.
argument-hint: Feature name or description
---
```

```markdown
Create a comprehensive, actionable plan for: $ARGUMENTS

## Instructions

### Step 0: Auto-Read Plan (if no arguments)
If $ARGUMENTS is empty:
1. Look for the most recent plan file in ~/.claude/plans/
2. Use that as the basis for dev-docs

### Step 1: Analyze Context
1. Analyze the request scope
2. Read existing codebase
3. Read CLAUDE.md and relevant docs

### Step 2: Create Structured Plan
Generate a plan with:
- Executive Summary
- Current State Analysis
- Implementation Phases
- Detailed Tasks (Part > Section > Task hierarchy)
- Risk Assessment

### Step 3: Create Files
Create directory: docs/plan/active/[feature-name]/

Generate three files:
1. [feature]-plan.md — comprehensive plan
2. [feature]-context.md — key context for continuation
3. [feature]-tasks.md — checklist with Part > Section > Task

### Task Rules
- Max 3 levels: Part > Section > Task
- Last section of each Part = Verification
- Status markers: [ ] pending, [x] complete
- Each task atomic and independently verifiable
```
