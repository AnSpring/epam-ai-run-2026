# Maturity Gap Analysis

**Date:** 2026-06-08  
**Author:** Anastazja Bobrowa - Data Quality Engineer  
**Project:** Personal learning project — EPAM AI Run Mission 2026 / Bootcamp 4.0  
**Committed location:** https://github.com/AnSpring/epam-ai-run-2026/blob/main/katas/kata3-maturity-gap-analysis/maturity-gap-analysis.md

---

## Scorecard

| Dimension            | Level (L1 / L2 / L3) | Score (1.0 / 2.0 / 3.0) | Evidence (2–3 sentences)                                                                                                                                                                                                                                                                                                       |
| -------------------- | -------------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| AI Capabilities      | L1                   | 1.0                     | AI is used individually and without a consistent process — there is no coverage threshold met across deliverables. Course artifacts (guides, glossary, kata outputs) are produced with AI assistance, but usage is ad hoc and not systematically applied to every deliverable. No agentic workflows exist.                     |
| Reusability          | L1                   | 1.0                     | All prompts exist locally or in personal notes and have not been committed to a shared repository. The prompt template from Kata 2 was created but not yet committed to a team-accessible location. There is no shared prompt library, no reuse norm, and no colleague who can access these prompts without asking the author. |
| AI Champions         | L1                   | 1.0                     | On the real project, AI enthusiasts exist but have no mandate, no designated role, and no responsibility for team AI adoption. On the personal learning project, there is no team — the author is the sole user. No Champion with an official role exists in either context.                                                   |
| Performance Tracking | L1                   | 1.0                     | No productivity metrics are defined or measured on either the real project or the personal learning project. AI usage is perceived as helpful but no before/after data exists. There is no logging process, no defined KPIs, and no review cadence.                                                                            |
| DAU                  | L1                   | 1.0                     | The author uses AI tools daily, which represents 100% personal DAU. However, on the real project the team does not use AI tools daily at >70% — usage is occasional and individual. Assessed at team level per the matrix definition.                                                                                          |
| **Average**          |                      | **1.0**                 |                                                                                                                                                                                                                                                                                                                                |
| **Overall Level**    |                      |                         | **L1** (1.0–1.9)                                                                                                                                                                                                                                                                                                               |

---

## Gap Analysis

### Gap 1

**Dimension:** Reusability  
**Current level:** L1  
**Why this gap is most damaging:** Every task starts from zero — when the author is unavailable or the project ends, all AI-assisted workflows and prompt knowledge disappear with them, leaving no reusable team asset.  
**Root cause:** There is no designated shared location for prompt templates and no norm requiring a prompt to be committed before it is used a second time — so reuse never happens by default.

---

### Gap 2

**Dimension:** Performance Tracking  
**Current level:** L1  
**Why this gap is most damaging:** Without measurable data it is impossible to justify AI investment, identify which task types benefit most from AI, or demonstrate progress toward L2 maturity to stakeholders or course facilitators.  
**Root cause:** There is no defined moment in the workflow where time or quality is recorded — AI is used opportunistically with no before/after measurement, making all perceived gains anecdotal and unverifiable.

---

## 30-Day Improvement Plan

### Step 1 — addresses Gap 1 (Reusability)

| Field              | Value                                                                                                                                                                                                                                                        |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Action**         | Create a `/prompts` folder in the `epam-ai-run-2026` GitHub repository and commit at least 2 prompt templates there — including the PySpark function generator from Kata 2 — so any teammate can find and run them via direct link without asking the author |
| **Owner**          | Anastazja Bobrowa                                                                                                                                                                                                                                            |
| **Timeline**       | 2026-07-08                                                                                                                                                                                                                                                   |
| **Success metric** | ≥2 prompt templates committed to `/prompts` folder and accessible via direct GitHub URL without login                                                                                                                                                        |

---

### Step 2 — addresses Gap 2 (Performance Tracking)

| Field | Value |
|---|---|
| **Action** | Before each course assignment, write one row in `time-tracking.md`: task name + estimated time without AI (via Google + manual writing) + actual time with AI. Start from the next assignment after this commit. |
| **Owner** | Anastazja |
| **Timeline** | 2026-07-08 |
| **Success metric** | ≥3 assignments logged in `time-tracking.md` with three numeric columns: estimated minutes without AI / actual minutes with AI / delta |

---

## Peer Review

**Reviewer:** [Name — Role]  
**Date reviewed:** YYYY-MM-DD

| Review question | Reviewer answer |
|---|---|
| Is the evidence for each dimension specific and observable — not aspirational? | [One sentence] |
| Which score do you challenge, and why? | [At least one — dimension, proposed alternative score, reason] |
| Is each root cause a structural/behavioural cause — not a symptom? | Yes / No — [one sentence] |
| Are the success metrics measurable without asking the author? | Yes / No — [one sentence] |
| Would you sign off on this plan as a teammate? | Yes / No — [one sentence] |

---

## Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | 2026-06-08 | Initial commit | Anastazja |
| 1.1 | YYYY-MM-DD | Post-review update | [Name] |
