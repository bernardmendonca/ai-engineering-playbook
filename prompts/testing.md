# Testing Prompts

> Prompts for generating unit tests, edge cases, and integration tests.

## Unit Test Generation

### Generate Tests for Existing Function

```
Write unit tests for [function/file]. Requirements:
- Test framework: [Jest/pytest/JUnit/etc.]
- Follow the patterns in [existing test file]
- Cover: happy path, edge cases, error cases
- Use descriptive test names that explain the expected behavior
- Mock [list what to mock] using [mocking library]
- Do NOT test implementation details — test behavior

Focus on:
- What happens with valid input (multiple cases)
- What happens with invalid input (null, empty, wrong type)
- Boundary conditions ([specific boundaries])
- Error handling paths
```

### Generate Edge Case Tests

```
I have tests for [function] covering the happy path. Add tests for:
- Null/undefined inputs
- Empty collections/strings
- Boundary values (0, -1, MAX_INT, empty string)
- Unicode and special characters
- Concurrent access (if applicable)
- Very large inputs (performance boundary)
- Invalid types (if dynamically typed)

Follow existing test style in [test file].
Each test should have a clear, descriptive name.
```

### Generate Test Data Factory

```
Create a test data factory for [entity] that:
- Generates valid default instances
- Allows overriding specific fields
- Supports creating related entities
- Produces realistic but deterministic data

Use [factory library or pattern].
Follow the factory pattern in [existing factory file].
Include variations: [list common test scenarios]
```

---

## Integration Tests

### API Endpoint Integration Test

```
Write integration tests for [endpoint]:
- Test framework: [supertest/requests/etc.]
- Database: [in-memory/test DB/fixtures]
- Cover:
  - Valid request returns correct response and status
  - Invalid input returns 400 with error details
  - Unauthorized request returns 401
  - Not found returns 404
  - Duplicate/conflict returns 409 (if applicable)
- Verify database state after mutations
- Clean up test data after each test

Follow patterns in [existing integration test file].
```

---

## Test Improvement

### Strengthen Existing Tests

```
Review these existing tests for [module]. They pass but may be:
- Testing implementation details instead of behavior
- Missing error cases
- Not testing boundary conditions
- Using brittle assertions

Suggest improvements. For each suggestion:
- What's wrong with the current test
- Why it matters (what could slip through)
- The improved test code
```

---

## Tips for Testing Prompts

- Always specify the test framework and style
- Reference an existing test file for conventions
- Ask for behavioral tests, explicitly exclude implementation testing
- Include specific edge cases you know about
- Request descriptive test names (not `test1`, `test2`)
- For integration tests, specify setup/teardown requirements
