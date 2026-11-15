# Prompt template — contribution typing + sub-categories

Two classification layers, both run as blind agent batches over
title+abstract (3 parallel batches of ~30 worked well). The agent returns
*guesses*; a human confirms via the stage-8 review UIs.

## Layer 1 — contribution type (paper's role in the review)

Decide what the paper CONTRIBUTES to a review of syllabus topics / ILOs /
activities — one of:

- **C1 motivation** — evidence or argument for WHY genAI literacy is needed
  (gap studies, workforce analyses, vision/position papers)
- **C2 framework** — defines WHAT genAI literacy is (competencies,
  frameworks, curricula, teaching guidelines)
- **C5 assessment** — HOW genAI literacy is measured (instruments, scales,
  tests, assessment frameworks)
- **C4 activity** — a discipline-specific course activity using genAI
  (course-embedded interventions; in our run these became a frozen
  sub-result rather than corpus members)

Judgement rule that resolves most boundary cases: *if a paper applies an
existing instrument to make a needs argument, the contribution is the
evidence (C1), not the instrument (C5)* — that ruling retyped our last C6
paper. Residual types are allowed but expect them to collapse: our C3
(retyped/excluded at review) and C6 (one excluded, one retyped C1) both
dissolved at full text.

## Layer 2 — sub-category (within each type)

Per-type menus (from our run; extend as your corpus demands):

- C1: vision-position · needs-evidence
- C2: competency-framework · course-design · curriculum-integration ·
  pedagogical-guidelines
- C5: scale-development · scale-validation · assessment-framework ·
  knowledge-test
- C4 (two facets): **subject** (Intro-Programming, Software-Engineering,
  General-CS, DSA, Databases, Web-Dev, AI-ML, Cybersecurity,
  Systems-Networks, HCI, Game-Dev, Capstone, Non-CS, Other:<label>) and
  **activity type** (the codebook B-codes: verify, prompt, reflect, pair,
  project, comprehend, decompose, demo, build, assessg — multi-label)

## Batch prompt skeleton

---
Read [batch-N.json] (record_id, [category,] title, year, abstract) — papers
from a systematic review on [topic]. For EACH record assign
[a contribution type / a sub-category within its category / a subject and
activity codes], using exactly the labels defined above. Prefer the most
specific applicable label; use the residual label only when nothing
specific fits; "Other: <short-label>" if none fits. Judge from
title+abstract only. Confidence: high/medium/low. Rationale: <=12 words
citing the deciding cue.

Final message: ONLY the data, one line per record, semicolon-delimited,
no header, no commentary:
record_id;label;confidence;rationale
All records must appear exactly once.
---

## Notes for the operator

- Keep batches blind to prior tags — re-classification agreement against an
  earlier pass is then a real check (ours agreed 77/84 on C4 subjects; the
  7 diffs were all worth a look and 4 exposed scope problems).
- Low/medium confidence guesses go into the sheet's Comments so the human
  pass can prioritise them.
- Validate returned labels against the menu (an off-menu label is a signal,
  not garbage — it usually means the menu is missing a real category).
