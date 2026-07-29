# Example: CI/CD Integration

> GitHub Actions workflows that integrate AI into your development pipeline.

## Example 1: PR Summary Generator

This action calls an AI API to generate a structured PR description from the diff.

```yaml
# .github/workflows/pr-summary.yml
name: Generate PR Summary

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  summarize:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Get diff
        id: diff
        run: |
          DIFF=$(git diff origin/${{ github.base_ref }}...HEAD -- '*.ts' '*.tsx' '*.py' '*.java' | head -c 10000)
          echo "diff<<EOF" >> $GITHUB_OUTPUT
          echo "$DIFF" >> $GITHUB_OUTPUT
          echo "EOF" >> $GITHUB_OUTPUT

      - name: Generate summary
        id: summary
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          # Call AI API with diff, parse response
          # This is a simplified example — production would use a proper script
          curl -s https://api.anthropic.com/v1/messages \
            -H "x-api-key: $ANTHROPIC_API_KEY" \
            -H "content-type: application/json" \
            -H "anthropic-version: 2023-06-01" \
            -d '{
              "model": "claude-3-5-haiku-20241022",
              "max_tokens": 1024,
              "messages": [{"role": "user", "content": "Summarize this PR diff in 3-5 bullet points. Focus on what changed and why it matters:\n\n${{ steps.diff.outputs.diff }}"}]
            }' | jq -r '.content[0].text' > summary.txt

      - name: Post comment
        uses: actions/github-script@v7
        with:
          script: |
            const fs = require('fs');
            const summary = fs.readFileSync('summary.txt', 'utf8');
            await github.rest.issues.createComment({
              owner: context.repo.owner,
              repo: context.repo.repo,
              issue_number: context.issue.number,
              body: `## AI Summary\n\n${summary}\n\n---\n*Generated automatically. May not capture full context.*`
            });
```

**Cost:** ~$0.01–0.05 per PR (using Haiku for summarization).

**Notes:**
- Uses Haiku (cheapest model) since summarization doesn't need deep reasoning
- Truncates diff to 10K chars to control cost
- Disclaimer on the comment so reviewers know it's AI-generated
- Only processes code files (skips lock files, generated code)

---

## Example 2: Coverage Gap Detector

```yaml
# .github/workflows/coverage-check.yml
name: Coverage Gap Alert

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  coverage-check:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: '20'

      - run: npm ci

      - name: Run tests with coverage
        run: npm run test:coverage -- --reporter=json --outputFile=coverage.json

      - name: Check for uncovered new code
        run: |
          # Script that:
          # 1. Gets list of changed files
          # 2. Checks coverage for those files
          # 3. If any file <80% coverage, flags it
          node scripts/check-coverage-gaps.js

      - name: Comment if gaps found
        if: steps.coverage.outputs.has_gaps == 'true'
        uses: actions/github-script@v7
        with:
          script: |
            // Post comment listing uncovered files with suggestion
            // "Consider adding tests for: [list of files]"
```

**Cost:** 🆓 (no AI API call — just coverage analysis).

---

## Example 3: AI-Assisted Security Scan

```yaml
# .github/workflows/security-ai.yml
name: AI Security Review

on:
  pull_request:
    paths:
      - 'src/auth/**'
      - 'src/middleware/auth*'
      - 'src/api/admin/**'

jobs:
  security-review:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Get security-relevant diff
        id: diff
        run: |
          git diff origin/${{ github.base_ref }}...HEAD -- src/auth/ src/middleware/auth* src/api/admin/ > security-diff.txt

      - name: AI Security Review
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          # Only runs when auth/admin code changes
          # Uses a more capable model for security analysis
          # Posts findings as PR review comments
          node scripts/ai-security-review.js security-diff.txt
```

**Cost:** ~$0.05–0.30 per relevant PR (only triggers for auth/admin code changes).

**Key design decisions:**
- Only runs when security-relevant paths change (not every PR)
- Uses a more capable model (worth the cost for security)
- Triggers a review comment, not a blocking check (advisory only)

---

## Cost Management Tips

1. **Use cheap models for simple tasks** — Haiku/GPT-4o-mini for summaries, better models for security
2. **Truncate inputs** — Don't send entire files when a diff suffices
3. **Trigger selectively** — Not every PR needs every AI check
4. **Cache where possible** — Don't re-analyze unchanged files
5. **Set budget alerts** — Monitor monthly CI-AI costs separately
