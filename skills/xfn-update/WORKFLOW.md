# How /xfn-update executes

> Plain-English walkthrough of what happens when a PM invokes /xfn-update, from request received to artifact delivered.

This document is the human-readable companion to SKILL.md, checklist.md, and validator.md. It exists for two audiences:

1. PMs who want to understand what the skill does without reading three markdown files
2. Anyone building a UI or integration on top of this skill who needs to know what the model is doing on their behalf

---

## The 11 steps

### Step 1: Read CLAUDE.md (the house rules)

Before doing anything skill-specific, the model reads CLAUDE.md to internalize:

- House voice rules: no em dashes anywhere, pipes for tabular rows, colons for label/value pairs, short sentences, active voice
- House integrity rules: no fabricated content, mark missing data as `[TBD]`, every output ends with a confidence note
- The 3-file skill pattern and the validator-before-delivery requirement

### Step 2: Read SKILL.md (the skill instructions)

The model loads the /xfn-update SKILL.md, which contains:

- The skill's purpose (per-team status update with Status, Blockers, Asks, Risks)
- Input handling rules (what signals to extract from the messy input)
- The output template (Context section + per-team blocks)
- Voice rules inherited from CLAUDE.md
- Nine explicit non-goals (what the skill does NOT do)
- The workflow (which is what this document describes)

### Step 3: Read context-library/stakeholders.md (the team list)

This is the file that makes /xfn-update generalize across companies. It contains:

- The list of cross-functional teams that exist at your company
- The named lead for each team
- Per-team preferred update format (e.g. Eng wants bullets, Legal wants under 5 sentences, Data wants a metrics table)
- Stakeholder dynamics worth knowing

The skill uses this file to decide which teams to include and how to format each one. Without this file, the skill produces a generic update. With it, the skill produces a company-specific update tailored to each team's preferences.

### Step 4: Read context-library/voice.md (company writing style)

Layered on top of CLAUDE.md house voice. Contains:

- Vocabulary rules specific to your company
- Forbidden phrases
- Format defaults (e.g. XFN updates capped at 300 words, bullet-first)
- Length norms

### Step 5: Read context-library/company.md (business context)

For grounding only. The skill does not generate facts about the company. It uses this file to interpret the input correctly — knowing your company's stage, product, and north star metric changes how the model interprets shorthand in the input.

### Step 6: Process the messy input

The user pastes a chunk of project state: notes, jira ticket IDs, slack threads, calendar items, ad-hoc thoughts. The model extracts six signal categories:

1. Which teams are involved
2. What is the current project or workstream
3. What changed since last update
4. What is blocked, with reasons and owners
5. What we need from each team, with deadlines
6. What is unresolved or conflicting

If the input is too thin to support a real update, the skill stops and asks for richer input rather than fabricating sections.

### Step 7: Identify which teams have signal

Cross-reference the input against stakeholders.md. Only teams that appear in the input get sections. The model does NOT include a team just because it exists in stakeholders.md — the team must have actual signal in the input.

This is the first integrity check. It prevents the most common failure mode: padded sections for teams the input never mentioned.

### Step 8: Draft per-team sections

For each team with signal:

1. Apply the per-team format preference from stakeholders.md
2. Fill Status with concrete observations from the input (numbers, dates, named artifacts)
3. Fill Blockers only if the input contains blockers; otherwise drop the row entirely
4. Fill Asks with action + named recipient + deadline; if a deadline is inferred from stakeholders.md, mark it `[derived]` inline
5. **Fill Risks for every team.** Pull from stakeholders.md "Known concerns / red flags," from concrete project dependencies, from timeline pressure, or from known technical debt. Each risk gets 4 fields: risk, trigger, likelihood, impact. If genuinely no risk exists for the team this cycle, write "None identified this cycle."
6. Apply voice.md vocabulary rules

Sections are ordered by stakeholder importance per stakeholders.md. Within each team, the order is: Status, Blockers, Asks, Risks.

### Step 9: Run the checklist

Before delivery, the model walks checklist.md:

- Input completeness checks
- Structure checks (every blocker has reason + owner + date, every ask has recipient + deadline)
- Integrity checks (no invented teams, no soft asks, no padding)
- Voice and format checks (zero em dashes, pipes for rows)
- Inferred-date marking check
- Confidence note presence check

If any item in "Integrity" fails, the model does not deliver. Either the section is fixed or the user is asked for more input.

### Step 10: Score on the validator

Self-score on 6 dimensions, 4 points each, total 24:

| Dimension | What it measures |
|-----------|------------------|
| Team Coverage | Right teams included, no invented ones, ordered by importance |
| Status Specificity | Concrete numbers and named artifacts, not vague activity descriptions |
| Blocker Honesty | Every blocker has what + why + owner + date, no soft hedging |
| Ask Specificity | Every ask has action + recipient + deadline, no polite hedging |
| Integrity | No fabricated content, every claim traces to input, confidence note matches input quality |
| Risk Honesty | Every team has a Risks row with 4 fields, traced to real signal |

A score below 17 triggers revision. Below 12 triggers a request for richer input.

### Step 11: Deliver with confidence note

Output is delivered as a structured document with:

- Context section (2-3 sentences)
- Per-team blocks with Status, Blockers, Asks, Risks (empty rows dropped)
- Visible validator score
- Confidence note: `CONFIDENCE: [High / Medium / Low]. [one-line reason]`
- DOUBLE-CHECK line if any dimension scored 2 or below

---

## What makes this different from "just prompt Claude to write a status update"

Three things specifically:

**1. Context-grounded, not generic.** The skill reads stakeholders.md and produces a status update for the actual teams at your company, with the actual format preferences each team wants. A generic prompt produces a generic update.

**2. Integrity-first, not polish-first.** The skill refuses to invent owners, deadlines, or teams. Missing data stays missing, marked `[TBD]`. Inferred dates are flagged inline. A confident-sounding hallucination is the worst possible failure for a status update.

**3. Validated, not just produced.** The skill self-scores on 24 points before delivery and refuses to ship below threshold. The validator catches the five most common failure modes (padding, vagueness, soft blockers, polite asks, invented owners) by name.

---

## What this means for anyone building a UI on top of this skill

Every /xfn-update API call should:

1. Send CLAUDE.md + SKILL.md + checklist.md + validator.md as the system prompt
2. Send context-library/stakeholders.md + voice.md + company.md as additional context
3. Let the user paste their messy input as the user message
4. Stream the response so the chat feels responsive
5. Parse the confidence note and validator score from the output and display them as separate UI elements
