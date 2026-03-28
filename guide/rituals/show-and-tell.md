# Show and Tell

The final quality gate before marking a feature complete. The engineer walks the stakeholder through completed work interactively — demonstrating features, explaining decisions, running tests live, and surfacing any remaining gaps.

## When to Use

- After code review is complete
- Before archiving a feature from `active/` to `archive/`
- Before any stakeholder sign-off

## Process

1. **Prepare**: Read the zen-audit report (`handoff/<feature>-audit-*.md`) for any flagged items. Review the feature's dev-docs (plan, context, tasks).

2. **Scope & Overview**: Present what was built — features, architecture, key files changed. One section at a time.

3. **Design Decisions**: Walk through trade-offs, alternatives considered, and why this approach was chosen. Reference ADRs if created.

4. **Interactive Test Execution**: Run tests live. Execute one command at a time. Explain what you expect before running. Note what actually happened.

5. **Test Coverage**: Show test count, coverage of critical paths, and any gaps. Gaps are fine if documented — hiding them is not.

6. **Tech Debt & TODOs**: Scan for TODO/FIXME markers. Categorize: must-fix vs. acceptable vs. tracked in backlog. Cross-reference against tasks.md.

7. **Security**: Review key material handling, error messages (no sensitive data), input validation, dependency audit results.

8. **Documentation Sync**: Verify CLAUDE.md updated, domain docs current, ADRs written, CLI guides updated, code comments accurate.

9. **Summary & Sign-off**: Recap findings, list any follow-up actions, get stakeholder approval to archive.

## Rules

- **One section at a time** — pause after each for questions
- **Execute one command at a time** during testing — never batch
- **Explain before running** — state what you expect, then verify
- **Be honest about gaps** — the stakeholder should hear problems from you, not discover them later
- **Only mark complete after Show & Tell** — this is the gate, not a formality

## Anti-Patterns

- Skipping the demo and just describing what was built
- Batching all tests into one "everything passes" statement
- Hiding tech debt or deferred items
- Rushing through without pausing for questions
- Presenting without having read the audit report first

## Success Criteria

- Work is demonstrated live, not described
- Decisions are explained with rationale
- Tests run successfully in front of the stakeholder
- Gaps are acknowledged and tracked
- Stakeholder has opportunity to ask questions at every stage
- Feature is only archived after approval

> "If you can't show it, it's not done."
