# Inclusion / Exclusion Criteria — v0.3.1 (refactor, abstract-calibrated)

*v0.3.1, 2026-06-30 — **FROZEN** for the clean run (Ric, 2026-06-30). This is the operative criteria
set; changes after this point require a version bump and re-freeze. Abstract-stage calibration (25 abstracts, Ric + agent,
`Screening/calibration-v0.3.md`) lifted blind agreement to binary κ 0.44 / 3-class κ 0.26 (from
v0.2's 0.23 / 0.12) and removed the directional bias. The one residual fixable boundary — "effective
use of a genAI tool" vs infrastructure — was tightened in IN2/EX1 (+ worked examples); the CS/SE
scope (EX3) was reinforced. With these, all blind disagreements reconciled. A simplification of v0.2
(`inclusion-exclusion-criteria.md`)
informed by the test run: the abstract dual-screen showed disagreement concentrated on a
single axis (literacy-as-object vs activity-embedded), and four exclusions did ~95% of the
work while seven boundary rulings had accreted as patches. v0.3 keeps the **same scope** but
states it more crisply and anchors the hard boundary with worked examples. Nothing is silently
dropped — see the §Lineage table. **Not yet frozen**: intended to be calibrated at the abstract
stage (≈25 abstracts, Ric + agents, target κ) and then frozen before the definitive run.*

**Anti-circularity principle.** Inclusion is anchored to the *construct definition* of
generative-AI literacy (below). The discovered taxonomy (codebook v0.2, A1–A7) and the team's
course ILOs are used as **illustrative examples only — never as the gate**. This preserves the
review's independence from the course being designed.

---

## Construct definition (the inclusion anchor)
**Generative-AI literacy** = knowledge, skills, and dispositions *about generative AI itself*:
its capabilities and limitations; effective and critical use (including prompting); evaluation
and verification of outputs; ethical/responsible use; and human–AI collaboration. Distinct from
merely *using* a genAI tool to learn something else.

## Inclusion — a paper is included iff ALL four hold

| # | Test | Detail |
|---|---|---|
| **IN1 Population** | Students in degree-granting higher education, in a **computer-science or software-engineering** programme, or in a CS/SE course (incl. non-majors taking such a course — tag `majors`/`non-majors`/`mixed`). | **CS+SE-core scope** (decided 2026-06-30, matches query v1.1): other computing sub-disciplines (IS, data science, IT, informatics, HCI) are out of scope this iteration. *Waived for the `construct` stratum* (population-agnostic genAI-literacy frameworks/instruments — see Strata). |
| **IN2 genAI-literacy ILO or activity** | Reports at least one **identifiable, concrete** intended learning outcome **or** learning activity targeting genAI literacy *about genAI itself*, in one of: foundational understanding · effective use & prompting · critical evaluation/verification of output · ethical & responsible use · integration into practice · metacognition & agency · human–AI collaboration. | The genAI-literacy element need not be the whole paper, but must be identifiable and concrete enough to code. **ILOs and activities both count, and may appear separately** (a paper may contribute only an activity). "Concrete" = specific enough to enter the taxonomy. **"Effective use" qualifies only when it builds *transferable genAI competence*** — prompting strategy, tool/model selection, output evaluation/verification, awareness of capabilities/limits. Merely using a genAI tool to accomplish a domain task (navigate a codebase, pass a course), with the tool as productivity infrastructure, is **EX1, not IN2**. |
| **IN3 Time** | Published **November 2022 or later**. | Strict event boundary (ChatGPT release). Year-2022 rows month-checked. *Exception: a small `foundational` stratum of canonical pre-2022 AI-literacy frameworks may be seeded deliberately — tagged, not from the query.* |
| **IN4 Publication** | Peer-reviewed venue (journal, conference, workshop), in English. | Preprints included but **tagged `preprint`** (O1). Grey literature from professional bodies tagged `grey` (O3). |

## Exclusion — a paper is excluded if ANY one fires

| # | Exclusion | Typical case |
|---|---|---|
| **EX1 Infrastructure-only** | genAI used only as a tool/aid, with **no genAI-directed ILO or activity** (fails IN2) — incl. teaching students to *use* a genAI tool productively for a domain task (navigate a codebase, complete assignments) without building transferable genAI competence. | "CS1 with Copilot" where the only outcomes are programming skills; "use Copilot to work with a large codebase" with no prompting/evaluation focus. |
| **EX2 Tool-eval / benchmarking** | Evaluates model/tool performance with **no student learning design**. | Benchmarking LLMs on exam questions, tutoring quality, code generation. |
| **EX3 Out-of-population** | K-12, general public, workplace/professional training, or students outside CS/SE only — incl. other computing sub-disciplines (IS, data science, IT, informatics, HCI) and non-computing (fails IN1, and not `construct`). | Cross-faculty "AI for everyone"; a data-science-only or IS-only cohort with no CS/SE slice. |
| **EX4 Use / perception / policy only** | Attitude, adoption, usage, integrity, detection, or policy study with **no instructional design** (no ILO, no activity). | Attitude surveys, usage analytics, plagiarism-detection, policy analyses. |

*(A paper that is simply **not about genAI literacy** — e.g. pre-genAI AI/ML literacy — is
excluded by failing IN2, no separate criterion needed.)*

## Operational handling (not quality exclusions)
- **Secondary studies** (reviews, meta-analyses, bibliometrics): excluded from the corpus but
  **harvested for snowballing** and logged as such.
- **Not retrievable in full text / not English / minor (e.g. < 3 pp, abstract-only):** logged
  and set aside, not silently dropped.

## Strata & tags (carried over unchanged — filter-flippable, no re-screening on WG reversal)
- **`construct`** — population-agnostic genAI-literacy frameworks/instruments (e.g. GLAT, GAILS,
  *Twelve Competencies*, AI-literacy heptagon). IN1 waived; must still be genAI-specific and
  concrete. Feeds RQ-a (ILO taxonomy), not RQ-b computing-practice claims. **`instrument`** for
  validated scales/inventories.
- **O1 `preprint`**, **O2** strict Nov-2022 window (year-2022 month-checked), **O3 `grey`**
  (professional-body curricula). Provisionally adopted; WG reversal = filter flip.
- Coding tags applied at extraction: `maturity` (proposed/implemented/evaluated) ·
  `population` (majors/non-majors/mixed/none) · `rq_lean` (RQ-a/RQ-b/both) ·
  `assessment` (RQ-c, where reported).

## Decision aids — worked examples for the hard boundary (EX1 vs IN2)
These replace v0.2's boundary rulings B1–B7. Disagreement on these means the criteria text needs
work, not the paper.

| Case | Verdict | Why |
|---|---|---|
| Prompt-construction exercises taught in CS1 (*Prompt Problems*) | **Include** | concrete prompting activity (IN2), even when motivated as a programming skill |
| Teaching students to **verify/critique/debug AI-generated code** | **Include** | output evaluation is core genAI literacy (IN2) |
| CS1 that merely uses an AI tutor, outcomes purely programming | **Exclude EX1** | no genAI-directed ILO |
| Teaching students to use Copilot productively for a software task (navigate a large codebase), no prompting/evaluation focus | **Exclude EX1** | tool as productivity infrastructure, not transferable genAI competence |
| Teaching students *prompting strategy / how to evaluate or when to trust* a coding assistant | **Include** | builds transferable genAI competence (IN2 effective use) |
| LLM benchmarked on undergraduate CS exam questions | **Exclude EX2** | tool performance, no learning design |
| Survey of students' genAI adoption/attitudes, no instruction | **Exclude EX4** | perception only |
| Population-agnostic genAI-literacy framework/scale (no computing slice) | **Include (`construct`)** | IN1 waived for the construct stratum |
| University-wide "AI for everyone", no identifiable CS/SE slice | **Exclude EX3** | unless a CS/SE-student slice is identifiable |
| Embedded activity (prompting / output-eval) inside a CS course, literacy not the central object | **Include** | ILOs and activities both in scope and may appear separately (IN2) |

---

## Lineage — how v0.2 maps into v0.3 (nothing dropped)

| v0.2 | v0.3 |
|---|---|
| I1 population | IN1 |
| I2 concept · I4 concrete evidence · B1 prompting · B5 output-eval · B7 ILO/activity-separate | merged into **IN2** + worked examples |
| I3 time · O2 window | IN3 |
| I5 publication · O1 preprints · O3 grey | IN4 + Strata |
| E1 | EX1 |
| E2 | EX2 |
| E3 · B4 university-wide | EX3 + worked example |
| E5 · E6 integrity/detection/policy | EX4 |
| E4 non-generative | folded into "fails IN2" |
| E7 secondary | Operational (snowball harvest) |
| E8 not retrievable · E9 minor | Operational |
| B2 faculty-planning incl. concrete ILOs | covered by IN2 (concrete ILO/activity required) |
| B3 instruments · B6 population-agnostic constructs | `construct`/`instrument` strata (IN1 waiver) |

**Net change:** 5 inclusion + 9 exclusion + 7 boundary rulings → **4 inclusion + 4 exclusion +
worked examples**, same scope. The only genuinely *new* element is the optional `foundational`
pre-2022 framework stratum (IN3 exception), added because the course rests on frameworks the
date window excludes.
