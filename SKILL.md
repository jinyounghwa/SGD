# SKILL.md: Sprint Progress Tracking Guide

**English | [한국어](SKILL.ko.md)**

---

> A dashboard that tracks the meta information and cumulative progress of a small-to-medium project using SGD — at a glance.
> **Key**: This single file lets you grasp the current status in 30 seconds after a session disconnection.

---

## Purpose

This document **tracks the real-time progress of each Sprint in an ongoing project.**
- 💡 **Anyone can see** where things stand right now
- 📊 **Objective** metrics (test count, code volume, development time)
- 🎯 **Next steps** clearly indicated

---

## Project Status Overview

Fill in your project information using this template:

| Item | Example | Description |
|------|---------|-------------|
| **Project Name** | AWS Guardian / Your Project | Name of the project in progress |
| **Current Sprint** | 38 / N | Current Sprint number |
| **Total Tests Completed** | 153 / Total Tests | Number of tests that have PASSED so far |
| **Total Tests Planned** | 332 / Full Target | Target test count when project is complete |
| **Completion Rate** | 46% | (Completed tests / Planned tests) × 100 |
| **Total Code Lines** | 76,000+ | Total lines of code written so far |
| **Development Time** | ~35 hours | Development time spent so far |

---

## Sprint Progress Timeline

This section **records each Sprint's goal, test count, and status in chronological order.**

> 💡 **Writing Pattern:**
> - When a Sprint is complete, change status to `✅ Complete`
> - If in progress: `🔄 In Progress`, if planning stage: `⏳ Planned`
> - Specify which features were implemented per Phase
> - Write goals and features to match your project

### ✅ Sprint 1: Foundation
- **Duration**: 4 hours
- **Goal**: [Project first-step goal]
- **Tests**: 22
- **Cumulative**: 22 tests
- **Status**: ✅ Complete

**Phase Structure:**
- Phase 1: [Feature 1] (9 tests)
- Phase 2: [Feature 2] (5 tests)
- Phase 3: [Feature 3] (4 tests)
- Phase 4: [Feature 4] (4 tests)

### ✅ Sprint 2: Core Feature Expansion
- **Duration**: 5 hours
- **Goal**: [Second step goal]
- **Tests**: 36
- **Cumulative**: 58 tests
- **Status**: ✅ Complete

**Phase Structure:**
- Phase 1: [Feature A] (12 tests)
- Phase 2: [Feature B] (15 tests)
- Phase 3: [Feature C] (9 tests)

### ✅ Sprint 3: Advanced Feature Development
- **Duration**: 8 hours
- **Goal**: [Third step goal]
- **Tests**: 56
- **Cumulative**: 114 tests
- **Status**: ✅ Complete

**Phase Structure:**
- Phase 1: [Feature 1] (15 tests)
- Phase 2: [Feature 2] (14 tests)
- Phase 3: [Feature 3] (15 tests)
- Phase 4: [Feature 4] (12 tests)

### 🔄 Sprint 4: Integration & Optimization
- **Duration**: Estimated 12 hours (in progress)
- **Goal**: [Fourth step goal]
- **Tests**: Total 65 planned
- **Cumulative**: [Current] / [Target] tests
- **Status**: 🔄 In Progress

**Phase Progress:**
- Phase 1: [First Task] (23 tests) ✅
  - [Detail 1]
  - [Detail 2]
  - [Detail 3]
  - [Detail 4]

- Phase 2: [Second Task] (16 tests) ✅
  - [Detail 1]
  - [Detail 2]
  - [Detail 3]
  - [Detail 4]

- Phase 3: [Third Task] (8 tests) 🔄 In Progress
  - [Detail 1]
  - [Detail 2]
  - [Detail 3]
  - [Detail 4]

- Phase 4: [Fourth Task] (12 tests) ⏳ Planned
  - [Detail 1]
  - [Detail 2]
  - [Detail 3]
  - [Detail 4]

- Phase 5: [Fifth Task] (10 tests) ⏳ Planned
  - [Detail 1]
  - [Detail 2]
  - [Detail 3]
  - [Detail 4]

---

## Cumulative Statistics

**Record objective metrics for your ongoing project.**

### Test Count

Update this table as you progress to visually track cumulative progress:

```
Sprint 1:   22 tests ████░░░░░░░░░░░░░░░░░ 22 total
Sprint 2:   36 tests ██████░░░░░░░░░░░░░░░░ 58 total
Sprint 3:   56 tests █████████░░░░░░░░░░░░░ 114 total
Sprint 4:   65 tests (planned)
            └─ Phase 1: 23 tests ✅
            └─ Phase 2: 16 tests ✅
            └─ Phase 3: 8 tests 🔄
            └─ Phase 4: 12 tests ⏳
            └─ Phase 5: 10 tests ⏳

Target: [Total target test count]
```

> **Tip**: Displaying cumulative tests per Sprint helps you see if your pace is improving.

### Code Scale

Track how much your project has grown:

- **Total Code Lines**: [Project LOC]
- **Backend Logic**: [Backend LOC]
- **Test Code**: [Test LOC] ([ratio]% of total code)
- **Frontend**: [Frontend LOC]
- **Infrastructure/Config**: [Infra LOC]

> 💡 **Tip**: Periodically calculating LOC helps track increasing project complexity.
> ```bash
> # Backend code
> find src -name "*.py" -o -name "*.js" -o -name "*.ts" | xargs wc -l | tail -1
> # Test code
> find tests -name "*.py" -o -name "*.test.js" -o -name "*.test.ts" | xargs wc -l | tail -1
> ```

### Development Velocity

Measure your project's speed and efficiency:

- **Average Phase Time**: [Project average] hours
- **Average Tests/Hour**: [Project average] tests/hour
- **Total Development Time**: [Cumulative hours]

> 💡 **Interpretation**:
> - Higher tests/hour = more efficient development (helped by team collaboration, automation)
> - Decreasing time per Phase means the development process is stabilizing (learning curve flattening)
> - Estimated completion = (Remaining tests) / (Average tests/hour)
> - Example: 50 remaining tests, average 10 tests/hour = 5 hours

---

## Key Milestones

Record your project's major completion points in chronological order:

| Date | Event | Tests | Progress |
|------|-------|-------|----------|
| YYYY-MM-DD | Sprint 1 Complete | 22 ✅ | 7% |
| YYYY-MM-DD | Sprint 2 Complete | 58 ✅ | 18% |
| YYYY-MM-DD | Sprint 3 Complete | 114 ✅ | 34% |
| YYYY-MM-DD | Sprint 4 Phase 1-2 Complete | 153 ✅ | 46% |
| YYYY-MM-DD | [Important Event] | - | - |
| YYYY-MM-DD | Sprint 4 Phase 3 Started | 🔄 | - |
| YYYY-MM-DD | Sprint 4 Completion Planned | [Target] ✅ | 100% |

> 💡 **Tip**: Documenting milestones makes it easy to explain progress to team members or stakeholders.
> - Record immediately after each Sprint completion
> - Include estimated completion dates for easier schedule management

---

## Technical Debt Tracking

Organize items that need to be resolved in your project by priority:

### Low (No action needed)
- ✅ Good code cohesion
- ✅ Test coverage >90%
- ✅ Sufficient documentation

### Medium (Improvement recommended)
- ⚠️ [Item needing improvement 1] (current state)
- ⚠️ [Item needing improvement 2] (current state)

Examples:
- ⚠️ Add end-to-end (e2e) tests (Currently: unit tests only)
- ⚠️ Implement load testing (Currently: functional tests only)
- ⚠️ Write API documentation (Currently: basic README only)

### High (Not yet implemented)
- 🔴 [Major unimplemented item 1] (Priority: Low/Medium/High)
- 🔴 [Major unimplemented item 2] (Priority: Low/Medium/High)

Examples:
- 🔴 Multi-region/multi-tenant support (Priority: Low)
- 🔴 ML-based analysis addition (Priority: Low)
- 🔴 Mobile app development (Priority: Medium)

---

## Next Milestone

### Current Sprint Completion Criteria

```
[ ] Phase 1: [Feature Name] (NN tests) - [Status]
[ ] Phase 2: [Feature Name] (NN tests) - [Status]
[ ] Phase 3: [Feature Name] (NN tests) - [Status]
[ ] All tests PASS
[ ] Git commit
```

Example:
```
[ ] Phase 3: Cost Management Features (8 tests) - In Progress
[ ] Phase 4: Dashboard UI Improvements (12 tests) - Planned
[ ] Phase 5: Multi-Account Support (10 tests) - Planned
[ ] Total 332 tests PASS
```

### Next Sprint Plan

```
Sprint N - [Topic]
- **Goal**: [Goal description]
- **Tests**: [Expected test count]
- **Cumulative**: [Cumulative test count]
- **Priority**: High / Medium / Low
```

Example:
```
Sprint 5 - ML-Based Analysis
- **Goal**: Data pattern learning + auto-classification + performance benchmarking
- **Tests**: 25-30 tests
- **Cumulative**: 357-362 tests
- **Priority**: Medium
```

---

## Team/Collaboration Information

Document the team members participating in the project and their roles:

| Role | Name | Status | Area |
|------|------|--------|------|
| Lead Developer | [Name] | 🟢 Active | [Responsible area] |
| Supporting Developer | [Name] | 🟢 Active | [Responsible area] |
| Code Review | [Name] | 🟢 Active | [Responsible area] |
| QA / Tester | [Name] | 🟡 Paused | [Responsible area] |

**Status Legend**: 🟢 Active (currently working), 🟡 Paused (temporarily suspended), ⚫ N/A (not set), 🔴 Blocked

Example:
| Role | Name | Status | Area |
|------|------|--------|------|
| Lead Developer | Alice | 🟢 Active | Backend + Infrastructure |
| Frontend Developer | Bob | 🟢 Active | Web UI + Dashboard |
| Code Reviewer | Charlie | 🟢 Active | Code quality + Testing |
| Tech Lead | (TBD) | ⚫ N/A | - |

---

## Checklist (Current Sprint)

Track all tasks for the ongoing Sprint step by step.

### Planning Stage
- [ ] Write SPRINT_XX_PLAN.md
- [ ] Specify implementation files per Phase
- [ ] Set test count targets
- [ ] Team review and approval

### Phase 1: [First Feature]
- [ ] [Implementation item 1]
- [ ] [Implementation item 2]
- [ ] Write [N] tests
- [ ] All tests PASS
- [ ] Git commit: `feat: Sprint X Phase 1 - [Feature Name]`

### Phase 2: [Second Feature]
- [ ] [Implementation item 1]
- [ ] [Implementation item 2]
- [ ] Write [N] tests
- [ ] All tests PASS
- [ ] Git commit: `feat: Sprint X Phase 2 - [Feature Name]`

### Phase 3: [Third Feature]
- [ ] [Implementation item 1]
- [ ] [Implementation item 2]
- [ ] Write [N] tests
- [ ] All tests PASS
- [ ] Git commit: `feat: Sprint X Phase 3 - [Feature Name]`

### Wrap-up
- [ ] Confirm all Phases complete
- [ ] Update cumulative statistics
- [ ] Update SKILL.md
- [ ] Plan next Sprint

**Example (Actual Project Checklist):**

### Planning Stage
- [x] Write SPRINT_4_PLAN.md
- [x] Specify implementation files per Phase
- [x] Set test count targets
- [x] Team review and approval

### Phase 1: API Integration Verification
- [x] Implement RestClient
- [x] Add error handling
- [x] Write 12 tests
- [x] All tests PASS
- [x] Git commit

### Phase 2: Data Caching
- [x] Implement CacheLayer
- [x] TTL management logic
- [x] Write 8 tests
- [x] All tests PASS
- [x] Git commit

### Phase 3: Performance Optimization
- [ ] Query optimization
- [ ] Add indexing
- [ ] Write 10 tests
- [ ] All tests PASS
- [ ] Git commit (in progress)

---

## Document Links & Usage

This SKILL.md serves as the **meta dashboard for your ongoing project.**

### Standard Project Structure

```
project-root/
├── CLAUDE.md              ← Project overview + dev guide
├── README.md              ← Project introduction (external)
│
├── SGD/                   ← SGD methodology docs
│   ├── SKILL.md           ← This file (progress tracking)
│   ├── SKILL.ko.md      ← Korean version
│   ├── CLAUDE.md          ← Developer getting-started guide
│   ├── CLAUDE.ko.md       ← Korean version
│   ├── README.md          ← SGD methodology explanation
│   ├── README.ko.md       ← Korean version
│   └── SPRINT_TEMPLATE.md ← Sprint planning template
│
├── SPRINT_01_PLAN.md      ← Sprint 1 detailed plan
├── SPRINT_02_PLAN.md      ← Sprint 2 detailed plan
├── SPRINT_XX_PLAN.md      ← Detailed plan for each Sprint
│
└── /tests                 ← Test code (per Phase)
```

### Document Roles

| Document | Purpose | When Written | Update Frequency |
|----------|---------|-------------|-----------------|
| CLAUDE.md | Project overview and dev method | Project start | Only when needed |
| SPRINT_XX_PLAN.md | Detailed plan per Sprint | Before Sprint start | At Sprint start |
| SKILL.md (this file) | Progress tracking dashboard | After first Sprint starts | After Phase completion |

### Typical Usage Flow

1. **Project Start**
   - Write CLAUDE.md (project overview)
   - Write README.md (project introduction)

2. **Sprint Start**
   - Write SPRINT_XX_PLAN.md
   - Add Sprint info in SKILL.md

3. **Phase Completion**
   - Update checklist in SKILL.md
   - Refresh cumulative statistics
   - Git commit

4. **Sprint Completion**
   - Update milestones in SKILL.md
   - Add next Sprint plan

---

## Document Maintenance Guide

### After Phase Completion (every Phase)
1. Update the corresponding Phase checkbox in the checklist (`[ ]` → `[x]`)
2. **Update "Cumulative Statistics" section:**
   - Change Sprint's cumulative test count
   - Recalculate completion rate
3. **Update "Key Milestones" section:**
   - Add today's date and event
4. Git commit:
   ```bash
   git add SKILL.md
   git commit -m "docs: Update SKILL.md - Sprint X Phase Y complete (NN tests)"
   ```

### At Sprint Start (every Sprint)
1. Change "Current Sprint" number in "Project Status Overview" section
2. Add new Sprint entry in "Sprint Progress Timeline" section
3. Update checklist in "Next Milestone"
4. Check "Team/Collaboration Info" (update if changed)

### Weekly (weekly review)
1. **Calculate completion rate**: `(Completed tests / Planned tests) × 100`
2. **Check development velocity**: `Cumulative tests / Cumulative hours`
3. **Calculate estimated completion**: `(Remaining tests) / (Average tests/hour)`
4. Modify "Next Milestone" if needed

### Quarterly (or monthly review)
1. Refresh cumulative statistics (code scale, development time)
2. Revisit and update technical debt
3. Check team status and roles

---

## Quick Reference

| Situation | Action |
|-----------|--------|
| Phase ended | Update cumulative tests + record milestone + commit |
| Sprint started | Add Sprint info + initialize checklist |
| Weekly review | Calculate completion rate / velocity + check estimated completion |
| Bug/delay | Record in technical debt section + adjust next milestone |

---

**Last Updated:** 2026-05-24  
**Next Update:** After Sprint 38 Phase 3 completion  
**Project Owner:** jinyounghwa
