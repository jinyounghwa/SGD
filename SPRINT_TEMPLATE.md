# Sprint Template (Sprint Planning Template)

**English | [한국어](SPRINT_TEMPLATE.ko.md)**

---

> Copy this template before each Sprint start and create `SPRINT_XX_PLAN.md`.
> Write in detail so that AI collaborators can fully understand the context even after a session disconnection.
> **Token-saving tip**: Keep this plan concise so the AI can grasp the context with fewer tokens.

---

# Sprint [NUMBER]: [Sprint Title]

## Current Status

### Previous Sprint Completion
- Sprint [N-1]: [Goal] ([X] tests) ✅
- Sprint [N-2]: [Goal] ([Y] tests) ✅
- ...

### Cumulative Progress
- Cumulative tests so far: **XXX tests**
- This Sprint target: **YY tests**
- Expected cumulative: **XXX + YY = ZZZ tests**

### Architecture State
[One-line description of current system architecture]

Example:
```
CloudTrail → DynamoDB Streams → EventBridge → Lambda
    ↓              ↓                  ↓          ↓
 Logging      Detection        Scheduling    Execution
```

---

## Goals

### Sprint Topic
**[One-sentence description]**

Example: "Build an engine that monitors large projects in real-time and responds automatically"

### Per-Phase Goals

| Phase | Feature | Tests | Estimated Time |
|-------|---------|-------|----------------|
| 1 | [Feature Name] | NN tests | X hours |
| 2 | [Feature Name] | MM tests | Y hours |
| 3 | [Feature Name] | KK tests | Z hours |
| 4 | [Feature Name] | LL tests | W hours |
| **Total** | | **NN+MM+KK+LL** | **X+Y+Z+W** |

---

## Implementation File List

### Phase 1: [Feature Name]

| File Path | Filename | Description | New/Modified | Lines |
|-----------|----------|-------------|-------------|-------|
| `lambda/guardian/handlers/` | `rule_handler.py` | Rule processing | New | ~300 |
| `lambda/guardian/storage/` | `rule_cache.py` | Rule cache | New | ~200 |
| `tests/backend/` | `test_rules.py` | Tests | New | ~400 |
| **Total** | | | | ~900 |

### Phase 2: [Feature Name]

| File Path | Filename | Description | New/Modified |
|-----------|----------|-------------|-------------|
| ... | ... | ... | ... |

### Phase 3: [Feature Name]

...

---

## Implementation Strategy

### Phase 1: [Feature Name] (NN tests)

#### Goal
[Specific Phase goal, 3-4 lines]

#### Core Concepts
```python
class [CoreClass]:
    def [core_method](self):
        """[Method's role]"""
        # Step 1: [Description]
        # Step 2: [Description]
        # Step 3: [Description]
        return result
```

#### Test Strategy
- **Test Group 1**: [Test category] (X tests)
  - test_feature_basic
  - test_feature_with_edge_case
  - ...

- **Test Group 2**: [Test category] (Y tests)
  - test_performance
  - test_error_handling
  - ...

#### Expected Issues & Solutions
| Potential Issue | Solution |
|----------------|----------|
| [Issue] | [Solution] |
| Example: Memory shortage | Batch processing optimization |

#### Completion Criteria
- [ ] [File 1] implementation complete
- [ ] [File 2] implementation complete
- [ ] All NN tests PASS
- [ ] Git commit complete

---

### Phase 2: [Feature Name] (MM tests)

#### Goal
[...]

#### Core Concepts
[...]

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Runtime** | Python 3.12 |
| **Framework** | boto3, asyncio |
| **Data Storage** | DynamoDB |
| **Testing** | pytest |
| **Deployment** | AWS SAM |

---

## Success Criteria

### Quantitative
- [ ] All NN+MM+KK+LL = ZZZ tests PASS
- [ ] Code lines: ~XXXX lines added
- [ ] Coverage: >90%

### Qualitative
- [ ] Architecture consistency maintained
- [ ] Sufficient documentation
- [ ] Team member review passed (if applicable)

---

## Dependencies & Prerequisites

### External Dependencies
- AWS account with appropriate IAM permissions
- DynamoDB table `SecurityRulesTable`
- EventBridge rule configured

### Prerequisite Completion
- [X] [Previous Sprint] complete
- [X] [Required libraries] installed
- [X] [Required configuration] done

---

## Risk Factors & Mitigation Plan

| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|------------|
| [Risk factor] | High | Medium | [Mitigation plan] |
| Example: Dependency version conflict | High | Low | Pre-testing |

---

## Commit Message Template

Commit in the following format upon each Phase completion:

```
feat: Sprint [N] Phase [M] - [Feature Title] ([X] tests)

[One-line description]

Components:
- Feature A: [Description]
- Feature B: [Description]

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

## References

- [CLAUDE.md](CLAUDE.md) / [CLAUDE.ko.md](CLAUDE.ko.md) - Project overview
- [SKILL.md](SKILL.md) / [SKILL.ko.md](SKILL.ko.md) - Meta progress
- [README.md](README.md) / [README.ko.md](README.ko.md) - SGD methodology
- [../README.md](../README.md) - AWS Guardian README

---

## Execution Checklist

### Planning Stage (1 hour)
- [ ] Copy this template and create `SPRINT_XX_PLAN.md`
- [ ] Define per-Phase goals
- [ ] Write file list
- [ ] Establish test strategy

### Phase Implementation (2-4 hours per Phase)
- [ ] Implement core classes
- [ ] Write comprehensive tests
- [ ] Verify all tests PASS
- [ ] Perform Git commit

### Sprint Completion
- [ ] All Phases complete
- [ ] Final test verification
- [ ] Update cumulative statistics (SKILL.md)
- [ ] Review next Sprint plan

---

**Template Version:** 1.0  
**Last Updated:** 2026-05-24
