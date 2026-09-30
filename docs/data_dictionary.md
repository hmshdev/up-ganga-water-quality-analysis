# Data Dictionary

This data dictionary was created by the project author based on direct inspection of the two CSV files. No official CWC data dictionary accompanied the data. Where a column's meaning is inferred rather than documented by the source, this is stated explicitly.

## Source files

| File | Rows | Columns | Actual date range |
|---|---|---|---|
| `swq_manual_chemical_parameters_cwc_up_1961_2020.csv` | 30,359 | 52 | 1963-08-01 to 2020-12-21 |
| `swq_chemical_parameter_manual_cwc_up_2021_2025.csv` | 12,178 | 52 | 2021-01-01 to 2025-04-23 |

Both files share an identical column schema.

## Conventions

- **Missing:** an empty cell, represented as `NaN` when loaded with `pandas.read_csv`.
- **Sentinel `-`:** a literal hyphen used as a placeholder in specific text columns. Not treated as `NaN` unless explicitly documented.
- **dtype as loaded:** all columns were loaded as `pandas.StringDtype` for inspection. Numeric parsing is deferred to later phases.

## Column reference

### Administrative and geographic columns

| Column | Role | Historical `-` | Historical null | Recent `-` | Recent null | Notes |
|---|---|---|---|---|---|---|
| `SlNo` | Record index | 0 | 0 | 0 | 0 | Unique per file (30,359 / 12,178 distinct). Not globally unique across files. |
| `Station` | Monitoring station name | 0 | 0 | 0 | 0 | 99 distinct (historical), 95 (recent). Naming variants observed. |
| `Agency` | Reporting agency | 0 | 0 | 0 | 0 | 1 distinct value in both files (believed to be `CWC` based on sample rows to be confirmed in Data Quality Audit). |
| `State LGD Code` | Local Government Directory code for state | 0 | 0 | 0 | 0 | 1 distinct value in both files (sample row shows `9`). |
| `State` | State name | 0 | 0 | 0 | 0 | 1 distinct value in both files (sample row shows `Uttar Pradesh`). |
| `District LGD Code` | LGD code for district | 0 | 0 | 0 | 0 | 53 distinct (historical), 49 (recent). |
| `District` | District name | 0 | 0 | 0 | 0 | 53 distinct (historical), 49 (recent). |
| `Tehsil` | Tehsil name | 0 | 0 | 286 | 0 | Tehsil uses `-` only in the recent file. |
| `Block` | Block name | 28,913 | 0 | 11,389 | 0 | >93% `-`. Not usable for grouping. 7 distinct values, the non `-` values require Data Quality inspection. |
| `Village` | Village name | 28,913 | 0 | 11,389 | 0 | Same pattern as `Block`. |

### Hydrological columns

| Column | Role | Historical `-` | Recent `-` | Historical distinct | Recent distinct |
|---|---|---|---|---|---|
| `River` | River name | 0 | 0 | 1 | 1 | Constant: `Ganga`. |
| `Basin` | Basin name | 0 | 0 | 1 | 1 | Constant: `Ganga`. |
| `Tributary` | Tributary name | 4,944 | 2,166 | 12 | 11 | |
| `Subtributary` | Subtributary name | 16,771 | 6,439 | 20 | 21 | `-` here likely means "not applicable at this level". |
| `SubSubtributary` | Sub-subtributary name | 23,966 | 10,160 | 7 | 7 | |
| `Local River` | Local river name | 18 | (see Data Quality Audit) | 31 | 30 | |

### Coordinate columns

| Column | Historical distinct | Recent distinct | Notes |
|---|---|---|---|
| `Latitude` | 98 | 94 | Stored as strings; plausible decimal values in sample rows. Validity checks in Data Quality Audit. |
| `Longitude` | 99 | 94 | Same. |

### Record and time columns

| Column | Historical distinct | Recent distinct | Notes |
|---|---|---|---|
| `Data Acquisition Time` | 12,434 | 6,925 | Format `DD-MM-YYYY HH:MM`. Zero unparseable dates when parsed with `dayfirst=True`. |

### Chemical parameter columns (33 total)

All parameter columns contain no non-numeric tokens. Missing values are empty cells (`NaN`).

| Column | Historical non-null | Historical null % | Recent non-null | Recent null % |
|---|---|---|---|---|
| `Amonia N (mgN/L)` | 17,939 | 40.91 | 11,979 | 1.63 |
| `Boron (mg/L)` | 0 | 100.00 | 0 | 100.00 |
| `Carbonate (mg/L)` | 29,529 | 2.73 | 12,068 | 0.90 |
| `Calcium (mg/L)` | 29,568 | 2.61 | 12,136 | 0.34 |
| `Chloride (mg/L)` | 29,556 | 2.65 | 12,046 | 1.08 |
| `Dissolved oxygen (mg/L)` | 15,119 | 50.20 | 11,563 | 5.05 |
| `Total Dissolved Solids (mg/L)` | 10,825 | 64.34 | 12,086 | 0.76 |
| `Fluoride (mg/L)` | 0 | 100.00 | 0 | 100.00 |
| `Bicarbonate (mg/L)` | 29,567 | 2.61 | 12,151 | 0.22 |
| `Potassium (mg/L)` | 0 | 100.00 | 0 | 100.00 |
| `Magnesium (mg/L)` | 29,560 | 2.63 | 12,144 | 0.28 |
| `Sodium (mg/L)` | 28,930 | 4.71 | 12,144 | 0.28 |
| `Nitrite N+Nitrate N (mgN/L)` | 15,952 | 47.46 | 12,101 | 0.63 |
| `Potential of Hydrogen (pH)` | 29,933 | 1.40 | 12,124 | 0.44 |
| `Sulphate (mg/L)` | 29,417 | 3.10 | 12,139 | 0.32 |
| `Total Phosphorus (mgP/L)` | 11,124 | 63.36 | 2,844 | 76.65 |
| `Arsenic (mg/L)` | 621 | 97.95 | 3,156 | 74.08 |
| `Total Alkalinity (mg/L as CaCO3)` | 26,423 | 12.96 | 2,666 | 78.11 |
| `Cadmium (mg/L)` | 675 | 97.78 | 3,156 | 74.08 |
| `Chromium (mg/L)` | 670 | 97.79 | 3,156 | 74.08 |
| `Iron(mg/L)` | 18,739 | 38.28 | 4,463 | 63.35 |
| `Hardness Calcium (mgCaCO3/L)` | 4,295 | 85.85 | 2,106 | 82.71 |
| `Mercury(mg/L)` | 1 | ~100 | 1,885 | 84.52 |
| `Hardness_Magnesium (mg/L as CaCO3)` | 0 | 100.00 | 1,324 | 89.13 |
| `Total Hardness (mgCaCO3/L)` | 28,200 | 7.11 | 2,562 | 78.96 |
| `Manganese (mg/L)` | 0 | 100.00 | 1 | 99.99 |
| `Nitrate N (mgN/L)` | 16,467 | 45.76 | 11,055 | 9.22 |
| `Nickel (mg/L)` | 649 | 97.86 | 3,094 | 74.59 |
| `Lead (mg/L)` | 668 | 97.80 | 3,147 | 74.16 |
| `Zinc (mg/L)` | 665 | 97.81 | 3,146 | 74.17 |
| `Sodium Adsorption Ratio (%)` | 24,376 | 19.71 | 6 | 99.95 |
| `Nitrate (mg/L)` | 0 | 100.00 | 577 | 95.26 |
| `Copper (mg/L)` | 357 | 98.82 | 3,155 | 74.09 |

### Interpretation notes

- **Units** are embedded in the column names (e.g. `mg/L`, `mgN/L`, `mgP/L`, `mgCaCO3/L`). No separate unit column is provided.
- **`Nitrate (mg/L)` vs `Nitrate N (mgN/L)` vs `Nitrite N+Nitrate N (mgN/L)`** measure different chemical quantities. They must not be combined without conversion. Conversions and comparisons are deferred until the chemistry interpretation stage, where reporting basis (elemental vs. ionic vs. nitrogen-equivalent) is examined explicitly.
- **`Hardness Calcium (mgCaCO3/L)` vs `Hardness_Magnesium (mg/L as CaCO3)` vs `Total Hardness (mgCaCO3/L)`** are related but distinct. Their relationship will be examined during exploratory and statistical analysis.
- **`Sodium Adsorption Ratio (%)`** is reported as a percentage in this dataset, which is unusual - SAR is conventionally unitless. This warrants careful interpretation and is flagged for the chemistry interpretation stage.

### Known limitations of this dictionary

- The meaning of some columns is inferred from their names and observed values. Official documentation was not available from the source.
- The Agency, State, and State LGD Code constant values are based on a small sample; they will be confirmed during the data quality audit.
- Sub-subtributary and subtributary `-` values likely mean "not applicable at this level" but this is an interpretation, not a documented fact.