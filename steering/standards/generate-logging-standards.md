---
inclusion: manual
---

# Generate Logging Standards Steering

Please help me generate a logging standards file.

> **Important**: Detect the user's project language and recommend appropriate logging libraries. Python uses logging/loguru, JavaScript/TypeScript uses winston/pino, Go uses zap/zerolog, Java uses SLF4J/Log4j, etc. Generate examples in the detected language.

## Required Information

Please generate logging standards based on the following questions (ask me if not provided):

### 1. Logging Framework
- What logging library?
- Log output destinations?

### 2. Log Levels
- Use cases for each level?
- Default level for production?

### 3. Log Format
- Log message format?
- What fields to include?

### 4. Special Requirements
- Sensitive data handling?
- Performance considerations?

## Output Format

```markdown
---
inclusion: always
---

# Logging Standards

## Log Levels

| Level | Purpose | Example Scenario |
|-------|---------|------------------|
| DEBUG | Debug information | Variable values, function calls |
| INFO | Normal operation info | Request handling, task completion |
| WARNING | Warnings | Retries, degradation |
| ERROR | Errors | Request failures, validation failures |
| CRITICAL | Critical errors | Service unavailable |

## Logging Functions

```python
# Use project's unified logging functions
from utils.logger import log_print, log_debug

log_print("User login successful")           # INFO
log_debug("Request params: ...")             # DEBUG
log_print("Validation failed", "WARNING")    # WARNING
log_print("Database connection failed", "ERROR") # ERROR
```

## Log Format

```
{timestamp} - {module} - {level} - {message}
```

## Log Content Standards

### Required Information

| Scenario | Must Include |
|----------|--------------|
| API request | Request ID, method, path, status code, duration |
| Database operation | Operation type, table name, duration |
| Error log | Error type, error message |

### Writing Log Messages

```python
# ✅ Good log message
log_print(f"[UserService] User {user_id} login successful")

# ❌ Bad log message
log_print("Success")  # Too vague
```

## Sensitive Data Handling

### Prohibited Information

- Passwords, keys, tokens
- Full credit card numbers
- Full ID numbers, phone numbers

### Data Masking

```python
log_print(f"User phone: {phone[:3]}****{phone[-4:]}")
```
```

## Usage Example

```
/generate-logging-standards

We use custom log_print/log_debug functions, need logging standards
```
