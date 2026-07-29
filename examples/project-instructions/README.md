# Example: Project Instructions Files

> Ready-to-copy example instruction files for different tech stacks. For guidance on how to write and maintain these, see [04 — Context Engineering: Project Instructions](../../04-context-engineering/project-instructions.md).

## What These Are

These are copy-paste starting points for different stacks. Pick the one closest to your project and customize.

For the full explanation of *why* these work, tool-specific loading behavior, maintenance guidance, and best practices, refer to the [Context Engineering section](../../04-context-engineering/project-instructions.md).

---

## Example 1: Node.js/TypeScript API (Express + Prisma)

**File:** `CLAUDE.md` (or adapt for `.cursorrules` / `.github/copilot-instructions.md`)

```markdown
# Project Instructions

## Overview
Node.js/TypeScript REST API using Express, Prisma ORM, and PostgreSQL.

## Conventions
- Use async/await (never callbacks or raw promises)
- Error handling: use AppError class from src/errors/AppError.ts
- All endpoint handlers follow: validate → execute → respond pattern
- Use zod for request validation (schemas in src/schemas/)
- Database queries go through repository classes (src/repositories/)
- Never use `any` type — prefer `unknown` with type narrowing

## File Structure
- src/routes/ — Express route definitions
- src/handlers/ — Request handler functions
- src/services/ — Business logic
- src/repositories/ — Database access
- src/schemas/ — Zod validation schemas
- src/errors/ — Error classes
- src/middleware/ — Express middleware
- tests/ — Test files mirror src/ structure

## Testing
- Framework: Jest with ts-jest
- Run: `npm test`
- Patterns: see tests/handlers/users.test.ts for reference
- Mock database using jest.mock on repository layer
- Never mock the service layer in handler tests

## Security Rules
- Never log PII (email, name, phone)
- Never return stack traces in API responses
- Always validate and sanitize input before use
- Use parameterized queries (Prisma handles this)

## Commands
- `npm run dev` — Start development server
- `npm test` — Run all tests
- `npm run lint` — ESLint
- `npm run build` — TypeScript compilation
- `npm run db:migrate` — Run Prisma migrations
```

---

## Example 2: React/TypeScript Frontend

**File:** `.cursorrules` (or adapt for `CLAUDE.md`)

```markdown
You are working on a TypeScript/React frontend application.

## Stack
React 18, TypeScript strict, Vite, TanStack Query, Zustand, Tailwind CSS, Vitest

## Conventions
- Functional components only (no class components)
- Custom hooks in src/hooks/ for reusable logic
- API calls go through src/api/ layer (never fetch directly in components)
- Components: PascalCase files, default export
- Hooks: camelCase files starting with `use`, named export
- Tests: co-located as ComponentName.test.tsx

## Patterns
- Data fetching: useQuery/useMutation from TanStack Query
- Client state: Zustand stores (src/stores/)
- Forms: React Hook Form + Zod resolver
- Styling: Tailwind utility classes, no inline styles

## Accessibility
- All interactive elements must be keyboard accessible
- Use semantic HTML (nav, main, article, section)
- Images require alt text
- Form inputs require associated labels

## Don't
- Don't use index.ts barrel files (causes circular imports)
- Don't put business logic in components (extract to hooks/services)
- Don't use @ts-ignore without comment
- Don't create God components (max 150 lines)
```

---

## Example 3: Java/Spring Boot Microservice

**File:** `CLAUDE.md` (or `.github/copilot-instructions.md`)

```markdown
# Project: Payment Service
Java 17 + Spring Boot 3.2. Handles PCI-scoped payment processing.

## Commands
- Build: `./gradlew build`
- Test: `./gradlew test`
- Run locally: `./gradlew bootRun`
- Lint: `./gradlew spotlessCheck`

## Conventions
- Records for DTOs, classes for entities
- Constructor injection only (no @Autowired on fields)
- Custom exceptions extend RuntimeException
- Validation: Jakarta Bean Validation on DTOs
- Mapping: MapStruct for entity ↔ DTO
- Lombok: @Builder and @Slf4j only (no @Data on entities)

## Testing
- JUnit 5 + Mockito for unit tests
- @SpringBootTest with Testcontainers for integration
- Test naming: shouldDoX_whenConditionY()

## Security (CRITICAL)
- NEVER log card numbers, CVV, or full account numbers
- NEVER return PCI-scoped data in error responses
- Always use parameterized queries (JPA handles this)
- Auth validated via JWT — never accept unsigned tokens

## Don'ts
- Don't use @Data on entities (breaks JPA proxies)
- Don't create interfaces for classes with single implementations
- Don't use field injection
```

---

## Example 4: Python/FastAPI Service

**File:** `.github/copilot-instructions.md` (or `CLAUDE.md`)

```markdown
## Stack
Python 3.12+, FastAPI, SQLAlchemy 2.0 (async), Alembic, pytest

## Conventions
- Type hints required on all function signatures
- Use `async def` for all route handlers
- Dependency injection via FastAPI Depends()
- Error responses use ProblemDetail (RFC 7807)
- Pydantic v2 models for request/response schemas

## File Structure
- app/routes/ — FastAPI routers
- app/services/ — Business logic
- app/models/ — SQLAlchemy models
- app/schemas/ — Pydantic schemas
- app/deps/ — Dependency injection functions
- tests/ — mirrors app/ structure

## Commands
- Run: `uvicorn app.main:app --reload`
- Test: `pytest`
- Lint: `ruff check .`
- Format: `ruff format .`
- Migrate: `alembic upgrade head`

## Don'ts
- Don't use sync database operations
- Don't put business logic in route handlers
- Don't expose internal IDs in URLs (use UUIDs)
```

---

## Adapting These Examples

1. Copy the example closest to your stack
2. Replace placeholder references with your actual file paths
3. Add your project-specific security rules
4. Add your project-specific "don'ts" (what AI keeps getting wrong)
5. Commit to your repository root

For deeper guidance on writing effective instructions, maintenance, and tool-specific behavior: [04 — Context Engineering: Project Instructions](../../04-context-engineering/project-instructions.md).
