# Responsible AI in Engineering

> Bias, transparency, accountability, and ethical considerations for AI-assisted development.

## What "Responsible AI" Means for Engineering Teams

Responsible AI for engineering teams isn't the same as responsible AI for ML model builders. You're not training models — you're using them. Your responsibilities are different:

| If you're building AI products... | If you're using AI tools for engineering... |
|-----------------------------------|----------------------------------------------|
| Bias in model outputs to users | Bias in AI-generated code (defaults, assumptions) |
| Fairness in AI decisions | Fair evaluation of developer work (AI-assisted vs. not) |
| Model transparency | Transparency about AI use in your codebase |
| Data ethics | Data handling in AI tool usage |

---

## Responsibility 1: Transparency

### When to Disclose AI Involvement

| Context | Disclosure needed? | How |
|---------|:-----------------:|-----|
| AI-generated code in your codebase | Recommended | Git trailers, PR tags, commit prefixes |
| AI-assisted code review | No | Expected part of tooling |
| AI-generated documentation | Recommended | Note at top: "Generated with AI assistance" |
| AI-generated responses to customers | Yes | Company communication policy |
| AI-generated architecture proposals | No | Internal working tool |

### Practical Implementation

Commit message convention:
```
feat: add pagination to users API

Co-authored-by: AI Assistant
AI-tool: claude-code
```

Or PR labels: `ai-assisted`, `ai-generated`

**Why bother?** Not for blame — for learning. Tracking AI involvement helps you understand what works, identify quality patterns, and improve processes.

---

## Responsibility 2: Accountability

### The Ownership Question

> "If AI generated this code and it breaks production, who's responsible?"

**Answer: The developer who submitted it.**

This isn't punitive — it's practical:
- Someone must own the code for on-call, debugging, and maintenance
- AI can't be paged at 3 AM
- The review and approval process is the human quality gate

### Implications

| Stakeholder | Responsibility |
|------------|---------------|
| **Developer** | Reviewing AI output before submission. Owns the code once merged. |
| **Reviewer** | Same review standard regardless of author (human or AI) |
| **Manager** | Ensuring team has training and time to review properly |
| **Organization** | Providing tools, policies, and processes that enable quality |

---

## Responsibility 3: Bias Awareness

### How Bias Appears in AI-Generated Code

AI models reflect their training data. This shows up in engineering:

| Bias type | Example | Impact |
|-----------|---------|--------|
| **Default assumptions** | `gender: "male"` as default in user models | Exclusionary to non-male users |
| **Naming bias** | Using culturally-specific names in examples | Subtle signal about who "belongs" |
| **Accessibility gaps** | Generated UIs without aria labels, keyboard nav | Excludes users with disabilities |
| **Language bias** | Comments/docs assume English; variable names assume Western concepts | Alienates global teams |
| **Security defaults** | Generating code that assumes trusted input | Vulnerable to attacks |

### Practical Mitigations

1. **Review AI output for assumptions** — Especially in user-facing code, data models, and defaults
2. **Include accessibility in prompts** — "Generate a form component that is fully accessible (WCAG 2.1 AA)"
3. **Use inclusive examples** — Configure custom instructions to use diverse sample data
4. **Lint for accessibility** — Automated tools (axe, pa11y) catch what humans and AI miss
5. **Code standards that address defaults** — Team conventions about default values in data models

---

## Responsibility 4: Fair Treatment of Developers

### AI and Performance Evaluation

| Don't | Why | Instead |
|-------|-----|---------|
| Compare AI-users' output volume to non-users | Unfair comparison, different tooling | Evaluate outcomes, not output volume |
| Require AI usage in performance goals | Poisons voluntary adoption | Make tools available, measure team outcomes |
| Penalize developers who don't use AI | Personal tool choice varies | Focus on results, not methods |
| Attribute team improvements to AI-using individuals | Improvements are team + tool combined | Credit team-level gains |

### The Junior Developer Question

> "If AI can write boilerplate, do we still hire juniors?"

**Answer: Yes, but their role evolves.**

- Juniors still need to learn fundamentals (AI doesn't eliminate that need)
- Their work shifts: more reviewing, more integration, more testing, less raw typing
- AI can accelerate their learning (better explanations, faster iteration)
- Remove AI in interview/assessment if you want to evaluate raw skill
- Mentoring humans is still a human job

---

## Responsibility 5: Environmental Consideration

AI tools have a carbon footprint. At scale, it's worth acknowledging:

| Factor | Scale | Action |
|--------|-------|--------|
| API calls (cloud inference) | Moderate per developer | Not a blocker but worth noting in sustainability reporting |
| Training models (not your problem) | High (but vendor responsibility) | Choose vendors with sustainability commitments |
| Self-hosted GPU infrastructure | High if applicable | Factor into build-vs-buy decisions |

**Practical stance:** This isn't a reason to avoid AI tools (the productivity gains likely offset the energy cost). But it's worth tracking and reporting if your organization has sustainability commitments.

---

## 📋 Quick Checklist: Responsible AI for Engineering

- [ ] We disclose AI involvement in code (convention defined)
- [ ] Accountability is clear: human owns the code
- [ ] Code review standard doesn't change based on author (human or AI)
- [ ] We review AI output for bias in defaults and assumptions
- [ ] Accessibility is part of our AI prompting standards
- [ ] Performance evaluation doesn't unfairly compare AI-users to non-users
- [ ] Junior developers are supported, not replaced
- [ ] We have a process for reporting concerns about AI usage

---

## Next

- Compliance considerations → [Compliance](./compliance.md)
- AI usage policy → [AI Usage Policy](./ai-usage-policy.md)
- Return to section overview → [README](./README.md)
