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
   - Project instructions (CLAUDE.md, .cursorrules, steering files)
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
