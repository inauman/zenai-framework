# Testing Standard

Testing validates behavior, not implementation. Tests are executable specifications that document what the system does and catch regressions when it changes.

## Core Principles

### Test Pyramid
- **Foundation**: Many fast, focused unit tests
- **Middle**: Fewer integration tests for component interaction
- **Top**: Minimal end-to-end tests for critical user journeys
- **Balance**: Optimize for speed, reliability, and maintainability

### Shift-Left Testing
- Test as early as possible in the development cycle
- Prevent defects rather than just detect them
- Integrate testing into every phase (not just before deployment)
- Use testing as quality gates (validation checklist)

### Tests as Documentation
- Tests serve as executable specifications
- Test names describe behavior, not implementation
- New team members (and AI agents) understand the system by reading tests
- When docs and tests disagree, the test is the source of truth

## What to Test

### Always Test
- Critical business logic (anything that handles money, data, decisions)
- Error paths (what happens when things fail?)
- Public API contracts (what consumers depend on)
- Security-sensitive operations (auth, encryption, validation)

### Test Strategically
- Edge cases for complex algorithms
- Integration points between components
- State transitions (especially in workflows and ceremonies)
- Concurrent operations (race conditions, deadlocks)

### Don't Over-Test
- Don't test private implementation details
- Don't test framework behavior (test YOUR code)
- Don't chase 100% coverage — cover critical paths at 90%+
- Don't test what the compiler already guarantees (type safety)

## Test Organization

```
tests/
├── unit/           # Fast, isolated, no external dependencies
├── integration/    # Component interaction, may use test databases
└── e2e/            # Full user journeys, may use real services
```

- Unit tests: next to the code they test (Rust: `#[cfg(test)]` module)
- Integration tests: in a separate `tests/` directory
- E2E tests: separate directory, may need infrastructure setup

## Testing Anti-Patterns

- **Mirror tests**: Tests that mirror implementation instead of testing behavior
- **Flaky tests**: Tests that pass sometimes and fail sometimes — fix or delete, never ignore
- **Test debt**: Accumulating skipped or disabled tests — treat as tech debt
- **Testing only happy paths**: Missing error scenarios, edge cases, and failure modes
- **Cargo cult coverage**: Achieving high coverage numbers without testing meaningful behavior

## Validation Command

Every project should have a single command that validates everything:

```bash
make validate    # or: npm test, cargo test --workspace, etc.
```

Run this before every commit, handoff, and verification phase. If it doesn't pass, the work isn't done.

## Integration with Workflow

- **During execution**: Run tests after each task. Tests go in the same Part as the code they validate.
- **Before verification**: `make validate` must pass before invoking zen-audit/zen-review
- **During code review**: Verify test coverage, test quality, and missing scenarios
- **Validation checklist**: "Tests pass" is a mandatory checkbox
