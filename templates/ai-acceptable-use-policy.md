# Template: AI Acceptable Use Policy

> Adapt this template for your organization. Remove/add sections as appropriate.

---

# AI Tools Acceptable Use Policy

**Effective date:** [Date]
**Owner:** [VP Engineering / CISO / Name]
**Review cadence:** Quarterly
**Next review:** [Date + 3 months]

---

## 1. Purpose

This policy defines how [Organization Name] engineering teams may use AI-powered development tools. It enables productivity gains while protecting our code, data, and intellectual property.

## 2. Scope

**Applies to:** All engineering personnel (employees, contractors, vendors) who write, review, or manage code for [Organization Name].

**Covers:** AI coding assistants, AI agents, AI code review tools, and any service that processes our source code using AI/ML models.

## 3. Approved Tools

### General Use (all engineering staff)
- [Tool A] — [tier/plan]
- [Tool B] — [tier/plan]

### Restricted Use (specific teams/approval required)
- [Tool C] — approved for [use case] only
- [Tool D] — approved with [condition]

### Not Approved
- Personal accounts (ChatGPT, Claude.ai, etc.) for company code
- Any tool not listed above
- Free/individual tiers of approved tools (use company account only)

### New Tool Requests
Submit via [process/form/channel]. Security review required. Typical turnaround: [X weeks].

## 4. Data Classification

### ✅ Approved for AI Tools
- Code in repositories classified as **Internal**
- Open source code
- General programming questions
- Test code and synthetic data

### ⚠️ Requires Explicit Approval
- Code in repositories classified as **IP-Sensitive**
- Infrastructure code with architecture details
- [Add organization-specific items]

### ❌ Never Send to AI Services
- Code classified as **Restricted**
- Secrets, API keys, tokens, credentials
- Customer data or PII
- Code under NDA or third-party IP restrictions
- [Add organization-specific items]

## 5. Usage Rules

### Code Quality
- AI-generated code is held to the same standard as human-written code
- All AI-generated code must be reviewed before merging
- Tests are required for AI-generated features (same as any code)
- Mark AI-assisted PRs with [label/tag/convention]

### Security
- Never include secrets in AI tool context
- Use content exclusion (`.copilotignore`) for sensitive paths
- Report suspected data exposure to [security channel] within 1 hour
- Enable privacy/enterprise mode on all approved tools

### Cost
- Stay within allocated team budget
- Report cost anomalies to your manager
- Do not run agents without monitoring (set timeouts)
- [Monthly budget per developer: $X / team: $Y]

### Accountability
- Developer who submits code owns it (regardless of how it was created)
- Reviewer who approves is accountable for review quality
- AI suggestions do not reduce human responsibility

## 6. Agent-Specific Rules

When using AI coding agents (autonomous multi-step tools):
- Agents may not push to protected branches
- Agents may not modify CI/CD pipeline configuration without approval
- Agents may not access production systems or credentials
- Agent commands limited to: [approved command list]
- [Autonomy level policy — e.g., "supervised mode for Restricted-adjacent code"]

## 7. Incident Response

### Data Exposure
1. Stop using the tool immediately
2. Report to [security team / channel] within 1 hour
3. Do not attempt to "undo" — let security assess
4. Follow security team guidance

### Quality Incident (AI code caused production issue)
1. Follow standard incident response
2. Note AI involvement in postmortem
3. Review whether controls need updating
4. No individual blame — focus on systemic improvement

### Policy Violation
1. Report via [channel] (anonymous option available)
2. First occurrence: Education and retraining
3. Repeated violations: Manager involvement
4. Malicious violations: Standard disciplinary process

## 8. Exceptions

- Exceptions require written approval from [policy owner]
- Exceptions are time-limited (max [X months], then re-evaluate)
- Document: what, why, risk mitigation, duration
- Submit via [process]

## 9. Governance

- **Owner:** [Name/Role]
- **Review:** Quarterly (or when significant tool/landscape changes occur)
- **Updates communicated via:** [Channel — email, Slack, all-hands]
- **Questions/clarifications:** [Channel]

---

*Last updated: [Date] | Version: [X.X]*
