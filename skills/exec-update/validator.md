# exec-update validator

## What Claude fixes autonomously
- Word count over 400 → trim in this order: Highlights first (cut weakest "so what"), 
  then risk mitigation detail, then gist. Never cut status color, ask, or project description.

## What Claude flags to the PM
- Status color and risk/Bottom Line tell different stories → ask: "Your status is [COLOR] but 
  your Bottom Line / top risk says [X]. Should the status be YELLOW, or is the risk lower 
  priority than it sounds?"
- Any section where Claude had to guess because notes were too thin → flag which section 
  and what was assumed
- Decisions/Asks and Top Risk feel repetitive → check: Asks = what exec needs to DO, 
  Risk = what happens if they DON'T. If both are still saying the same thing after 
  that lens, flag to PM.
- If the update contains a sequence of dependent steps with dates → check if 
  the timeline is realistic. If steps are back-to-back with no buffer between 
  them, do not call it "tight but achievable." Instead flag: "The sequence of 
  [X → Y → Z] leaves no buffer. If anything slips in [X], [Y] and launch are 
  at risk. Is this reflected in the status color?"

## Section checks
- [ ] Project name + description present and jargon-free?
- [ ] Status color stated with appropriate explanation?
  - RED or YELLOW: reason given in one sentence?
  - GREEN: one short clause only, not a full sentence?
- [ ] Bottom Line captures the single most important thing?
- [ ] Highlights: 3-5 points, each with a "so what"?
- [ ] Decisions/Asks starts with a clear ownership signal — is it obvious 
      whether the exec needs to act or just read?
- [ ] Top risk: one risk with active mitigation stated?

## Quality checks
- [ ] Total word count 400 words or fewer?
- [ ] Do status color, gist, and risk tell the same story?
- [ ] Any jargon or acronyms that aren't explained?
- [ ] Are asks specific with a deadline or decision point?
- [ ] House voice rules followed — no em dashes, named owners, numbers over adjectives, no forbidden phrases?

## Output
If any section check fails: fix autonomously if in scope above, otherwise flag to PM.
If all checks pass: deliver the update.