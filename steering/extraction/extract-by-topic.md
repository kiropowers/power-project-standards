---
inclusion: manual
---

# Extract Steering by Topic

Please extract Steering rules about **[specify topic]** from our conversation.

## Common Topics Reference

If you haven't decided on a topic, choose from:

- API Design
- Database Operations
- Error Handling
- Logging
- Testing Strategy
- Security Standards
- Performance Optimization
- Code Style
- Component Development
- State Management

## Extraction Requirements

### 1. Collect Related Content

Find all topic-related items from the conversation:
- Decisions and choices
- Rules and conventions
- Examples and patterns
- Caveats and pitfalls

### 2. Organize into Rules

Organize collected content into:
- Clear rule lists
- Each rule explains "what" and "why"
- Provide correct vs incorrect examples

### 3. Determine inclusion Mode

Choose appropriate mode based on topic:

| Topic Type | Suggested Mode | fileMatchPattern Example |
|------------|----------------|-------------------------|
| General code style | always | - |
| API development | fileMatch | `src/api/**/*.py` |
| Database operations | fileMatch | `**/db/**/*.py`, `**/models/**` |
| Testing standards | fileMatch | `*_test.py`, `**/__tests__/**` |
| React components | fileMatch | `**/*.tsx`, `**/components/**` |
| Troubleshooting | manual | - |

## Output Format

```markdown
---
inclusion: [mode]
fileMatchPattern: "[if fileMatch]"
---

# [Topic] Standards

## Overview
[Brief description of purpose and scope]

## Rules

### Rule 1: [Rule Name]
**Requirement**: [Specific requirement]
**Reason**: [Why this is important]

✅ Correct example:
```[language]
[correct code]
```

❌ Incorrect example:
```[language]
[incorrect code]
```

### Rule 2: [Rule Name]
...

## FAQ

### Q: [Question]
A: [Answer]

## References
- [Related docs or links]
```

---

## Usage Example

Use in Chat like this:

```
/extract-by-topic

Topic: Error Handling
```

Or specify the topic directly:

```
/extract-by-topic

Please extract the API design standards we discussed
```
