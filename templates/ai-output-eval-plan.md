# Template: AI Output Evaluation Plan

> Use this to design an evaluation approach for an AI feature or automation *before* you ship it — this evaluates the AI's output quality, not the vendor. For choosing between tools/vendors, see the [AI Tool Evaluation Scorecard](./ai-tool-evaluation-scorecard.md) instead. For the underlying concepts, see [Harness Engineering: Evaluation](../ai-engineering-practices/harness-engineering.md).

---

## What This Covers

| This template is for... | Not this template |
|---|---|
| "Is our PR-summary bot's output good enough to ship unattended?" | "Should we buy Copilot or Cursor?" (→ [Tool Evaluation Scorecard](./ai-tool-evaluation-scorecard.md)) |
| "How do we know our AI code-review comments aren't noise?" | "Is this vendor SOC 2 compliant?" (→ [Vendor Security Assessment](./vendor-security-assessment.md)) |
| "Did the last prompt change make output worse?" | |

---

## 1. What Is Being Evaluated

| Field | Details |
|-------|---------|
| AI workflow/feature name | [e.g., "PR summary generator," "AI security review bot"] |
| Where it runs | [CI/CD step, Slack bot, IDE feature, etc.] |
| Who consumes the output | [Developers, reviewers, customers] |
| Runs attended or unattended? | [Human always sees it before it matters / Fully automated, no human gate] |
| Current maturity level | [See [Harness Engineering maturity model](../ai-engineering-practices/harness-engineering.md) — Level 0–4] |

> **Rule of thumb:** The less human oversight before this output has an effect, the more rigorous this evaluation plan needs to be.

---

## 2. Success Definition

*Write this before looking at any output — otherwise you'll rationalize whatever you got.*

**Good output looks like:** [Specific, concrete description]

**Bad output looks like:** [Specific, concrete description — be as precise as "good"]

**Non-negotiable failure conditions** (any one of these = fix before shipping):
- [ ] [e.g., "Ever recommends removing an authentication check"]
- [ ] [e.g., "Ever fabricates a fact about the codebase that isn't in context"]

---

## 3. Evaluation Approach

Choose one or more (per [Harness Engineering's Evaluation Approaches](../ai-engineering-practices/harness-engineering.md)):

| Approach | Use for this workflow? | Notes |
|----------|:-----------------------:|-------|
| Deterministic checks (regex, schema validation) | ☐ | Best when output has a required structure |
| Golden dataset comparison (known inputs → expected outputs) | ☐ | Best for regression testing after prompt/model changes |
| LLM-as-judge (second AI call scores the first) | ☐ | Best for subjective quality at scale |
| Human spot-check (sample N/week) | ☐ | Baseline for anything customer-facing |
| Downstream metrics (merge rate, revert rate, override rate) | ☐ | Best proxy for real-world value |

---

## 4. Test Set

| Field | Details |
|-------|---------|
| Number of test cases | [N] |
| Where they came from | [Real historical examples / synthetic / adversarial edge cases] |
| Coverage of edge cases | [List the specific edge cases included — empty input, huge input, ambiguous input, malicious input] |
| Who reviewed the expected outputs | [Name — someone other than the prompt author, ideally] |

---

## 5. Baseline Results

| Metric | Result | Target | Pass/Fail |
|--------|--------|--------|:---------:|
| [e.g., % passing deterministic checks] | | | ☐ |
| [e.g., LLM-judge average score] | | | ☐ |
| [e.g., human spot-check agreement rate] | | | ☐ |
| [e.g., % outputs requiring human correction] | | | ☐ |

---

## 6. Ongoing Monitoring Plan

*How will you know if quality degrades after this ships? See [Harness Engineering: Observability](../ai-engineering-practices/harness-engineering.md).*

| Signal | Threshold that triggers review | Owner |
|--------|-------------------------------|-------|
| [e.g., override/revert rate] | [e.g., >10% in a week] | [Name/team] |
| [e.g., human spot-check score] | [e.g., drops below X] | [Name/team] |
| [e.g., cost per run] | [e.g., exceeds $X] | [Name/team] |

**Review cadence:** [Weekly / Monthly / On alert]

---

## 7. Rollback Plan

**If this evaluation plan reveals the output isn't good enough:**
- [ ] Fallback behavior: [e.g., "revert to no AI summary, just a template"]
- [ ] Who decides to roll back: [Name/role]
- [ ] How fast can it be rolled back: [Time estimate]

---

## Sign-off

| Role | Name | Approved |
|------|------|:--------:|
| Feature owner | | ☐ |
| Reviewer (quality) | | ☐ |
| Reviewer (security, if customer-facing or unattended) | | ☐ |

---

## Next

- Building the harness this evaluates? → [Harness Engineering](../ai-engineering-practices/harness-engineering.md)
- Choosing a tool rather than evaluating output? → [AI Tool Evaluation Scorecard](./ai-tool-evaluation-scorecard.md)
