# exec-update checklist

## Pre-Flight
- [ ] context-library/voice.md read
- [ ] context-library/stakeholders.md read
- [ ] If PM named a specific exec: their priorities and red flags identified from stakeholders.md
- [ ] Minimum viable input confirmed:
  - [ ] Status color present (RED / YELLOW / GREEN)
  - [ ] People named specifically, not "the team"
  - [ ] Dates are actual dates, not "soon" or "next week"
  - [ ] Metrics have numbers, not adjectives
  - [ ] Dependencies named with status (confirmed, pending, unresponsive)

## In-Flight
- [ ] If minimum viable input is missing: all gaps consolidated into one single question to PM
- [ ] After PM responds once: draft immediately with what's available, mark remaining gaps [TBD]
- [ ] Update drafted in exact order:
  - [ ] Project name + one-line description
  - [ ] Status color with appropriate explanation
  - [ ] Bottom Line
  - [ ] Highlights (3-5 points, each with a "so what")
  - [ ] Decisions / Asks with clear ownership signal
  - [ ] Top risk with active mitigation

## Reviews
- [ ] eng-reviewer.md run against draft
- [ ] design-reviewer.md run against draft
- [ ] exec-reviewer.md run against draft
- [ ] HIGH concerns from all three collected

## Validation
- [ ] validator.md run against draft
- [ ] Autonomous fixes applied
- [ ] Remaining issues flagged to PM

## Delivery
- [ ] Part 1: clean exec update, ready to send
- [ ] Part 2: HIGH concerns from sub-agent reviewers (skip if none)
- [ ] CONFIDENCE: [High / Medium / Low] with one-line reason based on input quality
