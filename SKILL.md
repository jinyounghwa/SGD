# SKILL.md: Sprint Progress Tracker (Required)

**English | [한국어](SKILL.ko.md)**

---

> **This file is required.** It tracks what's done and what's next.
> Without it, you can't create sprint plans because you don't know where you are.

---

## Current Project

| Item | Value |
|------|-------|
| **Project** | [Your Project] |
| **Current Sprint** | [N] |
| **Tests Passed** | [X] |
| **Tests Target** | [Y] |

---

## Sprint Timeline

### ✅ Sprint 1: [Title]
- **Tests**: [N]
- **Cumulative**: [N]
- **Status**: ✅ Complete

### ✅ Sprint 2: [Title]
- **Tests**: [N]
- **Cumulative**: [N+N]
- **Status**: ✅ Complete

### 🔄 Sprint 3: [Title] (Current)
- **Phase 1**: [Feature] (N tests) ✅
- **Phase 2**: [Feature] (N tests) 🔄
- **Phase 3**: [Feature] (N tests) ⏳

---

## Milestones

| Date | Event | Tests |
|------|-------|-------|
| YYYY-MM-DD | Sprint 1 complete | N ✅ |
| YYYY-MM-DD | Sprint 2 complete | N ✅ |
| YYYY-MM-DD | Sprint 3 Phase 1 complete | N ✅ |

---

## Update Guide

**After each Phase:**
1. Update the Phase status (🔄 → ✅)
2. Update cumulative test count
3. Add milestone entry
4. Commit: `git commit -m "docs: SKILL.md - Sprint X Phase Y (N tests)"`

**After Sprint Complete:**
1. Write `SPRINT_XX_COMPLETION.md` (test results, architecture, metrics)
2. Update SKILL.md with final results
3. Commit: `git commit -m "docs: Sprint X complete - COMPLETION.md + SKILL.md"`

> 💡 **Claude Code Memory:** `SPRINT_XX_COMPLETION.md` serves as AI memory.
> The AI references previous completion reports when planning the next sprint, resulting in more accurate plans.

---

**Last Updated:** 2026-05-26
