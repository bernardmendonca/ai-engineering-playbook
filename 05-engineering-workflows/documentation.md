# Documentation with AI

> Keeping documentation alive, accurate, and useful — with AI as the maintenance engine.

## The Documentation Problem

Documentation is always stale. Everyone knows it. Nobody fixes it. AI can break this cycle — not by replacing human documentation, but by automating the maintenance that humans consistently neglect.

---

## What AI Does Well for Documentation

| Task | Quality | Cost |
|------|---------|------|
| Generate API reference from code | High — factual, verifiable | 🆓 Built into agents |
| Update docs when code changes | High — detects drift | 💰 CI integration |
| Create README for new modules | Medium — needs human review | 🆓 Built into agents |
| Write architectural docs | Low — lacks context and "why" | 🆓 But needs heavy editing |
| Generate onboarding guides | Medium — good structure, may miss tribal knowledge | 🆓 Good starting point |

> **Our take:** Let AI fully own **API reference documentation**. It's factual, verifiable, and generated from code — there's no "why" or judgment involved. Hook it into CI so it regenerates on merge. Humans should never manually maintain API reference docs again. Everything else (architecture docs, ADRs, onboarding guides) should be AI-drafted and human-edited. Architecture docs in particular should never be AI-only — the "why" is the valuable part and AI doesn't have it.

---

## Patterns

### Pattern 1: Generated-and-Verified API Docs

**What:** AI generates API documentation from code (types, endpoints, function signatures), human verifies.

**When:** New APIs, libraries, or SDKs. Any code that has consumers who need reference docs.

**Approach:**
1. Agent reads source code (types, endpoints, JSDoc/docstrings)
2. Generates structured documentation (parameters, return types, examples)
3. Human adds: "why", usage guidance, gotchas
4. CI checks: docs stay in sync with code

---

### Pattern 2: Doc-Drift Detection in CI

**What:** CI step detects when code changes make existing docs stale.

**When:** Any project where docs exist and should be maintained.

**Approach:**
1. Map code files → doc files (convention or config)
2. On PR: detect if code changed but related docs didn't
3. AI generates suggested doc update
4. Post as PR comment: "This code change may make [doc.md] stale. Suggested update: ..."

---

### Pattern 3: Architecture Decision Records (ADRs)

**What:** Use agents to draft ADRs from conversations and code context.

**When:** After architectural decisions are made (design meetings, Slack discussions, PRs).

**Approach:**
1. Human provides: context, decision made, options considered
2. Agent generates: structured ADR (title, context, decision, consequences, status)
3. Human edits: adds nuance, validates accuracy
4. Committed to repo (standard ADR process)

**Template prompt:**
> "Write an Architecture Decision Record for the decision to [X]. Context: [Y]. We considered [options A, B, C]. We chose [B] because [reasons]. The tradeoffs are [Z]."

---

### Pattern 4: Code-to-Comment Generation

**What:** Add inline documentation to undocumented code.

**When:** Legacy codebases where tribal knowledge hasn't been captured.

**Approach:**
1. Agent reads function/class
2. Generates JSDoc/docstring explaining purpose, params, return values
3. Human verifies accuracy
4. Particularly valuable before the author leaves the team

**⚠️ Caution:** AI documents what code *does*, not what it *should* do. For complex business logic, human must validate that the documentation reflects intent, not just behavior.

---

## What to Document with AI vs. Humans

| Document type | AI-generated? | Human role |
|--------------|:-------------:|-----------|
| API reference | ✅ | Verify accuracy, add examples |
| README/getting started | ✅ (draft) | Add context, validate completeness |
| Architecture docs | ⚠️ (structure only) | Provide the "why" and decisions |
| Runbooks/playbooks | ✅ (from code/config) | Verify steps work, add tribal knowledge |
| Onboarding guides | ⚠️ (draft) | Add team-specific context |
| Design decisions (ADRs) | ✅ (structured draft) | Validate reasoning, add nuance |
| Release notes | ✅ (from git history) | Edit for audience, add impact context |

---

## Anti-Patterns

| Anti-pattern | Problem | Instead |
|-------------|---------|---------|
| "AI, document everything" | Generates volume without value | Document what humans need; skip the obvious |
| AI-generated docs never reviewed | Inaccurate docs worse than no docs | Human verification is non-negotiable |
| Docs generated once, then abandoned | Same staleness problem, new format | CI-based drift detection keeps docs current |
| Over-documenting obvious code | `// Increment counter` on `counter++` | Document "why" and "when", not "what" |

---

## Next

- Testing workflows → [Testing Workflows](./testing.md)
- CI/CD integration → [CI/CD Integration](./cicd-integration.md)
- Return to section overview → [README](./README.md)
