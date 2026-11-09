# Human double coding – protocol (validation sample)

**Sample.** 40 country-level instrument summaries (20 flagged binding, 20 non-binding by the AI Policy Tracker), drawn with a fixed seed in notebook Step 7.

**Coding sheets.** `coding_sheet_coder_A.xlsx` and `coding_sheet_coder_B.xlsx` (identical): one row per summary with a **randomized coding ID (V01–V40) and the summary text only** – no titles, countries, binding flags or dictionary output. Sheet *Definitions* lists the 13 codes. Each code cell has a 0/1 drop-down.

**Rules.**
1. Code independently. Do not look at the other coder's sheet, Table S4 (dictionary codes), `ai_rater_codes.csv` or `TableS5b_validation_key_not_for_coders.csv`.
2. 1 = the summary itself explicitly expresses the sub-theme as defined; 0 = otherwise. Use no outside knowledge about the instrument. Fill every cell (blank cells are rejected).
3. Save as `coder_A.xlsx` and `coder_B.xlsx` in this folder (keep the `coding_id` column and the column names).
4. Adjudication: list every cell where A and B differ, discuss, record the agreed value for **all** 40 × 13 cells in `consensus.xlsx` (same format). Note how disagreements were resolved.
5. Re-run the notebook. Table 1.2 then reports percentage agreement and Cohen's κ for coder A vs B and dictionary vs consensus per code and dimension (criterion κ ≥ 0.70). Codes below 0.70 are reported as a limitation; validation labels never replace the dictionary codes.

The loader stops with an explicit message if a file has duplicate or unknown IDs, missing summaries, missing columns or values other than 0/1, and human validation is reported as complete only when coder A, coder B and consensus are all present.
