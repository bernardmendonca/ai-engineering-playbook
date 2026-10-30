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
| Developer fully-loaded cost | $150,000/year | Industry average for experienced dev (US-market assumption — adjust for your region) |
| Hourly cost (2,000 hrs/year) | $75/hour | |
| Time saved per developer per day | 30 minutes | Conservative; studies show 30–90 min |
| Working days per year | 220 | |
| Annual time saved per developer | 110 hours | 30 min × 220 days |
| Value of saved time per developer | $8,250/year | 110 hours × $75/hour |
| Tool cost per developer (💰 team tier) | $2,400–5,000/year | Range across tools and tiers |
| **Net value per developer** | **$3,250–5,850/year** | After tool cost |
| **ROI** | **65–240%** | Net value / tool cost |

> **On the "Source" column:** Where this table says "industry average" or "studies show," treat that as a starting assumption to validate, not a citation — no specific study is named here, and published estimates for time-saved-per-day vary widely by task type and methodology. Use this model for your *initial* pitch only. Once you have pilot data, replace every row with your own measured numbers (see "The Honest Model" in [Investment Strategy](../ai-strategy/investment-strategy.md)) — that's the version worth defending to a skeptical executive.

### What the Evidence Says About These Inputs

The weakest row in this model is "time saved per developer per day." Three findings should shape how you use it (details in [What the Research Says](../productivity/what-the-research-says.md)):

- **Self-reported time savings overstate reality.** In METR's 2025 randomized trial, developers believed they were ~20% faster with AI when they were 19% slower. Don't fill this row from a survey.
- **Individual output gains don't automatically become delivery gains.** Faros' 2025 telemetry across 10,000+ developers found 98% more merged PRs, 91% longer review times, and flat organization-level delivery. Saved minutes only count if review, testing, and release can absorb the extra work.
- **There's a cost line most models miss.** DORA's 2026 ROI report calls it the "verification tax": reviewer time, test automation, and CI capacity to handle more code. It also models AI-driven instability as a cost (its sample calculator shows a negative downtime impact when change failure rate rises from 5% to 6%).

**A better approach:** Use [DORA's ROI calculator](https://dora.dev/ai/roi/report/) with your own pilot data, and run three scenarios (conservative, realistic, optimistic). DORA's illustrative 500-engineer organization returns about 39% in year one with an ~8-month payback, and the authors call it a high-uncertainty estimate. That's a more defensible anchor than the 65–240% range above.

### At Scale (100 developers, 💰 team/enterprise tier)

| | Conservative | Moderate | Optimistic |
|---|---|---|---|
| Time saved/dev/day | 30 min | 45 min | 60 min |
| Annual value (100 devs) | $825,000 | $1,237,500 | $1,650,000 |
| Tool cost (100 devs) | $150,000–350,000 | $150,000–350,000 | $150,000–350,000 |
| Net annual value | $475,000–675,000 | $887,500–1,087,500 | $1,300,000–1,500,000 |

*Tool cost range reflects a 100-developer org sitting in the middle of the [50–200 dev "mid-size" band](../ai-strategy/investment-strategy.md) — see that page for the full breakdown including enablement FTE.*

> **Important:** These numbers assume time saved translates to value. In practice, "saved time" might mean more features shipped, fewer bugs, faster onboarding, or reduced overtime — not headcount reduction. Frame accordingly.

---

## What Executives Will Ask (And Your Answers)

### "Will this replace developers?"

**Answer:** No. It makes developers more productive — they produce more output per hour, handle broader scope, and spend less time on repetitive work. Headcount needs are driven by your roadmap ambition, not your tool efficiency. DORA's 2026 ROI report explicitly argues against headcount reduction as the goal: retaining and retraining staff preserves institutional knowledge and costs less than rehiring it later.

**Be ready for the follow-up about juniors.** Stanford's payroll research (August 2026) finds employment of 22–25-year-olds in AI-exposed occupations, software development included, running about 19% below trend. Cutting junior hiring saves money now and leaves you without mid-level engineers in three to five years. See [Upskilling](../team-adoption/upskilling.md#the-junior-pipeline).

### "What's the security risk?"

**Answer:** Real but manageable. Code is sent to third-party AI services (similar to how code goes to GitHub, CI/CD providers, or cloud hosting). Enterprise tiers offer contractual guarantees: no training on your code, data encryption, SOC 2 compliance. Self-hosted options exist for highest-sensitivity code. [See our security section.](../security/)

### "What if we do nothing?"

**Answer:** Your competitors are adopting. Developer expectations are shifting — candidates increasingly expect AI tools. Productivity gap compounds over time. Doing nothing isn't risk-free; it's choosing the risk of falling behind over the risk of adoption.

### "How quickly will we see results?"

**Answer:** Expect a J-curve. Developers feel faster within weeks, but team and delivery metrics often dip first while workflows adapt: people learn the tools, reviewers absorb more code, and testing and release processes catch up. DORA's 2026 ROI research describes this dip as normal and warns against pulling funding during it. Plan to show leading indicators (adoption, sentiment, review latency) in the first quarter and delivery and quality results by the second. DORA's illustrative model pays back in about eight months.

### "What's the total cost?"

**Answer:** For a 100-developer org: 💰 $150K–350K/year in tool costs (comparable to your CI/CD or observability spend), plus roughly 0.5–1 FTE for enablement and governance. Total: $200K–450K/year — consistent with the [mid-size band in Investment Strategy](../ai-strategy/investment-strategy.md) — for an estimated $825K–1.65M in productivity value (see the table above). Note these dollar figures assume US-market costs; adjust proportionally for your region.

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

Don't ask for the full budget upfront. Propose a phased approach that de-risks the investment. *(This is the same phasing framework as [Investment Strategy's Phased Investment section](../ai-strategy/investment-strategy.md#phased-investment-de-risking) — the version below is scoped to a 100-developer example for the executive pitch; see that page for the org-size-general breakdown.)*

**Phase 1 (Month 1–2): Exploration — 🆓 $0**
- Individual developers explore free tiers
- Leader builds hands-on experience
- Deliverable: Informed recommendation

**Phase 2 (Month 2–4): Pilot — 💰 $5K–10K**
- One team on paid tier (6–8 seats)
- Measure impact against baseline
- Deliverable: Data-driven recommendation to expand or stop

**Phase 3 (Month 4–8): Expansion — 💰 $50K–100K annualized**
- Multiple teams, standardized tool
- Governance in place
- Deliverable: Proven playbook, ROI data for org-wide decision

**Phase 4 (Month 8+): Org-wide — 🏢 $200K–450K annualized (for 100 devs — see [Investment Strategy](../ai-strategy/investment-strategy.md) for the full org-size breakdown)**
- Enterprise agreement
- Full governance and support
- Deliverable: Sustained productivity improvement

Each phase has a clear go/no-go gate. This makes it an easy "yes" — you're only asking for Phase 1 approval today.

> ✅ **My take:** Always present Phase 1 (exploration) as $0 and Phase 2 (pilot) as a single budget request. Don't present the full Phase 4 number upfront — it scares executives into "no" before they've seen evidence. The phased approach is not just de-risking; it's a sales technique. Get the small "yes," deliver evidence, then ask for more. This is a pattern observed anecdotally across pitches, not a benchmarked statistic — see [Investment Strategy](../ai-strategy/investment-strategy.md) for the fuller version of this argument.

---

## One-Page Executive Summary (Template)

Use this structure for your exec presentation:

```
TITLE: Developer AI Tools Investment Proposal

THE ASK: $[X] for Phase [N] — [tool name] for [N developers] for [N months]

THE PROBLEM:
- Our developers spend ~40% of time on repetitive, low-value coding tasks
- Industry peers are adopting AI tools; independent research (DORA, METR) shows real gains where review, testing, and release processes are strong, and a temporary dip before them
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
