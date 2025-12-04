---
inclusion: manual
---

# Generate Performance Optimization Guide Steering

Please help me generate a performance optimization guide file.

> **Important**: Detect the user's project language and tech stack. Generate performance optimization examples using the appropriate ORM, caching libraries, and async patterns for that language (Python/SQLAlchemy, TypeScript/Prisma, Go/GORM, etc.).

## Required Information

Please generate performance guide based on the following questions (ask me if not provided):

### 1. Application Type
- Web app / API / background service?
- Main performance bottlenecks?

### 2. Performance Metrics
- Response time requirements?
- Throughput requirements?

### 3. Tech Stack
- What database?
- Any caching?
- Any async processing?

## Output Format

```markdown
---
inclusion: always
---

# Performance Optimization Guide

## Performance Goals

| Metric | Target | Notes |
|--------|--------|-------|
| API Response Time | < 200ms | P95 |
| Page Load Time | < 3s | First contentful paint |
| Database Query | < 100ms | Single query |
| Memory Usage | < 512MB | Per process |

## Database Optimization

### Query Optimization

```python
# ✅ Correct: only query needed fields
db.query(User.id, User.name).filter(...)

# ❌ Wrong: SELECT *
db.query(User).filter(...)

# ✅ Correct: use index
db.query(User).filter(User.email == email)  # email is indexed

# ❌ Wrong: function invalidates index
db.query(User).filter(func.lower(User.email) == email.lower())
```

### Avoid N+1 Queries

```python
# ❌ N+1 problem
users = db.query(User).all()
for user in users:
    print(user.orders)  # queries on each iteration

# ✅ Use joinedload
users = db.query(User).options(joinedload(User.orders)).all()
```

### Paginated Queries

```python
# ✅ Use LIMIT + OFFSET
def get_users(page: int, limit: int = 20):
    offset = (page - 1) * limit
    return db.query(User).offset(offset).limit(limit).all()
```

## Caching Strategy

### Cache Layers

| Layer | Tool | Purpose | TTL |
|-------|------|---------|-----|
| Local cache | LRU Cache | Hot data | 5 minutes |
| Distributed cache | Redis | Shared data | 1 hour |
| CDN | CloudFlare | Static assets | 1 day |

### Cache Example

```python
from functools import lru_cache

@lru_cache(maxsize=100)
def get_config(key: str) -> str:
    return db.query(Config).filter(Config.key == key).first()

# Redis cache
async def get_user_cached(user_id: int):
    cache_key = f"user:{user_id}"
    cached = await redis.get(cache_key)
    if cached:
        return json.loads(cached)
    
    user = await db.get(User, user_id)
    await redis.setex(cache_key, 3600, json.dumps(user.dict()))
    return user
```

## Async Processing

### Async Long-Running Operations

```python
# ❌ Sync processing: blocks request
@app.post("/orders")
def create_order(data: OrderCreate):
    order = create_order_in_db(data)
    send_email(order)  # Blocking!
    return order

# ✅ Async processing: fast response
@app.post("/orders")
async def create_order(data: OrderCreate):
    order = await create_order_in_db(data)
    background_tasks.add_task(send_email, order)  # Background execution
    return order
```

## Performance Monitoring

### Slow Query Logging

```python
SLOW_QUERY_THRESHOLD = 1.0  # seconds

if query_time > SLOW_QUERY_THRESHOLD:
    logger.warning(f"Slow query: {query}, duration: {query_time:.2f}s")
```

### Performance Metrics

```python
# Record API response time
@app.middleware("http")
async def add_timing(request, call_next):
    start = time.time()
    response = await call_next(request)
    duration = time.time() - start
    response.headers["X-Response-Time"] = f"{duration:.3f}s"
    return response
```

## Checklist

- [ ] Database queries use indexes
- [ ] Avoid N+1 queries
- [ ] Hot data uses caching
- [ ] Long-running operations are async
- [ ] Large datasets are paginated
- [ ] Monitor slow queries and slow endpoints
```

## Usage Example

```
/generate-performance

We are a Python web application, need performance optimization guide
```
