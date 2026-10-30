# References

> Curated links, papers, talks, and further reading on AI in engineering organizations.

> **Last verified:** 2026-10-30 · **Re-check by:** 2027-01-30

For a full list of terms and acronyms used throughout this playbook, see the [Glossary](./glossary.md).

## Research and Reports

### Developer Productivity with AI

- **GitHub Copilot Research** — GitHub's published research on developer productivity with Copilot (survey methodology, task completion studies)
  - https://github.blog/ai-and-ml/github-copilot/
- **DORA / State of DevOps** — Annual report tracking engineering performance metrics. Increasingly includes AI tool impact.
  - https://dora.dev
- **SPACE Framework** (Microsoft Research) — Multi-dimensional developer productivity framework
  - Paper: "The SPACE of Developer Productivity" (2021)
- **Stack Overflow Developer Survey** — Annual survey with AI tool adoption and sentiment data
  - https://survey.stackoverflow.co
- **METR developer productivity studies** (2025 randomized trial; 2026 update) — The clearest evidence that self-reported AI speedups are unreliable
  - https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/
  - https://metr.org/blog/2026-02-24-uplift-update/
- **DORA State of AI-assisted Software Development (2025)** and **ROI of AI-assisted Software Development (2026.01)** — AI as an amplifier, the AI Capabilities Model, the J-curve, and an ROI calculator
  - https://dora.dev/ai/roi/report/
- **Faros AI, The AI Productivity Paradox (2025)** — Telemetry from 10,000+ developers on PR volume, review time, and delivery
- **How AI Impacts Skill Formation** (Shen et al., Anthropic, 2026) — Randomized trial on learning with and without AI
  - https://arxiv.org/abs/2601.20245
- **Canaries in the Coal Mine** (Stanford Digital Economy Lab, updated Aug 2026) — Early-career employment in AI-exposed occupations
  - https://digitaleconomy.stanford.edu/news/canariesaug26/
- **Context Rot** (Chroma Research, 2025) — How model performance degrades as input length grows
  - https://research.trychroma.com/context-rot

See [What the Research Says](../productivity/what-the-research-says.md) for a summary of these findings.

### AI Code Quality and Security

- **GitHub Security Research** — Studies on vulnerability patterns in AI-generated code
- **OWASP AI Security** — Guidance on AI-specific security threats
  - https://owasp.org/www-project-ai-security-and-privacy-guide/
- **Asleep at the Keyboard?** (NYU Tandon, 2021) — Pearce, Dolan-Gavitt, Karri et al. research on security of Copilot-generated code

- **OWASP Top 10 for Agentic Applications** (December 2025) — Ten risk categories specific to autonomous agents, from agent goal hijack (ASI01) to rogue agents (ASI10). Applied to coding agents in [Agentic Security](../security/agentic-security.md)
  - https://genai.owasp.org/
- **OWASP Agentic Skills Top 10** — Risks in agent skill ecosystems, starting with malicious skills (AST01)
  - https://owasp.org/www-project-agentic-skills-top-10/ast01
- **GitHub Spec Kit** — Open-source toolkit for spec-driven development with many coding agents
  - https://github.com/github/spec-kit

### Open Standards for Agents

- **AGENTS.md** — Cross-tool project instructions file for coding agents
  - https://agents.md
- **Agentic AI Foundation (Linux Foundation)** — Neutral home for MCP, AGENTS.md, Agent Skills, A2A, and related projects
  - https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation

### Responsible AI

- **EU AI Act** — Full regulation text and implementation guidance
  - https://artificialintelligenceact.eu
- **NIST AI Risk Management Framework** — US framework for AI risk management
  - https://www.nist.gov/artificial-intelligence/ai-risk-management-framework

---

## Tool Documentation

### AI Coding Assistants

| Tool | Cost | Documentation | Pricing |
|------|------|--------------|---------|
| GitHub Copilot | 🆓💰🏢 | https://docs.github.com/copilot | https://github.com/features/copilot#pricing |
| Kiro *(AWS's successor to Amazon Q Developer, which reaches end-of-support April 2027)* | 🆓💰 | https://kiro.dev/docs | https://kiro.dev/pricing |
| Cursor *(acquired by SpaceX Aug 2026; sold as part of "The X Subscription" since Oct 2026)* | 🆓💰🏢 | https://cursor.com/docs | https://cursor.com/pricing |
| OpenAI Codex | 🆓💰🏢 | https://developers.openai.com/codex | https://chatgpt.com/codex/pricing |
| Google Antigravity *(replaced Gemini CLI for consumer tiers, June 2026)* | 🆓💰🏢 | https://antigravity.google | Via Google AI plans / Gemini Enterprise |
| Claude Code | 🆓💰🏢 | https://docs.anthropic.com/en/docs/claude-code | https://www.anthropic.com/pricing |
| Devin Desktop *(formerly Windsurf, rebranded by Cognition June 2026)* | 🆓💰🏢 | https://docs.devin.ai | https://devin.ai/pricing |
| Aider | 🆓 | https://aider.chat/docs | Open source (free) |
| Cline | 🆓 | https://github.com/cline/cline | Open source (free) |

### AI Code Review

| Tool | Cost | Documentation |
|------|------|--------------|
| CodeRabbit | 🆓💰 | https://docs.coderabbit.ai |
| Sourcery | 🆓💰 | https://docs.sourcery.ai |

### AI APIs (for custom integrations)

| Provider | Cost | API Docs | Pricing |
|----------|------|----------|---------|
| Anthropic (Claude) | 💰🏢 | https://docs.anthropic.com | https://www.anthropic.com/pricing |
| OpenAI | 💰🏢 | https://platform.openai.com/docs | https://openai.com/pricing |
| AWS Bedrock | 💰🏢 | https://docs.aws.amazon.com/bedrock | https://aws.amazon.com/bedrock/pricing |
| Google Vertex AI | 💰🏢 | https://cloud.google.com/vertex-ai/docs | https://cloud.google.com/vertex-ai/pricing |

---

## Books

### For Engineering Leaders

- **"Team Topologies"** (Skelton & Pais) — How team structures affect delivery. Relevant for AI-era team design.
- **"Accelerate"** (Forsgren, Humble, Kim) — The science behind DORA metrics. Foundation for measuring AI impact.
- **"An Elegant Puzzle"** (Larson) — Engineering management. Useful framing for adoption as a systems problem.
- **"The Manager's Path"** (Fournier) — Engineering leadership at all levels. Context for how AI changes each level.

### For AI Understanding

- **"AI Engineering"** (Chip Huyen, 2025) — Building applications with LLMs. Technical foundation for leaders.
- **"Prompt Engineering for Developers"** — Various authors. Practical skill building.

---

## Talks and Presentations

### Recommended for Leaders

- **"How to Adopt AI Coding Tools at Enterprise Scale"** — Various conference talks from GitHub, Anthropic, and AWS leadership
- **"Developer Productivity in the Age of AI"** — DORA team presentations at conferences
- **"Responsible AI in Practice"** — Microsoft and Google responsible AI teams

### Conference Tracks

- **GitHub Universe** — AI and developer tools track
- **AWS re:Invent** — Developer tools and AI sessions
- **QCon** — AI-assisted software engineering track
- **LeadDev** — Engineering leadership with AI adoption topics

---

## Newsletters and Blogs

### High-Signal Sources

| Source | Focus | Frequency |
|--------|-------|-----------|
| The Pragmatic Engineer (Gergely Orosz) | Engineering leadership, AI adoption coverage | Weekly |
| Lenny's Newsletter | Product + engineering intersection | Weekly |
| GitHub Blog (AI/ML section) | Copilot updates, research | As published |
| Anthropic Blog | Claude updates, research | As published |
| Simon Willison's Weblog | AI tools, practical experimentation | Multiple/week |
| Latent Space Podcast | AI engineering deep dives | Weekly |

---

## Communities

| Community | Platform | Focus |
|-----------|----------|-------|
| r/ExperiencedDevs | Reddit | Senior developer discussions (AI adoption threads) |
| LeadDev Community | Slack/Events | Engineering leadership |
| Rands Leadership Slack | Slack | Engineering management |
| AI-assisted Dev | Discord/GitHub | AI coding tool discussion |

---

## Standards and Frameworks

| Standard | Relevance | Link |
|----------|-----------|------|
| DORA Metrics | Measuring engineering performance | https://dora.dev |
| SPACE Framework | Developer productivity measurement | Microsoft Research paper |
| OWASP Top 10 | Security baseline for AI-generated code review | https://owasp.org |
| SOC 2 | Compliance framework, AI tool audit readiness | https://www.aicpa.org |
| ISO 27001 | Information security, AI tool vendor assessment | https://www.iso.org |
| EU AI Act | AI regulation compliance | https://artificialintelligenceact.eu |

---

## Contributing

Found a great resource? Submit a PR adding it to the relevant category. Include a one-sentence description of why it's valuable for the target audience (engineering leaders making AI adoption decisions).

**Selection criteria for inclusion:**
- Relevant to engineering leaders (not just AI researchers or individual developers)
- Practical (actionable, not purely theoretical)
- Current (published within last 2 years, or timeless classics)
- Trustworthy source (established publication, major vendor, peer-reviewed research)

---

## Status

🟢 Active — accepting contributions.
