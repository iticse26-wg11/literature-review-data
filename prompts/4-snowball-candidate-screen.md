# Prompt template — snowball candidate screen

Snowball candidates re-enter the standard cascade, with two twists: the
input rows are *references/citers* (often incomplete metadata), and the
seen-set dedup has already happened. Title stage first, then abstract for
survivors (recover abstracts by DOI), then the stage-5 full-text pass for
anything still standing.

---

You are screening SNOWBALL CANDIDATES for a systematic literature review on
[generative-AI literacy education for computing students in higher
education]. These are [references extracted from / papers citing] confirmed
corpus papers.

Read the frozen criteria: [inclusion-exclusion-criteria-v0.3.md, v0.3.1].

Read [candidates-NN.csv]: ref_id, citing/cited id, year, title[, abstract].

Apply the same conservative rules as the main screen:
- title stage: exclude only on an unambiguous criterion; advance on any
  uncertainty; route reviews to the harvest list rather than dropping.
- abstract stage: include / maybe / exclude with criterion, confidence,
  <=15-word rationale.
- REMEMBER the publication criteria: peer-reviewed venue AND English full
  text (state language if determinable) AND in the review window. (A
  non-English full text behind an English title/abstract is a known trap.)

Also record provenance untouched: which corpus paper led here, and the
round number.

Return ONLY CSV lines, one per record, no commentary:
ref_id,verdict,criterion,confidence,rationale

Every record must appear exactly once.

---

## Notes for the operator

- Dedup BEFORE screening (dedup_refs.py vs the cumulative seen-set) — never
  spend agent calls on records already judged, and never let a
  previously-rejected record sneak back in a later round (dedup against
  *seen*, not against *included*).
- Verify DOIs of anything advancing; a non-resolving DOI with plausible
  metadata is a fabricated-reference signal — log it.
- Every eventual addition still goes through the stage-5 full-text
  eligibility prompt before joining the corpus.
