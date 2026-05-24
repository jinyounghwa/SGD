# CLAUDE.en.md: Developer Project Getting-Started Guide

**[한국어](CLAUDE.md) | English**

---

> **This guide explains how to apply the SGD methodology to develop small-to-medium projects in limited token environments without session disconnection.**

---

## About This Project

### Project Name
**AWS Guardian**: A serverless security and cost monitoring system that automatically watches AWS accounts and responds when threats are detected.
https://github.com/jinyounghwa/backend_loader

### Scale
- **Tests**: ~438 test functions
- **Code**: ~41,000 lines (Lambda 8,600 + Frontend 8,900 + Tests 9,200 + Infra)
- **Sprints**: 32+ Sprints (25 plans, 22 completion reports)
- **Methodology**: **SGD (Sprint-Guided Development)**

### Why Should You Look at This Project?
1. **Solo developer managing a small-to-medium project** — achievable with limited tokens
2. **AI collaboration** (Claude) — practical methods for development without session disconnection
3. **Complete documentation** — track the entire project with just 3 documents
4. **Validated methodology** — quality management proven with ~438 tests

---

## 🎯 Purpose of SGD

### Why Do You Need SGD?

**The Problem:**
```
When collaborating with AI (Claude/GPT):
  1. Token limit (200K) → Context compression in long sessions
  2. Session disconnection → Previous decisions lost
  3. Want to develop without complex tools
```

**SGD's Solution:**
```
Just 3 documents (CLAUDE.md, SKILL.md, SPRINT_XX_PLAN.md)
  → Recover in 1 minute even after session disconnects
  → No complex harness/memory system needed
  → Complete projects with minimal tokens
```

### Comparison with Agentic/Harness Approach

| Item | Agentic Development | SGD |
|------|-------------------|-----|
| **Tools** | Claude + Gemini CLI + Memory system | Claude alone + 3 documents |
| **Memory** | `.claude/projects/memory/` multiple files | CLAUDE.md, SKILL.md |
| **Review** | Code review via Gemini CLI | Self-verification via tests |
| **Complexity** | High (bidirectional collaboration scripts) | Low (plan → implement → test → commit) |
| **Token Cost** | High (Gemini calls + memory reads) | Low (read only 3 documents) |
| **Session Recovery** | Search through Memory system | 1-minute recovery via SKILL.md + git log |
| **Best For** | Large + long-term projects | **Small-to-medium + limited tokens** |

> 💡 **Key Insight**: The Agentic approach is powerful but requires complex setup and high token consumption.
> SGD focuses on **developing faster with fewer tools**.

---

## 🚀 Starting Your Own Project

### Step 1: Project Decomposition (1 hour)

**Breaking big features into Sprints:**

```
Your Idea
    ↓
Full Feature List (5-10 items)
    ↓
Sprint Decomposition (3-5 features/Sprint)
    ↓
Phase Decomposition (3-5 steps/Sprint)
    ↓
Ready to Implement!
```

**AWS Guardian Example:**
```
Overall: "AWS Account Auto-Monitoring System"
  ├─ Sprint 1-5: Foundation (Lambda, DynamoDB, Telegram)
  ├─ Sprint 6-10: Feature Expansion (CloudTrail, GuardDuty, Discord)
  ├─ Sprint 11-20: Advanced Features (Multi-region, Auto-response, Analytics)
  └─ Sprint 21-32: Quality & Optimization (Refactoring, E2E tests, Deployment)
```

### Step 2: Plan Your First Sprint (1 hour)

Copy SPRINT_TEMPLATE.md and create **SPRINT_01_PLAN.md**:

```
# Sprint 1: [Your First Feature]

## Current Status
- Previous project: none (new)
- Cumulative: 0 tests

## Goals
- Phase 1: [Feature A] (10 tests)
- Phase 2: [Feature B] (8 tests)
- Phase 3: [Feature C] (6 tests)

## File List
| File | Description |
|------|-------------|
| src/core.py | Core logic |
| tests/test_core.py | Tests |
```

### Step 3: Implement Your First Phase (2-3 hours)

**Phase 1 Cycle:**

```
1. Implement core classes/functions (~30 min)
   └─ Minimal functionality only (doesn't need to be perfect)

2. Write comprehensive tests (~1 hour)
   └─ Happy path + edge cases
   └─ e.g., test_core_basic, test_core_with_edge_case

3. Verify all tests PASS (~10 min)
   └─ pytest tests/ -v ✅

4. Git Commit (~5 min)
   └─ feat: Sprint 1 Phase 1 - [Feature] (10 tests)

Result: First checkpoint complete! ✅
```

---

## 📁 Project Structure (Reference)

### SGD Document Structure

```
project-root/
├── SGD/                           # Methodology docs (must include!)
│   ├── README.md                  # Methodology explanation
│   ├── CLAUDE.md                  # This file
│   ├── SKILL.md                   # Progress tracking
│   └── SPRINT_TEMPLATE.md         # Planning template
│
├── src/                           # Core implementation (language/framework free)
├── tests/                         # Tests (very important!)
├── SPRINT_01_PLAN.md              # First Sprint plan
├── SPRINT_02_PLAN.md              # Second Sprint plan
└── README.md                      # Project README
```

### AWS Guardian Directory Structure (Actual Example)

```
backend_loader/
├── lambda/guardian/               # Lambda functions (~8,600 lines, 55 files)
│   ├── checkers/                  # Security checks (EC2, S3, IAM, Cost...)
│   ├── responders/                # Auto-response (Telegram, Discord...)
│   ├── storage/                   # Data storage (DynamoDB)
│   ├── analytics/                 # Analytics (cost, optimization)
│   └── handlers/                  # Entry points
│
├── apps/web/                      # Next.js dashboard (~8,900 lines, 84 files)
│   ├── src/components/Dashboard/  # UI components
│   └── src/app/api/               # API routes
│
├── tests/                         # Tests (~9,200 lines, 42 files, ~438 tests)
│   ├── lambda/                    # Lambda tests (harness, contract, performance)
│   ├── guardian/                  # Integration tests
│   └── cloudformation/            # Infrastructure tests
│
├── terraform/                     # IaC (~923 lines)
├── docs/sprints/                  # Sprint documents (54 files)
└── sam/                           # Deployment config
```

---

## 🧪 Test-Centric Development (Core!)

### Why Are Tests Important?

**SGD Core: "All tests PASS" = Safe Checkpoint**

```
❌ Vibe Coding (Risky)
Partial implementation → Unclear state → Bug fixes later

✅ SGD (Safe)
Phase 1 (10 tests) → All PASS → Git Commit ✅
Phase 2 (8 tests) → All PASS → Git Commit ✅
Phase 3 (6 tests) → All PASS → Git Commit ✅
```

### Test Writing Example (Python)

```python
# tests/test_feature.py
def test_feature_basic():
    """Basic feature test"""
    result = feature.execute()
    assert result is not None
    assert len(result) > 0

def test_feature_with_invalid_input():
    """Invalid input handling"""
    with pytest.raises(ValueError):
        feature.execute(invalid_param=True)

def test_feature_performance():
    """Performance test"""
    import time
    start = time.time()
    feature.execute()
    elapsed = time.time() - start
    assert elapsed < 1.0  # Under 1 second
```

### Running & Verifying Tests

```bash
# Run all tests
pytest tests/ -v

# Run specific file only
pytest tests/test_feature.py -v

# Example result
tests/test_feature.py::test_feature_basic PASSED [33%]
tests/test_feature.py::test_feature_with_invalid_input PASSED [66%]
tests/test_feature.py::test_feature_performance PASSED [100%]

========================= 3 passed in 0.15s =========================
```

---

## 📋 Three Essential Documents

### 1. This File (CLAUDE.md): Project Overview
- What the project is
- How developers can get started
- Architecture overview

### 2. SKILL.md: Progress Tracking
- Sprint-by-sprint status (✅ Complete / 🔄 In Progress / ⏳ Planned)
- Cumulative test count
- Timeline and milestones

### 3. SPRINT_XX_PLAN.md: Detailed Plan per Sprint
- Implementation files per Phase
- Test strategy
- Expected issues & solutions

**With just these 3 documents, even a solo developer can manage a small-to-medium project without session disconnection!**

---

## 💡 Learning from the AWS Guardian Case Study

### Actual Progress

**AWS Guardian completed ~41,000 lines of code validated with ~438 tests across 32+ Sprints.**

```
Sprint 1-5: Foundation (~5 hours)
  └─ Lambda handlers + DynamoDB + Telegram alerts

Sprint 6-15: Feature Expansion (~15 hours)
  └─ EC2/S3/IAM/Cost checkers + Discord dashboard + Auto-response

Sprint 16-25: Advanced Features (~12 hours)
  └─ Multi-region + Parallel orchestrator + ML anomaly detection + WebSocket

Sprint 26-32: Quality & Deployment (~8 hours)
  └─ Refactoring + E2E tests + Performance optimization + LocalStack deployment
```

### Session Disconnection Scenario

**Situation: Claude session disconnects during Phase 3**

```
[Solution]

1. Read SKILL.md (30 seconds)
   "Sprint 28 Phase 1-2 complete, 380 tests passed"

2. Check git log (10 seconds)
   "Last commit: Sprint 28 Phase 2"

3. Find Phase 3 in SPRINT_28_PLAN.md (1 minute)
   "Phase 3 target: E2E tests + performance baseline (12 tests)"

4. Resume Phase 3 implementation! ✅
```

> 💡 **With the Agentic approach?** You'd need to search through `.claude/projects/memory/` for relevant memory files.
> SGD provides all context in **a single SKILL.md file**.

---

## 🎯 Checklist to Follow

### ✅ Before Starting a Project
- [ ] Create SGD folder (README.md, CLAUDE.md, SKILL.md, SPRINT_TEMPLATE.md)
- [ ] Plan first Sprint (SPRINT_01_PLAN.md)
- [ ] Create basic project structure (src/, tests/)

### ✅ Each Phase
- [ ] Implement core classes (30 min)
- [ ] Write comprehensive tests (1 hour)
- [ ] Verify all tests PASS (10 min)
- [ ] Git commit (5 min)

### ✅ After Each Sprint Completion
- [ ] Update progress in SKILL.md
- [ ] Check all commits with git log
- [ ] Review next Sprint plan

---

## 🔧 Tech Stack Selection (Flexible!)

AWS Guardian uses the following, but **choose what fits your project:**

| Layer | AWS Guardian | Your Choice |
|-------|--------------|-------------|
| **Language** | Python 3.12 | Free (Java, Go, Rust...) |
| **Testing** | pytest | Free (unittest, JUnit...) |
| **Deployment** | AWS Lambda + SAM | Free (Docker, Kubernetes...) |
| **Data** | DynamoDB | Free (PostgreSQL, MongoDB...) |

**Important:** The methodology (SGD) doesn't change! Only the implementation differs.

---

## 📚 Next Steps

1. **Reading this file complete** ✅
2. **Read README.md** — Understand SGD methodology
3. **Read SKILL.md** — Understand progress tracking
4. **Copy SPRINT_TEMPLATE.md** — Plan first Sprint
5. **Start Phase 1 implementation** — Write code!

---

## 🆘 Troubleshooting

### "How do I start Phase 1?"
→ See the "Implementation Strategy" section in SPRINT_TEMPLATE.md

### "How many tests should I write?"
→ Rule: 1-3 tests per feature
  (Simple feature: 1, Complex feature: 3-5)

### "How do I collaborate with AI (Claude)?"
→ See "Real-world Example for Solo Developers" in README.md

### "Should I use Agentic or SGD?"
→ Small-to-medium + limited tokens → **SGD** (simple, low token cost)
→ Large + long-term + multi-AI → Agentic (powerful, complex)

---

## 📞 References

- **Methodology**: README.md (full explanation)
- **Progress**: SKILL.md (current status)
- **Plans**: SPRINT_XX_PLAN.md (per Sprint)
- **Original Project**: AWS Guardian https://github.com/jinyounghwa/backend_loader

---

**SGD: Complete small-to-medium projects with minimal tokens, without session disconnection.** 💪

---

**Last Updated:** 2026-05-24  
**Version:** 2.0 - Developer Getting-Started Guide
