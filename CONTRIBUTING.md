# Contributing to AI Engineering Playbook

Thank you for your interest in contributing. This playbook is a living document and benefits from real-world experience.

## How to Contribute

### Content Contributions

1. **Fork** this repository
2. **Create a branch** for your contribution (`git checkout -b add/topic-name`)
3. **Write or edit** content following the guidelines below
4. **Submit a pull request** with a clear description of what you've added or changed

### What We're Looking For

- Real-world experience reports and case studies
- Decision frameworks backed by practitioner experience
- Tool comparisons with fair, balanced analysis
- Security considerations and threat models
- Metrics and measurement approaches that have worked in practice
- Prompt libraries and templates that teams can adopt directly

### Content Guidelines

- **Be practical** — Theory is fine as background, but lead with actionable guidance
- **Show tradeoffs** — Where multiple valid approaches exist, present them fairly with context on when each applies
- **Be opinionated where it matters** — If there's a clear best practice, say so directly
- **Stay current** — Reference specific tools; mark time-sensitive pages with a last-verified date (see [below](#keeping-time-sensitive-content-current))
- **Use Mermaid for diagrams** — Keep visuals in Markdown so they're easy to maintain and render on GitHub

### Formatting

- Use Markdown for all content
- Use Mermaid code blocks for diagrams and flows
- Keep files focused — one major topic per file
- Use front-matter or clear headings to indicate the audience and context for each piece
- **Always indicate cost context** — Use `🆓` (free/explore), `💰` (paid/team), `🏢` (enterprise) labels when discussing tools or services
- **Distinguish POC from production** — If something works great for experimentation but has different implications at scale, say so explicitly

### Keeping Time-Sensitive Content Current

AI tooling changes monthly. In 2026 alone, several major tools were acquired, renamed, or retired, and most vendors changed how they bill. These rules keep the playbook accurate.

**1. Mark time-sensitive pages.** Any page with prices, vendor capabilities, regulatory dates, or fast-moving research carries this line directly under its description:

```markdown
> **Last verified:** YYYY-MM-DD · **Re-check by:** YYYY-MM-DD
```

Set the re-check date three months out. When you verify a page, update both dates in the same PR as any fixes. Verifying means checking every vendor claim on the page against the vendor's current docs or pricing page, not skimming.

**2. Keep prices in one place.**

| Content | Lives only in | Everywhere else |
|---------|--------------|-----------------|
| Coding-agent prices and plans (Copilot, Claude Code, Codex, Kiro, Cursor, Devin, Antigravity, Aider, Cline) | [`ai-coding-agents/agent-landscape.md`](./ai-coding-agents/agent-landscape.md) | Link to the vendor's section there |
| Prices for other tool categories (code review, testing, docs, observability) | [`ai-tools/tool-categories.md`](./ai-tools/tool-categories.md) | Link there |
| Budgets and cost models | May use **ranges** (for example "$19–40/user/month in seats") | Never quote a specific vendor's current tier price outside the two pages above |
| Case studies | May record what the organization paid at the time | Label it as historical; don't update it to current prices |

When a vendor changes pricing, update the source page, then search for the vendor name to catch prose that describes the old model.

**3. Don't put model versions in guidance.** Write model *tiers* in prose ("a small, fast model", "Anthropic's Opus tier"). Runnable examples read the model ID from configuration, not from code. Vendors retire model versions every few months.

**4. Mark what you couldn't confirm.** If you can't verify a claim from a primary source, write "Verify" in the table cell or say so in the text. Don't guess.

**5. Re-check on triggers, not just on schedule.** An acquisition, rebrand, pricing-model change, or product retirement means re-verifying every page that mentions the vendor, whatever the re-check date says.

**Find pages that are due for review:**

```bash
grep -rHo --include='*.md' 'Re-check by:\*\* [0-9-]*' . \
  | awk -v t="$(date +%F)" -F'\\*\\* ' '$2 < t {print $1}' \
  | sed 's/:Re-check by://'
```

### What We Won't Accept

- Marketing content or vendor-biased comparisons
- Purely theoretical content with no practical application
- Content that ignores security or governance considerations
- Vendor prices or plan details added outside the two pricing source pages

## Questions?

Open an issue to discuss ideas before writing large contributions. This helps avoid duplicate effort and ensures alignment with the playbook's direction.
