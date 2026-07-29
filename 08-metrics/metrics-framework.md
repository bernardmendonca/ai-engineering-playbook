# Metrics Framework

> What to measure for AI adoption — organized by type, audience, and actionability.

## Metric Categories

### Leading Indicators (Early Signals)

These move first. They tell you whether adoption is happening and whether developers find value.

| Metric | What it measures | Source | Target |
|--------|-----------------|--------|--------|
| **Adoption rate** | Active weekly users / eligible users | Tool analytics | >70% after 3 months |
| **Suggestion acceptance rate** | % of AI suggestions accepted | Tool analytics | 25–35% (lower is normal) |
| **Agent tasks per developer/week** | How often devs use agent mode | Tool analytics | Trending upward |
| **Time-to-first-value** | Days from tool access to meaningful use | Onboarding tracking | <5 days |
| **Developer sentiment** | Survey: "AI tools make me more productive" | Quarterly survey | >3.5/5 |

### Lagging Indicators (Business Impact)

These take longer to move but tell the real story. Measure over 8+ weeks for meaningful signal.

| Metric | What it measures | Source | Expected change |
|--------|-----------------|--------|----------------|
| **PR cycle time** | Time from PR open → merge | Git analytics | 15–25% decrease |
| **Deployment frequency** | Deploys per team per week | CI/CD metrics | 10–20% increase |
| **Lead time for changes** | Commit → production time | DORA metrics | 15–25% decrease |
| **Bug introduction rate** | Bugs found within 14 days of deploy | Bug tracker | Should NOT increase |
| **Change failure rate** | % of deploys causing incidents | Incident tracking | Should NOT increase |
| **Onboarding time** | Days for new dev to first meaningful PR | HR/git data | 20–40% decrease |
| **Sprint velocity** | Story points / features per sprint | Project tracker | 10–20% increase |

### Quality Guardrails (Must Not Regress)

These are not goals — they're boundaries. If these get worse, AI adoption is net-negative.

| Metric | Acceptable range | Action if violated |
|--------|-----------------|-------------------|
| Bug introduction rate | ≤ baseline | Pause expansion, investigate |
| Change failure rate | ≤ baseline | Review AI-generated code quality |
| Security vulnerabilities | ≤ baseline | Add security checks to AI workflow |
| Test coverage | ≥ baseline | Ensure AI-generated code has tests |
| Code review rejection rate | ≤ baseline + 10% | Improve AI configuration/prompting |

### Cost Metrics

| Metric | What it measures | Source | Action threshold |
|--------|-----------------|--------|-----------------|
| **Cost per developer/month** | Total AI tool spend / active users | Finance | Track trend; budget ± 10% |
| **Cost per PR** | AI-related costs / PRs merged | Finance + git | Monitor for outliers |
| **Token cost by team** | API consumption by team | Tool analytics | Alert at >150% budget |
| **Inactive licenses** | Users with zero usage in 30 days | Tool analytics | Reclaim or investigate |
| **ROI ratio** | (Estimated value from productivity) / tool cost | Calculation | Should be > 2x |

---

## Measurement Cadence

| Frequency | What to measure | Who reviews |
|-----------|----------------|-------------|
| **Weekly** | Adoption rate, cost | Platform team / enablement |
| **Monthly** | PR cycle time, velocity, sentiment snapshot | Engineering managers |
| **Quarterly** | Full metrics review, ROI calculation, survey | VP/Director + leadership |
| **Annually** | Strategic review, vendor evaluation, budget planning | CTO / VP Engineering |

---

## Baseline: You Need One Before You Start

**Critical:** Measure your baseline *before* introducing AI tools. Without a baseline, you can't prove improvement.

Minimum baseline (4–6 weeks of data):
- [ ] PR cycle time (median and p90)
- [ ] Deployment frequency
- [ ] Bug introduction rate
- [ ] Developer satisfaction survey (even one data point)
- [ ] Sprint velocity (if using sprints)

---

## Metric Anti-Patterns

For detailed guidance on measurement *methods* (before/after studies, cohort comparison, task timing, surveys, DORA) and how to present results to different audiences, see [06 — Measurement Approaches](../06-productivity/measurement-approaches.md).

---

## Next

- Building dashboards → [Dashboard Design](./dashboard-design.md)
- Presenting to leadership → [Reporting to Leadership](./reporting.md)
- Measurement methods in depth → [06 — Measurement Approaches](../06-productivity/measurement-approaches.md)
