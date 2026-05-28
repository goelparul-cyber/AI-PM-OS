# /prd-draft Quality Bar

Every item must pass before the PRD is presented.

## Language & clarity
- [ ] A new hire could understand the problem statement after reading it once
- [ ] No jargon used without a definition
- [ ] Every paragraph is under 4 sentences
- [ ] Active voice throughout — no "will be built," "is expected to"
- [ ] Feature type is classified at the top (new feature / new product / system change / ML-AI / internal)

## Problem statement
- [ ] Names specific roles or segments who feel the pain — not generic "users" or "customers"
- [ ] States how painful it is with at least one concrete signal (frequency, ticket volume, time wasted, revenue lost)
- [ ] Explains "why now" — what changed that makes this worth building today

## Impact & stakeholders
- [ ] Every affected team is named
- [ ] Estimated reach is stated (even if rough: "~50K daily transactions" or "all 200 internal analysts")

## Solution overview
- [ ] One-paragraph plain-language description exists before any diagram
- [ ] At least one Mermaid process flow diagram showing the happy path
- [ ] At least one Mermaid system diagram showing which systems are involved
- [ ] For complex system changes: both current-state and proposed-state diagrams exist

## User stories
- [ ] 4-6 stories, each referencing a specific role (not "user")
- [ ] At least one edge case story (what happens when things go wrong)
- [ ] At least one internal-user story if the feature touches internal systems
- [ ] Stories are concrete enough to estimate (not vague wishes)

## Dependency matrix
- [ ] Table format with columns: system/team, what they own, what changes, dependency type, risk level
- [ ] Every dependency classified as Blocking / Enhancing / Informational
- [ ] Uncertain dependencies explicitly flagged — not silently omitted
- [ ] For complex system changes: at least 5 systems evaluated

## Metrics
- [ ] 2-4 success metrics, each with: measurement, baseline, target, timeframe
- [ ] At least one leading indicator measurable within the first week
- [ ] At least one guardrail metric (something that must NOT get worse)
- [ ] For ML/AI features: model performance metrics included

## Ramp-up plan
- [ ] Pilot phase defined: who, scope, duration, learning goals, kill criteria
- [ ] Kill criteria are specific and measurable — not "if it doesn't work"
- [ ] Full rollout criteria stated

## Prototype
- [ ] A React component is generated — no exceptions, even for backend changes
- [ ] The prototype is functional enough to demo, not just a wireframe
- [ ] For backend features: the prototype visualizes data flow, system states, or monitoring

## Open questions
- [ ] Every question has a proposed owner
- [ ] Top 3 risks listed with mitigation ideas
- [ ] Uncertain dependencies from section 5 reappear here with investigation owners
