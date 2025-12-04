---
inclusion: manual
---

# Generate Error Handling Standards Steering

Please help me generate an error handling standards file.

> **Important**: Detect the user's project language and generate examples accordingly. Python uses exceptions, Go uses error returns, TypeScript/JavaScript uses try-catch or Result types, etc. Adapt the patterns to the language's idioms.

## Required Information

Please generate error handling standards based on the following questions (ask me if not provided):

### 1. Exception Hierarchy
- What exception base class?
- Custom exception categories?

### 2. Error Code Design
- Error code format?
- Error code categories?

### 3. Error Propagation
- How do exceptions propagate between layers?
- When to catch, when to throw?

### 4. Error Response
- Error message format?
- For users vs for developers?

## Output Format

```markdown
---
inclusion: always
---

# Error Handling Standards

## Design Principles

1. **Fail Fast** - Detect errors early, report early
2. **Clear Errors** - Error messages should be clear and actionable
3. **Layered Handling** - Each layer only handles errors it can handle
4. **Unified Format** - Consistent error response format

## Exception Hierarchy

### Base Exception

```python
class AppException(Exception):
    def __init__(self, message: str, code: str = None):
        self.message = message
        self.code = code or "UNKNOWN_ERROR"
        super().__init__(self.message)
```

### Exception Categories

| Exception Class | Purpose | HTTP Status |
|-----------------|---------|-------------|
| `ValidationError` | Parameter validation failed | 400 |
| `AuthenticationError` | Authentication failed | 401 |
| `NotFoundError` | Resource not found | 404 |
| `BusinessError` | Business logic error | 422 |
| `InternalError` | Internal error | 500 |

## Error Code Design

### Error Code Format

```
{module}{type}{sequence}
```

- Module: 2 letters
- Type: 1 digit
- Sequence: 3 digits

### Error Code Categories

| Range | Type | Example |
|-------|------|---------|
| xx1xxx | Validation errors | US1001 Invalid username format |
| xx2xxx | Business errors | OR2001 Insufficient inventory |
| xx3xxx | System errors | PA3001 Payment gateway timeout |

## Error Propagation Rules

### When to Catch

| Scenario | Handling |
|----------|----------|
| Can recover | Catch and handle |
| Need to transform | Catch and throw more specific exception |
| Need to log | Catch, log, re-throw |
| Cannot handle | Don't catch, let upper layer handle |

## Error Response Format

```json
{
  "code": "US2001",
  "message": "User not found",
  "details": {
    "resource": "User",
    "identifier": "123"
  }
}
```
```

## Usage Example

```
/generate-error-handling

We use Python + FastAPI, need unified error handling standards
```
