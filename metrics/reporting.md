# Reporting to Leadership

> How to communicate AI adoption metrics to executives, boards, and peers — in their language.

## The Translation Problem

Engineers think in: PR cycle time, acceptance rates, token costs, DORA metrics.
Executives think in: revenue impact, competitive position, risk, ROI.

Your job is translation — not dumbing down, but reframing the same data in terms that resonate.

---

## Report Structure by Audience

### For Your Direct Manager (VP/Director)

**Frequency:** Monthly
**Format:** 1-page summary + detail appendix
**Focus:** Progress vs. plan, team impact, decisions needed

```
SUBJECT: AI Tools Monthly Update — [Month]

STATUS: On track / Attention needed / Exceeding expectations

KEY METRICS (vs. baseline):
• Adoption: X% (target: Y%)
• PR cycle time: X hours → Y hours (Z% improvement)
• Quality: Stable ✅ / Regressing ⚠️
• Cost: $X/month ($Y/user)

HIGHLIGHTS:
• [Specific win with numbers]
• [Specific win with numbers]

CONCERNS:
• [Issue + proposed action]

DECISION NEEDED:
• [If any — expand to Phase X? Increase budget? Change tool?]

NEXT MONTH:
• [What you'll focus on]
```

---

### For Executives (CTO, CEO, CFO)

**Frequency:** Quarterly
**Format:** 3 slides or 1 page
**Focus:** ROI, risk position, strategic recommendation

**Slide 1: The Headline**
```
AI Developer Tools — Q[X] Summary

Investment: $[X]/quarter
Estimated return: $[Y]/quarter (Z:1 ROI)
Risk status: Managed ✅
Recommendation: Continue / Expand / Adjust
```

**Slide 2: The Evidence**
```
PRODUCTIVITY:
• Developers shipping 20% more per sprint
• New features reaching production 25% faster
• New hire productivity in 1.5 weeks vs. 3 weeks

QUALITY:
• Bug rate: Stable (not increasing)
• Security: No AI-related incidents
• Customer impact: None negative

COST:
• $[X]/developer/month
• Comparable to [existing tool they understand — CI/CD, observability]
```

**Slide 3: What's Next**
```
NEXT QUARTER:
• Expand to [X more teams / whole org]
• Expected additional investment: $[X]
• Expected additional return: $[Y]

OR

DECISION REQUESTED:
• Approve enterprise agreement ($[X]/year)
• Expected ROI: [X]:1 based on pilot data
```

---

### For the Board

**Frequency:** Annually (or as part of technology strategy update)
**Format:** 1 paragraph in broader technology update
**Focus:** Strategic positioning, risk management

```
"We've deployed AI developer tools across [X%] of engineering.
Based on 6 months of measurement, we're seeing [X%] productivity
improvement at a cost of [$X/year] — a [X]:1 return on investment.
Security and quality metrics remain stable. This positions us
competitively in [market context]. We plan to [next step]."
```

That's it. The board doesn't need metrics details.

---

## Framing Techniques

### Don't Say → Say Instead

| Technical framing (don't) | Business framing (do) |
|--------------------------|----------------------|
| "PR cycle time decreased 25%" | "Features reach customers 25% faster" |
| "Acceptance rate is 32%" | "Developers find AI suggestions useful for ~1/3 of their work" |
| "We saved 110 hours per developer per year" | "Each developer has the equivalent of 3 extra weeks per year for new work" |
| "Token costs are $0.03 per request" | "AI tools cost $30/developer/month — less than their IDE license" |
| "DORA metrics improved" | "We ship more frequently with fewer failures" |

### The Comparison Anchor

Executives understand relative cost better than absolute:

| AI tool cost | Comparable tool they already pay for |
|-------------|--------------------------------------|
| $20/dev/month | Less than a JetBrains license ($25/mo) |
| $40/dev/month | Less than Datadog per-host pricing |
| $500K/year for 200 devs | Less than one senior developer hire |
| $1M/year for 500 devs | Less than your annual CI/CD infrastructure |

---

## The CFO Conversation

CFOs will ask different questions than CTOs:

| CFO asks | Your answer |
|----------|-------------|
| "What's the payback period?" | "Based on pilot: 2–4 months. Productivity gains exceed tool cost by month 3." |
| "Is this a one-time cost or recurring?" | "Recurring SaaS subscription. Scales linearly with headcount." |
| "What happens if we cancel?" | "Developers revert to pre-AI productivity levels. No sunk cost beyond subscription period." |
| "Can we capitalize this?" | "Typically OpEx (SaaS subscription). Check with accounting for your specific treatment." |
| "What's the risk of NOT doing this?" | "Competitors are adopting. Talent expects these tools. Gap compounds over time." |

---

## When Results Are Mixed

Not every quarter shows clear positive results. How to report honestly:

```
SCENARIO: Adoption high but productivity metrics flat

REPORT:
"AI tool adoption reached 75%, with strong developer satisfaction (4.0/5).
Productivity metrics (PR cycle time, deployment frequency) are stable but
haven't shown the improvement we expected. We believe this is because:
1. Teams are still in the learning curve (research shows 4-6 weeks to habit)
2. This quarter had unusual project complexity [specifics]

PLAN:
• Continue for one more quarter before concluding
• Increase training focus on high-impact use cases
• Re-measure against more stable project work next quarter

IF no improvement by [date]: Re-evaluate tool choice and approach."
```

**Key principle:** Honest reporting builds trust. Overpromising and underdelivering destroys it.

---

## ⚠️ Reporting Mistakes

| Mistake | Impact | Instead |
|---------|--------|---------|
| Cherry-picking only good metrics | Loses credibility when reality surfaces | Report balanced: wins + concerns |
| Technical jargon to executives | Eyes glaze, no decision made | Business language, anchored to money/time |
| No baseline comparison | "We're at 25h cycle time" means nothing without "was 34h" | Always show before/after or trend |
| Attributing everything to AI | Executives will be skeptical (rightly) | "Correlated with" not "caused by" — unless you ran a controlled study |
| Reporting too frequently | Data doesn't change week-to-week at exec level | Match frequency to decision cadence |
| No recommendation | Information without action is noise | Always end with "recommend" or "decision needed" |

---

## Next

- Metrics framework → [Metrics Framework](./metrics-framework.md)
- Dashboard layouts → [Dashboard Design](./dashboard-design.md)
- Business case framing → [Business Case](../foundations/business-case.md)
