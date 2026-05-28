# /prd-draft Validator

Runs AFTER the draft is complete. This is a separate pass — never combined with drafting.

## Step 1: Language check
Read the entire PRD and answer:
- Can a new hire understand the problem statement in one read? Y/N
- Are there any jargon terms used without definition? List them.
- Are there paragraphs longer than 4 sentences? List them.
- Any passive voice? ("will be built," "is expected to") List instances.

## Step 2: Checklist sweep
For EACH item in checklist.md:
- Re-read the relevant section
- Pass (Y) or Fail (N)
- If fail: one sentence explaining what's missing

## Step 3: Diagram validation
- Does section 3 contain at least one Mermaid process flow? Y/N
- Does section 3 contain at least one Mermaid system diagram? Y/N
- For complex system changes: do both current-state and proposed-state exist? Y/N
- Do the diagrams actually match the solution described in the text? (Read both and compare)

## Step 4: Dependency completeness
- Read the dependency matrix
- For each system mentioned ANYWHERE else in the PRD: does it appear in the matrix? Flag any missing.
- Are there dependencies marked as "uncertain"? (Good — this means the PM is being honest)
- Do uncertain dependencies reappear in section 9 (Open Questions)?

## Step 5: Metric validation
For each success metric:
- Has a measurement? Y/N
- Has a baseline? Y/N
- Has a target? Y/N
- Has a timeframe? Y/N
- Is there at least one leading indicator? Y/N
- Is there at least one guardrail? Y/N

## Step 6: Prototype check
- Was a React component generated? Y/N
- Is it functional (interactive) or just static markup? Flag if static.
- Does it match the solution described in sections 3-4? Y/N

## Output format

```
## Validator Report — /prd-draft

**Feature type:** [New feature / New product / System change / ML-AI / Internal]
**Overall: X/Y checks passed**

### Language quality
- New-hire readable: Y/N
- Jargon without definition: [list or "none"]
- Long paragraphs: [list or "none"]
- Passive voice instances: [count]

### Section-by-section results
| Section | Checks | Passed | Failed | Issues |
|---|---|---|---|---|
| Problem statement | 3 | 3 | 0 | — |
| Impact & stakeholders | 2 | 1 | 1 | Missing team: [which] |
| ... | ... | ... | ... | ... |

### Dependency gaps
- Systems mentioned but not in matrix: [list]
- Uncertain dependencies without investigation owners: [list]

### Metric gaps
- Incomplete metrics: [list which are missing baseline/target/timeframe]

### Prototype assessment
- Generated: Y/N
- Functional: Y/N
- Matches solution: Y/N

### Top 3 things to fix before sharing
1. [Most critical gap]
2. [Second]
3. [Third]
```
