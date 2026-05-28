# primer.md — Example (Fictional Company: NestWise, a home services marketplace)

> **This is an example file.** It shows what a populated primer.md looks like after several sessions of use. Use it as a reference for how to fill in your own primer.md.

---

## Layer 1 — Persistent Context
*Fill this in once. Update it as things change. This layer persists across all sessions.*

### Who I am
Jordan Lee, Senior PM at NestWise. Leading the booking experience squad. Reporting to Sandra Lee (CEO). Working closely with Chris Wong (Lead Eng) and Aiko Tanaka (Design).

### My preferences
- Direct feedback over diplomatic softening — if something is wrong, say so
- Always name the tradeoff — I don't trust recommendations that don't acknowledge what we're giving up
- I work in 2-week sprints; always frame next actions within the current sprint window
- Exec updates go to Sandra — she reads in 90 seconds, metrics first
- I prefer tables over bullets for status; prose for problem statements

### Active projects
| Project | One-line description | Exec audience | Key decisions made |
|---------|---------------------|---------------|-------------------|
| Booking Completion v2 | Reduce drop-off in booking flow by surfacing pro availability in real time | Sandra (CEO), Kevin (CTO) | Mobile-first; web in v2; no upfront price guarantees in v1 |
| Pro Response Time | Surface pro response rate prominently on profile to build trust | Sandra (CEO) | Show median response time, not average — less skewed by outliers |

### Standing decisions
- Always use VP-level framing in exec updates — Sandra reads these, not ICs
- Always pilot in 2 metro areas before national rollout
- Never ship a feature touching payments without Beth Morin (Legal) sign-off
- Loop Omar (BD) in at kickoff, not just at launch — he feels like an afterthought otherwise

---

## Layer 2 — Last Session
*This section is automatically overwritten by /endsession at the end of every session.*

### What we were working on
Drafted PRD for Booking Completion v2. Ran /review-panel on the problem statement section. Incorporated feedback from eng-reviewer and exec-reviewer sub-agents.

### Current state
PRD draft is at v0.3. Problem statement approved. Success metrics section needs work — current metrics are output-focused, not outcome-focused. Design hasn't seen it yet.

### Decisions made this session
- Removed "same-day booking guarantee" from v1 scope — legal risk too high per Beth's feedback
- Agreed to use median response time (not average) on pro profiles

### Open items
- Success metrics section needs to be rewritten — swap output metrics for outcome metrics
- Schedule design review with Aiko before end of sprint
- Follow up with Omar on partner impact of real-time availability feature

### Next action
Rewrite success metrics section using /exec-update to pressure-test outcome framing. Then share with Aiko for design review.

---
Session closed: 2025-04-08
