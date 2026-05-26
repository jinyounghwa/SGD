# CLAUDE.md: Project Overview (Required)

**English | [한국어](CLAUDE.ko.md)**

---

> **This file is required.** It describes the project you're building.
> Without it, you can't plan sprints because you don't know what you're building.

---

## Project: [Name]

> One-line description

### Scale
- **Tests**: [N] test functions
- **Code**: ~[N] lines
- **Sprints**: [N] completed

### Tech Stack
| Layer | Technology |
|-------|-----------|
| Language | ... |
| Testing | ... |
| Deployment | ... |

### Directory Structure
```
project/
├── src/
├── tests/
├── docs/sprints/
└── ...
```

### Core Architecture
[Describe the main components and how they connect]

### Key Decisions
- [Design decision 1 and why]
- [Design decision 2 and why]

---

## Reference

- **Methodology**: See [README.md](README.md)
- **Sprint Template**: See [SPRINT_TEMPLATE.md](SPRINT_TEMPLATE.md)
- **Progress**: See [SKILL.md](SKILL.md)

## Sprint Workflow (Claude Code Memory)

```
1. SPRINT_XX_PLAN.md 작성 (구현 전 상세 설계)
2. 구현 (서비스, 핸들러, 테스트 작성)
3. SPRINT_XX_COMPLETION.md 작성 (테스트 결과, 아키텍처, 메트릭)
```

- Each sprint follows this three-step cycle
- `SPRINT_XX_PLAN.md` is written before implementation
- `SPRINT_XX_COMPLETION.md` is written after implementation
- Completion reports serve as AI memory for the next sprint plan

---

**Last Updated:** 2026-05-26
