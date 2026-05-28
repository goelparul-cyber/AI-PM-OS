# Validator: /xfn-update

> Skill Owner: Vidya
> Self-score on 6 dimensions before delivery. Each dimension 0-4. Total: 24 points.
> Below 17: revise. Below 12: do not deliver, ask for richer input.

## Dimension 1: Team Coverage (0-4)

**4**: Every team mentioned in input gets a section. No invented teams. Sections ordered by stakeholder importance.

**3**: Right teams included, but ordering is generic.

**2**: One team that should be included is missing, OR one team is included with no real signal.

**1**: Multiple teams missing, or sections padded for teams with no signal.

**0**: Update is generic prose, not organized by team.

## Dimension 2: Status Specificity (0-4)

**4**: Every Status item is concrete: a thing happened, a thing shipped, a thing is in flight at X% or week N of M. Numbers when available.

**3**: Status is mostly concrete with one or two vague items.

**2**: Status sections describe activity in general terms ("working on", "progressing").

**1**: Status reads like a meeting agenda, not a state report.

**0**: Status is a paragraph of vibes.

## Dimension 3: Blocker Honesty (0-4)

**4**: Every blocker has: what is stuck, why is stuck, named owner, needed-by date. Missing data marked `[TBD]`, not invented. Empty Blockers rows are dropped, not padded.

**3**: Blockers present and named, but one or two are missing the why or the date.

**2**: Blockers listed but vague ("waiting on Design").

**1**: Blockers softened or buried in Status.

**0**: Update claims no blockers when input clearly contains them.

## Dimension 4: Ask Specificity (0-4)

**4**: Every Ask is: a specific action, addressed to a named person or role, with a deadline. Asks are direct, not hedged.

**3**: Asks are specific and named, but one or two lack deadlines.

**2**: Asks are addressed to a team in general ("eng team please review").

**1**: Asks read as suggestions ("might be helpful if someone could").

**0**: No asks, or asks are buried in narrative.

## Dimension 5: Integrity (0-4)

**4**: No fabricated content. Every team, status, blocker, owner, and date traces to the input. Confidence note matches input quality.

**3**: Faithful to input but confidence note is generic or missing.

**2**: Minor inferences (a deadline guessed from context without flagging).

**1**: Material content added that wasn't in the input.

**0**: Invented teams, blockers, or asks.

## Dimension 6: Risk Honesty (0-4)

**4**: Every team has a Risks row. Every risk has 4 fields: risk, trigger, likelihood (Low/Med/High), if-it-hits impact. Risks trace to real signal: stakeholders.md red flags, concrete dependencies, timeline pressure, or known technical debt. "None identified this cycle" is used only after honest analysis.

**3**: Risks present for every team but one or two have a vague trigger or missing likelihood.

**2**: Risks listed but generic ("scope creep", "team capacity") without specific triggers.

**1**: Risks read as filler, copied across teams, or skip the trigger/likelihood/impact structure.

**0**: Risks row missing for one or more teams, OR all risks invented (no link to stakeholders.md or project state).

## Scoring guide

- **22-24**: Deliver with confidence
- **17-21**: Deliver, but flag weakest dimension to user
- **12-16**: Revise before delivering
- **Below 12**: Do not deliver. Ask for richer input.

## Failure modes to watch for

These patterns produce low scores even when the update "looks fine":

1. **The Padded Update**: every team has a section, but half of them are filler because the input did not actually say anything about those teams. Score Dimension 1 hard. Drop sections without signal.

2. **The Vague Status**: "Eng is making good progress on the build." Tells the reader nothing. Score Dimension 2 hard. Demand specifics.

3. **The Soft Blocker**: "Waiting on alignment with Design." Hides the real blocker. Score Dimension 3 hard. Name what is stuck and why.

4. **The Polite Ask**: "It would be great if Legal could review when they have a chance." Score Dimension 4 hard. Asks need names and deadlines.

5. **The Invented Owner**: a deadline or owner name appears that was not in the input. Score Dimension 5 hard. This is the most damaging failure because it gets forwarded as fact.

6. **The Generic Risk**: every team has a "scope creep" or "team capacity" risk with no specific trigger. Reads as filler. Score Dimension 6 hard. Risks must trace to real signal: a stakeholders.md red flag, a concrete dependency, a tight timeline, a known technical debt area. If genuinely no risk exists, "None identified this cycle" is honest; copy-pasted generics is filler.

If any of these patterns shows up, stop and rewrite the affected section before delivering.
