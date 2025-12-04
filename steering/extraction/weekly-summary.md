---
inclusion: manual
---

# Periodic Knowledge Consolidation

This is the knowledge consolidation session for this week/sprint. Please review all our conversations and extract content that should be consolidated as Steering.

## Review Scope

Please check the following areas:

### 1. New Technical Decisions
- What new technology/library/tool was introduced?
- Why was it chosen?
- What usage conventions apply?

### 2. Discovered Best Practices
- What approaches worked well?
- What patterns are worth promoting?
- What tips can be shared?

### 3. Lessons Learned
- What problems were encountered?
- What was the root cause?
- How to prevent recurrence?

### 4. New Standards Requirements
- Any new code standards?
- Any process changes?
- Any security requirements?

### 5. Architecture Evolution
- Any architecture changes?
- Any module boundary adjustments?
- Any data flow changes?

## Output Requirements

### 1. Change Summary

First output this week's change summary:

```
## Weekly Knowledge Consolidation Summary

### New Steering Files
1. [filename] - [brief description]
2. [filename] - [brief description]

### Updated Steering Files
1. [filename] - [update content]
2. [filename] - [update content]

### No Changes Needed
- [Explain why certain discussions don't need consolidation]
```

### 2. New Steering Files

For new Steering files, provide complete content:

```markdown
---
inclusion: [mode]
---

# [Title]

[Complete content]
```

### 3. Update Suggestions

For existing Steering that needs updates, specify:
- Which file to update
- Which section to update
- New/modified content

```
### Update: api-standards.md

Add after "Error Handling" section:

## Rate Limiting

When API returns 429 status code:
1. Read Retry-After header
2. Wait specified time before retry
3. Maximum 3 retries

Example:
...
```

## Checklist

Before completing consolidation, confirm:

- [ ] All important decisions are documented
- [ ] Standards are clear and actionable
- [ ] Example code is correct and representative
- [ ] inclusion mode is appropriate
- [ ] No sensitive information included
- [ ] No conflicts with existing Steering

## Follow-up Actions

After consolidation, recommend:

1. **Review Generated Content**
   - Confirm accuracy
   - Add missing details

2. **Save Files**
   - Save new files to `.kiro/steering/`
   - Update existing files

3. **Notify Team**
   - Notify relevant people of important changes
   - Conduct team review if necessary

4. **Verify Activation**
   - Start a new conversation
   - Confirm Steering loads correctly
