# Project Instructions

> Configuring AI tools at the project level — the highest-leverage context engineering activity.

> **Last verified:** 2026-10-30 · **Re-check by:** 2027-01-30

## What Project Instructions Are

Project instruction files are static context that AI tools read at the start of every interaction. They tell the AI: "Here's how this project works. Follow these conventions."

### Start with AGENTS.md

[`AGENTS.md`](https://agents.md) is a plain Markdown file in the repository root that gives any coding agent project-specific guidance. It began as a cross-vendor convention (OpenAI Codex, Cursor, Google, and others) and is now stewarded by the Linux Foundation's Agentic AI Foundation, alongside MCP. Most major agents read it natively.

> ✅ **My take:** Write one `AGENTS.md` as the source of truth, and add tool-specific files only as thin overlays for features a tool needs (conditional inclusion in Kiro, path-scoped rules in Cursor or Copilot). This keeps your context investment portable when you change or add tools, and avoids maintaining the same conventions in four files that drift apart.

Nested `AGENTS.md` files in subdirectories apply to the code beneath them, which is useful in monorepos.

### Tool-specific files

Every major AI coding tool also supports its own format:

| Tool | Reads `AGENTS.md`? | Native file/mechanism | Format |
|------|:------------------:|-----------------------|--------|
| Claude Code | No — import it | `CLAUDE.md` in project root. Add a line `@AGENTS.md` to import the shared file | Markdown |
| OpenAI Codex | ✅ | `AGENTS.md` is the native format | Markdown |
| GitHub Copilot | ✅ | `.github/copilot-instructions.md`, plus path-scoped `.github/instructions/*.instructions.md` | Markdown |
| Kiro | ✅ (workspace root or `~/.kiro/steering/`) | `.kiro/steering/*.md` files with inclusion modes | Markdown with front-matter |
| Cursor | ✅ | `.cursor/rules/*.mdc` (the older `.cursorrules` file is deprecated) | Markdown/MDC |
| Aider | Via config (`read:` in `.aider.conf.yml`) | `.aider.conf.yml` + conventions file | YAML + Markdown |
| Devin Desktop *(formerly Windsurf)* | ✅ (nested files apply to their directory) | Rules in `.devin/rules/*.md` or `.windsurf/rules/*.md`; legacy `.windsurfrules` still read | Markdown with trigger front-matter |
| Cline | ✅ | Rules in `.clinerules/` or `.cline/rules/` (also reads `.cursorrules` and `.windsurfrules`) | Markdown, optional `paths` front-matter |

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

**Loaded:** Automatically when Claude Code starts in a directory with CLAUDE.md. Claude Code does not read `AGENTS.md` on its own. If you keep shared conventions in `AGENTS.md`, make CLAUDE.md import it:

```markdown
@AGENTS.md

## Claude Code-specific notes
- (anything that only applies to Claude Code)
```

**Power features:**
- Supports nested CLAUDE.md files (subdirectory-specific instructions)
- Can reference other files: "See architecture in `docs/ARCHITECTURE.md`"
- Persistent across conversations in the same project
- Supports memory files for learned preferences

**Best for:** CLI-based agent workflows, complex multi-file tasks.

For a full copy-paste example: see [Examples: Java/Spring Boot CLAUDE.md](../examples/project-instructions/).

---

### Kiro Steering Files (.kiro/steering/)

**Loaded:** Based on the `inclusion` front-matter key:
- `always` (the default if omitted) — loaded into every interaction
- `fileMatch` — loaded when files matching `fileMatchPattern` are in context
- `manual` — loaded only when a developer references it with `#` in chat
- `auto` — loaded when the request matches the file's `description` (requires `name` and `description` keys)

Kiro also picks up an `AGENTS.md` in the workspace root or in `~/.kiro/steering/`.

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
inclusion: always
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

### Project Rules (Cursor)

**Loaded:** When Cursor opens a project with rule files in `.cursor/rules/*.mdc`. The older single-file `.cursorrules` still works but Cursor's own docs mark it deprecated — new projects should use the `.cursor/rules/` directory.

**Best for:** IDE-native developers who want codebase-wide AI behavior tuning.

For copy-paste examples: see [Examples: React Cursor rule](../examples/project-instructions/).

---

### .github/copilot-instructions.md (GitHub Copilot)

**Loaded:** By Copilot across supported clients (VS Code, Visual Studio, JetBrains, and more) and by the Copilot cloud agent — not gated to a specific paid tier, though enterprise policy controls may affect how it's enforced org-wide. Copilot also reads `AGENTS.md` and path-scoped `.github/instructions/*.instructions.md` files (with an `applyTo` glob in front-matter). Verify current client support in GitHub's docs, as this has broadened over time.

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

1. Create `AGENTS.md` in the repo root (and, if your team uses Claude Code, a CLAUDE.md containing `@AGENTS.md`)
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
