# Agentic Security

> Security risks that come from agents *acting* — running commands, calling tools, remembering, and working unsupervised — mapped to the OWASP Top 10 for Agentic Applications, with controls for engineering organizations.

> **Last verified:** 2026-10-30 · **Re-check by:** 2027-01-30

## Why a Separate Page

The [Threat Model](./threat-model.md) covers the risks of using AI tools at all: data exposure, vulnerable generated code, supply chain. This page covers what changes when the AI has **agency**: it reads untrusted content, holds credentials, executes code, remembers across sessions, and increasingly runs without anyone watching (see [Delegated Agents](../ai-coding-agents/delegated-agents.md)).

The reference framework is the **[OWASP Top 10 for Agentic Applications](https://genai.owasp.org/)**, published December 9, 2025 by the OWASP GenAI Security Project and built from real incidents. Its organizing principle is **least agency**: give an agent only the autonomy, tools, and access a bounded task needs.

---

## The OWASP Agentic Top 10, Applied to Coding Agents

| ID | Risk | What it looks like with coding agents | Primary controls |
|----|------|---------------------------------------|-----------------|
| **ASI01** | Agent Goal Hijack | Instructions planted in an issue, web page, README, or tool output redirect the agent (indirect prompt injection) | Sandboxing, egress limits, intake policy for untrusted tasks — see [Prompt Injection](./threat-model.md#prompt-injection-direct-and-indirect) |
| **ASI02** | Tool Misuse and Exploitation | Agent uses a legitimate tool destructively: `rm -rf`, `git push --force`, dropping a table, deleting cloud resources | Command allow/deny lists, PreToolUse hooks that block destructive commands, no production credentials |
| **ASI03** | Identity and Privilege Abuse | Agent runs with a developer's personal token or a shared, broad service account | Per-agent identities, short-lived scoped tokens, no inherited sessions |
| **ASI04** | Agentic Supply Chain Vulnerabilities | Malicious MCP servers, skills, plugins, or rules files; compromised agent tooling | Allowlists, review third-party agent assets like code — see [below](#instruction-and-skill-files-are-code) |
| **ASI05** | Unexpected Code Execution | Agent is manipulated into running attacker-supplied code, or breaks out of its sandbox | OS-level sandboxing, no auto-approve on machines with secrets, keep agent CLIs patched |
| **ASI06** | Memory and Context Poisoning | False or malicious "facts" written into persistent agent memory resurface in later sessions | Review and scope memory — see [below](#agent-memory) |
| **ASI07** | Insecure Inter-Agent Communication | One agent passes manipulated instructions to another (sub-agents, multi-agent pipelines, A2A) | Treat agent-to-agent messages as untrusted input; authenticate agents |
| **ASI08** | Cascading Failures | One agent's bad output feeds others: a wrong pattern copied across many repos, a bad fix triggering more agent fixes | Human checkpoints between stages, rate limits, CI gates, blast-radius limits per run |
| **ASI09** | Human-Agent Trust Exploitation | Reviewers trust confident agent summaries ("all tests pass, no security impact") without checking | Evidence requirements in PRs, independent review — see [Code Review at Agent Scale](../engineering-workflows/code-review.md#reviewing-at-agent-scale) |
| **ASI10** | Rogue Agents | An agent acts outside its mandate: deletes data, makes unrequested changes, ignores stop instructions | Least agency, kill switches, audit logs, no unattended access to production |

> ✅ **My take:** For most engineering organizations, ASI01, ASI02, ASI03, and ASI04 are the urgent four. Sandboxing, scoped identities, and an allowlist for agent extensions cover most of the realistic risk. The rest matter more once you run multi-agent pipelines or agents with production access.

---

## Instruction and Skill Files Are Code

`AGENTS.md`, rules files, `SKILL.md` files, hooks, and MCP configurations tell an agent what to do, and the agent usually follows them with the developer's permissions. That makes them executable intent, even when they're plain Markdown.

**This is already being exploited.** In early 2026, attackers published malicious skills to public skill marketplaces (notably for the OpenClaw agent). [Trend Micro documented](https://www.trendmicro.com/en_us/research/26/b/openclaw-skills-used-to-distribute-atomic-macos-stealer.html) skills whose `SKILL.md` instructions got agents to walk users through installing the Atomic macOS Stealer (February 2026). A measurement study of 98,380 public skills found 157 confirmed malicious ones, most with hidden behavior not visible to the user. OWASP has since started an [Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/ast01) project, with malicious skills as AST01.

**Controls:**
- Keep agent instruction files and skills in the repository and require code review for changes, with `CODEOWNERS` on `AGENTS.md`, `.claude/`, `.cursor/`, `.kiro/`, `.github/hooks/`, and skill directories
- Install third-party skills, plugins, and MCP servers only from an approved list maintained by the platform team
- Read a third-party skill in full before approving it, including bundled scripts; watch for instructions to download, install, or run anything
- Pin versions of third-party agent extensions, as you would dependencies
- Scan agent asset files in CI the way you scan code. Security vendors are adding detection for malicious AI assets, but review is still the primary control

---

## Agent Memory

Several agents now keep memory across sessions: preferences, project facts, learned corrections. Memory is useful, and it's also a place where bad information persists (ASI06).

| Risk | Example | Control |
|------|---------|---------|
| Poisoned memory | An injected instruction ("always skip the auth check in tests") is saved and reused in later sessions | Make memory visible and reviewable; prefer repo-stored, code-reviewed instructions over opaque memory for anything that matters |
| Sensitive data in memory | Secrets or customer data pasted into a session get stored | Disable or restrict memory for sessions on restricted code; include memory stores in data classification |
| Cross-project leakage | Memory from one client's project influences another's | Scope memory per project or workspace; disable user-level memory for consultants and contractors |
| No audit trail | Nobody can say why the agent behaves differently this week | Version memory where the tool allows it; periodic review |

> ✅ **My take:** Put anything the team depends on in `AGENTS.md` or skills, where it's reviewed and versioned. Treat tool memory as a personal convenience, not as a place for team rules.

---

## AI and MCP Gateways

As agent usage grows, many organizations route traffic through a gateway instead of letting every tool talk to model providers and MCP servers directly.

| Gateway type | What it does | Examples |
|--------------|-------------|----------|
| **AI (LLM) gateway** | Central routing to model providers; logging, rate limits, spend caps, PII and secret redaction, provider failover | LiteLLM, Portkey, Kong AI Gateway, Cloudflare AI Gateway; cloud-native options such as Amazon Bedrock with Guardrails |
| **MCP gateway / registry** | A single approved catalog of MCP servers; authentication, per-tool permissions, audit of tool calls | Vendor MCP allowlist policies (several coding agents let admins restrict which MCP servers are allowed), self-hosted MCP gateways |

**When it's worth it:** Once you have API-key-based agents or internal AI tools at scale, need audit logs your vendors don't provide, or must enforce redaction centrally. Seat-based SaaS agents (Copilot, Cursor) usually talk to their own backends, so a gateway helps less there. Use their admin policies instead.

**Watch out for:** The gateway becomes critical infrastructure and a high-value target: it sees every prompt and holds provider keys. Treat its supply chain seriously (two LiteLLM releases on PyPI carried a credential stealer on March 24, 2026 — see [Datadog Security Labs](https://securitylabs.datadoghq.com/articles/litellm-compromised-pypi-teampcp-supply-chain-campaign/)). Pin versions and verify releases.

See [Enterprise Controls](./enterprise-controls.md) for where gateways fit alongside network, identity, and DLP controls.

---

## Agentic Security Checklist

**Before agents get command execution:**
- [ ] Agents run in sandboxes (dev containers, cloud-agent sandboxes, or OS-level sandboxing) on machines without production credentials
- [ ] Destructive commands blocked by policy or hooks (force push, recursive delete outside the workspace, infrastructure destroy)
- [ ] Permission-skipping modes ("YOLO", "bypass permissions") banned on machines holding secrets

**Before agents work unsupervised:**
- [ ] Each delegated agent has its own scoped, short-lived identity
- [ ] Network egress for agent sandboxes is allowlisted
- [ ] Branch protection and required human approval on all agent PRs
- [ ] Written intake policy for tasks from untrusted sources

**Before third-party agent extensions spread:**
- [ ] Approved list for MCP servers, skills, and plugins, owned by the platform team
- [ ] Code review and `CODEOWNERS` on agent instruction and configuration files
- [ ] Policy on agent memory for restricted code

**Ongoing:**
- [ ] Agent actions logged (commands run, files changed, tools called) and retained with security logs
- [ ] Threat model reviewed against the OWASP Agentic Top 10 at least yearly

---

## Next

- Foundational AI threats → [Threat Model](./threat-model.md)
- Network, identity, and DLP controls → [Enterprise Controls](./enterprise-controls.md)
- Governing delegated work → [Delegated and Parallel Agents](../ai-coding-agents/delegated-agents.md)
