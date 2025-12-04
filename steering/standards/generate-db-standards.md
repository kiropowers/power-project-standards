---
inclusion: manual
---

# Generate Database Standards Steering

Please help me generate a database operations standards file.

> **Important**: Detect the user's project language and recommend appropriate ORMs/database libraries. Python uses SQLAlchemy/Prisma, TypeScript uses Prisma/TypeORM/Drizzle, Go uses GORM/sqlx, Java uses JPA/Hibernate, etc. Generate examples in the detected language.

## Required Information

Please generate database standards based on the following questions (ask me if not provided):

### 1. Database Type
- What database?
- ORM framework?

### 2. Connection Management
- Connection pool config
- Timeout settings

### 3. Query Standards
- Query optimization requirements
- Index usage rules

### 4. Transaction Handling
- Transaction boundaries
- Isolation level

## Output Format

```markdown
---
inclusion: fileMatch
fileMatchPattern: "**/db/**/*.py,**/models/**/*.py"
---

# Database Operations Standards

## Database Configuration

### Connection Pool

| Parameter | Value | Description |
|-----------|-------|-------------|
| Max connections | 10 | Adjust based on server config |
| Min connections | 2 | Idle connections to maintain |
| Connection timeout | 5s | Timeout for acquiring connection |
| Query timeout | 30s | Timeout for single query |

## Query Standards

### Basic Principles

1. **Only query needed fields**
2. **Use parameterized queries**
3. **Avoid N+1 queries**

### Paginated Query

```python
def get_users_paginated(page: int, limit: int):
    offset = (page - 1) * limit
    return db.query(User)\
        .order_by(User.created_at.desc())\
        .offset(offset)\
        .limit(limit)\
        .all()
```

### Batch Operations

```python
# ✅ Correct: batch insert
db.bulk_insert_mappings(User, user_data_list)

# ❌ Wrong: loop insert
for data in user_data_list:
    db.add(User(**data))
```

## Transaction Handling

### Use Context Manager

```python
async with db.transaction():
    await db.execute(...)
    await db.execute(...)
```

## Index Usage

### Must Index Scenarios

- Primary key (automatic)
- Foreign keys
- Fields frequently used in WHERE
- Fields frequently used in ORDER BY

### Index Naming

```sql
CREATE INDEX idx_users_email ON users(email);
```

## Error Handling

```python
from sqlalchemy.exc import IntegrityError

try:
    db.add(user)
    db.commit()
except IntegrityError:
    db.rollback()
    raise DuplicateError("User already exists")
```
```

## Usage Example

```
/generate-db-standards

We use PostgreSQL + SQLAlchemy, need database operations standards
```
