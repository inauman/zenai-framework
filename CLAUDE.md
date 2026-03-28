# CLAUDE.md

## Repository Overview

ZenAI Framework is a documentation-only project — no application code. It provides a battle-tested framework for AI-assisted software development on long-running, complex projects.

## Structure

```
guide/          Core framework docs (numbered 01-05 for reading order)
guide/rituals/  4 surviving ceremonies (show-and-tell, retrospective, validation, antipatterns)
guide/standards/ 4 technical standards (security, testing, logging, error-handling)
guide/insights/  Hard-won lessons (same-mind-self-praise, skills-vs-subagents, what-didnt-work)
templates/       Skill, agent, and dev-docs templates + project-setup starter files
examples/        End-to-end workflow walkthrough
archive/v1/      Previous framework version (preserved for reference)
```

## Key Concepts

- **Skills**: Knowledge loaded into default agent for interactive work
- **Verification Agents**: zen-audit (task auditor) and zen-review (code reviewer) — fire-and-forget with isolated context
- **Dev-docs**: 3-file system (plan.md, context.md, tasks.md) for session continuity
- **Handoff prompts**: Generated before every /clear to preserve session knowledge

## Development

This is a docs-only project. To work on it:

```bash
# Local development with MkDocs
pip install -r requirements.txt
mkdocs serve                    # Preview at http://localhost:8000

# Build for deployment
mkdocs build                    # Output to site/
```

## Guidelines

- No BarqPay or project-specific references — this is a generalized framework
- All examples should be generic (REST API, web app, backend service)
- Keep files under 500 lines
- No emojis in content
- Principles first, tools second (Claude Code is the reference implementation, not the only option)
