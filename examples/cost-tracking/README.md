# Example: Cost Tracking

> Scripts and approaches for monitoring AI tool spend across your organization.

## Approach 1: Vendor Dashboard Export (Simplest)

Most AI tool vendors provide usage dashboards. Start here.

| Vendor | Dashboard location | Export option |
|--------|-------------------|-------------|
| GitHub Copilot | github.com → Organization → Copilot | CSV export, API |
| Amazon Q | AWS Console → Q Developer | CloudWatch metrics |
| Anthropic (API) | console.anthropic.com → Usage | API, CSV |
| OpenAI (API) | platform.openai.com → Usage | API, CSV |
| Cursor | cursor.com → Team settings | Dashboard only |

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
  python ai-cost-tracker.py --month 2025-06 --output report.csv
"""

import os
from datetime import datetime, timedelta

# Pricing (update as vendors change prices)
PRICING = {
    "claude-3-5-sonnet": {"input": 3.00, "output": 15.00},  # per 1M tokens
    "claude-3-5-haiku": {"input": 0.25, "output": 1.25},
    "gpt-4o": {"input": 2.50, "output": 10.00},
    "gpt-4o-mini": {"input": 0.15, "output": 0.60},
}

def calculate_cost(model: str, input_tokens: int, output_tokens: int) -> float:
    """Calculate cost for a single API call."""
    if model not in PRICING:
        return 0.0
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

### AWS (for Amazon Q / Bedrock)
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

## Cost Optimization Checklist

- [ ] Use cheapest model that works for each task (Haiku for summaries, Sonnet for complex reasoning)
- [ ] Set per-session/per-day limits to prevent runaway costs
- [ ] Monitor for stuck agent loops (high token usage with no useful output)
- [ ] Right-size seat licenses (remove inactive users quarterly)
- [ ] Negotiate volume pricing at 50+ seats
- [ ] Track cost-per-PR and cost-per-feature for ROI calculation
- [ ] Budget alert at 80% of monthly allocation
