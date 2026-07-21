# stakeholders.md — Example (Fictional Company: NestWise, a home services marketplace)

> **This is an example file.** It shows what a completed stakeholders.md looks like for a fictional company called NestWise. Use it as a reference, then fill in your own stakeholders.md with your actual team.

---

## Stakeholder map

| Name | Role | Influence area | What they care most about | Known concerns / red flags |
|------|------|----------------|--------------------------|---------------------------|
| Sandra Lee | CEO & Co-founder | Vision, fundraising, final call on strategy | MAH growth, NPS, Series B narrative | Will push back hard on anything that slows MAH growth or muddies the brand story |
| Kevin Park | CTO & Co-founder | Eng capacity, architecture decisions | Technical debt reduction, platform stability | Very protective of eng bandwidth; skeptical of features that touch the payments system |
| Diana Cruz | VP Marketing / Growth | Acquisition, lifecycle, partnerships | CAC, activation rate, email/push engagement | Wants product hooks for growth loops; frustrated when PM ships without a comms plan |
| Omar Shaikh | Head of Partnerships (BD) | Pro supply quality, deal reliability | Partner NPS, number of exclusive pros | Concerned product team undervalues pro relationship complexity |
| Nina Patel | Head of Customer Success | Retention, support ticket volume | CSAT, churn rate, scheduling-related ticket reduction | Wants PM to read CS tickets before writing specs |
| Chris Wong | Lead Engineer | Eng execution, scoping, technical feasibility | Accurate scoping, no surprise scope creep | Does not like specs that ship without eng review; allergic to "just a small change" |
| Beth Morin | Legal Counsel (part-time) | Compliance, pricing feature review | Risk exposure, pricing guarantee language | Slow to respond; loop her in at least 1 week before launch for pricing features |

---

## Decision-making structure
**Who has final call on shipping?** Sandra (CEO) for anything strategic; PM lead for day-to-day feature decisions
**Who must approve before eng starts?** Chris (eng feasibility sign-off) + PM lead
**Who can kill a project late-stage?** Sandra or Kevin if it creates platform risk; Beth if it creates legal exposure

---

## XFN leads (for /xfn-update)
| Team | Lead | Preferred update format |
|------|------|------------------------|
| Engineering | Chris Wong | Bullet list: what's done, what's blocked, what's needed from eng |
| Design | Interim: senior designer Aiko Tanaka | Annotated Figma link + 3-bullet summary |
| Data / Analytics | Priya Mehta | Metrics table: current vs. target, trend, confidence level |
| Legal / Compliance | Beth Morin | Risk flag + specific ask; keep it under 5 sentences |
| GTM / Marketing | Diana Cruz | Feature benefit in one sentence + proposed launch timing |
| Customer Success | Nina Patel | User-facing change summary + predicted CS ticket impact |
| Partnerships (BD) | Omar Shaikh | Pro-facing impact + any action required from BD |

---

## Notes on stakeholder dynamics
- Kevin and Diana have an ongoing tension: Kevin pushes to slow down and reduce debt, Diana wants to ship fast to hit MAH. PM often has to broker.
- Omar feels like an afterthought in planning — proactively looping him in early builds significant goodwill.
- Nina is your most useful ally for validating problem statements — she has deep qualitative signal from CS tickets.
- Beth has a 1-week minimum lead time for anything touching pricing or guarantees — never surprise her before launch.
