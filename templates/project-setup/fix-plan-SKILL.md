# /fix-plan Skill — Starter Template

Copy to `.claude/skills/fix-plan/SKILL.md` and customize.

---

```yaml
---
name: fix-plan
description: Create a fix plan from zen-audit and zen-review findings. Reads handoff reports, triages and deduplicates, creates fix docs inside the existing feature folder.
argument-hint: Feature name (e.g., "auth-module")
---
```

```markdown
Create a combined fix plan from audit and review findings for: $ARGUMENTS

## Process

### Step 1: Locate Reports
Find latest reports in handoff/ matching the feature name:
- handoff/<feature>-audit-*.md
- handoff/<feature>-review-*.md

### Step 2: Read Feature Context
Read ALL files in docs/plan/active/<feature>/

### Step 3: Triage Findings
For each finding:
1. Classify: CRITICAL / MAJOR / MINOR
2. Deduplicate across audit and review reports
3. Validate against current codebase
4. Categorize: Fix now / Intentional / Defer to backlog
5. Present triage to user — wait for approval

### Step 4: Create Fix Documents
After approval, create in docs/plan/active/<feature>/:
- audit-review-fix-plan.md — triage table + fix approach
- audit-review-fix-context.md — combined findings summary
- audit-review-fix-tasks.md — fix checklist (Part > Section > Task)

### Step 5: Create Backlog Items
For deferred findings, create docs/plan/backlog/<item>.md

## Rules
- Every finding classified (none silently dropped)
- Fix plan traceable to original report findings
- Fixes ordered by dependency (structural before quality)
- Testing strategy included

## Additional Context: $ARGUMENTS
```
