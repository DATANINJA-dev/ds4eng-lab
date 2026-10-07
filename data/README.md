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
Used in: **Session 2**, Session 3, Session 4-5

- **Source:** UCI Machine Learning Repository, dataset 597
- **DOI:** https://doi.org/10.24432/C51S6D
- **Licence:** Creative Commons Attribution 4.0 International (**CC BY 4.0**)
- **Citation:** *Productivity Prediction of Garment Employees* [Dataset]. (2020).
  UCI Machine Learning Repository. Original study: Imran, A. A., Amin, M. N.,
  Islam Rifat, M. R., & Mehreen, S. (2019). *Deep Neural Network Approach for
  Predicting the Productivity of Garment Employees.* CoDIT 2019, pages 1402-1407.

**Shape:** 1197 rows x 15 columns (14 features and the target), no duplicate rows. A garment factory in
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

> ⚠️ **Note for instructors.** Three things in this file disagree with its dataset
> card, and all three are deliberate teaching material in Session 2. The CSV is
> exactly as distributed by UCI and **nothing has been cleaned**.
>
> 1. The card types `wip`, `idle_time` and `no_of_workers` as **Integer**; in the
>    file all three are `float64`. For `wip` the cause is the gaps.
> 2. **`wip` is empty in 506 rows, and every one of them is finishing.** Sewing has
>    zero gaps. This is not missing data: a finishing line has no work in progress.
>    It should be read as "not applicable", never filled with a zero.
> 3. The card says a month is divided into four quarters. The file has five.
>
> **Not a disagreement, although it reads like one:** the card declares
> `num_features = 14` while the file has 15 columns. It is not a contradiction — the
> card counts *features*, and its own variable table lists all 15, fourteen with role
> `Feature` and `actual_productivity` with role `Target`. The same applies to the
> `num_features = 6` of AI4I 601. Do not use either as an example of a card
> contradicting its file: the real one in AI4I is that the card writes the first
> column `UID` and the header says `UDI`.
>
> One more, which is not a card disagreement but matters for any comparison between
> departments: **58 % of sewing rows record `actual_productivity` within 0.001 of
> `targeted_productivity`** (42 % identical to three decimals), against 0.2 % in finishing. Any
> statement comparing the two departments' hit rates is describing recording
> practice at least as much as performance.
>
> Verified against the file on 22 September 2026. Zip sha256 `446026846b37d738…`.

---

## Absenteeism at work

Used in: Session 3, Part 2 (read directly from UCI)

`Absenteeism_at_work.csv` inside the UCI zip - **740 rows x 21 columns**, separator `;`, no missing values.

A courier company in Brazil, **July 2007 to July 2010**. **Each row is one recorded
absence** of one employee (not an employee, not a month). There are 36 employees.

The question we use it for: *when someone calls in absent, will it last more than one
working day?* - long absence = `Absenteeism time in hours` > 8.

### Columns

| Column (exact name) | Type in the file | What it means |
|---|---|---|
| `ID` | int64 | Employee number (1-36). Identifies a person, not an absence. |
| `Reason for absence` | int64 | Why the person was absent, as written on the medical certificate: codes 1-21 are disease chapters of the ICD, 22-28 are other reasons (see the table below). 0 is not documented. |
| `Month of absence` | int64 | Month of the absence, 1-12. The year is NOT in the file. 0 appears in 3 rows. |
| `Day of the week` | int64 | 2 = Monday, 3 = Tuesday, 4 = Wednesday, 5 = Thursday, 6 = Friday. |
| `Seasons` | int64 | Period of the year, 1-4 (see the notes: the names in the source do not match the months). |
| `Transportation expense` | int64 | Commuting cost for this employee (period and currency not documented). |
| `Distance from Residence to Work` | int64 | Kilometres from home to work. |
| `Service time` | int64 | Years working for the company (one value per employee, not updated). |
| `Age` | int64 | Age in years (one value per employee, not updated). |
| `'Work load Average/day '` | float64 | Average daily workload of the company that month (units not documented). One value per month, the same for everybody. Note the space at the end of the column name. |
| `Hit target` | int64 | Target achievement, 81-100 (probably a percentage; not documented). One value per month, the same for everybody. |
| `Disciplinary failure` | int64 | 1 = this row records a disciplinary failure, 0 = no. |
| `Education` | int64 | 1 = high school, 2 = graduate, 3 = postgraduate, 4 = master or doctor. |
| `Son` | int64 | Number of children. |
| `Social drinker` | int64 | 1 = yes, 0 = no. Health data. |
| `Social smoker` | int64 | 1 = yes, 0 = no. Health data. |
| `Pet` | int64 | Number of pets. |
| `Weight` | int64 | Weight (kg, by its range). Health data. |
| `Height` | int64 | Height (cm, by its range). Health data. |
| `Body mass index` | int64 | Weight / height squared (kg/m2), rounded. Health data. |
| `Absenteeism time in hours` | int64 | How long the absence lasted, in hours. The TARGET. 8 hours = one working day. |

The column `'Work load Average/day '` has a **space at the end of its name**. Typing it
without the space gives a `KeyError`.

### Reason for absence codes

| Code | Meaning | Rows |
|---|---|---|
| 0 | (not documented - see notes) | 43 |
| 1 | I - Certain infectious and parasitic diseases | 16 |
| 2 | II - Neoplasms | 1 |
| 3 | III - Diseases of the blood and immune system | 1 |
| 4 | IV - Endocrine, nutritional and metabolic diseases | 2 |
| 5 | V - Mental and behavioural disorders | 3 |
| 6 | VI - Diseases of the nervous system | 8 |
| 7 | VII - Diseases of the eye and adnexa | 15 |
| 8 | VIII - Diseases of the ear and mastoid process | 6 |
| 9 | IX - Diseases of the circulatory system | 4 |
| 10 | X - Diseases of the respiratory system | 25 |
| 11 | XI - Diseases of the digestive system | 26 |
| 12 | XII - Diseases of the skin and subcutaneous tissue | 8 |
| 13 | XIII - Diseases of the musculoskeletal system and connective tissue | 55 |
| 14 | XIV - Diseases of the genitourinary system | 19 |
| 15 | XV - Pregnancy, childbirth and the puerperium | 2 |
| 16 | XVI - Certain conditions originating in the perinatal period | 3 |
| 17 | XVII - Congenital malformations and chromosomal abnormalities | 1 |
| 18 | XVIII - Symptoms and abnormal findings, not elsewhere classified | 21 |
| 19 | XIX - Injury, poisoning and other consequences of external causes | 40 |
| 20 | XX - External causes of morbidity and mortality | 0 |
| 21 | XXI - Factors influencing health status and contact with health services | 6 |
| 22 | patient follow-up (no ICD code) | 38 |
| 23 | medical consultation (no ICD code) | 149 |
| 24 | blood donation (no ICD code) | 3 |
| 25 | laboratory examination (no ICD code) | 31 |
| 26 | unjustified absence (no ICD code) | 33 |
| 27 | physiotherapy (no ICD code) | 69 |
| 28 | dental consultation (no ICD code) | 112 |

Codes 1-21 are the chapters of the International Classification of Diseases (ICD, in
Portuguese "CID"). Codes 22-28 have no ICD code. Code 0 is not documented: in this file
it appears only on rows with 0 hours that are disciplinary records or the 3 rows with month 0.

### Things in the file worth knowing

- The rows are in **time order** (July 2007 first), but there is no date or year column.
- There are exact duplicate rows. With no date, two equal rows may be two real absences
  (for example, physiotherapy every Wednesday in the same month).
- Every row with `Disciplinary failure` = 1 has 0 hours and reason 0: it is not an absence.
- The 3 rows with `Month of absence` = 0 are the last 3 rows, with reason 0 and 0 hours.
- Age, service time, weight and the other personal columns do not change over the three
  years for an employee: they are a snapshot, not the value on the day of the absence.
- The source documents call the `Seasons` codes summer (1), autumn (2), winter (3) and
  spring (4), but code 1 covers June-September, which is winter in Brazil. Treat
  `Seasons` as four periods of the year, not as season names.
- Units of `Transportation expense`, `Work load Average/day ` and `Hit target` are not documented.

### Source and licence

Martiniano, A. & Ferreira, R. (2012). Absenteeism at work [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5X882. Licensed under CC BY 4.0. Original study: Martiniano, A., Ferreira, R. P., Sassi, R. J., & Affonso, C. (2012). Application of a neuro fuzzy network in prediction of absenteeism at work. 7th Iberian Conference on Information Systems and Technologies (CISTI), 1-4. IEEE.

Licence **CC BY 4.0** - DOI [10.24432/C5X882](https://doi.org/10.24432/C5X882). Original data from the UCI Machine
Learning Repository, used unmodified with attribution, as the licence allows.
Zip sha256 `89ecdfed5f107bb97015c335b1d812d7...`
