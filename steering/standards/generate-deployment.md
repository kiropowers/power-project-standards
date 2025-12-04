---
inclusion: manual
---

# Generate Deployment Standards Steering

Please help me generate a deployment standards file.

## Required Information

Please generate deployment standards based on the following questions (ask me if not provided):

### 1. Deployment Environment
- Where to deploy? (cloud / self-hosted / containers)
- What environments? (dev / staging / prod)

### 2. CI/CD
- What CI/CD tool?
- Automation level?

### 3. Configuration Management
- How to manage environment variables?
- How to manage secrets?

### 4. Release Strategy
- Blue-green / rolling update / canary?
- Rollback strategy?

## Output Format

```markdown
---
inclusion: manual
---

# Deployment Standards

## Environment Configuration

| Environment | Purpose | URL | Branch |
|-------------|---------|-----|--------|
| dev | Development testing | dev.example.com | develop |
| staging | Pre-production | staging.example.com | release/* |
| prod | Production | example.com | main |

## CI/CD Pipeline

### Pipeline Stages

```
Code commit → Code check → Unit tests → Build → Deploy to test → Integration tests → Deploy to prod
```

### GitHub Actions Example

```yaml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Run tests
        run: pytest
      
      - name: Build
        run: docker build -t app:${{ github.sha }} .
      
      - name: Deploy
        run: ./deploy.sh
```

## Configuration Management

### Environment Variables

```bash
# .env.example (commit to Git)
DATABASE_URL=postgresql://user:pass@localhost/db
REDIS_URL=redis://localhost:6379
API_KEY=your-api-key

# Production injects via env vars or secret management service
```

### Configuration Layers

| Layer | Content | Example |
|-------|---------|---------|
| Code defaults | Dev environment defaults | `DEBUG=True` |
| Config files | Environment-specific config | `config/prod.yaml` |
| Environment variables | Sensitive info | `DATABASE_URL` |

## Release Strategy

### Rolling Update

```yaml
# Kubernetes rolling update
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
```

### Rollback Process

```bash
# 1. Confirm rollback needed
# 2. Execute rollback
kubectl rollout undo deployment/app

# 3. Verify service
curl https://api.example.com/health

# 4. Notify team
```

## Deployment Checklist

### Before Deployment

- [ ] Code review passed
- [ ] All tests passed
- [ ] Database migrations ready
- [ ] Configuration updated
- [ ] Relevant people notified

### After Deployment

- [ ] Health check passed
- [ ] Monitoring metrics normal
- [ ] Critical functionality verified
- [ ] No abnormal errors in logs

## Prohibited Actions

| Prohibited | Reason |
|------------|--------|
| Directly modifying code on prod server | Cannot track changes |
| Skipping test env to deploy to prod | Too risky |
| Deploying during peak hours | Affects user experience |
| Deploying without notifying team | No one knows if issues occur |
```

## Usage Example

```
/generate-deployment

We use Docker + Kubernetes, need deployment standards
```
