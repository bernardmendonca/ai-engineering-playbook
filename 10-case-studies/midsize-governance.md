# Case Study: Mid-Size — Balancing Speed and Governance

> A 150-engineer SaaS company adds AI tools while building governance that doesn't kill momentum.

## Context

- **Size:** 150 engineers across 12 teams
- **Industry:** B2B SaaS (HR tech)
- **Tech stack:** Java (backend), React (frontend), Kubernetes, AWS
- **Stage:** Growth stage, IPO-track, SOC 2 certified
- **Starting point:** 30–40 developers already using personal Copilot subscriptions (unsanctioned). Leadership aware but no official position.

## Challenge

- Shadow IT: developers using personal AI accounts with company code
- Security team uncomfortable with data going to uncontrolled services
- Executives asking "why aren't we using AI?" while security says "we can't approve it yet"
- Need to move fast enough to retain talent while being responsible enough for SOC 2 audit
- No budget line item for AI tools yet

## Approach

### Month 1: Acknowledge Reality, Start Small

- **Acknowledged shadow IT:** "We know some of you are using AI tools. We're going to make it official so you can do it safely."
- **Quick security review:** 2-week focused assessment of GitHub Copilot Business (their biggest shadow IT tool)
- **Immediate actions:** Approved Copilot Business for 3 volunteer teams. Enterprise DPA signed.
- **Data classification exercise:** 1-week sprint to classify repos (80% Internal, 15% Restricted, 5% Public)
- **Budget:** $3,000/month for pilot (15 seats × $19/month Copilot Business + buffer)

### Month 2–3: Structured Pilot

- **Three pilot teams selected:** Platform (complex infra), Growth (fast feature work), Mobile (different tech stack)
- **Baseline metrics captured** before giving teams access
- **Weekly check-ins:** 15-min standup with pilot leads
- **Champions identified:** 1 per pilot team, given extra training and direct line to platform team
- **Governance v1 written:** Lightweight acceptable use policy (1 page)

### Month 4–6: Expansion (First Attempt — Partially Failed)

- **What happened:** Tried to expand to all 12 teams simultaneously
- **Problem:** Support overwhelmed. Teams with complex legacy code struggled. Two teams had bad experiences and stopped using.
- **Course correction:** Pulled back to opt-in model. Let champions drive. Built self-serve docs.

### Month 4–6 (Corrected): Opt-In Expansion

- **Opened enrollment:** Teams sign up when ready, get champion + onboarding session
- **Support infrastructure:** Slack channel (#ai-tools), wiki, monthly office hours
- **Additional tool approved:** Claude Code for senior engineers doing complex refactoring ($2,000/month API budget)
- **Governance v2:** Expanded policy with agent-specific rules, cost limits, data classification enforcement

### Month 7–12: Steady Scaling

- **9 of 12 teams adopted** (3 teams opted out — respected)
- **Enterprise agreement signed:** Volume pricing, SSO integration, audit logging
- **Metrics dashboard automated:** Grafana dashboard pulling from GitHub, Jira, and Copilot analytics
- **SOC 2 audit passed** with AI tooling fully documented (auditor satisfied with governance)
- **Champions network formalized:** Monthly meetup, tip sharing, direct channel to leadership

## Results

| Metric | Baseline | After 12 months | Change |
|--------|----------|-----------------|--------|
| Official AI tool adoption | 0% (40% shadow) | 75% of eligible devs | From shadow to sanctioned |
| PR cycle time (median) | 32 hours | 24 hours | 25% faster |
| Deployment frequency | 8/week (org-wide) | 12/week | 50% increase |
| Sprint velocity (avg team) | 28 points | 34 points | 21% increase |
| Bug introduction rate | Baseline | Stable | No regression ✅ |
| New hire onboarding | 3.5 weeks | 2 weeks | 43% faster |
| Developer satisfaction (AI) | N/A | 3.9/5 | Strong |
| SOC 2 compliance | ✅ | ✅ (with AI docs) | Maintained |
| Monthly AI tool cost | $0 official | ~$8,500 | $56/active user/month |
| Shadow IT usage | ~40% unofficial | <5% unofficial | Dramatic reduction |

## Lessons Learned

### What Worked

1. **Acknowledging shadow IT instead of punishing** — Built trust immediately. Developers felt heard.
2. **Security review as enabler, not blocker** — Security team said "here's how to do it safely" not "no."
3. **Champions model over mandates** — Organic adoption through peer influence was sustainable.
4. **Opt-in expansion after the failed big-bang** — Respecting team autonomy led to better outcomes.
5. **Governance that grew with adoption** — v1 was 1 page. v2 was 3 pages. Matched to maturity level.
6. **SOC 2 preparation from the start** — Documenting governance early made audit smooth.

### What They'd Do Differently

1. **Never try big-bang expansion** — The failed simultaneous rollout to all teams wasted a month and created skeptics. Opt-in from the start.
2. **Champions training before expansion** — Champions were thrown into the deep end. Should have had 2 sessions with them before opening to their teams.
3. **Tool evaluation more carefully** — Initially picked a different tool that didn't integrate well with their Java ecosystem. Switched to Copilot after 3 weeks. Wasted evaluation time.
4. **Budget for API costs earlier** — Senior engineers hit personal API limits. Should have had team budgets from month 2.
5. **Include security team as champions** — They became allies eventually but were adversaries for the first 2 months. Early inclusion would have been better.

### The Failed First Expansion

This deserves emphasis because it's a common mistake:

**What happened:** After positive pilot results, leadership said "roll out to everyone next month." Platform team sent announcements, gave everyone access, and waited.

**What went wrong:**
- Teams without champions had nobody to ask questions
- Legacy Java teams hit limitations that pilot teams (on newer code) hadn't
- Support channel overwhelmed with basic questions
- Two teams had bad first experiences (wrong tasks for AI) and declared "this doesn't work"
- Those teams took 4 months to re-engage

**Key lesson:** Scaling requires support infrastructure, not just access. Access without support is setting teams up for failure.

## Applicable If...

This pattern fits your organization if:
- Mid-size (50–300 engineers) with some structure but not heavy bureaucracy
- SOC 2 or similar compliance requirement (but not extreme regulation)
- Shadow IT already happening (developers using unsanctioned AI tools)
- Mix of modern and legacy code (not all greenfield)
- Leadership supportive but needs data before committing budget

---

## Next

- Enterprise with heavy compliance → [Enterprise Case Study](./enterprise-compliance.md)
- Small team approach → [Startup Case Study](./startup-ai-first.md)
