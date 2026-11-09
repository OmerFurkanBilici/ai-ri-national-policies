# LLM-assisted rater: procedure (validation/ai_rater_codes.csv)

**Purpose.** A second, independent rater for the 40-summary validation sample, used to estimate the agreement of the dictionary coding before human double coding is available. It is **not** a substitute for the human validation specified in the proposal and is reported separately in Table 1.2.

**Model.** Claude Opus 5.5 (Anthropic; API model string `claude-opus-5-5`), used through the Claude app in an interactive session on 9 November 2026.

**Input given to the rater.** For each of the 40 sampled instruments: the Tracker `summary_plain` text (with the slug, country, title and binding flag as they appeared in the v1.0.0 validation sheet). Coding rules: the 13 operational definitions in Table S2 (`definition` column).

**Blinding.** Partial. The rater did not see the dictionary codes or matched terms for the 40 summaries (Table S4) before coding. Limitation (prior exposure): the same model had read the notebook, including the codebook's regular expressions, while revising the analysis; the codes were assigned from the written definitions, and no code was changed after the dictionary–rater agreement was computed.

**Instruction (paraphrased prompt).** "Code each summary on the 13 binary sub-themes. Assign 1 only if the summary itself explicitly expresses the sub-theme as defined; otherwise 0. Use no outside knowledge about the instrument. Apply each definition consistently across summaries."

**Procedure.** Single pass, one summary at a time, all 13 codes per summary; decision rules fixed during coding (e.g., security/security assessments counted as risk assessment and safety; obligations counted only when imposed on actors, not when a law merely asks government to adopt a plan; existing ministries coordinating were not counted as a dedicated institution). Output saved unchanged as `ai_rater_codes.csv` (columns `slug` + 13 codes).

**Reporting.** In the manuscript's Methods, report the model, date and procedure above, and present dictionary-vs-LLM κ as an exploratory agreement check, separately from human coder A–B and dictionary-vs-consensus κ (Elsevier requires disclosure of AI use in the research process).
