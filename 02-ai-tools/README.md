# 02 — AI Tools

> Evaluating, comparing, and choosing AI developer tools for your organization.

## Why This Section Matters

The AI developer tooling market is crowded, fast-moving, and heavily marketed. Every tool claims to "10x developer productivity." Without a structured evaluation approach:

- **You pick on hype, not fit** — the tool with the best marketing wins, not the one that matches your ecosystem and constraints
- **Wasted budget and switching cost** — 6 months in, you discover it doesn't integrate with your IDE or meet compliance requirements. Switching costs developer time and trust.
- **Team resentment from forced tools** — a tool chosen without developer input sits unused; 40% of seats go to waste
- **Vendor lock-in by default** — without evaluating build vs. buy tradeoffs upfront, you discover too late that you're locked into a pricing model or architecture that doesn't scale

Leaders need frameworks for evaluation, not just feature lists — because the best tool depends entirely on your constraints.

## In This Section

| Page | What you'll learn |
|------|-------------------|
| [Tool Categories](./tool-categories.md) | Taxonomy of AI developer tools beyond coding agents |
| [Evaluation Framework](./evaluation-framework.md) | Structured approach to comparing and selecting tools |
| [Build vs. Buy](./build-vs-buy.md) | When to use off-the-shelf vs. custom-build vs. API integration |

## Key Decision

> **The question isn't "which tool is best?" — it's "which tool is best for our constraints?"**
>
> Constraints include: compliance requirements, existing IDE ecosystem, budget, language stack, security posture, and team preferences.

## Cost Tiers: Know What You're Signing Up For

```mermaid
flowchart LR
    A[🆓 Free / Explore] --> B[💰 Paid / Team]
    B --> C[🏢 Enterprise]

    A -.- A1[Individual learning<br/>POC, hackathons<br/>No enterprise controls]
    B -.- B1[Team usage<br/>Per-seat licensing<br/>Basic admin controls]
    C -.- C1[Org-wide deployment<br/>SSO, audit, DLP<br/>Custom agreements]
```

- **For POC/exploration:** Use free tiers. Don't request budget yet. Build evidence.
- **For team pilots:** Budget $10–50/user/month. This unlocks controls you need to evaluate properly.
- **For production rollout:** Expect enterprise agreements with volume pricing.

## Quick Navigation

- Looking specifically for coding agents? → [03 — AI Coding Agents](../03-ai-coding-agents/)
- Need security evaluation criteria? → [05 — Security](../06-security/)
- Want to measure tool effectiveness? → [08 — Metrics](../09-metrics/)

## Status

🟢 Active — content being written and refined.

## AI Engineering Maturity: Tools

| Level | What it looks like | What to do |
|:-----:|-------------------|-----------|
| **0** | No AI tools | Start at [01 — Foundations](../01-foundations/) |
| **1** | Individuals on free tiers, no org awareness | Evaluate tools, build evidence for pilot budget |
| **2** | One team on paid tier, evaluating formally | Run structured evaluation, prepare governance |
| **3** | Approved shortlist, enterprise-evaluated, multiple teams | Negotiate volume pricing, standardize configuration |
| **4** | Enterprise agreement, regular re-evaluation cadence, portfolio managed | Optimize, track emerging tools quarterly |
