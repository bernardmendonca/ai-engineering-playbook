# Refactoring Prompts

> Prompts for code improvement, migrations, and pattern changes.

## Code Improvement

### Extract and Simplify

```
Refactor [function/class] to improve readability:
- Extract [specific logic] into a separate, well-named function
- Use early returns for error/guard conditions
- Reduce nesting depth (max 2 levels)
- Keep the same public interface (don't change callers)
- Don't change behavior — this is a pure refactoring

Verify: all existing tests should still pass without modification.
```

### Apply Design Pattern

```
Refactor [code] to use [pattern — e.g., repository pattern, strategy pattern]:
- Current structure: [describe what exists]
- Desired structure: [describe target]
- Reason for change: [why this pattern fits]

Requirements:
- Existing tests must pass (update test implementation, not assertions)
- No behavior change from the caller's perspective
- Follow naming conventions in [similar pattern in our codebase]
```

---

## Migration

### Framework/Library Migration

```
Migrate [file/module] from [old library] to [new library]:
- Old usage: [describe current pattern]
- New equivalent: [describe desired pattern if known, or "find equivalent"]
- Preserve all existing behavior
- Update imports
- Update any type definitions
- Run tests to verify

Our new library conventions: [any project-specific patterns for the new library]
```

### Language Version Upgrade

```
Update [file] to use [language version] features where appropriate:
- Replace [old pattern] with [new pattern] (e.g., callbacks → async/await)
- Use [new feature] where it improves readability (e.g., optional chaining)
- Do NOT change just for the sake of change — only where it genuinely improves code

Don't touch:
- Code that's already clear and readable
- Performance-critical sections (unless the new pattern is provably better)
- Public API signatures (unless we're doing a major version bump)
```

### Rename/Move Concept

```
Rename the concept "[old name]" to "[new name]" across the codebase:
- Files: rename files containing the old name
- Types/interfaces: update type names and references
- Variables and functions: update all usages
- Tests: update test descriptions and assertions
- Documentation: update comments, docs, and READMEs
- Database: [create migration / leave DB column names as-is]
- API: [update endpoint paths / keep for backward compatibility]

Verify: all tests pass after rename.
```

---

## Decomposition

### Split Large File

```
This file ([filename]) is [X] lines and does too much. Split it into:
- [suggested module 1]: [responsibility]
- [suggested module 2]: [responsibility]
- [suggested module 3]: [responsibility]

Requirements:
- No circular dependencies between new modules
- Each module has a clear, single responsibility
- Update all imports in files that reference the original
- Index file re-exports if needed for backward compatibility
- Existing tests should pass (split test file similarly if needed)
```

---

## Tips for Refactoring Prompts

- Always specify "don't change behavior"
- Reference existing tests as the verification mechanism
- Be explicit about what NOT to change (callers, APIs, etc.)
- For large refactors, break into steps and verify after each
- Include naming conventions you want followed
- Specify whether to update tests or keep them as behavioral verification
