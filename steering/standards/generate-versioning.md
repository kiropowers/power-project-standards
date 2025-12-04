---
inclusion: manual
---

# Generate Version Control Configuration Steering

Please help me configure automated version control and CHANGELOG generation for the project.

## Features

This command will help you configure:
1. **standard-version** - Auto-generate CHANGELOG.md
2. **Conventional Commits** - Standardized commit messages
3. **Semantic Versioning** - Auto-calculate version numbers
4. **Release Scripts** - One-click release new versions

## Required Information

Please tell me (I'll use defaults if not provided):

### 1. Project Information
- Project name?
- Project description?
- Git repository URL?

### 2. Branch Configuration
- Main branch name? (main / master)
- Push to remote?

### 3. Additional Configuration
- Need commitlint (commit message checking)?
- Need husky (Git hooks)?

## Execution Steps

I will help you complete the following configuration:

### Step 1: Create/Update package.json

```json
{
  "name": "your-project-name",
  "version": "0.1.0",
  "description": "Project description",
  "scripts": {
    "release": "standard-version",
    "release:minor": "standard-version --release-as minor",
    "release:major": "standard-version --release-as major",
    "release:patch": "standard-version --release-as patch",
    "release:first": "standard-version --first-release"
  },
  "devDependencies": {
    "standard-version": "^9.5.0"
  }
}
```

### Step 2: Create .versionrc.json (optional, custom config)

```json
{
  "types": [
    {"type": "feat", "section": "✨ Features"},
    {"type": "fix", "section": "🐛 Bug Fixes"},
    {"type": "docs", "section": "📚 Documentation"},
    {"type": "style", "section": "💄 Styles"},
    {"type": "refactor", "section": "♻️ Refactoring"},
    {"type": "perf", "section": "⚡ Performance"},
    {"type": "test", "section": "✅ Tests"},
    {"type": "chore", "section": "🔧 Chores"},
    {"type": "ci", "section": "👷 CI/CD"}
  ],
  "commitUrlFormat": "{{host}}/{{owner}}/{{repository}}/commit/{{hash}}",
  "compareUrlFormat": "{{host}}/{{owner}}/{{repository}}/compare/{{previousTag}}...{{currentTag}}"
}
```

### Step 3: Create Initial CHANGELOG.md

```markdown
# Changelog

All notable changes to this project will be documented in this file.

See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.
```

## Usage

After configuration, you can use it like this:

### Daily Commits (Following Conventional Commits)

```bash
# New feature
git commit -m "feat(user): add user login functionality"

# Bug fix
git commit -m "fix(auth): fix token expiration issue"

# Documentation update
git commit -m "docs(readme): update installation instructions"

# Refactoring
git commit -m "refactor(api): refactor user interface"

# Performance optimization
git commit -m "perf(db): optimize query performance"
```

### Release New Version

```bash
# Auto-determine version (based on commit types)
pnpm release

# Specify version type
pnpm release:patch   # 0.1.0 → 0.1.1 (Bug fixes)
pnpm release:minor   # 0.1.0 → 0.2.0 (New features)
pnpm release:major   # 0.1.0 → 1.0.0 (Breaking changes)

# First release
pnpm release:first
```

### Version Auto-Calculation Rules

| Commit Type | Version Change | Example |
|-------------|----------------|---------|
| fix | PATCH | 0.1.0 → 0.1.1 |
| feat | MINOR | 0.1.0 → 0.2.0 |
| BREAKING CHANGE | MAJOR | 0.1.0 → 1.0.0 |

## Generated CHANGELOG Example

```markdown
# Changelog

## [0.2.0](https://github.com/user/repo/compare/v0.1.0...v0.2.0) (2024-01-15)

### ✨ Features

* **user:** add user login functionality ([abc1234](https://github.com/user/repo/commit/abc1234))
* **order:** add order export functionality ([def5678](https://github.com/user/repo/commit/def5678))

### 🐛 Bug Fixes

* **auth:** fix token expiration issue ([ghi9012](https://github.com/user/repo/commit/ghi9012))

### 📚 Documentation

* **readme:** update installation instructions ([jkl3456](https://github.com/user/repo/commit/jkl3456))
```

## Optional: Add Commit Checking (commitlint + husky)

If you need to enforce commit message format:

### Install Dependencies

```bash
pnpm add -D @commitlint/cli @commitlint/config-conventional husky
```

### Create commitlint.config.js

```javascript
module.exports = {
  extends: ['@commitlint/config-conventional'],
  rules: {
    'type-enum': [2, 'always', [
      'feat', 'fix', 'docs', 'style', 'refactor',
      'perf', 'test', 'chore', 'ci', 'revert'
    ]],
    'subject-case': [0],
  }
};
```

### Configure husky

```bash
npx husky install
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit "$1"'
```

## Usage Example

```
/generate-versioning

Please help me configure version control, project name is my-project, main branch is main
```

or

```
/generate-versioning

I need full configuration including commitlint and husky
```

---

## Quick Setup (Minimal)

If you only need basic configuration:

1. Create `package.json` (if not exists)
2. Run `pnpm add -D standard-version`
3. Add release scripts
4. Start using!

```bash
# Initialize
pnpm init
pnpm add -D standard-version

# Add scripts (manually edit package.json or let me help)
# Then you can use
pnpm release
```
