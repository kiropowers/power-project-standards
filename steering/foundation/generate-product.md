---
inclusion: manual
---

# Generate Product Overview Steering

Please help me generate a product overview file `product.md`.

## Required Information

Please generate the product overview based on the following questions (ask me if not provided):

### 1. Product Positioning
- What is this product? (one sentence)
- What problem does it solve?
- Who are the target users?

### 2. Core Features
- What are the main features? (list 3-5)
- Brief description of each feature

### 3. Business Goals
- What are the business objectives?
- What are the success metrics?

### 4. Constraints
- Any business constraints?
- Any compliance requirements?

## Output Format

```markdown
---
inclusion: always
---

# Product Overview

## Product Positioning

[Product Name] is a [product type] that helps [target users] solve [core problem].

## Target Users

### Primary Users
- **[User Role 1]**: [Description]
- **[User Role 2]**: [Description]

### User Needs
- [Need 1]
- [Need 2]
- [Need 3]

## Core Features

### [Feature 1]
[Feature description]

### [Feature 2]
[Feature description]

### [Feature 3]
[Feature description]

## Business Goals

- [Goal 1]
- [Goal 2]
- [Goal 3]

## Success Metrics

- [Metric 1]
- [Metric 2]

## Constraints

### Business Constraints
- [Constraint 1]
- [Constraint 2]

### Compliance Requirements
- [Requirement 1]
- [Requirement 2]

## Non-Goals

The following are out of scope for the current product:
- [Non-goal 1]
- [Non-goal 2]
```

## Usage Example

```
/generate-product

This is a bid monitoring system that helps companies discover bidding opportunities.
Target users are sales staff and bid managers.
Core features include: multi-platform crawling, keyword matching, email notifications, report generation.
```

## Why product.md?

When Kiro understands your product goals, it can:
- Provide suggestions aligned with business needs
- Consider business impact in technical decisions
- Generate code that better fits user requirements
- Avoid implementations that deviate from product direction
