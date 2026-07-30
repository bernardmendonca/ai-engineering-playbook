# Glossary

> Terms and acronyms used throughout this playbook — organized by category.

---

## Core AI & Engineering Terms

| Term | Definition |
|------|-----------|
| **AI** | Artificial Intelligence — in this playbook, refers specifically to generative AI used for software development (code generation, review, testing, documentation) |
| **LLM** | Large Language Model — the foundation model behind AI coding tools (GPT-4, Claude, Gemini, etc.) |
| **Agent** | An AI tool that can plan, execute multi-step tasks, run commands, and iterate on its own output autonomously |
| **MCP** | Model Context Protocol — an open standard for connecting AI tools to external data sources (databases, APIs, ticket systems) |
| **RAG** | Retrieval-Augmented Generation — a technique where AI retrieves relevant documents/data before generating a response, improving accuracy for domain-specific questions |
| **Context Engineering** | The discipline of structuring and delivering the right information to AI tools so they produce consistently useful output across an organization |
| **Steering** | Configuration files that provide persistent instructions to AI tools about project conventions, patterns, and rules |
| **Prompt Engineering** | The skill of writing effective instructions for AI tools in individual interactions |

---

## Development Process Terms

| Term | Definition |
|------|-----------|
| **PR** | Pull Request — a code change submitted for review before merging into the main branch |
| **CI/CD** | Continuous Integration / Continuous Deployment — automated pipelines that build, test, and deploy code |
| **SDLC** | Software Development Lifecycle — the full process from planning through deployment and monitoring |
| **DORA** | DevOps Research and Assessment — a framework defining four key metrics for engineering performance (deployment frequency, lead time, change failure rate, mean time to recovery) |
| **SPACE** | A developer productivity framework (Satisfaction, Performance, Activity, Communication, Efficiency) developed by Microsoft Research |
| **ADR** | Architecture Decision Record — a document recording a significant architectural decision, its context, and consequences |
| **IaC** | Infrastructure as Code — managing infrastructure through code and version control (Terraform, CloudFormation, CDK) |

---

## Business & Organizational Terms

| Term | Definition |
|------|-----------|
| **ROI** | Return on Investment — the ratio of value gained to cost invested |
| **FTE** | Full-Time Equivalent — one person working full-time. "0.5 FTE" means half of one person's time |
| **POC** | Proof of Concept — a small-scale experiment to validate an approach before committing fully |
| **CoE** | Center of Excellence — a dedicated team providing expertise and governance for a specific capability |
| **DPA** | Data Processing Agreement — a legal contract between your organization and a vendor specifying how they handle your data |
| **SLA** | Service Level Agreement — a vendor's contractual guarantee of service availability and performance |
| **IP** | Intellectual Property — proprietary code, algorithms, or business logic that gives competitive advantage |

---

## Security & Identity Terms

| Term | Definition |
|------|-----------|
| **SSO** | Single Sign-On — one login gives access to multiple tools (e.g., log into your company account once, AI tools authenticate automatically) |
| **SAML** | Security Assertion Markup Language — a standard protocol for SSO between identity providers and service providers |
| **SCIM** | System for Cross-domain Identity Management — a standard for automatically provisioning and deprovisioning user accounts across tools |
| **DLP** | Data Loss Prevention — tools and policies that detect and prevent sensitive data from leaving your network |
| **SAST** | Static Application Security Testing — automated scanning of source code for security vulnerabilities |
| **DAST** | Dynamic Application Security Testing — automated security testing of running applications |
| **SIEM** | Security Information and Event Management — centralized platform for collecting and analyzing security logs and alerts |
| **IAM** | Identity and Access Management — systems for controlling who can access what resources |
| **PII** | Personally Identifiable Information — data that can identify a specific individual (name, email, phone, SSN) |
| **MFA** | Multi-Factor Authentication — requiring multiple forms of verification to authenticate |

---

## Compliance & Regulatory Terms

| Term | Definition |
|------|-----------|
| **SOC 2** | Service Organization Control 2 — a compliance framework for service providers, auditing security, availability, processing integrity, confidentiality, and privacy |
| **GDPR** | General Data Protection Regulation — EU law governing the processing and protection of personal data |
| **HIPAA** | Health Insurance Portability and Accountability Act — US law governing the protection of patient health information (PHI) |
| **PCI-DSS** | Payment Card Industry Data Security Standard — security standard for organizations that handle credit card data |
| **FedRAMP** | Federal Risk and Authorization Management Program — US government program for security assessment of cloud services |
| **SOX** | Sarbanes-Oxley Act — US law requiring financial controls and audit trails for public companies |
| **EU AI Act** | European Union's regulation on artificial intelligence — classifies AI systems by risk level and sets requirements for each |

---

## Tool-Specific Terms

| Term | Definition |
|------|-----------|
| **CLAUDE.md** | A project instructions file for Claude Code — tells the AI about your project conventions, commands, and rules |
| **.cursorrules** | A project instructions file for Cursor IDE — configures AI behavior for a specific codebase |
| **Copilot-instructions.md** | GitHub Copilot's project-level instruction file (`.github/copilot-instructions.md`) |
| **Hooks** | Event-driven automation — scripts that run automatically when specific events occur (file saved, task completed, tool invoked) |
| **Skills** | Packaged bundles of instructions that teach AI tools how to perform specific tasks consistently |

---

## How Terms Are Used in This Playbook

When a term first appears in a section, it's typically defined in context. This glossary serves as a reference when you encounter an unfamiliar acronym later.

If you encounter a term not listed here, please [contribute](../CONTRIBUTING.md) a definition.
