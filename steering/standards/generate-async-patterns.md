---
inclusion: manual
---

# Generate Async Programming Standards Steering

Please help me generate an async programming standards file.

> **Important**: Detect the user's project language and generate examples accordingly. Python uses asyncio, JavaScript/TypeScript uses Promises/async-await, Go uses goroutines/channels, Java uses CompletableFuture, etc. Adapt patterns to the language's async model.

## Required Information

Please generate async standards based on the following questions (ask me if not provided):

### 1. Async Framework
- What async framework? (asyncio / threading / multiprocessing)
- Using coroutines?

### 2. Concurrency Control
- Maximum concurrency?
- Timeout settings?

### 3. Error Handling
- How to handle async exceptions?
- Retry strategy?

## Output Format

```markdown
---
inclusion: fileMatch
fileMatchPattern: "**/*async*.py,**/tasks/**/*.py"
---

# Async Programming Standards

## Basic Principles

1. **Avoid Blocking** - Don't call sync blocking operations in async functions
2. **Control Concurrency** - Use semaphores to limit concurrency
3. **Proper Cancellation** - Support task cancellation and timeouts
4. **Exception Handling** - Catch and handle async exceptions

## async/await Usage

### Basic Syntax

```python
import asyncio

# ✅ Correct: async function
async def fetch_data(url: str) -> dict:
    async with aiohttp.ClientSession() as session:
        async with session.get(url) as response:
            return await response.json()

# ❌ Wrong: using sync blocking in async function
async def bad_fetch(url: str):
    response = requests.get(url)  # Blocking!
    return response.json()
```

### Concurrent Execution

```python
# ✅ Correct: concurrent execution of multiple tasks
async def fetch_all(urls: list[str]):
    tasks = [fetch_data(url) for url in urls]
    results = await asyncio.gather(*tasks)
    return results

# ❌ Wrong: sequential execution
async def fetch_all_slow(urls: list[str]):
    results = []
    for url in urls:
        result = await fetch_data(url)  # waiting one by one
        results.append(result)
    return results
```

## Concurrency Control

### Using Semaphore to Limit Concurrency

```python
semaphore = asyncio.Semaphore(10)  # max 10 concurrent

async def limited_fetch(url: str):
    async with semaphore:
        return await fetch_data(url)
```

### Timeout Control

```python
async def fetch_with_timeout(url: str, timeout: float = 30):
    try:
        return await asyncio.wait_for(
            fetch_data(url),
            timeout=timeout
        )
    except asyncio.TimeoutError:
        logger.warning(f"Request timeout: {url}")
        return None
```

## Exception Handling

```python
async def safe_fetch(url: str):
    try:
        return await fetch_data(url)
    except aiohttp.ClientError as e:
        logger.error(f"Request failed: {url}, {e}")
        return None
    except asyncio.CancelledError:
        logger.warning(f"Task cancelled: {url}")
        raise  # re-raise cancellation
```

## Task Cancellation

```python
async def cancellable_task():
    try:
        while True:
            await do_work()
            await asyncio.sleep(1)
    except asyncio.CancelledError:
        # cleanup resources
        await cleanup()
        raise
```

## Checklist

- [ ] No sync blocking calls in async functions
- [ ] Use gather for concurrent independent tasks
- [ ] Use semaphore to control concurrency
- [ ] Set reasonable timeouts
- [ ] Properly handle CancelledError
```

## Usage Example

```
/generate-async-patterns

We use Python asyncio, need async programming standards
```
