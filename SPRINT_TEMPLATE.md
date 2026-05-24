# SPRINT_TEMPLATE.md: Sprint Planning Template

**English | [한국어](SPRINT_TEMPLATE.ko.md)**

---

> Copy this template to create `SPRINT_XX_PLAN.md` before each sprint.
> This is the only document you actually need.

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
- [ ] Plan created (this file)
- [ ] Phases defined with test targets

### Each Phase
- [ ] Implementation done
- [ ] Tests written and passing
- [ ] Committed

### Sprint Complete
- [ ] All phases done
- [ ] All tests passing
- [ ] Next sprint planned (if needed)

---

**Template Version:** 3.0  
**Last Updated:** 2026-05-24
