# What the Research Says

> The controlled studies and large telemetry reports on AI and developer productivity — what they found, where they agree, and what that means for how you measure and pitch.

> **Last verified:** 2026-10-30 · **Re-check by:** 2027-01-30

## Why This Page Exists

Most AI productivity claims are self-reported ("it feels 30% faster") or come from vendors. Since mid-2025 there's a better evidence base: randomized trials, telemetry from thousands of developers, and DORA's large surveys. The findings are more mixed than the marketing, and they change how you should measure.

> This research moves fast and several studies below have already been revised by their own authors. Check for updates before quoting a number to leadership.

---

## The Key Studies

| Study | Method | Headline finding |
|-------|--------|-----------------|
| **METR (July 2025)** | Randomized trial: 16 experienced open-source developers, 246 tasks in their own repos, early-2025 tools | With AI allowed, tasks took **19% longer**. Developers predicted a 24% speedup beforehand and still believed they'd been ~20% faster afterward |
| **METR update (Feb 2026)** | Same design, 57 developers, 143 repos, 800+ tasks, late-2025 tools | Raw estimates now point to a speedup (returning developers ~18% faster, new developers ~4% faster), but both confidence intervals include a slowdown. METR calls the result **unreliable**: many developers refused to work without AI, so the study misses the heaviest users and the tasks with the biggest expected gains. METR believes real speedups in early 2026 are likely larger than in 2025 |
| **DORA 2024** | Annual survey of technology professionals | Each 25% increase in AI adoption was associated with a 1.5% drop in delivery throughput and a 7.2% drop in delivery stability, alongside gains in documentation quality, code quality, and review speed |
| **DORA 2025, *State of AI-assisted Software Development*** | ~5,000 respondents plus 100+ hours of interviews | 90% use AI at work; over 80% believe it made them more productive. AI is an **amplifier**: it magnifies strong and weak organizations alike. AI adoption is now associated with higher throughput but still with higher instability. Introduced the seven-capability [AI Capabilities Model](#the-dora-ai-capabilities-model) |
| **DORA, *ROI of AI-assisted Software Development* (2026.01)** | Financial model built on DORA research | Expect a **J-curve**: a temporary dip from the learning curve, the "verification tax" of reviewing AI output, and downstream processes catching up. Illustrative 500-engineer org: ~$11.6M first-year value against ~$8.4M investment (39% ROI, ~8-month payback), labeled by the authors as a high-uncertainty estimate. Explicitly discourages headcount reduction as the goal |
| **Faros AI, *The AI Productivity Paradox* (2025)** | Telemetry from 10,000+ developers across 1,255 teams | High-AI-adoption teams completed 21% more tasks and merged 98% more PRs, but PR review time rose 91%, PR size rose 154%, and bug counts rose 9%. Organization-level delivery metrics stayed flat |
| **Anthropic, *How AI Impacts Skill Formation* (Jan 2026)** | Randomized trial of developers learning a new async Python library | The AI-assisted group scored **17% lower** on a comprehension quiz (about 50% vs. 67%) and was not significantly faster on average. Developers who used AI to ask conceptual questions kept most of the learning; those who fully delegated learned least |
| **Stanford research cited in the DORA ROI report** | Productivity study across many companies | AI yields roughly 35–40% gains on simple greenfield tasks, but often 10% or less on complex legacy code |
| **Stanford Digital Economy Lab, *Canaries in the Coal Mine* (Aug 2026 update)** | Payroll data | Employment of workers aged 22–25 in AI-exposed occupations (including software development) is ~19% below where it would be had it tracked less-exposed peers; experienced workers show no comparable gap |

---

## Where the Evidence Agrees

### 1. Self-reported speedups are unreliable

METR's 2025 trial found a gap of roughly 40 percentage points between how fast developers *felt* and how fast they *were*. METR's own 2026 update still treats self-reports as untrustworthy. Surveys remain useful for sentiment and friction, but **not as evidence of time saved**.

### 2. Individual output rises; organizational delivery doesn't automatically follow

Faros saw nearly double the merged PRs with flat organization-level delivery. DORA describes "localized pockets of productivity" lost in downstream bottlenecks. The extra output piles up in review, testing, and deployment.

### 3. Instability is the cost to watch

DORA associated AI adoption with lower delivery stability in both 2024 and 2025. Faros saw larger PRs and more bugs. More code moving faster strains review and release processes unless those processes change too.

### 4. The organizational system determines the return

DORA's seven capabilities, its J-curve, and the Faros data all point the same way: the payoff depends on version control discipline, small batches, test automation, internal platforms, and review capacity, not on which tool you buy.

### 5. Gains depend heavily on the work

Greenfield and well-specified tasks gain the most; complex legacy code gains far less. An org-wide average hides this, so measure by work type.

### 6. Speed and learning can trade off

When developers are learning something new, delegating to AI reduces what they learn. This matters most for juniors and for anyone who will later have to debug or review the code. See [Upskilling](../team-adoption/upskilling.md#learning-with-ai-not-instead-of-it).

---

## The DORA AI Capabilities Model

DORA's 2025 research identified seven capabilities that determine whether AI amplifies a team's effectiveness or its problems:

| Capability | What it means in practice | Where this playbook covers it |
|-----------|---------------------------|-------------------------------|
| Clear and communicated AI stance | Developers know what's allowed, expected, and supported | [AI Usage Policy](../governance/ai-usage-policy.md) |
| Healthy data ecosystems | Internal data is high quality, accessible, and unified | [Knowledge Architecture](../ai-engineering-practices/knowledge-architecture.md) |
| AI-accessible internal data | AI tools can reach your docs, codebases, and conventions | [Context Engineering](../ai-engineering-practices/what-is-context-engineering.md) |
| Strong version control practices | Frequent commits, easy rollback, clean history | [Governing Agents](../ai-coding-agents/governing-agents.md) |
| Working in small batches | Small, frequent changes rather than large drops | [Code Review at Agent Scale](../engineering-workflows/code-review.md#reviewing-at-agent-scale) |
| User-centric focus | Teams stay oriented to user outcomes, not output volume | [Defining Productivity](./defining-productivity.md) |
| Quality internal platforms | Self-service tooling, paved paths, fast CI | [Harness Engineering](../ai-engineering-practices/harness-engineering.md) |

---

## What This Means for You

### For measurement

- **Pair every throughput metric with an instability metric.** Track change fail rate and deployment rework rate alongside PR volume and lead time. See [Measurement Approaches](./measurement-approaches.md).
- **Measure review time and PR size.** These are where AI's extra output shows up first.
- **Don't count PRs or lines of code as success.** Faros' data shows PR counts can nearly double while delivery stays flat.
- **Segment by work type.** Report greenfield, maintenance, and legacy work separately.
- **Use surveys for sentiment, not speed.**

### For the business case

- **Plan for the J-curve.** Tell leadership up front that the first months may show a dip in delivery metrics while workflows adapt, so a dip isn't read as failure and defunded. See [Business Case](../foundations/business-case.md).
- **Budget for the verification tax.** Reviewer time, test automation, and CI capacity are part of the cost of AI adoption.
- **Frame the return as capacity, not headcount.** DORA's ROI report argues against headcount reduction; so do the skill-formation and junior-pipeline findings.
- **Use DORA's ROI calculator and run three scenarios** (conservative, realistic, optimistic) with your own pilot data instead of industry averages.

> ✅ **My take:** The honest summary for an executive is: "AI reliably increases how much code we produce. Whether that becomes faster delivery depends on our review, testing, and release systems, and we'll know within two quarters." That's defensible against every study on this page. "AI makes developers 50% faster" is not.

---

## Sources

- METR, [Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) (July 2025)
- METR, [We are Changing our Developer Productivity Experiment Design](https://metr.org/blog/2026-02-24-uplift-update/) (February 2026)
- DORA, [State of AI-assisted Software Development 2025](https://dora.dev/) and [Balancing AI tensions](https://dora.dev/insights/balancing-ai-tensions/)
- DORA, [ROI of AI-assisted Software Development](https://dora.dev/ai/roi/report/) (2026.01); summary in [InfoQ](https://www.infoq.com/news/2026/05/dora-roi-ai-assisted-dev-report)
- Faros AI, The AI Productivity Paradox (2025), summarized on the [Faros blog](https://www.faros.ai/blog/why-cheaper-ai-models-can-cost-more-hidden-model-tax)
- Shen et al. (Anthropic), [How AI Impacts Skill Formation](https://arxiv.org/abs/2601.20245) (January 2026)
- Stanford Digital Economy Lab, [Canaries in the Coal Mine — August 2026 update](https://digitaleconomy.stanford.edu/news/canariesaug26/)

*Findings are paraphrased from the sources above.*

---

## Next

- Turning this into metrics → [Measurement Approaches](./measurement-approaches.md)
- Where AI helps most, by task → [What AI Accelerates](./what-ai-accelerates.md)
- Pitching with realistic numbers → [Business Case](../foundations/business-case.md)
