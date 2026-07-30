# AI Anti-Patterns

> The mistakes engineering organizations keep making with AI adoption — and how to avoid them.

## Why This Section Exists

Every playbook tells you what to do. This section tells you what **not** to do — the patterns that look reasonable but reliably fail. These aren't theoretical; they're drawn from repeated observations across organizations of all sizes.

Reading this takes 10 minutes. It can save you 6 months of learning the hard way.

> **Engineering Manager Note**
>
> If you only read one section before starting your AI adoption journey, make it this one.
>
> Avoiding the top 5 mistakes matters more than getting everything else perfect.

---

## 🧭 Decide — Strategy Anti-Patterns

### 1. "Let's wait until AI matures"

**What it looks like:** Leadership decides to wait 12–18 months "until the dust settles."

**Why it fails:** The dust won't settle — this is a continuous evolution. Meanwhile, your developers use tools on personal accounts (zero governance), competitors ship faster, and your best talent leaves for companies that provide AI tools.

**The fix:** Start exploring now with free tiers. Waiting for certainty is choosing the risk of irrelevance over the risk of imperfection.

→ [Foundations: Org Readiness](./foundations/org-readiness.md)

---

### 2. "AI is an R&D experiment"

**What it looks like:** AI tools budgeted under R&D or innovation. Framed as "let's see if this works."

**Why it fails:** Experiments get cut. When budget pressure comes, "experiments" are first on the chopping block — regardless of results. Also signals internally that this isn't serious.

**The fix:** Frame as developer tooling infrastructure (same category as CI/CD, IDEs, observability). Permanent capability, not experiment.

→ [AI Strategy: Investment Strategy](./ai-strategy/investment-strategy.md)

---

### 3. "We need an AI Center of Excellence first"

**What it looks like:** Before any developer uses AI tools, leadership creates a 5-person dedicated team to "figure out AI for the org."

**Why it fails:** The CoE builds frameworks nobody asked for. Months pass. No developer has touched a tool. The CoE becomes a gate instead of an enabler. Meanwhile, shadow IT grows.

**The fix:** Start with developers using tools. Let structure emerge from need, not speculation. CoE (if needed) comes after you have 100+ developers using AI tools — not before.

→ [AI Strategy: Organizational Models](./ai-strategy/org-models.md)

---

### 4. "Our CTO tried it and it was great — roll it out to everyone"

**What it looks like:** A senior leader has a great personal experience and mandates immediate org-wide deployment.

**Why it fails:** What works for one technical leader on their side project doesn't generalize. No governance, no baseline metrics, no support infrastructure. Teams flounder. Adoption looks high (it's mandated) but value is low.

**The fix:** Phased rollout. Pilot one team, measure, expand with support. Never skip from "one person tried it" to "everyone must use it."

→ [Team Adoption: Adoption Phases](./team-adoption/adoption-phases.md)

---

### 5. "We'll figure out security later"

**What it looks like:** Tools deployed first, security reviewed retroactively (if ever).

**Why it fails:** By the time security reviews, 50 developers have been sending code to an unapproved service for 3 months. Now you either grandfather the risk or disrupt 50 people's workflows.

**The fix:** Security review in parallel with Phase 1 exploration — not sequentially after. It takes 2 weeks. Start it when you start exploring.

→ [Security: Threat Model](./security/threat-model.md)

---

## 🔧 Implement — Technical Anti-Patterns

### 6. "Let the AI write everything"

**What it looks like:** Developers give agents maximum autonomy from day one. "Just build the feature."

**Why it fails:** Agents produce plausible-looking code that may be subtly wrong, over-engineered, or insecure. Without review discipline, these problems compound. Quality regresses silently.

**The fix:** Start with supervised mode. Earn autonomy through demonstrated quality. Human reviews every agent PR until trust is established.

→ [AI Coding Agents: When to Use Agents](./ai-coding-agents/when-to-use-agents.md)

---

### 7. "AI will fix our broken processes"

**What it looks like:** Team has no code review culture, no CI, no tests. Adopts AI hoping it will compensate.

**Why it fails:** AI amplifies what you have. Good process + AI = faster good work. No process + AI = faster bad work. Agents without CI can't verify their own output. Agents without code review send unexamined code to production.

**The fix:** Fix fundamentals first. CI, code review, and basic test coverage are prerequisites — not nice-to-haves.

→ [Foundations: Org Readiness](./foundations/org-readiness.md)

---

### 8. "One prompt fits all"

**What it looks like:** No project instructions, no steering files, no team conventions codified. Each developer prompts individually every time.

**Why it fails:** Inconsistent output across the team. Developer A gets great results (good prompts); Developer B gets garbage (vague prompts). Team concludes "AI is unreliable" when really the context is unreliable.

**The fix:** Write a project instructions file (CLAUDE.md, .cursorrules, etc.). Two hours of work. Immediately improves consistency for every developer on that project.

→ [Context Engineering: Project Instructions](./context-engineering/project-instructions.md)

---

### 9. "We'll use AI for everything"

**What it looks like:** Deploying agents for architectural decisions, complex business logic, security-critical code, and novel design work.

**Why it fails:** Agents excel at pattern-following, not pattern-creating. Architecture requires business context agents don't have. Security code requires threat awareness agents lack. Using agents for these tasks produces plausible but wrong output.

**The fix:** Define task suitability. Agents for: refactoring, tests, boilerplate, migrations. Humans for: architecture, security design, novel algorithms, ambiguous requirements.

→ [AI Coding Agents: When to Use Agents](./ai-coding-agents/when-to-use-agents.md)

---

### 10. "We accept AI-generated tests at face value"

**What it looks like:** Agent generates 50 tests. They pass. Team merges without reviewing test quality.

**Why it fails:** AI-generated tests often test the implementation (tautological) rather than the behavior. They provide false coverage confidence. When the implementation changes, the tests change too — catching nothing.

**The fix:** Review AI tests with one question: "If I rewrote the implementation differently but correctly, would these tests still pass?" If no, the tests are worthless.

→ [Engineering Workflows: Testing](./engineering-workflows/testing.md)

---

### 11. "We don't need to configure the AI tool"

**What it looks like:** Install the tool, give developers access, done. No project instructions, no hooks, no steering.

**Why it fails:** The tool works generically but doesn't know your conventions, patterns, or standards. Output requires constant correction. Developers spend time fighting the tool instead of leveraging it.

**The fix:** Invest 2–4 hours in project instructions. Add hooks for quality gates. The setup pays for itself within the first week.

→ [Context Engineering](./context-engineering/)

---

## 🔁 Sustain — Organizational Anti-Patterns

### 12. "Mandate usage, measure activity"

**What it looks like:** "All developers must use AI tools 5+ times per day. Usage tracked in performance reviews."

**Why it fails:** Developers game the metric. Open the tool, ask meaningless questions, close it. Metric looks great. Value is zero. Resentment grows. Tool becomes associated with surveillance.

**The fix:** Mandate availability, not usage. Measure outcomes (cycle time, quality), not inputs (tool usage count). Let value drive adoption.

→ [Team Adoption: Handling Resistance](./team-adoption/handling-resistance.md)

---

### 13. "We'll measure later"

**What it looks like:** Deploy tools, skip baselining, figure out metrics "once things are running."

**Why it fails:** Three months later, someone asks "is this working?" and you have no baseline to compare against. You can't prove improvement. Budget renewal becomes a political fight instead of a data conversation.

**The fix:** Capture baseline metrics (PR cycle time, deployment frequency, bug rate) for 4–6 weeks BEFORE introducing tools. It's the single most important thing you can do for your future self.

→ [Metrics: Metrics Framework](./metrics/metrics-framework.md)

---

### 14. "One policy for all teams"

**What it looks like:** Identical AI governance policy applied uniformly. Same rules for the team building internal dashboards and the team handling PCI-scoped payment processing.

**Why it fails:** Over-governs low-risk teams (blocking productivity) while potentially under-governing high-risk teams (giving false confidence). Teams route around policies that don't fit their context.

**The fix:** Tiered governance. Light for low-risk work, strict for sensitive work. Data classification drives the tier, not a blanket rule.

→ [Security: Data Classification](./security/data-classification.md)

---

### 15. "Set and forget"

**What it looks like:** Pick a tool, write a policy, deploy. Never revisit. "We did AI adoption — check."

**Why it fails:** The landscape changes quarterly. Your tool may be obsolete in 12 months. Your policy may be out of date in 6. New capabilities emerge. Costs shift. Better options appear.

**The fix:** Quarterly review cadence: Is our tool still the right choice? Is our policy still current? Are our metrics still relevant? Is adoption healthy?

→ [AI Strategy: Vendor Strategy](./ai-strategy/vendor-strategy.md)

---

### 16. "Ignore the skeptics"

**What it looks like:** Focus all energy on enthusiasts. Dismiss resistant developers as "behind the times."

**Why it fails:** Skeptics often have valid concerns (quality, security, job safety). Ignoring them creates underground resistance. One influential skeptic's experience story outweighs ten quiet successes. They may also catch real problems that enthusiasts overlook.

**The fix:** Engage skeptics directly. Address concerns honestly. Give them valued roles (security reviewer for AI code, quality gatekeeper). Their scrutiny makes your adoption stronger.

→ [Team Adoption: Handling Resistance](./team-adoption/handling-resistance.md)

---

### 17. "Big-bang rollout"

**What it looks like:** "We've decided. Everyone gets access Monday. Here's a Slack message about it."

**Why it fails:** No support infrastructure. Teams with complex legacy code struggle. No one to ask questions. First experience is bad for many. Those bad experiences calcify into "AI doesn't work here" narrative that takes months to undo.

**The fix:** Phased rollout with support at each stage. Pilot → expand → normalize. Each stage has support capacity matching demand.

→ [AI Coding Agents: Production Rollout](./ai-coding-agents/production-rollout.md)

---

### 18. "AI-generated code doesn't need the same review"

**What it looks like:** "The AI wrote it, it's probably fine." Lower review bar for agent-generated PRs because the code "looks" correct.

**Why it fails:** AI makes different mistakes than humans — consistent subtle errors, missing edge cases, over-engineering, scope creep. These require *more* scrutiny, not less, because they look intentional.

**The fix:** Same quality bar, different focus. When reviewing AI code: check coherence, completeness, security boundaries, scope discipline, and test quality specifically.

→ [Engineering Workflows: Code Review](./engineering-workflows/code-review.md)

---

## Quick Reference: The Top 5

If you remember nothing else, avoid these:

| # | Anti-pattern | One-line fix |
|---|-------------|-------------|
| 1 | Waiting for AI to mature | Start now. Free tiers. Zero risk. |
| 7 | AI on broken processes | Fix CI/review first. AI amplifies what exists. |
| 8 | No project instructions | Write CLAUDE.md today. Two hours. |
| 12 | Mandating usage metrics | Measure outcomes, not tool opens. |
| 13 | No baseline before deploying | 4 weeks of metrics BEFORE you start. |

---

## AI Engineering Maturity: Anti-Pattern Awareness

| Level | What it looks like |
|:-----:|-------------------|
| **0** | Unaware of common failure modes — likely to make most of these mistakes |
| **1** | Aware of anti-patterns but no systematic prevention |
| **2** | Anti-patterns addressed in policy and training — team knows what to avoid |
| **3** | Detection mechanisms in place (reviews, metrics, retrospectives catch anti-patterns early) |
| **4** | Learning organization — anti-patterns surfaced and addressed proactively, shared across teams |

---

## Contributing

Experienced an anti-pattern not listed here? [Contribute](./CONTRIBUTING.md) it. The most valuable additions include: what it looked like, why it failed, and what you did instead.
