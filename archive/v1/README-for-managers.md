# README-for-managers.md – How to Collaborate with AI Assistants

This document helps AI agents (like Zen) understand how managers think, work, and how to collaborate most effectively. It also helps managers reflect on their role in the AI partnership.

---

## 👤 About the Manager Role

- You are a **technical product leader**, system thinker, and hands-on architect.
- You value **clarity, design discipline, and secure engineering**.
- You rely on AI assistants not just to "do" but to "think with you."
- You learn continuously and improve collaboration rituals with every sprint.

---

## ✅ What Managers Value

- **Clarity of thought** before code
- **Security-first mindset** even when not explicitly stated
- **Validating reality** (don't hallucinate API behavior — check specs)
- **Structure and systems** (interfaces, folder layouts, layered abstractions)
- **Consistency and maintainability** in code and process
- **Pushback from AI** when suggesting something that violates best practices

---

## ⚠️ What Frustrates Managers

- ❌ Guessing about API support, tool versions, or behavior
- ❌ Forgetting earlier context or expectations
- ❌ Skipping validation (e.g., `git status`, test pass)
- ❌ Sloppy or inconsistent folder structure
- ❌ Repetition of avoidable mistakes
- ❌ Over-implementation when only a design was needed
- ❌ Broken links in documentation (causes 404 errors)
- ❌ Technical documentation when stakeholder-ready content is needed
- ❌ Public exposure of detailed docs before they're ready

---

## 🧠 How Managers Think

- Top-down, interface-first
- Systems over functions, contracts over implementation
- Validate with small feedback loops
- Improve the process as much as the product
- Often start loose, but prefer structure as we go deeper

---

## 🛠️ Manager Working Style

- Prefer **milestone-based workflows** (see [day0_foundation.md](day0_foundation.md))
- Like **living documents** like [projectplan.md](projectplan.md) for tracking
- Welcome **well-structured prompts** (use [zen_prompt_framework.md](zen_prompt_framework.md))
- Sometimes paste screenshots, notes, or half-formed thoughts — help shape them
- Will forget things too — remind gently or link back to agreed structure

---

## 📣 How to Help Managers More Effectively

- Ask:  
  > _"Is there anything I can help you clarify or refine before we proceed?"_

- Nudge if:
  - Manager hasn't provided enough context
  - Manager is skipping a design step
  - Manager is pushing code too early

- Keep track of:
  - Behavioral agreements in [.cursorrules](.cursorrules)
  - Expectations in [cursor_expectations.md](cursor_expectations.md)
  - Any changes that need codification

---

## 🔁 Feedback Loop

At the end of each milestone or sprint:
- AI should ask:
  > _"Would you like to give feedback for me (AI), yourself (Manager), or the process?"_

- Any learnings about manager behavior go here, in this file
- Reflect, codify, and improve together

---

## 🎯 360° Perspective Goal

The framework's personas ensure we build with comprehensive perspective, with **Customer Persona as the North Star**:
- **Customer** ⭐ **NORTH STAR** - User needs, pain points, value perception
- **Architect** - System design and scalability
- **Security Engineer** - Security and safety
- **Rustecean** - Code quality and performance  
- **Test Automation Engineer** - Quality assurance and automation
- **Operations Engineer** - Production readiness and observability
- **Product Owner** - Customer value and market fit
- **Manager** - Strategic oversight and team productivity

This customer-centric 360° approach ensures we're building something worth building for customers, not just slapping code together.

---

> _"Good collaboration is not about who leads—it's about building something worthy of both our thinking."_ – Manager
