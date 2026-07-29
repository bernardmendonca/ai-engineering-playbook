# Code Generation Prompts

> Prompts for generating features, endpoints, and data models — adapt to your stack and conventions.

## Feature Implementation

### Implement a New Endpoint

```
Implement a [HTTP method] endpoint at [path] that:
- Accepts: [describe input/body schema]
- Validates: [list validation rules]
- Does: [describe business logic]
- Returns: [describe response format]
- Error cases: [list expected errors and status codes]

Follow the pattern established in [existing similar file].
Use our existing [middleware/framework conventions].
Include input validation and proper error responses.
```

### Add a New Feature Following Existing Patterns

```
I need to add [feature] to this project. Here's what it should do:
[describe the feature behavior]

Follow the exact patterns used in [similar existing feature].
Match the file structure, naming conventions, and error handling approach.
Include:
- Implementation
- Input validation
- Error handling
- Unit tests following [test file] patterns
```

### Generate a Data Model

```
Create a data model for [entity] with these fields:
- [field]: [type] — [description/constraints]
- [field]: [type] — [description/constraints]
...

Include:
- Type/interface definition
- Validation logic (using [validation library])
- Database migration (using [ORM/migration tool])
- Factory/fixture for tests
- Follow naming conventions in [existing model file]
```

---

## API Design

### Generate CRUD Endpoints

```
Generate a complete CRUD implementation for [resource]:
- POST /[resource] — Create (validate [fields])
- GET /[resource] — List with pagination (page, limit params)
- GET /[resource]/:id — Get single
- PUT /[resource]/:id — Update (partial update supported)
- DELETE /[resource]/:id — Soft delete

Use [framework] with [ORM].
Follow patterns in [existing resource implementation].
Include: input validation, error handling, proper HTTP status codes.
Do NOT include: authentication (handled by middleware already).
```

### Design an API Contract

```
Design a REST API contract for [feature]. Define:
- Endpoints (paths, methods)
- Request schemas (with examples)
- Response schemas (with examples)
- Error responses (format consistent with our existing APIs)
- Pagination approach (match our existing pattern: [describe])

Output as: [OpenAPI spec / TypeScript types / markdown table]
Our API conventions: [describe any non-obvious conventions]
```

---

## Utility Functions

### Generate Helper Function

```
Write a utility function that:
- Purpose: [what it does]
- Input: [parameters with types]
- Output: [return type and description]
- Edge cases: [list known edge cases to handle]
- Error handling: [throw vs. return error vs. Result type]

Make it pure (no side effects) and well-typed.
Add JSDoc/docstring with examples.
```

---

## Tips for Code Generation Prompts

- Always reference existing patterns in your codebase
- Include what NOT to do (prevents over-engineering)
- Specify error handling approach explicitly
- Ask for tests alongside implementation
- Include accessibility requirements for UI code
- Mention security considerations for user-facing code
