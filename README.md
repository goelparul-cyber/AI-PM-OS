# AI PM OS
### A Claude-powered operating system for product managers

AI PM OS turns four recurring PM jobs into 10-minute jobs. It works by loading your company context — your users, stakeholders, voice, and decisions — into Claude once, then routing every request to a skill designed specifically for that job.

The result: outputs that sound like they came from your team, not a generic AI.

---

## What it does

| Skill | Input | Output |
|-------|-------|--------|
| `/prd-draft` | One-line idea | Full PRD with diagrams, user stories, metrics, and a working prototype |
| `/interview-synth` | Raw transcript | Structured synthesis with verified verbatim quotes |
| `/xfn-update` | Messy project notes | Status update organized by cross-functional team |
| `/exec-update` | Project state | 1-pager a Sr Director/VP reads in under 2 minutes |

Each skill reads your context that lives in the context library before generating output. Every output includes a validator report, and most skills also end with a confidence score.

---

## Why we built this

The PM drill: paste context into Claude, explain your PRD structure, get something halfway there. Now repeat that across 5 projects, 12 features, and a framework nobody remembers to follow.

What if the context, the structure, and the quality bar were baked in — and stayed current automatically?

The real unlock isn't any single skill. It's the context library and automated pipelines. When AI knows your company's systems, your stakeholder approval chains, and your writing style, output quality improves dramatically.

This is what "AI-native PM" actually means: using AI as a system, where context stays current, skills check their own work, and reviewers catch what you miss.

We built this over a weekend to solve our own problems. It's not a product. It's a system we use ourselves, and we're sharing it so other PMs can adapt it for their context.

---

## Why this is more than a prompt

This isn't a clever prompt you paste into ChatGPT or Claude.ai. It's a four-layer
architecture, and that's what makes it something you can trust to work
consistently, not just something that looks impressive once.

```
PERCEPTION       EXECUTION         CRITIQUE         CONTINUITY
what it knows    what it does      what it checks   what it remembers
```

**Perception, what it knows.** Before generating anything, skills read the
context library: your company, your users, your stakeholders, your voice.
This is what makes output sound like your team, not a generic AI.

**Execution, what it does.** These are the skills, the actual PM jobs:
drafting a PRD, an exec update, a status update, a research synthesis.

**Critique, what it checks.** Before output reaches you, every skill runs a
validator, a quality gate that scores the draft before delivery. `/exec-update`
goes further: three reviewer personas, engineering, design, and exec, flag
concerns before you send.

**Continuity, what it remembers.** Session memory (`primer.md`) means you're
not re-explaining your context every time you come back.

Skip any one of these layers and you get something that looks impressive but
you can't actually rely on.

---

## Prerequisites

**For Option 1 (Claude Projects)**
- A Claude.ai account with access to Projects (available on paid plans)

**For Option 2 (Claude Code)**
- [Claude Code](https://claude.com/claude-code) installed
- An Anthropic account with Claude Code access
- Git, to clone this repo

---

## Getting started

### Option 1 — Claude Projects
1. Create a new Project in Claude.ai
2. Download this repo to your computer (Code → Download ZIP on GitHub)
3. Fill in your `context-library/*.md` files and `primer.md` Layer 1 locally (see "Setting up your context" below)
4. Upload all files to Project content
5. Start a new conversation and type `/startsession`

### Option 2 — Claude Code (most seamless)
1. Clone this repo
2. `cd` into the folder
3. Fill in your `context-library/*.md` files and `primer.md` Layer 1 (see "Setting up your context" below)
4. Run `claude` to start Claude Code
5. Claude Code automatically reads `CLAUDE.md` and loads the full OS
6. Type `/startsession` to begin

---

## Setting up your context

This is what makes the OS yours. Before running any skill, fill in six files.

### Context library (five files)

| File | What to add |
|------|-------------|
| `context-library/company.md` | Company overview, product, business model, current OKRs, constraints |
| `context-library/users.md` | Primary and secondary personas, pain points, key research insights |
| `context-library/stakeholders.md` | Team leads, what they care about, decision-making structure, dynamics |
| `context-library/voice.md` | Writing principles, tone by doc type, vocabulary rules, format defaults |
| `context-library/decisions.md` | Key decisions made, alternatives considered, open questions |

Each file has a blank template and a filled-in example (`.example.md`) to show you what good looks like. Fill in the templates and leave the examples for reference.

### primer.md Layer 1

`primer.md` has two layers. Layer 1 is persistent context about you: your name,
role, company, and how you like to work. Fill it in once to start;
`/endsession` also auto-appends it whenever you make an explicit preference
statement during a session (e.g. "I always...", "from now on..."). Layer 2 is
session memory, automatically written by `/endsession` and read by
`/startsession`, don't edit it by hand.

---

## Running a skill

Once your context library is set up, skills are simple to invoke:

```
/exec-update Here's what happened this week: shipped the pro response time feature, 
bookings up 8% WoW, Sandra wants an update, main blocker is Android is 2 weeks 
behind iOS...
```

```
/xfn-update [paste your project notes, Jira tickets, Slack threads]
```

```
/prd-draft Add real-time pro availability to the booking flow
```

```
/interview-synth [paste or attach raw customer interview transcript]
```

It never invents information — missing data is marked `[TBD]`.

---

## Session memory

Start every session:
```
/startsession
```
Claude loads your last session state and surfaces open threads. On your first
ever run, there's no session to load yet, Claude will instead check that
`primer.md` Layer 1 and your context library are filled in, and ask you to do
that first if they aren't.

End every session:
```
/endsession
```
Claude writes a handoff summary to `primer.md` — what you worked on, current state, decisions made, open items, next action.

**If using Claude Code:** `primer.md` is updated automatically.
**If using Claude.ai:** Copy the output into your `primer.md` file manually.

> `/endsession` automatically appends Layer 1 with any explicit preference statements you made during the session (e.g. "I always...", "from now on..."). Detecting patterns across past sessions to suggest updates is planned for v2.

---

## Repo structure

```
AI-PM-OS/
├── CLAUDE.md                          — the brain, routes all commands
├── primer.md                          — session memory (fill in once, updated each session)
├── primer.example.md                  — example of a populated primer
├── context-library/
│   ├── company.md + company.example.md
│   ├── users.md + users.example.md
│   ├── stakeholders.md + stakeholders.example.md
│   ├── voice.md + voice.example.md
│   ├── decisions.md + decisions.example.md
│   └── interviews/                    — drop raw transcripts here for /interview-synth
│       ├── interviews-README.md
│       └── sample-interview.example.md
├── skills/
│   ├── startsession/                  — SKILL.md, checklist.md, validator.md
│   ├── endsession/                    — SKILL.md, checklist.md, validator.md
│   ├── exec-update/                   — SKILL.md, checklist.md, validator.md + reviewers
│   ├── xfn-update/                    — SKILL.md, checklist.md, validator.md, WORKFLOW.md
│   ├── interview-synth/               — SKILL.md, checklist.md, validator.md
│   └── prd-draft/                     — SKILL.md, checklist.md, validator.md
│       └── sub-agents/                — 7 reviewer personas + REVIEW-PANEL.md
└── .gitignore
```

---

## What's next (v2)

- Automatic Layer 1 updates — Claude detects patterns across sessions and suggests updates to your persistent context
- `/meeting-cleanup` — turns raw meeting notes into decisions, actions, and follow-ups
- `/competitive-teardown` — structured competitive analysis from a URL or description
- `/launch-checklist` — pre-launch readiness check across all XFN teams
- Web UI — a browser-based interface with all skills and session memory

---

## Built by

This OS was built collaboratively over a weekend by four senior product leaders:

- [Priyanka Chaturvedi](https://www.linkedin.com/in/priyankachaturvedimit/)
- [Vidya Sarangapany](https://www.linkedin.com/in/vsara/)
- [Bhagyashree Prabhakar](https://www.linkedin.com/in/bhagya-prabhakar/)
- [Parul Goel](https://www.linkedin.com/in/pg2121/)

---

## License

MIT. Fork it, adapt it, make it yours. If you build something interesting on top of it, we'd love to hear about it.

Run into issues? Open a GitHub Issue on this repo.
