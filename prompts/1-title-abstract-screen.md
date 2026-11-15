# Prompt template — abstract screen

One agent per blind batch. Attach the frozen criteria and the batch file
(record_id, title, year, abstract). Template:

---

You are performing TITLE+ABSTRACT screening for a systematic literature
review on [generative-AI literacy education for computing students in higher
education].

Read the attached criteria document ([inclusion-exclusion-criteria-v0.3.md],
version [v0.3.1], FROZEN). Apply the inclusion test and exclusion criteria
exactly as written, including the worked examples.

Then read [batch-NN.csv]: record_id, title, year, abstract.

For EACH record return one verdict:

- **include** — the abstract gives positive evidence for every inclusion
  criterion and no exclusion criterion fires.
- **exclude** — an exclusion criterion fires, or an inclusion criterion is
  clearly unmet. Name the single criterion that decides it.
- **maybe** — genuinely on the boundary: plausibly eligible but the abstract
  is missing the decisive information (e.g. population unstated, learning
  intent unclear, genAI-specificity uncertain). Do NOT use maybe to hedge
  clear calls; every maybe costs a human review.

Also tag:
- confidence: high / medium / low
- stratum: [population tag — e.g. CS-majors / non-majors / construct
  (population-agnostic framework or instrument) / out-of-scope]
- rationale: <= 15 words citing the decisive phrase of the abstract.

Return ONLY CSV lines, one per record, no commentary:
record_id,verdict(include|maybe|exclude),criterion,confidence,stratum,rationale

Every record must appear exactly once.

---

## Notes for the operator

- Run a human/agent calibration on ~25 records with `kappa.py` BEFORE the
  full pass; fix criteria text until kappa is acceptable and unbiased, then
  freeze.
- Dual-screen a ~100-record random sample during the pass (human blind);
  adjudicate disagreements against the frozen text.
- Every maybe must be resolved by a human before the full-text stage.
