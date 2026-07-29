# Project Instructions

> Configuring AI tools at the project level — the highest-leverage context engineering activity.

## What Project Instructions Are

Project instruction files are static context that AI tools read at the start of every interaction. They tell the AI: "Here's how this project works. Follow these conventions."

Every major AI coding tool supports some form of this:

| Tool | File/mechanism | Format |
|------|---------------|--------|
| Claude Code | `CLAUDE.md` in project root | Markdown |
| Kiro | `.kiro/steering/*.md` files | Markdown with front-matter |
| Cursor | `.cursorrules` in project root | Markdown/text |
| GitHub Copilot | `.github/copilot-instructions.md` | Markdown |
| Aider | `.aider.conf.yml` + conventions file | YAML + Markdown |
| Windsurf | `.windsurfrules` | Markdown/text |
| Cline | Custom instructions in settings | Text |

---

## What to Include

### The Essential Template

Every project instructions file should cover these areas:

```markdown
# [Project Name]

## Overview
[One paragraph: what this project does, who uses it, what it's built with]

## Tech Stack
[Languages, frameworks, key libraries, infrastructure]

## Conventions
[Naming, patterns, error handling, file structure rules]

## File Structure
[Map of important directories and what goes where]

## How to Build and Test
[Commands: build, test, lint, run locally]

## Security Rules
[What never to do: no secrets in code, no PII logging, etc.]

## Don'ts
[Common mistakes to avoid, anti-patterns for this project]
```

### What Makes Instructions Effective

| Principle | Example |
|-----------|---------|
| **Specific over vague** | "Use `AppError` from `src/errors/`" not "handle errors properly" |
| **Reference existing code** | "Follow the pattern in `UserService.ts`" gives AI a concrete example |
| **Include commands** | AI agents need to know how to build, test, and lint |
| **State what NOT to do** | Prevents over-engineering: "Don't add interfaces for single implementations" |
| **Keep it under 100 lines** | Too long dilutes the important signals |

---

## Tool-Specific Guidance

### CLAUDE.md (Claude Code / Claude)

**Loaded:** Automatically when Claude Code starts in a directory with CLAUDE.md.

**Power features:**
- Supports nested CLAUDE.md files (subdirectory-specific instructions)
- Can reference other files: "See architecture in `docs/ARCHITECTURE.md`"
- Persistent across conversations in the same project
- Supports memory files for learned preferences

**Best for:** CLI-based agent workflows, complex multi-file tasks.

For a full copy-paste example: see [Examples: Java/Spring Boot CLAUDE.md](../examples/project-instructions/).
- Auth validated via JWT — never accept unsigned tokens

---

### Kiro Steering Files (.kiro/steering/)

**Loaded:** Based on inclusion mode (always, file-match, or manual).

**Power features:**
- Multiple files with different triggers (conditional inclusion)
- `fileMatchPattern` — steering activates only when relevant files are in context
- `#[[file:relative_path]]` — includes other files by reference
- Supports front-matter for configuration

**Best for:** Conditional context (different rules for different parts of the codebase), referencing external specs.

```markdown
---
inclusion: fileMatch
fileMatchPattern: "src/api/**"
---

# API Development Standards

When working on API files:

## Endpoint Pattern
- Controller validates input (Zod schema)
- Service contains business logic
- Repository handles data access
- Never put business logic in controllers

## Response Format
All responses follow: #[[file:docs/api-response-format.md]]

## Error Handling
Use AppError class. See pattern in: src/api/users/handler.ts
```

```markdown
---
inclusion: auto
---

# Always-Active Standards

## Git Commits
- Conventional commits: feat:, fix:, refactor:, docs:, test:
- Imperative mood in commit messages
- Reference ticket: "feat: add pagination (PROJ-123)"

## Code Quality
- No `any` types
- No `// @ts-ignore` without explanation
- No console.log in committed code (use logger)
```

---

### .cursorrules (Cursor)

**Loaded:** When Cursor opens a project with `.cursorrules` in the root.

**Best for:** IDE-native developers who want codebase-wide AI behavior tuning.

For copy-paste examples: see [Examples: React .cursorrules](../examples/project-instructions/).

---

### .github/copilot-instructions.md (GitHub Copilot)

**Loaded:** By Copilot when working in the repository (Enterprise/Business tiers).

**Best for:** Organizations standardized on GitHub ecosystem.

For copy-paste examples: see [Examples: Python/FastAPI copilot-instructions](../examples/project-instructions/).

---

## Maintaining Project Instructions

### When to Update

| Trigger | Action |
|---------|--------|
| New framework/library adopted | Add to stack, add conventions |
| Architecture change | Update file structure, patterns |
| Bug caused by AI following old patterns | Update instructions with correct pattern |
| New team member joins and AI gives wrong output | Whatever they had to correct → add to instructions |
| Quarterly review | Check for drift, remove stale content |

### Who Updates

- **Any developer** can PR a change to project instructions
- **Tech lead** reviews and approves (same as architecture decisions)
- **AI can help maintain** — ask it to suggest updates based on recent code changes

### Signs Your Instructions Need Updating

- Developers frequently override AI suggestions with the same correction
- New hires get different AI output than experienced devs (missing context)
- AI-generated PRs consistently need the same type of fix
- Instructions reference patterns that no longer exist in the code

---

## Getting Started (30 minutes)

1. Create the appropriate file for your tool (CLAUDE.md, .cursorrules, etc.)
2. Write 3 sections: Stack, Conventions, Don'ts
3. Include your build/test commands
4. Add one "Security" rule (even just "no secrets in code")
5. Commit to your repository
6. Tell your team it exists

That's it. You'll immediately notice more consistent AI output. Refine over weeks as you see what the AI gets wrong without guidance.

---

## Next

- Extending behavior with hooks and skills → [Skills and Hooks](./skills-and-hooks.md)
- Connecting to live knowledge → [Knowledge Architecture](./knowledge-architecture.md)
- Scaling instructions across an org → [Org-Wide Strategy](./org-wide-strategy.md)
