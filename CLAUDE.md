# CLAUDE.md: 개발자를 위한 프로젝트 시작 가이드

**한국어 | [English](CLAUDE.en.md)**

---

> **이 파일은 SGD 방법론을 적용하여 중소규모 프로젝트를 한정된 토큰 환경에서 세션 단절 없이 개발하는 방법을 설명하는 가이드입니다.**

---

## 이 프로젝트에 대해

### 프로젝트명
**AWS Guardian**: AWS 계정을 자동으로 감시하고 위협 탐지 시 자동으로 대응하는 서버리스 보안/비용 감시 시스템
https://github.com/jinyounghwa/backend_loader

### 규모
- **테스트**: ~438개 테스트 함수
- **코드**: ~41,000줄 (Lambda 8,600줄 + Frontend 8,900줄 + 테스트 9,200줄 + 인프라)
- **Sprint**: 32+ Sprint 진행 (25개 계획서, 22개 완료 보고서)
- **개발 방식**: **SGD (Sprint-Guided Development)**

### 왜 이 프로젝트를 봐야 하는가?
1. **중소규모 프로젝트를 1인 개발자가 관리** — 한정된 토큰으로도 완성 가능
2. **AI와의 협업** (Claude) — 세션 단절 없이 개발하는 실전 방법
3. **완전한 문서화** — 3개 문서만으로 프로젝트 전체를 추적
4. **검증된 방법론** — ~438개 테스트로 증명된 품질 관리

---

## 🎯 SGD의 목적

### 왜 SGD가 필요한가?

**문제 상황:**
```
AI(Claude/GPT)와 협업할 때:
  1. 토큰 제한 (200K) → 긴 세션에서 컨텍스트 압축
  2. 세션 단절 → 이전 결정사항 상실
  3. 복잡한 도구 없이 개발하고 싶음
```

**SGD의 해결:**
```
3개 문서 (CLAUDE.md, SKILL.md, SPRINT_XX_PLAN.md)만 있으면
  → 세션 끊겨도 1분 안에 복구
  → 복잡한 하네스/메모리 시스템 불필요
  → 적은 토큰으로도 프로젝트 완성 가능
```

### Agentic/Harness 방식과의 비교

| 항목 | Agentic Development | SGD |
|------|-------------------|-----|
| **도구** | Claude + Gemini CLI + Memory 시스템 | Claude 단독 + 문서 3개 |
| **메모리** | `.claude/projects/memory/` 다수 파일 | CLAUDE.md, SKILL.md |
| **리뷰** | Gemini CLI로 코드 리뷰 | 테스트로 자가 검증 |
| **복잡도** | 높음 (양방향 협업 스크립트) | 낮음 (계획→구현→테스트→커밋) |
| **토큰 소모** | 많음 (Gemini 호출 + 메모리 읽기) | 적음 (문서 3개만 읽기) |
| **세션 복구** | Memory 시스템에서 검색 | SKILL.md + git log로 1분 복구 |
| **적합 규모** | 대규모 + 장기 프로젝트 | **중소규모 + 제한된 토큰** |

> 💡 **핵심**: Agentic 방식은 강력하지만 설정이 복잡하고 토큰 소모가 많습니다.
> SGD는 **더 적은 도구로 더 빠르게** 개발하는 데 초점을 맞춥니다.

---

## 🚀 당신의 프로젝트 시작하기

### Step 1: 프로젝트 분해 (1시간)

**큰 기능을 Sprint로 나누기:**

```
당신의 아이디어
    ↓
전체 기능 목록 (5-10개)
    ↓
Sprint 분해 (3-5개 기능/Sprint)
    ↓
Phase 분해 (3-5개 단계/Sprint)
    ↓
구현 준비 완료!
```

**AWS Guardian의 예시:**
```
전체: "AWS 계정 자동 감시 시스템"
  ├─ Sprint 1-5: 기반 구축 (Lambda, DynamoDB, Telegram)
  ├─ Sprint 6-10: 기능 확장 (CloudTrail, GuardDuty, Discord)
  ├─ Sprint 11-20: 고급 기능 (멀티 리전, 자동 대응, 분석)
  └─ Sprint 21-32: 품질 & 최적화 (리팩토링, E2E 테스트, 배포)
```

### Step 2: 첫 Sprint 계획하기 (1시간)

SPRINT_TEMPLATE.md를 복사하여 **SPRINT_01_PLAN.md** 생성:

```
# Sprint 1: [당신의 첫 기능]

## 현황
- 이전 프로젝트: 없음 (신규)
- 누적: 0 tests

## 목표
- Phase 1: [기능 A] (10 tests)
- Phase 2: [기능 B] (8 tests)
- Phase 3: [기능 C] (6 tests)

## 파일 목록
| 파일 | 설명 |
|------|------|
| src/core.py | 핵심 로직 |
| tests/test_core.py | 테스트 |
```

### Step 3: 첫 Phase 구현하기 (2-3시간)

**Phase 1의 사이클:**

```
1. 핵심 클래스/함수 구현 (~30분)
   └─ 최소 기능만 (완벽할 필요 없음)

2. 포괄적 테스트 작성 (~1시간)
   └─ 정상 경로 + 엣지 케이스
   └─ 예: test_core_basic, test_core_with_edge_case

3. 모든 테스트 PASS 확인 (~10분)
   └─ pytest tests/ -v ✅

4. Git Commit (~5분)
   └─ feat: Sprint 1 Phase 1 - [기능] (10 tests)

Result: 첫 체크포인트 완성! ✅
```

---

## 📁 프로젝트 구조 (참고)

### SGD 문서 구조

```
project-root/
├── SGD/                           # 방법론 문서 (반드시 포함!)
│   ├── README.md                  # 방법론 설명
│   ├── CLAUDE.md                  # 이 파일
│   ├── SKILL.md                   # 진행률 추적
│   └── SPRINT_TEMPLATE.md         # 계획 템플릿
│
├── src/                           # 핵심 구현 (언어/프레임워크 자유)
├── tests/                         # 테스트 (매우 중요!)
├── SPRINT_01_PLAN.md              # 첫 Sprint 계획
├── SPRINT_02_PLAN.md              # 두 번째 Sprint 계획
└── README.md                      # 프로젝트 README
```

### AWS Guardian 디렉토리 구조 (실제 예시)

```
backend_loader/
├── lambda/guardian/               # Lambda 함수 (~8,600줄, 55파일)
│   ├── checkers/                  # 보안 검사 (EC2, S3, IAM, Cost...)
│   ├── responders/                # 자동 대응 (Telegram, Discord...)
│   ├── storage/                   # 데이터 저장 (DynamoDB)
│   ├── analytics/                 # 분석 (비용, 최적화)
│   └── handlers/                  # 엔트리 포인트
│
├── apps/web/                      # Next.js 대시보드 (~8,900줄, 84파일)
│   ├── src/components/Dashboard/  # UI 컴포넌트
│   └── src/app/api/               # API 라우트
│
├── tests/                         # 테스트 (~9,200줄, 42파일, ~438 tests)
│   ├── lambda/                    # Lambda 테스트 (harness, contract, performance)
│   ├── guardian/                  # 통합 테스트
│   └── cloudformation/            # 인프라 테스트
│
├── terraform/                     # IaC (~923줄)
├── docs/sprints/                  # Sprint 문서 (54개)
└── sam/                           # 배포 설정
```

---

## 🧪 테스트 중심 개발 (핵심!)

### 왜 테스트가 중요한가?

**SGD의 핵심: "모든 테스트 PASS" = 안전한 체크포인트**

```
❌ Vibe Coding (위험)
부분 구현 → 불명확한 상태 → 나중에 버그 수정

✅ SGD (안전)
Phase 1 (10 tests) → 모두 PASS → Git Commit ✅
Phase 2 (8 tests) → 모두 PASS → Git Commit ✅
Phase 3 (6 tests) → 모두 PASS → Git Commit ✅
```

### 테스트 작성 예시 (Python)

```python
# tests/test_feature.py
def test_feature_basic():
    """기본 기능 테스트"""
    result = feature.execute()
    assert result is not None
    assert len(result) > 0

def test_feature_with_invalid_input():
    """잘못된 입력 처리"""
    with pytest.raises(ValueError):
        feature.execute(invalid_param=True)

def test_feature_performance():
    """성능 테스트"""
    import time
    start = time.time()
    feature.execute()
    elapsed = time.time() - start
    assert elapsed < 1.0  # 1초 이내
```

### 테스트 실행 & 확인

```bash
# 모든 테스트 실행
pytest tests/ -v

# 특정 파일만 테스트
pytest tests/test_feature.py -v

# 결과 예시
tests/test_feature.py::test_feature_basic PASSED [33%]
tests/test_feature.py::test_feature_with_invalid_input PASSED [66%]
tests/test_feature.py::test_feature_performance PASSED [100%]

========================= 3 passed in 0.15s =========================
```

---

## 📋 필수 문서 3가지

### 1. 이 파일 (CLAUDE.md): 프로젝트 개요
- 프로젝트가 뭔지 설명
- 개발자가 시작하는 방법
- 아키텍처 개요

### 2. SKILL.md: 진행률 추적
- Sprint별 상태 (✅ 완료 / 🔄 진행 / ⏳ 예정)
- 누적 테스트 수
- 타임라인 및 마일스톤

### 3. SPRINT_XX_PLAN.md: 각 Sprint의 상세 계획
- Phase별 구현 파일
- 테스트 전략
- 예상 문제 & 해결책

**이 3가지 문서만 있으면 1인 개발자도 중소규모 프로젝트를 세션 단절 없이 관리 가능!**

---

## 💡 AWS Guardian으로 배우는 실전 사례

### 실제 진행 과정

**AWS Guardian은 32+ Sprint에 걸쳐 ~41,000줄 코드를 ~438개 테스트로 검증했습니다.**

```
Sprint 1-5: 기반 구축 (~5시간)
  └─ Lambda 핸들러 + DynamoDB + Telegram 알림

Sprint 6-15: 기능 확장 (~15시간)
  └─ EC2/S3/IAM/Cost 체커 + Discord 대시보드 + 자동 대응

Sprint 16-25: 고급 기능 (~12시간)
  └─ 멀티 리전 + 병렬 오케스트레이터 + ML 이상 탐지 + WebSocket

Sprint 26-32: 품질 & 배포 (~8시간)
  └─ 리팩토링 + E2E 테스트 + 성능 최적화 + LocalStack 배포
```

### 세션 단절 시나리오

**상황: Phase 3 중간에 Claude와의 세션이 끊김**

```
[해결 방법]

1. SKILL.md 읽기 (30초)
   "Sprint 28 Phase 1-2 완료, 380 tests 통과"

2. git log 확인 (10초)
   "마지막 commit: Sprint 28 Phase 2"

3. SPRINT_28_PLAN.md에서 Phase 3 찾기 (1분)
   "Phase 3 목표: E2E 테스트 + 성능 베이스라인 (12 tests)"

4. Phase 3 구현 재개 가능! ✅
```

> 💡 **Agentic 방식이라면?** `.claude/projects/memory/`에서 관련 메모리 파일을 검색해야 합니다.
> SGD는 **SKILL.md 1개 파일**에서 모든 컨텍스트를 파악할 수 있습니다.

---

## 🎯 당신이 따를 체크리스트

### ✅ 프로젝트 시작 전
- [ ] SGD 폴더 생성 (README.md, CLAUDE.md, SKILL.md, SPRINT_TEMPLATE.md)
- [ ] 첫 Sprint 계획 (SPRINT_01_PLAN.md)
- [ ] 기본 프로젝트 구조 생성 (src/, tests/)

### ✅ 각 Phase마다
- [ ] 핵심 클래스 구현 (30분)
- [ ] 포괄적 테스트 작성 (1시간)
- [ ] 모든 테스트 PASS 확인 (10분)
- [ ] Git commit (5분)

### ✅ 각 Sprint 완료 후
- [ ] SKILL.md에서 진행률 업데이트
- [ ] git log로 모든 commits 확인
- [ ] 다음 Sprint 계획 검토

---

## 🔧 기술 스택 선택 (자유로움!)

AWS Guardian은 다음을 사용하지만, **당신의 프로젝트에 맞게 선택하세요:**

| 레이어 | AWS Guardian | 당신의 선택 |
|--------|--------------|-----------|
| **언어** | Python 3.12 | 자유 (Java, Go, Rust...) |
| **테스트** | pytest | 자유 (unittest, JUnit...) |
| **배포** | AWS Lambda + SAM | 자유 (Docker, Kubernetes...) |
| **데이터** | DynamoDB | 자유 (PostgreSQL, MongoDB...) |

**중요:** 방법론(SGD)은 변하지 않음! 구현만 바뀝니다.

---

## 📚 다음 단계

1. **이 파일 읽기 완료** ✅
2. **README.md 읽기** - SGD 방법론 이해
3. **SKILL.md 읽기** - 진행 방식 이해
4. **SPRINT_TEMPLATE.md 복사** - 첫 Sprint 계획
5. **Phase 1 구현 시작** - 코드 작성!

---

## 🆘 문제 발생했을 때

### "Phase 1을 어떻게 시작하나요?"
→ SPRINT_TEMPLATE.md의 "구현 전략" 섹션 참고

### "테스트를 몇 개 작성해야 하나요?"
→ 규칙: 기능 1개당 1-3개 테스트
  (간단한 기능: 1개, 복잡한 기능: 3-5개)

### "AI(Claude)와 협업할 때 어떻게 하나요?"
→ README.md에서 "1인 개발자를 위한 실전 예시" 참고

### "Agentic 방식과 SGD 중 뭘 쓰나요?"
→ 중소규모 + 제한된 토큰 → **SGD** (간단, 적은 토큰)
→ 대규모 + 장기 + 다중 AI → Agentic (강력, 복잡)

---

## 📞 연락처 & 참고

- **방법론**: README.md (완전한 설명)
- **진행률**: SKILL.md (현재 상태)
- **계획**: SPRINT_XX_PLAN.md (각 Sprint)
- **원본 프로젝트**: AWS Guardian https://github.com/jinyounghwa/backend_loader

---

**SGD: 적은 토큰으로, 세션 단절 없이, 중소규모 프로젝트를 완성하세요.** 💪

---

**Last Updated:** 2026-05-24  
**Version:** 2.0 - 개발자 시작 가이드
