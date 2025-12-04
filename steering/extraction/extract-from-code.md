---
inclusion: manual
---

# Extract Steering from Code Analysis

Please analyze the specified code files/directories and extract implicit coding standards as Steering.

> **Important**: Detect the programming language of the analyzed code and generate the steering file with examples in that same language. The analysis dimensions apply to all languages, but examples should match the codebase being analyzed.

## Usage

After using this command, specify the file or directory to analyze:

```
/extract-from-code

Please analyze #src/services/ directory
```

or

```
/extract-from-code

Please analyze #src/api/user.py file
```

## Analysis Dimensions

### 1. Naming Patterns
- Variable naming style (camelCase/snake_case/PascalCase)
- Function naming conventions (verb prefix?)
- Class naming rules
- File naming rules
- Constant naming rules

### 2. Code Organization
- File structure (import order, code block order)
- Module organization
- Class/function organization
- Public/private member distinction

### 3. Error Handling
- Exception types used
- Error message format
- Error propagation approach
- Retry mechanisms

### 4. Logging
- Log level usage
- Log message format
- When to log
- Sensitive data handling

### 5. Comment Style
- Docstring format
- Inline comment style
- TODO/FIXME markers
- Type annotations

### 6. Testing Patterns (if test files exist)
- Test naming conventions
- Test organization
- Mock/Stub usage
- Assertion style

## Output Requirements

### 1. Analysis Report

First output the analysis findings:

```
## Analysis Findings

### Naming Patterns
- Variables: snake_case
- Functions: snake_case, verb prefix
- Classes: PascalCase
- Files: snake_case

### Code Organization
- Import order: stdlib → third-party → local
- Class structure: __init__ → public methods → private methods

### Error Handling
- Uses custom exception classes
- Error messages include context

...
```

### 2. Generate Steering File

Based on analysis, generate Steering file:

```markdown
---
inclusion: fileMatch
fileMatchPattern: "[based on analyzed file types]"
---

# [Project] Code Standards

## Naming Conventions

### Variable Naming
- Use snake_case
- Boolean variables use is_/has_/can_ prefix

Example:
```python
# ✅ Correct
user_name = "John"
is_active = True
has_permission = False

# ❌ Incorrect
userName = "John"
active = True
```

### Function Naming
...

## Code Organization
...
```

## Notes

1. **Identify Patterns vs Coincidence**
   - Only extract consistently appearing patterns
   - Ignore potentially accidental one-time usage

2. **Distinguish Good vs Bad Practices**
   - Point out inconsistencies if found
   - Suggest unified direction

3. **Consider Context**
   - Some patterns may be framework requirements
   - Some patterns may be legacy code

4. **Keep it Practical**
   - Only extract valuable standards
   - Avoid overly trivial rules
