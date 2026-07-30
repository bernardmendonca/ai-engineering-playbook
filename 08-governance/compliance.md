# Compliance Considerations

> Navigating the regulatory landscape for AI in engineering — what to watch, what to do now.

## The Regulatory Landscape (2025)

Regulation is catching up to AI adoption. As a leader, you don't need to be a legal expert — but you need awareness of what's coming and how it affects your engineering practices.

### Key Regulations to Watch

| Regulation | Geography | Impact on engineering AI tools |
|-----------|-----------|-------------------------------|
| **EU AI Act** | EU | Classification of AI systems by risk. Developer tools likely "minimal risk" but must be transparent. |
| **US Executive Orders on AI** | US | Federal guidelines on safety and security. May influence procurement requirements. |
| **GDPR** (existing) | EU | Applies to any PII processed through AI tools. Data handling matters. |
| **SOC 2** (standard) | Global | AI tool vendors should be SOC 2 compliant. Your audit may ask about AI tool usage. |
| **Industry-specific** (HIPAA, PCI, FedRAMP) | Varies | May restrict which AI tools can touch regulated data/code. |

---

## What This Means for Engineering Leaders

### Low Urgency (Monitor)

- EU AI Act classification of developer tools (likely minimal risk)
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

---

## Industry-Specific Guidance

For detailed data classification frameworks (Public/Internal/Restricted tiers, repo-level classification, enforcement mechanisms, and file exclusion patterns), see [05 — Data Classification](../06-security/data-classification.md).

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
- Most AI coding tools are NOT yet FedRAMP authorized
- Amazon Q may have FedRAMP path via AWS GovCloud
- GitHub Copilot has GitHub Enterprise Server (self-hosted) option

---

## IP and Legal Considerations

### Code Ownership

| Question | Current consensus (2025) |
|----------|------------------------|
| Who owns AI-generated code? | The person/organization who prompted and directed it (in most jurisdictions) |
| Can AI-generated code be copyrighted? | Unclear — evolving legal landscape. Pure AI output may not be copyrightable. |
| Does using AI tools violate open-source licenses? | Generally no — using a tool doesn't change your code's license. |
| Can AI tools introduce copyleft contamination? | Theoretical risk — mitigated by IP indemnification from vendors. |

### Practical Actions

1. **Get IP indemnification** from your AI tool vendor (Copilot Enterprise and Q offer this)
2. **Document AI involvement** (protects against future disputes)
3. **Don't claim copyright on purely AI-generated work** without human creative contribution
4. **Review legal terms** of your AI tool agreement with counsel
5. **Monitor legal developments** — this area is evolving rapidly

---

## Compliance Readiness Checklist

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
- Security controls → [05 — Security](../06-security/)
