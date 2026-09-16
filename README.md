# DS4Eng — Organisation Lab

**Applied Data Science for Engineering (205038)** · Master's in Industrial Engineering
ESEIAAT · UPC · Autumn 2026/27

Lab sessions for groups **ORG1** and **ORG2**.
Instructor: **Alfons Marquès** · Course coordinator: Alfredo Vellido

---

## Getting started

You need **nothing installed**. No Python, no Anaconda, no downloads.

1. Click the **Open in Colab** badge for the session.
2. In Colab: `File → Save a copy in Drive`. Now it is yours and your work is saved.
3. Run the cells from top to bottom.

Bring your own laptop and be logged into a Google account.

---

## Sessions

| # | Date | Session | Notebook |
|---|------|---------|----------|
| 1 | 16 Sep | **Survival Python** — from a spreadsheet to a DataFrame | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DATANINJA-dev/ds4eng-lab/blob/main/sessions/s01/s01_survival_python.ipynb) |
| 2 | 23 Sep | Understanding the problem — EDA and the data dictionary | *soon* |
| 3 | 30 Sep | CRISP-DM in a notebook | *soon* |
| 4 | 07 Oct | Data quality and the anatomy of what is missing | *soon* |
| 5 | 14 Oct | Imputing without cheating, and outliers | *soon* |
| 6 | 21 Oct | From 590 columns to 20 — feature selection | *soon* |
| 7 | 11 Nov | PCA and the cost of interpretability | *soon* |
| 8 | 18 Nov | Visualising to defend a claim · Project 1 workshop | *soon* |
| 9 | 25 Nov | The canonical workflow — train/test and honest metrics | *soon* |
| 10 | 02 Dec | Without labels — clustering and anomalies | *soon* |
| 11 | 09 Dec | Temporal validation and remaining useful life | *soon* |
| 12 | 16 Dec | Interpretability, bias and governance | *soon* |

No class on 28 October or 4 November. **Sessions 3 (30 Sep) and 4 (7 Oct) are online.**

Direct link to today's notebook:
https://colab.research.google.com/github/DATANINJA-dev/ds4eng-lab/blob/main/sessions/s01/s01_survival_python.ipynb

Course folder on the UPC Drive (slides, notebook, data):
https://drive.google.com/drive/folders/1olQg_qW7iPQU0Z1tDLhZpg7Zu9hF4MEm

---

## How a session runs

| Minutes | Block |
|---|---|
| 0–20 | **The idea** — one concept, tied to theory you have already seen, with one worked example |
| 20–120 | **The lab** — guided → semi-guided (in pairs) → open, no hints. I walk the room and ask |

Every notebook starts from a clean dataset provided here. **You never depend on last
week's results**, so a bad week never blocks the next one.

Stuck on a cell? Every task has a folded answer underneath it. Open it and move on.

---

## Assessment

Your two lab projects are **80 % of the subject's final mark**.

| | Weight | Mode | Released | Due |
|---|---|---|---|---|
| **Project 1** | 30 % | Groups of 3 | Session 6 · 21 Oct | 23 Nov |
| **Project 2** | 50 % | Individual | Session 9 · 25 Nov | January |

---

## Using AI in this course

You are expected to use a language model. Gemini is available to you through UPC.

The rule is short: **the model writes the code, it does not make the judgement — and
you may not submit anything you cannot defend out loud.**

Every Atenea submission carries the UPC authorship declaration, where you state which
tools you used and **how you validated the results**. That last box is the same
question as this subject's learning outcome. We practise it every week with three
questions: *What did it get right? What did it assume it had no way of knowing? How
did you check?*

---

## Data

| Dataset | Source | Licence |
|---|---|---|
| **AI4I 2020 Predictive Maintenance** | [UCI 601](https://doi.org/10.24432/C5HS5C) | CC BY 4.0 |

Datasets are redistributed here under their original licences, with attribution. See
[`data/README.md`](data/README.md).

---

## Repository layout

```
data/              datasets, ready to load — no upload, no install
sessions/sNN/      one notebook per session
cheatsheet/        coming from Excel, MATLAB or R? start here
troubleshooting/   when Colab misbehaves
```

Course material © Alfons Marquès, released under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Code samples under MIT.
