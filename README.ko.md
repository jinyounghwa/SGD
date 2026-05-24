# SGD: Sprint-Guided Development Methodology

**[English](README.md) | 한국어**

---

## SGD란?

**SGD (Sprint-Guided Development)**는 하나의 핵심 아이디어로 구성된 실용적인 개발 방법론입니다:

> **작업을 작은 Phase로 나누고, 각 Phase를 테스트로 검증하고, 매 체크포인트마다 커밋한다.**

그게 전부입니다. 복잡한 도구도, 프레임워크 종속성도 없습니다. 그저:

```
Sprint 계획 → Phase 분해 → 구현 → 테스트 → 커밋 → 반복
```

---

## 왜 효과가 있는가?

### 문제: 구조 없는 개발

```
❌ 구조 없이:
  "인증 시스템 전체를 만들어야지"
  → 3일 코딩
  → 아무것도 안 됨
  → 뭐가 깨진지 모름
  → 처음부터 다시

✅ SGD:
  Sprint 5: 인증 시스템
    Phase 1: JWT 토큰 생성 (8 tests) → commit ✅
    Phase 2: 로그인 엔드포인트 (6 tests) → commit ✅
    Phase 3: 토큰 갱신 (5 tests) → commit ✅
    Phase 4: 로그아웃 + 정리 (4 tests) → commit ✅
```

각 Phase는 **한 번에 완료할 수 있을 만큼 작고**, **테스트로 검증**되며, **안전하게 커밋**됩니다.

### 실제로 도움이 되는 3가지

**1. Phase 분해**
- 코딩 전에 생각하게 강제
- 각 Phase는 관리 가능한 크기 (30분~2시간)
- 예측과 추적이 쉬움

**2. 테스트 체크포인트**
- 모든 Phase에 테스트 목표가 있음
- 뭔가 깨지면 즉시 알 수 있음
- "모든 테스트 통과" = 안전하게 커밋하고 다음으로 넘어가도 됨

**3. 매 Phase마다 커밋**
- 모든 커밋은 되돌리기 지점
- 커밋 메시지에 변경 내용과 테스트 수가 기록됨
- `git log --oneline`이 진행 보고서가 됨

---

## 사이클

### Sprint 계획 (30분)

`SPRINT_XX_PLAN.md` 작성:

```markdown
# Sprint 1: 사용자 인증

## Phases
| Phase | 기능 | 테스트 | 시간 |
|-------|------|--------|------|
| 1 | JWT 생성 | 8 | 1.5h |
| 2 | 로그인 엔드포인트 | 6 | 1h |
| 3 | 토큰 갱신 | 5 | 1h |
| **합계** | | **19** | **3.5h** |

## 파일
- src/auth/jwt.py - JWT 처리
- src/auth/routes.py - API 엔드포인트
- tests/test_auth.py - 테스트
```

### Phase 실행 (각 1-2시간)

```
1. 기능 구현
2. 테스트 작성
3. 실행: pytest tests/ -v
4. 모두 초록? → git commit
5. 필요시 계획 수정
```

### 커밋 메시지

```
feat: Sprint 5 Phase 2 - 로그인 엔드포인트 (6 tests)

- POST /auth/login with email/password
- JWT access + refresh 토큰 반환
- 잘못된 자격증명 처리

누적: 8 + 6 = 14 tests
```

---

## 다른 방식과의 관계

SGD는 개발을 구조화하는 여러 방법 중 하나입니다:

| | SGD | Agentic Dev | Scrum | Vibe Coding |
|---|---|---|---|---|
| **범위** | 1인 / 소규모 | 1인 + AI 페어 | 팀 | 누구나 |
| **계획** | Sprint 계획서 | Memory 시스템 | Sprint 보드 | 없음 |
| **작업 단위** | Phase (1-2h) | Task | Story (1-2주) | 자유 |
| **검증** | Phase별 테스트 | 테스트 + Gemini 리뷰 | Sprint 리뷰 | 희망 |
| **도구** | 테스트만 | Claude + Gemini + Memory | Jira 등 | 없음 |
| **복잡도** | 낮음 | 중간~높음 | 높음 | 없음 |

SGD는 실용적인 중간 지점에 있습니다: **Vibe coding보다 구조적이고, Agile/Agentic보다 오버헤드가 적습니다.**

---

## 문서 구조

세 개의 필수 문서:

### 1. `CLAUDE.md` — 프로젝트 개요
무엇을 만드는지. 기술 스택, 아키텍처, 디렉토리 구조.
이게 없으면 무엇을 만들지 모르니 Sprint를 계획할 수 없습니다.

### 2. `SKILL.md` — 진행 추적기
현재 어디에 있는지. 누적 테스트, Sprint 이력, 현재 Phase.
이게 없으면 현재 위치를 모르니 다음 Sprint를 계획할 수 없습니다.

### 3. `SPRINT_XX_PLAN.md` — 현재 Sprint 계획
이번 Sprint에서 할 것. Phase 분해, 파일 목록, 테스트 목표.
[SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md)에서 생성.

### 흐름
```
CLAUDE.md (무엇을 만들지)
    → SKILL.md (현재 어디인지)
        → SPRINT_XX_PLAN.md (다음에 할 것)
            → 구현 → 테스트 → 커밋
                → SKILL.md 업데이트
                    → 다음 Sprint 계획
```

---

## 실제로 검증됨

**AWS Guardian** (https://github.com/jinyounghwa/backend_loader) 은 이 방식으로 개발되었습니다:

- ~41,000줄 코드 (Lambda + Next.js)
- ~438개 테스트 함수, 42개 테스트 파일
- 32+ Sprint, 계획서와 완료 보고서 포함
- 1명 개발자, AI 보조 (Claude)

프로젝트의 `docs/sprints/` 디렉토리에 실제 사용된 Sprint 계획서가 있습니다.

---

## 시작하기

### 1. 템플릿 복사
```bash
cp SPRINT_TEMPLATE.md SPRINT_01_PLAN.md
```

### 2. 첫 Sprint 정의
기능을 3-5개 Phase로 나누고 테스트 목표 설정.

### 3. 사이클 실행
```
각 Phase마다:
  구현 → 테스트 → 커밋
```

### 4. 반복
Sprint가 끝나면 다음 것을 계획.

---

## 이게 전부

설치할 프레임워크도 없고, 설정할 도구도 없습니다. 그저:

1. **계획** — 무엇을 만들지 정의
2. **구현** — 작은 Phase로 나누어
3. **테스트** — 각 Phase마다
4. **커밋** — 테스트가 통과하면

---

**Last Updated:** 2026-05-24  
**Version:** 3.0
