# Philosophy

ZenAI is a framework for building software with AI assistants on long-running, complex projects. It emerged from the gap between "AI can generate code" and "AI can help me ship a production system over months of work."

## The Problem

Modern AI coding assistants are powerful within a single session. But real software projects span weeks and months, involve multiple features, and require accumulated knowledge that no single context window can hold. The failure modes are predictable:

- **Context amnesia**: Every new session starts from zero. You repeat the same explanations, corrections, and design decisions.
- **Self-praise**: The same agent that built the code reviews it, finds issues, then talks itself into them being acceptable.
- **Knowledge rot**: Insights from debugging sessions, API quirks, and architectural decisions live only in conversation history that gets discarded.
- **Agent confusion**: Multiple specialized agents sound good in theory, but you lose track of who you're talking to and waste time on handoff friction.

ZenAI solves these with three principles: skills for knowledge, agents for verification, and documents for continuity.

## Core Principles

### Customer Value as North Star

Every technical decision filters through one question: does this serve the user? A customer persona (documented, referenced, updated) keeps the team aligned. Architecture serves the customer. Code quality serves the customer. Even the choice of which bug to fix first serves the customer.

This isn't a platitude — it's a decision-making framework. When two approaches are equivalent technically, the one that better serves the customer wins.

### Human Directs, AI Executes and Verifies

The human is the manager. The AI is the team. The human sets direction, makes judgment calls, and decides what's "good enough." The AI researches, plans, implements, tests, and verifies — but never decides alone on ambiguous matters.

This is not about distrust. It's about playing to strengths. Humans are better at judgment, context, and priorities. AI is better at thoroughness, consistency, and tireless execution.

### Design Before Code

Never start implementing before understanding the problem. Read existing code. Research current versions. Verify APIs actually work the way you think. A few minutes of verification saves hours of debugging wrong assumptions.

This applies at every scale: before a feature (plan mode), before a function (read the surrounding code), before using a library (check the actual API).

### Security by Default

Security is not a phase. It's a property of every decision. Sensitive data is encrypted at rest. Secrets never appear in logs. Input is validated at boundaries. Dependencies are audited. This applies whether you're building a wallet, a web app, or a CLI tool.

### Honest Verification

The biggest insight from real-world usage: **an agent cannot objectively evaluate its own work.** It finds real issues, then rationalizes them away. The fix is structural — use a separate agent with a separate context window for verification. It reads the task contract and the code cold, with no emotional attachment to the implementation.

### Continuous Knowledge Capture

The most expensive waste in AI-assisted development is rediscovery. Every session produces insights — API quirks, architectural decisions, debugging breakthroughs, corrections. If you don't capture them, the next session (or the next person) pays the full discovery cost again.

Knowledge capture should be frictionless (one command), prompted (the AI suggests it), and persistent (written to docs, not just conversation history).

## What Survived Real Usage

This framework was validated over months on a complex production project. Here's what made it through:

**Kept:**
- Customer persona as decision filter
- Design-before-code discipline
- Security-first mindset
- Structured task tracking (Part → Section → Task)
- Show & Tell as a quality gate
- Retrospectives for learning
- Antipattern awareness

**Changed:**
- 12 specialized agents → skills for interactive work, 2 agents for verification only
- Complex 3-layer context hierarchy → simple 3-file dev-docs system
- Agent-to-agent handoffs → session handoff prompts via `/update-dev-docs`
- ZenMaster orchestrator → the default agent with skills loaded on demand
- Cursor-specific tooling → Claude Code first (tool-agnostic principles)

**Removed:**
- Complex agent I/O contracts
- Agent personas with behavioral scripts
- Context evolution chains
- Multi-agent routing decisions
- The "sub-2-minute context loading" metric (replaced by "zero repeated explanations")

The framework that survived is simpler, more practical, and honest about what doesn't work. See [insights/](insights/) for the detailed postmortem.
