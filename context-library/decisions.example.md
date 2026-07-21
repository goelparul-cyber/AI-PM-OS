# decisions.md — Example (Fictional Company: NestWise, a home services marketplace)

> **This is an example file.** It shows what a completed decisions.md looks like for a fictional company called NestWise. Use it as a reference, then log your own team's decisions in decisions.md.

---

## Decision log

---

### No upfront pricing guarantees in v1
**Date:** March 14, 2025
**Decision:** NestWise will show price ranges, not fixed quotes, in the booking flow for v1.
**Why:** Fixed quotes require deep integration with pro pricing APIs we don't have yet. Price ranges set honest expectations without creating legal exposure. Beth (Legal) flagged that guarantee language requires additional compliance review we can't complete before launch.
**Alternatives considered:**
- Fixed upfront quotes — rejected because: requires pro API integration (6+ week build) and creates liability if quotes are inaccurate
- No pricing shown until after booking — rejected because: user research showed this was the #1 abandonment trigger
**Who decided:** Sandra Lee (CEO) with input from Beth Morin (Legal) and Chris Wong (CTO)
**Still stands?** Yes — revisit in Q3 2025 when pro API integration is scoped

---

### Pro vetting is manual for v1
**Date:** February 28, 2025
**Decision:** All new pros are manually reviewed by the NestWise ops team before going live on the platform.
**Why:** Automated vetting has too many false positives at our current data volume. Trust is our core differentiator — one bad pro experience early damages the brand more than slow supply growth. Manual review gives us quality signal we can use to train an automated system later.
**Alternatives considered:**
- Fully automated vetting — rejected because: insufficient data to train a reliable model; too much trust risk at this stage
- Self-certification by pros — rejected because: no accountability mechanism; legal exposure if a self-certified pro causes harm
**Who decided:** Sandra Lee (CEO)
**Still stands?** Yes — revisit when pro applications exceed 200/month (currently at 60/month)

---

### Mobile-first, web is secondary
**Date:** January 15, 2025
**Decision:** All new features ship on iOS and Android first. Web is secondary and may lag by 1–2 sprints.
**Why:** 84% of our bookings happen on mobile. Web users skew toward property managers (a secondary persona). Maintaining full parity slows mobile velocity without meaningful impact on core metrics.
**Alternatives considered:**
- Full parity across web and mobile — rejected because: doubles eng effort; web represents 16% of bookings
- Web-only for v1 — rejected because: our primary persona (Jordan) is mobile-native
**Who decided:** Kevin Park (CTO) + PM lead
**Still stands?** Yes

---

## Deferred / open questions
| Question | Why deferred | Revisit trigger |
|----------|-------------|-----------------|
| Should NestWise offer a subscription tier for frequent bookers? | Insufficient data on booking frequency to model LTV accurately | When 90-day repeat booking rate exceeds 30% |
| Should pros be able to set their own availability in real time? | Requires a pro-side app we haven't scoped | When pro supply becomes a bottleneck (currently demand-constrained) |
| International expansion — Canada first? | Too early; domestic growth is the priority | When MAH exceeds 500K |
