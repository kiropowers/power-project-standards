---
inclusion: manual
---

# Generate API Design Standards Steering

Please help me generate an API design standards file.

> **Important**: Detect the user's project language and framework (FastAPI, Express, NestJS, Gin, Spring Boot, etc.) and generate examples accordingly. The API design principles are universal, but code examples should match the user's tech stack.

## Required Information

Please generate API standards based on the following questions (ask me or analyze existing APIs if not provided):

### 1. API Style
- RESTful / GraphQL / RPC?
- Versioning approach?

### 2. Request Standards
- URL naming rules
- Request parameter format
- Authentication method

### 3. Response Standards
- Response format
- Status code usage
- Error handling

### 4. Other Conventions
- Pagination approach
- Filtering/sorting
- Rate limiting strategy

## Output Format

```markdown
---
inclusion: fileMatch
fileMatchPattern: "src/api/**/*.py"
---

# API Design Standards

## Basic Principles

- RESTful style
- Resource-oriented
- Stateless

## URL Design

### Naming Rules

| Rule | Example |
|------|---------|
| Use plural nouns | `/users`, `/orders` |
| Use lowercase | `/user-profiles` |
| Use hyphens | `/order-items` |
| Nested resources | `/users/{id}/orders` |

### HTTP Methods

| Method | Purpose | Example |
|--------|---------|---------|
| GET | Retrieve resource | `GET /users` |
| POST | Create resource | `POST /users` |
| PUT | Full update | `PUT /users/{id}` |
| PATCH | Partial update | `PATCH /users/{id}` |
| DELETE | Delete resource | `DELETE /users/{id}` |

### Versioning

- URL path versioning: `/api/v1/users`
- Major version change indicates breaking API changes

## Request Standards

### Request Headers

```
Content-Type: application/json
Authorization: Bearer {token}
X-Request-ID: {uuid}
```

### Request Body

```json
{
  "field1": "value1",
  "field2": "value2"
}
```

### Query Parameters

| Parameter | Purpose | Example |
|-----------|---------|---------|
| page | Page number | `?page=1` |
| limit | Items per page | `?limit=20` |
| sort | Sorting | `?sort=-created_at` |
| filter | Filtering | `?status=active` |

## Response Standards

### Success Response

```json
{
  "code": 0,
  "message": "success",
  "data": {
    // actual data
  }
}
```

### List Response

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "items": [...],
    "total": 100,
    "page": 1,
    "limit": 20
  }
}
```

### Error Response

```json
{
  "code": 40001,
  "message": "Invalid parameter",
  "error": {
    "field": "email",
    "reason": "Invalid email format"
  }
}
```

## Status Codes

| Code | Meaning | Use Case |
|------|---------|----------|
| 200 | Success | GET, PUT, PATCH, DELETE success |
| 201 | Created | POST creation success |
| 204 | No Content | DELETE success, no body |
| 400 | Bad Request | Parameter validation failed |
| 401 | Unauthorized | Missing or invalid auth |
| 403 | Forbidden | No permission to access |
| 404 | Not Found | Resource doesn't exist |
| 409 | Conflict | Resource state conflict |
| 422 | Unprocessable | Business logic error |
| 429 | Too Many Requests | Rate limit triggered |
| 500 | Server Error | Internal server error |

## Error Code Design

| Range | Type |
|-------|------|
| 10000-19999 | System errors |
| 20000-29999 | Auth errors |
| 30000-39999 | Validation errors |
| 40000-49999 | Business logic errors |

## Authentication

### Bearer Token

```
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

### Token Refresh

- Access Token validity: 2 hours
- Refresh Token validity: 7 days
- Refresh endpoint: `POST /auth/refresh`

## Rate Limiting

- Default limit: 100 requests/minute
- Response headers include rate limit info:
  ```
  X-RateLimit-Limit: 100
  X-RateLimit-Remaining: 95
  X-RateLimit-Reset: 1640000000
  ```

## Example

### Create User

```http
POST /api/v1/users
Content-Type: application/json
Authorization: Bearer {token}

{
  "name": "John Doe",
  "email": "john@example.com"
}
```

Response:
```json
{
  "code": 0,
  "message": "success",
  "data": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "created_at": "2024-01-15T10:00:00Z"
  }
}
```
```

## Usage Example

```
/generate-api-standards

Please analyze #src/api/ directory and generate API design standards
```
