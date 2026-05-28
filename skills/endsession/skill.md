name: endsession
invoke: /endsession
goal: Capture the current session so the PM can pick up exactly where they left off.
inputs: Full conversation history, existing primer.md
output: Updated primer.md with both layers populated
process: 1. Read checklist. 2. Capture session. 3. Update primer. 4. Validate. 5. Deliver.

---

## Goal
Capture the current session so the PM can pick up exactly where they left off.

## Process

### Step 1 — Read the full conversation
Review the entire conversation from this session. Identify:
- What skill or task was being worked on
- What stage or version it's at
- What decisions were made
- What's still open or unresolved
- What the next action is

### Step 2 — Update Layer 2
Write a clean Layer 2 snapshot with all five fields:
- **What we were working on:** The skill or task and what it was for
- **Current state:** Where the artifact or work stands right now
- **Decisions made this session:** Specific decisions with enough context to understand them later
- **Open items:** Anything unresolved, blocked, or still pending
- **Next action:** One concrete, specific action the PM should take next session

Layer 2 should be specific enough that the PM can pick up without re-reading the conversation.

### Step 3 — Update Layer 1
Review the current session for explicit preference statements only. Look for:
- "I always...", "I prefer...", "we never...", "from now on...", "I want you to always..."

If found: append to the relevant Layer 1 section. Do not overwrite existing entries.
If not found: leave Layer 1 unchanged.

> **Note:** Claude cannot detect patterns across previous sessions. Layer 1 auto-updates are limited to explicit preference statements made in the current session. Cross-session pattern detection is a planned v2 feature.

### Step 4 — Output the updated primer.md
Output the complete updated primer.md — both layers — as a clean markdown block.

**If running in Claude Code:** primer.md is updated automatically.
**If running in Claude.ai:** Tell the PM: "Copy this into your primer.md file to save your session."

## Output format
Clean markdown. Both layers. Complete. Ready to copy-paste into primer.md.
