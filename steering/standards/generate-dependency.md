---
inclusion: manual
---

# Generate Dependency Management Standards Steering

Please help me generate a dependency management standards file.

## Required Information

Please generate dependency standards based on the following questions (ask me if not provided):

### 1. Package Manager
- What package manager? (pip / npm / yarn)
- Using lock files?

### 2. Version Strategy
- Version locking strategy?
- Update frequency?

### 3. Security Checks
- Vulnerability scanning?
- License checking?

## Output Format

```markdown
---
inclusion: manual
---

# Dependency Management Standards

## Basic Principles

1. **Lock Versions** - Use exact version numbers to avoid unexpected upgrades
2. **Regular Updates** - Check and update dependencies monthly
3. **Security Checks** - Scan for vulnerabilities before each update
4. **Minimal Dependencies** - Only add necessary dependencies

## Version Strategy

| Strategy | Format | Example | Use Case |
|----------|--------|---------|----------|
| Exact version | x.y.z | `1.2.3` | Production deps |
| Compatible version | ^x.y.z | `^1.2.3` | Dev deps |
| Latest version | * | `*` | ❌ Prohibited |

## Dependency Files

### Python Project

```
requirements.txt      # Production dependencies
requirements-dev.txt  # Development dependencies
requirements.lock     # Locked versions (optional)
```

### Dependency Categories

```txt
# requirements.txt - Production dependencies
fastapi==0.95.0
sqlalchemy==2.0.0
pydantic==1.10.0

# requirements-dev.txt - Development dependencies
-r requirements.txt
pytest==7.3.0
black==23.3.0
flake8==6.0.0
```

## Adding Dependencies Process

1. **Evaluate Necessity** - Do we really need this dependency?
2. **Check Security** - Any known vulnerabilities?
3. **Check License** - Is the license compatible?
4. **Check Maintenance** - Is it actively maintained?
5. **Add and Lock** - Add with exact version number

## Security Checks

### Vulnerability Scanning

```bash
# Python
pip-audit
safety check

# Node.js
npm audit
```

### Regular Checks

- Weekly automatic vulnerability scans
- Monthly dependency update checks
- Quarterly dependency necessity review

## Update Process

```bash
# 1. Create update branch
git checkout -b deps/update-2024-01

# 2. Update dependencies
pip install --upgrade package-name

# 3. Run tests
pytest

# 4. Commit and review
git commit -m "chore(deps): update package-name to x.y.z"
```

## Prohibited Actions

| Prohibited | Reason |
|------------|--------|
| Using `*` version | May introduce breaking changes |
| Directly modifying lock file | Should update via package manager |
| Ignoring security warnings | May have vulnerabilities |
| Adding unused dependencies | Increases attack surface and maintenance cost |
```

## Usage Example

```
/generate-dependency

We use Python + pip, need dependency management standards
```
