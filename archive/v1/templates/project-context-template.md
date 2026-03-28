# Project Context Template

Use this template to create your master `/context.md` file for sub-2-minute AI agent onboarding.

---

# [Project Name] - Master Context

## What This Is
[2-3 sentence description of your project. Focus on WHAT it does and WHO it's for.]

Example:
> A cross-platform desktop application for secure file encryption using military-grade standards. Built for users who need to protect sensitive documents before cloud storage or sharing.

## Current State

### Completed ✅
- [Major milestone or feature completed]
- [Another completed item]

### In Progress 🚧
- [What you're actively working on]
- [Current sprint focus]

### Next Up 📋
- [Immediate priority after current work]
- [Next major milestone]

## Tech Stack

| Layer | Technology | Version | Notes |
|-------|------------|---------|-------|
| Frontend | [e.g., React] | [e.g., 19.0] | [Any special config] |
| Backend | [e.g., Node.js] | [e.g., 20.x] | [Framework used] |
| Database | [e.g., PostgreSQL] | [e.g., 15] | [ORM/driver] |
| Infrastructure | [e.g., AWS] | - | [Key services] |

## Project Structure
```
project-root/
├── src/           # [Main source code]
├── tests/         # [Test files]
├── docs/          # [Documentation]
├── scripts/       # [Build/deploy scripts]
└── config/        # [Configuration files]
```

## Essential Commands

```bash
# Development
npm run dev        # Start development server
npm test          # Run tests
npm run build     # Build for production

# Git workflow
git status        # Check changes
git add .         # Stage changes
git commit        # Commit with conventional format

# Project specific
[your commands]   # [Description]
```

## Navigation Map

| Domain | Location | Purpose |
|--------|----------|---------|
| Architecture | `/docs/architecture/` | System design and patterns |
| API | `/docs/api/` | Endpoint documentation |
| Testing | `/docs/testing/` | Test strategies and coverage |
| Security | `/docs/security/` | Security considerations |

## Recent Decisions

| Date | Decision | Rationale |
|------|----------|-----------|
| [YYYY-MM-DD] | [What was decided] | [Why it was decided] |
| [YYYY-MM-DD] | [Another decision] | [Business/technical reason] |

## Known Issues & Blockers

### Active Issues
- **[Issue name]**: [Brief description] - [Impact/priority]

### Workarounds
- **For [problem]**: [Temporary solution until fixed]

## Team & Responsibilities

| Role | Agent/Person | Focus |
|------|--------------|-------|
| Architect | [Name/Agent] | System design, patterns |
| Frontend | [Name/Agent] | UI implementation |
| Backend | [Name/Agent] | API, business logic |
| QA | [Name/Agent] | Testing, quality |

## Key Patterns & Standards

### Code Style
- [Language]: [Style guide used]
- Formatting: [Tool used, e.g., Prettier]
- Linting: [Tool used, e.g., ESLint]

### Git Workflow
- Branch naming: `feature/`, `bugfix/`, `hotfix/`
- Commit format: Conventional commits
- PR process: [Your review process]

### Testing
- Unit tests: [Coverage target]
- Integration tests: [Approach]
- E2E tests: [Tool/framework]

## Context Maintenance

### Update Frequency
- **Daily**: Task status, blockers
- **Weekly**: Completed items, new decisions
- **Sprint**: Archive completed, update priorities

### Domain Contexts
Additional detailed contexts available in:
- `/docs/architecture/context.md` - Technical architecture
- `/docs/product/context.md` - Product requirements
- `/docs/engineering/context.md` - Implementation details

## Quick Links

- **Repository**: [GitHub/GitLab/Bitbucket URL]
- **Documentation**: [Wiki/Confluence/Notion URL]
- **CI/CD**: [Pipeline URL]
- **Deployment**: [Staging/Production URLs]
- **Issue Tracker**: [Jira/Linear/GitHub Issues URL]

---

*Last Updated: [YYYY-MM-DD] | Next Review: [YYYY-MM-DD]*
*Maintained by: [Team/Person responsible]*

---

## Usage Instructions

1. **Copy this template** to your project root as `/context.md`
2. **Fill in all sections** with your project-specific information
3. **Delete these instructions** and example content
4. **Commit** the context file to your repository
5. **Update regularly** following the maintenance schedule

### Tips for Effective Context

- **Be concise**: Bullets > paragraphs
- **Be current**: Update immediately when things change
- **Be clear**: Avoid jargon, explain acronyms
- **Be complete**: Cover all essential information
- **Be navigable**: Use clear headers and structure

### For AI Agents

When starting a new session, instruct your AI:
```
Please read /context.md first to understand the project.
For detailed work, also read /docs/[domain]/context.md.
```

This ensures consistent, fast onboarding every time.