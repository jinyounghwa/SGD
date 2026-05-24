# SGD: Sprint-Guided Development Methodology

**English | [한국어](README.ko.md)**

---

## What is SGD?

**SGD (Sprint-Guided Development)** is a practical development methodology built around one core idea:

> **Break work into small phases, verify each phase with tests, commit at every checkpoint.**

That's it. No complex tooling, no framework dependencies. Just a disciplined cycle of:

```
Plan a Sprint → Break into Phases → Implement → Test → Commit → Repeat
```

---

## Why Does This Work?

### The Problem: Unstructured Development

```
❌ Without structure:
  "I'll build the whole authentication system"
  → 3 days of coding
  → nothing works
  → no idea what broke
  → start over

✅ With SGD:
  Sprint 5: Authentication System
    Phase 1: JWT token generation (8 tests) → commit ✅
    Phase 2: Login endpoint (6 tests) → commit ✅
    Phase 3: Token refresh (5 tests) → commit ✅
    Phase 4: Logout + cleanup (4 tests) → commit ✅
```

Each phase is **small enough to complete in one sitting**, **verified by tests**, and **safely committed**.

### Three Things That Actually Help

**1. Phase Decomposition**
- Forces you to think before coding
- Each phase is a manageable chunk (30min - 2 hours)
- Easier to estimate and track

**2. Test Checkpoints**
- Every phase has a test target
- Tests tell you immediately if something broke
- "All tests pass" = safe to commit and move on

**3. Commit at Every Phase**
- Every commit is a rollback point
- Commit messages document what changed and how many tests verify it
- `git log --oneline` becomes your progress report

---

## The Cycle

### Sprint Planning (30 min)

Write a `SPRINT_XX_PLAN.md`:

```markdown
# Sprint 1: User Authentication

## Phases
| Phase | Feature | Tests | Time |
|-------|---------|-------|------|
| 1 | JWT generation | 8 | 1.5h |
| 2 | Login endpoint | 6 | 1h |
| 3 | Token refresh | 5 | 1h |
| **Total** | | **19** | **3.5h** |

## Files
- src/auth/jwt.py - JWT handling
- src/auth/routes.py - API endpoints
- tests/test_auth.py - Tests
```

### Phase Execution (1-2 hours each)

```
1. Implement the feature
2. Write tests
3. Run: pytest tests/ -v
4. All green? → git commit
5. Update plan if needed
```

### Commit Message

```
feat: Sprint 5 Phase 2 - Login endpoint (6 tests)

- POST /auth/login with email/password
- Returns JWT access + refresh tokens
- Handles invalid credentials

Cumulative: 8 + 6 = 14 tests
```

---

## Relationship to Other Approaches

SGD is one of many ways to structure development. Here's how it compares:

| | SGD | Agentic Dev | Scrum | Vibe Coding |
|---|---|---|---|---|
| **Scope** | Solo / small team | Solo + AI pair | Team | Anyone |
| **Planning** | Sprint plan doc | Memory system | Sprint board | None |
| **Unit of work** | Phase (1-2h) | Task | Story (1-2 weeks) | Whatever |
| **Verification** | Tests per phase | Tests + Gemini review | Sprint review | Hope |
| **Tooling** | Just tests | Claude + Gemini + Memory | Jira etc. | None |
| **Complexity** | Low | Medium-High | High | None |

SGD sits in a practical middle ground: **more structure than vibe coding, less overhead than full Agile/Agentic**.

---

## Document Structure

Three required documents:

### 1. `CLAUDE.md` — Project Overview
What you're building. Tech stack, architecture, directory structure.
Without this, you can't plan sprints because you don't know what you're building.

### 2. `SKILL.md` — Progress Tracker
Where you are right now. Cumulative tests, sprint history, current phase.
Without this, you can't plan the next sprint because you don't know where you are.

### 3. `SPRINT_XX_PLAN.md` — Current Sprint Plan
What you're doing this sprint. Phase breakdown, file list, test targets.
Created from [SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md).

### Flow
```
CLAUDE.md (what to build)
    → SKILL.md (where we are)
        → SPRINT_XX_PLAN.md (what to do next)
            → Implement → Test → Commit
                → Update SKILL.md
                    → Plan next sprint
```

---

## Validated In Practice

**AWS Guardian** (https://github.com/jinyounghwa/backend_loader) was built using this approach:

- ~41,000 lines of code (Lambda + Next.js)
- ~438 test functions across 42 test files
- 32+ sprints with documented plans and completions
- 1 developer, AI-assisted (Claude)

The project's `docs/sprints/` directory contains the actual sprint plans used during development.

---

## Getting Started

### 1. Copy the template
```bash
cp SPRINT_TEMPLATE.md SPRINT_01_PLAN.md
```

### 2. Define your first sprint
Break your feature into 3-5 phases with test targets.

### 3. Execute the cycle
```
For each phase:
  Implement → Test → Commit
```

### 4. Repeat
When the sprint is done, plan the next one.

---

## That's It

No frameworks to install. No tools to configure. Just:

1. **Plan** what you'll build
2. **Build** it in small phases
3. **Test** each phase
4. **Commit** when tests pass

---

**Last Updated:** 2026-05-24  
**Version:** 3.0
