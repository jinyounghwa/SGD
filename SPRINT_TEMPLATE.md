# SPRINT_TEMPLATE.md: Sprint Planning Template

**English | [한국어](SPRINT_TEMPLATE.ko.md)**

---

> Copy this template to create `SPRINT_XX_PLAN.md` before each sprint.
> Prerequisites: [CLAUDE.md](CLAUDE.md) (project overview) and [SKILL.md](SKILL.md) (current progress) must exist first.
>
> **AI generation:** You can ask Claude to generate the sprint plan:
> ```
> Read CLAUDE.md and SKILL.md, check git log, then
> generate SPRINT_XX_PLAN.md using SPRINT_TEMPLATE.md format.
> ```

---

# Sprint [NUMBER]: [Title]

## Status

### Previous Sprint
- Sprint [N-1]: [goal] ([X] tests) ✅

### Cumulative
- Tests so far: **XXX**
- This sprint target: **YY**
- Expected total: **XXX + YY = ZZZ**

---

## Phases

| Phase | Feature | Tests | Time |
|-------|---------|-------|------|
| 1 | [Feature] | NN | Xh |
| 2 | [Feature] | MM | Yh |
| 3 | [Feature] | KK | Zh |
| **Total** | | **NN+MM+KK** | **X+Y+Zh** |

---

## Implementation Files

### Phase 1: [Feature]

| Path | File | Description | New/Modified |
|------|------|-------------|-------------|
| `src/` | `feature.py` | Core logic | New |
| `tests/` | `test_feature.py` | Tests | New |

### Phase 2: [Feature]
...

### Phase 3: [Feature]
...

---

## Strategy

### Phase 1: [Feature] (NN tests)

#### Goal
[What this phase accomplishes]

#### Core Concept
```python
class CoreClass:
    def core_method(self):
        # Step 1: ...
        # Step 2: ...
        return result
```

#### Test Plan
- Test Group 1: [category] (X tests)
- Test Group 2: [category] (Y tests)

#### Risks
| Issue | Mitigation |
|-------|-----------|
| [Risk] | [Solution] |

#### Done When
- [ ] Implementation complete
- [ ] NN tests PASS
- [ ] Committed

---

### Phase 2: [Feature] (MM tests)
...

---

## Commit Message Template

```
feat: Sprint [N] Phase [M] - [Title] ([X] tests)

[Description]

Cumulative: [prev] + [new] = [total] tests
```

---

## Checklist

### Before Starting
- [ ] [CLAUDE.md](CLAUDE.md) exists with project overview
- [ ] [SKILL.md](SKILL.md) is up to date with current progress
- [ ] Phases defined with test targets

### Each Phase
- [ ] Implementation done
- [ ] Tests written and passing
- [ ] Committed

### Sprint Complete
- [ ] All phases done
- [ ] All tests passing
- [ ] [SKILL.md](SKILL.md) updated with results
- [ ] **`SPRINT_XX_COMPLETION.md` written** (test results, architecture, metrics)
- [ ] Next sprint planned (if needed)

---

## Completion Report Template

> After all phases are complete, create `SPRINT_XX_COMPLETION.md` using this template.
> This serves as AI memory for future sprint planning.

```markdown
# Sprint [NUMBER] Completion Report

## Summary
- **Sprint**: [NUMBER] - [Title]
- **Status**: ✅ Complete
- **Duration**: [start date] ~ [end date]

## Test Results
| Phase | Feature | Planned | Actual | Status |
|-------|---------|---------|--------|--------|
| 1 | [Feature] | NN | NN | ✅ |
| 2 | [Feature] | MM | MM | ✅ |
| **Total** | | **NN+MM** | **NN+MM** | ✅ |

## Architecture Decisions
| Decision | Reason | Alternative Considered |
|----------|--------|----------------------|
| [Decision] | [Why] | [What else was considered] |

## Metrics
- **Tests added**: [N]
- **Cumulative tests**: [total]
- **Files created**: [N]
- **Files modified**: [N]
- **Lines added**: ~[N]

## Issues & Lessons Learned
- [Issue encountered and how it was resolved]

## Files Changed
### Created
- `path/to/new_file.py`

### Modified
- `path/to/existing_file.py`
```

---

## Reference

- [CLAUDE.md](CLAUDE.md) — Project overview (what we're building)
- [SKILL.md](SKILL.md) — Progress tracker (where we are)
- [README.md](README.md) — SGD methodology

---

**Template Version:** 4.0  
**Last Updated:** 2026-05-26
