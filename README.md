# Responsible Innovation in National AI Policies — Analysis Code and Results

**Group 7 · Team Batman** — Necla İlayda Güler & Ömer Furkan Bilici
Module: *AI, Power & Responsibility: Governing Intelligence*
Target journal: *Technological Forecasting and Social Change* (Elsevier)

This repository contains the **final executed run** of the analysis for our research proposal: the notebook with all cell outputs, and every figure and table it produced (`results/`). Re-running the notebook on the public data reproduces all results.

## Research questions

| RQ | Question |
|---|---|
| RQ1 | Which responsible innovation dimensions do national AI policy instruments articulate, and does the RI profile shift from ethics-oriented reflexivity in non-binding instruments to risk- and accountability-oriented responsiveness in binding ones? |
| RQ2 | Is government effectiveness associated with national AI strategy adoption, and is this association conditional on a country’s income level? |
| RQ3 | Among countries that have adopted AI policies, does governance capacity predict the actualization of strategic commitments into binding instruments, or are the two decoupled? |
| RQ4 | How have the legal status and responsible innovation profile of AI policy instruments changed between the pre-generative-AI period (2017–2022) and the generative-AI period (2023 onward)? |

## Files

| File | Content |
|---|---|
| `ai_ri_policy_analysis.ipynb` | The executed notebook with outputs (19 code cells, each preceded by a markdown cell explaining what it does and which RQ / method step it serves) |
| `results/ai_ri_policy_results.zip` | All outputs of the final run in one archive |
| `results/outputs/` | The same outputs unzipped: `figures/` (Figures 1–4, PDF + PNG), `tables/` (CSV), `key_findings.md` |
| `requirements.txt` | Python dependencies |
| `README.md` | This file |

## Dependencies

Python ≥ 3.10 with `pandas`, `numpy`, `matplotlib`, `scipy`, `statsmodels`, `openpyxl` (and optionally `scikit-learn`). All are pre-installed on Kaggle. Locally:

```bash
pip install -r requirements.txt
```

No machine learning and no GPU are needed.

## Dataset access

Both datasets are public, free, need no registration and are licensed under **CC BY 4.0**.

| Dataset | Files to download | URL |
|---|---|---|
| AI Policy Tracker — Open Data | `policies.csv` (policy instruments) | https://aipolicytracker.org/open-data/policies.csv |
| | `jurisdictions.csv` (jurisdiction profiles) | https://aipolicytracker.org/open-data/jurisdictions.csv |
| | Landing page | https://aipolicytracker.org/open-data |
| World Bank Worldwide Governance Indicators (WGI), 2026 release | `WGI 2026 Governance Estimates and Scores (1996-2025).xlsx` | https://datacatalogfiles.worldbank.org/ddh-published/0038026/DR0095947/WGI%202026%20Governance%20Estimates%20and%20Scores%20(1996-2025).xlsx |
| | Catalog page | https://datacatalog.worldbank.org/search/dataset/0038026/worldwide-governance-indicators |

File names do not need to be changed: the notebook finds any file whose name contains `policies` (.csv), `jurisdictions` (.csv) and `wgi` (.xlsx), regardless of upper or lower case.

## How to run

**On Kaggle (recommended)**
1. *Datasets → New Dataset*: upload the three files above and create the dataset.
2. *Code → New Notebook → File → Import Notebook*: select `ai_ri_policy_analysis.ipynb`.
3. *Add Input*: attach the dataset from step 1.
4. *Run All* (about one minute on the default CPU).
5. Results appear under `/kaggle/working/outputs` and as `/kaggle/working/ai_ri_policy_results.zip` (*Output* tab).

**Locally**
1. Put the three data files in the same folder as the notebook (or any sub-folder).
2. `pip install -r requirements.txt`
3. `jupyter notebook ai_ri_policy_analysis.ipynb` → *Run All*. Results go to `./outputs` and `./ai_ri_policy_results.zip`.

## Execution procedure (what the notebook does)

| Step | Purpose | RQ |
|---|---|---|
| 1–1b | Set-up, output folders, publication style, locate input files | all |
| 2 | Load and audit the three source files | all |
| 3 | Keep country-level instruments; build a frame of all countries (non-adopters kept) | all |
| 4 | Link WGI Government Effectiveness, Regulatory Quality and income group | RQ2, RQ3 |
| 5 | Country indicators (strategy, any policy, enacted binding instrument, EU AI Act sensitivity) | RQ2, RQ3 |
| 6 | Responsible-innovation codebook (Stilgoe et al., 2013 dimensions + actualization markers) | RQ1, RQ4 |
| 7 | Apply the codebook to policy summaries; export coding sheet and validation sample | RQ1, RQ4 |
| 8 | Binding vs non-binding RI profile: Fisher exact tests, odds ratios, Benjamini–Hochberg | RQ1 |
| 9 | Strategy adoption vs GE within income groups: Mann–Whitney, logit with GE × income | RQ2 |
| 10 | Articulation vs actualization: Kruskal–Wallis, two-stage Firth logistic regression | RQ3 |
| 11 | 2017–2022 vs 2023+: Fisher exact tests, Benjamini–Hochberg | RQ4 |
| 12 | Robustness checks (verified records, pre-period GE, Regulatory Quality, EU) | all |
| 13 | Data-driven summary of key findings (numbers taken from the tables) | all |
| 14 | Manifest and single zip of all outputs | all |

## Outputs (included in `results/`; re-created when the notebook is run)

- `outputs/figures/` — Figures 1–4, one per RQ, as **PDF** (and PNG)
- `outputs/tables/` — all tables as **CSV** (main tables per RQ, codebook, robustness checks, coding sheet, validation sample, country dataset)
- `ai_ri_policy_results.zip` — everything above in one archive

## Optional: manual coding

To replace the dictionary coding with human-verified codes, add a file `manual_coding.csv` (column `slug` plus any code columns such as `ref_ethics`, `ant_risk`, values 0/1) to the input data. The notebook then uses these codes and reports Cohen’s κ against the dictionary coding.

## Limitations

Responsible-innovation themes are coded from the tracker’s short policy summaries, not from full policy texts; the tracker is a curated selection with uneven country coverage; the design is cross-sectional, so results are associations rather than causal effects; and documented commitments are not evidence of actual implementation or enforcement.

## Data citation

- AI Policy Tracker, Open Data (CC BY 4.0). https://aipolicytracker.org/open-data
- World Bank (2026). Worldwide Governance Indicators, 2026 update (CC BY 4.0). https://www.worldbank.org/en/publication/worldwide-governance-indicators

## How to cite

Güler, N. İ., & Bilici, Ö. F. (2026). *Responsible Innovation in National AI Policies — analysis code and results* [Software]. Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX
