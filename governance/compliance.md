# Compliance Considerations

> Navigating the regulatory landscape for AI in engineering — what to watch, what to do now.

## The Regulatory Landscape

> Last substantively reviewed mid-2026. This area moves fast — the EU AI Act timeline alone shifted by 16 months in a single legislative update this year. Re-verify dates before using this page to set a compliance deadline.

Regulation is catching up to AI adoption. As a leader, you don't need to be a legal expert — but you need awareness of what's coming and how it affects your engineering practices.

### Key Regulations to Watch

| Regulation | Geography | Impact on engineering AI tools |
|-----------|-----------|-------------------------------|
| **EU AI Act (as amended by the AI Omnibus, July 2026)** | EU | Classification of AI systems by risk. Developer tools likely "minimal risk" but must be transparent. High-risk obligations were delayed 16 months by the AI Omnibus — see below. |
| **US federal AI policy** | US | Currently deregulatory (EO 14179, Jan 2025), not a safety/security framework — see below. May still shape procurement in specific agencies. |
| **GDPR** (existing) | EU | Applies to any PII processed through AI tools. Data handling matters. |
| **SOC 2** (standard) | Global | AI tool vendors should be SOC 2 compliant. Your audit may ask about AI tool usage. |
| **Industry-specific** (HIPAA, PCI, FedRAMP) | Varies | May restrict which AI tools can touch regulated data/code. |

### EU AI Act: the Omnibus delay (update)

The EU's "AI Omnibus" (Regulation (EU) 2026/1744) entered into force July 27, 2026 and materially pushed out the AI Act's own timeline:

- **High-risk AI system obligations** (Annex III — e.g., employment, credit scoring, education, critical infrastructure) were delayed from Aug 2, 2026 to **Dec 2, 2027** (a 16-month delay).
- **Annex I high-risk obligations** (AI as a safety component of regulated products) were delayed to **Aug 2, 2028**.
- **Article 50 transparency obligations** (disclosure requirements for certain AI systems) were *not* delayed — they became generally applicable and enforceable **Aug 2, 2026**, with fines up to €15M or 3% of global turnover for non-compliance. If your tools or AI-assisted products fall under Article 50, this is not a "monitor" item.

Practical effect for most engineering orgs: developer tools (autocomplete, chat, coding agents) remain in the "likely minimal risk" category and are not directly caught by the high-risk provisions above. But don't treat "EU AI Act" as a single monolithic deadline — check which specific provisions apply to what you're building, since the timeline now varies by obligation type.

### US federal AI policy: correction

Contrary to how this section previously framed it, there is currently no unified US federal "safety and security" AI framework driving procurement requirements. The governing executive order since January 2025 is **EO 14179** ("Removing Barriers to American Leadership in AI"), which explicitly *revoked* the prior administration's safety-focused EO 14110 and is deregulatory/innovation-focused rather than a compliance framework. A planned cybersecurity-focused AI executive order was withdrawn before signing in 2026. Don't assume a stable federal safety baseline exists — if you sell into US federal customers, check current agency-specific procurement requirements directly rather than inferring them from a general federal AI policy, since the landscape is actively in flux and could shift again with a future administration.

---

## What This Means for Engineering Leaders

### Low Urgency (Monitor)

- EU AI Act classification of developer tools as "minimal risk" (still likely accurate, but re-check if you build AI-adjacent products, not just use AI dev tools)
- Potential future requirements for AI-generated code disclosure
- Evolving IP law around AI-generated works

### Medium Urgency (Prepare)

- Audit trail for AI tool usage (SOC 2 auditors are starting to ask)
- Data handling documentation for AI tools (GDPR, data residency)
- Vendor assessment including AI-specific questions

### High Urgency (Act Now)

- Data classification for what goes to AI services (PII, regulated data)
- Enterprise DPA with AI tool vendors (contractual protection)
- If in regulated industry: verify AI tools don't process regulated data inappropriately

---

## SOC 2 and AI Tools

SOC 2 auditors are increasingly asking:

| Question they'll ask | What they want to see |
|---------------------|----------------------|
| "Do developers use AI tools?" | Honest answer + documentation of which tools |
| "How is data handled by AI tools?" | Vendor DPA, no-training clause, data flow diagram |
| "Is there an acceptable use policy?" | Written policy (see [AI Usage Policy](./ai-usage-policy.md)) |
| "How do you monitor AI tool usage?" | Audit logging, access reviews |
| "Can AI tools access production data?" | Demonstrate isolation (they shouldn't) |

**Preparation:** If you have SOC 2 audit upcoming, document your AI tool usage now. Having a policy and vendor agreements in place turns this from a finding into a non-issue.

---

## GDPR Implications

If your development involves EU personal data:

| Scenario | GDPR concern | Mitigation |
|----------|-------------|-----------|
| Code that processes PII sent to AI tool | PII in transit to third party | Exclude PII-handling code from AI context, or verify vendor DPA covers this |
| AI tool processes developer data (telemetry) | Employee data processing | Include in privacy notice, verify vendor data handling |
| AI generates code that handles PII | Generated code must be GDPR-compliant | Standard code review applies — AI authorship doesn't change compliance requirements |
| Your data is processed by a US-hosted AI vendor | Cross-border transfer of EU personal data outside the EEA | Confirm the vendor relies on a valid transfer mechanism — Standard Contractual Clauses (SCCs) or, where applicable, an EU-US Data Privacy Framework certification/adequacy basis. Don't assume a DPA alone covers this: a DPA governs *how* data is processed, a transfer mechanism governs whether it can leave the EEA at all. Ask your vendor which mechanism they rely on and get it in writing. |

---

## Industry-Specific Guidance

For detailed data classification frameworks (Public/Internal/Restricted tiers, repo-level classification, enforcement mechanisms, and file exclusion patterns), see [Data Classification](../security/data-classification.md).

Below are the **compliance-specific** considerations that go beyond data classification:

### Healthcare (HIPAA)

- AI-assisted changes to PHI-handling code must follow same CM (change management) process
- Vendor BAA (Business Associate Agreement) may be required if vendor could access PHI
- Document AI tool usage in your HIPAA risk assessment

### Financial Services (PCI-DSS, SOX)

- Audit trail requirements align well with enterprise AI tool logging
- Change management documentation: AI-assisted changes must follow same CM process
- SOX-relevant systems: document AI involvement in financial system changes

### Government (FedRAMP)

- FedRAMP-scoped code: Only FedRAMP-authorized tools
- Most AI coding tools are still NOT FedRAMP authorized, but this is changing — GitHub shipped FedRAMP Moderate-authorized models with US/EU data residency directly in Copilot (April 2026), available to GitHub Enterprise Cloud customers, not just self-hosted GitHub Enterprise Server
- Kiro (AWS's successor to Amazon Q Developer) may have a FedRAMP path via AWS GovCloud — verify current authorization status directly with AWS before relying on it for FedRAMP-scoped work
- Check current authorization status for any tool before assuming coverage — this list changes faster than this page does

---

## IP and Legal Considerations

### Code Ownership

These are two genuinely different questions with different answers — don't conflate them:

| Question | What it's actually about | Current consensus |
|----------|--------------------------|-------------------|
| Who *owns* (contractually) AI-generated code? | A ToS/contract question between you and your AI tool vendor | Most vendor terms assign ownership/rights to the person or org who prompted and directed the output — this is a contractual grant, not a copyright determination |
| Can AI-generated code be *copyrighted*? | A legal/case-law question about authorship | Under current US Copyright Office guidance and case law (including the *Thaler* line of cases), copyright requires meaningful human creative control — prompting alone is generally insufficient. Output with substantial human editing/arrangement has a stronger claim than raw, unedited AI output. This is genuinely unsettled and evolving — don't treat "we own it contractually" as equivalent to "it's copyrightable." |
| Does using AI tools violate open-source licenses? | Generally no — using a tool doesn't change your code's license. |
| Can AI tools introduce copyleft contamination? | Theoretical risk — mitigated by IP indemnification from vendors (verify specific vendor commitments — coverage details vary and shouldn't be assumed). |

**Practical implication:** Your vendor agreement can tell you who has the *right* to use and license AI-generated code. It cannot tell you whether that code is *copyrightable* in the first place — that's a separate, unresolved legal question that depends on how much human creative judgment went into the final output. If copyrightability matters for a specific deliverable (e.g., code you plan to license commercially), get counsel involved rather than relying on the contractual ownership clause alone.

### Practical Actions

1. **Get IP indemnification** from your AI tool vendor (Copilot Enterprise and Q offer this)
2. **Document AI involvement** (protects against future disputes)
3. **Don't claim copyright on purely AI-generated work** without human creative contribution
4. **Review legal terms** of your AI tool agreement with counsel
5. **Monitor legal developments** — this area is evolving rapidly

---

## 📋 Compliance Readiness Checklist

- [ ] AI tool vendors assessed for compliance certifications (SOC 2, ISO 27001)
- [ ] Data Processing Agreements signed with AI tool vendors
- [ ] AI acceptable use policy written and communicated
- [ ] Data classification applied to repositories (what goes to AI, what doesn't)
- [ ] Audit logging enabled for AI tool usage
- [ ] Industry-specific requirements mapped to AI tool restrictions
- [ ] Legal review of AI tool terms of service completed
- [ ] IP indemnification confirmed in vendor contracts
- [ ] SOC 2 audit preparation includes AI tool documentation
- [ ] Quarterly compliance review scheduled

---

## Next

- Write your AI policy → [AI Usage Policy](./ai-usage-policy.md)
- Responsible AI practices → [Responsible AI](./responsible-ai.md)
- Security controls → [Security](../security/)
