# Templates Domain Context

## Domain Overview
The Templates domain serves as the **actionable embodiment of ZenAI standards**, providing structured starting points that enforce consistency, quality, and best practices across all development activities. Templates are not mere suggestions—they are **enforced through process** and represent the crystallization of our collective wisdom into reusable, evolving artifacts.

## Why Templates Matter
Templates transform abstract standards into **concrete, actionable tools** that:
- **Reduce cognitive load** by providing proven starting points
- **Enforce consistency** across team members and projects
- **Embody best practices** in immediately usable form
- **Accelerate onboarding** by making expectations explicit
- **Enable continuous improvement** through iterative refinement
- **Support quality gates** with built-in validation criteria

## Core Templates

### 1. Document Template (`document-template.md`)
**Purpose**: The cornerstone of our context management and migration strategy.

**Critical Role**:
- Defines the **lifecycle of knowledge artifacts** from creation through deprecation
- Enables **systematic migration** of legacy documentation to context-aware formats
- Provides **metadata structure** for AI agents to understand document purpose and relevance
- Establishes **review cycles** to keep documentation fresh and actionable

**Key Features**:
- Structured metadata headers for context classification
- Version tracking and migration status indicators
- Cross-reference mapping to related domains
- Deprecation and archival workflows
- Quality gates for documentation review

**Migration Strategy Integration**:
This template is **essential** for transitioning from scattered documentation to our unified context system. Every document migrated using this template becomes:
- Machine-readable for AI agents
- Human-navigable through consistent structure
- Version-controlled with clear lifecycle status
- Linked within the broader knowledge graph

### 2. Code Review Checklist (`code-review-checklist.md`)
**Purpose**: Standardize code review practices across all pull requests.

**Enforcement Points**:
- Pre-merge validation in CI/CD pipelines
- Reviewer accountability through explicit checklist completion
- Quality metrics tracking for continuous improvement
- Integration with automated tooling for objective criteria

**Key Sections**:
- Security review requirements
- Performance impact assessment
- Test coverage validation
- Documentation completeness
- Architectural alignment verification

### 3. Commit Message Template (`commit-message-template.md`)
**Purpose**: Ensure meaningful, searchable, and consistent version history.

**Format Enforcement**:
```
type(scope): subject

body

footer
```

**Integration Points**:
- Git hooks for format validation
- Automated changelog generation
- Release note compilation
- Traceability to issues and requirements

### 4. Pull Request Template (`pull-request-template.md`)
**Purpose**: Standardize PR submissions for efficient review and merging.

**Required Sections**:
- Problem statement and solution approach
- Testing strategy and results
- Breaking changes and migration guides
- Checklist linking to code review criteria
- Performance and security impact assessments

**Process Integration**:
- Auto-populated from branch naming conventions
- Links to related issues and documentation
- Triggers automated validation workflows
- Generates review assignments based on code ownership

### 5. Testing Template (`testing-template.md`)
**Purpose**: Document test strategies, plans, and results consistently.

**Coverage Areas**:
- Test plan structure and rationale
- Test case documentation format
- Test data management approach
- Results reporting templates
- Regression test selection criteria

**Quality Gates**:
- Minimum coverage thresholds
- Performance baseline comparisons
- Security vulnerability scanning
- Accessibility compliance checks

## Template Lifecycle Management

### Creation Process
1. **Identify Pattern**: Recognize repeated practices needing standardization
2. **Draft Template**: Create initial version based on best examples
3. **Peer Review**: Validate with team members and stakeholders
4. **Pilot Usage**: Test with real projects for refinement
5. **Formal Adoption**: Integrate into standard workflows

### Evolution Mechanism
Templates are **living documents** that evolve through:
- **Retrospective Feedback**: Lessons learned from template usage
- **Tool Integration**: Automation opportunities and enhancements
- **Cross-Domain Learning**: Insights from related standards
- **External Best Practices**: Industry evolution and new patterns

### Deprecation Protocol
When templates become obsolete:
1. Mark as deprecated with migration guidance
2. Provide timeline for transition
3. Update dependent processes and tools
4. Archive with historical context preserved

## Integration with Other Domains

### Common Standards Domain
Templates **implement** the standards defined in the Common domain:
- Documentation standards → Document template
- Coding standards → Code review checklist
- Communication standards → PR and commit templates

### Engineering Domain
Templates **support** engineering practices:
- Development workflows use PR templates
- Testing strategies leverage testing templates
- Code quality enforced through review checklists

### Project Domain
Templates **enable** project execution:
- Project plans follow document template structure
- Milestone reviews use validation checklists
- Retrospectives capture template improvement opportunities

## Enforcement Mechanisms

### Process Integration
- **CI/CD Pipelines**: Automated validation of template compliance
- **IDE Integration**: Template snippets and autocomplete
- **Git Hooks**: Pre-commit and pre-push validations
- **Review Gates**: Human verification of template usage

### Metrics and Monitoring
- Template adoption rates across projects
- Deviation tracking and root cause analysis
- Time saved through template usage
- Quality improvements from standardization

### Training and Onboarding
- Template workshops for new team members
- Best practice examples and anti-patterns
- Regular refreshers on template updates
- Mentorship on effective template usage

## Success Criteria

A template is successful when it:
- **Reduces decision fatigue** by providing clear starting points
- **Increases velocity** through elimination of boilerplate work
- **Improves quality** via embedded best practices
- **Enables automation** through consistent structure
- **Facilitates learning** by making patterns explicit

## Template Quality Standards

Every template must:
- Include clear purpose and usage instructions
- Provide concrete examples and anti-patterns
- Define completion criteria and quality gates
- Link to related templates and standards
- Support progressive disclosure of complexity
- Enable both novice and expert usage patterns

## Future Evolution

### Near-term Enhancements
- AI-powered template suggestions based on context
- Dynamic template generation from project requirements
- Cross-project template analytics and optimization
- Template versioning with backward compatibility

### Long-term Vision
- Self-adapting templates that learn from usage patterns
- Context-aware template recommendations
- Automated template compliance reporting
- Template marketplace for cross-organization sharing

## Action Items for Teams

1. **Immediate**: Adopt document-template.md for all new documentation
2. **This Week**: Migrate high-value documents using the template
3. **This Sprint**: Integrate templates into CI/CD workflows
4. **This Quarter**: Measure and report on template effectiveness
5. **Ongoing**: Contribute improvements through retrospectives

## Conclusion

Templates are not bureaucratic overhead—they are **force multipliers** that transform individual expertise into team capability. By treating templates as first-class citizens in our development process, we create a foundation for sustainable, scalable, and high-quality software delivery.

The document-template.md, in particular, represents our commitment to **intentional knowledge management**, ensuring that every piece of documentation serves its purpose effectively and evolves with our understanding.

Through disciplined template usage, we achieve the seemingly paradoxical goal of **standardization that enables creativity**—providing enough structure to eliminate wasteful decisions while preserving space for innovation where it matters most.