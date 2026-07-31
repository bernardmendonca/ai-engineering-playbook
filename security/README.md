# 05 — Security

> Threat models, data privacy, supply chain risks, and compliance for AI in engineering.

## Why This Section Matters

Security is the most common blocker for AI adoption in enterprise environments — and rightfully so. But "no AI" is not a security strategy. It pushes usage underground. This section covers real risks, practical mitigations, and how to build a security posture that *enables* adoption within safe boundaries.

## In This Section

| Page | What you'll learn |
|------|-------------------|
| [Threat Model](./threat-model.md) | What can go wrong — a structured view of AI-specific threats |
| [Data Classification](./data-classification.md) | What code can go where — frameworks for data handling decisions |
| [AI-Generated Code Risks](./generated-code-risks.md) | Vulnerabilities, license issues, and supply chain risks in AI output |
| [Enterprise Controls](./enterprise-controls.md) | Network, identity, DLP, and monitoring controls for AI tools |

## 💡 Key Insight

> **Security should enable AI adoption, not just block it.**
>
> A "no AI" policy is not a security strategy — it pushes usage underground where you have zero visibility. Build guardrails that let teams move fast within safe boundaries.

## Decision Framework: Cloud vs. Self-Hosted

```mermaid
flowchart TD
    A[AI tool evaluation] --> B{Does code leave your network?}
    B -->|No - self-hosted| C[Lower data risk<br/>Higher ops cost<br/>Lower model quality]
    B -->|Yes - cloud| D{What data is sent?}
    D --> E{Contains secrets/PII?}
    E -->|Yes| F[Block or redact before sending]
    E -->|No| G{IP-sensitive code?}
    G -->|Yes| H[Evaluate vendor DPA + training policy]
    G -->|No| I[Standard cloud usage with monitoring]
```

## Cost Context

| Security approach | Cost | Trade-off |
|------------------|------|-----------|
| Cloud AI with enterprise DPA | 💰 Standard enterprise pricing | Trust vendor, contractual protection |
| Cloud AI with proxy/DLP | 💰 Tool cost + proxy infra | Higher control, some latency |
| Self-hosted models | 🏢 GPU infra + ops team | Full control, lower model quality, high cost |
| No AI (prohibition) | 🆓 (nominally) | Hidden cost: shadow IT, talent attrition, competitive disadvantage |

## Status

🟢 Active — content being written and refined.

## AI Engineering Maturity: Security

> **Engineering Manager Note**
>
> "No AI" is not a security posture. It's an invitation to shadow IT.
>
> Your job is to give teams a safe path — not to block the road and hope they don't find a side street.

| Level | What it looks like | What to do |
|:-----:|-------------------|-----------|
| **0** | No policy — shadow IT with unknown tools | Acknowledge usage, begin data classification |
| **1** | Awareness only — developers know risks exist | Classify repos, remove secrets from code |
| **2** | Data classified, enterprise DPA signed, approved tool list | Content exclusion configured, basic audit in place |
| **3** | Enterprise controls active — SSO, audit logging, DLP | Proxy/gateway for inspection, anomaly alerting |
| **4** | Comprehensive — full monitoring, regular pen testing, compliance automated | Continuous improvement, threat model updated quarterly |
