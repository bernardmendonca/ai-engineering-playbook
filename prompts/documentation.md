# Documentation Prompts

> Prompts for generating API docs, READMEs, ADRs, and inline documentation.

## API Documentation

```
Generate API documentation for [endpoint/module]:
- Format: [OpenAPI/Markdown/JSDoc]
- Include: parameters, return types, error responses, examples
- Audience: [internal developers / external API consumers]
- Tone: [technical reference / tutorial-style]

For each endpoint include:
- Description of what it does (one sentence)
- Request format with example
- Response format with example (success + error)
- Authentication requirements
- Rate limiting (if applicable)
```

## README Generation

```
Generate a README for [project/module] that includes:
1. One-paragraph description of what this does and why it exists
2. Quick start (how to run locally in <5 steps)
3. Key architecture decisions (brief)
4. Development workflow (how to contribute)
5. Testing (how to run tests)
6. Deployment (how this gets to production)

Keep it concise. Developers should get productive within 5 minutes of reading.
Don't include obvious things (like "install Node.js" for a Node project).
```

## Architecture Decision Record

```
Write an ADR for the following decision:

Title: [short descriptive title]
Context: [what situation prompted this decision]
Decision: [what we decided to do]
Options considered:
- Option A: [description] — pros: [X], cons: [Y]
- Option B: [description] — pros: [X], cons: [Y]
- Option C (chosen): [description] — pros: [X], cons: [Y]
Consequences: [what changes as a result]
Status: [Accepted/Proposed/Superseded]

Follow the format of ADRs in [our ADR directory if exists].
Be honest about tradeoffs — don't oversell the chosen option.
```

## Inline Documentation

```
Add documentation to [file/function] following these rules:
- Document "why", not "what" (the code shows what)
- Add JSDoc/docstring to public functions (params, returns, throws)
- Add brief comments for non-obvious logic only
- Don't comment obvious code (no "// increment counter")
- Include @example for complex functions
- Note any assumptions or prerequisites
```

---

## Tips for Documentation Prompts

- Specify the audience (internal vs. external changes tone dramatically)
- Ask for examples — docs without examples are incomplete
- "Why" is more valuable than "what" for inline documentation
- Request conciseness — verbose docs don't get read
