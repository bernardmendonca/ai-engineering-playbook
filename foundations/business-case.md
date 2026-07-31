# The Business Case for AI in Engineering

> How to frame AI investment for executive audiences — in their language, with their concerns.

## The Executive Conversation

Executives don't care about token counts or model architectures. They care about:
- **Cost** — How much does this cost and what's the return?
- **Risk** — What could go wrong?
- **Speed** — When do we see results?
- **Competition** — What happens if we don't do this?

Frame your business case around these four axes.

---

## Framing: Not "AI Experiment" — "Developer Tooling Investment"

**Wrong framing:** "We want to invest in AI because it's the future."

**Right framing:** "We want to invest in developer tooling that reduces time-to-market by 15–25%, based on pilot data and industry benchmarks."

AI coding tools belong in the same budget category as:
- IDE licenses
- CI/CD infrastructure
- Observability tools
- Developer experience platforms

They're not an R&D experiment. They're a productivity tool with measurable ROI.

---

## The ROI Model

### Conservative Estimate

| Variable | Conservative value | Source |
|----------|-------------------|--------|
| Developer fully-loaded cost | $150,000/year | Industry average for experienced dev |
| Hourly cost (2,000 hrs/year) | $75/hour | |
| Time saved per developer per day | 30 minutes | Conservative; studies show 30–90 min |
| Working days per year | 220 | |
| Annual time saved per developer | 110 hours | 30 min × 220 days |
| Value of saved time per developer | $8,250/year | 110 hours × $75/hour |
| Tool cost per developer | $2,400–5,000/year | Range across tools and tiers |
| **Net value per developer** | **$3,250–5,850/year** | After tool cost |
| **ROI** | **65–240%** | Net value / tool cost |

### At Scale (100 developers)

| | Conservative | Moderate | Optimistic |
|---|---|---|---|
| Time saved/dev/day | 30 min | 45 min | 60 min |
| Annual value (100 devs) | $825,000 | $1,237,500 | $1,650,000 |
| Tool cost (100 devs) | $240,000–500,000 | $240,000–500,000 | $240,000–500,000 |
| Net annual value | $325,000–585,000 | $737,500–997,500 | $1,150,000–1,410,000 |

> **Important:** These numbers assume time saved translates to value. In practice, "saved time" might mean more features shipped, fewer bugs, faster onboarding, or reduced overtime — not headcount reduction. Frame accordingly.

---

## What Executives Will Ask (And Your Answers)

### "Will this replace developers?"

**Answer:** No. It makes developers more productive — they produce more output per hour, handle broader scope, and spend less time on repetitive work. Headcount needs are driven by your roadmap ambition, not your tool efficiency. Teams that adopt AI typically ship more, not hire less.

### "What's the security risk?"

**Answer:** Real but manageable. Code is sent to third-party AI services (similar to how code goes to GitHub, CI/CD providers, or cloud hosting). Enterprise tiers offer contractual guarantees: no training on your code, data encryption, SOC 2 compliance. Self-hosted options exist for highest-sensitivity code. [See our security section.](../security/)

### "What if we do nothing?"

**Answer:** Your competitors are adopting. Developer expectations are shifting — candidates increasingly expect AI tools. Productivity gap compounds over time. Doing nothing isn't risk-free; it's choosing the risk of falling behind over the risk of adoption.

### "How quickly will we see results?"

**Answer:** Individual productivity gains are immediate (first week). Team-level metrics improve in 4–6 weeks. Org-wide ROI is demonstrable in 3–6 months. This isn't a multi-year R&D bet — it's a tool with fast feedback loops.

### "What's the total cost?"

**Answer:** For a 100-developer org: $240K–500K/year in tool costs (comparable to your CI/CD or observability spend). Plus ~0.5 FTE for enablement and governance. Total: $300K–600K/year for estimated $800K–1.6M in productivity value.

---

## The Risk of Inaction

| Risk | Impact | Likelihood |
|------|--------|-----------|
| Developers use unapproved tools (shadow IT) | Security exposure, no governance | High — already happening at most orgs |
| Talent attrition (developers want AI tools) | Recruitment/retention disadvantage | Medium-High — becoming a hiring differentiator |
| Competitors ship faster | Market position erosion | Medium — depends on industry |
| Technical debt accumulates faster | Slower future development | Medium — AI helps address this, absence compounds it |

---

## Phased Investment Approach

Don't ask for the full budget upfront. Propose a phased approach that de-risks the investment:

**Phase 1 (Month 1–2): Exploration — $0**
- Individual developers explore free tiers
- Leader builds hands-on experience
- Deliverable: Informed recommendation

**Phase 2 (Month 2–4): Pilot — $5K–10K**
- One team on paid tier (6–8 seats)
- Measure impact against baseline
- Deliverable: Data-driven recommendation to expand or stop

**Phase 3 (Month 4–8): Expansion — $50K–100K annualized**
- Multiple teams, standardized tool
- Governance in place
- Deliverable: Proven playbook, ROI data for org-wide decision

**Phase 4 (Month 8+): Org-wide — $250K–500K annualized (for 100 devs)**
- Enterprise agreement
- Full governance and support
- Deliverable: Sustained productivity improvement

Each phase has a clear go/no-go gate. This makes it an easy "yes" — you're only asking for Phase 1 approval today.

> ✅ ✅ **Our take: Always present Phase 1 (exploration) as $0 and Phase 2 (pilot) as a single budget request. Don't present the full Phase 4 number upfront — it scares executives into "no" before they've seen evidence. The phased approach is not just de-risking; it's a sales technique. Get the small "yes," deliver evidence, then ask for more. Executives who've seen pilot data say "yes" to expansion 80% of the time. Executives asked to fund a full rollout from nothing say "let me think about it" — which means "no."

---

## One-Page Executive Summary (Template)

Use this structure for your exec presentation:

```
TITLE: Developer AI Tools Investment Proposal

THE ASK: $[X] for Phase [N] — [tool name] for [N developers] for [N months]

THE PROBLEM:
- Our developers spend ~40% of time on repetitive, low-value coding tasks
- Industry peers are adopting AI tools and reporting 15-30% productivity gains
- We have no policy — developers are using unapproved tools with unknown security posture

THE SOLUTION:
- Deploy [tool] to [team/org] with appropriate governance
- Measured pilot showed [metrics from Phase 2]

EXPECTED OUTCOME:
- [X]% reduction in time-to-production for new features
- [X] hours saved per developer per week
- $[X] annual productivity value vs. $[Y] tool cost

RISK MITIGATION:
- Enterprise DPA signed — no code used for training
- Governance policy defined (acceptable use, data classification)
- Phased rollout with checkpoint at [date]

TIMELINE:
- [Phase] starts [date], results by [date]
- Go/no-go decision at [date]
```

---

## Next

- Ready to assess your org? → [Organizational Readiness](./org-readiness.md)
- Need to understand the tool landscape? → [AI Tools](../ai-tools/)
- Want governance frameworks? → [Governance](../governance/)
