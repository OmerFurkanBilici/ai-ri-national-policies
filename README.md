# Responsible Innovation in National AI Policies — Analysis Code, Data Snapshot and Results

**Group 7 · Team Batman** — Necla İlayda Güler & Ömer Furkan Bilici
Module: *AI, Power & Responsibility: Governing Intelligence*
Target journal: *Technological Forecasting and Social Change* (Elsevier)
Version: **v1.2.1** (revised analysis after three rounds of technical review; v1.0.0 was the first executed run)

This repository is the replication package for our study. It contains the executed notebook with all outputs, the exact input files used (with SHA-256 checksums), the validation codings, and every figure and table produced by the final run.

## Research questions

| RQ | Question |
|---|---|
| RQ1 | Which responsible innovation dimensions do national AI policy instruments articulate, and does the RI profile shift from ethics-oriented reflexivity in non-binding instruments to risk- and accountability-oriented responsiveness in binding ones? |
| RQ2 | Is government effectiveness associated with national AI strategy adoption, and is this association conditional on a country’s income level? |
| RQ3 | *As analysed:* among countries with a recorded AI policy, is government effectiveness associated with having an enacted national binding measure? (The proposal asked whether strategic commitments are actualized into binding instruments or decoupled; that transition would require linking individual strategies to later laws, which the cross-sectional data do not allow, so the decoupling interpretation is not claimed.) |
| RQ4 | How have the legal status and responsible innovation profile of AI policy instruments changed between the pre-generative-AI period (2017–2022) and the generative-AI period (2023 onward)? |

**Scope of inference.** All analyses are cross-sectional and observational. Country-level results describe associations between governance indicators and the instruments *recorded by the AI Policy Tracker*; they do not trace individual strategies into law and are not causal estimates. RI content is coded from the Tracker's short policy summaries, not from full policy texts.

## Repository contents

| Path | Content |
|---|---|
| `ai_ri_policy_analysis.ipynb` | Executed notebook (v1.2.1) with all cell outputs; every code cell is preceded by a markdown cell explaining what it does and which RQ / method step it serves |
| `data/` | Exact input snapshot used for the archived run, `checksums.sha256`, and `data/README.md` (sources, licences, retrieval) |
| `validation/ai_rater_codes.csv` | Blind LLM-assisted codings of the 40-summary validation sample (see *Coding validation*) |
| `validation/llm_rater_procedure.md` | Model, date, instruction and procedure of the LLM-assisted rater |
| `validation/coding_protocol.md`, `validation/coding_sheet_coder_A.xlsx`, `validation/coding_sheet_coder_B.xlsx` | Protocol and blind sheets (randomized IDs, summary text only) for human double coding |
| `results/ai_ri_policy_results.zip` | All outputs of the final run in one archive |
| `results/outputs/` | The same outputs unzipped: `figures/` (8 figures, PDF + PNG), `tables/` (CSV), `key_findings.md`, `session_info.txt` |
| `requirements.txt` | Pinned Python environment of the archived run |
| `CITATION.cff`, `LICENSE` | Citation metadata; MIT licence for the code |

## How to reproduce

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute ai_ri_policy_analysis.ipynb --output ai_ri_policy_analysis.ipynb
```

Run from the repository root. The notebook reads the inputs from `data/` under their **original file names**, verifies them against `data/checksums.sha256` (reported in Table S1c) and writes all results to `./outputs` and `./ai_ri_policy_results.zip`. Runtime is about one minute on a laptop CPU.

**On Kaggle:** upload the three files from `data/` (names unchanged; matching is case-insensitive) and `validation/ai_rater_codes.csv` as one dataset, import the notebook, attach the dataset and *Run All*. Results appear under `/kaggle/working/outputs`.

**Fresh download.** The Tracker is a living database. A newer download of `policies.csv` or `jurisdictions.csv` will have a different checksum (flagged as *NO – different snapshot* in Table S1c) and can change the results; use the files in `data/` to reproduce the archived numbers exactly.

## Data

| Dataset | Files | Source | Licence |
|---|---|---|---|
| AI Policy Tracker — Open Data | `policies.csv`, `jurisdictions.csv` | https://aipolicytracker.org/open-data | CC BY 4.0 |
| World Bank Worldwide Governance Indicators, 2026 release | `WGI 2026 Governance Estimates and Scores (1996-2025).xlsx` | https://datacatalog.worldbank.org/search/dataset/0038026/worldwide-governance-indicators | CC BY 4.0 |

Details, retrieval information and checksums: `data/README.md`.

## Execution procedure

| Step | Purpose | RQ |
|---|---|---|
| 1–1b | Set-up, session info, explicit input paths and checksum verification | all |
| 2 | Load and audit the source files | all |
| 3 | Country-level sample; reference date and its source; procedural stage (proposal / finalized / archived or superseded) and legal status (enacted binding / binding proposal / non-binding finalized / non-binding proposal / non-binding archived or superseded) | all |
| 4 | Link WGI Government Effectiveness, Regulatory Quality and income group | RQ2, RQ3 |
| 5 | Country indicators (recorded strategy, any recorded policy, enacted national binding measure, EU membership) | RQ2, RQ3 |
| 6 | RI codebook with operational definitions (Stilgoe et al., 2013 dimensions + actualization markers) | RQ1, RQ3, RQ4 |
| 7–7b | Dictionary coding of all summaries; validation sample; exploratory dictionary–LLM agreement check (κ) | RQ1 |
| 8 | Enacted binding vs finalized non-binding RI profile (proposals and archived/superseded records excluded): Fisher tests, BH q-values; country-clustered, length-adjusted logits | RQ1 |
| 9 | Recorded strategy adoption vs GE within income groups; M1–M3 logits, LR test; interaction re-estimated for pre-period GE and Regulatory Quality | RQ2 |
| 10 | GE across policy stages (Kruskal–Wallis, Holm-adjusted pairwise tests); two-stage Firth logit with convergence/rank checks and profile CIs; strategy × law co-occurrence and chronology | RQ3 |
| 11 | 2017–2022 vs 2023–2025 comparison of the recorded instrument mix; missing dates; clustered/length-adjusted, finalized-only and partial-2026 sensitivities | RQ4 |
| 12 | Robustness checks with fixed outcomes and model terms (Table S3) | all |
| 13–14 | Data-driven key findings; manifest with checksums; results zip | all |

## Outputs

8 figures (two per RQ, as planned in the proposal) and the following tables: 1.1–1.4, 2.1–2.3, 3.1–3.4, 4.1–4.5, and supplementary tables S1a–S1d, S2–S9 (S5 = blind human coding sheet, S5b = its ID key). `results/outputs/tables/manifest.csv` lists every file with its research question and SHA-256 checksum.

## Coding validation

Dictionary codes are the single measurement used for all instruments. A stratified sample of 40 summaries (fixed seed) was coded by an **LLM-assisted rater** (Claude Opus 5.5, Anthropic) from the operational definitions in Table S2, without access to the dictionary codes for these summaries but with prior exposure to the dictionary rules. Table 1.2 is therefore an **exploratory dictionary–LLM agreement check**; agreement and Cohen's κ are reported per code and per dimension in Table 1.2, and the procedure is documented in `validation/llm_rater_procedure.md`. **This is not a human validation, and the RI findings that depend on the coding (RQ1, RQ3 concreteness, RQ4 profile) are presented as exploratory.** *Deviation from the proposal:* the proposal planned two independent human coders with an adjudicated consensus; this was not carried out for v1.2.0, so reliability evidence rests on the LLM-assisted rater only (7 of 13 sub-themes reach κ ≥ 0.70; dimension-level κ 0.66–0.85). Human double coding can still be added without changing the code: two coders fill `validation/coding_sheet_coder_A.xlsx` / `_B.xlsx` independently (randomized IDs, summary text only), save them as `coder_A.xlsx` and `coder_B.xlsx`, adjudicate disagreements into `consensus.xlsx`, and re-run. The notebook then reports coder A–B and dictionary–consensus agreement and κ, and reports human validation as complete only when all three files are present.

## Limitations

RI themes are coded from short Tracker summaries rather than full texts; the Tracker is a curated, living database with uneven country coverage; the design is cross-sectional, so results are associations, not causal effects; recorded commitments are not evidence of implementation or enforcement; Stage 2 of RQ3 rests on few events and has wide confidence intervals; the human double coding planned in the proposal was not carried out, so coding reliability is supported only by an LLM-assisted rater, and six sub-themes fall below κ = 0.70.

## How to cite

Güler, N. İ., & Bilici, Ö. F. (2026). *Responsible Innovation in National AI Policies — analysis code, data snapshot and results* (Version 1.2.1) [Software]. Zenodo.

Zenodo assigns the version-specific DOI when the GitHub release is archived, so it cannot be written into the archived files themselves; it is shown on the Zenodo record of release v1.2.1 and is added to this README and `CITATION.cff` on GitHub after the release. Earlier versions (superseded): v1.2.0 = https://doi.org/10.5281/zenodo.24091090; v1.0.0 = https://doi.org/10.5281/zenodo.24089357.

## Data citation

- AI Policy Tracker, Open Data (CC BY 4.0). https://aipolicytracker.org/open-data
- World Bank (2026). Worldwide Governance Indicators, 2026 update (CC BY 4.0). https://www.worldbank.org/en/publication/worldwide-governance-indicators
