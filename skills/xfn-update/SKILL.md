name: xfn-update
invoke: /xfn-update <project-name or paste project state>
goal: Convert raw project state into a status update organized by cross-functional team, with status, blockers, asks, and risks per team.
inputs: project state (notes, tickets, slack threads, calendar events) + context-library/stakeholders.md (for team list and tone preferences)
output: A structured update with one section per cross-functional team. Each section has Status, Blockers, Asks, and Risks.
process: 1. Read checklist. 2. Identify which teams are involved. 3. Draft per-team sections. 4. Validate. 5. Revise if fail.

# /xfn-update: Cross-Functional Status Update

## Purpose

Most cross-functional updates are written for one audience and forwarded to four. The result is that every team reads through irrelevant content to find their part, and most teams miss their actual asks.

This skill produces an update where each team finds their section in 5 seconds and knows exactly:

1. **Status**: what is happening that affects them
2. **Blockers**: what is stuck and why
3. **Asks**: what we need from them this week
4. **Risks**: what could go wrong, the trigger, the likelihood, and the impact

## When to use this skill

Trigger when the user provides:
- Raw project notes, jira tickets, slack threads, or meeting notes
- A request for a "weekly update", "status update", "team update"
- An ask like "what should I tell eng / design / data this week"

Do NOT use this skill for:
- Exec summaries (use /exec-update)
- PRDs (use /prd-draft)
- User research synthesis (use /interview-synth)

## Input handling

Before drafting, extract these signals from the input:

1. **Which teams are involved?** Read context-library/stakeholders.md. Common teams: Eng, Design, Data, Legal, GTM, CS, Finance. Only include teams the input actually mentions or implies.
2. **What is the current project or workstream?** One sentence.
3. **What changed since last update?** Status updates only matter if there is delta.
4. **What is blocked?** A blocker has a name, a reason, and an owner.
5. **What do we need from each team?** Asks are specific, time-bound, and addressed to a named person or role.

If the input is too thin to support a real update (3 lines of notes, no team signal), stop and ask for richer input rather than fabricating sections.

## Output template

Use this structure. Repeat the team block for every team involved.

```
XFN UPDATE: [Project Name] | Week of [date]

CONTEXT (2-3 sentences)
What this project is, what changed this week, what is up next.

==========

ENGINEERING

Status:
- [What is happening that affects eng]
- [What shipped, what is in flight]

Blockers:
- [Blocker]: [why it is stuck] | Owner: [name] | Needed by: [date]

Asks:
- [Specific ask] | Addressed to: [name or role] | By: [date]

Risks:
- [Risk] | Trigger: [what would make it real] | Likelihood: [Low/Med/High] | If it hits: [impact]

==========

DESIGN

Status:
- [...]

Blockers:
- [...]

Asks:
- [...]

Risks:
- [...]

==========

[Repeat for each team: Data, Legal, GTM, CS, Finance, etc.]

==========

VALIDATOR: [N]/24 | Team Coverage [n]/4 | Status Specificity [n]/4 | Blocker Honesty [n]/4 | Ask Specificity [n]/4 | Integrity [n]/4 | Risk Honesty [n]/4
CONFIDENCE: [High / Medium / Low]. [one-line reason]
```

## Voice rules (inherited from CLAUDE.md house voice)

- No em dashes anywhere. Use commas, colons, periods, or pipes.
- Pipes for tabular rows: `Blocker | Owner | Needed by`
- Colons for label/value pairs: `Status:`, `Owner:`
- Short sentences. Active voice.
- Numbers over adjectives: "3 tickets blocked" not "several tickets blocked".
- Mobile readable. Each team section scannable in 5 seconds.

## What this skill does NOT do

1. Does not invent teams that were not in the input. If the input only mentions Eng and Design, the update only has Eng and Design sections.
2. Does not invent blockers, owners, or deadlines. Missing data stays `[TBD]`.
3. Does not soften asks. If the user owes Design a decision by Tuesday, the ask says so.
4. Does not produce a generic narrative paragraph. The structure IS the value.
5. Does not include a team section that has no Status, no Blockers, no Asks, AND no Risks. Empty sections get dropped, not padded.
6. **Does not include empty Status, Blockers, or Asks rows within a section.** If a team has Status and Asks but no Blockers, drop the Blockers row entirely. Do not write "Blockers: None this week."
7. **Marks inferred dates inline with `[derived]`.** Any deadline pulled from context-library/stakeholders.md or implied from project context (not explicitly stated in the input) is marked `[derived]` next to the date. Example: `By: May 1 [derived from stakeholders.md: legal needs 1 week before launch]`. Do not bury the inference only in the confidence note.
8. **Does not skip the Risks row.** Risks are required for every included team, even when the input does not state them explicitly. If genuinely no risk exists for a team this week, write `Risks: None identified this cycle.`
9. **Does not invent risks.** Risks must trace to something real: a stakeholders.md red flag, a concrete dependency, a tight timeline, a known technical debt area. Generic risks like "scope creep" or "team capacity" without a specific trigger are not allowed.

## Workflow

1. Read input end-to-end before drafting.
2. Read context-library/stakeholders.md for team list and tone.
3. Identify which teams have signal in the input.
4. Run the checklist (checklist.md).
5. Draft per-team sections.
6. Run the validator (validator.md). Self-score on 24 points across 6 dimensions.
7. If score below 17, revise. If below 12, ask for richer input.
8. Deliver with **visible validator score** and confidence note.

## Output footer (required)

Every output ends with these two lines, in this order, after the last team section:

```
VALIDATOR: [N]/24 | Team Coverage [n]/4 | Status Specificity [n]/4 | Blocker Honesty [n]/4 | Ask Specificity [n]/4 | Integrity [n]/4 | Risk Honesty [n]/4
CONFIDENCE: [High / Medium / Low]. [one-line reason]
```

If any dimension scored 2 or below, add a third line:

```
DOUBLE-CHECK: [the specific section or claim that scored low]
```

## Edge cases

- **Only one team has signal**: still produce the update with one team section. Note in confidence why.
- **A team has Status but no Blockers or Asks**: include the section with just Status. Do not pad.
- **Conflicting info across input sources**: flag the conflict in the relevant team section. Do not pick one.
- **A team is mentioned but no specifics**: do not create a section for them. Note in confidence.

## Sample output shape

```
XFN UPDATE: Pricing Tier Rollout | Week of April 25

CONTEXT
Hybrid pricing model approved last week (usage-based for enterprise, flat for mid-market).
Eng started build Monday. Design pricing page redesign in flight. Finance modeling cap risk.

==========

ENGINEERING

Status:
- Usage tracking infra build started Monday, week 1 of 3
- Cap logic spec'd, build starts week 2

Asks:
- Confirm parallel build plan for cap logic | Addressed to: [Eng Lead] | By: April 28

Risks:
- Cap logic complexity may extend week 2 build | Trigger: dependency on usage tracking infra completing on time | Likelihood: Med | If it hits: launch slips by 1 week

==========

DESIGN

Status:
- Pricing page redesign at 60%, on track for May 2 review

Blockers:
- Waiting on final pricing copy from Marketing | Owner: [TBD] | Needed by: April 30

Asks:
- Identify pricing copy owner | Addressed to: Marketing lead | By: April 28

Risks:
- Late copy delivery forces design rework | Trigger: copy lands after April 30 | Likelihood: Med | If it hits: redesign cycle adds 3-4 days

==========

FINANCE

Status:
- Margin model for cap scenarios in progress

Blockers:
- Need historical usage data for top 20 enterprise customers | Owner: Data team | Needed by: April 29

Asks:
- Pull usage data export | Addressed to: Data team | By: April 29

Risks:
- Margin exposure if cap is hit by 20%+ of enterprise customers | Trigger: usage patterns exceed model assumptions | Likelihood: Low | If it hits: revenue impact 5-8% per affected customer

==========

VALIDATOR: 23/24 | Team Coverage 4/4 | Status Specificity 4/4 | Blocker Honesty 4/4 | Ask Specificity 4/4 | Integrity 3/4 | Risk Honesty 4/4
CONFIDENCE: High. Input was clear on team involvement, blockers, and named owners.
```

## Why this skill ships in v1

It solves the most universal PM pain: writing the same update for five different audiences. The structure (status / blockers / asks / risks per team) is the value, and it is portable across companies.
