# endsession validator

## Layer 2 quality checks
- [ ] "What we were working on" names the specific skill and artifact — not just "worked on a doc"
- [ ] "Current state" describes where the work stands precisely — not just "in progress"
- [ ] "Decisions made" includes enough context to understand each decision without re-reading the conversation
- [ ] "Open items" are specific — not just "follow up needed"
- [ ] "Next action" is a single concrete action — not a list, not vague

## Layer 1 quality checks
- [ ] Only explicit preference statements promoted — not session details or one-off decisions
- [ ] New entries appended, not overwriting existing ones
- [ ] If no explicit preferences stated this session, Layer 1 is unchanged

## Overall output quality
- [ ] PM can read the primer.md output and pick up next session without re-reading this conversation
- [ ] No invented details — everything traceable to the actual conversation
- [ ] Both layers present and complete in the output block

## What Claude fixes autonomously
- Next action is vague → rewrite as a specific, concrete action
- Layer 2 field is generic → rewrite using specific details from the conversation
- Layer 1 entry is a session detail not a standing preference → move to Layer 2 open items instead

## What Claude flags to the PM
- Conversation too short or unclear to produce a reliable session capture → flag: "This session doesn't have enough to capture. Can you tell me what you worked on and what the next action is?"
- Next action genuinely ambiguous → flag: "I identified two possible next actions: [A] and [B]. Which should I record?"

## Confidence note
Every endsession output ends with:
`CONFIDENCE: [High / Medium / Low]. [one-line reason]`
