# Dev-Docs Tasks Template

Use this template for `[feature]-tasks.md` in `docs/plan/active/<feature>/`.

---

```markdown
# Tasks: [Feature Name]
**Last Updated**: YYYY-MM-DD

## Status Markers
[ ]  - Pending (not started)
[x]  - Complete (verified working)
[~]  - In progress (partially done)
[!]  - Blocked (needs resolution)

## Task Hierarchy

Part 1: [Major Phase/Milestone]
  Section 1.1: [Logical Grouping]
    Task 1.1.1: [Specific deliverable] [ ]
    Task 1.1.2: [Unit test for above] [ ]

  Section 1.2: [Another Grouping]
    Task 1.2.1: [Specific deliverable] [ ]
    Task 1.2.2: [Specific deliverable] [ ]

  Section 1.3: Verification
    Task 1.3.1: Integration test [ ]
    Task 1.3.2: Full build verification [ ]

Part 2: [Next Phase/Milestone]
  Section 2.1: [Logical Grouping]
    Task 2.1.1: [Specific deliverable] [ ]
    Task 2.1.2: [Specific deliverable] [ ]

  Section 2.2: Verification
    Task 2.2.1: Integration test [ ]
    Task 2.2.2: End-to-end test [ ]
```

## Rules

- **Max 3 levels** of nesting: Part > Section > Task
- **Tests go close to the code they test** (not in a separate testing Part)
- **Last section of each Part MUST be Verification** (integration tests, build checks)
- **Each task is atomic** and independently verifiable
- **Tasks are deliverable-level** (not commit-level) so auditors can verify completion
