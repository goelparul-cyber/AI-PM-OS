# primer.md — PM OS Memory

> **Instructions:** This file gives Claude memory across sessions. Fill in Layer 1 once and keep it updated as your context evolves. Layer 2 is automatically overwritten at the end of every session by /endsession and reloaded at the start by /startsession. Do not manually edit Layer 2 — let the OS manage it.

---

## Layer 1 — Persistent Context
*Fill this in once. Update it as things change. This layer persists across all sessions.*

### Who I am
<!-- Your name, role, company, and anything else Claude should always know about you -->
[Your name, role, and company]

### My preferences
<!-- How do you like to work? Communication style, decision patterns, working style -->
[e.g. "I prefer direct feedback over diplomatic softening", "I always want tradeoffs named explicitly", "I work in 2-week sprints"]

### Active projects
<!-- One entry per active project. Update as projects change. -->
| Project | One-line description | Exec audience | Key decisions made |
|---------|---------------------|---------------|-------------------|
| [Project name] | [What it is] | [Who sees updates] | [Key decisions so far] |

### Standing decisions
<!-- Things that are always true regardless of project. Claude will apply these without being asked. -->
- [e.g. "Always use VP-level framing in exec updates"]
- [e.g. "Always pilot with one market before scaling"]
- [e.g. "Never ship without eng feasibility sign-off from [name]"]

---

## Layer 2 — Last Session
*This section is automatically overwritten by /endsession at the end of every session. Do not edit manually.*

### What we were working on
[Populated by /endsession]

### Current state
[Populated by /endsession]

### Decisions made this session
[Populated by /endsession]

### Open items
[Populated by /endsession]

### Next action
[Populated by /endsession]

---
Session closed: [Populated by /endsession]
