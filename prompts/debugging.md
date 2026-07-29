# Debugging Prompts

> Prompts for investigation, root cause analysis, and fix verification.

## Bug Investigation

```
This test/function is producing incorrect results:
- Expected behavior: [what should happen]
- Actual behavior: [what happens instead]
- Reproduction: [input/steps that trigger the issue]
- Error message (if any): [paste error]

Investigate the root cause. Don't just fix the symptom.
Check: [list specific areas you suspect]
After identifying the cause, propose a fix and explain why it works.
```

## Error Diagnosis

```
We're seeing this error in [production/staging/tests]:

[paste error message and relevant stack trace]

Context:
- This started happening after [recent change / deployment / event]
- It affects [scope — all users / specific endpoint / specific condition]
- Frequency: [constant / intermittent / under load]

Diagnose the likely cause. If multiple possibilities, rank by likelihood.
For the most likely cause, suggest a fix.
```

## Performance Investigation

```
[Endpoint/function/query] is slow:
- Expected performance: [X ms]
- Actual performance: [Y ms]
- Conditions: [when does it slow down — load, data size, specific inputs?]

Analyze the code and identify potential bottlenecks.
Rank by likely impact (fix the biggest bottleneck first).
For each bottleneck, suggest a fix with estimated improvement.
```

## Root Cause Analysis (Post-Fix)

```
We fixed [bug/issue] by [describe the fix]. Now I need to understand:
1. Root cause: Why did this happen in the first place?
2. Contributing factors: What allowed this to slip through?
3. Prevention: What test or check would have caught this earlier?
4. Similar risks: Could this same type of issue exist elsewhere in our codebase?

Write a brief root cause analysis for our postmortem.
```

## Fix Verification

```
I've fixed [bug] by [describe change]. Verify my fix:
1. Does this fix address the root cause (not just the symptom)?
2. Could this fix introduce new issues?
3. What edge cases might still fail?
4. Write a regression test that would catch this if it recurs.
```

---

## Tips for Debugging Prompts

- Include actual error messages and stack traces (AI needs the specifics)
- Mention what changed recently (most bugs come from recent changes)
- Ask for root cause, not just symptom fix
- Request regression tests alongside the fix
- Include environment details if relevant (versions, OS, configuration)
