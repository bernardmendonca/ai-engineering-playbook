# Dashboard Design

> Building metrics dashboards for different audiences — what to show, what to hide, and how to make data actionable.

## One Dashboard Doesn't Fit All

Different audiences need different views of the same underlying data:

| Audience | What they need | Refresh rate | Format |
|----------|---------------|-------------|--------|
| Platform/enablement team | All metrics, detailed, real-time | Daily | Full dashboard |
| Engineering managers | Team metrics, weekly trends | Weekly | Summary dashboard |
| VP/Director | Org metrics, monthly trends | Monthly | 1-page summary |
| C-suite/Board | ROI, strategic position | Quarterly | 3 slides max |

---

## Dashboard 1: Platform Team (Operational)

**Purpose:** Monitor adoption health, catch issues early, manage costs.

**Metrics displayed:**

```
┌─────────────────────────────────────────────────────┐
│ AI Tools Operational Dashboard                       │
├─────────────────────────────────────────────────────┤
│                                                     │
│  Active Users: 142/180 (79%)    Cost MTD: $4,231    │
│                                                     │
│  ┌──────────────┐  ┌──────────────┐                │
│  │ Adoption     │  │ Cost/User    │                │
│  │ Trend (12w)  │  │ Trend (12w)  │                │
│  │   ↗ 79%     │  │   → $29.80   │                │
│  └──────────────┘  └──────────────┘                │
│                                                     │
│  Top teams by usage:        Inactive licenses: 12   │
│  1. Platform (98%)          Cost outliers: 2 devs   │
│  2. Frontend (85%)          Errors today: 3         │
│  3. Backend (78%)                                   │
│  ...                                                │
│  8. Data (45%) ⚠️                                   │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Actions from this dashboard:**
- Low adoption team → investigate barriers, offer support
- High-cost outliers → check for stuck agent loops
- Inactive licenses → reclaim or reach out
- Error spikes → tool issue or configuration problem

---

## Dashboard 2: Engineering Manager (Team Health)

**Purpose:** Understand AI impact on team delivery and quality.

**Metrics displayed:**

```
┌─────────────────────────────────────────────────────┐
│ Team AI Impact — [Team Name]                         │
├─────────────────────────────────────────────────────┤
│                                                     │
│  PR Cycle Time      Deployment Freq    Bug Rate     │
│  18h (was 26h)      3.2/week (was 2.4)  Same ✅    │
│  ↓ 31% ✅          ↑ 33% ✅           Stable ✅   │
│                                                     │
│  Sprint Velocity: 34 pts (was 28)  ↑ 21% ✅        │
│  Developer Satisfaction: 4.1/5 (last quarter: 3.7)  │
│                                                     │
│  AI Usage:                                          │
│  - 6/8 team members active this week                │
│  - Top use cases: tests (40%), features (35%),      │
│    refactoring (25%)                                │
│                                                     │
│  ⚠️ Watch: Code review comments up 15%              │
│     (may indicate AI output needs more review)      │
│                                                     │
└─────────────────────────────────────────────────────┘
```

**Actions from this dashboard:**
- Quality metrics regressing → investigate, adjust AI usage patterns
- Low satisfaction → survey follow-up, tool training
- Velocity up + quality stable → success, share practices
- Some team members not using → check barriers (not a mandate to force)

---

## Dashboard 3: VP/Director (Org Summary)

**Purpose:** Monthly summary of AI impact across org. Supports budget decisions.

```
┌─────────────────────────────────────────────────────┐
│ AI Developer Tools — Monthly Report                  │
│ June 2025                                           │
├─────────────────────────────────────────────────────┤
│                                                     │
│  ADOPTION: 79% active (target: 70%) ✅              │
│  VELOCITY: PR cycle time ↓22% vs. baseline ✅       │
│  QUALITY:  Bug rate stable, CFR ↓5% ✅              │
│  COST:     $4,231/month ($29.80/active user) ✅     │
│  ROI:      Estimated 3.2x return on investment      │
│  SENTIMENT: 4.0/5 developer satisfaction            │
│                                                     │
│  KEY WINS:                                          │
│  - Platform team saved ~120 hours on Q2 migration   │
│  - Test coverage org-wide: 62% → 71%               │
│  - New hire onboarding: 3 weeks → 1.5 weeks        │
│                                                     │
│  ATTENTION:                                         │
│  - Data team adoption low (45%) — investigating     │
│  - Token costs trending up — monitoring             │
│                                                     │
│  RECOMMENDATION: Proceed with Phase 3 expansion     │
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## Data Sources

| Metric | Typical source | Tools |
|--------|---------------|-------|
| Adoption, usage, acceptance | AI tool vendor analytics | Copilot dashboard, Q dashboard, vendor API |
| PR cycle time, frequency | Git platform | GitHub Insights, GitLab analytics, LinearB, Sleuth |
| Deployment frequency | CI/CD platform | GitHub Actions, Jenkins, ArgoCD metrics |
| Bug rate, incidents | Issue tracker + incident tool | Jira, Linear, PagerDuty |
| Developer sentiment | Survey tool | Google Forms, Lattice, Culture Amp |
| Cost | Finance/billing | Vendor billing, AWS Cost Explorer |
| Sprint velocity | Project management | Jira, Linear, Shortcut |

---

## Implementation Approaches

### Minimal (Start Here)

- Spreadsheet updated weekly by one person
- Data pulled manually from tool dashboards
- Good enough for pilot and early expansion

**Cost:** 🆓 (1–2 hours/week of someone's time)

### Standard

- Automated data collection via APIs
- Dashboard tool (Grafana, Datadog, Looker)
- Updates daily or real-time

**Cost:** 💰 ($10–30/month for dashboard tooling + engineering setup time)

### Enterprise

- Unified data platform
- Automated alerts and anomaly detection
- Executive reporting pipeline
- Integration with HR/finance systems

**Cost:** 🏢 (Part of broader data/analytics platform investment)

---

## Next

- Reporting to different audiences → [Reporting to Leadership](./reporting.md)
- What metrics to track → [Metrics Framework](./metrics-framework.md)
- Productivity measurement methods → [06 — Measurement Approaches](../06-productivity/measurement-approaches.md)
