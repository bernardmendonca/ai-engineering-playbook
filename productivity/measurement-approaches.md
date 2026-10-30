# Measurement Approaches

> How to prove (or disprove) that AI tools are improving productivity — methods, pitfalls, and practical guidance.

## The Measurement Challenge

Measuring AI productivity impact is hard because:
- Many variables change simultaneously (team composition, project complexity, scope)
- The "control group" problem — you can't easily A/B test developer tools
- Hawthorne effect — being observed changes behavior
- Proxy metrics (PR count, lines of code) can mislead

Despite these challenges, you need measurement. Without it, you're guessing.

---

## Method 1: Before/After Comparison

**What:** Measure key metrics for 4–6 weeks before AI tool adoption, then same metrics for 4–6 weeks after.

**Metrics to track:**
- PR cycle time (open → merge)
- Deployment frequency
- Code review turnaround time
- Bug introduction rate (bugs found within 2 weeks of deploy)

**Advantages:** Simple, low overhead, uses existing data.

**Disadvantages:** Other variables may change simultaneously. Season effects. Team composition changes.

**When to use:** Pilot phase. Good enough for "directional signal" — not rigorous proof.

**Strengthening the method:**
- Control for team size and project complexity
- Note any other process changes during the period
- Use multiple metrics (if all point same direction, signal is stronger)

---

## Method 2: Cohort Comparison

**What:** Compare teams using AI tools vs. teams not using them (simultaneously).

**Advantages:** Controls for time-based confounders (same period, same company context).

**Disadvantages:** Teams are never truly equivalent. Selection bias (enthusiastic teams adopt first and may be inherently more productive).

**When to use:** Expansion phase when you have both adopting and non-adopting teams.

**Strengthening the method:**
- Match cohorts on: team size, seniority mix, project type, baseline metrics
- Acknowledge selection bias in findings
- Use as directional evidence, not definitive proof

---

## Method 3: Task Timing Studies

**What:** Time specific standardized tasks with and without AI tools.

**Examples:**
- "Implement pagination for endpoint X" — time with AI vs. without
- "Write unit tests for module Y" — time with AI vs. without
- "Investigate and fix bug Z" — time with AI vs. without

**Advantages:** High precision for specific task types. Controls most variables.

**Disadvantages:** Artificial setting. Hawthorne effect. Doesn't account for day-to-day variability. Time-consuming to run.

**When to use:** Evaluation phase when choosing between tools. Compelling for executive presentations ("same task took 45 min without, 18 min with").

---

## Method 4: Developer Experience Surveys

**What:** Regular surveys asking developers about their experience with AI tools.

**Questions to ask (quarterly):**

| Question | Scale | What it tells you |
|----------|-------|-------------------|
| "AI tools make me more productive" | 1–5 agree/disagree | Perceived value |
| "I trust AI-generated code quality" | 1–5 | Confidence level |
| "AI tools reduce my frustration with tedious tasks" | 1–5 | Toil reduction |
| "I spend less time on boilerplate than before" | 1–5 | Specific acceleration |
| "AI tools help me learn unfamiliar code faster" | 1–5 | Knowledge acceleration |
| "I would choose not to use AI tools" | 1–5 | Voluntary adoption signal |
| "What's the most useful thing AI helps you with?" | Open text | Use case discovery |
| "What's the most frustrating thing about AI tools?" | Open text | Improvement signals |

**Advantages:** Captures subjective experience, identifies issues quantitative metrics miss.

**Disadvantages:** Subjective, influenced by sentiment/hype. Not defensible alone for ROI claims. **Do not use survey answers as evidence of time saved:** in METR's 2025 randomized trial, developers estimated AI had made them ~20% faster when measured task time was 19% *longer*. Ask about friction, trust, and toil; measure speed from systems data. See [What the Research Says](./what-the-research-says.md).

**When to use:** Always. Run quarterly alongside quantitative metrics.

---

## Method 5: DORA Metrics Comparison

**What:** Track the five DORA software delivery metrics before and during AI adoption. DORA groups them into throughput and instability.

| DORA metric | Type | Expected AI impact | Why |
|-------------|------|-------------------|-----|
| Deployment frequency | Throughput | ↑ Increase | Faster implementation → more features ready to ship |
| Change lead time | Throughput | ↓ Decrease | Less time from commit to production |
| Failed deployment recovery time *(formerly MTTR)* | Throughput | → Stable or slight ↓ | AI-assisted debugging may help slightly |
| Change fail rate | Instability | → Should not increase | Rises if review discipline drops as volume grows |
| Deployment rework rate *(added 2024)* | Instability | → Should not increase | Share of deployments that are unplanned fixes for earlier ones — the most direct signal of AI-generated churn |

> **Watch instability, not just throughput.** DORA's 2024 report associated higher AI adoption with *lower* delivery stability, and the 2025 report found AI amplifies a team's existing strengths and weaknesses. If throughput rises while change fail rate or rework rate also rises, AI is producing work faster than your system can absorb it.

**Advantages:** Industry-standard metrics. Already tracked at many organizations. Meaningful to executives.

**Disadvantages:** Influenced by many factors beyond AI tools. Hard to attribute causally.

**When to use:** Org-wide phase. Long-term trending.

---

## What "Good" Looks Like

| Metric | Baseline (typical) | With AI (realistic target) | Exceptional |
|--------|--------------------|-----------------------------|-------------|
| PR cycle time (median) | 24–48 hours | 16–36 hours (15–25% ↓) | 12–24 hours |
| Deployment frequency | Weekly | 2–3× per week | Daily+ |
| Time to first commit (new dev) | 2–4 weeks | 1–2 weeks | First day |
| Developer satisfaction (AI tools) | N/A | 3.5/5 | 4.2+/5 |
| Change failure rate | 15–25% | ≤15% (should not increase) | <10% |

---

## ⚠️ Common Measurement Mistakes

| Mistake | Why it fails | Instead |
|---------|-------------|---------|
| Only measuring activity (PRs, commits) | Activity ≠ value. Gaming easy. Faros' 2025 telemetry saw merged PRs nearly double while org-level delivery stayed flat | Measure outcomes (features, quality, cycle time) |
| Ignoring review time and PR size | AI's extra output piles up in review first (Faros: review time +91%, PR size +154%) | Track review latency and PR size alongside throughput |
| No baseline before AI adoption | Can't prove improvement | Measure 4–6 weeks before introducing tools |
| Attributing all improvement to AI | Other factors change too | Acknowledge confounders, present as "correlated" not "caused" |
| Expecting immediate results | Learning curve takes 2–4 weeks | Measure after ramp-up period, not from day one |
| Measuring individual developers | Creates gaming, privacy concerns | Measure at team level |
| Ignoring quality metrics | Speed without quality is negative ROI | Always pair speed metrics with quality metrics |
| Single metric | Any single number can mislead | Dashboard of 4–6 metrics that together paint a picture |

---

## Presenting Results to Leadership

**For directors/VPs:**
- Lead with DORA metrics (they likely already track these)
- Show before/after trend lines
- Include developer sentiment alongside quantitative data
- Be honest about confounders

**For executives (C-level):**
- Lead with cost savings (time × hourly rate × developers)
- Show ROI calculation (value delivered ÷ tool cost)
- One or two compelling examples ("this migration took 2 days instead of 2 weeks")
- Keep it to one page with supporting appendix

**For the board:**
- One line: "Developer productivity tools delivering X% ROI based on Y months of data"
- Compare to industry benchmarks
- Frame as competitive advantage investment

---

## Next

- Full metrics framework → [Metrics](../metrics/)
- Business case framing → [Business Case](../foundations/business-case.md)
- Return to section overview → [README](./README.md)
