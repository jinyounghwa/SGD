# SKILL.md: Sprint 진행 추적기 (선택 사항)

**[English](SKILL.md) | 한국어**

---

> 이 파일은 선택 사항입니다. `git log --oneline`로도 같은 정보를 얻을 수 있습니다.
> git history보다 단일 대시보드 파일을 선호할 때만 사용하세요.

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

**아니면 그냥 안 해도 됩니다.** `git log`를 대신 쓰세요.

---

**Last Updated:** 2026-05-24
