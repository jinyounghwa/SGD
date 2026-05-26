# SKILL.md: Sprint 진행 추적기 (필수)

**[English](SKILL.md) | 한국어**

---

> **이 파일은 필수입니다.** 완료된 것과 다음 할 것을 추적합니다.
> 이게 없으면 현재 위치를 모르니 Sprint 계획을 세울 수 없습니다.

---

## 현재 프로젝트

| 항목 | 값 |
|------|-----|
| **프로젝트** | [프로젝트명] |
| **현재 Sprint** | [N] |
| **통과한 테스트** | [X] |
| **테스트 목표** | [Y] |

---

## Sprint 타임라인

### ✅ Sprint 1: [제목]
- **테스트**: [N]
- **누적**: [N]
- **상태**: ✅ 완료

### ✅ Sprint 2: [제목]
- **테스트**: [N]
- **누적**: [N+N]
- **상태**: ✅ 완료

### 🔄 Sprint 3: [제목] (현재)
- **Phase 1**: [기능] (N tests) ✅
- **Phase 2**: [기능] (N tests) 🔄
- **Phase 3**: [기능] (N tests) ⏳

---

## 마일스톤

| 날짜 | 이벤트 | 테스트 |
|------|--------|--------|
| YYYY-MM-DD | Sprint 1 완료 | N ✅ |
| YYYY-MM-DD | Sprint 2 완료 | N ✅ |
| YYYY-MM-DD | Sprint 3 Phase 1 완료 | N ✅ |

---

## 업데이트 가이드

**각 Phase 후:**
1. Phase 상태 업데이트 (🔄 → ✅)
2. 누적 테스트 수 업데이트
3. 마일스톤 항목 추가
4. 커밋: `git commit -m "docs: SKILL.md - Sprint X Phase Y (N tests)"`

**Sprint 완료 후:**
1. `SPRINT_XX_COMPLETION.md` 작성 (테스트 결과, 아키텍처, 메트릭)
2. SKILL.md에 최종 결과 업데이트
3. 커밋: `git commit -m "docs: Sprint X complete - COMPLETION.md + SKILL.md"`

> 💡 **Claude Code Memory:** `SPRINT_XX_COMPLETION.md`는 AI의 메모리 역할을 합니다.
> 다음 Sprint 계획 시 AI가 이전 완료 보고서를 참조하여 더 정확한 계획을 세웁니다.

---

**Last Updated:** 2026-05-26
