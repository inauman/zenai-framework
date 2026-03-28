# Adoption Guide

Set up ZenAI on your project in 30 minutes.

## Prerequisites

- Claude Code (or any AI coding assistant with skills and subagent support)
- A git repository for your project
- Familiarity with your project's build and test commands

## Step 1: Create Project Structure (5 minutes)

Create the directories ZenAI expects:

```bash
mkdir -p docs/plan/active docs/plan/archive docs/plan/backlog
mkdir -p handoff
echo "handoff/" >> .gitignore
```

## Step 2: Set Up Project-Level Skills (10 minutes)

Copy the starter skills from `templates/project-setup/` into your project's `.claude/skills/` directory:

```bash
mkdir -p .claude/skills/create-dev-docs .claude/skills/update-dev-docs
mkdir -p .claude/skills/add-backlog .claude/skills/fix-plan

cp templates/project-setup/create-dev-docs-SKILL.md .claude/skills/create-dev-docs/SKILL.md
cp templates/project-setup/update-create-dev-docs-SKILL.md .claude/skills/update-dev-docs/SKILL.md
cp templates/project-setup/add-backlog-SKILL.md .claude/skills/add-backlog/SKILL.md
cp templates/project-setup/fix-plan-SKILL.md .claude/skills/fix-plan/SKILL.md
```

**Customize each skill** for your project:
- Update file paths (docs directory structure, build commands)
- Add project-specific context references (your CLAUDE.md, ADR directory, etc.)
- Adjust the task hierarchy template if you prefer a different structure

## Step 3: Set Up Verification Agents (5 minutes)

Create two agents in your global `.claude/agents/` directory (or project-level):

```bash
mkdir -p .claude/agents
```

**zen-audit.md** — Copy from `templates/agent-template.md` and customize:
- Update the build/test command (e.g., `make test`, `npm test`, `cargo test`)
- Set the model to your most capable option
- Keep tools as: Read, Grep, Glob, Bash, Write

**zen-review.md** — Copy from `templates/agent-template.md` and customize:
- Add your code review and architecture skills to the `skills:` field
- Add instructions for loading your domain skills on-demand
- Keep the same tool restrictions

## Step 4: Create Your First Domain Skill (5 minutes)

Pick your project's primary technology domain and create a skill for it:

```bash
mkdir -p .claude/skills/d-<your-domain>
```

Write a `SKILL.md` (see `templates/skill-template.md`) that captures:
- Key concepts and terminology
- Common commands and APIs
- Architecture patterns specific to your domain
- Known gotchas and corrections
- Links to official documentation

Keep it under 500 lines. Move detailed reference material to a `references/` subdirectory.

## Step 5: Write Your CLAUDE.md (5 minutes)

If you don't have one, create a `CLAUDE.md` at your project root (see `templates/project-setup/CLAUDE.md` for a starter). Include:
- Project overview and architecture
- Build and test commands
- Critical rules (what to never do)
- Directory structure explanation

## Step 6: Run Your First Cycle

### Plan
```
/plan
"I want to implement <feature>. Research the codebase and propose an approach."
```

Review and iterate. When satisfied:
```
/create-dev-docs <feature-name>
/update-dev-docs
/clear
```

### Execute
Paste the handoff prompt. Work through tasks:
```
# When context gets long or before switching topics:
/update-dev-docs
/clear
# Paste handoff prompt, continue
```

### Verify
```
Terminal 2: @zen-audit "Audit <feature>"
Terminal 3: @zen-review "Review <feature> — reference d-<your-domain>"
```

### Fix
```
/fix-plan <feature>
/plan
# Review triage, approve, execute fixes
```

### Review + Demo
```
/code-review
# Work through findings
/show-n-tell
# Demo to stakeholder
```

### Archive
```bash
mv docs/plan/active/<feature>/ docs/plan/archive/
rm handoff/<feature>-*
```

## What to Do Next

After your first cycle:

1. **Add more domain skills** — one per technology domain you work with frequently
2. **Tune your verification agents** — adjust based on what they catch vs. miss
3. **Capture insights** — use `/capture` after deep technical discussions
4. **Customize rituals** — adapt show-and-tell and code review to your team's style
5. **Read the insights** — `guide/insights/` explains the reasoning behind the framework

## Incremental Adoption

You don't have to adopt everything at once. Start with:

1. **Week 1**: `/create-dev-docs` + `/update-dev-docs` — just the session continuity system
2. **Week 2**: Add `@zen-audit` — catch the self-praise problem
3. **Week 3**: Add domain skills — encode your project's knowledge
4. **Week 4**: Full workflow with `/fix-plan`, `/code-review`, `/show-n-tell`

Each addition is independent and provides value on its own. The full workflow emerges naturally as you add pieces.
