name: startsession
invoke: /startsession <primer.md contents>

## Goal
Resume a PM OS session exactly where it left off using the contents of primer.md.

## Process

### Step 1 — Read primer.md
Read both layers carefully before responding.

### Step 2 — Check for a fresh install or first session
- If Layer 1 still contains placeholder brackets (e.g. `[Your name, role, and company]`): this is a fresh install. Skip Steps 3 and 4. Tell the user to fill in Layer 1 of primer.md and the context-library files first, then stop.
- If Layer 1 is filled in but Layer 2 still says `[Populated by /endsession]`: this is the first real session. Skip the Layer 2 recap in Step 3. Acknowledge Layer 1 only, then ask what they want to work on today.
- Otherwise, continue to Step 3 as normal.

### Step 3 — Acknowledge context
Briefly confirm what you know:
- Who the PM is and their preferences (Layer 1)
- What was being worked on (Layer 2)
- What the next action is (Layer 2)

Keep this short — 3-4 lines max. The PM wants to get back to work, not read a summary.

### Step 4 — Prompt next action
End with a single line: "Ready to pick up where we left off — [next action]. Shall we?"

## Output format
Short, warm, confident. No bullet points. 
The PM should feel like they never left.