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

### Sprint 계획

두 가지 옵션이 있습니다:

**옵션 A: 수동 (30분)**

[템플릿](SPRINT_TEMPLATE.md)을 사용하여 직접 `SPRINT_XX_PLAN.md`를 작성합니다.

**옵션 B: AI 생성 (5분)**

Claude(또는 다른 AI)에게 Sprint 계획 생성을 요청합니다. 이 프롬프트를 사용하세요:

```
CLAUDE.md와 SKILL.md를 읽고:
1. git log로 최근 커밋을 확인
2. 테스트를 실행하여 현재 상태 확인
3. SPRINT_TEMPLATE.md 형식으로 SPRINT_XX_PLAN.md 생성
   적절한 Phase, 파일 목록, 테스트 목표 포함
```

AI는:
1. CLAUDE.md 읽기 → 프로젝트가 무엇인지 이해
2. SKILL.md 읽기 → 현재 위치 파악
3. git log 분석 → 방금 완료된 것 확인
4. SPRINT_XX_PLAN.md 생성 → 다음 Sprint 제안

리뷰하고 조정한 후 구현을 시작합니다.

> 💡 AWS Guardian이 이 방식으로 개발되었습니다 — Claude가
> CLAUDE.md + SKILL.md + git log를 기반으로 Sprint 계획을 생성하고
> 개발자가 이를 리뷰했습니다.

### 3단계 Sprint 워크플로우 (Claude Code Memory)

**Claude Code**(또는 메모리 기능이 있는 AI 코딩 에이전트)를 사용할 때,
각 Sprint는 검증된 3단계 사이클을 따릅니다:

```
1. SPRINT_XX_PLAN.md       →  구현 전 상세 설계
2. 구현                    →  서비스, 핸들러, 테스트 작성
3. SPRINT_XX_COMPLETION.md →  테스트 결과, 아키텍처, 메트릭
```

**왜 3단계인가?**

| 단계 | 문서 | 목적 |
|------|------|------|
| **계획** | `SPRINT_XX_PLAN.md` | 코딩 전에 무엇을 만들지 정의. 범위 확장 방지. |
| **구현** | (코드 + 테스트) | 만들기. 각 Phase를 테스트로 검증. |
| **완료 보고서** | `SPRINT_XX_COMPLETION.md` | 실제로 무슨 일이 있었는지 기록. AI 메모리에 저장되어 다음 Sprint 계획에 활용. |

완료 보고서는 AI 에이전트와 함께 사용할 때 특히 강력합니다 — 테스트 결과, 아키텍처 결정, 메트릭을 명확하게 기록하여
다음 Sprint 계획이 더 정확해집니다.

> 💡 **Claude Code Memory 팁:** 이 3단계 워크플로우를
> `CLAUDE.md`에 추가하면 AI 에이전트가 자동으로 따릅니다:
> ```
> 1. SPRINT_XX_PLAN.md 작성 (구현 전 상세 설계)
> 2. 구현 (서비스, 핸들러, 테스트 작성)
> 3. SPRINT_XX_COMPLETION.md 작성 (테스트 결과, 아키텍처, 메트릭)
> ```

### Sprint 계획 예시

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

Sprint당 4개 문서:

### 1. `CLAUDE.md` — 프로젝트 개요
무엇을 만드는지. 기술 스택, 아키텍처, 디렉토리 구조.
이게 없으면 무엇을 만들지 모르니 Sprint를 계획할 수 없습니다.

### 2. `SKILL.md` — 진행 추적기
현재 어디에 있는지. 누적 테스트, Sprint 이력, 현재 Phase.
이게 없으면 현재 위치를 모르니 다음 Sprint를 계획할 수 없습니다.

### 3. `SPRINT_XX_PLAN.md` — Sprint 계획서 (Step 1)
이번 Sprint에서 할 것. Phase 분해, 파일 목록, 테스트 목표.
[SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md)에서 생성.
**구현 전**에 작성합니다.

### 4. `SPRINT_XX_COMPLETION.md` — Sprint 완료 보고서 (Step 3)
실제로 무슨 일이 있었는지. 테스트 결과, 아키텍처 결정, 메트릭.
**구현 완료 후**에 작성합니다.

### 흐름
```
CLAUDE.md (무엇을 만들지)
    → SKILL.md (현재 어디인지)
        → SPRINT_XX_PLAN.md (다음에 할 것)           ← Step 1
            → 구현 → 테스트 → 커밋                  ← Step 2
                → SPRINT_XX_COMPLETION.md (무슨 일이 있었는지) ← Step 3
                    → SKILL.md 업데이트
                        → 다음 Sprint 계획 (수동 또는 AI 생성)
```

### AI Sprint 생성

CLAUDE.md + SKILL.md + 이전 COMPLETION 보고서는 이중 목적을 가집니다:
1. **개발자**가 프로젝트 상태를 이해하기 위해 읽음
2. **AI**가 다음 Sprint 계획을 생성하기 위해 읽음

이 문서들이 없으면 AI가 의미 있는 Sprint 계획을 생성할 수 없습니다.
이것이 필수인 이유입니다.

### 완료 보고서의 이점

`SPRINT_XX_COMPLETION.md`는 단순한 문서가 아닙니다 — **AI 메모리**입니다:

- **테스트 결과** → AI가 정확히 무엇이 검증되었는지 알 수 있음
- **아키텍처 결정** → AI가 코드가 왜 이렇게 구성되었는지 이해
- **메트릭** → AI가 속도를 추적하고 더 나은 예측 가능
- **발생한 이슈** → AI가 같은 실수를 반복하지 않음

이것이 3단계 워크플로우의 핵심 이점입니다: 각 Sprint의 완료 보고서가
AI의 다음 Sprint 계획을 더 정확하고 정보에 기반하게 만듭니다.

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

### 1. CLAUDE.md 작성
프로젝트 개요를 작성합니다. 기술 스택, 아키텍처, 무엇을 만드는지.

### 2. SKILL.md 작성
진행 추적기를 설정합니다. 초기 상태: 0 테스트, 아직 Sprint 없음.

### 3. 첫 Sprint 계획 생성

**수동:** [SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md)를 복사하여 `SPRINT_01_PLAN.md` 작성

**AI 생성:** AI에게 요청:
```
CLAUDE.md와 SKILL.md를 읽고.
3-5개 Phase와 테스트 목표로 SPRINT_01_PLAN.md를 생성해.
```

### 4. 사이클 실행
```
각 Phase마다:
  구현 → 테스트 → 커밋
```

### 5. 반복
Sprint가 끝나면 SKILL.md를 업데이트하고 다음 Sprint 계획을 생성합니다.

---

## 이게 전부

설치할 프레임워크도 없고, 설정할 도구도 없습니다. 그저:

1. **계획** — 무엇을 만들지 정의
2. **구현** — 작은 Phase로 나누어
3. **테스트** — 각 Phase마다
4. **커밋** — 테스트가 통과하면

---

**Last Updated:** 2026-05-26  
**Version:** 4.0
