---
inclusion: manual
---

# Generate Project Structure Steering

Please help me generate a project structure file `structure.md`.

## Required Information

Please generate the project structure document based on the following questions (analyze project directory or ask me if not provided):

### 1. Directory Structure
- Main directories and their purposes
- File organization approach

### 2. Naming Conventions
- File naming rules
- Directory naming rules
- Module naming rules

### 3. Import Rules
- Import order
- Path aliases
- Circular dependency handling

### 4. Architecture Decisions
- Layering approach
- Module boundaries
- Dependency direction

## Output Format

```markdown
---
inclusion: always
---

# Project Structure

## Directory Structure

project-root/
├── src/                    # Source code
│   ├── api/               # API layer
│   ├── services/          # Business logic layer
│   ├── models/            # Data models
│   ├── utils/             # Utility functions
│   └── config/            # Configuration
├── tests/                  # Test code
│   ├── unit/              # Unit tests
│   └── integration/       # Integration tests
├── docs/                   # Documentation
├── scripts/                # Scripts
└── config/                 # Config files

## Directory Descriptions

### src/
Source code directory containing all business code.

#### src/api/
API layer, handles HTTP requests and responses.
- One file per resource
- File naming: `{resource}.py`

#### src/services/
Business logic layer containing core business logic.
- One file per domain
- File naming: `{domain}_service.py`

### tests/
Test code, structure mirrors src/.

## Naming Conventions

### File Naming

| Type | Rule | Example |
|------|------|---------|
| Python module | snake_case | `user_service.py` |
| Test file | test_{module} | `test_user_service.py` |
| Config file | snake_case | `settings.yml` |

### Class Naming

| Type | Rule | Example |
|------|------|---------|
| Regular class | PascalCase | `UserService` |
| Exception class | PascalCase + Error/Exception | `ValidationError` |
| Abstract class | Base + PascalCase | `BaseCrawler` |

## Import Rules

### Import Order

1. Standard library
2. Third-party libraries
3. Local modules

Blank line between each group.

```python
# Standard library
import os
from datetime import datetime

# Third-party libraries
import requests
from fastapi import FastAPI

# Local modules
from src.services import UserService
```

## Architecture Rules

### Layered Architecture

API Layer (api/)
    ↓ calls
Business Layer (services/)
    ↓ calls
Data Layer (models/, repositories/)

### Dependency Direction

- Upper layers can depend on lower layers
- Lower layers cannot depend on upper layers
- Same-layer communication through interfaces
```

## Usage Example

```
/generate-structure

Please analyze #src/ directory structure and generate project structure document
```

## Why structure.md?

When Kiro understands your project structure, it can:
- Create new files in the correct location
- Follow project naming conventions
- Organize import statements correctly
- Respect architecture boundaries
