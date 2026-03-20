# Claude Development Rules

This project uses AI-assisted development.
All generated code must follow the rules below.

---

# Architecture Rules

1. Follow **Clean Architecture**.
2. Domain layer must NOT depend on infrastructure.
3. Business logic must exist only in the **Usecase layer**.
4. HTTP handlers must be thin and contain no business logic.
5. Use DTO objects for API responses.
6. Follow the existing directory structure.
7. Do not introduce new frameworks or libraries without approval.

---

# API Design Rules

All APIs must follow **RESTful design**.

## API Version

All APIs must include a version prefix.

Examples:

/api/v1/listings  
/api/v1/users

---

## Pagination

List APIs must support pagination.

Parameters:

limit  
cursor

Example:

GET /api/v1/listings?limit=20&cursor=abc123

Cursor pagination is preferred.

---

## Authentication

Authentication uses **JWT**.

Access Token:
- short lived

Refresh Token:
- long lived

Authorization header:

Authorization: Bearer <token>

---

## Response Format

All APIs must follow a consistent response structure.

### Success Response

```json
{
  "data": {},
  "meta": {}
}
````

### Error Response

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid request"
  }
}
```

---

# Testing Rules

1. All new features must include tests.
2. API logic must have **unit tests**.
3. Frontend must include **E2E tests**.
4. Tests must be placed in the `/test` directory.

---

# Code Generation Constraints

AI must NOT:

* change API contracts
* modify architecture rules
* introduce hidden dependencies
* bypass testing requirements

If uncertain, ask before generating code.


