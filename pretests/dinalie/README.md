
# dinalie — dataset pretests and preprocessing notes

This folder is a personal workspace for exploratory checks and preprocessing plans for the following educational datasets (summary and suggested next steps).

## Datasets included / considered

- **OULAD (Open University Learning Analytics Dataset)**
  - Description: 32K+ students, demographics, VLE engagement events, assessment attempts and final results. Rich for time-series of interactions and demographics.
  - Typical contents: student demographics, module registrations, assessment scores, VLE interaction logs.

- **xAPI-Edu-Data (Kaggle)**
  - Description: Behavioral indicators such as raised hands, discussion participation, and other features relating to classroom behavior and performance.
  - Typical contents: student-level behavioral features and labels (performance categories).

- **UCI Student Performance Dataset**
  - Description: Two smaller datasets (math and Portuguese) with grades, demographic and social data, family background, and study habits.
  - Typical contents: student attributes, two course datasets, final grade (numeric), often used for regression/classification tasks.

- **Educational Process Mining Dataset**
  - Description: Sequential event logs capturing student interactions over time (e.g., problem attempts, hint requests) suitable for process mining and sequence models.

> Note: This folder currently holds notes and plans. If you place raw dataset files here, use the naming convention described below to allow preprocessing scripts to find them easily.

## Goals for this pretest folder

1. Check each dataset's schema and data quality.
2. Assess whether datasets can be combined into a single analysis dataset (and how).
3. Define and implement minimal preprocessing steps to transform each dataset into a common, analysis-ready format (CSV per-dataset and an optional merged CSV).
4. Provide example code snippets / command line steps to run the preprocessing.


## Roughly planned Preprocessing checklist and steps

1. Raw data intake
	- Place raw files into `raw/` with intuitive names, e.g. `raw/oulad.csv`, `raw/xapi_edu.csv`, `raw/uci_math.csv`, `raw/epm_log.csv`.
	- Record source URL and license in `raw/SOURCES.txt`.

2. Schema inspection
	- Read first N rows and infer column names/types. Verify encodings and handle non-UTF8 if present.

3. Cleaning
	- Standardize missing value markers, trim whitespace, normalize text case.
	- Remove or mark obvious duplicates.
	- Handle outliers for numeric fields using clipping or log transforms where appropriate.

4. Identifier handling
	- Inspect possible student identifiers and document them in `processed/ID_MAP.csv` (columns: `source_dataset`, `orig_id`, `generated_id`, `notes`).
	- If no stable common id, generate stable per-dataset `generated_id` (e.g. `oulad_000123`) and consider merging only when mapping is available.

5. Feature engineering and aggregation
	- For event logs (OULAD, EPM), produce aggregate features per student and per-course: counts, rates, recency, session lengths, percentiles.
	- For temporal features, create fixed-window aggregates (last 7/30/90 days) if timestamps exist.

6. Label harmonization
	- Convert grades to consistent scales; for classification create categorical labels (`A/B/C` or `pass/fail`) and document thresholds.

7. Save processed outputs
	- Store per-dataset canonical CSVs under `processed/` and place any mapping files and transformation logs into `processed/meta/`.

## Planned file structure

```
pretests/dinalie/
├─ raw/                # put original downloaded files here
│  ├─ oulad/           # raw OULAD files (multiple CSVs often)
│  ├─ xapi_edu.csv
│  ├─ uci_student-math.csv
│  └─ epm_logs.csv
├─ processed/          # outputs from preprocessing
│  ├─ oulad_students.csv
│  ├─ xapi_students.csv
│  ├─ uci_students.csv
│  └─ merged_students.csv   # optional final merge when safe to do
├─ scripts/            # any preprocessing scripts or notebooks
├─ SOURCES.txt         # data URLs and license notes
└─ README.md           # this file
```

