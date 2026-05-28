# interview-synth validator

Run this after drafting the synthesis. Output goes to validator-report.md.

## Quote verification
FOR each quoted string in the synthesis:
  1. Locate the exact string in the raw transcript
  2. If found verbatim → PASS (record line number)
  3. If not found verbatim → ORPHAN
     - Check if it's a close paraphrase → flag as PARAPHRASE, must be fixed
     - Check if it's a composite of two turns → flag as COMPOSITE, must be fixed
  4. Check surrounding context (2 turns before + after):
     - Does the interpretation hold? → PASS
     - Does context change the meaning? → CONTEXT FAIL, must fix insight

## Theme support check
FOR each theme:
  - Count independent supporting signals (quotes or observations)
  - If < 2 signals → flag as THIN THEME (note, don't auto-remove)

## Cross-reference check
FOR each insight in "Implications":
  - Scan decisions.md for related open questions
  - If match found and not already cross-referenced → flag MISSING XREF

## Output format  →  validator-report.md

# Validator report — [participant name] — [date]

## Summary
Quotes checked: N  |  PASS: N  |  ORPHAN: N  |  PARAPHRASE: N  |  CONTEXT FAIL: N

## Issues (fix before shipping)
| Quote (first 8 words) | Line ref | Issue type | Required action |
|-----------------------|----------|------------|-----------------|
| ...                   |          |            |                 |

## Thin themes (review, don't auto-fix)
-

## Missing cross-references
-

## Result
[ ] PASS — synthesis is clean, ready to share
[ ] FAIL — N issues must be resolved first
