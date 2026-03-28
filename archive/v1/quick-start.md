# ZenAI Quick Start Guide

Get your AI agent team operational in 15 minutes.

## 5-Minute Setup

### Step 1: Create Your Master Context (2 min)

Create `/context.md` in your project root:

```markdown
# [Your Project] - Master Context

## What This Is
[2-3 sentence description]

## Current State
- ✅ [What's done]
- 🚧 [What's in progress]
- 📋 [What's next]

## Tech Stack
- Frontend: [your stack]
- Backend: [your stack]
- Database: [your stack]

## Quick Commands
- `npm test` - Run tests
- `npm run dev` - Start development
- [your commands]
```

### Step 2: Define Your First Agents (2 min)

Start with these three core agents:

```markdown
# Your Agent Team

## ZenMaster (Orchestrator)
Routes tasks between specialists

## System Architect
Designs system structure and patterns

## Full-Stack Engineer
Implements features across the stack
```

### Step 3: Set Up Your First Handoff (1 min)

Create a simple handoff protocol:

```markdown
# Handoff Protocol

1. Agent completes work
2. Updates context
3. Signals next agent
4. Next agent acknowledges and begins
```

## Your First Agent-Driven Task

### Example: Add User Authentication

#### 1. Assign to Architect (1 min)
```
"System Architect, design a user authentication system.
Read context.md first, then create an architecture plan."
```

#### 2. Review and Handoff (1 min)
```
"Looks good. Engineer, implement the authentication
based on the architect's design."
```

#### 3. Context Update (1 min)
```
"Update context.md with:
- ✅ Authentication design complete
- 🚧 Authentication implementation in progress"
```

## Scaling Your Team

### Week 1: Core Team
- ZenMaster
- System Architect
- Full-Stack Engineer

### Week 2: Add Specialists
- Frontend Engineer
- Backend Engineer
- QA Engineer

### Week 3: Full Team
- Product Owner
- UX Designer
- Security Engineer
- DevOps Engineer

## Context Management Basics

### Daily Routine (5 min)
```bash
1. Check context.md
2. Update completed items
3. Add new blockers
4. Commit changes
```

### Weekly Routine (15 min)
```bash
1. Archive completed work
2. Update all domain contexts
3. Clean stale information
4. Review agent performance
```

## Common Patterns

### Pattern 1: Feature Development
```
Product Owner → UX Designer → Architect → Engineers → QA
```

### Pattern 2: Bug Fix
```
QA → Engineer → Security Review → QA → Deploy
```

### Pattern 3: Architecture Change
```
Architect → Security Review → Engineers → Full Testing
```

## Tips for Success

### DO
✅ Start small with 3-4 agents
✅ Update context immediately
✅ Use clear handoffs
✅ Review agent outputs
✅ Iterate based on results

### DON'T
❌ Skip context updates
❌ Create too many agents initially
❌ Forget human oversight
❌ Ignore quality gates
❌ Overcomplicate early

## Troubleshooting

### "Agents keep losing context"
→ Update context.md more frequently
→ Make handoffs more explicit

### "Too much overhead"
→ Start with fewer agents
→ Simplify handoff protocol

### "Agents producing poor quality"
→ Add review cycles
→ Improve context quality
→ Define clearer requirements

## Next Steps

1. **Read Full Guides**:
   - [Context Management](context-management.md)
   - [Agent Orchestration](agent-orchestration.md)

2. **Explore Rituals**:
   - [Context Management Ritual](rituals/ritual_context_management.md)
   - [Agent Handoff Ritual](rituals/ritual_agent_handoff.md)

3. **Study Patterns**:
   - [Personas Guide](personas.md)
   - [Standards](standards/)

## Get Help

- **Documentation**: This repository
- **Issues**: GitHub Issues
- **Community**: Discussions (coming soon)

---

*Remember: Start simple, iterate often, measure results.*