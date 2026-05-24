# SGD: Sprint-Guided Development Methodology

**[English](README.md) | 한국어**

---

## 탄생 배경

### 문제: Vibe Coding + AI 세션 단절 + 토큰 제한

중소규모 프로젝트를 AI(Claude)와 협업할 때 발생하는 문제들:

**1. 세션 단절 문제**
- Claude의 컨텍스트 윈도우는 약 200K 토큰 (충분하지만 제한적)
- 장시간 개발 후 컨텍스트가 압축되면 이전 결정사항을 잃음
- 같은 실수를 반복하거나 아키텍처 일관성이 깨짐

**2. Vibe Coding의 한계**
- 기분 따라 개발하면 구조가 흩어짐
- 테스트 없이 진행하면 나중에 대규모 버그 수정 필요
- 어떤 기능이 완성되었는지 불명확함

**3. 기존 방식의 복잡도**
- Agentic Development (Claude + Gemini + Memory)는 강력하지만 설정이 복잡
- Harness 기반 테스트는 SAM/Docker 등 인프라가 필요
- 중소규모 프로젝트에는 과한 설정

---

## SGD의 해결책

### Core Idea: 문서 3개로 세션 단절 극복

```
CLAUDE.md      → 프로젝트 전체 개요 (읽기 1분)
SKILL.md       → 현재 진행 상태 (읽기 30초)
SPRINT_XX_PLAN → 이번 Sprint 계획 (읽기 30초)
```

**핵심:**
- 세션이 끊겨도 **문서 3개만 읽으면 2분 안에 복구**
- Agentic 방식의 Memory 시스템 없이도 컨텍스트 유지
- 복잡한 도구 설정 없이 Claude 단독으로 개발 가능

### Sprint Gate: 안전한 체크포인트

각 Phase 완료 시 **"모든 테스트 PASS"** = 복구 가능한 상태

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

## Agentic / Harness 방식과의 비교

| 항목 | Agentic Development | SGD (이 방법론) |
|------|-------------------|----------------|
| **도구** | Claude + Gemini CLI + Memory | Claude 단독 + 문서 3개 |
| **메모리** | `.claude/projects/memory/` | CLAUDE.md, SKILL.md |
| **리뷰** | Gemini CLI로 외부 리뷰 | 테스트로 자가 검증 |
| **하네스** | SAM Local + Docker 필요 | 일반 pytest만으로 충분 |
| **복잡도** | 높음 (양방향 스크립트, 메모리 관리) | 낮음 (계획→구현→테스트→커밋) |
| **토큰 소모** | 많음 (Gemini + 메모리 읽기) | 적음 (문서 3개만) |
| **세션 복구** | Memory 시스템 검색 | SKILL.md + git log로 1분 |
| **학습 곡선** | 중간~높음 | 낮음 |
| **적합 규모** | 대규모 + 장기 프로젝트 | **중소규모 + 제한된 토큰** |

> 💡 **확인 결과**: Agentic 방식은 `agentic-loop.sh`, Gemini CLI 연동, `.claude/projects/memory/` 관리가 필요합니다.
> SGD는 **문서 3개와 테스트만으로 동일한 목표(세션 단절 방지)를 더 쉽게 달성**합니다.

---

## 개요

**SGD (Sprint-Guided Development)**는 중소규모 소프트웨어 프로젝트를 한정된 토큰 환경에서 세션 단절 없이 개발하기 위한 방법론입니다.

- **목적**: 적은 토큰으로, 복잡한 도구 없이, AI와 협업하여 프로젝트 완성
- **도구**: Claude 단독 + 문서 3개 (CLAUDE.md, SKILL.md, SPRINT_XX_PLAN.md)
- **검증**: AWS Guardian 프로젝트에서 실증 (~438 tests, ~41,000줄, 32+ Sprint)

---

## 핵심 원칙

### 1️⃣ **Phase 기반 분해**
- 각 Sprint를 3-5개의 작은 Phase로 나눔
- 각 Phase = 구체적인 기능 + 테스트 + 커밋
- Phase별 독립적 실행 가능 (의존성 최소화)

### 2️⃣ **명확한 테스트 목표**
- 각 Phase마다 구체적인 테스트 수 설정
- 모든 테스트가 PASS할 때까지 Phase 완료 안 함
- 테스트 = 신뢰도 증명서

### 3️⃣ **최소 문서로 컨텍스트 유지**
- CLAUDE.md: 프로젝트 전체 개요
- SKILL.md: 현재 진행 상태 (Sprint별)
- SPRINT_XX_PLAN.md: 이번 Sprint 상세 계획
- 이 3개만 있으면 세션 복구에 충분

### 4️⃣ **토큰 효율성**
- Agentic 방식 대비 토큰 소모 최소화
- 문서는 간결하게 유지
- AI에게 필요한 컨텍스트만 전달

### 5️⃣ **Git 기반 체크포인트**
- 각 Phase 완료 시 커밋
- 커밋 메시지에 테스트 수 + 진행 정보 포함
- git log만으로 진행 이력 파악 가능

---

## Sprint 구조

```
Sprint N (전체 목표)
├── Phase 1 (기능 A, Y 테스트)
│   ├── 구현
│   ├── 테스트 (Y개)
│   └── 커밋
├── Phase 2 (기능 B, Y 테스트)
│   ├── 구현
│   ├── 테스트 (Y개)
│   └── 커밋
├── Phase 3 (기능 C, Y 테스트)
└── ...
└── SKILL.md 업데이트
```

---

## 개발 사이클

### 1. Sprint 계획 (30분~1시간)

```markdown
# Sprint N: 스프린트 제목

## 현황
- 이전 Sprint 완료: X 테스트
- 누적: Y 테스트

## 목표
- Phase 1: [기능], Z 테스트
- Phase 2: [기능], Z 테스트

## 파일 목록
- `path/file1.py` - [설명]
- `path/file2.py` - [설명]
```

### 2. Phase 구현 (2-4시간)

```
1. 핵심 클래스/함수 구현
2. 포괄적 테스트 작성
3. 모든 테스트 PASS 확인
4. Phase 커밋
   └── git commit -m "feat: Sprint N Phase M - [설명] (Z tests)"
```

### 3. 세션 복구 (끊겼을 때, 2분)

```
1. SKILL.md 읽기 → 현재 위치 파악 (30초)
2. git log --oneline → 완료된 Phase 확인 (10초)
3. SPRINT_XX_PLAN.md → 다음 Phase 확인 (1분)
4. 구현 재개 ✅
```

---

## 1인 개발자를 위한 실전 예시

### Case Study: AWS Guardian

**상황:**
- 프로젝트: AWS 계정 자동 감시 시스템 (중소규모)
- 개발자: 1명
- 규모: ~41,000줄, ~438 테스트, 32+ Sprint
- AI 협업: Claude 단독 (세션 단절 빈번)

### 실제 진행 패턴

```
Sprint 1-5: 기반 구축
  ├─ Phase 1: Lambda 핸들러 + 테스트 (8 tests)
  ├─ Phase 2: DynamoDB 연동 + 테스트 (6 tests)
  ├─ Phase 3: Telegram 알림 + 테스트 (5 tests)
  └─ 누적: ~19 tests

Sprint 6-15: 기능 확장
  ├─ EC2/S3/IAM/Cost 체커 (각 5-10 tests)
  ├─ Discord 대시보드 (8 tests)
  ├─ 자동 대응 로직 (12 tests)
  └─ 누적: ~150 tests

Sprint 16-32: 품질 & 최적화
  ├─ 리팩토링 + 타입 힌트 (15 tests)
  ├─ E2E 통합 테스트 (20 tests)
  ├─ 성능 베이스라인 (10 tests)
  └─ 누적: ~438 tests
```

### 세션 단절 시나리오

**상황:** Phase 3 중간에 Claude 세션이 끊김

```
[Agentic 방식이라면]
1. .claude/projects/memory/ 에서 관련 파일 검색
2. MEMORY.md 인덱스 확인
3. 여러 feedback/project 파일 읽기
→ 복구에 5-10분 + 많은 토큰 소모

[SGD 방식]
1. SKILL.md 읽기 (30초)
   "Sprint 20 Phase 1-2 완료, 250 tests 통과"
2. git log --oneline (10초)
   "마지막 commit: Sprint 20 Phase 2"
3. SPRINT_20_PLAN.md에서 Phase 3 찾기 (1분)
4. Phase 3 구현 재개! ✅
→ 복구에 2분 + 최소 토큰
```

### AI 협업 팁 (토큰 절약)

**Good Practice (토큰 효율):**
```markdown
현황:
- 완료: Sprint 15 Phase 1-2 (14 tests)
- 진행: Sprint 15 Phase 3
- 계획: SPRINT_15_PLAN.md 참고

다음 할 일:
- Phase 3 나머지 구현
- 모든 테스트 PASS 확인
```

**Bad Practice (토큰 낭비):**
```
지금까지의 전체 코드를 보여주기
모든 파일의 이력을 설명하기
Gemini CLI로 외부 리뷰 요청하기
```

---

## 장점

✅ **간단함**
- 문서 3개 + 테스트만으로 프로젝트 관리
- 복잡한 도구 설정 불필요

✅ **토큰 효율**
- Agentic 대비 토큰 소모 최소화
- 세션 복구에 2분 + 최소 토큰

✅ **진행도 명확**
- 누적 테스트 수로 객관적 측정
- git log로 히스토리 추적

✅ **세션 안전**
- Phase별 Git 커밋 = 복구 지점
- SKILL.md 1개 파일로 전체 상태 파악

---

## 체크리스트

### Sprint 시작 전
- [ ] SPRINT_XX_PLAN.md 작성
- [ ] Phase별 구현 파일 명시
- [ ] 테스트 수 목표 설정

### Phase 완료 후
- [ ] 모든 테스트 PASS 확인
- [ ] 커밋 메시지 작성 (테스트 수 포함)
- [ ] SKILL.md 업데이트

### Sprint 완료 후
- [ ] 전체 테스트 PASS 확인
- [ ] 누적 통계 정리
- [ ] 다음 Sprint 계획 검토

---

## 다른 프로젝트에 적용하기

### 1단계: 프로젝트 분석
```
큰 기능 → Sprint 분해 → Phase 분해 → 구현
(예: 인증 시스템 → Sprint N → Phase 1-3 → OAuth, JWT, 2FA)
```

### 2단계: SGD 문서 생성
- CLAUDE.md (프로젝트 개요)
- SKILL.md (진행률 추적)
- SPRINT_TEMPLATE.md 복사 → SPRINT_01_PLAN.md

### 3단계: 첫 Sprint 실행
- Phase 1 구현 & 테스트
- 모든 테스트 PASS → Git 커밋
- 학습 & 조정

### 4단계: 지속적 개선
- 각 Sprint 후 회고
- 토큰 사용량 모니터링
- 프로세스 조정

---

## 참고 자료

- `CLAUDE.md` / `CLAUDE.ko.md` - 개발자 프로젝트 시작 가이드
- `SPRINT_TEMPLATE.md` - Sprint 계획 템플릿
- `SKILL.md` - 진행률 추적 가이드
- **원본 프로젝트**: AWS Guardian https://github.com/jinyounghwa/backend_loader

---

> 📖 **한국어 버전**: [README.ko.md](README.ko.md)

---

**Last Updated:** 2026-05-24  
**Version:** 2.0  
**Status:** Production-ready
