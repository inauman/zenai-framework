# Validation Checklist

A ritualized pause before marking work complete. Not a blocker — a safeguard for quality, safety, and alignment.

## When to Use

- Before marking a task `[x]` in tasks.md
- Before committing code
- Before handing off to verification agents
- During code review

## Implementation Validation

- [ ] Code compiles/builds without errors
- [ ] Linting passes (e.g., clippy, eslint)
- [ ] Tests pass (unit, integration, E2E as applicable)
- [ ] No TODO/FIXME markers in the critical path (or they're tracked in tasks.md)
- [ ] Security implications reviewed for sensitive logic

## Cognitive Validation

- [ ] Implementation aligns with the agreed plan (check plan.md)
- [ ] Design choices are explained in commit messages or ADRs
- [ ] Threat mitigation documented (if applicable)
- [ ] Edge cases considered and handled (or explicitly deferred with rationale)

## Hygiene & Commit

- [ ] `git status` is clean (no untracked or leftover files)
- [ ] Commit uses conventional format: `feat(scope): description`
- [ ] Commit is atomic, focused, and meaningful
- [ ] Task marked complete in tasks.md
- [ ] Build/validation command passes (e.g., `make validate`, `npm test`)

## Documentation

- [ ] Existing docs updated (don't create new files unnecessarily)
- [ ] CLAUDE.md updated if rules or architecture changed
- [ ] ADR created if a significant architectural decision was made
- [ ] API changes reflected in relevant guides

## Communication

- [ ] Any blockers or concerns raised to the stakeholder
- [ ] Follow-up items captured (in tasks.md or backlog)
- [ ] Context.md updated with session knowledge

## The Reflection Test

> "Would I trust this output if it held my secrets?"

If you're rushing to check off a task, pause and run through this checklist. The few minutes it takes prevent the hours of debugging that sloppy completion causes.
