---
inclusion: manual
---

# Generate Security Coding Standards Steering

Please help me generate a security coding standards file.

> **Important**: Detect the user's project language and generate security examples accordingly. Adapt SQL injection prevention, input validation, and authentication patterns to the specific language and framework being used.

## Required Information

Please generate security standards based on the following questions (ask me if not provided):

### 1. Application Type
- Web app / API / CLI?
- What type of data is processed?

### 2. Authentication & Authorization
- Authentication method?
- Permission model?

### 3. Data Security
- Sensitive data types?
- Encryption requirements?

## Output Format

```markdown
---
inclusion: always
---

# Security Coding Standards

## Basic Principles

1. **Least Privilege** - Only grant necessary permissions
2. **Defense in Depth** - Multiple layers of security
3. **Secure by Default** - Default configuration should be secure
4. **Fail Securely** - Failures should fail safely

## Input Validation

### All Input is Untrusted

```python
# ✅ Correct: validate all input
def create_user(data: dict):
    if not data.get("email"):
        raise ValidationError("Email is required")
    if not is_valid_email(data["email"]):
        raise ValidationError("Invalid email format")
```

## SQL Injection Prevention

```python
# ✅ Correct: parameterized query
cursor.execute(
    "SELECT * FROM users WHERE id = %s",
    (user_id,)
)

# ❌ Wrong: string concatenation
cursor.execute(f"SELECT * FROM users WHERE id = {user_id}")
```

## Authentication Security

### Password Handling

```python
from passlib.context import CryptContext

pwd_context = CryptContext(schemes=["bcrypt"])

def hash_password(password: str) -> str:
    return pwd_context.hash(password)
```

## Sensitive Data Protection

### Sensitive Data Classification

| Level | Data Type | Handling Requirements |
|-------|-----------|----------------------|
| High | Passwords, keys | Encrypted storage, no logging |
| Medium | ID numbers, bank cards | Encrypted storage, masked display |
| Low | Phone numbers, emails | Masked display |

### Data Masking

```python
def mask_phone(phone: str) -> str:
    return f"{phone[:3]}****{phone[-4:]}"
```

## Configuration Security

```python
# ✅ Correct: read from environment variables
DATABASE_URL = os.getenv("DATABASE_URL")

# ❌ Wrong: hardcoded
DATABASE_URL = "postgresql://user:password@localhost/db"
```

## Logging Security

```python
# ❌ Prohibited logging
logger.info(f"User password: {password}")

# ✅ Correct: log after masking
logger.info(f"User login: user_id={user_id}")
```
```

## Usage Example

```
/generate-security

We are a web application handling user personal information, need security coding standards
```
