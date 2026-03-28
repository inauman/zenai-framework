# Validation Checklist – ZenAI Milestone Completion Gate

Before marking a task or milestone as complete, this checklist ensures the work has been validated, committed, and reviewed with discipline and quality.

---

## 🎯 Purpose

- Enforce quality control before task/milestone closure
- Ensure consistent commit and delivery hygiene
- Act as a ritualized pause for reflection and feedback

---

## ✅ When to Use

- After completing any milestone or numbered task in [projectplan.md](projectplan.md)
- Before pushing a commit
- During code review or pre-deploy QA

---

## 📋 Completion Criteria

Check all that apply before marking a task complete in [projectplan.md](projectplan.md).

### 🔧 Implementation

- [ ] Code compiles/builds without errors
- [ ] Linting passes (e.g., ESLint, Clippy)
- [ ] Tests pass (unit/integration/E2E as applicable)
- [ ] Sensitive logic reviewed for security implications

### 🧠 Cognitive Validation

- [ ] Code or artifact aligns with the agreed design/contract
- [ ] Implementation choices are explained in comments or commit message
- [ ] Threat mitigation notes are documented (if applicable)
- [ ] Validate security posture in both dev and production builds (some features like CSP may only be enforced in production).
- [ ] Consult the latest official schema or documentation before editing any configuration (schema-first ritual).
- [ ] Confirm that all build paths (e.g., `frontendDist`) are correct for both dev and production environments.
- [ ] **Documentation Link Validation**: Run link validation script for any documentation changes
- [ ] **Product-First Content**: Ensure documentation is stakeholder-ready, not just technical
- [ ] **Privacy Check**: Confirm sensitive/private docs are properly excluded from public repos

### 🗂️ Hygiene & Commit

- [ ] `git status` is clean (no untracked or leftover files)
- [ ] Commit created with conventional format:
  - Example: `feat(crypto): add age encryption interface`
- [ ] Commit is atomic, focused, and meaningful
- [ ] Cursor task marked complete in [projectplan.md](projectplan.md)
- [ ] Complete a brief retrospective: What went well? What could be improved? What will we do differently next time?

### 📣 Communication & Feedback

- [ ] Zen has asked: _“Is there anything I missed?”_
- [ ] Feedback (if any) captured in [README-for-managers.md](README-for-managers.md) or [.cursorrules](.cursorrules)
- [ ] Linked documents updated (e.g., architecture.md, diagrams, READMEs)

---

## 🧘 Ritual Tip

> If you're rushing to check off a task, stop and reflect:  
> _“Would I trust this output if it held my secrets?”_

---

## 🧩 Linked Ritual Artifacts

Refer to:
- [.cursorrules](.cursorrules)
- [projectplan.md](projectplan.md)
- [security_principles.md](security_principles.md)

These files form the behavioral contract and implementation planning base for all future milestones.

---

Use this checklist not as a blocker, but as a safeguard for quality, safety, and alignment.
