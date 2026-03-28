# Workflow Walkthrough

A complete end-to-end example showing one full cycle of the ZenAI workflow. This uses a generic "user authentication" feature as the example — substitute your own feature and domain skills.

## Setup

Assume you have a project with:
- ZenAI project-level skills installed (`/dev-docs`, `/update-dev-docs`, `/add-backlog`, `/fix-plan`)
- Verification agents configured (`zen-audit`, `zen-review`)
- At least one domain skill (e.g., `/d-backend`)

## Phase 1: Plan

Start Claude Code in your project directory.

```
You: /plan
     I need to implement user authentication with JWT tokens and
     password hashing. Support login, register, and token refresh.

Claude: [enters plan mode, researches codebase, proposes approach]
        [discusses with you: session-based vs. JWT? bcrypt vs. argon2?]
        [you iterate on the plan together]

You: Looks good. Let's go with JWT + argon2.
     [Claude produces the plan]

You: /dev-docs auth-system
     [Claude creates docs/plan/active/auth-system/]
     [Three files: plan.md, context.md, tasks.md]

You: /update-dev-docs
     [Claude captures insights from planning discussion]
     [Generates handoff prompt in context.md]

You: /clear
```

**Result**: `docs/plan/active/auth-system/` with 3 files + handoff prompt.

## Phase 2: Execute

New session. Paste the handoff prompt.

```
You: [paste handoff prompt from context.md]

Claude: [reads all referenced files, picks up full context]
        Starting with Task 1.1.1: Create User model...

[... work through tasks, commit frequently ...]

You: [after a breakthrough] Good catch on the token rotation —
     let's capture that.
     /update-dev-docs
     [Claude checkpoints progress + captures the token rotation insight]

[... continue working ...]

You: [context getting long]
     /update-dev-docs
     /clear
     [paste new handoff prompt, continue in fresh session]

[... complete all tasks ...]
```

**Result**: All tasks in tasks.md marked `[x]`. Code committed.

## Phase 3: Verify

Open two additional terminals.

```
Terminal 2:
You: @zen-audit "Audit auth-system implementation"

Terminal 3:
You: @zen-review "Review auth-system — reference d-backend. Focus on security."
```

Both agents run independently (15-40 minutes each):
- zen-audit reads tasks.md, greps codebase, verifies each `[x]` task
- zen-review reads code changes, applies security and architecture checklists

**Result**: Two reports in `handoff/`:
- `handoff/auth-system-audit-0328-1.md`
- `handoff/auth-system-review-0328-1.md`

## Phase 4: Fix

Back in Terminal 2 (or any terminal where an agent finished):

```
You: /fix-plan auth-system
     [Claude reads both reports, deduplicates, presents triage]

Claude: Found 12 findings total (3 overlap):
        Fix now: 6 (2 critical, 4 major)
        Intentional: 2 (documented design choices)
        Defer to backlog: 1 (nice-to-have refactor)

        [Shows triage table]

You: Agree with triage. The rate limiter deferral is fine for now.

Claude: [Creates fix docs in docs/plan/active/auth-system/]
        - audit-review-fix-plan.md
        - audit-review-fix-context.md
        - audit-review-fix-tasks.md

You: /plan
     [Review fix approach, approve]

Claude: [Exits plan mode, executes fixes]
        [Works through fix tasks: add missing test, fix token
         validation edge case, add rate limit TODO to backlog]
```

**Result**: All critical and major findings fixed. One item deferred to backlog.

## Phase 5: Code Review

```
You: /code-review
     Start by reading handoff/auth-system-review-0328-1.md.
     Then review the recent changes.

Claude: [Loads code-review skill, reads zen-review report]
        [Walks through findings interactively]
        [You discuss each finding, fix remaining issues]

You: The password hashing timing looks suspicious —
     can you verify it's constant-time?

Claude: [Investigates, confirms argon2 handles this internally]
```

## Phase 6: Show & Tell

```
You: /show-n-tell
     Read handoff/auth-system-audit-0328-1.md before starting.

Claude: [Loads show-n-tell skill]

        Section 1: Scope & Overview
        We implemented JWT authentication with argon2 password
        hashing. Three endpoints: POST /register, POST /login,
        POST /refresh...

        [Pauses for questions]

You: How does token refresh work when the original is expired?

Claude: [Explains, shows code, runs test]

        Section 2: Design Decisions
        We chose argon2 over bcrypt because...
        [Continues through all sections, one at a time]
```

## Phase 7: Archive

```bash
# Move completed feature to archive
mv docs/plan/active/auth-system/ docs/plan/archive/

# Clean up ephemeral reports
rm handoff/auth-system-*

# Optional: retrospective
You: Let's do a quick retrospective on the auth-system work.
     [5-question retrospective]
     /capture
     [Persist key insights into permanent project docs]
```

## Timeline

| Phase | Duration | Notes |
|---|---|---|
| Plan | 1-3 hours | Interactive, may span multiple sessions |
| Execute | Hours to days | Depends on scope, checkpoint frequently |
| Verify | 15-40 min | Parallel, fire-and-forget |
| Fix | 30 min - 2 hours | Depends on findings |
| Code Review | 30 min - 1 hour | Interactive |
| Show & Tell | 30 min - 1 hour | Interactive, section by section |

Total overhead from ZenAI ceremonies: ~2-4 hours. Time saved from catching issues early, preserving context, and avoiding repeated explanations: significantly more.
