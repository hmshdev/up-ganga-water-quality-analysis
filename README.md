# UP Ganga Water Quality Analysis

An end-to-end data analytics project investigating surface water chemical quality across Central Water Commission (CWC) monitoring stations in Uttar Pradesh, India.

**Status:** In progress — Phase 1 (Project setup)

## Data Sources

Raw data is **not** stored in this repository. The original CSV files can be downloaded from the official National Water Data Portal:

1. **Surface Water Quality (Manual — Chemical Parameters), Uttar Pradesh, CWC (1961–2020)**
   [Download CSV](https://nwdp.nwic.gov.in/dataset/4e4c6fcc-6f5a-4a7f-822c-a101581e4767/resource/6d862ee8-c4c3-441e-a174-a0c7b309f155/download/swq_manual_chemical_parameters_cwc_up_1961_2020.csv)

2. **Surface Water Quality Chemical Parameters, CWC Uttar Pradesh (2021–2025) — Manual**
   [Download CSV](https://nwdp.nwic.gov.in/dataset/4e4c6fcc-6f5a-4a7f-822c-a101581e4767/resource/d2a17b9d-617f-4890-ba3c-1ed32fd978f3/download/swq_chemical_parameter_manual_cwc_up_2021_2025.csv)

Place both files in `data/raw/` before running the notebooks.

> **Note:** No official CWC data dictionary or metadata document was available at the time of this project. A project-derived data dictionary will be created in `docs/data_dictionary.md` based on actual inspection of the datasets.

## Tools

- Python (Pandas, NumPy, Matplotlib/Seaborn)
- (PostgreSQL)
- Microsoft Excel
- Power BI
- Git / GitHub

## Project Structure
```
├───data
│   ├───external
│   ├───processed
│   └───raw
├───docs
├───excel
├───figures
├───notebooks
├───powerbi
├───screenshots
├───sql
│   ├───queries
│   └───schema
└───src
```



## Reproducibility

*(To be completed after the cleaning pipeline is established.)*

## Limitations

*(To be completed after data quality audit.)*

## Author

Himanshu Kushwaha — [GitHub profile](www.linkedin.com/in/himanshu-kushwaha-98506b199)
