# Retrospective

A focused learning ritual after completing a feature or milestone. Captures what worked, what failed, and what to change — then persists the insights so they survive across sessions.

## When to Use

- After completing a feature (before archiving)
- After a significant milestone within a feature
- After a particularly difficult debugging session
- Before starting a new feature (apply learnings from the last one)

## The 5-Question Template

```markdown
# Retrospective: [Feature/Milestone Name]
**Date**: YYYY-MM-DD

## 1. What Went Well
- [Specific success — what approach worked and why]
- [Another success — what tool/pattern/decision paid off]

## 2. What Went Wrong
- [Specific failure — what didn't work and what happened]
- [Another issue — time wasted, wrong approach taken]

## 3. How to Prevent Recurrence
- [Concrete action: add a check, update a doc, create a skill]
- [Process change: checkpoint more often, test earlier]

## 4. How Can the Human Help
- [What guidance would have been useful earlier]
- [What context was missing that caused wrong turns]
- [What decisions should the human make sooner]

## 5. Key Insights Worth Preserving
- [Architectural insight that should become permanent knowledge]
- [API quirk or gotcha that would save time in the future]
- [Process improvement that should be adopted going forward]
```

## Process

1. **Run the retrospective** — answer all 5 questions honestly. Don't skip "what went wrong."
2. **Identify actionable items** — for each answer, is there something concrete to do?
3. **Persist insights** — use `/capture` to write key insights into permanent project docs (ADRs, learning docs, guides). Don't let them live only in this retrospective file.
4. **Update the framework** — if you discovered a new antipattern, add it to your project's conventions. If a skill was missing, create it.

## Rules

- **Honesty over comfort** — a retrospective that says "everything went great" is useless
- **Specifics over generalities** — "we should test more" is not actionable. "We should test the hardware wallet flow on signet before mainnet" is.
- **Persist the valuable parts** — insights in a retrospective file that nobody reads again are wasted. Extract and write to permanent docs.
- **Keep it short** — 15-20 minutes. If it takes longer, you're going too deep.

## Anti-Patterns

- Writing a retrospective but not acting on it
- Only listing positives (self-praise disguised as reflection)
- Being vague ("communication could be better")
- Not persisting insights into permanent docs
- Skipping the retrospective because "we're behind schedule"

## Integration with the Workflow

The retrospective fits naturally at the end of the workflow, after Show & Tell:

```
... → /show-n-tell → retrospective → /capture (persist insights) → archive
```

Alternatively, run a mini-retrospective after each Part completion within a feature, not just at the end.
