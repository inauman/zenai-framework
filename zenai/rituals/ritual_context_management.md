# Context Management Ritual

## Purpose

Maintain fresh, accurate, and accessible project context that enables sub-2-minute AI agent onboarding and prevents the "Context Reconstruction Problem."

## When to Use This Ritual

### Immediate Triggers
- Starting a new project
- Onboarding new AI agents
- Major architecture decisions
- Sprint/milestone completion
- Significant pivot or change

### Regular Cadence
- **Daily**: 5-minute status update
- **Weekly**: 15-minute context review
- **Sprint**: 30-minute deep maintenance
- **Quarterly**: Context health audit

## The Ritual Steps

### Phase 1: Initial Setup (New Projects)

#### Step 1: Create Master Context
```markdown
# Create /context.md
1. Project overview (2-3 sentences)
2. Current state snapshot
3. Navigation map to domains
4. Tech stack summary
5. Essential commands
```

**Time**: 15 minutes
**Owner**: Project Lead or Architect

#### Step 2: Establish Domain Contexts
```markdown
# For each domain (architecture, product, engineering)
1. Create /docs/[domain]/context.md
2. Define domain scope
3. List key patterns
4. Set up reference links
```

**Time**: 10 minutes per domain
**Owner**: Domain specialists

#### Step 3: Initialize Evolution Tracking
```markdown
# Create /docs/evolution/ structure
1. Set up decision-chains folder
2. Create first decision template
3. Document initial architecture
```

**Time**: 10 minutes
**Owner**: System Architect

### Phase 2: Daily Maintenance (5 minutes)

```yaml
daily_update:
  1_check: "Review /docs/current/active-work.md"
  2_update: "Mark completed tasks"
  3_add: "New blockers or decisions"
  4_commit: "git commit -m 'docs(context): daily update'"
```

**Checklist**:
- [ ] Task status current?
- [ ] New blockers noted?
- [ ] Priorities still valid?
- [ ] Context committed?

### Phase 3: Weekly Review (15 minutes)

```yaml
weekly_review:
  1_audit: "Check all domain contexts"
  2_archive: "Move completed work"
  3_clean: "Remove stale information"
  4_update: "Refresh key decisions"
  5_validate: "Cross-check with reality"
```

**Validation Questions**:
- Does context match actual project state?
- Are all recent decisions captured?
- Is archived content properly stored?
- Are priorities aligned with team?

### Phase 4: Sprint Maintenance (30 minutes)

```yaml
sprint_maintenance:
  1_comprehensive: "Full context audit"
  2_evolution: "Update decision chains"
  3_archive: "Sprint artifacts"
  4_refactor: "Reorganize if needed"
  5_metrics: "Measure context quality"
```

**Sprint Checklist**:
- [ ] Master context updated
- [ ] All domains refreshed
- [ ] Evolution chains current
- [ ] Archives organized
- [ ] Metrics documented

## Context Quality Standards

### Freshness Indicators
```markdown
## Good Context
- Last updated: Today
- Status: Current sprint work
- Decisions: Last 30 days
- References: Valid links

## Stale Context
- Last updated: >1 week
- Status: Old sprint items
- Decisions: >60 days old
- References: Broken links
```

### Content Guidelines

#### DO Write
- Concise bullet points
- Clear status indicators (✅ 🚧 📋)
- Dated decisions with rationale
- Smart references with metadata
- Evolution chains for major changes

#### DON'T Write
- Long paragraphs
- Implementation code
- Outdated information
- Deep nesting (>3 levels)
- Duplicate content

## Evolution Chain Template

When decisions evolve, track them:

```markdown
# Feature: [Name] Evolution

## Current State (Active)
- Implementation: [current approach]
- Location: [file/module]
- Status: [active/stable/deprecated]

## Evolution History
### v3 (Current) - [Date]
- Approach: [what we're doing]
- Why: [rationale for change]

### v2 (Superseded) - [Date]
- Approach: [what we tried]
- Issue: [why we changed]

### v1 (Original) - [Date]
- Approach: [initial attempt]
- Issue: [what we learned]

## Key Insights
- [Preserved knowledge from v1]
- [Lessons from v2]
- [Success factors for v3]

## See Also
- Architecture: [link]
- Implementation: [link]
- Decisions: [link]
```

## Measurement and Success

### Quantitative Metrics

| Metric | Target | How to Measure |
|--------|--------|----------------|
| Context Load Time | <2 min | Time from new chat to first code |
| Update Frequency | Daily | Git commit history |
| Freshness | <7 days | Last updated timestamps |
| Completeness | >90% | Checklist completion |

### Qualitative Indicators

- **Agent Success**: Can new agents start work immediately?
- **Decision Clarity**: Are past decisions understandable?
- **Navigation Ease**: Can you find information quickly?
- **Team Alignment**: Does context reflect team understanding?

## Common Pitfalls

### Pitfall 1: Context Bloat
**Problem**: Adding everything to context
**Solution**: Use hierarchy - summary in context, details in references

### Pitfall 2: Update Procrastination
**Problem**: "I'll update context later"
**Solution**: 5-minute daily ritual, automated reminders

### Pitfall 3: Lost Evolution
**Problem**: Deleting old decisions
**Solution**: Archive don't delete, maintain evolution chains

### Pitfall 4: Context Silos
**Problem**: Each person maintains different context
**Solution**: Single source of truth, clear ownership

## Automation Opportunities

### Git Hooks
```bash
# Pre-commit hook to check context freshness
#!/bin/bash
days_old=$(find . -name "context.md" -mtime +7 | wc -l)
if [ $days_old -gt 0 ]; then
  echo "Warning: Context files older than 7 days"
fi
```

### CI/CD Integration
- Automated freshness checks
- Link validation
- Structure compliance
- Metric tracking

### Templates
```bash
# Generate new domain context
./scripts/new-domain-context.sh [domain-name]

# Archive sprint
./scripts/archive-sprint.sh [sprint-id]

# Context health report
./scripts/context-health.sh
```

## Integration with Other Rituals

### With Retrospectives
- Extract patterns → Update context
- Document decisions → Evolution chains
- Learn from mistakes → Refine structure

### With Documentation
- Context provides navigation
- Documentation provides depth
- Evolution tracks changes

### With Agent Handoffs
- Context enables smooth transitions
- Updates trigger handoffs
- Quality gates check context

## Success Stories

### Pattern: The 2-Minute Miracle
"After implementing context ritual, new team member was productive in first hour instead of first week"

### Pattern: Decision Archaeology
"Evolution chains helped us understand why we chose technology X over Y, saving us from repeating past mistakes"

### Pattern: Living Memory
"Context became our project's living memory - always current, always accessible"

---

*Remember: Context is cheap to maintain but expensive to reconstruct. Invest 5 minutes daily to save 35 minutes per session.*