# Practical Work #3. Data Cleaning and Transformation

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Batedwall/pandas-practice-3/blob/main/Pasovystyy_Lb3.ipynb)

**Author:** Julian Pasovystyy

## Overview
This repository contains my solution to Practical Work #3. The goal is to practice detecting and handling
missing values, duplicates and outliers; converting data types; working with string and datetime values;
creating new features; encoding categories; applying normalization and standardization; and building
a reproducible data-cleaning pipeline.

## Repository Contents
| File | Description |
|---|---|
| `Pasovystyy_Lb3.ipynb` | Jupyter notebook (Google Colab) with all steps, individual tasks and the bonus task |
| `data/index_1.csv` | Source dataset: coffee sales (3,636 rows, 6 columns) |
| `data/cleaned_sales.csv` | Result of step 10: cleaned dataset with new features (`hour`, `day_of_week`, `month`, `money_norm`, `money_std`) |
| `data/sales_cleaned_task2.csv` | Result of task 2: dataset with 5 artificial NaNs and 3 duplicates, cleaned |
| `data/cleaned_demo.csv` | Result of the bonus task: output of `clean_dataset()` on a synthetic dirty dataset |

## Dataset
Coffee sales data (`data/index_1.csv`):

- `date` – date of the transaction
- `datetime` – exact date and time of the transaction
- `cash_type` – payment type (`card` / `cash`)
- `card` – anonymized card ID (empty for cash payments)
- `money` – transaction amount
- `coffee_name` – name of the drink

## What Was Done
- Detected and handled missing values (`isnull()`, `dropna()`, `fillna()` with mean / median / mode)
- Detected and removed duplicates (`duplicated()`, `drop_duplicates()`)
- Detected outliers with the IQR method
- Converted `datetime` to `datetime64` with `pd.to_datetime()`
- Cleaned string columns with `.str.strip()`, `.str.lower()`, `.str.replace()`
- Created new features with the `.dt` accessor (year, month, day, day of week, hour)
- Applied one-hot encoding with `pd.get_dummies()` and created a binary feature with `np.where()`
- Applied min-max normalization and standardization to `money`
- **Bonus:** wrote the function `clean_dataset(df)` that removes duplicates, converts dates, fills missing values
  (median for numeric, mode for categorical) and removes IQR outliers, and tested it on a synthetic dirty dataset

## How to Run
1. Upload `data/index_1.csv` to the root of your Google Drive (`My Drive`).
2. Open `Pasovystyy_Lb3.ipynb` in [Google Colab](https://colab.research.google.com).
3. Run the cells from top to bottom and allow access to Google Drive when prompted.
4. The result files will appear in `My Drive`.

The notebook also works in a local Jupyter Notebook: put `index_1.csv` next to the notebook.

## Requirements
- Python 3
- pandas
- numpy

(All of them are preinstalled in Google Colab.)
