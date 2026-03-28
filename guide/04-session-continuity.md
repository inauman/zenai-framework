# Session Continuity

The biggest productivity killer in AI-assisted development is not slow code generation. It's **losing session knowledge during context resets.** Every `/clear`, every new session, every topic switch destroys insights that took hours to build. You end up repeating corrections, re-explaining architecture, and re-discovering gotchas like a parent teaching a child who keeps forgetting.

ZenAI solves this with the dev-docs system and session handoff prompts.

## The Dev-Docs System

Three files per feature, stored in `docs/plan/active/<feature>/`:

### plan.md — The Strategy
- Executive summary
- Architectural approach and design decisions
- Risk assessment and mitigation
- Implementation phases

### context.md — The Knowledge
This is the most critical file for session continuity. It captures everything that would be lost when a session ends:

**Required reading list** — files the next session must read, in order:
- Project docs (CLAUDE.md, relevant ADRs)
- These dev-docs (context.md, plan.md, tasks.md)
- Source files actively being modified

**External references** — URLs, API docs, protocol specs consulted:
- Include why each is relevant, not just the URL

**Session insights** — discoveries that can't be derived from code:
- Architectural insights ("use subscription from local database instead of polling the external service")
- API quirks ("the SDK returns X that already includes Y, no need to add manually")
- Integration discoveries ("hardware device requires Z even when config says otherwise")
- Performance observations ("operation takes 2s due to sequential round-trips")
- Process insights ("refer to testing guide X for reset steps", "use `pbcopy` to share tokens")

**Design decisions and rationale** — choices made and WHY:
- What was chosen, what was rejected, and the reasoning
- "We tried X first and it didn't work because Y" — saves the next session from the same dead end

**Corrections and gotchas** — things that were wrong and corrected:
- Wrong API assumptions caught and fixed
- Incorrect approaches that wasted time
- **These are the highest-value items** — they prevent repeated mistakes

**Current implementation state**:
- What's working vs. broken
- Uncommitted changes
- Commands to verify state

**Session handoff prompt** (last section) — see below.

### tasks.md — The Tracking

Part → Section → Task hierarchy with explicit status markers:

```
Part 1: Core Implementation
  Section 1.1: Data Layer
    Task 1.1.1: Create repository interface [ ]
    Task 1.1.2: Implement SQLite adapter [ ]
    Task 1.1.3: Unit tests for adapter [ ]

  Section 1.2: Verification
    Task 1.2.1: Integration test [ ]
    Task 1.2.2: Full build verification [ ]
```

**Rules:**
- Max 3 levels of nesting (Part → Section → Task)
- Last section of each Part = Verification (integration tests, build checks)
- Each task is atomic and independently verifiable
- Status: `[ ]` pending, `[x]` complete, `[~]` in progress, `[!]` blocked

## The Session Handoff Prompt

The critical deliverable of `/update-dev-docs`. Written as the last section of `context.md`, it's a self-contained prompt you paste into a new session:

```markdown
## Session Handoff Prompt

> Paste this into a new session to continue where we left off.

You are continuing work on [feature] for [project].

**Read these files first (in order):**
1. `CLAUDE.md` — project rules
2. `docs/plan/active/<feature>/context.md` — full context
3. `docs/plan/active/<feature>/tasks.md` — task status
4. `docs/plan/active/<feature>/plan.md` — approach
5. [other critical files]

**Key insights you MUST know (do NOT rediscover these):**
- [Insight 1 — the non-obvious thing]
- [Insight 2]

**Corrections — do NOT repeat these mistakes:**
- [Mistake 1 and the correct approach]

**Current state:**
- [What's working]
- [What's in progress]

**Next steps:**
- [Task X.Y.Z — first thing to do]

**External references:**
- [URL — why it's needed]
```

**The mental test:** "If I read only this prompt and the files it references, could I continue without asking the user to repeat anything?"

## When to Checkpoint

Run `/update-dev-docs` at these moments:

- **Before every `/clear`** — non-negotiable
- **After a breakthrough** — capture the insight before it gets buried
- **Before switching topics** — checkpoint current work before pivoting
- **After major milestones** — completed a Part? Checkpoint before starting the next
- **Before session end** — preserve everything for next time
- **Before phase transitions** — Plan → Execute, Execute → Verify

## Dev-Docs Lifecycle

```
docs/plan/backlog/    → lightweight future items (one file per idea)
docs/plan/active/     → current work (3+ files per feature)
docs/plan/archive/    → completed features (moved from active/)
handoff/              → ephemeral verification reports (gitignored)
```

### Backlog Items

Quick captures — not full plans. One markdown file per idea with:
- What, why, rough scope
- Origin (which session surfaced it)
- Priority (low/medium/high)

Promoted to `active/` via `/dev-docs` when you're ready to spec it out.

### Phase Accumulation

A feature folder grows beyond the initial 3 files as you iterate:

```
docs/plan/active/my-feature/
├── plan.md                      # Original plan
├── context.md                   # Living context (updated each session)
├── tasks.md                     # Task tracking
├── api-redesign-plan.md         # Iteration 2 (scope changed)
├── performance-fix-plan.md      # Iteration 3 (found bottleneck)
└── audit-review-fix-plan.md     # Post-verification fixes
```

All files in the directory are part of the scope. Verification agents read everything.

## Knowledge Capture

Beyond dev-docs, use `/capture` (or your equivalent) to persist insights into permanent project documentation:

- Architecture decisions → ADRs
- Protocol learnings → protocol docs
- Testing procedures → testing guides
- Integration discoveries → learning docs

The difference: dev-docs are ephemeral (per-feature, archived when done). Knowledge capture is permanent (project-level docs that outlive any single feature).

## What Replaced the Old Context System

The v1 framework had a 3-layer context hierarchy (Master Context, Domain Context, Detail Context) with evolution chains and context inheritance. In practice:

- The hierarchy was too complex to maintain
- "Context evolution chains" became stale immediately
- The real problem wasn't loading project overview — it was preserving session-specific insights
- A simple 3-file system with a handoff prompt solved 90% of the continuity problem

The remaining 10% is solved by `/capture` — writing insights into permanent docs so they're available to any future session, not just the next one.
