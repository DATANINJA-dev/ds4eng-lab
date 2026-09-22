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
| `Type` | Quality variant. **In the file: L 6 000 rows (60 %), M 2 997 (30 %), H 1 003 (10 %).** The dataset card says 50 / 30 / 20 % — a second place where the card and the file disagree |
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

---

## Productivity Prediction of Garment Employees

File: `garments_worker_productivity.csv`
Used in: **Session 2**, Session 3, Session 5

- **Source:** UCI Machine Learning Repository, dataset 597
- **DOI:** https://doi.org/10.24432/C51S6D
- **Licence:** Creative Commons Attribution 4.0 International (**CC BY 4.0**)
- **Citation:** *Productivity Prediction of Garment Employees* [Dataset]. (2020).
  UCI Machine Learning Repository. Original study: Imran, A. A., Amin, M. N.,
  Islam Rifat, M. R., & Mehreen, S. (2019). *Deep Neural Network Approach for
  Predicting the Productivity of Garment Employees.* CoDIT 2019, pages 1402-1407.

**Shape:** 1197 rows x 15 columns, no duplicate rows. A garment factory in
Bangladesh, January to March 2015. One row is one team, on one day, in one
department.

| Column | dtype in the file | Missing | Meaning |
|---|---|---|---|
| `date` | object | 0 | Day of production, as **text** in `m/d/yyyy`. 59 distinct days |
| `quarter` | object | 0 | Portion of the month. **Five values, not four** — Q1-Q4 are blocks of seven days, `Quarter5` is days 29 and 31 |
| `department` | object | 0 | **Three labels for two departments**: `sweing` 691, `finishing ` (trailing space) 257, `finishing` 249 |
| `day` | object | 0 | Day of the week. **Six values — there is no Friday**, the weekend in Bangladesh |
| `team` | int64 | 0 | Production team, 1 to 12. A label stored as a number |
| `targeted_productivity` | float64 | 0 | Goal given to the team, 0 to 1. **Only 9 distinct values**, from 0.07 to 0.80 |
| `smv` | float64 | 0 | Standard minute value: minutes one garment should take. Mean 3.89 in finishing against 23.25 in sewing |
| `wip` | float64 | **506** | Work in progress. See the note below |
| `over_time` | int64 | 0 | Overtime, in minutes |
| `incentive` | int64 | 0 | Bonus paid, in Bangladeshi taka. Mean 38.2, **median 0**, 604 rows at zero |
| `idle_time` | float64 | 0 | Minutes the line was stopped. Above zero in only 18 rows |
| `idle_men` | int64 | 0 | Workers idle while the line was stopped |
| `no_of_style_change` | int64 | 0 | Product changes that day, 0 to 2 |
| `no_of_workers` | float64 | 0 | Workers on the team. 2 to 89, median 34 |
| `actual_productivity` | float64 | 0 | Target — what the team delivered, 0 to 1. **37 rows exceed 1.00**, up to 1.12 |

> ⚠️ **Note for instructors.** Four things in this file disagree with its dataset
> card, and all four are deliberate teaching material in Session 2. The CSV is
> exactly as distributed by UCI and **nothing has been cleaned**.
>
> 1. The card declares **14 features**; the file has **15 columns** (14 plus the
>    target). Same ambiguity as the 6-vs-14 of AI4I in Session 1.
> 2. The card types `wip`, `idle_time` and `no_of_workers` as **Integer**; in the
>    file all three are `float64`. For `wip` the cause is the gaps.
> 3. **`wip` is empty in 506 rows, and every one of them is finishing.** Sewing has
>    zero gaps. This is not missing data: a finishing line has no work in progress.
>    It should be read as "not applicable", never filled with a zero.
> 4. The card says a month is divided into four quarters. The file has five.
>
> One more, which is not a card disagreement but matters for any comparison between
> departments: **58 % of sewing rows record `actual_productivity` exactly equal to
> `targeted_productivity`** to three decimals, against 0.2 % in finishing. Any
> statement comparing the two departments' hit rates is describing recording
> practice at least as much as performance.
>
> Verified against the file on 22 September 2026. Zip sha256 `446026846b37d738…`.
