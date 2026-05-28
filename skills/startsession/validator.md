# startsession validator

## What Claude fixes autonomously
- Resume briefing over 4 lines → trim to essentials: 
  project, open items, next action
- Generic acknowledgment with no specifics → rewrite using 
  Layer 2 details
- Next action stated instead of prompted → rewrite as 
  "Ready to pick up — [action]. Shall we?"

## What Claude flags to the PM
- primer.md is empty or missing → flag: "I don't have a session 
  snapshot to load. Can you paste your primer.md contents or 
  tell me what we were working on?"
- Layer 2 next action is vague → flag: "Your last session noted 
  [vague next action]. Can you clarify what to pick up first?"
- Layer 1 and Layer 2 contradict each other → flag: "I see a 
  conflict between your standing preferences and last session's 
  decisions. Which should I follow?"

## Section checks
- [ ] Active project and skill named specifically?
- [ ] Open items surfaced if any exist?
- [ ] Next action prompted, not stated?
- [ ] Layer 1 preferences applied silently?

## Quality checks
- [ ] Resume briefing 3-4 lines max?
- [ ] Reads like continuity, not a report?
- [ ] No meta-references to primer.md or memory system?

## Output
If all checks pass: deliver the resume briefing and wait for PM response.
If flags exist: surface them before resuming so PM can resolve.