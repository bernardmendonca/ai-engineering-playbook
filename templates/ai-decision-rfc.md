# Template: AI Adoption Decision Doc / RFC

> Use this to propose and document a significant AI-adoption decision — tool selection, org model change, policy shift, or governance change — so the reasoning is captured, not just the outcome.

---

## Title

**RFC: [Short, specific title — e.g., "Adopt Claude Code as our secondary CLI-based AI tool"]**

| Field | Details |
|-------|---------|
| Status | [Draft / In Review / Approved / Rejected / Superseded] |
| Author | [Name, role] |
| Reviewers | [Names/roles — typically security, platform lead, affected team leads] |
| Date | [Date] |
| Decision needed by | [Date, if time-sensitive] |

---

## Context

*What situation makes this decision necessary right now? What's the status quo, and why isn't it sufficient?*

- [Current state]
- [What triggered this — pilot results, cost pressure, vendor change, incident, growth]
- [Who is affected by this decision]

---

## Problem Statement

*One or two sentences. If you can't state the problem crisply, you're not ready to propose a solution.*

> [Problem statement]

---

## Options Considered

List every option seriously considered, including "do nothing." Give each a fair treatment — this is what separates a real RFC from a pitch.

### Option A: [Name]

- **Description:** [What this option involves]
- **Pros:** [Bulleted]
- **Cons:** [Bulleted]
- **Cost:** [🆓 / 💰 / 🏢 — with rough figures]
- **Risk:** [Low / Medium / High — with the specific risk named]

### Option B: [Name]

*(repeat structure)*

### Option C: Do Nothing / Status Quo

- **Description:** Keep current approach.
- **Pros:** [No transition cost, no new risk]
- **Cons:** [What continues to be a problem]

---

## Recommendation

**Recommended option:** [A / B / C]

**Why:** [The specific reasoning — not just "it's better" but the tradeoffs that made this the right call given your constraints]

**What would change our mind:** [The specific evidence or event that would make you revisit this decision]

---

## Impact

| Area | Impact |
|------|--------|
| Cost | [🆓/💰/🏢 — $ amount, budget line] |
| Teams affected | [Which teams, how many people] |
| Timeline | [When this takes effect, migration period if any] |
| Reversibility | [How hard is this to undo if it doesn't work — see [Mental Models: Risk/Reversibility](../foundations/mental-models.md)] |
| Security/compliance | [Any review needed — link to [Security](../security/) or [Governance](../governance/) if relevant] |

---

## Open Questions

- [ ] [Anything unresolved that shouldn't block the decision but should be tracked]

---

## Decision Log

*Fill in after the decision is made — this is what makes the RFC useful six months later.*

| Date | Decision | Decided by |
|------|----------|-----------|
| [Date] | [Approved Option A / Rejected / Deferred pending X] | [Name/role] |

---

## Next

- Need the budgeting framework this RFC should reference? → [Investment Strategy](../ai-strategy/investment-strategy.md)
- Deciding on ownership rather than a tool? → [Organizational Models](../ai-strategy/org-models.md)
