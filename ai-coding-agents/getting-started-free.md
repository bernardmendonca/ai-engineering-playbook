# Getting Started Free

> Zero-cost paths to hands-on experience with AI coding agents — for individual exploration, team evaluation, and building intuition before committing budget.

> **Last verified:** 2026-10-30 · **Re-check by:** 2027-01-30

## Why Start Free?

Before requesting budget, before writing a policy doc, before running an evaluation — you need hands-on experience. You can't make informed decisions about AI agents without using them yourself. The good news: you can get meaningful experience without spending anything.

> **This page is for decision-makers who want to get their hands dirty.** Not to evaluate enterprise features (you need paid tiers for that), but to understand what agents can actually do, build intuition about where they help, and have informed conversations with your teams.

---

## Quick Start: Choose Your Path

```mermaid
flowchart TD
    A[I want to try an AI coding agent for free] --> B{How much time do I have?}
    B -->|30 minutes| C[Path 1: Quickest taste]
    B -->|2–3 hours| D[Path 2: Real exploration]
    B -->|A full day| E[Path 3: Deep evaluation]

    C --> C1[GitHub Copilot Free<br/>or Kiro Free tier]
    D --> D1[Cursor Free<br/>or Kiro]
    E --> E1[Aider + local model or API key<br/>or Claude Code on Pro]
```

---

## Path 1: Quickest Taste (30 minutes)

**Goal:** Understand what "agent mode" feels like. Get one meaningful task done.

### Option A: GitHub Copilot Free

🆓 **Cost:** $0 (2,000 completions/month plus a small monthly allowance of GitHub AI Credits for chat and agent mode; auto model selection only)

**Setup:**
1. Install VS Code (if you don't have it)
2. Install the GitHub Copilot extension
3. Sign in with your GitHub account (free accounts work)
4. Open agent mode: `Ctrl+Shift+I` / `Cmd+Shift+I` → switch to Agent

**Try this task:**
> "Look at this project and add input validation to the user registration endpoint. Include appropriate error messages and update the tests."

**What you'll observe:** The agent reads files, proposes multi-file changes, and can run tests. This is fundamentally different from autocomplete.

**Limitations on free tier:** The credit allowance runs out after a handful of agent tasks, and you can't pick the model. Use it for a taste, not daily work. The cloud agent (assign an issue, get a PR) requires a paid plan.

---

### Option B: Kiro Free Tier

> **Note:** Amazon Q Developer — the tool previously recommended here — stopped accepting new signups in May 2026 and reaches full end-of-support in April 2027. AWS's successor product is Kiro, which has since gone GA. If you're already on Amazon Q, start planning your migration; new explorers should start with Kiro directly.

🆓 **Cost:** $0 (Free tier — 50 credits/month across agent chat and spec workflows; simple requests use fractions of a credit)

**Setup:**
1. Download Kiro from kiro.dev
2. Sign in
3. Open your project
4. Start using — no configuration needed

**Try this task:**
> "Analyze this codebase and suggest improvements to error handling. Then implement the improvements."

**What you'll observe:** A capable free tier with real agent capabilities and, distinctively, an optional structured spec workflow (requirements → design → tasks) alongside conversational mode.

**Why this is worth trying first:** Kiro's free tier includes real agent capabilities without needing a credit card, and it's the actively developed, currently-supported option in AWS's coding-agent lineup. 50 credits is enough for one or two small features, so plan your tasks before you start.

---

## Path 2: Real Exploration (2–3 hours)

**Goal:** Use an agent on a real task in your own codebase. Build enough experience to have an opinion.

### Option A: Cursor Free Tier

🆓 **Cost:** $0 on the Free tier (limited agent requests). Since October 2026 Cursor is sold as part of SpaceX/xAI's "X Subscription", and trial terms have changed several times this year — check cursor.com/pricing for any current paid-tier trial. Note that the cheapest paid tier only includes Grok and Cursor's own models (see [current Cursor plans](./agent-landscape.md#cursor-spacex--xai)).

**Setup:**
1. Download Cursor from cursor.com
2. Sign up (email, free)
3. Open your project
4. Let it index your codebase (takes a few minutes)
5. Open the Agent panel (`Cmd+I` / `Ctrl+I`)

**Try these tasks (in order):**

**Task 1 — Warm up:**
> "Add comprehensive error handling to [specific file]. Include proper error types, logging, and user-friendly messages."

**Task 2 — Multi-file:**
> "Refactor the [module name] to use the repository pattern. Create the interface, implement it, and update all callers."

**Task 3 — The real test:**
> "We need to add [feature X]. Here's what it should do: [describe]. Implement it following the patterns established in [similar feature]."

**What you'll observe:** The agent reads your codebase, follows existing patterns, and generates coherent multi-file changes.

**Limits:** The Free tier is enough to complete the three tasks above and stay familiar, not enough for daily agent use.

---

### Option B: Kiro

🆓 **Cost:** $0 (Free tier — see [Path 1](#option-b-kiro-free-tier) above for setup if you haven't already; paid Pro/Pro+/Pro Max/Power tiers exist for higher usage)

**Setup:**
1. Download Kiro from kiro.dev
2. Sign in
3. Open your project
4. Try both Vibe mode (conversational) and Spec mode (structured)

**Try these tasks:**

**Task 1 — Vibe mode (conversational):**
> "Add pagination to the /users endpoint. Update the handler, data layer, and tests."

**Task 2 — Spec mode (structured requirements → implementation):**
> Start a spec session for a new feature. Let Kiro guide you through requirements → design → tasks, then execute the tasks.

**What you'll observe:** Spec mode is distinctly different from other agents — it enforces structure before implementation. This is valuable for teams that want repeatability and auditability.

**Why this is interesting for leaders:** The spec-driven workflow appeals to teams that want repeatability and auditability before implementation begins — a different tradeoff than the "just do it" approach of other agents, not a strictly better one. Whether that structure helps or adds friction depends on your team and task type.

---

## Path 3: Deep Evaluation (Full Day)

**Goal:** Stress-test an agent on varied tasks. Understand limitations, failure modes, and real-world effectiveness.

### Option A: Aider (Fully Open Source)

🆓 **Cost:** $0 for the tool. API costs optional (can use free credits or local models).

**Setup (zero-cost with local model):**
1. Install: `python -m pip install aider-install && aider-install` (or `pip install aider-chat`)
2. Install Ollama: `brew install ollama` (macOS) or from ollama.com
3. Pull a current open-weight coding model from the [Ollama library](https://ollama.com/library) (for example, the latest Qwen Coder or DeepSeek release that fits your machine's memory): `ollama pull <model>`
4. Run: `aider --model ollama_chat/<model>`

**Setup (with API credits):**
1. Install Aider as above
2. Create an API key with Anthropic or OpenAI and add a small prepaid balance (check each provider's current free-credit offers; they change often)
3. Run: `aider --model <provider>/<current-model-id>`. Aider's docs list current model aliases (for example, `--model sonnet`), and `aider --list-models <keyword>` shows what's available

**Try these tasks:**

**Task 1 — Simple (build confidence):**
> "Add unit tests for the [module] file. Aim for 80% coverage including edge cases."

**Task 2 — Multi-file refactoring:**
> "Rename the concept 'User' to 'Account' across the entire codebase — models, services, routes, tests, and docs."

**Task 3 — Bug hunting:**
> "The function [X] returns incorrect results when [condition]. Investigate and fix."

**Task 4 — Migration:**
> "Migrate all callback-based async code in [directory] to async/await."

**Task 5 — The failure test (important!):**
> Give it a task that's too vague, too architectural, or too large. See how it fails. This teaches you more than success.

**What you'll observe:**
- With local models: Free but noticeably less capable than top-tier cloud models. Good for learning the workflow, not for evaluating agent quality.
- With API credits: Real quality, limited budget. A small prepaid balance goes further than you think for focused tasks.
- You'll see the raw agent loop — plan, code, test, iterate. No IDE polish. Just the mechanics.

**Why this path is valuable for leaders:** You'll experience the full spectrum — from "this is incredible" to "this is completely wrong." Both experiences are necessary for setting realistic expectations.

---

### Option B: Claude Code (Pro plan or API key)

💰 **Cost:** The entry-level Claude Pro plan includes Claude Code, or pay per token with an API key. There is no free tier. See [current Claude Code plans](./agent-landscape.md#claude-code-anthropic).

**Setup:**
1. Install with the native installer: `curl -fsSL https://claude.ai/install.sh | bash` (macOS/Linux), or `brew install --cask claude-code`. The npm package is deprecated.
2. Run: `claude` in your project directory and sign in with your Claude account (or an API key)
3. Start with: `/init` to let it understand your project and generate a CLAUDE.md

**Try these tasks:**

**Task 1 — Understand your codebase:**
> "Explain the architecture of this project. What are the main components and how do they interact?"

**Task 2 — Complex implementation:**
> "Add rate limiting to all API endpoints. Use a sliding window approach, configure limits per endpoint, and add tests."

**Task 3 — Multi-step with verification:**
> "The /search endpoint is slow. Profile it, identify the bottleneck, implement a fix, and verify with a benchmark."

**What you'll observe:** Deep reasoning, multi-step execution, self-correction. This is the "premium agent experience" — useful for understanding what's possible at the top end.

**Cost awareness:** On Pro you'll hit usage limits on long sessions; on an API key, a complex task can cost several dollars. Start small and check `/cost` or your usage page.

---

## What to Evaluate During Your Exploration

Use this scorecard to structure your experience. Rate each dimension 1–5 after trying the tool:

| Dimension | What to observe | Your rating |
|-----------|----------------|-------------|
| **Task understanding** | Does it understand what you actually want? | /5 |
| **Code quality** | Is the generated code good enough to ship? | /5 |
| **Pattern following** | Does it match your existing codebase style? | /5 |
| **Error handling** | How does it recover when something goes wrong? | /5 |
| **Scope discipline** | Does it stay within the task boundaries? | /5 |
| **Speed** | How long does a typical task take? | /5 |
| **Effort to use** | How much prompting and correction is needed? | /5 |
| **Failure transparency** | Does it tell you when it can't do something? | /5 |

---

## From Exploration to Decision

After trying agents, you'll likely fall into one of these positions:

```mermaid
flowchart TD
    A[After exploring agents...] --> B{Your conclusion?}
    B -->|This is clearly valuable| C[Move to Production Rollout<br/>Define scope, get budget, pilot with a team]
    B -->|Useful for some tasks, not others| D[Define your task suitability matrix<br/>See When to Use Agents]
    B -->|Not ready for us yet| E[Document why<br/>Revisit in 3–6 months<br/>The landscape moves fast]
    B -->|I need more data| F[Run a structured pilot<br/>3–5 developers, 4 weeks, defined metrics]
```

---

## Things Free Tiers Won't Tell You

Be aware of what you *cannot* evaluate on free tiers:

| You can evaluate for free | You cannot evaluate for free |
|--------------------------|------------------------------|
| Code generation quality | Enterprise SSO/SAML integration |
| Agent reasoning capability | Audit logging and compliance features |
| Task suitability | Admin dashboards and usage analytics |
| Developer experience/UX | Content exclusion policies |
| Speed and responsiveness | IP indemnification terms |
| Failure modes and limits | Data residency guarantees |
| Personal productivity gain | Team-wide adoption patterns |

> **The gap:** Free tiers are optimized to show you the *capability*. They don't show you the *governance*. Don't make an enterprise purchasing decision based only on how the tool feels to use individually. The governance features (covered in [Governing Agents](./governing-agents.md)) require paid tier evaluation.

---

## The 5-Day Challenge (For Engineering Leaders)

If you want a structured exploration experience, try this:

| Day | Task | Tool | Goal |
|-----|------|------|------|
| **Monday** | Generate tests for an untested module | Any free option | Understand basic agent interaction |
| **Tuesday** | Refactor a real file in your codebase | Same tool | See how it handles your code |
| **Wednesday** | Try a multi-file feature implementation | Cursor, Kiro, or Copilot | Experience agent mode at full power |
| **Thursday** | Give it a task that's too hard | Same tool | Understand failure modes |
| **Friday** | Write up your findings | — | Document insights for your team |

After this week, you'll have enough experience to:
- Set realistic expectations with your team
- Know which tasks are agent-suitable in your codebase
- Have an informed opinion on which tool fits your context
- Make a credible budget request (if warranted)

---

## Next Steps

- Ready to scale beyond personal use? → [Production Rollout](./production-rollout.md)
- Want to understand governance before scaling? → [Governing Agent Usage](./governing-agents.md)
- Need to know which tasks are appropriate? → [When to Use Agents](./when-to-use-agents.md)
