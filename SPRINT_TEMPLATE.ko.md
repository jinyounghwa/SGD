# SPRINT_TEMPLATE.md: Sprint 계획 템플릿

**[English](SPRINT_TEMPLATE.md) | 한국어**

---

> 각 Sprint 시작 전 이 템플릿을 복사하여 `SPRINT_XX_PLAN.md`로 생성합니다.
> 전제조건: [CLAUDE.md](CLAUDE.md) (프로젝트 개요)와 [SKILL.md](SKILL.md) (현재 진행)가 먼저 있어야 합니다.
>
> **AI 생성:** Claude에게 Sprint 계획 생성을 요청할 수 있습니다:
> ```
> CLAUDE.md와 SKILL.md를 읽고, git log를 확인한 후
> SPRINT_TEMPLATE.md 형식으로 SPRINT_XX_PLAN.md를 생성해.
> ```

---

# Sprint [NUMBER]: [제목]

## 현황

### 이전 Sprint
- Sprint [N-1]: [목표] ([X] tests) ✅

### 누적
- 현재까지 테스트: **XXX**
- 이번 Sprint 목표: **YY**
- 예상 총계: **XXX + YY = ZZZ**

---

## Phases

| Phase | 기능 | 테스트 | 시간 |
|-------|------|--------|------|
| 1 | [기능] | NN | Xh |
| 2 | [기능] | MM | Yh |
| 3 | [기능] | KK | Zh |
| **합계** | | **NN+MM+KK** | **X+Y+Zh** |

---

## 구현 파일

### Phase 1: [기능]

| 경로 | 파일 | 설명 | 신규/수정 |
|------|------|------|----------|
| `src/` | `feature.py` | 핵심 로직 | 신규 |
| `tests/` | `test_feature.py` | 테스트 | 신규 |

### Phase 2: [기능]
...

### Phase 3: [기능]
...

---

## 구현 전략

### Phase 1: [기능] (NN tests)

#### 목표
[이 Phase가 달성하는 것]

#### 핵심 개념
```python
class CoreClass:
    def core_method(self):
        # Step 1: ...
        # Step 2: ...
        return result
```

#### 테스트 계획
- 테스트 그룹 1: [카테고리] (X tests)
- 테스트 그룹 2: [카테고리] (Y tests)

#### 리스크
| 문제 | 대응 |
|------|------|
| [리스크] | [해결책] |

#### 완료 조건
- [ ] 구현 완료
- [ ] NN개 테스트 PASS
- [ ] 커밋 완료

---

### Phase 2: [기능] (MM tests)
...

---

## 커밋 메시지 템플릿

```
feat: Sprint [N] Phase [M] - [제목] ([X] tests)

[설명]

누적: [이전] + [이번] = [총계] tests
```

---

## 체크리스트

### 시작 전
- [ ] [CLAUDE.md](CLAUDE.md)에 프로젝트 개요가 있음
- [ ] [SKILL.md](SKILL.md)에 현재 진행 상태가 최신임
- [ ] Phase별 테스트 목표 설정

### 각 Phase
- [ ] 구현 완료
- [ ] 테스트 작성 및 통과
- [ ] 커밋

### Sprint 완료
- [ ] 모든 Phase 완료
- [ ] 모든 테스트 통과
- [ ] [SKILL.md](SKILL.md)에 결과 업데이트
- [ ] **`SPRINT_XX_COMPLETION.md` 작성** (테스트 결과, 아키텍처, 메트릭)
- [ ] 다음 Sprint 계획 (필요시)

---

## 완료 보고서 템플릿

> 모든 Phase가 완료된 후 이 템플릿으로 `SPRINT_XX_COMPLETION.md`를 작성합니다.
> 이 문서는 향후 Sprint 계획을 위한 AI 메모리 역할을 합니다.

```markdown
# Sprint [NUMBER] 완료 보고서

## 요약
- **Sprint**: [NUMBER] - [제목]
- **상태**: ✅ 완료
- **기간**: [시작일] ~ [종료일]

## 테스트 결과
| Phase | 기능 | 계획 | 실제 | 상태 |
|-------|------|------|------|------|
| 1 | [기능] | NN | NN | ✅ |
| 2 | [기능] | MM | MM | ✅ |
| **합계** | | **NN+MM** | **NN+MM** | ✅ |

## 아키텍처 결정
| 결정 | 이유 | 고려한 대안 |
|------|------|-------------|
| [결정] | [이유] | [고려한 다른 옵션] |

## 메트릭
- **추가된 테스트**: [N]
- **누적 테스트**: [총계]
- **생성된 파일**: [N]
- **수정된 파일**: [N]
- **추가된 줄 수**: ~[N]

## 이슈 & 교훈
- [발생한 이슈와 해결 방법]

## 변경된 파일
### 생성
- `path/to/new_file.py`

### 수정
- `path/to/existing_file.py`
```

---

## 참고

- [CLAUDE.md](CLAUDE.md) — 프로젝트 개요 (무엇을 만드는지)
- [SKILL.md](SKILL.md) — 진행 추적기 (현재 어디인지)
- [README.md](README.md) — SGD 방법론

---

**템플릿 버전:** 4.0  
**최종 업데이트:** 2026-05-26
