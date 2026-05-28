name: interview-synth
invoke: /interview-synth <transcript-file>

# Goal
Convert a raw interview transcript into a structured synthesis where every
quoted claim is verified word-for-word against the source.

# Inputs
- transcript file (paste or file path)
- context-library/users.md       — for persona matching
- context-library/decisions.md   — to flag insights that touch open questions

# Output
- interview-synth-[name]-[date].md  — structured synthesis
- validator-report.md               — quote verification pass/fail

# Process
1. Read checklist.md
2. Parse transcript: identify speaker turns, timestamps if present
3. Draft synthesis (sections: summary, key themes, verbatim quotes, implications)
4. Run validator.md: verify every quote against raw transcript
5. If any quote fails → mark ORPHAN, revise or remove
6. Output synthesis + validator-report.md

# Output format
## One-line summary
[What this person told us in a single sentence]

## Key themes  (max 5)
### [Theme name]
- [insight] — "[verbatim quote]" (line [N])
- [insight] — "[verbatim quote]" (line [N])

## Implications
- [so what for the product / roadmap]
- Cross-ref: [any open question in decisions.md this touches]

## Raw signals (unclassified)
- [anything notable that didn't fit a theme]
