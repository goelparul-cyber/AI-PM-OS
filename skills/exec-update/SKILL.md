# exec-update

name: exec-update
invoke: /exec-update <pm-notes>
goal: Convert a PM's messy notes into a 1-pager a Sr Director or VP reads in under 2 minutes.
inputs: PM notes (required), checklist.md, validator.md, eng-reviewer.md, design-reviewer.md, exec-reviewer.md
output: A clean 1-pager ready to send, plus HIGH reviewer concerns under "Before you send"
process: 1. Read checklist. 2. Check minimum viable input. 3. Draft. 4. Run sub-agent reviews. 5. Validate. 6. Deliver.

## Process

### Step 1 — Read context and notes
Read in this order before doing anything else:
1. context-library/voice.md — to match the team's communication style
2. context-library/stakeholders.md — to understand the exec audience
3. PM's notes — the input to process

If context-library files are missing or empty, proceed with defaults.
Do not block on missing context.

**How to use stakeholders.md:**
- If the PM identifies the exec audience → find them in stakeholders.md and tailor 
  the update to what they care most about
- If no exec is named → use the general Sr Director framing as default
- Flag stakeholder-specific risks if relevant:
  - Project touches Points system → note Tom's likely skepticism
  - Financial feature → check if Lena has been looped in with enough lead time
  - Scope has changed → note Marcus's sensitivity to surprise scope creep
  - No comms plan mentioned → note Anita's frustration with unplanned launches
- Inform the Decisions/Asks section with what this specific stakeholder needs:
  - Use "what they care most about" to frame the ask in their language
  - Use "known concerns / red flags" to anticipate pushback

### Step 2 — Check for minimum viable input
Before drafting, scan for gaps. Combine ALL of the following into one single question:

- Status color if missing
- Specificity gaps:
  - People with no names
  - Dates with no actual date
  - Metrics with no numbers
  - Meetings with no outcome or decision
  - Dependencies with no name, date, or response status

Ask everything in one message, like this:
"Before I draft, a few quick gaps to close:
1. Status color? RED / YELLOW / GREEN
2. [specific gap]
3. [specific gap]"

After the PM responds once — draft immediately with what you have.
Flag anything still missing as [TBD] in the output.
Exception: if the PM fundamentally changes the nature of the update 
(e.g. from informational to decision-needed), ask one focused follow-up 
to capture the new ask. Then draft immediately.

### Step 3 — Draft the update
Using checklist.md, draft the update in this exact order:
1. Project name + one-line description
2. Status color
   - RED or YELLOW: add one sentence explaining what is driving it
   - GREEN: add one short clause only e.g. "GREEN — on track, no blockers"
3. Bottom Line
4. Highlights
5. Decisions / Asks
6. Top risk

### Step 4 — Run sub-agent reviews
Run all three reviewers against the draft in parallel:
- eng-reviewer.md — technical accuracy and risk honesty
- design-reviewer.md — narrative clarity and flow
- exec-reviewer.md — readability and actionability

Collect HIGH concerns only. Ignore MED and LOW.

### Step 5 — Validate
Run every check in validator.md.
Fix what you can fix autonomously.
Flag what needs PM judgment.

### Step 6 — Deliver
Present the output in two parts:

Part 1 — the exec update, clean and ready to send.

Part 2 — Before you send:
🔧 Eng: [HIGH concern or "No HIGH concerns"]
🎨 Design: [HIGH concern or "No HIGH concerns"]
👔 Exec: [HIGH concern or "No HIGH concerns"]

If all three have no HIGH concerns, skip Part 2 and say:
"All three reviewers passed. Ready to send."

End with:
CONFIDENCE: [High / Medium / Low]. [one-line reason based on input quality]

Example: CONFIDENCE: Medium. Notes were thin on timeline and dependency status.