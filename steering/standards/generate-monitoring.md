---
inclusion: manual
---

# Generate Monitoring and Alerting Standards Steering

Please help me generate a monitoring and alerting standards file.

## Required Information

Please generate monitoring standards based on the following questions (ask me if not provided):

### 1. Monitoring Tools
- What monitoring tools?
- Log collection method?

### 2. Metrics
- What metrics to monitor?
- What business metrics?

### 3. Alert Rules
- Alert thresholds?
- Alert notification methods?

### 4. Incident Response
- On-call schedule?
- Incident severity levels?

## Output Format

```markdown
---
inclusion: manual
---

# Monitoring and Alerting Standards

## Monitoring Metrics

### System Metrics

| Metric | Description | Alert Threshold |
|--------|-------------|-----------------|
| CPU Usage | Server CPU | > 80% |
| Memory Usage | Server memory | > 85% |
| Disk Usage | Disk space | > 90% |
| Network Traffic | Inbound/outbound | Abnormal fluctuation |

### Application Metrics

| Metric | Description | Alert Threshold |
|--------|-------------|-----------------|
| Request Latency | API response time | P95 > 500ms |
| Error Rate | 5xx error ratio | > 1% |
| Request Volume | QPS | Abnormal fluctuation |
| Active Connections | Database connections | > 80% |

### Business Metrics

| Metric | Description | Alert Threshold |
|--------|-------------|-----------------|
| Order Volume | Hourly orders | Drop > 50% |
| User Registration | Daily new users | Drop > 30% |
| Payment Success Rate | Payment success ratio | < 95% |

## Logging Standards

### Log Levels

| Level | Purpose | Alert |
|-------|---------|-------|
| DEBUG | Debug info | No |
| INFO | Normal operation | No |
| WARNING | Needs attention | Optional |
| ERROR | Errors | Yes |
| CRITICAL | Critical errors | Immediate |

### Structured Logging

```json
{
  "timestamp": "2024-01-15T10:30:45Z",
  "level": "ERROR",
  "service": "user-service",
  "message": "Database connection failed",
  "context": {
    "error": "Connection refused",
    "retry_count": 3
  }
}
```

## Alert Rules

### Alert Severity Levels

| Level | Response Time | Notification | Example |
|-------|---------------|--------------|---------|
| P0 | 5 minutes | Phone + SMS | Service unavailable |
| P1 | 15 minutes | SMS + Slack | Error rate spike |
| P2 | 1 hour | Slack | Performance degradation |
| P3 | 24 hours | Email | Disk space low |

### Alert Suppression

- Same alert not repeated within 5 minutes
- Send recovery notification after resolution
- Silence alerts during maintenance windows

## Incident Response

### Response Process

```
Alert triggered → Acknowledge → Assess impact → Handle incident → Restore service → Post-mortem
```

### Post-mortem Template

```markdown
## Incident Report

**Time**: 2024-01-15 10:30 - 11:00
**Impact**: Users unable to login
**Cause**: Database connection pool exhausted
**Resolution**: Restarted service, increased pool size
**Improvement**: Add connection pool monitoring alert
```
```

## Usage Example

```
/generate-monitoring

We need monitoring and alerting standards, using Prometheus + Grafana
```
