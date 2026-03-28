# Project Plan Template – ZenAI Living Collaboration Artifact

This template provides a structured approach to project planning and tracking that works effectively for AI-human collaboration. It serves as a **living, breathing document** that evolves with the project and keeps both parties accountable.

---

## 🎯 Purpose

- **Single Source of Truth** for project status and progress
- **Collaboration Contract** between AI assistant and human manager
- **Living Document** that evolves with the project
- **Accountability Tool** for both parties
- **Validation Gate** for task completion

---

## 📋 Template Structure

```markdown
# [Project Name] Project Plan

## Project Overview
[2-3 sentence description of what we're building]

## Development Principles
- **Principle 1**: [Core principle with brief explanation]
- **Principle 2**: [Core principle with brief explanation]
- **Principle 3**: [Core principle with brief explanation]

## Technology Stack
- **Frontend**: [Technology choices]
- **Backend**: [Technology choices]
- **Infrastructure**: [Deployment/CI choices]

## Project Structure
```
[High-level folder structure - keep it simple]
```

## Design Decisions & Clarifications
[Key architectural or UX decisions that guide implementation]

## Milestones

### Milestone 1: [Foundation/Setup]
**Goal**: [Clear, measurable goal]

| #    | Task Description                          | Status | Owner    | Notes                        |
|------|-------------------------------------------|--------|----------|------------------------------|
| 1.1  | [Specific task]                           | [ ]    | Zen      | [Optional notes]             |
| 1.2  | [Specific task]                           | [ ]    | Manager  | Depends on 1.1               |
| 1.3  | [Specific task]                           | [ ]    | Zen      | Awaiting approval            |

### Milestone 2: [Core Feature]
**Goal**: [Clear, measurable goal]

| #    | Task Description                          | Status | Owner    | Notes                        |
|------|-------------------------------------------|--------|----------|------------------------------|
| 2.1  | [Specific task]                           | [ ]    | Zen      | [Optional notes]             |
| 2.2  | [Specific task]                           | [ ]    | Zen      | Depends on 2.1               |
| 2.3  | [Specific task]                           | [ ]    | Manager  | Final validation             |

## Testing Strategy
[Brief testing approach - unit, integration, E2E]

## Development Workflow
[How tasks flow from planning to completion]

## Success Metrics
[How we measure success]

## Timeline Estimate
[High-level timeline with phases]

## Next Steps
[Immediate next actions]
```

### Alternative: Bullet Format (for simpler projects)

```markdown
### Milestone 1: [Foundation/Setup]
**Goal**: [Clear, measurable goal]

- [ ] 1.1: [Specific task]
  - [ ] 1.1.1: [Subtask if needed]
  - [ ] 1.1.2: [Subtask if needed]
- [ ] 1.2: [Specific task]
- [ ] 1.3: [Specific task]
```

---

## 🧠 Usage Guidelines

### **For AI Assistant (Zen)**
- **Update Status Religiously**: Mark tasks complete only after validation
- **Add New Tasks**: When scope expands or new requirements emerge
- **Link to Implementation**: Reference specific files or commits
- **Ask for Clarification**: When tasks are ambiguous or underspecified

### **For Human Manager**
- **Review Regularly**: Check progress and provide feedback
- **Prioritize Tasks**: Help AI understand what's most important
- **Clarify Scope**: Provide additional context when needed
- **Validate Completion**: Confirm tasks are truly done

### **For Both**
- **Keep It Current**: Update as the project evolves
- **Use as Communication Tool**: Reference in discussions
- **Learn from Patterns**: Improve the template based on usage

### **Feedback Loop Ritual**
- **End of each milestone**: Zen asks: *"Is there anything I missed?"*
- **Manager provides feedback**: Add to project plan or retro files
- **Mid-milestone reviews**: Optional but encouraged for long phases
- **Dependency tracking**: Use "Depends on X.Y" in notes column

---

## ✅ Task Completion Criteria

Each task must meet these criteria before being marked complete:

- [ ] **Implementation Complete**: Code/feature works as intended
- [ ] **Validation Passed**: Tests, linting, security review
- [ ] **Documentation Updated**: Code comments, README, etc.
- [ ] **Git Status Clean**: Committed with conventional message
- [ ] **Manager Review**: Human has validated the work
- [ ] **Retrospective Done**: Learnings captured (see [retrospective_ritual.md](retrospective_ritual.md))

## 👥 Owner Assignment Guidelines

### **Zen (AI Assistant)**
- Implementation tasks (coding, testing, documentation)
- Technical design and architecture
- Code review and validation
- Performance optimization

### **Manager (Human)**
- Business requirements and scope definition
- Final validation and approval
- Stakeholder communication
- Priority decisions and trade-offs

### **Status Tracking**
- `[ ]` = Incomplete
- `[x]` = Complete (after validation)
- Use notes column for: dependencies, blockers, context

---

## 📊 Example: E-commerce Platform

```markdown
# E-commerce Platform Project Plan

## Project Overview
Building a modern e-commerce platform with React frontend and Node.js backend, focusing on performance and user experience.

## Development Principles
- **Performance First**: Sub-2s page loads, optimized images
- **Mobile-First Design**: Responsive design with touch-friendly interactions
- **Security by Default**: HTTPS, input validation, secure authentication

## Technology Stack
- **Frontend**: React 18, TypeScript, Tailwind CSS
- **Backend**: Node.js, Express, PostgreSQL
- **Infrastructure**: Docker, AWS, GitHub Actions

## Project Structure
```
ecommerce/
├── frontend/          # React application
├── backend/           # Node.js API
├── shared/            # Shared types and utilities
├── docs/              # Documentation
└── scripts/           # Build and deployment
```

## Design Decisions & Clarifications
- **State Management**: Zustand for client state, React Query for server state
- **Authentication**: JWT tokens with refresh mechanism
- **Payment**: Stripe integration with webhook validation

## Milestones

### Milestone 1: Project Foundation
**Goal**: Establish development environment and basic project structure

| #    | Task Description                          | Status | Owner    | Notes                        |
|------|-------------------------------------------|--------|----------|------------------------------|
| 1.1  | Initialize project repositories           | [x]    | Zen      | Done                        |
| 1.2  | Set up development environment            | [x]    | Zen      | Done                        |
| 1.3  | Configure CI/CD pipeline                  | [x]    | Zen      | Done                        |
| 1.4  | Set up database schema                    | [ ]    | Zen      | Awaiting requirements        |
| 1.5  | Create basic API endpoints                | [ ]    | Zen      | Depends on 1.4               |

### Milestone 2: User Authentication
**Goal**: Complete user registration, login, and profile management

| #    | Task Description                          | Status | Owner    | Notes                        |
|------|-------------------------------------------|--------|----------|------------------------------|
| 2.1  | Design authentication flow                | [ ]    | Manager  | Define requirements          |
| 2.2  | Implement user registration               | [ ]    | Zen      | Depends on 2.1               |
| 2.3  | Implement user login                      | [ ]    | Zen      | Depends on 2.2               |
| 2.4  | Add password reset functionality          | [ ]    | Zen      | Depends on 2.3               |
| 2.5  | Create user profile management            | [ ]    | Zen      | Depends on 2.3               |

### Milestone 3: Product Catalog
**Goal**: Build product browsing and search functionality

| #    | Task Description                          | Status | Owner    | Notes                        |
|------|-------------------------------------------|--------|----------|------------------------------|
| 3.1  | Design product data model                 | [ ]    | Manager  | Define product attributes    |
| 3.2  | Implement product listing API             | [ ]    | Zen      | Depends on 3.1               |
| 3.3  | Create product search functionality       | [ ]    | Zen      | Depends on 3.2               |
| 3.4  | Build product detail pages                | [ ]    | Zen      | Depends on 3.2               |
| 3.5  | Add product filtering and sorting         | [ ]    | Zen      | Depends on 3.3               |

## Testing Strategy
- **Unit Tests**: Jest for business logic, React Testing Library for components
- **Integration Tests**: API endpoint testing with supertest
- **E2E Tests**: Playwright for critical user journeys

## Development Workflow
1. **Plan**: Define task in project plan
2. **Implement**: Code with TDD approach
3. **Validate**: Run tests and linting
4. **Review**: Manager validates completion
5. **Update**: Mark task complete in plan

## Success Metrics
- 95% test coverage
- Lighthouse score >90
- Zero critical security vulnerabilities
- <2s page load times

## Timeline Estimate
- **Phase 1** (Foundation): 2 weeks
- **Phase 2** (Authentication): 3 weeks
- **Phase 3** (Catalog): 4 weeks
- **Phase 4** (Checkout): 3 weeks

**Total**: 12 weeks for MVP

## Next Steps
1. Complete database schema design
2. Set up authentication flow
3. Begin user registration implementation
```

---

## 🔄 Integration with Other Rituals

### **Validation Checklist**
Use [validation_checklist.md](validation_checklist.md) before marking tasks complete.

### **Retrospectives**
Complete [retrospective_ritual.md](retrospective_ritual.md) after each milestone.

### **Day 0 Foundation**
Reference this template during [day0_foundation.md](day0_foundation.md) planning.

---

## 🎯 Success Criteria

A good project plan should:
- ✅ **Be Living**: Updated regularly, not static
- ✅ **Be Clear**: Unambiguous tasks and goals
- ✅ **Be Measurable**: Trackable progress and completion
- ✅ **Be Collaborative**: Works for both AI and human
- ✅ **Be Honest**: Reflects real progress, not wishful thinking

---

## 🧩 Linked Ritual Artifacts

Refer to:
- [day0_foundation.md](day0_foundation.md) - Use during initial planning
- [validation_checklist.md](validation_checklist.md) - Before marking tasks complete
- [retrospective_ritual.md](retrospective_ritual.md) - After milestone completion
- [personas.md](personas.md) - Consider different perspectives when planning
- [.cursorrules](.cursorrules) - AI behavior contract

---

> _"A good plan is like a map—it shows you where you are, where you're going, and how to get there."_ – Zen 