---
inclusion: manual
---

# Generate Git Workflow Standards Steering

Please help me generate a Git workflow standards file.

## Required Information

Please generate Git standards based on the following questions (ask me if not provided):

### 1. Branch Strategy
- What branching model?
- What are the main branches?

### 2. Commit Standards
- Commit message format?
- Commit granularity requirements?

### 3. Merge Strategy
- PR/MR process?
- Code review requirements?

### 4. Release Process
- Version number rules?
- Release branch management?

## Output Format

```markdown
---
inclusion: manual
---

# Git Workflow Standards

## Branch Strategy

### Branch Types

| Branch | Purpose | Naming Rule |
|--------|---------|-------------|
| main | Production code | main |
| develop | Development integration | develop |
| feature | New features | feature/{issue-id}-{description} |
| bugfix | Bug fixes | bugfix/{issue-id}-{description} |
| hotfix | Emergency fixes | hotfix/{version}-{description} |

## Commit Standards

### Commit Message Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type Categories

| Type | Description |
|------|-------------|
| feat | New feature |
| fix | Bug fix |
| docs | Documentation update |
| style | Code formatting |
| refactor | Refactoring |
| perf | Performance optimization |
| test | Testing related |
| chore | Build/tooling |

### Commit Example

```
feat(auth): add user login functionality

- Implement username/password login
- Add JWT token generation

Closes #123
```

## Pull Request Standards

### PR Rules

| Rule | Requirement |
|------|-------------|
| Size | Single PR should not exceed 500 lines changed |
| Review | At least 1 reviewer approval |
| CI | All checks must pass |

## Version Management

### Version Number Rules (Semantic Versioning)

```
MAJOR.MINOR.PATCH
```

| Part | When to Increment |
|------|-------------------|
| MAJOR | Incompatible API changes |
| MINOR | Backward-compatible new features |
| PATCH | Backward-compatible bug fixes |
```

## Usage Example

```
/generate-git-workflow

Our team uses GitHub, need a Git workflow standard
```
