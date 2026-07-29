# AI Usage Policy

> How to write an effective AI acceptable use policy — with a starter template you can adapt.

## Why You Need a Policy

Without explicit policy:
- Developers don't know what's allowed (and either do nothing or do everything)
- Security and legal teams have no framework for evaluating requests
- Incidents have no clear response path
- Shadow IT flourishes (developers use personal accounts for unapproved tools)

---

## Policy Design Principles

1. **Enable, don't just restrict** — The goal is safe usage, not prohibition
2. **Be specific** — "Use AI responsibly" is not a policy. Name tools, name boundaries.
3. **Be discoverable** — Developers should find the policy without searching. Put it where they already look.
4. **Be current** — Review quarterly. Outdated policy is worse than no policy (developers learn to ignore it).
5. **Be enforceable** — Don't write rules you can't check or won't enforce.

---

## Policy Structure Template

### Section 1: Scope and Purpose

```markdown
## Purpose
This policy defines acceptable use of AI-powered tools for software
development within [Organization Name]. It enables teams to benefit
from AI productivity tools while protecting organizational security,
intellectual property, and code quality.

## Scope
Applies to: All engineering staff (employees, contractors, vendors)
Covers: AI coding assistants, agents, code review tools, and any
tool that processes our source code using AI/ML models.
```

### Section 2: Approved Tools

```markdown
## Approved Tools

### Tier 1: Approved for General Use
- [Tool A] — approved for all non-restricted code
- [Tool B] — approved for all non-restricted code

### Tier 2: Approved with Restrictions
- [Tool C] — approved for [specific use cases] only
- [Tool D] — approved for non-sensitive code only

### Not Approved
- Personal ChatGPT/Claude accounts for company code
- Any tool not listed above

### Requesting a New Tool
Submit request via [process]. Security review required.
Typical turnaround: [X weeks].
```

### Section 3: Data Classification Rules

```markdown
## What Can Be Sent to AI Services

### ✅ Allowed
- Application code classified as Internal (see data classification policy)
- Open source code
- General programming questions without proprietary context
- Test code and sample data

### ⚠️ Requires Approval
- Code in repositories classified as IP-sensitive
- Infrastructure code containing architecture details
- Code that references customer-specific logic

### ❌ Never Allowed
- Source code classified as Restricted
- API keys, secrets, credentials, tokens
- Customer PII or data
- Code under NDA or external IP restrictions
- Security implementations (auth, crypto, access control) — without explicit approval
```

### Section 4: Usage Rules

```markdown
## Usage Rules

### Code Quality
- AI-generated code must pass the same review standards as human-written code
- PR descriptions must indicate if substantial portions were AI-generated
- AI-generated tests must be reviewed for meaningfulness (not just coverage)

### Security
- Never include secrets, credentials, or PII in AI tool context
- Use .copilotignore / content exclusion for sensitive paths
- Report any suspected data exposure immediately to security team

### Accountability
- The developer who submits AI-generated code owns it
- Code review approval means you've reviewed for correctness, not just style
- AI suggestions do not reduce the reviewer's responsibility

### Cost
- Stay within team-allocated AI tool budget
- Report unexpected cost spikes to your manager
- Don't run agents in loops without monitoring
```

### Section 5: Incident Response

```markdown
## When Things Go Wrong

### If sensitive data was sent to an AI service:
1. Stop using the tool immediately
2. Report to security team via [channel] within 1 hour
3. Security will assess exposure and determine response
4. Do NOT attempt to "undo" or cover up the exposure

### If AI-generated code caused a production incident:
1. Follow standard incident response process
2. Note in postmortem that AI was involved in code generation
3. Review whether governance controls need updating
4. No blame on individual — focus on systemic improvement

### If you discover policy violations:
1. Report via [channel] (anonymous reporting available)
2. Manager and security team assess
3. Focus on education and process improvement, not punishment
```

### Section 6: Governance and Review

```markdown
## Policy Governance

- **Owner:** [VP Engineering / CISO / Governance Committee]
- **Review cadence:** Quarterly (or when landscape changes significantly)
- **Exception process:** Submit to [committee/owner] with justification
- **Effective date:** [Date]
- **Next review:** [Date + 3 months]
```

---

## Common Policy Mistakes

| Mistake | Consequence | Better approach |
|---------|------------|----------------|
| Too restrictive ("no AI anywhere") | Shadow IT, talent loss | Enable with guardrails |
| Too vague ("use AI responsibly") | No actionable guidance | Name specific tools, rules, boundaries |
| Never updated | Developers ignore stale policy | Quarterly review, date stamp visible |
| Hidden in wiki nobody reads | Nobody knows it exists | Announce, pin in Slack, reference in onboarding |
| Only punitive (consequences only) | Fear-based compliance, underreporting | Lead with enablement, include support paths |
| No exception process | Either people break rules or good work is blocked | Clear, fast exception request path |

---

## Rollout Advice

1. **Draft** with input from Security, Legal, and senior developers
2. **Review** with 3–5 developers for clarity and practicality
3. **Announce** with context ("why this exists, how it helps you")
4. **Train** — 15-minute overview session, recorded for async
5. **Enforce gently** at first — remind, educate, then escalate for repeat violations
6. **Review** first quarter after launch, incorporate feedback

---

## Next

- Responsible AI practices → [Responsible AI](./responsible-ai.md)
- Compliance landscape → [Compliance](./compliance.md)
- Agent-specific governance → [03 — Governing Agents](../03-ai-coding-agents/governing-agents.md)
