# Sprint Template (스프린트 계획 템플릿)

**한국어 | [English](SPRINT_TEMPLATE.en.md)**

---

> 각 Sprint 시작 전 이 템플릿을 복사하여 `SPRINT_XX_PLAN.md`로 생성합니다.
> AI 협업자가 세션 단절 후에도 컨텍스트를 완전히 이해할 수 있도록 상세히 작성합니다.
> **토큰 절약 팁**: 이 계획서를 간결하게 유지하면 AI가 더 적은 토큰으로 컨텍스트를 파악할 수 있습니다.

---

# Sprint [NUMBER]: [스프린트 제목]

## 현황

### 이전 스프린트 완료
- Sprint [N-1]: [목표] ([X] tests) ✅
- Sprint [N-2]: [목표] ([Y] tests) ✅
- ...

### 누적 진행
- 이전까지의 누적 테스트: **XXX tests**
- 이번 스프린트 목표: **YY tests**
- 예상 누적: **XXX + YY = ZZZ tests**

### 아키텍처 상태
[현재 시스템 아키텍처 한 줄 설명]

예:
```
CloudTrail → DynamoDB Streams → EventBridge → Lambda
    ↓              ↓                  ↓          ↓
 Logging      Detection        Scheduling    Execution
```

---

## 목표 (Goals)

### Sprint 주제
**[한 문장 설명]**

예: "대규모 프로젝트를 실시간으로 감시하고 자동으로 대응하는 엔진 구축"

### Phase별 목표

| Phase | 기능 | 테스트 | 예상 시간 |
|-------|------|--------|---------|
| 1 | [기능명] | NN tests | X시간 |
| 2 | [기능명] | MM tests | Y시간 |
| 3 | [기능명] | KK tests | Z시간 |
| 4 | [기능명] | LL tests | W시간 |
| **합계** | | **NN+MM+KK+LL** | **X+Y+Z+W** |

---

## 구현 파일 목록

### Phase 1: [기능명]

| 파일 경로 | 파일명 | 설명 | 신규/수정 | 라인 수 |
|---------|--------|------|---------|--------|
| `lambda/guardian/handlers/` | `rule_handler.py` | 규칙 처리 | 신규 | ~300 |
| `lambda/guardian/storage/` | `rule_cache.py` | 규칙 캐시 | 신규 | ~200 |
| `tests/backend/` | `test_rules.py` | 테스트 | 신규 | ~400 |
| **합계** | | | | ~900 |

### Phase 2: [기능명]

| 파일 경로 | 파일명 | 설명 | 신규/수정 |
|---------|--------|------|---------|
| ... | ... | ... | ... |

### Phase 3: [기능명]

...

---

## 구현 전략

### Phase 1: [기능명] (NN tests)

#### 목표
[Phase의 구체적 목표 3-4줄]

#### 핵심 개념
```python
class [CoreClass]:
    def [core_method](self):
        """[메서드의 역할]"""
        # Step 1: [설명]
        # Step 2: [설명]
        # Step 3: [설명]
        return result
```

#### 테스트 전략
- **Test Group 1**: [테스트 카테고리] (X tests)
  - test_feature_basic
  - test_feature_with_edge_case
  - ...

- **Test Group 2**: [테스트 카테고리] (Y tests)
  - test_performance
  - test_error_handling
  - ...

#### 예상 이슈 & 해결책
| 잠재적 문제 | 해결책 |
|-----------|--------|
| [문제] | [해결책] |
| 예: 메모리 부족 | 배치 처리 최적화 |

#### 완료 조건
- [ ] [파일1] 구현 완료
- [ ] [파일2] 구현 완료
- [ ] 모든 NN개 테스트 PASS
- [ ] Git commit 완료

---

### Phase 2: [기능명] (MM tests)

#### 목표
[...]

#### 핵심 개념
[...]

---

## 기술 스택

| 레이어 | 기술 |
|--------|------|
| **런타임** | Python 3.12 |
| **프레임워크** | boto3, asyncio |
| **데이터 저장** | DynamoDB |
| **테스트** | pytest |
| **배포** | AWS SAM |

---

## 성공 지표

### 정량적
- [ ] 모든 NN+MM+KK+LL = ZZZ 개 테스트 PASS
- [ ] 코드 라인: ~XXXX 줄 추가
- [ ] 커버리지: >90%

### 정성적
- [ ] 아키텍처 일관성 유지
- [ ] 문서화 충분
- [ ] 팀원 리뷰 통과 (있으면)

---

## 의존성 & 선행 조건

### 외부 의존성
- AWS 계정 (적절한 IAM 권한 필요)
- DynamoDB 테이블 `SecurityRulesTable`
- EventBridge 규칙 구성

### 선행 완료 조건
- [X] [이전 Sprint] 완료
- [X] [필수 라이브러리] 설치
- [X] [필수 설정] 완료

---

## 위험 요소 & 완화 계획

| 위험 | 영향도 | 가능성 | 완화책 |
|-----|--------|--------|--------|
| [위험 요소] | 높음 | 중간 | [완화 계획] |
| 예: 의존성 버전 충돌 | 높음 | 낮음 | 사전 테스트 |

---

## 커밋 메시지 템플릿

각 Phase 완료 시 다음 형식으로 commit:

```
feat: Sprint [N] Phase [M] - [기능 제목] ([X] tests)

[한 줄 설명]

Components:
- Feature A: [설명]
- Feature B: [설명]

Test Coverage:
- Test Group 1: X tests
- Test Group 2: Y tests

Performance Metrics:
- Metric 1: value
- Metric 2: value

Cumulative: [prev] + [new] = [total] tests

Co-Authored-By: [Your Name] <noreply@[domain]>
```

---

## 참고 자료

- [CLAUDE.md](CLAUDE.md) / [CLAUDE.en.md](CLAUDE.en.md) - 프로젝트 개요
- [SKILL.md](SKILL.md) / [SKILL.en.md](SKILL.en.md) - 메타 진행률
- [README.md](README.md) / [README.en.md](README.en.md) - SGD 방법론
- [../README.md](../README.md) - AWS Guardian README

---

## 실행 체크리스트

### 계획 단계 (1시간)
- [ ] 이 템플릿 복사하여 `SPRINT_XX_PLAN.md` 생성
- [ ] Phase별 목표 정의
- [ ] 파일 목록 작성
- [ ] 테스트 전략 수립

### Phase 구현 (각 Phase당 2-4시간)
- [ ] 핵심 클래스 구현
- [ ] 포괄적 테스트 작성
- [ ] 모든 테스트 PASS 확인
- [ ] Git commit 수행

### Sprint 완료
- [ ] 모든 Phase 완료
- [ ] 최종 테스트 검증
- [ ] 누적 통계 업데이트 (SKILL.md)
- [ ] 다음 Sprint 계획 검토

---

**Template Version:** 1.0  
**Last Updated:** 2026-05-24
