---
inclusion: manual
---

# Extract Steering from Conversation

Please review our conversation and extract content that can be used as Steering rules.

## Extraction Criteria

Please identify the following types of information:

1. **Technical Decisions**
   - What technology/library/framework was chosen
   - Why this choice was made
   - What alternatives were rejected

2. **Code Conventions**
   - Naming conventions (variables, functions, classes, files)
   - Code organization patterns
   - Import/dependency management rules

3. **Architecture Principles**
   - Layering rules
   - Module boundaries
   - Data flow patterns

4. **Best Practices**
   - Error handling patterns
   - Logging approaches
   - Performance optimization tips

5. **Business Rules**
   - Data validation rules
   - Business logic constraints
   - Security requirements

## Output Requirements

For each extracted item, please provide:

### 1. File Information
- **Suggested filename**: e.g., `api-conventions.md`
- **inclusion mode**:
  - `always` - General conventions needed in every conversation
  - `fileMatch` - Conventions for specific file types, with `fileMatchPattern`
  - `manual` - Occasionally needed guidelines

### 2. Complete File Content

```markdown
---
inclusion: [mode]
fileMatchPattern: "[pattern, if fileMatch]"
---

# [Title]

## [Section]
[Content]

## Examples
[Code examples]
```

## Exclusions

Please do not include:
- Temporary discussion content
- Implementation details for specific tasks
- Sensitive information (passwords, keys, tokens)
- Personal preferences (not team consensus)

## Output Format

If multiple Steering files are extracted, output them separately:

---

### Steering 1: [filename]

**Purpose**: [Brief description]
**inclusion**: [mode]

```markdown
[Complete file content]
```

---

### Steering 2: [filename]

...
