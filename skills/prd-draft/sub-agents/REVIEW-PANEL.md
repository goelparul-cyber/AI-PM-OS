# /review-panel

## Invocation
`/review-panel <document or paste the content>`

## Goal
Run 7 independent reviewer perspectives against a document in parallel, then present a unified critique.

## The 7 reviewers
Each reviewer has its own prompt in sub-agents/. They are:

1. **eng-reviewer** — technical feasibility, dependencies, scale
2. **design-reviewer** — UX blind spots, user mental models, edge cases
3. **exec-reviewer** — business value, opportunity cost, strategic fit
4. **legal-reviewer** — privacy, compliance, liability flags
5. **data-reviewer** — metric validity, instrumentation, measurability
6. **gtm-reviewer** — positioning, launch readiness, sales enablement
7. **customer-reviewer** — support burden, adoption friction, churn risk

## Process
1. Read the document the user provides.
2. For each reviewer, apply its lens and generate 2-5 inline comments.
3. Each comment must be anchored to a specific section of the document.
4. After all 7 have run, present the output in a unified format.
5. Deduplicate — if two reviewers flag the same issue, merge into one comment and note both perspectives.

## Output format

```
## Review Panel — [Document Title]

**7 reviewers · X total comments · Y unique issues**

### Critical (must address before shipping)
- [Section: Problem Statement] **Eng + Data:** The success metric "improve retention" has no baseline or instrumentation plan. Engineering can't validate this without a data pipeline that doesn't exist yet.

### Important (should address)
- [Section: User Stories] **Design:** Stories only cover the happy path. What happens when the user has no data yet? Empty state is undefined.

### Consider (nice to address)
- [Section: Competitive Context] **GTM:** We name Competitor X but don't say what we do differently. Sales will get this question on every call.

### What's strong
- [1-2 sentences on what the document does well — reviewers aren't only critics]
```

## Severity rules
- **Critical:** The document has a gap that would cause a launch failure, user harm, or wasted eng cycles.
- **Important:** A gap that weakens the document but doesn't block launch.
- **Consider:** A suggestion that would improve quality but isn't essential.

## Deduplication rules
If two or more reviewers flag the same underlying issue (even from different angles), merge them into one comment and tag all contributing reviewers. Example: if Eng says "timeline is unrealistic" and Exec says "ROI doesn't justify 3-month investment" — those are the same issue (scope vs. value) and should be merged.
