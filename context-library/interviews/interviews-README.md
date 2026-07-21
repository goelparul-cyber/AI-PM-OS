# interviews/

This folder is the raw material input for the `/interview-synth` skill.

---

## What goes here

Drop raw customer interview transcripts into this folder before running `/interview-synth`. Transcripts can be:

- Copied directly from a recording tool (Otter.ai, Grain, Dovetail, etc.)
- Pasted from a Google Doc
- Typed notes from an in-person session

Format doesn't need to be perfect — the skill is designed to handle messy, unstructured input.

---

## How /interview-synth uses this folder

When you run `/interview-synth`, Claude:

1. Reads the transcript(s) you specify
2. Extracts key themes, pain points, and behavioral patterns
3. Surfaces verbatim quotes verified against the original transcript
4. Produces a structured synthesis (1–2 pages) ready to paste into a PRD or share with stakeholders

**Important:** Every quote in the synthesis is verified word-for-word against the source transcript. Claude will never paraphrase and present it as a quote.

---

## Connection to PRDs

The /interview-synth output is designed to feed directly into your PRD's problem statement section. A typical workflow:

1. Run 5–8 customer interviews
2. Drop transcripts into this folder
3. Run `/interview-synth` across all transcripts
4. Use the synthesis as the evidence layer in your PRD problem statement
5. Cite specific quotes inline using the format: `[Quote — Participant name/label, date]`

---

## What NOT to store here

- Transcripts containing PII (full names, contact details, company names) unless your org has approved storage
- Recordings or audio files — text only
- Processed or edited transcripts — keep them raw so the validator can verify quotes accurately

---

## File naming convention

Use this format for consistency:

```
YYYY-MM-DD_participant-label_topic.md
```

Example: `2025-03-14_maya-s_coupon-discovery.md`

---

## Privacy note

Customer interviews are sensitive. Do not commit real transcripts to a public GitHub repo. This folder is for local use only. The `.gitignore` excludes all `.md` files in this folder except this README and `.example.md` files.
