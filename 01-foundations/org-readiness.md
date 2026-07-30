# Organizational Readiness

> Assessing where your org is today and what's needed before successful AI adoption.

## The Readiness Question

"Are we ready for AI?" is the wrong question. The right questions are:
- Ready for *which* AI capabilities?
- Ready at *what* adoption level (individual, team, org)?
- What *prerequisites* are we missing?

---

## Readiness Assessment Framework

Rate your organization on each dimension (1 = not ready, 5 = fully ready):

### Technical Readiness

| Dimension | 1 (Not ready) | 3 (Partial) | 5 (Ready) |
|-----------|---------------|-------------|-----------|
| **CI/CD maturity** | Manual deployments, no pipeline | Basic pipeline, some automation | Full CI/CD, automated testing, deployment gates |
| **Code quality baseline** | No linting, no tests, no review | Some teams have standards | Consistent standards, >60% coverage, mandatory review |
| **Developer tooling** | Mixed IDEs, no standardization | Common IDE, basic extensions | Standardized tooling, centrally managed |
| **Source control hygiene** | Inconsistent branching, rare PRs | Standard branching model, PRs required | Branch protection, review requirements, clean history |
| **Security baseline** | No scanning, no data classification | Basic scanning in CI | SAST/DAST in pipeline, secrets management, data classification |

### Organizational Readiness

| Dimension | 1 (Not ready) | 3 (Partial) | 5 (Ready) |
|-----------|---------------|-------------|-----------|
| **Leadership alignment** | No awareness or interest | Some leaders interested, no strategy | Executive sponsor, clear mandate |
| **Budget availability** | No budget for AI tooling | Could allocate for a pilot | Budget earmarked for AI tools |
| **Policy foundation** | No security or acceptable use policies | Policies exist but not updated for AI | Policies updated or being updated for AI |
| **Change management capacity** | No experience with tool rollouts | Some rollout experience | Proven playbook for tool adoption |
| **Developer openness** | Active resistance or fear | Mixed — some curious, some skeptical | Generally enthusiastic, experimenting already |

### Process Readiness

| Dimension | 1 (Not ready) | 3 (Partial) | 5 (Ready) |
|-----------|---------------|-------------|-----------|
| **Code review culture** | No reviews or rubber-stamping | Reviews happen but inconsistently | Strong review culture with constructive feedback |
| **Measurement practice** | No engineering metrics | Some metrics (DORA) tracked | Regular measurement with baselines established |
| **Experimentation culture** | New tools discouraged | New tools tolerated if they work | Active experimentation encouraged, failures learned from |
| **Documentation** | Tribal knowledge only | Some docs, often stale | Living documentation maintained as part of workflow |

---

## Interpreting Your Score

**Total score: 15 dimensions, max 75**

| Score | Interpretation | Recommended action |
|-------|---------------|-------------------|
| 55–75 | **Ready for org-wide adoption** | Move fast. Your main risk is going too slow while competitors move. |
| 40–54 | **Ready for team pilots** | Start with willing teams. Use the pilot to build missing readiness. |
| 25–39 | **Ready for individual exploration** | Encourage personal learning. Work on prerequisites in parallel. |
| 15–24 | **Foundation building needed** | Fix basic engineering practices first. AI tools amplify what you have — including chaos. |

---

## Common Prerequisites and How to Build Them

### "We don't have consistent code review"

**Why it matters:** AI agents generate code that needs review. Without a review culture, agent output goes unexamined into production.

**How to fix (2–4 weeks):**
1. Implement mandatory PR reviews (at least one reviewer)
2. Start with simple rubric: correctness, tests, security
3. Use AI review tools to provide baseline automated feedback
4. Build the muscle before adding agents

---

### "We don't have CI/CD"

**Why it matters:** Agents work best when they can run tests and verify their own output. Without CI, neither humans nor agents have a safety net.

**How to fix (2–6 weeks):**
1. Set up basic pipeline: lint → build → test → deploy to staging
2. Even minimal test coverage gives agents feedback loops
3. This prerequisite is non-negotiable for agent usage

---

### "We don't have data classification"

**Why it matters:** AI tools send code to external services. Without data classification, you can't decide what's safe to send.

**How to fix (1–2 weeks):**
1. Simple three-tier classification: Public / Internal / Restricted
2. Map repositories to tiers
3. Restricted code = no cloud AI tools (or self-hosted only)
4. Internal code = approved tools with enterprise DPA
5. Public code = any vetted tool

---

### "Our developers are resistant"

**Why it matters:** Forced adoption creates resentment and underground workarounds.

**How to address:**
1. Understand the resistance (fear of replacement? quality concerns? previous bad experience?)
2. Address concerns directly and honestly
3. Start with volunteers — let results create pull
4. Give skeptics respected roles (security reviewers for AI code, quality gatekeepers)
5. Never mandate usage metrics

---

### "We have no budget"

**Why it matters:** Exploration is free. Production isn't.

**How to work with this:**
1. Start with free tiers — genuinely generous options exist (see [Getting Started Free](../03-ai-coding-agents/getting-started-free.md))
2. Build evidence during exploration phase
3. Frame budget request with data: "Based on X weeks of exploration, here's the value we've seen"
4. Compare to existing tool costs (AI tools are cheaper than most observability or CI tools per seat)

---

## Readiness by AI Capability Level

Not all AI capabilities require the same readiness:

| AI Capability | Minimum readiness needed | Key prerequisites |
|--------------|------------------------|-------------------|
| Code autocomplete | Low (score 20+) | IDE standardization, basic awareness |
| Chat assistants | Low (score 25+) | Developer interest, basic security awareness |
| Coding agents | Medium (score 35+) | CI/CD, code review culture, data classification |
| Automated code review AI | Medium (score 35+) | Existing review culture, PR-based workflow |
| AI in CI/CD pipelines | Medium-High (score 40+) | Mature CI/CD, security baseline, cost monitoring |
| Org-wide standardization | High (score 50+) | All of the above, plus governance and measurement |

---

## The "Start Tomorrow" Checklist

If you want to start AI adoption tomorrow with minimal prerequisites:

- [ ] One team willing to try (3–5 developers)
- [ ] Each developer has an IDE (VS Code or JetBrains)
- [ ] The team uses git with pull requests
- [ ] Basic CI exists (even just `npm test` on PR)
- [ ] No regulatory prohibition on cloud AI tools for this code
- [ ] One leader willing to sponsor and observe

That's it. You can start exploring with free tiers. Everything else can be built in parallel as you learn.

> **Our take:** Most organizations wait too long. If you have the six items above, start this week. Perfection is the enemy of progress — you'll learn more from 2 weeks of hands-on exploration than 2 months of readiness planning. The prerequisites that genuinely block you (CI/CD, data classification) can be built in parallel with Phase 1 exploration.

---

## Next

- Need to build the executive case? → [The Business Case](./business-case.md)
- Ready to choose tools? → [02 — AI Tools](../02-ai-tools/)
- Want to understand the landscape first? → [AI Landscape](./ai-landscape.md)
