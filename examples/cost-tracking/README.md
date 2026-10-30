# Example: Cost Tracking

> Scripts and approaches for monitoring AI tool spend across your organization.

## Approach 1: Vendor Dashboard Export (Simplest)

Most AI tool vendors provide usage dashboards. Start here.

| Vendor | Cost | Dashboard location | Export option |
|--------|------|--------------------|-------------|
| GitHub Copilot | 💰🏢 | github.com → Organization → Copilot | CSV export, API |
| Kiro *(AWS's successor to Amazon Q Developer)* | 🆓💰 | AWS Console / kiro.dev | Usage dashboard, CloudWatch metrics |
| Anthropic (API) | 💰 | console.anthropic.com → Usage | API, CSV |
| OpenAI (API) | 💰 | platform.openai.com → Usage | API, CSV |
| Cursor | 💰🏢 | cursor.com → Team settings | Dashboard only |

---

## Approach 2: API-Based Cost Tracking Script

For token-based tools (Anthropic/OpenAI API), track costs programmatically:

```python
#!/usr/bin/env python3
"""
ai-cost-tracker.py
Pulls AI API usage data and reports costs by team/project.

Prerequisites:
  pip install anthropic openai pandas

Usage:
  python ai-cost-tracker.py --month 2026-10 --output report.csv
"""

import os
from datetime import datetime, timedelta

# Pricing per 1M tokens, keyed by the exact model IDs that appear in your
# usage logs. Fill these in from each vendor's current pricing page:
# model versions and prices change every few months, so keep this table in
# config (or pull it from the vendor's API) rather than hardcoding it.
PRICING = {
    "<small-tier-model-id>": {"input": 0.0, "output": 0.0},
    "<mid-tier-model-id>":   {"input": 0.0, "output": 0.0},
    "<top-tier-model-id>":   {"input": 0.0, "output": 0.0},
}

def calculate_cost(model: str, input_tokens: int, output_tokens: int) -> float:
    """Calculate cost for a single API call."""
    if model not in PRICING:
        # Fail loudly: silently costing unknown models at $0 hides spend.
        raise KeyError(f"No pricing configured for model '{model}'")
    pricing = PRICING[model]
    input_cost = (input_tokens / 1_000_000) * pricing["input"]
    output_cost = (output_tokens / 1_000_000) * pricing["output"]
    return input_cost + output_cost

# Example: Parse API logs and calculate per-team costs
# In practice, you'd pull from your API proxy logs or vendor API
```

---

## Approach 3: Budget Alerts Configuration

### Anthropic API (via usage limits)
Set spending limits in the Anthropic console:
- Workspace monthly limit: $[X]
- Per-API-key daily limit: $[Y]
- Alert at 80% of limit

### AWS (for Kiro / Bedrock) 💰
```json
{
  "BudgetName": "AI-Tools-Monthly",
  "BudgetLimit": {
    "Amount": "5000",
    "Unit": "USD"
  },
  "NotificationsWithSubscribers": [
    {
      "Notification": {
        "NotificationType": "ACTUAL",
        "ComparisonOperator": "GREATER_THAN",
        "Threshold": 80
      },
      "Subscribers": [
        {"SubscriptionType": "EMAIL", "Address": "eng-leads@company.com"}
      ]
    }
  ]
}
```

---

## Approach 4: Per-Developer Cost Awareness

Create a simple Slack bot or weekly report showing:

```
Weekly AI Cost Report — Week of Jun 16, 2025

Team totals:
  Platform:  $342 (8 devs, avg $42.75/dev)
  Frontend:  $187 (6 devs, avg $31.17/dev)
  Backend:   $256 (7 devs, avg $36.57/dev)
  Data:      $89  (4 devs, avg $22.25/dev)

Org total:   $874 (budget: $1,200 — 73% utilized)
Status:      ✅ On track

Outliers:
  ⚠️  dev-x: $127 (running large migration task — expected)
```

**Key principle:** Visibility, not gatekeeping. Developers should see their cost impact without feeling monitored. Report team-level, flag individual outliers only when unusual.

---

## 📋 Cost Optimization Checklist

- [ ] Use cheapest model that works for each task (Haiku for summaries, Sonnet for complex reasoning)
- [ ] Set per-session/per-day limits to prevent runaway costs
- [ ] Monitor for stuck agent loops (high token usage with no useful output)
- [ ] Right-size seat licenses (remove inactive users quarterly)
- [ ] Negotiate volume pricing at 50+ seats
- [ ] Track cost-per-PR and cost-per-feature for ROI calculation
- [ ] Budget alert at 80% of monthly allocation
