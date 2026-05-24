# SGD: Sprint-Guided Development Methodology

**English | [한국어](README.ko.md)**

---

## Origin Story

### The Problem: Vibe Coding + AI Session Disconnection + Token Limits

Problems that arise when collaborating with AI (Claude) on small-to-medium projects:

**1. Session Disconnection Problem**
- Claude's context window is about 200K tokens (sufficient but limited)
- After extended development, context compression causes previous decisions to be lost
- Same mistakes repeated or architectural consistency breaks

**2. Limitations of Vibe Coding**
- Developing by feel scatters the structure
- Proceeding without tests requires large-scale bug fixes later
- Unclear which features are complete

**3. Complexity of Existing Approaches**
- Agentic Development (Claude + Gemini + Memory) is powerful but requires complex setup
- Harness-based testing requires SAM/Docker infrastructure
- Overkill for small-to-medium projects

---

## SGD's Solution

### Core Idea: Overcome Session Disconnection with Just 3 Documents

```
CLAUDE.md      → Full project overview (1 min read)
SKILL.md       → Current progress status (30 sec read)
SPRINT_XX_PLAN → Current Sprint plan (30 sec read)
```

**Key Points:**
- Even after session disconnects, **read 3 documents to recover in 2 minutes**
- Maintain context without the Agentic approach's Memory system
- Develop with Claude alone, no complex tool setup needed

### Sprint Gate: Safe Checkpoints

At the end of each Phase, **"All tests PASS"** = Recoverable state

```
Phase 1 (10 tests ✅)
    ↓
    [Git Commit]
    ↓
Phase 2 (8 tests ✅)
    ↓
    [Git Commit]
    ↓
Phase 3 (6 tests ✅)
    ↓
    [Git Commit]
```

---

## Comparison with Agentic/Harness Approach

| Item | Agentic Development | SGD (This Methodology) |
|------|-------------------|------------------------|
| **Tools** | Claude + Gemini CLI + Memory | Claude alone + 3 documents |
| **Memory** | `.claude/projects/memory/` | CLAUDE.md, SKILL.md |
| **Review** | External review via Gemini CLI | Self-verification via tests |
| **Harness** | SAM Local + Docker required | Regular pytest is sufficient |
| **Complexity** | High (bidirectional scripts, memory management) | Low (plan → implement → test → commit) |
| **Token Cost** | High (Gemini + memory reads) | Low (read only 3 documents) |
| **Session Recovery** | Search through Memory system | 1-minute recovery via SKILL.md + git log |
| **Learning Curve** | Medium~High | Low |
| **Best For** | Large + long-term projects | **Small-to-medium + limited tokens** |

> 💡 **Verified**: The Agentic approach requires `agentic-loop.sh`, Gemini CLI integration, and `.claude/projects/memory/` management.
> SGD achieves the same goal (preventing session disconnection) **more easily with just 3 documents and tests**.

---

## Overview

**SGD (Sprint-Guided Development)** is a methodology for developing small-to-medium software projects in limited token environments without session disconnection.

- **Purpose**: Complete projects with minimal tokens, no complex tools, in collaboration with AI
- **Tools**: Claude alone + 3 documents (CLAUDE.md, SKILL.md, SPRINT_XX_PLAN.md)
- **Validated**: AWS Guardian project (~438 tests, ~41,000 lines, 32+ Sprints)

---

## Core Principles

### 1️⃣ **Phase-Based Decomposition**
- Divide each Sprint into 3-5 small phases
- Each Phase = specific feature + tests + commit
- Phases are independently executable

### 2️⃣ **Clear Test Goals**
- Set specific test count per Phase
- Phase not complete until all tests PASS
- Tests = proof of reliability

### 3️⃣ **Minimum Documents for Context**
- CLAUDE.md: Full project overview
- SKILL.md: Current progress (per Sprint)
- SPRINT_XX_PLAN.md: Current Sprint detailed plan
- These 3 are sufficient for session recovery

### 4️⃣ **Token Efficiency**
- Minimize token consumption vs Agentic approach
- Keep documents concise
- Deliver only the context AI needs

### 5️⃣ **Git-Based Checkpoints**
- Commit at each Phase completion
- Include test count + progress info in commit message
- Track progress via git log alone

---

## Sprint Structure

```
Sprint N (Overall Goal)
├── Phase 1 (Feature A, Y tests)
│   ├── Implementation
│   ├── Tests (Y)
│   └── Commit
├── Phase 2 (Feature B, Y tests)
│   ├── Implementation
│   ├── Tests (Y)
│   └── Commit
├── Phase 3 (Feature C, Y tests)
└── ...
└── SKILL.md Update
```

---

## Development Cycle

### 1. Sprint Planning (30 min ~ 1 hour)

```markdown
# Sprint N: Sprint Title

## Current Status
- Previous Sprint complete: X tests
- Cumulative: Y tests

## Goals
- Phase 1: [Feature], Z tests
- Phase 2: [Feature], Z tests

## File List
- `path/file1.py` - [description]
- `path/file2.py` - [description]
```

### 2. Phase Implementation (2-4 hours)

```
1. Implement core classes/functions
2. Write comprehensive tests
3. Verify all tests PASS
4. Phase commit
   └── git commit -m "feat: Sprint N Phase M - [description] (Z tests)"
```

### 3. Session Recovery (when disconnected, 2 min)

```
1. Read SKILL.md → Locate current position (30 sec)
2. git log --oneline → Check completed Phases (10 sec)
3. SPRINT_XX_PLAN.md → Find next Phase (1 min)
4. Resume implementation ✅
```

---

## Real-World Example for Solo Developers

### Case Study: AWS Guardian

**Context:**
- Project: AWS Account Auto-Monitoring System (small-to-medium)
- Developer: 1 person
- Scale: ~41,000 lines, ~438 tests, 32+ Sprints
- AI Collaboration: Claude alone (frequent session disconnections)

### Actual Progress Pattern

```
Sprint 1-5: Foundation
  ├─ Phase 1: Lambda handler + tests (8 tests)
  ├─ Phase 2: DynamoDB integration + tests (6 tests)
  ├─ Phase 3: Telegram alerts + tests (5 tests)
  └─ Cumulative: ~19 tests

Sprint 6-15: Feature Expansion
  ├─ EC2/S3/IAM/Cost checkers (5-10 tests each)
  ├─ Discord dashboard (8 tests)
  ├─ Auto-response logic (12 tests)
  └─ Cumulative: ~150 tests

Sprint 16-32: Quality & Optimization
  ├─ Refactoring + type hints (15 tests)
  ├─ E2E integration tests (20 tests)
  ├─ Performance baseline (10 tests)
  └─ Cumulative: ~438 tests
```

### Session Disconnection Scenario

**Situation: Claude session disconnects during Phase 3**

```
[With Agentic approach]
1. Search through .claude/projects/memory/ for relevant files
2. Check MEMORY.md index
3. Read multiple feedback/project files
→ Recovery takes 5-10 min + high token cost

[With SGD]
1. Read SKILL.md (30 sec)
   "Sprint 20 Phase 1-2 complete, 250 tests passed"
2. git log --oneline (10 sec)
   "Last commit: Sprint 20 Phase 2"
3. Find Phase 3 in SPRINT_20_PLAN.md (1 min)
4. Resume Phase 3 implementation! ✅
→ Recovery takes 2 min + minimal tokens
```

### AI Collaboration Tips (Token Saving)

**Good Practice (token efficient):**
```markdown
Current Status:
- Complete: Sprint 15 Phase 1-2 (14 tests)
- In Progress: Sprint 15 Phase 3
- Plan: See SPRINT_15_PLAN.md

Next steps:
- Complete remaining Phase 3
- Verify all tests PASS
```

**Bad Practice (token waste):**
```
Show all code written so far
Explain history of all files
Request external review via Gemini CLI
```

---

## Benefits

✅ **Simplicity**
- Manage projects with just 3 documents + tests
- No complex tool setup required

✅ **Token Efficiency**
- Minimal token consumption vs Agentic approach
- 2-minute recovery + minimal tokens for session restore

✅ **Clear Progress**
- Objective measurement via cumulative test count
- Track history via git log

✅ **Session Safety**
- Per-Phase Git commit = recovery point
- Full status visible in a single SKILL.md file

---

## Checklist

### Before Sprint Start
- [ ] Write SPRINT_XX_PLAN.md
- [ ] Specify implementation files per Phase
- [ ] Set test count targets

### After Phase Completion
- [ ] Verify all tests PASS
- [ ] Write commit message (include test count)
- [ ] Update SKILL.md

### After Sprint Completion
- [ ] Verify all tests PASS
- [ ] Compile cumulative statistics
- [ ] Review next Sprint plan

---

## Applying to Other Projects

### Step 1: Project Analysis
```
Large Feature → Sprint Decomposition → Phase Decomposition → Implementation
(Example: Auth System → Sprint N → Phase 1-3 → OAuth, JWT, 2FA)
```

### Step 2: Create SGD Documents
- CLAUDE.md (project overview)
- SKILL.md (progress tracking)
- Copy SPRINT_TEMPLATE.md → SPRINT_01_PLAN.md

### Step 3: Execute First Sprint
- Implement Phase 1 + tests
- All tests PASS → Git commit
- Learn & adjust

### Step 4: Continuous Improvement
- Retrospective after each Sprint
- Monitor token usage
- Adjust process

---

## Resources

- `CLAUDE.md` / `CLAUDE.ko.md` - Developer project getting-started guide
- `SPRINT_TEMPLATE.md` - Sprint planning template
- `SKILL.md` - Progress tracking guide
- **Original Project**: AWS Guardian https://github.com/jinyounghwa/backend_loader

---

**Last Updated**: 2026-05-24  
**Version**: 2.0  
**Status**: Production-ready
