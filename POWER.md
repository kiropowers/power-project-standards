---
name: "project-standards"
displayName: "Project Standards Generator"
description: "Generate project documentation, coding standards, and extract knowledge from conversations and code"
keywords: ["steering", "template", "standards", "code review", "naming", "documentation", "project setup", "extract", "generate"]
author: "sol.tao"
---

# Project Standards Generator

This power helps you quickly establish project standards and documentation through slash commands.

## Available Commands

### 📥 Knowledge Extraction

| Command | Description |
|---------|-------------|
| `/extract-from-chat` | Extract steering from current conversation |
| `/extract-by-topic` | Extract steering by specific topic |
| `/extract-from-code` | Analyze code and extract patterns as steering |
| `/weekly-summary` | Periodic knowledge consolidation |

### 🏗️ Foundation Documents

| Command | Description |
|---------|-------------|
| `/generate-product` | Generate product overview (product.md) |
| `/generate-tech` | Generate tech stack documentation |
| `/generate-structure` | Generate project structure documentation |

### 📋 Standards Generation

| Command | Description |
|---------|-------------|
| `/generate-code-review` | Code review checklist |
| `/generate-naming-conventions` | Naming conventions |
| `/generate-error-handling` | Error handling standards |
| `/generate-security` | Security coding standards |
| `/generate-git-workflow` | Git workflow standards |
| `/generate-api-standards` | API design standards |
| `/generate-db-standards` | Database standards |
| `/generate-test-standards` | Testing standards |
| `/generate-logging-standards` | Logging standards |
| `/generate-documentation` | Documentation standards |
| `/generate-performance` | Performance optimization guide |
| `/generate-async-patterns` | Async programming patterns |
| `/generate-deployment` | Deployment standards |
| `/generate-monitoring` | Monitoring and alerting standards |
| `/generate-dependency` | Dependency management standards |
| `/generate-versioning` | Version control + auto CHANGELOG |

## Usage

1. Use any slash command above in chat
2. Provide context when prompted
3. Review the generated steering file
4. Save to `.kiro/steering/` directory

## Recommended Workflow

### New Project Setup

```
/generate-product    → product.md
/generate-tech       → tech.md  
/generate-structure  → structure.md
```

### Establish Standards

```
/generate-git-workflow
/generate-code-review
/generate-naming-conventions
```

### Knowledge Extraction

After valuable discussions:
```
/extract-from-chat
```

Or analyze existing code:
```
/extract-from-code
```
