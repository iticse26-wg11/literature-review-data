# Prompt template — full-text eligibility pass

One agent per paper (or small batch). Used verbatim (modulo brackets) for the
v1.1 corpus; this is the prompt that produced our WG-13 exclusion and R2483
retype, so it is battle-tested on both outcomes.

---

You are performing a full-text eligibility screen for a systematic
literature review on [generative-AI literacy education for computing
students in higher education].

1. Read the criteria file: [report/inclusion-exclusion-criteria-v0.3.md]
   (criteria [v0.3.1] — the frozen operative version).
2. Read the full text: [path/to/<ID>.txt]
   (Paper [ID], currently [status/type], "[title]".)

Apply the criteria to the FULL TEXT. Pay particular attention to:
- genAI-specificity (generative AI, not general-AI literacy only — the most
  frequent full-text overturn reason)
- population ([computing students in higher education]; note if broader)
- whether it reports concrete ILOs and/or learning activities with learning
  intent about genAI itself (recommendations in a discussion section do NOT
  count)
- publication criteria ([peer-reviewed venue, English, in window])

Your final message must be ONLY these semicolon-delimited fields on one
line, followed by a verbatim evidence quote:

ft_verdict(include|exclude);ft_criterion(deciding code or 'meets-all');ft_population(...);ft_maturity(proposed|implemented|evaluated);ft_strata(short tag);ft_ilo_activity(<=25 words summarising the ILOs/activities found)
EVIDENCE: "<verbatim quote from the full text that supports the verdict>"

---

## Notes for the operator

- Run this BEFORE the paper is used as a snowball root or cited in analysis.
- The evidence quote is non-negotiable: verify it exists in the text
  (a fabricated quote is how you catch a hallucinating pass).
- Expect ~20% of abstract-stage includes to fall here; every overturn goes
  to the human for the final call, with the corpus-changing procedure in
  `MANUAL.md`.
