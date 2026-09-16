# Datasets

Redistributed here under their original licences so that sessions load in one line,
with no install and no upload. Attribution below.

---

## AI4I 2020 Predictive Maintenance Dataset

Files: `ai4i2020.csv` (original), `ai4i.parquet` (same data, columnar format)
Used in: **Session 1**, Session 10

- **Source:** UCI Machine Learning Repository, dataset 601
- **DOI:** https://doi.org/10.24432/C5HS5C
- **Licence:** Creative Commons Attribution 4.0 International (**CC BY 4.0**)
- **Citation:** *AI4I 2020 Predictive Maintenance Dataset* [Dataset]. (2020).
  UCI Machine Learning Repository.

**Shape:** 10 000 rows × 14 columns. A synthetic but realistic milling-machine
dataset.

| Column | Meaning |
|---|---|
| `UDI` | Row identifier |
| `Product ID` | Product serial, prefixed by variant |
| `Type` | Quality variant: L (50 %), M (30 %), H (20 %) |
| `Air temperature [K]` | Ambient temperature, kelvin |
| `Process temperature [K]` | Process temperature, kelvin |
| `Rotational speed [rpm]` | Spindle speed |
| `Torque [Nm]` | Torque |
| `Tool wear [min]` | Cumulative tool wear |
| `Machine failure` | Target — did the process fail |
| `TWF` | Tool wear failure |
| `HDF` | Heat dissipation failure |
| `PWF` | Power failure |
| `OSF` | Overstrain failure |
| `RNF` | Random failure |

> ⚠️ **Note for instructors.** The dataset page states that `Machine failure` is 1
> "if at least one of the failure modes is true". **In the data this does not hold in
> 27 rows**: 18 rows have `RNF` set with `Machine failure = 0`, and 9 rows are
> failures with no cause flag at all. This is deliberate teaching material in Session
> 1, not a corruption of the file — the CSV is exactly as distributed by UCI.

The file here is unmodified. `ai4i.parquet` was produced with
`pd.read_csv(...).to_parquet(...)`, no cleaning applied.
