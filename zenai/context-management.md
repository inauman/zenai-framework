# Context Management - The ZenAI Approach

## Overview

Context Management is the core innovation that enables sub-2-minute AI agent onboarding. This guide shows you how to structure, maintain, and evolve project context for effective Agent-Driven Development.

## The Context Reconstruction Problem

Every new AI session faces two expensive phases:

### Static Context (15-20 minutes)
- System architecture and patterns
- Technology stack and constraints
- Coding standards and conventions
- Project structure and organization

### Dynamic Context (10-15 minutes)
- Current implementation progress
- Recent decisions and rationale
- Active issues and blockers
- Immediate priorities

**Total Cost**: 25-35 minutes creates "Chat Reset Dread" - developers avoid fresh sessions, leading to degraded long-running chats.

## The Three-Layer Solution

### Layer 1: Master Context (2 minutes)
```markdown
/context.md
├── Project overview
├── Current state snapshot
├── Navigation to domains
└── Essential commands
```

**Purpose**: Quick orientation for any agent
**Content**: High-level project state, key decisions, navigation map

### Layer 2: Domain Contexts (3-5 minutes)
```markdown
/docs/[domain]/context.md
├── Domain-specific patterns
├── Current work items
├── Recent decisions
└── References to details
```

**Purpose**: Focused context for specialized work
**Domains**: architecture, product, engineering, operations

### Layer 3: Detailed Documentation (on-demand)
```markdown
/docs/[domain]/detailed/
├── Full specifications
├── Implementation guides
├── Historical decisions
└── Research findings
```

**Purpose**: Deep reference when needed
**Access**: Only when referenced from context layers

## Implementation Guide

### Step 1: Create Master Context

Create `/context.md` with this template:

```markdown
# [Project Name] - Master Context

## What This Is
[2-3 sentence project description]

## Current State
- ✅ [Completed milestone]
- 🚧 [In progress]
- 📋 [Next priority]

## Navigation Map
| Domain | Location | Purpose |
|--------|----------|---------|
| Architecture | `/docs/architecture/context.md` | System design |
| Product | `/docs/product/context.md` | Requirements |
| Engineering | `/docs/engineering/context.md` | Implementation |

## Tech Stack
- Frontend: [stack]
- Backend: [stack]
- Infrastructure: [stack]

## Essential Commands
- `make test` - Run tests
- `make build` - Build project
[other key commands]
```

### Step 2: Create Domain Contexts

For each domain, create `/docs/[domain]/context.md`:

```markdown
# [Domain] Context

## Current Focus
- Active: [current work]
- Priority: [immediate focus]
- Blocked: [issues]

## Key Patterns
- [Pattern 1]: [description]
- [Pattern 2]: [description]

## Recent Decisions
- [Date]: [Decision] - [Rationale]

## References
- Details: [link to specs]
- Standards: [link to guidelines]
```

### Step 3: Implement Evolution Chains

Track decision evolution without noise:

```markdown
/docs/evolution/[feature].md
├── Current State (what's active)
├── History (v1 → v2 → v3)
├── Key Decisions (why current)
└── Preserved Knowledge (insights)
```

## Maintenance Protocols

### Daily (5 minutes)
```bash
1. Update current work status
2. Note new blockers
3. Adjust priorities
4. Commit changes
```

### Weekly (15 minutes)
```bash
1. Archive completed items
2. Update domain contexts
3. Review freshness
4. Clean stale info
```

### Sprint (30 minutes)
```bash
1. Full context audit
2. Update evolution chains
3. Archive sprint artifacts
4. Refactor if needed
```

## Context Quality Checklist

### Before Starting Work
- [ ] Read master context (2 min)
- [ ] Read domain context (3-5 min)
- [ ] Check current priorities
- [ ] Note known blockers

### During Work
- [ ] Update task progress
- [ ] Document decisions
- [ ] Flag new issues
- [ ] Prepare handoffs

### After Work
- [ ] Update status
- [ ] Archive completed
- [ ] Update contexts
- [ ] Commit changes

## Smart References

Use contextual references:

```markdown
**Architecture**: See [System Design](../architecture/system.md)
_Updated: 2024-01-15 | Scope: API design | Status: Stable_
```

## Archival Strategy

```
Still needed?
├── YES → Update in place
└── NO → Historical value?
    ├── YES → Archive with metadata
    └── NO → Delete (rare)
```

## Success Metrics

| Metric | Target | Measure |
|--------|--------|---------|
| Context Load Time | <2 minutes | Time to productive work |
| Freshness | >95% accuracy | Alignment with reality |
| Handoff Success | >90% | First-attempt success |

## Best Practices

### DO
- Keep concise and scannable
- Include "why" not just "what"
- Date significant updates
- Link to details
- Update immediately

### DON'T
- Duplicate specifications
- Include code blocks
- Leave outdated info
- Create deep nesting (>3)
- Mix current/historical

## Integration with Agent Teams

Each agent has context responsibilities:

- **ZenMaster**: Maintains master context
- **Architects**: Update design contexts
- **Engineers**: Update implementation
- **QA**: Update test coverage
- **Product**: Update requirements

## Advanced Patterns

### Multi-Repository
- Master context in primary repo
- Repo-specific contexts
- Cross-references
- Sync during planning

### Long-Running Projects
- Quarterly audits
- Annual consolidation
- Evolution summaries
- Context refactoring

### Team Scaling
- Domain owners
- Update protocols
- Sync meetings
- Automated checks

---

*Context Management is a living discipline. Keep it current, concise, and correct.*