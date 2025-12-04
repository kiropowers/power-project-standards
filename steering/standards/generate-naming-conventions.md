---
inclusion: manual
---

# Generate Naming Conventions Steering

Please help me generate a naming conventions file.

> **Important**: Analyze the user's project to detect the programming language (Python, TypeScript, JavaScript, Go, Java, etc.) and generate examples in that language. The examples below are for reference only - adapt naming styles to match the language's conventions.

## Required Information

Please generate naming conventions based on the following questions (ask me or analyze existing code if not provided):

### 1. Programming Language
- What main language?
- Multiple languages?

### 2. Naming Style Preferences
- Variable naming style?
- Function/method naming style?
- Class naming style?

### 3. Special Conventions
- Any special prefixes/suffixes?
- Any prohibited names?

## Output Format

```markdown
---
inclusion: always
---

# Naming Conventions

## Basic Principles

1. **Clarity over brevity** - Names should clearly express intent
2. **Consistency** - Use unified naming style across the project
3. **Searchable** - Avoid single-letter variables (except loop variables)
4. **Avoid abbreviations** - Unless widely recognized

## Naming Styles

| Style | Format | Example | Usage |
|-------|--------|---------|-------|
| snake_case | lowercase+underscore | `user_name` | Python variables, functions |
| camelCase | lowerCamelCase | `userName` | JavaScript variables, functions |
| PascalCase | UpperCamelCase | `UserName` | Class names |
| UPPER_SNAKE_CASE | uppercase+underscore | `MAX_SIZE` | Constants |
| kebab-case | lowercase+hyphen | `user-name` | URLs, filenames |

## Variable Naming

### Basic Rules

```python
# ✅ Good naming
user_count = 10
is_active = True
has_permission = False
max_retry_count = 3

# ❌ Bad naming
n = 10           # Too short, unclear meaning
userCnt = 10     # Unnecessary abbreviation
flag = True      # Too vague
temp = 3         # Unclear purpose
```

### Boolean Variables

Use `is_`, `has_`, `can_`, `should_` prefixes:

```python
is_valid = True
has_children = False
can_edit = True
should_retry = False
```

### Collection Variables

Use plural form or collection type suffix:

```python
users = []           # Plural
user_list = []       # _list suffix
user_ids = set()     # Plural
user_map = {}        # _map suffix
user_dict = {}       # _dict suffix
```

### Numeric Variables

Indicate unit or purpose:

```python
timeout_seconds = 30
max_file_size_mb = 10
retry_count = 3
page_index = 0       # 0-based
page_number = 1      # 1-based
```

## Function/Method Naming

### Basic Rules

Start with verb, describe the function's behavior:

```python
# ✅ Good naming
def get_user_by_id(user_id):
def create_order(order_data):
def validate_email(email):
def send_notification(user, message):

# ❌ Bad naming
def user(id):        # Unclear if get or create
def process(data):   # Too vague
def do_stuff():      # Meaningless
```

### Common Verbs

| Verb | Purpose | Example |
|------|---------|---------|
| get | Retrieve data | `get_user()` |
| set | Set data | `set_config()` |
| create | Create new object | `create_order()` |
| update | Update object | `update_user()` |
| delete | Delete object | `delete_order()` |
| find | Find (may return empty) | `find_user_by_email()` |
| fetch | Fetch from remote | `fetch_data()` |
| load | Load data | `load_config()` |
| save | Save data | `save_to_file()` |
| validate | Validate | `validate_input()` |
| parse | Parse | `parse_json()` |
| format | Format | `format_date()` |
| convert | Convert | `convert_to_dict()` |
| calculate | Calculate | `calculate_total()` |
| check | Check (returns boolean) | `check_permission()` |
| is/has/can | Judge (returns boolean) | `is_valid()` |

### Private Methods

Use single underscore prefix:

```python
class UserService:
    def get_user(self, user_id):
        """Public method"""
        return self._fetch_from_db(user_id)
    
    def _fetch_from_db(self, user_id):
        """Private method"""
        pass
```

## Class Naming

### Basic Rules

Use PascalCase, nouns or noun phrases:

```python
# ✅ Good naming
class User:
class OrderService:
class DatabaseConnection:
class HttpClient:

# ❌ Bad naming
class user:          # Should use PascalCase
class DoSomething:   # Class name shouldn't be verb
class Data:          # Too vague
```

### Special Types

| Type | Naming Rule | Example |
|------|-------------|---------|
| Regular class | PascalCase | `User`, `Order` |
| Abstract class | Base + Name | `BaseCrawler`, `BaseService` |
| Interface | I + Name or Name + Interface | `IRepository`, `CrawlerInterface` |
| Exception | Name + Error/Exception | `ValidationError`, `NotFoundError` |
| Mixin | Name + Mixin | `LoggingMixin` |

## File Naming

### Python Files

```
# Module files: snake_case
user_service.py
database_connection.py

# Test files: test_ prefix
test_user_service.py

# Config files
settings.py
config.py
```

### Directory Naming

```
# Use snake_case
src/
├── user_management/
├── order_processing/
└── utils/
```

## Constant Naming

Use UPPER_SNAKE_CASE:

```python
MAX_RETRY_COUNT = 3
DEFAULT_TIMEOUT = 30
API_BASE_URL = "https://api.example.com"
DATABASE_NAME = "mydb"
```

## Prohibited Names

| Prohibited | Reason | Alternative |
|------------|--------|-------------|
| `l`, `O`, `I` | Easily confused with numbers | Use full words |
| `data`, `info` | Too vague | Use specific names |
| `temp`, `tmp` | Unclear purpose | Use descriptive names |
| `foo`, `bar` | Meaningless | Use actual names |

## Abbreviation Rules

### Allowed Abbreviations

| Abbreviation | Full Form |
|--------------|-----------|
| id | identifier |
| url | uniform resource locator |
| api | application programming interface |
| db | database |
| config | configuration |
| max/min | maximum/minimum |
| num | number |
| msg | message |
| err | error |
| req/res | request/response |

### Abbreviation Usage Rules

```python
# Treat abbreviation as a word
user_id = 1        # not userId
http_url = "..."   # not httpURL
api_key = "..."    # not APIKey

# Abbreviations in class names
class HttpClient:  # not HTTPClient
class ApiService:  # not APIService
```
```

## Usage Example

```
/generate-naming-conventions

We use Python, need unified naming conventions
```
