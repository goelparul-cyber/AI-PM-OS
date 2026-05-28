# AI PM OS
### A Claude-powered operating system for product managers

AI PM OS turns five recurring PM jobs into 10-minute jobs. It works by loading your company context — your users, stakeholders, voice, and decisions — into Claude once, then routing every request to a skill designed specifically for that job.

The result: outputs that sound like they came from your team, not a generic AI.

---

## What it does

| Skill | Input | Output |
|-------|-------|--------|
| `/prd-draft` | One-line idea | Full PRD with diagrams, user stories, metrics, and a working prototype — plus a 7-perspective review panel |
| `/interview-synth` | Raw transcript | Structured synthesis with verified verbatim quotes |
| `/xfn-update` | Messy project notes | Status update organized by cross-functional team |
| `/exec-update` | Project state | 1-pager a Sr Director reads in under 2 minutes |

Each skill reads your context library before generating output. Every output includes a confidence score and a validator report.

> **About the review panel:** `/prd-draft` includes a built-in review panel that critiques your PRD from 7 lenses — Engineering, Design, Executive, Legal, Data, GTM, and Customer. Each reviewer runs in parallel and flags Critical, Important, and Consider issues. The reviewers live in `skills/prd-draft/sub-agents/`.

---

## Why we built this

The PM drill: paste context into Claude, explain your PRD structure, get something halfway there. Now repeat that across 5 projects, 12 features, and a framework nobody remembers to follow.

What if the context, the structure, and the quality bar were baked in — and stayed current automatically?

The real unlock isn't any single skill. It's the context library and automated pipelines. When AI knows your company's systems, your stakeholder approval chains, and your writing style, output quality improves dramatically.

We stress-tested it on a PRD for a complex multi-system feature — the kind where one change touches 8 systems and 7 teams, and the PM building it doesn't know half the dependencies. The review panel caught a dependency contradiction in the doc, questioned the rollout strategy, and flagged a compliance risk nobody had raised. From prompts we wrote in a day.

This is what "AI-native PM" actually means: using AI as a system, where context stays current, skills check their own work, and reviewers catch what you miss.

We built this over a weekend to solve our own problems. It's not a product. It's a system we use ourselves, and we're sharing it so other PMs can adapt it for their context.

---

## How it works

The OS has four layers:

```
PERCEPTION       EXECUTION         CRITIQUE         CONTINUITY
context-library/ skills/           sub-agents/      primer.md
what we know     what we do        what we check    what we remember
```

**Context library** — five files you fill in once: your company, users, stakeholders, voice, and active decisions. Every skill reads these before generating output. This is what makes outputs feel company-specific rather than generic.

**Skills** — each skill has three files: `SKILL.md` (the process), `checklist.md` (execution guide), and `validator.md` (quality gate). The skill runs the checklist during execution and the validator before delivery.

**Sub-agents** — seven reviewer personas (Engineering, Design, Executive, Legal, Data, GTM, Customer) that critique any document from their specific lens. Used by `/review-panel` and `/prd-draft`.

**Primer** — a session memory file (`primer.md`) that lets Claude pick up where you left off. `/endsession` writes a handoff summary. `/startsession` loads it and surfaces open threads.

---

## Getting started

### Option 1 — Claude Projects (recommended, no code required)
1. Create a new Project in Claude.ai
2. Upload all files to Project content
3. Start a new conversation and type `/startsession`
4. Fill in your context library files and re-upload them

### Option 2 — Claude Code (most seamless)
1. Clone this repo
2. `cd` into the folder
3. Run `claude` to start Claude Code
4. Claude Code automatically reads `CLAUDE.md` and loads the full OS
5. Type `/startsession` to begin

---

## Setting up your context library

The context library is what makes this yours. Before running any skill, fill in these five files:

| File | What to add |
|------|-------------|
| `context-library/company.md` | Company overview, product, business model, current OKRs, constraints |
| `context-library/users.md` | Primary and secondary personas, pain points, key research insights |
| `context-library/stakeholders.md` | Team leads, what they care about, decision-making structure, dynamics |
| `context-library/voice.md` | Writing principles, tone by doc type, vocabulary rules, format defaults |
| `context-library/decisions.md` | Key decisions made, alternatives considered, open questions |

Each file has a blank template and a filled-in example (`.example.md`) to show you what good looks like. Fill in the templates and leave the examples for reference.

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
/review-panel [paste any document]
```

If input is missing key details, the skill asks one consolidated question before drafting. It never invents information — missing data is marked `[TBD]`.

---

## Session memory

Start every session:
```
/startsession
```
Claude loads your last session state and surfaces open threads.

End every session:
```
/endsession
```
Claude writes a handoff summary to `primer.md` — what you worked on, decisions made, open items, next action.

**If using Claude Code:** `primer.md` is updated automatically.
**If using Claude.ai:** Copy the output into your `primer.md` file manually.

> Layer 1 of `primer.md` (persistent context about you and your preferences) is manually maintained in v1. Automatic cross-session learning is planned for v2.

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
│   └── decisions.md + decisions.example.md
├── skills/
│   ├── startsession/                  — SKILL.md, checklist.md, validator.md
│   ├── endsession/                    — SKILL.md, checklist.md, validator.md
│   ├── exec-update/                   — SKILL.md, checklist.md, validator.md + reviewers
│   ├── xfn-update/                    — SKILL.md, checklist.md, validator.md, WORKFLOW.md
│   ├── interview-synth/               — SKILL.md, checklist.md, validator.md
│   └── prd-draft/                     — SKILL.md, checklist.md, validator.md
│       └── sub-agents/                — 7 reviewer personas + REVIEW-PANEL.md
├── interviews/                        — drop raw transcripts here for /interview-synth
│   ├── README.md
│   └── sample-interview.example.md
└── .gitignore
```

---

## What's next (v2)

- Automatic Layer 1 updates — Claude detects patterns across sessions and suggests updates to your persistent context
- `/meeting-cleanup` — turns raw meeting notes into decisions, actions, and follow-ups
- `/competitive-teardown` — structured competitive analysis from a URL or description
- `/launch-checklist` — pre-launch readiness check across all XFN teams
- Web UI — a browser-based interface with all skills, review panel, and session memory (prototype included as `pm-os-copilot.jsx`)

---

## Built by

This OS was built collaboratively over a weekend by four senior product leaders:

- [Parul Goel](https://www.linkedin.com/in/pg2121/)
- [Priyanka Chaturvedi](https://www.linkedin.com/in/priyankachaturvedimit/)
- [Vidya Sarangapany](https://www.linkedin.com/in/vsara/)
- [Bhagyashree Prabhakar](https://www.linkedin.com/in/bhagya-prabhakar/)

---

## License

MIT. Fork it, adapt it, make it yours. If you build something interesting on top of it, we'd love to hear about it.
