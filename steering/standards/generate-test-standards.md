---
inclusion: manual
---

# Generate Testing Standards Steering

Please help me generate a testing standards file.

> **Important**: Detect the user's project language and recommend appropriate testing frameworks. Python uses pytest, JavaScript/TypeScript uses Jest/Vitest, Go uses testing package, Java uses JUnit, etc. Generate examples in the detected language.

## Required Information

Please generate testing standards based on the following questions (ask me if not provided):

### 1. Testing Framework
- What testing framework?
- Mock library?

### 2. Test Types
- Unit tests / Integration tests / E2E tests?

### 3. Coverage Requirements
- Minimum coverage?

### 4. Test Organization
- File structure
- Naming conventions

## Output Format

```markdown
---
inclusion: fileMatch
fileMatchPattern: "*_test.py,test_*.py,**/tests/**/*.py"
---

# Testing Standards

## Testing Framework

| Type | Framework |
|------|-----------|
| Unit tests | pytest |
| Mock | pytest-mock |
| Coverage | pytest-cov |

## Test Organization

### Directory Structure

```
tests/
├── unit/                  # Unit tests
├── integration/           # Integration tests
├── fixtures/              # Test data
└── conftest.py           # Shared fixtures
```

### File Naming

| Type | Naming Rule | Example |
|------|-------------|---------|
| Test file | test_{module}.py | `test_user_service.py` |
| Test class | Test{Class} | `TestUserService` |
| Test function | test_{scenario} | `test_create_user_success` |

## Test Structure

### AAA Pattern

```python
def test_create_user_success():
    # Arrange - prepare test data
    user_data = {"name": "John", "email": "test@example.com"}
    
    # Act - execute code under test
    result = user_service.create_user(user_data)
    
    # Assert - verify results
    assert result.name == "John"
```

## Fixtures

```python
@pytest.fixture
def test_user(db_session):
    user = User(name="Test User", email="test@example.com")
    db_session.add(user)
    db_session.commit()
    return user
```

## Mock Usage

```python
def test_send_email(mocker):
    mock_send = mocker.patch("services.email.send_email")
    mock_send.return_value = True
    
    result = notification_service.notify_user(user_id=1)
    
    mock_send.assert_called_once()
```

## Coverage Requirements

| Module | Minimum Coverage |
|--------|------------------|
| Core business logic | 80% |
| Utility functions | 70% |
| Overall | 70% |

## Parameterized Tests

```python
@pytest.mark.parametrize("input,expected", [
    ("valid@email.com", True),
    ("invalid-email", False),
])
def test_validate_email(input, expected):
    assert validate_email(input) == expected
```

## Running Tests

```bash
pytest                    # Run all tests
pytest -v                 # Verbose output
pytest --cov=src          # Coverage report
```
```

## Usage Example

```
/generate-test-standards

We use pytest, need to generate testing standards
```
