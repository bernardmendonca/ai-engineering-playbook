# Case Study: Enterprise — Scaling with Compliance

> An 800-engineer financial services company adopts AI tools within strict regulatory constraints.

## Context

- **Size:** 800+ engineers across 50+ teams, 4 business units
- **Industry:** Financial services (banking platform)
- **Tech stack:** Java, Kotlin, Python, microservices, on-prem + cloud hybrid
- **Stage:** Established enterprise, PCI-DSS, SOX, and multiple regulatory frameworks
- **Starting point:** Official policy was "no AI tools." Informal usage happening on personal devices.

## Challenge

- Regulatory pressure: PCI-DSS scope code cannot leave the network
- Security team had blanket ban; developers frustrated and using personal devices
- Board asking "what's our AI strategy?" — leadership needed an answer
- Talent attrition: losing developers to companies that allow AI tools
- Complex approval process: 6 months for any new tool (normal procurement)

## Approach

### Month 1–3: Building the Foundation

- **Executive sponsorship secured:** CTO championed with CISO and General Counsel
- **Cross-functional working group:** Engineering + Security + Legal + Compliance + Risk
- **Data classification exercise:** All 200+ repositories classified (70% Internal, 25% Restricted, 5% Public)
- **Vendor evaluation:** Formal RFP process evaluating Copilot Enterprise, Amazon Q, and self-hosted options
- **Policy drafted:** Comprehensive AI acceptable use policy through legal review

**Key decision:** Approved Copilot Enterprise for Internal-classified code. Restricted code remains off-limits for cloud AI. Evaluated self-hosted options for future.

### Month 4–6: Controlled Pilot

- **Pilot scope:** 30 engineers across 4 teams (deliberately diverse: Java backend, Python ML, frontend, platform)
- **Controls implemented:** SSO integration, content exclusion for all Restricted repos, audit logging to SIEM
- **Compliance documentation:** Full paper trail for PCI-DSS auditor
- **Metrics baseline:** 6 weeks of data before AI tool access granted
- **Cost:** ~$1,200/month (30 × $39/user Enterprise tier)

### Month 7–9: Phased Expansion

- **Wave 1:** 100 engineers (teams with Internal-only code)
- **Wave 2:** 200 more engineers (expanding to teams with mixed Internal/Restricted — content exclusion enforced)
- **Governance committee formed:** Monthly review of usage patterns, incidents, and policy adjustments
- **Training program launched:** Mandatory 1-hour awareness session + optional 2-hour workshop

### Month 10–14: Enterprise Scale

- **Full rollout:** 600+ engineers with access (remaining teams in Restricted-only codebases excluded from cloud tools)
- **Self-hosted pilot:** Evaluating local model deployment for Restricted code (using open-source models)
- **Enterprise agreement:** 3-year contract with volume pricing negotiated ($32/user/month at scale)
- **Annual tool cost:** ~$230K/year for 600 seats
- **Audit passed:** PCI-DSS assessor reviewed AI tool usage documentation, no findings

## Results

| Metric | Baseline | After 14 months | Change |
|--------|----------|-----------------|--------|
| Developers with AI access | 0 (official) | 600/800 (75%) | From ban to enablement |
| PR cycle time (teams with access) | 42 hours | 30 hours | 29% faster |
| Deployment frequency | 3/week per team | 4.5/week per team | 50% increase |
| Bug introduction rate | Baseline | -8% | Improved (more test generation) |
| Security incidents (AI-related) | 0 | 0 | Clean record |
| Compliance findings (AI-related) | N/A | 0 | Audit-clean |
| Developer attrition (eng) | 18%/year | 12%/year | 6-point improvement |
| New hire offer acceptance rate | 72% | 84% | AI tools mentioned as differentiator |
| Annual AI tool cost | $0 | ~$230K | Investment |
| Estimated annual value (productivity) | $0 | ~$1.2M (conservative) | 5.2x ROI |

## Lessons Learned

### What Worked

1. **Security as co-pilot, not blocker** — CISO was co-sponsor from day one. Security designed the guardrails collaboratively.
2. **Compliance-first approach** — Having paper trail ready before auditors asked made the conversation easy.
3. **Content exclusion as the enabler** — "You can use AI for everything except Restricted repos" was simple to understand and enforce.
4. **Patient timeline** — 14 months felt slow but built unshakeable organizational confidence. No incidents because nothing was rushed.
5. **Talent retention argument** — Framing as "we're losing developers because we ban AI" got executive attention fast.
6. **Self-hosted for Restricted code** — Acknowledging that some code can never go to cloud AI (and planning an alternative) showed security team they were heard.

### What They'd Do Differently

1. **Start vendor engagement earlier** — Enterprise procurement took 3 months. Should have started RFP in month 1 alongside policy work.
2. **Smaller working group initially** — 12-person cross-functional group was slow to make decisions. Should have been 5 people with authority, expanding later.
3. **Developer communication earlier** — Engineers heard "no AI" for 6 months before hearing "actually, we're working on it." Should have communicated intent earlier, even without timeline.
4. **Don't exclude teams entirely** — Teams in Restricted-only codebases felt left out. Should have offered at least chat/explanation features (non-code-sending) from the start.
5. **Budget for champions from the start** — Champions emerged organically but had no time allocation. Should have been explicit: "10% of your time is enablement."

### What Made Enterprise Different

| Challenge unique to enterprise | How they solved it |
|-------------------------------|-------------------|
| Multi-month procurement process | Started early, ran in parallel with policy work |
| Multiple regulatory frameworks | Single policy covering all, with per-framework exceptions |
| 50+ teams with different needs | Phased rollout with team-level opt-in |
| Mixed compliance environments | Content exclusion + data classification as enforcement |
| Audit requirements | Documented everything from day one |
| Large-scale cost | Negotiated volume pricing, phased spending |
| Organizational inertia | Executive sponsorship + talent retention framing |

## Applicable If...

This pattern fits your organization if:
- Large enterprise (500+ engineers)
- Regulatory requirements (PCI, HIPAA, SOX, FedRAMP)
- Formal procurement and vendor management processes
- Security team has significant influence/veto power
- Mixed code sensitivity (some code can use cloud AI, some cannot)
- Long planning horizons are acceptable

This pattern does NOT fit if:
- Small team that can move fast informally
- No regulatory constraints
- Need results in weeks, not months
- Single-tier code sensitivity (everything is the same classification)

---

## Next

- Small team approach → [Startup Case Study](./startup-ai-first.md)
- Mid-size approach → [Mid-Size Case Study](./midsize-governance.md)
- Security controls in detail → [Security](../security/)
