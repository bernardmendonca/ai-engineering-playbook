# Code Review Prompts

> Prompts for AI-assisted code review — security, quality, and performance focus.

## Security Review

```
Review this code for security issues. Focus on:
- Input validation (are all user inputs validated before use?)
- SQL/command injection (any string concatenation with user input?)
- Authentication/authorization (are checks in place and correct?)
- Secrets (any hardcoded credentials, keys, or tokens?)
- Error exposure (do errors leak internal details to users?)
- CORS/CSP (are headers appropriate for this endpoint?)

For each issue found:
- Severity (Critical/High/Medium/Low)
- Location (file:line)
- What's wrong
- How to fix (with code example)
```

## Quality Review

```
Review this code for quality issues. Focus on:
- Error handling (are errors caught, logged, and handled appropriately?)
- Edge cases (what inputs would cause unexpected behavior?)
- Naming (are variables/functions named clearly?)
- Complexity (any functions doing too much? Deep nesting?)
- DRY violations (repeated logic that should be extracted?)
- Type safety (any `any` types, unchecked casts, or assertions?)

Rate overall quality 1-5 and explain.
List issues by priority (fix now vs. consider later).
```

## Performance Review

```
Review this code for performance concerns:
- N+1 queries (database calls inside loops?)
- Unnecessary allocations (objects created but not needed?)
- Missing indexes (queries on unindexed fields?)
- Blocking operations (sync I/O in async context?)
- Memory leaks (event listeners, subscriptions not cleaned up?)
- Caching opportunities (repeated expensive computations?)

Only flag issues that matter at our scale ([describe scale — e.g., "10K requests/minute"]).
Don't flag micro-optimizations that won't make a measurable difference.
```

## PR Summary

```
Summarize this pull request diff for a reviewer. Include:
1. One-sentence summary of what changed
2. List of files changed, grouped by purpose
3. Key design decisions made in this PR
4. Potential risks or areas requiring careful review
5. Suggested review order (which files to read first)

Format as a PR description that helps a reviewer understand the change quickly.
```

---

## Tips for Review Prompts

- Specify severity levels to avoid noise (not everything is critical)
- Include your scale context (what's a performance issue depends on traffic)
- Ask for fixes alongside findings (actionable > informational)
- Use as first pass before human review, not replacement
