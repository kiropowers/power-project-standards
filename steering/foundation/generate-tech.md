---
inclusion: manual
---

# Generate Tech Stack Steering

Please help me generate a tech stack file `tech.md`.

## Required Information

Please generate the tech stack document based on the following questions (analyze project files or ask me if not provided):

### 1. Core Technologies
- Programming language and version
- Main frameworks
- Runtime environment

### 2. Dependencies
- Core dependencies (must use)
- Utility libraries (recommended)
- Prohibited libraries (if any)

### 3. Development Tools
- Package manager
- Build tools
- Testing framework
- Code linting tools

### 4. Infrastructure
- Database
- Cache
- Message queue
- Cloud services

## Output Format

```markdown
---
inclusion: always
---

# Tech Stack

## Core Technologies

| Category | Technology | Version | Notes |
|----------|------------|---------|-------|
| Language | [Language] | [Version] | [Notes] |
| Framework | [Framework] | [Version] | [Notes] |
| Runtime | [Runtime] | [Version] | [Notes] |

## Dependency Management

### Package Manager
- Use [package manager name]
- Lock file: [lock file name]

### Core Dependencies

| Library | Purpose | Notes |
|---------|---------|-------|
| [Library] | [Purpose] | [Notes] |

### Recommended Libraries

The following libraries are team-recommended:

| Scenario | Recommended | Reason |
|----------|-------------|--------|
| HTTP requests | [Library] | [Reason] |
| Date handling | [Library] | [Reason] |
| Data validation | [Library] | [Reason] |

### Prohibited Libraries

The following libraries are prohibited in this project:

| Library | Reason | Alternative |
|---------|--------|-------------|
| [Library] | [Reason] | [Alternative] |

## Development Tools

### Build Tools
- [Tool]: [Purpose]

### Testing Framework
- Unit tests: [Framework]
- Integration tests: [Framework]
- E2E tests: [Framework]

### Code Quality
- Linter: [Tool]
- Formatter: [Tool]
- Type checking: [Tool]

## Infrastructure

### Database
- Primary database: [Database]
- Purpose: [Description]

### Cache
- [Cache solution]

### Other Services
- [Service list]

## Technical Constraints

### Must Follow
- [Constraint 1]
- [Constraint 2]

### Performance Requirements
- [Requirement 1]
- [Requirement 2]

## Version Requirements

- Node.js >= [version]
- Python >= [version]
- [Other version requirements]
```

## Usage Example

```
/generate-tech

Please analyze #package.json and #requirements/ directory to generate tech stack document
```

or

```
/generate-tech

Tech stack:
- Python 3.11
- FastAPI
- PostgreSQL
- Redis
- pytest
```

## Why tech.md?

When Kiro knows your tech stack, it can:
- Use correct libraries and APIs
- Follow framework best practices
- Avoid introducing incompatible dependencies
- Generate code that meets version requirements
