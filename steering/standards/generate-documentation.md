---
inclusion: manual
---

# Generate Documentation Standards Steering

Please help me generate a documentation standards file.

> **Important**: Detect the user's project language and generate docstring/comment examples accordingly. Python uses docstrings (Google/NumPy style), TypeScript/JavaScript uses JSDoc, Go uses godoc comments, Java uses Javadoc, etc.

## Required Information

Please generate documentation standards based on the following questions (ask me if not provided):

### 1. Documentation Types
- What types of documentation needed?
- Target audience?

### 2. Code Comments
- What comment style?
- What needs comments?

### 3. API Documentation
- What tool to generate?
- Documentation format requirements?

## Output Format

```markdown
---
inclusion: always
---

# Documentation Standards

## Documentation Types

| Type | Location | Target Audience | Update Frequency |
|------|----------|-----------------|------------------|
| README | Project root | Everyone | On feature changes |
| API docs | docs/api/ | Developers | On API changes |
| Architecture docs | docs/architecture/ | Developers | On architecture changes |
| User guide | docs/guide/ | End users | On feature changes |
| Changelog | CHANGELOG.md | Everyone | Each release |

## Code Comments

### When Comments Are Needed

| Scenario | Required | Notes |
|----------|----------|-------|
| Public API | ✅ Must | All public functions, classes, methods |
| Complex logic | ✅ Must | Non-obvious algorithms or business logic |
| Temporary solutions | ✅ Must | TODO/FIXME markers |
| Simple code | ❌ Not needed | Code is already clear |
| Private methods | ⚠️ Depends | Complex private methods need them |

### When Comments Are NOT Needed

```python
# ❌ Not needed: code is already clear
# Get user
user = get_user(user_id)

# ❌ Not needed: comment repeats code
# Increment counter
counter += 1

# ✅ Needed: explains why
# Using 30s timeout because external API is slow
timeout = 30
```

## Python Docstrings

### Module Documentation

```python
"""
User service module

Provides user-related business logic including:
- User creation and management
- User authentication
- Permission checking

Example:
    from services.user_service import UserService
    
    service = UserService()
    user = service.get_user(123)
"""
```

### Class Documentation

```python
class UserService:
    """User service class
    
    Handles user-related business logic.
    
    Attributes:
        db: Database connection
        cache: Cache client
    
    Example:
        service = UserService()
        user = service.get_user(123)
    """
```

### Function Documentation (Google Style)

```python
def get_user_by_id(user_id: int, include_deleted: bool = False) -> User:
    """Get user by ID
    
    Query user information from database by specified ID.
    
    Args:
        user_id: User ID
        include_deleted: Whether to include deleted users, default False
    
    Returns:
        User: User object
    
    Raises:
        NotFoundError: Raised when user doesn't exist
        DatabaseError: Raised when database query fails
    
    Example:
        user = get_user_by_id(123)
        print(user.name)
    """
```

### Simple Functions

```python
def is_valid_email(email: str) -> bool:
    """Validate if email format is correct"""
    return bool(re.match(EMAIL_PATTERN, email))
```

## Inline Comments

### Usage Rules

```python
# ✅ Good inline comment: explains why
timeout = 30  # External API is slow, needs longer timeout

# ✅ Good inline comment: explains complex logic
# Using bitwise operation to check permission, more efficient than loop
has_permission = (user_permissions & required_permission) != 0

# ❌ Bad inline comment: explains what (code already shows)
user_count = len(users)  # Get user count
```

### TODO/FIXME Markers

```python
# TODO: Add cache support to improve query performance
# TODO(john): Need to complete before v2.0

# FIXME: Concurrency issue here, needs locking
# FIXME(jane): Temporary solution, waiting for upstream fix

# HACK: Workaround for third-party library bug
# NOTE: This algorithm has O(n^2) time complexity
# WARNING: Do not use in production
```

## README Standards

### Must Include

```markdown
# Project Name

Brief project description (one or two sentences)

## Features

- Feature 1
- Feature 2
- Feature 3

## Quick Start

### Requirements

- Python >= 3.9
- PostgreSQL >= 13

### Installation

```bash
pip install -r requirements.txt
```

### Configuration

```bash
cp .env.example .env
# Edit .env file
```

### Run

```bash
python main.py
```

## Usage Example

```python
# Example code
```

## Project Structure

```
src/
├── api/
├── services/
└── models/
```

## Development Guide

### Run Tests

```bash
pytest
```

### Code Standards

```bash
black .
flake8
```

## Contributing

1. Fork the project
2. Create feature branch
3. Submit PR

## License

MIT License
```

## Changelog

### Format

```markdown
# Changelog

## [1.2.0] - 2024-01-15

### Added
- Added user export feature
- Added batch delete API

### Changed
- Optimized query performance
- Updated dependency versions

### Fixed
- Fixed login timeout issue
- Fixed data export encoding issue

### Deprecated
- Deprecated v1 API, will be removed in 2.0

### Removed
- Removed old config format support

### Security
- Fixed XSS vulnerability
```

## Documentation Maintenance

### When to Update

| Event | Documentation to Update |
|-------|------------------------|
| New feature | README, API docs, Changelog |
| Bug fix | Changelog |
| API change | API docs, Changelog |
| Architecture change | Architecture docs |
| Version release | Changelog |

### Review Checklist

- [ ] Documentation matches code
- [ ] Example code runs
- [ ] Links are valid
- [ ] Format is correct
- [ ] No spelling errors
```

## Usage Example

```
/generate-documentation

We use Python + FastAPI, need documentation standards
```
