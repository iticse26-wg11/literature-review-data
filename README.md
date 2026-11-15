# Literature Review Data

Data behind the hybrid literature review in the ITiCSE 2026 Working Group 11 report, *Generative AI Literacy for Computing Students: A Proposal for Learning Outcomes and Activities* (Section 5). It holds every screening decision from the database search to the final set of 105 papers, the agreement check on the agent screen, the coding of the 71 activity papers, and the criteria and prompts the agents worked from.

The ILOs the activity coding refers to (H01, MM03, CS04a, …) are defined in [intended-learning-outcomes](https://github.com/iticse26-wg11/intended-learning-outcomes).

## Contents

| Folder | What it holds |
|---|---|
| [`data/`](data/) | One CSV per review stage, `1-seed.csv` to `8-final-set.csv`. Each paper keeps one `record_id` from start to finish. |
| [`validation/`](validation/) | The blind human check of the agent screen on a sample of 100 titles. |
| [`activities/`](activities/) | The 71 activity papers: course, what the activity asks of students, the ILOs it develops or relies on, and the GenAI literacy gaps the paper reports. |
| [`criteria/`](criteria/) | The inclusion and exclusion criteria (v0.3.1), frozen before the screen ran. |
| [`prompts/`](prompts/) | The prompt templates the agents were given at each stage. |

## Method

The report describes the method in full (Section 5.1). In short:

1. **Search.** On 30 June 2026 we queried OpenAlex, Scopus and the ACM Digital Library over titles and abstracts, for work published from November 2022. The query is *(GenAI literacy phrase AND higher-education population) OR (GenAI technology term AND computing-education population)*. A seed set of 60 papers (29 from WG members, 31 from the ICER 2025 integrative review of AI literacy) was screened the same way.
2. **Title and abstract screen.** Language-model agents screened every record in blind batches against the frozen criteria, returning include, maybe or exclude. The review lead resolved every maybe and the 24 records with no abstract. An earlier title-only screen was dropped after validation showed it excluded too much (`validation/`).
3. **Read and tag.** The review lead assigned each advancing paper to one of four categories (motivation, frameworks, assessment, activities), checked it against the criteria, and ruled on an agent full-text eligibility screen that cited evidence for each criterion.
4. **Snowball.** Every included paper was snowballed backward through its references until a round added nothing, and forward through citing papers (OpenAlex and Semantic Scholar, to 30 June 2026). Candidates were screened by title, abstract and full text under the same criteria; every addition was confirmed at full text.
5. **WG review.** Three WG members each read the full texts of one category and filed exclusions as GitHub tickets, which were applied as filed. The WG dissolved the motivation category as too vague for the report's aim.
6. **Activity analysis.** Agents coded each activity paper from its full text: the activity, the course, whether it develops or relies on GenAI literacy, the ILOs involved, and the gaps the paper reports. Every code carries a verbatim quote that was checked automatically against the paper's text. The review lead ruled on each paper's inclusion.

| | Motivation | Frameworks | Assessment | Activities | Total |
|---|---|---|---|---|---|
| Include set (stage 5) | 7 | 42 | 12 | 75 | 136 |
| Snowball (stage 6) | +1 | +12 | +11 | +17 | +41 |
| WG review (stage 7) | −8 | −32 | −12, +1 | −21 | −73, +1 |
| **Final set (stage 8)** | – | **22** | **12** | **71** | **105** |

### Who decided what

| Stage | Agents | Humans |
|---|---|---|
| Title and abstract screen | Screened every record | Review lead resolved every maybe; a second reader checked a sample of 100 (`validation/`) |
| Read and tag | Suggested a category; screened full texts with evidence quotes | Review lead assigned categories and ruled on every paper |
| Snowball | Screened candidates by title, abstract and full text | Review lead resolved every maybe and confirmed every addition |
| WG review | — | Three WG members, one per category |
| Activity analysis | Coded each paper, with quotes checked against the text | Review lead ruled on each paper's inclusion; no second coder checked the codes |

Agent exclusions at the title and abstract stage were not checked one by one; the validation sample and the snowball are the checks on them. Every exclusion after that stage was a human decision.

## Guide

### Following a paper

Search for its `record_id` across the files in `data/`. The prefix tells you where it came from:

| Prefix | Source |
|---|---|
| `R`, `N` | Database search |
| `WG-`, `GE-`, `EXT-`, `FND-` | Seed set |
| `C1-`, `C2-`, `C5-` | Backward snowball from the motivation, framework and assessment papers |
| `FS-`, `FW-` | Forward snowball (citing papers) |
| `C4B1-`, `C4F1-` | Backward and forward snowball from the activity papers |
| `NP-` | Proposed by a WG member during the WG review |

`5-read-and-tag.csv` shows the category and the review lead's verdict, `6-snowball-set.csv` how a snowball paper was found (`found_via`), `7-wg-review.csv` the WG member's reason for an exclusion, and `8-final-set.csv` whether the paper is in the final set.

### Reproducing the report's numbers

| Report | File | How |
|---|---|---|
| Figure 1: search and screen | `data/2-database.csv`, `3-merge-dedup.csv`, `4-title-abstract-screen.csv` | Count rows by `source_db`; count `final_decision` = `advance` (195) |
| Title validation (κ 0.30, AC1 0.31) | `validation/title-validation.csv` | Compare `agent_verdict` with `human_verdict` (advance or exclude) |
| Read and tag: 136 included | `data/5-read-and-tag.csv` | Count `disposition` by `contribution_type` (C1 motivation, C2 frameworks, C5 assessment, C4 activities) |
| Figure 2: snowball and WG review | `data/6-snowball-set.csv`, `7-wg-review.csv` | Count rows by `contribution_type`; count `action` |
| Final set of 105 | `data/8-final-set.csv` | Count `contribution_type` |
| Table 4: activity papers by course | `activities/activity-papers.csv` | Group by `course_group`; count `develops`, `relies` and `gap_reported` = `yes` |
| Table 5: activity papers by competence | `activities/ilo-mapping.csv`, `competence-groups.csv` | Join on `ilo`. A paper counts under *Develop* if it develops any ILO in the group, and under *Rely only* if it relies on one but develops none |
| Gap types (5.5) | `activities/gap-summary.csv`, `gaps.csv` | One row per gap type, and one row per coded gap with its quote |

### Criterion codes

The criteria document uses IN1–IN4 and EX1–EX4. The report numbers them IC1–IC5 and EC1–EC4, splitting IN4 (peer-reviewed and in English) into IC4 (publication) and IC5 (language). The WG review form used its own codes:

| Code | Meaning |
|---|---|
| E1 | GenAI used only as teaching infrastructure (EX1) |
| E2 | Tool evaluation without a student learning design (EX2) |
| E3 | Population out of scope (EX3) |
| E4 | Non-generative AI literacy only |
| E5, EC4 | Perception, adoption or position paper without instructional design (EX4) |
| E7 | Secondary study (literature review) |
| E8 | Full text not retrievable |
| E9 | Minor paper (under 3 pages, abstract or poster) |

### Columns

- `4-title-abstract-screen.csv`: `verdict` and `criterion` are the agent's; `maybe_verdict` is the review lead's ruling on a maybe; `final_decision` is the outcome; `abstract_source` says where the abstract came from; `tag` = `ext` marks 27 papers that an earlier title-only screen had excluded.
- `5-read-and-tag.csv`: `ric_verdict` is the review lead's criteria check, `ft_verdict` the full-text ruling, `disposition` the result (`corpus`, `C4`, `excluded`, `duplicate`).
- `6-snowball-set.csv`: `snowball` is the run that found the paper, `direction` backward or forward, `wg_review` what happened to it in the WG review.
- `7-wg-review.csv`: one row per ticket; `criterion`, `reason` and `evidence` are the reviewer's own words.
- `activities/fulltext-check.csv`: the coded answers for all 87 activity papers read in full, with `keep` (the agent's recommendation) and `ruling` (the review lead's decision).
- `activities/ilo-mapping.csv`: one row per paper and ILO; `role` is `develops` or `requires`, `evidence` a quote from the paper.

## What is not here

- **Full texts and abstracts.** Publishers and database licences do not allow us to share them. Every paper has a DOI or stable locator (`doi`, `locator`).
- **The title and abstract validation.** The report gives κ 0.70 and AC1 0.85 for a second human check of the title and abstract screen; those decisions will be added here.

## Licence and citation

The data is released under [CC BY 4.0](LICENSE). Paper titles, identifiers and short quotes belong to their authors. Please cite the working group report; [`CITATION.cff`](CITATION.cff) gives the reference.
