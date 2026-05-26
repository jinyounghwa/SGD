# CLAUDE.md: 프로젝트 개요 (필수)

**[English](CLAUDE.md) | 한국어**

---

> **이 파일은 필수입니다.** 만들 프로젝트를 설명하는 문서입니다.
> 이게 없으면 무엇을 만들지 모르니 Sprint를 계획할 수 없습니다.

---

## 프로젝트: [이름]

> 한 줄 설명

### 규모
- **테스트**: [N]개 테스트 함수
- **코드**: ~[N]줄
- **Sprint**: [N]개 완료

### 기술 스택
| 레이어 | 기술 |
|--------|------|
| 언어 | ... |
| 테스트 | ... |
| 배포 | ... |

### 디렉토리 구조
```
project/
├── src/
├── tests/
├── docs/sprints/
└── ...
```

### 핵심 아키텍처
[주요 컴포넌트와 연결 방법을 설명]

### 주요 설계 결정
- [설계 결정 1과 이유]
- [설계 결정 2과 이유]

---

## 참고

- **방법론**: [README.md](README.md) 참고
- **Sprint 템플릿**: [SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md) 참고
- **진행률**: [SKILL.md](SKILL.md) 참고

## Sprint 워크플로우 (Claude Code Memory)

```
1. SPRINT_XX_PLAN.md 작성 (구현 전 상세 설계)
2. 구현 (서비스, 핸들러, 테스트 작성)
3. SPRINT_XX_COMPLETION.md 작성 (테스트 결과, 아키텍처, 메트릭)
```

- 각 Sprint는 이 3단계 사이클을 따릅니다
- `SPRINT_XX_PLAN.md`는 구현 전에 작성합니다
- `SPRINT_XX_COMPLETION.md`는 구현 완료 후 작성합니다
- 완료 보고서는 다음 Sprint 계획을 위한 AI 메모리 역할을 합니다

---

**Last Updated:** 2026-05-26
