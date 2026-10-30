# Delegated and Parallel Agents

> Handing whole tasks to cloud agents that work on their own and come back with a pull request — what changes, when it's worth it, and how to govern it.

> **Last verified:** 2026-10-30 · **Re-check by:** 2027-01-30

## What Changed

Most of this playbook describes a developer working *with* an agent: one session, in the IDE or terminal, watching it work. Since 2025 a second mode has become mainstream: **delegation**. A developer (or an automation) assigns a task, the agent runs in a cloud sandbox without supervision, and the result arrives as a pull request. Developers increasingly run several of these at once.

At GitHub Universe in October 2026, GitHub said agents now start roughly 40% of pull requests on its platform ([TNW](https://thenextweb.com/news/github-universe-copilot-fusion-octoverse-agents)). Whatever the exact share in your org, delegated work is now large enough to need its own rules.

| | Interactive agent | Delegated agent |
|---|---|---|
| **Where it runs** | Developer's machine or IDE | Vendor's cloud sandbox (or your CI runners) |
| **Who watches** | Developer, step by step | Nobody until the PR arrives |
| **Unit of work** | A session | A task that ends in a PR |
| **Concurrency** | One at a time | Several per developer |
| **Main risk** | Bad edits the developer misses | Unreviewed volume, untrusted task input, over-broad credentials |
| **Main control** | Approval prompts, permissions | Sandbox, identity, branch protection, review |

### Where you'll find it

| Product | How work is assigned | Notes |
|---------|---------------------|-------|
| GitHub Copilot cloud agent | Assign an issue to Copilot, or start from the Copilot app, VS Code, or mobile | Runs in a GitHub Actions-backed environment with a firewall; pushes only to its own branches |
| OpenAI Codex (cloud tasks) | Codex app, IDE extension, ChatGPT, or GitHub | Runs in a cloud container; network access configurable |
| Claude Code (cloud / web sessions) | Claude apps, or GitHub via the Claude Code GitHub Action | Also runs headless in your own CI |
| Cursor cloud agents | Cursor editor, web, or integrations | Included from the Premium tier of the X Subscription |
| Kiro Web (autonomous mode) | `kiro` label or `/kiro` comment on a GitHub issue, or app.kiro.dev | Asks clarifying questions, plans with sub-agents, opens a PR |
| Devin | Devin app, Slack, or ticket integrations | Cognition's autonomous agent; Devin Desktop is the IDE side |
| Google Antigravity | Agent manager in the Antigravity IDE | Manages multiple agents in parallel |

*Vendor details change quickly; check current docs. See [Agent Landscape](./agent-landscape.md) for pricing and enterprise controls.*

---

## When to Delegate

Delegation pays off when a task is well specified and cheap to verify. It fails when the agent needs judgment calls nobody wrote down.

| Delegate | Keep interactive |
|----------|-----------------|
| Bug fixes with a clear reproduction | Bugs you can't reproduce yet |
| Test coverage for a named module | Design of a new module or API |
| Dependency upgrades and mechanical migrations | Changes to auth, payments, or data deletion paths |
| Small features with written acceptance criteria | Anything where "done" isn't defined |
| Docs updates, lint fixes, flaky-test triage | Cross-repo changes with ordering constraints |

The [When to Use Agents](./when-to-use-agents.md) suitability matrix applies, with one adjustment: for delegated work, **verifiability matters more than difficulty**. A hard task with a strong test suite is a better delegation candidate than an easy task with no tests, because no one is watching the agent's reasoning along the way.

> ✅ **My take:** The best predictor of delegation success is the quality of the issue. If a competent new hire couldn't finish the task from the issue text alone, the agent won't either. Teams that get value from delegation improve their issue writing first.

---

## Governing Delegated Agents

Delegation moves the control point from "approve each step" to "control the environment and review the output." Six areas need explicit decisions.

### 1. Identity

Each agent should act as its own non-human identity with scoped, short-lived credentials, never as a developer's personal token. This keeps the audit trail honest and limits what a hijacked agent can reach (OWASP ASI03, Identity and Privilege Abuse — see [Agentic Security](../security/agentic-security.md)).

- Use the vendor's built-in agent identity where one exists (for example, Copilot's cloud agent commits as its own bot account)
- If you run agents in your own CI, issue per-run tokens scoped to the one repository and the permissions the task needs
- Record which human assigned each task

### 2. Sandbox and network

- Run delegated agents only in isolated environments, never on a machine holding production credentials
- Default network access to an allowlist (package registries, your docs), not the open internet
- Give the sandbox only the secrets the task needs. Most tasks need none.

### 3. Repository controls

These already exist in your Git platform. Delegation makes them mandatory:

- Branch protection on default and release branches, with required status checks
- Agents push to their own branches only
- At least one human approval required to merge, from someone other than the person who assigned the task where possible (GitHub enforces this for Copilot's cloud agent: the person who asked Copilot for the PR can't approve it)
- CI on agent PRs runs with the same restrictions as PRs from forks. GitHub, for example, doesn't run Actions workflows on Copilot's PRs until someone with write access approves the run.

### 4. Task intake

Who can assign work to an agent is a security decision. An issue is untrusted input: if anyone can open an issue and the agent acts on it, anyone can instruct your agent (see [prompt injection](../security/threat-model.md#prompt-injection-direct-and-indirect)).

| Source of the task | Policy |
|--------------------|--------|
| Issue written by a team member | Can be assigned to an agent directly |
| Issue from an outside contributor or customer | A team member restates or approves the task before assignment |
| Automated trigger (alert, scanner finding) | Allowed for narrow, pre-approved task types only (e.g. dependency bumps) |

### 5. Ownership

Every agent PR has one named human owner: the person who assigned it. They answer review comments, decide whether it merges, and own it in production. "The agent wrote it" is never an answer in an incident review. This is the same principle as [Governing Agents](./governing-agents.md#attribution-who-wrote-this-code), applied to work nobody watched being done.

### 6. Concurrency and cost

Parallel agents multiply both output and spend.

- Cap concurrent agent tasks per developer at the level their review capacity supports
- Watch for abandoned agent PRs: work that was started, not reviewed, and left to rot is pure cost
- Track spend per assigned task, not just per seat (see [Spend Management](../ai-strategy/spend-management.md))

---

## Supervising Several Agents at Once

The new skill is less "write a good prompt" and more "run a small queue of work." Practices that help:

- **Write the issue as the spec.** Context, acceptance criteria, files likely involved, how to verify. See [Spec-Driven Development](../ai-engineering-practices/spec-driven-development.md).
- **Keep tasks independent.** Parallel agents editing the same files produce merge conflicts and contradictory changes. Split work along file or module boundaries.
- **Batch your reviews.** Check in on agent PRs at set times rather than context-switching every time one finishes.
- **Kill early.** If the first push is heading the wrong way, close it and rewrite the issue. Steering a confused agent through review comments costs more than restarting.
- **Make agents show evidence.** Require test output, screenshots, or a reproduction in the PR description (see [Code Review at Agent Scale](../engineering-workflows/code-review.md#reviewing-at-agent-scale)).

> ✅ **My take:** Start each developer at one or two concurrent delegated tasks. Raise the limit only when their agent PRs are getting reviewed within a day and the rejection rate is stable. Most teams find review, not agent capacity, is the ceiling.

---

## Rollout Path

| Step | What to do | Exit criteria |
|------|-----------|---------------|
| **1. Prerequisites** | Branch protection, required CI, sandboxed agent environment, written intake policy | All agent-eligible repos meet the controls above |
| **2. Narrow pilot** | One team, task types limited to tests, docs, and dependency upgrades | 4 weeks with stable change fail rate and review times |
| **3. Widen task types** | Add bug fixes and small features with acceptance criteria | Rejection rate and rework rate stay at or below baseline |
| **4. Scale** | More teams; automated triggers for pre-approved task types | Spend per merged PR and review latency within targets |

Measure the same things as any agent rollout ([Production Rollout](./production-rollout.md)), plus three delegation-specific metrics:

| Metric | Why it matters |
|--------|---------------|
| Agent PR acceptance rate (merged ÷ opened) | Low rates mean poor task selection or poor issue quality |
| Time from agent PR opened to first human review | Rising latency means agents are outrunning review capacity |
| Cost per merged agent PR | The unit economics of delegation |

---

## Maturity

Delegated agents add a level above the four in [What Is an Agent?](./what-is-an-agent.md):

| Level | What it looks like |
|:-----:|-------------------|
| **4 — Agent** | Developers run interactive agents, supervising each session |
| **5 — Delegated** | Developers assign well-specified tasks to cloud agents and review the resulting PRs; agents run in sandboxes with their own identities; review capacity is managed as a constraint |

---

## Next Steps

- Review practices for high PR volume → [Code Review with AI](../engineering-workflows/code-review.md#reviewing-at-agent-scale)
- Security risks specific to autonomous agents → [Agentic Security](../security/agentic-security.md)
- Budgeting for usage-based agents → [Spend Management](../ai-strategy/spend-management.md)
- General agent governance → [Governing Agent Usage](./governing-agents.md)
