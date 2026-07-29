# Template: AI Tool Vendor Security Assessment

> Questions to ask AI tool vendors during procurement. Score each answer and determine overall risk.

---

## Assessment Context

| Field | Value |
|-------|-------|
| **Vendor** | [Vendor name] |
| **Tool/Product** | [Product name and tier] |
| **Assessed by** | [Name, role] |
| **Date** | [Date] |
| **Planned use** | [Brief description — e.g., "Code completion for 150 developers"] |
| **Data involved** | [What code/data will the tool process] |

---

## Section 1: Data Handling

| # | Question | Answer | Risk |
|---|----------|--------|:----:|
| 1.1 | Is customer code used to train or fine-tune models? | | ☐ |
| 1.2 | Where is code processed geographically? (data residency) | | ☐ |
| 1.3 | How long is code retained after processing? | | ☐ |
| 1.4 | Is code encrypted in transit and at rest? | | ☐ |
| 1.5 | What happens to our data if we terminate the contract? | | ☐ |
| 1.6 | Can we opt out of telemetry/usage data collection? | | ☐ |
| 1.7 | Do you offer a zero-retention option? | | ☐ |
| 1.8 | Can we exclude specific repositories/files from processing? | | ☐ |

**Acceptable answers:**
- 1.1: Must be "No" for enterprise use
- 1.2: Must meet our data residency requirements
- 1.3: Prefer zero retention; max 30 days acceptable
- 1.4: Must be "Yes" with details (TLS 1.2+, AES-256)
- 1.5: Must be "deleted within [X] days"

---

## Section 2: Security & Compliance

| # | Question | Answer | Risk |
|---|----------|--------|:----:|
| 2.1 | Do you hold SOC 2 Type II certification? (provide date) | | ☐ |
| 2.2 | Do you hold ISO 27001 certification? | | ☐ |
| 2.3 | Do you conduct annual third-party penetration testing? | | ☐ |
| 2.4 | Do you have a documented incident response process? | | ☐ |
| 2.5 | What is your breach notification timeline? (hours) | | ☐ |
| 2.6 | Do you have a bug bounty program? | | ☐ |
| 2.7 | Are you FedRAMP authorized? (if applicable) | | ☐ |
| 2.8 | Can you share your most recent penetration test summary? | | ☐ |

---

## Section 3: Access & Identity

| # | Question | Answer | Risk |
|---|----------|--------|:----:|
| 3.1 | Do you support SSO/SAML integration? | | ☐ |
| 3.2 | Do you support SCIM for user provisioning? | | ☐ |
| 3.3 | Can you enforce MFA? | | ☐ |
| 3.4 | Is there role-based access control for admin functions? | | ☐ |
| 3.5 | How are API keys/tokens managed and rotated? | | ☐ |
| 3.6 | Is automatic deprovisioning supported (offboarding)? | | ☐ |

---

## Section 4: Administration & Monitoring

| # | Question | Answer | Risk |
|---|----------|--------|:----:|
| 4.1 | Is there an admin dashboard with usage analytics? | | ☐ |
| 4.2 | Can audit logs be exported to our SIEM? | | ☐ |
| 4.3 | What events are logged? (list) | | ☐ |
| 4.4 | Can admins set organization-wide policies? | | ☐ |
| 4.5 | Can admins control which features are enabled/disabled? | | ☐ |
| 4.6 | Is there spend management / budget alerting? | | ☐ |

---

## Section 5: Legal & Contractual

| # | Question | Answer | Risk |
|---|----------|--------|:----:|
| 5.1 | Do you offer IP indemnification for generated code? | | ☐ |
| 5.2 | What are the terms for code ownership? | | ☐ |
| 5.3 | What is your SLA? (uptime guarantee) | | ☐ |
| 5.4 | What are contract termination terms? | | ☐ |
| 5.5 | Is a DPA (Data Processing Agreement) available? | | ☐ |
| 5.6 | Do you support custom contract terms for enterprise? | | ☐ |

---

## Section 6: Business Continuity

| # | Question | Answer | Risk |
|---|----------|--------|:----:|
| 6.1 | What is your disaster recovery approach? | | ☐ |
| 6.2 | What happens if the service is unavailable? (developer impact) | | ☐ |
| 6.3 | Do you provide status page and incident communication? | | ☐ |
| 6.4 | What is your planned support model for our tier? | | ☐ |

---

## Risk Summary

| Section | Risk Level | Notes |
|---------|:----------:|-------|
| Data Handling | ☐ Low ☐ Medium ☐ High | |
| Security & Compliance | ☐ Low ☐ Medium ☐ High | |
| Access & Identity | ☐ Low ☐ Medium ☐ High | |
| Administration | ☐ Low ☐ Medium ☐ High | |
| Legal | ☐ Low ☐ Medium ☐ High | |
| Business Continuity | ☐ Low ☐ Medium ☐ High | |

**Overall risk assessment:** ☐ Low ☐ Medium ☐ High ☐ Unacceptable

---

## Recommendation

☐ **Approve** — Acceptable risk for intended use
☐ **Approve with conditions** — [List conditions]
☐ **Reject** — Unacceptable risk. [Reason]
☐ **More information needed** — [What's missing]

**Assessed by:** [Name] | **Date:** [Date]
**Reviewed by:** [Security lead] | **Date:** [Date]
