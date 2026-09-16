# One page: coming from Excel, MATLAB or R

You already know how to analyse data. This page is only about **where the buttons
moved**. Find your column and read across.

---

## The five things that trip everyone up

| | What bites you |
|---|---|
| **1. Counting starts at 0** | The first row is `0`, not `1`. MATLAB and R both start at 1. This causes more first-week bugs than anything else |
| **2. Ranges exclude the end** | `df[0:3]` gives you rows 0, 1, 2 — **not** 3. `1:3` in MATLAB gives you three elements *including* 3 |
| **3. A DataFrame is not a matrix** | Columns have names and can have different types. It is much closer to a spreadsheet than to a matrix |
| **4. `=` does not copy** | `b = a` makes `b` another name for the same table. Editing `b` edits `a`. Use `a.copy()` when you mean a copy |
| **5. Missing is `NaN`, and it is contagious** | `NaN` is not zero and not empty text. Most operations skip it silently — which is convenient right up to the moment it is not |

---

## Doing the same thing in four places

| Task | Excel | MATLAB | R | **pandas** |
|---|---|---|---|---|
| Open a table | `Ctrl+O` | `readtable('f.csv')` | `read.csv("f.csv")` | `pd.read_csv("f.csv")` |
| See the top | scroll | `head(T)` | `head(df)` | `df.head()` |
| Size | name box | `size(T)` | `dim(df)` | `df.shape` |
| Column names | row 1 | `T.Properties.VariableNames` | `names(df)` | `df.columns` |
| Summary stats | `=AVERAGE()`… | `summary(T)` | `summary(df)` | `df.describe()` |
| One column | a column | `T.Torque` | `df$Torque` | `df["Torque"]` |
| Several columns | select | `T(:, {'a','b'})` | `df[, c("a","b")]` | `df[["a", "b"]]` |
| Filter rows | AutoFilter | `T(T.Torque > 40, :)` | `df[df$Torque > 40, ]` | `df[df["Torque"] > 40]` |
| New column | type a formula | `T.kW = T.T .* T.w` | `df$kW <- df$T * df$w` | `df["kW"] = df["T"] * df["w"]` |
| Pivot table | PivotTable | `grpstats` | `aggregate()` / `dplyr` | `df.groupby("Type").mean()` |
| VLOOKUP / join | `VLOOKUP` | `join` | `merge()` | `df.merge(other, on="id")` |
| Count by category | pivot count | `groupcounts` | `table(df$x)` | `df["x"].value_counts()` |
| Sort | Sort | `sortrows(T,'x')` | `df[order(df$x), ]` | `df.sort_values("x")` |
| Count blanks | `COUNTBLANK` | `sum(ismissing(T))` | `sum(is.na(df))` | `df.isna().sum()` |
| Mean of a column | `=AVERAGE(B:B)` | `mean(T.x)` | `mean(df$x)` | `df["x"].mean()` |

---

## If you come from Excel

The hard part is not the syntax — it is that **you cannot see the whole table any
more**. You gain three things in exchange:

- **It is repeatable.** Same code, same result, next month, on a bigger file.
- **It scales.** 10 000 rows is small. A spreadsheet starts hurting long before pandas does.
- **It is auditable.** Every step is written down. Nobody has to wonder which cells had a formula.

A 0/1 column is your friend: `df["Machine failure"].mean()` *is* the failure rate,
because the average of zeros and ones is the proportion of ones.

## If you come from MATLAB

You will feel at home fast. Two honest warnings:

- **Stop writing loops.** If you are looping over rows, there is almost always a
  column operation that does it in one line and a hundred times faster.
- **`df["x"]` returns a Series**, not an array. It carries an index along with it,
  and that index will line things up for you — or surprise you — during arithmetic.

`.values` gets you the underlying array when you really want one.

## If you come from R

The concepts map almost one to one: `data.frame` → `DataFrame`, `$` → `["..."]`,
`dplyr` verbs → `.query()`, `.assign()`, `.groupby()`.

The real difference is that **pandas chains methods** where dplyr pipes:

```python
(df
 .query("Torque > 40")
 .groupby("Type")["Machine failure"]
 .mean())
```

You will see R in this subject — the Electrical lab starts in R, and it turns up in
the modelling theory. Neither language is better. Python is what we use here because
Colab gives it to you for free with no installation, and because the AI tooling you
will lean on is Python-first.

---

## When you are stuck

1. Read the **last line** of the error. Python puts the useful part at the bottom.
2. `type(x)` and `x.shape` answer most "why is this not working".
3. Ask Gemini — then ask yourself the three questions: *What did it get right? What
   did it assume it had no way of knowing? How did I check?*

---

*Equivalences for spreadsheets and SQL are documented officially by the pandas
project ("Comparison with spreadsheets", "Comparison with SQL", BSD-3-Clause).*
