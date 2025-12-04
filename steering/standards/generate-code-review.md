---
inclusion: manual
---

# Generate Code Review Checklist Steering

Please help me generate a code review checklist file.

## Required Information

Please generate code review checklist based on the following questions (ask me if not provided):

### 1. Project Type
- What type of project?
- Main tech stack?

### 2. Review Focus
- What aspects are most important?
- Any special requirements?

### 3. Team Situation
- Team size?
- Review process?

## Output Format

```markdown
---
inclusion: manual
---

# Code Review Checklist

## Review Goals

The purpose of code review is:
1. **Quality Assurance** - Find bugs, design issues
2. **Knowledge Sharing** - Team members learn from each other
3. **Consistency** - Ensure unified code style
4. **Skill Improvement** - Continuous improvement through feedback

## Review Process

```
Submit PR → Auto checks → Assign reviewer → Code review → Modify/Discuss → Approve → Merge
```

## Review Checklist

### 1. Functional Correctness

- [ ] Does the code implement the required functionality?
- [ ] Are edge cases handled?
- [ ] Are error cases handled?
- [ ] Are there any missing scenarios?

### 2. Code Design

- [ ] Is the code structure clear?
- [ ] Does it follow single responsibility principle?
- [ ] Is there duplicate code that can be extracted?
- [ ] Is the abstraction level appropriate?

### 3. Code Readability

- [ ] Are names clear and meaningful?
- [ ] Are functions/methods too long? (recommend < 50 lines)
- [ ] Is nesting too deep? (recommend < 4 levels)
- [ ] Is complex logic explained?

### 4. Error Handling

- [ ] Are possible exceptions caught?
- [ ] Is exception handling appropriate?
- [ ] Are error messages helpful?

### 5. Security

- [ ] Any SQL injection risks?
- [ ] Any XSS risks?
- [ ] Is sensitive data handled correctly?
- [ ] Are permission checks complete?

### 6. Performance

- [ ] Any unnecessary database queries?
- [ ] Any N+1 query problems?
- [ ] Any operations in loops that can be extracted?

### 7. Testing

- [ ] Are necessary tests added?
- [ ] Do tests cover main scenarios?
- [ ] Do tests cover edge cases?

## Review Feedback Standards

| Marker | Meaning | Action |
|--------|---------|--------|
| 🔴 [Must] | Must fix | Fix before merge |
| 🟡 [Suggest] | Suggested fix | Can discuss |
| 🔵 [Question] | Have question | Need explanation |
| 🟢 [Nice] | Well done | Encouragement |

## Self-Review Checklist

Before submitting PR, self-review:

- [ ] Code runs correctly
- [ ] All tests pass
- [ ] No lint warnings
- [ ] No debug code
- [ ] Commit message follows convention
```

## Usage Example

```
/generate-code-review

We are a 5-person Python development team, need a code review checklist
```
