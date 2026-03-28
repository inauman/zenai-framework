# Skill Template

Copy this structure to create a new skill.

## Directory Structure

```
.claude/skills/<skill-name>/
├── SKILL.md          # Required, under 500 lines
└── references/       # Optional, for detailed reference material
    ├── topic-a.md
    └── topic-b.md
```

## SKILL.md Template

```yaml
---
name: <skill-name>
description: <One-line description. This drives when Claude auto-suggests the skill. Be specific about when to use it.>
argument-hint: <Optional hint shown in autocomplete, e.g., "task description or question">
allowed-tools: <Optional tool restriction, e.g., "Read, Glob, Grep">
---
```

```markdown
<objective>
What this skill provides and when to use it.
</objective>

<quick_start>
The first thing to do when this skill is invoked.
1. Step one
2. Step two
3. Step three
</quick_start>

<core_content>
The main knowledge this skill provides.
Keep this section focused and actionable.
</core_content>

<when_to_consult_references>
**Need detailed X?** -> references/topic-a.md
**Need detailed Y?** -> references/topic-b.md
</when_to_consult_references>

<gotchas>
Known issues, corrections, and non-obvious behaviors.
These are the highest-value items — they prevent mistakes.
</gotchas>

<validation>
How to verify work done with this skill's guidance.
</validation>
```

## Guidelines

- **Under 500 lines** for SKILL.md — it loads into context when invoked
- **References load on-demand** — Claude reads them only when following a link
- **Description is critical** — it determines when Claude auto-suggests the skill
- **No emojis** unless explicitly requested
- **Generalize** — skills should be reusable, not tied to one feature
- **Set `disable-model-invocation: true`** only for skills with side effects (deploys, destructive ops)

## Naming Convention

| Prefix | Purpose | Examples |
|---|---|---|
| `a-` | Utility (anytime helpers) | `a-capture`, `a-deep-research` |
| `b-` | Engineering quality (workflow ceremonies) | `b-code-review`, `b-show-n-tell` |
| `d-` | Domain expertise (project-specific) | `d-graphql`, `d-postgres`, `d-swift` |
| (none) | Project-level workflow skills | `dev-docs`, `update-dev-docs`, `fix-plan` |
