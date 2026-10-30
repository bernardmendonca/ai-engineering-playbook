# Upskilling

> Training developers to be effective with AI tools — beyond "here's how to install it."

## The Skill Shift

AI tools don't just require knowing which buttons to press. They require a new set of skills:

| Old skill (still needed) | New skill (additive) |
|-------------------------|---------------------|
| Writing code | Reviewing and directing AI-written code |
| Debugging by reading code | Debugging by prompting and constraining |
| Searching documentation | Asking AI and validating answers |
| Planning implementation | Decomposing tasks for AI suitability |
| Reviewing human code | Reviewing AI code (different failure patterns) |
| Writing tickets for humans | Writing task specs an agent can complete unsupervised |
| Learning by doing | Learning *with* AI without letting it do the learning for you |

---

## Training Curriculum

### Level 1: Awareness (All developers, 30 minutes)

**Format:** Recorded presentation or live session
**Content:**
- What AI coding tools can and can't do
- Our approved tools and where to get access
- Our policy: what's allowed, what's not
- Where to get help (channel, docs, office hours)
- Quick demo: one impressive example and one failure

**Outcome:** Everyone knows what's available and what the rules are.

---

### Level 2: Basic Proficiency (All interested developers, 2 hours)

**Format:** Hands-on workshop (live or self-paced)
**Content:**
1. Tool setup and configuration (15 min)
2. Effective prompting basics (30 min)
   - Be specific about what you want
   - Provide context (file, language, framework)
   - Iterate: first output is rarely final
3. Autocomplete + chat usage (30 min)
   - When to accept suggestions
   - How to ask good questions
   - Using chat for explanation and exploration
4. Agent basics (30 min)
   - Starting an agent task
   - Reviewing agent output
   - When to stop and take over
5. Practice tasks (15 min)
   - Generate tests for a real module
   - Refactor with AI assistance
   - Ask AI to explain unfamiliar code

**Outcome:** Developers can use AI tools effectively for daily work.

> ✅ **My take on training investment:** Level 2 (2-hour hands-on workshop) is the minimum viable training for any team adopting AI tools. Skipping directly to "here's your login, figure it out" cuts adoption in half. The 2-hour workshop is non-negotiable. Level 3 (advanced) is optional and should target your 20% of power users — they'll become your champions. Don't send everyone to Level 3; it's not worth the time for developers who will be light users.

---

### Level 3: Advanced Usage (Power users, 4 hours over 2 weeks)

**Format:** Self-paced with weekly group discussion
**Content:**
1. Prompt engineering for code (1 hour)
   - System prompts and custom instructions
   - Context management: what to include, what to exclude
   - Multi-turn prompting strategies
   - Chain-of-thought for complex tasks
2. Agent mastery (1 hour)
   - Task decomposition for agents
   - Configuring autonomy levels
   - Cost management and budget awareness
   - Recognizing when to stop an agent
3. Custom workflows (1 hour)
   - Project instructions (AGENTS.md, plus tool overlays such as CLAUDE.md, Cursor rules, Kiro steering)
   - Building reusable prompts for team patterns
   - CI/CD integration patterns
4. Review skills (1 hour)
   - Reviewing AI-generated PRs (what to watch for)
   - Quality assessment of AI output
   - Teaching AI your standards

**Outcome:** Developers are highly effective and help others.

---

## Training Delivery Methods

| Method | Best for | Investment |
|--------|----------|-----------|
| **Self-serve docs + videos** | Basic awareness, reference material | 🆓 One-time creation effort |
| **Live workshop** | Basic proficiency, group learning | 🆓 2 hours of facilitator time + attendees |
| **Pair programming with AI expert** | Advanced skills transfer | 🆓 Expert's time (1:1 or 1:3) |
| **Office hours** | Ongoing questions, troubleshooting | 🆓 1 hour/week |
| **Internal blog/tips series** | Continuous improvement, culture | 🆓 20 min/week to write |
| **External training/course** | Deep skill building, certification | 💰 $500–2000/person |
| **Hackathon/AI day** | Exploration, team building, generating excitement | 🆓 + 💰 one day of team time |

---

## The Prompt Engineering Minimum

Every developer should understand these basics:

### 1. Be Specific
```
❌ "Fix this code"
✅ "Fix the null pointer exception in the processOrder function.
    The issue occurs when items array is empty."
```

### 2. Provide Context
```
❌ "Write a test"
✅ "Write a unit test for the UserService.createUser method.
    Follow the pattern in UserService.test.ts.
    Use Jest. Mock the database layer."
```

### 3. Constrain the Output
```
❌ "Refactor this"
✅ "Refactor this function to:
    - Separate validation from processing
    - Use early returns for error cases
    - Keep the same public interface
    - Don't change behavior, only structure"
```

### 4. Iterate, Don't Accept First Output
```
First: "Implement pagination for the /users endpoint"
Then: "Add input validation for page and limit parameters"
Then: "Handle the edge case where page exceeds total pages"
Then: "Add tests for the boundary conditions"
```

---

## Learning With AI, Not Instead of It

Using AI to get work done and using AI to learn are different activities, and the same habits don't serve both.

Anthropic researchers ran a randomized trial (January 2026) with developers learning a new asynchronous Python library. The group with AI assistance scored **17% lower** on a comprehension quiz covering concepts, code reading, and debugging (about 50% vs. 67%), and wasn't significantly faster on average. Developers who fully delegated the coding learned the least. But three of the six interaction patterns the researchers identified preserved learning even with AI help, and they all involved staying cognitively engaged.

**Habits that preserve learning** (teach these explicitly):

| Instead of… | Do this |
|-------------|---------|
| "Write the function that does X" | "Explain how this library handles X, then I'll write it" |
| Accepting a fix you don't understand | Ask why the bug happened and why the fix works before accepting |
| Letting the agent pick the approach | Sketch your approach first, then ask the AI to critique it |
| Reading only the final diff | Ask the agent to explain the change, then predict what a test would show before running it |
| Delegating the first task in a new area | Do the first one or two by hand (with AI as a tutor), then delegate the repetitive ones |

These habits cost some speed. That's the right trade when someone is learning a codebase, a language, or a domain they'll need to debug and review later.

> ✅ **My take:** Separate "learning mode" from "delivery mode" in your team norms. When someone is new to an area, the goal is understanding, and AI should be a tutor. Once they know the area, the goal is throughput, and AI can do the typing. The failure is staying in delivery mode forever and never building the judgment needed to review what the agent produces.

---

## The Junior Pipeline

Agents do much of the work that used to train junior engineers: boilerplate, small bug fixes, tests. Hiring data is moving with it. Stanford's Digital Economy Lab (August 2026 update) finds employment of 22–25-year-olds in AI-exposed occupations, software development included, about 19% below where it would be if it had tracked less-exposed occupations. Experienced workers show no comparable gap.

Fewer juniors now means fewer mid-level and senior engineers in a few years, and seniors are exactly the people who can judge agent output. Plan for this deliberately.

### For juniors already on the team

- **"Code solo first" on unfamiliar ground.** For their first weeks in a new area, juniors write code with AI as a tutor, not an author
- **Explain-back in review.** Juniors explain their AI-assisted PRs in their own words; reviewers ask "why" questions, not just "what"
- **Debugging rotations.** Give juniors real bug investigations, where understanding the system is the point
- **Pair with seniors on agent review.** Reviewing agent PRs alongside a senior is one of the fastest ways to learn what good looks like

### For hiring and leveling

| Area | What changes |
|------|-------------|
| **Interviews** | Test judgment as well as production: reviewing a flawed AI-generated PR, decomposing a vague task, explaining tradeoffs. Decide and state your policy on AI use during interviews |
| **Leveling expectations** | Move weight toward specification, decomposition, verification, and review quality. Lines of code and PR count were never good signals and are worse now |
| **Junior hiring** | Keep a junior pipeline sized for the senior engineers you'll need in three to five years, not just this year's output |
| **Onboarding** | Teach the codebase before teaching the agent; a new hire who learns both at once learns neither well |

> ✅ **My take:** Cutting junior hiring because agents do junior work is a short-term saving with a long-term cost. The teams that do well with agents are the ones with enough experienced reviewers, and you only get experienced reviewers by training juniors.

---

## Measuring Training Effectiveness

| Signal | What it tells you |
|--------|-------------------|
| Tool adoption after training (should increase) | Training was relevant and motivating |
| Questions in support channel decrease over time | Self-sufficiency improving |
| Quality of AI-generated PRs improves | Skills improving, better prompts/review |
| Developers sharing tips with each other | Culture building, knowledge spreading |
| Requests for advanced training | Demand exists, basic training worked |

---

## Next

- Building champions → [Champions Model](./champions-model.md)
- Managing resistance → [Handling Resistance](./handling-resistance.md)
- Return to section overview → [README](./README.md)
