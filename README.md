# UP Ganga Water Quality Analysis

An end-to-end data analytics project investigating surface water chemical quality across Central Water Commission (CWC) monitoring stations in Uttar Pradesh, India.

**Status:**  In progress - Data Understanding complete

## Overview

This project examines surface water quality measurements from the CWC monitoring network across Uttar Pradesh, spanning the Ganga river system. It combines Python, PostgreSQL, Excel, and Power BI to move from raw source files to validated findings, with a documented data quality audit and explicit limitations.

The project is designed as a portfolio piece for entry-level data analytics roles, with a focus on reproducible workflows, honest handling of missing data, and clear communication of what the data can and cannot support.

## Data Sources

Raw data is **not** stored in this repository. The original CSV files can be downloaded from the official National Water Data Portal:

1. **Surface Water Quality (Manual - Chemical Parameters), Uttar Pradesh, CWC (1961–2020)**
   [Download CSV](https://nwdp.nwic.gov.in/dataset/4e4c6fcc-6f5a-4a7f-822c-a101581e4767/resource/6d862ee8-c4c3-441e-a174-a0c7b309f155/download/swq_manual_chemical_parameters_cwc_up_1961_2020.csv)

2. **Surface Water Quality Chemical Parameters, CWC Uttar Pradesh (2021–2025) - Manual**
   [Download CSV](https://nwdp.nwic.gov.in/dataset/4e4c6fcc-6f5a-4a7f-822c-a101581e4767/resource/d2a17b9d-617f-4890-ba3c-1ed32fd978f3/download/swq_chemical_parameter_manual_cwc_up_2021_2025.csv)

Place both files in `data/raw/` before running the notebooks.

> **Note:** No official CWC data dictionary or metadata document accompanied these files. A project-derived data dictionary was created from direct inspection and is available in [`docs/data_dictionary.md`](docs/data_dictionary.md).

## Project Workflow

The project follows a documented analytical workflow. Each stage produces its own notebook or deliverable.

- [x] **Project Setup** - repository structure, environment verification
- [x] **Data Understanding** - schema, coverage, missingness, sentinel detection
- [ ] **Data Quality Audit** - duplicates, coordinate validity, anomalous values
- [ ] **Dataset Integration** - determine whether and how to combine the two source files
- [ ] **Cleaning and Validation** - reproducible cleaning pipeline with validation checks
- [ ] **Exploratory Analysis** - temporal, geographic, and parameter-level patterns
- [ ] **Statistical Analysis** - distributions, correlations, group comparisons
- [ ] **Chemistry Interpretation** - scientific meaning of measured parameters, units, benchmarks
- [ ] **SQL Analysis** - PostgreSQL schema and analytical queries
- [ ] **Excel Reporting** - summary workbook with pivot tables and checks
- [ ] **Power BI Dashboard** - interactive reporting on coverage, parameters, quality
- [ ] **Findings and Recommendations** - evidence-based conclusions with limitations
- [ ] **Portfolio Review** - final documentation and interview preparation

## Tools

- **Python** - pandas, NumPy, Matplotlib, Seaborn, JupyterLab
- **PostgreSQL** - schema design and analytical SQL
- **Microsoft Excel** - summary workbook and quality checks
- **Power BI** - interactive dashboard
- **Git / GitHub** - version control and portfolio hosting

## Project Structure
```
up-ganga-water-quality-analysis/
├── data/
│ ├── raw/ # Original CSVs (not committed)
│ ├── processed/ # Cleaned, analysis-ready data
│ └── external/ # Source notes and metadata
├── notebooks/ # Step-by-step analysis notebooks
├── src/ # Reusable Python scripts
├── sql/ # PostgreSQL schema and analytical queries
├── excel/ # Excel deliverables
├── powerbi/ # Power BI dashboard
├── docs/ # Documentation
├── figures/ # Exported charts
└── screenshots/ # Dashboard and workbook screenshots
```


## Documentation

Detailed documentation is maintained alongside the analysis:

| Document | Purpose |
|---|---|
| [`docs/data_dictionary.md`](docs/data_dictionary.md) | Column reference derived from direct inspection |
| *(more to follow)* | Data quality report, methodology, findings and limitations |

## Key Findings So Far

From the **Data Understanding** stage:

- Both source files share an identical 52-column schema.
- `River` and `Basin` are constant (`Ganga`) throughout both files; the useful hydrological variation is in `Tributary`, `Subtributary`, `SubSubtributary`, and `Local River`.
- All 33 chemical parameter columns are free of non-numeric tokens - no detection-limit markers, quality flags, or stray text.
- The two files have complementary measurement coverage (e.g. `Total Hardness` is 7% null in the historical file but 79% null in the recent file). This constrains any cross-period comparison.
- `Block` and `Village` are more than 93% placeholder `-` and are not usable for grouping.
- Actual date coverage: **1963-08-01** to **2025-04-23**, continuous across the two files.
- 86 stations match by normalized name; the remaining differences require a documented manual mapping during cleaning.

Full details and per-column statistics are in [`notebooks/01_data_understanding.ipynb`](notebooks/01_data_understanding.ipynb).

## Reproducibility

*(To be completed after the cleaning pipeline is established.)*

## Limitations

*(To be completed after the data quality audit.)*

## Author

Himanshu — [GitHub profile](https://github.com/hmshdev)