# Checklist: /xfn-update

> Skill Owner: Vidya
> Run BEFORE delivery. If any item fails, fix or flag.

## Input completeness

- [ ] I read the full input (notes, tickets, slack, calendar) before drafting
- [ ] I checked context-library/stakeholders.md for team list and tone
- [ ] I identified which teams have actual signal in the input
- [ ] I noted what changed this week vs last week
- [ ] I extracted explicit blockers with reasons
- [ ] I extracted explicit asks with named recipients

## Structure

- [ ] Context section is 2-3 sentences, names the project, captures the delta
- [ ] Every team section has Status (or is dropped entirely)
- [ ] Every blocker has: blocker, reason, owner, needed-by date (or `[TBD]`)
- [ ] Every ask has: action, addressed to, deadline (or `[TBD]`)
- [ ] **Every team has a Risks row** (required, even if "None identified this cycle")
- [ ] **Every risk has 4 fields**: risk, trigger, likelihood (Low/Med/High), if-it-hits impact
- [ ] Teams with no signal are NOT included
- [ ] Sections are ordered by stakeholder importance per stakeholders.md
- [ ] Section order within each team: Status, Blockers, Asks, Risks
- [ ] Empty Status / Blockers / Asks rows are dropped (no "None this week" filler)
- [ ] Inferred dates are marked `[derived]` inline, with source noted

## Integrity

- [ ] I did NOT invent teams that were not in the input
- [ ] I did NOT invent blockers, owners, or deadlines
- [ ] I did NOT invent risks with generic triggers (no "scope creep" without specifics)
- [ ] I did NOT soften or omit difficult asks
- [ ] I did NOT pad empty Status/Blockers/Asks sections with filler
- [ ] I did NOT bury inferred dates only in the confidence note
- [ ] If "None identified this cycle" is used for Risks, it reflects honest analysis (not skipped work)
- [ ] If the input had conflicting info, I flagged the conflict (did not pick one)

## Voice and format

- [ ] Zero em dashes anywhere in the output
- [ ] Pipes used for tabular rows (Blocker | Owner | Needed by)
- [ ] Colons used for label/value pairs (Status:, Owner:)
- [ ] No corporate hedging language
- [ ] Active voice, named subjects
- [ ] Each team section scannable in 5 seconds on mobile
- [ ] Short sentences

## Confidence note

- [ ] **Visible validator score line** included as second-to-last line: `VALIDATOR: [N]/24 | [breakdown across 6 dimensions]`
- [ ] One-line confidence statement at the end
- [ ] Confidence level matches input quality
- [ ] If confidence is Medium or Low, the reason names what was thin
- [ ] If any dimension scored 2 or below, a `DOUBLE-CHECK:` line names what to verify

## Final gate

If 3+ items in "Structure" or any item in "Integrity" fails: do NOT deliver. Fix the update or ask for richer input.
